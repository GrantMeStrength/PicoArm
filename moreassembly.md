# Some ARM stuff

Back to some sensible, calming, rational ARM assembly as used on a regular Raspberry Pi.

## Registers

The ARM processor has:

* 16 integer registers, named r0 to r15. They are 32 bits wide.
* 32 floating point registers (wow! take that, Z80!)

## Basic math

```
mov r1, #42 		/* Move 42 into r1 */
mov r2, #1			/* Move 1 into r2 */
add r0, r1, r2		/* Move the sum of r1 and r2 into r0 */ 
add r1, r1, r2		/* Move the sum of r1 and r2 into r1 */
```

## Accessing data - and program strucuture

You must store data *aligned* properly. Also, code and data sections are defined, and registers like to use pointers rather than direct references.


```
/* myCode2.as */

.data 									/* The data section */

.balign 4								/* Align things */

theanswer:
										/* Words of data */
	.word 42	
	.word 74
	.word 16

.text									/* The code section */

.balign 4								/* Align things */

.global main							/* Main entry point */

main:
	ldr r1, pointer_to_theanswer		/* Move memory address 'theanswer' into r1 */
	ldr r0, [r1]						/* Move the contents of the address in r1 into r0 */
	bx lr 								/* return */

pointer_to_theanswer : .word theanswer	/* The pointer */


```

