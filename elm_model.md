
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
    class Accreditation["Accreditation"]{
        +String decision
    }
    Accreditation --> WebResource : report
    Accreditation --> Organisation : organisation
    Accreditation --> Qualification : limitQualification
    LearningOpportunity --> Grant : grant
    class LearningOpportunity["Learning Opportunity"]
    class Qualification["Qualification"]
    class Grant["Grant"]
```