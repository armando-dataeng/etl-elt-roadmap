# BATCH PROCESSING

## Definición

Batch Processing es un modelo de procesamiento donde los datos se recopilan durante un período de tiempo y luego se procesan en grupos (batches).

En lugar de procesar cada evento individualmente:

```text
Se procesan conjuntos de datos.
```

---

# ¿Por qué existe?

Supongamos una empresa de retail.

Durante el día se generan:

```text
Ventas

Pedidos

Pagos

Clientes
```

---

Pregunta:

```text
¿Necesitamos procesar
cada evento inmediatamente?
```

---

Respuesta:

```text
No siempre.
```

---

En muchos escenarios:

```text
Procesar una vez al día
es suficiente.
```

---

# Concepto de Batch

Un batch es:

```text
Un conjunto de datos
procesado como una unidad.
```

---

Ejemplo:

```text
Todas las ventas del día.
```

---

Arquitectura:

```text
Datos Generados
        ↓

Acumulación
        ↓

Batch
        ↓

Procesamiento
```

---

# Flujo General

```text
Data Sources
       ↓

Storage
       ↓

Batch Processing
       ↓

Data Warehouse
       ↓

Reporting
```

---

# Ejemplo Real

## Ventas Diarias

Durante el día:

```text
100,000 ventas
```

---

A las:

```text
02:00 AM
```

---

Se ejecuta:

```text
Batch Job
```

---

Resultado:

```text
FactSales actualizada.
```

---

# Características

## Procesamiento Periódico

Ejemplos:

```text
Cada hora

Cada noche

Cada semana

Cada mes
```

---

## Grandes Volúmenes

Procesa:

```text
Miles

Millones

Billones de registros
```

---

## Mayor Throughput

Optimizado para volumen.

---

## Mayor Latencia

Los datos no están disponibles inmediatamente.

---

# Arquitectura Batch

```text
ERP
CRM
APIs
Files
      ↓

Batch Job
      ↓

Data Lake
      ↓

Data Warehouse
```

---

# Casos de Uso

## Data Warehousing

Muy común.

---

Ejemplo:

```text
Carga nocturna.
```

---

## Reportes Empresariales

Ejemplo:

```text
Ventas diarias.
```

---

## Facturación

Ejemplo:

```text
Cierre mensual.
```

---

## Procesamiento Financiero

Ejemplo:

```text
Liquidaciones.
```

---

## Machine Learning

Ejemplo:

```text
Entrenamiento nocturno.
```

---

# Herramientas Comunes

## Apache Spark

Procesamiento distribuido.

---

## Hadoop

Procesamiento masivo.

---

## Azure Data Factory

Orquestación batch.

---

## Airflow

Programación de procesos.

---

## dbt

Transformaciones batch.

---

# Ventajas

## Simplicidad

Fácil implementación.

---

## Menor costo

Comparado con sistemas en tiempo real.

---

## Escalabilidad

Ideal para grandes volúmenes.

---

## Procesamiento eficiente

Optimizado para throughput.

---

# Desventajas

## Latencia

Los datos no son inmediatos.

---

Ejemplo:

```text
Venta realizada:
10:00 AM

Disponible:
02:00 AM siguiente día
```

---

## Procesamiento tardío

No adecuado para decisiones instantáneas.

---

# Batch Window

## Definición

Período disponible para ejecutar procesos batch.

---

Ejemplo:

```text
12:00 AM
↓
05:00 AM
```

---

Durante esa ventana:

```text
Se ejecutan ETLs.
```

---

# SLA

Ejemplo:

```text
Pipeline inicia:
01:00 AM

Pipeline finaliza:
02:00 AM
```

---

SLA:

```text
1 hora
```

---

# Caso Real

## Empresa Retail

Objetivo:

```text
Actualizar dashboard
cada mañana.
```

---

Solución:

```text
Batch Processing
a las 02:00 AM.
```

---

Resultado:

```text
Datos listos
antes del inicio laboral.
```

---

# Batch vs Real-Time

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
Minutos
Horas
Días
```

---

## Real-Time

```text
Evento
↓
Procesamiento
↓
Resultado
```

---

Latencia:

```text
Segundos
Milisegundos
```

---

# Batch vs Stream Processing

| Característica | Batch | Stream |
|---------------|--------|--------|
| Procesamiento | Por lotes | Continuo |
| Latencia | Alta | Baja |
| Complejidad | Menor | Mayor |
| Costo | Menor | Mayor |
| Casos de Uso | DW, BI | Tiempo Real |

---

# Caso de Entrevista

Pregunta:

```text
¿Cuándo utilizarías
Batch Processing?
```

---

Respuesta:

```text
Cuando la latencia no es crítica
y se requiere procesar grandes
volúmenes de datos de forma eficiente.
```

---

# Buenas prácticas

## Definir ventanas batch

Evitar conflictos con usuarios.

---

## Monitorear tiempos

Controlar duración.

---

## Diseñar procesos idempotentes

Evitar duplicados.

---

## Implementar alertas

Detectar retrasos.

---

## Optimizar cargas

Reducir consumo de recursos.

---

# Error común

Muchos principiantes creen:

```text
Tiempo real
=
Siempre mejor
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
Batch Processing
=
Tecnología antigua
```

---

Incorrecto.

Actualmente sigue siendo fundamental en:

- Data Warehouses
- BI
- ETL
- Analytics
- Machine Learning

---

# Pensamiento de Data Engineering

Antes de elegir Batch Processing pregúntate:

1. ¿Cuál es la latencia aceptable?
2. ¿Qué volumen procesaré?
3. ¿Cuál es el SLA?
4. ¿Qué costo tiene el procesamiento?
5. ¿Necesito tiempo real?
6. ¿Qué infraestructura utilizaré?
7. ¿La solución escalará?

---

# Relación con los siguientes módulos

```text
AZURE DATA FACTORY
        ↓
BATCH PROCESSING
        ↓
STREAM PROCESSING
        ↓
ETL CASE STUDY
```

---

# Resumen

Batch Processing es un modelo donde los datos se procesan en grupos o lotes.

Características principales:

- Procesamiento periódico
- Grandes volúmenes
- Mayor throughput
- Mayor latencia

Herramientas comunes:

- Apache Spark
- Hadoop
- Airflow
- Azure Data Factory
- dbt

Batch Processing sigue siendo uno de los pilares fundamentales de Data Engineering y Data Warehousing moderno.
