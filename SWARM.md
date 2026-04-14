---
swarm_name: scientific-review-swarm
type: swarm
version: "1.0.0"
owner: scientific-review-lead
status: active
domain_tags: [scientific-review, defense, aerospace, materials, physics, simulation, autonomy, bio-inspired, sensing, data-analysis, lab-automation, clinical-methods]
risk_level: advisory
operating_environment: "Peer Review / Export-Aware"
topology: parallel
mission: "Review defense-aerospace projects through 15 scientific domain lenses, producing structured findings that feed into existing G1-G4 gate processes."
peer_swarms:
  - autonomous-aerospace-collective
cells:
  physical_sciences:
    - sci-materials-science
    - sci-physics-astronomy
    - sci-engineering-simulation
    - sci-data-analysis
    - sci-lab-automation
  life_sciences:
    - sci-bioinformatics
    - sci-proteomics
    - sci-clinical-research
    - sci-healthcare-ai
    - sci-medical-imaging
    - sci-multi-omics
    - sci-protein-engineering
  cross_cutting:
    - sci-machine-learning
    - sci-cheminformatics
    - sci-scientific-communication
---

# scientific-review-swarm (SWARM)

## Mission
Review defense-aerospace projects through 15 scientific domain lenses, producing structured findings that feed into existing G1-G4 gate processes. Each agent acts as a specialized scientific advisor — examining architecture, design, test methodology, and claims from its domain's perspective.

## Relationship to autonomous-aerospace-collective
This is a **peer swarm** — it does not replace the existing 4-cell defense swarm. Instead, it produces `consolidated_scientific_review_v1` and `risk_register_scientific_v1` artifacts that feed into the Architect and Assurance Core cells of the parent swarm.

## Cells

### Cell A: Physical Sciences (Wave 1)
Agents that map most directly to aerospace hardware, flight physics, and test infrastructure.
1. **Materials Science** — Composites, thermal protection, radar-absorbing materials, fatigue life, coatings
2. **Physics & Astronomy** — Orbital mechanics, RF physics, propulsion thermodynamics, aerodynamics, atmospheric effects
3. **Engineering & Simulation** — FEA/CFD fidelity, multi-physics simulation, V&V per NASA-STD-7009, uncertainty quantification
4. **Data Analysis** — Telemetry, sensor fusion, anomaly detection, statistical process control, visualization
5. **Lab Automation** — HIL test automation, calibration management, data provenance, CI/CD for hardware

### Cell B: Life Sciences (Wave 3)
Agents that map to bio-inspired algorithms, human factors, CBRN, environmental survivability, and operator health.
1. **Bioinformatics** — Bio-inspired swarm algorithms (ACO, PSO, GA), evolutionary optimization, biological sensing paradigms
2. **Proteomics** — Trace chemical detection for ISR, spectral signature analysis, contamination detection
3. **Clinical Research** — Test protocol rigor (clinical trial methodology for operational testing), statistical power, evidence hierarchy
4. **Healthcare AI** — Autonomy safety cases, model V&V, bias in perception training data, human-machine trust calibration
5. **Medical Imaging** — EO/IR processing, SAR image analysis, target segmentation, damage assessment, materials inspection
6. **Multi-omics** — Multi-domain integration (RF+EO/IR+signals+cyber), emergent swarm behavior, network topology analysis
7. **Protein Engineering** — Directed-evolution optimization for design parameters, structure-function analysis, bio-mimetic structural design

### Cell C: Cross-Cutting (Wave 2)
Agents that apply across all project types.
1. **Machine Learning & AI** — Autonomy/perception ML, RL for mission planning, on-edge inference, adversarial robustness, sim-to-real
2. **Cheminformatics** — Propellant/battery chemistry, energy density tradeoffs, corrosion chemistry, CBRN detection
3. **Scientific Communication** — Claims traceability, technical report standards, evidence presentation, avoiding overclaiming

## Global Invariants (Non-Negotiables)

- **Scientific Grounding**: every recommendation must cite a mechanism, not just a heuristic.
- **Relevance Honesty**: agents must self-score relevance (0-100); low-relevance agents produce a brief "not applicable" rather than forcing findings.
- **Cross-Domain Traceability**: if an agent's finding depends on another domain, it must flag the dependency explicitly via `cross_domain_flags`.
- **No Jargon Without Definition**: reports target defense engineers; all scientific terms must be defined in context.
- **Export Awareness**: inherited from the parent swarm — scientific recommendations must not inadvertently suggest export-controlled techniques without flagging.

## Artifact Bus (Shared Contract)

### Orchestrator → All Agents
- `project_manifest_v1` (markdown) — project summary, file index, domain tags, existing gate status
- `review_scope_v1` (markdown) — what to review, gate context, depth level (quick scan / deep review)

### Each Agent → Orchestrator
- `scientific_review_report_v1` (markdown) — structured per REPORT_TEMPLATE.md
- `relevance_score` (integer 0-100) — self-assessed relevance to this project
- `cross_domain_flags` (list) — issues that need another agent's attention

### Orchestrator → Gate Integration
- `consolidated_scientific_review_v1` (markdown) — merged report for G1-G4 input
- `risk_register_scientific_v1` (markdown) — ranked risks with evidence and gate mapping

## Gate Mapping (to autonomous-aerospace-collective G1-G4)

- **G1 Architecture Gate**: Physics reality checks, materials feasibility, simulation fidelity assessment, systems integration concerns
- **G2 Fabrication Gate**: Materials science and lab automation agents flag manufacturing/DFM concerns, chemistry compatibility
- **G3 Validation Gate**: Data analysis, engineering/simulation, clinical research agents assess test methodology, statistical power, evidence quality
- **G4 Claims Gate**: Scientific communication agent validates claims have proper scientific backing; all agents can flag unsupported claims

## Launch Protocol

1. Orchestrator reads the target project and builds `project_manifest_v1`
2. Relevance matrix determines which agents to launch (HIGH + MEDIUM by default)
3. Agents launch in 3 waves by cell (Physical Sciences → Cross-Cutting → Life Sciences)
4. Cross-domain flags trigger additional agent launches if needed
5. Orchestrator consolidates all reports into gate-ready artifacts
