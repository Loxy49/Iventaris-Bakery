"# Iventaris-Bakery" 
# Deskripsi 
Repositori ini dibuat untuk memenuhi tugas mata kuliah Struktur Data. Kami membuat sistem Inventaris Toko Roti berbasis Linked List menggunakan bahasa pemrograman C++.
Anggota Kelompok:
1.  [Miftahush Syaadah](https://github.com/loxy49) (C030324077)
2.  [Nur Azkia](https://github.com/vonirisee) (C030324102)
3.  [Tiara Lestari](https://github.com/tyaaralestari) (C030324111)

# Studi Kasus
Toko Rootie adalah usaha rumahan yang bergerak di bidang kuliner, khususnya roti dan makanan ringan. Pemilik toko mengalami kesulitan dalam mencatat daftar produk secara manual karena:
1. Stok produk sering berubah-ubah
2. Produk baru sering ditambahkan
3. Ada produk yang sudah tidak dijual

Untuk itu, kami membuat sistem inventaris yang dapat:
Create (Tambah Produk)
Read (Lihat Daftar Produk)
Update (Perbarui Informasi Produk)
Delete (Hapus Produk)

# Fitur Program
1. Menambahkan produk roti baru ke dalam inventaris
2. Menyisipkan produk di awal daftar
3. Mengedit nama, deskripsi, atau stok produk
4. Menghapus produk berdasarkan nama
5. Menampilkan seluruh daftar produk yang tersedia
6. Validasi input angka (harga & stok) 

# Dokumentasi Program
Berikut ini merupakan penjelasan masing-masing prosedur atau fungsi yang telah dibuat agar pengguna dapat memahami bagaimana sistem ini bekerja secara menyeluruh.


## Tambah Produk Roti

Prosedur `tambah_item` menggunakan operator `new` untuk mengalokasikan memori secara dinamis (di heap) dan mengembalikan pointer ke memori tersebut.

```cpp
if(head == nullptr) {
    head = itemBaru;
    return;
} 
```

Jika inventaris kosong (`head` masih `nullptr`), maka produk pertama langsung ditempatkan di `head`. Jika sudah ada produk lain, maka program akan menelusuri hingga akhir daftar dan menambahkan produk baru di ujung:

```cpp
printing_item* temp = head;
while(temp->selanjutnya != nullptr) {
    temp = temp->selanjutnya;
}
temp->selanjutnya = itemBaru;
```

---

## Sisipkan Produk Roti di Awal

Fungsi `sisipkan_item` digunakan untuk menambahkan produk roti baru **di awal** daftar inventaris.

```cpp
printing_item* hanyar = new printing_item{nm, desk, stok, head};
head = hanyar;
```

Produk baru langsung dijadikan sebagai `head`, dan menunjuk ke produk sebelumnya.

---

## Perbarui Produk Roti

Fungsi `update_item` digunakan untuk mengubah informasi dari produk roti yang sudah ada dalam daftar, berdasarkan **nama produk**.

```cpp
void update_item(printing_item* head, string nm)
```

- `head`: pointer ke produk pertama.
- `nm`: nama produk yang ingin dicari dan diperbarui.

Menu akan muncul untuk memilih bagian yang ingin diubah: nama roti, deskripsi, atau jumlah stok.

---

## Hapus Produk Roti

Prosedur `hapus_item` digunakan untuk menghapus produk roti dari inventaris menggunakan `delete`. Tahapan penghapusan sebagai berikut:

if (temp->nama == target) {
    if (!prev) head = temp->next;
    else prev->next = temp->next;
    delete temp;
}


### 1. Cek apakah inventaris kosong

```cpp
if (head == nullptr) {
    cout << "Daftar Kosong." << endl;
    return;
}
```

### 2. Cek apakah produk pertama sesuai

```cpp
printing_item* temp = head;
if (temp->nama == nm){
    head = temp->selanjutnya;
    delete temp;
    cout << "Produk Dihapus" << endl;
    return;
}
```

### 3. Jika tidak, telusuri seluruh daftar

```cpp
while (temp != nullptr){
    if (temp->nama == nm){
        sebelum->selanjutnya = temp->selanjutnya;
        delete temp;
        cout << "\n[!] Produk Dihapus\n" << endl;
        return;
    }
    sebelum = temp;
    temp = temp->selanjutnya;
}
```

### 4. Jika produk tidak ditemukan

```cpp
cout << "Produk Tidak Ada" << endl;
```

---

## Tampilkan Semua Produk

Fungsi `tampilkan_item` menampilkan semua produk roti yang tersedia di dalam inventaris.

### 1. Cek apakah inventaris kosong

```cpp
if(head == nullptr) {
    cout << "Tidak ada produk dalam inventaris." << endl;
    return;
}
```

### 2. Tampilkan semua produk

```cpp
printing_item* temp = head;
while(temp != nullptr) {
    cout << "Nama Produk : " << temp->nama << endl;
    cout << "Deskripsi   : " << temp->deskripsi << endl;
    cout << "Stok        : " << temp->stok << "\n" << endl;
    temp = temp->selanjutnya;
}
```
