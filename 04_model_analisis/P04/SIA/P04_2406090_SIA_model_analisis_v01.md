<!-- Hubungan Diagram Kumulatif SIA -->

| Sumber | Hubungan | Tujuan |
|---|---|---|
| Mahasiswa | Association (tetap) | SIA-UC01 Lihat Jadwal Kuliah |
| Mahasiswa | Association (tetap) | SIA-UC03 Ajukan KRS |
| Mahasiswa | Association (tetap) | SIA-UC05 Unduh Bukti Pengajuan KRS |
| Admin Akademik | Association (tetap) | SIA-UC02 Kelola Jadwal Kuliah |
| Dosen Wali | Association (tetap) | SIA-UC06 Proses Keputusan KRS |
| SIA-UC03 Ajukan KRS | `<<include>>` (tetap dari Pertemuan 3) | SIA-UC04 Validasi KRS |
| SIA-UC05 Unduh Bukti Pengajuan KRS | `<<extend>>` (tetap dari Pertemuan 3) | SIA-UC03 Ajukan KRS |
| Mahasiswa | Generalization → | Civitas Akademika |
| Dosen | Generalization → | Civitas Akademika |
| Civitas Akademika | Association | SIA-UC07 Lihat Kalender Akademik |
| Dosen | Association | SIA-UC08 Input Nilai Mata Kuliah |
| Mahasiswa | Association | SIA-UC09 Lihat KHS |
| Admin Akademik | Association | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC11 Tambah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC12 Ubah Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC13 Hapus Data Mahasiswa | Generalization → | SIA-UC10 Kelola Data Mahasiswa |
| SIA-CO01 Input Nilai Mata Kuliah (collaboration) | Realization → | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 Lihat KHS (collaboration) | Realization → | SIA-UC09 Lihat KHS |

Kondisi extend: [mahasiswa memilih mengunduh bukti].

Extension point pada Ajukan KRS: Konfirmasi penyimpanan pengajuan.

<!-- Situasi A — Mahasiswa Melihat Kalender Akademik -->

Mahasiswa tetap dapat melihat kalender akademik meskipun tidak memiliki
garis asosiasi langsung ke SIA-UC07 Lihat Kalender Akademik.

Mahasiswa merupakan aktor khusus dari Civitas Akademika sehingga
mewarisi asosiasi aktor umum tersebut. Asosiasi cukup digambar satu
kali dari Civitas Akademika ke Lihat Kalender Akademik.

Hasil yang diharapkan: Mahasiswa dapat melihat kalender akademik
melalui kemampuan yang diwarisi dari Civitas Akademika.

<!-- Situasi B — Dosen Bukan Pengampu Menginput Nilai -->

Sistem harus menolak penginputan nilai apabila dosen bukan pengampu
mata kuliah yang dipilih. Hal ini sesuai dengan prasyarat dan alur
alternatif A1 pada deskripsi SIA-UC08 Input Nilai Mata Kuliah.

Hasil yang diharapkan: Akses ditolak, pemberitahuan ditampilkan,
dan tidak ada nilai yang berubah.

<!-- Situasi C — Menghapus Mahasiswa dengan Data Akademik Aktif -->

Sistem harus menolak penghapusan apabila mahasiswa masih memiliki
data akademik aktif. Admin Akademik hanya dapat menghapus mahasiswa
yang memenuhi ketentuan penghapusan pada tugas.

Hasil yang diharapkan: Penghapusan ditolak, alasan penolakan
ditampilkan, dan data mahasiswa tetap tersimpan.

<!-- Hal yang Belum Dirinci -->

1. Rentang angka nilai mengikuti ketentuan akademik dan tidak
   ditentukan secara khusus dalam jobsheet.
2. Pihak dan mekanisme publikasi nilai belum dirinci.
3. Rincian kriteria data akademik aktif belum ditentukan.
4. Hal-hal tersebut dicatat sebagai pertanyaan terbuka, bukan
   dianggap sudah selesai dimodelkan.