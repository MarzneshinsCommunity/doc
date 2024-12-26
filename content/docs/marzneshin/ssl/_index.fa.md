---
title: سرتیفیکیت  
weight: 3  
---

در این راهنما، شما یاد خواهید گرفت که چگونه از ابزار `acme.sh` برای دریافت گواهی SSL رایگان استفاده کنید.

{{% steps %}}

### 1. نصب acme

ابتدا باید ابزار `acme.sh` را نصب کنید. برای این کار دستور زیر را اجرا کنید:

```bash
curl https://get.acme.sh | sh
```

### 2. تنظیم ایمیل

بعد از نصب، برای دریافت اعلان‌های گواهی‌ها، ایمیل خود را ثبت کنید:

```bash
~/.acme.sh/acme.sh --register-account -m your_email@example.com
```

### 3. دریافت گواهی SSL

برای دریافت گواهی SSL برای دامنه‌های مختلف، از دستورهای زیر استفاده کنید. در اینجا نحوه دریافت گواهی برای دامنه‌های تکی و چندگانه آورده شده است:

{{< tabs items="تکی,مولتی" >}}

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

### 4. نصب گواهی

بعد از دریافت گواهی، آن را در مسیر مناسب نصب کنید. برای نصب گواهی در دایرکتوری‌های مختلف، از دستورات زیر استفاده کنید:

{{< tabs items="مرزنشین,مرزنود" >}}

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --install-cert -d yourdomain.com \
--cert-file /var/lib/marzneshin/certs/yourdomain/fullchain.pem \
--key-file /var/lib/marzneshin/certs/yourdomain/privkey.pem
```
{{< /tab >}}  

{{< tab >}}  
```bash
~/.acme.sh/acme.sh --install-cert -d yourdomain.com \
--cert-file /var/lib/marznode/certs/yourdomain/fullchain.pem \
--key-file /var/lib/marznode/certs/yourdomain/privkey.pem
```
{{< /tab >}}  

{{< /tabs >}}

### 5. تمدید خودکار گواهی

برای اطمینان از تمدید خودکار گواهی SSL، دستور زیر را برای نصب کرون‌جاب (job cron) اجرا کنید:

```bash
~/.acme.sh/acme.sh --install-cronjob
```

{{% /steps %}}