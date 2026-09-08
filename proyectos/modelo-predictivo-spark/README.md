# Modelo predictivo de transacciones con PySpark

Este proyecto desarrolla un modelo de clasificación binaria para identificar transacciones potencialmente riesgosas a partir de datos simulados de ventas.

El trabajo recorre un flujo completo de análisis: carga y exploración de datos, limpieza, transformación de variables, construcción de una pipeline de Machine Learning, entrenamiento del modelo y evaluación de sus resultados.

## Objetivo

Clasificar las transacciones como normales o riesgosas utilizando variables como la sucursal, el producto, la cantidad, el precio unitario, el monto total y la hora de la compra.

Para efectos del ejercicio, una transacción se considera riesgosa cuando:

- Su monto total supera los $7.000.
- Ocurre durante la madrugada, antes de las 06:00.

## Tecnologías utilizadas

- Python
- Apache Spark
- PySpark SQL
- PySpark MLlib
- Google Colab
- Pandas

## Proceso realizado

1. Creación de una sesión local de Spark.
2. Lectura y exploración inicial de 200 registros.
3. Revisión de valores nulos y conversión de tipos de datos.
4. Eliminación de registros incompletos o inválidos.
5. Creación de la variable objetivo `label`.
6. Codificación de variables categóricas con `StringIndexer`.
7. Integración de variables con `VectorAssembler`.
8. Separación de datos de entrenamiento y prueba en una proporción aproximada de 80/20.
9. Construcción de una pipeline reproducible.
10. Entrenamiento de una regresión logística.
11. Evaluación mediante accuracy, AUC, F1-score y matriz de confusión.

## Resultados

| Métrica | Resultado |
|---|---:|
| Accuracy | 83,33 % |
| AUC | 0,8908 |
| F1-score | 0,8333 |

Los resultados muestran que el modelo logra diferenciar de buena manera las transacciones normales y riesgosas dentro del conjunto de prueba. El AUC es el resultado más destacado, ya que refleja una buena capacidad de separación entre ambas clases.

## Conclusiones y próximos pasos

La regresión logística fue adecuada como primer modelo por tratarse de una clasificación binaria y porque entrega tanto una clase predicha como su probabilidad asociada. Esto permite priorizar las transacciones que requieren revisión.

Como mejoras futuras se podrían incorporar validación cruzada, búsqueda de hiperparámetros y variables históricas. También sería importante construir la etiqueta de riesgo a partir de eventos reales, ya que en este ejercicio fue definida mediante una regla simulada.

## Archivos

- [Notebook ejecutado](./modelo_predictivo_spark.ipynb)
- [Abrir versión original en Google Colab](https://colab.research.google.com/drive/1FI36XbXFQa1W624Pe0IBBR-_kQcq_H2n?authuser=2)

> El notebook conserva sus resultados de ejecución. Para volver a ejecutarlo desde cero es necesario cargar el archivo de datos original en el entorno de Colab.
