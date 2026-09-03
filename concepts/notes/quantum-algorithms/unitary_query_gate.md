# Unitary Query gate

> why query gates has to be unitary? why it says it is hardware limitation? how does unitary query gate overcome the physical limitations using query register and target register using bitwise XOR?
>

In quantum mechanics, nature has a strict rule: You cannot create or destroy quantum information. 
- Unitary = reversible 
- A unitary query gate: a quantum operation that never loses information. If we ran the gate backward, we would get exact starting states back.

### The problem with standard functions
If we have a function where $f(0) = 0$ and $f(1) = 0$ (a Constant function), and we feed a qubit into it, both paths smash down into a single 0. The original input (0 or 1) is deleted.  
Quantum mechanics forbids this. You cannot just overwrite qubits.

### Unitary Oracle Solution
To make the black-box function "Unitary" (reversible), quantum scientists use two qubits instead of one:

   1. Top Qubit (Input register): Holds your question ($x$).
   2. Bottom Qubit (Output register): Holds a placeholder ($y$).

Instead of overwriting $x$, the black box leaves $x$ completely alone. It calculates $f(x)$ and flips the bottom qubit if $f(x) = 1$.
Because the top qubit is never destroyed, you can always undo the step. This two-qubit setup is what makes the gate Unitary.