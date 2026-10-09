Reja
- HTML Tree (Shajara)
- Combinators

## HTML Tree

### Oila shajarasi

![[Pasted image 20261009100650.png]]

### HTML shajarasi

```html
<body>
    <div id="content">
        <h1>Sarlavha</h1>
        <p>Paragraf</p>
        <p>
            <em>Paragraf 2</em>
        </p>
    </div>

    <div id="nav">
        <ul>
            <li>Ro'yxat elementi 1</li>
            <li>Ro'yxat elementi 2</li>
            <li>Ro'yxat elementi 3</li>
        </ul>
    </div>
</body>
```

Shajara shaklida
![[html_tree.png]]

## Combinators

>[!NOTE] Eslab qoling
>Combinators (Kombinatorlar) - "selectorlar" orasidagi munosabatni (bog'liqlik) ko'rsatib beradigan maxsus simvollar

Turlari
- Descendant selector (avlod selectori)
- Child selector (farzand selektori)
- Adjacent selector (qo'shni qardosh selektori)
- General sibling selector (umumiy qardosh slektori)

### Descendant selector

> [!NOTE] Eslab qoling
> **Descendant selector** - belgilangan elementning avlodlari bo'lgan barcha elementlarni tanlab oladi

```html
<style>
    main p {
        background-color: yellow;
	}
</style>

==========================================

<body>
	<header>
		<h2>Avlod selektor</h2>
		<p>Belgilangan elementning avlodlari bo'lgan barcha elementlarni tanlab oladi</p>
	</header>
	
    <main>
        <p>Paragraf 1: "main" ni ichida</p>
        <p>Paragraf 2: "main" ni ichida</p>
        <div>
            <p>Paragraf 3: "main" ni ichida</p>
        </div>
    </main>
    
    <footer>
	    <p>Paragraf 4: "main" ichida emas</p>
    </footer>
</body>
```


### Child selector

>[!NOTE] Eslab qoling
>Belgilangan elementning farzandlari bo'lgan barcha elementlarni tanlab oladi

```html
<style>
    main > p {
        background-color: yellow;
	}
</style>

==========================================

<body>
	<header>
		<h2>Avlod selektor</h2>
		<p>Belgilangan elementning avlodlari bo'lgan barcha elementlarni tanlab oladi</p>
	</header>
	
    <main>
        <p>Paragraf 1: "main" ni ichida</p>
        <p>Paragraf 2: "main" ni ichida</p>
        <div>
            <p>Paragraf 3: "main" ni ichida</p>
        </div>
    </main>
    
    <footer>
	    <p>Paragraf 4: "main" ichida emas</p>
    </footer>
</body>
```


### Adjacent sibling selector

>[!NOTE] Eslab qoling
>**Adjacent sibling selector** - bir elementga yon qo'shni bo'lgan birinchi boshqa elementni tanlash uchun ishlatiladi


```html
<style>
    main + p {
        background-color: yellow;
	}
</style>

==========================================

<body>
	<header>
		<h2>Avlod selektor</h2>
		<p>Belgilangan elementning avlodlari bo'lgan barcha elementlarni tanlab oladi</p>
	</header>
	
    <main>
        <p>Paragraf 1: "main" ni ichida</p>
        <p>Paragraf 2: "main" ni ichida</p>
        <div>
            <p>Paragraf 3: "main" ni ichida</p>
        </div>
    </main>
    
     <p>Paragraf 4: "main" ichida emas</p>
	 <p>Paragraf 5: "main" ichida emas</p>
     
    <footer>
	    <p>Paragraf 6: "main" ichida emas</p>
    </footer>
</body>
```

### General sibling selector

>[!NOTE] Eslab qoling
>**General sibling selector** - bir elementga qo'shni bo'lgan barcha elementlarni tanlash uchun ishlatiladi

```html
<style>
    main ~ p {
        background-color: yellow;
	}
</style>

==========================================

<body>
	<header>
		<h2>Avlod selektor</h2>
		<p>Belgilangan elementning avlodlari bo'lgan barcha elementlarni tanlab oladi</p>
	</header>
	
    <main>
        <p>Paragraf 1: "main" ni ichida</p>
        <p>Paragraf 2: "main" ni ichida</p>
        <div>
            <p>Paragraf 3: "main" ni ichida</p>
        </div>
    </main>
    
     <p>Paragraf 4: "main" ichida emas</p>
	 <p>Paragraf 5: "main" ichida emas</p>
     
    <footer>
	    <p>Paragraf 6: "main" ichida emas</p>
    </footer>
</body>
```
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[06 - Inheritance]]
- [[08 - Classes and combined selectors]]
