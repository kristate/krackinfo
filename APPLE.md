# KRACK and Apple

## First Response
The first unofficial reaction by Apple was via [Twitter](https://twitter.com/reneritchie/status/919988216501030914) on 2017-10-18.

## Patch Overview
On 2017-10-31 and 2017-11-01, Apple started to roll out first official final releases containing corrections for KRACK. Find below a table describing the current known status of corrections available.

| Affected CVE                                                      | iOS     | OS X/macOS   | tvOS    | watchOS |
|-------------------------------------------------------------------|---------|--------------|---------|---------|
| [CVE-2017-13077](https://nvd.nist.gov/vuln/detail/CVE-2017-13077) | 10.3.1 not affected<sup>1</sup><br />others: unknown | fixed with [10.13.1 and 10.12.6 and 10.11.6](https://support.apple.com/en-us/HT208221) | unknown | unknown |
| [CVE-2017-13078](https://nvd.nist.gov/vuln/detail/CVE-2017-13078) | 10.3.1 is affected<sup>2</sup><br />others: unknown | fixed with [10.13.1 and 10.12.6 and 10.11.6](https://support.apple.com/en-us/HT208221) | unknown | unknown |
| [CVE-2017-13079](https://nvd.nist.gov/vuln/detail/CVE-2017-13079) | 10.3.1 is affected<sup>2</sup><br />others: unknown | 10.9.5 and 10.12.? are affected<sup>2</sup><br />others: unknown | unknown | unknown |
| [CVE-2017-13080](https://nvd.nist.gov/vuln/detail/CVE-2017-13080) | 10.3.1 is affected<sup>2</sup><br />fixed with [11.1](https://support.apple.com/de-de/HT208222) <br />e.g. iPhone 7 and later product versions, iPad Pro 9.7-inch (early 2016) and later product versions<br />others: unknown | fixed with [10.13.1 and 10.12.6 and 10.11.6](https://support.apple.com/en-us/HT208221) | fixed with [11.1](https://support.apple.com/de-de/HT208219)<br />e.g. Apple TV 4k | fixed with [4.1](https://support.apple.com/de-de/HT208220)<br />e.g. Watch Series 1 and 2 |
| [CVE-2017-13081](https://nvd.nist.gov/vuln/detail/CVE-2017-13081) | 10.3.1 is affected<sup>2</sup><br />others: unknown | 10.9.5 and 10.12.? are affected<sup>2</sup><br />others: unknown | unknown | unknown |
| [CVE-2017-13082](https://nvd.nist.gov/vuln/detail/CVE-2017-13082) | unknown | unknown | unknown | unknown |
| [CVE-2017-13084](https://nvd.nist.gov/vuln/detail/CVE-2017-13084) | unknown | unknown | unknown | unknown |
| [CVE-2017-13086](https://nvd.nist.gov/vuln/detail/CVE-2017-13086) | unknown | unknown | unknown | unknown |
| [CVE-2017-13087](https://nvd.nist.gov/vuln/detail/CVE-2017-13087) | unknown | unknown | unknown | unknown |
| [CVE-2017-13088](https://nvd.nist.gov/vuln/detail/CVE-2017-13088) | unknown | unknown | unknown | unknown |

A cell being filled with statement "unknown" indicates that as of writing there is no information available and thus any of the following cases may hold true:

* The corresponding software is not affected by this attack at all.
* The corresponding software is affected, but the vendor did not detect this yet.
* The corresponding software is affected, the vendor is working on a solution, but did not release any patch yet.
* The corresponding software is affected, the vendor has already provided a patch in the meantime, but it is not listed in the table above.


## Footnotes
| Footnote | Comment |
|----------|------------------------------------------------------------------------------|
| 1        | Mentioned version not affected based on a statement of the [original paper by Marthy Vanhoef](https://papers.mathyvanhoef.com/ccs2017.pdf), Table 1 |
| 2        | Mentioned version is known to be affected based on a statement of the [original paper by Marthy Vanhoef](https://papers.mathyvanhoef.com/ccs2017.pdf), Table 1 |
