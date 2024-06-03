### Crear contenedor de Postgres sin que exponga los puertos. Usar la imagen: postgres:11.21-alpine3.17
# COMPLETAR
```
docker run -d --name postgresCont postgres:11.21-alpine3.17
```
### Crear un cliente de postgres. Usar la imagen: dpage/pgadmin4
#### Creación de la red
```
docker network create pg-net
```
#### Creación del contenedor
```
docker run -d --name postgresCount --network pg-net -e POSTGRES_PASSWORD=admin22 postgres:11.21-alpine3.17
```
#### Levantar contenedor pgAdmin
```
docker run -d --name my_pgadmin --network pg-net -p 80:80 -e PGADMIN_DEFAULT_EMAIL=some@gmail.com -e PGADMIN_DEFAULT_PASSWORD=admin22 dpage/pgadmin4
```
# COMPLETAR

La figura presenta el esquema creado en donde los puertos son:
- a: 80
- b: 80
- c: 5432

![Imagen](imagenes/esquema-ejercicio3.PNG)

## Desde el cliente
### Acceder desde el cliente al servidor postgres creado.
# COMPLETAR CON UNA CAPTURA DEL LOGIN
### Crear la base de datos info, y dentro de esa base la tabla personas, con id (serial) y nombre (varchar), agregar un par de registros en la tabla, obligatorio incluir su nombre.

## Desde el servidor postgresl
### Acceder al servidor
### Conectarse a la base de datos info
# COMPLETAR
### Realizar un select *from personas
# AGREGAR UNA CAPTURA DE PANTALLA DEL RESULTADO
