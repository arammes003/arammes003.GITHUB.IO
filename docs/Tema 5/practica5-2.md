# # Ejercicios Git y Github II

## Ejercicios de creación y actualización de repositorios

### Ejercicio 1

Configurar Git definiendo el nombre del usuario, el correo electrónico y activar el coloreado de la salida.
![alt text](./assets/practica5-2/image.png)

Mostrar la configuración final.
![alt text](./assets/practica5-2/image-1.png)

### Ejercicio 2

Crear un repositorio nuevo con el nombre libro y mostrar su contenido.
![alt text](./assets/practica5-2/image-2.png)

### Ejercicio 3

Comprobar el estado del repositorio.
![alt text](./assets/practica5-2/image-3.png)

Crear un fichero indice.txt con el siguiente contenido:

```Capítulo 1: Introducción a Git
Capítulo 2: Flujo de trabajo básico
Capítulo 3: Repositorios remotos
```

![alt text](./assets/practica5-2/image-4.png)

Comprobar de nuevo el estado del repositorio.
![alt text](./assets/practica5-2/image-5.png)

Añadir el fichero a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-6.png)

Volver a comprobar una vez más el estado del repositorio.
![alt text](./assets/practica5-2/image-7.png)

### Ejercicio 4

Realizar un commit de los últimos cambios con el mensaje “Añadido índice del libro.” y ver el estado del repositorio.
![alt text](./assets/practica5-2/image-8.png)

### Ejercicio 5

Cambiar el fichero indice.txt para que contenga lo siguiente:

```
Capítulo 1: Introducción a Git
Capítulo 2: Flujo de trabajo básico
Capítulo 3: Gestión de ramas
Capítulo 4: Repositorios remotos
```

![alt text](./assets/practica5-2/image-9.png)

Mostrar los cambios con respecto a la última versión guardada en el repositorio.
![alt text](./assets/practica5-2/image-10.png)

Hacer un commit de los cambios con el mensaje “Añadido capítulo 3 sobre gestión de ramas”.
![alt text](./assets/practica5-2/image-11.png)

### Ejercicio 6

Mostrar los cambios de la última versión del repositorio con respecto a la anterior.
![alt text](./assets/practica5-2/image-12.png)

Cambiar el mensaje del último commit por “Añadido capítulo 3 sobre gestión de ramas al índice.”
![alt text](./assets/practica5-2/image-13.png)

Volver a mostrar los últimos cambios del repositorio.
![alt text](./assets/practica5-2/image-14.png)

## Ejercicios de manejo del historial de cambios

### Ejercicio 1

Mostrar el historial de cambios del repositorio.
![alt text](./assets/practica5-2/image-15.png)

Crear la carpeta capitulos y crear dentro de ella el fichero capitulo1.txt con el siguiente texto.

`Git es un sistema de control de versiones ideado por Linus Torvalds.`
![alt text](./assets/practica5-2/image-16.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-17.png)

Hacer un commit de los cambios con el mensaje “Añadido capítulo 1.” Volver a mostrar el historial de cambios del repositorio.
![alt text](./assets/practica5-2/image-18.png)

## Ejercicio 2

Crear el fichero capitulo2.txt en la carpeta capitulos con el siguiente texto.

```bash
El flujo de trabajo básico con Git consiste en:
1- Hacer cambios en el repositorio.
2- Añadir los cambios a la zona de intercambio temporal.
3- Hacer un commit de los cambios.
```

![alt text](./assets/practica5-2/image-19.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-20.png)

Hacer un commit de los cambios con el mensaje “Añadido capítulo 2.”
![alt text](./assets/practica5-2/image-21.png)

Mostrar las diferencias entre la última versión y dos versiones anteriores.
![alt text](./assets/practica5-2/image-22.png)

### Ejercicio 3

Crear el fichero capitulo3.txt en la carpeta capitulos con el siguiente texto.

`Git permite la creación de ramas lo que permite tener distintas versiones del mismo proyecto y trabajar de manera simultanea en ellas.`
![alt text](./assets/practica5-2/image-23.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-24.png)

Hacer un commit de los cambios con el mensaje “Añadido capítulo 3.”
![alt text](./assets/practica5-2/image-25.png)

Mostrar las diferencias entre la primera y la última versión del repositorio.
![alt text](./assets/practica5-2/image-26.png)

### Ejercicio 4

Añadir al final del fichero indice.txt la siguiente línea:
`Capítulo 5: Conceptos avanzados`
![alt text](./assets/practica5-2/image-27.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-28.png)

Hacer un commit de los cambios con el mensaje “Añadido capítulo 5 al índice.”.
![alt text](./assets/practica5-2/image-29.png)

Mostrar quién ha hecho cambios sobre el fichero indice.txt.
![alt text](./assets/practica5-2/image-30.png)

## Ejercicios de deshacer cambios

### Ejercicio 1

Eliminar la última línea del fichero indice.txt y guardarlo.
![alt text](./assets/practica5-2/image-31.png)

Comprobar el estado del repositorio.
![alt text](./assets/practica5-2/image-32.png)

Deshacer los cambios realizados en el fichero indice.txt para volver a la versión anterior del fichero.
![alt text](./assets/practica5-2/image-33.png)

Volver a comprobar el estado del repositorio.
![alt text](./assets/practica5-2/image-34.png)

### Ejercicio 2

Eliminar la última línea del fichero indice.txt y guardarlo.
![alt text](./assets/practica5-2/image-35.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-36.png)

Comprobar de nuevo el estado del repositorio.
![alt text](./assets/practica5-2/image-37.png)

Quitar los cambios de la zona de intercambio temporal, pero mantenerlos en el directorio de trabajo.
![alt text](./assets/practica5-2/image-38.png)

Comprobar de nuevo el estado del repositorio.
![alt text](./assets/practica5-2/image-39.png)

Deshacer los cambios realizados en el fichero indice.txt para volver a la versión anterior del fichero.
![alt text](./assets/practica5-2/image-40.png)

Volver a comprobar el estado del repositorio.
![alt text](./assets/practica5-2/image-41.png)

### Ejercicio 3

Eliminar la última línea del fichero indice.txt y guardarlo.
![alt text](./assets/practica5-2/image-42.png)

Eliminar el fichero capitulos/capitulo3.txt.
![alt text](./assets/practica5-2/image-43.png)

Añadir un fichero nuevo capitulos/capitulo4.txt vacío.
![alt text](./assets/practica5-2/image-44.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-45.png)

Comprobar de nuevo el estado del repositorio.
![alt text](./assets/practica5-2/image-46.png)

Quitar los cambios de la zona de intercambio temporal, pero mantenerlos en el directorio de trabajo.
![alt text](./assets/practica5-2/image-47.png)

Comprobar de nuevo el estado del repositorio.
![alt text](./assets/practica5-2/image-48.png)

Deshacer los cambios realizados para volver a la versión del repositorio.
![alt text](./assets/practica5-2/image-49.png)

Volver a comprobar el estado del repositorio.
![alt text](./assets/practica5-2/image-50.png)

### Ejercicio 4

Eliminar la última línea del fichero indice.txt y guardarlo.
![alt text](./assets/practica5-2/image-51.png)

Eliminar el fichero capitulos/capitulo3.txt.
![alt text](./assets/practica5-2/image-52.png)

Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Borrado accidental.”
![alt text](./assets/practica5-2/image-53.png)

Comprobar el historial del repositorio.
![alt text](./assets/practica5-2/image-54.png)

Deshacer el último commit pero mantener los cambios anteriores en el directorio de trabajo y la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-55.png)

Comprobar el historial y el estado del repositorio.
![alt text](./assets/practica5-2/image-56.png)

Volver a hacer el commit con el mismo mensaje de antes.
![alt text](./assets/practica5-2/image-57.png)

Deshacer el último commit y los cambios anteriores del directorio de trabajo volviendo a la versión anterior del repositorio.
![alt text](./assets/practica5-2/image-58.png)

Comprobar de nuevo el historial y el estado del repositorio.
![alt text](./assets/practica5-2/image-59.png)

## Ejercicios de gestión de ramas

### Ejercicio 1

Crear una nueva rama bibliografia y mostrar las ramas del repositorio.
![alt text](./assets/practica5-2/image-60.png)

### Ejercicio 2

Crear el fichero capitulos/capitulo4.txt y añadir el texto siguiente

`En este capítulo veremos cómo usar GitHub para alojar repositorios en remoto.`
![alt text](./assets/practica5-2/image-61.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-62.png)

Hacer un commit con el mensaje “Añadido capítulo 4.”
![alt text](./assets/practica5-2/image-63.png)

Mostrar la historia del repositorio incluyendo todas las ramas.
![alt text](./assets/practica5-2/image-64.png)

### Ejercicio 3

Cambiar a la rama bibliografia.
![alt text](./assets/practica5-2/image-65.png)

Crear el fichero bibliografia.txt y añadir la siguiente referencia

`Chacon, S. and Straub, B. Pro Git. Apress.`
![alt text](./assets/practica5-2/image-66.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-67.png)

Hacer un commit con el mensaje “Añadida primera referencia bibliográfica.”
![alt text](./assets/practica5-2/image-68.png)

Mostrar la historia del repositorio incluyendo todas las ramas.
![alt text](./assets/practica5-2/image-70.png)

### Ejercicio 4

Fusionar la rama bibliografia con la rama master.
![alt text](./assets/practica5-2/image-71.png)

Mostrar la historia del repositorio incluyendo todas las ramas.
![alt text](./assets/practica5-2/image-72.png)

Eliminar la rama bibliografia.
![alt text](./assets/practica5-2/image-73.png)

Mostrar de nuevo la historia del repositorio incluyendo todas las ramas.
![alt text](./assets/practica5-2/image-74.png)

### Ejercicio 5

Crear la rama bibliografia.
![alt text](./assets/practica5-2/image-75.png)

Cambiar a la rama bibliografia.
![alt text](./assets/practica5-2/image-76.png)

Cambiar el fichero bibliografia.txt para que contenga las siguientes referencias:

```
Scott Chacon and Ben Straub. Pro Git. Apress.
Ryan Hodson. Ry’s Git Tutorial. Smashwords (2014)
```

![alt text](./assets/practica5-2/image-77.png)

Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Añadida nueva referencia bibliográfica.”
![alt text](./assets/practica5-2/image-78.png)

Cambiar a la rama master.
![alt text](./assets/practica5-2/image-79.png)

Cambiar el fichero bibliografia.txt para que contenga las siguientes referencias:

```Chacon, S. and Straub, B. Pro Git. Apress.
Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.
```

![alt text](./assets/practica5-2/image-80.png)

Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Añadida nueva referencia bibliográfica.”
![alt text](./assets/practica5-2/image-81.png)

Fusionar la rama bibliografia con la rama master.
![alt text](./assets/practica5-2/image-82.png)

Resolver el conflicto dejando el fichero bibliografia.txt con las referencias:

```Chacon, S. and Straub, B. Pro Git. Apress.
Loeliger, J. and McCullough, M. Version control with Git. O’Reilly.
Hodson, R. Ry’s Git Tutorial. Smashwords (2014)
```

![alt text](./assets/practica5-2/image-83.png)

Añadir los cambios a la zona de intercambio temporal y hacer un commit con el mensaje “Resuelto conflicto de bibliografía.”
![alt text](./assets/practica5-2/image-84.png)

Mostrar la historia del repositorio incluyendo todas las ramas.
![alt text](./assets/practica5-2/image-85.png)

## Ejercicios de repositorios remotos

### Ejercicio 1

Crear un nuevo repositorio público en GitHub con el nombre libro-git.
Añadirlo al repositorio local del libro.
Mostrar todos los repositorios remotos configurados.
![alt text](./assets/practica5-2/image-86.png)

### Ejercicio 2

Añadir los cambios del repositorio local al repositorio remoto de GitHub.
![alt text](./assets/practica5-2/image-87.png)

Acceder a GitHub y comprobar que se han subido los cambios mostrando el historial de versiones.
![alt text](./assets/practica5-2/image-88.png)

### Ejercicio 3

Colaborar en el repositorio remoto libro-git de otro usuario.
![alt text](./assets/practica5-2/image-89.png)

Clonar su repositorio libro-git.
![alt text](./assets/practica5-2/image-90.png)

Añadir el fichero autores.txt que contenga el nombre del usuario y su correo electrónico.
![alt text](./assets/practica5-2/image-95.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-91.png)

Hacer un commit con el mensaje “Añadido autor.”
![alt text](./assets/practica5-2/image-96.png)

Subir los cambios al repositorio remoto.
![alt text](./assets/practica5-2/image-93.png)

### Ejercicio 4

Hacer una bifurcación del repositorio remoto asalber/libro-git en GitHub.
![alt text](./assets/practica5-2/image-94.png)

Clonar el repositorio creado en la cuenta de GitHub del usuario.
![alt text](./assets/practica5-2/image-97.png)

Crear una nueva rama autoria y activarla.
![alt text](./assets/practica5-2/image-98.png)

Añadir el nombre del usuario y su correo al fichero autores.txt.
![alt text](./assets/practica5-2/image-99.png)

Añadir los cambios a la zona de intercambio temporal.
![alt text](./assets/practica5-2/image-100.png)

Hacer un commit con el mensaje “Añadido nuevo autor.”
![alt text](./assets/practica5-2/image-101.png)

Subir los cambios de la rama autoria al repositorio remoto en GitHub.
![alt text](./assets/practica5-2/./assets/practica5-2/image-102.png)

Hacer un Pull Request de los cambios en la rama autoria.
![alt text](./assets/practica5-2/image-103.png)
![alt text](./assets/practica5-2/image-104.png)
![alt text](./assets/practica5-2/image-105.png)
![alt text](./assets/practica5-2/image-106.png)
