# AWS MFA & Authentication Security Guide

A practical, self-contained learning repository covering Multi-Factor Authentication (MFA) for AWS root access — from foundational concepts to hands-on setup guides.

---

## What this covers

- How MFA works and why it matters
- Every MFA method available for AWS root (FIDO2, TOTP, Hardware tokens, Passkeys, SMS)
- Step-by-step AWS setup guides with visual references
- Password manager integration (KeePassXC, Authy, 1Password)
- Passkeys on Windows, Android, and across platforms
- Disaster-proof backup strategies so you never get locked out

---

## Repository structure

```
aws-mfa-guide/
│
├── README.md                          ← You are here
│
├── docs/
│   ├── 01-concepts/                   ← Core MFA theory
│   │   ├── MFA-overview.md
│   │   └── MFA-comparison.md
│   │
│   ├── 02-mfa-methods/                ← One file per MFA type
│   │   ├── FIDO2-hardware-keys.md
│   │   ├── TOTP-authenticator-apps.md
│   │   ├── Hardware-TOTP-tokens.md
│   │   ├── Passkeys.md
│   │   └── SMS-2FA-why-insecure.md
│   │
│   ├── 03-aws-setup/                  ← AWS-specific guides
│   │   ├── AWS-root-access-overview.md
│   │   ├── AWS-FIDO2-setup.md
│   │   └── AWS-KeePassXC-setup.md
│   │
│   ├── 04-tools/                      ← Tool-specific guides
│   │   ├── KeePassXC.md
│   │   └── Windows-Hello-PIN.md
│   │
│   └── 05-passkeys/                   ← Passkeys deep dive
│       ├── Passkeys-complete-guide.md
│       └── Passkeys-vs-hardware-keys.md
│
├── assets/
│   ├── images/                        ← Screenshots and diagrams
│   ├── html/                          ← Interactive HTML reference cards
│   │   ├── mfa-comparison.html
│   │   ├── fido2-aws-guide.html
│   │   ├── totp-app-comparison.html
│   │   ├── passkeys-vs-hardware-keys.html
│   │   ├── hardware-totp-tokens.html
│   │   └── sms-2fa-insecurity.html
│   └── svg/
│       └── fido2-flow.svg
│
└── examples/
    └── disaster-proof-setup-checklist.md
```

---

## Quick navigation

| I want to... | Go to |
|---|---|
| Understand what MFA is | [MFA Overview](docs/01-concepts/MFA-overview.md) |
| Compare all MFA methods | [MFA Comparison](docs/01-concepts/MFA-comparison.md) · [Interactive](assets/html/mfa-comparison.html) |
| Set up a YubiKey on AWS root | [FIDO2 Setup](docs/03-aws-setup/AWS-FIDO2-setup.md) · [Interactive](assets/html/fido2-aws-guide.html) |
| Choose a TOTP app | [TOTP Apps](docs/02-mfa-methods/TOTP-authenticator-apps.md) · [Interactive](assets/html/totp-app-comparison.html) |
| Understand passkeys | [Passkeys Guide](docs/05-passkeys/Passkeys-complete-guide.md) |
| Use KeePassXC with AWS | [KeePassXC Setup](docs/03-aws-setup/AWS-KeePassXC-setup.md) |
| Understand why SMS 2FA is weak | [SMS 2FA](docs/02-mfa-methods/SMS-2FA-why-insecure.md) · [Interactive](assets/html/sms-2fa-insecurity.html) |
| Avoid getting locked out | [Disaster-proof checklist](examples/disaster-proof-setup-checklist.md) |

---

## MFA security ranking (for AWS root)

```
FIDO2 hardware key (YubiKey)   ████████████████████  Best — phishing-proof, physical
Passkey (Windows Hello, etc.)  ██████████████████    Great — phishing-proof, free
TOTP app (KeePassXC, Authy)    █████████████         Good — offline, not phishing-proof
Hardware TOTP token            ████████████          OK — no phone, not phishing-proof
SMS / Email OTP                ██████                Weak — SS7 vuln, SIM swap risk
                               └── NOT available for AWS root
```

---

## Interactive HTML reference cards

Each HTML file in `assets/html/` is a fully self-contained, standalone reference card with embedded CSS. Open directly in any browser — no server required.

| File | Contents |
|---|---|
| `mfa-comparison.html` | Full MFA method comparison table with security strength bars |
| `fido2-aws-guide.html` | Hardware key selector + AWS setup steps |
| `totp-app-comparison.html` | KeePassXC vs Authy vs Google Authenticator vs 1Password |
| `passkeys-vs-hardware-keys.html` | Side-by-side passkey vs hardware key comparison |
| `hardware-totp-tokens.html` | Hardware token devices, use cases, TOTP vs FIDO2 |
| `sms-2fa-insecurity.html` | SMS attack types + vulnerability comparison table |

---

## Prerequisites

No code required. This is a documentation-only repository. You need:
- A browser (for HTML reference cards)
- A Markdown viewer (GitHub renders `.md` files natively)

---

## Contributing

If you spot outdated information (prices, AWS UI changes, new YubiKey models), please open an issue or submit a pull request. AWS IAM and MFA settings change periodically.

---

## License

MIT — use freely for personal learning, team onboarding, or internal documentation.
