---
title: Theat Hunting Loop
date: 2025-06-22
draft: false
tags:
  - ThreatHunting
  - Cybersecurity
---
> "a **threat** is any circumstance or event that has the potential to exploit vulnerabilities."

\- Definition of Threat in *Practical Threat Intelligence and Data-Driven Threat Hunting*. By *Valentina Costa-Gazcón*.

---
# The Threat Hunting Loop.

The Threat Hunting Loop is a methodology that aids one of the main problems of Threat Hunting. Organizations often require a methodology for Threat Hunting and Threat Hunters need tools that facilitate Theat Hunting.

The **iterative process** of Threat Hunting Loop:

{{< mermaid >}}
graph TD

1["Create Hypotheses"] --> 2["Investigate via tools and techniques"] --> 3["Uncover new patters and TTPs"] --> 4["Enrich analytics"] --> 1

class 1,2,3,4 internal-link;
{{< /mermaid >}}
---
# Hypothesis Creation.

1. The most important part of a Threat Hunting is to define the proper questions to assess the Threat Hunting process and approach.

**Threat Hunters** might ask questions like:
	*"How could the attacker infiltrate into the network?"*

## Types of hypotheses.

| Type                              | Definition                                                                                                                                 | Approach                                                                                                                                                                                                                                                                                                                                                                                       | Example                                                                                                                                                                                                                                                                              |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Intelligence-Driven Hypotheses.   | Based on Tactics, Techniques and Procedures (TTPs) with further context provided by assessments of the geopolitical and threat landscapes. | Relying only on Indicators of Compromise can over burden your findings with low quality matches. Instead, use IOCs for quick win if lacking of time, then move up to Pyramid of Pain to understand. TTPs                                                                                                                                                                                       | *"I know that (group) is a high priority threat for my organization because of our location and industry. If this threat actor is present in our network, we should be able to detect evidence of multiple techniques used by the group, consistent with their known attack paths."* |
| Situational Awareness Hypotheses. | Based on the understanding of the environment and identifying when it changes in some significant way.                                     | Defenders can develop hypotheses about adversary activities that might occur in their environments. They also require to focus on their most important assets by using Crown Jewel Analysis (CJA) and use automation (*like dashboards*) to keep up with rapidly changing infrastructure, applications and vulnerabilities.                                                                    | *"I will limit my search to just high-value targets (crown jewels), such as the domain admin accounts. If attackers abuse domain admin credentials in our network, we should be able to detect outliers like a spike in Domain Admin account logons."*                               |
| Domain Expertise Hypotheses.      | Based on the hunter's unique set of experiences and skills. However this approaching can have a side effect, bias.                         | Domain expertise can be viewed as both CTI and Situational awareness in a historical context, but experience often comes with bias. Hunters need to be aware of their cognitive biases to ensure good decisions are made. They can use Analysis of Competing Hypotheses (ACH) or The Diamond Model of Intrusion Analysis to draw accurate conclusions and structuring data to overcome biases. |                                                                                                                                                                                                                                                                                      |

---
# Investigating Via Tools and Techniques.

 The next step of **Create Hypotheses**. Here we test our hypothesis.

Threat Hunters must ask questions before diving into investigations. These questions ensure the hypothesis is strong or able to be investigated.

- Which data sources we need?
- Do we have the required data visibility?
- Do we have the required historical data?

{{< mermaid >}}
graph TD

A((Hypothesis Testing)) --> B[Which data sources do we need?]
B --> C[Firewall logs, Endpoint logs, Network Traffic, etc.]

A --> BB[Do we have required data visibility?]
BB --> CC[SIEM, XDR, IDS, NIDS]

A --> BBB[Do we have historical data?]
BBB --> CCC[Past events, incidents, configurations]

C --> D[Start hunting]
CC --> D
CCC --> D
{{< /mermaid >}}

## What can you do with your findings?

- Inform Incident Response Team to investigate.
- Uncover new patters and TTPs to Detection Engineers.

---
# Uncovering New Patterns and TTPs.

1. The process of reporting your threat hunting findings.

Your hypotheses maybe could or **could not lead to any results**, or you can find new IOCs

{{< mermaid >}}
graph LR

A((Hypothesis)) --> B{Hunt}
B -- Success --> C[Document findings]
C --> End[Plan future hunt]

B -- Fail --> CC[Reflect on failure]
CC --> D["Inefficient tools, data gaps, or wrong queries"]
D --> End

End --> A
{{< /mermaid >}}

Failed Threat Huntings may reveal non-malicious but risky configurations or behaviors such as:
- Suspicious IOCs (*files, IP Adresses, Hashes*).
- Misconfigured systems.
- Unpatched software.
- Blind spots in data or logs, known as ***Logging gaps***.

---
# Inform and Enrich Analytics.

1. The process where you transform your relevant findings into insights.

The **final process**, where you convert your conclusions into recommendations and immediate actions to improve the security posture.

You can either save your results and schedule them to quickly repeat the hunting in the future to find more IOCs or tactics related.

| Turn your results into.                           |
| ------------------------------------------------- |
| Analytics, such as Sigma or Yara rules.           |
| Scheduled tasks to repeat huntings in the future. |

---
*By José Reyes - CTI (Coffee, Tails and Insights). 2025*
