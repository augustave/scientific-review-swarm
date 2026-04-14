# Scientific Review Swarm

A peer swarm of **15 scientific-domain agents** that review defense-aerospace projects from their specialized perspectives, feeding structured findings into G1-G4 gate processes.

**Built:** 2026-04-13 | **Version:** 1.0.0 | **Status:** Active, pilot-tested | **Author:** Tao Conrad

---

## Table of Contents

1. [Genesis — Where This Came From](#genesis--where-this-came-from)
2. [Build Intention — What Problem It Solves](#build-intention--what-problem-it-solves)
3. [Research Intent — The Scientific Lens Thesis](#research-intent--the-scientific-lens-thesis)
4. [Architecture — How It Works](#architecture--how-it-works)
5. [The 15 Agents — Defense-Aerospace Mappings](#the-15-agents--defense-aerospace-mappings)
6. [Design Decisions — Why It's Built This Way](#design-decisions--why-its-built-this-way)
7. [Pilot Test — MINI-D Review Results](#pilot-test--mini-d-review-results)
8. [Quick Start](#quick-start)
9. [Integration with autonomous-aerospace-collective](#integration-with-autonomous-aerospace-collective)
10. [File Structure](#file-structure)
11. [Build History — Session Timeline](#build-history--session-timeline)
12. [Future Work](#future-work)

---

## Genesis — Where This Came From

### The Spark

The concept emerged from a single image: the **Claude Scientific Skills** collection by Ki-Dense — a catalog of 128+ ready-to-use scientific skills across 15 domains (bioinformatics, cheminformatics, proteomics, clinical research, healthcare AI, medical imaging, ML/AI, materials science, physics, engineering simulation, data analysis, lab automation, scientific communication, multi-omics, protein engineering).

The question was: *"What if these 15 scientific domains weren't just standalone tools — what if they formed a swarm that could look at defense-aerospace projects from their perspective?"*

This is not the first swarm in the ecosystem. The **autonomous-aerospace-collective** already exists as a defense-grade swarm with 4 cells (Vanguard, Architect, Foundry, Assurance Core), gates G1-G4, and an artifact bus. The scientific-review-swarm was conceived as a **peer swarm** — a parallel advisory board that feeds scientific insights into the existing gate process.

### The Existing Ecosystem

Before this swarm was built, the following defense-aerospace infrastructure already existed:

| Project | Path | Purpose |
|---------|------|---------|
| **MINI DRONE (MINI-D)** | `Dev/GitHub 4/MINI DRONE/` | Distributed drone swarm simulation & verification lab |
| **autonomous-aerospace-collective** | `Dev/SKILLS/autonomous-aerospace-collective-v2/` | 4-cell defense aircraft design swarm |
| **Sentinel-Century-Radar** | `Dev/GitHub 4/BALTHAZAR/...` | 100-node bio-quantum sensing sentinel swarm |
| **CYPHER-TRICK Grand Prix** | `Dev/GitHub 4/CYPHER-TRICK/GRANDPRIX/` | AI autonomous drone racing (Anduril competition) |
| **APEX** | `Dev/GitHub 4/APEX/` | Defense-readiness documentation framework |
| **Swarm Aircraft Digital Twin** | `Dev/Skills Temp/swarm_aircraft_skillmds/` | 9 specialized aircraft engineering roles |

Plus **16+ existing defense skills** covering C2, SIGINT, orbital mechanics, warfighter systems, avionics foundry, and more.

The scientific-review-swarm was designed to sit alongside all of this — not replacing any of it, but adding a new analytical dimension that none of the existing tools provided.

---

## Build Intention — What Problem It Solves

### The Problem

Defense-aerospace engineering is deep but often narrow. An avionics engineer thinks about PCB layout and firmware. A flight scientist thinks about aerodynamics and control surfaces. A test engineer thinks about HIL rigs and regression. But who asks:

- "Is the battery discharge model using the right distribution?" *(Materials Science)*
- "Does the test campaign have enough statistical power to detect the claimed improvement?" *(Clinical Research)*
- "Is the swarm coordination algorithm reinventing solutions that biology already solved?" *(Bioinformatics)*
- "Could the drift model use a Gaussian instead of uniform — and does it matter?" *(Engineering Simulation)*
- "Are claims supported by evidence at the stated confidence level?" *(Scientific Communication)*

These are **cross-disciplinary questions** that fall between the cracks of domain-specific engineering review. The scientific-review-swarm exists to ask these questions systematically.

### The Solution

Transform 15 scientific domains into **defense-aerospace-aware review agents**, each fluent in both its home discipline and its defense-relevant applications. Deploy them as a parallel swarm against any project, collect structured reports, and consolidate findings into gate-ready artifacts.

### What It Is NOT

- **Not a replacement** for domain-specific engineering review. The Architect cell still owns flight sciences. The Foundry cell still owns avionics. The Assurance Core still owns test.
- **Not a compliance tool**. It does not enforce ITAR, DO-178C, or MIL-STD-882E. It flags where those standards might apply.
- **Not a simulation**. It reviews projects by reading code, documentation, and architecture — it does not run simulations itself.
- **Not a gatekeeper**. It produces advisory findings. Only G3/G4 have a "Scientific Review Lead" signoff role, and even that is recommended, not mandatory.

---

## Research Intent — The Scientific Lens Thesis

### Core Thesis

> Every defense-aerospace project embeds scientific assumptions — in its physics models, its materials choices, its statistical methods, its coordination algorithms, its evidence standards. Most of these assumptions are invisible to domain engineers because they are in fields outside their training. A swarm of scientific domain experts can surface these hidden assumptions, identify where they are wrong or underspecified, and propose improvements from established scientific methods.

### The Translation Challenge

The hardest part of this project was not building agents — it was **mapping scientific domains to defense-aerospace contexts**. Some mappings are obvious:

- Materials Science → airframe composites, thermal protection
- Physics → orbital mechanics, RF propagation
- ML/AI → autonomy, perception, decision-making

Others required creative analogical reasoning:

| Scientific Domain | Defense-Aerospace Mapping | Translation Mechanism |
|-------------------|--------------------------|----------------------|
| Bioinformatics | Swarm coordination algorithms | ACO, PSO, GA are directly from biology. Stigmergy, quorum sensing, chemotaxis are swarm primitives. |
| Clinical Research | Operational test methodology | A test campaign is a clinical trial. Statistical power, confounding variables, and intention-to-treat apply identically. |
| Proteomics | ISR trace detection, spectral analysis | Mass spec sensitivity/specificity maps to sensor detection limits. False discovery rate maps to false alarm rate. |
| Healthcare AI | Autonomy safety cases | Clinical AI safety (FDA-grade model V&V, bias detection, human-in-the-loop) translates directly to autonomous defense systems. |
| Multi-omics | Multi-domain data integration | RF + EO/IR + SIGINT + Cyber layers are structurally identical to genomics + transcriptomics + proteomics + metabolomics. Integration strategies (early/mid/late fusion) are the same. |
| Protein Engineering | Design space optimization | Directed evolution = iterative design optimization. Epistasis = non-additive interactions between design variables. Structure-function = modular architecture analysis. |
| Medical Imaging | EO/IR and SAR processing | Segmentation, registration, and anomaly detection algorithms are domain-agnostic. DICOM workflow parallels defense imagery chains. |
| Scientific Communication | Claims traceability, G4 compliance | Peer review methodology, evidence hierarchies, and overclaiming detection apply directly to defense claims validation. |

### The Relevance Honesty Principle

Not every domain applies to every project. A Materials Science agent reviewing a pure-software simulation should not manufacture findings about composites. The **Relevance Honesty** invariant was designed specifically for this: agents must self-score their relevance (0-100) and produce a "Not Applicable" section explaining what doesn't apply. This prevents the swarm from generating noise.

The pilot test validated this: Materials Science scored itself 28/100 against MINI-D (a simulation project) and correctly focused on simulation fidelity of materials-adjacent phenomena (battery models, wind models) rather than forcing irrelevant findings about composites or coatings.

---

## Architecture — How It Works

### Topology: Parallel Peer Swarm

```
                    ┌─────────────────────────────────┐
                    │    autonomous-aerospace-collective    │
                    │  Vanguard │ Architect │ Foundry │ Assurance │
                    │           │           │         │           │
                    │      G1 ──── G2 ──── G3 ──── G4           │
                    └──────▲──────────────────▲────────┘
                           │                  │
          consolidated_scientific_review_v1    risk_register_scientific_v1
                           │                  │
                    ┌──────┴──────────────────┴────────┐
                    │      scientific-review-swarm           │
                    │                                        │
                    │   ┌─ Wave 1: Physical Sciences ──┐     │
                    │   │  Materials, Physics, Eng/Sim │     │
                    │   │  Data Analysis, Lab Auto     │     │
                    │   └──────────────────────────────┘     │
                    │   ┌─ Wave 2: Cross-Cutting ──────┐     │
                    │   │  ML/AI, Cheminformatics      │     │
                    │   │  Scientific Communication    │     │
                    │   └──────────────────────────────┘     │
                    │   ┌─ Wave 3: Life Sciences ──────┐     │
                    │   │  Bioinformatics, Proteomics  │     │
                    │   │  Clinical, Healthcare AI     │     │
                    │   │  Medical Imaging, Multi-omics│     │
                    │   │  Protein Engineering         │     │
                    │   └──────────────────────────────┘     │
                    │                                        │
                    │          ▼ Orchestrator ▼               │
                    │   consolidated_scientific_review_v1     │
                    │   risk_register_scientific_v1           │
                    └────────────────────────────────────────┘
```

### Artifact Bus

| From | To | Artifact |
|------|----|----------|
| Orchestrator | All Agents | `project_manifest_v1` — project summary, file index, domain tags |
| Orchestrator | All Agents | `review_scope_v1` — what to review, gate context, depth |
| Each Agent | Orchestrator | `scientific_review_report_v1` — structured per REPORT_TEMPLATE |
| Each Agent | Orchestrator | `relevance_score` (0-100) — self-assessed relevance |
| Each Agent | Orchestrator | `cross_domain_flags` — issues needing another agent |
| Orchestrator | Gates | `consolidated_scientific_review_v1` — merged report for G1-G4 |
| Orchestrator | Gates | `risk_register_scientific_v1` — ranked risks with evidence |

### Global Invariants

1. **Scientific Grounding** — Every recommendation must cite a mechanism, not just a heuristic
2. **Relevance Honesty** — Agents self-score; low-relevance agents produce "not applicable" rather than forcing findings
3. **Cross-Domain Traceability** — Cross-domain dependencies must be flagged explicitly
4. **No Jargon Without Definition** — Reports target defense engineers; all scientific terms defined in context
5. **Export Awareness** — Inherited from parent swarm; flag controlled techniques

---

## The 15 Agents — Defense-Aerospace Mappings

### Cell A: Physical Sciences (Wave 1)

| # | Agent | Color | Scientific Domain | Defense-Aerospace Lens | Key Questions |
|---|-------|-------|-------------------|----------------------|---------------|
| 1 | `sci-materials-science` | Yellow | Composites, thermal, coatings, fatigue, corrosion | Airframe materials, radar-absorbing materials, environmental durability | Materials appropriate for thermal envelope? Fatigue life methodology? RCS-driven material tradeoffs? |
| 2 | `sci-physics-astronomy` | White | Classical mechanics, EM, optics, orbital mechanics | Orbital mechanics, RF/radar physics, propulsion thermo, aerodynamics | RF link budget consistent with propagation models? Orbital perturbations accounted for? |
| 3 | `sci-engineering-simulation` | Green | FEA, CFD, multi-physics, V&V, UQ | Simulation credibility (NASA-STD-7009), mesh convergence, uncertainty quantification | Simulation credibility appropriate for decision? Mesh convergence documented? Uncertainties quantified? |
| 4 | `sci-data-analysis` | Blue | Statistics, time series, sensor fusion, visualization | Telemetry analysis, anomaly detection, statistical process control, decision support | Appropriate statistical methods? Sensor fusion uncertainty quantified? Visualizations effective? |
| 5 | `sci-lab-automation` | Cyan | HIL, calibration, LIMS, CI/CD for hardware | Test automation, data provenance, evidence chain integrity | Tests automated with logging? Calibration managed? Results reproducible from archives? |

### Cell B: Life Sciences (Wave 3)

| # | Agent | Color | Scientific Domain | Defense-Aerospace Lens | Key Questions |
|---|-------|-------|-------------------|----------------------|---------------|
| 6 | `sci-bioinformatics` | Green | Genomics, bio-inspired algorithms | ACO/PSO/GA for swarm coordination, stigmergy, quorum sensing, biological sensing | Swarm uses established bio-inspired optimization? Evolutionary strategies for route planning? |
| 7 | `sci-proteomics` | Blue | Mass spec, spectral analysis, trace detection | ISR payload sensors, spectral signature analysis, contamination detection | Sensor suite addresses trace-level detection? Spectral pipelines validated? |
| 8 | `sci-clinical-research` | Cyan | Trial design, evidence hierarchy, statistical power | Test protocol rigor, confounding variables, intention-to-treat for operational testing | Test campaign statistically powered? Confounders controlled? Evidence hierarchy clear? |
| 9 | `sci-healthcare-ai` | Magenta | Clinical ML safety, model V&V, bias detection | Autonomy safety cases, human-machine trust calibration, runtime safety monitoring | Safety case exists? Model drift detected? Human-override validated? |
| 10 | `sci-medical-imaging` | Orange | Segmentation, registration, DICOM workflows | EO/IR processing, SAR image analysis, damage assessment, materials inspection | Segmentation FP/FN rates? Pipeline validated against ground truth? |
| 11 | `sci-multi-omics` | Orange | Multi-scale integration, network biology, emergent behavior | Multi-domain fusion (RF+EO/IR+SIGINT+cyber), emergent swarm behavior, network topology | Multi-domain integration consistent? Emergent behavior modeled? Network topology analyzed? |
| 12 | `sci-protein-engineering` | Purple | Directed evolution, structure-function, bio-mimetic design | Design parameter optimization, modular architecture analysis, bio-mimetic structures | Directed evolution for design search? Structure-function coupling analyzed? |

### Cell C: Cross-Cutting (Wave 2)

| # | Agent | Color | Scientific Domain | Defense-Aerospace Lens | Key Questions |
|---|-------|-------|-------------------|----------------------|---------------|
| 13 | `sci-machine-learning` | Red | DL, RL, adversarial ML, deployment | Autonomy/perception, sim-to-real, on-edge inference, adversarial robustness | ML fits SWaP? Sim-to-real gap addressed? Adversarial robustness tested? |
| 14 | `sci-cheminformatics` | Purple | Molecular properties, energetics, corrosion | Battery chemistry, propellants, corrosion chemistry, CBRN detection | Battery thermal runaway tradeoffs? Corrosion coatings specified? |
| 15 | `sci-scientific-communication` | Magenta | Technical writing, claims, evidence standards | Claims traceability, G4 compliance, overclaiming detection, evidence presentation | Claims supported at stated confidence? Limitations stated? G4 schema compliant? |

### MCP Tool Access

Select agents get additional data access via MCP servers:
- **bioRxiv/medRxiv**: Bioinformatics, Proteomics, Multi-omics, Protein Engineering
- **ClinicalTrials.gov**: Clinical Research, Healthcare AI
- **ChEMBL**: Cheminformatics

---

## Design Decisions — Why It's Built This Way

### Why Agents, Not Skills?

The existing `autonomous-aerospace-collective` uses **skills** (`.skill.md`) for producing artifacts within a cell — the Vanguard skill produces `market_requirements_doc`, the Architect skill produces `architecture_spec_v1`. Skills have inputs, outputs, and ports.

The scientific-review-swarm uses **agents** (`.md` in `agents/`) because the review role is fundamentally different: it reads a project, reasons about it from a scientific perspective, and produces a structured report. This matches the `feature-dev` plugin's pattern where `code-explorer`, `code-architect`, and `code-reviewer` agents analyze code without modifying it. The agent format (model, color, tools, read-only focus) is the right abstraction for review.

### Why 3 Cells Instead of 15 Individual Agents?

Launching all 15 agents simultaneously would be wasteful (many will be LOW relevance for any given project) and would overwhelm context. The cell structure provides:

1. **Wave-based launching** — Physical Sciences first (most broadly applicable), Cross-Cutting second, Life Sciences third
2. **Cross-domain flag propagation** — Wave 1 findings inform Wave 2/3 agents
3. **Relevance triage** — the orchestrator consults the relevance matrix and only launches HIGH + MEDIUM agents by default (typically 8-12 of 15)

### Why Sonnet Model for All Agents?

Review agents need to read code, reason about scientific applicability, and produce structured reports. This matches the `code-architect` / `code-explorer` pattern which all use `sonnet`. The orchestrator command runs on the main model (which can be opus for deeper reasoning). Sonnet provides the right balance of depth and speed for parallel agent deployment.

### Why Self-Assessed Relevance Scores?

Forcing all 15 agents to produce deep reports on every project is wasteful. A Materials Science agent reviewing documentation-only should return "relevance: 10" and a brief report. The orchestrator uses these scores to weight the consolidated report and determine which findings to feature prominently.

The pilot test validated this design: Materials Science scored 28/100 against MINI-D and focused on simulation fidelity of materials-adjacent phenomena. Scientific Communication scored 92/100 and produced the deepest findings. The relevance scores correctly prioritized attention.

### Why a Relevance Matrix?

The matrix pre-classifies agent relevance by project type, enabling the orchestrator to skip LOW-relevance agents before they even launch. This is an efficiency optimization — it typically reduces the agent count from 15 to 8-12, saving ~40% compute while preserving the most impactful reviews.

The matrix is a starting guide, not a cage. Users can override it (`--full` flag), and cross-domain flags can promote skipped agents if a running agent discovers something that needs another domain's perspective.

### Why the SWARM.md Pattern?

The existing `autonomous-aerospace-collective-v2/SWARM.md` established a proven pattern: YAML frontmatter defining the swarm's identity, topology, and skills, followed by markdown documenting cells, artifact bus, gates, and invariants. The scientific-review-swarm follows this pattern exactly, enabling potential future tooling that reads SWARM.md files to orchestrate multi-swarm operations.

### Why Peer Swarm Instead of Adding Cells to the Existing Swarm?

The autonomous-aerospace-collective is a **production swarm** — its 4 cells produce artifacts that feed into a manufacturing pipeline. Adding 15 scientific review agents as cells would pollute the production topology. The peer swarm architecture keeps the scientific review cleanly separated while still feeding into the same gate process via the artifact bus bridge.

---

## Pilot Test — MINI-D Review Results

### Deployment: 2026-04-13

The swarm's first operational test was a deep review of **MINI-D** (Distributed Mini-Drone Autonomy Simulation Lab).

### Configuration

- **Project type detected:** Drone Swarm Simulation
- **Agents deployed:** 10 / 15 (HIGH + MEDIUM relevance)
- **Agents skipped (LOW):** Physics/Astronomy, Cheminformatics, Proteomics, Medical Imaging, Protein Engineering
- **Review depth:** Deep
- **Wall-clock time:** ~20 minutes (all agents ran in parallel background)

### Results Summary

| Metric | Value |
|--------|-------|
| Total findings | 70 |
| Critical | 13 |
| Major | 30 |
| Minor | 24 |
| Informational | 3 |
| Strengths identified | 8 |
| Opportunities identified | 15+ |
| NASA-STD-7009 credibility level | 1-2 / 5 |

### Top 5 Findings (Cross-Agent Convergence)

| # | Finding | Agents Flagging | Gate |
|---|---------|----------------|------|
| 1 | **ProofConsole displays fabricated data as "verification"** — `Math.random()` and hardcoded formulas with paper citations, "99.8% integrity" | Sci Comm, Data Analysis | G4 |
| 2 | **No uncertainty quantification** on any metric or claim — all point estimates, no CI, no variance | Eng Sim, Data, ML, Clinical **(4 agents)** | G3/G4 |
| 3 | **CoV runner: 3 seeds, labeled "95% (N=5)"** — both numbers wrong, majority vote suppresses failures | Sci Comm, Data, Clinical | G4 |
| 4 | **Drift uses Uniform instead of Gaussian** — `driftSigma` sampled uniform, underestimates tail events by 3.5x | Eng Sim, ML | G1 |
| 5 | **Claim ID namespace collision** — C-001..C-009 in docs vs C1..C7 in code, no mapping, no `artifact_hash` | Sci Comm | G4 |

### Cross-Agent Convergence Map

The strongest signal from the pilot test was **independent convergence** — multiple agents discovering the same issue without knowledge of each other's findings:

| Issue | Independent Agent Count |
|-------|------------------------|
| No uncertainty quantification | **4** (Eng Sim, Data, ML, Clinical) |
| Wind model too simple | **3** (Eng Sim, Materials, ML) |
| CoV seed/confidence label wrong | **3** (Sci Comm, Data, Clinical) |
| ProofConsole fabricated data | **2** (Sci Comm, Data) |
| Uniform ≠ Gaussian drift | **2** (Eng Sim, ML) |
| Centralized dispatch gap | **2** (Bioinformatics, ML) |
| Single-seed phase diagram | **2** (Data, Clinical) |

This convergence validates the swarm design: findings that appear across multiple independent scientific lenses have the highest signal-to-noise ratio.

### Unique Discoveries by Domain

Each agent also discovered issues that no other agent found, demonstrating the value of diverse perspectives:

| Agent | Unique Discovery |
|-------|-----------------|
| Bioinformatics | Existing chemotaxis and gap junction features are dormant (taxisWeight=0); only 1 of 3 Reynolds boid rules implemented |
| Clinical Research | E3_SIZE has no golden fixtures (blind spot in regression gate); E4 confounds 3 variables simultaneously |
| Multi-omics | Panic cascade is structurally identical to site percolation; 4 feedback loops identified but uncharacterized |
| Healthcare AI | No swarm-level safe state; dispatch failure reasons computed but never shown in UI |
| Lab Automation | CI pipeline exists (missed by other agents); BASE_CONFIG duplicated across 4+ files |
| ML/AI | Project is 80% of a Gymnasium RL environment; no adversarial agent modeling |
| Materials Science | Battery model lacks temperature-dependent capacity fade; drone profiles lack material-class metadata |

### Pilot Test Validation Conclusions

1. **Relevance honesty works** — Materials Science (28/100) correctly scoped itself; Scientific Communication (92/100) produced the deepest findings
2. **Cross-domain convergence is the signal** — 4-agent convergence on UQ is a much stronger signal than any single agent's finding
3. **Unique discoveries justify breadth** — each agent found something no other agent could have
4. **Wave-based launch is efficient** — agents can run concurrently without coordination overhead
5. **The report template produces consistent, comparable outputs** — easy to consolidate across domains

### Artifacts Produced

- `reviews/MINI-D_consolidated_scientific_review_v1.md` — Full consolidated review with gate mapping
- `reviews/MINI-D_risk_register_scientific_v1.md` — 20 ranked risks with evidence and recommendations

---

## Quick Start

```
/scientific-review /path/to/your/defense-project
```

The orchestrator will:
1. **Discover** the project — read README, SWARM.md, key configs, detect project type
2. **Triage** — select agents via the relevance matrix, present roster for approval
3. **Launch** agents in 3 waves (Physical Sciences, Cross-Cutting, Life Sciences)
4. **Collect** reports, resolve cross-domain flags
5. **Consolidate** into `consolidated_scientific_review_v1` + `risk_register_scientific_v1`
6. **Present** top 5 findings, risk register, and gate mapping

### Options

- `--full` — Launch all 15 agents regardless of relevance
- `--depth quick` — Rapid scan, top 3 findings per agent
- `--depth deep` — Full comprehensive review (default)

### Target Projects

The swarm is designed to review any defense-aerospace project:

| Project Type | Typical Agents (8-12) |
|-------------|----------------------|
| Drone Swarm | Materials, ML, Eng/Sim, Data, Bioinformatics, Multi-omics, Clinical, Healthcare AI, Lab Auto, Sci Comm |
| Aircraft Design | Materials, Physics, Eng/Sim, Lab Auto, ML, Cheminformatics, Sci Comm, Clinical |
| Radar/Sensing | Physics, Data, Proteomics, Medical Imaging, Eng/Sim, ML, Sci Comm, Multi-omics |
| Racing Drone | Materials, ML, Eng/Sim, Data, Bioinformatics, Sci Comm, Healthcare AI |
| Defense Docs | Sci Comm, Data, Clinical, Lab Auto |
| Digital Twin | ML, Physics, Eng/Sim, Data, Multi-omics, Materials, Clinical, Lab Auto |

---

## Integration with autonomous-aerospace-collective

### Relationship

This is a **peer swarm** — it does not replace the existing 4-cell defense swarm. It feeds scientific findings into the existing gate process.

### Artifact Bus Bridge

```
scientific-review-swarm                    autonomous-aerospace-collective
========================                   ================================

15 Scientific Agents                       4 Cells + Lab Engineer
        |                                          |
        v                                          |
  Orchestrator                                     |
        |                                          |
        +-- consolidated_scientific_review_v1 ---> Architect Cell
        |                                          |
        +-- risk_register_scientific_v1 ---------> Assurance Core
                                                   |
                                            G1 -- G2 -- G3 -- G4
```

### Gate Mapping

| Gate | Scientific Contributions | Primary Agents |
|------|------------------------|----------------|
| **G1 Architecture** | Physics reality checks, materials feasibility, simulation fidelity | Physics, Materials, Eng/Sim, Multi-omics |
| **G2 Fabrication** | Manufacturing concerns, chemistry compatibility, DFM | Materials, Cheminformatics, Lab Auto |
| **G3 Validation** | Test methodology rigor, statistical power, evidence quality | Clinical, Data, Eng/Sim, Lab Auto |
| **G4 Claims** | Claims scientific backing, overclaiming detection, G4 schema compliance | Sci Comm, all agents |

### Release Authority Extension

| Gate | Existing Signatories | + Scientific Review Lead |
|------|---------------------|--------------------------|
| G1 | Architect | Advisory |
| G2 | Foundry Lead | Advisory |
| G3 | Assurance Core Lead | **Required signoff** |
| G4 | Swarm Lead | **Required signoff** |

See `docs/GATE_INTEGRATION.md` for full details.

---

## File Structure

```
scientific-review-swarm/
|-- .claude-plugin/
|   +-- plugin.json                         # Plugin metadata
|-- README.md                               # This file
|-- SWARM.md                                # Master swarm config (cells, bus, gates, invariants)
|-- agents/                                 # 15 scientific domain agents
|   |-- sci-materials-science.md
|   |-- sci-machine-learning.md
|   |-- sci-physics-astronomy.md
|   |-- sci-engineering-simulation.md
|   |-- sci-data-analysis.md
|   |-- sci-lab-automation.md
|   |-- sci-bioinformatics.md
|   |-- sci-cheminformatics.md
|   |-- sci-proteomics.md
|   |-- sci-clinical-research.md
|   |-- sci-healthcare-ai.md
|   |-- sci-medical-imaging.md
|   |-- sci-scientific-communication.md
|   |-- sci-multi-omics.md
|   +-- sci-protein-engineering.md
|-- commands/
|   +-- scientific-review.md               # Orchestrator slash command (6 phases)
|-- skills/
|   +-- review-orchestrator/
|       +-- SKILL.md                       # Orchestrator skill (artifact contracts)
|-- docs/
|   |-- RELEVANCE_MATRIX.md               # Agent selection per project type
|   |-- REPORT_TEMPLATE.md                # Structured report format
|   +-- GATE_INTEGRATION.md              # How findings map to G1-G4
+-- reviews/                              # Generated review artifacts
    |-- MINI-D_consolidated_scientific_review_v1.md
    +-- MINI-D_risk_register_scientific_v1.md
```

---

## Build History — Session Timeline

### Phase 0: Catalyst (2026-04-13, T+0)

**Input:** User shared an image of the "Claude Scientific Skills" collection — 128+ scientific skills across 15 domains by Ki-Dense.

**Question posed:** *"What do you think I can do with it?"*

**Response:** Identified that the user already had several bio-research skills installed (scvi-tools, single-cell-rna-qc, nextflow, etc.) plus bioRxiv, ClinicalTrials.gov, and ChEMBL MCP servers. Listed practical capabilities.

### Phase 1: Concept — "Transform them into a swarm" (T+5min)

**User intent:** *"I would like to transform them into a swarm that could look at my defense-aerospace projects from their perspective."*

This single sentence defined the entire project. Three key elements:
1. **"Transform them"** — take the 15 scientific domains and make them active agents
2. **"into a swarm"** — not individual tools, but a coordinated multi-agent system
3. **"from their perspective"** — each domain maintains its own scientific lens

### Phase 2: Research & Discovery (T+8min)

Three parallel exploration agents deployed:
1. **Defense-aerospace project discovery** — found 6 major projects, 16+ skills
2. **Skill/agent format discovery** — mapped the plugin structure (YAML frontmatter + markdown), agent format, command format, hooks
3. **Existing swarm pattern discovery** — found the autonomous-aerospace-collective SWARM.md, its 4 cells, gates, artifact bus, and invariant patterns

Key reference files identified:
- `autonomous-aerospace-collective-v2/SWARM.md` — the SWARM.md pattern to follow
- `defense-market-vanguard.skill.md` — the skill artifact contract pattern
- `feature-dev/agents/code-architect.md` — the agent definition format
- `feature-dev/commands/feature-dev.md` — the orchestrator command pattern

### Phase 3: Architecture Design (T+15min)

A Plan agent designed the complete architecture:
- Plugin structure with 22 files
- SWARM.md with 3 cells, artifact bus, gates, invariants
- All 15 agent definitions with defense-aerospace perspective mappings
- Relevance matrix (15 agents x 6 project types)
- 6-phase orchestrator command
- Report template with severity/category/gate definitions
- Gate integration with existing G1-G4
- 7-phase implementation order

### Phase 4: Implementation — Foundation (T+20min)

Created plugin skeleton:
- `.claude-plugin/plugin.json`
- `SWARM.md` (95 lines)
- `docs/REPORT_TEMPLATE.md` (75 lines)
- `docs/RELEVANCE_MATRIX.md` (60 lines)

### Phase 5: Implementation — 15 Agents (T+25min)

Built all 15 agents in 3 parallel batches:
- **Batch 1 (Core, 5 agents):** Materials, ML, Physics, Eng/Sim, Data Analysis
- **Batch 2 (Supporting, 5 agents):** Lab Auto, Sci Comm, Bioinformatics, Clinical Research, Healthcare AI
- **Batch 3 (Specialized, 5 agents):** Medical Imaging, Multi-omics, Cheminformatics, Proteomics, Protein Engineering

Each agent: ~80-150 lines of defense-aerospace-aware scientific review guidance.

### Phase 6: Implementation — Orchestrator & Integration (T+35min)

- `commands/scientific-review.md` — 6-phase orchestrator (125 lines)
- `skills/review-orchestrator/SKILL.md` — artifact contracts with input/output/port specifications
- `docs/GATE_INTEGRATION.md` — full gate mapping with release authority extension
- `README.md` — initial quick-start documentation

### Phase 7: Pilot Test — MINI-D (T+40min)

Live deployment against MINI-D:

1. **Project discovery agent** — built comprehensive project manifest (directory structure, key files, experiment modes, verification gates, NPM scripts)
2. **Relevance triage** — selected 10 of 15 agents (skipped 5 LOW-relevance)
3. **Wave 1 launch** — Materials, Eng/Sim, Data Analysis (3 agents in parallel)
4. **Wave 2 launch** — ML, Bioinformatics, Sci Comm (3 agents in parallel)
5. **Wave 3 launch** — Multi-omics, Clinical Research, Healthcare AI, Lab Auto (4 agents in parallel)
6. **Report collection** — all 10 agents returned within ~20 minutes
7. **Consolidation** — merged 70 findings into consolidated review + risk register

### Phase 8: Consolidation & Delivery (T+65min)

- `reviews/MINI-D_consolidated_scientific_review_v1.md` — full consolidated review with Top 5, gate mapping, cross-cutting themes, NASA-STD-7009 assessment, opportunities
- `reviews/MINI-D_risk_register_scientific_v1.md` — 20 ranked risks with severity, domain, gate, description, recommendation

### Total Build Time: ~65 minutes

From "what do you think I can do with it" to a fully operational 15-agent swarm with a completed pilot review producing 70 findings across 10 scientific domains.

---

## Future Work

### Immediate (next session)

1. **Register plugin** in `~/.claude/settings.json` for permanent availability
2. **Fix MINI-D critical findings** — ProofConsole, UQ, CoV seeds, Gaussian drift
3. **Run against autonomous-aerospace-collective** — test the peer swarm integration

### Near-term

4. **Run against all 6 defense-aerospace projects** — build a cross-project risk landscape
5. **Tune agent prompts** based on pilot test report quality
6. **Add MCP tool access** to agents that can benefit from bioRxiv/ClinicalTrials/ChEMBL data
7. **Build a review dashboard** — aggregate findings across projects and track resolution

### Long-term

8. **Scheduled scientific reviews** — weekly automated swarm runs via cron triggers
9. **Cross-swarm orchestration** — scientific-review-swarm and autonomous-aerospace-collective running in coordinated sessions
10. **Agent specialization evolution** — agents learn from previous reviews to improve their defense-aerospace mappings
11. **Community templates** — publish the plugin for other defense-aerospace teams

---

## Key Principles

1. **Scientific Grounding** — Every recommendation cites a mechanism, not a heuristic
2. **Relevance Honesty** — Agents self-score; low-relevance agents say "not applicable" rather than forcing findings
3. **Cross-Domain Traceability** — Dependencies between domains are flagged explicitly
4. **No Jargon Without Definition** — Reports target defense engineers
5. **Export Awareness** — Inherited from parent swarm; scientific recommendations flag controlled techniques
6. **Convergence Is Signal** — Findings flagged independently by multiple agents have the highest confidence
7. **Breadth Enables Discovery** — Each agent finds things no other agent could have; the value is in the union, not the intersection
8. **Peer, Not Parent** — The scientific swarm advises; the engineering swarm decides
