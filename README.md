# Evidence-Based Operator Network Fault Localisation

**Hackathon:** AIORI-3 — Cybersecurity  
**Problem Statement:** PS-035  
**Team Code:** A3-PS035-TC262  

---

## 🎥 Team Introduction Video

As part of the AIORI-3 hackathon's initial orientation, our team has
prepared an introduction video presenting our understanding of the
problem statement, our proposed solution, and the assigned roles
and responsibilities of each team member.

**▶️ [Watch Our Team Introduction Video](https://youtu.be/nVIh0pni0wo)**


Modern operator networks are complex, multi-hop environments.
## 1. Problem Statement

Modern operator networks are complex, multi-hop environments. When a physical link fails or a router interface goes down, the failure rarely produces an isolated alarm. Instead, network operations centers (NOCs) are inundated with a cascade of correlated secondary symptoms—including interface state transitions, BGP session drops, routing re-convergence alerts, and active latency/packet loss warnings across adjacent hops.

Manually isolating the genuine root cause requires operators to mentally cross-reference high-volume alarm floods against dynamic topology maps under time-critical conditions. This increases Mean Time to Repair (MTTR) and risks misdiagnoses.

---

## 2. Proposed Solution

The proposed system is an evidence-based fault localisation engine designed to automate symptom correlation and assist network operators. By unifying three primary data sources:
1. **Network Topology Definitions:** Graph representation of nodes, links, and operational dependencies.
2. **Operator Logs:** Syslog events capturing state changes and protocol notifications.
3. **Active Measurements:** Periodic active ping/reachability probes across node pairs.

The engine correlates observed anomalies across network hops, executes a rule-based diagnostic baseline to rank the most probable root causes (Top-1 and Top-3), and generates human-verifiable evidence chains explaining each diagnosis. Crucially, when observed symptoms are ambiguous or telemetry is incomplete, the system explicitly identifies that available evidence is insufficient rather than making unwarranted assumptions.

---

## 3. Key Requirements

- **Five-Node Network Topology:** A controlled instrumented lab topology of 5 nodes representing operator network paths.
- **Five Seeded Fault Scenarios:** Systematic injection of 5 distinct fault types (e.g., link degradation/cut, node reboot, BGP misconfiguration/peering drop, interface flapping, high packet loss).
- **Rule-Based Diagnostic Baseline:** A deterministic baseline engine correlating telemetry events to candidate faults.
- **Evidence-Supported Diagnosis Ranking:** Ranked fault candidates paired with explicit explanatory evidence (e.g., timestamps, matched log patterns, impacted probe paths).
- **Top-1 and Top-3 Accuracy Evaluation:** Quantitative evaluation benchmarks measured against held-out validation runs.
- **Handling Insufficient Evidence:** Explicit detection and classification of cases where telemetry is inconclusive.
- *(Optional Future Extension)*: A secondary AI/ML diagnostic model evaluated alongside the rule-based baseline.
- *(Scope Guardrails)*: No automated network remediation, no unconstrained autonomous agents, and no false guarantees of infallible root-cause identification.

---

## 4. Proposed Workflow

The end-to-end diagnostic pipeline follows a structured, evidence-backed workflow:

```
[Network Topology] + [Syslog Events] + [Active Ping Probes]
                             │
                             ▼
               [Symptom Correlation Pipeline]
                             │
                             ▼
             [Rule-Based Diagnostic Baseline]
                             │
                             ▼
       [Ranked Root Causes (Top-1 / Top-3) + Evidence]
                             │
            ┌────────────────┴────────────────┐
            ▼                                 ▼
   [Sufficient Evidence]            [Insufficient Evidence]
    - Ranked Root Causes             - Explicit Inconclusive Flag
    - Correlated Evidence Chain      - Identified Telemetry Gaps
            │                                 │
            └────────────────┬────────────────┘
                             ▼
               [Accuracy & Run Evaluation]
```

---

## 5. Technology Stack

> **Status:** Preliminary selection; implementation in development.

- **Language:** Python *(Target runtime: Python 3.10+)* — *TBD*
- **Network Emulation / Lab:** *TBD* (e.g., Mininet, Containerlab, or simulated network telemetry harness)
- **Telemetry Processing:** *TBD* (Syslog parser and ICMP probe monitor)
- **Diagnostic Engine:** Rule-based expert system / graph traversal baseline (*TBD*)
- **AI/ML Extension:** *TBD (Optional addition following baseline validation)*

---

## 6. Repository Structure

This repository retains the official AIORI-3 template structure:

```
.
├── Proposed-structure-hackathon.pdf  # Official presentation & structure template
├── README.md                         # Project documentation and specifications
└── src/                              # Source code directory
    └── README.md                     # Source layout and module guide
```

*Note: All core fault-localization source code and scripts will be housed under `src/` as development progresses.*

---

## 7. Setup and Execution

> **Status:** Implementation Pending

No diagnostic scripts or dependencies have been implemented yet. Setup and run instructions will be provided here as modules are developed.

