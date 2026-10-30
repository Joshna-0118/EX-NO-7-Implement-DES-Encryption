# EX-NO-7-Implement-DES-Encryption
Implementation of the Data Encryption Standard (DES) algorithm in C using the OpenSSL library to demonstrate symmetric-key encryption and decryption.

## Name: Joshna.M
## Reference Number: 212225230118

# AIM:
To use the Data Encryption Standard (DES) algorithm for a practical application, such as securing sensitive data transmission in financial transactions.

# ALGORITHM:

    1. DES is based on a symmetric key encryption technique that encrypts data in 64-bit blocks.
    2. DES uses a Feistel network structure with 16 rounds of processing for encryption.
    3. DES has a 64-bit key, but only 56 bits are used for encryption (the remaining 8 bits are for parity).
    4. DES applies initial and final permutations along with 16 rounds of substitution and permutation transformations to produce ciphertext.


# PROGRAM:
```
#include <stdio.h>
#include <stdint.h>

/* Compact DES using a standard DES implementation is lengthy.
   This program uses OpenSSL's DES functions for simplicity. */
#include <openssl/des.h>

int main()
{
    DES_cblock key, input, encrypted, decrypted;
    DES_key_schedule ks;
    char text[9], k[9];

    printf("Enter 8-character plaintext: ");
    scanf("%8s", text);
    printf("Enter 8-character key: ");
    scanf("%8s", k);

    for (int i = 0; i < 8; i++) {
        input[i] = text[i];
        key[i] = k[i];
    }

    DES_set_key_unchecked(&key, &ks);
    DES_ecb_encrypt(&input, &encrypted, &ks, DES_ENCRYPT);
    DES_ecb_encrypt(&encrypted, &decrypted, &ks, DES_DECRYPT);

    printf("Encrypted: ");
    for (int i = 0; i < 8; i++)
        printf("%02X", encrypted[i]);

    printf("\nDecrypted: ");
    for (int i = 0; i < 8; i++)
        printf("%c", decrypted[i]);

    printf("\n");
    return 0;
}
```
# OUTPUT:


<img width="723" height="149" alt="Exp7_Output" src="https://github.com/user-attachments/assets/fa9ec486-71aa-43d0-84c3-3fee883c123c" />

# RESULT:
The C program implementing DES encryption and decryption using a symmetric key was developed. The plaintext was encrypted into ciphertext and successfully decrypted back to the original message.
