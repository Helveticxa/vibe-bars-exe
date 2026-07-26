# Vibe Bars

**Satu bar melayang di tengah-atas layar yang menampilkan status semua sesi AI coding agent-mu — dan membiarkanmu menjawabnya tanpa mencari-cari terminal.**

Untuk Windows 11 (dan Windows 10 64-bit). Padanan [Vibe Island](https://vibeisland.app/) yang selama ini hanya ada di macOS.

---

## Unduh

### **[Vibe-Bars-Setup.exe](https://github.com/Helveticxa/vibe-bars-exe/raw/main/Vibe-Bars-Setup.exe)** — 3,36 MB

Klik, jalankan, selesai. Pemasangan per-pengguna, **tidak perlu hak administrator**.

```
SHA-256  F50B86A300BC303EDCED0FDC42190F4529E0C1DB5FD631C47660DF3729199D03
Versi    0.1.0
```

Verifikasi berkasnya sebelum menjalankan (opsional tapi disarankan):

```powershell
Get-FileHash .\Vibe-Bars-Setup.exe -Algorithm SHA256
```

---

## Windows akan menampilkan peringatan — ini yang terjadi dan kenapa

Installer ini **belum ditandatangani secara digital**, jadi Windows SmartScreen akan
menampilkan layar biru *"Windows protected your PC"*.

Untuk melanjutkan: klik **More info** lalu **Run anyway**.

Saya tidak akan berpura-pura ini normal. Sertifikat penandatanganan kode berbayar dan
butuh verifikasi identitas usaha; selama Vibe Bars masih beta, biayanya belum masuk akal.
Yang bisa saya berikan sebagai gantinya adalah **checksum SHA-256 di atas** — cocokkan,
dan kamu tahu berkas yang kamu jalankan persis sama dengan yang saya unggah.

Penandatanganan kode ada di rencana sebelum versi berbayar dirilis.

---

## Apa yang kamu dapat

**Status live semua agent dalam satu tempat.** Claude Code, Codex, dan Hermes terbaca
otomatis — nama proyek, apa yang sedang dikerjakan agent detik ini, model, git branch,
token, jumlah berkas tersentuh, diff `+/−`, subagent, dan MCP server yang terpakai.

**Setujui izin tanpa pindah jendela.** Saat Claude Code minta izin menjalankan perintah,
kartunya muncul di bar lengkap dengan diff-nya. Klik Allow atau Deny, dan sesi di
terminal lanjut jalan.

**Jawab pertanyaan agent dari bar.** Kartu AskUserQuestion dengan opsi bernomor.

**Lompat ke terminalnya.** Satu klik, jendela terminal sesi itu naik ke depan — bahkan
kalau sedang diminimize atau tertimbun jendela lain.

**Kuota, bukan tebakan.** Sisa kuota Codex dibaca dari berkas lokal, tanpa jaringan.
Kuota Claude Code 5 jam dan 7 hari tersedia sebagai opsi (default mati — lihat Privasi).

**Tidak pernah merebut fokus.** Bar-nya melayang di atas segalanya tapi tidak pernah
mengambil keyboard, tidak muncul di taskbar, tidak muncul di Alt-Tab. Di luar area
bar, klik tembus ke aplikasi di bawahnya seolah bar-nya tidak ada.

**Ringan saat diam.** Sekitar 0,5–1,2% dari satu core saat menganggur, dan proses
intinya memakai 26 MB.

---

## Privasi — singkat, dan bisa diperiksa

- **Tidak ada akun, tidak ada cloud, tidak ada telemetri.** Semua data dibaca dari
  berkas transcript yang sudah ada di komputermu.
- **Satu-satunya fitur yang memakai jaringan** adalah kuota Claude Code, dan itu
  **default mati**. Kalau kamu menyalakannya, ia memanggil endpoint resmi Anthropic
  memakai token yang sudah dipakai Claude Code sendiri — tujuan yang sama yang sudah
  dihubungi CLI-mu setiap hari.
- Token dibaca saat panggilan dilakukan lalu dibuang. **Tidak pernah** disalin ke disk,
  ke log, atau ke pengaturan aplikasi. Vibe Bars **tidak pernah menulis** ke berkas
  kredensialmu dan tidak pernah menyegarkan tokenmu.

---

## Cara memasang

1. Unduh dan jalankan installer. Lewati peringatan SmartScreen seperti di atas.
2. Bar muncul di tengah-atas layar, dan layar sambutan terbuka sendiri.
3. Kalau kamu memakai Claude Code, tekan **Pasang hook & mulai**. Ini menambahkan tiga
   entri ke `~/.claude/settings.json` supaya kartu izin dan kartu pertanyaan bisa jalan.

   Yang dijamin, dan bisa kamu periksa sendiri di berkasnya: entri kita **ditambahkan**,
   bukan menimpa — hook milik alat lain tidak pernah disentuh, urutan kunci JSON
   dipertahankan, dan berkas aslinya di-backup lebih dulu. Bisa dicabut kapan saja lewat
   Pengaturan, dan uninstaller mencabutnya otomatis.

   Kalau Vibe Bars mati atau ditutup, Claude Code **tidak ikut macet** — hook-nya
   fail-open dan CLI lanjut seperti biasa.

4. Arahkan kursor ke bar untuk membuka panel. Tidak perlu klik.

**Mencopot:** lewat Settings lalu Apps di Windows seperti aplikasi biasa. Hook otomatis
dicabut dari `settings.json`. Pengaturanmu di `%APPDATA%\vibe-bars` sengaja **tidak**
dihapus, supaya pemasangan ulang mengembalikan preferensimu.

---

## Yang belum bisa — dikatakan di depan

- **Codex tidak punya approve/deny.** Bukan kami yang belum membuatnya; Codex memang
  tidak menyediakan kanal untuk itu. Tombolnya sengaja tidak ditampilkan.
- **Hermes hanya menampilkan rencana.** Hermes tidak menulis transcript sesi, jadi
  status live, token, dan biaya dibiarkan kosong alih-alih ditebak.
- **Kolom biaya menampilkan tanda strip** sampai kamu mengisi tabel harga di
  `%APPDATA%\vibe-bars\pricing.json`. Tabel bawaannya sengaja kosong: menebak harga
  menghasilkan angka yang terlihat meyakinkan tapi salah, dan itu lebih buruk daripada
  tidak menampilkan apa-apa.
- **Kuota Codex hanya berubah saat Codex berjalan**, karena di situlah angkanya ditulis
  ke berkas. Bacaan lama ditandai jelas, bukan ditampilkan seolah masih berlaku.
- **Pintasan keyboard belum berfungsi.** Konsekuensi langsung dari desain "tidak pernah
  merebut fokus". Semua tombol bisa diklik seperti biasa.

---

## Butuh apa

| | |
|---|---|
| Windows | 10 64-bit atau 11 |
| Hak admin | Tidak perlu |
| WebView2 | Sudah dibundel di installer, dipasang otomatis kalau belum ada |
| Rust / Node / compiler | **Tidak perlu.** Itu kebutuhan saat membangun, bukan saat menjalankan |

---

## Lapor masalah

Buka [issue](https://github.com/Helveticxa/vibe-bars-exe/issues). Kalau ada yang aneh,
jalankan dengan `VB_DEBUG=1` dan sertakan keluarannya:

```powershell
$env:VB_DEBUG=1; & "$env:LOCALAPPDATA\Vibe Bars\vibe-bars.exe"
```

---

Repositori ini **hanya berisi installernya**. Kode sumbernya tidak publik.
Lihat [LICENSE](LICENSE) untuk ketentuan pemakaian.
