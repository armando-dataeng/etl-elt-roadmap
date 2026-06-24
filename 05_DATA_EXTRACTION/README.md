# DATA EXTRACTION

## Definición

Data Extraction es el proceso de obtener datos desde una fuente para ser utilizados en un pipeline de datos.

Es la primera etapa de cualquier proceso ETL o ELT.

Flujo:

```text
Data Source
      ↓
Extract
      ↓
Transform
      ↓
Load
```

---

# ¿Por qué es importante?

Si la extracción falla:

```text
No existen datos para procesar.
```

Por lo tanto:

```text
La calidad de todo el pipeline
depende de una extracción confiable.
```

---

# Objetivos de la extracción

Una extracción debe ser:

- Completa
- Confiable
- Repetible
- Escalable
- Segura

---

# Fuentes de extracción

Los datos pueden extraerse desde:

## Bases de Datos

- SQL Server
- PostgreSQL
- MySQL
- Oracle

---

## APIs

- REST APIs
- GraphQL APIs
- SaaS APIs

---

## Archivos

- CSV
- JSON
- XML
- Excel

---

## Streaming

- Kafka
- Event Hubs
- Kinesis

---

# Extracción desde Bases de Datos

La forma más común.

Ejemplo:

```sql
SELECT *
FROM Customers;
```

---

## Ventajas

- Datos estructurados
- SQL conocido
- Alta confiabilidad

---

## Desventajas

- Impacto sobre sistemas productivos
- Bloqueos
- Grandes volúmenes

---

# Extracción desde APIs

Muy común en sistemas modernos.

---

## Ejemplo

```http
GET /customers
```

---

Respuesta:

```json
{
  "id": 100,
  "name": "Pedro"
}
```

---

## Desafíos

- Límites de consumo (Rate Limits)
- Autenticación
- Paginación
- Cambios de versión

---

# Extracción desde Archivos

Frecuente en integraciones empresariales.

---

Ejemplos:

```text
sales.csv
customers.xlsx
inventory.json
```

---

## Desafíos

- Archivos corruptos
- Formatos inconsistentes
- Codificación incorrecta

---

# Tipos de extracción

## Full Extraction

Extrae todos los registros.

---

Ejemplo:

```sql
SELECT *
FROM Customers;
```

---

Resultado:

```text
Toda la tabla.
```

---

## Ventajas

Simple.

---

## Desventajas

Costosa para tablas grandes.

---

# Incremental Extraction

Extrae únicamente datos nuevos o modificados.

---

Ejemplo:

```sql
SELECT *
FROM Customers
WHERE LastModifiedDate >
      '2024-01-01';
```

---

Resultado:

```text
Solo cambios recientes.
```

---

## Ventajas

Más eficiente.

---

## Desventajas

Mayor complejidad.

---

# Extracción Basada en Fechas

Muy utilizada.

---

Ejemplo:

```sql
SELECT *
FROM Orders
WHERE OrderDate >= CURRENT_DATE - 1;
```

---

Permite:

```text
Cargas diarias.
```

---

# Extracción Basada en Watermarks

Se almacena:

```text
Último registro procesado.
```

---

Ejemplo:

```text
LastProcessedID = 1000
```

---

Consulta:

```sql
SELECT *
FROM Orders
WHERE OrderID > 1000;
```

---

# Extracción mediante CDC

CDC significa:

```text
Change Data Capture
```

---

Permite detectar:

- INSERT
- UPDATE
- DELETE

---

Sin consultar toda la tabla.

---

Ejemplo:

```text
Registro creado
Registro actualizado
Registro eliminado
```

---

# Arquitectura de Extracción

```text
Source System
      ↓

Data Extraction
      ↓

Raw Layer
      ↓

Transformation
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

Proceso:

```text
Extract Customers
Extract Orders
Extract Products
```

---

Resultado:

```text
Raw Data Layer
```

---

# Desafíos Comunes

## Volumen

Millones de registros.

---

## Latencia

Necesidad de datos recientes.

---

## Calidad

Datos incompletos.

---

## Disponibilidad

Sistemas fuente fuera de línea.

---

## Rendimiento

Evitar afectar producción.

---

# Buenas prácticas

## Evitar SELECT *

Incorrecto:

```sql
SELECT *
FROM Customers;
```

---

Correcto:

```sql
SELECT
    CustomerID,
    CustomerName
FROM Customers;
```

---

## Extraer solo lo necesario

Reducir volumen.

---

## Utilizar extracción incremental

Cuando sea posible.

---

## Registrar auditoría

Guardar:

- Fecha
- Hora
- Cantidad de registros

---

## Monitorear errores

Toda extracción debe ser observable.

---

# Seguridad

Nunca ignorar:

- Credenciales
- Secretos
- Tokens
- Accesos

---

Utilizar:

```text
Key Vault
Secret Manager
Credential Store
```

---

# Error común

Muchos principiantes ejecutan:

```sql
SELECT *
FROM TablaGigante;
```

sobre producción.

---

Resultado:

```text
Impacto en rendimiento.
```

---

# Error conceptual frecuente

Muchos creen:

```text
Extraer = Copiar.
```

---

Incorrecto.

Extraer implica:

- Conectividad
- Seguridad
- Rendimiento
- Escalabilidad
- Monitoreo

---

# Pensamiento de Data Engineering

Antes de diseñar una extracción pregúntate:

1. ¿Cuál es la fuente?
2. ¿Qué volumen existe?
3. ¿Necesito Full o Incremental?
4. ¿Cómo detectar cambios?
5. ¿Cómo evitar impacto en producción?
6. ¿Qué ocurre si falla?
7. ¿Cómo monitorearé el proceso?

---

# Relación con los siguientes módulos

```text
DATA SOURCES
        ↓
DATA EXTRACTION
        ↓
DATA TRANSFORMATION
        ↓
DATA_LOADING
```

---

# Resumen

Data Extraction es el proceso de obtener datos desde sistemas origen.

Métodos principales:

- Full Extraction
- Incremental Extraction
- Watermarks
- CDC

Fuentes comunes:

- Bases de datos
- APIs
- Archivos
- Streaming

Una extracción eficiente es la base de cualquier pipeline de datos confiable.
