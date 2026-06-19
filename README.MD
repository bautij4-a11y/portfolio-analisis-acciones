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

### Frontera eficiente

La simulación genera 10.000 portafolios aleatorios y encuentra la combinación de activos que maximiza el ratio Sharpe. El portafolio óptimo y el de mínima varianza quedan marcados explícitamente en el gráfico.

*(Ver notebook `04_optimizacion_portafolio.ipynb` para el gráfico interactivo)*

### Matriz de correlaciones

El análisis de correlación muestra que incluir SPY como activo de referencia reduce la correlación promedio del portafolio, mejorando la diversificación frente a activos de renta variable argentina.

*(Ver notebook `02_analisis_retornos.ipynb`)*

---

## 👤 Autor

Juan Bautista Jeanneret
Estudiante de Análisis de Datos | Interesado en finanzas cuantitativas y mercados de capitales

- 🔗 https://www.linkedin.com/in/juan-bautista-jeanneret-934aa3263/
- 📧 Bautij4@gmail.com

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Podés usarlo, modificarlo y distribuirlo libremente con atribución.

---

> **Nota**: Este proyecto es de carácter educativo. No constituye asesoramiento financiero ni recomendación de inversión.
