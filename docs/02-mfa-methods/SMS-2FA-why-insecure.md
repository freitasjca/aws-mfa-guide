# Why SMS 2FA is Insecure

> **See also:** [Interactive HTML reference card](../../assets/html/sms-2fa-insecurity.html)  
> **Related:** [MFA Comparison](../01-concepts/MFA-comparison.md)

SMS 2FA has fundamental architectural weaknesses that go beyond "someone could steal your phone." It's a 1980s messaging system being pressed into service as a security layer — and the seams show.

---

## Attack types

### SIM swap — High risk

An attacker calls your mobile carrier, impersonates you using personal data (date of birth, address, last 4 of ID number) purchased from data brokers, and convinces the carrier to transfer your number to a new SIM they control. Your phone loses signal. All SMS codes go to the attacker.

> **No malware needed — just a phone call to your carrier.**

High-profile victims have included cryptocurrency holders and tech executives. The attack is low-tech and disturbingly effective.

---

### SS7 protocol exploit — Infrastructure flaw

SS7 (Signalling System 7) is the 1970s-era protocol that routes SMS worldwide. It was designed for trust between carriers, not security. Anyone with SS7 network access — nation-states, criminal groups, rogue carriers — can silently redirect SMS messages in transit without touching your phone.

> **No fix is possible — it is a flaw baked into global telecom infrastructure.**

---

### Real-time phishing interception — Common

A fake login page captures your password, immediately logs into the real site, triggers an SMS, then prompts you for the code. You type it in. The attacker relays it to the real site within the 30-second window.

> **Note: TOTP apps are equally vulnerable to this specific attack.**

---

### Malware on device — Moderate

Android malware can read SMS messages directly from the inbox. Banking trojans have done this for years. The code arrives; the malware forwards it before you even see the notification.

---

### Requires mobile signal — Availability issue

Unlike TOTP or hardware keys, SMS requires your phone to have active mobile service. Travel, roaming problems, carrier outages, or poor signal can lock you out entirely.

---

## Vulnerability comparison

| Attack | SMS | TOTP app | FIDO2 key |
|---|---|---|---|
| SIM swap | ❌ Vulnerable | ✅ Safe | ✅ Safe |
| SS7 intercept | ❌ Vulnerable | ✅ Safe | ✅ Safe |
| Real-time phishing | ❌ Vulnerable | ❌ Vulnerable | ✅ Safe |
| Device malware | ❌ Vulnerable | ⚠️ Partial | ✅ Safe |
| No signal / offline | ❌ Breaks | ✅ Works | ✅ Works |
| Password-only breach | ✅ Still protected | ✅ Still protected | ✅ Still protected |

---

## The bottom line

SMS 2FA is much better than no 2FA at all — it stops essentially all automated credential-stuffing attacks. The attacks above require targeted effort against a specific person.

However, for any high-value account — AWS root, primary email, banking — the SIM swap risk alone justifies upgrading to TOTP or FIDO2.

This is why **AWS does not offer SMS as an MFA option for root accounts.**

---

## What to use instead

| Situation | Recommendation |
|---|---|
| AWS root | FIDO2 hardware key |
| Personal accounts (Google, GitHub) | Passkeys or TOTP app |
| Work accounts | TOTP app or hardware key per policy |
| Currently using SMS | Upgrade to Authy or Google Authenticator minimum |
