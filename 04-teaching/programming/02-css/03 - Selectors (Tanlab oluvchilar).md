## Dars reja
### CSS syntax

```css
p {
	color: red;
}
```

> [!TIP] Diqqat, yodda tuting!
> `p` -> selector (tanlovchi)
> `color` -> property (xossa)
> `green` -> value (qiymat)

### Selectors
> [!TIP] Selector
> HTML hujjatmizidan element(lar)ni tanlab olish uchun ishlatiladi

#### Element (tag)
```html
<style>
p {
	color: red;
}

----------------------------

<p>Hello World</p>
```

#### Class
```html
<style>
.hello {
	color: red;
}

----------------------------

<p class="hello">Hello World</p>
```

#### ID
```html
<style>
#hello {
	color: red;
}

----------------------------

<p id="hello">Hello World</p>
```

#### Attribute
```html
<style>
[disabled] {
	color: red;
}

----------------------------

<p disabled>Hello World</p>
```

#### Universal
```html
<style>
* {
	color: red;
}

----------------------------

<p>Hello World</p>
```

---
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[02 - Loyiha strukturasi]]
- [[04 - Comments]]
