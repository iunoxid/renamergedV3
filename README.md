# Renamerged

Selamat datang di **Renamerged**! Aplikasi ini adalah solusi praktis untuk mengelola file PDF, terutama dokumen pajak atau transaksi bisnis. Renamerged (singkatan dari *Rename-Merged*) dirancang untuk mengotomatisasi proses *rename* dan *merge* file PDF berdasarkan informasi seperti ID TKU Penjual dan Nama Lawan Transaksi, sehingga dokumen Anda tersusun rapi tanpa kerja manual yang melelahkan.

Renamerged hadir dengan GUI modern yang intuitif, mendukung kustomisasi nama file, dan fitur-fitur yang memudahkan pengelolaan dokumen. Berikut informasi lebih lanjut tentang apa yang Renamerged tawarkan.

<img width="860" height="616" alt="image" src="https://github.com/user-attachments/assets/c04e5ad7-982c-47bb-9037-9efd24e6327a" />


## Apa Itu Renamerged?

Renamerged adalah alat efisien untuk mengelola file PDF dengan fitur berikut:

- **Rename Otomatis**: Membaca isi PDF, mengambil informasi seperti ID TKU Penjual (22 digit) dan Nama Lawan Transaksi, lalu mengganti nama file sesuai kebutuhan Anda.
- **Merge File PDF**: Menggabungkan PDF dengan ID TKU Penjual dan Nama Lawan Transaksi yang sama menjadi satu file (opsional).
- **Organisasi File**: Menyimpan hasil di folder `ProcessedPDFs` (atau folder pilihan Anda), diorganisir berdasarkan ID TKU Penjual.

Aplikasi ini sangat cocok untuk Anda yang sering menangani dokumen pajak, transaksi bisnis, atau file PDF lainnya yang perlu dirapikan secara otomatis.

## Fitur Unggulan

- **Modern UI dengan Card-Based Design**: Antarmuka grafis yang intuitif dengan card layout, Slate color palette, Inter font, dan desain yang responsif dan modern.
- **Pengaturan yang Dapat Disembunyikan**: Panel pengaturan proses dapat di-expand/collapse dengan tombol chevron untuk UI yang lebih bersih dan tidak berantakan.
- **Real-time PDF Counter**: Counter otomatis yang mendeteksi jumlah file PDF di folder input secara real-time dengan debouncing untuk performa optimal.
- **Mode Pemrosesan Fleksibel**: Pilih "Rename Saja" (tanpa merge) atau "Rename dan Merge" (rename PLUS merge file yang sama).
- **Kustomisasi Nama File Draggable**: Pada mode "Rename Saja", pilih dan atur urutan komponen nama file (Nama Lawan Transaksi, Tanggal Faktur Pajak, Referensi, Nomor Faktur Pajak) dengan drag & drop.
- **Smart Filename Management**: Otomatis memotong referensi yang terlalu panjang dengan visual delimiter `{}` untuk menjaga kompatibilitas Windows.
- **Real-time Settings Persistence**: Pengaturan user (tema, mode, separator, urutan komponen, dll) disimpan otomatis secara real-time dengan throttling system untuk performa optimal.
- **Advanced Error Handling**: Pesan error yang jelas dengan solusi praktis untuk berbagai masalah umum (permission denied, file not found, memory issues, dll).
- **Filename Length Warning**: Peringatan otomatis jika nama file terlalu panjang dengan opsi penyesuaian otomatis.
- **Pratinjau File PDF**: Lihat daftar file PDF sebelum diproses untuk memastikan file yang tepat.
- **Organisasi File Otomatis**: Hasil disimpan di folder `ProcessedPDFs`, diorganisir berdasarkan ID TKU Penjual.
- **Validasi File PDF**: Memeriksa file PDF untuk memastikan tidak ada yang korup sebelum diproses.
- **Kustomisasi Tema**: Pilih antara *Dark mode* atau *light mode* untuk kenyamanan visual dengan color palette yang konsisten.
- **Logging Komprehensif**: Log aktivitas disimpan di `misc/log.txt` untuk memudahkan debugging.
- **Tombol Donasi**: Dukung pengembangan proyek ini dengan donasi via tombol di GUI.
- **Contact Developer**: Tombol "Hubungi Dev" untuk langsung menghubungi developer melalui Telegram jika ada kendala.

## Sistem Persyaratan

Untuk menjalankan source code:

- **Python**: Versi 3.8 atau lebih baru.

- **Library**: Lihat `requirements.txt`. Instal dengan:

  ```bash
  pip install -r requirements.txt
  ```

- **Sistem Operasi**: Windows 10 atau lebih baru (versi macOS/Linux mungkin perlu penyesuaian).

- **RAM**: Minimal 2 GB.

- **Penyimpanan**: Minimal 50 MB ruang kosong untuk aplikasi dan log.

## Struktur Proyek

```
renamerged/
|-- main.py               # entry CLI/GUI
|-- main.pyw              # entry tanpa console
|-- requirements.txt
|-- changelogs.txt
|-- README.md
|-- src/
|   |-- app/
|   |   |-- gui.py                  # bootstrap UI
|   |   `-- __init__.py
|   |-- components/                # komponen UI
|   |   |-- draggable_component.py
|   |   |-- settings_frame.py
|   |   |-- file_selection_frame.py
|   |   |-- status_frame.py
|   |   |-- process_button.py
|   |   |-- progress_bar.py
|   |   |-- header.py
|   |   |-- tooltip.py
|   |   |-- pdf_counter.py
|   |   |-- custom_pdf_dialog.py
|   |   |-- file_input_output.py
|   |   |-- filename_warning_dialog.py
|   |   |-- mode_selection.py
|   |   |-- output_location.py
|   |   |-- file_list.py
|   |   |-- statistics.py
|   |   `-- __init__.py
|   |-- pdf/                      # logic PDF
|   |   |-- pdf_processor.py
|   |   |-- pdf_processor_rename.py
|   |   |-- pdf_utils.py
|   |   `-- __init__.py
|   `-- utils/                    # utilitas umum
|       |-- styles.py
|       |-- settings_manager.py
|       |-- selection_handler.py
|       |-- filename_checker.py
|       |-- utils.py
|       `-- __init__.py
`-- old/                        # versi lama (legacy scripts)
    |-- renamerged.py
    `-- rename.py
```
## Cara Pakai

1. **Clone Repository**:

   ```bash
   git clone https://github.com/iunoxid/renamerged
   cd renamerged
   ```

2. **Instal Dependensi**: Pastikan Python terinstal, lalu instal dependensi:

   ```bash
   pip install -r requirements.txt
   ```

3. **Jalankan Aplikasi**: Jalankan aplikasi tanpa jendela CMD:
   
   ```bash
   python main.py
   ```
   atau 
   
   ```bash
   Klik 2x pada file "main.pyw"
   ```

5. **Gunakan Aplikasi**:

   - Pilih mode pemrosesan: "Rename Saja" atau "Rename dan Merge".
   - Jika memilih "Rename Saja", centang komponen nama file (Nama Lawan Transaksi, Tanggal Faktur Pajak, dll.) dan atur urutannya dengan drag & drop atau panah ←/→.
   - Klik "Browse" untuk pilih folder input PDF.
   - Lihat counter PDF yang terdeteksi secara real-time.
   - Preview file PDF yang akan diproses.
   - (Opsional) Pilih folder output (default: `ProcessedPDFs`).
   - (Opsional) Ganti tema (*Dark/light mode*) via tombol di header.
   - (Opsional) Collapse/expand pengaturan dengan tombol chevron untuk UI yang lebih bersih.
   - Klik "Mulai Proses" untuk memulai (tombol berada di samping browse buttons).
   - Setelah selesai, klik "Buka Folder Hasil" untuk melihat hasil.

## Contoh Penggunaan

### File Awal:

- `dokumen1.pdf`: ID TKU = `1234567890123456789012`, Nama = `PT ABC`, Nomor Faktur = `123456`, Tanggal = `01-01-2025`.
- `dokumen2.pdf`: ID TKU = `1234567890123456789012`, Nama = `PT ABC`, Nomor Faktur = `123457`, Tanggal = `02-01-2025`.
- `dokumen3.pdf`: ID TKU = `9876543210987654321098`, Nama = `PT XYZ`, Nomor Faktur = `123458`, Tanggal = `03-01-2025`.

### Mode "Rename dan Merge":

- `dokumen1.pdf` dan `dokumen2.pdf` digabung menjadi `PT ABC.pdf` di `ProcessedPDFs/1234567890123456789012/PT ABC.pdf`.
- `dokumen3.pdf` di-rename menjadi `PT XYZ.pdf` di `ProcessedPDFs/9876543210987654321098/PT XYZ.pdf`.

### Mode "Rename Saja" (Komponen: Nama Lawan Transaksi PLUS Nomor Faktur):

- `dokumen1.pdf` menjadi `PT ABC - 123456.pdf` di `ProcessedPDFs/1234567890123456789012/PT ABC - 123456.pdf`.
- `dokumen2.pdf` menjadi `PT ABC - 123457.pdf` di `ProcessedPDFs/1234567890123456789012/PT ABC - 123457.pdf`.
- `dokumen3.pdf` menjadi `PT XYZ - 123458.pdf` di `ProcessedPDFs/9876543210987654321098/PT XYZ - 123458.pdf`.

## Catatan Penting

- **Keamanan File**: Aplikasi ini aman digunakan. Jika Windows Defender memblokir, tambahkan ke *exclusion* di *Virus & Threat Protection*.
- **Real-time User Settings**: Pengaturan user disimpan otomatis secara real-time di file `user_settings.json` dengan throttling system untuk performa optimal. File auto-generate jika tidak ada.
- **Smart Filename Handling**: Aplikasi otomatis menangani referensi panjang dan memberikan peringatan untuk nama file yang melebihi batas Windows (260 karakter).
- **Error Recovery**: Jika terjadi error, aplikasi memberikan pesan yang jelas dengan solusi praktis untuk memperbaiki masalah.
- **Log**: Log aktivitas disimpan di `misc/log.txt` untuk debugging.
- **Kendala**: Jika ada masalah, hubungi saya di [Telegram](https://t.me/iunoin) atau gunakan tombol "Hubungi Dev" di aplikasi.

## Donasi

Jika Renamerged membantu Anda, dukung pengembangan proyek ini dengan donasi via tombol "Donasi" di aplikasi atau melalui QRIS. Donasi Anda sangat membantu saya melanjutkan proyek ini. Terima kasih! 🙏

## Kontribusi dan Feedback

Saya terbuka untuk masukan! Jika ada ide fitur baru atau bug, hubungi saya di [Telegram](https://t.me/iunoin) atau buka *issue* di repository ini.

## Terima Kasih

Terima kasih telah menggunakan Renamerged! Semoga aplikasi ini mempermudah pengelolaan dokumen PDF Anda. Jangan lupa *share* ke teman-teman yang membutuhkan.

## Pertanyaan

Silahkan hubungi saya di [sini](https://t.me/iunoin)

## BONUS

Aku ketika ngoding dan ga ada BUG bee like :

![image](https://github.com/user-attachments/assets/8c819a28-52f1-4503-9469-e81e467ad619)

---

✨ **Dibuat dengan ❤️ oleh [iunoin](https://t.me/iunoin)** ✨

