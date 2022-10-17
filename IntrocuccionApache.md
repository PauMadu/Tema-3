# Introducción a Apache.
Este trabajo recopila información para introducirnos el entorno Apache; conocer un poco su historia la cual empezó hace más de dos décadas, su importante funcionalidad y como Instalarlo mediante comandos en la terminal de Linux.

## Palabras clave.
1. Historia.
2. Funcionalidad.
3. Instalación.

## Índice. 
- Palabras clave
- Contexto.
    - Qué es Apache.
- Instalación.
     - Instalar.
     - Ajustar el Firewall.
     - Verificar ejecución.
     - Administrar el proceso.
- Configuración.
     - Creación del sitio web.
     - Configuración del Virtualhost.
     - Activación del archivo VirtualHost.
- Que se ha conseguido?
- Valoración personal.
- Motivación.
- Bibliografía.

## Contexto.
El proyecto está realizado en el centro didáctico "Ágil Centros", en la asignatura de Despliegue de Aplicaciones Web donde ha sido uno de los proyectos que los alumnos han tenido que realizar para introducirse a Apache.
    
### ¿Qué es Apache?
Trabajamos con el entorno Apache. Apache es un servidor web HTTP de código abierto, y es el más usado del mundo.
Apache ofrece muchas herramientas y características, como módulos que se cargan de forma dinámica, una sólida compatibilidad con medios y amplia integración con otras herramientas de software.
Su desarrollo comenzó en 1995, y apenas un año después ya fué el servidor HTTP más utilizado hasta la actualidad. Además Apache consistía solamente en un conjunto de parches para aplicar al servidor NCSA, y de ahí salió su reconocido nombre.

Pero antes de instalarlo, deberemos tener nuestra cuenta de Linux con privilegios sudo (administrador).

## Instalación Apache.
**1.** Para **instalar** Apache en **Ubuntu** primeramente actualizaremos los paquetes locales (para ver los últimos cambios). Deberemos escribir el siguiente código       en la **Terminal**:  
    ```
    $ sudo apt update
    ```  
    Después instalaremos el paquete **"Apache2"**:  
    ```
    $ sudo apt install apache2
    ```  
**2.** Antes de probar Apache, es necesario modificar los **ajustes de firewall** para permitir el acceso externo a los puertos web predeterminados.  
    _(Apache se registra con UFW)_  
    ```  
    $ sudo ufw app list
    ```  
    Y para que el cortafuegos permita el tráfico en el puerto 80:  
    ```  
    $ sudo ufw allow 'Apache'
    ```  
    Y deberemos verificar el cambio:  
    ```
    $ sudo ufw status
    ```  
    Si nos indica Disabled, o inactivo pondremos:  
    ```
    $ sudo ufw enable
    ```  
**3.** Y por último deberemos verificar si se encuentra en ejecución:  
    ```
    $ sudo systemctl status apache2
    ```

**También podemos verificar la ejecución...** Abriendo otra terminal y poniendo 
```
$ hostname -I
```
Obtendremos la dirección ip, la cual deberemos poner en el navegador web mediante: 
```
http:// (la direccion ip)
```

### 4. Administrar el proceso Apache.
- Para detener el servidor:
    ```
    $ sudo systemctl stop apache
    ```
- Para iniciar el servidor:
    ```
    $ sudo systemctl start apache2
    ```
- Para recargar Apache, y poder ver los cambios de configuración:
    ```
    $ sudo systemctl reload apache2
    ```
    
# Configuración.
Una vez instalado, y comprobado en www.localhost que tenemos nuestra página operativa. Pasaremos a la configuración y creación de nuestro sitio web.
**1.** Primeramente crearemos una carpeta en el sitio web,(lo hemos llamado gci):  
    ```sudo mkdir /var/www/gci/```  
    Y a continuación crearemos un html para el directorio:  
    Entramos dentro de la carpeta con: ```cd /var/www/gci/```  
    Y para crear el html: ```nano index.html```   
    Entonces ya podremos crear nuestro html a nuestro gusto, pero siempre siguiendo su estructura, por ejemplo;  
    ```<html>
    <head>
      <title> Título de mi increible pagina </title>
    </head>
    <body>
      <p> Y aquí pondremos nuestro html junto a imágenes, links, texto de todas <b>las formas</b> y estilos...</p>
    </body>
    </html>
    ```   
**2.** Luego configuraremos el archivo de configuración de VirtualHost.
    ```cd /etc/apache2/sites-available/```
    Nos aprovecharemos de la base que ya viene predefinida en cualquier archivo;  
    ```sudo cp 000-default.conf gci.conf```  
    Entonces ya podremos editar la configuración.  
    ```sudo nano gci.conf```  
    2.2 Como **paso opcional** siempre está bien poner nuestro correo electrónico, para que los usuarios puedan comunicarse 
        con nosotros si experimentan algún error. ```ServerAdmin ejemplo@gmail.com```  
    Queremos cambiar la dirección de nuestra página sea www (el nombre de nuestra página), en vez de HTML.. Entonces deberemos poner;  
    ```DocumentRoot /var/www/gci/```  
    Y junto al paso anterior, con el siguiente código haremos que al escribir lo siguiente en nuestro buscador nos lleve a nuestra página.
    ```ServerName gci.example.com``` 

**3.** Para finalizar la configuración de nuestro sitio web tendremos que activar el archivo de hosts virtuales;
    ```sudo a2ensite gci.conf```
    Y finalmente al poner; ```service apache2 reload``` reiniciamos Apache y cargará nuestra página.
    Pero nos saltará un error, por tanto para solucionarlo pondremos la siguiente linea; ```sudo gedit /etc/hosts```, y se 
    nos abrirá un bloc de no en el cual tendremos que poner 127.0.0.1 y la ruta de nuestro sitio, por ejemplo: 
    ```127.0.0.1 gci.example.com```.  
    
**Fin -->** Ahora ya podremos buscar nuestro sitio web en el navegador y obtendremos la página con su contenido

## ¿Qué se ha conseguido?
Con este trabajo realizado se ha conseguido instalar el entorno Apache, crear una carpeta para almacenar el contenido del sitio web, y por último lanzar un sitio web, en pocos pasos de forma rápida y sencilla.

## Valoración personal.
Personalmente estoy contento de mi progreso y aprendizaje ya que una de las cosas más importantes para mi ha sido entender cómo conectar todos los contenidos aprendidos en este grado los cuales van desde JavaScript, PHP, HTML, CSS y muchos mas, par que todos juntos pùedan funcionar con una sinergia y lógica y formen mi pagina web.

## Motivación.
La motivación que me ha llevado a realizar este trabajo consiste en obtener conocimientos sobre Apache, para poder conseguir controlar perfectamente este servidor HTML y sacarle todo el partido a sus características y herramientas. A esto también le tenemos que añadir el aprendizaje a lanzar un sitio web, y lo más relevante para mi, entender como juntar todos los contenidos aprendidos en este grado, para que todos juntos funcionen y muestren la página creada.

## Bibliografía.
[Descripción de Apache](https://es.wikipedia.org/wiki/Servidor_HTTP_Apache)  
[Seguir la Instalacion](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-20-04-es)  
[Pagina pasos configuración](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview)  
[Pagina para solucionar el error del sitio web](https://www.desarrollolibre.net/blog/apache/que-son-y-como-emplear-los-virtualhost-en-apache)
