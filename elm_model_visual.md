
# European Learning Model data model diagrammed using Mermaid.

See [readme](README.md) for details. Yes there is too much in this diagram to be useful 

```mermaid
---
title: ELM Model
description: European Learning Model data model diagrammed using Mermaid.
---
classDiagram
%%======
%% Accreditation
%%======
    class Accreditation["Accreditation"]{
        +String adms_identifier
        +Concept dc_type
        +String dc_title
        +String dc_description
        +Date dc_issued
        +Concept status
        +Date dc_modified
        +Date dc_valid        
        +String   decision
        +Date     reviewDate
        +Concept  limitField
        +Concept  limitEQFLevel
        +Concept  limitJurisdiction
        +Concept  limitCredentialType
        +Concept  limitAbstractProgramme
    }
   Accreditation --> Note : additionalNote
   Accreditation --> WebResource : supplementaryDocument
   Accreditation --> WebResource : foaf_homepage
    Accreditation --> WebResource : report
    Accreditation --> Organisation : organisation
    Accreditation --> Qualification : limitQualification
    Accreditation --> Organisation : accreditingAgent
    Accreditation --> WebResource : landingPage
%%======
%% Address
%%======
    class Address["Address"]{
        +String adms_identifier
        +Concept countryCode
    }
   Address --> Note : fullAddress
%%======
%% Agent
%%======
    class Agent["Agent"]{
        +String adms_identifier
        +String skos_altLabel
        +String skos_prefLabel
        +Date lastModificationDate    
    }
   Agent --> Note : additionalNote
   Agent --> dc_Location : location
    Agent --> ContactPoint : contactPoint
%%======
%% Amount
%%======
    class Amount["Amount"]{
        +String value
        +Concept  unit
    }
%%======
%% Awarding Body
%%======
    class AwardingBody["Awarding Body"]{
    }
%%======
%% Awarding Opportunity
%%======
    class AwardingOpportunity["Awarding Opportunity"]{
        +String adms_identifier
        +Date endDate
    }
   AwardingOpportunity --> dc_Location : location
   AwardingOpportunity --> LearningAchievementSpecification : learningAchievementSpecification
   AwardingOpportunity --> dc_PeriodOfTime : dc_temporal
%%======
%% Awarding Process
%%======
    class AwardingProcess["Awarding Process"]{
        +String adms_identifier
        +String dc_description
        +Date awardingDate
        +Concept educationalSystemNote
    }
   AwardingProcess --> Note : additionalNote
   AwardingProcess --> AwardingBody : awardingBody
   AwardingProcess --> dc_Location : location
   AwardingProcess --> LearningAssessment : used
   AwardingProcess --> Claim : awards
%%======
%% Claim
%%======
    class Claim["Claim"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
        +Concept dc_type
   }
   Claimclass --> Note : additionalNote
   Claimclass --> WebResource : supplementaryDocument
   Claimclass --> Claimclass : hasPart
   Claimclass --> AwardingProcess : awardedBy
    Claim --> Specification : specifiedBy
    Claim --> AwardingProcess : awardedBy
%%======
%% Contact Point
%%======
    class ContactPoint["Contact Point"]{
        +String dc_description
    }
   ContactPoint --> Note : additionalNote
   ContactPoint --> Address : address    
    ContactPoint --> Phone : phone
    ContactPoint --> Mailbox : emailAddress
    ContactPoint --> WebResource : contactForm
%%======
%% Credit Point
%%======
    class CreditPoint["Credit Point"]{
        +String point
    }
    CreditPoint --> WebResource framework
%%======
%% Display Parameter
%%======
    class DisplayParameter ["Display Parameter"]{
        +String dc_title
        +String dc_description
        +Concept dc_language
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
        +String evidenceStatement
        +Concept dc_type
    }
    Evidence --> Agent : evidenceTarget
    Evidence --> MediaObject : embeddedEvidence
%%======
%% European Digital Credential
%%======
    class EuropeanDigitalCredential["European Digital Credential"]{
        +Concept  credentialProfiles
        +String adms_identifier
        +Date dc_issued
        +Date cred_validFrom
        +Date cred_validUntil
        +Date cred_issuanceDate
        +Date cred_expirationDate
        +Concept cred_credentialStatus
    }
   EuropeanDigitalCredential --> Organisation : cred_issuer
   EuropeanDigitalCredential --> Person : cred_subject
   EuropeanDigitalCredential --> WebResource : cred_evidence
   EuropeanDigitalCredential --> WebResource : cred_termsOfUse
   EuropeanDigitalCredential --> WebResource : cred_credentialSchema
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
        +String dc_title
        +String dc_description
        +Concept dc_type
        +URL contentUrl
    }
    Grant --> WebResource : supplementaryDocument
%%======
%% Grading Scheme
%%======
    class GradingScheme["Grading Scheme"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
   }
   GradingScheme --> WebResource : supplementaryDocument   
%%======
%% Group
%%======
    class Group["Group"]{
        +String adms_identifier
        +String skos_altLabel
        +String skos_prefLabel
        +Concept dc_type
    }
   Group --> Note : additionalNote
   Group --> dc_Location : location
   Group --> ContactPoint : contactPoint
   Group --> Agent : foaf_hasMember
%%======
%% Identifier
%%======
    class Identifier["Identifier"]{
        +String skos_notation
        +String adms_schemeAgency
        +Date dc_issued
        +Concept dc_type
    }
   Identifier --> Agent : dc_creator
%%======
%% Individual display
%%======
    class IndividualDisplay["Individual display"]{
        +Concept dc_language
    }
    IndividualDisplay --> DisplayDetail : displayDetail
%%======
%% Learning Achievement
%%======
    class LearningAchievement["Learning Achievement"]{
        +String adms_identifier
        +String dc_title
        +String dc_description
    }
   LearningAchievement --> Note : additionalNote
   LearningAchievement --> WebResource : supplementaryDocument
   LearningAchievement --> LearningAchievement : hasPart
   LearningAchievement --> LearningAchievementSpecification : specifiedBy
   LearningAchievement --> AwardingProcess : awardedBy
%%======
%% Learning Achievement Specification
%%======
    class LearningAchievementSpecification["Learning Achievement Specification"]{
        +String adms_identifier
        +Concept dc_type
        +String dc_title
        +String skos_altLabel
        +String dc_description
        +String category
        +Duration volumeOfLearning
        +Concept dc_language
        +Concept mode
        +Date lastModificationDate
        +Duration maximumDuration
        +Concept  ISCEDFCode
        +Concept  educationSubject
        +Concept  learningSetting
        +Concept  targetGroup
    }
   LearningAchievementSpecification --> Note : additionalNote
   LearningAchievementSpecification --> WebResource : foaf_homepage
   LearningAchievementSpecification --> WebResource : supplementaryDocument
   LearningAchievementSpecification --> LearningAchievementSpecification : hasPart
   LearningAchievementSpecification --> LearningAchievementSpecification : specialisationOf
   LearningAchievementSpecification --> LearningAssessment : provenBy
   LearningAchievementSpecification --> LearningActivity : influencedBy
   LearningAchievementSpecification --> LearningEntitlement : entitlesTo
    LearningAchievementSpecification --> Note : learningOutcomeSummary
    LearningAchievementSpecification --> CreditPoint : creditPoint
    LearningAchievementSpecification --> Note : entryRequirement
    LearningAchievementSpecification --> LearningOutcome : learningOutcome
    LearningAchievementSpecification --> AwardingOpportunity : awardingOpportunity
%%======
%% Learning Activity
%%======
    class LearningActivity["Learning Activity"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String dc_description
    }
   LearningActivity --> Note : additionalNote
   LearningActivity --> WebResource : supplementaryDocument
   LearningActivity --> AwardingProcess : awardedBy
   LearningActivity --> dc_Location : location
   LearningActivity --> dc_PeriodOfTime : dc_temporal
   LearningActivity --> LearningOpportunity : learningOpportunity
   LearningActivity --> LearningActivity : hasPart
   LearningActivity --> LearningActivitySpecification : specifiedBy
%%======
%% Learning Activity Specification
%%======
    class LearningActivitySpecification["Learning Activity Specification"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String skos_altLabel
        +String dc_description
        +String category
        +Concept dc_language
        +Concept mode
        +Date lastModificationDate
    }
   LearningActivitySpecification --> Note : additionalNote
   LearningActivitySpecification --> WebResource : foaf_homepage
   LearningActivitySpecification --> WebResource : supplementaryDocument
   LearningActivitySpecification --> LearningAchievement : influences
   LearningActivitySpecification --> LearningActivitySpecification : hasPart
   LearningActivitySpecification --> LearningActivitySpecification : specialisationOf
%%======
%% Learning Assessment
%%======
    class LearningAssessment["Learning Assessment"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String dc_description
        +Date dc_issued
        +String   grade
        +String   assessmentStatus
        +Concept  grade
        +Concept  idVerification
    }
   LearningAssessment --> Note : additionalNote
   LearningAssessment --> WebResource : supplementaryDocument
   LearningAssessment --> AwardingProcess : awardedBy
   LearningAssessment --> LearningAssessment : hasPart
   LearningAssessment --> LearningAssessmentSpecification : specifiedBy
    LearningAssessment --> ShortenedGrading : shortenedGrading
    LearningAssessment --> ResultDistribution : resultDistribution
    LearningAssessment --> Agent : assessedBy
%%======
%% Learning Assessment Specification
%%======
    class LearningAssessmentSpecification["Learning Assessment Specification"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String skos_altLabel
        +String dc_description
        +String category
        +Concept dc_language
        +Date lastModificationDate
    }
   LearningAssessmentSpecification --> Note : additionalNote
   LearningAssessmentSpecification --> WebResource : foaf_homepage
   LearningAssessmentSpecification --> WebResource : supplementaryDocument
   LearningAssessmentSpecification --> LearningAchievement : proves
   LearningAssessmentSpecification --> LearningAssessmentSpecification : hasPart
   LearningAssessmentSpecification --> LearningAssessmentSpecification : specialisationOf
    LearningAssessmentSpecification --> GradingScheme : gradingScheme
%%======
%% Learning Entitlement
%%======
    class LearningEntitlement["Learning Entitlement"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String dc_description
        +Date dc_issued
        +Date expiryDate
    }
   LearningEntitlement --> Note : additionalNote
   LearningEntitlement --> WebResource : supplementaryDocument
   LearningEntitlement --> AwardingProcess : awardedBy
   LearningEntitlement --> LearningEntitlement : hasPart
   LearningEntitlement --> LearningEntitlementSpecification : specifiedBy
%%======
%% Learning Entitlement Specification
%%======
    class LearningEntitlementSpecification["Learning Entitlement Specification"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String skos_altLabel
        +String dc_description
        +String category
        +Concept status
        +Date lastModificationDate
        +Concept  limitJurisdiction
        +Concept  limitOccupation
        +Concept  limitOccupation
        +Concept  entitlementStatus
    }
   LearningEntitlementSpecification --> Note : additionalNote
   LearningEntitlementSpecification --> WebResource : foaf_homepage
   LearningEntitlementSpecification --> WebResource : supplementaryDocument
   LearningEntitlementSpecification --> LearningAssessment : proves
   LearningEntitlementSpecification --> LearningEntitlementSpecification : hasPart
   LearningEntitlementSpecification --> LearningEntitlementSpecification : specialisationOf
    LearningEntitlementSpecification --> Organisation : limitOrganisation
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
%% Learning Outcome
%%======
    class LearningOutcome["Learning Outcome"]{
        +String adms_identifier
        +String dc_title
        +Concept dc_type
    }
%%======
%% Legal Identifier
%%======
    class LegalIdentifier["Legal Identifier"]{
        +String skos_notation
        +String adms_schemeAgency
        +Date dc_issued
        +Concept dc_type
        +String adms_schemeName
        +String adms_schemeVersion
        +Concept dc_spatial
    }
   Legalidentifier --> Agent : dc_creator
   
%%======
%% Location 
%%======
    class Location["Location"]{
        +String adms_identifier
        +String dc_description
        +String geographicName
        +Concept spatialCode
    }
    Location --> Address : address
%%======
%% Mailbox
%%======
    class Mailbox["Mailbox"]{
    }
%%======
%% Media Object
%%======
    class MediaObject["Media Object"]{
        +String dc_title
        +String dc_description
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
        +Concept dc_language
        +Concept dc_subject
        +String noteLiteral
        +Concept noteFormat
    }
%%======
%% Organisation
%%======
    class Organisation["Organisation"]{
        +String rov_legalName
        +String skos_altLabel
        +String adms_identifier
        +String rov_registration
        +Date lastModificationDate
    }
   Organisation --> WebResource : foaf_homepage
   Organisation --> Note : additionalNote
   Organisation --> Accreditation : accreditation
   Organisation --> dc_Location : location
   Organisation --> ContactPoint : contactPoint
   Organisation --> Organization : org_hasSubOrganization
   Organisation --> Organization : org_subOrganizationOf
   Organisation --> Agent : org_hasMember
    Organisation --> LegalIdentifier : eidasLegalIdentifier
    Organisation --> LegalIdentifier : vatIdentifier
    Organisation --> LegalIdentifier : taxIdentifier
    Organisation --> MediaObject : logo
%%======
%% Period of Time
%%======
    class Person["Person"]{
        +String skos_prefLabel
        +Date startDate
        +Date endDate
    }
%%======
%% Person
%%======
    class Person["Person"]{
        +String foaf_name
        +String foaf_givenName
        +String foaf_familyName
        +String cpv_birthName
        +String cpv_patronymicName
        +String adms_identifier
        +Date lastModificationDate
        +Date     dateOfBirth
        +Concept  gender
        +Concept  citizenshipCountry
    }
   Person --> dc_Location : location
   Person --> ContactPoint : contactPoint
   Person --> Note : additionalNote
   Person --> Organization : org_memberOf
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
        +String adms_identifier
        +String skos_prefLabel
        +String dc_description
    }
   PriceDetail --> Note : additionalNote
    PriceDetail --> Amount : amount
%%======
%% Qualification
%%======
    class Qualification["Qualification"]{
        +String adms_identifier
        +Concept dc_type
        +String dc_title
        +String skos_altLabel
        +String dc_description
        +String category
        +Duration volumeOfLearning
        +Concept dc_language
        +Concept mode
        +Concept ISCEDFCode
        +Concept educationSubject
        +Concept educationLevel
        +Concept learningSetting
        +Duration maximumDuration
        +Concept targetGroup
        +Boolean isPartialQualification
        +Concept  EQFLevel
        +Concept  NQFLevel
        +Concept  qualificationCode
    }
   Qualification --> Note : additionalNote
   Qualification --> WebResource : foaf_homepage
   Qualification --> WebResource : supplementaryDocument
   Qualification --> Qualification : hasPart
   Qualification --> Qualification : specialisationOf
   Qualification --> LearningAssessment : provenBy
   Qualification --> LearningActivity : influencedBy
   Qualification --> LearningEntitlement : entitlesTo
   Qualification --> Note : learningOutcomeSummary
   Qualification --> CreditPoint : creditPoint
   Qualification --> LearningAchievementSpecification : entryRequirement
   Qualification --> LearningOutcome : learningOutcome
   Qualification --> AwardingOpportunity : awardingOpportunity
   Qualification --> Accreditation : accreditation
%%======
%% Qualification Reference
%%======
    class QualificationReference["Qualification Reference"]{
        +String adms_identifier
    }
%%======
%% Result Category
%%======
    class ResultCategory["Result Category"]{
        +String label
        +String score
        +String   minScore
        +String   maxScore
        +PositiveInteger    count
    }
%%======
%% Result Distribution
%%======
    class ResultDistribution["Result Distribution"]{
        +String dc_description
    }
    ResultDistribution --> ResultCategory : resultCategory
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
        +String adms_identifier
        +String dc_title
        +Concept dc_type
        +String skos_altLabel
        +String dc_description
        +Date lastModificationDate
    }
   Specification --> Note : additionalNote
   Specification --> WebResource : foaf_homepage
   Specification --> WebResource : supplementaryDocument
   Specification --> Specification : hasPart
    Specification --> Specification : specialisationOf
    Specification --> Specification : generalisationOf
%%======
%% Verification Check
%%======
    class VerificationCheck["Verification Check"]{
        +Concept dc_type
        +Concept status
        +String dc_description
        +Concept  verificationStatus
        +URL contentUrl
    }
    VerificationCheck --> EuropeanDigitalCredential : subject
%%======
%% Web Resource
%%======
    class WebResource["Web Resource"]{
        +String dc_title
        +Concept dc_language
        +Concept foaf_topic
    }