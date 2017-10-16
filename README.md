# *K*ey *R*einstallation *A*tta*ck*s (KRACK)

From the KRACK <a href="https://www.krackattacks.com/">website</a>:
> In a key reinstallation attack, the adversary tricks a victim into reinstalling an already-in-use key. This is achieved by manipulating and replaying cryptographic handshake messages. When the victim reinstalls the key, associated parameters such as the incremental transmit packet number (i.e. nonce) and receive packet number (i.e. replay counter) are reset to their initial value. Essentially, to guarantee security, a key should only be installed and used once. Unfortunately, we found this is not guaranteed by the WPA2 protocol. By manipulating cryptographic handshakes, we can abuse this weakness in practice.

## Unless a known patch has been applied, assume that all WPA2 enabled Wi-fi devices are vulnerable.

## Attacks that can be made (できること)
* Adversary can decrypt arbitrary packets.
  * This allows an adversary to obtain the TCP sequence numbers of a connection, and <a href="https://en.wikipedia.org/wiki/TCP_sequence_prediction_attack">hijack TCP connections</a>.
* Adversary can replay broadcast and multicast frames.
* Adversary can both decrypt and inject arbitrary packets. *(TKIP or GCMP ONLY)*
* Adversary can force the client into using a predictable all-zero encryption key. *(ANDROID 6.0+ and LINUX)*

## Attacks that can not be made (できないこと)
* Adversary can not recover WPA password.
* Adversary can not inject packets. *(AES-CCMP ONLY)*


# Vendor Response

| Vendor                                           | Official Response                                                                                            | Comment                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Last Checked | Last Updated | Date Notified by CERT |
|--------------------------------------------------|--------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|--------------|-----------------------|
| Android                                          | No Known Official Response                                                                                   | Android 6.0 and above affected (Android uses wpa_supplicant and therefore is affected).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | 2017-10-16   | 2017-10-16   |                       |
| Apple                                            | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Buffalo / MELCO                                  | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Cisco                                            | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   | 28 Aug 2017           |
| Debian / Ubuntu                                  | http://seclists.org/bugtraq/2017/Oct/25                                                                      | * Add patches to fix WPA protocol vulnerabilities (CVE-2017-13077,    CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081,    CVE-2017-13082, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088):    - hostapd: Avoid key reinstallation in FT handshake    - Prevent reinstallation of an already in-use group key    - Extend protection of GTK/IGTK reinstallation of WNM-Sleep Mode cases    - Fix PTK rekeying to generate a new ANonce    - TDLS: Reject TPK-TK reconfiguration    - WNM: Ignore WNM-Sleep Mode Response if WNM-Sleep Mode has not been used    - WNM: Ignore WNM-Sleep Mode Response without pending request    - FT: Do not allow multiple Reassociation Response frames    - TDLS: Ignore incoming TDLS Setup Response retries | 2017-10-16   | 2017-10-16   |                       |
| Espressif Systems                                | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-19   | 2017-10-19   | 22 Sep 2017           |
| FreeBSD Project                                  | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-20   | 2017-10-20   | 28 Aug 2017           |
| Google                                           | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| HPE Aruba                                        | http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007.txt                                             |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   | 28 Aug 2017           |
| Huawei                                           | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Intel Corporation                                | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-21   | 2017-10-21   | 28 Aug 2017           |
| Juniper Networks                                 | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-22   | 2017-10-22   | 28 Aug 2017           |
| Linksys                                          | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Linux                                            | Patches: https://w1.fi/security/2017-1/                                                                      | wpa_supplicant version 2.4 and above is affected. Linux's wpa_supplicant v2.6 is also vulnerable to the installation of an all-zero encryption key in the 4-way handshake.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      | 2017-10-16   | 2017-10-16   |                       |
| MediaTek                                         | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Meraki                                           | No Known Official Response                                                                                   | Fixed for Cisco Meraki in 24.11 and 25.7                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | 2017-10-16   | 2017-10-16   |                       |
| Microchip Technology                             | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-23   | 2017-10-23   | 28 Aug 2017           |
| Microsoft                                        | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Mikrotik                                         | https://forum.mikrotik.com/viewtopic.php?f=21&t=126695                                                       | We released fixed versions last week, so if you upgrade your devices routinely, no further action is required.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  | 2017-10-16   | 2017-10-16   |                       |
| OpenBSD                                          | https://marc.info/?l=openbsd-announce&m=148839684520133&w=2                                                  | This problem only affects OpenBSD clients. OpenBSD access points are unaffected. The problem has been fixed in -current. For 5.9 and 6.0 the following errata patches are available.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | 2017-10-16   | 2017-10-16   |                       |
| Red Hat, Inc.                                    | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-24   | 2017-10-24   | 28 Aug 2017           |
| Samsung Mobile                                   | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-25   | 2017-10-25   | 28 Aug 2017           |
| Toshiba Commerce Solutions                       | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-26   | 2017-10-26   | 15 Sep 2017           |
| Toshiba Electronic Devices & Storage Corporation | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-27   | 2017-10-27   | 28 Aug 2017           |
| Toshiba Memory Corporation                       | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   | 28 Aug 2017           |
| Ubiquiti Networks                                | https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365 | Ubiquiti has released 3.9.3.7537 to mitigate these vulnerabilities.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | 2017-10-16   | 2017-10-16   |                       |
| WiFi Alliance                                    | https://www.wi-fi.org/security-update-october-2017                                                           | Users should refer to their Wi-Fi device vendor’s website or security advisories to determine if their device has been affected and has an update available. As always, Wi-Fi users should ensure they have installed the latest recommended updates from device manufacturers.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| Yamaha                                           | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-16   | 2017-10-16   |                       |
| ZyXEL                                            | No Known Official Response                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | 2017-10-17   | 2017-10-17   | 28 Aug 2017           |

