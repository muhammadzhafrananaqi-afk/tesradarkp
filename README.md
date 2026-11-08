# ALKP Radar

Situs direktori lomba dan olimpiade pelajar. Satu file HTML tanpa build step, tanpa dependensi (hanya Google Fonts).

## Menjalankan

Buka `index.html` di browser, atau deploy ke hosting statis (GitHub Pages, Netlify, Vercel, Cloudflare Pages).

### GitHub Pages
1. Buat repo baru di GitHub, unggah `index.html` dan `README.md`.
2. Settings > Pages > Source: Deploy from a branch > `main` / root.
3. Situs aktif di `https://USERNAME.github.io/NAMA-REPO/`.

## Mengubah data lomba

Data ada di array `D` pada bagian `<script>` di `index.html` (cari `var D=[`). Satu lomba:

```js
{id:10,type:'lomba',f:'Voli',t:'Judul lomba',
 s:'Ringkasan singkat (maks 160 karakter).',lg:'Deskripsi lengkap.',
 pl:'Tempat',d:'20 sampai 22 Februari 2027',dl:'2027-01-30',
 fee:'Rp 500.000 per tim',lv:'SMA/SMK sederajat',org:'Penyelenggara',
 pz:'Hadiah',ct:'Kontak',link:'https://contoh.id',hot:1,ph:'',
 tl:[['Sampai 30 Jan','Pendaftaran'],['20 Feb','Pertandingan']]}
```

- `type`: `'lomba'` atau `'olimpiade'`
- `dl`: batas pendaftaran, format `TTTT-BB-HH` (wajib)
- `hot:1`: tampil di bagian populer
- `ph`: URL atau data URL poster (boleh kosong)
- `id` harus unik

## Mode admin

Tombol **Admin** di header membuka form tambah, edit, dan hapus lomba serta unggah poster.

Penting: penyimpanan permanen lewat tombol admin hanya bekerja saat halaman dibuka di claude.ai oleh akun pemilik (memakai kemampuan `artifact` dan `assets` milik claude.ai). Di hosting lain, perubahan dari mode admin hanya hidup selama tab terbuka. Di sana, ubah data langsung di array `D`.

### Mengganti password admin

Password tidak disimpan, hanya hash SHA-256 dari `alkp-radar-v1:` + password. Buat hash baru di konsol browser:

```js
crypto.subtle.digest('SHA-256', new TextEncoder().encode('alkp-radar-v1:PASSWORDBARU'))
 .then(b => console.log([...new Uint8Array(b)].map(x => x.toString(16).padStart(2,'0')).join('')))
```

Tempel hasilnya ke konstanta `PH` di `index.html`. Pemeriksaan password terjadi di sisi browser, jadi hanya pengaman ringan.

## Struktur

```
index.html   semua markup, CSS, dan JavaScript
README.md    dokumentasi ini
```
