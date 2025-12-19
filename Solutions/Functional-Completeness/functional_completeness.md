# Functional Completeness Levels
In this category, we learn about implementing alternatives to the **Nand** gate.

## Solutions Description
The solutions are similar to those in the **Computer** subcategory. We have to implement the **Nand** gate using **Nor** gates, **And** gates, and **Inv** gates. This way, we prove that we can build everything not only with **Nand** gates.

## Nand from Nor
In this level, we only get to use **Nor** gates. Since a **Nor** gate works like an **Inv** gate when both inputs have the same source, and since two **Nor** gates form an **Or** gate, we can use this to form the final **Nand** gate. We negate the inputs and pass them to an **Or** gate, which is equivalent to a **Nand** gate. The final result is optimal.

<img src="Nand(from Nor).png" alt="Nand(from Nor)" width="928"/>

## Nand from And and Invert
This level is even simpler, since we get to use the **And** gate and **Inv** gate, from which we get a **Nand** gate if they are combined.

<img src="Nand(from And and Invert).png" alt="Nand(from And and Invert)" width="928"/>
