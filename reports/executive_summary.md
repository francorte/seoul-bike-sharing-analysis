# Resumen ejecutivo — Seoul Bike Sharing Demand

## Decisión principal

El sistema debería planificar su disponibilidad con reglas diferenciadas por hora, tipo de día, estación y lluvia. Una capacidad uniforme durante todo el año no refleja la variación observada en la demanda.

## Objetivo y alcance

Se analizaron 8.760 registros horarios del sistema público de bicicletas de Seúl entre el 1 de diciembre de 2017 y el 30 de noviembre de 2018. El objetivo fue identificar patrones temporales, meteorológicos y de calendario que apoyen decisiones de disponibilidad y redistribución.

El análisis de demanda se limitó a 8.465 horas operativas. Las 295 horas restantes corresponden a interrupciones del servicio y presentan demanda cero.

## Calidad de los datos

- No se detectaron valores ausentes ni filas duplicadas.
- La fecha se convirtió desde texto a formato temporal y se combinó con la hora.
- Se identificaron 17 valores de humedad iguales a 0 %, incompatibles con la temperatura y el punto de rocío. Se estimaron mediante la fórmula de Magnus y se conservaron los valores originales para mantener trazabilidad.
- El criterio IQR identificó 152 demandas altas —1,80 % de las horas operativas—. No se eliminaron porque se concentran en horas punta plausibles.

## Hallazgos comprobados

### 1. La demanda se concentra en las horas punta laborables

Los días laborables presentan dos máximos:

- 08:00: 1.306 alquileres por hora de media.
- 18:00: 1.724 alquileres por hora de media.

La demanda media de las 18:00 es aproximadamente un 48 % superior a la de las 08:00. Durante el fin de semana desaparece el pico matinal y el máximo se desplaza a las 17:00, con 1.161 alquileres.

### 2. Los valores altos son picos reales

De los 152 registros superiores al límite IQR, 86 —56,6 %— ocurren a las 18:00. El 88,8 % se concentra entre las 18:00 y las 20:00. Los 15 máximos se registran a las 18:00, en días no festivos y sin lluvia.

### 3. La estación cambia la intensidad, no la hora principal

| Estación | Demanda media por hora | Pico horario |
|---|---:|---:|
| Invierno | 225,5 | 18:00 |
| Primavera | 746,3 | 18:00 |
| Verano | 1.034,1 | 18:00 |
| Otoño | 924,1 | 18:00 |

La demanda media de verano es 4,59 veces la de invierno. Esta asociación no puede atribuirse únicamente a la temperatura.

### 4. Los festivos reducen especialmente las horas punta

La demanda media desciende de 739 alquileres en días no festivos a 529 en festivos: aproximadamente un 28,4 % menos.

La reducción alcanza el 66,0 % a las 08:00 y el 46,7 % a las 18:00. La muestra festiva contiene 408 observaciones y debe interpretarse con cautela.

### 5. La lluvia está asociada con una reducción intensa

Sin ajuste, la media es de 167 alquileres durante la lluvia y 766 sin lluvia. Tras comparar cada observación con la mediana de su misma estación y hora:

- Índice medio con lluvia: 24,5.
- Índice medio sin lluvia: 103,9.
- Diferencia aproximada: −76,4 %.

Este control es parcial y no demuestra causalidad, pero la asociación continúa siendo operativamente relevante.

### 6. La temperatura presenta una asociación positiva no lineal

La correlación global de Spearman entre temperatura y demanda es 0,612. La demanda media aumenta hasta el intervalo de 20–30 °C y desciende ligeramente por encima de 30 °C.

La asociación se mantiene dentro de cada estación, aunque es más débil en verano:

- Invierno: 0,418.
- Primavera: 0,564.
- Verano: 0,217.
- Otoño: 0,424.

## Recomendaciones operativas

1. **Días laborables:** reforzar disponibilidad y redistribución entre las 17:00 y las 20:00, priorizando las 18:00.
2. **Fin de semana:** utilizar una cobertura vespertina más uniforme entre las 15:00 y las 19:00.
3. **Planificación estacional:** aumentar capacidad prevista en verano y otoño; reducirla en invierno sin eliminar el servicio.
4. **Lluvia:** incorporar previsiones meteorológicas al dimensionamiento diario y revisar a la baja las expectativas de demanda.
5. **Festivos:** reducir el refuerzo matinal y vespertino respecto a un día laborable ordinario.
6. **Siguiente fase:** desarrollar y validar un modelo predictivo temporal antes de automatizar decisiones de inventario o redistribución.

## Limitaciones

- Un único año y una única ciudad.
- Sin información por estación o barrio.
- Sin disponibilidad de bicicletas, capacidad de anclajes, costes ni rutas.
- Sin propósito del viaje ni características de los usuarios.
- Pocos registros festivos respecto al resto.
- Posibles factores de confusión no controlados.
- Asociaciones descriptivas; no se demuestra causalidad.

## Conclusión

Los resultados justifican una planificación dinámica. La hora y el calendario determinan la forma del patrón de demanda, mientras que la estación y la meteorología modifican fuertemente su intensidad. Las recomendaciones son adecuadas para orientar operaciones y formular hipótesis, pero deben validarse con datos más recientes, información espacial y un modelo predictivo antes de automatizar decisiones.
