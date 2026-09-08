# What is the difference between Andriolo (2026) and Valerio/Scarani (2009)?
If you look at Section 2 (Related Work), the authors explicitly reference Valerio’s 2009 paper (Ref6) as a classic, broad review of QKD7. However, the field has undergone a massive paradigm shift in the 17 years between them.
  
The differences can be broken down into three main areas:

1. Loops vs. Limits (Asymptotic vs. Finite-Key Security)
   1. Valerio (2009): Mostly focused on asymptotic key rates8. It assumed that Alice and Bob could exchange an infinite number of quantum states ($n \to \infty$)89. In this idealized limit, the math is relatively simple, but it is physically impossible because real systems can only run a finite number of times before sending a key810.
   2. Andriolo (2026): Focuses heavily on the finite-key regime ($n < 10^6$)10. It details powerful new mathematical tools developed since 2009—like the Entropy Accumulation Theorem (EAT) and Quantum de Finetti theorems—which allow us to calculate safety bounds for short, finite-length keys under general, real-world attacks8more_horiz.

2. Analytical Approximations vs. Automated Computers (Numerical Optimization
   1. Valerio (2009): Relied almost entirely on analytical proofs313. If a protocol was highly symmetric (like standard BB84), theorists could write a neat, hand-solved formula for security3. If a protocol was slightly modified or asymmetric, calculating security was mathematically impossible313.
   2. Andriolo (2026): Showcases the rise of automated numerical security proofs312. Instead of hand-writing complex formulas, modern researchers use classical algorithms—like semidefinite programming (SDP) and non-symmetric conic optimization—to calculate exact security bounds for highly complex or imperfect setups3more_horiz.

3. loophole Spotting vs. loophole Solving
   1. Valerio (2009): Acted as a "warning system"6. It did an excellent job identifying the newly discovered physical vulnerabilities (like the Photon-Number-Splitting attack) and proposing specific hardware-heavy workarounds (like the Decoy State protocol)1516.
   2. Andriolo (2026): Acts as a "systematic solution"317. It explains how we can use unified mathematical maps (using isometries and pinching channels) to translate almost any physical device flaw (detector dark counts, efficiency mismatch, or source fluctuations) directly into computer constraints to automatically calculate key security