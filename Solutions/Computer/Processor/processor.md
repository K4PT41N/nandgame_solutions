
# Processor
In this subcategory, we will use all the components we've made to create the **Computer**. The levels are about putting these components together and connecting the inputs and outputs appropriately.


## Combined Memory
This is a very easy level; we get the solution by following the instructions on the page. We just have to use two **Registers** and one **RAM** and connect the nodes as explained. One thing to note: the **A register** is the address of the value stored in the **A register**. Hard to fail.

<img src="Combined-Memory.png" alt="Combined Memory" width="928"/>


## ALU Instruction
This level is about splitting a 16-bit value, which represents an instruction, with each bit specifying which operation should be executed and where the results should be stored. Again, the solution is very straightforward.

<img src="ALU-Instruction.png" alt="ALU Instruction" width="928"/>


## Control Selector
Here, we just switch between the values of multiple control buses. A control bus carries commands from the CPU along with status messages from other components. The solution is easy to implement.

<img src="Control-Selector.png" alt="Control Selector" width="928"/>


## Control Unit
This level provides an overview of how instructions are carried and written to the register. Based on the instruction's 15th bit, either a data instruction or an ALU instruction is executed.

<img src="Control-Unit.png" alt="Control Unit" width="928"/>


## Computer
Finally, we get to connect everything. We use a clock to trigger every cycle. We trigger the **Counter** to increment the value of the address selected in the **ROM** component. The value at the address selected in the **ROM** is the instruction command we send to the **Control Unit**. The **Control Unit** has access to the registers and **RAM**, and the output is then sent to the memory. The memory provides an address to the **Counter**, which is then incremented, but the **Counter** will restore the initial address if the output of the **ALU** passes the conditions that were set in the instruction. We finally get a functioning basic **Computer** that has a CPU, memory, and a control bus.

<img src="Computer.png" alt="Computer" width="928"/>


## Input and Output
This additional level is about understanding how input and output signals work. This is an easy level to follow.

<img src="Input-and-Output.png" alt="Input and Output" width="928"/>
