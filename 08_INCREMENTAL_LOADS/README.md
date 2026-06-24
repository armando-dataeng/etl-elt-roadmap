# INCREMENTAL LOADS

## Definición

Incremental Loading es una estrategia de carga donde únicamente se procesan los registros nuevos o modificados desde la última ejecución.

En lugar de cargar toda la información:

```text
Solo se cargan los cambios.
```

---

# ¿Por qué existen?

Supongamos una tabla:

```text
Orders
```

con:

```text
100 millones de registros
```

---

Cada día se agregan:

```text
50,000 registros nuevos
```

---

Pregunta:

```text
¿Tiene sentido volver a cargar
100 millones de registros?
```

---

Respuesta:

```text
No.
```

---

La solución es:

```text
Incremental Load
```

---

# Full Load vs Incremental Load

## Full Load

```text
100,000,000 registros
```

↓

```text
Se cargan todos.
```

---

## Incremental Load

```text
50,000 registros nuevos
```

↓

```text
Solo se cargan esos.
```

---

# Arquitectura

```text
Source System
        ↓

Incremental Extraction
        ↓

Transformation
        ↓

Load
        ↓

Data Warehouse
```

---

# Beneficios

## Rendimiento

Menos datos procesados.

---

## Menor costo

Menor uso de:

- CPU
- Memoria
- Almacenamiento

---

## Escalabilidad

Ideal para grandes volúmenes.

---

## Menor tiempo de ejecución

Pipelines más rápidos.

---

# Estrategias de Incremental Load

Existen varias formas de detectar cambios.

---

# Método 1: Timestamp

El más común.

---

Tabla:

```text
Orders
```

---

Columnas:

```text
OrderID
LastModifiedDate
```

---

Ejemplo:

| OrderID | LastModifiedDate |
|----------|------------------|
| 100 | 2024-01-01 |
| 101 | 2024-01-02 |

---

Consulta:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      '2024-01-01';
```

---

Resultado:

```text
Solo registros nuevos
o modificados.
```

---

# Método 2: Incremental ID

Basado en claves secuenciales.

---

Tabla:

| OrderID |
|----------|
| 100 |
| 101 |
| 102 |

---

Último ID procesado:

```text
101
```

---

Consulta:

```sql
SELECT *
FROM Orders
WHERE OrderID > 101;
```

---

Resultado:

```text
Solo registros nuevos.
```

---

# Método 3: Watermark

Muy utilizado en Data Engineering.

---

## Definición

Guardar el último valor procesado.

---

Ejemplo:

```text
LastProcessedDate
=
2024-01-01 23:59:59
```

---

Próxima ejecución:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      LastProcessedDate;
```

---

# Método 4: CDC

CDC significa:

```text
Change Data Capture
```

---

Detecta:

```text
INSERT
UPDATE
DELETE
```

---

Sin escanear toda la tabla.

---

Ejemplo:

```text
Registro insertado
Registro actualizado
Registro eliminado
```

---

Muy común en:

- SQL Server CDC
- Debezium
- Kafka Connect

---

# Flujo Incremental

Primera ejecución:

```text
Carga completa.
```

---

Ejecuciones posteriores:

```text
Solo cambios.
```

---

Ejemplo:

```text
Día 1
100 registros

Día 2
5 registros nuevos

Día 3
10 registros nuevos
```

---

# Caso Real

## Empresa Retail

Tabla:

```text
Orders
```

---

Registros:

```text
50 millones
```

---

Nuevos registros diarios:

```text
25,000
```

---

Estrategia:

```text
Incremental Load
```

---

Beneficio:

```text
Menor costo.
Mayor velocidad.
```

---

# Incremental Load + Data Warehouse

Arquitectura:

```text
ERP
CRM
E-commerce
        ↓

Incremental Load
        ↓

Data Warehouse
```

---

Solo se procesan cambios.

---

# Incremental Load + MERGE

Muy común.

---

Ejemplo:

```sql
MERGE INTO Customers AS Target
USING StagingCustomers AS Source
ON Target.CustomerID =
   Source.CustomerID

WHEN MATCHED THEN
    UPDATE

WHEN NOT MATCHED THEN
    INSERT;
```

---

Beneficio:

```text
Insertar y actualizar
en una sola operación.
```

---

# Desafíos

## Datos atrasados

Late-arriving data.

---

Ejemplo:

```text
Pedido creado ayer
pero recibido hoy.
```

---

# Actualizaciones

No solo existen INSERT.

---

También:

```text
UPDATE
DELETE
```

---

# Duplicados

Reprocesamientos accidentales.

---

# Watermarks incorrectos

Pueden provocar:

```text
Pérdida de datos.
```

---

# Auditoría

Toda carga incremental debe registrar:

- Fecha ejecución
- Último watermark
- Registros procesados
- Registros exitosos
- Registros fallidos

---

Ejemplo:

| ExecutionDate | RecordsLoaded |
|--------------|---------------|
| 2024-01-01 | 25000 |

---

# Buenas prácticas

## Mantener Watermarks

Siempre almacenar:

```text
Último valor procesado.
```

---

## Diseñar procesos idempotentes

Una ejecución repetida no debe generar duplicados.

---

## Utilizar MERGE

Cuando existan actualizaciones.

---

## Registrar auditoría

Toda ejecución debe ser trazable.

---

## Monitorear retrasos

Especialmente datos tardíos.

---

# Error común

Muchos principiantes utilizan:

```text
Full Load
```

para tablas enormes.

---

Resultado:

```text
Altos costos.
Lentitud.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Incremental Load
=
Solo INSERT
```

---

Incorrecto.

También puede involucrar:

- UPDATE
- DELETE
- UPSERT

---

# Pensamiento de Data Engineering

Antes de diseñar una carga incremental pregúntate:

1. ¿Cómo detectaré cambios?
2. ¿Existe una columna timestamp?
3. ¿Necesito CDC?
4. ¿Cómo manejaré actualizaciones?
5. ¿Qué ocurre con datos tardíos?
6. ¿Cómo evitaré duplicados?
7. ¿Cómo almacenaré el watermark?

---

# Relación con los siguientes módulos

```text
DATA LOADING
        ↓
INCREMENTAL LOADS
        ↓
FULL LOADS
        ↓
CHANGE DATA CAPTURE (CDC)
```

---

# Resumen

Incremental Loading es una estrategia que procesa únicamente datos nuevos o modificados.

Métodos comunes:

- Timestamp
- Incremental ID
- Watermarks
- CDC

Beneficios:

- Mayor rendimiento
- Menor costo
- Mejor escalabilidad

Es una de las técnicas más utilizadas en Data Engineering moderno porque permite procesar grandes volúmenes de datos de forma eficiente.
