# Data Lake

## Objetivos
- Probar inter-operabilidad de fuentes de información grandes (Big Data) del sistema de salud en Colombia.
- Generar modelos descriptivos y predictivos. 

## Flujo de datos
```mermaid
flowchart LR
    subgraph DL[Data Lake]
        subgraph R["Datos crudos (rawdata)"]
            subgraph A[RIPS]
                DATA_RIPS[Datos RIPS]
                DOC_RIPS["`Documento entendimiento
                     de los datos 
                     RIPS`"]
                CRIPS([Clasificación RIPS])
            end
            subgraph B[Estadísticas vitales]
                DATA_EV[Datos Estarísticas vitales]
                DOC_EV["`Documento entendimiento
                     de los datos 
                     ESTADÍSTICAS VITALES`"]
            end
            subgraph C[SEGCOVID]
                DATA_SEGCOVID[Datos SEGCOVID]
                DOC_SEGCOVID["`Documento entendimiento
                     de los datos 
                     SEGCOVID`"]
            end
            subgraph D[SIVIGILA]
                DATA_SIVIGILA[Datos SIVIGILA]
                DOC_SIVIGILA["`Documento entendimiento
                     de los datos 
                     SIVIGILA`"]
            end
            subgraph E[VACUNASCOVID]
                DATA_VACUNASCOVID[Datos VACUNASCOVID]
                DOC_VACUNASCOVID["`Documento entendimiento
                     de los datos 
                     VACUNASCOVID`"]
            end
        end


        A --> L
        B --> L
        C --> L
        D --> L
        E --> L

        
        L([Limpieza])
        subgraph DP["Data limpia (stagedata)"]
        end

        L --> DP
        DP --> P

        P([Preprocesamiento])

        P --> ST

        ST[Stage]

    end
    
    ST --> RD
    ST --> RS


    OD[(Repositorio OneDrive)]

    OD --> DB

    subgraph G["Generación de reportes"]
        RD([Reportes descriptivos])
        DB([COVID19 Dashboard])
        RS([RIPS Surveillance])
    end


    


    classDef data fill:#fff,stroke:#333,stroke-width:2px,color:#000,rx:10,ry:10;
    classDef doc fill:#cab,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black;
    classDef repository fill:#aaa,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef process2 fill:green,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#aeb,stroke:#333,stroke-width:2px,color:#000;

    class DOC_RIPS,DOC_EV,DOC_SEGCOVID,DOC_SIVIGILA,DOC_VACUNASCOVID doc;
    class DATA_RIPS,DATA_EV,DATA_SEGCOVID,DATA_SIVIGILA,DATA_VACUNASCOVID data;
    class R data;
    class DL repository;
    class CRIPS process;
    class L,P process;
    class DP,OD,ST data;
    class RD,DB,RS process

    click L "https://github.com/AGORA-COL/Data_lake"
    click P "https://github.com/AGORA-COL/Data_lake"

    click DOC_RIPS "https://docs.google.com/document/d/1v1sbOreJdBO0SDKUqhwKxVJw9MxYego8/view"
    click DOC_EV "https://docs.google.com/document/d/1iS1R8nHHWaVkTCsxTbTI5t9atf6AJeuR/view"
    click DOC_SEGCOVID "https://docs.google.com/document/d/1ErjxN7yliQpPZoOO_h-7L-Qg5XQCONbd/view"
    click DOC_SIVIGILA "https://docs.google.com/document/d/17mFQoDqTd8Azzy9971D3XkibAzFu6egv/view"
    click DOC_VACUNASCOVID "https://docs.google.com/document/d/1kIC2y6j7VdZ7J-GziTIGz7EuRUx8Aec9/view"

    click CRIPS "https://drive.google.com/drive/folders/1pApPVLWTkwgCbYgMG0tAWkvJDn2RRe1K"

    click RD "https://github.com/AGORA-COL/dl-covid19-descriptive-reports"
    click DB "https://github.com/AGORA-COL/dl-covid19-col-dashboard"
    click RS "https://github.com/AGORA-COL/quality-rips-surveillance"

    click OD "https://livejaverianaedu-my.sharepoint.com/personal/jemurillo_javeriana_edu_co/_layouts/15/onedrive.aspx?e=5%3Afc7d68d1a9c84f048235ca67be22ebb1&sharingv2=true&fromShare=true&at=9&CT=1725289769440&OR=OWA-NT-Mail&CID=9c3ffb10-dcf6-37df-ea1c-3b1c7661d5db&id=%2Fpersonal%2Fjemurillo_javeriana_edu_co%2FDocuments%2FJAVERIANA%2FDatos_AGORA%2FPANDEMIA%20COLOMBIA-raw_data&FolderCTID=0x012000FE02BE409825504DAFD5FA09F3B44529&view=0"
```
