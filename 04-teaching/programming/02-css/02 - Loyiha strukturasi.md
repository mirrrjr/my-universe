## Dars reja

### 01. HTML hujjat va CSS'ni ulash
#### Satrili stillar (inline styles)
```html
<body>
    <h1 style="color: red">Sarlavha</h1>
    <a href="#" style="color: green">Google</a>
</body>
```
#### Ichki stillar (internal styles)
```html
<head>
    <style>
        h1 {
            color: red;
        }
        a {
            color: green;
        }
    </style>
</head>
<body>
    <h1>Sarlavha</h1>
    <a href="#">Google</a>
</body>
```
#### Tashqi stillar (external styles)
**index.html**
```html
<head>
    <link rel="stylesheet" href="style.css" />
</head>
<body>
    <h1>Sarlavha</h1>
    <a href="#">Google</a>
</body>
```
**style.css**
```css
h1 {
    color: red;
}

a {
    color: green;
}
```

### 02. Loyiha strukturasini yaratish
- [ ] Folder structure yaratib olish
	- [ ] `index.html` fayl
	- [ ] `images` folder
	- [ ] `css` folder

### 03. VSCode Live Server
- [ ] "Live Server" pluginini (extension) o'rnatish

---

## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[01 - Kurs loyihasi]]
- [[03 - Selectors (Tanlab oluvchilar)]]
