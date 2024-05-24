# Exploratory Analysis of Property Sales Dataset

## Overview

This project involves an exploratory analysis and cleaning of a dataset containing information on properties for sale provided by the real estate company Properatti. The primary goal was to clean the dataset, addressing null fields and erroneous information to prepare it for further analysis.

## Dataset Details

- **Number of Rows:** 121220
- **Number of Columns:** 26
- **Percentage of Columns with Null Values:** 69%

**Note:** The dataset is not included in this repository due to its large size.

## Data Cleaning Process

### Column Removal

1. **Irrelevant Columns:**
   - Removed a column containing only indices.
   - Removed a column with no data variability.
   - Removed a column with outdated web addresses.

### `place_with_parent_names` Column

- **Structure Analysis:**
  - Detected variability in the number of subdivisions (2 to 5).
- **Data Extraction:**
  - Used regex to create 5 new columns (`new_place_x`).
- **Column Validations:**
  - `new_place_1` and `new_place_2` were redundant with `country_name` and `state_name`.
  - Retained the most relevant subdivision as `Place`.

### Geographic Coordinates

- **Latitude and Longitude:**
  - Split `lat-lon` into `lat_new` and `lon_new`.
  - Verified consistency across coordinate columns.
  - Merged with external `Geonames_id` dataset to fill missing values.
  - Reduced nulls from 43% to less than 7%.

### Price Data

- **Currency Handling:**
  - Standardized prices to USD using `price_aprox_usd`.
  - Removed irrelevant price columns and rows with missing USD prices.

### Surface Area

- **Surface Information:**
  - Validated and retained `price_usd_per_m2` and `surface_total_in_m2`.
  - Filled missing surface data using regex from `title` and `description`.

### Additional Columns

- **Floor:**
  - Eliminated floors above 56 and assigned floor "0" for specific property types.
  - Decided to remove the column due to high percentage of nulls (37%).

- **Rooms:**
  - Removed outliers and used regex to extract room information from `title` and `description`.
  - Reduced nulls to 13.32% and removed remaining null rows.

- **Expenses (expensas):**
  - Attempted to fill using descriptions but removed the column due to high percentage of nulls (60.91%).

### Functions

- **Outlier Removal:**
  - Function to identify and remove outliers from the dataset.
- **Mapping Locations:**
  - Function to plot property locations on a map of Argentina.

## Results

The cleaning process resulted in a significantly more usable dataset with a substantial reduction in missing values, making it ready for further analysis and modeling. Data set final:
- 0 campos nulos
- 75817 filas  (-37.5%) 
- 8 columnas (-14 campos)

## Final Dataset

   -0 null fields
   -75,817 rows (-37.5%)
   -8 columns (-14 fields

## Repository Structure

- `data/`
  - `Geonames_id.csv` : Auxiliary dataset for filling missing geographic data.
- `notebooks/`
  - `TP1 grupo 5.ipynb` : Jupyter notebook used for the cleaning and analysis process.
- `scripts/` : Python scripts used for data manipulation and cleaning.
- `maps/`
  - `provincia.*` : Shapefiles for mapping property locations.
- `presentation/`
  - `Presentación TP1 - DH - Grupo 5.pptx` : PowerPoint presentation detailing the project and findings.
- `README.md` : Overview and details of the project.

# Análisis Exploratorio del Dataset de Ventas de Propiedades

## Descripción General

Este proyecto implica un análisis exploratorio y limpieza de un dataset que contiene información sobre propiedades en venta proporcionado por la inmobiliaria Properatti. El objetivo principal fue limpiar el dataset, abordando los campos nulos y la información errónea para prepararlo para análisis posteriores.

## Detalles del Dataset

- **Número de Filas:** 121220
- **Número de Columnas:** 26
- **Porcentaje de Columnas con Valores Nulos:** 69%

**Nota:** El dataset no está incluido en este repositorio debido a su gran tamaño.

## Proceso de Limpieza de Datos

### Eliminación de Columnas

1. **Columnas Irrelevantes:**
   - Se eliminó una columna que solo contenía índices.
   - Se eliminó una columna sin variabilidad de datos.
   - Se eliminó una columna con direcciones web desactualizadas.

### Columna `place_with_parent_names`

- **Análisis de Estructura:**
  - Se detectó variabilidad en el número de subdivisiones (de 2 a 5).
- **Extracción de Datos:**
  - Se usó regex para crear 5 nuevas columnas (`new_place_x`).
- **Validación de Columnas:**
  - `new_place_1` y `new_place_2` eran redundantes con `country_name` y `state_name`.
  - Se retuvo la subdivisión más relevante como `Place`.

### Coordenadas Geográficas

- **Latitud y Longitud:**
  - Se separó `lat-lon` en `lat_new` y `lon_new`.
  - Se verificó la consistencia entre las columnas de coordenadas.
  - Se realizó un merge con el dataset externo `Geonames_id` para llenar valores faltantes.
  - Se redujeron los nulos del 43% a menos del 7%.

### Datos de Precio

- **Manejo de Monedas:**
  - Se estandarizaron los precios a USD usando `price_aprox_usd`.
  - Se eliminaron columnas de precio irrelevantes y filas con precios USD faltantes.

### Superficie

- **Información de Superficie:**
  - Se validaron y retuvieron `price_usd_per_m2` y `surface_total_in_m2`.
  - Se llenaron los datos faltantes de superficie usando regex en `title` y `description`.

### Columnas Adicionales

- **Piso:**
  - Se eliminaron pisos superiores a 56 y se asignó el piso "0" para ciertos tipos de propiedad.
  - Se decidió eliminar la columna debido a un alto porcentaje de nulos (37%).

- **Habitaciones:**
  - Se eliminaron outliers y se usó regex para extraer información de habitaciones de `title` y `description`.
  - Se redujeron los nulos al 13.32% y se eliminaron las filas restantes con nulos.

- **Expensas:**
  - Se intentó llenar usando descripciones, pero se eliminó la columna debido a un alto porcentaje de nulos (60.91%).

### Funciones

- **Eliminación de Outliers:**
  - Función para identificar y eliminar outliers del dataset.
- **Mapeo de Ubicaciones:**
  - Función para graficar las ubicaciones de las propiedades en un mapa de Argentina.

## Resultados

El proceso de limpieza resultó en un dataset significativamente más utilizable con una reducción sustancial en valores faltantes, preparándolo para análisis y modelado futuros. 

## Dataset final
   -0 campos nulos
   -75817 filas (-37.5%)
   -8 columnas (-14 campos

## Estructura del Repositorio


  - `Geonames_id.csv` : Dataset auxiliar para llenar datos geográficos faltantes.
- `notebooks/`
  - `TP1 grupo 5.ipynb` : Jupyter notebook usado para el proceso de limpieza y análisis.
- `scripts/` : Scripts de Python utilizados para la manipulación y limpieza de datos.
- `maps/`
  - `provincia.*` : Archivos shapefiles para mapear las ubicaciones de las propiedades.
- `presentation/`
  - `Presentación TP1 - DH - Grupo 5.pptx` : Presentación de PowerPoint detallando el proyecto y los hallazgos.
- `README.md` : Descripción general y detalles del proyecto.

