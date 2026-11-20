PDF Password Hash Extraction & Dictionary-Based Password Auditing (Kali Linux)

Internship: Network Walks Cybersecurity Internship — Week 3
Environment: Kali Linux

⚠️ Scope & Authorization
This exercise was performed only on PDF documents created specifically for testing, with explicit authorization as part of a structured internship exercise. The techniques below (hash extraction + dictionary attack) are for educational and authorized security-auditing purposes only. Do not run these steps against documents you do not own or do not have explicit written permission to test. Recovered passwords, extracted hashes, and the test documents themselves are not shared in this repository.

Project Overview

This project demonstrates how a password-protected PDF's encryption hash can be extracted and audited using a dictionary-based attack, to illustrate why weak passwords on sensitive documents are a real risk — and what it looks like from the attacker/auditor side.

Tools Used

	•	Kali Linux
	•	John the Ripper
	•	pdf2john.py
	•	PyHanko
	•	RockYou wordlist

Installation and Setup

Install John the Ripper and Python essentials:

sudo apt update
sudo apt install john python3-full python3-venv -y

Create a Python virtual environment (keeps PyHanko isolated from system Python):

python3 -m venv ~/pdf2john-venv

Install PyHanko inside the virtual environment:

~/pdf2john-venv/bin/pip install pyhanko

Verify the installation:

~/pdf2john-venv/bin/python -c "import pyhanko; print('PyHanko installed successfully')"

Practical Steps

1. Navigate to the working directory

cd ~/Desktop

2. Extract the PDF's password hash

~/pdf2john-venv/bin/python /usr/share/john/pdf2john.py "MyLockedPDF1.pdf" > "PDF hash 1.txt"

3. Verify the extracted hash file

ls -lh "PDF hash 1.txt"

4. Run the dictionary attack with John the Ripper

john --format=PDF --wordlist=/usr/share/wordlists/rockyou.txt "PDF hash 1.txt"

5. Display the cracked result

john --show --format=PDF "PDF hash 1.txt"

The same process can be repeated for additional authorized PDF documents, each using its own separate hash file.

What I Learned

	•	Extracting password hashes from PDF documents
	•	Using John the Ripper for password auditing
	•	Running dictionary-based attacks against weak passwords
	•	Managing isolated Python dependencies (venv) on Kali Linux
	•	Why password strength and encryption choice matter for document security

Conclusion

This exercise strengthened my practical understanding of password auditing and the workflow security professionals use to assess the real-world strength of password-protected PDF documents.

Disclaimer

Conducted for educational purposes only, on documents authorized for testing. No password hashes, recovered credentials, or private documents are included in this repository.
