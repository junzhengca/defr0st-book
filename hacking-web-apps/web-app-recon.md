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

### findomain

Findomain offers a very fast way to enumerate subdomains. It uses various services and have the option to connect to a Postgresql server for continuous monitoring.

The most basic use of findomain is&#x20;

```shell
findomain -t domain.com -u output.txt
```

## httprobe

After getting a list of subdomains, you can check if they are HTTP servers by running `httprobe`

<pre class="language-shell"><code class="lang-shell"><strong># Probe everything within amass.txt, with additional ports 8080 and 8443
</strong><strong>cat amass.txt | httprobe -p http:8080 -p https:8443 --prefer-https > httprobe.txt
</strong></code></pre>

## masscan

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

## Screenshots

### EyeWitness

You can use [EyeWitness](https://github.com/FortyNorthSecurity/EyeWitness) to do mass screenshots of websites

```shell
./EyeWitness.py -f input.txt --web -d eyewitness-report
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

<figure><img src="../.gitbook/assets/CleanShot 2023-01-10 at 16.55.27.png" alt=""><figcaption><p>n8n workflow for comprehansive scan</p></figcaption></figure>
