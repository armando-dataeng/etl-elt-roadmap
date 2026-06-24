# ETL CASE STUDY

## Objetivo

Aplicar los conceptos aprendidos a lo largo del roadmap mediante un caso real de Data Engineering.

Este caso integra:

- Data Sources
- Extraction
- Transformation
- Loading
- Data Quality
- Validation
- Error Handling
- Orchestration
- Scheduling
- Monitoring
- Airflow
- dbt
- Batch Processing

---

# Escenario

## Empresa Retail

La empresa vende productos mediante:

```text
E-commerce

ERP

CRM
```

---

La dirección necesita:

```text
Dashboard de ventas

Dashboard de clientes

Dashboard de productos
```

actualizados diariamente.

---

# Arquitectura General

```text
ERP
CRM
E-commerce
        ↓

Extraction
        ↓

Raw Layer
        ↓

Transformation
        ↓

Data Warehouse
        ↓

Power BI
```

---

# Sistemas Fuente

## CRM

Datos:

```text
Customers
```

---

## ERP

Datos:

```text
Products
Inventory
```

---

## E-commerce

Datos:

```text
Orders
Order Details
Payments
```

---

# Paso 1: Data Extraction

Extraer datos desde:

```text
CRM
ERP
E-commerce
```

---

Ejemplo:

```sql
SELECT *
FROM Customers;
```

---

Resultado:

```text
Raw Data
```

---

# Raw Layer

Almacena datos originales.

---

Ejemplo:

```text
raw_customers

raw_orders

raw_products
```

---

Objetivo:

```text
Preservar datos fuente.
```

---

# Paso 2: Data Quality

Validaciones iniciales.

---

Preguntas:

```text
¿Existen nulos?

¿Existen duplicados?

¿Existen formatos inválidos?
```

---

Ejemplo:

```sql
SELECT *
FROM Customers
WHERE Email IS NULL;
```

---

# Paso 3: Data Validation

Reglas de negocio.

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE TotalAmount <= 0;
```

---

Resultado:

```text
Pedidos inválidos detectados.
```

---

# Paso 4: Data Transformation

Limpiar y preparar datos.

---

Transformaciones:

```text
Deduplicación

Estandarización

Conversión de tipos

Enriquecimiento
```

---

Ejemplo:

Antes:

```text
USA
US
United States
```

---

Después:

```text
United States
```

---

# Modelo Staging

Capa inicial.

---

Ejemplos:

```text
stg_customers

stg_orders

stg_products
```

---

Objetivo:

```text
Normalizar datos.
```

---

# Modelo Dimensional

Diseño Star Schema.

---

Dimensiones:

```text
DimCustomer

DimProduct

DimDate
```

---

Tabla de hechos:

```text
FactSales
```

---

# Diseño

```text
DimCustomer
       ↓

FactSales

       ↑

DimProduct
       ↑

DimDate
```

---

# Paso 5: Data Loading

Carga al Data Warehouse.

---

Estrategia:

```text
Incremental Load
```

---

Método:

```text
LastModifiedDate
```

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      LastExecutionDate;
```

---

# Incremental Strategy

Primera ejecución:

```text
Full Load
```

---

Ejecuciones posteriores:

```text
Incremental Load
```

---

# Herramienta de Transformación

## dbt

Modelos:

```text
stg_customers

dim_customers

fact_sales
```

---

Beneficios:

- SQL versionado
- Testing
- Documentation

---

# Herramienta de Orquestación

## Airflow

Workflow:

```text
Extract Customers
          ↓

Extract Orders
          ↓

Run dbt
          ↓

Load Warehouse
          ↓

Refresh BI
```

---

Representado mediante:

```text
DAG
```

---

# Scheduling

Frecuencia:

```text
Diaria
```

---

Horario:

```text
02:00 AM
```

---

Objetivo:

```text
Dashboard listo
antes de iniciar la jornada.
```

---

# Monitoring

Métricas:

- Execution Time
- Records Processed
- Error Rate
- SLA Compliance

---

Ejemplo:

```text
Pipeline Duration:
15 minutos
```

---

# Error Handling

Escenarios:

## API caída

Acción:

```text
Retry
```

---

## Archivo corrupto

Acción:

```text
Quarantine Zone
```

---

## Error crítico

Acción:

```text
Alerting
```

---

# Data Warehouse Final

## Fact Table

```text
FactSales
```

---

Medidas:

```text
SalesAmount

Quantity

Profit
```

---

## Dimension Tables

```text
DimCustomer

DimProduct

DimDate
```

---

# Dashboard Final

KPIs:

```text
Ventas Totales

Clientes Activos

Productos Más Vendidos

Ingresos por Mes
```

---

# Flujo Completo

```text
CRM
ERP
E-commerce
        ↓

Extraction
        ↓

Raw Layer
        ↓

Validation
        ↓

Transformation
        ↓

dbt Models
        ↓

Data Warehouse
        ↓

Power BI
```

---

# Tecnologías Utilizadas

## Fuentes

- SQL Server
- APIs

---

## Orquestación

- Airflow

---

## Transformación

- dbt

---

## Almacenamiento

- Snowflake

---

## Visualización

- Power BI

---

# Qué aprendimos

Este caso integra:

## ETL

```text
Extract
Transform
Load
```

---

## ELT

```text
Extract
Load
Transform
```

---

## Data Quality

Validaciones automáticas.

---

## Data Warehouse

Star Schema.

---

## Incremental Loads

Procesamiento eficiente.

---

## Airflow

Orquestación.

---

## dbt

Transformaciones modernas.

---

# Caso de Entrevista

Pregunta:

```text
Describe un pipeline ETL
de extremo a extremo.
```

---

Respuesta:

```text
Extraigo datos desde múltiples fuentes,
valido calidad,
transformo mediante dbt,
cargo un Data Warehouse,
orquesto con Airflow,
implemento cargas incrementales,
monitoreo SLAs
y expongo información
mediante dashboards.
```

---

# Pensamiento de Data Engineering

Antes de diseñar un pipeline completo pregúntate:

1. ¿Cuáles son las fuentes?
2. ¿Cómo extraeré los datos?
3. ¿Qué validaciones necesito?
4. ¿Qué modelo dimensional utilizaré?
5. ¿Cómo cargaré los datos?
6. ¿Cómo automatizaré el proceso?
7. ¿Cómo monitorearé la solución?

---

# Relación con el siguiente módulo

```text
ETL CASE STUDY
        ↓
MODERN DATA STACK
```

---

# Resumen

Este caso de estudio integra los principales conceptos de Data Engineering:

- Data Sources
- Extraction
- Transformation
- Loading
- Data Quality
- Validation
- Airflow
- dbt
- Data Warehouse
- Monitoring

Representa una arquitectura moderna capaz de soportar procesos analíticos empresariales de forma escalable y confiable.
