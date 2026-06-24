# CHANGE DATA CAPTURE (CDC)

## Definición

Change Data Capture (CDC) es una técnica utilizada para identificar y capturar cambios realizados en una fuente de datos.

CDC permite detectar:

- INSERT
- UPDATE
- DELETE

sin necesidad de volver a leer toda la tabla.

---

# ¿Por qué existe CDC?

Supongamos una tabla:

```text
Orders
```

con:

```text
500 millones de registros
```

---

Cada día cambian:

```text
10,000 registros
```

---

Pregunta:

```text
¿Tiene sentido escanear
500 millones de filas
para encontrar 10,000 cambios?
```

---

Respuesta:

```text
No.
```

---

CDC permite capturar únicamente:

```text
Los cambios.
```

---

# Problema de las Cargas Incrementales

Las cargas incrementales suelen depender de:

```text
LastModifiedDate
```

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      LastExecutionDate;
```

---

Problemas:

- Requiere columnas de auditoría.
- Puede perder cambios.
- No detecta DELETE fácilmente.

---

CDC resuelve estos problemas.

---

# ¿Qué captura CDC?

## INSERT

Nuevo registro.

---

Antes:

| OrderID |
|----------|
| 100 |

---

Después:

| OrderID |
|----------|
| 100 |
| 101 |

---

CDC registra:

```text
INSERT
```

---

# UPDATE

Registro modificado.

---

Antes:

| OrderID | Status |
|----------|--------|
| 100 | Pending |

---

Después:

| OrderID | Status |
|----------|--------|
| 100 | Completed |

---

CDC registra:

```text
UPDATE
```

---

# DELETE

Registro eliminado.

---

Antes:

| OrderID |
|----------|
| 100 |

---

Después:

```text
Registro eliminado
```

---

CDC registra:

```text
DELETE
```

---

# Arquitectura

```text
Source Database
        ↓

      CDC
        ↓

Message Queue
        ↓

Data Pipeline
        ↓

Data Warehouse
```

---

# Cómo Funciona

CDC monitorea cambios en:

```text
Transaction Logs
```

---

No necesita consultar toda la tabla.

---

Ejemplo:

```text
INSERT OrderID = 100
UPDATE OrderID = 101
DELETE OrderID = 102
```

---

CDC captura esos eventos.

---

# Ventajas

## Rendimiento

No escanea tablas completas.

---

## Menor carga

Reduce impacto sobre producción.

---

## Tiempo casi real

Los cambios pueden procesarse inmediatamente.

---

## Escalabilidad

Ideal para grandes volúmenes.

---

# Tipos de CDC

## Log-Based CDC

El más utilizado.

---

Lee:

```text
Transaction Log
```

---

Ejemplos:

- SQL Server CDC
- MySQL Binlog
- PostgreSQL WAL

---

Ventajas:

- Muy eficiente.
- Bajo impacto.

---

# Trigger-Based CDC

Utiliza triggers.

---

Ejemplo:

```sql
CREATE TRIGGER trg_orders
AFTER INSERT
ON Orders
...
```

---

Ventajas:

- Fácil de implementar.

---

Desventajas:

- Impacta rendimiento.

---

# Query-Based CDC

Basado en consultas periódicas.

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      LastExecutionDate;
```

---

Ventajas:

- Simple.

---

Desventajas:

- Menos eficiente.

---

# CDC en SQL Server

SQL Server incluye CDC nativo.

---

Habilitar CDC:

```sql
EXEC sys.sp_cdc_enable_db;
```

---

Habilitar tabla:

```sql
EXEC sys.sp_cdc_enable_table
    @source_schema = 'dbo',
    @source_name = 'Orders';
```

---

Resultado:

```text
Tablas CDC creadas automáticamente.
```

---

# CDC en PostgreSQL

Utiliza:

```text
WAL
```

Write-Ahead Log.

---

Herramientas comunes:

- Debezium
- Kafka Connect

---

# CDC + Kafka

Arquitectura moderna.

```text
Database
      ↓

Debezium
      ↓

Kafka
      ↓

Consumers
      ↓

Data Warehouse
```

---

Beneficios:

```text
Streaming
Escalabilidad
Near Real-Time
```

---

# Caso Real

## Empresa Retail

Tabla:

```text
Orders
```

---

Cambios diarios:

```text
50,000
```

---

Volumen total:

```text
300 millones
```

---

Sin CDC:

```text
Escaneo completo.
```

---

Con CDC:

```text
Solo cambios.
```

---

Resultado:

```text
Menor costo.
Mayor velocidad.
```

---

# CDC y Data Warehousing

Arquitectura:

```text
ERP
CRM
E-commerce
        ↓

CDC
        ↓

Data Lake
        ↓

Data Warehouse
```

---

Permite:

```text
Actualizaciones frecuentes.
```

---

# CDC y SCD Type 2

Muy utilizados juntos.

---

Ejemplo:

```text
Cambio de dirección
```

---

CDC detecta:

```text
UPDATE
```

---

SCD Type 2 almacena:

```text
Historial.
```

---

# Buenas prácticas

## Utilizar Log-Based CDC

Siempre que sea posible.

---

## Monitorear latencia

Detectar retrasos.

---

## Implementar auditoría

Registrar eventos procesados.

---

## Manejar reintentos

Evitar pérdida de cambios.

---

## Diseñar procesos idempotentes

Procesar eventos repetidos sin errores.

---

# Error común

Muchos principiantes utilizan:

```text
SELECT *
```

sobre tablas enormes.

---

Resultado:

```text
Pipelines lentos.
```

---

CDC evita este problema.

---

# Error conceptual frecuente

Muchos creen:

```text
CDC = Incremental Load
```

---

Incorrecto.

CDC es:

```text
Una forma de detectar cambios.
```

---

Incremental Load es:

```text
Una estrategia de carga.
```

---

CDC puede alimentar cargas incrementales.

---

# Caso de Entrevista

Pregunta:

```text
¿Por qué CDC es mejor
que utilizar LastModifiedDate?
```

---

Respuesta:

```text
Porque detecta INSERT,
UPDATE y DELETE directamente
desde los logs de transacciones
sin escanear tablas completas.
```

---

# Pensamiento de Data Engineering

Antes de implementar CDC pregúntate:

1. ¿Qué base de datos utilizo?
2. ¿Existe soporte nativo para CDC?
3. ¿Necesito tiempo real?
4. ¿Cómo procesaré los eventos?
5. ¿Cómo evitaré pérdida de datos?
6. ¿Qué latencia es aceptable?
7. ¿Cómo monitorearé el pipeline?

---

# Relación con los siguientes módulos

```text
INCREMENTAL LOADS
        ↓
FULL LOADS
        ↓
CHANGE DATA CAPTURE (CDC)
        ↓
DATA QUALITY
        ↓
DATA VALIDATION
```

---

# Resumen

Change Data Capture (CDC) permite detectar cambios en sistemas fuente de forma eficiente.

Captura:

- INSERT
- UPDATE
- DELETE

Beneficios:

- Mejor rendimiento
- Menor carga sobre producción
- Procesamiento casi en tiempo real
- Escalabilidad

Tecnologías comunes:

- SQL Server CDC
- PostgreSQL WAL
- MySQL Binlog
- Debezium
- Kafka Connect

CDC es uno de los pilares de las arquitecturas modernas de Data Engineering y Real-Time Analytics.
