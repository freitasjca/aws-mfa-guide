# MFA Overview — What is Multi-Factor Authentication?

> **Prerequisites:** None. This is the starting point.  
> **Next:** [MFA Comparison](MFA-comparison.md)

---

## What MFA is

Multi-Factor Authentication (MFA) requires you to prove your identity using two or more independent factors before granting access. The three factor categories are:

| Factor | What it means | Examples |
|---|---|---|
| Something you **know** | A secret only you hold | Password, PIN |
| Something you **have** | A physical or digital object | Phone, hardware key |
| Something you **are** | A biological trait | Fingerprint, Face ID |

MFA = using at least **two of these categories together**. Using two passwords is not MFA — they're both "something you know."

---

## Why MFA matters

A password alone is a single point of failure. Data breaches, phishing, and credential stuffing attacks compromise passwords constantly. MFA ensures that stealing a password is not enough.

```
Without MFA:   stolen password → account compromised
With MFA:      stolen password + attacker still needs the second factor
```

MFA stops approximately 99% of automated account attacks (Microsoft, 2019).

---

## The five MFA methods — at a glance

### 1. FIDO2 / Hardware security key
A physical USB or NFC device (e.g. YubiKey). Uses public-key cryptography. The private key never leaves the device. Phishing-proof because authentication is bound to the exact website domain.

→ See [FIDO2 Hardware Keys](../02-mfa-methods/FIDO2-hardware-keys.md)

### 2. Passkey
The same FIDO2 cryptography as a hardware key, but the private key is stored in software — your OS (Windows Hello, Apple Secure Enclave) or a password manager. Backed up to the cloud. Free, no hardware needed.

→ See [Passkeys](../02-mfa-methods/Passkeys.md)

### 3. TOTP authenticator app
An app (Google Authenticator, Authy, KeePassXC) generates a 6-digit code every 30 seconds using a shared secret + current time. Works offline. Not phishing-proof — a fake site can relay the code in real time.

→ See [TOTP Authenticator Apps](../02-mfa-methods/TOTP-authenticator-apps.md)

### 4. Hardware TOTP token
A standalone physical device with an LCD screen — no phone, no USB. Press the button, read the code. Same TOTP algorithm as an app, just in dedicated hardware. Niche use case.

→ See [Hardware TOTP Tokens](../02-mfa-methods/Hardware-TOTP-tokens.md)

### 5. SMS / Email OTP
A code sent to your phone or email. Requires connectivity. Vulnerable to SIM swap attacks and SS7 interception. Weakest MFA option — not available for AWS root.

→ See [Why SMS 2FA is Insecure](../02-mfa-methods/SMS-2FA-why-insecure.md)

---

## How TOTP works (simplified)

```
Setup (once):
  Server generates secret key
  → shown as QR code
  → stored in your auth app
  → server also stores it

Every 30 seconds:
  secret key + current time → HMAC hash → 6-digit code
  (both your app and the server compute this independently)

Login:
  You type the code → server checks its own computation → match = access granted
```

Nothing is transmitted after setup except the short-lived 6-digit code.

---

## How FIDO2 works (simplified)

```
Registration (once per site):
  Hardware key generates a unique key pair for this site
  Private key: stays on the device forever
  Public key: sent to and stored by the website

Login (every time):
  Server sends a random challenge
  User touches the key
  Key signs the challenge with the private key
  Server verifies the signature with the stored public key
```

No secret is ever transmitted. A fake site gets a signature that is mathematically useless for the real site.

---

## For AWS root specifically

AWS root has unrestricted access to your entire account — it can delete everything, close the account, bypass IAM policies. AWS supports these MFA types for root:

| Method | Available for root |
|---|---|
| FIDO2 hardware key | ✅ Yes — recommended |
| TOTP authenticator app | ✅ Yes |
| Hardware TOTP token | ✅ Yes |
| Passkey (software) | ❌ Not currently supported |
| SMS | ❌ Deprecated for root |

AWS allows up to **8 MFA devices** registered on a root account simultaneously.

---

## Next steps

- [Compare all MFA methods side by side →](MFA-comparison.md)
- [Set up a hardware key on AWS root →](../03-aws-setup/AWS-FIDO2-setup.md)
- [View the interactive comparison card →](../../assets/html/mfa-comparison.html)
