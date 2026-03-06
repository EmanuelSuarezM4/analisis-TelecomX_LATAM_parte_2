# 📡 Análisis de Evasión de Clientes - TelecomX LATAM (Fase II)

Este proyecto desarrolla un sistema de **Machine Learning** de clasificación binaria para predecir la tasa de cancelación (Churn) en una operadora de telecomunicaciones. El objetivo es identificar los factores de riesgo y proporcionar una herramienta predictiva que permita a la empresa ejecutar estrategias de retención precisas.



## 📊 1. Análisis Exploratorio y Dirigido (EDA)

Se realizó un estudio de las variables para entender el comportamiento de los desertores frente a los clientes leales.

### Matriz de Correlación
Identificamos que la **Fibra Óptica** (+0.32) y los **Cargos Mensuales** (+0.23) son los principales impulsores de la evasión, mientras que la **Antigüedad** (-0.41) y los **Contratos a largo plazo** (-0.41) son los anclajes de retención más fuertes.

<img width="1403" height="1116" alt="image" src="https://github.com/user-attachments/assets/b03f6af9-4c06-4e34-9a81-1c6ef11bd0ed" />


### Comportamiento de Antigüedad y Gasto
Los clientes que cancelan suelen hacerlo dentro de los primeros **10 meses** de servicio. Además, existe un segmento de clientes de alto valor (Outliers en cargos totales) que están abandonando la compañía.

<img width="1584" height="583" alt="image" src="https://github.com/user-attachments/assets/a6213d46-35bb-42ca-8b0b-795776ac541d" />


---

## ⚙️ 2. Preprocesamiento y Preparación

Para garantizar que los modelos aprendan de forma equilibrada y sin sesgos de magnitud, se aplicó:

* **Balanceo de Clases (SMOTE):** Se generaron muestras sintéticas para equilibrar la clase minoritaria (Evasión), que representaba originalmente el **26.58%** de los datos.
* **Estandarización:** Se utilizó `StandardScaler` para normalizar variables como `Cargos_Totales`, asegurando que los modelos basados en distancia y optimización no se vean sesgados por la escala.
* **División Estratificada:** El dataset se dividió en **80% Entrenamiento (5,625 muestras)** y **20% Prueba (1,407 muestras)**, manteniendo la proporción original de evasión en ambos conjuntos.

---

## 🤖 3. Modelado y Evaluación Comparativa

Se evaluaron dos modelos con naturalezas distintas para encontrar el equilibrio óptimo entre precisión y detección:

| Métrica (Clase 1 - Churn) | Regresión Logística | Random Forest |
| :--- | :--- | :--- |
| **Exactitud (Accuracy)** | 77% | 77% |
| **Recall (Sensibilidad)** | **0.70** | 0.61 |
| **Precisión** | 0.56 | 0.57 |
| **F1-Score** | **0.62** | 0.59 |

### Matrices de Confusión
El modelo de **Regresión Logística** fue seleccionado como el ganador debido a su capacidad superior para detectar el **70% de las evasiones reales** (Recall), reduciendo significativamente los falsos negativos en comparación con el Random Forest.

<img width="388" height="988" alt="image" src="https://github.com/user-attachments/assets/42c26be0-d2fe-4aa5-8bc9-4c3306644038" />


---

## 💡 4. Hallazgos y Estrategias de Negocio

1.  **Revisión de Fibra Óptica:** Es el predictor de riesgo #1. Se recomienda una auditoría técnica inmediata sobre la calidad de este servicio.
2.  **Conversión de Contratos:** Los clientes con contratos de 2 años tienen una probabilidad de fuga drásticamente menor. Se propone incentivar la migración de planes mensuales a contratos anuales.
3.  **Programa de Bienvenida:** Dado que el riesgo es crítico en los primeros 12 meses, se deben implementar bonificaciones por lealtad durante el primer año para superar la barrera crítica de los 10 meses.

---

## 📁 Estructura del Proyecto
* `/data`: Datasets originales y procesados.
* `/notebooks`: `TelecomX_LATAM.ipynb` con el flujo completo de Ciencia de Datos.
* `README.md`: Documentación estratégica del proyecto.

---
**Desarrollado por:** Emanuel Suarez Merino – Analista de Datos / Ingeniero de Sistemas.
