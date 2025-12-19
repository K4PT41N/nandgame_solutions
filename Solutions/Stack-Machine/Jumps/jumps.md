
# Jumps
In this subcategory, we simplify jump operations by reducing code using macros.

## Goto
In this level, we implement the **goto** macro, which only takes a label and jumps to the label address.
```
A = label
JMP
```

Example:
```
init.stack
push.value x42
goto end
# this line should not be executed:
push.value x17
label end:
# top of stack should be x42
```

## If Goto
Here, we have to implement a conditional jump using the top value on the stack. If it's non-zero, the program jumps to the label location.
```
pop.D
A = label
D; JNE
```

Example:
```
init.stack
push.value 0
if.goto end
# this line should be executed
push.value 1
if.goto end
# this line should not be executed:
push.value x17
label end:
```