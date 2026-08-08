# Reglas dominantes y anomalas con PSO

Flujo reproducible para preparar el dataset cardiovascular, descubrir reglas dominantes y buscar reglas anomalas condicionadas.

## Orden de ejecucion

1. `notebooks/01_preparar_dataset.ipynb`
2. `notebooks/02_pso_reglas_dominantes.ipynb`
3. `notebooks/03_pso_reglas_anomalas.ipynb`

Los notebooks no dependen de Google Drive. Los artefactos intermedios se guardan en `artifacts/` y los resultados finales en `outputs/`.

El primer notebook descarga el dataset publico mediante `kagglehub`. El dataset y los resultados generados no deben subirse al repositorio si contienen datos o archivos pesados.

## Dependencias

```text
numpy
pandas
joblib
matplotlib
kagglehub
```

Instalacion:

```bash
pip install -r requirements.txt
```

