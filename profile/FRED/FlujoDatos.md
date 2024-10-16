# Modelo dinámico y de Agentes

El modelo FRED (Grefenstette et al., 2013) permite explorar cómo una enfermedad se propaga dentro de una población a través del tiempo.

En este caso, se utiliza para simular el proceso de dispersión del virus SARS-CoV-2 en cada departamento de Colombia.

![](../images/image.png)

# Flujo de datos

```mermaid
flowchart TB
    subgraph EPS[Elaboración Poblaciones sintéticas]
        GPS(["`Generador poblaciones sintéticas.
        Github: synthetic_populations`"])
        PS[(Poblaciones sintéticas)]
        CPS([Comparación poblaciones sintéticas])
        DC[(Datos censo 2018)]
    end 
    PS --> F
    subgraph CP[Calibración de parámetros]
        EC[Escenarios contrafactuales]
        FAM[Fred Agent Model]
        F(["`Versión modificada de FRED. 
        Github: FRED`"])
        FP[Parámetros FRED]
        RP(["`Regresión de parámetros. Github: fred_parameters_regression`"])
        ML[Modelo ML para regresión]
        AM([Actualizar modelo])
        EC --> F --> FP --> RP --> ML --> AM --> FAM --> F
    end
    R(["`Generación de reportes. Github: model-reports`"])

    GPS --> PS --> CPS
    DC --> CPS
    CP --> R
    CPS --> R


    %% Links
    click DC "https://livejaverianaedu-my.sharepoint.com/personal/jemurillo_javeriana_edu_co/_layouts/15/onedrive.aspx?e=5%3Aa55942a7bb4246b7b87344e4c2d263b8&sharingv2=true&fromShare=true&at=9&CT=1727201099492&OR=OWA%2DNT%2DMail&CID=737d02ea%2Df0eb%2Df341%2Df361%2D9bbdab61b3a7&id=%2Fpersonal%2Fjemurillo%5Fjaveriana%5Fedu%5Fco%2FDocuments%2FJAVERIANA%2FProyecto%20AGORA%2FProyecto%20FRED%20AGORA%2FDatos%20FRED%2FFRED%2Dinputs&FolderCTID=0x012000FE02BE409825504DAFD5FA09F3B44529&view=0"
    click GPS "https://github.com/AGORA-COL/synthetic_populations"
    click RP "https://github.com/AGORA-COL/fred_parameters_regression"
    click R "https://github.com/AGORA-COL/model-reports"
    click F "https://github.com/AGORA-COL/FRED"
    click FAM "https://github.com/AGORA-COL/fred_colombia_implementation"

    %% Styles
    class F,R,RP,GPS,CPS,AM process;
    class PS,DC repository;
    class EC,ML,FAM,FP model;

    classDef model fill:#fff,stroke:#333,stroke-width:2px,color:#000,rx:10,ry:10;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black,rx:30,ry:30;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef software fill:orange,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#ddd,stroke:#333,stroke-width:2px,color:#000;
```

