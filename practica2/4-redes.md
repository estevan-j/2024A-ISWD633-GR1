# Redes
Las redes son un componente fundamental que permite la comunicación entre contenedores, así como la comunicación de los contenedores con el mundo exterior. 
![Imagen](imagenes/redes.PNG)
- Bridge: Esta es la red por defecto en Docker. Permite la comunicación entre contenedores en el mismo host. Cada contenedor conectado a la red bridge tiene una IP propia en la subred de la red bridge.
    -  Brige por default: Cuando se ejecuta un contenedor, Docker crea automáticamente una red de tipo bridge por default. Esta red se utiliza para permitir la comunicación entre contenedores en el mismo host. Cada contenedor conectado a esta red obtiene su propia dirección IP en la subred de la red bridge.
    - Bridge creada por nosotros: Un usuario también puede crear sus propias redes de tipo bridge en Docker. Esto puede ser útil para organizar y segmentar los contenedores de una aplicación de manera más controlada. Al crear una red bridge personalizada, se puede especificar un rango de direcciones IP y otras configuraciones de red específicas. Los contenedores conectados a esta red utilizarán las direcciones IP de la subred definida por el usuario.
- Host: Con esta red, los contenedores comparten la red del host en lugar de tener su propia interfaz de red. Esto puede mejorar el rendimiento de red, pero los contenedores pueden entrar en conflicto con los puertos del host si intentan utilizar los mismos puertos.
- None: Con esta red, se deshabilita la configuración de red. Los contenedores que usan esta red tienen su propia red de bucle invertido y no pueden comunicarse con otros contenedores a menos que se conecten explícitamente a una red.

### Crear una red de tipo bridge

```
docker network create <nombre red> -d bridge
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/bf3561c0-2801-4d92-ab17-8a1eb4600453)

### Crear un contenedor vinculado a una red

```
docker run -d --name <nombre contenedor> --network <nombre red> <nombre imagen>
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/4107f321-e834-4738-8189-7689461419f6)

### Para saber a qué red está conectado un contenedor

```
docker inspect <nombre contenedor>
```
ó
```
docker network inspect <nombre red> 
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/eaf753e0-2bae-44a2-a75d-72b079177519)

### Vincular contenedor a una red
```
docker network connect <nombre red> <nombre contenedor>
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/42a67c43-3a60-4ead-a9cd-8aa119c0e87a)

### Para desvincular un contenedor de una red
```
docker network disconnect <nombre red> <nombre contenedor>
```

### Para listar las redes existentes
```
docker network ls
```

### Crear los contenedores y las redes que se presentan en el esquema. Usar para todos los contenedores la imagen de nginx:alpine

![Imagen](imagenes/esquema-ejercicio-redes.PNG)

# COLOCAR UNA CAPTURA DE LAS REDES EXISTENTES CREADAS
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/d44883c0-1923-491b-be44-65e4e8086d72)

# COLOCAR UNA(S) CAPTURAS(S) DE LOS CONTENEDORES CREADOS EN DONDE SE EVIDENCIE A QUÉ RED ESTÁN VINCULADOS
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/f78133e8-f52c-4008-9008-b501aff27089)
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/eb1afa45-9184-43a0-8d74-dbc067a4f697)

### Para eliminar las redes creadas
```
docker network rm <nombre de la red>
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/d12d2358-8bfa-40bf-bed8-61a8584a7027)

