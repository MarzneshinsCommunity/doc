---
title: رمز دیتابیس  
weight: 2  
---


رمز پیش‌فرض دیتابیس‌های MariaDB و MySQL در مرزنشین `12341234` است. بعد از تهیه بکاپ از دیتابیس، برای تغییر رمز باید مراحل زیر را دنبال کنید.

{{% steps %}}

### 1. لاگین به دیتابیس

برای اعمال تغییرات، ابتدا باید به دیتابیس لاگین کنید. دستور مناسب برای هر دیتابیس را اجرا کنید:

{{< tabs items="mariadb,mysql" >}}

{{< tab >}}  
```bash  
docker exec -it marzneshin-db-1 mariadb -u root -p
```  
{{< /tab >}}  

{{< tab >}}  
```bash  
docker exec -it marzneshin-db-1 mysql -u root -p
```  
{{< /tab >}}  

{{< /tabs >}}

### 2. تغییر رمز دیتابیس

برای تغییر رمز، دستور زیر را اجرا کنید:

```sql
ALTER USER 'root'@'%' IDENTIFIED BY 'NEW PASSWORD';
FLUSH PRIVILEGES;
```

### 3. خروج از دیتابیس

برای خروج از دیتابیس، دستور زیر را دوبار اجرا کنید:

```bash
exit
```

### 4. ویرایش فایل داکر

برای تغییر رمز در فایل داکر، دستور زیر را اجرا کنید:

```bash
nano /etc/opt/marzneshin/docker-compose.yml
```

سپس موارد زیر را ویرایش کنید:

{{< tabs items="mariadb,mysql" >}}

{{< tab >}}  

```yaml
SQLALCHEMY_DATABASE_URL: "mariadb+pymysql://root:NEWPASSWORD@127.0.0.1/marzneshin"
MARIADB_ROOT_PASSWORD: "NEW PASSWORD" 
```  

{{< /tab >}}  

{{< tab >}}  

```yaml
SQLALCHEMY_DATABASE_URL: "mysql+pymysql://root:NEWPASSWORD@127.0.0.1/marzneshin"
MYSQL_ROOT_PASSWORD: "NEW PASSWORD" 
```  

{{< /tab >}}  

{{< /tabs >}}

### 5. ریستارت مرزنشین

برای اعمال تغییرات، مرزنشین را با دستور زیر ریستارت کنید:

```bash
marzneshin restart
```

با انجام این مراحل، رمز دیتابیس شما تغییر کرده است.

{{% /steps %}}
