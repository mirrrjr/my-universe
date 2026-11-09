Reja
- Absolute
- Sticky

## Absolute

>**Absolute** - element o'zining eng yaqin joylashtirilgan (positioned) ajdod (ancestor) elementiga nisbatan joylashadi. Joylashtirilgan degani, position xossasi **static** qiymatdan boshqa qiymatga ega bo'lgan elementga aytiladi.

```html
<style>
	.relative-box {
		position: relative;
		width: 200px;
		height: 200px;
		border: 5px solid red;
	}
	
	.absolute-box {
		position: absolute;
		top: 10px;
		right: 20px;
		width: 50px;
		height: 100px;
		border: 5px solid blue;
	}
</style>

<div class="relative-box">Bu quti staticdan boshqa qiymatga ega
	<div class="absolute-box">Bu quti absolute qiymatga ega</div
</div>
```

## Stikcy

>**Sticky** - element **scroll**ning qayerda joylashganiga qarab joylashadi. Bu qiymat **relative** va **fixed** qiymatlarini o'zida saqlaydi va **scroll**ni qayerda joylashganiga qarab shu ikki qiymatdan birini o'ziga oladi.

```html
<style>
	.sticky-box {
		position: sticky;
		top: 10px;
		width: 200px;
		height: 200px;
		border: 5px solid red;
	}
	
	.high-box {
		height: 10000px;
		border: 5px solid blue;
	}
</style>

<h1>Sticky qiymatga misol</h1>
<div class="sticky-box">Sticky qiymatiga ega box</div>
<div class="high-box">
	Katta balandlikka ega quti
</div

```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[21 - Relative and fixed]]
- [[23 - Z index and overflow]]
