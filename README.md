# Forecast de Demanda en Retail

Este repositorio contiene el código y análisis de un proyecto de curso centrado en la predicción de series de tiempo para demanda en retail. Utilizando el dataset de la competencia **M5 Forecasting (Kaggle)**, el proyecto evalúa el desempeño de modelos estadísticos tradicionales frente a algoritmos modernos de Machine Learning.

---

## Objetivo del Proyecto

El objetivo principal es predecir la demanda diaria de productos de retail en un horizonte de **8 semanas (56 días)**, comparando el rendimiento de tres enfoques distintos:
1. Un modelo empírico de referencia, usado como baseline (**Seasonal Naive**).
2. Un modelo estadístico clásico univariado (**SARIMA**).
3. Un modelo global de Machine Learning basado en árboles de decisión (**XGBoost**).

---

## Alcance

*   **Dataset:** Datos de ventas diarias de tiendas Walmart ([Kaggle](https://www.kaggle.com/competitions/m5-forecasting-accuracy/overview)). Para este experimento sólo se necesitan los archivos ```sales_train_evaluation.csv``` y ```calendar.csv```.
*   **Segmentación:** Nos enfocamos en la categoría `FOODS` y la tienda `CA_1`, seleccionando específicamente una muestra aleatoria de 10 productos catalogados como "Smooth" (de demanda regular y estable) para la validación final.
*   **Horizonte de Pronóstico (Test):** 56 días.
*   **Estrategia de Modelado:** 
    *   *Local:* SARIMA se entrenó de forma aislada para cada uno de los 10 productos seleccionados.
    *   *Global:* XGBoost se entrenó con el dataset masivo completo (millones de filas) usando *Cross-Learning*, para luego validar sus predicciones únicamente en los 10 productos seleccionados.
*   **Métricas de Evaluación:** MAE (Mean Absolute Error).

---

## 📁 Estructura del Repositorio

```text
├── data/                            # Datos originales de Kaggle (sales_train_evaluation.csv, calendar.csv)
├── models/                          # Modelos entrenados
│   ├── sarima_models.pkl            # Modelos SARIMA entrenados 
│   └── xgboost_m5_global_gpu.pkl    # Modelo XGBoost entrenado 
├── notebooks/                         # Cuadernos de análisis
│   └── capstone_1.ipynb             # Cuaderno principal de análisis y modelado
└── README.md                        # Descripción del proyecto
```
---

## Referencias
- [Datos Kaggle](https://www.kaggle.com/competitions/m5-forecasting-accuracy/overview)
- Makridakis, S., Spiliotis, E., & Assimakopoulos, V. (2022). The M5 competition: Background, organization, and implementation. International Journal of Forecasting, 38(4), 1325–1336. https://doi.org/10.1016/j.ijforecast.2021.07.007