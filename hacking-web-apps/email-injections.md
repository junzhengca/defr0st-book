---
description: >-
  Email injections can be dangerous as it will allow attackers to inject
  arbitrary data into an email that you send.
---

# Email Injections

## HTML Injection

If the application is not sanitizing HTML content correctly before sending out emails. An email injection attack can occur.

The easiest injection would be to use `<style>` tags to hide the original content.

```
<style>*{color: transparent;} #bill{color: #000;} #bill a{color: blue;}</style> <p id=\"bill\">Pay your bill now, <a href=\"https://localhost/malicious_site\">pay now</a>. This is required</p>
```

However, modern web-based email clients doesn't support `<style>` tags. Following are a list of desktop / mobile clients that I have tested which supports CSS style.

* macOS native email client
* iOS native email client

If you can control something at the top of the email message, maybe they are sending `Hi, {name}`. Then you can try adding a lot of line breaks after your payload to push the original content down.
