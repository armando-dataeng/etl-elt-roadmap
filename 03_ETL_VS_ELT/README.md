# ETL VS ELT

## Introducción

ETL y ELT son dos estrategias utilizadas para mover e integrar datos.

Ambas persiguen el mismo objetivo:

```text
Convertir datos dispersos
en información útil.
```

La diferencia principal es:

```text
¿Cuándo ocurre la transformación?
```

---

# ETL

ETL significa:

```text
Extract
Transform
Load
```

Proceso:

```text
Extract
    ↓
Transform
    ↓
Load
```

---

## Flujo

```text
ERP
CRM
CSV
API
     ↓

Transformación

     ↓

Data Warehouse
```

---

## Características

- Transforma antes de cargar.
- Reduce volumen de datos.
- Requiere infraestructura de procesamiento.
- Muy utilizado en arquitecturas tradicionales.

---

# ELT

ELT significa:

```text
Extract
Load
Transform
```

Proceso:

```text
Extract
    ↓
Load
    ↓
Transform
```

---

## Flujo

```text
ERP
CRM
CSV
API
     ↓

Data Warehouse

     ↓

Transformación
```

---

## Características

- Carga primero.
- Transforma después.
- Aprovecha el poder del Data Warehouse.
- Muy utilizado en arquitecturas modernas.

---

# Comparación Visual

## ETL

```text
Datos Fuente
      ↓

Transformación

      ↓

Data Warehouse
```

---

## ELT

```text
Datos Fuente
      ↓

Data Warehouse
      ↓

Transformación
```

---

# Caso Real

## Empresa Retail

Sistemas:

```text
ERP
E-commerce
CRM
```

---

Pregunta:

```text
¿Dónde se realizan
las transformaciones?
```

---

## ETL

```text
Servidor ETL
```

Transforma antes de cargar.

---

## ELT

```text
Snowflake
BigQuery
Databricks
```

Transforma después de cargar.

---

# Ventajas de ETL

## Menor carga en el destino

El Data Warehouse recibe datos procesados.

---

## Mayor control

Transformaciones definidas antes de cargar.

---

## Adecuado para sistemas legacy

Arquitecturas tradicionales.

---

# Desventajas de ETL

## Mayor complejidad

Necesita infraestructura adicional.

---

## Escalabilidad limitada

El servidor ETL puede convertirse en cuello de botella.

---

## Menor flexibilidad

Si cambian los requisitos:

```text
Reprocesar puede ser costoso.
```

---

# Ventajas de ELT

## Escalabilidad

Aprovecha el procesamiento distribuido.

---

## Flexibilidad

Los datos crudos permanecen disponibles.

---

## Simplicidad

Menos infraestructura externa.

---

## Ideal para cloud

Diseñado para plataformas modernas.

---

# Desventajas de ELT

## Mayor almacenamiento

Se conservan datos sin transformar.

---

## Dependencia del Data Warehouse

Las transformaciones ocurren allí.

---

## Costos de cómputo

Las transformaciones consumen recursos del DW.

---

# Herramientas ETL

Ejemplos:

- SSIS
- Informatica
- Talend
- Pentaho

---

# Herramientas ELT

Ejemplos:

- dbt
- Snowflake
- BigQuery
- Databricks
- Azure Synapse

---

# ETL vs ELT

| Característica | ETL | ELT |
|---------------|-----|-----|
| Transformación | Antes de cargar | Después de cargar |
| Escalabilidad | Menor | Mayor |
| Flexibilidad | Menor | Mayor |
| Infraestructura | Externa | Dentro del DW |
| Cloud | Menos común | Muy común |
| Datos Crudos | No siempre | Sí |
| Reprocesamiento | Más difícil | Más sencillo |

---

# Arquitectura Tradicional

```text
Sistemas Fuente
       ↓

Servidor ETL

       ↓

Data Warehouse
```

---

# Arquitectura Moderna

```text
Sistemas Fuente
       ↓

Data Lake
       ↓

Data Warehouse
       ↓

dbt
```

---

# ¿Cuál es mejor?

La respuesta correcta es:

```text
Depende.
```

---

## Utiliza ETL cuando:

- Existen sistemas legacy.
- El Data Warehouse tiene recursos limitados.
- Las transformaciones deben ocurrir antes de almacenar.

---

## Utiliza ELT cuando:

- Trabajas en cloud.
- Utilizas Snowflake o BigQuery.
- Necesitas máxima flexibilidad.
- Deseas conservar datos originales.

---

# Caso de Entrevista

Pregunta:

```text
¿Por qué ELT se volvió tan popular?
```

Respuesta:

```text
Porque los Data Warehouses modernos
poseen suficiente capacidad de almacenamiento
y procesamiento para ejecutar transformaciones
directamente sobre los datos cargados.
```

---

# Error común

Muchos principiantes creen:

```text
ELT reemplazó ETL.
```

---

Incorrecto.

Ambos siguen utilizándose.

---

La elección depende de:

- Arquitectura.
- Costos.
- Herramientas.
- Requisitos del negocio.

---

# Error conceptual frecuente

Muchos creen:

```text
ETL y ELT son herramientas.
```

---

Incorrecto.

Son:

```text
Patrones de integración de datos.
```

---

Las herramientas implementan esos patrones.

---

# Pensamiento de Data Engineering

Antes de elegir ETL o ELT pregúntate:

1. ¿Dónde ejecutaré las transformaciones?
2. ¿Qué plataforma utilizaré?
3. ¿Necesito conservar datos crudos?
4. ¿Cuál es mi volumen de datos?
5. ¿Cómo escalará la solución?

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

ETL y ELT son dos enfoques para integrar datos.

ETL:

```text
Extract
↓
Transform
↓
Load
```

ELT:

```text
Extract
↓
Load
↓
Transform
```

ETL domina arquitecturas tradicionales.

ELT domina arquitecturas modernas basadas en cloud.

Comprender ambos enfoques es fundamental para cualquier Data Engineer.
