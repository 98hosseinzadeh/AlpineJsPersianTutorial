# شروع کار با Alpine.js
یک فایل خالی در سیستم خود به نام i-love-alpine.html 
ایجاد کنید.
فایل رو با ویرایشگر کد باز کنید و کد HTML زیر رو درونش قرار بدید:
```html
<html>
<head>
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
</head>
<body>
    <h1 x-data="{ message: 'I ❤️ Alpine' }" x-text="message"></h1>
</body>
</html>
```
این فایل رو در یک مرورگر باز کنید اگه عبارت 
"I ❤️ Alpine"
رو دیدید یعنی همه چیز اوکیه...

اکنون برای شروع آماده اید. بیایید به سه مثال عملی به عنوان پایه ای برای یادگیری اصول اولیه 
Alpine
نگاهی بیاندازیم.
در انتهای این مثال ها شمادرک مناسبی از ساختار
alpine.js
به دست خواهید آورد. پس بزن بریم...

1. ساخت یک شمارنده
2. ساخت یک منوی کشویی
3.  ساخت یک input برای جستجو

## # ساخت یک شمارنده
بیایید با یک کامپوننت شمارنده ساده شروع کنیم تا اصول اولیه تعریف 
State
و 
Event
را در 
Alpine
به شما نشان دهیم.

در داخل تگ 
`<body>`
خود این دستورات را وارد کنید:
```html
<div x-data="{ count: 0 }">
    <button x-on:click="count++">Increment</button>
 
    <span x-text="count"></span>
</div>
```
اکنون می بینید ما با سه 
Attribute
که ما به تگ های
HTML
اضافه کردیم یک شمارنده ساده ساختیم.

![counter](../images/l1-cunter-example.gif)

بیایید آنچه اتفاق افتاد رو تفسیر کنیم :

### Declaring data
```html
 <div x-data="{ count: 0 }"> 
```

همه چیز در 
Alpine
با دستور
`x-data`
شروع می شود.
در داخل
`x-data`
با جاوااسکریپت  خالص یک 
Object 
یا شیء از داده را که 
Alpine
شناسایی می کند ، تعریف می کنیم.

هر
property
داخل این 
object
که ساخته خواهد شد در دسترس
directive
ها یا دستورالعمل های دیگر قرار می گیرد. علاوه بر این زمانی که یک 
property
تغییر می کند هر چیزی که به آن وابسته باشد نیز تغییر می کند.

بریم یک نگاهی به 
`x-on`
بیاندازیم و ببینیم چگونه می تواند به
property
که اسمش رو گزاشتیم 
count
دسترسی و 
modify
داشته باشد و اون رو تغییر دهد.
### Listening for events
```html
<button x-on:click="count++">Increment</button>
```
اتریبیوت
`x-on`
یک 
directive
هست که می تواند از آن برای تعریف 
Event
 هاروی یک عنصر استفاده کرد.
در این مثال ما آماده ایم برای یک رویداد
click
و بنابراین دستور رویداد یا
Event
ما
`x-on:click`
می باشد.
همین طور که متصور شدید می تونید به
Event
های دیگه هم گوش بدید یا تعریفش کنید.
برای مثال رویداد 
`mouseenter`
به این صورت است:

`x-on:mouseenter`

هنگامی که یک رویداد رخ می دهد 
Alpine
عبارت یا دستور جاوااسکریپت مرتبط رو فراخوانی می کند.در مثال ما این عبارت یا دستور :
```js 
count++
```
می باشد. همان طور که قبلا گفتم ما داده های تعریف شده در 
`x-data`
دسترسی داریم.

> اغلب به جای
> `x-on`
> شما در کد ها
> `@`
> می بینید. این یک شیوه کوتاه تر و مورد پسند تر است که بسیاری آن را ترجیح می دهند.

### Reacting to changes
```html
<span x-text="count"></span>
```
با دستورالعمل 
`x-text` 
در
Alpine
می توانید برای تعریف محتوای متنی یک عنصر و همینطور عبارت جاواسکریپت استفاده کنید.
در این مورد به
Alpine
می گوییم همیشه محتوای این تگ
`<span>`
، مقدار
property
به نام
count
رو برای ما نمایش بده.

در صورتی که این مورد واضح نبود،
`x-text`
مانند اکثر 
directive
ها یک عبارت ساده جاواسکریپت را به عنوان آرگومان می پذیرد. بنابراین به عنوان مثال می توانید محتوای آن را
```js
 x-text="count * 2"
```
قرار دهید و محتوای متنی تگ
`<span>`
همیشه دو برابر مقدار 
`count`
خواهد بود.

## # ساخت منوی کشویی
با توجه به اینکه ما برخی قابلیت های پایه را دیده ایم بیایید به یک دستور مهم در 
Alpine
یعنی 
`x-show`
با ساخت یک  کامپوننت
dropdown 
یا منوی کشویی بپردازیم.

لطفا کد زیر را در تگ
`<body>`
وارد کنید:

```html
<div x-data="{ open: false }">
    <button @click="open = ! open">Toggle</button>
 
    <div x-show="open" @click.outside="open = false">
        <ul>
            <li>item one</li>
            <li>item two</li>
            <li>item three</li>
        </ul>
    </div>
</div>
```
![Dropdown-menu](../images/l1-dropdown-example.gif)

اگر این کامپوننت را بارگذاری کنید، باید ببینید که آیتم های یک،دو و سه به صورت پیشفرض مخفی هستند. شما می توانید با کلیک روی دکمه
`Toggle`
آنها را در صفحه نمایش دهید یا مخفی کنید.

دستورالعمل های 
`x-on` و `x-data`
باید برای شما از مثال قبلی آشنا باشد.
بنابراین درباره این دو مورد دوباره توضیح نمی دهیم.

### Toggling elements

```html
<div x-show="open" ...>
```

دستور 
`x-show`
یک دستور بسیار قدرتمند در
alpine
است که می تواند بر اساس نتیجه یک عبارت  جاوااسکریپت که در اینجا پراپرتی
open
می باشد،یک بلاک
HTML
را به نمایش در بیاورد.

### Listening for a click outside
```html
<div ... @click.outside="open = false">
```

در این مثال نکته جدیدی را متوجه خواهید شد.
در بسیاری از 
directive
ها در 
alpine
که مُدیفایر می پذیرند به انتهای
directive
ها این مُدیفایر زنجیر وار چسبانده و با یک نقط از هم جدا می شوند.

در این مورد
`outside`
به ما میگه به جای گوش دادن به رویداد کلیک در داخل
div
به رویداد کلیک در خارج از این 
div
واکنش نشان دهد.
به تصویر قبلی دقت کنید، حتما متوجه خواهید شد.

## # ساخت یک input برای جستجو
بیایید اکنون یک کامپوننت پیچیده تر بسازیم و  تعداد انگشت شماری از
directive
ها و
pattern
ها رو معرفی کنیم.

کد زیر را د تگ
`<body>`
وارد کنید:
```html
<div
    x-data="{
        search: '',
 
        items: ['foo', 'bar', 'baz'],
 
        get filteredItems() {
            return this.items.filter(
                i => i.startsWith(this.search)
            )
        }
    }"
>
    <input x-model="search" placeholder="Search...">
 
    <ul>
        <template x-for="item in filteredItems" :key="item">
            <li x-text="item"></li>
        </template>
    </ul>
</div>
```
![search-input](../images/l1-search-input-example.gif)

به طور پیشفرض همه آیتم های 
foo,bar,baz
در صفحه نمایش داده می شود.
اما می توان با تایپ کردن در
input
متنی، آنها را فیلتر کرد.
همانطور که در حال تایپ کردن هستید لیست آیتم ها در صفحه نمایش تغییر می کند تا نتیجه آن چیزی باشد که جستجو و تایپ می کنید.

اکنون اتفاقات زیادی اینجا رخ می دهد، بنابراین بیایید تکه تکه آنها را برسی کنیم.

### Multi line formatting

مورد اولی که می خواهیم به آن اشاره کنیم اینه که در حال حاضر استفاده از
`x-data`
عملکرد بسیار بیشتری نسبت به قبل دارد.
برای سهولت نوشتن و خواندن  ما آن را در چند خط 
HTML
نوشته ایم که این کاملا اختیاری است و ما در مورد چگونگی جلوگیری از این مشکل در ادامه به صورت کلی توضیح خواهیم داد.
اما در حال حاضر ما تمام کد های جاوااسکریپت را مستقیماً درون کد 
HTML
می نویسیم.

### Binding to inputs

```html
<input x-model="search" placeholder="Search...">
```

الان در کد بالا متوجه
directive
جدیدی شدید که ما تا حالا اون رو ندیده بودیم:
`x-model`

ویژگی 
`x-model`
برای 
bind
کردن یک مقدار به پراپرتی
`search`
از مقادیر 
دایرکتیو
`x-data`
استفاده می شود.

در این مورد
`x-data="{ search: '', ... }`
می باشد.

این به این معنی است که هر زمان مقدار 
`input`
تغییر کند مقدار پراپرتی
search
در
`x-data`
نیز تغییر می کند.

دایرکتیو
`x-model`
توانایی خیلی بیشتر از این مثال را دارد.

### Computed properties using getters
محاسبه پراپرتی ها با استفاده از getter ها

مورد بعدی که می خواهم توجه شما را به آن جلب کنم آیتم ها و متد 
`filteredItems`
از دایرکتیو
`x-data`
می باشد.
```js
{
    ...
    items: ['foo', 'bar', 'baz'],
 
    get filteredItems() {
        return this.items.filter(
            i => i.startsWith(this.search)
        )
    }
}
```
