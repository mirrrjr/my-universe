1. O'zgaruvchilar
2. String (matn)
3. Sonlar
4. List (ro'yxat)
5. Ro'yxatlar bilan ishlash
6. For takrorlash operatori

# 1. O'ZGARUVCHILAR
## O'zgaruvchilar (variables)
**O'zgaruvchi** —kompyuter xotirasida ma'lum bir qiymatni saqlash uchun ajratilgan joy. Soddaroq qilib tushuntirsak, o'zgaruvchini quti, quti ichidagi narsani esa qiymat deb tasavvur qilish mumkin. Pythonda qiymatlar son, matn, ro'yxat va hokazo ko'rinishida bo'lishi mumkin.

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLgatxylpGtKv0LiiV1%252F-MLgfAikZVcuHp-u5tHP%252FPic-of-labeled-boxes.jpg%3Falt%3Dmedia%26token%3D4bdf283d-c483-4158-8ce3-90527594f363&width=768&dpr=4&quality=100&sign=5d296a3e&sv=2)

O'zgaruvchilarni kerakli buyumlar (ma'lumotlat) saqlanadigan, nomlangan qutilarga o'xshatish mumkin

Quyidagi misolga e'tibor bering, biz 2 ta o'zgaruvchi yaratdik (`ism` va `yosh`) va ularga qiymatlar yukladik:

```python
ism = "Abdulloh"
yosh = 25
print(ism)
print(yosh)
```

Natija:

`Abdulloh`

`25`

O'zgaruvchi (variable) bunday deyilishiga sabab, uning qiymati istalgan vaqt o'zgartirilishi mumkin:

```python
ism = "Abdulloh"
print(ism)
ism="Muhammad"
print(ism)
```

Natija:

`Abdulloh`

`Muhammad`

Yuqoridagi misolda `ism` nomli o'zgaruvchiga avval `Abdulloh` keyin esa `Muhammad` qiymatlarini berdik.

## O'ZGARUVCHILARNI NOMLASH

O'zgaruvchilarga nom berishda quyidagi qoidalarga amal qiling:

- O'zgaruvchi nomi harf yoki pastki chiziq (`_`) bilan boshlanishi kerak
    
- O'zgaruvchi nomi raqam bilan boshlanishi mumkin emas
    
- O'zgaruvchi nomida faqatgina lotin alifbosi harflari (`A-z`), raqamlar (`0-9`) va pastki chiziq (`_`) qatnashishi mumkin
    
- O'zgaruvchi nomida bo'shliq (пробел) bo'lishi mumkin emas
    
- O'zgaruvchi nomida katta-kichik harflar turlicha talqin qilinadi (`ism`, `ISM`, va `Ism` uchta turli o'zgaruvchi)
    

Qo'shimcha qoida sifatida:

- O'zgaruvchi nomini kichik harflar bilan yozing.
    
- O'zgaruvchi nomida 2 va undan ortiq so'z qatnashsa ularning orasini pastki chiziq (_) bilan ajrating (`ism_sharif="Anvar Narzullaev"`)
    
- O'zgaruvchiga tushunarli nom bering (`y=20` emas `yosh=20`, `d="Korea"` emas `davlat = "Korea"` va hokazo)
    
- Shuningdek o'zgaruvchilarga Pythonda ishlatiladigan funktsiyalar va maxsus kalit so'zlarning (keywords) nomini bermang.
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLVzx_XI1kJZ-26z7qY%252F-MLW-W018dbAzZRednoA%252Fimage.png%3Falt%3Dmedia%26token%3Dd10d36e9-a759-4a23-b149-0c4fa791b405&width=768&dpr=4&quality=100&sign=e9652b0b&sv=2)

Bu so'zlardan o'zgaruvchilarni nomlashda foydalanmang

## AMALIYOT

Quyidagi mashqlarni bajaring:

- `"Hello World!"` matnini yangi o'zgaruvchiga yuklang va `print()` yordamida konsolga chiqaring
    
- `xabar` deb nomlangan o'zgaruvchiga biror matn yuklang va konsolga chiqaring, keyin esa o'zgaruvchiga yangi qiymat berib uni ham konsolga chiqaring.
    
- `class` den nomlangan o'zgaruvchi yarating, unga biror qiymat bering va konsolga chiqaring (siz kutgan natija chiqdimi?)
    
- Quyidagi kodni bajaring:
    

```python
radius = 5
pi = 3.14159
aylana_yuzi = pi * radius**2
print("Radiusi" , radius, "ga teng aylananing yuzi=", aylana_yuzi)
```

---

# 2. STRING (MATN)
## STRING VA UNICODE

**STRING** (matn) —Pythondagi eng mashxur ma'lumot turlaridan biri. Avvalgi darsda ko'rganimizdek, o'zgaruvchiga matn yuklash uchun matn qo'shtirnoq (`" "`) yoki birtirnoq (`' '`) ichida yozilishi kerak.

```python
shahar = "Қўқон"
viloyat = 'Фарғона'
```

Pythonda matnlar [Unicode](https://unicode-table.com/en/) jadvalidagi istalgan belgilaridan iborat bo'lishi mumkin (jumladan o'zbek, arab, hind, xitoy alifbosidagi harflar yoki turli emoji-smayliklar).

```python
matn = "Men yangi 📱 oldim"
print(matn)
```

Natija: `Men yangi 📱 oldim`

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLjUEbNQbWqMBCY1uql%252F-MLjVgUODxYRloFHWptm%252Fimage.png%3Falt%3Dmedia%26token%3D6e6eaef4-4958-479f-9622-523110678e8c&width=768&dpr=4&quality=100&sign=9cce1609&sv=2)

UNICODE jadvalidagi harf va belgilarga misol

## STRING USTIDA AMALLAR

### Matnlarni qo'shish operatori (`+`)

Matnlarni qo'shish uchun `+` operatoridan foydalanmiz:

```python
ism = 'Ahmad'
print("Mening ismim " + ism)
```

Natija: `Mening ismim Ahmad`

```python
ism = 'Ahad'
familiya = 'Qayum'
print(ism + familiya)
```

Natija: `AhadQayum`

Yuqoridagi kodda ism va familiya orasiga bo'shliq belgisini qo'shmaganimiz uchun ikki matn qo'shilib yozildi. Buni to'g'rilash uchun, 3-qatorni quyidagicha yozamiz:

```python
ism = 'Ahad'
familiya = 'Qayum'
print(ism + ' ' + familiya) # ikki o'zgaruvchi orasiga bo'sh joy qo'shamiz
```

Natija: `Ahad Qayum`

### f-string

Ikki (va undan ko'p) matn ko'rinishidagi o'zgaruvchilarni birlashtirish uchun f-string usulidan `f"{matn1} {matn2}"` ham foydalansak bo'ladi:

```python
ism = "Ahad"
familiya = 'Qayum'
ism_sharif = f"{ism} {familiya}"
print(ism_sharif)
```

Bu usul yordamida uzun matnlarni ham yasash mumkin:

```python
ism = "James"
familiya = 'Bond'
print(f"Salom, mening ismim {familiya}. {ism} {familiya}!")
```

Natija: `Salom, mening ismim Bond. James Bond!`

### Mahsus belgilar

Matnga bo'shliq qo'shish uchun `\t` belgisidan, yangi qatordan boshlash uchun `\n` belgisidan foydalanamiz:

```python
print('Hello World!')
print('Hello \tWorld!')
print('Hello \nWorld!')
```

Natija:

`Hello World!`

`Hello     World!`

`Hello`

`World!`

## STRING METODLARI

Pythonda string ustida amalga oshirish mumkin bo'lgan tayyor amallar to'plami mavjud. Bunday amallar to'plami **metodlar** deb ataladi.

Metodlarni qo'llash uchun metod nomi matndan so'ng `.metod_nomi()` ko'rinishida yoziladi. Keling shunday metodlarning ba'zilari bilan tanishaylik.

### `upper()` va `lower()` metodlari

`upper()` metodi matndagi har bir harfni katta harfga o'zgartiradi.

```python
ism = 'Ahad'
familiya = 'Qayum'
ism_sharif = f"{ism} {familiya}"
print(ism_sharif.upper())
```

Natija: `AHAD QAYUM`

`lower()` metodi esa aksincha, har bir harfni kichik harfga o'zgartiradi.

```python
ism = 'Ahad'
familiya = 'Qayum'
ism_sharif = f"{ism} {familiya}"
print(ism_sharif.lower())
```

Natija: `ahad qayum`

### `title()` va `capitalize()` metodlari

`title()` metodi matndagi har bir so'zning birinchi harfini katta harf bilan yozadi.

```python
ism_sharif = 'james bond'
print(ism_sharif.title())
```

Natija: `James Bond`

`capitalize()` esa faqatgina eng birinchi so'zning birinchi harfini katta bilan yozadi.

```python
ism_sharif = 'james bond'
print(ism_sharif.capitalize())
```

Natija: `James bond`

Metodlarni faqat o'zgaruvchilarga emas, balki to'g'ridan-to'g'ri matnga ham qo'llash mumkin (aslida o'zgaruvchi ham matnning (yoki boshqa ma'lumotning) manzili xolos)

```python
print('james bond'.upper())
```

Natija: `JAMES BOND`

### `strip()`, `rstrip()` va `lstrip()` metodlari

Bu metodlar matnning boshi va oxiridagi bo'sh joylarni olib tashlaydi.

- `lstrip()` — matn boshidagi bo'shliqni,
    
- `rstrip()` – matn oxiridagi bo'shliqni,
    
- `strip()` — matn boshi va oxiridagi bo'shliqlarni olib tashlaydi
    

```python
meva = "     olma     "
print("Men " + meva.lstrip() + " yaxshi ko'raman")
print("Men " + meva.rstrip() + " yaxshi ko'raman")
print("Men " + meva.strip() + " yaxshi ko'raman")
print("Men " + meva + " yaxshi ko'raman")
```

> Men olma      yaxshi ko'raman
> 
> Men     olma yaxshi ko'raman
> 
> Men olma yaxshi ko'raman
> 
> Men     olma     yaxshi ko'raman

Matnlar bilan ishlaydigan metodlar ko'p. Ularning ba'zilari bilan kelajakda yana tanishamiz, to'liq ro'yhatni esa quyidagi [sahifada](https://www.w3schools.com/python/python_ref_string.asp) ko'rishingiz mumkin.

**Metodlar o'zgaruvchi ichidagi asl matnni o'zgartirmaydi!**

## INPUT —FOYDALANUVCHI BILAN MULOQOT

Shu paytgacha biz o'zgaruvchilarning qiymatini dasturning ichida berayotgan edik. Keling endi qiymatni o'zimiz emas, balki dastur foydalanuvchilariga kiritish imkonini beramiz.

Buning uchun `input()` funktsyasidan foydalanamiz.

```python
ism = input("Ismingiz nima?")
print("Assalom alaykum, " + ism)
```

Yuqoridagi dastur, avval 1-qatorda foydalanuvchining ismini so'raydi. Foydalanuvchi ismini kiritib, **Enter** tugmasini bosgach, foydalanuvchi kiritgan matn`ism` degan o'zgaruvchiga yuklanadi va dasturining 2-qatori bajaradi:

Natija:

`Ismingiz nima?anvar`

`Assalom alaykum, anvar`

Keling yuqoridagi kod va uning natijasini chiroyliroq ko'rinishga keltiramiz.

```python
ism = input("Ismingiz nima?\n>>>") # Foydalanuvchi ismini yangi qatordan kiritadi
print("Assalom alaykum, " + ism.title())
```

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLg_Rlt3ghgz7tHHhmJ%252F-MLgalhJF6uRE0GABSmk%252Finput.gif%3Falt%3Dmedia%26token%3D9a2da927-7f2a-4094-a1a1-6b64dddc4b00&width=768&dpr=4&quality=100&sign=e81e9c68&sv=2)

Foydalanuvchidan qiymat olish

## AMALIYOT

Quyidagi mashqlarni bajaring:

- Quyidagi o'zgaruvchilarni yarating:
    
    - `kocha="Bog'bon"`
        
    - `mahalla="Sog'bon"`
        
    - `tuman="Bodomzor"`
        
    - `viloyat="Samarqand"`
        
    
- Yuqoridagi o'zgaruvchilarni jamlab, quyidagi ko'rinishda konsolga chiqaring:
    
    - `Bog'bon ko'chasi, Sog'bon mahallasi, Bodomzor tumani, Samarqand viloyati`
        
    
- Yuqoridagi o'zgaruvchilarning (`kocha`, `mahalla`, `tuman`, `viloyat`) qiymatini foydalanuvchidan so'rang. Va avvalgi mashqni takrorlang.
    
- Yuqoridagi matnni konsolga chiqarishda har bir verguldan keyin yangi qatordan yozing
    
- Yuqoridagi matnni **f-string** yordamida, yangi, `manzil` deb nomlangan o'zgaruvchiga yuklang
    
- `manzil`ga biz yuqorida o'rgangan `title()`, `upper()`, `lower()` , `capitalize()` metodlarini qo'llab ko'ring.
    
- Quyidagi o'zgaruvchilarni yarating:
    
    - `kocha="Bog'bon"`
        
    - `mahalla="Sog'bon"`
        
    - `tuman="Bodomzor"`
        
    - `viloyat="Samarqand"`
        
    
- Yuqoridagi o'zgaruvchilarni jamlab, quyidagi ko'rinishda konsolga chiqaring:
    
    - `Bog'bon ko'chasi, Sog'bon mahallasi, Bodomzor tumani, Samarqand viloyati`
        
    
- Yuqoridagi o'zgaruvchilarning (`kocha`, `mahalla`, `tuman`, `viloyat`) qiymatini foydalanuvchidan so'rang. Va avvalgi mashqni takrorlang.
    
- Yuqoridagi matnni konsolga chiqarishda har bir verguldan keyin yangi qatordan yozing
    
- Yuqoridagi o'zgaruvchilarni **f-string** yordamida, yangi, `manzil` deb nomlangan o'zgaruvchiga yuklang
    
- `manzil`ga biz yuqorida o'rgangan `title()`, `upper()`, `lower()` , `capitalize()` metodlarini qo'llab ko'ring.

---

---

# 3. SONLAR
## INTEGERS — BUTUN SONLAR

Butun sonlarni ham o'zgaruvchida saqlash, ularning ustida qo'shish (`+`), ayirish (`-`), ko'paytirish(`*`), bo'lish (`/`) kabi [arifmetik amalarni](https://python.sariq.dev/ilk-qadamlar/03-print#arifmetik-amallar) bajarish mumkin:

```python
a = 20  # Sonlar musbat yoko
b = -30 # manfiy bo'lishi mumkin
c = a + b
print(c)
```

Natija: `-10`

Python - operatorlar orasidagi bo'shliqlarni inobatga olmaydi. O'qishga qulay bo'lishi uchun yuqoridagi kabi (bo'shliqlar bilan) yozishingiz mumkin.

```python
# Kvadratning yuzini hisoblaymiz
kvdrt_tmni = 20 # Kavdratning tomoni 20 ga teng
kvdrt_yuzi = kvdrt_tmni**2 # Kvadrat yuzini hisoblaymiz
print(kvdrt_yuzi)
```

Natija: `400`

## FLOATS — O'NLIK SONLAR

Pythonda o'nlik sonlar **floating point numbers** yoki qisqa qilib **floats** deyiladi. "_Floating point numbers_" atamasini o'zbek tiliga "_suzuvchi nuqtali sonlar_" deb tarjima qilish mumkin. Ingliz tilida o'nlik sonlarni yozishda vergul (`,`) emas nuqta (`.`) belgisi ishlatiladi, va bu nuqta sonning katta kichikligiga qarab joyi o'zgargani uchun _"floating"_ _(suzuvchi)_ deyiladi.

```python
pi = 3.14159 # o'nlik son (float)
radius = 10  # butun son (integer)
diametr = 2*radius
print("Aylana uzunligi ", pi*diametr, " ga teng.")
```

Natija: `Aylana uzunligi 4.712384999999999 ga teng.`

## BUTUN SONDAN O'NLIK SONGA

Avval aytganimizdek ikki butun sonni bo'lish (`/`) natijasida o'nlik son hosil bo'ladi (natija butun bo'lsa ham).

```python
a = -20
b = 40
c = b/a
print(c) # natija o'nlik son bo'ladi
```

Natija: `-2.0`

Shuningdek butun va o'nlik sonlar o'rtasidagi har qanday arifmetik amallarning natijasi ham o'nlik son bo'ladi.

```python
a = 2
b = 3.0
# Quyidagi arifmetik amallarning natijasi o'nlik son hosil qiladi
print(a+b) 
print(a*b)
print(a**b)
print(2*(a+b))
```

Natijalar:

`2.0`

`5.0`

`6.0`

`8.0`

`10.0`

## UZUN SONLARNI KIRITISH

Uzun sonlarni kiritishda, qulaylik uchun, raqamlarni pastki chiziq (`_`) yordamida guruhlash mumkin. Python - son tarkibidagi pastki chiziqlarni (`_`) inobatga olmasdan, uzun sonligicha qabul qiladi.

```python
aholi_soni = 7_594_000_000 # o'zmizga qulay bo'lishi uchun shinday yozdik
print("Yer kurrasida", aholi_soni, " ga yaqin odam yashaydi")
```

Natija: `Yer kurrasida 7594000000 ga yaqin odam yashaydi`

## KONSTANTA

Aksar dasturlash tillarida konstant qiymatlar tushunchasi bor. Konstantlar o'zgarmas bo'ladi (misol uchunππ ning qiymati konstant, o'zgarmas qiymat). Pythonda konstant tushunchasi yo'q, shuning uchun dasturchilar bunday o'zgaruvchilarning nomini katta harflar bilan yozadilar (_ogohlantirish sifatida_). Bu albatta qat'iy qonun emas, lekin kelajakda o'zgaruvchilar orasida konstant qiymatlarni ajratish uchun yaxshi usul.

```python
PI = 3.14159
raduis = 21.2
```

## BIR NECHTA O'ZGARUVCHIGA QIYMAT BERISH

Birdaniga bir nechta o'zgaruvchiga qiymat berish uchun o'zgaruvchilar va ularga mos qiymatlar vergul `(,)` bilan ajratiladi:

```python
x, y, z = 10, -7.25, -30
```

Yuqoridagi kod `x` ga `10`, `y` ga `-7.25`, va `z` ga `-30` qiymatini yuklaydi.

## O'ZGARUVCHI TURINI ALMASHTIRISH

Keling quyidagi misolni ko'raylik, maqsadimiz `ism` va `yosh` degan ikki o'zgaruvchini yangi `xabar` degan o'zgaruvchiga yuklab, `"Jobir 16 yoshda"` degan matnni konsolga chiqarish:

```python
ism = 'Jobir'
yosh = 36
xabar = ism + ' ' + yosh + ' yoshda'
print(xabar)
```

Natija: `**TypeError: can only concatenate str (not "int") to str**`

Afsuski, kutilgan natija o'rniga xatolik chiqdi. Agar xatoni ingliz tilidan tarjima qilsak, matn (str) va son (int) ni jamlab bo'lmaydi degan ma'no chiqadi.

Demak Pythonda matn (string) va son (int, float) turidagi o'zgaruvchilarni jamlab bo'lmas ekan. Xo'sh, bunga yechim bormi? **Albatta**.

Pythonda bir turdagi o'zgaruvchini boshqa turga o'tkazish mumkin, bu ingliz tilida _**typecasting**_ detiladi. Buning uchun Pythonda mahsus funktsiyalar bor, keling ular bilan tanishamiz:

- `str()`— int yoki float turidagi sonlarni matnga o'zgartiradi.
    
- `int()`— matn yoki float ko'rinishidagi qiymatlarni butun songa o'zgartiradi. Bunda matn butun son ko'rinishida bo'lishi kerak.
    
- `float()`— matn yoki int ko'rinishidagi qiymatlarni o'nlik songa o'zgartiradi.
    

Demak, yuqoridagi kod to'g'ri ishlashi uchun 3-qatorni quyidagicha o'zgartiramiz:

```python
ism = 'Jobir'
yosh = 36
xabar = ism + ' ' + str(yosh) + ' yoshda'
print(xabar)
```

Natija: `Jobir 36 yoshda`

`str(yosh)` kodi `yosh` degan o'zgaruvchining qiymatini matn ko'rinishida ko'rsatdi xolos. Asl o'zgaruvchining qiymati sonligicha qoladi. `int()` va `float()`ham huddi shunday ishlaydi.

## O'ZGARUVCHI TURINI TEKSHIRISH

Kodimizda o'zgaruvchilar ko'payib ketdi. Yuqoridagi kabi xatolar qilmaslik uchun ba'zida o'zgaruvchinig turini tekshrish talab qilinadi. Buning uchun `type()` funktsiyasidan foydalanamiz:

```python
ism = 'Jobir'
yosh = 36
print(type(ism))  # ism degan o'zgaruvchining turini konsolga chiqaramiz
print(type(yosh)) # ismyosh degan o'zgaruvchining turini konsolga chiqaramiz
```

Natija:

`<class 'str'>`

`<class 'int'>`

Kurib turganingizdek, `ism` nomli o'zgaruvchi`'str'` ya'ni matn, `yosh` esa `'int'` son turida ekan.

## `INPUT()` VA SONLAR

Avvalgi darsimizda foydalanuvchidan ma'lumot olish uchun input() funktsyasidan foydalanishni o'rgandik. Kelin endi shu funktsiya yordamida foydalanuvchidan son olishni ko'raylik. Quyidagi kod foydalanuvchining tug'ilgan yilini so'raydi va uning yoshini hisoblab beradi:

```python
#1 foydalanuvchining tug'ilgan yilini so'raymiz
t_yil = input("Tug'ilgan yilingizni kiriting: ")
#2 foydalanuvchi yoshini xisoblaymiz
yosh = 2020 - t_yil # 
#3 foydalanuvchi yoshini konsolga chiqaramiz
print("Siz " + yosh + " yoshda ekansiz")
```

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLlNypIunyr4AW0df3A%252F-MLlO3YahEjv90pUVBMt%252Fimage.png%3Falt%3Dmedia%26token%3Dcab76abe-4792-4223-a790-14c0600f5276&width=768&dpr=4&quality=100&sign=874ceaec&sv=2)

Natija: `**TypeError: unsupported operand type(s) for -: 'int' and 'str'**`

Kutilgan natija o'rniga xatolik. Lekin xato qayerda? Dastur tug'ilgan yilimni so'radi, men `1983` deb kiritdim va shu zaxoti xato ro'y berdi va dastur to'xtadi. Xatoni tarjima qilsak son (int) va matn (str) o'rtasida ayirish (`-`) amalini bajarib bo'maydi deyapti.

Gap shundaki, `input()` funktsiyasi har qanday kiritilgan qiymatni matn (string) ko'rinishida qabul qiladi (garchi biz son kiritgan bo'lsak ham). Keling, konsolda `t_yil` degan o'zgaruvchining turini tekshirib ko'ramiz.

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLlNypIunyr4AW0df3A%252F-MLlPEmNc-bRsDfbd3Ib%252Fimage.png%3Falt%3Dmedia%26token%3D71fa7c8b-b820-4f5c-9805-c77631d98613&width=768&dpr=4&quality=100&sign=eb3a780f&sv=2)

Ko'rib turganingizdek `t_yil` o'zgaruvchisi saqlayotgan qiymat `str` ya'ni matn ekan. Kodimizning 2 va 6-qatorlarini o'zgartiramiz:

```python
#1 foydalanuvchining tug'ilgan yilini so'raymiz va qiymatni int ga aylantiramiz
t_yil = int(input("Tug'ilgan yilingizni kiriting: "))
#2 foydalanuvchi yoshini xisoblaymiz
yosh = 2020 - t_yil # 
#3 foydalanuvchi yoshini konsolga chiqaramiz
print("Siz " + str(yosh) + " yoshda ekansiz")
```

Natija:

`Tug'ilgan yilingizni kiriting: 1983`

`Siz 37 yoshda ekansiz`

Yuqoridagi kodning 2-qatoriga e'tibor bersangiz, biz ikki funktsiyani bir biriga joylab yozdik (`int(input()`). Aslida, ajratib ham yozishimiz mumkin edi:

```python
#1.1 foydalanuvchining tug'ilgan yilini so'raymiz
t_yil = input("Tug'ilgan yilingizni kiriting: ")
#1.2 t_yil o'zgaruvchini int ga aylantiramiz
t_yil = int(t_yil)
#2 foydalanuvchi yoshini xisoblaymiz
yosh = 2020 - t_yil # 
#3 foydalanuvchi yoshini konsolga chiqaramiz
print("Siz " + str(yosh) + " yoshda ekansiz")
```

## AMALIYOT

Quyidagi dasturlarning har birini alohida fayl ko'rinishida yozing va bajaring:

- Foydalanuvchi kiritgan sonning kvadrati va kubini konsolga chiqaruvchi dastur
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLounVATri6iU10sCuw%252F-MLqbUCW4fuICo4zdkrD%252Fimage.png%3Falt%3Dmedia%26token%3Da17936ee-7b1e-40bd-824c-971074a0e475&width=768&dpr=4&quality=100&sign=cb067574&sv=2)

- Foydalanuvchining yoshini so'rab, uning tug'ilgan yilini hisoblab, konsolga chiqaruvchi dastur
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLlQxcWdJFuxfNQYaOI%252F-MLlYLnFPKXzahFJOvR5%252Fimage.png%3Falt%3Dmedia%26token%3D19c4f43a-e686-4664-b1a1-99852df0cbe8&width=768&dpr=4&quality=100&sign=50394f43&sv=2)

- Foydalanuvchidan ikki son kiritshni so'rab, kiritilgan sonlarning yig'indisi, ayirmasi, ko'paytmasi va bo'linmasini chiqaruvchi dastur
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLmBsKDaC1xFQ77JlHJ%252F-MLmD9nxgqMpimSgbVKf%252Fimage.png%3Falt%3Dmedia%26token%3Dc7250d0b-fbbd-4c76-9e73-66588fbcb4e8&width=768&dpr=4&quality=100&sign=eede58b8&sv=2)

---

# 4. LIST (RO'YXAT)
## LIST BILAN TANISHAMIZ

Avvalgi darsimizda biz o'zgaruvchi yaratish, va uning ichida biror qiymatni (matn yoki son) saqlashni o'rgandik. Bunda biz bitta o'zgaruvchiga bitta qiymat berdik xolos.

Bugun o'rganadigan navbatdagi mal'umot turi **List** (**ro'yxat**) deb ataladi. Ro'yxat o'z nomi bilan, bitta o'zgaruvchida bir nechta qiymatlarni saqlash imkonini beradi. Bu qiymatlar List **elementlari** deyiladi. Ro'yxatda son, matn yoki aralash turdagi elementlarni saqlash mumkin.

List quyidagicha yaratiladi:

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik"] # mevalar ro'yxati (matnlar)
narhlar = [12000, 18000, 10900, 22000] # narhlar ro'yxati (sonlar)
sonlar = ['bir', 'ikki', 3, 4, 5] # sonlar va matnlar aralash ro'yxat
ismlar = [] # bo'sh ro'yxat
```

Ro'yxat saqlaydigan o'zgaruvchilarni nomlashda _-lar_ (ko'plik) qo'shimchasini qo'shish maqsadga muvofiq bo'ladi (inlgiz tilida _-s_).

Misol uchun: `mevalar`, `uylar`, `cars`, `toys`, `books`

## LIST ELEMENTLARI

Ro'yxatdagi har bir element tartib bilan joylashgani sababli, biz istalgan elementga uning tartib raqami (indeksi) bo'yicha murojat qilishimiz mumkin.

Dasturlash olamida indeks `0` dan boshlanadi! Ya'ni Listning birinchi elementing tartib raqami (indeksi) `0` ga, ikkinchi elementning indeksi `1` ga teng va hokazo.

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik"] # mevalar ro'yxati (matnlar)
print("Birinchi meva: ", mevalar[0])
print("Ikkinchi meva: ", mevalar[1])
```

Natija:

`Birinchi meva: olma`

`Ikkinchi meva: anjir`

Agar list ichidagi elementlar matn ko'rinishid bo'lsa, ularga [string metodlarni](https://python.sariq.dev/ozgaruvchilar-va-malumot-turlari/05-string#string-metodlari) qo'llashimiz mumkin:

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik"] # mevalar ro'yxati (matnlar)
print("Birinchi meva: ", mevalar[0].title())
print("Ikkinchi meva: ", mevalar[1].upper())
```

Natija:

`Birinchi meva: Olma`

`Ikkinchi meva: ANJIR`

List elementlari ustida arifmetik amallar bajarish:

```python
narhlar = [12000, 18000, 10900, 22000]
print(narhlar[2] + narhlar[3])
```

Natija: `32900`

Pythonda Listning eng oxirgi elementiga `-1` indeksi orqali ham murojat qilish mumkin. Bu usul Listning uzunligini bilmaganda juda asqotadi.

```python
car_models = ['Toyota', 'GM', 'Volvo', 'BMW', 'Hyundai', 'Kia', 'Volkswagen']
print(car_models[-1]) # Listning eng oxirgi elementiga -1 bilan murojat qilamiz 
```

Natija: `Volkswagen`

## ELEMENTLARNI QO'SHISH, O'CHIRISH VA O'ZGARTIRISH

Dastur davomida listning tarkibi o'zgarishi, yangi elementlar qo'shilishi, ba'zi elementlar o'chirilishi tabiiy hol. Misol uchun "Bozorlik ro'yxati" degan dasturni tasavvur qilaylik, foydalanuvchi ro'yxatga yangi mahsulotlar qo'shishi, sotib olganlarini esa o'chrishi mumkin.

### Elementni o'zgartirish

Ro'yxatdagi biror elementning qiymatini o'zgartirish uchun, o'sha elementga indeksi bo'yicha murojat qilamiz va yangi qiymat yuklaymiz

```python
narhlar = [12000, 18000, 10900, 22000]
narhlar[0] = 13000 # 1-qiymatni 13000 ga o'zgartiramiz
narhlar[2] = 11000 # 3-qiymatni 11000 ga o'zgartiramiz
narhlar[3] = narhlar[3]+2000 # 4-qiymatga 2000 qo'shamiz
print(narhlar)
```

Natija: `[13000, 18000, 11000, 24000]`

### Yangi element qo'shish

#### `.append()` metodi

Ro'yxatga yangi element qo'shishning oson usuli bu `**.append()**` metodi yordamida ro'yxatning **oxiriga** qiymat qo'shish:

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik"]
mevalar.append("tarvuz") # mevalar ga tarvuz qo'shamiz
print(mevalar)
```

Natija: `['olma', 'anjir', 'shaftoli', "o'rik", 'tarvuz']`

`**.append()**` metodi bo'sh ro'yxatni to'ldrisihda juda qulay usul. Odatda dastur boshida bo'sh ro'yxat yaratilib, dastur davomida ro'yxat foydalanuvchi tomonidan to'ldirib borilishi odatiy hol.

```python
cars = [] # bo'sh ro'yxat yaratamiz
cars.append('Lacetti') # ro'yxatga Lacetti mashinasini qo'shamiz
cars.append('Nexia 3') # ro'yxatga Nexia 3 mashinasini qo'shamiz
cars.append('Cobalt')  # ro'yxatga Cobalt  mashinasini qo'shamiz
print(cars)
```

Natija: `['Lacetti', 'Nexia 3', 'Cobalt']`

#### `.insert()` metodi

Ro'yxatning istalgan joyiga yangi element qo'shish uchun `**.insert()**` metodidan foydalanamiz. `.insert()` metodi ichida yangi elementning indeksi va qiymati beriladi:

```python
cars = ['Lacetti', 'Nexia 3', 'Cobalt']
cars.insert(0, 'Malibu') # 1-o'ringa yangi qiymat qo'shamiz
print(cars)
```

Natija: `['Malibu', 'Lacetti', 'Nexia 3', 'Cobalt']`

```python
cars.insert(2, 'Damas') # 3-o'ringa yangi qiymat qo'shamiz
print(cars)
```

Natija: `['Malibu', 'Lacetti', 'Damas', 'Nexia 3', 'Cobalt']`

### Elementni o'chirish

Ro'yxatdan biror elementni olib tashlash uchun uning indeksini yoki qiymatini bilishimiz lozim.

Inedks yordamida olib tashlash uchun `**del**` operatoridan foydalanamiz:

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik", 'anor']
del mevalar[1] # 2-element (anjir) ni o'chirib tashlaymiz
print(mevalar)
```

Natija: `['olma', 'shaftoli', "o'rik", 'anor']`

Element qiymati bo'yichi o'chirish uchun esa `**.remove(qiymat)**` metodidan foydalanamiz. Buning uchun qavs ichida o'chirib tashlash kerak bo'lgan qiymatni yozamiz

```python
mevalar = ['olma', 'anjir', 'shaftoli', "o'rik", 'anor']
mevalar.remove('shaftoli') # Ro'yxatdan shaftolini o'chirdik
print(mevalar)
```

Natija: `['olma', 'anjir', "o'rik", 'anor']`

`**.remove(qiymat)**` metodi ro'yxatda uchragan birinchi mos keluvchi qiymatni o'chiradi. Agar ro'yxatning ichida 2 va undan ko'p bir hil qiymatli elementlar bo'lsa, ulardan eng birinchisi o'chadi.

```python
hayvonlar = ['it', 'mushuk', 'sigir', 'qo\'y', 'quyon', 'mushuk']
hayvonlar.remove("mushuk") # Ro'yxatda 2 ta mushuk bor, ulardan birinchisi o'chadi
print(hayvonlar)
```

Natija: `['it', 'sigir', "qo'y", 'quyon', 'mushuk']`

### Elementni sug'urib olish

Ba'zida biror elementni butunlay o'chirib tashlash emas, balki uni ro'yxatdan sug'urib olish va undan foydalanish talab qilinishi mumkin. Buning uchun Pythonda `**.pop(indeks)**` metodidan foydalanmiz.

```python
bozorlik = ["yog'", 'un', 'piyoz', 'banan', "go'sht"]
mahsulot = bozorlik.pop(3) # Ro'yxatdan banan ni sug'urib olamiz
print("Men " + mahsulot + " sotib oldim")
print("Olinmagan mahsulotlar: ", bozorlik)
```

Natija:

`Men banan sotib oldim`

`Olinmagan mahsulotlar: ["yog'", 'un', 'piyoz', "go'sht"]`

Agar `**.pop()**` metodida indeks berilmasa, ro'yxatdan o'xirgi qiymat sug'urib olinadi.

## AMALIYOT

Quyidagi mashqlarni bajaring:

- `ismlar` degan ro'yxat yarating va kamida 3 ta yaqin do'stingizning ismini kiriting
    
- Ro'yxatdagi har bir do'stingizga qisqa xabar yozib konsolga chiqaring:
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLvZJbRru8b9RC9s6ag%252F-MLvbRkA4uEAqqhKk6Yi%252Fimage.png%3Falt%3Dmedia%26token%3Da768a42e-2516-4bbc-83ad-63d012758b25&width=768&dpr=4&quality=100&sign=862267ab&sv=2)

- `sonlar` deb nomlangan ro'yxat yarating va ichiga turli sonlarni yuklang (musbat, manfiy, butun, o'nlik).
    
- Yuqoridagi ro'yxatdagi sonlar ustida turli arifmetik amallar bajarib ko'ring. Ro'yxatdagi ba'zi sonlarning qiymatini o'zgartiring, ba'zilarini esa almashtiring.
    
- `t_shaxslar`va `z_shaxslar` degan 2 ta ro'yxat yarating va biriga o'zingiz eng ko'p hurmat qilgan tarixiy shaxslarning, ikkinchisiga esa zamonamizdagi tirik bo'lgan shaxslarning ismini kiriting.
    
- Yuqoridagi ro'yxatlarning har biridan bittadan qiymatni sug'urib olib (`**.pop()**`), quyidagi ko'rinishda chiqaring:
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MLvdTf93oJb9hVewsv7%252F-MLyyn0plvxsTJKVHnxQ%252Fimage.png%3Falt%3Dmedia%26token%3D76b9a4e8-14fe-4d66-bde4-72464e6edbad&width=768&dpr=4&quality=100&sign=152acdaf&sv=2)

- `friends`nomli bo'sh ro'yxat tuzing va unga `.append()` yordamida 5-6 ta mehmonga chaqirmoqchi bo'lgan do'stlaringizni kiriting.
    
- Yuqoridagi ro'yxatdan mehmonga kela olmaydigan odamlarni `.remove()` metodi yordamida o'chrib tashlang.
    
- Ro'yxatning oxiriga, boshiga va o'rtasiga yangi ismlar qo'shing.
    
- Yangi `mehmonlar`deb nomlangan bo'sh ro'yxat yarating. `.pop()` va `.append()` metodlari yordamida mehmonga kelgan do'stlaringizning ismini friends ro'yxatidan sug'urib olib, mehmonlar ro'yxatiga qo'shing.

---

# 5. RO'YXATLAR BILAN ISHLASH
## RO'YXATNI TARTIBLASH

Aksar holatlarda ro'yxat ichidagi elementlarni alifbo ketma-ketligida tartiblash talab qilinishi mumkin. Buning uchun list uchun maxsus `**.sort()**` metodidan foydalanamiz.

```python
cars = ['bmw','mercedes benz', 'volvo', 'general motors', 'tesla', 'audi']
cars.sort()
print(cars)
```

Natija: `['audi', 'bmw', 'general motors', 'mercedes benz', 'tesla', 'volvo']`

Kurib turibsiz, yuqoridagi ro'yxatimiz alifbo bo'yicha tartiblandi.

**Diqqat!** Tartiblashda katta harflar kichik harflardan avval kelishini hisobga oling. Agar matndagi so'zlarning bosh harfi katta-kichik aralash yozilgan bo'lsa, ularni bir ko'rinishga keltirib olish maqsadga muvofiq bo'ladi.

```python
cars = ['Bmw','mercedes benz', 'volvo', 'gm', 'tesla', 'audi']
cars.sort()
print(cars)
```

Natija: `['Bmw', 'audi', 'gm', 'mercedes benz', 'tesla', 'volvo']`

Yuqoridagi misolda 'Bmw' elementi katta harf bilan boshlangani uchun ro'yxatning boshidan joy oldi.

Ro'yxatni teskari tartibda saqlash uchun `.sort()` metodi ichida `reverse=True` argumentini ham kiritamiz.

```python
cars = ['bmw','mercedes benz', 'volvo', 'general motors', 'tesla', 'audi']
cars.sort(reverse=True)
print(cars)
```

Natija: `['volvo', 'tesla', 'mercedes benz', 'general motors', 'bmw', 'audi']`

`**.sort()**` metodi ro'yxatni tartiblaydi. Ba'zida asl ro'yxat ichidagi elementlarning ketma-ketligini buzmagan holda ro'yxatni tartiblash talab qilinishi mumkin. Buning uchun `**sorted()**` funktsiyasidan foydalanamiz:

```python
mehmonlar = ['Odil', 'Hamid', 'Temur', 'Avazbek', 'Farruh', 'Shamsiddin']
print("sorted() qaytargan ro'yxat:", sorted(mehmonlar))
print("Asl ro'yxat o'zgarmas qoldi:", mehmonlar)
```

Natija:

`sorted() qaytargan ro'yxat: ['Avazbek', 'Farruh', 'Hamid', 'Odil', 'Shamsiddin', 'Temur']`

`Asl ro'yxat o'zgarmas qoldi: ['Odil', 'Hamid', 'Temur', 'Avazbek', 'Farruh', 'Shamsiddin']`

`**sorted()**` funktsiyasi yordamida teskari tartiblash uchun ham `**reverse=True**` argumentini beramiz:

```python
print(sorted(mehmonlar, reverse=True))
```

Natija: `['Temur', 'Shamsiddin', 'Odil', 'Hamid', 'Farruh', 'Avazbek']`

Yuoqridagi ikki usul bilan sonli ro'yxatlarni ham tartiblashimiz mumkin:

```python
ages = [12, 98, 34, 65, 34, 76, 11]
ages.sort()
print(ages)
print(sorted(ages, reverse=True))
```

Natija:

`[11, 12, 34, 34, 65, 76, 98]`

`[98, 76, 65, 34, 34, 12, 11]`

## RO'YXATNI AYLANTIRISH

Ba'zida ro'yxatni aylantirish (boshini oxiriga, oxirini boshiga) talab qilinishi mumkin. Buning uchun `**.reverse()**` metodidan foydalanamiz.

```python
fruits = ['pear','banana','apple','watermelon','lemon']
fruits.reverse()
print(fruits)
```

Natija: `['lemon', 'watermelon', 'apple', 'banana', 'pear']`

Natija va asl ro'yxatni solishtiring.

## RO'YXATNING UZUNLIGINI BILISH

Ro'yxatning uzunligi, ya'ni uning ichidagi elementlar sonini aniqlash uchun `**len()**` funktsiyasidan foydalanamiz:

```python
fruits = ['pear','banana','apple','watermelon','lemon']
print("Elementlar soni:",len(fruits)) # len(fruits) ro'yxat uzunligini qaytaradi
```

Natija: `Elementlar soni: 5`

## `range()` FUNKTSIYASI

Bu funktsiya yordamida biz ma'lum oraliqdagi sonlar ketma-ketligini yaratishimiz mumkin. `**list()**` funktsiyasi yordamida esa bu oraliqni ro'yxat shaklida saqlab olamiz:

```python
sonlar = list(range(0,10)) # 
print(sonlar)
```

Natija: `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`

Yuqoridagi misolda `range(0,10)` funktsiyasi `0` dan `9` gacha sonlar ketma-ketligini shakllantirdi, `list(range(0,9))` esa bu ketma-ketlikni ro'yxatga aylantirdi.

**Diqqat!** E'tibor qiling `**range()**` funktsiyasi ikkinchi indeksdan bitta avval to'xtaydi.

`**range()**` yordamida qadamni ham berishimiz mumkin:

```python
juft_sonlar = list(range(0,20,2)) # 0 dan 20 gacha 2 qadam bilan
toq_sonlar = list(range(1,20,2))  # 1 dan 20 gacha 2 qadam bilan
print("Juft sonlar: ", juft_sonlar)
print("Toq sonlar: ", toq_sonlar)
```

Natija:

`Juft sonlar: [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]`

`Toq sonlar: [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]`

Agar sonlar ketma-ketligi 0 dan boshlansa, `range()` funktsiyasida yakuniy indeksni ko'rsatish kifoya. Misol uchun `range(0,10)` emas `range(10)` deb yozsak ham bo'laveradi.

## SONLI RO'YXAT USTIDA SODDA AMALLAR

Pythonda ro'yxatlar ustida ba'zi sodda amallarni ham bajarish mumkin. Misol uchun ro'yxatdagi eng kichik sonni topish uchun `**min()**` funktsiyasidan, eng katta sonni topish uchun esa `**max()**` funktsiyasidan, sonlarning yig'indisini topish uchun esa `**sum()**` funktsyasidan foydalansak bo'ladi:

```python
narhlar = [12000, 22500, 23456, 9800, 5600, 9934, 32874]
arzon = min(narhlar)
qimmat = max(narhlar)
jami = sum(narhlar)
print("Eng arzon narh ", arzon, ". Eng qimmati ", qimmat, ". Jami: ", jami)
```

Natija: `Eng arzon narh 5600 . Eng qimmati 32874 . Jami: 116164`

## RO'YXATNI KESISH

Ba'zida ro'yxatning ma'lum bir bo'lagini ajratib olish talab qilinishi mumkin, deylik biz quyidagi cars degan ro'yxatdan birinchi 3 ta elementni ajratib olmoqchimiz, buning uchun biz boshlang'ich va oxirgi indekslarni beramiz:

```python
cars = ['bmw','mercedes benz', 'volvo', 'general motors', 'tesla', 'audi']
my_cars = cars[0:3] # 0-indeskdan boshlab 3 ta element ajratib olamiz
print(my_cars) 
```

Natija: `['bmw', 'mercedes benz', 'volvo']`

**Diqqat!** Python 2-indeksdan bitta avval to'xtaydi. Yuqoridagi misolda ham 0,1,2-elementlar ajratib olindi.

Bu usul bilan ro'yxatning istalgan joyidan bo'lishimiz mumkin:

```python
print(cars[2:5]) # 2-3-4-elementlarni ajratib olamiz (5 kirmaydi)
```

Natija: `['volvo', 'general motors', 'tesla']`

Agar boshlang'ich indeksni bermasangiz, Python avtomat ravishda `0` indeksdan boshlab kesadi. Agar 2-indeksni kiritmasangiz, ro'yxat oxirigacha kesadi:

```python
print(cars[:4]) # Ro'yxat boshidan 4-gacha kesadi (0,1,2,3)
print(cars[2:]) # 2-elementdan boshlab ro'yxat oxirigacha kesib oladi
```

Natija:

`['bmw', 'mercedes benz', 'volvo', 'general motors']`

`['volvo', 'general motors', 'tesla', 'audi']`

## RO'YXATDAN NUSXA OLISH

Dastur davomida biror ro'yxatdan nusxa olish talab qilinishi mumkin. Buning uchun biz tenglik(`=`) belgisidan foydalansak bo'ladimi? Quyidagi misolga e'tibor bering:

```python
sonlar = [1, 2, 3, 4, 5] # donlar degan ro'yxat yaratamiz
sonlar2 = sonlar # sonlar2 degan ro'yxatni sonlar ga tenglaymiz
sonlar2.append(6) # sonlar2 ga 6 sonini qo'shamiz
sonlar2.append(7) # sonlar2 ga 7 sonini qo'shamiz
print("Bu sonlar ro'yxati:", sonlar)
print("Bu sonlar2 ro'yxati:", sonlar2)
```

Natija:

`Bu sonlar ro'yxati: [1, 2, 3, 4, 5, 6, 7]`

`Bu sonlar2 ro'yxati: [1, 2, 3, 4, 5, 6, 7]`

Natija biz kutgandek chiqdimi? Yo'q. Biz 6 va 7 sonlarini `sonlar2` degan ro'yxatga qo'shgan edik, lekin bu ikki son `sonlar` degan asl ro'yxatga ham qo'shilib qoldi.

Demak yuqorida biz `sonlar2=sonlar` deb yozgan komandamiz yangi ro'yxat yaratish o'rniga, ikkala o'zgaruvchini ham bitta ro'yxatga bog'lab (yo'naltirib) qo'ydi. Biz `sonlar` yoki `sonlar2` ustida bajargan amallarimiz aslida bitta ro'yxat ustida bajarilyapti.

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMJGzmHuPgjikKMOl0R%252F-MMJv_JeF1G7uIfp5RRc%252Fimage.png%3Falt%3Dmedia%26token%3D6f5d1db7-57d6-4ef3-983d-5fe640b44435&width=768&dpr=4&quality=100&sign=7db0903e&sv=2)

Ikki o'zgaruvchi, bir ro'yxat

Unda, qanday qilib ro'yxatdan nusxa olamiz? Buning uchun yuoqirdagi ka'bi ro'yxatni kesish usulidan foydalanamiz. Faqatgina, kvadrat qavs ichida ikkala indeksni ham ko'rsatmasdan, bo'sh qoldiramiz:

```python
sonlar = [1, 2, 3, 4, 5] # donlar degan ro'yxat yaratamiz
sonlar2 = sonlar[:] # [:] ro'yxatni to'liq ko'chirib oladi
sonlar2.append(6) # sonlar2 ga 6 sonini qo'shamiz
sonlar2.append(7) # sonlar2 ga 7 sonini qo'shamiz
print("Bu sonlar ro'yxati:", sonlar)
print("Bu sonlar2 ro'yxati:", sonlar2)
```

Natija:

`Bu sonlar ro'yxati: [1, 2, 3, 4, 5]`

`Bu sonlar2 ro'yxati: [1, 2, 3, 4, 5, 6, 7]`

## TUPLES - O'ZGARMAS RO'YXAT

Dastur yaratish davomida o'zgarmas ro'yxat tuzish talab qilinishi mumkin. Pythonda bunday ro'yxatlar **tuples** deb yuritiladi. Tuple ichidagi qiymatlarni bir marta, dastur boshida beriladi va so'ngra o'zgartirib bo'lmaydi. List dan farqli ravishda, Tuple e'lon qilishda kvadrat qavslar `[]` o'rniga oddiy qavslar `()` ishlatiladi:

```python
tomonlar = (20, 30, 55.2)
print(tomonlar)
```

Natija: `(20, 30, 55.2)`

Tuple ichidagi elementlarga huddi ro'yxat elementlariga murojat qilingani kabi murojat qilinaveradi:

```python
toys = ('bus','car','bear','dino','snake','lizard')
print(toys[0])
print(toys[-1])
print(toys[2:5])
```

Natija:

`bus`

`lizard`

`('bear', 'dino', 'snake')`

Keling Tuple ichidagi biror elementning qiymatini o'zgartirib ko'ramiz:

```python
toys = ('bus','car','bear','dino','snake','lizard')
toys[3] = 'dragon'
```

Natija: `**TypeError: 'tuple' object does not support item assignment**`

Demak yuqorida ko'rib turganingiz kabi, bu operatsiya xatolikka olib keldi. Shu kabi ro'yxatdan biror elementni o'chirish yoki yangi element qo'shish ham mumkin emas.

Agar Tuple ga o'zgartirish talab qilinsa, yagona yo'li o'zgarmas ro'yxatni `list()` funktsiyasi yordamida **List** (oddiy ro'yxat) ko'rinishiga keltirib olish, o'zgarishlarni bajarsih va qaytarib `tuple()` funktsiyasi yordamida o'zgarmas ro'yxatga o'tkazish mumkin:

```python
toys = ('bus','car','bear','dino','snake','lizard') # o'zgarmas ro'yxat
toys = list(toys) # o'zgarmas ro'yxatni oddiy ro'yxatga (List) aylantiramiz
# Ro'yxatga o'zgartirishlar kiritamiz
toys.append('dragon')
toys.remove('bus')
toys[1] = 'mcqueen'
toys = tuple(toys) # Ro'yxatni qaytadan o'zgarmas ro'yxatga (Tuple) aylantiramiz
print(toys)
```

Natija: `('car', 'mcqueen', 'dino', 'snake', 'lizard', 'dragon')`

## AMALIYOT

- O'zingizga ma'lum davlatlarning ro'yxatini tuzing va ro'yxatni konsolga chiqaring
    
- Ro'yxatning uzunligini konsolga chiqaring
    
- `sorted()` funktsiyasi yordamida ro'yxatni tartiblangan holda konsolga chiqaring
    
- `sorted()` yordamida ro'yxatni teskari tartibda konsolga chiqaring
    
- Asl ro'yxatni qaytadan konsolga chiqaring
    
- `reverse()` metodi yordamida ro'yxatni ortidan boshlab chiqaring
    
- `sort()` metodi yordamida ro'yxatni avval alifbo bo'yicha, keyin esa alifboga teskari tartibda konsolga chiqaring.
    
- `120` dan `1200` gacha bo'lgan juft sonlar ro'yxatini tuzing
    
- Ro'yxatdagi sonlar yig'indisini hisoblang va konsolga chiqaring
    
- Ro'yxatdagi eng katta va eng kichik son o'rtasidagi ayirmani hisoblang va konsolga chiqaring
    
- Ro'yxatdagi elementlar sonini hisoblang
    
- Ro'yxatning boshidan, o'rtasidan va oxiridan 20 ta qiymatni konsolga chiqaring
    
- `taomlar` degan ro'yxat yarating va ichiga istalgan 5ta taomni kiriting
    
- `nonushta` degan yangi ro'yxatga `taomlar`dan nusxa oling
    
- Yangi ro'yxatda faqat nonushtaga yeyiladigan taomlarni qoldiring, va qo'shimcha 2 ta taom qo'shing
    
- Ikkala ro'yxatni ham (`taomlar` va `nonushta`) konsolga chiqaring
    
- Yuqoridagi nonushta ro'yxatini o'zgarmas ro'yxatga aylantiring va `nonushta[0] = "qaymoq va non"` deb qiymat berib ko'ring.

---

# 6. FOR TAKRORLASH OPERATORI
## `for` BILAN TANISHAMIZ

Dasturlash davomida kodimizning biror qismini bir necha marta takrorlash talab etilishi mumkin. Misol uchun, ro'yxat ichidagi har bir elementni alohida qatordan konsolga chiqarish, yoki bo'lmasa har bir elementni kvdartaga oshirish va hokazo.

Mana shunday vaziyatlarda bizga `**for**` operatori yordam beradi. Dasturlashda bu **tsikl** (**loop**) deb ataladi.

Keling quyidagi misolni ko'ramiz. Bizda mehmonlar ro'yxati bor, biz har bir mehmonning ismini yangi qatordan chiqarmoqchimiz. Buning uchun quyidagi kodni yozamiz:

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(mehmon)
```

Natija:

`Ali`

`Vali`

`Hasan`

`Husan`

`Olim`

Keling, kodni tahlil qilaylik.

- 1-qatorda biz `mehmonlar` degan ro'yxat yaratdik va uni mehmonlarning ismi bilan to'ldirdik.
    
- 2-qatorda `for` tsiklini bohladik. Bu qator Pythonga `mehmonlar` degan ro'yxatdan har bir elementini olib uni yangi, `mehmon` degan o'zgaruvchiga yuklashni buyuryapti (_o'zgaruvchiga istalgan nom berishingiz mumkin. Biz tushunarli bo'lishi uchun_ `mehmon` _deb atadik_)
    
- 3-qatorda biz `mehmon` degan o'zgaruvchining qiymatini konsolga chiqardik. Bu tsikl to `mehmonlar` ro'yxatida elementlar tugagunga qadar takrorlanadi.
    

"**For**" so'zi ingliz tilidan "**uchun**" deb tarjima qilinadi.

Yuqoridagi kodni oddiy tilga tarjima qilsak _"Mehmonlar ro'yxatidagi har bir mehmon_ _**uchun**_ _uning ismini konsolga chiqar"_ degan ma'noni beradi.

## `for` QANDAY ISHLAYDI

Keling yana bir misol ko'raylik.

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(f"Hurmatli {mehmon}, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz")
    print("Hurmat bilan, Palonchiyevlar oilasi")
```

Natija:

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMPQyZT5FQp6KY-8-aY%252Fimage.png%3Falt%3Dmedia%26token%3D0c8954a5-7c1b-4d45-a941-4e4ecbdae325&width=768&dpr=4&quality=100&sign=8c69d697&sv=2)

Yuqoridagi kodda 2-qator bu tsikl boshi deyiladi. Aynan shu qator kodimiz nech marta takrorlanishini aniqlaydi. Bizning holatimizda tsikl `mehmonlar` ro'yxati ichidagi elementlar tugagunga qadar takrorlanadi. Tsikl boshlanishi ikki nuqta (`:`) bilan tugaydi. Undan keyingi 3 va 4-qatorlar bu tsiklning badani deyiladi.

Tsikl badani surilish (indentation) bilan ajratiladi, ya'ni tsiklning takrorlanuvchi qismi asosiy koddan bir muncha o'ngroqqa surilgan bo'ladi. Agar biz mana shu surilishni tark qilsak kodimiz xato beradi:

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
print(f"Hurmatli {mehmon}, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz")
print("Hurmat bilan, Palonchiyevlar oilasi\n")
```

Natija: `**IndentationError: expected an indented block**`

Ko'rib turganingizdek for dan keyingi qatorni o'ngga surmaganimiz uchun **indentation error** (surishda xatolik) degan xabarni oldik.

Shunigdek, ko'pchilik yo'l qo'yadigan yana bir xato, qo'shimcha qatorlarni surish esdan chiqishi:

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(f"Hurmatli {mehmon}, sizni 20 Dekabr kuni nahorga oshga taklif qilamiz")
print("Hurmat bilan, Palonchiyevlar oilasi\n")
```

Natija:

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMPUnWYBNdp6X7_11Mx%252Fimage.png%3Falt%3Dmedia%26token%3D45393130-8c29-421c-88bc-d567bdf87433&width=768&dpr=4&quality=100&sign=2b9358da&sv=2)

Yuqoridagi kodimizda 4-qatorni o'ngga surmaganimiz uchun, Python bu qatorni tsikl tashqarisida deb qabul qildi va faqatgina 1 marta, tsikl tugaganidan so'ng bajardi.

Huddi shu kabi agar takrorlanishi kerak bo'magan kodni tsikldan so'ng o'ngga surib qo'ysak Python bu qatorni tsiklning tarkibida deb hisoblab, qayta-qayta bajaradi:

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(mehmon)
    
    print(mehmonlar) # bu qator tsikl tashqarisida bo'lishi kerak edi
```

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMPV_aHRkWeJtIwqwGW%252Fimage.png%3Falt%3Dmedia%26token%3D6c4fe1f9-8225-41d4-be8b-8dd62a148409&width=768&dpr=4&quality=100&sign=67829a93&sv=2)

Yuoqirdagi misolda 5-qator o'ngga surilib qolgani uchun Python bu qatorni ham bir necha bor takrorlab, konsolga chiqardi. To'g'ri kod quyidagicha bo'ladi:

```python
mehmonlar = ['Ali','Vali','Hasan', 'Husan','Olim']
for mehmon in mehmonlar:
    print(mehmon)
    
print(mehmonlar)
```

## `for` YORDAMIDA SONLI RO'YXATLAR BILAN ISHLASH

Keling quyidagi misolni ko'ramiz

```python
sonlar = list(range(1,11))
for son in sonlar:
    print(f"{son} ning kvadrati {son**2} ga teng")
```

Natija:

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMPZMvGrHyynJZ4WQr7%252Fimage.png%3Falt%3Dmedia%26token%3D2e0ccfce-f6a2-4ca3-96e7-7a5861fd30c3&width=768&dpr=4&quality=100&sign=be25243e&sv=2)

`for` yordamida yangi ro'yxat ham shakllantirish mumkin:

```python
sonlar = list(range(11)) # 1 dan 10 gacha sonlar ro'yxatini yaratamiz
sonlar_kvadrati =[] # bo'sh ro'yxat yaratamiz
for son in sonlar:  # sonlar dagi har bir son uchun
    sonlar_kvadrati.append(son**2) # uning kv.ni hisoblab, sonlar_kvadrati ga yuklaymiz

print(sonlar)
print(sonlar_kvadrati)
```

Natija:

`[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]`

`[0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]`

## `for` va `input()`

for operatori va input() funktsiyasini jamlab, ro'yxatni foydalanuvchidan olingan qiymatlar bilan to'ldirish mumkin:

```python
dostlar = [] # bo'sh ro'yxat
print("5 ta eng yaqin do'stingiz kim?")
for n in range(5): # n bu yerda 0 dan 4 gacha qiymatlar oladi
    dostlar.append(input(f"{n+1}-do'stingizning ismini kiriting: "))
print(dostlar)
```

Natija:

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPaWvgJ__zmMdi1b7y%252F-MMT-gtwhVd0_teSQ415%252Fimage.png%3Falt%3Dmedia%26token%3Dc78b15e7-f2c9-4e22-806b-602dbee06a8c&width=768&dpr=4&quality=100&sign=5630f24a&sv=2)

Kodni tahlil qilamiz:

- 1-qatorda bo'sh `dostlar` ro'yxatini yaratdik
    
- 2-qatorda ekranga `"5 ta eng yaqin do'stingiz kim?"` degan xabarni chiqardik
    
- 3-qatorda tsiklni boshladik. `range(5)` funktsiyasi 0 dan 5 gacha sonlar ketma-ketligini yaratadi `(0,1,2,3,4)` tsikl esa `n` shularning har biriga teng bo'lib chiqquncha davom etadi.
    
- 4-qatorda tsikl badani kelgan. Bu yerda biz foydalanuvchidan `n+1` do'stingizni kiriting deb so'radik. Nima uchun `n+1` (`n` emas)? Sababi `n` 0 dan 4 gacha qiymatlarni oladi, foydalanuvchiga tushunarli bo'lishi uchun esa biz "0-do'stingizni ismini kiriting:" deb emas, balki `n+1` ya'ni 1-ismni kiriting deb murojat qilyapmiz.
    
- 5-qatorda shakllangan ro'yxatni konsolga chiqardik.
    

`**for**` tsikli har qanday dasturlash tilining eng muhim qismlaridan hisoblanadi va biz bu operatoraga hali takror-takror qaytamiz.

## AMALIYOT

- Kamida 5 elementdan iborat ismlar degan ro'yxat tuzing, va ro'yxatdagi har bir ismga takrorlanuvchi xabar yozing
    
- Yuoqirdagi tsikl tugaganidan so'ng, ekranga "Kod `n` marta takrorlandi" degan xabarni chiqaring (`n` o'rniga kod necha marta takrorlanganini yozing)
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMP_FTr--cIleoE1pUk%252Fimage.png%3Falt%3Dmedia%26token%3De6ff5313-10db-4dd2-81f5-ca42284f0218&width=768&dpr=4&quality=100&sign=b3f30c4e&sv=2)

Kutilgan natija

- 10 dan 100 gacha bo'lgan toq sonlar ro'yxatini tuzing. Ro'yxatning xar bir elementining kubini yangi qatordan konsolga chiqaring.
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMPNxgNwPmiIwnqKZ-n%252F-MMP_u9IVOIxvkgaD4R7%252Fimage.png%3Falt%3Dmedia%26token%3D26b4f01a-1487-4ef4-a1b4-b15a8ee0ec61&width=768&dpr=4&quality=100&sign=2e419983&sv=2)

- Foydalanuvchidan 5 ta eng sevimli kinolarini kiritshni so'rang, va `kinolar` degan ro'yxatga saqlab oling. Natijani konsolga chiqaring.
    
- Foydalanuvchidan bugun nechta odam bilan uchrashganini (suhbatlashganini) so'rang, va har bir suhbatlashgan odamning ismini birma-bir so'rab ro'yxatga yozing. Ro'yxatni konsolga chiqaring.
    

![](https://python.sariq.dev/~gitbook/image?url=https%3A%2F%2F1283015017-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-MGbkqs1tROquIT6oqUs%252F-MMT2VK6SaNLN7fUnjkD%252F-MMT5AHMlvPnOvBAj5Cg%252Fezgif-3-cbc37adef5e6.gif%3Falt%3Dmedia%26token%3D7b016282-f3fc-4806-b740-47d1a3ea2161&width=768&dpr=4&quality=100&sign=a74e7c58&sv=2)
