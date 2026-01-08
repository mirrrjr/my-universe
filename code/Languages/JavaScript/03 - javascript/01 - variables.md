#variables #assignmet 

**JavaScript**-da `var`, `let` va `const` o'zgaruvchilari mavjud. **ES6**-dan avval `var`-ning o'zi ishlatilgan.

`const` - bu o'zgarmas
- `block scoped`
- `hoisting` ishlaydi ammo xatolik beradi

`let` - bu o'zgaruvchi
- `block scoped`
- `hoisting` ishlaydi ammo xatolik beradi

`var` - bu o'zgaruvchi
- `function/local scoped`
- `hoisting` ishlaydi, qiymati `undefined`
- global elon qilinsa `window` obyektiga yoziladi
- bir xil nom bilan qayta elon qilish ishlaydi (`redeclaring`)

Avvallari `var`-ni global o'zgaruvchiga aylanib ketishini oldini olishda IIFE functiondan foydalanilgan:
```javascript
(function() {
	var message = "Hello";
	alert(message);
})();
```

