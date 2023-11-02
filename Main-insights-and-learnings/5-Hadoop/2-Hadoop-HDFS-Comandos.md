# Hadoop HDFS Comandos

A continuación, se presentan una serie de comandos que te permitirán interactuar con el *Sistema de Archivos Distribuido Hadoop (HDFS)*. Estos comandos son esenciales para gestionar archivos y directorios en HDFS y realizar diversas operaciones de administración en un entorno de clúster Hadoop.

## Listar Archivos y Directorios

### Listar Archivos y Directorios
```
hdfs dfs -ls /
```
Este comando lista todos los archivos y directorios en la ubicación especificada en HDFS. En este caso, se muestra el contenido de la raíz de HDFS.

### Listar Directorios como Archivos
```
hdfs dfs -ls -d /hadoop
```
Este comando lista los directorios como si fueran archivos, mostrando detalles sobre el directorio especificado en HDFS. En este ejemplo, se muestra información sobre el directorio "hadoop".

### Listar con Formato Legible
```
hdfs dfs -ls -h /data
```
Este comando lista archivos y directorios en HDFS con tamaños de archivo en un formato legible por humanos, como "64.0m" en lugar de "67108864". Facilita la comprensión de los tamaños de archivo.

### Listar Recursivamente
```
hdfs dfs -ls -R /hadoop
```
Este comando lista de manera recursiva todos los archivos en un directorio Hadoop y sus subdirectorios. Es útil para explorar la estructura de carpetas completa.

### Listar Archivos por Patrón
```
hdfs dfs -ls /hadoop/dat*
```
Este comando lista todos los archivos que coinciden con un patrón específico. En este caso, se listarán todos los archivos dentro del directorio "hadoop" que comiencen con "dat".

## Leer/Escribir Archivos

### Leer Archivo en Formato de Texto
```
hdfs dfs -text /hadoop/derby.log
```
Este comando toma un archivo fuente y muestra su contenido en formato de texto en la terminal. Los formatos permitidos son "zip" y "TextRecordInputStream".

### Mostrar Contenido del Archivo
```
hdfs dfs -cat /hadoop/test
```
Este comando muestra el contenido del archivo especificado en HDFS en la salida estándar. Es útil para visualizar el contenido de un archivo en HDFS.

### Adjuntar Contenido a un Archivo
```
hdfs dfs -appendToFile /home/ubuntu/test1 /hadoop/text2
```
Este comando agrega el contenido de un archivo local llamado "test1" a un archivo en HDFS llamado "text2". Permite la concatenación de archivos.

## Subir/Descargar Archivos

### Subir un Archivo a HDFS
```
hdfs dfs -put /home/ubuntu/sample /hadoop
```
Este comando copia un archivo desde el sistema de archivos local a HDFS. En este ejemplo, se copia el archivo "sample" desde el sistema local a la carpeta "hadoop" en HDFS.

### Subir con Sobrescritura
```
hdfs dfs -put -f /home/ubuntu/sample /hadoop
```
Este comando copia un archivo desde el sistema de archivos local a HDFS y, en caso de que el archivo local ya exista en la ubicación de destino, sobrescribirá el archivo existente.

### Subir con Conservación de Metadatos
```
hdfs dfs -put -p /home/ubuntu/sample /hadoop
```
Este comando copia un archivo desde el sistema de archivos local a HDFS, conservando metadatos como tiempos de acceso, propiedad y permisos.

### Descargar un Archivo desde HDFS
```
hdfs dfs -get /newfile /home/ubuntu/
```
Este comando copia un archivo desde HDFS al sistema de archivos local. En este caso, se copia el archivo "newfile" desde HDFS al directorio local "/home/ubuntu/".

### Descargar con Conservación de Metadatos
```
hdfs dfs -get -p /newfile /home/ubuntu/
```
Este comando copia un archivo desde HDFS al sistema de archivos local, conservando metadatos como tiempos de acceso, propiedad y permisos.

### Descargar Archivos por Patrón
```
hdfs dfs -get /hadoop/*.txt /home/ubuntu/
```
Este comando copia todos los archivos que coinciden con un patrón desde HDFS al sistema de archivos local. En este caso, se copiarán todos los archivos con extensión ".txt" desde el directorio "hadoop" a "/home/ubuntu/".

### Copiar desde un Origen Local
```
hdfs dfs -copyFromLocal /home/ubuntu/sample /hadoop
```
Este comando funciona de manera similar al comando "put", pero el origen está restringido a una referencia local.

### Copiar a un Destino Local
```
hdfs dfs -copyToLocal /newfile /home/ubuntu/
```
Este comando funciona de manera similar al comando "put", pero el destino está restringido a una referencia local.

### Mover desde un Origen Local
```
hdfs dfs -moveFromLocal /home/ubuntu/sample /hadoop
```
Este comando funciona de manera similar al comando "put", pero el origen se elimina después de copiarlo.

## Gestión de Archivos

### Copiar un Archivo
```
hdfs dfs -cp /hadoop/file1 /hadoop1
```
Este comando copia un archivo desde la fuente a un destino en HDFS. En este ejemplo, se copia el archivo "file1" desde el directorio "hadoop" al directorio "hadoop1".

### Copiar con Conservación de Metadatos
```
hdfs dfs -cp -p /hadoop/file1 /hadoop1
```
Este comando copia un archivo desde la fuente a un destino en HDFS, conservando metadatos como tiempos de acceso, propiedad y permisos.

### Copiar con Sobrescritura
```
hdfs dfs -cp -f /hadoop/file1 /hadoop1
```
Este comando copia un archivo desde la fuente a un destino en HDFS y sobrescribe el destino si ya existe.

### Mover Archivos
```
hdfs dfs -mv /hadoop/file1 /hadoop1
```
Este comando mueve archivos que coinciden con un patrón específico desde la fuente a un destino en HDFS. Cuando se mueven varios archivos, el destino debe ser un directorio.

### Eliminar un Archivo
```
hdfs dfs -rm /hadoop/file1
```
Este comando elimina un archivo en HDFS, enviándolo a la papelera.

### Eliminar un Directorio (Recursivo)
```
hdfs dfs -rm -r /hadoop
hdfs dfs -rm -R /hadoop
hdfs dfs -rmr /h
```
Estos comandos se utilizan para eliminar un directorio y su contenido de manera recursiva en HDFS. Se eliminan tanto los archivos como los subdirectorios.

### Eliminar sin Usar la Papelera
```
hdfs dfs -rm -skipTrash /hadoop
```
Este comando permite eliminar el archivo o directorio especificado sin enviarlo a la papelera. Si la papelera está habilitada, este comando la omite.

### Eliminar sin Mostrar Errores
```
hdfs dfs -rm -f /hadoop
```
Cuando se utiliza este comando, si el archivo o directorio no existe, no se mostrará un mensaje de error ni se modificará el estado de salida para reflejar un error.

### Eliminar un Directorio
```
hdfs dfs -rmdir /hadoop1
```
Este comando se utiliza para eliminar un directorio en HDFS. En este ejemplo, se elimina el directorio "hadoop1".

### Crear un Directorio
```
hdfs dfs -mkdir /hadoop2
```
Este comando se utiliza para crear un nuevo directorio en una ubicación específica de HDFS.

### Crear un Directorio Forzadamente
```
hdfs dfs -mkdir -f /hadoop2
```
Este comando se utiliza para crear un nuevo directorio en HDFS, incluso si el directorio ya existe en la ubicación especificada. No fallará en caso de que el directorio ya exista.

### Crear un Archivo Vacío
```
hdfs dfs -touchz /hadoop3
```
Este comando se utiliza para crear un archivo vacío en HDFS en una ubicación específica, con la hora actual como marca de tiempo del archivo.

## Propiedad y Validación

### Mostrar Información de Chequeo de Archivo
```
hdfs dfs -checksum /hadoop/file1
```
Este comando muestra información de checksum para archivos que coinciden con el patrón de archivo especificado. La información se muestra en la salida estándar.

### Cambiar Permisos de Archivo
```
hdfs dfs -chmod 755 /hadoop/file1
```
Este comando cambia los permisos del archivo en HDFS. En este ejemplo, se establecen permisos "755" para el archivo "file1".

### Cambiar Permisos de Archivos Recursivamente
```
hdfs dfs -chmod -R 755 /hadoop
```
Este comando cambia los permisos de los archivos y directorios de manera recursiva en HDFS. Los permisos "755" se aplican a todos los elementos dentro del directorio "hadoop".

### Cambiar Propietario de Archivo
```
hdfs dfs -chown ubuntu:ubuntu /hadoop/file1
```
Este comando cambia el propietario de un archivo en HDFS. El primer "ubuntu" es el propietario y el segundo "ubuntu" es el grupo.

### Cambiar Propietario de Archivos Recursivamente
```
hdfs dfs -chown -R ubuntu:ubuntu /hadoop
```
Este comando cambia el propietario de los archivos y directorios de manera recursiva en HDFS. El primer "ubuntu" es el propietario y el segundo "ubuntu" es el grupo.

## Sistema de Archivos

### Mostrar Información del Sistema de Archivos
```
hdfs dfs -df /hadoop
```
Este comando muestra la capacidad, espacio libre y espacio utilizado en el sistema de archivos. Es útil para obtener información sobre el estado del sistema de archivos HDFS.

### Mostrar Información del Sistema de Archivos con Formato Legible
```
hdfs dfs -df -h /hadoop
```
Este comando muestra la capacidad, espacio libre y espacio utilizado en el sistema de archivos en un formato legible por humanos. Los tamaños de archivo se muestran en un formato fácil de entender.

### Mostrar Uso de Espacio de Archivos
```
hdfs dfs -du /hadoop/file
```
Este comando muestra la cantidad de espacio utilizado por los archivos que coinciden con el patrón de archivo especificado. Muestra el tamaño de cada archivo individual.

### Mostrar Uso de Espacio de Archivos en Resumen
```
hdfs dfs -du -s /hadoop/file
```
En lugar de mostrar el tamaño de cada archivo individual, este comando muestra el tamaño total (resumen) de los archivos que coinciden con el patrón de archivo especificado.

### Mostrar Uso de Espacio de Archivos con Formato Legible
```
hdfs dfs -du -h /hadoop/file
```
Este comando muestra la cantidad de espacio utilizado por los archivos que coinciden con el patrón de archivo especificado en un formato legible por humanos. Los tamaños de archivo se muestran de manera legible.

## Administración

### Ejecutar el Balanceo de Clúster
```
hdfs balancer -threshold 30
```
Este comando ejecuta una utilidad de balanceo de clúster. Puede ajustar el umbral de capacidad con el valor en porcentaje. El comando sobrescribe el umbral predeterminado.

### Verificar la Versión de Hadoop
```
hadoop version
```
Este comando se utiliza para verificar la versión de Hadoop instalada en el sistema.

### Realizar una Comprobación de Salud del Sistema de Archivos
```
hdfs fsck /
```
Este comando comprueba la salud del sistema de archivos Hadoop. Proporciona información detallada sobre el estado del sistema de archivos.

### Salir del Modo Seguro de NameNode
```
hdfs dfsadmin -safemode leave
```
Este comando se utiliza para desactivar el modo seguro del NameNode, lo que permite la escritura en HDFS.

### Actualizar los Nodos
```
hdfs dfsadmin -refreshNodes
```
Este comando vuelve a leer los archivos de hosts y exclusión para actualizar el conjunto de nodos de datos permitidos para conectarse al NameNode, así como aquellos que deben ser retirados o reintegrados.

### Formatear el NameNode
```
hdfs namenode -format
```
Este comando se utiliza para formatear el NameNode en HDFS, lo que implica reiniciar el sistema de archivos.

Estos comandos son fundamentales para administrar y operar el Sistema de Archivos Distribuido Hadoop (HDFS) de manera eficaz. Pueden ser utilizados para realizar una variedad de operaciones, desde la gestión de archivos y directorios hasta la verificación del estado del sistema de archivos y la administración del clúster Hadoop.