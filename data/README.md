# Datos

El dataset es **UCI Wall-Following Robot Navigation Data**, versión de 4 atributos:
<https://archive.ics.uci.edu/dataset/194/wall+following+robot+navigation+data>

Falta copiar aquí el archivo **`sensor_readings_4.data`** (5456 filas; pesa menos de 1 MB):

1. Descarga el zip del conjunto desde la página de UCI (botón Download).
2. Extrae `sensor_readings_4.data` y guárdalo en esta carpeta (`data/`).
3. Sube el archivo al repositorio junto con el notebook: la docente pide el dataset en el repositorio (o su enlace si fuera muy grande).

El notebook también intenta descargarlo solo si no lo encuentra; esa descarga automática no se probó desde el entorno donde se preparó el repositorio, así que conviene dejar el archivo ya guardado aquí.

## Columnas

El archivo no es un CSV con encabezado: cada línea tiene 4 lecturas y la clase, separadas por comas. El notebook les pone estos nombres:

| Columna | Significado |
| --- | --- |
| `SD_front` | Lectura mínima en un arco de 60° al frente del robot |
| `SD_left` | Lectura mínima en un arco de 60° a la izquierda |
| `SD_right` | Lectura mínima en un arco de 60° a la derecha |
| `SD_back` | Lectura mínima en un arco de 60° detrás del robot |
| `Class` | Acción del robot: `Move-Forward`, `Slight-Right-Turn`, `Sharp-Right-Turn` o `Slight-Left-Turn` |
