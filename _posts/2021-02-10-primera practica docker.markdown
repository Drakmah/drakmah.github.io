---
typora-root-url: ../
layout: post
title:  "Primera práctica Docker"
categories: puesta en produccion segura

---
# Primera práctica Docker

Instalamos Docker y comprobamos que funciona. **ojo!** - En la instalación hay que modificar el archivo /etc/apt/sources.list : en la ultima línea (descomentada) hay que cambiar _"kalli-rolling”_ por _“stretch”_.

Ejecutamos `sudo docker ps` y comprobamos que funciona:

![](/images/practica_docker/docker01.JPG)

***

Estando dentro de la carpeta del proyecto, Lanzamos `./build.sh`, de forma que se crea el contenedor, para después lanzar `./debug.sh` para lanzar el contenedor en modo _foreground_![docker02](/images/practica_docker/docker02.JPG)

 De esta forma, cada vez que refrescamos el navegador, suma uno al contador:

![docker03](/images/practica_docker/docker03.JPG)

No obstante, cada vez que paremos y arranquemos el contenedor, el contador se reiniciará

***

Para evitar eso, usaremos el script `./persist.sh`, el cual crea un fichero .txt para guardar los datos del servidor, de forma que aunque paremos y arranquemos el contenedor, el contador continua donde lo dejamos

***

Por otra parte, el Script `./run.sh` ejecuta el contenedor en modo demonio, simulando el entorno de producción:

![docker05](/images/practica_docker/docker05.JPG)

##### ¡De esta forma ya tenemos creado nuestro primer contenedor en entorno de produccion!