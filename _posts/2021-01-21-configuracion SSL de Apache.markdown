---
typora-root-url: ../
layout: post
title:  "Configuración SSL de Apache"
categories: puesta en producción segura

---
# Configuracion SSL de Apache

En esta practica hemos creado un certificado auto-firmado para Apache y configurado el servidor Apache; De esta forma el trafico que tenemos por ejemplo en una intranet, estará cifrado. A continuacion mostramos el archivo de configuracion *default-ssl.conf*:

![conf-ssl](/images/ssl-apache/conf-ssl.JPG)



Modificamos tambien el archivo hosts para simular el dominio, y aunque el navegador nos indicará que la página no es segura, puesto que la hemos autofirmado, nuestra conexión ahora estará cifrada:![01](/images/ssl-apache/01.JPG)

![02](/images/ssl-apache/02.JPG)

![03](/images/ssl-apache/03.JPG)

![04](/images/ssl-apache/04.JPG)

![05](/images/ssl-apache/05.JPG)