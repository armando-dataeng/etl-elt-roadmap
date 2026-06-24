# FULL LOADS

## Definición

Full Load es una estrategia de carga donde todos los datos son procesados y cargados nuevamente durante cada ejecución.

No importa si los datos cambiaron o no.

```text
Todos los registros
son recargados.
```

---

# ¿Por qué existen?

Imaginemos una tabla:

```text
Products
```

con:

```text
10,000 registros
```

---

Cada noche:

```text
Se elimina el contenido actual.
```

---

Y se vuelve a cargar:

```text
Los 10,000 registros.
```

---

Esto es una:

```text
Full Load
```

---

# Arquitectura

```text
Source System
        ↓

Full Extraction
        ↓

Transformation
        ↓

Full Load
        ↓

Data Warehouse
```

---

# Flujo Básico

```text
Extraer todos los datos
        ↓

Transformar todos los datos
        ↓

Reemplazar datos destino
```

---

# Ejemplo

Tabla origen:

```text
Products
```

---

Registros:

| ProductID | ProductName |
|------------|-------------|
| 1 | Laptop |
| 2 | Mouse |
| 3 | Keyboard |

---

Proceso:

```text
Eliminar tabla destino
```

---

Después:

```text
Recargar todos los registros.
```

---

# Estrategias de Full Load

## Truncate and Load

La más utilizada.

---

Paso 1

```sql
TRUNCATE TABLE Products;
```

---

Paso 2

```sql
INSERT INTO Products
SELECT *
FROM SourceProducts;
```

---

Resultado:

```text
Tabla reconstruida completamente.
```

---

# Delete and Insert

Similar a Truncate.

---

Paso 1

```sql
DELETE FROM Products;
```

---

Paso 2

```sql
INSERT INTO Products
SELECT *
FROM SourceProducts;
```

---

Diferencia:

```text
DELETE registra transacciones.
TRUNCATE suele ser más rápido.
```

---

# Cuándo utilizar Full Loads

## Tablas pequeñas

Ejemplo:

```text
Catálogos
Dimensiones pequeñas
Configuraciones
```

---

## Datos poco frecuentes

Ejemplo:

```text
Lista de países
Lista de monedas
```

---

## Primera carga

Cuando el Data Warehouse se construye por primera vez.

---

## Reconstrucciones

Cuando:

```text
Existen errores históricos.
```

---

# Caso Real

## DimCountry

| CountryID | CountryName |
|------------|------------|
| 1 | Spain |
| 2 | France |

---

Cantidad:

```text
200 registros.
```

---

Estrategia recomendada:

```text
Full Load
```

---

Porque:

```text
El costo es mínimo.
```

---

# Ventajas

## Simplicidad

Muy fácil de implementar.

---

## Consistencia

Garantiza sincronización completa.

---

## Menor complejidad

No requiere:

```text
CDC
Watermarks
Timestamps
```

---

## Fácil mantenimiento

Menos lógica de negocio.

---

# Desventajas

## Mayor consumo de recursos

Se procesan todos los datos.

---

## Mayor tiempo de ejecución

Especialmente en tablas grandes.

---

## Mayor costo

Más CPU.

Más almacenamiento temporal.

Más procesamiento.

---

## Escalabilidad limitada

Problemas cuando los datos crecen.

---

# Full Load vs Incremental Load

| Característica | Full Load | Incremental Load |
|---------------|-----------|------------------|
| Registros Procesados | Todos | Solo cambios |
| Complejidad | Baja | Alta |
| Rendimiento | Menor | Mayor |
| Escalabilidad | Limitada | Alta |
| Mantenimiento | Simple | Más complejo |
| Costo | Alto | Bajo |

---

# Ejemplo Comparativo

## Tabla

```text
Orders
```

---

Cantidad:

```text
100 millones de registros
```

---

Cambios diarios:

```text
50,000 registros
```

---

## Full Load

Procesa:

```text
100 millones
```

cada día.

---

## Incremental Load

Procesa:

```text
50,000
```

cada día.

---

Resultado:

```text
Incremental es mucho más eficiente.
```

---

# Arquitectura Empresarial

```text
ERP
CRM
API
      ↓

Full Load
      ↓

Data Warehouse
```

---

Común en:

```text
Tablas pequeñas.
```

---

# Escenarios Comunes

## Catálogos

```text
Countries
Currencies
Departments
```

---

## Dimensiones pequeñas

```text
DimCountry
DimCurrency
```

---

## Ambientes de desarrollo

```text
Pruebas
Laboratorios
```

---

# Buenas prácticas

## Utilizar Full Load solo cuando tenga sentido

Evitar en tablas enormes.

---

## Medir tiempos de ejecución

Monitorear crecimiento.

---

## Implementar auditoría

Registrar:

- Fecha
- Hora
- Registros cargados

---

## Automatizar validaciones

Comparar:

```text
Origen
vs
Destino
```

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
Costos elevados.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Incremental siempre es mejor.
```

---

Incorrecto.

Para tablas pequeñas:

```text
Full Load
```

puede ser la solución más simple y eficiente.

---

# Caso de Entrevista

Pregunta:

```text
¿Cuándo elegirías Full Load
en lugar de Incremental Load?
```

---

Respuesta:

```text
Cuando el volumen es pequeño,
los datos cambian poco,
o la simplicidad es más importante
que la optimización.
```

---

# Pensamiento de Data Engineering

Antes de elegir Full Load pregúntate:

1. ¿Cuántos registros existen?
2. ¿Qué tan rápido crecen?
3. ¿Con qué frecuencia cambian?
4. ¿Vale la pena implementar Incremental Load?
5. ¿Cuál es el costo de reprocesar todo?
6. ¿Qué ocurre si la carga falla?
7. ¿La solución escalará en el futuro?

---

# Relación con los siguientes módulos

```text
INCREMENTAL LOADS
        ↓
FULL LOADS
        ↓
CHANGE DATA CAPTURE (CDC)
```

---

# Resumen

Full Load es una estrategia donde todos los datos se cargan nuevamente en cada ejecución.

Características:

- Simple.
- Fácil de implementar.
- Menor complejidad.
- Mayor consumo de recursos.

Es ideal para:

- Tablas pequeñas.
- Catálogos.
- Primeras cargas.
- Reconstrucciones completas.

Comprender cuándo utilizar Full Load es tan importante como saber cuándo utilizar Incremental Load.
