# AZURE DATA FACTORY (ADF)

## Definición

Azure Data Factory (ADF) es un servicio cloud de Microsoft utilizado para crear, orquestar y automatizar pipelines de integración de datos.

Permite mover, transformar y monitorear datos entre diferentes sistemas sin necesidad de administrar infraestructura.

---

# ¿Por qué existe?

Las organizaciones suelen tener datos distribuidos en múltiples sistemas:

```text
SQL Server
PostgreSQL
SAP
Salesforce
APIs
CSV
Azure Storage
```

---

Pregunta:

```text
¿Cómo mover todos esos datos
de forma automatizada?
```

---

Respuesta:

```text
Azure Data Factory
```

---

# ¿Qué problema resuelve?

Sin ADF:

```text
Scripts manuales

Procesos aislados

Mantenimiento complejo

Poca visibilidad
```

---

Con ADF:

```text
Pipelines visuales

Automatización

Monitoreo

Escalabilidad

Integración cloud
```

---

# Arquitectura General

```text
Data Sources
      ↓

Azure Data Factory
      ↓

Data Lake
      ↓

Data Warehouse
      ↓

Analytics
```

---

# Componentes Principales

## Pipeline

Unidad principal de trabajo.

---

Representa:

```text
Un flujo de actividades.
```

---

Ejemplo:

```text
Extract
↓
Transform
↓
Load
```

---

# Activity

Tarea individual dentro de un pipeline.

---

Ejemplos:

- Copy Data
- Execute SQL
- Data Flow
- Stored Procedure

---

# Dataset

Describe la estructura de los datos.

---

Ejemplos:

```text
CSV

JSON

SQL Table

Parquet
```

---

# Linked Service

Define la conexión a una fuente o destino.

---

Ejemplos:

```text
Azure SQL Database

Blob Storage

Snowflake

PostgreSQL
```

---

# Trigger

Permite ejecutar pipelines automáticamente.

---

Ejemplos:

```text
Cada hora

Cada día

Evento específico
```

---

# Copy Activity

Actividad más utilizada.

---

Permite:

```text
Mover datos
desde un origen
hasta un destino.
```

---

Ejemplo:

```text
SQL Server
      ↓

Copy Activity
      ↓

Azure Data Lake
```

---

# Data Flow

Permite transformar datos visualmente.

---

Operaciones comunes:

- Join
- Filter
- Aggregate
- Sort
- Derived Columns

---

Arquitectura:

```text
Source
    ↓

Transformations
    ↓

Destination
```

---

# Integration Runtime

Motor que ejecuta actividades.

---

Tipos:

## Azure Integration Runtime

Ejecuta procesos en Azure.

---

## Self-Hosted Integration Runtime

Permite conectarse a sistemas on-premises.

---

## Azure SSIS Integration Runtime

Ejecuta paquetes SSIS en Azure.

---

# Scheduling

ADF permite programar pipelines.

---

Ejemplos:

```text
Hourly

Daily

Weekly

Monthly
```

---

# Monitoring

ADF incluye monitoreo integrado.

---

Permite visualizar:

- Ejecuciones
- Duración
- Errores
- Actividades

---

Pregunta:

```text
¿Falló un pipeline?
```

---

Respuesta:

```text
Visible en Monitoring Hub.
```

---

# Error Handling

ADF soporta:

- Retries
- Alertas
- Dependencias
- Flujos condicionales

---

Ejemplo:

```text
Si falla:
    ↓
Enviar alerta
```

---

# Caso Real

## Empresa Retail

Fuentes:

```text
ERP

CRM

Salesforce

SQL Server
```

---

Proceso:

```text
Extract
↓
Azure Data Lake
↓
Transform
↓
Azure Synapse
↓
Power BI
```

---

ADF coordina todo el flujo.

---

# ADF y ETL

Arquitectura tradicional:

```text
Source
    ↓

ADF
    ↓

Transform
    ↓

Data Warehouse
```

---

# ADF y ELT

Arquitectura moderna:

```text
Source
    ↓

ADF
    ↓

Data Lake
    ↓

Synapse
    ↓

dbt
```

---

ADF mueve los datos.

---

dbt transforma los datos.

---

# Ventajas

## Low-Code

Interfaz visual.

---

## Integración Azure

Funciona de forma nativa con:

- Azure SQL
- Synapse
- Data Lake
- Power BI

---

## Escalabilidad

Procesa grandes volúmenes.

---

## Monitoreo Integrado

Visibilidad completa.

---

# Desafíos

## Dependencia del ecosistema Azure

Mayor beneficio dentro de Azure.

---

## Costos

Basados en uso.

---

## Complejidad

Pipelines empresariales pueden crecer rápidamente.

---

# Airflow vs Azure Data Factory

| Característica | Airflow | ADF |
|--------------|----------|-----|
| Open Source | Sí | No |
| Cloud Native | No | Sí |
| UI Visual | Limitada | Sí |
| Azure Integration | Media | Excelente |
| Flexibilidad | Muy alta | Alta |
| Gestión Infraestructura | Requiere configuración | Administrado |

---

# ADF vs dbt

ADF:

```text
Orquesta
Mueve datos
Automatiza pipelines
```

---

dbt:

```text
Transforma datos
dentro del Data Warehouse
```

---

# Buenas prácticas

## Diseñar pipelines modulares

Evitar procesos gigantes.

---

## Utilizar parametrización

Facilitar reutilización.

---

## Implementar monitoreo

Detectar fallos rápidamente.

---

## Configurar alertas

Reducir tiempo de respuesta.

---

## Documentar pipelines

Facilitar mantenimiento.

---

# Error común

Muchos principiantes utilizan:

```text
ADF para todas las transformaciones.
```

---

En arquitecturas modernas:

```text
ADF mueve datos

dbt transforma datos
```

---

# Error conceptual frecuente

Muchos creen:

```text
ADF reemplaza Airflow.
```

---

Incorrecto.

Ambos pueden resolver problemas similares.

---

La elección depende de:

- Arquitectura
- Cloud Provider
- Equipo
- Requisitos

---

# Caso de Entrevista

Pregunta:

```text
¿Qué es Azure Data Factory?
```

---

Respuesta:

```text
Un servicio cloud de integración
de datos que permite crear,
orquestar y monitorear pipelines
de ETL y ELT dentro del ecosistema Azure.
```

---

# Pensamiento de Data Engineering

Antes de elegir ADF pregúntate:

1. ¿Trabajo principalmente en Azure?
2. ¿Necesito integración visual?
3. ¿Qué volumen de datos procesaré?
4. ¿Necesito ETL o ELT?
5. ¿Cómo monitorearé los pipelines?
6. ¿Cómo manejaré errores?
7. ¿La solución escalará?

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
      ↓
STREAM PROCESSING
```

---

# Resumen

Azure Data Factory es una plataforma cloud para integración y orquestación de datos.

Conceptos principales:

- Pipelines
- Activities
- Datasets
- Linked Services
- Triggers
- Data Flows
- Monitoring

Beneficios:

- Low-Code
- Escalabilidad
- Integración Azure
- Automatización
- Monitoreo

ADF es una de las herramientas más utilizadas para construir pipelines empresariales en entornos Microsoft Azure.
