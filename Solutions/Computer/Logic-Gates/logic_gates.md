# Logic Gates
In this subcategory you have to implement the fundamental logic gates that will be used to build more complex components.

## Nand
To implement **Nand Gate** using relays you will have to add one **default off relay** connected to both inputs and one **default on relay** connected to the **default off relay** and the power input. This way, the output will always be 1 except when both inputs, **a** and **b**, are 1, since the current flows through a **default on relay**, and both **a** and **b** inputs need to be 1 for the **default on relay** to switch off.

<img src="Nand.png" alt="Nand" width="928"/>

## Invert
This level is easier. You have to use one **Nand Gate** to implement **Invert Gate**. It is pretty straight forward, you just connect both **Nand Gate** input nodes to the same input bit, which will then output 1 when the input bit is 0, and 0 when input bit is 1. This one is hard to fail.

<img src="Invert.png" alt="Invert" width="928"/>

## And
We encounter another easy level. From here you begin to combine different components from the tool box and you start to find solutions using logic tables and combining logic operators. So what happens now? You combine **Nand** and **Invert**, since **Nand** is **Not And**, so negating it will give you **And**. Two negatives is a positive. So use a **Nand Gate** and then pass the output to an **Invert Gate**. Voila, the **And Gate**!

<img src="And.png" alt="And" width="928"/>

## Or
This one is easy, but not Tutorial Mode easy. Some Logic Operator Theory would be useful. Digging a little into this field you will learn about De Morgan's Laws. The ```negation of A and B``` is same as ```negation of A or negation of B```. Similarly, the ```negation of A or B``` is same as ```negation of A and negation of B```. We can deduce from these laws that ```A or B``` comes from the ```negation of not A and not B```. We have just the right tools to implement **Or Gate**, we just have to invert the inputs and pass them through the Nand Gate.
- ```not (A or B) = (not A) and (not B)```
- ```not (A and B) = (not A) or (not B)```
- ```not (not A and not B) = not (not A) or not (not B) = A or B```

<img src="Or.png" alt="Or" width="928"/>

## Xor
This is an interesting Logic Gate, it outputs 1 only when both inputs are different. You need to combine different logic gates by passing the **Nand** and **Or** results to an **And Gate**.

<img src="Combining-Gates.png" alt="Combining Gates" width="640"/>

Getting an optimal solution requires replacing the components with parts and using some intuition. Fast forward, we get the optimal solution.

<img src="Xor.png" alt="Xor" width="928"/>