# 📊 TelecomX LATAM - Análisis de Churn (Abandono de Clientes)

## 📋 Descripción del Proyecto

Este proyecto tiene como objetivo analizar y predecir el **churn** (abandono de clientes) en una empresa de telecomunicaciones de la región LATAM. Se implementa un flujo completo de **ETL (Extract, Transform, Load)** y análisis de datos para identificar patrones, factores de riesgo y generar insights accionables.

### 🎯 Objetivos Principales:
1. Extraer y limpiar datos de clientes de telecomunicaciones
2. Identificar las principales variables que influyen en el abandono
3. Generar visualizaciones para comprender el comportamiento del churn
4. Preparar los datos para futuros modelos predictivos

## 📁 Estructura del Proyecto
TelecomX_LATAM
TelecomX_LATAM_informe_final.ipynb # Notebook principal con el análisis completo
TelecomX_Data.xlsx # Dataset exportado en español
TelecomX_Data_español.xlsx # Dataset final procesado
README.md # Este archivo

## 🔄 Flujo del Proyecto

### 1. **📌 Extracción de Datos**
- Conexión a API para descargar datos JSON
- Carga inicial de datos usando `pandas.read_json()`
- Desanidación de estructuras JSON complejas

### 2. **🔧 Transformación y Limpieza**
- **Limpieza de caracteres especiales**: Eliminación de `{}[]'"` de columnas de texto
- **Aplanamiento de datos**: Convertir estructuras JSON anidadas en columnas planas
- **Traducción de columnas**: Nombres en español para mejor comprensión
- **Codificación de variables categóricas**:
  - `Yes` → `1`
  - `No` → `0`
  - `No internet service` / `No phone service` → `0`
- **Manejo de valores nulos**:
  - `Charges.Total` con espacios → Convertido a numérico
  - Valores faltantes rellenados con `0`
- **Creación de nuevas variables**:
  - `Cuentas_Diarias`: Cálculo de cargos diarios (Mensual/30)
  - `Grupo_Permanencia`: Segmentación por antigüedad del cliente

### 3. **📊 Análisis y Visualización**
- **Análisis descriptivo**: Estadísticas básicas de todas las variables
- **Distribución de churn**: Gráfico de pastel interactivo con Plotly
- **Análisis por variables categóricas**:
  - Dependientes
  - Tipo de contrato
  - Antigüedad del cliente
- **Tasas de abandono**: Cálculo de porcentajes por segmento

## 🛠️ Tecnologías Utilizadas

- **Python 3.11+**
- **Pandas**: Manipulación y análisis de datos
- **NumPy**: Operaciones numéricas
- **Plotly/Express**: Visualizaciones interactivas
- **Requests**: Conexión a APIs
- **Jupyter Notebook**: Entorno de desarrollo

## 📈 Variables Clave Analizadas

### 🔑 Variables Principales para Predecir Churn:
1. **`Abandono`** (Churn): Variable objetivo (Sí/No)
2. **`Contrato`**: Clientes mes-a-mes tienen mayor riesgo
3. **`Permanencia_Meses`**: Antigüedad del cliente
4. **`Cargos_Mensuales`**: Tarifas mensuales
5. **`Cargos_Totales`**: Historial de pagos
6. **`Servicio_Internet`**: Tipo de servicio (Fiber optic/DSL)

### 📊 Métricas de Segmentación:
- **Tasa de abandono por antigüedad**:
  - 0-1 mes: 0.00%
  - 2-12 meses: 46.79%
  - 13-24 meses: 28.91%
  - +2 años: 13.85%

## 📋 Diccionario de Variables (Traducidas)

| Variable Original | Variable en Español | Descripción |
|------------------|---------------------|-------------|
| customerID | ID_Cliente | Identificador único del cliente |
| Churn | Abandono | Indica si el cliente abandonó (1) o no (0) |
| gender | Genero | Género del cliente |
| SeniorCitizen | Tercera_Edad | Indica si es adulto mayor (65+ años) |
| Partner | Socio | Tiene pareja (1) o no (0) |
| Dependents | Dependientes | Tiene dependientes (1) o no (0) |
| tenure | Permanencia_Meses | Meses con la empresa |
| PhoneService | Servicio_Telefono | Tiene servicio telefónico (1) o no (0) |
| MultipleLines | Multiples_Lineas | Tiene múltiples líneas (1) o no (0) |
| InternetService | Servicio_Internet | Tipo de servicio de internet |
| OnlineSecurity | Seguridad_Online | Tiene seguridad online (1) o no (0) |
| OnlineBackup | Copia_Seguridad_Online | Tiene backup online (1) o no (0) |
| DeviceProtection | Proteccion_Dispositivo | Tiene protección de dispositivo (1) o no (0) |
| TechSupport | Soporte_Tecnico | Tiene soporte técnico (1) o no (0) |
| StreamingTV | Streaming_TV | Tiene streaming TV (1) o no (0) |
| StreamingMovies | Streaming_Peliculas | Tiene streaming de películas (1) o no (0) |
| Contract | Contrato | Tipo de contrato |
| PaperlessBilling | Factura_Digital | Factura digital (1) o física (0) |
| PaymentMethod | Metodo_Pago | Método de pago |
| Charges.Monthly | Cargos_Mensuales | Cargos mensuales |
| Charges.Total | Cargos_Totales | Cargos totales acumulados |

## 📊 Hallazgos Clave

### 🚨 **Factores de Alto Riesgo de Churn:**
1. **Contrato mes-a-mes**: Mayor probabilidad de abandono
2. **Primer año de servicio**: 46.79% de tasa de abandono en primeros 12 meses
3. **Servicio Fiber optic**: Mayor sensibilidad a problemas de calidad
4. **Sin servicios adicionales**: Clientes sin OnlineSecurity/TechSupport tienen mayor riesgo
5. **Facturación digital**: Relación con mayor rotación

### ✅ **Factores de Retención:**
1. **Contratos largos** (2 años): Solo 13.85% de abandono
2. **Servicios adicionales**: OnlineSecurity, TechSupport, etc.
3. **Antigüedad**: Más de 2 años reduce significativamente el churn

## 🚀 Cómo Ejecutar el Proyecto

### Prerrequisitos:
```bash
pip install pandas numpy plotly requests jupyter

Pasos:
Clonar o descargar el repositorio
Abrir el notebook TelecomX_LATAM_informe_final.ipynb

Ejecutar las celdas en orden secuencial
Los datos se cargan automáticamente desde la API pública

📁 Archivos Generados
TelecomX_Data.xlsx: Dataset inicial procesado

TelecomX_Data_español.xlsx: Dataset final con todas las transformaciones

🔮 Próximos Pasos
🎯 Análisis Futuro:
Modelado Predictivo
Regresión logística
Random Forest
XGBoost
Segmentación Avanzada
Clustering de clientes
Análisis de cohortes
Dashboard Interactivo
Power BI/Tableau
Streamlit app

📈 Recomendaciones de Negocio:
Focalizar esfuerzos en clientes del primer año
Incentivar contratos anuales o bienales
Promover servicios adicionales como estrategia de retención
Mejorar calidad del servicio Fiber optic
Programas de fidelización para clientes antiguos

👥 Contribución
Este proyecto fue desarrollado como parte de un challenge de ciencia de datos para LATAM, implementando mejores prácticas de ETL y análisis exploratorio de datos.

📄 Licencia
Este proyecto es para fines educativos y de demostración. Los datos son públicos y utilizados con propósitos de aprendizaje.
