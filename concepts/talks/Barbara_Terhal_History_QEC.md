# History of Quantum Error Correction
Speaker: Barbara Terhal
Video Link: [QGSS2025 Distinguished Lecture - Barbara Terhal](https://www.youtube.com/watch?v=VPZAHYeXaoM&list=PLOFEBzvs-VvoIfbpOb_geVnwFmbW6ij0m&index=16)  
Slides: [QGSS2025 Distinguished Lecture Slides - Barbara Terhal](https://github.com/qiskit-community/qgss-2025-lecture-notes/blob/main/Day%208%20-%20Distinguished%20Lecture%20by%20Barbara%20Terhal.pdf)
  

---
Shor: one can reverse decoherence  
> "To preserve the state of superposition of the encoded qubit, what we do in effect is to measure the decoherence without measuring the state of the qubits."

*Notes*:  
- we can fix quantum mistakes and save a fragile quantum state before it gets ruined by the environment.
- WHY: In classical computers, we fix mistakes by making copies of files. But in quantum computing:
  - No-Cloning Theorem - cannot copy a quantum state
  - Measurement cause collapse 
  - So Shor's discovery is we don't need to look at the quantum state, just need to look at the mistake that happened to it. 
- HOW: 
  - Shor's 9-qubit code - take the information of 1 qubit and spread it out across 9 qubits.
  - Project errors on a set of Pauli Matrix Errors (bit flip, phase flip, Y error-both bit and phase flip)
  - Measure the mistake, not ask "what state it is inside". --- **Parity Check** + **Ancilla Qubit**
  - Apply correction to fix it. 
- From WHAT:
  - Infinite errors become simple - quantum mistakes can be messy and random, when we measure them, they are collapsed to a few simple types: bit flip or phase flip.
  - Fix the two basic types to cure any decoherence mistake.


Steane: fundamentals and 7 qubit code 
