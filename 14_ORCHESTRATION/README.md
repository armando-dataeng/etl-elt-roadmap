# ORCHESTRATION

## Definición

Orchestration es el proceso de coordinar, programar, monitorear y controlar la ejecución de tareas dentro de un pipeline de datos.

Permite que múltiples procesos trabajen juntos de forma organizada.

---

# ¿Por qué existe?

Supongamos un pipeline:

```text
Extraer Clientes
↓
Extraer Pedidos
↓
Transformar Datos
↓
Cargar Data Warehouse
↓
Actualizar Dashboard
```

---

Pregunta:

```text
¿Quién garantiza que cada tarea
se ejecute en el orden correcto?
```

---

Respuesta:

```text
La Orquestación.
```

---

# Problema Sin Orquestación

```text
Pipeline A
Pipeline B
Pipeline C
```

---

Ejecutados manualmente:

```text
Errores
Retrasos
Dependencias rotas
```

---

Resultado:

```text
Procesos poco confiables.
```

---

# Solución

Utilizar un orquestador.

---

Arquitectura:

```text
Data Sources
      ↓

Pipeline A
      ↓

Pipeline B
      ↓

Pipeline C
      ↓

Data Warehouse

      ↑

Orchestrator
```

---

# Objetivos

La orquestación busca:

- Automatizar procesos.
- Gestionar dependencias.
- Programar ejecuciones.
- Monitorear pipelines.
- Recuperarse de errores.

---

# Componentes

## Tasks

Unidad básica de trabajo.

---

Ejemplo:

```text
Extraer Clientes
```

---

## Workflow

Conjunto de tareas relacionadas.

---

Ejemplo:

```text
Extraer
↓
Transformar
↓
Cargar
```

---

## Dependencies

Definen el orden de ejecución.

---

Ejemplo:

```text
Transformación
```

depende de:

```text
Extracción
```

---

# Ejemplo

```text
Task A
   ↓
Task B
   ↓
Task C
```

---

Task B no puede iniciar hasta que:

```text
Task A finalice.
```

---

# DAG

Concepto fundamental.

---

## Definición

Directed Acyclic Graph.

Representa dependencias entre tareas.

---

Ejemplo:

```text
Extract Customers
          ↓

Transform Customers
          ↓

Load Customers
```

---

# Visualización

```text
Extract
   ↓

Transform
   ↓

Load
```

---

# Ejemplo Empresarial

## Pipeline de Ventas

```text
Extract Orders
        ↓

Transform Orders
        ↓

Load FactSales
        ↓

Refresh Dashboard
```

---

Cada tarea depende de la anterior.

---

# Scheduling

Permite ejecutar procesos automáticamente.

---

Ejemplos:

```text
Cada hora

Cada día

Cada semana

Cada mes
```

---

# Dependencias

Ejemplo:

```text
Load FactSales
```

no puede iniciar si:

```text
Transform Orders
```

falló.

---

# Retries

Reintentos automáticos.

---

Ejemplo:

```text
Intento 1
↓
Error
↓
Intento 2
↓
Éxito
```

---

Beneficio:

```text
Recuperación automática.
```

---

# Monitoring

Supervisión continua.

---

Preguntas:

```text
¿Ejecutó?

¿Cuánto tardó?

¿Falló?

¿Cuántos registros procesó?
```

---

# Alerting

Notificaciones automáticas.

---

Ejemplos:

- Email
- Slack
- Teams
- PagerDuty

---

Cuando:

```text
Pipeline falla.
```

---

# Caso Real

## Empresa Retail

Proceso:

```text
ERP
↓

Extract Orders
↓

Transform Orders
↓

Load Data Warehouse
↓

Power BI
```

---

Sin orquestación:

```text
Procesos manuales.
```

---

Con orquestación:

```text
Automatización completa.
```

---

# Herramientas de Orquestación

## Apache Airflow

La más popular.

---

Conceptos:

```text
DAGs
Tasks
Operators
Scheduling
```

---

## Azure Data Factory

Muy utilizada en Azure.

---

## Prefect

Alternativa moderna.

---

## Luigi

Framework de workflows.

---

## Dagster

Orientado a Data Engineering.

---

# Airflow Example

```python
from airflow import DAG
```

---

Conceptualmente:

```text
Extract
↓
Transform
↓
Load
```

definido como un DAG.

---

# Beneficios

## Automatización

Menos intervención manual.

---

## Confiabilidad

Procesos repetibles.

---

## Escalabilidad

Miles de tareas coordinadas.

---

## Observabilidad

Mayor visibilidad.

---

# Desafíos

## Dependencias complejas

Muchos pipelines conectados.

---

## Fallos encadenados

Una tarea puede afectar varias más.

---

## Monitoreo

Necesidad de visibilidad constante.

---

# Buenas prácticas

## Diseñar DAGs simples

Evitar complejidad innecesaria.

---

## Utilizar retries

Para errores temporales.

---

## Implementar alertas

Detectar fallos rápidamente.

---

## Registrar métricas

Tiempo de ejecución.

Registros procesados.

Errores.

---

## Diseñar tareas independientes

Facilita mantenimiento.

---

# Error común

Muchos principiantes utilizan:

```text
Scripts manuales
```

para ejecutar pipelines.

---

Resultado:

```text
Procesos difíciles de mantener.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Orchestration
=
Scheduling
```

---

Incorrecto.

Scheduling es solo una parte.

---

Orchestration incluye:

- Dependencias
- Monitoreo
- Reintentos
- Alertas
- Recuperación

---

# Caso de Entrevista

Pregunta:

```text
¿Cuál es la diferencia entre
Scheduling y Orchestration?
```

---

Respuesta:

```text
Scheduling define cuándo ejecutar.

Orchestration define cómo
coordinar todas las tareas,
dependencias y recuperaciones.
```

---

# Pensamiento de Data Engineering

Antes de diseñar un workflow pregúntate:

1. ¿Qué tareas existen?
2. ¿Qué dependencias tienen?
3. ¿Qué ocurre si una tarea falla?
4. ¿Necesito reintentos?
5. ¿Cómo monitorearé el proceso?
6. ¿Cómo alertaré problemas?
7. ¿La solución escalará?

---

# Relación con los siguientes módulos

```text
ERROR HANDLING
        ↓
ORCHESTRATION
        ↓
SCHEDULING
        ↓
PIPELINE MONITORING
```

---

# Resumen

Orchestration es el proceso de coordinar y automatizar pipelines de datos.

Conceptos principales:

- Tasks
- Workflows
- DAGs
- Dependencies
- Scheduling
- Monitoring
- Alerting
- Retries

Herramientas comunes:

- Apache Airflow
- Azure Data Factory
- Prefect
- Dagster
- Luigi

La orquestación es uno de los pilares fundamentales de cualquier plataforma moderna de Data Engineering.
