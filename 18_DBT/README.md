# DBT (DATA BUILD TOOL)

## Definición

dbt (Data Build Tool) es una herramienta open-source que permite transformar datos dentro de un Data Warehouse utilizando SQL.

Su filosofía principal es:

```text
Extract
↓
Load
↓
Transform
```

Es decir:

```text
ELT
```

---

# ¿Por qué existe?

En arquitecturas modernas:

```text
Snowflake
BigQuery
Databricks
Redshift
```

poseen suficiente capacidad para ejecutar transformaciones directamente.

---

Pregunta:

```text
¿Cómo gestionamos cientos
de transformaciones SQL
de manera organizada?
```

---

Respuesta:

```text
dbt
```

---

# Problema Sin dbt

Transformaciones distribuidas en:

```text
Scripts SQL

Stored Procedures

Consultas manuales

Procesos difíciles de mantener
```

---

Resultado:

```text
Código duplicado.

Poca documentación.

Difícil mantenimiento.
```

---

# Solución

dbt introduce prácticas de:

```text
Software Engineering
+
SQL
```

---

# Arquitectura Moderna

```text
Data Sources
       ↓

Extract
       ↓

Load
       ↓

Data Warehouse
       ↓

dbt
       ↓

Business Models
```

---

# Filosofía ELT

Antes:

```text
Extract
↓
Transform
↓
Load
```

---

Ahora:

```text
Extract
↓
Load
↓
Transform (dbt)
```

---

# Conceptos Fundamentales

## Models

Unidad básica de dbt.

---

Un model es:

```text
Una consulta SQL.
```

---

Ejemplo:

```sql
SELECT
    CustomerID,
    CustomerName
FROM Customers;
```

---

dbt convierte este SQL en:

```text
Tabla
o
Vista
```

---

Dentro del Data Warehouse.

---

# Sources

Representan datos de origen.

---

Ejemplo:

```text
ERP
CRM
Orders
Customers
```

---

Permiten documentar:

```text
De dónde vienen los datos.
```

---

# DAG

dbt construye automáticamente:

```text
Dependencias entre modelos.
```

---

Ejemplo:

```text
stg_customers
        ↓

dim_customers
        ↓

fact_sales
```

---

# Materializations

Definen cómo se almacena un modelo.

---

## View

Genera una vista.

---

## Table

Genera una tabla física.

---

## Incremental

Carga únicamente cambios.

---

Muy utilizado en producción.

---

# Ejemplo Conceptual

Modelo:

```sql
SELECT
    CustomerID,
    CustomerName
FROM Customers;
```

---

dbt:

```text
Compila SQL
↓
Ejecuta SQL
↓
Genera objeto en DW
```

---

# Testing

Una de las características más importantes.

---

Permite validar:

```text
NOT NULL

UNIQUE

Relationships

Accepted Values
```

---

Ejemplo:

```yaml
tests:
  - not_null
  - unique
```

---

Beneficio:

```text
Mejor Data Quality.
```

---

# Documentation

dbt genera documentación automáticamente.

---

Incluye:

```text
Modelos

Columnas

Dependencias

Descripciones
```

---

Resultado:

```text
Mayor gobernanza.
```

---

# Lineage

Permite visualizar:

```text
Origen
↓
Transformación
↓
Destino
```

---

Ejemplo:

```text
Orders
      ↓

stg_orders
      ↓

fact_sales
```

---

Muy útil para debugging.

---

# Caso Real

## Empresa Retail

Fuentes:

```text
ERP
CRM
E-commerce
```

---

Datos cargados en:

```text
Snowflake
```

---

dbt crea:

```text
stg_customers

dim_customers

fact_sales
```

---

Resultado:

```text
Modelo analítico listo.
```

---

# Capas Comunes

## Staging Layer

Limpieza inicial.

---

Ejemplo:

```text
stg_customers
stg_orders
```

---

# Intermediate Layer

Transformaciones intermedias.

---

Ejemplo:

```text
int_customer_metrics
```

---

# Mart Layer

Modelos finales.

---

Ejemplo:

```text
dim_customers

fact_sales
```

---

# dbt + Airflow

Arquitectura muy común.

```text
Airflow
      ↓

dbt
      ↓

Snowflake
```

---

Airflow:

```text
Orquesta.
```

---

dbt:

```text
Transforma.
```

---

# dbt + Data Warehouse

Compatibilidad:

- Snowflake
- BigQuery
- Databricks
- Redshift
- PostgreSQL

---

# Ventajas

## SQL First

Ideal para equipos de datos.

---

## Versionamiento

Integración con Git.

---

## Testing

Validaciones automáticas.

---

## Documentación

Generación automática.

---

## Lineage

Trazabilidad completa.

---

# Desafíos

## Curva de aprendizaje

Nuevos conceptos.

---

## Dependencia del Data Warehouse

Las transformaciones ocurren allí.

---

## Costos

Las consultas consumen recursos.

---

# Buenas prácticas

## Utilizar capas

- Staging
- Intermediate
- Mart

---

## Documentar modelos

Siempre agregar descripciones.

---

## Implementar tests

Desde el inicio.

---

## Versionar en Git

Seguir buenas prácticas de desarrollo.

---

## Diseñar modelos reutilizables

Reducir duplicación.

---

# Error común

Muchos principiantes utilizan dbt como:

```text
Herramienta ETL completa.
```

---

Incorrecto.

dbt:

```text
No extrae datos.

No carga datos.

Transforma datos.
```

---

# Error conceptual frecuente

Muchos creen:

```text
dbt reemplaza Airflow.
```

---

Incorrecto.

Airflow:

```text
Orquestación.
```

---

dbt:

```text
Transformación.
```

---

Normalmente trabajan juntos.

---

# Caso de Entrevista

Pregunta:

```text
¿Qué problema resuelve dbt?
```

---

Respuesta:

```text
Permite gestionar transformaciones
SQL dentro del Data Warehouse
utilizando prácticas modernas
de ingeniería de software.
```

---

# Pensamiento de Data Engineering

Antes de implementar dbt pregúntate:

1. ¿Dónde ocurren las transformaciones?
2. ¿Cómo versionaré el código?
3. ¿Qué validaciones necesito?
4. ¿Cómo documentaré los modelos?
5. ¿Qué dependencias existen?
6. ¿Necesito cargas incrementales?
7. ¿Cómo garantizaré Data Quality?

---

# Relación con los siguientes módulos

```text
AIRFLOW
      ↓
DBT
      ↓
AZURE DATA FACTORY
      ↓
BATCH PROCESSING
```

---

# Resumen

dbt es una herramienta de transformación de datos diseñada para arquitecturas ELT modernas.

Conceptos principales:

- Models
- Sources
- DAGs
- Materializations
- Testing
- Documentation
- Lineage

Beneficios:

- SQL First
- Versionamiento
- Data Quality
- Trazabilidad
- Documentación

dbt se ha convertido en una de las herramientas más importantes del Modern Data Stack y una habilidad altamente demandada en Data Engineering y Analytics Engineering.
