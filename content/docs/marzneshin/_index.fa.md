---  
title: نصب  
toc: False  
weight: 1  
---  

برای شروع، به یک دستگاه لینوکسی نیاز دارید. مرزنشین از هر دو معماری ARM و x86 پشتیبانی می‌کند. Docker نیز پشتیبانی می‌شود. مرزنشین از پایگاه‌های داده زیر پشتیبانی می‌کند. برای تنظیمات کوچک، **SQLite** مناسب است و برای کانفیگ‌های بزرگ‌تر، **MariaDB** توصیه می‌شود. 

{{< tabs items="mariadb,mysql,sqlite" >}}  

{{< tab >}}  
```bash  
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mariadb  
```  
{{< /tab >}}  
{{< tab >}}  
```bash  
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install --database mysql  
```  
{{< /tab >}}  
{{< tab >}}  
```bash  
sudo bash -c "$(curl -sL https://github.com/marzneshin/Marzneshin/raw/master/script.sh)" @ install  
```  
{{< /tab >}}  

{{< /tabs >}}  

{{< callout type="warning" >}}  
برای نصب آخرین نسخه **nightly** (حالت توسعه)، از فلگ `--nightly` استفاده کنید.  
{{< /callout >}}  

پس از اتمام نصب:  

- لاگ‌ها نمایش داده خواهند شد که با فشار دادن `Ctrl+C` می‌توانید مشاهده آن‌ها را متوقف کنید.  
- فایل تنظیمات در مسیر `/etc/opt/marzneshin/.env` قرار می‌گیرد.  
- فایل‌های داده در مسیر `/var/lib/marzneshin` ذخیره می‌شوند.  
- برای دسترسی به داشبورد مرزنشین، مرورگر وب خود را باز کرده و به آدرس `http://<SERVER_IP>:8000/dashboard/` بروید.  

در مرحله بعد، یک کاربر ادمین با دسترسی سودو برای ورود به داشبورد مرزنشین ایجاد کنید:  

```bash  
marzneshin cli admin create --sudo  
```  

همین! اکنون می‌توانید با استفاده از اطلاعات لاگین خود وارد داشبورد شوید.  

برای مشاهده پیام راهنما، دستور زیر را اجرا کنید:  

```bash  
marzneshin --help  
```