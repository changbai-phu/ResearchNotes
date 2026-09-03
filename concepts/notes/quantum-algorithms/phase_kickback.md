# Phase Kickback

Let’s look at the exact math of how the phase kickback happens. We will track a single state through a Constant box and a Balanced box so you can see exactly how the plus or minus sign gets kicked back to the top qubit.  

First, let's look at the mathematical rule of the Unitary Gate ($U_f$). As we discussed, it takes two inputs, $\vert{}x\rangle$ (top) and $\vert{}y\rangle$ (bottom), and does this:
$$U_f \vert{}x\rangle\vert{}y\rangle = \vert{}x\rangle\vert{}y \oplus f(x)\rangle$$ 
(The symbol $\oplus$ just means "flip the bit $y$ if $f(x) = 1$").

------------------------------
## The Secret Ingredient: The Bottom Qubit
Before entering the gate, the bottom qubit is put into the state $\vert{}-\rangle = \frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$.
Let's see what happens to this state if it gets flipped by the box:

* If $f(x) = 0$ (Don't flip):
The state stays exactly the same: $\frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$
* If $f(x) = 1$ (Flip it):
The $\vert{}0\rangle$ becomes $\vert{}1\rangle$, and the $\vert{}1\rangle$ becomes $\vert{}0\rangle$.
The state becomes: $\frac{1}{\sqrt{2}}(\vert{}1\rangle - \vert{}0\rangle)$.
If we pull out a common minus sign, that is mathematically identical to: $-\frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle)$.

Notice the magic trick: Flipping the bits of the bottom qubit didn't actually change the bottom qubit's state—it just attached a minus sign ($-$) to the front of the whole expression!
Because of this, we can write a shortcut rule for what happens when we query the box with the bottom qubit in the $\vert{}-\rangle$ state:
$$U_f \vert{}x\rangle\vert{}-\rangle = (-1)^{f(x)} \vert{}x\rangle\vert{}-\rangle$$ 
------------------------------
## Example 1: The "Constant" Box (Let's say $f(0)=0$ and $f(1)=0$)
The top qubit enters the box in a superposition of both choices: $\frac{1}{\sqrt{2}}(\vert{}0\rangle + \vert{}1\rangle)$.
Together with the bottom qubit, the total starting state entering the gate is:
$$\frac{1}{\sqrt{2}} (\vert{}0\rangle\vert{}-\rangle + \vert{}1\rangle\vert{}-\rangle)$$ 
Now, let's run the Unitary Gate $U_f$ on both pieces at the same time:

   1. For the $\vert{}0\rangle$ path: since $f(0)=0$, it gets a $(-1)^0 = +1$ multiplier.
   2. For the $\vert{}1\rangle$ path: since $f(1)=0$, it gets a $(-1)^0 = +1$ multiplier.

The state coming out of the box is:
$$\frac{1}{\sqrt{2}} (+1\vert{}0\rangle\vert{}-\rangle + 1\vert{}1\rangle\vert{}-\rangle) = \left[ \frac{1}{\sqrt{2}}(\vert{}0\rangle + \vert{}1\rangle) \right] \vert{}-\rangle$$ 
Look at the top qubit inside the brackets. It is still exactly $\frac{1}{\sqrt{2}}(\vert{}0\rangle + \vert{}1\rangle)$, which is the state $\vert{}+\rangle$.
When we hit this top qubit with the final H Gate, it turns cleanly back into a solid $\vert{}0\rangle$.

------------------------------
## Example 2: The "Balanced" Box (Let's say $f(0)=0$ and $f(1)=1$)
We start with the exact same total state entering the gate:
$$\frac{1}{\sqrt{2}} (\vert{}0\rangle\vert{}-\rangle + \vert{}1\rangle\vert{}-\rangle)$$ 
Now, let's run the Unitary Gate $U_f$ on this balanced setup:

   1. For the $\vert{}0\rangle$ path: since $f(0)=0$, it gets a $(-1)^0 = +1$ multiplier.
   2. For the $\vert{}1\rangle$ path: since $f(1)=1$, it gets a $(-1)^1 = -1$ multiplier!

The state coming out of the box is:
$$\frac{1}{\sqrt{2}} (+1\vert{}0\rangle\vert{}-\rangle - 1\vert{}1\rangle\vert{}-\rangle) = \left[ \frac{1}{\sqrt{2}}(\vert{}0\rangle - \vert{}1\rangle) \right] \vert{}-\rangle$$ 
Look at the top qubit now! Because $f(1)$ was equal to $1$, a minus sign was kicked back onto the $\vert{}1\rangle$ path. The top qubit has completely transformed into the state $\vert{}-\rangle$.
When we hit this altered top qubit with the final H Gate, the wave interference forces it to turn cleanly into a solid $\vert{}1\rangle$.

## Summary Table

| Box Type | What the Gate outputs | Top Qubit State | Final H-Gate Output |
|---|---|---|---|
| Constant | $\frac{1}{\sqrt{2}}(\vert{}0\rangle \mathbf{+} \vert{}1\rangle)\vert{}-\rangle$ | $\vert{}+\rangle$ | $\vert{}0\rangle$ |
| Balanced | $\frac{1}{\sqrt{2}}(\vert{}0\rangle \mathbf{-} \vert{}1\rangle)\vert{}-\rangle$ | $\vert{}-\rangle$ | $\vert{}1\rangle$ |

The bottom qubit acted like a mirror. Because it was in a subtraction state ($\vert{}0\rangle - \vert{}1\rangle$), whenever the oracle found a target ($f(x)=1$), it flipped the mirror, which kicked the negative sign all the way back up to that specific path on the top qubit.


