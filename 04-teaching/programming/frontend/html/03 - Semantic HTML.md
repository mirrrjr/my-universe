Reja:

- Semantik HTML nima?
- Asosiy semantik teglar
- Div va semantik teglar farqi
- Sarlavhalar iyerarxiyasi (h1–h6)
- Semantik tuzilishga o’tkazish

## 01. Semantik HTML nima?

Semantika — ma’no degani. Semantik HTML teglari sahifadagi qismlarning vazifasini ham bildiradi. Masalan, `<nav>` bu navigatsiya ekanini, `<footer>` esa sahifaning pastki qismi ekanini aytadi.

Bu teglar sahifaning ko’rinishini o’zgartirmaydi. Brauzerda ular oddiy `div` kabi ko’rinadi. Farq kodning ma’nosida va brauzer, qidiruv tizimlari, ekran o’qish dasturlari uchun ko’rinadigan tuzilishda.

## 02. Asosiy semantik teglar

Quyidagi teglar sahifaning asosiy qismlarini ifodalaydi:

```html
<header>  <!-- sahifa yoki bo’lim sarlavhasi -->
<nav>     <!-- navigatsiya havolalari -->
<main>    <!-- sahifaning asosiy mazmuni (bir marta) -->
<article> <!-- mustaqil maqola, post yoki kartochka -->
<section> <!-- mazmunning mantiqiy bo’limi -->
<aside>   <!-- asosiy mazmunga bevosita aloqasi kam qism -->
<footer>  <!-- pastki qism: mualliflik, kontakt, havolalar -->
```

Oddiy uy sahifasini tasavvur qiling: yuqorida logotip va menyu (`header`, `nav`), o’rtada asosiy yangiliklar (`main`), yon tomonda reklama yoki qo’shimcha havolalar (`aside`), pastda mualliflik yozuvi (`footer`).

## 03. Div va semantik teglar farqi

`div` faqat konteyner, u hech narsani anglatmaydi. Shuning uchun uni “ma’nosiz” teg deyish mumkin.

```html
<!-- Semantik bo’lmagan variant -->
<div class="header">
  <div class="menu">...</div>
</div>
<div class="content">...</div>
<div class="footer">...</div>
```

```html
<!-- Semantik variant -->
<header>
  <nav>...</nav>
</header>
<main>...</main>
<footer>...</footer>
```

Ikkinchi variant kodni o’qishni osonlashtiradi. Yangi dasturchi bir qarashda sahifa tuzilishini tushunadi. Qidiruv tizimlari ham asosiy mazmunni ajratib olishi osonroq bo’ladi. Ekran o’qish dasturlari (screen reader) esa “navigatsiya”ga o’tish imkoniyatini beradi.

Eslatma: `div` yo’q bo’lishi kerak degani emas. Agar teglarga mos keladigan semantik element bo’lmasa, `div` ishlatish to’g’ri.

## 04. Sarlavhalar iyerarxiyasi

`h1` dan `h6` gacha bo’lgan sarlavhalar mazmunning daraxtini ko’rsatadi. Sahifada odatda bitta `h1` bo’ladi, qolganlari undan pastroq darajada keladi.

```html
<main>
  <h1>HTML kursi</h1>
  <section>
    <h2>1-modul: HTML va CSS</h2>
    <h3>1-dars: HTML kirish</h3>
  </section>
</main>
```

Sarlavhalarni faqat matn o’lchamini o’zgartirish uchun ishlatmang. Matn ko’rinishi CSS orqali boshqariladi, sarlavha esa mazmun tuzilishini bildiradi. Bo’limlarni o’tkazib yuborish (masalan, `h1` dan keyin darhol `h4`) ham tavsiya etilmaydi.

## 05. Semantik tuzilishga o’tkazish

Amaliy yondashuv: avval sahifaning mazmunini qismlarga bo’ling, so’ng har bir qismga mos teg tanlang.

1. Sahifaning yuqorisidagi qism — `header`.
2. Menyu havolalari — `nav`.
3. Asosiy mazmun — `main`.
4. Mustaqil kartochkalar yoki maqolalar — `article`.
5. Pastki qism — `footer`.

Har bir tanlovni o’zingizga savol berib tekshiring: “Bu qism mustaqil ma’noga egami?”, “Bu sahifaning asosiy mazmunimi?”.

## Amaliyot

`div` lardan iborat quyidagi sahifani semantik tuzilishga o’tkazing:

```html
<div class="top">
  <div class="logo">Mening sahifam</div>
  <div class="menu">
    <a href="#">Bosh sahifa</a>
    <a href="#">Haqimda</a>
  </div>
</div>
<div class="content">
  <div class="card">
    <div class="title">Birinchi maqola</div>
    <div class="text">Maqola matni...</div>
  </div>
</div>
<div class="bottom">© 2026</div>
```

Ko’rsatma:

1. `top` ni `header` ga, `menu` ni `nav` ga o’zgartiring.
2. `content` ni `main` ga, `card` ni `article` ga o’zgartiring.
3. `title` ni `h2` ga, `text` ni `p` ga o’zgartiring.
4. `bottom` ni `footer` ga o’zgartiring.
5. `logo` uchun `h1` dan foydalaning, chunki bu sahifaning asosiy sarlavhasi.

Natijani brauzerda oching. Ko’rinishi o’zgarmasligi kerak, chunki semantik teglar standart holatda oddiy blok kabi ko’rinadi.

## Xulosa

Bugun quyidagilarni o’rgandik:

- Semantik teglar sahifa qismlarining vazifasini bildirishi;
- Asosiy teglar: `header`, `nav`, `main`, `article`, `section`, `aside`, `footer`;
- `div` konteyner, semantik teglar esa ma’noli elementlar ekani;
- `h1`–`h6` iyerarxiyasi va uni to’g’ri ishlatish;
- Mavjud sahifani semantik tuzilishga o’tkazish qadamlari.

---

## Vazifa

Uyga vazifa sifatida “Men haqimda” sahifangizni semantik teglar yordamida qayta yozing. Sahifada quyidagilar bo’lsin:

- `header` ichida sayt nomi (`h1`) va `nav` menyusi (kamida 2 ta havola);
- `main` ichida `section` bo’limlari: “Men haqimda” va “Qiziqishlarim”, har birida `h2` sarlavha;
- `aside` ichida sevimli saytlaringiz ro’yxati (`ul` va `li` bilan);
- `footer` ichida mualliflik yozuvi.

Vazifani GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!