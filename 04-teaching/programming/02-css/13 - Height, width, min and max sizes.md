## Reja
### Height

![[Pasted image 20261012104946.png]]

>[!NOTE] Eslab qoling
>**Height** - elementning balandligi


```css
selector-nomi {
	height: 200px;
}
```


Sahifamizni to'liq balandligini band qilish uchun
```css
html {
	height: 100%;
}

body {
	height: 100%;
}

selector-nomi {
	height: 100%;
}
```


### Width

![[Pasted image 20261012104946.png]]

>[!NOTE] Eslab qoling
>**Width** - elementning kengligi

```css
selector-nomi {
	width: 200px;
}
```

Sahifamizni to'liq kengligini band qilish uchun
```css
selector-nomi {
	width: 100%;
}
```
### Max-height, min-height

>[!NOTE] Eslab qoling
>**Max-height** - elementimiz ega bo'lishi mumkin bo'lgan eng katta balandlik qiymatini belgilaydi (uning balandligi ko'rsatilgan qiymatdan kichkina bo'lishi mumkin, lekin katta emas!).

```html
<style>
	.paragraph {
		background-color: red;
		max-height: 30px;
	}
</style>

=================================

<p class="paragraph">
	Lorem ipsum dolor sit, amet consectetur adipisicing elit. Impedit
	maiores error alias vel quam quaerat reiciendis possimus culpa quas
	dolorem.
</p>
```

>[!NOTE] Eslab qoling
>**Min-height** - elementimiz ega bo'lishi mumkin bo'lgan eng kichik balandlik qiymatini belgilaydi (uning balandligi ko'rsatilgan qiymatdan katta bo'lishi mumkin, lekin kichik emas!).

```html
<style>
	.paragraph {
		background-color: red;
		min-height: 30px;
	}
</style>

=================================

<p class="paragraph">
	Lorem ipsum dolor sit, amet consectetur adipisicing elit. Impedit
	maiores error alias vel quam quaerat reiciendis possimus culpa quas
	dolorem.
</p>
```
### Max-width, min-width

>[!NOTE] Eslab qoling
>**Max-width** - elementimiz ega bo'lishi mumkin bo'lgan eng katta kenglik qiymatini belgilaydi (uning balandligi ko'rsatilgan qiymatdan kichik bo'lishi mumkin, lekin katta emas!).

```html
<style>
	.box-1 {
		width: 500px;
		background-color: red;
	}
	.box-2 {
		max-width: 500px;
		background-color: blue;
	}
</style>

=================================

<div class="box-1">
	Lorem ipsum dolor sit
</div>

<div class="box-2">
	Lorem ipsum dolor sit, Lorem ipsum dolor sit
</div>
```


>[!NOTE] Eslab qoling
>**Min-width** - elementimiz ega bo'lishi mumkin bo'lgan eng kichik kenglik qiymatini belgilaydi (uning balandligi ko'rsatilgan qiymatdan katta bo'lishi mumkin, lekin kichik emas!).

```html
<style>
	.box-1 {
		width: 500px;
		background-color: red;
	}
	.box-2 {
		min-width: 500px;
		background-color: blue;
	}
</style>

=================================

<div class="box-1">
	Lorem ipsum dolor sit
</div>

<div class="box-2">
	Lorem ipsum dolor sit, Lorem ipsum dolor sit
</div>
```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[12 - Margin collapsing and shorthands]]
- [[14 - Display]]
