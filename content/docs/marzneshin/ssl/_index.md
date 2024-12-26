---
title: SSL  
weight: 3  
---

In this guide, you'll learn how to use `acme.sh` to obtain a free SSL certificate.

{{% steps %}}

### 1. Install acme

First, install the `acme.sh` tool by running the following command:

```bash
curl https://get.acme.sh | sh
```

### 2. Set up Email

Next, register your email for notifications:

```bash
acme.sh --register-account -m your_email@example.com
```

### 3. Obtain SSL Certificate

To obtain an SSL certificate for your domain(s), use the following commands. Below is how to obtain a certificate for both a single and multiple domains:

{{< tabs items="Single,Multiple" >}}

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --issue --standalone -d yourdomain.com
```

{{< /tab >}}  

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --issue --standalone -d yourdomain.com -d example.com
```

{{< /tab >}}  

{{< /tabs >}}

### 4. Install the Certificate

After obtaining the certificate, install it in the appropriate directory. Use the following commands for different installations:

{{< tabs items="Marzneshin,Marznode" >}}

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --install-cert -d yourdomain.com \
--cert-file /var/lib/marzneshin/yourdomain/fullchain.pem \
--key-file /var/lib/marzneshin/yourdomain/privkey.pem
```

{{< /tab >}}  

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --install-cert -d yourdomain.com \
--cert-file /var/lib/marznode/yourdomain/fullchain.pem \
--key-file /var/lib/marznode/yourdomain/privkey.pem
```

{{< /tab >}}  

{{< /tabs >}}

### 5. Auto-Renewal

To ensure automatic renewal of your SSL certificate, install a cron job by running:

```bash
~/.acme.sh/acme.sh --install-cronjob
```

{{% /steps %}}