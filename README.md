# Maulana Azizwara - 1301160210
## NO. 1
Diagram TCP finite state machine merupakan diagram yang menjelaskan alur terjadinya three way handshake pada saat pembuatan koneksi TCP. Starting point berada pada state CLOSED ketika belum ada koneksi.

### Client

   - Client mengirim SYN (SYN SENT)
   - Client menerima SYN dan ACK, kemudian mengirim ACK (CONNECTION ESTABLISHED)
   - Client mengirimkan FIN (FIN WAIT 1)
   - Client menerima ACK (FIN WAIT 2)
   - Client menerima FIN dan mengirim ACK (TIME WAIT)
   - Terjadi timeout, maka koneksi berakhir (CLOSED)

### Server

   - Server membuat koneksi secara passive open (LISTEN)
   - Server menerima SYN, kemudian mengirim SYN, ACK (SYN RCVD)
   - Server menerima ACK (CONNECTION ESTABLISHED)
   - Server menerima FIN, kemudian mengirimkan ACK (CLOSE WAIT)
   - Server mengirim FIN (LAST ACK)
   - Server mengakhiri koneksi (CLOSED)
   
## Nomor 2
### For
```go
package main

import "fmt"

func main() {
	i := 1
	for i <= 3 {
		fmt.Println(i)
		i = i + 1
	}
	for j := 7; j <= 9; j++ {
		fmt.Println(j)
	}
	for {
		fmt.Println("loop")
		break
	}
	for n := 0; n <= 5; n++ {
		if n%2 == 0 {
			continue
		}
		fmt.Println(n)
	}
}
```
### Penjelasan
* Melakukan perulangan sesuai dengan kondisi/nilai yang telah ditentukan.
* Perulangan berhenti ketika kondisi bernilai false.
* Perulangan dapat dihentikan dengan menggunakan break dan continue.

### Hasil
![alt screenshot2][2]

### If/Else
```go
package main

import "fmt"

func main() {
	if 7%2 == 0 {
		fmt.Println("& is even")
	} else {
		fmt.Println("7 is odd")
	}
	if 8%4 == 0 {
		fmt.Println("8 is divisible by 4")
	}

	if num := 9; num < 0 {
		fmt.Println(num, "is negative")
	} else if num < 10 {
		fmt.Println(num, "has 1 digit")
	} else {
		fmt.Println(num, "has multiple digits")
	}
}
```
### Penjelasan
* Merupakan suatu perbandingan yang dilakukan sesuai dengan kondisi yang telah ditentukan.
* If dijalankan ketika bernilai true, if else dijalankan ketika ada kondisi yang berbeda, dan else dijalankan ketika if dan if else bernilai false.

### Hasil
![alt screenshot2-2][22]

## Nomor 3
### Array
```go
package main

import "fmt"

func main() {
	var a [5]int
	fmt.Println("emp:", a)

	a[4] = 100
	fmt.Println("set:", a)
	fmt.Println("get:", a[4])

	fmt.Println("len:", len(a))

	b := [5]int{1, 2, 3, 4, 5}
	fmt.Println("dcl:", b)

	var twoD [2][3]int
	for i := 0; i < 2; i++ {
		for j := 0; j < 3; j++ {
			twoD[i][j] = i + j
		}
	}
	fmt.Println("2d: ", twoD)
}
```
### Penjelasan
* Array adalah sekumpulan variabel yang memiliki tipe data yang sama dan dinyatakan dengan nama yang sama dan memiliki indeks untuk setiap nilainya.
* Perintah ````len(variabelArray)```` digunakan untuk mengetahui panjang dari suatau array.
* Array dapat berbentuk 2D atau lebih.

### Hasil
![alt screenshot3][3]

### Function
```go
package main

import "fmt"

func plus(a int, b int) int {
	return a + b
}
func plusPlus(a, b, c int) int {
	return a + b + c
}

func main() {
	res := plus(1, 2)
	fmt.Println("1+2 =", res)

	res = plusPlus(1, 2, 3)
	fmt.Println("1+2+3 = ", res)
}
```
### Penjelasan
* Function adalah sekumpulan blok kode yang dibungkus dengan nama tertentu.
* Function akan dijalankan ketika dipanggil.

### Hasil
![alt screenshot3-2][32]

## Nomor 4
### Struct
```go
package main

import "fmt"

type person struct {
	name string
	age  int
}

func main() {
	fmt.Println(person{"Bob", 20})
	fmt.Println(person{name: "Alice", age: 30})
	fmt.Println(person{name: "Fred"})
	fmt.Println(person{name: "Ann", age: 40})

	s := person{name: "Sean", age: 50}
	fmt.Println(s.name)

	sp := &s
	fmt.Println(sp.age)

	sp.age = 51
	fmt.Println(sp.age)
}
```
### Penjelasan
* Kumpulan dari variabel yang dinyatakan dengan sebuah nama, dengan sifat setiap variabel dapat memiliki tipe yang berlainan.
* Ketika melakukan pemanggilan struct terdapat variabel yang tidak di definisikan, maka nilainya nil dan hanya akan menampilkan variable yang ditentukan.

### Hasil
![alt screenshot4][4]

### Method
```go
package main

import "fmt"

type rect struct {
	width, height int
}

func (r *rect) area() int {
	return r.width * r.height
}

func (r rect) perim() int {
	return 2*r.width + 2*r.height
}

func main() {
	r := rect{width: 10, height: 5}

	fmt.Println("area: ", r.area())
	fmt.Println("perim: ", r.perim())

	rp := &r
	fmt.Println("area: ", rp.area())
	fmt.Println("perim: ", rp.perim())
}
```
### Penjelasan
* Method merupakan suatu fungsi yang terdapat didalam struct/class.
* Method memiliki akses ke struct.

### Hasil
![alt screenshot4-2][42]

## Nomor 5
### Multiple Return Value
```go
package main

import "fmt"

func vals() (int, int) {
	return 3, 7
}
func main() {
	a, b := vals()
	fmt.Println(a)
	fmt.Println(b)

	_, c := vals()
	fmt.Println(c)
}
```
### Penjelasan
* Multiple return merupakan fungsi yang dapat mengembalikan lebih dari 1 nilai.

### Hasil
![alt screenshot5][5]

### Command Line
```go
package main

import (
	"flag"
	"fmt"
)

func main() {
	wordPtr := flag.String("word", "foo", "a string")

	numbPtr := flag.Int("numb", 42, "an int")
	boolPtr := flag.Bool("fork", false, "a bool")

	var svar string
	flag.StringVar(&svar, "svar", "bar", "a string var")

	flag.Parse()

	fmt.Println("word:", *wordPtr)
	fmt.Println("numb:", *numbPtr)
	fmt.Println("fork:", *boolPtr)
	fmt.Println("svar:", svar)
	fmt.Println("tail:", flag.Args())
}
```
### Penjelasan
* Deklarasi flag dapat berupa string, integer, dan boolean.
* Flag dideklarasikan dengan assign ke variable

### Hasil
![alt screenshot5-2][52]

## Nomor 6
### Simple Web Application
```go
package main

import (
	"fmt"
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		fmt.Fprintf(w, "Hello, you've requested: %s\n", r.URL.Path)
	})
	http.ListenAndServe(":8000", nil)
}
```
### Penjelasan
* HandleFunc merupakan fungsi yang digunakan untuk menentukan route/konten ketika diakses.
* ListenAndServe berfungsi untuk menentukan port yang digunakan untuk mengakses.

### Hasil
![alt screenshot6][6]



[2]: SS/no2for.png
[22]: SS/no2if.png
[3]: SS/no3array.png
[32]: SS/no3function.png
[4]: SS/no4struct.png
[42]: SS/no4method.png
[5]: SS/no5multi.png
[52]: SS/no5command.png
[6]: SS/no6.png
