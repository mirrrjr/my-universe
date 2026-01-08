#tdz

**TDZ** - bu `let` va `const`-ning shu `scope` boshidan to ular elon qilingan qatorgacha bo'lgan vaqt oralig'i.

```javascript
function anyFunc() {
	alert(message);          // Temporal
	                         // Dead
	let message = "Hello!";  // Zone
}

if(true) {
	// TDZ start
	console.log(x) // x is dead
	alert(1);
	const x = 1    // TDZ end
}
```
