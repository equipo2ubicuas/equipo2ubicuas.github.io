---
layout: post
title:  "Bloque 3 : Optimicación del nucleo de Linux para Baja Latencia"
date:   2015-06-20 00:00:00
categories: portafolio, actividad
bloque: 3
description: En esta única actividad vamos a estudiar la optimización de parámetros del kernel de linux para sistemas en tiempo real.
---

### PRÁCTICA 1

Para esta práctica se ha utilizado un ubuntu 14.04 de 64 bits en un procesador dual core T7300 a 2,4Ghz. Con 2Gb de RAM.

## 1º ACTUALIZAR EL KERNEL

Se puede hacer descargando los paquetes principales y el comando  sudo dpkg -i linux*.deb

Hay que saber el kernel que tenemos con ```uname –a```

![imagen](/resources/b3/b3-0a.png)

Descargamos los paquetes en la página [kernel.ubuntu.com] [2]
[2]:http://kernel.ubuntu.com/~kernel-ppa/mainline/
Es muy aconsejable leer el README antes de iniciar cualquier descarga  

![imagen](/resources/b3/b3-0b.png)

Descargados los paquetes, por terminal entramos en el directorio de Descargas y ejecutamos

```bash
 sudo dpkg -i linux*.deb
```

![imagen](/resources/b3/b3-0c.png)

---

### 2º ACTUALIZAR EL KERNEL A LA ÚLTIMA VERSIÓN DISPONIBLE

Para poder compilar el kernel necesitamos tener instalados y actualizados los paquetes:
```libncurses5 dpkg-dev build-essential initramfs-tools```

Utilizamos la sentencia

```bash
sudo apt install gcc libncurses5-dev dpkg-dev
```

![imagen](/resources/b3/b3-01.png)


Ejecutamos y comprobamos que están todos los paquetes que necesitamos instalados y en su versión más reciente.

```bash
Sudo apt install gcc libncurses5-dev dpkg-dev build-essential initramfs-tools
```

![imagen](/resources/b3/b3-03.png)

Descargamos la versión de Kernel más reciente de la página [www.kernel.org][3]
[3]:http://www.kernel.org

![imagen](/resources/b3/b3-04.png)

Vemos que está en la carpeta Descargas

![imagen](/resources/b3/b3-05.png)

Por terminal, entramos en el directorio descargas para descomprimir el archivo

```bash
 tar -xvf linux-4.0.5.tar.zx
 ```

![imagen](/resources/b3/b3-06.png)


una vez descomprimido hay que moverlo a /usr/src/ con la sentencia

```bash

 mv linux-4.0.5 /usr/src
```

Por terminal comprobamos que existe en el directorio /usr/src

![imagen](/resources/b3/b3-07.png)

Creamos un enlace simbólico a la carpeta que acabamos de incluir en /usr/src

```bash
 sudo ln -s /usr/src/linux-4.0.5 /usr/src/linux
```

![imagen](/resources/b3/b3-08.png)

Comprobado que se ha creado el enlace simbólico, hay que configurar y compilar el kernel. Hay que entrar en usr/src/linux y ejecutar: ``` make clean```

![imagen](/resources/b3/b3-09.png)

Al ejecutar obtenemos como resultado

![imagen](/resources/b3/b3-10.png)

Ejecutamos ``` make mrproper ```

![imagen](/resources/b3/b3-11.png)

El resultado se muestra en la siguiente imagen.

![imagen](/resources/b3/b3-12.png)

Por último ejecutamos: ``` make menuconfig ```

![imagen](/resources/b3/b3-13.png)

En el menú se deben indicar las características que necesitamos.

 **Configuración por defecto del nuevo kernel**

Si seleccionamos el apartado 64 bits y pulsamos la opción “save”, nos aparecerá una ventana en la que nos preguntará el nombre del archivo de configuración para compilar.
Dejamos el nombre por defecto (.config) y guardamos los cambios, dejando la configuración por defecto. Para compilar utilizamos sudo make y esperamos a que termine el proceso.
Una vez finalizado, debemos instalar el nuevo núcleo en nuestro sistema con:

```bash
sudo dpkg -i*.deb
```

Con el comando anterior el ordenador ya está actualizado al nuevo núcleo del sistema. Falta reiniciar el sistema y aparecerá en el gestor de arranque Grub una nueva entrada correspondiente al nuevo kernel. La seleccionamos y tendremos Ubuntu con todas las nuevas características y mejoras del núcleo sin la necesidad de actualizar la versión completa de la distribución LTS.

Según noticias recientes, Ubuntu 15.0 no vendrá con Linux 4.0 por lo que habrá que actualizar el núcleo.

**Personalizar el nuevo Kernel**

Al desplazarnos por el menú de configuración y aparece el **Kernel Configuration**

![imagen](/resources/b3/b3-14.png)

Lo más importante a configurar en esta sección es **Kernel compression mode**:

Nos permite elegir el nivel de compresión de la imagen del Kernel. Hay pocas diferencias entre elegir una u otra opción, si disponemos de espacio, elegiremos la más rápida.

-De mayor a menor compresión: XZ>LZMA>Bzip2>Gzip>LZO

-De mayor a menor rapidez comprimiendo: LZO>Gzip>Bzip2>LZMA>XZ

![imagen](/resources/b3/b3-15.png)

• **Gzip** Es el compresor por defecto y el habitual. Tiene unos valores de compresión y descompresión intermedios y un tamaño del kernel más bien alto.

• **Bzip2** La velocidad de compresión es intermedia. La descompresión es lenta. El tamaño del kernel será un 10% menor que con gzip. Bzip2 usa una gran cantidad de memoria.

• **LZMA** proporciona la mayor compresión, pero no es rápido (más bien bastante lento). El tamaño del kernel será aproximadamente un 33% (una tercera parte) más pequeño comparado con gzip.

• **LZO** La compresión es muy poca, un 10% más de tamaño del kernel con respecto a gzip, lo que le hace ser el más rápido.

![imagen](/resources/b3/b3-16.png)

Elegimos la opción de mayor comprensión, al ser una máquina virtual.

En caso de que tengamos un kernel que soporte Group scheduler, como son el 2.6.38 o superiores o a los que se les ha aplicado el parche Mike glabraith. Para poder comprimir en lzo tendremos que instalar primero el paquete lzop

**Support for paging of anonymous memory** Nos permite habilitar o deshabilitar la memoria swap.

![imagen](/resources/b3/b3-17.png)

**Optimize for size** Como el mismo nombre indica, optimiza GCC para obtener un kernel más pequeño. En la configuración por defecto no está marcado Optimize size, se marca al estar situado sobre la sección debemos pulsar y.

![imagen](/resources/b3/b3-18.png)

**Control Group Support Optimización** necesaria para habilitar el parche galbraith que mejora el desempeño multitarea (Para versiones del 2.6.38 o superiores o con parche Mike galbraith aplicado) Dentro de esta sección se habilitarán las siguientes opciones:

• Namespace cgroup subsystem

• Freezer cgroup subsystem

• Device Controller for cgroups

• Cpuset support

• Include legacy /proc/<pid>/cpuset

• Resource counters

• Memory Resource Controller for Control Groups

• Memory Resource Controller Swap Extension

• Group CPU scheduler (y lo que hay dentro)

![imagen](/resources/b3/b3-19.png)


Dentro de **Group CPU scheduler** tiene que estar marcado todo.

![imagen](/resources/b3/b3-20.png)

Además dentro de Kernel configuration en General setup debe estar habilitado **Automatic process group scheduling** parche galbraith que mejora el desempeño multitarea (Sólo Kernel 2.6.38 o superior o con parche Mike galbraith aplicado)

![imagen](/resources/b3/b3-21.png)


Terminado el bloque** Enable loadable module support** se pasa a **Enable the block layer**

![imagen](/resources/b3/b3-22.png)


Hay que entrar en  **IO schedulers** debe estar marcado **CFQ I/O cheduler**

![imagen](/resources/b3/b3-23.png)

Comprobado que está marcado **CFQ I/O cheduler**

![imagen](/resources/b3/b3-24.png)

Se sale del bloque Enable the block layer

![imagen](/resources/b3/b3-25.png)


**SECCION PROCESSOR TYPE AND FEATURES** de Kernel Configuration

![imagen](/resources/b3/b3-26.png)


En esta sección se configura todo lo relacionado con el procesador. Lo más importante a configurar en esta sección es:

• **Memtest** Permite realizar test de memoria con memtest

• **Processor family** Donde elegiremos nuestro procesador.

• **Maximum number of CPUs** número máximo de CPus

• **SMT (Hyperthreading) scheduler support** Imprescindible para procesadores con Hyperthreading y desaconsejado para los que no lo tengan

![imagen](/resources/b3/b3-27.png)

• **Timer frequency** Permite elegir la frecuencia del timer, 1000Hz es el valor recomendado para PC por mejorar el desempeño multitarea y 100Hz en servidores de muchos procesadores.

![imagen](/resources/b3/b3-28.png)

• **Dentro de Preemption Model Optimización** para mejorar el desempeño multitarea hay que marcar como predeterminado:Preemptible Kernel (low-latency desktop)

![imagen](/resources/b3/b3-29.png)

**Transparent Hugepage Support** hace un uso intensivo de memoria, al estar habilitada aparece  **Page migration** y **Transparent Hugepage Support sysfs defaults** habilitadas.

![imagen](/resources/b3/b3-30.png)

Dentro de **Transparent Hugepage Support sysfs defaults**, elegiremos **madvise** al ofrecer más garantías. Always  es más agresiva, pero ofrece menos garantías.

![imagen](/resources/b3/b3-31.png)

También está habilitado **Support for hot-pluggable CPUs** que permite habilitar y deshabilitar procesadores, no nos permite deshabilitarlo, aunque en este caso no es necesario al haber definido una maquina virtual con 1 núcleo.

**SECCIÓN POWER MANAGEMENT AND ACPI OPTIONS**

En esta sección dejamos los valores por defecto.

**Power management and ACPI options** ofrece el soporte para el manejo de alimentación. Útil cuando se utilizan sistemas con batería como los portátiles. Ahorra energía en periodos de inactividad desactivando dispositivos. Se realiza activando APM o ACPI. Estas características permiten el ahorro de energía activando y desactivando los distintos componentes del equipo en función de si están siendo o no utilizados.

![imagen](/resources/b3/b3-32.png)

**ACPI (Advanced Configuration and Power Interface) Support** Soporte para configuración avanzada e interfaz de alimentación ACPI, requiere hardware y firmware especifico y OS-directed configuration and power management (OSPM) software. Aumenta 70K el tamaño del núcleo.

![imagen](/resources/b3/b3-33.png)

**Suspend to RAM and standby** Permite entrar al sistema en estado de suspensión o dormido, en el cual la memoria se mantiene alimentada continuamente para no perder los datos y el resto del equipo permanece “dormido”.

**Hibernation (aka 'suspend to disk')** Habilita la suspensión a disco o hibernación, en la que todo el sistema está apagado, se crea una imagen del sistema y el contenido de la memoria y se almacena en el disco duro en una área de swap activa para poder recuperar el estado inicial.

**Run- time PM core functionality** Habilita ciertas funcionalidades para poner a los dispositivos de entrada/salida en estados de ahorro de energía o baja alimentación después de un periodo de inactividad.

**SFI (Simple Firmware Interface) Support** ofrece un método ligero para el paso de información entre el firmware y el sistema operativo mediante tablas estáticas en memoria.

**APM (Advanced Power Management ) BIOS support** es una especificación BIOS para el ahorro energético utilizando diferentes técnicas. Su uso está recomendado para portátiles con BIOS compatibles con APM, para sistemas multiprocesador hay que desactivarla.

**CPU Frequency scaling** Permite bajar la velocidad del reloj de la CPU para bajar el consumo de energía.

**SECCIÓN BUS OPTIONS (PCI etc.)**

Se deja con la configuración por defecto.

En esta sección, podremos administrar las conecciones, Pci, PCI-E y los distintos buses. Lo más importante a tener en cuenta de esta sección es PCI support, PCI Express support que  permite habilitar el soporte bus Pci-Express. Imprescindible para tarjetas gráficas actuales y PCI Express ASPM control proporciona un mejor control del consumo de energía en relación al Bus PCI-E.

Las otras secciones para el uso habitual de un ordenador no son necesarias.

Para mayor información se utilizará la información proporcionada en las webs:

[www.redeszone.net][4]

[gnulinuxvagos.es][5]
[4]:http://www.redeszone.net/2014/11/28/como-instalar-el-ultimo-kernel-de-linux-en-ubuntu-14-04-lts/

[5]:http://gnulinuxvagos.es/topic/22-configurar-y-compilar-el-kernel-linux-varios-m%C3%A9todos/
