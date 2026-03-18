# 🔑 Passkeys — Complete Reference Guide

---

## 1. What Are Passkeys?

Passkeys are a **passwordless authentication standard** based on public-key cryptography (FIDO2/WebAuthn). They replace traditional passwords with a cryptographic key pair, eliminating the risk of password leakage.

### How They Work

**Step 1 — Create a Passkey**
- The user confirms their identity using biometrics (Face ID, fingerprint) or a PIN
- A **private key** is generated and stored securely on the device
- The corresponding **public key** is sent to and stored by the website

**Step 2 — Sign In with a Passkey**
- The user selects their account and presents their credentials (biometric/PIN)
- The **private key** unlocks and authenticates — no password is ever transmitted
- Websites never store passwords, so there is nothing to leak or steal

> ✅ Passkeys are built on open standards and work across Windows, macOS, iOS, Android, and ChromeOS with a consistent user experience.

---

## 2. Platform Support

### ✅ Windows Laptop (e.g., Lenovo Legion Pro 5)

Requirements:
- **Windows 10 (2004+)** or **Windows 11** (recommended)
- **Windows Hello** — PIN, fingerprint, or face unlock
- **TPM 2.0** security chip
- Modern browser: Chrome or Edge

Full passkey support includes creating, storing, and signing in with passkeys using Windows Hello. Passkeys are managed via **Settings → Accounts → Passkeys**.

> ⚠️ **Local account limitation:** Passkeys stored on a local Windows account are **device-bound**. If the laptop is lost or reinstalled, those passkeys are lost — backups are essential.

### ✅ Standard Android (Android 9+, full Google services)

- Requires **Google Play Services + Credential Manager API**
- Secure lock screen (PIN or biometric) mandatory
- Works well on Android 13/14+ with Google Pixel, Samsung, etc.

### ❌ Huawei / EMUI 12

- Most post-2019 Huawei devices **lack Google Play Services**
- Passkeys on Android depend on Google infrastructure
- Support is **absent or unreliable** on EMUI 12
- Huawei's own ecosystem (HMS) offers only limited/proprietary passkey support

**To check passkey support on EMUI 12:**
1. Verify Google Play Services exists: *Settings → Apps → search "Google Play services"*
2. Confirm browser is updated (Chrome or Edge)
3. Check lock screen has PIN or biometric set
4. Do a real test: try creating a passkey at `myaccount.google.com` or `github.com`

---

## 3. Windows Passkey Readiness Checklist

| # | Check | Requirement |
|---|-------|-------------|
| 1 | Windows Version | Windows 10 (2004+) or Windows 11 |
| 2 | Windows Hello PIN | PIN set up and working |
| 3 | TPM Security Chip | TPM 2.0 present and enabled |
| 4 | Browser & Site Support | Chrome or Edge; site must support passkeys |
| 5 | Backup Login Methods | Password + 2FA + Recovery Codes saved |
| 6 | Test Passkey Setup | Create and log in with a passkey to confirm |

> 💡 **Tip:** Verify TPM 2.0 is active via *Device Manager → Security Devices → Trusted Platform Module 2.0*

---

## 4. Disaster-Proof Passkey Setup

Since passkeys on a local Windows account are device-bound, a proper backup strategy is essential.

### Step 1 — Prepare the Laptop
- Configure **Windows Hello PIN** (*Settings → Accounts → Sign-in options*)
- Keep Chrome/Edge updated
- Install a password manager: **1Password** or **Bitwarden**

### Step 2 — Enable Backup Login for Each Account

**Amazon**
- *Account & Lists → Login & Security*
- Set a password + enable Two-Step Verification (SMS, email, or authenticator app)
- Generate and save Recovery Codes offline

**Google**
- *myaccount.google.com → Security → 2-Step Verification*
- Enable authenticator app or SMS backup
- Download Backup Codes and store securely offline

**GitHub**
- *Settings → Security → Two-factor authentication*
- Enable authenticator app
- Generate and save Recovery Codes offline

### Step 3 — Create Passkeys
1. Open Chrome or Edge on the laptop
2. Go to the site's security settings
3. Select **"Create a passkey"**
4. Approve with Windows Hello (PIN or fingerprint)
5. The passkey is now bound to the laptop's TPM + Windows Hello

### Step 4 — Test Alternative Access
- Log out and attempt to sign in from **another device**
- Confirm that **Password + 2FA** or **Recovery Codes** work correctly
- This ensures you are never locked out if the laptop fails

### Step 5 (Optional) — Future-Proof with Microsoft Account
- Switching to a Microsoft account allows passkeys to **sync across devices automatically**
- Significantly reduces the risk of permanent lockout
- Local accounts + proper backups are still safe, but require more discipline

---

## 5. Emergency Protocol (If Laptop Fails)

1. Go to any other device (phone, desktop, another laptop)
2. Log in using: **Password + 2FA**, or **Recovery Codes**
3. Once in, create new passkeys on the new device
4. Update password manager and offline storage with new credentials

---

## 6. Secure Backup Storage Options

| Tool | Type | Cloud Sync | Offline Option |
|------|------|-----------|----------------|
| **1Password** | Password manager | ✅ Yes | ✅ Yes |
| **Bitwarden** | Password manager | ✅ Yes | ✅ Yes |
| **KeePassXC** | Password manager | ❌ Manual | ✅ Yes (local DB) |
| **Encrypted USB** | Physical storage | ❌ No | ✅ Yes |

> Store backup passwords, 2FA recovery codes, and any exportable passkeys in at least **one offline/encrypted location**.

---

## 7. Local Account vs Microsoft Account Summary

| Feature | Local Account | Microsoft Account |
|---------|--------------|-------------------|
| Passkey stored | Device only | Syncs across devices |
| Recovery if laptop dies | Requires backup password/2FA | Sign in on new device using synced passkeys |
| Risk of lockout | High (without backups) | Low |

---

## 8. Key Takeaways

- 🔐 **Passkeys eliminate passwords** — the private key never leaves your device
- 🖥️ **Windows 11 + Windows Hello + TPM 2.0** = full passkey support
- 📵 **EMUI 12 / Huawei** = unreliable or no passkey support without Google Play Services
- 💾 **Always keep backup login methods**: password + 2FA + recovery codes
- 🔄 **Test your backups** from another device periodically
- ☁️ **Microsoft account** reduces lockout risk through passkey sync
- 🛡️ **1Password or Bitwarden** are the recommended managers for storing recovery credentials
