# 📊 Entrega 6: Máquinas de Vectores de Soporte (SVM)

---

# 🧠 Proyecto de Clasificación Multiclase: Predicción de Categorías de Precio de Viviendas

---

## 🏫 Universidad del Valle de Guatemala - Campus Central  
**Facultad:** Ingeniería  
**Departamento:** Ciencias de la Computación  
**Curso:** Minería de Datos (CC3074) - Sección 10  
**Semestre:** I – 2025  
**Proyecto:** Proyecto #2  
**Entrega:** Entrega 6 – Máquinas de Vectores de Soporte (SVM)  

---

## 👥 Integrantes del Grupo #1  
- **Pablo Daniel Barillas Moreno** - *Carné No. 22193*  
- **Mathew Cordero Aquino** - *Carné No. 22982*  

---

## 📌 Descripción del Proyecto  

En esta entrega se utilizó el algoritmo de **Máquinas de Vectores de Soporte (SVM)** para predecir si una vivienda es **barata**, **media** o **cara**, utilizando el conjunto de datos de Kaggle **“House Prices: Advanced Regression Techniques”**.  
El modelo se entrenó sobre los conjuntos `train_set.csv` y `test_set.csv`, previamente definidos en entregas anteriores.

---

## 🔎 Actividades Realizadas  

### 1️⃣ Serie 1: Reutilización de conjuntos  
- Se cargaron `train_set.csv` (937 observaciones) y `test_set.csv` (232 observaciones).
- Se validó que `SalePriceCat` mantuviera la distribución balanceada: 313 baratas, 312 medias, 312 caras.

### 2️⃣ Serie 2: Preprocesamiento para SVM  
- Se eliminaron columnas irrelevantes (`Id`, `SalePrice`).
- Las variables categóricas fueron transformadas en **dummies** con `dummyVars()`.
- Se centraron y escalaron los datos con `preProcess()`.
- Se eliminaron predictores con varianza cero y se alinearon columnas entre train y test.

### 3️⃣ Serie 3: Entrenamiento del modelo SVM multiclase  
- Se entrenó un modelo **SVM lineal** con `SalePriceCat` como respuesta.
- Se usaron 207 predictores y validación cruzada de 10 folds.
- Resultados del modelo lineal:
  - **Accuracy:** 85.78%
  - **Kappa:** 0.7866
- El modelo mostró buen rendimiento, sin errores críticos.

### 4️⃣ Serie 4: Comparación con otros kernels  
- Se entrenaron 3 modelos de SVM:
  - **SVM lineal:** Accuracy 85.8%
  - **SVM radial:** Accuracy 87.0%
  - **SVM polinomial:** Accuracy 87.0%
- Se exploraron diferentes valores de **C**, **sigma** y **degree**.
- Se utilizó validación cruzada de 3 folds para reducir tiempo de cómputo.

### 5️⃣ Serie 5: Evaluación sobre conjunto de prueba  
- Se realizaron predicciones sobre `test_set.csv`.
- Se generaron y analizaron matrices de confusión para cada modelo.
- Las mejores métricas fueron:
  - **Balanced Accuracy (SVM radial):** 91.95% (barata), 94.50% (cara), 84.44% (media)
  - **Kappa (SVM radial/polinomial):** 0.806

### 6️⃣ Serie 6: Visualización de Resultados  
- Se generaron **gráficos de matriz de confusión** con `ggplot2`.
- Se compararon visualmente las predicciones correctas y los errores por clase.

### 7️⃣ Serie 7: Análisis de Overfitting  
- Al comparar el desempeño entre entrenamiento y prueba no se observaron diferencias sustanciales.
- Se concluyó que los modelos están **bien ajustados** y no presentan overfitting.
- Se sugirieron mejoras como regularización o reducción de predictores para futuros escenarios.

---

## 📦 Limpieza y Transformación de Datos  

- Conversión de variables categóricas a factores.
- Dummificación con `caret::dummyVars()`.
- Eliminación de variables con varianza cero.
- Alineación de columnas entre `train` y `test`.
- Estandarización de datos (centrado y escalado).

---

## 🛠 Herramientas Utilizadas  

- **Lenguaje:** R  
- **Entorno:** RStudio  
- **Librerías:** `caret`, `dplyr`, `ggplot2`, `e1071`, `doParallel`  
- **Datos:** Kaggle House Prices (`train.csv`)  
- **Control de versiones:** GitHub  

---

## 📢 Hallazgos Destacados  

✔️ Los tres modelos de SVM alcanzaron **precisiones superiores al 85%**.  
✔️ El **SVM radial y polinomial** obtuvieron mejor desempeño general que el lineal.  
✔️ La clase más difícil de predecir fue **media**, con menor sensibilidad.  
✔️ No se detectó **sobreajuste**, gracias a la validación cruzada y preprocesamiento riguroso.  
✔️ Las matrices de confusión y sus visualizaciones permitieron entender los errores comunes.  
✔️ El pipeline de SVM queda listo para ser comparado con modelos como Random Forest o XGBoost.
