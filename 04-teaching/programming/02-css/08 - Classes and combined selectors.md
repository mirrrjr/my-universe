Reja
- Multiple classes (bir nechta class'lar)
- Combined (qo'shma) selektorlar

## Multiple classes

>[!NOTE] Eslab qoling
>Multiple classes - elementga bir nechta `class` lar ko'rsatish imkoniyati

```html
 <style>
	.text-red {
        color: red;
    }
    .text-bold {
        font-weight: bold;
    }
    .text-green {
        color: green;
    }
</style>
        
=====================================

<body>
    <p class="text-red text-bold">Qizil va qalin ko'rinishdagi text</p>
    <p class="text-green text-bold">Yashil va qalin ko'rinishdagi text</p>
    <p class="text-green">Yashil ko'rinishdagi text</p>
</body>
```
## Combined selektorlar

>[!NOTE] Eslab qoling
>Combined selektorlar - bir elementni bir nechta selectorlar kombinatsiyasi orqali tanlab olish

```html
<style>
	h1 {
		color: red;
	}
	h1.active {
		color: white;
		background-color: red;
	}
	
	a.active {
		color: green;
	}
</style>

=======================================

<h1 class="active">Sarlavha 1</h1>
<h1>Sarlavha 2</h1>

<a href="#" class="active">Ilova 1</a>
<a href="#">Ilova 2</a>
```

## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[07 - Combinators]]
- [[09 - Class, ID and important]]
