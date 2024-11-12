**file named: sample.c**

`include <stdio.h>
int main() 
{
    int num = 5;
    printf("Number: %d\n", num);
    return 0;
}`

**Compile the program to assembly:**
`gcc -S -o sample.s sample.c`

**converting it back to C**
using decompilers like Ghidra or objdump disassembly

`gcc -o sample_program sample.s`

`objdump -d sample_program`

shows a disassembly of the program, which one can interpret to manually reconstruct the C logic.


