LUXE POINT V4.3

Fitur baru:
1. Admin bisa mengatur stok Robux dari dashboard.
2. Admin bisa menambah, mengedit, mengaktifkan/nonaktifkan, dan menghapus paket Robux.
3. Admin mengatur metode Gamepass/Instan, jumlah Robux, harga, harga coret, badge, dan urutan.
4. Website customer mengambil paket dan stok langsung dari Supabase.
5. Order memakai RPC server-side: harga/Robux diambil dari paket yang disetting admin, jadi customer tidak bisa mengganti harga lewat HTML.
6. Setelah order dibuat, customer mendapat Order ID dan Order ID otomatis dikirim ke WhatsApp.
7. Customer bisa cek status order dengan Order ID.
8. Customer hanya bisa memberi rating jika order sudah completed; satu Order ID hanya boleh satu rating.
9. Rating masuk ke admin untuk diverifikasi/tampilkan/sembunyikan/hapus.
10. Rating yang disetujui dapat tampil di website customer.
11. Manajemen kode promo tetap tersedia.

INSTALL:
A. Supabase
1. Buka Supabase > SQL Editor.
2. Jalankan isi file SUPABASE-V4.sql.
3. Pastikan tabel/function berikut exposed di Integrations > Data API jika dashboard Supabase kamu menampilkan API DISABLED:
   - store_settings
   - products
   - promos
   - order_ratings
   - orders (sesuai setup orders sebelumnya)
   - function create_public_order
   - function get_public_order_status
   - function submit_order_rating
4. Pastikan user admin sudah ada di admin_users seperti setup sebelumnya.

B. Website
Upload isi folder luxe-point ke root repository GitHub/Netlify:
index.html
admin/index.html
admin/dashboard.html
admin/reset-password.html

C. Admin
Buka /admin/ lalu login.
Di Dashboard:
- Pengaturan Toko > Stok Robux
- Tambah/Edit Paket
- Manajemen Kode Promo
- Order > ubah status
- Rating & Testimoni > tampilkan/sembunyikan/hapus

CATATAN:
- Stok adalah stok global yang dikelola manual admin. Order belum otomatis mengurangi stok ketika dibuat.
- Rating baru tampil di website setelah admin menekan Tampilkan.
- Order yang bisa diberi rating harus berstatus completed.
- Jika menggunakan Netlify, update Supabase Auth URL Configuration ke domain Netlify untuk login/reset password.


V4.1 FIX: Tombol order sekarang mengarahkan halaman langsung ke WhatsApp +62 895-1978-1533 setelah Order ID berhasil dibuat, sehingga tidak bergantung pada popup browser. Kolom kode promo tetap tampil di modal order; kode promo aktif dibuat dari dashboard admin.


V4.3 FIX:
- Menambahkan promo LUXEPOINTOPENING 5% (seed SQL, 20 hari sejak SQL dijalankan).
- Customer sekarang dapat memakai salah satu dari beberapa kode promo aktif, bukan hanya promo pertama.
- Tombol produk sekarang bertuliskan Order Product →. Jika stok admin tidak cukup, sistem tetap mencegah order dan menawarkan Tanya Stok via WhatsApp.
- Menambahkan grant sequence untuk insert promo/product/rating pada konfigurasi Data API terbaru.
