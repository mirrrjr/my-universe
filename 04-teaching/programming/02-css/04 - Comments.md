## Maqsad

> [!NOTE] Dars oxirida o'quvchi CSS da izoh yozishni, kodni bo'limlarga ajratishni va izohdan debug uchun foydalanishni biladi.

> [!TIP] Eslatma CSS da izoh: `/* izoh */`. Bir qatorli alohida sintaksis yo'q, ko'p qatorli ham xuddi shunday yoziladi.

**Vaqt:** ~20 daqiqa

## Mashq 1: Kodni "o'chirib qo'yish" (3 daqiqa)

```css
p {
  color: red;
  color: blue;
}
```

> [!TODO] Vazifa Izoh yordamida `color: blue` qatorini o'chirib qo'ying. Brauzerda rang qanday o'zgardi?

> [!SUCCESS]- Javob Avval `blue` (oxirgi qoida g'olib), izohdan keyin `red`. Izohga olingan kod brauzerga ko'rinmaydi.

---

## Mashq 2: Ko'p qatorli izoh (3 daqiqa)

```css
h1 { color: red; }
p { color: blue; }
```

> [!TODO] Vazifa Kodning tepasiga ko'p qatorli izoh yozing: fayl nomi, muallif va sana.

> [!SUCCESS]- Javob
> 
> ```css
> /*
>   Fayl: style.css
>   Muallif: Ism Familiya
>   Sana: 2026-10-07
> */
> ```

---

## Mashq 3: Xatoni toping (5 daqiqa)

```css
/* Sarlavha stillari
h1 {
  color: red;
}

/* Paragraf stillari */
p {
  color: blue;
}
```

> [!QUESTION] Savol Nima uchun `h1` ning rangi o'zgarmayapti? Xatoni toping va tuzating.

> [!SUCCESS]- Javob Birinchi izoh `*/` bilan yopilmagan, shuning uchun u keyingi `*/` gacha (`h1` qoidasini ham) "yeb qo'ydi". Birinchi izohning oxiriga `*/` qo'shish kerak.

---

## Mashq 4: Kodni bo'limlarga ajratish (5 daqiqa)

[[Mashqlar - Selectors]] dagi 6-mashq CSS kodini oling.

> [!TODO] Vazifa Izohlar bilan bo'limlarga ajrating: Matn, Ro'yxat, Forma.

> [!SUCCESS]- Namuna
> 
> ```css
> /* ===== Matn ===== */
> h1 { text-align: center; }
> .intro { font-size: 24px; }
> 
> /* ===== Ro'yxat ===== */
> .active { font-weight: bold; }
> 
> /* ===== Forma ===== */
> [disabled] { opacity: 0.5; }
> ```

---

## Mashq 5: Izoh bilan debug (4 daqiqa)

> [!TODO] Vazifa Istalgan 3 ta qoidani birin-ketin izohga oling va sahifa qanday o'zgarishini kuzating.

> [!QUESTION] Muhokama Qaysi qoida qaysi elementga ta'sir qilayotganini topishda izohlar qanday yordam beradi?

---

## Related Notes

- [[04-teaching/programming/02-css/00 - Index]]
- [[04 - Comments]]
- [[Mashqlar - Selectors]]
- [[Mashqlar - Specificity]]