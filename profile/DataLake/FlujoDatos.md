# Data Lake

## Objetivos
- Probar inter-operabilidad de fuentes de información grandes (Big Data) del sistema de salud en Colombia.
- Generar modelos descriptivos y predictivos. 

## Flujo de datos
```mermaid
flowchart LR
    subgraph R["1. Datos crudos (RAW)"]
        subgraph A[1.1 RIPS]
            DRIPS1[1. Documento entendimiento de los datos-RIPS- 2024-1.5v.docx]
            CRIPS1[Clasificación RIPS]
        end
        subgraph B[1.2 Estadísticas vitales]
            DRIPS2[2. Documento entendimiento de los datos- ESTADÍSTICAS VITALES- 2024-1.5v.docx]
        end
        subgraph C[1.3 SEGCOVID]
            DRIPS3[3. Documento entendimiento de los datos-SEGCOVID 2024-1.5v.docx]
        end
        subgraph D[1.4 SIVIGILA]
            DRIPS4[4. Documento entendimiento de los datos-SIVIGILA-2024-1.5v.docx]
        end
        subgraph E[1.5 VACUNASCOVID]
            DRIPS5[5. Documento entendimiento de los datos-VACUNASCOVID-2024-1.5v.docx]
        end
    end

    P([2. Preproceso])
    DP[("3. Data preprocesada")]
    subgraph G["4. Generación de reportes"]
        RD[Reportes descriptivos]
        DB[COVID19 Dashboard]
        RS[RIPS Surveillance]
    end


    A --> P
    B --> P
    C --> P
    D --> P
    E --> P

    P --> DP
    
    DP --> G


    classDef data fill:#fff,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#fff,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef process2 fill:green,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#aeb,stroke:#333,stroke-width:2px,color:#000;

    class DIRPS1,DRIPS2,DRIPS3,DRIPS4,DRIPS5,CRIPS1 repository;
    class P process;
    class DP repository;
    class RD,DB,RS repository

    click P "https://github.com/AGORA-COL/Data_lake"

    click DRIPS1 "https://docs.google.com/document/d/1v1sbOreJdBO0SDKUqhwKxVJw9MxYego8/view"
    click CRIPS1 "https://drive.google.com/drive/folders/1pApPVLWTkwgCbYgMG0tAWkvJDn2RRe1K"

    click DRIPS2 "https://docs.google.com/document/d/1iS1R8nHHWaVkTCsxTbTI5t9atf6AJeuR/view"
    click DRIPS3 "https://docs.google.com/document/d/1ErjxN7yliQpPZoOO_h-7L-Qg5XQCONbd/view"
    click DRIPS4 "https://docs.google.com/document/d/17mFQoDqTd8Azzy9971D3XkibAzFu6egv/view"
    click DRIPS5 "https://docs.google.com/document/d/1kIC2y6j7VdZ7J-GziTIGz7EuRUx8Aec9/view"

    click RD "https://github.com/AGORA-COL/dl-covid19-descriptive-reports"
    click DB "https://github.com/AGORA-COL/dl-covid19-col-dashboard"
    click RS "https://github.com/AGORA-COL/quality-rips-surveillance"
```
