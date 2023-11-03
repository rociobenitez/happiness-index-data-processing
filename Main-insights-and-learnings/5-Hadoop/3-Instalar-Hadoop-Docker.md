## Configuración de Hadoop con Docker

En este módulo, hemos decidido configurar nuestro clúster de Hadoop utilizando Docker, una herramienta eficiente para crear y gestionar un entorno de desarrollo de Big Data. A continuación, describimos los pasos que hemos seguido para poner en marcha nuestro clúster de Hadoop.

### 1. Descarga de la imagen de Hadoop

Primero, instalamos y probamos Hadoop 2.7 a partir de la siguiente operación:

```bash
docker ps
```

Utilizamos Docker para obtener una imagen de Hadoop desde el registro de Docker Hub. Ejecutamos el siguiente comando para descargar la imagen:

```bash
sudo docker pull sequenceiq/hadoop-docker:2.7.1
```

Esto nos proporciona una imagen de Hadoop preconfigurada que incluye componentes YARN, como el administrador de nodos, el administrador de recursos y el servidor de historial.

### 2. Verificación de la imagen

Para comprobar si la descarga de la imagen se realizó con éxito, ejecutamos el siguiente comando:

```bash
docker images
```

Esto mostrará la lista de imágenes Docker en su sistema, y la imagen de Hadoop debe estar presente.

![Images Docker](/Main-insights-and-learnings/5-Hadoop/img/docker-images.png)

### 3. Creación del contenedor de Hadoop

Ahora tienes dos opciones para configurar tu entorno de desarrollo con Hadoop.

#### Opción 1: Ejecutar un solo contenedor

Creamos un contenedor Docker que ejecutará Hadoop. Utilizamos el siguiente comando para iniciar un contenedor que aloja todos los componentes de Hadoop en un solo clúster:

```bash
docker run -it sequenceiq/hadoop-docker:2.7.1 /etc/bootstrap.sh -bash
```

#### Opción 2: Configurar un contenedor en diferentes puertos

El siguiente comando inicia un contenedor de Hadoop y lo expone en los puertos 50070 y 8088, lo que te permite acceder a diferentes servicios de Hadoop a través de tu máquina local en esos puertos.

```bash
docker run -p 50070:50070 -p 8088:8088 -it sequenceiq/hadoop-docker:2.7.1 /bin/bash -bash
```

Estos comandos inician el clúster de Hadoop y nos permiten trabajar con él desde dentro del contenedor.

Estas opciones te permiten configurar un entorno de desarrollo de Hadoop de manera eficaz y centrarte en el procesamiento y análisis de datos en lugar de perder tiempo en la administración del clúster.

### 4. Verificación de los servicios de Hadoop

Para confirmar que los servicios de Hadoop están en funcionamiento, ejecutamos el siguiente comando:

```bash
jps
```

Esto lista los procesos Java en ejecución y muestra que los contenedores están configurados para servicios como NodeManager, DataNode, ResourceManager y NameNode.

![jps terminal](/Main-insights-and-learnings/5-Hadoop/img/jps-docker.png)

### 5. Verificación de los contenedores en ejecución

Finalmente, para garantizar que todo esté configurado y funcionando correctamente, ejecutamos el siguiente comando:

```bash
docker ps
```

Este comando nos muestra los contenedores Docker que están actualmente en ejecución y confirma que nuestra configuración del clúster de Hadoop está lista y operativa.

![Containers Docker Desktop](/Main-insights-and-learnings/5-Hadoop/img/docker-containers.png)

Utilizando esta estrategia, podemos establecer un entorno de desarrollo de Hadoop de manera eficaz y centrarnos en el procesamiento y análisis de datos en lugar de perder tiempo en la administración del clúster.


## Cómo cambiar el Nombre de un Contenedor Docker 📝

Puedes cambiar el nombre de un contenedor Docker fácilmente utilizando el comando `docker rename`. Por ejemplo, si deseas cambiar el nombre de un contenedor llamado `competent_bohr` a `hadoop`, puedes hacerlo de la siguiente manera:

```bash
docker rename competent_bohr hadoop
```

En este comando, `competent_bohr` es el nombre original del contenedor y `hadoop` es el nuevo nombre que deseas asignar. Después de ejecutar el comando, el contenedor tendrá el nuevo nombre.

## Verificando el Proceso 🔍

Para verificar que el cambio de nombre se ha realizado con éxito, puedes utilizar el siguiente comando para listar todos los contenedores en tu sistema:

```bash
docker ps -a
```

Este comando mostrará una lista de todos los contenedores, junto con su nombre actual. Asegúrate de buscar el nuevo nombre, en este caso, `hadoop`, para confirmar que el cambio de nombre se ha aplicado correctamente.

![Containers Docker Desktop](/Main-insights-and-learnings/5-Hadoop/img/docker-ps-a.png)

Con estos pasos, puedes cambiar el nombre de un contenedor Docker y verificar que el proceso se haya completado con éxito. Esto puede ser útil para organizar tus contenedores y darles nombres más descriptivos.