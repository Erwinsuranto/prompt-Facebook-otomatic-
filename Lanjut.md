


# 
```

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
