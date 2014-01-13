Práctica 3: Diseño de máquinas virtuales.
===========================================

En esta práctica vamos buscar la configuración optima de una máquina virtual que opera con Ubuntu 12.04 de 64 bits.
Montaré la máquina virtual sobre WMware Player y, gracias a su interfaz, configuraré diversos aspectos como cantidad de RAM y número de procesadores para realizar una comparativa de configuraciones.
Las especificaciones del equipo en el que se va a realizar la práctica son:

  - Procesador: Intel Core i7 4700MQ
  - RAM: 8GB


Preparación de la máquina virtual.
=====================================

Inicialmente, instalo los paquetes necesarios para poder realizar la prueba de rendimiento. Estos son Apache y sus utilidades:

>sudo apt-get install apache2
>sudo apt-get install apache2-utils

Una vez instalado Apache, procedemos a configurarlo para que muestre una página web. Para ello, se debe copiar el archivo "index.html" de la web junto con sus archivos (imágenes, fuentes, etc) en la carpeta /var/www/, que es donde Apache aloja las webs para ser mostradas. La web la he obtenido de http://norfipc.com/, página que tiene a disposición páginas de prueba. Para copiar y pegar archivos en dicha carpeta se necesita ser superusuario, por lo que utilizaremos estos comandos:

> sudo cp web.zip /var/www
> sudo unzip web.zip

La web está comprimida en un .zip que copiamos y descomprimimos en el directorio de Apache para concluir la configuración.
Comprobamos que la web funciona adecuadamente escribiendo "localhost" en el navegador de la máquina virtual. Como podemos ver en la siguiente imagen, funciona correctamente.

![im1](https://dl.dropbox.com/s/m4c62x7ttwqg9wx/Captura%20de%20pantalla%20de%202014-01-13%2001%3A14%3A21.png)

Configuraciones de la máquina virtual.
=======================================

Voy a hacer las pruebas de rendimiento con una serie de configuraciones de la máquina virtual. Todas están realizadas en Ubuntu 12.04 64 bits. Estas configuraciones se detallan a continuación:

Configuración 1) --> RAM: 512 MB - Cores: 1   
                        
                  
Configuracion 2) --> RAM: 1024 MB - Cores: 1
                 

Configuración 3) --> RAM: 512 MB - Cores: 2      
                                            
                  
Configuracion 4) --> RAM: 1024 MB - Cores: 2
                 
                  
Configuración 5) --> RAM: 512 MB - Cores: 4      
                                           
                  
Configuracion 6) --> RAM: 1024 MB - Cores: 4

                 
Configuracion 7) --> RAM: 2048 MB - Cores: 2


Benchmarks
============

Ya está todo preparado para proceder al analisis de los recursos de la máquina virtual. Para ello utilizaremos la herramienta ab (Apache Benchmark) que viene incluida en el paquete apache2-utils. Está nos proporcionará multitud de información, pero en este caso, nos interesa la velocidad de respuesta y de transferencia. Usaremos dos parámetros en ab, -n (número de peticiones o consultas) y -c (concurrencia o número de usuarios accediendo).

> ab -n 1000 -c 10 http://127.0.0.1/index.html

Esto quiere decir que vamos a realizar 1000 peticiones, con una concurrencia de 10 usuarios.

Una vez realizadas las pruebas, obtenemos las siguientes tablas con los resultados. He realizado tres pruebas por cada configuración de las anteriormente mencionadas y, posteriormente, he realizado la media de las tres pruebas, con el objetivo de obtener unos resultados mas fiables.

![im2](https://dl.dropbox.com/s/cytc1gqdhij9la3/Captura%20de%20pantalla%20de%202014-01-13%2002%3A54%3A04.png)





















