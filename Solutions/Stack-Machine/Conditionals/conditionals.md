# Conditionals levels
In this subcategory we get to implement conditional functions using the macros we've learned: and, or, not and equals. Read about [Function calls](../Function-calls/function_calls.md#function-calls-levels) first.

## And
This is an easy function to implement. We push two arguments, and perform an Bit-And operation on them. The result is pushed on the stack.
```
function and 0
    push.argument 0
    push.argument 1
    pop.D
    pop.A
    D = D & A
    push.D
return
```

Example of how it is used:
```
init.stack
push.value x0FF0
push.value x0F0F
call and 2
# inspect top of stack. Should be 0F00.
```

## Or
This function is similar to the previous one, but instead of Bit-And we use Bit-Or operation.
```
init.stack
push.value x0FF0
push.value x0F0F
call and 2
# inspect top of stack. Should be 0F00.
```

Example:
```
init.stack
push.value x0F0F
push.value x00FF
call or 2
# inspect top of stack. Should be 0FFF.
```

## Not
This function inverts the bits of the argument. Also easy to implement.
```
function not 0
    push.argument 0
    pop.D
    D = ~D
    push.D
return
```

Example:
```
init.stack
push.value x0F0F
call not 1
# inspect top of stack. Should be F0F0.
```

## Equals
Here we have to implement a function that returns 0 if two values are equal and 0xFFFF otherwise. The arguments that were pushed are first subtracted. If the result is not 0, we push 0xFFFF, otherwise we push 0.
```
function equals 0
    push.argument 0
    push.argument 1
    pop.D
    pop.A
    D = D - A
    A = true
    D; JEQ
    A = false
    D; JNE
    # true block
    label true
    D = 0
    D = D - 1
    push.D
    A = end
    JMP
    # false block
    label false
    D = 0
    push.D
    A = end
    JMP
    # end
    label end
return
```

Example:
```
nit.stack
push.value 7
push.value 7
call equals 2
# inspect top of stack. Should be xFFFF.
```