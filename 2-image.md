# Imagen
Es un archivo único que contiene todos los programas, librerías, dependencias y configuraciones necesarias para instalar y/o ejecutar una aplicación o un conjunto de aplicaciones.
![Imagen](img/imagen.PNG)


## ¿Cuál es la relación entre una imagen y un contenedor?  

La relación radica en que una imagen es una plantilla de solo lectura con todo lo necesario para ejecutar una aplicación. Un contenedor es una instancia de esa imagen en ejecución, con su propio entorno y la capacidad de realizar cambios. Por lo qué, **la imagen es la plantilla que define lo que el contenedor va a ejecutar**


![Imagen y contenedores](img/imagenContenedores.JPG)
## Comandos para imágenes

### Descargar imagen
Descarga la última versión de la imagen disponible en el registro de Docker.

```
docker pull <nombre imagen> 
```

Descarga una versión específica de la imagen, cada imagen tiene etiquetas (tags) para diferentes versiones.
Una imagen puede tener la etiqueta latest para representar la última versión, si no se especifica una etiqueta se hará referencia a la versión latest.

```
docker pull <nombre imagen>:<tag>
```

Descargar la imagen **hello-world**  
```docker pull hello-world```  

**¿Qué es nginx**  

NGINX es un servidor web que también actúa como proxy de correo electróncio, proxy inverso y balanceador de carga.

Descargar la imagen  **nginx** en la versión **alpine**  
```docker pull nginx:alpine```  

### Listar imágenes

```
docker images
```  

![Imagen y contenedores](img/docker_images.png)  

**Identificadores**

En Docker, se utilizan varios identificadores para diferenciar de manera única los elementos del sistema, como imágenes, contenedores, volúmenes y redes. Estos identificadores son generados automáticamente por Docker y son únicos dentro del contexto del sistema Docker en el que se encuentran. 

### Inspeccionar una imagen
El comando docker inspect se utiliza para obtener información detallada sobre un objeto de Docker específico, como un contenedor, una imagen, un volumen o una red.  Proporciona información en formato JSON sobre el objeto especificado.

```
docker inspect <nombre imagen>
docker inspect <nombre imagen>:<tag>
```

Inspeccionar la imagen hello-world 
```
docker inspect hello-world
```

**¿Con qué algoritmo se está generando el ID de la imagen**
```` "Id": "sha256:d211f485f2dd1dee407a80973c8f129f00d54604d2c90732e8e320e5038a0348" ````
La salida muestra que el algoritmo con el que se genera el ID de la imagen es **SHA-256**, que toma como entrada los metadatos de la imagen, configuración y el contenido de las capas, y genera una cadena única de 64 caracteres que representa la imagen en su totalidad.

### Filtrar imágenes

```
docker images | grep <termino a buscar>

```

### Para eliminar una imagen
Eliminar permanentemente la imagen de tu sistema Docker.

```
docker rmi <nombre imagen>:<tag>
```

Eliminar la imagen hello-world 
````
docker rmi hello-world
````

-f: Es la opción para forzar la eliminación de la imagen incluso si hay contenedores en ejecución que utilizan esa imagen.
Cuando eliminas una imagen Docker, Docker no elimina automáticamente los contenedores que se han creado a partir de esa imagen. Esto significa que, aunque hayas eliminado la imagen, el contenedor seguirá ejecutándose normalmente.  
**Considerar**
Eliminar una imagen no afecta a los contenedores que se han creado a partir de esa imagen, a menos que esos contenedores dependan de archivos o configuraciones específicas de la imagen eliminada. En ese caso, es posible que los contenedores se comporten de manera inesperada después de eliminar la imagen.
Es una buena práctica detener y eliminar todos los contenedores que dependan de una imagen antes de eliminar la imagen en sí.

```
docker rmi -f <nombre imagen>:<tag>
```

