# Scientific Risk Register: MINI-D

## Project: MINI-D | Date: 2026-04-13 | Agents: 10/15

| # | Risk | Severity | Domain | Gate | Description | Recommendation |
|---|------|----------|--------|------|-------------|----------------|
| R-01 | ProofConsole fabricated verification data | Critical | Sci Comm, Data | G4 | Hardcoded `Math.random()` and toy formulas displayed as "proof" with paper citations and "99.8% integrity" | Remove, label as illustrative, or wire to real engine output |
| R-02 | Zero uncertainty quantification | Critical | Eng Sim, Data, ML, Clinical | G3, G4 | All metrics are point estimates. No CI, no variance, no error bars. Claims near thresholds are statistically meaningless. | Ensemble runs (N>=20), track variance, report CIs |
| R-03 | CoV "95% N=5" label is false | Critical | Sci Comm, Data, Clinical | G4 | 3 seeds, majority vote, labeled "95% confidence (N=5 Seeds)" — both numbers wrong | Fix label, increase seeds to 20+, use binomial test |
| R-04 | Uniform drift ≠ Gaussian (3.5x underestimate) | Critical | Eng Sim, ML | G1 | `(rng()-0.5)*sigma` produces uniform, not Gaussian. Named `driftSigma`. Underestimates tail events by 3.5x | Implement Box-Muller Gaussian RNG |
| R-05 | Claim ID namespace collision | High | Sci Comm | G4 | C-001..C-009 (docs) vs C1..C7 (code) with no mapping. Auditors cannot trace claims. | Unify claim registry, add cross-references |
| R-06 | No artifact hashes on evidence | High | Sci Comm, Lab Auto | G4 | G4 requires SHA-256 `artifact_hash`. Only DJB2 config hash exists. No `test_run_id` or `evidence_ref`. | Add SHA-256 hashing, structured evidence fields |
| R-07 | E3_SIZE missing from golden fixtures | High | Clinical | G3 | Only BASELINE, E1, E2, E4 have golden fixtures. E3 is tested but has no regression baseline. | Add E3 to `generate_golden.ts` SCENARIOS |
| R-08 | Forward Euler without stability analysis | High | Eng Sim | G1 | Repulsion force 400 at dt=0.1 can overshoot 15px repulsion zone in one step. No convergence study. | Add velocity-Verlet or RK2, cap force impulse, test dt convergence |
| R-09 | Single-seed phase diagram (N=1) | High | Data, Clinical | G3 | All 50 grid points evaluated on seed 12345. Phase boundary determined by one realization. | Run 10+ seeds per point, color by pass probability |
| R-10 | No safety case for autonomous dispatch | Medium | Healthcare AI | G1 | No GSN, no FMEA, no structured safety argument. Threat model covers repo risks, not dispatch logic. | Build minimal GSN safety case skeleton |
| R-11 | E4 confounds 3 variables | Medium | Clinical | G3 | E4 changes towers + density + range simultaneously. Cannot isolate individual contributions. | Factorial design (2^3 = 8 runs) |
| R-12 | Wind model: no turbulence/gusts/spatial variation | Medium | Eng Sim, Materials, ML | G1 | `sin(t*0.1)*vol*5` — smooth, periodic, spatially uniform. `gust_sensitivity` defined but unused. | Add Dryden or Perlin noise turbulence |
| R-13 | Centralized dispatch (scalability bottleneck) | Medium | Bioinformatics, ML | G1 | O(N*M) global scoring. No bio-inspired alternative. Single point of failure. | Implement stigmergy/ACO/quorum sensing |
| R-14 | No pre-registration / protocol locking | Medium | Clinical | G3 | Thresholds appear post-hoc. No locked protocol with timestamp. | Add `protocol_lock.json` with SHA-256 |
| R-15 | Hardcoded `timeSinceFix=5.0` | Medium | Eng Sim, ML | G1 | Nullifies time-growth drift model. `t0` ranges 45-160s but t is always 5. | Track `lastFixTime` per drone |
| R-16 | No evidence hierarchy in claims | Medium | Sci Comm, Clinical | G4 | No distinction between automated, manual, and documentation evidence types | Add Evidence Type column |
| R-17 | No swarm-level safe state | Medium | Healthcare AI | G1 | Individual failsafes exist but no collective safety invariant | Define collective safety threshold |
| R-18 | SpatialHash hardcoded 800x600 | Medium | Eng Sim | G1 | Not updated on resize. Out-of-bounds entities cluster at edges. | Add resize() method |
| R-19 | Landing lerp is frame-rate dependent | Medium | Eng Sim | G1 | `lerp(x, target, dt*speed)` not frame-rate invariant. Use `1-exp(-rate*dt)` | Replace with exponential decay |
| R-20 | No operator confidence display | Medium | Healthcare AI | G3 | p_drop, p_detect, failure reasons computed but not shown in UI | Surface dispatch diagnostics panel |
