---
layout: post
title: Instalar VirtualBox en Debian
categories: [Debian, Linux]
---
Primero que nada, es importante saber que **<a href="https://www.virtualbox.org" target="_blank" rel="noopener">VirtualBox</a>** es una herramienta de Virtualización creado por Oracle. Cuando hablamos de **Virtualización**, nos referimos a que podremos realizar una instalación de otros sistemas operativos (Windows, MacOS, BSD, Linux) sobre nuestro sistema anfitrion, o cualquiera que sea el sistema operativo principal que tengamos instalado en nuestro computador.

Se le hace llamar máquina virtual debido a que básicamente es una computadora instalada dentro de nuestra computadora pero que realmente no interactua con nuestro equipo como lo haría nuestro sistema operativo principal.

Quiza, en ocasiones habras visto que algunas personas llegan a tener en su computador dos o más sistemas operativos instalados, lo mas común de estos casos seria ver linux y windows compartiendo el mismo disco duro pero en particiones diferentes, a eso le llamamos **dualboot**.

El dualboot es comunmente usado por personas que en algunos casos utilizan linux como sistemas operativo pricipal, pero siguen dependiendo de alguna manera que alguna aplicacion el cual exclusivamente debe ser instalada en windows, normalmente cuando son creadas en lenguajes como Visual foxpro, vbasic, .net o cualquiera que de alguna manera este muy vinculada al sistema operativo. Otro caso comun es de los gamers que necesitan correr sus juegos para aprovechar al máximo los gráficos entre otras caracteristicas de sus juegos.

Sin embargo existen otros casos un poco menos "exigentes" en los que no tenemos la necesidad de compartir nuestro disco duro con un `SO` que no queramos usar, o que solamente usaremos para cosas puntuales o especeficas como: probar herramientas, simular equipos en red, configuraciones bases y más. todo esto lo podremos hacer en una maquina virtual [VM]. y de esta manera no tendremos que estar reiniciando nuestro equipo para cambiar de sistemas operativos.

## Instalando VirtualBox
En caso de **Debian** y derivados, lo podremos encontrar en repositorios oficiales, sin embargo yo recomeindo utilizar los repositorios de la pagina para obtener la última version estable del **vbox**

## Editando nuestros source.list

En este paso, debemos saber cual es la versión que estamos utilizando, en mi caso utilizo Debian y usaré **stretch** y que colocaremos de la siguiente manera:

```
deb https://download.virtualbox.org/virtualbox/debian contrib
```
En donde `mydist` será la versión que usaremos. Luego de comprendido esto, procemos a editar nuestro archivo.

`$ sudo vim /etc/apt/source.list`

y agregamos el repositorio
```
deb https://download.virtualbox.org/virtualbox/debian stretch contrib
```

Ahora, debemos agregar los *public key* para realizar una descarga segura desde los servidores de Oracle, Lo haremos de la siguiente manera.

Descargamos el archivo

`$ wget https://www.virtualbox.org/download/oracle_vbox_2016.asc`

y si todo sale bien deberia mostrar una salida como la siguiente:

```
--2018-05-13 18:06:48-- https://www.virtualbox.org/download/oracle_vbox_2016.asc
Resolviendo www.virtualbox.org (www.virtualbox.org)... 137.254.60.32
Conectando con www.virtualbox.org (www.virtualbox.org)[137.254.60.32]:443... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 3157 (3,1K) [text/plain]
Grabando a: "oracle_vbox_2016.asc"

oracle_vbox_2016.asc 100%[=====================================================================================>] 3,08K 19,8KB/s en 0,2s

2018-05-13 18:06:49 (19,8 KB/s) - "oracle_vbox_2016.asc" guardado [3157/3157]
```
Luego de esto procedemos a agregar

```
sudo apt-key add oracle_vbox_2016.asc
```
```
OK
```

Si queremos realizar todo desde un solo comando para decargar y agregar, se hace de la siguiente manera

`wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -`

la huella de la llave deberia ser la siguiente

```
B9F8 D658 297A F3EF C18D 5CDF A2F6 83C5 2980 AECF
Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org></info@virtualbox.org>
```

## Procedemos a instalar

`$ sudo apt-get update &amp;&amp; sudo apt-get install virtualbox-5.2`

Esto hará que nuestro sistema de actualice con la ultima version de vbox y posteriormente comienza la instalación.

## 2da Modalidad, Descargando el .deb
Antes de proceder a realizar la descarga, debemos estar seguro la version de nuestro sistema operativo sea 32 o 64 bit es decir que: `(32=i386)` y `(64=AMD64)`
lueg de identificado esto, procedemos a realizar la descarga desde la pagina de [VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads)

Luego de haber cultimando la descargar del archivo .deb procemos a la instalacion de la siguiente manera.

`$ sudo dpkg -i ~/Descargas/virtualbox-5.2_5.2.12-122591~Debian~stretch_amd64.deb`

y si todo ha salido como deberia, ya tenemos virtualbox instalado.

<img class="wp-image-331 size-medium" title="Instalando VirtualBox en Debian Buster GNU/Linux" src="https://lordvalor.com/wp-content/uploads/2018/05/vbox_verion_instaled-300x232.png" alt="Instalando VirtualBox en Debian Buster GNU/Linux" width="300" height="232" />

luego de esto, debemos agregar nuestro usuario al grupo **vboxusers** de la siguiente manera:

`$ sudo usermod -G vboxusers -a usuario`
Donde usuario seria el nombre de usuario de nuestro equipo con el que estamos trabajando.

Otra manera de hacerlo seria la siguiente:
`$ sudo usermod -G vboxusers -a $USER`

Espero que les sirva, Cualquier detalle no dudes en dejar sus comentários.

&nbsp;

*[VirtualBox]: VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.
*[vbox]: VirtualBox is a general-purpose full virtualizer for x86 hardware, targeted at server, desktop and embedded use.
*[Oracle]: Oracle Corporation is an American multinational computer technology corporation, headquartered in Redwood Shores, California.
*[Debian]:Debian is a Unix-like computer operating system that is composed entirely of free software, and packaged by a group of individuals participating in the Debian Project.
*[Virtualización]: In computing, virtualization refers to the act of creating a virtual version of something, including virtual computer hardware platforms, storage devices, and computer network resources.
