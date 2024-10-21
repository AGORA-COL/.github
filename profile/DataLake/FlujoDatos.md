# Data Lake

## Objetivos
- Probar inter-operabilidad de fuentes de información grandes (Big Data) del sistema de salud en Colombia.
- Generar modelos descriptivos y predictivos. 

## Flujo de datos
```mermaid
flowchart LR
    subgraph DL[Data Lake]
        subgraph R["Datos crudos (rawdata)"]
            direction LR
            subgraph A[RIPS]
                direction LR
                DATA_RIPS[("/rawdata/rips")]
                DOC_RIPS["`Documento entendimiento 
                de los datos RIPS`"]
                CRIPS[Clasificación RIPS]
            end
            subgraph B[Estadísticas vitales]
                direction LR
                DATA_EV[("/rawdata/vitales")]
                DOC_EV["`Documento entendimiento 
                de los datos ESTADÍSTICAS VITALES`"]
            end
            subgraph C[SEGCOVID]
                direction LR
                DATA_SEGCOVID[(/rawdata/segcovid)]
                DOC_SEGCOVID["`Documento entendimiento 
                de los datos SEGCOVID`"]
            end
            subgraph D[SIVIGILA]
                direction LR
                DATA_SIVIGILA[(/rawdata/sivigila)]
                DOC_SIVIGILA["`Documento entendimiento 
                de los datos SIVIGILA`"]
            end
            subgraph E[VACUNASCOVID]
                direction LR
                DATA_VACUNASCOVID[(/rawdata/vacunascovid2)]
                DOC_VACUNASCOVID["`Documento entendimiento 
                de los datos VACUNASCOVID`"]
            end
        end

        comm1["`Los datos se acceden por *HDFS*
                hdfs dfs -ls /rawdata
        `"]
        comm1 -.-> R
         

        comm2["`/rawdata/vacunascovid 
        tiene datos desactualizados`"]

        comm2 -.-> DATA_VACUNASCOVID

        DATA_RIPS --> L
        DATA_EV --> L
        DATA_SEGCOVID --> L
        DATA_SIVIGILA --> L
        DATA_VACUNASCOVID --> L
        
        L["`**Limpieza**
        (Github: *Data_lake*)`"]
        subgraph DP["Data limpia (stagedata)"]
        end

        comm3["`Los datos se acceden por *HDFS*
                hdfs dfs -ls /stagedata
        `"]
        comm3 -.-> DP

        L --> DP
        DP --> P

        P["`**Preprocesamiento** 
        (Github: *Data_lake*)`"]

        P --> AN

        AN["Data preprocesada (analytics)"]
        comm4["`Los datos se acceden por *HDFS*
                hdfs dfs -ls /analytics
        `"]
        comm4 -.-> AN

        comm5["`Estos datasets todavía
        no están listos`"]

        comm5 -.-> AN
        comm5 -.-> DP
    end
    
    %% AN --> RD
    R --> RD
    %% AN --> RS
    RIPS_MUESTRA --> RS


    subgraph OD["Repositorio OneDrive"]
        RIPS_MUESTRA[("`Muestra RIPS`")]
        PVP[("`Proyecto Visualizador 
        Pandemia - OneDrive`")]
        comm6["`Enlace al reposotorio 
        OneDrive`"]
    end
    PVP --> DB
    

    subgraph G[Generación de reportes]
        RD["`**Reportes descriptivos 
        COVID19**
        (Github: *dl-covid19-descriptive-reports*)`"]
        RS["`**RIPS Surveillance**
        (Github: *quality-rips-surveillance*)`"]
        DB["`**COVID19 Dashboard**
        (Github: *dl-covid19-col-dashboard*)`"]
        PBI["`Reportes PowerBI
        (Github: *Data_lake*)`"]
    end

    DATA_RIPS --> PBI
    RD --> RevDS

    RevDS["Revisión de datasets"]


    classDef data fill:#ffe7a6,stroke:#333,stroke-width:2px,color:#000,rx:0,ry:0;
    classDef doc fill:white,stroke:#333,stroke-width:2px,color:#000;
    classDef process fill:#99f,stroke:#333,stroke-width:2px,color:black,rx:30,ry:30;
    classDef repository fill:#aaa,stroke:#333,stroke-width:2px,stroke: 5 5,color:#000;
    classDef process2 fill:green,stroke:#333,stroke-width:2px,color:#000;
    classDef report fill:#aeb,stroke:#333,stroke-width:2px,color:#000;
    classDef paragraph fill:white,stroke:white;
    classDef comment fill:yellow,stroke:black,color:black,stroke-width:2px,font-style:italic
    classDef container fill:lightgray
    classDef label fill:transparent,stroke:transparent


    class CRIPS,DOC_RIPS,DOC_EV,DOC_SEGCOVID,DOC_SIVIGILA,DOC_VACUNASCOVID doc;
    class DATA_RIPS,DATA_EV,DATA_SEGCOVID,DATA_SIVIGILA,DATA_VACUNASCOVID data;
    class G,DL container;
    class R,DP,OD,AN,RIPS_MUESTRA,PVP data;
    class L,P,PBI,RD,DB,RS process;
    class comm1,comm2,comm3,comm4,comm5,comm6 comment;
    class RevDS report;

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

    click comm6 "https://livejaverianaedu-my.sharepoint.com/personal/jemurillo_javeriana_edu_co/_layouts/15/onedrive.aspx?e=5%3Aa55942a7bb4246b7b87344e4c2d263b8&sharingv2=true&fromShare=true&at=9&CT=1727201099492&OR=OWA%2DNT%2DMail&CID=737d02ea%2Df0eb%2Df341%2Df361%2D9bbdab61b3a7&id=%2Fpersonal%2Fjemurillo%5Fjaveriana%5Fedu%5Fco%2FDocuments%2FJAVERIANA%2FProyecto%20AGORA%2FProyecto%20lago%20de%20datos%20AGORA&FolderCTID=0x012000FE02BE409825504DAFD5FA09F3B44529&view=0"

    click RIPS_MUESTRA "https://livejaverianaedu-my.sharepoint.com/personal/jemurillo_javeriana_edu_co/_layouts/15/onedrive.aspx?e=5%3Aa55942a7bb4246b7b87344e4c2d263b8&sharingv2=true&fromShare=true&at=9&CT=1727201099492&OR=OWA-NT-Mail&CID=737d02ea-f0eb-f341-f361-9bbdab61b3a7&id=%2Fpersonal%2Fjemurillo_javeriana_edu_co%2FDocuments%2FJAVERIANA%2FProyecto%20AGORA%2FProyecto%20lago%20de%20datos%20AGORA%2FRIPS-%20Rutina%20clasificaci%C3%B3n%2Fdata&FolderCTID=0x012000FE02BE409825504DAFD5FA09F3B44529&view=0"

    click PBI "https://github.com/AGORA-COL/Data_lake/tree/main/Notebooks/PowerBI"

    click RevDS "https://drive.google.com/drive/folders/1_keziEHX_UJUSq2jJeK7qCer3D5KFRW_"
```
