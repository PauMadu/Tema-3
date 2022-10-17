
# Configuración.
Una vez instalado, y comprobado en www.localhost que tenemos nuestra pagina operativa. Pasaremos a la configuracion y creacion de nuestro sitio web.
1. Primeramente crearemos una carpeta en el sitio web,(lo hemos llamado gci):  
    ```sudo mkdir /var/www/gci/```  
    Y a continuación crearemos un html para el directorio:  
    Entramos dentro de la carpeta con: ```cd /var/www/gci/```  
    Y para crear el html: ```nano index.html```   
    Entonces ya podremos crear nuestro html a nuesttro gusto, pero siempre siguiendo su estructura, por ejemplo;  
    ```<html>
    <head>
      <title> Titulo de mi increible pagina </title>
    </head>
    <body>
      <p> Y aqui pondremos nuestro html junto a imagenes, links, texto de todass <b>las formas</b> y estilos...</p>
    </body>
    </html>
    ```   
2. Luego configuraremos el archivo de configuración de VirtualHost.
    ```cd /etc/apache2/sites-available/```
    Nos aprovecharemos dde la base que ya viene predefinida en cualqioer archivo;  
    ```sudo cp 000-default.conf gci.conf```  
    Entonces yua podremos editar la configuración.  
    ```sudo nano gci.conf```  
    2.2 Como **paso opcional** siempre esta bien poner nuestro correo elecronico, para que los usuarios puedan comunicarse 
        con nosotros si experimentan algun error. ```ServerAdmin ejemplo@gmail.com```
    

## Que se ha conseguido?

## Valoración personal.

## Bibliografía.
[Pagina pasos configuración](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview)
