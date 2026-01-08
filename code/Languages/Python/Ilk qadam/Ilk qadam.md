1. Kerakli dasturlar
2. `Hello World`
3. `print`, `syntax` va arifmetik amallar

# 1. Kerakli dasturlar

> Python

Avvalo agar biz Windows OS ishlayotgan bo'lsak python dasturlash tilini o'rnatib olishimiz kerak, buning uchun:
1. Rasmiy python web saytining `downloads` bo'limiga kiramiz: https://www.python.org/downloads/
2. Yuklab olamiz va `install` qilamiz

>IDE

Endi `python` kodini yozish uchhun maxsus matin muxarririni yuklab olishimiz kerak, maslan VS Code, VS Codium, Atom, Sublime Text va b...

Darslarda biz VS Codium dasturlash muhitidan foydalanamiz. Yuklab olish uchun link: https://vscodium.com/

# 2. Hello World
Kerakli dasturlarimiz tayyor, endi dastlabki kodimizni yozsak bo'ladi, bunik uchun sistemaning biror joyiga maxsus katalog(papka) yaratib olamiz va uni VS Coium orqali ochamiz.
Katalog ichida `app.py` nomli fayl yaratamiz va quyidagilarni yozamiz:

```python
# fayl nomi - app.py

print("Hello World")
```

Endi dasturimiz natijasini ko'rish uchun `terminal`-ni ochib quyidagilarni yozamiz:
```cmd
C:\your\script\folder\> py app.y
Hello World
```

## AMALIYOT

Matn muharririda quyidagi kodlarni yozib, bajarib ko'ring. Siz kutgan natijalar chiqdimi?

```
print('Assalom alaykum')
```

```
print(Hayrli tong!)
```

```
print(2+4*2)
```

```
print(19/5)
```

```
print(2**4)
```

# 3. Print(), Syntax va arifmetik amallar
## PRINT()

Avvalgi darsimizning yakunida bir nechta kodlarni pythonda bajarib ko'rishni vazifa qilgan edik. Keling shu kodlarning natijasini ko'ramiz:

```python
print("Assalom alaykum")
```

Natija: `Assalom alaykum`

Kutilganidek, yuqoridagi kod Assalom alaykum matnini konsolda ko'rsatdi. Keling endi keyingi kodni kiritamiz:

```python
print(Hayrli tong!)
```

Natija: `**SyntaxError: invalid syntax**`

Bu safar esa `Hayrli tong!` yozuvi o'rniga, `Syntax Error` (sinteksda xatolik) xabari chiqdi. Xatolik qayerda?

Avval aytganimizdek, `print()` funktsiyasi matn yoki ifodalarni konsolga chiqarish vazifasini bajaradi. Lekin bu funktsiya to'g'ri ishlashi uchun bir nechta qoidalarga amal qilish lozim. Jumladan, agar konsolga matn chiqarmoqchi bo'lsak, matnimiz albatta qo'shtirnoq (`" "`) yoki birtirnoq (`' '`) orasida yozlishi kerak. Demak `Hayrli tong!` so'zini konsolda chiqarish uchun to'g'ri kod:

```python
print("Hayrli tong!")
```

yoki

```python
print('Hayrli tong!')
```

bo'ladi.

Natija: `Hayrli tong!`

Qo'shitrnoq yoki birtirnoq ishlatishning afzalliklaridan biri, agar siz chiqarmoqchi bo'lgan matnda ikkovidan biri qatnashgan bo'lsa, `print()` funktsyasida ikkinchisidan foydalanasiz. Keling quyidagi misolni ko'ramiz:

```python
print('Men "Dell" markasidagi noutbuk sotib oldim')
```

Natija: `Men "Dell" markasidagi noutbuk sotib oldim`

Yuqoridagi matnda `"Dell"` so'zi qo'shtirnoq ichida eda. Bu matnni konsolga chiqarish uchun esa, `print()`funktsyasi ichida matnni birtirnoq ichiga oldik.

Agar matnni bir necha qatorga bo'lib yozish talab qilinsa, uchtalik qo'shtirnoq`(""" """)`yoki birtirnoqdan `(''' ''')`foydalanish mumkin:

```python
print("""Odami ersang, demagil odami,
Oniki, yo'q xalq g'amidin g'ami""")
```

Natija:

`Odami ersang, demagil odami,`

`Oniki, yo'q xalq g'amidin g'ami`

Qatorga bo'lishning yana bir usuli, qator so'nggida `\n` belgisini qo'yish.

```python
print("Odami ersang, demagil odami,\nOniki, yo'q xalq g'amidin g'ami")
```

Natija:

`Odami ersang, demagil odami,`

`Oniki, yo'q xalq g'amidin g'ami`

Yuoqridagi matnni birtirnoq orqali ham konsolga chiqarish mumkinmi? Matndagi `yo'q`, `g'am` so'zlaridagi birtirnoqlar bunga to'sqinlik qilmaydimi? **Qiladi.**

Buning oldini olish uchun esa matndagi birtirnoq belgisidan avval `\` belgisini qo'yish lozim.

```python
print('Odami ersang, demagil odami, \nOniki, yo\'q xalq g\'amidin g\'ami')
```

Natija:

`Odami ersang, demagil odami,`

`Oniki, yo'q xalq g'amidin g'ami`

Yuqoridagi kodga e'tibor bergan bo'lsangiz "yo'q" so'zi `yo\'q` ko'rinishida "g'am" so'zi esa `g\'am` ko'rinishida yozilgan. Umuman olganda `\` belgisi har qanday mahsus belgi oldidan qo'yiladi.

Agar yuqordagi kodimizda `\` belgisini ishlatmaganimizda natija qanday bo'lar edi?

```python
print('Odami ersang, demagil odami,\nOniki, yo'q xalq g'amidin g'ami')
```

Natija: `**SyntaxError: invalid syntax**`

Keling shu o'rinda **Syntax Error** (sinteksda xatolik) haqida ham gaplashaylik.

## SINTEKS XATOLIK (SYNTAX ERROR)

Har bir tilda orfografik va grammatik qoidalar bo'lgani kabi, dasturlash tillarining ham o'ziga yarasha qonun-qoidalari bor. Bu qoidalar to'plami **sinteks (syntax)** deb ataladi. **Sinteks xatolik** (Syntax Error) deb esa shu qoidalarning buzilishiga aytiladi.

Misol uchun keraksiz joyda qo'yilgan nuqta, vergul yoki bo'sh joy, shuningdek ma'lum funktsiyalar nomini xato yozish (`print()` o'rniga `prit()`), ochilmay yoki yopilmay qolgan qavs, noo'rin bo'shliq, qolib ketgan kalit so'z (keyword) kabilar ham Syntax Error hisoblanadi.

Syntax Error eng ko'p uchraydigan xatolik bo'lib, Python bunday xatolik bor dasturlarni **bajarmaydi**.

Biz darslarimiz davomida turli sinteks qoidalar haqida o'z o'rnida yana to'xtalamiz.

## ARIFMETIK AMALLAR

Amaliyotga qaytamiz, `print()` funktsiyasi nafaqat matn, balki turli ifodalarni ham konsolga chiqaradi.

Keling quyidagi kodlarni ham bajaramiz:

```python
print(2+4*2)
```

Natija: `10`

Python arifmetik amallarni bajarishda Matematika qoidalariga amal qiladi:

- Qavs ichidagi amallar qavs ortidagilardan avval bajariladi
    
- Darajaga oshirish (ildiz chiqarish) ko'paytirish va bo'lishdan avval bajariladi
    
- Ko'paytirish va bo'lish, qo'shish va ayirishdan avval bajariladi
    
- Boshqa holatlarda ifodalar chapdan o'ngga qarab bajariladi
    

Yuqoridagi misolda ham avval ko'paytirish (`4*2=8`), keyin esa qo'shish amali (`2+8=10`) bajarildi.

```python
print(19/5)
```

Natija: `3.8`

Ko'rib turganingizdek, `/` belgisi bo'lish amalini bajaradi va natija har doim o'nlik son ko'rinishida bo'ladi (garchi bo'lish amali natijasida butun son xosil bo'lsa ham):

```python
print(20/5)
```

Natija: `4.0`

Bo'lish amalidan butun son ko'rinishidagi natija olish uchun `//` belgisidan foydalanamiz:

```python
print(16//4)
```

Natija: `4`

```python
print(10//3)
```

Natija: `3`

Amaliyotimizdagi keyingi kodni ham bajaraylik:

```python
print(2**4)
```

Natija: `16`

Yuqoridagi `**` belgisi darajaga oshirishni anglatadi, ya'ni `2**4` ifodasi 2 ning 4-darajasini beradi.

Pythonda oddiy arifmetik amallar quyidagi jadvalda berilgan.


| Operator | Tavsif                         | Misol       |
| -------- | ------------------------------ | ----------- |
| +        | Qo'shish                       | 5+6=11      |
| -        | Ayirish                        | 5-6=-1      |
| *        | Ko'paytirish                   | 5*6=30      |
| /        | Bo'lish                        | 5/6=0.83333 |
| //       | Bo'lish va butun qismini olish | 5/6=0       |
| **       | Exponenta (daraja,ildiz)       | 5**6=15625  |
| %        | Bo'linmaning qoldig'ini olish  | 15%6=3      |


`print()` yordamida matn va ifodalarni jamlab chiqarish ham mumkin. Buning uchun har bir ifoda va matn vergul (`,`) bilan ajratiladi:

```python
print("To'qqizning kvadrati", 9**2, "ga teng")
```

Natija: `To'qqizning kvadrati 81 ga teng`

```python
print('3x3=',3*3)
```

Natija:`3x3= 9`

## IZOHLAR (COMMENTS)

Yaxshi dasturchilarning odatlaridan biri har qanday kodni izohlar bilan tushuntirib ketish. Izohlar kelajakda o'zimiz uchun ham, boshqalar uchun ham dasturimiz qanday ishlashini tushunishda yordam beradi.

Quyidagi ikki misolga e'tibor bering, va ulardan qay biri tushunarliroq ekanini solishtiring

```python
print(2*5*3.14159)
```

```python
#Radiusi 5 ga teng bo'lgan aylananing uzunligi quyidagicha hisoblanadi
print(2*5*3.14159)
```

Yuqoridagi misolda `#` belgisidan keyin yozilgan matn **izoh** (**comment**) deyiladi.

Izoh alohida qatorda yoki qator oxiridan ham yozilishi mumkin. Python `#` dan keyingi har qanday matnni (qator oxirigacha) e'tiborsiz qoldiaradi. `#` dan keyin yozligan kodlar ham bajarilmaydi:

```python
print("Assalom alaykum!") # Bu matn konsolda chiqadi
#Keyingi qator esa bajarilmaydi
#print("Mening ismim Anvar")
```

Natija: `Assalom alaykum!`

## AMALIYOT

Quyidagi matnni aynan shunday ko'rinishda konsolda chiqaring:

`"Nexia", "Tico", 'Damas' ko'rganlar qilar havas`

Quyidagi misollarga yechimni Pythonda chiqaring. Har bir misoldan avval misol matnini izoh ko'rinishida yozing:

1. 5 ning 4-darajasini toping
    
2. 22 ni 4 ga bo'lganda qancha qoldiq qoladi?
    
3. Tomonlari 125 ga teng kvadratning yuzi va perimetrini toping
    
4. Diametri 12 ga teng bo'lgan doiraning yuzini toping (π=3.14 deb oling)
    
5. Katetlari 6 va 7 bo'lgan to'g'ri burchakli uchburchakning gipotenuzasini toping ([Pifagor teoremasidan](https://fayllar.org/pifagor-teoremasi-va-uning-turli-hil-isbotlari-mavzusida-tajer.html) foydalaning)