
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
   note "Based on ELM RDF Ontology turtle representation."
namespace ELM {
    class `Accreditation`["Accreditation"]
    class `LearningOpportunity`["Learning Opportunity"]
    class `Grant`["Grant"]

   LearningOpportunity --> Grant : elm grant
}
```