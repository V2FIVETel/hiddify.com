---
title: آموزش نحوه کنترل منابع سرور در هیدیفای‌منیجر
---

<div dir=rtl markdown=1>

# کنترل منابع سرور در هیدیفای

خیلی وقت‌ها نیاز است که شما وضعیت منابع سرور یعنی CPU و RAM سرور خود را چک کنید. مثلا هنگامی که هنگی وجود دارد. برای این کار به چند روش می‌توانید این منابع را مانیتور کنید.

## استفاده از بخش داشبورد در پنل
برای اینکه از وضعیت استفاده CPU و RAM و هارددیسک خود مطلع بشید، به بخش داشبورد در پنل هیدیفای بروید. در اینجا اطلاعات مختلف و مفیدی دریاره وضعیت منابع سیستم و همچنین اطلاعات ترافیک کارت شبکه و کاربران آنلاین به صورت یکپارچه قابل مشاهده است.

![داشبورد هیدیفای](https://user-images.githubusercontent.com/125398461/236671492-9ffc4521-ea2a-4fcb-bfd9-c071ac5a3d4d.png)


## کنترل منابع با استفاده از ابزار htop
یکی از ابزارهایی که برای کنترل منابع در سرورهای لینوکسی می‌توان استفاده نمود، htop می‌باشد.




* ابتدا به سرور [SSH بزنید](/manager/wiki/SSH-%D8%A2%D9%85%D9%88%D8%B2%D8%B4-%D8%A7%D8%AA%D8%B5%D8%A7%D9%84-%D8%A8%D9%87-%D8%B3%D8%B1%D9%88%D8%B1-%D8%A7%D8%B2-%D8%B7%D8%B1%DB%8C%D9%82).

*  و با زدن `Cancel` و یا فشردن همزمان کلیدهای `ctrl+c` از منوی هیدیفای خارج شوید. در صورتی که بعد از اینکار همچنان منو برای شما نمایش داده می‌شود عبارت `clear` رو تایپ و اینتر کنید.
* سپس اگر `htop` روی سرور شما نصب نیست، از طریق دستور زیر آن را نصب کنید

<div dir=ltr markdown=1>
```
apt install htop
```
</div>

> معمولا روی ابونتو ۲۰.۰۴ و ۲۲.۰۴ این برنامه به صورت پیش‌فرض نصب است.

* سپس این دستور را اجرا کنید تا `htop` باز شود.

<div dir="ltr" markdown=1>
```
htop
```
</div>

![photo_2023-06-04_20-35-25](https://github.com/hiddify/hiddify-config/assets/125398461/38c5ab1f-8fed-49c9-9455-04c7a7e83917)


از این برنامه می‌توانید میزان مصرف منابع سرورتان توسط هر process را مشاهده کنید.

*  برای مشاهده میزان مصرف `CPU` هر process، روی `CPU` کلیک کنید تا بر این اساس مرتب شود و ببینید کدوم process درصد بیشتری از `CPU` رو به خودش اختصاص داده است.

* همچنین برای مشاهده میزان مصرف `RAM` توسط هر process، روی `MEM` کلیک کنید تا بر این اساس مرتب شود.

* در صورتی که بیشترین منابع را سرویس‌های هیدیفای  (مثل hidiffy-panel، hiddify-nginx, hiddify-xray و ...)استفاده می‌کنند، از htop خارج شوید. 

> برای خارج شدن از محیط htop باید کلیدهای `ctrl+c` یا `q` رو فشار بدید.

* سپس یکبار از طریق دستور زیر وارد منوی هیدیفای شوید.

<div dir=ltr markdown=1>
```
bash /opt/hiddify-config/menu.sh
```
</div>


*  با استفاده از کلیدهای جهتی (بالا و پایین) گزینه‌ی `restart` را انتخاب کنید و صبر کنید تا سرویس‌ها ریستارت شوند و مجددا از [منوی هیدیفای](/manager/wiki/SSH-%D9%86%D8%AD%D9%88%D9%87-%D8%A7%D8%AA%D8%B5%D8%A7%D9%84-%D9%88-%D8%B1%D9%81%D8%B9-%D8%B9%DB%8C%D8%A8-%D8%A7%D8%B2-%D8%B7%D8%B1%DB%8C%D9%82) خارج شوید و `htop` را بررسی کنید.




## خالی کردن حافظه رم
حافظه رم در واقع حافظه موقت هست که فضای آن توس سرویس‌های در حال اجرا اشغال می‌شود. بخشی از حافظه هم توسط خود سیستم عامل اشغال می‌شود.

پر شدن رم به تعداد کاربر شما روی پنل رابطه مستقیم ندارد. هر تعداد کاربر که در پنل تعریف شده باشند، یک سری سرویس‌ها در هر صورت باید در حال اجرا باشند تا سیستم عامل و سرویس های جانبی کار کنند. بنابراین تعداد کاربر روی پنل رابطه مستقیم و خطی با پر شدن رم ندارند بلکه سرویس‌های در حال اجرا رابطه مستقیم با مقدار رم استفاده شده دارند.

سیستم عامل همواره مدیریت منابع سرور را بر عهده دارد و اگر در سرور خود رم تا ۸۰٪ هم پر شده باشد، اتفاقی کاملا طبیعی است و نباید نگران باشید.

> در سرورهای لینوکسی به هیچ عنوان برای رفع مشکل پر شدن رم، سیستم را ریبوت نکنید.

* یکی از راه‌های بهبود وضعیت رم پر شده سرور، خالی کردن حافظه کش رم است. با این دستور در ترمینال سرور هنگامی که با یوزر روت لاگین کرده‌اید می‌توانید کش را خالی کنید.

<div dir=ltr markdown=1>
```
sync && systemctl -w vm.drop_caches=3
```
</div>

اگر دستور بالا با خطا مواجه شد، می‌توانید دستور زیر را استفاده کنید. 

<div dir=ltr markdown=1>
```

free && sync && echo 3 > /proc/sys/vm/drop_caches && free

```

</div>

> حتما توجه کنید که با یوزر روت لاگین کرده باشید و بعد این کامند را اجرا کنید.

## مدیریت هارد دیسک
* علاوه بر داشبورد پنل هیدیفای که وضعیت هارد دیسک را نمایش می‌دهد، می‌توان از دستور زیر نیز در ترمینال استفاده نمود.

<div dir=ltr markdown=1>
```
df -h --total
```
</div>

که خروجی آن به شکل زیر است.

<div align=center markdown=1>
![df command](https://github.com/hiddify/hiddify-config/assets/125398461/f3552ab5-a105-40b5-8210-65487903c6ba)
</div>

* در ایننجا فضای مربوط به `sda1` مطابق با شکل باید چک شود. اگر به هر دلیلی این فضا پر شده بود و نیاز بود مقداری از فضا را خالی نمایید، می‌توانید اطلاعات مربوط به لاگ‌ها را با دستور زیر پاک نمایید.

<div dir=ltr markdown=1>
```
rm -rf /opt/hiddify-config/log/system/*
```
</div>

* کار تمام است.