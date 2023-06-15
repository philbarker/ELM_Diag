
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
    class Accreditation["Accreditation"]{
        +String decision
        +Date reviewDate
        +Date expiryDate
    }
    Accreditation --> WebResource : report
    Accreditation --> Organisation : organisation
    Accreditation --> Qualification : limitQualification
    Accreditation --> Concept : limitField
    Accreditation --> Concept : limitEQFLevel
    Accreditation --> Concept : limitJurisdiction
    Accreditation --> Concept : limitCredentialType
    Accreditation --> Concept : limitAbstractProgramme
    Accreditation --> Organisation : accreditingAgent
    Accreditation --> WebResource : landingPage
    class LearningOpportunity["Learning Opportunity"]
    LearningOpportunity --> Grant : grant
    class Qualification["Qualification"]
    class Grant["Grant"]
```