# Arithmetics
In this subcategory you have to implement Addition, Subtraction and Comparison operations using Logic Gates. There will be levels with multiple outputs.

## Half Adder
This is not a very hard level to solve. Basically you have to implement the addition of two bits using Logic Gates. When both inputs are 0, output is 00. When one of the inputs is 1, the output is 01. When both inputs are 1, the output is 10, which is the binary representation of number 2. The trick is to have the first bit of the output set to 1 and the second bit set to 0 when both inputs are 1. For this we can use a gate for each output bit. So for the first bit we would get 1 only when both inputs are 1. Clearly the And gate works here. Now for the second bit, we want it set to 1 when one input is 1 and the other 0. The Xor gate works here. If we were to use the Or gate, the second output bit would be 1 when both inputs are 1 and that doesn't work, it has to be 0. So the first solution is to use And gate for the first output bit and Xor gate for the second output bit. Getting the optimal solution requires simplifying the circuits by reducing the number of Nand gates after replacing the components with parts using some intuition, eventually reaching a result similar to the [Xor optimal solution](../Logic-Gates/logic_gates.md#xor).

<img src="Half-Adder.png" alt="Half Adder" width="928"/>

## Full Adder
In this level we encounter the challenge of adding 3 bits instead of 2. The maximum value we would get by adding all the input bits is 11 which is the binary representation of number 3. As a start I added together **b** and **c** inputs using an Add component. So far we have half of the solution done. Now we have to deal with input **a** in order to have a complete solution. I added another Add component to which I attached input **a** and bit **l** from previous Add component. If we use the outputs from the second Add component as solutions, the level is still not fully solved, because we left out the output **h** from the first Add component and so, when we try to add three 1's or only inputs **b** and **c** set to 1, we don't get the desired result. We use another Add component, and we connect it to the other bit of the first Add component, the **h** output bit, and the **h** output bit of the second Add component. The final output comes from the **l** bits of both second and third Add component. We have managed to add all three bits and as a result we got a Full Adder.

<img src="Full-Adder-First-Solution.png" alt="Full Adder First Solution" width="480"/>

For the optimal solution the same strategy as before is used, just replace by parts all the components, get rid of redundant connections and apply some intuition in order to get the same results with fewer Nand gates.

<img src="Full-Adder.png" alt="Full Adder" width="928"/>