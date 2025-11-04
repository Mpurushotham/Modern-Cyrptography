It's all about the Modern Digital systems protecting using Cryptography methods and types. Let's do a deep dive 👇

---

# 👨‍💻 Cryptography: Principles, Evolution, Types, Implementations, and Strategic Importance in Modern Digital Systems 🔥
---

## Introduction

Cryptography stands at the core of modern digital security, ensuring data confidentiality, integrity, authentication, and non-repudiation across the connected world. As digital ecosystems have expanded, driven by e-commerce, cloud computing, remote work, and the Internet of Things, the critical need to shield sensitive data from growing cyber threats has intensified. This comprehensive report dissects the concept of cryptography from its historical origins to its present-day role in cybersecurity. It systematically explores the main cryptographic types—symmetric, asymmetric, and cryptographic hashing/salting—describes the most widely adopted algorithms and standards, details practical implementations including command-line tools and real-world examples, and analyzes cryptography’s foundational role in securing communications and compliance. Comparative tables, code examples, and authoritative references provide an exhaustive and practical perspective.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/52809126-3ab2-4123-8399-bcf122530de1" />

---


## 1. Definition and Core Principles of Cryptography

Cryptography, derived from the Greek words "kryptos" meaning hidden, and "graphein" meaning writing, is the science and art of protecting information by transforming it into an unreadable format, only reversible by authorized parties. It encompasses processes and algorithms that make data unintelligible to unauthorized entities while enabling its secure recovery by those possessing the necessary credentials, typically digital keys.

### 1.1. Fundamental Objectives (The CIA Triad)

Cryptography is engineered around four essential principles:

- **Confidentiality**: Ensures only authorized parties can access the information. Encryption transforms plaintext (readable data) into ciphertext (unreadable data), making unauthorized disclosure highly unlikely.
- **Integrity**: Prevents unauthorized modification, ensuring recipients can detect tampering during storage or transit, often by using cryptographic hashes or message authentication codes (MACs).
- **Availability**: Guarantees information and systems are accessible to legitimate users when required, protected against disruptions such as Denial-of-Service attacks.
- **Authentication**: Verifies the identities of communicating parties—the sender and receiver—thus confirming the source and destination of information, often realized with digital certificates or signatures.
- **Non-repudiation**: Ensures that senders cannot deny the authenticity of their transmitted data, providing irrefutable proof of origin, especially in legal or transactional scenarios.

Together, these four pillars serve as the methodological foundation of all modern cryptosystems.

### 1.2. Key Terms and Concepts

- **Plaintext**: The original, readable data.
- **Ciphertext**: The encrypted, unreadable data produced by an encryption algorithm operating on plaintext.
- **Key**: Secret (or public–private) parameters used in the encryption/decryption process.
- **Encryption**: Conversion of plaintext into ciphertext.
- **Decryption**: Conversion of ciphertext back into plaintext.
- **Cipher**: The algorithm used for encryption/decryption.
- **Key Exchange**: A secure process for sharing cryptographic keys between parties.

---

## 2. Historical Evolution of Cryptography

The evolution of cryptography mirrors the progression of human civilization's needs for secure communication, from ancient ciphers to post-quantum algorithms.

### 2.1 Ancient and Classical Cryptography

- **Egypt (ca. 1900 BC)**: Non-standard hieroglyphs used for sealing tomb messages.
- **Mesopotamia (ca. 1500 BC)**: Clay tablets enciphered to guard trade secrets.
- **Sparta (ca. 650 BC)**: The scytale (transposition cipher)—messages written on leather strips wound around staffs, decipherable only with the correct staff diameter (early symmetric key).
- **Rome (ca. 100–44 BC)**: Julius Caesar's substitution cipher (Caesar cipher)—shifting alphabet letters by a fixed number.

### 2.2. Middle Ages and Renaissance

- **Al-Kindi (800 AD)**: Frequency analysis for codebreaking—birth of cryptanalysis.
- **Alberti (1467)**: Polyalphabetic ciphers introducing stronger encryption methods, less vulnerable to frequency analysis.
- **Bellaso/Vigenère Ciphers (16th century)**: Polyalphabetic substitution ciphers introducing advanced cryptographic resilience.

### 2.3. Mechanical to Modern Digital Cryptography

- **Hebern Rotor Machine (1917)**: First electro-mechanical machine cipher.
- **Enigma Machine (1918–1945)**: Used by Nazi Germany, broken by Allied cryptanalysts during WWII—ushering in the era of machine/algorithmic cryptography and contributing to the foundations of modern computing and cryptanalysis (e.g., Alan Turing).

### 2.4. Advances in the Digital Era

- **Data Encryption Standard (DES, 1975)**: The first NIST-certified cryptosystem; later found insecure as computing power increased.
- **Diffie-Hellman Key Exchange (1976)**: Enabled secure sharing of cryptographic keys across insecure channels (pioneering asymmetric cryptography).
- **RSA Algorithm (1977)**: The first practical public-key encryption, secure due to mathematical difficulty of prime factorization.
- **Advanced Encryption Standard (AES, 2001)**: Replaced DES, became the gold standard for symmetric encryption.

### 2.5. The Quantum and Post-Quantum Eras

- **Quantum Cryptography**: Uses quantum principles (e.g., QKD) to achieve theoretically "unhackable" security.
- **Post-Quantum Cryptography (2024)**: Driven by the need to resist quantum attacks, NIST released the first three standardized quantum-resistant encryption algorithms (e.g., lattice-based NTRUEncrypt, Kyber, Dilithium).

---

## 3. Main Types of Cryptography: Concepts, Algorithms, and Use Cases

Modern cryptography is categorized primarily into symmetric, asymmetric, and hash-based (including salting) methods. Each type has distinct mathematical foundations, practical uses, strengths, and weaknesses.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b72a94c3-65ce-48e3-851a-8113c0e76064" />
---

### 3.1. Symmetric Cryptography

#### 3.1.1. Concept

Symmetric key cryptography (also called "secret-key" or "private-key" encryption) uses the same secret key for both encryption and decryption. Protection of the secret key's confidentiality is paramount—the entire system's security hinges on it.

#### 3.1.2. Strengths and Weaknesses

- **Strengths**:
    - Very fast and efficient for large data volumes.
    - Simple to implement.
    - Ideal for data-at-rest, bulk encryption, VPNs, and secure communications with pre-shared keys.

- **Weaknesses**:
    - Key distribution: Safe delivery and exchange of the secret key are challenging.
    - Scalability: With n users, n(n-1)/2 keys are needed for every possible private channel.
    - No built-in authentication or non-repudiation.

#### 3.1.3. Cipher Types

Symmetric algorithms are divided into:
- **Block Ciphers**: Encrypt fixed-size blocks (e.g., 128 bits). Examples: AES, DES, 3DES, Blowfish.
- **Stream Ciphers**: Encrypt data byte-by-byte/bit-by-bit. Examples: RC4, Salsa20, ChaCha20.

#### 3.1.4. Common Symmetric Algorithms

**Table 1: Key Symmetric Encryption Algorithms**

| Algorithm | Key Length | Block Size   | Strengths        | Weaknesses         | Typical Use Cases                  |
|-----------|------------|--------------|------------------|--------------------|-------------------------------------|
| DES       | 56 bits    | 64 bits      | Historical value | Insecure, weak     | Obsolete, legacy systems            |
| 3DES      | 112/168    | 64 bits      | Stronger than DES| Slower than AES    | Legacy payment systems              |
| AES       | 128/192/256| 128 bits     | Secure, fast     | None significant   | VPNs, disk/full-disk encryption, TLS|
| Blowfish  | 32–448     | 64 bits      | Fast, flexible   | 64-bit block size  | File encryption, VPNs               |
| Twofish   | 128–256    | 128 bits     | Open, fast       | Not standardized   | Open applications                   |
| ChaCha20  | 256 bits   | Stream cipher| Fast, secure     | Less hardware-optimized | Messaging, mobile computing    |

**Algorithm Notes:**

- *AES* (Advanced Encryption Standard) is globally standardized (FIPS 197), used by governments, corporations, and virtually every modern secure application.
- *3DES* applies DES three times, but is now deprecated due to speed and block size limitations.
- *Blowfish* and *Twofish* provide open, strong alternatives for special applications.
- *ChaCha20* is favored for efficiency on systems without hardware-accelerated AES and in mobile protocols (e.g., Google, WhatsApp).

#### 3.1.5. Modes of Operation

Block ciphers can be used in various modes (e.g., ECB, CBC, CFB, OFB, CTR, GCM), impacting security properties and error propagation.

- **ECB** (Electronic Codebook): Simple, but leaks patterns—highly discouraged.
- **CBC** (Cipher Block Chaining): Default for many applications, but vulnerable to certain attacks if not properly configured.
- **GCM/CCM**: Provide authenticated encryption (confidentiality & integrity).

#### 3.1.6. Key Management in Practice

Symmetric cryptography relies on secure generation, storage, distribution, and rotation of keys. Poor key management, randomness, or entropy can expose encrypted data to trivial attacks.

---

### 3.2. Asymmetric Cryptography

#### 3.2.1. Concept

Asymmetric (public-key) cryptography uses two mathematically linked keys: a public key (widely distributed) and a private key (kept secret). Data encrypted with the public key can only be decrypted with the private key, and vice versa. Asymmetric methods solve key distribution problems inherent in symmetric schemes.

#### 3.2.2. Strengths and Weaknesses

**Strengths:**
- Solves secure key exchange problem.
- Provides authentication, integrity, and non-repudiation (digital signatures).
- Designed for secure communications over open, untrusted channels (e.g., Internet).

**Weaknesses:**
- Slower and more computationally intensive than symmetric algorithms (not optimal for bulk data).
- Vulnerable to advances in mathematical or quantum computing attacks if not using sufficient key lengths.

#### 3.2.3. Key Algorithms and Standards

**Table 2: Key Asymmetric Encryption Algorithms**

| Algorithm   | Key Length         | Security Base             | Main Use Cases                   |
|-------------|-------------------|---------------------------|----------------------------------|
| RSA         | 1024–4096 bits    | Integer factorization     | Encryption, digital signatures, PKI, TLS |
| DSA         | 1024–3072 bits    | Discrete log problem      | Digital signatures               |
| ECC (ECDSA) | 160–521 bits      | Elliptic curve log prob.  | Mobile, IoT, digital signatures  |
| DH / ECDH   | Varied            | Key exchange              | Secure session key negotiation   |
| ElGamal     | 2048+ bits        | Discrete log problem      | Less common, experimental        |
| Post-quantum| NTRU, Kyber, etc. | Lattices, code theory     | Future-proof encryption and signatures |

**Algorithm Notes:**

- **RSA**: The most widely implemented asymmetric algorithm for both encryption and signing. Key lengths ≥2048 bits recommended.
- **ECC** (Elliptic Curve Cryptography): Mathematically different, achieves strong security with much shorter keys—essential for resource-constrained environments and modern protocols (TLS 1.3, mobile communications).
- **Diffie-Hellman (DH/ECDH)**: Used for secure key agreement, not for data encryption directly.
- **Post-quantum algorithms**: Undergoing rapid standardization to resist quantum computer attacks.

#### 3.2.4. Public Key Infrastructure (PKI)

PKI systems provide the infrastructure for issuing, verifying, and revoking digital certificates (e.g., TLS/SSL certificates used in HTTPS), anchored by trusted Certificate Authorities (CAs).

---

### 3.3. Hash Functions and Salting

#### 3.3.1. Hash Functions

**Concept**: A cryptographic hash function deterministically transforms arbitrary-length input into a fixed-length output (the "hash" or "digest"), such that:
- It is computationally infeasible to recover the input from the hash (pre-image resistance).
- It is infeasible to find two distinct inputs with the same hash (collision resistance).
- Every change in input results in a completely different hash (the avalanche effect).

Hash functions do **not** encrypt data—hashing is a one-way process with no decryption. Their primary role is to ensure data integrity (tamper detection), password management, digital signatures, and blockchain systems.

**Common Hashing Algorithms**:

| Algorithm  | Output Size   | Properties      | Status/Uses                                 |
|------------|--------------|-----------------|---------------------------------------------|
| MD5        | 128 bits     | Fast, weak      | Broken, legacy only                         |
| SHA-1      | 160 bits     | Older standard  | Weak, collisions known                      |
| SHA-2      | 224–512 bits | Secure          | Modern default (SHA-256, SHA-512, etc.)     |
| SHA-3      | 224–512 bits | Secure, new     | Keccak standard, higher security needs      |
| BLAKE2/BLAKE3| Variable   | Fast, secure    | Emerging in high-performance applications   |
| PBKDF2, Argon2, scrypt | Variable | Key derivation | Password storage, KDFs                      |

**Best Practice**: Use only SHA-2, SHA-3, BLAKE2, or Argon2 for new designs.

#### 3.3.2. Salting and Password Hashing

"Salting" involves adding random, unique data ("salt") to the input of a hash function before hashing passwords. This defends against attacks like rainbow tables (precomputed hash lookups) and ensures that identical passwords across users produce unique hashes.

Key recommendations:
- Use strong, slow KDFs (PBKDF2, bcrypt, scrypt, Argon2).
- Use unique, high-entropy random salts per password.
- Set iteration/work factors high enough to make brute-forcing impractical by modern hardware.

---

### 3.4. Comparative Table: Symmetric vs. Asymmetric vs. Hashing

| Feature                    | Symmetric           | Asymmetric         | Hash Function                 |
|----------------------------|---------------------|--------------------|-------------------------------|
| Keys Used                  | Single shared       | Public/private pair| None                          |
| Speed                      | Fast                | Slow               | Very fast (usually)           |
| Key Distribution           | Problematic         | Solved             | N/A                           |
| Scalability                | Poor at scale       | Excellent          | N/A                           |
| Typical Use Cases          | Bulk data, disk, VPN| Secure key exchange, signatures | Data integrity, password storage, signatures |
| Authentication             | Not intrinsic       | Yes                | Not intrinsic                  |
| Non-repudiation            | No                  | Yes                | Not intrinsic                  |
| Data Integrity Checking    | MAC (HMAC) add-on   | Digital signatures | Built-in                      |
| Example Algorithms         | AES, 3DES, Blowfish | RSA, ECC, DSA, DH  | SHA-2, SHA-3, BLAKE2, Argon2   |

---

## 4. Implementation in Practice: Algorithms, Tools, Commands, and Real-World Usage

### 4.1. Common Algorithms: Modern Standards

**Symmetric:** AES (FIPS 197 standard), Block ciphers (GCM/CTR/CBC modes)

**Asymmetric:** RSA (PKCS #1, FIPS 186), ECC (NIST P-256, Curve25519), DSA, ECDSA

**Hash:** SHA-256/512/3 (NIST FIPS 180/202), BLAKE2/3, HMAC(KDFs)

**Key Derivation:** PBKDF2 (RFC 2898), bcrypt, scrypt, Argon2

Reference standards: FIPS 197 (AES), FIPS 186 (DSS/ECDSA/DSA), FIPS 180/202 (SHA-2, SHA-3), FIPS 140-3 (Cryptographic module validation).

### 4.2. Real-World Cryptography Tools & Libraries

**Software tools and libraries supporting these standards:**

| Library/Tool     | Language/Usage  | Cryptographic Support (Sym/Asym/Hash) | FIPS 140 Certification | Notes              |
|------------------|----------------|---------------------|----------------------|----------------------|
| OpenSSL          | C (CLI, lib)   | All                 | Yes (3.x)            | Ubiquitous, standard |
| WolfCrypt/wolfSSL| C              | All                 | Yes                  | Embedded/IoT use     |
| Bouncy Castle    | Java, C#       | All                 | Yes                  | Cross-platform, extensive  |
| Crypto++         | C++            | All                 | No                   | Open source, broad  |
| GnuTLS           | C              | All                 | In process           | Open source, Linux  |
| Microsoft CAPI   | Windows        | All                 | Yes                  |                   |

*OpenSSL* is the most widely used, supporting symmetric, asymmetric, hash functions, digital certificates, and protocols including SSL/TLS.

---

### 4.3. Command-Line Tools and Code Examples

Here are practical examples demonstrating typical cryptographic operations for each major type:

#### 4.3.1. Symmetric Encryption with OpenSSL

**Encrypt a file with AES-256-CBC:**

```sh
openssl enc -aes-256-cbc -salt -in plaintext.txt -out encrypted.enc -k 'SecretPassword'
```

**Decrypt:**

```sh
openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt -k 'SecretPassword'
```
- `-salt` ensures a unique salt is used each time.
- `-k` provides the password to derive an AES key, but for best security use `-K` and `-iv` with randomly generated keys.

**Options:** See also `-aes-128-cbc`, `-aes-192-cbc`, `-aes-256-gcm` for variations.

#### 4.3.2. Asymmetric Key Generation and Use

**Generate RSA key pair:**

```sh
openssl genrsa -out private.pem 2048
openssl rsa -in private.pem -pubout > public.pem
```

**Encrypt with public key:**

```sh
openssl rsautl -encrypt -inkey public.pem -pubin -in secret.txt -out secret.enc
```

**Decrypt with private key:**

```sh
openssl rsautl -decrypt -inkey private.pem -in secret.enc > secret_decrypted.txt
```


#### 4.3.3. Hashing and Salting

**Create SHA-256 digest of a file:**

```sh
openssl dgst -sha256 file.txt
```
Output: `SHA256(file.txt)= <hash>`

**PBKDF2 password hashing (with salt):**

```sh
openssl enc -pbkdf2 -k password -S deadbeef -iter 100000 -md sha256
```
Argon2, bcrypt, scrypt, and higher-level libraries/toolkits provide modern key stretching.

**Verify file integrity:**
- Sender sends both the file and its hash digest. Receiver hashes the received file—if it matches, data integrity is intact.

#### 4.3.4. Digital Signatures (RSA Example)

**Sign a file:**

```sh
openssl dgst -sha256 -sign private.pem -out file.sign file.txt
```

**Verify:**

```sh
openssl dgst -sha256 -verify public.pem -signature file.sign file.txt
```


#### 4.3.5. Real-World Protocols

Protocols like TLS/SSL (HTTPS), VPNs, secure email, SSH, file encryption tools (VeraCrypt, BitLocker, FileVault), and secure messaging (Signal/WhatsApp) are built on these foundational cryptographic primitives.

---

## 5. Importance in Cybersecurity, Data Protection, and Compliance

Cryptography’s role in digital security goes far beyond theoretical value—it’s enforced by regulation, demanded by digital economies, and essential to digital trust.

### 5.1. Cybersecurity

- **Data protection**: Encryption renders stolen data unintelligible; even if breached, attackers cannot leverage the data without keys.
- **Secure communications**: End-to-end encryption in TLS secures websites (HTTPS), email, messaging apps, and VPNs.
- **Authentication and identity**: Digital certificates and signatures, used across web authentication and code signing.
- **Data integrity**: Hashing and digital signatures detect and prevent tampering.

### 5.2. Compliance and Data Protection Laws

- **GDPR (EU) & UK GDPR**: Strongly recommend encryption as a best practice for safeguarding personal data. Lost or stolen encrypted data may not be deemed a reportable breach if keys remain uncompromised.
- **PCI DSS (Payment Cards)**: Requires encrypted transmission and storage of cardholder data.
- **HIPAA (Healthcare, US)**: Mandates data encryption for patient health records.
- **Regulation and fines**: Strong cryptographic defenses can greatly mitigate legal and financial liabilities after an incident.

### 5.3. Strategic and Operational Risk Reduction

- Protects trade secrets, intellectual property, user privacy, and sensitive transactions.
- Enables business continuity by securing backups, cloud storage, and remote access solutions.
- Forms a core layer in security architectures ("defense in depth").

---

## 6. Cryptography in Secure Communications

**Transport Layer Security (TLS):** The gold standard for web security, using a hybrid system—RSA/ECC for key exchange/authentication and AES/ChaCha20 for data encryption. Key principles:
- **Confidentiality**: All traffic is unreadable to eavesdroppers.
- **Integrity**: HMAC and AEAD modes prevent undetected manipulation.
- **Authentication**: Digital certificates assure identity.
- **Forward secrecy**: ECDHE key exchange disables retrospective decryption if long-term keys are compromised.

---

### 6.1. Comparison Table: Cryptography Types, Algorithms, Use Cases

| Type                | Example Algorithms                | Applications/Use Cases                       | Notable Tools/Commands                  |
|---------------------|----------------------------------|----------------------------------------------|-----------------------------------------|
| Symmetric Encryption| AES, DES, 3DES, Blowfish, Twofish| Disk encryption, VPNs, bulk file security    | `openssl enc -aes-256-cbc`, VeraCrypt   |
| Asymmetric Encryption| RSA, ECC, Diffie-Hellman, DSA   | Key exchange, digital signatures, PKI, TLS   | `openssl genrsa`, `openssl rsautl`      |
| Hash Functions      | SHA-2, SHA-3, BLAKE2/3, Argon2   | Integrity, password hashing, blockchain      | `openssl dgst`, Argon2, bcrypt, scrypt  |
| Salting/KDFs        | PBKDF2, bcrypt, scrypt, Argon2   | Password storage, key derivation             | Libraries: libsodium, OpenSSL           |
| Message Auth Codes  | HMAC-SHA256, HMAC-SHA3           | API auth, data integrity, session tokens     | `openssl dgst -hmac`                    |

---

## 7. Cryptography Standards and Authoritative References

- **NIST (US):**
  - FIPS 140-3: Security requirements for cryptographic modules
  - FIPS 197: Advanced Encryption Standard (AES)
  - FIPS 186: Digital Signature Standards (DSS, ECDSA, DSA)
  - FIPS 180/202: Secure Hash Standards (SHA-2, SHA-3)
- **ISO/IEC 27001**: Information security management (encryption referenced for compliance).
- **RFCs**: IETF standards for TLS, PKCS (key standards), etc.
- **OWASP**: Guidelines for password storage, use of strong hashes/salts.
- **Major libraries**: OpenSSL, Bouncy Castle, GnuTLS, wolfSSL.

---

## 8. Future Trends and Quantum Threats

- **Quantum computing**: Algorithms like RSA and ECC, which rely on integer factorization/discrete log problems, will eventually be vulnerable to quantum attacks (e.g., Shor’s algorithm). Efforts are underway to transition to post-quantum cryptography, with new lattice-based, hash-based, and code-based cryptographic schemes on the horizon.
- **Crypto-agility**: Organizations must ensure systems are agile enough to swap cryptographic algorithms proactively as standards change.
- **Homomorphic encryption**: Enables computations on encrypted data without decryption; promises privacy in cloud computing.
- **Zero-knowledge proofs, blockchain, and more**: Innovations in privacy-preserving transactions and decentralized security.

---

## 9. Summary and Recommendations

**Cryptography** is foundational to every secure digital system. As threats evolve, cryptographic practices and standards must continually improve:

1. **Adopt modern algorithms** (AES-256, SHA-2/3, ECC, Argon2).
2. **Implement strict key management** (generation, storage, rotation, destruction).
3. **Leverage robust, validated libraries** and cryptographic modules (FIPS-certified whenever possible).
4. **Comply with legal, regulatory, and industry standards** for encryption—essential for GDPR, HIPAA, PCI DSS, and more.
5. **Regularly audit and update** cryptographic systems against emerging threats (especially quantum).
6. **Educate and train staff** about the secure use of cryptography and password practices.
7. **Design with flexibility and crypto-agility** to anticipate algorithm transitions as attack models shift.

Cryptography will remain a constantly developing field—its effectiveness is directly tied to rigorous implementation, proactive management, and security-centric organizational culture.

---

## Appendix: Quick Reference—Implementation Commands

| Cryptographic Task            | OpenSSL Command Example(s)                                      |
|-------------------------------|-----------------------------------------------------------------|
| AES-256 file encryption       | `openssl enc -aes-256-cbc -salt -in in.txt -out out.enc -k pwd` |
| AES-256 file decryption       | `openssl enc -d -aes-256-cbc -in out.enc -out out.txt -k pwd`   |
| Generate 2048-bit RSA keypair | `openssl genrsa -out private.pem 2048`<br>`openssl rsa -in private.pem -pubout > public.pem` |
| RSA encryption                | `openssl rsautl -encrypt -inkey public.pem -pubin -in x.txt -out x.enc` |
| RSA decryption                | `openssl rsautl -decrypt -inkey private.pem -in x.enc -out x.txt` |
| SHA-256 file hashing          | `openssl dgst -sha256 file.txt`                                 |
| Digital signing (SHA-256)     | `openssl dgst -sha256 -sign private.pem -out msg.sign msg.txt`  |
| Digital signature verification| `openssl dgst -sha256 -verify public.pem -signature msg.sign msg.txt` |
| Password hashing (PBKDF2)     | `openssl enc -pbkdf2 -k password -S salt -iter 100000 -md sha256` |

---

[Hands-on-Labs-Data-Encryption.md](https://github.com/Mpurushotham/Modern-Cyrptography/blob/81839c6166cc0022b59ec3eda3f3d31b9d360784/Hands-on-Labs-Data-Encryption.md)

[ENFORCING PASSWORD COMPLEXITY POLICY-PAM-Linux.md](https://github.com/Mpurushotham/Modern-Cyrptography/blob/c729b43853c055fbdab6dceb08a645491a4c99c6/ENFORCING%20PASSWORD%20COMPLEXITY%20POLICY-PAM-Linux.md)



**For further reading and detailed algorithm tables, refer to standards and implementations from NIST, ISO/IEC, FIPS publications, OWASP, and security library documentation.**
