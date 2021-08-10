# README: repro-lisa

---
## I. Estructura y contenido del proyecto reproducible

El presente proyecto sigue las directrices del Protocolo IPO ([Castillo, 2020](https://juancarloscastillo.github.io/ipo/index_es.html)). La documentación proporcionada aquí consiste en una jerarquía de carpetas y archivos electrónicos organizados como se muestra a continuación:

```
repro-lisa/ (la carpeta principal del proyecto)
│
│   readme.md (documento en el nivel principal con la descripción del proyecto)
│   paper.Rmd (publicación en formato R Markdown)
│   paper.pdf (publicación en formato pdf)
│   paper.html (publicación en formato html)
│   repro-lisa.Rproj (archivo R project)
│
├───input: (archivos de datos y utilidades)
│   │   readme-input.md (documento que describe el contenido de Input)
│   │
│   ├───bib (subcarpeta  de input con documentos de bibliografía)
│   │       referencias.bib
│   │       apa6.csl
│   │
│   ├───data (subcarpeta de input con datos originales y procesados, junto con documentación)
│   │   ├───original (datos originales del estudio)
│   │   │   │   ELSOC_W01_v4.01_R.RData
│   │   │   └───documentacion (documentación de datos originales)
│   │   │                   codebook_W01_S2016_ESP.pdf
│   │   │                   Questionnaire_W01_S2016_ESP.pdf
│   │   │                   User_Manual_ELSOC_Wave_01.pdf        
│   │   │
│   │   └───proc
│   │       │   datos_proc.RData
│   │       └───documentacion (documentación de datos procesados)
│   │                       codebook_datos_proc.pdf
│   │
│   ├───images (subcarpeta de input con imágenes externas)
│   │       logo-elsoc.png
│   │
│   └───prereg (subcarpeta de input con documentación para preregistro)
│           preregistro.pdf
│
├───procesamiento: (rutinas de código de preparación y análisis de datos)
│       readme-proc.md (documento que describe el contenido de Procesamiento)
│       proc_analisis.Rmd
│       proc_preparacion.Rmd
│
└───output: (resultados de análisis en figuras y tablas)  
    ├───imagenes (subcarpeta de output para guardar figuras)
    │       figura01.png
    │       figura02.png
    │
    └───tablas (subcarpeta de output para guardar tablas)
            tabla01.xls
            tabla02.xls
            tabla03.xls                
            tabla04.xls                        
```
## II. Instrucciones y rutinas de ejecución de resultados

Para la ejecución de las rutinas de código del proyecto es necesario tener acceso a una computadora con una copia de R instalada. (Las rutinas de código fueron programadas usando **`R`** versión 4.0.2 (2020-06-22) -- "Taking Off Again").

Los pasos a seguir para reproducir los resultados son los siguientes:

1. Copiar la carpeta y todo su contenido en la computadora que se empleará. No se debe modificar el orden y jerarquía de ninguna carpeta o archivo.
2. Iniciar **`R`**
3.  Fijar el directorio de trabajo en el nivel principal de la carpeta usando en consola el comando `setwd("user/carpeta/repro-lisa")`.
4. Abrir el archivo `proc_preparacion.Rmd` y correr el código desde la consola usando el comando `rmarkdown::render(input = "proc_preparacion.Rmd")`. **proc_preparacion.Rmd** realizará:

     - Cargar los datos del archivo de datos original `ELSOC_W01_v4.01_R.RData` (que está almacenado en la carpeta `input/data/original`).

    - Procesar los datos como sea necesario para crear el archivo de datos de análisis que se utilizará para generar los resultados.

     - Guardar los datos procesados para análisis en un archivo llamado `datos_proc.RData`, almacenado en la carpeta `input/data/proc`.  (Si una versión previamente generada de estos `datos_proc.RData` ya se encuentra almacenada en la carpeta `input/data/proc`, cuando se ejecute `proc_preparacion.Rmd` será sobrescrita).


5. Abrir el archivo `proc_analisis.Rmd` y correr el código desde la consola usando el comando `rmarkdown::render(input = "proc_analisis.Rmd")`. **proc_analisis.Rmd** realizará:

   - Cargar los datos del archivo de datos procesados para análisis `datos_proc.RData` (que fue creado y guardado en la carpeta `input/data/proc` ejecutó `proc_preparacion.Rmd`).
    - Generar figuras y tablas incluidas en la publicación. Cada figura visualiza los resultados descriptivos y modelos, serán guardadas en la carpeta `output/imagenes`. Las tablas representan resultados descriptivos y modelos, serán guardadas en la carpeta `output/tablas` (Si existen versiones previamente generadas de las figuras o tablas que ya se encuentran almacenadas en la carpetas `output/imagenes` o `output/imagenes`, cuando se ejecute `proc_analisis.Rmd`, éstas serán sobrescritas).
