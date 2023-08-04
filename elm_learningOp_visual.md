# ELM Learning Opportunity.

European Learning Model (ELM) showing just the neighbourhood aournd the `LearningOpportunity` class. See [readme](README.md) for details. 

```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
%%======
%% Learning Opportunity
%%======
    class LearningOpportunity["Learning Opportunity"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
        +Concept dc_type
        +Concept  learningSchedule
    }
   LearningOpportunity --> Note : additionalNote
   LearningOpportunity --> WebResource : foaf_homepage
   LearningOpportunity --> WebResource : supplementaryDocument
   LearningOpportunity --> dc_PeriodOfTime : dc_temporal
   LearningOpportunity --> dc_Location : location
   LearningOpportunity --> LearningOpportunity : hasPart
    LearningOpportunity --> Grant : grant
    LearningOpportunity --> Note : scheduleInformation
    LearningOpportunity --> Note : admissionProcedure
    LearningOpportunity --> PriceDetail : priceDetails
    LearningOpportunity --> MediaObject : bannerImage
%%======
%% Inbound links
%%======

       LearningActivity --> LearningOpportunity : learningOpportunity
