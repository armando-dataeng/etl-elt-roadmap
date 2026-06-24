# DATA VALIDATION

## Definición

Data Validation es el proceso de verificar que los datos cumplen reglas, restricciones y expectativas definidas por el negocio y la arquitectura de datos.

Su objetivo es detectar errores antes de que los datos sean consumidos por:

- Data Warehouses
- Dashboards
- Reportes
- Modelos de Machine Learning
- Aplicaciones

---

# ¿Por qué existe?

Supongamos una tabla:

| CustomerID | Age |
|------------|-----|
| 100 | 35 |
| 101 | 250 |

---

Problema:

```text
250 años no es un valor válido.
```

---

La validación permite detectar este problema.

---

# Relación con Data Quality

```text
Data Quality
      ↓

Define estándares

      ↓

Data Validation

Verifica cumplimiento
```

---

# Arquitectura

```text
Data Sources
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
```

---

# Tipos de Validación

## Null Validation

Verifica campos obligatorios.

---

Ejemplo:

```sql
SELECT *
FROM Customers
WHERE CustomerID IS NULL;
```

---

Problema detectado:

```text
Identificador faltante.
```

---

# Range Validation

Verifica valores dentro de rangos permitidos.

---

Ejemplo:

```sql
SELECT *
FROM Customers
WHERE Age < 0
   OR Age > 120;
```

---

Problema detectado:

```text
Edad inválida.
```

---

# Uniqueness Validation

Detecta duplicados.

---

Ejemplo:

```sql
SELECT
    CustomerID,
    COUNT(*)
FROM Customers
GROUP BY CustomerID
HAVING COUNT(*) > 1;
```

---

Problema detectado:

```text
CustomerID duplicado.
```

---

# Domain Validation

Verifica valores permitidos.

---

Ejemplo:

```text
Status
```

Valores válidos:

```text
Active
Inactive
Pending
```

---

Consulta:

```sql
SELECT *
FROM Customers
WHERE Status NOT IN
(
'Active',
'Inactive',
'Pending'
);
```

---

Problema detectado:

```text
Valor fuera del dominio permitido.
```

---

# Format Validation

Valida formatos específicos.

---

Ejemplo:

```text
Email
```

---

Valores válidos:

```text
user@email.com
```

---

Valores inválidos:

```text
user-email.com
```

---

Validación conceptual:

```text
Debe contener @
```

---

# Referential Integrity Validation

Valida relaciones entre tablas.

---

Ejemplo:

```sql
SELECT *
FROM Orders o
LEFT JOIN Customers c
ON o.CustomerID = c.CustomerID
WHERE c.CustomerID IS NULL;
```

---

Problema detectado:

```text
Pedido sin cliente asociado.
```

---

# Row Count Validation

Compara cantidad de registros.

---

Origen:

```text
10000 registros
```

---

Destino:

```text
9500 registros
```

---

Problema:

```text
500 registros perdidos.
```

---

# Aggregate Validation

Valida métricas importantes.

---

Ejemplo:

```sql
SELECT SUM(SalesAmount)
FROM Sales;
```

---

Comparar:

```text
Origen
vs
Destino
```

---

# Business Rule Validation

Reglas específicas del negocio.

---

Ejemplo:

```text
Un cliente Premium
debe tener crédito mayor a cero.
```

---

Consulta:

```sql
SELECT *
FROM Customers
WHERE CustomerType = 'Premium'
AND CreditLimit <= 0;
```

---

# Validaciones en ETL

```text
Extract
      ↓

Validate
      ↓

Transform
      ↓

Load
```

---

Beneficio:

```text
Errores detectados antes.
```

---

# Validaciones en ELT

```text
Extract
      ↓

Load
      ↓

Validate
      ↓

Transform
```

---

Muy común con:

- dbt
- Snowflake
- BigQuery

---

# Data Validation con dbt

Ejemplo:

```yaml
tests:
  - not_null
  - unique
```

---

Valida automáticamente:

```text
Campos nulos
Duplicados
```

---

# Caso Real

## Empresa Retail

Tabla:

```text
Orders
```

---

Reglas:

```text
OrderID obligatorio
Monto > 0
Cliente válido
```

---

Validaciones:

```sql
SELECT *
FROM Orders
WHERE Amount <= 0;
```

---

Resultado:

```text
Pedidos inválidos detectados.
```

---

# Estrategias de Manejo

## Reject Records

Descartar registros inválidos.

---

## Quarantine Zone

Enviar registros problemáticos.

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

## Alerting

Notificar errores automáticamente.

---

# Herramientas Comunes

## Open Source

- dbt
- Great Expectations
- Soda

---

## Cloud

- Azure Data Factory
- AWS Glue
- Dataplex

---

# Buenas prácticas

## Automatizar validaciones

Nunca depender de verificaciones manuales.

---

## Validar en múltiples etapas

- Extracción
- Transformación
- Carga

---

## Registrar resultados

Guardar evidencia de ejecución.

---

## Definir reglas claras

Las validaciones deben ser explícitas.

---

## Monitorear tendencias

No solo errores individuales.

---

# Error común

Muchos equipos validan únicamente:

```text
Cantidad de registros.
```

---

Pero ignoran:

```text
Contenido.
```

---

Resultado:

```text
Datos incorrectos
con conteos correctos.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Validar =
Buscar NULL
```

---

Incorrecto.

La validación incluye:

- Rangos
- Dominios
- Duplicados
- Formatos
- Integridad referencial
- Reglas de negocio

---

# Caso de Entrevista

Pregunta:

```text
¿Qué validaciones implementarías
en una tabla de clientes?
```

---

Respuesta:

```text
NOT NULL
UNIQUE
Formatos
Integridad referencial
Reglas de negocio
Conteos
Agregaciones
```

---

# Pensamiento de Data Engineering

Antes de implementar una validación pregúntate:

1. ¿Qué problema intento prevenir?
2. ¿Qué reglas de negocio existen?
3. ¿Qué ocurre si falla la validación?
4. ¿Cómo registraré el error?
5. ¿Cómo alertaré al equipo?
6. ¿La validación escala?
7. ¿Es automática?

---

# Relación con los siguientes módulos

```text
DATA QUALITY
        ↓
DATA VALIDATION
        ↓
ERROR HANDLING
```

---

# Resumen

Data Validation verifica que los datos cumplen reglas definidas.

Validaciones comunes:

- Null Validation
- Range Validation
- Uniqueness Validation
- Domain Validation
- Format Validation
- Referential Integrity Validation
- Aggregate Validation
- Business Rule Validation

Una buena validación evita que datos incorrectos lleguen a sistemas analíticos y de toma de decisiones.
