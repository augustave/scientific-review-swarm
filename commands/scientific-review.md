---
description: Launch a scientific review swarm against a defense-aerospace project — 15 scientific domain agents analyze your project from their specialized perspective
argument-hint: <path-to-project> [--full] [--depth quick|deep]
---

# Scientific Review Swarm

You are orchestrating a scientific review swarm — 15 specialized agents that each analyze a defense-aerospace project from their scientific domain's perspective. The swarm produces a consolidated review with findings mapped to G1-G4 gates.

## Configuration

- **SWARM definition**: Read `SWARM.md` in the plugin root for cell definitions, artifact bus, and invariants
- **Relevance matrix**: Read `docs/RELEVANCE_MATRIX.md` for agent selection per project type
- **Report template**: All agents follow `docs/REPORT_TEMPLATE.md`

## Input

Target project: $ARGUMENTS

If no path provided, ask the user which project to review.

---

## Phase 1: Project Discovery

**Goal**: Understand the target project and build the project manifest.

**Actions**:
1. Create todo list tracking all phases
2. Read the project's README.md, SWARM.md (if exists), CLAUDE.md, and key configuration files
3. Scan for domain indicators:
   - Swarm/distributed systems → "Drone Swarm" type
   - Airframe/avionics/flight sciences → "Aircraft Design" type
   - Radar/RF/sensor/SIGINT → "Radar/Sensing" type
   - Racing/gymnasium/RL → "Racing Drone" type
   - CONOPS/requirements/compliance → "Defense Docs" type
   - Digital twin/simulation/parametric → "Digital Twin" type
4. Build `project_manifest_v1`:
   ```
   Project: [name]
   Path: [path]
   Type(s): [detected types]
   Domain Tags: [extracted tags]
   Existing Gate Status: [if available]
   Key Files: [top 10 most relevant files]
   ```
5. Present the manifest to the user for confirmation

---

## Phase 2: Relevance Triage

**Goal**: Select which agents to launch based on the relevance matrix.

**Actions**:
1. Cross-reference the detected project type(s) against `docs/RELEVANCE_MATRIX.md`
2. If `--full` flag: select all 15 agents
3. Otherwise: select HIGH + MEDIUM relevance agents (typically 8-12 of 15)
4. Present the agent roster to the user:
   ```
   Selected Agents (HIGH):
   - sci-materials-science — Composites, thermal, fatigue, coatings
   - sci-engineering-simulation — FEA/CFD, V&V, uncertainty quantification
   [...]

   Selected Agents (MEDIUM):
   - sci-clinical-research — Test protocol rigor, evidence hierarchy
   [...]

   Skipped Agents (LOW):
   - sci-proteomics — Trace detection (low relevance for this project type)
   [...]
   ```
5. Ask user to confirm, add, or remove agents
6. Set review depth:
   - `--depth quick`: Agents do a rapid scan, focus on top 3 findings each
   - `--depth deep` (default): Full review with comprehensive findings

---

## Phase 3: Parallel Agent Launch

**Goal**: Launch agents in 3 waves by cell.

**Actions**:

### Wave 1: Physical Sciences Cell
Launch these agents in parallel (up to 3 at a time):
- `sci-materials-science`
- `sci-physics-astronomy`
- `sci-engineering-simulation`
- `sci-data-analysis`
- `sci-lab-automation`

Each agent receives this prompt:
```
You are reviewing a defense-aerospace project as part of the scientific-review-swarm.

PROJECT MANIFEST:
[insert project_manifest_v1]

REVIEW SCOPE:
- Depth: [quick/deep]
- Gate context: [relevant gates]
- Your domain: [agent's scientific domain]

INSTRUCTIONS:
1. Read the key project files listed in the manifest
2. Analyze the project from your scientific domain's perspective
3. Produce a structured report following the REPORT_TEMPLATE format
4. Self-assess your relevance score (0-100)
5. Flag any cross-domain issues for other agents
6. Focus on defense-aerospace applicability — don't force findings where your domain doesn't apply
```

### Wave 2: Cross-Cutting Cell
After Wave 1 completes, launch:
- `sci-machine-learning`
- `sci-cheminformatics`
- `sci-scientific-communication`

Include Wave 1 cross-domain flags in their briefing.

### Wave 3: Life Sciences Cell
After Wave 2 completes, launch relevant Life Sciences agents:
- `sci-bioinformatics`
- `sci-clinical-research`
- `sci-healthcare-ai`
- `sci-medical-imaging`
- `sci-multi-omics`
- `sci-proteomics`
- `sci-protein-engineering`

Include all accumulated cross-domain flags in their briefing.

**Cross-domain escalation**: If any agent flags a LOW-relevance agent via `cross_domain_flags`, promote and launch that agent in the next wave.

---

## Phase 4: Report Collection & Cross-Domain Resolution

**Goal**: Gather all reports and resolve cross-domain flags.

**Actions**:
1. Collect `scientific_review_report_v1` from each agent
2. Collect `relevance_score` and `cross_domain_flags` from each agent
3. If unresolved cross-domain flags remain, launch the referenced agents
4. Sort all findings by severity (Critical > Major > Minor > Informational)
5. Identify the **top 5 highest-impact findings** across all agents

---

## Phase 5: Consolidation

**Goal**: Merge all reports into gate-ready artifacts.

**Actions**:
1. Build `consolidated_scientific_review_v1`:
   ```markdown
   # Consolidated Scientific Review
   ## Project: [name]
   ## Date: [ISO date]
   ## Agents Deployed: [count] / 15
   ## Total Findings: [count by severity]

   ### Top 5 Highest-Impact Findings
   [ranked list with agent attribution]

   ### Findings by Gate
   #### G1 Architecture Gate
   [all G1-tagged findings]
   #### G2 Fabrication Gate
   [all G2-tagged findings]
   #### G3 Validation Gate
   [all G3-tagged findings]
   #### G4 Claims Gate
   [all G4-tagged findings]

   ### Findings by Domain
   [each agent's report summary with relevance score]

   ### Cross-Domain Interactions
   [findings that span multiple domains]

   ### Opportunities Summary
   [aggregated opportunities ranked by impact and feasibility]
   ```

2. Build `risk_register_scientific_v1`:
   ```markdown
   | # | Risk | Severity | Domain | Gate | Description | Recommendation |
   |---|------|----------|--------|------|-------------|----------------|
   ```

---

## Phase 6: Presentation

**Goal**: Present results and offer next actions.

**Actions**:
1. Present the **Top 5 Findings** with executive summaries
2. Present the **Risk Register** sorted by severity
3. Show the **Gate Mapping** — what needs to be addressed before each gate
4. Offer drill-down options:
   - "Show me the full [agent name] report"
   - "Expand on finding #N"
   - "Show all G3 findings"
5. Offer export options:
   - Save consolidated review as markdown
   - Save risk register as markdown/CSV
   - Feed findings into the autonomous-aerospace-collective artifact bus
6. Mark all todos complete and summarize

---

## Notes

- **Respect agent relevance honesty**: If an agent returns relevance < 20, include their "Not Applicable" section but do not feature their findings prominently
- **No forced findings**: It is better for an agent to report "this domain does not significantly apply" than to manufacture marginal findings
- **Evidence required**: Every Critical or Major finding must include specific file paths, line numbers, or data points as evidence
- **Terminology bridging**: When presenting cross-domain findings, ensure scientific terms are defined for defense engineers
