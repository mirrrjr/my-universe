Reja:
- PHP sinaksisi
- Commets
- Özgaruvçilar, constant
- Malumot turlari

---
## PHP sintaksisi

```php
<?php
echo "Salom dunyo";
>
```

---
## Comments

```php
// bir qatorli komment
#  bir qatorli ikkinçi komment

/*
	bu köp qatorli komment
*/
```

---
## Özgaruvçilar

```php
<?php

/*
	- $ beligisi bialan boşlanişi kerak
	- [A-Z, a-z] lotin harflari bilan boşlanişi mumkin 
	- patki chiziq (underscore) _ bilan boşlanişi mumkin
	  
	- sonlar yoki boşqa simvollar bilan boşlanişi mumkin emas
*/ 

echo "Özgaruvçilar";

$box = "Olma";
$ten = 10;
$name = "Mirsolih";

echo $name;

// Contants
define("FOO",     "something");
define("FOO2",    "something else");
define("FOO_BAR", "something more");
```

---
## Malumot turlari

```php
<?php

// string
$matn = "Assalomu alaykum";

// integer
$age = 28;

// float
$PI = 3.14;

// boolean
$a = true;
$b = false;

// NULL
$name = NULL;

var_dump($matn);

/*
	is_string()  - string'ni tekşiriş uçun
	is_integer() - integer'ni tekşiriş uçun
	is_bool()    - boolean'ni tekşiriş uçun
	is_null()    - null'ni tekşiriş uçun
*/
```

>[!NOTE] Eslab qoling
>`var_dump()` funksiyasi özgaruvçining tipi va qiymatini konsolga çiqarib beradi.

## Boshlangʻich tushunchalar boʻyicha vazifa

HTML va PHP yordamida quyidagi koʻrinishdagi jadvalni hosil qiling.
Ismlar va sonlarni koʻrsatishda oʻzgaruvchilardan foydalaning.
```markdown
---------------------
| Sardor   | $1000  |
---------------------
| Eshmat   | $1200  |
---------------------
| Toshmat  | $1500  |
---------------------
```
