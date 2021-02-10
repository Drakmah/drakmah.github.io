---
typora-root-url: ../
layout: post
title:  "Práctica nginx"
categories: puesta en produccion segura

---
# Práctica nginx

***

En vez de instalar nginx, que parece muy complicado, vamos a descarga una imagen de nginx en dockerhub :

![01](/images/practica_nginx/01.png)

Además de eso, ha comenzado la ejecución del contenedor como demonio y está publicado. Tan solo hay que ir a localhost:8080 para comprobar que el servidor está en marcha:

![02](/images/practica_nginx/02.png)

***

De forma predeterminada, nginx busca en el directorio _/usr/share/nginx/html_ dentro del contenedor los archivos para servir.

Vamos a vincular un directorio de la máquina local y asignar ese directorio a la máquina en ejecución. Para ello vamos a crear un directorio llamado _nginx_ y dentro de él otro llamado _site-content_ . En este directorio vamos a crear nuestro archivo html:

![03](/images/practica_nginx/03.png)

Ahora vamos a ejecutar :

~~~
docker run --rm -d -p 8080:80 --name web -v ~/Documentos/nginx/site-content:/usr/share/nginx/html nginx
~~~

El comando _"monta"_ nuestro directorio local (`~/Documentos/nginx/site-content`) que acabamos de crear en el contenedor que está ejecutándose, en la carpeta que sirve los documentos (Document root) en el servidor nginx (`/usr/share/nginx/html`)

![04](/images/practica_nginx/04.png)

Y esta es la salida:

![05](/images/practica_nginx/05.png)

***

Tener un volumen está bien, pero solamente podemos ejecutarlo localmente. Lo ideal es poder mover esa imagen y que los archivos html pudiesen moverse con ella. Para hacer esto, vamos a copiar los archivos html en la imagen, haciendo una _"imagen personalizada"_

Para ello, crearemos un Dockerfile, en el que crearemos una imagen base, para después copiar el archivo html en el directorio que sirve las páginas de nginx (`/usr/share/nginx/html`) , sobreescribiendo el archivo por defecto de nginx .

![07](/images/practica_nginx/07.png)

 Por ultimo construiremos la imagen con el comando 

~~~
docker build -t webserver .
~~~

De esta forma podemos ejecutar nuestra imagen en un contenedor, sin tener que crear un volumen para incluir el html, pues el dockerfile ya ha copiado el archivo