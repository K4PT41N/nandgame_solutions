
# Logic Gates
In this subcategory, you must implement the fundamental logic gates that will be used to build more complex components.


## Nand
To implement a **Nand** gate using relays, you need to add one **default off relay** connected to both inputs and one **default on relay** connected to the **default off relay** and the power input. This way, the output will always be 1 except when both inputs, **a** and **b**, are 1. In that case, the current flows through a **default on relay**, and both **a** and **b** inputs must be 1 for the **default on relay** to switch off.

<img src="Nand.png" alt="Nand" width="928"/>


## Invert
This level is easier. You have to use one **Nand** gate to implement an **Invert** gate. It is pretty straightforward: just connect both **Nand** gate input nodes to the same input bit. This will output 1 when the input bit is 0, and 0 when the input bit is 1. This one is hard to get wrong.

<img src="Invert.png" alt="Invert" width="928"/>


## And
This is another easy level. From here, you begin to combine different components from the toolbox and start to find solutions using logic tables and by combining logic operators. What happens now? You combine **Nand** and **Invert**, since **Nand** is **Not And**, so negating it will give you **And**. Two negatives make a positive. Use a **Nand** gate and then pass the output to an **Invert** gate. Voilà, the **And** gate!

<img src="And.png" alt="And" width="928"/>


## Or
This one is easy, but not quite "Tutorial Mode" easy. Some logic operator theory is useful here. If you look into this field, you'll learn about De Morgan's Laws. The `negation of A and B` is the same as `negation of A or negation of B`. Similarly, the `negation of A or B` is the same as `negation of A and negation of B`. We can deduce from these laws that `A or B` comes from the `negation of not A and not B`. We have just the right tools to implement the **Or** gate: invert the inputs and pass them through the **Nand** gate.
- `not (A or B) = (not A) and (not B)`
- `not (A and B) = (not A) or (not B)`
- `not (not A and not B) = not (not A) or not (not B) = A or B`

<img src="Or.png" alt="Or" width="928"/>


## Xor
This is an interesting logic gate: it outputs 1 only when both inputs are different. You need to combine different logic gates by passing the **Nand** and **Or** results to an **And** gate.

<img src="Combining-Gates.png" alt="Combining Gates" width="640"/>


Getting an optimal solution requires replacing the components with parts and using some intuition. Fast forward, and we get the optimal solution.

<img src="Xor.png" alt="Xor" width="928"/>