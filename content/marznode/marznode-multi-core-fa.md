---
title: "فعال‌سازی هسته‌های مرزنود"
---

___
  
### در این صفحه نحوه پیکربندی و راه‌اندازی هسته‌های زیر توضیح داده می‌شود

{{% steps %}}

### **Xray**  
### **hysteria2**
### **SingBox**  
### **جزئیات‌تکمیلی**

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
  
___ پایان ___

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

___ پایان ___


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

  ___ پایان ___


### جزئیات‌تکمیلی :

{{% /steps %}}

 {{% details title="جزئیات‌تکمیلی"closed="true" %}}

## متغیرهای عمومی و کاربرد آن‌ها

{{% steps %}}

### True و False
در متغیرهای تنظیمات، مقادیر `True و False` برای کنترل وضعیت ویژگی‌ها و سرویس‌ها استفاده می‌شوند:
* True: برای فعال‌سازی ویژگی یا سرویس استفاده می‌شود.
* False: برای غیرفعال‌سازی ویژگی یا سرویس استفاده می‌شود.
- اگر نیاز به فعال کردن یک قابلیت دارید، مقدار آن متغیر را به `True` تغییر دهید.
- اگر قصد غیرفعال کردن آن قابلیت را دارید، مقدار را به `False` تنظیم کنید.

___

### DEBUG
* این متغیر برای روشن یا خاموش کردن حالت اشکال‌زدایی `(Debug Mode)` به کار می‌رود.
  - ```bash
      DEBUG: "True"
      ```
* True: فعال‌سازی حالت اشکال‌زدایی. اطلاعات بیشتری برای بررسی خطاها و مشکلات نمایش داده می‌شود.
* False: غیرفعال‌سازی حالت اشکال‌زدایی. سیستم تنها اطلاعات حیاتی را نمایش می‌دهد.

___

### AUTH_GENERATION_ALGORITHM

* این متغیر مشخص می‌کند که چه الگوریتمی برای تولید هش یا کلید احراز هویت استفاده شود.

    - ```bash
      AUTH_GENERATION_ALGORITHM: "xxh128"
       ```
* xxh128: نسخه 128 بیتی الگوریتم xxHash که بسیار سریع و مناسب برای داده‌های بزرگ یا کاربردهایی است که به سرعت بالا و احتمال برخورد هش بسیار کم نیاز دارند.

* sha256: یکی از الگوریتم‌های استاندارد و ایمن برای تولید هش، مناسب برای کاربردهای حساس امنیتی.

* md5: الگوریتم قدیمی‌تر که با وجود سرعت بالا، به دلیل ضعف امنیتی برای کاربردهای حساس توصیه نمی‌شود.

> xxh128: اگر به سرعت بالا و کارایی نیاز دارید، این مقدار ایده‌آل است.

> sha256: برای کاربردهایی که امنیت بالاتر از سرعت اهمیت دارد، پیشنهاد می‌شود.

> md5: فقط در موارد غیرحساس استفاده شود.

___


### مدیریت سرویس `XRAY` در مرزنشین

##### متغیرها و توضیحات:

> متغیری برای فعال یا غیرفعال کردن سرویس XRAY.
> * `XRAY_ENABLED:` `"True" / "False"`

> مسیر فایل اجرایی XRAY که برای راه‌اندازی این سرویس استفاده می‌شود.
> * `XRAY_EXECUTABLE_PATH:` `"/usr/local/bin/xray"`

>   مسیر فایل‌های منابع و کتابخانه‌های مرتبط با XRAY.
> * `XRAY_ASSETS_PATH:` `"/usr/local/lib/xray"`

>  متغیری برای فعال کردن یا تغییر نوع جریان (Flow) در پیکربندی VLESS با پشتیبانی از ویژگی Reality.
> * `XRAY_VLESS_REALITY_FLOW:` `"xtls-rprx-vision"`

> مشخص می‌کند که آیا XRAY باید در صورت خطا به صورت خودکار مجدداً راه‌اندازی شود یا خیر.
> * `XRAY_RESTART_ON_FAILURE:` `"True" / "False"`

> فاصله زمانی بین تلاش‌های مجدد برای راه‌اندازی XRAY در صورت بروز خطا.
> `XRAY_RESTART_ON_FAILURE_INTERVAL: "0"`
>
> راهنمای استفاده: اگر به تلاش مجدد نیاز دارید، مقدار مشخصی را به ثانیه وارد کنید.

___

### مدیریت سرویس Hysteria در مرزنشین

##### متغیرها و توضیحات:

> متغیری برای فعال یا غیرفعال کردن سرویس Hysteria.
> * `HYSTERIA_ENABLED:` `"True" / "False"`

> مسیر فایل اجرایی Hysteria که برای راه‌اندازی این سرویس استفاده می‌شود.
> * `HYSTERIA_EXECUTABLE_PATH:` `"/usr/bin/hysteria"`

> مسیر فایل تنظیمات Hysteria که شامل پیکربندی‌های کلیدی سرویس است.
> * `HYSTERIA_CONFIG_PATH:` `"/var/lib/marznode/hysteria.yaml"`

___

### مدیریت سرویس Sing-Box در مرزنشین

##### متغیرها و توضیحات:

> متغیری برای فعال یا غیرفعال کردن سرویس Sing-Box.
> * `SING_BOX_ENABLED:` `"True" / "False"`

> مسیر فایل اجرایی Sing-Box که برای اجرای این سرویس استفاده می‌شود.
> * `SING_BOX_EXECUTABLE_PATH:` `"/usr/bin/sing-box"`

> مسیر فایل تنظیمات Sing-Box که شامل پیکربندی‌های کلیدی سرویس است.
> * `SING_BOX_CONFIG_PATH:` `"/var/lib/marznode/sing-box.json"`

> مشخص می‌کند که آیا Sing-Box باید در صورت خطا به صورت خودکار مجدداً راه‌اندازی شود یا خیر.
> * `SING_BOX_RESTART_ON_FAILURE:` `"True" / "False"`

> فاصله زمانی بین تلاش‌های مجدد برای راه‌اندازی Sing-Box در صورت بروز خطا.
> * `SING_BOX_RESTART_ON_FAILURE_INTERVAL: "0"`
>
> راهنمای استفاده: در صورت نیاز به تلاش مجدد، مقدار مشخصی (بر حسب ثانیه) را وارد کنید.





 
 {{% /steps %}}











    






{{% /details %}}


