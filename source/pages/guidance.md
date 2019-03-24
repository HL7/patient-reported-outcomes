---
title: Implementation Guidance
layout: default
active: guidance
f: http://build.fhir.org/
---

{:.no_toc}

<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

### Introduction

The implementation guidance outlined in this page provides useful information for developers implementing the various PRO actors and their capabilities. All resources and parameters used in this part of the IG are examples and are expected to conform to the resources, profiles and other constraints outlined in the [CapabilityStatements](capstatements.html).

### Implementation Guidance for administering Basic Questionnaires

The section outlines the implementation guidance for the various actors involved in the administration of Basic Questionnaires.

#### PROM Instrument and Meta data Repository Implementation

​The capabilities and requirements that need to be implemented by the PROM Instrument and Meta data Repository are outlined at [CapabilityStatements](capstatements.html)

Developers can follow these steps to implement the above capabilities.

**Step 1:** Implement a FHIR Server. (Choose Release 4)

There are many open source FHIR Servers that are available to be downloaded and used instead of starting from scratch. These can be found at [FHIR Open Source Implementations](http://wiki.hl7.org/index.php?title=Open_Source_FHIR_implementations).

Publish the FHIR Server Capability Statement for the Server.

**Step 2:** Implement the APIs for Questionnaires

* POST API : Support Creation of a PRO Measure using Questionnaire Resource and store it in a repository. 

`POST [BaseURL]/Questionnaire/` - Submit payload (body) of Questionnaire in JSON format.


* GET API : Will be used by an EHR or an External PRO Administration App to download a specific questionnaire.

`GET [BaseURL]/Questionnaire/1234` - Receive a payload (body) of Questionnaire in JSON format.

`GET [BaseURL]/Questionnaire/?_summary=true` - Receive all Questionnaires present in the system in summary format.

* Search API - Find Specific questionnaires.

`GET [BaseURL]/Questionnaire?_identifier=phq-9` - Receive a phq-9 Questionnaire.


**Step 3:** Implement appropriate security protocols for the Server.

At a minimum, HTTPS protocols must be used for the implementation using the right certificate.

#### EHR or Care Delivery Health IT System

​The capabilities and requirements that need to be implemented by the EHR or Care Delivery Health IT System to support PRO requirements are outlined at [CapabilityStatements](capstatements.html)

Developers can follow these steps to implement the above capabilities.

**Step 1:** Implement a FHIR Server. (Choose Release 4)

There are many open source FHIR Servers that are available to be downloaded and used instead of starting from scratch. These can be found at [FHIR Open Source Implementations](http://wiki.hl7.org/index.php?title=Open_Source_FHIR_implementations).

Map EHR data (schemas,tables,lookup tables) to FHIR Resources and interfaces as needed. (Some common FHIR resources that will be required are Patient, Observation, and Procedure)

Publish the FHIR Server Capability Statement for the Server.

**Step 2a:** Implement the APIs for Questionnaires

* POST API : Support creation of PRO Measure using Questionnaire Resource and store it internally for tracking administrations. 

`POST [BaseURL]/Questionnaire/` - Submit payload (body) of Questionnaire in JSON format.


* GET API : Will be used to download a specific Questionnaire by authorized systems and personnel.

`GET [BaseURL]/Questionnaire/1234` - Receive a payload (body) of Questionnaire in JSON format.

`GET [BaseURL]/Questionnaire/?_summary=true` - Receive all Questionnaires present in the system in summary format.

* Search API - Find Specific questionnaires.

`GET [BaseURL]/Questionnaire?_identifier=phq-9` - Receive a phq-9 Questionnaire.

**Step 2b:** Implement the APIs for QuestionnaireResponse

* POST API : Support collection of PRO Responses using QuestionnaireResponse Resource and store it internally for tracking administrations. 

`POST [BaseURL]/QuestionnaireResponse/` - Submit payload (body) of QuestionnaireResponse in JSON format.


* GET API : Will be used to download a specific QuestionnaireResponse (PRO Responses) by authorized systems and personnel.

`GET [BaseURL]/QuestionnaireResponse/1234` - Receive a payload (body) of QuestionnaireResponse in JSON format.

* Search API - Find Specific QuestionnaireResponses.

`GET [BaseURL]/QuestionnaireResponse?patient=1234` - Receive all QuestionnaireResponses for a patient

`GET [BaseURL]/QuestionnaireResponse?questionnaire=1234&authored=gt2017-01-15` - Receive QuestionnaireResponses for a specific questionnaire administered after Jan 15 2017.

**Step 3:** Implement appropriate security protocols for the Server.

At a minimum, HTTPS protocols must be used for the implementation using the right certificate.

**Step 4:** Implement SMART on FHIR Authorization Server (Only if the EHR supports External PRO Administration System)

When the EHR supports integration with External PRO Administration System, the EHR system has to be complemented with a SMART on FHIR Authorization Server that can be used to authorize the External App. The External App would be launched with Patient Context and after the data is collected the External App will submit the data to the EHR using the POST APIs.

To implement the SMART on FHIR Authorization Server and other SMART on FHIR capabilities, refer to [SMART on FHIR Sandbox](https://sandbox.smarthealthit.org).

#### External PRO Administration System

​The capabilities and requirements that need to be implemented by the External PRO Administration System to support PRO requirements are outlined at [CapabilityStatements](capstatements.html)

Developers can follow these steps to implement the above capabilities.

**Step 1:** Implement a FHIR Server. (Choose Release 4)

There are many open source FHIR Servers that are available to be downloaded and used instead of starting from scratch. These can be found at [FHIR Open Source Implementations](http://wiki.hl7.org/index.php?title=Open_Source_FHIR_implementations).

Publish the FHIR Server Capability Statement for the Server.

**Step 2a:** Implement the APIs for Questionnaires

* POST API : Support creation of PRO Measure using Questionnaire Resource and store it internally for tracking administrations. 

`POST [BaseURL]/Questionnaire/` - Submit payload (body) of Questionnaire in JSON format.

* GET API : Will be used to download a specific Questionnaire by authorized systems and personnel.

`GET [BaseURL]/Questionnaire/1234` - Receive a payload (body) of Questionnaire in JSON format.

`GET [BaseURL]/Questionnaire/?_summary=true` - Receive all Questionnaires present in the system in summary format.

* Search API - Find Specific questionnaires.

`GET [BaseURL]/Questionnaire?_identifier=phq-9` - Receive a phq-9 Questionnaire.

**Step 2b:** Implement the APIs for QuestionnaireResponse

* POST API : Support collection of PRO Responses using QuestionnaireResponse Resource and store it internally for tracking administrations. 

`POST [BaseURL]/QuestionnaireResponse/` - Submit payload (body) of QuestionnaireResponse in JSON format.


* GET API : Will be used to download a specific QuestionnaireResponse (PRO Responses) by authorized systems and personnel.

`GET [BaseURL]/QuestionnaireResponse/1234` - Receive a payload (body) of QuestionnaireResponse in JSON format.

* Search API - Find Specific QuestionnaireResponses.

`GET [BaseURL]/QuestionnaireResponse?patient=1234` - Receive all QuestionnaireResponses for a patient

`GET [BaseURL]/QuestionnaireResponse?questionnaire=1234&authored=gt2017-01-15` - Receive QuestionnaireResponses for a specific questionnaire administered after Jan 15 2017.

**Step 3:** Implement appropriate security protocols for the Server.

At a minimum, HTTPS protocols must be used for the implementation using the right certificate.

**Step 4:** Implement SMART on FHIR Authorization for clients (Only if the External PRO Administration System interacts with an EHR)

When the External PRO Administration System interacts with an EHR, the External PRO Administration System has to be registered with the EHRs Authorization Server to enable launching from within the EHR using SMART on FHIR Authorization protocols. After launch, the External PRO Administration System must support the query of appropriate resources for context. 

To implement the SMART on FHIR Authorization Server and other SMART on FHIR capabilities, refer to [SMART on FHIR Sandbox](https://sandbox.smarthealthit.org).

Once the data is collected, the External PRO Administration System may store the PRO responses in the EHR using the POST API creating the QuestionnaireResponse.

### Implementation Guidance for administering Adaptive Questionnaires

The section outlines the implementation guidance for the various actors involved in the administration of Adaptive Questionnaires.

#### Patient Facing Administration App

​The capabilities and requirements that need to be implemented by the Patient Facing Administration App to support PRO requirements are outlined at [CapabilityStatements](capstatements.html)

Developers can follow these steps to implement the above capabilities.

**Step 1:** Implement a FHIR Server. (Choose Release 4)

There are many open source FHIR Servers that are available to be downloaded and used instead of starting from scratch. These can be found at [FHIR Open Source Implementations](http://wiki.hl7.org/index.php?title=Open_Source_FHIR_implementations).

Publish the FHIR Server Capability Statement for the Server.

**Step 2a:** Implement the APIs for Questionnaires

* POST API : Support creation of PRO Measure using Questionnaire Resource and store it internally for tracking administrations. 

`POST [BaseURL]/Questionnaire/` - Submit payload (body) of Questionnaire in JSON format.


* GET API : Will be used to download a specific Questionnaire by authorized systems and personnel.

`GET [BaseURL]/Questionnaire/1234` - Receive a payload (body) of Questionnaire in JSON format.

`GET [BaseURL]/Questionnaire/?_summary=true` - Receive all Questionnaires present in the system in summary format.

* Search API - Find Specific questionnaires.

`GET [BaseURL]/Questionnaire?_identifier=phq-9` - Receive a phq-9 Questionnaire.

**Step 2b:** Implement the APIs for QuestionnaireResponse

* POST API : Support collection of PRO Responses using QuestionnaireResponse Resource and store it internally for tracking administrations. 

`POST [BaseURL]/QuestionnaireResponse/` - Submit payload (body) of QuestionnaireResponse in JSON format.


* GET API : Will be used to download a specific QuestionnaireResponse (PRO Responses) by authorized systems and personnel.

`GET [BaseURL]/QuestionnaireResponse/1234` - Receive a payload (body) of QuestionnaireResponse in JSON format.

* Search API - Find Specific QuestionnaireResponses.

`GET [BaseURL]/QuestionnaireResponse?patient=1234` - Receive all QuestionnaireResponses for a patient

`GET [BaseURL]/QuestionnaireResponse?questionnaire=1234&authored=gt2017-01-15` - Receive QuestionnaireResponses for a specific questionnaire administered after Jan 15 2017.

**Step 3:** Implement appropriate security protocols for the Server.

At a minimum, HTTPS protocols must be used for the implementation using the right certificate.

**Step 4:** Implement the Adaptive Questionnaire Administration following the guidance provided at 
[Adaptive Question Administration](http://build.fhir.org/ig/HL7/sdc/adaptive.html) using the [Questionnaire Next Question operation](http://build.fhir.org/ig/HL7/sdc/Questionnaire-next-question.html).

**Step 5:** Convert results from Adaptive Questionnaire Administration to Questionnaire and QuestionnaireResponse for access using APIs outlined above.

#### External Assessment Center

​The capabilities and requirements that need to be implemented by the External Assessment Center to support PRO requirements are outlined at [CapabilityStatements](capstatements.html)

Developers can follow these steps to implement the above capabilities.

**Step 1:** Implement a FHIR Server. (Choose Release 4)

There are many open source FHIR Servers that are available to be downloaded and used instead of starting from scratch. These can be found at [FHIR Open Source Implementations](http://wiki.hl7.org/index.php?title=Open_Source_FHIR_implementations).

Publish the FHIR Server Capability Statement for the Server.

**Step 2a:** Implement the APIs for Questionnaires

* POST API : Support creation of PRO Measure using Questionnaire Resource and store it internally for administrations. 

`POST [BaseURL]/Questionnaire/` - Submit payload (body) of Questionnaire in JSON format.


* GET API : Will be used to download a specific Questionnaire by authorized systems and personnel.

`GET [BaseURL]/Questionnaire/1234` - Receive a payload (body) of Questionnaire in JSON format.

`GET [BaseURL]/Questionnaire/?_summary=true` - Receive all Questionnaires present in the system in summary format.


**Step 2b:** Implement the APIs for QuestionnaireResponse

* GET API : Will be used to download a specific QuestionnaireResponse (PRO Responses) by authorized systems and personnel.

`GET [BaseURL]/QuestionnaireResponse/1234` - Receive a payload (body) of QuestionnaireResponse in JSON format.

**Step 3:** Implement appropriate security protocols for the Server.

At a minimum, HTTPS protocols must be used for the implementation using the right certificate.

**Step 4:** Implement the Adaptive Questionnaire Administration following the guidance provided at 
[Adaptive Question Administration](http://build.fhir.org/ig/HL7/sdc/adaptive.html) using the [Questionnaire Next Question operation](http://build.fhir.org/ig/HL7/sdc/Questionnaire-next-question.html).



