# 📊 Desafío Telecom X - Análisis de Evasión de Clientes

## Descripción del Proyecto
Bienvenido al Desafío Telecom X, un caso práctico del programa ONE de Alura LATAM. En este proyecto, me desempeño como analista de datos en una empresa de telecomunicaciones que enfrenta un problema crítico: la alta evasión de clientes (churn).

El objetivo principal es aplicar un proceso completo de ETL (Extract, Transform, Load) para limpiar, transformar y analizar los datos de los clientes, identificando los factores que influyen en la decisión de cancelar el servicio.

## Objetivos del Desafío
* 🧹 **Limpiar y tratar los datos** recibidos en formato JSON vía API.
* 🔍 **Realizar un análisis exploratorio detallado** para detectar patrones relevantes.
* 📊 **Identificar posibles causas** de la evasión de clientes.
* 📝 **Redactar un informe final** con conclusiones y recomendaciones estratégicas.
* 🚀 **Aplicar conocimientos de ETL** utilizando Python y sus principales bibliotecas.

## Tecnologías Utilizadas
* **Python 3.8+**
* **Pandas:** Manipulación y análisis de datos.
* **NumPy:** Cálculos numéricos.
* **Matplotlib:** Visualización de datos.
* **Seaborn:** Visualizaciones estadísticas.
* **Requests:** Extracción de datos desde API.
* **Google Colab:** Entorno de desarrollo.

## Estructura del Proyecto

📁 TelecomX_Challenge/
├── 📓 TelecomX_ETL_Analysis.ipynb    # Notebook principal con análisis completo
├── 📄 README.md                      # Descripción del proyecto (este archivo)
├── 📄 TelecomX_Procesado.csv         # Datos procesados en formato CSV
├── 📄 TelecomX_Procesado.json        # Datos procesados en formato JSON
├── 📄 TelecomX_Procesado.xlsx        # Datos procesados en formato Excel
└── 📄 resultados/                    # Carpeta con visualizaciones y reportes
├── 📊 distribucion_churn.png
├── 📊 correlacion_variables.png
└── 📊 analisis_categorico.png

## Proceso ETL Implementado

### 1. Extract (Extracción de Datos)
* ✅ **Fuente de Datos:** API de Telecom X en formato JSON.
* ✅ **URL:** `https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-latam/main/telecomx_data.json`.
* ✅ **Método:** Extracción mediante la biblioteca `requests` con manejo de errores.
* ✅ **Carga:** Conversión automática a un DataFrame de Pandas.

### 2. Transform (Transformación de Datos)
* **Limpieza de Datos:**
    * ✅ **Detección y tratamiento de valores nulos:** Rellenado con moda (categóricas) y mediana (numéricas).
    * ✅ **Eliminación de duplicados:** Se identificaron y eliminaron registros duplicados.
    * ✅ **Verificación de consistencia:** Análisis de valores únicos por columna.
* **Transformaciones Aplicadas:**
    * ✅ **Creación de columna "cuentas_diarias":** Cálculo a partir de la facturación mensual.
    * ✅ **Conversión de variables binarias:** Transformación de "Sí"/"No" a 1/0.
    * ✅ **Estandarización de nombres:** Renombrado de columnas para mayor claridad.
    * ✅ **Normalización de datos:** Ajuste de formatos y tipos de datos.

### 3. Load (Carga y Análisis)
* ✅ **Análisis Descriptivo:** Estadísticas resumen para variables numéricas y categóricas.
* ✅ **Análisis de Evasión:** Distribución de churn y tasas por segmentos.
* ✅ **Visualizaciones:** Gráficos de barras, boxplots, histogramas y mapas de calor.
* ✅ **Correlación:** Análisis de relaciones entre variables.
* ✅ **Exportación:** Guardado en múltiples formatos (CSV, JSON, Excel).

## Resultados del Análisis

### Hallazgos Principales
#### 1. Tasa de Evasión General
* **Tasa de Churn identificada:** 26.5% 📉.
* **Clientes totales analizados:** 7,043 👥.
* **Clientes que abandonaron:** 1,869 😔.
* **Clientes que permanecen:** 5,174 😊.

#### 2. Variables Categóricas con Mayor Impacto
| Variable           | Categoría de Mayor Riesgo | Tasa de Evasión | Impacto  |
|--------------------|---------------------------|-----------------|----------|
| 📱 Tipo de Contrato | Mes a Mes                 | 42.7%           | 🔴 Alto  |
| 💳 Método de Pago   | Cheque Electrónico        | 45.3%           | 🔴 Alto  |
| 🌐 Servicio Internet| Fibra Óptica              | 41.9%           | 🔴 Alto  |
| 👨‍💼 Soporte Técnico | Sin Soporte               | 31.6%           | 🟡 Medio |
| 📺 Streaming TV    | Sin Servicio              | 33.5%           | 🟡 Medio |

#### 3. Variables Numéricas con Mayor Impacto
| Variable             | Clientes que Abandonan | Clientes que Permanecen | Diferencia      |
|----------------------|------------------------|-------------------------|-----------------|
| 💰 Cargo Mensual     | $74.4                  | $61.3                   | +21.4% ⬆️       |
| ⏱️ Antigüedad        | 17.9 meses             | 37.6 meses              | -52.4% ⬇️       |
| 💳 Cargo Total       | $1,532                 | $2,552                  | -40.0% ⬇️       |
| 📅 Cuentas Diarias   | $2.48                  | $2.04                   | +21.6% ⬆️       |

#### 4. Correlaciones Significativas
| Variable             | Correlación con Churn | Relación      |
|----------------------|-----------------------|---------------|
| ⏱️ Antigüedad        | -0.35                 | Inversa 📉    |
| 💰 Cargo Mensual     | +0.19                 | Directa 📈    |
| 📊 Cuentas Diarias   | +0.19                 | Directa 📈    |
| 👨‍💼 Soporte Técnico | -0.17                 | Inversa 📉    |

### Visualizaciones Generadas
* 📊 **Distribución de evasión:** Gráfico circular mostrando la proporción de clientes que abandonan vs. permanecen.
* 📈 **Análisis por variables categóricas:** Gráficos de barras apiladas con tasas de evasión.
* 📉 **Análisis por variables numéricas:** Boxplots y histogramas comparativos.
* 🔥 **Mapa de calor de correlación:** Visualización de relaciones entre todas las variables.
* 📊 **Correlación con churn:** Gráfico de barras mostrando las variables más relacionadas.

## Conclusiones y Recomendaciones

### Conclusiones Clave
* **Factores de mayor riesgo:**
    * Los clientes con contratos `Mes a Mes` tienen casi el doble de probabilidad de abandonar.
    * El método de pago con `Cheque Electrónico` está fuertemente asociado a la evasión.
    * La falta de soporte técnico aumenta significativamente el riesgo de churn.
* **Patrones de comportamiento:**
    * Los clientes nuevos (menos de 12 meses) tienen mayor tendencia a abandonar.
    * Los clientes con cargos mensuales más altos muestran mayor tasa de evasión.
    * Los clientes sin servicios adicionales (streaming, soporte) son más propensos a irse.
* **Impacto económico:**
    * La evasión representa una pérdida significativa de ingresos recurrentes.
    * Los clientes que abandonan tienen, en promedio, cargos mensuales un 21% más altos.

### Recomendaciones Estratégicas
1.  **Segmentación y Retención:**
    * 📊 Implementar programas de fidelización para clientes de alto riesgo.
    * 🎁 Ofrecer descuentos en contratos anuales a clientes `Mes a Mes`.
    * 💡 Personalizar ofertas basadas en el perfil de riesgo de cada cliente.
2.  **Optimización de Pagos:**
    * 🔄 Promover métodos de pago automáticos (tarjeta, débito).
    * 💸 Ofrecer incentivos para cambiar de `Cheque Electrónico` a otros métodos.
    * 📱 Simplificar el proceso de pago para reducir la fricción.
3.  **Mejora de Servicios:**
    * 📞 Implementar soporte técnico proactivo para clientes nuevos.
    * 🎮 Crear paquetes de servicios atractivos que incluyan `Streaming` y `Soporte`.
    * 📊 Monitorear la satisfacción de clientes con cargos mensuales altos.
4.  **Monitoreo Continuo:**
    * 🔄 Establecer un dashboard en tiempo real de métricas de churn.
    * 📊 Implementar alertas tempranas para clientes en riesgo.
    * 📈 Realizar análisis A/B para evaluar la efectividad de las estrategias.

## Cómo Ejecutar el Proyecto
### Prerrequisitos
* Python 3.8 o superior.
* Cuenta de Google Colab (opcional).
* Conexión a internet para acceder a la API.

### Ejecución en Google Colab (Recomendado)
1.  📂 Abrir Google Colab: `colab.research.google.com`.
2.  📋 Crear nuevo notebook: `File` → `New notebook`.
3.  📋 Copiar el código: Copiar todo el código del archivo `TelecomX_ETL_Analysis.ipynb`.
4.  📋 Pegar y ejecutar: Pegar en las celdas del notebook y ejecutar.
5.  📊 Ver resultados: El análisis se ejecutará automáticamente mostrando todas las visualizaciones.

### Ejecución Local
```bash
# clonar el repositorio
git clone [https://github.com/gedp/telecomx_desafio_aluralatam.git](https://github.com/gedp/telecomx_desafio_aluralatam.git)
cd telecomx_desafio_aluralatam

# instalar dependencias
pip install pandas numpy matplotlib seaborn requests openpyxl

# ejecutar el notebook
jupyter notebook TelecomX_ETL_Analysis.ipynb

Archivos Generados
Archivo	Formato	Descripción
telecomx_procesado.csv	CSV	Datos limpios y transformados
telecomx_procesado.json	JSON	Datos en formato JSON
telecomx_procesado.xlsx	Excel	Datos con múltiples hojas
distribucion_churn.png	PNG	Gráfico de distribución de evasión
correlacion_variables.png	PNG	Mapa de calor de correlaciones
analisis_categorico.png	PNG	Análisis por variables categóricas

Logros del Proyecto
✅ Proceso ETL completo: Implementación exitosa de extracción, transformación y carga.

✅ Análisis exploratorio profundo: Identificación de patrones y tendencias.

✅ Visualizaciones profesionales: Gráficos claros e informativos.

✅ Insights accionables: Recomendaciones concretas para el negocio.

✅ Código replicable: Solución escalable y documentada.

✅ Múltiples formatos de salida: Flexibilidad en el uso de los datos.

Nota: Este proyecto fue desarrollado como parte del desafío de Alura LATAM para demostrar competencias en análisis de datos, proceso ETL y visualización de información.

⭐ Si este proyecto te fue útil, ¡considera darle una estrella! ⭐
