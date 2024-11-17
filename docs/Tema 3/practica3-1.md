# Práctica 3.1.- Instalación de Tomcat

## 1.- Instalación de Tomcat

El primer paso para instalar **Tomcat** será abrir el puerto por defecto usando el comando:<br>
`sudo ufw allow 8080`.<br>
![alt text](./assets/practica3.1/image-2.png)

Después ejecutamos un `sudo apt update` para actualizar los paquetes.<br>
![alt text](./assets/practica3.1/image-3.png)

El siguiente paso será instalar Java mediante el comando:<br>
`sudo apt install default-jre`.<br>
![alt text](./assets/practica3.1/1.png)

Verificamos la versión instalada de java con `java -version`.<br>
![alt text](./assets/practica3.1/2.png)

Ahora instalamos **Apache Tomcat** y el **Tomcat-admin** a través del comando<br>
`sudo apt install tomcat10 tomcat10-admin`.<br>
![alt text](./assets/practica3.1/3.png)

Tras instalar **Tomcat**, modificaremos el archivo **tomcat_users.xml** con el comando: <br>
`sudo nano /etc/tomcat10/tomcat_users.xml` y deberemos añadir: <br>

```
<role username="manager-gui> />
<user username="manager" password="TuContraseña" roles="manager-gui />
```

Tras añadirlo en nuestro fichero, el archivo quedará de la siguiente forma:<br>
![alt text](./assets/practica3.1/4.png)

Ahora que tomcat ya está instalado y nuestro usuario **manager-gui** creado, comprobamos que esta instalado correctamente a través de los comandos:<br>
`sudo systemctl start tomcat10`<br>
`sudo systemctl status tomcat10`<br>
![alt text](./assets/practica3.1/5.png)

Si todo ha ido bien, accedemos en el navegador a la dirección `localhost:8080/manager/html`, donde debe aparecernos algo así:<br>
![alt text](./assets/practica3.1/image-11.png)

Al iniciar sesión, deberá aparecernos esta pantalla.<br>
![alt text](./assets/practica3.1/image-12.png)

## 2.- Despliegue manual mediante la GUI de administración

Ahora vamos a realizar un despliegue de una aplicación **.WAR**, para ello:

1. Iniciamos sesión con el usuario previamente creado.
2. Buscamos el apartado que nos permite desplegar una aplicación:<br>
   ![alt text](./assets/practica3.1/image.png)
3. Buscamos la sección que nos permite desplegar un **WAR** manualmente y seleccionamos nuestro archivo. En mi caso el siguiente archivo: https://tomcat.apache.org/tomcat-6.0-doc/appdev/sample/<br>
   ![alt text](./assets/practica3.1/image-14.png)
4. Por último accedemos a `localhost:8080/sample` y veremos el contenido de nuestro **.war** y se vería algo así:<br>
   ![alt text](./assets/practica3.1/image-17.png)

## 3.- Despliegue con Maven

Ahora desplegaremos una aplicación realizada con **Maven**, para ello deberemos:

1. Actualizar los repositorios con `sudo apt update`.<br>
   ![alt text](./assets/practica3.1/image-18.png)

2. Instalamos **Maven** con `sudo apt install maven`.<br>
   ![alt text](./assets/practica3.1/6.png)

3. xxComprobamos que **Maven** se ha instalado correctamente viendo la versión instalada con el comando `mvn --v`.<br>
   ![alt text](./assets/practica3.1/image-20.png)

### 3.1.- Configuración de Maven

1. Por temas de seguridad, deberemos tener 2 usuarios, uno que tenga el rol de `manager-script` y otro que tenga `manager-gui`. Para ello, modificaremos el archivo de usuarios de **Tomcat** con <br>
   `sudo nano /etc/tomcat10/tomcat-users.xml`.<br>
   ![alt text](./assets/practica3.1/image-22.png)

2. Añadimos un nuevo **rol** para **manager-script** y el nuevo usuario, donde le asignaremos una contraseña que nosotros queramos.<br>
   ![alt text](./assets/practica3.1/7.png)
   Guardamos los cambios con `Ctrl + O` y salimos con `Ctrl + X`.

3. Ahora editamos el archivo `etc/maven/settings.xml` para indicarle a Maven, un identificador para el servidor sobre el que vamos a desplegar.<br>
   ![alt text](./assets/practica3.1/8.png)

4. Modificamos el **POM** del proyecto para que haga referencia a que el despliegue se realice con el plugin de **Maven**. Para esto, clonaremos un repositorio de github con el comando <br>
   `git clone https://github.com/cameronmcnz/rock-paper-scissors.git`<br>
   ![alt text](./assets/practica3.1/image-25.png)

5. Nos siutuamos dentro del proyecto que hemos creado con:<br>
   `cd rock-paper-scissors`<br>
   ![alt text](./assets/practica3.1/image-26.png)

6. Cambiamos de rama: <br>
   `git checkout patch-1`<br>
   ![alt text](./assets/practica3.1/image-27.png)

7. Tras esto, editamos el archivo **POM** con el comando <br>
   `sudo nano pom.xml`.<br>
   ![alt text](./assets/practica3.1/image-28.png)

8. Añadimos el siguiente bloque<br>

```
        <plugin>
        <groupId>org.apache.tomcat.maven</groupId>
        <artifactId>tomcat7-maven-plugin</artifactId>
        <version>2.2</version>
        <configuration>
            <url>http://localhost:8080/manager/text</url>
            <server>IdDeTuServer</server>
            <path>/myapp</path>
        </configuration>
        </plugin>
```

9. Quedaría de la siguiente forma:<br>
   ![alt text](./assets/practica3.1/9.png)

10. Hacemos un **deploy** con el comando <br>
    `mvn tomcat7:deploy`<br>
    ![alt text](./assets/practica3.1/11.png)

    Si todo ha ido bien, nos aparecerá un mensaje de color **verde** que pondrá **Build Success**, indicandonos que se ha desplegado correctamente:<br>
    ![alt text](./assets/practica3.1/12.png)

11. Por último, accedemos a nuestro navegador a la dirección `localhost:8080/tuPath`, donde **tuPath** es el **path** que hayas configurado en el **pom.xml** del proyecto, y deberiamos ver lo siguiente:<br>
    ![alt text](./assets/practica3.1/13.png)

## 4.- Cuestiones

### 4.1.- Habéis visto que los archivos de configuración que hemos tocado contienen contraseñas en texto plano, por lo que cualquiera con acceso a ellos obtendría las credenciales de nuestras herramientas.<br> En principio esto representa un gran riesgo de seguridad, ¿sabrías razonar o averigüar por qué esto está diseñado de esta forma?

Esta diseñado de esta manera por simplicidad y compatibilidad ya que **Tomcat** no incluye por defecto un sistema que cifre o gestione las contraseñas. Esto es un gran problema de seguridad ya que cualquier persona podría acceder a los datos sin estar autorizadas.
Una solución para cifrar las contraseñas y resolver este problema de seguridad sería a través del la herramienta `Apache Tomcat Jasypt`.
