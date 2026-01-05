# Diccionario de datos

En este diccionario de datos se puede encontrar los campos de cada tabla de la base de datos con su información y una descripción sobre el propósito de dicho campo.

### 1. Tabla: `users`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | Identificador único del usuario. |
| `username` | `username` | `String` | `VARCHAR(50)` | UNIQUE | NO | Nombre único para identificar usuarios |
| `nickname` | `nickname` | `String` | `VARCHAR(50)` |  | NO | Nombre visible o apodo. |
| `firebaseUid` | `firebase_uid` | `String` | `VARCHAR(128)` | UNIQUE | SI | Identificador del usuario en Firebase. |
| `email` | `email` | `String` | `VARCHAR(100)` | UNIQUE | NO | Correo electrónico. |
| `profilePicture` | `profile_picture` | `String` | `VARCHAR(255)` |  | SI | URL de la imagen de perfil. |
| `usersFollowed` |  | `Set<User>` |  |  | SI | Lista de usuarios a los que sigue esa persona. |
| `achievements` |  | `Set<Achievements>` |  |  | SI | Lista de logros del usuario |

### 2. Tabla: `follows`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
|  | `follower_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con followed_id) | NO | Usuario que sigue a otro. |
|  | `followed_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con follower_id) | NO | Usuario que es seguido. |

### 3. Tabla: `medias`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID único del contenido. |
| `externalId` | `external_id` | `String` | `VARCHAR(255)` | UNIQUE (con source) | NO | ID original de la API externa. |
| `source` | `source` | `SourceName` | `VARCHAR(32)` | UNIQUE (con external_id) | NO | Proveedor (TMDB, IGDB...). |
| `lastUpdated` | `last_updated` | `LocalDateTime` | `TIMESTAMP` |  | NO | Momento en el que se actualizó por última vez la información. |
| `title` | `title` | `String` | `VARCHAR(255)` |  | NO | Título de la obra. |
| `coverUrl` | `cover_url` | `String` | `VARCHAR(512)` |  | SI | URL de la portada. |
| `averageRating` | `average_rating` | `Double` | `FLOAT` | DEFAULT 0.0 | NO | Puntuación promedio global. |
| `voteCount` | `vote_count` | `Integer` | `INT` | DEFAULT 0 | NO | Cantidad total de votos. |
| `description` | `description` | `String` | `TEXT` |  | SI | Sinopsis o resumen. |
| `releaseYear` | `release_year` | `Integer` | `INT` |  | SI | Año de lanzamiento. |
| `creator` | `creator` | `String` | `VARCHAR(100)` |  | SI | Autor, Director o Desarrollador. |
| `genres` |  | `Set<Genre>` |  |  | SI | Set de géneros del contenido. |

### 4. Tabla: `medias_genres`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
|  | `media_id` |  | `BIGINT` | PK, FK, UNIQUE (con genre_id) | NO | Referencia a la tabla Media. |
|  | `genre_id` |  | `BIGINT` | PK, FK, UNIQUE (con media_id) | NO | Referencia a la tabla Genre. |

### 5. Tabla: `genres`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (medias) | NO | Id del género. |
| `name` | `name` | `String` | `VARCHAR(32)` | UNIQUE | NO | Nombre del género. |
| `medias` |  | `Set<Media>` |  |  | NO | Set de medias con esta etiqueta. |

### 6. Tabla: `movies`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (medias) | NO | Referencia a la tabla Media. |
| `duration` | `duration` | `Integer` | `INT` |  | SI | Duración en minutos. |

### 7. Tabla: `books`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (medias) | NO | Referencia a la tabla Media. |
| `bookType` | `book_type` | `BookType` | `VARCHAR(20)` |  | NO | Novel, Manga o Comic. |
| `isbn` | `isbn` | `String` | `VARCHAR(20)` |  | SI | Identificador ISBN. |
| `pages` | `pages` | `Integer` | `INT` |  | SI | Número de páginas. |
| `editorial` | `editorial` | `String` | `VARCHAR(100)` |  | SI | Editorial publicadora. |
| `chapters` | `chapters` | `Integer` | `INT` |  | SI | Capítulos (para mangas). |

### 8. Tabla: `series`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (Media) | NO | Referencia a la tabla Media. |
| `seasons` | `seasons` | `Integer` | `INT` |  | SI | Cantidad de temporadas. |
| `chapters` | `chapters` | `Integer` | `INT` |  | SI | Total de episodios. |
| `animator` | `animator` | `String` | `VARCHAR(100)` |  | SI | Estudio (solo Anime). |

### 9. Tabla: `videogames`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK, FK (Media) | NO | Referencia a la tabla Media. |
| `platforms` |  | `List<Platform>` |  |  | SI | Lista de plataformas del videojuego. |

### 10. Tabla: `platforms`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID de la plataforma. |
| `name` | `name` | `String` | `VARCHAR(50)` | UNIQUE | NO | Nombre (PC, Xbox, etc.). |

### 11. Tabla: `games_platforms`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
|  | `videogame_id` | `Long` | `BIGINT` | PK, FK (medias), UNIQUE (con platform_id) | NO | ID del videojuego. |
|  | `platform_id` | `Long` | `BIGINT` | PK, FK (platforms), UNIQUE (con media_id) | NO | ID de la plataforma. |

### 12. Tabla: `library_items`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID del registro. |
| `userId` | `user_id` | `Long` | `BIGINT` | FK (users), UNIQUE (con media_id) | NO | Usuario propietario. |
| `mediaId` | `media_id` | `Long` | `BIGINT` | FK (medias), UNIQUE (con user_id) | NO | Contenido guardado. |
| `status` | `status` | `ItemStatus` | `VARCHAR(20)` |  | NO | Pending, Watching, Completed... |
| `rating` | `rating` | `Integer` | `INT` |  | SI | Nota del 0 al 10. |
| `progress` | `progress` | `Integer` | `INT` |  | SI | Porcentaje del 0 al 100. |
| `addedDate` | `added_date` | `LocalDate` | `DATE` |  | NO | Fecha de añadido a la lista. |
| `completedDate` | `completed_date` | `LocalDate` | `DATE` |  | SI | Fecha de finalización. |

### 13. Tabla: `achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `id` | `id` | `Long` | `BIGINT` | PK | NO | ID del logro. |
| `name` | `name` | `String` | `VARCHAR(100)` |  | NO | Nombre del logro. |
| `description` | `description` | `String` | `VARCHAR(255)` |  | SI | Cómo conseguirlo. |

### 14. Tabla: `users_achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
| `userId` | `user_id` | `Long` | `BIGINT` | PK, FK (users), UNIQUE (con achievement_id) | NO | Usuario ganador. |
| `achievementId` | `achievement_id` | `Long` | `BIGINT` | PK, FK (achievements), UNIQUE (con user_id) | NO | Logro desbloqueado. |
| `unlockedAt` | `unlocked_at` | `LocalDate` | `DATE` |  | NO | Momento exacto del logro. |

### 15. Tabla: `medias_achievements`

| Columna Java | Columna SQL | Tipo de Dato Java | Tipo de Dato SQL | Restricciones | Nulo | Descripción |
| --- | --- | --- | --- | --- | --- | --- |
|  | `achievement_id` | `Long` | `BIGINT` | PK, FK (achievements), UNIQUE (con media_id) | NO | El logro que requiere este contenido. |
|  | `media_id` | `Long` | `BIGINT` | PK, FK (medias), UNIQUE (con achievement_id) | NO | El contenido necesario para el logro. |
