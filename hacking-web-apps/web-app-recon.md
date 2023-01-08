---
description: Discover assets to hack.
---

# Web App Recon

## Subdomain Discovery

For many bug bounty programs, `*.company.com` is included within the scope. So it is a great idea to enumerate through all subdomains.

### amass

`amass` is a great tool to enumerate domains. Usually I use this command:

```shell
amass enum -v -config amass.ini -d company.com -dir amass4company
```

Replace `company` with the company you are targeting.&#x20;
