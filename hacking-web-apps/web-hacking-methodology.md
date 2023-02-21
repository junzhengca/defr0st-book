---
description: >-
  This is the methodology I use when pentesting web applications. It is still in
  the works, so might lack some content as I slowly update.
---

# Web Hacking Methodology

## Stage 0. Recon

When testing web applications, one of the most things you need to do is recon.

### Figure out main features and note down initial observations

During this stage, we want to actually use the application, try to figure out what it can do, and note down some quick initial observations. For example

```
Main domain: app.com
  - Login
  - Sign up (can do social sign up using Google/Facebook)

Developer console: dev.app.com
  - OAuth through main application
  - Can create new applications
  - Can create apps that gets embeeded using iframes
  - API documentation api-doc.app.com
```

Of course, how to structure the note is completely up to you, it is just important to note down things as you go, so later you have a checklist of features to go through.

### Discover alternate assets & domain enumeration

This is probably the easiest part, you can try to scan for alternate assets such as different directories, or do domain enumeration.

{% content-ref url="web-app-recon/" %}
[web-app-recon](web-app-recon/)
{% endcontent-ref %}

### Discover API endpoints

You will want to try to figure out how the API works, there are a lot of ways to do this. Just remember, it is very important to take notes!
