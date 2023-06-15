
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
    class Accreditation["Accreditation"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
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
    Accreditation --> Concept : status
    Accreditation --> Organisation : accreditingAgent
    Accreditation --> WebResource : landingPage
    class Address["Address"]{
        +String adms_identifier

    }
    Address --> Note : fullAddress
    Address --> Concept : countryCode
    class Agent["Agent]{
        +String adms_identifier
        +String skos_altLabel
        +String skos_prefLabel
    }
    Agent --> Note : additionalNote
    class LearningOpportunity["Learning Opportunity"]
    LearningOpportunity --> Grant : grant
    class Qualification["Qualification"]
    class Grant["Grant"]
```