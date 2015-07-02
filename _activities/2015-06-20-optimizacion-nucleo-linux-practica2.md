---
layout: post
title:  "Bloque 3 Actividad 2: Optimicación del nucleo de Linux para Baja Latencia"
date:   2015-06-20 00:00:00
categories: portafolio, actividad
bloque: 3
description: En esta única actividad vamos a estudiar la optimización de parámetros del kernel de linux para sistemas en tiempo real.
---


# PRÁCTICA 2

Siempre que vamos a modificar el kernel debemos conocer su versión con el comando ```uname -a```

En la pagina de descargas de los archivos para el kernel encontramos también los archivos para baja latencia: [repositorio][6]

[6]:http://kernel.ubuntu.com/~kernel-ppa/mainline/

![imagen](/resources/b3/b32-01.png)

Para la versión del kernel de nuestro dispositivo entramos en la carpeta  [v3.18.16-vivid][7]

[7]:http://www.kernel.ubuntu.com/~kernel-ppa/mainline/v3.18.16-vivid

![imagen](/resources/b3/b32-02.png)

Localizamos la carpeta que buscamos  

![imagen](/resources/b3/b32-03.png)

Al clickar sobre la carpeta aparecen los archivos disponibles para su descarga.
Se descargan los ficheros para la baja latencia

**linux-headers-3.18.16-031816-lowlatency_3.18.16-031816.201506141335_i386.deb**

![imagen](/resources/b3/b32-04.png)

Segundo fichero necesario

**linux-headers-3.18.16-031816_3.18.16-031816.201506141335_all.deb**

![imagen](/resources/b3/b32-05.png)

Tercer archivo **linux-image-3.18.16-031816-lowlatency_3.18.16-031816.201506141335_i386.deb**

![imagen](/resources/b3/b32-06.png)


El siguiente paso es mover los archivos descargados.

![imagen](/resources/b3/b32-07.png)

Se mueven al directorio **usr/src** donde está el kernel de linux.

![imagen](/resources/b3/b32-08.png)

Comprobamos que los tres archivos están en el directorio con un **ls**.
![imagen](/resources/b3/b32-09.png)

Ejecutamos el comando:

```bash
sudo dpkg -i linux*.deb
```

![imagen](/resources/b3/b32-10.png)

Para actualizar el grub ejecutamos ```sudo update-grub``` y  ```sudo update-grub2```

![imagen](/resources/b3/b32-11.png)

Al cerrar reiniciar la máquina virtual ya aparece la opción del grub

![imagen](/resources/b3/b32-12.png)

Entrando en opciones avanzadas apra Ubuntu accedemos a la versión de baja latencia

![imagen](/resources/b3/b32-13.png)
