Reja:

- CSS nima?
- CSS ni HTML ga ulash
- CSS sintaksisi
- Asosiy xususiyatlar
- Birliklar (px, %, em, rem)

## 01. CSS nima?

CSS so’zining ma’nosi: Cascading Style Sheets, ya’ni “pog’onali uslublar jadvali”.

Oldingi darslarda HTML sahifaning tuzilishini yaratdik: sarlavha, paragraf, rasm, havola. Ammo hozircha ularning ko’rinishi standart holatda. CSS aynan shu ko’rinishni boshqaradi: rang, shrift, o’lcham, joylashuv.

Uy misolida davom etsak, HTML devor va eshiklarni quradi, CSS esa devorlarni bo’yaydi, derazalarga pardalar osadi va bog’ni chiroyli qiladi.

## 02. CSS ni HTML ga ulash

CSS ni HTML ga ulashning uchta usuli bor. Eng ko’p ishlatiladigani uchinchisi.

**1. Inline (teg ichida):**

```html
<p style="color: red;">Qizil matn</p>
```

Bu usul bitta elementga ta’sir qiladi. Katta loyihalarda kodni qiyinlashtiradi, shuning uchun kamroq ishlatiladi.

**2. Internal (head ichida):**

```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>
```

Bu usul shu HTML fayl uchun ishlaydi. Kichik sahifalar uchun qulay.

**3. External (alohida fayl):**

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```

`style.css` alohida faylda yoziladi. Bir nechta HTML sahifa bir xil uslubdan foydalana oladi. Loyihalarda aynan shu usul standart hisoblanadi.

## 03. CSS sintaksisi

CSS qoidasi uch qismdan iborat: selektor, xususiyat va qiymat.

```css
p {
  color: blue;
  font-size: 18px;
}
```

- `p` — selektor: qaysi elementga uslub berilishini bildiradi;
- `color` — xususiyat (property): nimani o’zgartirish kerakligini bildiradi;
- `blue` — qiymat (value): xususiyatga berilgan aniq ma’no;
- `;` — har bir qatorning oxirida yoziladi;
- `{ }` — uslublar guruhini o’rab turadi.

Izoh yozish uchun `/* */` ishlatiladi:

```css
/* Bu izoh, brauzer uni e’tiborsiz qoldiradi */
p {
  color: blue;
}
```

## 04. Asosiy xususiyatlar

Bugun eng ko’p ishlatiladigan dastlabki xususiyatlarni o’rganamiz:

```css
h1 {
  color: #1d2b3a;
  font-size: 48px;
  text-align: center;
}

p {
  color: #6a7179;
  font-size: 18px;
  line-height: 1.6;
}

body {
  background-color: #fbfbf8;
  font-family: Arial, sans-serif;
}
```

- `color`: matn rangi;
- `background-color`: fon rangi;
- `font-size`: shrift o’lchami;
- `font-family`: shrift turi;
- `line-height`: qatorlar orasidagi masofa;
- `text-align`: matnni joylashtirish (`left`, `center`, `right`).

Ranglarni nomi (`red`), HEX (`#1d2b3a`) yoki `rgb(29, 43, 58)` ko’rinishida yozish mumkin. Odatda HEX ishlatiladi.

## 05. Birliklar

CSS da o’lchamlar turli birliklarda beriladi:

- `px` — piksel, aniq o’lcham. Masalan: `font-size: 16px;`
- `%` — ota elementga nisbatan foiz. Masalan: `width: 50%;`
- `em` — joriy elementning shrift o’lchamiga nisbatan. Masalan: `padding: 2em;`
- `rem` — sahifaning asosiy (root) shrift o’lchamiga nisbatan. Masalan: `font-size: 1.5rem;`

Boshlang’ich dasturchi uchun `px` tushunish oson. Keyinchalik responsiv dizaynda `rem` va `%` ko’proq ishlatiladi.

## Amaliyot

Oldingi darslardagi `index.html` faylini oling va unga tashqi `style.css` faylini ulang.

1. `index.html` ning `head` qismiga `<link rel="stylesheet" href="style.css">` qo’shing.
2. `style.css` faylini yarating va sahifa fonini och rangga bo’yang: `body { background-color: #fbfbf8; }`.
3. `h1` ni markazga joylashtiring va rangini o’zgartiring.
4. `p` uchun `font-size: 18px;` va `line-height: 1.6;` yozing.
5. Bitta `p` ga inline `style` atributi bilan boshqa rang bering, va farqni ko’ring.

Natijani Live Server orqali brauzerda oching.

## Xulosa

Bugun quyidagilarni o’rgandik:

- CSS HTML ning ko’rinishini boshqarish tili ekani;
- CSS ni inline, internal va external usullarda ulash;
- Selektor, xususiyat va qiymatdan iborat sintaksis;
- `color`, `background-color`, `font-size`, `font-family`, `line-height`, `text-align` xususiyatlari;
- `px`, `%`, `em`, `rem` birliklari.

---

## Vazifa

Uyga vazifa sifatida “Men haqimda” sahifangizga tashqi `style.css` faylini ulang. Quyidagilar bo’lsin:

- `body` uchun fon rangi;
- `h1` uchun rang va markazga joylashtirish;
- `p` uchun `font-size` va `line-height`;
- Kamida 3 ta xususiyat, har biri alohida selektor uchun.

Faylni GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!