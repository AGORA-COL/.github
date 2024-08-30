# Modelo dinámico y de Agentes

El modelo FRED (Grefenstette et al., 2013) permite explorar cómo una enfermedad se propaga dentro de una población a través del tiempo.

En este caso, se utiliza para simular el proceso de dispersión del virus SARS-CoV-2 en cada departamento de Colombia.

![](images/image.png)

# Flujo de datos

```mermaid
flowchart TB
    subgraph EPS[1. Elaboración Poblaciones sintéticas]
        GPS([Generador poblaciones sintéticas])
        PS[(Poblaciones sintéticas)]
        CPS([Comparación poblaciones sintéticas])
        DC[(Datos censo 2018)]
    end 
    PS --> FE
    subgraph CP[2. Calibración de parámetros]
        EC[Escenarios contrafactuales]
        FAM[Fred Agent Model]
        FE([FRED])
        FP[Parámetros FRED]
        RP([Regresión de parámetros])
        ML[Modelo ML para regresión]
        AM([Actualizar modelo])
        FAM --> FE --> FP --> RP --> ML --> AM --> FAM
        EC --> FE
    end
    R([4. Generación de reportes])

    GPS --> PS --> CPS
    DC --> CPS
    CP --> R
    CPS --> R


    click GPS "https://github.com/AGORA-COL/synthetic_populations"


    class FE,R,RP,GPS,CPS,AM process;
    class PS,DC repository;
    class EC,ML,FAM,FP model;


    classDef model fill:white,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef software fill:orange,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#ddd,stroke:#333,stroke-width:2px,color:#000;

```
# 1. Elaboración Poblaciones sintéticas
- [AGORA-COL/synthetic_populations: Training in synthetic populations by doing the Guido's scripts](https://github.com/AGORA-COL/synthetic_populations)

# 2. Calibración de parámetros
## Regresión de parámetros
## Modelo ML para regresión
Modelo ML para regresión de parámetros FRED calibrados
[AGORA-COL/fred_parameters_regression: This repo contains the ML model for the regression of calibrated FRED parameters](https://github.com/AGORA-COL/fred_parameters_regression)

## Actualizar modelo

# 3. Escenarios contrafactuales

# 4. Reportes
- [AGORA-COL/model-reports](https://github.com/AGORA-COL/model-reports)

# FRED
## FRED Software
- [AGORA-COL/FRED: This is a duplicate of FRED from PHDL repository specific for COVID-19](https://github.com/AGORA-COL/FRED)
## FRED Agent Model
- [AGORA-COL/fred_colombia_implementation: Implemetation of the agent model FRED for the description of the COVID-19 outbreak in Colombia](https://github.com/AGORA-COL/fred_colombia_implementation)

