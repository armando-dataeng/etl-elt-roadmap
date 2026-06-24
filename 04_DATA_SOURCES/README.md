# DATA SOURCES

## Definición

Una Data Source (Fuente de Datos) es cualquier sistema, aplicación o repositorio que genera o almacena información utilizada por una organización.

Los Data Engineers extraen datos desde estas fuentes para construir:

- Data Warehouses
- Data Lakes
- Dashboards
- Reportes
- Modelos Analíticos

---

# ¿Por qué son importantes?

Antes de diseñar un pipeline debemos entender:

```text
¿De dónde vienen los datos?
```

La calidad del pipeline depende directamente de la calidad de las fuentes.

---

# Arquitectura General

```text
Data Sources
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

# Tipos de Data Sources

Las fuentes de datos pueden clasificarse en varias categorías.

---

# Bases de Datos Relacionales

Son las fuentes más comunes.

Ejemplos:

- SQL Server
- PostgreSQL
- MySQL
- Oracle
- MariaDB

---

## Ejemplo

Tabla:

```text
Customers
```

Consulta:

```sql
SELECT *
FROM Customers;
```

---

Características:

- Datos estructurados.
- SQL.
- Alta consistencia.
- Muy comunes en sistemas OLTP.

---

# Bases de Datos NoSQL

Diseñadas para datos no estructurados o semi-estructurados.

Ejemplos:

- MongoDB
- Cassandra
- DynamoDB
- Couchbase

---

## Documento JSON

```json
{
  "customer_id": 100,
  "name": "Pedro"
}
```

---

Características:

- Flexibilidad.
- Escalabilidad horizontal.
- Datos semi-estructurados.

---

# APIs

Muy utilizadas en arquitecturas modernas.

---

## Ejemplos

- Salesforce API
- Stripe API
- GitHub API
- REST APIs
- GraphQL APIs

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

Características:

- Acceso en tiempo real.
- Integración sencilla.
- Muy utilizadas en SaaS.

---

# Archivos

Una de las fuentes más utilizadas en ETL.

---

## CSV

```csv
CustomerID,Name
100,Pedro
101,Ana
```

---

## Excel

```text
sales.xlsx
```

---

## JSON

```json
{
  "sales": 1000
}
```

---

## XML

```xml
<Customer>
  <Name>Pedro</Name>
</Customer>
```

---

Características:

- Simples.
- Portables.
- Muy comunes en integraciones empresariales.

---

# Sistemas SaaS

Aplicaciones en la nube utilizadas por empresas.

---

## Ejemplos

- Salesforce
- HubSpot
- Workday
- Zendesk
- ServiceNow

---

Características:

- Generalmente exponen APIs.
- Datos de negocio críticos.

---

# ERP Systems

Enterprise Resource Planning.

---

## Ejemplos

- SAP
- Oracle ERP
- Microsoft Dynamics

---

Información típica:

```text
Clientes
Ventas
Inventario
Finanzas
```

---

# CRM Systems

Customer Relationship Management.

---

## Ejemplos

- Salesforce
- HubSpot
- Zoho CRM

---

Información típica:

```text
Leads
Clientes
Oportunidades
Ventas
```

---

# Streaming Sources

Generan datos continuamente.

---

## Ejemplos

- Apache Kafka
- Event Hubs
- Kinesis

---

Flujo:

```text
Evento
↓
Evento
↓
Evento
↓
Evento
```

---

Características:

- Tiempo real.
- Alta velocidad.
- Grandes volúmenes.

---

# IoT Devices

Internet of Things.

---

Ejemplos:

- Sensores
- GPS
- Cámaras
- Dispositivos médicos

---

Datos generados:

```text
Temperatura
Ubicación
Presión
Humedad
```

---

# Data Lakes

En algunos escenarios:

```text
Un Data Lake
```

también puede convertirse en fuente de datos.

---

Ejemplos:

- Azure Data Lake
- Amazon S3
- Google Cloud Storage

---

# Estructurados vs Semi-estructurados vs No estructurados

## Estructurados

Ejemplo:

```text
SQL Server
PostgreSQL
MySQL
```

---

## Semi-estructurados

Ejemplo:

```text
JSON
XML
APIs
```

---

## No estructurados

Ejemplo:

```text
Imágenes
Videos
Audio
PDFs
```

---

# Caso Real

## Empresa Retail

Fuentes:

```text
ERP
CRM
E-commerce
CSV
API de Pagos
```

---

Pipeline:

```text
ERP
CRM
API
CSV
      ↓

Extract
      ↓

Data Warehouse
```

---

# Desafíos Comunes

## Datos incompletos

Campos vacíos.

---

## Formatos diferentes

```text
MM/DD/YYYY

vs

DD/MM/YYYY
```

---

## Duplicados

Registros repetidos.

---

## Calidad inconsistente

Errores humanos.

---

# Buenas prácticas

## Documentar las fuentes

Siempre conocer:

- Origen.
- Frecuencia.
- Propietario.

---

## Validar calidad

Nunca asumir que los datos son correctos.

---

## Automatizar extracción

Evitar procesos manuales.

---

## Monitorear cambios

Las fuentes evolucionan constantemente.

---

# Error común

Muchos principiantes creen:

```text
Todos los datos provienen de SQL.
```

---

Incorrecto.

Un Data Engineer trabaja con:

- APIs
- Archivos
- Streaming
- SaaS
- Bases de datos

---

# Error conceptual frecuente

Muchos creen:

```text
Data Source = Database
```

---

Incorrecto.

Una base de datos es solo un tipo de fuente.

---

# Pensamiento de Data Engineering

Antes de conectar una fuente pregúntate:

1. ¿Qué sistema genera los datos?
2. ¿Cuál es su frecuencia de actualización?
3. ¿Qué formato utiliza?
4. ¿Qué volumen genera?
5. ¿Cómo accederé a los datos?
6. ¿Qué problemas de calidad existen?
7. ¿Qué ocurre si la fuente cambia?

---

# Relación con los siguientes módulos

```text
DATA SOURCES
        ↓
DATA EXTRACTION
        ↓
DATA TRANSFORMATION
        ↓
DATA LOADING
```

---

# Resumen

Las Data Sources son el punto de partida de cualquier pipeline.

Tipos principales:

- Bases de datos relacionales
- Bases de datos NoSQL
- APIs
- Archivos
- SaaS
- ERP
- CRM
- Streaming
- IoT

Comprender las fuentes de datos es fundamental para diseñar pipelines escalables y confiables.
