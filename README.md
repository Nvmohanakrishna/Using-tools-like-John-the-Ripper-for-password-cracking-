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

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
<img width="1450" height="953" alt="Screenshot 2025-10-04 101130" src="https://github.com/user-attachments/assets/c899527f-7348-4647-b0ce-0ab273eb1503" />
<img width="914" height="742" alt="Screenshot 2025-10-04 101245" src="https://github.com/user-attachments/assets/cf3e1a1d-ff0a-4aa5-9631-f3ba32b6c5bb" />
<img width="1616" height="1199" alt="Screenshot 2025-10-04 101807" src="https://github.com/user-attachments/assets/c205623d-2e13-4447-8ba3-318689203a3a" />
<img width="951" height="1199" alt="Screenshot 2025-10-04 102255" src="https://github.com/user-attachments/assets/485e0132-0107-4418-a27c-d7c1194ad0ca" />
<img width="1911" height="539" alt="Screenshot 2025-10-04 105752" src="https://github.com/user-attachments/assets/39022c02-9740-4d80-a7ed-00a7ad6c2952" />
<img width="949" height="800" alt="Screenshot 2025-10-04 104453" src="https://github.com/user-attachments/assets/b763549e-b25c-4090-9197-1868539422c7" />
<img width="725" height="643" alt="Screenshot 2025-10-04 104829" src="https://github.com/user-attachments/assets/8164cefc-4236-4c83-8340-00a6f097108a" />
<img width="793" height="222" alt="image" src="https://github.com/user-attachments/assets/f8cd94cf-9107-4dcd-8fe8-c939eaad68d4" />




Cracked Passwords from Hash File

## RESULT:
The password hashes were successfully cracked using John the Ripper.

