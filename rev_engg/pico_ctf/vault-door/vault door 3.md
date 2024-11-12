#Vault Door3

##Description
This vault uses for-loops and byte arrays. 
The source code for this vault is here: VaultDoor3.java

**flag:**
picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_79958f}


**brute force code I used to get flag:**
`import java.util.*;

class VaultDoor3brute {
    public static void main(String args[]) {
        VaultDoor3brute vaultDoor = new VaultDoor3brute();
        String requiredPassword = vaultDoor.revealPassword();
        System.out.println("The correct password should be: picoCTF{" + requiredPassword + "}");
    }

    public String revealPassword() {
        // Target password string we want in the buffer
        String target = "jU5t_a_sna_3lpm18g947_u_4_m9r54f";
        char[] password = new char[32];

        int i;
        // Reverse-engineer each segment to find the needed password characters
        for (i = 0; i < 8; i++) {
            password[i] = target.charAt(i);
        }
        for (; i < 16; i++) {
            password[23 - i] = target.charAt(i);
        }
        for (; i < 32; i += 2) {
            password[46 - i] = target.charAt(i);
        }
        for (i = 31; i >= 17; i -= 2) {
            password[i] = target.charAt(i);
        }

        return new String(password);
    }
}
`

**source code:**
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
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

    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;

        for (i = 0; i < 8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i < 16; i++) {
            buffer[i] = password.charAt(23 - i);
        }
        for (; i < 32; i += 2) {
            buffer[i] = password.charAt(46 - i);
        }
        for (i = 31; i >= 17; i -= 2) {
            buffer[i] = password.charAt(i);
        }

        // Print the buffer to reveal the password
        String reconstructedPassword = new String(buffer);
        System.out.println("Password should be: " + reconstructedPassword);

        return reconstructedPassword.equals("jU5t_a_sna_3lpm18g947_u_4_m9r54f");
    }
}

