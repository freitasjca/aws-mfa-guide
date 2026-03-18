# Passkeys vs Hardware Security Keys

> **See also:** [Interactive HTML comparison](../../assets/html/passkeys-vs-hardware-keys.html)

Both passkeys and hardware keys use the same underlying cryptography (FIDO2/WebAuthn). The difference is entirely about **where the private key lives** and whether it can ever leave.

---

## Side-by-side comparison

| | Passkey | Hardware security key |
|---|---|---|
| Private key stored in | OS / password manager | Tamper-proof chip |
| Authentication via | Biometric or PIN | Physical touch |
| Can be backed up | ✅ Yes — cloud sync | ❌ No — by design |
| Physical device needed | No | Yes — always |
| Phishing resistant | ✅ Yes | ✅ Yes |
| Can be extracted if compromised | ⚠️ Theoretically | ❌ Never |
| Cost | Free | €35–70 |

---

## Where passkeys live (by platform)

| Platform | Storage | Sync mechanism |
|---|---|---|
| Windows Hello | TPM chip on device | Microsoft account (optional) |
| Apple iOS / macOS | Secure Enclave chip | iCloud Keychain |
| Android | Secure element | Google Password Manager |
| 1Password / Bitwarden | Encrypted vault | Cloud vault sync |

---

## The threat model difference

Both methods are phishing-proof — a fake site cannot use either type of authentication credential because the keys are cryptographically bound to the exact website domain.

The distinction is about what happens if your **device or cloud account** is compromised:

- **Passkey:** If an attacker fully owns your OS or cloud account, they could theoretically extract the private key. The sync feature that makes passkeys convenient is also what makes this possible.
- **Hardware key:** The private key is generated inside a dedicated security chip and architecturally cannot leave it. Even the device's own firmware cannot read the key out. No export, no backup, no sync — by design.

---

## Which to use — by account type

| Account | Recommendation | Reason |
|---|---|---|
| AWS root | Hardware key | Passkeys not supported for root MFA |
| AWS IAM users | Either | Both are phishing-proof and well-supported |
| Google, GitHub, Amazon | Passkey | Free, phishing-proof, cloud sync prevents lockout |
| Banking | Passkey | Most banks now support passkeys |
| Personal accounts generally | Passkey | Convenience with strong security |
| Shared/emergency accounts | Hardware key | No personal device dependency |

---

## Key insight

Passkeys trade the hardware key's "cannot be copied" guarantee for the convenience of cloud sync and not needing a physical device. For most personal accounts, that tradeoff is excellent. For AWS root — where the account has unrestricted access to everything — the hardware key's absolute guarantee is worth the added friction.
