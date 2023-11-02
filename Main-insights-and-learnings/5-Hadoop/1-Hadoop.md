# Introducción a Hadoop: Manipulación de Datos con HDFS

[Hadoop](https://hadoop.apache.org/) es un framework de código abierto que permite el procesamiento y almacenamiento distribuido de grandes conjuntos de datos en clústeres de servidores. Uno de los componentes centrales de Hadoop es el **Sistema de Archivos Distribuido Hadoop (HDFS)**, que permite el almacenamiento y la recuperación eficiente de datos en un entorno de clúster. Vamos a explorar los conceptos básicos de HDFS y cómo interactuar con él a través de la línea de comandos.

## Características

- Distribuido
- Escalable
- Tolerante a fallos
- Open-source

## Sintaxis Básica de un Comando HDFS

Antes de sumergirnos en la manipulación de archivos en HDFS, es importante comprender la sintaxis básica de un comando HDFS. Los comandos de HDFS siguen la siguiente estructura:

```
hdfs dfs comando parametros_del_comando
```

Donde:

- `hdfs` indica que estamos utilizando la consola de HDFS.
- `dfs` indica que queremos manipular los archivos en HDFS (dfs = distribuited filesystem).
- `comando` es el comando que deseamos ejecutar en HDFS, como por ejemplo el comando `-ls` que se utiliza para listar el contenido de una carpeta en HDFS.
- `parámetros_del_comando` son los parámetros asociados al comando, por ejemplo, si el comando fuera `-mkdir`, el parámetro sería el nombre de la carpeta que se crea.

## La Carpeta Raíz de HDFS

HDFS es un sistema de archivos distribuido, lo que significa que tiene una carpeta raíz `/` donde se encuentran todas las demás carpetas y archivos. La carpeta raíz se representa con una barra diagonal.

## Listar el Contenido de una Carpeta

Para listar el contenido de una carpeta en HDFS, utilizamos el comando `-ls`. Por ejemplo:

```
hdfs dfs -ls /
```

Este comando listará el contenido de la carpeta raíz de HDFS, mostrando información sobre los archivos y subcarpetas presentes.

## Creación de Carpetas

Puedes crear una carpeta en HDFS con el comando `-mkdir`. Por ejemplo:

```
hdfs dfs -mkdir /example/carpeta1
```

Este comando crea una carpeta llamada `carpeta1` dentro de la carpeta `/example` en HDFS.

Si deseas crear una carpeta y sus subcarpetas de manera recursiva, puedes usar la opción `-p`, como se muestra a continuación:

```
hdfs dfs -mkdir -p /example/carpeta2/carpetaA/carpetaB/carpetaC
```

Este comando crea toda la estructura de carpetas, incluidas las subcarpetas, si no existen.

## Creación de un Archivo Vacío

Puedes crear un archivo vacío en HDFS con el comando `-touchz`. Por ejemplo:

```
hdfs dfs -touchz /example/archivo_vacio.txt
```

Este comando crea un archivo vacío llamado `archivo_vacio.txt` en la carpeta `/example` en HDFS.

## Subiendo Archivos a HDFS

HDFS te permite subir archivos desde tu sistema local al sistema distribuido. Puedes usar el comando `-put` para lograrlo. Por ejemplo:

```
hdfs dfs -put /ruta/archivo_local.txt /example/
```

Este comando sube el archivo local `archivo_local.txt` a la carpeta `/example` en HDFS.

## Viendo el Contenido de los Archivos

Para ver el contenido de un archivo en HDFS, utiliza el comando `-cat`. Por ejemplo:

```
hdfs dfs -cat /example/archivo_vacio.txt
```

Este comando muestra el contenido del archivo `archivo_vacio.txt` en la carpeta `/example` de HDFS.

## Eliminando Recursos en HDFS

Puedes eliminar archivos y carpetas en HDFS utilizando el comando `-rm`. Por ejemplo, para eliminar un archivo:

```
hdfs dfs -rm /example/archivo_vacio.txt
```

Para eliminar recursos que cumplan un patrón, puedes utilizar el comodín `*`. Por ejemplo:

```
hdfs dfs -rm /example/transacciones*.data
```

Este comando eliminará todos los archivos en la carpeta `/example` que coincidan con el patrón `transacciones*.data`.

Para eliminar una carpeta y su contenido de manera recursiva, utiliza el comando `-rm -r -f`. Por ejemplo:

```
hdfs dfs -rm -r -f /example/carpeta1
```

Este comando eliminará la carpeta `carpeta1` y todo su contenido de manera recursiva.

## Conclusion

**HDFS** es un componente fundamental de Hadoop que permite el almacenamiento y la gestión de grandes volúmenes de datos de manera distribuida. Con los comandos básicos de HDFS, puedes manipular archivos y carpetas de manera eficiente en un entorno de clúster.