# Esquema de Red

## Adaptadores
En esta práctica vamos a usar dos tipos de adaptadores
  - Adaptador puente
  - Adaptador en Red Interna

<img src=https://github.com/AleBayo/nginx/blob/main/img/Foto%20de%20adaptadores.png>

## Configuración

Vamos a poner el Adaptador puente en DHCP y el adaptador por red interna en una ip estatica, para ponerla en estatica tendremos que en la terminal poner el comando `cd /etc/network` y despues el comando  `nano /etc/Network/interfaces`

<img src=https://github.com/AleBayo/nginx/blob/main/img/ocnfiguracion%20de%20red.png>

Despues de la configuración vamos a reinniciar el servicio con el comando `systemctl restart NetworkManager`, al cual despues le hacemos el comando `systemctl status NetworkManager` para confirmar que este activo

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20114621.png>

Para confirmar que todo ha ido bien hacemos el comando `ip a` para confirmar que las ip's se han puesto bien

<img src=https://github.com/AleBayo/nginx/blob/main/img/Captura%20de%20pantalla%202025-02-02%20115522.png>
