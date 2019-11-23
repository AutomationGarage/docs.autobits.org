---
id: WebInterface
title: Web Interface
sidebar_label: Web Interface
---

enables AutoBits to have user interface.

The user interface provides customizable dashboards and access to settings, that let you fine-tune AutoBits for your application.

The user interface is web-based and opens in a web browser. It is also accessible over a network when configured appropriately.

These properties define on which network interface and port the UI is made accessible:
```ini
hostOrIpAddress = localhost
uiPort = 8090
```

- `hostOrIpAddress` - can be set to a hostname, an IP address or special keyword `all`. When set to 'localhost' the UI can only be opened on the same computer. When set to 'all' the UI can be accessed via network on all network interfaces.
- `uiPort` - port number to use

#### HTTPS

To enable HTTPS, configure path to SSL certificate and password:

```ini
sslCertificatePath = "path\to\certificate.pfx"
sslCertificatePassword = 1234
```