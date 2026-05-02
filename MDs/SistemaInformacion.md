# Sistema de información

Participantes:

- Emilio García Muñoz
- Jonathan Villalba Moran
- Sergio Llorente Gonzalez
- Diego Fernando Valencia Correa

Existen diversas aplicaciones en las que los usuarios pueden llevar un seguimiento de los contenidos que ven o leen y pueden ponerles una nota. Además pueden ver a otros usuarios y el contenido que estos consumen. Sin embargo, necesitar tener diversas cuentas en diferentes aplicaciones o páginas web para poder realizar un seguimiento de tus aficiones. Esto hace que llevar un registro de ellas sea tedioso o dificil. Debido a este problema, hemos decidido aportar nuestra propia solución: MediaLibrary.

MediaLibrary es una aplicación web y móvil en la que la gente puede crear su propia lista de películas, libros y videojuegos que hayan visto, leído y/o jugado. En dicha lista podrás ponerle una nota del 0 al 10 a los contenidos que añadas. Además podrás seguir a otros usuarios y ver sus listas.

De cada usuario se desea almacenar su nombre de usuario (que es único para cada persona), su apodo en la aplicación (este si que podrá ser repetido), su correo electrónicoy foto de perfil.

Además, queremos almacenar los usuarios a los que sigue cada persona.

De cada contenido en la librería de un usuario deseamos almacenar la calificación de dicho contenido, el progreso del usuario y la fecha en la que lo añadió.

Además, los usuarios podrán almacenar en una lista de deseados los contenidos que quieren ver en un futuro. En dicha lista no habrá una calificación del contenido.

Un contenido que esté en la libería del usuario no puede estár también en la lista de deseados, por lo que al añadir un contenido a su librería se quitará automáticamente de la lista de deseados en caso de que hubiese sido añadido ahí anteriormente. A su misma vez, tampoco se podrá añadir a la lista de deseados un contenido que ya esté en la librería personal.

Los usuarios tambíen pueden desbloquear logros dependiendo del contenido que tengan añadido en sus librerías. De estos logros queremos almacenar el nombre y el contenido que lo conforma.

Sobre los contenidos de nuestra aplicación:

De las películas queremos saber su nombre, creador, portada, género y sinopsis.

De los libros deseamos conocer su nombre, escritor, portada, sinopsis y género.

De los videojuegos deseamos conocer su nombre, sinopsis, compañia/creador, portada, género.

De las plataformas en las que estarán disponibles los videojuegos queremos conocer su nombre.
