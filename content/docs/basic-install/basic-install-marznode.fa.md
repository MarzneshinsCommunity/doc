---
title: مرزنود
---


# **مرزنود**


### پیش‌نیازها
  * *docker*
  * *docker compose*



{{< callout type="info" >}}

 اطمینان حاصل کنید که داکر نصب شده است.
 
 برای نصب داکر از دستور زیر استفاده کنید:
 
 ``` 
 curl -fsSL https://get.docker.com | sh 
 ```
  {{< /callout >}}

  

{{% steps %}}

### تنظیم گواهی‌نامه (Certificate)

   * ابتدا دایرکتوری مورد نیاز را ایجاد کنید:


    
     - ```
        mkdir -p /var/lib/marznode/
       ```


 * سپس گواهی‌نامه خود را از تنظیمات مرزنشین دریافت کرده و در مسیر زیر قرار دهید:

    - ```
      nano /var/lib/marznode/client.pem
      ```



### تنظیم کانفیگ Xray

  * </sub>کانفیگ اولیه Xray برای نود را از مخزن مرزنود دریافت کنید (بعداً می‌توانید از طریق داشبورد آن را تغییر دهید):<sub>

       
    -  ```
       curl -L https://github.com/marzneshin/marznode/raw/master/xray_config.json > /var/lib/marznode/xray_config.json
       ```



### دریافت مرزنود

      
  *  برای کلون کردن مخزن مرزنود:

     - 
        ```
         git clone https://github.com/marzneshin/marznode
         cd marznode 
         ```
        
                    
### اجرای کانتینر


  * برای اجرای نود، دستور زیر را اجرا کنید:

     
    -
       ```
       docker compose -f ./compose.yml up -d 
       ```

{{% /steps %}}
  
{{< callout type="warning" >}}
   
  ### تنظیمات پیش‌فرض پورت
 

  * پورت پیش‌فرض برای اتصال نود به پنل ` 53042 ` است. اطمینان حاصل کنید که تنظیمات شما با این پورت همخوانی داشته باشد، مگر اینکه تغییرات دیگری داده باشید.

  * در صورتی که نیاز به تغییر پورت دارید، هم در تنظیمات نود و هم پنل این تغییر را اعمال کنید.

{{< /callout >}}


## مراحل تغییر پورت مرزنود

{{% steps %}}

### وارد دایرکتوری مرزنود شوید و فایل ` compose.yml ` را باز کنید:

   * ```
     cd marznode
     nano compose.yml
     ```

### متغیر زیر را اضافه کنید:

   * ```
       SERVICE_PORT: "53043"
     ```

   تغییرات را با ترکیب کلیدهای ` Ctrl + X `سپس ` Y ` و ` Enter ` ذخیره کنید و از ویرایشگر خارج شوید.


### ری‌استارت کردن داکر :

   * ```
     docker compose down && docker compose up -d
       ```
{{% /steps %}}


{{< callout emoji="💠" >}}


  [راه‌اندازی هسته‌های مرزنود - همین حالا شروع کنید](/marznode/marznode-multi-core-fa/)


  {{< /callout >}}