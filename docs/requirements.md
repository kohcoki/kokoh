# Kebutuhan Sistem POS & Inventory (MOISTALIMA)

Dokumen ini merangkum kebutuhan fungsional untuk produsen **MOISTALIMA** yang melayani mitra distributor, toko, reseller, dan penjualan langsung kepada customer, termasuk skema **cashback** mitra berdasarkan jumlah pengambilan atau penjualan barang.

## Modul Master Data
- Produk: SKU, nama, kategori, kemasan/satuan, harga pokok, harga jual, pajak.
- Mitra: distributor, toko, reseller (tier/level, alamat, kontak, termin pembayaran).
- Customer langsung: identitas, alamat, kontak.
- Gudang/Lokasi: alamat gudang dan pengaturan stok.

## Modul Inventory
- Stok gudang tunggal (untuk saat ini).
- Mutasi stok masuk/keluar (produksi, penjualan, penyesuaian).
- Riwayat pergerakan stok per produk.
- Batch/lot dan tanggal kedaluwarsa (jika diperlukan).

## Modul Produksi/Stok Masuk
- Pencatatan hasil produksi sebagai stok masuk.
- Biaya produksi per batch (opsional).

## Modul Penjualan (POS)
- Transaksi POS dengan barcode/lookup produk.
- Tipe transaksi: penjualan ke mitra dan penjualan langsung ke customer.
- Diskon per item dan per transaksi.
- Metode pembayaran (tunai, kartu, transfer).
- Cetak struk/nota transaksi.

## Modul Pengiriman
- Pembuatan Surat Jalan dari transaksi penjualan.
- Status pengiriman (draft, dikirim, diterima).

## Modul Penagihan
- Penerbitan Invoice Penjualan.
- Termin pembayaran dan jatuh tempo.
- Status invoice (draft, terkirim, lunas).

## Alur Utama PO → Surat Jalan → Invoice
Alur ini menjadi siklus utama untuk mengelola stok masuk dari pemasok (Purchasing) maupun pesanan keluar ke pelanggan besar (B2B Sales).

### Purchase Order (PO) - Dokumen Pemesanan
- Diterbitkan di awal oleh pembeli kepada penjual sebagai komitmen resmi pembelian.
- Fungsi inventory: PO berstatus "On Order/Pending" sehingga stok fisik belum bertambah, tetapi tercatat sebagai expected stock.
- Data kunci: nomor PO unik, daftar item, kuantitas, harga satuan, dan syarat pembayaran.

### Surat Jalan - Dokumen Logistik
- Dibuat saat barang dikirim dan dibawa bersama fisik barang sebagai bukti pengiriman.
- Fungsi inventory: saat Surat Jalan diterima dan dikonfirmasi, stok fisik bertambah (pembelian) atau berkurang (penjualan).
- Verifikasi: sistem mencocokkan jumlah barang di Surat Jalan dengan PO untuk mendeteksi selisih (partial delivery).
- Data kunci: nomor Surat Jalan, referensi nomor PO, detail kuantitas barang, dan tanda tangan penerima.

### Invoice (Faktur) - Dokumen Penagihan
- Diterbitkan oleh penjual setelah barang diterima untuk menagih pembayaran.
- Fungsi keuangan: mencatat utang (jika kita pembeli) atau piutang (jika kita penjual).
- Finalisasi: invoice merujuk pada nomor Surat Jalan dan PO untuk memastikan nominal tagihan sesuai barang yang diterima.
- Data kunci: nomor invoice, total tagihan, rincian pajak (PPN), diskon, dan batas waktu pembayaran (due date).

### Rekomendasi Fitur
- Auto-filling: pembuatan invoice menarik data otomatis dari Surat Jalan atau PO terpilih.
- Status tracking: label status seperti "Partial Received" saat barang datang sebagian.
- 4-way matching: validasi kesesuaian antara PO, Surat Jalan, Barang Fisik, dan Invoice sebelum pembayaran.

## Modul Cashback Mitra
- Aturan cashback berdasarkan kuantitas/omzet per periode.
- Tingkatan cashback per jenis mitra (distributor/toko/reseller).
- Rekap cashback per mitra dan status pencairan.

## Laporan
- Laporan stok & kartu stok.
- Laporan penjualan per periode (mitra vs customer langsung).
- Laporan piutang mitra.
- Laporan rekap cashback mitra.

## Dokumen Cetak
- Template Purchase Order (PO), Surat Jalan, dan Invoice Penjualan.
- Penomoran otomatis berdasarkan konfigurasi (prefix, format, urutan).
- Dukungan logo perusahaan dan tanda tangan digital.

## Integrasi dan Akses
- Hak akses per peran (admin, kasir, gudang, akuntansi).
- Audit log aktivitas pengguna.

## Data yang Diperlukan dari Pengguna
- Detail proses bisnis (alur distribusi, format dokumen).
- Template dokumen yang diinginkan (logo, layout).
- Aturan cashback per mitra dan periode.
- Daftar metode pembayaran dan pajak.
