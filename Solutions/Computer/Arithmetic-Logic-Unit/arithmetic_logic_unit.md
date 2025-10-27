# Arithmetic Logic Unit
This subcategory is about making the ALU component which is composed of an arithmetic unit and a logic unit. Both units are made out of arithmetic components and switches.

## Logic Unit
Super easy level, since you will have to use almost all the components from the Toolbox. You add the logic gates, bind them to the input and then you add three Select components to select between operations based on **op1** and **op2** bits.

<img src="Logic-Unit.png" alt="Logic Unit" width="928"/>

## Arithmetic Unit
Another easy level where you have to use almost all of the components from the Toolbox. Solution is similar to the previous level, but here you need to select first between inputs and then use the output of these selects for the arithmetic components.

<img src="Arithmetic-Unit.png" alt="Arithmetic Unit" width="928"/>

## ALU
Again this level is not that complicated, because the same idea is used. Select first the inputs which are then used by the Arithmetic Unit and Logic Unit.

<img src="ALU.png" alt="ALU" width="928"/>

## Condition
Not a very hard level, but it takes some time to optimize it. First you need to combine the condition bits with the input using logic gates and conditional gates. This requires basic logic knowledge, compounding Is Zero and Is Neg to get a less than or equal to zero condition for example, and so on. When you've finished implementing all these conditions, you need to replace by parts and remove redundant Nand Gates along with using some intuition to remove even more redundant connections.

<img src="Condition.png" alt="Condition" width="928"/>