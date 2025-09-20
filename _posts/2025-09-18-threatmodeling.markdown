---
layout: post
title:  "Threat Modeling Practitioner"
date:   2025-09-18 15:21:57 +0100
permalink: /threat-modeling/
---

## What is Threat Modeling?

Threat modeling is the process of analyzing system representations to highlight concerns about **security** and **privacy**.

* **Threat modeling:** anticipates attacks before they occur
* **Penetration testing:** validates the system by actively trying to exploit vulnerabilities

## Threat Model Analysis – In a Nutshell

1. Apply successful known attacks
2. Identify points in the system attackers might reach
3. Gauge the potential impact
4. Rate the risk for each attack scenario
5. Identify the appropriate defenses

## DICE Model

The 4 stages of threat modeling (DICE):

1. **Diagram** – What are we building?
2. **Identify threats** – What can go wrong?
3. **Control/countermeasures** – What are we going to do about it?
4. **Evaluate** – Did we do a good enough job?

### 1. Diagramming

* Identify **doomsday scenarios**: focus on business impact, who is targeting you, etc.
* **DFD (Data Flow Diagrams):**

    * External entity (rectangle): external user, application, etc.
    * Process (circle): logical activities within the system
    * Data store (two lines): resting place for data (database, file store, …)
    * Data flow (arrow): direction of data movement
    * Trust boundary (red dashed line): different trust zones or levels. These can be prioritized

**Levels of DFDs**:

* Context diagram: high-level overview
* Level 1: single scenario, still high-level
* Level 2: includes subcomponents
* Level 3: very detailed

### 2. Identifying Threats

**Methodology: STRIDE**

| Category               | Explanation                               | Property        |
| ---------------------- |-------------------------------------------| --------------- |
| Spoofing               | Pretending to be someone/something else   | Authentication  |
| Tampering              | Modifying data                            | Integrity       |
| Repudiation            | Denying an action without us having proof | Non-repudiation |
| Information disclosure | Gaining access to unauthorized data       | Confidentiality |
| Denial of Service      | Reducing system availability              | Availability    |
| Elevation of privilege | Gaining higher access rights              | Authorization   |

**Tools for threat identification:**

* **Stride-per-element tables:** STRIDE rows × entity/data flow/process columns, with mitigations & vulnerabilities.
* **Attack trees:** attacker’s point of view, different paths to a goal. Focus on path of least resistance.

    * Identify attack goals (each goal = separate tree)
    * Expand with possible attacks
    * Verify with peers

**Attack libraries:**

1. [OWASP Top 10](https://owasp.org/www-project-top-ten/) – Web application focus
2. [MITRE ATT\&CK](https://attack.mitre.org/) – Real-world tactics & techniques
3. [CAPEC](https://capec.mitre.org/) – Attack pattern classification
4. SANS Top 25 – Common coding mistakes
5. OWASP Attack Category
6. OWASP Top 10 Proactive Controls
7. OWASP ASVS – Application Security Verification Standard

### 3. Control / Countermeasures

**Risk scoring methods:**

* **DREAD** – subjective, no longer in use
* **CVSS** – Common Vulnerability Scoring System ([online calculator](https://www.first.org/cvss/calculator/4-0))
* **OWASP Risk Rating (simplified)** – commonly used

**OWASP Risk Rating (simplified):**

* A: Attack vector – ease of exploitation
* B: Prevalence – portion of system affected
* C: Detectability – from attacker’s point of view
* D: Technical impact

Formula: `Risk = (A + B + C) / 3 * D`

* Low: < 3
* Medium: < 7
* High: ≤ 9

#### Enterprise Context (Layers of Threat Modeling)

1. **Organization** – culture, leadership, policies
2. **Architecture** – high-level design, topology, trust zones
3. **Application Design** – user roles, data handling, protocols
4. **Technical Implementation** – code-level security practices
5. **Operations** – deployment, patching, monitoring, incident response

#### Addressing Threats

* Redesign to eliminate
* Apply standard mitigations
* Invent new mitigations
* Accept vulnerability in design (last resort)

### Threat Personas

* **Spy** – national interests, expert/specialist.
* **Thief** – personal gain, skill range from beginner to expert.
* **Trespasser** – personal fame, script kiddie → advanced attacker.
* **Vandal** – curiosity/personal fame, usually script kiddie.
* **Author** – curiosity/personal fame, often expert.

### 4. Evaluate

* Triage threats & prioritize countermeasures:
    * Evaluate impact (severity)
    * Assess ease of exploit (prioritize low-effort attacks)
    * Protect key assets (critical systems first)
    * Follow regulations (avoid compliance penalties)
    * Act on top threats first

**Reference:** [OWASP Threat Modeling Playbook](https://owasp.org/www-project-threat-modeling-playbook/)
