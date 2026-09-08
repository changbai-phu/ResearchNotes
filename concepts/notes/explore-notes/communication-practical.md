## 4 Questions to ask myself
1. What problems does this field solve?
Bridge the gap between theoretical quantum protocols and real-world hardware.
It solves side-channel vulnerabilities, optical channel losses, physical device imperfections, and standardized practical QKD. 

Nobert - [Optical Quantum Communication Theory Group](https://uwaterloo.ca/institute-for-quantum-computing/research/groups/optical-quantum-communication-theory-group)
tight and complete security proofs for practical quantum key distribution (QKD) that do fit to actual implementations. We are involved in activities that support standardization and certification of QKD.

2. What does a researcher actually do day-to-day?
CV-QKD
finite-size analysis 

3. What part made me curious?
the sentence says 'bridge the gap between theoretical protocols to real hardware' part sounds interesting. 'Standardization of QKD' sounds a really important and fundamental work.
If it is implementing on hardware is actually interesting as well.
Analyze for atmospheric channels sounds cool. 

4. What part made me bored / resistant?
Security proofs of QKD? I am bit worry about that, is it math heavy? 
But personally not sure about hardware...maybe I dont really know anything about it...
By roughly reading te recent publish, I found construct noise channel is actually not that easy..the paper name: Imperfect detectors for adversarial tasks with applications to quantum key distribution. 

---
## Practical quantum communication / QKD security
### QKD
Alice and Bob, connected by two channels
- quantum channel: share quantum signals
- classical channel: send classical messages back and forth 
  - need to be authenticated
- task: guarantee security against an adversarial eavesdropper (Eve)
- security: non-secret key is never used
- QKD's security comes from 3 main physics rules:
  - **Rule 1: Measuring something changes it**
    - In quantum physics, you cannot look at or measure a quantum particle without disturbing it. In other words, Alice and Bob will immediately notice when Eve tries to spy on the message (her measurements will tamper with the signal).
    - **Note**: measurement disruption is like 'can we look at a quantum state without altering it'. The answer is we cannot extract information from an unknown state via measurement without changing the state - wavefunction collapse.
  - **Rule 2: Cannot make exact copies**
    - *No-cloning theorem*: physically impossible to create a perfect duplicate of an unknown quantum state without destroying the original. 
    - **Note**: No-cloning is trying to duplicate a state without measuring it first, is like 'can we duplicate a state using a quantum machine without measuring it?'. The answer is: no universal quantum operation (unitary transformation) exists that takes an unknown state and outputs two identical copies.
  - **Rule 3: Connected particles create unpredictable results**
    - When using entangled pairs, their measurement results don't exist until the exact moment they are measured. Since the outcome isn't predetermined, Eve cannot guess or copy the secret key beforehand. The result comes into existence only when Bob receives it. 
  - In summary, because the system is protected by the laws of physics, it provides unconditional security. 

### use of light
1. Why Light is the Only Choice
While quantum computing can use ions, atoms, or electron spins, QKD requires light (photons).
- **Distance**: QKD is designed to share secrets across long distances (between cities, ground stations, or satellites).
- **Stability**: Light rarely interacts with surrounding matter, meaning its fragile quantum states travel without easily getting garbled or corrupted (decoherence).

2. The Main Problem: **Particle Loss (Scattering)**
Light rarely gets scrambled, but it easily gets lost. Photons scatter in optical fibers or atmosphere, causing two main problems:
- Lower Speeds & Distance Limits: Farther distances mean fewer photons survive. Eventually, the signal drops so low that detectors only pick up random background noise (dark counts).
- Security Risks: Depending on the type of light used (like laser pulses vs. individual single photons), lost photons can leak information to an eavesdropper.

3. How Detectors Handle Lost Photons
Different detector systems handle photon loss in distinct ways:
- Photon Counters (Discrete Variables): If a photon gets lost in transit, the detector simply doesn't click. The system discards that attempt and moves on. This works because QKD only builds a random key; losing a pulse doesn't break the final secret.
- Homodyne Detectors (Continuous Variables): These detectors measure continuous light waves rather than individual photons. They read a signal every single time, so photon loss shows up as background noise rather than a missing event.

4. Footnote Highlight: Why Not Send Direct Messages?
Quantum Secure Direct Communication (QSDC)—an alternative idea where you send the actual secret message directly over quantum channels instead of generating a key first.
  
 Why QSDC is impractical compared to standard QKD:
- If photons get lost along the way, you lose actual pieces of your message.
- Unlike key distribution, you cannot clean up or amplify privacy on a direct message if an eavesdropper manages to intercept part of it.
  
In summary:
- Light is the permanent medium for QKD, traveling through either fiber optic cables or open air/space (free-space links).

### BB84

**BB84 Protocol & Intercept-Resend Attack**

#### Key Rules of Quantum Polarization

In BB84, bits are encoded using two bases: **Rectilinear ($+$)** and **Diagonal ($\times$)**.

* **Matching Basis:** Measuring a photon in its original basis yields a **100% deterministic result** and **does NOT alter** its quantum state.
* **Mismatched Basis:** Measuring a photon in the wrong basis causes the quantum state to **collapse**, resulting in a **$50/50$ random outcome** and altering the photon state.


#### The BB84 Step-by-Step Flow

1. **Quantum Transmission (Step 1):** Alice sends photons randomly encoded in $0$ or $1$ using either $+$ or $\times$ bases. Bob measures each photon using his own randomly chosen basis ($+$ or $\times$). All quantum transmission occurs in this step.
2. **Sifting (Step 2):** Alice and Bob talk publicly to compare **only the bases** they used (never the actual bit values). They discard all mismatched attempts, leaving the **Raw Key**.
3. **Error Estimation & Post-Processing (Step 3):** Alice and Bob publicly compare a small random sample of their raw key bits to calculate the **Quantum Bit Error Rate (QBER)**. That sample is discarded afterward.
* **Low Error Rate ($<11\%\text{--}17\%$):** They perform error correction and privacy amplification to produce the final secret key.
* **High Error Rate ($>11\%\text{--}17\%$):** An eavesdropper is present; they abort and destroy the key.


#### The Intercept-Resend Attack & Why Eve Gets Caught

* **How It Works:** Eve intercepts Alice’s photon in transit, measures it using a randomly chosen basis, generates a **brand-new photon** matching her measurement outcome, and sends it to Bob.
* **Why Eve Must Measure Immediately:** Eve cannot store or copy unmeasured quantum states due to the **No-Cloning Theorem**.
* **Why the Error Rate is 25% (Not 100%):**
* **Eve guesses the CORRECT basis (50% chance):** Her measurement leaves the photon intact. She sends a perfect copy to Bob, resulting in **0% error**.
* **Eve guesses the WRONG basis (50% chance):** Her measurement collapses the photon into a random state. When Bob measures this corrupted photon in Alice's original basis, he gets the wrong bit **50% of the time**.
* **Total Error Rate:** $50\% \text{ (Eve wrong)} \times 50\% \text{ (Bob wrong)} = \mathbf{25\%}$.


#### Summary Table

| Parameter / Step | Normal Operation (No Eve) | Intercept-Resend Attack |
| --- | --- | --- |
| **Photon State Integrity** | Preserved when bases match | Altered 50% of the time by Eve |
| **QBER (Error Rate)** | $\approx 0\%$ (low hardware noise) | **25%** |
| **Outcome** | Secret key generated | **Aborted** (25% exceeds safety threshold) |

---
Whenever the measurement basis doesn't match the photon's orientation, the original information collapses, and the result becomes a pure $50/50$ random guess.

### The Two Rules of Quantum Measurement in BB84

| Alice Sends In... | Receiver Measures In... | Result | State Altered? |
| --- | --- | --- | --- |
| **$+$ Basis** ($H$ or $V$) | **$+$ Basis** | **100% Deterministic** (Gets exact bit) | **NO** (State remains $H$ or $V$) |
| **$+$ Basis** ($H$ or $V$) | **$\times$ Basis** ($+45^\circ / -45^\circ$) | **50% / 50% Random** (Equal chance of $0$ or $1$) | **YES** (Collapses to diagonal) |
| **$\times$ Basis** ($+45^\circ / -45^\circ$) | **$\times$ Basis** | **100% Deterministic** (Gets exact bit) | **NO** (State remains $+45^\circ$ or $-45^\circ$) |
| **$\times$ Basis** ($+45^\circ / -45^\circ$) | **$+$ Basis** ($H$ or $V$) | **50% / 50% Random** (Equal chance of $0$ or $1$) | **YES** (Collapses to rectilinear) |


- [2009-Valerio-The Security of Practical Quantum Key Distribution](https://arxiv.org/html/0802.4155v3#S1)


---
## What exactly was the moment where I wanted to understand more?
- understand how the BB84 works, and how Eve can attack but be prevented/detected.

### Some questions I had in the process:
- Independent Principles vs. Measurement Rules: "Isn't no-cloning theorem coming out from the rule 1? because measurement will disrupt the states, so cannot copy? or no-cloning is copy but not measure the state?"

- QKD Protocol Flow & Mechanics: "Can you explain in a more clear way? so basically, Alice encode the photon and send to Bob... Then they share another photon? over public... And what is Intercept-resend again? Eve send new photon to Bob, but cannot be part of the public talk?"
  >can you explain in a more clear way? so basically, alice endcode the photon and send to Bob, bob measure that photon using his choice of basis. They repeat this process thousands of times. Then they share another photon? over public, and both using their choice os basis to encode/decode it? do they both know each other's result this step? and drop the mismatch I got this part.Then they calculate the error rate, dropped count/total photons?And what is Intercept-resend again? Eve send new photon to Bob, but cannot be part of the public talk? so wont able to compare? 

- Physical State Changes & Probabilities: "I still don't get the intercept-resend part... why Eve need to measure the photon now? before or after she sends the photon?... this measure will alter the photon state, right?... why 11%-17%?"
  > I still dont get the intercept-resend part. So you mean Eve will fake photon and send to Bob, that's step 1, Bob measure using his choice of basis. Why Eve need to measure the photon now? before or after she sends the photon? and Step 2 she listens to the public channel to compare basis, drop mismatch ones. What would she get? or you mean she hailjack? the photon from Alice, and she needs to measure it before send that photon to Bob? this measure will alter the photon state, right? Bob doesnt know that, he measure it again using his basis, and alter the photon state the second time (give me an example). Then Step 2, compare the basis, at the step, both Eve and Bob can have probabilities match with Alice. Until Step 3, when Alice and Bob share the partial sample for error validation, they will find their results completely mismatches? because Eve hijacked the photon, measured it, even Alice and Bob used the same basis, the photon state will be 100% mismatch, isn't? why 11%-17%?
  > I think I know where I got wrong, I thought even Eve and Bob using the same basis, they will change the state twice, but the state actually does not change? Why Eve generate a new photon then? New photon is different from the original photon Alice send...how can measuring lead to the same result? Oh..you said Eve generate the new photon based on her measurement result..so for example Eve hijacked the photon, measure it in +, got 0, she then send a photon 0 state to Bob? 

- Specific Scenario Execution: "What if Alice sent bit 0 in x basis? Eve measure in x basis, Bob measure in x basis?"

- Core Quantum Measurement Rule: "So only when Alice send +/-, but receiver either Eve/Bob measure in x will collapse the information, got 50% 50% wrong result. Same if Alice send x, receiver measure in +/1, again got 50% 50%?"

- Synthesis & Note-Taking: "Cool, can you now summarize the questions we discussed above regarding BB84 and intercept-resend using simple language for future notes?"