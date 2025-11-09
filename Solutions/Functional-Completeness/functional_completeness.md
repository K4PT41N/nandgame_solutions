# Functional Completeness levels
In this category you learn about implementing alternatives to **Nand Gate**.

## Solutions description
The solutions are similar to the ones in the **Computer** subcategory. We have to implement **Nand Gate** using **Nor Gates**, **And Gates** and **Inv Gates**. This way we will prove that we can build everything not only with **Nand Gates**.

## Nand from Nor
In this level we only get to use **Nor Gates**. Since **Nor Gate** works like **Inv Gate** when both inputs have the same source, and since two **Nor Gates** form an **Or gate**, we can use this and form the final **Nand Gate**. We negate the inputs and pass them to an **Or Gate** which is equivalent to a **Nand Gate**. The final result is optimal.

<img src="Nand(from Nor).png" alt="Nand(from Nor)" width="928"/>

## Nand from And and Invert
This level is even more simple, since we get to use **And Gate** and **Inv Gate**, from which we get a **Nand Gate** if they are combined.

<img src="Nand(from And and Invert).png" alt="Nand(from And and Invert)" width="928"/>
