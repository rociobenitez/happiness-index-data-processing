# Apache Hive

Apache Hive es una infraestructura de almacenamiento de datos construida sobre Hadoop para proporcionar agrupación, consulta y análisis de datos. Es un software que facilita la lectura, escritura y gestión de grandes conjuntos de datos que residen en un almacenamiento distribuido utilizando SQL. Hive actúa como una base de datos de metadatos y presenta varias similitudes y diferencias en comparación con las bases de datos tradicionales.

**Similitudes**:

- **Lenguaje de consulta**: Hive implementa una variante del SQL llamada HQL (Hive Query Language). Esto significa que los usuarios pueden consultar los datos en Hadoop utilizando un lenguaje similar al SQL, lo que facilita la adopción por parte de aquellos familiarizados con SQL.

- **Facilita la gestión de grandes conjuntos de datos**: Al igual que las bases de datos tradicionales, Hive permite a los usuarios leer, escribir y administrar grandes volúmenes de datos, incluso si estos residen en un almacenamiento distribuido, como HDFS.

- **Reducción de la complejidad de MapReduce**: Hive reduce la complejidad de la programación MapReduce al permitir a los usuarios expresar sus consultas en HQL en lugar de escribir código MapReduce a nivel de programación.

**Diferencias**:

- **Orientado a aplicaciones de Data Warehouse**: Hive está orientado a aplicaciones de tipo Data Warehouse, con datos estáticos y poco cambiantes. No es adecuado para aplicaciones que requieren tiempos de respuesta rápidos o consultas en tiempo real.

- **Gestión de almacenamiento y formato de datos**: Hive permite a los usuarios despreocuparse de en qué formato y dónde se almacenan los datos, ya que se encarga de gestionar el almacenamiento. Hive almacena datos en tablas y permite su consulta a través de HQL.

- **Limitaciones en SQL**: Hive tiene un soporte SQL limitado en comparación con bases de datos relacionales. No admite subconsultas, transacciones ni índices, lo que lo hace menos adecuado para aplicaciones que requieren transacciones y consultas complejas.

## Componentes 🧩

![Arquitectura Hive](/Main-insights-and-learnings/6-Hive/img/hive-arq.png)

### Hive Server

HiveServer 2 (HS2) es la versión más reciente del servicio, permitiendo a clientes externos ejecutar consultas contra Apache Hive y obtener resultados. Utiliza Thrift RPC, admite clientes concurrentes y se inicia con el comando `hiveserver2`, escuchando en el puerto 10000.

```bash
iabd@iabd-virtualbox:~$ hiveserver2
2023-01-20 09:39:51: Iniciando HiveServer2
SLF4J: La ruta de clase contiene múltiples implementaciones de SLF4J.
SLF4J: ...
ID de sesión Hive = 9e39b0c8-45a6-46ca-bfb0-6e320c85f989
```

Conéctate a este servidor utilizando la herramienta *Beeline (Beeline CLI)*.

### Hive Metastore

Es el **repositorio central para los metadatos de Hive**, almacenado en una *base de datos relacional* como MySQL, PostgreSQL o Apache Derby (incorporado). Gestiona metadatos, tablas y tipos mediante ***Hive DDL (Lenguaje de Definición de Datos)***. El metastore se puede configurar para almacenar estadísticas de operaciones y registros de autorización para optimizar consultas.

En versiones recientes de Hive, el metastore se puede desplegar de forma remota e independiente, evitando compartir la misma JVM con HiveServer. Incluye el Catálogo de Hive (HCatalog), que proporciona acceso a los metadatos como una API. Al poder desplegarse de forma independiente, otras aplicaciones pueden utilizar el esquema sin necesidad de desplegar el motor de consultas de Hive. En la sesión del Catálogo de Spark, veremos cómo herramientas externas acceden y utilizan los metadatos almacenados.

Accede al Metastore utilizando *HiveCLI* o de forma remota a través de *Hive Server mediante Beeline*.

### Beeline

Hive incluye Beeline, un cliente basado en **JDBC para consultas de línea de comandos** contra Hive Server. Funciona sin dependencias de Hive, y puedes usar el siguiente comando:

```bash
iabd@iabd-virtualbox:~$ beeline
SLF4J: La ruta de clase contiene múltiples implementaciones de SLF4J.
SLF4J: ...
Beeline versión 3.1.2 de Apache Hive
beeline>
```

Alternativamente, puedes usar *Hive CLI*, un cliente basado en *Apache Thrift* que utiliza los mismos controladores que Hive.


## Tipos de datos 💻

En Hive, los tipos de datos son similares a los utilizados en el DDL de SQL. Los **tipos simples** comunes incluyen `STRING` e `INT`, aunque también se pueden usar otros como `TINYINT, BIGINT, DOUBLE, DATE, TIMESTAMP`, entre otros.

Para realizar conversiones explícitas de tipos, como de texto a numérico, se emplea la función CAST:

```sql
SELECT CAST('1' AS INT) FROM tablaPruebas;
```

En cuanto a los **tipos compuestos**, existen tres:

1. Arrays con el tipo `ARRAY`, para agrupar elementos del mismo tipo: `["manzana", "pera", "naranja"]`.
2. Mapas con el tipo `MAP`, para definir parejas clave-valor: `{1: "manzana", 2: "pera"}`.
3. Estructuras con el tipo `STRUCT`, para definir objetos con propiedades: `{"fruta": "manzana", "cantidad": 1, "tipo": "postre"}`.
```

## Ejemplos de comandos HiveQL 👩🏼‍💻

- Crear una tabla:

    ```sql
    CREATE TABLE empleados (id INT, nombre STRING, salario DOUBLE);
    ```

- Cargar datos en una tabla desde un archivo:

    ```sql
    LOAD DATA LOCAL INPATH '/ruta/al/archivo/datos.txt' OVERWRITE INTO TABLE empleados;
    ```

- Realizar una consulta:

    ```sql
    SELECT nombre, salario FROM empleados WHERE salario > 50000;
    ```

- Crear una nueva tabla a partir de una consulta:

    ```sql
    CREATE TABLE empleados_mayor_salario AS
    SELECT nombre, salario FROM empleados WHERE salario > 50000;
    ```

- Agregar datos a una tabla existente:

    ```sql
    INSERT INTO TABLE empleados VALUES (101, 'Juan', 60000);
    ```

- Unir dos tablas:

    ```sql
    SELECT e.nombre, d.departamento
    FROM empleados e
    JOIN departamentos d ON e.departamento_id = d.id;
    ```


## Creación de la base de datos y la tabla en Hive 💻

En Hive, puedes definir la estructura de tus tablas, incluyendo el formato y la ubicación en HDFS. Algunas de las especificaciones comunes incluyen:

   - `ROW FORMAT DELIMITED`: Indica que la tabla tiene un archivo cuyo contenido está delimitado.
   - `FIELDS TERMINATED BY '|'`: Especifica que los campos de la tabla están separados por el carácter "|".
   - `LINES TERMINATED BY '\n'`: Indica que cada registro en la tabla está separado por un salto de línea (ENTER).
   - `STORED AS TEXTFILE`: Define el formato del archivo como TEXTFILE, lo que significa que los datos en HDFS serán legibles por un humano.

Ejemplo de creación de tabla en Hive con estas especificaciones:

```sql
CREATE TABLE MIUSUARIO_TEST.PERSONA (
    ID STRING,
    NOMBRE STRING,
    TELEFONO STRING,
    CORREO STRING,
    FECHA_INGRESO STRING,
    EDAD INT,
    SALARIO DOUBLE,
    ID_EMPRESA STRING
)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY '|'
LINES TERMINATED BY '\n'
STORED AS TEXTFILE;
```

## Ubicación de la base de datos y la tabla en HDFS 💻

- Por defecto, Hive crea bases de datos y tablas en la ruta HDFS "/user/hive/warehouse". Hive automáticamente convierte el nombre de la base de datos y la tabla a minúsculas y agrega ".db" a la base de datos en HDFS. Por ejemplo, "MIUSUARIO_TEST" se convierte en "miusuario_test.db".
- Para listar el contenido de la carpeta de una base de datos en HDFS, puedes usar el comando `hdfs dfs -ls`:

  ```bash
  hdfs dfs -ls /user/hive/warehouse/miusuario_test.db
  ```

- Dentro de la carpeta de la base de datos, puedes ver la carpeta de la tabla:

  ```bash
  hdfs dfs -ls /user/hive/warehouse/miusuario_test.db/persona
  ```

### Cambiar la ubicación de la base de datos y la tabla en HDFS

- Puedes especificar una ubicación personalizada para la base de datos y la tabla en HDFS al crearlas en Hive. Por ejemplo, crear una base de datos llamada "MIUSUARIO_TEST2" en la ruta HDFS "/user/miusuario/bd":

  ```sql
  CREATE DATABASE MIUSUARIO_TEST2 LOCATION "/user/miusuario/bd/miusuario_test2";
  ```

- Luego, al crear la tabla, puedes especificar la ubicación personalizada para la tabla en HDFS:

  ```sql
  CREATE TABLE MIUSUARIO_TEST2.PERSONA (
      ...
  )
  LOCATION '/user/miusuario/bd/miusuario_test2/persona';
  ```

Esto te permite controlar dónde se almacenan los datos de tus tablas en HDFS en lugar de utilizar la ubicación predeterminada de Hive. Además, tienes la capacidad de cargar datos en la tabla y realizar operaciones en ella según tus necesidades.

Si deseas realizar operaciones específicas en Hive, como la creación de tablas en ubicaciones personalizadas, el uso de tablas "EXTERNAL" o la manipulación de datos en HDFS, es importante tener un conocimiento sólido de HiveQL y HDFS para administrar y analizar tus datos de manera efectiva.

### Eliminar una tabla

```sql
DROP TABLE MIUSUARIO_TEST2.PERSONA;
```

### Explicación

Cuando ejecutas el comando `DROP TABLE`, Hive elimina la definición de la tabla y todos sus metadatos, incluida la estructura de la tabla y la información sobre la ubicación de los datos. Sin embargo, lo que sucede con la ruta y el archivo HDFS depende del tipo de tabla que hayas creado:

- Si la tabla es **"INTERNAL"**, como suele ser la configuración predeterminada, Hive también eliminará todos los datos relacionados con la tabla en el sistema de archivos distribuido HDFS. En otras palabras, se eliminará la carpeta y los archivos de datos asociados con la tabla en HDFS.

- Si la tabla es **"EXTERNAL"**, la eliminación de la tabla en Hive no afectará los datos en HDFS. Los datos seguirán existiendo en la ruta especificada al crear la tabla. Hive solo eliminará los metadatos relacionados con la tabla.

A continuación, se muestra un ejemplo de cómo verificar el estado de la ruta HDFS después de eliminar una tabla:

```bash
-- Supongamos que la base de datos es MIUSUARIO_TEST2 y la tabla es PERSONA
-- Verificamos la ruta de la base de datos en HDFS
hdfs dfs -ls /user/miusuario/bd/miusuario_test2

-- Verificamos la ruta de la tabla en HDFS
hdfs dfs -ls /user/miusuario/bd/miusuario_test2/persona
```

### Consideraciones adicionales 

- Para eliminar todo el contenido de una tabla, puedes utilizar `TRUNCATE TABLE MI_BASE_DE_DATOS.MI_TABLA`. Sin embargo, este comando no funciona sobre tablas "EXTERNAL". En ese caso, debes utilizar `hdfs dfs -rm -r -f /ruta/a/mi/tabla/*` para eliminar los archivos HDFS de la tabla "EXTERNAL".

- Si deseas eliminar una base de datos, puedes utilizar `DROP DATABASE MI_BASE_DE_DATOS`. Esto solo funcionará si la base de datos no contiene tablas. Si hay tablas en la base de datos, debes ejecutar `DROP DATABASE MI_BASE_DE_DATOS CASCADE`.

- Puedes agregar validadores "IF EXISTS" o "IF NOT EXISTS" en algunas sentencias para verificar si algo existe antes de ejecutar la sentencia. Por ejemplo, `CREATE DATABASE IF NOT EXISTS MI_BASE_DE_DATOS`, `CREATE TABLE IF NOT EXISTS MI_BASE_DE_DATOS.MI_TABLA`, `DROP TABLE IF EXISTS MI_BASE_DE_DATOS.MI_TABLA`, `DROP DATABASE IF EXISTS MI_BASE_DE_DATOS`. Estos validadores ayudan a evitar errores cuando trabajas con bases de datos y tablas en Hive.

Recuerda que la forma en que se gestionan los datos en Hive depende de si la tabla es "INTERNAL" o "EXTERNAL". La elección del tipo de tabla dependerá de tus necesidades de retención de datos en HDFS.


## Enlaces de interés 🔗

- [Web oficial Apache Hive](https://hive.apache.org/)
- [Hive en Docker](https://hub.docker.com/r/apache/hive)
- [Hive](https://aitor-medrano.github.io/iabd2223/hadoop/06hive.html)