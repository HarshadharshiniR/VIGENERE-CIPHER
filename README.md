# VIGENERE-CIPHER
## EX. NO: 4
### NAME   : HARSHADHARSHINI R
### Reg no : 212224230089

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


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
