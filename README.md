# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
#include <stdio.h>

int power(int base, int exp, int mod)
{
    int result = 1;

    while(exp > 0)
    {
        result = (result * base) % mod;
        exp--;
    }

    return result;
}

int main()
{
    int p, g;
    int x;
    int y;
    int m, k;
    int c1, c2;
    int decrypted;

    printf("Enter prime number (p): ");
    scanf("%d", &p);

    printf("Enter generator (g): ");
    scanf("%d", &g);

    printf("Enter private key (x): ");
    scanf("%d", &x);

    y = power(g, x, p);

    printf("Public Key = %d\n", y);

    printf("Enter message: ");
    scanf("%d", &m);

    printf("Enter random value (k): ");
    scanf("%d", &k);

    c1 = power(g, k, p);
    c2 = (m * power(y, k, p)) % p;

    printf("\nEncrypted Cipher Text:\n");
    printf("C1 = %d\n", c1);
    printf("C2 = %d\n", c2);

    decrypted = (c2 * power(c1, p - 1 - x, p)) % p;

    printf("\nDecrypted Message = %d\n", decrypted);

    return 0;
}
```

## Output:
<img width="1919" height="918" alt="image" src="https://github.com/user-attachments/assets/89c0cf67-6240-4bab-bf81-bf0e1bace930" />


## Result:
The program is executed successfully.
