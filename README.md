# Seoul Bike Sharing Demand | Exploratory Data Analysis

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/francorte/seoul-bike-sharing-analysis/blob/main/seoul_bike_sharing_eda.ipynb)
[![UCI Dataset](https://img.shields.io/badge/Data-UCI%20ML%20Repository-blue)](https://archive.ics.uci.edu/dataset/560/seoul%2Bbike%2Bsharing%2Bdemand)
[![License: MIT](https://img.shields.io/badge/Code%20License-MIT-green.svg)](LICENSE)

Análisis exploratorio reproducible de la demanda horaria del sistema público de bicicletas de Seúl. El proyecto transforma datos de movilidad y meteorología en recomendaciones operativas, documentando las decisiones de calidad y evitando interpretar asociaciones como causalidad.

*Reproducible exploratory analysis of Seoul's public bike-sharing demand, focused on temporal patterns, weather conditions and actionable operational insights.*

## Resultado ejecutivo

La demanda no es uniforme: se concentra en horas punta laborables, aumenta en las estaciones cálidas y disminuye notablemente durante la lluvia y los festivos.

| Hallazgo | Resultado |
|---|---:|
| Horas operativas analizadas | 8.465 |
| Pico laborable principal | 18:00 — 1.724 alquileres de media |
| Pico laborable matinal | 08:00 — 1.306 alquileres de media |
| Diferencia verano/invierno | Verano: 4,59 veces la demanda media de invierno |
| Diferencia en festivos | −28,4 % de demanda media |
| Diferencia festiva a las 08:00 | −66,0 % |
| Índice ajustado durante lluvia | 24,5 frente a 103,9 sin lluvia |
| Demandas altas conservadas | 152 picos plausibles; 1,80 % de las horas |

## Recomendaciones

- Reforzar disponibilidad y redistribución entre las 17:00 y las 20:00 en días laborables, especialmente a las 18:00.
- Aplicar una planificación distinta los fines de semana, con cobertura más uniforme durante la tarde.
- Dimensionar recursos estacionalmente: mayor capacidad en verano y otoño y menor expectativa de demanda en invierno.
- Incorporar previsiones de lluvia a la planificación diaria.
- Reducir el refuerzo de las horas punta durante los festivos, sobre todo por la mañana.
- Utilizar el EDA como base de un futuro modelo predictivo, no como un conjunto de reglas causales.

## Problema analítico

> ¿Cómo varía la demanda horaria del sistema público de bicicletas de Seúl según el tiempo, las condiciones meteorológicas, la estación y los días festivos, y qué recomendaciones operativas pueden extraerse?

Audiencia: responsables de movilidad urbana y gestores del servicio.

## Datos

- **Fuente:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/560/seoul%2Bbike%2Bsharing%2Bdemand)
- **DOI:** [10.24432/C5F62R](https://doi.org/10.24432/C5F62R)
- **Periodo:** 1 de diciembre de 2017 – 30 de noviembre de 2018
- **Cobertura:** 8.760 observaciones horarias y 14 variables
- **Licencia de los datos:** CC BY 4.0
- **Carga:** reproducible mediante `ucimlrepo` con el identificador 560

El análisis de demanda se realiza sobre 8.465 horas operativas. Los 295 registros restantes corresponden a interrupciones del servicio y coinciden con demanda cero.

## Calidad y preparación

- 0 valores ausentes declarados.
- 0 filas duplicadas.
- Conversión explícita de fecha y creación de una marca temporal horaria.
- Separación entre dataset original, copia transformada y subconjunto operativo.
- Corrección trazable de 17 valores inválidos de humedad mediante la fórmula de Magnus; los originales se conservan.
- Revisión contextual de valores IQR: los 152 valores altos se conservaron al corresponder a picos horarios plausibles.
- Ajuste descriptivo parcial de la meteorología por estación y hora.

## Flujo de análisis

1. Definición del problema, audiencia y preguntas.
2. Carga reproducible y diccionario de variables.
3. Auditoría de estructura, tipos, ausencias y duplicados.
4. Validaciones de coherencia y transformaciones justificadas.
5. Distribución de la demanda y contextualización de valores altos.
6. Patrones horarios, semanales, estacionales y festivos.
7. Asociaciones meteorológicas y ajuste parcial por estación y hora.
8. Registro de decisiones, limitaciones y recomendaciones.

## Archivos

- [Notebook completo](seoul_bike_sharing_eda.ipynb)
- [Resumen ejecutivo](reports/executive_summary.md)
- [Documentación de datos](data/README.md)
- [Dependencias](requirements.txt)
- [Licencia del código](LICENSE)

## Reproducibilidad

### Google Colab

Usa el botón **Open in Colab** situado al inicio del README y ejecuta todas las celdas en orden.

### Entorno local

```bash
git clone https://github.com/francorte/seoul-bike-sharing-analysis.git
cd seoul-bike-sharing-analysis
python -m venv .venv
pip install -r requirements.txt
jupyter notebook seoul_bike_sharing_eda.ipynb
```

## Limitaciones

- Un único sistema urbano y un periodo de un año.
- Sin información por estación, zona, disponibilidad de bicicletas o capacidad de los puntos.
- Sin información sobre usuarios o propósito de los viajes.
- Muestra festiva reducida.
- Ajuste meteorológico parcial, no causal.
- Resultados no generalizables automáticamente a otras ciudades o periodos.

## Tecnologías

Python · Pandas · NumPy · Matplotlib · Seaborn · Jupyter · Google Colab · UCI Machine Learning Repository

## Autor

**Francisco de la Corte**  
Biólogo y analista de datos especializado en sostenibilidad, bioeconomía e IA aplicada.

## Licencias y cita

El código y la documentación del proyecto se publican bajo licencia [MIT](LICENSE). El dataset conserva su licencia CC BY 4.0.

> Seoul Bike Sharing Demand [Dataset]. (2020). UCI Machine Learning Repository. https://doi.org/10.24432/C5F62R
