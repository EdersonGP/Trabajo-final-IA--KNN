# Proyecto final IA (IS-484): KNN para la navegación de un robot

Trabajo final de laboratorio de Inteligencia Artificial I (IS-484), Escuela Profesional de Ingeniería de Sistemas, 2026-II.
Docente: Ing. Leidy Rosmery Maldonado Chauca.

**Integrantes:** COMPLETAR nombre 1 (@usuario-github) · COMPLETAR nombre 2 (@usuario-github)

## Problema

Un robot móvil debe decidir qué movimiento hacer en cada instante para seguir una pared sin chocar.
Se plantea como **clasificación multiclase**: dadas 4 distancias medidas por sus sensores, predecir la acción del robot.

- **Entrada:** `SD_front`, `SD_left`, `SD_right`, `SD_back` (lectura mínima en un arco de 60° al frente, a la izquierda, a la derecha y detrás del robot).
- **Salida:** `Class`, una de 4 acciones: `Move-Forward`, `Slight-Right-Turn`, `Sharp-Right-Turn`, `Slight-Left-Turn`.

## Dataset

[UCI Wall-Following Robot Navigation Data](https://archive.ics.uci.edu/dataset/194/wall+following+robot+navigation+data),
archivo `sensor_readings_4.data` (versión de 4 atributos), guardado en `data/`.

| Requisito de la docente | Dato del dataset |
| --- | --- |
| Dataset público | UCI, donado en 2010 |
| Mínimo 500 filas | 5456 filas |
| Clase menos frecuente con al menos 50 casos | 328 casos (6,01 %) |

Las clases están desbalanceadas (la más frecuente pesa 40,41 % y la menos frecuente 6,01 %), por eso la división es estratificada y se reporta **F1 macro** además de la accuracy.

## Algoritmo

**KNN (K vecinos más cercanos).** Guarda los ejemplos de entrenamiento y clasifica una lectura nueva con el voto de las K lecturas más cercanas,
medidas con la distancia euclidiana sobre las 4 variables estandarizadas. K se ajusta con validación cruzada de 5 particiones (F1 macro).

**Segundo algoritmo para la comparación:** árbol de decisión, con `max_depth` ajustado con la misma validación cruzada y las mismas métricas.

### Cálculo a mano

El notebook (sección 3) desarrolla a mano KNN con 9 filas de entrenamiento y 1 lectura nueva: media y desviación, estandarización,
distancias euclidianas y votación con K = 1, 3 y 5; después lo comprueba con NumPy y scikit-learn.
Posiciones de las 10 filas en el dataset: COMPLETAR (semilla: COMPLETAR).

## Resultados

COMPLETAR con los números de la sección 6 del notebook ejecutado:

| Modelo | Parámetro elegido | F1 macro (CV) | Accuracy (prueba) | F1 macro (prueba) |
| --- | --- | --- | --- | --- |
| KNN | K = COMPLETAR | COMPLETAR | COMPLETAR | COMPLETAR |
| Árbol de decisión | max_depth = COMPLETAR | COMPLETAR | COMPLETAR | COMPLETAR |

## Conclusión

COMPLETAR: qué modelo elegirían y por qué, con los números de arriba (F1 macro, desempeño en la clase menos frecuente, estabilidad y costo de decidir).

## Cómo ejecutar

```bash
python -m venv venv_ia1
# Windows (PowerShell): .\venv_ia1\Scripts\Activate.ps1
# Linux o macOS:        source venv_ia1/bin/activate
pip install -r requirements.txt
jupyter notebook notebooks/Proyecto_KNN_Robot.ipynb
```

Después, en Jupyter: Kernel → Restart & Run All.

## Estructura del repositorio

```
├─ README.md
├─ CHECKLIST.md
├─ requirements.txt
├─ data/
│  └─ sensor_readings_4.data
├─ notebooks/
│  └─ Proyecto_KNN_Robot.ipynb
└─ slides/
```

## Referencias

- Freire, A., Veloso, M. y Barreto, G. (2010). Wall-Following Robot Navigation Data. UCI Machine Learning Repository. <https://archive.ics.uci.edu/dataset/194/wall+following+robot+navigation+data>
- Guías de laboratorio 1 a 8 de IS-484 (KNN en la guía 7, árbol de decisión en la guía 8).
