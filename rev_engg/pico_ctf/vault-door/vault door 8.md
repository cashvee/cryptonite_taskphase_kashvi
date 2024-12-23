## Description
Apparently Dr. Evil's minions knew that our agency was making copies of their source code, because they intentionally sabotaged this source code in order to make it harder for our agents to analyze and crack into! The result is a quite mess, but I trust that my best special agent will find a way to solve it. 
The source code for this vault is here: VaultDoor8.java

**flag:**
picoCTF{s0m3_m0r3_b1t_sh1fTiNg_89eb3994e}

## Writeup
I defined the scrambled expected array.
The unscramble method reverses the bit swaps applied in the original scrambling process.
The unscrambled characters are combined into the password and printed as picoCTF{s0m3_m0r3_b1t_sh1fTiNg_89eb3994e}.

The scramble method in VaultDoor8 scrambles each character in the password by repeatedly switching specific pairs of bits. The scramblin is:

Switch bits 1 and 2
Switch bits 0 and 3
Switch bits 5 and 6
Switch bits 4 and 7
Switch bits 0 and 1
Switch bits 3 and 4
Switch bits 2 and 5
Switch bits 6 and 7

To retrieve the original password, I reversed this scrambling sequence in the unscramble method in the brute-force code. Each bit switch operation in unscramble is the opposite of the sequence in scramble. from starting from the last operation and going backward. By applyingg this reversed sequence to each scrambled character in the expected array, I re-construct the original characters of password.


## **brute - rev engg code:**
```
import java.util.*;

public class VaultDoor8 {
    public static void main(String[] args) {
        VaultDoor8 vaultDoor = new VaultDoor8();
        char[] expected = {
            0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4,
            0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86,
            0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xC2,
            0xD2, 0x95, 0xA4, 0xF0, 0xD2, 0xD2, 0xC1, 0x95
        };

        // Unscramble the expected array to find the original password
        char[] unscrambled = vaultDoor.unscramble(expected);
        String password = new String(unscrambled);
        System.out.println("The password is: picoCTF{" + password + "}");
    }

    public char[] scramble(String password) {
        // Scramble the password by transposing pairs of bits
        char[] chars = password.toCharArray();
        for (int i = 0; i < chars.length; i++) {
            char c = chars[i];
            c = switchBits(c, 1, 2);
            c = switchBits(c, 0, 3);
            c = switchBits(c, 5, 6);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 0, 1);
            c = switchBits(c, 3, 4);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 6, 7);
            chars[i] = c;
        }
        return chars;
    }

    public char[] unscramble(char[] scrambled) {
        // Unscramble by reversing the bit switches in the opposite order
        for (int i = 0; i < scrambled.length; i++) {
            char c = scrambled[i];
            c = switchBits(c, 6, 7);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 3, 4);
            c = switchBits(c, 0, 1);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 5, 6);
            c = switchBits(c, 0, 3);
            c = switchBits(c, 1, 2);
            scrambled[i] = c;
        }
        return scrambled;
    }

    public char switchBits(char c, int p1, int p2) {
        // Move the bit in position p1 to position p2, and vice versa
        char mask1 = (char)(1 << p1);
        char mask2 = (char)(1 << p2);
        char bit1 = (char)(c & mask1);
        char bit2 = (char)(c & mask2);
        char rest = (char)(c & ~(mask1 | mask2));
        char shift = (char)(p2 - p1);
        return (char)((bit1 << shift) | (bit2 >> shift) | rest);
    }
}
```

## **source code:** (after cleanup)

// These pesky special agents keep reverse engineering our source code and then
// breaking into our secret vaults. THIS will teach those sneaky sneaks a
// lesson.
//
// -Minion #0891
import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor8 {
    public static void main(String args[]) {
        Scanner b = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String c = b.next();
        String f = c.substring(8, c.length() - 1);
        VaultDoor8 a = new VaultDoor8();

        if (a.checkPassword(f)) {
            System.out.println("Access granted.");
        }

        else {
            System.out.println("Access denied!");
        }
    }

    public char[] scramble(String password) {/* Scramble a password by transposing pairs of bits. */
        char[] a = password.toCharArray();
        for (int b = 0; b < a.length; b++) {
            char c = a[b];
            c = switchBits(c, 1, 2);
            c = switchBits(c, 0, 3); /* c = switchBits(c,14,3); c = switchBits(c, 2, 0); */
            c = switchBits(c, 5, 6);
            c = switchBits(c, 4, 7);
            c = switchBits(c, 0, 1); /* d = switchBits(d, 4, 5); e = switchBits(e, 5, 6); */
            c = switchBits(c, 3, 4);
            c = switchBits(c, 2, 5);
            c = switchBits(c, 6, 7);
            a[b] = c;
        }
        return a;
    }

    public char switchBits(char c, int p1, int p2) {/*
                                                     * Move the bit in position p1 to position p2, and move the bit
                                                     * that was in position p2 to position p1. Precondition: p1 < p2
                                                     */

        char mask1 = (char) (1 << p1);
        char mask2 = (char) (1 << p2); /* char mask3 = (char)(1<<p1<<p2); mask1++; mask1--; */
        char bit1 = (char) (c & mask1);
        char bit2 = (char) (c & mask2); /*
                                         * System.out.println("bit1 " + Integer.toBinaryString(bit1));
                                         * System.out.println("bit2 " + Integer.toBinaryString(bit2));
                                         */
        char rest = (char) (c & ~(mask1 | mask2));
        char shift = (char) (p2 - p1);
        char result = (char) ((bit1 << shift) | (bit2 >> shift) | rest);
        return result;
    }

    public boolean checkPassword(String password) {
        char[] scrambled = scramble(password);
        char[] expected = { 0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4, 0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4,
                0x86, 0xD0, 0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xC2, 0xD2, 0x95, 0xA4, 0xF0, 0xD2, 0xD2, 0xC1, 0x95 };
        return Arrays.equals(scrambled, expected);
    }
}
```
