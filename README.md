# Telecom X - ETL y análisis de evasión de clientes

## Propósito del análisis

Este proyecto desarrolla un proceso de **ETL (Extract, Transform, Load)** en Python a partir de los datos de clientes de **Telecom X**, consumidos desde una API en formato JSON.

El objetivo principal es **extraer, limpiar, transformar y organizar los datos** para dejarlos listos para análisis exploratorio y visualización, con foco en identificar patrones asociados a la **evasión de clientes (churn)**.

A través de este proceso se busca responder preguntas como:

- ¿Cuál es la tasa general de churn?
- ¿Qué tipos de contrato presentan mayor riesgo de cancelación?
- ¿Qué métodos de pago y servicios se asocian con mayor evasión?
- ¿Cómo influye la antigüedad del cliente en la cancelación del servicio?

---

## Estructura del proyecto y organización de archivos

La estructura base del repositorio es la siguiente:

```bash
telecomx-etl/
│
├── README.md
├── TelecomX_ETL.ipynb
├── TelecomX_Data.json
├── telecomx_etl_limpio.csv
└── img/
    ├── churn_distribucion.png
    ├── churn_por_contrato.png
    └── churn_por_pago.png
```

### Descripción de archivos

- **README.md**: documentación general del proyecto.
- **TelecomX_ETL.ipynb**: notebook principal con las etapas de extracción, transformación, carga, análisis e informe final.
- **TelecomX_Data.json**: archivo fuente en formato JSON con la información original de clientes.
- **telecomx_etl_limpio.csv**: dataset final procesado y listo para análisis.
- **img/**: carpeta opcional para almacenar gráficos exportados desde el notebook.

> Nota: si tu notebook tiene otro nombre, solo reemplaza `TelecomX_ETL.ipynb` por el nombre real en el repositorio.

---

## Proceso ETL desarrollado

### 1. Extracción

Los datos fueron consumidos desde una **API pública** que entrega la información en formato JSON. Como respaldo, también puede utilizarse el archivo local `TelecomX_Data.json`.

### 2. Transformación

Durante esta fase se realizaron las siguientes tareas:

- Aplanamiento del JSON anidado con `pandas.json_normalize`.
- Renombrado de columnas para facilitar el análisis.
- Limpieza de valores vacíos y normalización de tipos de datos.
- Conversión de variables numéricas como `tenure`, `monthly_charges` y `total_charges`.
- Creación de variables derivadas como `churn_flag`, `daily_charges` y `tenure_group`.

### 3. Carga y análisis

Luego del procesamiento, los datos limpios fueron exportados a un archivo `.csv`, que sirve como base para análisis exploratorio y visualizaciones orientadas a la toma de decisiones.

### 4. Informe final

Se documentaron los principales hallazgos del análisis, destacando variables asociadas a una mayor probabilidad de churn.

---

## Ejemplos de gráficos e insights obtenidos

A partir del dataset procesado, se generaron gráficos para entender mejor el comportamiento de cancelación de clientes.

### Gráficos sugeridos

- **Distribución de churn**: muestra la proporción entre clientes que permanecen y clientes que cancelan.
- **Tasa de churn por tipo de contrato**: permite comparar el riesgo de cancelación según el compromiso contractual.
- **Tasa de churn por método de pago**: ayuda a identificar comportamientos asociados a la forma de pago.
- **Tasa de churn por tipo de servicio de internet**: evidencia diferencias en cancelación según el servicio contratado.
- **Tasa de churn por antigüedad del cliente**: muestra cómo la permanencia influye en la retención.

### Insights principales

Con base en el análisis del dataset:

- La **tasa general de churn** es de aproximadamente **26.54%**.
- Los clientes con contrato **Month-to-month** presentan la mayor tasa de cancelación, con **42.71%**.
- El método de pago con mayor churn es **Electronic check**, con **45.29%**.
- Los clientes con servicio de internet **Fiber optic** muestran una tasa de churn de **41.89%**.
- Los clientes con menor antigüedad (**0 a 12 meses**) concentran el mayor riesgo de evasión, con **47.44%**.

Estos resultados sugieren que la empresa podría enfocar estrategias de retención en clientes nuevos, clientes con contrato mensual y segmentos con métodos de pago más sensibles al abandono.

---

## Instrucciones para ejecutar el notebook

### Requisitos

Asegúrate de tener instalado Python 3.10 o superior y las siguientes librerías:

```bash
pip install pandas numpy matplotlib requests
```

### Ejecución

1. Clona este repositorio:

```bash
git clone <URL_DE_TU_REPOSITORIO>
cd telecomx-etl
```

2. Abre el notebook `TelecomX_ETL.ipynb` en:
   - **Jupyter Notebook**, o
   - **Google Colab**.

3. Ejecuta las celdas en orden, siguiendo la estructura del proyecto:
   - Extracción
   - Transformación
   - Carga y análisis
   - Informe final

4. Si deseas consumir los datos directamente desde la API, verifica que la variable `API_URL` apunte a la fuente correcta.

5. Al finalizar la ejecución, se generará el archivo procesado:

```bash
telecomx_etl_limpio.csv
```

---

## Tecnologías utilizadas

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Requests**
- **Jupyter Notebook / Google Colab**

---

## Conclusión

Este proyecto demuestra cómo un proceso ETL en Python permite transformar datos semiestructurados en una base analítica limpia, consistente y útil para la toma de decisiones.

Además de organizar la información, el análisis permitió detectar patrones relevantes de evasión de clientes, que pueden servir como insumo para estrategias de fidelización y mejora del servicio en Telecom X.
