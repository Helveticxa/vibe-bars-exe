# Vibe Bars

**Satu bar melayang yang menampilkan status semua sesi AI coding agent-mu — dan membiarkanmu menjawabnya tanpa mencari-cari terminal.**

Untuk Windows 11 (dan Windows 10 64-bit). Padanan [Vibe Island](https://vibeisland.app/) yang selama ini hanya ada di macOS.

---

## Unduh

### **[Vibe-Bars-Setup.exe](https://github.com/Helveticxa/vibe-bars-exe/releases/latest/download/Vibe-Bars-Setup.exe)** — 4,32 MB

Klik, jalankan, selesai. Pemasangan per-pengguna, **tidak perlu hak administrator**.

```
SHA-256  473983F25E556A3F49B0F5F6F99F19D62CEC6FCFE7D4F0F5E7271E0860745DB3
Versi    0.4.1
```

Daftar lengkap perubahan tiap versi ada di
**[halaman rilis](https://github.com/Helveticxa/vibe-bars-exe/releases)**.

> **Sudah memakai Vibe Bars?** Tidak perlu mengunduh apa pun dan tidak perlu mencopot
> yang lama. Buka **Pengaturan → Pembaruan** di dalam aplikasi: versi baru terdeteksi
> sendiri, lengkap dengan daftar perubahannya, lalu terpasang dengan satu klik.

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

**Atas atau bawah, terserah kamu.** Bar bisa menempel di tepi atas layar (bawaan) atau
tepi bawah; panelnya membuka menjauhi tepi itu. Penempatannya mengikuti *work area*
Windows, jadi ia tidak pernah bertabrakan dengan taskbar di sisi mana pun ia dipasang.
Punya dua monitor? Bar bisa dikunci ke salah satunya supaya tidak ikut berpindah
mengikuti kursor.

**Singkirkan sesi yang tidak kamu pedulikan.** Setiap baris punya tombol ✕. Sesi
percobaan yang terminalnya sudah kamu tutup hilang untuk selamanya — tapi kalau sesi
itu benar-benar hidup lagi, ia muncul sendiri tanpa kamu perlu melakukan apa pun.
Tidak ada yang benar-benar terhapus: ada baris "N disembunyikan · tampilkan" untuk
membatalkannya.

**Memperbarui dirinya sendiri.** Tidak perlu mencopot lalu memasang ulang. Pengaturan →
Pembaruan menunjukkan versi yang tersedia beserta daftar perubahannya, mengunduh, lalu
memasang. Setiap paket **wajib lolos verifikasi tandatangan** sebelum dipasang — paket
yang tidak ditandatangani kunci kami ditolak, jadi menguasai saluran unduh saja tidak
cukup untuk menyusupkan sesuatu ke komputermu.

**Tidak pernah merebut fokus.** Bar-nya melayang di atas segalanya tapi tidak pernah
mengambil keyboard, tidak muncul di taskbar, tidak muncul di Alt-Tab. Di luar area
bar, klik tembus ke aplikasi di bawahnya seolah bar-nya tidak ada.

**Ringan saat diam.** Sekitar 0,5–1,2% dari satu core saat menganggur, dan proses
intinya memakai 26 MB.

---

## Privasi — singkat, dan bisa diperiksa

**Tidak ada akun, tidak ada cloud, tidak ada telemetri.** Semua data sesi dibaca dari
berkas transcript yang sudah ada di komputermu.

Ada tepat **dua** hal yang menyentuh jaringan, dan keduanya bisa dimatikan:

| | Default | Yang dikirim | Ke mana |
|---|---|---|---|
| Pemeriksaan pembaruan | **menyala** | tidak ada — hanya permintaan `GET` biasa, lalu nomor versi dibaca dari balasannya | halaman rilis repositori ini di GitHub |
| Kuota Claude Code 5H/7D | **mati** | token OAuth yang sudah dipakai Claude Code sendiri | `api.anthropic.com`, tujuan yang sama yang dihubungi CLI-mu setiap hari |

Bedanya default keduanya bukan soal "jaringan atau bukan", tapi soal **apa yang ikut
terkirim**. Pemeriksaan pembaruan tidak membawa apa pun tentangmu — tidak ada pengenal
perangkat, tidak ada data sesi, tidak ada kredensial. Kuota Claude memakai tokenmu, dan
itu kelas yang berbeda, jadi ia tetap harus kamu pilih sendiri.

Tokennya dibaca saat panggilan dilakukan lalu dibuang. **Tidak pernah** disalin ke disk,
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
