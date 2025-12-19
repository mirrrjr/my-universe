>Funksiya va metodlarda `context(this)`-ni o'zgartirish uchun ishlatiladi

Bir-biridan farqlari quyidagicha:
- `call(nexContext, arg1?, arg2?)` - ishlatishimiz bilan funksiya/metodni yangi *context* bilan ishlatib yuboradi
- `apply(newConext, [arg1?, arg2?])` - *call* bilan bir xil, faqat funksiya/metod argumentlarini array ko'rinishida bersak bo'ladi
- `bind(newContext, arg1?, arg2?)` - *call* bilan bir xil, faqat funksiyani yangi context bilan qaytarib beradi. Qaytgan funksiyani o'zgaruvchiga olib hohlagancha ishlatsak bo'ladi.

```javascript
const actions = {
	sayName() {
		console.log("My name is " + this.name);
	};
	sayAge() {
		console.log("My age is " + this.age);
	};
};

let users = [
	{name: "John", age: 22},
	{name: "Jack", age: 23},
];

users.forEach(user => {
	actions.sayName.call(user);
})
```