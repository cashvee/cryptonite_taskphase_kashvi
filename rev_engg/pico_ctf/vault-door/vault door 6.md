# Vault Door 6 

## Description
This vault uses an XOR encryption scheme. 
The source code for this vault is here: VaultDoor6.java

**flag**: picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_948b888}

## **Writeup** 
In the brute-force code, I decoded the password by reversing the XOR encryption used:

1. The given `myBytes` array contains XOR-encrypted values.
2. I XOR each byte in `myBytes` with `0x55` to get the original characters of the password.
3. I then convert each decoded byte to a character and build the password string.

The final decoded password is printed as the output.

## **Brute Force Codw**
```
class VaultDoor6brute {
    public static void main(String[] args) {
        byte[] myBytes = {
                0x3b, 0x65, 0x21, 0xa, 0x38, 0x0, 0x36, 0x1d,
                0xa, 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa,
                0x21, 0x1d, 0x61, 0x3b, 0xa, 0x2d, 0x65, 0x27,
                0xa, 0x6c, 0x61, 0x6d, 0x37, 0x6d, 0x6d, 0x6d,
        };

        StringBuilder password = new StringBuilder();

        for (int i = 0; i < 32; i++) {
            byte decodedByte = (byte) (myBytes[i] ^ 0x55);
            password.append((char) decodedByte);
        }

        System.out.println("The password is: " + password.toString());
    }
}

```
## **Source Code**
```
import java.util.*;

class VaultDoor6 {
    public static void main(String args[]) {
        VaultDoor6 vaultDoor = new VaultDoor6();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Dr. Evil gave me a book called Applied Cryptography by Bruce Schneier,
    // and I learned this really cool encryption system. This will be the
    // strongest vault door in Dr. Evil's entire evil volcano compound for sure!
    // Well, I didn't exactly read the *whole* book, but I'm sure there's
    // nothing important in the last 750 pages.
    //
    // -Minion #3091
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        byte[] passBytes = password.getBytes();
        byte[] myBytes = {
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x61, 0x6d, 0x37, 0x6d, 0x6d, 0x6d,
        };
        for (int i=0; i<32; i++) {
            if (((passBytes[i] ^ 0x55) - myBytes[i]) != 0) {
                return false;
            }
        }
        return true;
    }
}

```
