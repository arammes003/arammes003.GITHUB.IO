# Ejercicios Git y Github I

## 1.- Crear repositorio DEAW

1. El primer paso para realizar esta práctica será crear un nuevo repositorio en Github llamado `DEAW`;
   ![alt text](./assets/practica5-1/image.png)
2. Clonamos el repositorio en nuestro sistema local con el enlace que nos genera el repositorio con `git clone https://github.com/TuUsuarioDeGit/DEAW.git`.
   ![alt text](./assets/practica5-1/image-1.png)

## 2.- Crear un README

En este paso lo único que tenemos que hacer es crear un README.md con `sudo nano`.
![alt text](./assets/practica5-1/image-2.png)

## 3.- Commit inicial

Realizamos un commit con el comentario `Comenzamos con los ejercicios de Git` con los siguientes comandos:

```bash
    git add README.md
    git commit -m "Comenzamos con los ejercicios de Git"
```

![alt text](./assets/practica5-1/image-3.png)

## 4.- Push inicial

1. Subimos los cambios al repositorio remoto con el comando `git push -u origin main`.
   ![alt text](./assets/practica5-1/image-4.png)

2. Accedemos a nuestra cuenta de **GitHub** y comprobamos que se han subido los cambios.
   ![alt text](./assets/practica5-1/image-5.png)

## 5.- Ignorar archivos

1. Creamos un archivo local llamado `privado.txt` dentro de nuestro repositorio con `nano privado.txt`.
   ![alt text](./assets/practica5-1/image-6.png)

2. Creamos una carpeta llamada `privada` con `mkdir privada`.
   ![alt text](./assets/practica5-1/image-7.png)
3. Ignoramos la subida del directorio y del fichero creando un fichero `nano .gitignore` dónde pondremos lo siguiente:

```bash
privado.txt
privada
```

![alt text](./assets/practica5-1/image-8.png)

## 6.- Añadir fichero 1.txt

Para añadir un fichero al repositorio local tenemos que hacer lo siguiente:

1. Debemos crear el fichero con `nano 1.txt`.
   ![alt text](./assets/practica5-1/image-9.png)

2. Añadimos el fichero con `git add 1.txt`.
   ![alt text](./assets/practica5-1/image-10.png)

3. Vemos el estado de git con `git status`.
   ![alt text](./assets/practica5-1/image-11.png)

## 7.- Crear el tag v0.1

1. Creamos el tag con `git tag v0.1`.
   ![alt text](./assets/practica5-1/image-12.png)

## 8.- Subir el tag v0.1

1. Creamos un commit con `git commit -m "Texto Descriptivo";
   ![alt text](./assets/practica5-1/image-13.png)

## 9.- Cuenta de GitHub

### 9.1.- Actualizar foto de perfil

Para ello, seguimos los siguientes pasos:

1. Entramos en github.
2. En la parte superior derecha encontramos un logo que es nuestro perfil.
3. Clicamos en tu perfil
4. Pulsamos sobre la imagen que sale y nos sale la opcion de cambiar avatar.
   ![alt text](./assets/practica5-1/image-14.png)

### 9.2.- Activar factor de doble autenticación

1. Accedemos a configuración.
2. Clicamos en contraseña y autenticación y pulsamos el boton de activar.
   ![alt text](./assets/practica5-1/image-15.png)
3. Nos pide nuestra contraseña de Github.
4. Seguimos una serie de pasos para activarlo.
5. Cuando acabemos nos aparecerá esta pantalla.
   ![alt text](./assets/practica5-1/image-17.png)
6. Ya tendríamos activado nuestro doble factor de autenticación.
   ![alt text](./assets/practica5-1/image-18.png)

## 10.- Uso social de GitHub

### 10.1.- Seguir a 2 compañeros de clase

Para ello buscamos el nombre en la lupa.
![alt text](./assets/practica5-1/image-19.png)

Y clicamos en seguir.
![alt text](./assets/practica5-1/image-21.png)
![alt text](./assets/practica5-1/image-22.png)

Desde nuestro perfil podemos ver a quien seguimos.
![alt text](./assets/practica5-1/image-23.png)

### 10.2.- Añadir una estrella a los repositorios DEAW de tus compañeros.

![alt text](./assets/practica5-1/image-24.png)

## 11.- Crear una tabla

Crear una tabla en el fichero `README.md` con la información de algunos de tus compañeros.
![alt text](./assets/practica5-1/image-25.png)

Añadimos el fichero a stash con `git add README.md`
![alt text](./assets/practica5-1/image-27.png)

Creamos un commit con los cambios`git commit -m "Tabla en Git"`.
![alt text](./assets/practica5-1/image-28.png)

Subimos los cambios con `git push -u origin main`.
![alt text](./assets/practica5-1/image-26.png)

## 12.- Colaboradores

Aquí invitamos a un compañero a ser colaborador, para ello:

1. Accedemos al repositorio.
2. Accedemos a la configuración del repositorio.
3. Pulsamos en colabordores.
4. Pulsamos en añadir colabordores.
   ![alt text](./assets/practica5-1/image-29.png)
5. Añadimos el nombre de la persona.
   ![alt text](./assets/practica5-1/image-30.png)
6. Le invitamos.
   ![alt text](./assets/practica5-1/image-31.png)

## 13.- Crear una rama v0.2

![alt text](./assets/practica5-1/image-32.png)

## 14.- Añadir fichero 2.txt

![alt text](./assets/practica5-1/image-33.png)

## 15.- Crear rama remota v0.2

![alt text](./assets/practica5-1/image-34.png)
![alt text](./assets/practica5-1/image-35.png)
![alt text](./assets/practica5-1/image-36.png)

## 16.- Merge directo

![alt text](./assets/practica5-1/image-37.png)

## 17.- Merge con conflicto

Para esto, ambas ramas tendrán que modificar el mismo archivo, para ello, modificaremos el fichero **1.txt**.

1. Desde la rama `main`, pondremos un texto, en mi caso **main**;
   ![alt text](./assets/practica5-1/image-38.png)
2. Hacemos commit:
   ![alt text](./assets/practica5-1/image-39.png)
   ![alt text](./assets/practica5-1/image-40.png)

3. Desde la rama `v0.2`, pondremos **v0.2**;
   ![alt text](./assets/practica5-1/image-41.png)

4. Hacemos un merge desde main:

## 18.- Listado de ramas

## 19.- Arreglar conflicto

## 20.- Borrar rama

## 21.- Listado de cambios
