---
title: Security Event Refinement Framework
abbrev: SERF
docname: draft-birkholz-serf-latest 
wg:  I2NSF
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
- ins: H. Birkholz
  name: Henk Birkholz
  org: Fraunhofer SIT
  abbrev: Fraunhofer SIT
  email: henk.birkholz@sit.fraunhofer.de
  street: Rheinstrasse 75
  code: '64295'
  city: Darmstadt
  country: Germany
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


normative:
  RFC2119:

informative:

--- abstract 

Millions of low-level events, such as byte counters, triggered filter 
policies, or interaction attempts, are created continuously in a 
multitude of network topologies. Constrained-node networks, such as 
sensor networks, smart meters in LPWAN, or vehicle networks with 
various interconnected layer 2 topologies, exhibit domain-specific 
behaviors that can be considered to be compliant or - in contrast - as 
potential anomalies in regard to declarative guidance. In order to 
facilitate an automated assessment of the behavior of interconnected 
components that constitute, for example, service chains or downstream 
work-flows, available low-level events have to be brought into a larger 
semantic context by refining them into a lower volume of security 
events with a higher grade of expressiveness or significance.

This work describes an architecture, its corresponding components, 
interfaces and interaction model, as well as a security event 
information model to facilitate  a refinement framework to process 
event streams via aggregation, correlation and machine-learning 
methods.  The components defined are virtual encapsulations of 
corresponding machine-learning and AI function that require certain 
features derived from the event data that is made available by 
low-level event streams. 

--- middle

# Introduction

In the domain of networks, security automation requires input of high 
refinement and high confidence to base corresponding security decisions 
on. Vital tasks that depend on these refined security events include 
the verification of compliance in regard to the integrity of network 
separation (network slicing) or content of PDU flows and the assessment 
of the impact of identified vulnerabilities, configuration drift, or 
malfunctions that result in degraded availability or integrity of data. 

In the domain of autonomous services, security automation supports the 
decision making in the domains of spacial cognition, advanced planning, 
adaptive behavior or game theory based decision making. Creating 
relevant (security) events of high refinement from an staggering amount 
of raw events of low refinement is the objective of the solution 
proposed in this document. This document defines and illustrates five 
core elements that are required to facilitate a refinement process that 
conducts aggregation, correlation and analysis of event streams with 
machine learning and AI procedures in a distributed mash of virtual 
(and sometimes also hardware-bound) functions:

* an information sharing architecture that is feasible to be applied in 
the thing-2-thing scope, including a pub/sub approach virtual functions 
that are bundled in SERF components can exchange information with
* an information model that defines the basic set of information 
elements providing the features required for machine-learning functions 
and AI procedures to create output of higher refinement in order to 
satisfy common security requirements via automation procedures
* a concise data model for security events that can be interpreted and 
processed by SERF components to fuel corresponding machine-learning 
functions and AI procedures
* two alternative architecture designs based on CoAP pub/sub 
interaction model and based on SSLS peer-2-peer topics that are 
brokered via a resource directory
* integration of content authorization into existing and emerging 
building-blocks that compose a SERF domain, leveraging solutions 
developed in the ACE work group

The architectures defined in this document provide the capability to 
bundle machine-learning and AI procedures in SERF components in the 
form of virtual functions. Hence, SERF components can be migrated, 
spawned and discarded to support dynamic changes in regard to 
processing capability and scalability. The dynamic orchestration of the 
virtual functions that compose a SERF domain address the resilience and 
scalability required to mitigate or remediate malicious acts, such as 
DDoS attacks in production systems, targeted attacks at the SERF domain 
itself, or massive system failures. SERF components are able to attest 
their integrity using traditional remote attestation and emerging 
attestation procedures (such as TUDA). Heterogeneous sources of events 
are addressed by SERF, such as proprietary anomaly detection 
components, netflow statistics, automobile ECU, actuators and sensors 
in ICS, or constrained-node networks in the thing-2-thing scope.

## Requirements notation

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT",
"SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and
"OPTIONAL" in this document are to be interpreted as described in RFC
2119, BCP 14 {{RFC2119}}.

# General Architechture

Every SERF component is a bundle of virtual functions with interfaces 
to the management, control and data plane.

## SERF components & functions

SERF components are bundles of virtual functions that can be chained, 
composed in a service graph, migrated or orchestrated, and therefore 
dynamically instantiated, modified or discarded.

SERF components contain SERF functions. A SERF function typically is a 
specifc software (agent) that processes events or collects and provides 
corresponding event data continuously, scheduled or on an ad-hoc basis. 
The interconnected work-flows (service chains) SERF components compose 
constitute a SERF domain. SERF components can be geographically 
grouped, spawned into distributed cloud infrastructure or use the 
excess processing capabilities of existing infrastructure as part of a 
fog-computing domain. SERF components that emit raw events to a SERF 
domain typically reside on endpoints, such as notebooks, vehicle ECU, 
IoT devices, or ICS actuators. The majority of SERF functions support 
the aggregation, correlation, analysis, assertion and assessment of 
events. Each SERF component supports the goal of event refinement in 
one way or another. The output of a SERF domain are events - although 
it could be argued that the corresponding events can be of such high 
refinement that they are analogous to statements (as produced by a SACM 
domain) or even reports (as produces by a MILE domain).

Larger picture orchestration, such as load balancing, utilization based 
instantiation and requirement-based migration of functions (which 
requires the resolution of discrepancy between contradicting 
requirements via appropriate machine-learning and AI functions) is 
conducted by a specialized mesh of SERF orchestrator components.

### Machine-Learning & AI procedures

The heart of very SERF component are the modular machine-learning and 
AI procedures that contributes to the event refinement framework. Even 
the simplest aggregation procedure can benefit from learning a standard 
pattern and alerting deviations from that pattern. Most desirable for 
SERF component modules are un-supervised machine-learning procedures, 
but semi-supervised or even supervised learning has to be applied if 
unsupervised-learning results in a too high amount of false positives. 
A chaining of unsupervised machine-learning function and basic pattern 
recognition procedures, such as text-distance analysis, markov-models, 
or dynamic time warping can support the semi-supervised learning 
methods and in the end result in a SERF domain that does not require 
supervision, in the end.

## Management Plane functions

Imperative and declarative guidance is transported via the management 
plane. Short term loss of availability of the management plane does not 
impact the functionality of a SERF domain. Components retain their 
(potentially dynamic) configuration that is the basis for orchestration 
capabilities on the control plane and the corresponding refinement 
work-flow on the data plane.

Examples include:

* Configuration of the functions incorporated in a SERF component

* Monitoring of resource load, availability, and other indicators 
critical to a congestion-less event refinement work-flow

* Detection of configuration drift via declarative guidance and 
remediation of corresponding configuration that is in conflict with 
declarative guidance.

## Control Plane Functions

A work-flow of event refinement is orchestrated via control plane 
functions. A significant portion of control plane functions is 
facilitated by each SERF component itself. Examples include:

* propagation of individual capabilities (based on incorporated 
functions) and corresponding imperative guidance regarding input and 
output of interfaces provided by a SERF components via registration and 
discovery function

* registration, subscription and publication functions, also 
peer-2-peer negotiation of communication channels with specific 
interaction and data model (e.g. IPFIX, NETMOD)

* monitoring of SERF component specific event volume, trending analysis 
and dynamical adaption of function resources of the SERF components 
itself and publication of corresponding control events and features to 
support the orchestration of the entire SERF domain via a redundant 
mash of SERFO (SERF orchestration components).

* requesting and updating incorporated function modules that extend or 
change the interfaces of a SERF component via changing, adapting or 
updating corresponding refinement functions (e.g. machine-learning 
functions or AI procedures). Effectively, the need to modify a function 
set of a SERF component is detected and orchestrated on the control 
plane. The actual update is conducted via the management plane in the 
context of imperative guidance (which new function has to be installed 
in which way) and declarative guidance (which function should be 
replaced by which function).

## Data Plane Functions

On the data plane, the actual function chaining is conducted. The 
output of each function has to be processable in an automatic fashion 
by the next function in the chain. While the term "chain" implies a 
linear sequence of single function, in fact a directed graph that might 
even include refinement loops with termination conditions can be 
composed in a SERF domain. Hence, a service graph with rather complex 
event impressment streams can be the result of data plane event flow. 
The standard payload of the data plane are (security) events. The 
structure of data plane function typically adheres to a hierarchical 
(tree- or taxonomy-like) composition. This is only the typical default 
in general setups. In none-cricle-free graphs with multiple condition 
based branching and various work-flow layers can be the result of a 
rather sophisticated event refinement requirements a data plane 
work-flow is based upon.

Typical data plane function include:

* machine-learning algorithms, such as (hidden) markov-models, 
neural-networks, time-line-analysis, CEP sliding window analysis, 
text-distance-analysis and others.

* interface that define the required data model for data in motion, 
optionally semantic properties (e.g. in the form of tags, annotations 
or even ontological structured data), interface that define the output 
data model for data in motion

* specific data plane operation that can generate data, access and 
modify SERF components that provide existing (potentially historical, 
e.g. a event log, or complementary, e.g. a vulnerability data base) 
data, request data from SERF components or standard pools of data (e.g. 
an LDAP directory).

* event format constructor, parser and validators

* resolving discrepancies between contradicting informations of events 
of any refinement level.

 Larger picture orchestration, such as load balancing, utilization 
 based instantiation and requirement-based migration of functions 
 (which requires the resolution of discrepancy between contradicting 
 requirements via appropriate machine-learning and AI functions). 
 (typically called "downstream", although feedback loops can create 
 events that are inserted again of an event processesment level of 
 lower refinement or result in specifically tailored monitoring task or 
 the instantiation of more specific SERF components to facilitate a 
 more unique (situation-depended/aware) refinement work-flow.

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
