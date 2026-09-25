# Password-Cracking-Cryptographic-Hash-Extraction
# Cryptographic Hash Extraction & Document Password Cracking

## Executive Summary
This repository documents a practical cybersecurity lab demonstrating how encrypted file headers can be audited to assess password strength. Using web-based cryptographic tools, the project covers extracting raw hash signatures (`$pdf$`) from password-protected PDF files and running dictionary attacks to recover plain-text credentials.

---

## Technical Context
Document encryption (PDF, ZIP, MS Office) relies on password-derived hashes rather than storing passwords directly in plain text. Recovering access involves a two-stage process:

1. **Hash Extraction:** Isolating the cryptographic hash signature stored within the file's metadata structure (formatted for tools like John the Ripper or Hashcat).
2. **Dictionary Attack Execution:** Passing wordlist entries through the target hashing algorithm in real time until a matching hash output is generated.

---

## Lab Architecture & Workflow

### Environment & Tools
* **Target File:** `My Locked PDF1.pdf`
* **Extraction Utility:** Networkwalks Hash Calculator
* **Cracking Engine:** Networkwalks Password Cracker (Dictionary Attack Mode)
* **Execution Environment:** Web Browser (Linux / Windows)

---

### Step-by-Step Procedure

#### Phase 1: Hash Extraction
* Uploaded `My Locked PDF1.pdf` to the Hash Calculator interface.
* Parsed the encrypted metadata to generate the standard `$pdf$` hash string.

<https://github.com/advocals/Password-Cracking-Cryptographic-Hash-Extraction/blob/main/Screenshot%20(429).png>

#### Phase 2: Hash Cracking & Verification
* Copied the full extracted `$pdf$` hash into the Password Cracker engine.
* Launched a dictionary attack using a built-in wordlist to compute matching hashes.
* Successfully matched the hash to recover the cleartext key.

<https://github.com/advocals/Password-Cracking-Cryptographic-Hash-Extraction/blob/main/Screenshot%20(431).png>

---

## Findings & Technical Results

| Target Artifact | Extracted Hash Signature | Attack Strategy | Recovered Credential |
| :--- | :--- | :--- | :--- |
| `My Locked PDF1.pdf` | `$pdf$*4*2*128*...` | Dictionary Attack (Wordlist) | `password1` |

### Proof of Access
Entering `password1` successfully decrypted the target PDF and exposed the internal flag content.

<https://github.com/advocals/Password-Cracking-Cryptographic-Hash-Extraction/blob/main/Screenshot%20(433).png>

---

## Key Security Takeaways
* **Password Entropy:** Common words combined with predictable numbers (like `password1`) are vulnerable to automated wordlist sweeps within seconds.
* **Length vs. Complexity:** Moving from a simple 8-character password to a 12+ character passphrase significantly increases the search space, rendering dictionary and brute-force attacks computationally infeasible.
* **Strong Encryption Standards:** Always ensure file encryption protocols utilize modern algorithms (e.g., AES-256) to resist rapid key derivation.
