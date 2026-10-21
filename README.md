# Maintenance Operations releases

## Desktop 1.21.0 / APK 0.39.0 — 21 Oktober 2026

- [Rilis lengkap, installer perangkat baru dan paket update EXE](https://github.com/iathaariq10/mtc-apk-releases/releases/tag/operations-v1.21.0-apk0.39.0).
- [APK 0.39.0](https://github.com/iathaariq10/mtc-apk-releases/releases/download/operations-v1.21.0-apk0.39.0/app-release.apk), version code 74; 14.461.077 byte.
- SHA-256 `07ec0c25112ce58499408581a44f172b7f5dd84f43ee5ca96c9d7e047c1fd274`.
- Hanya checksheet Shift 1 perlu verifikasi admin. DT dan monitoring Shift 2/3 diterima sistem; Admin Gudang tetap memeriksa pemakaian fisik.
- Update EXE melalui Velopack di aplikasi dengan backup SQLite; APK mengunduh dan memverifikasi paket di aplikasi lalu meminta konfirmasi Android.
- APK 0.38.0 memerlukan satu pemasangan awal untuk mendapatkan updater baru. Update selanjutnya memakai halaman pembaruan di APK baru.

EXE 1.21.0 terpasang; API/manifest 2026.39 aktif, hash publik sesuai. Settings dan form 2026.08.5 tidak berubah. Enam job CI, staging, upgrade EXE/data serta emulator MTC_API35 upgrade/retensi dan 24 skenario UI lulus. Bukan verifikasi HP fisik.

## Operasional

Aktivasi konfigurasi memakai OAuth provider resmi, backup/recovery dan audit
`ota.release.config_deploy`; tidak membuat login aplikasi atau push massal baru.
Form publisher mengenali audit tersebut dan menolak publikasi/notifikasi ganda.
Installer digunakan untuk perangkat baru/pemulihan. APK/paket rilis terbaru berada
di GitHub Releases agar binary tidak digandakan di history Git.

[APK 0.38.0](releases/v0.38.0/app-release.apk) tetap disimpan untuk rollback.
Source, kredensial, database dan data operasional tidak disimpan di repository ini.
