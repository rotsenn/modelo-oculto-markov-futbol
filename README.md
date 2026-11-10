# Análisis de fases tácticas del fútbol mediante un Modelo Oculto de Markov discreto y experimentación Monte Carlo

## Descripción del proyecto

Este proyecto implementa un Modelo Oculto de Markov (HMM) discreto para analizar las fases tácticas de un equipo de fútbol mediante secuencias de observaciones simuladas.

Se utiliza el algoritmo de Viterbi para reconstruir la secuencia de estados ocultos y se realizan experimentos Monte Carlo para evaluar el comportamiento del modelo bajo diferentes escenarios y condiciones.

El proyecto utiliza partidos sintéticos de 90 minutos. Por tanto, los resultados corresponden a simulaciones y no a datos reales de encuentros de fútbol.

## Objetivos

- Implementar un Modelo Oculto de Markov discreto.
- Simular secuencias de estados y observaciones relacionadas con las fases tácticas del fútbol.
- Aplicar el algoritmo de Viterbi para reconstruir los estados ocultos.
- Evaluar el desempeño del modelo mediante métricas y matrices de confusión.
- Analizar diferentes escenarios mediante experimentación Monte Carlo.
- Evaluar la reproducibilidad y sensibilidad de los resultados.

## Modelo implementado

El modelo contempla tres estados ocultos:

| Estado | Fase táctica |
|---|---|
| S0 | Defensiva |
| S1 | Transición |
| S2 | Ataque |

Y tres tipos de observaciones:

| Observación | Acción |
|---|---|
| O0 | Pase corto |
| O1 | Pase largo |
| O2 | Tiro a puerta |

El HMM se representa mediante:

\[
\lambda=(S,V,A,B,\pi)
\]

Donde se definen los estados, las observaciones, la matriz de transición, la matriz de emisión y la distribución inicial.

## Estructura del notebook

El archivo `experimento_hmm_futbol.ipynb` contiene el desarrollo completo del proyecto.

**Importante:** para reproducir el experimento desde cero, se deben ejecutar todas las etapas, desde la Etapa 2 hasta la Etapa 6, respetando el orden de las celdas. No se deben omitir etapas, ya que algunas variables, funciones y resultados se utilizan en las etapas posteriores.

### Etapa 2. Configuración y simulación del modelo

Se establecen los parámetros del HMM, las matrices de transición y emisión, la distribución inicial y las condiciones para simular los partidos.

### Etapa 3. Generación de secuencias

Se generan las secuencias sintéticas de estados ocultos, observaciones y posesión del balón durante los 90 minutos.

### Etapa 4. Algoritmo de Viterbi

Se implementa el algoritmo de Viterbi utilizando log-probabilidades para reconstruir la secuencia más probable de estados ocultos a partir de las observaciones.

### Etapa 5. Evaluación y visualización de resultados

Esta etapa contiene dos bloques de código de visualización en el notebook.

**Primer bloque: generación de las cinco gráficas principales**

Genera una carpeta denominada `resultados_etapa5` con los siguientes archivos PNG:

| Archivo | Descripción |
|---|---|
| `01_linea_tiempo_fases.png` | Línea de tiempo de las fases tácticas. |
| `02_acciones_observadas.png` | Distribución de las acciones observadas. |
| `03_evolucion_posesion.png` | Evolución de la posesión del balón. |
| `04_matriz_confusion.png` | Matriz de confusión del modelo. |
| `05_comparacion_tiempo_fases.png` | Comparación del tiempo por fase táctica. |

### Etapa 6. Experimentación Monte Carlo

Se realizan experimentos para evaluar el comportamiento del HMM bajo diferentes escenarios, utilizando simulaciones repetidas y métricas estadísticas.

Se generan dos gráficas iniciales:

- `01_exactitud_por_escenario.png`
- `02_tiempo_fases_por_escenario.png`

También se generan los archivos CSV con los resultados de los experimentos.

### Bloque final de visualización de la Etapa 6

Después de la Etapa 6 existe una última celda de código que está identificada como Etapa 5 en el notebook.

Aunque conserva esa denominación, su función es generar nuevamente las dos gráficas de comparación correspondientes a los resultados de la Etapa 6, utilizando una numeración consecutiva.

Estas imágenes se guardan en `resultados_etapa6`:

- `06_exactitud_por_escenario.png`
- `07_tiempo_fases_por_escenario.png`

Este bloque también genera los **10 archivos CSV** correspondientes a los resultados de la experimentación Monte Carlo.

Por tanto, se recomienda ejecutar esta última celda después de completar la Etapa 6.

## Resultados generados

Al ejecutar el notebook completo se obtienen los siguientes resultados:

| Carpeta | Contenido |
|---|---|
| `resultados_etapa5/` | Cinco gráficas principales en formato PNG. |
| `resultados_etapa6/` | Gráficas de experimentación y 10 archivos CSV. |

En total se documentan siete gráficas:

- Cinco correspondientes a la evaluación y visualización del modelo.
- Dos correspondientes a la experimentación Monte Carlo, con numeración consecutiva `06` y `07` en el bloque final.

Los resultados numéricos principales de exactitud media obtenidos fueron:

| Escenario | Exactitud media |
|---|---:|
| E1 - Base | 44.48 % |
| E2 - Mayor permanencia | 46.27 % |
| E3 - Menor discriminación | 38.92 % |

Estos valores corresponden a los resultados obtenidos en la experimentación realizada.

## Estructura del repositorio

```text
hmm-futbol-montecarlo/
│
├── README.md
├── requirements.txt
├── .gitignore
│
├── experimento_hmm_futbol.ipynb
│
├── resultados_etapa5/
│   ├── 01_linea_tiempo_fases.png
│   ├── 02_acciones_observadas.png
│   ├── 03_evolucion_posesion.png
│   ├── 04_matriz_confusion.png
│   └── 05_comparacion_tiempo_fases.png
│
├── resultados_etapa6/
│   ├── 06_exactitud_por_escenario.png
│   ├── 07_tiempo_fases_por_escenario.png
│   └── [10 archivos CSV]
│
└── docs/
    └── articulo_hmm_futbol.pdf
```

La estructura representa los resultados que deben conservarse en el repositorio. Los nombres de los CSV se encuentran definidos por los archivos que genera el notebook.

## Tecnologías y librerías utilizadas

El proyecto está desarrollado en Python y utiliza las siguientes librerías:

| Librería | Uso |
|---|---|
| NumPy | Operaciones matemáticas y manejo de matrices. |
| Pandas | Procesamiento y exportación de resultados en CSV. |
| Matplotlib | Generación de gráficas. |
| SciPy | Funciones y herramientas estadísticas. |
| Jupyter | Ejecución del notebook. |
| IPykernel | Integración del entorno Python con los notebooks de VS Code. |

## Requisitos

- Python 3.
- Visual Studio Code o Google Colab.
- Extensiones de Python y Jupyter en Visual Studio Code, si se utiliza este entorno.

## Instalación

Se recomienda utilizar un entorno virtual para instalar las dependencias del proyecto.

### 1. Crear el entorno virtual

```bash
python -m venv .venv
```

### 2. Activar el entorno virtual

En Windows:

```bash
.venv\Scripts\activate
```

En Linux o macOS:

```bash
source .venv/bin/activate
```

### 3. Actualizar pip

```bash
python -m pip install --upgrade pip
```

### 4. Instalar las dependencias

```bash
python -m pip install -r requirements.txt
```

El archivo `requirements.txt` contiene:

```text
numpy
pandas
matplotlib
scipy
jupyter
ipykernel
```

También se pueden instalar directamente todas las librerías mediante:

```bash
python -m pip install numpy pandas matplotlib scipy jupyter ipykernel
```

## Ejecución del proyecto

### En Visual Studio Code

1. Abrir la carpeta del repositorio.
2. Abrir `experimento_hmm_futbol.ipynb`.
3. Seleccionar el intérprete de Python correspondiente al entorno virtual `.venv`.
4. Verificar que las dependencias estén instaladas.
5. Ejecutar las celdas en orden, comenzando por la Etapa 2.
6. Continuar con las etapas 3, 4, 5 y 6.
7. Ejecutar también el último bloque de visualización que aparece después de la Etapa 6.

**No se deben ejecutar las etapas de manera aislada si se desea reproducir el experimento completo desde cero.**

### En Google Colab

1. Abrir el notebook en Google Colab.
2. Instalar las dependencias si el entorno lo requiere.
3. Ejecutar las celdas desde la Etapa 2 hasta la última celda, respetando el orden establecido.
4. Verificar la generación de las carpetas y los archivos de resultados.

## Reproducibilidad

Se utilizan semillas aleatorias para controlar la generación de secuencias y facilitar la reproducibilidad de los experimentos.

La experimentación Monte Carlo contempla diferentes escenarios y pruebas complementarias de reproducibilidad y sensibilidad.

Los archivos CSV y las gráficas generadas permiten consultar y analizar los resultados sin necesidad de volver a ejecutar las simulaciones.

## Alcance y limitaciones

- El análisis se basa en partidos sintéticos y no en datos reales de fútbol.
- El modelo utiliza tres estados ocultos y tres categorías de observaciones.
- La reconstrucción de estados mediante Viterbi puede presentar diferencias respecto a la secuencia real simulada.
- Los resultados dependen de los parámetros definidos para el modelo y de los supuestos de simulación.
- Las conclusiones no deben interpretarse como una validación del modelo sobre partidos reales.

## Artículo académico

En la carpeta `docs/` se encuentra el artículo académico que documenta el fundamento teórico, la metodología, los experimentos, los resultados y las conclusiones del proyecto.

## Autor

**[Nombre del autor]**

Proyecto académico desarrollado en el marco de Ingeniería de Software y Datos.