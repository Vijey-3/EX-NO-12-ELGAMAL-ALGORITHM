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

long long modExp(long long base, long long exp, long long mod)
{
    long long result = 1;

    while(exp > 0)
    {
        if(exp % 2 == 1)
        {
            result = (result * base) % mod;
        }

        base = (base * base) % mod;
        exp = exp / 2;
    }

    return result;
}

int main()
{
    long long p, g;
    long long privateKeyVijey, publicKeyVijey;
    long long k, message;
    long long c1, c2;
    long long decryptedMessage;

    printf("Enter prime number (p): ");
    scanf("%lld", &p);

    printf("Enter generator (g): ");
    scanf("%lld", &g);

    printf("Enter Vijey's private key: ");
    scanf("%lld", &privateKeyVijey);

    publicKeyVijey = modExp(g, privateKeyVijey, p);

    printf("Vijey's Public Key = %lld\n", publicKeyVijey);

    printf("Enter message to encrypt: ");
    scanf("%lld", &message);

    printf("Enter random value k: ");
    scanf("%lld", &k);

    c1 = modExp(g, k, p);
    c2 = (message * modExp(publicKeyVijey, k, p)) % p;

    printf("\nEncrypted Cipher Text:\n");
    printf("C1 = %lld\n", c1);
    printf("C2 = %lld\n", c2);

    decryptedMessage =
        (c2 * modExp(c1, p - 1 - privateKeyVijey, p)) % p;

    printf("\nDecrypted Message = %lld\n", decryptedMessage);

    return 0;
}
```

## Output:
<img width="1919" height="918" alt="image" src="https://github.com/user-attachments/assets/89c0cf67-6240-4bab-bf81-bf0e1bace930" />


## Result:
The program is executed successfully.
