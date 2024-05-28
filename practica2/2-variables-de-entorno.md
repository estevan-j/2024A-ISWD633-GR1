# Variables de Entorno
### ¿Qué son las variables de entorno
# COMPLETAR

### Para crear un contenedor con variables de entorno

```
docker run -d --name <nombre contenedor> -e <nombre variable1>=<valor1> -e <nombre variable2>=<valor2>
```

### Crear un contenedor a partir de la imagen de nginx:alpine con las siguientes variables de entorno: username y role. Para la variable de entorno rol asignar el valor admin.

# COMPLETAR
```
docker run -d name webN -e username=someone -e role=admin nginx:alpine
```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/89c61f7b-c3ba-468b-871f-48f0785df877)

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR
```docker exec webN env```
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/a7313e53-d97d-4e5c-82fa-2d8fee533004)

### Crear un contenedor con mysql:8 , mapear todos los puertos
# COMPLETAR
````docker run -d --name dbMysql -e MYSQL_ROOT_PASSWORD=a1234 mysql:8  ```

### ¿El contenedor se está ejecutando?
>No, me muestra que debo configurar la siguiente variable de entorno:  >MYSQL_ROOT_PASSWORD

# COMPLETAR
## error solucionado.
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/29dc4675-d94c-4c9f-967d-adbfc108f8f5)
### Identificar el problema
# COMPLETAR
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/fdc9aa47-492d-4889-af98-5d3e0f5fbc88)
### Eliminar el contenedor creado con mysql:8 
# COMPLETAR
![image](https://github.com/estevan-j/2024A-ISWD633-GR1/assets/94009206/78beebbb-dff4-453a-8a52-6a49c6457250)

### Para crear un contenedor con variables de entorno especificadas
- Portabilidad: Las aplicaciones se vuelven más portátiles y pueden ser desplegadas en diferentes entornos (desarrollo, pruebas, producción) simplemente cambiando el archivo de variables de entorno.
- Centralización: Todas las configuraciones importantes se centralizan en un solo lugar, lo que facilita la gestión y auditoría de las configuraciones.
- Consistencia: Asegura que todos los miembros del equipo de desarrollo o los entornos de despliegue utilicen las mismas configuraciones.
- Evitar Exposición en el Código: Mantener variables sensibles como contraseñas, claves API, y tokens fuera del código fuente reduce el riesgo de exposición accidental a través del control de versiones.
- Control de Acceso: Los archivos de variables de entorno pueden ser gestionados con permisos específicos, limitando quién puede ver o modificar la configuración sensible.

Previo a esto es necesario crear el archivo y colocar las variables en un archivo, **.env** se ha convertido en una convención estándar, pero también es posible usar cualquier extensión como **.txt**.
```
docker run -d --name <nombre contenedor> --env-file=<nombreArchivo>.<extensión> <nombre imagen>
```
**Considerar**
Es necesario especificar la ruta absoluta del archivo si este se encuentra en una ubicación diferente a la que estás ejecutando el comando docker run.

### Crear un contenedor con mysql:8 , mapear todos los puertos y configurar las variables de entorno mediante un archivo
# COMPLETAR

# CAPTURA CON LA COMPROBACIÓN DE LA CREACIÓN DE LAS VARIABLES DE ENTORNO DEL CONTENEDOR ANTERIOR 

### ¿Qué bases de datos existen en el contenedor creado?
# COMPLETAR
