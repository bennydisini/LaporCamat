Nama Aplikasi : Portal Pengaduan Masyarakat
Tujuan        : Platform digital terpadu untuk masyarakat dalam mengajukan, melacak, dan mengevaluasi pengaduan ke tingkat kecamatan, serta menyediakan sistem manajemen, disposisi, dan pelaporan real-time bagi aparatur kecamatan.

FITUR UTAMA:

Portal Publik (Pengajuan tanpa login, auto-generate Nomor Tiket, Upload Lampiran)

Modul Pelacakan Publik (Cek status berdasarkan Nomor Tiket)

Modul Verifikasi & Disposisi (Untuk Operator mengarahkan ke Petugas terkait)

Dashboard Monitoring (Statistik total, diproses, selesai, metrik kinerja)

Manajemen Pengguna (Hak akses: Admin, Operator, Petugas, Pimpinan)

Modul Laporan & Audit (Ekspor data, log aktivitas transparan)

Survei Kepuasan (Rating & Ulasan pasca penyelesaian)

ARSITEKTUR DATABASE (Google Sheets):
Sheet: users
Kolom: id, username, password, role, name, created_at

Sheet: pengaduan
Kolom: id, tiket, nik, nama_pelapor, telepon, kategori, deskripsi, lokasi, lampiran_url, status, petugas_id, created_at, updated_at

Sheet: tindak_lanjut
Kolom: id, tiket_id, user_id, catatan, status_baru, created_at

Sheet: survei
Kolom: id, tiket_id, rating, ulasan, created_at

Sheet: audit_log
Kolom: id, user_id, aksi, detail, created_at

DAFTAR ACTION API:

"login"           : Autentikasi pengguna aparatur (Admin/Operator/Petugas/Pimpinan)

"getAll"          : Mengambil data pengaduan dengan dukungan filter (status, kategori, tanggal)

"create"          : Menambah pengaduan baru dari masyarakat (termasuk upload media) & generate tiket

"update"          : Mengubah data pengaduan, verifikasi, dan disposisi (memicu penambahan log dan tindak lanjut)

"delete"          : Menghapus data pengaduan (Hanya Admin)

"trackTicket"     : Mengambil detail pengaduan beserta riwayat tindak lanjut berdasarkan Nomor Tiket (Untuk publik)

"getStats"        : Mengambil rekapitulasi data untuk Dashboard Monitoring

"submitSurvei"    : Mengirimkan penilaian dari pelapor untuk pengaduan yang berstatus Selesai

ROLE & HAK AKSES:

Admin     : Akses Penuh (CRUD semua data, Kelola Pengguna, Pengaturan, Audit Log)

Operator  : Verifikasi awal, Filter, Disposisi tiket ke Petugas Penanganan

Petugas   : Melihat disposisi, update progress penanganan, dan penyelesaian

Pimpinan  : View-only dashboard, melihat Laporan, Statistik, & Audit Log

Publik    : Hak akses terbatas (Submit pengaduan, Lacak Tiket, Isi Survei)# LaporCamat
