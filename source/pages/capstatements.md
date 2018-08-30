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

The conformance requirements in this section are for actors supporting the Basic Questionnaire administration.

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

The PROM Instrument and Meta data Repository SHALL implement the profile specific interactions as specified in the table below.

---
**Implementation Note**
The way to read the table is as follows. 
For example, the first row indicates that, 
The PROM Instrument and Metadata Repository SHALL support the CREATE, READ, SEARCH operations, SHOULD support the vREAD and HISTORY operations for the SDC Questionnaire profile.

--- 


| Profile Name   | create | read | search (type level) | vread |  history (instance level) |
|:---------------|-------:|-----:|--------------------:|------:|--------------------------:|
|[SDC Questionnaire](http://build.fhir.org/ig/HL7/sdc/sdc-questionnaire.html)|SHALL|SHALL|SHALL|SHOULD|SHOULD|


<br />
