# P5.-DNS---Docker-Compose
**Configura un contenedor coa imaxe oficial de bind9 usando docker-compose.**  
**Usa os volumes como se explica no setup da imaxe**  
**Unha comprobado que o contenedor funciona, sube a GitHub o ficheiro nun repo.**

Para configurar un contenedor o primeiro debemos facer é crear un ficheiro yaml no cal estableceremos todos os parametros. Dimoslle o nome de ```docker-compose.yml```. O código é o seguinte:  
services:  
  bind9:   
    image: internetsystemsconsortium/bind9:9.18   
    container_name: Practica5_bind9   
    ports:  
      - 54:53/udp  
      - 54:53/tcp  
      - 127.0.0.1:953:953/tcp   
    volumes:  
      - ./etc/bind:/etc/bind  
      - ./var/cache/bind:/var/cache/bind  
    restart: always   


Ademas disto configuraremos dous directorios dentro de este repositorio que serviran como volumes. A carpeta ```/etc/bind``` e a carpeta ```/var/cache/bind```. A primeira de todos a utilizaremos para configurar o ```archivo named.conf```, este arquivo é crucial para configurar o servidor BIND, conten a configuración principal e o último contén o espazo de traballo do funcionamento de BIND.  

Para a posterior comporbación utilziaremos o comando ```docker compose up -d``` o parámetro -d é para que se execute en segundo plano. E este é o resultado:

[+] Running 2/2  
 ✔ Network p5-dns---docker-compose_default  Created                        0.1s   
 ✔ Container Practica5_bind9                Started                        0.3s   