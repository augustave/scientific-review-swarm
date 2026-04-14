# Gate Integration Guide

How the scientific-review-swarm feeds into the autonomous-aerospace-collective's G1-G4 gate process.

---

## Architecture

```
scientific-review-swarm                    autonomous-aerospace-collective
========================                   ================================

15 Scientific Agents                       4 Cells + Lab Engineer
        │                                          │
        ▼                                          │
  Orchestrator                                     │
        │                                          │
        ├── consolidated_scientific_review_v1 ───► Architect Cell
        │                                          │
        └── risk_register_scientific_v1 ─────────► Assurance Core Cell
                                                   │
                                            G1 ── G2 ── G3 ── G4
```

## Gate Mapping

### G1 Architecture Gate
**Scientific contributions**: Physics reality checks, materials feasibility, simulation fidelity, systems integration

**Primary agents**:
- `sci-physics-astronomy` — Validates physics models, orbital mechanics, RF calculations
- `sci-materials-science` — Assesses materials selection for the operating environment
- `sci-engineering-simulation` — Evaluates simulation credibility for design decisions
- `sci-multi-omics` — Analyzes system-of-systems integration and emergent behavior

**Integration point**: Scientific findings tagged G1 become additional items in the Architecture Gate checklist. The Architect cell must address Critical/Major findings before passing G1.

**Example**: If `sci-physics-astronomy` finds that the RF link budget uses incorrect atmospheric attenuation for the operating frequency, this blocks G1 until the link budget is corrected.

---

### G2 Fabrication Gate
**Scientific contributions**: Manufacturing feasibility, chemistry compatibility, materials processing

**Primary agents**:
- `sci-materials-science` — DFM assessment, composite cure specifications, material availability
- `sci-cheminformatics` — Battery chemistry safety, corrosion at dissimilar material interfaces
- `sci-lab-automation` — Fabrication quality control, inspection automation

**Integration point**: Scientific findings tagged G2 feed into the Foundry cell's fabrication readiness checklist. The Foundry cell must address findings before ordering components.

**Example**: If `sci-cheminformatics` identifies a thermal runaway risk in the selected battery pack configuration, this blocks G2 until the battery management system is redesigned.

---

### G3 Validation Gate
**Scientific contributions**: Test methodology rigor, statistical power, evidence quality, measurement validity

**Primary agents**:
- `sci-clinical-research` — Test protocol rigor, statistical power, bias identification
- `sci-data-analysis` — Statistical methods, sensor fusion validation, data quality
- `sci-engineering-simulation` — Simulation V&V, uncertainty quantification
- `sci-lab-automation` — Test automation coverage, calibration management, data provenance

**Integration point**: Scientific findings tagged G3 feed into the Assurance Core's validation checklist. The Assurance Core must address findings before claims are published.

**Example**: If `sci-clinical-research` finds that the test campaign is not statistically powered to detect the claimed performance difference, this blocks G3 until additional tests are designed or claims are reduced.

---

### G4 Claims Gate
**Scientific contributions**: Evidence-claim traceability, overclaiming detection, scientific backing

**Primary agents**:
- `sci-scientific-communication` — Claims validation, evidence quality, overclaiming detection
- All agents — Any agent can flag an unsupported claim in their domain

**Integration point**: Scientific findings tagged G4 are checked against the claims schema:
- `claim_id` — unique identifier
- `evidence_ref` — artifact path
- `test_run_id` — run identifier
- `artifact_hash` — SHA-256 hash of evidence artifact

Every claim flagged by the scientific review must either be supported by evidence meeting the claims schema or be withdrawn/qualified.

**Example**: If `sci-scientific-communication` finds a "best-in-class detection range" claim with no quantitative comparison to competitors and no statistical confidence interval, this blocks G4 until the claim is either substantiated or reworded.

---

## Release Authority Extension

Add "Scientific Review Lead" as a signoff role in `docs/release_authority.md`:

| Gate | Existing Signatories | + Scientific Review Lead |
|------|---------------------|--------------------------|
| G1 | Architect | Advisory (can flag but not block) |
| G2 | Foundry Lead | Advisory (can flag but not block) |
| G3 | Assurance Core Lead | **Required signoff** for validation methodology |
| G4 | Swarm Lead | **Required signoff** for claims scientific backing |

The Scientific Review Lead signs off based on the `consolidated_scientific_review_v1` — specifically that all Critical findings have been resolved and all Major findings have been addressed or accepted with documented rationale.

---

## Invariant Strengthening

The scientific review swarm strengthens these existing invariants:

| Existing Invariant | Strengthened By | How |
|--------------------|----------------|-----|
| Physics Reality | sci-physics-astronomy, sci-engineering-simulation | Independent physics model validation |
| Traceability | sci-clinical-research, sci-scientific-communication | Evidence hierarchy assessment, claims validation |
| No "Random Glitch" Closure | sci-data-analysis, sci-clinical-research | Root cause analysis rigor, confounding variable identification |
| MOSA Discipline | sci-multi-omics, sci-protein-engineering | Module coupling analysis, interface quality assessment |
| Export & Compliance | All agents | Export awareness invariant — flag controlled techniques |

---

## Workflow

1. Run `/scientific-review <project-path>` to launch the swarm
2. Orchestrator produces `consolidated_scientific_review_v1` and `risk_register_scientific_v1`
3. These artifacts enter the autonomous-aerospace-collective artifact bus
4. Architect cell reviews scientific findings when preparing for G1
5. Foundry cell reviews when preparing for G2
6. Assurance Core reviews when preparing for G3
7. Scientific Review Lead provides signoff for G3 and G4
8. All Critical findings must be resolved before gate passage
9. Major findings must be addressed or accepted with documented rationale
