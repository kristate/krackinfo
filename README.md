# KRACK: (K)ey (R)einstallation (A)tta(ck)

From the KRACK <a href="https://www.krackattacks.com/">website</a>:
> In a key reinstallation attack, the adversary tricks a victim into reinstalling an already-in-use key. This is achieved by manipulating and replaying cryptographic handshake messages. When the victim reinstalls the key, associated parameters such as the incremental transmit packet number (i.e. nonce) and receive packet number (i.e. replay counter) are reset to their initial value. Essentially, to guarantee security, a key should only be installed and used once. Unfortunately, we found this is not guaranteed by the WPA2 protocol. By manipulating cryptographic handshakes, we can abuse this weakness in practice.

***Unless a known patch has been applied, assume that all WPA2 enabled Wi-fi devices are vulnerable.***

## The Good
* Should a vendor take responsibility, devices are for the most part updatable.

## The Bad
* Many devices do not have an easy way to apply updates.
* A huge burden is placed on the consumer to keep their devices up to date
  * It may not be easy to search for all updates to all devices.
* The attack is works for both clients and access points
  * Updating an access point does not keep clients protected!

## The Ugly
* Attacks against Android 6.0+ devices are very easy to accomplish.
  * It is advised to disable Wi-Fi and only use 4G for the time being.
* Updates may never come for many IoT devices.

### Attacks that can be made (できること)
* Adversary can decrypt arbitrary packets.
  * This allows an adversary to obtain the TCP sequence numbers of a connection, and <a href="https://en.wikipedia.org/wiki/TCP_sequence_prediction_attack">hijack TCP connections</a>.
* Adversary can replay broadcast and multicast frames.
* Adversary can both decrypt and inject arbitrary packets. *(TKIP or GCMP ONLY)*
* Adversary can force the client into using a predictable all-zero encryption key. *(ANDROID 6.0+ and LINUX)*


### Attacks that cannot be made (できないこと)
* Adversary can not recover WPA password.
* Adversary can not inject packets. *(AES-CCMP ONLY)*


### Related Reading
* https://blog.cryptographyengineering.com/2017/10/16/falling-through-the-kracks/
* https://www.reddit.com/r/KRaCK/comments/76pjf8/krack_megathread_check_back_often_for_updated/

## Vendor Patch Matrix (non-complete)

| Vendor | Patch Available | In Development | Not Directly Affected |
|--------|-----------------|----------------|-----------------------|
| Arch Linux | X |  |  |
| Arista |  |  | X |
| Aruba | X |  |  |
| Cisco |  | X |  |
| DD-WRT | X |  |  |
| Debian | X |  |  |
| Extreme Networks |  | X |  |
| Fedora | X |  |  |
| FreeBSD |  | X |  |
| Lenovo |  |  | X |
| LineageOS |  | X |  |
| LXDE |  | X |  |
| Meraki | X |  |  |
| MikroTik | X |  |  |
| Synology |  | X |  |
| Turris Omnia |  | X |  |
| Ubiquiti | X |  |  |
| Ubuntu | [X](https://usn.ubuntu.com/usn/usn-3455-1/) |  |  |
| UniFi | X |  |  |
| VMware |  |  | X |
| Watchguard Cloud | X |  |  |
| Watchguard |  | X | |
| Windows 10 | X |  |  |
| WPA_supplicant | X |  |  |

## Vendor Response (complete)

| Vendor | Official Response | Comment | Last Checked | Last Updated | Date Notified by CERT |
|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|--------------|-----------------------|
| 3com Inc | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Actiontec | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Aerohive | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Alcatel-Lucent | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Amazon | No Known Official Response | "We are in the process of reviewing which of our devices may contain this vulnerability and will be issuing patches where needed." | 2017-10-17 | 2017-10-17 |  |
| Android | No Known Official Response | Android 6.0 and above affected (Android uses wpa_supplicant and therefore is affected). | 2017-10-16 | 2017-10-16 |  |
| Apple | No Known Official Response; See comment for unofficial response | Via twitter : "Apple has confirmed to me that #wpa2 #KRACK exploit has already been patched in iOS, tvOS, watchOS, macOS betas." https://twitter.com/reneritchie/status/919988216501030914 | 2017-10-17 | 2017-10-17 |  |
| Arch Linux | [wpa_supplicant](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/wpa_supplicant&id=9c1bda00a846ff3b60e7c4b4f60b28ff4a8f7768), [hostapd](https://git.archlinux.org/svntogit/community.git/commit/trunk?h=packages/hostapd&id=d31735a09b4c25eaa69fb13b1031910ca3c29ee5) | N/A | 2017-10-16 | 2017-10-16 |  |
| Arduino | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Asus | No Known Official Response | According to https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/ at the time of this commit no statement from Asus | 2017-10-17 | 2017-10-17 |  |
| Barracuda Networks | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Belkin, Linksys, and Wemo | No Known Official Response | "Belkin Linksys, and Wemo are aware of the WPA vulnerability.  Our security teams are verifying details and we will advise accordingly.  Also know that we are committed to putting the customer first and are planning to post instructions on our security advisory page on what customers can do to update their products, if and when required." | 2017-10-16 | 2017-10-16 |  |
| Broadcom | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Buffalo / MELCO | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Canon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| CentOS | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Cisco | https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20171016-wpa | Multiple Cisco wireless products are affected by these vulnerabilities. | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Comcast | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| CZ.NIC Turris | https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/8 | via @spike411: CZ.NIC Turris team is testing a fix (backported from hostapd upstream):https://gitlab.labs.nic.cz/turris/openwrt/commit/a60970f33f65bfb1d531ce822bfd28ee049a702f | 2017-10-16 | 2017-10-16 |  |
| D-Link | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| DD-WRT | http://svn.dd-wrt.com/changeset/33525 | N/A | 2017-10-17 | 2017-10-17 |  |
| Debian | https://www.debian.org/security/2017/dsa-3999 | * Add patches to fix WPA protocol vulnerabilities (CVE-2017-13077,    CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081,    CVE-2017-13082, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088):    - hostapd: Avoid key reinstallation in FT handshake    - Prevent reinstallation of an already in-use group key    - Extend protection of GTK/IGTK reinstallation of WNM-Sleep Mode cases    - Fix PTK rekeying to generate a new ANonce    - TDLS: Reject TPK-TK reconfiguration    - WNM: Ignore WNM-Sleep Mode Response if WNM-Sleep Mode has not been used    - WNM: Ignore WNM-Sleep Mode Response without pending request    - FT: Do not allow multiple Reassociation Response frames    - TDLS: Ignore incoming TDLS Setup Response retries | 2017-10-16 | 2017-10-16 |  |
| Dell | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Denon | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Draytek | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Edimax | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| EMC Corporation | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Espressif Systems | http://espressif.com/en/media_overview/news/espressif-releases-patches-wifi-vulnerabilities-cert-vu228519 | Espressif released patches for the WiFi vulnerabilities in their products including ESP-IDF, ESP8266 RTOS and ESP8266 NON-OS. Arduino ESP32 will be updated shortly. | 2017-10-16 | 2017-10-16 | 22 Sep 2017 |
| Extreme Networks | https://extremeportal.force.com/ExtrArticleDetail?n=000018005 | N/A | 2017-10-16 | 2017-10-16 | 2017-08-28 |
| F5 Networks | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Fedora | https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc27 | Status: Fixed Release: Pending (* Manual installation is possible) | 2017-10-17 | 2017-10-17 |  |
| FortiNet | http://docs.fortinet.com/uploaded/files/3961/fortiap-v5.6.1-release-notes.pdf | FortiAP 5.6.1 is no longer vulnerable to the following CVE Reference:...CVE-2017-13077CVE-2017-13078CVE-2017-13079CVE-2017-13080CVE-2017-13081CVE-2017-13082 | 2017-10-16 | 2017-10-16 |  |
| Foundry Brocade | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| FreeBSD Project | https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001805.html | `wpa_supplicant` 2.5 in base. Recommended to use wired connection or install the `security/wpa_supplicant` port or package until base is patched. | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Google | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Hewlett Packard Enterprise | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Honeywell | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| HPE Aruba | http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007.txt | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Huawei | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| IBM | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Intel Corporation | https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00101&languageid=en-fr | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| IO DATA | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Juniper Networks | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| KPN | https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol | No Fix as of yet | 2017-10-17 | 2017-10-17 |  |
| Kyocera Communications | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| LEDE | http://lists.infradead.org/pipermail/lede-dev/2017-October/009349.html | Fixed snapshots for master available. 17.01.4 pending release. | 2017-10-17 | 2017-10-17 | |
| LineageOS | https://review.lineageos.org/#/q/topic:krack-n | N/A | 2017-10-17 | 2017-10-17 |  |
| Linux | Patches: https://w1.fi/security/2017-1/ | wpa_supplicant version 2.4 and above is affected. Linux's wpa_supplicant v2.6 is also vulnerable to the installation of an all-zero encryption key in the 4-way handshake. | 2017-10-16 | 2017-10-16 |  |
| Logitech | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Marantz | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Marvell Semiconductor | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| MediaTek | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Meraki | https://documentation.meraki.com/zGeneral_Administration/Support/802.11r_Vulnerability_(CVE%3A_2017-13082)_FAQ | Fixed for Cisco Meraki in 24.11 and 25.7 | 2017-10-16 | 2017-10-16 |  |
| Microchip Technology | http://www.microchip.com/design-centers/wireless-connectivity/embedded-wi-fi/wpa2-protocol-vulnerability | N/A | 2017-10-17 | 2017-10-17 | 28 Aug 2017 |
| Microsoft | [Windows Related](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-13080) | When clicking the link, accept the EULA then click the link again | 2017-10-16 | 2017-10-16 |  |
| Mikrotik | https://forum.mikrotik.com/viewtopic.php?f=21&t=126695 | We released fixed versions last week, so if you upgrade your devices routinely, no further action is required. | 2017-10-16 | 2017-10-16 |  |
| NEC | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nest Labs | No Known Official Response | Doggy answer from support: "No known attacks can be carried out against our hardware" | 2017-10-17 | 2017-10-17 |  |
| Netgear | https://kb.netgear.com/000049498/Security-Advisory-for-WPA-2-Vulnerabilities-PSV-2017-2826-PSV-2017-2836-PSV-2017-2837 | N/A | 2017-10-16 | 2017-10-16 |  |
| Nikon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nintendo | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Onkyo | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Open-Mesh / CloudTrax | https://help.cloudtrax.com/hc/en-us/articles/115001567804-KRACK-Bulletin | An update is expected to be delivered to all of those that use automatic updates by the end over October 17th. | 2017-10-17 | 2017-10-17 |  |
| OpenBSD | https://marc.info/?l=openbsd-announce&m=150410604407872&w=2 | Errata patches for the wireless stack have been released for OpenBSD 6.1 and 6.0. State transition errors could cause reinstallation of old WPA keys. Binary updates for the amd64 and i386 platforms are available via the syspatch utility. Source code patches can be found on the respective errata pages. As this affects the kernel, a reboot will be needed after patching. | 2017-10-16 | 2017-10-16 |  |
| Pakedge | No Known Official Response | Via @spike411 "They have acknowledged they have received my enquiry but don’t have any info about the state of this vulnerability in their products." | 2017-10-16 | 2017-10-16 |  |
| pfSense | https://redmine.pfsense.org/issues/7951 | N/A | 2017-10-17 | 2017-10-17 |  |
| Pioneer | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Qualcomm Atheros | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Red Hat, Inc. | This issue affects the versions of wpa_supplicant as shipped with Red Hat Enterprise Linux 6 and 7. https://access.redhat.com/security/cve/cve-2017-13087 | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Ring | No Known Official Response | Per support "They promise to update public shortly, actively working with developers." | 2017-10-17 | 2017-10-17 |  |
| Ruckus Wireless | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Samsung Mobile | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Sharp | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Sonicwall | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Sony | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Sophos AP | https://community.sophos.com/kb/en-us/127658 | N/A | 2017-10-17 | 2017-10-17 |  |
| SUSE / openSUSE | https://bugzilla.suse.com/show_bug.cgi?id=1063479 |  | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Synology | https://www.synology.com/en-us/support/security/Synology_SA_17_60_KRACK | Synology DiskStation Manager (DSM) with attached WiFi dongle and Synology Router Manager (SRM) are vulnerable to Krack. According to Synology, updates for affected products will be released soon. | 2017-10-17 | 2017-10-17 |  |
| Toshiba Commerce Solutions | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 15 Sep 2017 |
| Toshiba Electronic Devices & Storage Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Toshiba Memory Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| TP-Link | No Known Official Response | TP-Link suggested to follow their official website for news: http://www.tp-link.com/us/news.html | 2017-10-17 | 2017-10-17 |  |
| Turris Omnia | https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/9 | N/A | 2017-10-17 | 2017-10-17 |  |
| Ubiquiti Networks | https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365 | Ubiquiti has released 3.9.3.7537 in beta to mitigate these vulnerabilities in UniFi APs that have a client mode. mFi devices are likely vulnerable and [no statement or patch](https://community.ubnt.com/t5/mFi/KRACK-WPA2-broken-Plans-for-mFi-hardware-fixes/m-p/2099826) has been released. | 2017-10-16 | 2017-10-16 |  |
| Ubuntu | https://usn.ubuntu.com/usn/usn-3455-1/ | Updates are available for wpasupplicant and hostapd in Ubuntu 17.04, Ubuntu 16.04 LTS, and Ubuntu 14.04 LTS. | 2017-10-16 | 2017-10-16 |  |
| WatchGuard | https://www.watchguard.com/wgrd-blog/wpa-and-wpa2-vulnerabilities-update | Sunday, October 15, 2017:,AP120, 320, 322, 420:,Release 8.3.0-657, Cloud mode only . Monday, October 30, 2017: AP300: Release 2.0.0.9 ,AP100, 102, 200: Release 1.2.9.14, AP120, 320, 322, 420:,Release 8.3.0-657, Non-Cloud (GWC mode) | 2017-10-17 | 2017-10-17 |  |
| WiFi Alliance | https://www.wi-fi.org/security-update-october-2017 | Users should refer to their Wi-Fi device vendor’s website or security advisories to determine if their device has been affected and has an update available. As always, Wi-Fi users should ensure they have installed the latest recommended updates from device manufacturers. | 2017-10-16 | 2017-10-16 |  |
| Xfinity | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Xirrus | https://www.xirrus.com/vulnerability-statements/ | As soon as the patch is released, it will be made available through the Xirrus Support Community. | 2017-10-17 | 2017-10-17 |  |
| Yamaha | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Yi (Xiaoyi) | No Known Official Response | "Waiting on a reply" | 2017-10-17 | 2017-10-17 |  |
| ZTE | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| ZyXEL | http://www.zyxel.com/support/announcement_wpa2_key_management.shtml | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
