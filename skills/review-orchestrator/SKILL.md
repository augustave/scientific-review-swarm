---
name: review-orchestrator
type: skill
version: "1.0.0"
owner: scientific-review-lead
risk_level: low
intent: >
  Orchestrates the scientific review swarm — manages project discovery, agent selection
  via relevance matrix, parallel wave-based agent launch, report collection, cross-domain
  flag resolution, and consolidated report generation for gate integration.
inputs:
  - name: project_path
    type: text
    description: "Path to the defense-aerospace project to review."
  - name: review_depth
    type: enum
    values: [quick, deep]
    default: deep
    description: "Quick scan (top 3 findings per agent) or deep review (comprehensive)."
  - name: full_review
    type: boolean
    default: false
    description: "Launch all 15 agents regardless of relevance matrix."
outputs:
  - name: project_manifest_v1
    type: file/markdown
    description: "Project summary, file index, domain tags, existing gate status."
  - name: review_scope_v1
    type: file/markdown
    description: "What to review, gate context, depth level."
  - name: consolidated_scientific_review_v1
    type: file/markdown
    description: "Merged report from all agents, organized by gate and domain."
  - name: risk_register_scientific_v1
    type: file/markdown
    description: "Ranked risks with evidence, domain attribution, and gate mapping."
dependencies:
  knowledge: [relevance_matrix, report_template, swarm_definition, gate_mapping]
  agents:
    physical_sciences:
      - sci-materials-science
      - sci-physics-astronomy
      - sci-engineering-simulation
      - sci-data-analysis
      - sci-lab-automation
    cross_cutting:
      - sci-machine-learning
      - sci-cheminformatics
      - sci-scientific-communication
    life_sciences:
      - sci-bioinformatics
      - sci-proteomics
      - sci-clinical-research
      - sci-healthcare-ai
      - sci-medical-imaging
      - sci-multi-omics
      - sci-protein-engineering
ports:
  provides:
    - consolidated_scientific_review_v1
    - risk_register_scientific_v1
    - project_manifest_v1
  consumes:
    - scientific_review_report_v1  # from each agent
    - relevance_score              # from each agent
    - cross_domain_flags           # from each agent
  feeds_into:
    - autonomous-aerospace-collective/architect  # consolidated review → architecture decisions
    - autonomous-aerospace-collective/assurance  # risk register → validation priorities
---

# Review Orchestrator

## Definition of Done
- All selected agents have produced `scientific_review_report_v1` with self-assessed `relevance_score`
- All `cross_domain_flags` have been resolved (referenced agents launched and reported)
- `consolidated_scientific_review_v1` produced with findings organized by gate (G1-G4) and by domain
- `risk_register_scientific_v1` produced with all Critical and Major findings ranked
- Top 5 highest-impact findings identified and presented with executive summaries
- No Critical finding left without a specific, actionable recommendation
- Scientific terms defined for defense engineering audience throughout

## Orchestration Protocol

### Wave Launch Sequence
1. **Wave 1 (Physical Sciences)**: Launch up to 3 agents in parallel — Materials, Physics, Eng/Sim, Data Analysis, Lab Automation
2. **Wave 2 (Cross-Cutting)**: Launch after Wave 1 — ML/AI, Cheminformatics, Scientific Communication. Include Wave 1 cross-domain flags.
3. **Wave 3 (Life Sciences)**: Launch after Wave 2 — selected Life Sciences agents at MED+ relevance. Include all accumulated cross-domain flags.

### Cross-Domain Flag Protocol
- When Agent A flags Agent B: if Agent B is already running or completed, append the flag to their report context. If Agent B was skipped (LOW relevance), promote and launch.
- Cross-domain flags create a `cross_domain_interaction` entry in the consolidated report linking the two findings.

### Relevance Score Handling
- Score ≥ 80: Feature prominently in consolidated report
- Score 50-79: Include in consolidated report with standard weight
- Score 20-49: Include summary only, full report available on drill-down
- Score < 20: Include "Not Applicable" note only

### Gate Mapping Rules
- Every Critical/Major finding MUST be mapped to at least one gate (G1-G4)
- Minor/Informational findings MAY be mapped to a gate or left unmapped
- Findings that affect multiple gates should list all applicable gates
- Gate-mapped findings feed into `autonomous-aerospace-collective` gate checklists
