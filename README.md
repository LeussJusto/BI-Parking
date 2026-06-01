#  Proyecto BI – Sistema de Análisis de Flujo Vehicular (Parking)

---

# 1. FUENTE DE DATOS (SISTEMA TRANSACCIONAL)

El punto de partida es una base de datos operativa en SQL Server que contiene información diaria del sistema de estacionamiento.

## Tablas principales:
- TB_FLUJO_VEHICULAR
- TB_CLIENTE
- TB_DOCUMENTO_PLACA
- TB_VEHICULO
- TB_UBIGEO

## ¿Qué representa?
Es la información cruda generada por la operación del negocio:
- registros de ingreso y salida de vehículos
- datos de clientes
- información de vehículos
- ubicación geográfica

---

# 2. ODS (Operational Data Store)

## ¿Qué es?

El ODS es una capa intermedia donde los datos se limpian, transforman y estandarizan antes de ser analizados.

## ¿Qué se hace aquí?

- Limpieza de datos (nulos, duplicados, formatos)
- Normalización de fechas y horas
- Homologación de campos
- Construcción de tablas intermedias de procesamiento
- Preparación de variables operativas

## ¿Para qué sirve?

Permite tener datos confiables y consistentes antes de construir el modelo analítico.

---

# 3. DATA WAREHOUSE (DW / BDS_PARKING)

## ¿Qué es?

El Data Warehouse es la base analítica central donde los datos ya están estructurados para análisis de negocio.

## Diferencia con ODS:

| ODS | DW |
|-----|----|
| Datos limpios y temporales | Datos estructurados y permanentes |
| Enfocado en preparación | Enfocado en análisis |
| Nivel técnico-operativo | Nivel analítico y de negocio |

---

## MODELO UTILIZADO: ESQUEMA ESTRELLA

---

# TABLA HECHOS (FACT_FLUJO_VEHICULAR)

## ¿Qué es?

Es la tabla central del modelo donde se registran los eventos del negocio.

## ¿Qué representa?

Cada fila representa una visita o transacción de un vehículo dentro del sistema de parking.

## ¿Para qué sirve?

Permite medir:
- actividad del negocio
- flujo de vehículos
- ingresos
- permanencia
- comportamiento operativo

---

# TABLAS DIMENSIÓN

Las dimensiones describen la tabla de hechos y permiten segmentar la información.

---

## DIM_FECHA
Permite análisis temporal (año, mes, día, semana).

---

## DIM_CLIENTE
Permite segmentación de clientes (edad, sexo, ingreso, ubicación).

---

## DIM_VEHICULO
Describe características del vehículo (marca, modelo, tipo, año).

---

## DIM_UBIGEO
Permite análisis geográfico (departamento, provincia, distrito).

---

## DIM_PUERTA
Representa los puntos de ingreso/salida del sistema.

---

## DIM_TIPO_CLIENTE
Clasifica el tipo de cliente del sistema.

---

## DIM_TRAMO_HORARIO
Agrupa las horas del día en segmentos (mañana, tarde, noche).

---

# OBJETIVO DEL DATA WAREHOUSE

Transformar datos operativos en un modelo estructurado que permita análisis de negocio, segmentación y toma de decisiones.

---

# 4. POWER BI (CAPA DE VISUALIZACIÓN)

Power BI se utiliza como herramienta de análisis y visualización conectada directamente al Data Warehouse.

---

# NIVELES DE DASHBOARD IMPLEMENTADOS

---

## 🔵 DASHBOARD OPERATIVO

Enfocado en el monitoreo del comportamiento diario del sistema:
- flujo de vehículos
- actividad del sistema
- control de operación
- indicadores básicos del negocio

---

## 🟡 DASHBOARD TÁCTICO

Enfocado en el análisis y optimización del negocio:
- comportamiento de clientes
- análisis por segmentos
- rendimiento por tipo de vehículo
- análisis geográfico
- eficiencia operativa

---

## 🔴 DASHBOARD ESTRATÉGICO

Enfocado en la toma de decisiones de largo plazo:
- análisis de crecimiento del negocio
- rentabilidad general
- segmentación de clientes de alto valor
- tendencias temporales
- análisis de mercados más importantes

---

# FLUJO GENERAL DEL SISTEMA

FUENTE DE DATOS → ODS → DATA WAREHOUSE → POWER BI → TOMA DE DECISIONES

---

# CONCLUSIÓN

El sistema implementado permite transformar datos transaccionales en información estructurada y analítica, facilitando la generación de insights para distintos niveles de decisión dentro de la organización:
- operativo
- táctico
- estratégico
