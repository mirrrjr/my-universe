## 1. MySQL da `CHAR` va `VARCHAR` farqi

---

### `CHAR` — qat'iy uzunlik

`CHAR(n)` — har doim **aynan n ta belgini** saqlaydi. Kam belgi kiritilsa, **bo'sh joy bilan to'ldiriladi.**

```sql
CREATE TABLE test ( code CHAR(5) );

INSERT INTO test VALUES ('AB');    -- 'AB   ' saqlanadi (3 bo'sh joy)
INSERT INTO test VALUES ('ABCDE'); -- 'ABCDE' saqlanadi
```

---

### `VARCHAR` — o'zgaruvchan uzunlik

`VARCHAR(n)` — **kiritilgan belgini** saqlaydi, maksimum n ta. Ortiqcha joy sarflamaydi.

```sql
CREATE TABLE test (
    name VARCHAR(100)
);

INSERT INTO test VALUES ('Ali');       -- 3 belgi saqlaydi
INSERT INTO test VALUES ('Alibek');    -- 6 belgi saqlaydi
INSERT INTO test VALUES ('Ali Vali'); -- 8 belgi saqlaydi
```

---

### Xotira sarfi farqi

```sql
-- CHAR(10) ga 'Ali' saqlasak:
CHAR    → 'Ali       ' = 10 bayt (har doim)

-- VARCHAR(10) ga 'Ali' saqlasak:
VARCHAR → 'Ali' = 3 bayt + 1 bayt (uzunlik) = 4 bayt
```

|Qiymat|`CHAR(10)`|`VARCHAR(10)`|
|---|---|---|
|`'A'`|10 bayt|2 bayt|
|`'Ali'`|10 bayt|4 bayt|
|`'Alibek'`|10 bayt|7 bayt|
|`'Alibek123'`|10 bayt|10 bayt|

---

### Qachon `CHAR` ishlatish kerak?

Uzunligi **har doim bir xil** bo'lgan ma'lumotlar uchun:

```sql
CREATE TABLE users (
    -- Har doim 2 ta harf
    country_code    CHAR(2),    -- 'UZ', 'US', 'RU'

    -- Har doim 36 belgi
    uuid            CHAR(36),   -- '550e8400-e29b-41d4-a716'

    -- Har doim 60 belgi
    password_hash   CHAR(60),   -- bcrypt hash

    -- Har doim 10 raqam
    phone_code      CHAR(10)    -- '+99890...'
);
```

---

### Qachon `VARCHAR` ishlatish kerak?

Uzunligi **har xil** bo'lgan ma'lumotlar uchun:

```sql
CREATE TABLE products (
    name            VARCHAR(255),   -- har xil uzunlik
    description     VARCHAR(1000),  -- har xil uzunlik
    email           VARCHAR(100),   -- har xil uzunlik
    address         VARCHAR(500)    -- har xil uzunlik
);
```

---

### Tezlik farqi

```sql
-- CHAR tezroq:
-- Uzunligi bir xil bo'lgani uchun MySQL uni tezroq o'qiydi

-- VARCHAR sekinroq (lekin juda oz farq):
-- Har safar uzunlikni tekshirib oladi
```

```sql
-- Index qo'yishda CHAR biroz samaraliroq
CREATE INDEX idx_code ON users(country_code); -- CHAR — tez
CREATE INDEX idx_email ON users(email);       -- VARCHAR — biroz sekin
```

---

### Muhim farqlar jadvali

|Xususiyat|`CHAR`|`VARCHAR`|
|---|---|---|
|**Uzunlik**|Qat'iy (fixed)|O'zgaruvchan|
|**Bo'sh joy**|To'ldiriladi|To'ldirilmaydi|
|**Xotira**|Har doim n bayt|Haqiqiy + 1-2 bayt|
|**Tezlik**|Biroz tezroq|Biroz sekinroq|
|**Ishlatish**|Bir xil uzunlik|Har xil uzunlik|
|**Max hajm**|255 belgi|65,535 belgi|

---

### Amaliy misol

```sql
CREATE TABLE users (
    id              INT PRIMARY KEY AUTO_INCREMENT,

    -- CHAR — uzunligi doim bir xil
    gender          CHAR(1),        -- 'M' yoki 'F'
    country_code    CHAR(2),        -- 'UZ', 'US'
    status          CHAR(8),        -- 'active  ', 'inactive'

    -- VARCHAR — uzunligi har xil
    first_name      VARCHAR(50),
    last_name       VARCHAR(50),
    email           VARCHAR(100),
    bio             VARCHAR(500)
);
```

---

> 💡 **Asosiy qoida:**
> 
> - Uzunlik **doim bir xil** → `CHAR`
> - Uzunlik **har xil** → `VARCHAR`

## 2. MySQL da `FLOAT`, `DOUBLE` va `DECIMAL`

---

### `FLOAT` — taxminiy, kam xotira

```sql
FLOAT        -- 4 bayt, ~7 aniq raqam
FLOAT(p)     -- p = aniqlik darajasi (1-24 oralig'ida FLOAT)
```

```sql
CREATE TABLE sensors (
    temperature  FLOAT,    -- 36.6
    humidity     FLOAT,    -- 45.2
    battery      FLOAT     -- 98.5
);
```

---

### `DOUBLE` — taxminiy, yuqori aniqlik

```sql
DOUBLE        -- 8 bayt, ~15-16 aniq raqam
DOUBLE(p)     -- p = aniqlik darajasi (25-53 oralig'ida DOUBLE)
```

```sql
CREATE TABLE locations (
    latitude   DOUBLE,    -- 41.29949612234567
    longitude  DOUBLE     -- 69.24007345678901
);
```

---

### `DECIMAL` — aniq, hech qanday yaxlitlash yo'q

```sql
DECIMAL(M, D)
-- M = umumiy raqamlar soni (1-65)
-- D = kasr qismdagi raqamlar soni (0-30)
```

```sql
CREATE TABLE orders (
    price     DECIMAL(10, 2),   -- 99999999.99
    tax       DECIMAL(5, 2),    -- 999.99
    discount  DECIMAL(4, 2)     -- 99.99
);
```

---

### Aniqlik taqqoslash

```sql
CREATE TABLE precision_test (
    f  FLOAT,
    d  DOUBLE,
    dc DECIMAL(20, 10)
);

INSERT INTO precision_test VALUES (
    1234567.12345678,
    1234567.12345678,
    1234567.12345678
);

SELECT * FROM precision_test;
-- f  → 1234567.1      ← aniqlik yo'qoldi!
-- d  → 1234567.12346  ← biroz yo'qoldi
-- dc → 1234567.1234567800  ← to'liq aniq!
```

---

### Pul hisoblashda farq

```sql
CREATE TABLE payments (
    float_amount   FLOAT,
    double_amount  DOUBLE,
    exact_amount   DECIMAL(10, 2)
);

INSERT INTO payments VALUES (19.99, 19.99, 19.99);

SELECT
    float_amount  * 100,   -- 1999.0000992   ❌
    double_amount * 100,   -- 1999.0000000   ✅ (lekin ishonchsiz)
    exact_amount  * 100;   -- 1999.00        ✅
```

---

### Xotira sarfi

```sql
-- FLOAT
FLOAT  → 4 bayt (har doim)

-- DOUBLE
DOUBLE → 8 bayt (har doim)

-- DECIMAL — M ga qarab o'zgaradi
DECIMAL(5,  2) → 3 bayt   -- 999.99
DECIMAL(10, 2) → 5 bayt   -- 99999999.99
DECIMAL(20, 2) → 9 bayt   -- 999999999999999999.99
```

---

### Amaliy ishlatish

```sql
CREATE TABLE ecommerce (

    -- Narx, pul → DECIMAL
    price          DECIMAL(10, 2),    -- 99999999.99
    discount       DECIMAL(5, 2),     -- 999.99
    tax_rate       DECIMAL(4, 2),     -- 99.99

    -- GPS koordinata → DOUBLE
    latitude       DOUBLE,            -- 41.299496123456
    longitude      DOUBLE,            -- 69.240073456789

    -- Taxminiy o'lchov → FLOAT
    weight_kg      FLOAT,             -- 1.5
    rating         FLOAT,             -- 4.7
    temperature    FLOAT              -- 36.6
);
```

---

### Umumiy taqqoslash jadvali

|Xususiyat|`FLOAT`|`DOUBLE`|`DECIMAL`|
|---|---|---|---|
|**Xotira**|4 bayt|8 bayt|M ga qarab|
|**Aniqlik**|~7 raqam|~15-16 raqam|To'liq aniq|
|**Tezlik**|Eng tez|Tez|Sekinroq|
|**Yaxlitlash**|Bor ⚠️|Bor ⚠️|Yo'q ✅|
|**Pul uchun**|❌|❌|✅|
|**GPS uchun**|❌|✅|✅|
|**Ilmiy hisob**|❌|✅|✅|
|**Taxminiy qiymat**|✅|✅|✅|

---

### Qaysi birini tanlash?

```
Pul, moliya, bank         →  DECIMAL
GPS, koordinatalar        →  DOUBLE
Ilmiy hisoblash           →  DOUBLE
Harorat, og'irlik, reyting →  FLOAT
Tezlik muhim, taxminiy    →  FLOAT
```

---

> 💡 **Asosiy qoida:**
> 
> - **Aniqlik** muhim → `DECIMAL`
> - **Yuqori aniqlik** kerak → `DOUBLE`
> - **Xotira** muhim, taxminiy → `FLOAT`
> - **Pul** uchun → **har doim** `DECIMAL`!

## 3. MySQL va SQL ning farqi

### 🔹 SQL (Structured Query Language)

- Bu **dasturlash tili** (aniqrog‘i — so‘rovlar tili).

#### Ma’lumotlar bazasi bilan ishlash uchun ishlatiladi:

- ma’lumot qo‘shish (`INSERT`)
- o‘qish (`SELECT`)
- yangilash (`UPDATE`)
- o‘chirish (`DELETE`)
- SQL — bu **standart til**, ko‘plab DBMS (Database Management System) lar tomonidan qo‘llaniladi.

---

### 🔹 MySQL

- Bu **ma’lumotlar bazasini boshqarish tizimi (DBMS)**.
- SQL tilidan foydalanib ma’lumotlarni saqlaydi va boshqaradi.
- Uni Oracle Corporation ishlab chiqadi va qo‘llab-quvvatlaydi.

#### Boshqa DBMS lar ham bor:

- PostgreSQL
- Microsoft SQL Server
- SQLite

## 4. MySQL da IF bormi?

SQL’da `IF` ishlatilishi qaysi DBMS (masalan, MySQL) ga bog‘liq. Eng ko‘p uchraydigan variantlarni sodda qilib tushuntiraman:

---

### 1. `IF` funksiyasi (MySQL’da)

MySQL’da `IF()` funksiyasi bor:

```sql
SELECT IF(5 > 3, 'Ha', 'Yo‘q');
```

📌 Natija: `Ha`

**Sintaksis:**

```sql
IF(shart, true_bo‘lsa, false_bo‘lsa)
```

---

### 🔹 2. `CASE WHEN` (barcha SQL’da ishlaydi)

Bu universal usul — deyarli barcha SQL tizimlarda ishlaydi:

```sql
SELECT
  CASE
    WHEN age >= 18 THEN 'Katta'
    ELSE 'Kichik'
  END AS status
FROM users;
```

📌 Bu `IF` o‘rniga ishlatiladi.

---

### 🔹 3. `IF` statement (faqat prosedura ichida)

MySQL’da stored procedure yoki function ichida:

```sql
IF age >= 18 THEN
   SET status = 'Katta';
ELSE
   SET status = 'Kichik';
END IF;
```

---

### 🔸 Qachon qaysi biri ishlatiladi?

|Holat|Qanday yoziladi|
|---|---|
|Oddiy SELECT ichida|`IF()` yoki `CASE`|
|Ko‘p DBMS uchun|`CASE WHEN`|
|Prosedura ichida|`IF ... THEN`|

---

### 🔑 Qisqa xulosa:

- `IF()` → faqat MySQL’da qulay
- `CASE WHEN` → eng universal
- `IF THEN` → faqat procedural SQL’da

## 5. MySQL da FOR bormi?

SQL’da `FOR` tushunchasi boshqa dasturlash tillaridagi kabi keng ishlatilmaydi. U asosan **loop (takrorlash)** uchun ishlatiladi va ko‘proq procedural qismda (masalan, MySQL stored procedure larida) uchraydi.

---

### 🔹 1. MySQL’da `FOR` bormi?

❗ To‘g‘ridan-to‘g‘ri `FOR` loop **MySQL’da mavjud emas**.

MySQL o‘rniga quyidagilar ishlatiladi:

- `WHILE`
- `LOOP`
- `REPEAT`

---

### 🔹 2. `WHILE` bilan loop (MySQL’da)

```sql
SET i = 1;

WHILE i <= 5 DO
   SELECT i;
   SET i = i + 1;
END WHILE;
```

📌 Bu 1 dan 5 gacha chiqaradi.

---

### 🔹 3. `LOOP` ishlatish

```sql
SET i = 1;

my_loop: LOOP
   SELECT i;
   SET i = i + 1;

   IF i > 5 THEN
      LEAVE my_loop;
   END IF;
END LOOP;
```

---

### 🔹 4. Boshqa DBMS’da `FOR` mavjud

Masalan, PostgreSQL da `FOR` bor:

```sql
FOR i IN 1..5 LOOP
   RAISE NOTICE '%', i;
END LOOP;
```

---

### 🔸 Muhim tushuncha

SQL — bu asosan **set-based til**, ya’ni:

- Ko‘pincha loop ishlatish shart emas
- Bitta `SELECT` bilan ko‘p ma’lumotni olish mumkin

📌 Masalan:

```sql
SELECT * FROM users;
```

Bu barcha qatorlarni bir martada qaytaradi — loop kerak emas.

---

### 🔑 Xulosa:

- MySQL’da `FOR` yo‘q ❌
- O‘rniga `WHILE`, `LOOP`, `REPEAT` ishlatiladi ✅
- Ba’zi DBMS (masalan PostgreSQL) da `FOR` bor ✅
- SQL’da loop kam ishlatiladi, ko‘proq query orqali ishlanadi

## 6. MySQL **aggregate functions**

MySQL’da **aggregate (yig‘indi) funksiyalar** — bu bir nechta satrlar ustida hisob-kitob qilib, **bitta natija qaytaradigan funksiyalar**dir. Ular odatda `GROUP BY` bilan birga ishlatiladi, lekin alohida ham ishlatish mumkin.

Quyida eng ko‘p ishlatiladigan aggregate funksiyalarni tushuntiraman:

---

### 🔹 1. `COUNT()`

Satrlar sonini hisoblaydi.

**Sintaksis:**

```sql
SELECT COUNT(*) FROM table_name;
```

**Misol:**

```sql
SELECT COUNT(*) FROM students;
```

👉 `students` jadvalidagi barcha yozuvlar sonini qaytaradi.

---

### 🔹 2. `SUM()`

Berilgan ustundagi qiymatlarning yig‘indisini hisoblaydi.

```sql
SELECT SUM(salary) FROM employees;
```

👉 Barcha xodimlarning oyliklari yig‘indisi.

---

### 🔹 3. `AVG()`

O‘rtacha qiymatni hisoblaydi.

```sql
SELECT AVG(age) FROM users;
```

👉 Foydalanuvchilarning o‘rtacha yoshi.

---

### 🔹 4. `MAX()`

Eng katta qiymatni topadi.

```sql
SELECT MAX(price) FROM products;
```

👉 Eng qimmat mahsulot narxi.

---

### 🔹 5. `MIN()`

Eng kichik qiymatni topadi.

```sql
SELECT MIN(price) FROM products;
```

👉 Eng arzon mahsulot narxi.

---

### 🔹 6. `GROUP BY` bilan ishlatish

Aggregate funksiyalar ko‘pincha guruhlab ishlatiladi.

**Misol:**

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

👉 Har bir bo‘limdagi xodimlar sonini chiqaradi.

---

### 🔹 7. `HAVING`

`HAVING` — aggregate natijalar bo‘yicha filter qilish uchun ishlatiladi.

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

👉 5 tadan ko‘p xodimi bor bo‘limlar.

---

### 🔹 Muhim eslatmalar:

- `WHERE` → oddiy filter
- `HAVING` → aggregate natijani filter qiladi
- `NULL` qiymatlar odatda hisobga olinmaydi (`COUNT(*)` bundan mustasno)

---

## 7. **TRUNCATE** ning vazifasi nima?

MySQL’da `TRUNCATE` va `DELETE` — ikkalasi ham jadvaldagi ma’lumotlarni o‘chirish uchun ishlatiladi, lekin ular orasida muhim farqlar bor.

---

### 🔹 `TRUNCATE` nima?

`TRUNCATE` — jadvaldagi **barcha yozuvlarni tezda tozalaydi (reset qiladi)**.

**Sintaksis:**

```sql
TRUNCATE TABLE table_name;
```

👉 Bu jadvalni “bo‘shatadi”, lekin strukturasi (ustunlar) saqlanib qoladi.

---

### 🔹 `DELETE` nima?

`DELETE` — jadvaldan yozuvlarni **shart asosida yoki to‘liq o‘chiradi**.

**Sintaksis:**

```sql
DELETE FROM table_name WHERE condition;
```

👉 `WHERE` bilan aniq yozuvlarni o‘chirish mumkin.

---

### 🔥 Asosiy farqlar

|Xususiyat|TRUNCATE|DELETE|
|---|---|---|
|O‘chirish turi|Hammasini birdan|Shart bilan yoki hammasini|
|Tezligi|Juda tez ⚡|Sekinroq|
|`WHERE` ishlatish|❌ Yo‘q|✅ Bor|
|Rollback (qaytarish)|❌ Yo‘q|✅ Bor (transactionda)|
|AUTO_INCREMENT|Reset bo‘ladi|O‘zgarmaydi|
|Log yozish|Minimal|Har bir satr yoziladi|
|Trigger ishlaydi|❌ Yo‘q|✅ Ha|

---

### 🔹 Misollar

### ✅ `TRUNCATE`

```sql
TRUNCATE TABLE students;
```

👉 `students` jadvalidagi hamma ma’lumot o‘chadi va ID qaytadan 1 dan boshlanadi.

---

### ✅ `DELETE`

```sql
DELETE FROM students WHERE age < 18;
```

👉 Faqat 18 yoshdan kichiklar o‘chiriladi.

---

### ✅ `DELETE` (hammasini o‘chirish)

```sql
DELETE FROM students;
```

👉 Bu ham hammasini o‘chiradi, lekin:

- sekinroq
- AUTO_INCREMENT reset bo‘lmaydi

---

### 🔹 Qachon qaysi biri ishlatiladi?

- 🧹 **TRUNCATE** → jadvalni to‘liq tozalash kerak bo‘lsa (tez va samarali)
    
- 🎯 **DELETE** → aniq yozuvlarni o‘chirish kerak bo‘lsa
    
- **`DELETE`** → indexni **har bir satr o‘chirilganda yangilaydi** (sekinroq)
    
- **`TRUNCATE`** → indexni **to‘liq reset qilib, qayta yaratadi** (juda tez)
    

👉 Xulosa:

**`TRUNCATE` indexga ko‘proq ta’sir qiladi**, `DELETE` esa faqat asta-sekin o‘zgartiradi.

---

## 8. MySQL komanda turlari

### SQL buyruqlari 4 guruhga bo'linadi:

|Tur|To'liq nomi|Buyruqlar|Vazifasi|
|---|---|---|---|
|**DDL**|Data Definition Language|CREATE, ALTER, DROP, TRUNCATE|Tuzilmani boshqaradi|
|**DML**|Data Manipulation Language|SELECT, INSERT, UPDATE, DELETE|Ma'lumotlarni boshqaradi|
|**DCL**|Data Control Language|GRANT, REVOKE|Ruxsatlarni boshqaradi|
|**TCL**|Transaction Control Language|BEGIN, COMMIT, ROLLBACK, SAVEPOINT|Tranzaksiyalarni boshqaradi|

### ALTER ning vazifasi nima?

👉 **`ALTER`** — jadvalning **strukturasi (tuzilishi)** ni o‘zgartirish uchun ishlatiladi.

---

### 🔹 Nimalar qilish mumkin?

- Ustun qo‘shish
- Ustun o‘chirish
- Ustun turini o‘zgartirish
- Jadval nomini o‘zgartirish

---

### 🔹 Misollar:

**Ustun qo‘shish:**

```sql
ALTER TABLE students ADD age INT;
```

**Ustun o‘chirish:**

```sql
ALTER TABLE students DROP COLUMN age;
```

**Ustun turini o‘zgartirish:**

```sql
ALTER TABLE students MODIFY age BIGINT;
```

---

### 🔚 Xulosa:

👉 `ALTER` — **jadvalni o‘zgartiradi (structure)**,

👉 ma’lumotni emas, balki **sxemani boshqaradi**.

## 9. **Protsedura** va **Funksiya** farqi nimada?

👉 **Protsedura** va **funksiya** — ikkalasi ham **ma’lumotlar bazasida bajariladigan kod bloklari**, lekin farqlari bor.

---

### 🔹 **Protsedura (Stored Procedure)**

- **Protsedura** — bu **bir nechta SQL buyruqlarini** bir joyga joylashtiradigan va **xabarlarni (output)** qaytaradigan kod blokidir.
- **Natija** qaytarmaydi (odatda).

**Misol:**

```sql
CREATE PROCEDURE GetEmployees()
BEGIN
    SELECT * FROM employees;
END;
```

👉 Protsedura — **faqat bajarish uchun** ishlatiladi, ma’lumot qaytarmaydi.

---

### 🔹 **Funksiya (Function)**

- **Funksiya** — bu **ma’lum bir qiymatni qaytaradigan** kod blokidir.
- **Qaytarilgan qiymat**ni **SELECT** yoki boshqa SQL buyruqlari bilan ishlatish mumkin.

**Misol:**

```sql
CREATE FUNCTION GetEmployeeCount()
RETURNS INT
BEGIN
    DECLARE employee_count INT;
    SELECT COUNT(*) INTO employee_count FROM employees;
    RETURN employee_count;
END;
```

👉 Funksiya — **qiymat qaytaradi**, bu qiymat SQL so‘rovlarida ishlatilishi mumkin.

---

### 🔹 Asosiy farqlar:

|Xususiyat|**Protsedura**|**Funksiya**|
|---|---|---|
|**Natija**|Natija qaytarmaydi (faqat bajariladi)|Qiymat qaytaradi|
|**Ishlatish**|`CALL` bilan chaqiriladi|`SELECT` yoki boshqa SQL buyruqlarida ishlatiladi|
|**Qaytarish**|Qaytarilmaydi|Ma'lum bir qiymat qaytaradi|
|**Ishlash**|Asosan ma’lumotni o‘zgartirish (INSERT, UPDATE)|Faqat o‘qish (SELECT) va hisob-kitob qilish|

---

### 🔚 Xulosa:

👉 **Protsedura** — bajarish uchun,

👉 **Funksiya** — qiymat qaytarish uchun ishlatiladi.


## Link
<- [[PHP intervyu savollar]]