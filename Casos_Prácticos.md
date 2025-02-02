# Casos prácticos

## a) Versión Instalada del nginx

Para ver la versión la cual tenemos instalada vamos a usar el comando ` sudo nginx -v`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20121241.png>

## b) Servicio asociado

Para comprobar que este funcionando perfectamente hacemos el comando `systemctl status nginx`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20121442.png>

## c) Ficheros de configuración

Para ver la configuración primero tenemos que hacer un `ls /etc/nginx`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20121715.png>

Para ver el archivo de configuración hacemos un `cd /etc/nginx` y despues `nano nginx.conf`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20121925.png>

## d) Página web por defecto

Para ocnfigurar la página wweb tenemos que hacer `nano  /var/www/html/index.nginx-debian.html` y modificarlo a nuestro placer

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20122455.png>

## e) Virtual Hosting

> Queremos que nuestro servidor web ofrezca dos sitios web, teniendo en cuenta lo siguiente: Cada sitio web tendrá nombres distintos. Cada sitio web compartirán la misma dirección IP y el mismo puerto (80). Los dos sitios web tendrán las siguientes características:
> 
> El nombre de dominio del primero será www.web1.org, su directorio base será /var/www/web1 y contendrá una página llamada index.html, donde sólo se verá una bienvenida a la página web1.
> 
> El nombre de dominio del primero será www.web2.org, su directorio base será /var/www/web2 y contendrá una página llamada index.html, donde sólo se verá una bienvenida a la página web2.

Creamos dos directotios para guardar ls información de las web `mkdir -p /var/web1` y `mkdir -p /var/web2`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20122950.png>

Ahora vamos a darles permisos `chown -R www-data:www-data /var/www/web1`, `chown -R www-data:www-data /var/www/web2` y para terminar de dar permisos `chown -R 755 /var/www`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20123640.png>

Vamos a crear en cada fichero web un index.html para quer la pagina tenga algo

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20124108.png>

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20124247.png>

Ahora vamos a añadir los dos directorios creados al servicio nginx para que se puedan usar y vamos a modificar el archivo `/etc/host` para que las direcciones de las web's tengan ip y se puedan buscar desde el buscador

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20124553.png>

Para confirmar que lo estamos haciendo bien vamos a nuiestro navegador y buscamos `www.web1.org` y `www.web2.org`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20124853.png>

## f) Autentificación, autorización y control de acceso

>www.web1.org se puede acceder desde la red externa y la red interna. www.web2.org sólo se puede acceder desde la red interna.

Modificamos los sitios que están habilitados a entrar a cada web `nano web1` y `nano web2`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20125742.png>

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20131316.png>

Ahora modificamos el archivo hosts con las ip's que permitimos

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20130205.png>

Vamos a comprobar que la red interna puede acceder a las dos páginas web, para ello vamos a usar el comando `curl --interface enp0s8 http://www.web1.org` y `curl --interface enp0s8 http://www.web2.org`, si no esta instalado el comando curl lo instalamos con `apt-get install curl`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20130804.png>

## g) Autentificación, autorizacición y control de acceso

> www.web1.org contiene un directorio llamado privado. Configura una autentificación básica. Sólo puede acceder usuarios válidos.

Vamos a poner una contraseña para que solo puedan acceder los usuarios admitidos

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20132041.png>

Ahora comprobamos que te pida acceso

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20132241.png>

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20132456.png>

## h) Autentificación, Autorización y Control de acceso

> www.web1.org contiene un directorio llamado privado. Desde la red externa pide autorización y desde la red interna NO.

Volvemos a modificar el archivo de web1 para volver a dar acceso

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20132815.png>

## i) Seguridad

> Configura el sitio virtual www.web1.org para que el acceso sea seguro.

Para que nuestra página web sea segura vamos a crear una contraseña privada con el comando `openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/selfigned.key -out /etc/ssl/certs/selfsigned.crt`

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20133536.png>

Modificamos el archivo de web1 para que use la contraseña creada

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20134031.png>
