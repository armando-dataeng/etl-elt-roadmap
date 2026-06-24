# ETL FUNDAMENTALS

## Definición

ETL significa:

```text
Extract
Transform
Load
```

Es un proceso utilizado para extraer datos de diferentes fuentes, transformarlos según las necesidades del negocio y cargarlos en un sistema destino.

Generalmente:

```text
Sistemas Fuente
        ↓
    Extract
        ↓
   Transform
        ↓
      Load
        ↓
 Data Warehouse
```

---

# ¿Por qué existe ETL?

Las organizaciones almacenan datos en múltiples sistemas.

Ejemplos:

```text
ERP
CRM
E-commerce
Aplicaciones móviles
APIs
Archivos CSV
Bases de datos
```

Cada sistema contiene información valiosa.

Sin embargo:

```text
Los datos están dispersos.
```

ETL permite consolidarlos en una única plataforma para análisis y toma de decisiones.

---

# Objetivos de ETL

ETL busca:

- Integrar datos.
- Limpiar datos.
- Estandarizar formatos.
- Aplicar reglas de negocio.
- Preparar información para análisis.

---

# Componentes de ETL

## Extract

Proceso de extracción de datos desde sistemas origen.

Fuentes comunes:

```text
SQL Server
PostgreSQL
MySQL
Oracle
CSV
JSON
REST APIs
SAP
Salesforce
```

---

### Ejemplo

```sql
SELECT *
FROM Customers;
```

---

Resultado:

```text
Datos obtenidos desde el sistema origen.
```

---

# Transform

Proceso de limpieza y transformación.

Aquí se aplican reglas de negocio.

---

## Ejemplos

### Convertir formatos

```text
01/01/2024
```

↓

```text
2024-01-01
```

---

### Eliminar duplicados

Antes:

| CustomerID |
|------------|
| 100 |
| 100 |

---

Después:

| CustomerID |
|------------|
| 100 |

---

### Calcular métricas

```text
Precio × Cantidad
```

↓

```text
VentasTotales
```

---

### Estandarizar nombres

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

# Load

Proceso de carga hacia el sistema destino.

Normalmente:

```text
Data Warehouse
Data Lake
Data Mart
```

---

Ejemplo:

```sql
INSERT INTO FactSales
VALUES (...);
```

---

# Flujo Completo

```text
CRM
ERP
API
CSV
      │
      ▼

   EXTRACT
      │
      ▼

  TRANSFORM
      │
      ▼

     LOAD
      │
      ▼

DATA WAREHOUSE
```

---

# Caso Real

## Empresa Retail

Sistemas:

```text
Tienda Física
E-commerce
ERP
```

---

Problema:

Los datos están separados.

---

Solución:

```text
ETL
```

---

Proceso:

```text
Extract
↓
Obtener ventas

Transform
↓
Limpiar y unificar

Load
↓
Cargar al Data Warehouse
```

---

# ETL vs Reportes Directos

## Sin ETL

```text
Power BI
      ↓
ERP
      ↓
CRM
      ↓
E-commerce
```

Problemas:

- Lentitud.
- Datos inconsistentes.
- Consultas complejas.

---

## Con ETL

```text
ERP
CRM
E-commerce
       ↓
      ETL
       ↓
Data Warehouse
       ↓
Power BI
```

Beneficios:

- Mejor rendimiento.
- Datos consistentes.
- Consultas simplificadas.

---

# Características de ETL

## Integración

Combina múltiples fuentes.

---

## Transformación

Aplica reglas de negocio.

---

## Automatización

Puede ejecutarse automáticamente.

---

## Repetibilidad

El mismo proceso puede ejecutarse diariamente.

---

# Tipos de ETL

## Batch ETL

Procesamiento por lotes.

Ejemplo:

```text
Carga nocturna.
```

---

## Near Real-Time ETL

Actualizaciones frecuentes.

Ejemplo:

```text
Cada 5 minutos.
```

---

## Real-Time ETL

Procesamiento continuo.

Ejemplo:

```text
Eventos de streaming.
```

---

# Herramientas ETL

Herramientas comunes:

- SQL Server Integration Services (SSIS)
- Azure Data Factory
- Informatica
- Talend
- Pentaho
- Apache NiFi
- Airflow

---

# Beneficios

## Centralización

Información en un solo lugar.

---

## Calidad de datos

Datos limpios y consistentes.

---

## Mejor análisis

Facilita BI y Analytics.

---

## Automatización

Reduce trabajo manual.

---

# Desventajas

## Complejidad

Los pipelines requieren mantenimiento.

---

## Costos

Infraestructura y monitoreo.

---

## Latencia

Los datos pueden no estar disponibles inmediatamente.

---

# Error común

Muchos principiantes creen:

```text
ETL = Copiar datos
```

---

Incorrecto.

ETL implica:

```text
Extraer
Transformar
Cargar
```

---

La transformación es una parte crítica del proceso.

---

# Error conceptual frecuente

Muchos creen que ETL es únicamente una herramienta.

---

Incorrecto.

ETL es:

```text
Un proceso.
```

Las herramientas simplemente lo implementan.

---

# Pensamiento de Data Engineering

Antes de diseñar un ETL pregúntate:

1. ¿De dónde vienen los datos?
2. ¿Qué calidad tienen?
3. ¿Qué transformaciones son necesarias?
4. ¿Cuál es el sistema destino?
5. ¿Cada cuánto debe ejecutarse?
6. ¿Qué ocurre si falla?
7. ¿Cómo monitorearé el pipeline?

---

# Relación con los siguientes módulos

```text
ETL FUNDAMENTALS
        ↓
ELT FUNDAMENTALS
        ↓
ETL VS ELT
        ↓
DATA SOURCES
        ↓
DATA EXTRACTION
```

---

# Resumen

ETL (Extract, Transform, Load) es un proceso utilizado para integrar datos desde múltiples fuentes hacia una plataforma analítica.

Fases:

```text
Extract
↓
Transform
↓
Load
```

Objetivos:

- Integrar datos.
- Mejorar calidad.
- Automatizar procesos.
- Preparar información para análisis.

ETL es uno de los pilares fundamentales de Data Engineering y Data Warehousing.
