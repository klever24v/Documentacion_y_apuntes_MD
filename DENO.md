# Instalación y configuración
	- instalar DENO `npm install -g deno`
	- comprobar versión  `deno --version`
	- se pude usar la extensión de Deno o la extensión de una librería y esta la descarga automáticamente
	- ahora  creamos el `index.js` principal
		- ```Codigo  
		  		console.log("✅ Server running on http://localhost:8000");
		          Deno.serve({
		            port: 8000,
		          }, (_req) => {
		            return new Response("Hello World");
		          });
		  ```ç
	- Antes de ejecutar tenemos que tener en cuenta que deno tiene permisos
		- ### 📌 **Principales permisos en Deno**
		  collapsed:: true
			- | Permiso | Descripción |
			  | ------ |
			  | `allow-net`   | Permite realizar **peticiones HTTP** y abrir servidores. |
			  | `--allow-env` | Permite acceder a **variables de entorno** (`Deno.env.get("HOME")`). |
			  | `--allow-ffi` | Permite usar **FFI (Foreign Function Interface)** para interactuar con librerías compiladas (`.so`, `.dll`). |
			  | `--allow-hrtime` | Permite acceder a **alta resolución de tiempo** (`Deno.performance.now()`). |
			  | `--allow-read` | Permite **leer archivos y directorios** en el sistema (`Deno.readTextFile("file.txt")`). |
			  | `--allow-run` | Permite ejecutar **comandos del sistema** (`Deno.run({ cmd: ["ls"] })`). |
	- ejecutamos como prueba `deno run index.js` de esta forma nos sale un mensaje para darle todos los permisos o podemos usar el siguiente comando  `deno run --allow-net index.js `
	- si queremos que deno nos formatee el código usamos `deno fmt index.js`
	- hacer ejecutable `deno index.js`
-
-
-
- README
	- Programa basico con DENO y uso de las erramientas predefinidas para DENO
	- Deno no hace falta importarlo tras hacer el instalar DENO `npm install -g deno`  ya funciona sin ningun import
-