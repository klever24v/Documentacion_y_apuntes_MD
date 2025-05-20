
# Guía de generación automática de documentación del código con ChatOpenAI

## Descripción general del proyecto

Este proyecto tiene como objetivo automatizar la creación de documentación técnica en formato Markdown analizando el código fuente de un proyecto utilizando un modelo de lenguaje grande (LLM). En concreto, se emplea el modelo **ChatOpenAI** de OpenAI, integrado con la biblioteca LangChain, para leer el código (por ejemplo, archivos `.py`, `.js`, `.java`, etc.) y producir un resumen explicativo en Markdown. La idea es ahorrar tiempo en la elaboración manual de documentación, ayudando incluso a quienes se i...

## Requisitos y librerías utilizadas

- **Python 3.10+**
- **LangChain**: Framework para conectar LLMs con fuentes de datos y herramientas externas.
- **langchain-openai** / **langchain-community**: Submódulos de LangChain recomendados por su mantenimiento y actualizaciones.
- **dotenv**: Para cargar las variables de entorno desde un archivo `.env`.
- **openai**: Cliente oficial para acceder a modelos de OpenAI.

## Problemas encontrados durante el desarrollo

1. **Python no reconocido por PowerShell**: El sistema no tenía Python agregado al `PATH`. Se resolvió agregándolo manualmente.
2. **Permisos denegados al modificar variables de entorno a nivel de máquina**: Se intentó modificar el `PATH` desde PowerShell sin permisos de administrador.
3. **Falta de `requirements.txt`**: No había una lista de dependencias definida. Se optó por instalar manualmente los paquetes requeridos.
4. **Problemas con `langchain.chat_models.ChatOpenAI`**: Esta clase fue deprecada. Se migró a `langchain_community.chat_models` o `langchain_openai.ChatOpenAI`.
5. **Error por falta de clave API**: El sistema requería la variable de entorno `OPENAI_API_KEY`, la cual se colocó en el archivo `.env`.
6. **Ruta mal escrita (escape sequences)**: Las rutas con `\` causaban advertencias (`SyntaxWarning`). Se corrigió usando `r"ruta"` o `/`.
7. **No se encontraba código Python**: El script inicialmente solo leía archivos `.py`. Se amplió para incluir múltiples lenguajes como `.js`, `.java`, etc.

## Cómo funciona el script

1. **Lee todos los archivos de código dentro de un directorio** (y subdirectorios) cuyo nombre o extensión coincida con una lista de extensiones comunes (`.py`, `.js`, `.java`, `.ts`, `.cpp`, etc.).
2. **Genera un prompt largo** con todo el código concatenado, enviado al modelo LLM (por defecto `gpt-3.5-turbo` o `gpt-4`).
3. **El modelo devuelve una descripción estructurada en Markdown** con explicaciones sobre la estructura del proyecto, funciones clave, módulos, etc.
4. **Se guarda un archivo Markdown** en la carpeta `documentacion_generada` con la documentación generada.

## Cómo probarlo paso a paso

1. Clonar el repositorio o copiar los scripts a un nuevo proyecto.
2. Crear un entorno virtual: `python -m venv env`
3. Activar el entorno: `.\env\Scriptsctivate` en Windows.
4. Instalar dependencias necesarias: `pip install langchain langchain-openai python-dotenv openai`
5. Crear un archivo `.env` con:
    ```env
    OPENAI_API_KEY=tu_clave_api
    MODEL=gpt-4
    TEMPERATURE=0.2
    DEBUG=True
    PROJECT_NAME=mcp_code_documenter
    ```
6. Colocar el código fuente a documentar dentro de una carpeta (por ejemplo, `D:/proyecto-ejemplo`).
7. Ejecutar el script con `python main.py` (ajustando la ruta dentro del código a tu proyecto).
8. Ver la documentación generada dentro de `documentacion_generada/`.

## Conclusión

Este proyecto demuestra cómo puede utilizarse un LLM como ChatGPT para analizar el código de un proyecto completo y generar documentación automáticamente. Aunque requiere una clave de API válida, la herramienta puede ser adaptada para otros modelos o flujos personalizados. Fue una buena demostración de uso práctico de modelos de lenguaje en tareas de desarrollo de software.

---

*Esta guía explica de forma detallada cómo configurar y usar el script de análisis de código con un modelo LLM, abarcando desde la instalación de librerías hasta la resolución de problemas comunes. Ha sido redactada pensando en quien se inicia en programación e inteligencia artificial.*
