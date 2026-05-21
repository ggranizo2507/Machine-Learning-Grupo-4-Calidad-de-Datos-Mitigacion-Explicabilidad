<div align="center">

<!-- BANNER -->
<img src="https://img.shields.io/badge/UEES-Maestría%20en%20IA-1C7293?style=for-the-badge&logo=academia&logoColor=white"/>
<img src="https://img.shields.io/badge/Machine%20Learning-Mayo%202026-02C39A?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/Grupo-4-F96167?style=for-the-badge"/>

<br/><br/>

# 🧠 Predicción de Burnout en Desarrolladores
### Ridge Regression · Calidad de Datos · Mitigación de Sesgos · Explicabilidad XAI

<br/>

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout/blob/main/Calidad-de-Datos-Mitigacion-Explicabilidad_Grupo-4.ipynb)
&nbsp;&nbsp;
[![Dataset](https://img.shields.io/badge/Dataset-Kaggle-20BEFF?style=flat&logo=kaggle&logoColor=white)](https://www.kaggle.com/datasets/asifxzaman/developer-burnout-prediction-dataset7000-samples)
&nbsp;&nbsp;
[![Wiki](https://img.shields.io/badge/📖%20Ver%20Wiki%20Completa-1C7293?style=flat)](../../wiki)

<br/>

---

</div>

## 📌 ¿De qué trata este proyecto?

El **burnout laboral** en desarrolladores de software es un problema creciente que afecta al sector tecnológico a nivel global. Este proyecto aplica técnicas de **Machine Learning supervisado** para predecir el nivel de estrés (`stress_level`, escala 0–100) de un desarrollador a partir de métricas de comportamiento laboral, garantizando rigor técnico, equidad algorítmica y plena explicabilidad de las decisiones del modelo.

> **Tipo de problema:** Regresión supervisada  
> **Modelo final:** Ridge Regression (α = 1.0, optimizado con GridSearchCV)  
> **Dataset:** 7,000 registros × 12 variables — [Kaggle Developer Burnout Prediction Dataset](https://www.kaggle.com/datasets/asifxzaman/developer-burnout-prediction-dataset7000-samples)

---

## 📊 Resultados Clave

<div align="center">

| Métrica | Valor | Interpretación |
|:---|:---:|:---|
| **R² (test)** | `0.81` | El modelo explica el 81% de la varianza del estrés |
| **RMSE (test)** | `10.21 pts` | Error promedio en escala 0–100 |
| **MAE (test)** | `8.06 pts` | Desviación absoluta media |
| **Gap train→test** | `0.54%` | Sin overfitting — modelo robusto |
| **Mejora vs baseline** | `56.5%` | Sobre DummyRegressor (predice siempre la media) |
| **CV 5-fold RMSE** | `10.17 ± 0.11` | Alta estabilidad entre folds |
| **Equidad (Δ RMSE)** | `< 1.0 pt` | Entre grupos de jornada y edad |

</div>

---

## 🔬 Técnicas XAI Aplicadas

El notebook implementa **5 métodos de explicabilidad** validados con consistencia cruzada:

| # | Técnica | Celda | Propósito |
|:---:|:---|:---:|:---|
| 1 | **Coeficientes Ridge** | 10 | Interpretación directa — efecto por variable |
| 2 | **Permutation Importance** | 10 | Impacto real en RMSE — 30 repeticiones |
| 3 | **Partial Dependence Plots** | 11 | Relación marginal de cada variable con el target |
| 4 | **SHAP** (Shapley Values) | 12 | Explicación exacta global e individual |
| 5 | **LIME** | 13 | Aproximación lineal local con análisis de fidelidad |

---

## 📁 Estructura del Repositorio

```
📦 Machine-Learning-Grupo-4-Developer-Burnout/
├── 📓 Calidad-de-Datos-Mitigacion-Explicabilidad_Grupo-4.ipynb   ← Notebook principal
├── 📄 developer_burnout_dataset.csv                               ← Dataset
└── 📖 README.md                                                   ← Este archivo
```

> 📚 **La documentación completa, metodología, resultados y análisis ético están en la [Wiki del repositorio](../../wiki).**

---

## 🗺️ Navegación de la Wiki

La Wiki está organizada en **8 páginas** que cubren todo el pipeline del proyecto:

<div align="center">

| Página | Contenido |
|:---|:---|
| [🏠 Inicio](../../wiki/Home) | Visión general, objetivos y guía de navegación |
| [📊 1 · Descripción del Problema y Dataset](../../wiki/1-Descripcion-del-Problema-y-Dataset) | EDA, calidad de datos, leakage detectado |
| [⚙️ 2 · Metodología y Preprocesamiento](../../wiki/2-Metodologia-y-Preprocesamiento) | Pipeline unificado, justificación de cada decisión |
| [🤖 3 · Modelo y Evaluación](../../wiki/3-Modelo-y-Evaluacion) | Ridge Regression, GridSearch, métricas finales |
| [⚖️ 4 · Equidad Algorítmica](../../wiki/4-Equidad-Algoritmica) | Fairness por grupo, MetricFrame, mitigación |
| [🔍 5 · Explicabilidad XAI](../../wiki/5-Explicabilidad-XAI) | SHAP, LIME, PDP, Coeficientes, Permutation Importance |
| [🧭 6 · Reflexión Ética](../../wiki/6-Reflexion-Etica) | Riesgos, LOPDP, análisis crítico del modelo |
| [✅ 7 · Conclusiones y Mejoras](../../wiki/7-Conclusiones-y-Mejoras) | Síntesis ejecutiva, recomendaciones, trabajo futuro |

</div>

---

## 👥 Equipo — Grupo 4

<div align="center">

<table>
  <tr>
    <td align="center">
      <b>Eduardo Ceballos Jijón</b><br/>
      <sub>Introducción del Problema<br/>Metodología</sub>
    </td>
    <td align="center">
      <b>Guillermo Granizo Veintimilla</b><br/>
      <sub>Análisis del Modelo<br/>Transparencia XAI</sub>
    </td>
    <td align="center">
      <b>José Ulloa Manzur</b><br/>
      <sub>Equidad Algorítmica<br/>Riesgos Éticos</sub>
    </td>
    <td align="center">
      <b>Christian Valle Maridueña</b><br/>
      <sub>Conclusiones<br/>Mejoras del Modelo</sub>
    </td>
  </tr>
</table>

</div>

---

## 🚀 Cómo Ejecutar el Notebook

### Opción 1 — Google Colab (recomendado)

1. Haz clic en el botón **Open in Colab** al inicio de este README
2. Sube el archivo `developer_burnout_dataset.csv` usando **Files → Upload** en Colab
3. Ejecuta las celdas en orden (Celda 1 → Celda 19)

### Opción 2 — Localmente

```bash
# Clonar el repositorio
git clone https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout.git
cd Machine-Learning-Grupo-4-Developer-Burnout

# Instalar dependencias
pip install scikit-learn pandas numpy matplotlib seaborn scipy fairlearn shap lime

# Abrir el notebook
jupyter notebook Calidad-de-Datos-Mitigacion-Explicabilidad_Grupo-4.ipynb
```

---

## 📋 Flujo del Pipeline

```
Dataset (7,000 × 12)
       │
       ▼
  1. Limpiar categorías
       │
       ▼
  2. Eliminar leakage (burnout_level)
       │
       ▼
  3. Split TRAIN/TEST — 80%/20% estratificado
       │
       ▼
  4. Pipeline unificado (fit solo en train):
     ├─ Winsorizer P5–P95
     ├─ SimpleImputer (mean)
     └─ StandardScaler
       │
       ▼
  5. Ridge Regression — GridSearchCV (α óptimo = 1.0)
       │
       ▼
  6. Evaluación — R²=0.81 | RMSE=10.21
       │
       ▼
  7. Fairness — MetricFrame | Δ RMSE < 1 pt
       │
       ▼
  8. XAI — SHAP · LIME · PDP · Coeficientes · Perm. Importance
```

---

<div align="center">

**UEES · Maestría en Inteligencia Artificial · Machine Learning · Mayo 2026**

[![Wiki](https://img.shields.io/badge/📖%20Ir%20a%20la%20Wiki%20Completa-1C7293?style=for-the-badge)](../../wiki)

</div>
