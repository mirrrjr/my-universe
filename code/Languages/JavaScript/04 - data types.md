#datatypes

>Malumot tiplari ikkiga bo'linadi: **Primitive** va **Non-primitive**

## Primitive data types
1. Number
2. BigInt
3. String
4. Boolean
5. null
6. undefined
7. symbol

### Number
The _number_ type represents both integer and floating point numbers.
There are many operations for numbers, e.g. multiplication `*`, division `/`, addition `+`, subtraction `-`, and so on.

Besides regular numbers, there are so-called “special numeric values” which also belong to this data type: `Infinity`, `-Infinity` and `NaN`.

- `Infinity` represents the mathematical [Infinity](https://en.wikipedia.org/wiki/Infinity) ∞. It is a special value that’s greater than any number.

```javascript
alert( 1 / 0 ); // Infinity
```

Or just reference it directly:

```javascript
alert( "not a number" / 2 ); // NaN, such division is erroneous
```

`NaN` is sticky. Any further mathematical operation on `NaN` returns `NaN`:

So, if there’s a `NaN` somewhere in a mathematical expression, it propagates to the whole result (there’s only one exception to that: `NaN ** 0` is `1`).

>[!TIP] Mathematical operations are safe
Doing maths is “safe” in JavaScript. We can do anything: divide by zero, treat non-numeric strings as numbers, etc.

The script will never stop with a fatal error (“die”). At worst, we’ll get `NaN` as the result.

Special numeric values formally belong to the “number” type. Of course they are not numbers in the common sense of this word.

### BigInt
In JavaScript, the “number” type cannot safely represent integer values larger than `(253-1)` (that’s `9007199254740991`), or less than `-(253-1)` for negatives.

To be really precise, the “number” type can store larger integers (up to `1.7976931348623157 * 10308`), but outside of the safe integer range `±(253-1)` there’ll be a precision error, because not all digits fit into the fixed 64-bit storage. So an “approximate” value may be stored.

For example, these two numbers (right above the safe range) are the same:
```javascript
console.log(9007199254740991 + 1); // 9007199254740992
console.log(9007199254740991 + 2); // 9007199254740992
```

So to say, all odd integers greater than `(253-1)` can’t be stored at all in the “number” type.

For most purposes `±(253-1)` range is quite enough, but sometimes we need the entire range of really big integers, e.g. for cryptography or microsecond-precision timestamps.

`BigInt` type was recently added to the language to represent integers of arbitrary length.

A `BigInt` value is created by appending `n` to the end of an integer:
```javascript
// the "n" at the end means it's a BigInt
const bigInt = 1234567890123456789012345678901234567890n;
```
As `BigInt` numbers are rarely needed, we don’t cover them here, but devoted them a separate chapter [BigInt](https://javascript.info/bigint). Read it when you need such big numbers.

### String
A string in JavaScript must be surrounded by quotes.

```javascript
let str = "Hello";
let str2 = 'Single quotes are ok too';
let phrase = `can embed another ${str}`;
```

In JavaScript, there are 3 types of quotes.

1. Double quotes: `"Hello"`.
2. Single quotes: `'Hello'`.
3. Backticks: `` `Hello` ``.

### Boolean
The boolean type has only two values: `true` and `false`.

This type is commonly used to store yes/no values: `true` means “yes, correct”, and `false` means “no, incorrect”.

For instance:

```javascript
let nameFieldChecked = true; // yes, name field is checked
let ageFieldChecked = false; // no, age field is not checked
```

Boolean values also come as a result of comparisons:

```javascript
let isGreater = 4 > 1;

alert( isGreater ); // true (the comparison result is "yes")
```

We’ll cover booleans more deeply in the chapter [Logical operators](https://javascript.info/logical-operators).

### The "null" value

The special `null` value does not belong to any of the types described above.

It forms a separate type of its own which contains only the `null` value:

```javascript
let age = null;
```

In JavaScript, `null` is not a “reference to a non-existing object” or a “null pointer” like in some other languages.

It’s just a special value which represents “nothing”, “empty” or “value unknown”.

The code above states that `age` is unknown.

### The “undefined” value

The special value `undefined` also stands apart. It makes a type of its own, just like `null`.

The meaning of `undefined` is “value is not assigned”.

If a variable is declared, but not assigned, then its value is `undefined`:
```javascript
let age;

alert(age); // shows "undefined"
```
Technically, it is possible to explicitly assign `undefined` to a variable:
```javascript
let age = 100;

// change the value to undefined
age = undefined;

alert(age); // "undefined"
```
…But we don’t recommend doing that. Normally, one uses `null` to assign an “empty” or “unknown” value to a variable, while `undefined` is reserved as a default initial value for unassigned things.

### Symbols
The `symbol` type is used to create unique identifiers for objects. We have to mention it here for the sake of completeness, but also postpone the details till we know objects.

---
## Non-primitive data types
1. **Object**

Obyektlar primitive qiymatlardan farqli o'laroq, `call stack`-da `reference` saqlaydi. Bu reference bizni obyektning `heap`-dagi manzilida turgan qiymatiga olib boradi. Shu sab obyektlar `mutable`, primitive qiymatlar `immutable` deyiladi.


|            | Call         | stack         |     | Heap          |           |
| ---------- | ------------ | ------------- | --- | ------------- | --------- |
|            | **Address**  | **Value**     |     | **Address**   | **Value** |
| *newVar*   | 00QDWWF5F52  | 1             |     | F5EF1EF15SEFE | [1, 2]    |
| *myNumber* | WD6W4D6W4D   | 32            |     |               |           |
| *myString* | 13Q13QD31D31 | 'hello'       |     |               |           |
| *myArray*  | D1WD2WW32D   | F5EF1EF15SEFE |     |               |           |


The `object` type is special.

All other types are called “primitive” because their values can contain only a single thing (be it a string or a number or whatever). In contrast, objects are used to store collections of data and more complex entities.

Being that important, objects deserve a special treatment. We’ll deal with them later in the chapter [Objects](https://javascript.info/object), after we learn more about primitives.

### Obyektlar qanday ishlaydi? Primitive qiymatlardan nima farqi bor?

Obyektlar primitive qiymatlardan farqli o'laroq, `call stack`-da `reference` saqlaydi. Bu reference bizni obyektning `heap`-dagi manzilida turgan qiymatiga olib boradi. Shu sabab obyektlar **mutable**, primitive qiymatlar `immutable` deyiladi