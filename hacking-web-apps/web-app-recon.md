---
description: Discover assets to hack.
---

# Web App Recon

## Wordlists

You can't recon without wordlists :). So download these to your machine.

{% embed url="https://github.com/danielmiessler/SecLists" %}

## Subdomain Discovery

For many bug bounty programs, `*.company.com` is included within the scope. So it is a great idea to enumerate through all subdomains.

### amass

`amass` is a great tool to enumerate domains. Usually I use this command:

```shell
amass enum -v -config amass.ini -d company.com -dir amass4company
```

Replace `company` with the company you are targeting. This command will automatically scan the domain provided and store the result within a directory called `amass4company`.

{% hint style="info" %}
`amass` can be very slow depending on various factors: wordlist provided if brute-forcing / if doing recursive brute-forcing / DNS resolution speed.

It is recommended that you use a cloud VM along with `screen` when doing scans.
{% endhint %}
