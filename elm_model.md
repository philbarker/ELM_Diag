
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
    class Accreditation["Accreditation"]{
        +String decision
        +Comment("The quality assurance or licensing of an organisation or a qualification. An accreditation instance can be used to specify information about:  (1) the quality assurance and/or licensing of an organisation,  (2) the quality assurance and/or licensing of an organisation with respect to a specific qualification.")
    }
    Accreditation --> WebResource : report

    class LearningOpportunity["Learning Opportunity"]
    LearningOpportunity --> Grant : grant
    class Grant["Grant"]
    class Qualification["Qualification]


```