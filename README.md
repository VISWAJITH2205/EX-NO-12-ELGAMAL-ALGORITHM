# NAME : VISWAJITH LALITHRAM R.V

# REG.NO : 212224240187

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

int modexp(int base, int exp, int mod) {
    int res = 1;
    base %= mod;
    while (exp > 0) {
        if (exp & 1) res = (res * base) % mod;
        base = (base * base) % mod;
        exp >>= 1;
    }
    return res;
}

int main() {
    int p, g, x, k, M, y, C1, C2, dec;
    
    printf("Enter a prime number p: ");
    scanf("%d", &p);
    printf("Enter a primitive root g of p: ");
    scanf("%d", &g);
    printf("Enter the private key x: ");
    scanf("%d", &x);
    
    y = modexp(g, x, p);
    printf("Public key y: %d\n", y);
    
    printf("Enter the message (integer) to encrypt: ");
    scanf("%d", &M);
    printf("Enter a random integer k: ");
    scanf("%d", &k);
    
    C1 = modexp(g, k, p);
    C2 = (M * modexp(y, k, p)) % p;
    printf("Encrypted message: (C1, C2) = (%d, %d)\n", C1, C2);
    
    dec = (C2 * modexp(C1, p - 1 - x, p)) % p;
    printf("Decrypted message: %d\n", dec);
    
    printf("\n=== Code Execution Successful ===\n");
    return 0;
}



```

## Output:


<img width="1260" height="756" alt="image" src="https://github.com/user-attachments/assets/d6590988-99b5-4de6-90f9-09409b5864bf" />





## Result:
The program is executed successfully.
