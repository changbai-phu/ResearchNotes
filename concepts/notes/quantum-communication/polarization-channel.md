Depending on context, "polarization channel" refers to two distinct concepts: a **physical medium** (e.g., optical fiber affecting photon polarization) or a **coding technique** (**Channel Polarization / Polar Codes**).

---

### Comparison Matrix

| Aspect | **Physical Polarization Channel** | **Channel Polarization / Polar Channel** | **Degradable Channel** |
| --- | --- | --- | --- |
| **Category** | Physical Noise Model | Algorithmic Coding Technique | Mathematical Classification |
| **What it describes** | How physical polarization states (e.g., $H/V$) rotate, dephase, or depolarize. | A technique that splits/combines $N$ noisy channels into extreme "perfect" vs "useless" channels. | A structural property where Eve's state can be derived by degrading Bob's state. |
| **Mathematical Role** | Defines a specific CPTP map $\mathcal{N}(\rho)$ (e.g., Pauli/depolarizing channel). | A method to construct explicit capacity-achieving codes (Quantum Polar Codes). | A condition that guarantees **single-letter additivity** ($Q = Q^{(1)}$). |
| **Physical Reality** | Direct physical model of optical fiber / atmospheric links. | Mathematical framework applied on top of physical channels. | Rare idealization; real physical channels are usually non-degradable. |

---

### Breakdown of the Terms

#### 1. Physical Polarization Channel (The Noise Model)

This describes an optical path where information is encoded in the polarization state of light (such as horizontal $\vert{}H\rangle$, vertical $\vert{}V\rangle$, or diagonal $\vert{}+\rangle$). Noise manifests as:

* **Polarization Mode Dispersion (PMD):** Birefringence in optical fiber causes different polarization components to travel at slightly different speeds, dephasing the state.
* **Depolarization Noise:** Thermal fluctuations randomly turn pure polarization into mixed noise (a Pauli noise channel).

#### 2. Channel Polarization / Polar Codes (The Algorithmic Scheme)

Invented by Erdal Arıkan (2009) for classical channels and extended to quantum channels (Wilde & Guha, 2013), **channel polarization** is a code construction technique:

1. You take $N$ copies of a noisy channel.
2. You link them together using quantum gates (like CNOT or Clifford unitaries) and split them into $N$ virtual "coordinate channels."
3. As $N \to \infty$, these virtual channels **polarize** into two extremes:
* A fraction equal to the channel capacity becomes **100% noiseless** (perfect for transmitting data).
* The remaining fraction becomes **100% noisy** (used only for fixed "frozen" bits or EPR pairs).



#### 3. How They Relate to Degradable Channels

A **degradable channel** is a mathematical label on a single channel's information leakage. It ensures that Bob always holds a cleaner state than Eve, eliminating superadditivity and making the capacity $Q(\mathcal{N})$ easy to compute.

* A **physical polarization channel** (like a depolarizing fiber) is usually **non-degradable**, meaning calculating its exact capacity is hard due to potential superadditivity.
* To achieve capacity on such channels, researchers use **channel polarization (polar codes)** to synthesize virtual noiseless links directly out of noisy physical channels.