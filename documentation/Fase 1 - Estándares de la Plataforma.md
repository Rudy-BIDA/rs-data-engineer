# Fase 1 - Estándares de la Plataforma Microsoft Fabric

## Objetivo

Definir los estándares iniciales para el proyecto de Data Engineering en Microsoft Fabric, siguiendo prácticas utilizadas en entornos empresariales.

La meta es construir una plataforma analítica completa utilizando:

- Microsoft Fabric
- OneLake
- Lakehouse
- Data Pipelines
- Notebooks
- Data Warehouse
- Power BI

Aplicando separación de ambientes:

```text
DEV → TEST → PROD
```

---

# Ambientes

## Workspaces

### Desarrollo

```text
Retail-DEV
```

Propósito:

- Desarrollo de pipelines
- Desarrollo de notebooks
- Pruebas de transformaciones
- Diseño de modelos de datos

---

### Testing

```text
Retail-TEST
```

Propósito:

- Validación funcional
- Validación técnica
- Validación de calidad de datos
- Pruebas previas a despliegue

---

### Producción

```text
Retail-PROD
```

Propósito:

- Consumo de datos certificados
- Dashboards productivos
- Modelos semánticos aprobados
- Cargas programadas

---

# Convención de nombres

## Lakehouse

```text
LH_Retail
```

Prefijo:

```text
LH = Lakehouse
```

---

## Warehouse

```text
WH_Retail
```

Prefijo:

```text
WH = Warehouse
```

---

## Pipelines

```text
PL_Ingestion_Retail
PL_Bronze_Silver
PL_Silver_Gold
```

Prefijo:

```text
PL = Pipeline
```

---

## Notebooks

```text
NB_Load_Bronze
NB_Bronze_Silver
NB_Silver_Gold
```

Prefijo:

```text
NB = Notebook
```

---

## Semantic Models

```text
SM_RetailSales
```

Prefijo:

```text
SM = Semantic Model
```

---

## Reportes

```text
RPT_ExecutiveSales
RPT_Inventory
RPT_CustomerAnalytics
```

Prefijo:

```text
RPT = Report
```

---

# Arquitectura Medallion

Toda la plataforma seguirá el patrón:

```text
Bronze
   ↓
Silver
   ↓
Gold
```

---

## Bronze Layer

Datos crudos provenientes de sistemas fuente.

Características:

- Sin transformaciones significativas
- Conservación del dato original
- Primera zona de aterrizaje

Ejemplos:

```text
brz_sales
brz_customers
brz_products
brz_stores
```

---

## Silver Layer

Datos limpios y estandarizados.

Características:

- Tipos de datos corregidos
- Duplicados eliminados
- Validaciones aplicadas

Ejemplos:

```text
slv_sales
slv_customers
slv_products
slv_stores
```

---

## Gold Layer

Datos listos para consumo de negocio.

Características:

- Agregaciones
- KPIs
- Métricas certificadas

Ejemplos:

```text
gld_sales_summary
gld_customer_metrics
gld_product_performance
```

---

# Caso de Negocio

## Empresa

```text
Contoso Retail Perú
```

Industria:

```text
Retail
```

Productos:

```text
Laptops
Monitores
Mouse
Teclados
Accesorios
```

---

# Entidades Iniciales

El modelo de datos estará compuesto inicialmente por:

```text
Customers
Products
Stores
Sales
```

---

# Artefacto Inicial

La construcción de la plataforma comenzará con:

```text
LH_Retail
```

No se crearán inicialmente:

- Warehouse
- Pipelines
- Notebooks

El primer objetivo es disponer de un Lakehouse correctamente estructurado.

---

# Estructura Inicial del Lakehouse

## Files

```text
Files
│
└── raw
    │
    ├── customers
    ├── products
    ├── stores
    └── sales
```

---

## Estructura futura

```text
Files
│
├── raw
├── staging
└── archive
```

---

# Estructura Objetivo del Proyecto

```text
LH_Retail

Files
│
└── raw
    ├── customers
    ├── products
    ├── sales
    └── stores

Tables
│
├── brz_customers
├── brz_products
├── brz_sales
├── brz_stores
│
├── slv_customers
├── slv_products
├── slv_sales
├── slv_stores
│
├── gld_sales_summary
├── gld_customer_metrics
└── gld_product_performance
```

---

# Principios de Gobierno

## Desarrollo

Todo nuevo artefacto será creado inicialmente en:

```text
Retail-DEV
```

---

## Validación

Todo artefacto aprobado será promovido a:

```text
Retail-TEST
```

---

## Producción

Solo artefactos validados podrán desplegarse en:

```text
Retail-PROD
```

---

# Configuración Base de los Workspaces

Capacidad:

```text
Microsoft Fabric Trial Capacity
```

Formato de almacenamiento:

```text
Large Semantic Model Storage Format
```

Template Apps:

```text
Deshabilitado
```

---

# Objetivo de Aprendizaje

Al finalizar el proyecto se deberá ser capaz de explicar y demostrar:

- Arquitectura Medallion
- OneLake
- Lakehouse
- Data Pipelines
- PySpark Notebooks
- Delta Tables
- Data Warehouse
- Semantic Models
- Power BI
- Promoción DEV → TEST → PROD

utilizando una plataforma analítica completa implementada en Microsoft Fabric.
`