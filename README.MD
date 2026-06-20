# 📊 Análisis de Portafolio de Acciones

Proyecto de análisis cuantitativo de un portafolio de acciones usando Python. Incluye descarga de datos históricos, cálculo de métricas de riesgo/retorno, análisis de correlación y optimización de portafolio mediante simulación Monte Carlo con la teoría moderna de Markowitz.

---

## 🎯 Objetivos del proyecto

- Descargar y procesar precios históricos de activos financieros con `yfinance`
- Calcular retornos diarios, acumulados y métricas clave de riesgo
- Analizar la correlación entre activos para evaluar diversificación
- Optimizar la composición del portafolio maximizando el ratio Sharpe
- Visualizar la frontera eficiente y los portafolios óptimos

---

## 📁 Estructura del repositorio

```
portfolio-analisis-acciones/
│
├── notebooks/
│   ├── 01_descarga_datos.ipynb          # Descarga y exploración de precios históricos
│   ├── 02_analisis_retornos.ipynb       # Retornos diarios, acumulados y correlaciones
│   ├── 03_metricas_riesgo.ipynb         # Volatilidad, Sharpe, VaR y Max Drawdown
│   └── 04_optimizacion_portafolio.ipynb # Frontera eficiente y portafolio óptimo
│
├── src/
│   └── portfolio_utils.py               # Funciones reutilizables del proyecto
│
├── data/
│   └── precios_historicos.csv           # Datos exportados para reproducibilidad
│
├── requirements.txt
└── README.md
```

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso en el proyecto |
|---|---|
| `yfinance` | Descarga de precios históricos desde Yahoo Finance |
| `pandas` | Manipulación y transformación de series de tiempo financieras |
| `numpy` | Cálculos matriciales para la optimización del portafolio |
| `matplotlib` | Visualizaciones: precios, retornos, drawdown y frontera eficiente |
| `seaborn` | Heatmap de correlaciones entre activos |
| `scipy` | Optimización numérica para la frontera eficiente |

---

## 📈 Activos analizados

El portafolio de ejemplo incluye una combinación de activos argentinos, regionales e internacionales:

| Ticker | Empresa | Mercado |
|---|---|---|
| `GGAL` | Grupo Financiero Galicia | Argentina / NYSE |
| `YPF` | YPF S.A. | Argentina / NYSE |
| `MELI` | MercadoLibre | Latinoamérica / NASDAQ |
| `SPY` | S&P 500 ETF | Estados Unidos / NYSE |

> Los tickers y el período de análisis son fácilmente configurables en cada notebook.

---

## 📐 Métricas implementadas

- **Retorno anualizado**: rendimiento promedio proyectado a un año
- **Volatilidad anualizada**: desvío estándar de retornos × √252
- **Ratio Sharpe**: retorno ajustado por riesgo respecto a la tasa libre de riesgo
- **Value at Risk (VaR 95%)**: pérdida máxima esperada con 95% de confianza
- **Maximum Drawdown**: caída máxima desde un pico histórico hasta el punto más bajo
- **Matriz de correlación**: relación entre los retornos de los activos del portafolio

---

## 🚀 Cómo correr el proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/tu-usuario/portfolio-analisis-acciones.git
cd portfolio-analisis-acciones
```

### 2. Crear un entorno virtual e instalar dependencias

```bash
python -m venv venv
source venv/bin/activate        # En Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Abrir Jupyter y ejecutar los notebooks en orden

```bash
jupyter notebook
```

Ejecutar los notebooks en el orden numérico: `01` → `02` → `03` → `04`.

---

## 📦 requirements.txt

```
yfinance>=0.2.36
pandas>=2.0.0
numpy>=1.24.0
matplotlib>=3.7.0
seaborn>=0.12.0
scipy>=1.10.0
jupyter>=1.0.0
```

---

## 🔍 Qué se puede aprender con este proyecto

Este proyecto cubre los conceptos fundamentales que se aplican en roles de analista de datos en el sector financiero:

1. **Manejo de series de tiempo financieras** con pandas: resampling, fechas, valores faltantes
2. **Cálculo de retornos** simples y logarítmicos y su interpretación
3. **Teoría moderna de portafolios** (Markowitz): cómo la diversificación reduce el riesgo
4. **Simulación Monte Carlo** aplicada a la optimización de pesos de activos
5. **Métricas de riesgo estándar** de la industria financiera (Sharpe, VaR, Drawdown)
6. **Buenas prácticas** de código: funciones reutilizables, notebooks documentados, estructura de proyecto

---

## 📊 Resultados destacados

### Métricas de riesgo por activo

| Activo | Retorno anual | Volatilidad anual | Ratio Sharpe | VaR 95% diario | Max Drawdown |
|---|---|---|---|---|---|
| GGAL | 64.88% | 63.52% | 0.94 | -5.24% | -62.95% |
| MELI | 18.15% | 39.15% | 0.34 | -3.58% | -40.82% |
| SPY | 20.35% | 15.26% | **1.01** | -1.42% | -18.76% |
| YPF | 55.87% | 54.49% | 0.93 | -4.44% | -48.79% |

A pesar de tener el menor retorno bruto del grupo, **SPY obtuvo el mejor ratio Sharpe (1.01)** gracias a su baja volatilidad, mostrando que el retorno ajustado por riesgo no siempre coincide con el de mayor rendimiento nominal. GGAL, en cambio, combinó el retorno más alto (64.88%) con el mayor riesgo: una volatilidad de 63.52% y un drawdown máximo de -62.95%.

*(Ver notebook `03_metricas_riesgo.ipynb` para el cálculo completo)*

### Frontera eficiente y portafolio óptimo

La simulación Monte Carlo (10.000 portafolios aleatorios) identificó dos estrategias óptimas:

| | Máximo Sharpe | Mínima Varianza |
|---|---|---|
| GGAL | 3.92% | 0.87% |
| MELI | 1.65% | 0.07% |
| SPY | 74.32% | 93.28% |
| YPF | 20.12% | 5.79% |
| **Retorno esperado** | 29.21% | 22.79% |
| **Volatilidad** | 19.88% | 15.71% |
| **Ratio Sharpe** | **1.22** | 1.13 |

Ambas estrategias concentran la mayor parte del capital en SPY, consistente con su mejor relación riesgo/retorno individual. El portafolio de máximo Sharpe asume algo más de volatilidad a cambio de un retorno esperado mayor, mientras que el de mínima varianza prioriza estabilidad casi por completo.

*(Ver notebook `04_optimizacion_portafolio.ipynb` para el gráfico de la frontera eficiente)*

### Matriz de correlaciones

El análisis de correlación muestra que incluir SPY como activo de referencia reduce la correlación promedio del portafolio, mejorando la diversificación frente a activos de renta variable argentina.

*(Ver notebook `02_analisis_retornos.ipynb`)*

---

## 👤 Autor

Juan Baustista Jeanneret
Estudiante de Análisis de Datos | Interesado en finanzas cuantitativas y mercados de capitales

- 🔗 [LinkedIn]https://www.linkedin.com/in/juan-bautista-jeanneret-934aa3263/
- 💻 [GitHub]https://github.com/bautij4-a11y
- 📧 Bautij4@gmail.com

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Podés usarlo, modificarlo y distribuirlo libremente con atribución.

---

> **Nota**: Este proyecto es de carácter educativo. No constituye asesoramiento financiero ni recomendación de inversión.