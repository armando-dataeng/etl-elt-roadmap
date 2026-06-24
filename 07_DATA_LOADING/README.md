# DATA LOADING

## Definición

Data Loading es el proceso de cargar datos transformados en un sistema destino.

Es la última etapa de un proceso ETL.

Flujo:

```text
Extract
    ↓
Transform
    ↓
Load
```

---

# ¿Por qué existe?

Después de extraer y transformar los datos:

```text
Necesitamos almacenarlos
en una plataforma analítica.
```

Por ejemplo:

```text
Data Warehouse
Data Lake
Data Mart
Analytics Platform
```

---

# Objetivos

Una carga de datos debe ser:

- Confiable
- Escalable
- Repetible
- Segura
- Monitoreable

---

# Arquitectura

```text
Data Sources
       ↓

Extraction
       ↓

Transformation
       ↓

Loading
       ↓

Data Warehouse
```

---

# Sistemas Destino

Los datos pueden cargarse en:

## Data Warehouse

Ejemplos:

- Snowflake
- BigQuery
- Redshift
- Synapse

---

## Data Lake

Ejemplos:

- Azure Data Lake
- Amazon S3
- Google Cloud Storage

---

## Data Mart

Subconjuntos especializados para áreas de negocio.

---

## Bases de Datos

- SQL Server
- PostgreSQL
- Oracle
- MySQL

---

# Tipos de Carga

## Full Load

Carga todos los datos.

---

Ejemplo:

```text
Eliminar contenido anterior
y volver a cargar todo.
```

---

## Flujo

```text
Source
   ↓

Delete

   ↓

Insert All
```

---

### Ventajas

- Fácil implementación.
- Datos consistentes.

---

### Desventajas

- Costoso.
- Lento para grandes volúmenes.

---

# Incremental Load

Carga únicamente registros nuevos o modificados.

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE LastModifiedDate >
      LastExecutionDate;
```

---

### Ventajas

- Más rápido.
- Menor consumo de recursos.

---

### Desventajas

- Mayor complejidad.

---

# Append Load

Solo agrega nuevos registros.

---

Ejemplo:

```text
Histórico de ventas.
```

---

## Flujo

```text
Datos Nuevos
      ↓

Append
      ↓

Tabla Destino
```

---

# Upsert

Combina:

```text
INSERT
+
UPDATE
```

---

Si existe:

```text
Actualizar.
```

---

Si no existe:

```text
Insertar.
```

---

## SQL Conceptual

```sql
MERGE INTO Customers
USING StagingCustomers
ON Customers.CustomerID =
   StagingCustomers.CustomerID

WHEN MATCHED THEN
    UPDATE

WHEN NOT MATCHED THEN
    INSERT;
```

---

# Capa Staging

Muy utilizada en Data Engineering.

---

## Definición

Área temporal donde los datos son cargados antes del destino final.

---

Arquitectura:

```text
Source
   ↓

Staging
   ↓

Data Warehouse
```

---

## Beneficios

- Validación.
- Auditoría.
- Recuperación ante errores.

---

# Batch Loading

Procesamiento por lotes.

---

Ejemplo:

```text
Cada noche a las 2 AM.
```

---

Características:

- Menor complejidad.
- Muy utilizado en ETL tradicional.

---

# Real-Time Loading

Carga continua.

---

Ejemplo:

```text
Eventos de streaming.
```

---

Tecnologías:

- Kafka
- Event Hubs
- Kinesis

---

# Caso Real

## Empresa Retail

Datos:

```text
Clientes
Pedidos
Productos
Ventas
```

---

Proceso:

```text
Extract
↓
Transform
↓
Load
```

---

Destino:

```text
Snowflake
```

---

Resultado:

```text
Dashboard actualizado.
```

---

# Estrategias de Carga

## Truncate + Load

```sql
TRUNCATE TABLE Sales;
```

---

Después:

```sql
INSERT INTO Sales
SELECT ...
```

---

Uso:

```text
Full Load
```

---

# Merge Load

Utiliza:

```sql
MERGE
```

---

Uso:

```text
Incremental Load
```

---

# Particionamiento

Muy común en Data Warehouses.

---

Ejemplo:

```text
2024
2025
2026
```

---

Beneficios:

- Mejor rendimiento.
- Menor tiempo de carga.

---

# Desafíos Comunes

## Duplicados

Carga repetida.

---

## Datos Perdidos

Errores en extracción.

---

## Rendimiento

Grandes volúmenes.

---

## Bloqueos

Sistemas compartidos.

---

## Consistencia

Datos incompletos.

---

# Auditoría

Toda carga debe registrar:

- Fecha
- Hora
- Registros procesados
- Registros exitosos
- Registros fallidos

---

Ejemplo:

| ExecutionDate | RecordsLoaded |
|--------------|---------------|
| 2024-01-01 | 50000 |

---

# Buenas prácticas

## Utilizar Staging

Evita problemas en producción.

---

## Implementar auditoría

Toda carga debe ser trazable.

---

## Validar conteos

Comparar:

```text
Fuente
vs
Destino
```

---

## Diseñar procesos idempotentes

La ejecución repetida no debe generar errores.

---

## Utilizar cargas incrementales

Cuando sea posible.

---

# Error común

Muchos principiantes utilizan:

```text
Full Load
```

para todo.

---

Resultado:

```text
Pipelines lentos.
Altos costos.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Load = Insert
```

---

Incorrecto.

La carga puede incluir:

- Insert
- Update
- Merge
- Append
- Replace

---

# Pensamiento de Data Engineering

Antes de diseñar una carga pregúntate:

1. ¿Cuál es el destino?
2. ¿Necesito Full o Incremental?
3. ¿Cómo evitar duplicados?
4. ¿Qué ocurre si falla?
5. ¿Cómo validaré los resultados?
6. ¿Cómo escalará el proceso?
7. ¿Es idempotente?

---

# Relación con los siguientes módulos

```text
DATA EXTRACTION
        ↓
DATA TRANSFORMATION
        ↓
DATA LOADING
        ↓
INCREMENTAL LOADS
        ↓
FULL LOADS
        ↓
CDC
```

---

# Resumen

Data Loading es el proceso de cargar datos hacia un sistema destino.

Tipos principales:

- Full Load
- Incremental Load
- Append Load
- Upsert

Conceptos importantes:

- Staging
- Auditoría
- Particionamiento
- Idempotencia

Una estrategia de carga bien diseñada es fundamental para construir pipelines confiables y escalables.
