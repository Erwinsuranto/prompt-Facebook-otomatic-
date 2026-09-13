


# 
```

```
# 
```

```
# 
```
uei
```
# 
```
CONTENTPILOT — FIX GOOGLE DRIVE PRODUCTION REDIRECT URI

PERBAIKI MASALAH INI LANGSUNG. JANGAN BERTANYA KEPADA SAYA.

Temuan audit:
- Google OAuth provider sudah terdeteksi/configured.
- Callback endpoint berjalan.
- Masalah: GOOGLE_DRIVE_REDIRECT_URI masih menggunakan:
  http://localhost:4000/api/storage/google_drive/callback
- Production API adalah:
  https://api.contentpilot.biz.id
- Redirect URI production yang benar harus:
  https://api.contentpilot.biz.id/api/storage/google_drive/callback

LAKUKAN:

1. Masuk ke:
   /root/content-pilot

2. Periksa konfigurasi environment production.

3. Ubah GOOGLE_DRIVE_REDIRECT_URI menjadi TEPAT:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback

4. Pastikan tidak ada konfigurasi lain yang memaksa redirect URI kembali ke localhost.

5. Periksa source code untuk memastikan redirect URI dibaca dari environment dan tidak hardcoded ke localhost.

6. Jika ada dokumentasi/config contoh yang jelas-jelas masih menunjuk localhost untuk production, perbaiki dokumentasinya agar konsisten dengan production. Jangan mengubah hal yang tidak berkaitan.

7. Pastikan Google OAuth authorization URL menggunakan redirect URI production tersebut.

8. Pastikan callback endpoint tetap:
   /api/storage/google_drive/callback

9. Pastikan URL production:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback

10. Restart HANYA service yang memang perlu agar perubahan environment aktif:
    - content-pilot-api.service
    - content-pilot-worker.service

    Jangan restart Caddy dan jangan restart service lain kecuali benar-benar diperlukan.

11. Setelah itu lakukan verifikasi:
    - API active/running
    - Worker active/running
    - Google provider configured = YES
    - redirect URI = production
    - callback endpoint = PASS
    - connect endpoint = PASS/expected auth response
    - tidak ada localhost redirect pada production OAuth flow
    - tidak ada secret/token yang ditampilkan

12. Jalankan regression:
    pnpm typecheck
    pnpm lint
    pnpm test
    pnpm build

13. Jika Google Cloud Console masih belum memiliki Authorized Redirect URI production, JANGAN mengarang hasil.
    Laporkan secara jelas bahwa satu-satunya langkah eksternal yang tersisa adalah menambahkan:
    https://api.contentpilot.biz.id/api/storage/google_drive/callback
    ke Authorized redirect URIs Google OAuth Client.
    Jangan meminta saya memilih apa pun; cukup laporkan sebagai BLOCKED_EXTERNAL jika memang itu satu-satunya hambatan.

ATURAN:
- Jangan bertanya.
- Jangan menunggu approval.
- Perbaiki semua yang bisa diperbaiki langsung di VPS.
- Jangan commit.
- Jangan push.
- Jangan mengubah database/schema.
- Jangan mengubah Caddy.
- Jangan menampilkan secret.
- Jangan melakukan login Google menggunakan akun saya.
- Jangan melakukan tindakan destruktif.

LAPORAN AKHIR:
1. Perubahan yang dilakukan
2. Google OAuth status
3. Redirect URI sebelum/sesudah
4. Service status
5. typecheck
6. lint
7. test
8. build
9. Jika masih BLOCKED_EXTERNAL, jelaskan tepat apa yang harus dilakukan di Google Cloud Console.

STOP setelah selesai.
```
# 
```
CONTENTPILOT — APPLY GOOGLE OAUTH ENV ONLY

Google OAuth secret sudah saya set di production .env.

Lakukan hanya langkah berikut:

1. Pastikan API dan Worker membaca .env production terbaru.
2. Restart HANYA:
   - content-pilot-api.service
   - content-pilot-worker.service

3. Jangan restart:
   - content-pilot-web.service
   - Caddy
   - service lain

4. Jangan mengubah source code.
5. Jangan mengubah database/schema/migration.
6. Jangan commit.
7. Jangan push.
8. Jangan mengubah GitHub.
9. Jangan menampilkan nilai secret, token, client secret, atau credential apa pun.

Setelah restart, verifikasi:
- API active/running
- Worker active/running
- Google OAuth provider = configured/YES
- Google Client ID = SET/EMPTY
- Google Client Secret = SET/EMPTY
- Google Redirect URI = SET/EMPTY
- API health/readiness = PASS/FAIL

Jika Google masih NOT CONFIGURED, jangan memperbaiki apa pun. Laporkan penyebabnya dan STOP.

LAPORKAN HASIL SAJA.
```
