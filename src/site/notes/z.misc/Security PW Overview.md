---
{"dg-publish":true,"permalink":"/z-misc/security-pw-overview/","dg-note-properties":{}}
---

#pw #s8 
 labs ask for **Windows 10 as a VM**, not as host.

| Lab | Windows? | Note                                                                                           |
| --- | -------: | ---------------------------------------------------------------------------------------------- |
| 1   |      Yes | Windows 10 target VM + Kali attacker VM                                                        |
| 2   |      Yes | Windows 10 target VM for Meterpreter/backdoor                                                  |
| 3   |       No | Kali Linux + DVWA/Docker/Burp Suite                                                            |
| 4   |      Yes | Windows 10 attacker VM + Kali victim/IDS/IPS                                                   |
| 5   |       No | MySQL, PHP, Composer, Docker; Linux Mint is suitable                                           |
| 6   |  Part II | SonarQube steps are written for Windows, but SonarQube can also run on Linux/Docker if allowed |
| 7   |       No | Kali/Linux + Python/ML work                                                                    |

1. ~~Install **VirtualBox**.~~
2. Create two VMs:
   - **Kali Linux**
   - **Windows 10**
3. Use the required network mode per lab:
   - Labs 1 and 2: Bridged Adapter
   - Lab 4: Host-only/NAT as specified
1. Keep Windows Defender/SmartScreen disabled **only inside the Windows VM** when the lab requires it.

Recommended :

- RAM: **16 GB**
- Storage: at least **80–100 GB free**
- CPU virtualization enabled: **Intel VT-x / AMD-V**

If limited RAM, start needed VMs one a time.