---
type: lesson
tags:
  - web
  - internet
  - domen
  - url
  - hosting
  - ip
created: 2026-06-04 21:20
---
# 01. Internet

- **Internet** - malumotlar almashish tarmog'i
- **Internet** - ko'plab kompyuterlar ulangan tarmoq

## ISP - internet service provider

![[Pasted image 20260604212545.png]]

---

# 02. Web ilovalarning arxitekturasi

![[Pasted image 20260604213652.png]]

---

# 03. Protokollar

**Protokol** - malumotlarni formatlash va qayta ishlash uchun standart qoidalar to'plamidir.

- `IP/TSCP` - Transmission Control Protocol
- `HTTP` - Hypertext Transfer Protocol
- `TLS` - Transport Layer Security

![[Pasted image 20260604214941.png]]

Misol: Brauzer orqali google.com ga kiryapsiz
## 1-qadam: HTTP

Siz brauzerga yozasiz:

```text
https://google.com
```

Brauzer HTTP so'rov yaratadi:

```http
GET / HTTP/1.1
Host: google.com
```

Rasmda:

```text
Client
┌──────┐
│ HTTP │
└──────┘
```

qatlamida hosil bo'ladi.

---

## 2-qadam: TLS

HTTP ma'lumot TLS ga uzatiladi.

TLS aytadi:

> "Men buni shifrlayman."

Masalan:

```http
GET / HTTP/1.1
Host: google.com
```

quyidagiga o'xshash ko'rinishga keladi:

```text
A9F7C2E1...
8D34A1B5...
```

Rasmda:

```text
HTTP
  ↓
TLS
```

---

## 3-qadam: TCP

Shifrlangan ma'lumot TCP ga tushadi.

TCP vazifasi:

- Paketlarga bo'lish
    
- Tartibni saqlash
    
- Yetib borgani tekshirish

Masalan:

```text
Packet #1
Packet #2
Packet #3
```

Rasmda:

```text
TLS
 ↓
TCP
```

---

## 4-qadam: IP

TCP paketlarini IP qayerga yuborishni aniqlaydi.

Masalan:

```text
Destination IP:
142.250.185.78
```

Rasmda:

```text
TCP
 ↓
IP
```

---

## 5-qadam: Internet

Endi paketlar internet bo'ylab harakat qiladi.

Rasmning markazidagi bulut:

```text
Internet
```

aslida:

- Routerlar
    
- Switchlar
    
- ISP lar
    
- Magistral tarmoqlar

to'plamidir.

IP qatlamining asosiy vazifasi:

```text
"Bu paketni qayerga yuborish kerak?"
```

---

## Server tomonda nima bo'ladi?

Paket serverga yetib keladi.

Endi jarayon teskarisiga ishlaydi.

---

## IP

Server paketni qabul qiladi:

```text
IP
```

---

## TCP

TCP paketlarni yig'adi:

```text
Packet #1
Packet #2
Packet #3
```

↓

```text
Bitta ma'lumot
```

hosil qiladi.

---

## TLS

TLS paketlarni ochadi (decrypt).

Masalan:

```text
A9F7C2E1...
```

↓

```http
GET / HTTP/1.1
Host: google.com
```

---

## HTTP

HTTP qatlamiga tayyor request beriladi:

```http
GET /
```

Web server (Nginx, Apache, Caddy va hokazo) uni qayta ishlaydi.

Masalan:

```html
<html>
Hello World
</html>
```

javob tayyorlaydi.

---

## Rasmda ko'k punktir chiziqlar nimani bildiradi?

Ko'pchilik aynan shu joyni noto'g'ri tushunadi.

Ko'k chiziqlar:

```text
HTTP  <------> HTTP
TLS   <------> TLS
TCP   <------> TCP
```

degan ma'noni beradi.

Ya'ni mantiqan:

- Client HTTP server HTTP bilan gaplashadi.
    
- Client TLS server TLS bilan gaplashadi.
    
- Client TCP server TCP bilan gaplashadi.
    

Lekin fizik jihatdan ma'lumot to'g'ridan-to'g'ri HTTP dan HTTP ga bormaydi.

Aslida:

```text
HTTP
 ↓
TLS
 ↓
TCP
 ↓
IP
 ↓
Internet
 ↓
IP
 ↓
TCP
 ↓
TLS
 ↓
HTTP
```

yo'lini bosib o'tadi.

---

## Backend dasturchi uchun amaliy ko'rinish

Siz Laravel yoki PHP da:

```php
Route::get('/', function () {
    return 'Hello';
});
```

yozganingizda faqat:

```text
HTTP
```

qatlami bilan ishlaysiz.

Lekin foydalanuvchi request yuborganda uning ostida avtomatik ravishda:

```text
HTTP
 ↓
TLS
 ↓
TCP
 ↓
IP
 ↓
Internet
 ↓
IP
 ↓
TCP
 ↓
TLS
 ↓
HTTP
```

jarayoni sodir bo'ladi.

Shuning uchun:

- **404** → HTTP muammosi
    
- **SSL certificate error** → TLS muammosi
    
- **Connection refused** → TCP muammosi
    
- **No route to host** → IP/tarmoq muammosi

---



degan xatolar turli qatlamlarga tegishli bo'ladi.

Rasm aslida internetdagi deyarli har bir HTTPS requestning ichki sayohatini ko'rsatmoqda.

---

# 04. IP, Domen, URL, Hosting

## 1) IP - internetdagi qurilmaning noyob manzili

![[Pasted image 20260604223229.png]]

IPv4:

```text
142.250.185.78
```

yoki IPv6:

```text
2404:6800:4009:81c::200e
```

Internetdagi har bir serverning IP manzili bo'ladi.

Masalan:

```text
Google serveri
↓
142.250.185.78
```

Kompyuterlar bir-biri bilan aynan IP orqali gaplashadi.

Misol:

```text
Sizning kompyuteringiz
192.168.1.5

↓ Internet ↓

Server
142.250.185.78
```

Muammo

Odamlar IP ni eslab qolishi qiyin:

```text
142.250.185.78
172.217.168.78
157.240.18.35
```

Shu sabab domenlar paydo bo'lgan.

## 2) Domen (Domain Name)

![[Pasted image 20260604224700.png]]

Domen — IP manzil uchun inson o'qiy oladigan nom.

Masalan:

```text
google.com
youtube.com
github.com
```

Aslida:

```text
google.com
↓
142.250.185.78
```

### DNS nima qiladi?

Brauzer:

```text
google.com
```

ko'radi.

DNS serverdan so'raydi:

```text
google.com qaysi IP?
```

DNS javob beradi:

```text
142.250.185.78
```

Shundan keyin ulanish boshlanadi.

### Domen tuzilishi

Misol:

```text
blog.example.com
```

Qismlari:

```text
blog      → Subdomain
example   → Domain
com       → TLD
```

### TLD (Top Level Domain)

Masalan:

```text
.com
.net
.org
.dev
.uz
```

## 3) URL (Uniform Resource Locator)

![[Pasted image 20260604224736.png]]

URL — internetdagi aniq resurs manzili.

Misol:

```text
https://blog.example.com/posts/1
```

Qismlarga ajratamiz:

```text
https://blog.example.com/posts/1
│       │                │
│       │                └─ Path
│       │
│       └─ Domain
│
└─ Protocol
```

### URL tarkibi

```text
https://blog.example.com/posts/1?sort=desc#comments
```

| Qism     | Qiymat           |
| -------- | ---------------- |
| Protocol | https            |
| Domain   | blog.example.com |
| Path     | /posts/1         |
| Query    | sort=desc        |
| Fragment | comments         |

### Misol

```text
https://youtube.com/watch?v=abc123
```

Bu yerda:

```text
https      → TLS bilan HTTP
youtube.com → domen
/watch      → resurs
v=abc123    → parametr
```

## 4) Hosting

![[Pasted image 20260604224811.png]]

Hosting — sayt fayllari saqlanadigan server.

Masalan sizda Laravel loyiha bor:

```text
app/
routes/
storage/
vendor/
```

Ularni biror serverga joylashtirasiz.

O'sha server hosting hisoblanadi.

### Oddiy misol

Tasavvur qiling:

```text
Uy = Hosting
Uy manzili = IP
Uy nomi = Domen
To'liq manzil = URL
```

Masalan:

```text
Hosting
↓
Ubuntu Server
↓
IP
185.100.87.10
↓
Domen
example.com
↓
URL
https://example.com/blog/post-1
```

## Hammasini bog'laymiz

Foydalanuvchi brauzerga yozadi:

```text
https://example.com/about
```

### 1-qadam

Brauzer URL ni tahlil qiladi:

```text
Protocol: HTTPS
Domain: example.com
Path: /about
```

### 2-qadam

DNS dan so'raydi:

```text
example.com → ?
```

Javob:

```text
185.100.87.10
```

### 3-qadam

Serverga ulanadi:

```text
185.100.87.10:443
```

### 4-qadam

Hostingdagi web server (Nginx, Apache va hokazo) requestni qabul qiladi.

### 5-qadam

Laravel ishlaydi:

```php
Route::get('/about', function () {
    return view('about');
});
```

### 6-qadam

HTML javob qaytadi.

## Bir jumlada

| Tushuncha | Vazifasi                          |
| --------- | --------------------------------- |
| IP        | Serverning haqiqiy tarmoq manzili |
| Domen     | IP uchun qulay nom                |
| URL       | Saytdagi aniq resurs manzili      |
| Hosting   | Sayt fayllari joylashgan server   |

Masalan:

```text
URL:
https://blog.example.com/posts/1

Protocol : https
Domain   : blog.example.com
IP       : 185.100.87.10
Hosting  : shu IP dagi server
```

Shu 4 tushunchani tushunsangiz, keyingi bosqichda **DNS, nameserver, registrar, reverse proxy, virtual host, CDN va load balancer** mavzularini o'rganish ancha osonlashadi.

---

# 05. DNS

![[Pasted image 20260604225138.png]]

...