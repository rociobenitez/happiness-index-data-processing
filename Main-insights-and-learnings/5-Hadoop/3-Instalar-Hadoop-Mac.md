# Instalar Hadoop en MacOS (M1/M2)

### 1. Instalación de Hadoop con Brew

Para instalar Hadoop, utiliza Brew. Abre la terminal y ejecuta el siguiente comando:

```bash
brew install hadoop
```

### 2. Accede al Directorio de Configuración

Ve al directorio de configuración de Hadoop. Asegúrate de reemplazar "3.3.6" con la versión de Hadoop que estés utilizando:

```bash
cd /opt/homebrew/Cellar/hadoop/3.3.6/libexec/etc/hadoop
```

### 3. Edita los Archivos de Configuración

Abre el directorio en tu editor de código preferido (por ejemplo, Visual Studio Code) con el siguiente comando:

```bash
code .
```
![Directorio de Configuración de Hadoop en VSCode](/Main-insights-and-learnings/5-Hadoop/img/hadoop-files.png)

Ahora, edita los archivos de configuración clave:

- `core-site.xml`:

    ```xml
    <property>
        <name>fs.defaultFS</name>
        <value>hdfs://localhost:9000</value>
        <final>true</final>
    </property>
    ```

- `hdfs-site.xml`:

    ```xml
    <configuration>
        <property>
            <name>dfs.replication</name>
            <value>1</value>
        </property>
    </configuration>
    ```

- `mapred-site.xml`:

    ```xml
    <configuration>
        <property>
            <name>yarn.app.mapreduce.am.env</name>
            <value>HADOOP_MAPRED_HOME=/opt/homebrew/opt/hadoopp</value>
        </property>
        <property>
            <name>mapreduce.map.env</name>
            <value>HADOOP_MAPRED_HOME=/opt/homebrew/opt/hadoop</value>
        </property>
        <property>
            <name>mapreduce.reduce.env</name>
            <value>HADOOP_MAPRED_HOME=/opt/homebrew/opt/hadoop</value>
        </property>
    </configuration>
    ```

- `yarn-site.xml`:

    ```xml
    <configuration>
        <property>
            <name>yarn.nodemanager.aux-services</name>
            <value>mapreduce_shuffle</value>
        </property>
    </configuration>
    ```

### 4. Configura la Variable de Entorno JAVA_HOME

En el archivo `hadoop-env.sh`, establece la variable de entorno `JAVA_HOME` (debe agregarse la ruta local de Java).

Puedes utilizar este comando para encontrar la ruta en la terminal:

```$ usr/libexec/java_home```

y agrega la ubicación en `hadoop-env.sh`:

```bash
export JAVA_HOME=/Users/rociobenitezgarcia/Library/Java/JavaVirtualMachines/openjdk-21.0.1/Contents/Home
```

Ahora ve a Preferencias del Sistema y:

![Preferencias del sistema](/Main-insights-and-learnings/5-Hadoop/img/sesion-remota.png)


### 5. Verifica y Ejecuta Hadoop

Ejecuta el siguiente comando en la terminal para iniciar Hadoop:

```bash
start-all.sh
```

Y escribe `jps` para confirmar que todas las partes de Hadoop se han instalado y ejecutado.

```bash
jps
```

Debería verse algo como:

![Usando el comando jps](/Main-insights-and-learnings/5-Hadoop/img/jps-hadoop.png)

Ahora simplemente escribe http://localhost:9870

![Ejecutándose localhost:9870](/Main-insights-and-learnings/5-Hadoop/img/localhost9870.png)


### 6. Crear directorios

Ahora a crear el directorio.

```bash
hadoop fs -mkdir /usuario 
hadoop fs -mkdir /usuario/rocio.benitez
```

Agregar archivos en el directorio existente

```bash
hadoop fs -put Demo/ /usuario/rocio.benitez
```

Espero que estos pasos te ayuden a configurar Hadoop en tu macOS. ¡Buena suerte! 🍀


## Comentarios adicionales ✨

He observado que la instalación de Hadoop en macOS puede ser un proceso complicado, y tras investigar, he notado que muchos usuarios enfrentan dificultades al intentar instalar Hadoop localmente.

En mi caso, me encontré con un error específico que decía *"Failed to retrieve data from /webhdfs/v1/?op=LISTSTATUS: Server Error"* cuando intentaba abrir la pestaña *"Browse the file system"* en la interfaz web de Hadoop.

Este problema podría estar relacionado con el uso de una versión de Java incompatible, especialmente si se tiene una versión superior a Java 11, como se menciona en la documentación de Hadoop. Debido a estas dificultades, opté por [instalar Hadoop en Docker](/Main-insights-and-learnings/5-Hadoop/3-Instalar-Hadoop-Docker.md), lo cual resultó ser una solución más conveniente y efectiva.