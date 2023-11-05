# Hive en Docker

Hive es una herramienta de big data que permite consultar y analizar datos almacenados en Hadoop Distributed File System (HDFS) utilizando SQL-like queries. Puedes ejecutar Hive dentro de un contenedor Docker en modo pseudodistribuido siguiendo estos pasos.

## Inicio Rápido

### Paso 1: Extraer la Imagen 🐝

Extrae la imagen de DockerHub: [Repositorio de Apache Hive en DockerHub](https://hub.docker.com/r/apache/hive/tags). Actualmente, hay varias imágenes disponibles. Por ejemplo, para extraer la versión 4.0.0-alpha-2:

```bash
docker pull apache/hive:4.0.0-alpha-2
```

### Paso 2: Exportar la Versión de Hive 🐝

Define la versión de Hive en una variable de entorno. Por ejemplo:

```bash
export HIVE_VERSION=4.0.0-alpha-2
```

### Paso 3: Iniciar HiveServer2 con un Metastore Integrado 🐝

Para una configuración rápida, puedes iniciar HiveServer2 con un Metastore ligero que utiliza Derby como base de datos. Ejecuta el siguiente comando:

```bash
docker run -d -p 10000:10000 -p 10002:10002 --env SERVICE_NAME=hiveserver2 --name hive4 apache/hive:${HIVE_VERSION}
```

### Paso 4: Conéctese a Beeline 🐝

Puedes conectarte a Hive utilizando Beeline desde el contenedor. Ejecuta:

```bash
docker exec -it hiveserver2 beeline -u 'jdbc:hive2://hiveserver2:10000/'
```

### Nota: Iniciar Metastore Independiente

Si deseas utilizar un Metastore independiente con Derby, puedes ejecutar:

```bash
docker run -d -p 9083:9083 --env SERVICE_NAME=metastore --name metastore-standalone apache/hive:${HIVE_VERSION}
```

## Uso

### HiveServer2 en la Web

Accede a HiveServer2 en tu navegador en http://localhost:10002/.

### Línea de Comandos

Para acceder a HiveServer2 desde la línea de comandos:

```bash
docker exec -it hiveserver2 beeline -u 'jdbc:hive2://hiveserver2:10000/'
# O, si Beeline está instalado en tu máquina local
beeline -u 'jdbc:hive2://localhost:10000/'
```

Se mostrará la versión de Beeline utilizada:

```
Beeline version 2.3.9 by Apache Hive
```

Ejecuta algunas consultas de Hive para comenzar a trabajar con tus datos.

## Nota

Recuerda que esta documentación se basa en las instrucciones proporcionadas en la [documentación oficial de Apache Hive](https://hive.apache.org/developement/quickstart/) y puede estar sujeta a cambios. Asegúrate de consultar la documentación más reciente para obtener detalles actualizados.