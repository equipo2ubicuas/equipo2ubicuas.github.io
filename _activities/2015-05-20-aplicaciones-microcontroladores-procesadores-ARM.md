---
layout: post
title:  "Actividad 2 Bloque 2 : Aplicaciones Microcontroladores y Microprocesadores "
date:   2015-04-15 00:00:00
categories: portafolio, actividad
bloque: 2
description: En esta actividad, se van a mostrar distintas aplicaciones que se han realizado usando microcontroladores y microprocesadores ARM.
---

### Arduino para control de procesos

- **Autor:** Francisco Javier Rosales ALmansa

Proyecto donde utilizando un arduino se es capaz de controlar la velocidad de rotación de un motor por medio de la red a través de un arduino Ethernet.

![plataforma1](/resources/plataforma1.png)

**Objetivo**

El  objetivo  es  el  de  realizar  una  comunicación  entre  la plataforma y un navegador web  de forma  que  se  pueda  interactuar  entre el navegador web y viceversa para realizar un proceso de  control  de  la  regulación  de  la  velocidad  de  un  motor  eléctrico  de  corriente  continua acoplado mecánicamente  a  un  generador  de corriente continua. El proceso de regulación se produce  cuando  se extrae  la  energía  eléctrica  producida  por  el generador, a través de una carga eléctrica, que consta de un relé y un motor  eléctrico  de  corriente  continua que mueve una  plataforma  rotatoria.

**Componentes del proyecto**

Seguidamente se muestran los distintos componentes de los que se componen el proyecto.

- Modulo Arduino Ethernet.
- Módulo Motor Eléctrico Directriz
- Módulo Driver
- Módulo Encoder
- Módulo Generador
- Módulo Relé
- Módulo plataforma

![hardwarearduino](/resources/hardwarearduino.png)

### Utilización de Android en Sistemas empotrados

**Autor:** Víctor Suárez García.

Una de las aplicaciones que podemos ver hoy en día es el uso de los teléfonos inteligentes u otros dispositivos que utilicen el Sistema operativo Android. Es por esto, que vamos a utilizar este sistema operativo para un Sistema de Visión Artificial. Todo ello en placas con procesador ARM.

![logoandroid](/resources/androidlogo.png)

En primer lugar vamos a especificar que hemos utilizado el entorno de desarrollo Android Studio para realizar esta aplicación y la librería *Boofcv* para poder realizar las operaciones de Visión Artificial por medio de la camara de fotos integrada en el teléfono.

Lo que queremos conseguir en nuestra aplicacion es detectar manchas en una superficie y poder especificar cuanto % de la superficie esta dañado.

Para ello vamos a utilizar una foto realizada con la camara de fotos y realizaremos el análisis de esta.

Antes de poder continuar vamos a especificar que vamos a trabajar en un espacio de color distintos al que solemos trabajar que suele ser RGB en este caso, para que el color no quede afectado(o al menos lo menos posible) por la luz, vamos a utilizar el espacio de color HSV.

**HSV**

El modelo HSV (del inglés Hue, Saturation, Value – Matiz, Saturación, Valor), también llamado HSB (Hue, Saturation, Brightness – Matiz, Saturación, Brillo), define un modelo de color en términos de sus componentes.

![HSV](/resources/Triangulo_HSV.png)

Utilizando este Espacio de color, podemos visualizar la foto en dicho espacio.

![ejemplohsv](/resources/ejemplohsv.png)

Cuando se visualiza la foto en HSV vemos que queda menos afectado por la luz. Una vez conseguido esto, vamos a realizar una busqueda del color que necesitemos por ello se utiliza un umbral.

Una vez que tenemos el umbral, vamos a buscar cambios buscos en dicho umbral y por lo tanto podremos obtener una lista de las manchas detectadas.

### Referencias

- [Arduino](http://arduino.cc)
- [Android](http://developer.android.com/)
- [HSV](https://es.wikipedia.org/wiki/Modelo_de_color_HSV)
- [BoofCV](http://boofcv.org)
