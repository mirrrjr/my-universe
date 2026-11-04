Reja
- Relative
- Fixed

![[Pasted image 20261103213736.png]]

## Relative

> **Relative** - element o'zining hozirgi (normal) joylashuviga nisbatan joylashadi

```html
<style>
	.relative-box {
		position: relative;
		background-color: red;
		height: 200px;
	}
	.box {
		background-color: blue;
		height: 100px;
	}
</style>


<div class="relative-box">Box 1</div>
<div class="box">Box 2</div>
```

## Fixed

>[!NOTE] Eslab qoling
>**Viewport** - web sahifamizning foydalanuvchiga ko'rinadigan qismi

Misol:

![[Pasted image 20261104121331.png]]

> **Fixed** - element `viewport`ga nisbatan joylashadi, Bu degani, u har doim o'zini joyida qoladi va scroll paytida joyini o'zgartirmaydi.

```html
<style>
.fixed-box {
	position: fixed;
	top: 50px;
	right: 0;
	background-color: blue;
	height: 200px;
}
</style>

<div class="fixed-box">Fixed qiymatga ega box</div>
```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[20 - Positioning and static]]
- [[22 - Absolute and sticky]]
