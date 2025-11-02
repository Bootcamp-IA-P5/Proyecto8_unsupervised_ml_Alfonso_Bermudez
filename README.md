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

## 🧩 Resultados y análisis comparativo

Durante el análisis se observaron distintos comportamientos según la técnica aplicada.  
El resumen siguiente refleja tanto los **resultados obtenidos** como las **decisiones razonadas** en cada fase:

| Método | Tipo | Métrica / Resultado | Observaciones |
|:--|:--|:--|:--|
| **PCA (2D)** | Reducción | Varianza total explicada: **16.5 %** | Las dos primeras componentes principales (PC1, PC2) permiten visualizar cierta separación entre *comestibles* y *venenosos*, aunque con solapamientos. |
| **K-Means (Exploratorio)** | No supervisado | Método del codo → **k ≈ 4–5**  | La inercia se estabiliza a partir de k=4–5, indicando que podrían existir subgrupos dentro de las clases principales. |
| **Coeficiente Silhouette** | No supervisado | Máx. en **k = 9**, valor medio **≈ 0.21** | Sugiere una estructura interna algo más compleja y difusa; los clusters no son totalmente compactos. |
| **K-Means (Forzado k=2)** | No supervisado | Accuracy ≈ **89 %** respecto a las clases reales | Se observa una buena correspondencia con las etiquetas (*edible / poisonous*), aunque con cierto solapamiento. |
| **t-SNE** | No supervisado | Visualización 2D no lineal | Refuerza la existencia de dos grupos principales con fronteras poco definidas. |
| **Random Forest (GridSearchCV)** | Supervisado | Accuracy ≈ **99.9 %** | Clasificación prácticamente perfecta al usar las etiquetas reales. |

---

## 🔍 Interpretación global y conclusiones

- El **PCA** mostró que las dos primeras componentes solo explican el **16.5 %** de la varianza,  
  lo cual es esperable en datasets categóricos con muchas variables codificadas.  
  Aun así, permitió identificar una **separación parcial** entre las clases.
- El **K-Means** reveló una estructura interna **no perfectamente binaria**, con posibles **subgrupos naturales** dentro de las clases *edible* y *poisonous* (k ≈ 4–5).  
  Esto puede deberse a combinaciones específicas de variables como *odor*, *color de esporas* o *hábitat*.
- Al **forzar k=2**, los clusters se alinearon en un **89 %** con las etiquetas reales,  
  lo que confirma una **separación latente**, aunque con zonas de intersección.
- El **coeficiente silhouette** relativamente bajo (≈ 0.21) sugiere que los límites entre grupos son difusos,  
  probablemente por la alta dimensionalidad y el solapamiento entre características visuales.
- El modelo **Random Forest**, en cambio, logró una precisión **casi perfecta (~100%)**,  
  lo que confirma que el conjunto de variables —especialmente `odor`, `spore-print-color` y `ring-type`—  
  contienen suficiente información para discriminar las clases con exactitud.

> 🧠 En resumen:
> - Los métodos **no supervisados** evidencian patrones coherentes, pero imperfectos.  
> - El modelo **supervisado** aprovecha esa estructura subyacente para lograr una clasificación exacta.  
> - Este contraste refuerza la importancia de combinar **análisis exploratorio** con **modelos predictivos**,  
>   para comprender tanto la estructura como el comportamiento de los datos.

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