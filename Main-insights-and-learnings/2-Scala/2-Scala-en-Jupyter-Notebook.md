# Instalación de Scala en Jupyter Notebook con Spylon Kernel

Scala es un lenguaje de programación versátil que puedes utilizar en Jupyter Notebook. Para lograrlo, puedes instalar el kernel Spylon, que permite la ejecución de código Scala en tu cuaderno. Puedes descargar el archivo de [2-Scala-en-Jupyter-Notebook.ipynb](/Main-insights-and-learnings/2-Scala/2-Scala-en-Jupyter-notebook.ipynb). A continuación, se detallan los pasos para instalarlo:

## Paso 1: Instalar el paquete Spylon Kernel

El primer paso consiste en instalar el paquete Spylon Kernel utilizando pip. Abre una terminal y ejecuta el siguiente comando:

```bash
pip install spylon-kernel
```

## Paso 2: Crear una especificación de kernel

Después de instalar el paquete Spylon Kernel, debes crear una especificación de kernel para Jupyter. Esto permitirá seleccionar el kernel de Scala en tus cuadernos. En la misma terminal, ejecuta el siguiente comando:

```bash
python -m spylon_kernel install
```

Esto registrará el kernel de Spylon en Jupyter Notebook.

## Paso 3: Iniciar Jupyter Notebook

Ahora que tienes el kernel de Spylon instalado, puedes iniciar Jupyter Notebook. Abre una terminal y ejecuta el siguiente comando:

```bash
ipython notebook
```

Esto abrirá la interfaz web de Jupyter en tu navegador.

## Paso 4: Crear un cuaderno con el kernel de Spylon

En la interfaz de Jupyter Notebook, selecciona "Nuevo" y verás una opción llamada "spylon-kernel". Haz clic en ella para crear un cuaderno utilizando el kernel de Scala. Esto iniciará tu kernel de Scala.

![spylon-kernel](/Main-insights-and-learnings/2-Scala/img/spylon-kernell.png)

## Paso 5: Probar el cuaderno

Ahora que tienes tu cuaderno de Scala listo, puedes comenzar a escribir y ejecutar código Scala en las celdas. Por ejemplo:

```scala
val x = 2
val y = 3
x + y
```

Al ejecutar estas celdas, deberías ver el resultado, y también deberías observar un mensaje que indica "Initializing Scala interpreter...", lo que confirma que el kernel de Spylon se está utilizando.

## Verificar la instalación

Para verificar que el kernel de Spylon se ha instalado correctamente, puedes realizar una verificación adicional en la terminal de Jupyter:

### Verificar que el kernel esté instalado

Ejecuta el siguiente comando en la terminal de Jupyter para ver si el kernel de Spylon está instalado y disponible:

```bash
jupyter kernelspec list
```

Deberías ver una lista de kernels instalados, incluyendo "spylon-kernel". Esto confirma que el kernel Spylon está instalado y disponible en tu entorno de Jupyter Notebook.

![Verificacion kernelspec list](/Main-insights-and-learnings/2-Scala/img/verificacion-kernelspec.png)

Ahora estás listo para escribir y ejecutar código Scala en tus cuadernos de Jupyter.