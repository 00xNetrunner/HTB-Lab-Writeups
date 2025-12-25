# HTB-Lab-Writeups

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║                                                                               ║
║  ██╗  ██╗████████╗██████╗     ██╗      █████╗ ██████╗ ███████╗                ║
║  ██║  ██║╚══██╔══╝██╔══██╗    ██║     ██╔══██╗██╔══██╗██╔════╝                ║
║  ███████║   ██║   ██████╔╝    ██║     ███████║██████╔╝███████╗                ║
║  ██╔══██║   ██║   ██╔══██╗    ██║     ██╔══██║██╔══██╗╚════██║                ║
║  ██║  ██║   ██║   ██████╔╝    ███████╗██║  ██║██████╔╝███████║                ║
║  ╚═╝  ╚═╝   ╚═╝   ╚═════╝     ╚══════╝╚═╝  ╚═╝╚═════╝ ╚══════╝                ║
║                                                                               ║
║  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ ║
║  ░░░ H A C K   T H E   B O X   //   W R I T E U P S   D A T A B A S E ░░░    ║
║  ▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓▓ ║
║                                                                               ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

> Personal collection of Hack The Box lab writeups with detailed attack chains, credential dumps, and MITRE ATT&CK mappings.

---

## `>>> TARGET_INDEX`

### Windows Machines

| Machine | Difficulty | Attack Vector | Status |
|---------|------------|---------------|--------|
| [Support](machines/windows/Support/Support.md) | Easy | LDAP + GenericAll + RBCD | `[PWNED]` |

---

## `>>> ATTACK_CATEGORIES`

```
┌────────────────────────────────────────────────────────────────┐
│  ████ TECHNIQUES DOCUMENTED ████                               │
├────────────────────────────────────────────────────────────────┤
│  [+] Active Directory Exploitation                             │
│  [+] LDAP Enumeration & Attacks                                │
│  [+] Resource-Based Constrained Delegation (RBCD)              │
│  [+] BloodHound Attack Path Analysis                           │
│  [+] Credential Harvesting                                     │
│  [+] .NET Binary Reverse Engineering                           │
└────────────────────────────────────────────────────────────────┘
```

---

## `>>> TOOLS_ARSENAL`

- **Impacket** - Python collection for network protocols
- **BloodHound** - AD attack path visualization
- **Evil-WinRM** - Windows Remote Management shell
- **NetExec** - Network service enumeration
- **Rustscan** - Fast port scanner

---

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║  Author: Netrunner                                                            ║
║  Status: Active Development                                                   ║
╚═══════════════════════════════════════════════════════════════════════════════╝
```
