# Scientific Review Report Template

All agents in the scientific-review-swarm produce reports following this structure.

---

```markdown
# Scientific Review: [Domain Name]
## Project: [Project Name]
## Reviewer: [Agent Name]
## Date: [YYYY-MM-DD]
## Relevance Score: [0-100]

---

### Executive Summary
[2-3 sentences describing overall assessment from this domain's perspective. State the most important finding upfront.]

---

### Findings

#### Finding 1: [Descriptive Title]
- **Severity:** Critical / Major / Minor / Informational
- **Category:** Risk / Opportunity / Gap / Recommendation
- **Gate Relevance:** G1 / G2 / G3 / G4 / None
- **Description:** [What was found — be specific, reference file paths and line numbers]
- **Evidence:** [File paths, code snippets, data points, or document sections that support this finding]
- **Scientific Basis:** [The mechanism or principle from this scientific domain that makes this significant. Define any domain-specific terms.]
- **Recommendation:** [Specific, actionable recommendation]
- **Cross-Domain Flag:** None / [Agent name + brief reason why their perspective is needed]

#### Finding 2: [Title]
[Repeat structure for each finding]

---

### Opportunities
[Scientific approaches from this domain that could improve the project. Each opportunity should include:]
- What the opportunity is
- Why it applies to this defense-aerospace context
- Expected impact (quantify if possible)
- Implementation complexity (low / medium / high)

---

### Not Applicable
[Aspects of this scientific domain that do NOT apply to this project, with brief rationale. This section is mandatory — it demonstrates relevance honesty and prevents forced findings.]

---

### References
[Papers, standards, databases, or data sources consulted during the review. Include DOIs or URLs where available.]
```

---

## Severity Definitions

| Severity | Definition | Gate Impact |
|----------|-----------|-------------|
| **Critical** | Fundamental scientific flaw that could cause mission failure, safety hazard, or invalid claims | Blocks gate passage |
| **Major** | Significant gap in scientific rigor that weakens the design, test methodology, or evidence base | Should be resolved before gate passage |
| **Minor** | Improvement opportunity that would strengthen the project but is not blocking | Track for future iteration |
| **Informational** | Observation or best practice suggestion from this scientific domain | No gate impact |

## Category Definitions

| Category | Definition |
|----------|-----------|
| **Risk** | Something that could go wrong — a vulnerability, weakness, or failure mode identified through this scientific lens |
| **Opportunity** | Something that could be better — an approach, technique, or method from this domain that would improve the project |
| **Gap** | Something missing — a required analysis, test, or consideration that is absent |
| **Recommendation** | A specific action to take — a concrete improvement with clear implementation path |

## Relevance Score Guidelines

| Score Range | Meaning | Expected Report Depth |
|-------------|---------|----------------------|
| 80-100 | Core relevance — this domain is central to the project | Full report with multiple findings |
| 50-79 | Moderate relevance — several aspects of this domain apply | Focused report on applicable areas |
| 20-49 | Peripheral relevance — limited but real connection | Brief report with 1-2 key findings |
| 0-19 | Minimal relevance — domain barely applies | "Not Applicable" section only |
