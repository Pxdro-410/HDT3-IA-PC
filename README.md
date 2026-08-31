# HDT3-IA-PC

Hoja de trabajo #3 - Sistemas RAG AI engineering

### Autor: Pedro Caso -241286

- Enlace del video: https://youtu.be/R2Bv2DOvZVQ

## Descripción

Agente de preguntas frecuentes (FAQs) para Parachute S.A., una empresa de
paracaidismo que solicitó un demo de un agente conversacional en terminal.
El agente responde preguntas del usuario basándose únicamente en el contenido
de un archivo de texto con las FAQs del evento que la empresa proporcionó.

El proyecto implementa la arquitectura RAG más simple posible: el archivo de
texto se lee del sistema de archivos al iniciar el programa y se inyecta
completo dentro del system prompt del modelo. No se usan embeddings ni bases
de datos vectoriales.

## Requisitos

- Python 3.11 o superior
- Una API key de [Nvidia Build](https://build.nvidia.com/) (tier gratuito)

## Estructura del proyecto

```
HDT3-IA-PC/
├── agent.py                                   Punto de entrada del agente (CLI)
├── data/
│   └── FAQs_Parachute_SA_Guatemala_2026.txt    Archivo de FAQs proporcionado por Parachute S.A.
├── requirements.txt                            Dependencias del proyecto
├── .env.example                                Plantilla de variables de entorno
└── .env                                        Variables de entorno reales 
```

## Instalación

1. Clonar el repositorio y ubicarse en la carpeta del proyecto.

2. Crear y activar un entorno virtual.

   En PowerShell (Windows):
   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

   En bash (Linux/Mac):
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```

3. Instalar las dependencias:
   ```
   pip install -r requirements.txt
   ```

4. Crear el archivo `.env` a partir de la plantilla y completar los valores:
   ```
   cp .env.example .env
   ```

   Variables requeridas en `.env`:

   | Variable          | Descripción                                            |
   |-------------------|---------------------------------------------------------|
   | NVIDIA_API_KEY    | API key personal de Nvidia Build                        |
   | NVIDIA_BASE_URL   | Endpoint compatible con la API de OpenAI (Nvidia Build)  |
   | NVIDIA_MODEL      | Identificador del modelo a utilizar                      |


## Uso

Con el entorno virtual activado, ejecutar:
```
python agent.py
```

El agente inicia una sesión interactiva en la terminal donde se pueden hacer
múltiples preguntas de forma consecutiva. Para finalizar la sesión:

- Escribir la palabra `Bye`, o
- Presionar `Ctrl-C`

Si la pregunta realizada no puede responderse con la información contenida en
el archivo de FAQs, el agente lo indicará explícitamente en lugar de inventar
una respuesta.

## Notas de seguridad

No se pusheó ninguna API key al repositorio. El archivo `.env` está
ignorado por git mediante el `.gitignore`; únicamente se provee el `.env.example` (sin valores reales) en el control de versiones.
