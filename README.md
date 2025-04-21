# VIGENERE-CIPHER
## EX. NO: 1(D)
 

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
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Function to generate the Vigenère Cipher encryption
void vigenereEncrypt(char* text, char* key) {
    int textLength = strlen(text);
    int keyLength = strlen(key);
    char encryptedText[textLength + 1]; // For the encrypted text

    for (int i = 0, j = 0; i < textLength; i++) {
        // Only encrypt alphabetic characters, leave others as is
        if (isalpha(text[i])) {
            char currentKeyChar = toupper(key[j % keyLength]); // Get the key character
            char currentTextChar = toupper(text[i]); // Encrypt upper case letter
            int keyIndex = currentKeyChar - 'A'; // Calculate the key's index (0-25)
            int textIndex = currentTextChar - 'A'; // Calculate the text's index (0-25)

            // Vigenère cipher encryption formula
            encryptedText[i] = (textIndex + keyIndex) % 26 + 'A';

            // Move to the next character of the key
            j++;
        } else {
            encryptedText[i] = text[i]; // Non-alphabet characters remain the same
        }
    }
    encryptedText[textLength] = '\0'; // Null-terminate the encrypted string
    printf("Encrypted Text: %s\n", encryptedText);
}

// Function to decrypt the Vigenère Cipher
void vigenereDecrypt(char* cipherText, char* key) {
    int textLength = strlen(cipherText);
    int keyLength = strlen(key);
    char decryptedText[textLength + 1]; // For the decrypted text

    for (int i = 0, j = 0; i < textLength; i++) {
        // Only decrypt alphabetic characters, leave others as is
        if (isalpha(cipherText[i])) {
            char currentKeyChar = toupper(key[j % keyLength]); // Get the key character
            char currentCipherChar = toupper(cipherText[i]); // Decrypt upper case letter
            int keyIndex = currentKeyChar - 'A'; // Calculate the key's index (0-25)
            int cipherIndex = currentCipherChar - 'A'; // Calculate the cipher text's index (0-25)

            // Vigenère cipher decryption formula
            decryptedText[i] = (cipherIndex - keyIndex + 26) % 26 + 'A';

            // Move to the next character of the key
            j++;
        } else {
            decryptedText[i] = cipherText[i]; // Non-alphabet characters remain the same
        }
    }
    decryptedText[textLength] = '\0'; // Null-terminate the decrypted string
    printf("Decrypted Text: %s\n", decryptedText);
}

int main() {
    char text[100];
    char key[100];

    // Input the plaintext and the key
    printf("Enter the plaintext: ");
    fgets(text, sizeof(text), stdin);
    text[strcspn(text, "\n")] = '\0'; // Remove newline character

    printf("Enter the key: ");
    fgets(key, sizeof(key), stdin);
    key[strcspn(key, "\n")] = '\0'; // Remove newline character

    // Encrypt the plaintext
    vigenereEncrypt(text, key);

    // Input the ciphertext to decrypt
    char cipherText[100];
    printf("Enter the ciphertext to decrypt: ");
    fgets(cipherText, sizeof(cipherText), stdin);
    cipherText[strcspn(cipherText, "\n")] = '\0'; // Remove newline character

    // Decrypt the ciphertext
    vigenereDecrypt(cipherText, key);

    return 0;
}


## OUTPUT

![Screenshot 2025-04-21 170239](https://github.com/user-attachments/assets/9795d4f0-93b5-48e8-acb0-843ee034066f)

## RESULT

 implemented the Vigenere Cipher substitution technique using C program.
