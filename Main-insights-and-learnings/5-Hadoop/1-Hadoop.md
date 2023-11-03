# Introducción a Hadoop: Manipulación de Datos con HDFS

[Hadoop](https://hadoop.apache.org/) es un framework de código abierto que permite el ***procesamiento y almacenamiento distribuido de grandes conjuntos de datos en clústeres de servidores***. Uno de los componentes centrales de Hadoop es el **Sistema de Archivos Distribuido Hadoop (HDFS)**, que permite el almacenamiento y la recuperación eficiente de datos en un entorno de clúster. Vamos a explorar los conceptos básicos de HDFS y cómo interactuar con él a través de la línea de comandos.

## Características 📝

- **Distribuido y Escalable:** los datos y su procesamiento se distribuyen sobre un clúster de ordenadores (escalado horizontal), desde un único servidor a miles de máquinas.
- **Tolerante a fallos:** tras detectar un fallo aplica una recuperación automática.
- **Open-source**
- **Confiable:** crea múltiples copias de los datos de manera automática.
- **Portable:** se puede instalar en todo tipo de hardware y sistemas operativos.

## Procesamiento distribuido 🔀

Hadoop sigue un enfoque donde guarda y procesa datos en el mismo lugar, evitando trasladar los datos al sistema de procesamiento. Esto se logra mediante un sistema distribuido con dos tipos de nodos:

1. **Nodos maestros**: Controlan la gestión global, supervisan los trabajos y datos. Por lo general, se utilizan 3 de ellos con hardware más robusto.

2. **Nodos workers**: Manejan datos locales y procesamiento de aplicaciones. El número varía según las necesidades, desde 4 hasta miles, con hardware económico tipo servidor X86.

Además, existen los **nodos edge** que actúan como intermediarios entre el clúster y la red externa, proporcionando interfaces de comunicación.

Cada vez que añadimos un nuevo nodo worker, aumentamos tanto la capacidad como el rendimiento de nuestro sistema.

## Enlaces de interés para empezar a utilizar Hadoop 🔗

- [Amazon Elastic MapReduce(EMR)](https://aws.amazon.com/es/emr/) de AWS
- [CDH](https://www.cloudera.com/products/open-source/apache-hadoop/key-cdh-components.html) de Cloudera
- [Dataproc](https://cloud.google.com/dataproc?hl=es) de Google
- [Azure HDInsight](https://azure.microsoft.com/es-es/products/hdinsight/) de Microsoft


## HDFS 💻

Divide los archivos en bloques y los replica en múltiples nodos para garantizar la redundancia y la disponibilidad. Está optimizado para escrituras únicas y lecturas múltiples, y es **ideal para datos de entrada** utilizados en procesos de cómputo.

**No ofrece buen rendimiento para:**
- Acceder a datos de baja latencia
- Manejar ficheros pequeños
- Múltiples escritores
- Modificaciones arbitrarias de ficheros

Los datos, una vez escritos en HDFS son **immutables**. Cada fichero de HDFS solo permite añadir contenido *(append-only)*. Una vez se ha creado y escrito en él, solo podemos añadir contenido o eliminarlo. Es decir, a priori, no podemos modificar los datos.

*HBase* y *Hive* son soluciones que se construyen sobre HDFS y permiten la modificación de datos, lo que lo convierte en una capa de almacenamiento más versátil.

## Bloques 🧱

Los bloques en HDFS son ***unidades de datos mínimas que se leen o escriben***, generalmente de **128 MB** de tamaño. Los archivos se dividen en bloques, y si un archivo es más pequeño que el tamaño del bloque, ocupará solo el espacio necesario en disco.

Además, los bloques se replican para garantizar la redundancia y la disponibilidad, con un valor predeterminado de *replicación de 3*, lo que significa que un archivo de 600 MB, dividido en 5 bloques, se almacena en 15 bloques en diferentes nodos del clúster.

En HDFS, se pueden identificar **tres tipos de máquinas**:

1. **Namenode:** Actúa como el servidor principal y almacena los metadatos para construir el sistema de archivos a partir de bloques. Controla la ubicación de todos los bloques.

2. **Datanode:** Son los nodos esclavos que almacenan los bloques que componen cada archivo.

3. **Secondary Namenode:** Su función principal es tomar puntos de control de los metadatos del sistema de archivos presentes en el Namenode.

Más información sobre la arquitectura de HDFS en [HDFS-Namenodes-Datanodes.md](/Main-insights-and-learnings/5-Hadoop/5-HDFS-Namenodes-Datanodes.md).

## Instalación 👩🏼‍💻

Mi intento de [instalar Hadoop localmente en macOS](/Main-insights-and-learnings/5-Hadoop/3-Instalar-Hadoop-Mac.md) se convirtió en un desafío, ya que me encontré con varias dificultades. Una de las principales complicaciones fue el error *"Failed to retrieve data from /webhdfs/v1/?op=LISTSTATUS: Server Error"* al usar la interfaz web de Hadoop. Investigando, descubrí que este problema podría estar relacionado con una versión de Java incompatible, especialmente si se tenía una versión superior a Java 11, como se menciona en la documentación de Hadoop.

Después de luchar con estos problemas, decidí cambiar mi enfoque y opté por [instalar Hadoop en Docker](/Main-insights-and-learnings/5-Hadoop/3-Instalar-Hadoop-Docker.md). Esta elección resultó ser más sencilla y efectiva, permitiéndome evitar los obstáculos que encontré al intentar una instalación local.

## Sintaxis Básica de un Comando HDFS ⌨️

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