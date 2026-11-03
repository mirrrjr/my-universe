Reja:
- Arifmetik operatorlar
- Özlaştiriş operatorlari
- Increment va Decrement operatorlari
- Taqqoslaş operatorlari
- Ternary va Strinig operatorlari
- Mantiqiy operatorlar


![[Pasted image 20261031185616.png]]

## Arifmetik operatorlar

![[Pasted image 20261031185857.png]]

![[Pasted image 20261031190008.png]]

## Özlaştirish operatorlari

![[Pasted image 20261031190737.png]]

```php
$y = 100;
$x = $y;
// $x özgaruvçiga $y ning qiymatini beriş

$x += $y; // yoki $x = $x + $y
// $x özgaruvçining qiymatiga $y ni qiymatini qöşiş

$x -= $y; // yoki $x = $x - $y

$x *= $y; // yoki $x = $x * $y

$x /= $y; // yoki $x = $x / $y

$x %= $y; // yoki $x = $x % $y

# String qiymatlarini bir biriga qöşiş
$a = "Assalomu alaykum!";
$a .= " Xuş kelibsiz"; // $a = $a . " Xuş kelibsiz"
echo $a; // Assalomu alaykum! Xuş kelibsiz

$a = 'a';
$b = 'b';
$a .= $b .= "foo";
```