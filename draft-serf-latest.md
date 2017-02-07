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

Security automation requires input of high refinement and high confidence to base corresponding security decisions on. Vital tasks that depend on these refined security events include, integrity of network separation (network slicing), traffic analysis, vulnerability assessment, configuration drift, or malfunction that results in degraded availability or integrity of data. Creating security events of high refinement from the overwhelming amount of (security) events of low refinement is the objective of the solution proposed in this document. This document defines and illustrate five core elements that are required to facilitate a refinement process conducts aggregation, correlation and analysis of event streams with machine learning and AI procedures in a distributed mash of virtual (and sometimes hardware-bound) functions:

* an information sharing architecture that is feasible in the thing-2-thing scope, including a pub/sub approach virtual functions that are bundled in SERF components can exchange information with
* an information model that defines the basic set of information elements that provides the features for machine learning functions and AI procedures to produce output of higher refinement that supports
goals in security automation
* a concise data format for events that can be interpreted and processed by every SERF component that consumes (subscribed to) corresponding types of information (topics)
* alternative architecture implementation based on CoAP and CoMI CoAP pub/sub interaction models and SSLS peer-2-peer topics that are brokered via a corresponding resource directory
* integration of content authorization in existing and to be developed building-blocks that compose a SERF domain leveraging solutions developed in the ACE work group

The resulting architecture provides the capability to bundle machine-learning and AI procedures in SERF components that compose virtual functions. SERF components can be migrated and spawned to support dynamically changes in the requirements of processing capabilities to scale with the amount of security events that can spike in cases of malicious acts, such as DDoS or massive system failures. SERF components are able to attest their integrity using traditional remote attestation and emerging attestation procedures (such as TUDA). Heterogeneous sources of security events, such as proprietary anomaly detection components, netflow statistics, automobile ECU, actuators and sensors in ICS, or constrained-node networks in the thing-2-thing scope.

--- middle

# Introduction

The Introduction goes here

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
