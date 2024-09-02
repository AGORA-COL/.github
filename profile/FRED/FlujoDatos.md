# Modelo dinámico y de Agentes

El modelo FRED (Grefenstette et al., 2013) permite explorar cómo una enfermedad se propaga dentro de una población a través del tiempo.

En este caso, se utiliza para simular el proceso de dispersión del virus SARS-CoV-2 en cada departamento de Colombia.

![](../images/image.png)

# Flujo de datos

```mermaid
flowchart TB
    subgraph EPS[1. Elaboración Poblaciones sintéticas]
        GPS([Generador poblaciones sintéticas])
        PS[(Poblaciones sintéticas)]
        CPS([Comparación poblaciones sintéticas])
        DC[(Datos censo 2018)]
    end 
    PS --> F
    subgraph CP[2. Calibración de parámetros]
        EC[Escenarios contrafactuales]
        FAM[Fred Agent Model]
        F([FRED])
        FP[Parámetros FRED]
        RP([Regresión de parámetros])
        ML[Modelo ML para regresión]
        AM([Actualizar modelo])
        EC --> F --> FP --> RP --> ML --> AM --> FAM --> F
    end
    R([Generación de reportes])

    GPS --> PS --> CPS
    DC --> CPS
    CP --> R
    CPS --> R


    %% Links
    click GPS "https://github.com/AGORA-COL/synthetic_populations"
    click ML "https://github.com/AGORA-COL/fred_parameters_regression"
    click R "https://github.com/AGORA-COL/model-reports"
    click F "https://github.com/AGORA-COL/FRED"
    click FAM "https://github.com/AGORA-COL/fred_colombia_implementation"

    %% Styles
    class F,R,RP,GPS,CPS,AM process;
    class PS,DC repository;
    class EC,ML,FAM,FP model;

    classDef model fill:#fff,stroke:#333,stroke-width:2px,color:#000,rx:10,ry:10;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef software fill:orange,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#ddd,stroke:#333,stroke-width:2px,color:#000;
```

