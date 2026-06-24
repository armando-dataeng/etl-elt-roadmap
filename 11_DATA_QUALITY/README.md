# DATA QUALITY

## Definición

Data Quality es el conjunto de procesos, métricas y controles utilizados para garantizar que los datos sean confiables, completos, consistentes y útiles para el negocio.

En otras palabras:

```text
Datos de calidad
=
Datos en los que podemos confiar.
```

---

# ¿Por qué es importante?

Supongamos un dashboard financiero.

---

Ventas reales:

```text
$1,000,000
```

---

Ventas reportadas:

```text
$800,000
```

---

Problema:

```text
Los datos son incorrectos.
```

---

Consecuencia:

```text
Malas decisiones de negocio.
```

---

# Objetivo

Garantizar que los datos sean:

- Correctos
- Completos
- Consistentes
- Precisos
- Oportunos

---

# Arquitectura

```text
Data Sources
        ↓

Data Extraction
        ↓

Data Quality Checks
        ↓

Transformation
        ↓

Data Warehouse
```

---

# Dimensiones de Calidad

## Completeness

¿Faltan datos?

---

Ejemplo:

| CustomerID | Email |
|------------|--------|
| 100 | NULL |

---

Problema:

```text
Información incompleta.
```

---

# Validación

```sql
SELECT *
FROM Customers
WHERE Email IS NULL;
```

---

# Accuracy

¿Los datos representan la realidad?

---

Ejemplo:

```text
Edad = 250 años
```

---

Problema:

```text
Valor imposible.
```

---

# Validación

```sql
SELECT *
FROM Customers
WHERE Age > 120;
```

---

# Consistency

¿Los datos son coherentes?

---

Ejemplo:

Sistema A:

```text
USA
```

---

Sistema B:

```text
United States
```

---

Problema:

```text
Inconsistencia.
```

---

# Uniqueness

¿Existen duplicados?

---

Ejemplo:

| CustomerID |
|------------|
| 100 |
| 100 |

---

Problema:

```text
Duplicación.
```

---

# Validación

```sql
SELECT
    CustomerID,
    COUNT(*)
FROM Customers
GROUP BY CustomerID
HAVING COUNT(*) > 1;
```

---

# Timeliness

¿Los datos llegan a tiempo?

---

Ejemplo:

```text
Dashboard actualizado ayer.
```

---

Problema:

```text
Información desactualizada.
```

---

# Validity

¿Los datos cumplen reglas definidas?

---

Ejemplo:

```text
Email inválido.
```

---

Problema:

```text
Formato incorrecto.
```

---

# Caso Real

## Empresa Retail

Tabla:

```text
Customers
```

---

Problemas:

```text
Emails vacíos
Duplicados
Países inconsistentes
```

---

Resultado:

```text
Reportes incorrectos.
```

---

# Reglas de Calidad

## Valores Obligatorios

Ejemplo:

```text
CustomerID
```

nunca puede ser NULL.

---

Validación:

```sql
SELECT *
FROM Customers
WHERE CustomerID IS NULL;
```

---

# Rangos Permitidos

Ejemplo:

```text
Edad
```

---

Regla:

```text
0 - 120
```

---

Validación:

```sql
SELECT *
FROM Customers
WHERE Age < 0
   OR Age > 120;
```

---

# Valores Permitidos

Ejemplo:

```text
Status
```

---

Permitidos:

```text
Active
Inactive
Pending
```

---

Validación:

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

# Integridad Referencial

Verificar relaciones.

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

Problema:

```text
Pedido sin cliente.
```

---

# Métricas de Calidad

## Completeness %

```text
Registros completos
÷
Total registros
```

---

## Duplicate Rate

```text
Duplicados
÷
Total registros
```

---

## Error Rate

```text
Errores
÷
Total registros
```

---

# Data Quality en ETL

```text
Extract
      ↓

Quality Checks
      ↓

Transform
      ↓

Load
```

---

Beneficio:

```text
Problemas detectados temprano.
```

---

# Data Quality en ELT

```text
Extract
      ↓

Load
      ↓

Quality Checks
      ↓

Transform
```

---

Muy común con:

- dbt
- Snowflake
- BigQuery

---

# Herramientas

## Open Source

- Great Expectations
- Soda
- dbt Tests

---

## Cloud

- Azure Data Factory
- AWS Glue Data Quality
- Google Cloud Dataplex

---

# Caso de Entrevista

Pregunta:

```text
¿Qué harías si descubres
duplicados en una tabla crítica?
```

---

Respuesta:

```text
Investigar origen,
implementar validaciones,
crear monitoreo
y corregir el pipeline.
```

---

# Buenas prácticas

## Validar temprano

Detectar problemas antes de cargar.

---

## Automatizar validaciones

Evitar procesos manuales.

---

## Medir calidad continuamente

No solo una vez.

---

## Crear alertas

Detectar anomalías rápidamente.

---

## Definir SLAs

Establecer niveles mínimos de calidad.

---

# Error común

Muchos equipos validan:

```text
Cantidad de registros.
```

---

Pero ignoran:

```text
Calidad de contenido.
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
Data Quality
=
Limpiar datos
```

---

Incorrecto.

Data Quality incluye:

- Monitoreo
- Validación
- Métricas
- Auditoría
- Gobierno de datos

---

# Pensamiento de Data Engineering

Antes de mover datos pregúntate:

1. ¿Puedo confiar en esta información?
2. ¿Qué reglas de calidad existen?
3. ¿Cómo detectaré errores?
4. ¿Cómo mediré calidad?
5. ¿Qué ocurre si una validación falla?
6. ¿Quién es responsable de los datos?
7. ¿Cómo alertaré problemas?

---

# Relación con los siguientes módulos

```text
CHANGE DATA CAPTURE (CDC)
        ↓
DATA QUALITY
        ↓
DATA VALIDATION
        ↓
ERROR HANDLING
```

---

# Resumen

Data Quality garantiza que los datos sean confiables para análisis y toma de decisiones.

Dimensiones principales:

- Completeness
- Accuracy
- Consistency
- Uniqueness
- Timeliness
- Validity

Una arquitectura moderna de datos no se mide por la cantidad de datos que almacena.

Se mide por la confianza que genera en esos datos.
