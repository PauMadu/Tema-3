# Introduccion a Apache.
Este trabajo recopila informacion para introducirnos el entorno Apache; conocer un poco su historia la cual empezo hace mas de dos decadas, su importante funcionalidad y como Instalarlo mediante comandos en la terminal de Linux.

## Palabras clave.
1. Historia.
2. Funcionalidad.
3. Instalacion.

## Indice. 
- Palabras clave
- Contexto.
    - Que es Apache.
- Instalacion.
     - Instalar.
     - Ajustar el Firewall.
     - Verificar ejecución.
     - Administrar el proceso.
- Bibliografía.

## Contexto.
El proyecto esta realizado en el centro didactico "Agil Centros", en la asignatura de Despliegue de Aplicaciones Web donde ha sido uno de los proyectos que los alumnos han tenido que realizar para introducirse a Apache.
    
### Que es Apache?
Trabajamos con el entorno Apache. Apache es un servidor web HTTP de código abierto, y es el más usado del mundo.
Apache ofrece muchas herramientas y caracteristicas, como módulos que se cargan de forma dinámica, una sólida compatibilidad con medios y amplia integración con otras herramientas de software.
Su desarrollo comenzó en 1995, y apaenas un año despues ya fué el servidor HTTP mas utilizado hasta la actualidad. Además Apache consistía solamente en un conjunto de parches para aplicar al servidor NCSA, y de ahi salió su reconocido nombre.

Pero antes de instalarlo, deberemos tener nustra cuenta de Linux con privilegios sudo (administrador).

## Instalacion Apache.
**1.** Para **instalar** Apache en **Ubuntu** primeramente actualizaremos los paquetes locales (para ver los ultimos cambios). Deberemos escribir el siguiente codigo       en la **Terminal**:  
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
    Si nos indica Dissabled, o inactivo pondremos:  
    ```
    $ sudo ufw enabed
    ```  
**3.** Y por ultimo deberemos verificar si se encuentra en ejecucion:  
    ```
    $ sudo systemctl status apache2
    ```

**Tambien podemos verificar la ejecucion...** Abriendo otra terminal y poniendo 
```
$ hostname -I
```
Obtendremos la direccion ip, la cual deberemos poner en el navegador web mediante: 
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
- Para recargar Apache, y poder ver los cambios de configuracion:
    ```
    $ sudo systemctl reload apache2
    ```
    
## Motivación.


## Bibliografia.
[Descripción de Apache](https://es.wikipedia.org/wiki/Servidor_HTTP_Apache)  
[Seguir la Instalacion](https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-20-04-es)
