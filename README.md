# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```
<img width="907" height="450" alt="Screenshot 2025-10-04 112155" src="https://github.com/user-attachments/assets/4ed65d6d-91d8-4eb3-b82e-309d49311532" />



### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:

  <img width="900" height="570" alt="Screenshot 2025-10-04 112217" src="https://github.com/user-attachments/assets/255c321c-22b1-46f6-9eb3-7d6df79b4a95" />

```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
<img width="884" height="390" alt="Screenshot 2025-10-04 112234" src="https://github.com/user-attachments/assets/c42fdc65-c68b-4d38-ad21-c5e8c51f53c1" />

  
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
<img width="742" height="571" alt="Screenshot 2025-10-04 112340" src="https://github.com/user-attachments/assets/18abf7f5-5599-492b-8600-19098ed37441" />

   
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
<img width="966" height="619" alt="Screenshot 2025-10-04 112357" src="https://github.com/user-attachments/assets/ad1b22c3-6e78-45ef-9ef8-5b0d676322d0" />


4. **Password Recovery** – Successfully cracked passwords are displayed.

   <img width="735" height="590" alt="Screenshot 2025-10-04 112415" src="https://github.com/user-attachments/assets/527f5178-522c-4f39-8cd9-154ebde13a33" />


## OUTPUT:
Cracked Passwords from Hash File

## RESULT:
The password hashes were successfully cracked using John the Ripper.

