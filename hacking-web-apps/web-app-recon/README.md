---
description: Discover assets to hack.
---

# Web App Recon

## Wordlists

You can't recon without wordlists :). So download these to your machine.

{% embed url="https://github.com/danielmiessler/SecLists" %}

[subdomain-discovery.md](subdomain-discovery.md "mention")

[web-server-discovery.md](web-server-discovery.md "mention")

[screenshot-web-pages.md](screenshot-web-pages.md "mention")

### masscan

Masscan can automatically run nmap scans on a list of IP addresses. It is quite useful when testing different stuff.

You must provide a list of IP addresses, you can get it from amass output, or use a tool like [https://www.infobyip.com/ipbulklookup.php](https://www.infobyip.com/ipbulklookup.php) to convert domain names to IPs.

Following command will scan top 1000 ports, which is usually pretty fast

```shell
sudo masscan -iL ips.txt --top-ports 1000 > output.txt
```

You can also scan all ports, but this would be quite slow

```shell
sudo masscan -iL ips.txt -p- > output.txt
```

## Content Discovery

### recursebuster

`recursebuster` is a really nice TUI tool for quickly scraping websites. You can do a quick scan without a wordlist for spider only.

```shell
recursebuster -iL urls.txt -o recursebuster.txt
```

Or you can also specify a wordlist to use the bruteforce mode

```shell
recursebuster -iL urls.txt -w wordlist.txt -o recursebuster.txt
```

## Vulnerability Scan

Some common vulnerabilities can be scanned

### corsy

{% embed url="https://github.com/s0md3v/Corsy" %}

Corsy is a tool you can use to check CORS misconfigurations, you must have a list of URLs to test.

```shell
python3 corsy.py -i urls.txt
```

## n8n Workflow

<figure><img src="../../.gitbook/assets/CleanShot 2023-01-10 at 16.55.27.png" alt=""><figcaption><p>n8n workflow for comprehansive scan</p></figcaption></figure>
