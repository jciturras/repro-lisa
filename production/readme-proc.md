# README

---
## Procesamiento

**Dependencias**

Para ejecutar las rutinas de debe tener claridad de las dependencias de cada procedimiento. A continuación se detalla esta información

`proc_preparacion.Rmd`:


* Depende del archivo `ELSOC_W01_v4.01_R.RData` ubicado en la carpeta `input/data/original`.
* Resultado: genera la base de datos `datos_proc.RData`, la cual es guardada en `input/data/proc`.

`proc_analisis.Rmd`:

* Depende del archivo `datos_proc.RData` ubicado en `input/data/proc`.
* Resultado: genera figuras y tablas que son guardadas en `output/imagenes` y `output/tablas`, respectivamente.

  - **Descriptivos**:
    - `tabla01.xls`: Tabla resumen de descriptivos
    - `tabla02.xls`: Tabla contingencia educación y sexo
    - `figura01.png`: Figura de boxplots estatus social subjetivo por educación
    - `figura02.png`: Figura de matriz correlación estatus social subjetivo y edad
  - **Prueba hipótesis**
    - `tabla03.xls`: Tabla modelos regresión estatus social subjetivo
  - **Análisis exploratorio y/o secundario**
    - `tabla04.xls`: Tabla modelo regresión incluye variable ingreso
