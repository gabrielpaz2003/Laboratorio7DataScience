# Laboratorio 7 — Predicción de Diabetes con AutoGluon

## Descripción
Proyecto de aprendizaje automático para predecir el riesgo de diabetes utilizando AutoGluon y un conjunto de datos tipo Pima Indians. Incluye análisis exploratorio, limpieza de datos, un modelo base con Regresión Logística, entrenamiento con AutoGluon (`best_quality`), evaluación con métricas y gráficas, importancia de variables y una reflexión crítica.

## Contenidos
- `Lab7_AutoGluon_Diabetes.ipynb`
- `diabetes.csv`

## Requisitos
- Python 3.10 o superior
- pip actualizado

## Instalación
```bash
pip install -U pip setuptools wheel
pip install -U autogluon==1.1.1 scikit-learn matplotlib seaborn pandas numpy
```

## Ejecución del cuaderno
1. Ubicar `Lab7_AutoGluon_Diabetes.ipynb` y `diabetes.csv` en la misma carpeta.
2. Abrir el cuaderno en Jupyter, VS Code o Google Colab.
3. Ejecutar las celdas en orden, iniciando por la de instalación si es necesario.

## Estructura sugerida del repositorio
```
.
├─ README.md
├─ Lab7_AutoGluon_Diabetes.ipynb
└─ diabetes.csv
```

## Flujo del trabajo en el cuaderno
1. Instalación de dependencias y configuración general.
2. Carga del dataset y descripción de variables.
3. Análisis exploratorio (estadísticos, nulos, duplicados, histogramas, boxplots, correlaciones).
4. Limpieza y preparación (tratamiento de ceros inválidos e imputación con mediana).
5. Partición de datos estratificada.
6. Baseline con Regresión Logística (pipeline con imputación y escalado).
7. Entrenamiento con AutoGluon (`presets="best_quality"`, `eval_metric="accuracy"`, `time_limit` configurable).
8. Evaluación: leaderboard, matriz de confusión, accuracy, precision, recall, F1, curva ROC y AUC.
9. Importancia de características.
10. Reflexión crítica sobre AutoML en contextos de salud.
11. Sección de reproducibilidad (versiones de librerías).

## Dataset
- Archivo: `diabetes.csv`
- Columna objetivo: `Outcome` (1 positivo, 0 negativo)
- Variables típicas: `Pregnancies`, `Glucose` o `GlucosePlasma`, `BloodPressure`, `SkinThickness` o `Skin`, `Insulin`, `BMI`, `DiabetesPedigreeFunction`, `Age`

## Notas de compatibilidad de columnas
En algunos CSV las columnas pueden variar de nombre. El cuaderno incluye una resolución de alias para detectar nombres equivalentes y evitar errores. Si el nombre de la variable objetivo difiere de `Outcome`, el flujo se ajusta automáticamente.

## Resultados esperados
- Tabla comparativa entre baseline y mejor modelo de AutoGluon.
- Gráficas: matriz de confusión, ROC y AUC.
- Importancia de variables.
- Discusión de desempeño y consideraciones de interpretabilidad y ética.

## Solución de problemas comunes
### No module named 'seaborn'
```python
%pip install seaborn==0.13.2
```
### No module named 'autogluon'
```python
%pip install autogluon==1.1.1
```
### KeyError por nombres de columnas
Revisar la sección de alias en el cuaderno. Confirmar que `diabetes.csv` tenga las columnas esperadas o equivalentes.

### Indexación de `predict_proba`
El cuaderno maneja `Series`, `DataFrame` y `ndarray`. En caso de error, ejecutar nuevamente la celda de evaluación para normalizar la salida y extraer la probabilidad de la clase positiva.

## Métricas de evaluación
- Exactitud (Accuracy)
- Precisión (Precision)
- Sensibilidad (Recall)
- F1-Score
- AUC-ROC

## Licencia
MIT
