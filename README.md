# Clasificador de tumores de mama — Actividad 3.2.1

Proyecto de **aprendizaje automático supervisado** (clasificación binaria) para la materia *Fundamentos de Inteligencia Artificial*.
A partir de 10 medidas de núcleos celulares (biopsia FNA), el sistema predice si un tumor es **benigno** o **maligno**.

> ⚠️ Proyecto educativo. No es un dispositivo médico ni sustituye un diagnóstico profesional.

## Problema y datos
- **Dataset:** Breast Cancer Wisconsin (Diagnostic) — UCI Machine Learning Repository (incluido en `scikit-learn`).
- **Registros:** 569 (357 benignos / 212 malignos) · **Variables:** 10 medidas "media" · **Objetivo:** `diagnosis` (1 = maligno).
- **Tipo de problema:** clasificación. **Métrica prioritaria:** Recall de la clase maligna.

## Resultados (conjunto de prueba, 114 casos)
| Modelo | Accuracy | Precision | Recall | F1 | ROC AUC |
|---|---|---|---|---|---|
| **SVM (ganador)** | 0.974 | 0.976 | 0.952 | 0.964 | 0.989 |
| KNN | 0.947 | 0.909 | 0.952 | 0.930 | 0.975 |
| Random Forest | 0.939 | 0.927 | 0.905 | 0.916 | 0.985 |
| Árbol de Decisión | 0.921 | 0.923 | 0.857 | 0.889 | 0.928 |

El ganador se eligió con validación cruzada repetida (5 x 3) sobre el conjunto de entrenamiento; SVM y Random Forest quedaron prácticamente empatados. Detalles y limitaciones en `docs/informe_metodologico.pdf`.

## Estructura
```
├── actividad_3_2_1.ipynb     # EDA, preparación, 4 modelos, evaluación y guardado del modelo
├── app.py                    # Aplicación web (Streamlit)
├── requirements.txt
├── data/                     # Dataset en CSV y tablas de resultados
├── figures/                  # Gráficas generadas por el notebook
├── models/                   # modelo.joblib y metadata.json
└── docs/informe_metodologico.pdf
```

## Instrucciones de uso
```bash
git clone <URL-DE-TU-REPOSITORIO>
cd <carpeta>
python -m venv .venv && source .venv/bin/activate     # en Windows: .venv\Scripts\activate
pip install -r requirements.txt

# (opcional) reproducir todo el análisis y regenerar el modelo
jupyter notebook actividad_3_2_1.ipynb

# lanzar la aplicación
streamlit run app.py
```
También puedes abrir el notebook en Google Colab. Si tu versión de `scikit-learn` difiere de la indicada y el modelo no carga, ejecuta el notebook para regenerar `models/modelo.joblib`.

**Uso de la app:** ingresa las 10 medidas (o elige un ejemplo), pulsa **Predecir** y revisa la clase y la probabilidad estimada.

## Reproducibilidad
Semilla fija (`random_state=42`), partición estratificada 80/20, escalado dentro de un `Pipeline` (sin fuga de datos) y búsqueda de hiperparámetros con validación cruzada.

## Declaración de uso de IA generativa
Se utilizó **Claude (Anthropic)** como apoyo para estructurar el proyecto y generar el código base y borradores de documentación. El equipo revisó, ejecutó y adaptó el contenido.

## Equipo
- [Integrante 1]
- [Integrante 2]
- [Integrante 3]
