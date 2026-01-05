# 📊 Monitoreo y Seguimiento: Proyecto de Educación en Emergencias

Este repositorio contiene el flujo de trabajo completo para el procesamiento, limpieza y análisis de datos de un programa de respuesta humanitaria simulado en Colombia. El proyecto se enfoca en la gestión de información de campo en departamentos críticos como Santander, Norte de Santander, Arauca, Nariño y Putumayo.

## 🎯 Objetivo
Transformar datos crudos (unificados de diversas fuentes de campo) en información estructurada y confiable para alimentar tableros de control (Dashboards) que orienten la toma de decisiones estratégicas en contextos de vulnerabilidad.

## 🛠️ Flujo de Trabajo (Pipeline)

### 1. Auditoría y Exploración de Datos (EDA)
Se realizó una auditoría técnica mediante **R** para identificar fallas en la calidad de la información. Hallazgos principales:
* **Integridad:** Se detectaron y eliminaron 50 registros duplicados exactos.
* **Consistencia Geográfica:** Inconsistencias en nombres de municipios (ej: "cucuta" vs "Cúcuta").
* **Validez de Edad:** Datos atípicos con valores negativos y registros superiores a 100 años.
* **Tipado Erróneo:** La columna `Fecha_Intervencion` se identificó como clase `character`, impidiendo análisis temporales.
* **Vacíos (NAs):** Datos faltantes en la variable de costos y municipios.

### 2. Limpieza y Transformación (R - Tidyverse)
Como Economista, apliqué criterios de **gestión de proyectos** para la limpieza:
* **Estandarización:** Uso de `stringr` y `case_when` para unificar categorías de género y municipios (incluyendo el manejo de errores de exportación como valores "Na").
* **Imputación Financiera:** Para no subestimar la ejecución presupuestal, los costos faltantes se imputaron basándose en la **media por tipo de actividad** (`Costo_Media`), asegurando coherencia técnica.
* **Feature Engineering:** * Conversión de fechas a objeto `Date`.
  * Creación de la variable **Grupo Etario** (Ciclo Vital) para permitir un análisis con enfoque diferencial (Primera infancia, infancia, adolescencia, etc.).

### 3. Visualización y Reporte
Los datos limpios (`df_final`) han sido estructurados para conectarse a **Looker Studio**, permitiendo visualizar:
* Cobertura territorial y densidad de beneficiarios.
* Análisis de satisfacción de la población atendida.
* Distribución de inversión por tipo de actividad y población.

## 📂 Estructura del Proyecto
* `scripts/`: Script de R con la lógica de limpieza y auditoría.
* `data/`: Contiene el dataset original (`data_simulada_educacion.csv`) y el producto final limpio.
* `visualizaciones/`: Capturas de pantalla del Dashboard interactivo.

## 🚀 Herramientas Utilizadas
* **Lenguaje:** R (Dplyr, Tidyverse, Lubridate).
* **BI:** Looker Studio / Power BI.
* **Document
