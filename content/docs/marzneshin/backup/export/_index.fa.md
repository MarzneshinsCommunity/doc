---
title: اکسپورت اطلاعات
weight: 1
---

{{< tabs items="SQLite, MariaDB, MySQL" >}}

{{< tab >}}  

### بکاپ فایل‌ها

اطلاعات مرزنشین شما در دایرکتوری‌های زیر ذخیره می‌شود:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< /tab >}}  

{{< tab >}}  


{{% steps %}}

### بکاپ فایل‌ها
اطلاعات مرزنشین شما در دایرکتوری‌های زیر ذخیره می‌شود:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< callout type="warning" >}}
**مهم:** دایرکتوری `/var/lib/marzneshin/mysql` نباید ذخیره شود. اگر به اشتباه آن را ذخیره کرده‌اید، قبل از ادامه حذفش کنید.
{{< /callout >}}

### نصب ابزارهای مورد نیاز
برای اطمینان از نصب ابزارهای لازم، دستور زیر را اجرا کنید:

```bash
docker exec -it marzneshin-db-1 bash -c "apt update && apt install -y mariadb-client"
```

### تعریف رمز دیتابیس
رمز دیتابیس را با دستور زیر تعریف کنید:

```bash
export MARZDBPASS="pass"
```

### بکاپ از دیتابیس
برای گرفتن بکاپ از دیتابیس دستور زیر را اجرا کنید:

```bash
docker exec -i marzneshin-db-1 mariadb-dump -u root -p$MARZDBPASS marzneshin > /var/lib/marzneshin/marzneshin-$(date +%F).sql
```

{{% /steps %}}

فایل بکاپ با تاریخ روز در مسیر `/var/lib/marzneshin` ذخیره خواهد شد.

{{< /tab >}}  

{{< tab >}}  

{{% steps %}}

### بکاپ فایل‌ها
اطلاعات مرزنشین شما در دایرکتوری‌های زیر ذخیره می‌شود:

- `/etc/opt/marzneshin/`
- `/var/lib/marzneshin/`
- `/var/lib/marznode/`

{{< callout type="warning" >}}
**مهم:** دایرکتوری `/var/lib/marzneshin/mysql` نباید ذخیره شود. اگر به اشتباه آن را ذخیره کرده‌اید، قبل از ادامه حذفش کنید.
{{< /callout >}}

### نصب ابزارهای مورد نیاز
برای اطمینان از نصب ابزارهای لازم، دستور زیر را اجرا کنید:

```bash
docker exec -it marzneshin-db-1 bash -c "apt update && apt install -y mysql-client"
```

### تعریف رمز دیتابیس
رمز دیتابیس را با دستور زیر تعریف کنید:

```bash
export MARZDBPASS="pass"
```

### بکاپ از دیتابیس
برای گرفتن بکاپ از دیتابیس دستور زیر را اجرا کنید:

```bash
docker exec -i marzneshin-db-1 mysqldump -u root -p$MARZDBPASS marzneshin > /var/lib/marzneshin/marzneshin-$(date +%F).sql
```

{{% /steps %}}

فایل بکاپ با تاریخ روز در مسیر `/var/lib/marzneshin` ذخیره خواهد شد.

{{< /tab >}}  

{{< /tabs >}}
