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

## Contenido del repositorio

```
Covid Desempeno Sanitario/
├── README.md                        # Este archivo
├── Notebooks/
│   ├── Grupo 7 - Proyecto Covid-19.ipynb
└── CSV/
│   └── covid_internados.csv
└── Informe/
│   └── Grupo 7 - Informe Proyecto Final Covid-19
└── Presentacion/
    └── Grupo 7 - Presentacion Covid-19

```
---
## Datos

```

El dataset completo **no se incluye en este repositorio** por su tamaño (~6 GB
en su versión original). Para obtenerlo:
  1. Acceder al portal oficial:
     [datos.gob.ar](https://datos.gob.ar/dataset/salud-covid-19-casos-registrados-republica-argentina)
  2. Descargar el archivo `Covid19Casos.csv` en caso que quiera conocer el archivo completo.

Ejecucion del Dataset y Notebook:
  1. Descargar y gardar en la carpeta de trabajo el archivo `covid_internados.csv`. Desde el siguiente 
     enlace https://drive.google.com/file/d/1wTv6yeMsqVeuErM9lSkBNio-SIqoLRyj/view?usp=drive_link
  2. Ejecutar el notebook `Grupo 7 - Proyecto Covid-19.ipynb` para
     generar el dataset filtrado `covid_internados_limpio.csv` (~120 MB)
     que utilizan los notebooks posteriores.


```
---

## Metodología

```

El proyecto sigue la metodología **CRISP-DM**:

| Fase CRISP-DM |
|---------------|
| Comprensión del negocio |
| Comprensión de los datos |
| Preparación de los datos |
| Modelado |
| Evaluación |
| Despliegue |

---

## Principales resultados

- **Clustering**: se identificaron perfiles estructurales diferenciados
  entre sistemas hospitalarios provinciales con Silhouette Score > 0.35.
- **Regresión**: el modelo seleccionado explica una proporción
  significativa de la varianza en mortalidad entre sistemas
  hospitalarios (R² > baseline).
- **H1 y H2 confirmada**: persisten diferencias sistemáticas de mortalidad
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

| Integrante |
|------------|
| Jessica Marcela Kaufman |
| Matias Lercari |
| Juan Pablo Villareal Nuñez |
| Sebastian Vera |

---

## Licencia

Datos fuente: Ministerio de Salud de la Nación Argentina.
Licencia Creative Commons Attribution 4.0 International (CC BY 4.0).

