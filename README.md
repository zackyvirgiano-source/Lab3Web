# Praktikum 3 : HTML Lanjutan - Pemrograman Web

Repository ini dibuat untuk menyelesaikan tugas Praktikum 3 Pemrograman Web.  
  
Nama :  Muhammad Zacky Virgiano 
NIM : 312510349
Kelas : I251B  
Mata Kuliah : Pemrograman Web  


## Struktur Folder Proyek

```
Lab2Web/
├── index.html
├── style_eksternal.css
├── README.md
```
<img width="428" height="160" alt="image" src="https://github.com/user-attachments/assets/c8d505fe-65e8-4705-9bb5-ccc69731c380" />



## Langkah-Langkah Praktikum

### 1. Membuat Dokumen HTML

pada langkah ini kita membuat tampilan awal menggunakan HTML
<img width="1107" height="866" alt="image" src="https://github.com/user-attachments/assets/dc368574-e0f4-4f07-a430-533acfee7910" />

<img width="1916" height="345" alt="image" src="https://github.com/user-attachments/assets/393c0cbf-2357-40fc-8774-9217794bf445" />



### 2. Mendeklarasikan CSS internal
kemudian tambahkan deklarasi CSS internal dibagian ('head')

<img width="1072" height="768" alt="image" src="https://github.com/user-attachments/assets/da5b9f23-3b45-416a-80b0-d6d8b41c77ac" />

<img width="1912" height="391" alt="image" src="https://github.com/user-attachments/assets/d7528c63-73d5-4e16-8112-ec8d4170b18e" />


### 3. Menambahkan Inline CSS

Tambahkan deklrasi inline CSS pada tag <p>

<img width="1050" height="342" alt="image" src="https://github.com/user-attachments/assets/a7c2460d-bf33-4f10-9ff0-92c2f8cc8abe" />

<img width="1915" height="412" alt="image" src="https://github.com/user-attachments/assets/033a6b07-5d63-4663-ad22-056070b454eb" />


### 4. Membuat CSS eksternal

menambahkan css eksternal dengan membuat file baru dengan nama style_eksternal.css

<img width="786" height="90" alt="image" src="https://github.com/user-attachments/assets/2cbe21c9-9ec2-4dac-94c7-2759b6bb8e5e" />


<img width="495" height="511" alt="image" src="https://github.com/user-attachments/assets/c6e225cd-3408-4893-9490-e40353752e3a" />

<img width="1908" height="471" alt="image" src="https://github.com/user-attachments/assets/03b95450-6d87-4dbd-94df-fac8e2339896" />



### 5. Menambahkan CSS Selector

menambahkan CSS selector menggunakan ID dan Class Selector pada file style_eksternal.css.

<img width="970" height="601" alt="image" src="https://github.com/user-attachments/assets/93bc4073-7a37-48a3-bbe4-160ea0fd59de" />


<img width="1910" height="480" alt="image" src="https://github.com/user-attachments/assets/4cfcf43a-96b0-4403-825c-2e39cdaf1be8" />





### 6. Validasi Dokumen CSS 

Tahap terakhir yaitu memvalidasi css dengan menggunakan https://jigsaw.w3.org/css-validator/validator

<img width="1848" height="675" alt="image" src="https://github.com/user-attachments/assets/e831ff25-932a-4b84-b0ee-15a557e9724f" />

## Jawaban Pertanyaan dan Tugas

### 1. Eksperimen mengubah dan menambah properti CSS

Saya menambahkan beberapa properti baru di `style_eksternal.css`:

```css
#intro {
    border-radius: 8px;                          /* sudut kotak melengkung */
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.25);  /* bayangan */
}
.button {
    border-radius: 6px;
    font-weight: bold;
}
.button:hover {
    background: #b01e32;                         /* warna tombol berubah saat kursor di atasnya */
}
```

Hasilnya kotak intro jadi melengkung dan punya bayangan, tombol menjadi tebal dan melengkung, serta warnanya lebih gelap saat kursor diarahkan ke tombol. Gambar 5 di atas sudah memakai properti-properti ini.

### 2. Perbedaan `h1 { ... }` dengan `#intro h1 { ... }`

- `h1 { ... }` adalah **selector elemen**. Aturannya berlaku untuk **semua** tag `<h1>` di halaman.
- `#intro h1 { ... }` adalah **selector turunan (descendant)** dengan ID. Aturannya hanya berlaku untuk `<h1>` yang berada **di dalam** elemen ber-`id="intro"`.

Karena `#intro h1` lebih spesifik, aturannya menang bila bentrok dengan `h1` biasa. Di praktikum ini terlihat jelas: `h1` di `<header>` tetap biru dan rata tengah (aturan `h1`), sedangkan `h1` "Hello World" di dalam `#intro` menjadi putih dan rata kiri (aturan `#intro h1`), padahal keduanya sama-sama tag `<h1>`.

### 3. Internal, eksternal, dan inline CSS pada elemen yang sama

Yang tampil di browser adalah **inline CSS**. Alasannya, inline punya prioritas tertinggi dibanding internal maupun eksternal.

Untuk internal dan eksternal, bobot (specificity) keduanya sama, sehingga yang menang adalah aturan yang **dibaca paling akhir** (prinsip *cascading*). Jadi bila `<link>` diletakkan **sebelum** `<style>`, internal yang menang. Bila `<link>` diletakkan **sesudah** `<style>`, eksternal yang menang.

Contoh:

```css
/* style_eksternal.css */
p { color: green; }
```
```html
<head>
    <link rel="stylesheet" href="style_eksternal.css">
    <style> p { color: red; } </style>
</head>
<body>
    <p style="color: blue;">Teks ini berwarna biru</p>
    <p>Teks ini berwarna merah</p>
</body>
```

Paragraf pertama **biru** (inline menang), paragraf kedua **merah** (internal menang karena ditulis setelah `<link>`). Urutan prioritasnya: **inline > internal/eksternal (yang terakhir dibaca)**. Pengecualian: deklarasi yang memakai `!important` mengalahkan inline sekalipun.

### 4. Elemen dengan ID dan Class sekaligus: `<p id="paragraf-1" class="textparagraf">`

Yang tampil adalah deklarasi **ID selector**, karena ID lebih spesifik daripada class. Bobot specificity: ID bernilai lebih tinggi dari class, dan class lebih tinggi dari selector elemen. Urutannya kira-kira: inline > ID > class > elemen.

Contoh:

```css
.textparagraf { color: red; }
#paragraf-1   { color: green; }
```
```html
<p id="paragraf-1" class="textparagraf">Paragraf ini berwarna hijau</p>
```

Paragraf berwarna **hijau**, walaupun `.textparagraf` ditulis lebih dulu atau lebih belakang. Hasilnya tidak bergantung pada urutan penulisan, karena bobot ID lebih besar. Properti yang tidak bentrok tetap digabung, misalnya bila class mengatur `font-size` dan ID mengatur `color`, kedua aturan itu tetap berlaku.

---







      
