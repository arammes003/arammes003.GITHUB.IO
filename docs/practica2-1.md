# Practica 2.1 - Instalación y configuración de un servidor web Nginx

## 1.- Instalación servidor

Para instalar el servidor de **NGINX** en nuestra máquina **Debian**, lo primero que tendremos que hacer es actualizar los repositorios con:
`sudo apt update`<br>

![alt text](./assets/practica2-1/1.png)<br>
Después lo que tenemos que hacer es instalar el paquete correspondiente para instalar nginx:
`sudo apt install nginx`<br>

![alt text](./assets/practica2-1/nginx.png)<br>
Cuando estemos en el proceso de instalación aparecerá un mensaje de '¿Desea continuar? [S/n]', en el cuál le deberemos decir que sí.<br>

Ahora tendremos que comprobar que **nginx** se ha instalado y este funcionando correctamente con el comando:
`systemctl status nginx`

![alt text](./assets/practica2-1/status_nginx.png)
<br>
Si todo está correcto, veremos un mensaje en verde: `active (running)`

## 2.- Creación de las carpeta del sitio web

Al igual que en Apache, todos los archivos que formarán parte de un sitio web se organiza en carpetas. Normalmente, estas carpetas van dentro de la ubicación `\var\www`.<br>
Ahora crearemos la carpeta de nuestro sitio web dentro de la ruta mencionada anteriormente con el siguiente comando: <br>
`sudo mkdir -p /var/www/nombre_web/html`<br>

- Donde `nombre_web` pondremos el nombre que queremos del sitio web sin espacios.<br>

![alt text](./assets/practica2-1/image.png)

Ahora accedemos a esa carpeta:<br>

![alt text](./assets/practica2-1/image-1.png)

Dentro de esa carpeta, deberemos clonar el siguiente repositorio de github: `https://github.com/cloudacademy/static-website-example`, en caso de no tener **git** instalado lo instalamos con `sudo apt install git`. <br>

![alt text](./assets/practica2-1/image-2.png)

Ahora clonamos el repositorio con el comando `sudo git clone https://github.com/cloudacademy/static-website-example`.<br>

![alt text](./assets/practica2-1/image-3.png)

Además, haremos que el propietario de los datos de esa carpeta sea del usuario www-data, que normalmente es el usuario del servicio web.
`sudo chown -R www-data:www-data /var/www/nombre_web/html`.<br>

![alt text](./assets/practica2-1/image-4.png)

Y le damos los permisos adecuados para que no nos de un error de acceso no autorizado al entrar en el sitio web con `sudo chmod -R 755 /var/www/nombre_web`.<br>

![alt text](./assets/practica2-1/image-5.png)

Ahora comprobamos que el servidor este funcionando y sirviendo páginas correctamente, para ello accedemos desde un navegador a: `http://IP-maq-virtual`.<br>

- Donde `IP-maq-virtual` es la dirección IP de tu máquina Debian. En caso de no saber cuál es, hacemos un `ip -a`.<br>

![alt text](./assets/practica2-1/image-6.png)

Ahora buscamos la dirección en el navegador de tu máquina física con `http://IP_maq_virtual` donde nos tendrá que aparecer la siguiente ventana:<br>

![alt text](./assets/practica2-1/11.png)

Esto significa que de momento todo esta funcionando correctamente.

# 3.- Configuración de servidor web NGINX

En **Nginx** hay dos rutas importantes. La primera es **`sites-available`**, que es donde se almacenan los archivos de configuración de los host virtuales. Es decir, cada uno de los sitios web que está almacenado en el servidor.<br>

Por otro lado, está **`sites-enabled`**, que contiene los archivos que almacenan la configuración de los sitios web que están habilitados.<br>

Por defecto, hay un archivo de configuración dentro de **`sites-available`**, que es la página web que hemos visto en el anterior paso.<br>

Para mostrar el contenido de nuetra web, debemos crear un bloque nuevo, para ello, crearemos un nuevo fichero de configuración en la ruta y con el comando siguiente: <br>
`sudo nano /etc/nginx/sites-available/tu_dominio`<br>

![alt text](./assets/practica2-1/image-7.png)

Y se nos abrirá esta ventana completamente vacía <br>

![alt text](./assets/practica2-1/image-8.png)

Dentro tendremos que poner este contenido para configurarlo correctamente:<br>

```
server {

        listen 80;
        listen [::]:80;
        root /ruta/absoluta/archivo/index;
        index index.html index.htm index.nginx-debian.html;
        server_name nombre_web;
        location / {
                try_files $uri $uri/ =404;
        }
}
```

![alt text](./assets/practica2-1/image-9.png)

Para guardar los cambios hacemos `Ctrl + O` y después `Ctrl + X` para salir.<br>

Ahora crearemos un archivo simbólico entre el archivo que acabamos de crear y el de sitios habilitados, para que así, se de de alta automáticamente, para ello utilizaremos el siguiente comando: <br>
`sudo ln -s /etc/nginx/sites-available/nombre_web /etc/nginx/sites-enabled/`, donde:

- **`nombre_web`**, es el nombre que le dimos anteriormente al servidor.<br>

![alt text](./assets/practica2-1/image-10.png)

Por último, reiniciamos el servidor de **nginx** para que la configuración se aplique correctamente con: `sudo systemctl restart nginx`.<br>

Si no aparece ningún mensaje de error es que esta todo funcionando correctamente:<br>

![alt text](./assets/practica2-1/image-11.png)

Por seguridad, para comprobar que el servidor esta activo, ponemos `sudo systemctl status nginx`.<br>

![alt text](./assets/practica2-1/image-12.png)

Si todo está bien aparecera un mensaje en verde de: **`active (running)`**<br>

# 4.- Comprobaciones

Como aún no tenemos un servidor DNS que traduzca las IPs a nombres, deberemos hacerlo de forma manual **editando** nuestro archivo `/etc/hosts` de **nuestra máquina física** para que así asocie la IP de la máquina virtual a nuestro nombre del server.<br>

En caso de estar en **Linux**, modificaremos el archivo: `/etc/hosts`.<br>

Y en Windows: `C:\Windows\System32\drivers\etc\hosts`.

En esa línea añadimos la **dirección IP** junto al **nombre** de nuestro **servidor**, de la siguiente manera: `192.168.X.X nombre_web`;<br>

En caso de no saber la **direción IP** de vuestro servidor, ponemos en la **terminal** de nuestra máquina Debian `ip a`.<br>

![alt text](./assets/practica2-1/image-14.png)

Ahora, añadimos una línea con lo mencionado anteriormente.<br>

![alt text](./assets/practica2-1/image-13.png)

# 5.- FTP

En caso de querer tener varios sitios webs en el mismo servidor de **nginx**, tendremos que repetir todos los pasos anteriores con el nuevo nombre de dominio.

## 5.1.- Configurar servidor SFTP en Debian

En primer lugar, lo instalaremos desde los repositorios con estos comandos:<br>

`sudo apt-get update && sudo apt-get install vsftpd`<br>

![alt text](./assets/practica2-1/vsftpd.png)

Ahora creamos una carpeta en nuestro **home** de Debian con: <br>
`mkdir /home/nombre_usuario/ftp`, donde:

- `nombre_usuario` es el nombre del usuario en la máquina virtual.<br>

  ![alt text](./assets/practica2-1/mkdirftp.png)<br>

Ahora creamos un certificados de seguridad necesario para aportar la capa de cifrado de nuestra conexión a través del comando:<br>
`sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem`<br>

![alt text](./assets/practica2-1/openssl.png)

Una vez puesto este comando, nos empezarán a hacer distintas preguntas, las cuales podemos dejar en blanco o responder, en mi caso las dejo en blanco.<br>

![alt text](./assets/practica2-1/image-24.png)

Una vez realizado este paso, configuraremos el archivo de configuración de **vsftpd** con el comando: `sudo nano /etc/vsftpd.conf`.

Primero buscamos estas líneas, las cuales tendremos que eliminar:

```
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
```

![alt text](./assets/practica2-1/rsa1.png)

Y ponemos lo siguiente: <br>

```
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH

local_root=/home/nombre_usuario/ftp
```

![alt text](./assets/practica2-1/rsa.png)

Cuando guardemos los cambios, reiniciamos el servicio para que la nueva configuración se habilite: `sudo systemctl restart --now vsftpd`. Si todo va bien, no nos aparecerá ningún mensaje:<br>

![alt text](./assets/practica2-1/ipa.png)

Tras acabar la configuración, podremos acceder a nuestro servidor mediante un cliente de FTP, en mi caso será **Filezilla**, el cuál podemos descargar en nuestra máquina física a través de este enlace: [FileZilla](https://filezilla-project.org). <br>

![alt text](./assets/practica2-1/image-25.png)

Cuando termine el proceso de instalación, iniciamos la aplicacion y nos encontraremos con la siguiente ventana:<br>

![alt text](./assets/practica2-1/image-34.png)

Deberemos configurarlo de la siguiente manera:

- **Servidor**, pondremos la dirección IP de la máquina Debian.
- **Nombre de usuario**, pondremos el nombre de usuario de Debian.
- **Contraseña**, pondremos la contraseña del usuario
- **Puerto**, será el 21 para conectarnos usando los certificados que hemos generado antes.<br>
  Quedaría de la siguiente manera:<br>

![alt text](./assets/practica2-1/image-27.png)

Ahora damos clic en **`Conexión rápida`** y nos saltará un aviso a propósito del certificado, pulsamos en aceptar ya que este peligro lo hemos generado nosotros mismos:<br>

![alt text](./assets/practica2-1/image-23.png)

Una vez que ya estemos conectados, buscaremos en la sección izquierda de la pantalla la carpeta donde tengamos el **`.zip`** y en la parte derecha seleccionaremos la carpeta donde queremos subirla, haciendo doble click o utilizando el **`botón derecho > subir`**.

![alt text](./assets/practica2-1/image-28.png)

Otra opción es conectarnos mediante **SFTP**, que para ello tendriamos que:

- En servidor pondremos: **`sftp://dirección_ip`**
- Quitaremos la contraseña.
- Pondremos el puerto 22.

Quedaría de la siguiente manera:

![alt text](./assets/practica2-1/image-30.png)

Hacemos click en **`Conexión rápida`** y empezará a conectarnos con el servidor **Debian**. Devido a que estamos usando claves FTP para conectarnos, nos aparecerá un aviso parecido al que nos salía al conectarnos por primera vez por SSH a nuestra **Debian**, que aceptamos porque sabemos que no entraña ningún peligro en este caso:

![alt text](./assets/practica2-1/image-29.png)

Aquí nos conecta al `/home` del usuario, en vez de al `ftp`.
Como vemos si accedemos al directorio `/ftp`, aparece el archivo que hemos subido anteriormente.

![alt text](./assets/practica2-1/image-31.png)

Ahora vamos a descomprimir el archivo desde nuestra máquina **Debian**, para ello usamos el comando: `unzip nombre_archivo.zip -d /nombre/directorio`.

![alt text](./assets/practica2-1/image-32.png)

Una vez ese paso está completado, veremos que el archivo se encuentra en el directorio donde lo habíamos descomprimido, que en mi caso es en el escritorio.

![alt text](./assets/practica2-1/image-33.png)

# 6.- HTTPS

En este apartado le añadiremos a nuestro servidor una capa de seguridad necesaria por seguridad. Haremos que todos nuestros sitios web alojados hagan uso de certificados SSL y se acceda a ellos por medio de HTTPS.

El primer paso será generar un **Certificado SSL**, para ello usaremos el comando:<br>
`sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt
`
![alt text](./assets/practica2-1/image34.png)

Nos pedirá una serie de datos las cuales podemos dejar en blanco:

![alt text](./assets/practica2-1/image35.png)

Ahora tendremos que configurar el fichero `/etc/nginx/sites-available/nombre_dominio`, a través de `sudo nano` y pondremos lo siguiente:

![alt text](./assets/practica2-1/image36.png)

Guardamos los cambios con `Ctrl + O` y salimos con `Ctrl + X`.

Tras eso comprobamos que la sintaxis esté bien con `sudo nginx -t`, si no hay problemas aparecerá un mensaje de `syntax is ok`:

![alt text](./assets/practica2-1/image39.png)

Ahora reiniciamos nuestro servidor de **nginx** para que se activen los cambios con `sudo systemctl restart nginx`. Si todo va bien no aparecerá ningún mensaje de error:

![alt text](./assets/practica2-1/image37.png)

Y en nuestra máquina añadimos la dirección ip de la máquina Debian:

![alt text](./assets/practica2-1/image40.png)

Y ya podemos acceder en nuestro navegador a la dirección y veremos la siguiente ventana:

![alt text](./assets/practica2-1/imagefin.png)

# 7.- Cuestiones finales

### Cuestión 1: ¿Qué pasa si no hago el link simbólico entre `sites-available` y `sites-enabled` de mi sitio web?

Si no hacemos el enlace el stio web no será visible, ya que el archivo que habilita los servidores web es `sites-enabled`

### Cuestión 2: ¿Qué pasa si no le doy los permisos adecuados a `/var/www/nombre_web`?

Si no le damos los permisos adecuados, lo más probable es que ocurran problemas a la hora de intentar acceder al sitio web, ya que si no tenemos permisos de lectura y en algunos casos de ejecución de archivos y directorios, podemos encontrarnos con errores a la hora de acceder como:

- `403 Forbidden`, que ocurre cuando el servidor no tiene permiso para acceder al directorio.
