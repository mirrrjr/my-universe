Reja:

- Selektor nima?
- Element, class va id selektorlari
- Guruhlash va universal selektor
- Ichma-ich selektorlar
- Atribut va holat selektorlari
- Specificity asoslari

## 01. Selektor nima?

Selektor CSS qoidasining birinchi qismi bo’lib, qaysi HTML elementga uslub berilishini aniqlaydi. Oldingi darsda `p { color: blue; }` ko’rgan edik: bu yerda `p` selektor, ya’ni barcha paragraflarni tanlaydi.

Selektor bo’lmasa, CSS qaysi elementga ta’sir qilishini bilmaydi. Shuning uchun selektorni to’g’ri tanlash CSS da eng muhim ko’nikmalardan biri.

## 02. Element, class va id selektorlari

Uchta asosiy selektor bor:

```css
/* Element selektori: barcha p teglariga */
p {
  color: #6a7179;
}

/* Class selektori: nuqta (.) bilan, bir nechta elementga */
.card {
  padding: 16px;
  border: 1px solid #e3e6e4;
}

/* ID selektori: panjara (#) bilan, sahifada yagona bo’lishi kerak */
#main-title {
  font-size: 48px;
}
```

```html
<h1 id="main-title">Sarlavha</h1>
<div class="card">
  <p>Birinchi kartochka</p>
</div>
<div class="card">
  <p>Ikkinchi kartochka</p>
</div>
```

- Element selektori (`p`): nomi bo’yicha barcha shu teglarga ta’sir qiladi.
- Class selektori (`.card`): bir nechta elementga bir xil uslub berish uchun. Bir elementga bir nechta class yozish mumkin: `class="card featured"`.
- ID selektori (`#main-title`): bitta aniq elementga. Bir sahifada bir ID faqat bir marta ishlatiladi.

Amaliy qoida: asosan class ishlating. ID ni JavaScript va aniq bog’lanishlar uchun saqlang.

## 03. Guruhlash va universal selektor

Bir xil uslubni bir nechta selektorga berish uchun vergul ishlatiladi:

```css
h1, h2, h3 {
  font-family: Georgia, serif;
}
```

Universal selektor (`*`) barcha elementlarga ta’sir qiladi:

```css
* {
  box-sizing: border-box;
}
```

Universal selektorni ehtiyot bilan ishlating, chunki u sahifadagi hamma elementga birdan ta’sir qiladi.

## 04. Ichma-ich selektorlar

Elementlarning joylashuviga qarab tanlash mumkin:

```css
/* Descendant: .card ichidagi barcha p lar */
.card p {
  line-height: 1.6;
}

/* Child: faqat .card ning bevosita farzandi bo’lgan p lar */
.card > p {
  margin-top: 0;
}
```

- Bo’sh joy (descendant) ichidagi barcha avlodlarga ta’sir qiladi.
- `>` (child) faqat bevosita farzandlarga ta’sir qiladi.

## 05. Atribut va holat selektorlari

Atribut bo’yicha tanlash:

```css
/* href atributi bor barcha a lar */
a[href] {
  color: #2f6f5e;
}

/* type="text" bo’lgan input lar */
input[type="text"] {
  border: 1px solid #e3e6e4;
}
```

Holat (pseudo-class) selektorlari elementning holatiga qarab ishlaydi:

```css
/* Sichqoncha ustiga kelganda */
a:hover {
  text-decoration: underline;
}

/* Birinchi element */
li:first-child {
  font-weight: bold;
}
```

`:hover` va `:first-child` ni ko’p ishlatasiz. Holat selektorlari interaktiv sahifalarda juda foydali.

## 06. Specificity asoslari

Bir elementga bir nechta qoida tegishli bo’lsa, qaysi biri ishlashini specificity (ustunlik darajasi) belgilaydi. Oddiy tartib:

1. Inline `style` atributi eng kuchli.
2. ID selektori (`#id`) keyin keladi.
3. Class, atribut va holat selektorlari (`.class`, `[href]`, `:hover`) o’rtada.
4. Element selektori (`p`, `div`) eng past.

```css
p { color: black; }
.text { color: blue; }
#intro { color: red; }
```

Agar `<p id="intro" class="text">` bo’lsa, rang `red` bo’ladi, chunki ID kuchliroq. Bu bosqichda tushunish yetarli. Chuqur qoidalarni keyinroq o’rganamiz.

## Amaliyot

Oldingi darsdagi `index.html` va `style.css` faylini oling va quyidagilarni bajaring.

1. Barcha `h1, h2, h3` uchun umumiy shrift (`font-family`) yozing.
2. Bir nechta `div` ga `class="card"` bering va `.card` uchun `padding` va `border` qo’shing.
3. `.card` ichidagi `p` larga `line-height: 1.6;` bering.
4. Sahifadagi bitta sarlavhaga `id="main-title"` bering va unga alohida rang bering.
5. Havolalarga `a:hover` qo’shing va sichqoncha ustiga kelganda rang o’zgarsin.
6. `li:first-child` uchun qalin shrift yozing.

Natijani Live Server orqali brauzerda oching va har bir selektor qaysi elementga ta’sir qilganini tekshiring.

## Xulosa

Bugun quyidagilarni o’rgandik:

- Selektor CSS qoidasida qaysi elementga uslub berilishini aniqlashi;
- Element (`p`), class (`.card`) va id (`#main-title`) selektorlari;
- Guruhlash (`,`) va universal (`*`) selektor;
- Ichma-ich (`.card p`) va bevosita farzand (`.card > p`) selektorlari;
- Atribut (`a[href]`) va holat (`:hover`, `:first-child`) selektorlari;
- Specificity: inline, id, class, element tartibi.

---

## Vazifa

Uyga vazifa sifatida “Men haqimda” sahifangizga quyidagilarni qo’shing:

- Kamida 2 ta `class` (masalan, `.card`, `.highlight`) va ularni ishlatilgan elementlarga bering;
- Sahifadagi bitta elementga `id` bering va unga alohida uslub yozing;
- Havolalar uchun `a:hover` holatini qo’shing;
- Bitta ichma-ich selektor (`.card p` yoki `.card > p`) ishlating.

Faylni GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!