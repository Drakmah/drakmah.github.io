---
typora-root-url: ../
layout: post
title:  "Práctica Rails"
categories: puesta en producción segura

---
# Práctica rails

> #### En esta práctica vamos a crear una app Rails con PostgreeSQL

***

#### 1. Definimos el proyecto

- Creamos un archivo `Dockerfile ` con el siguiente contenido:

![rails01](/images/practica_rails/rails01.png)

- Creamos el archivo `Gemfile` con el siguiente contenido:

![rails02](/images/practica_rails/rails02.png)

- Creamos un archivo vacío con el nombre `Gemfile.lock`

- Creamos un script con el nombre `entrypoint.sh` para prevenir el restart del servidor en el caso de que encuentre un archivo `server.pid` anterior

  ![rails04](/images/practica_rails/rails04.png)

- Por último, creamos nuestro archivo `docker-compose.yml` que describe los servicios que vamos a usar:

![rails05](/images/practica_rails/rails05.png)

***

#### 2. Construimos el proyecto

- Construimos la base del proyecto con el comando:

~~~
docker-compose run --no-deps web rails new . --force \
--database=postgresql
~~~

![rails06](/images/practica_rails/rails06.png)

- En Linux los archivos se crean con el propietario root. Hay que cambiar el propietario de los archivos creados con el siguiente comando:

~~~
sudo chown -R $USER:$USER .
~~~

​		Ahora tienen el propietario adecuado:

![rails07](/images/practica_rails/rails07.png)

- Habremos generado un nuevo Gemfile, por lo que hemos de volver a construir la imagen, con el comando:

~~~
docker-compose build
~~~

![rails08](/images/practica_rails/rails08.png)

***

#### 3. Conectar con la BBDD

- Hay que cambiar el nombre de la base de datos y el nombre de usuario para configurarla. Modificaremos el archivo `config/database.yml` de la siguiente forma:

![rails09](/images/practica_rails/rails09.png)

- Y ejecutamos el comando:

~~~
docker-compose up
~~~

![rails10](/images/practica_rails/rails10.png)

- En otro terminal, creamos la BBDD con el comando:

~~~
docker-compose run web rake db:create
~~~

![rails11](/images/practica_rails/rails11.png)

#### 4. Todo listo, solo queda...

- Ya lo tenemos todo listo, tan solo hay que visitar `localhost:3000` y...

![rails12](/images/practica_rails/rails12.png)



***

#### Ya lo tenemos!!

> **Recursos:**
>
> <https://github.com/Drakmah/PracticasPeps/tree/main/practicarails>

