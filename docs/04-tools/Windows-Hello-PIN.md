# Windows Hello PIN  

---

## How It Works

Windows Hello PIN is a **local convenience unlock** — it is an alternative way to prove to Windows that *you* are present at the device. Under the hood, your **user account password still exists** and is still fully functional.

Think of it like this:

> PIN = a faster local shortcut to unlock your session
> Password = the underlying account credential that still works normally

---

## You Can Always Use Your Password

At the Windows login screen:
- Click **"Sign-in options"** (below the PIN field)
- Select the **key/password icon**
- Type your regular user password as usual

This works even if Windows Hello PIN is your default login method.

---

## When Is the Password Still Required?

There are situations where Windows will ask for your **password instead of PIN**:

| Situation | Requires Password |
|---|---|
| First login after a reboot (sometimes) | ✅ |
| PIN not yet set up on a new device | ✅ |
| Joining/leaving a domain | ✅ |
| Changing account settings | ✅ |
| Remote Desktop (RDP) login | ✅ |
| PIN has been reset or corrupted | ✅ |
| After certain Windows updates | ✅ |

---

## Important Distinction — Local vs Microsoft Account

- **Local account:** Your password is stored only on the device. PIN is just an easier way to unlock it.
- **Microsoft account:** Your password is your Microsoft/Outlook credentials. PIN unlocks the session locally without sending the password over the internet — which is actually more secure.

---

## Bottom Line

> ✅ Activating Windows Hello PIN **does not disable your password**.
> Both work independently. Your password remains your safety net.