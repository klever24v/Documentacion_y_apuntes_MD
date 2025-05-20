- Comandos Linux básicos
	- # 🚀 Comandos Básicos de Linux
	  Lista de comandos básicos organizados por categorías para facilitar su aprendizaje. 📌
	  ---
	- ## **1️⃣ Comandos Relacionados con Usuarios y Grupos 🧑**
	- ### 📀 Información del Usuario
	  
	  ```
	       	whoami      # Muestra el usuario actual
	  		id          # Muestra el UID, GID y grupos del usuario
	  		who         # Muestra qué usuarios están conectados al sistema
	  		w           # Muestra información detallada de usuarios conectados
	  		last        # Muestra el historial de inicios de sesión
	  ```
	- ### 📀 Gestión de Usuarios
	  
	  ```
	  		adduser usuario          # Crea un nuevo usuario
	  		userdel usuario          # Elimina un usuario
	  		usermod -aG grupo usuario # Añade un usuario a un grupo
	  		passwd usuario           # Cambia la contraseña de un usuario
	  ```
	- ### 📀 Gestión de Grupos
	  
	  ```
	  		groupadd grupo     # Crea un nuevo grupo
	  		groupdel grupo     # Elimina un grupo
	  		groups usuario     # Muestra los grupos a los que pertenece un usuario
	  ```
	- ### 📀 Permisos y Propiedades
	  
	  ```
	  chmod 755 archivo            # Cambia permisos de un archivo o directorio
	  chown usuario:grupo archivo  # Cambia el propietario de un archivo
	  ```
	  
	  ---
	- ## **2️⃣ Comandos Relacionados con Directorios 📂**
	  
	  ```
	  		pwd       # Muestra la ruta del directorio actual
	  		ls        # Lista archivos y directorios
	  		ls -la    # Lista archivos con detalles y archivos ocultos
	  		cd dir    # Cambia de directorio
	  		cd ..     # Sube un nivel en la jerarquía de directorios
	  		mkdir dir # Crea un nuevo directorio
	  		rmdir dir # Elimina un directorio vacío
	  		rm -r dir # Elimina un directorio y su contenido
	  ```
	  
	  ---
	- ## **3️⃣ Comandos Relacionados con Ficheros 📝**
	  
	  ```
	  		touch archivo     # Crea un archivo vacío
	  		cat archivo       # Muestra el contenido de un archivo
	  		less archivo      # Muestra el contenido de un archivo con paginación
	  		nano archivo      # Edita un archivo con el editor Nano
	  		vim archivo       # Edita un archivo con el editor Vim
	  		cp archivo destino # Copia un archivo a otra ubicación
	  		mv archivo destino # Mueve o renombra un archivo
	  		rm archivo        # Elimina un archivo
	  		stat archivo      # Muestra detalles de un archivo (fecha, permisos, tamaño)
	  ```
	  
	  ---
	- ## **4️⃣ Comandos Ú tiles e Interesantes 🛠️**
	- ### 📀 Información del Sistema
	  
	  ```
	  		uname -a   # Muestra información del sistema
	  		df -h      # Muestra el espacio libre en disco
	  		free -h    # Muestra el uso de memoria RAM
	  		uptime     # Muestra el tiempo que lleva encendido el sistema
	  		top        # Muestra procesos en ejecución
	  		htop       # Alternativa más visual a 'top' (requiere instalación)
	  ```
	- ### 📀 Red y Conectividad
	  
	  ```
	  		ip a         # Muestra las interfaces de red y sus IPs
	  		ping google.com  # Verifica la conectividad con un host
	  		wget URL     # Descarga un archivo de una URL
	  		curl -I URL  # Muestra la cabecera HTTP de una URL
	  ```
	- ### 📀 Administración de Procesos
	  
	  ```
	  		ps aux         # Muestra los procesos en ejecución
	  		kill PID       # Mata un proceso por su ID
	  		killall proceso # Mata todos los procesos con un nombre específico
	  		jobs           # Muestra los procesos en segundo plano
	  		bg             # Reanuda un proceso en segundo plano
	  		fg             # Trae un proceso al primer plano
	  ```
	  
	  ---