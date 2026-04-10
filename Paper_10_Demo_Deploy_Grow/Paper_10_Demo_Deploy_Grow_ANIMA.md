# From Demo to Deploy to Grow: A Lifecycle Model for Self-Organizing AI Systems

**Author:** Myeong Jun Jo  
**Affiliation:** Meta-Convergence Graduate Program, ANIMA University  
**Date:** April 2026  
**Status:** Thesis Paper 2 — Submitted for Defense

---

## Abstract

Existing AI lifecycle models — MLOps, CRISP-DM, NIST AI RMF — assume systems that are designed, deployed, and maintained by human operators. They do not account for AI systems that self-organize, evolve beyond their original specification, and become part of larger computational ecosystems. We propose the **Demo-Deploy-Grow (DDG) lifecycle model**, a three-phase framework that extends conventional AI lifecycles with a formal "Grow" phase addressing self-organizing systems. The Demo phase (proof of concept in controlled environments) and Deploy phase (reliable operation under real-world conditions) are well-understood; our primary contribution is the formalization of the Grow phase, where systems evolve, form new capabilities, and participate in computational ecosystems. We introduce **transition gates** with formally specified criteria for phase advancement, a **governance gradient** that adapts oversight intensity to lifecycle stage, and a **regression protocol** for systems that must retreat from Grow to Deploy or from Deploy to Demo. We map all seven disciplines of a convergent AI education (formal methods, creative prototyping, cognitive science, decision theory, biodesign, cultural analytics, systems engineering) to specific lifecycle phases, showing that different disciplines dominate different phases. The model provides both a descriptive framework (understanding where existing systems are in their lifecycle) and a prescriptive framework (guiding teams through lifecycle transitions). We validate the model through analysis of three case studies representing systems at different lifecycle stages.

**Keywords:** AI lifecycle, self-organizing systems, MLOps, governance, computational ecosystems, regenerative design

---

## 1. Introduction

The lifecycle of an AI system — from initial conception through development, deployment, operation, and eventual retirement — is a central concern of AI engineering. Several lifecycle models exist. CRISP-DM (Wirth & Hipp, 2000) defines six phases for data mining projects. MLOps practices (Kreuzberger et al., 2023) extend software DevOps to machine learning, adding continuous training and monitoring. The NIST AI Risk Management Framework (NIST, 2023) organizes lifecycle governance around Map, Measure, Manage, and Govern functions.

These models share a critical assumption: **the system's boundaries are fixed by its designers.** A machine learning model may be retrained on new data, but it does not spontaneously develop new capabilities, recruit new components, or reorganize its architecture. The lifecycle is a human-managed pipeline, not an organic process.

This assumption is increasingly violated. Modern AI systems exhibit self-organizing behavior:
- Large language models develop emergent capabilities not explicitly trained (Wei et al., 2022)
- Multi-agent systems form coalitions and develop communication protocols not specified by designers (Foerster et al., 2016)
- AI systems deployed in complex environments adapt their behavior in ways that surprise their creators (Amodei et al., 2016)

As AI systems become more autonomous, adaptive, and interconnected, we need a lifecycle model that accounts for **growth** — not merely maintenance or retraining, but genuine evolution of capability, structure, and purpose.

**Contribution statement.** This paper makes four contributions:
1. We critique existing lifecycle models and identify their shared blind spot: the absence of a "growth" phase for self-organizing systems.
2. We propose the **Demo-Deploy-Grow (DDG)** model with formally specified phases and transition gates.
3. We introduce the **governance gradient** — a framework for adapting oversight intensity across lifecycle phases, addressing the fundamental challenge of governing systems that are changing themselves.
4. We map seven contributing disciplines to lifecycle phases, showing which disciplinary tools are most relevant at each stage and enabling multi-disciplinary lifecycle management.

---

## 2. Related Work

### 2.1 Existing AI Lifecycle Models

**CRISP-DM** (Wirth & Hipp, 2000) defines Business Understanding → Data Understanding → Data Preparation → Modeling → Evaluation → Deployment. The model is linear with feedback loops but treats deployment as the endpoint. There is no concept of post-deployment evolution beyond rerunning the pipeline. CRISP-DM remains the most widely adopted data science methodology (Saltz & Shamshurin, 2016), but its assumption of a stable deployment target is increasingly unrealistic.

**MLOps** (Kreuzberger et al., 2023) extends DevOps to machine learning, adding continuous training (CT) to continuous integration and delivery (CI/CD). The MLOps lifecycle is: Data Management → Model Development → Model Deployment → Model Monitoring → Model Retraining. This is a significant advance over CRISP-DM — it acknowledges that models degrade and need retraining. But retraining is corrective, not generative: it restores the model to its original specification rather than enabling it to grow beyond that specification.

**NIST AI RMF** (NIST, 2023) provides a governance framework organized around four functions: Map (context and risk identification), Measure (risk assessment), Manage (risk treatment), and Govern (oversight structures). The framework is comprehensive for risk management but does not address the lifecycle of self-organizing systems specifically. Its "Govern" function assumes human governance over a system with known boundaries.

**Model Cards and Datasheets** (Mitchell et al., 2019; Gebru et al., 2021) provide transparency documentation for AI systems, capturing intended use, limitations, and evaluation results. These are valuable for the Deploy phase but static — they describe a system at a point in time, not a system that is evolving.

### 2.2 Self-Organizing Systems

The study of self-organization has deep roots in cybernetics (Ashby, 1956), systems theory (von Bertalanffy, 1968), and complexity science (Holland, 1995; Kauffman, 1993). Heylighen (2001) provides a comprehensive account of self-organization in complex adaptive systems. Maturana and Varela's (1980) autopoiesis theory describes systems that produce and maintain themselves. These theoretical foundations describe the *phenomenon* of self-organization but do not provide lifecycle models for *engineering* self-organizing systems.

In AI specifically, multi-agent systems exhibit self-organizing behavior through emergent communication (Foerster et al., 2016), coalition formation (Shehory & Kraus, 1998), and distributed learning (Li et al., 2020). The challenge of governing emergent behavior in AI systems is well-recognized (Amodei et al., 2016) but not yet addressed through lifecycle models.

### 2.3 Biological Lifecycle Models

Biology offers lifecycle models for growing systems: embryology (development), ecology (ecosystem dynamics), and evolutionary biology (speciation and adaptation). Turner and Baker (2019) survey bio-inspired software lifecycle models. Regenerative design (Mang & Reed, 2012; Wahl, 2016) proposes that human-designed systems should not merely sustain but actively improve their environments. These biological models inform our "Grow" phase but require significant adaptation for computational systems.

---

## 3. The Demo-Deploy-Grow Model

### 3.1 Phase 1: Demo

**Definition.** The Demo phase is the period during which a system exists as a proof of concept, demonstrating capability in a controlled environment without production requirements.

**Characteristics:**
- Environment is controlled (sandbox, lab, limited users)
- Failures are acceptable and expected
- The goal is learning, not reliability
- Rapid iteration is prioritized over stability
- Metrics: "Does it work?" (capability demonstration)

**Dominant disciplines:**
- *Creative Prototyping (Program B)*: The ethos is "demo or die" — build fast, show results, iterate
- *Cognitive Science (Program C)*: Understanding how users perceive and interact with the system
- *Decision Theory (Program D)*: Evaluating whether the system's decision logic is sound in principle

**Governance model:** Minimal. The creator is the governor. Ethics review for research involving human subjects, but no production governance. This is the "anything goes" phase within ethical bounds.

**Anti-pattern:** Staying in Demo too long. "Perpetual prototype" syndrome — the system is always being improved but never deployed. The prototyping tradition's "demo or die" is explicitly anti-this: you must show it works.

### 3.2 Phase 2: Deploy

**Definition.** The Deploy phase is the period during which a system operates in a real environment, serving real users, with production-level reliability, safety, and governance requirements.

**Characteristics:**
- Environment is real (production, real users, real consequences)
- Failures have costs (financial, reputational, safety)
- Stability and reliability are prioritized
- Changes are controlled (CI/CD, staged rollouts, canary deployments)
- Metrics: "Does it work reliably, safely, at scale?"

**Dominant disciplines:**
- *Formal Methods (Program A)*: Production systems require verified correctness for critical paths
- *Systems Engineering (Program G)*: Full-stack reliability, monitoring, incident response
- *Cultural Analytics (Program F)*: The system's behavior must be interpretable and culturally appropriate for its user base

**Governance model:** Structured. Formal policies, audit trails, incident response procedures, regulatory compliance. The NIST AI RMF is well-suited to this phase. Human oversight is continuous and direct.

**Anti-pattern:** Over-engineering governance. "Red tape paralysis" — governance so heavy that the system cannot be updated, leading to staleness and eventual failure. The governance must be proportional to the risk.

### 3.3 Phase 3: Grow

**Definition.** The Grow phase is the period during which a system evolves beyond its original specification, developing new capabilities, forming new relationships, and participating in a computational ecosystem.

**Characteristics:**
- The system's boundaries are not fixed — it may recruit new components, form new connections, develop new capabilities
- Evolution is structural, not just parametric (the system changes its architecture, not just its weights)
- The system participates in an ecosystem — interacting with other systems, sharing resources, co-evolving
- Metrics: "Does it improve itself and its environment over time?" (the regenerative criterion)

**Dominant disciplines:**
- *Biodesign (Program E)*: Growth, adaptation, regeneration, ecosystem participation
- *Cognitive Science (Program C)*: Self-modeling, meta-cognition, adaptive learning strategies
- *Decision Theory (Program D)*: Meta-decision-making — the system decides how to decide

**Governance model:** Adaptive. The governance itself must evolve as the system evolves. We propose a **governance gradient**:

| Aspect | Demo | Deploy | Grow |
|--------|------|--------|------|
| Oversight | Creator | Structured team | Distributed + automated |
| Change control | None | Staged rollout | Behavioral envelope |
| Failure response | Iterate | Incident response | Self-repair + report |
| Metrics | Capability | Reliability | Regenerative capacity |
| Governance evolution | N/A | Version-controlled | Co-evolutionary |

The key innovation is the **behavioral envelope** (formalized in our companion paper, Thesis 1): the Grow phase system operates within a formally specified envelope of acceptable behaviors. Within the envelope, the system is free to self-organize. Crossing the envelope boundary triggers governance intervention.

**Anti-pattern:** Unmonitored growth. "Feral AI" — a system that grows without governance, developing capabilities that are unknown to its operators. The Grow phase is NOT "let the system do whatever it wants." It is governed growth — freedom within formal bounds.

### 3.4 Transition Gates

**Gate 1: Demo → Deploy (Readiness Gate)**

Criteria:
1. **Capability verified**: The system demonstrates its intended capabilities consistently (not just once)
2. **Risk assessed**: Known failure modes are documented with mitigation plans
3. **Governance ready**: Production governance structures are in place (monitoring, incident response, audit)
4. **User validation**: Target users have interacted with the system and confirmed value
5. **Engineering maturity**: The system meets production standards for the target environment (latency, uptime, security)

Formal condition: The system satisfies its specification Spec_deploy, verified through testing (Deploy readiness) or proof (critical systems).

**Gate 2: Deploy → Grow (Evolution Gate)**

Criteria:
1. **Stable operation**: The system has operated reliably for a defined period (stability proof)
2. **Growth capability**: The system has architectural capacity for self-modification (not hardcoded)
3. **Behavioral envelope defined**: Formal bounds on acceptable growth are specified and verifiable
4. **Ecosystem readiness**: The computational ecosystem can support and monitor the growing system
5. **Recovery mechanism**: The system can regress to Deploy phase if growth violates bounds
6. **Governance gradient**: Adaptive governance mechanisms are in place and tested

Formal condition: The system satisfies Spec_deploy (still production-quality) AND has a defined behavioral envelope Env such that Spec_min ⊆ Env ⊆ Spec_max, where Spec_min guarantees safety and Spec_max prevents harmful growth.

### 3.5 Regression Protocol

Systems can move backward through phases:

**Grow → Deploy (Growth Containment):**
- Triggered when: system exits its behavioral envelope, or monitoring detects concerning emergent behavior
- Process: freeze self-modification capabilities, activate full human oversight, investigate
- Recovery: expand the behavioral envelope (if growth was beneficial but unexpected) or restrict the system

**Deploy → Demo (Production Recall):**
- Triggered when: system fails production requirements, or a safety incident occurs
- Process: remove from production, return to controlled environment, diagnose
- Recovery: fix and re-deploy (re-pass Gate 1)

**Grow → Demo (Emergency Recall):**
- Triggered when: system's growth has compromised its core functionality
- Process: complete restart in controlled environment
- This is the "nuclear option" — expensive but necessary if governance has failed

---

## 4. The Seven-Discipline Lifecycle Map

### 4.1 Discipline Dominance by Phase

Each discipline contributes to all phases, but *dominates* specific phases:

| Discipline | Demo (primary) | Deploy (primary) | Grow (primary) |
|-----------|---------------|------------------|----------------|
| Formal Methods | Prototype specs | Production verification | Self-verification |
| Creative Prototyping | **Core innovation** | A/B testing | Evolutionary design |
| Cognitive Science | **User modeling** | User experience | **Adaptive cognition** |
| Decision Theory | **Decision logic** | Operational decisions | **Meta-decisions** |
| Biodesign | Proof of life | Environmental adaptation | **Regenerative growth** |
| Cultural Analytics | Demo narrative | **Cultural fit** | **Evolving identity** |
| Systems Engineering | Stack prototype | **Production stack** | Living infrastructure |

### 4.2 Cross-Phase Disciplines

Two disciplines span all phases equally:

**Formal Methods** transforms across phases:
- Demo: lightweight specification (what are we trying to build?)
- Deploy: production verification (does it meet requirements?)
- Grow: behavioral envelopes (what is the system allowed to become?)

**Cultural Analytics** transforms across phases:
- Demo: the story of what we're building (pitch, vision)
- Deploy: the story of what the system does for users (documentation, trust)
- Grow: the evolving narrative identity of the system (who is this system becoming?)

### 4.3 Phase Transition Discipline Shifts

At each transition gate, the dominant discipline shifts:

**Demo → Deploy:** Creative Prototyping hands leadership to Systems Engineering. The question shifts from "Does it work?" to "Does it work reliably?"

**Deploy → Grow:** Systems Engineering shares leadership with Biodesign. The question shifts from "Does it work reliably?" to "Does it improve?"

These shifts are not merely organizational — they represent fundamental changes in the epistemological framework governing the system. In Demo, knowledge is experimental. In Deploy, knowledge is operational. In Grow, knowledge is ecological.

---

## 5. Case Studies

### 5.1 Case Study 1: Large Language Models (Demo → Deploy)

Large language models illustrate the Demo → Deploy transition. GPT-3 (Brown et al., 2020) began as a research demo — impressive capability with unpredictable failure modes. Its evolution through GPT-3.5 and GPT-4 to ChatGPT represents a Demo → Deploy transition:
- Capability was refined through RLHF (Ouyang et al., 2022)
- Governance was added through content policies and Constitutional AI principles (Bai et al., 2022)
- Monitoring was established through user feedback systems
- Engineering maturity increased through optimization and scaling

However, these systems have NOT entered the Grow phase. They do not self-modify their architecture. They do not form autonomous relationships with other systems. Their evolution is entirely human-directed. By our model, they are firmly in Deploy.

### 5.2 Case Study 2: Federated Learning Systems (Early Grow)

Federated learning systems (McMahan et al., 2017; Li et al., 2020) exhibit early Grow-phase characteristics:
- Multiple nodes contribute to a shared model without central data collection
- The system's capabilities emerge from distributed participation
- New participants can join, changing the system's effective training distribution
- The system's behavior evolves as its ecosystem of participants changes

However, federated learning lacks key Grow-phase requirements: behavioral envelopes are not formally defined, ecosystem health is not monitored, and regression protocols are ad hoc. By our model, federated learning is at the Deploy-Grow boundary — exhibiting growth characteristics without growth governance.

### 5.3 Case Study 3: Biological Neural Networks (Full Grow)

The human brain is the paradigmatic Grow-phase system:
- It self-organizes (neuroplasticity, synaptic pruning)
- It forms new connections based on experience
- It participates in ecosystems (social networks, cultural environments)
- It improves its environment (through tool-making, communication, cooperation)
- It has governance mechanisms (prefrontal cortex executive control, social norms)

The brain's governance is instructive for AI: it is not centralized control but *distributed constraint satisfaction* — multiple competing and cooperating subsystems that collectively maintain behavioral coherence. This is the model for Grow-phase AI governance.

---

## 6. Discussion

### 6.1 The Governance Paradox

The Grow phase presents a fundamental paradox: **how do you govern a system that is changing the rules?**

In the Deploy phase, governance is straightforward: define rules, monitor compliance, enforce. But in the Grow phase, the system may legitimately need to change its own rules as it adapts to new circumstances. Governance must be:
- **Flexible enough** to permit beneficial evolution
- **Rigid enough** to prevent harmful deviation
- **Self-reflective** enough to know when flexibility is needed vs. when rigidity is needed

Our solution — the behavioral envelope — resolves this paradox at one level: the envelope defines the space of acceptable evolution. But the paradox recurs at a higher level: who defines the envelope? And what happens when the envelope itself needs to change?

We propose **meta-governance**: a governance layer that governs the evolution of governance itself. Meta-governance operates on a slower timescale than operational governance and involves broader stakeholder input. In the brain analogy: operational governance is moment-to-moment executive control; meta-governance is the slow reshaping of values and priorities through experience and reflection.

### 6.2 Failure Mode Analysis

| Failure Mode | Phase | Description | Detection | Recovery |
|-------------|-------|-------------|-----------|----------|
| Perpetual prototype | Demo | Never deploys | Time-in-phase exceeds threshold | Force Gate 1 review |
| Premature deployment | Demo→Deploy | Deploys before ready | Gate 1 criteria not met | Return to Demo |
| Governance paralysis | Deploy | Over-governed, cannot update | Performance degradation | Governance review |
| Premature growth | Deploy→Grow | Grows before stable | Gate 2 criteria not met | Restrict to Deploy |
| Feral growth | Grow | Unmonitored evolution | Envelope violation | Regression to Deploy |
| Growth collapse | Grow | System degrades through growth | Regenerative ratio < 1 | Regression + diagnosis |
| Ecosystem parasitism | Grow | System exploits its ecosystem | Symbiosis score drops | Isolate + restructure |

### 6.3 Relationship to Thesis 1

This lifecycle model is the **temporal counterpart** to the structural framework of Thesis 1 (Convergent Intelligence). Where Thesis 1 asks "what is the structure of a coherent multi-disciplinary design?" (a static question), this paper asks "how does a system move through phases that require different disciplinary emphases?" (a dynamic question).

The Integration Topos from Thesis 1 applies differently in each phase:
- **Demo**: The design need not be fully in the topos — some functor relationships may be temporarily violated
- **Deploy**: The design must be in the topos — all discipline components must be coherent
- **Grow**: The design must remain in the topos as the system evolves — coherence must be maintained through change

### 6.4 Limitations

1. **Validation gap**: The model is theoretical. Empirical validation requires tracking real AI systems through all three phases, which may take years.
2. **Grow phase immaturity**: Few AI systems have intentionally entered the Grow phase. Our formalization is based on biological analogy and extrapolation from early examples (federated learning, multi-agent systems).
3. **Governance scalability**: Our governance gradient is described at the conceptual level. Implementing adaptive governance for complex, large-scale systems requires operational research beyond this paper's scope.
4. **Cultural assumptions**: The model assumes values (safety, regeneration, ecosystem health) that may not be universally shared. Different cultural contexts may prioritize different lifecycle properties.

---

## 7. Conclusion

We have presented the Demo-Deploy-Grow lifecycle model for self-organizing AI systems. By formalizing the Grow phase — where systems evolve beyond their original specification — and providing transition gates, governance gradients, and regression protocols, we address a critical gap in existing AI lifecycle frameworks.

The model's key insight is that **growth is not the absence of governance but requires a different kind of governance** — one that operates through behavioral envelopes and meta-governance rather than fixed rules. The seven-discipline mapping shows that different phases demand different disciplinary expertise, providing practical guidance for team composition and skill development.

As AI systems become more autonomous and adaptive, the distinction between Deploy and Grow will become increasingly important. Systems that were designed for Deploy but exhibit Grow-phase behavior (emergent capabilities, self-modification, ecosystem participation) need lifecycle models that acknowledge and govern this transition. The DDG model provides that foundation.

Future work includes: empirical validation through longitudinal case studies, formal specification of the governance gradient using the behavioral type systems from Thesis 1, and extension of the model to multi-system ecosystems where multiple DDG lifecycles interact.

---

## References

1. Amodei, D. et al. (2016). "Concrete Problems in AI Safety." arXiv:1606.06565.
2. Amershi, S. et al. (2019). "Software Engineering for Machine Learning: A Case Study." *ICSE-SEIP*, 291-300.
3. Ashby, W.R. (1956). *An Introduction to Cybernetics.* Chapman & Hall.
4. Bai, Y. et al. (2022). "Constitutional AI: Harmlessness from AI Feedback." arXiv:2212.08073.
5. Brown, T. et al. (2020). "Language Models are Few-Shot Learners." *NeurIPS*, 1877-1901.
6. Foerster, J. et al. (2016). "Learning to Communicate with Deep Multi-Agent Reinforcement Learning." *NeurIPS*, 2137-2145.
7. Gebru, T. et al. (2021). "Datasheets for Datasets." *CACM*, 64(12), 86-92.
8. Heylighen, F. (2001). "The Science of Self-Organization and Adaptivity." *The Encyclopedia of Life Support Systems*, 5(3), 253-280.
9. Holland, J. (1995). *Hidden Order: How Adaptation Builds Complexity.* Addison-Wesley.
10. Kauffman, S. (1993). *The Origins of Order.* Oxford UP.
11. Kreuzberger, D., Kuhl, N., & Hirschl, S. (2023). "Machine Learning Operations (MLOps): Overview, Definition, and Architecture." *IEEE Access*, 11, 31866-31879.
12. Li, T. et al. (2020). "Federated Learning: Challenges, Methods, and Future Directions." *IEEE Signal Processing Magazine*, 37(3), 50-60.
13. Mang, P. & Reed, B. (2012). "Designing from Place: A Regenerative Framework." *Building Research & Information*, 40(1), 23-38.
14. Maturana, H. & Varela, F. (1980). *Autopoiesis and Cognition.* D. Reidel.
15. McMahan, B. et al. (2017). "Communication-Efficient Learning of Deep Networks from Decentralized Data." *AISTATS*, 1273-1282.
16. Mitchell, M. et al. (2019). "Model Cards for Model Reporting." *FAT*, 220-229.
17. NIST (2023). "Artificial Intelligence Risk Management Framework (AI RMF 1.0)." NIST AI 100-1.
18. Ostrom, E. (1990). *Governing the Commons.* Cambridge UP.
19. Ouyang, L. et al. (2022). "Training Language Models to Follow Instructions with Human Feedback." *NeurIPS*, 27730-27744.
20. Saltz, J. & Shamshurin, I. (2016). "Big Data Team Process Methodologies." *IEEE BigData*, 2872-2879.
21. Sculley, D. et al. (2015). "Hidden Technical Debt in Machine Learning Systems." *NeurIPS*, 2503-2511.
22. Shehory, O. & Kraus, S. (1998). "Methods for Task Allocation via Agent Coalition Formation." *AIJ*, 101(1-2), 165-200.
23. Turner, R. & Baker, R. (2019). "Bio-inspired Software Engineering Lifecycle Models." *JSSS*, 147, 52-63.
24. von Bertalanffy, L. (1968). *General System Theory.* George Braziller.
25. Wahl, D.C. (2016). *Designing Regenerative Cultures.* Triarchy Press.
26. Wei, J. et al. (2022). "Emergent Abilities of Large Language Models." *TMLR*.
27. Wirth, R. & Hipp, J. (2000). "CRISP-DM: Towards a Standard Process Model for Data Mining." *Proc. 4th Intl. Conf. Practical Applications of KDD*, 29-39.
