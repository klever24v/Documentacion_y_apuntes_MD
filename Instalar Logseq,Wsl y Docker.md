- LATER  Instalar Logseq y escribir documentación de cómo montar el entorno WSL y Docker
	- ## Instalacion
		- ### 1. Instalar Logseq.
			- [Descargar el instalador](https://logseq.com)
			- Después de instalarlo  nos pedirá que seleccionaremos el directorio donde vamos a almacenar los ficheros, y ya procedemos a
				- ==Docker usa la arquitectura "AMD64", compatible con Intel==
				- Instalación
					- 🌀Añadir acceso directo (opcional).
					- Comprobar que Docker este funcionando comprobamos la versión-->  `docker --version`
					- Tenemos dos formas de configurarlo
					  collapsed:: true
						- **configuración recomendada**(requiere contraseña de administrador)
						  logseq.order-list-type:: number
						- **Usar configuración avanzada** Permite configurar manualmente las preferencias según tus necesidades.
						  logseq.order-list-type:: number
						- Si es tu **primer contacto con Docker**, te **recomiendo usar la configuración recomendada**.
					- Al ejecutarlo nos presenta **Preguntas opcionales** que aparece durante la instalación de Docker Desktop para conocer tu **rol o perfil profesional**.
			- Comandos básicos de uso.
			  collapsed:: true
				- [[]] -->  Crear una Página Nueva
				- \# etiquetas --> usamos contra barra para que no lo detecte como etiqueta
				- [Descargar el instalador](https://logseq.com) --> Usamos [texto]+(enlace) para decorar el enlace.
				- -Lista de viñetas
				- 1.Lista numerada
				- ==Resaltar Texto==
				- TODO --> Tarea pendiente
				- DOING --> Tarea en proceso
				  :LOGBOOK:
				  CLOCK: [2025-03-17 Mon 12:36:13]
				  :END:
				- DONE --> Tarea completada
				- **Texto negrita**
				- *Texto cursiva*
				- `código` --> añadir una línea de código
				- Añadir bloque de código
				- ```bash 
				  ```
				- Insertar tablas: --> igual que en .md
					- | Nombre  | Edad | Ciudad |
					  |---------|------|--------|
					  | Juan    | 25   | Madrid |
					  | Ana     | 30   | Barcelona |
					  | Carlos  | 22   | Valencia |
				- @Nombre de la pagina -->  para hacer referencia a otras paginas creadas.
				- ((ID_del_bloque)) --> Cada bloque en Logseq tiene un ID único y puedes enlazarlo.
				  id:: 67d81e06-997a-44c6-8228-2b8ea0999775
				- \/time --> define la hora actual
				- \/date --> Añade una fecha especifica.
				- Usa `Ctrl + K` --> Para buscar cualquier página o contenido.
				- Usa `Ctrl + B` --> Negrita
				- Usa `Ctrl + I` --> Cursiva
		- ### 2. Instalar WSL. ⚠️Docker actualizara WSL instalar esto antes
		  collapsed:: true
			- Instalador por comando--> `wsl --install`, si no quieres instalar Ubuntu usamos  `--no-distribution`
			- verificar si esta funcionando --> `wsl --list --verbose`
			- Terminada la instalación iniciamos con el terminal
				- Iniciamos  `cmd` o  `PowerShell`
				- usamos `wsl` para iniciar
				- Cuando ejecutaste `wsl` **la primera vez que inicias WSL** y el sistema necesita un usuario por defecto para trabajar.
				- Si no hay ningún incidente comprobamos el usuario que estamos usando con `whoami`
				- Si estamso con root y queremos cambiar de usuario usamos `su [nomrbeUsuario]` y reiniciamos wsl con `wsl --shutdown` si todo va bien aparece lo siguiente
				- ``` bash
				  		klever@klever:/mnt/c/Users/ketoa$
				  ```
			- Comandos básicos de Linux [[Comandos Linux]]
		- ### 3. Instalar  Docker
			- [Descargar instalador](https://www.docker.com/get-started/)
	- ## Prueba
	  collapsed:: true
		- Comprobar funcionamiento
		  logseq.order-list-type:: number
			- Verificamos  que funcionen correctamente en el terminal comprobando su versión
			  logseq.order-list-type:: number
			  collapsed:: true
				- WSL --> `wsl --list --verbose`
				  logseq.order-list-type:: number
					- ``` Salida
					  		NAME      STATE           VERSION
					  		Ubuntu    Running         2
					  ```
				- Docker --> `docker --version`
				  logseq.order-list-type:: number
					- ````Salida
					  		Docker version 27.5.1, build 9f9e405
					  ```
					- **Prueba Docker con un Contenedor de Prueba**
						- `docker run hello-world`
						- ```Salida esperada 
						  		Hello from Docker!
						  		This message shows that your installation appears to be working correctly.
						  ```
						-
		- Probar Docker Dentro de WSL
		  logseq.order-list-type:: number
			- Dentro de WSL, ejecutamos:  `docker run -it ubuntu bash`
			- Se iniciara un contenedor de Ubuntu y nos mostrara algo parecido a lo siguiente, lo cual nos indica que funciona correctamente.
			- ```Salida 
			  		root@container_id:/#
			  ```
			- ahora dentro del contenedor probaremos los siguientes comandos.
			- ```bash 
			  		lsb_release -a    # Verifica que estás dentro de Ubuntu
			  		apt update && apt upgrade -y   # Actualiza los paquetes dentro del contenedor
			  		exit    # Sal del contenedor
			  ```
			- En mi vaso Vamos a leer un fichero almacenado en C:\logseq\Comandos Linux para ello usamos el siguiente comando `docker run --rm -it -v /mnt/c/Logseq/pages:/data ubuntu bash` esto los ejecuta un contenedor con nuestro Ubuntu dentro de este ya procedemos a usar `cat /data/Comandos\ Linux.md` para  Leer el Archivo, si lo leemos con `cat` es para ver Contenido Completo.
			- En este caso espero  la siguiente salda
			- ``` Salida
			  		klever@klever:/mnt/c/Users/ketoa$ docker run --rm -it -v /mnt/c/Logseq/pages:/data ubuntu bash
			  			root@be105aead2ae:/# cat /data/Comandos\ Linux.md
			  				- Comandos Linux básicos
			          		- # 🚀 Comandos Básicos de Linux
			            			Lista de comandos básicos organizados por categorías para facilitar su aprendizaje. 📌
			            			---
			         			 - ## **1️⃣ Comandos Relacionados con Usuarios y Grupos 🧑**
			         			 - ### 📀 Información del Usuario
			  
			           		 ```
			  ```
			  -
			  - Incidencia.
			  - ```Salida de Error  
			  	root@klever:/mnt/c/Users/ketoa# docker --version
			  
			  	The command 'docker' could not be found in this WSL 2 distro.
			  	We recommend to activate the WSL integration in Docker Desktop settings.
			  	For details about using Docker Desktop with WSL 2, visit:
			  
			  	https://docs.docker.com/go/wsl2/
			  	root@klever:/mnt/c/Users/ketoa#
			  ```
		- El mensaje indica que **Docker no está disponible dentro de tu distribución de WSL 2**. Esto ocurre porque **Docker Desktop no tiene activada la integración con WSL** o porque **Docker no está en el `PATH` dentro de WSL**.
			- ### **Activar la Integración de Docker con WSL**
			  Para que Docker funcione en WSL 2, debes activar la integración en **Docker Desktop**:
			  1️⃣ **Abre Docker Desktop**
			  2️⃣ Ve a **Settings (Configuración)** 
			  3️⃣ En la sección **Resources > WSL Integration**, activa la opción:
			  ✅ **"Enable integration with my default WSL distro"**
			  4️⃣ Asegúrate de que **Ubuntu** o tu distribución está activada en la lista.
			  5️⃣ Haz clic en **"Apply & Restart"**.
		- Error **`lsb_release: command not found`** significa que el paquete `lsb-release` **no está instalado**  Este comando se usa para mostrar información sobre la versión de Ubuntu.
		- lo instalamos usando el siguiente comando `apt update && apt install -y lsb-release`
		- ==Nota== -->  El comando anterior lo podemos ejecutar en el mismo contenedor ya que es tamos usando Ubuntu,  no obstante hay que tener en cuenta que   los cambios en un contenedor no son permanentes Por defecto, si sales del contenedor (`exit`) y lo vuelves a ejecutar con `docker run`, los cambios **se perderán**.
		-
-