---
title: نصب نود با یک دستور
weight: 3
---

 {{< callout type="info" >}}
  ### پیش نیاز ها 
   * *اکانت گیت هاب*
   * *سرتیفیکیت پنل client.pem*
   * *محتوای فایل xray_config.json*
   * *محتوای فایل compose.yml*
  {{< /callout >}}


{{% steps %}}

### آماده سازی پیش نیاز ها 

 {{% steps %}}
  ### وارد گیت هابتون بشید روی پروفایلتون بزنید، بالا، گوشه صفحه ،دست راست ، سپس گذینه Your gists انتخاب کنید.
  * سپس 
    - سرتیفیکیت پنل client.pem
    - محتوای فایل xray_config.json
    - محتوای فایل compose.yml
  - این فایل هارو اینجا بزاریم و لینک **Raw** بگیریم .

  ### وسط صفحه گذینه سبز رنگ Create a gist بزنید .
   * داخل قسمت Filename including extension... اسم فایل رو مینویسید.
   - مثلا panel-main-client.pem 
   - سپس قسمت Enter file contents here سرتیفیکیت همین پنلو میزارید و در اخر گزینه سبز رنگ پایین Create secret gist رو میزنید.
   - حالا لینک مستقیم شما آمادس ، گوشه صفحه Raw نوشته میزنید و لینک رو کپی میکنید .

  ### سپس همین مراحلو برای فایل های زیر انجام میدید و لینک **Raw** این دوتارو هم میگیرید.

  * محتوای فایل xray_config.json
  * محتوای فایل compose.yml

 {{% /steps %}}

### جمع اوری دستوراتی که باید اجرا شوند 

{{% details title=" دستورات" closed="true" %}} 


> #### لینک های **Raw** که در مراحل قبل گرفتید رو باید جای گذاری کنید بجای :
> - your Raw link/client.pem
> - your Raw link/xray_config.json
> - your Raw link/compose.yml


 * اپدیت سرور 
    
   ```bash
   apt-get update -y
   ```

 * نصب داکر

  ```bash
  curl -fsSL https://get.docker.com | sh
  ```

 * ساخت دایرکتوری مرزنود
  ```bash
  mkdir -p /var/lib/marznode/
  ```

 * کلون کردن مرزنود 
  ```bash
  git clone https://github.com/marzneshin/marznode
  ```
 * دانلود سرتیفیکیت پنل client.pem
  ```bash
  curl -L your Raw link/client.pem > /var/lib/marznode/client.pem
  ```

 * دانلود محتوای فایل xray_config.json
  ```bash
  curl -L your Raw link/xray_config.json > /var/lib/marznode/xray_config.json
  ```

 * دایرکتوری مرزنود
  ```bash
  cd marznode
  ```

 * دانلود محتوای فایل compose.yml
  ```bash
  curl -L your Raw link/compose.yml > compose.yml
  ```

 * اجرای داکر
  ```bash
  docker compose -f ./compose.yml up -d 
  ```

{{% /details %}}


### آماده سازی دستور نهایی 

- یدونه gist دیگه میسازیم با اسم مثلا 
  - germany-panel-test-install.sh
- دستوراتی که تو مراحل قبل اماده کردیم میزاریم داخلش .

- قسمت اول فایل باید این سه خط زیر رو قرار بدید :
```bash
#!/bin/bash
set -e
set -o pipefail
```
- سپس دستورات رو دونه دونه به ترتیب با یک خط فاصله وارد کنید .

{{< callout type="error" >}}
دستوراتی که داخل این فایل میزارید به ترتیب از بالا به پایین دونه دونه داخل سرور اجرا میشوند .
- حواستون به ترتیب دستورات باشه تا به مشکل نخورید.
{{< /callout >}}
{{% details title=" نمونه " closed="true" %}} 

## نمونه محتوای 
- germany-panel-test-install.sh
```bash
#!/bin/bash
set -e
set -o pipefail


echo " اپدیت سرور "
apt-get update -y 

echo " نصب داکر "
curl -fsSL https://get.docker.com | sh

echo " ساخت دایرکتوری مرزنود "
mkdir -p /var/lib/marznode/

echo " کلون کردن مرزنود"
git clone https://github.com/marzneshin/marznode

echo " دانلود سرتیفیکیت پنل client.pem "
curl -L your Raw link/client.pem > /var/lib/marznode/client.pem

echo " xray_config.json دانلود متحوای فایل "
curl -L your Raw link/xray_config.json > /var/lib/marznode/xray_config.json

echo " دایرکتوری مرزنود "
cd marznode 

echo " دانلود محتوای فایل compose.yml "
curl -L your Raw link/compose.yml > compose.yml

echo " اجرای داکر "
docker compose -f ./compose.yml up -d

```

{{% /details %}}

### دستور نهایی

- وقتی فایل germany-panel-test-install.sh را کامل کردید لینک **Raw** گرفتید 

  - با **your Raw link** دستور زیر جایگذین کنید.

```bash
curl -L your Raw link | bash
```
 ---

{{% /steps %}}
