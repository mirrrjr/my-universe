## Reja
- Cascading (Kaskadlanish)
- Specificity (O'ziga hoslik)

## Cascading (Kaskadlanish)
> [!NOTE] Yodda tuting
> Cascading (Kaskadlanish) — bir HTML elementga bir necha CSS qoidalar körsatilishi va ulardan birining amal qilishi

```html
<style>
#heading1 {
	color: red;
}

.heading {
	color: yellow;
	font-size: 24px;
}

h1 {
	color: green;
	font-size: 48px;
}
</style>

--------------------------------------------

<h1 id="heading1" class="heading">Hello World</h1>
```

## Specificity (O'ziga hoslik)

> [!NOTE]
> 1. Satirli stillar (inline styles)
> 2. ID (#) 
> 3. Class (.) va Attribute ([]) 
> 4. Tag (< >)
> 5. _*_ (Universal)
## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[04 - Comments]]
- [[06 - Inheritance]]
