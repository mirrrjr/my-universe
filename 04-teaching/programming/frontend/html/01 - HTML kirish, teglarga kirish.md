Reja:

- HTML nima?
- Tag nima?
- Attributlar
- Teglarni joylashtirish

## 01. HTML nima?

HTML so’zining ma’nosi: HyperText Markup Language, ya’ni “giper matnli belgilash tili”.

HTML dasturlash tili emas. U belgilash tili (markup language). Ya’ni HTML hech qanday hisob-kitob qilmaydi. U faqat sahifadagi narsalarni tavsiflaydi: bu sarlavha, bu paragraf, bu rasm, bu tugma.

Tasavvur qiling, siz uy quryapsiz. HTML bu uyning qurilish chizmasi bo’lib, devor qayerda, eshik qayerda, deraza qayerda ekanini ko’rsatadi. Bezak, rang va joylashuvni esa CSS hal qiladi. Keyingi modullarda buni batafsil o’rganamiz.

![[Pasted image 20261103193928.png]]

## 02. Tag nima?

HTML ning asosiy tushunchasi, bu teg. Teg, bu burchakli qavs ichidagi buyruq bo’lib, brauzerga “bu yerda nima bor” deb aytadi.
Teglar ko’pincha juft bo’ladi. Ochuvchi teg va yopuvchi teg:

```html
<p>Bu paragraf matni</p>
```

>Bu yerda `<p>` ochuvchi teg, `</p>` esa yopuvchi teg. Yopuvchi teg oldida slesh (/) bor. Ular orasidagi narsa, ya’ni matn, shu elementning mazmuni hisoblanadi va `content` deb ataladi.

Ba’zi teglar esa yopilmaydi. Ularni toq (void) teglar deyiladi. Masalan:

```html
<br>
<img src="rasm.jpg" alt="Tasvir">
```

>`<br>` bu qator tushirish, `<img>` esa rasm qo’yish uchun ishlatiladi.

## 03. Attributlar

Teglarga qo’shimcha ma’lumot berish uchun atributlardan foydalanamiz. Atribut ochuvchi tegning ichida, nom="qiymat" ko’rinishida yoziladi:

```html
<a href="https://google.com">Google'ga o'tish</a>
```

>Bu yerda `href` atributi havola manzilini bildiradi. Har bir atributning o’z vazifasi bor, bularni keyinroq ko’p uchratamiz.

## 04. Teglarni joylashtirish

Teglar bir-birining ichiga joylashishi mumkin. Buni ichma-ich joylashtirish (nesting) deyiladi. Lekin qoida: birinchi ochilgan teg oxirida yopiladi.

```html
<!-- To'g'ri -->
<p>Bu <strong>muhim</strong> matn.</p>

<!-- Noto'g'ri -->
<p>Bu <strong>muhim</p></strong>
```

>Ikkinchi variant brauzerda ishlashi mumkin, lekin bu yomon odat va katta xatolarga olib keladi. Har doim tegni ochilgan tartibda yoping.

## Amaliyot

Endi amalda ko’ramiz. Birinchi qadam: kompyuteringizda `html-kurs` nomli papka yarating va ichida `index.html` fayli yarating.

Fayl kengaytmasi `.html` bo’lishi shart.

Endi faylga quyidagi kodni yozamiz:

```html
<!DOCTYPE html>
<html lang="uz">
<head>
  <meta charset="UTF-8">
  <title>Mening birinchi sahifam</title>
</head>
<body>
  <h1>Salom, dunyo!</h1>
  <p>Bu mening birinchi veb-sahifam.</p>
  <img src="https://picsum.photos/300/200" alt="Tasodifiy rasm">
  <a href="https://google.com">Google'ga o'tish</a>
</body>
</html>
```
Hozircha `<!DOCTYPE html>`, `<html>`, `<head>` va `<body>` nimaligini batafsil bilmasangiz ham bo’ladi. Ularni keyingi darsda, HTML strukturasida, to’liq tahlil qilamiz. Hozir bu shunchaki sahifa “qobig’i” ekanini bilib qo’ying.

Faylni saqlang. Brauzerda ochish uchun faylni ikki marta bosing yoki VSCodium’da **Live Server** kengaytmasini o’rnatib, “Go Live” tugmasini bosing.


## Xulosa

Bugun quyidagilarni o’rgandik:

- HTML belgilash tili ekani va uning vazifasi;
- Teg nima, juft va bo’sh teglar farqi;
- Atributlar va ularning ishlatilishi;
- Teglarni to’g’ri joylashtirish qoidasi;
- Birinchi `index.html` sahifasini yaratish.

---
## Vazifa
Uyga vazifa sifatida o’zingizning “Men haqimda” sahifangizni yarating. Sahifada quyidagilar bo’lsin:

- Sarlavha (`h1`): ismingiz;
- Paragraf (`p`): o’zingiz haqingizda 2–3 gap;
- Rasm (`img`): o’zingizga yoqqan rasm;
- Kamida 2 ta havola (`a`): sevimli saytlaringizga.

Vazifani GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!