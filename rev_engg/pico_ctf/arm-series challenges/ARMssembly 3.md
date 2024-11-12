## Description
What integer does this program print with argument 469937816? 
File: chall_3.S 

**FLAG:** picoCTF{00000024}

```
func1:
        stp     x29, x30, [sp, -48]!
        add     x29, sp, 0
        str     w0, [x29, 28]
        str     wzr, [x29, 44]
        b       .L2

.L4:
        ldr     w0, [x29, 28]
        and     w0, w0, 1
        cmp     w0, 0
        beq     .L3
        ldr     w0, [x29, 44]
        bl      func2
        str     w0, [x29, 44]

.L3:
        ldr     w0, [x29, 28]
        lsr     w0, w0, 1
        str     w0, [x29, 28]
.L2:
        ldr     w0, [x29, 28]
        cmp     w0, 0
        bne     .L4
        ldr     w0, [x29, 44]
        ldp     x29, x30, [sp], 48
        ret
        .size   func1, .-func1
        .align  2
        .global func2
        .type   func2, %function

func2:
        sub     sp, sp, #16
        str     w0, [sp, 12]
        ldr     w0, [sp, 12]
        add     w0, w0, 3
        add     sp, sp, 16
        ret
        .size   func2, .-func2
        .section        .rodata
        .align  3

.LC0:
        .string "Result: %ld\n"
        .text
        .align  2
        .global main
        .type   main, %function   

ain:
        stp     x29, x30, [sp, -48]!
        add     x29, sp, 0
        str     w0, [x29, 28]
        str     x1, [x29, 16]
        ldr     x0, [x29, 16]
        add     x0, x0, 8
        ldr     x0, [x0]
        bl      atoi
        bl      func1
        str     w0, [x29, 44]
        adrp    x0, .LC0
        add     x0, x0, :lo12:.LC0
        ldr     w1, [x29, 44]
        bl      printf
        nop
        ldp     x29, x30, [sp], 48
        ret
        .size   main, .-main
        .ident  "GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
        .section        .note.GNU-stack,"",@progbits   
```

#### Analysis of the Codw:

1. **Initial**:
   - `[x29, 28]` stores the input `469937816`.
   - `[x29, 44]` initializes to `0`.

2. **Loop**:
   - In each iteration, the program:
     - Checks if `[x29, 28]` is odd using `and w0, w0, 1`.
     - If odd, it calls `func2`, which adds **3** to `[x29, 44]`
     - Right shifts `[x29, 28]` by 1.
   - Loop continues until `[x29, 28]` becomes `0`.

3. **`func2`**:
   - Adds **3** to `[x29, 44]` each time its called.

4. **Result**:
   - The result is the total sum of **3** added to `[x29, 44]` each time an odd bit is encountered in `[x29, 28]`.
   - Since `469937816` in binary has **12 odd bits**, `[x29, 44]` is `3 * 12 = 36`.

5. **Output**:
   - Program prints `Result: 36`.
  
     hex of 36 is 0x24 which is our flag.


                                                                                                                 
