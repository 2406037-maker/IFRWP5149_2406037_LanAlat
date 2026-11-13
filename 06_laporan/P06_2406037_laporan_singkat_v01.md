### A. Tujuan Praktikum

Tujuan praktikum pertemuan 6 adalah menyusun activity diagram dari tabel skenario use case pertemuan 5, sehingga langkah Kegiatan dan Respon sistem diubah menjadi alur aktivitas yang dapat diikuti dari awal sampai akhir. Secara khusus, praktikum ini bertujuan agar mahasiswa mampu:

1. Menyusun alur utama dari Skenario Normal dengan satu initial node, action yang berurutan, dan activity final node tanpa alur yang terputus.
2. Mengubah Skenario Alternative menjadi cabang decision dengan guard yang lengkap, lalu mengembalikannya ke alur utama melalui merge atau mengakhirinya pada jalur akhir yang jelas.
3. Menggunakan fork dan join sebagai pasangan untuk dua proses yang berjalan paralel.
4. Mengelompokkan setiap action ke dalam swimlane sesuai aktor pada tabel skenario.
5. Menelusuri setiap action ke langkah tabel skenario pertemuan 5 dan memeriksa hasil dengan checklist penilaian.

### B. Dasar Teori

Activity diagram adalah diagram UML yang memodelkan alur kegiatan suatu proses, meliputi urutan action, percabangan keputusan, proses paralel, dan pembagian tanggung jawab antar pelaku. Jika use case diagram menunjukkan fungsi apa saja yang disediakan sistem dan tabel skenario menguraikan fungsi itu menjadi langkah, maka activity diagram menggambarkan langkah-langkah tersebut sebagai alur.

Unsur activity diagram yang dipakai pada praktikum ini:

| Unsur | Fungsi |
|---|---|
| Initial node | Titik awal alur; tepat satu pada setiap diagram |
| Action | Satu langkah kegiatan dari tabel skenario, ditulis dengan kata kerja dan objek |
| Control flow | Panah urutan pelaksanaan antar action |
| Decision | Titik cabang bersyarat; setiap alur keluar wajib memiliki guard dalam kurung siku |
| Merge | Titik penggabungan cabang kembali ke alur utama |
| Fork | Membagi alur menjadi dua proses atau lebih yang berjalan paralel |
| Join | Menyatukan proses paralel dari fork; fork selalu berpasangan dengan join |
| Activity final node | Titik akhir alur |
| Swimlane | Pengelompokan action menurut aktor pelaksananya |

Pemetaan dari tabel skenario ke activity diagram: Skenario Normal menjadi alur utama; Skenario Alternative menjadi cabang decision dengan guard; langkah include menjadi action wajib pada alur utama; langkah extend menjadi cabang decision tersendiri dengan condition yang sama dengan diagram pertemuan 4; kolom Kegiatan menjadi action pada swimlane aktor; kolom Respon sistem menjadi action pada swimlane Sistem; Skenario Akhir menjadi activity final node. Collaboration tidak digambar pada activity diagram.

### C. Hasil Praktikum

Praktikum dikerjakan dengan draw.io dan hasilnya disimpan pada folder 04_model_analisis/P06. Pada studi kasus Sistem Informasi Peminjaman dan Pengembalian Peralatan Laboratorium (LAB) dibuat tujuh activity diagram untuk tujuh use case utama:

| No. | Activity diagram | Sumber skenario | Swimlane | Unsur utama |
|---|---|---|---|---|
| 1 | Lihat Ketersediaan Peralatan | LAB-UC01 | Peminjam, Sistem | Decision Peralatan tersedia? dengan guard [tersedia] dan [tidak tersedia], merge |
| 2 | Kelola Data Peralatan | LAB-UC02, UC08, UC09, UC10 | Petugas Laboratorium, Sistem | Decision bentuk pengelolaan dengan tiga cabang [tambah], [ubah], [hapus]; decision Data peralatan ditemukan?, Syarat penghapusan terpenuhi?, Data lengkap dan sah?; merge |
| 3 | Peminjaman | LAB-UC03 | Mahasiswa, Sistem, Petugas Laboratorium | Action include Periksa ketersediaan (dari LAB-UC04); decision Peralatan tersedia?; cabang extend Cetak Bukti Pengajuan (dari LAB-UC05) dengan guard [ya, memilih cetak] dan [tidak]; merge |
| 4 | Cetak Bukti Pengajuan | LAB-UC05 | Mahasiswa, Sistem | Alur dimulai dari konteks extend; decision Mahasiswa memilih cetak bukti?; merge |
| 5 | Proses Keputusan Peminjaman | LAB-UC06 | Petugas Laboratorium, Sistem | Decision Pengajuan dapat diproses? dan Pengajuan disetujui?; status Disetujui dan Ditolak; merge |
| 6 | Pengembalian | LAB-UC11 | Mahasiswa, Sistem, Petugas Laboratorium | Fork dan join untuk dua pemeriksaan paralel; decision Kondisi peralatan baik dan lengkap; merge |
| 7 | Lihat Laporan Peminjaman | LAB-UC07 | Kepala Laboratorium, Sistem | Alur pilih periode laporan; decision Ada data peminjaman?; merge |

Hal-hal penting pada hasil diagram LAB:

1. Activity Peminjaman memuat action include Periksa ketersediaan (dari LAB-UC04) sebagai langkah wajib setelah data pengajuan disimpan. Jika peralatan [tidak tersedia], mahasiswa menerima pemberitahuan pengajuan tidak terpenuhi; jika [tersedia], petugas memproses keputusan peminjaman. Kedua cabang digabung dengan merge sebelum Sistem mencatat hasil akhir pengajuan, lalu decision cetak bukti menjadi cabang extend ke Cetak Bukti Pengajuan (dari LAB-UC05).
2. Activity Pengembalian memuat satu pasang fork dan join setelah Catat Pengembalian Peralatan. Dua pemeriksaan berjalan paralel pada swimlane Petugas Laboratorium, yaitu Periksa kondisi peralatan (dari LAB-UC12) untuk kondisi fisik dan Periksa kelengkapan aksesoris peralatan. Action kedua diberi keterangan (unsur proses baru) karena merupakan kebutuhan proses baru dari jobsheet dan bukan berasal dari pertemuan 3, 4, atau 5. Setelah join, decision Kondisi peralatan baik dan lengkap bercabang ke [baik dan lengkap] (status peralatan diperbarui menjadi tersedia) dan [rusak atau tidak lengkap] (kerusakan atau kekurangan dicatat dan perbaikan dijadwalkan), kemudian digabung dengan merge menuju Menutup transaksi peminjaman.
3. Activity Kelola Data Peralatan melipat LAB-UC08, UC09, dan UC10 sebagai tiga cabang varian dalam satu diagram. Cabang alternatif yang digambar: data peralatan tidak ditemukan pada cabang ubah, syarat penghapusan tidak terpenuhi pada cabang hapus (pesan peralatan masih terpakai), dan data tidak lengkap atau tidak sah (penyimpanan ditolak).
4. Activity Cetak Bukti Pengajuan, Proses Keputusan Peminjaman, Lihat Ketersediaan Peralatan, dan Lihat Laporan Peminjaman disusun dari alur utama, kemudian ditambah cabang alternatif beserta guard dan merge pada berkas final. Pada Activity Lihat Laporan Peminjaman tidak ditambahkan fitur di luar tabel skenario, seperti ekspor atau unduh laporan.

Pada studi kasus Sistem Informasi Akademik (SIA) disusun activity diagram dari tabel skenario pertemuan 5, yaitu:

| No. | Activity diagram        | Sumber skenario                   | Swimlane                  | Unsur utama                                                                                                                                         |
| --- | ----------------------- | --------------------------------- | ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Ajukan KRS              | Pengajuan KRS, SIA-UC03, SIA-UC04 | Mahasiswa, Sistem         | Include Validasi KRS, decision Validasi memenuhi pemeriksaan? dengan guard [memenuhi] dan [tidak_memenuhi], serta extend Unduh Bukti Pengajuan KRS. |
| 2   | Input Nilai Mata Kuliah | SIA-UC08                          | Dosen, Sistem             | Decision Dosen memiliki hak akses?, Nilai dalam rentang yang sah?, dan Data nilai lengkap?                                                          |
| 3   | Kelola Data Mahasiswa   | SIA-UC09        | Admin Akademik, Sistem    | Decision fungsi pengelolaan [tambah], [ubah], [hapus], pemeriksaan data ditemukan, syarat penghapusan, dan kelengkapan data.                        |
| 4   | Kelola Jadwal Kuliah    | Pengelolaan Jadwal Kuliah         | Admin Akademik, Sistem    | Decision Data lengkap dan tidak bentrok? serta konfirmasi penyimpanan jadwal.                                                                       |
| 5   | Lihat Jadwal Kuliah     | Lihat Jadwal Kuliah               | Mahasiswa, Sistem         | Decision Jadwal kuliah tersedia? dengan guard [tersedia] dan [belum_tersedia].                                                                      |
| 6   | Lihat Kalender Akademik | SIA-UC06                          | Civitas Akademika, Sistem | Decision Kalender akademik tersedia? dengan guard [tersedia] dan [belum_tersedia].                                                                  |
| 7   | Lihat KHS               | SIA-UC08                          | Mahasiswa, Sistem         | Decision Data KHS ditemukan? dan Nilai sudah dipublikasikan?                                                                                        |
| 8   | Proses Keputusan KRS    | Proses Keputusan KRS              | Dosen Wali, Sistem        | Decision Ada pengajuan KRS yang menunggu? dan Keputusan dan catatan lengkap?                                                                        |
| 9   | Unduh Bukti KRS         | SIA-UC04                          | Mahasiswa, Sistem         | Decision Bukti berhasil disiapkan? dengan guard [berhasil] dan [gagal].                                                                             |

### D. Analisis

1. Keterlacakan ke skenario. Setiap action pada diagram memakai kata kerja dan objek yang sama dengan bunyi langkah pada tabel skenario pertemuan 5, sehingga sumber langkahnya mudah ditunjuk. Action yang berasal dari use case lain diberi rujukan ID, misalnya (dari LAB-UC04), (dari LAB-UC05), dan (dari LAB-UC12).
2. Include dan extend. Include digambar sebagai action wajib pada alur utama (Periksa ketersediaan pada peminjaman dan Periksa kondisi peralatan pada pengembalian). Extend digambar sebagai cabang bersyarat dengan condition yang sama dengan diagram pertemuan 4, yaitu [ya, memilih cetak].
3. Use case yang tidak dibuatkan activity sendiri. LAB-UC04 dan LAB-UC12 tercakup sebagai action include pada activity induknya, sedangkan LAB-UC08, UC09, dan UC10 tercakup sebagai cabang varian pada Activity Kelola Data Peralatan.
4. Pembagian swimlane. Action aktor ditempatkan pada swimlane aktor yang melakukannya, dan respon sistem pada swimlane Sistem. Kepala Laboratorium hanya muncul pada Activity Lihat Laporan Peminjaman (LAB-UC07) dan tidak muncul pada Activity Peminjaman maupun Pengembalian, karena fungsinya bukan bagian dari kedua alur tersebut. Mahasiswa tidak digambar pada Activity Proses Keputusan Peminjaman karena pada skenario LAB-UC06 mahasiswa tidak melakukan langkah apa pun.
5. Fork dan join. Fork dan join dipakai pada Activity Pengembalian karena pemeriksaan kondisi fisik dan pemeriksaan kelengkapan aksesoris tidak saling bergantung. Join memastikan keputusan akhir baru diambil setelah kedua pemeriksaan selesai; proses paralel tidak disatukan dengan merge karena merge tidak menunggu proses lain selesai.
6. Decision, guard, dan merge. Setiap alur keluar decision diberi guard dalam kurung siku yang saling lepas dan menutup semua kemungkinan, misalnya [tersedia] dan [tidak_tersedia]. Cabang yang tidak kembali ke alur utama bermuara ke activity final node dengan keadaan akhir yang jelas, misalnya pesan penolakan atau pemberitahuan.
7. Kendala dan perbaikan. Kesalahan yang paling sering terjadi adalah guard yang belum lengkap, cabang yang menggantung, dan action yang salah swimlane. Karena itu seluruh diagram diperiksa dengan checklist penilaian sebelum diekspor ke PNG.

### E. Kesimpulan

Berdasarkan praktikum pertemuan 6, dapat disimpulkan bahwa activity diagram menggambarkan langkah-langkah pada tabel skenario sebagai alur yang utuh dari initial node sampai activity final node. Skenario Normal menjadi alur utama, Skenario Alternative menjadi cabang decision dengan guard, dan pembagian aktor pada tabel skenario menjadi swimlane, sehingga tanggung jawab setiap action terbaca dari partisinya.

Penggunaan fork dan join pada Activity Pengembalian menunjukkan cara memodelkan dua pemeriksaan yang berjalan paralel dan harus selesai bersama sebelum alur dilanjutkan. Dengan menelusuri setiap action ke tabel skenario dan memeriksa hasilnya dengan checklist, ketujuh activity diagram LAB dan activity diagram SIA yang dibuat menjadi konsisten dengan diagram use case pertemuan 4 dan skenario pertemuan 5.