---
title: Patient Reported Outcomes FHIR Implementation Guide
layout: default
active: home
---


<!-- TOC  the css styling for this is \pages\assets\css\project.css under 'markdown-toc'-->

* Do not remove this line (it will not be displayed)
{:toc}


<!-- end TOC -->



###  Introduction

The Patient Reported Outcomes (PRO) FHIR Implementation Guide (IG) will focus on capturing and exchanging patient reported outcome data electronically using the FHIR standard. The data that is captured will be made available to both providers and authorized researchers. While the PRO FHIR IG can be applied to multiple use cases, the current requirements have been drawn from [PCORnet](https://pcornet.org/) use cases and implementations. The capabilities described as part of the IG are intended to be leveraged to build US data infrastructure for a Learning Health System (LHS).

PRO FHIR IG will leverage the US-Core IG and profiles for the resources that overlap with US-Core. PRO FHIR IG will also leverage the Structured Data Capture (SDC) FHIR IG.

The next section provides a road map for the reader to walk through the implementation guide.

###  Guidance to the readers

The following table will provide a road map to the reader to follow and absorb the content of the implementation guide.

| Topic to Read  | What it Contains and its relationship to PRO IG | Where can I find the content ? |
|:---------------|:------------------------------------------------|-------------------------------:|
| Basic Definitions | The set of definitions applicable to the PRO FHIR IG. (Definition of“Supported or MUST Support”, Usage of Code Bindings in US Core Profiles.).| [US-Core Definitions]({{site.data.fhir.uscoreR4}}index.html)|
| PRO Overview | The artifact provides background on Patient Reported Outcomes, Patient Reported Outcome Measures and other PRO related topics.| [PRO Overview](pro-overview.html)|
| Profiles | The artifact defines the various profiles, extensions and resources that make up the PRO FHIR IG.| [Profiles](profiles.html)|
| Capability Statements | The artifact defines the various capability statements (implementation requirements) for each PRO actor that make up the PRO FHIR IG.| [Capability Statements](capstatements.html)|
| Implementation Guidance | The artifact contains guidance and examples that will help implementers of PRO FHIR IG.| [Implementation Guidance](guidance.html)|




<!-- {% raw %}>{% include link-list.md %} {% endraw %}-->

{% include link-list.md %}
