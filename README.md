# KidsScreenTimer

Tool untuk mengontrol dan membatasi waktu layar PC anak lewat Telegram tanpa server, tanpa cloud.

---

## Kenapa ini ada?

Aplikasi parental control di pasaran kebanyakan berbayar, kompleks, atau butuh akun cloud. Saya ingin sesuatu yang simpel: **buka Telegram, pencet tombol, PC anak terkunci.** Itu saja.

Proyek ini jalan langsung di PC anak. Bot Telegram-nya cuma jembatan — tidak ada data yang lewat server lain.

---

## Install

1. Download `KidsScreenTimer2.exe` dari halaman [Releases](../../releases)
2. Jalankan, isi form setup:
   - **Bot Token** — dari [@BotFather](https://t.me/BotFather) di Telegram
   - **Chat ID** — dari [@userinfobot](https://t.me/userinfobot) di Telegram
   - **Nama PC** — bebas, contoh: `PC-Andi` (penting kalau pakai di banyak PC)
   - **PIN Admin** — untuk proteksi pengaturan lokal
3. Selesai. Buka chat bot di Telegram → ketik `/menu`

> Tidak perlu install runtime tambahan. Butuh Windows 7+ 64-bit.

---

## Cara Pakai

Semua kontrol lewat bot Telegram. Setelah setup, ketik `/menu` di chat bot:

```
/menu        → tampilkan semua kontrol
/status      → cek waktu tersisa
/kunci       → kunci layar PC sekarang
/buka        → buka kunci (butuh PIN atau jawab soal matematika)
/laporan     → lihat riwayat sesi hari ini
```

Atau pakai tombol inline langsung dari menu — tidak perlu hafal perintah.

**Kirim voice note** ke bot → diputar otomatis di PC anak.  
**Catatan:** pertama kali kirim voice note, app akan download ~40MB komponen audio otomatis.

---

## Fitur

| Fitur | Keterangan |
|-------|-----------|
| Timer layar | Set batas waktu, peringatan otomatis 5 & 1 menit |
| Kunci layar | Kunci/buka PC dari Telegram |
| Soal matematika | Anak harus jawab soal untuk buka kunci |
| Pesan OSD | Tampilkan pesan di layar PC |
| Voice note | Kirim suara — diputar di PC anak |
| Screenshot | Ambil tangkap layar PC anak |
| Webcam | Foto dari kamera PC |
| Cek aplikasi | Lihat app yang sedang berjalan |
| Kill app | Paksa tutup aplikasi |
| Power control | Shutdown / Restart / Sleep |
| Laporan sesi | Riwayat harian & bulanan |
| Multi-PC | Satu bot untuk banyak PC |
| Multi-admin | Sampai 3 akun Telegram bisa kontrol |

---

## Multi-PC

Pasang di PC kedua, ketiga, dst dengan **Bot Token yang sama** tapi **Nama PC berbeda**. Tiap PC kirim menu sendiri berlabel namanya. Tombol sudah diarahkan otomatis — tidak akan salah PC.

---

## Ganti HP / Tambah Admin

Klik ikon di System Tray → **Ubah Konfigurasi** → tambahkan Chat ID HP baru di kolom ke-2 atau ke-3.

---

## File Suara

Aplikasi butuh 4 file `.wav` yang harus kamu siapkan sendiri, taruh di folder yang sama dengan `.exe`:

| Nama File | Kapan Diputar |
|-----------|--------------|
| `notif_pesan.wav` | Ada pesan masuk dari Telegram |
| `notif_5menit.wav` | Peringatan sisa 5 menit |
| `notif_1menit.wav` | Peringatan sisa 1 menit |
| `notif_sukses.wav` | Anak berhasil jawab soal |

Ambil file WAV gratis di [Mixkit](https://mixkit.co/free-sound-effects/) atau [Pixabay](https://pixabay.com/sound-effects/), rename sesuai nama di atas.

---

## Hal yang Perlu Diperhatikan

- **ffplay.exe tidak ikut di-download** bareng `.exe` ini karena ukurannya 200MB+. App akan otomatis download saat pertama kali ada voice note masuk — butuh koneksi internet saat itu.
- **Konfigurasi (token, PIN) disimpan terenkripsi** di `%APPDATA%\KidsScreenTimer\` pakai Windows DPAPI. Artinya config terikat ke akun Windows — kalau reinstall Windows, perlu setup ulang.

---

## Tech Stack

- C# — .NET Framework 4.0 (tanpa dependency eksternal)
- Telegram Bot API — polling manual, tidak pakai library pihak ketiga
- Windows DPAPI — enkripsi config lokal
- ffplay (FFmpeg) — playback voice note

---

## Kontribusi

Issue dan PR terbuka. Kalau ada bug atau request fitur, buka issue dulu sebelum kirim PR.

---

## Lisensi

MIT
