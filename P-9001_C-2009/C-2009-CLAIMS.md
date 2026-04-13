# CLAIMS -C-2009
## By: DeepSeek | Cleanroom: spec-derived only

**1. A method for regulating decision provenance in a pharmacological data processing system, comprising:**  
   **quantifying a pharmacological mass of prior context associated with a decision event, wherein the pharmacological mass represents a contextual potency relative to a therapeutic indication of the decision event;**  
   **calibrating a therapeutic window defined by a minimum effective dose (MED) threshold and a maximum tolerated dose (MTD) threshold, wherein the MED threshold corresponds to a minimum contextual potency required for decision accountability, and the MTD threshold corresponds to a maximum contextual potency beyond which decision toxicity occurs;**  
   **modulating an administration rate of contextual history to maintain the pharmacological mass within the therapeutic window; and**  
   **outputting a decision provenance record constrained by the therapeutic window.**  

**2. The method of claim 1, wherein quantifying the pharmacological mass comprises measuring at least one of: a lineage entropy metric, a contextual binding affinity score, or a temporal decay-adjusted potency index.**  

**3. The method of claim 1, wherein calibrating the therapeutic window further comprises dynamically adjusting at least one of the MED threshold or the MTD threshold based on a decision-type classification or a real-time system load parameter.**  

**4. The method of claim 1, wherein modulating the administration rate comprises applying a sigmoid sensitivity function to context accumulation, such that a marginal change in administration rate decreases as the pharmacological mass approaches either the MED threshold or the MTD threshold.**  

**5. The method of claim 1, further comprising generating an audit trail that excludes contextual data exceeding the MTD threshold while preserving contextual data meeting or exceeding the MED threshold.**  

**6. The method of claim 1, wherein decision toxicity includes at least one of: decision latency exceeding a predetermined latency tolerance, decision paralysis indicated by a failure to produce an output within a time window, or privacy exposure exceeding a privacy risk threshold.**