# 📊 Reto: Clasificación en Mercadotecnia Telefónica

## <b> Puedes revisar el codigo en GoogleColab </b>
[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ADRIANVM117/TEC_MTY_PORTAFOLIO/blob/main/Mercadotecnia_Telefónica/Solucion_Reto_SC_63_ADRIAN_VAZQUEZ.ipynb)

## 🎯 Objetivo

Predecir si un cliente aceptará contratar un depósito a plazo fijo (`y`) con base en los datos de campañas telefónicas previas. Este es un problema de **clasificación binaria**.

---

## 🔍 Análisis Exploratorio (EDA)

### ✅ Principales hallazgos:

1. **Variable objetivo `y` es binaria**: yes / no ⇒ problema de clasificación.
2. **Clases moderadamente balanceadas**: ~57% "no", ~43% "yes".
3. **Presencia de múltiples variables categóricas**: job, marital, education, etc.
4. **Variables numéricas sesgadas y con outliers**: balance, duration, pdays.
5. **Relaciones no lineales** entre variables y la clase objetivo (especialmente `duration`, `pdays`).

---

## 🧠 Modelos Desarrollados

Se entrenaron dos modelos base para comparación:

| Modelo                | Detalles                                 |
|-----------------------|-------------------------------------------|
| **Regresión Logística** | Modelo interpretable, baseline clásico.  |
| **Red Neuronal MLP**    | Captura no linealidades complejas.       |

**Preprocesamiento aplicado:**
- Codificación One-Hot para variables categóricas.
- Escalado MinMax para variables numéricas.
- División de datos en `train`, `validation`, y `test`.

---

### **6.a Justifica el uso de LabelEncoder o OneHotEncoder**

Se utilizó **OneHotEncoder** para transformar las variables categóricas debido a que estas no tienen un orden intrínseco (por ejemplo, `job`, `marital`, `education`, `contact`). OneHotEncoder permite representar cada categoría como una columna binaria, lo que evita introducir relaciones numéricas artificiales entre las categorías, algo que podría ocurrir si se usara LabelEncoder. Esto es especialmente importante en modelos lineales como la Regresión Logística, que pueden verse influenciados por escalas numéricas mal interpretadas.

Para algunas variables binarias (`yes` / `no`), como `default`, `housing` y `loan`, se utilizó **LabelEncoder** por su simplicidad, ya que estas variables ya representan un valor booleano natural.

---

## 📈 Resultados Comparativos

### Conjunto de Validación

| Métrica          | Regresión Logística | Red Neuronal (MLP) |
|------------------|---------------------|---------------------|
| Accuracy         | 0.83                | 0.81                |
| Precision (1)    | 0.79                | 0.75                |
| Recall (1)       | 0.81                | 0.82                |
| F1-score (1)     | 0.80                | 0.79                |
| AUC              | **0.90**            | 0.88                |

### Conjunto de Prueba

| Métrica          | Regresión Logística | Red Neuronal (MLP) |
|------------------|---------------------|---------------------|
| Accuracy         | 0.83                | 0.82                |
| Precision (1)    | 0.78                | 0.77                |
| Recall (1)       | 0.81                | 0.82                |
| F1-score (1)     | 0.80                | 0.79                |
| AUC              | **0.90**            | 0.89                |

---

## ✅ Conclusión y Recomendación Final

- Ambos modelos **generalizan bien**, sin sobreajuste.
- La **regresión logística** muestra:
  - Mejor precisión y f1-score.
  - Mayor capacidad discriminativa (AUC = 0.90).
  - Interpretabilidad y eficiencia.
- La **red neuronal** tiene mejor recall, útil si se prioriza captar más clientes positivos.

> 🔵 **Modelo elegido: Regresión Logística**, por su desempeño sólido, interpretabilidad y balance entre precisión y sensibilidad.

---

### **13.a Conclusiones del problema: uso de técnicas de inteligencia artificial en problemas de mercadotecnia**

Las técnicas de inteligencia artificial, como la **Regresión Logística** y las **Redes Neuronales**, permiten analizar grandes volúmenes de datos de clientes y campañas de manera eficiente para **predecir comportamientos**, como la probabilidad de que un cliente contrate un producto financiero.

En este caso, observamos que ambos modelos alcanzaron métricas de desempeño sobresalientes (AUC ≈ 0.90), lo cual indica que pueden identificar patrones útiles en los datos históricos para apoyar la **toma de decisiones en marketing**, optimizando recursos y enfocando los esfuerzos en los clientes con mayor probabilidad de conversión.

En resumen, la IA representa una herramienta poderosa para mejorar el **retorno de inversión (ROI)** en campañas de mercadotecnia y personalizar estrategias de contacto con base en el comportamiento histórico de los usuarios.

---

## 📁 Archivos entregables

- `EDA.pdf / notebook.ipynb`: Análisis exploratorio detallado.
- `models.py`: Entrenamiento de regresión logística y MLP.
- `metrics_report.txt`: Resultados de validación y prueba.
- `plots/`: Gráficas EDA, curvas ROC, etc.

---

## 👨‍💻 Autor

**Adrián Vázquez**  
Data Scientist | Actuario | Python ML Developer  
[LinkedIn](#) | [GitHub](#)
