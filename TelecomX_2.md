# 📊 TELECOM X - FASE 2: INTELIGENCIA PREDICTIVA DE INGRESOS Y CHURN

## 🎯 PROPÓSITO DEL PROYECTO
El objetivo principal de este análisis es transformar los datos operativos de Telecom X en activos estratégicos. Mediante el uso de Machine Learning, hemos desarrollado dos soluciones clave:
1. Predicción de Valor (Regresión): Estimación de los 'Cargos Totales' por cliente.
2. Prevención de Abandono (Clasificación): Identificación temprana de clientes con alta probabilidad de cancelar su servicio (Churn).

---

## 📂 ESTRUCTURA DEL PROYECTO
* notebook_principal.ipynb  : Cuaderno con el flujo de limpieza, EDA y modelado.
* datos_codificados.csv     : Dataset procesado y normalizado.
* champion.pkl              : Modelo final serializado para producción.
* reportes/                 : Carpeta con visualizaciones de importancia de variables.

---

## ⚙️ PREPARACIÓN DE DATOS Y MODELADO

### 1. Clasificación de Variables
* Numéricas: Permanencia_Meses, Cargos_Mensuales, Cargos_Totales.
* Categóricas: Servicio_Internet, Tipo_Contrato, Metodo_Pago, Es_Fiel.

### 2. Ingeniería de Características
* Codificación: Uso de One-Hot Encoding para transformar categorías en variables binarias (0 y 1).
* Limpieza: Tratamiento de valores nulos (NaN) y eliminación de infinitos para asegurar la estabilidad del modelo.
* Segmentación: División de datos en 70% Entrenamiento y 30% Prueba (test_size=0.3).

### 3. Justificación del Modelo
Se seleccionó Random Forest Regressor/Classifier por su alta capacidad para manejar relaciones no lineales y su robustez contra el sobreajuste (overfitting). El modelo final alcanzó un R2 de 0.98, superando ampliamente a la baseline inicial.

---

## 📈 INSIGHTS Y VISUALIZACIÓN (EDA)
Durante el análisis exploratorio y de importancia de variables, se determinó:
* Permanencia: Es el factor #1 que determina el ingreso acumulado.
* Fibra Óptica: Los clientes con este servicio generan más ingresos pero tienen un riesgo de fuga 20% mayor si no cuentan con soporte técnico.
* Contratos: Los contratos anuales actúan como el principal retenedor de valor.

---

## 🚀 INSTRUCCIONES DE EJECUCIÓN

### Requisitos Previos (Bibliotecas)
Es necesario tener instalado Python 3.x y las siguientes librerías:
> pip install pandas scikit-learn matplotlib seaborn

### Pasos para ejecutar:
1. Abrir el cuaderno en Jupyter Notebook o Google Colab.
2. Asegurarse de que 'datos_codificados.csv' esté en la misma ruta.
3. Ejecutar las celdas de forma secuencial.
4. Para usar el modelo guardado, emplear la función 'pickle.load' con el archivo 'champion.pkl'.

---
Documento generado para el proyecto Telecom X - 2024.


---

## 🛠️ INSTALACIÓN Y CONFIGURACIÓN

Para replicar este entorno de análisis en tu máquina local, sigue estos pasos:

### 1. Clonar o Descargar el Proyecto
Descarga los archivos en una carpeta local y asegúrate de mantener la estructura de archivos sugerida.

### 2. Crear un Entorno Virtual (Recomendado)
Para evitar conflictos con otras librerías, ejecuta en tu terminal:
```bash
python -m venv venv_telecom
# Activar en Windows:
venv_telecom\Scripts\activate
# Activar en Mac/Linux:
source venv_telecom/bin/activate