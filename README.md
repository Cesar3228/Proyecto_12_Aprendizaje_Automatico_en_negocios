# Proyecto_12_Aprendizaje_Automatico_en_negocios
## Selección de la región óptima para extracción de petróleo (OilyGiant)  
## Optimal Oil Well Location Selection (OilyGiant)

---

## 🧩 Descripción general / Overview

### 🇪🇸 Español

Trabajas para la compañía de extracción de petróleo **OilyGiant**, cuyo objetivo es identificar la **mejor región para desarrollar 200 nuevos pozos petrolíferos**.  
La decisión debe basarse en predicciones de volumen de reservas, análisis de beneficios y evaluación de riesgos financieros.

En este proyecto se construye un **modelo de regresión lineal** para predecir el volumen de reservas de nuevos pozos petrolíferos en tres regiones distintas y, posteriormente, se utiliza la técnica de **bootstrapping** para analizar la distribución de beneficios y el riesgo de pérdidas.

La región seleccionada debe:
- Tener un **riesgo de pérdidas inferior al 2.5%**
- Ofrecer el **mayor beneficio promedio** entre las regiones viables

Este proyecto corresponde al **Sprint 12 – Machine Learning para toma de decisiones de negocio** del programa de **Data Science de TripleTen**.

---

### 🇬🇧 English

You are working for the oil extraction company **OilyGiant**, whose goal is to identify the **best region to develop 200 new oil wells**.  
The decision must be based on reserve volume predictions, profit analysis, and financial risk assessment.

In this project, a **linear regression model** is built to predict oil reserve volumes in three different regions. The **bootstrapping technique** is then used to assess profit distributions and loss risk.

The selected region must:
- Have a **loss risk below 2.5%**
- Provide the **highest average profit** among viable regions

This project corresponds to **Sprint 12 – Machine Learning for business decision-making** in the **TripleTen Data Science program**.

---

## 📂 Datos / Data

### Archivos / Files
- `/datasets/geo_data_0.csv`
- `/datasets/geo_data_1.csv`
- `/datasets/geo_data_2.csv`

### Variables / Features
- `id` — identificador único del pozo  
- `f0`, `f1`, `f2` — características geológicas  
- `product` — volumen de reservas (miles de barriles)

> **Nota / Note:**  
> El conjunto de datos no se incluye en este repositorio debido a restricciones de la plataforma **TripleTen**.  
> The dataset is not included due to **TripleTen platform restrictions**.

---

## ⚙️ Condiciones del proyecto / Project Constraints

- Modelo permitido: **Regresión Lineal**
- Evaluación inicial: **500 pozos**, selección de los **200 mejores**
- Presupuesto total: **100 millones USD**
- Ingreso por unidad: **$4,500 USD** (reservas en miles de barriles)
- Producción mínima por pozo para evitar pérdidas: **111.1 unidades**
- Riesgo máximo permitido: **2.5%**

---

## 🔍 Metodología / Methodology

### 🇪🇸 Español

1. **Preparación de datos**
   - Lectura de datasets por región
   - Separación de características y variable objetivo
   - División de datos en entrenamiento (75%) y validación (25%)

2. **Entrenamiento del modelo**
   - Entrenamiento de un modelo de **regresión lineal** por región
   - Predicción del volumen de reservas en el conjunto de validación
   - Cálculo del **RMSE** y del volumen medio predicho

3. **Análisis preliminar**
   - Comparación del volumen medio predicho con el punto de equilibrio
   - Evaluación inicial del potencial económico por región

4. **Cálculo de beneficios**
   - Selección de los **200 pozos con mayor volumen predicho** por región
   - Cálculo del beneficio total esperado por región

5. **Análisis de riesgo (Bootstrapping)**
   - Aplicación de **1000 muestras bootstrap**
   - Estimación del beneficio promedio, intervalo de confianza del 95% y riesgo de pérdidas
   - Selección final de la región óptima

---

## 📊 Resultados del modelo / Model Results

### 📈 Calidad del modelo por región

| Región | RMSE | Volumen medio predicho |
|------|------|------------------------|
| Región 0 | 37.58 | 92.59 |
| Región 1 | 0.89 | 68.73 |
| Región 2 | 40.03 | 94.97 |

Ninguna región alcanza en promedio el punto de equilibrio de **111.1 unidades por pozo**, por lo que la selección final se basa en **beneficio agregado y control de riesgo**, no en promedios individuales.

---

### 💰 Beneficio potencial (Top 200 pozos)

| Región | Beneficio total estimado (USD) |
|------|--------------------------------|
| Región 0 | $33.2 M |
| Región 2 | $27.1 M |
| Región 1 | $24.2 M |

---

### 🔁 Análisis de riesgo (Bootstrapping – 1000 muestras)

| Región | Beneficio promedio (USD) | IC 95% (USD) | Riesgo de pérdidas |
|------|---------------------------|-------------|--------------------|
| Región 0 | $3,908,065 | [-$1,187,709 , $9,002,204] | **6.80%** |
| Región 1 | $4,571,469 | [$459,915 , $8,615,557] | **1.40% ✅** |
| Región 2 | $3,937,975 | [-$1,720,922 , $9,363,611] | **9.00%** |

---

## ✅ Decisión final / Final Decision

### 🇪🇸 Español

De acuerdo con los criterios del proyecto:

- ✅ Riesgo de pérdidas **< 2.5%**
- ✅ Máximo beneficio promedio entre regiones viables

La **Región 1** es la **única región que cumple el criterio de riesgo** y, además, presenta el **mayor beneficio promedio**, por lo que se recomienda como la mejor región para desarrollar los 200 pozos petrolíferos.

Esta elección **no coincide** con la selección basada únicamente en el beneficio potencial bruto, lo que demuestra la importancia de incorporar el **análisis de riesgo** en decisiones de inversión.

---

### 🇬🇧 English

According to the project criteria:

- ✅ Loss risk **< 2.5%**
- ✅ Highest average profit among viable regions

**Region 1** is the **only region that meets the risk requirement** and also has the **highest average profit**, making it the recommended region for developing the 200 oil wells.

This choice **differs** from the selection based solely on raw profit potential, highlighting the importance of incorporating **risk analysis** into investment decisions.

---

## 📁 Estructura del repositorio / Repository Structure

```text
.
├── Proyecto_12.ipynb
├── requirements.txt
└── README.md
