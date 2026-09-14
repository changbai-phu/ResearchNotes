# Title: Imperfect detectors for adversarial tasks with applications to quantum key distribution 
Authors: Shlok Nahar, Devashish Tupkary, and Norbert Lutkenhaus   
Year:  2026    
Institute: IQC    
Link: https://quantum-journal.org/papers/q-2026-03-24-2044/pdf/    
Document: [2000-Shor-Preskill-proof-of-BB84](resources/papers_download/QComm_2026-Nahar-Tupkary-Lutkenhaus-Imperfect-detctors.pdf)   


## One-sentence summary
This paper introduce a flexible framework to integrate detector imperfections using device parameters like dark counts and detection efficiency within certain ranges, allowing security proofs not only working on ideal device models. 

*Notes*:
- develop a general framework for analyzing imperfect threshold detectors, treating device parameters (dark counts, detection efficiency) as adversarially controlled within some ranges, which enable worst-case analysis, ensuring security proofs remain valid under realistic conditions. -- abstract


## Problem - claim
Most theoretical quantum security proofs assume perfect detectors, but real-world detectors suffer from dark counts, efficiency mismatches, and memory lag (dead times/afterpulsing). The authors claim that by constructing (CPTP?) noise channels, any detector parameter uncertainty can be absorbed into the mathematical proof, preserving worst-case security guarantees. 

*Notes*:  
- entropic uncertainty relation (EUR)- and phase-error correction-based proofs...work [13, 5] addressing imperfections compatible with entropy accumulation theorem-based proofs either assume qubit sources [13], or require bounds on quantities that cannot be easily related to physical device parameters. -- Intro
- In this work we address the problem of imperfect detection setups with threshold detectors by extending the idea of squashing maps [14, 15, 16, 17, 18] in a general framework, leaving the problem of imperfect sources for future work.
- treats imperfectly characterised device parameters equivalently to untrusted device parameters by ‘giving’ the uncharacterised component to Eve.

## Motivation




## Evidence - support the claim



## Questions - weaken
- Source Imperfections Excluded: The paper focuses exclusively on detection setups, explicitly leaving hardware imperfections in photon sources (e.g., intensity fluctuations or phase randomization leaks) for future work.
- Proof Sketch for Memory Effects: While memoryless noise channels are fully proven, the treatment of detector memory (dead time/afterpulsing) is presented as a proof sketch within MEAT that requires further formalization.
- Reliance on Flag Space Weight Bounds: Utilizing flag-state squashing maps requires calculating valid lower bounds on preserved subspaces, which remains mathematically challenging for active basis choice setups under certain proof techniques like postselection.

*Notes*:  
- Memory effects are an important consideration in realistic detection setups, as all practical detectors exhibit phenomena such as dead times and afterpulsing...Our approach is tailored to a specific proof technique — namely, the marginal-constrained entropy accumulation theorem (MEAT) ... our contribution is limited to a proof sketch, and that completing the full argument remains a technically challenging and important direction for future work. We also note that alternate ways to address this problem within phase error estimation-based proofs. -- Intro


## Notes-taken
1. The "Give the Noise to Eve" Strategy
   1. Instead of trying to write a custom security proof for every single imperfect detector setup, the authors map the noisy detector POVM ($\boldsymbol{\Gamma}_{\mathbf{d}_B, \boldsymbol{\eta}}$) to an ideal detector POVM ($\mathbf{F}$) preceded by a virtual noise channel ($\Phi$).
   2. Because quantum channels can only lose information when passed through noise, giving this virtual noise channel to Eve represents a strict worst-case scenario that guarantees absolute security if the protocol still generates keys under these conditions.
2. Specialized Noise Channels
   1. Dark Count Noise Channel ($\Phi_{\mathbf{d}_B}$): Models thermal noise and independent false clicks as a classical post-processing operation ($P_{\mathbf{d}_B}$), establishing bounds on the flag-space weight ($W_{\mathbf{d}_B}$).
   2. Loss & Efficiency Mismatch Noise Channel ($\Phi_{\boldsymbol{\eta}}$): Models unequal detector efficiencies ($\eta_{\min}$ vs. $\eta_{\max}$) across spatial/temporal modes, mapping them to a common ideal efficiency parameter ($\eta^*$).
   3. Generic Noise Channel (Theorem 3): Provides a general operator inequality ($\boldsymbol{\Gamma}_{m, \text{noise}} - (1-q_m)\boldsymbol{\Gamma}_{m, \text{ideal}} \ge 0$) to calculate noise channels for arbitrary, unmodeled physical imperfections.
3. Detector Memory Effects (Dead Times & Afterpulsing)
   1. Practical single-photon avalanche diodes (SPADs) exhibit afterpulsing (trapped charges causing false follow-up clicks) and dead times (recovery periods after a click).
   2. The paper sketches a formal integration with the Marginal-Constrained Entropy Accumulation Theorem (MEAT): if a detector clicks in round $i$, the protocol explicitly discards round $i+1$ (and subsequent correlated rounds). Conditioning single-round entropy estimators on past public announcements allows memory-induced correlations to be eliminated from the key rate calculation.


## Some related papers/ papers mentioned



### Related contents from other paper



## Interesting 


---
This paper introduces a new method to make **Quantum Key Distribution (QKD)**—a method for unhackable quantum communication—much more secure in the real world.

Here is what the research means in simple terms:

**1. The Problem: Real-World Equipment Has Flaws**
In theory, QKD is completely secure. In practice, light detectors aren't perfect:

* They sometimes register a signal when there isn't one (**dark counts**).
* They miss signals because they aren't 100% efficient (**loss**).
* An eavesdropper (named **Eve**) could try to use these equipment flaws to hack the system without getting caught.

**2. The Solution: "Give" the Imperfections to the Hacker**
The researchers created a mathematical framework that assumes Eve has complete control over these equipment flaws. By calculating the absolute worst-case scenario where Eve gets free access to every flaw in the system, they prove that the system can still stay secure.

**3. Key Features of the Work**

* **Works across different setups:** The method isn't tied to just one type of system; it is flexible and can be applied to many quantum protocols.
* **Based on real test data:** It uses realistic ranges for equipment flaws (like efficiency limits and dark count rates) measured in laboratory tests.
* **Tolerates high flaw levels:** The security proof works even when the equipment has relatively large imperfections, generating higher key generation rates than previous methods.
* **Initial steps on "Memory Effects":** Real detectors sometimes get stuck after firing (dead times) or trigger false extra signals (afterpulsing). The paper outlines a preliminary strategy to account for these time-delay flaws as well.