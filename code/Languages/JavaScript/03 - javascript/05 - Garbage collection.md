#garbage_collection #gc

**Garbage collection** - `heap` to'lib qolmasligi uchun `garbage collector` keraksiz obyektlarni xotiradan o'chirib turadi va shu holatni `garbage collection` deb ataladi. Bu `JavaScript` da default bor, lekin ayrim dasturlash tillari, masalan `rust`-da bu ishni dasturchining o'zi amalga oshiradi.

```javascript
let obj = { name: "John" }; // GC ishlaydi | unreachable
obj = { name: "Jack" };
```
