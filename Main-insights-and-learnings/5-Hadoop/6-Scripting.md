# Scripting en HDFS

A continuación se muestras una serie de comandos en el entorno de Hadoop Distributed File System (HDFS).

## Scripting Sencillo 👩🏼‍💻

```archivo .sh
#Listamos la raíz del sistema de archivos distribuidos
hdfs dfs -ls /

#Creamos la carpeta
hdfs dfs -mkdir /example

#Listamos el directorio de example
hdfs dfs -ls /example

#Creamos un archivo .txt
hdfs dfs -touchz /example/archivo_vacio.txt

#Listamos nuevamente el dictorio de example
hdfs dfs -ls /example
```

## Scripting Avanzado 👩🏼‍💻

### Sección 1: Listado de Carpetas

```archivo .sh
#Listamos la raíz del sistema de archivos distribuidos
hdfs dfs -ls /

#Listamos una de las carpetas
hdfs dfs -ls /example

#Listamos la carpeta "user"
#En esta carpeta cada usuario tiene una carpeta para trabajar
hdfs dfs -ls /user

#Listamos nuestra carpeta
hdfs dfs -ls /user/spark
```

En esta sección, se realizan comandos para **listar carpetas** en el sistema de archivos distribuidos. Se empieza mostrando el contenido de la raíz ("/") y luego se listan carpetas específicas como "/example", "/user", y "/user/spark".

### Sección 2: Creación de Carpetas

```archivo .sh

#Creamos una carpeta dentro de nuestra carpeta de usuario
hdfs dfs -mkdir -p /user/rocio/example

#Listamos nuestra carpeta y veremos que se ha creado "carpeta1"
hdfs dfs -ls /user/rocio

#Como cada uno de nosotros tenemos nuestro propio usuario crearemos una variable que almacene el nombre del usuario
export PARAM_USERNAME=rocio

#Vemos el contenido de la variable
echo $PARAM_USERNAME

#Listamos nuestra carpeta de usuario usando la variable
hdfs dfs -ls /user/$PARAM_USERNAME

#Creamos algunas carpetas mas
hdfs dfs -mkdir -p /user/$PARAM_USERNAME/example/carpeta1
hdfs dfs -mkdir -p /user/$PARAM_USERNAME/example/carpeta2
hdfs dfs -mkdir -p /user/$PARAM_USERNAME/example/carpeta3

#Listamos la carpeta "example"
hdfs dfs -ls -p /user/$PARAM_USERNAME/example

#Vamos a crear una estructura de carpetas anidadas dentro de example:
#
# - /user/$PARAM_USERNAME
#	- carpeta1
#		- carpetaA
#			- carpetaB
#				- carpetaC

#Trataremos de ejecutar el comando de creación
#hdfs dfs -mkdir /user/$PARAM_USERNAME/example/carpeta1/carpetaA/carpetaB/carpetaC

#Obtendremos un error
#Agregaremos un parametro para creacion recursiva de carpetas
hdfs dfs -mkdir -p /user/$PARAM_USERNAME/example/carpeta1/carpetaA/carpetaB/carpetaC

#Verificamos
hdfs dfs -ls -R /user/$PARAM_USERNAME/example
```

En esta parte, se realizan acciones relacionadas con la creación de carpetas en HDFS. Se crea una carpeta llamada "example" dentro de la carpeta del usuario llamado "rocio". Luego, se crea una estructura de carpetas anidadas y se verifica su creación.

### Sección 3: Creación de Archivos Vacíos

```archivo.sh
#Creacion de un archivo vacio con extension
hdfs dfs -touchz /user/$PARAM_USERNAME/example/archivo_vacio.txt

#Verificamos
hdfs dfs -ls /user/$PARAM_USERNAME/example
```

Esta sección se centra en la creación de archivos vacíos en HDFS. Se crea un archivo llamado "archivo_vacio.txt" dentro de la carpeta "example" del usuario "rocio".

### Sección 4: Subida de Archivos al Cluster

```archivo.sh
#Subir un archivo desde Linux a HDFS
hdfs dfs -put ./datasets/persona.data /user/$PARAM_USERNAME/example

#Verificamos
hdfs dfs -ls /user/$PARAM_USERNAME/example

#Vemos el contenido del archivo
hdfs dfs -cat /user/$PARAM_USERNAME/example/persona.data

#Vemos solo algunos registros del archivo
hdfs dfs -tail /user/$PARAM_USERNAME/example/persona.data

#Subir archivos que cumplan un patrón, desde Linux a HDFS
hdfs dfs -put ./datasets/transacciones*.data /user/$PARAM_USERNAME/example

#Verificamos
hdfs dfs -ls /user/$PARAM_USERNAME/example
```

En esta parte, se lleva a cabo la subida de archivos desde el sistema local al cluster HDFS. Se sube un archivo llamado "persona.data" a la carpeta "example" del usuario "rocio". Luego, se verifican los archivos en esa carpeta y se muestra el contenido de "persona.data". También se suben archivos que cumplen un patrón, en este caso, archivos que comienzan con "transacciones" seguido de cualquier texto y tienen la extensión ".data".

Estos comandos son útiles para manipular y gestionar archivos y carpetas en un entorno distribuido como HDFS.