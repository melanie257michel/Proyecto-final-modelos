# Proyecto Final - Modelado No Lineal de Series de Tiempo

**Equipo:** Melanie Michel, Santiago Aguirre, Regina Flores  
**Fecha:** 15 de mayo de 2025  
**Profesor:** Oscar David Jaramillo Zuluaga  
**Expedientes:** 735572, 742976, 742641  
**GitHub:** [Enlace al repositorio](https://github.com/melanie257michel/Proyecto-final-modelos)  

---

## Objetivo
Desarrollar modelos de pronóstico para series de tiempo aplicados al consumo eléctrico de una casa en Houston, TX, integrando métodos lineales (SARIMAX) y no lineales (redes neuronales). Además, transformar el problema en clasificación para predecir si el consumo supera el promedio.

---

## Estructura del Proyecto

.
├── data/ # Datos originales
│ ├── power_usage_2016_to_2020.csv # Consumo eléctrico
│ └── weather_2016_2020.csv # Datos climáticos
├── notebooks/
│ └── guiaproyectom-2.py # Jupyter Notebook con el análisis
├── README.md # Este archivo
└── requirements.txt # Dependencias


---

## 🔍 Análisis Realizado

### 1. **Pronóstico de Series de Tiempo**
- **Modelo lineal (SARIMAX):**  
  - Ajuste con parámetros `(2,1,2)` y estacionalidad semanal (`s=7`).  
  - Resultados:  
    - MSE: 0.4837  
    - MAPE: 0.5448  
    - R²: -0.5268 (limitado para patrones no lineales).  

### 2. **Modelos Neuronales**
- **Univariados (solo consumo eléctrico):**  
  - **LSTM** obtuvo el mejor desempeño (MSE: 0.0884, R²: 0.7203).  
  - Comparación completa:  
    | Modelo     | MSE     | R²      |
    |------------|---------|---------|
    | LSTM1      | 0.0884  | 0.7203  |
    | MLP3       | 0.0934  | 0.7047  |
    | CNN-LSTM3  | 0.0916  | 0.7103  |

- **Multivariados (consumo + clima):**  
  - Mejor modelo: **LSTM1** (MSE: 0.1696, R²: 0.6302).  
  - Los modelos complejos (CNN-LSTM) mostraron sobreajuste sin ajuste fino.  

### 3. **Clasificación (Consumo > Promedio)**
- **Mejor modelo:** Random Forest (Accuracy: 0.85, F1: 0.86).  
- Comparación de métodos:  
  | Modelo               | Accuracy | F1-Score |
  |----------------------|----------|----------|
  | RandomForest         | 0.85     | 0.86     |
  | CNN2                 | 0.82     | 0.83     |
  | LSTM1                | 0.81     | 0.82     |

---

## 📌 Conclusiones
- **LSTM** superó a SARIMAX en capturar patrones temporales complejos.  
- Datos multivariados requieren ajuste cuidadoso para evitar sobreajuste.  
- Random Forest fue óptimo para clasificación binaria. 
