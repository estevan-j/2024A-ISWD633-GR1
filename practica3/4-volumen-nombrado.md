## VOLUMEN NOMBRADO
Un volumen nombrado (named volume) es un tipo de volumen gestionado por Docker que se almacena en una ubicación específica del sistema de archivos del host y se identifica mediante un nombre único. Los volúmenes nombrados no requieren que especifiques una ruta del sistema de archivos del host, y en su lugar, Docker se encarga de la gestión y el almacenamiento del volumen.


### Crear volumen
```
docker volume create <nombre volumen>
```

### Crear el volumen nombrado: vol-postgres
# COMPLETAR CON EL COMANDO
```
docker volume create vol-postgres
```
## MOUNTPOINT
Un mountpoint se refiere al lugar en el sistema de archivos donde un dispositivo de almacenamiento se une (o monta) al sistema de archivos. Es el punto donde los archivos y directorios almacenados en ese dispositivo de almacenamiento son accesibles para el sistema operativo y las aplicaciones.

Por ejemplo, en Windows las unidades de almacenamiento (como `C:`, `D:`, etc.) actúan como puntos de montaje principales para discos duros, unidades flash, unidades ópticas y otros dispositivos de almacenamiento.

Cuando creas un volumen nombrado, Docker asigna un punto de montaje específico en el sistema de archivos del host para ese volumen.

### ¿Cuál es el Mountpoint de vol-postgres?
# COMPLETAR CON LA RESPUESTA A LA PREGUNTA
>El Mountpoint de vol-postgres se puede obtener ejecutando:
```
docker volume inspect vol-postgres
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/8f627790-c0be-43af-9c72-76ccb04ad2df)

### Estructura del Punto de Montaje:
- /var/lib/docker/volumes/: Es la ubicación base donde Docker almacena todos los volúmenes en el sistema de archivos del host.
- nombreVolumen/: Es el nombre del volumen nombrado que has creado. Docker crea un directorio con este nombre dentro de /var/lib/docker/volumes/ para almacenar los datos del volumen.
- _data: Es el subdirectorio dentro de vol-postgres/ donde se almacenan los datos reales del volumen. El nombre _data es una convención utilizada por Docker para indicar el directorio donde se encuentran los datos del volumen.

### ¿Cómo acceder a ese Mountpoint?
En el contexto de WSL (Windows Subsystem for Linux), wsl$ se refiere al nombre de un recurso compartido de red especial que representa la raíz del sistema de archivos de Windows desde WSL. Cuando accedes a \\wsl$ desde el Explorador de archivos de Windows, puedes ver y acceder a los archivos del sistema de archivos de la distribución de Linux en WSL.
\\wsl.localhost\docker-desktop-data\data\docker\volumes

### Crear un contenedor vinculado a un volumen nombrado
```
docker run -d --name <nombre contenedor> -v <nombre volumen>:<ruta contenedor> <nombre imagen>
```

### Crear la red net-drupal de tipo bridge
# COMPLETAR CON EL COMANDO
```
docker network create --drive bridge net-drupal
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/9e17ffd3-9f90-47b5-8ce1-9e2ede1388d5)

### Crear un servidor postgres vinculado a la red net-drupal, completar la ruta del contenedor
docker run -d --name server-postgres -e POSTGRES_DB=db_drupal -e POSTGRES_PASSWORD=12345 -e POSTGRES_USER=user_drupal -v vol-postgres:<ruta contenedor> --network net-drupal postgres
_No es necesario exponer el puerto, debido a que nos vamos a conectar desde la misma red de docker_

```
docker run -d --name server-postgres -e POSTGRES_DB=db_drupal -e POSTGRES_PASSWORD=a1234 -e POSTGRES_USER=user_drupal -v vol-postgres:/var/lib/postgresql/data --network net-drupal postgres
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/4409c32f-071f-4efa-90ed-6703034e01ba)

### Crear un cliente postgres vinculado a la red drupal a partir de la imagen dpage/pgadmin4, completar el correo
docker run -d --name client-postgres --publish published=9500,target=80 -e PGADMIN_DEFAULT_PASSWORD=54321 -e PGADMIN_DEFAULT_EMAIL=<correo> --network net-drupal dpage/pgadmin4
```
docker run -d --name client-postgres -p 9500:80 -e PGADMIN_DEFAULT_PASSWORD=12345 -e PGADMIN_DEFAULT_EMAIL=correo@example.com --network net-drupal dpage/pgadmin4
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/6c437586-743f-4503-874f-bb72c80573d3)

### Usar el cliente postgres para conectarse al servidor postgres, para la conexión usar el nombre del servidor en lugar de la dirección IP.
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/77788fdf-f511-4811-97e7-5a89887c8235)

### Crear los volúmenes necesarios para drupal, esto se puede encontrar en la documentación
### COMPLETAR CON LOS COMANDOS
```
docker volume create vol-drupal-web
docker volume create vol-drupal-modules
docker volume create vol-drupal-profiles
docker volume create vol-drupal-sites
```
### Crear el contenedor server-drupal vinculado a la red, usar la imagen drupal, y vincularlo a los volúmenes nombrados
docker run -d --name server-drupal --publish published=9700,target=80 -v <nombre volumen>:<ruta contenedor> -v <nombre volumen>:<ruta contenedor> -v <nombre volumen>:<ruta contenedor> -v <nombre volumen>:<ruta contenedor> --network net-drupal drupal
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/40b1a270-5d96-441a-82dd-3c8bb5c6f0bb)

### Ingrese al server-drupal y siga el paso a paso para la instalación.
# COMPLETAR CON UNA CAPTURA DE PANTALLA DEL PASO 4
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/5c9ac7e4-692e-4e1e-805f-7d5f93cb3719)

_La instalación puede tomar varios minutos, mientras espera realice un diagrama de los contenedores que ha creado en este apartado._

# COMPLETAR CON EL DIAGRAMA SOLICITADO
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/6b1bb8ac-fbe9-4273-b57a-ae4e243511a4)

### Eliminar un volumen específico
```
docker volume rm <nombre volumen>
```
```
docker volume rm vol-postgres
```
**Considerar**
Datos Persistentes: Asegúrate de que el volumen no contiene datos críticos antes de eliminarlo, ya que esta operación no se puede deshacer.
Contenedores Activos: No puedes eliminar un volumen que está actualmente en uso por un contenedor activo. Debes detener y/o eliminar el contenedor primero.
