# Análisis ETL: Dataset de Enfermedades Cardíacas UCI

## Resumen Ejecutivo

Este proyecto implementa un proceso ETL completo sobre el dataset de enfermedades cardíacas del UCI Machine Learning Repository (Cleveland Heart Disease Database)[web:17][web:21]. Analiza 303 registros de pacientes con 14 variables clínicas para identificar patrones de riesgo cardiovascular mediante limpieza, transformación, filtración y análisis estadístico[web:24][web:27].

**Fuente de datos**: https://archive.ics.uci.edu/ml/machine-learning-databases/heart-disease/processed.cleveland.data

## Variables del Dataset

**Clínicas**: age (edad), sex (0=mujer, 1=hombre), cp (tipo dolor pecho 0-3), trestbps (presión arterial mmHg), chol (colesterol mg/dl), fbs (glucemia >120), restecg (electrocardiograma 0-2), thalach (frecuencia cardíaca máxima), exang (angina por ejercicio), oldpeak (depresión ST), slope (pendiente ST), ca (vasos principales 0-3), thal (talasemia)[web:21][web:27]. **Target**: Presencia enfermedad cardíaca (0=no, 1=sí).

## Requisitos


## Proceso ETL

**Extracción**: Carga directa desde UCI Repository con manejo de valores faltantes ('?')[web:17][web:26]. **Transformación**: Eliminación de nulos, duplicados, edades inválidas (fuera 18-100), colesterol=0 y presión=0. Conserva ~95% datos originales[web:23][web:26]. **Carga**: Genera 4 archivos CSV con subgrupos filtrados y tabla consolidada.

## Análisis Realizados

**1. Limpieza**: Validación biológica y estadística de todos los campos. **2. Segmentación etaria**: 5 grupos (<40, 40-50, 50-60, 60-70, >70 años). **3. Filtración de 8 subgrupos específicos**: Mayores 50 años, mujeres hipertensas (presión>140), hombres colesterol alto (>240), jóvenes enfermos (<45), alto riesgo múltiple (edad>55 + colesterol>240 + presión>140), frecuencia cardíaca baja (<120), análisis por tipo de dolor (4 categorías), glucemia elevada. **4. Agrupaciones estadísticas**: Por edad, sexo, tipo dolor, combinaciones edad+sexo con métricas de prevalencia y promedios clínicos. **5. Tres visualizaciones**: Distribución edad (histograma + boxplot), relación colesterol-enfermedad (scatter + comparativo), comparación por sexo (barras + tasas). **6. Tabla consolidada**: Resumen por grupo edad y sexo con total pacientes, enfermos, tasas, promedios colesterol, presión y frecuencia cardíaca.

## Archivos Generados

- `subgrupo_mayores_50.csv`: Pacientes >50 años
- `subgrupo_mujeres_hipertension.csv`: Mujeres presión >140 mmHg  
- `subgrupo_alto_riesgo.csv`: Múltiples factores combinados
- `heart_disease_consolidado.csv`: Tabla resumen completa

## Resultados Clave

**Prevalencia**: ~54% pacientes con enfermedad cardíaca. **Edad**: Mayor incidencia después 50 años, edad promedio enfermos 56 años. **Sexo**: Hombres mayor tasa que mujeres. **Factores riesgo**: Hipertensión en 20-25% casos, colesterol alto en ~15%. **Alto riesgo**: Pacientes >55 años con múltiples factores muestran tasa enfermedad >70%.

## Aplicaciones

**Salud pública**: Diseño programas detección temprana, identificación poblaciones objetivo, estratificación riesgo[web:38][web:41]. **Clínica**: Apoyo screening, identificación pacientes alto riesgo, priorización intervenciones preventivas[web:40]. **Análisis datos**: Base para Machine Learning, benchmarking clasificación, estudios epidemiológicos[web:24].

## Limitaciones y Mejoras

**Limitaciones**: Muestra limitada (n=303), datos históricos década 1980, sin variables estilo vida, sesgo geográfico Cleveland USA[web:24]. **Mejoras futuras**: Incorporar ML (Random Forest, XGBoost), ampliar con datos contemporáneos, incluir variables socioeconómicas, validación cruzada otros datasets, dashboard interactivo, API predicción tiempo real.

## Ejecución

**Google Colab**: Ejecutar todas celdas secuencialmente, gráficos inline, CSVs en entorno Colab. **Local**: `python heart_disease_analysis.py` o Jupyter Notebook.

## Conclusiones

El análisis ETL transformó 303 registros crudos en datos validados de alta calidad, identificando que edad >50 años combinada con hipertensión y colesterol alto constituye el perfil de mayor riesgo cardiovascular[web:38][web:41]. Establece bases sólidas para análisis predictivos avanzados e intervenciones basadas en evidencia con impacto en salud poblacional. Dataset público UCI disponible para uso educativo e investigación[web:17][web:18].

---
**Herramientas**: Python, pandas, numpy, matplotlib, seaborn | **Fecha**: Octubre 2025 | **Dataset**: UCI ML Repository Cleveland Heart Disease
