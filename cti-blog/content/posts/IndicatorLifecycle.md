---
title: The Indicator Lifecycle
date: 2025-06-22
draft: false
tags:
  - ThreatIntelligence
  - Cybersecurity
---
> An indicator is any piece of information that describes an intrusion.

\- Definition of an Indicator in *Visual Threat Intelligence: An Illustrated Guide For Threat Researchers*. By *Thomas Roccia*..

# The Indicator Lifecycle.

1. The indicator Lifecycle highlights the importance of analyzing attacks and tracking an indicator's derivation from its predecessors.

Types of ***Indicators***:

| Type           | Definition                                                                                                          | Example                                    |
| -------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| **Atomic**     | Simple and indivisible indicators with context-specific meaning.                                                    | Malicious IP addresses, Malicious domains. |
| **Computed**   | Indicators derived from data involved in an incident.                                                               | Hashes, Malware.                           |
| **Behavioral** | Collections of ***atomic*** and ***computed*** indicators, Often characterized by quantity and combinatorial logic. | Tactics, Techniques and Procedures (TTPs)  |

The **Indicator Lifecycle** process:

{{< mermaid >}}
graph LR

0[Reports] --> 1((Revelation)) -- Leverage --> 2((Maturation)) -- Discover --> 3((Utilization)) -- Analyze --> 1

{{< /mermaid >}}

1. Analysts **uncover** indicators through analysis.
2. Analysts **optimize** usage, updating sensors, improving detection tools.
3. The indicator's potential is realized when it can be used to detect hostile activity.

## ♟ Relevant example.

A team of Malware Analysts can:
- Analyze (*Revelation*) a malware sample to obtain ***atomic*** indicators.
- Update (*Maturation*) their detection systems with the obtained indicators.
- Monitor (*Utilization*) network traffic using the redefined detection systems, identifying infection attempts made by the same malware.

---
*[Intelligence-Driven Computer Network Defense Informed by Analysis of Adversary Campaigns and Intrusion Kill Chains](https://www.lockheedmartin.com/content/dam/lockheed-martin/rms/documents/cyber/LM-White-Paper-Intel-Driven-Defense.pdf) paper. By Lockheed Martin*
