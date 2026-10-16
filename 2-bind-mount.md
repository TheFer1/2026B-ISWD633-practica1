# BIND MOUNT
En un bind mount mapeamos (montar) un directorio o archivo específico del sistema de archivos del host con una parte del sistema de ficheros del contenedor.

```
docker run -d --name <nombre contenedor> -v <ruta carpeta host>:<ruta carpeta contenedor> <imagen> 
```
ó
```
docker run -d --name <nombre contenedor> --mount type=bind,source=<ruta carpeta host>,target=<ruta carpeta contenedor> <imagen>
```
- destination, dst, target: La ruta donde se monta el archivo o directorio en el contenedor.
- source, src: El origen del montaje.
  
### En tu computador crear una carpeta llamada nginx y dentro de esta carpeta crea otra llamada html. Como se aprecia en la figura.
![Volúmenes](directorio.PNG)

### Crear un contenedor con la imagen nginx:alpine, mapear todos por puertos, para la ruta carpeta host colocar el directorio en donde se encuentra la carpeta html en tu computador y para la ruta carpeta contenedor: /usr/share/nginx/html (esta ruta se obtiene al revisar la documentación de la imagen)
![Volúmenes](volumen-host.PNG)
# COMPLETAR CON EL COMANDO
docker run -d --name srvngix -v C:\Users\P3E010-D\Downloads\dockerf\nginx\html:/usr/share/nginx/html  -p 8080:80 nginx:alpine
### ¿Qué sucede al ingresar al servidor de nginx?
Al ingresar en el localhost80 me dirige a un apartado web pero que me da un error 403 
### ¿Qué pasa con el archivo index.html del contenedor?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
la opción -v para montar una carpeta local vacía sobre esa ruta, el contenido original queda oculto mientras el montaje está activo. Por esta razón, Nginx no encuentra un archivo index.html que mostrar y devuelve el error 403 Forbidden. 
### Ir a https://html5up.net/ y descargar un template gratuito, descomprirlo dentro de tu computador en la carpeta html
### ¿Qué sucede al ingresar al servidor de nginx?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
Como ya existe un recurso .html dentro de la carpeta ya no me sale el error 403 y ya me muestra la plantilla que se descargo.
### Eliminar el contenedor
docker rm -f srvngix
### ¿Qué sucede al crear nuevamente un contenedor montado al directorio definidos anteriormente?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
al eliminar el contenedor pero como ya existe información en el directorio ya definido anteriormente se muestra la plantilla que existe en ese directorio sin dar ningun error 
