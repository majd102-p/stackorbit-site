---
title: "Reset a forgotten Windows password using recovery CMD (your own PC only)"
description: "Step‑by‑step guide to using the classic utilman.exe trick from Windows recovery CMD to reset a local account password on your own machine."
pubDate: "Dec 05 2025"
category: "Windows"
tags: ["windows", "recovery", "account", "cmd", "tips"]
heroImage: "../../assets/blog-placeholder-3.jpg"
draft: false
lang: "en"
---

> For **your own devices only** (or systems you have explicit permission to work on).

Sometimes you lose the password to a local Windows account but still have access to Windows recovery. One classic method is to boot into recovery, temporarily replace `utilman.exe` with `cmd.exe`, then use that elevated CMD from the login screen to reset the password.

## Steps (high‑level)

1. Boot into Windows setup or recovery and open **Command Prompt**.  
2. Identify the Windows drive (usually `C:`), then run:

X:> C:
C:>cd \Windows\System32


3. Back up `utilman.exe` and replace it with `cmd.exe`:

C:\Windows\System32>ren utilman.exe utilman1.exe
C:\Windows\System32>ren cmd.exe utilman.exe
C:\Windows\System32>exit

4. Reboot to the normal login screen and click the **Ease of Access** icon.  
An elevated command prompt should open instead of the usual accessibility tools.

5. Reset the local account password:

C:\Windows\System32>control userpasswords2


In the User Accounts window, select the locked account → **Reset Password…** and set a new strong password.  
If needed, you can also use:

net user
net user USERNAME NEW_STRONG_PASSWORD


6. After logging in successfully, restore the original files:

cd %SystemRoot%\System32
ren utilman.exe cmd.exe
ren utilman1.exe utilman.exe

This keeps the trick purely for recovery while returning your system to a secure, default state once you’re back in.
