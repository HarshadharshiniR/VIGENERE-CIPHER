# VIGENERE-CIPHER
## EX. NO: 4
### NAME   : HARSHADHARSHINI R
### Reg no : 212224230089

## IMPLEMETATION OF VIGENERE CIPHER
 


## PROGRAM
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to perform Vigenere encryption
void vigenere_encrypt(char text[], char key[], char result[]) {
    int i, j = 0;
    int keyLength = strlen(key);

    for (i = 0; text[i] != '\0'; i++) {
        char ch = text[i];

        if (isalpha(ch)) {
            char base = isupper(ch) ? 'A' : 'a';
            int k = toupper(key[j % keyLength]) - 'A';

            result[i] = ((ch - base + k) % 26) + base;
            j++;
        } else {
            result[i] = ch;
        }
    }

    result[i] = '\0';
}

// Function to perform Vigenere decryption
void vigenere_decrypt(char text[], char key[], char result[]) {
    int i, j = 0;
    int keyLength = strlen(key);

    for (i = 0; text[i] != '\0'; i++) {
        char ch = text[i];

        if (isalpha(ch)) {
            char base = isupper(ch) ? 'A' : 'a';
            int k = toupper(key[j % keyLength]) - 'A';

            result[i] = ((ch - base - k + 26) % 26) + base;
            j++;
        } else {
            result[i] = ch;
        }
    }

    result[i] = '\0';
}

// Main function
int main() {
    char message[1000], key[100];
    char encrypted[1000], decrypted[1000];
    int i;

    // Input message
    printf("Enter your secret message: ");
    fgets(message, sizeof(message), stdin);

    // Remove newline character
    message[strcspn(message, "\n")] = '\0';

    // Input key
    printf("Enter the key: ");
    scanf("%s", key);

    // Check if key is empty
    if (strlen(key) == 0) {
        printf("Error: Key cannot be empty.\n");
        return 0;
    }

    // Check if key contains only alphabets
    for (i = 0; key[i] != '\0'; i++) {
        if (!isalpha(key[i])) {
            printf("Error: Key must contain only alphabets.\n");
            return 0;
        }
    }

    // Encrypt the message
    vigenere_encrypt(message, key, encrypted);
    printf("Encrypted Message: %s\n", encrypted);

    // Decrypt the message
    vigenere_decrypt(encrypted, key, decrypted);
    printf("Decrypted Message: %s\n", decrypted);

    return 0;
}
```
## OUTPUT
<img width="1696" height="781" alt="image" src="https://github.com/user-attachments/assets/000ae683-31b2-4972-ae87-f51876d67ee8" />


## RESULT
The code executed successsfully.
