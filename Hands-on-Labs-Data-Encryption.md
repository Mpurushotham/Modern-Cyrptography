

# 🔬 Hands-On Labs: AES, RSA, and SHA-256 with Python & CLI Tools

These labs will help you build practical cryptography skills using real-world tools. Here's a structured plan:

### 1. 🔐 AES Encryption Lab (Symmetric)
**Goal:** Encrypt and decrypt a file using AES-256

**Tools:** Python (`pycryptodome`), OpenSSL CLI

**Steps:**
- Generate a 256-bit key
- Encrypt a text file using AES in CBC mode
- Decrypt and verify the output
- Bonus: Use OpenSSL CLI for the same task

```bash
# Encrypt with OpenSSL
openssl enc -aes-256-cbc -salt -in plaintext.txt -out encrypted.txt -pass pass:yourpassword

# Decrypt
openssl enc -aes-256-cbc -d -in encrypted.txt -out decrypted.txt -pass pass:yourpassword
```

---

### 2. 🔑 RSA Encryption & Digital Signature Lab (Asymmetric)
**Goal:** Encrypt a message and sign it digitally

**Tools:** Python (`cryptography`), OpenSSL CLI

**Steps:**
- Generate RSA key pair (2048-bit)
- Encrypt a message with public key
- Decrypt with private key
- Sign a message and verify signature

```bash
# Generate keys
openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048
openssl rsa -pubout -in private.pem -out public.pem

# Encrypt
openssl rsautl -encrypt -inkey public.pem -pubin -in message.txt -out encrypted.bin

# Decrypt
openssl rsautl -decrypt -inkey private.pem -in encrypted.bin -out decrypted.txt
```

---

### 3. 🧮 SHA-256 Hashing Lab
**Goal:** Hash a password and verify integrity

**Tools:** Python (`hashlib`), CLI (`sha256sum`)

**Steps:**
- Hash a password with SHA-256
- Store and compare hashes
- Simulate integrity check for a file

```bash
# Hash a file
sha256sum file.txt

# Python hash
import hashlib
hash = hashlib.sha256(b"yourpassword").hexdigest()
print(hash)
```

---

## 🛠️ DevSecOps Workflow Diagram: GitHub + Azure DevOps

Here’s a detailed flow you can visualize or document:

### 🔄 Full Pipeline Stages

| Stage | Tool | Security Integration |
|-------|------|----------------------|
| **Code Commit** | GitHub | Secret scanning (GitHub Advanced Security) |
| **CI/CD Build** | Azure DevOps Pipelines | Code signing, SBOM generation |
| **Infrastructure Provisioning** | Terraform + Azure | Secrets encryption via Azure Key Vault |
| **Containerization** | Docker | Image signing with Notary or Cosign |
| **Deployment** | Azure Kubernetes Service | TLS, JWT, RBAC |
| **Monitoring & Logging** | Azure Monitor + Log Analytics | Secure audit trails, anomaly detection |

### 🔐 Security Touchpoints
- Pre-commit hooks for secret detection
- Static code analysis (SonarQube, Semgrep)
- Secrets rotation via Azure Key Vault
- Runtime scanning with Defender for Cloud
- Secure logging with centralized dashboards

---

<img width="1536" height="1024" alt="Copilot_20251104_123651" src="https://github.com/user-attachments/assets/6772fbb3-1cdc-488c-8db3-00e40136ef4e" />


