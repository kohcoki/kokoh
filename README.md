# Kokoh (MOISTALIMA)

Aplikasi POS dan Inventory untuk produsen **MOISTALIMA** yang melayani mitra distributor, toko, reseller, serta penjualan langsung ke customer. Sistem ini perlu mendukung skema **cashback** mitra berdasarkan jumlah pengambilan atau penjualan barang.

## Fitur Utama
- Manajemen master data: produk, kemasan/satuan, kategori, pelanggan, mitra, gudang.
- Stok gudang tunggal dengan mutasi masuk/keluar dan pelacakan batch (opsional).
- Penjualan: transaksi POS untuk customer langsung dan penjualan ke mitra.
- Pengiriman: Surat Jalan untuk distribusi barang.
- Penagihan: Invoice Penjualan.
- Program cashback mitra berdasarkan kuantitas/volume.
- Laporan: stok, penjualan, penagihan, dan rekap cashback mitra.

## Dokumen yang Dicetak
- **Purchase Order (PO)**
- **Surat Jalan**
- **Invoice Penjualan**

## Alur Kerja Ringkas
1. Buat master data produk, mitra (distributor/toko/reseller), dan customer langsung.
2. Atur aturan cashback berdasarkan kuantitas atau omzet.
3. Proses penjualan ke mitra atau customer langsung.
4. Cetak Surat Jalan untuk pengiriman.
5. Terbitkan Invoice Penjualan.
6. Hitung dan terapkan cashback mitra sesuai periode.

Lihat detail kebutuhan di `docs/requirements.md`.
