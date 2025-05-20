# 📃 Guía Completa para Aprender a Usar AIChat y sus Herramientas
- Esta guía está pensada para principiantes, especialmente si:
  > - Estás usando Ubuntu dentro de WSL en Windows.
  > - No sabes programación ni informática.
  > - Quieres entender QUÉ es AIChat, CÓMO funciona y PARA QUÉ sirve cada cosa.
  
  ---
- ## ✈️ 1. ¿Qué es AIChat?
  
  AIChat es una **herramienta de línea de comandos (CLI)** que te permite interactuar con modelos de lenguaje como ChatGPT, Claude, LLaMA, etc., desde tu terminal.
- ### 🤔 ¿Para qué sirve?
  
  Puedes usarlo para:
- Hacer preguntas como si chatearas con una IA.
- Ejecutar funciones, leer archivos, escribir, etc.
- Automatizar tareas repetitivas con lenguaje natural.
- Trabajar con "roles" que definen comportamientos personalizados.
  
  ---
- ## ⚙️ 2. Instalación de AIChat y Entorno
	- ## Manual Completo de Instalación, Configuración y Uso de aichat y llm-functions
	- ### 1. Requisitos Previos
	- **WSL con Ubuntu 20.04:** (Ya configurado)
	- **Rust y Cargo:** Necesarios para compilar ambas herramientas.
		- Instalación:
		  ```Bash
		          curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
		          source "$HOME/.cargo/env"
		  ```
	- **argc:** Marco de línea de comandos Bash.
		- sudo apt update
		          sudo apt install -y argc
	- **jq:** Procesador JSON.
		- Instalación:
		  
		  ```Bash
		          sudo apt install -y jq
		  ```
	- ### 2. Instalación de aichat
	- Clonar el repositorio:
	  
	  ```Bash
	          git clone https://github.com/sigoden/aichat.git
	          cd aichat
	  ```
	- Compilar e instalar:
	  
	  
	  Bash
	  
	  
	  ```
	          cargo install --path .
	  ```
	- Verificar la instalación:
	  
	  ```Bash
	          aichat --version
	  ```
	- ### 3. Configuración Inicial de aichat
	- Crear el directorio de configuración:
	  
	  ```Bash
	          mkdir -p ~/.config/aichat/
	  ```
	- Copiar el archivo de configuración de ejemplo y editarlo:
	  
	  ```Bash
	          cp config.example.yaml ~/.config/aichat/config.yaml
	          nano ~/.config/aichat/config.yaml
	  ```
	- Añadir las claves API de los proveedores de modelos de lenguaje (OpenAI, Google Gemini, etc.):
	  
	  ```YAML
	          providers:
	          openai:
	            api_key: "tu_clave_api_openai"
	          google_gemini:
	            api_key: "tu_clave_api_google_gemini"
	          # Añade otros proveedores según sea necesario
	  ```
	- ### 4. Instalación de llm-functions
	- Clonar el repositorio:
	  ¡
	  
	  ```Bash
	          git clone https://github.com/sigoden/llm-functions.git
	          cd llm-functions
	  ```
	  
	  <!----><!----><!---->
	  
	  <!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!----><!---->
	- Compilar e instalar:
	  <!----><!----><!----><!----><!----><!----><!----><!----><!----><!---->
	  
	  Bash
	  
	  <!----><!----><!---->
	  
	  <!---->
	  
	  <!---->
	  
	  ```
	          cargo install --path .
	  ```
	- Verificar la instalación:
	  
	  ```Bash
	          llm-fn --version
	  ```
	- ### 5. Integración de llm-functions con aichat
	- llm-functions se usa para definir funciones que los agentes de aichat pueden usar.
	- Para integrarlo, se debe definir las funciones en archivos YAML y configurarlas en los archivos de configuración de los agentes en aichat.
	- ### 6. Uso de Roles y Agentes
	- #### Roles
	- Definen el comportamiento del modelo.
		- Ejemplo: Rol de traductor:
			- Crear `~/.config/aichat/roles/translator.yaml`:
			  ```YAML
			          name: translator
			          prompt: "Actúa como un traductor experto. Traduce el texto al idioma especificado."
			  ```
	- Uso:
	  
	  ```Bash
	          aichat -r translator "Traduce 'Hola mundo' al inglés."
	  ```
	- #### Agentes
	- Roles avanzados con funciones externas.
		- Ejemplo: Agente de búsqueda web:
			- Definir la función en `search.yaml`:
			  
			  ```YAML
			          name: search_web
			          description: "Busca información en la web."
			          parameters:
			          query:
			          type: string
			          description: "La consulta de búsqueda."
			  ```
	- Crear `web_researcher.yaml`:
	  
	  ```YAML
	          name: web_researcher
	          prompt: "Eres un investigador web. Usa search_web para buscar información."
	          functions:
	          - search_web
	  ```
	- Configurar aichat para que el agente pueda usar la funcion en el config.yaml principal, en la sección de agents.
	- Uso:
	  ```Bash
	          aichat -a web_researcher "Busca la población de Tokio."
	  ```
	- ### 7. Glosario
	- `aichat`: CLI para interactuar con modelos de lenguaje.
	- `llm-functions`: CLI para definir funciones para agentes.
	- `cargo`: Gestor de paquetes de Rust.
	- `WSL`: Subsistema de Windows para Linux.
	- `API key`: Clave de autenticación para modelos de lenguaje.
	- `config.yaml`: Archivo de configuración principal de aichat.
	- `roles`: Definiciones de comportamiento del modelo.
	- `agents`: Roles avanzados con funciones externas.
	- `prompt`: Instrucción al modelo.
	- `function`: Herramienta para agentes.
	- `argc`: Herramienta para crear interfaces de línea de comandos.
	- `jq`: Procesador de archivos JSON.
	- `git clone`: Comando de Git para copiar un repositorio. Ejemplo: `git clone https://github.com/sigoden/aichat.git`
	- `cd`: Comando para cambiar de directorio. Ejemplo: `cd aichat`
	- `cargo install --path .`: Comando de Cargo para instalar un paquete desde el directorio actual.
	- `aichat --version`: Comando para verificar la versión instalada de aichat.
	- `mkdir -p`: Comando para crear directorios, incluso si los directorios padres no existen. Ejemplo: `mkdir -p ~/.config/aichat/`
	- `cp`: Comando para copiar archivos. Ejemplo: `cp config.example.yaml ~/.config/aichat/config.yaml`
	- `nano`: Editor de texto en línea de comandos. Ejemplo: `nano ~/.config/aichat/config.yaml`
	- `sudo apt update`: Comando para actualizar la lista de paquetes disponibles en Ubuntu.
	- `sudo apt install -y`: Comando para instalar paquetes en Ubuntu sin pedir confirmación. Ejemplo: `sudo apt install -y argc`
	- `llm-fn --version`: Comando para verificar la versión de llm-functions.
		- `aichat -r`: Comando aichat para usar un rol. Ejemplo: `aichat -r translator "Traduce..."`
			- `aichat -a`: Comando aichat para usar un agente. Ejemplo: `aichat -a web_researcher "Busca..."`
-