<!-- Deskripsi -->
Mahasiswa mengajukan KRS dengan memilih mata kuliah. Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal. Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali. Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan. 

<!-- tabel kebutuhan -->
|  ID   |                              Kebutuhan tugas                             |
|-------|--------------------------------------------------------------------------|
|SIA-R01|                  Mahasiswa dapat melihat jadwal kuliah                   |
|SIA-R02|               Admin akademik dapat mengelola jadwal kuliah               |
|SIA-R03|                      Mahasiswa dapat mengajukan KRS                      |
|SIA-R04|             Sistem memvalidasi KRS sebagai bagian pengajuan              |
|SIA-R05|Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
|SIA-R06|        Dosen wali dapat memproses persetujuan atau penolakan KRS         |

<!-- batas sistem dan aturan -->
Batas dan asumsi: 
•	Pengguna telah terautentikasi. 
•	Data mata kuliah, prasyarat, dan jadwal tersedia. 
•	Validasi gagal menyebabkan pengajuan belum berhasil tersimpan. 
•	Unduh bukti tidak menjadi syarat keberhasilan pengajuan. 
•	KRS tersimpan belum berarti disetujui. 
•	Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas. 
 

<!-- tabel identifikasi -->
|         Aktor        |                    Tujuan terhadap sistem                      |
|----------------------|----------------------------------------------------------------|
|       Mahasiswa      |         Melihat jadwal, mengajukan KRS, mengunduh bukti        |
|     admin akademik   |                       Mengelola jadwal                         |
|      dosen wali      |                   Memproses persetujuan KRS                    |


<!-- tabel susnan katalog use case -->
|   ID   |          Nama use case          |        Peran dalam model         |
|--------|---------------------------------|----------------------------------|
|SIA-UC01|       Lihat jadwal kuliah       |    Fungsi utama mahasiswa        |
|SIA-UC02|         mengelola jadwal        |  Fungsi utama admin akademik     |
|SIA-UC03|           Ajukan KRS            |    Fungsi utama mahasiswa        |
|SIA-UC04|      Periksa validasi KRS       | Perilaku yang disertakan UC03    |
|SIA-UC05|   unduh bukti pengajuan KRS     |  Tambahan bersyarat pada UC03    |
|SIA-UC06|      Proses keputusan KRS       |     Fungsi utama dosen wali      |



<!-- relasi include -->
LAB-UC03 «include» LAB-UC04 
Alasan: Pengajuan KRS harus diperiksa validitasnya agar sesuai dengan ketentuan akademik.

<!-- relasi extend -->
LAB-UC05 «extend» LAB-UC03 
Extension point: Bukti pengajuan tersedia. 
Kondisi: [mahasiswa memilih unduh]. 
Alasan:.pengajuan tetap berhasil tanpa diunduh.