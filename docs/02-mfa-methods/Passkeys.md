# Passkey MFA  

Passkeys as MFA and hardware keys

## The core difference — where the secret lives

[![](./assets/images/passkeys-vs-hardware-keys.png)](./passkeys-vs-hardware-keys.html)

Both passkeys and hardware keys use identical cryptography (FIDO2/WebAuthn). The difference is entirely about where the private key is stored and whether it can ever leave.

With a **passkey**, the private key lives inside your OS's secure storage (Windows Hello TPM, Apple Secure Enclave, Android secure element) or in a password manager vault. The crucial detail: it can be backed up and synced. This is a feature — lose your phone, your passkey moves to your new one via iCloud or Google account. But it also means that if someone fully compromises your cloud account or your OS, they could theoretically extract the key.

With a **hardware key** (YubiKey etc.), the private key is generated inside a purpose-built tamper-proof chip and is architecturally designed to never leave it — not even the device's own firmware can read it back out. There is no export, no backup, no sync. The key either exists on that physical device or it doesn't exist anywhere.

## Why AWS root specifically requires hardware keys

AWS does not currently support software passkeys for root MFA — only FIDO2 hardware security keys, TOTP apps, and hardware TOTP tokens. This is a deliberate policy decision given the risk level of root access (unrestricted, can do anything in the account including delete everything and close the account).

The rule of thumb is straightforward: the higher the stakes of the account, the more you want the guarantee that "cannot be copied" provides. AWS root is about as high-stakes as it gets, so hardware keys are the right tool.

## When passkeys are the better choice

For everyday accounts — Google, GitHub, Amazon, banking — passkeys are actually the smarter option for most people. They are just as phishing-proof as hardware keys, they're free, you don't need to carry anything extra, and cloud sync means you won't get locked out if you lose a device. The marginal risk from "could theoretically be extracted if your entire cloud account is also compromised" is very small for typical personal accounts.

The practical recommendation: use passkeys for everything in daily life, and reserve hardware keys for AWS root and any other accounts where losing access or compromise would be catastrophic.