# object-oriented-php-1

## 1. Class dan Object
### Latar belakang topik
Dalam pemograman berbasis objek, kita akan memetakan masalah kedalam class, serta memecah masalah kedalam bagian class – class, sehingga program akan terbagi menjadi bagian – bagian yang lebih kecil, didalam class akan terdiri method atau fungsi, serta terdapat property atau attribute, nah dari class nanti kita bisa membuat object dari class yang telah dibuat.

Misalkan pada karyawan yang ada di suatu kantor, terdapat Steven, Rudolf, Smith, dan Kevin yang merupakan karyawan yang ada di kantor tersebut. Mereka antara satu sama lain memiliki kemiripan berupa sama-sama karyawan namun memiliki karakteristik atau ciri yang berbeda antara satu sama lain. Sehingga, mereka bisa disebut sebagai Objek. Salah satu karakteristik berbeda yang mereka miliki ialah nama. Dimana antar karyawan yang ada memiliki nama yang berbeda, nama ini bisa disebut dengan Atribute atau Property.

Kemiripan yang ada pada objek Steven dan objek Rudolf ialah sama-sama merupakan entitas karyawan maka bisa dibuat Class yang disebut dengan Class Employee. Sehingga pada Class Employee ini, terdapat 4 objek, yaitu employee1 yaitu Steven, employee2 yaitu Rudolf, employee3 yaitu Smith, dan employee4 yaitu Kevin. Maka bisa dibilang kalau, Class lah yang mencetak objek-objek.

### Pengantar Class dan Object
Class adalah template, cetakan yang mewakili entitas dunia nyata, dimana pada Class dibutuhkan Atribute dan Method agar dapat menghasilkan suatu Object. Maka, Class adalah kerangka dasar yang harus dibuat terlebih dahulu sebelum membuat suatu Object. Object merupakan reference types, sehingga apabila object di-passing ke sebuah fungsi, maka value dari attribute nya dapat berubah.

#### Membuat Class

```php
<?php

class Employee{
    public $name;
    
    function set_name($name) {
        $this->name = $name;
    }

    function get_name() {
        return $this->name;
    }
}
```

#### Metode Print di php

##### Cara Pertama
Membuat class dan instalasi object, lalu menampilkan hasilnya dengan `echo`
```php
<?php

class Employee{
    public $name;
    
    function set_name($name) {
        $this->name = $name;
    }

    function get_name() {
        return $this->name;
    }
}

$employee1 = new Employee();
$employee1->set_name("Steven");
echo $employee1->get_name();
echo "\n";

//Bisa juga ditulis dengan syntax dibawah ini

$employee2 = new Employee();
$employee2->set_name("Rudolf");
echo $employee2->{"get_name"}();
echo "\n";
```

##### Cara Kedua
Membuat object baru untuk menjalankan get_name, lalu menampilkan hasilnya
```php
<?php

class Employee{
    public $name;
    
    function set_name($name) {
        $this->name = $name;
    }

    function get_name() {
        return $this->name;
    }
}

$employee3 = new Employee();
$employee3->set_name("Smith");
$funcGetNama = "get_name";
echo $employee3->{$funcGetNama}();
echo "\n";
```
##### Cara Ketiga
Tanpa menggunakan set_name dan get_name
```php
<?php
class Employee{
    public $name;
}

$employee4 = new Employee();
$employee4-> name = "Kevin"; //set nama
echo $employee4->name; //print nama
echo "\n";
```
#### Mengubah Variabel
```php
<?php
class Employee{
    public $name;
    
    function set_name($name) {
        $this->name = $name;
    }

    function get_name() {
        return $this->name;
    }
}

function change_name($emp){
    $emp->name = "Smith";
}

$employee1 = new Employee();
$employee1->set_name("Steven");

echo $employee1->get_name(); //sebelum diubah
echo "\n";

change_name($employee1);

echo $employee1->get_name(); //sesudah diubah
echo "\n";
```
