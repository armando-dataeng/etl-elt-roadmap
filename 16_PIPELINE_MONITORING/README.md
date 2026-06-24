# PIPELINE MONITORING

## Definición

Pipeline Monitoring es el proceso de supervisar, medir y analizar el comportamiento de los pipelines de datos para garantizar que funcionen correctamente.

Su objetivo es detectar problemas antes de que impacten al negocio.

---

# ¿Por qué existe?

Supongamos un pipeline:

```text
Extract
↓
Transform
↓
Load
```

---

Pregunta:

```text
¿Terminó correctamente?
```

---

Segunda pregunta:

```text
¿Procesó todos los datos?
```

---

Tercera pregunta:

```text
¿Cumplió el SLA?
```

---

Pipeline Monitoring responde estas preguntas.

---

# Objetivos

Pipeline Monitoring busca:

- Detectar fallos rápidamente.
- Medir rendimiento.
- Verificar SLAs.
- Garantizar disponibilidad.
- Mejorar confiabilidad.

---

# Arquitectura

```text
Data Sources
       ↓

Pipeline
       ↓

Data Warehouse

       ↑

Monitoring
Logging
Alerting
Metrics
```

---

# ¿Qué debemos monitorear?

## Estado de ejecución

Preguntas:

```text
¿Ejecutó?

¿Terminó?

¿Falló?
```

---

Estados comunes:

```text
Running

Success

Failed

Cancelled
```

---

# Tiempo de ejecución

Métrica:

```text
Execution Time
```

---

Ejemplo:

```text
Inicio:
01:00 AM

Fin:
01:10 AM
```

---

Duración:

```text
10 minutos
```

---

# Volumen procesado

Cantidad de registros.

---

Ejemplo:

```text
100,000 registros
```

---

Pregunta:

```text
¿Es normal?
```

---

Si normalmente procesamos:

```text
1,000,000
```

y hoy:

```text
100,000
```

---

Existe una anomalía.

---

# Tasa de errores

Error Rate.

---

Ejemplo:

```text
10 registros fallidos
```

de:

```text
10,000
```

---

Resultado:

```text
0.1%
```

---

# Latencia

Tiempo entre:

```text
Generación del dato
```

y

```text
Disponibilidad para análisis
```

---

Ejemplo:

```text
Evento:
10:00

Dashboard:
10:02
```

---

Latencia:

```text
2 minutos
```

---

# SLA Monitoring

## Definición

Verificar cumplimiento de acuerdos de servicio.

---

Ejemplo:

```text
Pipeline debe finalizar
antes de las 06:00 AM
```

---

Resultado:

```text
SLA cumplido
```

o

```text
SLA incumplido
```

---

# Logging

Monitoreo depende de buenos logs.

---

Ejemplo:

```text
Pipeline iniciado

Conexión exitosa

10000 registros procesados

Pipeline finalizado
```

---

Beneficio:

```text
Facilita diagnóstico.
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

Cuando:

```text
SLA no se cumple.
```

---

Cuando:

```text
Volumen anormal.
```

---

# Dashboards Operativos

Visualización centralizada.

---

Métricas comunes:

- Ejecuciones exitosas
- Fallos
- Duración
- Volumen procesado
- Latencia

---

Ejemplo:

```text
Pipeline Health Dashboard
```

---

# Observabilidad

Concepto moderno.

---

Pregunta:

```text
¿Qué está ocurriendo
dentro del pipeline?
```

---

Incluye:

- Logs
- Métricas
- Trazabilidad
- Alertas

---

# Monitoreo de Calidad

No solo monitorear:

```text
Infraestructura
```

---

También:

```text
Calidad de datos
```

---

Ejemplos:

- Nulos
- Duplicados
- Valores inválidos

---

# Caso Real

## Empresa Retail

Pipeline:

```text
Orders
↓
Transform
↓
FactSales
```

---

Volumen esperado:

```text
50,000 registros
```

---

Volumen recibido:

```text
500 registros
```

---

Monitoreo detecta:

```text
Anomalía.
```

---

Alerta enviada.

---

Problema resuelto antes de afectar reportes.

---

# Métricas Importantes

## Availability

Porcentaje de tiempo operativo.

---

Ejemplo:

```text
99.9%
```

---

# Success Rate

Porcentaje de ejecuciones exitosas.

---

Ejemplo:

```text
98%
```

---

# Mean Time To Detect (MTTD)

Tiempo promedio para detectar fallos.

---

Objetivo:

```text
Lo más bajo posible.
```

---

# Mean Time To Recovery (MTTR)

Tiempo promedio para recuperar un servicio.

---

Objetivo:

```text
Recuperación rápida.
```

---

# Herramientas de Monitoreo

## Data Engineering

- Apache Airflow
- Prefect
- Dagster

---

## Observabilidad

- Datadog
- Grafana
- Prometheus

---

## Cloud

- Azure Monitor
- AWS CloudWatch
- Google Cloud Monitoring

---

# Monitoreo en Airflow

Información disponible:

- Estado DAG
- Duración
- Logs
- Retries
- Fallos

---

# Monitoreo en Azure Data Factory

Información disponible:

- Pipeline Runs
- Trigger Runs
- Activity Runs

---

# Buenas prácticas

## Monitorear todo

No solo errores.

---

## Definir SLAs

Medir cumplimiento continuamente.

---

## Crear alertas automáticas

Reducir tiempo de respuesta.

---

## Registrar métricas históricas

Identificar tendencias.

---

## Monitorear calidad de datos

No solo infraestructura.

---

# Error común

Muchos equipos monitorean:

```text
Pipeline Success
```

---

Pero ignoran:

```text
Volumen

Calidad

Latencia
```

---

Resultado:

```text
Pipeline exitoso
con datos incorrectos.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Monitoring
=
Ver logs
```

---

Incorrecto.

Monitoring incluye:

- Logs
- Métricas
- Alertas
- Dashboards
- Observabilidad

---

# Caso de Entrevista

Pregunta:

```text
¿Qué métricas monitorearías
en un pipeline crítico?
```

---

Respuesta:

```text
Execution Time

Success Rate

Volume Processed

Latency

Error Rate

SLA Compliance

Data Quality Metrics
```

---

# Pensamiento de Data Engineering

Antes de desplegar un pipeline pregúntate:

1. ¿Cómo sabré que funciona?
2. ¿Qué métricas debo medir?
3. ¿Qué alertas necesito?
4. ¿Cómo detectaré anomalías?
5. ¿Cómo monitorearé SLAs?
6. ¿Cómo reduciré el MTTR?
7. ¿Cómo garantizaré observabilidad?

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
```

---

# Resumen

Pipeline Monitoring permite supervisar y garantizar el correcto funcionamiento de los pipelines de datos.

Conceptos principales:

- Execution Monitoring
- Logging
- Alerting
- SLAs
- Latency
- Error Rate
- Observability

Herramientas comunes:

- Airflow
- Grafana
- Datadog
- Prometheus
- Azure Monitor
- CloudWatch

Un pipeline en producción no termina cuando se despliega.

Termina cuando puede ser monitoreado, observado y mantenido de forma confiable.
