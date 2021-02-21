# Building an Assembly Language Project

Now I'm switching over to a [Thinkingeek guide](https://thinkingeek.com/2013/01/09/arm-assembler-raspberry-pi-chapter-1/) I found.

It looks like either by default, or by installing the SDK and tools, the correct assembler has been installed. And so I can write and run my very first sample assembly language program, and run it on the Raspberry Pi that I'm logged into (not the Pico!)

```
/* myCode.as */

.global main

main:
	mov r0, #2
	bx lr
	
```

and assemble it:

```
as -o mycode.o mycode.s

```

and link it:

```
gcc -o mycode mycode.o
```

and run it:

```
./mycode

```

As expected, this does nothing. BUT AT LEAST IT DIDN'T CRASH!

If you call it like this:

```
./mycode ; echo $?
```

then the contents of r0 will be displayed.

## Thoughts..

Q. Would this run on the Pico if it was built into the right format? The Pico has a similar/same CPU?

Q. What other magic will it take in order to create the .uf file format that the Pico likes?

Q. How can I write assembler that makes the LED blink, so I know I've done it right?

