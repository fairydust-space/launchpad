---
title: "FAQ"
date: 2021-01-06T18:00:00Z
draft: false
---

## Frequently Asked Questions

{{% notice info %}}
If your question hasn't been answered yet, please [contact us]({{%relref "contact.md" %}})! :-)
{{% /notice %}}

### Which data do you keep about your users?

We only keep the data required to provide the service. We do not keep any data on top of that.

### Does the server only run “free software”?

That depends on which aspect of “free” you're referring to.

#### Free as in gratis (referring to cost)

Yes, there are no license fees imposed by the software we use.

#### Free as in public (referring to availability)

Yes, all the software we use is publicly available.

#### Free as in libre or OpenSource (referring to the license)

These licenses are used by the software packages used on this server. This includes build- and runtime dependencies.

- APACHE20
- ART10
- BSD2CLAUSE
- BSD3CLAUSE
- BSD4CLAUSE
- CDDL
- FTL
- GPLv1+
- GPLv2
- GPLv2+
- GPLv3
- GPLv3+
- ICU
- IJG
- LGPL21+
- Libpng
- LLVM
- LLVM2
- MIT
- MPL11
- MPL20
- PD
- PostgreSQL
- PSFL
- REGEX
- TclTk
- TRIO
- ZLIB

To learn more about them please check the [Open Source Initiative](https://opensource.org/licenses/category)'s or the [Free Software Foundation](https://www.gnu.org/licenses/license-list.html)'s license lists.

#### Free as in boot process (referring to the firmware of the hardware we run)

No, this hardware is using a proprietary BIOS by “American Megatrends Inc.” (AMI BIOS).

### Which country is the server located in?

#### Matrix Server, Webservices

Germany, Europe (EU)

#### Mail Server

Austria, Europe (EU)

### Are the server disks encrypted?

No. This server is configured to boot through to service availability without requiring user interaction.

### Is presence enabled on this Matrix instance?

Presence is disabled on fairydust.space for privacy and performance reasons.

### Do you support 3rd party web interfaces?

Yes, you can use any Matrix webinterface hosted by a third party or yourselves with the fairydust.space Matrix server. Depending on your interface you may need to manually tell it how to connect to our homeserver running at `https://matrix.fairydust.space`. We do support client autodiscovery if the webinterface of your trust also supports it.

### Are you providing any publicly available bridges to other services?

We are not providing any bridges to other services. Since Matrix is a *federated* network, you are free to use bridges provided by other servers, provided these other services allow you to use them.
