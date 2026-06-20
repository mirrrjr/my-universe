---
type: qa
tags:
  - database
  - backend
---
## 🟢 Junior Darajasi

### 1. PostgreSQL nima va u boshqa ma'lumotlar bazalaridan qanday farq qiladi?

PostgreSQL — ochiq manbali, ob'ektga yo'naltirilgan relyatsion ma'lumotlar bazasi boshqaruv tizimi (RDBMS). 1986-yilda Berkeley universiteti tomonidan yaratilgan bo'lib, ACID standartlarini to'liq qo'llab-quvvatlovchi eng kuchli tizimlardan biri hisoblanadi.

**Boshqa bazalardan farqi:**

|Xususiyat|PostgreSQL|MySQL|SQLite|
|---|---|---|---|
|Arxitektura|Server-based|Server-based|Fayl asosida|
|JSON/JSONB|✅ Kuchli|Cheklangan|❌|
|Full-text search|✅|Cheklangan|❌|
|Kengaytmalar|✅ Ko'p|Cheklangan|❌|
|Parallel so'rovlar|✅|Cheklangan|❌|

> 💡 **Eslatma:** PostgreSQL MVCC (Multi-Version Concurrency Control) ishlatadi — bu bir vaqtda ko'p tranzaksiyani bloklashsiz bajarishga imkon beradi.

---

### 2. PRIMARY KEY va UNIQUE constraint orasidagi farq nima?

Ikkalasi ham ustundagi qiymatlarning noyobligini ta'minlaydi, lekin muhim farqlari bor:

|Xususiyat|PRIMARY KEY|UNIQUE|
|---|---|---|
|NULL qiymat|❌ Ruxsat yo'q|✅ Ruxsat bor (bir nechta NULL)|
|Soni|Jadvalda faqat 1 ta|Ko'p bo'lishi mumkin|
|Index|Avtomatik yaratiladi|Avtomatik yaratiladi|
|Maqsad|Asosiy identifikator|Qo'shimcha yagonalik|

```sql
CREATE TABLE foydalanuvchilar (
id        SERIAL PRIMARY KEY,       -- NULL bo'lmaydi, yagona
email     VARCHAR(255) UNIQUE,      -- NULL bo'lishi mumkin
username  VARCHAR(50) UNIQUE NOT NULL -- NULL bo'lmaydi, yagona
);
```

---

### 3. JOIN turlari qanday? INNER JOIN va LEFT JOIN farqini tushuntiring.

JOIN — ikki yoki undan ortiq jadvallarni bog'lash uchun ishlatiladi.

|JOIN turi|Natija|
|---|---|
|INNER JOIN|Faqat ikkala jadvalda mos qatorlar|
|LEFT JOIN|Chap jadval hammasi + o'ngdan moslar (mos kelmasa NULL)|
|RIGHT JOIN|O'ng jadval hammasi + chapdan moslar|
|FULL OUTER JOIN|Ikkala jadvaldagi barcha qatorlar|
|CROSS JOIN|Barcha kombinatsiyalar (Kartezian ko'paytma)|

```sql
-- INNER JOIN: faqat buyurtmasi bor mijozlar
SELECT m.ism, b.summa
FROM mijozlar m
INNER JOIN buyurtmalar b ON m.id = b.mijoz_id;

-- LEFT JOIN: buyurtmasi yo'q mijozlar ham ko'rinadi
SELECT m.ism, b.summa
FROM mijozlar m
LEFT JOIN buyurtmalar b ON m.id = b.mijoz_id;
-- buyurtmasi yo'q mijozlar uchun b.summa = NULL
```

---

### 4. WHERE va HAVING farqi nima?

||WHERE|HAVING|
|---|---|---|
|Qachon ishlaydi|GROUP BY **dan oldin**|GROUP BY **dan keyin**|
|Nimalarga qo'llanadi|Alohida qatorlarga|Guruh natijalariga|
|Agregat funksiya|❌ Ishlatib bo'lmaydi|✅ Ishlatish mumkin|

```sql
-- WHERE: guruhlanishdan oldin filtr
SELECT bolim, COUNT(*) AS xodimlar_soni
FROM xodimlar
WHERE oylik > 5000000     -- avval filtr
GROUP BY bolim;

-- HAVING: guruhlanishdan keyin filtr
SELECT bolim, COUNT(*) AS xodimlar_soni
FROM xodimlar
GROUP BY bo'lim
HAVING COUNT(*) > 5;      -- guruh natijasiga filtr
```

---

### 5. NULL qiymat bilan ishlashda qanday ehtiyotkorlik kerak?

NULL — qiymat yo'qligini bildiradi (0 yoki bo'sh satr emas). NULL bilan oddiy taqqoslash operatorlari ishlamaydi.

**Muhim qoidalar:**

- `NULL = NULL` → `FALSE` (natija noma'lum, `UNKNOWN`)
- `NULL + 5` → `NULL` (NULL har qanday hisob-kitobda tarqaladi)
- Faqat `IS NULL` yoki `IS NOT NULL` to'g'ri ishlaydi

```sql
-- NOTO'G'RI:
SELECT * FROM mahsulotlar WHERE tavsif = NULL;  -- hech narsa qaytarmaydi!

-- TO'G'RI:
SELECT * FROM mahsulotlar WHERE tavsif IS NULL;

-- COALESCE: NULL o'rniga standart qiymat qaytaradi
SELECT ism, COALESCE(telefon, 'Kiritilmagan') AS tel
FROM mijozlar;

-- NULLIF: agar qiymat berilganga teng bo'lsa NULL qaytaradi
SELECT NULLIF(bolinuvchi, 0);  -- nolga bo'linishdan himoya
```

> 💡 **Eslatma:** `COALESCE()` birinchi NULL bo'lmagan qiymatni qaytaradi. `NULLIF(a, b)` — a = b bo'lsa NULL, aks holda a ni qaytaradi.

---

### 6. SERIAL va SEQUENCE nima? Auto-increment qanday ishlaydi?

SERIAL — PostgreSQL'da INTEGER tipiga sequence biriktiradigan shortcut. Yangi qator qo'shilganda avtomatik raqam beradi.

```sql
-- SERIAL (qisqa usul)
CREATE TABLE mahsulotlar (
id   SERIAL PRIMARY KEY,
nomi VARCHAR(100)
);

-- Yuqoridagi aslida shuni bajaradi:
CREATE SEQUENCE mahsulotlar_id_seq;
CREATE TABLE mahsulotlar (
id   INTEGER DEFAULT nextval('mahsulotlar_id_seq') PRIMARY KEY,
nomi VARCHAR(100)
);

-- PostgreSQL 10+: IDENTITY (SQL standarti)
CREATE TABLE mahsulotlar (
id   INTEGER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
nomi VARCHAR(100)
);

-- Sequence'ni qo'lda boshqarish
SELECT nextval('mahsulotlar_id_seq');    -- keyingi qiymat
SELECT currval('mahsulotlar_id_seq');    -- joriy qiymat
SELECT setval('mahsulotlar_id_seq', 100); -- qiymatni o'rnatish
```

---

### 7. DDL, DML, DCL va TCL nima?

SQL buyruqlari 4 guruhga bo'linadi:

|Tur|To'liq nomi|Buyruqlar|Vazifasi|
|---|---|---|---|
|**DDL**|Data Definition Language|CREATE, ALTER, DROP, TRUNCATE|Tuzilmani boshqaradi|
|**DML**|Data Manipulation Language|SELECT, INSERT, UPDATE, DELETE|Ma'lumotlarni boshqaradi|
|**DCL**|Data Control Language|GRANT, REVOKE|Ruxsatlarni boshqaradi|
|**TCL**|Transaction Control Language|BEGIN, COMMIT, ROLLBACK, SAVEPOINT|Tranzaksiyalarni boshqaradi|

```sql
-- DDL
CREATE TABLE test (id SERIAL);
ALTER TABLE test ADD COLUMN nomi TEXT;

-- DML
INSERT INTO test (nomi) VALUES ('birinchi');
UPDATE test SET nomi = 'yangilandi' WHERE id = 1;

-- DCL
GRANT SELECT ON test TO foydalanuvchi;
REVOKE INSERT ON test FROM foydalanuvchi;

-- TCL
BEGIN;
DELETE FROM test WHERE id = 1;
ROLLBACK;  -- o'chirish bekor bo'ldi
```

---

### 8. INDEX nima va nega kerak?

Index — ma'lumotlarni tezroq topish uchun ishlatiladigan maxsus ma'lumotlar tuzilmasi. Kitobdagi "mundarija" kabi ishlaydi.

**Index yaratmasdan:** Seq Scan — har qator tekshiriladi (O(n)) **Index bilan:** Index Scan — daraxt bo'ylab tez qidiruv (O(log n))

```sql
-- Oddiy index
CREATE INDEX idx_foydalanuvchilar_email
ON foydalanuvchilar (email);

-- Ko'p ustunli index (composite)
CREATE INDEX idx_buyurtmalar_sana_holat
ON buyurtmalar (sana, holat);

-- Index ishlatilishini tekshirish
EXPLAIN ANALYZE
SELECT * FROM foydalanuvchilar WHERE email = 'test@test.com';
-- "Index Scan" ko'rinsa - index ishlayapti ✅
-- "Seq Scan" ko'rinsa - index ishlatilmayapti ⚠️
```

> 💡 **Eslatma:** Index qidiruvni tezlashtiradi, lekin INSERT/UPDATE/DELETE ni sekinlashtiradi va disk joyini egallaydi. Har qanday ustunga index qo'yish shart emas.

---

### 9. TRUNCATE va DELETE farqi nima?

|Xususiyat|DELETE|TRUNCATE|
|---|---|---|
|WHERE sharti|✅ Ishlatish mumkin|❌ Ishlatib bo'lmaydi|
|Tezlik|Sekin (qator-qator)|Juda tez|
|ROLLBACK|✅ Mumkin|✅ PostgreSQL'da mumkin|
|Trigger|✅ Ishga tushadi|❌ Ishga tushmaydi|
|Sequence reset|❌|✅ RESTART IDENTITY bilan|

```sql
-- DELETE: ma'lum qatorlarni o'chirish
DELETE FROM log_jadval WHERE sana < '2023-01-01';

-- TRUNCATE: hammasini tozalash (juda tez)
TRUNCATE TABLE vaqtinchalik_malumotlar;

-- TRUNCATE + sequence reset + bog'liq jadvallar
TRUNCATE TABLE mahsulotlar RESTART IDENTITY CASCADE;
```

---

### 10. Subquery (ichma-ich so'rov) nima? Qachon ishlatiladi?

Subquery — boshqa so'rov ichida joylashgan SQL so'rov. Murakkab mantiqni bosqichlarga bo'lib yozishga yordam beradi.

```sql
-- WHERE ichida: o'rtacha oylikdan yuqori xodimlar
SELECT ism, oylik
FROM xodimlar
WHERE oylik > (
SELECT AVG(oylik) FROM xodimlar
);

-- FROM ichida (derived table)
SELECT bolim, o_oylik
FROM (
SELECT bolim, AVG(oylik) AS o_oylik
FROM xodimlar
GROUP BY bolim
) AS bolim_statistika
WHERE o_oylik > 7000000;

-- IN bilan: ma'lum kategoriyalardagi mahsulotlar
SELECT nomi FROM mahsulotlar
WHERE kategori_id IN (
SELECT id FROM kategoriyalar WHERE turi = 'elektronika'
);
```

> 💡 **Eslatma:** Ko'p hollarda subquery o'rniga JOIN yoki CTE (WITH) ishlatish tezroq va o'qilishi osonroq bo'ladi.

---

## 🔵 Middle Darajasi

### 11. ACID xususiyatlari nima? PostgreSQL ularni qanday ta'minlaydi?

ACID — tranzaksiya ishonchliligi uchun 4 ta xususiyat:

|Harf|Xususiyat|Ma'nosi|PostgreSQL qanday ta'minlaydi|
|---|---|---|---|
|**A**|Atomicity (Atomarlik)|Yo to'liq bajariladi, yo bekor|WAL (Write-Ahead Logging)|
|**C**|Consistency (Izchillik)|Ma'lumot doim yaroqli|CHECK, FOREIGN KEY constraintlar|
|**I**|Isolation (Izolyatsiya)|Parallel tranzaksiyalar xalaqit bermaydi|MVCC|
|**D**|Durability (Doimiylik)|COMMIT qilingan yo'qolmaydi|WAL + fsync|

```sql
-- Atomarlik namunasi: pul o'tkazish
BEGIN;
UPDATE hisoblar SET balans = balans - 1000000 WHERE id = 1;
UPDATE hisoblar SET balans = balans + 1000000 WHERE id = 2;
COMMIT;  -- ikkisi birga bajariladi, biri muvaffaqiyatsiz bo'lsa ROLLBACK

-- Izolyatsiya darajasini o'rnatish
BEGIN ISOLATION LEVEL SERIALIZABLE;
SELECT * FROM buyurtmalar WHERE holat = 'yangi';
-- boshqa tranzaksiya bu vaqtda o'zgartira olmaydi
COMMIT;
```

> 💡 **MVCC haqida:** Har bir tranzaksiya ma'lumotning o'z snapshotini ko'radi. Read operatsiyalar write ni, write esa read ni bloklamaydi.

---

### 12. CTE (Common Table Expression) nima? WITH operatori qanday ishlaydi?

CTE — murakkab so'rovni oqilona bo'laklarga bo'lish imkonini beruvchi vaqtinchalik nom berilgan natija to'plami. `WITH` kalit so'zi bilan yoziladi.

**Afzalliklari:** o'qilishi osonroq, qayta ishlatish mumkin, rekursiv so'rovlar yozish mumkin.

```sql
-- Oddiy CTE
WITH yuqori_oyliklar AS (
SELECT bolim, AVG(oylik) AS o_oylik
FROM xodimlar
GROUP BY bolim
HAVING AVG(oylik) > 8000000
)
SELECT x.ism, yo.o_oylik
FROM xodimlar x
JOIN yuqori_oyliklar yo ON x.bolim = yo.bolim;

-- Bir nechta CTE
WITH
aktiv_mijozlar AS (
SELECT id, ism FROM mijozlar WHERE holat = 'aktiv'
),
buyurtma_soni AS (
SELECT mijoz_id, COUNT(*) AS soni FROM buyurtmalar GROUP BY mijoz_id
)
SELECT am.ism, bs.soni
FROM aktiv_mijozlar am
JOIN buyurtma_soni bs ON am.id = bs.mijoz_id;

-- Rekursiv CTE: tashkilot ierarxiyasi
WITH RECURSIVE ierarxiya AS (
-- Boshlanish: top-level xodimlar (rahbarsiz)
SELECT id, ism, rahbar_id, 1 AS daraja
FROM xodimlar WHERE rahbar_id IS NULL

UNION ALL

-- Rekursiv qism: pastki darajalar
SELECT x.id, x.ism, x.rahbar_id, i.daraja + 1
FROM xodimlar x
JOIN ierarxiya i ON x.rahbar_id = i.id
)
SELECT daraja, ism FROM ierarxiya ORDER BY daraja, ism;
```

---

### 13. Window funksiyalari nima? OVER(), PARTITION BY, ROW_NUMBER() tushuntiring.

Window funksiyalar — `GROUP BY` kabi guruhlamasdan, qatorlar orasida hisob-kitob olib boradi. Har bir qator o'z qiymatini saqlaydi.

**Asosiy window funksiyalar:**

|Funksiya|Vazifasi|
|---|---|
|`ROW_NUMBER()`|Noyob tartib raqami (1,2,3,...)|
|`RANK()`|Reyting (tenglar bo'shliq bilan: 1,1,3)|
|`DENSE_RANK()`|Reyting (tenglar bo'shliqsiz: 1,1,2)|
|`LAG(n)`|Oldingi qator qiymati|
|`LEAD(n)`|Keyingi qator qiymati|
|`SUM() OVER`|Kumulyativ yoki guruh summasi|
|`FIRST_VALUE()`|Oyna ichidagi birinchi qiymat|

```sql
-- Har bir bo'limda oylik bo'yicha raqamlash
SELECT
ism,
bolim,
oylik,
ROW_NUMBER() OVER (
PARTITION BY bolim
ORDER BY oylik DESC
) AS raqam,
SUM(oylik) OVER (PARTITION BY bolim) AS bolim_jami,
ROUND(oylik * 100.0 / SUM(oylik) OVER (PARTITION BY bolim), 2) AS foizi
FROM xodimlar;

-- Har bo'limdan eng yuqori oylikli xodimni olish
SELECT * FROM (
SELECT *, ROW_NUMBER() OVER (PARTITION BY bolim ORDER BY oylik DESC) AS rn
FROM xodimlar
) ranked
WHERE rn = 1;

-- Oldingi/keyingi qiymat: LAG/LEAD
SELECT
sana,
sotuv,
LAG(sotuv) OVER (ORDER BY sana) AS oldingi_sotuv,
sotuv - LAG(sotuv) OVER (ORDER BY sana) AS o'sish
FROM sotuv_statistika;
```

> 💡 **RANK vs DENSE_RANK:** `RANK()` tenglar orasida bo'shliq qoldiradi (1,1,3), `DENSE_RANK()` qoldirmaydi (1,1,2). `ROW_NUMBER()` esa doim noyob raqam beradi.

---

### 14. PostgreSQL'da tranzaksiya izolyatsiya darajalari qanday?

**Muammolar va darajalar:**

|Muammo|Tavsif|
|---|---|
|Dirty read|Commit qilinmagan ma'lumotni o'qish|
|Non-repeatable read|Bir tranzaksiyada bir xil so'rov turli natija beradi|
|Phantom read|Yangi qatorlar paydo bo'lib so'rov natijasi o'zgaradi|
|Serialization anomaly|Parallel tranzaksiyalar ketma-ket bajarilgandekdan farq qiladi|

|Daraja|Dirty read|Non-repeatable|Phantom read|
|---|---|---|---|
|READ UNCOMMITTED|✅ (PG'da yo'q)|Mumkin|Mumkin|
|READ COMMITTED (default)|❌|Mumkin|Mumkin|
|REPEATABLE READ|❌|❌|❌ (PG'da)|
|SERIALIZABLE|❌|❌|❌|

```sql
-- Izolyatsiya darajasini o'rnatish
BEGIN TRANSACTION ISOLATION LEVEL REPEATABLE READ;

-- Sessiya darajasida
SET default_transaction_isolation = 'serializable';

-- Joriy izolyatsiya darajasini ko'rish
SHOW transaction_isolation;
```

---

### 15. EXPLAIN va EXPLAIN ANALYZE qanday ishlatiladi?

`EXPLAIN` — PostgreSQL query planner qanday reja tuzganini ko'rsatadi (so'rovni bajarmaydi). `EXPLAIN ANALYZE` esa rejani bajaradi va haqiqiy vaqtni ham ko'rsatadi.

**Asosiy tushunchalar:**

- `cost=0.00..245.00` — birinchi natijaga va barcha natijaga yetish narxi
- `rows=12` — taxminiy qatorlar soni
- `actual time=0.023..1.234` — haqiqiy vaqt (ms)
- `loops=1` — qayta bajarish soni

```sql
EXPLAIN ANALYZE
SELECT * FROM buyurtmalar
WHERE mijoz_id = 123 AND sana > '2024-01-01';

-- Natija namunasi:
-- Seq Scan on buyurtmalar (cost=0.00..245.00 rows=12 width=64)
--   (actual time=0.023..1.234 rows=8 loops=1)
--   Filter: (mijoz_id = 123 AND sana > '2024-01-01')
--   Rows Removed by Filter: 4992
-- Planning Time: 0.5 ms
-- Execution Time: 1.3 ms

-- JSON formatda (to'liqroq ma'lumot)
EXPLAIN (FORMAT JSON, ANALYZE, BUFFERS)
SELECT * FROM buyurtmalar WHERE id = 1;

-- Vizual ko'rish uchun: explain.depesz.com yoki explain.dalibo.com
```

> 💡 **Seq Scan ko'rinsa** — index yo'q yoki ishlatilmayapti. `Rows Removed by Filter` katta bo'lsa — partial index kerak bo'lishi mumkin.

---

### 16. PostgreSQL'da INDEX turlari qanday?

|Index turi|Qachon ishlatish|Operatorlar|
|---|---|---|
|**B-tree** (default)|Skalyar qiymatlar, tartiblash|=, <, >, BETWEEN, LIKE 'abc%'|
|**Hash**|Faqat tenglik|=|
|**GIN**|Massivlar, JSONB, FTS|@>, <@, &&, @@|
|**GiST**|Geometrik, range, FTS|&&, @>, <@|
|**BRIN**|Katta, tartiblangan jadvallar|=, <, > (taxminiy)|
|**SP-GiST**|Nuqta, telefon, IP|=, <<, >>|

```sql
-- B-tree (default)
CREATE INDEX idx_email ON users (email);

-- GIN: JSONB ustunida qidirish
CREATE INDEX idx_meta_gin ON mahsulotlar USING GIN (meta_data);
SELECT * FROM mahsulotlar WHERE meta_data @> '{"rang": "qizil"}';

-- Partial index: faqat kerakli qatorlar uchun (kichik va tez)
CREATE INDEX idx_aktiv_foydalanuvchilar
ON users (email)
WHERE holat = 'aktiv';

-- Expression index: funksiya natijasiga index
CREATE INDEX idx_kichik_email
ON users (LOWER(email));

-- Covering index: qo'shimcha ustunlar bilan (index only scan)
CREATE INDEX idx_buyurtma_covering
ON buyurtmalar (mijoz_id)
INCLUDE (summa, sana);
```

---

### 17. Foreign Key va referential integrity nima?

Foreign Key — bir jadval ustuni boshqa jadvaldagi asosiy kalit bilan bog'liqligini ta'minlaydi.

**ON DELETE/UPDATE harakatlari:**

|Harakat|Nima bo'ladi|
|---|---|
|`CASCADE`|Ota o'chganda/o'zgarganda bola ham o'chadi/o'zgaradi|
|`SET NULL`|Bog'liq ustun NULL ga o'rnatiladi|
|`SET DEFAULT`|Standart qiymat o'rnatiladi|
|`RESTRICT`|Taqiqlanadi (xatolik qaytaradi)|
|`NO ACTION`|Default, kechiktirilgan tekshiruv|

```sql
CREATE TABLE kategoriyalar (
id   SERIAL PRIMARY KEY,
nomi VARCHAR(100)
);

CREATE TABLE mahsulotlar (
id          SERIAL PRIMARY KEY,
nomi        VARCHAR(100),
kategori_id INTEGER REFERENCES kategoriyalar(id)
          ON DELETE CASCADE      -- kategoriya o'chsa, mahsulot ham o'chadi
          ON UPDATE CASCADE      -- id o'zgarse, bog'liq ham o'zgaradi
);

-- ALTER bilan qo'shish
ALTER TABLE mahsulotlar
ADD CONSTRAINT fk_kategori
FOREIGN KEY (kategori_id) REFERENCES kategoriyalar(id)
ON DELETE SET NULL;

-- Foreign key'larni ko'rish
SELECT conname, conrelid::regclass, confrelid::regclass
FROM pg_constraint WHERE contype = 'f';
```

---

### 18. PostgreSQL'da JSONB vs JSON farqi nima?

|Xususiyat|JSON|JSONB|
|---|---|---|
|Saqlash|Matn (as-is)|Binary (parsed)|
|Yozish tezligi|Tezroq|Sekinroq|
|O'qish tezligi|Sekin (har safar parse)|Tez|
|Kalit tartibi|Saqlanadi|Saqlanmaydi (tartiblangan)|
|Takroriy kalitlar|Mumkin|Yo'q (oxirgisi qoladi)|
|GIN index|❌|✅|
|Ishlab chiqarishda|Kam ishlatiladi|**Tavsiya etiladi**|

```sql
CREATE TABLE mahsulotlar (
id        SERIAL PRIMARY KEY,
nomi      TEXT,
xususiyat JSONB  -- JSONB tavsiya etiladi
);

INSERT INTO mahsulotlar (nomi, xususiyat) VALUES (
'Telefon',
'{"rang": "qora", "xotira": 128, "teglar": ["yangi", "top"]}'
);

-- JSONB operatorlari
SELECT
xususiyat->'rang'           -- JSON qaytaradi: "qora"
, xususiyat->>'rang'          -- TEXT qaytaradi:  qora
, xususiyat->'teglar'->0      -- massiv elementi: "yangi"
, xususiyat#>>'{teglar,0}'    -- path orqali:      yangi
FROM mahsulotlar;

-- GIN index JSONB uchun
CREATE INDEX idx_xususiyat ON mahsulotlar USING GIN (xususiyat);
SELECT * FROM mahsulotlar WHERE xususiyat @> '{"rang": "qora"}';

-- JSONB funksiyalari
SELECT jsonb_keys(xususiyat) FROM mahsulotlar;
SELECT jsonb_set(xususiyat, '{rang}', '"ko''k"') FROM mahsulotlar;
```

> 💡 `->` JSON/JSONB qaytaradi, `->>` TEXT qaytaradi. `@>` operatori "o'z ichiga oladi" degani.

---

### 19. VIEW va MATERIALIZED VIEW farqi nima?

|Xususiyat|VIEW|MATERIALIZED VIEW|
|---|---|---|
|Ma'lumot saqlanadi|❌ (har safar hisoblaydi)|✅ (diskda saqlangan)|
|Yangilik|Doim yangi|REFRESH qilguncha eski|
|Tezlik|Sekin (katta so'rovda)|Tez|
|Index|❌|✅ Yaratish mumkin|
|Disk joyi|0|Jadval hajmidek|

```sql
-- Oddiy VIEW
CREATE VIEW aktiv_foydalanuvchilar AS
SELECT id, ism, email
FROM foydalanuvchilar
WHERE holat = 'aktiv';

-- MATERIALIZED VIEW
CREATE MATERIALIZED VIEW bo'lim_statistika AS
SELECT
bo'lim,
COUNT(*) AS xodimlar,
AVG(oylik) AS o'rtacha_oylik,
SUM(oylik) AS jami_oylik
FROM xodimlar
GROUP BY bo'lim
WITH DATA;  -- darhol to'ldirish

-- Yangilash (bloklaydi)
REFRESH MATERIALIZED VIEW bo'lim_statistika;

-- Yangilash (bloklamasdan - UNIQUE index kerak)
REFRESH MATERIALIZED VIEW CONCURRENTLY bo'lim_statistika;

-- Avtomatik yangilash (trigger orqali)
CREATE OR REPLACE FUNCTION refresh_bo'lim_statistika()
RETURNS TRIGGER AS $$
BEGIN
REFRESH MATERIALIZED VIEW CONCURRENTLY bo'lim_statistika;
RETURN NULL;
END;
$$ LANGUAGE plpgsql;
```

---

### 20. Stored procedure va Function farqi nima? PL/pgSQL qanday ishlaydi?

|Xususiyat|Function|Procedure|
|---|---|---|
|Qiymat qaytaradi|✅ Majburiy|Ixtiyoriy (OUT parametr)|
|SELECT ichida|✅ Ishlatish mumkin|❌|
|COMMIT/ROLLBACK|❌|✅ (PostgreSQL 11+)|
|Chaqirish|`SELECT func()`|`CALL proc()`|
|Tranzaksiya boshqarish|❌|✅|

```sql
-- Funksiya
CREATE OR REPLACE FUNCTION soliq_hisoblash(summa NUMERIC)
RETURNS NUMERIC AS $$
BEGIN
RETURN summa * 0.12;
END;
$$ LANGUAGE plpgsql;

SELECT soliq_hisoblash(1000000);  -- 120000

-- PL/pgSQL: murakkab funksiya
CREATE OR REPLACE FUNCTION pul_otkazish(
jo'natuvchi_id INT,
qabul_qiluvchi_id INT,
miqdor NUMERIC
) RETURNS TEXT AS $$
DECLARE
jo'natuvchi_balans NUMERIC;
BEGIN
SELECT balans INTO jo'natuvchi_balans
FROM hisoblar WHERE id = jo'natuvchi_id;

IF jo'natuvchi_balans < miqdor THEN
RETURN 'Mablag'' yetarli emas';
END IF;

UPDATE hisoblar SET balans = balans - miqdor WHERE id = jo'natuvchi_id;
UPDATE hisoblar SET balans = balans + miqdor WHERE id = qabul_qiluvchi_id;

RETURN 'Muvaffaqiyatli';
END;
$$ LANGUAGE plpgsql;
```

---

### 21. N+1 muammo nima va uni qanday hal qilish mumkin?

N+1 muammo — bitta asosiy so'rov (1) + har bir natija uchun alohida so'rov (N) natijasida paydo bo'ladigan ishlash muammosi.

**Misol:** 100 ta foydalanuvchining buyurtmalarini olish = 101 ta so'rov!

```sql
-- N+1 muammo (ORM kodida):
-- SELECT * FROM foydalanuvchilar        → 1 so'rov
-- SELECT * FROM buyurtmalar WHERE ...   → har foydalanuvchi uchun
-- = 1 + N so'rov, N katta bo'lsa juda sekin!

-- Yechim 1: JOIN bilan bitta so'rovga birlashtirish
SELECT
f.id, f.ism,
b.id AS buyurtma_id, b.summa
FROM foydalanuvchilar f
LEFT JOIN buyurtmalar b ON f.id = b.foydalanuvchi_id;

-- Yechim 2: JSON aggregatsiya (har foydalanuvchi uchun massiv)
SELECT
f.id,
f.ism,
json_agg(
json_build_object('id', b.id, 'summa', b.summa)
ORDER BY b.sana DESC
) FILTER (WHERE b.id IS NOT NULL) AS buyurtmalar
FROM foydalanuvchilar f
LEFT JOIN buyurtmalar b ON f.id = b.foydalanuvchi_id
GROUP BY f.id, f.ism;

-- Yechim 3: IN bilan batch
SELECT * FROM buyurtmalar
WHERE foydalanuvchi_id = ANY(ARRAY[1, 2, 3, ..., 100]);
```

> 💡 ORM'larda: Django → `select_related()` / `prefetch_related()`, SQLAlchemy → `joinedload()` / `selectinload()`, Rails → `includes()`.

---

### 22. Trigger nima? Qachon va qanday ishlatiladi?

Trigger — jadvalda ma'lum hodisa (INSERT, UPDATE, DELETE) sodir bo'lganda avtomatik chaqiriladigan funksiya.

```sql
-- Audit log uchun trigger funksiyasi
CREATE OR REPLACE FUNCTION audit_log()
RETURNS TRIGGER AS $$
BEGIN
IF TG_OP = 'DELETE' THEN
INSERT INTO audit_jadval(jadval, harakat, eski_qiymat, sana)
VALUES (TG_TABLE_NAME, 'DELETE', row_to_json(OLD), NOW());
RETURN OLD;
ELSIF TG_OP = 'UPDATE' THEN
INSERT INTO audit_jadval(jadval, harakat, eski_qiymat, yangi_qiymat, sana)
VALUES (TG_TABLE_NAME, 'UPDATE', row_to_json(OLD), row_to_json(NEW), NOW());
RETURN NEW;
ELSIF TG_OP = 'INSERT' THEN
INSERT INTO audit_jadval(jadval, harakat, yangi_qiymat, sana)
VALUES (TG_TABLE_NAME, 'INSERT', row_to_json(NEW), NOW());
RETURN NEW;
END IF;
END;
$$ LANGUAGE plpgsql;

-- Trigger'ni jadvalga bog'lash
CREATE TRIGGER buyurtmalar_audit
AFTER INSERT OR UPDATE OR DELETE ON buyurtmalar
FOR EACH ROW EXECUTE FUNCTION audit_log();
```

---

## 🔴 Senior Darajasi

### 23. PostgreSQL partitioning nima? Table partitioning turlari va qo'llanilishi.

Partitioning — katta jadvalni kichik qismlarga (partition) bo'lish. Katta hajmli ma'lumotlarda so'rov tezligini oshiradi.

**Partitioning turlari:**

|Tur|Qachon ishlatish|Misol|
|---|---|---|
|**RANGE**|Diapazon bo'yicha|Sanalar, raqamlar (oylik loglar)|
|**LIST**|Aniq qiymatlar bo'yicha|Mintaqa, status, kategoriya|
|**HASH**|Teng taqsimot uchun|Tasodifiy taqsimlash|

```sql
-- RANGE partitioning: oylik loglar
CREATE TABLE loglar (
id      BIGSERIAL,
sana    DATE NOT NULL,
xabar   TEXT
) PARTITION BY RANGE (sana);

-- Har oy uchun partition
CREATE TABLE loglar_2024_01 PARTITION OF loglar
FOR VALUES FROM ('2024-01-01') TO ('2024-02-01');

CREATE TABLE loglar_2024_02 PARTITION OF loglar
FOR VALUES FROM ('2024-02-01') TO ('2024-03-01');

-- Default partition (mos kelmagan qatorlar uchun)
CREATE TABLE loglar_default PARTITION OF loglar DEFAULT;

-- Partition pruning: faqat kerakli bo'limni skanerlaydi
EXPLAIN SELECT * FROM loglar WHERE sana = '2024-01-15';
-- faqat loglar_2024_01 skanerlaydi!

-- Eski partitionni o'chirish (darhol, bloklashsiz)
DROP TABLE loglar_2024_01;
-- DELETE ga qaraganda minglab marta tezroq!
```

> 💡 `pg_partman` kengaytmasi partition boshqaruvini avtomatlashtiradi — yangi oy kelganda avtomatik partition yaratadi.

---

### 24. VACUUM va AUTOVACUUM nima? MVCC bilan bog'liqligi.

**MVCC va o'lik qatorlar:**

MVCC'da UPDATE/DELETE qilingan qatorlar darhol o'chirilmaydi — "o'lik qatorlar" (dead tuples) sifatida qoladi. VACUUM bu o'lik qatorlarni tozalaydi.

||VACUUM|VACUUM FULL|
|---|---|---|
|Bloklaydimi|❌|✅ (Exclusive lock)|
|Hajm kamayadimi|❌ (qayta ishlatish uchun ajratadi)|✅|
|Tezlik|Tez|Sekin|
|Qachon ishlatish|Avtomatik (autovacuum)|Jadval juda ulkanida|

```sql
-- O'lik qatorlar statistikasi
SELECT
schemaname,
tablename,
n_dead_tup     AS olik_qatorlar,
n_live_tup     AS tirik_qatorlar,
ROUND(n_dead_tup * 100.0 / NULLIF(n_live_tup + n_dead_tup, 0), 2) AS foiz,
last_autovacuum
FROM pg_stat_user_tables
ORDER BY n_dead_tup DESC;

-- Qo'lda VACUUM
VACUUM ANALYZE buyurtmalar;        -- bloklashsiz, statistika yangilaydi
VACUUM FULL buyurtmalar;           -- to'liq (bloklaydi)
VACUUM FREEZE VERBOSE buyurtmalar; -- Transaction ID Wraparound oldini olish

-- Autovacuum sozlamalari (postgresql.conf)
-- autovacuum = on
-- autovacuum_vacuum_threshold = 50        -- min 50 dead tuple
-- autovacuum_vacuum_scale_factor = 0.2    -- + jadval hajmining 20%
```

> 💡 **Transaction ID Wraparound:** XID 32-bit, ~2 milliard limit. `VACUUM FREEZE` eski XID larni muzlatib, wraparound oldini oladi. `pg_stat_user_tables.n_mod_since_analyze` ni kuzatib boring!

---

### 25. PostgreSQL replication turlari: Streaming va Logical Replication.

**Replication turlari:**

||Streaming Replication|Logical Replication|
|---|---|---|
|Mexanizm|WAL (bit-by-bit)|Mantiqiy o'zgarishlar|
|Jadval tanlash|❌ (hammasi)|✅ (alohida jadvallar)|
|Versiyalar orasida|❌|✅|
|Boshqa DBMS'ga|❌|✅|
|Read scaling|✅|✅|
|Failover|✅|Murakkab|

```sql
-- postgresql.conf (primary server)
-- wal_level = replica
-- max_wal_senders = 3
-- wal_keep_size = 1GB

-- Replikatsiya foydalanuvchisi
CREATE USER repl_user REPLICATION LOGIN
ENCRYPTED PASSWORD 'parol';

-- pg_hba.conf (primary)
-- host replication repl_user standby_ip/32 md5

-- Standby serverda (terminal):
-- pg_basebackup -h primary_host -U repl_user -D /data -Fp -Xs -P

-- Logical Replication: Publication yaratish (primary)
CREATE PUBLICATION my_pub FOR TABLE buyurtmalar, foydalanuvchilar;
-- Faqat INSERT uchun
CREATE PUBLICATION insert_only FOR TABLE loglar WITH (publish = 'insert');

-- Subscriber serverda
CREATE SUBSCRIPTION my_sub
CONNECTION 'host=primary dbname=mydb user=repl_user password=parol'
PUBLICATION my_pub;

-- Replication status
SELECT * FROM pg_stat_replication;      -- primary'da
SELECT * FROM pg_stat_subscription;    -- subscriber'da
```

---

### 26. Connection pooling nima? PgBouncer qanday ishlaydi?

**Muammo:** PostgreSQL'da har bir ulanish yangi process yaratadi (~5-10MB RAM). 1000 ulanish = ~10GB RAM faqat ulanishlar uchun!

**PgBouncer rejimlari:**

|Rejim|Qanday ishlaydi|Qachon ishlatish|
|---|---|---|
|**Session**|1 client = 1 server conn (sessiya davomida)|Prepared statements kerak bo'lsa|
|**Transaction**|1 tranzaksiya = 1 server conn|**Eng samarali (tavsiya)**|
|**Statement**|1 so'rov = 1 server conn|Faqat autocommit|

```
# pgbouncer.ini
[databases]
mydb = host=127.0.0.1 port=5432 dbname=mydb

[pgbouncer]
pool_mode = transaction
max_client_conn = 1000
default_pool_size = 20
reserve_pool_size = 5
server_pool_size = 25
```

```sql
-- Optimal PostgreSQL ulanishlar soni:
-- max_connections = (CPU yadrolar * 2) + disk soni
-- 4-core: 4*2+1 = ~9 real connection, qolganlar PgBouncer orqali

-- Joriy ulanishlarni ko'rish
SELECT
state,
COUNT(*) AS soni,
wait_event_type,
wait_event
FROM pg_stat_activity
GROUP BY state, wait_event_type, wait_event;

-- Uzoq yuradigan so'rovlar
SELECT pid, age(clock_timestamp(), query_start) AS vaqt, query
FROM pg_stat_activity
WHERE state != 'idle' AND query_start < NOW() - INTERVAL '5 minutes'
ORDER BY vaqt DESC;
```

---

### 27. Dead lock nima? Qanday oldini olish va aniqlash mumkin?

Deadlock — ikki yoki undan ortiq tranzaksiya bir-birini kutib qolganda. PostgreSQL deadlock ni avtomatik aniqlab (~1 sekund), bittasini abort qiladi.

```sql
-- Deadlock situatsiyasi:
-- Tranzaksiya 1:
BEGIN;
UPDATE hisoblar SET balans = balans - 100 WHERE id = 1;  -- A ni qulfladi
-- kutmoqda...
UPDATE hisoblar SET balans = balans + 100 WHERE id = 2;  -- B ni kutadi

-- Tranzaksiya 2 (bir vaqtda):
BEGIN;
UPDATE hisoblar SET balans = balans - 50 WHERE id = 2;   -- B ni qulfladi
UPDATE hisoblar SET balans = balans + 50 WHERE id = 1;   -- A ni kutadi
-- DEADLOCK! Ikkalasi ham kutadi

-- Yechim: doim bir xil tartibda lock qilish
-- Ikkala tranzaksiya ham KICHIK id'ni oldin yangilaydi:
BEGIN;
UPDATE hisoblar SET balans = balans - 100 WHERE id = 1;
UPDATE hisoblar SET balans = balans + 100 WHERE id = 2;
COMMIT;

-- Lock'larni ko'rish
SELECT
pid,
locktype,
relation::regclass,
mode,
granted,
wait_start
FROM pg_locks l
JOIN pg_stat_activity a USING (pid)
WHERE NOT granted;

-- Deadlock logging
-- log_lock_waits = on
-- deadlock_timeout = 1s
```

> 💡 **Oldini olish qoidalari:** Resurslarni doim bir xil tartibda lock qiling. Tranzaksiyalarni qisqa tuting. `SELECT FOR UPDATE` dan ehtiyotkorlik bilan foydalaning.

---

### 28. Query optimization: slow query'larni topish va optimallashtirish.

```sql
-- 1. pg_stat_statements aktivlashtirish (postgresql.conf)
-- shared_preload_libraries = 'pg_stat_statements'
CREATE EXTENSION IF NOT EXISTS pg_stat_statements;

-- Eng sekin so'rovlar TOP 10
SELECT
ROUND(total_exec_time::numeric, 2) AS jami_ms,
calls,
ROUND(mean_exec_time::numeric, 2) AS ortacha_ms,
ROUND(stddev_exec_time::numeric, 2) AS standart_og'ish,
rows,
LEFT(query, 100) AS so'rov
FROM pg_stat_statements
ORDER BY total_exec_time DESC
LIMIT 10;

-- 2. Slow query logging (postgresql.conf)
-- log_min_duration_statement = 1000  (1 sekunddan sekin)

-- 3. Kuzatish va optimallash
EXPLAIN (ANALYZE, BUFFERS, FORMAT TEXT)
SELECT * FROM buyurtmalar
WHERE holat = 'pending' AND yaratilgan > NOW() - INTERVAL '7 days';

-- "Seq Scan" + "Rows Removed by Filter" katta bo'lsa:
CREATE INDEX CONCURRENTLY idx_buyurtmalar_holat_sana
ON buyurtmalar (holat, yaratilgan)
WHERE holat = 'pending';  -- partial index

-- 4. Statistikani yangilash (noto'g'ri rejalar uchun)
ANALYZE buyurtmalar;
-- Yoki barcha jadvallar uchun:
ANALYZE VERBOSE;
```

---

### 29. WAL (Write-Ahead Log) nima? Point-in-Time Recovery (PITR).

**WAL ishlash prinsipi:**

1. Har qanday o'zgarish **avval WAL ga yoziladi**
2. Keyin ma'lumot fayllariga yoziladi
3. Tizim to'xtatilsa WAL orqali o'zgarishlar tiklanadi

```sql
-- WAL arxivlash sozlamalari (postgresql.conf)
-- wal_level = replica
-- archive_mode = on
-- archive_command = 'cp %p /wal_archive/%f'
-- archive_timeout = 300  -- 5 daqiqada majburiy arxivlash

-- pg_basebackup: to'liq zaxira nusxa
-- pg_basebackup -h localhost -U repl_user -D /backup/base -Ft -z -Xs -P

-- PITR sozlash (postgresql.conf, PostgreSQL 12+)
-- restore_command = 'cp /wal_archive/%f %p'
-- recovery_target_time = '2024-01-15 14:30:00'
-- recovery_target_action = 'promote'

-- WAL fayllari va LSN
SELECT pg_walfile_name(pg_current_wal_lsn());
SELECT pg_size_pretty(pg_wal_lsn_diff(pg_current_wal_lsn(), '0/0'));

-- WAL fayllari joylashuvi
SELECT name, size FROM pg_ls_waldir() LIMIT 10;
```

> 💡 **pgBackRest** yoki **Barman** — professional WAL arxivlash va PITR uchun eng yaxshi toollar. WAL siqish, parallel restore, incremental backup qo'llab-quvvatlaydi.

---

### 30. Row Level Security (RLS) nima?

RLS — foydalanuvchi kimligiga qarab qaysi qatorlarni ko'rishi/o'zgartirishi mumkinligini jadval darajasida boshqarish. Multi-tenant ilovalar uchun juda foydali.

```sql
-- 1. RLS yoqish
ALTER TABLE hujjatlar ENABLE ROW LEVEL SECURITY;

-- 2. Policy yaratish
CREATE POLICY foydalanuvchi_hujjatlari
ON hujjatlar
FOR ALL
USING (egasi_id = current_setting('app.user_id')::INT);

-- Alohida SELECT va INSERT/UPDATE uchun
CREATE POLICY hujjat_korish
ON hujjatlar FOR SELECT
USING (
egasi_id = current_setting('app.user_id')::INT
OR umumiy = TRUE
);

CREATE POLICY hujjat_yangilash
ON hujjatlar FOR UPDATE
USING (egasi_id = current_setting('app.user_id')::INT)
WITH CHECK (egasi_id = current_setting('app.user_id')::INT);

-- 3. App sessiyasida foydalanuvchi ID ni o'rnatish
SET app.user_id = '42';
SELECT * FROM hujjatlar;  -- faqat user 42 ning hujjatlari

-- 4. Barcha policy'larni ko'rish
SELECT tablename, policyname, permissive, roles, cmd, qual
FROM pg_policies WHERE tablename = 'hujjatlar';
```

> 💡 `BYPASSRLS` — superuser va bu belgisi bor role RLS ni o'tkazib yuboradi. `FORCE ROW LEVEL SECURITY` table owner uchun ham RLS ishlatishni majburlaydi.

---

### 31. PostgreSQL'da Full-Text Search (FTS) qanday ishlaydi?

FTS — matndagi so'zlarni ildiz (stem) bo'yicha qidirish. `LIKE '%so'z%'` ga qaraganda ancha moslashuvchan va tezroq.

```sql
-- Asosiy tushunchalar
SELECT to_tsvector('english', 'PostgreSQL is a powerful database system');
-- 'databas':6 'power':4 'postgresql':1 'system':7

SELECT to_tsquery('english', 'powerful & database');
-- 'power' & 'databas'

-- Jadvalda FTS
SELECT sarlavha
FROM maqolalar
WHERE to_tsvector('english', matn) @@ to_tsquery('english', 'postgresql & index');

-- Hisoblab saqlash + GIN index (tezroq)
ALTER TABLE maqolalar
ADD COLUMN matn_vektor tsvector
GENERATED ALWAYS AS (to_tsvector('english', matn)) STORED;

CREATE INDEX idx_matn_gin ON maqolalar USING GIN (matn_vektor);

-- Relevantlik bo'yicha tartiblash
SELECT
sarlavha,
ts_rank(matn_vektor, q) AS relevantlik,
ts_headline('english', matn, q, 'MaxWords=20') AS parcha
FROM maqolalar, to_tsquery('english', 'postgresql') q
WHERE matn_vektor @@ q
ORDER BY relevantlik DESC;

-- pg_trgm: LIKE '%...%' ni ham tezlashtiradi
CREATE EXTENSION pg_trgm;
CREATE INDEX idx_trgm ON maqolalar USING GIN (matn gin_trgm_ops);
SELECT * FROM maqolalar WHERE matn LIKE '%PostgreSQL%';
```

---

### 32. PostgreSQL sharding, Horizontal Scaling va Citus nima?

**Scaling strategiyalari (kichikdan kattaga):**

1. **Vertical scaling** — kuchliroq server
2. **Read replicas** — o'qishni tarqatish
3. **Connection pooling** — ulanishlarni optimallashtirish
4. **Partitioning** — ma'lumotni bo'lish
5. **Sharding** — bir nechta serverlarga tarqatish

```sql
-- FDW (Foreign Data Wrapper): boshqa serverdan jadval
CREATE EXTENSION postgres_fdw;

CREATE SERVER remote_server
FOREIGN DATA WRAPPER postgres_fdw
OPTIONS (host '192.168.1.10', port '5432', dbname 'baza');

CREATE USER MAPPING FOR CURRENT_USER
SERVER remote_server
OPTIONS (user 'foydalanuvchi', password 'parol');

CREATE FOREIGN TABLE uzoq_buyurtmalar (
id    INT,
mijoz TEXT,
summa NUMERIC
) SERVER remote_server
OPTIONS (schema_name 'public', table_name 'buyurtmalar');

-- Citus: distributed table
-- CREATE EXTENSION citus;

-- Distribute qilish (shard key bo'yicha)
-- SELECT create_distributed_table('buyurtmalar', 'mijoz_id');

-- Reference table (hamma nodeda to'liq nusxa)
-- SELECT create_reference_table('kategoriyalar');

-- Citus parallel so'rov
-- SELECT bo'lim, COUNT(*) FROM buyurtmalar GROUP BY bo'lim;
-- Hamma shardlarda parallel bajariladi, keyin birlashtiradi
```

> 💡 Sharding juda murakkab arxitektura. Ko'p hollarda **Partitioning + Connection Pooling + Read Replicas** yetarli. Sharding faqat haqiqatan kerak bo'lganda, yaxshi o'ylab qilinsin.

---

## 📚 Qo'shimcha Resurslar

|Manba|Tavsif|
|---|---|
|[postgresql.org/docs](https://www.postgresql.org/docs/)|Rasmiy hujjatlar|
|[explain.depesz.com](https://explain.depesz.com/)|EXPLAIN natijasini vizualizatsiya|
|[pganalyze.com](https://pganalyze.com/)|PostgreSQL monitoring|
|[use-the-index-luke.com](https://use-the-index-luke.com/)|Index optimizatsiya|
|[pgbadger](https://github.com/darold/pgbadger)|Log tahlil qilish|

---

_Tayyorlagan: PostgreSQL Intervyu Savollari To'plami — Junior, Middle, Senior darajalar uchun_

---

## Link
<- [[01 - PHP savollar|PHP intervyu savollar]]

## Related Notes
- [[00 - Index]]
- [[01 - MySQL]]
