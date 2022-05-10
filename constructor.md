# Constructor

[Kembali](README.md)

## Latar belakang topik
Dalam Pemrograman Berbasis Objek, setelah membuat `Class`, maka nantinya kita bisa menghasilkan `Object`. Proses menghasilkan / mencetak `objek` dari `class` ini disebut dengan `Instansiasi (Instantiation)`. Biasanya setelah melakukan instansiasi inilah kita bisa melakukan eksekusi pada object, misalnya dengan menggunakan setter (set_name, etc) lalu getter (get_name, etc). Namun terdapat cara dimana ketika melakukan instansiasi maka setelahnya tidak perlu melakukan setter ataupun getter untuk mengeksekusi, karena saat di instansiasi, object akan langsung dieksekusi caranya ialah dengan menggunakan fungsi `Constructor`. Selain constructor, terdapat yang namanya fungsi `Destructor` yang sifatnya langsung dijalankan jika semua kondisi yang diinginkan telah terpenuhi.

## Konsep-konsep

`Constructor` ialah fungsi khusus dimana dia akan mengeksekusi object pada saat object di instansiasi, sedangkan `Destructor` merupakan kebalikan dari Constructor, fungsi ini akan berjalan ketika semua kondisi yang diinginkan telah berjalan (fungsi yang berjalan terakhir). `Constructor` dan `Destructor` tidak harus ada didalam suatu Class. Method constructor biasanya berisi pemberian nilai default dari masing-masing properties (variabel). Untuk membuat constructor, cukup dengan mendefinisikan suatu fungsi dengan nama `__construct()`. Begitupun dengan destructor, fungsi ini bisa didefinisikan dengan nama `__destruct()`.

## Metode Constructor tanpa Parameter

### Membuat Class

Membuat `Class Employee` dengan constructor dan destructor

```php
<?php
class Employee {
        public $name;
        public $position;
        function __construct(){
            echo "\nSelamat datang di kantor!\n";
        }
        function set_name($name){
            $this->name = $name;
        }
        function get_name(){
            return $this->name;
        }
        function set_position($position){
            $this->position = $position;
        }
        function get_position(){
            return $this->position;
        }
        function __destruct(){
            echo "Sampai jumpa lagi!\n\n";
        }
    }

```

Metode `__construct` adalah sebuah constructor. Constructor disini dilakukan tanpa menggunakan parameter. Pada `Class Employee`, constructor hanya akan melakukan print. Constructor akan dijalankan setiap sebuah `object` di instansiasi
```php
function __construct(){
    echo "\nSelamat datang di kantor!\n";
}
```

Metode `__destruct` adalah sebuah destructor. Pada `Class Employee`, destructor hanya akan melakukan print. Destructor akan dijalankan setiap sebuah `object` dihapuskan atau saat sebuah script telah selesai dijalankan
```php
function __destruct(){
    echo "Sampai jumpa lagi!\n\n";
}
```

### Instansiasi Object

Menginstansiasi `object` akan langsung menjalankan fungsi constructor. 

```php
<?php
class Employee {
        public $name;
        public $position;
        function __construct(){
            echo "\nSelamat datang di kantor!\n";
        }
        function set_name($name){
            $this->name = $name;
        }
        function get_name(){
            return $this->name;
        }
        function set_position($position){
            $this->position = $position;
        }
        function get_position(){
            return $this->position;
        }
        function __destruct(){
            echo "Sampai jumpa lagi!\n\n";
        }
    }

$employee1 = new Employee();
```

Hasilnya 

![image](https://user-images.githubusercontent.com/100663573/167545313-f96885f7-9a47-44a1-b43c-693ea5b7ec75.png)

Dapat dilihat pada hasil diatas bahwa constructor berjalan saat `object` di instansiasi dan destructor berjalan saat script selesai

### Instansiasi Object dengan Fungsi

Memanggil fungsi set_nama dan get_nama untuk menampilkan hasilnya.

```php
<?php
class Employee {
        public $name;
        public $position;
        function __construct(){
            echo "\nSelamat datang di kantor!\n";
        }
        function set_name($name){
            $this->name = $name;
        }
        function get_name(){
            return $this->name;
        }
        function set_position($position){
            $this->position = $position;
        }
        function get_position(){
            return $this->position;
        }
        function __destruct(){
            echo "Sampai jumpa lagi!\n\n";
        }
    }

$employee1 = new Employee();
$employee1->set_name("Marcus");
$employee1->set_position("CEO");
echo "Karyawan ini bernama ".$employee1->get_name().", dia merupakan seorang ".$employee1->get_position().".\n";
```

Hasilnya 

![image](https://user-images.githubusercontent.com/100663573/167545814-2350d7bf-3211-41c4-9808-16025e71ea37.png)

Dapat dilihat pada hasil diatas bahwa constructor berjalan saat `object` di instansiasi. Selanjutnya akan dilakukan print sesuai dengan script dan terakhir destructor berjalan saat script selesai


## Metode Constructor dengan Parameter

### Membuat Class

Membuat `Class Employee` dengan constructor yang menggunakan parameter dan destructor diakhir. Ketika menggunakan constructor tidak apa-apa jika tidak mendefinisikan atributnya sebelum fungsi constructnya.

```php
<?php
class Employee{
  function __construct($name, $position) { 
    $this->name = $name;
    $this->position = $position;
  }
  
  function cetak(){
    return "Karyawan ini bernama ".$this->name.", dia merupakan seorang ".$this->position.".";
  }

  function __destruct(){
    echo "\nSampai jumpa lagi!\n\n";
  }
}
```

Pada `Class Employee`, constructor akan secara langsung melakukan set name dan position sehingga saat `object` di instansiasi sehingga `object` akan langsung memiliki name dan position

```php
function __construct($name, $position) { 
  $this->name = $name;
  $this->position = $position;
}
```

Sama seperti sebelumnya, kita akan membuat juga sebuah destructor yang akan dijalankan setiap sebuah `object` dihapuskan atau saat sebuah script telah selesai dijalankan
```php
function __destruct(){
    echo "Sampai jumpa lagi!\n\n";
}
```

### Instansiasi Object

Menginstansiasi object dengan parameter nama dan posisi disini akan secara langsung menjalankan fungsi constructor. Disini `object` akan langsung menyimpan Marcus sebagai name dan CEO sebagai position

```php
<?php
class Employee{
  function __construct($name, $position) { 
    $this->name = $name;
    $this->position = $position;
  }
  
  function cetak(){
    return "Karyawan ini bernama ".$this->name.", dia merupakan seorang ".$this->position.".";
  }

  function __destruct(){
    echo "\nSampai jumpa lagi!\n\n";
  }
}

$employee1 = new Employee("Marcus", "CEO");
```

Maka output yang dihasilkan 

![image](https://user-images.githubusercontent.com/100663573/167545554-98891d85-17ac-4656-8b18-a7c577cc23e8.png)

Dapat dilihat pada hasil diatas apabila script hanya akan melakukan print pada bagian destructor. Hal ini dikarenakan tidak ada perintah `echo` pada constructor serta fungsi `cetak` tidak dipanggil

### Instansiasi Object dengan Fungsi

Memanggil fungsi cetak untuk memperlihatkan hasil name dan position `object`

```php
<?php
class Employee{
  function __construct($name, $position) { 
    $this->name = $name;
    $this->position = $position;
  }
  
  function cetak(){
    return "Karyawan ini bernama ".$this->name.", dia merupakan seorang ".$this->position.".";
  }

  function __destruct(){
    echo "\nSampai jumpa lagi!\n\n";
  }
}

$employee1 = new Employee("Marcus", "CEO");
echo $employee1->cetak();
```

Output yang dihasilkan

![image](https://user-images.githubusercontent.com/100663573/167545756-a0144ce8-cea1-41a7-89ca-b13fda82cdb8.png)

Dapat dilihat pada hasil diatas apabila name dan position yang disimpan adalah Marcus dan CEO sesuai dengan name dan position yang disimpan saat `object` di instansiasi. Pada saat script berakhir, seperti biasa destructor akan ikut dijalankan
