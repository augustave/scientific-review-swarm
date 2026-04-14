# Scientific Review Swarm — Relevance Matrix

The orchestrator uses this matrix to determine which agents to launch for each project type.

**Default behavior:** Launch HIGH + MEDIUM agents. Skip LOW agents unless the user requests a full review.

## Matrix

| Agent | Drone Swarm | Aircraft Design | Radar/Sensing | Racing Drone | Defense Docs | Digital Twin |
|-------|:-----------:|:---------------:|:-------------:|:------------:|:------------:|:------------:|
| sci-materials-science | HIGH | HIGH | MED | HIGH | LOW | MED |
| sci-machine-learning | HIGH | MED | MED | HIGH | LOW | HIGH |
| sci-physics-astronomy | MED | HIGH | HIGH | MED | LOW | HIGH |
| sci-engineering-simulation | HIGH | HIGH | MED | HIGH | LOW | HIGH |
| sci-data-analysis | HIGH | MED | HIGH | MED | MED | HIGH |
| sci-lab-automation | MED | HIGH | MED | MED | LOW | MED |
| sci-bioinformatics | HIGH | LOW | LOW | MED | LOW | MED |
| sci-cheminformatics | LOW | MED | LOW | MED | LOW | LOW |
| sci-proteomics | LOW | LOW | HIGH | LOW | LOW | LOW |
| sci-clinical-research | MED | MED | LOW | LOW | MED | MED |
| sci-healthcare-ai | MED | MED | LOW | MED | LOW | MED |
| sci-medical-imaging | MED | LOW | HIGH | MED | LOW | MED |
| sci-scientific-communication | MED | MED | MED | MED | HIGH | MED |
| sci-multi-omics | HIGH | MED | MED | LOW | LOW | HIGH |
| sci-protein-engineering | LOW | MED | LOW | LOW | LOW | LOW |

## Project Type Detection

The orchestrator classifies projects by scanning for these indicators:

### Drone Swarm
- Keywords: swarm, formation, distributed, multi-agent, coordination, consensus
- Files: simulation configs, swarm parameters, communication protocols

### Aircraft Design
- Keywords: airframe, avionics, flight sciences, aerodynamics, propulsion, SWaP
- Files: architecture specs, power budgets, interface control docs

### Radar/Sensing
- Keywords: radar, RF, sensor, detection, imaging, SAR, EO/IR, SIGINT
- Files: link budgets, signal processing code, sensor specifications

### Racing Drone
- Keywords: racing, gymnasium, reinforcement learning, PPO, gate, track
- Files: RL policies, physics simulation, reward functions

### Defense Docs
- Keywords: CONOPS, requirements, claims, validation, compliance, ITAR
- Files: defense-readiness docs, test plans, risk registers

### Digital Twin
- Keywords: digital twin, simulation, model, virtual, parametric
- Files: 3D models, simulation configs, engineering analysis

## Override Rules

1. User can always force inclusion of any agent regardless of relevance score
2. User can request "full review" to launch all 15 agents
3. Cross-domain flags from running agents can promote a LOW agent to launch
4. If a project spans multiple types, use the highest relevance score for each agent
