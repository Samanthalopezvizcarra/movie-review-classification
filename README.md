# 🎬 Movie Review Sentiment Classification

Proyecto para clasificar automáticamente reseñas de películas como **positivas o negativas** utilizando técnicas de NLP y modelos de machine learning.

---

## 📘 Descripción del proyecto
**Film Junky Union**, una comunidad para aficionados del cine clásico, quiere filtrar y categorizar reseñas de películas automáticamente.  
Se trabajó con el dataset `imdb_reviews.tsv`, que contiene reseñas etiquetadas como positivas (`1`) o negativas (`0`).  

**Objetivo:** Alcanzar un **F1 ≥ 0.85** en el conjunto de prueba.

---

## 🗂 Dataset
Archivo: `imdb_reviews.tsv`  

**Campos principales:**
- `review` — texto de la reseña  
- `pos` — objetivo (0 = negativo, 1 = positivo)  
- `ds_part` — parte del dataset (`entrenamiento` / `prueba`)  

Fuente: Maas et al., 2011 (ACL 2011)

---

## 🛠️ Proceso del proyecto

### 1. Preparación de datos
- Carga y exploración de datos  
- Análisis exploratorio para identificar desequilibrio de clases  
- Preprocesamiento de texto usando NLTK y spaCy  

### 2. Modelado
Se entrenaron al menos tres modelos diferentes:  
- **Dummy** – línea base (F1=0)  
- **TF-IDF + Regresión Logística** (NLTK y spaCy) – Accuracy y F1 ≈ 0.88–0.92  
- **spaCy + TF-IDF + LGBMClassifier** – sobreajuste en train, métricas en test similares a la regresión logística  

### 3. Evaluación
- Métricas: F1, Accuracy, ROC AUC, APS  
- Comparación de predicciones en reseñas individuales para observar calibración y sensibilidad a opiniones mixtas  

---

## 📊 Observaciones
- Todos los modelos superan ampliamente al Dummy  
- NLTK tiende a asignar probabilidades más bajas en casos positivos moderados  
- spaCy es más sensible a opiniones equilibradas, asignando scores más altos  
- LGBM clasifica con mayor agresividad, aumentando scores en casos ambiguos  
- Incrementar la complejidad no aportó mejoras significativas frente a TF-IDF + Regresión Logística  

---

## 🏆 Conclusión
- TF-IDF + Regresión Logística (NLTK o spaCy) es **suficiente para alta precisión**  
- Modelos más complejos como LGBM no mejoran significativamente los resultados y pueden sobreajustar  
- El sistema permite detectar de manera confiable críticas negativas para mejorar la experiencia de los usuarios  

---

## 🧰 Tecnologías utilizadas
- Python  
- pandas · numpy  
- scikit-learn · LightGBM  
- NLTK · spaCy  
- matplotlib / seaborn  
