Description
For what argument does this program print `win` with variables 68, 2 and 3? 
File: chall_1.S 
Flag format: picoCTF{XXXXXXXX} -> (hex, lowercase, no 0x, and 32 bits. ex. 5614267 would be picoCTF{0055aabb})

90 in hex: 0000005a

**flag:** picoCTF{0000005a}

wget https://mercury.picoctf.net/static/d6c56d724795c006b319c6aa6a09140e/chall_1.S
(the link address of the challenge file)

vi chall_2.S 
vi chall.S will open the file chall.S in the Vi editor

func:
        sub     sp, sp, #32
        str     w0, [sp, 12]
        mov     w0, 68
        str     w0, [sp, 16]
        mov     w0, 2
        str     w0, [sp, 20]
        mov     w0, 3
        str     w0, [sp, 24]

stack + 12 = user input
stack + 16 = 68
stack + 20 = 2
stack + 24 = 3

        ldr     w0, [sp, 20] --> load "2" into w0
        ldr     w1, [sp, 16] -->
        lsl     w0, w1, w0
        str     w0, [sp, 28]


        ldr     w1, [sp, 28]
        ldr     w0, [sp, 24]
        sdiv    w0, w1, w0
        str     w0, [sp, 28]
stack + 12 = user input
stack + 16 = 68
stack + 20 = 2
stack + 24 = 3
stack + 28 = 90

        ldr     w1, [sp, 28]
        ldr     w0, [sp, 12]
        ⭐sub     w0, w1, w0
        str     w0, [sp, 28]
        ldr     w0, [sp, 28]
        add     sp, sp, 32


        ret
        .size   func, .-func
        .section        .rodata
        .align  3

.LC0:
        .string "You win!"
        .align  3
.LC1:
        .string "You Lose :("
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
        str     w0, [x29, 44]
        ldr     w0, [x29, 44]
        bl      func
        **cmp     w0, 0**  --> We want the w0 variable to be 0! If it's not, we branch to .L4 which branches to .L1, and we don't want the result to be .L1 but .L0:
   since we want w0 to be 0, **⭐sub w0, w1, w0** which is 90-user input being stored in w0, here user input should be 90 to get 0. thus, the argument is 90

        bne     .L4
        adrp    x0, .LC0
        add     x0, x0, :lo12:.LC0
        bl      puts
        b       .L6
.L4:
        adrp    x0, .LC1 -->branching to LC1
        add     x0, x0, :lo12:.LC1
        bl      puts

.L6:
        nop
        ldp     x29, x30, [sp], 48
        ret
        .size   main, .-main
        .ident  "GCC: (Ubuntu/Linaro 7.5.0-3ubuntu1~18.04) 7.5.0"
        .section        .note.GNU-stack,"",@progbits