# ELT FUNDAMENTALS

## Definición

ELT significa:

```text
Extract
Load
Transform
```

Es una estrategia de integración de datos donde los datos se cargan primero en el sistema destino y posteriormente se transforman.

Flujo:

```text
Extract
    ↓
Load
    ↓
Transform
```

---

# ¿Qué significa ELT?

En ETL tradicional:

```text
Extract
    ↓
Transform
    ↓
Load
```

Las transformaciones ocurren antes de cargar los datos.

---

En ELT:

```text
Extract
    ↓
Load
    ↓
Transform
```

Los datos llegan primero al Data Warehouse.

Luego se transforman utilizando el poder de cómputo de la plataforma.

---

# ¿Por qué existe ELT?

Los Data Warehouses modernos poseen:

- Gran capacidad de almacenamiento.
- Procesamiento distribuido.
- Escalabilidad automática.
- Motores SQL altamente optimizados.

Por ello ya no es necesario transformar todo antes de cargar.

---

# Evolución

## ETL Tradicional

```text
ERP
CRM
APIs
       ↓

Transformación

       ↓

Data Warehouse
```

---

## ELT Moderno

```text
ERP
CRM
AP
