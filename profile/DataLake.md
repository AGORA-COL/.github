<style>

</style>

# Data Lake

## Objetivos
- Testar inter-operabilidad de fuentes de información grandes (Big Data) del sistema de salud en Colombia.
- Generar modelos descriptivos y predictivos. 

## Flujo de datos
```mermaid
flowchart LR
    subgraph "1. Datos crudos (RAW)"
        A[("1.1 RIPS")]
        B[("1.2 Estadísticas Vitales")]
        C[("1.3 SEGCOVID")]
        D[("1.4 SIVIGILA")]
        E[("1.5 VACUNASCOVID")]
    end

    subgraph 2. Data Lake
    F(["2. Preproceso"])
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
# 1. Datos crudos (RAW)
## 1.1 RIPS
## 1.2 Estadísticas Vitales
## 1.3 SEGCOVID
## 1.4 SIVIGILA
## 1.5 VACUNASCOVID
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


