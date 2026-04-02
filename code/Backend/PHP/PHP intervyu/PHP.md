## 1. PHPda **echo** teg qanday yoziladi?

```php
<?= $count >
```

## 2. PHP **data type**’lar

**Primitive Data Types**

|**Data Type**|**Description**|
|---|---|
|bool|Represents a boolean value: true or false.|
|int|Represents an integer value (whole number).|
|float|Represents a floating-point number (decimal).|
|string|Represents a sequence of characters.|
|NULL|Represents a variable with no value.|

**Compound Data Types**

|**Data Type**|**Description**|
|---|---|
|array|An ordered map of key/value pairs.|
|object|An instance of a class.|
|callable|A reference to a function.|
|iterable|Any array or object that implements the Traversable interface.|
|resource|A reference to an external resource (e.g., database connection).|

## 3. **Global** o’zgaruvchilar

**Global o‘zgaruvchi** — skriptning global scope (asosiy qismi) da yaratilgan va boshqa joylarda, xususan funksiyalar ichida ham foydalanish mumkin bo‘lgan o‘zgaruvchi.

PHP’da global o‘zgaruvchini funksiyada ishlatish uchun ikki usul bor:

- `global` kalit so‘zi
- `$GLOBALS` superglobal massivi

```php
<?php

$x = 10; // global o'zgaruvchi

function test() {
    global $x; // global o'zgaruvchini chaqirish
    echo $x;
}

test();
```

```php
<?php

$x = 20;

function test() {
    echo $GLOBALS['x'];
}

test();
```

## 4. PHPda **static** va **local** o'zgaruvchilar

**Local o‘zgaruvchi** — faqat **funksiya yoki blok ichida e’lon qilinadigan va shu joyning o‘zida ishlaydigan o‘zgaruvchi**. Funksiya tugagach yoki blok yopilgach u **yo‘qoladi** va tashqaridan unga murojaat qilib bo‘lmaydi:

```php
<?php

function test() {
    $x = 10; // local o'zgaruvchi
    echo $x;
}

test();
echo $x; // xatolik => Undefined variable $x
```

**Static o‘zgaruvchi** — funksiya ichida e’lon qilinadi, lekin funksiya har chaqirilganda **qiymatini saqlab qoladi:**

```php
<?php

function counter() {
    static $x = 0;
    $x++;
    echo $x . "\n";
}

counter();
counter();
counter();
```

Natija:

```php
1
2
3
```

Sababi: `static` o‘zgaruvchi **oldingi qiymatini saqlab qoladi**.

## 5. **Property** va **variable** farqi nimada?

**`Variable`** — qiymat saqlash uchun ishlatiladigan umumiy o‘zgaruvchi bo‘lib, u **funksiya ichida yoki global scope da** e’lon qilinadi.

**`Property`** — bu **class ichida e’lon qilingan o‘zgaruvchi**, ya’ni **obyektga tegishli variable**.

## 6. **Array** nima?

**`Array`** — o’zida bir necha turdagi malumotlarni saqlay oladigan ma’lumotlar tuzilmasi **(data structure)**.

```php
$arr = [1, "Hello", true];
```

## 7. **isset()** metodining vazifasi nima?

PHPdagi `isset()` funksiyasi o'zgaruvchining belgilangan va nolga teng emasligini tekshirish uchun ishlatiladi. Agar o'zgaruvchi mavjud bo'lsa va nolga teng bo'lmagan qiymatga ega bo'lsa, u `true` qiymatini qaytaradi; aks holda, u `false` qiymatini qaytaradi.

## 8. **Cooki** vs **Session**

**`Cookie:`**

- Saqlash joyi: Cookie-lar foydalanuvchining brauzerida saqlanadi.
- Ma'lumot turi: Ular kichik ma'lumot bo'laklarini (kalit/qiymat juftliklari) saqlaydi.
- Muddati: Cookie-larga muddат belgilash mumkin. Agar belgilanmasa, brauzer yopilganda o'chib ketadi.
- Kirish: Cookie-larga `$_COOKIE` superglobali orqali kirish mumkin.
- Xavfsizlik: Cookie-lar XSS va CSRF kabi xavfsizlik muammolariga moyil bo'lishi mumkin. Maxfiy ma'lumotlardan qochish lozim.
- Hajm chegarasi: Odatda har bir cookie uchun taxminan 4KB bilan chegaralangan.

**`Session:`**

- Saqlash joyi: Sessiya ma'lumotlari serverda saqlanadi.
- Ma'lumot turi: Sessiyalar cookie-larga nisbatan ko'proq ma'lumot saqlashi mumkin.
- Muddati: Sessiyalar odatda faolsizlik davridan keyin tugaydi (standart — taxminan 20 daqiqa).
- Kirish: Sessiya ma'lumotlariga `$_SESSION` superglobali orqali kirish mumkin.
- Xavfsizlik: Sessiyalar odatda xavfsizroq, chunki ma'lumotlar mijoz tomoniga chiqarilmaydi.
- Sessiya ID: Foydalanuvchi brauzeriga cookie sifatida yuborilgan noyob sessiya ID foydalanuvchini uning sessiya ma'lumotlari bilan bog'laydi.

## 9. **Anonymous** functionlar

**Anonymous function** — bu nomsiz funksiya bo‘lib, uni o‘zgaruvchiga tayinlab yoki boshqa funksiyaga argument sifatida berib ishlatish mumkin.

### Sintaksis

```php
$greet = function($name) {
    return "Hello, $name";
};

echo $greet("Ali");
```

Bu yerda:

- `function($name) { ... }` → anonymous function
- `$greet` → funksiyani saqlayotgan o‘zgaruvchi
- `$greet("Ali")` → funksiyani chaqirish

### Callback sifatida ishlatilishi

Anonymous functionlar ko‘pincha **callback** sifatida ishlatiladi.

```php
$numbers = [1, 2, 3, 4];

$squared = array_map(function($n) {
    return $n * $n;
}, $numbers);

// yoki $squared = array_map(fn($n) => $n * $n, $numbers);

print_r($squared);
```

Natija:

```
[1, 4, 9, 16]
```

### Tashqi o‘zgaruvchini olish (`use`)

Anonymous function tashqi scope dagi o‘zgaruvchini **`use`** orqali olishi mumkin.

```php
$message = "Salom";

$greet = function($name) use ($message) {
    return "$message, $name";
};

echo $greet("Ali");
```

Natija:

```
Salom, Ali
```

PHP **Anonymous function**:

- nomi bo‘lmagan funksiya
- o‘zgaruvchiga saqlanishi mumkin
- callback sifatida ishlatiladi
- `use` orqali tashqi o‘zgaruvchilarni qabul qilishi mumkin

### Ko‘p ishlatiladigan joylar

- `array_map()`
- `array_filter()`
- `array_reduce()`
- event / callback funksiyalar

## 10. PHPda **SHELL** komandalari

**PHP Shell komandalar** — PHP dasturi ichidan tizimning terminal buyruqlarini bajarish va ularning natijasini olish uchun ishlatiladigan mexanizm.

---

### Asosiy funksiyalar

### 1. `shell_exec()`

Terminal komandani bajaradi va natijani **string** sifatida qaytaradi.

```php
$output = shell_exec("ls -l");
echo $output;
```

---

### 2. `exec()`

Komandani bajaradi va natijani **array** ko‘rinishida olish mumkin.

```php
exec("ls -l", $output);

print_r($output);
```

---

### 3. `system()`

Komandani bajaradi va natijani **to‘g‘ridan-to‘g‘ri ekranga chiqaradi**.

```php
system("ls -l");
```

---

### 4. `passthru()`

Ko‘pincha **binary output** (masalan video, zip, image) uchun ishlatiladi.

```php
passthru("tar -czf backup.tar.gz project/");
```

---

### 5. `command` (backtick operator)

Shell komandani yozishning qisqa sintaksisi.

```php
$output = `ls -l`;
echo $output;
```

---

### Misol

```php
$path = "/home/mirrrjr/dev/php/intervue";

$result = shell_exec("ls $path");

echo $result;
```

Bu kod serverdagi papka ichidagi fayllar ro‘yxatini chiqaradi.

---

### Muhim xavfsizlik masalasi

Shell komandalar bilan ishlaganda **Command Injection** xavfi mavjud.

Masalan:

```php
$user_input = $_GET['file'];
shell_exec("cat $user_input");
```

Agar foydalanuvchi zararli buyruq yuborsa, serverda boshqa komandalar ham bajarilishi mumkin.

Shuning uchun quyidagilar ishlatiladi:

```php
escapeshellarg()
escapeshellcmd()
```

Misol:

```php
$file = escapeshellarg($_GET['file']);
shell_exec("cat $file");
```

---

### Qayerlarda ishlatiladi

- backup yaratish (`tar`, `zip`, `gzip`)
- server monitoring (`top`, `df`, `uptime`)
- git komandalarini ishga tushirish
- image/video processing (`ffmpeg`, `imagemagick`)
- deployment skriptlar

---

## 11. Pass by Reference

**Pass by Reference (referens orqali uzatish)** — bu funksiyaga argument yuborilganda **o‘zgaruvchining nusxasi emas, balki uning asl manzili (reference)** uzatiladigan usuldir. Natijada funksiya ichida o‘zgaruvchi o‘zgartirilsa, **tashqaridagi asl o‘zgaruvchi ham o‘zgaradi**.

PHP’da referens orqali uzatish uchun **`&`** belgisi ishlatiladi.

```php
function increment(&$num) {
    $num++;
}

$value = 5;
increment($value);

echo $value; // 6
```

Bu yerda:

- `&$num` → argument referens orqali uzatilmoqda
- funksiya ichida `$num` o‘zgarsa
- tashqaridagi `$value` ham o‘zgaradi

---

### Pass by Value (taqqoslash uchun)

Oddiy holatda PHP **pass by value** ishlatadi.

```php
function increment($num) {
    $num++;
}

$value = 5;
increment($value);

echo $value; // 5
```

Bu yerda:

- `$num` → `$value` ning **nusxasi**
- funksiya ichidagi o‘zgarish tashqariga ta’sir qilmaydi

---

### Referens bilan o‘zgaruvchi bog‘lash

PHP’da referens faqat funksiyada emas, o‘zgaruvchilar orasida ham ishlatiladi.

```php
$a = 10;
$b = &$a;

$b = 20;

echo $a; // 20
```

Bu yerda `$a` va `$b` **bir xil xotira manziliga ishora qiladi**.

---

### Qisqa xulosa

**Pass by Reference:**

- o‘zgaruvchi **manzili** uzatiladi
- funksiya ichidagi o‘zgarish **tashqi o‘zgaruvchiga ham ta’sir qiladi**
- PHP’da `&` belgisi bilan yoziladi

---

## 12. Garbage Collection va garbage collector

### Garbage Collection

**Garbage Collection** — bu dastur ishlashi davomida **endi ishlatilmayotgan xotira (memory) ni avtomatik ravishda bo‘shatish jarayoni**. Ya’ni dastur tomonidan foydalanilmay qolgan obyektlar yoki o‘zgaruvchilar xotiradan olib tashlanadi.

PHP’da bu jarayon **avtomatik** amalga oshadi va dasturchi ko‘pincha uni qo‘lda boshqarishi shart emas.

---

### Garbage Collector

**Garbage Collector** — bu **ishlatilmayotgan obyektlarni aniqlab, ularni xotiradan o‘chiradigan mexanizm** yoki tizim komponentidir. U dastur ishlash vaqtida xotirani nazorat qiladi va kerak bo‘lmagan ma’lumotlarni tozalaydi.

---

### PHP’da qanday ishlaydi

PHP asosan **reference counting** usulidan foydalanadi.

Har bir o‘zgaruvchi yoki obyekt nechta referensga ega ekanligi hisoblab boriladi.

Misol:

```php
$a = "Hello";
$b = $a;
```

Bu yerda:

- `"Hello"` qiymatining **2 ta referensi** bor (`$a` va `$b`)

Agar:

```php
unset($a);
```

bo‘lsa:

- reference soni **1 ga kamayadi**

Agar:

```php
unset($b);
```

bo‘lsa:

- reference soni **0 bo‘ladi**
- memory **avtomatik bo‘shatiladi**

---

### Circular Reference muammosi

Ba’zida obyektlar **bir-biriga referens bo‘lib qoladi** va reference count 0 ga tushmaydi.

```php
class A {
    public $ref;
}

$a = new A();
$b = new A();

$a->ref = $b;
$b->ref = $a;
```

Bu holatda:

- `$a` → `$b` ni ko‘rsatadi
- `$b` → `$a` ni ko‘rsatadi

Natijada **circular reference** yuz beradi.

PHP’da **Garbage Collector** aynan shunday holatlarni aniqlab, xotirani tozalaydi.

---

### Qo‘lda Garbage Collector chaqirish

PHP’da GC ni qo‘lda ham ishga tushirish mumkin:

```php
gc_collect_cycles();
```

Bu funksiya:

- circular reference larni tekshiradi
- foydalanilmayotgan obyektlarni o‘chiradi

---

### Qisqa xulosa

**Garbage Collection**

- ishlatilmayotgan xotirani tozalash jarayoni

**Garbage Collector**

- shu jarayonni amalga oshiradigan mexanizm

**PHP xotira boshqaruvi**

- reference counting
- circular reference aniqlash
- `gc_collect_cycles()` orqali qo‘lda ishga tushirish mumkin

---

PHP’da xotira boshqaruvi odatda **ikkita mexanizm kombinatsiyasi** orqali ishlaydi:

1. **Reference Counting**
2. **Garbage Collection (Cycle Collector)**

Quyida ularning farqi va qanday ishlashini tushuntiraman.

---

### 1. Reference Counting

**Reference Counting** — obyekt yoki qiymatga nechta o‘zgaruvchi murojaat qilayotganini hisoblash usuli.

Har bir qiymat uchun **reference counter** mavjud bo‘ladi.

### Misol

```php
$a = "Hello";
$b = $a;
$c = $a;
```

Holat:

```
"Hello"
   ↑
a, b, c
Reference count = 3
```

Agar:

```php
unset($a);
```

bo‘lsa:

```
"Hello"
   ↑
b, c
Reference count = 2
```

Agar oxirgi referens ham o‘chirilsa:

```php
unset($b);
unset($c);
```

```
Reference count = 0
```

Shunda **memory avtomatik bo‘shatiladi**.

Bu usul **juda tez ishlaydi**, chunki faqat counter tekshiriladi.

---

### 2. Muammo — Circular Reference

Reference counting **bitta holatda ishlamaydi**:

**circular reference**.

### Misol

```php
class Node {
    public $ref;
}

$a = new Node();
$b = new Node();

$a->ref = $b;
$b->ref = $a;

unset($a);
unset($b);
```

Memory holati:

```
a → b
↑   ↓
└───┘
```

Muammo:

- `$a` o‘chirildi
- `$b` o‘chirildi
- lekin ular **bir-biriga referens bo‘lib turibdi**

Natija:

```
reference count ≠ 0
```

Shuning uchun **memory leak** bo‘lishi mumkin.

---

### 3. Garbage Collector (Cycle Collector)

Shu muammoni hal qilish uchun PHP’da **Garbage Collector** bor.

U:

1. obyektlar grafigini tekshiradi
2. **circular reference** larni topadi
3. tashqi referens yo‘qligini aniqlaydi
4. xotirani tozalaydi

Diagramma:

```
Before GC

a → b
↑   ↓
└───┘

After GC

(memory freed)
```

---

### 4. Qo‘lda GC chaqirish

PHP’da GC ni qo‘lda ham ishga tushirish mumkin:

```php
gc_collect_cycles();
```

Bu funksiya:

- circular reference larni aniqlaydi
- ishlatilmayotgan obyektlarni o‘chiradi

---

### 5. Qisqa taqqoslash

|Mexanizm|Vazifasi|
|---|---|
|Reference Counting|oddiy referenslarni tez tozalaydi|
|Garbage Collector|circular reference larni aniqlab tozalaydi|

---

### 6. Muhim interview xulosasi

PHP memory management:

```
Reference Counting  → asosiy mexanizm
Garbage Collector   → circular reference ni tozalaydi
```

---

Agar xohlasangiz, yana **Senior PHP interviewlarda so‘raladigan 3 ta chuqur GC savoli** bor (Laravel va long-running PHP processlarda memory leak haqida).

## 13. Abstract class va interfacening farqi

**Abstract class** — bu to‘liq obyekt yaratilmaydigan (instansiya qilib bo‘lmaydigan) klass bo‘lib, u boshqa klasslar uchun **asos (base class)** sifatida xizmat qiladi. Unda **ham abstract metodlar, ham oddiy metodlar** bo‘lishi mumkin.

Misol:

```php
abstract class Animal {
    abstract public function makeSound();

    public function sleep() {
        echo "Sleeping...";
    }
}
```

---

**Interface** — bu klasslar uchun **faqat metodlar shablonini (contract)** belgilab beradigan tuzilma. Unda metodlar **faqat e’lon qilinadi**, lekin implementatsiya bo‘lmaydi.

Misol:

```php
interface Animal {
    public function makeSound();
}
```

---

### Asosiy farqlar

|Abstract Class|Interface|
|---|---|
|Abstract va oddiy metodlar bo‘lishi mumkin|Faqat metod e’loni bo‘ladi|
|Property (xususiyatlar) bo‘lishi mumkin|Property bo‘lmaydi|
|`extends` orqali meros olinadi|`implements` orqali ishlatiladi|
|Bir klass faqat **bitta abstract class** ni meros oladi|Bir klass **bir nechta interface** ni implement qilishi mumkin|

---

### Qisqa xulosa

- **Abstract class** → qisman tayyor klass (ba’zi metodlar yozilgan bo‘ladi)
- **Interface** → faqat metodlar shartnomasi (contract)

## 14. Trait nima?

**Trait** — bu PHP’da bir nechta klasslar o‘rtasida **kodni qayta ishlatish (code reuse)** uchun mo‘ljallangan tuzilma. Trait ichida metodlar yoziladi va ularni bir nechta klasslarga **`use`** orqali qo‘shish mumkin.

Trait **klass ham emas, interface ham emas**, u klasslarga qo‘shimcha funksionallik berish uchun ishlatiladi.

---

### Misol

```php
trait Logger {
    public function log($message) {
        echo "Log: $message";
    }
}

class User {
    use Logger;
}

$user = new User();
$user->log("User created");
```

Bu yerda:

- `Logger` → trait
- `use Logger` → trait metodlarini klassga qo‘shadi
- `User` klassi `log()` metodidan foydalanadi

---

### Traitning vazifasi

Trait asosan **multiple inheritance muammosini hal qilish** uchun ishlatiladi. PHP’da klass faqat bitta klassni `extends` qila oladi, lekin **bir nechta traitlarni `use` qilish mumkin**.

Misol:

```php
trait A {
    public function testA() {}
}

trait B {
    public function testB() {}
}

class Example {
    use A, B;
}
```

---

### Qisqa xulosa

**Trait**:

- kodni qayta ishlatish uchun ishlatiladi
- klass ichida `use` bilan qo‘shiladi
- bir klass bir nechta trait ishlatishi mumkin
- metodlar va property lar bo‘lishi mumkin

---

## 15. PHP da OOP (Object-Oriented Programming) Prinsiplari

OOP — bu dasturni **obyektlar** asosida quradigan paradigma. PHP da OOP ning 4 asosiy printsipi mavjud:

---

### 1. 🔒 Encapsulation (Inkapsulyatsiya)

Ma'lumotlarni va metodlarni bitta sinfga to'plash, tashqi kirishni cheklash.

```php
class BankAccount {
    private float $balance; // tashqaridan to'g'ridan-to'g'ri kirish mumkin emas

    public function __construct(float $initialBalance) {
        $this->balance = $initialBalance;
    }

    public function deposit(float $amount): void {
        if ($amount > 0) $this->balance += $amount;
    }

    public function getBalance(): float {
        return $this->balance;
    }
}

$account = new BankAccount(1000);
$account->deposit(500);
echo $account->getBalance(); // 1500
// echo $account->balance; // ❌ Xato! private
```

---

### 2. 🧬 Inheritance (Meros olish)

Bir sinf boshqa sinfning xususiyat va metodlarini meros qilib oladi.

```php
class Animal {
    public string $name;

    public function __construct(string $name) {
        $this->name = $name;
    }

    public function speak(): string {
        return "...";
    }
}

class Dog extends Animal {
    public function speak(): string {
        return "{$this->name} says: Woof!";
    }
}

class Cat extends Animal {
    public function speak(): string {
        return "{$this->name} says: Meow!";
    }
}

$dog = new Dog("Rex");
echo $dog->speak(); // Rex says: Woof!
```

---

### 3. 🎭 Polymorphism (Polimorfizm)

Bir xil interfeys orqali turli xil obyektlar bilan ishlash.

```php
interface Shape {
    public function area(): float;
}

class Circle implements Shape {
    public function __construct(private float $radius) {}

    public function area(): float {
        return M_PI * $this->radius ** 2;
    }
}

class Rectangle implements Shape {
    public function __construct(
        private float $width,
        private float $height
    ) {}

    public function area(): float {
        return $this->width * $this->height;
    }
}

// Bir xil funksiya har xil shakllar bilan ishlaydi
function printArea(Shape $shape): void {
    echo "Maydon: " . $shape->area() . "\n";
}

printArea(new Circle(5));       // Maydon: 78.54
printArea(new Rectangle(4, 6)); // Maydon: 24
```

---

### 4. 🫥 Abstraction (Abstraktsiya)

Murakkablikni yashirib, faqat kerakli qismni ko'rsatish.

```php
abstract class Payment {
    // Umumiy logika
    public function process(float $amount): void {
        $this->validate($amount);
        $this->charge($amount);
        $this->sendReceipt($amount);
    }

    // Har bir to'lov turi o'zicha amalga oshiradi
    abstract protected function charge(float $amount): void;

    private function validate(float $amount): void {
        if ($amount <= 0) throw new Exception("Noto'g'ri summa!");
    }

    private function sendReceipt(float $amount): void {
        echo "Chek yuborildi: $amount so'm\n";
    }
}

class CreditCard extends Payment {
    protected function charge(float $amount): void {
        echo "Kredit karta orqali {$amount} so'm yechildi\n";
    }
}

class PayPal extends Payment {
    protected function charge(float $amount): void {
        echo "PayPal orqali {$amount} so'm yechildi\n";
    }
}

(new CreditCard())->process(50000);
(new PayPal())->process(30000);
```

---

### 📊 Xulosa jadvali

|Prinsip|Maqsad|Kalit so'z|
|---|---|---|
|**Encapsulation**|Ma'lumotni himoya qilish|`private`, `protected`, `public`|
|**Inheritance**|Kodni qayta ishlatish|`extends`|
|**Polymorphism**|Moslashuvchanlik|`interface`, `implements`|
|**Abstraction**|Murakkablikni yashirish|`abstract`|

Bu to'rtta prinsip birgalikda kodni **tartibli, qayta ishlatiluvchi va kengaytiriluvchi** qiladi.

## 16. PHP da `final` kalit so'zi

`final` — sinfni **meros olishdan** yoki metodlarni **qayta yozishdan** (override) himoya qiladi.

---

### 1. `final` Sinf — meros olish mumkin emas

```php
final class Singleton {
    private static ?Singleton $instance = null;

    private function __construct() {}

    public static function getInstance(): Singleton {
        if (self::$instance === null) {
            self::$instance = new Singleton();
        }
        return self::$instance;
    }
}

// ❌ Xato! final sinfdan meros olish mumkin emas
class Child extends Singleton {}
// Fatal error: Class Child cannot extend final class Singleton
```

---

### 2. `final` Metod — qayta yozish mumkin emas

```php
class Payment {
    // Bu metodni hech kim o'zgartira olmaydi
    final public function process(float $amount): void {
        $this->validate($amount);
        $this->charge($amount);
    }

    protected function charge(float $amount): void {
        echo "To'lov: $amount\n";
    }

    private function validate(float $amount): void {
        if ($amount <= 0) throw new Exception("Xato summa!");
    }
}

class CreditCard extends Payment {
    protected function charge(float $amount): void {
        echo "Karta orqali: $amount\n"; // ✅ Bu mumkin
    }

    // ❌ Xato! final metodini override qilib bo'lmaydi
    public function process(float $amount): void {}
    // Fatal error: Cannot override final method Payment::process()
}
```

---

### Qachon ishlatish kerak?

|Holat|Sabab|
|---|---|
|**Xavfsizlik uchun**|Muhim biznes logikasi o'zgartirilmasin|
|**Singleton pattern**|Faqat bitta nusxa bo'lishi kerak|
|**Tezlik uchun**|PHP `final` sinflarni biroz tezroq ishlata oladi|
|**API dizayni**|Kutubxona foydalanuvchilari sinfni buzmasin|

---

### ⚠️ Eslatma

`final` **property** (o'zgaruvchi)larga ishlatib bo'lmaydi — faqat **sinf** va **metodlar** uchun.

```php
class Example {
    final public int $value = 10; // ❌ Xato! Ishlamaydi
}
```

## 17. PHP da `$this` va `self`

---

### `$this` — joriy obyektga ishora

`$this` — sinfdan **yaratilgan obyekt**ga murojaat qiladi. Faqat **instance metodlari** ichida ishlatiladi.

```php
class User {
    public string $name;
    public int $age;

    public function __construct(string $name, int $age) {
        $this->name = $name; // joriy obyektning $name si
        $this->age = $age;
    }

    public function introduce(): string {
        return "Men {$this->name}, yoshim {$this->age}"; // joriy obyekt
    }
}

$user1 = new User("Ali", 25);
$user2 = new User("Vali", 30);

echo $user1->introduce(); // Men Ali, yoshim 25
echo $user2->introduce(); // Men Vali, yoshim 30
// $this har bir obyekt uchun o'z qiymatini oladi
```

---

### `self` — sinfning o'ziga ishora

`self` — **sinf** ga murojaat qiladi (obyektga emas). `static` va `const` bilan ishlatiladi.

```php
class Counter {
    private static int $count = 0;
    const VERSION = "1.0";

    public function __construct() {
        self::$count++; // sinfning o'zgaruvchisiga murojaat
    }

    public static function getCount(): int {
        return self::$count; // self ishlatiladi, $this emas
    }

    public static function getVersion(): string {
        return self::VERSION;
    }
}

new Counter();
new Counter();
new Counter();

echo Counter::getCount();   // 3
echo Counter::getVersion(); // 1.0
```

---

### Farqini ko'rsatuvchi misol

```php
class Animal {
    public string $type = "Animal";
    public static string $planet = "Yer";

    public function getType(): string {
        return $this->type;    // ✅ obyekt o'zgaruvchisi
    }

    public static function getPlanet(): string {
        // return $this->planet; ❌ static metodda $this yo'q!
        return self::$planet;  // ✅ sinf o'zgaruvchisi
    }
}

$animal = new Animal();
echo $animal->getType();       // Animal   ($this orqali)
echo Animal::getPlanet();      // Yer      (self orqali)
```

---

### `self` vs `static` (bonus)

Meros olganda farq chiqadi:

```php
class ParentClass {
    public static function create(): static {
        return new self();   // har doim ParentClass yaratadi
    }

    public static function createStatic(): static {
        return new static(); // qaysi sinfdan chaqirilsa, shuni yaratadi
    }
}

class ChildClass extends ParentClass {}

$a = ChildClass::create();       // ParentClass obyekti  ⚠️
$b = ChildClass::createStatic(); // ChildClass obyekti   ✅
```

---

### 📊 Xulosa

||`$this`|`self`|
|---|---|---|
|**Nimaga ishora qiladi**|Obyektga|Sinfga|
|**Qayerda ishlatiladi**|Instance metodlarda|Static metodlarda, const|
|**Meros bilan**|Har bir obyekt uchun|Har doim shu sinf|
|**Sintaksis**|`$this->property`|`self::$property`|

## 18. PHP da Dependency Injection (DI)

**Dependency Injection** — obyekt o'ziga kerakli bog'liqliklarni (dependency) o'zi yaratmay, **tashqaridan qabul qiladi**.

---

### ❌ DI siz (yomon usul)

```php
class UserService {
    private Database $db;
    private Logger $logger;

    public function __construct() {
        // Bog'liqliklar ichida yaratilmoqda — muammo!
        $this->db = new MySQLDatabase();   // qattiq bog'liq
        $this->logger = new FileLogger();  // qattiq bog'liq
    }
}

// MySQLDatabase ni o'zgartirib bo'lmaydi
// Test yozish qiyin
```

---

### ✅ DI bilan (to'g'ri usul)

```php
interface Database {
    public function query(string $sql): array;
}

interface Logger {
    public function log(string $message): void;
}

class UserService {
    // Bog'liqliklar tashqaridan beriladi
    public function __construct(
        private Database $db,
        private Logger $logger
    ) {}

    public function getUser(int $id): array {
        $this->logger->log("User $id so'raldi");
        return $this->db->query("SELECT * FROM users WHERE id = $id");
    }
}

// Istalgan Database va Logger ni berib yuborish mumkin
$service = new UserService(
    new MySQLDatabase(),
    new FileLogger()
);
```

---

### DI ning 3 turi

### 1. Constructor Injection (eng ko'p ishlatiladi)

```php
class OrderService {
    public function __construct(
        private PaymentGateway $payment,
        private EmailService $email
    ) {}
}

$order = new OrderService(
    new StripePayment(),
    new SmtpEmail()
);
```

### 2. Setter Injection

```php
class ReportService {
    private Logger $logger;

    public function setLogger(Logger $logger): void {
        $this->logger = $logger;
    }

    public function generate(): void {
        $this->logger->log("Hisobot yaratildi");
    }
}

$report = new ReportService();
$report->setLogger(new FileLogger()); // kerak bo'lganda o'rnatiladi
```

### 3. Interface Injection

```php
interface LoggerAware {
    public function setLogger(Logger $logger): void;
}

class ProductService implements LoggerAware {
    private Logger $logger;

    public function setLogger(Logger $logger): void {
        $this->logger = $logger;
    }
}
```

---

### DI Container (avtomatik boshqaruv)

Katta loyihalarda bog'liqliklarni qo'lda berish qiyin. **DI Container** buni avtomatik qiladi:

```php
class Container {
    private array $bindings = [];

    // Bog'liqlikni ro'yxatga olish
    public function bind(string $abstract, callable $factory): void {
        $this->bindings[$abstract] = $factory;
    }

    // Bog'liqlikni olish
    public function make(string $abstract): mixed {
        if (isset($this->bindings[$abstract])) {
            return ($this->bindings[$abstract])($this);
        }
        throw new Exception("$abstract topilmadi");
    }
}

// Container sozlash
$container = new Container();

$container->bind(Database::class, fn() => new MySQLDatabase());
$container->bind(Logger::class, fn() => new FileLogger());

$container->bind(UserService::class, fn($c) => new UserService(
    $c->make(Database::class),
    $c->make(Logger::class)
));

// Foydalanish — bog'liqliklar avtomatik beriladi
$userService = $container->make(UserService::class);
```

---

### Testda afzalligi

```php
// Test uchun soxta (mock) obyekt beriladi
class MockDatabase implements Database {
    public function query(string $sql): array {
        return [["id" => 1, "name" => "Test User"]]; // real DB siz
    }
}

class MockLogger implements Logger {
    public array $logs = [];
    public function log(string $message): void {
        $this->logs[] = $message; // faylga yozmaydi
    }
}

// Test
$service = new UserService(new MockDatabase(), new MockLogger());
$user = $service->getUser(1);
// ✅ Real database kerak emas!
```

---

### 📊 Xulosa

||DI siz|DI bilan|
|---|---|---|
|**Bog'liqlik**|Ichida yaratiladi|Tashqaridan beriladi|
|**Test**|Qiyin|Oson (mock)|
|**Moslashuvchanlik**|Past|Yuqori|
|**Kodni almashtirish**|Qiyin|Oson|

> 💡 **Asosiy qoida:** "Sinflar o'zlariga kerakli narsalarni so'rasin, o'zlari yaratmasin!"

## 19. PHP da `throw`

**`throw`** — dasturda xato yoki kutilmagan holat yuz berganda **istisno (exception) otadi** va dastur normal oqimini to'xtatadi.

---

### Asosiy sintaksis

```php
throw new Exception("Xato xabari");
```

---

### Oddiy misol

```php
function divide(int $a, int $b): float {
    if ($b === 0) {
        throw new Exception("Nolga bo'lish mumkin emas!");
    }
    return $a / $b;
}

try {
    echo divide(10, 2);  // ✅ 5
    echo divide(10, 0);  // ❌ Exception otadi
} catch (Exception $e) {
    echo "Xato: " . $e->getMessage(); // Xato: Nolga bo'lish mumkin emas!
}
```

---

### try / catch / finally

```php
function getUser(int $id): array {
    if ($id <= 0) {
        throw new InvalidArgumentException("ID musbat bo'lishi kerak!");
    }
    if ($id > 1000) {
        throw new RuntimeException("Foydalanuvchi topilmadi!");
    }
    return ["id" => $id, "name" => "Ali"];
}

try {
    $user = getUser(-1);

} catch (InvalidArgumentException $e) {
    echo "Noto'g'ri argument: " . $e->getMessage();

} catch (RuntimeException $e) {
    echo "Runtime xato: " . $e->getMessage();

} finally {
    // Xato bo'lsa ham, bo'lmasa ham DOIM ishlaydi
    echo "Amal yakunlandi";
}
```

---

### Custom Exception (o'z xato sinfini yaratish)

```php
// O'z exception sinflarimiz
class ValidationException extends Exception {
    private array $errors;

    public function __construct(array $errors) {
        parent::__construct("Validatsiya xatosi");
        $this->errors = $errors;
    }

    public function getErrors(): array {
        return $this->errors;
    }
}

class NotFoundException extends Exception {
    public function __construct(string $model, int $id) {
        parent::__construct("$model #$id topilmadi");
    }
}

class AuthException extends Exception {}
```

```php
// Ishlatish
function createUser(array $data): void {
    $errors = [];

    if (empty($data['name'])) {
        $errors[] = "Ism kiritilmagan";
    }
    if (empty($data['email'])) {
        $errors[] = "Email kiritilmagan";
    }

    if (!empty($errors)) {
        throw new ValidationException($errors);
    }

    echo "Foydalanuvchi yaratildi!";
}

try {
    createUser([]);

} catch (ValidationException $e) {
    echo $e->getMessage() . "\n";
    print_r($e->getErrors());
    // Validatsiya xatosi
    // ["Ism kiritilmagan", "Email kiritilmagan"]

} catch (NotFoundException $e) {
    echo $e->getMessage();

} catch (Exception $e) {
    echo "Umumiy xato: " . $e->getMessage();
}
```

---

### Exception zanjiri (chaining)

```php
function connectDatabase(): void {
    try {
        // ulanish urinishi...
        throw new RuntimeException("Server javob bermadi");

    } catch (RuntimeException $e) {
        // Asl xatoni saqlab, yangi exception otamiz
        throw new Exception("Database ulanishda xato", previous: $e);
    }
}

try {
    connectDatabase();
} catch (Exception $e) {
    echo $e->getMessage() . "\n";           // Database ulanishda xato
    echo $e->getPrevious()->getMessage();   // Server javob bermadi
}
```

---

### `throw` expression (PHP 8+)

PHP 8 dan boshlab `throw` ni ifoda sifatida ishlatish mumkin:

```php
// Ternary ichida
$age = -1;
$result = $age > 0 ? $age : throw new InvalidArgumentException("Yosh noto'g'ri!");

// Null coalescing ichida
$config = null;
$value = $config ?? throw new Exception("Config topilmadi!");

// Arrow function ichida
$getUser = fn($id) => $id > 0 ? $id : throw new Exception("Xato ID!");
```

---

### Exception ierarxiyasi

```php
Throwable
├── Error                    // PHP ichki xatolar
│   ├── TypeError
│   ├── ParseError
│   └── DivisionByZeroError
└── Exception                // Dasturchi xatolari
    ├── RuntimeException
    ├── InvalidArgumentException
    ├── LogicException
    └── (sizning custom exception)
```

---

### 📊 Xulosa

|Kalit so'z|Vazifasi|
|---|---|
|`throw`|Xato otadi|
|`try`|Xato bo'lishi mumkin bo'lgan kod|
|`catch`|Xatoni ushlab oladi|
|`finally`|Har doim ishlaydi|
|`Exception`|Asosiy xato sinfi|

> 💡 **Qoida:** `throw` ni faqat **haqiqiy xato** holatlarida ishlating, oddiy oqim boshqaruvida emas!

## 20. **Class** nima?

👉 **Class (klass)** — bu **obyektlar uchun shablon (template)**.

---

### 🔹 Tushuncha:

Class ichida:

- **xususiyatlar (properties)**
- **harakatlar (methods)** bo‘ladi

---

### 🔹 Misol:

```php
class Car
{
	$color = "red";

  public function drive(self)
  {
        print("Car is moving");
  }
}
```

👉 Bu yerda `Car` — class

👉 undan yaratilgan obyekt — mashina

---

### 🔚 Xulosa:

👉 **Class — obyektlarni yaratish uchun model yoki qolip.**

## 21. **Object** nima?

👉 **Object (obyekt)** — bu **class asosida yaratilgan aniq nusxa (instance)**.

---

### 🔹 Tushuncha:

- Class → shablon
- Object → shu shablondan yaratilgan real obyekt

---

### 🔹 Misol:

```php
class Car
{
    $color = "red";
}
$car1 = new Car();
```

👉 `Car` — class

👉 `car1` — object

---

### 🔚 Xulosa:

👉 **Object — classdan yaratilgan real element (nusxa).**

## 22. **Access modifiers** nima?

**Access modifiers** — bu **class ichidagi property va methodlarga qayerdan kirish mumkinligini belgilaydi**.

---

### 🔹 Turlari:

### 1. `public`

- Hamma joydan kirish mumkin

```php
class Test {
    public $name;
}
```

---

### 2. `private`

- Faqat **shu class ichida** ishlatiladi

```php
class Test {
    private $name;
}
```

---

### 3. `protected`

- Shu class va **meros olgan (child) classlar** ichida ishlatiladi

```php
class Test {
    protected $name;
}
```

---

### 🔚 Xulosa:

👉 **Access modifiers** — ma’lumotni himoya qilish va nazorat qilish uchun ishlatiladi.

## 23. **PSR** nima?

👉 **PSR (PHP Standards Recommendation)** — bu **PHP kodlash va loyihalash uchun rasmiy standartlar majmui**.

---

### 🔹 Tushuncha:

- PSR **PHP Framework Interoperability Group (PHP-FIG)** tomonidan ishlab chiqiladi.
- Maqsad: **PHP loyihalarida kodni bir xil uslubda yozish va boshqa kutubxonalar bilan oson integratsiya qilish**.

---

### 🔹 Eng mashhur PSR’lar:

1. **PSR-1** — Basic Coding Standard (asosiy kodlash qoidalari)
2. **PSR-2 / PSR-12** — Coding Style Guide (formatlash va style qoidalari)
3. **PSR-4** — Autoloading Standard (classlarni avtomatik yuklash)

---

### 🔚 Xulosa:

👉 **PSR — PHP kodini tartibli, oson o‘qiladigan va boshqa loyihalar bilan mos qiluvchi standartlar to‘plami.**

## 24. **header()** metodining vazifasi

👉 **`header()`** — bu **PHP’da HTTP sarlavhalarini (headers) yuborish uchun ishlatiladigan funksiya**.

---

### 🔹 Tushuncha:

- Web serverga **brauzerga yoki mijozga qo‘shimcha ma’lumot yuborish** imkonini beradi.
- Masalan: **redirect qilish, content-type o‘rnatish, cookie yoki cache boshqarish**.

---

### 🔹 Misollar:

**1️⃣ Redirect qilish (boshqa sahifaga yo‘naltirish):**

```php
header("Location: https://example.com");
exit();
```

**2️⃣ Content-type o‘rnatish (JSON yuborish uchun):**

```php
header("Content-Type: application/json");
echo json_encode($data);
```

**3️⃣ Cache boshqarish:**

```php
header("Cache-Control: no-cache, must-revalidate");
```

---

### 🔚 Muhim eslatma:

- `header()` chaqirilishidan **oldin hech qanday HTML yoki echo bo‘lmasligi kerak**.
- Aks holda xatolik yuz beradi: _“Cannot modify header information — headers already sent”_.

---

Quyida PHP’da `header()` bilan ishlatiladigan eng muhim **HTTP sarlavhalari**ni jadval shaklida ko‘rsataman:

|**Header**|**Tavsif**|**Misol**|
|---|---|---|
|`Location`|Brauzerni boshqa URLga yo‘naltiradi (redirect)|`header("Location: https://example.com"); exit();`|
|`Content-Type`|Jo‘natilayotgan ma’lumot turi|`header("Content-Type: application/json");`|
|`Cache-Control`|Cache boshqarish|`header("Cache-Control: no-cache, must-revalidate");`|
|`Expires`|Ma’lumotning amal qilish muddati|`header("Expires: Tue, 01 Jan 2025 00:00:00 GMT");`|
|`Set-Cookie`|Cookie yaratish|`header("Set-Cookie: user=John; Path=/; HttpOnly");`|
|`Content-Disposition`|Fayl yuklab olish yoki inline ko‘rsatish|`header("Content-Disposition: attachment; filename=file.txt");`|
|`WWW-Authenticate`|Basic auth talab qilish|`header('WWW-Authenticate: Basic realm="My Realm"');`|
|`HTTP/1.1 404 Not Found`|HTTP status kodini o‘rnatish|`header("HTTP/1.1 404 Not Found");`|
|`Refresh`|Sahifani avtomatik yangilash yoki redirect|`header("Refresh:5; url=https://example.com");`|

---

### 🔹 Muhim qoidalar:

1. `header()` chaqirilishidan **oldin hech qanday output (echo, HTML, bo‘sh joy)** bo‘lmasligi kerak.
2. Redirect qilgandan keyin **`exit();`** ishlatish tavsiya qilinadi.
3. Bir nechta header’larni ketma-ket qo‘yish mumkin:

```php
header("Content-Type: application/json");
header("Cache-Control: no-cache");
```

---

## 25. **Type hinting** nima?

👉 **PHP’da type hinting** — bu **funksiya yoki method argumentlari va qaytadigan qiymatning turini belgilash** imkonini beruvchi mexanizm.

---

### 🔹 Tushuncha:

- PHP 7 va undan keyin rasmiy ravishda qo‘llab-quvvatlanadi.
- Maqsad: **kodni xavfsizroq va tushunarliroq qilish**, noto‘g‘ri turdagi qiymat yuborishni oldini olish.

---

### 🔹 Misollar:

**1️⃣ Argumentlar uchun:**

```php
function add(int $a, int $b) {
    return $a + $b;
}

echo add(2, 3); // 5
// add("2", 3); -> xatolik beradi
```

**2️⃣ Qaytish turi uchun:**

```php
function getName(): string {
    return "John";
}

$name = getName(); // $name tip: string
```

**3️⃣ Class / Object uchun:**

```php
class User {}

function setUser(User $user) {
    // faqat User obyektlari qabul qilinadi
}
```

---

### 🔹 Afzalliklari:

1. Kodni **to‘g‘ri ishlashini tekshiradi**
2. **Xatolarni erta aniqlash** imkonini beradi
3. Katta loyihalarda **kodni oson tushunish va integratsiya qilish**

---

## 26. **NAN** nima?

👉 **NaN (Not a Number)** — bu PHP’da **son emasligini bildiradigan maxsus qiymat**.

---

### 🔹 Qachon paydo bo‘ladi?

Matematik jihatdan noto‘g‘ri amallar natijasida:

```php
$result = sqrt(-1);
var_dump($result); // NaN
```

---

### 🔹 Tekshirish:

```php
is_nan($result); // true qaytaradi
```

---

### 🔹 Muhim:

- NaN hech qachon boshqa NaN bilan teng bo‘lmaydi

```php
var_dump(NAN == NAN); // false
```

---

### 🔚 Xulosa:

👉 **NaN — bu matematik jihatdan aniqlanmagan yoki noto‘g‘ri hisob natijasini bildiruvchi qiymat.**

## 27. **preg_match(), preg_match_all(), mb_ereg_match()**

👉 Bu funksiyalar PHP’da **matnni regex (regular expression) yordamida tekshirish** uchun ishlatiladi.

---

### 🔹 1. `preg_match()`

- Matnda **pattern bor-yo‘qligini tekshiradi**
- Faqat **birinchi mos kelgan natijani** topadi

```php
preg_match("/php/", "I love php"); // 1 (topildi)
```

👉 Agar topilsa `1`, topilmasa `0` qaytaradi.

---

### 🔹 2. `preg_match_all()`

- Matndagi **barcha mos kelgan natijalarni** topadi

```php
preg_match_all("/php/", "php is great, php is popular", $matches);
```

👉 `$matches` ichida barcha topilgan natijalar bo‘ladi.

---

### 🔹 3. `mb_ereg_match()`

- **Multibyte (UTF-8)** matnlar bilan ishlaydi
- Multilingual (masalan, o‘zbek, rus, arab harflari) uchun qulay

```php
mb_ereg_match("^[a-z]+$", "hello"); // true
```

👉 `mb_ereg_*` funksiyalar UTF-8 matnlarni to‘g‘ri ishlashini ta’minlaydi.

---

### 🔚 Xulosa:

- `preg_match()` → birinchi moslikni tekshiradi
- `preg_match_all()` → barcha mosliklarni topadi
- `mb_ereg_match()` → UTF-8 (multibyte) matnlar uchun regex tekshiruv

---

### 🔹 Regex nima?

👉 **Regex (regular expression)** — bu **matn ichidan ma’lum pattern (qolip)** ni topish, tekshirish yoki ajratib olish uchun ishlatiladigan qoidalar to‘plami.

---

### 🔹 Oddiy misol:

```php
preg_match("/php/", "I love php");
```

👉 Bu yerda `/php/` — pattern

👉 Matnda “php” bor-yo‘qligini tekshiradi

---

### 🔹 Asosiy belgilar:

### 1. `^` — boshlanish

```php
"/^hello/"
```

👉 Matn “hello” bilan boshlanishi kerak

---

### 2. `$` — tugash

```php
"/world$/"
```

👉 Matn “world” bilan tugashi kerak

---

### 3. `.` — istalgan belgi

```php
"/h.t/"
```

👉 “hat”, “hot”, “hit” → mos keladi

---

### 4. `*` 0 yoki ko‘p takrorlanish

```php
"/a*/"
```

👉 "", "a", "aaa" ham mos

---

### 5. `+` — 1 yoki ko‘p takrorlanish

```php
"/a+/"
```

👉 "a", "aaa" mos, lekin "" mos emas

---

### 6. `[]` — belgilar oralig‘i

```php
"/[a-z]/"
```

👉 kichik harflar

```php
"/[0-9]/"
```

👉 raqamlar

---

### 7. `{}` — takrorlanish soni

```php
"/a{3}/"
```

👉 aynan 3 ta “a”

---

### 🔹 Misol (email tekshirish):

```php
preg_match("/^[a-z0-9]+@[a-z]+\.[a-z]{2,}$/", "test@gmail.com");
```

👉 Email formatini tekshiradi

---

### 🔚 Xulosa:

👉 Regex — bu **matnni pattern orqali tekshirish va qidirish vositasi**

👉 PHP’da `preg_match`, `preg_match_all` kabi funksiyalar bilan ishlatiladi


## Link
<- [[PHP intervyu savollar]]