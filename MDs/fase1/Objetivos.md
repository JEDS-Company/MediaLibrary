# Objetivos del proyecto

## Objetivos generales

Con MediaLibrary hemos establecido una serie de objetivos generales que pretendemos que nuestro proyecto sea capaz de cumplir para el final de su desarrollo: 

- Llevar un registro de las películas, libros y/o videojuegos que consumen los usuarios.
- Puntuar el contenido de tu librería.
- Ver las librerías de otros usuarios.
- Seguir a otros usuarios.
- Que los usuarios puedan descubrir contenido nuevo mediante una funcionalidad.
- Desbloquear logros dependiendo de los contenidos que los usuarios tengan en sus librerías.
- Añadir el progreso del libro, la película o videojuego que el usuario está disfrutando.
- Poder guardar el contenido que quieras consumir en un futuro.

## Objetivos específicos

Para llevar a cabo los objetivos generales, hemos marcado estas otras pautas relacionadas con el desarrollo y diseño de la arquitectura de nuestro proyecto:

- Crear una base de datos PostgreSQL para almacenar los datos de los usuarios y las medias de la aplicación.
- Crear una API en Java Spring Boot que gestione las peticiones del cliente web y de la aplicación móvil, recupere la información de la base de datos o en su defecto consiga la información de las APIs externas y por último devuelva la información al cliente de origen.
- Crear un cliente web en React que haga peticiones a la API de MediaLibrary.
- Crear una aplicación móvil en Kotlin que también consuma la API de MediaLibrary.
- Hostear la API y el cliente web en un entorno cloud.
