

# 📌 Predicción del Tipo de Cambio (MXN/USD) con FFNN

## 📖 Descripción del proyecto

Este proyecto implementa una **Red Neuronal Feed Forward (FFNN)** para predecir el **tipo de cambio FIX (MXN/USD)** utilizando datos obtenidos de la **API de Banxico**.

El modelo se entrena con datos históricos y genera predicciones para los últimos días, comparando su desempeño frente a un modelo ingenuo. Se busca evaluar la capacidad de la red neuronal para capturar patrones no lineales en series temporales financieras.

---

## ⚙️ Flujo de trabajo

### 1. Obtención de datos

* Fuente: **API de Banxico**.
* Serie utilizada: tipo de cambio FIX.
* Periodo: últimos **2 años**.
* Conjuntos de datos:

  * **Train set:** todos los datos excepto los últimos 15 días.
  * **Test set:** últimos 15 días (para evaluación).

### 2. Preparación de datos

* Normalización: `MinMaxScaler` para escalar los valores en rango `[0,1]`.
* Creación de ventanas deslizantes (`sliding windows`) con diferentes rezagos (10, 15 y 30 días).
* Justificación: se probaron distintos tamaños para balancear entre captura de patrones y evitar sobreajuste.

### 3. Modelo FFNN

* Framework: **Keras / TensorFlow**.
* Arquitectura:

  * Capas densas ocultas con activación **ReLU**.
  * Capa de salida: 1 neurona (predicción del valor del tipo de cambio).
* Hiperparámetros:

  * Epochs: **100**
  * Batch size: **16**
  * Optimizador: **Adam**
* Justificación: valores seleccionados tras pruebas iniciales que mostraron estabilidad y convergencia adecuada.

### 4. Entrenamiento y predicción

* Entrenamiento en el **train set**.
* Predicción sobre los últimos 15 días (**test set**).
* Desnormalización de resultados para regresar a escala original (MXN/USD).

### 5. Evaluación

* Métrica: **MAPE (Mean Absolute Percentage Error)**.
* Visualización de resultados con **Plotly**:



---

## 📊 Resultados

* El modelo logra capturar la tendencia general y movimientos de corto plazo del tipo de cambio.
* **MAPE obtenido:** *(inserta aquí tu valor del notebook, ej. ~2-3%)*

📈 **Gráfica de resultados (ejemplo actual):**

![Predicción FFNN](2d8c3039-7984-4803-baec-b9ed50a26a90.png)

---

## 🔎 Conclusiones

1. **Ventana óptima:**
   Se observó que ventanas entre **15–30 días** ofrecieron mejor balance entre precisión y estabilidad.

2. **Hiperparámetros sensibles:**
   El número de neuronas en la capa oculta y el batch size tuvieron mayor impacto en la estabilidad del modelo.

3. **Comparación con modelo ingenuo:**
   El FFNN mejoró la precisión frente a un modelo naïve (último valor como predicción), especialmente en la tendencia descendente reciente.

4. **Posibles mejoras:**

   * Usar más datos históricos (5–10 años).
   * Incluir variables exógenas (inflación, tasas de interés, S&P500, etc.).
   * Probar arquitecturas más avanzadas (LSTM, GRU).

---

## 📂 Entregables

* `FNN_en_Series_de_Tiempo.ipynb` → Notebook con:

  * Código documentado.
  * Gráficas interactivas con Plotly.
  * Reporte en Markdown (este README).

---

¿Quieres que también te arme un **mini resumen en inglés** al final del README para que quede bilingüe (más académico/profesional), o prefieres dejarlo solo en español?
