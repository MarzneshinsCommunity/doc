---
title: "فعال‌سازی هسته‌های مرزنود"
---

   
 ___
  
### در این صفحه نحوه پیکربندی و راه‌اندازی هسته‌های زیر توضیح داده می‌شود

{{% steps %}}

### **Xray**  
### **hysteria2**
### **SingBox**  

{{% /steps %}}
 ___


{{% steps %}}

### Xray  
* هنگامی که مرزنود را نصب میکنید هسته  بصورت پیش فرض نصب و فعال میشود و نیازی به تنظیمات اضافی برای این هسته نیست 

>#### برای غیرفعال کردن هسته ایکس‌ری متغییر زیرو رو مقدار دهی کنید 
>* `XRAY_ENABLED:` `"False"` / `"True"`
>    - ```bash
>        XRAY_ENABLED: "False"
>       ```
>
>
  
__

### hysteria2

{{< callout type="info" >}}

با استفاده از آموزش گرفتن [سرتیفیکیت برای مرزنود](mskksjssjnsn)برای نودتون سرت بگیرید و داخل اینباند هیستریا قرار بدید تا ران بشه هسته هیستریاتون

{{< /callout >}}

 {{% steps %}}

### دانلود فایل کانفیگ Hysteria2:
*  با دستور زیر فایل کانفیگ را دریافت و در مسیر مشخص ذخیره کنید
    - ```bash
         curl -L https://github.com/marzneshin/marznode/raw/master/hysteria.yaml > /var/lib/marznode/hysteria.yaml
       ```
### ویرایش فایل تنظیمات Marznode:
* ابتدا به دایرکتوری Marznode بروید و فایل تنظیمات Docker Compose را باز کنید
    - ```bash
       cd marznode && nano compose.yml
      ```
### ویرایش فایل تنظیمات نود `لوکال`(local) پنل:
* برای نود `لوکال`، فایل زیر را ویرایش کنید
    - ```bash
      nano /etc/opt/marzneshin/docker-compose.yml
      ```

### افزودن متغیرهای زیر به فایل داکر:

  ```bash
HYSTERIA_CONFIG_PATH: "/var/lib/>marznode/hysteria.yaml"  
HYSTERIA_ENABLED: "True"  
 ```

### ریستارت Marznode:
* پس از اعمال تغییرات، سرویس Marznode را ریستارت کنید:

    - ```bash
      docker compose down && docker compose up -d
      ```
### ریستارت نود لوکال پنل Marzneshin:
* برای نود لوکال از دستور زیر استفاده کنید
    
     - ```bash
       marzneshin restart
        ```


> #### برای غیرفعال کردن هسته هیستریا متغییر زیرو مقدار دهی کنید 
> 
> * `HYSTERIA_ENABLED:` `"False"` / `True`
>    - ```bash
>       HYSTERIA_ENABLED: "False"  
>      ```
>
   {{% /steps %}}

__


### Sing-Box
 {{% steps %}}

 ### دانلود فایل کانفیگ sing-box
  * با دستور زیر فایل کانفیگ را دریافت و در مسیر مشخص ذخیره کنید

     - ```bash
         curl -L https://raw.githubusercontent.com/MarzneshinsCommunity/files/refs/heads/main/sing-box.json > /var/lib/marznode/sing-box.json
         ```

### ویرایش فایل تنظیمات Marznode:
* ابتدا به دایرکتوری Marznode بروید و فایل تنظیمات Docker Compose را باز کنید
    - ```bash
       cd marznode && nano compose.yml
        ```
### ویرایش فایل تنظیمات نود `لوکال`(local) پنل:
*  برای نود (local)`لوکال`، فایل زیر را ویرایش کنید
    - ```bash
       nano /etc/opt/marzneshin/docker-compose.yml
        ```

### افزودن متغیرهای زیر به فایل داکر:
* ```bash
   SING_BOX_ENABLED: "True"
   SING_BOX_CONFIG_PATH: "/var/lib/marznode/sing-box.json"

   ```
### ریستارت Marznode:
* پس از اعمال تغییرات، سرویس Marznode را ریستارت کنید
    - ```bash
       docker compose down && docker compose up -d
        ```
### ریستارت نود لوکال پنل Marzneshin:
* برای نود لوکال از دستور زیر استفاده کنید:
    - ```bash 
       marzneshin restart
       ```
 >   #### برای غیرفعال کردن هسته سینگ‌باکس متغییر زیرو مقدار دهی کنید 
 >  * `SING_BOX_ENABLED:` `"False"` / `"True"`
 >       - ```bash
 >           SING_BOX_ENABLED: "False"
 >           ```



  {{% /steps %}}
{{% /steps %}}
