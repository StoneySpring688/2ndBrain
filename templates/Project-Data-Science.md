---
title: "Proyecto de Data Science - [Nombre descriptivo]"
type: project
tags: [area/data-science, topic/specific-domain, level/intermediate]
status: draft
last_reviewed: YYYY-MM-DD
start_date: YYYY-MM-DD
end_date: YYYY-MM-DD
tech_stack: [python, pandas, scikit-learn, jupyter]
domain: data-science
project_type: [classification, regression, clustering, nlp, computer-vision, time-series]
dataset_size: small | medium | large
business_impact: high | medium | low
---

# Proyecto: [Nombre del Proyecto de Data Science]

Descripción breve del problema de negocio, el enfoque de data science y el valor esperado.

## 🎯 Objetivo y problema de negocio

### Problema
Descripción clara del problema que se busca resolver con datos:
- **Contexto del negocio:** Situación actual y pain points
- **Stakeholders:** Quién se beneficia de la solución
- **Impacto esperado:** Métricas de éxito del negocio

### Objetivo del proyecto
- **Objetivo principal:** Qué resultado específico se busca
- **Objetivos secundarios:** Insights o productos adicionales
- **Restricciones:** Limitaciones técnicas, temporales o de recursos

### Hipótesis inicial
- **Hipótesis 1:** Creemos que X variable influye en Y porque...
- **Hipótesis 2:** Esperamos que el modelo pueda predecir Z con precisión > 85%
- **Supuestos:** Qué asumimos sobre los datos y el problema

## 📊 Datos y metodología

### Fuentes de datos
| Fuente | Descripción | Tamaño | Frecuencia | Calidad |
|--------|-------------|---------|------------|---------|
| Sistema A | Transacciones de usuarios | 1M registros | Diario | Alta |
| API B | Datos externos de mercado | 50K registros | Semanal | Media |
| Base C | Datos históricos | 5M registros | Estático | Variable |

### Schema de datos principal
```python
# Estructura principal del dataset
{
    'user_id': 'int64',           # Identificador único
    'timestamp': 'datetime64',    # Momento de la transacción
    'amount': 'float64',          # Monto en USD
    'category': 'object',         # Categoría del producto
    'location': 'object',         # Ubicación geográfica
    'is_fraud': 'bool'           # Variable objetivo (ejemplo)
}
```

### Metodología
- **Tipo de problema:** Clasificación/Regresión/Clustering/etc.
- **Métricas de evaluación:** Accuracy, Precision, Recall, F1, AUC-ROC
- **Validación:** Time series split / K-fold / Hold-out
- **Baseline:** Modelo simple para comparar (regla heurística, promedio histórico)

## 🗂️ Estructura del proyecto

```
proyecto-data-science/
├── data/
│   ├── raw/                 # Datos originales sin procesar
│   ├── interim/             # Datos intermedios durante processing
│   ├── processed/           # Datos finales para modelado
│   └── external/            # Datos externos (APIs, referencias)
├── notebooks/
│   ├── 01-exploratory-data-analysis.ipynb
│   ├── 02-data-cleaning.ipynb
│   ├── 03-feature-engineering.ipynb
│   ├── 04-modeling.ipynb
│   └── 05-evaluation.ipynb
├── src/
│   ├── data/               # Scripts para obtener/procesar datos
│   ├── features/           # Feature engineering
│   ├── models/             # Entrenamiento y predicción
│   └── visualization/      # Gráficos y reportes
├── models/                 # Modelos entrenados serializados
├── reports/               # Reportes y documentación
├── tests/                 # Tests unitarios
├── requirements.txt
├── README.md
└── Makefile              # Comandos automatizados
```

## 🔍 Análisis exploratorio (EDA)

### Características del dataset
```python
# Resumen básico del dataset
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Cargar datos
df = pd.read_csv('data/raw/dataset.csv')

print(f"Shape del dataset: {df.shape}")
print(f"Memoria utilizada: {df.memory_usage(deep=True).sum() / 1024**2:.2f} MB")

# Información general
df.info()
df.describe()
```

### Hallazgos clave del EDA
- **Calidad de datos:** X% de valores faltantes, Y outliers identificados
- **Distribuciones:** Variable objetivo balanceada/desbalanceada (ratio Z:W)
- **Correlaciones:** Variables A y B altamente correlacionadas (r=0.85)
- **Patrones temporales:** Estacionalidad semanal/mensual observable
- **Segmentos:** 3 clusters naturales de usuarios identificados

### Visualizaciones importantes
```python
# Distribución de variable objetivo
plt.figure(figsize=(10, 6))
df['target'].value_counts().plot(kind='bar')
plt.title('Distribución de Variable Objetivo')
plt.show()

# Correlaciones
plt.figure(figsize=(12, 8))
correlation_matrix = df.select_dtypes(include=[np.number]).corr()
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', center=0)
plt.title('Matriz de Correlación')
plt.show()

# Series temporal si aplica
plt.figure(figsize=(15, 5))
df.groupby('date')['target'].mean().plot()
plt.title('Evolución temporal de la variable objetivo')
plt.show()
```

## 🛠️ Procesamiento de datos

### Limpieza de datos
```python
# src/data/clean_data.py
def clean_dataset(df):
    """
    Limpia el dataset aplicando reglas específicas del dominio.
    """
    # Remover duplicados
    df_clean = df.drop_duplicates()
    
    # Tratar valores faltantes
    df_clean['numeric_col'].fillna(df_clean['numeric_col'].median(), inplace=True)
    df_clean['categorical_col'].fillna('Unknown', inplace=True)
    
    # Filtrar outliers usando IQR
    Q1 = df_clean['amount'].quantile(0.25)
    Q3 = df_clean['amount'].quantile(0.75)
    IQR = Q3 - Q1
    lower_bound = Q1 - 1.5 * IQR
    upper_bound = Q3 + 1.5 * IQR
    
    df_clean = df_clean[
        (df_clean['amount'] >= lower_bound) & 
        (df_clean['amount'] <= upper_bound)
    ]
    
    return df_clean
```

### Feature Engineering
```python
# src/features/build_features.py
def engineer_features(df):
    """
    Crea features relevantes para el problema.
    """
    # Features temporales
    df['hour'] = df['timestamp'].dt.hour
    df['day_of_week'] = df['timestamp'].dt.dayofweek
    df['is_weekend'] = df['day_of_week'].isin([5, 6]).astype(int)
    
    # Features agregadas
    user_stats = df.groupby('user_id')['amount'].agg(['mean', 'std', 'count'])
    user_stats.columns = ['user_avg_amount', 'user_std_amount', 'user_transaction_count']
    df = df.merge(user_stats, on='user_id', how='left')
    
    # Features de ratio
    df['amount_vs_user_avg'] = df['amount'] / df['user_avg_amount']
    
    # Encoding categórico
    df_encoded = pd.get_dummies(df, columns=['category', 'location'], prefix=['cat', 'loc'])
    
    return df_encoded

def select_features(df, target_col):
    """
    Selecciona features más relevantes usando técnicas estadísticas.
    """
    from sklearn.feature_selection import SelectKBest, f_classif
    
    X = df.drop(columns=[target_col])
    y = df[target_col]
    
    # Seleccionar top K features
    selector = SelectKBest(score_func=f_classif, k=20)
    X_selected = selector.fit_transform(X, y)
    
    # Obtener nombres de features seleccionadas
    selected_features = X.columns[selector.get_support()].tolist()
    
    return selected_features
```

## 🤖 Modelado

### Configuración experimental
```python
# src/models/config.py
RANDOM_STATE = 42
TEST_SIZE = 0.2
VALIDATION_SIZE = 0.2

MODELS_CONFIG = {
    'logistic_regression': {
        'model': LogisticRegression(random_state=RANDOM_STATE),
        'params': {
            'C': [0.001, 0.01, 0.1, 1, 10, 100],
            'penalty': ['l1', 'l2'],
            'solver': ['liblinear']
        }
    },
    'random_forest': {
        'model': RandomForestClassifier(random_state=RANDOM_STATE),
        'params': {
            'n_estimators': [100, 200, 300],
            'max_depth': [10, 20, None],
            'min_samples_split': [2, 5, 10],
            'min_samples_leaf': [1, 2, 4]
        }
    },
    'xgboost': {
        'model': XGBClassifier(random_state=RANDOM_STATE),
        'params': {
            'n_estimators': [100, 200, 300],
            'max_depth': [3, 6, 9],
            'learning_rate': [0.01, 0.1, 0.2],
            'subsample': [0.8, 0.9, 1.0]
        }
    }
}
```

### Pipeline de entrenamiento
```python
# src/models/train_model.py
from sklearn.model_selection import GridSearchCV, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.pipeline import Pipeline
from sklearn.metrics import classification_report, confusion_matrix

def train_models(X_train, y_train, X_val, y_val):
    """
    Entrena múltiples modelos y selecciona el mejor.
    """
    results = {}
    
    for name, config in MODELS_CONFIG.items():
        print(f"Entrenando {name}...")
        
        # Crear pipeline con preprocessing
        pipeline = Pipeline([
            ('scaler', StandardScaler()),
            ('model', config['model'])
        ])
        
        # Grid search con validación cruzada
        param_grid = {f'model__{k}': v for k, v in config['params'].items()}
        
        grid_search = GridSearchCV(
            pipeline,
            param_grid,
            cv=5,
            scoring='f1_weighted',
            n_jobs=-1,
            verbose=1
        )
        
        grid_search.fit(X_train, y_train)
        
        # Evaluar en conjunto de validación
        y_pred = grid_search.predict(X_val)
        
        results[name] = {
            'model': grid_search.best_estimator_,
            'best_params': grid_search.best_params_,
            'cv_score': grid_search.best_score_,
            'val_predictions': y_pred,
            'classification_report': classification_report(y_val, y_pred, output_dict=True)
        }
        
        print(f"Best CV Score for {name}: {grid_search.best_score_:.4f}")
    
    return results

# Seleccionar mejor modelo
best_model_name = max(results.keys(), key=lambda x: results[x]['cv_score'])
best_model = results[best_model_name]['model']

print(f"Mejor modelo: {best_model_name}")
```

### Evaluación del modelo
```python
# src/models/evaluate_model.py
def evaluate_model(model, X_test, y_test, model_name="Model"):
    """
    Evaluación comprehensiva del modelo.
    """
    y_pred = model.predict(X_test)
    y_pred_proba = model.predict_proba(X_test)[:, 1]  # Para problemas binarios
    
    # Métricas básicas
    from sklearn.metrics import accuracy_score, precision_score, recall_score, f1_score, roc_auc_score
    
    metrics = {
        'accuracy': accuracy_score(y_test, y_pred),
        'precision': precision_score(y_test, y_pred, average='weighted'),
        'recall': recall_score(y_test, y_pred, average='weighted'),
        'f1': f1_score(y_test, y_pred, average='weighted'),
        'auc_roc': roc_auc_score(y_test, y_pred_proba)
    }
    
    print(f"Métricas para {model_name}:")
    for metric, value in metrics.items():
        print(f"{metric.upper()}: {value:.4f}")
    
    # Matriz de confusión
    cm = confusion_matrix(y_test, y_pred)
    plt.figure(figsize=(8, 6))
    sns.heatmap(cm, annot=True, fmt='d', cmap='Blues')
    plt.title(f'Matriz de Confusión - {model_name}')
    plt.ylabel('Real')
    plt.xlabel('Predicción')
    plt.show()
    
    # Curva ROC
    from sklearn.metrics import roc_curve
    fpr, tpr, _ = roc_curve(y_test, y_pred_proba)
    
    plt.figure(figsize=(8, 6))
    plt.plot(fpr, tpr, label=f'{model_name} (AUC = {metrics["auc_roc"]:.3f})')
    plt.plot([0, 1], [0, 1], 'k--', label='Random')
    plt.xlabel('False Positive Rate')
    plt.ylabel('True Positive Rate')
    plt.title('Curva ROC')
    plt.legend()
    plt.show()
    
    return metrics

# Feature importance
def plot_feature_importance(model, feature_names, top_n=20):
    """
    Visualiza la importancia de features.
    """
    if hasattr(model.named_steps['model'], 'feature_importances_'):
        importances = model.named_steps['model'].feature_importances_
    elif hasattr(model.named_steps['model'], 'coef_'):
        importances = np.abs(model.named_steps['model'].coef_[0])
    else:
        print("El modelo no tiene feature importance disponible")
        return
    
    # Crear DataFrame para facilitar visualización
    importance_df = pd.DataFrame({
        'feature': feature_names,
        'importance': importances
    }).sort_values('importance', ascending=False).head(top_n)
    
    plt.figure(figsize=(10, 8))
    sns.barplot(data=importance_df, x='importance', y='feature')
    plt.title(f'Top {top_n} Features más importantes')
    plt.xlabel('Importancia')
    plt.show()
    
    return importance_df
```

## 📈 Resultados y métricas

### Performance del modelo final
- **Modelo seleccionado:** Random Forest con hiperparámetros optimizados
- **Accuracy:** 87.3% en conjunto de test
- **Precision:** 85.1% (importante para minimizar falsos positivos)
- **Recall:** 89.2% (importante para capturar casos positivos)
- **F1-Score:** 87.1% (balance entre precision y recall)
- **AUC-ROC:** 0.923 (excelente capacidad discriminativa)

### Comparación con baseline
| Métrica | Baseline (Regla heurística) | Modelo ML | Mejora |
|---------|----------------------------|-----------|---------|
| Accuracy | 72.1% | 87.3% | +15.2% |
| Precision | 68.5% | 85.1% | +16.6% |
| Recall | 75.0% | 89.2% | +14.2% |

### Features más importantes
1. **user_avg_amount** (0.23) - Promedio histórico del usuario
2. **amount_vs_user_avg** (0.18) - Ratio respecto al promedio personal
3. **hour** (0.12) - Hora del día de la transacción
4. **user_transaction_count** (0.11) - Frecuencia de transacciones del usuario
5. **is_weekend** (0.08) - Si ocurre en fin de semana

### Análisis de errores
- **Falsos positivos:** Principalmente transacciones legítimas en horarios inusuales
- **Falsos negativos:** Fraudes que imitan patrones normales del usuario
- **Sesgo identificado:** Menor precisión en usuarios con pocos datos históricos

## 🚀 Implementación y despliegue

### API de predicción
```python
# src/api/predict.py
from flask import Flask, request, jsonify
import joblib
import pandas as pd

app = Flask(__name__)

# Cargar modelo entrenado
model = joblib.load('models/best_model.pkl')
preprocessor = joblib.load('models/preprocessor.pkl')

@app.route('/predict', methods=['POST'])
def predict():
    try:
        # Obtener datos del request
        data = request.json
        
        # Convertir a DataFrame
        df = pd.DataFrame([data])
        
        # Aplicar preprocessing
        df_processed = preprocessor.transform(df)
        
        # Realizar predicción
        prediction = model.predict(df_processed)[0]
        probability = model.predict_proba(df_processed)[0]
        
        return jsonify({
            'prediction': int(prediction),
            'probability': {
                'class_0': float(probability[0]),
                'class_1': float(probability[1])
            },
            'confidence': float(max(probability))
        })
        
    except Exception as e:
        return jsonify({'error': str(e)}), 400

@app.route('/health', methods=['GET'])
def health():
    return jsonify({'status': 'healthy'})

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5000)
```

### Monitoreo del modelo
```python
# src/monitoring/model_monitoring.py
def monitor_model_performance(predictions_df, actuals_df):
    """
    Monitorea degradación del modelo en producción.
    """
    # Calcular métricas actuales
    current_accuracy = accuracy_score(actuals_df['actual'], predictions_df['prediction'])
    
    # Comparar con métricas baseline
    baseline_accuracy = 0.873  # Del entrenamiento
    
    if current_accuracy < baseline_accuracy - 0.05:  # 5% degradación
        print(f"⚠️  ALERTA: Degradación del modelo detectada!")
        print(f"Accuracy actual: {current_accuracy:.3f}")
        print(f"Accuracy baseline: {baseline_accuracy:.3f}")
        
        # Enviar alerta (email, Slack, etc.)
        send_alert("Modelo necesita reentrenamiento")
    
    # Drift en features
    check_feature_drift(predictions_df)
    
    return {
        'current_accuracy': current_accuracy,
        'baseline_accuracy': baseline_accuracy,
        'degradation': baseline_accuracy - current_accuracy
    }

def check_feature_drift(new_data):
    """
    Detecta drift en las features usando estadísticas.
    """
    # Cargar datos de entrenamiento para comparar
    training_stats = joblib.load('models/training_statistics.pkl')
    
    for column in new_data.select_dtypes(include=[np.number]).columns:
        current_mean = new_data[column].mean()
        training_mean = training_stats[column]['mean']
        
        # Test simple de drift (se puede mejorar con tests estadísticos)
        if abs(current_mean - training_mean) / training_mean > 0.2:  # 20% cambio
            print(f"⚠️  Drift detectado en feature '{column}'")
            print(f"Media entrenamiento: {training_mean:.3f}")
            print(f"Media actual: {current_mean:.3f}")
```

## 📊 Business impact y ROI

### Métricas de negocio
- **Reducción de falsos positivos:** 25% menos de transacciones legítimas bloqueadas
- **Detección mejorada:** 40% más de fraudes detectados vs sistema anterior
- **Ahorro estimado:** $150K anuales por reducción de pérdidas
- **Costo de implementación:** $50K (desarrollo + infraestructura)
- **ROI proyectado:** 200% en el primer año

### Impact dashboard
```python
# Dashboard para stakeholders
import streamlit as st
import plotly.express as px

def create_business_dashboard():
    st.title("ML Model Business Impact Dashboard")
    
    # Métricas principales
    col1, col2, col3, col4 = st.columns(4)
    
    with col1:
        st.metric("Fraud Detection Rate", "89.2%", "+14.2%")
    with col2:
        st.metric("False Positive Rate", "12.7%", "-16.6%")
    with col3:
        st.metric("Monthly Savings", "$12.5K", "+25%")
    with col4:
        st.metric("Model Accuracy", "87.3%", "+15.2%")
    
    # Gráficos de evolución temporal
    st.subheader("Performance Over Time")
    
    # Simulación de datos temporales
    dates = pd.date_range('2024-01-01', periods=30, freq='D')
    performance_data = pd.DataFrame({
        'date': dates,
        'accuracy': np.random.normal(0.873, 0.02, 30),
        'precision': np.random.normal(0.851, 0.025, 30),
        'recall': np.random.normal(0.892, 0.03, 30)
    })
    
    fig = px.line(performance_data, x='date', y=['accuracy', 'precision', 'recall'],
                  title="Model Performance Metrics Over Time")
    st.plotly_chart(fig)
```

## 🔄 Próximos pasos

### Mejoras técnicas identificadas
- [ ] **Experiment tracking:** Implementar MLflow para mejor seguimiento de experimentos
- [ ] **Feature store:** Centralizar features para reutilización
- [ ] **AutoML:** Explorar soluciones automatizadas para baseline rápido
- [ ] **Deep learning:** Evaluar redes neuronales para patrones más complejos
- [ ] **Online learning:** Implementar actualización incremental del modelo

### Extensiones del producto
- [ ] **Real-time scoring:** Reducir latencia de predicción a <50ms
- [ ] **Explainability:** Dashboard de explicaciones para analistas
- [ ] **A/B testing:** Framework para comparar versiones de modelo
- [ ] **Multi-model ensemble:** Combinar múltiples modelos para mayor robustez
- [ ] **Feedback loop:** Incorporar feedback de usuarios para mejorar modelo

### Proceso y organización
- [ ] **Model governance:** Políticas de versionado y aprobación
- [ ] **Automated retraining:** Pipeline automático de reentrenamiento
- [ ] **Data quality monitoring:** Alertas proactivas de calidad de datos
- [ ] **Documentation:** Wiki técnico para facilitar handoff
- [ ] **Training:** Capacitación para equipos de negocio

## 🔗 Recursos relacionados

- [Concepto: Machine Learning Pipeline](../../10-Concepts/ml-pipeline.md)
- [HowTo: Deploy ML Model to AWS](../../20-HowTos/ml/deploy-aws.md)
- [Snippet: Model Evaluation Utilities](../../30-Snippets/Python/ml-evaluation.md)
- [Research: Latest in Fraud Detection](../../50-Research/fraud-detection-sota.md)

## 📖 Referencias y recursos

### Papers académicos
- [Original fraud detection paper](https://arxiv.org/abs/xxxx.xxxxx)
- [Survey on imbalanced learning](https://link.springer.com/article/xxxx)
- [Feature selection techniques](https://ieeexplore.ieee.org/document/xxxxx)

### Herramientas y frameworks
- [Scikit-learn documentation](https://scikit-learn.org/stable/)
- [XGBoost documentation](https://xgboost.readthedocs.io/)
- [MLflow for experiment tracking](https://mlflow.org/)
- [Streamlit for dashboards](https://streamlit.io/)

### Datasets públicos similares
- [Credit Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)
- [IEEE-CIS Fraud Detection](https://www.kaggle.com/c/ieee-fraud-detection)

---

**Estado del proyecto:** En producción desde MM/YYYY
**Próxima revisión:** Trimestral
**Owner:** Data Science Team
**Stakeholders:** Risk Management, Product, Engineering