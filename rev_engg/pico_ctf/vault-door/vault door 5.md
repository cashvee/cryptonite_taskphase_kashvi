# Vault Door 5

## Description
In the last challenge, you mastered octal (base 8), decimal (base 10), and hexadecimal (base 16) numbers, but this vault door uses a different change of base as well as URL encoding! 
The source code for this vault is here: VaultDoor5.java

## **Writeup**
In this challenge, the checkPassword function in VaultDoor5 first URL-encodes the input password and then encodes the result in Base64 to check against a given encoded string.

To solve it, I reversed this encoding process in my brute-force code (Vault5_rev). 
Starting with the expected Base64 string, I decoded it to get a URL-encoded string. 
Then, I decoded that string from URL encoding to reveal the actual password.

This final decoded password provides the input required to unlock the vault and retrieve the flag.
The Base64.getDecoder().decode() function in Java is used to decode a Base64-encoded string into its original byte array form.

```
Base64.getDecoder(): This part retrieves an instance of the Base64 decoder.
.decode(String): This method of the decoder instance takes a Base64-encoded string as input and returns the decoded data as a byte array.
```


**FLAG:** picoCTF{c0nv3rt1ng_fr0m_ba5e_64_e3152bf4}

## **brute force code i used:**
```
import java.net.URLDecoder;
import java.util.Base64;

public class Vault5_rev {
    public static void main(String[] args) throws Exception
{
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                + "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0";

        // Decode from base64
        byte[] base64DecodedBytes = Base64.getDecoder().decode(expected);
        String urlEncodedString = new String(base64DecodedBytes);

        // Decode from URL encoding
        String password = URLDecoder.decode(urlEncodedString, "UTF-8");

        System.out.println("Decoded password: " + password);
    }
}
```


## **source code:**
```
import java.net.URLDecoder;
import java.util.*;

class VaultDoor5 {
    public static void main(String args[]) {
        VaultDoor5 vaultDoor = new VaultDoor5();
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

    // Minion #7781 used base 8 and base 16, but this is base 64, which is
    // like... eight times stronger, right? Riiigghtt? Well that's what my twin
    // brother Minion #2415 says, anyway.
    //
    // -Minion #2414
    public String base64Encode(byte[] input) {
        return Base64.getEncoder().encodeToString(input);
    }

    // URL encoding is meant for web pages, so any double agent spies who steal
    // our source code will think this is a web site or something, defintely not
    // vault door! Oh wait, should I have not said that in a source code
    // comment?
    //
    // -Minion #2415
    public String urlEncode(byte[] input) {
        StringBuffer buf = new StringBuffer();
        for (int i=0; i<input.length; i++) {
            buf.append(String.format("%%%2x", input[i]));
        }
        return buf.toString();
    }

    public boolean checkPassword(String password) {
        String urlEncoded = urlEncode(password.getBytes());
        String base64Encoded = base64Encode(urlEncoded.getBytes());
        String expected = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"
                        + "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"
                        + "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0";
        return base64Encoded.equals(expected);
    }
}
```
