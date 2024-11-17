# Práctica 3.2: Despliegue de aplicaciones con Node Express

El primer paso para esta práctica sera parar el servidor **Tomcat**, ya que si no, este nos dará problemas, para ello lo paramos con el comando: <br>
`sudo systemctl stop tomcat10`
![alt text](./assets/practica3.2/image.png)

## 1.- Instalación de Node.js, Express y test de la primera aplicación

Para instalar **NodeJS**, el primer paso es actualizar los paquetes del sistema mediante un `sudo apt update`.<br>
![alt text](./assets/practica3.2/image-1.png)

Tras actualizar los paquetes del sistema, instalamos **NodeJS** con el comando `sudo apt -y install nodejs npm`.<br>
![alt text](./assets/practica3.2/image-2.png)

Cuando lo tengamos instalado, instalamos tambien **ExpressJS** con el comando `sudo npm install -g express`.<br>
![alt text](./assets/practica3.2/image-3.png)

Ahora creamos un nuevo directorio con `mkdir` donde crearemos nuestra primera aplicacion de prueba. Despues nos meteremos dentro de la carpeta con `cd` e inicializamos el proyecto con el comando `npm init -y`.<br>
![alt text](./assets/practica3.2/image-4.png)

Ahora instalamos **ExpressJS** localmente en este proyecto con el comando `npm install express`.<br>
![alt text](./assets/practica3.2/image-5.png)

Tras eso creamos un nuevo fichero con `sudo nano app.js` donde configuraremos nuestra primera app y añadimos el siguiente bloque:<br>

```
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
    res.send('Hello. Welcome to this blog')
})

app.listen(port, () => {
    console.log(`Example app listening at http://localhost:${port}`)
})
```

Quedaria de la siguiente forma:
![alt text](./assets/practica3.2/image-6.png)

Y por ultimo corremos la aplicación `node app.js` y deberiamos ver en la consola el siguiente mensaje: <br>
![alt text](./assets/practica3.2/image-7.png)

Y si accedemos al navegador veremos el contenido del archivo: <br>
![alt text](./assets/practica3.2/image-8.png)

## 2.- Despliegue de una nueva aplicación

Para este paso, clonaremos un repositorio de **github** de un proyecto ya creado con el comaando<br>
`git clone https://github.com/contentful/the-example-app.nodejs.git`<br>
![alt text](./assets/practica3.2/image-9.png)

Nos metemos dentro del directorio con `cd the-example-app.nodejs` e instalamos las librerias neecesarias con `npm install`<br>
![alt text](./assets/practica3.2/image-10.png)

Cuando se complete la instalaciun de las librerias, podremos iniciar la aplicacion con el comando `npm run start:dev`<br>
![alt text](./assets/practica3.2/image-11.png)

Nos metemos en el navegador y vemos el contenido:<br>
![alt text](./assets/practica3.2/image-12.png)

## 3.- Cuestiones

1. <b>Cuando ejecutáis el comando npm run start:dev, lo que estáis haciendo es ejecutar un script. ¿Donde podemos ver que script se está ejecutando?</b><br>
   En el fichero **package.json**. En este fichero estan establecidos todos los comanmdos disponibles relaacionados con la aplicacion.
   ![alt text](./assets/practica3.2/image-13.png)
   <b>¿Qué comando está ejecutando?</b><br>
   Esta ejecutando **node ./bin/www**.

# Parte 2.- Despliegue con Netlify

Para comenzar con el despliegue en Netlify, empezaremos clonando un nuevo repositorio de **github** con `git clone`, que será `https://github.com/StackAbuse/color-shades-generator`<br>
![alt text](./assets/practica3.2/image-14.png)

Accedemos al repositorio que acabamos de crear con `cd` e instalamos los módulos necesarios de **netlify** con el comando `sudo npm install netlify-cli -g`<br>
![alt text](./assets/practica3.2/image-15.png)

El siguiente paso será crearnos una cuenta en **Netlify** y generar un **token**. Después de registrarnos veremos la siguiente pantalla: <br>
![alt text](./assets/practica3.2/image-16.png)

Pulsamos en **New access token** en el apartado de **Personal access tokens** y seguimos los siguientes pasos:<br>
![alt text](./assets/practica3.2/image-17.png)

Tras eso, pulsamos en `Generate Token` y ya tendremos nuestro token disponible. El siguiente paso es exportar nuestro token almancenandolo en una variable, eso lo hacemos con el comando: <br>
`export NETLIFY_AU $Token`.<br>
![alt text](./assets/practica3.2/image-18.png)

Ahora ya podremos loguearnos con `netlify login`. Tras poner este comando se nos abrirá el navegador pidiendo que autoricemos, pulsamos en autorizar y nos aparecerá lo siguiente en la terminal: <br>
![alt text](./assets/practica3.2/image-19.png)

Primero, deberemos instalar todas las dependencias con el comando `npm install`<br>
![alt text](./assets/practica3.2/image-25.png)

Y cuando ya las tengamos instaladas hacemos un `npm run build`<br>
![alt text](./assets/practica3.2/image-26.png)

Tras esto, ya podemos hacer un `netlify deploy` para desplegar nuestra aplicación. <br>

1. Seleccionamos la opcion de `Crear y configurar un nuevo sitio`.
2. Seleccionamos el `Equipo`.
3. Asignamos un nombre.
4. Asignamos la ruta de despliegue del proyecto clonado, es decir, `./build`.
   ![alt text](./assets/practica3.2/image-21.png)

Si todo ha ido bien, nos apareceran estos mensajes: <br>
![alt text](./assets/practica3.2/image-22.png)

Cogemos la direccion del apartado `Website draft URL` y comprobamos que se vea el contenido:<br>
![alt text](./assets/practica3.2/image-23.png)

Ahora realizaremos el despliegue a producción con el comando: `netlify deploy --prod`<br>
![alt text](./assets/practica3.2/image-24.png)

Cogemos el último enlace y comprobamos que se ve el contenido:<br>
![alt text](./assets/practica3.2/image-27.png)

## 2.1.- Despliegue mediante conexión con Github

Para realizar este paso, vamos a eliminar el despliegue que habíamos creado anteriormente.<br>
![alt text](./assets/practica3.2/image-28.png)
![alt text](./assets/practica3.2/image-29.png)

Ahora eliminamos el repositorio que clonamos anteriormente con el comando `rm -rf color-shades-generator`:<br>
![alt text](./assets/practica3.2/image-30.png)

Tras estos pasos, importamos un archivo **.zip** de un repositorio a través del comando: <br>
`wget https://github.com/StackAbuse/color-shades-generator/archive/refs/heads/main.zip`<br>
![alt text](./assets/practica3.2/image-31.png)

Tras importar el archivo, creamos un nuevo directorio con `mkdir` donde descomprimiremos el archivo con el comando `sudo unzip main.zip -d $NombreDirectorio`.<br>
![alt text](./assets/practica3.2/image-32.png)

Ahora accedemos al directorio y creamos un nuevo repositorio en Github:
![alt text](./assets/practica3.2/image-33.png)
![alt text](./assets/practica3.2/image-34.png)

Tras esto, seguimos los siguientes comandos:<br>

```
sudo git init
sudo git add .
sudo git commit -m "Subiendo el codigo"
sudo git branch -M main
```

![alt text](./assets/practica3.2/image-35.png)
![alt text](./assets/practica3.2/image-36.png)

Y ahora solo queda referenciar la carpeta al repositorio, para ello usamos los siguientes comandos: <br>

```
sudo git remote add origin https://github.com/arammes003/practica3-2.git
sudo git push -u origin main
```

![alt text](./assets/practica3.2/image-37.png)
![alt text](./assets/practica3.2/image-38.png)

Ahora que ya está enlazado el código a **Github**, entraremos en el sitio web de **Netlify** y desde el dashboard le daremos a importar un proyecto existente de `git`.<br>
![alt text](./assets/practica3.2/image-39.png)

Le indicamos concretamente que sea de **Github**:<br>
![alt text](./assets/practica3.2/image-40.png)

Y nos saltará una ventana pidiendo que autoricemos a **Netlify** a acceder a nuestros repositorios de **Github**:
![alt text](./assets/practica3.2/image-41.png)

Luego le indicamos que no acceda a todos nuestros repositorios, si no sólo al repositorio de la práctica.<br>

![alt text](./assets/practica3.2/image-42.png)

El próximo paso es desplegar la aplicación. <br>
![alt text](./assets/practica3.2/image-43.png)

**IMPORTANTE** Tras el deploy, deberemos cambiar el nombre de la aplicación por nombre-practica3-4.<br>
![alt text](./assets/practica3.2/image-44.png)

- Ahora vamos a comprobar que el nombre se ha cambiado correctamente, para ello dentro de la carpeta `public` encontramos el archivo `robots.txt` cuyo objetivo es indicar a los rastreadores de los buscadores a que URLs del sitio pueden acceder.<br>
  ![alt text](./assets/practica3.2/image-45.png)

- Dentro de la carpeta `public`, utilizaremos un editor de texto para modificar el archivo `robots.txt` y pondremos nuestro nombre y apellido. <br>
  ![alt text](./assets/practica3.2/image-46.png)

- Hacemos un nuevo commit para que se apliquen los cambios de manera automática. <br>
  ![alt text](./assets/practica3.2/image-47.png)
  ![alt text](./assets/practica3.2/image-48.png)

Y lo podremos comprobar en nuestra página de **Netlify** tras realizar el push. <br>
![alt text](./assets/practica3.2/image-49.png)

Y tras ello, también lo comprobamos en el navegador web.
![alt text](./assets/practica3.2/image-50.png)

## 3.- Cuestiones

1. <b>Investiga y explica que es un Dyno en terminología Heroku.</b><br>

   Es una unidad de ejecución ligera que se utiliza para ejecutar aplicaciones en la plataforma.

2. <b>En Heroku no todo es de color de rosa, tiene sus limitaciones y desventajas. Busca, investiga y explica algunas de ellas detalladamente. </b><br>

   Tiene costos elevados: Escalar aplicaciones en Heroku puede volverse caro, especialmente al usar múltiples Dynos o bases de datos grandes​.

   Limitaciones del plan gratuito: Restricciones en horas de uso, suspensión tras inactividad, y bajo rendimiento, lo que lo hace poco ideal para producción.​

   Rendimiento variable: No es óptimo para aplicaciones con alto tráfico o necesidades avanzadas sin costosos upgrades​.

   Falta de soporte avanzado: Configuraciones complejas o tecnologías modernas como Jamstack no están tan bien soportadas como en otras plataformas como AWS o Vercel​.

   Dependencia del ecosistema: Migrar desde Heroku puede ser complicado y costoso​.
