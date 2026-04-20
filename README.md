# Bautista-post1-u5
Unidad 5: Integración en Aplicaciones Web Post-Contenido 1

Este proyecto consiste en el desarrollo de una API REST para la gestión de libros, implementada con Spring Boot. Permite realizar operaciones básicas como crear, consultar, actualizar, eliminar y buscar libros dentro de una base de datos en memoria.

La aplicación está orientada a demostrar el uso de arquitectura en capas, validaciones de datos y persistencia con JPA.

Tecnologías utilizadas
Java 17 o superior
Spring Boot
Spring Data JPA
Hibernate
Base de datos H2
Maven
Estructura del proyecto

El proyecto sigue una arquitectura por capas:

controller: expone los endpoints REST
service: contiene la lógica de negocio
repository: maneja el acceso a datos
model: define la entidad Libro
Entidad Libro

La entidad principal del sistema es Libro, la cual contiene los siguientes atributos:

id: identificador único
titulo: nombre del libro
autor: autor del libro
isbn: código único del libro
anioPublicacion: año de publicación
categoria: categoría o género

Se aplican validaciones para asegurar la integridad de los datos, como campos obligatorios y formato del ISBN.

Ejecución del proyecto

Para ejecutar la aplicación se deben seguir los siguientes pasos:

Clonar el repositorio
Ubicarse en la carpeta del proyecto
Ejecutar el comando:
./mvnw spring-boot:run

La aplicación se iniciará en:

http://localhost:8080

Base de datos

Se utiliza H2 en memoria, lo que significa que los datos se reinician cada vez que se reinicia la aplicación.

La consola de administración está disponible en:

http://localhost:8080/h2-console

Configuración:

JDBC URL: jdbc:h2:mem:biblioteca_db
Usuario: SA
Contraseña: (vacía)
Endpoints disponibles
Crear libro

POST /api/libros

Ejemplo:

curl -X POST http://localhost:8080/api/libros \
-H "Content-Type: application/json" \
-d '{
  "titulo": "Clean Code",
  "autor": "Robert C. Martin",
  "isbn": "9780132350884",
  "anioPublicacion": 2008,
  "categoria": "Ingenieria"
}'

Respuesta: 201 Created con el libro creado.

Listar libros

GET /api/libros

curl http://localhost:8080/api/libros

Respuesta: lista de libros en formato JSON.

Obtener libro por id

GET /api/libros/{id}

curl http://localhost:8080/api/libros/1

Respuesta: 200 OK o 404 Not Found.

Actualizar libro

PUT /api/libros/{id}

curl -X PUT http://localhost:8080/api/libros/1 \
-H "Content-Type: application/json" \
-d '{
  "titulo": "Clean Code Updated",
  "autor": "Robert C. Martin",
  "isbn": "9780132350884",
  "anioPublicacion": 2008,
  "categoria": "Software"
}'
Eliminar libro

DELETE /api/libros/{id}

curl -X DELETE http://localhost:8080/api/libros/1

Respuesta: 204 No Content o 404 si no existe.

Buscar libros

GET /api/libros/buscar?q=palabra

curl "http://localhost:8080/api/libros/buscar?q=Clean"

Permite buscar libros por coincidencias en el título o autor.

Manejo de errores
400 Bad Request: datos inválidos en la solicitud
404 Not Found: recurso no encontrado
500 Internal Server Error: error interno del servidor

## Evidencias ##
<img width="1460" height="478" alt="image" src="https://github.com/user-attachments/assets/0eafddd4-210f-46c7-8ed9-3860858f2d03" />
