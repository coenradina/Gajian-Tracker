# Duit Gajian Ke Mana Aja? · Starter Dashboard

Starter project untuk kelas **Build Data Dashboard with Google Antigravity** dari [Generation Girl](https://www.generationgirl.org).

Isinya satu file `index.html`, yaitu dashboard pengeluaran bulanan yang strukturnya sudah jadi tapi masih memakai **data dummy**. Di kelas, kamu akan menyambungkannya ke data Google Sheets milikmu sendiri dengan bantuan agent di Google Antigravity.

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
2. Ekstrak ZIP-nya ke folder yang gampang dicari, misalnya `Documents/duit-gajian`.

**Cara B (kalau sudah punya Git)**

```bash
git clone https://github.com/<username-kamu>/<nama-repo>.git
```

## 3. Buka di Antigravity

1. Buka **Antigravity**, klik ikon folder, pilih **New Project** → **Add Folder**, lalu arahkan ke folder tadi dan klik **Create**.
2. Buka juga `index.html` di **Google Chrome** (klik dua kali file-nya, atau drag ke Chrome).
3. Kalau muncul banner kuning bertuliskan **"Mode data dummy"**, berarti starter sudah jalan.

---

## 4. Aktivitas 2: Sambungkan ke Google Sheets

Ganti `[TEMPEL LINK CSV KAMU]` dengan link CSV dari *File > Share > Publish to web* di Google Sheets, lalu kirim prompt ini ke agent. Waktu memulai percakapan, pilih **Local mode**.

```
Peran: Kamu adalah front-end developer yang teliti.

Esensi: Sambungkan dashboard di index.html ke data Google Sheets saya.

Situasi: index.html sudah punya struktur lengkap, tapi masih memakai DUMMY_DATA.
Link CSV saya: [TEMPEL LINK CSV KAMU]
Kolom di CSV: Tanggal, Keterangan, Kategori, Nominal, Metode Bayar.

Aturan:
- Isi variabel CSV_URL dengan link di atas.
- Ubah HANYA fungsi loadData(). Jangan ubah layout, CSS, atau fungsi lain.
- Pakai Papa.parse (PapaParse sudah dimuat di <head>) dengan download: true,
  header: true, dan skipEmptyLines: true. Rapikan setiap baris dengan normalizeRow(),
  lalu saring dengan isValidRow().
- Kalau CSV_URL kosong, tetap kembalikan DUMMY_DATA dengan source "dummy".
  Kalau datanya dari CSV, pakai source "csv".
- Kalau gagal, lempar Error dengan pesan berbahasa Indonesia yang jelas.

Nuansa: Jelaskan rencanamu dulu sebelum mengubah kode, dan tunggu persetujuan saya.
```

**Sebelum menyetujui**, baca plan dan code diff dari agent. Pastikan yang diubah memang cuma `loadData()` dan `CSV_URL`. Setelah itu, refresh `index.html` di Chrome.

### Cek hasilnya (wajib)

- [ ] Banner berubah jadi **"Terhubung ke Google Sheets"**.
- [ ] Angka **Total pengeluaran** sama dengan `=SUM(D:D)` di Sheet kamu.
- [ ] Jumlah transaksi sama dengan jumlah baris data di Sheet.

Kalau angkanya beda, berarti ada yang salah. Bisa di datanya, bisa juga di kodenya. Justru ini gunanya dicek.

## 5. Aktivitas 3: Kustomisasi bebas

Pilih prompt sesuai level kamu, atau tulis versimu sendiri. Selalu tambahkan kalimat *"Jangan ubah fungsi loadData()."* supaya koneksi datanya tidak rusak.

**Pemula**
```
Ganti warna utama dashboard jadi [warna favoritmu] dan ubah judulnya jadi
"Duit Gajian [nama kamu]". Pastikan teks tetap mudah dibaca.
Jangan ubah fungsi loadData().
```

**Menengah**
```
Ubah grafik "Per metode bayar" jadi donut chart, lalu tambahkan kartu KPI
keempat: rata-rata pengeluaran per hari. Jangan ubah fungsi loadData().
```

**Advanced**
```
Tambahkan dropdown filter kategori di atas grafik. Semua KPI, grafik, dan
tabel ikut berubah sesuai filter. Di grafik "Per kategori", tampilkan juga
budget tiap kategori (dari objek BUDGET) supaya kelihatan kategori mana yang
lewat budget. Jangan ubah fungsi loadData().
```

Setelah selesai, screenshot dashboard kamu dan submit di workbook bersama 1 insight dan angka pendukungnya.

---

## 6. PR (opsional): Publikasikan dashboard-mu

Dengan GitHub Pages, dashboard-mu bisa punya link sendiri yang bisa dibagikan. Gratis dan tanpa terminal.

1. Di halaman fork kamu, klik **Add file** → **Upload files**, lalu drag `index.html` versi terbarumu ke sana. Tulis pesan singkat (misalnya *"Sambungkan ke data Sheets"*), lalu klik **Commit changes**.
2. Buka **Settings** → **Pages**. Di bagian *Branch*, pilih `main` dan folder `/ (root)`, lalu klik **Save**.
3. Tunggu 1–2 menit. Link dashboard-mu akan muncul di halaman yang sama (`https://<username-kamu>.github.io/<nama-repo>/`).

Setiap commit adalah *save point*. Kalau suatu saat dashboard-mu rusak, kamu bisa melihat dan mengembalikan versi sebelumnya lewat tab **Commits**.

## Catatan privasi

- Link *Publish to web* dan GitHub Pages bisa dibuka **siapa saja**. Pakai data dummy saja.
- Jangan pernah menaruh API key, password, atau token di `index.html`. Semua yang dimuat browser bisa dilihat orang lewat *View Source*.
- Kalau mau mencoba dengan data pribadi, simpan file-nya di laptop dan jangan di-publish.

---

Data di dashboard ini fiktif dan dibuat untuk latihan. Dibuat oleh Generation Girl.
