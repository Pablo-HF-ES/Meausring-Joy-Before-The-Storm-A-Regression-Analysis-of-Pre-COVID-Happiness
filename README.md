# Meausring-Joy-Before-The-Storm-A-Regression-Analysis-of-Pre-COVID-Happiness
Análisis de regresión en R del World Happiness Report 2019 pre-COVID. Destaca por la selección de características (AIC), diagnóstico de supuestos (Kolmogorov-Smirnov, Durbin-Watson) y manejo iterativo de outliers. Logra un R2 ajustado de 0.8352, demostrando rigor analítico.

# Análisis de Regresión: Determinantes de la Felicidad Pre-COVID (2019)

Este repositorio contiene un análisis estadístico predictivo implementado en **R**, utilizando datos del **World Happiness Report 2019** publicado por la UN SDSN. El proyecto modela la puntuación de felicidad nacional (Score) en 156 países justo antes de la crisis global de COVID-19, estableciendo una línea base histórica para entender el bienestar socioeconómico.

---

## Stack Tecnológico & Librerías
* **Lenguaje:** R
* **Modelado Predictivo:** Regresión Lineal Múltiple (`lm`), Selección algorítmica Stepwise (AIC)
* **Diagnóstico de Modelos (Diagnostics):** `lmtest` (Durbin-Watson), `car` (Gráficos Component+Residual, Influence Index)

---

## Enfoque y Rigor Estadístico

A diferencia de aplicar un modelo lineal como "caja negra", este proyecto demuestra un dominio profundo de las matemáticas subyacentes del aprendizaje automático clásico, verificando empíricamente cada suposición estadística:

### 1. Selección de Variables (Feature Selection)
* Se implementó un procedimiento **Stepwise iterativo en ambas direcciones basado en el Criterio de Información de Akaike (AIC)** para penalizar la complejidad del modelo y evitar el sobreajuste.
* Esto permitió refinar el modelo original, descartando variables de ruido y demostrando estadísticamente que factores como la **Generosidad (Generosity)** carecen de impacto significativo en el bienestar nacional percibido ($p > 0.32$).

### 2. Diagnóstico Exhaustivo de Residuos (Model Diagnostics)
* **Normalidad:** Se comprobó visualmente mediante gráficos Q-Q y se validó formalmente con el **Test de Kolmogorov-Smirnov** ($p = 0.6658$), garantizando que los residuos se distribuyen normalmente.
* **Independencia:** Se aplicó el test de **Durbin-Watson** ($p = 0.0109$), detectando una ligera autocorrelación positiva que fue debidamente documentada para la interpretación de inferencias.
* **Linealidad y Homocedasticidad:** Analizada aislando efectos parciales con **Component+Residual plots** y gráficas de residuos estandarizados, confirmando varianzas constantes.

### 3. Tratamiento Iterativo de Outliers (Data Cleaning)
* Se utilizó la **Distancia de Cook y Residuos Estandarizados (umbral $\pm 2.5$)** para identificar anomalías de alto apalancamiento (leverage).
* A través de una depuración iterativa (eliminación secuencial de 7 observaciones extremas), el modelo incrementó su precisión predictiva: la varianza explicada (**$R^2_{adj}$**) saltó de un 0.77 inicial a un **0.8352**.
* El error estándar residual final se redujo a **0.4427**, logrando un modelo sumamente estable.

---

## Conclusiones Clave del Análisis
* **Drivers principales:** La felicidad percibida por un país se explica casi en su totalidad por tres pilares estructurales: el **PIB per cápita, el apoyo social y la esperanza de vida saludable**.
* Las métricas subjetivas (como las percepciones de corrupción) aportan valor predictivo marginal, mientras que la generosidad resultó estadísticamente no significativa.
* **Trabajo Futuro:** Como mejora para el pipeline analítico, se propone explorar regularización matemática (Modelos **LASSO / Ridge**) para gestionar la colinealidad detectada, o arquitecturas no lineales para descubrir estructuras latentes más complejas.
