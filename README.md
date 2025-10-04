Perfecto 🚀. Te armo un **README.md** base adaptado para tu notebook `FNN_en_Series_de_Tiempo.ipynb`. Lo estructuré para que documente claramente tu flujo: desde la API de Banxico hasta la FFNN, entrenamiento, resultados y conclusiones. Solo tendrías que ir llenando los huecos con tus métricas, gráficas y detalles específicos.

---

# 📌 Predicción del Tipo de Cambio (MXN/USD) con FFNN

## 📖 Descripción del proyecto

Este proyecto implementa una **Red Neuronal Feed Forward (FFNN)** para predecir el tipo de cambio FIX (MXN/USD) utilizando datos de la **API de Banxico**.

El objetivo es comparar el desempeño de un modelo de aprendizaje profundo frente a un modelo ingenuo, explorando la capacidad de la FFNN para aprender patrones no lineales a partir de rezagos históricos de la serie.

---

## ⚙️ Flujo de trabajo

### 1. Obtención de datos

* Fuente: **API de Banxico**.
* Serie utilizada: Tipo de cambio FIX.
* Periodo: Últimos **2 años**.
* División de conjuntos:

  * **Train:** todos los datos excepto los últimos 15 días.
  * **Test:** últimos 15 días.

### 2. Preparación de datos

* Normalización: `MinMaxScaler` entre `[0,1]`.
* Construcción de ventanas deslizantes (`sliding windows`) con **n rezagos** (ejemplo: 10, 15, 30 días).
* Justificación del tamaño de ventana: *(explicar aquí la razón del número elegido).*

### 3. Modelo FFNN

* Implementado con **Keras/TensorFlow**.
* Arquitectura:

  * Varias capas densas ocultas con activación **ReLU/tanh**.
  * Capa de salida con 1 neurona (predicción del tipo de cambio).
* Hiperparámetros:

  * Capas: *[indicar número de capas/neuronas]*
  * Epochs: *[ej. 100]*
  * Batch size: *[ej. 16/32]*
  * Optimizador: Adam.
* Justificación: *(explicar por qué se eligieron estos valores).*

### 4. Entrenamiento y predicción

* Entrenamiento con el **train set**.
* Predicción sobre los últimos 15 días (**test set**).
* Desnormalización de resultados a escala original (MXN/USD).

### 5. Evaluación

* Métricas:

  * **MAPE (Mean Absolute Percentage Error)**.
* Visualizaciones con **Plotly**:

  * Serie real vs. predicha.
  * Comparación train vs. test.

---

## 📊 Resultados

* **MAPE obtenido:** *(llenar con valor real).*
* Gráficas:

  * 📈 Tipo de cambio real vs. predicho.
  * 📉 Comparación train/test.

---

## 🔎 Conclusiones

1. **Ventana temporal óptima:** *(explicar cuál funcionó mejor y por qué).*
2. **Hiperparámetros más sensibles:** *(ej. número de neuronas, epochs, etc.).*
3. **Comparación con modelo ingenuo:** *(qué tanto mejora respecto al naïve).*
4. **Propuestas de mejora:**

   * Incluir más años de datos históricos.
   * Incorporar variables exógenas (ej. inflación, tasas de interés, S&P500).
   * Probar modelos más avanzados (LSTM, GRU).

---


