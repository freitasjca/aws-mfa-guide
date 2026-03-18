# Disaster-Proof AWS Root MFA Setup Checklist

Use this checklist to ensure you can always access your AWS root account — even if your laptop fails, your phone is lost, or your primary MFA device is unavailable.

---

## Phase 1 — Prepare your laptop

- [ ] Windows Hello PIN configured (*Settings → Accounts → Sign-in options*)
- [ ] Browser up to date (Chrome or Edge recommended)
- [ ] Password manager installed (KeePassXC, 1Password, or Bitwarden)
- [ ] `.kdbx` vault backed up to at least two locations (external drive + encrypted cloud)

---

## Phase 2 — Set up primary MFA on AWS root

- [ ] Sign in to AWS console as root
- [ ] Navigate to *Account menu → Security credentials → Multi-factor authentication*
- [ ] Assign first MFA device (FIDO2 hardware key recommended)
- [ ] Test: sign out and sign back in using MFA
- [ ] Register a **second** MFA device (backup key or TOTP app)
- [ ] Store second device in a physically separate, secure location

---

## Phase 3 — Amazon account backup

- [ ] Password stored in password manager
- [ ] Two-Step Verification enabled (*Account & Lists → Login & Security*)
- [ ] Recovery codes generated and saved offline
- [ ] Test login from a second device using password + 2FA

---

## Phase 4 — Google account backup

- [ ] *myaccount.google.com → Security → 2-Step Verification* enabled
- [ ] Authenticator app or backup codes configured
- [ ] Backup codes downloaded and stored offline/encrypted
- [ ] Test login from a second device

---

## Phase 5 — GitHub account backup

- [ ] *Settings → Security → Two-factor authentication* enabled
- [ ] Authenticator app configured
- [ ] Recovery codes generated and stored offline
- [ ] Test login from a second device

---

## Phase 6 — Emergency protocol (if laptop fails)

If your laptop is lost, stolen, or broken:

1. Go to any other device (phone, another laptop, desktop)
2. Log in using: **Password + 2FA backup**, or **Recovery codes**
3. Once in, register new MFA devices on the new device
4. Update password manager / offline storage with new credentials

---

## Storage locations — what goes where

| Item | Where to store |
|---|---|
| Master password for KeePassXC | Memory only — never written down |
| KeePassXC `.kdbx` vault | Encrypted USB + encrypted cloud (OneDrive, etc.) |
| Recovery codes (AWS, Google, GitHub) | Password manager vault + printed copy in a safe |
| Backup hardware key | Physically separate location from primary key |
| Hardware TOTP token (if used) | Physical safe — replace before battery dies (3–5 years) |

---

## Periodic maintenance

- [ ] Monthly: test that backup login method still works from another device
- [ ] Annually: check hardware token battery status / expiry
- [ ] When leaving a job: rotate all credentials and deregister shared devices
- [ ] After any device loss: immediately revoke old MFA, register new device

---

## Key principles

- Never store your primary and backup MFA devices together
- Always have at least two independent ways into every critical account
- Recovery codes are your last resort — store them like a physical key
- Test your backups before you need them
