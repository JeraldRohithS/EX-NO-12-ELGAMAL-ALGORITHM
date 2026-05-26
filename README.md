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
# EX-NO-12 - ELGAMAL ALGORITHM
# AIM: To implement ElGamal Algorithm

# Function to find modular inverse
def mod_inverse(a, p):
    for i in range(1, p):
        if (a * i) % p == 1:
            return i
    return None

# Public values
p = int(input("Enter a prime number (p): "))
g = int(input("Enter primitive root (g): "))

# Receiver private key
x = int(input("Enter private key (x): "))

# Public key
y = pow(g, x, p)

print("\nPublic Key (p, g, y):", (p, g, y))
print("Private Key x:", x)

# Message
m = int(input("\nEnter message to encrypt: "))

# Random integer k
k = int(input("Enter random integer (k): "))

# Encryption
c1 = pow(g, k, p)
c2 = (m * pow(y, k, p)) % p

print("\nEncrypted message:")
print("Ciphertext (c1, c2):", (c1, c2))

# Decryption
s = pow(c1, x, p)
s_inv = mod_inverse(s, p)

decrypted = (c2 * s_inv) % p

print("\nDecrypted message:", decrypted)

```

## Output:

<img width="351" height="327" alt="image" src="https://github.com/user-attachments/assets/4c23e7c3-09f5-47f5-a2b9-0404f43082eb" />



## Result:
The program is executed successfully.
