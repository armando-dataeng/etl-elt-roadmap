# STREAM PROCESSING

## Definición

Stream Processing es un modelo de procesamiento donde los datos son procesados continuamente a medida que son generados.

En lugar de esperar a acumular datos:

```text
Los eventos se procesan
en tiempo casi real.
```

---

# ¿Por qué existe?

Supongamos una aplicación de comercio electrónico.

Cada segundo ocurren:

```text
Nuevos pedidos

Pagos

Devoluciones

Actualizaciones de inventario
```

---

Pregunta:

```text
¿Debemos esperar hasta mañana
para procesar esta información?
```

---

Respuesta:

```text
No.
```

---

Muchos negocios necesitan:

```text
Información inmediata.
```

---

# Concepto de Stream

Un stream es:

```text
Una secuencia continua
de eventos.
```

---

Ejemplo:

```text
Pedido #1001
↓
Pedido #1002
↓
Pedido #1003
↓
Pedido #1004
```

---

Los eventos llegan constantemente.

---

# Arquitectura General

```text
Data Sources
       ↓

Event Stream
       ↓

Stream Processing
       ↓

Analytics
Applications
Dashboards
```

---

# Flujo Básico

```text
Evento
    ↓

Procesamiento
    ↓

Resultado
```

---

Todo ocurre continuamente.

---

# Ejemplo Real

## Plataforma de E-commerce

Evento:

```text
Nuevo pedido realizado.
```

---

Flujo:

```text
Pedido
    ↓

Kafka
    ↓

Stream Processor
    ↓

Dashboard
```

---

Resultado:

```text
Actualización inmediata.
```

---

# Características

## Procesamiento Continuo

Los datos nunca dejan de llegar.

---

## Baja Latencia

Respuesta rápida.

---

Ejemplo:

```text
Milisegundos

Segundos
```

---

## Eventos Individuales

Cada evento puede procesarse por separado.

---

## Escalabilidad

Diseñado para grandes volúmenes.

---

# Casos de Uso

## Detección de Fraude

Ejemplo:

```text
Tarjeta utilizada
↓
Validación inmediata
```

---

## Monitoreo IoT

Ejemplo:

```text
Sensor genera datos
cada segundo.
```

---

## Tracking de Usuarios

Ejemplo:

```text
Clicks

Navegación

Compras
```

---

## Trading Financiero

Ejemplo:

```text
Cambios de mercado
en tiempo real.
```

---

## Monitoreo de Aplicaciones

Ejemplo:

```text
Logs
Métricas
Eventos
```

---

# Arquitectura Stream

```text
Applications
      ↓

Kafka
      ↓

Stream Processing
      ↓

Storage
Analytics
```

---

# Componentes

## Producer

Genera eventos.

---

Ejemplos:

```text
Aplicación

API

Sensor IoT
```

---

## Stream

Flujo continuo de eventos.

---

## Consumer

Consume eventos.

---

Ejemplo:

```text
Aplicación analítica.
```

---

# Event-Driven Architecture

Concepto fundamental.

---

Arquitectura:

```text
Evento
      ↓

Acción
```

---

Ejemplo:

```text
Pedido Creado
      ↓

Actualizar Inventario
```

---

# Ventanas (Windows)

Muy utilizadas en Stream Processing.

---

## Definición

Agrupar eventos dentro de un período.

---

Ejemplo:

```text
Últimos 5 minutos.
```

---

Permite calcular:

```text
Promedios

Conteos

Sumatorias
```

---

# Tipos de Ventanas

## Tumbling Window

Ventanas fijas.

---

Ejemplo:

```text
00:00 - 00:05

00:05 - 00:10
```

---

## Sliding Window

Ventanas superpuestas.

---

Ejemplo:

```text
Últimos 5 minutos
actualizados continuamente.
```

---

# Stream Processing Tools

## Apache Kafka

La plataforma más popular.

---

Permite:

```text
Publicar eventos

Consumir eventos

Escalar flujos
```

---

## Azure Event Hubs

Servicio de streaming en Azure.

---

## Amazon Kinesis

Servicio de streaming en AWS.

---

## Apache Pulsar

Alternativa moderna a Kafka.

---

# Procesamiento de Streams

## Apache Spark Streaming

Permite procesar streams.

---

## Apache Flink

Diseñado específicamente para streaming.

---

## Kafka Streams

Biblioteca para procesamiento de eventos.

---

# Caso Real

## Empresa de Transporte

Evento:

```text
GPS actualizado.
```

---

Flujo:

```text
Vehículo
      ↓

Kafka
      ↓

Flink
      ↓

Dashboard
```

---

Resultado:

```text
Ubicación en tiempo real.
```

---

# Stream vs Batch

## Batch

```text
Acumular
↓
Procesar
↓
Publicar
```

---

Latencia:

```text
Horas
Minutos
```

---

## Stream

```text
Evento
↓
Procesar
↓
Publicar
```

---

Latencia:

```text
Segundos

Milisegundos
```

---

# Comparación

| Característica | Batch | Stream |
|---------------|--------|--------|
| Procesamiento | Por lotes | Continuo |
| Latencia | Alta | Baja |
| Complejidad | Menor | Mayor |
| Infraestructura | Más simple | Más compleja |
| Tiempo Real | No | Sí |
| Costos | Menores | Mayores |

---

# Desafíos

## Complejidad

Más componentes.

---

## Escalabilidad

Grandes volúmenes de eventos.

---

## Orden de Eventos

Los eventos pueden llegar desordenados.

---

## Tolerancia a Fallos

Evitar pérdida de eventos.

---

## Monitoreo

Necesidad de observabilidad constante.

---

# Buenas prácticas

## Diseñar eventos claros

Facilitar consumo.

---

## Monitorear latencia

Detectar retrasos.

---

## Implementar reintentos

Manejar fallos temporales.

---

## Garantizar idempotencia

Evitar duplicados.

---

## Diseñar para escalabilidad

Pensar en crecimiento futuro.

---

# Error común

Muchos principiantes creen:

```text
Stream Processing
=
Siempre mejor.
```

---

Incorrecto.

Muchos procesos empresariales funcionan perfectamente con:

```text
Batch Processing.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Kafka
=
Stream Processing
```

---

Incorrecto.

Kafka es:

```text
Una plataforma de eventos.
```

---

El procesamiento puede realizarse con:

- Flink
- Spark Streaming
- Kafka Streams

---

# Caso de Entrevista

Pregunta:

```text
¿Cuándo utilizarías
Stream Processing?
```

---

Respuesta:

```text
Cuando el negocio requiere
procesamiento continuo
y baja latencia,
como fraude,
IoT,
tracking o monitoreo.
```

---

# Pensamiento de Data Engineering

Antes de elegir Stream Processing pregúntate:

1. ¿Necesito tiempo real?
2. ¿Cuál es la latencia aceptable?
3. ¿Qué volumen de eventos recibiré?
4. ¿Cómo manejaré errores?
5. ¿Cómo garantizaré orden?
6. ¿Qué costo tendrá la solución?
7. ¿Realmente necesito streaming?

---

# Relación con los siguientes módulos

```text
BATCH PROCESSING
        ↓
STREAM PROCESSING
        ↓
ETL CASE STUDY
        ↓
MODERN DATA STACK
```

---

# Resumen

Stream Processing es un modelo donde los eventos se procesan continuamente conforme ocurren.

Conceptos principales:

- Events
- Producers
- Consumers
- Event-Driven Architecture
- Windows
- Low Latency

Tecnologías comunes:

- Apache Kafka
- Azure Event Hubs
- Amazon Kinesis
- Apache Flink
- Spark Streaming
- Kafka Streams

Stream Processing es fundamental para aplicaciones modernas que requieren procesamiento en tiempo real y análisis continuo.
