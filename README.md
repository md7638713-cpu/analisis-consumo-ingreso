# Función de consumo en EE. UU. (1959–2009): regresión simple y sus límites

Proyecto de análisis de datos y econometría. Estima la propensión marginal a consumir con una regresión simple y muestra por qué un R² alto no basta cuando se trabaja con series de tiempo.

**Autora:** María de la Luz Flores Porras · Lic. en Economía y Desarrollo Sustentable, Universidad Autónoma de Tamaulipas.

## Pregunta
¿Cuánto del ingreso disponible adicional se destina al consumo, y qué tan confiable es una regresión simple para estimarlo?

## Datos
Serie trimestral `macrodata` incluida en `statsmodels` (EE. UU., 1959-T1 a 2009-T3, dólares de 2005): consumo personal real (`realcons`) e ingreso personal disponible real (`realdpi`).

## Método
1. Exploración gráfica de consumo e ingreso.
2. Regresión MCO en niveles y en logaritmos (elasticidad).
3. Diagnóstico de autocorrelación con Durbin-Watson.
4. Estimación en primeras diferencias para contrastar el riesgo de regresión espuria.

## Resultados principales
| Modelo | Pendiente | R² | Durbin-Watson |
|---|---|---|---|
| Niveles | 0.954 | 0.998 | 0.253 |
| Log-log | 1.032 | 0.998 | 0.188 |
| Diferencias de logs | 0.341 | 0.193 | 1.889 |

En niveles el ajuste parece casi perfecto, pero el Durbin-Watson muy bajo indica residuos autocorrelacionados. En diferencias la relación es mucho más modesta: gran parte del ajuste venía de la tendencia común de las series.

## Cómo reproducirlo
```bash
pip install -r requirements.txt
jupyter notebook consumo_ingreso.ipynb
```

## Siguientes pasos
Replicar con datos de México (INEGI), agregar pruebas de raíz unitaria (ADF) y un modelo de corrección de errores.

## Archivos
- `consumo_ingreso.ipynb`: análisis completo con código, resultados y conclusiones.
- `figura_consumo_ingreso.png`, `figura_residuos.png`: gráficas generadas.
- `requirements.txt`: dependencias.
