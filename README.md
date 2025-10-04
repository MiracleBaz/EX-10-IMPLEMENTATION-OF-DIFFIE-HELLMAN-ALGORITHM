## EX 10 : IMPLEMENTATION OF DIFFIE HELLMAN ALGORITHM

## AIM :
To implement key exchange between users using Diffie Hellman algorithm.

## ALGORITHM :
1.	Select a large prime number P and a primitive root G of P (publicly known).
2.	Alice selects a private key a and computes her public key x = (G^a) mod P.
3.	Bob selects a private key b and computes his public key y = (G^b) mod P.
4.	Alice and Bob exchange their public keys (x and y).
5.	Alice computes the secret key as ka = (y^a) mod P.
6.	Bob computes the secret key as kb = (x^b) mod P.
7.	Both ka and kb will be the same, forming a shared secret key for secure communication.


## PROGRAM :
```
#include <stdio.h>

long long int power(long long int a, long long int b, long long int P) {
    long long int result = 1;
    a = a % P;
    while (b > 0) {
        if (b % 2 == 1)
            result = (result * a) % P;
        b = b / 2;
        a = (a * a) % P;
    }
    return result;
}

int main() {
    long long int P, G, x, a, y, b, ka, kb;

    printf("\n***** Diffie-Hellman Key Exchange algorithm *****\n\n");

    printf("Enter the value of P: ");
    scanf("%lld", &P);
    printf("The value of P: %lld\n", P);

    printf("Enter the value of G (Primitive root of P): ");
    scanf("%lld", &G);
    printf("The value of G: %lld\n\n", G);

    a = 4;
    printf("The private key a for Alice: %lld\n", a);
    x = power(G, a, P);

    b = 3;
    printf("The private key b for Bob: %lld\n\n", b);
    y = power(G, b, P);

    ka = power(y, a, P);
    kb = power(x, b, P);

    printf("Secret key for Alice: %lld\n", ka);
    printf("Secret key for Bob: %lld\n", kb);

    return 0;
}
```


## OUTPUT:

<img width="822" height="547" alt="Screenshot 2025-10-04 150305" src="https://github.com/user-attachments/assets/91f61cce-eeaa-4152-a490-bb7de12de99b" />


## RESULT :
The Diffie-Hellman key exchange algorithm has been successfully simulated, with correct execution	of	the	program	and	verification	of	the	results.
