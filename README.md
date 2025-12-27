# Auto AD Recon
### NetExec Wrapper for Automated Active Directory Enumeration

Auto AD Recon is a modular Python wrapper for NetExec  
https://github.com/Pennyw0rth/NetExec

It performs extensive Active Directory enumeration over **SMB** and **LDAP**, supporting multiple authentication methods and custom modules for privilege escalation and misconfiguration discovery. Designed for red teams, internal pentests, and AD-focused CTFs.

---

## Features
- Multi-protocol AD enumeration (SMB, LDAP)
- Authentication via password, NTLM hash, or null session
- Parallel execution of built-in and custom NetExec modules
- ADCS misconfiguration detection (ESC1–ESC8)
- ACL parsing (GenericAll, WriteDACL, etc.)
- LAPS credential extraction
- Trusts, group membership, machine quota discovery
- Optional BloodHound-compatible collection
- Colorized CLI output + optional file logging
- Command summaries and error handling

---

## Installation

### Install NetExec
```bash
pipx install netexec
# or
pip install netexec
```

### Clone the wrapper
```bash
git clone https://github.com/azunhsephiroth77/auto-ad-recon-netexec.git
cd auto-ad-recon-netexec
chmod +x auto_ad_recon.py
```

---

## Usage Examples

### Full enumeration with credentials
```bash
python3 auto_ad_recon.py -t dc.domain.com -u username -pw password
```

### Null session enumeration
```bash
python3 auto_ad_recon.py -t 192.168.1.10 --null-session
```

### NTLM hash authentication
```bash
python3 auto_ad_recon.py -t target.htb -u admin -H <NTLM_HASH>
```

### LDAP-only enumeration
```bash
python3 auto_ad_recon.py -t dc.corp.local -u user -pw pass -p ldap
```

### SMB-only enumeration
```bash
python3 auto_ad_recon.py -t 10.10.10.100 -u guest -pw '' -p smb
```

### BloodHound-compatible collection
```bash
python3 auto_ad_recon.py -t dc.htb.local -u user -pw pass --dns-server 10.129.169.157
```

---

## Command-Line Arguments
```text
-t, --target        Target IP or hostname (required)
-u, --username      Username
-pw, --password     Password
-H                  NTLM hash
--null-session      Anonymous bind
-p, --protocols     ldap | smb | both (default: both)
--builtin-only      Run only NetExec built-in flags
--modules-only      Run only custom modules
--dns-server        DNS server IP (BloodHound)
-d, --delay         Delay between commands (default: 2s)
-o, --output        Write output to file
```

---

## Author
**Abhishek Joshi**  
GitHub: https://github.com/TechnoFlux  
LinkedIn: https://www.linkedin.com/in/reverse-shell
