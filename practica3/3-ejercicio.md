## Esquema para el ejercicio
![Imagen](imagenes/esquema-ejercicio3.PNG)

### Crear red net-wp
# COMPLETAR CON EL COMANDO COMANDO
```
docker network create net-wp
```
### Para que persista la información es necesario conocer en dónde mysql almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (a) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/db

### ¿Qué contiene la carpeta db del host?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
> Inicialmente, la carpeta db del host está vacía. Después de iniciar el contenedor MySQL, contendrá los archivos de la base de datos.
### Crear un contenedor con la imagen mysql:8  en la red net-wp, configurar las variables de entorno: MYSQL_ROOT_PASSWORD, MYSQL_DATABASE, MYSQL_USER y MYSQL_PASSWORD
# COMPLETAR CON EL COMANDO
```
docker run --name contMysq --env-file=./mysq.env -v /c/Users/Usuario/Documents//git\ hub\ uni/2024A-ISWD633-GR1/practica3/db:/var/lib/mysql --network net-wp -d mysql:8
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/2ae53123-408c-4c56-9979-f6348606d15d)

### ¿Qué observa en la carpeta db que se encontraba inicialmente vacía?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
>Después de iniciar el contenedor MySQL, la carpeta db en el host contendrá archivos y directorios correspondientes a las bases de datos >MySQL, como ibdata1, ib_logfile0, y directorios de bases de datos.
### Para que persista la información es necesario conocer en dónde wordpress almacena la información.
# COMPLETAR LA SIGUIENTE ORACIÓN. REVISAR LA DOCUMENTACIÓN DE LA IMAGEN EN https://hub.docker.com/)
En el esquema del ejercicio la carpeta contenedor (b) es (COMPLETAR CON LA RUTA)
Ruta carpeta host: .../ejercicio3/www

### Crear un contenedor con la imagen wordpress en la red net-wp, configurar las variables de entorno WORDPRESS_DB_HOST, WORDPRESS_DB_USER, WORDPRESS_DB_PASSWORD y WORDPRESS_DB_NAME (los valores de estas variables corresponden a los del contenedor creado previamente)
# COMPLETAR CON EL COMANDO
```
docker run -d --name contWork --network net-wp -p:9500:80 -v /c/Users/Usuario/Documents/git\ hub\ uni/2024A-ISWD633-GR1/practica3/www/:/var/www/html --env-file ./wordpress.env wordpress
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/2b39f0bc-af05-47af-92ce-6713dbe4df82)

### Personalizar la apariencia de wordpress y agregar una entrada

### Eliminar el contenedor y crearlo nuevamente, ¿qué ha sucedido?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
```
docker run -d --name contWork --network net-wp -p:9500:80 -v /c/Users/Usuario/Documents/git\ hub\ uni/2024A-ISWD633-GR1/practica3/www/:/var/www/html --env-file ./wordpress.env wordpress
```
Al eliminar el contenedor y crearlo nuevamente, las personalizaciones y las entradas agregadas anteriormente deberían persistir porque los datos están almacenados en el volumen montado desde el host. Esto asegura que cualquier cambio realizado en WordPress se mantenga, incluso si el contenedor es eliminado y recreado.

