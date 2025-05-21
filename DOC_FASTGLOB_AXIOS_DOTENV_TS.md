# Documentación de Librerías Esenciales para Desarrollo Node.js/TypeScript

Este documento proporciona una visión general y ejemplos de uso de las librerías clave utilizadas en proyectos Node.js/TypeScript, especialmente aquellas que facilitan el desarrollo, la gestión de entornos y la interacción con APIs externas.

---

## 1. `fast-glob`

Una librería extremadamente rápida y eficiente para buscar archivos y directorios utilizando patrones "glob" (como `*.js`, `**/*.ts`, etc.). Es ideal para proyectos donde necesitas leer y listar archivos de forma selectiva.

* **Descripción:** Permite encontrar rutas de archivos y directorios que coinciden con patrones de shell estilo globbing. Es una alternativa optimizada a otras herramientas similares, destacando por su rendimiento.
* **Casos de uso comunes:**
    * Listar todos los archivos fuente (`.ts`, `.js`) en un proyecto.
    * Encontrar archivos de configuración o recursos específicos.
    * Automatizar la construcción de listas de archivos para empaquetadores (bundlers).
* **Instalación:**
    ```bash
    npm install fast-glob
    # o
    yarn add fast-glob
    ```
* **Ejemplo de Uso:**
    ```typescript
    import fg from 'fast-glob';
    import path from 'path';

    async function listarArchivosDeCodigo() {
        // Rutas a buscar (puedes ajustar el directorio base)
        const entrada = ['**/*.ts', '**/*.js', '!node_modules']; // Excluir node_modules

        // Opciones para fast-glob
        const opciones = {
            cwd: process.cwd(), // Directorio actual del proceso
            ignore: ['node_modules/**', '.git/**'], // Ignorar directorios comunes
            onlyFiles: true, // Asegurarse de que solo se devuelvan archivos
            absolute: true, // Devolver rutas absolutas
        };

        try {
            const rutasDeArchivos = await fg(entrada, opciones);
            console.log('Archivos de código encontrados:');
            rutasDeArchivos.forEach(ruta => console.log(path.relative(process.cwd(), ruta)));
        } catch (error) {
            console.error('Error al listar archivos:', error);
        }
    }

    listarArchivosDeCodigo();
    ```
* **Enlaces:**
    * **GitHub/Documentación:** [https://github.com/mrmlnc/fast-glob](https://github.com/mrmlnc/fast-glob)
    * **NPM:** [https://www.npmjs.com/package/fast-glob](https://www.npmjs.com/package/fast-glob)

---

## 2. `axios`

Un cliente HTTP basado en promesas para el navegador y Node.js. Es ampliamente utilizado por su facilidad de uso, flexibilidad y robustez en la gestión de solicitudes HTTP.

* **Descripción:** Permite realizar solicitudes `GET`, `POST`, `PUT`, `DELETE`, etc., a APIs RESTful. Ofrece características como interceptores de solicitudes/respuestas, manejo automático de JSON, cancelación de solicitudes y protección XSRF.
* **Casos de uso comunes:**
    * Interactuar con cualquier API externa (como la API de OpenAI, Ollama, etc.).
    * Consumir servicios web internos en una arquitectura de microservicios.
    * Descargar o subir archivos.
* **Instalación:**
    ```bash
    npm install axios
    # o
    yarn add axios
    ```
* **Ejemplo de Uso (para interactuar con un LLM, por ejemplo, Ollama o OpenAI):**
    ```typescript
    import axios from 'axios';

    async function llamarLLM(prompt: string) {
        const urlOllama = 'http://localhost:11434/api/generate'; // Ejemplo para Ollama
        const urlOpenAI = '[https://api.openai.com/v1/chat/completions](https://api.openai.com/v1/chat/completions)'; // Ejemplo para OpenAI
        const OPENAI_API_KEY = process.env.OPENAI_API_KEY; // Obtenida de .env

        try {
            // Ejemplo con Ollama
            const respuestaOllama = await axios.post(urlOllama, {
                model: 'llama2', // O cualquier modelo que tengas descargado en Ollama
                prompt: prompt,
                stream: false, // Para obtener la respuesta completa de una vez
            });
            console.log('\nRespuesta de Ollama:');
            console.log(respuestaOllama.data.response);

            // Ejemplo con OpenAI (requiere API Key y configuración de headers)
            if (OPENAI_API_KEY) {
                const respuestaOpenAI = await axios.post(urlOpenAI, {
                    model: 'gpt-4o', // O 'gpt-3.5-turbo', etc.
                    messages: [{ role: 'user', content: prompt }],
                }, {
                    headers: {
                        'Authorization': `Bearer ${OPENAI_API_KEY}`,
                        'Content-Type': 'application/json',
                    },
                });
                console.log('\nRespuesta de OpenAI:');
                console.log(respuestaOpenAI.data.choices[0].message.content);
            } else {
                console.warn('OPENAI_API_KEY no está configurada. No se pudo llamar a la API de OpenAI.');
            }

        } catch (error: any) {
            console.error('Error al llamar al LLM:', error.message);
            if (error.response) {
                // El servidor respondió con un estado fuera del rango 2xx
                console.error('Datos del error:', error.response.data);
                console.error('Estado del error:', error.response.status);
            }
        }
    }

    // Uso de la función
    // llamarLLM('Explica brevemente qué es una función asíncrona en JavaScript.');
    ```
* **Enlaces:**
    * **GitHub/Documentación:** [https://github.com/axios/axios](https://github.com/axios/axios)
    * **NPM:** [https://www.npmjs.com/package/axios](https://www.npmjs.com/package/axios)

---

## 3. `dotenv`

Una librería de carga de variables de entorno desde un archivo `.env` en `process.env`. Es esencial para la gestión de configuraciones sensibles.

* **Descripción:** Permite separar los secretos de tu código fuente (como claves API, credenciales de bases de datos, etc.) en un archivo `.env` que no debe ser versionado en tu control de código fuente (añádelo a `.gitignore`).
* **Casos de uso comunes:**
    * Almacenar claves API para servicios externos.
    * Definir URLs de bases de datos o servicios.
    * Gestionar configuraciones específicas de entornos (desarrollo, producción).
* **Instalación:**
    ```bash
    npm install dotenv
    # o
    yarn add dotenv
    ```
* **Ejemplo de Uso:**
    1.  **Crea un archivo `.env` en la raíz de tu proyecto:**
        ```env
        OPENAI_API_KEY=tu_clave_secreta_de_openai
        DB_HOST=localhost
        DB_PORT=5432
        ```
    2.  **Crea un archivo `.gitignore` en la raíz de tu proyecto y añade:**
        ```
        .env
        ```
        Esto asegura que tu archivo `.env` **nunca se suba a tu repositorio de Git.**
    3.  **En tu código (normalmente al inicio de tu archivo principal, por ejemplo, `index.ts` o `app.ts`):**
        ```typescript
        import dotenv from 'dotenv';

        // Carga las variables de entorno del archivo .env
        dotenv.config();

        // Ahora puedes acceder a ellas a través de process.env
        const apiKey = process.env.OPENAI_API_KEY;
        const dbHost = process.env.DB_HOST;

        console.log('API Key:', apiKey ? 'Cargada' : 'No cargada');
        console.log('DB Host:', dbHost);

        if (!apiKey) {
            console.warn('¡Advertencia! La clave de la API de OpenAI no está configurada en .env');
        }
        ```
* **Enlaces:**
    * **GitHub/Documentación:** [https://github.com/motdotla/dotenv](https://github.com/motdotla/dotenv)
    * **NPM:** [https://www.npmjs.com/package/dotenv](https://www.npmjs.com/package/dotenv)

---

## 4. `typescript`

El lenguaje de programación base de este proyecto, que extiende JavaScript añadiendo tipado estático opcional.

* **Descripción:** TypeScript (TS) es un superconjunto de JavaScript que compila a JavaScript. Proporciona características como interfaces, tipos de unión, genéricos y más, lo que mejora la legibilidad, la mantenibilidad y la detección de errores en tiempo de desarrollo.
* **Casos de uso comunes:**
    * Desarrollo de aplicaciones a gran escala que requieren un mantenimiento robusto.
    * Mejorar la colaboración en equipos grandes al imponer contratos de datos claros.
    * Aprovechar el autocompletado y la refactorización en IDEs.
* **Instalación (como dependencia de desarrollo):**
    ```bash
    npm install --save-dev typescript
    # o
    yarn add --dev typescript
    ```
* **Configuración básica (`tsconfig.json`):**
    Para usar TypeScript, necesitas un archivo `tsconfig.json` en la raíz de tu proyecto que configure cómo TypeScript compila tu código.
    ```json
    {
      "compilerOptions": {
        "target": "es2020",         /* Especifica la versión de ECMAScript para el código de salida. */
        "module": "commonjs",       /* Especifica el sistema de módulos para el código de salida. */
        "outDir": "./dist",         /* Redirige la salida a un directorio especificado. */
        "rootDir": "./src",         /* Especifica el directorio raíz de los archivos de entrada. */
        "strict": true,             /* Habilita todas las opciones estrictas de comprobación de tipos. */
        "esModuleInterop": true,    /* Habilita la interoperabilidad entre módulos CommonJS y ES. */
        "skipLibCheck": true,       /* Omite la comprobación de tipos de todos los archivos .d.ts. */
        "forceConsistentCasingInFileNames": true /* Asegura que los nombres de archivo usan siempre el mismo casing en todo el proyecto. */
      },
      "include": [
        "src/**/*.ts"               /* Incluye solo los archivos .ts en el directorio src. */
      ],
      "exclude": [
        "node_modules"              /* Excluye el directorio node_modules. */
      ]
    }
    ```
* **Ejemplo de Uso (en `src/index.ts`):**
    ```typescript
    // src/index.ts
    interface Persona {
        nombre: string;
        edad: number;
        saludar(): string;
    }

    class Usuario implements Persona {
        constructor(public nombre: string, public edad: number) {}

        saludar(): string {
            return `Hola, mi nombre es ${this.nombre} y tengo ${this.edad} años.`;
        }
    }

    const usuario1 = new Usuario('Ana', 30);
    console.log(usuario1.saludar());

    // Ejemplo de tipo para una función
    type OperacionMatematica = (a: number, b: number) => number;

    const sumar: OperacionMatematica = (x, y) => x + y;
    console.log(`2 + 3 = ${sumar(2, 3)}`);
    ```
* **Enlaces:**
    * **Documentación Oficial:** [https://www.typescriptlang.org/docs/](https://www.typescriptlang.org/docs/)
    * **NPM:** [https://www.npmjs.com/package/typescript](https://www.npmjs.com/package/typescript)

---

## 5. `ts-node`

Un ejecutor de TypeScript para Node.js. Permite ejecutar archivos `.ts` directamente sin necesidad de una compilación previa a `.js`.

* **Descripción:** `ts-node` compila automáticamente tus archivos TypeScript en memoria (o en un caché) antes de ejecutarlos con Node.js. Esto es ideal para el desarrollo local, scripts y pruebas, ya que acelera el ciclo de desarrollo al evitar el paso explícito de `tsc`.
* **Casos de uso comunes:**
    * Ejecutar scripts TypeScript directamente sin construir el proyecto.
    * Desarrollo de APIs Node.js con TypeScript con reinicio automático (`nodemon`).
    * Ejecutar archivos de prueba escritos en TypeScript.
* **Instalación (como dependencia de desarrollo):**
    ```bash
    npm install --save-dev ts-node
    # o
    yarn add --dev ts-node
    ```
* **Ejemplo de Uso:**
    Asumiendo que tienes el archivo `src/index.ts` del ejemplo de `typescript`:
    ```bash
    # Ejecutar directamente el archivo TypeScript
    npx ts-node src/index.ts
    ```
    También puedes añadirlo a tu `package.json` en los scripts:
    ```json
    {
      "name": "my-project",
      "version": "1.0.0",
      "scripts": {
        "start": "ts-node src/index.ts",
        "build": "tsc"
      },
      "devDependencies": {
        "typescript": "^5.0.0",
        "ts-node": "^10.0.0"
      }
    }
    ```
    Y luego ejecutarlo con:
    ```bash
    npm start
    # o
    yarn start
    ```
* **Enlaces:**
    * **GitHub/Documentación:** [https://github.com/TypeStrong/ts-node](https://github.com/TypeStrong/ts-node)
    * **NPM:** [https://www.npmjs.com/package/ts-node](https://www.npmjs.com/package/ts-node)

---

## 6. `@types/node`

Colección de definiciones de tipos TypeScript para entornos Node.js.

* **Descripción:** Cuando escribes código TypeScript para Node.js, necesitas definiciones de tipos para las APIs nativas de Node.js (como `fs`, `path`, `http`, `process`, etc.). `@types/node` proporciona estas definiciones, lo que permite a TypeScript verificar tu código y a tu IDE ofrecer autocompletado y validación de tipos para las funciones de Node.js.
* **Casos de uso comunes:**
    * Cualquier proyecto Node.js que use TypeScript.
    * Asegurar la seguridad de tipos al interactuar con el sistema de archivos, variables de entorno, etc.
* **Instalación (como dependencia de desarrollo):**
    ```bash
    npm install --save-dev @types/node
    # o
    yarn add --dev @types/node
    ```
* **Ejemplo de Uso:**
    No se usa directamente en el código, sino que TypeScript lo consume automáticamente para proporcionar la información de tipos.
    ```typescript
    import fs from 'fs'; // 'fs' es un módulo nativo de Node.js

    // TypeScript sabe que 'path' es una cadena gracias a @types/node
    const filePath: string = './miarchivo.txt';

    fs.promises.readFile(filePath, 'utf-8')
        .then((data: string) => { // TypeScript sabe que 'data' será una cadena
            console.log('Contenido del archivo:', data);
        })
        .catch((err: NodeJS.ErrnoException) => { // TypeScript sabe el tipo de error
            console.error('Error al leer el archivo:', err.message);
        });

    // Acceso a variables de entorno (gracias a @types/node para process)
    const envVar = process.env.MI_VARIABLE_DE_ENTORNO;
    console.log('MI_VARIABLE_DE_ENTORNO:', envVar);
    ```
* **Enlaces:**
    * **GitHub:** [https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/node](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types/node)
    * **NPM:** [https://www.npmjs.com/package/@types/node](https://www.npmjs.com/package/@types/node)
