Reja:
- Forma strukturasi
- Input, select va textarea
- Button

## Forma strukturasi

```html
<form action="server.php" method="GET">

    <label for="firstname">Firstname</label>
    <input type="text" id="firstname" name="firstname" placeholder="Ismingiz">

    <label for="lastname">Lastname</label>
    <input type="text" id="lastname" name="firstname" placeholder="Familiyangiz">

    <label for="country">Davlat</label>
    <select name="country" id="country">
        <option value="uzb">Uzbekistan</option>
        <option value="jap">Japan</option>
        <option value="usa">USA</option>
    </select>

    <label for="mesage">Xabar</label>
    <textarea name="message" id="message" placeholder="Xabaringiz"></textarea>

	<button type="submit">Yuborish</button>
</form>
```


## Input, select va textarea

```css
input, select, textarea {
	width: 100%;
	padding: 10px;
	border: 1px solid #ddd;
	border-radius: 4px;
	margin: 5px 0 20px 0;
}
```

## Button

```css
button {
	background-color: #2e856f;
	color: white;
	padding: 10px 20px;
	border: none;
	border-radius: 4px;
	cursor: pointer;
}
button:hover {
	background-color: #006a4a;
}
```

## Related Notes
- [[04-teaching/programming/02-css/00 - Index]]
- [[28 - Images yordamida loyihani yaxshilash]]
- [[30 - Formalarga style berish II]]
