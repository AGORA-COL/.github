# Data Lake

## Objetivos
- Probar inter-operabilidad de fuentes de información grandes (Big Data) del sistema de salud en Colombia.
- Generar modelos descriptivos y predictivos. 

## Flujo de datos
```mermaid
flowchart LR
    subgraph "1. Datos crudos (RAW)"
        A[(<a href="https://docs.google.com/document/d/1v1sbOreJdBO0SDKUqhwKxVJw9MxYego8/edit">1.1 RIPS</a>)]
        B[(<a href="https://docs.google.com/document/d/1iS1R8nHHWaVkTCsxTbTI5t9atf6AJeuR/edit">1.2 Estadísticas vitales</a>)]
        C[(<a href="https://docs.google.com/document/d/1ErjxN7yliQpPZoOO_h-7L-Qg5XQCONbd/edit">1.3 SEGCOVID</a>)]
        D[(<a href="https://docs.google.com/document/d/17mFQoDqTd8Azzy9971D3XkibAzFu6egv/edit">1.4 SIVIGILA</a>)]
        E[(<a href="https://docs.google.com/document/d/1kIC2y6j7VdZ7J-GziTIGz7EuRUx8Aec9/edit">1.5 VACUNASCOVID</a>)]
    end

    subgraph 2. Data Lake
    F([<a href="./Preproceso.md">2. Preproceso</a>])
    DP[("3. Data preprocesada")]
    G(["4. Generación de Reportes"])
    end

    subgraph 4. Reportes
        R1["4.1 Reporte 1"]
        R2["4.2 Reporte 2"]
        R3["4.3 Reporte 3"]
        R4["4.4 Reporte 4"]
        R5["4.5 Reporte 5"]
    end

    A --> F
    B --> F
    C --> F
    D --> F
    E --> F

    F --> DP
    
    DP --> G

    G --> R1
    G --> R2
    G --> R3
    G --> R4
    G --> R5

    classDef data fill:#f9f,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef process2 fill:green,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#ddd,stroke:#333,stroke-width:2px,color:#000;

    class A,B,C,D,E repository;
    class F process;
    class DP repository;
    class R1,R2,R3,R4,R5 report;
    class G process2;


```

# 2. Preproceso
```mermaid
flowchart LR
    R[("1. Datos crudos (RAW)")]
    subgraph 2. Preproceso
        direction LR
        C(["2.1. Conversión"])
        P[("2.2. Datos en formato Parquet")]
        S(["2.3. Staging"])
    end
    D[("3. Data preprocesada")]

    R --> C --> P --> S --> D

    class R data;
    class C process;
    class P data;
    class S process;
    class D data;

    classDef data fill:white,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef process2 fill:green,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#ddd,stroke:#333,stroke-width:2px,color:#000;

    class A,B,C,D,E data;
    class F process;
    class DL repository;
    class R1,R2,R3,R4,R5 report;
    class G process2;    

```
## 2.2. Conversión
## 2.3. Datos en formato Parquet
## 2.4. Staging
## 2.5. Data preprocesada

# 3. Data Lake
# 4. Generación de Reportes
## 4.1 Reporte 1
## 4.2 Reporte 2
## 4.3 Reporte 3
## 4.4 Reporte 4
## 4.5 Reporte 5


