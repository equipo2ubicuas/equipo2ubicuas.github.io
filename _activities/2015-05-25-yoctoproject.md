---
layout: post
title:  "Actividad 3 Bloque 2 : YoctoProject"
date:   2015-05-25 00:00:00
categories: portafolio, actividad
bloque: 2
description: Tras estudiar los microcontroladores y ver sus aplicaciones vamos a analizar el uso de placas con procesadores ARM para poder crear distribuciones para dicho procesador de forma personalizada usando el software yoctoproject el cual nos permite de manera sencilla crear una distribución para distintas arquitecturas(ARM, ARM64, MIPS, x86, x86_64).
---

### ¿QUÉ ES YOCTO PROJECT?

El Yocto Project es un grupo de trabajo de la *Fundación Linux* definido como:
_"Yocto Project proporciona código abierto, infraestructura de alta calidad y herramientas para ayudar a los desarrolladores a crear sus propios distribuciones personalizadas de Linux para cualquier arquitectura de hardware. El Proyecto yocto está destinado a proporcionar un punto de partida útil para los desarrolladores."_

El *Yocto Project* es un proyecto de colaboración de código abierto que proporciona plantillas, herramientas y métodos para ayudar a crear sistemas personalizados basados en Linux para los productos integrados, según la arquitectura del hardware.

Las productos son muchos y tan variadas como sistemas de seguridad inteligentes, receptores GPS, sistemas de control y guiado para vehículos o sistemas de infotainment (neologismo surgido de la unión de information y entertainment).

Es un proyecto respaldado por la GNU/Linux Foundation, que buscaba facilitar soluciones de GNU/Linux embebido sin tener que complicarnos en la creación de una nueva distribución base. Un sistema operativo embebido es un sistema diseñado para realizar una o algunas funciones específicas en un dispositivo concreto.

La compilación de código fuente que, realizada bajo una determinada arquitectura genera código ejecutable para una arquitectura diferente se denomina *compilación cruzada*. Un entorno de compilación cruzada nos brinda la posibilidad de aprovechar los recursos que disponemos en una computadora tipo PC que sería el sistema huesped y se genera el Sistema objetivo que buscamos.  

La elección de este sistema objetivo se basa en la arquitectura de hardware del dispositivo. Para realizar este tipo de compilación es necesario contar con una serie de programas y librerías que establezcan un ambiente propicio para llevar a cabo esta tarea. Este ambiente se denomina *Entorno de compilación cruzada*.

En la configuración de un entorno de compilación cruzada sobre un sistema operativo GNU/Linux se necesita la configuración y descripción de los componentes que forman parte de este proceso. Cuando se quiere desarrollar una solución de un sistema empotrado tenemos dos soluciones desde GNU/Linux: construir un sistema usando la técnica LFS (Linux From Scrath- GNU/Linux desde cero) o enredarnos con las escasísimas soluciones privativas que se ofrecen en el mercado. A este sector apuntó Yocto Project.

Además de la GNU/Linux Foundation, en este proyecto se han embarcado el Consumer Electronics Linux Forum (CELF) y el fabricante de microchips Intel. La presencia de esta última podría hacer sospechar a priori que el trabajo de este nuevo grupo va a dirigirse solamente a la plataforma x86 pero los productos de Yocto Project van a ser utilizable en las plataformas ARM, MIPS, PowerPC y x86.

Al estar gestionado la Fundación Linux, el proyecto sigue siendo independiente de sus organizaciones miembros que participan de diversas maneras y proporcionan recursos para el proyecto.

Fue iniciado en 2010 como una colaboración de muchos fabricantes de hardware, sistemas operativos de código abierto, proveedores y empresas de electrónica, en un esfuerzo para reducir la duplicación de su trabajo, el suministro de recursos y la información que atienden a los usuarios nuevos y experimentados  de los sistemas empotrados que nos permiten la operatividad de la robotecnia.

El proyecto se centra en proporcionar estándares y herramientas que  permitan construir sistemas empotrados logrando una reducción de la fragmentación existente.

![imagen](/resources/PicsY/yp1.png)

Teniendo su propio entorno de construcción, herramientas y servicios, la cantidad de dependencia de software se reduce.
Para producir estos resultados, las herramientas de Yocto Project están presentes en todos los pasos. La reutilización de componentes de software y utilidades se maximiza en la construcción.

Tanto las librerías, como cualquier otro componente de software se incorporan con la configuración deseada. Además, el código fuente necesario se descargará de sus respectivos repositorios como pueden ser The Linux Kernel Archives (www.kernel.org), GitHub y www.SourceForge.net.

### INICIO RÁPIDO EN YOCTO PROJECT

Descripción de una iniciación rápida de la presentación Developing Embedded Linux Devices Using the Yocto ProjectTM

![imagen](/resources/PicsY/yp2.png)

### POKY

*POKY* es el sistema de referencia en Yocto Project, se compone de una colección de herramientas y metadatos. Es independiente de la plataforma y realiza compilación cruzada. Proporciona el mecanismo para construir y combinar miles de proyectos de código abierto distribuido para formar una pila de software de Linux totalmente personalizable, completa y coherente.

El principal objetivo de *POKY* es proporcionar todas las características que un desarrollo incrustado necesita, haciendo hincapié en un mayor uso de componentes adicionales, metadatos y subconjuntos

![imagen](/resources/PicsY/yp3.png)



### BITBAKE
*Bitbake* es un programador de tareas de código mixto: Python y Shell Script. El código analizado genera y ejecuta tareas, que son básicamente un conjunto de pasos ordenados de acuerdo a las dependencias del código.

Evalúa todos disponibles archivos de configuración y metadatos, la gestión dinámica de la expansión de variable, dependencias, y la generación de código. Se realiza un seguimiento de todas las tareas en proceso con el fin de asegurar su finalización, maximizando el uso de recursos de procesamiento para reducir el tiempo de construcción.

El desarrollo de bitbake se centraliza en la lista de correo bitbake-devel@lists.openembedded.org, y su código se puede encontrar en el subdirectorio bitbake.

#### OPENEMBEDDED-CORE
La colección de metadatos *OpenEmbedded-Core* está diseñado para proporcionar las características básicas del sistema que queremos construir.

Proporciona soporte para cinco diferentes arquitecturas de procesador (ARM, x86, x86-64, PowerPC, MIPS y MIPS64).

El desarrollo se centraliza en el openembedded-core@lists.openembedded.

#### METADATOS
Los metadatos, que se compone de una mezcla de archivos de texto en Python y Shell Script, que proporciona flexibilidad al sistema.

Poky hace uso de estos metadatos para extender OpenEmbedded- Core. Hay dos capas diferentes, que son subconjuntos de metadatos:

• *meta-yocto*: Esta capa proporciona las distribuciones por defecto y compatibles, marca visual, y seguimiento de la información de metadatos (mantenedores, estado aguas arriba, y así sucesivamente)

• *meta-yocto-bsp*: Esta capa, en la parte superior de la misma, proporciona las referencias de cada  hardware específico  para su uso en Poky.

![imagen](/resources/PicsY/yp4.png)

### FLUJO DE TRABAJO EN POKY
Es importante entender los conceptos básicos involucrados en el flujo de trabajo POKY.

![imagen](/resources/PicsY/yp5.png)

Inicialmente hay que descargar y configurar, preparar el entorno de compilación POKY y compilar para obtener el sistema objetivo.
La construcción del sistema se realiza por capas.

![imagen](/resources/PicsY/yp6.png)

### CONFIGURACIÓN DE UN SISTEMA


El proceso necesario para establecer nuestro sistema empotrado depende de la distribución en la que va a correr el sistema. Poky tiene un conjunto de distribuciones de Linux preparadas, y si somos nuevos en el desarrollo de Linux embebido, es recomendable utilizar una de las distribuciones Linux compatibles para evitar perder tiempo en la depuración.

![imagen](/resources/PicsY/yp7.png)

Actualmente, las distribuciones compatibles son los siguientes:

• *meta-yocto* Ubuntu 12.04 (LTS)

• *meta-yocto* Ubuntu 13.10

• *meta-yocto* Ubuntu 14.04 (LTS)

• *meta-yocto* Fedora liberar 19 (Gato de Schrödinger)

• *meta-yocto* lanzamiento de Fedora 20 (Heisenbug)

• *meta-yocto* CentOS liberan 6,4

• *meta-yocto* CentOS liberan 6,5

• *meta-yocto* Debian GNU / Linux 7.x (Wheezy)

• *meta-yocto* openSUSE 12.2

• *meta-yocto* openSUSE 12.3

• *meta-yocto* openSUSE 13.1







### Instalación de los paquetes

Si la distribución elegida para nuestro sistema no está en la lista anterior, también se puede usar con POKY, que las herramientas de yocto project no no proporcionen una distribución Linux no significa que no sea posible utilizarlas. Pero para abordar la construcción de un sistema con una distribución de Linux diferente se necesita cierto grado de experiencia para conseguir el sistema empotrado deseado.

Cuando no se tiene la suficiente experiencia se poden obtener resultados inesperados debido a que todos los paquetes que deben ser instalados en el sistema de acogida varían de una distribución a otra. Se puede encontrar las instrucciones para todas las distribuciones soportadas en el Manual de Referencia de Yocto Project.

![imagen](/resources/PicsY/yp8.png)

Para instalar los paquetes necesarios para Debian o Ubuntu ejecute el siguiente comando:

```bash
$: sudo apt-get install gawk wget git-core diffstat unzip texinfo build-essential chrpath*
```

Si el sistema anfitrión tiene soporte gráfico, se ejecuta el comando:

```bash
$: sudo apt-get install libsdl1.2-dev xterm
```

#### La descarga del código fuente en Poky
Después instalamos los paquetes necesarios en nuestro sistema de acogida de desarrollo, tenemos que conseguir el código fuente que se puede descargar con Git, con el siguiente comando:

```bash
$: git clone git://git.yoctoproject.org/poky --branch daisy
```

#### Preparación del entorno de compilación
Dentro del directorio POKY, hay un script llamado oe-init-build-env, que debe ser usado para configurar el entorno de compilación. El script se debe ejecutar:

```bash
$: source poky/oe-init-build-env [build-directory]
```
En este caso, buil-directory es un parámetro opcional para el nombre del directorio donde se establece el entorno de las compilaciones. Es muy cómodo usar diferentes directorios de construcción. Así podemos trabajar en proyectos distintos con montajes paralelos o diferentes sin afectar a otros.

### El archivo local.conf
Cuando inicializamos un entorno de compilación, se crea el archivo build/conf/local.conf, donde se guarda la configuración del equipo que estamos construyendo.

![imagen](/resources/PicsY/yp9.png)

Contiene la arquitectura del sistema anfitrión que se utilizarán para la compilación cruzada, con los parámetros de optimización para la máxima reducción del tiempo de construcción. Los comentarios dentro del archivo de *build/conf/local.conf* son una muy buena documentación y referencia de posibles variables y sus valores predeterminados.

El conjunto mínimo de variables que debemos adaptar a la arquitectura del sistema anfitrión son:

```
BB_NUMBER_THREADS ?= "${@oe.utils.cpu_count()}"

PARALLEL_MAKE ?= "-j ${@oe.utils.cpu_count()}"

MACHINE ??= "qemux86"
```
Con la variable MÁCHINE se determina el equipo de destino que queremos construir.

![imagen](/resources/PicsY/yp10.png)

Actualmente Poky soporta los siguientes máquinas en su referencia Board Support Package (BSP):

•   beaglebone

•	genericx86

•	genericx86-64

•	mpc8315e-rdb

•	edgerouter


![imagen](/resources/PicsY/yp11.png)


Las máquinas necesitan de una capa llamada meta-yocto-bsp. Además de estas máquinas, OpenEmbedded-Core también proporciona soporte para:

• qemuarm: Esta es la emulación ARM QEMU

• qemumips: Esta es la emulación MIPS QEMU

• qemumips64: Esta es la emulación MIPS64 QEMU

• qemuppc: Esta es la emulación de PowerPC QEMU

• qemux86-64: Esta es la emulación x86-64 QEMU

• qemux86: Esta es la emulación x86 QEMU

##La construcción de una imagen de destino

Poky ofrece varias recetas de imágenes prediseñadas que podemos utilizar para construir nuestra propia imagen binaria. Podemos comprobar la lista de imágenes disponibles ejecutando el siguiente comando desde el directorio:

```bash
$: ls meta*/recipes*/images/*.bb
```


Todas las recetas proporcionan imágenes que son, en esencia, un conjunto de paquetes descomprimidos y configurados, generando un sistema que podemos utilizar en un hardware real. La lista de imágenes hasta a la fecha se puede ver en el Manual de Referencias de Yocto Project.

![imagen](/resources/PicsY/yp12.png)

El proceso de construcción de una imagen para un objetivo es muy simple. Hay que ejecutar el siguiente comando:  bitbake <nombre de la receta>
Por ejemplo, la construcción de core-image-full-cmdline, ejecute el siguiente comando:

```bash
$: bitbake core-image-full-cmdline
```


##Ejecución de imágenes en QEMU
Como muchos proyectos tienen una dependencia del hardware, la emulación de hardware viene a acelerar el proceso de desarrollo al permitir que la imagen pueda funcionar sin el hardware real.

![imagen](/resources/PicsY/yp13.png)

*Quick EMUlator (QEMU)* es un paquete de software libre y de código abierto que lleva a cabo la virtualización de hardware. Las máquinas basadas en QEMU permiten pruebas y desarrollo sin hardware real. En la actualidad, la ARM, MIPS, MIPS64, PowerPC y x86 y x86-64 son emulaciones compatibles. La manera de ejecutar el script es el siguiente:

```bash
Runqemu _machine zImage  sistemas_de_archivos_
```

![imagen](/resources/PicsY/yp14.png)

### Referencias

- Practical Kernel Development Darren Hart Intel Corporation April 11, 2011

- Developing Embedded Linux Devices Using the Yocto Project™ David Stewart Intel Corporation October, 2011

- Introduction to the Yocto Project Mark Hatle & Bruce Ashfield Yocto Project Barcelona, Spain 08-Nov-2012 The Linux Foundation. All rights reserved.

- Embedded Linux Development with Yocto Project Otavio Salvador Daiane Angolini Packt Publishind July 2014

- [Hacklab Almeria](http://hacklabalmeria.net/actividades/2015/06/12/taller-de-hardware-abierto.html)

- Noticia del enlace web:
[http://observatorio.cenatic.es/index.php?option=com_content&view=article&id=632:yocto-project-el-linux-empotrado-a-medida&catid=54:tecnologia&Itemid=62](http://observatorio.cenatic.es/index.php?option=com_content&view=article&id=632:yocto-project-el-linux-empotrado-a-medida&catid=54:tecnologia&Itemid=62
)
