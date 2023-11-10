# Instalación de SQL Server en Mac utilizando Docker

La instalación de SQL Server en Mac se simplifica gracias a [Docker](https://www.docker.com/get-started/), una herramienta que permite crear contenedores con todas las configuraciones necesarias para que una aplicación funcione correctamente.

## Pasos de Instalación:

1. **Descargar e Instalar Docker:** Descarga e instala Docker desde [este enlace](https://www.docker.com/get-started/).

2. **Configurar la Memoria de Docker:** Abre Docker y configura la memoria a 4 GB, ya que es un requisito para SQL Server.

   ![Docker](/Main-insights-and-learnings/9-SQLServer/img/docker.png)

3. **Obtener la Imagen de SQL Server:** Ejecuta el siguiente comando en la línea de comandos para descargar la imagen de SQL Server:

     ```bash
     sudo docker pull mcr.microsoft.com/mssql/server:2019-latest
     ```

4. **Iniciar el Contenedor de SQL Server:** Utiliza el siguiente comando para correr la imagen de SQL Server, acepta los términos de la licencia, establece la contraseña del usuario "sa" (debe ser compleja; debe tener al menos 8 caracteres y contener 3 de los siguientes 4 conjuntos: mayúsculas, minúsculas, dígitos y símbolos, de lo contrario no funcionará) y define el puerto:

     ```bash
     docker run -d --name sql_server_mac -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=miContrasena123+' -p 1433:1433 mcr.microsoft.com/mssql/server:2019-latest
     ```

5. **Verificar el Estado de SQL Server:** Ejecuta el siguiente comando para comprobar que SQL Server está en funcionamiento:

     ```bash
     docker ps -a
     ```

     El estado debe ser "Up". Si no está corriendo, revisa los logs con:

     ```bash
     docker logs [primeras 4 letras del Container ID]
     ```
     
     Ejemplo:
     
     ```bash
     docker logs 34b1
     ```

6. **Alternativas para la Gestión de SQL Server en Mac:**

   - **Azure Data Studio:** Utiliza [Azure Data Studio](https://docs.microsoft.com/en-us/sql/azure-data-studio/download-azure-data-studio?view=sql-server-ver15) como una alternativa al SQL Management Studio en Mac.

   - **Visual Studio Code:** Puedes utilizar la extensión de SQL Server (`mssql`) en Visual Studio Code para gestionar y consultar la base de datos.

   ![Docker](/Main-insights-and-learnings/9-SQLServer/img/sqlserver-vsc.png)