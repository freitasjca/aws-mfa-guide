# MFA Methods — Full Comparison

> **See also:** [Interactive HTML comparison card](../../assets/html/mfa-comparison.html) — open in any browser

---

## Feature comparison

| Method | Phishing resistant | Works offline | No phone needed | Recovery if lost | Cost |
|---|---|---|---|---|---|
| **FIDO2 hardware key** | ✅ Yes | ✅ Yes | ✅ Yes | Register 2nd key | €35–70 |
| **Passkey** | ✅ Yes | ✅ Yes | Depends on platform | Cloud sync | Free |
| **TOTP app** | ❌ No | ✅ Yes | ❌ Phone required | Backup codes | Free |
| **Hardware TOTP token** | ❌ No | ✅ Yes | ✅ Yes | Buy spare | €20–50 |
| **SMS / Email OTP** | ❌ No | ❌ No | ❌ Phone required | Easy | Free |

---

## Security strength (relative)

```
FIDO2 hardware key    ████████████████████  95%  Phishing-proof + physical presence
Passkey               ██████████████████    88%  Phishing-proof, software-stored key
TOTP app              █████████████         65%  Offline, interceptable in real time
Hardware TOTP token   ████████████          60%  No phone, same interception risk
SMS / Email OTP       ██████                30%  SS7 vuln + SIM swap + needs signal
```

---

## Attack vulnerability matrix

| Attack vector | SMS | TOTP app | FIDO2 key |
|---|---|---|---|
| SIM swap | ❌ Vulnerable | ✅ Safe | ✅ Safe |
| SS7 network intercept | ❌ Vulnerable | ✅ Safe | ✅ Safe |
| Real-time phishing relay | ❌ Vulnerable | ❌ Vulnerable | ✅ Safe |
| Device malware | ❌ Vulnerable | ⚠️ Partial | ✅ Safe |
| No signal / offline use | ❌ Breaks | ✅ Works | ✅ Works |
| Password-only breach | ✅ Still protected | ✅ Still protected | ✅ Still protected |

**Key insight:** FIDO2 is the only method that defeats real-time phishing — because authentication is cryptographically bound to the exact website domain. A fake site receives a signature that cannot be used on the real site.

---

## Decision guide — which method to choose

**For AWS root account:**
Use a FIDO2 hardware key (YubiKey). Register two. Passkeys are not currently supported for root MFA. SMS is not available.

**For AWS IAM users:**
Hardware key or TOTP app both work well. TOTP app (KeePassXC) is the lowest-friction option.

**For Google, GitHub, Amazon, banking:**
Passkeys are the best choice — phishing-proof, free, no hardware to carry. Use a TOTP app as backup.

**For regulated workplaces (no phones allowed):**
Hardware TOTP token or FIDO2 hardware key. Both work without a smartphone.

**For non-technical users:**
TOTP app (Google Authenticator) or hardware TOTP token — both are simple to operate.

---

## AWS root: what is and isn't available

| Method | AWS root support |
|---|---|
| FIDO2 / Security key | ✅ Supported — strongly recommended |
| TOTP authenticator app | ✅ Supported |
| Hardware TOTP token | ✅ Supported |
| Passkey (software) | ❌ Not currently supported for root |
| SMS | ❌ Deprecated — not available for root |

Maximum MFA devices on a root account: **8**

---

## Related guides

- [FIDO2 Hardware Keys →](../02-mfa-methods/FIDO2-hardware-keys.md)
- [TOTP Authenticator Apps →](../02-mfa-methods/TOTP-authenticator-apps.md)
- [Hardware TOTP Tokens →](../02-mfa-methods/Hardware-TOTP-tokens.md)
- [Passkeys →](../02-mfa-methods/Passkeys.md)
- [Why SMS 2FA is Insecure →](../02-mfa-methods/SMS-2FA-why-insecure.md)
