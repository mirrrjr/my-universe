## Reja

### Margin collapsing

>[!NOTE] Eslab qoling
>**Margin collapsing** - ikki elementning `top` va `bottom` *margin*lari bazida birlashib, ikkovida kattasiniki natijaviy margin bo'lib qoladi

 
![[Pasted image 20261012110908.png]]

```html
<style>
	.box1 {
		margin: 30px;
	}
	.box2 {
		margin: 20px;
	}
</style>

=======================================

<div class="box1">Box 1</div>
<div class="box2">Box 2</div>
```

### Shorthands

>[!NOTE] Eslab qoling
>**Shorthands** - CSS hossalarining qiymatlarini qisqartirilgan ko'rinishda yozish

#### Border

To'liq yozilishi
```css
.selector {
	border-width: 10px;
	border-style: solid;
	border-color: blue;
}
```

Qisqartma ko'rinishi
```css
.selector {
	border: 10px solid blue;
}
```

Faqatgina malum bir tomonga stil berish
```css
.selector{
	border-top: 5px solid red;
	border-right: 2px dotted yellow;
	border-bottom: 10px dashed green;
	border-left: 4px groove pink;
}
```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[11 - Box model, margin and padding]]
- [[13 - Height, width, min and max sizes]]
