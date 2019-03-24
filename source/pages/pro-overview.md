---
title: PRO Overview
layout: default
active: overview
---


<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}


<!-- end TOC -->



###  Background

A patient’s perspective is critical part of the healthcare eco-system. It can inform decisions regarding prevention, diagnosis, treatment and long-term care. Patients have the ability to give insight on their health that an observer or technology cannot provide. In scenarios where quality of life plays an essential role in treatment, Patient Reported Outcomes (PROs) and Patient Reported Outcome Measure(s) (PROM) are becoming more prevalent. PROs and PROMs can be used to inform the clinical management of individuals, shared decision-making, patient self-management, care planning, goal setting and attainment, and patient-centered outcomes research. The United States Food and Drug Administration (FDA) defines PROs as “any report of the status of a patient’s health condition that comes directly from the patient, without interpretation of the patient’s response by a clinician or anyone else. The outcome can be measured in absolute terms (e.g., severity of a symptom, sign, or state of a disease) or as a change from a previous measure”. PROMs are defined as validated questionnaires or short forms that can eventually turn symptoms into a numerical score and hence measure PROs. While there is promise in the clinical use of PROs and PROMs, health systems have been slow to utilize PRO data due to clinical work flow related operational barriers, technology barriers preventing use of electronic PROs and inclusion of the PRO data in electronic health records (EHRs). Currently some EHRs are able to capture PRO data, including the use of the National Institutes of Health (NIH)-funded Patient Reported Outcomes Measurement Information System (PROMIS) instruments, however this information is not commonly collected at the point of care and is not shared with researchers widely. As a result there is a need to use standards such as HL7 FHIR to capture and exchange PRO data. The abstract model and capabilities required for a PRO eco-system is outlined in the next few sections.


###  PRO Measure (PROM) Life Cycle

Figure 1 below shows a typical PROM life cycle starting with the PROM definition and ending with PROM usage. The next few sub-sections define the various life cycle phases.

{% include img.html img="prom-life-cycle.png" caption="Figure 1: PRO Measure Life Cycle " %}


**PROM Definition** PROM definition phase involves the activities of identifying the relevant research for creation of a PROM, defining the purpose of the PROM, the target audience of the PROM, conditions to consider prior to administering the PROM, collection of PROM data, usage of the collected PROM data and its intended effectiveness. This activity is typically performed by researchers, clinical subject matter experts, provider organizations, patient advocates among others.

**PROM Administration Planning** PROM administration planning entails many decisions that are made by a provider or organization prior to administering a PROM to a patient. These decisions include

* Identifying and selection of an appropriate PROM based on its benefit to various stakeholders which include patients, providers, researchers among others.
* Customizing the PROM for organizational needs and for compliance purposes (For example, a primary care provider organization may eliminate some of the questions in a PROM if they are not applicable to the setting or the patient’s condition)
* Identifying the Patient population for which the PROM needs to be administered
* Identifying “When” the PROM is administered (For example administering a PROM during an encounter, prior to a surgery, post surgery, every 2 months after surgery for a year)
* Type of training and education needed for the providers, caregivers and others involved in the PROM activities
* Type of training and education needed for the patients
* Identifying “How” the PROM will be administered (For example some organizations may use paper, some may use a stand-alone system, some may use EHRs, some may use 3rd party technology such as Assessment Center API)
* Identifying “Who” will receive the PRO data from the PROM (For example, clinicians may be provided the PRO data prior to the encounter, researchers may be provided the PRO data for secondary uses)
* Identifying “How” the PRO data is made available to the various stakeholders.

**PROM Creation and Publishing** PROM creation involves the activity of actually creating the PROM instrument which will be administered based on the PROM administration planning outlined earlier. Once the PROM is created it needs to be published to be accessible to the various work flows within the organization. An organization that chooses to use paper to administer PROMs will create the PROM and publish the PROM using paper copies that can be administered. Organizations may choose to publish an electronic version of the PROM in a repository from where a stand-alone health IT system may access the PROM for administration. Organizations may ask their technology vendors to incorporate the PROM into their health IT system so that it can be administered using existing interfaces.

**PROM Administration** PROM administration involves the activity of actually making the PROM available to the patient at the appropriate time, on the desired platform and at the desired location based on the PROM administration planning outlined earlier. Effective PROM administration ensures good response rates and quality data from the patient. An important outcome of administration is the fact that PROM responses depends on mode of administration. (For example, administering the same PROM instrument in a phone call is not considered comparable to self-administration in an office setting.)

**PROM Response Collection** PROM response collection involves the activity of capturing responses from the patient, storing the response data appropriately with provenance and integrity and integrating the data with the rest of the patient’s data within the organization.

**PROM Response Scoring** PROM usage is most effective when the collected data is turned into a numerical score that can be used by providers and researchers. This activity is called scoring. Scoring of a PROM can vary based on the PROM itself and the organization using the PROM. The scores for each PROM administered is a critical part of the PRO data collection before its intended usage. The representation of the PRO scores and making these scores available in a standardized manner will help improve the overall usage of PROs. For the purposes of standardization through the PRO FHIR IG, only the representation of scores are being standardized while the actual scoring algorithms themselves are out of scope. The algorithms are not considered for standardization because of the variations and proprietary nature of the algorithms and the IP is typically owned by the designers of the instrument and the algorithm. Hence in the above diagram only part of the PRO Response Scoring is covered with the red dotted line indicating that only part of the activity (Score representation) is being standardized while the algorithms are left out of the standardization activities. 

**PROM Response & Score Usage** PROM Response & Score usage involves the activity where the providers and researchers use the PRO data collected, the scores that were created as part of their PROM administration activities. PRO usage may also suggest improvements to the PROM over time based on the data collected and this is shown as feedback in the PROM life cycle diagram above. Research use of PROM Responses and Scores may be different from use for clinical decision making, where a provider may develop interpretations that are calibrated to his practice vs. calibrated to a body of evidence. In order for effective usage of

**PROM Life Cycle Activities for Standardization** As described earlier the PROM life cycle contains many different phases many of which are dependent on activities that vary based on the organization intending to administer, collect and use PRO data. While PRO usage could be improved in the real-world by standardizing all life cycle activities described above, we have to account for organizational differences, allow the ability for vendors to innovate and provide value added services around PROs. Hence the following areas identified in the PROM life cycle are considered for standardization as a first step to improving the usage of PROs in the real-world

* PROM creation and publishing
* PROM administration within EHRs and outside EHRs
* PROM Response collection and storage
* PROM scoring representation


###  Abstract Model, Actors and Definitions

This section outlines the abstract model which is used to identify the specific actors and interactions that are in-scope for the PRO FHIR IG. There are two different abstract models to consider and are outlined below

* __Abstract model for administering fixed format (Basic) questionnaires__: In this model the all the items of the questionnaires are administered to the patient unless some of the items have to be skipped based on skip logic or other simple criteria. For example, A Questionnaire might skip a question on pregnancy if the person is a male.
	 	
* __Abstract model for administering Item Response Theory (IRT) based questionnaires__: This is also known as Computerized Adaptive Testing (CAT), or administration of Adaptive Questionnaires. In this case a set of questions typically 4 to 12 are administered from a question bank containing a large number of questions. The selected questions are based on Item Response Theory algorithms which look at the answers provided and select the next question based on IRT algorithms. The selection of questions will help in obtaining responses for a few questions and finish the administration. These small set of questions still provide the necessary confidence and scores required to interpret the data appropriately as if the whole questionnaire was administered. 
	
	
#### Abstract Model for administering Basic (fixed format) Questionnaires

Figure 2 below shows the abstract model, actors and the data flows for the administration of Basic Questionnaires. The actors and their interactions are outlined in the next few paragraphs.

 {% include img.html img="pro-abstract-model-basic.png" caption="Figure 2: Abstract Model for Basic Questionnaires " %}
 
**PROM Instrument and Meta data Repository**: The PROM Instrument and Meta data Repository is a system that is capable of storing the PROMs along with its meta data. In addition to storing the PROMs, the repository provides APIs to health IT systems to retrieve PROMs for administration. The repository may be hosted by an organization (e.g. PCORnet CDRN such as REACHnet, pSCANNER) individually or can be hosted centrally by a federal agency (e.g. NIH) or a network such as Common Well or an independent organization providing PRO services (e.g. Northwestern).

**EHR or Care Delivery Health IT System**: In the context of PRO work flows, EHR or Care Delivery Health IT Systems are used by providers to deliver care and can capture and store the health information about the patient. These EHR or Care Delivery systems can be used to administer PROs to patient as part of routine care. These EHRs or Care Delivery systems will render the PRO instrument natively, capture the PRO data and then persist the captured PRO data within the system.

**External PRO Administration System**: In the context of PRO work flows, External PRO Administration Systems are those which are considered to be independent and external to the EHR or Care Delivery Health IT system. There are many different variations of these systems. Some examples include independent health IT systems which have no connection to an EHR (e.g. Tablets with PRO modules used to collect PRO data and have their own databases to store the data), a SMART on FHIR App which can be launched from an EHR with the patient context and communicate with the EHR is used to collect and store PRO data. The key aspect of these external PRO systems is the fact that they are outside the clinical care delivery system (i.e. EHR) and hence will need a mechanism to integrate with the EHR for the PRO data to be useful widely.

**Data Flow Descriptions**
As shown in the Figure 2 above, there are multiple ways a PROM can be administered in the real-world. We will examine these different work flows in the next few paragraphs.

__PROM Administration using EHR or Care Delivery Health IT System (Identified as DF1 in Abstract Model)__ All PROM administration activities start with the creation and publishing of the instrument along with the meta data necessary for administration which is shown in Step 1 of the diagram. When the PROM is administered using an EHR or Care Delivery system natively, the PROM is retrieved by the EHR as shown in step 2. (The context of which patient should be administered a PROM is part of the PROM Administration and Planning activity and is not shown as part of the abstract model) Once the PROM is retrieved and rendered the patient will fill out the PROM (the actual user interface may be a tablet or web interface or a patient portal etc.) and the responses are collected and scored as shown in Step 3. The collected PRO data is then made available to Providers, Care givers and Researchers as part of Step 6 and 7. The APIs to be used by providers and researchers to access the PRO data will be specified in the IG , however the required security and privacy controls and user interfaces to be used to access the PRO data are not defined as part of the abstract model.

__PROM Administration using External PRO Administration System (Identified as DF2 in Abstract Model)__ All PROM administration activities start with the creation and publishing of the instrument along with meta data necessary for administration which is shown in Step 1 of the diagram. When a PROM is administered using an External PRO Administration System, the PROM is retrieved as shown in step 2a. (The context of which patient should be administered a PROM is part of the PROM Administration and Planning activity and is not shown as part of the abstract model). Once the PROM is retrieved and rendered the patient will fill out the PROM (the actual user interface may be a tablet or web interface or a mobile app) and the responses are collected and scored as shown in Step 3a. If the collected PRO data is to be persisted in an EHR, then the PRO data will be submitted to the EHR via a message or an API as shown in Step 5. The collected PRO data will be made available to Researchers as part of Step 7. The APIs to be used by providers and researchers to access the PRO data will be specified in the IG , however the required security and privacy controls and user interfaces to be used to access the PRO data are not defined as part of the abstract model.

__PROM Administration using SMART on FHIR App (Identified as DF3 in Abstract Model)__ All PROM administration activities start with the creation and publishing of the instrument along with meta data necessary for administration which is shown in Step 1 of the diagram. When a PROM is administered using an External PRO Administration System which is coupled to an EHR or Care Delivery system such as a SMART on FHIR App, the provider has to launch the SMART on FHIR App with the user context as shown in Step 4. Once the app is launched with the appropriate permissions, the PROM is retrieved as shown in step 2a. (The context of which patient should be administered a PROM is part of the PROM Administration and Planning activity and is not shown as part of the abstract model). Once the PROM is retrieved and rendered the patient will fill out the PROM (the actual user interface may be a tablet or web interface or a mobile app) and the responses are collected and scored as shown in Step 3a. The collected PRO data is then persisted in the EHR, using APIs as shown in Step 5. The collected PRO data will be made available to Providers, Care givers and Researchers as part of Steps 6 and 7. The APIs to be used by providers and researchers to access the PRO data will be specified in the IG , however the required security and privacy controls and user interfaces to be used to access the PRO data are not defined as part of the abstract model.
	

#### Abstract Model for administering IRT based (Adaptive or CAT) Questionnaires

Figure 3 below shows the abstract model, actors and the data flows for the administration of Basic Questionnaires. The actors and their interactions are outlined in the next few paragraphs.

{% include img.html img="pro-abstract-model-adaptive.png" caption="Figure 3: Abstract Model for Adaptive Questionnaires " %}
 
**External Assessment Center**: The External Assessment Center is a system that is capable of administering a questionnaire based on IRT algorithms. The data that is necessary for the administration is only the initial item bank. The External Assessment Center does not need to know about the specific patient identity or any other clinical information. The Assessment Center will use algorithms recommended by the Questionnaire designer to determine how to administer the questionnaire.

**Patient Facing Administration App**: The Patient Facing Administration App is the actual app that is being used to present the questions to the patient. It can be an EHR, a SMART on FHIR App, an Independent PRO Administration App. 


**Data Flow Description for Adaptive Questionnaires Administration**

As shown in Figure 3 above, the Patient Facing Administration App (EHR, Care Delivery System, Independent App or SMART on FHIR App) acts as the client and initiates the administration process. In the first step, the available adaptive questionnaires are discovered and a specific PROM is selected for administration. (Note: this step is optional) The following are the steps that take place in the interaction.
* The administration is initiated with a specific PROM.
* The Assessment Center responds to the start request with a Questionnaire and the first item for administration.
* The Patient Facing Administration App will then display the question to the user and collect the response.
* The Patient Facing Administration App will then send the answer to the Assessment Center and ask for the next question.
* The Assessment Center will use the answer to determine the next question based on the algorithm and respond back with the next question until the assessment is done.
* If the Assessment Center determines that the assessment is done, it will respond with the final results which will contain all the questions that were answered, along with the answers, the individual scores and the overall score.



<!-- {% raw %}>{% include link-list.md %} {% endraw %}-->

{% include link-list.md %}
