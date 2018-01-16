# KRACK: (K)ey (R)einstallation (A)tta(ck)

From the KRACK <a href="https://www.krackattacks.com/">website</a>:
> In a key reinstallation attack, the adversary tricks a victim into reinstalling an already-in-use key. This is achieved by manipulating and replaying cryptographic handshake messages. When the victim reinstalls the key, associated parameters such as the incremental transmit packet number (i.e. nonce) and receive packet number (i.e. replay counter) are reset to their initial value. Essentially, to guarantee security, a key should only be installed and used once. Unfortunately, we found this is not guaranteed by the WPA2 protocol. By manipulating cryptographic handshakes, we can abuse this weakness in practice.

***Unless a known patch has been applied, assume that all WPA2-enabled Wi-Fi devices are vulnerable.***

# ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Administrators: Remember to <a href="https://github.com/kristate/krackinfo/subscription">watch this page</a> for changes

## Go Directly to [Vendor Response Matrix](#vendor-response-complete)
## For Android devices please check the [Android Response Matrix](ANDROID.md)
## 日本人の皆さまへ： [こちらをご覧ください](/krackinfo_JA-JP.md)(日本語)

## The Good
* Should a vendor take responsibility, devices are for the most part updatable.
* Access points are only affected, if they implement the standard 802.11r (a.k.a. Fast-BSS Transition).

## The Bad
* Many devices do not have an easy way to apply updates.
* A huge burden is placed on the consumer to keep their devices up to date
  * It may not be easy to search for all updates to all devices.
* The attack affects both clients and access points
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

### Further information
* Marthy Vanhoef gave an overview presentation including implications at the conference 34c3. A [recording of his session](https://ftp.darmstadt.ccc.de/congress/2017/h264-hd/34c3-9273-eng-deu-spa-KRACKing_WPA2_by_Forcing_Nonce_Reuse_hd.mp4) is available.
* A [set of scripts](https://github.com/vanhoefm/krackattacks-scripts) has been made available which allows to check devices whether they are vulnerable.

### CVE List and Device Types Affected 
The reinstallation attack is not a single attack, but a group consisting of ten (10) independent security flaws which do have a common underlying approach. The security holes may be exploited indepdently of each other, and thus have to be fixed individually (if a device is affected). As it is common in computer security, each of them got assigned to a Common Vulnerabilities and Exposures (CVE) number, which are aggregated in [VU #228519](http://www.kb.cert.org/vuls/id/228519) for better tracking.
Based on a [statement provided by Zyxel](http://www.zyxel.com/support/announcement_wpa2_key_management.shtml) you may group these CVEs based on which communication party is affected:

| Common Vulnerabilities and Exposures (CVE)                        | Party Affected |
| ------------------------------------------------------------------|----------------|
| [CVE-2017-13077](https://nvd.nist.gov/vuln/detail/CVE-2017-13077) | Wi-Fi clients  |
| [CVE-2017-13078](https://nvd.nist.gov/vuln/detail/CVE-2017-13078) | Wi-Fi clients  |
| [CVE-2017-13079](https://nvd.nist.gov/vuln/detail/CVE-2017-13079) | Wi-Fi clients  |
| [CVE-2017-13080](https://nvd.nist.gov/vuln/detail/CVE-2017-13080) | Wi-Fi clients  |
| [CVE-2017-13081](https://nvd.nist.gov/vuln/detail/CVE-2017-13081) | Wi-Fi clients  |
| [CVE-2017-13082](https://nvd.nist.gov/vuln/detail/CVE-2017-13082) | Access Points, if implementing standard 802.11r |
| [CVE-2017-13084](https://nvd.nist.gov/vuln/detail/CVE-2017-13084) | Wi-Fi clients  |
| [CVE-2017-13086](https://nvd.nist.gov/vuln/detail/CVE-2017-13086) | Wi-Fi clients  |
| [CVE-2017-13087](https://nvd.nist.gov/vuln/detail/CVE-2017-13087) | Wi-Fi clients  |
| [CVE-2017-13088](https://nvd.nist.gov/vuln/detail/CVE-2017-13088) | Wi-Fi clients  |

Access points, which are intended for the consumer market, typically do *not* implement the standard 802.11r. However, access points for the enterprise market may do so. 

Based on the table above, it becomes apparent that the primary effort for correcting the security flaw is to be expected for the Wi-Fi clients.
As of writing, there is no possibility known to safeguard Wi-Fi clients by changing the access point's behavior. This implies that patching the Wi-Fi device is the only way to fix the problem for Wi-Fi clients.

### Related Reading
* https://blog.cryptographyengineering.com/2017/10/16/falling-through-the-kracks/
* https://www.reddit.com/r/KRaCK/comments/76pjf8/krack_megathread_check_back_often_for_updated/

## Vendor Patch Matrix (non-complete)

| Vendor | Patch Available | In Development | Not Directly Affected |
|--------|-----------------|----------------|-----------------------|
| Apple | [X](APPLE.md) | ? |  |
| Arch Linux | X |  |  |
| Arista |  |  | X |
| Aruba | [X](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007_FAQ_Rev-1.pdf) |  |  |
| Asus |  | [X](https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/)  | X |
| CentOS | X |  |  |
| Cisco | [X](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20171016-wpa) |  |  |
| DD-WRT | X |  |  |
| Debian | X |  |  |
| Endian  | X |  |  |
| Extreme Networks | [X](https://extremeportal.force.com/ExtrArticleDetail?n=000018005) | [X](https://extremeportal.force.com/ExtrArticleDetail?n=000018005) |  |
| Fedora | X |  |  |
| FreeBSD | [X](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001806.html) |  |  |
| Google | [X](https://source.android.com/security/bulletin/2017-11-01) |  |  |
| Lenovo |  |  | ? |
| LineageOS | [X](https://mobile.twitter.com/LineageAndroid/status/920143977256382464) |  |  |
| LXDE |  | X |  |
| Meraki | X |  |  |
| MikroTik | X |  |  |
| Mojo Networks | X |  |  |
| Red Hat | X |  |  | 
| Ruckus | [X](https://support.ruckuswireless.com/krack-ruckus-wireless-support-resource-center) |  |  |
| Synology | [X](https://www.synology.com/en-global/releaseNote/DDSM) |  |  |
| SUSE / openSUSE | [X](https://bugzilla.suse.com/show_bug.cgi?id=1056061) | [X](https://bugzilla.suse.com/show_bug.cgi?id=1063479)  |  |
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
| 3com Inc | No Known Official Response | N/A | 2017-10-29 | 2017-10-17 |  |
| Actiontec | [Link](https://actiontecsupport.zendesk.com/hc/en-us/articles/115005205283-KRACK-vulnerability) | N/A | 2017-10-18 | 2017-10-18 |  |
| Aerohive | [Link](https://boundless.aerohive.com/technology/Aerohive-Response-To-KRACK.html) | N/A | 2017-10-17 | 2017-10-17 |  |
| Alcatel-Lucent | [LINK](https://www.al-enterprise.com//en/-/media/assets/internet/documents/sa-n0050_wpa2_key_reinstallation_vulnerabilities.pdf) | Support is suggested to go via the network vendors; patches are available for OmniAccess and OmniAccess Stellar WLAN products | 2017-10-29 | 2017-10-18 |  |
| Amazon | No Known Official Response | "We are in the process of reviewing which of our devices may contain this vulnerability and will be issuing patches where needed." | 2017-10-29 | 2017-10-17 |  |
| Android | [Security Bulletin](https://source.android.com/security/bulletin/2017-11-01) | fixed with versions 5.0.2, 5.1.1, 6.0, 6.0.1, 7.0, 7.1.1, 7.1.2, 8.0 <br />Security patch level 2017-11-06 or later required to be fixed. Note that security patch level 2017-11-05 is **not** sufficient.<br />Distribution to vendors to downstream has started; vendors may need additional fixes from hardware suppliers. | 2017-11-11 | 2017-11-11 |  |
| Apple | [General Security Updates](https://support.apple.com/en-us/HT201222) | [see details page](APPLE.md) | 2017-11-01 | 2017-11-01 |  |
| Arch Linux | [wpa_supplicant](https://git.archlinux.org/svntogit/packages.git/commit/trunk?h=packages/wpa_supplicant&id=9c1bda00a846ff3b60e7c4b4f60b28ff4a8f7768), [hostapd](https://git.archlinux.org/svntogit/community.git/commit/trunk?h=packages/hostapd&id=d31735a09b4c25eaa69fb13b1031910ca3c29ee5) | N/A | 2017-10-16 | 2017-10-16 |  |
| Arduino | No Known Official Response | EspressIf [fixed its ESP8266 SDK](https://github.com/espressif/ESP8266_NONOS_SDK/commit/b762ea222ee94b9ffc5e040f4bf78dd8ba4db596) in upstream (see also row "Espressif Systems" in this table below); [SDK Fix](https://github.com/esp8266/Arduino/issues/3725) is on the way | 2017-10-29 | 2017-10-29 |  |
| Asus | [LINK](https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/) | New firmware available / Additionally, an email response from "security@asus.com" says that they are "co-working with chipset vendors for solutions and will release patched firmware for affected routers soon."; the [security advisory statement from 2017-10-31](https://www.asus.com/Static_WebPage/ASUS-Product-Security-Advisory/) lists more than 70 devices *not* affected by the attack | 2017-11-21 | 2017-11-21 |  |
| AVM (FRITZ!Box)  | [LINK](https://en.avm.de/news/short-notes/2017/wpa2-flaw-fritzbox-on-broadband-connections-are-secure/), [LINK2](https://avm.de/service/aktuelle-sicherheitshinweise/) | WPA2 flaw – FRITZ!Box on broadband connections are secure. AVM has provided updates for its wireless repeaters and its Powerline product series. Download of new firmwares are available in the [download area](https://avm.de/nc/service/downloads/) | 2017-10-28 | 2017-10-28 |  |
| Barracuda Networks | [LINK](https://community.barracudanetworks.com/forum/index.php?/topic/23525-security-advisories/page-2#entry84537) | Our investigations indicate that currently only Barracuda NextGen Firewall Wi-Fi Models used under Wi-Fi Client mode are affected. | 2017-10-17 | 2017-10-17 |  |
| BearExtender / Bearifi | No Known Official Response | N/A | 2017-11-12 | 2017-11-12 |  |
| Belkin, Linksys, and Wemo | [LINK@Linksys](https://www.linksys.com/us/support-article?articleNum=246427), [LINK@Belkin](http://www.belkin.com/us/support-article?articleNum=275531) | "We are still confirming all product skus affected, including Belkin Routers and Range Extenders, Linksys Routers, Adapters, Access Points, Bridges and Range Extenders and Wemo Products.  As mentioned, when firmware is available, it will be posted to the associated brands’ support page." | 2017-10-28 | 2017-10-28 |  |
| bintec elmeg (Teldat Group) | [LINK](https://e2e.ti.com/support/wireless_connectivity/simplelink_wifi_cc31xx_cc32xx/f/968/t/632869) | APs do not have support for 802.11r and 802.11s (thus not affected in AP-only mode); APs in client mode may be affected: further investigations ongoing | 2017-10-29 | 2017-10-29 |  |
| Broadcom / Cypress | [LINK](https://community.cypress.com/docs/DOC-13871) (Cypress community login required) | WICED Studio, `wpa_supplicant`, and linux releases in late October will address the relevant CVEs. | 2017-10-18 | 2017-10-18 |  |
| Brother | No Known Official Response | N/A | 2017-10-29 | 2017-10-19 |  |
| Buffalo / MELCO | [LINK(JA)](http://buffalo.jp/support_s/t20171017.html) | N/A | 2017-10-18 | 2017-10-18 |  |
| Canon | No Known Official Response | N/A | 2017-10-29 | 2017-10-16 |  |
| CentOS | [CentOS 6](https://lists.centos.org/pipermail/centos-announce/2017-October/022570.html), [CentOS 7](https://lists.centos.org/pipermail/centos-announce/2017-October/022569.html) | From upstream Red Hat Security Advisories [RHSA-2017:2911](https://access.redhat.com/errata/RHSA-2017:2911), and [RHSA-2017:2907](https://access.redhat.com/errata/RHSA-2017:2907) Arch: Centos6 [i386](http://mirror.centos.org/centos-6/6/updates/i386/Packages/), [x86_64](http://mirror.centos.org/centos-6/6/updates/x86_64/Packages/); Centos7 [x86_64](http://mirror.centos.org/centos-7/7.4.1708/updates/x86_64/Packages/), [ARM](http://mirror.centos.org/altarch/7/updates/armhfp/Packages/) (Raspberry PI), [ppc64](http://mirror.centos.org/altarch/7/updates/ppc64/Packages/), [ppc64le](http://mirror.centos.org/altarch/7/updates/ppc64le/Packages/),  | 2017-10-18 | 2017-10-18 |  |
| Cisco | [LINK](https://tools.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-20171016-wpa) | Multiple Cisco wireless products are affected by these vulnerabilities. | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Comcast | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| ConnMann | No Known Official Response | Connman has not released any information or updates yet. [LINK](https://01.org/connman/blogs) | 2017-10-17 | 2017-10-20 |  |
| CZ.NIC Turris | [LINK](https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/8) | via @spike411: CZ.NIC Turris team is testing a fix (backported from hostapd upstream): [LINK](https://gitlab.labs.nic.cz/turris/openwrt/commit/a60970f33f65bfb1d531ce822bfd28ee049a702f) | 2017-10-16 | 2017-10-16 |  |
| D-Link | [LINK](http://supportannouncement.us.dlink.com/announcement/publication.aspx?name=SAP10075) | [List of affected products](http://www.dlink.com/uk/en/support/support-news/2017/october/18/response-to-krack-wpa2-key-reinstallation-attack-security-vulnerability) (includes statement for which models patches are already provided) | 2017-10-28 | 2017-10-28 |  |
| DD-WRT | [LINK](http://svn.dd-wrt.com/changeset/33525) | N/A | 2017-10-17 | 2017-10-17 |  |
| Debian | [LINK](https://www.debian.org/security/2017/dsa-3999) | * Add patches to fix WPA protocol vulnerabilities (CVE-2017-13077,    CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081,    CVE-2017-13082, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088):    - hostapd: Avoid key reinstallation in FT handshake    - Prevent reinstallation of an already in-use group key    - Extend protection of GTK/IGTK reinstallation of WNM-Sleep Mode cases    - Fix PTK rekeying to generate a new ANonce    - TDLS: Reject TPK-TK reconfiguration    - WNM: Ignore WNM-Sleep Mode Response if WNM-Sleep Mode has not been used    - WNM: Ignore WNM-Sleep Mode Response without pending request    - FT: Do not allow multiple Reassociation Response frames    - TDLS: Ignore incoming TDLS Setup Response retries | 2017-10-16 | 2017-10-16 |  |
| Dell | [LINK](http://www.dell.com/support/article/de/de/debsdt1/sln307822/wi-fi-security-protocol-key-re-installation-attack--krack---impact-status-on-dell-products?lang=en) | Several products affected; patches are under development | 2017-10-29 | 2017-10-29 |  |
| Denon | No Known Official Response | N/A | 2017-11-21 | 2017-10-17 |  |
| Devolo | [LINK](https://www.heise.de/forum/p-31221501/)(German only) | They are currently reviewing the attack scenario for their products according to [this tweet](https://twitter.com/devoloAG/status/920253378873233408); they report that they are not affected by this (both old and current devices), as the WPA2 parts, which are affected, are not used in their products | 2017-10-29 | 2017-10-29 |  |
| DrayTek | [LINK](http://www.draytek.co.uk/information/our-technology/wpa2-krack-vulnerability) | DrayTek are investigating solutions for this and plan to issue appropriate updates (firmware) as soon as possible. First firmware updates are either announced (with patch version numbers provided) or even released (and then can be found at the [firmware download page](https://www.draytek.com/en/download/firmware/), e.g. VigorAP 902) | 2017-10-28 | 2017-10-28 |  |
| ecobee | No Known Official Response | Twitter response [1](https://twitter.com/ecobee/status/920316685193707521) and [2](https://twitter.com/ecobee/status/920316741334552576): "ecobee is aware of the industry-wide vulnerability in WPA2 referred to as KRACK.   The security of our customers is very important to us and we have confirmed that ecobee device security is not impacted by this issue." Likely this means ecobee considers underlying https / ssl to be secure despite KRACK | 2017-10-17 | 2017-10-17 |  |
| Edimax | [LINK](http://www.edimax.com/edimax/post/post/data/edimax/global/response_to_krack/) | EDIMAX Wi-Fi Router, Range Extender, USB NIC(SoftAP) and Access Points(WDS Mode) are impacted with WDS or repeater mode; patches are on the way. EDIMAX USB NIC, Access Points and IP Camera are not impacted. | 2017-10-28 | 2017-10-28 |  |
| eero | [LINK](https://blog.eero.com/krack-update-fix-available-eero-ota/) | Patched firmware automatically pushed to users OTA;  also available for download | 2017-10-17 | 2017-10-17 | |
| ELECOM | [LINK(JA)](http://www.elecom.co.jp/support/news/20171018/) | N/A | 2017-10-20 | 2017-10-20 |  |
| EMC Corporation | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Endian | [LINK](https://help.endian.com/hc/en-us/articles/115013641427-WPA-and-WPA2-Vulnerability-KRACK-Key-Reinstallation-Attacks-Update) | Community version is not affected. Fixed on Enterprise 5.0 | 2017-10-18 | 2017-10-18 |  |
| EnGenius | [LINK](https://helpcenter.engeniustech.com/hc/en-us/articles/115002197872-EnGenius-Advisory-on-the-WPA2-KRACK-vulnerability) | "EnGenius software developers are currently working on security patches and will issue firmware releases as soon as possible." | 2017-10-18 | 2017-10-18 |  |
| Espressif Systems | [LINK](http://espressif.com/en/media_overview/news/espressif-releases-patches-wifi-vulnerabilities-cert-vu228519) | Espressif released patches for the WiFi vulnerabilities in their products including ESP-IDF, ESP8266 RTOS and ESP8266 NON-OS. Arduino ESP32 will be updated shortly. | 2017-10-16 | 2017-10-16 | 22 Sep 2017 |
| Extreme Networks | [LINK](https://extremeportal.force.com/ExtrArticleDetail?n=000018005) | Patches available for ExtremeWireless, ExtremeWireless WiNG. ExtremeCloud and WLAN 8100/9100 patches still in development. | 2017-10-26 | 2017-10-25 | 2017-08-28 |
| F5 Networks | [LINK](https://support.f5.com/csp/article/K23642330) | There is no impact; F5 products are not affected by this vulnerability. | 2017-10-19 | 2017-10-19 |  |
| Fedora | Fedora [26](https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc26) / [27 (beta)](https://bodhi.fedoraproject.org/updates/wpa_supplicant-2.6-11.fc27) | Status: Fixed Release: Stable (* Manual installation is possible) Arch: x86_64 and ARM (Raspberry PI) | 2017-10-17 | 2017-10-19 |  |
| FortiNet | [LINK](http://www.fortiguard.com/psirt/FG-IR-17-196) | Only affected in client / mesh leaf mode or when using 802.11r; patches available | 2017-11-07 | 2017-11-02 |  |
| Foundry Brocade | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| FreeBSD Project | [Response](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001805.html), [patch](https://lists.freebsd.org/pipermail/freebsd-announce/2017-October/001806.html) | Binary and source updates to base system available. Alternatively one can install the `security/wpa_supplicant` port or package in lieu of the same in base. | 2017-10-17 | 2017-10-17 | (?) |
| Google | [Nexus/Pixel](https://source.android.com/security/bulletin/pixel/2017-11-01)<br />[ChromeOS Fix](https://productforums.google.com/forum/#!topic/chromebook-central/OFNTYYpOnFc) | Nexus/Pixel devices: Security patch level 2017-11-06 or later required to be fixed. Note that security patch level 2017-11-05 is **not** sufficient. Distribution expected to happen with [December security update](https://arstechnica.com/gadgets/2017/11/pixel-wont-get-krack-fix-until-december-but-is-that-really-a-big-deal/). For further details, see also *Android* above.<br />Link to [initial statement](https://www.cnet.com/au/news/google-to-patch-krack-impacted-devices-in-the-next-few-weeks/) | 2017-11-13 | 2017-11-13 |  |
| Hewlett Packard Enterprise / Aruba | [LINK@HPE](http://h22208.www2.hpe.com/eginfolib/securityalerts/Krack%20Attack/WPA2-KrackAttack.html), [Aruba Patch Info](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007.txt) - [Aruba FAQ](http://www.arubanetworks.com/assets/alert/ARUBA-PSA-2017-007_FAQ_Rev-1.pdf) | Analysis still ongoing. First Aruba | 2017-10-17 | 2017-10-17 | Aruba: 2017-08-28 |
| Honeywell | No Known Official Response | Impact [in assessment](https://github.com/kristate/krackinfo/issues/217); no fix available, yet | 2017-11-12 | 2017-11-12 |  |
| Huawei | [LINK](http://www.huawei.com/en/psirt/security-notices/huawei-sn-20171017-01-wpa-en) | "Huawei immediately launched investigation and carried out technical communication with the researcher." | 2017-11-28 | 2017-11-20 |  |
| I-O DATA | [LINK(JA)](http://www.iodata.jp/support/information/2017/wpa2/) | N/A | 2017-10-18 | 2017-10-18 |  |
| IBM | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Icotera | Icotera products are not affected [LINK](https://icotera.zendesk.com/hc/en-us/articles/115002195451-WPA2-Key-re-installation-attacks-KRACK-on-Icotera-products-) | The investigation concluded that none of current Icotera products is affected by the described vulnerability, as it does not apply to a device running Access Point mode only | 2017-10-19 | 2017-10-19 |  |
| Intel Corporation | [LINK](https://security-center.intel.com/advisory.aspx?intelid=INTEL-SA-00101&languageid=en-fr) | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| IPFire | [LINK](https://planet.ipfire.org/post/krack-attack-patches-are-on-their-way) | Update: packages for all architectures are now available | 2017-10-19 | 2017-10-19 |  |
| iRobot (Roomba) | No Known Official Response | Chat support: "So far as we can tell, we haven't been impacted. So that's good news lol." [IMG](https://user-images.githubusercontent.com/271922/31730055-05bd1658-b431-11e7-84fc-0b5ef663905b.png) | 2017-10-17 | 2017-10-17 |  |
| Jolla | [LINK](https://together.jolla.com/question/170073/krack-attacks-wpa2-is-not-secure-anymore/?answer=170198#post-id-170198) | N/A | 2017-10-17 | 2017-10-17 |  |
| Juniper Networks | [LINK](https://kb.juniper.net/InfoCenter/index?page=content&id=JSA10827) | Patches for WLAN available; patches for SRX and SSG outstanding | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| KPN | [LINK](https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol) | KPN routers to be found safe. See update 17th [LINK](https://overons.kpn/nl/nieuws/2017/beveiligingsonderzoekers-vinden-kwetsbaarheid-in-wifi-protocol) | 2017-10-17 | 2017-10-20 |  |
| Kyocera Communications | No Known Official Response | N/A | 2017-10-29 | 2017-10-17 |  |
| LEDE | [LINK](https://lede-project.org/releases/17.01/notes-17.01.4) | Released fix in version 17.01.4. | 2017-10-18 | 2017-10-18 | |
| Lenovo | [LINK](https://support.lenovo.com/de/de/product_security/len-17420) | Impact assessment apparently still ongoing | 2017-10-29 | 2017-10-29 |  |
| LineageOS | [LINK](https://review.lineageos.org/#/q/topic:krack-n) | "All official 14.1 builds built after this tweet have been patched for KRACK.":[LINK](https://twitter.com/LineageAndroid/status/920143977256382464) | 2017-10-17 | 2017-10-17 |  |
| Linux | Patches: [LINK](https://w1.fi/security/2017-1/) | wpa_supplicant version 2.4 and above is affected. Linux's wpa_supplicant v2.6 is also vulnerable to the installation of an all-zero encryption key in the 4-way handshake. | 2017-10-16 | 2017-10-16 |  |
| Logitech | [LINK](https://community.logitech.com/s/question/0D55A000077ySvjSAE/harmony-hub-and-krack-wifi-wpa2-security) | Harmony: vendor is aware of the vulnerability; review in process | 2017-11-12 | 2017-11-12 |  |
| Luxul | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Marantz | No Known Official Response | N/A | 2017-11-21 | 2017-10-17 |  |
| Marvell Semiconductor | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| MediaTek | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Meraki | [LINK](https://documentation.meraki.com/zGeneral_Administration/Support/802.11r_Vulnerability_(CVE%3A_2017-13082)_FAQ) | Fixed for Cisco Meraki in 24.11 and 25.7 | 2017-10-16 | 2017-10-16 |  |
| Microchip Technology | [LINK](http://www.microchip.com/design-centers/wireless-connectivity/embedded-wi-fi/wpa2-protocol-vulnerability) | N/A | 2017-10-17 | 2017-10-17 | 28 Aug 2017 |
| Microsoft | [Windows Related](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-13080) | When clicking the link, accept the EULA then click the link again. Provided security fix apparently does not solve the issue under all circumstances ("[...] however, when affected Windows based systems enter a connected standby mode in low power situations, the vulnerable functionality may be offloaded to installed Wi-Fi hardware", see FAQ at [link](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/CVE-2017-13080)), i.e. hardware vendors *also* may have to provide fixes for their devices | 2017-10-16 | 2017-10-28 |  |
| MidnightBSD | No Known Official Response | Workaround available by installing wpa_supplicant from mports/security/wpa_supplicant | 2017-10-21 | 2017-10-21 |  |
| Mikrotik | [LINK](https://forum.mikrotik.com/viewtopic.php?f=21&t=126695) | We released fixed versions last week, so if you upgrade your devices routinely, no further action is required. | 2017-10-16 | 2017-10-16 |  |
| Mojo Networks | [LINK](https://www.mojonetworks.com/wpa2-vulnerability) | Update to cloud management platform completed. In order to mitigate client-side vulnerabilities, Mojo recommends upgrading AP software to version 8.5, and enabling MAC Spoofing and Man-in-the-middle attack prevention with built-in WIPs. | 2017-10-17 | 2017-10-17 |  |
| NEC (ATERM) | [LINK(JA)](http://www.aterm.jp/product/atermstation/info/2017/info1018.html) | N/A | 2017-10-20 | 2017-10-20 |  |
| Nest Labs | [LINK](https://nest.com/support/article/KRACK-vulnerability) | Nest Tweeted: "We plan to roll out patches to our products in the coming weeks. These won't require any action on the part of the user.", First firmware updates are in distribution. Nest Protect still is missing. | 2017-10-28 | 2017-10-28 |  |
| netBSD | [LINK](http://mail-index.netbsd.org/pkgsrc-changes/2017/10/17/msg165433.html) | N/A | 2017-10-22 | 2017-10-22 |  |
| Netgear | [LINK](https://kb.netgear.com/000049498/Security-Advisory-for-WPA-2-Vulnerabilities-PSV-2017-2826-PSV-2017-2836-PSV-2017-2837) | N/A | 2017-10-16 | 2017-10-16 |  |
| Nikon | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nintendo | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Nokia | No Known Official Response | "I have forwarded your support request to our Tier 3 team for their assistance. We appreciate your patience as we work to resolve your issue, and will get back in touch as soon as we have additional steps for you to take.", source: [#174](https://github.com/kristate/krackinfo/issues/174) | 2017-10-27 | 2017-10-27 |  |
| Nvidia | [FIX](https://shield.nvidia.com/support/nvidia-android-tv/release-notes/1) | Android Security patch has been applied | 2017-11-12 | 2017-11-12 |  |
| OmniROM | [LINK](https://blog.omnirom.org/development/2017/10/17/omni-builds-updated-krack/) | "all official OmniROM N builds have the fix included." | 2017-10-19 | 2017-10-19 |  |
| OnePlus | [LINK for OxygenOS 3.6.1](https://www.androidsage.com/2017/10/26/oxygen-os-3-6-1-for-oneplus-2/) [LINK for OxygenOS 4.5.14](https://forums.oneplus.net/threads/oxygenos-4-5-14-ota-for-the-oneplus-5.671640/) | N/A | 2017-11-12 | 2017-11-12 |  |
| Onkyo | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Open-Mesh / CloudTrax | [LINK](https://help.cloudtrax.com/hc/en-us/articles/115001567804-KRACK-Bulletin) | An update is expected to be delivered to all of those that use automatic updates by the end over October 17th. | 2017-10-17 | 2017-10-17 |  |
| OpenBSD | [LINK](https://marc.info/?l=openbsd-announce&m=150410604407872&w=2) | Errata patches for the wireless stack have been released for OpenBSD 6.1 and 6.0. State transition errors could cause reinstallation of old WPA keys. Binary updates for the amd64 and i386 platforms are available via the syspatch utility. Source code patches can be found on the respective errata pages. As this affects the kernel, a reboot will be needed after patching. | 2017-10-16 | 2017-10-16 |  |
| OPNsense | No Known Official Response | (CALL FOR TESTING) KRACK Attack fixes [LINK](https://forum.opnsense.org/index.php?topic=6183.msg25964#msg25964)| 2017-10-18 | 2017-10-18 |  |
| Pakedge | No Known Official Response | Via @spike411 "They have acknowledged they have received my enquiry but don’t have any info about the state of this vulnerability in their products." | 2017-10-16 | 2017-10-16 |  |
| Particle | [LINK](https://community.particle.io/t/krack-patch-eta/36759/5?u=zachary) | Once Cypress releases updates to WICED Studio, Particle will create system firmware releases. Users can then build their apps on the new system versions. | 2017-10-18 | 2017-10-18 |  |
| Peplink | [LINK](https://forum.peplink.com/t/security-advisory-krack-wpa2-vulnerability-vu-228519/12715) | "We are developing firmware to address the vulnerability." ... "ETA for the firmware releases is within two weeks." | 2017-10-17 | 2017-10-17 | 2017-08-28 |
| PetNet &amp; Electric Imp | [LINK](http://blog.electricimp.com/post/166480380360/security-news-key-reinstallation-attacks-krack) | Not affected, as all communication is TLS-secured; waiting for hardware vendors to provide fixes to allow incorporation into one of the next impOS versions | 2017-11-12 | 2017-11-12 |  |
| pfSense | [RELEASES](https://www.netgate.com/blog/pfsense-2-4-1-release-now-available.html) [LINK](https://redmine.pfsense.org/issues/7951) | pfSense 2.4.1 & 2.3.5 releases (and later patches) contain "Fixes for the set of WPA2 Key Reinstallation Attack issues commonly known as KRACK" | 2017-10-29 | 2017-10-29 |  |
| Pioneer | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| PLANEX | [LINK(JA)](http://www.planex.co.jp/news/info/20171019_info.shtml) | N/A | 2017-10-20 | 2017-10-20 |  |
| Qualcomm Atheros | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| Rachio | No Known Official Response | Support response: "When it boils down into it, the KRACK attack can only target improperly done HTTPS / SSL connections, and we are perfectly safe in that regard. There is no need for our controller to get an update due to the leak itself, due to the massive lack of a GUI there is nothing at risk from our controller. <br/> From what I can see in my research and testing, KRACK vulnerability cannot potentially modify data on the network, or even eavesdrop from our controller. <br/> The absolute only thing at risk, after thorough testing, that a KRACK attacker would be able to *potentially* see is that you have a Rachio on your network. And even then, the only way they have the slightest ability to get any further would be via timing analysis, and even then it only would be your watering times." [LINK](https://twitter.com/Fezmid/status/920261178852630530)  | 2017-10-17 | 2017-10-17 |  |
| Raspbian (Raspberry Pi) | No Known Official Response | Update (20171002 01:38): The fixes for raspbian Jessie and Stretch should now be in the public raspbian repo. The fix for raspbian buster should follow in a few hours. I do not know if/when there will be a fix for wheezy. source: [LINK](https://raspberrypi.stackexchange.com/questions/73879/rpi-vulnerable-for-wi-fi-wpa2-krack-attack/73908#73908) [REPO](http://archive.raspbian.org/raspbian/pool/main/w/wpa/) [FORUM](https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=195507)| 2017-10-17 | 2017-10-17 |  |
| Realtek | No Known Official Response | N/A | 2017-10-28 | 2017-10-28 | |
| Red Hat, Inc. | This issue affects the versions of wpa_supplicant as shipped with Red Hat Enterprise Linux 6 and 7. [LINK](https://access.redhat.com/security/cve/cve-2017-13087) | Red Hat Security Advisories for Red Hat Enterprise Linux 7 [RHSA-2017:2911](https://access.redhat.com/errata/RHSA-2017:2911) and Red Hat Enterprise Linux 6 [RHSA-2017:2907](https://access.redhat.com/errata/RHSA-2017:2907) | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Ring | No Known Official Response | Per support "They promise to update public shortly, actively working with developers." | 2017-10-17 | 2017-10-17 |  |
| Rosewill | No Known Official Response | N/A | 2017-10-25 | 2017-10-25 | |
| Ruckus Wireless | [KRACK Resource Center](https://support.ruckuswireless.com/krack-ruckus-wireless-support-resource-center)  | N/A | 2017-10-17 | 2017-10-17 |  |
| Sagemcom | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 | |
| Samsung Electronics | [LINK](https://security.samsungmobile.com/securityUpdate.smsb) | Delivery of patches with [Security Maintenance Release SMR-NOV-2017](https://security.samsungmobile.com/securityUpdate.smsb) planned; Expected [scope](https://security.samsungmobile.com/workScope.smsb) until December: S8, S8+, S8 Active, S7, S7 edge, S7 Active, S6 edge+, S6, S6 edge, S6 Active; additionally with the next quarterly update: A3 (2016), A3 (2017), A7 (2017), J1 Mini, J1 Mini Prime, J1 Ace, J1 (2016), J2 (2016), J3 (2016), J5 (2016),  J7 (2016), J3 Pro, J3 Pop, J7 Pop, J3 (2017), J5 (2017), J7 (2017), J7 Max, J7 Neo, Tab S2 L Refresh, Tab S3 9.7, Note FE | 2017-11-13 | 2017-11-13 | 28 Aug 2017 |
| Sharp | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 |  |
| SnapAV | No Known Official Response (See comment for unofficial response) | An email from G Paul Hess, Chief Product Officer states that Araknis Networks Wireless Access Points and Autonomic 1e Music Streamer are affected. "We are currently working on a firmware update, which will be available on SnapAV’s website, as well as OvrC." | 2017-10-16 | 2017-10-17 |  |
| Sonicwall | [LINK](https://www.sonicwall.com/en-us/support/product-notification/wpa2-krack-exploit-a-sonicwall-alert) | N/A | 2017-10-17 | 2017-10-17 |  |
| Sonos | [LINK](https://en.community.sonos.com/ask-a-question-228987/is-sonos-vulnerable-to-the-krack-attack-6792188) | We're aware of the issues with WPA2 and our team is working to determine any ramifications this may have for Sonos players. | 2017-10-18 | 2017-10-18 |  |
| Sony | [LINK](https://talk.sonymobile.com/t5/Other-Discussions-General/KRACK-attack-on-wifi-WPA2/m-p/1269528) | First Xperia devices announced to receive patches; Android Security Patch level will be dated above 2017-11-05 | 2017-10-29 | 2017-10-29 |  |
| Sophos AP | [LINK](https://community.sophos.com/kb/en-us/127658) | N/A | 2017-10-17 | 2017-10-17 |  |
| SUSE / openSUSE | [hostap](https://bugzilla.suse.com/show_bug.cgi?id=1063479)  [wpa_supplicant](https://bugzilla.suse.com/show_bug.cgi?id=1056061) |  Patches available for `wpa_supplicant`. `hostap` in the works. See links for details | 2017-10-20 | 2017-10-20 | 28 Aug 2017 |
| Swisscom | [LINK](https://supportcommunity.swisscom.ch/t5/Diskussionen-%C3%BCber-Ger%C3%A4te-und/WPA2-Leack-wirklich-oder-wieder-nur-Baitfishing/m-p/511992#M18540) | Internet Box and Centro routers not affected. AirTies repeaters to be clarified. | 2017-10-31 | 2017-10-19 | |
| Synology | [LINK 1](https://www.synology.com/en-global/releaseNote/DDSM) [LINK 1](https://www.synology.com/en-us/support/security/Synology_SA_17_60_KRACK) | Synology DiskStation Manager (DSM) with attached WiFi dongle and Synology Router Manager (SRM) are vulnerable to Krack. As of Version 6.1.3-15152-8: Fixed multiple security vulnerabilities regarding WPA/WPA2 protocols for wireless connections (CVE-2017-13077, CVE-2017-13078, CVE-2017-13079, CVE-2017-13080, CVE-2017-13081, CVE-2017-13082, CVE-2017-13084, CVE-2017-13086, CVE-2017-13087, CVE-2017-13088). | 2017-10-17 | 2017-10-17 |  |
| Technicolor | No Known Official Response | N/A | 2017-10-29 | 2017-10-29 | |
| Tesco | [LINK](https://twitter.com/Tesco/status/920254455135854592) | Tesco has chosen not to patch the Hudl: "There will be no further updates to the hudl software" | 2017-10-17 | 2017-10-17 |  |
| Texas Instruments | [LINK](https://e2e.ti.com/support/wireless_connectivity/simplelink_wifi_cc31xx_cc32xx/f/968/t/632869) | Patches already provided | 2017-10-29 | 2017-10-29 |  |
| Toshiba Commerce Solutions | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 15 Sep 2017 |
| Toshiba Electronic Devices & Storage Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| Toshiba Memory Corporation | No Known Official Response | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
| TP-Link | [LINK](http://forum.tp-link.com/showthread.php?101094-Security-Flaws-Severe-flaws-called-quot-KRACK-quot-are-discovered-in-the-WPA2-protocol), [LINK2](http://www.tp-link.com/en/faq-1970.html) | TP-Link has been working on affected models and will release firmware over the next few weeks on our official website. | 2017-10-18 | 2017-10-18 |  |
| Turris Omnia | [LINK](https://forum.turris.cz/t/major-wpa2-vulnerability-to-be-disclosed/5363/9) | N/A | 2017-10-17 | 2017-10-17 |  |
| Ubiquiti Networks | [LINK](https://community.ubnt.com/t5/UniFi-Updates-Blog/FIRMWARE-3-9-3-7537-for-UAP-USW-has-been-released/ba-p/2099365) | Ubiquiti has released 3.9.3.7537 in beta to mitigate these vulnerabilities in UniFi APs that have a client mode. mFi devices are likely vulnerable and [no statement or patch](https://community.ubnt.com/t5/mFi/KRACK-WPA2-broken-Plans-for-mFi-hardware-fixes/m-p/2099826) has been released. | 2017-10-16 | 2017-10-16 |  |
| Ubuntu | [LINK](https://usn.ubuntu.com/usn/usn-3455-1/) | Updates are available for wpasupplicant and hostapd in Ubuntu 17.04, Ubuntu 16.04 LTS, and Ubuntu 14.04 LTS. wpasupplicant and hostapd were updated before the release of Ubuntu 17.10. | 2017-10-16 | 2017-10-16 |  |
| Volumio | [LINK](https://volumio.org/forum/changelog-t1575.html) | Updates are available for wpasupplicant and hostapd in Volumio starting from version 2.296 | 2017-10-18 | 2017-10-18 |  |
| WatchGuard | [LINK](https://www.watchguard.com/wgrd-blog/wpa-and-wpa2-vulnerabilities-update) | Sunday, October 15, 2017:,AP120, 320, 322, 420:,Release 8.3.0-657, Cloud mode only. Monday, October 30, 2017: AP300: Release 2.0.0.9, AP100, 102, 200: Release 1.2.9.14, AP120, 320, 322, 420:,Release 8.3.0-657, Non-Cloud (GWC mode) | 2017-10-17 | 2017-10-17 |  |
| webOS | No Known Official Response | Also see entry ConnMan | 2017-10-17 | 2017-10-20 |  |
| WiFi Alliance | [LINK](https://www.wi-fi.org/security-update-october-2017) | Users should refer to their Wi-Fi device vendor’s website or security advisories to determine if their device has been affected and has an update available. As always, Wi-Fi users should ensure they have installed the latest recommended updates from device manufacturers. | 2017-10-16 | 2017-10-16 |  |
| Xfinity | No Known Official Response | N/A | 2017-10-17 | 2017-10-17 |  |
| Xiaomi | [LINK](http://en.miui.com/thread-954223-1-1.html) | MIUI Beta 9 v7.10.19 for some of the [mobile devices](ANDROID_S-Z.md) released.  | 2017-10-22 | 2017-10-22 | 2017-07-28 |2
| Xirrus | [LINK](https://www.xirrus.com/vulnerability-statements/) | As soon as the patch is released, it will be made available through the Xirrus Support Community. | 2017-10-17 | 2017-10-17 |  |
| Yamaha | No Known Official Response | N/A | 2017-11-12 | 2017-10-16 |  |
| Yi (Xiaomi) | No Known Official Response | "Waiting on a reply" | 2017-10-17 | 2017-10-17 |  |
| Zoom Telephonics | No Known Official Response  | sells amongst other Routers and Access Points; [some of them](https://github.com/kristate/krackinfo/issues/167) may also run as supplicants | 2017-11-12 | 2017-11-12 |  |
| ZTE | No Known Official Response | Also see entry KPN | 2017-10-17 | 2017-10-20 |  |
| ZyXEL | [LINK](http://www.zyxel.com/support/announcement_wpa2_key_management.shtml) | N/A | 2017-10-16 | 2017-10-16 | 28 Aug 2017 |
