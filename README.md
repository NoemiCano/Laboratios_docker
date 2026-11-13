### 1. ¿Por qué el frontend no necesita conectarse a PostgreSQL?
Porque el frontend no debería de poder conectarse directamente a la base de datos, sino que debe enviar la información al backend y este se encargará de redirigir la información a la base de datos. Así hay un paso extra de seguridad.

### 2. ¿Por qué el backend pertenece a dos redes?
Porque el backend necesita poder recibir datos del frontend que luego comunicara a la base de datos, por lo que necesita tener acceso a las dos redes. Así el backend actua como puente entre ambos.

### 3. ¿Qué servicio necesita publicar un puerto en el anfitrión?
El frontend sería el único que debe exponer un puerto hacia el exterior para poder acceder a la aplicacion desde el navegador.

### 4. ¿Por qué publicar PostgreSQL hacia fuera no es la solución adecuada para un fallo de comunicación interno?
Con la comunicación hacia fuera podemos conectarnos a la bbdd sin necesidad de acceder a través del backend. Esto sería un fallo de seguridad porque cualquiera podría conectarse a la base de datos sin pasar por el backend.

### 5. ¿Qué ventaja ofrece Docker Compose respecto a ejecutar los tres contenedores manualmente?
Te ahorra mucho tiempo de tener que levantarlos uno a uno a mano y, además si necesitas modificar algun dato de alguno de los contenedores es mucho mas sencillo porque solo es necesario modificarlo en el compose.

### 6. ¿Por qué hemos dividido la arquitectura en dos redes?
Para que el front no hable directamente con la bbdd sino que tenga que pasar por el backend y este tiene dos redes para hacer de ese intermediario.

### 7. ¿Por qué el backend utiliza `db` como dirección de PostgreSQL?
Porque llamamos al contenedor db que ya contiene la información de PostgreSQL.

### 8. ¿Qué diferencia existe entre detener un proyecto y eliminar sus volúmenes?
si detienes un proyecto puedes volverlo a iniciar sin problema y los datos persisten pero si elimnas sus volumenes se pierden los datos de esos contenedores.

### 9. ¿Qué consecuencias tendría para la empresa perder el volumen de PostgreSQL?
Que estarías eliminando la bbdd y todos sus datos.