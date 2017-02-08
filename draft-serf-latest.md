---
title: Secruity Event Refinement Framework
abbrev: SERF
docname: draft-serf-latest
wg: TBD
stand_alone: true
ipr: trust200902
area: Security
kw: Internet-Draft
cat: std
pi:
  toc: yes
  sortrefs: yes
  symrefs: yes

author:
- ins: R. Moskowitz
  name: Robert Moskowitz
  org: Huawei
  abbrev: Huawei
  email:  rgm@htt-consult.com
  street: "" 
  code: 48237
  city: Oak Park
  region: MI
  country: USA
- ins: H. Birkholz
  name: Henk Birkholz
  org: Fraunhofer SIT
  abbrev: Fraunhofer SIT
  email: henk.birkholz@sit.fraunhofer.de
  street: Rheinstrasse 75
  code: '64295'
  city: Darmstadt
  country: Germany


normative:
  RFC2119:

informative:

--- abstract 

Millions of low-level events, such as byte counters, triggered filter policies, or interaction attempts, are created continuously in a multitude of network topologies. Constrained-node networks, such as sensor networks, smart meters in LPWAN, or vehicle networks with various interconnected layer 2 topologies, exhibit domain-specific behaviors that can be considered to be compliant or - in contrast - as potential anomalies in regard to declarative guidance. In order to facilitate an automated assessment of the behavior of interconnected components that constitute, for example, service chains or downstream work-flows, available low-level events have to be brought into a larger semantic context by refining them into a lower volume of security events with a higher grade of expressiveness or significance. This work describes an architecture, its corresponding components, interfaces and interaction model, as well as a security event information model to facilitate  a refinement framework to process event streams via aggregation, correlation and machine-learning methods.  The components defined are virtual encapsulations of corresponding machine-learning and AI function that require certain features derived from the event data that is made available by low-level event streams. 

--- middle

# Introduction

Security automation requires input of high refinement and high confidence to base corresponding security decisions on. Vital tasks that depend on these refined security events include the verification of compliance in regard to the integrity of network separation (network slicing) or content of PDU flows and the assessment of the impact of identified vulnerabilities, configuration drift, or malfunctions that result in degraded availability or integrity of data. Creating security events of high refinement from an staggering amount of (security) events of low refinement is the objective of the solution proposed in this document. This document defines and illustrates five core elements that are required to facilitate a refinement process that conducts aggregation, correlation and analysis of event streams with machine learning and AI procedures in a distributed mash of virtual (and sometimes also hardware-bound) functions:

* an information sharing architecture that is feasible to be applied in the thing-2-thing scope, including a pub/sub approach virtual functions that are bundled in SERF components can exchange information with
* an information model that defines the basic set of information elements providing the features required for machine-learning functions and AI procedures to create output of higher refinement in order to satisfy common security requirements via automation procedures
* a concise data model for security events that can be interpreted and processed by SERF components to fuel correpsonding machine-learning functions and AI procedures
* two alternative architecture designs based on CoAP pub/sub interaction model and based on SSLS peer-2-peer topics that are brokered via a resource directory
* integration of content authorization into existing and emerging building-blocks that compose a SERF domain, leveraging solutions developed in the ACE work group

The architectures defined in this document provide the capability to bundle machine-learning and AI procedures in SERF components in the form of virtual functions. Hence, SERF components can be migrated, spawned and discarded to support dynamic changes in regard to processing capability and scalability. The dynamic orchestration of the virtual functions that compose a SERF domain address the resilience and scalability required in the of malicious acts, such as DDoS attacks in production systems, targeted attacks at the SERF domain itself, or massive system failures that requires ad-hoc remediation. SERF components are able to attest their integrity using traditional remote attestation and emerging attestation procedures (such as TUDA). Heterogeneous sources of security events, such as proprietary anomaly detection components, netflow statistics, automobile ECU, actuators and sensors in ICS, or constrained-node networks in the thing-2-thing scope.

## Requirements notation

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in RFC
2119, BCP 14 {{RFC2119}}.

# Section 1

The meat goes here.

The second paragraph is here

This is:

: a defintion

~~~ 

This
is
a
listing

~~~

# Section 2

Some more meat here.

#  IANA considerations

This document will include requests to IANA:

* first item
* second item

#  Security Considerations

There are always some.

#  Acknowledgements

Maybe.

#  Change Log

No changes yet.

--- back
