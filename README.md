# 🚀 Proyecto RappiPlus: De Datos a Decisiones de Negocio

Este repositorio contiene un análisis end-to-end orientado a evaluar el desempeño, la rentabilidad, el comportamiento de los usuarios y la efectividad de las mejoras de producto en **RappiPlus**. A través del procesamiento de datos en Python, consultas avanzadas en SQL, pruebas de hipótesis y visualización interactiva en Business Intelligence, este proyecto transforma datos masivos en decisiones estratégicas.

---

## 📌 Tabla de Contenidos
1. [Descripción del Proyecto](#-descripción-del-proyecto)
2. [Estructura del Proyecto](#-estructura-del-proyecto)
3. [Flujo de Trabajo y Metodología](#-flujo-de-trabajo-y-metodología)
4. [Resultados e Insights Clave](#-resultados-e-insights-clave)
5. [Dashboard e Informes Interactivos](#-dashboard-e-informes-interactivos)
6. [Tecnologías Utilizadas](#-tecnologías-utilizadas)
7. [Instrucciones de Ejecución](#-instrucciones-de-ejecución)

---

## 📖 Descripción del Proyecto

El objetivo principal es responder a preguntas clave sobre la sostenibilidad económica y el crecimiento del servicio **RappiPlus**:
- **Calidad de datos:** ¿Podemos confiar en los datos de los pedidos, catálogos y campañas?
- **Rentabilidad:** ¿El servicio es rentable considerando los costos de productos e inversión en marketing?
- **Funnel de conversión:** ¿En qué etapa del proceso de compra perdemos mayor cantidad de usuarios?
- **Retención:** ¿Los usuarios siguen activos en las semanas posteriores a su registro?
- **Experimentación (A/B Test):** ¿Los cambios en la interfaz de usuario (UI) en el *checkout* generan un incremento estadísticamente significativo en las conversiones?

---

## 📂 Estructura del Proyecto

```text
.
├── data/
│   ├── raw/                       # Datasets originales (CSV)
│   └── processed/                 # Datasets limpios (orders_clean.csv, catalog_clean.csv, etc.)
├── notebooks/
│   └── rappiplus_analysis.ipynb   # Notebook principal con todo el pipeline de análisis
├── queries/
│   └── PostgreSQL Queries         # Consultas SQL para funnel y cohortes
└── README.md                      # Documentación del proyecto

```
## 🛠️ Flujo de Trabajo y Metodología

1. 🔍 Limpieza y Validación de Datos (Python / Pandas)
- Carga de datasets: Pedidos (orders), Catálogo (catalog) e Inversión en Marketing (marketing).
- Tratamiento de datos nulos, formato de fechas e identificación/eliminación del 0.40% de registros duplicados.
- Filtrado de valores incoherentes o negativos en cantidad y montos.

2. 💰 Análisis de Rentabilidad y KPIs Financieros
- Revenue Total: $51,987,462.26
- Costo Total de Producto: $43,124,018.41
- Inversión en Marketing: $2,871,843.53
- Profit Bruto: $8,863,443.85
- Profit Neto: $6,081,600.32

3. 🛒 Análisis de Funnel de Conversión (SQL - PostgreSQL)
- Consulta de eventos (events) para determinar el flujo de usuarios desde first_visit hasta purchase.
- Identificación de los puntos de fuga críticos a lo largo del proceso de checkout.

4. 🔁 Retención por Cohortes (SQL - PostgreSQL)
- Definición de cohortes mensuales basadas en la fecha de registro (users).
- Evaluación de la retención semanal (user_activity) durante las semanas W1, W2 y W3 (~40-43% de retención promedio semanal).

5. 🧪 Test de Hipótesis A/B (Prueba Z de Proporciones)
- Experimento: Evaluación de la nueva UI en Checkout (experiment_checkout_ui.csv).
- Hipótesis:
  - $H_0$: La tasa de conversión entre la UI actual (Control) y la nueva UI (Tratamiento) es igual.
  - $H_1$: Existe una diferencia significativa en la tasa de conversión.
- Resultado: $p\text{-value} > 0.05$. No hay evidencia estadística suficiente para rechazar $H_0$, lo que implica que la diferencia observada (~0.6%) se debe al azar.

6. 📊 Visualización BI (Power BI / Tableau)
- Creación de dos tableros principales: Overview Ejecutivo y Detalle / Drill-through.
- Modelado de datos dimensional, tabla calendario y métricas DAX/LODs para análisis temporal YTD/YoY.

## 📈 Resultados e Insights Clave
- Rentabilidad Positiva: El negocio genera un margen de profit sostenible, aunque el costo directo del catálogo representa la mayor porción de los ingresos totales.
- Efectividad del Experimento: Se recomienda no desplegar la nueva UI de checkout, ya que los costos asociados a su implementación no se justifican por un impacto estadísticamente insignificante.
- Estabilidad de la Retención: Las cohortes muestran un comportamiento estable cercano al 41-43% de retención en las primeras semanas, señal de una buena adopción inicial.

## 🖥️ Dashboard e Informes Interactivos
- Los tableros interactivos e insumos limpios se encuentran disponibles para su consulta:
- 
   🔗 Acceso a Dashboard y Archivos: [Descargar archivo Power BI](dashboards/rappiplus_dashboard.pbix](https://github.com/ericecologics/-RappiPlus-An-lisis-de-Datos-para-Decisiones-de-Negocio/blob/1b870a0eb48b4e673d00df0cf15d8c35caab03c1/dashboard_rappiplus.pbix))
-
## ⚙️ Tecnologías Utilizadas
- Lenguaje de Programación: Python 3.x
- Librerías de Análisis: Pandas, NumPy, Statsmodels (proportions_ztest)
- Base de Datos & SQL: PostgreSQL, SQLAlchemy
- Herramientas de BI: Power BI 
- Entorno de Desarrollo: Jupyter Notebooks 

🚀 Instrucciones de Ejecución
-Clonar el repositorio:
Bash
git clone [https://github.com/tu-usuario/rappiplus-data-analysis.git](https://github.com/ericecologics/-RappiPlus-An-lisis-de-Datos-para-Decisiones-de-Negocio/tree/main)
cd rappiplus-data-analysis


-Instalar dependencias:
Bash
pip install pandas numpy sqlalchemy psycopg2-binary statsmodels


Ejecutar el Notebook:
Abre notebooks/rappiplus_analysis.ipynb y ejecuta las celdas en orden secuencial para reproducir los resultados y análisis.
