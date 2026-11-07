# ALKP RADAR

Website pencari lomba dan olimpiade untuk pelajar. Satu file HTML statis tanpa build.

## Fitur
- Beranda dengan lomba hot dan lomba yang segera ditutup
- Cari lomba dengan filter bidang dan filter olimpiade per mata pelajaran
- Detail lomba: tempat, biaya, batas daftar, hadiah, kontak, timeline
- Mode admin (password) untuk tambah, edit, hapus lomba

## Menjalankan
Buka `index.html` di browser, atau deploy ke Vercel sebagai situs statis.

## Catatan
- Data lomba yang diinput admin disimpan di browser (localStorage), jadi belum dibagikan ke pengunjung lain.
- Password admin ada di bagian `PW_HASH` pada `index.html` dalam bentuk hash SHA-256 dengan garam `alkp-radar-v1:`. Ganti sebelum dipakai sungguhan.
