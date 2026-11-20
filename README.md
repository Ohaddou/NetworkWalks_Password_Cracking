<div align="center">
  <h1>Password Cracking Lab</h1>
  <p><b>John the Ripper (JTR) & Networkwalks Online Tools</b></p>

  <img src="https://img.shields.io/badge/Batch-B084-1F3A5F" alt="Batch">
  <img src="https://img.shields.io/badge/OS-Kali%20%7C%20Windows-1F3A2F" alt="OS">
  <img src="https://img.shields.io/badge/Tools-John%20the%20Ripper%20%7C%20NW%20Tools%20%7C%20pdf2john-E67E22" alt="Tools">
  
</div>

## 📌 Project Overview

Password cracking is the process of recovering a password from stored data or a protected file. Security professionals use it to test password strength and demonstrate the risks of weak credentials.

In this project, I extracted the hash from a locked PDF file (`My Locked PDF3.pdf`) and recovered the password using three different methodologies:

1. **John the Ripper (GUI version - Johnny)**
2. **John the Ripper (CLI in Kali Linux)**
3. **Networkwalks Online Hash Calculator & Password Cracker**

**Target File:** `My Locked PDF3.pdf`
**Recovered Password:** `1qaz2wsx`
**Captured Flag:** `nw{networkwalks_flag_260821_1}`

---

## 🛠️ Step 1: Cracking using John the Ripper (GUI - Johnny)

For the first approach, I used the graphical interface "Johnny" to perform the password cracking.

### 1. Installation & Setup

- ![JTR Install](screenshots/John%20The%20Ripper/Requirements_zip.png)

  I downloaded and installed the Johnny GUI and configured the path to the John the Ripper executable.

- ![JTR Install](screenshots/John%20The%20Ripper/JTR_Install.png)
- ![JTR GUI](screenshots/John%20The%20Ripper/JTR_GUI.png)

Configuring the JTR by adding the john.exe path

- ![JTR Settings](screenshots/John%20The%20Ripper/JRT_Settings.png)

### 2. Hash Extraction

I loaded the locked PDF file into Johnny.

- ![Locked PDF](screenshots/John%20The%20Ripper/Locked_PDF.png)
  Using the built-in extractor, I extracted the hash and saved it to a file.
- ![PDF Hash Extract](screenshots/John%20The%20Ripper/PDF%20Hash%20Extract.png)
- ![Save The Hash](screenshots/John%20The%20Ripper/Save%20The%20Hash.png)

### 3. Configuring Settings & Cracking

I loaded the extracted hash file back into Johnny, selected the `rockyou.txt` wordlist,

Add to open password file to start- ![Open Password](screenshots/John%20The%20Ripper/Open%20PASSWORD.png)

Ran the attack. The tool successfully cracked the password.

- ![Password Cracked](screenshots/John%20The%20Ripper/Password%20Cracked.png)

### 4. Unlocking the PDF

Using the cracked password (`1qaz2wsx`), I opened the PDF and accessed the flag.

- ![Pwd Use](screenshots/John%20The%20Ripper/Pwd%20Use.png)

- ![PDF Content Access](screenshots/John%20The%20Ripper/PDF%20Content%20Access.png)

---

## 🐉 Step 2: Cracking using JTR Kali Tool (CLI)

For the second approach, I utilized the native command-line version of John the Ripper inside my Kali Linux terminal.

### 1. Extracting the Hash

I used the `pdf2john` script to extract the hash directly from the PDF and saved it as `pdf.hash`.

```bash
pdf2john "My Locked PDF3.pdf" > pdf.hash
```

### 2. Running the Attack

I executed John the Ripper using the `rockyou.txt` dictionary against the hash file. The terminal output showed the password was cracked instantly.

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt pdf.hash
```

- ![JTR Kali Tool Usage](screenshots/John%20The%20Ripper/JTR%20Kali%20Tool%20Usage.png)

### 3. Displaying the Result

I used the `--show` flag to display the recovered password.

```bash
john --show pdf.hash
```

**Output:** `My Locked PDF3.pdf:1qaz2wsx`

---

## 🌐 Step 3: Cracking using Networkwalks Online Tool

For the final approach, I used the web-based tools provided by Networkwalks Academy.

### 1. Hash Extraction

I uploaded the locked PDF file to the **Networkwalks Hash Calculator** (`networkwalks.com/hash-calculator/`). It successfully processed the file and generated the compatible hash.

- ![NW Hash Calculator](screenshots/NW%20Tool/NW%20Hash%20Calculator.png)

### 2. Running the Dictionary Attack

I copied the hash and pasted it into the **Networkwalks Password Cracker** (`networkwalks.com/password-cracker/`). I utilized the built-in dictionary list and initiated the cracking process.

- ![NW PWD Cracker](screenshots/NW%20Tool/NW%20PWD%20Cracker.png)
- ![NW Start Attack](screenshots/NW%20Tool/NW%20Start%20Attack.png)

### 3. Unlocking the PDF

The online tool successfully cracked the password, which I then used to unlock the file.

- ![NW Password Cracked](screenshots/NW%20Tool/NW%20Password%20Cracked.png)
- ![Password Use](screenshots/NW%20Tool/Password%20Use.png)

---

## 📊 Risk Analysis: The Danger of Weak Passwords

Through this lab, it became evident how quickly a weak password can be compromised. The cracked password `1qaz2wsx` is a common sequential pattern on a standard keyboard.

**Risks associated with weak passwords include:**

- **Dictionary Attacks:** Attackers use massive wordlists (like `rockyou.txt`) that contain millions of leaked passwords. Any password found in these lists can be cracked in seconds.
- **Brute Force & Pattern Recognition:** Attackers know users often use keyboard patterns (like `qwerty`, `123456`, or `1qaz2wsx`). Automated tools check these patterns first.
- **Data Breach:** If a protected file, system, or account falls into the wrong hands, a weak password offers virtually no defense, leading to data exposure, privilege escalation, or complete system compromise.

---

## 💡 Recommendations

To mitigate the risks of password cracking, the following security practices should be implemented:

1. **Enforce Strong Password Policies:** Require minimum lengths (12+ characters) and a mix of uppercase, lowercase, numbers, and symbols. Block common dictionary words and keyboard patterns.
2. **Implement Multi-Factor Authentication (MFA):** Even if a password is cracked, MFA acts as a critical second layer of defense.
3. **Use Password Managers:** Encourage the use of password managers to generate and store highly complex, unique passwords for every service.
4. **Upgrade Hashing Algorithms:** For application developers, ensure files and passwords are encrypted using strong, modern algorithms (like AES-256 for files and bcrypt or Argon2 for user passwords) to slow down cracking tools.

---

## 🎓 Conclusion

This lab provided hands-on experience with the mechanics of password cracking. By extracting hashes and using both GUI and CLI versions of John the Ripper, as well as online tools, I gained a deep understanding of how dictionary attacks operate.

I learned that password security is not just about stopping an attacker at the login screen; it's about ensuring that if data is ever extracted, the underlying hashes are resilient. This exercise reinforced the absolute necessity of strong, unique passwords and the importance of using robust encryption standards in cybersecurity.

---

## ⚠️ Ethical Disclaimer

This lab environment is strictly for educational purposes and authorized security testing only. Any password cracking techniques practiced here must only be applied to systems, files, and networks where explicit written permission has been granted. Unauthorized access to protected data or systems is illegal and strictly prohibited. The instructor, authors, and Networkwalks are not responsible for the misuse of this knowledge.

---

## 👨‍💻 Author

**Ohaddou**  
_Cybersecurity Professional - Cohort B084_  
[LinkedIn Profile](https://linkedin.com/in/your-profile) | [GitHub Profile](https://github.com/Ohaddou)
