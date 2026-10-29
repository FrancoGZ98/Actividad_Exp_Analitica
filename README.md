# MLflow en Databricks: clasificación de tumores de mama

Práctica del Seminario de Experiencias en Analítica (Maestría en Ciencia de Datos, EAFIT).

Reproduce el flujo de MLflow visto en clase con otro dataset: `breast_cancer` de scikit-learn
(569 muestras, 30 variables, clasificación binaria maligno/benigno).

## Qué incluye `mlflow_cancer_mama.ipynb`

1. Runs con parámetros, métricas, tags y artefactos (matriz de confusión, curva ROC).
2. Métricas por paso (curva de F1 del gradient boosting).
3. Búsqueda de hiperparámetros de random forest con runs anidados.
4. Autolog.
5. Consulta de runs con `mlflow.search_runs` y desempate por simplicidad.
6. Modelo final con firma, evaluado una sola vez en el set de prueba.
7. Registro en Unity Catalog con alias `@champion` / `@challenger` y regla de promoción.
8. Inferencia por alias con `spark_udf`.
9. Tracing con `@mlflow.trace`.

Los hiperparámetros se eligen sobre un set de **validación**, separado del set de **prueba**.

## Cómo ejecutarlo en Databricks (Free Edition)

1. **Workspace › Create › Git folder** y pega la URL de este repositorio.
2. Abre `mlflow_cancer_mama.ipynb` dentro de la carpeta clonada.
3. Conecta el cómputo **Serverless** y ejecuta **Run all**.
4. Revisa los resultados en **Experiments › curso-mlflow-cancer-mama** y el modelo en
   **Catalog › workspace › default › clasificador_cancer_mama**.

Los widgets `catalogo` y `esquema` permiten cambiar dónde se registra el modelo (por defecto `workspace.default`).
