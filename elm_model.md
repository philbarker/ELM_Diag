
```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
%%=========
%% Accreditation
%%=========
    class Accreditation["Accreditation"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
        +Date dc_issued
        +Date dc_modified
        +Date dc_valid
        +String decision
        +Date reviewDate
        +Date expiryDate
        +Concept limitField
        +Concept limitEQFLevel
        +Concept limitJurisdiction
        +Concept limitCredentialType
        +Concept limitAbstractProgramme
        +Concept status
        +Concept dc_type
    }
    Accreditation --> WebResource : report
    Accreditation --> Organisation : organisation
    Accreditation --> Qualification : limitQualification
    Accreditation --> Organisation : accreditingAgent
    Accreditation --> WebResource : landingPage
    Accreditation --> WebResource : foaf_homePage
    Accreditation --> WebResource : supplementaryDocument
%%=========
%% Address
%%=========
    class Address["Address"]{
        +String adms_identifier
        +Concept countryCode
    }
    Address --> Note : fullAddress
%%=========
%% Agent
%%=========
    class Agent["Agent"]{
        +String adms_identifier
        +String skos_altLabel
        +String skos_prefLabel
        +Date lastModificationDate
    }
    Agent --> Note : additionalNote
    Agent --> dc_Location : location
    Agent --> ContactPoint : contactPoint
%%=========
%% Group
%%=========
    class Group["Group"]{
        +String adms_identifier
        +String skos_altLabel
        +String skos_prefLabel
        +Concept dc_type
    }
    Group --> Note : additionalNote
    Group --> dc_Location : location
    Group --> ContactPoint : contactPoint
    Group --> Agent : foaf_member
%%=========
%% Amount
%%=========
    class Amount["Amount"]{
        +Concept unit
        +String value
    }
%%=========
%% AwardingOpportunity
%%=========
    class AwardingOpportunity["Awarding Opportunity"]{
        +String adms_identifier
    }
    AwardingOpportunity --> dc_Location : location
    AwardingOpportunity --> LearningAchievementSpecification : learningAchievementSpecification
    AwardingOpportunity --> dc_temproal : dc_PeriodOfTime
    AwardingOpportunity --> Organisation : awardingBody 
%%=========
%% AwardingProcess
%%=========
    class AwardingProcess["Awarding Process"]{
        +String adms_identifier
        +String dc_description
        +Date awardingDate
        +Concept educationalSystemNote
    }
    AwardingProcess --> Note : additionalNote
    AwardingProcess --> Organization : awardingBody
    AwardingProcess --> dc_Location : location
    AwardingProcess --> LearningAssessment : used
    AwardingProcess --> Claim : awards
%%=========
%% Claim
%%=========
    class Claim["Claim"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
        +Concept dc_type
    }
    Claim --> Note : additionalNote
    Claim --> WebResource : supplementaryDocument
    Claim --> AwardingProcess : awardedBy
    Claim --> Specification : specifiedBy
    Claim --> Claim : hasPart
%%=========
%% Code
%%=========
    class Code["Code (as skos Concept)"]{
        +String skos_prefLabel
    }
    Code --> ConceptScheme : inScheme
%%======
%% Contact Point
%%======
    class ContactPoint["Contact Point"]{
    }
    ContactPoint --> Phone : phone
    ContactPoint --> Mailbox : emailAddress
    ContactPoint --> WebResource : contactForm

```



Copy from auto translation

%%======
%% Contact Point
%%======
    class ContactPoint["Contact Point"]{
    }
    ContactPoint --> Phone : phone
    ContactPoint --> Mailbox : emailAddress
    ContactPoint --> WebResource : contactForm
%%======
%% Credit Point
%%======
    class CreditPoint["Credit Point"]{
    }
%%======
%% Display Parameter
%%======
    class DisplayParameter ["Display Parameter"]{
    }
    DisplayParameter  --> IndividualDisplay : individualDisplay
%%======
%% Display Detail
%%======
    class DisplayDetail["Display Detail"]{
    }
%%======
%% Evidence
%%======
    class Evidence["Evidence"]{
    }
%%======
%% European Digital Credential
%%======
    class EuropeanDigitalCredential["European Digital Credential"]{
        +Concept  credentialProfiles
    }
    EuropeanDigitalCredential --> DisplayParameter  : displayParameter
    EuropeanDigitalCredential --> MediaObject : attachment
%%======
%% European Digital Credential Presentation
%%======
    class EuropeanDigitalPresentation["European Digital Credential Presentation"]{
    }
    EuropeanDigitalPresentation --> EuropeanDigitalCredential : verifiableCredential
    EuropeanDigitalPresentation --> VerificationCheck : verificationCheck
%%======
%% Grant
%%======
    class Grant["Grant"]{
    }
%%======
%% Grading Scheme
%%======
    class GradingScheme["Grading Scheme"]{
    }
%%======
%% Group
%%======
    class Group["Group"]{
    }
%%======
%% Identifier
%%======
    class Identifier["Identifier"]{
    }
%%======
%% Individual display
%%======
    class IndividualDisplay["Individual display"]{
    }
    IndividualDisplay --> DisplayDetail : displayDetail
%%======
%% Learning Achievement
%%======
    class LearningAchievement["Learning Achievement"]{
    }
%%======
%% Learning Achievement Specification
%%======
    class LearningAchievementSpecification["Learning Achievement Specification"]{
        +Duration maximumDuration
        +Concept  ISCEDFCode
        +Concept  educationSubject
        +Concept  learningSetting
        +Concept  targetGroup
    }
    LearningAchievementSpecification --> Note : learningOutcomeSummary
    LearningAchievementSpecification --> CreditPoint : creditPoint
    LearningAchievementSpecification --> Note : entryRequirement
    LearningAchievementSpecification --> LearningOutcome : learningOutcome
    LearningAchievementSpecification --> AwardingOpportunity : awardingOpportunity
%%======
%% Learning Activity
%%======
    class LearningActivity["Learning Activity"]{
    }
%%======
%% Learning Activity Specification
%%======
    class LearningActivitySpecification["Learning Activity Specification"]{
    }
%%======
%% Learning Assessment
%%======
    class LearningAssessment["Learning Assessment"]{
        +String   grade
        +String   assessmentStatus
        +Concept  grade
        +Concept  idVerification
    }
    LearningAssessment --> ShortenedGrading : shortenedGrading
    LearningAssessment --> ResultDistribution : resultDistribution
    LearningAssessment --> Agent : assessedBy
%%======
%% Learning Assessment Specification
%%======
    class LearningAssessmentSpecification["Learning Assessment Specification"]{
    }
    LearningAssessmentSpecification --> GradingScheme : gradingScheme
%%======
%% Learning Entitlement
%%======
    class LearningEntitlement["Learning Entitlement"]{
    }
%%======
%% Learning Entitlement Specification
%%======
    class LearningEntitlementSpecification["Learning Entitlement Specification"]{
        +Concept  limitJurisdiction
        +Concept  limitOccupation
        +Concept  limitOccupation
        +Concept  entitlementStatus
    }
    LearningEntitlementSpecification --> Organisation : limitOrganisation
%%======
%% Learning Opportunity
%%======
    class LearningOpportunity["Learning Opportunity"]{
        +Concept  learningSchedule
    }
    LearningOpportunity --> Grant : grant
    LearningOpportunity --> Note : scheduleInformation
    LearningOpportunity --> Note : admissionProcedure
    LearningOpportunity --> PriceDetail : priceDetails
    LearningOpportunity --> MediaObject : bannerImage
%%======
%% Learning Outcome
%%======
    class LearningOutcome["Learning Outcome"]{
    }
%%======
%% Legal Identifier
%%======
    class LegalIdentifier["Legal Identifier"]{
    }
%%======
%% Mailbox
%%======
    class Mailbox["Mailbox"]{
    }
%%======
%% Media Object
%%======
    class MediaObject["Media Object"]{
        +String   content
        +Integer  contentSize
        +Concept  contentEncoding
        +Concept  contentType
        +Concept  attachmentType
    }
%%======
%% Note
%%======
    class Note["Note"]{
    }
Remaining properties:  [rdflib.term.URIRef('http://data.europa.eu/snb/model/elm/noteLiteral'), rdflib.term.URIRef('http://data.europa.eu/snb/model/elm/noteFormat')]
%%======
%% Organisation
%%======
    class Organisation["Organisation"]{
    }
    Organisation --> LegalIdentifier : eidasLegalIdentifier
    Organisation --> LegalIdentifier : vatIdentifier
    Organisation --> LegalIdentifier : taxIdentifier
    Organisation --> MediaObject : logo
%%======
%% Person
%%======
    class Person["Person"]{
        +Date     dateOfBirth
        +Concept  gender
        +Concept  citizenshipCountry
    }
    Person --> MediaObject : dateOfBirth
    Person --> LegalIdentifier : nationalId
    Person --> Group : groupMemberOf
    Person --> EuropeanDigitalCredential : hasCredential
    Person --> Claim : hasClaim
%%======
%% Phone
%%======
    class Phone["Phone"]{
        +String   phoneNumber
        +String   countryDialing
        +String   areaDialing
        +String   dialNumber
    }
%%======
%% Price Detail
%%======
    class PriceDetail["Price Detail"]{
    }
    PriceDetail --> Amount : amount
%%======
%% Qualification
%%======
    class Qualification["Qualification"]{
        +Boolean isPartialQualification
        +Concept  EQFLevel
        +Concept  NQFLevel
        +Concept  qualificationCode
    }
%%======
%% Qualification Reference
%%======
    class QualificationReference["Qualification Reference"]{
    }
%%======
%% Result Category
%%======
    class ResultCategory["Result Category"]{
        +String   minScore
        +String   maxScore
        +PositiveInteger    count
    }
%%======
%% Result Distribution
%%======
    class ResultDistribution["Result Distribution"]{
    }
%%======
%% Shortened Grading
%%======
    class ShortenedGrading["Shortened Grading"]{
        +Integer  percentageLower
        +Integer  percentageEqual
        +Integer  percentageHigher
    }
%%======
%% Specification
%%======
    class Specification["Specification"]{
    }
    Specification --> Specification : specialisationOf
    Specification --> Specification : generalisationOf
%%======
%% Verification Check
%%======
    class VerificationCheck["Verification Check"]{
        +Concept  verificationStatus
    }
    VerificationCheck --> EuropeanDigitalCredential : subject
%%======
%% Web Resource
%%======
    class WebResource["Web Resource"]{
    }
%%======
%% Shacl Validator 2017
%%======
    class ShaclValidator2017["Shacl Validator 2017"]{
    }