# SCHEDULING

## Definición

Scheduling es el proceso de definir cuándo y con qué frecuencia se ejecutan los pipelines de datos.

Permite automatizar tareas sin intervención manual.

---

# ¿Por qué existe?

Imaginemos un pipeline:

```text
Extraer Ventas
↓
Transformar Datos
↓
Cargar Data Warehouse
```

---

Pregunta:

```text
¿Cuándo debe ejecutarse?
```

---

Opciones:

```text
Cada hora

Cada día

Cada semana

Cada mes
```

---

La respuesta depende de:

- Requisitos del negocio
- Latencia aceptable
- Costos
- Infraestructura

---

# Arquitectura

```text
Pipeline
      ↑

Scheduling
      ↓

Execution
```

---

# Objetivos

Scheduling busca:

- Automatizar ejecuciones
- Reducir tareas manuales
- Garantizar consistencia
- Cumplir SLAs
- Optimizar recursos

---

# Tipos de Scheduling

## Manual

Ejecución iniciada por una persona.

---

Ejemplo:

```text
Ejecutar Pipeline
```

---

Desventajas:

- Propenso a errores
- No escalable

---

# Time-Based Scheduling

Basado en tiempo.

---

Ejemplos:

```text
Cada hora

Cada día

Cada lunes

Cada mes
```

---

Muy común en ETL tradicional.

---

# Event-Based Scheduling

Basado en eventos.

---

Ejemplos:

```text
Archivo recibido

Mensaje Kafka

API completada

Proceso terminado
```

---

Arquitectura:

```text
Evento
      ↓

Pipeline
```

---

# Dependency-Based Scheduling

Basado en dependencias.

---

Ejemplo:

```text
Extract Orders
      ↓

Transform Orders
      ↓

Load Orders
```

---

Cada tarea espera a la anterior.

---

# Batch Scheduling

Procesamiento por lotes.

---

Ejemplo:

```text
02:00 AM
```

todos los días.

---

Ventajas:

- Menor costo
- Fácil implementación

---

Desventajas:

- Mayor latencia

---

# Near Real-Time Scheduling

Actualizaciones frecuentes.

---

Ejemplo:

```text
Cada 5 minutos
```

---

Uso común:

```text
Dashboards operativos
```

---

# Real-Time Scheduling

Procesamiento continuo.

---

Ejemplo:

```text
Kafka
↓
Streaming
↓
Procesamiento
```

---

Latencia:

```text
Segundos
o milisegundos
```

---

# Frecuencia de Ejecución

## Hourly

```text
Cada hora
```

---

Uso:

```text
Ventas
Inventario
```

---

# Daily

```text
Cada día
```

---

Uso:

```text
Data Warehouses
```

---

# Weekly

```text
Cada semana
```

---

Uso:

```text
Reportes ejecutivos
```

---

# Monthly

```text
Cada mes
```

---

Uso:

```text
Cierres financieros
```

---

# Cron Expressions

Muy utilizadas en herramientas de orquestación.

---

## Ejemplo

```text
0 2 * * *
```

---

Significa:

```text
Ejecutar todos los días
a las 02:00 AM
```

---

## Ejemplos comunes

Cada hora:

```text
0 * * * *
```

---

Cada día a medianoche:

```text
0 0 * * *
```

---

Cada lunes:

```text
0 0 * * 1
```

---

# Batch Window

## Definición

Ventana de tiempo disponible para ejecutar procesos.

---

Ejemplo:

```text
12:00 AM
↓
05:00 AM
```

---

Durante este período:

```text
Se ejecutan pipelines.
```

---

# SLA

## Definición

Service Level Agreement.

Tiempo máximo esperado para completar un proceso.

---

Ejemplo:

```text
Pipeline inicia:
01:00 AM

Pipeline termina:
02:00 AM
```

---

SLA:

```text
1 hora
```

---

# Missed Schedule

Ocurre cuando una ejecución programada no sucede.

---

Ejemplo:

```text
Servidor caído.
```

---

Problema:

```text
Datos desactualizados.
```

---

# Catch-Up

Permite recuperar ejecuciones perdidas.

---

Ejemplo:

```text
Pipeline no ejecutó
durante 2 días.
```

---

Al restaurarse:

```text
Ejecuta cargas pendientes.
```

---

# Caso Real

## Empresa Retail

Pipeline:

```text
Extract Orders
↓
Transform Orders
↓
Load FactSales
```

---

Frecuencia:

```text
Cada hora.
```

---

Objetivo:

```text
Dashboard actualizado.
```

---

# Scheduling con Airflow

Ejemplo conceptual:

```python
schedule="@daily"
```

---

Resultado:

```text
Ejecución diaria.
```

---

# Scheduling con Azure Data Factory

Opciones:

- Horario
- Evento
- Trigger

---

# Scheduling con dbt

Normalmente combinado con:

- Airflow
- GitHub Actions
- Azure Data Factory

---

# Buenas prácticas

## Definir frecuencia correcta

No ejecutar más veces de las necesarias.

---

## Considerar SLAs

Alinear con necesidades del negocio.

---

## Evitar conflictos

No ejecutar procesos dependientes simultáneamente.

---

## Monitorear ejecuciones

Detectar retrasos.

---

## Configurar alertas

Notificar fallos automáticamente.

---

# Error común

Muchos equipos programan:

```text
Cada minuto
```

---

sin necesidad.

---

Resultado:

```text
Costos elevados.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Más frecuencia
=
Mejor solución
```

---

Incorrecto.

La frecuencia debe estar alineada con:

- Necesidades del negocio
- Costos
- Infraestructura

---

# Caso de Entrevista

Pregunta:

```text
¿Cómo decidirías la frecuencia
de un pipeline?
```

---

Respuesta:

```text
Analizando requerimientos,
latencia aceptable,
SLA,
costos
y volumen de datos.
```

---

# Pensamiento de Data Engineering

Antes de programar un pipeline pregúntate:

1. ¿Qué tan frescos deben ser los datos?
2. ¿Cuál es el SLA?
3. ¿Qué volumen procesaré?
4. ¿Existen dependencias?
5. ¿Qué ocurre si una ejecución falla?
6. ¿Necesito catch-up?
7. ¿Cuál es el costo de la frecuencia elegida?

---

# Relación con los siguientes módulos

```text
ORCHESTRATION
        ↓
SCHEDULING
        ↓
PIPELINE MONITORING
```

---

# Resumen

Scheduling define cuándo se ejecutan los pipelines de datos.

Tipos principales:

- Manual
- Time-Based
- Event-Based
- Dependency-Based

Conceptos importantes:

- Cron Expressions
- Batch Windows
- SLAs
- Catch-Up
- Triggers

Un buen Scheduling garantiza que los datos estén disponibles cuando el negocio los necesita, sin desperdiciar recursos.
