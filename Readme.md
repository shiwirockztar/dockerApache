docker run -dit --name myapachito -p 8080:80 httpd ==> ejecutar un contenedor
docker ps ==> ver contenedores creados

### modo terminal de linux (bash)

docker exec -it myapachito bash ==>ejecutar en modo bash
pwd ==> ver directorio ruta
ls ==> mostrar archivos

### dentro de la carpeta htdocs

cat index.html ==> vemos el contenido del index
touch about.html ==> creamos pagina

#http://localhost:8080/about.html
echo '<html><body><h1>About!</h1></body></html>' > about.html ==> editamos la pagina

Ctrl+D para salir del modo bash

### enviar contenido en un contenedor

docker run --name mywebApache -dit -p 3000:80 -v ${PWD}:/usr/local/apache2/htdocs/ httpd

### Inicio del dockerfile

docker stop $(docker ps -aq) ==> parar contenedores activos, obtener todos los ids $(docker ps -aq)
docker ps -a ==> ver contenedores existentes
docker rm $(docker ps -aq) ==> eliminar contenedores

### crear imagen

docker build -t template-fotograpghy-apache . ==> construir imagen dentro de la carpeta destino

### correr imagen como contenedor

docker run -p 5000:80 --name photoContainer -d template-fotograpghy-apache
docker run -dit --name photoContainer -p 9000:80 template-fotograpghy-apache
