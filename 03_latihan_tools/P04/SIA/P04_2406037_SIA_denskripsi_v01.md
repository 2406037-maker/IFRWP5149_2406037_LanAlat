<!-- tabel use case description jadwal -->
|        Elemen        |                            LAB-UC03—Ajukan KRS                           |
|----------------------|--------------------------------------------------------------------------|
|        Tujuan        |                   Menghasilkan pengajuan KRS yang tersimpan              |
|      Aktorutama      |                                Mahasiswa                                 |
|    Sumberkebutuhan   |                     SIA-R03, SIA-R04 dan SIA-R05                         |
|        Pemicu        |                 Mahasiswa memilih fungsi pengajuan KRS                   |
|      Prasyarat       |             Mahasiswa telah terautentikasi; data KRS tersedia            |
| Pascakondisi berhasil|     Pengajuan tersimpan dengan nomor dan status Menunggu keputusan       |
|  Pascakondis  gagal  |             Tidak ada pengajuan baru yang berhasil tersimpan             |
|        Include       |                     SIA-UC04 — Periksa ketersediaan                      |
|    Extensionpoint    |                 Bukti pengajuan tersedia, pada langkah 6                 |
|        Extend        |                 SIA-UC05 jika [mahasiswa memilih unduh]                  |

