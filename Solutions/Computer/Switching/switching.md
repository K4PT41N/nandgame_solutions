# Switching
In this subcategory we implement bit selection and bit switching, the next leap from Logic Gates and Arithmetic operations.

## Selector
Based on a single bit, one input or the other will be the output. When bit **s** is 0, the **d0** input will be the output, otherwise the **d1** input will be the output. So the logic is to allow **d1** to be the output when s is 1 using an And Gate. This way the output will change only when **d1** changes, while **s** is always 1. For **d0** we do the opposite, we allow it to be the output when **s** is 0 using an And Gate, but also an Inv Gate for **s**, so that when its 0, Inv will be 1. Finally we use an Or Gate to combine both results. 

<img src="Selector-First-Solution.png" alt="Selector First Solution" width="480"/>

To get the optimal solution, replace by parts all the components and remove redundant Nand Gates. You will get the following solution.
<img src="Selector.png" alt="Selector" width="928"/>