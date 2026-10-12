## Reja:
### Box model

>[!NOTE] Eslab qoling
>**Box model** - HTML'dagi har bir lemement CSS uchun shu modelga asoslangan bo'ladi. Yani CSS har bir elementimizni `Box` (quti) modeli ostida ko'radi

![[Pasted image 20261012104946.png]]

---
### Padding

>[!NOTE] Eslab qoling
>**Padding** - elementning *content* qismidan *border* (chegara) qismigacha bo'lgan masofa

```html
<style>
	.box {
		padding: 10px;
	}
</style>

==========================================

<div class="box">Box (quti) modelini amalda ko'rish</div>
```

---

### Border

>[!NOTE] Eslab qoling
>**Border** - elementning chegarasi

```html
<style>
	.box {
		border-width: 1px;
		border-style: solid;
		border-color: black;
	}
</style>

==========================================

<div class="box">Box (quti) modelini amalda ko'rish</div>
```

---

### Margin

>[!NOTE] Eslab qoling
>Margin - element va uning atrofidagi elementlar orqasidagi masofa

```html
<style>
	.box {
		margin: 10px;
	}
</style>

==========================================

<div class="box">Box (quti) modelini amalda ko'rish</div>
```

---
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[10 - CSS asoslari yordamida loyihani yaxshilash]]
- [[12 - Margin collapsing and shorthands]]
