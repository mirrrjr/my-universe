## `img` tegi va asosiy attribute’lari

- Rasmlarni sahifada ko'rsatish uchun ishlatiladi
- **src** va **alt.**
- src - fayl manzili yozish uchun
- alt - agar rasm ishlamasa default yozuv ko'rinishi, accessibility uchun

---

## `a` tegi va asosiy attribute’lari

- Link qo'yish uchun ishlatiladi
- **href** va **target** teglari bor
- **href**'ga manzil yoziladi
- **target** manzil shu sahifada yoki yangi tab'da ochilishini taminlaydi

Masalan bu yerda sahifa yangi tab'da ochiladi:

```html
<a href="example.com" target="_blank">Link</a>
```

- **anchor teg** landing page'da pastga scroll qilish uchun ishlatiladi:

```html
<nav>
  <ul>
    <li><a href="#about">About</a></li>
  </ul>
</nav>

<!-- ... Boshqa qismlar ... -->

<section id="about">
  <h2>About Us</h2>
  <p>Company haqida ma'lumot...</p>
</section>
```

## Link
<- [[PHP intervyu savollar]]