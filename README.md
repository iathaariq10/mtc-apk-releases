# mtc-apk-releases

## Latest artifact: 0.38.0

- [APK 0.38.0](releases/v0.38.0/app-release.apk), version code 73.
- SHA-256: `6b160364f69c5ba2cc43e5e4e4a58c3fe784d475df8618536cad414f6b16710d`; 14,460,993 bytes.
- Material berasal dari master mold. Kode resep dan pilihan cara ukur dihapus dari input.
- Cycle Time, Injection Time dan Cushion tetap pembacaan aktual; tidak diberi target buatan.
- PDF pengamatan hanya muncul bila ada pembacaan. Empat template checksheet lama tetap; lampiran baru A4 portrait.
- Lulus 107 unit/lint, trial 5 UI/PDF + 1 layar 320 dp + 3 kontrak JSON, upgrade release 0.37 ke 0.38 dan startup delapan detik di MTC_API35. Bukan verifikasi HP fisik.

OTA 0.38.0/API 2026.38 aktif dan terverifikasi pada 17 Oktober 2026 setelah Desktop 1.19.0 terpasang. Hash APK publik cocok; Settings dan wire form 2026.08.5 tetap identik. Transaksi menambah satu release dan satu audit tanpa mengubah data bisnis, membuat login aplikasi, atau mengirim push baru.

## Operasional

Deployment konfigurasi provider memakai audit `ota.release.config_deploy`, backup,
uji transaksi dan rollback. Tidak membuat login aplikasi atau push baru. Publisher
mengenali audit tersebut agar tidak melakukan aktivasi/notifikasi ganda.

[APK 0.37.0](releases/v0.37.0/app-release.apk) disimpan untuk rollback.
Source, kredensial, database dan data operasional tidak disimpan di repository ini.
