<div align="center">

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

El **burnout laboral** en desarrolladores de software es un problema creciente en el sector tecnológico. Este proyecto aplica **Machine Learning supervisado** para predecir el nivel de estrés (`stress_level`, escala 0–100) de un desarrollador a partir de métricas de comportamiento laboral, garantizando rigor técnico, equidad algorítmica y plena explicabilidad.

> **Tipo de problema:** Regresión supervisada  
> **Modelo final:** Ridge Regression (α = 1.0, optimizado con GridSearchCV 5-fold)  
> **Dataset:** 7,000 registros × 12 columnas originales → **10 variables predictoras** tras eliminar el target (`stress_level`) y el leakage (`burnout_level`)  
> **Nota técnica:** Las predicciones se recortan con `np.clip(0, 100)` — Ridge puede predecir fuera del rango físico válido

---

## 📊 Resultados Clave

<div align="center">

| Métrica | Valor | Interpretación |
|:---|:---:|:---|
| **R² (test)** | `0.81` | El modelo explica el 81% de la varianza del estrés |
| **RMSE (test)** | `10.17 pts` | Error promedio en escala 0–100 (con `np.clip`) |
| **MAE (test)** | `7.99 pts` | Desviación absoluta media |
| **Gap train→test** | `0.50%` | Sin overfitting — modelo robusto |
| **Mejora vs baseline** | `56.7%` | Sobre DummyRegressor (predice siempre la media) |
| **CV 5-fold RMSE** | `10.17 ± 0.11` | Alta estabilidad entre folds |
| **Δ RMSE por jornada** | `≈ 1.02 pts` | Menor al umbral de 3 pts ✅ |
| **Δ RMSE por edad** | `≈ 0.54 pts` | Menor al umbral de 3 pts ✅ |

</div>

---

## 🔬 Técnicas XAI Aplicadas

El notebook implementa **5 métodos de explicabilidad** con consistencia validada entre métodos independientes:

| # | Técnica | Celda | Resultado clave |
|:---:|:---|:---:|:---|
| 1 | **Coeficientes Ridge** | 10 | `daily_work_hours` = 27.1% del peso total |
| 2 | **Permutation Importance** | 10 | Permutar `daily_work_hours` → RMSE aumenta **+10.31 pts** (35.2%) |
| 3 | **Partial Dependence Plots** | 11 | Relación lineal confirmada en 4 variables principales |
| 4 | **SHAP** (Shapley Values) | 12 | Explicación exacta global e individual (beeswarm + waterfall) |
| 5 | **LIME** | 13 | Fidelidad variable por instancia: R² local ≈ 0.07–0.59 |

> ⚠️ LIME tiene fidelidad variable — siempre se contrasta con SHAP, que para Ridge Regression es matemáticamente exacto.

---

## 🚨 Data Leakage Detectado y Resuelto

La variable `burnout_level` es una **discretización determinística** de `stress_level`:

```
Low    → stress_level ∈ [0.00,  35.00]  (sin solapamiento)
Medium → stress_level ∈ [35.02, 69.97]  (sin solapamiento)
High   → stress_level ∈ [70.01, 100.00] (sin solapamiento)
```

Incluirla como feature equivale a entrenar el modelo con la respuesta disfrazada. **Se elimina en el Paso 1 del pipeline**, antes de cualquier otra operación.

---

## 📁 Estructura del Repositorio

```
📦 Machine-Learning-Grupo-4-Developer-Burnout/
├── 📓 Calidad-de-Datos-Mitigacion-Explicabilidad_Grupo-4.ipynb   ← Notebook (19 celdas de código)
├── 📌 Burnout_Prediccion_Grupo4_UEES.pdf                          ← Presentación técnica
├── 📄 developer_burnout_dataset.csv                               ← Dataset
├── 🚀 LICENCE                                                     ← Licencia de uso
└── 📖 README.md                                                   ← Este archivo
```

> 📚 **La documentación completa está en la [Wiki del repositorio](../../wiki).**

---

## 🗺️ Navegación de la Wiki

<div align="center">

| Página | Contenido |
|:---|:---|
| [🏠 Inicio](../../wiki/Home) | Visión general, resumen ejecutivo y guía de navegación |
| [📊 1 · Descripción del Problema y Dataset](../../wiki/1-Descripción-del-Problema-y-Dataset) | EDA, correlaciones, calidad de datos, leakage |
| [⚙️ 2 · Metodología y Preprocesamiento](../../wiki/2-Metodología-y-Preprocesamiento) | Pipeline, justificación de cada decisión, `np.clip` |
| [🤖 3 · Modelo y Evaluación](../../wiki/3-Modelo-y-Evaluación) | Ridge, GridSearch, métricas finales, residuales |
| [⚖️ 4 · Equidad Algorítmica](../../wiki/4-Equidad-Algorítmica) | Fairness por grupo, MetricFrame, mitigación |
| [🔍 5 · Explicabilidad XAI](../../wiki/5-Explicabilidad-XAI) | SHAP, LIME (fidelidad real), PDP, Coeficientes |
| [🧭 6 · Reflexión Ética](../../wiki/6-Reflexión-Ética) | Riesgos, LOPDP, análisis crítico |
| [✅ 7 · Conclusiones y Mejoras](../../wiki/7-Conclusiones-y-Mejoras) | Síntesis, recomendaciones, trabajo futuro |

</div>

---

## 👥 Equipo — Grupo 4

<div align="center">

<table>
  <tr>
    <td align="center"><b>Eduardo Ceballos Jijón</b><br/><sub>Introducción · Metodología</sub></td>
    <td align="center"><b>Guillermo Granizo Veintimilla</b><br/><sub>Análisis del Modelo · XAI</sub></td>
    <td align="center"><b>José Ulloa Manzur</b><br/><sub>Equidad · Riesgos Éticos</sub></td>
    <td align="center"><b>Christian Valle Maridueña</b><br/><sub>Conclusiones · Mejoras</sub></td>
  </tr>
</table>

</div>

---

## 🚀 Cómo Ejecutar el Notebook

### Opción 1 — Google Colab (recomendado)
1. Clic en **Open in Colab** al inicio de este README
2. Sube `developer_burnout_dataset.csv` con **Files → Upload**
3. Ejecuta las **19 celdas de código** en orden (Celda 1 → Celda 19)

### Opción 2 — Localmente
```bash
git clone https://github.com/ggranizo2507/Machine-Learning-Grupo-4-Developer-Burnout.git
cd Machine-Learning-Grupo-4-Developer-Burnout
pip install scikit-learn pandas numpy matplotlib seaborn scipy fairlearn shap lime
jupyter notebook Calidad-de-Datos-Mitigacion-Explicabilidad_Grupo-4.ipynb
```

---

## 📋 Flujo del Pipeline

```
Dataset (7,000 × 12 columnas)
       │
       ▼
  1. Limpiar categorías (strip + capitalize)
       │
       ▼
  2. Eliminar leakage (drop burnout_level — discretización determinística)
       │
       ▼
  3. Split TRAIN/TEST — 80%/20% estratificado por rango de estrés
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
  6. np.clip(predictions, 0, 100)  ← recorte al rango físico válido
       │
       ▼
  7. Evaluación — R²=0.81 | RMSE=10.17 | MAE=7.99 | Gap=0.50%
       │
       ▼
  8. Fairness — MetricFrame | Δ RMSE ≈ 1.02 pts jornada, 0.54 pts edad
       │
       ▼
  9. XAI — SHAP · LIME (R²≈0.07–0.59) · PDP · Coeficientes · Perm. Imp.
```

---

<div align="center">

**UEES · Maestría en Inteligencia Artificial · Machine Learning · Mayo 2026**

[![Wiki](https://img.shields.io/badge/📖%20Ir%20a%20la%20Wiki%20Completa-1C7293?style=for-the-badge)](../../wiki)

</div>
