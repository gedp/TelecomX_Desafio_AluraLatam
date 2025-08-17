📊 Desafío telecom x - análisis de evasión de clientes
Python
Pandas
License

Descripción del proyecto
Bienvenido al desafío telecom x, un caso práctico del programa one de alura latam. En este proyecto, me desempeño como analista de datos en una empresa de telecomunicaciones que enfrenta un problema crítico: alta evasión de clientes (churn).

El objetivo principal es aplicar un proceso completo de etl (extract, transform, load) para limpiar, transformar y analizar los datos de clientes, identificando los factores que influyen en la decisión de cancelar el servicio.

Objetivos del desafío
🧹 Limpiar y tratar los datos recibidos en formato json vía api
🔍 Realizar un análisis exploratorio detallado para detectar patrones relevantes
📊 Identificar posibles causas de la evasión de clientes
📝 Redactar un informe final con conclusiones y recomendaciones estratégicas
🚀 Aplicar conocimientos de etl utilizando python y sus principales bibliotecas
Tecnologías utilizadas
Python Python 3.8+
Pandas Pandas - manipulación y análisis de datos
NumPy NumPy - cálculos numéricos
Matplotlib Matplotlib - visualización de datos
Seaborn Seaborn - visualizaciones estadísticas
Requests Requests - extracción de datos desde api
Google Colab Google Colab - entorno de desarrollo
Estructura del proyecto

Line Wrapping

Collapse
Copy
1
2
3
4
5
6
7
8
9
10
📁 TelecomX_Challenge/
├── 📓 TelecomX_ETL_Analysis.ipynb    # notebook principal con análisis completo
├── 📄 README.md                      # descripción del proyecto (este archivo)
├── 📄 TelecomX_Procesado.csv         # datos procesados en formato csv
├── 📄 TelecomX_Procesado.json        # datos procesados en formato json
├── 📄 TelecomX_Procesado.xlsx        # datos procesados en formato excel
└── 📄 resultados/                    # carpeta con visualizaciones y reportes
    ├── 📊 distribucion_churn.png
    ├── 📊 correlacion_variables.png
    └── 📊 analisis_categorico.png
Proceso etl implementado
1. Extract (extracción de datos)
✅ Fuente de datos: api de telecom x en formato json
✅ Url: https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-latam/main/telecomx_data.json
✅ Método: extracción mediante biblioteca requests con manejo de errores
✅ Carga: conversión automática a dataframe de pandas
python

Line Wrapping

Collapse
Copy
1
2
3
4
5
# extracción de datos desde la api
url = "https://raw.githubusercontent.com/alura-cursos/challenge2-data-science-latam/main/telecomx_data.json"
response = requests.get(url)
data = response.json()
df = pd.DataFrame(data)
2. Transform (transformación de datos)
Limpieza de datos
✅ Detección y tratamiento de valores nulos: rellenado con moda (categóricas) y mediana (numéricas)
✅ Eliminación de duplicados: se identificaron y eliminaron registros duplicados
✅ Verificación de consistencia: análisis de valores únicos por columna
Transformaciones aplicadas
✅ Creación de columna "cuentas_diarias": cálculo a partir de facturación mensual
✅ Conversión de variables binarias: transformación de "sí"/"no" a 1/0
✅ Estandarización de nombres: renombrado de columnas para mayor claridad
✅ Normalización de datos: ajuste de formatos y tipos de datos
python

Line Wrapping

Collapse
Copy
1
2
3
4
# ejemplo de transformaciones
df['cuentas_diarias'] = df['cargo_mensual'] / 30
df['evasion'] = df['evasion'].map({'sí': 1, 'no': 0})
df = df.rename(columns={'customerid': 'id_cliente', 'gender': 'genero'})
3. Load (carga y análisis)
✅ Análisis descriptivo: estadísticas resumen para variables numéricas y categóricas
✅ Análisis de evasión: distribución de churn y tasas por segmentos
✅ Visualizaciones: gráficos de barras, boxplots, histogramas y mapas de calor
✅ Correlación: análisis de relaciones entre variables
✅ Exportación: guardado en múltiples formatos (csv, json, excel)
Resultados del análisis
Hallazgos principales
1. Tasa de evasión general
Tasa de churn identificada: 26.5% 📉
Clientes totales analizados: 7,043 👥
Clientes que abandonaron: 1,869 😔
Clientes que permanecen: 5,174 😊
2. Variables categóricas con mayor impacto
Variable
Categoría de mayor riesgo
Tasa de evasión
Impacto
📱 Tipo de contrato
Mes a mes
42.7%
🔴 alto
💳 Método de pago
Cheque electrónico
45.3%
🔴 alto
🌐 Servicio internet
Fibra óptica
41.9%
🔴 alto
👨‍💼 Soporte técnico
Sin soporte
31.6%
🟡 medio
📺 Streaming tv
Sin servicio
33.5%
🟡 medio
3. Variables numéricas con mayor impacto
Variable
Clientes que abandonan
Clientes que permanecen
Diferencia
💰 Cargo mensual
$74.4
$61.3
+21.4% ⬆️
⏱️ Antigüedad
17.9 meses
37.6 meses
-52.4% ⬇️
💳 Cargo total
$1,532
$2,552
-40.0% ⬇️
📅 Cuentas diarias
$2.48
$2.04
+21.6% ⬆️
4. Correlaciones significativas
Variable
Correlación con churn
Relación
⏱️ Antigüedad
-0.35
Inversa 📉
💰 Cargo mensual
+0.19
Directa 📈
📊 Cuentas diarias
+0.19
Directa 📈
👨‍💼 Soporte técnico
-0.17
Inversa 📉
Visualizaciones generadas
📊 Distribución de evasión: gráfico circular mostrando la proporción de clientes que abandonan vs. permanecen
📈 Análisis por variables categóricas: gráficos de barras apiladas con tasas de evasión
📉 Análisis por variables numéricas: boxplots y histogramas comparativos
🔥 Mapa de calor de correlación: visualización de relaciones entre todas las variables
📊 Correlación con churn: gráfico de barras mostrando las variables más relacionadas
Conclusiones y recomendaciones
Conclusiones clave
Factores de mayor riesgo:
Los clientes con contratos mes a mes tienen casi el doble de probabilidad de abandonar
El método de pago con cheque electrónico está fuertemente asociado a la evasión
La falta de soporte técnico aumenta significativamente el riesgo de churn
Patrones de comportamiento:
Los clientes nuevos (menos de 12 meses) tienen mayor tendencia a abandonar
Los clientes con cargos mensuales más altos muestran mayor tasa de evasión
Los clientes sin servicios adicionales (streaming, soporte) son más propensos a irse
Impacto económico:
La evasión representa una pérdida significativa de ingresos recurrentes
Los clientes que abandonan tienen, en promedio, cargos mensuales un 21% más altos
Recomendaciones estratégicas
1. Segmentación y retención
📊 Implementar programas de fidelización para clientes de alto riesgo
🎁 Ofrecer descuentos en contratos anuales a clientes mes a mes
💡 Personalizar ofertas basadas en el perfil de riesgo de cada cliente
2. Optimización de pagos
🔄 Promover métodos de pago automáticos (tarjeta, débito)
💸 Ofrecer incentivos para cambiar de cheque electrónico a otros métodos
📱 Simplificar el proceso de pago para reducir fricción
3. Mejora de servicios
📞 Implementar soporte técnico proactivo para clientes nuevos
🎮 Crear paquetes de servicios atractivos que incluyan streaming y soporte
📊 Monitorear la satisfacción de clientes con cargos mensuales altos
4. Monitoreo continuo
🔄 Establecer un dashboard en tiempo real de métricas de churn
📊 Implementar alertas tempranas para clientes en riesgo
📈 Realizar análisis a/b para evaluar la efectividad de las estrategias
Cómo ejecutar el proyecto
Prerrequisitos
Python 3.8 o superior
Cuenta de google colab (opcional)
Conexión a internet para acceder a la api
Ejecución en google colab (recomendado)
📂 Abrir google colab: colab.research.google.com
📋 Crear nuevo notebook: file → new notebook
📋 Copiar el código: copiar todo el código del archivo telecomx_etl_analysis.ipynb
📋 Pegar y ejecutar: pegar en las celdas del notebook y ejecutar
📊 Ver resultados: el análisis se ejecutará automáticamente mostrando todas las visualizaciones
Ejecución local
bash

Line Wrapping

Collapse
Copy
1
2
3
4
5
6
7
8
9
# clonar el repositorio
git clone https://github.com/gedp/telecomx_desafio_aluralatam.git
cd telecomx_desafio_aluralatam

# instalar dependencias
pip install pandas numpy matplotlib seaborn requests openpyxl

# ejecutar el notebook
jupyter notebook telecomx_etl_analysis.ipynb
Archivos generados
El proyecto genera los siguientes archivos de salida:

Archivo
Formato
Descripción
telecomx_procesado.csv
Csv
Datos limpios y transformados
telecomx_procesado.json
Json
Datos en formato json
telecomx_procesado.xlsx
Excel
Datos con múltiples hojas
distribucion_churn.png
Png
Gráfico de distribución de evasión
correlacion_variables.png
Png
Mapa de calor de correlaciones
analisis_categorico.png
Png
Análisis por variables categóricas
Logros del proyecto
✅ Proceso etl completo: implementación exitosa de extracción, transformación y carga
✅ Análisis exploratorio profundo: identificación de patrones y tendencias
✅ Visualizaciones profesionales: gráficos claros e informativos
✅ Insights accionables: recomendaciones concretas para el negocio
✅ Código replicable: solución escalable y documentada
✅ Múltiples formatos de salida: flexibilidad en el uso de los datos

Licencia
Este proyecto está bajo la licencia mit - ver el archivo license para detalles.

Contribuciones
¡Las contribuciones son bienvenidas! Por favor, sientete libre de abrir un issue o un pull request.

Nota: este proyecto fue desarrollado como parte del desafío de alura latam para demostrar competencias en análisis de datos, proceso etl y visualización de información.

⭐ Si este proyecto te fue útil, ¡considera darle una estrella! ⭐



