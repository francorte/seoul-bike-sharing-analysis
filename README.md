# Seoul Bike Sharing Demand — análisis exploratorio

Análisis reproducible de la demanda horaria del sistema público de bicicletas de Seúl a partir del conjunto de datos **Seoul Bike Sharing Demand** del UCI Machine Learning Repository.

## Objetivo

Analizar cómo varía la demanda de bicicletas según la hora, el calendario, las condiciones meteorológicas y el funcionamiento del servicio, y traducir los hallazgos en recomendaciones operativas comprensibles.

> Este proyecto identifica patrones y asociaciones en una muestra histórica. No demuestra relaciones causales.

## Pregunta principal

**¿Cómo varía la demanda horaria del sistema público de bicicletas de Seúl en función del tiempo, las condiciones meteorológicas, la estación y los días festivos, y qué recomendaciones operativas pueden extraerse para mejorar la disponibilidad del servicio?**

## Preguntas de análisis

1. ¿Cuáles son las horas y los días con mayor y menor demanda?
2. ¿Cómo cambia la demanda entre estaciones?
3. ¿Qué diferencias aparecen entre festivos y días ordinarios?
4. ¿Cómo se relacionan temperatura, lluvia, nieve y humedad con los alquileres?
5. ¿Existen observaciones atípicas o periodos anómalos?
6. ¿Cuándo convendría reforzar o reducir la disponibilidad de bicicletas?
7. ¿Qué conclusiones son descriptivas y cuáles necesitarían un modelo predictivo?

## Datos

- **Fuente:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/560/seoul%2Bbike%2Bsharing%2Bdemand)
- **DOI:** [10.24432/C5F62R](https://doi.org/10.24432/C5F62R)
- **Cobertura:** 8.760 observaciones horarias
- **Variables:** demanda, fecha, hora, meteorología, estación, festivo y funcionamiento del servicio
- **Valores ausentes declarados por UCI:** ninguno
- **Licencia de los datos:** CC BY 4.0

El archivo original no se duplicará inicialmente en el repositorio: el notebook lo obtiene mediante `ucimlrepo`, lo que mantiene trazabilidad y reproducibilidad.

## Método

1. Definición del problema y de las preguntas.
2. Importación reproducible y revisión del diccionario de variables.
3. Comprobación de estructura, tipos, duplicados y valores ausentes.
4. Limpieza y transformación justificadas.
5. Análisis univariante, temporal y bivariante.
6. Identificación y revisión contextual de valores atípicos.
7. Separación entre observaciones, interpretaciones y recomendaciones.
8. Documentación de limitaciones y revisión humana.

## Estructura

```text
.
├── README.md
├── seoul_bike_sharing_eda.ipynb
├── requirements.txt
├── LICENSE
├── data/
│   └── README.md
└── reports/
    └── executive_summary.md
```

## Ejecución

```bash
pip install -r requirements.txt
jupyter notebook seoul_bike_sharing_eda.ipynb
```

También puede abrirse en Google Colab desde el enlace que se añadirá cuando el notebook esté consolidado.

## Estado

**En desarrollo.** La primera versión establece el planteamiento, la carga reproducible y la auditoría inicial. Los resultados y el resumen ejecutivo se incorporarán después de ejecutar y revisar el EDA.

## Autor

**Francisco de la Corte**  
Biólogo y analista de datos — sostenibilidad, bioeconomía e IA aplicada.

## Cita

Seoul Bike Sharing Demand [Dataset]. (2020). UCI Machine Learning Repository. https://doi.org/10.24432/C5F62R
