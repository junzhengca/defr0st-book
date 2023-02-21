# Scanning Ports

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
