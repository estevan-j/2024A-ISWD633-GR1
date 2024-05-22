<# Contenedores

### Crear un contenedor
Para crear un nuevo contenedor Docker a partir de una imagen específica, pero sin iniciarlo automáticamente. 

```
docker create --name <nombre contenedor> <nombre imagen>:<tag>
```
Crear el contenedor  **srv-web** usando la imagen nginx version alpine
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/6273c569-9f96-4fa4-a597-f15d9a1873a7)

# COMPLETAR

Si creas un contenedor en Docker sin asignarle un nombre específico utilizando la opción --name, Docker asignará automáticamente un nombre aleatorio al contenedor. Este nombre suele consistir en una combinación de palabras y números.  

Crear el contenedor usando la imagen hello-world
# COMPLETAR

### Listar los contenedores ejecutándose o no

```
docker ps -a
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/b0efd425-147f-4e84-8dc1-7fa6f9d9afc7)

### Para iniciar un contenedor

```
docker start <nombre contenedor o identificador>
```
Iniciar el contenedor srv-web 
# COMPLETAR

### Listar los contenedores ejecutándose
```
docker ps 
docker ps | grep <nombre contenedor>
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/11a239a2-3e16-42e9-a01a-c2484e0f3985)

### Para detener un contenedor

```
docker stop <nombre contenedor>
```

### Para crear un contenedor y ejecutarlo inmediatamente

```
docker run --name <nombre contenedor> <nombre imagen>:<tag>
```
![Ecosistema de Docker](imagenes/dockerRun.PNG)

Crear y ejecutar inmediatamente el contenedor **srv-web2** usando la imagen nginx:alpine
# COMPLETAR

**¿Qué sucede luego de la ejecución del comando?**
__
Primeramente el comando en enviado por el docker CLI, al Docker Server que ejecuta la instrucción recibida.
Si es un comando de ejecución el docker server busca la imagen localmente, y sino la encuentra la descarga de docker Hub.  Creando y ejecutando una instancia de la imagen descargada, el cli muestra al contenedor corriendo, hasta salir.

# COMPLETAR  

Cuando ejecutas un contenedor en primer plano sin la opción -d (modo detach), el contenedor captura la entrada estándar (stdin) del terminal, lo que significa que el terminal queda "atrapado" y no puedes introducir más comandos hasta que detengas el contenedor.

### Para crear un contenedor y ejecutarlo inmediatamente sin estar vinculados al mismo
-d: Es la opción que indica a Docker que ejecute el contenedor en segundo plano (en modo "detach").
Cuando un contenedor se ejecuta en segundo plano, Docker devuelve el control al terminal inmediatamente después de iniciar el contenedor, lo que permite al usuario seguir ejecutando otros comandos en el mismo terminal sin que el contenedor detenga la interacción.

```
docker run -d --name <nombre contenedor> <nombre imagen>:tag
```
Crear y ejecutar inmediatamente el contenedor **srv-web3** en modo detach usando la imagen nginx:alpine
# COMPLETAR

### Para eliminar un contenedor

```
docker rm <nombre contenedor>
```
Eliminar el contenedor que se creó a partir de la imagen hello-world 
# COMPLETAR

Verificar que el contenedor que se eliminó
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/38727dbf-ebb6-44f6-b265-d54f7fe97cfd)

# COMPLETAR

### Para eliminar un contenedor que esté ejecutándose

```
docker rm -f <nombre contenedor>
```
Eliminar el contenedor **srv-web3** 
# COMPLETAR
Verificar que el contenedor que se eliminó
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/3b0f40bd-3135-426e-845d-4b01f2743ca9)

# COMPLETAR

### Para inspecionar un contenedor 

Inspeccionar el contenedor **srv-web** 
# COMPLETAR
