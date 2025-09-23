---

title: phpmyadmin  
weight: 6  

---

`phpMyAdmin` یک ابزار قدرتمند و کاربرپسند برای مدیریت دیتابیس‌های MySQL/MariaDB از طریق رابط وب است. این ابزار به شما امکان می‌دهد تا کوئری‌ها اجرا کنید، جداول را مدیریت کنید، و تنظیمات دیتابیس را به‌راحتی تغییر دهید. برای راه‌اندازی `phpMyAdmin` در مرزنشین، مراحل زیر را دنبال کنید.

{{% steps %}}

### ویرایش فایل Docker Compose

```bash
nano /etc/opt/marzneshin/docker-compose.yml
```

### افزودن سرویس phpMyAdmin

توجه داشته باشید:  
- **فاصله‌ها** در فایل YAML بسیار مهم هستند.  
- می‌توانید **پورت‌ها** را بر اساس نیاز خود تغییر دهید.  

```yaml
  phpmyadmin:
    image: phpmyadmin/phpmyadmin:latest
    restart: always
    env_file: .env
    network_mode: host
    environment:
      PMA_HOST: 127.0.0.1
      PMA_PORT: 3306
      APACHE_PORT: 8010
      UPLOAD_LIMIT: 1024M
    depends_on:
      - db
```

### ریستارت سرویس مرزنشین

```bash
marzneshin restart
```

اکنون `phpMyAdmin` آماده است و می‌توانید با وارد کردن آدرس `http://IP:PORT` در مرورگر خود، به صفحه‌ی مدیریت آن دسترسی پیدا کنید. از یوزرنیم `root` و پسورد دیتابیس خود برای ورود استفاده کنید.

{{< callout type="warning" >}}

⚠️ **هشدار:**  
لطفاً در دیتابیس خود تغییراتی اعمال نکنید و یا پیش از اعمال هرگونه تغییر، حتماً یک نسخه‌ی پشتیبان (بکاپ) تهیه کنید.

{{< /callout >}}

{{% /steps %}}