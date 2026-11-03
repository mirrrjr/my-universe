Reja:

- HTML hujjat tuzilishi
- DOCTYPE va html
- Head bo’limi
- Body bo’limi
- Kodni joylashtirish (indentation)

## 01. HTML hujjat tuzilishi

Har bir HTML fayl ma’lum bir skeletga ega. Brauzer shu skelet asosida sahifani tushunadi. Skelet quyidagicha ko’rinadi:

```html
<!DOCTYPE html>
<html lang="uz">
<head>
  <!-- sahifa haqida ma’lumot -->
</head>
<body>
  <!-- foydalanuvchi ko’radigan mazmun -->
</body>
</html>
```

Bu tuzilishni uyning qurilish chizmasiga o’xshatish mumkin: `head` uyning hujjatlari (ko’rinmaydi), `body` esa uyning o’zi (hamma ko’radi).

## 02. DOCTYPE va html

`<!DOCTYPE html>` brauzerga “bu HTML5 hujjat” deb aytadi. Bu teg HTML tegi emas, u faqat brauzer uchun ko’rsatma. Har doim faylning eng birinchi qatorida yoziladi.

`<html>` esa butun hujjatning ildizi (root). Barcha boshqa teglar shu tegning ichida joylashadi. `lang="uz"` atributi sahifa tilini bildiradi, bu qidiruv tizimlari va ekran o’qish dasturlari uchun foydali.

## 03. Head bo’limi

`<head>` ichida sahifaning “ko’rinmas” ma’lumotlari joylashadi. Foydalanuvchi bu yerdagi narsalarni sahifada ko’rmaydi, lekin brauzer va qidiruv tizimlari ularni o’qiydi.

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mening birinchi sahifam</title>
</head>
```

- `<meta charset="UTF-8">`: o’zbek harflari (o’, g’, sh, ch) to’g’ri ko’rinishi uchun kodlash;
- `<meta name="viewport">`: sahifa telefonda to’g’ri kenglikda ochilishi uchun (keyingi modullarda muhim bo’ladi);
- `<title>`: brauzer oynasi va qidiruv natijasidagi sarlavha.

## 04. Body bo’limi

`<body>` ichida foydalanuvchi ko’radigan barcha narsa joylashadi: sarlavhalar, matnlar, rasmlar, havolalar.

```html
<body>
  <h1>Salom, dunyo!</h1>
  <p>Bu mening birinchi veb-sahifam.</p>
  <img src="https://picsum.photos/300/200" alt="Tasodifiy rasm">
  <a href="https://google.com">Google’ga o’tish</a>
</body>
```

>Eslatma: `head` ichidagi `<title>` ko’rinmaydi, u faqat brauzer oynasining sarlavha qatorida ko’rinadi. `body` ichidagi `<h1>` esa sahifaning o’zida ko’rinadi.

## 05. Kodni joylashtirish (indentation)

Ichma-ich teglar odatda ikki bo’shliqqa suriladi. Bu kodni o’qishni ancha osonlashtiradi:

```html
<body>
  <main>
    <h1>Sarlavha</h1>
    <p>Matn</p>
  </main>
</body>
```

Brauzer bo’shliqlarga e’tibor bermaydi, lekin siz va jamoangiz uchun kod tartibli bo’lishi muhim. Shuning uchun har doim bir xil indentatsiya ishlating.

## Amaliyot

Oldingi darsda yaratgan `index.html` faylingizni oling va uni to’liq skelet ko’rinishiga keltiring.

1. Faylning eng yuqorisiga `<!DOCTYPE html>` yozing.
2. `<html lang="uz">` tegini qo’shing.
3. `head` ichiga `meta charset`, `meta viewport` va `title` qo’shing.
4. `body` ichiga bitta `h1`, ikkita `p` va bitta `footer` joylashtiring.

Natija quyidagicha bo’lishi kerak:

```html
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mening birinchi sahifam</title>
</head>
<body>
  <h1>Salom, dunyo!</h1>
  <p>Bu mening birinchi veb-sahifam.</p>
  <p>Bugun HTML struktura bilan tanishdim.</p>
  <footer>
    <p>2026 Mening sahifam</p>
  </footer>
</body>
</html>
```

Faylni saqlang va Live Server orqali brauzerda oching. Sahifa nomi brauzer oynasining sarlavha qatorida ko’rinishini tekshiring.

## Xulosa

Bugun quyidagilarni o’rgandik:

- HTML hujjatning asosiy tuzilishi: `DOCTYPE`, `html`, `head`, `body`;
- `head` ichida ko’rinmas ma’lumotlar (`meta`, `title`) joylashishi;
- `body` ichida foydalanuvchi ko’radigan mazmun joylashishi;
- Kodni indentatsiya bilan tartibli yozish qoidasi.

---

## Vazifa

Uyga vazifa sifatida amaliyotdagi skeletga asoslanib, o’zingizning “Men haqimda” sahifangizni yarating. Sahifada quyidagilar bo’lsin:

- To’liq skelet: `DOCTYPE`, `html lang="uz"`, `head` (meta charset, viewport, title) va `body`;
- Sarlavha (`h1`): ismingiz;
- Paragraf (`p`): o’zingiz haqingizda 2–3 gap;
- Pastki qismda `footer` ichida mualliflik yozuvi.

Vazifani GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!