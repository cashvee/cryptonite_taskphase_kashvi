# Vault Door 7

## Description
This vault uses bit shifts to convert a password string into an array of integers. Hurry, agent, we are running out of time to stop Dr. Evil's nefarious plans! 
The source code for this vault is here: VaultDoor7.java

**flag:** picoCTF{A_b1t_0f_b1t_sh1fTiNg_07990cd3b6}

## Writeup
to decode each integer in targetValues into four ASCII characters to reconstruct the password.


Each integer holds four characters packed as bytes:
I used bit shifting to isolate each byte: value >> 24, value >> 16, value >> 8, and the last byte directly.
In a 32-bit integer:

The first 8 bits represent the first character,
The next 8 bits represent the second character,
The third 8 bits represent the third character,
The last 8 bits represent the fourth character.
By shifting:

value >> 24 moves the first 8 bits to the lowest position, isolating the first character.
value >> 16 moves the second 8 bits to the lowest position, isolating the second character.
value >> 8 does the same for the third character.
The last character doesn’t require shifting because it’s already in the correct position.

Each shift extracts a byte (8 bits) representing one character.


After decoding all characters, they were combined to form the password string.
Finally, I wrapped the password

## **bruteforce code:**
```
public class VaultDoor7 {
    public static void main(String[] args) {
        // Given integer values in the checkPassword method
        int[] targetValues = {
            1096770097, 1952395366, 1600270708, 1601398833,
            1716808014, 1734291511, 960049251, 1681089078
        };

        StringBuilder password = new StringBuilder();
        
        // Convert each integer to 4 ASCII characters and append to the password
        for (int value : targetValues) {
            password.append((char) ((value >> 24) & 0xFF));
            password.append((char) ((value >> 16) & 0xFF));
            password.append((char) ((value >> 8) & 0xFF));
            password.append((char) (value & 0xFF));
        }
        
        // Print the password in the correct format
        System.out.println("The password is: picoCTF{" + password.toString() + "}");
    }
}
```

## **source code:**
```
import java.util.*;
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;
import java.security.*;

class VaultDoor7 {
    public static void main(String args[]) {
        VaultDoor7 vaultDoor = new VaultDoor7();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
        String input = userInput.substring("picoCTF{".length(), userInput.length() - 1);
        if (vaultDoor.checkPassword(input)) {
            System.out.println("Access granted.");
        } else {
            System.out.println("Access denied!");
        }
    }

    // Each character can be represented as a byte value using its
    // ASCII encoding. Each byte contains 8 bits, and an int contains
    // 32 bits, so we can "pack" 4 bytes into a single int. Here's an
    // example: if the hex string is "01ab", then those can be
    // represented as the bytes {0x30, 0x31, 0x61, 0x62}. When those
    // bytes are represented as binary, they are:
    //
    // 0x30: 00110000
    // 0x31: 00110001
    // 0x61: 01100001
    // 0x62: 01100010
    //
    // If we put those 4 binary numbers end to end, we end up with 32
    // bits that can be interpreted as an int.
    //
    // 00110000001100010110000101100010 -> 808542562
    //
    // Since 4 chars can be represented as 1 int, the 32 character password can
    // be represented as an array of 8 ints.
    //
    // - Minion #7816
    public int[] passwordToIntArray(String hex) {
        int[] x = new int[8];
        byte[] hexBytes = hex.getBytes();
        for (int i = 0; i < 8; i++) {
            x[i] = hexBytes[i * 4] << 24
                    | hexBytes[i * 4 + 1] << 16
                    | hexBytes[i * 4 + 2] << 8
                    | hexBytes[i * 4 + 3];
        }
        return x;
    }

    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        int[] x = passwordToIntArray(password);
        return x[0] == 1096770097
                && x[1] == 1952395366
                && x[2] == 1600270708
                && x[3] == 1601398833
                && x[4] == 1716808014
                && x[5] == 1734291511
                && x[6] == 960049251
                && x[7] == 1681089078;
    }
}
```
