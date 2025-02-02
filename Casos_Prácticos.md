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

<img src=

## g) Autentificación, autorizacición y control de acceso


## h) Autentificación, Autorización y Control de acceso


## i) Seguridad


