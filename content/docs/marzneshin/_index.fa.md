---
title: مرزنشین
toc: False
weight: 1
---

برای شروع، به یک سرور لینوکس (هردستگاهی که توانایی اجرای داکر دارد) نیاز دارید.

{{< callout type="info" >}}
ما اوبونتو را به دلیل سهولت استفاده توصیه می‌کنیم، اگرچه مرزنشین می‌تواند بر روی هر توزیع لینوکس اجرا شود.
{{< /callout >}}

مرزنشین از هر دو معماری ARM و x86 پشتیبانی می‌کند. Docker نیز پشتیبانی می‌شود.

{{< callout type="info" >}}
نصب سریع:

```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install
```

پس از آن، یک ادمین ایجاد کنید:

```bash
marzneshin cli admin create --sudo
```

{{< /callout >}}

مرزنشین از پایگاه‌های داده زیر پشتیبانی می‌کند. SQLite برای تنظیمات کوچک ترجیح داده می‌شود، در حالی که MariaDB برای پردازش های بیشتر توصیه می شود.
{{< tabs items="mariadb,mysql,sqlite" >}}

{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mariadb
```{{< /tab >}}
{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mysql
```{{< /tab >}}
{{< tab >}}```bash
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install
```{{< /tab >}}

{{< /tabs >}}

{{< callout type="warning" >}}
برای نصب آخرین نسخه **nightly**، از فلگ `--nightly` استفاده کنید.
{{< /callout >}}

پس از اتمام نصب:

- شما لاگ‌ها را مشاهده خواهید کرد که می‌توانید با فشار دادن `Ctrl+C` مشاهده آن‌ها را متوقف کنید. فرآیند به طور عادی ادامه خواهد یافت.
- فایل پیکربندی در مسیر `/etc/opt/marzneshin/.env` قرار دارد (به صفحه [پیکربندی](/docs/configuration/marzneshin) مراجعه کنید).
- فایل‌های داده در مسیر `/var/lib/marzneshin` قرار خواهند گرفت، به عنوان مثال، پایگاه داده SQLite.
- شما می‌توانید به داشبورد مرزنشین با باز کردن یک مرورگر وب و رفتن به `http://<SERVER_IP>:8000/dashboard/` دسترسی پیدا کنید.

سپس، یک ادمین سودو برای ورود به داشبورد مرزنشین با استفاده از فرمان زیر ایجاد کنید:

```bash
marzneshin cli admin create --sudo
```

همین! شما می‌توانید با استفاده از این credentials به داشبورد خود وارد شوید.

برای مشاهده پیام راهنمای اسکریپت مرزنشین، فرمان زیر را اجرا کنید:

```bash
marzneshin --help
```
