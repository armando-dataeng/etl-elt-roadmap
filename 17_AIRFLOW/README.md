# APACHE AIRFLOW

## Definición

Apache Airflow es una plataforma open-source utilizada para orquestar, programar y monitorear workflows de datos.

Permite automatizar pipelines complejos mediante la definición de tareas y dependencias.

---

# ¿Por qué existe?

Imaginemos un pipeline:

```text
Extract Customers
        ↓

Transform Customers
        ↓

Load Data Warehouse
        ↓

Refresh Dashboard
```

---

Pregunta:

```text
¿Quién ejecuta estas tareas
en el orden correcto?
```

---

Respuesta:

```text
Apache Airflow
```

---

# ¿Qué problema resuelve?

Sin Airflow:

```text
Scripts manuales

Cron Jobs

Procesos aislados

Poco monitoreo
```

---

Resultado:

```text
Difícil mantenimiento.
```

---

Con Airflow:

```text
Automatización

Dependencias

Monitoreo

Alertas

Retries
```

---

# Arquitectura General

```text
Data Sources
      ↓

Airflow DAG
      ↓

ETL / ELT
      ↓

Data Warehouse
```

---

# Conceptos Fundamentales

## DAG

DAG significa:

```text
Directed Acyclic Graph
```

---

Representa:

```text
Un workflow.
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

Cada nodo es una tarea.

---

# Task

Unidad básica de trabajo.

---

Ejemplos:

```text
Extract Customers

Transform Orders

Load FactSales
```

---

# Operator

Define qué hace una tarea.

---

Ejemplos:

- PythonOperator
- BashOperator
- SQL Operators
- DockerOperator

---

Conceptualmente:

```text
Task
+
Operator
=
Trabajo ejecutable
```

---

# Dependency

Define relaciones entre tareas.

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

Transform depende de:

```text
Extract
```

---

# Scheduler

Componente encargado de:

```text
Programar ejecuciones.
```

---

Ejemplos:

```text
Cada hora

Cada día

Cada semana
```

---

# Executor

Componente encargado de:

```text
Ejecutar tareas.
```

---

Tipos comunes:

- SequentialExecutor
- LocalExecutor
- CeleryExecutor
- KubernetesExecutor

---

# Web UI

Interfaz gráfica de Airflow.

---

Permite:

- Ver DAGs
- Monitorear ejecuciones
- Consultar logs
- Reiniciar tareas

---

# Ejemplo Visual

```text
Extract Customers
          ↓

Transform Customers
          ↓

Load Customers
```

---

Representado como un DAG.

---

# Ejemplo Básico

```python
from airflow import DAG
from airflow.operators.python import PythonOperator
```

---

Conceptualmente:

```text
Crear DAG
↓
Crear Tasks
↓
Definir Dependencias
```

---

# Scheduling

Airflow permite programar workflows.

---

Ejemplo:

```text
@daily
```

---

Resultado:

```text
Ejecución diaria.
```

---

# Retries

Reintentos automáticos.

---

Ejemplo:

```text
Task falla
      ↓

Retry
      ↓

Éxito
```

---

Beneficio:

```text
Mayor resiliencia.
```

---

# Logging

Cada tarea genera logs.

---

Ejemplo:

```text
Inicio

Procesamiento

Fin
```

---

Muy útil para debugging.

---

# Monitoring

Airflow permite monitorear:

- DAG Runs
- Task Runs
- Duración
- Errores

---

Pregunta:

```text
¿Falló una tarea?
```

---

Respuesta:

```text
Visible en Airflow UI.
```

---

# Alerting

Integración con:

- Email
- Slack
- Teams

---

Cuando:

```text
Una tarea falla.
```

---

# Caso Real

## Empresa Retail

Workflow:

```text
Extract Orders
       ↓

Transform Orders
       ↓

Load FactSales
       ↓

Refresh Power BI
```

---

Airflow coordina:

```text
Dependencias

Scheduling

Monitoring
```

---

# Casos de Uso

## ETL Pipelines

```text
Extract
↓
Transform
↓
Load
```

---

## ELT Pipelines

```text
Extract
↓
Load
↓
dbt
```

---

## Machine Learning

```text
Training
↓
Validation
↓
Deployment
```

---

## Data Warehousing

```text
Staging
↓
Dimensions
↓
Facts
```

---

# Componentes de Airflow

## DAG

Workflow completo.

---

## Task

Unidad de trabajo.

---

## Operator

Acción ejecutada.

---

## Scheduler

Planificador.

---

## Executor

Motor de ejecución.

---

## Metadata Database

Almacena:

- DAG Runs
- Logs
- Estado

---

## Web Server

Interfaz visual.

---

# Ventajas

## Open Source

Amplia comunidad.

---

## Escalable

Desde pequeños pipelines hasta plataformas empresariales.

---

## Flexible

Integración con múltiples tecnologías.

---

## Observabilidad

Excelente monitoreo.

---

# Desafíos

## Curva de aprendizaje

Puede resultar compleja inicialmente.

---

## Operación

Requiere mantenimiento.

---

## Infraestructura

Necesita componentes adicionales.

---

# Airflow + Data Engineering

Arquitectura moderna:

```text
API
Database
Files
      ↓

Airflow
      ↓

dbt
      ↓

Snowflake
      ↓

Power BI
```

---

# Buenas prácticas

## DAGs simples

Evitar dependencias innecesarias.

---

## Tareas pequeñas

Facilitan debugging.

---

## Configurar retries

Manejar errores temporales.

---

## Monitorear SLAs

Garantizar disponibilidad.

---

## Mantener código versionado

Utilizar Git.

---

# Error común

Muchos principiantes utilizan Airflow para:

```text
Procesar datos pesados.
```

---

Incorrecto.

Airflow debe:

```text
Orquestar.
```

---

No realizar transformaciones masivas.

---

# Error conceptual frecuente

Muchos creen:

```text
Airflow = ETL Tool
```

---

Incorrecto.

Airflow es:

```text
Una herramienta de orquestación.
```

---

Puede coordinar:

- ETL
- ELT
- ML Pipelines
- Data Warehouses

---

# Caso de Entrevista

Pregunta:

```text
¿Qué es un DAG en Airflow?
```

---

Respuesta:

```text
Un Directed Acyclic Graph
que representa un workflow
y las dependencias entre tareas.
```

---

# Pensamiento de Data Engineering

Antes de crear un DAG pregúntate:

1. ¿Qué tareas existen?
2. ¿Qué dependencias tienen?
3. ¿Qué ocurre si una tarea falla?
4. ¿Necesito retries?
5. ¿Cuál es el SLA?
6. ¿Cómo monitorearé el workflow?
7. ¿La solución escalará?

---

# Relación con los siguientes módulos

```text
ORCHESTRATION
        ↓
SCHEDULING
        ↓
PIPELINE MONITORING
        ↓
AIRFLOW
        ↓
DBT
        ↓
AZURE DATA FACTORY
```

---

# Resumen

Apache Airflow es una plataforma de orquestación utilizada para automatizar y monitorear workflows de datos.

Conceptos principales:

- DAGs
- Tasks
- Operators
- Dependencies
- Scheduler
- Executor
- Monitoring
- Alerting

Airflow es una de las herramientas más demandadas en Data Engineering y una pieza fundamental en arquitecturas modernas de datos.
