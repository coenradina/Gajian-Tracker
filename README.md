# Gajian Tracker · Starter Dashboard

Starter project untuk kelas **Build Data Dashboard with Google Antigravity** dari [Generation Girl](https://www.generationgirl.org).

Isinya satu file `index.html`, yaitu dashboard pengeluaran bulanan yang strukturnya sudah jadi tapi masih memakai **data dummy**. Di kelas, kamu akan membuatnya bisa membaca **file Excel** (hasil download dari Google Sheets) dengan bantuan agent di Google Antigravity. Datamu tetap di laptop, tidak perlu di-publish ke mana-mana.

![Mode data dummy](https://img.shields.io/badge/status-data%20dummy-fdfbcb?labelColor=004987)

---

## 1. Ambil starter-nya (fork)

*Fork* artinya menyalin repo ini ke akun GitHub kamu sendiri. Kamu bebas mengubah salinanmu tanpa memengaruhi repo aslinya.

1. Login ke GitHub (bikin akun gratis di [github.com](https://github.com) kalau belum punya).
2. Klik tombol **Fork** di kanan atas halaman ini, lalu klik **Create fork**.
3. Sekarang kamu punya salinan di `github.com/<username-kamu>/<nama-repo>`.

## 2. Pindahkan ke laptop

Pilih salah satu cara.

**Cara A (paling gampang, tanpa install apa-apa)**

1. Di halaman fork kamu, klik tombol hijau **Code**, lalu pilih **Download ZIP**.
2. Ekstrak ZIP-nya ke folder yang gampang dicari, misalnya `Documents/gajian-tracker`.

**Cara B (kalau sudah punya Git)**

```bash
git clone https://github.com/<username-kamu>/<nama-repo>.git
```

## 3. Buka di Antigravity

1. Buka **Antigravity**, di sidebar **Projects** klik ikon folder bertanda +, pilih **New Project**, lalu pilih folder tadi dan klik **Open**.
2. Buka juga `index.html` di **Google Chrome** (klik dua kali file-nya, atau drag ke Chrome).
3. Kalau muncul banner kuning bertuliskan **"Mode data dummy"**, berarti starter sudah jalan.

---

## 4. Aktivitas 2: Baca data dari file Excel

**Siapkan file-nya dulu.** Di Google Sheets yang sudah kamu bersihkan, klik *File > Download > Microsoft Excel (.xlsx)*. Simpan di folder project ini supaya gampang dicari.

Lalu kirim prompt ini ke agent. Pastikan pilihan di bawah kotak chat menunjukkan **Local**.

```
Peran: Kamu adalah front-end developer yang teliti.

Esensi: Buat dashboard di index.html bisa membaca data dari file Excel saya.

Situasi: index.html sudah punya struktur lengkap, tapi masih memakai DUMMY_DATA.
Tombol "Upload file Excel" dan "Update realtime" sudah jadi. Keduanya memanggil
loadData(file) dengan file yang dipilih.
File saya .xlsx hasil download dari Google Sheets, datanya di tab "Transaksi".
Kolom: Tanggal, Keterangan, Kategori, Nominal, Metode Bayar.

Aturan:
- Ubah HANYA fungsi loadData(file). Jangan ubah layout, CSS, tombol, atau fungsi lain.
- Pakai SheetJS (XLSX, sudah dimuat di <head>): baca file dengan file.arrayBuffer(),
  lalu XLSX.read(buffer, { type: "array", raw: true }).
- Ambil tab NAMA_SHEET (kalau tidak ada, tab pertama), ubah jadi array dengan
  XLSX.utils.sheet_to_json(sheet, { defval: "" }), rapikan setiap baris dengan
  normalizeRow(), lalu saring dengan isValidRow().
- Kalau file kosong (belum dipilih), tetap kembalikan DUMMY_DATA dengan source "dummy".
  Kalau datanya dari file, pakai source "file".
- Kalau gagal, lempar Error dengan pesan berbahasa Indonesia yang jelas.

Nuansa: Jelaskan rencanamu dulu sebelum mengubah kode, dan tunggu persetujuan saya.
```

**Sebelum menyetujui**, baca plan dan code diff dari agent. Pastikan yang diubah memang cuma `loadData()`. Setelah itu, refresh `index.html` di Chrome dan klik **Upload file Excel**.

### Cek hasilnya (wajib)

- [ ] Banner berubah jadi **"Terbaca dari file Excel"**.
- [ ] Angka **Total pengeluaran** sama dengan `=SUM(D:D)` di Sheet kamu.
- [ ] Jumlah transaksi sama dengan jumlah baris data di Sheet.

Kalau angkanya beda, berarti ada yang salah. Bisa di datanya, bisa juga di kodenya. Justru ini gunanya dicek.

### Upload vs Update realtime

| Tombol | Cara kerja | Browser |
|---|---|---|
| **Upload file Excel** | Dibaca sekali. Kalau file-nya kamu ubah, upload lagi. | Semua browser |
| **Update realtime** | Pilih file sekali, klik izinkan. Dashboard mengecek file tiap 2 detik dan ikut berubah setiap file disimpan. | Chrome, Edge, Arc |

Update realtime butuh aplikasi yang menyimpan langsung ke file `.xlsx` atau `.csv`, misalnya Microsoft Excel atau LibreOffice. Numbers di Mac menyimpan ke format `.numbers`, jadi untuk Numbers pakai *File > Export To > Excel* lalu Upload ulang.

## 5. Aktivitas 3: Kustomisasi bebas

Pilih prompt sesuai level kamu, atau tulis versimu sendiri. Selalu tambahkan kalimat *"Jangan ubah fungsi loadData()."* supaya koneksi datanya tidak rusak.

**Pemula**
```
Ganti warna utama dashboard jadi [warna favoritmu] dan ubah judulnya jadi
"Gajian Tracker [nama kamu]". Pastikan teks tetap mudah dibaca.
Jangan ubah fungsi loadData().
```

**Menengah**
```
Ubah grafik "Per metode bayar" jadi donut chart, lalu tambahkan kartu KPI
keempat: rata-rata pengeluaran per hari. Jangan ubah fungsi loadData().
```

**Mahir**
```
Tambahkan dropdown filter kategori di atas grafik. Semua KPI, grafik, dan
tabel ikut berubah sesuai filter. Di grafik "Per kategori", tampilkan juga
budget tiap kategori (dari objek BUDGET) supaya kelihatan kategori mana yang
lewat budget. Jangan ubah fungsi loadData().
```

Setelah selesai, screenshot dashboard kamu dan kirim di form submission bersama 1 insight dan angka pendukungnya.

---

## 6. PR (opsional): Publikasikan dashboard-mu

Dengan GitHub Pages, dashboard-mu bisa punya link sendiri yang bisa dibagikan. Gratis dan tanpa terminal.

1. Di halaman fork kamu, klik **Add file** → **Upload files**, lalu drag `index.html` versi terbarumu ke sana. Tulis pesan singkat (misalnya *"Baca data dari file Excel"*), lalu klik **Commit changes**.
2. Buka **Settings** → **Pages**. Di bagian *Branch*, pilih `main` dan folder `/ (root)`, lalu klik **Save**.
3. Tunggu 1–2 menit. Link dashboard-mu akan muncul di halaman yang sama (`https://<username-kamu>.github.io/<nama-repo>/`).

Di GitHub Pages, tombol Upload dan Update realtime tetap jalan. File yang kamu pilih dibaca di browser-mu sendiri dan tidak ikut ter-upload ke GitHub.

Setiap commit adalah *save point*. Kalau suatu saat dashboard-mu rusak, kamu bisa melihat dan mengembalikan versi sebelumnya lewat tab **Commits**.

## Catatan privasi

- File Excel yang kamu pilih dibaca **di browser-mu sendiri**. Isinya tidak dikirim ke server mana pun.
- Agent di Antigravity bisa membaca semua file di folder project. Jangan simpan file berisi data pribadi asli di folder ini kalau sedang memakai agent.
- Link GitHub Pages bisa dibuka **siapa saja**. Jangan commit file Excel berisi data asli ke repo.
- Jangan pernah menaruh API key, password, atau token di `index.html`. Semua yang dimuat browser bisa dilihat orang lewat *View Source*.

---

Data di dashboard ini fiktif dan dibuat untuk latihan. Dibuat oleh Generation Girl.
