# MODERN DATA STACK

## Definición

Modern Data Stack (MDS) es un conjunto de herramientas, prácticas y arquitecturas modernas utilizadas para construir plataformas de datos escalables, flexibles y orientadas al análisis.

Su objetivo es simplificar:

- Ingesta de datos
- Transformación
- Almacenamiento
- Orquestación
- Monitoreo
- Analítica

---

# ¿Por qué existe?

Arquitectura tradicional:

```text
ETL
      ↓

Data Warehouse
      ↓

Reporting
```

---

Problemas:

```text
Infraestructura compleja

Escalabilidad limitada

Costos elevados

Procesos lentos
```

---

La nube cambió este modelo.

---

# Filosofía Moderna

En lugar de:

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
Transform
```

---

Es decir:

```text
ELT
```

---

# Arquitectura General

```text
Data Sources
        ↓

Ingestion
        ↓

Cloud Storage
        ↓

Data Warehouse
        ↓

Transformations
        ↓

Analytics
```

---

# Componentes Principales

## Data Sources

Origen de datos.

---

Ejemplos:

```text
Databases

APIs

Files

Applications

Streaming
```

---

# Ingestion Layer

Responsable de mover datos.

---

Herramientas comunes:

- Fivetran
- Airbyte
- Azure Data Factory
- Kafka Connect

---

# Cloud Storage

Almacenamiento escalable.

---

Ejemplos:

- Amazon S3
- Azure Data Lake
- Google Cloud Storage

---

# Data Warehouse

Centro analítico moderno.

---

Ejemplos:

- Snowflake
- BigQuery
- Redshift
- Synapse

---

Características:

```text
Escalable

Cloud Native

Separación de cómputo y almacenamiento
```

---

# Transformation Layer

Responsable de transformar datos.

---

Herramienta dominante:

```text
dbt
```

---

Ejemplo:

```text
Raw Data
      ↓

Staging
      ↓

Dimensions
      ↓

Facts
```

---

# Orchestration Layer

Coordina procesos.

---

Herramientas:

- Airflow
- Prefect
- Dagster

---

Responsabilidades:

```text
Scheduling

Dependencies

Monitoring
```

---

# Analytics Layer

Consumo de datos.

---

Herramientas:

- Power BI
- Tableau
- Looker

---

Objetivo:

```text
Generar insights.
```

---

# Arquitectura Moderna Completa

```text
Applications
Databases
APIs
Files
        ↓

Fivetran / Airbyte
        ↓

Snowflake
        ↓

dbt
        ↓

Power BI
```

---

# Modern Data Stack vs Tradicional

## Tradicional

```text
ETL
      ↓

Data Warehouse
      ↓

Reports
```

---

## Moderno

```text
ELT
      ↓

Cloud DW
      ↓

dbt
      ↓

Analytics
```

---

# Herramientas Populares

## Ingestion

- Fivetran
- Airbyte
- Azure Data Factory

---

## Storage

- S3
- ADLS
- GCS

---

## Warehouse

- Snowflake
- BigQuery
- Redshift
- Synapse

---

## Transformation

- dbt

---

## Orchestration

- Airflow
- Prefect
- Dagster

---

## Streaming

- Kafka
- Event Hubs
- Kinesis

---

## Visualization

- Power BI
- Tableau
- Looker

---

# Caso Real

## Empresa SaaS

Fuentes:

```text
PostgreSQL

Salesforce

Stripe

Google Analytics
```

---

Pipeline:

```text
Airbyte
      ↓

Snowflake
      ↓

dbt
      ↓

Power BI
```

---

Resultado:

```text
Reporting centralizado.
```

---

# Beneficios

## Escalabilidad

Procesar grandes volúmenes.

---

## Flexibilidad

Herramientas desacopladas.

---

## Cloud Native

Infraestructura administrada.

---

## Menor mantenimiento

Menos servidores.

---

## Desarrollo más rápido

Mayor productividad.

---

# Desafíos

## Costos Cloud

Controlar consumo.

---

## Complejidad de herramientas

Muchas piezas integradas.

---

## Gobernanza

Gestionar accesos y calidad.

---

## Observabilidad

Monitorear toda la plataforma.

---

# Data Engineer en el Modern Data Stack

Responsabilidades:

```text
Diseñar pipelines

Implementar ELT

Orquestar procesos

Garantizar calidad

Optimizar costos

Monitorear plataformas
```

---

# Arquitectura de Referencia

```text
PostgreSQL
Salesforce
Stripe
        ↓

Airbyte
        ↓

Snowflake
        ↓

dbt
        ↓

Airflow
        ↓

Power BI
```

---

# Evolución del Data Engineer

## Nivel Inicial

```text
SQL
```

---

## Nivel Intermedio

```text
Data Modeling

ETL

Data Warehouse
```

---

## Nivel Avanzado

```text
Airflow

dbt

Cloud

Streaming
```

---

## Nivel Senior

```text
Arquitecturas

Gobernanza

Observabilidad

Optimización
```

---

# Buenas prácticas

## Diseñar ELT

Aprovechar Data Warehouses modernos.

---

## Automatizar todo

Reducir procesos manuales.

---

## Implementar Data Quality

Desde el inicio.

---

## Monitorear costos

Especialmente en cloud.

---

## Diseñar arquitecturas modulares

Facilitar evolución.

---

# Error común

Muchos equipos adoptan:

```text
Herramientas modernas
```

---

Pero mantienen:

```text
Procesos antiguos.
```

---

Resultado:

```text
Mayor complejidad
sin beneficios reales.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Modern Data Stack
=
Conjunto de herramientas.
```

---

Incorrecto.

También es:

```text
Una filosofía arquitectónica.
```

---

Basada en:

- Cloud
- ELT
- Automatización
- Escalabilidad
- Observabilidad

---

# Caso de Entrevista

Pregunta:

```text
¿Qué es el Modern Data Stack?
```

---

Respuesta:

```text
Es una arquitectura moderna
de datos basada en herramientas cloud,
ELT, Data Warehouses escalables,
orquestación, transformación y analítica,
que permite construir plataformas
de datos flexibles y escalables.
```

---

# Pensamiento de Data Engineering

Antes de diseñar una plataforma moderna pregúntate:

1. ¿Dónde vivirán los datos?
2. ¿Cómo los moveré?
3. ¿Dónde transformaré la información?
4. ¿Cómo orquestaré procesos?
5. ¿Cómo garantizaré calidad?
6. ¿Cómo monitorearé la plataforma?
7. ¿Cómo controlaré costos?

---

# Resumen

Modern Data Stack es el conjunto de arquitecturas y herramientas utilizadas en plataformas modernas de datos.

Componentes principales:

- Ingestion
- Cloud Storage
- Data Warehouse
- dbt
- Airflow
- Streaming
- Analytics

Herramientas comunes:

- Airbyte
- Fivetran
- Snowflake
- BigQuery
- dbt
- Airflow
- Kafka
- Power BI

Representa el enfoque predominante en Data Engineering moderno y la evolución natural de las arquitecturas tradicionales de ETL.
