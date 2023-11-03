En HDFS (Hadoop Distributed File System), encontramos los siguientes elementos:

## Namenodes

1. **Namenode**: 
   - Existe un ***único*** `Namenode` que sirve como **servidor principal**.
   - Los clientes se conectan a este nodo para realizar **lecturas y escrituras**.
   - Mantiene el árbol del sistema de archivos y los metadatos de todos los archivos y directorios, incluyendo la ubicación de los bloques de datos.
   - **Almacena metadatos tanto en memoria como en disco**, lo que requiere una cantidad significativa de memoria RAM.
   - No es responsable de almacenar o transferir los datos reales (bloques de datos).
   - La **caída** del Namenode **impide el acceso a HDFS**, por lo que es esencial mantener copias de seguridad.

2. **Secondary Namenode**:
   - Su función principal es ***guardar copias de seguridad de los metadatos*** del sistema de archivos, como FsImage y EditLog.
   - No es un nodo de respaldo.
   - Generalmente se ejecuta en una máquina diferente.
   - Además de distribuir los bloques de datos, replica los datos para garantizar su disponibilidad en caso de fallos.

Dicho de otra manera, el `Namenode` es esencial para la operación de HDFS y almacena metadatos críticos, mientras que el `Secondary Namenode` no es un respaldo del Namenode, pero juega un papel importante en la protección de los metadatos. Estos nodos **trabajan juntos** para mantener y gestionar el sistema de archivos distribuidos. HDFS se utiliza en implementaciones a gran escala, como en Facebook, donde gestionan un clúster masivo con miles de nodos y petabytes de almacenamiento.



## Datanodes

- Puede haber ***varios*** Datanodes en un clúster HDFS, con múltiples Datanodes por cada Namenode.
- Almacenan y leen bloques de datos reales.
- Informan al Namenode sobre la lista de bloques que están almacenando.
- Los bloques de datos pueden estar distribuidos en diferentes discos.
- Los Datanodes también almacenan un checksum (suma de verificación) para cada bloque.

### Procesos de Lectura

1. El cliente abre un archivo que desea leer mediante el método `open()` del sistema de archivos distribuido.
2. El Namenode, a través de una llamada RPC, indica al cliente la ubicación del primer bloque del archivo y la lista de Datanodes que tienen copias de ese bloque.
3. El cliente obtiene un `FSDataInputStream` que le permite leer los datos y se conecta al Datanode más cercano.
4. Los datos se leen desde el Datanode mediante llamadas al método `read()`. Una vez que se completa la lectura de un bloque, el flujo de datos cambia al Datanode siguiente.
5. Este proceso continúa hasta que el cliente completa la lectura y cierra la conexión con el flujo de datos. Se gestionan errores y reintentos automáticamente.

### Proceso de Escritura

1. El cliente crea un archivo utilizando el método `create()` del `DistributedFileSystem`.
2. Se realiza una llamada RPC al Namenode para crear el archivo en el sistema de archivos del Namenode. En este punto, no hay bloques asociados al archivo. El Namenode determina cómo dividir los datos en bloques y qué Datanodes utilizar.
3. El cliente obtiene un `FSDataOutputStream` que se encarga de gestionar la comunicación con los Datanodes y el Namenode para que el cliente pueda comenzar a escribir datos en el lugar adecuado.
4. A medida que el cliente escribe datos, el flujo de datos obtiene una lista de Datanodes candidatos para almacenar las réplicas. Estos nodos forman un "pipeline", y los datos se envían secuencialmente a través de cada Datanode en el pipeline.
5. Una vez que todos los Datanodes confirman la recepción y el almacenamiento de los datos, se envía una confirmación al flujo de datos.
6. Cuando el cliente finaliza la escritura de los datos, cierra el flujo de datos, lo que libera los paquetes pendientes al pipeline de Datanodes. El Namenode se informa de la finalización de la escritura y de los bloques finales que componen el archivo.

Estos procesos de lectura y escritura aseguran la integridad y disponibilidad de los datos almacenados en HDFS. Los Datanodes juegan un papel fundamental al almacenar y recuperar los bloques de datos en el clúster.

## HDFS por dentro

HDFS opera con un conjunto de archivos que gestionan los cambios en el clúster. Para entender cómo funciona, podemos explorar la carpeta de datos configurada para el Namenode en el archivo `hdfs-site.xml`. Supongamos que esta carpeta está en `/opt/hadoop-data/hdfs/namenode`.

Dentro de esta carpeta, encontraremos una carpeta llamada "current," que contiene una serie de archivos con nombres que siguen ciertos patrones:

- `edits_000NNN`: Estos archivos registran un histórico de cambios que ocurren en HDFS.
- `edits_inprogress_NNN`: Estos archivos contienen los cambios actuales en memoria que aún no se han guardado de manera permanente.
- `fsimage_000NNN`: Estos archivos son instantáneas en el tiempo del sistema de archivos.

Cuando HDFS se inicia, el sistema carga en memoria el último archivo "fsimage" disponible, junto con los "edits" que aún no se han procesado. El Secondary Namenode se encarga de sincronizar los cambios que se encuentran en "edits_inprogress" y crear un nuevo "fsimage" cada vez que se llena un bloque.

Cada vez que el Namenode se reinicia, realiza una operación de fusión (merge) entre los archivos "fsimage" y el registro de cambios "edits log," lo que garantiza que el sistema de archivos se encuentre en un estado coherente y actualizado.


## Trabajando con HDFS

Para interactuar con el sistema de archivos HDFS desde la línea de comandos, utilizamos el comando `hdfs`. Este comando ofrece varias opciones a las que podemos acceder a través de un segundo parámetro.

Es importante destacar que, ante cualquier duda o consulta, es recomendable consultar la documentación oficial de Hadoop para obtener información precisa y actualizada.

Hasta ciertas versiones anteriores, se empleaba el comando `hadoop fs` para acceder al sistema de archivos genérico que podía apuntar a diversas fuentes, como sistemas locales, HDFS, FTP, S3, entre otros. Sin embargo, este enfoque se ha vuelto obsoleto y ha sido reemplazado por `hdfs dfs` para interactuar específicamente con el sistema de archivos Hadoop.

Para utilizar el comando `hdfs dfs`, debemos agregar un segundo argumento precedido por un guion, que corresponderá a uno de los comandos del shell de Linux para realizar diversas operaciones. La **lista completa de estos comandos** está disponible en la [documentación oficial](https://hadoop.apache.org/docs/current/hadoop-project-dist/hadoop-hdfs/HDFSCommands.html).

Algunos de los **comandos más comunes** incluyen:

- `put` (o `copyFromLocal`): Utilizado para transferir un archivo al sistema de archivos HDFS.
- `get` (o `copyToLocal`): Permite recuperar un archivo de HDFS y llevarlo de regreso a nuestro sistema local.
- `cat`, `text`, `head`, `tail`: Estos comandos se utilizan para visualizar el contenido de un archivo.
- `mkdir` y `rmdir`: Permiten crear o eliminar una carpeta, respectivamente.
- `count`: Proporciona información sobre el número de elementos en una ubicación, incluyendo la cantidad de carpetas, archivos, tamaño y rutas.
- `cp`, `mv` y `rm`: Se utilizan para copiar, mover-renombrar o eliminar un archivo, respectivamente.