# Quantum channel
In classical information, a channel is a matrix of transition probabilities $P(Y\vert{}X)$. In quantum information, a channel is a **Completely Positive Trace-Preserving (CPTP)** map that models noise, loss, or decoherence acting on a density matrix $\rho$. Think of it as a physical process where your system inevitably interacts with an unmeasured environment.
  
In physics, a channel is an open system: your photon travels through an environment (fiber or atmosphere) and leaks information to it. Mathematically, it is described as a CPTP map (Completely Positive Trace-Preserving map) that maps an input density matrix $\rho_{\text{in}}$ to an output $\rho_{\text{out}}$.
  
These physical mechanisms occur simultaneously along the transmission path:
- Loss (Attenuation): Photons are absorbed or scattered away into the environment. The particle simply fails to arrive.
- Decoherence (Dephasing): The photon arrives, but its quantum phase relationship relative to other states is corrupted because it entangled slightly with stray thermal or atmospheric noise.
- Noise (Depolarization / Bit Flips): Random physical perturbations flip the polarization or state (e.g., turning horizontal polarization into vertical).

### Why CPTP? (Completely Positive Trace-Preserving)
In linear algebra, a matrix having "positive entries" means the numbers in the grid are positive.   
In quantum mechanics, positivity means something entirely different.  
A quantum state is represented by a density matrix $\rho$, which must be positive semi-definite (all of its eigenvalues are $\ge 0$). This guarantees that all physical probabilities calculated from $\rho$ stay between $0\%$ and $100\%$.  

A quantum channel $\mathcal{N}$ is a mathematical function (a "map") that transforms an input density matrix into an output density matrix: $\rho_{\text{out}} = \mathcal{N}(\rho_{\text{in}})$.  
[ Input State: ρ_in ]  --->  [ Quantum Channel: N ]  --->  [ Output State: ρ_out ]  
  (Trace = 1, λ ≥ 0)                                         (Trace = 1, λ ≥ 0)  

The name CPTP breaks down into two non-negotiable physical constraints:
- Trace-Preserving (TP)
  - What it means: $\text{Tr}(\mathcal{N}(\rho)) = \text{Tr}(\rho) = 1$.
  - Physics reason: The total probability of all possible measurement outcomes must always sum to $100\%$ ($1.0$). A trace-preserving channel ensures no probabilities "leak out" of the universe or sum to something impossible like $120\%$.

- Completely Positive (CP)
  - Why "Positive" isn't enough: A map is positive if it turns a valid density matrix ($\rho \ge 0$) into another valid density matrix ($\mathcal{N}(\rho) \ge 0$).
  - Why "Completely Positive" is required: Suppose your input particle $A$ is entangled with another idle particle $B$ sitting in the lab. The channel $\mathcal{N}$ acts only on particle $A$, while the identity map $\mathcal{I}_B$ does nothing to particle $B$.
  - The combined transformation is $(\mathcal{N}_A \otimes \mathcal{I}_B)(\rho_{AB})$.
  - Complete Positivity guarantees that even when system $A$ is entangled with an arbitrary spectator system $B$, the output density matrix of the entire joint system remains positive semi-definite (eigenvalues $\ge 0$).
  - Fun Fact: The mathematical transpose operation $T(\rho) = \rho^T$ is positive, but not completely positive. If you apply transpose to only half of an entangled pair, it yields negative eigenvalues (unphysical "negative probabilities"). Thus, a real physical quantum channel can never perform a pure transpose!

## Channel capacity
- Classical Capacity ($C$): How many classical bits (0s and 1s) can you reliably transmit per channel use? (e.g., Holevo bound / HSW theorem).
- Quantum Capacity ($Q$): How many quantum states ($\lvert\psi\rangle$) or entangled pairs can you transmit without losing coherence? (e.g., Devetak / LSD theorem). $Q \le C$ always.
    
To calculate a channel's quantum capacity (how much quantum information it can send reliably), we look at its coherent information.  
For most quantum channels, sending messages in entangled blocks across multiple uses yields a higher transmission rate than sending messages one-by-one—a phenomenon called superadditivity. This makes general quantum capacity mathematically intractable because you have to calculate interactions across an infinite number of channel uses ($n \to \infty$).  

## Quantum Shannon theory
In classical Shannon theory, information capacities are strictly additive. If Channel A can transmit 100 Mbps and Channel B can transmit 50 Mbps, using them together in parallel yields $100 + 50 = 150$ Mbps.
  
In Quantum Shannon Theory, capacity describes how much quantum information (or secret key rate) you can transmit per channel use. Because quantum states can be entangled across parallel channels, capacities do not always add up simply:
1. Additive
   $$\text{Capacity}(A + B) = \text{Capacity}(A) + \text{Capacity}(B)$$  
   This happens when you treat two channels as completely independent classical links. You send unentangled states down Channel A and unentangled states down Channel B.

2. Super-Additive (The Quantum Surprise)
   $$\text{Capacity}(A + B) > \text{Capacity}(A) + \text{Capacity}(B)$$  
   Instead of sending independent photons down Channel A and Channel B, you send entangled photon pairs across both channels simultaneously, or use joint quantum measurements across both outputs at the receiver end.The combined channel can transmit more quantum information than the sum of its individual capacities.The 
   - Super-Additive Capacity: Achieved when you prepare an entangled state across the inputs of both channels before sending them. The entanglement links the two physical channels together, unlocking a higher transmission rate than if you used Channel 1 and Channel 2 as isolated systems.
     
   Extreme Example (Superactivation):  
   There exist certain noisy quantum channels where Channel A has zero quantum capacity ($Q(A) = 0$), and Channel B has zero quantum capacity ($Q(B) = 0$).  
   If used individually, neither can send a single qubit. But if you send entangled states across Channel A and Channel B together, the joint capacity becomes greater than zero ($Q(A + B) > 0$). Two useless channels combined create a functional quantum line.
   
3. What about "Sub-additive"?  
   Sub-additivity ($\text{Capacity} < \text{Capacity}_A + \text{Capacity}_B$) doesn't happen for total channel capacities in a harmful sense—you can always choose not to entangle inputs and achieve at least the additive sum. However, the term non-additive in quantum information theory is almost universally used as a synonym for super-additive, highlighting that single-channel capacity formulas fail to capture the full power of parallel quantum channels.
  
**Summary of Terms**  
| Mathematical Property | Definition | Does it happen to Quantum Channel Capacity? |
|---|---|---|
| Additive | $C(A + B) = C(A) + C(B)$ | Yes (Standard classical baseline behavior). |
| Super-additive | $C(A + B) > C(A) + C(B)$ | Yes (Quantum phenomenon via entangled inputs / joint measurements). |
| Sub-additive | $C(A + B) < C(A) + C(B)$ | No (You can always fall back to independent channel uses). |
| Non-additive | $C(A + B) \neq C(A) + C(B)$ | Yes (Used as the overarching label, but practically synonymous with super-additive here). |

In Quantum Shannon Theory, when papers say a channel capacity is "non-additive," they almost always mean super-additive ($C(A + B) > C(A) + C(B)$).  
Quantum channel capacities do not suffer from sub-additivity because you always have the option to ignore entanglement between channel inputs and send independent states down Channel A and Channel B separately. Therefore, you can always guarantee at least $C(A) + C(B)$.  
Because capacities can never drop below the additive baseline, the only way a capacity can be "non-additive" in practice is by being super-additive.

## Degradable Channel
Whenever you send a signal through a quantum channel, noise leaks some information to the surrounding environment. A channel is degradable if the signal received by the receiver (Bob) is strictly cleaner/more complete than what leaked to the environment (Eve), such that Eve's signal can be obtained merely by applying further noise ("degrading") to Bob's signal.
- Key Property: In degradable channels, coherent information is additive. Using the channel $n$ times offers no quantum cheat code over using it once.
- Why it matters: Because there is no superadditivity, you only need to analyze a single use of the channel to compute its exact quantum capacity.

## Non-degradable Channel
A channel is non-degradable if Bob's received output cannot be simply mapped to Eve's environmental output by adding local noise.
- The Problem: In non-degradable channels, Bob and Eve receive complex, incomparable structures of information.
- The Consequences: These channels usually exhibit superadditivity-—where sending entangled states across $2$ or $n$ parallel uses yields a higher capacity per use than a single run ($Q^{(1)}(\mathcal{N}^{\otimes n}) > n \cdot Q^{(1)}(\mathcal{N})$). This makes their quantum capacities extremely difficult to compute or bound.