# Function calls levels
In this subcategory we learn about the function call and we will get to implement some simple functions later. A function consists of three parts: the function call, the function content and the return. 

## Call
In this level we will implement the function call macro. The idea is to use the stack where we prepare the data for the function call, such as the address pointing to the arguments location or local variable locations. We also store the **return** address after the function execution is finished and then proceed with restoring the initial state of the stack before the function was called.

We push the address of the arguments, the address of the locals, and the address of the location right after the jump to where the function is executed.
```
push.static ARGS
push.static LOCALS
push.value after
```

We then update the value on ARGS address by subtracting the number of arguments we pushed before the function call and the number of arguments we previously pushed in the function call, which is 3, from the value of the **Stack Pointer**.
```
A = SP
D = *A
A = argumentCount
D = D - A
A = 3
D = D - A
A = ARGS
*A = D
```

After that we proceed with jumping to the function block. Right after this jump, we must write the label (**after**) we previously pushed on the stack for the return address.
```
goto functionName
label after
```

When the programs returns from the function, we have to temporarily store the current ARGS value. 
```
A = ARGS
D = *A
A = TEMP_ADDR
*A = D
```

After that we pop the stack, which is the **LOCAL** address we stored at the beginning, and then we do the same for the **ARGS**. 
```
pop.D
A = LOCALS
*A = D
pop.D
A = ARGS
*A = D
```

We then set the **Stack Pointer** to the temporarily stored **ARGS** address. 
```
A = ARGS
*A = D
A = TEMP_ADDR
D = *A
A = SP
*A = D
```

At last, we access the address on **RETVAL** and push the return value on stack.
```
A = RETVAL
D = *A
push.D
```

In the end we managed to prepare the stack before executing the instructions in the function and then restore the program state before the call, after the function finished executing.

The final code can be found here: [Call solution](./Call.txt)

## Function
The function macro adjusts the stack for local storage. We make space by saving the current **Stack Pointer** value on **LOCALS** address then incrementing the **Stack Pointer** to the number of local values we want to use.

First we define the label where we jump during the call.
```
label functionName 
```

Then we save the current **Stack Pointer** on the **LOCALS** address.
```
A = SP
D = *A
A = LOCALS
*A = D
```

Finally we update the **Stack Pointer**, by adding the number of local values we are gonna use, which means we are making space.
```
A = localsCount
D = A
A = SP
D = D + *A
*A = D
```

## Return
This part prepares the end of the function block by storing the return value at **RETVAL** address and restoring the previous **Stack Pointer** value at the beginning of the function block.

So we first pop the return value we would push at the end of a function and store it at **RETVAL** address.
```
pop.D
A = RETVAL
*A = D
```

Next we restore the **Stack Pointer** we previously stored on **LOCALS** address.
```
A = LOCALS
D = *A
A = SP
*A = D
```

Finally we pop the return address of the instruction after the jump instruction to the function block, from the call macro.
```
A = LOCALS
D = *A
A = SP
*A = D
```

## Push argument
This macro is used inside the function to push values on stack indexed from **ARGS** address. We first get access to argument we want to push by adding an index to the **ARGS** address, and then we push this value on the stack.
```
A = ARGS
D = *A
A = index
D = D + A
A = D
D = *A
push.D
```

## Pop argument
This macro is also used inside the function to pop a value from the stack and store it on an addressed indexed from **ARGS** address. First we need to calculate the address where we want to store the top stack value, and then store this address on a temporary memory slot
```
#Calculate memory address where to write
A = ARGS
D = *A
A = index
D = D + A
A = TEMP_ADDR
*A = D
```

After we stored the memory address, we pop the top stack value and store it on that address.
```
pop.D
A = TEMP_ADDR
A = *A
*A = D
```

## Add
Since we are done implementing all the needed macros for a function call, we are now able to create functions that simplify our code. A basic function is the add function, where we push 2 values, call a function and return their sum.

We define the function name and the number of local variable it needs (in our case it is 0). Then we push the arguments on top of the stack, which we will then pop. We add these two values and then we push the result before calling **return**.
```
function add 0
    push.argument 0
    push.argument 1
    pop.D
    pop.A
    D = D + A
    push.D
return 
```

Here is an example where we push two arguments and call the add function:
```
init.stack
push.value 7
push.value 3
call add 2
# Return value should be 10
```

## Sub
A similar level, but instead of the addition we implement the subtraction of two arguments. In this case the order of the arguments matter. The first argument we push is the one we subtract from.
```
function sub 0
    push.argument 0
    push.argument 1
    pop.D
    pop.A
    D = A - D
    push.D
return
```

This is an example:
```
init.stack
push.value 7
push.value 3
call sub 2
# Return value should be 4
```

## Negate
We also get to implement the negate function. We push a value and we return its negative.
```
function negate 0
    push.argument 0
    pop.D
    D = -D
    push.D
return
```

Example:
```
init.stack
push.value 7
call negate 1
# Return value should be -7
```

## getChar
In this level we implement a function that returns user key press. It first waits for a button press then it stores the key code as the return value and then it waits for a button release to exit the function. We check the input using the keyboard input address. As long as it is 0, we have no input. When its non-zero, we register the input and push it to the stack. Then another loop starts that waits for the input to be 0 again, until the button is not pressed anymore.
```
function getChar 0
    label loop_press
    A = 0x6000
    D = *A
    A = loop_press
    D; JEQ
    push.D
    label loop_release
    A = 0x6000
    D = *A
    A = loop_release
    D; JNE
return
```

This is how the function is used:
```
init.stack
call getChar 0
# type a character. The character code should be pushed to the stack.
```

## putChar
In this level we implement another easy function. Using this function we can send inputs to a typewriter. We just have to get the argument value we want to send, and store it on the typewriter input address.
```
function putChar 0
    push.argument 0
    pop.D
    A = 0x6002
    *A = D
return
```

Example:
```
# ASCII code for 'A' is 0x0041
push.value 0x0041
call putChar 1
# Inspect typewriter. Should write the letter 'A'.
```