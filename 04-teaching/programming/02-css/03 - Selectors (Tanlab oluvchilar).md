## CSS syntax

```css
p {
	color: green;
}
```

> [!TIP] Diqqat, yodda tuting!
> `p` -> selector (tanlovchi)
> `color` -> property (xossa)
> `green` -> value (qiymat)

## Selectors
> [!TIP] Selector
> HTML hujjatmizdan element(lar)ni tanlab olish uchun ishlatiladi

### Element (tag)
```html
<style>
p {
	color: red;
}
</style>
----------------------------

<p>Hello World</p>
```

### Class
```html
<style>
.hello {
	color: red;
}
</style>
----------------------------

<p class="hello">Hello World</p>
```

### ID
```html
<style>
#hello {
	color: red;
}
</style>
----------------------------

<p id="hello">Hello World</p>
```

### Attribute
```html
<style>
[disabled] {
	color: red;
}
</style>
----------------------------

<p disabled>Hello World</p>
```

### Universal
```html
<style>
* {
	color: red;
}
</style>
----------------------------

<p>Hello World</p>
```

---
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[02 - Loyiha strukturasi]]
- [[04 - Comments]]
