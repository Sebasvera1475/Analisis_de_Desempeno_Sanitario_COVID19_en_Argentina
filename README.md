# Análisis de Desempeño Sanitario durante COVID-19 en Argentina
### Diplomatura en Ciencia de Datos y Análisis Avanzado — UTN BA
**Grupo 7** | Sebastian Vera · Jessica Marcela Kaufman · Matias Lercari · Juan Pablo Villareal Nuñez

---

## Descripción del proyecto

Este proyecto desarrolla un marco analítico reproducible para evaluar
el desempeño de los sistemas hospitalarios provinciales argentinos
durante la pandemia de COVID-19 (marzo 2020 – junio 2022), utilizando
registros oficiales del SISA (Ministerio de Salud de la Nación).

La unidad de análisis es la **provincia de atención** (carga_provincia_nombre),
es decir, el sistema hospitalario donde el paciente fue efectivamente
internado y tratado. Este enfoque permite evaluar la capacidad de
respuesta y eficiencia de cada sistema de salud provincial como
**proveedor de atención**, independientemente del lugar de residencia
de los pacientes.

El análisis combina técnicas de segmentación no supervisada (clustering)
y modelado supervisado (regresión) para:

- Construir indicadores de desempeño hospitalario comparables entre
  sistemas provinciales y sectores (público/privado).
- Identificar perfiles estructurales de desempeño hospitalario
  mediante clustering.
- Evaluar si persisten diferencias sistemáticas de mortalidad entre
  sistemas hospitalarios aun controlando por edad y severidad de los
  pacientes atendidos (Hipótesis H1 y H2).
- Simular escenarios de presión sobre los sistemas hospitalarios
  ante una nueva variante epidémica.

---

## Estructura del repositorio

```
covid-desempeno-sanitario/
├── README.md                        # Este archivo
├── requirements.txt                 # Dependencias del proyecto
├── data/
│   └── INSTRUCCIONES_DATOS.md       # Cómo obtener el dataset
├── notebooks/
│   ├── 00_configuracion.ipynb       # Imports y paleta de colores
│   ├── 01_carga_y_eda.ipynb         # Exploración inicial
│   ├── 02_limpieza_y_estandarizacion.ipynb
│   ├── 03_feature_engineering.ipynb # Variables derivadas
│   ├── 04_kpis_y_visualizaciones.ipynb
│   ├── 05_clustering.ipynb          # K-Means + Jerárquico
│   ├── 06_modelado_supervisado.ipynb
│   └── 07_valor_de_negocio.ipynb    # Simulación y recomendaciones
├── outputs/
│   ├── graficos/                    # PNG generados por los notebooks
│   └── tablas/                      # CSV exportados
└── informe/
    └── Grupo7_Informe_Final.pdf
```

---

## Requisitos e instalación

### Python
Este proyecto requiere **Python 3.9 o superior**.

### Instalación de dependencias

```bash
# 1. Clonar el repositorio
git clone https://github.com/[usuario]/covid-desempeno-sanitario.git
cd covid-desempeno-sanitario

# 2. Crear entorno virtual (recomendado)
python -m venv venv
source venv/bin/activate        # Linux / Mac
venv\Scripts\activate           # Windows

# 3. Instalar dependencias
pip install -r requirements.txt
```

### Contenido de `requirements.txt`

```
pandas>=1.5.0
numpy>=1.23.0
matplotlib>=3.6.0
seaborn>=0.12.0
scikit-learn>=1.2.0
scipy>=1.9.0
jupyter>=1.0.0
```

---

## Datos

El dataset **no se incluye en este repositorio** por su tamaño (~6 GB
en su versión original). Para obtenerlo:

1. Acceder al portal oficial:
   [datos.gob.ar](https://datos.gob.ar/dataset/salud-covid-19-casos-registrados-republica-argentina)
2. Descargar el archivo `Covid19Casos.csv`
3. Ejecutar el notebook `02_limpieza_y_estandarizacion.ipynb` para
   generar el dataset filtrado `covid_internados_limpio.csv` (~120 MB)
   que utilizan los notebooks posteriores.

El archivo `data/INSTRUCCIONES_DATOS.md` detalla el proceso completo
de descarga y filtrado.

---

## Orden de ejecución

Los notebooks están numerados en orden de ejecución. Cada uno lee
los archivos generados por el anterior:

| Notebook | Entrada | Salida principal |
|----------|---------|-----------------|
| 00 | — | Configuración global |
| 01 | `Covid19Casos.csv` | Exploración inicial |
| 02 | `Covid19Casos.csv` | `covid_internados_limpio.csv` |
| 03 | `covid_internados_limpio.csv` | Dataset con variables derivadas |
| 04 | Dataset limpio | Gráficos KPIs |
| 05 | `matriz_kpis_*.csv` | `clusters_resultado_*.csv` |
| 06 | Dataset limpio | `modelo_supervisado_resultados.csv` |
| 07 | Resultados previos | Gráficos y recomendaciones |

---

## Metodología

El proyecto sigue la metodología **CRISP-DM**:

| Fase CRISP-DM | Notebooks |
|---------------|-----------|
| Comprensión del negocio | README + Informe |
| Comprensión de los datos | 01, 02 |
| Preparación de los datos | 02, 03 |
| Modelado | 05, 06 |
| Evaluación | 06, 07 |
| Despliegue | 07 + Informe |

---

## Principales resultados

- **Clustering**: se identificaron perfiles estructurales diferenciados
  entre sistemas hospitalarios provinciales con Silhouette Score > 0.35.
- **Regresión**: el modelo seleccionado explica una proporción
  significativa de la varianza en mortalidad entre sistemas
  hospitalarios (R² > baseline).
- **H5 confirmada**: persisten diferencias sistemáticas de mortalidad
  entre sistemas hospitalarios provinciales aun controlando por edad,
  severidad y sector de los pacientes atendidos.
- **Benchmarking**: se estiman vidas evitables si los sistemas
  hospitalarios de bajo desempeño alcanzaran el nivel del cluster
  de referencia.
- **Simulación**: ante una nueva variante con perfil del pico histórico,
  los sistemas hospitalarios de 5 provincias concentrarían la mayor
  presión de atención.

---

## Consideraciones éticas

- El análisis utiliza exclusivamente datos anonimizados de acceso público.
- Las comparaciones entre sistemas hospitalarios provinciales y sectores
  se interpretan con cautela, reconociendo factores estructurales,
  heterogeneidad en la complejidad de los casos recibidos y sesgos
  de registro.
- El proyecto no infiere desempeño individual ni profesional.
- No se incluyen datos que permitan reidentificación de personas.

---

## Equipo

| Integrante | Rol principal |
|------------|--------------|
| Sebastian Vera | |
| Jessica Marcela Kaufman | |
| Matias Lercari | |
| Juan Pablo Villareal Nuñez | |

---

## Licencia

Datos fuente: Ministerio de Salud de la Nación Argentina.
Licencia Creative Commons Attribution 4.0 International (CC BY 4.0).

