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
- **Style guide**: kosakata epik, menu pembuka yang dirotasi, pola kontras, peta metafora benda sepele.
- **20 contoh** pasangan input dan output sebagai acuan nada.
- **Checklist** sebelum keluar: makna asli tetap terbaca, bentuk sesuai mode, tidak mengulang pembuka.

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

Pemicu yang dikenali antara lain: "puitiskan", "terjemahin jadi puitis", "bikin epik", "gaya anak lapangan", "orasi himpunan", "lebay heroik".

Output hanya berisi hasil jadinya, tanpa penjelasan proses. Sebut mode secara eksplisit jika ingin memilih sendiri.

## Tiga Mode — Tiga Nyala Api

Mode dipilih otomatis dari sifat input, atau sebutkan sendiri.

| Mode | Cocok untuk | Bentuk |
|---|---|---|
| **Naratif** | perasaan, cerita, rasa syukur | 3-4 kalimat, lembut. Suasana, lalu "ada mereka yang...", lalu kontras, lalu penutup bermakna. |
| **Padat** | kejadian atau aksi singkat | 3 kalimat, keras. Kondisi sulit, lalu "Namun mereka yang...", lalu "Ini bukan tentang X, tapi Y". |
| **Berima** | permintaan "puisi", "berima", "bersajak" | 4 baris, semuanya berakhir dengan bunyi vokal yang sama (-a, -an, -ah, atau -i). |

## Cara Kerja — Di Balik Tempaan

1. Tangkap inti makna: siapa, melakukan apa, perasaannya.
2. Pilih mode.
3. Angkat subjek dari "gw/lu" menjadi "mereka", "kami", "kalian", atau "aku".
4. Pilih pembuka dan pola kontras dari [style-guide.md](.claude/skills/abang-abangan-lapangan-soker/style-guide.md), berbeda dari output sebelumnya.
5. Tulis draf sesuai resep mode.
6. Cek: makna asli masih bisa ditebak, bentuk sesuai mode, ada kosakata epik dan satu pembalikan. Revisi sekali jika perlu.
7. Keluarkan hasilnya saja.

Pembuka dirotasi lewat menu, bukan lewat larangan. Alasannya, panduan berbentuk resep positif lebih patuh diikuti model daripada daftar "jangan", dan rotasi ini mencegah semua output terdengar seragam.

## Isi Repo — Peta Medan

```text
.
├── README.md
└── .claude/
    └── skills/
        └── abang-abangan-lapangan-soker/
            ├── SKILL.md         # alur, tiga mode, nada, checklist
            ├── style-guide.md   # kosakata, menu pembuka, pola kontras, peta metafora
            └── examples.md      # 20 pasangan input dan output yang disetujui
```

Mengikuti prinsip *progressive disclosure*: hanya `name` dan `description` yang selalu dimuat, `SKILL.md` dimuat saat skill terpicu, dan dua file lainnya dibaca hanya saat dibutuhkan.

## Menambah Contoh — Menitipkan Api

Kualitas skill ini ditentukan oleh contohnya. Untuk menambah:

1. Tulis pasangan input biasa dan output puitis di `examples.md`, tandai modenya.
2. Pastikan output lolos checklist di `SKILL.md`: makna kebawa, bentuk sesuai mode, rima konsisten untuk mode berima.
3. Jika menemukan pembuka atau kosakata baru yang khas, tambahkan ke `style-guide.md`.

Contoh yang paling berguna adalah yang topiknya berbeda dari 20 contoh yang ada dan yang nyerempet kehidupan kampus lain, bukan hanya IF.

## Peta Jalan — Fajar yang Belum Tiba

- [x] Skill dasar dengan tiga mode dan 20 contoh
- [ ] Uji formal: bandingkan output dengan skill dan tanpa skill, termasuk pengukuran variasi pembuka
- [ ] Perbanyak contoh menjadi 50 atau lebih, termasuk topik per fakultas dan jurusan
- [ ] Uji di beberapa model (Haiku, Sonnet, Opus)
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
