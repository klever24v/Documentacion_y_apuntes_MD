# **Documentación del Proyecto WildPath**
- ## **1. Introducción**
  collapsed:: true
	- WildPath es una aplicación diseñada para los amantes de la aventura y la naturaleza. Su objetivo es proporcionar una plataforma donde los usuarios puedan descubrir, compartir y navegar rutas al aire libre, ya sea para senderismo, ciclismo, running o cualquier otra actividad en la naturaleza. También facilita la planificación y registro de rutas mediante funcionalidades avanzadas como geolocalización, seguimiento en tiempo real y análisis de recorridos.
- ## **2. Alcance del Proyecto**
  collapsed:: true
	- WildPath está dirigido a excursionistas, ciclistas y cualquier persona interesada en actividades al aire libre. La plataforma permitirá la consulta de rutas existentes, el registro de nuevas rutas y la interacción con otros usuarios mediante comentarios y calificaciones. Además, integrará alertas meteorológicas y recomendaciones de seguridad para mejorar la experiencia del usuario.
	- ### **Alcance Funcional**
	  collapsed:: true
		- **Mapa Interactivo:** Permite a los usuarios explorar rutas disponibles en un mapa detallado.
		- **Seguimiento GPS en tiempo real:** Registro de recorridos con datos precisos.
		- **Filtrado avanzado de rutas:** Búsqueda por actividad, dificultad, duración, etc.
		- **Sistema de puntos de interés:** Identificación de lugares clave en cada ruta.
		- **Interacción social:** Comentarios y sistema de "Me gusta" en rutas.
		- **Logros y recompensas:** Insignias por hitos alcanzados en el uso de la app.
		- **Personalización de perfiles:** Historial de rutas, estadísticas y configuraciones personales.
		- **Clima en tiempo real:** Integración con una API meteorológica para mostrar el clima en la zona.
		- **Compartir rutas mediante QR:** Generación de códigos QR para compartir rutas.
		- **Modo oscuro automático:** Cambio dinámico entre modo claro y oscuro.
		- **Alertas de seguridad:** Notificaciones sobre condiciones climáticas adversas.
- ## **3. Objetivos del Proyecto**
  collapsed:: true
	- ### **Objetivo General**
	  collapsed:: true
		- Facilitar la exploración de rutas al aire libre con información detallada y personalizada para mejorar la experiencia de los usuarios.
	- ### **Objetivos Específicos**
	  collapsed:: true
		- **Crear una comunidad:** Permitir que los usuarios compartan sus experiencias y recomendaciones sobre rutas.
		- **Implementar una navegación GPS intuitiva:** Para evitar que los usuarios se pierdan.
		- **Proporcionar datos completos sobre cada ruta:** Como dificultad, distancia, desnivel y tiempo estimado.
		- **Permitir la personalización de perfiles y el seguimiento de actividades.**
		- **Ofrecer herramientas de seguridad:** Como alertas meteorológicas y zonas de riesgo.
- ## **4. Características Principales** (==TODO== Revisar)
  id:: 67e5325f-908d-47c3-aed7-1dc79d96213c
  collapsed:: true
	- **Mapa Interactivo:** Permite a los usuarios explorar rutas disponibles en un mapa detallado.
	- **Seguimiento GPS en tiempo real:** Registro de recorridos con datos precisos.
	- **Filtros avanzados de rutas:** Búsqueda por actividad, dificultad, duración, etc.
	- **Sistema de puntos de interés:** Identificación de lugares clave en cada ruta.
	- **Interacción social:** Comentarios y sistema de "Me gusta" en rutas.
	- **Logros y recompensas:** Insignias por hitos alcanzados en el uso de la app.
	- **Personalización de perfiles:** Historial de rutas, estadísticas y configuraciones personales.
	- **Clima en tiempo real:** Integración con una API meteorológica para mostrar el clima en la zona. (==TODO== googlemaps)
	- **Compartir rutas mediante QR:** Generación de códigos QR para compartir rutas.
	- **Modo oscuro automático:** Cambio dinámico entre modo claro y oscuro.
	- **Alertas de seguridad:** Notificaciones sobre condiciones climáticas adversas.
	  
	  ![Ejemplo de interfaz del mapa interactivo](url-imagen)
- ## **5. Requisitos del Sistema**
  collapsed:: true
	- ### **Requisitos Funcionales**
	  collapsed:: true
		- **Registro e inicio de sesión:** El usuario debe poder registrarse e iniciar sesión con un correo o cuenta de Google.
		- **Creación, edición y eliminación de rutas personalizadas.**
		- **Recomendaciones personalizadas de rutas.**
		- **Interacción con rutas:** Los usuarios deben poder dejar comentarios y calificar rutas.
		- **Interfaz de administración:** Para gestionar rutas y reportes de usuarios (esto podría ser modificado más adelante).
	- ### **Requisitos No Funcionales** (==TODO== quitar despues es para aclararme que debe cumplir la APP)
	  collapsed:: true
		- **Responsividad:** La aplicación debe ser responsiva y funcionar en dispositivos móviles y computadoras.
		- **Tiempo de carga:** Los tiempos de carga no deben superar los 3 segundos en una conexión estándar.
		- **Privacidad:** Se debe garantizar la privacidad de los datos de los usuarios.
- ## **6. Funcionalidades Detalladas**
  collapsed:: true
	- ### **1. Gestión de Cuentas**
	  collapsed:: true
		- Registro y autenticación con email o cuenta de Google.
		- Edición y personalización del perfil.
		- Administración de rutas guardadas y actividades realizadas.
	- ### **2. Mapa Interactivo**
	  collapsed:: true
		- Visualización de rutas en un mapa dinámico.
		- Capas personalizables (satélite, topográfico, estándar).
		  
		  ![TODO IMAGEN Ejemplo de visualización de rutas en el mapa](url-imagen)
	- ### **3. Seguimiento GPS** (==TODO== Ideas para concretar )
	  collapsed:: true
		- Registro de rutas con distancia, velocidad y tiempo.
		- Estadísticas en tiempo real.
		- Descarga de rutas offline.
	- ### **4. Filtros Avanzados de Búsqueda** (==TODO== revisar)
	  collapsed:: true
		- Búsqueda de rutas por tipo de actividad o nombre.
		- Filtros por dificultad, duración, distancia y altitud.
	- ### **5. Interacción Social**
	  collapsed:: true
		- Comentarios en cada ruta.
		- Sistema de "Me gusta".
		- Foros de discusión y recomendaciones entre usuarios. (==TODO== Comentarios quitar esto después  )
		  
		  ![TODO IMAGEN Ejemplo de interacción social en la app](url-imagen)
	- ### **6. Seguridad y Alertas** (==TODO== idea pero no se como implementarla)
	  collapsed:: true
		- Notificaciones meteorológicas en tiempo real.
		- Registro de zonas peligrosas y recomendaciones de seguridad.
- ## **7. Tecnologías Utilizadas**
	- ### **Frontend:**
		- **Vue.js:** Framework JavaScript para la creación de interfaces interactivas.
		- **Bootstrap:** Para diseño responsivo y componentes visuales (como formularios, barra de navegación, etc.).
	- ### **Backend:**
		- **Node.js:** Plataforma de JavaScript en el servidor.
		- **Express.js:** Framework para crear APIs y manejar rutas.
		- **MongoDB:** Base de datos NoSQL para almacenar usuarios, rutas y otros datos. (==TODO== estamos seguros ??)
		- ### **Otras Tecnologías:**
		- **JWT (JSON Web Tokens):** Para la autenticación y gestión de sesiones. (==TODO== cambiar por Firebase)
		- **API meteorológica:** Para integrar las alertas y el clima en tiempo real.(==TODO== Segun lalo esto va con googlemaps XD )
- ## **8. Estructura de Ficheros** ( ==TODO== PENDIENTE REVISAR es una plantilla generada)
  collapsed:: true
	- ```
	      /wildpath
	      /backend
	        /controllers
	          - authController.js
	          - routeController.js
	          - userController.js
	        /models
	          - routeModel.js
	          - userModel.js
	        /routes
	          - authRoutes.js
	          - routeRoutes.js
	          - userRoutes.js
	      /frontend 
	        /components
	          - Header.vue
	          - RouteList.vue
	          - MapView.vue
	        /views
	          - Home.vue
	          - RouteDetail.vue
	        /assets
	          - logo.png
	          - map-icon.svg
	      /public
	        - index.html
	      /config
	        - config.js
	      .gitignore
	      README.md
	  ```
- ## **9. API Web**
  collapsed:: true
	- ### **Endpoints Principales:**
	- **Autenticación y Login:**
	  collapsed:: true
		- **POST /api/v1/login:** Autenticar usuarios y devolver token.
	- **Usuarios:**
	  collapsed:: true
		- **POST /api/v1/users:** Crear un nuevo usuario.
		- **GET /api/v1/users/{id}:** Consultar detalles del usuario.
		- **PUT /api/v1/users/{id}:** Editar datos del usuario.
		- **DELETE /api/v1/users/{id}:** Eliminar un usuario.
	- **Rutas:**
	  collapsed:: true
		- **POST /api/v1/routes:** Crear una nueva ruta.
		- **GET /api/v1/routes:** Consultar rutas.
		- **PUT /api/v1/routes/{id}:** Editar una ruta.
		- **DELETE /api/v1/routes/{id}:** Eliminar una ruta.
	- **Comentarios y Calificaciones:**
	  collapsed:: true
		- **POST /api/v1/routes/{id}/comments:** Dejar un comentario.
		- **POST /api/v1/routes/{id}/likes:** Dar un "me gusta" a una ruta.
- ## **10. Seguridad y Accesos**
  collapsed:: true
	- **Autenticación:** Cada endpoint validará el token de autenticación del usuario. (FIREBASE)
	- **Control de Roles:** Los usuarios tendrán acceso solo a los recursos y acciones que les corresponden según su rol. (Pendiente preguntar a lalo)
- ## **11. Conclusión**
  collapsed:: true
	- WildPath tiene el objetivo de revolucionar la forma en que los amantes de la naturaleza y las actividades al aire libre interactúan con las rutas. La plataforma proporcionará herramientas tanto para la exploración como para la seguridad de los usuarios, mientras fomenta la creación de una comunidad activa que comparta y valore rutas, experiencias y consejos.
- ==Nota== --> hay puntos con ==TODO== a revisar
  collapsed:: true
	- Cada sección de esta documentación puede ampliarse y detallar más aspectos técnicos y de implementación a medida que se avance en el desarrollo del proyecto,
	- falta añadir las tablas con objetivos funcionales  y añadir las imágenes sobre el proyecto en ``[TODO Imagen]``
	- Esto es el contenido mas o menos representativo, de aquí hay que ver que modificamos.
	- ==Preguntas==
	  collapsed:: true
		- si implementamos IA por ejemplo para que nos lea los ficheros json y nos liste las rutas y nos cargue en la pantalla principal ?? (tenemos que aprender a hacerlo pero queda chulo xD )
		- la implementación de ia es mucho curro tenemos que ver bien si podemos o no automatizar ciertas partes de nuestro proyecto, tenemos que tener en cuenta que pueda ser escalable, pero aun así la lectura automática con una ia compilada es una cosa a tener en cuenta.