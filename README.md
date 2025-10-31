# 🍄 Taller de Aprendizaje Automático No Supervisado (Mushrooms Dataset)
**Autor:** Alfonso Bermúdez  
**Bootcamp IA – Proyecto Individual**

---

### 📘 Descripción

Este repositorio contiene un taller práctico de **aprendizaje automático no supervisado**, usando técnicas de **PCA** y **K-Means Clustering**, junto con una comparativa con un modelo supervisado (**Random Forest** optimizado con GridSearchCV).

El objetivo es analizar si los hongos pueden clasificarse como **comestibles o venenosos** en función de sus características morfológicas.

---

## 📂 Dataset

Puedes obtener el dataset desde el siguiente enlace:

🔗 [Mushroom Dataset - UCI Repository](https://archive.ics.uci.edu/ml/datasets/Mushroom)

- **Instancia:** Cada fila representa un hongo.
- **Variables:** Todas son **categóricas** (forma, color, olor, etc.).
- **Variable objetivo (`class`)**: Binaria — `e` (edible/comestible) o `p` (poisonous/venenoso).

---

## 🧠 Objetivos del taller

- Cargar y explorar un dataset categórico complejo.
- Tratar valores nulos y eliminar columnas no informativas.
- Codificar variables categóricas usando **One-Hot Encoding**.
- Reducir dimensionalidad con **PCA (Análisis de Componentes Principales)**.
- Aplicar **K-Means Clustering** para detectar estructuras ocultas en los datos.
- Comparar el rendimiento del modelo no supervisado con un modelo supervisado (**Random Forest**).

---

### 📂 Estructura del proyecto

```
Proyecto8_unsupervised_ml_Alfonso_Bermudez/
│
├── notebooks/
│   └── EDA_unsupervised_ml_mushrooms.ipynb
├── data/
├── docs/
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```

---

## 🔧 Tecnologías utilizadas

- Python 3.13.9  
- Pandas / NumPy
- Seaborn / Matplotlib
- Scikit-learn (`PCA`, `KMeans`, `RandomForestClassifier`, `GridSearchCV`)
- JupyterLab

---

## 🗂️ Contenido del notebook

### 1. 📥 Carga y exploración de datos
- Visualización general del dataset.
- Conteo de valores nulos y valores únicos por variable.
- Eliminación de columnas constantes o poco informativas.

### 2. 🧼 Preprocesamiento
- Imputación o eliminación de valores faltantes.
- Conversión de variables categóricas con **OneHotEncoder**.
- Separación entre `X` (features) e `y` (class).

### 3. 🧪 PCA (Análisis de Componentes Principales)
- Reducción de dimensionalidad a 2 componentes.
- Visualización de los datos en 2D.
- Evaluación visual de separabilidad.

### 4. 🌳 Clasificación supervisada (Random Forest)
- Entrenamiento de un modelo de clasificación.
- Evaluación con métricas de precisión.
- Estudio del impacto del número de componentes en el rendimiento del modelo.

### 5. 🔍 Clustering con K-Means
- Determinación del número óptimo de clusters (método del codo).
- Entrenamiento y visualización de clusters.
- Evaluación de la correspondencia entre clusters y clases reales (sin usar las etiquetas).

### 📊 Resultados obtenidos

  **Supervisado** `Random Forest`:  **Accuracy: $\approx 1.0000$** El problema es trivialmente clasificable con etiquetas. |
| **No Supervisado** `K-Means`:  **ARI: $\approx 0.99 - 1.00$** Coincidencia casi perfecta con las clases reales. |
| **Reducción** `PCA (2D)`: Separa las clases de forma visible. La información crucial se concentra eficientemente. |



### 🎯 Conclusiones

- **KMeans (no supervisado)** logró ≈ **90% de precisión** agrupando hongos **sin saber** si eran comestibles o venenosos.

- **Random Forest (supervisado)** logró **100%** porque **sí sabía** las respuestas correctas durante el entrenamiento.

Cuando tenemos datos etiquetados (supervisado), podemos alcanzar mejores resultados, pero el no supervisado es increíblemente útil cuando **no tenemos etiquetas** o queremos **descubrir grupos** que no conocíamos.

