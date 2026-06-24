# ERROR HANDLING

## Definición

Error Handling es el conjunto de estrategias, procesos y mecanismos utilizados para detectar, registrar, gestionar y recuperarse de errores dentro de un pipeline de datos.

Su objetivo es garantizar que los procesos sean:

- Confiables
- Recuperables
- Observables
- Resistentes a fallos

---

# ¿Por qué existe?

Los errores son inevitables.

Ejemplos:

```text
API fuera de servicio

Base de datos inaccesible

Archivo corrupto

Falta de memoria

Timeouts

Datos inválidos
```

---

Sin manejo de errores:

```text
Pipeline falla
↓
Datos no llegan
↓
Reportes incorrectos
```

---

Con Error Handling:

```text
Pipeline detecta problema
↓
Registra incidente
↓
Notifica equipo
↓
Intenta recuperarse
```

---

# Arquitectura

```text
Data Source
      ↓

Extraction
      ↓

Validation
      ↓

Transformation
      ↓

Loading
      ↓

Data Warehouse

       ↑

 Error Handling
 Logging
 Monitoring
 Alerting
```

---

# Tipos de Errores

## Errores de Conectividad

Ejemplos:

```text
API caída

Base de datos no disponible

DNS incorrecto
```

---

## Errores de Datos

Ejemplos:

```text
Valores nulos

Duplicados

Formato inválido
```

---

## Errores de Negocio

Ejemplos:

```text
Monto negativo

Cliente inexistente

Estado inválido
```

---

## Errores de Infraestructura

Ejemplos:

```text
Falta de memoria

Disco lleno

Problemas de red
```

---

## Errores de Aplicación

Ejemplos:

```text
Bug en código

SQL incorrecto

Excepción no controlada
```

---

# Estrategias de Manejo

## Fail Fast

Detener inmediatamente el proceso.

---

Ejemplo:

```text
No existe conexión
a la base de datos.
```

---

Resultado:

```text
Pipeline detenido.
```

---

Ventaja:

```text
Evita corrupción de datos.
```

---

# Retry

Reintentar automáticamente.

---

Ejemplo:

```text
API devuelve error temporal.
```

---

Estrategia:

```text
Intento 1

Intento 2

Intento 3
```

---

Resultado:

```text
Recuperación automática.
```

---

# Exponential Backoff

Incrementar tiempo entre reintentos.

---

Ejemplo:

```text
1 segundo

2 segundos

4 segundos

8 segundos
```

---

Beneficio:

```text
Reduce presión sobre sistemas.
```

---

# Skip and Continue

Ignorar registros problemáticos.

---

Ejemplo:

```text
1 registro inválido
```

---

Resultado:

```text
Procesar resto de registros.
```

---

# Quarantine Zone

Enviar datos inválidos a una zona separada.

---

Arquitectura:

```text
Valid Records
      ↓

Data Warehouse

Invalid Records
      ↓

Quarantine
```

---

Beneficio:

```text
No se pierden datos.
```

---

# Logging

## Definición

Registrar eventos del pipeline.

---

Ejemplo:

```text
Inicio ejecución

Fin ejecución

Error encontrado

Cantidad procesada
```

---

Registro:

```text
2024-01-01 08:00

Pipeline iniciado
```

---

# Niveles de Logging

## INFO

Eventos normales.

---

## WARNING

Posibles problemas.

---

## ERROR

Fallo importante.

---

## CRITICAL

Proceso detenido.

---

# Monitoring

Supervisión continua.

---

Preguntas:

```text
¿Pipeline ejecutó?

¿Cuánto tardó?

¿Cuántos registros procesó?

¿Falló?
```

---

# Alerting

Notificaciones automáticas.

---

Ejemplos:

```text
Email

Slack

Microsoft Teams

PagerDuty
```

---

Cuando:

```text
Pipeline falla.
```

---

# Dead Letter Queue (DLQ)

Muy utilizada en sistemas distribuidos.

---

Definición:

```text
Cola para mensajes fallidos.
```

---

Arquitectura:

```text
Message Queue
       ↓

Procesamiento
       ↓

Error
       ↓

Dead Letter Queue
```

---

Beneficio:

```text
No perder eventos.
```

---

# Idempotencia

## Definición

Ejecutar varias veces produce el mismo resultado.

---

Ejemplo:

```text
Ejecutar pipeline 2 veces
```

---

Resultado:

```text
Sin duplicados.
```

---

Muy importante para recuperación.

---

# Caso Real

## API de Clientes

Proceso:

```text
Extract
↓
Transform
↓
Load
```

---

Problema:

```text
API responde 500.
```

---

Solución:

```text
Retry
↓
Exponential Backoff
↓
Alerting
```

---

# Caso Real

## Archivo CSV

Problema:

```text
Archivo corrupto.
```

---

Solución:

```text
Mover a Quarantine
↓
Notificar equipo
```

---

# Error Handling en ETL

```text
Extract
      ↓

Error Handling
      ↓

Transform
      ↓

Load
```

---

# Error Handling en ELT

```text
Extract
      ↓

Load
      ↓

Validation
      ↓

Error Handling
      ↓

Transform
```

---

# Herramientas Comunes

## Orquestación

- Apache Airflow
- Azure Data Factory
- Prefect

---

## Observabilidad

- Datadog
- Grafana
- Prometheus

---

## Alertas

- Slack
- Teams
- PagerDuty

---

# Buenas prácticas

## Registrar todos los errores

Nunca ignorarlos.

---

## Implementar reintentos

Para errores temporales.

---

## Diseñar procesos idempotentes

Evitar duplicados.

---

## Crear alertas automáticas

Reducir tiempo de respuesta.

---

## Mantener auditoría

Toda ejecución debe ser trazable.

---

# Error común

Muchos principiantes utilizan:

```text
TRY
CATCH
```

y creen que eso es suficiente.

---

No lo es.

---

Error Handling incluye:

- Logging
- Alerting
- Monitoring
- Recovery
- Auditoría

---

# Error conceptual frecuente

Muchos creen:

```text
Error Handling
=
Corregir errores
```

---

Incorrecto.

También implica:

```text
Detectar

Registrar

Notificar

Recuperar

Prevenir
```

---

# Caso de Entrevista

Pregunta:

```text
¿Qué harías si una API crítica
deja de responder?
```

---

Respuesta:

```text
Implementar retries,
exponential backoff,
logging,
alerting
y mecanismos de recuperación.
```

---

# Pensamiento de Data Engineering

Antes de desplegar un pipeline pregúntate:

1. ¿Qué puede fallar?
2. ¿Cómo detectaré el error?
3. ¿Cómo registraré el problema?
4. ¿Cómo alertaré al equipo?
5. ¿Puedo reintentar?
6. ¿Perderé datos?
7. ¿Cómo recuperaré el proceso?

---

# Relación con los siguientes módulos

```text
DATA QUALITY
        ↓
DATA VALIDATION
        ↓
ERROR HANDLING
        ↓
ORCHESTRATION
        ↓
SCHEDULING
```

---

# Resumen

Error Handling permite construir pipelines resilientes y confiables.

Conceptos principales:

- Retry
- Exponential Backoff
- Logging
- Monitoring
- Alerting
- Quarantine Zone
- Dead Letter Queue
- Idempotencia

Los mejores Data Engineers no diseñan sistemas que nunca fallan.

Diseñan sistemas que se recuperan correctamente cuando fallan.
