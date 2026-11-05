
Reja
- Z-index
- Overflow

## Z-index

>**Z-index** — ustama-ust  tushib qolgan elementlarni ketma-ketligini aniqlab beradi. Kattaroq **z-index**ga ega bo'lgan element kichikrog'iga qaraganda oldinda joylashadi. **Z-index** har doim joylashtirilgan (positioned) elementlarga amal qiladi.

![[Pasted image 20261105193053.png]]

![[Pasted image 20261105193132.png]]
![[Pasted image 20261105193253.png]]

```html
<style>
	.box-1 {
		height: 200px;
		background-color: red;
	}
	.box-2 {
		height: 100px;
		background-color: blue;
	}
</style>

<div class="box-1">
	Box 1
</div>
<div class="box-2">
	Box 2
</div>
```
## Overflow

>**Overflow** — kontent elementning ichiga sig'may qolgan paytda, o'zini qanday tutishni aniqlab beradi.

![[Pasted image 20261105194135.png]]

Qiymatlari:
- visible (default)
- hidden
- scroll
- auto

1. **Visible**
	>Sig'may qolgan qismi boricha ekranda ko'rinadi va bu default qiymat hisoblanadi.
	
2. **Hidden**
	>Sig'may qolgan qism ekrandan yashiriladi (berkitiladi)
	
3. **Scroll**
	>Sig'may qolgan qismni ko'rish uchun scroll qo'shiladi
	
4. **Auto**
	>Xuddi **scroll**ga o'xshab sig'may qolgan qismini ko'rish uchun **scroll** qo'shiladi, lekin faqat kerak bo'lgan payti
	

>[!NOTE]
>Vertikal hamda gorizantal **scroll**ni **overflow-x** va **overflow-y** yordamida alohida qilib ko'rsatish mumkin.


## Related Notes

- [[04-teaching/programming/02-css/00 - Index]]
- [[22 - Absolute and sticky]]
- [[24 - Positioning yordamida loyihani yaxshilash]]
