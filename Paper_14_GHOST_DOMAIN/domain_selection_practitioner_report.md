# From Smart Farms to Warhammer 40K:
# A Practitioner's Guide to Domain Selection in Semantic Camouflage

## 0. Executive Summary

Semantic Camouflage is not ordinary anonymization. Its practical value comes from moving a sensitive source problem into a semantically distant but structurally equivalent virtual domain, then forcing the external model to reason only inside that virtual domain.

This report summarizes the documented GHOST_DOMAIN usage notes and mapping examples as a practitioner-facing appendix. The main lesson is simple:

> The best ghost domain is not the most exotic domain. It is the domain whose entities, relations, failure modes, roles, and decision rituals naturally match the source domain while remaining far away in surface semantics.

For academic UKBP-style literature analysis, the project notes mark GHOST_DOMAIN as OFF because the source data is not inherently sensitive. For sensitive trading, private operations, personal data, internal infrastructure, or proprietary strategy analysis, domain camouflage remains the preferred protection layer.

## 1. Why Domain Selection Matters

A poor ghost domain hides words but damages reasoning. A good ghost domain hides the source domain while preserving the task topology:

- entities remain entities;
- causal links remain causal links;
- hierarchy remains hierarchy;
- constraints remain constraints;
- failure modes remain diagnosable;
- model outputs can be reversed without semantic loss.

This is why GHOST_DOMAIN uses a bijective session dictionary, a dynamic domain rotator, a cognitive confinement prompt, a leakage guard, and a reverse restore step. The domain is not decoration. It is the temporary reasoning universe.

## 2. Domain Selection Matrix

The distance score below is a practitioner heuristic, not an empirical privacy guarantee. A higher score means greater surface-semantic distance from the source domain, assuming the mapping is implemented with a bijective session dictionary and local-only restoration table.

| Source domain | Strong ghost domain | Heuristic semantic distance | Why it fits | Watch-outs |
|---|---|---:|---|---|
| IT infrastructure / SRE / operations | CHEF | 0.88 | Servers become ovens, CPU load becomes heat, load balancing becomes heat redistribution, incident recovery becomes failed-dish recovery. The operational workflow is intuitive. | Avoid culinary metaphors that collapse distinct infrastructure roles into one vague "kitchen" concept. |
| Cross-domain knowledge mapping / literature topology | FARMER | 0.83 | Papers become seed lots, citations become graft relations, topic clusters become field sections, validation becomes harvest testing. Growth, propagation, and yield map well to research diffusion. | For non-sensitive academic UKBP data, direct transmission may be better because camouflage adds friction without privacy gain. |
| Machine fault diagnosis / vibration / sensor anomalies | MUSICIAN | 0.79 | Vibration anomaly becomes dissonance, bearing wear becomes string fatigue, calibration becomes tuning, stable state becomes harmonic lock. Signal quality maps naturally to sound quality. | Strong for diagnosis, weaker for inventory, ownership, or regulatory metadata. |
| Software architecture / module dependency / system design | ARCHITECT | 0.46 | Modules become rooms, APIs become corridors, dependencies become beams, bottlenecks become blocked passages. Spatial reasoning helps preserve structure. | Semantic distance is lower because architecture is already common software language. Use only when utility matters more than maximum concealment. |
| Network health / distributed failure / service circulation | DOCTOR | 0.74 | Traffic becomes circulation, overloaded nodes become inflamed organs, bottlenecks become clots, symptoms become clinical signs. Diagnosis vocabulary is rich. | Medical language can invite overly causal conclusions; guard against false certainty. |
| Trading strategy / private execution history / sensitive performance data | Rotating CHEF / FARMER / MUSICIAN / COACH | 0.78-0.91 | Rotating practical domains reduce repeated-pattern exposure while keeping enough workflow structure for evaluation, ranking, and recommendations. | Rotation can make longitudinal comparison harder; keep internal audit IDs and local-only mapping tables. |
| Neural circuits / cognitive architecture / agentic control networks | WARHAMMER 40K / Forge World / Noosphere | 0.94 | Neurons become machine spirits, circuits become noospheric conduits, synchronization becomes rites of alignment. Fictional worldbuilding can strongly confine the model's cognitive path. | High expressiveness increases lore drift. Use strict schemas and block free-form lore expansion. |
| Server administration / permissions / security rituals | WIZARD / SPACE EMPIRE / TEMPLE | 0.86-0.93 | Admin approval, shields, access gates, rituals, curses, and fleets map well to permissions, firewalling, deployment, and process control. | Fiction domains are useful for confinement but require stronger leakage and hallucination checks. |

## 3. Practical Heuristics

### 3.1 Match topology before vocabulary

Do not start by asking "what is a cute replacement for server?" Start by listing the source topology:

- primary entities;
- secondary entities;
- roles;
- state variables;
- recurring processes;
- failure modes;
- evaluation criteria;
- acceptable output actions.

Only after that should a ghost domain be chosen.

### 3.2 Prefer domains with real workflows

CHEF works because kitchens have heat, timing, ingredients, bottlenecks, quality control, and senior roles. FARMER works because fields have propagation, seasons, grafts, yield, and validation. MUSICIAN works because instruments have tuning, resonance, fatigue, noise, and harmony.

A domain with only aesthetic flavor but no workflow usually fails as camouflage.

### 3.3 Maintain semantic distance

The ghost domain should not share obvious vocabulary with the source domain. For example, using "digital twin factory" to hide software infrastructure is weak because the surface language remains close to engineering. Using a kitchen, farm, orchestra, hospital, temple, or fiction empire creates more distance.

The rotator should prefer domains with low overlap against recently used domains. A Jaccard-distance style filter is useful because repeated camouflage domains can become a fingerprint.

### 3.4 Keep the mapping reversible

Every active mapping must be bijective inside the session dictionary. If two source terms map to one ghost term, reverse restoration becomes lossy. If one source term maps to multiple ghost terms, the external model can fragment the concept and produce inconsistent recommendations.

The local mapping table should remain on the secure side only. External models should see ghost IDs and virtual-domain descriptions, not raw identifiers.

### 3.5 Constrain the model's cognitive path

The system prompt should say that all user data belongs only to the virtual domain and that the model must not infer, discuss, or reconstruct the original domain. This is especially important for fiction domains such as Warhammer 40K, where the model may otherwise start adding lore instead of solving the structural task.

Strict JSON output helps. Free-form prose increases leakage and drift.

## 4. Lessons From Automation

### 4.1 Manual camouflage does not scale

Hand-written metaphor prompts are fragile. They work for demos but fail under repeated use because terms drift, mappings become inconsistent, and reverse restoration becomes ambiguous. The automated pipeline should produce a `MappingBundle` with:

- source domain;
- target domain;
- session seed;
- source-to-target dictionary;
- target-to-source dictionary.

### 4.2 Ghost IDs are safer than expressive labels

The integrated pipeline's `ghost_id` pattern is important. A ghost ID lets the external model compare and score items without seeing raw names. Expressive labels may help reasoning, but they also increase accidental disclosure risk.

### 4.3 Fiction domains are powerful but unstable

Warhammer 40K, wizard schools, space empires, and temples are strong for cognitive confinement because they pull the model far from the original domain. They are best when the source topology is abstract, agentic, ritualized, or networked.

The trade-off is lore drift. Fiction domains should be used with:

- tight role prompts;
- schema-only outputs;
- leakage checks;
- short task windows;
- local-only reverse restoration.

IP notice: Warhammer 40,000 is a trademarked fictional setting owned by Games Workshop Ltd. It is referenced here only as an academic example of high-distance virtual-domain structure. Production deployments should prefer custom-generated fictional domains or internally owned world models to avoid operational dependence on third-party intellectual property.

### 4.4 Rotation protects against frequency analysis

If the same sensitive operation is always converted into the same ghost domain, the camouflage itself becomes recognizable. Dynamic rotation reduces this risk by changing the virtual world per session or request.

The cost is comparability. Internal logs should preserve stable audit IDs so that analysts can compare results across rotated sessions without exposing those IDs externally.

### 4.5 Leakage guards catch symptoms, not the whole disease

A token-level cognitive guard can block obvious leaks such as source-domain terms, company names, identifiers, or technical vocabulary. It does not fully catch conceptual leakage. A mature evaluation should include semantic leakage tests: can a separate reviewer infer the original domain from the ghost transcript?

### 4.6 Failed mappings are data, not embarrassment

A failed ghost domain usually fails for structural reasons, not because the metaphor was insufficiently clever. One common failure pattern is applying MUSICIAN to people-management or HR performance analysis. The source domain contains reporting lines, incentives, tenure, evaluation politics, role seniority, and policy constraints. MUSICIAN can express harmony and dissonance, but it does not naturally preserve authority, accountability, promotion criteria, or compliance boundaries.

In that case, a COACH, HOSPITAL, COURT, or SCHOOL domain may preserve the role structure better. The failure teaches the central rule again: topology first, vocabulary second.

## 5. Automation Adoption Timeline

| Phase | Typical duration | Operating mode | What changes | Exit criterion |
|---|---:|---|---|---|
| Phase 1: Manual camouflage | 1-2 weeks | Human-written CHEF/FARMER/MUSICIAN prompts | Teams learn which source structures survive translation and which metaphors collapse. | At least three repeatable mappings produce useful restored outputs. |
| Phase 2: Semi-automated bundles | 3-4 weeks | Template-driven mapping dictionaries and local restore tables | Mapping drift is reduced; ghost IDs become standard; reviewers can audit restoration. | Restore accuracy is high enough that manual correction is rare. |
| Phase 3: Automated rotation | 4-8 weeks | Domain pool, rotator, cognitive guard, reverse restore pipeline | Session-level rotation reduces repeated-pattern exposure; leakage checks block obvious failures. | Multiple domains produce stable task decisions under leakage thresholds. |
| Phase 4: Operational hardening | ongoing | Evaluation harness and audit logs | Semantic leakage tests, drift scoring, and analyst review time are tracked. | The system can justify both privacy posture and task utility to a reviewer. |

## 6. Suggested Evaluation Metrics

| Metric | Question | Target |
|---|---|---|
| Restore accuracy | Can outputs be mapped back without ambiguity? | Near 100% for controlled terms |
| Leakage ratio | How many source-domain terms appear in the model output? | Below configured block threshold |
| Semantic leakage | Can another model or human infer the source domain? | Low inference confidence |
| Task utility | Does the ghost answer still solve the original task after restoration? | Comparable to direct baseline |
| Domain drift | Did the model add irrelevant ghost-world lore? | Minimal |
| Analyst audit time | How long does a human need to verify restoration? | Lower than manual anonymization |
| Rotation robustness | Do outputs remain stable across different ghost domains? | Stable recommendation class |

## 7. Appendix Structure for Paper Use

This material can be attached to the main patent paper as a practitioner appendix:

- Appendix A: Domain Selection Matrix
- Appendix B: Mapping Bundle Schema
- Appendix C: Operational Prompts and Cognitive Confinement
- Appendix D: Leakage and Restore Evaluation
- Appendix E: Case Notes from CHEF, FARMER, MUSICIAN, and Fiction Domains

If used as a standalone technical report, the strongest positioning is:

> This report bridges the gap between the formal claim of semantic camouflage and the daily engineering question: "Which virtual world should I choose for this sensitive source problem?"

## 8. Case Notes

### CHEF: operational systems

CHEF is the most practical default for IT and operations because heat, timing, ingredients, stations, senior roles, and recovery rituals map well to infrastructure. It is easy for general-purpose LLMs to reason inside the domain without needing special lore.

### FARMER: research propagation and UKBP-style mapping

FARMER is excellent for literature graphs, knowledge propagation, and validation workflows. Seeds, grafts, fields, and harvests preserve the structure of ideas spreading and being tested.

For UKBP specifically, project rules say to keep GHOST_DOMAIN off when the data is ordinary academic material. The same FARMER mapping becomes valuable when the literature graph is mixed with private strategy, proprietary scoring, or sensitive internal labels.

### MUSICIAN: signal quality and fault diagnosis

MUSICIAN is strong when the source task is about signal quality, resonance, calibration, instability, or anomaly diagnosis. It gives the model a natural vocabulary for subtle changes without exposing machine data.

### WARHAMMER 40K: high-distance cognitive confinement

Warhammer 40K-style Forge World and Noosphere language is useful when the source domain is abstract, networked, and agentic. It can preserve relations between circuits, spirits, rites, synchronization, and control loops while moving far away from technical vocabulary.

This mode is best treated as a high-distance confinement mode, not a default business workflow. It should be paired with strict output schemas and aggressive leakage checks.

### Failed MUSICIAN mapping: HR performance analysis

MUSICIAN can describe tension, rhythm, and harmony, but it struggles when the source problem depends on formal responsibility and institutional power. HR performance analysis needs reporting hierarchy, evaluation rules, tenure, incentives, role expectations, and policy constraints. If those are flattened into "band members" and "tracks," the model may produce fluent but structurally weak advice.

The better replacement is a domain with explicit authority and evaluation structure, such as COACH for team performance, SCHOOL for grading and curriculum, COURT for procedural judgment, or HOSPITAL for triage and care responsibility.

## 9. Bottom Line

The practitioner rule is:

> Choose the ghost domain that makes the external model competent in the fake world while making it ignorant of the real one.

Smart farms, orchestras, kitchens, hospitals, temples, and Warhammer-style noospheres are not interchangeable skins. Each is a different reasoning substrate. The core engineering task is to select the substrate whose structure matches the source problem closely enough for utility, while remaining semantically distant enough for protection.

## Trademark Notice

All third-party trademarks referenced in this document are the property of their respective owners and are used here solely for academic illustration.
