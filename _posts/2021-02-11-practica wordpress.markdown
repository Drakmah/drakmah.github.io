---
typora-root-url: ../
layout: post
title:  "Práctica Wordpress"
categories: puesta en produccion segura

---
# Práctica Wordpress

***

Vamos a usar **docker compose** para hacer que dos contenedores puedan compartir sus recursos. De esta forma podremos tener en un contenedor una *bbdd* y en otro contenedor una aplicación web que haga uso de esa base de datos.

***

Veremos que con docker es extremadamente sencillo:

+ Paso 1: Crear un directorio vacío que usaremos de contexto de la imagen de la aplicación

+ Paso 2: Dentro del directorio creamos un archivo `docker-compose.yml` en el cual se definirán todos los servicios que vamos a usar. 

  Este es nuestro archivo `docker-compose.yml`

  ![wpress01](/images/practica_wordpress/wpress01.PNG)

  Dentro del archivo se pueden ver todas las configuraciones de los servicios, como los usuarios y contraseñas, puertos, etc..

+ Paso 3 : Construimos el proyecto ejecutando `docker-compose up -d ` (dentro del directorio). Esto ejecutará _docker-compose up_ en modo separado, extrae las imágenes de docker, e inicia ambos contenedores (wordpress y bbdd). ¡Así de fácil!

  ![wpress02](/images/practica_wordpress/wpress02.png)

  

  ***

  Con estos 3 sencillos pasos y gracias a docker, ya tenemos nuestro worpress en marcha:

  ![wordpress03](/images/practica_wordpress/wordpress03.png)

  ![wordpress04](/images/practica_wordpress/wordpress04.png)

  

  ### ¡wordpress en marcha!

