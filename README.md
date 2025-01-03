# Tugas-Project-Uas-Bahasa-Pemprograman

**Program akan meminta kita untuk memasukkan nama produk, harga produk, stok produk**
![OutPut UAS](https://github.com/user-attachments/assets/32677432-bc11-4d19-b131-b019a53cf029)

**Class Data**

**_init.py**
```
# class_data/__init__.py
from .class_data import Produk
```

**class_data.py**
```
# class_data/class_data.py
class Produk:
    def __init__(self, nama, harga, stok):
        self.nama = nama
        self.harga = harga
        self.stok = stok
```

**Class Process**

**_init_.py**
```
# class_process/__init__.py
from .class_process import ProdukProcess
```

**class_process.py**
```
# class_process/class_process.py
from class_data import Produk

class ProdukProcess:
    def __init__(self):
        self.produk_list = []

    def tambah_produk(self, nama, harga, stok):
        if not nama:
            raise ValueError("Nama produk tidak boleh kosong.")
        if harga <= 0:
            raise ValueError("Harga produk harus lebih besar dari 0.")
        if stok < 0:
            raise ValueError("Stok produk tidak boleh negatif.")
        
        produk = Produk(nama, harga, stok)
        self.produk_list.append(produk)

    def get_produk(self):
        return self.produk_list
```

**ClassView**

**_init.py_**

```
# class_view/__init__.py
from .class_view import ProdukView
```

**class_view**

```
# class_view/class_view.py
class ProdukView:
    def tampilkan_produk(self, produk_list):
        print(f"{'Nama Produk':<20} {'Harga':<10} {'Stok':<10}")
        print("-" * 40)
        for produk in produk_list:
            print(f"{produk.nama:<20} {produk.harga:<10.2f} {produk.stok:<10}")
```
**main.py**

```
# main.py
from class_data import Produk
from class_process import ProdukProcess
from class_view import ProdukView

def main():
    process = ProdukProcess()  # Membuat instance dari ProdukProcess
    view = ProdukView()        # Membuat instance dari ProdukView

    while True:
        try:
            # Meminta input nama produk
            nama = input("Masukkan nama produk (atau ketik 'exit' untuk keluar): ")
            if nama.lower() == 'exit':
                break
            
            # Meminta input harga produk
            harga = float(input("Masukkan harga produk: "))
            
            # Meminta input stok produk
            stok = int(input("Masukkan stok produk: "))
            
            # Menambahkan produk ke dalam daftar
            process.tambah_produk(nama, harga, stok)
        except ValueError as e:
            print(f"Error: {e}")

    # Tampilkan data produk
    print("\nDaftar Produk:")
    view.tampilkan_produk(process.get_produk())

if __name__ == "__main__":
    main()
```

**Penjelasan Code**

Input Data Produk:

Program meminta pengguna untuk memasukkan nama produk, harga, dan stok secara bergantian.
Data yang dimasukkan oleh pengguna kemudian disimpan dalam suatu struktur data (misalnya, list atau dictionary) untuk dikelola lebih lanjut.
Proses input data akan terus berulang hingga pengguna memasukkan kata kunci "exit" untuk mengakhiri proses input.
Menampilkan Daftar Produk:

Setelah proses input selesai, program akan menampilkan daftar produk yang telah diinputkan dalam bentuk tabel sederhana.
Tabel tersebut biasanya terdiri dari tiga kolom: nama produk, harga, dan stok.
Kemungkinan Bahasa Pemrograman:

Berdasarkan struktur kode dan fungsinya, bahasa pemrograman yang mungkin digunakan adalah:

Python: Bahasa ini sangat populer untuk pemrograman interaktif dan sering digunakan untuk tugas-tugas sederhana seperti ini.
Bahasa scripting lainnya: Bahasa seperti Bash, Perl, atau Ruby juga bisa digunakan untuk membuat program sejenis.
Struktur Data:

Untuk menyimpan data produk yang diinputkan, program ini kemungkinan menggunakan struktur data seperti:

List: Setiap elemen dalam list bisa berupa tuple atau dictionary yang berisi informasi tentang satu produk (nama, harga, stok).
Dictionary: Setiap kunci dalam dictionary bisa berupa nama produk, dan nilainya adalah dictionary lain yang berisi informasi harga dan stok.
Peningkatan yang Mungkin:

Kode ini bisa ditingkatkan dengan menambahkan fitur-fitur berikut:

Validasi input: Memastikan bahwa data yang dimasukkan oleh pengguna valid (misalnya, harga harus berupa angka).
Penyimpanan data: Menyimpan data produk ke dalam file atau database agar data tidak hilang ketika program dijalankan ulang.
Pencarian produk: Memungkinkan pengguna untuk mencari produk berdasarkan nama atau kriteria lainnya.
Penghapusan produk: Memungkinkan pengguna untuk menghapus produk dari daftar.
Pengubahan data produk: Memungkinkan pengguna untuk mengubah harga atau stok suatu produk.
Antarmuka pengguna yang lebih baik: Menggunakan modul atau library untuk membuat tampilan yang lebih menarik dan user-friendly.
