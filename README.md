# 📊 Entrega 5: Regresión Logística (RL)

---

## 🧠 Tema: Predicción de Viviendas Caras

---

## 🏫 Universidad del Valle de Guatemala - Campus Central  
**Facultad:** Ingeniería  
**Departamento:** Ciencias de la Computación  
**Curso:** Minería de Datos (CC3074) - Sección 10  
**Semestre:** II – 2025  
**Proyecto:** Proyecto #2  
**Entrega:** Entrega 5 – Regresión Logística  

---

## 👥 Integrantes del Grupo #1  
- **Pablo Daniel Barillas Moreno** - *Carné No. 22193*  
- **Mathew Cordero Aquino** - *Carné No. 22982*  
- **Andrés Rafael Chivalán Marroquín** - *Carné No. 21534*

---

## 📌 Descripción del Proyecto  

Se trabajó con los datos del concurso **"House Prices: Advanced Regression Techniques"** de Kaggle. El objetivo de esta entrega fue construir un modelo de **regresión logística binaria** para predecir si una vivienda es **cara** en función de variables clave.

Este análisis se construyó sobre las entregas anteriores (Árboles de decisión, Naive Bayes, KNN), utilizando los mismos conjuntos `train_set.csv` y `test_set.csv`.

---

## 🔎 Actividades Realizadas  

### 1. Creación de variables dicotómicas  
- Se transformó `SalePriceCat` (categórica: `barata`, `media`, `cara`) en 3 variables binarias:
  - `es_barata`
  - `es_media`
  - `es_cara`
- Estas variables permitieron modelar cada clase por separado.

### 2. Reutilización de conjuntos  
- Se reutilizaron los conjuntos de entrenamiento y prueba generados en entregas anteriores.
- Se aseguró la reproducibilidad con semilla fija.

### 3. Modelo de regresión logística  
- Se entrenó un modelo para predecir `es_cara` (vivienda cara o no).
- Se usaron 5 predictores clave: `OverallQual`, `GrLivArea`, `GarageCars`, `TotalBsmtSF`, `YearBuilt`.
- Validación cruzada de 10 folds, preprocesamiento (centrado, escalado, imputación) y upsampling.

### 4. Análisis del modelo  
- Se calculó el VIF para cada predictor → **no hubo multicolinealidad** (todos los VIF < 2).
- Todos los coeficientes fueron estadísticamente significativos (`p < 0.01`).
- La matriz de correlación mostró relaciones moderadas, sin colinealidades altas.
- Ajuste del modelo:
  - Accuracy (CV): 88.9%
  - AIC: 674.3
  - Reducción sustancial de la devianza

### 5. Evaluación en conjunto de prueba  
- El modelo clasificó correctamente el **92.67%** de los casos.
- Matriz de confusión:
  - `caro` predicho correctamente: 72
  - `no_caro` predicho correctamente: 143
- Kappa: 0.8385  
- Balanced Accuracy: 92.88%

### 6. Curvas de aprendizaje y sobreajuste  
- Se generaron curvas de error y precisión para entrenamiento vs prueba.
- No se observó overfitting: las curvas convergen.
- El modelo generaliza correctamente y no depende excesivamente del conjunto de entrenamiento.

---

## 🛠 Herramientas Utilizadas  

- **Lenguaje:** R  
- **Entorno:** RStudio  
- **Librerías:** `caret`, `dplyr`, `ggplot2`, `ROCR`, `car`  
- **Datos:** Kaggle House Prices (`train.csv`)  
- **Control de versiones:** GitHub  

---

## 📢 Hallazgos Destacados  

✔️ Todas las variables utilizadas en el modelo aportan significativamente a la predicción.  
✔️ El modelo no presenta multicolinealidad y se ajusta bien a los datos.  
✔️ La clasificación en el conjunto de prueba tiene una alta precisión (93%).  
✔️ No se detectó sobreajuste según las curvas de aprendizaje.  
✔️ El enfoque de clasificación binaria permitió obtener un modelo simple y potente.
