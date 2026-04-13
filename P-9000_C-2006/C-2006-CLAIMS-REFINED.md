# REFINED CLAIMS — C-2006
## By: DeepSeek (Opus-proxy) | Post-adversarial refinement

**1. A computer-implemented method for detecting unauthorized autonomous agents in a distributed governance system, comprising:**  
continuously ingesting, via a network interface, a time-series dataset of governance events, each event comprising a digital record of a decision outcome and an associated authorized decision pathway identifier from a plurality of authorized pathways;  
generating, by a processor, a predictive model of expected governance outcomes by training a recurrent neural network (RNN) on the time-series dataset, wherein the RNN learns temporal patterns and outcome distributions specific to each authorized decision pathway;  
computing, by the processor, a multi-dimensional deviation vector for each new governance event by comparing its observed outcome parameters against the RNN's predicted outcome distribution for its associated authorized pathway;  
identifying a cluster of events as an anomalous deviation region when a statistical significance test, applied to the magnitude and directional consistency of their corresponding deviation vectors over a sliding time window, exceeds a predefined threshold;  
executing a source localization routine by: (i) constructing a directed influence graph of system components based on event metadata and pathway dependencies, (ii) performing a probabilistic graph traversal from nodes associated with events in the anomalous deviation region to identify a candidate component with maximal inverse-path probability, and flagging said candidate component as a probable unauthorized autonomous agent; and  
rendering, on a display device, an interactive topological map comprising a visual representation of the directed influence graph, wherein nodes corresponding to the anomalous deviation region are visually accentuated and the flagged candidate component is annotated as the probable unauthorized agent.

**2. The method of claim 1, wherein the statistical significance test is a Hotelling's T-squared test applied to the deviation vectors within the sliding time window to reject the null hypothesis that the deviations originate from the authorized pathway's learned distribution.**

**3. The method of claim 1, wherein the probabilistic graph traversal is a Monte Carlo simulation of influence propagation, and wherein the candidate component is identified by computing a maximum a posteriori (MAP) estimate from the simulation results.**

**4. The method of claim 1, wherein the time-series dataset of governance events further includes a cryptographic proof of pathway authorization appended to each digital record, and wherein the method further comprises verifying the cryptographic proof prior to generating the predictive model.**

**5. The method of claim 1, wherein the interactive topological map is dynamically updated and wherein the visual accentuation of the anomalous deviation region is proportional to the computed statistical significance.**

**6. The method of claim 1, further comprising initiating a containment protocol by generating and transmitting a control signal to a network orchestration layer to isolate the flagged candidate component from the distributed governance system.**
