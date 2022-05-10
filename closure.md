# Closure

[Kembali](README.md)

## Latar belakang topik

Terkadang kita ingin menulis dan memanggil fungsi dengan mudah, terutama dalam fungsi callable, dimana kita ingin menuliskan fungsi secara langsung dalam parameternya, bukan menuliskan nama fungsi tersebut dalam parameter. Untuk mempermudahkan penulisan tersebut, kita dapat menggunakan closure pada parameter callable. Selain itu, variabel yang dapat digunakan untuk merujuk ke sebuah fungsi juga semakin mendukung penggunaan closure.

## Konsep-konsep

Closure atau anonymous function merupakan fungsi yang tidak memiliki nama. Untuk memanggilnya secara individu, kita dapat menggunakan variabel yang merujuk pada closure tersebut. Seperti fungsi pada umumnya, closure juga dapat memiliki parameter dan me-return sebuah nilai. Pada umumnya, closure digunakan sebagai nilai parameter callable. 

## Penerapan Closure

### Closure tanpa Parameter

Cara pertama dalam penggunaan closure adalah dengan menggunakan variable yang merujuk pada closure tanpa parameter

```php
<?php

$print_message1 = function(){
  echo "Hello!\n";
};
$print_message1();

?>
```

Pada tahap pertama, diperlukan sebuah variable yang merujuk pada closure

```
$print_message1 = function(){
  echo "Hello!\n";
};
```

Kemudian dilakukan pemanggilan variable tadi diikuti dengant tanda kurung

```
$print_message1();
```

Pada cara ini, output yang dihasilkan adalah `Hello!`.

### Closure dengan Parameter

Cara selanjutnya adalah dengam menggunakan variable yang merujuk kepada closure dengan parameter.
```php
<?php

$get_message = function($name){
  return "Hello, " . $name . "!\n";
};
echo $get_message("Steven");

?>
```
Sama seperti sebelumnya, variable dibuat terlebih dahulu yang merujuk pada closure dengan parameter dan return value
```
$get_message = function($name){
  return "Hello, " . $name . "!\n";
};
```

Kemudian dilakukan pemanggilan variable tadi diikuti dengan parameter yang diinputkan
```
echo $get_message("Steven");
```

Pada cara ini, output yang dihasilkan adalah `Hello, Steven!`.

### Closure dengan Keyword Use

Cara lain dalam penggunaan closure adalah dengan menggunakan metode keyword use. .  
```php
<?php

$message = "Hello!";
$print_message2 = function() use ($message){
  echo $message;
  echo "\n";
};

$print_message2();

?>
```
Sebuah variable dibuat terlebih dahulu agar dapat digunakan oleh closure
```
$message = "Hello!";
```

Selanjutnya, dibuatlah sebuah variable yang merujuk kepada closure tanpa parameter dengan keyword use agar closure dapat menggunakan variable di luar closure
```
$print_message2 = function() use ($message){
  echo $message;
  echo "\n";
};
```

Setelah itu, seperti biasa dilakukan pemanggilan variable diikuti dengan tanda kurung
```
$print_message2();
```

Pada cara ini, output yang dihasilkan adalah `Hello!`.

### Closure dengan Array Walk

Closure juga dapat digunakan dengan fungsi `array_walk`. Fungsi array_walk merupakan fungsi yang menjalankan setiap elemen array dalam fungsi yang ditentukan pengguna. Value dan key array adalah parameter dalam fungsi dan dalam pengimplementasian array_walk, value dan key tidak dapat diubah urutannya, namun untuk mengganti nama variabelnya diperbolehkan. 

#### Tanpa Menggunakan Variable

Closure dapat digunakan dengan fungsi array walk secara langsung tanpa menggunakan variable
```php
<?php

$fruits = ["a" => "Apel", "b" => "Belimbing", "c" => "Cerry"];

array_walk($fruits, function($value, $key) {
 echo $key . ". "  . $value . "\n";
});

?>
```

Pada cara ini, langkah pertama adalah melakukan instansiasi associative array (array dengan named key) `fruits`
```
$fruits = ["a" => "Apel", "b" => "Belimbing", "c" => "Cerry"];
```

Lalu dilakukan pemanggilan fungsi `arraw_walk` dengan parameter associative array sebelumnya yaitu `fruits` dan closure
```
array_walk($fruits, function($value, $key) {
 echo $key . ". "  . $value . "\n";
});
```

Pada cara ini, output yang dihasilkan adalah sebagai berikut.
```
a. Apel
b. Belimbing
c. Cerry
```

#### Dengan Variable

Walaupun kita dapat menulis closure secara langsung dalam parameter fungsi array_walk, kita juga dapat membuat variabel yang menunjuk pada closure dan memanggil nama variabel tersebut dari parameter fungsi array_walk.

```php
<?php

$fruits = ["a" => "Apel", "b" => "Belimbing", "c" => "Cerry"];

$print_fruits = function($value, $key) {
 echo $key . ". "  . $value . "\n";
};

array_walk($fruits, $print_fruits);

?>
```

Output yang dihasilkan akan sama seperti sebelumnya

### Menggunakan Parameter Lain

Selain value dan key, kita juga dapat passing parameter lain, seperti associative array fruits. Namun, urutannya harus tetap, value diletakkan di awal dan diikuti dengan key.

```php
<?php

$fruits = ["a" => "Apel", "b" => "Belimbing", "c" => "Cerry"];

array_walk($fruits, function($value, $key, $fruits) {
 echo $key . ". "  . $value . "\n";
 var_dump($fruits);
}, $fruits);

?>
```

Pada cara ini, output yang dihasilkan adalah sebagai berikut.

```
a. Apel
array(3) {
  ["a"]=>
  string(4) "Apel"
  ["b"]=>
  string(9) "Belimbing"
  ["c"]=>
  string(5) "Cerry"
}
b. Belimbing
array(3) {
  ["a"]=>
  string(4) "Apel"
  ["b"]=>
  string(9) "Belimbing"
  ["c"]=>
  string(5) "Cerry"
}
c. Cerry
array(3) {
  ["a"]=>
  string(4) "Apel"
  ["b"]=>
  string(9) "Belimbing"
  ["c"]=>
  string(5) "Cerry"
}
```
