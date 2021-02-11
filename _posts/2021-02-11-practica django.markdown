---
typora-root-url: ../
layout: post
title:  "Práctica django"
categories: puesta en produccion segura

---
# Práctica django

> **Vamos a crear un servidor django en 7 cómodos pasos:**

#### Paso 1: Crear directorio de trabajo

Crearemos un directorio de trabajo donde se contendrán todos los ficheros del proyecto

***

#### Paso 2: Crear dockerfile

Creamos el fichero `Dockerfile ` en donde se definirán las imágenes de la aplicación y su configuración. Una vez creada la imagen, podremos ejecutar el contenedor.

![django01](/images/practica_django/django01.png)

***

#### Paso 3: Crear requirements.txt

Creamos (siempre dentro del directorio de nuestro proyecto) el archivo `requirements.txt`  en donde añadimos las siguientes líneas:

~~~~
Django>=3.0,<4.0
psycopg2-binary>=2.8
~~~~

De momento nuestro directorio queda así:

![django02](/images/practica_django/django02.png)

***

#### Paso 4: Creamos docker-compose

Siempre dentro del directorio del proyecto, creamos el archivo `docker-compose.yml` en donde indicaremos los servicios que vamos a usar: __db__ y __web__ .

Nuestro directorio tiene que tener en este punto este contenido:

![django03](/images/practica_django/django03.png)

***

#### Paso 5: Creamos el proyecto django

Mediante el siguiente comando, creamos el proyecto django:

~~~
sudo docker-compose run web django-admin startproject composeexample .
~~~

![django04](/images/practica_django/django04.png)

Como hemos ejecutado como sudo, los archivos creados tienen como propietario root, así que cambiamos el propietario a nuestro usuario mediante el comando:

~~~
sudo chown -R $USER:$USER .
~~~

![django05](/images/practica_django/django05.png)

***

#### Paso 6: Conectamos la base de datos

Para ello, modificamos el archivo `composeexample/settings.py` de nuestro proyecto, reemplazando 

~~~
DATABASES = ...
~~~

  por:

~~~
# settings.py
   
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres',
        'HOST': 'db',
        'PORT': 5432,
    }
}
~~~

***

#### Paso 7:  Ponerlo en ejecución

Ejecutamos el comando `docker-compose up` desde el directorio raíz de nuestro proyecto. En este momento, tenemos django en marcha:

![django07](/images/practica_django/django07.png)

![django08](/images/practica_django/django08.png)

***

#### Running !!

> **Recursos:**
>
> <https://github.com/Drakmah/PracticasPeps/tree/main/practicadjango>