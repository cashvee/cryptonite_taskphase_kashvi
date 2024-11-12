## Description
What integer does this program print with argument 3297082261? 
File: chall_2.S 

**flag:** picoCTF{4d9072bf}

```
func1:
        sub     sp, sp, #32
        str     w0, [sp, 12]
        str     wzr, [sp, 24]
        str     wzr, [sp, 28]
        b       .L2
.L3:
        ldr     w0, [sp, 24]
        add     w0, w0, 3
        str     w0, [sp, 24]
        ldr     w0, [sp, 28]
        add     w0, w0, 1
        str     w0, [sp, 28]
.L2:
        ldr     w1, [sp, 28]
        ldr     w0, [sp, 12]
        cmp     w1, w0
        bcc     .L3
        ldr     w0, [sp, 24]
        add     sp, sp, 32
        ret
        .size   func1, .-func1
        .section        .rodata
        .align  3
.LC0:
        .string "Result: %ld\n"
        .text
        .align  2
        .global main
        .type   main, %function
main:
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

#### Objective
To fibd the output for the argument `3297082261`.

#### Code Analysis

1. **Initial Setup**:
   - `[sp, 12]` stores `3297082261` (ourr input).
   - `[sp, 24]` and `[sp, 28]` start at 0.

2. **Loop**:
   - In each loop iteration:
     - `[sp, 24]` increments by 3.
     - `[sp, 28]` increments by 1.
   - Loop continues until `[sp, 28]` matches `3297082261`.

3. **Final Calculation**:
   - After `3` iterations:
     - `[sp, 24] = 3297082261 * 3 = 9891246783`.

4. **Result**:
   - Program prints `Result: 9891246783`.
  
     thus, our flag is the hex value of 9891246783.

---

