# Introduccion a Apache.


## Indice. 


## Palabras clave.



## Que es Apache?
El servidor HTTP Apache es el más usado del mundo.
Ofrece muchas características, como módulos que se cargan de forma dinámica, una sólida compatibilidad con medios y amplia integración con otras herramientas de software.

Pero antes de instalar deberemos tener nustra cuenta de Linux con privilegios sudo (administrador).

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
    
    
    
    ## Bibliografia.
    https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-20-04-es
