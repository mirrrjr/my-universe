Reja:

- HTML nima?
- Tag nima?
- Attributlar
- Teglarni joylashtirish
# HTML nima?

**HTML** (HyperText Markup Language) veb sahifaning tuzilmasini belgilaydigan tildir. Sahifada qayerda sarlavha, qayerda matn, qayerda rasm va qayerda tugma bo'lishini brauzerga aytib beradi.

Uyni qurishga o'xshatish mumkin. HTML uyning **skeleti**: devorlar, xonalar va eshiklarning joylashuvi. CSS uning **bezagi** (ranglar, shriftlar, joylashuv), JavaScript esa **ichidagi mexanizmlari** (harakat va interaktivlik).

HTML dasturlash tili emas, balki **markup tili** hisoblanadi. U mantiqiy hisob-kitob qilmaydi, faqat mazmunni belgilaydi.
![[Pasted image 20261103193928.png]]

# Tag nima?

**Tag** (teg) HTML elementlarini belgilash uchun ishlatiladigan burchakli qavsli yozuvdir. Ko'pincha juftlikda keladi:

```html
<p>Salom, dunyo!</p>
```

- `<p>` — **ochilish tegi** (boshlanish)
- `</p>` — **yopilish tegi** (tugash, `/` belgisi bilan)
- `Salom, dunyo!` — **tarkib** (kontent)

Ochilish tegi, tarkib va yopilish tegi birgalikda **element** deyiladi.

Ba'zi teglar yopilmaydi, chunki ular hech narsani o'rab olmaydi. Masalan:

```html
<img src="rasm.jpg">
<br>
<input type="text">
```

Bunday teglar **bo'sh (void) teglar** deb ataladi.

Har bir tegning vazifasi bor:

- `<h1>` — asosiy sarlavha
- `<p>` — paragraf (oddiy matn)
- `<a>` — havola (link)
- `<img>` — rasm
- `<button>` — tugma

---

# Attributlar

**Attribut** (atribut) tegga qo'shimcha ma'lumot beradi. U ochilish tegining ichida yoziladi va odatda `nom="qiymat"` ko'rinishida bo'ladi:

```html
<a href="https://t.me/username" class="" id="">Google'ga o'tish</a>

<h2 class="sarlavha-2">
	Salom
</h2>
```

Bu yerda:

- `href` — attribut nomi
- `"https://google.com"` — attribut qiymati
- `<a>` — teg

Eng ko'p uchraydigan attributlar:

|Attribut|Vazifasi|Misol|
|---|---|---|
|`href`|Havolaning manzili|`<a href="index.html">`|
|`src`|Rasm yoki fayl manzili|`<img src="logo.png">`|
|`alt`|Rasm tavsifi (rasm ko'rinmasa yoki ekranni o'qish dasturi uchun)|`<img alt="Logotip">`|
|`class`|Elementga nom berish (CSS uchun)|`<p class="matn">`|
|`id`|Elementga noyob nom berish|`<h1 id="sarlavha">`|
|`lang`|Sahifa tili|`<html lang="uz">`|

Bir elementda bir nechta attribut bo'lishi mumkin:

```html
<img src="rasm.jpg" alt="Tog' manzarasi" width="300">
```

---

# Teglarni joylashtirish

## 1. To'g'ri ichma-ich joylashtirish (nesting)

Teglarni bir-birining ichiga joylashtirish mumkin, lekin ular **to'g'ri tartibda** yopilishi kerak. Oxirgi ochilgan teg birinchi bo'lib yopiladi:

```html
<!-- To'g'ri -->
<div>
  <p>Bu <strong>muhim</strong> matn.</p>
</div>
```

```html
<!-- Noto'g'ri -->
<div>
  <p>Bu <strong>muhim</strong> matn.</div></p>
</div>
```

Teglar bir-birini "kesib o'tmasligi" kerak. Yuqoridagi noto'g'ri misolda `</div>` yopilishi `<p>` ichida keladi, bu esa xatolikka olib keladi.

## 2. Hujjatning asosiy tuzilishi

Har bir HTML sahifa quyidagi asosiy qismlardan iborat bo'ladi:

```html
<!DOCTYPE html>
<html lang="uz">
  <head>
    <meta charset="UTF-8">
    <title>Mening birinchi sahifam</title>
  </head>
  <body>
    <h1>Salom, dunyo!</h1>
    <p>Bu mening birinchi veb sahifam.</p>
  </body>
</html>
```

- `<!DOCTYPE html>` — brauzerga bu HTML5 hujjat ekanini aytadi
- `<html>` — butun sahifaning ildizi
- `<head>` — sahifa haqida yashirin ma'lumotlar (sarlavha, belgi kodirovkasi). Ekranda ko'rinmaydi.
- `<body>` — ekranda ko'rinadigan barcha mazmun

## 3. Tartib va chiroyli yozuv

HTML brauzerda ko'rsatilishida teglar orasidagi bo'sh joy va qator o'tishlarni e'tiborsiz qoldiradi. Shuning uchun kodni o'qish oson bo'lishi uchun **ichkari surish (indentatsiya)** ishlatiladi. Bu ko'rinishga ta'sir qilmaydi, faqat kodni tushunarli qiladi.

---

# Qisqacha xulosa

- **HTML** — veb sahifa tuzilmasini yozish tili
- **Tag** — `<...>` ko'rinishidagi belgi, elementni boshlaydi yoki tugatadi
- **Element** — ochilish tegi + tarkib + yopilish tegi
- **Attribut** — tegga qo'shimcha ma'lumot beradi (`nom="qiymat"`)
- **Joylashtirish** — teglar to'g'ri ichma-ich bo'lishi va to'g'ri tartibda yopilishi kerak

---
## Vazifa
Uyga vazifa sifatida o’zingizning “Men haqimda” sahifangizni yarating. Sahifada quyidagilar bo’lsin:

- Sarlavha (`h1`): ismingiz;
- Paragraf (`p`): o’zingiz haqingizda 2–3 gap;
- Rasm (`img`): o’zingizga yoqqan rasm;
- Kamida 2 ta havola (`a`): sevimli saytlaringizga.

Vazifani GitHub’ga yuklang yoki kurs guruhida ulashing. Keyingi darsda ko’rishguncha!