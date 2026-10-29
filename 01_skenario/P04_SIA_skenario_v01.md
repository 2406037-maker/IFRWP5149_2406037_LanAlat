Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa: menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian

• Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap mempunyai identitas berbeda. • Pengguna telah terautentikasi dan memiliki hak akses sesuai peran. • Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); jangan menyamakannya dengan jadwal kuliah pada Pertemuan 2. • Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan. • Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini fiktif untuk latihan. • Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3. Pembayaran dan perancangan basis data berada di luar tugas ini.

|No|   Nama_Aktor   |                        Kedudukan                         |                                          Fungsi                                            |
|--|----------------|----------------------------------------------------------|--------------------------------------------------------------------------------------------|
|1 |CivitasAkademika|            Aktor umum, baru pada Pertemuan 4             |                                 Melihat kalender akademik.                                 |
|2 |   Mahasiswa    |           Aktor khusus dari Civitas Akademika            |    Melihat jadwal kuliah, mengajukan KRS, mengunduh bukti pengajuan KRS, melihat kalender  | 
|3 |     Dosen      |Aktor khusus dari Civitas Akademika, baru pada Pertemuan 4| Melihat kalender akademik melalui pewarisan dan menginput nilai mata kuliah yang diampunya |
|4 |     Admin      |        Akademik  Aktor lama dari pertemuan sebelumnya    |                  Mengelola jadwal kuliah serta mengelola data mahasiswa                    |
|5 |     Dosen      |            Wali  Aktor lama dari Pertemuan 3             |                                  Memproses keputusan KRS                                   |



1. Hierarki Mahasiswa dan Dosen

Civitas Akademika merupakan aktor umum (general actor), sedangkan Mahasiswa dan Dosen merupakan aktor khusus (specialized actor).

Mahasiswa → Civitas Akademika: Mahasiswa mewarisi fungsi melihat kalender akademik dari aktor umum Civitas Akademika.
Dosen → Civitas Akademika: Dosen mewarisi fungsi melihat kalender akademik dari aktor umum Civitas Akademika.
2. Fungsi yang Diwarisi

Fungsi yang diwarisi oleh Mahasiswa dan Dosen adalah SIA-UC07 Lihat Kalender Akademik. Dengan demikian, keduanya dapat mengakses fungsi tersebut melalui hubungan generalization tanpa perlu membuat asosiasi masing-masing aktor ke use case yang sama.

3. Alasan Pemodelan

Generalization digunakan karena Mahasiswa dan Dosen memiliki fungsi bersama, yaitu melihat kalender akademik. Dengan menempatkan fungsi tersebut pada aktor umum Civitas Akademika, diagram menjadi lebih sederhana, mengurangi pengulangan asosiasi, dan menunjukkan hubungan pewarisan fungsi dengan jelas.

4. Aturan Penggambaran Diagram

Hubungkan aktor Mahasiswa ke Civitas Akademika menggunakan relasi generalization.
Hubungkan aktor Dosen ke Civitas Akademika menggunakan relasi generalization.
Hubungkan Civitas Akademika satu kali ke SIA-UC07 Lihat Kalender Akademik.
Arah panah generalization menggunakan garis dengan segitiga kosong yang menunjuk ke aktor umum Civitas Akademika.
Jangan menggambar asosiasi langsung dari Mahasiswa dan Dosen ke SIA-UC07 karena fungsi tersebut sudah diwarisi dari aktor umum.
Use Case Umum:

SIA-UC10 — Kelola Data Mahasiswa: Use case umum yang digunakan Admin Akademik untuk mengelola data mahasiswa.
Tiga Use Case Khusus:

SIA-UC11 — Tambah Data Mahasiswa: Admin Akademik menambahkan data mahasiswa baru ke dalam sistem.
SIA-UC12 — Ubah Data Mahasiswa: Admin Akademik memperbarui data mahasiswa yang sudah tersimpan di dalam sistem.
SIA-UC13 — Hapus Data Mahasiswa: Admin Akademik menghapus data mahasiswa yang sudah tidak diperlukan sesuai ketentuan sistem.
Alasan Pemodelan: SIA-UC11, SIA-UC12, dan SIA-UC13 merupakan use case khusus dari SIA-UC10 karena ketiganya memiliki tujuan umum yang sama, yaitu mengelola data mahasiswa, tetapi memiliki perilaku yang berbeda. Hubungan generalization digambarkan dengan garis berujung segitiga kosong dari setiap use case khusus menuju SIA-UC10 sebagai use case umum.

|ID_Collaboration|Nama_Collaboration|            Use_Case_yang_Direalisasikan             |
|----------------|------------------|-----------------------------------------------------|
|    SIA-CO01    |      Input       |Nilai Mata Kuliah SIA-UC08 — Input Nilai Mata Kuliah |
|    SIA-CO02    |    Lihat_KHS     |                SIA-UC09 — Lihat KHS                 |


Penjelasan:

SIA-CO01 — Input Nilai Mata Kuliah merupakan collaboration yang merealisasikan SIA-UC08 — Input Nilai Mata Kuliah.
SIA-CO02 — Lihat KHS merupakan collaboration yang merealisasikan SIA-UC09 — Lihat KHS.
Kedua collaboration menggambarkan interaksi antarbagian sistem untuk mewujudkan perilaku yang ditetapkan pada use case terkait. Nama collaboration harus sama persis dengan nama use case yang direalisasikannya. Aturan penggambaran diagram: Hubungkan setiap collaboration dengan use case yang direalisasikannya menggunakan relasi realization, yaitu garis putus-putus dengan segitiga kosong yang mengarah ke use case. Collaboration digambarkan di dalam batas sistem, dan aktor tidak dihubungkan langsung ke collaboration.