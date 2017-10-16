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

## Related Reading
* https://blog.cryptographyengineering.com/2017/10/16/falling-through-the-kracks/
* https://www.reddit.com/r/KRaCK/comments/76pjf8/krack_megathread_check_back_often_for_updated/


# Vendor Response

| Vendor | Official Response | Comment | Last Checked | Last Updated | Date Notified by CERT |
|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|--------------|-----------------------|
| Aerohive | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Android | No Known Official Response | Android 6.0 and above affected (Android uses wpa_supplicant and therefore is affected). | 2017-10-16 | 2017-10-16 |  |
| Apple | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Arch Linux | [wpa_supplicant](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/wpa_supplicant&id=9c1bda00a846ff3b60e7c4b4f60b28ff4a8f7768), [hostapd](https://git.archlinux.org/svntogit/community.git/commit/trunk?h=packages/hostapd&id=d31735a09b4c25eaa69fb13b1031910ca3c29ee5) | N/A | 2017-10-16 | 2017-10-16 |  |
| Arduino | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Asus | No Known Official Response | According to https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/ at the time of this commit no statement from Asus | 2017-10-17 | 2017-10-17 |  |
| Broadcom | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Buffalo / MELCO | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Canon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Cisco | https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20171016-wpa | Multiple Cisco wireless products are affected by these vulnerabilities. | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Comcast | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| CZ.NIC Turris | https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/8 | via @spike411: CZ.NIC Turris team is testing a fix (backported from hostapd upstream):https://gitlab.labs.nic.cz/turris/openwrt/commit/a60970f33f65bfb1d531ce822bfd28ee049a702f | 2017-10-16 | 2017-10-16 |  |
| D-Link | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Debian / Ubuntu | http://seclists.org/bugtraq/2017/Oct/25 | * Add patches to fix WPA protocol vulnerabilities (CVE-2017-13077,    CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081,    CVE-2017-13082, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088):    - hostapd: Avoid key reinstallation in FT handshake    - Prevent reinstallation of an already in-use group key    - Extend protection of GTK/IGTK reinstallation of WNM-Sleep Mode cases    - Fix PTK rekeying to generate a new ANonce    - TDLS: Reject TPK-TK reconfiguration    - WNM: Ignore WNM-Sleep Mode Response if WNM-Sleep Mode has not been used    - WNM: Ignore WNM-Sleep Mode Response without pending request    - FT: Do not allow multiple Reassociation Response frames    - TDLS: Ignore incoming TDLS Setup Response retries | 2017-10-16 | 2017-10-16 |  |
| Espressif Systems | http://espressif.com/en/media_overview/news/espressif-releases-patches-wifi-vulnerabilities-cert-vu228519 | Espressif released patches for the WiFi vulnerabilities in their products including ESP-IDF, ESP8266 RTOS and ESP8266 NON-OS. Arduino ESP32 will be updated shortly. | 2017-10-16 | 2017-10-16 | 22 Sep 2017 |
| Fedora | https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc27 | Status: Fixed Release: Pending (* Manual installation is possible) | 2017-10-17 | 2017-10-17 |  |
| FortiNet | http://docs.fortinet.com/uploaded/files/3961/fortiap-v5.6.1-release-notes.pdf | FortiAP 5.6.1 is no longer vulnerable to the following CVE Reference:...CVE-2017-13077CVE-2017-13078CVE-2017-13079CVE-2017-13080CVE-2017-13081CVE-2017-13082 | 2017-10-16 | 2017-10-16 |  |
| FreeBSD Project | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Google | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Honeywell | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| HPE Aruba | http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007.txt | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Huawei | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Intel Corporation | https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00101&languageid=en-fr | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| IO DATA | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Juniper Networks | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| KPN | https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol | No Fix as of yet | 2017-10-17 | 2017-10-17 |  |
| Linksys | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Linux | Patches: https://w1.fi/security/2017-1/ | wpa_supplicant version 2.4 and above is affected. Linux's wpa_supplicant v2.6 is also vulnerable to the installation of an all-zero encryption key in the 4-way handshake. | 2017-10-16 | 2017-10-16 |  |
| Logitech | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| MediaTek | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Meraki | https://documentation.meraki.com/zGeneral_Administration/Support/802.11r_Vulnerability_(CVE%3A_2017-13082)_FAQ | Fixed for Cisco Meraki in 24.11 and 25.7 | 2017-10-16 | 2017-10-16 |  |
| Microchip Technology | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Microsoft | [Windows Related](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-13080) | When clicking the link, accept the EULA then click the link again | 2017-10-16 | 2017-10-16 |  |
| Mikrotik | https://forum.mikrotik.com/viewtopic.php?f=21&t=126695 | We released fixed versions last week, so if you upgrade your devices routinely, no further action is required. | 2017-10-16 | 2017-10-16 |  |
| NEC | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Netgear | https://kb.netgear.com/000049498/Security-Advisory-for-WPA-2-Vulnerabilities-PSV-2017-2826-PSV-2017-2836-PSV-2017-2837 | N/A | 2017-10-16 | 2017-10-16 |  |
| Nikon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nintendo | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| OpenBSD | https://marc.info/?l=openbsd-announce&m=150410604407872&w=2 | Errata patches for the wireless stack have been released for OpenBSD 6.1 and 6.0. State transition errors could cause reinstallation of old WPA keys. Binary updates for the amd64 and i386 platforms are available via the syspatch utility. Source code patches can be found on the respective errata pages. As this affects the kernel, a reboot will be needed after patching. | 2017-10-16 | 2017-10-16 |  |
| Pakedge | No Known Official Response | Via @spike411 "They have acknowledged they have received my enquiry but don’t have any info about the state of this vulnerability in their products." | 2017-10-16 | 2017-10-16 |  |
| Qualcomm Atheros | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Red Hat, Inc. | This issue affects the versions of wpa_supplicant as shipped with Red Hat Enterprise Linux 6 and 7. https://access.redhat.com/security/cve/cve-2017-13087 | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Ruckus Wireless | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Samsung Mobile | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Sharp | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Sony | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Sophos AP | https://community.sophos.com/kb/en-us/127658 | N/A | 2017-10-17 | 2017-10-17 |  |
| SUSE / openSUSE | https://bugzilla.suse.com/show_bug.cgi?id=1063479 |  | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Toshiba Commerce Solutions | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 15 Sep 2017 |
| Toshiba Electronic Devices & Storage Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Toshiba Memory Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| TP-Link | No Known Official Response | TP-Link suggested to follow their official website for news: http://www.tp-link.com/us/news.html | 2017-10-17 | 2017-10-17 |  |
| Ubiquiti Networks | https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365 | Ubiquiti has released 3.9.3.7537 in beta to mitigate these vulnerabilities in UniFi APs that have a client mode. mFi devices are likely vulnerable and [no statement or patch](https://community.ubnt.com/t5/mFi/KRACK-WPA2-broken-Plans-for-mFi-hardware-fixes/m-p/2099826) has been released. | 2017-10-16 | 2017-10-16 |  |
| WatchGuard | https://www.watchguard.com/wgrd-blog/wpa-and-wpa2-vulnerabilities-update | Sunday, October 15, 2017:,AP120, 320, 322, 420:,Release 8.3.0-657, Cloud mode only . Monday, October 30, 2017: AP300: Release 2.0.0.9 ,AP100, 102, 200: Release 1.2.9.14, AP120, 320, 322, 420:,Release 8.3.0-657, Non-Cloud (GWC mode) | 2017-10-17 | 2017-10-17 |  |
| WiFi Alliance | https://www.wi-fi.org/security-update-october-2017 | Users should refer to their Wi-Fi device vendor’s website or security advisories to determine if their device has been affected and has an update available. As always, Wi-Fi users should ensure they have installed the latest recommended updates from device manufacturers. | 2017-10-16 | 2017-10-16 |  |
| Xfinity | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Xirrus | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Yamaha | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| ZTE | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| ZyXEL | http://www.zyxel.com/support/announcement_wpa2_key_management.shtml | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |