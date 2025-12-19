**Tagged template literals** - bu `template literal` va funlsiyalarni birlashtirgan holda `template literal`-larni *parse* qilib olishda ishlatiladi.

```javascript
// Syntax
tagFunction`template literal ${myVar}`;

// Example
fucntion highlight(strings, ...values) {
	let str = "";
	strings.forEach((string, i) => {
		str += `${string} <span class="h1">${values[i] || ""}</span>`;	
	});
	return str;
};

let catName = "Tom";
let catAge = 5;
let sentence = highlight`My cat's name is ${catName} and she is ${catAge} years old`;

```