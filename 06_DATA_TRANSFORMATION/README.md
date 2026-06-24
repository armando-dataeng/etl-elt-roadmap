# DATA TRANSFORMATION

## Definición

Data Transformation es el proceso de convertir datos extraídos en un formato limpio, consistente y útil para análisis, reporting y toma de decisiones.

Es la segunda etapa de un proceso ETL.

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

Los datos provenientes de sistemas fuente suelen contener:

- Valores nulos
- Duplicados
- Formatos inconsistentes
- Errores humanos
- Datos incompletos
- Estructuras incompatibles

---

Ejemplo:

## Sistema A

```text
USA
```

---

## Sistema B

```text
United States
```

---

## Sistema C

```text
US
```

---

Problema:

```text
Tres valores representan
el mismo país.
```

---

La transformación permite:

```text
Estandarizar datos.
```

---

# Objetivos

La transformación busca:

- Limpiar datos.
- Estandarizar formatos.
- Aplicar reglas de negocio.
- Mejorar calidad.
- Preparar información para análisis.

---

# Arquitectura

```text
Data Sources
       ↓

Data Extraction
       ↓

Data Transformation
       ↓

Data Loading
       ↓

Data Warehouse
```

---

# Tipos de Transformaciones

## Limpieza de Datos

Elimina errores y problemas de calidad.

---

### Ejemplo

Antes:

| CustomerID | Name |
|------------|------|
| 100 | Pedro |
| 100 | Pedro |

---

Después:

| CustomerID | Name |
|------------|------|
| 100 | Pedro |

---

Resultado:

```text
Duplicados eliminados.
```

---

# Manejo de Valores Nulos

Antes:

| CustomerID | Email |
|------------|--------|
| 100 | NULL |

---

Transformación:

```sql
SELECT
    CustomerID,
    COALESCE(Email,'unknown@email.com')
FROM Customers;
```

---

Resultado:

```text
Valores nulos gestionados.
```

---

# Conversión de Tipos

Antes:

```text
'2024-01-01'
```

como texto.

---

Después:

```sql
CAST(OrderDate AS DATE)
```

---

Resultado:

```text
Tipo DATE válido.
```

---

# Estandarización

Antes:

```text
usa
USA
United States
```

---

Después:

```text
United States
```

---

Beneficio:

```text
Consistencia.
```

---

# Reglas de Negocio

Transformaciones específicas de la empresa.

---

Ejemplo:

```text
Precio × Cantidad
```

↓

```text
VentasTotales
```

---

SQL:

```sql
SELECT
    Price * Quantity AS TotalSales
FROM Sales;
```

---

# Enriquecimiento de Datos

Agregar información adicional.

---

Ejemplo:

## Antes

| CustomerID |
|------------|
| 100 |

---

## Después

| CustomerID | Segment |
|------------|----------|
| 100 | Gold |

---

Resultado:

```text
Más contexto para análisis.
```

---

# Filtrado

Eliminar registros no necesarios.

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE Status = 'Completed';
```

---

Resultado:

```text
Solo pedidos válidos.
```

---

# Agregación

Resumir información.

---

Ejemplo:

```sql
SELECT
    ProductID,
    SUM(SalesAmount)
FROM Sales
GROUP BY ProductID;
```

---

Resultado:

```text
Ventas por producto.
```

---

# División de Columnas

Antes:

```text
Pedro López
```

---

Después:

```text
Nombre = Pedro
Apellido = López
```

---

# Unión de Datos

Combinar múltiples fuentes.

---

Ejemplo:

```sql
SELECT *
FROM Customers c
INNER JOIN Orders o
ON c.CustomerID = o.CustomerID;
```

---

Resultado:

```text
Información integrada.
```

---

# Caso Real

## Empresa Retail

Fuentes:

```text
ERP
CRM
E-commerce
```

---

Problemas:

```text
Clientes duplicados
Países inconsistentes
Fechas incorrectas
```

---

Transformaciones:

```text
Deduplicación
Estandarización
Validación
Enriquecimiento
```

---

Resultado:

```text
Datos listos para análisis.
```

---

# Transformaciones en ETL

```text
Extract
      ↓

Transformación Externa

      ↓

Load
```

---

Herramientas comunes:

- SSIS
- Informatica
- Talend

---

# Transformaciones en ELT

```text
Extract
      ↓

Load
      ↓

Transformación dentro del DW
```

---

Herramientas comunes:

- dbt
- Snowflake
- BigQuery
- Databricks

---

# Data Quality

Toda transformación debe mejorar:

## Completitud

```text
¿Faltan datos?
```

---

## Consistencia

```text
¿Los formatos son iguales?
```

---

## Exactitud

```text
¿Los datos son correctos?
```

---

## Unicidad

```text
¿Existen duplicados?
```

---

# Buenas prácticas

## Mantener datos originales

Nunca perder el dato fuente.

---

## Documentar reglas

Toda transformación debe ser trazable.

---

## Automatizar procesos

Evitar cambios manuales.

---

## Validar resultados

Verificar antes de cargar.

---

## Diseñar transformaciones reutilizables

Facilita mantenimiento.

---

# Error común

Transformar demasiadas veces.

---

Resultado:

```text
Pipelines complejos.
Difíciles de mantener.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Transformar = Limpiar
```

---

Incorrecto.

Transformar también implica:

- Integrar
- Agregar
- Enriquecer
- Aplicar reglas de negocio

---

# Pensamiento de Data Engineering

Antes de transformar datos pregúntate:

1. ¿Qué problema intento resolver?
2. ¿Qué reglas de negocio existen?
3. ¿Cómo mejoraré la calidad?
4. ¿Necesito conservar el dato original?
5. ¿Cómo validaré el resultado?
6. ¿La transformación escala?
7. ¿Está documentada?

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
```

---

# Resumen

Data Transformation convierte datos crudos en información útil.

Transformaciones comunes:

- Limpieza
- Estandarización
- Conversión de tipos
- Manejo de nulos
- Deduplicación
- Agregación
- Enriquecimiento
- Integración

Su objetivo es mejorar la calidad de los datos y prepararlos para análisis y toma de decisiones.

La transformación es una de las etapas más importantes dentro de cualquier pipeline de datos.
