# 🍄 Taller de Aprendizaje Automático No Supervisado (Mushrooms Dataset)
**Autor:** Alfonso Bermúdez  
**Bootcamp IA – Proyecto Individual**

---

## 📘 Descripción

Este repositorio contiene un taller práctico de **aprendizaje automático no supervisado**, usando técnicas de **PCA** y **K-Means Clustering**, junto con una comparativa con un modelo supervisado (**Random Forest** optimizado con GridSearchCV).

Este proyecto explora el clásico **dataset de hongos (Mushroom Dataset)** del repositorio UCI para analizar si las especies pueden clasificarse como **comestibles o venenosas** en función de sus características morfológicas.  

---

## 📂 Dataset

Puedes obtener el dataset desde el siguiente enlace:

🔗 [Mushroom Dataset - UCI Repository](https://archive.ics.uci.edu/ml/datasets/Mushroom)

- **Instancia:** Cada fila representa un hongo.  
- **Variables:** Todas son **categóricas** (forma, color, olor, tipo de anillo, etc.).  
- **Variable objetivo (`class`)**: Binaria — `e` (edible/comestible) o `p` (poisonous/venenoso).  
- Se detectaron valores faltantes en la variable `stalk-root`, imputados con la **moda**.

---

## 🧠 Objetivos del taller

- Explorar y limpiar un dataset categórico con valores faltantes.  
- Aplicar **One-Hot Encoding** para variables categóricas.  
- Reducir la dimensionalidad con **PCA (Análisis de Componentes Principales)**.  
- Identificar patrones ocultos mediante **K-Means** y **t-SNE**.  
- Comparar resultados con un modelo **supervisado (Random Forest)** optimizado con **GridSearchCV**.

---

## ⚙️ Pipeline metodológico

1. **EDA (Exploratory Data Analysis)**  
   - Identificación de valores nulos (`?`) en `stalk-root`.  
   - Imputación por moda (manteniendo el tamaño y balance del dataset).  
   - Eliminación de columnas no informativas (`veil-type`).

2. **Preprocesamiento**  
   - Conversión a formato numérico mediante *One-Hot Encoding*.  
   - Escalado de variables con `StandardScaler`.

3. **PCA (Reducción de dimensionalidad)**  
   - Se conservaron las dos primeras componentes principales (PC1 y PC2),  
     que explican el **16.5 %** de la varianza total.  
   - Permite visualizar una separación parcial entre las dos clases.

4. **Clustering (No supervisado)**  
   - El **método del codo** sugiere *k ≈ 4-5*, mientras que el **coeficiente silhouette** apunta a *k ≈ 9-10*.  
   - Forzando *k = 2*, se obtiene una **coincidencia del 89 %** con las clases reales.  
   - Esto confirma que el dataset presenta una estructura separable, aunque no perfectamente lineal.  
   - El **t-SNE** refuerza esta conclusión mostrando dos grupos principales con ligeros solapamientos.

5. **Clasificación supervisada (Random Forest)**  
   - Entrenamiento y optimización con **GridSearchCV**.  
   - Precisión en test: **≈ 100 %**.  
   - Las variables más influyentes:  
     - `odor` (olor) → casi determinante.  
     - `spore-print-color` (color de esporas).  
     - `ring-type` y `gill-size` (características estructurales).

---

## 🧩 Resultados comparativos

| Método | Tipo | Métrica | Resultado | Observaciones |
|:--|:--|:--|:--:|:--|
| **PCA (2D)** | Reducción | Varianza total explicada | 16.5 % | Separación parcial entre clases. |
| **K-Means** | No supervisado | Accuracy (k = 2) | 0.892 | Detecta dos grupos con solapamientos leves. |
| **t-SNE** | No supervisado | Visualización | — | Dos grupos visibles con fronteras difusas. |
| **Random Forest** | Supervisado | Accuracy | 0.999 | Clasificación perfecta gracias a etiquetas reales. |

---

## 🔍 Conclusiones finales

- El conjunto **presenta una estructura naturalmente separable** en dos grandes grupos (comestibles y venenosos).  
- La variable **`odor`** tiene una capacidad predictiva excepcional: puede casi determinar la clase por sí sola.  
- **PCA** y **t-SNE** permiten observar esta separación desde la perspectiva no supervisada.  
- **K-Means** logra identificar grupos coherentes sin conocer las etiquetas (≈ 89 % de coincidencia).  
- **Random Forest**, al incorporar las etiquetas, alcanza una clasificación prácticamente perfecta (**≈ 100 %**).  

> 🔹 **Conclusión general:**  
> Los métodos no supervisados revelan patrones internos consistentes,  
> mientras que el modelo supervisado confirma y perfecciona esa estructura.  
> Ambos enfoques se complementan: **el no supervisado explora**,  
> **el supervisado predice** con precisión.

---

## 🧰 Tecnologías utilizadas

- Python 3.13  
- Pandas / NumPy  
- Seaborn / Matplotlib  
- Scikit-learn (`PCA`, `KMeans`, `RandomForestClassifier`, `GridSearchCV`, `t-SNE`)  
- JupyterLab  

---

## 📁 Estructura del proyecto

```
Proyecto8_unsupervised_ml_Alfonso_Bermudez/
│
├── notebooks/
│   └── EDA_unsupervised_ml_mushrooms.ipynb
├── data/
│   └──agaricus-lepiota.data     <-- dataset origial de UCI (no subido al repositorio)
├── docs/
├── src/
├── .gitignore
├── requirements.txt
└── README.md
```