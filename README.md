# Predicción de Consumo de Combustible (MPG)

**Módulo 5 — Aprendizaje Supervisado · Diplomado en Ciencia de Datos**  
Auto MPG Dataset · UCI Machine Learning Repository · 398 observaciones

## Equipo

| Integrante |
|---|
| Alan A. Castañeda Ramos |
| Daniel Macias Soto |
| Guillermo A. Martinez Vanegas | 
| Mariana Vigil Villegas | 
| Ronaldo Berrocal Reyes | 

---

## Resultados finales

| # | Modelo | MAE ↓ | RMSE | R² ↑ |
|---|---|---|---|---|
| 1 | **RF Optimizado** | **1.5547** | **2.1306** | **0.9156** |
| 2 | RF Baseline | 1.5964 | 2.1674 | 0.9126 |
| 3 | AdaBoost GS | 1.6681 | 2.2467 | 0.9061 |
| 4 | AdaBoost | 1.7400 | 2.4324 | 0.8900 |
| 5 | XGBoost GS | 1.7433 | 2.3211 | 0.8998 |
| 6 | XGBoost | 1.7853 | 2.2911 | 0.9024 |
| 7 | MLP | 1.9427 | 2.4478 | 0.8886 |
| 8 | OLS (baseline) | 2.2882 | 2.8877 | 0.8449 |
| 9 | Ridge (L2) | 2.2895 | 2.8914 | 0.8445 |
| 10 | Lasso (L1) | 2.2935 | 2.9085 | 0.8427 |
| 11 | Elastic Net | 2.2961 | 2.9037 | 0.8432 |

**Split:** 80/20 · `random_state=42` · **Métrica principal:** MAE  
**Mejora sobre baseline OLS:** 32% menos error (2.2882 → 1.5547 mpg)

---

## Estructura del repositorio

```
proyecto-auto-mpg/
├── data/
│   ├── auto_mpg_clean.csv       # Dataset limpio (398 autos, sin nulos)
│   ├── train_raw.csv            # 318 autos — entrenamiento sin escalar
│   ├── test_raw.csv             # 80 autos  — prueba sin escalar
│   ├── train_scaled.csv         # Entrenamiento escalado (StandardScaler)
│   ├── test_scaled.csv          # Prueba escalada
│   ├── scaler.pkl               # Scaler ajustado SOLO en train
│   ├── metricas_rf.csv          # Métricas RF Baseline y Optimizado
│   └── metricas_boosting.csv    # Métricas AdaBoost y XGBoost (base + GS)
├── notebooks/
│   ├── 01_EDA_Preprocesamiento.ipynb      # Exploración y limpieza
│   ├── 02_Modelos_Lineales.ipynb          # OLS, Ridge, Lasso, Elastic Net
│   ├── 03_Random_Forest.ipynb             # RF Baseline y Optimizado
│   ├── 04_AdaBoost_XGBoost.ipynb          # AdaBoost y XGBoost + GridSearch
│   └── 05_MLP_Comparativa_Final.ipynb     # MLP + tabla comparativa final
├── reportes/
│   └── reporte_proyecto.pdf               # Informe técnico (8-12 páginas)
├── figures/                               # Gráficas generadas por los NB
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Reproducibilidad

```bash
pip install -r requirements.txt
```

Ejecutar los notebooks **en orden numérico** (01 → 05).  
El NB01 genera los archivos en `/data/` que usan todos los demás.  
Todos los notebooks usan `random_state=42` y el mismo split 80/20.

---

## Dataset

**Auto MPG — UCI Machine Learning Repository**  
398 autos fabricados entre 1970 y 1982 · 9 variables · Sin valores nulos (post-limpieza)

| Variable | Tipo | Descripción |
|---|---|---|
| `mpg` | Continua | **TARGET** — Millas por galón |
| `cylinders` | Entera | Número de cilindros (3–8) |
| `displacement` | Continua | Cilindrada del motor (pulg³) |
| `horsepower` | Continua | Potencia (caballos de fuerza) |
| `weight` | Continua | Peso del vehículo (libras) |
| `acceleration` | Continua | Tiempo 0–60 mph (segundos) |
| `model_year` | Entera | Año de fabricación (70–82) |
| `origin_2` | Dummy | Origen europeo (1=sí) |
| `origin_3` | Dummy | Origen japonés (1=sí) |

---

## Modelos implementados

- **Lineales:** OLS · Ridge (L2) · Lasso (L1) · Elastic Net
- **Ensambles:** Random Forest (baseline + GridSearch) · AdaBoost (base + GS) · XGBoost (base + GS)
- **Red neuronal:** MLP — arquitectura 8→64→32→16→1, ReLU, Adam, early stopping

## Referencia

Quinlan, R. (1993). Auto MPG Dataset. UCI Machine Learning Repository.  
https://archive.ics.uci.edu/dataset/9/auto+mpg
