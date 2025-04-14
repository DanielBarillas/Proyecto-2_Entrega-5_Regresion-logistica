# 📊 Entrega 5: Regresión Logística (RL)

---

# 🧠 Proyecto de Regresión Logística: Predicción de Viviendas Caras

---

## 🏫 Universidad del Valle de Guatemala - Campus Central  
**Facultad:** Ingeniería  
**Departamento:** Ciencias de la Computación  
**Curso:** Minería de Datos (CC3074) - Sección 10  
**Semestre:** I – 2025  
**Proyecto:** Proyecto #2  
**Entrega:** Entrega 5 – Regresión Logística  

---

## 👥 Integrantes del Grupo #1  
- **Pablo Daniel Barillas Moreno** - *Carné No. 22193*  
- **Mathew Cordero Aquino** - *Carné No. 22982*  

---

## 📌 Descripción del Proyecto  

Se trabajó con los datos del concurso **"House Prices: Advanced Regression Techniques"** de Kaggle. El objetivo de esta entrega fue construir un modelo de **regresión logística binaria** para predecir si una vivienda es **cara** en función de variables clave.  
Este análisis se basó en entregas anteriores (Árboles de Decisión, Naive Bayes, KNN), utilizando los mismos conjuntos `train_set.csv` y `test_set.csv`.

---

## 🔎 Actividades Realizadas  

### 🔢 Serie 1: Creación de Variables Dicotómicas  
- Se generaron 3 variables binarias: `es_barata`, `es_media`, `es_cara`, a partir de `SalePriceCat`.
- Se verificó que las etiquetas fueran correctas mediante tablas cruzadas.

### 📁 Serie 2: Reutilización de los Conjuntos  
- Se usaron los mismos archivos `train_set.csv` (937 casos) y `test_set.csv` (232 casos) definidos con una semilla fija.

### 📈 Serie 3: Modelo de Regresión Logística  
- Se entrenó un modelo binario (`es_cara`) usando validación cruzada (10-fold) y balanceo (`upsampling`).
- Se incluyeron 5 variables predictoras: `OverallQual`, `GrLivArea`, `GarageCars`, `TotalBsmtSF`, `YearBuilt`.

### 📊 Serie 4: Análisis del Modelo  
- Se analizó la multicolinealidad con **VIF**: todos los valores fueron menores a 2.
- Se analizó la **significancia estadística** de los coeficientes (todos con `p < 0.01`).
- Se graficó la **matriz de correlación** para detectar redundancia entre predictores.
- El modelo mostró buen ajuste:
  - **Accuracy (CV)**: 88.9%  
  - **Kappa**: 0.76  
  - **AIC**: 674.3

### 🧪 Serie 5: Evaluación en Conjunto de Prueba  
- Accuracy: **92.67%**
- Balanced Accuracy: **92.88%**
- Sensibilidad: **93.5%**, Especificidad: **92.2%**
- Kappa: **0.8385**
- La matriz de confusión mostró solo **17 errores de clasificación**.

### 📉 Serie 6: Curvas de Aprendizaje y Overfitting  
- Se entrenaron modelos sobre subconjuntos crecientes del entrenamiento.
- Se graficaron curvas de error y precisión.
- No se detectó **sobreajuste**: las curvas convergen y se mantienen estables.

### 🔍 Serie 7: Evaluación Visual del Modelo  
- Se utilizó `ROCR` para graficar curvas ROC y comparar precisión.
- El AUC fue alto, reforzando la buena capacidad discriminativa del modelo.

### 📦 Serie 8: Análisis de Variables Relevantes  
- Se filtraron las 5 variables más significativas tras pruebas previas.
- Estas mostraron fuerte correlación con `SalePrice` y alta importancia en modelos anteriores.

### 🧹 Serie 9: Transformación de `SalePrice`  
- `SalePrice` fue categorizada en terciles (`barata`, `media`, `cara`) usando cuantiles.
- Se verificó la distribución balanceada: aprox. 1/3 en cada categoría.

### 📉 Serie 10: Validación Cruzada  
- Se mantuvo la metodología de validación cruzada 10-fold con balanceo.
- Se evitó la varianza alta entre particiones, asegurando reproducibilidad.

### 📤 Serie 11: Preparación Final de Predicciones  
- Se aplicó el modelo sobre el conjunto de prueba para predecir `es_cara`.
- Las predicciones fueron almacenadas y comparadas con valores reales para evaluación.

---

## 📦 Limpieza y Transformación de Datos  

- Categorización de `SalePrice` en 3 niveles con terciles.
- Normalización y estandarización de variables numéricas.
- Imputación de valores faltantes con la mediana.
- Conversión de variables binarias a factores (`factor`) para uso con `caret`.

---

## 🛠 Herramientas Utilizadas  

- **Lenguaje:** R  
- **Entorno:** RStudio  
- **Librerías:** `caret`, `dplyr`, `ggplot2`, `ROCR`, `car`  
- **Datos:** Kaggle House Prices (`train.csv`)  
- **Control de versiones:** GitHub  
## 📢 Hallazgos Destacados  

✔️ Todas las variables utilizadas en el modelo son significativas (`p < 0.01`).  
✔️ No hay multicolinealidad según VIF.  
✔️ Accuracy en prueba superior al 92%.  
✔️ No se observó overfitting.  
✔️ La estrategia de clasificación binaria mostró un excelente desempeño y balance.  
