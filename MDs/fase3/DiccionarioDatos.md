# Diccionario de datos 

En este diccionario de datos se puede encontrar los campos de cada tabla de la base de datos con su información y una descripción sobre el propósito de dicho campo.

### 1\. Tabla: `users`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | Identificador único del usuario. |
| `username` | `username` | `String` | `VARCHAR(50)` | UNIQUE | NO | Nombre único para identificar usuarios. |
| `nickname` | `nickname` | `String` | `VARCHAR(50)` | | NO | Nombre visible o apodo. |
| `email` | `email` | `String` | `VARCHAR(100)` | UNIQUE | NO | Correo electrónico. |
| `password` | `password` | `String` | `VARCHAR(255)` | | NO | Contraseña hasheada. |
| `profilePicture` | `profile_picture` | `String` | `VARCHAR(255)` | | SÍ | URL de la imagen de perfil. |

### 2\. Tabla: `follows`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | `follower_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con followed\_id) | NO | Usuario que sigue a otro. |
| | `followed_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con follower\_id) | NO | Usuario que es seguido. |

### 3\. Tabla: `medias`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID único del contenido. |
| | `dtype` | `String` | `VARCHAR(31)` | | NO | Discriminador (Movie, Book, etc.). Se genera automáticamente. |
| `externalId` | `external_id` | `String` | `VARCHAR(100)` | UNIQUE (con source) | NO | ID original de la API externa. |
| `source` | `source` | `SourceEnum` | `VARCHAR(20)` | UNIQUE (con external\_id) | NO | Proveedor (TMDB, IGDB...). |
| `lastUpdated` | `last_updated` | `LocalDateTime` | `TIMESTAMP` | | NO | Momento en el que se actualizó por última vez la información. |
| `title` | `title` | `String` | `VARCHAR(255)` | | NO | Título de la obra. |
| `coverUrl` | `cover_url` | `String` | `VARCHAR(255)` | | SÍ | URL de la portada. |
| `averageRating` | `average_rating` | `Double` | `FLOAT` | | SÍ | Puntuación promedio global. |
| `voteCount` | `vote_count` | `Integer` | `INT` | DEFAULT 0 | NO | Cantidad total de votos. |
| `description` | `description` | `String` | `TEXT` | | SÍ | Sinopsis o resumen. |
| `releaseYear` | `release_year` | `Integer` | `INT` | | SÍ | Año de lanzamiento. |
| `creator` | `creator` | `String` | `VARCHAR(100)` | | SÍ | Autor, Director o Desarrollador. |
| `genre` | `genre` | `String` | `VARCHAR(100)` | | SÍ | Género principal. |

### 4\. Tabla: `movies`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (medias) | NO | Referencia a la tabla Media. |
| `duration` | `duration` | `Integer` | `INT` | | SÍ | Duración en minutos. |

### 5\. Tabla: `books`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (medias) | NO | Referencia a la tabla Media. |
| `bookType` | `book_type` | `BookTypeEnum` | `VARCHAR(20)` | | NO | Novel, Manga o Comic. |
| `isbn` | `isbn` | `String` | `VARCHAR(20)` | | SÍ | Identificador ISBN. |
| `pages` | `pages` | `Integer` | `INT` | | SÍ | Número de páginas. |
| `editorial` | `editorial` | `String` | `VARCHAR(100)` | | SÍ | Editorial publicadora. |
| `chapters` | `chapters` | `Integer` | `INT` | | SÍ | Capítulos (para mangas). |

### 6\. Tabla: `series`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (Media) | NO | Referencia a la tabla Media. |
| `seasons` | `seasons` | `Integer` | `INT` | | SÍ | Cantidad de temporadas. |
| `chapters` | `chapters` | `Integer` | `INT` | | SÍ | Total de episodios. |
| `animator` | `animator` | `String` | `VARCHAR(100)` | | SÍ | Estudio (solo Anime). |

### 7\. Tabla: `platforms`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID de la plataforma. |
| `name` | `name` | `String` | `VARCHAR(50)` | | NO | Nombre (PC, Xbox, etc.). |

### 8\. Tabla: `games_platforms`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | `media_id` | `Long` | `BIGINT` | PK, FK (medias), UNIQUE (con platform\_id) | NO | ID del videojuego. |
| | `platform_id` | `Long` | `BIGINT` | PK, FK (platforms), UNIQUE (con media\_id) | NO | ID de la plataforma. |

### 9\. Tabla: `library_items`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID del registro. |
| `userId` | `user_id` | `Long` | `BIGINT` | FK (users), UNIQUE (con media\_id) | NO | Usuario propietario. |
| `mediaId` | `media_id` | `Long` | `BIGINT` | FK (medias), UNIQUE (con user\_id) | NO | Contenido guardado. |
| `status` | `status` | `StatusEnum` | `VARCHAR(20)` | | NO | Pending, Watching, Completed... |
| `rating` | `rating` | `Integer` | `INT` | | SÍ | Nota del 0 al 10. |
| `progress` | `progress` | `Integer` | `INT` | | SÍ | Porcentaje, pág o cap actual. |
| `addedDate` | `added_date` | `LocalDate` | `DATE` | | NO | Fecha de añadido a la lista. |
| `completedDate` | `completed_date` | `LocalDate` | `DATE` | | SÍ | Fecha de finalización. |

### 10\. Tabla: `achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID del logro. |
| `name` | `name` | `String` | `VARCHAR(100)` | | NO | Nombre del logro. |
| `description` | `description` | `String` | `VARCHAR(255)` | | SÍ | Cómo conseguirlo. |

### 11\. Tabla: `users_achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `userId` | `user_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con achievement\_id) | NO | Usuario ganador. |
| `achievementId` | `achievement_id` | `Long` | `BIGINT` | PK, FK (achievements), UNIQUE (con user\_id) | NO | Logro desbloqueado. |
| `unlockedAt` | `unlocked_at` | `LocalDate` | `DATE` | | NO | Momento exacto del logro. |

### 12\. Tabla: `medias_achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| | `achievement_id` | `Long` | `BIGINT` | PK, FK (achievements), UNIQUE (con media\_id) | NO | El logro que requiere este contenido. |
| | `media_id` | `Long` | `BIGINT` | PK, FK (medias), UNIQUE (con achievement\_id) | NO | El contenido necesario para el logro. |