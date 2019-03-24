---
title: CapabilityStatements defined for this Guide
layout: default
active: capstatements
---
<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}

<!-- end TOC -->

The section outlines conformance requirements for each of the PRO actors which includes the specific profiles, operations, security mechanisms and search parameters that need to be supported.

### Conformance Requirements for Actors supporting Basic Questionnaire (Fixed Formats) Administration

This section outlines conformance requirements for actors supporting the Basic Questionnaire administration.

#### PROM Instrument and Metadata Repository Conformance Requirements

The following are the conformance requirements for the PROM Instrument and Meta data Repository.

##### Behavior and Formats

The PROM Instrument and Meta data Repository **SHALL**: 
* Implement the RESTful behavior according to the [FHIR HTTP Specification](http://hl7.org/fhir/http.html).
* Support **json** resource formats for all PRO interactions.
* Declare a CapabilityStatement identifying the list of profiles, operations and search parameters supported.

---
**Implementation Note**
The FHIR HTTP specification outlines specific requirements on how to deal with successful operations, invalid parameters, unauthorized request, insufficient scopes, unknown resources etc.

---
##### Profiles and Interactions

The PROM Instrument and Meta data Repository needs to implement the profile specific interactions as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The PROM Instrument and Metadata Repository **SHALL** support the CREATE, READ, SEARCH operations, SHOULD support the vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 

| Profile Name          | create     | read       | search (type level)      | vread          |  history (instance level) |
|:----------------------|-----------:|-----------:|-------------------------:|---------------:|--------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|

##### Search and Other Parameters

The PROM Instrument and Meta data Repository needs to implement the search parameters as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The PROM Instrument and Metadata Repository **SHALL** support _id, identifier, combination of identifier & version search parameters and _summary search result parameters for the SDC Questionnaire profile.

--- 

| Profile Name          | SEARCH and Search Result parameters and combinations     |   
|:----------------------|---------------------------------------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|_id (SHALL)|
||identifier (SHALL)|
||identifier & version (SHALL)|
||_summary (SHALL)|


##### Security Requirements

The PROM Instrument and Meta data Repository **SHALL** support the Communication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#http)

The PROM Instrument and Meta data Repository **SHALL** support the Authenitication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#authentication)

The PROM Instrument and Meta data Repository **SHOULD** support other security recommendations outlined in FHIR Security as appropriate.

#### EHR or Care Delivery Health IT System Conformance Requirements

The following are the conformance requirements for the EHR or Care Delivery Health IT System.

##### Behavior and Formats

The EHR or Care Delivery Health IT System **SHALL**: 
* Implement the RESTful behavior according to the [FHIR HTTP Specification](http://hl7.org/fhir/http.html).
* Support **json** resource formats for all PRO interactions.
* Declare a CapabilityStatement identifying the list of profiles, operations and search parameters supported.

---
**Implementation Note**
The FHIR HTTP specification outlines specific requirements on how to deal with successful operations, invalid parameters, unauthorized request, insufficient scopes, unknown resources etc.

---
##### Profiles and Interactions

The EHR or Care Delivery Health IT System needs to implement the profile specific interactions as specified table below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The EHR or Care Delivery Health IT System **SHALL** support the CREATE, READ, SEARCH operations, SHOULD support the vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 

| Profile/Resource Name          | create     | read       | search (type level)      | vread          |  history (instance level) |
|:----------------------|-----------:|-----------:|-------------------------:|---------------:|--------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[US Core Results / Observation - Note1](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|MAY|MAY|MAY|MAY|MAY|
|[ServiceRequest - Note2](http://build.fhir.org/servicerequest.html)|MAY|MAY|MAY|MAY|MAY|

---
**Note1**
US Core Results Observation profile is optional and only needs to be supported if the answers to the questions in the QuestionnaireResponse are translated to Observations.

**Note2**
Some sites are planning to use ServiceRequest to capture the ordering of a PROM instrument to a specific patient. 

**Feedback Required**
We are requesting feedback from pilot sites and challenge participants on whether the use of US CoreResults and/or ServiceRequest should be mandated or left optional.

--- 

##### Search and Other Parameters

The EHR or Care Delivery Health IT System needs to implement the search parameters as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The EHR or Care Delivery Health IT System **SHALL** support _id, identifier, combination of identifier & version search parameters and _summary search result parameters for the SDC Questionnaire profile.

--- 

| Profile Name          | SEARCH and Search Result parameters and combinations     |   
|:----------------------|---------------------------------------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|_id (SHALL)|
||identifier (SHALL)|
||identifier & version (SHALL)|
||_summary (SHALL)|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|_id (SHALL)|
||identifier (SHALL)|
||patient (SHALL)|
||questionnaire (SHALL)|
||author (SHALL)|
||authored (SHALL)|
|[US Core Results - Observation](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|patient (SHALL)|
||patient & category (SHALL)|
||patient & category & date (SHALL)|
||patient & relatedTarget referring to QuestionnaireResponse (SHOULD)|
|[ServiceRequest - Note2](http://build.fhir.org/servicerequest.html))|patient (SHALL)|
||patient & intent (SHOULD)|


##### Security Requirements

The EHR or Care Delivery Health IT System **SHALL** support the Communication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#http)

The EHR or Care Delivery Health IT System **SHALL** support the Authentication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#authentication)

The EHR or Care Delivery Health IT System **SHOULD** support other security recommendations outlined in FHIR Security as appropriate.

##### SMART on FHIR App Interactions 

For EHR or Care Delivery Health IT Systems supporting the collection of PRO data using External PRO Administration System by passing patient context information the following requirements apply. 

The EHR or Care Delivery Health IT System **SHALL** support the **EHR Launch Sequence** from the [SMART on FHIR App Authorization guide](http://docs.smarthealthit.org/authorization) applicable to the EHR.

The EHR or Care Delivery Health IT System **SHALL** support information retrieval during **EHR Launch Sequence** using tokens and parameters for [US Core profiles](http://hl7.org/fhir/us/core/index.html)

In order to receive collected PRO data, The EHR or Care Delivery Health IT System **SHALL** support the SDC QuestionnnaireResponse profile and interactions outlined earlier in the section.

#### External PRO Administration System Conformance Requirements

The following are the conformance requirements for the External PRO Administration System.

##### Behavior and Formats

The External PRO Administration System **SHALL**: 
* Implement the RESTful behavior according to the [FHIR HTTP Specification](http://hl7.org/fhir/http.html).
* Support **json** resource formats for all PRO interactions.
* Declare a CapabilityStatement identifying the list of profiles, operations and search parameters supported.

---
**Implementation Note**
The FHIR HTTP specification outlines specific requirements on how to deal with successful operations, invalid parameters, unauthorized request, insufficient scopes, unknown resources etc.

---
##### Profiles and Interactions

The External PRO Administration System needs to implement the profile specific interactions as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The External PRO Administration System **SHALL** support the CREATE, READ, SEARCH operations, SHOULD support the vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 

| Profile/Resource Name          | create     | read       | search (type level)      | vread          |  history (instance level) |
|:----------------------|-----------:|-----------:|-------------------------:|---------------:|--------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[US Core Results / Observation - Note1](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|MAY|MAY|MAY|MAY|MAY|
|[ServiceRequest - Note2](http://build.fhir.org/servicerequest.html)|MAY|MAY|MAY|MAY|MAY|

---
**Note1**
US Core Results Observation profile is optional and only needs to be supported if the answers to the questions in the QuestionnaireResponse are translated to Observations.

**Note2**
Some sites are planning to use ServiceRequest to capture the ordering of a PROM instrument to a specific patient. 

**Feedback Required**
We are requesting feedback from pilot sites and challenge participants on whether the use of US CoreResults and/or ServiceRequest should be mandated or left optional.

--- 

##### Search and Other Parameters

The External PRO Administration System needs to implement the search parameters as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The External PRO Administration System **SHALL** support _id, identifier, combination of identifier & version search parameters and _summary search result parameters for the SDC Questionnaire profile.

--- 

| Profile Name          | SEARCH and Search Result parameters and combinations     |   
|:----------------------|---------------------------------------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|_id (SHALL)|
||identifier (SHALL)|
||identifier & version (SHALL)|
||_summary (SHALL)|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|_id (SHALL)|
||identifier (SHALL)|
||patient (SHALL)|
||questionnaire (SHALL)|
||author (SHALL)|
||authored (SHALL)|
|[US Core Results - Observation](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|patient (SHALL)|
||patient & category (SHALL)|
||patient & category & date (SHALL)|
||patient & relatedTarget referring to QuestionnaireResponse (SHOULD)|
|[ServiceRequest - Note2](http://build.fhir.org/servicerequest.html)|patient (SHALL)|
||patient & intent (SHOULD)|


##### Security Requirements

The External PRO Administration System **SHALL** support the Communication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#http)

The External PRO Administration System **SHALL** support the Authentication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#authentication)

The External PRO Administration System **SHOULD** support other security recommendations outlined in FHIR Security as appropriate.

##### SMART on FHIR App Interactions 

For External PRO Administration Systems interacting with EHRs to receive patient and other clinical context data from the EHR the following requirments apply:

The External PRO Administration System **SHALL** support the **EHR Launch Sequence** from the [SMART on FHIR App Authorization guide](http://docs.smarthealthit.org/authorization) as a client.

The External PRO Administration System **SHALL** request information from EHR during **EHR Launch Sequence** using tokens and parameters for [US Core profiles](http://hl7.org/fhir/us/core/index.html) as a client.

In order to store collected PRO data in the EHR, The External PRO Administration System **SHALL** use create interaction for the  SDC QuestionnnaireResponse profile with the EHR as the target system. (In other words the External App will do a POST to the EHR FHIR endpoint to store the QuestionnaireResponse data).

### Conformance Requirements for Actors supporting Adaptive Questionnaires (CAT or IRT based questionnaires) Administration

This section outlines conformance requirements for actors supporting the Adaptive Questionnaire administration.

#### Patient Facing Administration App Conformance Requirements

The following are the conformance requirements for the Patient Facing Administration App.

##### Behavior and Formats

The Patient Facing Administration App **SHALL**: 
* Implement the RESTful behavior according to the [FHIR HTTP Specification](http://hl7.org/fhir/http.html).
* Support **json** resource formats for all PRO interactions.
* Declare a CapabilityStatement identifying the list of profiles, operations and search parameters supported.

---
**Implementation Note**
The FHIR HTTP specification outlines specific requirements on how to deal with successful operations, invalid parameters, unauthorized request, insufficient scopes, unknown resources etc.

---
##### Profiles and Interactions

The Patient Facing Administration App needs to implement the profile specific interactions as specified below.

---
**Implementation Note**
The way to read the table is as follows

The Patient Facing Administration App **SHALL** support the CREATE, READ, SEARCH operations, SHOULD support the vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 

| Profile/Resource Name          | create     | read       | search (type level)      | vread          |  history (instance level) |
|:----------------------|-----------:|-----------:|-------------------------:|---------------:|--------------------------:|
|[SDC Adaptive Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire-adapt.html)|SHALL|MAY|MAY|MAY|MAY|
|[SDC Adaptive QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse-adapt.html)|SHALL|MAY|MAY|MAY|MAY|
|[SDC Questionnaire - Note1](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[SDC QuestionnaireResponse - Note1](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|
|[US Core Results / Observation - Note2](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|MAY|MAY|MAY|MAY|MAY|
|[ServiceRequest - Note2](http://build.fhir.org/servicerequest.html)|MAY|MAY|MAY|MAY|MAY|


---
**Note1** 
The Patient Facing Administration App will use the SDC Adaptive Questionnaire and SDC Adaptive QuestionnaireResponse profile to administer the PRO, but should store the resulting Questionnaire and QuestionnaireResponse from the PRO administration using the same profiles that are used for Basic Questionnaires to ensure consistency. 

**Note2**
US Core Results Observation profile is optional and only needs to be supported if the answers to the questions in the QuestionnaireResponse are translated to Observations.

**Note3**
Some sites are planning to use ServiceRequest to capture the ordering of a PROM instrument to a specific patient. 

**Feedback Required**
We are requesting feedback from pilot sites and challenge participants on whether the use of US CoreResults and/or ServiceRequest should be mandated or left optional.

--- 

##### Adaptive Questionnaire Operations

The Patient Facing Administration App **SHALL** support the [Adaptive Questionnaire Next Question](http://build.fhir.org/ig/HL7/sdc/Questionnaire-next-question.html) operation to facilitate Adaptive Questionnaire administration process using IRT based algorithms.

##### Search and Other Parameters

The Patient Facing Administration App needs to implement the search parameters as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The Patient Facing Administration App **SHALL** support _id, identifier, combination of identifier & version search parameters and _summary search result parameters for the SDC Questionnaire profile.

--- 

| Profile Name          | SEARCH and Search Result parameters and combinations     |   
|:----------------------|---------------------------------------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|_id (SHALL)|
||identifier (SHALL)|
||identifier & version (SHALL)|
||_summary (SHALL)|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|_id (SHALL)|
||identifier (SHALL)|
||patient (SHALL)|
||questionnaire (SHALL)|
||author (SHALL)|
||authored (SHALL)|
|[US Core Results - Observation](http://hl7.org/fhir/us/core/StructureDefinition-us-core-observationresults.html)|patient (SHALL)|
||patient & category (SHALL)|
||patient & category & date (SHALL)|
||patient & relatedTarget referring to QuestionnaireResponse (SHOULD)|
|[ServiceRequest](http://build.fhir.org/servicerequest.html)|patient (SHALL)|
||patient & intent (SHOULD)|


##### Security Requirements

The Patient Facing Administration App System **SHALL** support the Communication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#http)

The Patient Facing Administration App **SHALL** support the Authentication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#authentication)

The Patient Facing Administration App **SHOULD** support other security recommendations outlined in FHIR Security as appropriate.

The Patient Facing Administration App **MAY** have to comply with other security requirements to interact with the External Assessment Center. 

#### External Assessment Center Conformance Requirements

The following are the conformance requirements for the External Assessment Center to interact using the PRO IG.

##### Behavior and Formats

The External Assessment Center **SHALL**: 
* Implement the RESTful behavior according to the [FHIR HTTP Specification](http://hl7.org/fhir/http.html).
* Support **json** resource formats for all PRO interactions.
* Declare a CapabilityStatement identifying the list of profiles, operations and search parameters supported.

---
**Implementation Note**
The FHIR HTTP specification outlines specific requirements on how to deal with successful operations, invalid parameters, unauthorized request, insufficient scopes, unknown resources etc.

---
##### Profiles and Interactions

The External Assessment Center needs to implement the profile specific interactions as specified below.

---
**Implementation Note**
The way to read the table is as follows

The External Assessment Center **SHALL** support the CREATE and READ operations, SHOULD support the SEARCH operations and MAY support vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 

| Profile/Resource Name          | create     | read       | search (type level)      | vread          |  history (instance level) |
|:----------------------|-----------:|-----------:|-------------------------:|---------------:|--------------------------:|
|[SDC Adaptive Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire-adapt.html)|SHALL|MAY|MAY|MAY|MAY|
|[SDC Adaptive QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse-adapt.html)|SHALL|MAY|MAY|MAY|MAY|
|[SDC Questionnaire - Note1](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHOULD|MAY|MAY|
|[SDC QuestionnaireResponse - Note1](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|SHALL|SHALL|MAY|MAY|MAY|

---
**Note1** 
The External Assessment Center will use the SDC Adaptive Questionnaire and SDC Adaptive QuestionnaireResponse profile to administer the PRO, but should provide the resulting Questionnaire and QuestionnaireResponse from the PRO administration using the same profiles that are used for Basic Questionnaires to ensure consistency. 

---

##### Adaptive Questionnaire Operations

The External Assessment Center **SHALL** support the [Adaptive Questionnaire Next Question](http://build.fhir.org/ig/HL7/sdc/Questionnaire-next-question.html) operation to facilitate Adaptive Questionnaire administration process using IRT based algorithms.

##### Search and Other Parameters

The External Assessment Center needs to implement the search parameters as specified below.

---
**Implementation Note**
The way to read the table (for example the first row) is as follows

The External Assessment Center App **SHALL** support _id, identifier, combination of identifier & version search parameters and _summary search result parameters for the SDC Questionnaire profile.

--- 

| Profile Name          | SEARCH and Search Result parameters and combinations     |   
|:----------------------|---------------------------------------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|_id (SHALL)|
||identifier (SHALL)|
||identifier & version (SHALL)|
||_summary (SHALL)|
|[SDC QuestionnaireResponse](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaireresponse.html)|_id (SHALL)|


##### Security Requirements

The External Assessment Center System **SHALL** support the Communication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#http)

The External Assessment Center **SHALL** support the Authentication security mechanisms outlined in [FHIR Security Specification](http://hl7.org/fhir/security.html#authentication)

The External Assessment Center **SHOULD** support other security recommendations outlined in FHIR Security as appropriate.

The External Assessment Center **MAY** outline other security requirements to interact with the Patient Facing Administration App.

---
**Feedback Required**
We require implementers of the PRO IG using an External Assessment Center to provide feedback on whether we should adapt the SMART on FHIR Backend Services specification for the interaction between the Patient Facing Administration App and the External Assessment Center or leave it open as it is currently.

---

 


<br />
