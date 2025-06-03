#  Employee Promotion Prediction

Este proyecto aborda la problemática de identificar qué empleados tienen mayor probabilidad de ser promovidos dentro de una organización. Utiliza datos demográficos, historial laboral y desempeño previo para entrenar modelos de clasificación que permitan asistir al área de Recursos Humanos en sus procesos de toma de decisiones.

---

##  Dataset

El dataset contiene registros de empleados, con variables como:

- `department`: área funcional del empleado
- `region`: zona geográfica donde labora
- `education`: nivel educativo
- `gender`: género
- `recruitment_channel`: medio por el cual fue contratado
- `previous_year_rating`: calificación del año anterior
- `avg_training_score`: promedio de evaluación de entrenamientos actuales
- `is_promoted`: variable objetivo (1 = fue promovido, 0 = no promovido)

---

##  Preprocesamiento

Se realizaron los siguientes pasos de limpieza:

1. Se eliminaron registros con valores faltantes en `education` y `previous_year_rating`.
2. Se eliminó `employee_id` por no aportar valor predictivo.
3. Se codificaron variables categóricas mediante `LabelEncoder`.
4. Se dividió el conjunto en entrenamiento y prueba (80/20).
5. Dado el desbalance en la variable objetivo, se aplicó **SMOTE** para balancear la clase positiva (`is_promoted = 1`).

---

##  Exploración

Se utilizó **Sweetviz** para realizar un análisis comparativo de las características entre hombres y mujeres en relación con su probabilidad de promoción.

---

## ⚙ Modelado

Se utilizó el framework de AutoML:

- **PyCaret** para comparar modelos, ajustar hiperparámetros y evaluar desempeño.
- Se seleccionó el modelo con mejor desempeño en `accuracy`, que fue un **Random Forest**.
- El modelo se optimizó con `tune_model()` y se evaluó en el conjunto de prueba con `predict_model()`.

---

##  Resultados

- **Accuracy** en conjunto de prueba: ~90%
- **Recall (clase positiva)**: ~32%
- **F1-score (clase positiva)**: ~36%

Aunque la precisión general fue alta, el recall relativamente bajo indica que aún hay espacio de mejora en la detección de empleados que deberían ser promovidos.

---
