# KRACK: (K)ey (R)einstallation (A)tta(ck)

From the KRACK <a href="https://www.krackattacks.com/">website</a>:
> In a key reinstallation attack, the adversary tricks a victim into reinstalling an already-in-use key. This is achieved by manipulating and replaying cryptographic handshake messages. When the victim reinstalls the key, associated parameters such as the incremental transmit packet number (i.e. nonce) and receive packet number (i.e. replay counter) are reset to their initial value. Essentially, to guarantee security, a key should only be installed and used once. Unfortunately, we found this is not guaranteed by the WPA2 protocol. By manipulating cryptographic handshakes, we can abuse this weakness in practice.

***Unless a known patch has been applied, assume that all WPA2 enabled Wi-fi devices are vulnerable.***

## Go Directly to [Vendor Response Matrix](#vendor-response-complete)
## For Android devices please check the [Android Response Matrix](ANDROID.md)
## 日本人の皆さまへ： [こちらをご覧ください](/krackinfo_JA-JP.md)(日本語)

## The Good
* Should a vendor take responsibility, devices are for the most part updatable.

## The Bad
* Many devices do not have an easy way to apply updates.
* A huge burden is placed on the consumer to keep their devices up to date
  * It may not be easy to search for all updates to all devices.
* The attack works for both clients and access points
  * Updating an access point does not keep clients protected!

## The Ugly
* Attacks against Android 6.0+ devices are very easy to accomplish.
  * It is advised to disable Wi-Fi and only use 4G for the time being.
* Updates may never come for many IoT devices.

### Attacks that can be made
* Adversary can decrypt arbitrary packets.
  * This allows an adversary to obtain the TCP sequence numbers of a connection, and <a href="https://en.wikipedia.org/wiki/TCP_sequence_prediction_attack">hijack TCP connections</a>.
* Adversary can replay broadcast and multicast frames.
* Adversary can both decrypt and inject arbitrary packets. *(TKIP or GCMP ONLY)*
* Adversary can force the client into using a predictable all-zero encryption key. *(ANDROID 6.0+ and LINUX)*


### Attacks that cannot be made
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
| Aruba | [X](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007_FAQ_Rev-1.pdf) |  |  |
| Asus |  | [X](https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/) | X |
| CentOS | X |  |  |
| Cisco |  | X |  |
| DD-WRT | X |  |  |
| Debian | X |  |  |
| Endian  | X |  |  |
| Extreme Networks |  | X |  |
| Fedora | X |  |  |
| FreeBSD | [X](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001806.html) |  |  |
| Lenovo |  |  | X |
| LineageOS | [X](https://mobile.twitter.com/LineageAndroid/status/920143977256382464) |  |  |
| LXDE |  | X |  |
| Meraki | X |  |  |
| MikroTik | X |  |  |
| Mojo Networks | X |  |  |
| Ruckus |  | X |  |
| Synology | [X](https://www.synology.com/en-us/releaseNote/DS414) |  |  |
| Turris Omnia |[X](https://forum.turris.cz/t/turris-os-3-8-4-is-out-with-krack-fix/5391)|  |  |
| Ubiquiti | [X](https://community.ubnt.com/t5/UniFi-Updates-Blog/bg-p/Blog_UniFi) |  |  |
| Ubuntu | [X](https://usn.ubuntu.com/usn/usn-3455-1/) |  |  |
| UniFi | [X](https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365) |  |  |
| VMware |  |  | X |
| Watchguard Cloud | X |  |  |
| Watchguard |  | X | |
| Windows 10 | X |  |  |
| WPA_supplicant | X |  |  |

## Vendor Response (complete)

| Vendor | Official Response | Comment | Last Checked | Last Updated | Date Notified by CERT |
|--------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|--------------|-----------------------|
| 3com Inc | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Actiontec | [Link](https://actiontecsupport.zendesk.com/hc/en-us/articles/115005205283-KRACK-vulnerability) | N/A | 2017-10-18 | 2017-10-18 |  |
| Aerohive | [Link](https://boundless.aerohive.com/technology/Aerohive-Response-To-KRACK.html) | N/A | 2017-10-17 | 2017-10-17 |  |
| Alcatel-Lucent | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Amazon | No Known Official Response | "We are in the process of reviewing which of our devices may contain this vulnerability and will be issuing patches where needed." | 2017-10-17 | 2017-10-17 |  |
| Android | No Known Official Response | Android 6.0 and above affected (Android uses wpa_supplicant and therefore is affected). | 2017-10-16 | 2017-10-16 |  |
| Apple | No Known Official Response; See comment for unofficial response | Via twitter : "Apple has confirmed to me that #wpa2 #KRACK exploit has already been patched in iOS, tvOS, watchOS, macOS betas." [LINK](https://twitter.com/reneritchie/status/919988216501030914) | 2017-10-17 | 2017-10-17 |  |
| Arch Linux | [wpa_supplicant](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/wpa_supplicant&id=9c1bda00a846ff3b60e7c4b4f60b28ff4a8f7768), [hostapd](https://git.archlinux.org/svntogit/community.git/commit/trunk?h=packages/hostapd&id=d31735a09b4c25eaa69fb13b1031910ca3c29ee5) | N/A | 2017-10-16 | 2017-10-16 |  |
| Arduino | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Asus | [LINK](https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/) | Additionally, an email response from "security@asus.com" says that they are "co-working with chipset vendors for solutions and will release patched firmware for affected routers soon. If your router is RT-N12 D1, RT-N66U, RT-AC66U, RT-AC68U, RT-AC3200, RT-AC88U, RT-AC3100, RT-AC5300 or GT-AC5300 then your router is not affected by the WPA2 vulnerability in router and AP mode." | 2017-10-17 | 2017-10-18 |  |
| AVM (FRITZ!Box)  | [LINK](https://en.avm.de/news/short-notes/2017/wpa2-flaw-fritzbox-on-broadband-connections-are-secure/) | WPA2 flaw – FRITZ!Box on broadband connections are secure. AVM will provide updates for its wireless repeaters. | 2017-10-18 | 2017-10-18 |  |
| Barracuda Networks | [LINK](https://community.barracudanetworks.com/forum/index.php?/topic/23525-security-advisories/page-2#entry84537) | Our investigations indicate that currently only Barracuda NextGen Firewall Wi-Fi Models used under Wi-Fi Client mode are affected. | 2017-10-17 | 2017-10-17 |  |
| Belkin, Linksys, and Wemo | [LINK(Linksys)](https://www.linksys.com/us/support-article?articleNum=246427) | "Belkin Linksys, and Wemo are aware of the WPA vulnerability.  Our security teams are verifying details and we will advise accordingly.  Also know that we are committed to putting the customer first and are planning to post instructions on our security advisory page on what customers can do to update their products, if and when required." | 2017-10-17 | 2017-10-17 |  |
| Broadcom / Cypress | [LINK](https://community.cypress.com/docs/DOC-13871) (Cypress community login required) | WICED Studio, `wpa_supplicant`, and linux releases in late October will address the relevant CVEs. | 2017-10-18 | 2017-10-18 |  |
| Buffalo / MELCO | [LINK(JA)](http://buffalo.jp/support_s/t20171017.html) | N/A | 2017-10-18 | 2017-10-18 |  |
| Brother | No Known Official Response | N/A | 2017-10-19 | 2017-10-19 |  |
| Canon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| CentOS | [CentOS 6](https://lists.centos.org/pipermail/centos-announce/2017-October/022570.html), [CentOS 7](https://lists.centos.org/pipermail/centos-announce/2017-October/022569.html) | From upstream Red Hat Security Advisories [RHSA-2017:2911](https://access.redhat.com/errata/RHSA-2017:2911), and [RHSA-2017:2907](https://access.redhat.com/errata/RHSA-2017:2907) Arch: Centos6 [i386](http://mirror.centos.org/centos-6/6/updates/i386/Packages/), [x86_64](http://mirror.centos.org/centos-6/6/updates/x86_64/Packages/); Centos7 [x86_64](http://mirror.centos.org/centos-7/7.4.1708/updates/x86_64/Packages/), [ARM](http://mirror.centos.org/altarch/7/updates/armhfp/Packages/) (Raspberry PI), [ppc64](http://mirror.centos.org/altarch/7/updates/ppc64/Packages/), [ppc64le](http://mirror.centos.org/altarch/7/updates/ppc64le/Packages/),  | 2017-10-18 | 2017-10-18 |  |
| Cisco | [LINK](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20171016-wpa) | Multiple Cisco wireless products are affected by these vulnerabilities. | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Comcast | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| ConnMann | No Known Official Response | Connman has not released any information or updates yet. [LINK](https://01.org/connman/blogs) | 2017-10-17 | 2017-10-20 |  |
| CZ.NIC Turris | [LINK](https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/8) | via @spike411: CZ.NIC Turris team is testing a fix (backported from hostapd upstream): [LINK](https://gitlab.labs.nic.cz/turris/openwrt/commit/a60970f33f65bfb1d531ce822bfd28ee049a702f) | 2017-10-16 | 2017-10-16 |  |
| D-Link | [LINK](http://supportannouncement.us.dlink.com/announcement/publication.aspx?name=SAP10075) | N/A | 2017-10-17 | 2017-10-17 |  |
| DD-WRT | [LINK](http://svn.dd-wrt.com/changeset/33525) | N/A | 2017-10-17 | 2017-10-17 |  |
| Debian | [LINK](https://www.debian.org/security/2017/dsa-3999) | * Add patches to fix WPA protocol vulnerabilities (CVE-2017-13077,    CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081,    CVE-2017-13082, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088):    - hostapd: Avoid key reinstallation in FT handshake    - Prevent reinstallation of an already in-use group key    - Extend protection of GTK/IGTK reinstallation of WNM-Sleep Mode cases    - Fix PTK rekeying to generate a new ANonce    - TDLS: Reject TPK-TK reconfiguration    - WNM: Ignore WNM-Sleep Mode Response if WNM-Sleep Mode has not been used    - WNM: Ignore WNM-Sleep Mode Response without pending request    - FT: Do not allow multiple Reassociation Response frames    - TDLS: Ignore incoming TDLS Setup Response retries | 2017-10-16 | 2017-10-16 |  |
| Dell | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Denon | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Devolo | No Known Official Response | They are currently reviewing the attack scenario for their products according to [this tweet](https://twitter.com/devoloAG/status/920253378873233408) | 2017-10-18 | 2017-10-18 |  |
| DrayTek | [LINK](http://www.draytek.co.uk/information/our-technology/wpa2-krack-vulnerability) | DrayTek are investigating solutions for this and plan to issue appropriate updates (firmware) as soon as possible. We will update this page in due course. | 2017-10-17 | 2017-10-17 |  |
| ecobee | No Known Official Response | Twitter response [1](https://twitter.com/ecobee/status/920316685193707521) and [2](https://twitter.com/ecobee/status/920316741334552576): "ecobee is aware of the industry-wide vulnerability in WPA2 referred to as KRACK.   The security of our customers is very important to us and we have confirmed that ecobee device security is not impacted by this issue." Likely this means ecobee considers underlying https / ssl to be secure despite KRACK | 2017-10-17 | 2017-10-17 |  |
| Edimax | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| EMC Corporation | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Endian | [LINK](https://help.endian.com/hc/en-us/articles/115013641427-WPA-and-WPA2-Vulnerability-KRACK-Key-Reinstallation-Attacks-Update) | Community version is not affected. Fixed on Enterprise 5.0 | 2017-10-18 | 2017-10-18 |  |
| EnGenius | [LINK](https://helpcenter.engeniustech.com/hc/en-us/articles/115002197872-EnGenius-Advisory-on-the-WPA2-KRACK-vulnerability) | "EnGenius software developers are currently working on security patches and will issue firmware releases as soon as possible." | 2017-10-18 | 2017-10-18 |  |
| Espressif Systems | [LINK](http://espressif.com/en/media_overview/news/espressif-releases-patches-wifi-vulnerabilities-cert-vu228519) | Espressif released patches for the WiFi vulnerabilities in their products including ESP-IDF, ESP8266 RTOS and ESP8266 NON-OS. Arduino ESP32 will be updated shortly. | 2017-10-16 | 2017-10-16 | 22 Sep 2017 |
| Extreme Networks | [LINK](https://extremeportal.force.com/ExtrArticleDetail?n=000018005) | N/A | 2017-10-16 | 2017-10-16 | 2017-08-28 |
| F5 Networks | [LINK](https://support.f5.com/csp/article/K23642330) | There is no impact; F5 products are not affected by this vulnerability. | 2017-10-19 | 2017-10-19 |  |
| Fedora | Fedora [26](https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc26) / [27 (beta)](https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc27) | Status: Fixed Release: Stable (* Manual installation is possible) Arch: x86_64 and ARM (Raspberry PI) | 2017-10-17 | 2017-10-19 |  |
| FortiNet | [LINK](http://www.fortiguard.com/psirt/FG-IR-17-196) | FortiAP 5.6.1 has been patched. All other patches are upcoming. | 2017-10-16 | 2017-10-18 |  |
| Foundry Brocade | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| FreeBSD Project | [Response](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001805.html), [patch](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001806.html) | Binary and source updates to base system available. Alternatively one can install the `security/wpa_supplicant` port or package in lieu of the same in base. | 2017-10-17 | 2017-10-17 | (?) |
| Google | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Hewlett Packard Enterprise | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Honeywell | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| HPE Aruba | [Patch Info](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007.txt) - [FAQ](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007_FAQ_Rev-1.pdf) | N/A | 2017-10-17 | 2017-10-17 | 28 Aug 2017 |
| Huawei | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| IBM | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Icotera | Icotera products are not affected [LINK](https://icotera.zendesk.com/hc/en-us/articles/115002195451-WPA2-Key-re-installation-attacks-KRACK-on-Icotera-products-) | The investigation concluded that none of current Icotera products is affected by the described vulnerability, as it does not apply to a device running Access Point mode only | 2017-10-19 | 2017-10-19 |  |
| Intel Corporation | [LINK](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00101&languageid=en-fr) | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| I-O DATA | [LINK(JA)](http://www.iodata.jp/support/information/2017/wpa2/) | N/A | 2017-10-18 | 2017-10-18 |  |
| IPFire | [LINK](https://planet.ipfire.org/post/krack-attack-patches-are-on-their-way) | Update: packages for all architectures are now available | 2017-10-19 | 2017-10-19 |  |
| iRobot (Roomba) | No Known Official Response | Chat support: "So far as we can tell, we haven't been impacted. So that's good news lol." [IMG](https://user-images.githubusercontent.com/271922/31730055-05bd1658-b431-11e7-84fc-0b5ef663905b.png) | 2017-10-17 | 2017-10-17 |  |
| Jolla | [LINK](https://together.jolla.com/question/170073/krack-attacks-wpa2-is-not-secure-anymore/?answer=170198#post-id-170198) | N/A | 2017-10-17 | 2017-10-17 |  |
| Juniper Networks | [LINK](https://kb.juniper.net/InfoCenter/index?page=content&id=JSA10827) | Patches for WLAN available; patches for SRX and SSG outstanding | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| KPN | [LINK](https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol) | KPN routers to be found safe. See update 17th [LINK](https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol) | 2017-10-17 | 2017-10-20 |  |
| Kyocera Communications | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| LEDE | [LINK](https://lede-project.org/releases/17.01/notes-17.01.4) | Released fix in version 17.01.4. | 2017-10-18 | 2017-10-18 | |
| LineageOS | [LINK](https://review.lineageos.org/#/q/topic:krack-n) | "All official 14.1 builds built after this tweet have been patched for KRACK.":[LINK](https://twitter.com/LineageAndroid/status/920143977256382464) | 2017-10-17 | 2017-10-17 |  |
| Linux | Patches: [LINK](https://w1.fi/security/2017-1/) | wpa_supplicant version 2.4 and above is affected. Linux's wpa_supplicant v2.6 is also vulnerable to the installation of an all-zero encryption key in the 4-way handshake. | 2017-10-16 | 2017-10-16 |  |
| Logitech | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Luxul | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Marantz | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Marvell Semiconductor | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| MediaTek | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Meraki | [LINK](https://documentation.meraki.com/zGeneral_Administration/Support/802.11r_Vulnerability_(CVE%3A_2017-13082)_FAQ) | Fixed for Cisco Meraki in 24.11 and 25.7 | 2017-10-16 | 2017-10-16 |  |
| Microchip Technology | [LINK](http://www.microchip.com/design-centers/wireless-connectivity/embedded-wi-fi/wpa2-protocol-vulnerability) | N/A | 2017-10-17 | 2017-10-17 | 28 Aug 2017 |
| Microsoft | [Windows Related](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-13080) | When clicking the link, accept the EULA then click the link again | 2017-10-16 | 2017-10-16 |  |
| Mikrotik | [LINK](https://forum.mikrotik.com/viewtopic.php?f=21&t=126695) | We released fixed versions last week, so if you upgrade your devices routinely, no further action is required. | 2017-10-16 | 2017-10-16 |  |
| Mojo Networks | [LINK](https://www.mojonetworks.com/wpa2-vulnerability) | Update to cloud management platform completed. In order to mitigate client-side vulnerabilities, Mojo recommends upgrading AP software to version 8.5, and enabling MAC Spoofing and Man-in-the-middle attack prevention with built-in WIPs. | 2017-10-17 | 2017-10-17 |  |
| NEC | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nest Labs | No Known Official Response | Nest Tweeted: "We plan to roll out patches to our products in the coming weeks.  These won't require any action on the part of the user." | 2017-10-17 | 2017-10-17 |  |
| Netgear | [LINK](https://kb.netgear.com/000049498/Security-Advisory-for-WPA-2-Vulnerabilities-PSV-2017-2826-PSV-2017-2836-PSV-2017-2837) | N/A | 2017-10-16 | 2017-10-16 |  |
| Nikon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nintendo | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| OmniROM | [LINK](https://blog.omnirom.org/development/2017/10/17/omni-builds-updated-krack/) | "all official OmniROM N builds have the fix included." | 2017-10-19 | 2017-10-19 |  |
| OnePlus | No Known Official Response | "We encouraged you to stay tuned and keep track on our Community Forums and official website and other social media channels." | 2017-10-17 | 2017-10-16 |  |
| Onkyo | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Open-Mesh / CloudTrax | [LINK](https://help.cloudtrax.com/hc/en-us/articles/115001567804-KRACK-Bulletin) | An update is expected to be delivered to all of those that use automatic updates by the end over October 17th. | 2017-10-17 | 2017-10-17 |  |
| OpenBSD | [LINK](https://marc.info/?l=openbsd-announce&m=150410604407872&w=2) | Errata patches for the wireless stack have been released for OpenBSD 6.1 and 6.0. State transition errors could cause reinstallation of old WPA keys. Binary updates for the amd64 and i386 platforms are available via the syspatch utility. Source code patches can be found on the respective errata pages. As this affects the kernel, a reboot will be needed after patching. | 2017-10-16 | 2017-10-16 |  |
| OPNsense | No Known Official Response | (CALL FOR TESTING) KRACK Attack fixes [LINK](https://forum.opnsense.org/index.php?topic=6183.msg25964#msg25964)| 2017-10-18 | 2017-10-18 |  |
| Pakedge | No Known Official Response | Via @spike411 "They have acknowledged they have received my enquiry but don’t have any info about the state of this vulnerability in their products." | 2017-10-16 | 2017-10-16 |  |
| Particle | [LINK](https://community.particle.io/t/krack-patch-eta/36759/5?u=zachary) | Once Cypress releases updates to WICED Studio, Particle will create system firmware releases. Users can then build their apps on the new system versions. | 2017-10-18 | 2017-10-18 |  |
| Peplink | [LINK](https://forum.peplink.com/t/security-advisory-krack-wpa2-vulnerability-vu-228519/12715) | "We are developing firmware to address the vulnerability." ... "ETA for the firmware releases is within two weeks." | 2017-10-17 | 2017-10-17 | 2017-08-28 |
| pfSense | [LINK](https://redmine.pfsense.org/issues/7951) | N/A | 2017-10-17 | 2017-10-17 |  |
| Pioneer | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Qualcomm Atheros | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Rachio | No Known Official Response | Support response: "When it boils down into it, the KRACK attack can only target improperly done HTTPS / SSL connections, and we are perfectly safe in that regard. There is no need for our controller to get an update due to the leak itself, due to the massive lack of a GUI there is nothing at risk from our controller. <br/> From what I can see in my research and testing, KRACK vulnerability cannot potentially modify data on the network, or even eavesdrop from our controller. <br/> The absolute only thing at risk, after thorough testing, that a KRACK attacker would be able to *potentially* see is that you have a Rachio on your network. And even then, the only way they have the slightest ability to get any further would be via timing analysis, and even then it only would be your watering times." [LINK](https://twitter.com/Fezmid/status/920261178852630530)  | 2017-10-17 | 2017-10-17 |  |
| Raspbian (Raspberry Pi) | No Known Official Response | Update (20171002 01:38): The fixes for raspbian Jessie and Stretch should now be in the public raspbian repo. The fix for raspbian buster should follow in a few hours. I do not know if/when there will be a fix for wheezy. source: [LINK](https://raspberrypi.stackexchange.com/questions/73879/rpi-vulnerable-for-wi-fi-wpa2-krack-attack/73908#73908) | 2017-10-17 | 2017-10-17 |  |
| Red Hat, Inc. | This issue affects the versions of wpa_supplicant as shipped with Red Hat Enterprise Linux 6 and 7. [LINK](https://access.redhat.com/security/cve/cve-2017-13087) | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Ring | No Known Official Response | Per support "They promise to update public shortly, actively working with developers." | 2017-10-17 | 2017-10-17 |  |
| Ruckus Wireless | [Security Advisory Bulletin](https://ruckus-www.s3.amazonaws.com/pdf/security/faq-security-advisory-id-101617-v1.0.pdf)  | More forthcoming. [LINK](https://theruckusroom.ruckuswireless.com/wi-fi/2017/10/16/commonsense-approach-uncommon-problem/) | 2017-10-17 | 2017-10-17 |  |
| Sagemcom | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 | |
| Samsung Electronics | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Sharp | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| SnapAV | No Known Official Response (See comment for unofficial response) | An email from G Paul Hess, Chief Product Officer states that Araknis Networks Wireless Access Points and Autonomic 1e Music Streamer are affected. "We are currently working on a firmware update, which will be available on SnapAV’s website, as well as OvrC." | 2017-10-16 | 2017-10-17 |  |
| Sonicwall | [LINK](https://www.sonicwall.com/en-us/support/product-notification/wpa2-krack-exploit-a-sonicwall-alert) | N/A | 2017-10-17 | 2017-10-17 |  |
| Sonos | [LINK](https://en.community.sonos.com/ask-a-question-228987/is-sonos-vulnerable-to-the-krack-attack-6792188) | We're aware of the issues with WPA2 and our team is working to determine any ramifications this may have for Sonos players. | 2017-10-18 | 2017-10-18 |  |
| Sony | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Sophos AP | [LINK](https://community.sophos.com/kb/en-us/127658) | N/A | 2017-10-17 | 2017-10-17 |  |
| SUSE / openSUSE | [LINK](https://bugzilla.suse.com/show_bug.cgi?id=1063479) |  | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Swisscom | [LINK](https://supportcommunity.swisscom.ch/t5/Diskussionen-%C3%BCber-Ger%C3%A4te-und/WPA2-Leack-wirklich-oder-wieder-nur-Baitfishing/m-p/511992#M18540) | Internet Box routers not affected. Centro routers and AirTies repeaters to be clarified. | 2017-10-17 | 2017-10-17 | |
| Synology | [LINK](https://www.synology.com/en-us/support/security/Synology_SA_17_60_KRACK) | Synology DiskStation Manager (DSM) with attached WiFi dongle and Synology Router Manager (SRM) are vulnerable to Krack. According to Synology, updates for affected products will be released soon. | 2017-10-17 | 2017-10-17 |  |
| Tesco | [LINK](https://twitter.com/Tesco/status/920254455135854592) | Tesco has chosen not to patch the Hudl: "There will be no further updates to the hudl software" | 2017-10-17 | 2017-10-17 |  |
| Toshiba Commerce Solutions | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 15 Sep 2017 |
| Toshiba Electronic Devices & Storage Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Toshiba Memory Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| TP-Link | [LINK](http://forum.tp-link.com/showthread.php?101094-Security-Flaws-Severe-flaws-called-quot-KRACK-quot-are-discovered-in-the-WPA2-protocol), [LINK2](http://www.tp-link.com/en/faq-1970.html) | TP-Link has been working on affected models and will release firmware over the next few weeks on our official website. | 2017-10-18 | 2017-10-18 |  |
| Turris Omnia | [LINK](https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/9) | N/A | 2017-10-17 | 2017-10-17 |  |
| Ubiquiti Networks | [LINK](https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365) | Ubiquiti has released 3.9.3.7537 in beta to mitigate these vulnerabilities in UniFi APs that have a client mode. mFi devices are likely vulnerable and [no statement or patch](https://community.ubnt.com/t5/mFi/KRACK-WPA2-broken-Plans-for-mFi-hardware-fixes/m-p/2099826) has been released. | 2017-10-16 | 2017-10-16 |  |
| Ubuntu | [LINK](https://usn.ubuntu.com/usn/usn-3455-1/) | Updates are available for wpasupplicant and hostapd in Ubuntu 17.04, Ubuntu 16.04 LTS, and Ubuntu 14.04 LTS. wpasupplicant and hostapd were updated before the release of Ubuntu 17.10. | 2017-10-16 | 2017-10-16 |  |
| Volumio | [LINK](https://volumio.org/forum/changelog-t1575.html) | Updates are available for wpasupplicant and hostapd in Volumio starting from version 2.296 | 2017-10-18 | 2017-10-18 |  |
| WatchGuard | [LINK](https://www.watchguard.com/wgrd-blog/wpa-and-wpa2-vulnerabilities-update) | Sunday, October 15, 2017:,AP120, 320, 322, 420:,Release 8.3.0-657, Cloud mode only . Monday, October 30, 2017: AP300: Release 2.0.0.9 ,AP100, 102, 200: Release 1.2.9.14, AP120, 320, 322, 420:,Release 8.3.0-657, Non-Cloud (GWC mode) | 2017-10-17 | 2017-10-17 |  |
| webOS | No Known Official Response | Also see entry ConnMan | 2017-10-17 | 2017-10-20 |  |
| WiFi Alliance | [LINK](https://www.wi-fi.org/security-update-october-2017) | Users should refer to their Wi-Fi device vendor’s website or security advisories to determine if their device has been affected and has an update available. As always, Wi-Fi users should ensure they have installed the latest recommended updates from device manufacturers. | 2017-10-16 | 2017-10-16 |  |
| Xfinity | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Xirrus | [LINK](https://www.xirrus.com/vulnerability-statements/) | As soon as the patch is released, it will be made available through the Xirrus Support Community. | 2017-10-17 | 2017-10-17 |  |
| Yamaha | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Yi (Xiaomi) | No Known Official Response | "Waiting on a reply" | 2017-10-17 | 2017-10-17 |  |
| ZTE | No Known Official Response | Also see entry KPN | 2017-10-17 | 2017-10-20 |  |
| ZyXEL | [LINK](http://www.zyxel.com/support/announcement_wpa2_key_management.shtml) | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
