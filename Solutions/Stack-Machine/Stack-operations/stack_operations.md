# Stack operations
In this subcategory we have to implement operations on the memory stack, like initializing the stack, storing and extracting values in an organize way using LIFO principle (Last in, First out).

## Init stack
To implement a stack first we need to store somewhere the memory address were the stack starts. The address of the stack is the value of the **Stack Pointer**(SP), which is 0x100, and this value will be where we start storing values. In the future, we will have to increment the **Stack Pointer** each time we push a value and decrement it each time we pop a value. The **Stack Pointer** will always point at memory location that stores the last element pushed on the stack.
```
A = 0x100
D = A
A = SP
*A = D
```

If we wanted to call the macro that initializes our stack we would use:
```
init.stack
```

## Push D
Implementing the push operation is easy. We access the **Stack Pointer** memory address where we write the value from **D** register, and then we increment the **Stack Pointer** for future operations.
```
A = SP
A = *A
*A = D
A = SP
*A = *A+1
```

This is how we store values on stack memory:
```
init.stack
D = 1
push.d
```

## Pop D
Another easy task is the **pop** operation. The idea is to extract the last value from the stack and store it on **D** register. This is basically the reverse of **push.d** operation. We access the address of the last pushed value, store it on **D** register, then decrement the **Stack Pointer**.
```
A = SP
A = *A - 1
D = *A
A = SP
*A = *A - 1
```

After pushing a value on the stack, then popping the value on register **D**, we expect register **D** to store the value from the stack.
```
init.stack
D = 1
push.d
A = 0x42
D = A
pop.D
# inspect D. Should be 1.
```

## Pop A
We can implement a different **pop** operation, one that doesn't use the register **D**. This way we can pop values without affecting the **D** register.
```
A = SP
*A = *A - 1
A = *A
A = *A
```

A clear example of the advantage of using **pop.A** is here:
```
init.stack
D = 1
push.D
A = 0x42
D = A
pop.A
# inspect A. Should be 1.
# inspect D - should be 0x42
```

## Push Value
We simplify the **push** operation even more, by assigning the **value** input to the **D** register through register **A** and then pushing from register **D**.
```
A = value
D = A
push.D
```

Here is an example:
```
init.stack
push.value 114
# Inspect stack: top should be 114
```

## Push Static
In this level we get to implement a **push** operation that stores a value from a memory address on the stack. This operation will take a memory address and push the value that is stored there directly on the stack.
```
A = address
D = *A
push.D
```

This is how the macro is used:
```
init.stack
# store 42 at address 16
A = 42
D = A
A = 16
*A = D
push.static 16
# top of stack should be 42
```

## Pop Static
This is the reverse of the **push.static** operation, in which we pop a value on the address passed to the macro.
```
pop.D
A = address
*A = D
```

Example:
```
init.stack
push.value 42
pop.static 0x16
# address 16 should have value 42
```

## Push Memory
This is another special **push** operation. It pushes the value at the address stored on the top of the stack. So it first pops the stack, reads the value on the address that was popped and pushes that value on the stack.
```
pop.D
A = D
D = *A
push.D
```

Here is an example:
```
init.stack
# store 42 at address 16
A = 42
D = A
A = 16
*A = D

push.value 16
push.memory
# top of stack should have value 42
```

## Pop Memory
This **pop** operation is easy to implement. We pop two values and the second value popped is the address at which we store the first value popped.
```
pop.D
pop.A
*A = D
```

This is how its used:
```
init.stack
push.value 16
push.value 42
pop.memory
# address 16 should have value 42
```