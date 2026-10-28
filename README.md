# Active Directory Home Lab

A Windows Server 2025 Domain Controller lab built from scratch in VirtualBox to practice enterprise identity and network infrastructure.

## Architecture
```

┌─────────────────────────────────────────┐
│           VirtualBox Host               │
│         (Internal Network)              │
│                                         │
│  ┌─────────────────────────────┐        │
│  │   DC01                      │        │
│  │   Windows Server 2025       │        │
│  │   • Active Directory DS     │        │
│  │   • DNS Server              │        │
│  │   • DHCP Server             │        │
│  │   IP: 192.168.56.10        │        │
│  └─────────────────────────────┘        │
│                                         │
│  Domain: akrem.local                    │
│  Network: 192.168.56.0/24               │
└─────────────────────────────────────────┘

```

| Machine | OS | Role | IP Address |
|---------|-----|------|------------|
| DC01 | Windows Server 2025 Standard Evaluation | Domain Controller, DNS, DHCP | 192.168.56.10 |

## What I Built

### Phase 1: Domain Controller
- Installed Windows Server 2025 Standard Evaluation (Desktop Experience) from ISO in VirtualBox
- Configured static IP: `192.168.56.10` / `255.255.255.0`
- Installed Active Directory Domain Services, DNS Server, and DHCP Server roles
- Promoted server to Domain Controller for forest `akrem.local`
- Created Organizational Units: `IT`, `HR`, `Finance`
- Created test domain user: `tuser`

### Phase 2: DNS Configuration
- Configured forward lookup zone for `akrem.local`
- Set DC as primary DNS server (`192.168.56.10`)
- Verified name resolution for domain resources

### Phase 3: DHCP Configuration
- New scope: `192.168.56.100` – `192.168.56.200`
- Subnet mask: `255.255.255.0`
- DNS server: `192.168.56.10`
- Authorized and activated the scope

### Phase 4: Linux Client Exploration
- Deployed Ubuntu 22.04 LTS VM on VirtualBox Internal Network
- Configured static IP via Netplan (`192.168.56.101/24`)
- Explored cross-platform Active Directory integration using `realmd`, `sssd`, and Kerberos
- Documented networking and DNS troubleshooting process

## Key Configuration

### Static IP Configuration (DC01)
| Setting | Value |
|---------|-------|
| IP Address | 192.168.56.10 |
| Subnet Mask | 255.255.255.0 |
| DNS Server | 127.0.0.1 (self) |

### DHCP Scope
| Setting | Value |
|---------|-------|
| Start IP | 192.168.56.100 |
| End IP | 192.168.56.200 |
| DNS Server | 192.168.56.10 |

## Screenshots

![Server Manager - Roles Installed]
![Local Server Properties]
![Active Directory Users and Computers]
![DNS Manager - Forward Lookup Zone]
![IP Configuration - ipconfig all]

## Skills Demonstrated

- **Windows Server Administration:** AD DS, DNS, DHCP, user/computer management
- **Network Configuration:** Static IP assignment, subnetting, DNS resolution
- **Virtualization:** Oracle VirtualBox, internal networking, VM resource management
- **Directory Services:** Domain creation, OU structure, security principals
- **Troubleshooting:** DNS resolution, DHCP scope issues, service configuration
- **Linux Integration:** Netplan configuration, cross-platform identity concepts

## Tools Used

| Category | Tools |
|----------|-------|
| Virtualization | Oracle VirtualBox |
| Server OS | Windows Server 2025 |
| Directory Services | Active Directory Domain Services |
| Network Services | DNS, DHCP |
| Linux Client | Ubuntu 22.04 LTS |

## Next Steps

- [ ] Configure Group Policy Objects (GPOs) for security hardening
- [ ] Automate bulk user creation with PowerShell
- [ ] Pursue Azure Administrator (AZ-104) certification

---

*Built as part of a self-directed sysadmin training path targeting infrastructure roles in the Middle East.*
