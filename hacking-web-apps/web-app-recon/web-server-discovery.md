# Web Server Discovery

After getting a list of domains, you usually want to discovery interesting servers. Following is a guide to automatically discover web servers.

## httprobe

After getting a list of subdomains, you can check if they are HTTP servers by running `httprobe`

<pre class="language-shell"><code class="lang-shell"><strong># Probe everything within amass.txt, with additional ports 8080, 8443, 3000, and 3443
</strong>cat amass.txt | httprobe -p http:8080 -p https:8443 -p http:3000 -p https:3443 --prefer-https > httprobe.txt
</code></pre>
