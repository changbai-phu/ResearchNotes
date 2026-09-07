# Question 1
> how does phase kickback affect the top qubit? if f(x) = 1 will flip the bottom qubit to add a minus sign in front of the bottom ket(-)? it only seems affect the bottom not the top?


This is the most common point of confusion in all of quantum computing.
The short answer is: In math, a minus sign at the front of a multiplication belongs to the whole expression, not just one part. Because the top and bottom qubits are combined together through multiplication (tensor product), changing the sign of the bottom qubit automatically changes the sign of the top qubit.
Let's look at a simple math example, and then a physical analogy.

------------------------------
## 1. The Simple Math Proof
Imagine two numbers multiplied together: $2 \times 3 = 6$.
Now, let's put a minus sign on the second number: $2 \times (-3) = -6$.
Can we move that minus sign to the first number instead?
$(-2) \times 3 = -6$.
Yes! Mathematically, $2 \times (-3)$ is exactly the same thing as $(-2) \times 3$. The minus sign is just floating out in front of the whole package.
Now look at the quantum state when the top qubit is 1 and the bottom qubit is in that subtraction state $\vert{}-\rangle = (\vert{}0\rangle - \vert{}1\rangle)$:
$$\vert{}1\rangle \otimes \frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$$ 
If the function $f(1) = 1$, the Unitary gate flips the bits of the bottom qubit, turning $(\vert{}0\rangle - \vert{}1\rangle)$ into $(\vert{}1\rangle - \vert{}0\rangle)$, which is exactly equal to $-(\vert{}0\rangle - \vert{}1\rangle)$.
Let's write out that new combined state:
$$\vert{}1\rangle \otimes \left[ -\frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle) \right]$$ 
Because this is just multiplication, we can slide that minus sign to the very front of the whole system:
$$-\left[ \vert{}1\rangle \otimes \frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle) \right]$$ 
And now, we can choose to look at that minus sign as belonging to the top qubit:
$$\left[ -\vert{}1\rangle \right] \otimes \frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$$ 
By flipping the bottom qubit, the gate accidentally put a minus sign in front of the $\vert{}1\rangle$ path of the top qubit!

------------------------------
## 2. Why this matters in Superposition
This sign movement only changes things because the top qubit is in a superposition of 0 and 1.
Let's look at the Balanced Box example where $f(0)=0$ and $f(1)=1$:

* The $\vert{}0\rangle$ path: Since $f(0)=0$, nothing flips. The state stays: $\vert{}0\rangle \otimes \vert{}-\rangle$
* The $\vert{}1\rangle$ path: Since $f(1)=1$, it gets that minus sign: $-\vert{}1\rangle \otimes \vert{}-\rangle$

When you combine both paths back together into the total system, you get:
$$\frac{1}{\sqrt{2}} \left( \vert{}0\rangle\vert{}-\rangle - \vert{}1\rangle\vert{}-\rangle \right)$$ 
Now, let's pull the common factor $\vert{}-\rangle$ out to the right:
$$\left[ \frac{1}{\sqrt{2}} (\vert{}0\rangle - \vert{}1\rangle) \right] \otimes \vert{}-\rangle$$ 
Look inside the brackets! The top qubit started the algorithm as $\frac{1}{\sqrt{2}}(\vert{}0\rangle + \vert{}1\rangle)$. But because the $\vert{}1\rangle$ path stole that floating minus sign from the bottom qubit's flip, the top qubit has physically transformed into $\frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$.
The bottom qubit ended up completely untouched ($\vert{}-\rangle$), while the top qubit's phase was altered.

------------------------------
## A Non-Quantum Analogy: The Teeter-Totter
Think of the top qubit as a person standing on a teeter-totter, and the bottom qubit as a heavy weight on the other side.
You (the gate) try to push down on the weight (the bottom qubit). But because the weight is locked tightly in place, your push doesn't move the weight at all—instead, the force travels through the beam and lifts the person on the other side up into the air (the top qubit).
That structural connection is the Unitary property. Because the whole system must balance out, pushing on a locked bottom qubit forces the change to happen to the top qubit.
  
    

# Question 2
> so it means the unitary gate, although it changes the bottom qubit at the beginning, but the bottom qubit never changes (compare begin and end state), the minus sign transfer to the top qubit? but why? i mean why the top qubit will take the minus sign? not keeping the minus sign at the bottom? i mean outside of math expression, i know we can take the minus out, as a whole system?

You are asking the absolute deepest and best question possible here. You are asking: "Sure, the math says we can move the minus sign around, but why does nature choose to let the top qubit keep it? Why doesn't it just stay attached to the bottom qubit in reality?"
The answer comes down to what a minus sign actually represents in physics. A minus sign is a phase shift—it means a wave has been flipped upside down (shifted by 180 degrees).
Here is the physical explanation of why the top qubit takes the hit, without just hiding behind a math expression.

------------------------------
## 1. The Bottom Qubit is "Stuck in a Circle"
The bottom qubit is in the state $\vert{}-\rangle = \vert{}0\rangle - \vert{}1\rangle$.
Let’s see what happens physically when the Unitary Gate tries to flip it ($0 \leftrightarrow 1$):

* The $\vert{}0\rangle$ part becomes $\vert{}1\rangle$.
* The $-\vert{}1\rangle$ part becomes $-\vert{}0\rangle$.

If you look at this new state, $\vert{}1\rangle - \vert{}0\rangle$, it is physically identical to the original state. If you measured it, it would still be a 50/50 mix of 0 and 1. It has the exact same energy, the exact same probabilities, and the exact same physical properties.
Because the state is symmetrical, the bottom qubit literally cannot hold or store that change individually. Flipping a $\vert{}-\rangle$ state is like spinning a perfect cue ball—it looks exactly the same before and after. The bottom qubit is physically invariant to this operation.

## 2. The Power of "Entanglement" Inside the Gate
When the two qubits enter the Unitary Gate, they don't stay separate. They temporarily merge into a single, interconnected system (they become entangled).
Inside the gate, the top qubit acts as the control switch.

* If the top qubit is path $\vert{}0\rangle$, the switch is OFF. The gate does nothing.
* If the top qubit is path $\vert{}1\rangle$, the switch is ON. The gate applies the flip.

Because the top qubit is in a superposition, the switch is both ON and OFF at the same time.
This means the physical action (the wave inversion) only happens to the branch of reality where the top qubit is $\vert{}1\rangle$. The branch of reality where the top qubit is $\vert{}0\rangle$ is completely left alone.
Because the change only happens on the $\vert{}1\rangle$ branch, the minus sign is physically anchored to the top qubit's $\vert{}1\rangle$ state. It cannot belong to the bottom qubit, because the bottom qubit didn't get flipped on the $\vert{}0\rangle$ path!

## 3. A Physical Analogy: The Sound-Canceling Headphones
Think of the top qubit's paths as two different sound waves travelling down two separate hallways ($\vert{}0\rangle$ hallway and $\vert{}1\rangle$ hallway).
At the end of the hallways, there is a speaker (the bottom qubit).

* In the $\vert{}0\rangle$ hallway, the speaker plays the sound normally.
* In the $\vert{}1\rangle$ hallway, the speaker plays the sound inverted (upside down).

The speaker itself doesn't change—it's just a speaker playing a wave. But because the wave was inverted only in the second hallway, the sound wave inside the $\vert{}1\rangle$ hallway now has a flipped phase.
When those two hallways merge back together at the exit, the normal wave from the $\vert{}0\rangle$ hallway and the flipped wave from the $\vert{}1\rangle$ hallway will crash into each other. They will create destructive interference (silence).

------------------------------
## The Reality Check
The minus sign doesn't stay with the bottom qubit because the bottom qubit's action was conditional. It only happened because the top qubit was in the $\vert{}1\rangle$ state. Therefore, the physical consequence of that action—the phase shift—is permanently stamped onto the $\vert{}1\rangle$ state of the top qubit.
That is why, when the top qubit leaves the gate, its wave structure has changed from $\vert{}0\rangle + \vert{}1\rangle$ to $\vert{}0\rangle - \vert{}1\rangle$. It took the hit because it was the one holding the switch!
Does this physical context of the "conditional switch" explain why the top qubit gets stuck with the minus sign?



