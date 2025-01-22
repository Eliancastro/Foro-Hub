Foro Hub es una aplicación de foro diseñada para facilitar la comunicación y discusión entre usuarios. Esta aplicación permite a los usuarios crear tópicos, responder a los mismos y participar en discusiones.

Características:
Registro y autenticación de usuarios.
Creación, edición y eliminación de tópicos.
Respuesta a tópicos existentes.
Listado de usuarios y tópicos.
Autenticación mediante JWT.

Tecnologías utilizadas:
Java
Spring Boot
Spring Security
JWT (JSON Web Tokens)
JPA (Java Persistence API)
H2 Database (para desarrollo y pruebas)
Postman (para pruebas de API)
Swagger (para documentación de API)

Estructura del proyecto:
Entities: Clases de entidad que representan las tablas de la base de datos.
Dto: Clases de Data Transfer Object utilizadas para transferir datos entre el cliente y el servidor.
Repository: Interfaces que extienden JpaRepository para realizar operaciones CRUD en las entidades.
Service: Clases de servicio que contienen la lógica de negocio.
Controller: Clases de controlador que manejan las solicitudes HTTP.
Security: Clases relacionadas con la configuración de seguridad y la autenticación.

Clona el repositorio:
git clone https://github.com/Eliancastro/Foro-Hub

Abre el proyecto en tu IDE favorito.
Configuración
Base de datos: MySQL 

Este proyecto está configurado para usar una base de datos H2 en memoria por defecto. Puedes cambiar la configuración de la base de datos en el archivo application.properties.

Swagger:
Swagger está configurado para generar documentación de la API automáticamente. Puedes acceder a la interfaz de Swagger en la siguiente URL cuando el servidor esté en funcionamiento:
http://localhost:8080/swagger-ui/index.html

<img width="608" alt="chrome_8qC8WQ28US" src="https://github.com/user-attachments/assets/17ac6605-dfe0-4f68-be30-938104a18fd8" />

Para ejecutar la aplicación, utiliza el siguiente comando en la raíz del proyecto:
mvn spring-boot:run

La aplicación estará disponible en http://localhost:8080.

Endpoints principales:
/login: Endpoint para autenticación de usuarios. Envía una solicitud POST con un JSON que contiene username y password.
/usuarios: Endpoint para listar usuarios. Requiere autenticación mediante un token JWT.
/topicos: Endpoint para manejar la creación, actualización y eliminación de tópicos.

Ejemplos:

Para una autenticación

Solicitud:
POST http://localhost:8080/login

Body:
{
    "username": "nombre_usuario",
    "password": "contraseña"
}

Respuesta:
{
    "token": "jwt_token_generado"
}

Crear un tópico

Solicitud:
GET http://localhost:8080/topico/topicos

Headers:
Authorization: Bearer jwt_token_generado
Content-Type: application/json

Body:
{
  "totalPages": 1,
  "totalElements": 3,
  "size": 3,
  "content": [
    {
      "id": 1,
      "title": "Ciencias",
      "message": "Exploración de física, y química.",
      "status": "ACTIVO",
      "usuario_Id": 1,
      "curso": "Introducción a la Ciencia",
      "date": "2024-07-01T08:00:00.000Z"
    },
    {
      "id": 2,
      "title": "Historia",
      "message": "Estudio de eventos históricos",
      "status": "ACTIVO",
      "usuario_Id": 2,
      "curso": "Civilización Antigua",
      "date": "2024-07-02T09:30:00.000Z"
    },
    {
      "id": 3,
      "title": "Arte",
      "message": "Explorando diversas formas de expresión Artistica.",
      "status": "ACTIVO",
      "usuario_Id": 3,
      "curso": "Dibujo y Pintura",
      "date": "2024-07-03T11:00:00.000Z"
    }
  ],
  "number": 0,
  "sort": "asc",
  "first": true,
  "last": true,
  "numberOfElements": 3,
  "pageable": {
    "offset": 0,
    "sort": "asc",
    "paged": true,
    "unpaged": true,
    "pageNumber": 0,
    "pageSize": 3
  },
  "empty": false
}

