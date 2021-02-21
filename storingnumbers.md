# Storing numbers

Use the opcode ```str``` to save into memory, thus:

```
	mov r0, #42
	ldr r1, pointer_to_variable
	str r0, [r1]
```

This will store 42 into the memory address pointed to by *pointer_to_variable*.


## Dissassembling

```
gdb ./mycode
start
disassemble
```

## Branching

```
b <address> - unconditional branch
cmp r1, r0
beq <address> - branch if equal
bne <address> - branch if not equal
bge <address> - branch if greater than
```

..and lots more.

