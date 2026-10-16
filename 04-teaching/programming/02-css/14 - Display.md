## Reja

### Block va inlilne elementlar

>[!NOTE] Eslab qoling
>**Block element** - ota (parent) elementni to'liq kengligiga yoyiladi va har doim yangi qatordan boshlanadi. `<div>`, `<h1>`, `<ul>`, `<li>` va yana bir qator teglar *blok* element yaratadi.

```html
<style>
	.heading-1 {
		background-color: red;
	}
</style>

=================================

<h1 class="heading-1">Sarlavha</h1>
```

>[!NOTE] Eslab qoling
>**Inline element** - faqatgina o'zini kontenti uchun yetarli bo'ladigan kenglikka ega bo'ladi va yangi qatordan boshlanmaydi, aksincha yonma-yon joylashadi. `<span>`, `<a>`, `<b>`, `<em>` va yana bir qator teglar *inline* element yaratadi.

```html
<style>
	.link {
		background-color: red;
	}
</style>

=================================

<a href="#" class="link">Ilova 1</a>
<a href="#" class="link">Ilova 2</a>
```
### Display

>[!NOTE] Eslab qoling
>**Display** - elementimizni web sahifamizda qanday ko'rsatilishini belgilaydi


#### Qiymatlari

- **Block**
	```html
	<style>
		.to-block {
			display: block
		}
	</style>
	
	============================
	
	<a href="#" class="to-block">Block elementga aylantirish</a>
	```

- **Inline** - element inline elementga xos xususiyatga ega bo'ladi
	```html
	<style>
		.to-inline {
			display: inline
		}
	</style>
	
	============================
	
	<div class="to-inline">Inline elementga aylantirish</div>
	```

- **Inline-block** - inline elementga o'xshab faqat kontenti uchun yetarli bo'ladigan kenglikka ega bo'ladi va yonma-yon joylashadi. Qo'shimcha ravishda block elementga o'xshab `width`, `margin/padding` - `top`, `margin/padding` - `bottom` xossalarini qabul qiladi
	```html
	<style>
		.to-inline-block {
			display: inline
		}
	</style>
	
	============================
	
	<span class="to-inline-block">Inline-Block elementga aylantirish</span>
	```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[13 - Height, width, min and max sizes]]
- [[15 - Text align, vertical align and float]]
