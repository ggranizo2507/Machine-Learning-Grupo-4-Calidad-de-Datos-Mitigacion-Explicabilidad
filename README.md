# 🧠 Predicción de Burnout en Desarrolladores de Software

**Modelo de Machine Learning supervisado para predecir el nivel de estrés laboral en desarrolladores, con explicabilidad (XAI), equidad algorítmica y reflexión ética.**

---

## 📋 Descripción del Proyecto

Este proyecto desarrolla un modelo de **Ridge Regression** para predecir el `stress_level` (0–100) de desarrolladores de software a partir de métricas de comportamiento laboral: horas de trabajo, bugs por día, reuniones, horas de sueño, ejercicio y consumo de cafeína.

El notebook implementa el **flujo obligatorio anti-leakage**:

```
Limpiar → Eliminar Leakage → Split TRAIN/TEST → Imputar → Scaling
```

Todo el preprocesamiento y el modelo están encapsulados en un **único Pipeline unificado**, utilizado de forma consistente en validación cruzada, GridSearch, evaluación, fairness, SHAP y LIME.

---

## 👥 Integrantes — Grupo 4

| Nombre | Rol en el proyecto |
|--------|-------------------|
| **Eduardo Alejandro Ceballos Jijón** | Introducción, EDA, Preprocesamiento |
| **Guillermo Leonidas Granizo Veintimilla** | Modelo, Evaluación, SHAP |
| **José Farid Ulloa Manzur** | Fairness, Mitigación de Sesgo, Ética |
| **Christian Xavier Valle Maridueña** | LIME, PDP, Conclusiones |

**Universidad:** UEES — Universidad de Especialidades Espíritu Santo  
**Programa:** Maestría en Machine Learning  
**Período:** 2026

---

## 📊 Resultados Principales

| Métrica | Valor |
|---------|-------|
| Modelo | Ridge Regression (α = 1.0) |
| RMSE test | **10.17 pts** (escala 0–100) |
| R² test | **0.8121** (explica el 81.2% de la varianza) |
| Gap train/test | **0.50%** (sin overfitting) |
| % dentro de ±10 pts | **67.7%** |
| Mejora vs baseline | **56.5%** |
| Errores graves (Bajo↔Alto) | **0** |

### Equidad Algorítmica (Fairness)

| Grupo sensible | Δ RMSE entre grupos | Evaluación |
|---------------|--------------------:|-----------|
| Jornada laboral (Normal/Alta/Extrema) | 1.00 pts | ✅ Equitativo |
| Edad (Junior/Mid/Senior) | 0.54 pts | ✅ Equitativo |

---

## 🗂️ Estructura del Notebook

El notebook `Burnout_Grupo4_Pipeline_Unificado.ipynb` contiene **19 celdas** organizadas en el siguiente flujo:

| # | Celda | Contenido |
|---|-------|-----------|
| 1 | Instalación | Dependencias: `fairlearn`, `shap`, `lime` |
| 2 | Imports | Todas las librerías del proyecto |
| 3 | Carga | Dataset desde Google Drive o directorio local |
| 4 | EDA | Exploración, calidad de datos, detección de leakage |
| 5 | Preprocesamiento | Flujo obligatorio + Pipeline unificado |
| 6 | Entrenamiento | CV 5-fold, GridSearchCV sobre alpha |
| 7 | Evaluación | RMSE, MAE, R², residuales, overfitting |
| 8 | Fairness | MetricFrame, DP Difference por grupo |
| 9 | Mitigación de Sesgo | Ablación de variable sensible (`age`) |
| 10 | Importancia | Coeficientes Ridge + Permutation Importance |
| 11 | PDP | Partial Dependence Plots (4 variables) |
| 12 | SHAP | Explicabilidad global e individual exacta |
| 13 | LIME | Aproximación local con análisis de fidelidad |
| 14 | Predicción | Perfiles nuevos con SHAP individual |
| 15 | Validación | 1,372 registros del test set |
| 16 | Inspección | Mejores y peores predicciones |
| 17 | Ética | Transparencia, riesgos y reflexión |
| 18 | Resumen | Métricas finales y cumplimiento de rúbrica |
| 19 | Rúbrica | Tabla completa de criterios cubiertos |

---

## 🔬 Técnicas XAI Implementadas

| Técnica | Tipo | Celda |
|---------|------|-------|
| Coeficientes Ridge | Global · Exacto | 10 |
| Permutation Importance | Global · 30 repeticiones | 10 |
| Partial Dependence Plots (PDP) | Global · Rango P5–P95 | 11 |
| SHAP (Shapley Values) | Global + Individual | 12 |
| LIME | Local · Con análisis de fidelidad | 13 |

---

## 🚀 Cómo Ejecutar

### Opción A — Google Colab (recomendado)

1. Abrir [Google Colab](https://colab.research.google.com/)
2. Subir el archivo `Burnout_Grupo4_Pipeline_Unificado.ipynb`
3. Subir el dataset `developer_burnout_dataset.csv` a `/content/`
4. Ejecutar todas las celdas en orden (`Runtime → Run all`)

### Opción B — Google Drive

1. Colocar el dataset en:  
   `My Drive/MachineLearning/TareasCompartidas/Semana4/developer_burnout_dataset.csv`
2. La Celda 3 montará Drive automáticamente si no encuentra el archivo local

### Opción C — Entorno local

```bash
pip install jupyter fairlearn shap lime scikit-learn pandas numpy matplotlib seaborn scipy
jupyter notebook Burnout_Grupo4_Pipeline_Unificado.ipynb
```

---

## 📦 Dependencias

```
python >= 3.9
scikit-learn >= 1.2
pandas >= 1.5
numpy >= 1.23
matplotlib >= 3.6
seaborn >= 0.12
scipy >= 1.9
fairlearn >= 0.9
shap >= 0.42
lime >= 0.2
```

---

## 📁 Estructura del Repositorio

```
├── Burnout_Grupo4_Pipeline_Unificado.ipynb   # Notebook principal
├── developer_burnout_dataset.csv             # Dataset (7,000 registros)
├── README.md                                 # Este archivo
├── LICENSE                                   # Licencia MIT
└── wiki/                                     # Documentación extendida
    ├── 01-descripcion-del-proyecto.md
    ├── 02-dataset.md
    ├── 03-metodologia.md
    ├── 04-resultados.md
    ├── 05-explicabilidad-xai.md
    ├── 06-fairness.md
    └── 07-etica.md
```

---

## ⚠️ Nota Ética

Este modelo es una herramienta de **alerta temprana para bienestar laboral**, no un sistema de evaluación o sanción. Su uso responsable requiere:

- Consentimiento informado de los empleados
- Supervisión humana en toda decisión
- Comunicar siempre el intervalo de error (± 10 pts)
- Auditoría periódica de sesgo por grupos sensibles
- Cumplimiento de la LOPDP (Ecuador) y principios de IA ética

---

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**. Ver [LICENSE](LICENSE) para más detalles.
