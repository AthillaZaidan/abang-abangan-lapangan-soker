# Abang-Abangan Lapangan Soker

> Dari keluh yang sederhana, ditempa menjadi sumpah yang menggema.

Sebuah [Agent Skill](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) untuk Claude yang menerjemahkan kalimat sehari-hari menjadi narasi **epik-heroik ala anak lapangan ITB**: gaya orasi himpunan dan kaderisasi, khidmat, lantang, dan sedikit terlalu serius untuk topiknya.

Nama skill: `abang-abangan-lapangan-soker`

## Daftar Isi

- [Tentang](#tentang--mengapa-sumpah-ini-ditulis)
- [Sebelum dan Sesudah](#sebelum-dan-sesudah--bara-yang-menyala)
- [Instalasi](#instalasi--menyalakan-bara)
- [Cara Pakai](#cara-pakai--mengangkat-palu)
- [Tiga Mode](#tiga-mode--tiga-nyala-api)
- [Cara Kerja](#cara-kerja--di-balik-tempaan)
- [Hasil Uji](#hasil-uji--bukti-dari-medan)
- [Isi Repo](#isi-repo--peta-medan)
- [Menambah Contoh](#menambah-contoh--menitipkan-api)
- [Peta Jalan](#peta-jalan--fajar-yang-belum-tiba)
- [Kontribusi](#kontribusi)
- [Disclaimer](#disclaimer)
- [Lisensi](#lisensi)

## Tentang — Mengapa Sumpah Ini Ditulis

Di antara kelas yang terlalu pagi dan tugas yang terlalu menumpuk, ada mereka yang bicara dengan kalimat biasa. Bukan karena kata mereka kecil, melainkan karena belum ada yang menempanya. Skill ini hadir sebagai palu dan bara: ia mengangkat "wifi-nya lemot" menjadi medan juang, dan "gw capek" menjadi sumpah yang tak patah. Sebab bagi anak lapangan, tak ada keluh yang terlalu sepele untuk diucapkan dengan khidmat.

Secara teknis, skill ini memberi Claude:

- **Resep gaya** untuk tiga bentuk output (naratif, padat, berima).
- **Menu pembuka dan menu pembalik** yang dirotasi, supaya setiap hasil tidak terdengar seragam.
- **Style guide**: kosakata epik, pola kontras dan penutup, peta metafora benda sepele, cara menjaga rima.
- **20 contoh** pasangan input dan output sebagai acuan nada.
- **Checklist** sebelum keluar: fakta input (termasuk nama diri dan ucapan) tetap tersurat, tidak ada peristiwa karangan, bentuk sesuai mode.

## Sebelum dan Sesudah — Bara yang Menyala

| Biasa | Puitis lapangan |
|---|---|
| Wifi-nya lemot banget, tapi tugas tetap harus dikumpul. | Sinyal tertatih, jaringan runtuh di tengah jalan. Namun tekad kami tak bergantung pada tiang pemancar mana pun. Ini bukan tentang siapa yang tersambung, tapi siapa yang bertahan ketika koneksi memilih pergi. |
| Gw begadang ngerjain tugas sampai subuh. | Tatkala malam menutup mata dunia,<br>ada mereka yang menyalakan layar sebagai pelita.<br>Pelita yang menolak padam meski kantuk menggoda,<br>karena tanggung jawab tak mengenal jam tidur manusia. |
| Makasih ya udah nemenin gw begadang. | Di antara sepi dan kantuk, ada mereka yang tetap duduk di sisiku tanpa diminta. Tak ada kata besar, tak ada janji, hanya kehadiran yang diam-diam menjadi penyangga. Untuk kalian yang tak pernah mengeluh, hutang ini akan kuingat sampai akhir. |

Semua contoh lengkap ada di [examples.md](.claude/skills/abang-abangan-lapangan-soker/examples.md).

## Instalasi — Menyalakan Bara

### Claude Code, di proyek ini

Skill sudah berada di `.claude/skills/`, jadi cukup clone dan buka Claude Code di foldernya.

```bash
git clone https://github.com/AthillaZaidan/abang-abangan-lapangan-soker.git
cd abang-abangan-lapangan-soker
claude
```

### Claude Code, global (semua proyek)

```bash
git clone https://github.com/AthillaZaidan/abang-abangan-lapangan-soker.git
cp -r abang-abangan-lapangan-soker/.claude/skills/abang-abangan-lapangan-soker ~/.claude/skills/
```

Restart sesi Claude Code agar skill terbaca.

### Claude.ai

Kompres folder `abang-abangan-lapangan-soker` menjadi `.zip`, lalu unggah lewat pengaturan Skills di Claude.ai. Langkah rincinya ada di [dokumentasi resmi](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview).

## Cara Pakai — Mengangkat Palu

Cukup tulis kalimat biasa dengan salah satu pemicu. Claude akan memuat skill-nya sendiri, atau panggil langsung dengan `/abang-abangan-lapangan-soker`.

```text
puitiskan: gw telat bangun, kelas udah mulai
```

```text
terjemahin jadi puitis anak lapangan: revisian dosen banyak banget
```

```text
versi berima: hujan deras tapi gw tetep berangkat
```

```text
puitiskan gaya anak lapangan satu-satu ya:
1. gw ketiduran di kelas
2. printer di kosan rusak
```

Pemicu yang dikenali antara lain: "puitiskan", "terjemahin jadi puitis", "bikin epik", "versi epik", "dramatisir", "lebay-in", "gaya anak lapangan", "orasi himpunan", "gaya kaderisasi", juga permintaan berbahasa Inggris seperti "make this epic".

Output hanya berisi hasil jadinya, tanpa penjelasan proses. Sebut mode secara eksplisit jika ingin memilih sendiri. Beberapa input sekaligus akan diberi nomor, dan setiap hasil memakai pembuka dan pembalik yang berbeda. Input berbahasa apa pun menghasilkan output berbahasa Indonesia.

## Tiga Mode — Tiga Nyala Api

Mode dipilih otomatis dari sifat input, atau sebutkan sendiri.

| Mode | Cocok untuk | Bentuk |
|---|---|---|
| **Naratif** | perasaan, cerita, ucapan, input berisi beberapa kegiatan | 3-5 kalimat, lembut. Suasana, lalu tokohnya, lalu kontras "bukan karena X, melainkan Y", lalu penutup bermakna. |
| **Padat** | kejadian atau aksi singkat | 3 kalimat, keras. Kondisi sulit, lalu kalimat pembalik dari menu, lalu "Ini bukan tentang X, tapi Y". |
| **Berima** | hanya bila diminta puisi, rima, atau sajak | 4 baris, semuanya berakhir dengan bunyi vokal yang sama (-a, -an, -ah, atau -i). |

## Cara Kerja — Di Balik Tempaan

1. Catat fakta input: tindakan, perasaan, nama diri, tempat, angka, dan ucapan (selamat, terima kasih, maaf).
2. Pilih mode.
3. Pilih sudut pandang. Ucapan ke seseorang disapa langsung dengan "kau", "engkau", atau "kalian". Pengalaman sendiri diangkat menjadi "aku", "kami", atau "mereka".
4. Pilih satu pembuka dan satu pembalik dari menu di [SKILL.md](.claude/skills/abang-abangan-lapangan-soker/SKILL.md), yang belum dipakai dalam jawaban maupun percakapan.
5. Tulis draf sesuai resep mode.
6. Cek: setiap fakta muncul tersurat, tidak ada peristiwa karangan, bentuk sesuai mode, ada kosakata epik dan satu pembalikan. Revisi sekali jika perlu.
7. Keluarkan hasilnya saja.

Pembuka dan pembalik dirotasi lewat menu, bukan lewat larangan. Alasannya, panduan berbentuk resep positif lebih patuh diikuti model daripada daftar "jangan", dan rotasi ini mencegah semua output terdengar seragam.

## Hasil Uji — Bukti dari Medan

Skill diuji dengan 9 input baru yang tidak ada di `examples.md`. Isinya mencakup topik sedih, ucapan selamat ke orang lain, paragraf panjang, input bahasa Inggris, permintaan berima, dan empat input sekaligus. Setiap input dijalankan di Claude Haiku dan Opus dalam tiga kondisi: tanpa skill, skill tersedia tanpa dipanggil, dan skill dipanggil langsung. Penilaian otomatis mengecek tanda seru, slang, emoji, teks meta, panjang, fakta input yang tersurat, rima, dan variasi pembuka.

| Model | Tanpa skill | Skill tersedia | Skill dipanggil |
|---|---|---|---|
| Haiku | 66% | 68% (terpicu 1 dari 9) | 84% |
| Opus | 57% | 88% (terpicu 9 dari 9) | 95% |

Tanpa skill, Claude cenderung memberi beberapa versi sekaligus, membiarkan slang seperti "gw" lolos, dan memakai emoji. Uji ini juga menemukan lima kelemahan yang kemudian diperbaiki di versi sekarang:

- Description terlalu lunak, sehingga Haiku jarang memuat skill.
- Frasa "mereka yang" muncul di setiap hasil.
- Nama diri seperti "Google" hilang, dan muncul peristiwa yang tidak ada di input.
- Ucapan ke orang lain berubah menjadi "mereka".
- Pembuka berulang ketika banyak input diproses sekaligus.

Perbaikan tersebut belum diuji ulang. Angka di tabel di atas berasal dari versi sebelum perbaikan.

## Isi Repo — Peta Medan

```text
.
├── README.md
└── .claude/
    └── skills/
        └── abang-abangan-lapangan-soker/
            ├── SKILL.md         # alur, tiga mode, menu pembuka dan pembalik, nada, checklist
            ├── style-guide.md   # kosakata, pola kontras dan penutup, peta metafora, rima
            └── examples.md      # 20 pasangan input dan output yang disetujui
```

Mengikuti prinsip *progressive disclosure*: hanya `name` dan `description` yang selalu dimuat, `SKILL.md` dimuat saat skill terpicu, dan dua file lainnya dibaca hanya saat dibutuhkan.

## Menambah Contoh — Menitipkan Api

Kualitas skill ini ditentukan oleh contohnya. Untuk menambah:

1. Tulis pasangan input biasa dan output puitis di `examples.md`, tandai modenya.
2. Pastikan output lolos checklist di `SKILL.md`: makna kebawa, bentuk sesuai mode, rima konsisten untuk mode berima.
3. Jika menemukan pembuka atau pembalik baru yang khas, tambahkan ke menu di `SKILL.md`. Kosakata dan metafora baru masuk ke `style-guide.md`.

Contoh yang paling berguna adalah yang topiknya berbeda dari 20 contoh yang ada dan yang nyerempet kehidupan kampus lain, bukan hanya IF.

## Peta Jalan — Fajar yang Belum Tiba

- [x] Skill dasar dengan tiga mode dan 20 contoh
- [x] Uji formal di Haiku dan Opus: dengan skill dan tanpa skill, termasuk pengukuran variasi pembuka
- [x] Perbaikan dari hasil uji: description lebih tegas, menu pembalik, fakta konkret dijaga, sapaan orang kedua
- [ ] Uji ulang setelah perbaikan, ditambah Sonnet
- [ ] Perbanyak contoh menjadi 50 atau lebih, termasuk topik per fakultas dan jurusan
- [ ] Mode tambahan, misalnya sindiran halus (passive-aggressive)
- [ ] Opsional: kumpulkan pasangan input dan output sebagai dataset untuk fine-tune model lokal (LoRA) agar tidak bergantung pada API

## Kontribusi

Issue dan pull request dipersilakan, terutama untuk contoh baru, perbaikan rima, dan temuan output yang meleset dari gaya. Sertakan input yang dipakai dan output yang dihasilkan agar mudah direproduksi.

## Disclaimer

Proyek ini dibuat untuk hiburan dan latihan menulis. Ia tidak berafiliasi dengan, dan tidak mewakili, ITB atau himpunan mana pun. Semua contoh dibuat untuk repo ini sebagai ilustrasi gaya.

## Lisensi

Belum ditentukan. Tambahkan berkas `LICENSE` sebelum menggunakan ulang atau mendistribusikan.

---

Di ujung hari yang melelahkan, tertinggal satu kalimat biasa,
kalimat yang menunggu tangan yang berani menempanya.
Maka bawalah ia ke sini, tanpa gentar, tanpa ragu apa-apa,
dan pulanglah sebagai orasi yang tak lagi bisa dilupa.
