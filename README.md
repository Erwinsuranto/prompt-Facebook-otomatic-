# prompt-Facebook-otomatic-

# 
```


````
# 
```


````
# 
```


````
# 
```


````
# 
```


````
# 
```


````
# 
```

AUDIT + WORK LOG REPOSITORY — WAJIB DITERAPKAN

Kerjakan audit/verifikasi sesuai instruksi sebelumnya, tetapi mulai sekarang SEMUA HASIL KERJA AI WAJIB disimpan sebagai artefak di dalam repository agar dapat diaudit tanpa screenshot.

Repository/project:
 /root/content-pilot

Buat folder khusus:

.ai-work/

Struktur:

.ai-work/
├── README.md
├── 001-google-drive-oauth-audit/
│   ├── RESULT.md
│   ├── AUDIT.md
│   └── COMMANDS.md
├── 002-readonly-full-audit/
│   ├── RESULT.md
│   ├── AUDIT.md
│   └── COMMANDS.md
└── 003-readonly-convention/
    ├── RESULT.md
    ├── AUDIT.md
    └── COMMANDS.md

ATURAN PENTING:

1. Setiap task/audit yang kamu kerjakan harus mempunyai folder sendiri dengan nomor berurutan.

2. RESULT.md
   Berisi hasil akhir yang mudah dibaca:
   - status: PASS / FAILED / BLOCKED
   - tanggal/waktu
   - tujuan task
   - perubahan yang dilakukan
   - file yang diperiksa
   - hasil verifikasi
   - masalah yang ditemukan
   - langkah berikutnya
   - kesimpulan

3. AUDIT.md
   Berisi audit teknis secara detail:
   - kondisi sebelum
   - kondisi sesudah
   - konfigurasi yang diperiksa
   - command yang dijalankan
   - output penting
   - alasan setiap keputusan
   - risiko/regresi yang ditemukan
   - hal yang sengaja TIDAK diubah

4. COMMANDS.md
   Berisi command yang benar-benar dijalankan selama task.
   Jangan menuliskan command yang hanya direncanakan tetapi tidak pernah dijalankan.

5. JANGAN menyimpan secret/token/password asli di .ai-work/.
   Jika output terminal mengandung credential, API key, OAuth token, client secret, password, cookie, atau credential lain, REDACT menjadi:
   [REDACTED]

6. Jangan memasukkan isi .env asli ke file hasil audit.
   Boleh mencatat nama variable dan statusnya, contoh:
   GOOGLE_CLIENT_ID=<configured>
   GOOGLE_CLIENT_SECRET=<configured>
   tetapi jangan tulis nilainya.

7. Jika task FAILED atau BLOCKED, tetap buat RESULT.md.
   FAILED/BLOCKED berarti objek yang diaudit gagal/belum dapat diverifikasi.
   Jangan menghapus hasil gagal agar histori audit tetap tersedia.

8. Jangan mengklaim PASS hanya karena command berhasil dijalankan.
   PASS hanya jika kriteria keberhasilan benar-benar terbukti.

9. Setiap task baru harus merujuk ke task sebelumnya jika memang berkaitan.

10. Update .ai-work/README.md dengan index seluruh task:
    - nomor
    - nama task
    - status
    - tanggal
    - ringkasan
    - lokasi RESULT.md

11. Jangan mengubah source code hanya demi membuat audit terlihat PASS.
    Jika menemukan masalah, laporkan masalahnya terlebih dahulu dan hanya lakukan perubahan jika memang termasuk scope pekerjaan.

12. Setelah selesai, jalankan git status dan pastikan artefak audit yang baru memang ada.

13. Commit dan push hanya jika instruksi pekerjaan memang meminta commit/push.
    Jika saya meminta commit/push, gunakan commit message yang jelas dan pastikan tidak ada secret ikut ter-commit.

14. JANGAN menjalankan test/integration test Gorouter.app.
    Jika test suite otomatis memasukkan Gorouter.app, skip/exclude test tersebut.
    Provider NVIDIA dan TokenHarbor.ai boleh diverifikasi sesuai kebutuhan.

15. Untuk audit Google Drive/OAuth:
    - jangan mencetak OAuth token/refresh token
    - jangan menyimpan credential mentah
    - dokumentasikan hanya status/configuration yang diperlukan
    - jika authorization URL perlu dicatat, redact client secret/token dan jangan menyimpan credential sensitif.

16. Setiap kali kamu selesai mengerjakan task, SELALU tampilkan:
    WORK RESULT:
    Task: <nomor dan nama>
    Status: PASS/FAILED/BLOCKED
    Result file: .ai-work/<folder>/RESULT.md
    Audit file: .ai-work/<folder>/AUDIT.md
    Commands: .ai-work/<folder>/COMMANDS.md

17. Jika ada perubahan file project, catat semua file yang berubah di RESULT.md dan AUDIT.md.

18. Sebelum menyatakan selesai, pastikan file artefak sudah benar-benar dibuat di repository, bukan hanya dijelaskan di chat.

Tujuan utama:
Saya ingin seluruh pekerjaan, audit, command, hasil verifikasi, dan masalah terdokumentasi di repository sehingga pada percakapan berikutnya saya cukup meminta AI lain/assistant untuk membaca folder .ai-work tanpa perlu saya mengirim screenshot terminal lagi.

Sekarang terapkan sistem work-log ini pada task yang sedang kamu kerjakan, buat/update .ai-work/README.md dan buat artefak hasil untuk task saat ini.
````
# 
```
Lakukan AUDIT READ-ONLY menyeluruh terhadap project /root/content-pilot berdasarkan kondisi TERKINI server.

PENTING:
- Jangan mengubah file apa pun.
- Jangan mengubah konfigurasi, database, environment, service, DNS, Cloudflare, OAuth, atau credential.
- Jangan restart service.
- Jangan melakukan git commit/push.
- Jangan mengirim request yang mengubah state.
- Jangan menjalankan test yang dapat membuat/menghapus/mengubah data.
- Jangan menampilkan nilai secret/token/password/client_secret secara lengkap; MASK semua secret.
- Audit harus benar-benar membaca konfigurasi dan source code yang relevan, bukan hanya menyimpulkan dari output sebelumnya.

Tujuan audit:
Memastikan project content-pilot siap digunakan dan integrasi Google Drive OAuth benar-benar konsisten end-to-end.

Periksa minimal:

1. PROJECT STRUCTURE
- Identifikasi frontend, backend/API, worker, storage module, auth/session module, dan konfigurasi yang relevan.
- Pastikan tidak ada konfigurasi ganda yang saling bertentangan.

2. ENVIRONMENT
- Audit /root/content-pilot/.env dan seluruh env yang benar-benar digunakan aplikasi.
- Verifikasi GOOGLE_CLIENT_ID
- Verifikasi GOOGLE_CLIENT_SECRET
- Verifikasi GOOGLE_DRIVE_REDIRECT_URI
- Verifikasi API_HOST/API_PORT
- Verifikasi WEB_BASE_URL
- Verifikasi bahwa runtime benar-benar membaca .env yang sama.
- Cari placeholder seperti REPLACE_WITH_*, <client_id>, example, dummy, atau nilai kosong.
- Jangan tampilkan secret asli.

3. GOOGLE OAUTH
- Telusuri source code yang membuat authorization URL.
- Pastikan client_id berasal dari environment/config yang benar.
- Pastikan redirect_uri yang digunakan code SAMA PERSIS dengan:
  https://api.contentpilot.biz.id/api/storage/google_drive/callback
- Pastikan scope Google Drive sesuai kebutuhan aplikasi.
- Pastikan state OAuth dibuat dan divalidasi dengan benar.
- Pastikan callback menukar authorization code menggunakan client credentials server-side.
- Pastikan access/refresh token disimpan dengan aman.
- Pastikan tidak ada client_secret yang dikirim ke browser/frontend.
- Pastikan tidak ada hardcoded OAuth credential.

4. GOOGLE DRIVE CONNECTION FLOW
Audit endpoint:
- authorization URL
- callback
- connection status
- disconnect jika ada
- storage connection/user mapping

Pastikan alurnya:
UI → authorization URL → Google → callback → token exchange → encrypted token storage → status=connected.

Periksa kemungkinan error:
- invalid_client
- redirect_uri_mismatch
- state mismatch
- token exchange failure
- callback 404
- token tidak tersimpan
- status connected palsu.

5. API / PROXY / CADDY
- Verifikasi aplikasi listen pada interface/port yang benar.
- Verifikasi Caddy/reverse proxy.
- Verifikasi HTTPS.
- Verifikasi upstream localhost:4000 atau target sebenarnya.
- Cari konfigurasi yang menyebabkan API hanya bisa diakses localhost.
- Pastikan public endpoint:
  https://api.contentpilot.biz.id
  mengarah ke service yang benar.

6. CLOUDFLARE
- Audit konfigurasi yang dapat diperiksa dari server.
- Cari potensi konflik Cloudflare ↔ Caddy ↔ HTTPS.
- Pastikan tidak ada konfigurasi yang membuat TLS origin salah.
- Jangan melakukan perubahan Cloudflare.

7. CORS / COOKIE / SESSION
- Audit CORS.
- Pastikan origin production tidak menggunakan wildcard jika credential/cookie diperlukan.
- Audit Secure, HttpOnly, SameSite cookie.
- Pastikan WEB_BASE_URL konsisten.
- Pastikan session tidak rusak karena domain/subdomain berbeda.

8. STORAGE SECURITY
- Audit enkripsi token.
- Pastikan encryption key tersedia dan konsisten.
- Pastikan token Google tidak disimpan plaintext.
- Pastikan token tidak masuk log.
- Pastikan endpoint status tidak membocorkan credential.

9. DATABASE / MIGRATION
- Audit schema/model yang berkaitan dengan Google Drive connection.
- Pastikan tidak ada mismatch antara schema dan source code.
- Jangan menjalankan migration yang mengubah database.

10. SERVICE/RUNTIME
- Identifikasi process/service yang menjalankan API dan worker.
- Periksa apakah process menggunakan environment terbaru.
- Periksa apakah ada process lama yang masih memakai konfigurasi lama.
- Jangan restart apa pun.

11. ROUTES
Audit route yang berkaitan dengan:
- /health
- /api/storage/google_drive/*
- authentication/session
- callback OAuth

Pastikan route benar-benar terdaftar dan tidak hanya disebut dalam dokumentasi.

12. SECURITY
Cari:
- hardcoded secret
- leaked credential
- token di log
- insecure callback
- missing state validation
- open CORS
- insecure cookie
- exposed internal endpoint
- localhost/public URL mismatch
- OAuth misconfiguration.

13. CONSISTENCY CHECK
Bandingkan:
ENV → source code → route → reverse proxy → frontend configuration.

Jika menemukan konfigurasi berbeda, tunjukkan:
A. nilai/config yang ditemukan (secret wajib dimasking)
B. lokasi file
C. konfigurasi yang seharusnya
D. dampaknya.

14. VERIFICATION
Hanya lakukan pemeriksaan READ-ONLY yang aman.
Boleh menggunakan:
- grep
- sed/cat untuk membaca konfigurasi
- git status
- process/service inspection
- route/source inspection
- curl GET/HEAD/read-only terhadap health endpoint bila aman.

Jangan melakukan POST/PUT/PATCH/DELETE ke Google atau aplikasi.
Jangan melakukan OAuth login.
Jangan membuat connection baru.
Jangan mengubah state.

HASIL AKHIR WAJIB dalam format:

=== AUDIT RESULT ===

STATUS:
[READY / NOT READY / BLOCKED]

CRITICAL ISSUES:
1.
2.
3.

WARNINGS:
1.
2.
3.

PASSED:
1.
2.
3.

GOOGLE OAUTH:
- Client ID configured: YES/NO
- Client secret configured: YES/NO
- Redirect URI consistent: YES/NO
- Callback route exists: YES/NO
- State validation: YES/NO
- Token encryption: YES/NO
- Browser exposure risk: YES/NO

PUBLIC API:
- HTTPS: PASS/FAIL
- Reverse proxy: PASS/FAIL
- API health: PASS/FAIL
- CORS: PASS/FAIL
- Cookie/session: PASS/FAIL

CONFIGURATION:
- Placeholder found: YES/NO
- Duplicate/conflicting env: YES/NO
- Runtime using expected env: YES/NO

FILES CHANGED:
MUST be 0.

TESTS THAT WERE RUN:
List only read-only/safe checks.

FINAL DIAGNOSIS:
Jelaskan secara singkat apakah project benar-benar siap untuk langkah login Google Drive berikutnya.

Jika ada masalah, JANGAN memperbaikinya.
Berikan tepat langkah/perintah yang perlu saya lakukan pada tahap berikutnya setelah audit selesai.

````
# 
```
AUDIT HASIL PROMPT TERAKHIR — JANGAN MELAKUKAN PERUBAHAN

Lakukan audit menyeluruh terhadap kondisi project /root/content-pilot berdasarkan pekerjaan yang baru saja dilakukan.

TUJUAN:
Memastikan implementasi Google Drive OAuth, API, HTTPS/Cloudflare, dan konfigurasi environment benar-benar sudah sesuai dan tidak ada pekerjaan yang hanya terlihat selesai tetapi sebenarnya belum berfungsi.

ATURAN PENTING:
1. AUDIT ONLY. Jangan mengubah file apa pun.
2. Jangan menjalankan git commit, git push, atau menghapus data.
3. Jangan mengubah konfigurasi Cloudflare, OpenStack, DNS, firewall, atau VPS.
4. Jangan meminta saya memasukkan credential/secret ke chat.
5. Jangan menampilkan nilai secret/token/client secret secara lengkap. Masking semua credential.
6. Jangan menjalankan atau mengubah test/integration test GoRouter.app.
7. Jangan menyentuh provider lain yang tidak diperlukan untuk audit ini.
8. NVIDIA API dan TokenHarbor.ai boleh diverifikasi jika memang relevan dengan kondisi proxy, tetapi jangan melakukan perubahan terhadapnya.
9. Jangan menganggap konfigurasi benar hanya karena file/env terlihat ada. Verifikasi penggunaan aktual oleh aplikasi.

CHECKLIST AUDIT:

A. PROJECT STATE
- Pastikan project benar-benar /root/content-pilot.
- Periksa git status.
- Identifikasi file yang berubah dari pekerjaan terakhir.
- Pastikan tidak ada perubahan tidak sengaja.
- Periksa package/workspace yang relevan.
- Jangan mengubah apa pun.

B. ENVIRONMENT
Audit /root/content-pilot/.env.
Pastikan variabel Google OAuth yang dibutuhkan memang ada dan terbaca aplikasi:
- GOOGLE_CLIENT_ID
- GOOGLE_CLIENT_SECRET
- GOOGLE_DRIVE_REDIRECT_URI

Pastikan:
- GOOGLE_CLIENT_ID bukan placeholder.
- GOOGLE_CLIENT_SECRET bukan placeholder.
- GOOGLE_DRIVE_REDIRECT_URI sesuai route callback aplikasi.
- Nilai secret jangan ditampilkan penuh.
- Pastikan aplikasi benar-benar membaca variabel tersebut, bukan hanya env memiliki variabelnya.

C. GOOGLE OAUTH
Audit implementasi OAuth Google Drive:
- Cari source code yang membaca GOOGLE_CLIENT_ID / GOOGLE_CLIENT_SECRET.
- Cari endpoint authorization.
- Cari endpoint callback.
- Pastikan authorization URL dibangun menggunakan client ID aktual.
- Pastikan redirect_uri yang dikirim ke Google sama persis dengan redirect URI yang dikonfigurasi aplikasi.
- Pastikan callback dapat menukar authorization code menjadi token.
- Pastikan state OAuth ditangani dengan benar.
- Pastikan scope Google Drive sesuai kebutuhan aplikasi.
- Pastikan access token/refresh token tidak ditulis ke log.
- Pastikan penyimpanan token menggunakan mekanisme encryption/storage yang memang tersedia di project.

D. API / ROUTE
Periksa route:
- /health
- /api/storage/google_drive/callback
- endpoint authorization Google Drive
- endpoint status koneksi Google Drive

Pastikan route benar-benar terdaftar pada server yang sedang dijalankan.

E. SERVER
Periksa proses/service API.
Verifikasi:
- API listen pada port yang benar.
- API_HOST/API_PORT sesuai konfigurasi.
- service tidak crash.
- health endpoint memberikan response yang benar.
- restart terakhir benar-benar menggunakan konfigurasi .env terbaru jika memang restart diperlukan.

Jangan restart atau mengubah service kecuali saya meminta.

F. HTTPS / CLOUDFLARE
Audit secara read-only:
- https://api.contentpilot.biz.id/health
- status HTTP response.
- apakah request mencapai origin.
- apakah ada masalah Cloudflare 521.
- apakah origin/API benar-benar listen.
- apakah konfigurasi reverse proxy Caddy secara logika sudah sesuai.
- pastikan tidak ada asumsi bahwa Cloudflare sudah benar hanya berdasarkan konfigurasi lokal.

Jangan mengubah Cloudflare atau firewall.

G. CADDY / REVERSE PROXY
Audit konfigurasi Caddy:
- domain api.contentpilot.biz.id
- reverse_proxy ke localhost:4000 atau port aplikasi yang sebenarnya.
- TLS configuration.
- pastikan tidak ada konfigurasi yang menyebabkan loop atau salah upstream.
- cek status/config secara read-only.

H. GOOGLE DRIVE CALLBACK
Pastikan callback URL yang digunakan aplikasi konsisten dengan:
https://api.contentpilot.biz.id/api/storage/google_drive/callback

Periksa apakah callback route benar-benar dapat menerima request Google OAuth.

I. FRONTEND / UI
Jika ada UI Settings → Storage → Connect Google Drive:
- pastikan tombol/flow Connect Google Drive menggunakan authorization endpoint yang benar.
- pastikan redirect kembali ke callback.
- pastikan status koneksi dapat dibaca setelah OAuth.
- jangan mengubah UI.

J. SECURITY AUDIT
Cari potensi:
- secret Google masuk git.
- secret masuk source code.
- secret masuk log.
- token OAuth masuk response yang tidak semestinya.
- redirect URI terbuka terhadap open redirect.
- state OAuth tidak divalidasi.
- credential ditampilkan pada endpoint publik.

Jika menemukan masalah, hanya laporkan. Jangan memperbaikinya.

OUTPUT WAJIB:

Berikan laporan dengan format:

1. OVERALL STATUS
PASS / PARTIAL / FAIL

2. PROJECT STATE
- apa yang ditemukan
- apakah ada perubahan tidak diinginkan

3. GOOGLE OAUTH
- Client ID: VALID / PLACEHOLDER / TIDAK TERDETEKSI
- Client Secret: VALID / PLACEHOLDER / TIDAK TERDETEKSI
- Redirect URI: VALID / SALAH / TIDAK TERDETEKSI
- Authorization flow: PASS / FAIL
- Callback: PASS / FAIL
- Token storage: PASS / FAIL

4. API
- Health: PASS / FAIL
- Routes: PASS / FAIL
- Server: PASS / FAIL

5. CADDY / HTTPS / CLOUDFLARE
- Caddy: PASS / FAIL
- HTTPS: PASS / FAIL
- Cloudflare/origin: PASS / FAIL
- 521: YA / TIDAK

6. SECURITY
- temuan keamanan
- tingkat: LOW / MEDIUM / HIGH / CRITICAL

7. MASALAH YANG BENAR-BENAR TERBUKTI
Pisahkan dari dugaan/asumsi.

8. YANG SUDAH BENAR
Daftar bagian yang benar-benar terverifikasi.

9. YANG MASIH HARUS DIPERBAIKI
Hanya daftar masalah yang terbukti.

10. NEXT STEP
Berikan langkah berikutnya secara berurutan.
Jangan melakukan langkah tersebut sekarang.

PENTING:
Jangan mengatakan "sudah selesai" hanya karena konfigurasi terlihat benar.
Audit harus berdasarkan bukti dari source code, konfigurasi, route, proses server, dan response aktual.
Jika sesuatu tidak bisa diverifikasi tanpa credential atau perubahan eksternal, tandai sebagai "TIDAK DAPAT DIVERIFIKASI" dan jelaskan alasannya.

SELESAI SETELAH LAPORAN AUDIT.
Jangan melakukan coding atau perubahan apa pun.

````
# 
```

Lanjutkan dari kondisi sekarang.

Saya sudah mengisi GOOGLE_CLIENT_ID dan GOOGLE_CLIENT_SECRET di /root/content-pilot/.env dengan kredensial OAuth Google yang asli.

Tolong:
1. Jangan mengubah GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, atau GOOGLE_DRIVE_REDIRECT_URI.
2. Baca dan validasi nilai dari /root/content-pilot/.env tanpa menampilkan secret ke output.
3. Restart API content-pilot agar konfigurasi .env terbaca.
4. Pastikan redirect URI yang digunakan adalah:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
5. Pastikan endpoint health berjalan normal.
6. Generate ulang Authorization URL menggunakan client_id yang sekarang sudah asli, bukan placeholder.
7. Jangan mengubah provider lain.
8. Jangan menjalankan atau mengubah test Gorouter.app.
9. Jangan commit/push perubahan apa pun.
10. Setelah Authorization URL berhasil dibuat, tampilkan URL tersebut agar saya bisa membukanya di browser dan melakukan login Google.

Jangan meminta saya mengisi Client ID/Secret lagi karena sudah saya isi di .env.
````
# 
```
Lanjutkan dari kondisi saat ini.

Saya sudah mengisi GOOGLE_CLIENT_ID dan GOOGLE_CLIENT_SECRET menggunakan /root/set-google-creds.py.

Sekarang:
1. Validasi bahwa kedua credential tersimpan dengan benar tanpa menampilkan nilai secret.
2. Restart API content-pilot agar konfigurasi terbaca.
3. Pastikan /health merespons 200.
4. Generate ulang Authorization URL Google Drive menggunakan client_id asli dan redirect_uri:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
5. Jangan ubah provider lain.
6. Jangan menjalankan test GoRouter.app.
7. Jangan melakukan commit/push.
8. Jangan mengubah file yang tidak diperlukan.

Setelah selesai, tampilkan status setiap langkah dan Authorization URL yang siap saya buka di browser untuk login Google Drive. Jika ada error, berhenti dan tampilkan error sebenarnya tanpa menebak.

````
# 
```

Lanjutkan setup Google Drive OAuth untuk project /root/content-pilot.

Kondisi saat ini:
- OAuth Client ID "content pilot google drive" sudah dibuat di Google Cloud.
- Authorized redirect URI sudah diset:
  https://api.contentpilot.biz.id/api/storage/google_drive/callback
- Jangan mengubah provider lain, jangan menjalankan/test Gorouter.app, dan jangan melakukan commit/push.
- Jangan meminta saya mengirim GOOGLE_CLIENT_SECRET ke chat.

Tugas sekarang:
1. Periksa file /root/content-pilot/.env dan pastikan konfigurasi Google Drive memakai:
   GOOGLE_CLIENT_ID=<client ID asli dari Google Cloud>
   GOOGLE_CLIENT_SECRET=<client secret asli dari Google Cloud>
2. Karena secret tidak akan saya kirim melalui chat, berikan perintah/cara paling aman agar saya dapat memasukkan kedua nilai tersebut langsung di VPS tanpa menampilkannya kembali di output.
3. Setelah nilai tersimpan, validasi bahwa format GOOGLE_CLIENT_ID dan GOOGLE_CLIENT_SECRET tidak kosong dan tidak lagi berupa placeholder.
4. Restart API content-pilot agar konfigurasi terbaca.
5. Cek /health dan pastikan API kembali berjalan.
6. Generate authorization URL Google Drive menggunakan redirect URI persis:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
7. Tampilkan hanya authorization URL yang aman untuk saya buka di browser. Jangan tampilkan client secret.
8. Setelah saya menyelesaikan login Google, lanjutkan verifikasi callback dan status koneksi Google Drive.
9. Jangan mengubah file atau konfigurasi lain di luar kebutuhan Google Drive OAuth.

Berhenti setelah authorization URL siap dan beri tahu saya langkah berikutnya.
````
# 
```

Lanjutkan project /root/content-pilot dari kondisi terakhir.

Jangan mengubah provider lain dan jangan menjalankan atau mengaktifkan test Gorouter.app.

Konteks saat ini:
- OAuth Google Drive sudah dibuat di Google Cloud.
- OAuth Client: "content pilot google drive"
- Authorized redirect URI:
  https://api.contentpilot.biz.id/api/storage/google_drive/callback
- API publik: https://api.contentpilot.biz.id
- API internal berjalan di port 4000.
- Google OAuth masih dalam status Testing.
- Test user Google sudah ditambahkan.

Tugas sekarang:
1. Periksa /root/content-pilot/.env dan source code yang terkait Google Drive OAuth.
2. Jangan pernah menampilkan GOOGLE_CLIENT_SECRET atau credential sensitif ke terminal/chat/output.
3. Pastikan konfigurasi OAuth menggunakan:
   GOOGLE_CLIENT_ID
   GOOGLE_CLIENT_SECRET
   GOOGLE_DRIVE_REDIRECT_URI=https://api.contentpilot.biz.id/api/storage/google_drive/callback
4. Jika GOOGLE_CLIENT_ID dan GOOGLE_CLIENT_SECRET belum ada atau masih placeholder, BERHENTI dan minta saya memasukkan nilainya. Jangan menebak.
5. Jika sudah tersedia, validasi konfigurasi tanpa membocorkan secret.
6. Restart API dengan cara yang sesuai dengan project.
7. Verifikasi endpoint health dan endpoint OAuth Google Drive.
8. Buat/gunakan authorization URL Google Drive yang benar dengan redirect URI persis:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
9. Jangan melakukan perubahan pada provider lain.
10. Jangan commit atau push perubahan apa pun.
11. Setelah selesai, laporkan hanya:
   - status konfigurasi
   - status API
   - URL authorization yang aman untuk dibuka di browser (tanpa client secret)
   - langkah berikutnya yang harus saya lakukan.

Jangan meminta saya mengirim client secret ke chat jika sebenarnya sudah tersedia di .env.
````
# 
```
Lanjutkan project /root/content-pilot.

Jangan mengubah provider lain dan jangan menjalankan atau mengubah Gorouter.app.

Kondisi terakhir:
- GOOGLE_CLIENT_ID dan GOOGLE_CLIENT_SECRET sudah dimasukkan ke /root/content-pilot/.env
- OAuth Client Google Drive sudah dibuat
- Authorized redirect URI sudah diset:
  https://api.contentpilot.biz.id/api/storage/google_drive/callback
- Cloudflare sudah diarahkan ke origin VPS
- Caddy/reverse proxy sudah dikonfigurasi untuk api.contentpilot.biz.id -> 127.0.0.1:4000
- Endpoint publik /health sudah diuji
- Redis/Postgres/MinIO sudah berjalan
- Jangan menebak konfigurasi yang belum diketahui.

Sekarang lakukan VERIFIKASI END-TO-END Google Drive saja.

Tujuan:
1. Periksa konfigurasi .env yang diperlukan untuk Google Drive OAuth, tetapi JANGAN menampilkan nilai secret/client secret lengkap.
2. Pastikan callback route benar-benar terdaftar di aplikasi.
3. Pastikan aplikasi berjalan dengan konfigurasi terbaru.
4. Jika perlu restart service, lakukan hanya untuk content-pilot.
5. Buat/ambil authorization URL Google Drive dari implementasi aplikasi yang sudah ada.
6. Verifikasi bahwa redirect URI yang digunakan aplikasi PERSIS:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
7. Jangan membuat route baru jika route yang benar sudah ada.
8. Jangan mengubah arsitektur atau provider lain.
9. Jangan melakukan commit.
10. Jangan menghapus data/storage yang sudah ada.

Setelah pemeriksaan selesai, BERHENTI dan tampilkan:
- status setiap pemeriksaan
- file yang diperiksa/diubah
- command yang dijalankan
- authorization URL jika memang sudah tersedia
- langkah manual berikutnya yang harus saya lakukan di browser.

Jangan melakukan perubahan tambahan sebelum saya mengirim hasil login/authorization Google Drive.

````
# 
```
Lanjutkan implementasi Google Drive OAuth sekarang. Jangan bertanya lagi soal URL—gunakan konfigurasi produksi yang sudah saya tetapkan:

- Production base URL: https://api.contentpilot.biz.id
- OAuth redirect URI: https://api.contentpilot.biz.id/api/storage/google_drive/callback
- API internal tetap berjalan di localhost:4000
- Caddy reverse proxy: api.contentpilot.biz.id -> localhost:4000
- Google Drive OAuth Client: "content pilot google drive"
- Google Cloud project: utility-canto-507016-h9
- Scope yang sudah diizinkan:
  https://www.googleapis.com/auth/drive.file
  https://www.googleapis.com/auth/userinfo.email
  openid

Konteks:
Google Drive API sudah ENABLED, OAuth consent screen sudah Testing, test user sudah ditambahkan, OAuth Web Client sudah dibuat, dan Authorized redirect URI sudah diset ke URL produksi di atas.

Kerjakan SEKARANG langkah berikut secara berurutan:

1. Periksa .env/server/worker dan pastikan GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, GOOGLE_DRIVE_REDIRECT_URI, serta konfigurasi cookie/session yang diperlukan sudah benar. Jangan menampilkan secret ke output.
2. Pastikan Postgres dan Redis sesuai docker-compose yang ada sudah berjalan.
3. Pastikan Caddy memiliki reverse proxy untuk:
   api.contentpilot.biz.id {
     reverse_proxy localhost:4000
   }
   lalu reload Caddy.
4. Restart API + worker setelah konfigurasi selesai agar config/cache terbaca ulang.
5. Verifikasi:
   - API health
   - worker health/status
   - endpoint Google Drive storage
   - konfigurasi provider Google Drive terbaca sebagai configured=true jika memang sudah sesuai.
6. Jangan hanya mengecek file konfigurasi. Lakukan smoke test OAuth Google Drive end-to-end sampai tahap yang bisa diverifikasi dari server.
7. Jangan mengubah provider lain.
8. Jangan menjalankan atau mengubah test/integration test Gorouter.app. Jika test suite otomatis memuat Gorouter.app, skip/exclude test tersebut.
9. NVIDIA dan TokenHarbor.ai jangan disentuh kecuali benar-benar diperlukan oleh perubahan ini.
10. Jangan commit dan jangan push ke GitHub.
11. Jika ada error, diagnosis dan perbaiki langsung. Jangan berhenti hanya untuk meminta saya memilih opsi yang URL-nya sudah jelas.
12. Setelah selesai, tampilkan ringkasan:
   - file yang diubah
   - service yang direstart
   - hasil health check
   - hasil verifikasi Google Drive
   - apakah OAuth callback production sudah siap
   - jika masih ada langkah manual di browser, jelaskan tepat langkah berikutnya.

Penting: gunakan https://api.contentpilot.biz.id/api/storage/google_drive/callback sebagai redirect URI final. Jangan gunakan localhost atau IP publik sebagai redirect URI.

````
# 
```
Lanjutkan konfigurasi Google Drive OAuth sesuai instruksi sebelumnya.

Saya sudah membuat OAuth Client:
- Name: content pilot google drive
- Type: Web application
- Google Drive API: Enabled
- Data Access scopes sudah diset:
  - https://www.googleapis.com/auth/drive.file
  - https://www.googleapis.com/auth/userinfo.email
  - openid
- Test user sudah ditambahkan.
- OAuth Client sudah dibuat.

Untuk OAuth Client tersebut, saya akan menggunakan konfigurasi produksi berikut:

Authorized redirect URI:
https://api.contentpilot.biz.id/api/storage/google_drive/callback

Authorized JavaScript origins:
kosongkan, karena flow yang digunakan adalah server-side OAuth.

Sekarang lanjutkan dari sisi project /root/content-pilot.

Tugas Anda:
1. Pastikan konfigurasi Google Drive OAuth membaca GOOGLE_CLIENT_ID, GOOGLE_CLIENT_SECRET, dan GOOGLE_REDIRECT_URI dari environment.
2. Pastikan GOOGLE_REDIRECT_URI menggunakan persis:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback
3. Jangan mengubah provider lain.
4. Jangan melakukan commit.
5. Jangan menjalankan atau mengubah test Gorouter.app.
6. Setelah konfigurasi siap, restart API + worker sesuai arsitektur project.
7. Verifikasi endpoint callback dan flow OAuth Google Drive.
8. Lanjutkan sampai tahap pengujian Connect Google Drive.
9. Jika ada konfigurasi yang masih kurang di Google Cloud, berhenti dan beri saya instruksi klik yang tepat. Jangan menebak nilai URL.
10. Jangan meminta saya memasukkan secret ke chat. Jika secret sudah ada di VPS/.env, gunakan konfigurasi yang tersedia di server.

Sebelum melakukan perubahan besar, periksa konfigurasi existing dan struktur kode terlebih dahulu agar tidak merusak implementasi yang sudah berjalan.

````
# 
```

Lanjutkan setup Google Drive OAuth untuk project ini.

Kondisi Google Cloud saat ini:
- Project: utility-canto-507016-h9
- Google Drive API: sudah ENABLED
- OAuth configuration: sudah dibuat
- Data Access sudah berisi scope:
  - drive.file
  - userinfo.email
  - openid
- Publishing status masih Testing
- Test user sudah ditambahkan
- OAuth Client ID sudah dibuat dengan nama: content pilot google drive
- Tipe: Web application
- Saat ini Authorized JavaScript origins dan Authorized redirect URIs masih kosong.

Jangan mengubah kode/project dulu.

Tugas kamu:
1. Periksa source code project untuk menemukan endpoint/callback OAuth Google Drive yang sebenarnya digunakan aplikasi.
2. Tentukan secara pasti nilai yang harus saya masukkan ke:
   - Authorized JavaScript origins
   - Authorized redirect URIs
3. Jangan menebak URL. Ambil berdasarkan konfigurasi/source code yang ada.
4. Jika server menggunakan localhost, IP VPS, domain, atau port tertentu, jelaskan URL lengkapnya.
5. Berikan instruksi langkah demi langkah untuk saya setting di Google Cloud Console dari posisi saya sekarang.
6. Setelah saya selesai memasukkan URI di Google Cloud, baru lanjutkan ke pengujian OAuth/Connect Google Drive.
7. Jangan commit perubahan dan jangan menjalankan test provider lain.
8. Fokus hanya pada integrasi Google Drive OAuth pada project ini.

Untuk sekarang, berhenti setelah memberikan URI yang harus saya masukkan dan menunggu saya mengirim screenshot hasilnya.
````
# 
```
Lanjutkan setup Google Drive untuk project ini.

KONTEKS:
- Google Auth Platform / OAuth configuration sudah berhasil dibuat di Google Cloud.
- Jangan membuat perubahan kode dulu.
- Jangan membuat credential palsu.
- Fokus hanya pada persiapan Google Drive OAuth.

TUGAS:
1. Audit repository saat ini untuk menemukan implementasi Google Drive OAuth yang sudah ada.
2. Temukan endpoint/callback OAuth yang benar-benar digunakan backend.
3. Tentukan secara pasti:
   - OAuth Application type yang harus dibuat di Google Cloud
   - Authorized JavaScript origins jika diperlukan
   - Authorized redirect URIs yang harus dimasukkan
4. Cocokkan dengan kode di:
   - packages/providers/gdrive/
   - apps/api/src/
   - apps/web/src/
   - konfigurasi environment yang relevan
5. Jangan mengubah source code.
6. Jangan membuat commit.
7. Jangan push.
8. Jangan menjalankan live Google Drive verification.
9. Jangan meminta saya memasukkan atau menampilkan GOOGLE_CLIENT_SECRET.

OUTPUT HANYA:
- Status implementasi Google Drive OAuth saat ini
- OAuth Client type yang harus dipilih
- Exact Authorized redirect URI yang harus saya masukkan ke Google Cloud
- Exact Authorized JavaScript origin jika memang diperlukan
- Nama environment variable yang nanti harus diisi
- Langkah berikutnya setelah OAuth Client dibuat

Jika ada lebih dari satu kemungkinan URI, jelaskan mana yang benar untuk production dan mana yang untuk local/development.

````
# 
```
LANJUT KE IMPLEMENTASI GOOGLE DRIVE STORAGE — REAL INTEGRATION

Repository saat ini adalah Content Pilot di /root/content-pilot.

Dari audit sebelumnya:
- Core/destination architecture sudah tersedia.
- Destination isolation sudah diterapkan.
- Storage abstraction sudah tersedia.
- Google Drive provider/foundation sudah tersedia.
- Google Drive live verification sebelumnya belum dijalankan karena credential belum tersedia.
- Jangan membuat commit kosong.
- Jangan mengubah architecture yang sudah benar hanya demi menghasilkan diff.

Sekarang fokus HANYA pada Google Drive sebagai PRIMARY STORAGE PROVIDER.

JANGAN mengerjakan:
- Facebook publishing
- Facebook OAuth
- YouTube
- Instagram
- TikTok
- provider storage lain
- S3/R2/MinIO
- production auto-publishing
- queue hardening di luar kebutuhan storage
- perubahan besar core architecture

==================================================
TUJUAN
==================================================

Pastikan Content Pilot benar-benar memiliki fondasi Google Drive Storage yang production-ready secara architecture.

Target:

Content Pilot
    ↓
StorageProvider
    ↓
GoogleDriveStorage
    ↓
Google Drive API

Google Drive harus menjadi storage provider pertama yang benar-benar digunakan oleh media pipeline.

Database Content Pilot tetap menjadi source of truth.

Google Drive hanya menjadi storage backend.

==================================================
1. AUDIT IMPLEMENTASI GOOGLE DRIVE YANG SUDAH ADA
==================================================

Sebelum coding:

Baca implementation aktual repository.

Periksa minimal:

packages/providers/gdrive/
apps/api/
apps/web/
packages/db/
storage connection model
storage registry
media model
API routes
UI settings/storage
environment configuration
tests
documentation

Identifikasi:

- apa yang sudah benar-benar implemented
- apa yang masih abstraction
- apa yang masih mock
- apa yang masih TODO
- apa yang belum terhubung
- apakah Google Drive SDK/client sudah digunakan
- bagaimana token/credential disimpan
- bagaimana storage connection dikaitkan ke user/destination

JANGAN membuat ulang sesuatu yang sudah ada.

==================================================
2. GOOGLE OAUTH
==================================================

Jika OAuth Google Drive belum benar-benar selesai:

implementasikan connection flow menggunakan OAuth resmi Google.

Gunakan dokumentasi resmi Google sebagai sumber utama.

Jangan mengarang scope.

Gunakan scope minimum yang memang diperlukan untuk operasi storage yang direncanakan.

Perhatikan:

- authorization code flow
- redirect URI
- state/CSRF protection
- access token
- refresh token
- token expiry
- reconnect
- disconnect
- revoked access
- invalid_grant
- credential encryption
- secret handling

Access token dan refresh token:

JANGAN:
- ditampilkan di UI
- ditulis ke log
- disimpan plaintext jika architecture secure storage/encryption tersedia
- dimasukkan ke error response
- di-commit ke Git

Jika environment belum memiliki Google OAuth credentials:

jangan membuat fake credentials.

Implementasikan integration dengan konfigurasi environment yang jelas dan biarkan live verification tetap NEEDS CREDENTIAL jika memang credential belum tersedia.

==================================================
3. STORAGE CONNECTION
==================================================

Pastikan model storage connection dapat membedakan:

User
→ Google Drive Connection

dan destination/workspace.

Jika architecture saat ini memiliki storage connection global per user, jangan mengubahnya menjadi destination-specific secara paksa.

Namun storage object/media HARUS tetap dapat dikaitkan secara jelas dengan destination/workspace jika requirement isolation mengharuskannya.

Gunakan model existing sebagai source of truth.

Status minimal:

connected
disconnected
expired
error

API jangan pernah mengembalikan credential/token.

==================================================
4. GOOGLE DRIVE ROOT
==================================================

Google Drive harus memiliki root folder khusus untuk Content Pilot.

Contoh logical structure:

Content Pilot/
    Page A/
        Incoming/
        Ready/
        Published/
        Failed/

    Page B/
        Incoming/
        Ready/
        Published/
        Failed/

Jangan membuat folder global yang menyebabkan Page A dan Page B tercampur tanpa metadata.

Folder ID harus disimpan sebagai provider-specific reference.

Jangan menggunakan nama folder sebagai identifier utama.

Gunakan Google Drive file/folder ID.

Jika root/folder sudah pernah dibuat:

gunakan kembali.

Jangan membuat duplicate folder setiap kali user reconnect atau request ulang.

==================================================
5. DESTINATION ISOLATION
==================================================

WAJIB.

Media dari Destination A tidak boleh masuk ke logical storage scope Destination B.

Contoh:

Destination A
→ Google Drive Folder A

Destination B
→ Google Drive Folder B

Jika satu media digunakan untuk beberapa destination:

jangan memindahkan ownership media secara diam-diam.

Gunakan model media + storage object/reference yang sudah ditentukan architecture.

PublishingJob tetap destination-specific.

==================================================
6. GOOGLE DRIVE OPERATIONS
==================================================

StorageProvider harus mendukung operasi yang memang diperlukan.

Minimal:

connect
disconnect
getConnectionStatus

createFolder
getFolder
upload
getMetadata
download/stream jika dibutuhkan
exists
move
delete/archive sesuai architecture

Jangan membuat method yang tidak diperlukan hanya untuk memperbesar interface.

GoogleDriveStorage harus mengimplementasikan StorageProvider.

Core tidak boleh import Google Drive SDK secara langsung.

Google Drive SDK hanya boleh berada di provider/module Google Drive.

==================================================
7. UPLOAD
==================================================

Implementasikan upload media ke Google Drive.

Perhatikan:

- MIME type
- filename sanitization
- file size
- stream handling
- timeout
- error handling
- resumable upload jika diperlukan untuk file besar
- duplicate handling
- provider object ID
- upload status

Jangan membaca seluruh video ke memory jika architecture dapat menggunakan stream.

Storage object harus menyimpan:

media_id
destination_id
storage_connection_id
provider
provider_object_id
status
metadata
created_at
updated_at

Jika field yang setara sudah ada, gunakan field existing.

Jangan membuat duplicate model tanpa alasan.

==================================================
8. DOWNLOAD / STREAM
==================================================

Pastikan media dapat diambil kembali dari Google Drive menggunakan provider object ID.

Jangan mengandalkan:

filename
folder name
path

sebagai identifier utama.

Jika publishing pipeline nantinya membutuhkan stream:

buat API/provider abstraction yang dapat memberikan stream atau temporary access sesuai architecture.

Jangan membuat public Google Drive URL sebagai permanent secret.

==================================================
9. DELETE / ARCHIVE
==================================================

Implementasikan behavior yang aman.

Jangan langsung permanently delete jika architecture belum menetapkan policy tersebut.

Bedakan:

database delete
storage delete
archive

Jangan menghapus Google Drive object hanya karena database record dihapus kecuali memang policy mengharuskannya.

Jika belum ada retention policy:

gunakan behavior konservatif dan dokumentasikan.

==================================================
10. DUPLICATE DETECTION
==================================================

Periksa apakah project sudah memiliki duplicate detection.

Jika belum:

buat abstraction yang aman.

Jangan hanya membandingkan filename.

Pertimbangkan:

- provider object ID
- file size
- checksum/hash jika tersedia
- source reference
- media identity

Jangan menghitung hash video besar dengan cara yang membuat memory usage tidak masuk akal.

Jika duplicate detection belum perlu untuk tahap ini:

jangan over-engineer.

Dokumentasikan sebagai follow-up.

==================================================
11. API
==================================================

Pastikan API storage tersedia secara aman.

Minimal konsep:

GET /api/settings/storage
GET /api/settings/storage/google-drive/connect
GET /api/settings/storage/google-drive/callback
POST /api/settings/storage/google-drive/disconnect

dan endpoint media/storage sesuai architecture existing.

Jangan membuat duplicate endpoint jika route existing sudah memiliki fungsi yang sama.

Semua endpoint:

- authenticated
- authorized
- no secret leakage
- CSRF/state protected untuk OAuth
- destination scoped jika berkaitan dengan destination data

==================================================
12. UI STORAGE
==================================================

Audit UI existing terlebih dahulu.

Gunakan UI storage yang sudah ada jika sesuai.

Target:

Storage

Google Drive

Status:
● Connected

Account:
example@gmail.com

Storage:
Google Drive

Actions:
[Open]
[Disconnect]

Jika belum connected:

Google Drive
Not connected

[Connect Google Drive]

Jangan menampilkan:
- access token
- refresh token
- client secret

Jika credential belum dikonfigurasi:

tampilkan status yang jelas:

Google Drive
Configuration required

Jangan fake menjadi Connected.

==================================================
13. MEDIA FLOW
==================================================

Pastikan flow architecture menjadi:

Manual Upload
       │
       ▼
Media Service
       │
       ▼
GoogleDriveStorage
       │
       ▼
Google Drive
       │
       ▼
StorageObject
       │
       ▼
Media READY

Downloader nantinya harus dapat menggunakan pipeline yang sama.

Jangan membuat uploader terpisah yang bypass StorageProvider.

==================================================
14. TEST
==================================================

WAJIB.

Pertahankan semua test existing.

Tambahkan/update test untuk:

1. provider registry menemukan Google Drive provider
2. Google Drive provider mengimplementasikan StorageProvider
3. provider tidak terkonfigurasi menghasilkan status yang benar
4. credential tidak pernah masuk response
5. credential tidak pernah masuk log
6. storage connection terisolasi per user sesuai architecture
7. destination A tidak dapat membaca storage object destination B
8. upload menghasilkan provider object ID
9. metadata dapat dibaca kembali
10. reconnect tidak membuat duplicate root folder
11. disconnect mengubah status dengan benar
12. invalid/revoked credential menghasilkan error yang aman
13. OAuth state/CSRF validation
14. duplicate folder creation dicegah
15. filename tidak digunakan sebagai primary identifier

Gunakan mock HTTP/client untuk unit test.

Jangan mengklaim live Google Drive berhasil jika credential nyata belum tersedia.

==================================================
15. LIVE VERIFICATION
==================================================

Jika environment memiliki:

GOOGLE_CLIENT_ID
GOOGLE_CLIENT_SECRET
GOOGLE_REDIRECT_URI

dan credential tersebut benar-benar valid:

jalankan live verification yang aman.

Test minimal:

1. OAuth connection
2. account identification
3. root folder discovery/creation
4. destination folder discovery/creation
5. upload test file
6. metadata retrieval
7. download/stream verification jika implementasinya tersedia
8. cleanup test object jika aman
9. disconnect/reconnect behavior

Jangan upload file user secara sembarangan.

Gunakan test object yang jelas.

Jika credential TIDAK tersedia:

tulis:

GOOGLE DRIVE LIVE VERIFICATION: NOT RUN
REASON: GOOGLE_CLIENT_ID/SECRET/REDIRECT_URI unavailable

Jangan membuat fake PASS.

==================================================
16. SECURITY AUDIT
==================================================

Periksa seluruh Google Drive flow untuk:

- token exposure
- secret exposure
- OAuth CSRF
- authorization
- IDOR
- cross-user storage access
- cross-destination access
- path traversal
- malicious filename
- MIME spoofing
- oversized upload
- SSRF jika URL source digunakan
- log leakage

Periksa juga:

git diff

untuk memastikan tidak ada:

.env
credentials.json
service-account JSON
OAuth token
refresh token
client secret
API key

yang masuk commit.

==================================================
17. DOCUMENTATION
==================================================

Update dokumentasi existing.

Jangan membuat duplicate docs.

Dokumentasikan:

Google Drive Storage Architecture

Authentication

OAuth scopes yang benar-benar digunakan

Storage connection

Folder structure

Destination isolation

Upload flow

Media lifecycle

Error handling

Reconnect

Disconnect

Credential handling

Live verification status

Configuration environment variables

Jika scope/permission masih perlu verifikasi:

tulis UNKNOWN / NEEDS VERIFICATION.

==================================================
18. ENVIRONMENT CONFIG
==================================================

Jika environment variables belum tersedia, dokumentasikan nama variable yang benar-benar digunakan implementation.

Jangan menaruh nilai credential nyata ke repository.

Contoh bentuk dokumentasi:

GOOGLE_CLIENT_ID=
GOOGLE_CLIENT_SECRET=
GOOGLE_REDIRECT_URI=

Gunakan nama yang konsisten dengan implementation.

Jangan membuat nama environment variable baru jika repository sudah memiliki convention yang benar.

==================================================
19. NO FAKE SUCCESS
==================================================

ATURAN KERAS:

Jangan menulis:

Google Drive connected

jika credential belum benar-benar terhubung.

Jangan menulis:

Upload success

jika request tidak benar-benar berhasil.

Jangan menulis:

Live verification PASS

jika belum dijalankan.

Gunakan:

NOT CONFIGURED
NOT RUN
NEEDS VERIFICATION
FAILED

sesuai kondisi sebenarnya.

==================================================
20. REGRESSION
==================================================

Setelah implementation:

jalankan command project yang benar berdasarkan package.json.

Minimal jika tersedia:

pnpm typecheck
pnpm lint
pnpm test
pnpm build

Periksa seluruh test.

Jangan skip test hanya supaya hijau.

Jika ada test yang memang harus di-skip karena membutuhkan credential live:

jelaskan secara eksplisit.

==================================================
21. GIT
==================================================

Setelah implementation selesai:

git status

git diff

review semua perubahan.

Jika tidak ada perubahan yang diperlukan:

JANGAN membuat commit.

Jika ada perubahan valid:

commit:

feat: implement google drive storage integration

Kemudian push ke branch aktif.

Jangan force push.

Jangan commit secret.

Setelah push:

verifikasi remote.

==================================================
22. FINAL REPORT
==================================================

Tampilkan:

GOOGLE DRIVE STORAGE STATUS

AUDIT:
PASS/FAIL

PROVIDER:
PASS/FAIL

OAUTH:
PASS/FAIL/NOT CONFIGURED

CONNECTION:
PASS/FAIL

ROOT FOLDER:
PASS/FAIL/NOT VERIFIED

DESTINATION ISOLATION:
PASS/FAIL

UPLOAD:
PASS/FAIL/NOT LIVE VERIFIED

DOWNLOAD/STREAM:
PASS/FAIL/NOT IMPLEMENTED

METADATA:
PASS/FAIL

DUPLICATE HANDLING:
PASS/FAIL/DEFERRED

SECURITY:
PASS/FAIL

API:
PASS/FAIL

UI:
PASS/FAIL

TEST:
PASS/FAIL

TYPECHECK:
PASS/FAIL

LINT:
PASS/FAIL

BUILD:
PASS/FAIL

LIVE GOOGLE DRIVE:
PASS/FAIL/NOT RUN

GIT STATUS:
CLEAN/NOT CLEAN

COMMIT:
<hash atau NONE>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS/FAILED/N/A

REMOTE VERIFIED:
YES/NO/N/A

FILES CHANGED:
<summary>

OPEN ISSUES:
<only real issues>

NEXT RECOMMENDED PHASE:
<one phase only>

==================================================
STOP CONDITION
==================================================

Setelah Google Drive storage work selesai dan, jika ada perubahan valid, berhasil di-push:

STOP.

Jangan lanjut ke Facebook.

Jangan lanjut ke YouTube.

Jangan lanjut ke Instagram.

Jangan lanjut ke TikTok.

Jangan implementasikan storage provider lain.

Jangan implementasikan auto-publishing baru.

Tunggu instruksi berikutnya.

````
# 
```
LANJUT KE PHASE 1 — CORE FOUNDATION & DESTINATION WORKSPACE ARCHITECTURE

Gunakan repository Content Pilot yang sedang aktif sebagai source of truth.

Hasil Phase 0 sudah selesai.
Jangan mengulang audit Phase 0 kecuali diperlukan untuk memastikan struktur aktual.

Sekarang mulai IMPLEMENTASI PHASE 1.

==================================================
TUJUAN PHASE 1
==================================================

Bangun fondasi core Content Pilot yang benar-benar platform-independent.

Fokus utama:

1. User
2. Platform
3. PlatformConnection
4. Destination
5. Destination Workspace
6. Media foundation
7. PublishingJob foundation
8. Provider Registry
9. Storage abstraction
10. Queue abstraction/foundation
11. Scheduler abstraction/foundation
12. Destination-scoped data access
13. Destination isolation
14. API foundation
15. UI foundation untuk workspace/destination

JANGAN implementasikan Facebook publishing pada phase ini.

JANGAN implementasikan Facebook OAuth pada phase ini.

JANGAN implementasikan YouTube/Instagram/TikTok publishing.

JANGAN membuat fake provider.

JANGAN membuat fake OAuth.

JANGAN membuat fake publishing success.

==================================================
ATURAN ARSITEKTUR
==================================================

Core tidak boleh mengetahui detail API Facebook.

Core hanya mengetahui konsep generik.

Target:

Core
│
├── Platform Registry
│
├── Account / Connection
│
├── Destination
│
├── Workspace
│
├── Media
│
├── Publishing Job
│
├── Storage
│
├── Queue
│
├── Scheduler
│
└── History / Audit

Provider/platform-specific implementation harus tetap terisolasi.

Konsep:

Core
   ↓
Provider Registry
   ↓
Platform Provider
   ↓
Platform-specific implementation

Contoh future:

FacebookProvider
YouTubeProvider
InstagramProvider
TikTokProvider

Tetapi pada Phase 1 jangan implementasikan publishing provider tersebut.

==================================================
1. PLATFORM MODEL
==================================================

Buat model platform generik.

Contoh:

Platform
- id
- key
- name
- status
- capabilities
- created_at
- updated_at

Platform key contoh:

facebook
youtube
instagram
tiktok

Tetapi jangan menganggap semuanya aktif.

Platform dapat memiliki status:

available
coming_soon
disabled

Jangan membuat platform yang belum diimplementasikan terlihat aktif di UI.

==================================================
2. PLATFORM CONNECTION
==================================================

Buat abstraction untuk koneksi account platform.

Contoh konsep:

PlatformConnection
- id
- user_id
- platform_id
- provider_account_id
- account_name
- status
- credential_reference
- metadata
- created_at
- updated_at
- last_connected_at
- last_error_at
- last_error_code

Credential/token jangan disimpan plaintext jika architecture existing menyediakan secure storage.

Jangan menyimpan access token di frontend.

Jangan commit token.

Jangan membuat OAuth implementation pada Phase 1.

Status connection harus dapat mewakili:

connected
disconnected
expired
error
pending

==================================================
3. DESTINATION
==================================================

Buat entity Destination generik.

Contoh:

Destination
- id
- user_id
- platform_connection_id
- platform_id
- external_id
- name
- type
- status
- metadata
- created_at
- updated_at

Contoh:

Facebook:
Page A
Page B

YouTube:
Channel A

Instagram:
Account A

TikTok:
Account A

Core tidak boleh menggunakan field khusus Facebook seperti:

facebook_page_id

sebagai identifier utama.

Gunakan:

external_id

dan platform/provider metadata.

==================================================
4. DESTINATION WORKSPACE
==================================================

Ini adalah bagian PALING PENTING Phase 1.

Setiap Destination harus memiliki workspace sendiri secara logical.

Contoh:

User
│
├── Facebook Account
│   ├── Page A
│   │   └── Workspace A
│   └── Page B
│       └── Workspace B
│
└── YouTube Account
    └── Channel A
        └── Workspace C

Workspace tidak harus menjadi microservice.

Workspace adalah logical context/scoping layer.

Setiap workspace harus memiliki:

- destination context
- dashboard
- downloader context
- storage context
- publish context
- queue context
- scheduler context
- history context

Semua data operasional harus dapat ditrace ke destination.

==================================================
5. DESTINATION ISOLATION
==================================================

WAJIB.

Destination A tidak boleh membaca data Destination B.

Semua query repository/service yang berkaitan dengan:

- media
- publishing jobs
- schedules
- queue
- history
- settings

harus menggunakan destination scope jika entity tersebut memang destination-scoped.

Contoh:

getMedia(destinationId)

getPublishingJobs(destinationId)

getSchedules(destinationId)

getHistory(destinationId)

Jangan membuat endpoint global yang mengembalikan seluruh data destination tanpa authorization/scoping.

Authorization harus memeriksa:

user → destination ownership/access

Bukan hanya:

user authenticated = boleh akses semua destination.

==================================================
6. MEDIA FOUNDATION
==================================================

Buat media model generik.

Contoh:

Media
- id
- owner_user_id
- destination_id
- filename
- mime_type
- size
- duration
- width
- height
- storage_provider
- storage_object_id
- source_type
- source_reference
- status
- metadata
- created_at
- updated_at

Source type minimal:

manual
downloader
import

Jangan membuat:

FacebookVideo
YouTubeVideo
InstagramVideo

sebagai model utama.

Media harus dapat digunakan oleh beberapa publishing job.

Perhatikan:

Satu media dapat dipublish ke:

Page A
Page B
YouTube Channel A

Jadi jangan membuat media terkunci secara permanen ke satu publishing job.

Namun jika media memiliki destination scope karena aturan workspace, desain harus jelas dan konsisten.

Jika architecture Phase 0 menetapkan destination-scoped media, pertahankan aturan tersebut.

Jika satu media perlu digunakan untuk beberapa destination, gunakan relationship/reference yang aman tanpa merusak isolation.

Jangan mengubah keputusan architecture tanpa alasan.

==================================================
7. PUBLISHING JOB FOUNDATION
==================================================

Buat PublishingJob generik.

Contoh:

PublishingJob
- id
- user_id
- media_id
- destination_id
- platform_id
- status
- schedule_source
- scheduled_at
- sequence_number
- attempt_count
- last_error_code
- last_error_message
- next_retry_at
- created_at
- updated_at

Status minimal:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jangan membuat publishing API nyata pada Phase 1.

Job hanya foundation.

==================================================
8. ONE DESTINATION = ONE JOB
==================================================

Jika satu media dipilih untuk banyak destination:

Media A

→ Page A = Job A
→ Page B = Job B
→ YouTube A = Job C

Setiap job berdiri sendiri.

Jangan membuat satu job global yang memiliki array destination dan kemudian kehilangan status per destination.

==================================================
9. PROVIDER REGISTRY
==================================================

Buat provider registry abstraction.

Registry harus dapat mendaftarkan provider berdasarkan platform key.

Contoh konsep:

registerProvider("facebook", provider)

getProvider("facebook")

hasProvider("facebook")

listProviders()

Tetapi provider interface harus generic.

Jangan memasukkan Facebook-specific code ke core registry.

Provider harus dapat memiliki capability.

Contoh:

capabilities:
- video
- reels
- photo
- text_post
- scheduling
- analytics

Jangan mengaktifkan capability hanya karena ditulis di interface.

Capability harus berasal dari implementation/provider.

==================================================
10. PROVIDER INTERFACE
==================================================

Buat interface abstraction secukupnya.

Jangan membuat interface raksasa hanya untuk memenuhi roadmap.

Pisahkan concern jika diperlukan:

Authentication capability

Account discovery capability

Destination discovery capability

Media validation capability

Publishing capability

Status capability

Scheduling capability

Contoh konsep:

Provider
- key
- metadata
- capabilities

Provider services dapat berkembang kemudian.

Tujuannya:

Facebook provider nantinya dapat diimplementasikan tanpa mengubah database/core architecture.

==================================================
11. STORAGE ABSTRACTION
==================================================

Google Drive adalah storage provider pertama.

Namun Phase 1 hanya membuat abstraction/foundation jika belum ada implementation yang stabil.

Konsep:

StorageProvider

- upload
- download
- delete
- getMetadata
- exists
- createFolder
- move/update jika diperlukan

Jangan memasukkan Google Drive SDK langsung ke core.

Target:

Core
 ↓
StorageProvider
 ↓
GoogleDriveStorage

Provider masa depan:

S3
R2
MinIO
VPS/local

belum perlu dibuat.

Jika Google Drive implementation dari pekerjaan sebelumnya sudah benar-benar ada, JANGAN menghapusnya.

Integrasikan hanya jika sesuai architecture.

Jangan melakukan live Google OAuth verification tanpa credential.

==================================================
12. QUEUE FOUNDATION
==================================================

Buat abstraction untuk publishing queue.

Core harus dapat:

enqueue(job)

claim(job)

complete(job)

fail(job)

retry(job)

cancel(job)

Namun jangan membuat production worker kompleks jika belum diperlukan pada Phase 1.

Pastikan queue tidak menghilangkan destination_id.

Worker nantinya harus selalu mengetahui:

job.id
media.id
destination.id
platform.id

==================================================
13. SCHEDULER FOUNDATION
==================================================

Buat scheduler abstraction.

Scheduler harus menerima:

destination
media
schedule settings
timezone

dan menghasilkan PublishingJob dengan:

scheduled_at

Jangan implementasikan seluruh daily-slot automation jika itu sudah direncanakan untuk Phase 4.

Pada Phase 1 cukup buat foundation/model/service boundary yang benar.

Jangan membuat scheduler global yang tidak mengetahui destination.

==================================================
14. SETTINGS FOUNDATION
==================================================

Jika settings model diperlukan, buat struktur yang memungkinkan configuration per destination.

Contoh:

DestinationSettings
- destination_id
- timezone
- auto_publish_enabled
- max_videos_per_day
- configuration

Daily slots dapat menjadi child/configuration entity sesuai architecture.

Jangan membuat setting global jika requirement sebenarnya destination-specific.

==================================================
15. API
==================================================

Buat API foundation untuk destination/workspace.

Minimal konsep endpoint:

GET /api/destinations

GET /api/destinations/:id

GET /api/destinations/:id/settings

GET /api/destinations/:id/media

GET /api/destinations/:id/jobs

GET /api/destinations/:id/schedules

Semua endpoint:

- authenticated
- authorization checked
- destination ownership/access checked
- tidak boleh cross-destination

Jangan membuat endpoint yang mengembalikan secret/token.

==================================================
16. UI WORKSPACE
==================================================

Buat atau sesuaikan UI berdasarkan UI existing.

Jangan membuat dashboard kedua jika dashboard sudah ada.

Tambahkan konsep:

Destination / Workspace Switcher

Contoh:

[ Facebook Page A ▼ ]

Workspace:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Ketika user memilih:

Facebook Page B

semua context berpindah ke:

Page B

Tidak boleh tetap menampilkan data Page A.

UI harus selalu memiliki destination context yang jelas.

Contoh header:

Facebook
Page A
● Connected

atau:

YouTube
Channel A
● Connected

Jika provider belum aktif:

Coming Soon

==================================================
17. UI ISOLATION
==================================================

Frontend tidak boleh hanya melakukan filter lokal seperti:

allMedia.filter(destinationId)

sebagai satu-satunya security mechanism.

Backend harus sudah destination-scoped.

Frontend filter hanya untuk presentation.

==================================================
18. DATABASE
==================================================

Gunakan database architecture yang ditemukan pada Phase 0.

Jangan mengganti database hanya karena preferensi pribadi.

Buat migration secara aman.

Sebelum migration:

- inspect schema existing
- hindari destructive migration
- jangan drop table sembarangan
- jangan menghapus data existing tanpa instruksi

Jika project baru memang belum memiliki production data, tetap gunakan migration yang bersih dan reversible jika memungkinkan.

Tambahkan index untuk query penting:

user_id
destination_id
platform_id
status
scheduled_at

Gunakan foreign key yang sesuai.

==================================================
19. TEST
==================================================

WAJIB menambahkan test untuk destination isolation.

Minimal test cases:

1. User A dapat mengakses Destination A.
2. User A tidak dapat mengakses Destination milik User B.
3. Destination A tidak dapat membaca media Destination B.
4. Destination A tidak dapat membaca jobs Destination B.
5. Destination A tidak dapat membaca schedule Destination B.
6. Destination A tidak dapat mengubah settings Destination B.
7. Multi-destination media menghasilkan job terpisah.
8. Job memiliki destination_id yang benar.
9. Provider registry dapat mendaftarkan provider generik.
10. Storage abstraction tidak bergantung langsung pada Google Drive implementation.
11. API mengembalikan unauthorized/forbidden/not-found sesuai security model.
12. Workspace switch tidak menyebabkan data destination sebelumnya bocor.

Jangan hanya test happy path.

==================================================
20. SECURITY
==================================================

Periksa:

- authorization
- destination ownership
- IDOR prevention
- token exposure
- secret logging
- API response
- database query scoping
- file access
- metadata leakage

Jangan log:

access token
refresh token
client secret
API key
password

Jika error provider memiliki secret di response, sanitize sebelum disimpan/log.

==================================================
21. DOCUMENTATION
==================================================

Update:

docs/ARCHITECTURE.md

docs/DATABASE.md

docs/PLATFORM_MODULES.md

docs/STORAGE.md jika tersedia

docs/ROADMAP.md

docs/UI_DESIGN.md

Dokumentasikan keputusan Phase 1.

Khusus:

Destination Workspace Architecture

dan

Destination Isolation Rules

harus ditulis secara eksplisit.

==================================================
22. JANGAN OVER-ENGINEER
==================================================

Jangan membuat:

microservices
Kubernetes
event bus kompleks
distributed transaction system
multi-region infrastructure

jika repository belum membutuhkannya.

Prioritaskan architecture yang sederhana tetapi benar.

==================================================
23. VERIFICATION
==================================================

Setelah implementation:

jalankan seluruh command yang tersedia dan relevan.

Minimal:

pnpm typecheck
pnpm lint
pnpm test
pnpm build

Jika command berbeda berdasarkan repository aktual, gunakan command yang benar dari package.json.

Jangan mematikan test.

Jangan mengurangi coverage hanya agar hijau.

Periksa:

git diff
git status

Pastikan tidak ada:

- secret
- token
- API key
- password
- credential
- file sensitif

==================================================
24. GIT
==================================================

Jika semua verification PASS:

buat commit:

feat: implement content pilot core foundation

Kemudian push ke branch aktif.

Jangan force push.

Jangan membuat commit kosong.

Jangan commit perubahan yang tidak berkaitan dengan Phase 1.

Setelah push:

verifikasi remote.

==================================================
25. FINAL REPORT
==================================================

Tampilkan laporan:

PHASE 1 STATUS:

CORE FOUNDATION:
PASS/FAIL

PLATFORM MODEL:
PASS/FAIL

PLATFORM CONNECTION:
PASS/FAIL

DESTINATION:
PASS/FAIL

DESTINATION WORKSPACE:
PASS/FAIL

DESTINATION ISOLATION:
PASS/FAIL

MEDIA FOUNDATION:
PASS/FAIL

PUBLISHING JOB:
PASS/FAIL

PROVIDER REGISTRY:
PASS/FAIL

STORAGE ABSTRACTION:
PASS/FAIL

QUEUE FOUNDATION:
PASS/FAIL

SCHEDULER FOUNDATION:
PASS/FAIL

API:
PASS/FAIL

UI:
PASS/FAIL

SECURITY:
PASS/FAIL

TEST:
PASS/FAIL

TYPECHECK:
PASS/FAIL

LINT:
PASS/FAIL

BUILD:
PASS/FAIL

GIT STATUS:
CLEAN/NOT CLEAN

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS/FAILED

REMOTE VERIFIED:
YES/NO

FILES CHANGED:
<summary>

IMPORTANT:
Jelaskan jika ada bagian yang sengaja TIDAK diimplementasikan karena memang masuk Phase berikutnya.

==================================================
STOP CONDITION
==================================================

Setelah Phase 1 selesai dan push berhasil:

STOP.

Jangan lanjut ke Phase 2.

Jangan implementasikan Facebook OAuth.

Jangan implementasikan Facebook publishing.

Jangan implementasikan YouTube.

Jangan implementasikan Instagram.

Jangan implementasikan TikTok.

Tunggu instruksi berikutnya.

````
# 
```
KOREKSI KONTEKS — STOP PEKERJAAN LLM PROVIDER

Respons sebelumnya keluar dari scope Content Pilot.

JANGAN mencari, membuat, atau memverifikasi:
- LLM provider
- ProviderRegistry untuk routing model AI
- multi-key rotation
- cooldown provider
- fallback LLM
- Empero-key
- AI routing layer
- subsystem LLM apa pun

Itu BUKAN bagian dari task Content Pilot.

KEMBALI KE PROJECT CONTENT PILOT.

Gunakan repository dan branch Content Pilot yang sedang aktif sebagai satu-satunya source of truth.

Konteks arsitektur yang harus dipertahankan:

1. Core harus platform-independent.
2. Facebook adalah provider pertama.
3. Sistem harus mendukung multiple Facebook account.
4. Satu Facebook account dapat memiliki banyak Page.
5. Setiap Page adalah Destination.
6. Setiap Destination/Page memiliki workspace sendiri.
7. Workspace Page memiliki konteks sendiri untuk:
   - Dashboard
   - Downloader
   - Storage
   - Publish
   - Queue
   - Schedule
   - History
8. Semua operasi harus destination-scoped.
9. Page A tidak boleh melihat atau memproses queue/media/schedule milik Page B kecuali melalui fitur multi-destination yang secara eksplisit membuat job terpisah.
10. Google Drive adalah storage provider pertama yang menjadi fokus.
11. Media tetap generik/platform-independent.
12. PublishingJob harus terpisah per destination.
13. Scheduler harus destination-scoped.
14. Sequence publishing tidak reset setiap hari.
15. Jangan menambahkan YouTube/Instagram/TikTok sekarang.
16. Jangan membuat fake success.
17. Jangan mengarang API atau credential.
18. Jangan melakukan destructive migration.
19. Jangan mengubah arsitektur yang sudah selesai tanpa audit terlebih dahulu.

SEBELUM CODING:

Audit state repository TERKINI.

Baca:
- docs/ROADMAP.md
- docs/ARCHITECTURE.md
- docs/DATABASE.md
- docs/STORAGE.md
- docs/QUEUE_SCHEDULER.md
- docs/PLATFORM_MODULES.md
- dokumentasi Facebook yang tersedia
- implementasi Google Drive yang sudah ada
- implementasi Destination/Workspace yang sudah ada
- scheduler
- queue
- worker
- publishing pipeline

Kemudian cocokkan implementasi aktual dengan roadmap.

JANGAN mengulang fitur yang sudah selesai.

JANGAN membuat fitur baru hanya karena tidak menemukan file tertentu sebelum memastikan struktur repository aktual.

Jika menemukan pekerjaan yang sudah selesai:
→ tandai COMPLETE
→ jangan implementasikan ulang.

Jika menemukan gap:
→ jelaskan gap tersebut
→ implementasikan hanya gap yang memang termasuk phase aktif.

FOKUS SAAT INI:

Hardening Content Pilot setelah Phase 4 yang sudah selesai.

Prioritas:
1. destination isolation
2. scheduler correctness
3. queue/job idempotency
4. concurrent worker safety
5. stale job recovery
6. retry/backoff
7. rate-limit handling
8. audit/observability
9. Google Drive integration boundary
10. UI status yang jujur

Pastikan terutama:

Page A:
- media Page A
- queue Page A
- schedule Page A
- publishing history Page A

tidak tercampur dengan Page B.

Untuk multi-destination publishing:

1 media dapat digunakan untuk beberapa destination,
tetapi harus dibuat:

Job A → Page A
Job B → Page B

dengan status dan history masing-masing.

Untuk Google Drive:

- jangan membuat provider storage baru
- gunakan abstraction yang sudah ada
- jangan membuat fake OAuth
- jangan mengklaim live verification jika credential belum tersedia
- pertahankan status NEEDS VERIFICATION/BLOCKED jika memang belum bisa live test

Untuk scheduler:

- sequence tidak reset setiap hari
- daily slots destination-scoped
- timezone destination-scoped
- manual schedule override tetap dihormati
- slot tidak boleh dialokasikan dua kali
- scheduler restart tidak membuat duplicate job

Untuk worker:

- dua worker tidak boleh memproses PublishingJob yang sama secara bersamaan
- gunakan database sebagai source of truth
- Redis bukan satu-satunya sumber status
- crash/restart harus dapat dipulihkan
- retry tidak boleh menghasilkan duplicate publish

Setelah implementasi:

- pnpm lint
- pnpm typecheck
- pnpm test
- pnpm build

Jangan mematikan test untuk membuat suite hijau.

Periksa git diff.

Pastikan tidak ada:
- secret
- token
- API key
- password

Kemudian commit perubahan yang benar-benar berkaitan dengan task ini dan push ke branch aktif.

JANGAN force push.

FINAL REPORT:

AUDIT STATUS:
IMPLEMENTATION STATUS:
DESTINATION ISOLATION:
SCHEDULER:
QUEUE:
CONCURRENCY:
IDEMPOTENCY:
RETRY:
RATE LIMIT:
GOOGLE DRIVE:
TEST:
BUILD:

GIT STATUS:
COMMIT:
BRANCH:
PUSH STATUS:
REMOTE VERIFIED:

Jika tidak ada gap yang perlu dikerjakan, JANGAN membuat perubahan palsu hanya untuk menghasilkan commit.

STOP setelah task Content Pilot selesai.

Jangan pernah kembali ke subsystem LLM provider.

````
# prompt audit/verifikasi berikut ke AI coding sekarang:
```
Sekarang jangan menambahkan fitur baru dan jangan mengubah arsitektur yang sudah PASS.

Lakukan VERIFIKASI KHUSUS terhadap requirement provider yang baru saja kita minta.

Pastikan secara nyata di code bahwa:

1. Setiap model memiliki provider yang tetap/terkunci.
2. Jika satu key gagal, sistem hanya berpindah ke key lain dari provider yang SAMA.
3. Tidak ada fallback otomatis dari Provider A ke Provider B.
4. Jika semua key provider tersebut gagal, request benar-benar mengembalikan error dan berhenti.
5. Cooldown/restart/retry provider atau key yang bermasalah menggunakan sekitar 180 detik (3 menit), bukan beberapa detik.
6. Selama cooldown, key/provider tersebut tidak digunakan.
7. Cooldown satu provider/key tidak menyebabkan request berpindah ke provider lain.
8. Audit seluruh provider yang sudah ada, bukan hanya NVIDIA atau Empero.
9. Cari semua provider/model list yang masih hardcoded di frontend.
10. Pastikan provider yang ditambahkan ke provider registry/code otomatis dapat terdeteksi backend dan muncul di UI tanpa harus mengedit daftar provider frontend secara manual.
11. Pastikan model baru dari provider tersebut juga otomatis tersedia di UI.
12. Pastikan backend dan frontend menggunakan single source of truth untuk provider/model sejauh memungkinkan dari arsitektur project.
13. Jangan membuat fitur COMBO sekarang.

WAJIB lakukan code inspection terlebih dahulu sebelum menyimpulkan PASS.

Buat test/mock yang membuktikan skenario berikut:

Provider Empero:
Key 1 → FAIL
Key 2 → FAIL
Key 3 → SUCCESS

Pastikan request GLM berhasil menggunakan Key 3.

Kemudian test:

Empero Key 1 → FAIL
Empero Key 2 → FAIL
Empero Key 3 → FAIL

Pastikan request GLM gagal dan TIDAK pernah mencoba provider lain.

Tambahkan provider dummy/test beserta model dummy/test ke registry dan pastikan provider serta model tersebut dapat terdeteksi oleh backend dan UI tanpa menambahkan entry manual baru di frontend.

Verifikasi juga cooldown dengan test bahwa key/provider yang gagal tidak dicoba kembali sebelum sekitar 180 detik.

Jangan menggunakan credential production.

Jangan menjalankan atau mengaktifkan test Gorouter.app. Jika test suite otomatis memuat Gorouter.app, skip/exclude test tersebut. NVIDIA dan TokenHarbor.ai boleh diverifikasi sesuai kebutuhan.

Setelah selesai, jangan hanya mengatakan PASS. Tampilkan bukti konkret:
- file/komponen routing yang menentukan provider;
- file/komponen multi-key rotation;
- lokasi cooldown 180 detik;
- lokasi yang mencegah fallback antar-provider;
- sumber data provider/model yang digunakan UI;
- test yang ditambahkan/dijalankan;
- hasil seluruh test;
- apakah provider/model dummy berhasil auto-discovery.

Jika ditemukan implementasi yang belum sesuai, PERBAIKI terlebih dahulu lalu jalankan test ulang.

Jangan lanjut ke fitur COMBO sampai seluruh verifikasi ini benar-benar PASS.

````
# hardening scheduler/publishing pipeline
```

Lanjutkan project Content Pilot dari state repository TERBARU di branch yang sedang digunakan.

PENTING:
- Audit commit dan implementasi TERBARU terlebih dahulu.
- Jangan mengulang fitur yang sudah selesai.
- Jangan menghapus atau merombak arsitektur existing tanpa alasan.
- Jangan membuat provider/platform baru.
- Jangan menambahkan YouTube/Instagram/TikTok.
- Jangan membuat fake success.
- Jangan menganggap fitur live terverifikasi jika belum benar-benar diverifikasi.
- Google Drive tetap menjadi storage provider utama yang sudah ada.
- Fokus hanya pada hardening pipeline yang sudah berjalan.

==================================================
TASK: PUBLISHING & SCHEDULER HARDENING
==================================================

Tujuan:
Membuat pipeline scheduler → publishing job → queue → worker lebih aman terhadap:

1. concurrent worker
2. duplicate processing
3. stale lock
4. rate limit
5. retry
6. crash/restart
7. race condition
8. observability/audit

==================================================
1. AUDIT IMPLEMENTASI TERKINI
==================================================

Periksa terlebih dahulu:

- packages/core
- packages/db
- packages/shared
- packages/providers/facebook
- apps/api
- apps/worker
- apps/web
- scheduler
- queue
- PublishingJob
- PublishingAttempt
- SlotAssignment/schedule
- idempotency
- stale-lock reaper
- retry/backoff
- existing rate limiter
- audit logging

Baca dokumentasi terkait:

- docs/ARCHITECTURE.md
- docs/QUEUE_SCHEDULER.md
- docs/STORAGE.md
- docs/facebook-publishing.md
- docs/research/facebook-api.md
- docs/ROADMAP.md

Jangan membuat implementasi kedua jika fungsi yang sama sudah tersedia.

==================================================
2. CONCURRENCY SAFETY
==================================================

Pastikan dua worker yang berjalan bersamaan TIDAK dapat memproses PublishingJob yang sama.

Audit dan perbaiki jika diperlukan:

- atomic claim
- database transaction
- row locking / compare-and-set
- status transition
- attempt creation
- idempotency key

Target:

Worker A → claim Job 123 → SUCCESS
Worker B → mencoba Job 123 → TIDAK BOLEH publish ulang

Tidak boleh terjadi:

Job 123
→ Facebook publish
→ Facebook publish kedua akibat race condition

Gunakan mekanisme database sebagai source of truth.

Redis tidak boleh menjadi satu-satunya sumber kebenaran untuk status job.

==================================================
3. STALE LOCK / CRASH RECOVERY
==================================================

Audit stale-lock reaper yang sudah ada.

Pastikan job yang worker-nya crash ketika berada pada state:

- processing
- uploading
- publishing

dapat dipulihkan secara aman.

Pastikan:

- job yang benar-benar masih diproses tidak direbut worker lain secara prematur
- job yang sudah stale dapat dikembalikan ke retry/queued sesuai aturan
- attempt history tetap tersimpan
- tidak membuat duplicate PublishingJob
- tidak melakukan duplicate publish ke Facebook

Dokumentasikan timeout/lease yang digunakan.

==================================================
4. FACEBOOK RATE LIMIT
==================================================

Implement/hardening rate limiting Facebook Reels sesuai requirement yang SUDAH diverifikasi dalam repository.

Jika repository sudah memiliki application-side limit:

- audit implementasinya
- pastikan atomic
- destination/page scoped
- aman terhadap concurrent worker
- tidak mudah bypass hanya karena worker lebih dari satu
- reset window tersimpan secara benar
- tidak menganggap rate limit internal sebagai bukti rate limit Meta jika belum diverifikasi live

Jangan mengarang limit baru.

Jika limit tertentu masih NEEDS VERIFICATION berdasarkan dokumentasi resmi Meta, pertahankan status tersebut dan jangan mengklaimnya sebagai fakta API.

==================================================
5. RETRY & ERROR CLASSIFICATION
==================================================

Audit:

temporary error:
- timeout
- network failure
- temporary API failure
- rate limit

permanent error:
- invalid credential
- permission denied
- invalid destination
- unsupported media
- validation failure

Pastikan:

temporary → retry/backoff
permanent → failed tanpa retry otomatis yang tidak perlu

Simpan:

- attempt count
- error code
- safe error message
- timestamp
- next retry
- provider metadata jika aman

Jangan menyimpan access token, Authorization header, atau secret dalam log/error metadata.

==================================================
6. IDEMPOTENCY
==================================================

Audit seluruh jalur:

Scheduler
→ PublishingJob
→ Queue
→ Worker
→ Provider

Pastikan restart/retry/concurrent execution tidak menghasilkan duplicate job atau duplicate publish.

Gunakan idempotency yang sudah ada jika memang sudah benar.

Jangan membuat sistem idempotency kedua yang tumpang tindih.

Tambahkan regression tests untuk:

- scheduler restart
- worker restart
- duplicate queue delivery
- concurrent claim
- retry setelah crash
- duplicate scheduler tick

==================================================
7. SCHEDULE / SLOT SAFETY
==================================================

Pastikan daily slot scheduler tetap memenuhi aturan:

- sequence tidak reset setiap hari
- sequence tidak digunakan ulang
- slot berdasarkan timezone Destination
- destination scoped
- Page A tidak mengambil schedule Page B
- manual schedule override tetap dihormati
- slot yang sudah reserved tidak dialokasikan dua kali
- perubahan settings tidak merusak job published
- cancellation tidak membuat sequence lama digunakan kembali

Test minimal:

Page A:
08:00 → Video 1
11:00 → Video 2

Page B:
08:00 → Video 1

Keduanya harus independent karena destination berbeda.

==================================================
8. OBSERVABILITY
==================================================

Audit logging dan worker logging.

Pastikan event penting dapat ditelusuri:

- job created
- job claimed
- job processing
- upload started
- publishing started
- publishing success
- publishing failed
- retry scheduled
- job cancelled
- stale job recovered
- rate limited

Log harus aman dan tidak membocorkan secret.

Gunakan correlation/job ID yang memungkinkan satu publishing trace ditelusuri.

Jangan menambahkan logging berlebihan yang berisi media bytes atau token.

==================================================
9. API / UI STATUS
==================================================

Periksa apakah status backend sudah ditampilkan secara jujur pada UI.

Pastikan UI dapat membedakan:

- queued
- processing
- uploading
- publishing
- published
- retrying
- failed
- cancelled

Jangan membuat UI mengatakan Published sebelum worker benar-benar menerima hasil sukses dari provider.

Jika provider belum dikonfigurasi:

tampilkan:
Needs configuration

bukan:
Published

==================================================
10. GOOGLE DRIVE
==================================================

JANGAN membuat storage provider baru.

Audit implementasi Google Drive yang sudah ada:

- StorageConnection
- OAuth
- token encryption
- refresh
- StorageObject
- destination isolation
- upload
- retry
- idempotency

Pastikan failure tidak menghasilkan READY palsu.

Jika live Google Drive verification belum dapat dilakukan karena credential tidak tersedia:

- jangan membuat fake test
- jangan mengklaim PASS
- dokumentasikan sebagai NEEDS VERIFICATION / BLOCKED
- tetap pastikan unit/integration boundary tests valid

==================================================
11. TESTING
==================================================

Tambahkan atau perbaiki test hanya jika diperlukan.

Minimal test:

1. concurrent worker claim
2. duplicate delivery
3. stale lock recovery
4. retry/backoff
5. rate limiter concurrency
6. destination isolation
7. sequence non-reset
8. slot collision
9. cancellation
10. scheduler restart/idempotency
11. Google Drive failure → no fake READY

Gunakan mock/injected boundary untuk provider eksternal.

Jangan menjalankan live Meta/Google integration test jika credential tidak tersedia.

==================================================
12. VALIDATION
==================================================

Setelah coding:

pnpm lint
pnpm typecheck
pnpm test
pnpm build

Jika ada test yang gagal:

- cari root cause
- perbaiki
- jalankan ulang

Jangan menonaktifkan test hanya agar suite hijau.

==================================================
13. DOCUMENTATION
==================================================

Update dokumentasi yang relevan:

- docs/ARCHITECTURE.md
- docs/QUEUE_SCHEDULER.md
- docs/STORAGE.md
- docs/ROADMAP.md

Dokumentasikan:

- concurrency model
- job claiming
- stale recovery
- retry
- rate limiting
- idempotency
- observability
- Google Drive verification status

Jangan membuat duplicate documentation.

==================================================
14. GIT
==================================================

Setelah semua perubahan selesai:

1. git status
2. inspect seluruh diff
3. pastikan tidak ada secret/token/API key/password
4. jalankan lint/typecheck/test/build
5. commit hanya perubahan task ini
6. gunakan commit message:

fix: harden publishing scheduler concurrency and recovery

7. push ke branch yang sedang digunakan
8. verifikasi commit benar-benar berada di remote

Jangan force push.

Jika push gagal:
- jangan mengklaim berhasil
- tampilkan error sebenarnya
- hentikan setelah perubahan lokal aman

==================================================
FINAL REPORT
==================================================

Tampilkan:

AUDIT STATUS: COMPLETE
CONCURRENCY STATUS: PASS / NEEDS FIX
RATE LIMIT STATUS: PASS / NEEDS VERIFICATION
RETRY STATUS: PASS / NEEDS FIX
IDEMPOTENCY STATUS: PASS / NEEDS FIX
SCHEDULER STATUS: PASS / NEEDS FIX
GOOGLE DRIVE STATUS: VERIFIED / NEEDS VERIFICATION / BLOCKED
TEST STATUS: PASS / FAIL
BUILD STATUS: PASS / FAIL

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS / FAILED
REMOTE VERIFIED: YES / NO

STOP setelah pekerjaan ini selesai.

Jangan lanjut ke provider YouTube, Instagram, TikTok, atau advanced automation.
````

# Phase 4 — Daily Slot & Auto-Publishing Scheduler
```
LANJUTKAN CONTENT PILOT — PHASE 4
DAILY SLOT & AUTO-PUBLISHING SCHEDULER

Kita sekarang masuk ke Phase 4 sesuai roadmap Content Pilot.

PENTING:
Jangan mengulang pekerjaan Phase 0, Phase 1, Phase 2, atau Phase 3 yang sudah selesai kecuali audit singkat menunjukkan ada dependency yang benar-benar dibutuhkan.

Gunakan repository dan implementasi AKTUAL sebagai source of truth.

Sebelum coding:
1. Periksa git status.
2. Baca ROADMAP.md.
3. Baca ARCHITECTURE.md.
4. Baca DATABASE.md.
5. Baca STORAGE.md atau dokumentasi storage yang tersedia.
6. Baca dokumentasi scheduler/queue yang sudah ada.
7. Periksa implementation Phase sebelumnya.
8. Periksa test yang sudah ada.
9. Jangan menghapus fitur yang sudah bekerja.
10. Jangan melakukan massive refactor.
11. Jangan membuat fake implementation.
12. Jangan membuat Facebook publishing production pada phase ini.
13. Jangan menambahkan provider baru pada phase ini.

==================================================
TUJUAN PHASE 4
==================================================

Implementasikan sistem:

DAILY SLOT
+
AUTO SCHEDULING
+
SEQUENCE
+
QUEUE INTEGRATION
+
MANUAL SCHEDULE OVERRIDE
+
RESCHEDULING
+
CANCELLATION
+
RETRY/IDEMPOTENCY FOUNDATION

Scheduler harus bersifat GENERIC dan tidak boleh bergantung langsung pada Facebook.

Scheduler hanya menentukan:

MEDIA MANA
DESTINATION MANA
KAPAN DIPUBLISH
JOB APA YANG HARUS DIBUAT

Provider/platform yang melakukan publishing adalah tanggung jawab phase/provider berikutnya.

==================================================
ARSITEKTUR DESTINATION WORKSPACE
==================================================

Ini adalah aturan paling penting.

Setiap Destination memiliki workspace sendiri.

Contoh:

Facebook Account
├── Page A
│   └── Workspace A
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
├── Page B
│   └── Workspace B
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
└── Page C
    └── Workspace C
        ├── Dashboard
        ├── Downloader
        ├── Storage
        ├── Publish
        ├── Queue
        ├── Schedule
        └── History

Scheduler HARUS selalu bekerja dalam context destination.

Setiap schedule harus memiliki:

destination_id

Setiap publishing job harus memiliki:

destination_id

Media yang digunakan oleh auto scheduler harus dapat ditelusuri ke destination/workspace yang sesuai.

==================================================
DESTINATION ISOLATION
==================================================

WAJIB:

Page A tidak boleh mengambil media milik Page B.

Page A tidak boleh mengambil schedule Page B.

Page A tidak boleh mengambil queue Page B.

Page A tidak boleh mengubah konfigurasi Page B.

Page A tidak boleh mengubah sequence Page B.

Page A tidak boleh melihat history publishing Page B kecuali UI secara eksplisit menyediakan global overview dengan authorization yang benar.

Semua query scheduler harus scoped.

Contoh konsep:

WHERE destination_id = currentDestinationId

Jangan mengandalkan filter frontend sebagai security.

Isolation harus terjadi di backend/database query layer.

Jika sebuah API menerima:

destination_id

backend WAJIB memverifikasi bahwa destination tersebut dimiliki/diakses oleh user yang sedang authenticated.

Jangan percaya destination_id dari client begitu saja.

==================================================
SCHEDULING SETTINGS
==================================================

Implementasikan konfigurasi scheduler per Destination/Workspace.

Minimal:

SchedulingSettings

- id
- destination_id
- enabled
- max_videos_per_day
- timezone
- daily_slots
- created_at
- updated_at

Contoh:

max_videos_per_day = 4

timezone = Asia/Jakarta

daily_slots:

08:00
11:00
14:00
17:00

Konfigurasi harus PER DESTINATION.

Contoh:

Page A:
4 video/day

Page B:
2 video/day

Page C:
6 video/day

Jangan membuat satu konfigurasi global untuk semua Page.

==================================================
TIMEZONE
==================================================

Timezone harus eksplisit.

Jangan menggunakan timezone server sebagai timezone publishing.

Contoh:

Destination A:
timezone = Asia/Jakarta

Destination B:
timezone = America/New_York

scheduled_at harus disimpan dengan representasi waktu yang aman/consistent sesuai database architecture yang sudah digunakan.

Scheduler harus menghitung slot berdasarkan timezone Destination.

Jangan menggunakan waktu lokal browser sebagai source of truth.

==================================================
DAILY SLOT
==================================================

User dapat menentukan slot waktu.

Contoh:

08:00
11:00
14:00
17:00

Jumlah slot dapat berbeda dari max_videos_per_day.

Jika:

max_videos_per_day = 3

slots:
08:00
11:00
14:00
17:00

Maka hanya 3 slot pertama yang digunakan sesuai aturan konfigurasi yang ditentukan.

Namun jangan mengasumsikan behavior tersebut jika repository sudah memiliki specification berbeda.

Dokumentasikan aturan final.

Validasi:

- slot harus valid HH:mm
- tidak boleh duplicate
- timezone harus valid
- max_videos_per_day harus valid
- slot harus dapat diurutkan
- konfigurasi tidak boleh menghasilkan scheduled_at yang ambigu

==================================================
AUTO SCHEDULING
==================================================

Ketika media sudah:

READY

dan auto scheduling aktif untuk Destination tersebut:

Scheduler mencari slot publikasi tersedia paling awal.

Contoh:

Max:
4 video/day

Slots:
08:00
11:00
14:00
17:00

Media:

Video 1
Video 2
Video 3

Maka:

Video 1 → 08:00
Video 2 → 11:00
Video 3 → 14:00

17:00 tetap kosong.

Jika Video 4 masuk:

Video 4 → 17:00

Jika Video 5 masuk:

Video 5 → next available day 08:00

==================================================
SEQUENCE
==================================================

Sequence HARUS GLOBAL PER DESTINATION dan TIDAK RESET SETIAP HARI.

Contoh:

Hari 1:
Video 1
Video 2
Video 3

Hari 2:

Video 4
Video 5
Video 6

Bukan:

Hari 2:
Video 1
Video 2
Video 3

Sequence harus tetap meningkat.

Namun sequence destination A dan destination B tidak boleh bercampur.

Contoh:

Page A:
1
2
3
4

Page B:
1
2
3

Sequence harus scoped per destination.

Jangan gunakan filename sebagai sequence identifier.

Jangan gunakan tanggal sebagai sequence identifier.

Jangan menggunakan array index sebagai sequence identifier.

Gunakan database-safe mechanism.

Jika terdapat concurrency, dua worker/request tidak boleh mendapatkan sequence number yang sama.

==================================================
SEQUENCE DAN FAILURE
==================================================

Sequence yang sudah diberikan tidak boleh dipakai ulang secara sembarangan.

Contoh:

Video 10 mendapatkan sequence 10.

Kemudian job gagal.

Sequence 10 tetap merupakan sequence yang pernah digunakan.

Video berikutnya tidak boleh otomatis menjadi sequence 10 hanya karena job sebelumnya gagal.

Jika repository architecture memilih sequence terpisah dari publishing job, dokumentasikan hubungan:

sequence_number
media_id
publishing_job_id
destination_id

Jangan membuat sequence_number sebagai pengganti job ID.

==================================================
MEDIA SOURCE
==================================================

Scheduler harus dapat menerima media dari pipeline yang sudah ada.

Contoh:

Manual Upload
↓
Media
↓
READY
↓
Scheduler

Downloader
↓
Media
↓
READY
↓
Scheduler

Jangan membuat scheduler khusus downloader.

Jangan membuat scheduler khusus manual upload.

Gunakan Media abstraction yang sudah ada.

Media harus memiliki source metadata jika implementation sebelumnya sudah mendukung:

source_type:
- manual
- downloader
- other

Jika field tersebut belum ada dan benar-benar diperlukan, tambahkan secara minimal dan dokumentasikan.

==================================================
AUTO SCHEDULING TRIGGER
==================================================

Tentukan trigger yang paling cocok berdasarkan architecture repository.

Kemungkinan:

1. ketika Media berubah menjadi READY
2. ketika media masuk queue
3. scheduler periodic worker
4. kombinasi event + reconciliation job

Pilih berdasarkan implementation yang sudah ada.

Jangan membuat dua scheduler yang saling berebut job.

Pastikan operasi idempotent.

Jika media sudah memiliki schedule/job aktif:

JANGAN membuat duplicate schedule/job.

==================================================
MANUAL SCHEDULE OVERRIDE
==================================================

User harus dapat memilih manual schedule.

Contoh:

Auto scheduler memilih:

14:00

User mengubah:

20:00

Maka schedule tersebut menjadi:

schedule_source = manual

Manual override harus mengalahkan auto slot.

Contoh metadata:

schedule_source:
AUTO
MANUAL

Jangan scheduler berikutnya memindahkan manual schedule kembali ke slot otomatis.

==================================================
FINAL / LOCKED SCHEDULE
==================================================

Bedakan schedule yang masih dapat diubah dan schedule yang sudah final.

Minimal konsep:

draft
scheduled
queued
processing
published
failed
cancelled

Jangan otomatis melakukan rescheduling terhadap:

published
processing

Dan jangan mengubah job yang sudah final tanpa aturan eksplisit.

Jika perlu tambahkan konsep:

schedule_locked

atau gunakan status existing jika sudah mencukupi.

Gunakan model existing jika tersedia.

==================================================
RESCHEDULING
==================================================

Jika konfigurasi daily slot berubah:

Contoh sebelumnya:

08:00
11:00
14:00
17:00

kemudian user mengubah menjadi:

09:00
13:00
18:00

JANGAN otomatis memindahkan semua history.

Hanya schedule yang masih eligible untuk reschedule yang boleh dipengaruhi.

Jangan mengubah:

published
processing

Rescheduling harus deterministic.

Dokumentasikan:

- kapan rescheduling diperbolehkan
- schedule mana yang terkena perubahan
- schedule mana yang tetap immutable
- bagaimana manual override diperlakukan
- bagaimana sequence diperlakukan

==================================================
NEXT AVAILABLE SLOT
==================================================

Buat algoritma untuk mencari:

next available slot

Algoritma harus:

1. menggunakan timezone Destination
2. memperhatikan slot yang sudah terisi
3. memperhatikan schedule yang cancelled
4. memperhatikan job yang masih aktif
5. tidak membuat collision
6. tidak mengubah schedule yang sudah final
7. pindah ke hari berikutnya jika slot hari ini penuh
8. mempertahankan sequence
9. aman terhadap concurrent request/worker

Contoh:

Hari ini:

08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Video baru:

→ 17:00

Jika 17:00 juga sudah terisi:

→ besok 08:00

==================================================
PAST TIME
==================================================

Jika scheduler menemukan slot hari ini yang sudah lewat:

JANGAN menjadwalkan job ke waktu masa lalu.

Contoh sekarang 15:30.

Slots:

08:00
11:00
14:00
17:00

Slot berikutnya:

17:00

Bukan:

08:00
11:00
14:00

Jika semua slot hari ini sudah lewat:

→ next available slot hari berikutnya.

Gunakan timezone Destination.

==================================================
MAX VIDEOS PER DAY
==================================================

max_videos_per_day harus benar-benar membatasi auto scheduling.

Contoh:

max_videos_per_day = 3

Slots:

08:00
11:00
14:00
17:00

Maka auto scheduler tidak boleh mengalokasikan lebih dari 3 video pada tanggal lokal Destination tersebut.

Perhatikan perbedaan:

jumlah slot konfigurasi

vs

maximum videos per day.

Jangan menganggap keduanya selalu sama.

==================================================
QUEUE INTEGRATION
==================================================

Scheduler tidak melakukan publishing langsung.

Flow:

Media READY
↓
Scheduler
↓
PublishingJob
↓
scheduled
↓
Queue
↓
Worker
↓
Provider
↓
Publish

Phase ini boleh membuat/finalisasi PublishingJob dan memasukkannya ke queue sesuai architecture existing.

Tetapi:

JANGAN membuat Facebook production publishing jika provider belum masuk phase ini.

Worker boleh berhenti pada provider execution boundary yang memang sudah tersedia.

Jangan membuat fake:

PUBLISHED

hanya untuk membuat test terlihat berhasil.

==================================================
JOB IDEMPOTENCY
==================================================

Satu media + destination + schedule tidak boleh menghasilkan duplicate job karena:

- request diulang
- browser refresh
- worker restart
- scheduler restart
- network retry
- process crash

Gunakan unique constraint/idempotency mechanism yang sesuai database architecture.

Contoh konsep:

destination_id
+
media_id
+
active schedule/job identity

Tetapi tentukan unique key berdasarkan schema aktual.

Jangan membuat unique constraint yang menghalangi legitimate rescheduling/retry.

==================================================
CANCELLATION
==================================================

User harus dapat membatalkan schedule yang belum diproses.

Contoh:

scheduled → cancelled

Setelah cancelled:

- job tidak boleh dieksekusi
- queue worker harus menghormati cancellation
- scheduler boleh menggunakan slot tersebut lagi jika aturan final mengizinkan
- history tetap mencatat bahwa schedule pernah ada dan dibatalkan

Jangan menghapus record secara hard delete hanya untuk menghilangkan schedule.

Gunakan status/history.

==================================================
RETRY
==================================================

Phase 4 harus menyiapkan retry foundation.

Temporary errors:

- timeout
- network failure
- temporary provider error
- rate limit

Permanent:

- invalid credential
- permission denied
- invalid destination
- unsupported media

Scheduler tidak boleh retry permanent error secara membabi buta.

PublishingAttempt jika sudah tersedia harus digunakan.

Jika belum tersedia, implementasikan hanya bagian minimal yang dibutuhkan Phase 4 dan dokumentasikan.

==================================================
QUEUE CONCURRENCY
==================================================

Pastikan scheduler tidak membuat duplicate job ketika dua proses berjalan bersamaan.

Contoh:

Request A:
alokasikan Video 10 → 14:00

Request B:
pada waktu hampir bersamaan mencoba alokasi Video 11

Tidak boleh keduanya mendapatkan slot 14:00.

Gunakan:

- database transaction
- row locking
- unique constraint
- atomic operation
- atau mekanisme yang sesuai stack

Jangan mengandalkan JavaScript in-memory lock saja.

==================================================
API
==================================================

Audit API existing sebelum menambahkan endpoint.

Jika endpoint belum tersedia, desain endpoint yang konsisten.

Minimal kebutuhan:

GET scheduling settings

PUT/PATCH scheduling settings

GET schedules

POST/manual schedule

POST schedule cancellation

POST reschedule jika diperlukan

GET queue/status jika existing architecture membutuhkan

Semua endpoint harus:

- authenticated
- authorization checked
- destination scoped
- validated
- tidak membocorkan destination lain
- memiliki error response konsisten

Jangan membuat endpoint duplicate jika sudah ada.

==================================================
CONTOH API
==================================================

Gunakan pola repository yang sudah ada.

Contoh konsep:

GET
/api/destinations/:destinationId/scheduling/settings

PUT
/api/destinations/:destinationId/scheduling/settings

GET
/api/destinations/:destinationId/scheduling

POST
/api/destinations/:destinationId/scheduling/media/:mediaId

POST
/api/destinations/:destinationId/scheduling/media/:mediaId/cancel

Tetapi jangan menganggap path di atas final.

Sesuaikan dengan API architecture aktual.

==================================================
UI
==================================================

UI harus mengikuti konsep workspace.

Ketika user berada di:

Page A Workspace

semua schedule yang tampil harus Page A.

Contoh:

Workspace Switcher

[ Facebook Page A ▼ ]

Menu:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Jika pindah:

[ Facebook Page B ▼ ]

semua context berubah ke Page B.

Schedule Page A tidak boleh tetap tampil di Page B.

==================================================
SCHEDULER PAGE
==================================================

Buat/ubah halaman scheduler yang sesuai UI existing.

Minimal tampilkan:

Destination/Workspace

Auto Publishing:
ON/OFF

Maximum videos per day

Timezone

Daily slots

Upcoming schedule

Sequence

Schedule source:

AUTO
MANUAL

Status:

Scheduled
Queued
Processing
Published
Failed
Cancelled

Jangan membuat UI terlalu rumit jika repository existing memiliki design system.

Gunakan reusable components.

==================================================
SCHEDULE VIEW
==================================================

Sediakan tampilan yang mudah dipahami.

Contoh:

TODAY

08:00
Video 001
AUTO
Scheduled

11:00
Video 002
AUTO
Scheduled

14:00
Video 003
MANUAL
Scheduled

17:00
Available

TOMORROW

08:00
Video 004
AUTO
Scheduled

Pastikan sequence terlihat.

==================================================
EMPTY STATE
==================================================

Jika tidak ada schedule:

Tampilkan empty state yang jelas.

Contoh:

No scheduled content

Auto publishing is enabled.

New READY media will be assigned to the next available slot.

Jangan fake data.

==================================================
SETTINGS UI
==================================================

User dapat mengubah:

Auto Publishing
Maximum videos/day
Timezone
Daily slots

Tambahkan validation.

Contoh:

Maximum:
1–100

Namun angka final harus mengikuti product requirement dan architecture.

Jangan membuat batas arbitrer tanpa alasan.

==================================================
DESTINATION SWITCHER
==================================================

Pastikan workspace switcher tidak hanya mengubah UI.

Ketika user memilih Page B:

frontend harus menggunakan destination_id Page B.

Backend tetap melakukan authorization.

Jangan:

GET semua data lalu filter di frontend.

Harus:

GET data berdasarkan destination context.

==================================================
DATABASE
==================================================

Audit schema existing.

Jika tabel schedule/scheduling_settings/publishing_jobs sudah ada:

gunakan dan extend secara minimal.

Jangan membuat:

schedules2
publishing_jobs2
daily_slots2

hanya karena implementasi baru.

Minimal relasi:

Destination
↓
SchedulingSettings

Destination
↓
Media

Destination
↓
Schedule / PublishingJob

Media
↓
PublishingJob

PublishingJob
↓
PublishingAttempt

Gunakan schema aktual sebagai source of truth.

==================================================
DATABASE CONSTRAINTS
==================================================

Pertimbangkan constraint untuk:

- destination ownership
- valid schedule
- no duplicate active allocation
- sequence uniqueness per destination
- valid status transition
- idempotency

Tetapi jangan menambahkan constraint yang bertentangan dengan kemampuan retry/reschedule.

==================================================
STATUS TRANSITION
==================================================

Definisikan state machine yang jelas.

Contoh:

draft
→ scheduled
→ queued
→ processing
→ publishing
→ published

Failure:

processing
→ failed

Retry:

failed
→ retrying
→ queued

Cancellation:

scheduled
→ cancelled

Queued cancellation harus memiliki aturan jelas.

Jangan memperbolehkan random status transition.

==================================================
AUDIT LOG
==================================================

Jika audit log architecture sudah tersedia, gunakan.

Catat event penting:

- scheduling settings changed
- auto publishing enabled
- auto publishing disabled
- media auto scheduled
- manual schedule created
- schedule rescheduled
- schedule cancelled
- retry triggered
- job state changed

Jangan log secret/token.

==================================================
NOTIFICATION
==================================================

Jangan membuat sistem notification besar pada phase ini.

Jika notification system sudah ada:

gunakan event yang relevan.

Jika belum ada:

dokumentasikan sebagai future enhancement.

==================================================
TESTING
==================================================

Test wajib mencakup:

1. auto scheduling
2. destination isolation
3. timezone
4. next available slot
5. past slot handling
6. max videos/day
7. sequence
8. sequence does not reset
9. sequence scoped per destination
10. manual override
11. rescheduling
12. cancellation
13. duplicate prevention
14. idempotency
15. concurrency
16. retry state
17. status transitions
18. authorization
19. empty schedule
20. configuration validation

Test skenario:

Page A:
4 slots

Page B:
2 slots

Masukkan media ke keduanya.

Pastikan:

Page A hanya mendapatkan media Page A.

Page B hanya mendapatkan media Page B.

Sequence tidak bercampur.

==================================================
REGRESSION
==================================================

Jangan merusak fitur Phase sebelumnya.

Setelah implementasi:

run seluruh test suite.

Jangan hanya menjalankan test scheduler.

Minimal:

typecheck
lint
test
build

Jika ada test existing yang gagal:

1. tentukan apakah failure disebabkan perubahan Phase 4
2. perbaiki jika memang regression
3. jangan menghapus test hanya agar suite hijau

==================================================
GOOGLE DRIVE
==================================================

Google Drive adalah primary storage provider pada Phase sebelumnya.

Scheduler harus menggunakan Media abstraction.

Jangan memasukkan Google Drive API langsung ke scheduler.

Flow tetap:

Google Drive
↓
Media
↓
READY
↓
Scheduler
↓
PublishingJob

Scheduler hanya membutuhkan Media yang valid/READY dan metadata storage yang diperlukan.

==================================================
DOWNLOADER
==================================================

Downloader bukan bagian utama Phase 4.

Jangan membuat downloader baru.

Gunakan downloader existing.

Yang harus dipastikan:

Downloader menghasilkan Media yang dapat masuk ke scheduler.

Contoh:

Downloader
→ Media
→ destination_id
→ READY
→ Auto Scheduler

==================================================
MULTI-DESTINATION PUBLISHING
==================================================

Jika satu media nantinya dipublish ke banyak destination:

Media dapat digunakan bersama.

Tetapi harus dibuat:

Job Page A
Job Page B
Job Page C

Jangan membuat satu job global:

Media A → Page A + Page B + Page C

karena status tiap destination harus independen.

Contoh:

Page A = published
Page B = failed
Page C = scheduled

harus dapat terjadi secara independen.

==================================================
SECURITY
==================================================

Periksa:

- authentication
- authorization
- destination ownership
- IDOR prevention
- input validation
- rate limiting
- audit logging
- secret handling

Jangan expose:

OAuth token
refresh token
Google Drive credential
Facebook token
API key

ke UI.

==================================================
NO FAKE PUBLISHING
==================================================

Phase ini TIDAK BOLEH:

- mengaku Facebook publish berhasil
- membuat fake Facebook response
- membuat status PUBLISHED tanpa provider execution nyata
- menggunakan fake credential sebagai production success

Mock hanya boleh digunakan di unit test dan harus diberi label jelas.

==================================================
DOCUMENTATION
==================================================

Update documentation yang relevan.

Minimal:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/ROADMAP.md
docs/UI_DESIGN.md

Jika ada:

docs/QUEUE_SCHEDULER.md

buat/update file tersebut.

Dokumentasikan:

- scheduler architecture
- daily slot rules
- sequence rules
- timezone
- destination isolation
- manual override
- rescheduling
- cancellation
- retry
- idempotency
- queue integration
- state transitions

Jangan membuat duplicate docs.

==================================================
IMPORTANT ARCHITECTURAL RULE
==================================================

Core Scheduler HARUS GENERIC.

Jangan:

if platform === "facebook"

untuk menentukan scheduling behavior.

Scheduler harus bekerja berdasarkan:

Destination
Media
Schedule
PublishingJob

Provider hanya dipanggil saat worker menjalankan PublishingJob.

==================================================
IMPLEMENTATION RULE
==================================================

Kerjakan secara bertahap:

STEP 1
Audit implementation existing.

STEP 2
Audit schema existing.

STEP 3
Audit queue existing.

STEP 4
Implement/adjust scheduling settings.

STEP 5
Implement next-slot allocation.

STEP 6
Implement sequence.

STEP 7
Implement manual override.

STEP 8
Implement cancellation/rescheduling.

STEP 9
Integrate PublishingJob/queue.

STEP 10
Implement idempotency/concurrency protection.

STEP 11
Implement UI.

STEP 12
Write/update tests.

STEP 13
Run typecheck.

STEP 14
Run lint.

STEP 15
Run full tests.

STEP 16
Run build.

STEP 17
Review git diff.

STEP 18
Update documentation.

==================================================
JANGAN MELAKUKAN
==================================================

JANGAN:

- menghapus architecture existing tanpa alasan
- membuat duplicate scheduler
- membuat duplicate queue
- membuat duplicate Media model
- membuat duplicate PublishingJob model
- membuat Facebook publisher baru
- membuat fake Facebook API
- membuat fake Google Drive API
- mencampur destination
- reset sequence setiap hari
- menggunakan filename sebagai identifier
- menggunakan frontend filter sebagai security
- hardcode Page ID
- hardcode timezone
- hardcode slot
- menyimpan secret di source code
- melakukan destructive migration tanpa alasan
- menghapus test yang gagal
- force push
- membuat commit kosong

==================================================
FINAL VERIFICATION
==================================================

Setelah selesai, tampilkan laporan lengkap:

PHASE 4 STATUS

Implementation:
PASS / INCOMPLETE

DAILY SLOT:
PASS / INCOMPLETE

AUTO SCHEDULING:
PASS / INCOMPLETE

DESTINATION ISOLATION:
PASS / INCOMPLETE

SEQUENCE:
PASS / INCOMPLETE

TIMEZONE:
PASS / INCOMPLETE

MANUAL OVERRIDE:
PASS / INCOMPLETE

RESCHEDULING:
PASS / INCOMPLETE

CANCELLATION:
PASS / INCOMPLETE

IDEMPOTENCY:
PASS / INCOMPLETE

QUEUE INTEGRATION:
PASS / INCOMPLETE

RETRY FOUNDATION:
PASS / INCOMPLETE

UI:
PASS / INCOMPLETE

TEST:
PASS / INCOMPLETE

TYPECHECK:
PASS / INCOMPLETE

LINT:
PASS / INCOMPLETE

BUILD:
PASS / INCOMPLETE

DOCUMENTATION:
PASS / INCOMPLETE

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash jika dibuat>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED / NOT RUN

REMOTE VERIFIED:
YES / NO / NOT RUN

==================================================
OPEN ISSUES
==================================================

Jika masih ada hal yang belum dapat diverifikasi atau belum aman untuk production:

tuliskan secara eksplisit.

Gunakan:

UNKNOWN / NEEDS VERIFICATION

Jangan mengklaim selesai jika sebenarnya belum.

==================================================
STOP CONDITION
==================================================

Setelah Phase 4 selesai:

STOP.

Jangan lanjut ke Phase 5.

Jangan implement Facebook publishing production.

Jangan menambahkan YouTube.

Jangan menambahkan Instagram.

Jangan menambahkan TikTok.

Tunggu instruksi berikutnya.

Tujuan Phase 4 adalah membuat fondasi scheduler yang benar-benar aman untuk:

Page A
Page B
Page C
dan destination platform lain nantinya,

tanpa mencampur media, schedule, queue, sequence, dan history antar destination.

````
# hubungkan Downloader → Media → Google Drive
```
Lanjutkan Content Pilot dari kondisi repository saat ini.

FOCUS PHASE:
Media Pipeline + Downloader → Google Drive → READY

Kondisi:
- Google Drive provider sudah tersedia.
- Storage auth/connection sudah tersedia.
- Test existing harus tetap dipertahankan.
- Destination/Workspace isolation sudah menjadi aturan utama.
- Google Drive adalah primary storage provider pertama.
- Jangan implement provider storage lain.
- Jangan implement Facebook publishing production pada phase ini.
- Jangan membuat fake Google Drive success jika credential live belum tersedia.

TUJUAN UTAMA:

Bangun alur nyata:

Downloader / Manual Upload
        ↓
Media
        ↓
Google Drive
        ↓
StorageObject
        ↓
Media READY
        ↓
siap digunakan Scheduler / Publishing Queue

SEMUA DATA HARUS destination-scoped.

ATURAN DESTINATION:

Setiap Page/Channel memiliki workspace sendiri.

Contoh:

Page A
→ Downloader A
→ Media A
→ Google Drive scope A
→ Storage A

Page B
→ Downloader B
→ Media B
→ Google Drive scope B
→ Storage B

Media Page A tidak boleh muncul di Page B.

Jangan hanya melakukan filtering di frontend.
Backend/database harus melakukan ownership + destination isolation.

MEDIA MODEL:

Audit Media model existing terlebih dahulu.

Pastikan media memiliki identifier stabil.

Minimal konsep:

Media
- id
- destination_id
- source_type
- source_id/source_url jika tersedia
- filename
- mime_type
- size
- duration jika tersedia
- status
- created_at
- updated_at

Jangan membuat model FacebookVideo atau GoogleDriveVideo.

Media harus platform-independent.

SOURCE TYPE:

Gunakan konsep seperti:

manual
downloader
import

Jangan menghapus source metadata.

Jika downloader mengambil video dari Facebook, simpan informasi source secara aman tetapi Media tetap generik.

STORAGE OBJECT:

Pastikan hubungan:

Media
→ StorageObject
→ StorageConnection
→ Google Drive provider

Minimal:

StorageObject
- id
- media_id
- destination_id
- storage_connection_id
- provider_object_id
- path/folder reference
- status
- created_at
- updated_at

provider_object_id adalah ID object Google Drive.

Jangan menggunakan filename sebagai identifier utama.

GOOGLE DRIVE FOLDER:

Gunakan destination-aware structure.

Contoh:

Content Pilot/
├── Page A/
│   ├── Incoming/
│   ├── Ready/
│   ├── Published/
│   └── Failed/
└── Page B/
    ├── Incoming/
    ├── Ready/
    ├── Published/
    └── Failed/

Jika struktur folder provider existing sudah berbeda, gunakan struktur existing dan jangan melakukan migration destruktif.

Folder creation harus idempotent.

Jika folder sudah ada:
→ gunakan folder tersebut.

Jika belum:
→ buat.

Jangan membuat folder duplicate setiap restart/request.

MANUAL UPLOAD:

Audit endpoint manual upload existing.

Jika user berada pada Workspace/Page A:

upload
→ destination_id = Page A
→ Media Page A
→ Google Drive Page A/Incoming
→ StorageObject
→ READY

Jika upload dilakukan pada Page B:
→ seluruh flow menggunakan Page B.

Jangan mengambil destination dari filename atau frontend saja.

DOWNLOADER:

Audit downloader existing.

Downloader harus menerima destination context.

Contoh:

Downloader Page A
→ download video
→ create Media(destination_id=A)
→ upload Google Drive scope A
→ create StorageObject
→ Media READY

Jika downloader belum benar-benar mengambil media dari source tertentu, jangan membuat fake download.

Gunakan abstraction downloader existing.

Jangan mengikat downloader secara permanen ke Facebook jika architecture downloader memang dirancang generic.

DUPLICATE HANDLING:

Audit duplicate detection existing.

Pertahankan constraint/index yang sudah ada.

Jika source media yang sama didownload dua kali:
- jangan membuat duplicate secara tidak sengaja
- gunakan mechanism idempotency existing
- jika duplicate memang harus diizinkan, dokumentasikan alasannya

Jangan menghapus unique constraint existing tanpa alasan.

MEDIA STATUS:

Gunakan status existing jika sudah tersedia.

Jika perlu, pastikan flow minimal dapat membedakan:

UPLOADING
READY
FAILED

Jangan membuat status baru jika enum existing sudah mencukupi.

Jika upload ke Google Drive gagal:

Media
→ FAILED

dan simpan error secara aman.

Jangan menandai READY jika file belum benar-benar tersimpan.

TRANSACTION / FAILURE:

Perhatikan kasus:

1. Media database berhasil dibuat tetapi upload Drive gagal.
2. Upload Drive berhasil tetapi database gagal menyimpan StorageObject.
3. Request terputus di tengah upload.
4. User melakukan retry.
5. Worker/restart terjadi.

Flow harus idempotent dan recovery-safe.

Jangan meninggalkan record seolah-olah READY jika storage object belum valid.

API:

Audit endpoint:

- manual upload
- downloader
- media list
- media detail
- media status
- storage object

Pastikan semua endpoint melakukan:

user ownership
+
destination ownership
+
workspace scope

Media list Page A hanya mengembalikan Page A.

Media detail Page A tidak boleh membuka media Page B.

Jika destination tidak dimiliki user:
gunakan pola error existing, jangan membocorkan keberadaan destination tersebut.

UI:

Audit UI existing.

Jangan membuat halaman baru jika sudah tersedia.

Storage/Media UI harus mengikuti workspace aktif.

Contoh:

Workspace: Page A

Media Library:
- Video 1
- Video 2
- Video 3

Pindah ke Page B:

Media Library:
- hanya media Page B

UI harus memiliki state:

- loading
- empty
- uploading
- ready
- failed
- retry jika sudah didukung

Jangan membuat status CONNECTED/READY palsu.

TESTING:

Tambahkan test untuk:

1. Manual upload Page A menghasilkan media destination A.
2. Manual upload Page B menghasilkan media destination B.
3. Media A tidak muncul pada list Page B.
4. Media detail melakukan destination ownership check.
5. Downloader Page A menghasilkan media destination A.
6. Downloader Page B menghasilkan media destination B.
7. StorageObject menyimpan destination_id yang benar.
8. Google Drive folder scope mengikuti destination.
9. Folder creation idempotent.
10. Duplicate request tidak menghasilkan duplicate object secara tidak sengaja.
11. Google Drive upload failure menghasilkan status FAILED.
12. Retry tidak membuat duplicate folder/object.
13. User tidak dapat mengakses destination user lain.
14. Existing tests tetap PASS.

LIVE GOOGLE DRIVE:

Jika credential Google belum tersedia:

GOOGLE DRIVE LIVE VERIFICATION: NOT RUN

Jangan fake success.

Jika credential sudah tersedia, lakukan verification nyata dengan aman.

Jangan pernah mencetak:
- client secret
- access token
- refresh token

SECURITY:

Periksa:
- authentication
- authorization
- destination isolation
- file type validation
- file size limit
- filename/path safety
- SSRF jika downloader menerima URL
- token security
- secret logging

Jangan commit .env atau credential.

DATABASE:

Sebelum migration:

1. Audit schema existing.
2. Gunakan model/field existing jika sudah tersedia.
3. Tambahkan migration hanya jika benar-benar diperlukan.
4. Jangan destructive migration.
5. Pastikan index destination_id/media_id sesuai kebutuhan.
6. Pastikan migration dapat dijalankan ulang dengan aman sesuai tooling project.

JANGAN:
- mengganti database
- mengganti framework
- membuat storage provider kedua
- membuat Facebook publisher production
- membuat scheduler baru
- membuat queue baru jika fondasinya sudah tersedia
- melakukan massive refactor
- menghapus test
- menghapus documentation

INTEGRATION:

Setelah Media + Storage selesai, pastikan interface siap untuk:

Media READY
→ Daily Slot Scheduler
→ PublishingJob

Tetapi JANGAN implementasikan scheduler phase berikutnya sekarang.

Dokumentasikan integration point saja.

DOCUMENTATION:

Update documentation existing yang relevan:

- STORAGE
- ARCHITECTURE
- DATABASE
- ROADMAP
- UI_DESIGN jika UI berubah

Dokumentasikan:

Downloader
→ Media
→ Google Drive
→ StorageObject
→ READY

dan destination isolation.

VERIFICATION:

Setelah implementation:

1. pnpm typecheck
2. pnpm lint
3. pnpm test
4. pnpm build

Gunakan command yang benar berdasarkan package.json/repository actual.

Jangan mengarang hasil test.

Periksa git diff.

Pastikan tidak ada secret.

GIT:

Jika semua PASS:

- git status
- inspect diff
- commit perubahan phase ini
- push ke branch aktif sesuai workflow existing
- verify remote

Jangan force push.
Jangan commit .env.
Jangan membuat empty commit.

FINAL REPORT:

Tampilkan:

MEDIA PIPELINE: PASS/PARTIAL
MANUAL UPLOAD: PASS/PARTIAL
DOWNLOADER: PASS/PARTIAL
GOOGLE DRIVE STORAGE: PASS/PARTIAL
DESTINATION ISOLATION: PASS/PARTIAL
STORAGE OBJECT: PASS/PARTIAL
DUPLICATE HANDLING: PASS/PARTIAL
ERROR RECOVERY: PASS/PARTIAL
UI: PASS/PARTIAL

TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL (jumlah)
BUILD: PASS/FAIL

GOOGLE DRIVE LIVE VERIFICATION:
PASS / NOT RUN

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

PUSH STATUS:
SUCCESS / NOT NEEDED / FAILED

OPEN ISSUES:
<jika ada>

NEXT RECOMMENDED PHASE:
Phase 4 — Daily Slot & Auto-Publishing Scheduler.

STOP setelah laporan.

````
# Google Drive → Destination/Workspace Isolation
```

Lanjutkan implementasi Content Pilot dari kondisi repository saat ini.

FOKUS PHASE INI:
Google Drive Storage + Destination/Workspace Isolation.

JANGAN mengubah scope menjadi provider lain.
JANGAN implement Facebook publishing production.
JANGAN implement YouTube/Instagram/TikTok.
JANGAN melakukan refactor besar yang tidak diperlukan.

KONDISI SAAT INI:
- Google Drive storage provider sudah memiliki fondasi implementation.
- GoogleDriveAuthProvider sudah terdaftar di StorageRegistry.
- createStorageAuthRegistry() sudah tersedia.
- API storage connection sudah tersedia.
- UI Storage sudah memiliki Connect/Disconnect.
- Test, typecheck, lint, dan build sebelumnya PASS.
- Live Google Drive verification belum dilakukan karena credential Google belum tersedia.
- META_APP_ID dan META_APP_SECRET sudah tersimpan di .env, jangan tampilkan atau log secret tersebut.

TUJUAN:
Pastikan Google Drive benar-benar terintegrasi dengan konsep Destination/Workspace, sehingga setiap Facebook Page memiliki workspace dan media storage yang terisolasi.

ARSITEKTUR TARGET:

User
│
├── Facebook Account A
│   ├── Page A
│   │   └── Workspace Page A
│   │       ├── Downloader
│   │       ├── Storage
│   │       ├── Publish
│   │       ├── Queue
│   │       ├── Schedule
│   │       └── History
│   │
│   └── Page B
│       └── Workspace Page B
│           ├── Downloader
│           ├── Storage
│           ├── Publish
│           ├── Queue
│           ├── Schedule
│           └── History
│
└── Facebook Account B
    └── Page C
        └── Workspace Page C

ATURAN ISOLASI:

1. Setiap Destination memiliki workspace sendiri secara logical.
2. Semua media harus memiliki destination_id.
3. Semua publishing job harus memiliki destination_id.
4. Schedule harus memiliki destination_id.
5. Queue/job processing harus mempertahankan destination scope.
6. History harus dapat difilter berdasarkan destination.
7. Storage object harus mengetahui destination yang memilikinya.
8. Downloader yang dijalankan dari Page A otomatis memasukkan media ke Page A.
9. Downloader Page A tidak boleh memasukkan media ke Page B.
10. Storage Page A tidak boleh menampilkan media Page B.
11. Publish Page A tidak boleh mengambil media Page B secara tidak sengaja.
12. Scheduler Page A tidak boleh mengambil job Page B.
13. Queue Page A tidak boleh memproses job Page B karena kesalahan scope.
14. Setiap API endpoint yang menerima destinationId wajib melakukan authorization/ownership check.
15. Jangan hanya melakukan filtering di frontend. Isolation harus ditegakkan di backend/query/database layer.
16. Jika destination tidak dimiliki user/session yang aktif, response harus 404/unauthorized sesuai pola keamanan project yang sudah ada.
17. Jangan membocorkan keberadaan destination milik user lain melalui error response.

GOOGLE DRIVE:

Google Drive adalah PRIMARY STORAGE PROVIDER pertama.

Gunakan abstraction yang sudah tersedia.

Target:

StorageProvider
└── GoogleDriveStorage

Jangan menanam logic Google Drive langsung ke:
- Downloader
- Scheduler
- Queue
- Facebook Provider
- Publishing Worker

Semua komunikasi Google Drive harus melalui storage abstraction/provider.

STORAGE CONNECTION:

Pertahankan konsep StorageConnection.

Minimal informasi logical:

StorageConnection
- id
- provider
- owner/account scope
- status
- credential reference
- created_at
- updated_at

Jangan menyimpan access token/refresh token plaintext jika architecture existing sudah menyediakan encrypted storage.

Jangan pernah:
- console.log token
- return token melalui API response
- menampilkan secret di UI
- commit .env
- menulis credential ke test fixture secara plaintext

STORAGE OBJECT:

Pastikan logical metadata dapat merepresentasikan:

StorageObject
- id
- media_id
- destination_id
- storage_connection_id
- provider_object_id
- path/folder reference
- status
- created_at
- updated_at

media_id adalah identifier utama Content Pilot.

provider_object_id adalah ID object dari Google Drive.

Jangan menggunakan:
- filename
- Google Drive filename
- folder name

sebagai primary identifier.

GOOGLE DRIVE FOLDER SCOPE:

Gunakan struktur logical seperti:

Content Pilot/
├── Page A/
│   ├── Incoming/
│   ├── Ready/
│   ├── Published/
│   └── Failed/
│
└── Page B/
    ├── Incoming/
    ├── Ready/
    ├── Published/
    └── Failed/

Folder naming boleh mengikuti implementation yang sudah ada, tetapi jangan merusak data existing.

Jika Google Drive folder structure belum dibuat, implementasikan secara aman melalui provider.

Setiap destination harus memiliki folder scope yang stabil.

Jangan membuat folder baru setiap kali aplikasi restart.

Gunakan metadata/database provider_object_id atau mekanisme idempotent yang sesuai.

FOLDER CREATION HARUS IDEMPOTENT.

Jika folder Page A sudah ada:
→ gunakan folder tersebut.

Jika belum ada:
→ buat.

Jika request diulang:
→ jangan membuat duplicate folder.

MEDIA FLOW:

Downloader / Manual Upload
        ↓
Media
        ↓
Google Drive Storage
        ↓
StorageObject
        ↓
Media READY
        ↓
Scheduler
        ↓
PublishingJob
        ↓
Queue
        ↓
Worker

Semua tahap harus mempertahankan destination_id.

CONTOH:

Downloader Page A
→ Media 001
→ destination_id = PAGE_A
→ Google Drive Page A/Incoming
→ READY

Downloader Page B
→ Media 002
→ destination_id = PAGE_B
→ Google Drive Page B/Incoming
→ READY

Jangan sampai:

Media 001 Page A
→ terlihat di Storage Page B.

API REQUIREMENTS:

Audit endpoint storage yang sudah ada.

Periksa:
- connect
- disconnect
- status
- folders
- upload
- list
- delete/move jika sudah tersedia

Pastikan setiap endpoint yang terkait destination menggunakan ownership check.

Jika endpoint existing belum destination-scoped tetapi seharusnya scoped, perbaiki dengan perubahan minimum yang konsisten dengan architecture existing.

Jangan membuat endpoint duplicate.

Gunakan naming convention project yang sudah ada.

UI REQUIREMENTS:

UI harus mengikuti workspace yang sedang aktif.

Contoh:

User sedang berada di:

Facebook → Page A

Maka halaman Storage harus menampilkan:

Storage — Page A

dan hanya media/storage object milik Page A.

Jika user pindah:

Facebook → Page B

maka:

Storage — Page B

dan hanya media Page B yang tampil.

Workspace switcher harus mempertahankan context.

Jangan mengandalkan query frontend saja.

Backend tetap wajib melakukan isolation.

UI Storage minimal harus dapat menunjukkan:
- connected/disconnected
- provider Google Drive
- destination/workspace aktif
- storage status
- media/file list jika endpoint tersebut sudah tersedia
- loading state
- empty state
- error state

Jangan membuat fake connected status.

Jika Google credential belum tersedia:
tampilkan status yang jujur seperti:
NOT CONFIGURED

Jangan mengatakan:
CONNECTED

hanya karena provider class tersedia.

TESTING:

Tambahkan atau perbaiki test untuk memastikan:

1. User dapat melihat storage destination miliknya.
2. User tidak dapat melihat storage destination milik user/destination lain.
3. Media Page A tidak muncul di Page B.
4. Upload Page A menggunakan destination_id Page A.
5. Upload Page B menggunakan destination_id Page B.
6. Storage object menyimpan destination_id yang benar.
7. Folder creation Google Drive bersifat idempotent.
8. Disconnect tidak membocorkan credential.
9. Invalid destination menghasilkan response keamanan yang sesuai.
10. Missing destination menghasilkan error yang konsisten.
11. API tidak menerima destination milik user lain.
12. Existing tests tetap PASS.

TEST TANPA CREDENTIAL GOOGLE:

Jika credential Google Drive belum tersedia di environment:
- jangan membuat fake live success
- jangan mengarang hasil Google API
- gunakan mock/unit test untuk provider
- tandai live verification sebagai NOT RUN / NEEDS CONFIGURATION

LIVE VERIFICATION:

Jangan mengklaim Google Drive live integration PASS jika:
GOOGLE_CLIENT_ID
GOOGLE_CLIENT_SECRET
atau credential lain yang memang diperlukan belum tersedia.

Jika environment sudah memiliki credential:
lakukan verification secara aman.

Jika belum:
laporkan:

GOOGLE DRIVE LIVE VERIFICATION: NOT RUN
REASON: Google OAuth credentials not configured

SECURITY:

Periksa:
- authorization
- ownership check
- destination isolation
- token encryption
- CSRF jika relevan
- SSRF jika ada URL-based import
- file validation
- file size limits
- path traversal
- secret logging

Jangan menampilkan secret dalam output.

DATABASE:

Sebelum migration:
- audit schema existing
- jangan membuat tabel duplicate
- gunakan model existing jika sudah tersedia
- tambahkan kolom/index/constraint hanya jika memang diperlukan

Jika destination_id sudah tersedia:
gunakan yang sudah ada.

Jika belum:
buat migration minimal yang sesuai architecture.

Pastikan index/query untuk:
destination_id
media_id
storage_connection_id

sesuai kebutuhan.

UNIQUE / IDEMPOTENCY:

Pastikan duplicate media/storage object dapat dicegah dengan mechanism yang sudah digunakan project.

Jangan menghapus duplicate-index protection yang sudah ada.

Jika sudah ada UNIQUE(media_id) atau constraint terkait:
pertahankan dan sesuaikan dengan destination scope hanya jika architecture memang mengharuskannya.

Jangan melakukan migration destruktif.

DOCUMENTATION:

Update dokumentasi yang relevan:

- docs/ARCHITECTURE.md
- docs/STORAGE.md jika sudah ada
- docs/DATABASE.md
- docs/ROADMAP.md
- docs/UI_DESIGN.md jika perubahan UI perlu didokumentasikan

Jangan membuat duplicate documentation jika file dengan tujuan sama sudah ada.

Dokumentasikan:

1. Google Drive sebagai primary storage provider pertama.
2. Storage abstraction.
3. Destination-scoped storage.
4. Workspace isolation.
5. Google Drive folder structure.
6. StorageConnection.
7. StorageObject.
8. Media lifecycle.
9. Security/ownership checks.
10. Future storage providers.

Jangan menambahkan provider lain sekarang.

CODE QUALITY:

Ikuti architecture existing.

Jangan:
- membuat giant file
- membuat duplicate service
- membuat duplicate API
- membuat duplicate provider
- menghapus test existing
- menghapus documentation existing tanpa alasan
- melakukan massive refactor
- mengganti framework
- mengganti database
- mengganti queue

Gunakan module/file yang sudah ada jika memang sesuai.

HASIL YANG DIHARAPKAN:

Setelah implementasi:

User
→ Destination Page A
→ Workspace Page A
→ Downloader
→ Media
→ Google Drive Storage A

dan:

User
→ Destination Page B
→ Workspace Page B
→ Downloader
→ Media
→ Google Drive Storage B

harus benar-benar terisolasi.

Satu user dapat memiliki banyak Page.

Satu Facebook Account dapat memiliki banyak Page.

Satu Page memiliki workspace sendiri.

Storage harus mengikuti workspace tersebut.

Jangan menganggap satu Facebook Account = satu Page.

Jangan menganggap satu Google Drive connection = satu Page.

Google Drive connection dapat menjadi credential/provider connection, sedangkan logical storage scope tetap ditentukan oleh destination/workspace.

SEBELUM CODING:

1. Audit repository actual.
2. Audit implementation Google Drive yang sudah ada.
3. Audit Destination model.
4. Audit Media model.
5. Audit Storage model.
6. Audit API routes.
7. Audit UI Storage.
8. Audit authorization/ownership checks.
9. Tentukan perubahan minimum yang diperlukan.

Jangan mengubah sesuatu yang sebenarnya sudah benar.

IMPLEMENTASI:

Kerjakan hanya perubahan yang diperlukan untuk:

Google Drive
+
Destination/Workspace Isolation.

Setelah selesai:

1. Typecheck.
2. Lint.
3. Test seluruh suite.
4. Build.
5. Periksa git diff.
6. Pastikan tidak ada secret.
7. Pastikan tidak ada perubahan unrelated.
8. Verifikasi migration jika ada.
9. Verifikasi API isolation.
10. Verifikasi UI workspace context.
11. Verifikasi Google Drive provider secara mock jika credential belum tersedia.

GIT:

Jika project menggunakan Git workflow yang sudah ada:

- jangan force push
- jangan commit secret
- jangan commit .env
- jangan membuat commit kosong
- commit hanya perubahan phase ini
- push hanya jika workflow project memang mengharuskan push

Jangan mengklaim remote verified jika belum benar-benar diverifikasi.

FINAL REPORT:

Tampilkan:

GOOGLE DRIVE PROVIDER: PASS / PARTIAL
DESTINATION ISOLATION: PASS / PARTIAL
WORKSPACE ISOLATION: PASS / PARTIAL
STORAGE API: PASS / PARTIAL
DATABASE: PASS / NO CHANGES
UI: PASS / PARTIAL
AUTHORIZATION: PASS / PARTIAL
TEST: PASS (jumlah test)
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
BUILD: PASS/FAIL

GOOGLE DRIVE LIVE VERIFICATION:
PASS / NOT RUN
Reason jika NOT RUN.

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash jika ada>

PUSH STATUS:
SUCCESS / NOT NEEDED / FAILED

OPEN ISSUES:
<jika ada>

NEXT RECOMMENDED STEP:
Lanjutkan ke integrasi Media Pipeline + Downloader → Google Drive → READY dengan destination scope yang sama.

STOP setelah laporan.
````
# 
```
LANJUTKAN PROJECT CONTENT PILOT.

PHASE 5 SUDAH SELESAI. JANGAN MENGULANG PHASE 1–5.

SEBELUM LANJUT CODING, AUDIT REPOSITORY TERAKHIR DAN SESUAIKAN IMPLEMENTASI DENGAN ARSITEKTUR YANG SUDAH ADA.

==================================================
FOKUS SEKARANG — GOOGLE DRIVE STORAGE
==================================================

Kita ingin menjadikan Google Drive sebagai STORAGE PROVIDER PERTAMA Content Pilot.

Jangan implementasikan S3, R2, Dropbox, OneDrive, MinIO, atau storage provider lain dulu.

Namun architecture WAJIB menggunakan abstraction agar provider lain dapat ditambahkan nanti tanpa membongkar Media Pipeline.

Target:

StorageProvider
└── GoogleDriveStorage

Provider masa depan:

- S3
- Cloudflare R2
- MinIO
- VPS/Local
- Dropbox
- OneDrive

Belum perlu diimplementasikan.

==================================================
1. AUDIT TERLEBIH DAHULU
==================================================

Periksa implementasi existing:

- Media
- Storage
- Downloader
- Destination
- Workspace
- Facebook Account
- Facebook Page
- PublishingJob
- Queue
- Scheduler
- OAuth
- environment configuration
- database
- existing storage service
- existing Google/Microsoft/cloud integration jika ada

Jangan membuat duplicate service/model.

Jika StorageProvider sudah ada:

REUSE.

Jika belum:

buat abstraction minimal yang benar.

==================================================
2. GOOGLE DRIVE SEBAGAI PRIMARY STORAGE
==================================================

Google Drive bukan hanya backup.

Google Drive menjadi media storage utama pada fase ini.

Flow:

Downloader / Manual Upload
        ↓
Media Pipeline
        ↓
Google Drive
        ↓
Media READY
        ↓
Scheduler
        ↓
PublishingJob
        ↓
Queue
        ↓
Worker
        ↓
Facebook Provider

Database Content Pilot tetap menjadi source of truth untuk:

- media status
- destination
- publishing status
- schedule
- queue
- history

Jangan menjadikan folder/nama file Google Drive sebagai source of truth.

==================================================
3. DESTINATION-SCOPED STORAGE
==================================================

Setiap Page/Destination memiliki storage scope sendiri.

Contoh:

Facebook Account
├── Page A
│   └── Workspace A
│       └── Google Drive
│
└── Page B
    └── Workspace B
        └── Google Drive

Page A tidak boleh melihat media Page B.

Page B tidak boleh melihat media Page A.

Backend wajib melakukan authorization.

Jangan hanya melakukan filter di frontend.

==================================================
4. GOOGLE DRIVE FOLDER STRUCTURE
==================================================

Gunakan struktur logical:

Content Pilot/
├── Page A/
│   ├── Incoming/
│   ├── Ready/
│   ├── Published/
│   └── Failed/
│
└── Page B/
    ├── Incoming/
    ├── Ready/
    ├── Published/
    └── Failed/

Namun jangan bergantung pada folder untuk menentukan status.

Status utama tetap berada di database.

Google Drive folder ID harus disimpan sebagai provider-specific metadata/reference.

Jangan menggunakan filename sebagai identifier utama.

==================================================
5. MEDIA MODEL
==================================================

Pastikan Media tetap platform-independent.

Minimal:

Media
- id
- destination_id
- source_type
- source_id/source_url jika tersedia
- filename
- mime_type
- file_size
- duration
- width
- height
- checksum jika tersedia
- status
- created_at
- updated_at

Jangan membuat:

FacebookVideo
GoogleDriveVideo
DownloaderVideo

sebagai model utama.

==================================================
6. STORAGE MODEL
==================================================

Jika belum ada model yang tepat, gunakan konsep:

StorageConnection
- id
- provider
- owner/user scope
- status
- credentials/reference
- metadata
- created_at
- updated_at

StorageObject
- id
- media_id
- destination_id
- storage_connection_id
- provider_object_id
- path/folder reference
- status
- metadata
- created_at
- updated_at

Sesuaikan dengan schema existing.

Jangan membuat tabel duplicate jika model existing sudah mencukupi.

==================================================
7. GOOGLE DRIVE AUTHENTICATION
==================================================

Research dan gunakan Google Drive API/OAuth resmi.

Verifikasi:

- OAuth authorization
- callback
- state validation
- access token
- refresh token
- token expiration
- reconnect
- revoke/disconnect
- required scopes

Jangan mengarang OAuth scope.

Jangan menyimpan token plaintext jika architecture security mengharuskan encryption.

Jangan memasukkan token ke log.

Jangan memasukkan token ke Git.

Jika credential Google belum tersedia:

implementasikan integration dengan aman tetapi:

GOOGLE DRIVE LIVE VERIFICATION:
NOT RUN

Jangan membuat fake connected status.

==================================================
8. GOOGLE DRIVE API
==================================================

Gunakan official Google Drive API.

Verifikasi kemampuan:

- create folder
- find folder
- upload file
- resumable upload
- list files
- get metadata
- download/stream
- update/move file
- delete file
- permission/access
- quota/error handling

Jangan mengarang endpoint.

Jika kemampuan tertentu belum diverifikasi:

NEEDS VERIFICATION

==================================================
9. STORAGE PROVIDER ABSTRACTION
==================================================

Buat interface generik sesuai architecture existing.

Minimal capability:

- connect
- disconnect
- createFolder
- ensureFolder
- upload
- download/stream
- getMetadata
- list
- move/update
- delete
- exists

Jangan membuat method yang tidak dibutuhkan hanya untuk terlihat lengkap.

Provider-specific implementation:

GoogleDriveStorage

Core tidak boleh memanggil Google Drive API secara langsung.

Contoh:

MediaService
→ StorageProvider
→ GoogleDriveStorage
→ Google Drive API

Bukan:

MediaService
→ GoogleDrive API

==================================================
10. DOWNLOADER
==================================================

Downloader existing harus menggunakan storage abstraction.

Flow:

Downloader
→ Media
→ GoogleDriveStorage.upload()
→ StorageObject
→ Media READY

Downloader tidak boleh memiliki logic Google Drive langsung.

Manual upload juga harus menggunakan flow yang sama.

==================================================
11. MANUAL UPLOAD
==================================================

Workspace Page A:

Storage
→ Upload

File:

video1.mp4

Flow:

Upload
→ validation
→ Media record
→ Google Drive Incoming
→ processing
→ Ready
→ database status READY

Page B harus masuk ke folder/storage scope Page B.

==================================================
12. IMPORT DARI GOOGLE DRIVE
==================================================

Google Drive juga harus dapat menjadi SOURCE MEDIA.

Contoh:

Google Drive
→ pilih file
→ Import
→ Content Pilot Media
→ READY
→ Scheduler

Jika file sudah berada di Google Drive yang terhubung:

jangan mengunduh ulang tanpa alasan.

Simpan provider_object_id.

Jika architecture memungkinkan streaming langsung, gunakan abstraction yang aman.

Jika pipeline membutuhkan local processing:

gunakan temporary download/cache lalu proses ke storage sesuai architecture.

Jangan membuat duplicate media tanpa alasan.

==================================================
13. GOOGLE DRIVE MEDIA LIBRARY
==================================================

Storage Page A harus menampilkan media yang memang terkait Page A.

UI minimal:

- thumbnail
- filename
- status
- size
- duration
- source
- created time
- actions

Actions:

View
Import
Delete
Retry jika FAILED

Jangan menampilkan media Page lain.

==================================================
14. MEDIA ID VS GOOGLE DRIVE ID
==================================================

WAJIB dibedakan.

Contoh:

Content Pilot:

media_id =
cp-media-123

Google Drive:

provider_object_id =
1AbCdEf...

Jangan menggunakan Google Drive file ID sebagai Media ID.

Media harus tetap platform/storage-independent.

==================================================
15. STORAGE DELETION
==================================================

Delete Media harus aman.

Jangan hanya:

DELETE database record

tanpa menangani file Google Drive.

Jangan hanya:

DELETE Google Drive file

tanpa menangani database.

Gunakan service abstraction.

Pertimbangkan:

- soft delete
- storage cleanup
- active publishing job
- history

Jangan menghapus media yang sedang digunakan job aktif tanpa aturan.

==================================================
16. STORAGE ERROR
==================================================

Tangani:

- authentication expired
- permission denied
- quota exceeded
- file not found
- upload failure
- download failure
- network timeout
- Google API error
- rate limit

Bedakan:

temporary
dan
permanent.

Temporary dapat retry.

Permanent harus meminta reconnect/fix configuration.

==================================================
17. RETRY & IDEMPOTENCY
==================================================

Upload harus idempotent jika memungkinkan.

Jika worker restart ketika upload sedang berlangsung:

jangan membuat file duplicate tanpa kontrol.

Gunakan:

- media_id
- storage operation ID
- checksum
- provider object ID

sesuai architecture.

Jangan mengklaim exactly-once jika implementasinya tidak benar-benar menjamin itu.

==================================================
18. SECURITY
==================================================

WAJIB periksa:

- OAuth state
- CSRF
- token encryption
- secret handling
- destination isolation
- storage authorization
- path traversal
- filename sanitization
- MIME validation
- file size
- SSRF jika remote URL digunakan
- Google Drive permission handling
- log leakage

Jangan mengembalikan access/refresh token ke frontend.

Jangan memasukkan token ke error response.

==================================================
19. GOOGLE DRIVE ACCOUNT UI
==================================================

Tambahkan/gunakan halaman Storage Settings sesuai UI existing.

Contoh:

Storage

Google Drive
Status: Connected

[Connect]
[Reconnect]
[Disconnect]

Connected account:
user@example.com

Jangan menampilkan token.

Jika belum connected:

Google Drive
Status: Not Connected

[Connect Google Drive]

Status harus berasal dari backend nyata.

Jangan fake.

==================================================
20. DESTINATION STORAGE SETTINGS
==================================================

Setiap Page dapat menentukan Google Drive storage connection/folder scope.

Contoh:

Page A

Storage:
Google Drive

Folder:
Content Pilot / Page A

Page B:

Storage:
Google Drive

Folder:
Content Pilot / Page B

Jika satu Google Drive account digunakan untuk beberapa Page:

tetap pisahkan folder berdasarkan destination.

==================================================
21. STORAGE POLICY
==================================================

Siapkan struktur untuk policy per Destination:

- primary storage
- retention
- delete after publish
- keep original
- keep thumbnail

Untuk sekarang:

PRIMARY STORAGE:
Google Drive

Jangan implement backup provider.

Jika policy belum diperlukan oleh existing architecture, dokumentasikan sebagai future capability dan jangan membuat complexity berlebihan.

==================================================
22. SCHEDULER
==================================================

Jangan membuat scheduler baru.

Gunakan scheduler Phase 4.

Media:

READY

↓

Scheduler

↓

PublishingJob

Google Drive hanya menjadi storage layer.

Jangan mencampur:

storage status
dengan
publishing status.

==================================================
23. FACEBOOK PROVIDER
==================================================

Jangan mengubah Facebook provider hanya untuk membuat Google Drive bekerja.

Facebook provider mendapatkan media melalui Media/Storage abstraction.

Flow:

PublishingJob
→ MediaService
→ StorageProvider
→ GoogleDriveStorage
→ stream/file
→ FacebookProvider
→ Meta API

Jangan:

FacebookProvider
→ Google Drive API

==================================================
24. QUEUE / WORKER
==================================================

Jangan membuat queue baru.

Gunakan queue existing.

Flow:

Media READY
→ Scheduler
→ PublishingJob
→ Queue
→ Worker
→ Provider

Google Drive operations harus aman terhadap worker restart.

==================================================
25. TESTING
==================================================

Minimal test:

1. Google Drive provider registration.
2. OAuth state validation.
3. Google Drive connection.
4. Connection status.
5. Reconnect.
6. Disconnect.
7. Folder creation.
8. Destination folder isolation.
9. Upload file.
10. StorageObject creation.
11. Media READY.
12. Import existing Drive file.
13. List media.
14. Metadata retrieval.
15. Download/stream.
16. Delete.
17. Permission error.
18. Token expired.
19. Quota error.
20. Temporary network failure.
21. Retry.
22. Idempotent upload.
23. Page A cannot access Page B media.
24. Page B cannot access Page A media.
25. Google Drive ID never becomes Media ID.
26. Existing Phase 1–5 tests remain PASS.

Jika live Google OAuth credential tidak tersedia:

GOOGLE DRIVE LIVE TEST:
NOT RUN

Jangan membuat fake PASS.

Unit tests tetap harus dijalankan.

==================================================
26. DOCUMENTATION
==================================================

Update documentation existing.

Minimal:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md
docs/UI_DESIGN.md

Jika storage documentation sudah ada, update file tersebut.

Dokumentasikan:

- Google Drive provider
- OAuth
- storage abstraction
- folder structure
- destination isolation
- Media/StorageObject relationship
- import
- upload
- delete
- retry
- error handling
- security
- known limitations

Jangan membuat duplicate documentation.

==================================================
27. ENVIRONMENT
==================================================

Jika implementation membutuhkan environment variables:

tambahkan hanya nama variable ke .env.example.

Jangan masukkan credential nyata.

Contoh placeholder sesuai architecture actual.

Pastikan .env tetap ignored.

Jangan mencetak secret saat testing/reporting.

==================================================
28. GIT
==================================================

Sebelum commit:

git status
inspect diff
secret scan
typecheck
lint
test
build

Pastikan tidak ada:

- Google OAuth secret
- client secret
- access token
- refresh token
- META_APP_SECRET
- password
- API key

Commit hanya perubahan yang berkaitan dengan Google Drive Storage.

Gunakan commit message yang sesuai, misalnya:

feat: add google drive storage provider

Push ke branch yang sedang digunakan.

Jangan force push.

Setelah push:

GIT STATUS: CLEAN
COMMIT: <actual hash>
BRANCH: <actual branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

==================================================
29. ACCEPTANCE CRITERIA
==================================================

Phase ini dianggap selesai jika:

AC-01
StorageProvider abstraction tersedia/reused.

AC-02
GoogleDriveStorage tersedia.

AC-03
Google Drive OAuth aman.

AC-04
Google Drive connection status nyata.

AC-05
Destination dapat memiliki Google Drive storage scope.

AC-06
Page A dan Page B terisolasi.

AC-07
Manual upload bekerja melalui Google Drive provider.

AC-08
Downloader bekerja melalui Google Drive provider.

AC-09
Import dari Google Drive bekerja jika credential/API tersedia.

AC-10
Media tetap platform-independent.

AC-11
Google Drive file ID bukan Media ID.

AC-12
StorageObject menyimpan provider reference.

AC-13
Delete aman.

AC-14
Retry/idempotency ditangani.

AC-15
Token tidak bocor.

AC-16
Typecheck PASS.

AC-17
Lint PASS.

AC-18
Test PASS.

AC-19
Build PASS.

AC-20
Git CLEAN.

AC-21
Push SUCCESS.

==================================================
FINAL REPORT
==================================================

Tampilkan:

GOOGLE DRIVE STORAGE STATUS:
PASS / PARTIAL / BLOCKED

STORAGE ABSTRACTION:
PASS / FAIL

GOOGLE OAUTH:
PASS / NOT CONFIGURED / NEEDS VERIFICATION

UPLOAD:
PASS / FAIL

IMPORT:
PASS / FAIL / NOT VERIFIED

DOWNLOADER:
PASS / FAIL

DESTINATION ISOLATION:
PASS / FAIL

MEDIA INTEGRATION:
PASS / FAIL

DELETE:
PASS / FAIL

RETRY:
PASS / FAIL

IDEMPOTENCY:
PASS / FAIL

SECURITY:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

PUSH:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

LIVE GOOGLE DRIVE TEST:
PASS / NOT RUN

Jika live test tidak dijalankan karena credential belum tersedia, katakan secara jujur.

==================================================
STOP CONDITION
==================================================

Setelah Google Drive Storage selesai:

STOP.

Jangan implementasikan:

- S3
- Cloudflare R2
- Dropbox
- OneDrive
- MinIO
- storage provider lain
- provider sosial baru
- YouTube
- Instagram
- TikTok

Jangan membuat fake Google Drive connection.

Jangan membuat fake upload success.

Jangan membuat fake file ID.

Jangan mengubah status menjadi READY jika file sebenarnya belum berhasil tersimpan/tervalidasi.

Fokus hanya pada:

GOOGLE DRIVE STORAGE PROVIDER

dan integrasinya dengan Media/Downloader/Workspace yang sudah ada.

Kerjakan berdasarkan repository aktual, bukan asumsi.

````
# Phase 5 — Facebook Provider & Publishing.
```
PHASE 5 — FACEBOOK PROVIDER & PUBLISHING

Kita lanjutkan project Content Pilot dari kondisi repository TERAKHIR.

JANGAN mengulang pekerjaan Phase 0–4 yang sudah selesai.
JANGAN merombak architecture yang sudah ada hanya karena ingin membuat versi sendiri.
Audit implementasi yang sudah ada terlebih dahulu dan lanjutkan dari struktur aktual repository.

==================================================
TUJUAN PHASE 5
==================================================

Implementasikan Facebook sebagai provider publishing pertama dengan architecture yang sudah dibuat sebelumnya.

Facebook harus tetap menjadi PROVIDER, bukan core system.

Core system tidak boleh dipenuhi logic khusus Facebook.

Target:

User
 → Facebook Account
   → multiple Facebook Pages
     → masing-masing Page memiliki Destination Workspace
       → Downloader
       → Storage
       → Publish
       → Queue
       → Schedule
       → History

Setiap Page harus terisolasi berdasarkan destination_id.

==================================================
ATURAN WAJIB
==================================================

1. Jangan membuat fake Facebook success.
2. Jangan membuat fake PUBLISHED.
3. Jangan menggunakan username/password Facebook automation.
4. Gunakan official Meta/Facebook API.
5. Jangan mengarang endpoint atau permission.
6. Sebelum implementasi endpoint yang belum jelas, lakukan verifikasi dokumentasi resmi Meta.
7. Jika suatu kemampuan belum dapat diverifikasi, tandai NEEDS VERIFICATION dan jangan menganggapnya tersedia.
8. Jangan commit META_APP_SECRET, access token, refresh token, API key, password, cookie, atau credential lain.
9. Jangan menaruh secret di source code.
10. Jangan mengubah .env.example menjadi berisi secret nyata.
11. Jangan menghapus fitur Phase 1–4 yang sudah bekerja.
12. Jangan membuat duplicate scheduler, queue, storage, atau destination system.
13. Gunakan service/core yang sudah ada.
14. Facebook-specific logic harus berada di Facebook provider/module.
15. Jangan membuat seluruh Facebook integration menjadi satu giant file.
16. Jangan mengubah platform-independent core menjadi Facebook-specific.
17. Jangan melakukan destructive migration.
18. Jangan menghapus data existing.
19. Jangan mengubah schema existing tanpa migration yang jelas dan diperlukan.
20. Jangan melakukan fake live verification.
21. Jangan mengklaim Facebook publishing LIVE jika credential/provider configuration belum tersedia.
22. Setelah implementation selesai, lakukan typecheck, lint, test, build, dan pemeriksaan Git.
23. STOP setelah Phase 5 selesai.

==================================================
LANGKAH 1 — AUDIT IMPLEMENTASI PHASE 1–4
==================================================

Sebelum coding, periksa repository aktual.

Periksa:

- provider registry
- platform abstraction
- destination model
- PlatformConnection
- Facebook provider jika sudah ada
- authentication
- OAuth callback
- account discovery
- destination discovery
- destination workspace
- media
- storage
- downloader
- publishing job
- queue
- worker
- scheduler
- daily slot
- sequence
- retry
- idempotency
- history
- audit log
- UI workspace
- existing Facebook routes
- existing Meta configuration
- database migrations
- environment configuration
- tests
- documentation

Jangan membuat ulang sesuatu yang sudah ada.

Buat keputusan:

EXISTS AND REUSE
EXISTS BUT NEEDS EXTENSION
MISSING AND MUST CREATE
NOT NEEDED

Laporkan secara singkat sebelum implementation.

==================================================
LANGKAH 2 — VERIFIKASI META/FACEBOOK API
==================================================

Gunakan dokumentasi resmi Meta sebagai sumber utama.

Verifikasi kondisi API yang benar-benar digunakan oleh repository saat ini.

Minimal periksa:

- Meta App configuration
- OAuth flow
- redirect URI
- access token
- Page access token jika memang diperlukan oleh flow
- Page discovery
- Page ID
- Page name
- Page connection
- Page permission
- video publishing
- Reels publishing
- photo publishing
- text/link publishing jika memang masuk scope Phase 5
- publishing status
- error response
- token expiration
- permission errors
- rate limits
- upload requirements

Jangan memperluas scope hanya karena API mendukung banyak fitur.

Prioritas Phase 5:

1. Facebook account connection
2. Page discovery
3. Destination connection
4. Video publishing capability yang sudah diverifikasi
5. Publishing status
6. Error handling
7. Queue integration
8. History

Reels atau content type lain hanya implementasikan jika memang sudah jelas dari architecture dan dokumentasi resmi.

Jika sebuah endpoint/permission berubah atau tidak dapat diverifikasi:

MARK:

NEEDS VERIFICATION

Jangan membuat implementasi palsu.

==================================================
LANGKAH 3 — FACEBOOK PROVIDER ARCHITECTURE
==================================================

Pastikan Facebook berada di provider/module sendiri.

Gunakan struktur yang sesuai repository aktual.

Contoh konsep:

platforms/
  facebook/
    auth/
    accounts/
    destinations/
    publishing/
    media/
    api/
    facebook.provider.ts

Tetapi JANGAN memaksakan struktur tersebut jika repository sudah mempunyai struktur modular yang lebih baik.

Facebook provider minimal harus bertanggung jawab terhadap:

- authentication integration
- account information
- destination discovery
- destination validation
- capability reporting
- media validation
- publishing
- status mapping
- provider error mapping

Core tetap bertanggung jawab terhadap:

- users
- media
- publishing jobs
- queue
- scheduler
- retry policy
- history
- audit
- authorization
- destination isolation

==================================================
LANGKAH 4 — FACEBOOK ACCOUNT
==================================================

Pastikan satu User dapat memiliki banyak PlatformConnection.

Contoh:

User A
 ├── Facebook Account 1
 │    ├── Page A
 │    └── Page B
 │
 └── Facebook Account 2
      ├── Page C
      └── Page D

Jangan membuat:

user.facebookAccount

sebagai satu-satunya account.

Gunakan model:

User
 → PlatformConnection[]
 → Destination[]

Jika existing database sudah mendukung ini, REUSE.

==================================================
LANGKAH 5 — FACEBOOK PAGE DISCOVERY
==================================================

Setelah Facebook account berhasil terhubung:

1. Ambil destination/page yang memang dapat diakses oleh connection tersebut melalui official API.
2. Simpan metadata yang diperlukan.
3. Jangan menyimpan credential secara plaintext.
4. Jangan membuat Page secara manual jika API dapat melakukan discovery.
5. Jangan menampilkan Page yang tidak dapat digunakan.
6. Simpan provider/platform identifier yang diperlukan.
7. Pastikan destination dimiliki oleh PlatformConnection yang benar.
8. Jangan mencampurkan Page milik account lain.

Minimal konsep Destination:

- id
- platform_id
- platform_connection_id
- external_id
- name
- type
- status
- metadata
- created_at
- updated_at

Sesuaikan dengan schema existing.

==================================================
LANGKAH 6 — DESTINATION WORKSPACE
==================================================

Ini SANGAT PENTING.

Setiap Facebook Page memiliki workspace sendiri.

Contoh:

Facebook Account
 ├── Page A
 │    └── Workspace A
 │         ├── Dashboard
 │         ├── Downloader
 │         ├── Storage
 │         ├── Publish
 │         ├── Queue
 │         ├── Schedule
 │         └── History
 │
 └── Page B
      └── Workspace B
           ├── Dashboard
           ├── Downloader
           ├── Storage
           ├── Publish
           ├── Queue
           ├── Schedule
           └── History

Semua query dan mutation harus scoped berdasarkan destination_id.

Contoh:

GET /api/destinations/:destinationId/media

GET /api/destinations/:destinationId/queue

GET /api/destinations/:destinationId/schedule

GET /api/destinations/:destinationId/history

POST /api/destinations/:destinationId/publish

Gunakan route existing jika sudah ada.

Jangan membuat duplicate API jika endpoint generic existing sudah dapat digunakan.

==================================================
DESTINATION ISOLATION
==================================================

WAJIB dites:

Page A tidak boleh melihat:

- media Page B
- queue Page B
- schedule Page B
- history Page B
- publishing job Page B

Page A juga tidak boleh membuat publishing job untuk Page B hanya dengan mengganti destination_id di request.

Backend harus melakukan ownership/authorization check.

Jangan hanya mengandalkan filter frontend.

Frontend filter saja TIDAK CUKUP.

==================================================
LANGKAH 7 — FACEBOOK CAPABILITY
==================================================

Facebook provider harus melaporkan capability yang benar-benar tersedia.

Contoh:

facebook.capabilities()

→ video
→ reels
→ photo
→ text_post
→ scheduling

Tetapi hanya masukkan capability yang benar-benar diverifikasi dan diimplementasikan.

Jangan hardcode capability yang belum tersedia.

Jika Phase 5 hanya mengimplementasikan video:

Facebook:

video = AVAILABLE
reels = NOT_IMPLEMENTED / NEEDS VERIFICATION
photo = NOT_IMPLEMENTED
text_post = NOT_IMPLEMENTED
scheduling = CORE SCHEDULER READY / PROVIDER SUPPORT NEEDS VERIFICATION

Gunakan status yang jelas.

==================================================
LANGKAH 8 — MEDIA VALIDATION
==================================================

Sebelum publishing:

PublishingJob
 → provider = facebook
 → destination = Page A
 → media = Media X

Facebook provider melakukan validation sesuai requirement resmi.

Periksa hal yang relevan seperti:

- MIME type
- file exists
- storage availability
- file size
- duration
- dimensions
- media type
- provider capability

Jangan melakukan validasi berdasarkan angka yang belum diverifikasi.

Jika requirement tidak diketahui:

NEEDS VERIFICATION

Jangan mengarang batasan.

==================================================
LANGKAH 9 — PUBLISHING JOB
==================================================

Gunakan PublishingJob yang sudah dibuat pada phase sebelumnya.

Jangan membuat FacebookJob baru jika PublishingJob generik sudah tersedia.

Contoh:

PublishingJob:

id
destination_id
media_id
provider
sequence_number
scheduled_at
schedule_source
status
attempt_count
created_at
updated_at

Sesuaikan schema existing.

Facebook provider menerima job generik tersebut.

Flow:

PublishingJob
      ↓
Queue
      ↓
Worker
      ↓
Provider Registry
      ↓
Facebook Provider
      ↓
Meta API
      ↓
Provider Response
      ↓
PublishingJob status
      ↓
History

==================================================
LANGKAH 10 — PUBLISH NOW
==================================================

Implementasikan publish now melalui pipeline yang sama.

Flow:

User memilih:

Page A
Video A
Publish Now

↓

Create PublishingJob

↓

Queue

↓

Worker

↓

Facebook Provider

↓

Meta API

↓

status

Jangan langsung memanggil Meta API dari frontend.

Frontend → API → PublishingJob → Queue → Worker → Provider.

==================================================
LANGKAH 11 — SCHEDULED PUBLISHING
==================================================

Gunakan scheduler Phase 4 yang sudah ada.

Jangan membuat scheduler Facebook baru.

Flow:

Video
 ↓
Destination Page A
 ↓
Schedule
 ↓
Daily Slot System
 ↓
scheduled_at
 ↓
PublishingJob
 ↓
Queue
 ↓
Worker
 ↓
Facebook Provider
 ↓
Meta API

Jika scheduled_at belum waktunya:

job tidak boleh dipublish.

Jika waktunya sudah tiba:

scheduler/worker memproses job.

==================================================
LANGKAH 12 — SEQUENCE
==================================================

Pertahankan aturan Phase 4.

Sequence TIDAK reset setiap hari.

Contoh:

Hari 1:

08:00 Video 1
11:00 Video 2
14:00 Video 3
17:00 kosong

Hari 2:

08:00 Video 4
11:00 Video 5

Jika downloader memasukkan Video 4 setelah hari pertama selesai:

Video tersebut tetap sequence 4.

Jangan mengubah menjadi Video 1.

Jangan menggunakan kembali sequence yang sudah pernah digunakan.

==================================================
LANGKAH 13 — DOWNLOADER
==================================================

Downloader yang sudah ada harus tetap masuk ke media pipeline.

Contoh:

Facebook Downloader
 ↓
Media
 ↓
destination_id = Page A
 ↓
READY
 ↓
Auto Scheduler
 ↓
PublishingJob

Jika downloader dilakukan pada Page B:

destination_id = Page B

Jangan sampai media Page A masuk ke Page B.

Jika media dari downloader memiliki external/source identifier:

simpan metadata tersebut.

Minimal konsep:

source_type
source_id / source_url jika aman
source_metadata
created_at

Jangan menggunakan filename sebagai identifier utama.

==================================================
LANGKAH 14 — STORAGE
==================================================

Storage harus tetap generic.

Facebook provider tidak boleh memiliki storage system sendiri.

Media:

storage
 ↓
Media
 ↓
Facebook provider membaca media melalui abstraction existing.

Jika provider membutuhkan file/stream:

gunakan storage abstraction.

Jangan membuat path filesystem hardcoded di Facebook provider.

==================================================
LANGKAH 15 — PUBLISHING STATUS
==================================================

Gunakan status generik yang sudah ada.

Contoh:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Mapping provider harus jelas.

Contoh:

Meta success
→ published

Temporary provider error
→ retrying / failed sesuai retry policy

Permanent permission error
→ failed

Jangan menganggap request HTTP 200 saja sebagai published jika API memiliki asynchronous processing/status.

Jika Meta API menghasilkan media/post identifier:

simpan identifier provider yang diperlukan.

Jangan menyimpan token/secret sebagai metadata.

==================================================
LANGKAH 16 — ERROR HANDLING
==================================================

Pisahkan:

TEMPORARY

- timeout
- network error
- temporary Meta API failure
- rate limit
- transient server error

→ retry sesuai policy.

PERMANENT

- invalid token
- permission denied
- invalid destination
- unsupported media
- invalid request
- account disconnected

→ failed.

Error harus memiliki:

- provider
- provider error code jika tersedia
- safe error message
- attempt
- timestamp
- retryable
- raw provider metadata hanya jika aman

Jangan memasukkan access token atau secret ke log.

==================================================
LANGKAH 17 — RETRY & IDEMPOTENCY
==================================================

Gunakan retry/idempotency mechanism Phase 4.

Jangan membuat duplicate publish ketika worker restart.

Contoh:

Worker mulai publish
 ↓
process crash
 ↓
worker restart
 ↓
job diproses ulang

Sistem harus memiliki guard agar tidak sembarangan membuat duplicate publishing.

Gunakan identifier/idempotency strategy yang sudah tersedia.

Jika provider mendukung idempotency mechanism, gunakan sesuai dokumentasi.

Jika tidak mendukung:

gunakan local publishing state dan provider response tracking sesuai architecture.

Jangan mengklaim exactly-once delivery jika sebenarnya hanya at-least-once.

==================================================
LANGKAH 18 — UI FACEBOOK ACCOUNT
==================================================

Jika UI Accounts sudah ada, gunakan existing page.

Tambahkan hanya yang diperlukan.

Contoh:

Accounts

Facebook
  Connected

  Account information

  Pages:
    Page A     Connected
    Page B     Connected
    Page C     Connected

Actions:

Connect
Reconnect
Refresh Pages
Disconnect

Jangan membuat fake connected status.

Jika OAuth belum benar-benar dikonfigurasi:

tampilkan status yang jujur.

==================================================
LANGKAH 19 — PAGE WORKSPACE UI
==================================================

Destination switcher harus jelas.

Contoh:

[ Facebook Page A ▼ ]

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Jika user memilih:

[ Facebook Page B ▼ ]

seluruh data harus berpindah ke:

destination_id = Page B

Bukan hanya mengganti nama Page di UI.

Backend harus ikut berubah context.

==================================================
LANGKAH 20 — PUBLISH UI
==================================================

Publish page harus menggunakan destination context aktif.

Contoh:

Destination:
Facebook Page A

Media:
Video A

Caption:
[........................]

Schedule:

( ) Publish Now
( ) Schedule

Jika Schedule:

Date
Time

[Publish]

Sebelum membuat job:

backend melakukan:

- authorization
- destination ownership
- media ownership
- capability validation
- scheduling validation
- duplicate/idempotency check

Jangan percaya destination_id yang dikirim frontend.

==================================================
LANGKAH 21 — HISTORY
==================================================

History harus scoped destination.

Page A:

Video 1 → Published
Video 2 → Failed

Page B:

Video 3 → Published

Page A tidak boleh melihat history Page B melalui endpoint normal.

History harus dapat menunjukkan:

- media
- sequence
- destination
- status
- scheduled_at
- published_at
- provider
- error jika failed
- attempt count

Jangan menampilkan access token.

==================================================
LANGKAH 22 — AUDIT LOG
==================================================

Gunakan audit log existing.

Catat event penting:

- Facebook connection
- reconnect
- disconnect
- destination discovery
- destination refresh
- publish request
- schedule request
- cancel
- retry
- provider failure

Jangan memasukkan secret.

==================================================
LANGKAH 23 — TEST WAJIB
==================================================

Tambahkan/update tests sesuai architecture existing.

Minimal test:

1. Facebook provider registration
2. Facebook capability detection
3. account connection
4. destination discovery
5. destination ownership
6. destination isolation
7. media validation
8. publishing job creation
9. publish now
10. scheduled publish
11. queue processing
12. retryable error
13. permanent error
14. failed publish
15. successful publish mapping
16. duplicate/idempotency protection
17. Page A tidak dapat mengakses Page B
18. Page B tidak dapat mengakses Page A
19. sequence tidak reset
20. scheduler tetap destination-scoped

Untuk integration/live Facebook test:

JANGAN membuat fake credential.

Jika environment tidak memiliki:

META_APP_ID
META_APP_SECRET
redirect URI yang valid
Facebook connection

maka:

LIVE FACEBOOK VERIFICATION: NOT RUN

dan jelaskan alasannya.

Jangan mengubah menjadi PASS.

Unit/integration tests yang tidak membutuhkan credential tetap harus dijalankan.

==================================================
LANGKAH 24 — ENVIRONMENT
==================================================

Periksa .env.example dan konfigurasi existing.

Jika variabel berikut memang dibutuhkan oleh implementation:

META_APP_ID
META_APP_SECRET
META_REDIRECT_URI

dokumentasikan nama variabel yang benar sesuai code.

Jangan memasukkan nilai secret nyata.

Contoh:

META_APP_ID=your_meta_app_id
META_APP_SECRET=your_meta_app_secret
META_REDIRECT_URI=https://example.com/api/connections/facebook/callback

Sesuaikan dengan architecture actual.

.env harus tetap ignored oleh Git.

Pastikan:

git status

tidak menunjukkan .env sebagai file yang akan di-commit.

Jangan pernah mencetak nilai secret ke terminal report.

==================================================
LANGKAH 25 — SECURITY REVIEW
==================================================

Periksa:

- OAuth state validation
- CSRF protection
- callback validation
- token encryption
- authorization
- destination ownership
- media ownership
- SSRF
- upload validation
- MIME validation
- file size validation
- secret logging
- error logging
- rate limiting
- session security

Jika ada security gap yang ditemukan:

jangan sembunyikan.

Laporkan:

SECURITY GAP
SEVERITY
CURRENT BEHAVIOR
RECOMMENDED FIX

Perbaiki jika masih dalam scope Phase 5 dan aman.

Jika tidak aman untuk diperbaiki sekarang:

dokumentasikan sebagai follow-up.

==================================================
LANGKAH 26 — DOCUMENTATION
==================================================

Update documentation existing, jangan membuat duplicate.

Minimal perbarui jika relevan:

docs/ARCHITECTURE.md
docs/PLATFORM_MODULES.md
docs/DATABASE.md
docs/ROADMAP.md
docs/UI_DESIGN.md
docs/research/facebook-api.md

Dokumentasikan:

- Facebook provider
- account connection
- Page discovery
- destination workspace
- publishing flow
- queue flow
- status mapping
- retry
- error mapping
- security
- environment variables
- known limitations
- verification status

Jangan menulis "Facebook publishing fully verified" jika live credential belum tersedia.

==================================================
LANGKAH 27 — JANGAN MENGGANGGU PHASE 4
==================================================

Setelah Facebook provider masuk:

Pastikan:

Daily Slot:
PASS

Sequence:
PASS

Queue:
PASS

Retry:
PASS

Idempotency:
PASS

Destination Isolation:
PASS

Downloader:
PASS

Storage:
PASS

History:
PASS

Jangan menghapus atau mengganti logic Phase 4 yang sudah bekerja hanya agar Facebook provider lebih mudah dibuat.

Jika ditemukan bug existing:

perbaiki hanya jika memang diperlukan untuk Phase 5.

Dokumentasikan perubahan.

==================================================
LANGKAH 28 — TYPECHECK / LINT / TEST / BUILD
==================================================

Setelah implementation:

1. typecheck
2. lint
3. test
4. build

Semua harus dijalankan menggunakan command yang benar dari repository.

Jangan menebak command jika package.json/scripts tersedia.

Jika ada test existing yang gagal:

bedakan:

- regression akibat perubahan Phase 5
- failure existing
- environment failure
- credential-dependent test

Jangan menonaktifkan test hanya agar PASS.

Jangan menghapus test.

==================================================
LANGKAH 29 — GIT REVIEW
==================================================

Sebelum commit:

git status

Periksa diff.

Pastikan tidak ada:

- .env
- secret
- token
- credential
- password
- private key
- temporary file
- debug dump
- unrelated modification

Jangan commit secret.

Jangan membuat commit kosong.

Jangan force push.

==================================================
LANGKAH 30 — COMMIT & PUSH
==================================================

Jika semua pemeriksaan aman:

commit dengan message yang jelas, misalnya:

feat: add facebook provider publishing

atau gunakan commit message yang lebih tepat berdasarkan perubahan aktual.

Push ke branch yang sedang digunakan.

Setelah push:

verifikasi remote.

Jika push gagal:

JANGAN mengatakan SUCCESS.

Laporkan error sebenarnya.

==================================================
FINAL REPORT
==================================================

Setelah selesai tampilkan laporan ringkas tetapi lengkap:

PHASE 5 STATUS

Facebook Provider:
PASS / PARTIAL / BLOCKED

Facebook Authentication:
PASS / NOT CONFIGURED / NEEDS VERIFICATION

Page Discovery:
PASS / BLOCKED

Destination Workspace:
PASS

Destination Isolation:
PASS

Media Pipeline:
PASS

Publishing Job:
PASS

Queue:
PASS

Scheduler:
PASS

Retry:
PASS

Idempotency:
PASS

History:
PASS

Security:
PASS / NEEDS REVIEW

Tests:
PASS (jumlah test)

Typecheck:
PASS

Lint:
PASS

Build:
PASS

Facebook Live Verification:
PASS / NOT RUN

Jika NOT RUN, jelaskan alasan singkat tanpa membuat fake success.

==================================================
GIT FINAL STATUS
==================================================

Tampilkan:

GIT STATUS: CLEAN
COMMIT: <actual commit hash>
BRANCH: <actual branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

Jika ada error Git, tampilkan status sebenarnya.

==================================================
NEXT RECOMMENDED PHASE
==================================================

Setelah Phase 5 selesai, jangan langsung coding Phase 6.

Tentukan berdasarkan kondisi repository apakah berikutnya:

PHASE 6 — Queue & Worker Hardening

atau phase lain yang lebih tepat.

Jelaskan alasan singkat.

==================================================
STOP CONDITION
==================================================

STOP setelah Phase 5 selesai.

Jangan lanjut Phase 6.

Jangan membuat provider YouTube.
Jangan membuat provider Instagram.
Jangan membuat provider TikTok.
Jangan membuat analytics.
Jangan membuat automation baru di luar scope.
Jangan melakukan fake Facebook publishing.
Jangan membuat fake PUBLISHED.

Kerjakan hanya Facebook Provider & Publishing sesuai architecture existing.

Jika ada requirement yang belum dapat diverifikasi, tandai dengan jelas:

NEEDS VERIFICATION

Jika credential Meta belum tersedia di environment:

jangan membuat credential palsu.

Implementasikan code yang aman untuk environment tersebut dan lakukan live verification hanya jika credential resmi memang tersedia.

STOP.

````
# Phase 4 — Daily Slot & Auto-Publishing Scheduler.
```

LANJUTKAN PROJECT CONTENT PILOT.

PHASE 3 SUDAH SELESAI DAN SUDAH DI-PUSH.

Jangan mengulang Phase 3.
Jangan mengubah architecture yang sudah PASS kecuali memang diperlukan sebagai dependency Phase 4.

STATUS TERAKHIR:
- Build: PASS
- Git: CLEAN
- Commit: 107ba52
- Push: SUCCESS
- Remote verified: YES
- Migration media duplicate index sudah diterapkan
- Facebook Live publishing belum diverifikasi dan JANGAN disentuh pada phase ini

==================================================
PHASE 4 — DAILY SLOT & AUTO-PUBLISHING SCHEDULER
==================================================

Fokus phase ini hanya pada:

1. Daily Slot Configuration
2. Destination/Workspace scoped scheduling
3. Automatic slot allocation
4. Global sequence
5. Next-day rollover
6. Manual schedule override
7. Queue integration foundation
8. Retry/idempotency foundation
9. Schedule persistence
10. Scheduler worker
11. Scheduler history/status
12. Tests
13. Documentation

Jangan implement Facebook publishing production pada phase ini.

Jangan membuat fake Facebook publish.

==================================================
1. KONSEP UTAMA
==================================================

Setiap Facebook Page/Destination mempunyai workspace dan konfigurasi scheduler sendiri.

Contoh:

Facebook Account
├── Page A
│   ├── Downloader
│   ├── Storage
│   ├── Publish
│   ├── Queue
│   ├── Schedule
│   └── History
│
└── Page B
    ├── Downloader
    ├── Storage
    ├── Publish
    ├── Queue
    ├── Schedule
    └── History

Scheduler Page A tidak boleh mengambil konfigurasi atau slot Page B.

Scheduler Page B tidak boleh mengambil konfigurasi atau slot Page A.

Semua scheduling configuration harus mempunyai destination_id.

==================================================
2. DAILY SLOT CONFIGURATION
==================================================

Setiap Destination memiliki pengaturan:

- enabled
- timezone
- max_videos_per_day
- daily_slots

Contoh:

Destination:
Facebook Page A

Auto Publishing:
ON

Timezone:
Asia/Jakarta

Maximum videos per day:
4

Daily slots:

08:00
11:00
14:00
17:00

Konfigurasi tersebut hanya berlaku untuk Page A.

Page B dapat memiliki:

Maximum:
2

Slots:
09:00
19:00

Jangan membuat satu konfigurasi global untuk semua Page.

==================================================
3. SLOT HARUS TERSIMPAN
==================================================

Daily slot bukan hanya array frontend.

Simpan konfigurasi secara persistent di database.

Contoh konsep:

SchedulingSettings
- id
- destination_id
- enabled
- timezone
- max_videos_per_day
- created_at
- updated_at

DailySlot
- id
- scheduling_settings_id
- slot_time
- enabled
- sequence/order

Sesuaikan dengan architecture/database existing.

Jangan membuat tabel baru jika struktur existing sudah dapat menangani konsep tersebut dengan benar.

==================================================
4. TIMEZONE
==================================================

Timezone wajib menjadi bagian dari scheduler configuration.

Contoh:

Asia/Jakarta

Semua perhitungan:

- hari
- tanggal
- slot
- next available time
- rollover

harus menggunakan timezone Destination.

Jangan menggunakan timezone VPS/server secara langsung sebagai timezone bisnis.

Contoh:

Server UTC

Destination:
Asia/Jakarta

Scheduler tetap menghitung:

08:00 Asia/Jakarta

bukan:

08:00 UTC.

Gunakan library timezone yang sudah sesuai dengan stack project.

==================================================
5. MAX VIDEOS PER DAY
==================================================

Contoh:

max_videos_per_day = 4

dan slots:

08:00
11:00
14:00
17:00

Maka maksimum normal per hari adalah 4.

Namun jangan hanya mengandalkan max_videos_per_day.

Scheduler harus memastikan slot aktual juga tidak bentrok.

Jika konfigurasi:

max_videos_per_day = 4

tetapi hanya ada 3 slot aktif:

08:00
12:00
18:00

maka sistem tidak boleh membuat slot ke-4 yang tidak ada.

Slot aktif adalah sumber waktu publikasi.

Jika max_videos_per_day lebih besar daripada jumlah slot aktif, gunakan jumlah slot yang benar-benar tersedia.

Jika max_videos_per_day lebih kecil daripada jumlah slot aktif, hanya gunakan sejumlah slot sesuai limit.

Contoh:

max = 2

slots:
08:00
11:00
14:00
17:00

maka hanya:

08:00
11:00

yang digunakan untuk auto allocation.

==================================================
6. CONTOH UTAMA
==================================================

Configuration:

Maximum:
4 video/hari

Slots:

08:00
11:00
14:00
17:00

Jika downloader memasukkan:

Video 1
Video 2
Video 3
Video 4
Video 5

maka:

HARI 1

08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → Video 4

HARI 2

08:00 → Video 5

Video 5 TIDAK boleh kembali menjadi Video 1.

==================================================
7. JIKA HARI PERTAMA HANYA ADA 3 VIDEO
==================================================

Contoh:

Hari 1 hanya memiliki:

Video 1
Video 2
Video 3

maka:

08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Kemudian hari berikutnya user memasukkan:

Video 4

maka Video 4 menggunakan slot berikutnya berdasarkan aturan scheduler.

Jika hari pertama sudah selesai, Video 4:

Hari 2
08:00 → Video 4

Jangan mengisi kembali slot Hari 1 yang sudah lewat.

==================================================
8. SEQUENCE GLOBAL
==================================================

Sequence tidak boleh reset setiap hari.

Contoh:

Hari 1:
Video 1
Video 2
Video 3

Hari 2:
Video 4
Video 5
Video 6

Hari 3:
Video 7
Video 8

Jangan:

Hari 1:
1,2,3

Hari 2:
1,2,3

Sequence harus terus bertambah.

Sequence harus persistent di database.

Jangan menghitung sequence hanya dari frontend.

Jangan menggunakan filename sebagai sequence.

==================================================
9. SEQUENCE VS MEDIA ID VS JOB ID
==================================================

Bedakan:

media_id
sequence_number
publishing_job_id

Contoh:

media_id:
uuid-abc

sequence_number:
17

publishing_job_id:
uuid-job-xyz

Jangan menggunakan salah satunya sebagai pengganti yang lain.

==================================================
10. AUTO ALLOCATION
==================================================

Ketika Media berstatus READY dan auto publishing aktif:

Media
→ destination
→ scheduling settings
→ cari slot tersedia
→ pilih slot paling awal yang valid
→ buat PublishingJob
→ scheduled_at disimpan
→ status Scheduled

Contoh:

Sekarang:
10:00

Slot hari ini:
08:00
11:00
14:00
17:00

Slot 08:00 sudah lewat.

Maka media baru:

11:00

Jika 11:00 sudah terisi:

14:00

Jika semua slot hari ini sudah penuh:

Hari berikutnya
08:00

Jangan menjadwalkan pada waktu yang sudah lewat.

==================================================
11. SCHEDULED_AT
==================================================

PublishingJob harus menyimpan scheduled_at aktual.

Contoh:

scheduled_at:
2026-08-27T08:00:00+07:00

Jangan hanya menyimpan:

day = 2
slot = 1

Scheduler membutuhkan waktu aktual untuk worker.

Konsep:

PublishingJob
- id
- destination_id
- media_id
- sequence_number
- scheduled_at
- schedule_source
- status
- created_at
- updated_at

==================================================
12. SCHEDULE SOURCE
==================================================

Bedakan:

AUTO
MANUAL

AUTO:

scheduler menentukan waktu berdasarkan daily slot.

MANUAL:

user menentukan waktu sendiri.

Jika manual override diberikan:

schedule_source = MANUAL

dan scheduler tidak boleh memindahkan job tersebut ke slot otomatis kecuali user memang meminta reschedule.

==================================================
13. MANUAL SCHEDULE OVERRIDE
==================================================

User dapat memilih:

Schedule manually

Contoh:

Video 7

Manual:
2026-08-29 20:30

Maka:

schedule_source = MANUAL
scheduled_at = 2026-08-29 20:30

Auto scheduler tidak boleh mengganti waktu tersebut.

Jika waktu manual bentrok, tampilkan error/warning yang jelas.

Jangan diam-diam memindahkan waktu user.

==================================================
14. RESCHEDULING
==================================================

Perubahan konfigurasi scheduler tidak boleh sembarangan memindahkan job yang sudah final.

Minimal aturan:

PUBLISHED:
tidak boleh berubah.

PROCESSING:
tidak boleh dipindahkan.

PUBLISHING:
tidak boleh dipindahkan.

QUEUED:
hanya dipindahkan jika aturan reschedule mengizinkan.

SCHEDULED:
dapat dihitung ulang jika user secara eksplisit melakukan reschedule atau konfigurasi memang memiliki aturan rescheduling.

DRAFT:
boleh dihitung ulang.

Jangan membuat perubahan konfigurasi global otomatis mengacak semua schedule yang sudah dibuat.

==================================================
15. CONFIGURATION CHANGE
==================================================

Contoh awal:

08:00
11:00
14:00
17:00

Kemudian user mengubah menjadi:

09:00
13:00
18:00

Jangan langsung memindahkan semua job yang sudah:

published
queued
processing
publishing

Dokumentasikan aturan rescheduling.

Jika job belum final dan memang diperbolehkan untuk reschedule, gunakan aturan yang konsisten.

==================================================
16. DESTINATION ISOLATION
==================================================

WAJIB.

Page A:

max = 4
slots = 08:00,11:00,14:00,17:00

Page B:

max = 2
slots = 09:00,19:00

Jika Page A mempunyai:

Video 1
Video 2
Video 3

Scheduler Page B tidak boleh menghitung ketiga video tersebut.

Semua query harus scoped:

destination_id

Bukan:

SELECT semua scheduled jobs

lalu filter di frontend.

==================================================
17. CROSS DESTINATION SECURITY
==================================================

User tidak boleh mengubah:

destination_id

pada request lalu mengakses scheduler destination lain.

Backend harus memeriksa:

authenticated user
→ destination ownership/access
→ scheduler configuration
→ media ownership
→ publishing job ownership

Jangan percaya destination_id dari client tanpa authorization check.

==================================================
18. QUEUE INTEGRATION
==================================================

Phase 4 harus menyiapkan integrasi:

Scheduler
→ PublishingJob
→ Queue
→ Worker

Tetapi jangan melakukan Facebook publishing production.

Ketika scheduled_at sudah tiba:

PublishingJob dapat berubah:

SCHEDULED
→ QUEUED

Kemudian queue/worker mengambil job.

Jika provider Facebook belum dikonfigurasi untuk live publish:

jangan membuat fake PUBLISHED.

Gunakan status yang benar seperti:

QUEUED
FAILED
BLOCKED
WAITING_FOR_PROVIDER

sesuai architecture existing.

==================================================
19. SCHEDULER WORKER
==================================================

Scheduler harus aman jika dijalankan berulang.

Contoh worker dijalankan setiap menit.

Job yang sama tidak boleh dibuat berkali-kali.

Gunakan idempotency.

Jika scheduler memeriksa job yang sama 10 kali:

tetap satu PublishingJob.

Jangan menghasilkan:

Job 001
Job 002
Job 003

untuk satu media yang sama hanya karena scheduler dipanggil berulang.

==================================================
20. IDEMPOTENCY
==================================================

Gunakan unique/idempotency constraint yang sesuai.

Konsep:

destination_id
+
media_id
+
schedule intent

harus mencegah duplicate auto job.

Namun jangan membuat constraint yang menghalangi:

manual reschedule
retry
atau publishing ke destination berbeda.

Gunakan architecture yang tepat berdasarkan model existing.

==================================================
21. RETRY
==================================================

Bedakan:

temporary error
permanent error

Temporary:

- timeout
- network error
- temporary provider error
- rate limit

Permanent:

- invalid destination
- invalid credentials
- permission error
- unsupported media

Retry tidak boleh membuat PublishingJob baru untuk setiap attempt.

Tetap satu PublishingJob.

Buat PublishingAttempt terpisah jika model tersebut sudah tersedia.

Contoh:

Job 100
Attempt 1 → failed
Attempt 2 → failed
Attempt 3 → success

==================================================
22. CANCELLATION
==================================================

User dapat membatalkan scheduled job sebelum diproses.

Contoh:

SCHEDULED
→ CANCELLED

Setelah CANCELLED:

scheduler tidak boleh mengirim job tersebut ke queue.

Jangan menghapus history hanya karena job dibatalkan.

==================================================
23. EMPTY DAY
==================================================

Jika tidak ada video pada hari tertentu:

tidak perlu membuat dummy job.

Contoh:

Hari 1:
Video 1
Video 2
Video 3

Slot ke-4 kosong.

Jangan membuat:

Video NULL
Job kosong
Fake media

==================================================
24. BULK DOWNLOAD
==================================================

Jika user download:

Video 1
Video 2
Video 3
Video 4
Video 5
Video 6

dengan auto publishing aktif:

scheduler harus menentukan slot berdasarkan urutan media masuk/created time.

Contoh:

Video 1 → hari 1 08:00
Video 2 → hari 1 11:00
Video 3 → hari 1 14:00
Video 4 → hari 1 17:00
Video 5 → hari 2 08:00
Video 6 → hari 2 11:00

Jangan bergantung pada urutan tampilan frontend.

==================================================
25. DOWNLOAD BERURUTAN
==================================================

Jika downloader selesai:

Video 1
→ READY
→ schedule

kemudian:

Video 2
→ READY
→ schedule

Maka slot harus tetap konsisten.

Race condition harus diperhatikan jika beberapa downloader selesai hampir bersamaan.

Gunakan transaction/locking/unique constraint yang sesuai.

==================================================
26. RACE CONDITION
==================================================

Wajib test kondisi:

dua worker mencoba menjadwalkan dua media secara bersamaan.

Jangan sampai:

Video 1 → 08:00
Video 2 → 08:00

jika slot hanya boleh satu job.

Gunakan database transaction/locking atau mekanisme concurrency yang sesuai.

==================================================
27. SCHEDULE PAGE
==================================================

Buat Schedule page per Destination.

Contoh:

Facebook Page A
→ Schedule

Tampilkan:

Today
Tomorrow
Upcoming

Contoh:

TODAY

08:00
Video 1
Scheduled

11:00
Video 2
Scheduled

14:00
Video 3
Scheduled

17:00
Empty

TOMORROW

08:00
Video 4
Scheduled

Jangan menampilkan schedule destination lain.

==================================================
28. CALENDAR / LIST
==================================================

Jika architecture existing sudah memiliki calendar component, gunakan.

Jika belum, gunakan UI sederhana terlebih dahulu.

Minimal:

date
time
media
sequence
status
schedule source

Tidak perlu membuat calendar kompleks jika tidak dibutuhkan.

==================================================
29. SETTINGS UI
==================================================

Pada workspace Destination:

Settings
→ Auto Publishing

Contoh:

Auto Publishing
[ ON ]

Timezone
[ Asia/Jakarta ]

Maximum Videos Per Day
[ 4 ]

Daily Slots

[ 08:00 ] [ enabled ]
[ 11:00 ] [ enabled ]
[ 14:00 ] [ enabled ]
[ 17:00 ] [ enabled ]

[ Add Slot ]

[ Save Settings ]

Konfigurasi harus benar-benar tersimpan.

Jangan membuat UI dummy.

==================================================
30. SLOT VALIDATION
==================================================

Validasi:

- timezone valid
- max_videos_per_day >= 1 jika enabled
- slot time valid
- slot tidak duplicate
- slot berada dalam format yang benar
- jumlah slot konsisten
- tidak ada slot invalid

Jika:

08:00
08:00

tolak duplicate.

Jika:

25:99

tolak.

==================================================
31. SLOT ORDER
==================================================

Simpan slot dalam urutan waktu.

Contoh user memasukkan:

17:00
08:00
14:00
11:00

scheduler harus mengurutkan:

08:00
11:00
14:00
17:00

Jangan mengandalkan urutan input frontend.

==================================================
32. DAILY LIMIT VS SLOTS
==================================================

Contoh:

max_videos_per_day = 3

slots:

08:00
11:00
14:00
17:00

Gunakan:

08:00
11:00
14:00

Slot 17:00 tidak digunakan untuk auto allocation karena limit = 3.

Jika max berubah menjadi 4:

slot 17:00 mulai tersedia untuk job baru yang belum final sesuai aturan rescheduling.

Jangan memindahkan job published.

==================================================
33. SEQUENCE ALLOCATION
==================================================

Sequence harus atomik.

Jika dua media masuk bersamaan:

Media A
Media B

jangan sampai keduanya mendapat:

sequence = 10

Gunakan database mechanism yang aman.

Sequence harus unique sesuai scope yang sudah dipilih architecture.

Jika sequence memang global per destination:

destination A:
1,2,3...

destination B:
1,2,3...

Jangan membuat sequence global seluruh sistem jika kebutuhan bisnis sebenarnya per Destination.

Gunakan keputusan architecture yang konsisten:

sequence_number adalah urutan content pada Destination.

==================================================
34. HISTORY
==================================================

Schedule history minimal dapat menunjukkan:

- media
- sequence
- scheduled_at
- created_at
- source AUTO/MANUAL
- status
- destination

Jika reschedule terjadi, simpan audit/history yang sesuai.

Jangan menghapus history lama secara diam-diam.

==================================================
35. AUDIT LOG
==================================================

Jika AuditLog sudah tersedia, gunakan untuk:

- scheduler settings changed
- slot added
- slot removed
- auto publishing enabled/disabled
- manual schedule
- reschedule
- cancellation

Contoh:

User mengubah:

max videos:
4 → 5

Audit:

SCHEDULING_SETTINGS_UPDATED

Jangan log token/secret.

==================================================
36. DATABASE
==================================================

Audit database existing sebelum migration.

Jangan membuat duplicate table/model.

Jika model existing sudah dapat digunakan:

update model tersebut.

Jika migration diperlukan:

- buat migration
- jangan hapus data
- jangan destructive migration tanpa kebutuhan
- foreign key benar
- index benar
- unique constraint benar

Pertimbangkan index:

destination_id
scheduled_at
status
sequence_number

Gunakan nama migration mengikuti convention repository.

==================================================
37. API
==================================================

Minimal capability:

GET scheduler settings
UPDATE scheduler settings
LIST daily slots
CREATE/update/delete slot
LIST scheduled jobs
CREATE manual schedule
CANCEL scheduled job
RESCHEDULE jika diperbolehkan

Gunakan route convention existing.

Semua endpoint:

authenticated
destination-scoped
authorized

==================================================
38. AUTO SCHEDULING TRIGGER
==================================================

Auto scheduling dapat dipicu ketika:

Media → READY

Jika:

auto publishing = ON

maka scheduler mencoba mencari slot.

Jika:

auto publishing = OFF

media tetap READY dan tidak otomatis dijadwalkan.

User tetap dapat melakukan manual schedule jika fitur tersebut tersedia.

==================================================
39. DISABLE AUTO PUBLISHING
==================================================

Jika user mematikan:

Auto Publishing OFF

Jangan menghapus media.

Jangan menghapus history.

Jangan membatalkan job yang sudah published.

Untuk scheduled job yang sudah ada, gunakan aturan yang jelas dan aman.

Default:

existing scheduled jobs tetap scheduled kecuali user memilih "cancel upcoming schedules".

Jangan melakukan destructive action diam-diam.

==================================================
40. RE-ENABLE AUTO PUBLISHING
==================================================

Jika sebelumnya OFF kemudian ON:

media READY yang belum memiliki PublishingJob dapat dipertimbangkan untuk auto scheduling.

Media yang sudah memiliki job tidak boleh mendapatkan duplicate job.

==================================================
41. SCHEDULED MEDIA LOCK
==================================================

Jika media sudah memiliki scheduled PublishingJob:

scheduler tidak boleh membuat job kedua secara otomatis.

Jika user ingin jadwal baru:

gunakan reschedule/edit existing job.

==================================================
42. UI DESTINATION CONTEXT
==================================================

Setiap halaman scheduler harus menampilkan:

Facebook Page:
Page A

sehingga user tahu sedang mengatur Page mana.

Jika user berpindah:

Page A → Page B

semua:

settings
slots
schedule
queue

harus berubah mengikuti Page B.

==================================================
43. SECURITY
==================================================

Periksa:

- IDOR
- cross-destination access
- unauthorized schedule modification
- unauthorized cancellation
- user isolation
- race conditions
- duplicate jobs
- timezone manipulation
- invalid scheduled time
- scheduling in the past
- secret leakage

Jangan mempercayai:

destination_id
media_id
job_id

dari client tanpa authorization.

==================================================
44. FACEBOOK PUBLISHING
==================================================

JANGAN melakukan Facebook publishing production pada Phase 4.

Scheduler hanya menghasilkan:

PublishingJob

dan mengatur:

scheduled_at
status
queue state

Jika provider belum tersedia:

jangan mengubah status menjadi PUBLISHED.

Jangan membuat fake Graph API response.

==================================================
45. TESTING
==================================================

Minimal test:

1. Create scheduler settings.
2. Update scheduler settings.
3. Add daily slot.
4. Delete daily slot.
5. Duplicate slot ditolak.
6. Invalid time ditolak.
7. Timezone disimpan.
8. Page A mempunyai scheduler sendiri.
9. Page B mempunyai scheduler sendiri.
10. Page A tidak dapat membaca scheduler Page B.
11. Auto scheduling OFF tidak membuat job.
12. Auto scheduling ON membuat job ketika media READY.
13. Slot pertama yang tersedia dipilih.
14. Slot yang sudah lewat dilewati.
15. Slot penuh berpindah ke hari berikutnya.
16. Sequence tidak reset.
17. Sequence unique.
18. Hari pertama hanya 3 video tetap menyisakan slot kosong.
19. Video berikutnya masuk hari berikutnya.
20. max_videos_per_day dihormati.
21. Manual schedule override bekerja.
22. Manual schedule tidak diganti auto scheduler.
23. Scheduled job dapat dibatalkan.
24. Cancelled job tidak masuk queue.
25. Scheduler idempotent.
26. Dua worker tidak mendapatkan slot yang sama.
27. Duplicate PublishingJob dicegah.
28. Retry tidak membuat job baru.
29. Existing regression test tetap PASS.
30. Typecheck PASS.
31. Lint PASS.
32. Test PASS.
33. Build PASS.

==================================================
46. DOCUMENTATION
==================================================

Update dokumentasi yang sudah ada.

Minimal:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/ROADMAP.md
docs/UI_DESIGN.md

Jika dokumentasi scheduler sudah ada, update file tersebut.

Dokumentasikan:

- daily slot
- timezone
- max videos per day
- sequence
- rollover
- auto scheduling
- manual override
- rescheduling
- cancellation
- idempotency
- concurrency
- destination isolation

Jangan membuat duplicate documentation.

==================================================
47. GIT
==================================================

Setelah selesai:

git status
inspect diff
secret scan
typecheck
lint
test
build

Pastikan tidak ada:

- API key
- access token
- refresh token
- META_APP_SECRET
- password
- credential

di commit.

Commit:

feat: implement daily slot auto publishing scheduler

Push ke branch yang sedang digunakan.

Jangan force push.

Setelah push:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

==================================================
48. FINAL REPORT
==================================================

Tampilkan:

PHASE 4 STATUS

SCHEDULER SETTINGS:
PASS / FAIL

DAILY SLOT:
PASS / FAIL

TIMEZONE:
PASS / FAIL

MAX VIDEOS PER DAY:
PASS / FAIL

AUTO ALLOCATION:
PASS / FAIL

SEQUENCE:
PASS / FAIL

NEXT-DAY ROLLOVER:
PASS / FAIL

MANUAL OVERRIDE:
PASS / FAIL

RESCHEDULING:
PASS / FAIL

CANCELLATION:
PASS / FAIL

IDEMPOTENCY:
PASS / FAIL

CONCURRENCY:
PASS / FAIL

DESTINATION ISOLATION:
PASS / FAIL

SECURITY:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

PUSH:
SUCCESS / FAILED / NOT NEEDED

REMOTE VERIFIED:
YES / NO

NEXT RECOMMENDED PHASE:
PHASE 5 — FACEBOOK PROVIDER & PUBLISHING

==================================================
STOP CONDITION
==================================================

Setelah Phase 4 selesai:

STOP.

Jangan implement Phase 5.

Jangan melakukan Facebook publishing production.

Jangan menambahkan YouTube.
Jangan menambahkan Instagram.
Jangan menambahkan TikTok.

Jangan membuat fitur di luar scope.

Jika ada masalah architecture, laporkan masalah sebenarnya.

Jangan membuat fake PASS.

Kerjakan berdasarkan repository yang benar-benar ada sekarang.
````
# Phase 3 — Media, Downloader & Storage Pipelin
```

LANJUTKAN PROJECT CONTENT PILOT.

Phase 0 dan Phase 2 sebelumnya sudah selesai dan terverifikasi.
Jangan mengulang pekerjaan yang sudah PASS.

SEKARANG IMPLEMENTASIKAN HANYA:

PHASE 3 — MEDIA, DOWNLOADER & STORAGE PIPELINE

Jangan lanjut ke Phase 4/5.
Jangan implement publishing Facebook terlebih dahulu.
Jangan membuat fake Facebook publish.
Fokus pada media, downloader, storage, destination isolation, dan pipeline READY.

==================================================
1. ATURAN UTAMA
==================================================

Sebelum coding:

1. Audit kembali implementasi Phase 1 dan Phase 2 yang sudah ada.
2. Jangan mengganti architecture yang sudah berjalan tanpa alasan.
3. Jangan membuat duplicate model/service/page.
4. Gunakan abstraction yang sudah dibuat.
5. Jangan menghapus fitur yang sudah PASS.
6. Jangan membuat mock/fake success.
7. Semua data harus benar-benar tersimpan di database/storage.
8. Semua operasi media harus aman dan destination-scoped.

Jika ada bagian Phase 1/2 yang ternyata belum benar-benar terimplementasi, perbaiki hanya bagian yang memang menjadi dependency Phase 3.

STOP jika ditemukan masalah architecture besar yang menyebabkan Phase 3 tidak aman untuk dilanjutkan. Jelaskan masalahnya terlebih dahulu.

==================================================
2. DESTINATION WORKSPACE ADALAH KONTEKS UTAMA
==================================================

Project TIDAK boleh mempunyai satu halaman Downloader global yang mencampur semua Page.

Setiap Destination mempunyai workspace sendiri.

Contoh:

Facebook Account
├── Page A
│   └── Workspace Page A
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
├── Page B
│   └── Workspace Page B
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
└── Page C
    └── Workspace Page C
        ├── Dashboard
        ├── Downloader
        ├── Storage
        ├── Publish
        ├── Queue
        ├── Schedule
        └── History

Phase 3 fokus pada:

Downloader
Storage
Media Library
Media Detail
Destination isolation

Tetapi struktur workspace harus sudah benar supaya Phase berikutnya tidak perlu dibongkar lagi.

==================================================
3. DESTINATION ISOLATION
==================================================

Ini WAJIB.

Setiap media yang masuk melalui Downloader harus memiliki destination context.

Contoh:

Downloader Page A
→ download Video 1
→ media.destination_id = Page A

Downloader Page B
→ download Video 2
→ media.destination_id = Page B

Page A tidak boleh melihat Video 2 di Storage Page A.

Page B tidak boleh melihat Video 1 di Storage Page B.

Jangan mengandalkan frontend filter saja.

Isolation harus dilakukan di backend/database query.

Semua query media harus menggunakan destination scope.

Contoh konsep:

getMedia(destinationId)

bukan:

getAllMedia()

lalu frontend melakukan filter.

Backend harus memastikan user juga berhak mengakses destination tersebut.

Logical security:

User
→ PlatformConnection
→ Destination
→ Media

User tidak boleh mengakses Media milik Destination lain hanya dengan mengganti destination ID pada URL/API request.

Jika:

GET /destinations/page-A/media

maka backend harus memverifikasi:

1. destination exists
2. destination belongs to authenticated user
3. media belongs to destination

Jika tidak:

404 atau 403 sesuai pola security project.

Jangan membocorkan keberadaan destination milik user lain.

==================================================
4. MEDIA MODEL
==================================================

Gunakan Media sebagai entity generik.

Minimal data:

Media
- id
- user_id jika diperlukan oleh architecture
- destination_id
- source_type
- source_url/source_id jika relevan
- filename
- original_filename
- mime_type
- file_size
- duration
- width
- height
- storage_key
- thumbnail_key jika tersedia
- checksum/hash
- status
- metadata
- created_at
- updated_at

Jangan membuat model:

FacebookVideo
PageVideo
DownloaderVideo

sebagai entity utama.

Media harus platform-independent.

Contoh:

Media 001
destination = Page A
source_type = downloader

Media 002
destination = Page A
source_type = manual

Media 003
destination = Page B
source_type = downloader

==================================================
5. SOURCE TYPE
==================================================

Gunakan source type yang jelas.

Minimal:

manual
downloader

Jika architecture membutuhkan:

import
api
other

boleh ditambahkan.

Jangan membuat source type terlalu banyak tanpa kebutuhan.

Source metadata harus dapat menjawab:

- media berasal dari mana
- kapan masuk
- URL/source ID jika tersedia
- siapa yang memasukkan
- destination mana

==================================================
6. MEDIA STATUS
==================================================

Gunakan status yang jelas.

Minimal:

DOWNLOADING
PROCESSING
READY
FAILED
DELETED

Jika diperlukan:

QUEUED

tetapi jangan membuat status publishing di Media jika status tersebut sebenarnya milik PublishingJob.

PENTING:

Media READY berarti file sudah tersedia dan tervalidasi sehingga dapat digunakan pipeline berikutnya.

Media FAILED berarti proses media gagal.

Publishing status nanti tetap berada di PublishingJob.

Jangan mencampur:

Media status
dengan
PublishingJob status.

==================================================
7. STORAGE ABSTRACTION
==================================================

Storage harus platform-independent.

Jangan menyimpan file hanya berdasarkan Page ID secara hardcoded.

Gunakan storage abstraction.

Contoh konsep:

StorageService

- upload()
- get()
- delete()
- exists()
- generateUrl() jika diperlukan

Storage key harus aman dan tidak mudah bentrok.

Contoh konsep:

media/{userId}/{destinationId}/{mediaId}/original.ext

thumbnail:

media/{userId}/{destinationId}/{mediaId}/thumbnail.jpg

Struktur final sesuaikan dengan storage provider yang benar-benar digunakan.

Jangan menyimpan file dengan nama user sebagai identifier utama.

Media ID harus menjadi identifier utama.

==================================================
8. FILE SECURITY
==================================================

Validasi:

- MIME type
- extension
- file size
- file signature/magic bytes jika memungkinkan
- path traversal
- filename sanitization

Jangan percaya:

Content-Type dari browser
atau
extension filename saja.

Filename user hanya metadata.

Storage path harus dibuat oleh server.

Jangan membiarkan user menentukan storage_key secara bebas.

==================================================
9. MANUAL UPLOAD
==================================================

Implementasikan manual upload ke workspace Destination.

Flow:

Destination Workspace
→ Storage
→ Upload
→ pilih file
→ upload
→ processing
→ validation
→ READY
→ muncul di Media Library

Upload dari Page A:

Page A
→ Upload
→ Media.destination_id = Page A

Upload dari Page B:

Page B
→ Upload
→ Media.destination_id = Page B

Jangan membuat upload global yang tidak memiliki destination context.

UI harus menampilkan Page/Destination aktif dengan jelas.

Contoh:

Page A
Storage

[ Upload Video ]

Destination:
Facebook Page A

Video:
[..............]

[Upload]

==================================================
10. DOWNLOADER
==================================================

Downloader harus berada di workspace Destination.

Contoh:

Page A
→ Downloader
→ masukkan source URL
→ Download

hasil:

Media
destination_id = Page A
source_type = downloader

Jika Downloader Page B:

Media
destination_id = Page B

Jangan hanya menyimpan downloader result sebagai file fisik tanpa record database.

Setiap download harus menghasilkan Media record yang dapat dilacak.

Minimal:

media.id
destination_id
source_type
source_url/source_id
filename
storage_key
status
created_at

==================================================
11. DOWNLOADER IDENTITY
==================================================

Downloader harus memiliki identity/idempotency yang jelas.

Jika source platform memberikan video ID atau source ID, simpan.

Contoh:

source_type = downloader
source_id = <external video id>

Jika source ID tidak tersedia, gunakan kombinasi metadata yang aman seperti checksum/source URL sesuai kebutuhan.

Tujuan:

Sistem dapat mendeteksi duplicate download.

Jangan menggunakan filename sebagai unique identity.

==================================================
12. DUPLICATE DETECTION
==================================================

Implementasikan duplicate detection dengan hati-hati.

Minimal pertimbangkan:

- external source ID
- checksum
- source URL

Namun jangan membuat satu checksum global yang menyebabkan video yang sama tidak dapat digunakan oleh dua Destination.

Contoh:

Video X didownload ke Page A.

Kemudian Video X juga ingin digunakan di Page B.

Ini HARUS tetap dapat dilakukan.

Jadi:

Duplicate detection harus mencegah duplicate yang tidak diinginkan,
tetapi tidak merusak destination isolation atau reuse media.

Jika media benar-benar shared secara internal di masa depan, gunakan abstraction yang benar.

Untuk Phase 3, tetap prioritaskan destination-scoped media sesuai architecture yang sudah disepakati.

==================================================
13. MEDIA LIBRARY
==================================================

Setiap workspace memiliki Media Library sendiri.

Contoh:

Page A
→ Storage

Menampilkan hanya:

Media Page A

Page B
→ Storage

Menampilkan hanya:

Media Page B

UI Media Library minimal:

- thumbnail/preview
- filename
- status
- source
- size
- duration
- created time
- actions

Actions dapat meliputi:

View
Delete
Retry jika FAILED

Jangan menampilkan tombol publish sebagai fitur aktif jika Facebook publishing Phase 5 belum selesai.

Boleh tampilkan:

Publish
Coming in Phase 5

atau tombol disabled jika sesuai design.

==================================================
14. MEDIA DETAIL
==================================================

Buat Media Detail yang menunjukkan:

- preview video
- filename
- source type
- source URL/source ID jika tersedia
- destination
- status
- file size
- duration
- resolution
- created at
- updated at
- checksum jika memang perlu ditampilkan
- processing/error information

Jangan menampilkan credential atau secret.

==================================================
15. DELETE MEDIA
==================================================

Delete harus aman.

Jangan hanya menghapus database record lalu meninggalkan file.

Jangan hanya menghapus file lalu meninggalkan database record.

Flow harus mempertimbangkan:

database
+
storage

Jika soft delete digunakan oleh architecture:

status = DELETED

dan storage cleanup dapat dilakukan secara aman.

Jangan menghapus media yang sedang dipakai job aktif tanpa aturan yang jelas.

Jika belum ada PublishingJob production di Phase 3, tetap desain service agar aman ketika Phase 5 nanti sudah ada.

==================================================
16. DOWNLOADER QUEUE
==================================================

Jika downloader membutuhkan proses asynchronous:

Downloader request
→ Downloader Job
→ Worker
→ Download
→ Store
→ Validate
→ Media READY

Jangan memaksa download besar berjalan langsung dalam HTTP request jika dapat menyebabkan timeout.

Gunakan queue/worker yang sudah tersedia jika memang sudah dibuat pada Phase 1/2.

Namun jangan membuat queue architecture kedua.

Gunakan queue infrastructure existing.

==================================================
17. MEDIA PIPELINE
==================================================

Target pipeline:

Manual Upload ──────┐
                    │
                    v
                 Media
                    │
                    v
               Processing
                    │
                    v
                 Validate
                    │
                    v
                  READY
                    │
                    v
             Future Scheduler
                    │
                    v
            PublishingJob
                    │
                    v
                 Queue
                    │
                    v
                 Worker

Downloader ─────────┘

Untuk Phase 3:

Pipeline berhenti di READY.

Jangan implement publishing otomatis dulu.

==================================================
18. DAILY SLOT
==================================================

JANGAN implement Phase 4 sekarang.

Tetapi struktur Media harus siap digunakan oleh scheduler.

Downloader harus menyimpan:

created_at
destination_id
media_id
sequence-compatible identity

Jangan membuat daily slot logic sekarang kecuali dependency minimal benar-benar diperlukan.

Daily slot akan dibuat pada Phase 4.

==================================================
19. SEQUENCE
==================================================

Jangan membuat sequence harian.

Nomor sequence nantinya harus dapat berjalan terus.

Contoh:

Hari 1:
Video 1
Video 2
Video 3

Hari 2:
Video 4
Video 5
Video 6

Jika kapasitas hari pertama 4 tetapi hanya ada 3 video:

Hari 1:
08:00 Video 1
11:00 Video 2
14:00 Video 3
17:00 kosong

Jika Video baru masuk setelah hari pertama selesai:

Video baru = Video 4

bukan Video 1 lagi.

Phase 3 tidak perlu membuat scheduler final,
tetapi jangan membuat struktur data yang memaksa sequence reset setiap hari.

==================================================
20. PAGE / WORKSPACE NAVIGATION
==================================================

UI harus memiliki Destination/Workspace switcher.

Contoh:

[ Facebook Page A ▼ ]

Menu:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Jika user memilih:

[ Facebook Page B ]

context berubah menjadi Page B.

Semua halaman di workspace menggunakan destination context tersebut.

Contoh route konseptual:

/destinations/:destinationId/dashboard
/destinations/:destinationId/downloader
/destinations/:destinationId/storage
/destinations/:destinationId/publish
/destinations/:destinationId/queue
/destinations/:destinationId/schedule
/destinations/:destinationId/history

Gunakan pola routing yang sesuai dengan framework existing.

Jangan memaksakan URL tersebut jika framework mempunyai convention berbeda.

Yang WAJIB adalah destination context dan backend isolation.

==================================================
21. ACCOUNT vs DESTINATION
==================================================

Jangan mencampur:

Facebook Account
dengan
Facebook Page.

Contoh:

Account:
Facebook Login A

Destinations:
Page A
Page B
Page C

Downloader Page A harus memakai:

destination_id = Page A

bukan hanya:

account_id = Facebook Login A

Karena satu account dapat memiliki banyak Page.

==================================================
22. STORAGE ISOLATION
==================================================

Storage Page A dan Page B harus terpisah secara logical.

Contoh:

Page A:

Storage
→ Video 1
→ Video 2
→ Video 3

Page B:

Storage
→ Video 4
→ Video 5

Page A tidak boleh melihat Video 4.

Page B tidak boleh melihat Video 1.

Ini berlaku:

frontend
backend
database query
API
storage access

Jangan hanya menyembunyikan item melalui frontend.

==================================================
23. API
==================================================

Buat API yang sesuai dengan architecture existing.

Minimal capability:

Create/upload media
List media
Get media detail
Delete media
Create downloader job
Get downloader job/status

Semua endpoint harus authenticated.

Semua endpoint destination-scoped.

Contoh konsep:

POST /destinations/:destinationId/media/upload

GET /destinations/:destinationId/media

GET /destinations/:destinationId/media/:mediaId

DELETE /destinations/:destinationId/media/:mediaId

POST /destinations/:destinationId/downloader

GET /destinations/:destinationId/downloader/:jobId

Sesuaikan naming dengan API conventions existing.

==================================================
24. AUTHORIZATION
==================================================

Setiap request harus memeriksa:

Authenticated User
→ owns/accesses Destination
→ accesses Media
→ performs action

Jangan percaya destinationId yang dikirim client.

Jangan percaya userId yang dikirim client.

User identity harus berasal dari authentication/session/token server-side.

==================================================
25. ERROR HANDLING
==================================================

Error harus jelas.

Contoh:

Invalid destination
Unauthorized
Forbidden
Media not found
Unsupported file
File too large
Download failed
Storage failure
Processing failed
Duplicate detected

Jangan mengembalikan stack trace ke production UI.

Error internal dicatat di server/log system sesuai architecture.

==================================================
26. UI STATES
==================================================

Semua UI harus mempunyai:

Loading
Empty
Success
Error

Media Library kosong:

"Belum ada media"

Downloader sedang berjalan:

"Downloading..."

Media processing:

"Processing..."

READY:

"Ready"

FAILED:

"Failed"

Jangan menggunakan fake progress jika backend tidak menyediakan progress nyata.

==================================================
27. TESTING
==================================================

Tambahkan test untuk:

1. User dapat upload media ke Destination A.
2. Media masuk dengan destination_id A.
3. User dapat melihat media A.
4. User tidak dapat melihat media B dari workspace A.
5. User tidak dapat mengakses destination user lain.
6. Downloader membuat media record.
7. Downloader menyimpan source metadata.
8. Media berubah menjadi READY setelah pipeline sukses.
9. Failed download menghasilkan status FAILED.
10. Duplicate detection bekerja sesuai aturan.
11. Delete membersihkan/menandai media dengan benar.
12. Storage key aman.
13. Invalid MIME ditolak.
14. File terlalu besar ditolak.
15. Path traversal ditolak.
16. API authorization bekerja.
17. Workspace switcher menggunakan destination context yang benar.

Jangan menghapus test existing.

Semua regression test existing harus tetap PASS.

==================================================
28. SECURITY TEST
==================================================

Periksa khusus:

- IDOR
- unauthorized destination access
- cross-user media access
- cross-destination media access
- path traversal
- malicious filename
- invalid MIME
- oversized upload
- SSRF jika downloader menerima URL
- unsafe redirect
- arbitrary storage path
- credential leakage
- log leakage

Downloader URL harus divalidasi sesuai threat model.

Jika downloader mengambil URL remote, jangan langsung fetch arbitrary internal IP/private network.

Minimal pertimbangkan proteksi SSRF.

==================================================
29. DATABASE
==================================================

Jika schema database perlu perubahan:

1. Buat migration.
2. Jangan menghapus data existing.
3. Jangan destructive migration tanpa kebutuhan.
4. Gunakan foreign key yang benar.
5. Tambahkan index untuk query yang sering digunakan.

Minimal index yang kemungkinan dibutuhkan:

destination_id
status
created_at
source_type

Jika unique constraint digunakan, pastikan tidak menyebabkan media yang sama tidak dapat dipakai untuk destination berbeda.

==================================================
30. STORAGE
==================================================

Jika project menggunakan local storage sekarang:

buat StorageService abstraction agar nanti dapat dipindahkan ke:

S3
Cloudflare R2
MinIO
provider S3-compatible lainnya

tanpa mengubah Media business logic.

Jangan hardcode business logic ke filesystem.

==================================================
31. UI STRUCTURE
==================================================

Jangan membuat satu halaman besar yang berisi:

Downloader
Storage
Publish
Queue
Schedule
History

sekaligus.

Gunakan halaman/modul terpisah dalam workspace.

Contoh:

Page A
├── Dashboard
├── Downloader
├── Storage
├── Publish
├── Queue
├── Schedule
└── History

Phase 3 hanya perlu mengaktifkan:

Dashboard dasar
Downloader
Storage

Publish/Queue/Schedule/History dapat berupa placeholder yang jelas jika belum diimplementasikan.

Jangan membuat placeholder seolah-olah fitur sudah aktif.

==================================================
32. DASHBOARD WORKSPACE
==================================================

Jika Dashboard workspace sudah tersedia, gunakan.

Jika belum, buat minimal dashboard untuk destination tersebut.

Tampilkan informasi seperti:

Destination:
Facebook Page A

Media:
12

Ready:
8

Processing:
2

Failed:
2

Recent Media

Downloader status

Jangan membuat analytics palsu.

==================================================
33. FACEBOOK PUBLISHING
==================================================

JANGAN implementasikan Facebook publishing pada phase ini.

JANGAN memanggil Graph API publish.

JANGAN membuat fake published status.

Media READY hanya berarti media siap.

Publishing akan dilakukan pada Phase 5.

==================================================
34. FACEBOOK LIVE VERIFICATION
==================================================

Tidak perlu menjalankan live publishing verification pada Phase 3.

Jika environment belum memiliki:

META_APP_ID
META_APP_SECRET
OAuth credential

jangan membuat fake credential.

Jangan commit secret.

Phase 3 dapat diverifikasi tanpa live Facebook publishing.

==================================================
35. DOCUMENTATION
==================================================

Update documentation yang relevan.

Minimal:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/ROADMAP.md
docs/UI_DESIGN.md
docs/PLATFORM_MODULES.md

Jika ada dokumentasi media/storage yang memang diperlukan, buat dengan nama yang konsisten.

Dokumentasikan:

- Media model
- Storage abstraction
- Downloader pipeline
- Destination isolation
- Workspace architecture
- Media status
- source metadata
- duplicate detection
- security
- API flow

Jangan membuat duplicate documentation jika file existing sudah mempunyai bagian tersebut.

==================================================
36. ACCEPTANCE CRITERIA
==================================================

Phase 3 dianggap selesai hanya jika:

AC-01
Manual upload berhasil.

AC-02
Media tersimpan di database.

AC-03
Media file tersimpan di storage.

AC-04
Media mempunyai destination_id.

AC-05
Media Library Page A hanya menampilkan media Page A.

AC-06
Media Library Page B hanya menampilkan media Page B.

AC-07
Backend melakukan destination authorization.

AC-08
User tidak dapat melakukan IDOR terhadap destination/media.

AC-09
Downloader membuat Media record.

AC-10
Downloader menyimpan source metadata.

AC-11
Media pipeline dapat menghasilkan READY.

AC-12
Failed pipeline menghasilkan FAILED.

AC-13
Duplicate detection bekerja.

AC-14
Storage path aman.

AC-15
Upload validation bekerja.

AC-16
SSRF protection diperiksa jika downloader menggunakan remote URL.

AC-17
Delete media aman.

AC-18
Existing regression test tetap PASS.

AC-19
Typecheck PASS.

AC-20
Lint PASS.

AC-21
Test PASS.

AC-22
Build PASS.

AC-23
Git tidak mengandung secret.

==================================================
37. GIT
==================================================

Setelah implementation selesai:

1. git status
2. inspect diff
3. search secret
4. typecheck
5. lint
6. test
7. build

Pastikan tidak ada:

META_APP_SECRET
access token
refresh token
password
API key
credential

yang masuk Git.

Kemudian commit.

Commit message:

feat: implement media downloader and storage pipeline

Push ke branch yang sedang digunakan.

Jangan force push.

Setelah push:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

==================================================
38. FINAL REPORT
==================================================

Setelah selesai tampilkan:

PHASE 3 STATUS

MEDIA PIPELINE:
PASS / FAIL

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

STORAGE:
PASS / FAIL

DESTINATION ISOLATION:
PASS / FAIL

AUTHORIZATION:
PASS / FAIL

DUPLICATE DETECTION:
PASS / FAIL

SECURITY:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

PUSH STATUS:
SUCCESS / FAILED / NOT NEEDED

REMOTE VERIFIED:
YES / NO

NEXT RECOMMENDED PHASE:
PHASE 4 — DAILY SLOT & AUTO-PUBLISHING SCHEDULER

==================================================
STOP CONDITION
==================================================

SETELAH PHASE 3 SELESAI:

STOP.

Jangan implement Phase 4.

Jangan implement Facebook publishing.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Jangan menambahkan fitur di luar scope Phase 3.

Jika ada masalah, laporkan masalah sebenarnya.

Jangan membuat fake PASS.

Kerjakan berdasarkan repository yang benar-benar ada sekarang.
````
# Authentication & Account/Destination Management
```
Kita lanjutkan project Content Pilot dari kondisi repository TERAKHIR.

JANGAN mengulang Phase 0.
JANGAN membongkar architecture yang sudah PASS.
JANGAN membuat ulang fitur yang sudah selesai.
JANGAN membuat fake Facebook success.
JANGAN menggunakan credential palsu.
JANGAN menghapus fitur existing yang sudah bekerja.

Kondisi terakhir repository sudah memiliki fondasi:

- Facebook Provider: PASS
- Destination Workspace / Isolation: PASS
- Media Pipeline: PASS
- Downloader: PASS
- Publish / Queue / Worker: PASS
- Scheduler: PASS
- Daily Slot: PASS
- Sequence: PASS
- Retry: PASS
- Idempotency: PASS
- History: PASS
- Regression: PASS
- Typecheck: PASS
- Lint: PASS
- Test: PASS
- Build: PASS
- Git: CLEAN
- Push: SUCCESS
- Remote verified: YES

Facebook Live Verification dapat tetap NOT RUN apabila credential/provider configuration live memang belum tersedia di environment. Jangan membuat fake credential atau fake verification hanya untuk mengubah status menjadi PASS.

==================================================
TUJUAN PHASE BERIKUTNYA
==================================================

Sekarang lanjutkan ke:

PHASE 2 — AUTHENTICATION & ACCOUNT / DESTINATION MANAGEMENT

Tujuan phase ini adalah membuat fondasi yang benar untuk:

User
→ Platform Account / Connection
→ Destination
→ Destination Workspace

Sistem TIDAK boleh hanya mendukung satu Facebook account atau satu Facebook Page.

Arsitektur harus siap untuk:

User
├── Facebook Account 1
│   ├── Page A
│   ├── Page B
│   └── Page C
│
├── Facebook Account 2
│   ├── Page D
│   └── Page E
│
├── YouTube Account
│   ├── Channel A
│   └── Channel B
│
└── platform lain di masa depan

Facebook tetap hanya provider pertama.

Core system tetap platform-independent.

==================================================
ATURAN UTAMA
==================================================

1. Audit kondisi repository TERKINI terlebih dahulu sebelum coding.

2. Jangan membuat architecture baru jika architecture existing sudah memenuhi requirement.

3. Gunakan implementation existing yang sudah PASS.

4. Jangan melakukan massive refactor.

5. Jangan menghapus test existing.

6. Jangan menurunkan jumlah test.

7. Semua test yang sudah PASS harus tetap PASS setelah perubahan.

8. Jangan membuat mock/fake Facebook OAuth yang terlihat seperti OAuth sungguhan.

9. Gunakan Facebook/Meta official OAuth/API.

10. Jangan commit:
   - access token
   - refresh token
   - META_APP_SECRET
   - API key
   - password
   - cookie
   - session secret
   - credential lainnya

11. Environment variable tetap berada di environment server dan tidak boleh dimasukkan ke Git.

12. Jika `.env` sudah tersedia di VPS, gunakan environment tersebut.
    Jangan memindahkan secret ke source code.

13. Jangan mengubah secret yang sudah diberikan user.

14. Jangan meminta user mengulang secret jika tidak diperlukan.

15. Jika sebuah credential/configuration memang belum tersedia, tandai sebagai NEEDS CONFIGURATION.

16. Jangan membuat fake success hanya agar test hijau.

==================================================
BAGIAN 1 — AUDIT EXISTING AUTHENTICATION
==================================================

Sebelum coding, periksa:

- existing authentication
- user model
- session model
- authorization
- API authentication
- Facebook provider
- Meta OAuth flow
- PlatformConnection
- Destination
- database schema
- existing workspace/destination isolation
- existing UI
- existing routes
- existing tests

Cari apakah sudah ada:

- Facebook OAuth start endpoint
- Facebook OAuth callback
- token storage
- connection status
- Page discovery
- destination creation
- destination listing
- disconnect
- reconnect
- workspace switcher

Jika sudah ada, jangan buat duplicate.

Perbaiki implementation existing jika memang belum lengkap.

==================================================
BAGIAN 2 — DATA MODEL
==================================================

Pastikan model data dapat mendukung multi-account dan multi-destination.

Konsep minimal:

User

Platform

PlatformConnection

Destination

DestinationWorkspace / logical workspace

Media

PublishingJob

Schedule

PublishingAttempt

AuditLog

Jika repository sudah memiliki entity dengan nama berbeda tetapi fungsi sama, gunakan existing entity tersebut.

Jangan membuat duplicate entity hanya karena nama berbeda.

==================================================
PLATFORM
==================================================

Platform harus generik.

Contoh:

facebook
youtube
instagram
tiktok
x
pinterest
linkedin

Platform registry harus memungkinkan provider ditambahkan tanpa mengubah core publishing architecture.

==================================================
PLATFORM CONNECTION
==================================================

PlatformConnection harus mewakili koneksi account user ke platform.

Minimal konsep:

PlatformConnection

- id
- user_id
- platform_id / provider
- external_account_id
- account_name
- status
- access token reference / encrypted token storage
- token expiry jika tersedia
- created_at
- updated_at
- last_connected_at
- metadata jika diperlukan

Jangan menyimpan secret plaintext jika architecture repository sudah memiliki secure/encrypted storage.

Token jangan ditampilkan di UI.

Token jangan masuk log.

Token jangan masuk error message.

==================================================
DESTINATION
==================================================

Destination harus generik.

Contoh:

Facebook Page
YouTube Channel
Instagram Account
TikTok Account

Minimal konsep:

Destination

- id
- platform_connection_id
- external_id
- name
- type
- status
- metadata
- created_at
- updated_at

Destination harus selalu terkait dengan PlatformConnection.

Jangan membuat Page hanya berdasarkan nama.

Gunakan external ID sebagai identifier utama untuk destination integration.

==================================================
MULTI DESTINATION
==================================================

Satu user dapat memiliki banyak destination.

Contoh:

User A

Facebook Account
→ Page A
→ Page B
→ Page C

Jika user memiliki Facebook Account lain:

Facebook Account 2
→ Page D
→ Page E

Semua harus dapat hidup bersamaan.

Jangan overwrite Page lama ketika akun Facebook kedua di-connect.

Jangan menggunakan satu global:

FACEBOOK_PAGE_ID

sebagai konfigurasi utama.

Destination harus database-driven.

==================================================
DESTINATION WORKSPACE
==================================================

Setiap destination memiliki workspace sendiri.

Contoh:

Page A

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Page B

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History

Page A tidak boleh membaca data Page B secara tidak sengaja.

Semua query yang destination-scoped harus menggunakan destination_id atau relation yang aman.

Contoh:

GET /api/destinations/:destinationId/media

GET /api/destinations/:destinationId/queue

GET /api/destinations/:destinationId/schedule

GET /api/destinations/:destinationId/history

Tetapi jangan membuat route duplicate jika route existing sudah memiliki pola yang benar.

Backend harus menjadi sumber isolation.

JANGAN hanya melakukan filter di frontend.

==================================================
WORKSPACE SWITCHER
==================================================

UI harus memiliki Destination / Workspace Switcher.

Contoh:

Current Workspace:

[ Facebook Page A ▼ ]

Dropdown:

Facebook
  Page A
  Page B
  Page C

YouTube
  Channel A
  Channel B

Saat user memilih destination:

- Dashboard berubah ke destination tersebut
- Downloader menggunakan destination tersebut
- Storage menggunakan destination tersebut
- Publish menggunakan destination tersebut
- Queue menggunakan destination tersebut
- Schedule menggunakan destination tersebut
- History menggunakan destination tersebut

Jangan membuat data workspace hanya berdasarkan state frontend.

Destination ID harus ikut dalam request ke backend.

Backend tetap melakukan authorization dan isolation.

==================================================
FACEBOOK OAUTH
==================================================

Gunakan official Meta/Facebook OAuth flow.

Jangan menggunakan:

- username/password automation
- browser scraping
- cookie injection
- fake OAuth
- fake access token

Flow yang diinginkan:

User
→ Accounts
→ Connect Facebook
→ Meta authorization
→ callback
→ exchange authorization code
→ secure token storage
→ retrieve available Pages
→ create/update Destination records
→ user kembali ke Accounts / Destination selection

Jika existing implementation sudah memiliki callback:

/api/connections/facebook/callback

gunakan dan perbaiki jika diperlukan.

Jangan membuat callback duplicate.

==================================================
OAUTH CONFIGURATION
==================================================

Environment configuration harus mendukung minimal:

META_APP_ID
META_APP_SECRET

Jika aplikasi membutuhkan redirect URL atau public base URL, gunakan konfigurasi existing yang sudah sesuai architecture.

Jangan hardcode:

META_APP_ID
META_APP_SECRET
redirect URI

ke source code.

Pastikan `.env` tetap di-ignore Git.

Setelah perubahan:

periksa:

git status
git diff

Pastikan secret tidak ikut.

==================================================
CALLBACK / REDIRECT
==================================================

Pastikan OAuth callback memiliki redirect URI yang konsisten.

Jangan mengasumsikan localhost adalah production URL.

Support configuration seperti:

development
staging
production

Gunakan base URL/configuration yang sesuai environment.

Jika existing documentation menyebut SSH tunnel localhost untuk development, jangan mengubah production menjadi localhost.

Dokumentasikan:

- development callback
- production callback
- Meta Dashboard configuration yang diperlukan

Jangan memasukkan secret ke documentation.

==================================================
FACEBOOK PAGE DISCOVERY
==================================================

Setelah OAuth berhasil:

1. Ambil Page yang memang dapat diakses oleh connection.
2. Parse Page ID.
3. Parse Page name.
4. Simpan destination.
5. Jangan duplicate destination jika sudah ada.
6. Jika Page sudah ada tetapi metadata berubah, update metadata yang aman.
7. Jangan menghapus Page lama hanya karena tidak muncul dalam satu discovery response.
8. Status destination harus jelas.

Contoh:

Facebook Account
→ Page A
→ Page B
→ Page C

Setiap Page menjadi Destination tersendiri.

==================================================
RECONNECT
==================================================

Accounts UI harus dapat menunjukkan:

Connected
Needs Reconnect
Disconnected
Configuration Required
Error

Jika token expired/invalid:

status harus dapat berubah menjadi:

Needs Reconnect

Jangan otomatis menghapus destination dan history hanya karena connection bermasalah.

History publishing harus tetap ada.

Media harus tetap ada.

Schedule yang belum dipublish harus memiliki status yang jelas.

==================================================
DISCONNECT
==================================================

Disconnect harus aman.

Pisahkan:

Disconnect Platform Connection

dan:

Delete Destination

Jangan menghapus data publishing history secara otomatis hanya karena user disconnect.

Jika ada destructive action:

- tampilkan confirmation
- jelaskan konsekuensinya
- jangan melakukan cascading delete berbahaya

Jika requirement belum menentukan delete behavior, jangan mengarang.
Dokumentasikan sebagai open decision.

==================================================
AUTHORIZATION
==================================================

User A tidak boleh melihat:

- connection milik User B
- destination milik User B
- media milik User B
- publishing job milik User B
- schedule milik User B
- history milik User B

Authorization harus dicek backend.

Jangan hanya mengandalkan ID yang dikirim frontend.

Contoh:

GET /api/destinations/:id

Backend harus memastikan:

destination.user_id == current_user.id

atau relation authorization yang setara.

==================================================
DESTINATION AUTHORIZATION
==================================================

Setiap operasi harus memastikan user memang memiliki destination tersebut.

Contoh:

User A request:

POST /api/destinations/page-B/publish

Jika Page B milik User B:

→ 403/404 sesuai security policy.

Jangan publish.

Jangan return metadata sensitif.

==================================================
ACCOUNT UI
==================================================

Buat/rapikan halaman:

Accounts

Konsep:

Connected Accounts

[ Facebook ]
Status: Connected

2 Pages available

[ Manage ]

[ Disconnect ]

Jika belum connected:

[ Connect Facebook ]

Jangan membuat UI seolah YouTube/Instagram sudah tersedia jika provider belum diimplementasikan.

Platform yang belum tersedia:

Coming Soon

atau status capability yang sesuai.

==================================================
DESTINATION UI
==================================================

Buat halaman/section:

Destinations

Contoh:

Facebook
-------------------------
Page A
Connected
[Open Workspace]

Page B
Connected
[Open Workspace]

Page C
Needs Reconnect
[Reconnect]

Jangan menampilkan access token.

==================================================
WORKSPACE NAVIGATION
==================================================

Target:

Destination Switcher
→ Dashboard
→ Downloader
→ Storage
→ Publish
→ Queue
→ Schedule
→ History

Semua halaman harus mengetahui destination context.

Contoh URL dapat berupa:

/d/:destinationId/dashboard
/d/:destinationId/downloader
/d/:destinationId/storage
/d/:destinationId/publish
/d/:destinationId/queue
/d/:destinationId/schedule
/d/:destinationId/history

ATAU gunakan routing existing jika repository sudah memiliki pola yang lebih baik.

Jangan memaksakan URL tersebut jika architecture existing berbeda.

Yang wajib adalah:

destination context harus eksplisit dan backend-scoped.

==================================================
DOWNLOADER
==================================================

Jangan mengubah logic downloader yang sudah PASS kecuali diperlukan agar destination context benar.

Downloader harus menerima:

destination_id

atau context yang dapat diturunkan secara aman.

Hasil downloader:

Media
→ source metadata
→ destination scoped
→ READY

Jika downloader dijalankan dari Page A:

media.destination_id = Page A

Media tidak boleh otomatis masuk Page B.

==================================================
STORAGE
==================================================

Storage workspace harus destination-aware secara logical.

Contoh:

Page A
→ Media 1
→ Media 2

Page B
→ Media 3
→ Media 4

Jangan mencampur daftar media antar workspace.

Jika media yang sama nanti digunakan untuk banyak destination melalui multi-destination publishing:

core Media tetap satu.

PublishingJob dibuat terpisah:

Media X
→ Job Page A
→ Job Page B

Jangan duplicate binary file tanpa alasan.

==================================================
DAILY SLOT
==================================================

Jangan merusak sistem Daily Slot yang sudah PASS.

Konfigurasi tetap:

max_videos_per_day
timezone
daily_slots

Contoh:

max = 4

08:00
11:00
14:00
17:00

Sequence tidak reset ketika tanggal berganti.

Jika Hari 1 hanya memiliki:

Video 1
Video 2
Video 3

slot keempat kosong.

Jika video baru masuk setelah itu dan Hari 1 sudah selesai:

Video 4
→ slot berikutnya pada Hari 2

Bukan kembali menjadi Video 1.

Jika Hari 1 penuh:

Video 5
→ Hari 2 slot pertama.

Semua allocation harus deterministic dan idempotent.

Jangan mengubah schedule job yang sudah final/published.

==================================================
PUBLISHING JOB
==================================================

Tetap satu job per destination.

Contoh:

Media 100

Page A
→ Job A

Page B
→ Job B

YouTube Channel A
→ Job C

Status independen.

==================================================
QUEUE / WORKER
==================================================

Jangan membangun queue baru jika queue existing sudah PASS.

Gunakan queue existing.

Worker mengambil PublishingJob.

Worker mendapatkan:

- provider
- connection
- destination
- media
- schedule
- metadata

Kemudian memanggil provider yang sesuai.

==================================================
TESTING
==================================================

Sebelum perubahan:

jalankan test existing.

Catat baseline.

Setelah implementation:

1. typecheck
2. lint
3. unit test
4. integration test yang aman
5. build

Target:

semua test existing tetap PASS.

Tambahkan test untuk:

1. User memiliki multiple Facebook Pages.
2. User memiliki multiple Facebook connections.
3. Destination tidak duplicate.
4. Destination A tidak dapat diakses User B.
5. Media Page A tidak muncul di Page B.
6. Downloader Page A menghasilkan media scoped Page A.
7. Queue Page A tidak mengambil job Page B.
8. Schedule Page A tidak mengambil schedule Page B.
9. History Page A tidak mencampur Page B.
10. Workspace switcher mengirim destination context yang benar.
11. OAuth callback memproses connection yang benar.
12. Reconnect tidak menghapus history.
13. Disconnect tidak menghapus media secara otomatis.
14. Invalid destination ownership ditolak.
15. Daily Slot existing tetap PASS.
16. Sequence existing tetap tidak reset.
17. Retry/idempotency existing tetap PASS.

Jangan menghapus regression test yang sudah ada.

==================================================
LIVE FACEBOOK VERIFICATION
==================================================

Jika environment VPS sekarang sudah memiliki:

META_APP_ID
META_APP_SECRET

dan konfigurasi OAuth lengkap:

boleh lakukan real OAuth verification.

Namun:

JANGAN meminta user memberikan secret di chat.

JANGAN mencetak secret.

JANGAN memasukkan secret ke terminal output yang disimpan.

JANGAN membuat fake Page.

JANGAN membuat fake publish.

Jika redirect URI belum dikonfigurasi di Meta Dashboard:

laporkan sebagai:

NEEDS CONFIGURATION

dan lanjutkan verification yang aman tanpa fake success.

==================================================
DOCUMENTATION
==================================================

Update documentation yang relevan.

Minimal:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/UI_DESIGN.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md

Tambahkan dokumentasi:

### Account Architecture

User
→ PlatformConnection
→ Destination
→ Workspace

### Destination Isolation

Semua operasi destination-scoped.

### OAuth

Flow:

Connect
→ Authorize
→ Callback
→ Token storage
→ Destination discovery

### Reconnect

Token invalid/expired
→ Needs Reconnect
→ OAuth ulang
→ update connection
→ destination/history tetap aman

### Multi Account

Satu user dapat memiliki multiple connections dan destinations.

==================================================
DATABASE MIGRATION
==================================================

Jika database schema perlu berubah:

1. buat migration yang aman
2. jangan menghapus data existing
3. jangan destructive migration tanpa alasan
4. gunakan foreign key yang tepat
5. tambahkan index untuk query destination-scoped
6. pastikan authorization query efisien

Pertimbangkan index:

user_id
platform_connection_id
destination_id
external_id

Jangan membuat unique constraint yang mencegah user memiliki beberapa account jika requirement memang mendukung multiple account.

==================================================
SECURITY REVIEW
==================================================

Setelah coding lakukan review:

- secret tidak masuk Git
- token tidak masuk log
- token tidak masuk response API
- user isolation benar
- destination isolation benar
- OAuth state/CSRF protection benar
- callback validation benar
- redirect URI validation benar
- file upload security existing tetap PASS
- SSRF protection existing tetap PASS
- authorization backend benar

Jika menemukan vulnerability:

perbaiki sebelum commit.

==================================================
GIT
==================================================

Setelah semua selesai:

1. git status
2. git diff
3. periksa secret
4. jalankan test
5. typecheck
6. lint
7. build
8. commit
9. push ke branch yang sedang digunakan
10. verify remote

Commit message:

feat: implement account and destination management

Jangan force push.

Jangan commit secret.

Jangan membuat empty commit.

Jika tidak ada source change yang memang diperlukan, jangan membuat commit kosong.

==================================================
LAPORAN AKHIR
==================================================

Setelah selesai, tampilkan laporan ringkas tetapi lengkap:

PHASE:
Phase 2 — Authentication & Account / Destination Management

AUDIT:
PASS / FAIL

ACCOUNT MANAGEMENT:
PASS / PARTIAL / FAIL

FACEBOOK OAUTH:
PASS / NEEDS CONFIGURATION / NOT RUN

MULTI ACCOUNT:
PASS / FAIL

MULTI DESTINATION:
PASS / FAIL

DESTINATION ISOLATION:
PASS / FAIL

WORKSPACE SWITCHER:
PASS / FAIL

DOWNLOADER ISOLATION:
PASS / FAIL

STORAGE ISOLATION:
PASS / FAIL

QUEUE ISOLATION:
PASS / FAIL

SCHEDULE ISOLATION:
PASS / FAIL

HISTORY ISOLATION:
PASS / FAIL

AUTHORIZATION:
PASS / FAIL

SECURITY:
PASS / FAIL

DAILY SLOT REGRESSION:
PASS / FAIL

SEQUENCE REGRESSION:
PASS / FAIL

RETRY / IDEMPOTENCY:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / <jumlah test>

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / NOT NEEDED / FAILED

REMOTE VERIFIED:
YES / NO

Jika Facebook Live Verification tidak dapat dijalankan karena environment/Meta configuration, tuliskan alasan sebenarnya.

JANGAN mengubah NOT RUN menjadi PASS hanya dengan mock.

==================================================
STOP CONDITION
==================================================

Setelah Phase 2 selesai dan push berhasil:

STOP.

Jangan lanjut otomatis ke Phase 3.

Jangan mulai fitur baru.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Jangan implement analytics.

Jangan membuat fitur tambahan di luar scope Phase 2.

Tujuan phase ini hanya:

USER
→ MULTIPLE ACCOUNTS
→ MULTIPLE DESTINATIONS
→ DESTINATION WORKSPACE
→ SECURE OAUTH CONNECTION
→ DESTINATION DISCOVERY
→ DESTINATION ISOLATION
→ ACCOUNT MANAGEMENT

Fondasi Daily Slot, Downloader, Media Pipeline, Queue, Worker, Scheduler, Retry, Idempotency, dan History yang sudah PASS harus tetap dipertahankan.

Jika menemukan masalah architecture selama implementation, perbaiki hanya yang benar-benar diperlukan dan dokumentasikan alasannya.

STOP setelah laporan akhir dan remote verification.

````
# Phase Facebook Publishing Hardening
```

LANJUTKAN IMPLEMENTASI PROJECT CONTENT PILOT.

Jangan mengulang audit Phase 0 yang sudah selesai.
Jangan meminta konfirmasi kredit/approval.
Jangan berhenti hanya karena ada hal kecil yang perlu diperbaiki.
Kerjakan langsung sampai selesai, test, commit, dan push.

==================================================
KONTEKS PROJECT
==================================================

Project ini adalah Content Pilot, sebuah platform centralized content publishing.

Facebook adalah provider pertama, tetapi CORE SYSTEM harus tetap platform-independent agar nantinya dapat mendukung:

- Facebook
- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn
- platform lain yang memiliki official publishing API.

JANGAN membuat core menjadi Facebook-only.

Phase 0 sebelumnya sudah menghasilkan architecture, documentation, destination isolation, workspace concept, media/publishing foundation, dan roadmap.

Sekarang masuk ke implementasi berikutnya:

PHASE:
Facebook Publishing Hardening + Destination Workspace + Publishing Pipeline Integration

Tujuan phase ini adalah membuat alur Facebook publishing benar-benar siap digunakan secara nyata tanpa merusak architecture yang sudah ada.

==================================================
ATURAN UTAMA
==================================================

1. Jangan membuang architecture existing yang sudah PASS.
2. Jangan melakukan rewrite besar jika tidak diperlukan.
3. Jangan membuat duplicate system.
4. Jangan membuat fake Facebook success.
5. Jangan menggunakan Facebook username/password automation.
6. Gunakan official Facebook/Meta API.
7. Jangan mengarang endpoint atau permission.
8. Jika API tertentu berubah atau belum tersedia, research official documentation terlebih dahulu.
9. Jangan memasukkan secret/token ke Git.
10. Jangan commit .env.
11. Jangan mematikan test existing.
12. Jangan menghapus regression test.
13. Jangan membuat test palsu hanya supaya PASS.
14. Jangan menggunakan mock sebagai pengganti integration behavior yang sebenarnya jika environment memungkinkan verification.
15. Unit test boleh menggunakan mock provider untuk logic internal.
16. Integration test harus tetap membedakan antara:
   - test internal
   - test provider configuration
   - live Facebook verification.
17. Jika credential Facebook belum tersedia di VPS, jangan membuat fake success.
18. Jika live credential tidak tersedia, tandai live verification sebagai NOT RUN / NEEDS CONFIGURATION, tetapi seluruh logic internal tetap harus ditest.
19. Jangan berhenti hanya karena live credential tidak tersedia.
20. Setelah implementasi selesai, lakukan git status, diff review, test, build, commit, push, dan remote verification.

==================================================
ARSITEKTUR WORKSPACE
==================================================

Konsep utama project sekarang adalah:

USER
 └── Platform Accounts
      └── Destinations
           └── Destination Workspace

Contoh:

Facebook Account
├── Page A
│   └── Workspace Page A
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
├── Page B
│   └── Workspace Page B
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
└── Page C
    └── Workspace Page C
        ├── Dashboard
        ├── Downloader
        ├── Storage
        ├── Publish
        ├── Queue
        ├── Schedule
        └── History

Workspace bukan berarti harus menjadi service terpisah.

Workspace adalah logical scope yang terutama menggunakan:

destination_id

Semua operasi harus benar-benar destination-scoped.

==================================================
DESTINATION ISOLATION
==================================================

Ini WAJIB.

Downloader Page A:

→ hanya masuk ke media/storage Page A.

Publish Page A:

→ hanya dapat memilih destination Page A jika user berada di workspace Page A.

Queue Page A:

→ hanya memproses job Page A.

Schedule Page A:

→ hanya membuat schedule Page A.

History Page A:

→ hanya menampilkan history Page A.

Page B tidak boleh melihat/mengambil queue Page A secara tidak sengaja.

Backend harus melakukan authorization dan filtering berdasarkan destination_id.

JANGAN hanya mengandalkan frontend filter.

Frontend filter saja TIDAK dianggap isolation.

Backend harus menolak akses cross-destination.

Contoh:

GET /api/destinations/:destinationId/media

harus memastikan destination tersebut memang milik user/account yang sedang authenticated.

Jika tidak:

404 atau 403 sesuai pola API existing.

Hal yang sama berlaku untuk:

- media
- downloader
- storage
- publish
- queue
- schedule
- history
- publishing jobs
- attempts
- settings.

==================================================
DESTINATION WORKSPACE SWITCHER
==================================================

Implementasikan atau sempurnakan workspace/destination switcher.

User harus dapat memilih:

Facebook Page A
Facebook Page B
Facebook Page C

Saat berpindah Page:

SEMUA CONTEXT HARUS BERGANTI.

Contoh:

/d/page-a/dashboard
/d/page-a/downloader
/d/page-a/storage
/d/page-a/publish
/d/page-a/queue
/d/page-a/schedule
/d/page-a/history

Kemudian:

/d/page-b/dashboard
/d/page-b/downloader
...

Jika routing project menggunakan pola berbeda, ikuti pola existing.

Jangan memaksakan URL tersebut jika tidak cocok dengan framework.

Yang penting:

destination context harus eksplisit.

==================================================
PUBLISH PAGE
==================================================

Buat/sesuaikan halaman Publish dalam workspace destination.

Publish harus mengetahui destination saat ini.

Contoh:

CURRENT WORKSPACE:
Facebook Page A

User memilih media:

Video 001

Caption:
...

Publishing type:

- Video
- Reels
- Photo
- Text Post
- fitur lain hanya jika provider capability mendukung.

Destination:

Facebook Page A

Jangan menampilkan Page B sebagai destination default tanpa user memilihnya.

Jika multi-destination publishing didukung, target tambahan harus secara eksplisit dipilih dan masing-masing menghasilkan PublishingJob terpisah.

==================================================
MEDIA
==================================================

Media adalah entity generik.

Jangan membuat FacebookMedia sebagai storage utama.

Minimal media tetap memiliki konsep:

- id
- filename
- mime_type
- size
- duration
- width
- height
- storage_key/location
- thumbnail
- source_type
- source_id/source_url jika tersedia
- created_at
- status
- metadata

Source type minimal:

manual
downloader
other

Media downloader harus dapat dilacak dari sumbernya.

Jika downloader mengambil video dari Facebook:

simpan source metadata yang aman.

Jangan menganggap source URL sebagai identifier utama.

Media ID tetap menjadi identifier utama.

==================================================
DOWNLOADER
==================================================

Downloader harus terintegrasi dengan workspace.

Jika user berada di:

Facebook Page A

dan melakukan downloader:

video harus otomatis masuk ke:

Page A Storage / Media Library

bukan global tanpa destination context.

Jika downloader memang menghasilkan media generik yang nantinya bisa dipakai beberapa destination, tetap simpan:

source destination/context

dan buat publishing job destination-specific saat dipublish.

Jangan membuat downloader menggandakan file secara tidak perlu.

==================================================
STORAGE
==================================================

Storage harus terintegrasi dengan destination workspace.

Tampilkan:

- video
- thumbnail
- duration
- size
- source
- created date
- status
- publishing status jika ada.

Storage tidak boleh menampilkan media milik destination lain kecuali memang ada global library yang sengaja dirancang.

Jika terdapat global media library:

tetap pastikan destination-scoped view bekerja benar.

==================================================
FACEBOOK PROVIDER
==================================================

Facebook provider harus tetap berada di provider/module layer.

Core tidak boleh berisi Facebook Graph API logic.

Contoh konsep:

Core
→ Provider Registry
→ Facebook Provider
→ Facebook API Client
→ Facebook publishing implementation

Gunakan struktur existing project jika sudah tersedia.

Jangan memindahkan seluruh code ke struktur baru jika existing structure sudah modular.

==================================================
FACEBOOK CONNECTION
==================================================

Gunakan official OAuth/API.

Connection harus memiliki konsep:

- provider
- account identity
- access token / encrypted credential reference
- expiration jika tersedia
- status
- connected_at
- last_verified_at
- metadata aman.

Jangan menyimpan secret plaintext jika architecture existing menyediakan encryption.

Jangan memasukkan token ke logs.

Jangan menampilkan token di UI.

==================================================
FACEBOOK PAGE DISCOVERY
==================================================

Setelah Facebook account connected:

ambil Page/Destination yang memang dapat diakses oleh account tersebut menggunakan API resmi.

Setiap Page menjadi:

Destination

Contoh:

Destination:
- id
- platform = facebook
- type = page
- external_id
- name
- avatar/image jika tersedia
- connection_id
- status
- metadata.

External Page ID harus disimpan.

Jangan menggunakan nama Page sebagai unique identifier.

==================================================
FACEBOOK PUBLISHING
==================================================

Implementasikan publishing menggunakan official Facebook/Meta API yang sesuai dengan capability yang telah diverifikasi.

Minimal target:

- video publishing
- Reels publishing jika official API flow tersedia dan permission/configuration sesuai.

Jangan menganggap semua content type tersedia.

Gunakan provider capability.

Contoh:

FacebookProvider.capabilities():

video
reels
photo
text_post
scheduling

Hanya masukkan capability yang benar-benar didukung implementation dan API.

==================================================
PUBLISHING FLOW
==================================================

Flow:

User memilih media
        ↓
validasi media
        ↓
pilih destination
        ↓
pilih publish now / schedule
        ↓
buat PublishingJob
        ↓
queue
        ↓
worker
        ↓
Facebook Provider
        ↓
Facebook API
        ↓
status update
        ↓
history

Jangan langsung melakukan Facebook API call dari frontend.

Frontend → Backend → Queue/Worker → Provider → Facebook API.

==================================================
PUBLISH NOW
==================================================

Jika user memilih Publish Now:

buat job:

status = queued

kemudian worker memproses.

Jangan menganggap queued berarti published.

Status harus mengikuti lifecycle sebenarnya.

Contoh:

queued
→ processing
→ uploading
→ publishing
→ published

Jika gagal:

failed

==================================================
PUBLISHING STATUS
==================================================

PublishingJob minimal:

- id
- media_id
- destination_id
- provider
- content_type
- status
- scheduled_at
- published_at
- created_at
- updated_at
- attempt_count
- last_error_code
- last_error_message
- provider_post_id jika tersedia
- provider_metadata jika aman.

Jangan menyimpan access token di PublishingJob.

==================================================
PUBLISHING ATTEMPT
==================================================

Jika architecture mendukung PublishingAttempt:

buat satu record setiap attempt.

Minimal:

- id
- publishing_job_id
- attempt_number
- started_at
- finished_at
- status
- error_code
- error_message
- provider_request/reference metadata yang aman.

Jangan menyimpan token atau secret.

==================================================
IDEMPOTENCY
==================================================

Publishing harus idempotent.

Jangan sampai worker retry lalu membuat post Facebook dua kali jika attempt pertama sebenarnya sudah berhasil tetapi response timeout.

Gunakan strategy yang sesuai architecture:

- provider post ID
- idempotency key jika API mendukung
- persisted attempt state
- state transition guard
- unique publishing job constraints.

Jangan mengarang idempotency API Facebook jika tidak tersedia.

Buat protection di application layer.

==================================================
RETRY
==================================================

Temporary errors:

- timeout
- network error
- temporary provider error
- rate limit

→ retry dengan backoff.

Permanent errors:

- invalid credentials
- permission denied
- destination invalid
- unsupported media
- invalid request

→ failed tanpa infinite retry.

Simpan:

attempt_count
last_error_code
last_error_message
next_retry_at

Jangan membuat infinite retry loop.

==================================================
QUEUE
==================================================

Queue harus menggunakan architecture existing.

Jangan membuat queue kedua jika queue foundation sudah ada.

PublishingJob:

queued
→ worker
→ provider.

Worker harus mengetahui:

provider
destination
media
content type
schedule.

Worker mengambil job lalu memanggil provider berdasarkan provider registry.

Contoh:

provider = facebook

→ FacebookProvider.publish(job)

==================================================
SCHEDULER
==================================================

Jangan membuat scheduler khusus Facebook.

Scheduler harus generik.

Schedule selalu memiliki:

destination_id
publishing_job_id/media relation sesuai model existing
scheduled_at
timezone/context
status.

Scheduler tidak boleh mengambil schedule Page A ketika memproses Page B.

==================================================
DAILY SLOT SYSTEM
==================================================

Implementasikan atau integrasikan fondasi Daily Slot yang sudah dirancang sebelumnya.

Contoh:

Max videos/day = 4

Slots:

08:00
11:00
14:00
17:00

Jika downloader memasukkan:

Video 1
Video 2
Video 3
Video 4

maka:

Hari 1:
08:00 Video 1
11:00 Video 2
14:00 Video 3
17:00 Video 4

Jika kemudian:

Video 5

maka:

Hari 2:
08:00 Video 5

JANGAN RESET menjadi Video 1.

Sequence harus terus berjalan.

==================================================
KASUS HARI TIDAK PENUH
==================================================

Contoh:

Max videos/day = 4

Hari pertama hanya ada:

Video 1
Video 2
Video 3

maka:

Hari 1:
08:00 Video 1
11:00 Video 2
14:00 Video 3
17:00 kosong

Jika Video 4 baru masuk setelah slot hari pertama berlalu:

Video 4 → slot berikutnya yang tersedia di hari berikutnya.

Hari 2:
08:00 Video 4

Bukan:

Video 1 lagi.

Sequence tidak pernah reset hanya karena tanggal berganti.

==================================================
SEQUENCE
==================================================

Bedakan:

media_id
sequence_number
publishing_job_id

sequence_number tidak boleh bergantung pada filename.

sequence_number tidak reset setiap hari.

Jangan recycle sequence number dari job yang pernah dibuat.

Jika job gagal/cancelled:

sequence tetap tidak boleh digunakan ulang sembarangan.

Jika project existing sudah memiliki sequence implementation, pertahankan dan harden sesuai aturan ini.

==================================================
MANUAL SCHEDULE OVERRIDE
==================================================

User dapat memilih schedule manual untuk video tertentu.

Contoh:

Auto slot:
08:00

Tetapi user memilih:

20:00

Maka job tersebut menggunakan:

schedule_source = manual

dan scheduled_at = 20:00.

Jangan biarkan auto scheduler menimpa manual schedule kecuali user memang mengubahnya.

==================================================
RESCHEDULING
==================================================

Jika konfigurasi daily slot berubah:

contoh:

4 video/day
→ menjadi 3 video/day

Jangan sembarangan mengubah job yang sudah:

published
processing
publishing

Perubahan konfigurasi hanya mempengaruhi schedule yang masih eligible untuk diubah sesuai rules.

Job dengan schedule final harus aman.

Manual schedule harus dihormati.

==================================================
TIMEZONE
==================================================

Daily slot harus memiliki timezone.

Contoh:

Asia/Jakarta

Waktu UI harus jelas menggunakan timezone workspace/destination.

Jangan menggunakan timezone VPS sebagai satu-satunya sumber kebenaran.

Jika project existing sudah memiliki timezone provenance, pertahankan.

Simpan waktu internal dalam format yang konsisten, idealnya UTC, lalu tampilkan berdasarkan timezone destination/workspace.

==================================================
QUEUE + DAILY SLOT
==================================================

Flow yang diinginkan:

Downloader
    ↓
Media READY
    ↓
Destination Workspace
    ↓
Auto Scheduler
    ↓
Cari slot tersedia
    ↓
Buat PublishingJob
    ↓
scheduled
    ↓
Saat waktunya tiba
    ↓
queued
    ↓
Worker
    ↓
Facebook Provider
    ↓
Facebook API
    ↓
published / failed

Jangan membuat media langsung published hanya karena scheduler berhasil.

==================================================
HISTORY
==================================================

History harus destination-scoped.

Page A:

hanya melihat history Page A.

Page B:

hanya melihat history Page B.

History minimal menampilkan:

- video/media
- content type
- destination
- scheduled time
- publish time
- status
- provider post ID jika tersedia
- error jika gagal
- attempts.

==================================================
DASHBOARD
==================================================

Dashboard workspace harus menunjukkan konteks Page aktif.

Contoh:

FACEBOOK
Page A

Today:

Scheduled: 4
Published: 2
Queue: 1
Failed: 1

Storage:
Ready: 10
Processing: 1

Jangan mencampur angka Page A dan Page B.

Jika ada global dashboard, pisahkan dengan jelas dari workspace dashboard.

==================================================
SETTINGS PER DESTINATION
==================================================

Auto publishing settings harus destination-scoped.

Minimal:

enabled
max_videos_per_day
timezone
daily_slots
auto_publish_enabled

Contoh:

Page A:
4 videos/day
08:00
11:00
14:00
17:00

Page B:
2 videos/day
09:00
18:00

Keduanya tidak boleh saling mempengaruhi.

==================================================
API SECURITY
==================================================

Pastikan semua endpoint destination-aware.

Jangan cukup:

GET /api/media

lalu frontend melakukan filter.

Backend harus menerapkan scope.

Audit seluruh endpoint baru dan existing yang berhubungan dengan:

- destinations
- media
- downloader
- publish
- jobs
- queue
- schedule
- history
- settings.

Cari kemungkinan IDOR/cross-destination access.

Tambahkan regression test.

==================================================
TESTING
==================================================

Jangan hanya test happy path.

Minimal test:

1. Page A dapat melihat media Page A.
2. Page A tidak dapat melihat media Page B.
3. Page A dapat membuat publish job Page A.
4. Page A tidak dapat membuat publish job untuk Page B tanpa explicit authorization.
5. Downloader Page A menghasilkan destination_id Page A.
6. Scheduler Page A tidak mengambil media Page B.
7. Queue Page A tidak memproses job Page B secara salah.
8. History Page A tidak menampilkan Page B.
9. Daily slot 4/day bekerja.
10. Sequence tidak reset.
11. Hari pertama hanya 3 video → video berikutnya masuk slot hari berikutnya.
12. Video ke-5 setelah 4 video → masuk hari berikutnya.
13. Manual schedule override tidak ditimpa auto scheduler.
14. Failed job tidak membuat sequence reuse.
15. Retry temporary error.
16. Permanent error tidak retry infinite.
17. Idempotency protection.
18. Publish status transition.
19. Destination authorization.
20. Token tidak muncul di response/log.
21. Existing regression suite tetap PASS.

Jika provider Facebook tidak memiliki credential live di environment:

LIVE FACEBOOK VERIFICATION:
NOT RUN / NEEDS CONFIGURATION

Tetapi provider unit/integration logic tetap harus PASS.

==================================================
FACEBOOK LIVE TEST
==================================================

Jika environment memiliki:

META_APP_ID
META_APP_SECRET
dan credential OAuth/Page yang valid,

gunakan untuk verification nyata.

Jangan print secret.

Jangan print access token.

Jika belum ada:

jangan fake.

Tampilkan:

FACEBOOK LIVE VERIFICATION:
NOT RUN (credentials/provider configuration unavailable)

Ini bukan alasan untuk menghentikan implementasi internal.

==================================================
ENVIRONMENT
==================================================

Pastikan project membaca secret dari environment.

Contoh:

META_APP_ID=...
META_APP_SECRET=...

Jangan hardcode.

Jangan commit .env.

Periksa .gitignore.

Pastikan:

.env
.env.*
secret files
credential files

tidak masuk Git, tetapi jangan sampai meng-ignore file konfigurasi non-secret yang memang dibutuhkan repository.

Jika .env.example diperlukan:

gunakan placeholder.

Contoh:

META_APP_ID=
META_APP_SECRET=

Jangan masukkan credential nyata.

==================================================
DOCUMENTATION UPDATE
==================================================

Update documentation yang relevan setelah implementation.

Minimal jika sesuai repository:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/UI_DESIGN.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md

Dokumentasikan:

- Destination Workspace
- destination isolation
- Facebook provider
- publishing flow
- queue
- scheduler
- daily slots
- sequence
- manual override
- retry
- idempotency
- environment variables
- live verification requirements.

Jangan membuat duplicate documentation jika file sudah ada.

==================================================
NO DESTRUCTIVE REFACTOR
==================================================

Jika menemukan architecture lama yang tidak cocok:

jangan langsung hapus.

Gunakan existing architecture jika masih kompatibel.

Jika memang harus refactor:

1. identifikasi
2. implement replacement
3. migrasikan references
4. test
5. hapus hanya jika aman
6. pastikan tidak merusak feature existing.

==================================================
QUALITY GATE
==================================================

Sebelum selesai:

1. typecheck
2. lint
3. unit tests
4. integration tests
5. regression tests
6. build
7. inspect git diff
8. inspect git status
9. scan perubahan untuk secret
10. verify destination isolation
11. verify scheduler
12. verify queue
13. verify provider integration
14. verify documentation.

Jangan mematikan test hanya karena test gagal.

Jika ada test gagal:

perbaiki root cause.

==================================================
GIT
==================================================

Setelah semua selesai:

git status

Pastikan hanya perubahan yang relevan.

Review:

git diff

Pastikan tidak ada:

- .env
- token
- API key
- password
- access token
- secret
- credential dump.

Kemudian commit.

Gunakan commit message yang jelas, misalnya:

feat: harden facebook publishing and destination workspaces

Jika scope perubahan lebih cocok, gunakan commit message yang sesuai.

Jangan membuat commit kosong.

Jangan force push.

Push langsung ke branch project yang sedang digunakan.

Setelah push:

verifikasi remote.

==================================================
HASIL AKHIR WAJIB
==================================================

Di akhir laporan tampilkan:

FACEBOOK PROVIDER:
PASS / PARTIAL / NEEDS CONFIGURATION

DESTINATION WORKSPACE:
PASS

DESTINATION ISOLATION:
PASS

MEDIA PIPELINE:
PASS

DOWNLOADER:
PASS

PUBLISH:
PASS / NEEDS LIVE VERIFICATION

QUEUE:
PASS

WORKER:
PASS

SCHEDULER:
PASS

DAILY SLOT:
PASS

SEQUENCE:
PASS

RETRY:
PASS

IDEMPOTENCY:
PASS

HISTORY:
PASS

REGRESSION:
PASS

TYPECHECK:
PASS

LINT:
PASS

TEST:
PASS (<jumlah> tests)

BUILD:
PASS

GIT STATUS:
CLEAN

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS

REMOTE VERIFIED:
YES

FACEBOOK LIVE VERIFICATION:
PASS / NOT RUN (credentials unavailable)

==================================================
STOP CONDITION
==================================================

Setelah:

- implementation selesai
- test selesai
- build PASS
- git clean
- commit berhasil
- push berhasil
- remote verified

STOP.

Jangan melanjutkan ke YouTube, Instagram, TikTok, atau Phase berikutnya.

Jangan meminta konfirmasi kredit.

Jangan meminta saya mengulang prompt.

Kerjakan langsung sampai batas STOP CONDITION di atas.
````
# implementasi Phase 1: Core Foundation + Destination Workspace Architecture
```
Lanjutkan project Content Pilot dari hasil Phase 0 yang sudah selesai.

Jangan mengulang audit dari awal kecuali ada bagian yang benar-benar diperlukan untuk implementasi. Gunakan architecture, documentation, roadmap, dan keputusan yang sudah dibuat sebelumnya sebagai sumber kebenaran.

SEKARANG MULAI IMPLEMENTASI PHASE 1.

==================================================
PHASE 1 — CORE FOUNDATION & DESTINATION WORKSPACE
==================================================

Tujuan Phase 1:

Membangun fondasi architecture Content Pilot yang benar-benar mendukung:

- multi Facebook account
- multi Page
- multi platform account
- multi destination
- destination workspace isolation
- media/storage scoped ke destination
- manual upload
- downloader ingestion
- shared media pipeline
- publish foundation
- queue foundation
- scheduler foundation
- history foundation

Tetapi JANGAN implementasikan Facebook publishing live pada phase ini.

JANGAN membuat fake Facebook success.

JANGAN membuat fake API response.

JANGAN menggunakan credential Facebook palsu.

Facebook provider boleh dibuat sebagai architecture/interface/foundation jika diperlukan, tetapi publishing nyata masuk Phase Facebook Provider & Publishing.

==================================================
1. GUNAKAN ARCHITECTURE YANG SUDAH DISETUJUI
==================================================

Core system harus platform-independent.

Jangan membuat architecture:

Facebook
└── Page

sebagai root system.

Gunakan:

User
└── PlatformConnection
    └── Destination
        └── Workspace

Contoh:

User A
├── Facebook Account 1
│   ├── Page A
│   │   └── Workspace A
│   ├── Page B
│   │   └── Workspace B
│   └── Page C
│       └── Workspace C
│
└── YouTube Account 1
    ├── Channel A
    │   └── Workspace D
    └── Channel B
        └── Workspace E

Jangan membuat Facebook Page sebagai entity khusus yang menjadi dependency core.

Gunakan entity generik:

Destination.

Facebook Page hanyalah:

platform = facebook
destination_type = page

YouTube Channel nantinya:

platform = youtube
destination_type = channel

Instagram/TikTok dan platform lain mengikuti konsep yang sama.

==================================================
2. DESTINATION WORKSPACE
==================================================

Setiap Destination harus mempunyai workspace context sendiri.

Contoh:

Page A Workspace

- Dashboard
- Downloader
- Storage
- Publish
- Queue
- Schedule
- History
- Settings

Page B Workspace

- Dashboard
- Downloader
- Storage
- Publish
- Queue
- Schedule
- History
- Settings

Perhatikan:

Workspace tidak harus menjadi microservice.

Jangan membuat service terpisah hanya untuk workspace.

Workspace adalah logical isolation/context berdasarkan:

destination_id

Semua operasi harus menggunakan destination scope.

Contoh:

GET /api/destinations/:destinationId/media

GET /api/destinations/:destinationId/jobs

GET /api/destinations/:destinationId/history

GET /api/destinations/:destinationId/schedule

Jika route existing mempunyai struktur berbeda, gunakan pola yang paling konsisten dengan architecture project.

==================================================
3. DESTINATION ISOLATION
==================================================

Ini sangat penting.

Data Page A tidak boleh muncul di Page B.

Contoh:

Page A:
media A1
media A2
media A3

Page B:
media B1
media B2

Ketika user membuka Page A:

Storage hanya:

A1
A2
A3

Tidak boleh:

B1
B2

Hal yang sama berlaku untuk:

- downloader
- media
- storage
- publish
- queue
- schedule
- history
- settings
- auto publishing configuration

Semua harus destination-scoped.

Jangan hanya melakukan filter di frontend.

Isolation WAJIB terjadi di backend/service/database query.

Frontend filtering saja TIDAK dianggap security.

==================================================
4. DESTINATION SWITCHER
==================================================

Buat fondasi UI untuk memilih workspace/destination.

Contoh:

[ Facebook Account ]
        ↓
[ Page A ▼ ]

atau:

Workspace:
[ Yourreels ▼ ]

Ketika destination diganti:

- dashboard berubah
- media berubah
- downloader context berubah
- publish context berubah
- queue berubah
- schedule berubah
- history berubah

Jangan reload data dari destination sebelumnya.

Destination context harus jelas terlihat agar user tidak salah publish.

Contoh header:

Facebook
Page: Yourreels

atau:

Workspace: Yourreels

Jangan menggunakan Page ID sebagai label utama kepada user.

Gunakan:

destination.name

dengan ID sebagai metadata internal.

==================================================
5. MULTI ACCOUNT
==================================================

Database/model harus mendukung banyak PlatformConnection.

Contoh:

User
├── Facebook connection 1
├── Facebook connection 2
├── YouTube connection 1
└── TikTok connection 1

Jangan membuat:

user.facebook_access_token

sebagai satu-satunya model.

Gunakan konsep:

PlatformConnection

Minimal logical field:

id
user_id
platform_id / platform
account_external_id
account_name
status
metadata
created_at
updated_at

Credential/token jangan disimpan plaintext jika architecture project menyediakan secure storage/encryption.

Jika encryption belum diimplementasikan pada Phase 1, buat abstraction/interface yang memungkinkan secure credential storage pada Phase berikutnya.

Jangan commit secret.

==================================================
6. DESTINATION MODEL
==================================================

Destination harus generik.

Minimal logical data:

id
platform_connection_id
platform
destination_type
external_id
name
status
metadata
created_at
updated_at

Contoh:

id: internal UUID
platform: facebook
destination_type: page
external_id: Facebook Page ID
name: Yourreels

YouTube:

platform: youtube
destination_type: channel

Jangan membuat tabel:

facebook_pages

sebagai satu-satunya destination model jika tidak diperlukan.

Jika existing database sudah mempunyai Facebook-specific table, jangan langsung menghapusnya.

Buat migration strategy yang aman.

==================================================
7. MEDIA FOUNDATION
==================================================

Media adalah entity global tetapi penggunaan media harus dapat di-scope ke destination.

Penting:

Jangan membuat media model seperti:

FacebookVideo

Gunakan:

Media

Minimal:

id
filename
mime_type
size
duration
width
height
storage_key
thumbnail_key
source_type
source_url / source_reference jika tersedia
status
metadata
created_at
updated_at

source_type minimal:

manual
downloader

Boleh ditambah:

import
api
other

jika diperlukan.

==================================================
8. MANUAL UPLOAD
==================================================

Manual upload HARUS menggunakan shared media pipeline.

Flow:

User
→ pilih Destination Workspace
→ Upload
→ Media
→ validation
→ storage
→ READY
→ tersedia di Storage

Jangan membuat manual upload yang hanya menyimpan file sementara lalu hilang.

File harus masuk ke storage abstraction.

Jangan hardcode filesystem sebagai architecture final jika project menggunakan S3-compatible storage abstraction.

Jika existing storage sudah ada, gunakan dan perbaiki secara minimal.

==================================================
9. DOWNLOADER INGESTION
==================================================

Downloader juga harus menggunakan pipeline yang sama.

Flow:

Downloader
→ pilih/berada di Destination Workspace
→ download/import video
→ create Media
→ source_type = downloader
→ storage
→ validation
→ READY
→ masuk Storage destination tersebut

Downloader tidak boleh membuat entity video khusus yang terpisah dari Media.

Downloader dan manual upload harus menghasilkan Media dengan model yang sama.

Contoh:

Manual:

Media #001
source_type = manual

Downloader:

Media #002
source_type = downloader

Keduanya dapat digunakan oleh Publish/Queue/Scheduler.

==================================================
10. SOURCE TRACKING
==================================================

Untuk downloader, simpan metadata source bila tersedia.

Contoh:

source_type = downloader
source_url = ...
source_reference = ...
source_metadata = ...

Tetapi jangan menyimpan informasi yang tidak tersedia.

Jangan mengarang source ID.

Jika downloader sudah mempunyai identifier sendiri, gunakan identifier tersebut.

Tujuan:

User dapat mengetahui:

Video ini berasal dari manual upload

atau:

Video ini berasal dari downloader

==================================================
11. MEDIA STATUS
==================================================

Media harus memiliki lifecycle yang jelas.

Minimal:

uploading
processing
ready
failed
deleted

Jangan memasukkan media ke publishing queue sebelum:

status = ready

Jika invalid:

status = failed

Error harus dapat dilihat.

Contoh:

Unsupported video format

atau:

File too large

Jangan menampilkan READY jika validation gagal.

==================================================
12. MEDIA LIBRARY
==================================================

Buat foundation Storage/Media Library berdasarkan destination workspace.

Contoh:

Page A
Storage

[video1.mp4]
[video2.mp4]
[video3.mp4]

Page B
Storage

[video4.mp4]
[video5.mp4]

Jangan mencampur.

UI minimal harus dapat:

- list media
- preview video jika existing component mendukung
- filename
- source
- status
- created time
- size
- duration jika tersedia
- destination context

Tidak perlu membuat media editor kompleks.

==================================================
13. PUBLISH FOUNDATION
==================================================

Buat abstraction untuk publishing.

Core harus mengetahui:

PublishingJob

tetapi tidak mengetahui detail API Facebook.

Contoh:

PublishingJob

id
destination_id
media_id
provider
status
scheduled_at
schedule_source
sequence_number
caption
metadata
created_at
updated_at

Status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jangan membuat status palsu published.

Phase ini hanya foundation.

==================================================
14. ONE JOB PER DESTINATION
==================================================

Jika satu media nanti dipublish ke beberapa destination:

Media A

→ Page A = Job 001
→ Page B = Job 002
→ YouTube Channel A = Job 003

Jangan membuat satu job global yang mempunyai banyak destination.

Setiap destination memiliki job sendiri.

Dengan demikian:

Page A = published

Page B = failed

YouTube = queued

dapat terjadi secara bersamaan.

==================================================
15. SEQUENCE NUMBER
==================================================

Karena sistem nantinya memiliki automatic publishing, siapkan foundation untuk sequence.

Sequence tidak boleh menggunakan filename.

Jangan reset sequence setiap hari.

Contoh:

Hari 1:

Video 1
Video 2
Video 3

Hari 2:

Video 4
Video 5

Bukan:

Hari 2:
Video 1
Video 2

Sequence harus stabil.

Jika sebuah job gagal:

sequence yang sudah diberikan jangan dipakai ulang sembarangan.

Jika sequence_number belum diperlukan pada tahap tertentu, siapkan schema/model yang aman tanpa memaksakan implementasi scheduler penuh.

==================================================
16. DAILY SLOT FOUNDATION
==================================================

JANGAN implementasikan seluruh Auto Publishing Scheduler pada Phase 1.

Tetapi architecture harus siap.

Nantinya setiap Destination mempunyai konfigurasi:

SchedulingSettings

destination_id
enabled
timezone
max_videos_per_day
daily_slots
created_at
updated_at

Contoh:

enabled = true
timezone = Asia/Jakarta
max_videos_per_day = 4

slots:

08:00
11:00
14:00
17:00

Konfigurasi ini HARUS per Destination.

Page A:

4 video/day

Page B:

2 video/day

Page C:

6 video/day

Tidak boleh satu konfigurasi global.

==================================================
17. FUTURE AUTO SCHEDULING RULE
==================================================

Dokumentasikan aturan berikut tetapi jangan mengimplementasikan seluruh scheduler sekarang.

Jika:

max videos/day = 4

slot:

08:00
11:00
14:00
17:00

Hari pertama hanya ada 3 video:

08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Kemudian hari berikutnya downloader menerima video baru.

Video baru menjadi sequence berikutnya:

Video 4

dan ditempatkan pada slot tersedia berikutnya.

Jangan kembali menjadi Video 1.

Jika hari pertama penuh:

Video 1 → 08:00
Video 2 → 11:00
Video 3 → 14:00
Video 4 → 17:00

Downloader berikutnya:

Video 5 → hari kedua 08:00

Jika hari pertama hanya 3 video:

Video 4 tetap menjadi video berikutnya pada hari berikutnya.

Sequence tidak reset.

==================================================
18. MANUAL SCHEDULE OVERRIDE
==================================================

Architecture harus memungkinkan user memilih jadwal manual untuk video tertentu.

Contoh:

Auto schedule:

Video 4 → besok 08:00

User mengubah:

Video 4 → besok 20:00

Maka job:

schedule_source = manual

Jangan biarkan auto scheduler menimpa jadwal manual tanpa aturan eksplisit.

==================================================
19. QUEUE FOUNDATION
==================================================

Queue harus menerima PublishingJob.

Core:

PublishingJob
→ Queue
→ Worker
→ Provider

Worker tidak boleh mempunyai:

if facebook ...

yang menjadi architecture utama.

Gunakan provider registry.

Contoh konsep:

providerRegistry.get(job.provider)

lalu:

provider.publish(job)

Jangan implementasikan Facebook API nyata pada phase ini.

==================================================
20. PROVIDER INTERFACE
==================================================

Buat interface/provider contract yang cukup untuk future implementation.

Contoh konsep:

PlatformProvider

- getCapabilities()
- connect()
- disconnect()
- getDestinations()
- validateMedia()
- publish()
- getStatus()

Jangan menganggap semua method wajib digunakan semua platform.

Gunakan capability-based architecture.

Provider Facebook nanti dapat:

video
reels
photo
post

Provider YouTube nanti:

video
shorts

Provider TikTok:

video

Capability harus dapat diperluas.

==================================================
21. HISTORY FOUNDATION
==================================================

History harus destination-scoped.

Contoh:

Page A
History:

Video 1 → published
Video 2 → failed

Page B:

Video 3 → published

Jangan menampilkan history Page B ketika user berada di Page A.

PublishingAttempt nantinya menyimpan:

id
publishing_job_id
attempt_number
status
error_code
error_message
started_at
finished_at
provider_metadata jika aman

==================================================
22. AUDIT LOG
==================================================

Siapkan foundation AuditLog.

Contoh event:

media.uploaded
media.downloaded
destination.created
destination.updated
publishing_job.created
publishing_job.cancelled
schedule.created

Jangan menyimpan access token atau secret ke audit log.

==================================================
23. API STRUCTURE
==================================================

API harus terorganisasi berdasarkan domain.

Contoh konsep:

/api/accounts
/api/platforms
/api/destinations
/api/destinations/:destinationId/media
/api/destinations/:destinationId/downloader
/api/destinations/:destinationId/publish
/api/destinations/:destinationId/queue
/api/destinations/:destinationId/schedule
/api/destinations/:destinationId/history

Gunakan struktur yang sesuai dengan framework existing.

Jangan membuat route duplicate.

Jika existing API sudah mempunyai pola yang baik, pertahankan pola tersebut.

==================================================
24. FRONTEND STRUCTURE
==================================================

UI harus mempunyai destination context.

Contoh:

/dashboard
/destinations
/destinations/[destinationId]
/destinations/[destinationId]/downloader
/destinations/[destinationId]/storage
/destinations/[destinationId]/publish
/destinations/[destinationId]/queue
/destinations/[destinationId]/schedule
/destinations/[destinationId]/history

Tidak harus persis seperti ini jika routing architecture existing berbeda.

Yang penting:

destinationId menjadi context.

Jangan membuat:

/facebook/page-a
/facebook/page-b

sebagai architecture utama.

Gunakan destination abstraction.

==================================================
25. WORKSPACE NAVIGATION
==================================================

Di workspace destination, sediakan navigation:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History
Settings

Account/platform management tetap berada di level global:

Accounts
Platforms
Destinations

Contoh:

Global:

Accounts
Platforms
Destinations

Workspace:

Page A
├── Dashboard
├── Downloader
├── Storage
├── Publish
├── Queue
├── Schedule
├── History
└── Settings

==================================================
26. MOBILE UI
==================================================

Pastikan workspace dapat digunakan melalui mobile.

Navigation jangan terlalu lebar.

Destination switcher harus tetap mudah digunakan.

Downloader/upload harus nyaman dari mobile.

Storage list harus responsive.

Jangan membuat desktop-only layout.

==================================================
27. DATABASE MIGRATION
==================================================

Sebelum migration:

1. inspect existing schema
2. inspect existing migration system
3. jangan membuat migration duplicate
4. jangan menghapus data existing tanpa alasan
5. jangan melakukan destructive migration

Jika existing schema sudah mempunyai konsep yang dapat digunakan:

reuse.

Jika perlu perubahan:

buat migration incremental.

Setelah migration:

- run migration
- test schema
- test existing tests
- test new domain tests

==================================================
28. BACKWARD COMPATIBILITY
==================================================

Jika project existing sudah memiliki:

upload
downloader
media
queue
worker
scheduler

Jangan menghapus fitur tersebut.

Refactor secara bertahap agar masuk ke architecture baru.

Target:

Existing functionality tetap PASS.

Kemudian:

destination scoping ditambahkan.

Jangan membuat ulang seluruh sistem dari nol jika functionality existing masih bisa dipakai.

==================================================
29. TESTING
==================================================

Tambahkan test untuk destination isolation.

Minimal test:

Test 1:

Create Page A.

Create Page B.

Upload media ke Page A.

Pastikan Page B tidak melihat media tersebut.

Test 2:

Downloader Page A menghasilkan Media destination A.

Pastikan destination B tidak mendapat media tersebut.

Test 3:

Create publishing job Page A.

Pastikan job tidak muncul pada Page B.

Test 4:

History Page A hanya berisi job Page A.

Test 5:

SchedulingSettings Page A tidak mempengaruhi Page B.

Test 6:

Same Media dapat mempunyai dua PublishingJob untuk dua Destination.

Test 7:

Sequence number tidak reset berdasarkan tanggal.

Test 8:

Manual upload dan downloader menghasilkan Media model yang sama.

Test 9:

Media invalid tidak masuk READY.

Test 10:

Unauthorized destination access harus ditolak.

Security test WAJIB dilakukan di backend.

==================================================
30. SECURITY
==================================================

Pastikan:

- destination ownership diperiksa backend
- user A tidak dapat mengakses destination user B
- destination ID tidak boleh dianggap sebagai authorization
- API melakukan ownership check
- upload validation aktif
- MIME type validation
- file size limit
- path traversal protection
- secret tidak masuk Git
- token tidak masuk logs
- token tidak masuk error response
- audit log tidak mengandung credential

Jika ada vulnerability existing yang ditemukan:

perbaiki jika berkaitan langsung dengan Phase 1.

Jangan membuat refactor security besar yang tidak berkaitan tanpa melaporkan.

==================================================
31. DOCUMENTATION
==================================================

Update documentation sesuai implementasi sebenarnya.

Update:

docs/ARCHITECTURE.md
docs/DATABASE.md
docs/UI_DESIGN.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md

Tambahkan bagian:

Destination Workspace Architecture

Jelaskan:

User
→ PlatformConnection
→ Destination
→ Workspace

Jelaskan juga:

Downloader
→ Media
→ Storage
→ READY
→ PublishingJob

Dan:

Media
→ Job A
→ Job B
→ Job C

untuk multi-destination publishing.

Dokumentasi harus sesuai source code.

Jangan menulis fitur sebagai implemented jika belum benar-benar implemented.

==================================================
32. JANGAN IMPLEMENTASI DULU
==================================================

Jangan implementasi:

- Facebook OAuth live
- Facebook Page discovery live
- Facebook Reels API live
- YouTube OAuth
- Instagram API
- TikTok API
- production auto publishing
- fake publishing
- fake published status

Phase 1 hanya fondasi.

==================================================
33. GIT
==================================================

Setelah implementasi selesai:

1. git status
2. inspect git diff
3. pastikan tidak ada secret
4. run typecheck
5. run lint
6. run test
7. run build
8. run migration check jika ada database
9. periksa documentation
10. commit perubahan
11. push ke branch aktif
12. verifikasi remote

Jangan force push.

Jangan commit secret.

Jangan membuat empty commit.

Gunakan commit message yang jelas:

feat: implement destination workspace foundation

Jika commit message yang lebih tepat diperlukan, gunakan yang sesuai perubahan sebenarnya.

==================================================
34. JANGAN BERTANYA HAL YANG TIDAK PERLU
==================================================

Jangan berhenti hanya karena tidak ada kredit Kiro.

Jangan meminta saya mengonfirmasi setiap langkah kecil.

Jalankan pekerjaan berdasarkan specification ini.

Jika ada masalah teknis:

- diagnosis
- perbaiki
- test
- lanjutkan

Jika ada keputusan architecture yang benar-benar tidak dapat ditentukan dari repository:

pilih solusi paling aman dan konsisten dengan architecture yang sudah disepakati, lalu dokumentasikan keputusan tersebut.

Jangan membuat fake implementation hanya supaya test terlihat hijau.

==================================================
35. FINAL VERIFICATION
==================================================

Sebelum berhenti, pastikan:

[ ] Multi-account model siap
[ ] Multi-destination model siap
[ ] Destination workspace siap
[ ] Destination isolation backend siap
[ ] Destination switcher siap
[ ] Manual upload menggunakan Media pipeline
[ ] Downloader menggunakan Media pipeline
[ ] Storage destination scoped
[ ] Media READY state jelas
[ ] PublishingJob foundation siap
[ ] One job per destination
[ ] Queue foundation siap
[ ] Scheduler foundation siap
[ ] Daily slot configuration schema/foundation siap
[ ] Sequence tidak reset harian
[ ] Manual schedule override foundation siap
[ ] History destination scoped
[ ] Provider abstraction siap
[ ] Facebook tidak di-hardcode ke core
[ ] Database migration aman
[ ] Tests destination isolation PASS
[ ] Typecheck PASS
[ ] Lint PASS
[ ] Test PASS
[ ] Build PASS
[ ] Documentation updated
[ ] Git clean
[ ] Commit berhasil
[ ] Push berhasil
[ ] Remote verified

==================================================
FINAL REPORT
==================================================

Tampilkan laporan ringkas tetapi lengkap:

PHASE 1 STATUS:
COMPLETE / INCOMPLETE

IMPLEMENTED:
- ...

DATABASE:
- ...

API:
- ...

UI:
- ...

DESTINATION ISOLATION:
PASS / FAIL

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

MEDIA PIPELINE:
PASS / FAIL

PUBLISHING FOUNDATION:
PASS / FAIL

QUEUE FOUNDATION:
PASS / FAIL

SCHEDULER FOUNDATION:
PASS / FAIL

TEST:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

NEXT RECOMMENDED PHASE:
Phase 2 — Authentication & Account/Destination Management

STOP setelah laporan.

Jangan langsung mengerjakan Phase 2.

```
# Prompt 01 versi terbaru
```
# Prompt 01 — Continue & Correct Repository Audit

Kita lanjutkan Prompt 01.

Saya sudah meninjau hasil sebelumnya dan ada masalah penting:

Repository saat ini masih berisi project lama berbasis Python/NiceGUI dan platform sosial yang berbeda. Project tersebut BUKAN arsitektur final untuk project baru Content Pilot yang sedang kita bangun.

Karena itu, jangan menganggap struktur lama sebagai arsitektur final.

Tujuan kita sekarang adalah menyelesaikan Phase 0 dengan benar sebelum coding fitur apa pun.

## PROJECT BARU

Nama project:

Content Pilot

Tujuan:

Membangun web platform untuk mengelola dan melakukan automatic content publishing ke berbagai platform sosial.

Platform pertama yang akan diimplementasikan adalah Facebook.

Namun arsitektur HARUS siap untuk:

- Facebook
- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn
- platform lain yang nantinya memiliki API publishing resmi yang sesuai

Facebook adalah provider pertama, bukan core system.

## ATURAN UTAMA

Jangan mulai implementation fitur publishing.

Jangan membuat Facebook uploader.

Jangan membuat OAuth Facebook terlebih dahulu.

Jangan membuat queue production terlebih dahulu.

Jangan membuat dashboard production terlebih dahulu.

Selesaikan discovery, architecture, documentation, dan roadmap terlebih dahulu.

## REPOSITORY AUDIT

Audit repository yang benar-benar sedang digunakan.

Periksa:

- seluruh root directory
- seluruh source code
- package/dependency
- konfigurasi
- database
- frontend
- backend
- test
- Docker
- deployment
- existing UI
- existing documentation

Pisahkan hasil menjadi:

1. Existing project lama
2. Existing code yang dapat dipertahankan
3. Existing code yang tidak relevan
4. Existing documentation yang perlu dipertahankan
5. Documentation yang perlu diperbarui
6. Komponen yang harus dibuat untuk Content Pilot
7. Risiko migrasi/refactor

Jangan mengklaim architecture baru sudah ada jika file tersebut belum benar-benar dibuat di repository.

## JANGAN MENGHAPUS PROJECT LAMA SECARA SEMBARANGAN

Sebelum menghapus atau mengganti source code lama:

- identifikasi terlebih dahulu
- jelaskan apa yang tidak relevan
- tentukan apakah project baru memang akan menggantikan project lama
- dokumentasikan keputusan

Jangan melakukan destructive migration pada Phase 0.

## TARGET TECH STACK

Gunakan TypeScript full-stack sebagai kandidat utama.

Kandidat architecture:

Frontend:
Next.js

Backend/API:
Fastify atau NestJS

Worker:
BullMQ

Queue:
Redis

Database:
PostgreSQL

Object storage:
S3-compatible storage

Namun ini masih architecture proposal.

Jangan langsung install atau implementasikan semuanya sebelum architecture final disetujui.

Bandingkan Fastify vs NestJS berdasarkan kebutuhan project ini dan pilih yang paling tepat.

Pertimbangkan:

- maintainability
- modular provider architecture
- queue/worker
- OAuth
- API integration
- validation
- testing
- scalability
- developer experience

## CORE ARCHITECTURE

Core tidak boleh bergantung pada Facebook.

Core harus menangani konsep generik:

- User
- Platform
- PlatformConnection
- Destination
- Workspace
- Media
- Post
- PublishingJob
- PublishingAttempt
- Schedule
- Queue
- Scheduler
- History
- AuditLog
- Notification
- Storage

Platform-specific implementation harus berada di provider/module masing-masing.

Target konsep:

Core
→ Provider Registry
→ Platform Provider
→ Platform-specific implementation

Contoh:

Core
→ Facebook Provider
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

## PROVIDER SYSTEM

Desain provider abstraction yang benar-benar extensible.

Jangan memaksakan semua provider memiliki fitur identik.

Gunakan capability-based architecture.

Contoh capability:

- video
- reels
- photo
- text_post
- link_post
- short_video
- scheduling
- analytics

Provider harus dapat melaporkan capability yang memang didukung.

Jangan membuat capability berdasarkan asumsi.

Capability harus dapat berasal dari:

- kemampuan API
- implementation provider
- permission
- destination type

## MULTI ACCOUNT / MULTI DESTINATION

Sistem HARUS mendukung banyak account dan banyak destination sejak awal.

Contoh:

User
→ Facebook Account 1
→ Page A
→ Page B
→ Page C

User
→ Facebook Account 2
→ Page D
→ Page E

Dan nantinya:

User
→ YouTube Account 1
→ Channel A
→ Channel B

Jangan membuat database atau UI yang hanya mendukung satu Facebook Account atau satu Page.

## DESTINATION WORKSPACE / PAGE ISOLATION

Setiap Page/Channel/Destination harus memiliki workspace sendiri.

Contoh:

```text
Facebook Account
├── Page A
│   └── Workspace Page A
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
├── Page B
│   └── Workspace Page B
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
└── Page C
    └── Workspace Page C
        ├── Dashboard
        ├── Downloader
        ├── Storage
        ├── Publish
        ├── Queue
        ├── Schedule
        └── History

````
# Downloader/Storage/Publish/Queue/Schedule terpisah → auto daily slot → sequence tidak reset.
```
LANJUTKAN PROJECT CONTENT PILOT BERDASARKAN HASIL AUDIT DAN STRUKTUR YANG SUDAH DISEPAKATI.

JANGAN MENGUBAH PREMIS UTAMA PROJECT.

==================================================
TUJUAN UTAMA
==================================================

Content Pilot adalah platform content publishing multi-platform.

Facebook adalah provider pertama, tetapi CORE harus tetap platform-independent.

Arsitektur harus sejak awal mendukung:

- multiple Facebook accounts
- multiple Facebook Pages per account
- multiple YouTube accounts/channels
- multiple Instagram destinations
- multiple TikTok destinations
- platform lain di masa depan

Jangan membuat sistem hanya untuk satu Facebook account atau satu Page.

==================================================
KONSEP UTAMA: ACCOUNT → DESTINATION → WORKSPACE
==================================================

Struktur utama:

User
 ├── Facebook Account A
 │    ├── Page A
 │    │    └── Workspace Page A
 │    ├── Page B
 │    │    └── Workspace Page B
 │    └── Page C
 │         └── Workspace Page C
 │
 ├── Facebook Account B
 │    ├── Page D
 │    │    └── Workspace Page D
 │    └── Page E
 │         └── Workspace Page E
 │
 └── YouTube Account
      ├── Channel A
      │    └── Workspace Channel A
      └── Channel B
           └── Workspace Channel B

Destination adalah konsep generik.

Facebook Page, YouTube Channel, Instagram account, TikTok account, dan destination platform lain semuanya harus dapat menggunakan konsep Destination yang sama.

==================================================
DESTINATION WORKSPACE
==================================================

SETIAP DESTINATION MEMILIKI WORKSPACE SENDIRI.

Contoh:

Page A Workspace:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History
Settings

Page B Workspace:

Dashboard
Downloader
Storage
Publish
Queue
Schedule
History
Settings

Jangan membuat satu halaman global yang mencampurkan semua Page.

User harus selalu mengetahui workspace/destination yang sedang aktif.

UI harus menyediakan:

Destination / Workspace Switcher

Contoh:

[ Facebook Account A ]
    [ Page A ▼ ]

atau:

Current Workspace:
Facebook Page A

Ketika berpindah ke Page B:

Current Workspace:
Facebook Page B

Semua data yang tampil harus otomatis berubah mengikuti destination tersebut.

==================================================
DATA ISOLATION
==================================================

Semua operasi yang berkaitan dengan destination harus menggunakan destination_id.

Minimal:

Media
PublishingJob
PublishingAttempt
Schedule
Queue metadata
History
Auto-publish configuration
Downloader source
Publishing settings

harus dapat dilacak ke destination yang sesuai.

Downloader Page A:

Downloader
→ download video
→ Media destination_id = Page A
→ Storage Page A
→ Queue Page A
→ Schedule Page A
→ Publish Page A

Tidak boleh masuk ke Page B.

Downloader Page B:

Downloader
→ Media destination_id = Page B
→ Storage Page B
→ Queue Page B
→ Schedule Page B
→ Publish Page B

Tidak boleh tercampur.

CORE SERVICE tetap shared.

Tidak perlu membuat backend/service terpisah untuk setiap Page.

Gunakan logical isolation berdasarkan destination_id.

==================================================
MEDIA LIBRARY
==================================================

Media tetap merupakan entity generik.

Minimal:

Media
- id
- destination_id
- source_type
- source_id
- source_url jika tersedia
- filename
- mime_type
- size
- duration
- width
- height
- storage_key
- thumbnail
- metadata
- status
- created_at

source_type minimal:

manual
downloader
other

Media yang berasal dari Downloader harus tetap memiliki identifier/source metadata sehingga dapat diketahui asalnya.

Jangan menggunakan filename sebagai identifier utama.

==================================================
MANUAL UPLOAD
==================================================

Manual upload HARUS tetap tersedia.

Flow:

User membuka Workspace Page A
→ Publish / Upload
→ pilih file dari perangkat
→ upload
→ media pipeline
→ validation
→ storage
→ READY
→ dapat dipublish atau masuk auto scheduler.

Manual upload dan downloader HARUS menggunakan shared media pipeline.

Jangan membuat dua pipeline media yang berbeda.

==================================================
DOWNLOADER
==================================================

Downloader juga harus menjadi bagian dari Workspace.

Contoh:

Page A
→ Downloader
→ masukkan URL
→ download
→ media tersimpan
→ Media READY
→ otomatis masuk scheduling pipeline jika Auto Publish aktif.

Jika downloader menghasilkan beberapa video:

Video 1
Video 2
Video 3
Video 4

masing-masing harus mempunyai Media ID sendiri.

Urutan masuk harus dapat dilacak menggunakan created_at / sequence yang benar.

==================================================
AUTO PUBLISHING / DAILY SLOT
==================================================

Setiap Workspace/Destination memiliki pengaturan auto publishing sendiri.

Contoh:

Auto Publish:
ON

Maximum videos per day:
4

Timezone:
Asia/Jakarta

Daily Slots:

08:00
11:00
14:00
17:00

Pengaturan ini BUKAN global.

Page A dapat:

4 video/hari

Page B dapat:

2 video/hari

Page C dapat:

6 video/hari

==================================================
ATURAN SLOT
==================================================

Jika:

Maximum videos/day = 4

Slots:

08:00
11:00
14:00
17:00

dan downloader memasukkan:

Video 1
Video 2
Video 3
Video 4

maka:

Hari 1
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → Video 4

Jika downloader memasukkan Video 5 setelah empat slot hari pertama penuh:

Hari 2
08:00 → Video 5

Video 6:

11:00 → Video 6

dan seterusnya.

==================================================
JIKA HARI PERTAMA HANYA ADA 3 VIDEO
==================================================

Contoh:

Hari 1:

08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Jika tidak ada video ke-4 pada hari tersebut:

JANGAN membuat Video 4 secara dummy.

Slot 17:00 tetap kosong.

Jika besok downloader memasukkan Video 4:

Hari 2:

08:00 → Video 4

Bukan:

Hari 1:
17:00 → Video 4

Karena hari pertama sudah berlalu.

==================================================
SEQUENCE
==================================================

Sequence TIDAK RESET setiap hari.

Contoh:

Hari 1:

Video 1
Video 2
Video 3

Hari 2:

Video 4
Video 5
Video 6

Bukan:

Hari 2:
Video 1
Video 2
Video 3

Sequence harus tetap unik dan monoton.

Jangan mengubah nomor sequence media/job yang sudah diberikan.

Media ID, sequence number, dan PublishingJob ID adalah tiga konsep berbeda.

==================================================
BILA DOWNLOAD VIDEO SETELAH SLOT PENUH
==================================================

Contoh:

Maximum:
4 video/day

Hari 1 sudah:

Video 1
Video 2
Video 3
Video 4

Downloader berikutnya:

Video 5

Maka:

Hari 2
08:00 → Video 5

Downloader berikutnya:

Video 6

Hari 2
11:00 → Video 6

Downloader berikutnya:

Video 7

Hari 2
14:00 → Video 7

dan seterusnya.

Sistem harus mencari slot kosong paling awal di masa depan.

==================================================
BILA DOWNLOAD VIDEO BANYAK SEKALIGUS
==================================================

Jika user downloader:

Video 1
Video 2
Video 3
Video 4
Video 5
Video 6

dan konfigurasi:

4 video/day

maka:

Hari 1
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → Video 4

Hari 2
08:00 → Video 5
11:00 → Video 6

Urutan berdasarkan urutan masuk yang dapat dibuktikan oleh timestamp/sequence.

Jangan random.

==================================================
MANUAL SCHEDULE OVERRIDE
==================================================

Setiap video harus dapat diberikan schedule manual.

Contoh:

Video 10

Auto slot:
14:00

User mengubah:

20:30

Maka job menggunakan:

schedule_source = manual

dan scheduled_at = 20:30.

Manual override harus mengalahkan auto slot.

==================================================
PERUBAHAN KONFIGURASI
==================================================

Jika user mengubah:

Maximum videos/day
atau
daily slots
atau
timezone

JANGAN otomatis mengacak ulang job yang sudah:

published
processing
atau sudah final.

Job yang sudah final tidak boleh dipindahkan.

Job yang belum final dapat di-reschedule berdasarkan aturan yang jelas.

Jangan melakukan silent rescheduling.

Jika rescheduling dilakukan, simpan audit/history.

==================================================
PUBLISHING JOB
==================================================

Satu target destination = satu PublishingJob.

Contoh:

Media 100

→ Facebook Page A
PublishingJob A

→ Facebook Page B
PublishingJob B

→ YouTube Channel A
PublishingJob C

Status setiap job independen.

Contoh:

Page A:
published

Page B:
failed

YouTube:
queued

Jangan menjadikan satu global status sebagai pengganti status child job.

==================================================
QUEUE
==================================================

Queue tetap shared secara infrastructure, tetapi job harus memiliki destination_id.

Contoh:

Queue

Job 001
destination = Page A

Job 002
destination = Page B

Worker mengambil job:

→ membaca provider
→ membaca destination
→ menjalankan provider yang sesuai
→ memperbarui job.

Queue tidak boleh salah mengambil destination.

==================================================
SCHEDULER
==================================================

Scheduler harus membaca:

destination_id
timezone
daily_slots
max_videos_per_day
existing scheduled jobs
existing published jobs
manual overrides

Kemudian menentukan scheduled_at.

Scheduler harus menyimpan waktu aktual:

scheduled_at

Jangan hanya menyimpan:

day_number
slot_number

Contoh:

scheduled_at:
2026-08-27T08:00:00+07:00

Timezone harus diperhitungkan.

==================================================
DATABASE
==================================================

Model harus mendukung minimal:

User
Platform
PlatformConnection
Destination
Media
PublishingJob
PublishingAttempt
Schedule
AuditLog

Tambahkan entity konfigurasi jika diperlukan, misalnya:

DestinationSchedulingSettings

atau struktur equivalent yang paling cocok dengan database.

DestinationSchedulingSettings minimal:

destination_id
enabled
max_videos_per_day
timezone
daily_slots
created_at
updated_at

Jangan memaksakan nama tabel jika architecture existing memiliki convention berbeda.

==================================================
PLATFORM PROVIDER
==================================================

Core tidak boleh mengetahui detail Facebook API.

Gunakan provider abstraction.

Contoh:

Core
→ Provider Registry
→ Facebook Provider

Nanti:

Core
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

Provider harus memiliki capability masing-masing.

Contoh:

Facebook:
video
reels
photo
text_post
scheduling

Tetapi capability hanya boleh dinyatakan tersedia jika benar-benar didukung oleh implementation/API.

==================================================
FACEBOOK ACCOUNT
==================================================

Satu Facebook account dapat memiliki banyak Page.

Contoh:

Facebook Account 1

Page A
Page B
Page C

Semua Page harus dapat ditemukan melalui official Facebook/Meta API setelah authentication berhasil.

Setiap Page menjadi Destination tersendiri.

Jangan membuat:

facebook_page_id global tunggal.

Gunakan:

PlatformConnection
→ Destination[]

==================================================
STORAGE
==================================================

Storage juga harus terstruktur berdasarkan destination secara logical.

Contoh:

storage/
  destinations/
    page-A/
      media/
      thumbnails/
    page-B/
      media/
      thumbnails/

Implementasi storage fisik boleh berbeda jika menggunakan S3/MinIO/object storage.

Yang penting:

Media harus dapat dilacak dengan:

destination_id
storage_key

dan tidak tercampur secara logical.

==================================================
UI STRUCTURE
==================================================

Jangan membuat semua fitur menjadi satu halaman besar.

Gunakan struktur:

Accounts
    └── Facebook Account A
          ├── Page A
          ├── Page B
          └── Page C

Setelah memilih Page:

Page A Workspace

├── Dashboard
├── Downloader
├── Storage
├── Publish
├── Queue
├── Schedule
├── History
└── Settings

==================================================
WORKSPACE DASHBOARD
==================================================

Dashboard workspace menampilkan data Page yang sedang aktif.

Contoh:

Facebook Page A

Today's Schedule
08:00 Video 1
11:00 Video 2
14:00 Video 3
17:00 Empty

Queue
2 queued

Published Today
3

Failed
0

Storage
27 videos

Jangan menampilkan angka gabungan semua Page kecuali user memang membuka Global Dashboard.

==================================================
DOWNLOADER PAGE
==================================================

Downloader harus hanya bekerja untuk workspace aktif.

Header:

Downloader
Facebook Page A

Input:

URL

[ Download ]

Setelah berhasil:

Video
Source
Status
Media ID
Created
Scheduled At

Jika Auto Publish aktif:

Status:

Downloaded
→ Ready
→ Scheduled

Jika Auto Publish mati:

Downloaded
→ Ready

User dapat menjadwalkan manual.

==================================================
STORAGE PAGE
==================================================

Storage hanya menampilkan media milik destination aktif.

Filter:

All
Ready
Scheduled
Published
Failed

Search:

filename
source
media ID

Jangan menampilkan media Page lain kecuali user berpindah workspace.

==================================================
PUBLISH PAGE
==================================================

Publish page hanya menggunakan destination aktif.

Contoh:

Publishing to:

Facebook Page A

Media:
[select media]

Caption:
[...]

Schedule:
Publish Now
Schedule

Jika publish ke beberapa destination memang diperlukan, buat child PublishingJob untuk masing-masing destination secara eksplisit.

==================================================
SCHEDULE PAGE
==================================================

Tampilkan:

Calendar/List

Tanggal
Jam
Video
Status
Source

Contoh:

27 Aug
08:00
Video 1
Scheduled

27 Aug
11:00
Video 2
Scheduled

27 Aug
14:00
Video 3
Scheduled

27 Aug
17:00
Empty

28 Aug
08:00
Video 4
Scheduled

==================================================
QUEUE PAGE
==================================================

Hanya menampilkan queue workspace aktif.

Filter:

Queued
Processing
Retrying
Failed
Completed
Cancelled

Setiap job menampilkan:

sequence
media
destination
scheduled_at
status
attempts
last_error

==================================================
HISTORY PAGE
==================================================

History hanya untuk destination aktif.

Tampilkan:

published
failed
cancelled
retry
publish attempts

Jangan mencampur history antar Page.

==================================================
GLOBAL DASHBOARD
==================================================

Global Dashboard tetap boleh tersedia.

Global Dashboard hanya merupakan overview.

Contoh:

Accounts
5

Destinations
12

Scheduled
27

Queue
8

Published Today
19

Tetapi ketika user masuk ke Workspace, seluruh data menjadi destination-scoped.

==================================================
SETTINGS
==================================================

Settings harus dibagi jelas:

Global Settings
Account Settings
Destination/Workspace Settings
Scheduling Settings
Storage Settings
Provider Settings

Pengaturan seperti:

max videos/day
timezone
daily slots
auto publishing

HARUS berada pada Destination/Workspace Settings.

==================================================
SECURITY
==================================================

Jangan pernah:

- commit access token
- commit refresh token
- commit META_APP_SECRET
- commit API key
- menampilkan secret di UI
- menyimpan secret plaintext jika tidak diperlukan

Gunakan environment/secure secret storage.

.env harus tetap ignored oleh Git.

==================================================
IMPLEMENTATION RULE
==================================================

SEBELUM CODING:

1. Audit architecture existing.
2. Pastikan schema existing.
3. Pastikan UI existing.
4. Pastikan queue existing.
5. Pastikan scheduler existing.
6. Pastikan downloader existing.
7. Pastikan media pipeline existing.

Jika komponen sudah ada dan PASS:

JANGAN dibuat ulang.

Gunakan dan perluas architecture existing.

Jika ada gap:

perbaiki gap tersebut secara minimal dan modular.

Jangan melakukan rewrite besar tanpa alasan.

==================================================
TESTING
==================================================

Tambahkan test untuk aturan penting:

1. Page A tidak melihat media Page B.
2. Downloader Page A membuat media destination_id Page A.
3. Downloader Page B membuat media destination_id Page B.
4. max_videos_per_day = 4.
5. Empat video masuk Hari 1.
6. Video kelima masuk Hari 2.
7. Jika Hari 1 hanya ada tiga video, slot keempat kosong.
8. Video berikutnya tetap masuk Hari 2.
9. Sequence tidak reset.
10. Download batch menghasilkan urutan deterministic.
11. Manual schedule override bekerja.
12. Published job tidak dipindahkan saat konfigurasi berubah.
13. Queue tidak mencampur destination.
14. History tidak mencampur destination.
15. Timezone bekerja benar.
16. Multi-destination publishing membuat child job terpisah.
17. Failed job tidak merusak job destination lain.
18. Downloader dan manual upload menggunakan shared media pipeline.

==================================================
JANGAN FAKE
==================================================

Jangan membuat:

fake Facebook success
fake OAuth success
fake publishing
fake Page discovery
fake scheduler success
fake queue success

Jika API/credential belum tersedia:

gunakan status yang jujur:

NOT CONFIGURED
NEEDS CONFIGURATION
NOT RUN
NEEDS VERIFICATION

Jangan mengubahnya menjadi PASS palsu.

==================================================
GIT
==================================================

Setelah perubahan selesai:

1. git status
2. inspect diff
3. pastikan tidak ada secret
4. typecheck
5. lint
6. test
7. build
8. commit
9. push ke branch aktif
10. verifikasi remote

Jangan force push.

Jangan commit secret.

Jangan membuat empty commit.

Jika semuanya berhasil:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

==================================================
HASIL YANG DIINGINKAN
==================================================

Saya ingin hasil akhir memiliki konsep:

ACCOUNT
↓
DESTINATION / PAGE
↓
WORKSPACE
↓
DOWNLOADER
↓
STORAGE
↓
MEDIA READY
↓
AUTO DAILY SLOT
↓
SCHEDULE
↓
QUEUE
↓
WORKER
↓
PUBLISH
↓
HISTORY

Dan setiap Destination berdiri sendiri secara logical.

Contoh:

Page A
Downloader A
Storage A
Schedule A
Queue A
Publish A
History A

Page B
Downloader B
Storage B
Schedule B
Queue B
Publish B
History B

Tetapi seluruhnya tetap menggunakan CORE/backend/worker infrastructure yang sama.

==================================================
STOP CONDITION
==================================================

Jangan mengarang fitur yang belum tersedia.

Jangan menghapus fitur yang sudah PASS.

Jangan membuat duplicate architecture.

Jangan membuat semua Page menjadi satu workspace.

Jangan membuat daily sequence reset.

Jangan memindahkan job published.

Jangan mencampur media antar destination.

Setelah implementation/verifikasi selesai, tampilkan laporan singkat:

CHANGES
TESTS
BUILD
GIT STATUS
COMMIT
PUSH STATUS
REMOTE VERIFIED

Lalu STOP.


````
# 
```
# Prompt 01 — Continue & Correct Repository Audit

Kita lanjutkan Prompt 01.

Saya sudah meninjau hasil sebelumnya dan ada masalah penting:

Repository saat ini masih berisi project lama berbasis Python/NiceGUI dan platform sosial yang berbeda. Project tersebut BUKAN arsitektur final untuk project baru Content Pilot yang sedang kita bangun.

Karena itu, jangan menganggap struktur lama sebagai arsitektur final.

Tujuan kita sekarang adalah menyelesaikan Phase 0 dengan benar sebelum coding fitur apa pun.

## PROJECT BARU

Nama project:

Content Pilot

Tujuan:

Membangun web platform untuk mengelola dan melakukan automatic content publishing ke berbagai platform sosial.

Platform pertama yang akan diimplementasikan adalah Facebook.

Namun arsitektur HARUS siap untuk:

* Facebook
* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang nantinya memiliki API publishing resmi yang sesuai

Facebook adalah provider pertama, bukan core system.

## ATURAN UTAMA

Jangan mulai implementation fitur publishing.

Jangan membuat Facebook uploader.

Jangan membuat OAuth Facebook terlebih dahulu.

Jangan membuat queue production terlebih dahulu.

Jangan membuat dashboard production terlebih dahulu.

Selesaikan discovery, architecture, documentation, dan roadmap terlebih dahulu.

## REPOSITORY AUDIT

Audit repository yang benar-benar sedang digunakan.

Periksa:

* seluruh root directory
* seluruh source code
* package/dependency
* konfigurasi
* database
* frontend
* backend
* test
* Docker
* deployment
* existing UI
* existing documentation

Pisahkan hasil menjadi:

1. Existing project lama
2. Existing code yang dapat dipertahankan
3. Existing code yang tidak relevan
4. Existing documentation yang perlu dipertahankan
5. Documentation yang perlu diperbarui
6. Komponen yang harus dibuat untuk Content Pilot
7. Risiko migrasi/refactor

Jangan mengklaim architecture baru sudah ada jika file tersebut belum benar-benar dibuat di repository.

## JANGAN MENGHAPUS PROJECT LAMA SECARA SEMBARANGAN

Sebelum menghapus atau mengganti source code lama:

* identifikasi terlebih dahulu
* jelaskan apa yang tidak relevan
* tentukan apakah project baru memang akan menggantikan project lama
* dokumentasikan keputusan

Jangan melakukan destructive migration pada Phase 0.

## TARGET TECH STACK

Gunakan TypeScript full-stack sebagai kandidat utama.

Kandidat architecture:

Frontend:
Next.js

Backend/API:
Fastify atau NestJS

Worker:
BullMQ

Queue:
Redis

Database:
PostgreSQL

Object storage:
S3-compatible storage

Namun ini masih architecture proposal.

Jangan langsung install atau implementasikan semuanya sebelum architecture final disetujui.

Bandingkan Fastify vs NestJS berdasarkan kebutuhan project ini dan pilih yang paling tepat.

Pertimbangkan:

* maintainability
* modular provider architecture
* queue/worker
* OAuth
* API integration
* validation
* testing
* scalability
* developer experience

## CORE ARCHITECTURE

Core tidak boleh bergantung pada Facebook.

Core harus menangani konsep generik:

* User
* Platform
* PlatformConnection
* Destination
* Media
* Post
* PublishingJob
* PublishingAttempt
* Schedule
* Queue
* Scheduler
* History
* AuditLog
* Notification
* Storage

Platform-specific implementation harus berada di provider/module masing-masing.

Target konsep:

Core
→ Provider Registry
→ Platform Provider
→ Platform-specific implementation

Contoh:

Core
→ Facebook Provider
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

## PROVIDER SYSTEM

Desain provider abstraction yang benar-benar extensible.

Jangan memaksakan semua provider memiliki fitur identik.

Gunakan capability-based architecture.

Contoh capability:

* video
* reels
* photo
* text_post
* link_post
* short_video
* scheduling
* analytics

Provider harus dapat melaporkan capability yang memang didukung.

Jangan membuat capability berdasarkan asumsi.

Capability harus dapat berasal dari:

* kemampuan API
* implementation provider
* permission
* destination type

## FACEBOOK

Facebook adalah provider pertama.

Tetapi sebelum implementation, lakukan research resmi.

Research:

* authentication
* OAuth
* Page connection
* Page discovery
* destination model
* video publishing
* Reels publishing
* photo publishing
* post publishing
* scheduling
* status checking
* error handling
* rate limits
* permissions
* app review requirements
* token expiration
* token refresh/reconnect

Jika fitur belum dapat diverifikasi:

MARK AS UNKNOWN / NEEDS VERIFICATION

Jangan mengarang endpoint atau permission.

## API RESEARCH

Gunakan dokumentasi resmi sebagai sumber utama.

Prioritas:

1. Meta/Facebook official documentation
2. YouTube official documentation
3. Instagram official documentation
4. TikTok official documentation

Untuk platform lain, research dilakukan setelah provider utama stabil.

Buat capability matrix.

Contoh kolom:

Platform
Authentication
Destination
Video
Reels
Photo
Text Post
Scheduling
Analytics
Required Permissions
Upload Flow
Known Limitations
Verification Status

Jangan menulis fitur sebagai AVAILABLE jika belum diverifikasi.

## MULTI ACCOUNT

Dari awal sistem harus mendukung:

User
→ multiple PlatformConnection
→ multiple Destination

Contoh:

User
→ Facebook Account
→ Page A
→ Page B
→ Page C

Dan nanti:

User
→ YouTube Account
→ Channel A
→ Channel B

Jangan membuat database yang hanya mendukung satu account atau satu Page.

## DESTINATION WORKSPACE / PAGE ISOLATION

Setiap Destination harus memiliki **workspace sendiri** di UI dan secara logis terisolasi dari destination lain.

Contoh Facebook:

text
Facebook Account
├── Page A
│   └── Workspace Page A
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
├── Page B
│   └── Workspace Page B
│       ├── Dashboard
│       ├── Downloader
│       ├── Storage
│       ├── Publish
│       ├── Queue
│       ├── Schedule
│       └── History
│
└── Page C
    └── Workspace Page C
        ├── Dashboard
        ├── Downloader
        ├── Storage
        ├── Publish
        ├── Queue
        ├── Schedule
        └── History

Aturan:

1. Downloader yang dijalankan dari suatu Destination otomatis memasukkan media ke workspace/storage Destination tersebut.
2. Storage, queue, schedule, publish history, dan konfigurasi auto-publishing harus terikat ke `destination_id`.
3. Scheduler suatu Destination tidak boleh mengambil media dari Destination lain.
4. Queue suatu Destination tidak boleh memproses job milik Destination lain kecuali terdapat fitur multi-destination publishing yang secara eksplisit membuat child job terpisah.
5. Pengaturan `max_videos_per_day`, timezone, daily slots, dan aturan auto-publishing adalah konfigurasi per Destination/Workspace, bukan global.
6. Setiap workspace memiliki Page/Channel/Account context yang jelas sehingga pengguna tidak mudah salah mem-publish ke destination lain.
7. UI harus menyediakan Destination/Workspace switcher untuk berpindah Page/Channel dengan cepat.
8. Konsep ini harus generik: Facebook Page, YouTube Channel, Instagram destination, TikTok destination, dan destination platform lain dapat memiliki workspace sendiri tanpa membuat core architecture khusus Facebook.

Secara backend, workspace tidak harus menjadi service terpisah. Core tetap shared, tetapi seluruh data dan operasi harus scoped berdasarkan `destination_id`.

Logical flow:

text
Destination Workspace
        │
        ├── Downloader ──→ Media/Storage (destination scoped)
        ├── Publish ─────→ PublishingJob (destination scoped)
        ├── Schedule ────→ Scheduler (destination scoped)
        ├── Queue ───────→ Worker
        └── History ─────→ PublishingAttempt/History


Untuk kebutuhan future multi-destination publishing, satu media dapat tetap digunakan bersama, tetapi setiap target Destination harus mendapatkan PublishingJob terpisah dengan status, schedule, queue, dan history masing-masing.

## PUBLISHING JOB

Gunakan satu job per destination.

Contoh:

Video A

→ Facebook Page A = Job 001
→ Facebook Page B = Job 002
→ YouTube Channel A = Job 003

Setiap job memiliki status sendiri.

Contoh status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jika Facebook berhasil dan YouTube gagal:

Facebook = published
YouTube = failed

Bukan satu global job yang kehilangan detail platform.

## MEDIA ARCHITECTURE

Media harus platform-independent.

Video hanya disimpan sekali di media/storage layer.

Kemudian dapat digunakan oleh beberapa publishing job.

Jangan membuat:

FacebookVideo
YouTubeVideo
InstagramVideo

sebagai storage model utama.

Gunakan media generik lalu provider melakukan transformasi/validation sesuai capability platform.

## QUEUE

Queue harus platform-independent.

Core queue menerima PublishingJob.

Worker mengambil job.

Worker memanggil provider yang sesuai.

## AUTO PUBLISHING QUEUE & DAILY SLOT CONFIGURATION

Sistem publishing nantinya harus mendukung konfigurasi otomatis berdasarkan kuota video per hari dan slot waktu.

Contoh konfigurasi:
text
Maximum videos per day: 4
Slots:
08:00
11:00
14:00
17:00


Aturan utama:

1. Manual upload dan downloader harus masuk ke **shared media/publishing pipeline yang sama**.
2. Media dari downloader harus otomatis tersimpan sebagai Media dengan identifier/source metadata yang dapat dilacak.
3. Setelah media berstatus READY, jika auto scheduling aktif, sistem mencari **slot publikasi tersedia paling awal**.
4. Nomor urut video bersifat global/sequence dan **tidak reset setiap hari**.
5. Jika hari pertama hanya memiliki 3 video dari kapasitas 4:

text
Hari 1
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Jika hari tersebut sudah lewat dan video baru masuk, video baru menjadi Video 4 dan ditempatkan pada slot tersedia berikutnya di hari berikutnya. Jangan mengubahnya kembali menjadi Video 1.

6. Jika hari pertama penuh 4 video, video berikutnya otomatis masuk ke slot pertama hari kedua.
7. Jika beberapa video didownload sekaligus, masing-masing memperoleh slot berurutan berdasarkan urutan masuk/created time.
8. Jangan melakukan reset sequence ketika tanggal berganti.
9. Jangan menggunakan ulang nomor sequence media/post yang sudah pernah diberikan, termasuk ketika job gagal atau dibatalkan.
10. Pengaturan jumlah video per hari dan slot waktu harus dapat diubah tanpa merusak job yang sudah published.
11. Perubahan konfigurasi hanya boleh mempengaruhi job/schedule yang belum final/published sesuai aturan rescheduling yang jelas.
12. Setiap video boleh memiliki **manual schedule override** yang menggantikan slot otomatis untuk video tersebut.
13. Scheduler harus menyimpan scheduled_at yang aktual pada job, bukan hanya menyimpan nomor hari/slot.

Logical flow:

text
Manual Upload ─┐
               ├→ Media Library → READY → Auto Scheduler → Publishing Job → Queue → Worker
Downloader ────┘


Minimal konsep konfigurasi:

text
SchedulingSettings
- enabled
- max_videos_per_day
- timezone
- daily_slots[]


Minimal metadata queue/job:

text
Media
- id
- source_type (manual | downloader | other)
- source_id/source_url jika tersedia
- created_at

PublishingJob
- sequence_number
- media_id
- scheduled_at
- schedule_source (auto | manual)
- status
- destination_id


Sequence number, media ID, dan publishing job ID harus dibedakan. Jangan menggunakan filename sebagai identifier utama.

Arsitektur ini harus dirancang secara generik sehingga nantinya dapat dipakai untuk Facebook, YouTube, Instagram, TikTok, dan provider lain.

Contoh:

PublishingJob
→ provider = facebook
→ destination = Page A
→ publish()

Kemudian:

PublishingJob
→ provider = youtube
→ destination = Channel A
→ publish()

## RETRY

Bedakan temporary error dan permanent error.

Temporary:

* timeout
* network failure
* temporary API failure
* rate limit

Permanent:

* invalid token
* permission denied
* unsupported media
* invalid destination

Simpan:

* attempt count
* error code
* error message
* timestamp
* next retry
* provider response metadata jika aman

## SECURITY

Architecture harus memperhatikan:

* OAuth
* access token
* refresh token
* encryption
* secret management
* environment variables
* authorization
* user isolation
* file upload validation
* MIME validation
* file size limit
* path traversal
* SSRF
* rate limiting
* audit logs

Jangan commit secrets.

## UI DESIGN

Audit apakah repository saat ini sudah memiliki UI yang relevan untuk Content Pilot.

Jika UI lama tidak sesuai, jangan langsung menganggapnya sebagai UI final.

Dokumentasikan:

Current UI
→ reusable
→ needs redesign
→ obsolete

Untuk Content Pilot, target UI harus clean, modern, responsive, dan nyaman digunakan melalui desktop maupun mobile.

Konsep utama:

Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings

Tetapi jangan implementasikan semua halaman sekarang.

## UI DOCUMENTATION

Buat UI specification agar AI coding nantinya memiliki referensi yang konsisten.

Minimal dokumentasikan:

* layout
* navigation
* responsive behavior
* typography
* spacing
* buttons
* forms
* cards
* tables
* upload interface
* video preview
* publishing status
* queue
* scheduled posts
* account connection
* error state
* loading state
* empty state

Jangan membuat UI specification yang bertentangan dengan UI yang benar-benar dipilih untuk project.

## DOCUMENTATION

Buat documentation untuk project baru.

Gunakan struktur yang sederhana.

Minimal:

README.md

docs/ARCHITECTURE.md

docs/UI_DESIGN.md

docs/PLATFORM_MODULES.md

docs/DATABASE.md

docs/ROADMAP.md

docs/research/facebook-api.md

Jika dokumentasi dengan tujuan yang sama sudah ada, update file tersebut.

Jangan membuat duplicate documentation.

## DATABASE DESIGN

Buat ERD/logical model terlebih dahulu.

Minimal entity:

User
Platform
PlatformConnection
Destination
Media
Post
PublishingJob
PublishingAttempt
Schedule
AuditLog

Pastikan model mendukung:

1 user
→ many platform connections
→ many destinations
→ many media
→ many posts
→ many publishing jobs

Destination harus generik.

Facebook Page dan YouTube Channel harus dapat direpresentasikan sebagai destination tanpa mengubah core model.

## ROADMAP

Buat roadmap berdasarkan hasil audit aktual.

Phase 0:
Discovery, Audit, Research, Architecture, Documentation

Phase 1:
Core Foundation

Phase 2:
Authentication & Platform Connection

Phase 3:
Facebook Provider

Phase 4:
Facebook Publishing Capabilities

Phase 5:
Queue & Scheduler hardening

Phase 6:
YouTube Provider

Phase 7:
Instagram Provider

Phase 8:
TikTok Provider

Phase 9:
Advanced Automation

Jangan menganggap urutan ini final jika hasil audit menunjukkan urutan yang lebih baik.

Jelaskan alasan setiap phase.

## IMPORTANT

Pada tahap ini:

DO NOT implement publishing.

DO NOT implement Facebook OAuth.

DO NOT implement YouTube.

DO NOT implement TikTok.

DO NOT create fake API integrations.

DO NOT create fake success states.

DO NOT perform a massive refactor without reporting it.

DO NOT delete existing project files simply to make the repository look clean.

Fokus pada Phase 0.

## OUTPUT

Setelah selesai, berikan laporan:

Repository Status

Existing Stack

Existing Architecture

Existing UI

Existing Database

Existing Code

Reusable Components

Obsolete Components

Target Architecture

Provider Architecture

Database Model

UI Architecture

Facebook API Research

Platform Capability Matrix

Security Considerations

Migration Strategy

Roadmap

Recommended Phase 1

Risks

Open Questions

## REQUIRED FINAL STATUS

Tampilkan:

AUDIT STATUS: COMPLETE

ARCHITECTURE STATUS: READY / NEEDS REVISION

API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION

DOCUMENTATION STATUS: COMPLETE / INCOMPLETE

ROADMAP STATUS: READY

IMPLEMENTATION STATUS: NOT STARTED

NEXT RECOMMENDED STEP: ...

Jika architecture masih memiliki masalah, jangan menyatakan READY.

Tunjukkan masalahnya dan perbaiki dokumentasi terlebih dahulu.

STOP setelah Phase 0 selesai.

Jangan lanjut coding Phase 1 tanpa instruksi berikutnya.

## GIT COMMIT & PUSH

Setelah seluruh pekerjaan Phase 0 selesai dan dokumentasi sudah benar:

1. Periksa git status.
2. Pastikan tidak ada secret, token, API key, password, atau file sensitif yang akan di-commit.
3. Periksa diff seluruh perubahan.
4. Jalankan pemeriksaan yang aman dan relevan terhadap dokumentasi/struktur yang dibuat.
5. Commit seluruh perubahan Phase 0 dengan commit message yang jelas, misalnya:
   docs: complete content pilot phase 0 architecture audit
6. Push commit tersebut langsung ke branch yang sedang digunakan untuk project ini.
7. Setelah push berhasil, verifikasi bahwa commit sudah berada di remote repository.
8. Laporkan commit hash dan branch yang berhasil di-push.

Jangan melakukan push jika terdapat secret atau perubahan yang tidak berkaitan dengan Phase 0.
Jangan membuat commit kosong.
Jangan melakukan force push.

Jika push gagal karena authentication, permission, remote, atau masalah Git lainnya, jangan mengarang bahwa push berhasil. Laporkan error sebenarnya dan hentikan proses setelah pekerjaan lokal aman.

Setelah push berhasil, tampilkan:

GIT STATUS: CLEAN
COMMIT: <commit hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

Kemudian STOP.


````
# 
```

Lanjutkan project Content Pilot dari hasil Phase 0.

JANGAN melakukan implementation/coding dulu.
JANGAN mengubah source code.
JANGAN membuat database migration.
JANGAN membuat UI production.

Fokus hanya menyusun SPECIFICATION untuk:

AUTO PUBLISHING QUEUE + DAILY SLOT CONFIGURATION

Requirement yang sudah disepakati:

1. Admin dapat mengatur:
   - Auto publishing ON/OFF
   - Maximum video per hari
   - Timezone
   - Slot waktu upload harian

Contoh:
Maximum videos/day = 4

Slots:
08:00
11:00
14:00
17:00

2. Manual Upload dan Downloader HARUS menggunakan shared pipeline:

Manual Upload ─┐
               ├→ Media → READY → Scheduler → Publishing Job → Queue → Worker
Downloader ────┘

3. Setiap media dari downloader harus memiliki identifier sendiri dan metadata:
   - media_id
   - source_type
   - source_id/source_url jika tersedia
   - created_at

Jangan menggunakan filename sebagai identifier utama.

4. Sequence video bersifat GLOBAL dan tidak reset ketika tanggal berubah.

Contoh:

Hari 1:
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Jika besok downloader video baru:

Hari 2:
08:00 → Video 4

BUKAN kembali menjadi Video 1.

5. Jika hari pertama penuh:

Hari 1:
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → Video 4

Video berikutnya:

Hari 2:
08:00 → Video 5

6. Jika downloader memasukkan beberapa video sekaligus, urutkan berdasarkan created_at/ingestion order yang stabil.

Contoh:
Video 1
Video 2
Video 3
Video 4

Masing-masing mendapat slot berurutan.

7. Jika slot hari ini sudah penuh, otomatis cari slot kosong berikutnya pada hari berikutnya.

8. Jangan pernah mengulang sequence_number yang sudah pernah diberikan.

Sequence number harus berbeda dari:
- media_id
- publishing_job_id
- filename

9. Setiap video boleh memiliki manual schedule override.

Contoh:

Auto slot:
08:00

Tetapi user memilih:
Video 7 → 20:30

Maka:
schedule_source = manual

dan scheduled_at = 20:30.

10. Scheduler harus menyimpan waktu aktual:

scheduled_at

Jangan hanya menyimpan:
day_number
slot_number

11. Jika konfigurasi slot berubah:

Contoh:
Awalnya:
08:00
11:00
14:00
17:00

kemudian diubah menjadi:
09:00
13:00
18:00

Jangan mengubah job yang sudah:
- published
- processing
- uploading

Buat aturan jelas untuk job yang masih:
- draft
- queued
- scheduled

12. Jika video gagal publish:

Sequence number TIDAK boleh dipakai ulang.

13. Jika job dibatalkan:

Sequence number TIDAK boleh dipakai ulang.

14. Scheduler harus timezone-aware.

15. Hindari double scheduling ketika:
- worker restart
- server restart
- scheduler restart
- job diproses ulang

Gunakan idempotency/deduplication.

16. Buat state transition yang jelas:

Media:
uploaded
processing
ready
failed

PublishingJob:
draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

17. Buat logical data model minimal:

SchedulingSettings
- id
- enabled
- timezone
- max_videos_per_day

DailySlot
- id
- settings_id
- slot_time
- enabled
- order

Media
- id
- sequence_number jika memang ditempatkan di Media,
  atau jelaskan jika lebih tepat berada di PublishingJob
- source_type
- source_id/source_url
- created_at
- status

PublishingJob
- id
- media_id
- provider
- destination_id
- sequence_number
- scheduled_at
- schedule_source
- status
- created_at

Jika menurutmu sequence_number lebih tepat hanya berada di PublishingJob, jelaskan alasannya dan gunakan desain tersebut.

18. Buat contoh algoritma scheduling.

Gunakan contoh:

Settings:
4 video/day
08:00, 11:00, 14:00, 17:00

Input:
Video 1
Video 2
Video 3
Video 4
Video 5
Video 6

Tunjukkan hasil schedule.

Kemudian contoh kedua:

Hari pertama hanya ada:
Video 1
Video 2
Video 3

Hari kedua downloader:
Video 4
Video 5

Tunjukkan hasil schedule.

19. Jelaskan kasus khusus:

- slot sudah lewat
- semua slot hari ini penuh
- downloader memasukkan 10 video sekaligus
- video gagal
- video dibatalkan
- server restart
- timezone berubah
- admin mengubah jumlah slot
- admin mengubah max videos/day
- manual override
- duplicate downloader event

20. Buat acceptance criteria yang jelas sehingga nanti implementation dapat dites.

21. Jangan membuat fake implementation.

22. Jangan mengubah code.

23. Jangan melakukan migration.

24. Jangan melakukan commit/push karena tahap ini hanya specification.

OUTPUT:

1. Auto Publishing Architecture
2. Scheduling Data Model
3. Sequence Number Strategy
4. Slot Allocation Algorithm
5. Queue Interaction
6. State Transition
7. Rescheduling Rules
8. Edge Cases
9. Idempotency Strategy
10. Acceptance Criteria
11. Implementation Plan untuk phase berikutnya

Setelah specification selesai:

STOP.

Tampilkan:

DAILY SLOT SPEC: COMPLETE
CODE CHANGES: NONE
DATABASE CHANGES: NONE
IMPLEMENTATION STATUS: NOT STARTED
NEXT STEP: IMPLEMENT DAILY SLOT SYSTEM
````
# 
```

Lanjutkan dari DAILY SLOT SPEC yang sudah COMPLETE.

JANGAN mengulang audit.
JANGAN membuat specification baru.
JANGAN bertanya untuk keputusan kecil yang sebenarnya sudah bisa ditentukan dari requirement sebelumnya.

Sekarang IMPLEMENTasikan DAILY SLOT SYSTEM.

ATURAN:
1. Pertahankan architecture dan code existing.
2. Jangan melakukan refactor besar yang tidak diperlukan.
3. Jangan merusak upload, downloader, queue, worker, scheduler, atau publishing yang sudah PASS.
4. Gunakan migration/schema yang aman.
5. Jangan membuat fake implementation.
6. Jangan commit secret.
7. Setelah selesai WAJIB test, build, git status, commit, dan push.

IMPLEMENTASI:

A. Scheduling Settings
Tambahkan konfigurasi:
- enabled
- max_videos_per_day
- timezone

B. Daily Slots
Tambahkan slot yang dapat dikonfigurasi:
- slot_time
- enabled
- order

Contoh default:
08:00
11:00
14:00
17:00

Jangan hardcode slot di scheduler.

C. Shared Pipeline

Pastikan:

Manual Upload ─┐
               ├→ Media → READY → Auto Scheduler → Publishing Job → Queue → Worker
Downloader ────┘

Downloader harus membuat Media dengan:
- media_id
- source_type
- source_id/source_url jika tersedia
- created_at

D. GLOBAL SEQUENCE

Implementasikan sequence global.

Contoh:
Hari 1:
Video 1
Video 2
Video 3

Hari 2:
Video 4
Video 5

Sequence TIDAK BOLEH reset setiap hari.

Sequence yang sudah pernah digunakan:
- published
- failed
- cancelled

TIDAK BOLEH digunakan ulang.

Jangan gunakan filename sebagai identifier.

E. AUTO SLOT ALLOCATION

Dengan konfigurasi:

max_videos_per_day = 4

08:00
11:00
14:00
17:00

Jika masuk:
Video 1 → 08:00
Video 2 → 11:00
Video 3 → 14:00
Video 4 → 17:00
Video 5 → hari berikutnya 08:00

Jika hari pertama hanya ada 3 video:

Video 1 → hari 1 08:00
Video 2 → hari 1 11:00
Video 3 → hari 1 14:00

Jika Video 4 baru masuk setelah hari pertama selesai:
Video 4 → hari 2 08:00

Jangan mengisi ulang Video 1.

F. MULTIPLE DOWNLOAD

Jika downloader memasukkan:

Video A
Video B
Video C
Video D
Video E

dalam satu batch, gunakan urutan ingestion/created_at yang stabil dan berikan slot berurutan.

Scheduler harus idempotent.

Restart scheduler/worker tidak boleh membuat duplicate PublishingJob.

G. MANUAL OVERRIDE

Setiap PublishingJob dapat memiliki:
schedule_source = auto | manual

Jika manual:
scheduled_at harus dihormati scheduler.

Jangan ditimpa oleh auto scheduler.

H. RESCHEDULING

Job yang sudah:
- published
- processing
- uploading
- publishing

JANGAN diubah karena konfigurasi slot berubah.

Job yang masih:
- draft
- queued
- scheduled

boleh disesuaikan hanya jika memang diperlukan dan tetap mengikuti aturan sequence.

I. TIMEZONE

scheduled_at harus disimpan sebagai waktu absolut yang aman.

Timezone konfigurasi hanya digunakan untuk menentukan slot lokal.

J. DUPLICATE PROTECTION

Pastikan terdapat protection untuk:
- duplicate media scheduling
- duplicate sequence
- duplicate PublishingJob
- scheduler restart
- worker restart
- duplicate downloader event

Gunakan constraint/database/idempotency yang sesuai architecture existing.

K. UI

Tambahkan UI minimal untuk:

Auto Publishing:
[ ON/OFF ]

Maximum videos/day:
[ 4 ]

Timezone:
[ ... ]

Daily Slots:
08:00 [ON]
11:00 [ON]
14:00 [ON]
17:00 [ON]

Tambahkan:
+ Add Slot

Jangan membuat dashboard baru jika UI existing sudah memiliki Settings.

L. TEST WAJIB

Tambahkan test untuk minimal:

1. 4 video mengisi 4 slot.
2. Video ke-5 masuk hari berikutnya.
3. Hari pertama hanya 3 video → video berikutnya tetap sequence berikutnya.
4. Sequence tidak reset saat tanggal berubah.
5. Batch downloader mendapat slot berurutan.
6. Manual override.
7. Slot yang sudah lewat.
8. Semua slot hari ini penuh.
9. Scheduler restart tidak duplicate.
10. Worker restart tidak duplicate.
11. Failed job tidak menggunakan ulang sequence.
12. Cancelled job tidak menggunakan ulang sequence.
13. Perubahan konfigurasi tidak mengubah published job.
14. Timezone.
15. Duplicate downloader event.

Jalankan:
- typecheck
- lint
- test
- build

Jangan menghapus test existing.

Jika test existing gagal karena perubahan ini, perbaiki implementation sampai regression kembali PASS.

GIT:

Setelah semua PASS:

1. git status
2. git diff
3. pastikan tidak ada secret
4. commit:
   feat: implement daily slot auto publishing
5. push ke branch aktif
6. verifikasi remote

Jangan force push.
Jangan membuat commit kosong.

OUTPUT AKHIR:

DAILY SLOT IMPLEMENTATION: COMPLETE
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL
GIT STATUS: CLEAN/NOT CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS/FAIL
REMOTE VERIFIED: YES/NO

Jika semua PASS, STOP.
````


# Prompt 02 — Auto Publishing Queue & Daily Slot Specification
```

Lanjutkan project Content Pilot dari hasil Phase 0.

JANGAN melakukan implementation/coding dulu.
JANGAN mengubah source code.
JANGAN membuat database migration.
JANGAN membuat UI production.

Fokus hanya menyusun SPECIFICATION untuk:

AUTO PUBLISHING QUEUE + DAILY SLOT CONFIGURATION

Requirement yang sudah disepakati:

1. Admin dapat mengatur:
   - Auto publishing ON/OFF
   - Maximum video per hari
   - Timezone
   - Slot waktu upload harian

Contoh:
Maximum videos/day = 4

Slots:
08:00
11:00
14:00
17:00

2. Manual Upload dan Downloader HARUS menggunakan shared pipeline:

Manual Upload ─┐
               ├→ Media → READY → Scheduler → Publishing Job → Queue → Worker
Downloader ────┘

3. Setiap media dari downloader harus memiliki identifier sendiri dan metadata:
   - media_id
   - source_type
   - source_id/source_url jika tersedia
   - created_at

Jangan menggunakan filename sebagai identifier utama.

4. Sequence video bersifat GLOBAL dan tidak reset ketika tanggal berubah.

Contoh:

Hari 1:
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong

Jika besok downloader video baru:

Hari 2:
08:00 → Video 4

BUKAN kembali menjadi Video 1.

5. Jika hari pertama penuh:

Hari 1:
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → Video 4

Video berikutnya:

Hari 2:
08:00 → Video 5

6. Jika downloader memasukkan beberapa video sekaligus, urutkan berdasarkan created_at/ingestion order yang stabil.

Contoh:
Video 1
Video 2
Video 3
Video 4

Masing-masing mendapat slot berurutan.

7. Jika slot hari ini sudah penuh, otomatis cari slot kosong berikutnya pada hari berikutnya.

8. Jangan pernah mengulang sequence_number yang sudah pernah diberikan.

Sequence number harus berbeda dari:
- media_id
- publishing_job_id
- filename

9. Setiap video boleh memiliki manual schedule override.

Contoh:

Auto slot:
08:00

Tetapi user memilih:
Video 7 → 20:30

Maka:
schedule_source = manual

dan scheduled_at = 20:30.

10. Scheduler harus menyimpan waktu aktual:

scheduled_at

Jangan hanya menyimpan:
day_number
slot_number

11. Jika konfigurasi slot berubah:

Contoh:
Awalnya:
08:00
11:00
14:00
17:00

kemudian diubah menjadi:
09:00
13:00
18:00

Jangan mengubah job yang sudah:
- published
- processing
- uploading

Buat aturan jelas untuk job yang masih:
- draft
- queued
- scheduled

12. Jika video gagal publish:

Sequence number TIDAK boleh dipakai ulang.

13. Jika job dibatalkan:

Sequence number TIDAK boleh dipakai ulang.

14. Scheduler harus timezone-aware.

15. Hindari double scheduling ketika:
- worker restart
- server restart
- scheduler restart
- job diproses ulang

Gunakan idempotency/deduplication.

16. Buat state transition yang jelas:

Media:
uploaded
processing
ready
failed

PublishingJob:
draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

17. Buat logical data model minimal:

SchedulingSettings
- id
- enabled
- timezone
- max_videos_per_day

DailySlot
- id
- settings_id
- slot_time
- enabled
- order

Media
- id
- sequence_number jika memang ditempatkan di Media,
  atau jelaskan jika lebih tepat berada di PublishingJob
- source_type
- source_id/source_url
- created_at
- status

PublishingJob
- id
- media_id
- provider
- destination_id
- sequence_number
- scheduled_at
- schedule_source
- status
- created_at

Jika menurutmu sequence_number lebih tepat hanya berada di PublishingJob, jelaskan alasannya dan gunakan desain tersebut.

18. Buat contoh algoritma scheduling.

Gunakan contoh:

Settings:
4 video/day
08:00, 11:00, 14:00, 17:00

Input:
Video 1
Video 2
Video 3
Video 4
Video 5
Video 6

Tunjukkan hasil schedule.

Kemudian contoh kedua:

Hari pertama hanya ada:
Video 1
Video 2
Video 3

Hari kedua downloader:
Video 4
Video 5

Tunjukkan hasil schedule.

19. Jelaskan kasus khusus:

- slot sudah lewat
- semua slot hari ini penuh
- downloader memasukkan 10 video sekaligus
- video gagal
- video dibatalkan
- server restart
- timezone berubah
- admin mengubah jumlah slot
- admin mengubah max videos/day
- manual override
- duplicate downloader event

20. Buat acceptance criteria yang jelas sehingga nanti implementation dapat dites.

21. Jangan membuat fake implementation.

22. Jangan mengubah code.

23. Jangan melakukan migration.

24. Jangan melakukan commit/push karena tahap ini hanya specification.

OUTPUT:

1. Auto Publishing Architecture
2. Scheduling Data Model
3. Sequence Number Strategy
4. Slot Allocation Algorithm
5. Queue Interaction
6. State Transition
7. Rescheduling Rules
8. Edge Cases
9. Idempotency Strategy
10. Acceptance Criteria
11. Implementation Plan untuk phase berikutnya

Setelah specification selesai:

STOP.

Tampilkan:

DAILY SLOT SPEC: COMPLETE
CODE CHANGES: NONE
DATABASE CHANGES: NONE
IMPLEMENTATION STATUS: NOT STARTED
NEXT STEP: IMPLEMENT DAILY SLOT SYSTEM
````
# 
```
# Prompt 01 — Continue & Correct Repository Audit

Kita lanjutkan Prompt 01.

Saya sudah meninjau hasil sebelumnya dan ada masalah penting:

Repository saat ini masih berisi project lama berbasis Python/NiceGUI dan platform sosial yang berbeda. Project tersebut BUKAN arsitektur final untuk project baru Content Pilot yang sedang kita bangun.

Karena itu, jangan menganggap struktur lama sebagai arsitektur final.

Tujuan kita sekarang adalah menyelesaikan Phase 0 dengan benar sebelum coding fitur apa pun.

## PROJECT BARU

Nama project:

Content Pilot

Tujuan:

Membangun web platform untuk mengelola dan melakukan automatic content publishing ke berbagai platform sosial.

Platform pertama yang akan diimplementasikan adalah Facebook.

Namun arsitektur HARUS siap untuk:

* Facebook
* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang nantinya memiliki API publishing resmi yang sesuai

Facebook adalah provider pertama, bukan core system.

## ATURAN UTAMA

Jangan mulai implementation fitur publishing.

Jangan membuat Facebook uploader.

Jangan membuat OAuth Facebook terlebih dahulu.

Jangan membuat queue production terlebih dahulu.

Jangan membuat dashboard production terlebih dahulu.

Selesaikan discovery, architecture, documentation, dan roadmap terlebih dahulu.

## REPOSITORY AUDIT

Audit repository yang benar-benar sedang digunakan.

Periksa:

* seluruh root directory
* seluruh source code
* package/dependency
* konfigurasi
* database
* frontend
* backend
* test
* Docker
* deployment
* existing UI
* existing documentation

Pisahkan hasil menjadi:

1. Existing project lama
2. Existing code yang dapat dipertahankan
3. Existing code yang tidak relevan
4. Existing documentation yang perlu dipertahankan
5. Documentation yang perlu diperbarui
6. Komponen yang harus dibuat untuk Content Pilot
7. Risiko migrasi/refactor

Jangan mengklaim architecture baru sudah ada jika file tersebut belum benar-benar dibuat di repository.

## JANGAN MENGHAPUS PROJECT LAMA SECARA SEMBARANGAN

Sebelum menghapus atau mengganti source code lama:

* identifikasi terlebih dahulu
* jelaskan apa yang tidak relevan
* tentukan apakah project baru memang akan menggantikan project lama
* dokumentasikan keputusan

Jangan melakukan destructive migration pada Phase 0.

## TARGET TECH STACK

Gunakan TypeScript full-stack sebagai kandidat utama.

Kandidat architecture:

Frontend:
Next.js

Backend/API:
Fastify atau NestJS

Worker:
BullMQ

Queue:
Redis

Database:
PostgreSQL

Object storage:
S3-compatible storage

Namun ini masih architecture proposal.

Jangan langsung install atau implementasikan semuanya sebelum architecture final disetujui.

Bandingkan Fastify vs NestJS berdasarkan kebutuhan project ini dan pilih yang paling tepat.

Pertimbangkan:

* maintainability
* modular provider architecture
* queue/worker
* OAuth
* API integration
* validation
* testing
* scalability
* developer experience

## CORE ARCHITECTURE

Core tidak boleh bergantung pada Facebook.

Core harus menangani konsep generik:

* User
* Platform
* PlatformConnection
* Destination
* Media
* Post
* PublishingJob
* PublishingAttempt
* Schedule
* Queue
* Scheduler
* History
* AuditLog
* Notification
* Storage

Platform-specific implementation harus berada di provider/module masing-masing.

Target konsep:

Core
→ Provider Registry
→ Platform Provider
→ Platform-specific implementation

Contoh:

Core
→ Facebook Provider
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

## PROVIDER SYSTEM

Desain provider abstraction yang benar-benar extensible.

Jangan memaksakan semua provider memiliki fitur identik.

Gunakan capability-based architecture.

Contoh capability:

* video
* reels
* photo
* text_post
* link_post
* short_video
* scheduling
* analytics

Provider harus dapat melaporkan capability yang memang didukung.

Jangan membuat capability berdasarkan asumsi.

Capability harus dapat berasal dari:

* kemampuan API
* implementation provider
* permission
* destination type

## FACEBOOK

Facebook adalah provider pertama.

Tetapi sebelum implementation, lakukan research resmi.

Research:

* authentication
* OAuth
* Page connection
* Page discovery
* destination model
* video publishing
* Reels publishing
* photo publishing
* post publishing
* scheduling
* status checking
* error handling
* rate limits
* permissions
* app review requirements
* token expiration
* token refresh/reconnect

Jika fitur belum dapat diverifikasi:

MARK AS UNKNOWN / NEEDS VERIFICATION

Jangan mengarang endpoint atau permission.

## API RESEARCH

Gunakan dokumentasi resmi sebagai sumber utama.

Prioritas:

1. Meta/Facebook official documentation
2. YouTube official documentation
3. Instagram official documentation
4. TikTok official documentation

Untuk platform lain, research dilakukan setelah provider utama stabil.

Buat capability matrix.

Contoh kolom:

Platform
Authentication
Destination
Video
Reels
Photo
Text Post
Scheduling
Analytics
Required Permissions
Upload Flow
Known Limitations
Verification Status

Jangan menulis fitur sebagai AVAILABLE jika belum diverifikasi.

## MULTI ACCOUNT

Dari awal sistem harus mendukung:

User
→ multiple PlatformConnection
→ multiple Destination

Contoh:

User
→ Facebook Account
→ Page A
→ Page B
→ Page C

Dan nanti:

User
→ YouTube Account
→ Channel A
→ Channel B

Jangan membuat database yang hanya mendukung satu account atau satu Page.

## PUBLISHING JOB

Gunakan satu job per destination.

Contoh:

Video A

→ Facebook Page A = Job 001
→ Facebook Page B = Job 002
→ YouTube Channel A = Job 003

Setiap job memiliki status sendiri.

Contoh status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jika Facebook berhasil dan YouTube gagal:

Facebook = published
YouTube = failed

Bukan satu global job yang kehilangan detail platform.

## MEDIA ARCHITECTURE

Media harus platform-independent.

Video hanya disimpan sekali di media/storage layer.

Kemudian dapat digunakan oleh beberapa publishing job.

Jangan membuat:

FacebookVideo
YouTubeVideo
InstagramVideo

sebagai storage model utama.

Gunakan media generik lalu provider melakukan transformasi/validation sesuai capability platform.

## QUEUE

Queue harus platform-independent.

Core queue menerima PublishingJob.

Worker mengambil job.

Worker memanggil provider yang sesuai.

## AUTO PUBLISHING QUEUE & DAILY SLOT CONFIGURATION

Sistem publishing nantinya harus mendukung konfigurasi otomatis berdasarkan kuota video per hari dan slot waktu.

Contoh konfigurasi:

```text
Maximum videos per day: 4
Slots:
08:00
11:00
14:00
17:00
```

Aturan utama:

1. Manual upload dan downloader harus masuk ke **shared media/publishing pipeline yang sama**.
2. Media dari downloader harus otomatis tersimpan sebagai Media dengan identifier/source metadata yang dapat dilacak.
3. Setelah media berstatus READY, jika auto scheduling aktif, sistem mencari **slot publikasi tersedia paling awal**.
4. Nomor urut video bersifat global/sequence dan **tidak reset setiap hari**.
5. Jika hari pertama hanya memiliki 3 video dari kapasitas 4:

```text
Hari 1
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong
```

Jika hari tersebut sudah lewat dan video baru masuk, video baru menjadi Video 4 dan ditempatkan pada slot tersedia berikutnya di hari berikutnya. Jangan mengubahnya kembali menjadi Video 1.

6. Jika hari pertama penuh 4 video, video berikutnya otomatis masuk ke slot pertama hari kedua.
7. Jika beberapa video didownload sekaligus, masing-masing memperoleh slot berurutan berdasarkan urutan masuk/created time.
8. Jangan melakukan reset sequence ketika tanggal berganti.
9. Jangan menggunakan ulang nomor sequence media/post yang sudah pernah diberikan, termasuk ketika job gagal atau dibatalkan.
10. Pengaturan jumlah video per hari dan slot waktu harus dapat diubah tanpa merusak job yang sudah published.
11. Perubahan konfigurasi hanya boleh mempengaruhi job/schedule yang belum final/published sesuai aturan rescheduling yang jelas.
12. Setiap video boleh memiliki **manual schedule override** yang menggantikan slot otomatis untuk video tersebut.
13. Scheduler harus menyimpan scheduled_at yang aktual pada job, bukan hanya menyimpan nomor hari/slot.

Logical flow:

```text
Manual Upload ─┐
               ├→ Media Library → READY → Auto Scheduler → Publishing Job → Queue → Worker
Downloader ────┘
```

Minimal konsep konfigurasi:

```text
SchedulingSettings
- enabled
- max_videos_per_day
- timezone
- daily_slots[]
```

Minimal metadata queue/job:

```text
Media
- id
- source_type (manual | downloader | other)
- source_id/source_url jika tersedia
- created_at

PublishingJob
- sequence_number
- media_id
- scheduled_at
- schedule_source (auto | manual)
- status
```

Sequence number, media ID, dan publishing job ID harus dibedakan. Jangan menggunakan filename sebagai identifier utama.

Arsitektur ini harus dirancang secara generik sehingga nantinya dapat dipakai untuk Facebook, YouTube, Instagram, TikTok, dan provider lain.

Contoh:

PublishingJob
→ provider = facebook
→ destination = Page A
→ publish()

Kemudian:

PublishingJob
→ provider = youtube
→ destination = Channel A
→ publish()

## RETRY

Bedakan temporary error dan permanent error.

Temporary:

* timeout
* network failure
* temporary API failure
* rate limit

Permanent:

* invalid token
* permission denied
* unsupported media
* invalid destination

Simpan:

* attempt count
* error code
* error message
* timestamp
* next retry
* provider response metadata jika aman

## SECURITY

Architecture harus memperhatikan:

* OAuth
* access token
* refresh token
* encryption
* secret management
* environment variables
* authorization
* user isolation
* file upload validation
* MIME validation
* file size limit
* path traversal
* SSRF
* rate limiting
* audit logs

Jangan commit secrets.

## UI DESIGN

Audit apakah repository saat ini sudah memiliki UI yang relevan untuk Content Pilot.

Jika UI lama tidak sesuai, jangan langsung menganggapnya sebagai UI final.

Dokumentasikan:

Current UI
→ reusable
→ needs redesign
→ obsolete

Untuk Content Pilot, target UI harus clean, modern, responsive, dan nyaman digunakan melalui desktop maupun mobile.

Konsep utama:

Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings

Tetapi jangan implementasikan semua halaman sekarang.

## UI DOCUMENTATION

Buat UI specification agar AI coding nantinya memiliki referensi yang konsisten.

Minimal dokumentasikan:

* layout
* navigation
* responsive behavior
* typography
* spacing
* buttons
* forms
* cards
* tables
* upload interface
* video preview
* publishing status
* queue
* scheduled posts
* account connection
* error state
* loading state
* empty state

Jangan membuat UI specification yang bertentangan dengan UI yang benar-benar dipilih untuk project.

## DOCUMENTATION

Buat documentation untuk project baru.

Gunakan struktur yang sederhana.

Minimal:

README.md

docs/ARCHITECTURE.md

docs/UI_DESIGN.md

docs/PLATFORM_MODULES.md

docs/DATABASE.md

docs/ROADMAP.md

docs/research/facebook-api.md

Jika dokumentasi dengan tujuan yang sama sudah ada, update file tersebut.

Jangan membuat duplicate documentation.

## DATABASE DESIGN

Buat ERD/logical model terlebih dahulu.

Minimal entity:

User
Platform
PlatformConnection
Destination
Media
Post
PublishingJob
PublishingAttempt
Schedule
AuditLog

Pastikan model mendukung:

1 user
→ many platform connections
→ many destinations
→ many media
→ many posts
→ many publishing jobs

Destination harus generik.

Facebook Page dan YouTube Channel harus dapat direpresentasikan sebagai destination tanpa mengubah core model.

## ROADMAP

Buat roadmap berdasarkan hasil audit aktual.

Phase 0:
Discovery, Audit, Research, Architecture, Documentation

Phase 1:
Core Foundation

Phase 2:
Authentication & Platform Connection

Phase 3:
Facebook Provider

Phase 4:
Facebook Publishing Capabilities

Phase 5:
Queue & Scheduler hardening

Phase 6:
YouTube Provider

Phase 7:
Instagram Provider

Phase 8:
TikTok Provider

Phase 9:
Advanced Automation

Jangan menganggap urutan ini final jika hasil audit menunjukkan urutan yang lebih baik.

Jelaskan alasan setiap phase.

## IMPORTANT

Pada tahap ini:

DO NOT implement publishing.

DO NOT implement Facebook OAuth.

DO NOT implement YouTube.

DO NOT implement TikTok.

DO NOT create fake API integrations.

DO NOT create fake success states.

DO NOT perform a massive refactor without reporting it.

DO NOT delete existing project files simply to make the repository look clean.

Fokus pada Phase 0.

## OUTPUT

Setelah selesai, berikan laporan:

Repository Status

Existing Stack

Existing Architecture

Existing UI

Existing Database

Existing Code

Reusable Components

Obsolete Components

Target Architecture

Provider Architecture

Database Model

UI Architecture

Facebook API Research

Platform Capability Matrix

Security Considerations

Migration Strategy

Roadmap

Recommended Phase 1

Risks

Open Questions

## REQUIRED FINAL STATUS

Tampilkan:

AUDIT STATUS: COMPLETE

ARCHITECTURE STATUS: READY / NEEDS REVISION

API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION

DOCUMENTATION STATUS: COMPLETE / INCOMPLETE

ROADMAP STATUS: READY

IMPLEMENTATION STATUS: NOT STARTED

NEXT RECOMMENDED STEP: ...

Jika architecture masih memiliki masalah, jangan menyatakan READY.

Tunjukkan masalahnya dan perbaiki dokumentasi terlebih dahulu.

STOP setelah Phase 0 selesai.

Jangan lanjut coding Phase 1 tanpa instruksi berikutnya.

## GIT COMMIT & PUSH

Setelah seluruh pekerjaan Phase 0 selesai dan dokumentasi sudah benar:

1. Periksa git status.
2. Pastikan tidak ada secret, token, API key, password, atau file sensitif yang akan di-commit.
3. Periksa diff seluruh perubahan.
4. Jalankan pemeriksaan yang aman dan relevan terhadap dokumentasi/struktur yang dibuat.
5. Commit seluruh perubahan Phase 0 dengan commit message yang jelas, misalnya:
   docs: complete content pilot phase 0 architecture audit
6. Push commit tersebut langsung ke branch yang sedang digunakan untuk project ini.
7. Setelah push berhasil, verifikasi bahwa commit sudah berada di remote repository.
8. Laporkan commit hash dan branch yang berhasil di-push.

Jangan melakukan push jika terdapat secret atau perubahan yang tidak berkaitan dengan Phase 0.
Jangan membuat commit kosong.
Jangan melakukan force push.

Jika push gagal karena authentication, permission, remote, atau masalah Git lainnya, jangan mengarang bahwa push berhasil. Laporkan error sebenarnya dan hentikan proses setelah pekerjaan lokal aman.

Setelah push berhasil, tampilkan:

GIT STATUS: CLEAN
COMMIT: <commit hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

Kemudian STOP.


````
# 
```
# Prompt 01 — Continue & Correct Repository Audit

Kita lanjutkan Prompt 01.

Saya sudah meninjau hasil sebelumnya dan ada masalah penting:

Repository saat ini masih berisi project lama berbasis Python/NiceGUI dan platform sosial yang berbeda. Project tersebut BUKAN arsitektur final untuk project baru Content Pilot yang sedang kita bangun.

Karena itu, jangan menganggap struktur lama sebagai arsitektur final.

Tujuan kita sekarang adalah menyelesaikan Phase 0 dengan benar sebelum coding fitur apa pun.

## PROJECT BARU

Nama project:

Content Pilot

Tujuan:

Membangun web platform untuk mengelola dan melakukan automatic content publishing ke berbagai platform sosial.

Platform pertama yang akan diimplementasikan adalah Facebook.

Namun arsitektur HARUS siap untuk:

* Facebook
* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang nantinya memiliki API publishing resmi yang sesuai

Facebook adalah provider pertama, bukan core system.

## ATURAN UTAMA

Jangan mulai implementation fitur publishing.

Jangan membuat Facebook uploader.

Jangan membuat OAuth Facebook terlebih dahulu.

Jangan membuat queue production terlebih dahulu.

Jangan membuat dashboard production terlebih dahulu.

Selesaikan discovery, architecture, documentation, dan roadmap terlebih dahulu.

## REPOSITORY AUDIT

Audit repository yang benar-benar sedang digunakan.

Periksa:

* seluruh root directory
* seluruh source code
* package/dependency
* konfigurasi
* database
* frontend
* backend
* test
* Docker
* deployment
* existing UI
* existing documentation

Pisahkan hasil menjadi:

1. Existing project lama
2. Existing code yang dapat dipertahankan
3. Existing code yang tidak relevan
4. Existing documentation yang perlu dipertahankan
5. Documentation yang perlu diperbarui
6. Komponen yang harus dibuat untuk Content Pilot
7. Risiko migrasi/refactor

Jangan mengklaim architecture baru sudah ada jika file tersebut belum benar-benar dibuat di repository.

## JANGAN MENGHAPUS PROJECT LAMA SECARA SEMBARANGAN

Sebelum menghapus atau mengganti source code lama:

* identifikasi terlebih dahulu
* jelaskan apa yang tidak relevan
* tentukan apakah project baru memang akan menggantikan project lama
* dokumentasikan keputusan

Jangan melakukan destructive migration pada Phase 0.

## TARGET TECH STACK

Gunakan TypeScript full-stack sebagai kandidat utama.

Kandidat architecture:

Frontend:
Next.js

Backend/API:
Fastify atau NestJS

Worker:
BullMQ

Queue:
Redis

Database:
PostgreSQL

Object storage:
S3-compatible storage

Namun ini masih architecture proposal.

Jangan langsung install atau implementasikan semuanya sebelum architecture final disetujui.

Bandingkan Fastify vs NestJS berdasarkan kebutuhan project ini dan pilih yang paling tepat.

Pertimbangkan:

* maintainability
* modular provider architecture
* queue/worker
* OAuth
* API integration
* validation
* testing
* scalability
* developer experience

## CORE ARCHITECTURE

Core tidak boleh bergantung pada Facebook.

Core harus menangani konsep generik:

* User
* Platform
* PlatformConnection
* Destination
* Media
* Post
* PublishingJob
* PublishingAttempt
* Schedule
* Queue
* Scheduler
* History
* AuditLog
* Notification
* Storage

Platform-specific implementation harus berada di provider/module masing-masing.

Target konsep:

Core
→ Provider Registry
→ Platform Provider
→ Platform-specific implementation

Contoh:

Core
→ Facebook Provider
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

## PROVIDER SYSTEM

Desain provider abstraction yang benar-benar extensible.

Jangan memaksakan semua provider memiliki fitur identik.

Gunakan capability-based architecture.

Contoh capability:

* video
* reels
* photo
* text_post
* link_post
* short_video
* scheduling
* analytics

Provider harus dapat melaporkan capability yang memang didukung.

Jangan membuat capability berdasarkan asumsi.

Capability harus dapat berasal dari:

* kemampuan API
* implementation provider
* permission
* destination type

## FACEBOOK

Facebook adalah provider pertama.

Tetapi sebelum implementation, lakukan research resmi.

Research:

* authentication
* OAuth
* Page connection
* Page discovery
* destination model
* video publishing
* Reels publishing
* photo publishing
* post publishing
* scheduling
* status checking
* error handling
* rate limits
* permissions
* app review requirements
* token expiration
* token refresh/reconnect

Jika fitur belum dapat diverifikasi:

MARK AS UNKNOWN / NEEDS VERIFICATION

Jangan mengarang endpoint atau permission.

## API RESEARCH

Gunakan dokumentasi resmi sebagai sumber utama.

Prioritas:

1. Meta/Facebook official documentation
2. YouTube official documentation
3. Instagram official documentation
4. TikTok official documentation

Untuk platform lain, research dilakukan setelah provider utama stabil.

Buat capability matrix.

Contoh kolom:

Platform
Authentication
Destination
Video
Reels
Photo
Text Post
Scheduling
Analytics
Required Permissions
Upload Flow
Known Limitations
Verification Status

Jangan menulis fitur sebagai AVAILABLE jika belum diverifikasi.

## MULTI ACCOUNT

Dari awal sistem harus mendukung:

User
→ multiple PlatformConnection
→ multiple Destination

Contoh:

User
→ Facebook Account
→ Page A
→ Page B
→ Page C

Dan nanti:

User
→ YouTube Account
→ Channel A
→ Channel B

Jangan membuat database yang hanya mendukung satu account atau satu Page.

## PUBLISHING JOB

Gunakan satu job per destination.

Contoh:

Video A

→ Facebook Page A = Job 001
→ Facebook Page B = Job 002
→ YouTube Channel A = Job 003

Setiap job memiliki status sendiri.

Contoh status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jika Facebook berhasil dan YouTube gagal:

Facebook = published
YouTube = failed

Bukan satu global job yang kehilangan detail platform.

## MEDIA ARCHITECTURE

Media harus platform-independent.

Video hanya disimpan sekali di media/storage layer.

Kemudian dapat digunakan oleh beberapa publishing job.

Jangan membuat:

FacebookVideo
YouTubeVideo
InstagramVideo

sebagai storage model utama.

Gunakan media generik lalu provider melakukan transformasi/validation sesuai capability platform.

## QUEUE

Queue harus platform-independent.

Core queue menerima PublishingJob.

Worker mengambil job.

Worker memanggil provider yang sesuai.

## AUTO PUBLISHING QUEUE & DAILY SLOT CONFIGURATION

Sistem publishing nantinya harus mendukung konfigurasi otomatis berdasarkan kuota video per hari dan slot waktu.

Contoh konfigurasi:

```text
Maximum videos per day: 4
Slots:
08:00
11:00
14:00
17:00
```

Aturan utama:

1. Manual upload dan downloader harus masuk ke **shared media/publishing pipeline yang sama**.
2. Media dari downloader harus otomatis tersimpan sebagai Media dengan identifier/source metadata yang dapat dilacak.
3. Setelah media berstatus READY, jika auto scheduling aktif, sistem mencari **slot publikasi tersedia paling awal**.
4. Nomor urut video bersifat global/sequence dan **tidak reset setiap hari**.
5. Jika hari pertama hanya memiliki 3 video dari kapasitas 4:

```text
Hari 1
08:00 → Video 1
11:00 → Video 2
14:00 → Video 3
17:00 → kosong
```

Jika hari tersebut sudah lewat dan video baru masuk, video baru menjadi Video 4 dan ditempatkan pada slot tersedia berikutnya di hari berikutnya. Jangan mengubahnya kembali menjadi Video 1.

6. Jika hari pertama penuh 4 video, video berikutnya otomatis masuk ke slot pertama hari kedua.
7. Jika beberapa video didownload sekaligus, masing-masing memperoleh slot berurutan berdasarkan urutan masuk/created time.
8. Jangan melakukan reset sequence ketika tanggal berganti.
9. Jangan menggunakan ulang nomor sequence media/post yang sudah pernah diberikan, termasuk ketika job gagal atau dibatalkan.
10. Pengaturan jumlah video per hari dan slot waktu harus dapat diubah tanpa merusak job yang sudah published.
11. Perubahan konfigurasi hanya boleh mempengaruhi job/schedule yang belum final/published sesuai aturan rescheduling yang jelas.
12. Setiap video boleh memiliki **manual schedule override** yang menggantikan slot otomatis untuk video tersebut.
13. Scheduler harus menyimpan scheduled_at yang aktual pada job, bukan hanya menyimpan nomor hari/slot.

Logical flow:

```text
Manual Upload ─┐
               ├→ Media Library → READY → Auto Scheduler → Publishing Job → Queue → Worker
Downloader ────┘
```

Minimal konsep konfigurasi:

```text
SchedulingSettings
- enabled
- max_videos_per_day
- timezone
- daily_slots[]
```

Minimal metadata queue/job:

```text
Media
- id
- source_type (manual | downloader | other)
- source_id/source_url jika tersedia
- created_at

PublishingJob
- sequence_number
- media_id
- scheduled_at
- schedule_source (auto | manual)
- status
```

Sequence number, media ID, dan publishing job ID harus dibedakan. Jangan menggunakan filename sebagai identifier utama.

Arsitektur ini harus dirancang secara generik sehingga nantinya dapat dipakai untuk Facebook, YouTube, Instagram, TikTok, dan provider lain.

Contoh:

PublishingJob
→ provider = facebook
→ destination = Page A
→ publish()

Kemudian:

PublishingJob
→ provider = youtube
→ destination = Channel A
→ publish()

## RETRY

Bedakan temporary error dan permanent error.

Temporary:

* timeout
* network failure
* temporary API failure
* rate limit

Permanent:

* invalid token
* permission denied
* unsupported media
* invalid destination

Simpan:

* attempt count
* error code
* error message
* timestamp
* next retry
* provider response metadata jika aman

## SECURITY

Architecture harus memperhatikan:

* OAuth
* access token
* refresh token
* encryption
* secret management
* environment variables
* authorization
* user isolation
* file upload validation
* MIME validation
* file size limit
* path traversal
* SSRF
* rate limiting
* audit logs

Jangan commit secrets.

## UI DESIGN

Audit apakah repository saat ini sudah memiliki UI yang relevan untuk Content Pilot.

Jika UI lama tidak sesuai, jangan langsung menganggapnya sebagai UI final.

Dokumentasikan:

Current UI
→ reusable
→ needs redesign
→ obsolete

Untuk Content Pilot, target UI harus clean, modern, responsive, dan nyaman digunakan melalui desktop maupun mobile.

Konsep utama:

Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings

Tetapi jangan implementasikan semua halaman sekarang.

## UI DOCUMENTATION

Buat UI specification agar AI coding nantinya memiliki referensi yang konsisten.

Minimal dokumentasikan:

* layout
* navigation
* responsive behavior
* typography
* spacing
* buttons
* forms
* cards
* tables
* upload interface
* video preview
* publishing status
* queue
* scheduled posts
* account connection
* error state
* loading state
* empty state

Jangan membuat UI specification yang bertentangan dengan UI yang benar-benar dipilih untuk project.

## DOCUMENTATION

Buat documentation untuk project baru.

Gunakan struktur yang sederhana.

Minimal:

README.md

docs/ARCHITECTURE.md

docs/UI_DESIGN.md

docs/PLATFORM_MODULES.md

docs/DATABASE.md

docs/ROADMAP.md

docs/research/facebook-api.md

Jika dokumentasi dengan tujuan yang sama sudah ada, update file tersebut.

Jangan membuat duplicate documentation.

## DATABASE DESIGN

Buat ERD/logical model terlebih dahulu.

Minimal entity:

User
Platform
PlatformConnection
Destination
Media
Post
PublishingJob
PublishingAttempt
Schedule
AuditLog

Pastikan model mendukung:

1 user
→ many platform connections
→ many destinations
→ many media
→ many posts
→ many publishing jobs

Destination harus generik.

Facebook Page dan YouTube Channel harus dapat direpresentasikan sebagai destination tanpa mengubah core model.

## ROADMAP

Buat roadmap berdasarkan hasil audit aktual.

Phase 0:
Discovery, Audit, Research, Architecture, Documentation

Phase 1:
Core Foundation

Phase 2:
Authentication & Platform Connection

Phase 3:
Facebook Provider

Phase 4:
Facebook Publishing Capabilities

Phase 5:
Queue & Scheduler hardening

Phase 6:
YouTube Provider

Phase 7:
Instagram Provider

Phase 8:
TikTok Provider

Phase 9:
Advanced Automation

Jangan menganggap urutan ini final jika hasil audit menunjukkan urutan yang lebih baik.

Jelaskan alasan setiap phase.

## IMPORTANT

Pada tahap ini:

DO NOT implement publishing.

DO NOT implement Facebook OAuth.

DO NOT implement YouTube.

DO NOT implement TikTok.

DO NOT create fake API integrations.

DO NOT create fake success states.

DO NOT perform a massive refactor without reporting it.

DO NOT delete existing project files simply to make the repository look clean.

Fokus pada Phase 0.

## OUTPUT

Setelah selesai, berikan laporan:

Repository Status

Existing Stack

Existing Architecture

Existing UI

Existing Database

Existing Code

Reusable Components

Obsolete Components

Target Architecture

Provider Architecture

Database Model

UI Architecture

Facebook API Research

Platform Capability Matrix

Security Considerations

Migration Strategy

Roadmap

Recommended Phase 1

Risks

Open Questions

## REQUIRED FINAL STATUS

Tampilkan:

AUDIT STATUS: COMPLETE

ARCHITECTURE STATUS: READY / NEEDS REVISION

API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION

DOCUMENTATION STATUS: COMPLETE / INCOMPLETE

ROADMAP STATUS: READY

IMPLEMENTATION STATUS: NOT STARTED

NEXT RECOMMENDED STEP: ...

Jika architecture masih memiliki masalah, jangan menyatakan READY.

Tunjukkan masalahnya dan perbaiki dokumentasi terlebih dahulu.

STOP setelah Phase 0 selesai.

Jangan lanjut coding Phase 1 tanpa instruksi berikutnya.

## GIT COMMIT & PUSH

Setelah seluruh pekerjaan Phase 0 selesai dan dokumentasi sudah benar:

1. Periksa git status.
2. Pastikan tidak ada secret, token, API key, password, atau file sensitif yang akan di-commit.
3. Periksa diff seluruh perubahan.
4. Jalankan pemeriksaan yang aman dan relevan terhadap dokumentasi/struktur yang dibuat.
5. Commit seluruh perubahan Phase 0 dengan commit message yang jelas, misalnya:
   docs: complete content pilot phase 0 architecture audit
6. Push commit tersebut langsung ke branch yang sedang digunakan untuk project ini.
7. Setelah push berhasil, verifikasi bahwa commit sudah berada di remote repository.
8. Laporkan commit hash dan branch yang berhasil di-push.

Jangan melakukan push jika terdapat secret atau perubahan yang tidak berkaitan dengan Phase 0.
Jangan membuat commit kosong.
Jangan melakukan force push.

Jika push gagal karena authentication, permission, remote, atau masalah Git lainnya, jangan mengarang bahwa push berhasil. Laporkan error sebenarnya dan hentikan proses setelah pekerjaan lokal aman.

Setelah push berhasil, tampilkan:

GIT STATUS: CLEAN
COMMIT: <commit hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

Kemudian STOP.


````
# CALLBACK CONFIGURATION: NEEDS CONFIGURATION
```

Lanjutkan dari kondisi saat ini.

STATUS SAAT INI:
- FACEBOOK PROVIDER: CONFIGURED
- FACEBOOK OAUTH: READY
- META_APP_ID: terbaca
- META_APP_SECRET: terbaca
- REDIRECT URI: aplikasi sudah menentukan nilai yang benar
- CALLBACK CONFIGURATION: NEEDS CONFIGURATION
- Manual Upload: PASS
- Downloader: PASS
- Media Ready: PASS
- Compose: PASS
- Queue: PASS
- Worker: PASS
- Scheduler: PASS
- Typecheck: PASS
- Lint: PASS
- Test: PASS
- Build: PASS
- Git: CLEAN

Sekarang fokus hanya menyelesaikan CALLBACK CONFIGURATION.

1. Baca source code dan temukan callback/redirect URI OAuth Facebook yang BENAR-BENAR digunakan aplikasi.
2. Jangan membuat callback URL baru jika sudah ada.
3. Tampilkan URL callback final yang digunakan aplikasi tanpa membocorkan secret/token.
4. Pastikan konfigurasi environment menggunakan base URL/domain VPS yang benar.
5. Pastikan redirect URI konsisten antara:
   - frontend
   - backend
   - OAuth route
   - environment
   - Meta OAuth configuration
6. Jangan mengubah flow OAuth yang sudah ada jika sudah benar.
7. Jangan membuat fake OAuth atau fake Facebook success.
8. Jangan meminta saya memasukkan META_APP_ID atau META_APP_SECRET lagi karena keduanya sudah tersedia di .env.
9. Jika yang kurang hanya konfigurasi Meta Developer Dashboard, berikan nilai Redirect URI yang harus saya masukkan ke Valid OAuth Redirect URIs.
10. Setelah konfigurasi lokal siap, lakukan verifikasi route callback dan OAuth flow sejauh yang bisa dilakukan dari VPS.
11. Jangan mengklaim Facebook OAuth berhasil penuh jika belum ada login/authorization nyata.
12. Jangan melakukan perubahan source code yang tidak diperlukan.

Setelah selesai, tampilkan:

FACEBOOK PROVIDER: CONFIGURED
META CREDENTIALS: CONFIGURED
OAUTH ROUTE: PASS/FAIL
REDIRECT URI: <URI AKTUAL>
CALLBACK ROUTE: PASS/FAIL
META DASHBOARD CONFIG: READY/NEEDS MANUAL CONFIGURATION
OAUTH E2E: PASS/NOT RUN
MANUAL UPLOAD: PASS
DOWNLOADER: PASS
TEST: PASS/FAIL
BUILD: PASS/FAIL

Jika hanya membutuhkan pengaturan Meta Dashboard, STOP dan jelaskan tepat satu langkah yang harus saya lakukan di Meta Dashboard.

Jangan commit/push jika tidak ada perubahan code.
````
# 
```
Lanjutkan dari kondisi repository saat ini.

Saya sudah menambahkan:
META_APP_ID
META_APP_SECRET

ke bagian paling bawah file `.env` di VPS baru.

Sekarang fokus hanya pada konfigurasi dan verifikasi Facebook/Meta. JANGAN mengubah architecture atau membuat ulang fitur yang sudah ada.

LANGKAH:

1. Baca `.env` yang sedang digunakan oleh aplikasi.
2. Pastikan `META_APP_ID` terbaca.
3. Pastikan `META_APP_SECRET` terbaca.
4. Jangan pernah menampilkan nilai secret/token ke terminal output, log, laporan, atau Git.
5. Pastikan `.env` masuk `.gitignore` dan tidak akan ikut commit/push.
6. Jangan commit secret apa pun ke GitHub.
7. Cek apakah nama environment variable yang dipakai source code memang:
   META_APP_ID
   META_APP_SECRET
   Jika source code menggunakan nama variable berbeda, sesuaikan konfigurasi dengan code yang sebenarnya, jangan membuat variable duplikat tanpa alasan.
8. Restart/reload service agar environment baru terbaca.
9. Jalankan diagnosis Facebook provider.
10. Pastikan status berubah dari:
    META APP ID: MISSING
    META APP SECRET: MISSING
    menjadi configured/available.
11. Jangan membuat fake credential, fake token, fake Page, atau fake Facebook success.
12. Jangan mengubah kode Facebook yang sudah ada jika sebenarnya masalahnya hanya `.env`.
13. Setelah credential terbaca, lanjutkan konfigurasi OAuth Facebook yang memang sudah tersedia di code.
14. Gunakan flow OAuth resmi yang sudah dibuat oleh project.
15. Jangan menggunakan Facebook username/password automation.
16. Jangan mengarang endpoint atau permission.
17. Jika OAuth membutuhkan redirect/callback URL, tampilkan URL yang BENAR-BENAR digunakan aplikasi dan cek apakah konfigurasi callback tersebut sudah sesuai.
18. Jika ada konfigurasi Meta Developer yang masih kurang, jelaskan tepat apa yang kurang.
19. Jangan berhenti hanya karena Facebook Live Verification belum bisa dilakukan jika credential/API configuration sudah bisa diverifikasi secara lokal.
20. Setelah perubahan konfigurasi selesai, jalankan:
    - typecheck
    - lint
    - test
    - build
    sesuai script yang tersedia di repository.

GIT:

- Jangan commit `.env`.
- Jangan commit secret.
- Jika hanya perubahan environment/config lokal dan tidak ada perubahan source code, TIDAK perlu membuat commit.
- Jangan melakukan commit kosong.
- Jangan push jika tidak ada perubahan code/documentation.
- Jika memang ada perubahan code yang benar-benar diperlukan, periksa diff dan pastikan tidak ada secret sebelum commit/push.
- Jika ada perubahan yang diperlukan, langsung commit dan push ke branch aktif.
- Jangan force push.

LAPORAN AKHIR:

META_APP_ID: CONFIGURED / MISSING
META_APP_SECRET: CONFIGURED / MISSING
FACEBOOK PROVIDER: CONFIGURED / NOT CONFIGURED
FACEBOOK OAUTH: READY / NOT READY
CALLBACK CONFIGURATION: READY / NEEDS CONFIGURATION
MANUAL UPLOAD: PASS / FAIL
DOWNLOADER: PASS / FAIL
MEDIA READY: PASS / FAIL
COMPOSE: PASS / FAIL
QUEUE: PASS / FAIL
WORKER: PASS / FAIL
SCHEDULER: PASS / FAIL
TYPECHECK: PASS / FAIL
LINT: PASS / FAIL
TEST: PASS / FAIL
BUILD: PASS / FAIL

GIT STATUS:
COMMIT:
PUSH STATUS:

Jika semua konfigurasi Meta sudah terbaca, langsung lanjutkan ke langkah berikutnya yang diperlukan untuk menghubungkan Facebook Page melalui OAuth. Jangan bertanya ulang mengenai credential yang sudah saya masukkan.

````
# 
```

LANJUTKAN DI PROJECT CONTENT PILOT.

Hasil audit terakhir SUDAH MEMBUKTIKAN:

FACEBOOK PROVIDER CODE: EXISTS
ENV CONFIG: INCOMPLETE
META APP ID: MISSING
META APP SECRET: MISSING
FACEBOOK PROVIDER: NOT CONFIGURED

Jadi jangan membuat Facebook provider baru dan jangan mengubah architecture/provider implementation.

ROOT CAUSE SEMENTARA:
Source code berasal dari GitHub, sedangkan secret/environment configuration tidak ikut repository. VPS baru belum memiliki konfigurasi Meta/Facebook.

Sekarang fokus hanya pada PEMULIHAN KONFIGURASI ENV di VPS baru.

ATURAN KEAMANAN:
- Jangan pernah menampilkan nilai secret.
- Jangan commit .env.
- Jangan push secret ke GitHub.
- Jangan membuat fake Meta App ID.
- Jangan membuat fake Meta App Secret.
- Jangan membuat fake access token.
- Jangan mengubah source code hanya untuk menghilangkan status provider_not_configured.
- Jangan menganggap Facebook PASS jika credential asli belum tersedia.

LANGKAH:

1. Audit seluruh repository untuk menemukan sumber konfigurasi Meta yang sebenarnya.

Cari:
- .env.example
- environment schema
- config loader
- provider configuration
- Meta/Facebook config
- OAuth config
- deployment config
- Docker/env config
- process manager config

2. Tentukan NAMA ENV VARIABLE yang benar-benar digunakan oleh source code.

Jangan menebak nama variable.

3. Laporkan hanya status:

META_APP_ID: PRESENT / MISSING
META_APP_SECRET: PRESENT / MISSING
META_ACCESS_TOKEN: PRESENT / MISSING
META_REFRESH_TOKEN: PRESENT / MISSING
FACEBOOK_PAGE_TOKEN: PRESENT / MISSING
OAUTH_REDIRECT_URI: PRESENT / MISSING
META_CONFIG: COMPLETE / INCOMPLETE

Jangan tampilkan nilainya.

4. Periksa apakah VPS lama pernah memiliki environment/configuration tersebut.

Jika VPS lama masih dapat diakses, cari konfigurasi environment Meta secara aman.

Jangan menampilkan secret.

5. Jika credential asli tersedia di VPS lama:
- pindahkan ke VPS baru secara aman
- gunakan environment/secret storage yang memang digunakan project
- jangan memasukkannya ke source code
- jangan memasukkannya ke Git

6. Jika credential asli TIDAK tersedia di VPS lama:
STOP dan laporkan credential apa saja yang dibutuhkan.

Jangan membuat credential palsu.

7. Setelah configuration asli tersedia, restart service yang membutuhkan environment tersebut.

8. Jalankan diagnosis ulang.

Target:

FACEBOOK PROVIDER: CONFIGURED

9. Setelah provider configured, verifikasi koneksi Facebook menggunakan credential asli.

10. Jika OAuth/session Page connection membutuhkan login ulang setelah pindah VPS, lakukan flow resmi yang memang digunakan project.

Jangan menggunakan Facebook username/password automation.

11. Setelah configuration berhasil, lakukan test nyata:

WEB
→ Accounts
→ Facebook
→ connection/status
→ Page discovery
→ pilih Page
→ Compose
→ Reels
→ pilih media
→ Publish

12. Jangan hanya menguji API response.

Jika memungkinkan, verifikasi Reel benar-benar muncul di Facebook Page asli.

13. Jangan mengubah fitur yang sudah PASS:

MANUAL UPLOAD
DOWNLOADER
MEDIA READY
COMPOSE
QUEUE
WORKER
SCHEDULER
REGRESSION
TYPECHECK
LINT
TEST
BUILD

14. Jika ternyata credential memang harus dibuat ulang di Meta Developer Console, jangan membuatnya secara otomatis.

Laporkan:
- credential apa yang harus dibuat
- di mana configuration tersebut harus dipasang
- redirect URI yang digunakan source code
- permission yang dibutuhkan source code

Jangan menebak permission atau endpoint.

15. Setelah semuanya selesai, jalankan pemeriksaan lengkap.

FINAL REPORT:

ROOT CAUSE:
...

FACEBOOK PROVIDER CODE:
EXISTS

ENV CONFIG:
COMPLETE / INCOMPLETE

META APP ID:
PRESENT / MISSING

META APP SECRET:
PRESENT / MISSING

META CONFIG:
CONFIGURED / NOT CONFIGURED

FACEBOOK OAUTH:
PASS / NOT RUN / FAIL

PAGE DISCOVERY:
PASS / NOT RUN / FAIL

PAGE CONNECTION:
PASS / NOT RUN / FAIL

FACEBOOK PUBLISH:
PASS / NOT RUN / FAIL

FACEBOOK LIVE VERIFICATION:
PASS / NOT RUN / FAIL

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

MEDIA READY:
PASS / FAIL

COMPOSE:
PASS / FAIL

QUEUE:
PASS / FAIL

WORKER:
PASS / FAIL

SCHEDULER:
PASS / FAIL

REGRESSION:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
...

PUSH:
SUCCESS / NOT NEEDED / FAILED

REMOTE VERIFIED:
YES / NO

STOP setelah laporan.

Jangan membuat perubahan code yang tidak diperlukan.
````
# 
```
LANJUTKAN PROJECT CONTENT PILOT.

Saya menduga masalah Facebook setelah pindah VPS terjadi karena source code diambil dari GitHub, sedangkan file .env/secrets memang tidak ikut repository.

JANGAN langsung mengubah code.

Lakukan diagnosis terlebih dahulu.

1. Audit repository dan pastikan apakah Facebook/Meta provider implementation SUDAH ADA di source code.

2. Cari configuration/env schema yang digunakan project untuk Meta/Facebook.

3. Periksa:
   - .env.example
   - .gitignore
   - config files
   - environment loader
   - deployment configuration
   - process manager configuration
   - provider configuration

4. Jangan pernah menampilkan nilai secret/token.

Tampilkan hanya:

META_APP_ID: PRESENT / MISSING
META_APP_SECRET: PRESENT / MISSING
META_ACCESS_TOKEN: PRESENT / MISSING
META_REFRESH_TOKEN: PRESENT / MISSING
FACEBOOK_CONFIG: PRESENT / MISSING
OAUTH_CONFIG: PRESENT / MISSING
CALLBACK_URL: PRESENT / MISSING
FACEBOOK_PROVIDER_CODE: EXISTS / MISSING

5. Jika Facebook provider code SUDAH ADA tetapi ENV/secret MISSING:

JANGAN membuat implementation baru.

Cari tahu credential/configuration apa yang diperlukan oleh code yang sudah ada.

6. Jika .env.example tersedia, gunakan itu sebagai referensi nama variable yang benar.

7. Jangan membuat .env dari tebakan.

8. Jangan membuat fake:
   - App ID
   - App Secret
   - access token
   - OAuth token
   - Page token

9. Jangan commit .env atau secret ke GitHub.

10. Jika VPS lama masih dapat diakses, periksa konfigurasi environment VPS lama secara aman dan bandingkan dengan VPS baru.

Jangan tampilkan nilai secret.
Hanya laporkan nama variable mana yang ada/hilang.

11. Jika credential Meta memang masih tersedia di VPS lama, pindahkan secara aman ke VPS baru menggunakan mekanisme secret/environment yang benar.

12. Setelah environment lengkap, restart service yang membutuhkan ENV.

13. Verifikasi:

FACEBOOK PROVIDER: CONFIGURED

14. Kemudian test dari WEB UI sebenarnya:

Compose
→ Reels
→ pilih media
→ pilih Facebook Page
→ Publish Now

15. Verifikasi sampai Reel benar-benar muncul di Facebook Page asli.

Jangan menganggap response API saja sebagai success.

16. Pastikan fitur yang sudah PASS tetap PASS:

MANUAL UPLOAD
DOWNLOADER
MEDIA READY
COMPOSE
QUEUE
WORKER
SCHEDULER
REGRESSION
TYPECHECK
LINT
TEST
BUILD

17. Jika ternyata Facebook provider code memang BELUM ADA di repository, jangan langsung membuat implementation besar.

Laporkan:

FACEBOOK PROVIDER CODE: MISSING

dan jelaskan file/module apa yang seharusnya dibuat berdasarkan architecture project.

18. Jika hanya ENV yang hilang, jangan mengubah source code.

19. Jika memang ada perubahan code yang diperlukan, baru lakukan perubahan tersebut dan pastikan tidak ada secret masuk Git.

20. Setelah selesai:

GIT STATUS
COMMIT
PUSH STATUS
REMOTE VERIFIED

Jangan membuat commit kosong.

FINAL REPORT:

ROOT CAUSE:
<penyebab sebenarnya>

FACEBOOK PROVIDER CODE:
EXISTS / MISSING

ENV CONFIG:
COMPLETE / INCOMPLETE

META APP ID:
PRESENT / MISSING

META APP SECRET:
PRESENT / MISSING

FACEBOOK PROVIDER:
CONFIGURED / NOT CONFIGURED

OAUTH:
PASS / NOT RUN / FAIL

PAGE CONNECTION:
PASS / NOT RUN / FAIL

FACEBOOK PUBLISH:
PASS / NOT RUN / FAIL

FACEBOOK LIVE VERIFICATION:
PASS / NOT RUN / FAIL

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

MEDIA READY:
PASS / FAIL

COMPOSE:
PASS / FAIL

QUEUE:
PASS / FAIL

WORKER:
PASS / FAIL

SCHEDULER:
PASS / FAIL

REGRESSION:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

PUSH:
SUCCESS / NOT NEEDED / FAILED

STOP setelah laporan.

````
# 
```
LANJUTKAN PROJECT CONTENT PILOT DARI KONDISI TERAKHIR.

HASIL VERIFIKASI TERAKHIR:

- REGRESSION: PASS
- TYPECHECK: PASS
- LINT: PASS
- TEST: PASS (261 tests)
- BUILD: PASS
- SCHEDULER: PASS
- GIT STATUS: CLEAN
- PUSH STATUS: SUCCESS
- REMOTE VERIFIED: YES

MASALAH YANG TERSISA HANYA FACEBOOK PROVIDER DI VPS BARU.

HASIL TERAKHIR:

FACEBOOK PUBLISH:
FAIL (honest) — META_APP_ID/META_APP_SECRET tidak tersedia di VPS baru.
Provider dengan benar mengembalikan provider_not_configured.
Job TIDAK fake-published.

FACEBOOK LIVE VERIFICATION:
NOT RUN — membutuhkan credential Meta asli dan OAuth login ke Page asli.

JANGAN MENGUBAH CODE FACEBOOK PUBLISHING YANG SUDAH BENAR HANYA UNTUK MEMBUAT TEST PASS.

==================================================
TUJUAN
==================================================

Pulihkan konfigurasi Meta/Facebook pada VPS baru menggunakan configuration/secrets yang benar, TANPA mengekspos secret dan TANPA mengubah architecture.

Tujuannya:

VPS baru
→ Meta configuration tersedia
→ Facebook OAuth dapat digunakan
→ Page connection tersedia
→ Facebook provider dapat berjalan
→ Publish Now dari Web UI
→ Queue
→ Worker
→ Facebook Graph API
→ published
→ verifikasi Reel pada Page asli.

==================================================
STEP 1 — AUDIT CONFIGURATION
==================================================

Periksa repository dan environment untuk mengetahui:

- nama variable Meta App ID yang sebenarnya
- nama variable Meta App Secret yang sebenarnya
- OAuth configuration
- callback URL
- Page connection configuration
- token storage
- encryption configuration
- application URL
- frontend URL
- backend URL

JANGAN mengarang nama environment variable.

Gunakan nama variable yang memang digunakan oleh source code.

JANGAN print value secret ke terminal.

Yang boleh ditampilkan hanya:

META_APP_ID: PRESENT / MISSING
META_APP_SECRET: PRESENT / MISSING
OAUTH CONFIG: PRESENT / MISSING
CALLBACK CONFIG: PRESENT / MISSING
PAGE AUTH: PRESENT / MISSING

Jangan pernah menampilkan nilai token/secret.

==================================================
STEP 2 — BEDAKAN CODE VS ENVIRONMENT
==================================================

Pastikan provider Facebook tidak rusak.

Periksa source code untuk memastikan:

- missing Meta configuration menghasilkan provider_not_configured
- tidak ada fake publish
- tidak ada fake success
- tidak ada hardcoded credential
- error tetap honest
- existing tests tetap valid

Jika code sudah benar:

JANGAN ubah code hanya untuk menghilangkan FAIL.

Masalah utama adalah environment VPS baru.

==================================================
STEP 3 — RESTORE ENVIRONMENT
==================================================

Konfigurasikan environment VPS baru sesuai configuration project.

Jika secret tersedia melalui deployment/environment yang sah, gunakan secret tersebut.

JANGAN:

- commit secret
- menulis secret ke source code
- menulis secret ke README
- menulis secret ke test fixture
- menampilkan secret di output
- membuat fake META_APP_ID
- membuat fake META_APP_SECRET

Pastikan `.env`/secret storage tetap berada di luar Git sesuai architecture project.

==================================================
STEP 4 — OAUTH CONFIGURATION
==================================================

Pastikan OAuth configuration menggunakan URL VPS baru yang benar.

Periksa:

- OAuth authorize URL
- callback URL
- application base URL
- backend callback URL
- redirect URI
- allowed origins jika memang digunakan

Jangan mengubah callback secara sembarangan.

Jika callback URL harus didaftarkan di Meta App Dashboard dan tidak dapat diubah hanya dari VPS:

laporkan dengan jelas konfigurasi apa yang perlu disesuaikan.

Jangan mengarang bahwa OAuth berhasil jika belum benar-benar dicoba.

==================================================
STEP 5 — RESTART APPLICATION
==================================================

Setelah environment diperbaiki:

restart component yang membutuhkan environment:

- API/backend
- worker
- scheduler
- frontend jika diperlukan

Pastikan process benar-benar membaca environment terbaru.

Jangan hanya restart frontend jika credential digunakan backend/worker.

==================================================
STEP 6 — PROVIDER HEALTH CHECK
==================================================

Verifikasi provider Facebook.

Target:

META CONFIG:
PASS

FACEBOOK PROVIDER:
CONFIGURED

Provider tidak boleh lagi:

provider_not_configured

jika semua configuration memang tersedia.

==================================================
STEP 7 — WEB OAUTH TEST
==================================================

Gunakan Web UI sebenarnya.

Flow:

Accounts
→ Facebook
→ Connect Account
→ OAuth
→ login/authorization Meta
→ callback ke VPS baru
→ token tersimpan aman
→ connection berhasil
→ Page dapat ditemukan

Jangan menggunakan Facebook username/password automation.

Gunakan OAuth resmi.

Jika Meta meminta App Review/permission tertentu:

catat permission yang diminta dan statusnya.

==================================================
STEP 8 — PAGE DESTINATION
==================================================

Setelah OAuth berhasil:

ambil Page/destination melalui flow provider yang sudah ada.

Pastikan:

- Page ditemukan
- Page ID tersimpan
- connection valid
- token tidak ditampilkan
- destination dapat dipilih dari Compose

Jangan hardcode Page ID.

==================================================
STEP 9 — REAL WEB PUBLISH TEST
==================================================

Lakukan test nyata melalui browser:

Compose
→ Reels
→ pilih media READY
→ pilih Facebook Page
→ isi caption
→ Publish Now

Pastikan:

UI
→ API
→ Queue
→ Worker
→ Facebook Provider
→ Graph API
→ published

Jangan langsung menganggap publish berhasil berdasarkan response internal.

==================================================
STEP 10 — FACEBOOK VERIFICATION
==================================================

Setelah publish:

verifikasi status melalui API yang memang digunakan project.

Pastikan hasil nyata:

publish_status = published

dan jika provider mengembalikan video/reel status:

video/reel status = ready

Kemudian verifikasi Reel benar-benar tersedia pada Page asli.

Catat ID/permalink yang aman untuk dilaporkan.

Jangan menampilkan access token.

==================================================
STEP 11 — REGRESSION
==================================================

Setelah credential diperbaiki, jalankan kembali:

- manual upload
- downloader
- media READY
- compose
- queue
- worker
- scheduler
- Facebook publish
- Facebook regression
- typecheck
- lint
- test
- build

Jangan menghapus test yang sebelumnya PASS.

Target tidak boleh hanya Facebook PASS.

Semua regression harus tetap PASS.

==================================================
STEP 12 — JIKA CREDENTIAL TIDAK DAPAT DIPULIHKAN
==================================================

Jika credential Meta asli memang tidak tersedia di VPS baru:

JANGAN membuat fake credential.

JANGAN fake OAuth.

JANGAN fake Facebook publish.

JANGAN mengubah test agar PASS.

JANGAN mengklaim Facebook LIVE VERIFICATION PASS.

Sebaliknya:

- pertahankan provider_not_configured yang honest
- pastikan semua bagian lain tetap PASS
- laporkan tepat configuration apa yang hilang
- jangan commit secret
- jangan melakukan perubahan code yang tidak diperlukan

==================================================
STEP 13 — GIT
==================================================

Jika hanya perubahan environment/secrets:

JANGAN commit secret.

Jika tidak ada perubahan source code:

jangan membuat commit kosong.

Jika memang ada perubahan code yang diperlukan dan aman:

- git status
- inspect diff
- pastikan tidak ada secret
- commit
- push
- verify remote

Jangan force push.

==================================================
FINAL REPORT
==================================================

Tampilkan:

META APP CONFIG:
PASS / MISSING

OAUTH CONFIG:
PASS / MISSING

FACEBOOK PROVIDER:
PASS / NOT CONFIGURED

FACEBOOK OAUTH:
PASS / NOT RUN

PAGE CONNECTION:
PASS / NOT RUN

PAGE DESTINATION:
PASS / NOT RUN

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

MEDIA READY:
PASS / FAIL

COMPOSE:
PASS / FAIL

QUEUE:
PASS / FAIL

WORKER:
PASS / FAIL

SCHEDULER:
PASS / FAIL

FACEBOOK PUBLISH:
PASS / FAIL / NOT RUN

FACEBOOK LIVE VERIFICATION:
PASS / FAIL / NOT RUN

REGRESSION:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash atau NONE>

PUSH STATUS:
SUCCESS / NOT NEEDED / FAILED

REMOTE VERIFIED:
YES / NO

==================================================
STOP CONDITION
==================================================

Jika Facebook credential asli berhasil dipasang dan Facebook Web E2E berhasil:

STOP setelah semua regression PASS dan push berhasil.

Jika credential Meta tidak tersedia:

STOP setelah diagnosis lengkap.

JANGAN membuat fake credential atau fake Facebook success.

Masalah saat ini adalah environment VPS baru, bukan alasan untuk membongkar architecture atau publishing flow yang sudah PASS.


````
# 
```
LANJUTKAN PROJECT CONTENT PILOT.

Jangan mulai dari nol.
Jangan membuat ulang fitur publishing yang sudah PASS.
Jangan melakukan refactor besar yang tidak diperlukan.

MASALAH SAAT INI:
Project sebelumnya sudah berhasil melewati banyak test:

- manual video upload: PASS
- downloader ingestion: PASS
- media pipeline: PASS
- media ready guard: PASS
- compose: PASS
- queue: PASS
- worker: PASS
- scheduler: PASS
- Facebook Reels: PASS
- Facebook live verification: PASS
- regression: PASS
- typecheck: PASS
- lint: PASS
- build: PASS
- Git clean / remote verified pada sesi sebelumnya

Tetapi setelah pindah VPS, Web E2E tidak dapat dijalankan karena environment VPS baru tidak lengkap.

Hasil sebelumnya secara eksplisit menunjukkan:

WEB E2E: NOT RUN

Alasan:
- PostgreSQL belum tersedia/terhubung
- Redis belum tersedia/terhubung
- MinIO belum tersedia/terhubung
- konfigurasi environment tertentu belum tersedia, termasuk META_APP_ID
- environment VPS baru belum sama dengan environment yang diperlukan untuk menjalankan Web E2E secara penuh

JANGAN menganggap ini sebagai bug pada publishing flow sebelum environment diverifikasi.

==================================================
TUJUAN SESI INI
==================================================

Perbaiki environment VPS baru sampai Web E2E dapat dijalankan.

Setelah environment siap:

1. jalankan aplikasi
2. jalankan Web E2E dari browser/web
3. test manual upload melalui UI
4. test downloader melalui UI
5. test media menjadi READY
6. test Compose
7. test Publish Now
8. test Queue
9. test Worker
10. test Facebook publishing
11. verifikasi Reel benar-benar muncul di Facebook Page
12. test Schedule jika environment mendukung
13. test failure handling
14. jalankan regression
15. typecheck
16. lint
17. test
18. build
19. git status
20. commit
21. push
22. verifikasi remote

==================================================
ATURAN PENTING
==================================================

JANGAN tanya saya soal kredit Kiro.

JANGAN berhenti untuk meminta konfirmasi yang sebenarnya bisa ditentukan dari repository atau environment.

LANGSUNG lanjutkan diagnosis → perbaikan → test → commit → push.

Namun:

- jangan mengarang hasil test
- jangan menganggap service berhasil hanya karena process berjalan
- jangan membuat fake success
- jangan mematikan test hanya agar PASS
- jangan skip Web E2E
- jangan menghapus regression test
- jangan mengubah Facebook publishing flow yang sudah PASS kecuali memang ditemukan bug nyata
- jangan mengganti architecture
- jangan membuat provider baru
- jangan membuat fitur baru yang tidak berhubungan dengan masalah VPS

==================================================
STEP 1 — AUDIT VPS BARU
==================================================

Periksa environment aktual.

Audit:

- OS
- Node.js
- npm/pnpm/yarn
- package manager
- Docker
- Docker Compose
- PostgreSQL
- Redis
- MinIO
- network
- port
- process/service manager
- environment variables
- .env files
- application configuration
- database connection
- Redis connection
- object storage connection
- Facebook/Meta configuration

Cari juga bagaimana project sebenarnya menjalankan:

- frontend
- backend/API
- worker
- scheduler
- database
- Redis
- MinIO

Jangan langsung install sesuatu sebelum memeriksa repository dan konfigurasi existing.

==================================================
STEP 2 — BANDINKAN DENGAN PROJECT
==================================================

Baca:

- README
- package.json
- docker-compose files jika ada
- Dockerfile jika ada
- .env.example
- config files
- test setup
- E2E configuration
- database configuration
- Redis configuration
- MinIO/S3 configuration
- worker configuration
- scheduler configuration

Cari semua environment variable yang benar-benar dibutuhkan.

Jangan mengarang nama variable.

Buat daftar:

REQUIRED
OPTIONAL
MISSING
INVALID
PRESENT

==================================================
STEP 3 — RESTORE DEPENDENCIES VPS
==================================================

Jika PostgreSQL, Redis, atau MinIO memang merupakan dependency project:

pastikan service tersebut tersedia dan benar-benar usable.

Jika project menggunakan Docker Compose:

gunakan konfigurasi existing project.

Jangan membuat stack kedua yang duplicate.

Jika project memang menggunakan service native:

gunakan service native sesuai architecture existing.

Pastikan:

PostgreSQL:
- running
- reachable
- database tersedia
- credentials benar
- migration/schema tersedia

Redis:
- running
- reachable
- queue dapat digunakan

MinIO/S3:
- running
- bucket tersedia
- credential benar
- application dapat upload/download object

Jangan hanya memeriksa `docker ps`.

Lakukan connection test nyata dari application/runtime.

==================================================
STEP 4 — ENVIRONMENT VARIABLES
==================================================

Audit seluruh environment variable.

Jangan copy secret secara sembarangan.

Jangan print:

- access token
- refresh token
- password
- API key
- secret
- encryption key

ke output terminal/report.

Pastikan configuration yang dibutuhkan Web E2E tersedia.

Termasuk jika memang diwajibkan oleh project:

- META_APP_ID
- Meta/Facebook configuration
- database URL
- Redis URL
- S3/MinIO endpoint
- storage credentials
- application URL
- worker configuration

Jika ada variable yang memang tidak diperlukan untuk test tertentu, jangan membuat fake value hanya untuk membuat test lewat.

Jika Meta configuration memang dibutuhkan untuk Facebook live verification, gunakan configuration yang benar dari environment existing/project.

==================================================
STEP 5 — DATABASE
==================================================

Jangan membuat database baru secara membabi buta jika database existing dapat digunakan.

Periksa migration.

Jalankan migration yang memang diwajibkan project.

Pastikan schema sesuai dengan code.

Jalankan database health check.

Pastikan tidak ada:

- missing table
- missing column
- migration mismatch
- connection failure

Jika ada data existing yang diperlukan untuk test, jangan menghapusnya sembarangan.

==================================================
STEP 6 — STORAGE / MINIO
==================================================

Pastikan media pipeline benar-benar dapat:

upload
→ store
→ retrieve
→ finalize
→ mark READY

Test object storage dari application.

Pastikan Web UI tidak hanya menampilkan file dari mock/local array.

Media harus benar-benar melewati storage flow yang digunakan production architecture.

==================================================
STEP 7 — START FULL STACK
==================================================

Jalankan seluruh component yang diperlukan:

Frontend
Backend/API
Worker
Scheduler
PostgreSQL
Redis
MinIO/S3

Pastikan tidak ada component yang hanya berjalan sebagian.

Periksa log.

Jika ada crash/restart loop, perbaiki sebelum Web E2E.

==================================================
STEP 8 — WEB E2E
==================================================

Sekarang WAJIB jalankan Web E2E.

Jangan lagi menulis:

WEB E2E: NOT RUN

Target:

WEB E2E: PASS

Test melalui web UI sebenarnya, bukan hanya API.

==================================================
STEP 9 — TEST MANUAL UPLOAD
==================================================

Dari browser:

Compose
→ Reels/video
→ pilih Upload Manual
→ pilih file video lokal
→ upload
→ tunggu upload selesai
→ finalize
→ pastikan media berubah menjadi READY
→ pilih media di Compose

Pastikan file upload manual benar-benar berasal dari browser/device.

Jangan hanya memilih media yang sudah ada di library.

Pastikan flow:

browser
→ upload endpoint
→ storage
→ finalize
→ media READY
→ compose picker

berfungsi.

==================================================
STEP 10 — TEST DOWNLOADER
==================================================

Test downloader dari UI menggunakan downloader yang memang sudah ada.

Flow:

Downloader
→ input URL/source yang valid
→ download
→ ingest media
→ storage
→ finalize
→ READY
→ muncul di Compose

Pastikan media dari downloader dapat dipakai oleh Compose.

==================================================
STEP 11 — REGRESSION MEDIA GUARD
==================================================

Pastikan media yang belum finalized tidak muncul sebagai READY.

Test:

upload sedang berlangsung
→ media tidak boleh dianggap READY

finalize berhasil
→ media menjadi READY

file invalid/non-video
→ status failed
→ tidak boleh muncul sebagai READY

Jangan mengubah behavior guard yang sudah PASS kecuali test nyata menemukan regression.

==================================================
STEP 12 — COMPOSE
==================================================

Dari web:

pilih media READY
→ pilih content type Reels
→ isi caption
→ pilih Facebook Page
→ Publish Now

Pastikan UI mengirim media ID yang benar.

Jangan menggunakan hardcoded media ID.

==================================================
STEP 13 — PUBLISH NOW
==================================================

Test publishing melalui web UI.

Flow wajib:

Compose
→ Publish Now
→ API
→ Queue
→ Worker
→ Facebook provider
→ Facebook Graph API
→ published

Pastikan UI menampilkan status yang sebenarnya.

Jangan mengubah status menjadi published sebelum worker/provider benar-benar berhasil.

==================================================
STEP 14 — FACEBOOK VERIFICATION
==================================================

Setelah publish:

verifikasi melalui Graph API sesuai flow project.

Pastikan:

publish_status = published
video_status = ready

Kemudian verifikasi dari Facebook Page yang sebenarnya.

Pastikan Reel benar-benar muncul.

Catat:

- external ID
- status
- permalink jika tersedia

Jangan menganggap HTTP success saja sebagai bukti publishing berhasil.

==================================================
STEP 15 — QUEUE / WORKER
==================================================

Pastikan:

Compose
→ queue job
→ worker mengambil job
→ processing
→ publishing
→ terminal status

Tidak boleh ada orphan job.

Test jika memungkinkan:

- successful job
- temporary failure
- retry
- permanent failure
- cancellation

Jangan merusak retry/cancel logic yang sudah PASS.

==================================================
STEP 16 — SCHEDULER
==================================================

Karena environment VPS sekarang sedang diperbaiki, jalankan Web E2E scheduler jika dependency tersedia.

Test:

Compose
→ Schedule
→ create schedule
→ queue/scheduler
→ worker
→ publish

Pastikan scheduler menggunakan timezone yang benar.

Pastikan job yang sudah expired tidak dieksekusi ulang secara salah.

Jika Facebook live verification untuk scheduled publishing membutuhkan credential yang tidak tersedia, laporkan secara jelas dan tetap test seluruh scheduler flow sampai titik yang dapat diverifikasi.

Jangan mengarang Facebook live result.

==================================================
STEP 17 — RUN FULL TEST SUITE
==================================================

Setelah Web E2E berhasil, jalankan test suite lengkap yang tersedia.

Minimal:

- typecheck
- lint
- unit tests
- API tests
- worker tests
- queue tests
- scheduler tests
- media tests
- regression tests
- Web E2E
- build

Jangan skip test yang sebelumnya PASS.

==================================================
STEP 18 — CHECK REGRESSION
==================================================

Pastikan perbaikan environment tidak mengubah:

- manual upload
- downloader
- media finalize
- media READY guard
- compose
- queue
- worker
- retry
- cancel
- scheduler
- Facebook Reels
- Facebook post/video flow
- existing API
- existing UI

Jika ada regression, perbaiki sebelum commit.

==================================================
STEP 19 — GIT
==================================================

Setelah semuanya PASS:

git status

Periksa seluruh diff.

Pastikan tidak ada:

- .env
- secret
- token
- password
- private key
- credentials
- generated sensitive file

yang masuk commit.

Jika perubahan hanya berupa environment/deployment configuration yang memang aman untuk repository, commit sesuai kebutuhan.

Jangan commit secret.

==================================================
STEP 20 — COMMIT
==================================================

Commit perubahan dengan message yang jelas, misalnya:

fix: restore web e2e environment on new vps

Jika perubahan code juga diperlukan:

gunakan commit message yang sesuai dengan perubahan sebenarnya.

Jangan membuat commit kosong.

==================================================
STEP 21 — PUSH
==================================================

Langsung push ke branch yang sedang digunakan.

Jangan force push.

Setelah push:

- cek remote
- pastikan HEAD sama dengan origin branch
- pastikan commit benar-benar sudah berada di remote

Jika push gagal:

JANGAN mengatakan SUCCESS.

Tampilkan error Git sebenarnya dan berhenti setelah local state aman.

==================================================
FINAL REPORT
==================================================

Tampilkan laporan ringkas:

VPS ENVIRONMENT:
PASS / FAIL

POSTGRESQL:
PASS / FAIL

REDIS:
PASS / FAIL

MINIO / STORAGE:
PASS / FAIL

ENVIRONMENT CONFIG:
PASS / FAIL

APPLICATION:
PASS / FAIL

WEB E2E:
PASS / FAIL

MANUAL UPLOAD:
PASS / FAIL

DOWNLOADER:
PASS / FAIL

MEDIA READY:
PASS / FAIL

COMPOSE:
PASS / FAIL

QUEUE:
PASS / FAIL

WORKER:
PASS / FAIL

FACEBOOK PUBLISH:
PASS / FAIL

FACEBOOK LIVE VERIFICATION:
PASS / FAIL

SCHEDULER:
PASS / FAIL

REGRESSION:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

Jika semuanya berhasil:

STOP setelah push.

Jangan lanjut membuat fitur baru.

==================================================
KONDISI SUKSES UTAMA
==================================================

Masalah utama sesi ini adalah:

"Setelah pindah VPS, Web E2E tidak bisa dijalankan karena environment dependency belum lengkap."

Jadi jangan hanya memperbaiki code.

Yang harus dibuktikan adalah:

VPS baru
→ semua dependency aktif
→ application aktif
→ browser dapat membuka web
→ manual upload bekerja
→ downloader bekerja
→ media READY
→ Compose bekerja
→ Queue bekerja
→ Worker bekerja
→ Facebook publish bekerja
→ Facebook Reel terverifikasi
→ Web E2E PASS
→ regression PASS
→ build PASS
→ commit
→ push

Jangan berhenti pada "service sudah running".

Harus dibuktikan melalui test nyata.

````
# Prompt berikutnya — Facebook Video & Post
```
Prompt: Facebook Publishing Capabilities — Video & Post

Lanjutkan project Content Pilot dari repository TERKINI.

Scheduler, Queue, Worker, Manual Upload, Downloader, Media Pipeline, Compose, dan Facebook Reels SUDAH PASS dan SUDAH DI-PUSH.

JANGAN mengulang atau merombak fitur tersebut.

TARGET SEKARANG:

Tambahkan publishing capability Facebook berikut secara modular:

1. Facebook Page Video
2. Facebook Page Photo/Text Post jika API dan architecture existing mendukungnya

PRINSIP:

- Facebook tetap provider/module, bukan core.
- Jangan membuat queue baru.
- Jangan membuat worker baru.
- Jangan membuat scheduler baru.
- Gunakan PublishingJob, Queue Manager, Worker, Media Pipeline, History, dan authorization existing.
- Reels flow yang sudah PASS tidak boleh rusak.
- Jangan membuat fake success.
- Jangan mengarang endpoint atau permission Facebook.

SEBELUM CODING:

Audit implementation Facebook existing dan gunakan abstraction yang sudah ada.

Periksa capability provider existing.

Pastikan Video dan Post ditambahkan sebagai capability/module baru tanpa merusak:

- Reels
- Upload
- Downloader
- Queue
- Worker
- Retry
- Cancel
- Scheduler

IMPLEMENTASI:

### Facebook Page Video

Flow:

Media READY
→ Compose pilih Video
→ pilih Facebook Page
→ caption
→ Publish Now / Schedule
→ PublishingJob
→ Queue Manager
→ Worker
→ Facebook Provider
→ upload/publish
→ status verification
→ History

Gunakan media pipeline existing.

### Facebook Photo/Text Post

Jika API resmi dan permission yang digunakan environment ini mendukung:

Implement capability secara modular.

Jika belum dapat diverifikasi:
JANGAN memaksakan implementation.

Tandai:

UNSUPPORTED / NEEDS VERIFICATION

dan lanjutkan fitur yang benar-benar dapat diverifikasi.

WEB UI:

Compose harus menampilkan content type berdasarkan capability Facebook yang benar-benar tersedia.

Jangan menampilkan fitur yang belum aktif seolah-olah aktif.

Untuk Video:

- media picker
- caption
- destination
- Publish now
- Schedule
- validation
- error state

Gunakan UI existing.

TEST:

Minimal:

1. Facebook Video manual upload
2. Facebook Video publish now
3. Facebook Video scheduled publish
4. Facebook Video invalid media
5. authorization regression
6. queue regression
7. worker regression
8. retry regression
9. cancel regression
10. scheduler regression
11. Facebook Reels regression
12. downloader regression
13. media pipeline regression
14. history regression
15. typecheck
16. lint
17. full test
18. build

REAL WEB E2E:

Gunakan video test baru.

Compose melalui WEB
→ pilih Facebook Video
→ pilih Page Yourdreels
→ upload/select media
→ caption "Content Pilot Facebook Video Test"
→ Publish Now

Verifikasi:

- job masuk queue
- worker memproses
- Facebook publish berhasil
- Graph API status benar
- video benar-benar muncul di Page
- History benar
- tidak duplicate

Setelah itu lakukan scheduled test jika aman.

Jangan menganggap response API saja sebagai bukti.

REGRESSION:

Pastikan Facebook Reels tetap benar-benar bekerja.

Jika ada failure:
DEBUG dan FIX.

Jangan menghapus test.

Jangan melemahkan validation.

Jangan mengubah status menjadi PASS tanpa test nyata.

GIT:

Setelah semua PASS:

git status
git diff
cek secret

Commit:

feat: add facebook video publishing

Push ke branch aktif.

Jangan force push.

Verifikasi:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

FINAL REPORT:

FACEBOOK VIDEO: PASS/FAIL
FACEBOOK POST: PASS/FAIL/NOT SUPPORTED
SCHEDULED VIDEO: PASS/FAIL
WEB E2E: PASS/FAIL
FACEBOOK LIVE: PASS/FAIL
REELS REGRESSION: PASS/FAIL
QUEUE: PASS/FAIL
WORKER: PASS/FAIL
SCHEDULER: PASS/FAIL
REGRESSION: PASS/FAIL
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL

STOP setelah push berhasil.

````
# Prompt: Scheduler & Scheduled Publishing
```
Lanjutkan project Content Pilot dari kondisi repository TERKINI.

JANGAN mengulang audit dari awal dan JANGAN merusak fitur yang sudah PASS.

STATUS TERKINI YANG SUDAH DIVERIFIKASI:

- Shared Upload Flow: PASS
- Manual Video Upload: PASS
- Downloader Ingestion: PASS
- Invalid File Validation: PASS
- Media Ready Guard: PASS
- Compose: PASS
- Facebook Reels: PASS
- Web Manual Upload: PASS
- Downloader → Web: PASS
- Web Downloader Publish: VERIFIED
- Queue Manager API: PASS
- Worker Integration: PASS
- Retry temporary-only: PASS
- Permanent retry ditolak: PASS
- Cancel: PASS
- User Authorization: PASS
- Facebook Reels Regression: PASS
- Typecheck: PASS
- Lint: PASS
- Tests: PASS
- Build: PASS
- Git repository clean
- Remote sudah verified

JANGAN mengubah flow publishing Facebook yang sudah PASS kecuali benar-benar diperlukan untuk integrasi Scheduler.

==================================================
TARGET PHASE
==================================================

Sekarang implementasikan:

SCHEDULER + SCHEDULED PUBLISHING

Tujuan:

User dapat membuat publishing job untuk waktu tertentu.

Flow:

Compose
→ pilih media
→ pilih destination
→ pilih "Schedule"
→ pilih tanggal & waktu
→ create scheduled job
→ job masuk status scheduled
→ scheduler menunggu waktu eksekusi
→ job masuk queue
→ worker menjalankan publishing
→ Facebook publish
→ status menjadi published / failed

Scheduler harus menggunakan Queue Manager dan Worker yang SUDAH ADA.

Jangan membuat sistem queue kedua.

Jangan membuat worker kedua.

==================================================
ATURAN ARSITEKTUR
==================================================

Scheduler harus tetap platform-independent.

Jangan membuat:

facebookScheduler

Gunakan:

Scheduler
→ PublishingJob
→ Queue
→ Worker
→ Provider

Contoh:

Schedule
  ↓
PublishingJob
  ↓
Scheduler
  ↓
Queue
  ↓
Worker
  ↓
Facebook Provider
  ↓
Published

Core Scheduler tidak boleh berisi logic Facebook API.

==================================================
SCHEDULE MODEL
==================================================

Gunakan model schedule yang sesuai dengan database yang SUDAH ADA.

Jangan membuat database baru.

Schedule minimal harus memiliki konsep:

- id
- publishing job id / relation
- scheduledAt
- status
- createdAt
- updatedAt

Status minimal:

scheduled
processing
published
failed
cancelled

Jika architecture existing sudah mempunyai field/model yang ekuivalen, gunakan yang sudah ada daripada membuat duplicate.

Timezone harus diperhatikan.

Jangan menyimpan waktu tanpa timezone jika architecture existing dapat menyimpan timezone/UTC dengan benar.

Gunakan UTC untuk persistence jika itu sesuai dengan architecture existing, lalu lakukan conversion hanya pada UI.

==================================================
SCHEDULE API
==================================================

Audit API existing terlebih dahulu.

Implement endpoint/service untuk:

1. Create scheduled publishing job
2. List scheduled jobs
3. Get scheduled job
4. Cancel scheduled job

Jangan membuat duplicate endpoint jika endpoint yang sama sudah tersedia.

Authorization WAJIB:

User hanya boleh melihat/mengubah schedule miliknya sendiri.

Jangan memperbolehkan user mengakses job milik user lain hanya dengan mengetahui ID.

==================================================
VALIDATION
==================================================

Scheduler wajib menolak:

- waktu schedule yang sudah lewat
- media yang belum READY
- media invalid
- destination invalid
- destination yang tidak dimiliki user
- publishing job yang sudah published
- publishing job yang sudah cancelled
- schedule duplicate yang tidak valid

Gunakan error yang jelas.

Jangan tampilkan raw provider error kepada user.

==================================================
QUEUE INTEGRATION
==================================================

Scheduler tidak boleh langsung melakukan Facebook publish.

Ketika scheduledAt tercapai:

scheduled job
→ enqueue existing PublishingJob
→ worker existing memproses
→ provider existing publish

Pastikan tidak terjadi double execution.

Jika scheduler restart:

scheduled job yang belum waktunya tetap harus aman.

Jika scheduler restart setelah waktunya lewat:

job yang valid harus dapat diproses dan tidak hilang.

Jika job sudah queued/processing/published:

scheduler tidak boleh memasukkannya lagi.

Gunakan idempotency / atomic state transition sesuai architecture existing.

==================================================
CANCEL
==================================================

User dapat cancel scheduled job sebelum execution.

Flow:

scheduled
→ cancelled

Setelah job sudah:

processing
atau
published

jangan izinkan cancellation seolah-olah masih scheduled.

Return error yang jelas.

==================================================
SCHEDULER WORKER
==================================================

Gunakan mekanisme scheduler yang sesuai dengan stack existing.

Jangan menambahkan dependency besar jika tidak diperlukan.

Scheduler harus:

- menemukan scheduled jobs yang waktunya sudah tiba
- melakukan atomic claim
- enqueue ke queue existing
- mencegah duplicate enqueue
- aman ketika process restart
- aman ketika ada lebih dari satu scheduler instance jika architecture memungkinkan

Jangan menggunakan setTimeout sederhana sebagai satu-satunya persistence mechanism.

Jangan membuat scheduler yang kehilangan job ketika process restart.

==================================================
COMPOSE UI
==================================================

Perbaiki Compose agar Schedule benar-benar berfungsi.

UI harus memiliki:

Content Type
Media
Caption
Destinations

Publish mode:

( ) Publish now
( ) Schedule

Jika Schedule dipilih:

Date
Time
Timezone

Button:

Schedule Post

Jangan menampilkan fake success.

Jika backend gagal:

tampilkan error sebenarnya dalam bentuk aman.

Jika berhasil:

tampilkan:

Scheduled successfully

dan schedule ID/status jika UI existing memang menampilkan metadata tersebut.

==================================================
SCHEDULED PAGE
==================================================

Jika route/page Scheduler sudah ada, gunakan dan perbaiki.

Jika belum ada, buat halaman Scheduler yang minimal tetapi benar-benar terhubung backend.

Tampilkan:

- scheduled content
- destination
- scheduled time
- status
- cancel action

Status:

Scheduled
Processing
Published
Failed
Cancelled

Jangan membuat halaman mock.

Semua data harus berasal dari API/database sebenarnya.

==================================================
DASHBOARD / QUEUE
==================================================

Integrasikan scheduler dengan UI existing.

Dashboard/Queue harus membedakan:

Scheduled
Queued
Processing
Published
Failed
Cancelled

Jangan mengubah statistik existing yang sudah PASS kecuali memang diperlukan.

==================================================
HISTORY
==================================================

Pastikan scheduled publishing yang akhirnya published/failed masuk ke history existing.

Jangan membuat history system kedua.

Status harus konsisten:

scheduled
→ queued
→ processing
→ published

atau:

scheduled
→ queued
→ processing
→ failed

==================================================
RETRY
==================================================

Jangan membuat retry mechanism baru.

Gunakan retry system yang sudah PASS.

Scheduled job yang gagal setelah execution harus mengikuti retry behavior existing.

Permanent error tetap tidak boleh retry permanen.

==================================================
TESTING
==================================================

WAJIB jalankan test setelah implementasi.

Minimal test:

1. Create schedule
2. Schedule future job
3. Reject past schedule
4. Reject invalid media
5. Reject unauthorized destination
6. List user's schedules
7. Get schedule
8. Cancel scheduled job
9. Cannot cancel published job
10. Scheduler detects due job
11. Due job enters existing queue
12. No duplicate enqueue
13. Worker publishes scheduled Facebook Reel
14. Scheduled job becomes published
15. Failed scheduled job becomes failed
16. Restart/recovery behavior
17. Authorization regression
18. Existing queue regression
19. Existing upload regression
20. Existing Facebook Reels regression

Jalankan:

- typecheck
- lint
- test
- build

Jika test existing gagal karena perubahan Scheduler:

DEBUG dan FIX.

Jangan menghapus test hanya supaya PASS.

==================================================
REAL END-TO-END TEST
==================================================

Setelah unit/integration tests PASS, lakukan test nyata melalui WEB.

Gunakan media yang sudah tersedia/READY.

Flow:

1. Buka Compose lewat web.
2. Pilih media.
3. Pilih Facebook Page Yourdreels.
4. Pilih Schedule.
5. Set waktu dekat yang aman untuk test.
6. Submit.
7. Verifikasi job muncul sebagai Scheduled.
8. Tunggu scheduler mengeksekusi.
9. Verifikasi masuk queue.
10. Verifikasi worker memproses.
11. Verifikasi Facebook Page menerima Reel.
12. Verifikasi status menjadi Published.
13. Verifikasi History.
14. Pastikan tidak ada duplicate Reel.

Jangan menganggap API response sebagai bukti publish.

Publish harus diverifikasi dari Facebook Page seperti test sebelumnya.

Jika live Facebook test tidak dapat dilakukan karena credential/environment, lakukan semua test yang memungkinkan dan laporkan blocker sebenarnya. Jangan membuat hasil palsu.

==================================================
REGRESSION SAFETY
==================================================

FITUR YANG SUDAH PASS HARUS TETAP PASS:

- Manual upload
- Downloader
- Shared upload pipeline
- Media finalize
- Media ready guard
- Compose
- Queue
- Worker
- Retry
- Cancel
- Facebook Reels

Jangan melakukan refactor besar terhadap flow tersebut.

Jika harus mengubah shared code:

1. jelaskan alasan
2. buat regression test
3. jalankan seluruh test suite

==================================================
SECURITY
==================================================

Periksa:

- authorization
- user isolation
- schedule ID enumeration
- input validation
- timezone handling
- duplicate execution
- race condition
- secret leakage
- raw provider error leakage

Jangan commit:

- API key
- Facebook token
- password
- credential
- .env
- secret file

==================================================
GIT
==================================================

Setelah implementation selesai:

1. git status
2. inspect git diff
3. pastikan hanya perubahan yang berhubungan dengan Scheduler
4. pastikan tidak ada secret
5. run typecheck
6. run lint
7. run tests
8. run build
9. lakukan real web E2E test jika environment memungkinkan

Jika semuanya PASS:

Commit:

feat: implement scheduled publishing

Kemudian PUSH langsung ke branch yang sedang digunakan.

JANGAN force push.

JANGAN membuat empty commit.

Setelah push:

- verifikasi remote
- pastikan HEAD == origin/<branch>
- git status harus clean

==================================================
FINAL REPORT
==================================================

Tampilkan ringkas:

SCHEDULER: PASS/FAIL
CREATE SCHEDULE: PASS/FAIL
CANCEL: PASS/FAIL
QUEUE INTEGRATION: PASS/FAIL
WORKER INTEGRATION: PASS/FAIL
WEB E2E: PASS/FAIL
FACEBOOK LIVE VERIFICATION: PASS/FAIL
REGRESSION: PASS/FAIL
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL

GIT STATUS: CLEAN/NOT CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS/FAILED
REMOTE VERIFIED: YES/NO

Jika ada kegagalan, tampilkan error sebenarnya.

Jangan mengklaim PASS jika belum benar-benar diuji.

SETELAH PUSH BERHASIL, STOP.

````
# Prompt: Web E2E — Manual Upload & Downloader → Facebook Page
```
LANJUT PROJECT CONTENT PILOT — PHASE QUEUE MANAGER

Kondisi repository saat ini:

Content Pilot sudah memiliki publishing flow yang benar dan sudah diverifikasi end-to-end.

VERIFIED:

- Web Manual Upload → PASS
- Downloader → Web → PASS
- Shared Media Upload Flow → PASS
- Media Finalize → PASS
- Media Ready Guard → PASS
- Compose → PASS
- Queue → PASS
- Worker → PASS
- Facebook Page Reels → PASS
- Graph API Verification → PASS
- Typecheck → PASS
- Lint → PASS
- Test → PASS
- Build → PASS
- Git remote sudah verified

Flow yang sudah terbukti:

Manual upload
→ media pipeline
→ media ready
→ compose
→ publish request
→ queue
→ worker
→ Facebook upload
→ published
→ history/status

Downloader:

Downloader
→ ingestion
→ shared media pipeline
→ media ready
→ compose
→ queue
→ worker
→ Facebook publish

JANGAN merusak atau mengganti publishing flow yang sudah PASS.

==================================================
TUJUAN PHASE INI
==================================================

Sekarang fokus pada:

QUEUE MANAGER

Tujuannya membuat halaman/interface Queue Manager benar-benar berguna untuk mengelola publishing jobs yang sudah ada.

Queue Manager harus menggunakan data publishing job yang sebenarnya dari backend/database.

JANGAN membuat dummy queue.

JANGAN membuat fake status.

JANGAN membuat status yang hanya berasal dari frontend.

JANGAN membuat mock worker.

==================================================
ATURAN PALING PENTING
==================================================

1. Audit implementasi queue yang sekarang terlebih dahulu.

2. Baca code yang sudah ada sebelum mengubah apa pun.

3. Jangan mengganti arsitektur queue yang sudah bekerja jika tidak diperlukan.

4. Jangan mengubah Facebook publishing flow kecuali benar-benar diperlukan untuk Queue Manager.

5. Jangan mengubah Media Upload / Downloader flow.

6. Jangan membuat duplicate queue system.

7. Jangan membuat queue kedua hanya untuk UI.

8. Queue Manager harus membaca publishing jobs yang sama yang digunakan worker.

9. Status UI harus berasal dari state backend/database yang sebenarnya.

10. Semua action harus melalui API/backend yang benar.

11. Tidak boleh ada fake success.

12. Tidak boleh ada fake progress.

13. Tidak boleh menampilkan job sebagai published jika backend belum menyatakan published.

==================================================
AUDIT TERLEBIH DAHULU
==================================================

Sebelum coding:

Periksa:

- PublishingJob model
- PublishingAttempt model jika ada
- queue implementation
- worker
- API route publishing
- API route status
- database schema
- status transition
- retry logic
- error handling
- existing Queue page
- dashboard queue overview
- history
- polling/refresh mechanism
- job identifiers
- provider/destination relationship

Cari apakah queue sekarang menggunakan:

- Redis
- database queue
- BullMQ
- custom queue
- worker polling
- atau mekanisme existing lainnya.

Jangan mengganti teknologi queue tanpa alasan.

==================================================
QUEUE STATUS MODEL
==================================================

Pertahankan status yang sudah digunakan repository.

Jika repository sudah memiliki status seperti:

queued
processing
uploading
publishing
published
failed
cancelled
retrying

gunakan status existing.

JANGAN membuat status baru hanya untuk mempercantik UI.

Jika status existing berbeda, ikuti status yang benar-benar digunakan backend.

UI harus memetakan status backend secara konsisten.

==================================================
QUEUE MANAGER UI
==================================================

Buat Queue Manager yang responsive untuk mobile dan desktop.

Target tampilan:

QUEUE MANAGER

Header:

Queue Manager

[Refresh]

Summary:

Queued
Processing
Publishing
Published
Failed

Summary harus berasal dari data sebenarnya.

Contoh:

Queued: 3
Processing: 1
Publishing: 1
Failed: 2

Jangan hardcode angka.

==================================================
FILTER
==================================================

Tambahkan filter jika sesuai dengan API existing:

Status:

All
Queued
Processing
Uploading
Publishing
Published
Failed
Cancelled

Destination:

All
Facebook Page A
Facebook Page B
dst.

Content type:

All
Reels
Video
Photo
Post

Source:

All
Manual
Downloader

Jika data source memang tersedia.

Jika backend belum memiliki field tertentu, jangan membuat fake field.

Implementasikan field hanya jika memang dapat ditentukan secara reliable.

==================================================
JOB CARD
==================================================

Setiap publishing job tampil sebagai card/list item.

Minimal informasi:

- media thumbnail jika tersedia
- filename/title
- caption ringkas
- destination
- platform
- content type
- status
- created time
- scheduled time jika ada
- published time jika ada
- attempt count jika tersedia
- last error jika failed

Contoh:

--------------------------------

Content Pilot Web Downloader Test

Facebook
Yourdreels

Reels

Published

Published:
25 Aug 2026 12:05

Attempts: 1

--------------------------------

Untuk failed:

--------------------------------

Paket Data Murah

Facebook
Yourdreels

Reels

Failed

Attempts: 2

Error:
<safe error message>

[Retry]

--------------------------------

==================================================
STATUS DETAIL
==================================================

Ketika user membuka job:

Tampilkan detail lengkap job.

Contoh:

Job ID
Media
Platform
Destination
Content Type
Status
Created
Scheduled
Started
Completed
Attempt Count

Publishing Attempts:

Attempt #1
Status
Started
Finished
Error

Attempt #2
Status
Started
Finished
Error

Jangan menampilkan:

- access token
- refresh token
- Authorization header
- secret
- raw credential
- sensitive provider response

==================================================
ERROR HANDLING
==================================================

Error harus aman.

Jangan menampilkan raw provider response kepada user.

Gunakan safe error message.

Contoh:

Backend:

VALIDATION_ERROR

UI:

"Media tidak memenuhi persyaratan Facebook."

Backend:

PERMISSION_DENIED

UI:

"Akun tidak memiliki permission untuk melakukan publishing."

Backend:

RATE_LIMITED

UI:

"Platform sedang membatasi request. Job akan dicoba kembali sesuai retry policy."

Backend:

MEDIA_NOT_READY

UI:

"Media masih diproses. Tunggu sampai media siap."

Jika error code sudah memiliki mapping di repository, gunakan mapping existing.

Jangan membuat mapping yang bertentangan dengan backend.

==================================================
RETRY
==================================================

Implement tombol:

[Retry]

Tetapi hanya untuk job yang memang dapat di-retry.

Bedakan:

Temporary error:

- timeout
- network error
- rate limit
- temporary provider error

→ retry boleh.

Permanent error:

- invalid token
- permission denied
- invalid destination
- unsupported media
- validation error

→ jangan otomatis retry tanpa memperbaiki penyebab.

Jika backend sudah mempunyai retry policy, gunakan policy tersebut.

JANGAN membuat retry hanya di frontend.

Retry harus membuat backend/queue melakukan pekerjaan sebenarnya.

Setelah retry:

failed
→ retrying/queued
→ worker
→ publishing
→ published / failed

Status harus benar-benar berasal dari backend.

==================================================
CANCEL JOB
==================================================

Jika queue architecture saat ini memungkinkan cancellation:

Tambahkan:

[Cancel]

Untuk job yang masih:

queued
scheduled
atau status lain yang memang aman dibatalkan.

Jangan izinkan cancel terhadap job yang sudah published.

Jangan membuat cancellation palsu.

Jika cancellation belum aman pada worker architecture saat ini, jangan memaksakan implementasi.

Dokumentasikan sebagai:

NOT AVAILABLE YET

daripada membuat fitur yang tidak benar.

==================================================
DELETE JOB
==================================================

Jangan langsung menambahkan delete job jika dapat merusak audit/history.

Pertahankan history publishing.

Jika perlu menghapus dari active queue:

gunakan konsep yang aman seperti cancellation/archive jika architecture mendukung.

Jangan menghapus database record hanya karena user menekan tombol.

==================================================
REFRESH / LIVE STATUS
==================================================

Queue Manager harus dapat memperbarui status.

Jika repository sudah memiliki polling/live status:

gunakan mekanisme tersebut.

Jika belum:

implementasikan polling ringan hanya jika memang diperlukan.

Jangan melakukan polling terlalu agresif.

Contoh:

5–10 detik untuk active jobs.

Job yang sudah:

published
failed
cancelled

tidak perlu terus dipolling.

Pastikan tidak terjadi:

- memory leak
- duplicate requests
- polling setelah halaman ditutup
- request terus berjalan tanpa batas

==================================================
DASHBOARD QUEUE OVERVIEW
==================================================

Dashboard sudah memiliki:

Queue Overview

Pastikan angka/status Queue Overview menggunakan sumber data yang sama dengan Queue Manager.

Jangan memiliki dua sumber queue berbeda.

Contoh:

Dashboard:

Queued 3
Processing 1
Failed 2

Queue Manager harus membaca data yang sama.

Jika Queue Manager menunjukkan:

Queued 3

tetapi Dashboard menunjukkan:

Queued 0

maka perbaiki data source, bukan sekadar UI.

==================================================
HISTORY
==================================================

Jangan merusak History.

History harus tetap menyimpan hasil publishing.

Contoh:

Queue:

queued
→ processing
→ publishing
→ published

Setelah published:

History tetap dapat menampilkan:

destination
content type
status
externalId
permalink
published time

Jika gagal:

History dapat menampilkan:

failed
error code
safe error message
attempt count

Gunakan struktur existing jika sudah ada.

==================================================
WORKER INTEGRATION
==================================================

Queue Manager tidak boleh menjalankan publishing sendiri.

Flow harus tetap:

Queue Manager
→ backend action
→ queue
→ worker
→ provider
→ Facebook API

Bukan:

Queue Manager
→ Facebook API langsung

Jangan memindahkan provider logic ke frontend.

==================================================
API
==================================================

Audit API existing.

Gunakan endpoint existing jika sudah mencukupi.

Jika belum mencukupi, tambahkan endpoint minimal yang diperlukan.

Contoh konsep:

GET /api/publishing/jobs

GET /api/publishing/jobs/:id

POST /api/publishing/jobs/:id/retry

POST /api/publishing/jobs/:id/cancel

Tetapi:

JANGAN menganggap endpoint di atas sudah ada.

Periksa repository terlebih dahulu.

Ikuti naming convention API yang sudah digunakan project.

==================================================
LIST API
==================================================

Jika membuat/menyempurnakan endpoint list job:

dukung jika sesuai architecture:

pagination
status filter
destination filter
content type filter
sorting

Default sorting:

newest jobs first

Jangan mengambil seluruh database jika jumlah job dapat menjadi besar.

Gunakan pagination jika architecture database mendukung.

==================================================
SECURITY
==================================================

Pastikan user hanya dapat melihat dan mengelola job miliknya sendiri.

Contoh:

User A

tidak boleh:

- melihat job User B
- retry job User B
- cancel job User B
- melihat media User B
- melihat destination User B

Semua authorization harus diverifikasi backend.

Jangan mengandalkan filtering frontend.

==================================================
MULTI DESTINATION
==================================================

Pastikan Queue Manager tetap mendukung:

1 media
→ multiple destinations
→ multiple publishing jobs

Contoh:

Video A

Facebook Page A
→ Job 001
→ published

Facebook Page B
→ Job 002
→ failed

YouTube Channel A
→ Job 003
→ queued

Jangan menggabungkan ketiganya menjadi satu job.

==================================================
PROVIDER INDEPENDENCE
==================================================

Queue Manager harus platform-independent.

Jangan membuat:

FacebookQueueManager

Gunakan:

Publishing Queue

Provider hanya salah satu property job.

Contoh:

provider = facebook

nantinya:

provider = youtube

provider = instagram

provider = tiktok

Queue Manager tidak perlu diubah ketika provider baru ditambahkan.

==================================================
MEDIA SOURCE
==================================================

Queue Manager harus dapat menangani job dari:

Manual Upload

dan:

Downloader

Keduanya harus masuk ke publishing job yang sama.

Jangan membuat:

ManualQueue

DownloaderQueue

Gunakan:

PublishingQueue

Source cukup menjadi metadata jika memang sudah tersedia.

==================================================
MOBILE UI
==================================================

Project digunakan dari mobile.

Pastikan Queue Manager nyaman pada layar kecil.

Jangan membuat tabel desktop yang sulit digunakan di mobile.

Gunakan card/list responsive.

Informasi penting harus terlihat:

- title
- destination
- status
- time
- error jika gagal
- action

Action jangan terlalu kecil.

==================================================
EMPTY STATE
==================================================

Jika tidak ada queue:

Tampilkan:

"No publishing jobs"

atau teks yang sesuai design system existing.

Tambahkan penjelasan singkat.

Jangan menampilkan fake job.

==================================================
LOADING STATE
==================================================

Gunakan loading state ketika data sedang diambil.

Jangan langsung menampilkan:

Queued: 0

sebelum request selesai jika itu dapat disalahartikan sebagai data sebenarnya.

Gunakan skeleton/loading state sesuai design system.

==================================================
ERROR STATE
==================================================

Jika API queue gagal:

Tampilkan error yang jelas.

Contoh:

"Unable to load publishing queue."

[Retry]

Jangan menampilkan stack trace.

Jangan menampilkan raw backend error.

==================================================
PERFORMANCE
==================================================

Perhatikan:

- database query
- pagination
- N+1 query
- thumbnail loading
- polling
- duplicate API calls
- unnecessary rerender

Jangan melakukan query besar hanya untuk menghitung summary.

Gunakan aggregation/query yang sesuai jika diperlukan.

==================================================
TESTING
==================================================

Tambahkan/ubah test sesuai architecture existing.

Minimal test:

1. Queue list berhasil
2. Empty queue
3. Status filter
4. Destination filter jika tersedia
5. Job detail
6. Failed job menampilkan safe error
7. Retry hanya untuk job yang valid
8. Permanent error tidak retry sembarangan
9. Cancel hanya untuk job yang dapat dibatalkan
10. User isolation
11. Multi-destination jobs
12. Manual upload job muncul
13. Downloader job muncul
14. Published job muncul
15. Queue summary benar

Jangan menghapus test existing.

==================================================
REGRESSION TEST
==================================================

SANGAT PENTING:

Setelah perubahan Queue Manager, ulangi regression test terhadap flow yang sebelumnya PASS.

Minimal:

Manual Upload
→ Media Ready
→ Compose
→ Publish
→ Queue
→ Worker
→ Facebook Reels
→ History

Dan:

Downloader
→ Media Ingestion
→ Media Ready
→ Compose
→ Publish
→ Queue
→ Worker
→ Facebook Reels
→ History

Jangan menganggap Queue Manager selesai jika publishing regression rusak.

==================================================
VALIDATION
==================================================

Sebelum selesai:

1. typecheck
2. lint
3. unit tests
4. API tests
5. build
6. inspect UI
7. inspect database queries
8. inspect authorization
9. inspect queue integration
10. regression test manual upload
11. regression test downloader
12. regression test Facebook Reels

==================================================
GIT
==================================================

Sebelum commit:

git status

Periksa diff.

Pastikan:

- tidak ada secret
- tidak ada token
- tidak ada password
- tidak ada credential
- tidak ada file test sensitif
- tidak ada perubahan unrelated

Commit dengan message:

feat(queue): add publishing queue manager

Push ke branch aktif.

Jangan force push.

Setelah push:

verifikasi remote.

==================================================
LARANGAN
==================================================

JANGAN:

- menghapus publishing flow
- mengganti worker tanpa alasan
- mengganti queue technology tanpa alasan
- membuat dummy jobs
- membuat fake status
- membuat fake retry
- membuat fake cancellation
- bypass authorization
- menampilkan token
- menampilkan raw Facebook response
- mengubah Facebook API flow hanya untuk UI
- membuat Facebook-specific Queue Manager
- membuat Downloader queue terpisah
- membuat Manual Upload queue terpisah
- menghapus history
- menghapus test existing
- melakukan massive refactor
- mengubah schema besar tanpa kebutuhan
- commit secret
- force push

==================================================
HASIL AKHIR YANG WAJIB DILAPORKAN
==================================================

Tampilkan:

QUEUE MANAGER STATUS:
PASS / FAIL

API:
PASS / FAIL

WORKER INTEGRATION:
PASS / FAIL

RETRY:
PASS / NOT IMPLEMENTED / FAIL

CANCEL:
PASS / NOT IMPLEMENTED / FAIL

USER AUTHORIZATION:
PASS / FAIL

MANUAL UPLOAD REGRESSION:
PASS / FAIL

DOWNLOADER REGRESSION:
PASS / FAIL

FACEBOOK REELS REGRESSION:
PASS / FAIL

TYPECHECK:
PASS / FAIL

LINT:
PASS / FAIL

TEST:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

==================================================
STOP CONDITION
==================================================

Jika semua verification PASS:

STOP.

Jangan lanjut ke Scheduler, Analytics, YouTube, Instagram, TikTok, atau fitur lain.

Laporkan hasil dan tunggu instruksi berikutnya.

Jika ada test gagal:

Jangan menyatakan PASS.

Cari akar masalah, perbaiki, ulangi test, kemudian laporkan hasil sebenarnya.

````
# Prompt: Web E2E — Manual Upload & Downloader → Facebook Page
```
Lanjutkan dari repository TERKINI.

Jangan melakukan refactor besar.
Jangan mengubah Facebook publishing backend yang sudah PASS.
Jangan membuat platform baru.

TUJUAN:
Verifikasi bahwa seluruh flow benar-benar bekerja dari UI Web sampai Reel muncul di Facebook Page.

TEST 1 — MANUAL UPLOAD

Dari Web → Compose:

1. Pilih Content Type = Reels.
2. Upload video baru dari perangkat/browser.
3. Pastikan upload menggunakan shared media upload flow yang sudah ada.
4. Tunggu proses upload dan finalize selesai.
5. Pastikan media berubah menjadi READY.
6. Pastikan media READY muncul di Media picker.
7. Pilih media tersebut.
8. Pilih Facebook Page "Yourdreels".
9. Isi caption:
   "Content Pilot Web Manual Test"
10. Pilih Publish Now.
11. Pastikan job masuk queue.
12. Worker memproses job.
13. Pastikan status menjadi published.
14. Verifikasi langsung melalui Facebook Graph API bahwa Reel benar-benar published.
15. Verifikasi Reel benar-benar terlihat pada Facebook Page.

TEST 2 — DOWNLOADER → WEB → FACEBOOK

1. Gunakan video yang berasal dari Downloader.
2. Pastikan downloader ingestion berhasil.
3. Pastikan media selesai finalize.
4. Pastikan media menjadi READY.
5. Buka Compose melalui Web.
6. Pastikan media Downloader muncul di Media picker.
7. Pilih media tersebut.
8. Pilih Facebook Page "Yourdreels".
9. Isi caption:
   "Content Pilot Web Downloader Test"
10. Publish Now.
11. Pastikan job masuk queue.
12. Pastikan worker memproses job.
13. Pastikan status menjadi published.
14. Verifikasi melalui Graph API.
15. Pastikan Reel benar-benar muncul di Facebook Page.

IMPORTANT:

Manual upload dan Downloader HARUS tetap menggunakan shared media pipeline.

Manual:
Browser
→ shared upload
→ finalize
→ READY
→ Compose
→ Facebook

Downloader:
Downloader
→ ingestion
→ finalize
→ READY
→ Compose
→ Facebook

Jangan membuat pipeline upload Facebook kedua.

MEDIA PICKER:

Pastikan hanya media status READY yang dapat dipilih.

Media:
- uploading
- processing
- failed
- invalid
- belum finalized

tidak boleh dapat dipublish.

Jika media belum READY, tampilkan pesan yang jelas.

ERROR HANDLING:

Jika backend memberikan error spesifik, UI harus menampilkan alasan yang aman.

Jangan selalu mengubah semua error menjadi:

"Failed to create the post from media."

Contoh pesan:

"Media belum siap. Tunggu proses upload selesai."

"File video tidak valid."

"Media gagal diproses."

Jangan tampilkan:
- access token
- API key
- raw Graph API response
- credential
- secret

REGRESSION:

Pastikan perubahan UI tidak merusak:

- Shared Upload Flow
- Manual Video Upload
- Downloader Ingestion
- Media Ready Guard
- Compose
- Facebook Reels publishing

TEST WAJIB:

- typecheck
- lint
- tests
- build
- Web manual upload
- Web Downloader media
- Facebook Page verification

Gunakan video TEST BARU untuk manual upload agar tidak hanya menggunakan artefak lama.

Jangan menganggap HTTP 200 atau response API sebagai bukti publish berhasil.

Publish harus diverifikasi sampai Reel benar-benar tercatat sebagai published pada Facebook Page.

LAPORKAN:

WEB MANUAL UPLOAD: PASS/FAIL
DOWNLOADER → WEB: PASS/FAIL
MEDIA READY: PASS/FAIL
COMPOSE: PASS/FAIL
QUEUE: PASS/FAIL
WORKER: PASS/FAIL
FACEBOOK PAGE REELS: PASS/FAIL
GRAPH API VERIFICATION: PASS/FAIL
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL

Jika semua PASS:

WEB MANUAL UPLOAD: VERIFIED
WEB DOWNLOADER PUBLISH: VERIFIED
FACEBOOK PAGE REELS: VERIFIED

Git:
- git status
- inspect diff
- jangan commit secret
- commit perubahan yang memang diperlukan
- push ke branch aktif
- verifikasi remote

Tampilkan:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

STOP setelah verifikasi.

Jangan lanjut ke Instagram, YouTube, TikTok, Scheduler, atau fitur lain.

````
# Prompt: Web Manual Upload + Downloader → Facebook Page Reels
```
Lanjutkan project Content Pilot dari kondisi repository TERKINI.

PENTING:
Jangan mengubah flow Facebook publishing yang sudah terbukti PASS.
Jangan refactor besar.
Jangan membuat fitur baru yang tidak diminta.

Kondisi saat ini:
- Facebook Page Reels publishing: PASS
- Manual Video Upload backend: PASS
- Downloader Ingestion: PASS
- Shared Upload Flow: PASS
- Media Ready Guard: PASS
- Facebook Reels verification: PASS
- Test: PASS
- Build: PASS
- Git clean dan sudah push

TUJUAN SEKARANG:

Pastikan fitur upload melalui WEB benar-benar bisa digunakan end-to-end dengan DUA sumber media:

1. Manual upload dari perangkat/local
2. Media hasil Downloader

FLOW 1 — MANUAL UPLOAD

Dari halaman Compose:

- pilih Content Type = Reels
- pilih/upload video dari perangkat
- video masuk ke shared media upload flow
- tunggu upload selesai
- finalize media
- media muncul sebagai READY
- media dapat dipilih di Media picker
- pilih Facebook Page
- isi caption
- Publish Now
- job masuk queue
- worker memproses
- Facebook Page menerima Reel
- verifikasi melalui Facebook Graph API
- status berubah menjadi published

FLOW 2 — DOWNLOADER

Gunakan media yang berasal dari fitur Downloader.

Pastikan:

Downloader
→ media ingestion
→ storage
→ finalize
→ READY
→ muncul di Compose Media picker
→ pilih Facebook Page
→ caption
→ Publish Now
→ queue
→ worker
→ Facebook Page Reel
→ Graph API verification
→ published

ATURAN MEDIA:

Jangan membuat sistem upload kedua yang terpisah.

Manual upload dan Downloader HARUS menggunakan shared media pipeline yang sama setelah media masuk ke sistem.

Contoh:

Manual:
Browser → Upload → Finalize → Media READY

Downloader:
Downloader → Ingestion → Finalize → Media READY

Kemudian keduanya:

Media READY
→ Compose
→ Publish
→ Facebook

MEDIA PICKER:

Pastikan Media picker hanya menampilkan media yang benar-benar READY.

Media yang:
- uploading
- failed
- invalid
- belum finalized

tidak boleh dapat dipilih untuk publish.

Jika user mencoba memilih media invalid, tampilkan error yang jelas.

WEB ERROR HANDLING:

Jangan tampilkan error generik seperti:

"Failed to create the post from media."

jika backend memberikan error yang lebih spesifik.

Tampilkan pesan yang aman dan jelas, misalnya:

"Media belum siap. Tunggu upload selesai."

atau

"File video tidak valid."

atau

"Media gagal diproses."

Jangan pernah menampilkan token, credential, atau raw provider response.

TEST WAJIB:

1. Manual upload video baru dari browser.
2. Pastikan video muncul sebagai READY.
3. Publish melalui Compose.
4. Verifikasi Reel benar-benar muncul di Facebook Page.
5. Ambil media dari Downloader.
6. Pastikan media Downloader muncul di Compose.
7. Publish media Downloader melalui Compose.
8. Verifikasi Reel benar-benar muncul di Facebook Page.
9. Coba pilih media yang belum READY dan pastikan ditolak dengan pesan yang benar.
10. Pastikan publishing flow Facebook existing tidak rusak.

JANGAN mengubah Facebook backend publishing flow kecuali ditemukan bug nyata yang diperlukan agar Web flow menggunakan API yang sudah ada.

Jika menemukan bug, perbaiki akar masalahnya, bukan membuat workaround khusus untuk test.

TESTING:

Setelah perubahan:

- typecheck
- lint
- unit/regression tests
- build
- test manual Web
- test Facebook Page verification

Gunakan video TEST BARU untuk memastikan bukan hanya memakai artefak test lama.

HASIL YANG WAJIB DILAPORKAN:

MANUAL WEB UPLOAD: PASS/FAIL
DOWNLOADER → WEB → FACEBOOK: PASS/FAIL
MEDIA READY GUARD: PASS/FAIL
COMPOSE: PASS/FAIL
FACEBOOK PAGE REELS: PASS/FAIL
GRAPH API VERIFICATION: PASS/FAIL
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL

Jika semua PASS:

WEB MANUAL UPLOAD: VERIFIED
DOWNLOADER WEB PUBLISH: VERIFIED
FACEBOOK PAGE REELS: VERIFIED

Kemudian STOP.

Jangan lanjut ke platform lain.
Jangan membuat fitur Instagram/YouTube/TikTok.
Jangan membuat scheduler baru.
Jangan melakukan refactor besar.

````
# 
```
PROMPT: FIX MANUAL UPLOAD VALIDATION & SHARED UPLOAD FLOW

Hasil E2E terakhir:

MOBILE BROWSER: PASS
REAL UPLOAD: PASS
COMPOSE: PASS
FACEBOOK REELS: PASS
FACEBOOK VERIFICATION: PASS
REGRESSION: PASS
BUILD: PASS

Real mobile browser sudah berhasil:

browser → pilih video → upload → compose → publish → Facebook Page → Reel terverifikasi.

JANGAN mengubah flow publishing Facebook yang sudah PASS.

JANGAN membuat uploader baru.

JANGAN mengubah downloader.

JANGAN melakukan refactor besar.

Hanya perbaiki 2 temuan berikut.

==================================================
BUG 1 — COMPOSE UPLOAD FLOW
==================================================

Saat ini Compose masih menangani file input secara langsung.

Gunakan shared upload helper/component/service yang sudah tersedia di repository agar:

Manual Upload
dan
Downloader Ingestion

menggunakan pipeline media yang konsisten.

Target:

Browser File Picker
→ shared upload flow
→ upload
→ finalize
→ media READY
→ Compose media picker

Jangan membuat duplicate upload implementation.

Cari implementation upload existing terlebih dahulu.

Reuse implementation tersebut.

Jika shared helper sudah ada tetapi Compose belum menggunakannya, ubah Compose agar menggunakan helper tersebut.

Jangan mengubah API contract jika tidak diperlukan.

==================================================
BUG 2 — INVALID FILE VALIDATION
==================================================

Saat user memilih file yang bukan video:

contoh:
.jpg
.png
.txt

file tidak boleh:

upload sampai dianggap READY
atau
masuk Compose sebagai media yang valid.

Backend finalize harus melakukan validasi MIME/content type yang sebenarnya.

Jika invalid, return error terstruktur:

VALIDATION_ERROR

dengan pesan yang jelas, misalnya:

"Unsupported video format"

atau pesan existing yang paling sesuai.

Jangan menggunakan error generik:

"Failed to create the post from media."

jika sebenarnya root cause adalah file bukan video.

Pastikan:

invalid file
→ validation failed
→ media tidak menjadi READY
→ Compose tidak dapat mempublikasikannya.

==================================================
REGRESSION
==================================================

Setelah perubahan, test kembali:

1. Manual browser upload video
2. Downloader ingestion
3. Compose media picker
4. Facebook Reels publish

Expected:

Manual Upload = PASS
Downloader = PASS
Media Finalize = PASS
Media Ready Filter = PASS
Compose = PASS
Facebook Reels = PASS

==================================================
TEST INVALID FILE
==================================================

Test minimal satu file non-video.

Expected:

UPLOAD VALIDATION = PASS
MEDIA READY = NO
ERROR CODE = VALIDATION_ERROR
ERROR MESSAGE = jelas dan spesifik

Pastikan tidak ada fake success.

==================================================
IMPORTANT
==================================================

Jangan mengubah:

- Facebook API
- Facebook provider
- worker publishing flow
- queue
- downloader
- storage architecture
- database schema

kecuali benar-benar diperlukan untuk memperbaiki dua bug di atas.

Jangan menghapus test existing.

Tambahkan/update test hanya jika diperlukan untuk mengunci regression.

==================================================
FINAL CHECK
==================================================

Jalankan:

typecheck
lint
tests
build

Kemudian:

git diff
git status

Jika semua PASS:

commit dengan message:

fix: unify compose upload and media validation

Push ke branch aktif.

Jangan force push.

Jika push gagal, laporkan error sebenarnya.

==================================================
FINAL REPORT
==================================================

Tampilkan:

SHARED UPLOAD FLOW: PASS/FAIL
MANUAL VIDEO UPLOAD: PASS/FAIL
DOWNLOADER REGRESSION: PASS/FAIL
INVALID FILE VALIDATION: PASS/FAIL
MEDIA READY GUARD: PASS/FAIL
COMPOSE: PASS/FAIL
FACEBOOK REELS: PASS/FAIL
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
TEST: PASS/FAIL
BUILD: PASS/FAIL

GIT STATUS: CLEAN/NOT CLEAN
COMMIT: <hash>
PUSH STATUS: SUCCESS/FAILED

STOP setelah selesai.

````
# 
```

TASK: REAL BROWSER MANUAL UPLOAD E2E TEST

Hasil implementation terakhir menunjukkan:

MEDIA PIPELINE: PASS
MANUAL UPLOAD: PASS
DOWNLOADER INGESTION: PASS
MEDIA FINALIZE: PASS
MEDIA READY FILTER: PASS
COMPOSE MEDIA PICKER: PASS
FACEBOOK PAGE REELS: PASS
REGRESSION TEST: PASS
BUILD: PASS

Namun sekarang saya ingin memverifikasi SATU HAL yang belum boleh diasumsikan:

APAKAH USER BENAR-BENAR BISA MEMILIH FILE VIDEO DARI PERANGKAT MELALUI WEB BROWSER DAN MEMPUBLISH-NYA?

Jangan hanya menjalankan unit/API test.
Jangan hanya melakukan backend import.
Jangan hanya menggunakan file yang sudah ada di Media Library.

Lakukan REAL BROWSER E2E TEST.

==================================================
TARGET FLOW
==================================================

Browser
→ Content Pilot
→ Compose
→ Reels
→ Upload Media / Select File
→ pilih video lokal
→ upload
→ upload selesai
→ finalize
→ status READY
→ media muncul/terpilih di Compose
→ pilih Facebook Page Yourdreels
→ Publish now
→ queue
→ worker
→ Facebook
→ published
→ verifikasi Reel benar-benar muncul di Facebook Page

==================================================
IMPORTANT
==================================================

Gunakan uploader/component yang SUDAH ADA.

JANGAN membuat uploader baru jika uploader existing sudah tersedia.

JANGAN mengubah backend publishing yang sudah PASS.

JANGAN mengubah Facebook provider kecuali ditemukan bug nyata yang menghambat browser upload.

Fokus pada jalur browser → upload → media → compose.

==================================================
STEP 1 — AUDIT UI
==================================================

Periksa halaman Compose.

Pastikan untuk content type:

Reels

tersedia cara yang jelas untuk:

1. memilih media existing
2. upload media dari perangkat

Jika UI saat ini hanya memiliki dropdown media seperti:

-- select --
compose_test.mp4
web_ui_test.mp4
...

dan TIDAK ada tombol/input:

Upload Media
Choose File
Select File

maka identifikasi component existing yang seharusnya digunakan.

Jangan membuat duplicate upload system.

==================================================
STEP 2 — REAL FILE INPUT
==================================================

Pastikan browser menggunakan:

<input type="file">

atau mekanisme file picker yang benar.

Accept minimal:

video/*

Jika project sudah memiliki restriction MIME tertentu, gunakan restriction existing.

Jangan menggunakan URL palsu.

Jangan menganggap file local path dapat dikirim langsung ke backend tanpa upload.

==================================================
STEP 3 — BROWSER UPLOAD
==================================================

Gunakan file video lokal baru yang BELUM ada di Media Library.

Contoh:

compose_browser_manual_test.mp4

Flow:

User memilih file
→ frontend upload
→ backend/storage
→ upload progress/status
→ finalize
→ Media status READY

Pastikan frontend tidak menganggap upload sukses hanya karena request awal mengembalikan HTTP 200.

==================================================
STEP 4 — READY GUARD
==================================================

Selama upload:

Media tidak boleh dianggap READY.

Jika finalize belum selesai:

media tidak boleh dipakai untuk publishing.

Setelah finalize:

status harus READY.

Kemudian media harus dapat dipilih oleh Compose.

==================================================
STEP 5 — COMPOSE
==================================================

Setelah upload selesai:

- media tampil/terpilih
- filename benar
- tidak ada error missing_media
- tidak ada "Failed to create the post from media"

Pastikan Compose mengirim MEDIA ID yang benar ke backend.

Jangan hanya mengirim filename/path.

==================================================
STEP 6 — PUBLISH
==================================================

Gunakan:

Content type:
Reels

Destination:
Yourdreels (Facebook Page)

Publish:
Publish now

Kemudian verifikasi:

queued
→ uploading
→ publishing
→ published

==================================================
STEP 7 — FACEBOOK VERIFICATION
==================================================

Jangan berhenti pada HTTP success.

Verifikasi melalui Facebook Page Yourdreels bahwa Reel benar-benar dibuat.

Verifikasi:

- video benar
- caption benar
- content type = Reel
- externalId tersedia
- permalink tersedia
- publish_status = published
- video_status = ready

==================================================
STEP 8 — TEST DOWNLOADER REGRESSION
==================================================

Jangan mengubah downloader.

Pastikan downloader existing tetap menghasilkan:

Downloader
→ Media
→ READY
→ Compose
→ Facebook Reels

Jika sudah PASS, cukup regression check.

==================================================
STEP 9 — ERROR TEST
==================================================

Test minimal satu kondisi invalid:

- file bukan video
atau
- upload gagal

Pastikan UI memberikan error yang sebenarnya.

Jangan menampilkan error generik jika backend sudah memberikan alasan yang lebih spesifik.

==================================================
STEP 10 — MOBILE BROWSER
==================================================

Karena aplikasi digunakan melalui HP, test juga browser mobile.

Pastikan:

- tombol upload dapat ditekan
- file picker terbuka
- video dapat dipilih dari perangkat
- upload berjalan
- UI tidak tertutup/terpotong
- status upload terlihat
- setelah READY media dapat dipilih
- publish tetap bekerja

==================================================
JANGAN MERUSAK
==================================================

Jangan mengubah:

- Facebook authentication
- Facebook Graph API publishing flow
- worker
- downloader
- storage architecture
- Media model

kecuali ditemukan bug yang benar-benar menyebabkan browser upload gagal.

==================================================
HASIL WAJIB
==================================================

Laporkan:

BROWSER MANUAL UPLOAD: PASS/FAIL
FILE PICKER: PASS/FAIL
UPLOAD: PASS/FAIL
FINALIZE: PASS/FAIL
MEDIA READY: PASS/FAIL
COMPOSE: PASS/FAIL
FACEBOOK PUBLISH: PASS/FAIL
FACEBOOK VERIFICATION: PASS/FAIL
MOBILE BROWSER: PASS/FAIL
DOWNLOADER REGRESSION: PASS/FAIL

Jika PASS, tampilkan:

SOURCE: Browser Manual Upload
FILE: <filename>
MEDIA ID: <id>
FACEBOOK PAGE: Yourdreels
CONTENT TYPE: Reels
STATUS: PUBLISHED
EXTERNAL ID: <id>
PERMALINK: <permalink>

Jika FAIL:

Jangan menutupi error.

Tampilkan root cause sebenarnya, file yang bermasalah, dan perbaikan minimal yang diperlukan.

STOP setelah verifikasi selesai.
````
# Prompt — Unified Media Pipeline: Manual Upload + Downloader
```

PROMPT: UNIFIED MEDIA PIPELINE — MANUAL UPLOAD + DOWNLOADER

Kita lanjutkan project Content Pilot.

JANGAN membuat fitur upload baru dari nol sebelum melakukan audit terhadap implementation yang SUDAH ADA.

Tujuan task ini adalah memastikan Content Pilot memiliki SATU media pipeline yang dapat menerima media dari dua sumber:

1. Manual Upload
   - User memilih video langsung dari perangkat/HP/PC.
2. Downloader
   - Video yang berhasil didownload oleh fitur downloader masuk ke media system yang sama.

Kedua sumber tersebut HARUS menghasilkan Media object yang sama dan dapat digunakan oleh Compose untuk publishing.

==================================================
ATURAN PALING PENTING
==================================================

1. Audit repository terlebih dahulu.
2. Cari implementation upload/manual upload yang SUDAH ADA.
3. Cari implementation downloader yang SUDAH ADA.
4. Cari Media Library yang SUDAH ADA.
5. Cari endpoint:
   - media upload
   - media finalize
   - media status
   - media listing
   - downloader output/import
6. Cari storage abstraction yang SUDAH ADA.
7. Cari Compose media picker yang SUDAH ADA.
8. Jangan membuat duplicate uploader.
9. Jangan membuat duplicate storage system.
10. Jangan membuat duplicate Media model jika sudah ada.
11. Jangan membuat duplicate downloader.
12. Jangan mengubah Facebook publishing flow yang sudah PASS kecuali benar-benar diperlukan untuk integrasi media.
13. Jangan mengubah Facebook Page/Reels API flow yang sudah terbukti berhasil.
14. Jangan membuat fake success state.
15. Jangan menggunakan browser automation untuk menggantikan official Facebook API.
16. Jangan menghapus implementation existing hanya karena struktur menurutmu kurang bagus.

==================================================
TARGET ARCHITECTURE
==================================================

Gunakan satu pipeline:

MANUAL UPLOAD
       │
       ▼
MEDIA INGESTION
       │
       ▼
STORAGE
       │
       ▼
FINALIZE
       │
       ▼
MEDIA STATUS = READY
       │
       ▼
MEDIA LIBRARY
       │
       ▼
COMPOSE MEDIA PICKER
       │
       ▼
FACEBOOK PAGE
       │
       ▼
REELS PUBLISHING


DOWNLOADER
       │
       ▼
MEDIA INGESTION
       │
       ▼
STORAGE
       │
       ▼
FINALIZE
       │
       ▼
MEDIA STATUS = READY
       │
       ▼
MEDIA LIBRARY
       │
       ▼
COMPOSE MEDIA PICKER
       │
       ▼
FACEBOOK PAGE
       │
       ▼
REELS PUBLISHING


PENTING:

Manual Upload dan Downloader TIDAK boleh memiliki dua media pipeline terpisah.

Keduanya harus berakhir pada Media entity/storage pipeline yang sama.

==================================================
MEDIA LIFECYCLE
==================================================

Media minimal memiliki lifecycle:

created
uploading
processing
ready
failed

Aturan:

- Media dengan status uploading tidak boleh digunakan Compose.
- Media dengan status processing tidak boleh digunakan Compose.
- Media dengan status failed tidak boleh digunakan Compose.
- Hanya media status ready yang boleh dipilih untuk publishing.

Jika repository sudah memiliki status yang berbeda, gunakan status existing dan jangan membuat duplicate status system.

==================================================
MANUAL UPLOAD
==================================================

Pastikan user dapat:

1. Membuka Compose atau Media Library.
2. Menekan tombol:

   Upload Media

   atau

   Upload from device

3. Memilih video dari perangkat.
4. Browser mengirim file ke backend/storage menggunakan flow existing.
5. Upload mendapatkan progress/status yang benar.
6. Setelah upload selesai, backend melakukan finalize.
7. Media berubah menjadi:

   READY

8. Media tersebut langsung dapat muncul di Media Library.
9. Media tersebut dapat dipilih dari Compose.

Jangan membuat upload langsung menjadi ready sebelum backend benar-benar menyelesaikan proses upload/finalize.

==================================================
DOWNLOADER
==================================================

Downloader yang sudah ada harus menggunakan Media Pipeline yang sama.

Flow:

Downloader
→ download video
→ create/ingest Media
→ storage
→ finalize
→ status ready
→ Media Library

Jangan membuat:

DownloaderMedia

jika Media generic sudah tersedia.

Downloader harus menghasilkan Media generic.

Jika downloader sudah menyimpan file ke storage, gunakan storage abstraction existing dan buat/register Media record yang benar.

Jangan mendownload ulang file hanya untuk memasukkannya ke Media Library.

==================================================
MEDIA LIBRARY
==================================================

Media Library harus menjadi tempat pusat semua media.

Media dapat memiliki metadata seperti:

- id
- filename
- mimeType
- size
- duration
- width
- height
- storage key/path
- thumbnail
- status
- source
- createdAt
- updatedAt

Jika field sudah ada, gunakan field existing.

Source dapat membedakan:

manual
downloader

Jika architecture existing sudah memiliki source field, gunakan itu.

Jika belum ada dan memang diperlukan, tambahkan dengan migration yang benar.

Contoh:

Media #001
source = manual
status = ready

Media #002
source = downloader
status = ready

Keduanya harus diperlakukan sama oleh Compose.

==================================================
COMPOSE
==================================================

Compose saat ini memiliki dropdown:

Media

yang menampilkan file seperti:

compose_test.mp4
web_ui_test.mp4
reel_missing.mp4
reel_e2e.mp4
reel_test.mp4

Jangan menghapus picker tersebut.

Perbaiki agar picker mengambil media dari Media API/storage layer yang benar.

HANYA tampilkan:

status = ready

Jangan tampilkan media yang masih:

uploading
processing
failed

Tambahkan kemampuan:

[ Upload Media ]

sehingga user dapat upload video manual tanpa harus masuk ke sistem terpisah jika architecture existing memang mendukung flow tersebut.

Jika repository sudah memiliki uploader di halaman lain, gunakan component/service tersebut kembali.

Jangan membuat uploader kedua.

==================================================
COMPOSE FLOW
==================================================

Target:

Compose

Content Type:
Reels

Media:

[ Upload Media ]

atau

[ Select existing media ]

User dapat:

A. Upload video baru

atau

B. Memilih video yang sudah ada dari:

- Manual Upload
- Downloader

Kemudian:

Caption

Publish to:

Facebook Page
Yourdreels

Publish now / Schedule

Publish

==================================================
FACEBOOK PUBLISHING
==================================================

Facebook Page Reels publishing yang sekarang SUDAH PASS.

JANGAN rewrite.

JANGAN mengganti Graph API flow.

JANGAN membuat provider Facebook baru.

JANGAN mengubah authentication/token flow.

JANGAN mengubah worker publishing flow jika tidak diperlukan.

Pastikan hanya media yang valid dan status ready yang diberikan ke publishing pipeline.

Existing successful flow harus tetap:

queued
→ uploading
→ published

dan Facebook harus menghasilkan:

publish_status = published
video_status = ready

serta permalink/externalId jika memang sudah tersedia.

==================================================
VALIDATION
==================================================

Untuk manual upload:

Validasi:

- MIME type
- extension
- file size
- video readability
- duration jika existing validator mendukung
- aspect ratio jika existing validator mendukung

Minimal video MP4 harus dapat diproses.

Jangan menambahkan restriction yang tidak diperlukan.

Jika backend sudah memiliki validator, gunakan validator existing.

==================================================
ERROR HANDLING
==================================================

Jangan menampilkan error generik jika backend sudah mengetahui penyebab sebenarnya.

Contoh:

Salah:

Failed to create the post from media.

Jika sebenarnya media masih uploading.

Harus:

Media is still uploading. Please wait until upload is complete.

Jika media belum finalized:

Media is not ready yet. Please wait for finalization.

Jika file invalid:

Unsupported video format.

Jika upload gagal:

Upload failed: <safe error message>

Jangan expose:

- access token
- API key
- internal secret
- raw provider response
- database credentials
- internal stack trace

==================================================
IMPORTANT: MISSING_MEDIA
==================================================

Sebelumnya ditemukan error:

missing_media

dan UI menampilkan:

Failed to create the post from media.

Audit root cause secara menyeluruh.

Pastikan:

Compose
→ memilih Media ID yang valid
→ backend dapat menemukan Media
→ storage object tersedia
→ media sudah finalized
→ worker dapat membaca media
→ Facebook provider menerima media
→ publishing berhasil.

Jangan hanya menyembunyikan error.

Perbaiki root cause.

==================================================
UPLOAD STORAGE
==================================================

Gunakan storage abstraction existing.

Repository sebelumnya menggunakan S3-compatible/MinIO/local development storage.

Jangan membuat storage baru.

Pastikan:

Manual Upload
→ storage existing

Downloader
→ storage existing

Facebook Publisher
→ media/storage existing

Jika presigned URL digunakan, pastikan URL tersebut dapat diakses oleh service yang memang membutuhkannya.

Jangan mengubah working storage architecture tanpa alasan.

==================================================
API
==================================================

Audit endpoint existing terlebih dahulu.

Cari endpoint seperti:

POST /api/media/upload

POST /api/media/finalize

GET /api/media

GET /api/media/:id

GET /api/media/:id/status

atau endpoint dengan fungsi yang sama.

Gunakan endpoint existing jika tersedia.

Jika endpoint missing:

buat endpoint minimal yang diperlukan.

Jangan membuat duplicate endpoint dengan fungsi sama.

Downloader juga harus menggunakan API/service/media ingestion yang sama jika architecture memungkinkan.

==================================================
FRONTEND
==================================================

Audit:

apps/web/src/app/compose/*
apps/web/src/components/*
atau struktur frontend existing.

Cari:

- Compose page
- media picker
- upload component
- media library
- API client
- upload handler

Reuse existing components.

Jika upload component sudah ada di Media Library:

gunakan component tersebut di Compose melalui reusable component.

Jangan copy-paste logic upload.

==================================================
BACKEND
==================================================

Audit:

- Media service
- Storage service
- Upload service
- Downloader service
- Worker
- Facebook provider
- Publishing service

Pastikan semua menggunakan Media entity yang sama.

Target:

Manual Upload
       \
        → MediaService → Storage
       /
Downloader

Bukan:

Manual Upload → ManualMediaService
Downloader → DownloaderMediaService

yang menghasilkan dua sistem berbeda.

==================================================
TESTING
==================================================

Setelah implementation selesai, WAJIB test end-to-end.

TEST 1 — MANUAL UPLOAD

Gunakan video baru dari local/device.

Flow:

local video
→ upload
→ finalize
→ status ready
→ muncul di Media Library
→ muncul di Compose
→ pilih video
→ pilih Facebook Page Yourdreels
→ publish
→ queue
→ worker
→ published

Verifikasi video benar-benar muncul di Facebook Page.

Jangan hanya memeriksa HTTP 200.

==================================================

TEST 2 — DOWNLOADER

Gunakan downloader existing.

Flow:

Downloader
→ download
→ Media
→ finalize
→ ready
→ Media Library
→ Compose
→ Facebook Page Yourdreels
→ Reels
→ publish
→ published

Verifikasi video benar-benar muncul di Facebook Page.

==================================================

TEST 3 — MEDIA READY GUARD

Upload media tetapi sebelum finalize selesai:

Media harus TIDAK muncul sebagai selectable di Compose.

Setelah:

status = ready

media harus muncul.

==================================================

TEST 4 — FAILED MEDIA

Simulasikan/gunakan media gagal.

Pastikan:

failed media tidak dapat dipublish.

UI harus memberikan error yang jelas.

==================================================
REGRESSION TEST
==================================================

Jalankan:

- typecheck
- lint
- unit tests
- API tests
- build
- existing Facebook regression tests

Pastikan Facebook publishing yang sebelumnya PASS tetap PASS.

Jangan menghapus test existing.

Jangan mengurangi jumlah test hanya agar build hijau.

==================================================
GIT SAFETY
==================================================

Sebelum commit:

git status
git diff

Pastikan:

- tidak ada secret
- tidak ada token
- tidak ada API key
- tidak ada credential
- tidak ada file pribadi

Jangan force push.

Jangan commit perubahan yang tidak berkaitan dengan task.

==================================================
OUTPUT YANG WAJIB DILAPORKAN
==================================================

Setelah selesai berikan:

1. EXISTING MEDIA SYSTEM
   - apa yang sudah ada
   - file/component/service yang digunakan

2. MANUAL UPLOAD
   - endpoint
   - component
   - storage flow
   - finalize flow

3. DOWNLOADER
   - bagaimana downloader masuk ke Media Pipeline

4. MEDIA LIFECYCLE
   - status yang digunakan
   - kapan menjadi ready

5. COMPOSE
   - bagaimana media ready muncul di picker

6. FACEBOOK
   - pastikan publishing flow existing tetap digunakan

7. FILES CHANGED
   - daftar file yang benar-benar diubah
   - alasan perubahan

8. TEST RESULTS
   - typecheck
   - lint
   - tests
   - build
   - manual upload E2E
   - downloader E2E
   - Facebook E2E

9. FACEBOOK VERIFICATION
   Tampilkan:

   FACEBOOK PAGE: Yourdreels
   CONTENT TYPE: Reels
   SOURCE: Manual / Downloader
   STATUS: PUBLISHED
   EXTERNAL ID: <id>
   PERMALINK: <permalink>

10. FINAL STATUS

Tampilkan:

MEDIA PIPELINE: PASS
MANUAL UPLOAD: PASS
DOWNLOADER INGESTION: PASS
MEDIA FINALIZE: PASS
MEDIA READY FILTER: PASS
COMPOSE MEDIA PICKER: PASS
FACEBOOK PAGE REELS: PASS
REGRESSION TEST: PASS
BUILD: PASS

==================================================
STOP CONDITION
==================================================

Jika Manual Upload sudah ada tetapi hanya tidak terhubung ke Compose:

JANGAN membuat uploader baru.

Jika Downloader sudah menghasilkan Media:

JANGAN membuat downloader baru.

Jika Media Library sudah ada:

JANGAN membuat Media Library baru.

Jika Facebook publishing sudah PASS:

JANGAN rewrite Facebook publishing.

Fokus hanya menyatukan:

MANUAL UPLOAD
+
DOWNLOADER
↓
ONE MEDIA PIPELINE
↓
MEDIA LIBRARY
↓
COMPOSE
↓
FACEBOOK PAGE REELS

Setelah seluruh test PASS dan Facebook Page benar-benar menampilkan Reel:

STOP.
````
# 
```
TASK: FIX WEB COMPOSE "FAILED TO CREATE THE POST FROM MEDIA"

Facebook Page publishing backend SUDAH TERBUKTI BERHASIL.

VERIFIED:
- Facebook Page: Yourdreels
- Publish Request: PASS
- Worker: PASS
- Facebook Reel: VERIFIED
- History: PASS
- Reel benar-benar muncul di Facebook Page
- Backend publishing flow sudah PASS

MASALAH SEKARANG HANYA DI WEB UI.

Di halaman Compose:
- Destination: Yourdreels (facebook)
- Video format: MP4
- Publish now
- Saat klik Publish muncul:

"Failed to create the post from media."

PENTING:
Jangan mengubah Facebook publishing flow yang sudah PASS.
Jangan mengubah Graph API publishing logic.
Jangan mengubah worker.
Jangan membuat mock success.
Jangan membuat workaround yang melewati web flow.

FOKUS HANYA:
Web Compose
→ create post from media
→ API request
→ response
→ queue/job creation

LANGKAH DEBUG:

1. Periksa frontend Compose dan cari fungsi/API yang dipanggil ketika tombol Publish ditekan.

2. Identifikasi endpoint POST yang digunakan untuk:
   "create post from media"

3. Periksa request payload yang dikirim frontend.

4. Periksa response HTTP sebenarnya:
   - status code
   - response body
   - error code
   - validation error
   - missing field
   - media ID
   - destination ID
   - content type
   - caption
   - publish mode

5. Cocokkan payload frontend dengan API contract/backend yang sebenarnya.

6. Periksa apakah frontend mengirim:
   - mediaId yang benar
   - destinationId yang benar
   - contentType yang benar
   - caption
   - publishNow/schedule data yang benar

7. Jika backend endpoint sebenarnya membutuhkan field tertentu tetapi frontend tidak mengirimnya, perbaiki frontend agar menggunakan contract backend yang benar.

8. Jika frontend memanggil endpoint yang salah, perbaiki endpoint frontend.

9. Jika backend endpoint menolak payload karena validation, jangan mematikan validation.
   Perbaiki payload frontend atau contract yang memang salah.

10. Gunakan browser/network log atau server log untuk mendapatkan error sebenarnya.

11. Setelah ditemukan root cause, lakukan perubahan MINIMAL.

REGRESSION RULE:

Setelah fix:

- Existing Facebook backend test harus tetap PASS.
- Worker test harus tetap PASS.
- Facebook Page publish test harus tetap PASS.
- Jangan merusak flow upload yang sudah berhasil.

TEST END-TO-END DARI WEB:

1. Buka Content Pilot melalui browser.
2. Compose.
3. Upload VIDEO BARU.
4. Pilih:
   Facebook Page → Yourdreels
5. Content type:
   Reels
6. Caption:
   Content Pilot Web Compose Test
7. Publish now.
8. Klik Publish.

WAJIB pastikan:

Web Compose
→ API create post from media
→ job dibuat
→ queued
→ uploading
→ publishing
→ published
→ History published
→ Reel benar-benar muncul di Facebook Page Yourdreels.

Jangan menyatakan PASS hanya karena API mengembalikan 200.

HASIL AKHIR:

WEB COMPOSE: PASS/FAIL
CREATE POST FROM MEDIA: PASS/FAIL
JOB CREATION: PASS/FAIL
QUEUE: PASS/FAIL
WORKER: PASS/FAIL
FACEBOOK PAGE: PASS/FAIL
FACEBOOK REEL VERIFIED: YES/NO
HISTORY: PASS/FAIL

ROOT CAUSE:
<jelaskan penyebab sebenarnya>

FILES CHANGED:
<daftar file>

TESTS:
<hasil test>

STOP setelah test selesai.

````
# Prompt — Test Facebook Page Publish via Web
```

TASK: TEST REAL FACEBOOK PAGE REEL THROUGH WEB UI

Web Content Pilot saat ini tidak bisa diakses / server mati.

Saya ingin kamu sekarang melakukan TEST END-TO-END melalui WEB UI yang sebenarnya.

JANGAN menambah fitur baru.
JANGAN redesign UI.
JANGAN membuat mock/fake success.
JANGAN mengubah flow Facebook publishing yang sudah terbukti PASS.
JANGAN melakukan refactor besar.

TUJUAN:
Pastikan user dapat membuka Content Pilot melalui browser dan melakukan:

Upload video
→ Compose
→ pilih Facebook Page "Yourdreels"
→ Publish now
→ Publish
→ Queue
→ Worker
→ Facebook Page
→ Reel benar-benar muncul
→ History = published

LANGKAH:

1. Periksa status service/project saat ini.
2. Jalankan service yang diperlukan agar WEB Content Pilot dapat diakses.
3. Pastikan frontend dan backend/API yang diperlukan benar-benar aktif.
4. Pastikan reverse proxy/nginx/Cloudflare route yang digunakan project mengarah ke service yang benar.
5. Jangan mengubah domain atau konfigurasi Cloudflare jika tidak diperlukan.

SETELAH WEB HIDUP:

6. Buka Content Pilot melalui browser.
7. Gunakan UI asli, bukan API/curl sebagai pengganti test.
8. Masuk ke halaman Compose.
9. Upload video test baru.
10. Pastikan upload berhasil.
11. Pilih destination:
    Facebook Page → Yourdreels
12. Pilih content type:
    Reel
13. Isi caption sederhana:
    Content Pilot Web Test
14. Pilih:
    Publish now
15. Klik Publish.

VERIFIKASI:

Pantau job dari UI dan backend sampai status:

queued
→ uploading
→ processing/publishing
→ published

Kemudian buka History.

Pastikan job menunjukkan:

Destination: Yourdreels (Facebook Page)
Content type: reels
Status: Published

SETELAH ITU:

16. Buka Facebook Page "Yourdreels" di browser.
17. Buka tab Reels.
18. Pastikan video test benar-benar muncul di Page.

PENTING:

Test harus menggunakan video BARU.

Jangan menganggap test berhasil hanya karena:
- API mengembalikan 200
- job menjadi published
- worker mengatakan success

Keberhasilan final harus diverifikasi dari Facebook Page bahwa Reel benar-benar muncul.

Jika gagal:

JANGAN langsung mengubah kode.

Catat titik kegagalannya:

A. Web server tidak hidup
B. Reverse proxy/Cloudflare
C. Frontend
D. Upload media
E. API request
F. Queue
G. Worker
H. Facebook publish
I. History/status update

Jika gagal di salah satu tahap, tampilkan error sebenarnya dan root cause berdasarkan log.

Jika server mati, hidupkan server terlebih dahulu.

Jika server sudah hidup tetapi Cloudflare menghasilkan 502, periksa service upstream, port listening, nginx/reverse proxy, dan koneksi localhost sebelum mengubah aplikasi.

Jangan menghapus data/job lama.

Jangan menjalankan test terhadap Facebook Profile pribadi.
TEST INI KHUSUS FACEBOOK PAGE "Yourdreels".

HASIL AKHIR WAJIB:

WEB STATUS: PASS/FAIL
WEB URL: <url>
UPLOAD: PASS/FAIL
FACEBOOK PAGE: Yourdreels
PUBLISH REQUEST: PASS/FAIL
WORKER: PASS/FAIL
FACEBOOK REEL: VERIFIED / NOT VERIFIED
HISTORY: PASS/FAIL

Jika Reel benar-benar terlihat di Facebook Page:

FACEBOOK PAGE REEL TEST: PASS

Jika belum terlihat:

FACEBOOK PAGE REEL TEST: FAIL

Jangan menyatakan PASS sebelum Reel benar-benar diverifikasi di Facebook Page.
STOP setelah test selesai.
````
# Prompt: Fix Facebook missing_media Without Breaking Successful Publishing
```

Kita lanjutkan debugging Facebook publishing.

Dari UI History ditemukan error nyata:

Destination: Yourdreels (Facebook Page)
Content type: video
Status: Failed
Error: missing_media

PENTING:
Facebook publishing sebelumnya SUDAH berhasil.
Jangan membongkar atau mengganti flow Facebook publishing yang sudah PASS.

Tujuan task ini hanya mencari dan memperbaiki root cause `missing_media`.

LANGKAH WAJIB:

1. Audit alur lengkap dari:
   Compose
   → media selection/upload
   → media/storage record
   → publishing job
   → queue
   → worker
   → Facebook provider
   → publish.

2. Cari semua lokasi yang dapat menghasilkan error:
   `missing_media`

3. Bandingkan:
   - job Facebook yang berhasil published sebelumnya
   - job Facebook yang gagal dengan missing_media.

4. Periksa database/job payload:
   - mediaId
   - media URL
   - storage key
   - MIME type
   - file path
   - media record
   - job payload
   - destinationId
   - post/content ID

5. Pastikan worker mengambil media dari sumber storage yang benar.

6. Jangan menggunakan fake media URL.
   Jangan membuat dummy success.
   Jangan bypass validasi media hanya supaya job menjadi published.

7. Jika media sebenarnya sudah tersimpan tetapi worker kehilangan referensinya:
   perbaiki persistence/serialization job agar media reference tetap tersedia ketika job masuk queue.

8. Jika media record terhapus terlalu cepat:
   perbaiki lifecycle media agar media tetap tersedia sampai publishing selesai.

9. Jika masalah berasal dari upload/finalize:
   perbaiki hubungan antara upload → finalized media → publishing job.

10. Pastikan retry terhadap job tidak kehilangan media reference.

11. Jangan mengubah:
   - Facebook authentication
   - Page connection
   - Page ID
   - Facebook provider architecture
   - successful publishing flow
   kecuali audit membuktikan bagian tersebut memang penyebab langsung.

12. Setelah perbaikan:
   - typecheck
   - lint
   - test
   - build

13. Buat test regression khusus:
   - create media
   - create publishing job dengan mediaId
   - worker membaca media
   - media tetap tersedia
   - Facebook provider menerima media yang benar.

14. Jalankan satu test publishing nyata ke Facebook Page `Yourdreels` menggunakan video test baru.

15. Verifikasi end-to-end:

upload
→ media finalized
→ job queued
→ worker processing
→ Facebook upload
→ Facebook publish
→ status published
→ History menunjukkan Published.

JANGAN hanya mengubah UI agar `missing_media` hilang.

JANGAN menghapus job lama dari database hanya untuk membersihkan History.

JANGAN menganggap sukses hanya berdasarkan response internal.

Sukses harus diverifikasi dari Facebook Page sebenarnya.

OUTPUT:

ROOT CAUSE:
<penyebab sebenarnya>

FIX:
<file dan perubahan>

REGRESSION TEST:
<PASS/FAIL>

FACEBOOK REAL PUBLISH:
<PASS/FAIL>

HISTORY STATUS:
<PUBLISHED/FAILED>

TYPECHECK:
<PASS/FAIL>

LINT:
<PASS/FAIL>

TEST:
<PASS/FAIL>

BUILD:
<PASS/FAIL>

GIT STATUS:
<status>

Jika semuanya berhasil, commit perubahan dengan pesan:

fix: resolve facebook missing media publishing

Push ke branch aktif dan verifikasi remote.

STOP setelah verifikasi.
````
# Prompt: Fix Web 502 — Jangan Ganggu Facebook
```

# Prompt — Fix Web 502 Without Changing Facebook Publishing

Kita lanjut dari kondisi terakhir.

STATUS PENTING:
- Facebook Upload: PASS
- Facebook Publish: PASS
- Job Worker: PASS
- Status Update: PASS
- History: PASS
- Flow: queued → processing → publishing → published
- Graph API mengonfirmasi publish_status = published
- Facebook Reel sudah berhasil dibuat.

JANGAN mengubah atau merusak Facebook uploader/publisher yang sudah PASS.

Masalah yang sekarang harus diperbaiki hanya:

https://contentpilot.biz.id

mengembalikan:

502 Bad Gateway
Cloudflare

## TUJUAN

Cari root cause kenapa domain contentpilot.biz.id mendapatkan HTTP 502 dan perbaiki akses web tanpa mengubah logic Facebook publishing.

## LANGKAH WAJIB

1. Audit service yang menjalankan frontend/web.
2. Audit service backend/API.
3. Cek process yang sedang berjalan.
4. Cek port yang digunakan masing-masing service.
5. Cek systemd/service manager jika digunakan.
6. Cek konfigurasi nginx/reverse proxy.
7. Cek upstream yang digunakan nginx.
8. Cek apakah frontend/web benar-benar listening.
9. Cek apakah backend/API benar-benar listening.
10. Test langsung dari server menggunakan localhost/127.0.0.1 terhadap port upstream.
11. Test domain dari server.
12. Periksa nginx error log.
13. Periksa service log.
14. Periksa apakah ada service yang crash atau restart loop.
15. Periksa konfigurasi Cloudflare hanya jika diperlukan.

Gunakan diagnosis berdasarkan hasil command nyata.

JANGAN menebak port.

## ATURAN PENTING

Jangan:
- mengubah Facebook provider
- mengubah Facebook publishing flow
- mengubah Graph API
- mengubah upload flow
- mengubah worker publishing
- mengubah database publishing
- menghapus file
- melakukan refactor besar
- mengganti arsitektur
- membuat fake endpoint
- membuat fake success response

Fokus hanya pada:
WEB → NGINX → BACKEND/FRONTEND → DOMAIN

## PERBAIKAN

Setelah menemukan root cause:

1. Perbaiki hanya konfigurasi/service yang menyebabkan 502.
2. Restart hanya service yang memang diperlukan.
3. Jangan restart worker Facebook jika tidak diperlukan.
4. Validasi service setelah restart.
5. Test localhost.
6. Test melalui nginx.
7. Test domain.
8. Pastikan HTTP response kembali normal.

## VERIFIKASI AKHIR

Pastikan:

WEB STATUS: PASS
API STATUS: PASS
DOMAIN STATUS: PASS
HTTP STATUS: 200 atau status aplikasi yang benar

Dan pastikan:

FACEBOOK UPLOAD: PASS
FACEBOOK PUBLISH: PASS
JOB WORKER: PASS

## GIT

Sebelum perubahan:
- git status
- catat file yang akan diubah

Setelah perubahan:
- git diff
- pastikan tidak ada secret
- jalankan test/build yang relevan
- jangan commit perubahan Facebook yang tidak diperlukan

Jika masalah hanya konfigurasi server dan tidak menyentuh repository, tidak perlu membuat perubahan kode.

## FINAL REPORT

Laporkan:

ROOT CAUSE:
...

FILE/SERVICE YANG DIPERBAIKI:
...

PORT:
...

NGINX STATUS:
...

WEB STATUS: PASS/FAIL
API STATUS: PASS/FAIL
DOMAIN STATUS: PASS/FAIL

FACEBOOK PUBLISHING:
UNCHANGED / PASS

Jangan lanjut mengerjakan fitur lain setelah 502 berhasil diperbaiki.
STOP.
````
# Prompt — Fix Facebook Publishing Status
```
# Prompt — Fix Facebook Reels Job Status

Fokus hanya pada masalah berikut:

Facebook Reels sudah berhasil dipublish ke Facebook Page.
Saya sudah memverifikasi Reel muncul di Facebook Page.

Namun di Content Pilot → History, publishing job masih berstatus:

Queued

Padahal seharusnya setelah Facebook berhasil menerima/publish Reel:

Queued → Processing/Publishing → Published

TASK:

1. Audit flow Facebook publishing yang sekarang.
2. Jangan mengubah UI/design.
3. Jangan mengubah Facebook uploader yang sudah berhasil.
4. Jangan membuat uploader baru.
5. Jangan mengubah destination/Page selection.
6. Jangan mengubah storage/upload flow yang sudah PASS.

Cari penyebab kenapa job tetap `queued` setelah Facebook berhasil publish.

Periksa terutama:

- PublishingJob lifecycle
- queue worker
- worker execution
- Facebook provider publish result
- Facebook response/result ID
- status update setelah publish berhasil
- database transaction
- polling/status verification jika digunakan
- worker acknowledgement/completion
- retry/error handling
- History API yang membaca status job

Pastikan alurnya menjadi:

Upload media
→ create PublishingJob
→ queued
→ worker mengambil job
→ processing
→ Facebook publish
→ Facebook berhasil
→ simpan Facebook post/reel ID
→ update PublishingJob = published
→ simpan publishedAt
→ History membaca status terbaru

Jika Facebook API sudah mengembalikan success tetapi worker tidak mengubah status database, perbaiki bagian tersebut.

Jika worker sebenarnya tidak berjalan, cari penyebabnya dan perbaiki worker/queue agar job benar-benar dieksekusi.

Jangan menggunakan fake success.
Status `published` hanya boleh diberikan setelah provider Facebook benar-benar mengembalikan keberhasilan.

Tambahkan/pertahankan informasi penting:

- provider
- destinationId
- providerPostId/reelId
- status
- publishedAt
- error jika gagal
- attempt count

Setelah perbaikan:

1. typecheck
2. lint
3. test yang relevan
4. build
5. restart service jika diperlukan
6. lakukan test upload Facebook Reels
7. verifikasi Reel benar-benar muncul di Facebook Page
8. verifikasi History berubah dari `Queued` menjadi `Published`

Jangan menyentuh provider lain.

Jangan mengubah UI.

Jangan melakukan refactor besar.

OUTPUT:

FACEBOOK UPLOAD: PASS/FAIL
FACEBOOK PUBLISH: PASS/FAIL
JOB WORKER: PASS/FAIL
STATUS UPDATE: PASS/FAIL
HISTORY: PASS/FAIL
BUILD: PASS/FAIL
TEST: PASS/FAIL

Jika semua PASS, tampilkan juga:

Publishing flow:
queued → processing → publishing → published

STOP setelah masalah ini selesai.

````
# Prompt — Fix Upload Failure
```
Prompt: Fix Upload Failure

Debug masalah upload pada Content Pilot yang sekarang muncul di UI:

"Upload failed. Please check your connection and retry."

KONDISI SAAT INI:
- Frontend production: https://contentpilot.biz.id
- API production: https://api.contentpilot.biz.id
- Facebook connection sudah berhasil.
- Facebook live publishing sebelumnya sudah berhasil.
- UI Compose sudah berjalan.
- History sudah menampilkan publishing job.
- Server/restart sebelumnya sudah berhasil.
- Jangan mengubah design/UI kecuali benar-benar diperlukan untuk memperbaiki error.

TUGAS:

1. Audit seluruh upload flow dari frontend sampai backend.
2. Telusuri request:
   frontend
   → /api/media/upload
   → storage/presigned upload
   → /api/media/finalize
3. Cari penyebab sebenarnya dari "Upload failed".
4. Periksa browser/API response, HTTP status, request URL, CORS, authentication, presigned URL, storage configuration, dan backend logs.
5. Pastikan production frontend TIDAK menggunakan localhost:4000.
6. Pastikan API production menggunakan:
   https://api.contentpilot.biz.id
7. Jangan membuat fake success.
8. Jangan bypass error hanya agar UI terlihat berhasil.
9. Jangan mengubah Facebook publishing logic yang sudah PASS.
10. Jangan mengubah design system.
11. Jangan menghapus test yang sudah PASS.

Jika menemukan masalah:
- perbaiki akar masalahnya
- pertahankan architecture yang sekarang
- gunakan error handling yang jelas
- jangan expose token/credential ke frontend atau response

SETELAH PERBAIKAN:

Jalankan:
- typecheck
- lint
- tests
- build

Kemudian restart/reload service production jika memang diperlukan.

Verifikasi:

GET https://api.contentpilot.biz.id/health
GET https://api.contentpilot.biz.id/ready
GET https://api.contentpilot.biz.id/api/platforms

Lakukan test upload menggunakan file test kecil.

Pastikan:
1. upload berhasil
2. finalize berhasil
3. media tercatat
4. tidak ada localhost:4000 di production bundle
5. tidak ada secret/token di Git diff
6. Facebook regression tetap PASS
7. UI tidak rusak

Jangan melakukan redesign.

Di akhir tampilkan:

UPLOAD STATUS: PASS/FAIL
UPLOAD ROOT CAUSE: ...
API STATUS: PASS/FAIL
BUILD: PASS/FAIL
TESTS: PASS/FAIL
FACEBOOK REGRESSION: PASS/FAIL
SERVER RESTART: SUCCESS/NOT REQUIRED/FAIL
GIT STATUS: ...
COMMIT: ...
PUSH STATUS: ...

STOP setelah debugging upload selesai.

````
# Prompt — Start Server untuk Preview UI
```

Jalankan server Content Pilot agar saya bisa melihat UI terbaru.

ATURAN:
1. Jangan mengubah source code.
2. Jangan mengubah UI.
3. Jangan melakukan commit atau push.
4. Jangan menjalankan migration.
5. Jangan mengubah .env atau credential.
6. Periksa terlebih dahulu service/server yang sedang berjalan.
7. Jika production server sudah aktif dan melayani build terbaru, jangan restart tanpa alasan.
8. Jika server belum berjalan, jalankan server dengan cara yang sesuai dengan repository.
9. Pastikan frontend dapat diakses melalui:
   https://contentpilot.biz.id
10. Pastikan API production tetap menggunakan:
   https://api.contentpilot.biz.id
11. Verifikasi endpoint:
   /health
   /ready
   /api/platforms
   /accounts
12. Setelah server aktif, tampilkan:
   - server status
   - frontend URL
   - API URL
   - port yang digunakan
   - apakah build terbaru sedang aktif

STOP setelah server berhasil aktif.

SERVER STATUS: READY
FRONTEND: <URL>
API: <URL>
````
# Prompt — Resume Visual UI
```

Lanjutkan pekerjaan UI Content Pilot dari kondisi repository saat ini.

PENTING:
Model/session ini harus memiliki kemampuan membaca gambar.

Reference utama:
docs/design-reference/admin-dashboard-reference.png

1. Buka dan lihat gambar reference tersebut secara visual.
2. Bandingkan dengan UI Content Pilot saat ini.
3. Identifikasi perbedaan layout, spacing, typography, colors, cards, navigation, buttons, badges, responsive behavior, dan visual hierarchy.
4. Implementasikan perubahan UI agar mengikuti reference sedekat mungkin.
5. Jangan mengubah backend/API/Facebook publishing yang sudah PASS.
6. Jangan membuat fitur baru di luar UI.
7. Jangan menebak desain jika gambar tidak dapat dibaca.

Setelah perubahan:
- mobile check
- desktop check
- typecheck
- lint
- tests
- build
- review git diff
- pastikan tidak ada secret

Jika model TIDAK bisa membaca image:
STOP SEGERA dan tampilkan:
VISUAL REFERENCE: NOT ACCESSIBLE

Jangan melakukan perubahan kode berdasarkan asumsi.

Jika image berhasil dibaca, lanjutkan implementasi UI sampai selesai, lalu commit dan push.
````
# Prompt: Restart Content Pilot — Visual Reference UI
```
# Prompt Restart — Content Pilot UI Reference

Lanjutkan project Content Pilot dari kondisi repository SAAT INI.

JANGAN mengulang pekerjaan yang sudah selesai.
JANGAN melakukan audit dari awal.
Baca kondisi repository, git history, dan perubahan terakhir terlebih dahulu.

## KONDISI TERAKHIR

Project:
Content Pilot

Repository:
`/root/content-pilot`

Reference design:
`docs/design-reference/admin-dashboard-reference.png`

Reference image tersebut adalah DESIGN UTAMA yang harus digunakan untuk UI Content Pilot.

Model/session ini memiliki kemampuan vision/image input.

## TUGAS UTAMA SEKARANG

Buka dan ANALISIS gambar:

`docs/design-reference/admin-dashboard-reference.png`

Jangan hanya membaca nama file.

Gunakan kemampuan vision untuk benar-benar melihat gambar dan memahami:

- layout
- sidebar
- topbar
- navigation
- card
- typography
- warna
- spacing
- border
- radius
- button
- badge
- icon
- table/grid
- responsive behavior
- mobile layout
- desktop layout
- visual hierarchy
- empty state
- loading state
- status indicator

Kemudian bandingkan desain tersebut dengan UI Content Pilot yang sekarang.

## ATURAN VISUAL

Gambar reference adalah sumber kebenaran visual.

Jangan membuat desain berdasarkan asumsi.

Jangan membuat design system baru jika elemen yang dibutuhkan sudah terlihat pada reference.

Jangan mengganti backend/API/provider yang sudah bekerja.

Jangan merusak Facebook publishing yang sudah PASS.

Fokus pada UI/UX.

Jika ada perbedaan antara UI sekarang dan reference:

→ sesuaikan UI agar sedekat mungkin dengan reference.

Pertahankan fungsi existing.

## PRIORITAS

Urutan pekerjaan:

1. Baca reference image.
2. Audit UI existing.
3. Identifikasi perbedaan.
4. Buat rencana perubahan kecil dan terkontrol.
5. Implementasikan UI.
6. Pastikan responsive desktop.
7. Pastikan responsive mobile.
8. Pastikan Facebook UI/regression tetap PASS.
9. Jalankan typecheck.
10. Jalankan lint.
11. Jalankan tests.
12. Jalankan build.
13. Review git diff.
14. Commit perubahan.
15. Push ke branch aktif.
16. Verifikasi remote.

## PENTING

Jangan berhenti hanya karena sebelumnya model tidak bisa membaca image.

Sekarang gunakan vision secara langsung.

Jika gambar berhasil dibaca:
lanjutkan implementation.

Jika gambar ternyata benar-benar tidak dapat dibaca oleh session ini:
STOP dan laporkan:

VISUAL REFERENCE: NOT ACCESSIBLE

Jangan menebak desain.

## SCOPE

Untuk sekarang fokus pada UI Content Pilot.

Jangan mulai:

- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn
- fitur publishing baru

Facebook yang sudah bekerja harus tetap aman.

## QUALITY CHECK

Setelah implementation:

UI STATUS: PASS / FAIL
DESKTOP UI: PASS / FAIL
MOBILE UI: PASS / FAIL
FACEBOOK REGRESSION: PASS / FAIL
TYPECHECK: PASS / FAIL
LINT: PASS / FAIL
TEST: PASS / FAIL
BUILD: PASS / FAIL

Jika ada failure, perbaiki sebelum commit.

## GIT

Sebelum commit:

- git status
- review git diff
- pastikan tidak ada secret/token/.env
- jangan commit perubahan yang tidak berhubungan dengan UI

Commit message:

feat(web): align content pilot ui with visual reference

Push ke branch aktif.

Setelah selesai tampilkan:

UI STATUS: PASS
REFERENCE STATUS: APPLIED
DESKTOP: PASS
MOBILE: PASS
FACEBOOK REGRESSION: PASS
TYPECHECK: PASS
LINT: PASS
TEST: PASS
BUILD: PASS
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

STOP setelah selesai.

````
# Prompt — Paksa Verifikasi Reference Image
```

# UI DESIGN REFERENCE — VISUAL VERIFICATION

Jangan melakukan perubahan kode terlebih dahulu.

Saya sudah menaruh gambar desain reference di:

docs/design-reference/

Tugas pertama kamu hanya melakukan verifikasi.

1. Periksa seluruh file di docs/design-reference/.
2. Pastikan file gambar benar-benar ada.
3. Untuk setiap gambar, gunakan kemampuan image/vision yang tersedia pada session ini untuk MEMBUKA DAN MELIHAT gambar secara visual.
4. Jangan hanya membaca nama file, metadata, atau ukuran file.
5. Jangan menebak isi desain.
6. Jangan membuat perubahan kode jika kamu tidak dapat melihat gambar secara visual.

Jika session/model ini TIDAK memiliki kemampuan untuk melihat gambar secara visual, berhenti dan laporkan:

VISUAL REFERENCE: NOT ACCESSIBLE

Jangan melakukan implementasi UI berdasarkan asumsi.

Jika gambar berhasil dilihat, laporkan secara singkat:

REFERENCE IMAGES: FOUND
VISUAL ACCESS: PASS
IMAGES REVIEWED: <jumlah>
PAGES/SCREENS IDENTIFIED: <daftar>
READY FOR UI IMPLEMENTATION: YES

Setelah itu STOP dan tunggu instruksi berikutnya.

Jangan coding.
Jangan mengubah file.
Jangan commit.
Jangan push.
````
# Prompt — Implement UI Mengikuti Design Reference
```

# CONTENT PILOT — IMPLEMENT UI FROM DESIGN REFERENCE

Saya sudah menyediakan gambar referensi desain UI di repository.

WAJIB baca dan lihat seluruh gambar di:

docs/design-reference/

Gambar di folder tersebut adalah DESIGN REFERENCE UTAMA untuk UI Content Pilot.

==================================================
ATURAN UTAMA
==================================================

Sebelum mengubah kode UI:

1. List seluruh file di:
   docs/design-reference/

2. Buka dan lihat setiap gambar desain yang relevan.

3. Pelajari visual design secara langsung.

4. Audit UI existing.

5. Bandingkan UI existing dengan design reference.

6. Implementasikan UI agar mengikuti design reference.

JANGAN hanya membaca nama file atau README.
JANGAN hanya mengandalkan deskripsi prompt.
WAJIB melihat gambar sebenarnya.

==================================================
YANG HARUS DIIKUTI DARI GAMBAR
==================================================

Gunakan gambar sebagai acuan untuk:

- layout
- sidebar
- navigation
- header
- typography
- font sizing
- spacing
- card layout
- border
- border radius
- button
- input
- status badge
- icon placement
- colors
- visual hierarchy
- empty state
- loading state
- error state
- content width
- grid
- responsive behavior
- mobile layout
- desktop layout

Tujuannya bukan membuat UI yang "mirip secara umum".

Tujuannya adalah membuat UI project mengikuti design reference sedekat mungkin secara visual, sambil tetap mempertahankan functionality existing.

==================================================
JANGAN COPY GAMBAR
==================================================

Gambar hanya sebagai reference.

JANGAN:

- menggunakan screenshot sebagai background
- memasukkan screenshot sebagai UI
- membuat halaman berupa gambar
- membuat mockup statis
- mengganti UI dengan image

Implementasikan design menggunakan:

- React/Next.js component existing
- CSS existing
- design tokens
- reusable components
- icon library yang sudah digunakan project

==================================================
PENTING — FUNCTIONALITY HARUS TETAP
==================================================

UI redesign TIDAK BOLEH merusak functionality yang sudah bekerja.

Pertahankan:

- authentication
- Accounts
- Facebook OAuth
- Facebook connection
- destination discovery
- reconnect
- disconnect
- token handling
- upload
- media handling
- publishing
- API integration
- queue
- scheduler
- history
- status
- existing API endpoints

Jangan mengubah backend hanya demi menyesuaikan tampilan.

Jika UI membutuhkan data yang belum tersedia:

gunakan empty state.

JANGAN membuat fake data atau fake success.

==================================================
CONTENT PILOT DESIGN SYSTEM
==================================================

Ikuti visual language dari gambar reference.

Target:

- modern SaaS
- premium
- clean
- professional
- dark UI
- compact tetapi tidak padat
- jelas secara visual
- nyaman digunakan di mobile
- nyaman digunakan di desktop

Jangan menambahkan design style baru yang bertentangan dengan reference.

Jika terdapat perbedaan antara UI existing dan gambar reference:

prioritaskan gambar reference untuk visual,
tetapi prioritaskan functionality existing untuk behavior.

==================================================
COMPONENT REUSE
==================================================

Sebelum membuat component baru:

audit component existing.

Jika component sudah tersedia dan dapat digunakan:

REUSE.

Jangan membuat duplicate:

- Button
- Card
- Badge
- StatusBadge
- Input
- Modal
- Navigation
- PlatformCard
- DestinationCard
- EmptyState
- LoadingState

Jika component existing perlu diperbaiki:

perbaiki component tersebut daripada membuat duplicate.

==================================================
PAGE YANG HARUS DIPERBAIKI
==================================================

Ikuti gambar reference untuk memperbaiki UI:

1. Dashboard
2. Accounts
3. Platforms
4. Upload
5. Media Library
6. Queue Manager
7. Scheduler
8. History
9. Status
10. Facebook destination/account UI

Jika beberapa page belum tersedia atau belum menjadi scope:

jangan membuat functionality palsu.

==================================================
ACCOUNTS UI
==================================================

Accounts harus terlihat seperti design reference.

Tampilkan informasi yang benar-benar berasal dari backend:

- platform
- account
- connection status
- destinations
- scopes/capabilities jika tersedia
- actions

Actions existing harus tetap bekerja:

- Connect
- Reconnect
- Refresh
- Disconnect
- View destinations
- Connect another

Jika API unavailable:

buat error state yang rapi.

Contoh:

API unavailable

Unable to connect to the Content Pilot API.

[Retry]

Jangan hanya menampilkan error teknis mentah.

==================================================
FACEBOOK UI
==================================================

Facebook adalah provider yang sudah bekerja.

Jangan merusak implementation Facebook.

UI Facebook harus mengikuti gambar reference.

Pertahankan:

- connection
- destination
- page
- publishing capability
- upload
- publishing flow

Jika publishing benar-benar tersedia:

tampilkan status berdasarkan data backend.

Jangan hardcode:

"Connected"

jika sebenarnya backend mengatakan disconnected.

==================================================
RESPONSIVE DESIGN
==================================================

WAJIB mengikuti gambar reference pada mobile dan desktop.

Test minimal:

360px
390px
430px
768px
1024px
desktop

Pastikan:

- tidak ada horizontal overflow
- tidak ada text overlap
- tidak ada button terpotong
- card tidak keluar layar
- grid collapse dengan benar
- navigation tetap usable
- touch target nyaman
- spacing tetap proporsional

Mobile bukan sekadar desktop yang diperkecil.

Implementasikan responsive layout yang benar.

==================================================
LOADING / EMPTY / ERROR
==================================================

Ikuti visual style dari design reference.

Loading:

gunakan skeleton jika memungkinkan.

Empty:

gunakan icon + title + description + CTA.

Error:

gunakan status indicator + message + retry.

Jangan menampilkan:

Loading...

sebagai satu-satunya loading UI jika design reference menunjukkan skeleton.

==================================================
VISUAL QA
==================================================

Setelah implementation:

bandingkan hasil UI dengan:

docs/design-reference/

Lakukan visual review.

Cari:

- layout mismatch
- spacing mismatch
- typography mismatch
- color mismatch
- card mismatch
- button mismatch
- responsive mismatch
- alignment mismatch

Perbaiki mismatch yang signifikan.

Jangan berhenti hanya karena build berhasil.

Build PASS ≠ UI sudah selesai.

==================================================
BACKEND REGRESSION
==================================================

Setelah UI selesai, jalankan test yang tersedia.

Minimal:

typecheck
lint
tests
build

Pastikan Facebook regression tetap PASS.

Jangan menghapus test hanya karena test gagal setelah redesign.

Jika ada failure:

investigasi dan perbaiki.

==================================================
GIT SAFETY
==================================================

Sebelum commit:

git status
git diff

Pastikan tidak ada:

.env
API key
OAuth token
password
secret

Pastikan gambar reference memang berada di:

docs/design-reference/

Jangan menghapus gambar reference.

==================================================
COMMIT
==================================================

Jika semua verification PASS:

commit perubahan dengan:

feat(web): implement ui from design reference

Push ke branch aktif.

Setelah push:

verifikasi remote.

Laporkan:

UI STATUS: PASS
DESKTOP: PASS
MOBILE: PASS
FACEBOOK REGRESSION: PASS
TYPECHECK: PASS
LINT: PASS
TEST: PASS
BUILD: PASS

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS
REMOTE VERIFIED: YES

==================================================
STOP CONDITION
==================================================

Setelah UI selesai, verification PASS, dan push berhasil:

STOP.

Jangan:

- menambah provider baru
- mengubah Facebook backend
- membuat YouTube
- membuat Instagram
- membuat TikTok
- melakukan refactor besar
- mengubah architecture core

Fokus task ini HANYA:

"Implement UI Content Pilot berdasarkan gambar di docs/design-reference/."

Jika gambar reference menunjukkan sesuatu yang belum ada di UI, implementasikan bagian UI tersebut hanya jika functionality backend yang diperlukan memang sudah tersedia.

Jika belum tersedia, buat UI state yang jujur seperti:

Coming Soon
Unavailable
Not connected

Jangan membuat fake functionality.

==================================================
FINAL REPORT
==================================================

Berikan ringkasan:

1. Gambar reference yang digunakan
2. Page yang diperbaiki
3. Component yang dibuat/reused
4. Responsive changes
5. Facebook regression result
6. Typecheck
7. Lint
8. Tests
9. Build
10. Git commit
11. Push status

STOP setelah laporan.
````
# Prompt: Buat Folder Design Reference
```
Buat folder khusus untuk menyimpan gambar referensi desain UI Content Pilot.

Folder:

docs/design-reference/

Jangan membuat atau mengubah UI apa pun sekarang.

Jangan mengubah backend.
Jangan mengubah API.
Jangan mengubah Facebook provider.
Jangan mengubah database.
Jangan melakukan refactor.

Yang perlu dilakukan hanya:

1. Buat folder:
   docs/design-reference/

2. Buat file README.md di dalam folder tersebut yang menjelaskan bahwa folder ini digunakan untuk menyimpan gambar/screenshot/reference desain UI Content Pilot.

3. README.md harus menjelaskan:

   - gambar di folder ini adalah visual reference
   - AI/coding agent wajib melihat gambar sebelum mengerjakan redesign UI
   - gambar tidak boleh digunakan sebagai background atau asset UI secara langsung kecuali memang diperintahkan
   - implementasi harus dibuat menggunakan component/UI code asli project
   - gambar reference tidak boleh mengubah logic backend atau API
   - nama file gambar sebaiknya jelas dan deskriptif

4. Jangan membuat gambar dummy.

5. Jangan membuat file PNG/JPG placeholder.

6. Jangan menambahkan dependency baru.

7. Jangan mengubah file lain di luar:
   docs/design-reference/

Setelah selesai, tampilkan:

DESIGN REFERENCE FOLDER: CREATED

PATH:
docs/design-reference/

FILES:
docs/design-reference/README.md

STATUS:
READY FOR IMAGE UPLOAD

STOP.

Saya akan mengupload gambar desain sendiri ke folder tersebut setelah prompt ini selesai.

````
# Prompt berikutnya — Fix Production API URL
```

Prompt: Fix Production API Base URL

Audit dan perbaiki masalah pada frontend Content Pilot.

Saat production dibuka melalui:
https://contentpilot.biz.id

halaman /accounts menampilkan:
"API unreachable"
"Couldn't reach the API at http://localhost:4000"

Padahal hasil server verification:
- API /health = 200
- API /ready = 200
- web = 200
- /accounts = 200
- /platforms = 200
- /upload = 200
- latest build active = YES

Tugas:

1. Cari semua penggunaan hardcoded:
   http://localhost:4000
   localhost:4000
   atau API URL development yang dipakai frontend.

2. Audit bagaimana frontend menentukan API base URL.

3. Buat konfigurasi yang benar untuk development dan production.
   Production JANGAN mengarah ke localhost.

4. Jika architecture memungkinkan same-origin API, gunakan mekanisme production yang paling aman dan konsisten dengan routing/nginx yang sudah ada.

5. Jangan mengubah Facebook provider, OAuth, token, publishing flow, database, worker, queue, atau scheduler.

6. Jangan membuat fake API response.

7. Jangan mengubah credential atau .env production tanpa alasan.

8. Pastikan /accounts dapat mengambil status API dan data Facebook melalui endpoint production.

9. Pastikan development tetap dapat menggunakan localhost jika memang diperlukan.

10. Setelah perubahan:
   - typecheck
   - lint
   - build
   - test terkait frontend/API
   - jalankan production verification

11. Restart service jika diperlukan agar build terbaru aktif.

12. Verifikasi melalui public URL:
   /accounts
   /platforms
   /upload

13. Pastikan browser production TIDAK lagi mencoba http://localhost:4000.

14. Jangan melakukan git reset atau force push.

15. Commit perubahan jika semua verification PASS dan push ke branch aktif.

Laporkan:

API URL AUDIT: PASS
LOCALHOST REFERENCES REMOVED FROM PRODUCTION: YES/NO
TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
BUILD: PASS/FAIL
TESTS: PASS/FAIL
PRODUCTION API: PASS/FAIL
ACCOUNTS: PASS/FAIL
PLATFORMS: PASS/FAIL
UPLOAD: PASS/FAIL
SERVER RESTART: SUCCESS/NOT NEEDED/FAILED
GIT STATUS: CLEAN/DIRTY
COMMIT: <hash>
PUSH: SUCCESS/FAILED

STOP setelah selesai.
````
# Prompt: Restart & Verify Production
```
Restart server Content Pilot setelah perubahan UI terakhir.

Lakukan:
1. Identifikasi process manager yang sedang menjalankan web/API (PM2/systemd/docker/etc).
2. Restart service yang benar, jangan mematikan service yang tidak terkait.
3. Pastikan API kembali healthy.
4. Pastikan web production kembali HTTP 200.
5. Verifikasi bundle terbaru sudah aktif.
6. Jangan mengubah source code.
7. Jangan mengubah .env atau credential.
8. Jangan melakukan git reset/force push.

Setelah restart, cek:
- https://contentpilot.biz.id
- /accounts
- /platforms
- /upload

Laporkan:
SERVER RESTART: SUCCESS/FAILED
API HEALTH: PASS/FAIL
WEB: PASS/FAIL
LATEST BUILD ACTIVE: YES/NO
GIT STATUS: CLEAN/DIRTY

STOP setelah verifikasi.

```
# Prompt: Facebook UI Final Polish
# 
```

# Prompt — Facebook UI Final Polish

Project: Content Pilot

STATUS SAAT INI:
- Facebook OAuth: PASS
- Facebook connection: PASS
- Facebook destination/Page discovery: PASS
- Facebook token/Graph API access: PASS
- Facebook media upload: PASS
- Facebook publishing flow: PASS
- Live Facebook publish test: PASS
- UI upload/preview: PASS
- API typecheck: PASS
- Web typecheck: PASS
- Lint: PASS
- Build: PASS

JANGAN mengubah atau merusak logic Facebook yang sudah PASS.

Fokus pekerjaan kali ini HANYA pada UI/UX polish dan kualitas frontend.

==================================================
1. AUDIT UI EXISTING
==================================================

Audit halaman yang berhubungan dengan:

- Accounts
- Platforms
- Facebook connection
- Facebook Pages / Destinations
- Upload
- Video preview
- Publishing
- Status
- History

Gunakan UI yang sudah ada.

JANGAN membuat halaman duplicate.

JANGAN membuat design system baru jika existing design system sudah cukup.

==================================================
2. TARGET DESIGN
==================================================

Buat UI terlihat seperti produk SaaS modern/profesional.

Prinsip:

- clean
- modern
- premium
- minimal
- responsive
- mobile-first
- desktop-friendly
- konsisten
- mudah dipahami
- tidak terlalu banyak whitespace
- tidak terlalu banyak border
- hierarchy informasi jelas

Pertahankan tema dark yang sudah digunakan Content Pilot.

Gunakan accent biru yang sudah ada secara konsisten.

Jangan mengganti branding secara drastis.

==================================================
3. ACCOUNTS UI
==================================================

Perbaiki halaman Accounts.

Card Facebook harus memiliki hierarchy yang jelas:

Facebook
Connected

Account
Nino Kuye

Status
Connected

Destinations
1 Page

Scopes
...

Actions:
- View Pages
- Refresh
- Reconnect
- Connect another
- Disconnect

Gunakan badge status yang konsisten:

● Connected
● Ready
● Warning
● Error

Jangan menggunakan text status yang terlihat seperti debug output.

Jika loading:

gunakan skeleton loader.

Jika belum ada account:

gunakan empty state yang jelas.

Jika error:

gunakan alert yang mudah dipahami user.

==================================================
4. FACEBOOK PAGES UI
==================================================

Bagian destination Facebook harus terlihat seperti daftar Page profesional.

Contoh:

Facebook Pages

┌──────────────────────────────┐
│ Yourreels                    │
│ Facebook Page                │
│ ● Active                     │
│                              │
│ [View] [Refresh]             │
└──────────────────────────────┘

Jika banyak Page:

gunakan grid/list yang responsive.

Mobile:
1 column

Desktop:
2–3 columns sesuai lebar container.

Jangan membuat horizontal overflow.

==================================================
5. UPLOAD UI
==================================================

Perbaiki upload interface.

Target flow:

Upload Content

[ Drag & Drop / Select Video ]

Setelah video dipilih:

[ Video Preview ]

Filename
Size
Duration
Resolution

Caption
[ textarea ]

Facebook Page
[ Select Page ]

Publishing

(•) Publish now
( ) Schedule

[ Publish to Facebook ]

Button harus jelas dan mudah ditekan di mobile.

Jika belum memilih Page:

Publish button disabled.

Jika upload sedang berlangsung:

tampilkan progress/loading.

Jika publishing:

tampilkan state:

Uploading
Publishing
Published
Failed

Jangan menampilkan fake success.

==================================================
6. VIDEO PREVIEW
==================================================

Video preview harus:

- responsive
- tidak keluar container
- tidak menyebabkan horizontal overflow
- aspect ratio tetap baik
- nyaman di mobile
- tidak terlalu besar di desktop

Gunakan container yang rapi.

Jangan mengubah backend upload/media logic.

==================================================
7. PUBLISHING STATUS
==================================================

Buat status publishing mudah dibaca.

Gunakan:

Queued
Uploading
Publishing
Published
Failed
Retrying
Cancelled

Setiap status menggunakan visual badge/icon yang konsisten.

Jangan menggunakan warna berlebihan.

Error message harus user-friendly.

Contoh:

BAD:
"Graph API error code 190"

GOOD:
"Facebook connection expired. Please reconnect your account."

Technical error tetap boleh tersedia di detail/log jika memang diperlukan.

==================================================
8. MOBILE RESPONSIVE
==================================================

Prioritaskan breakpoint sekitar:

360px
390px
430px
768px
1024px
desktop

Test terutama:

360px
390px
768px
desktop

Pastikan:

- tidak ada horizontal overflow
- button tidak terpotong
- card tidak melebar keluar viewport
- text tidak bertabrakan
- badge tidak overflow
- form nyaman disentuh
- navigation tetap usable
- video preview responsive
- grid berubah menjadi 1 column di mobile

==================================================
9. DESKTOP UI
==================================================

Desktop jangan terlihat seperti mobile yang diperbesar.

Gunakan:

- max-width content container
- spacing yang proporsional
- grid
- card layout
- clear page hierarchy

Content jangan terlalu melebar.

==================================================
10. LOADING / EMPTY / ERROR STATE
==================================================

Semua halaman Facebook-related harus memiliki:

Loading state
Empty state
Error state
Success state

Jangan menampilkan halaman kosong saat data sedang dimuat.

Gunakan skeleton jika sesuai.

==================================================
11. ACCESSIBILITY
==================================================

Periksa:

- button memiliki label jelas
- form memiliki label
- focus state
- keyboard navigation
- contrast
- disabled state
- aria-label jika diperlukan

Jangan mengorbankan accessibility demi visual.

==================================================
12. COMPONENT QUALITY
==================================================

Gunakan component yang reusable.

Jangan membuat:

- duplicate button
- duplicate card
- duplicate badge
- duplicate alert
- duplicate loading component

Jika sudah ada component yang cocok, gunakan kembali.

Jangan membuat giant component.

==================================================
13. FACEBOOK LOGIC PROTECTION
==================================================

SANGAT PENTING:

Jangan mengubah:

- OAuth implementation
- callback
- token handling
- Facebook provider
- Graph API logic
- upload implementation
- publishing worker
- queue
- scheduler
- database schema

kecuali perubahan benar-benar diperlukan untuk memperbaiki bug UI.

Jika menemukan masalah backend saat audit:

JANGAN langsung memperbaikinya.

Catat saja:

BACKEND ISSUE FOUND:
...

Tetapi fokus tetap UI.

==================================================
14. TESTING
==================================================

Setelah perubahan:

1. pnpm/npm API typecheck sesuai project
2. web typecheck
3. lint
4. build
5. existing frontend tests
6. Facebook regression tests yang relevan

Jangan menghapus test.

Jangan menurunkan assertion.

Jangan membuat fake test.

==================================================
15. VISUAL REVIEW
==================================================

Setelah build berhasil, review hasil UI pada:

- mobile 360px
- mobile 390px
- mobile 430px
- desktop

Periksa secara khusus:

- spacing
- typography
- button
- card
- badge
- upload area
- video preview
- Page selector
- publishing status
- navigation
- overflow

==================================================
16. GIT
==================================================

Sebelum commit:

git status
git diff

Pastikan tidak ada:

- token
- password
- API key
- .env
- secret
- file debug

Commit hanya perubahan UI.

Contoh:

feat: polish facebook publishing ui

Push ke branch yang sedang digunakan.

Jangan force push.

==================================================
17. FINAL REPORT
==================================================

Laporkan:

UI CHANGES:
- ...

MOBILE:
PASS/FAIL

DESKTOP:
PASS/FAIL

FACEBOOK REGRESSION:
PASS/FAIL

TYPECHECK:
PASS/FAIL

LINT:
PASS/FAIL

BUILD:
PASS/FAIL

GIT STATUS:
CLEAN/DIRTY

COMMIT:
<hash>

PUSH:
SUCCESS/FAILED

IMPORTANT:
Jika semua PASS, jangan lanjut ke YouTube/Instagram/TikTok.

STOP setelah UI Facebook selesai.

NEXT PHASE:
Tunggu instruksi berikutnya.
````
# Prompt: Phase 6 — Facebook Upload & Publishing UI
```

# Prompt — Phase 6: Facebook Upload & Publishing UI

Kita lanjutkan project Content Pilot dari kondisi repository SAAT INI.

JANGAN mengulang Phase 0–5.
JANGAN mengubah arsitektur Facebook connection yang sudah PASS.
JANGAN menyentuh YouTube, Instagram, TikTok, X, Pinterest, atau LinkedIn.

STATUS SAAT INI:

- Facebook OAuth/connection: PASS
- Facebook account connection: PASS
- Facebook Page discovery: PASS
- Destination persistence: PASS
- Reconnect: PASS
- Disconnect: PASS
- Connection persistence: PASS
- Facebook provider regression: PASS
- API typecheck: PASS
- Web typecheck: PASS
- Lint: PASS
- Production build: PASS
- Mobile UI regression: PASS
- Facebook Pages/destination UI: sudah diperbaiki
- Provider readiness: Facebook OAuth ready
- Destination: aktif
- Phase 5: selesai dan sudah di-commit/push

LIVE FACEBOOK PUBLISHING sebelumnya masih BLOCKED karena credential/permission publishing nyata belum tersedia.

Sekarang tugas kita adalah menyiapkan dan mengimplementasikan Facebook upload/publishing secara nyata menggunakan API resmi Meta/Facebook.

==================================================
1. ATURAN PALING PENTING
==================================================

Sebelum coding:

1. Inspect repository saat ini.
2. Baca implementation Facebook yang SUDAH ADA.
3. Jangan membuat ulang Facebook OAuth.
4. Jangan membuat ulang connection layer.
5. Jangan membuat fake upload.
6. Jangan membuat fake publish success.
7. Jangan menggunakan browser automation.
8. Jangan menggunakan username/password Facebook.
9. Gunakan Facebook/Meta Graph API resmi.
10. Jangan mengarang endpoint, permission, parameter, atau response.
11. Jika API capability belum pasti, cek dokumentasi resmi Meta terlebih dahulu.
12. Jangan mengubah provider lain.
13. Jangan melakukan massive refactor.
14. Jangan menghapus test yang sudah PASS.
15. Jangan merusak connection layer yang sudah stabil.

Jika credential/permission publishing belum tersedia, tetap implementasikan seluruh production-ready flow sampai boundary API dan berikan status yang jelas:

READY_FOR_LIVE_CREDENTIAL

bukan:

PUBLISHED

Jangan membuat mock response terlihat seperti publish berhasil.

==================================================
2. TUJUAN PHASE INI
==================================================

Bangun alur:

Upload video
→ validate video
→ preview
→ pilih Facebook Page
→ caption
→ publish
→ upload/publish process
→ status
→ result
→ history

Target UI:

Facebook Upload

[ Select Video / Drag & Drop ]

Video Preview

Filename
Size
Duration
Resolution

Caption
[.................................]

Facebook Page
[ Your Page ▼ ]

Publishing

( ) Publish Now
( ) Schedule

[ Publish to Facebook ]

Setelah submit:

Uploading...
Publishing...
Published
atau
Failed

==================================================
3. MEDIA UPLOAD
==================================================

Implement media upload secara modular.

Media harus tetap platform-independent.

Jangan membuat model seperti:

FacebookVideo

Gunakan media generic yang sudah ada/ditentukan architecture project.

Minimal validasi:

- MIME type
- file extension
- file size
- video readability
- duration jika diperlukan
- dimensions jika diperlukan

Jangan mengasumsikan batas ukuran/durasi.

Gunakan requirement resmi Meta untuk endpoint yang benar-benar digunakan.

Error harus jelas.

Contoh:

Unsupported format
File too large
Invalid video
Upload failed
Facebook rejected media

Jangan menampilkan error internal mentah kepada user jika tidak aman.

==================================================
4. FACEBOOK PAGE SELECTION
==================================================

Gunakan destination Facebook Page yang SUDAH tersimpan.

Jangan membuat Page connection baru.

UI harus menampilkan:

Facebook
Page name
Page status
Connected/Active

Jika hanya ada satu Page:

gunakan Page tersebut sebagai default.

Jika banyak Page:

gunakan dropdown/select.

Jika tidak ada Page:

tampilkan empty state:

"No Facebook Pages available"

dan tombol:

"Reconnect Facebook"

Jangan hardcode Page ID.

==================================================
5. CAPTION
==================================================

Buat caption editor yang bagus.

Minimal:

- textarea
- character counter jika memang relevan
- preserve line breaks
- trim input
- validation
- disabled state saat publishing

Jangan membuat caption editor terlalu besar.

Mobile harus nyaman digunakan.

==================================================
6. PUBLISH FLOW
==================================================

Gunakan PublishingJob yang SUDAH dirancang.

Jangan membuat sistem job baru khusus Facebook.

Flow:

User
→ create PublishingJob
→ queue
→ Facebook provider
→ upload/publish
→ update job status
→ save result
→ history

Gunakan status yang sudah ada.

Contoh:

draft
queued
processing
uploading
publishing
published
failed
retrying

Jangan mengubah status secara tidak valid.

==================================================
7. FACEBOOK PROVIDER
==================================================

Implement publishing di:

provider-facebook

atau struktur provider Facebook yang SUDAH ADA.

Jangan menaruh logic Facebook di:

- core
- generic publishing service
- generic queue
- generic media service

Core hanya memanggil provider.

Konsep:

PublishingJob
→ provider registry
→ FacebookProvider
→ Facebook API

==================================================
8. API IMPLEMENTATION
==================================================

Gunakan endpoint resmi Meta yang sesuai dengan jenis content yang kita pilih.

Sebelum implementation:

Research dokumentasi resmi Meta untuk:

- Page video publishing
- video upload flow
- Reels publishing jika memang menjadi target pertama
- required permissions
- Page access token
- resumable upload jika diperlukan
- publishing status
- error response

Pilih SATU jenis Facebook video publishing yang paling tepat untuk Phase ini berdasarkan API resmi dan kondisi credential yang sudah tersedia.

Jangan implementasikan banyak jenis publishing sekaligus.

Prioritas:

FACEBOOK VIDEO UPLOAD/PUBLISH TERLEBIH DAHULU.

Setelah stabil baru Reels.

==================================================
9. TOKEN SECURITY
==================================================

Gunakan connection/token system yang SUDAH ADA.

Jangan:

- hardcode token
- menyimpan token di frontend
- menampilkan token ke browser
- log access token
- commit token
- menyimpan token plaintext jika architecture existing sudah menggunakan secure storage

Backend/provider yang menangani credential.

Frontend hanya menerima status/error/result yang diperlukan.

==================================================
10. UPLOAD UI — REDESIGN
==================================================

Selain backend, perbaiki UI Upload agar terlihat jauh lebih modern dibanding UI Accounts sebelumnya.

Target:

Clean
Modern
Professional
Dark theme konsisten
Responsive
Mobile-first
Tidak terlalu banyak whitespace
Tidak terlalu banyak border
Tidak terlalu banyak tombol

Gunakan design system existing.

Jangan membuat design system kedua.

==================================================
11. UPLOAD PAGE
==================================================

Buat layout seperti:

------------------------------------------------
Facebook Upload
Upload content to your Facebook Page

[ Upload area ]

Drag & drop video here
or
[ Choose Video ]

Supported formats...
------------------------------------------------

Setelah video dipilih:

------------------------------------------------
Video Preview

[ VIDEO ]

filename.mp4
1080 × 1920
25 MB
00:32

[ Replace ]
------------------------------------------------

Caption

[ Write your caption... ]

0 / ...

------------------------------------------------

Publish to

Facebook

Page
[ Yourreels ▼ ]

------------------------------------------------

Publishing

[ Publish Now ]

atau schedule jika scheduler existing memang sudah siap.

[ Publish to Facebook ]
------------------------------------------------

UI harus berubah berdasarkan state.

==================================================
12. UPLOAD STATES
==================================================

Implement state yang jelas:

EMPTY

No video selected.

SELECTED

Video sudah dipilih.

VALIDATING

Validasi media.

READY

Media valid dan siap dipublish.

UPLOADING

Upload ke backend/provider.

PUBLISHING

Facebook sedang memproses publishing.

SUCCESS

Facebook publish berhasil.

FAILED

Publishing gagal.

RETRY

Jika error temporary dan retry memang diperbolehkan.

Jangan membuat SUCCESS sebelum provider benar-benar mengembalikan hasil sukses.

==================================================
13. SUCCESS UI
==================================================

Jika benar-benar sukses:

tampilkan:

Published successfully

Facebook
Page Name

Content ID / Post ID jika tersedia dan aman ditampilkan.

Timestamp.

Action:

[ View History ]

Jika API memberikan URL publik yang valid:

[ Open on Facebook ]

Jangan membuat URL Facebook secara manual jika response API tidak menyediakan informasi yang diperlukan.

==================================================
14. ERROR UI
==================================================

Error harus user-friendly.

Contoh:

Permission required

Facebook account needs publishing permission.

atau:

Facebook rejected this video

The selected media does not meet Facebook's requirements.

atau:

Temporary Facebook error

Please try again.

Simpan detail teknis di server log/job attempt, bukan ditampilkan semuanya ke user.

==================================================
15. RETRY
==================================================

Gunakan retry architecture yang SUDAH ADA.

Temporary error:

retry boleh.

Permanent error:

jangan automatic retry.

Contoh permanent:

- permission denied
- invalid destination
- invalid token
- unsupported media

Contoh temporary:

- timeout
- network error
- rate limit
- temporary provider error

Jangan membuat infinite retry.

==================================================
16. HISTORY
==================================================

Setelah publishing:

History harus dapat menampilkan:

Platform
Facebook

Destination
Page name

Content
thumbnail/video

Status

Published at

Error jika failed

Job ID jika diperlukan.

Jangan membuat history Facebook terpisah dari generic publishing history jika architecture existing sudah generic.

==================================================
17. TESTING
==================================================

Tambahkan test sesuai architecture existing.

Minimal:

API:

- upload validation
- create publishing job
- Facebook provider validation
- destination validation
- permission error
- provider error mapping
- successful response mapping
- temporary error
- permanent error

Worker:

- queued → processing
- processing → uploading
- uploading → publishing
- publishing → published
- failure handling
- retry handling

Frontend:

- empty state
- select video
- invalid video
- ready state
- publish disabled state
- loading state
- success state
- failure state
- mobile layout

Jangan menghapus test lama.

==================================================
18. LIVE TEST
==================================================

Setelah implementation:

JANGAN membuat fake Facebook account.

JANGAN membuat fake Page.

JANGAN membuat fake access token.

JANGAN membuat fake publish response.

Jika credential nyata dan permission publishing tersedia:

lakukan satu live test dengan content uji.

Jika credential/permission belum tersedia:

jalankan semua test sampai boundary API dan laporkan:

LIVE FACEBOOK PUBLISH TEST: BLOCKED

Reason:
<actual reason>

Jangan menyatakan PASS.

==================================================
19. UI REGRESSION
==================================================

Pastikan perubahan Upload tidak merusak:

/accounts
/platforms
Facebook connection
Facebook Pages
Reconnect
Disconnect
History
existing navigation

Test breakpoint minimal:

- mobile ~360px
- mobile ~390px
- tablet
- desktop

Pastikan:

- tidak ada horizontal overflow
- button tidak keluar layar
- text tidak terpotong
- modal/dialog responsive
- upload area responsive
- video preview responsive

==================================================
20. GIT SAFETY
==================================================

Sebelum commit:

git status

Periksa:

git diff

Pastikan tidak ada:

- access token
- refresh token
- password
- API key
- .env
- credential
- secret

Jangan commit perubahan yang tidak berhubungan dengan Phase ini.

==================================================
21. VERIFICATION
==================================================

Setelah implementation:

1. API typecheck
2. Web typecheck
3. lint
4. unit tests
5. provider tests
6. worker tests
7. web tests
8. production build
9. mobile UI regression
10. Facebook provider regression

Jika ada failure:

perbaiki akar masalah.

Jangan hanya bypass test.

Jangan menurunkan assertion.

==================================================
22. DOCUMENTATION
==================================================

Update documentation yang relevan.

Minimal:

README.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md
docs/research/facebook-api.md

Tambahkan status aktual:

Facebook connection: COMPLETE

Facebook destination discovery: COMPLETE

Facebook upload: <status>

Facebook publishing: <status>

Live publishing: <status>

Jangan menulis COMPLETE jika belum benar-benar selesai.

==================================================
23. COMMIT
==================================================

Jika semua verification yang bisa dilakukan PASS:

buat commit dengan message:

feat: add facebook video publishing flow

Jika live test masih blocked karena credential/permission eksternal tetapi implementation dan automated test sudah benar, tetap boleh commit implementation dengan status yang jelas.

Jangan mengklaim live publishing PASS jika belum dilakukan.

Push ke branch aktif.

Jangan force push.

Setelah push, verifikasi remote.

==================================================
24. FINAL REPORT
==================================================

Di akhir tampilkan:

PHASE: 6

FACEBOOK CONNECTION: PASS

FACEBOOK DESTINATION: PASS

MEDIA UPLOAD: PASS / BLOCKED

FACEBOOK PROVIDER: PASS / BLOCKED

PUBLISHING FLOW: PASS / BLOCKED

LIVE FACEBOOK PUBLISH TEST: PASS / BLOCKED

UI UPLOAD: PASS

MOBILE UI: PASS

API TYPECHECK: PASS/FAIL

WEB TYPECHECK: PASS/FAIL

LINT: PASS/FAIL

TESTS: PASS/FAIL

BUILD: PASS/FAIL

REGRESSION: PASS/FAIL

GIT STATUS: CLEAN/DIRTY

COMMIT: <hash>

BRANCH: <branch>

PUSH STATUS: SUCCESS/FAILED

REMOTE VERIFIED: YES/NO

Jika LIVE FACEBOOK PUBLISH TEST BLOCKED:

jelaskan alasan sebenarnya.

Jangan membuat fake success.

==================================================
STOP CONDITION
==================================================

Setelah Phase 6 selesai:

STOP.

Jangan mulai:

- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn
- bulk publishing
- advanced automation

Tunggu instruksi berikutnya.

Fokus sampai Facebook video upload/publishing benar-benar stabil.
````
# Prompt — Facebook UI Final Verification
```
Lanjutkan dari pekerjaan terakhir.

Fokus HANYA pada final verification Facebook UI. Jangan menambah fitur baru dan jangan menyentuh YouTube/Instagram/TikTok.

1. Jalankan:
   - pnpm --filter web typecheck
   - pnpm --filter web lint
   - production build web

2. Review apps/web/src/app/globals.css dan seluruh CSS/component yang baru disentuh.
   Pastikan:
   - tidak ada CSS duplicate
   - tidak ada class yang tidak terpakai
   - tidak ada style yang merusak halaman lain
   - responsive mobile/desktop tetap baik
   - tidak ada horizontal overflow
   - status badge, spinner, skeleton, cards, buttons, alert, destination grid konsisten

3. Audit halaman:
   - Accounts
   - Facebook connection
   - Facebook Pages/destinations
   - Platforms

4. Jika menemukan masalah UI kecil, perbaiki langsung.
   Jangan melakukan refactor besar.

5. Setelah itu jalankan regression test yang relevan untuk Facebook connection.
   Jangan mengubah backend yang sudah PASS.

6. Periksa git diff dan pastikan tidak ada:
   - secret
   - token
   - .env
   - perubahan platform lain

7. Jika semuanya PASS:
   - commit perubahan UI Facebook
   - push ke branch aktif
   - verifikasi remote

Commit message:
feat: polish facebook connection ui

8. Berikan laporan:

UI TYPECHECK: PASS/FAIL
LINT: PASS/FAIL
BUILD: PASS/FAIL
FACEBOOK REGRESSION: PASS/FAIL
MOBILE UI: PASS/FAIL
DESKTOP UI: PASS/FAIL
GLOBAL CSS: PASS/FAIL
GIT STATUS: CLEAN/DIRTY
COMMIT: <hash>
PUSH: SUCCESS/FAILED

STOP setelah laporan.
Jangan lanjut ke provider/platform lain.

````
# Prompt — Facebook Final UI Polish
```

# Prompt — Facebook Finalization: UI/UX Polish & Verification

Kita BELUM melanjutkan ke YouTube.

Fokus sekarang hanya menyelesaikan dan mempercantik bagian FACEBOOK sampai benar-benar siap digunakan.

==================================================
STATUS PROJECT SAAT INI
==================================================

Facebook provider sudah melalui beberapa phase dan hasil terakhir:

- Facebook OAuth: PASS
- OAuth callback: PASS
- Session persistence: PASS
- Connection persistence: PASS
- Destination persistence: PASS
- Multi-user isolation: PASS
- Reconnect: PASS
- Disconnect: PASS
- Facebook provider tests: PASS
- Typecheck: PASS
- Web build: PASS
- Regression Phase 4: PASS
- Queue/scheduler/idempotency: PASS
- Git clean
- Commit dan push terakhir berhasil

Facebook connection sudah berhasil digunakan dan destination/Page sudah ditemukan.

Jangan mengulang implementasi backend yang sudah PASS.

==================================================
TUJUAN SEKARANG
==================================================

Selesaikan Facebook sebagai provider pertama dengan fokus:

1. UI/UX
2. Connection management
3. Destination management
4. Publishing UI
5. Loading/error/empty states
6. Mobile responsiveness
7. Desktop responsiveness
8. Visual consistency
9. Final regression
10. Documentation

JANGAN mulai:

- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn

==================================================
1. AUDIT UI EXISTING
==================================================

Sebelum mengubah UI:

Audit seluruh UI Facebook yang sekarang.

Periksa:

- Accounts
- Platforms
- Facebook connection card
- OAuth flow
- Destination list
- Reconnect
- Disconnect
- Connect another
- Refresh
- Publishing UI
- Upload UI
- History
- Queue
- Scheduled posts
- Error states
- Loading states
- Empty states

Jangan membuat halaman duplicate.

Jangan membuat design system kedua.

Gunakan component/design system existing jika sudah tersedia.

==================================================
2. FACEBOOK ACCOUNTS UI
==================================================

Perbaiki halaman Accounts agar terlihat modern dan profesional.

Target:

Facebook
Connected

Account:
Nino Kuye

Status:
Connected

Destinations:
1 Page

Actions:

[View destinations]
[Refresh]
[Reconnect]
[Connect another]
[Disconnect]

Gunakan hierarchy visual yang jelas.

Status connected harus mudah terlihat.

Jangan membuat card terlalu tinggi.

Hindari whitespace yang berlebihan.

Desktop dan mobile harus sama-sama nyaman.

==================================================
3. DESTINATION UI
==================================================

Buat daftar Page Facebook lebih informatif.

Contoh:

Facebook Pages

┌──────────────────────────────┐
│ Yourreels                    │
│ Facebook Page                │
│ ● Connected                  │
│                              │
│ [Select]                     │
└──────────────────────────────┘

Jika terdapat banyak Page:

- gunakan list/grid yang rapi
- tampilkan nama
- tipe destination
- status
- external identifier jika memang diperlukan
- selected state

Jangan tampilkan token.

Jangan tampilkan credential.

==================================================
4. CONNECTION STATUS
==================================================

Gunakan status yang jelas:

Connected
Connecting
Needs Reconnect
Disconnected
Error

Gunakan visual yang konsisten dengan design system.

Jangan hanya mengandalkan warna.

Status harus tetap dapat dipahami tanpa warna.

==================================================
5. CONNECT FACEBOOK FLOW
==================================================

Perbaiki flow:

Connect Facebook
↓
Starting connection
↓
Redirect ke Facebook
↓
OAuth callback
↓
Discover destinations
↓
Connected

Tampilkan loading state yang jelas.

Jika gagal:

Connection failed

[Try again]

Jangan menampilkan:

"Connection successful"

jika callback sebenarnya gagal.

==================================================
6. ERROR MESSAGE
==================================================

Error harus:

- singkat
- mudah dipahami
- tidak menampilkan stack trace
- tidak menampilkan token
- tidak menampilkan internal URL
- tidak menampilkan credential

Contoh:

"Unable to connect Facebook. Please try again."

Jika backend memberikan error yang aman dan actionable:

"Facebook authorization expired. Please reconnect."

==================================================
7. SUCCESS MESSAGE
==================================================

Success notification harus lebih natural.

Contoh:

"Facebook connected successfully."

"Your Facebook Pages are ready."

"Facebook connection refreshed."

Hindari pesan teknis seperti:

"Destinations were discovered and saved."

Jika detail teknis memang penting, tampilkan sebagai secondary information.

==================================================
8. PUBLISHING UI
==================================================

Sekarang audit UI publishing Facebook.

Target flow:

Upload
↓
Preview
↓
Caption
↓
Select Facebook
↓
Select Page
↓
Publish now / Schedule
↓
Review
↓
Publish

UI harus jelas bahwa:

Facebook Page = destination.

Contoh:

Platform

Facebook ✓

Destination

Yourreels
Facebook Page

Schedule

[Publish now]
[Schedule]

[Publish]

==================================================
9. FACEBOOK CONTENT TYPES
==================================================

Tampilkan hanya capability Facebook yang BENAR-BENAR sudah tersedia.

Contoh:

Reels
Video
Photo
Text Post

Jangan menampilkan fitur sebagai available jika backend belum selesai.

Jika capability belum tersedia:

Coming soon

atau jangan tampilkan.

Jangan membuat fake UI.

==================================================
10. LIVE PUBLISHING
==================================================

PENTING:

Jika live publishing Facebook masih membutuhkan:

- App Review
- permission
- production credential
- verified app
- additional Meta approval

maka jangan memalsukan keberhasilan.

UI harus membedakan:

READY
vs
BLOCKED

Contoh:

Publishing
Ready for testing

atau:

Live publishing requires Meta approval.

Jangan pernah membuat mock publish terlihat sebagai publish nyata.

==================================================
11. PUBLISH REVIEW
==================================================

Sebelum publish, tampilkan review card:

Content
[thumbnail]

Platform
Facebook

Destination
Yourreels

Caption
...

Publish
Now / Scheduled

[Cancel]
[Publish]

Tujuannya agar user tidak salah memilih Page.

==================================================
12. QUEUE UI
==================================================

Jika Facebook publishing sudah menggunakan queue:

Tampilkan status:

Queued
Processing
Uploading
Publishing
Published
Failed
Retrying
Cancelled

Gunakan progress/status yang mudah dipahami.

Jangan menampilkan detail internal queue kecuali pada halaman detail.

==================================================
13. HISTORY UI
==================================================

Facebook history harus terlihat profesional.

Contoh:

Yourreels
Facebook

Reels
Published

23 Aug 2026
14:20

Thumbnail | Caption | Status

Filter:

All
Published
Failed
Scheduled

Jika gagal:

[View error]

Jangan menampilkan raw API response sebagai UI utama.

==================================================
14. MOBILE UI
==================================================

WAJIB test pada mobile width.

Perhatikan screenshot sebelumnya:

UI saat ini terlalu panjang pada beberapa bagian.

Perbaiki:

- spacing
- card height
- button layout
- typography
- navigation
- form width
- alert width
- destination cards
- bottom navigation jika ada

Button harus mudah ditekan.

Jangan membuat horizontal overflow.

==================================================
15. DESKTOP UI
==================================================

Desktop harus menggunakan ruang secara efisien.

Jangan membuat content terlalu lebar.

Gunakan:

- max-width
- responsive grid
- consistent cards
- proper spacing

Accounts dan Platforms tidak boleh terlihat seperti halaman mentah/debug.

==================================================
16. DESIGN SYSTEM
==================================================

Gunakan design system existing jika sudah ada.

Rapikan konsistensi:

- heading
- body text
- muted text
- button
- card
- border
- radius
- alert
- badge
- status
- input
- select
- modal

Jangan mengubah seluruh warna project tanpa alasan.

Prioritaskan clean, modern, professional.

==================================================
17. LOADING STATE
==================================================

Semua async action harus memiliki loading state:

Connect
Reconnect
Refresh
Disconnect
Load destinations
Publish
Schedule

Button harus disabled ketika request sedang berjalan untuk mencegah duplicate request.

==================================================
18. EMPTY STATE
==================================================

Jika Facebook belum memiliki destination:

Facebook Pages

No Facebook Pages found.

[Reconnect Facebook]

Jika belum connect:

Facebook isn't connected.

[Connect Facebook]

Jangan tampilkan blank page.

==================================================
19. CONFIRMATION
==================================================

Untuk action berbahaya:

Disconnect Facebook

tampilkan confirmation.

Contoh:

Disconnect Facebook?

This will remove the current Facebook connection and its destinations from this account.

[Cancel]
[Disconnect]

Jangan langsung disconnect karena salah klik.

==================================================
20. ACCESSIBILITY
==================================================

Audit:

- button labels
- keyboard navigation
- focus state
- form labels
- aria attributes jika diperlukan
- contrast
- readable font sizes
- touch target

Jangan mengorbankan accessibility demi tampilan.

==================================================
21. SECURITY UI
==================================================

Pastikan UI tidak pernah menampilkan:

- access token
- refresh token
- OAuth code
- client secret
- Authorization header
- internal credential

Jika ada debug output di frontend, hapus.

==================================================
22. BACKEND REGRESSION
==================================================

Jangan mengubah backend Facebook yang sudah PASS kecuali benar-benar diperlukan untuk memperbaiki UI integration.

Setelah perubahan:

- API typecheck
- Web typecheck
- lint
- tests
- production build

WAJIB regression:

Facebook OAuth
Facebook callback
Session
Connection
Destination
Reconnect
Disconnect
Multi-user isolation

==================================================
23. TESTING
==================================================

Tambahkan/perbaiki UI tests untuk:

- connected state
- disconnected state
- loading state
- error state
- empty state
- destination selection
- reconnect
- disconnect confirmation
- publish review
- mobile layout jika test framework mendukung

Jangan membuat test palsu.

==================================================
24. VISUAL REVIEW
==================================================

Setelah implementation:

Jalankan production build.

Buka UI sebenarnya.

Periksa secara manual:

Accounts
Platforms
Facebook connection
Destinations
Publishing
History

Periksa mobile dan desktop.

Perbaiki visual issue yang ditemukan.

Jangan berhenti hanya karena typecheck PASS.

==================================================
25. DOCUMENTATION
==================================================

Update dokumentasi existing.

Jangan membuat README baru.

Dokumentasikan:

- Facebook provider status
- connection flow
- destination model
- current capabilities
- known limitations
- live publishing status
- UI flow

Jika live publishing masih blocked karena Meta approval:

tulis jelas sebagai limitation.

==================================================
26. GIT
==================================================

Sebelum commit:

git status
git diff

Pastikan:

- tidak ada secret
- tidak ada token
- tidak ada .env
- tidak ada debug credential
- tidak ada perubahan YouTube/Instagram/TikTok

Commit:

feat: finalize facebook ui and ux

Push ke branch aktif.

Jangan force push.

Verifikasi remote.

==================================================
27. FINAL REPORT
==================================================

Tampilkan:

FACEBOOK FINALIZATION

OAuth:
PASS/FAIL

Connection:
PASS/FAIL

Destination:
PASS/FAIL

Reconnect:
PASS/FAIL

Disconnect:
PASS/FAIL

Multi-user isolation:
PASS/FAIL

Publishing UI:
PASS/FAIL

History UI:
PASS/FAIL

Queue UI:
PASS/FAIL

Mobile UI:
PASS/FAIL

Desktop UI:
PASS/FAIL

Loading states:
PASS/FAIL

Error states:
PASS/FAIL

Empty states:
PASS/FAIL

Accessibility:
PASS/FAIL

Security:
PASS/FAIL

API Typecheck:
PASS/FAIL

Web Typecheck:
PASS/FAIL

Tests:
PASS/FAIL

Production Build:
PASS/FAIL

LIVE FACEBOOK PUBLISH:
PASS / BLOCKED

Jika LIVE FACEBOOK PUBLISH masih membutuhkan Meta App Review/permission/credential:
tulis BLOCKED dan alasan sebenarnya.

GIT STATUS:
CLEAN/DIRTY

COMMIT:
<hash>

PUSH:
SUCCESS/FAILED

REMOTE VERIFIED:
YES/NO

FILES CHANGED:
<list>

==================================================
STOP CONDITION
==================================================

Facebook harus menjadi fokus terakhir sebelum platform berikutnya.

Setelah UI Facebook selesai dan semua regression PASS:

STOP.

Jangan mulai:

- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn

Tunggu instruksi berikutnya.

Jangan menyatakan Facebook "fully complete" jika live publishing masih BLOCKED.

Status yang benar jika backend + UI siap tetapi Meta approval belum ada:

FACEBOOK PROVIDER: COMPLETE
FACEBOOK UI/UX: COMPLETE
LIVE PUBLISHING: BLOCKED — EXTERNAL META REQUIREMENT
````
# Prompt 5 — Queue, Scheduler & Publishing Reliability
```
# Prompt 5 — Phase 5: Publishing Queue, Scheduler & Reliability Hardening

Kita lanjutkan project Content Pilot setelah Phase 4 selesai.

STATUS TERAKHIR:
- Facebook connection: PASS
- OAuth callback: PASS
- Session persistence: PASS
- Connection persistence: PASS
- Destination persistence: PASS
- Multi-user isolation: PASS
- Reconnect: PASS
- Disconnect: PASS
- Security checks: PASS
- Typecheck: PASS
- Tests: PASS
- Production build: PASS
- Facebook destination sudah tersimpan dan aktif
- Phase 4 sudah committed dan pushed
- Git terakhir clean
- LIVE Facebook publishing masih BLOCKED karena membutuhkan credential/App Review/permission live yang valid

PENTING:
LIVE FACEBOOK PUBLISHING YANG BLOCKED BUKAN BUG YANG HARUS DIPAKSA MENJADI PASS.

Jangan membuat fake credential.
Jangan mock live publish sebagai PASS.
Jangan bypass Facebook permission.
Jangan menyentuh credential Meta.
Jangan mengubah hasil live test menjadi PASS palsu.

Sekarang fokus ke PHASE 5.

==================================================
TUJUAN PHASE 5
==================================================

Hardening publishing infrastructure agar siap menangani:

- publish now
- scheduled publishing
- queue
- retry
- cancellation
- idempotency
- concurrent jobs
- failed jobs
- provider errors
- rate limiting
- job status
- publishing history

Architecture HARUS tetap platform-independent.

Facebook hanya salah satu provider.

Jangan membuat queue yang hardcoded untuk Facebook.

==================================================
ATURAN UTAMA
==================================================

Sebelum coding:

1. Audit implementasi queue/scheduler yang SUDAH ADA.
2. Audit database model yang SUDAH ADA.
3. Audit publishing job yang SUDAH ADA.
4. Audit provider interface yang SUDAH ADA.
5. Audit Facebook provider yang SUDAH ADA.
6. Jangan membuat duplicate system.
7. Jangan mengganti architecture yang sudah benar.
8. Jangan melakukan massive refactor tanpa alasan.
9. Jangan mengubah provider lain.
10. Jangan menyentuh YouTube/Instagram/TikTok/X/Pinterest/LinkedIn.
11. Jangan mengaktifkan LIVE Facebook test.
12. Jangan membuat fake publishing.
13. Jangan menggunakan browser automation untuk Facebook.
14. Gunakan implementation yang sudah ada sebagai baseline.

==================================================
1. PUBLISHING JOB MODEL
==================================================

Pastikan publishing job memiliki konsep yang jelas.

Minimal:

- id
- post/content reference
- platform/provider
- destination
- status
- scheduledAt
- startedAt
- completedAt
- attemptCount
- lastError
- nextRetryAt
- providerJobId/reference jika tersedia
- createdAt
- updatedAt

Sesuaikan dengan schema existing.

Jangan membuat field duplicate jika sudah tersedia.

==================================================
2. STATUS MACHINE
==================================================

Audit dan rapikan state machine.

Gunakan status yang sesuai dengan implementasi existing, misalnya:

draft
queued
scheduled
processing
uploading
publishing
published
failed
retrying
cancelled

Jangan membuat transisi status yang tidak valid.

Contoh:

scheduled
→ queued
→ processing
→ uploading
→ publishing
→ published

Jika error sementara:

publishing
→ retrying
→ queued/processing

Jika error permanent:

publishing
→ failed

Jika user membatalkan sebelum processing:

scheduled/queued
→ cancelled

Jangan izinkan:

published → queued

atau transisi tidak masuk akal lainnya.

==================================================
3. IDEMPOTENCY
==================================================

Pastikan satu publishing job tidak dapat diproses dua kali secara tidak sengaja.

Contoh:

Worker A mengambil Job 001
Worker B mencoba mengambil Job 001

Hanya satu worker yang boleh mendapatkan lock/ownership.

Gunakan mekanisme yang sesuai dengan stack existing:

- database lock
- atomic update
- queue job lock
- Redis lock
- provider idempotency jika tersedia

Jangan menambahkan Redis hanya jika repository belum membutuhkannya.

Pilih solusi berdasarkan architecture existing.

==================================================
4. CONCURRENCY
==================================================

Audit concurrency.

Pastikan worker tidak menjalankan job yang sama dua kali.

Pertimbangkan:

- per-user concurrency
- per-provider concurrency
- per-destination concurrency
- global worker concurrency

Jangan over-engineer.

Implement minimum yang aman berdasarkan repository sekarang.

==================================================
5. RETRY SYSTEM
==================================================

Implement/rapikan retry policy.

Temporary errors:

- timeout
- network error
- temporary provider error
- HTTP 429
- transient 5xx

→ retry.

Permanent errors:

- invalid token
- permission denied
- invalid destination
- unsupported media
- invalid request

→ failed tanpa infinite retry.

Gunakan exponential backoff jika sesuai.

Contoh:

attempt 1 → 30 sec
attempt 2 → 1 min
attempt 3 → 5 min

Tetapi sesuaikan dengan existing architecture.

Jangan hardcode retry jika konfigurasi sudah tersedia.

Simpan:

- attempt count
- error code
- error message
- timestamp
- next retry

Jangan menyimpan access token atau secret ke error log.

==================================================
6. RATE LIMITING
==================================================

Audit apakah provider-specific rate limit handling sudah ada.

Jika belum, buat abstraction yang dapat digunakan provider.

Contoh konsep:

Provider
→ rate limit policy
→ queue delay
→ retry

Jangan membuat Facebook-specific code di core queue.

Core hanya mengetahui:

provider key
destination
job

Provider dapat menentukan policy-nya.

==================================================
7. SCHEDULER
==================================================

Audit scheduler existing.

Pastikan scheduled job:

1. tersimpan di database
2. memiliki waktu eksekusi
3. tidak diproses sebelum waktunya
4. masuk queue saat waktunya tiba
5. tidak dibuat duplicate
6. tetap aman setelah worker restart

Scheduler harus idempotent.

Contoh:

Schedule 20:00

Scheduler restart pada 20:01.

Job tetap dapat ditemukan dan diproses.

Jangan membuat duplicate job.

==================================================
8. PUBLISH NOW
==================================================

Pastikan flow:

User memilih Publish Now
→ create publishing job
→ queued
→ worker mengambil job
→ provider publish
→ status diperbarui
→ history tersimpan

Jangan membuat frontend langsung memanggil provider untuk publishing jika architecture project menggunakan backend worker.

==================================================
9. SCHEDULED PUBLISH
==================================================

Flow:

User memilih Schedule
→ validasi tanggal/waktu
→ create scheduled job
→ status scheduled
→ scheduler menunggu
→ queue
→ worker
→ provider
→ published/failed

Validasi:

- waktu tidak boleh invalid
- timezone harus jelas
- jangan menjalankan schedule dua kali
- cancellation harus bekerja sebelum job diproses

==================================================
10. CANCELLATION
==================================================

Implement cancellation dengan aman.

Jika:

scheduled
atau
queued

→ boleh cancelled.

Jika:

processing
uploading
publishing

→ hanya boleh cancelled jika provider/worker benar-benar mendukung cancellation.

Jangan menampilkan cancellation sukses jika job sebenarnya masih berjalan.

==================================================
11. ERROR NORMALIZATION
==================================================

Provider error harus dinormalisasi.

Core tidak boleh bergantung pada format error Facebook.

Contoh generic:

ProviderError:

- code
- category
- retryable
- message
- provider
- providerRequestId jika aman
- metadata aman

Category:

AUTH
PERMISSION
RATE_LIMIT
NETWORK
VALIDATION
MEDIA
DESTINATION
PROVIDER
UNKNOWN

Facebook provider menerjemahkan error Facebook ke format generic.

==================================================
12. HISTORY
==================================================

Pastikan setiap publishing job memiliki history/attempt information.

Contoh:

Job 001

Attempt 1
→ failed
→ timeout

Attempt 2
→ failed
→ rate limit

Attempt 3
→ published

Dashboard dapat menunjukkan:

Status: Published
Attempts: 3

Jangan menghapus attempt lama ketika retry.

==================================================
13. LOGGING
==================================================

Audit logging.

Log harus membantu debugging:

- job ID
- provider
- destination ID
- status transition
- attempt
- error category
- duration

Jangan log:

- access token
- refresh token
- password
- API secret
- cookies
- authorization header

==================================================
14. UI
==================================================

Jangan membuat dashboard baru.

Gunakan UI existing.

Tambahkan hanya jika memang diperlukan:

Queue
Scheduled
Publishing status
Retry information
Cancel action
Error state

UI harus menunjukkan status sebenarnya.

Contoh:

QUEUED
PROCESSING
PUBLISHED
FAILED
RETRYING
CANCELLED

Jangan menggunakan:

"Success"

jika backend sebenarnya belum berhasil.

==================================================
15. API
==================================================

Audit API endpoint existing.

Jika perlu endpoint baru, gunakan struktur yang konsisten dengan project.

Contoh konsep:

POST /api/posts
POST /api/posts/:id/publish
POST /api/posts/:id/schedule
POST /api/publishing-jobs/:id/cancel
GET /api/publishing-jobs
GET /api/publishing-jobs/:id
GET /api/publishing-jobs/:id/attempts

JANGAN otomatis membuat endpoint tersebut jika endpoint equivalent sudah ada.

Ikuti architecture existing.

==================================================
16. DATABASE
==================================================

Jika schema perlu berubah:

- buat migration
- jangan menghapus data existing
- jangan reset database
- jangan menggunakan destructive migration
- pastikan migration dapat dijalankan ulang dengan aman

Sebelum migration:

audit schema existing.

==================================================
17. TESTING
==================================================

Buat/rapikan test untuk:

1. create job
2. queue job
3. scheduled job
4. worker processing
5. successful completion
6. temporary failure
7. retry
8. permanent failure
9. cancellation
10. duplicate worker prevention
11. idempotency
12. scheduler restart scenario
13. multi-user isolation
14. provider error normalization

Gunakan mock provider/unit test.

JANGAN menjalankan LIVE Facebook publishing.

Facebook integration/live credential test tetap BLOCKED jika credential/App Review belum tersedia.

==================================================
18. REGRESSION
==================================================

WAJIB menjaga hasil Phase 4.

Pastikan tetap PASS:

- Facebook OAuth
- callback
- session
- connection persistence
- destination persistence
- reconnect
- disconnect
- multi-user isolation
- security
- typecheck
- build
- existing provider-facebook tests

Jangan merusak fitur yang sudah PASS.

==================================================
19. PLATFORM BOUNDARY
==================================================

Pastikan architecture seperti:

Core
|
+-- Queue
+-- Scheduler
+-- Publishing Service
+-- Retry Policy
+-- Provider Registry
       |
       +-- Facebook Provider
       +-- future providers

Jangan:

Core
→ FacebookQueue
→ FacebookScheduler

Queue dan scheduler harus generic.

==================================================
20. TEST COMMANDS
==================================================

Setelah implementation:

- API typecheck
- Web typecheck
- lint
- unit tests
- integration tests yang aman
- production build

Gunakan command yang memang tersedia di repository.

Jangan mengarang command.

Jika test tertentu membutuhkan credential live Facebook:

SKIP/BLOCK sesuai aturan existing.

Jangan membuat fake PASS.

==================================================
21. SECURITY AUDIT
==================================================

Sebelum selesai:

- inspect git diff
- inspect secrets
- inspect .env
- inspect logs
- pastikan token tidak masuk source
- pastikan token tidak masuk test fixture
- pastikan token tidak masuk commit
- pastikan tidak ada credential plaintext baru

==================================================
22. GIT
==================================================

Setelah semua selesai:

1. git status
2. git diff
3. cek secret
4. test
5. build
6. commit

Commit message:

feat: harden publishing queue and scheduler

Kemudian push ke branch aktif.

Jangan force push.

Jika push gagal, laporkan error sebenarnya.

==================================================
23. FINAL REPORT
==================================================

Tampilkan:

PHASE 5 STATUS

QUEUE:
PASS/FAIL

SCHEDULER:
PASS/FAIL

RETRY:
PASS/FAIL

IDEMPOTENCY:
PASS/FAIL

CONCURRENCY:
PASS/FAIL

CANCELLATION:
PASS/FAIL

ERROR NORMALIZATION:
PASS/FAIL

HISTORY:
PASS/FAIL

SECURITY:
PASS/FAIL

TYPECHECK:
PASS/FAIL

TESTS:
PASS/FAIL

BUILD:
PASS/FAIL

FACEBOOK LIVE TEST:
BLOCKED / PASS

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

PUSH:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

FILES CHANGED:
<list>

IMPORTANT:
Jika ada bagian yang belum benar-benar selesai, tulis FAIL/BLOCKED.
Jangan menyatakan PASS berdasarkan asumsi.

==================================================
STOP CONDITION
==================================================

Setelah Phase 5 selesai:

STOP.

Jangan mulai YouTube.
Jangan mulai Instagram.
Jangan mulai TikTok.
Jangan membuat fitur baru di luar Phase 5.

Tunggu instruksi berikutnya.

````
# Prompt: Phase 4 — Facebook Reels Publishing
```

# Prompt — Phase 4: Facebook Reels Publishing

Kita lanjutkan project Content Pilot setelah Phase 3 Facebook Connection selesai.

STATUS SAAT INI:

- Facebook OAuth: PASS
- OAuth callback: PASS
- Session: PASS
- Connection persistence: PASS
- Destination persistence: PASS
- Multi-user isolation: PASS
- Reconnect: PASS
- Disconnect: PASS
- Facebook Page discovery: PASS
- Facebook destination aktif: PASS
- Typecheck: PASS
- Web build: PASS
- API tests: PASS
- Provider Facebook tests: PASS
- Git push Phase 3: SUCCESS

JANGAN membongkar atau mengganti connection layer yang sudah PASS.

Sekarang fokus hanya pada:

PHASE 4 — FACEBOOK REELS PUBLISHING

==================================================
1. TUJUAN
==================================================

Implementasikan publishing Facebook Reels melalui Facebook Graph API resmi.

Flow yang diinginkan:

User
→ pilih video
→ pilih Facebook Page
→ isi caption
→ Publish
→ create upload session
→ upload video
→ monitor processing/status
→ finalize/publish
→ simpan hasil
→ tampilkan status di UI

Arsitektur tetap provider-based.

Core tidak boleh berisi logic khusus Facebook.

Gunakan Facebook provider yang sudah ada dari Phase 3.

==================================================
2. JANGAN IMPLEMENTASI YANG TIDAK DIMINTA
==================================================

JANGAN:

- membuat YouTube provider
- membuat Instagram provider
- membuat TikTok provider
- membuat scheduler penuh
- membuat analytics
- membuat Facebook personal-profile publishing
- menggunakan username/password Facebook
- menggunakan browser automation
- menggunakan scraping
- membuat fake publishing
- membuat fake success
- membuat dummy Facebook response
- mengubah OAuth flow yang sudah PASS
- menghapus connection system yang sudah ada
- mengganti database architecture tanpa alasan
- melakukan refactor besar yang tidak diperlukan

Fokus hanya Facebook Reels publishing.

==================================================
3. OFFICIAL API
==================================================

Gunakan Facebook Graph API resmi.

Flow Reels terdiri dari:

1. initialize/create upload session
2. upload video
3. optional/status checking
4. finalize/publish

Konsep endpoint Reels:

POST /{page-id}/video_reels

dengan upload phase START/FINISH sesuai API yang digunakan provider.

Upload binary menggunakan upload URL dari response initialization.

Jangan hardcode API version jika project sudah memiliki konfigurasi API version.

Gunakan API version configuration yang sudah dipakai project.

Jika provider sudah memiliki abstraction untuk Graph API, gunakan abstraction tersebut.

Jangan membuat HTTP client Facebook kedua hanya untuk fitur Reels.

==================================================
4. PAGE ACCESS TOKEN
==================================================

Gunakan credential/token dari PlatformConnection Facebook yang sudah berhasil dibuat pada Phase 3.

Jangan meminta user memasukkan Page Access Token secara manual jika connection system sudah menyediakannya.

Jangan menyimpan token plaintext di log.

Jangan menampilkan token di frontend.

Jangan mengirim token ke browser.

Jika token harus didekripsi:

decrypt hanya di server/provider layer.

==================================================
5. CAPABILITY
==================================================

Tambahkan capability Facebook:

reels

Capability hanya boleh aktif jika provider Facebook memang mendukungnya.

Jangan membuat UI menganggap publishing tersedia hanya karena provider status = ready.

Bedakan:

provider ready
connection ready
destination ready
publishing capability ready

==================================================
6. MEDIA VALIDATION
==================================================

Sebelum membuat publishing job, lakukan validation.

Minimal periksa:

- file exists
- MIME type
- video format
- duration
- width
- height
- aspect ratio
- file size jika API requirement membutuhkannya

Untuk Reels, gunakan requirement resmi yang berlaku pada API yang dipakai.

Jangan hardcode requirement berdasarkan asumsi lama jika dokumentasi/API response menunjukkan requirement berbeda.

Jika video tidak memenuhi requirement:

JANGAN mengirim video ke Facebook.

Kembalikan error yang jelas kepada user.

Contoh:

"Video tidak memenuhi requirement Facebook Reels: aspect ratio harus 9:16."

Error harus terstruktur dan dapat ditampilkan UI.

==================================================
7. PUBLISHING JOB
==================================================

Gunakan PublishingJob architecture yang sudah ada.

Satu destination = satu publishing job.

Contoh:

Video A
→ Facebook Page YourReels
→ PublishingJob #123

Job harus menyimpan minimal:

- id
- userId
- platform
- connectionId
- destinationId
- mediaId
- content/caption
- status
- providerPostId/videoId jika tersedia
- attempt count
- error code
- error message
- createdAt
- updatedAt
- publishedAt jika berhasil

Sesuaikan dengan database model existing.

JANGAN membuat duplicate job model jika model generic sudah tersedia.

==================================================
8. STATUS MACHINE
==================================================

Gunakan status yang konsisten dengan core.

Minimal:

queued
processing
uploading
publishing
published
failed
retrying
cancelled

Jangan menandai:

published

sebelum Facebook benar-benar menerima publish/finalize successfully.

Response HTTP 200 dari upload initialization BUKAN berarti Reel sudah published.

Jangan membuat fake success.

==================================================
9. FACEBOOK REELS FLOW
==================================================

Implementasikan flow server-side:

STEP 1
Validate connection.

STEP 2
Validate destination.

Pastikan destination adalah Facebook Page yang valid.

STEP 3
Validate media.

STEP 4
Create PublishingJob.

STEP 5
Set status:

processing/uploading

STEP 6
Call Facebook Reels initialization.

Simpan provider video_id/upload session information yang aman jika diperlukan untuk melanjutkan job.

STEP 7
Upload binary video ke upload URL yang diberikan Facebook.

Jangan load file besar sepenuhnya ke memory jika streaming/chunked upload dapat digunakan dengan stack existing.

Gunakan streaming/chunking bila cocok dengan architecture project.

STEP 8
Jika API menyediakan upload/status checking:

gunakan status checking untuk mengetahui apakah upload/processing sudah selesai.

STEP 9
Finalize/publish Reel.

STEP 10
Jika response benar-benar menunjukkan publish berhasil:

status = published

simpan provider post/video ID.

STEP 11
Jika gagal:

status = failed

simpan error terstruktur.

==================================================
10. ERROR HANDLING
==================================================

Bedakan temporary error dan permanent error.

Temporary:

- timeout
- network error
- temporary Facebook API error
- rate limit
- temporary upload failure

Permanent:

- invalid token
- permission denied
- invalid destination
- unsupported media
- invalid parameter
- app permission problem

Temporary error boleh masuk retry mechanism jika queue architecture existing mendukungnya.

Permanent error jangan otomatis retry tanpa perubahan.

Jangan retry:

invalid OAuth token
permission denied
unsupported media

==================================================
11. IDEMPOTENCY
==================================================

Publishing harus sebisa mungkin idempotent.

Jangan membuat duplicate Reel ketika worker restart setelah request Facebook berhasil tetapi response tidak terbaca.

Gunakan provider operation ID / job metadata / existing publishing attempt mechanism jika tersedia.

Audit existing architecture terlebih dahulu.

Jangan membuat sistem idempotency baru jika sudah ada mekanisme yang dapat digunakan.

==================================================
12. PUBLISHING ATTEMPT
==================================================

Jika PublishingAttempt sudah tersedia:

gunakan untuk mencatat setiap percobaan.

Minimal:

- jobId
- attempt number
- startedAt
- finishedAt
- status
- provider request stage
- provider response code
- normalized error code
- normalized error message

Jangan menyimpan:

- access token
- refresh token
- secret
- credential plaintext

==================================================
13. BACKEND API
==================================================

Tambahkan endpoint API hanya jika memang belum tersedia.

Contoh konsep:

POST /api/publishing/facebook/reels

atau gunakan routing convention existing.

JANGAN membuat route duplicate.

Endpoint harus:

- authenticated
- authorize user
- validate input
- validate destination ownership
- validate media ownership
- create publishing job
- return job information

Jangan menerima Page ID arbitrary lalu langsung publish.

Pastikan destination memang milik connection/user yang sedang login.

==================================================
14. FRONTEND
==================================================

Tambahkan UI publishing Reels menggunakan design system existing.

Jangan membuat halaman baru jika existing Upload/Publish page dapat digunakan.

Flow:

Upload/select video

↓

Video preview

↓

Caption

↓

Platform:
Facebook

↓

Destination:
Facebook Page

↓

Validation

↓

Publish

↓

Publishing status

Contoh status:

Ready
Uploading
Processing
Publishing
Published
Failed

Jika Facebook connection belum tersedia:

tampilkan:

"Connect Facebook"

Jika connection tersedia tetapi destination tidak tersedia:

tampilkan:

"No Facebook Page available"

Jika media invalid:

tampilkan alasan validation.

Jangan menampilkan "Published" sebelum backend benar-benar menyatakan published.

==================================================
15. HISTORY
==================================================

Jika History system sudah tersedia:

Facebook Reels publishing harus muncul di history.

Minimal:

- thumbnail/media
- platform
- destination
- caption
- status
- created time
- published time
- error jika gagal

Gunakan existing History architecture.

Jangan membuat history system kedua.

==================================================
16. RETRY
==================================================

Gunakan retry architecture existing.

Jika belum tersedia:

buat minimal retry abstraction yang tidak mengunci core ke Facebook.

Jangan membangun scheduler kompleks.

Retry hanya untuk error yang memang temporary.

Gunakan exponential backoff jika cocok dengan queue architecture.

==================================================
17. SECURITY
==================================================

Periksa:

- authorization
- user isolation
- destination ownership
- media ownership
- token handling
- log redaction
- request validation
- file validation

Pastikan user A tidak dapat menggunakan destination milik user B.

Pastikan user A tidak dapat publish media milik user B.

Pastikan access token tidak muncul di:

- frontend
- API response
- logs
- errors
- database plaintext

==================================================
18. TESTING
==================================================

Karena live Facebook publishing membutuhkan credential/app configuration yang sesuai, JANGAN memalsukan live test.

Buat automated tests menggunakan mocked provider/API response.

Test minimal:

1. valid Reels publish request
2. invalid media
3. invalid destination
4. missing connection
5. expired/invalid token
6. permission denied
7. Facebook API temporary error
8. Facebook API permanent error
9. upload failure
10. finalize failure
11. successful publish response
12. retryable error
13. non-retryable error
14. user isolation
15. duplicate/idempotency scenario
16. token redaction

Test harus verificar status transition.

Contoh:

queued
→ processing
→ uploading
→ publishing
→ published

Failure:

queued
→ processing
→ uploading
→ failed

Jangan membuat test:

"Facebook published successfully"

jika hanya berdasarkan mock tanpa membedakannya sebagai mocked test.

Label dengan jelas:

MOCKED / UNIT / INTEGRATION

==================================================
19. LIVE TEST RULE
==================================================

Live Facebook publish test hanya boleh dilakukan jika credential/App Review/permission yang diperlukan memang tersedia.

Jika belum tersedia:

status:

LIVE PUBLISH TEST: BLOCKED

Bukan:

PASS

Jangan membuat fake credential.

Jangan membuat fake Page.

Jangan mengubah database agar terlihat seperti publish berhasil.

Jika live test blocked, tetap pastikan implementation dan automated tests PASS.

==================================================
20. API RESPONSE NORMALIZATION
==================================================

Provider Facebook harus menerjemahkan response Facebook menjadi error/status generic.

Core tidak boleh bergantung pada raw Facebook error structure.

Contoh:

Facebook error:
permission denied

Core:

PERMISSION_DENIED

Facebook error:
invalid token

Core:

AUTHENTICATION_FAILED

Facebook error:
rate limit

Core:

RATE_LIMITED

Facebook error:
invalid media

Core:

INVALID_MEDIA

Gunakan existing error abstraction jika sudah tersedia.

==================================================
21. OBSERVABILITY
==================================================

Tambahkan logging yang aman untuk:

- job started
- upload started
- upload completed
- publish started
- publish completed
- failure
- retry

Jangan log:

- access token
- refresh token
- authorization header
- cookies
- secrets

Gunakan job ID dan destination ID untuk tracing.

==================================================
22. DOCUMENTATION
==================================================

Update documentation yang relevan.

Minimal dokumentasikan:

- Facebook Reels publishing architecture
- publishing flow
- status machine
- required permissions
- media requirements
- error handling
- retry behavior
- live test limitation

Jika docs/PLATFORM_MODULES.md sudah ada:

UPDATE FILE tersebut.

Jangan membuat duplicate documentation.

Jika README memiliki current implementation status:

update status Facebook Reels sesuai kondisi sebenarnya.

==================================================
23. NO UNRELATED CHANGES
==================================================

Jangan menyentuh:

- YouTube
- Instagram
- TikTok
- X
- Pinterest
- LinkedIn

Jangan mengubah:

- existing Facebook OAuth
- connection callback
- destination discovery

kecuali benar-benar diperlukan untuk publishing dan perubahan tersebut terbukti aman.

Jika menemukan bug lama pada connection layer:

JANGAN melakukan refactor besar.

Catat sebagai finding kecuali bug tersebut benar-benar memblokir Phase 4.

==================================================
24. BUILD & VERIFICATION
==================================================

Setelah implementation:

1. typecheck
2. lint
3. unit tests
4. provider tests
5. API tests
6. web tests
7. production build
8. inspect git diff
9. inspect git status

Semua harus PASS sebelum commit.

Jika ada test lama yang unrelated dan gagal:

jangan menghapus test hanya agar PASS.

Investigasi dan laporkan.

==================================================
25. GIT
==================================================

Sebelum commit:

- git status
- git diff
- pastikan tidak ada secret
- pastikan perubahan hanya Phase 4
- pastikan tidak ada file temporary

Commit:

feat: add facebook reels publishing

Push langsung ke branch project yang sedang digunakan.

JANGAN force push.

Setelah push:

verifikasi remote.

==================================================
26. FINAL REPORT
==================================================

Di akhir tampilkan:

PHASE 4 STATUS

Facebook Reels Provider:
PASS / INCOMPLETE

Media Validation:
PASS / INCOMPLETE

Publishing Job:
PASS / INCOMPLETE

Upload Flow:
PASS / INCOMPLETE

Publish Flow:
PASS / INCOMPLETE

Status Tracking:
PASS / INCOMPLETE

Retry:
PASS / INCOMPLETE

History:
PASS / INCOMPLETE

Security:
PASS / INCOMPLETE

Tests:
PASS / INCOMPLETE

Build:
PASS / INCOMPLETE

LIVE FACEBOOK TEST:
PASS / BLOCKED

Jika live test blocked karena credential/App Review/permission:

jelaskan alasan sebenarnya.

Jangan menyatakan live publish berhasil.

Git:

GIT STATUS: CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS / FAILED
REMOTE VERIFIED: YES / NO

==================================================
STOP CONDITION
==================================================

Setelah Phase 4 selesai:

STOP.

Jangan lanjut ke Facebook Video/Photo/Text Post.

Jangan lanjut YouTube.

Jangan lanjut Instagram.

Jangan lanjut TikTok.

Tunggu instruksi berikutnya.
````
# Prompt: Phase 3 — Facebook Reels Publishing
```
Lanjutkan project Content Pilot dari kondisi terakhir.

STATUS TERAKHIR:
- Facebook OAuth: PASS
- Session: PASS
- Connection persistence: PASS
- Destination persistence: PASS
- Multi-user isolation: PASS
- Reconnect: PASS
- Disconnect: PASS
- Security: PASS
- Typecheck: PASS
- Build: PASS
- Connection Layer Status: READY
- Facebook Page destination: ACTIVE

Sekarang mulai PHASE 3:
FACEBOOK REELS PUBLISHING.

PENTING:
Jangan merusak connection layer yang sudah PASS.
Jangan mengubah arsitektur core tanpa alasan.
Jangan membuat fake/mock publishing success.
Jangan menggunakan Facebook username/password automation.
Gunakan Facebook/Meta official Graph API.

==================================================
1. RESEARCH TERLEBIH DAHULU
==================================================

Sebelum coding:

Audit kembali dokumentasi resmi Meta/Facebook API yang relevan untuk Page Reels publishing.

Verifikasi secara aktual:

- endpoint upload Reels
- API version yang digunakan project
- required access token
- required permissions
- Page access token requirement
- upload flow
- resumable upload jika diperlukan
- video requirements
- caption requirements
- publish/finalize flow
- status checking
- error response
- rate limits
- restrictions/limitations

JANGAN mengarang endpoint atau permission.

Jika ada bagian yang belum dapat diverifikasi:
MARK AS NEEDS VERIFICATION

Gunakan hasil research tersebut sebagai dasar implementation.

==================================================
2. PROVIDER ARCHITECTURE
==================================================

Facebook publishing harus tetap berada di Facebook provider.

Jangan memasukkan Facebook-specific API logic ke core.

Gunakan struktur/modul existing repository jika sudah ada.

Jika diperlukan, pisahkan:

facebook/
  auth/
  api/
  reels/
  provider/

Tetapi jangan membuat duplicate architecture jika repository sudah memiliki struktur yang sesuai.

Core hanya mengetahui konsep generik:

PublishingJob
Destination
Media
Provider
Capability

Facebook provider menangani detail API Facebook.

==================================================
3. CAPABILITY
==================================================

Tambahkan/aktifkan capability Facebook Reels hanya jika API research membuktikan capability tersebut tersedia.

Contoh konsep:

facebook:
  capabilities:
    - reels

Jangan hardcode capability sebagai available jika implementation belum benar-benar siap.

==================================================
4. PUBLISHING JOB
==================================================

Gunakan PublishingJob yang sudah dirancang.

Contoh:

Media
  ↓
PublishingJob
  ↓
provider = facebook
destination = Facebook Page
content_type = reels

Status:

draft
queued
processing
uploading
publishing
published
failed
retrying
cancelled

Jangan membuat global status yang menghilangkan status per destination.

==================================================
5. MEDIA VALIDATION
==================================================

Sebelum upload:

- validasi MIME type
- validasi file size
- validasi video metadata
- validasi duration
- validasi dimensions
- validasi requirement Facebook berdasarkan dokumentasi resmi
- pastikan file benar-benar tersedia di storage

Jangan upload file yang jelas tidak memenuhi requirement.

Error harus dikembalikan dengan jelas kepada user.

==================================================
6. PUBLISH FLOW
==================================================

Implement flow sebenarnya:

User memilih video
→ pilih Facebook Page
→ pilih Reels
→ isi caption
→ submit
→ create PublishingJob
→ queue
→ worker
→ Facebook provider
→ upload
→ publish/finalize
→ cek status jika diperlukan
→ simpan result
→ update job status

Jika Facebook berhasil:

published

Jika gagal:

failed

Simpan informasi error yang aman.

==================================================
7. QUEUE / WORKER
==================================================

Gunakan queue/worker architecture existing.

Jangan membuat queue Facebook terpisah jika core queue sudah tersedia.

Flow:

PublishingJob
→ Queue
→ Worker
→ Provider Registry
→ Facebook Provider
→ publishReel()

Worker harus dapat menangani:

- retryable error
- permanent error
- timeout
- rate limit
- invalid token
- permission denied
- unsupported media

==================================================
8. RETRY
==================================================

Temporary error:

- network error
- timeout
- temporary API error
- rate limit

→ retry sesuai mekanisme queue existing.

Permanent error:

- invalid token
- permission denied
- invalid destination
- unsupported media
- invalid request

→ failed tanpa infinite retry.

Simpan:

- attempt count
- error code
- error message
- timestamp
- provider response metadata jika aman

Jangan menyimpan access token di log.

==================================================
9. DATABASE
==================================================

Gunakan schema existing.

Jangan membuat model Facebook-specific seperti:

FacebookReelJob

jika PublishingJob generik sudah tersedia.

Gunakan:

Media
Post
PublishingJob
PublishingAttempt
Destination
PlatformConnection

Jika migration diperlukan:

- buat migration
- jangan menghapus data existing
- jangan reset database
- jangan menghapus connection user yang sudah berhasil
- verifikasi migration sebelum apply

==================================================
10. UI
==================================================

Update UI existing, jangan membuat dashboard baru.

Tambahkan flow minimal:

Upload Content
→ pilih video
→ pilih Facebook Page
→ pilih Reels
→ caption
→ Publish

Tampilkan:

- selected destination
- media preview
- caption
- publishing status
- error message jika gagal

Jangan menampilkan YouTube/Instagram/TikTok sebagai aktif.

Jika provider belum tersedia:
Coming Soon / unavailable.

UI harus responsive desktop dan mobile.

==================================================
11. SECURITY
==================================================

Pastikan:

- user hanya dapat menggunakan connection miliknya
- user hanya dapat publish ke destination miliknya
- access token tidak dikirim ke frontend
- access token tidak muncul di logs
- jangan commit secret
- validasi authorization setiap PublishingJob
- validasi ownership Media
- validasi ownership Destination
- validasi MIME/file upload
- cegah path traversal
- jangan menerima arbitrary internal URLs tanpa validasi jika ada remote media support

==================================================
12. TESTING
==================================================

Buat/ubah test yang relevan.

Minimal test:

1. Facebook provider registration
2. capability detection
3. destination ownership
4. media validation
5. PublishingJob creation
6. queue dispatch
7. retryable error
8. permanent error
9. successful publish response handling
10. user isolation

Untuk integration test Facebook:

Gunakan API resmi dan credential yang memang tersedia.

Jangan menggunakan fake success untuk menyatakan publishing berhasil.

Jika credential/API environment belum tersedia:

- jangan mengarang PASS
- jalankan unit/integration test yang dapat dilakukan
- tandai LIVE FACEBOOK PUBLISH TEST sebagai BLOCKED/NEEDS CREDENTIAL

==================================================
13. BUILD & VERIFICATION
==================================================

Setelah implementation:

API typecheck
Web typecheck
Lint
Unit tests
Integration tests yang aman
Production build

Kemudian verifikasi UI melalui browser.

Pastikan connection layer tetap bekerja:

Facebook connection
→ destination
→ Accounts
→ Platforms

Jangan sampai Phase 3 merusaknya.

==================================================
14. GIT
==================================================

Sebelum commit:

git status
git diff
audit secret
audit token
audit API key

Jangan commit:

.env
API key
access token
refresh token
password
credential

Commit hanya perubahan Phase 3.

Commit message:

feat: add facebook reels publishing

Push ke branch aktif.

Jangan force push.

Jika push gagal, laporkan error sebenarnya.

==================================================
15. FINAL REPORT
==================================================

Tampilkan:

PHASE 3 STATUS

FACEBOOK API RESEARCH: PASS/NEEDS VERIFICATION
FACEBOOK REELS PROVIDER: PASS/FAIL
MEDIA VALIDATION: PASS/FAIL
PUBLISHING JOB: PASS/FAIL
QUEUE: PASS/FAIL
WORKER: PASS/FAIL
RETRY: PASS/FAIL
ERROR HANDLING: PASS/FAIL
UI: PASS/FAIL
SECURITY: PASS/FAIL
TYPECHECK: PASS/FAIL
TESTS: PASS/FAIL
BUILD: PASS/FAIL

LIVE FACEBOOK PUBLISH TEST:
PASS / FAIL / BLOCKED

CONNECTION LAYER REGRESSION:
PASS / FAIL

GIT STATUS:
CLEAN / DIRTY

COMMIT:
<hash>

PUSH:
SUCCESS / FAILED

Jangan menyatakan publishing READY jika live API flow belum benar-benar diverifikasi.

Jika semua yang diperlukan PASS:

PHASE 3 FACEBOOK REELS: READY

STOP setelah laporan.
Jangan lanjut ke Phase 4 tanpa instruksi.

````
# 
```
Prompt: Verify Facebook Connection & Destination Persistence

Lanjutkan dari kondisi project saat ini.

Facebook OAuth sudah berhasil dan UI menunjukkan:

- Facebook OAuth ready
- Facebook account connected
- Destination ditemukan
- Destination: Yourdreels (page)
- Destination status: active
- Scope sudah tersedia

JANGAN membuat fitur publishing baru dulu.

Tugas sekarang hanya melakukan verifikasi dan hardening connection layer.

1. Audit implementasi Facebook connection yang sudah ada.

Pastikan:
- OAuth callback benar
- access token tidak disimpan plaintext di source code
- PlatformConnection tersimpan dengan benar
- Facebook account identity tersimpan
- Page/Destination tersimpan dengan benar
- destination provider = facebook
- destination type = page
- destination external ID tersimpan
- connection dan destination memiliki relasi yang benar
- data tidak tertukar antar user

2. Audit endpoint:

- login/session
- /api/auth/me
- /api/connections/facebook/connect
- /api/connections/facebook/callback
- endpoint destination discovery
- endpoint connection status
- endpoint reconnect
- endpoint disconnect

Pastikan semua endpoint menggunakan session/user yang benar.

3. Audit persistence.

Lakukan test:

Connect Facebook
→ OAuth callback
→ save connection
→ discover Page
→ save destination
→ refresh browser
→ login/session tetap valid
→ Accounts tetap menunjukkan Connected
→ Platforms tetap menunjukkan destination Active.

Jangan membuat fake/mock success.

4. Test multi-user isolation.

Pastikan user A tidak dapat melihat:
- connection user B
- Facebook Page user B
- token user B
- destination user B.

5. Test reconnect.

Pastikan reconnect tidak membuat duplicate PlatformConnection atau duplicate Destination jika connection yang sama sudah ada.

6. Test disconnect.

Pastikan disconnect:
- mencabut/menghapus connection sesuai desain keamanan
- destination terkait ditangani dengan benar
- UI berubah menjadi disconnected
- tidak meninggalkan token aktif yang tidak semestinya.

7. Audit database/schema.

Jika schema sudah ada, jangan mengganti arsitektur tanpa alasan.

Jika ada masalah, perbaiki hanya masalah yang diperlukan untuk connection persistence.

8. Jangan implement:
- Facebook publishing
- Reels uploader
- video publishing
- queue production
- scheduler production
- YouTube
- Instagram
- TikTok.

9. Jalankan:
- API typecheck
- Web typecheck
- lint jika tersedia
- test yang relevan
- production build jika aman

10. Setelah selesai, berikan laporan:

FACEBOOK CONNECTION: PASS/FAIL
OAUTH CALLBACK: PASS/FAIL
SESSION: PASS/FAIL
CONNECTION PERSISTENCE: PASS/FAIL
DESTINATION PERSISTENCE: PASS/FAIL
MULTI-USER ISOLATION: PASS/FAIL
RECONNECT: PASS/FAIL
DISCONNECT: PASS/FAIL
SECURITY: PASS/FAIL
TYPECHECK: PASS/FAIL
BUILD: PASS/FAIL

Jika semua PASS:

CONNECTION LAYER STATUS: READY

Jangan lanjut ke publishing sampai saya memberikan instruksi berikutnya.

````
# Prompt: Fix Facebook OAuth Domain Configuration
```

Perbaiki masalah Facebook OAuth pada project Content Pilot.

Kondisi saat ini:

- Backend API: https://api.contentpilot.biz.id
- Frontend: https://contentpilot.biz.id
- Facebook provider: sudah registered
- oauthStatus: ready
- POST /api/connections/facebook/connect: HTTP 200
- Backend sudah menghasilkan authorizationUrl
- Login/session web sudah berhasil
- Masalah terjadi ketika authorizationUrl dibuka di Facebook:
  "Can't load URL"
  "The domain of this URL isn't included in the app's domains."

JANGAN mengubah architecture besar.
JANGAN membuat fake OAuth.
JANGAN menggunakan Facebook username/password automation.
Gunakan Facebook/Meta OAuth resmi.

TUJUAN:

Buat Facebook OAuth benar-benar dapat membuka dialog Facebook dan kembali ke:

https://contentpilot.biz.id/accounts?connect=success

PERIKSA DAHULU:

1. Baca implementasi Facebook provider.
2. Cari:
   - META_APP_ID
   - META_APP_SECRET
   - META_REDIRECT_URI
   - authorizationUrl generation
   - callback route
   - WEB_BASE_URL
3. Pastikan tidak ada redirect URI yang berbeda antara:
   - environment
   - backend
   - frontend
   - authorization URL
   - callback handler
4. Jangan mengarang URL.

DOMAIN YANG BENAR:

Frontend:
https://contentpilot.biz.id

API:
https://api.contentpilot.biz.id

Facebook OAuth callback harus menggunakan API callback yang memang sudah digunakan backend.

JANGAN menggunakan:
- localhost
- 127.0.0.1
- http://
- contentpilot.biz.id untuk callback jika backend callback sebenarnya berada di api.contentpilot.biz.id

Pastikan authorization URL menggunakan redirect_uri yang EXACTLY sama dengan callback backend.

PERIKSA META CONFIGURATION:

Dokumentasikan kepada saya konfigurasi yang harus diisi di Meta Developer App:

App Domains:
contentpilot.biz.id

Jika Meta meminta domain/subdomain untuk callback, gunakan domain yang sesuai dengan redirect URI yang sebenarnya.

Valid OAuth Redirect URIs:
gunakan EXACT callback URI yang dipakai oleh backend.

Jangan membuat callback URI baru hanya untuk melewati error.

PENTING:

Redirect URI harus identik secara exact antara:

1. META_REDIRECT_URI
2. authorization URL
3. backend callback route
4. Meta Developer → Facebook Login → Valid OAuth Redirect URIs

Termasuk:
- https
- hostname
- path
- trailing slash jika ada

Jangan melakukan perubahan kode jika masalah hanya berasal dari Meta Developer configuration.

Jika kode ternyata sudah benar, katakan dengan jelas:

CODE STATUS: CORRECT
PROBLEM: META APP CONFIGURATION

Kemudian tampilkan konfigurasi Meta yang harus saya masukkan.

SETELAH CONFIGURATION DIPERBAIKI:

Restart hanya jika environment variable memang berubah:

sudo systemctl restart content-pilot-api

Kemudian verifikasi:

curl http://127.0.0.1:4000/api/platforms

Harus menunjukkan:

facebook
publishingAvailable: true
publishingStatus: ready
oauthStatus: ready

Kemudian test:

POST /api/connections/facebook/connect

Pastikan response:

status = ready
authorizationUrl = Facebook OAuth URL

Jangan menampilkan META_APP_SECRET atau access token ke output/chat.

TEST END-TO-END:

1. Login ke:
https://contentpilot.biz.id/accounts

2. Pastikan session aktif.

3. Klik:
Connect Facebook

4. Facebook OAuth harus terbuka tanpa:
"Can't load URL"

5. Login Facebook.

6. Approve permissions jika diminta.

7. Facebook redirect ke backend callback.

8. Backend menyelesaikan connection.

9. Redirect kembali ke:

https://contentpilot.biz.id/accounts?connect=success

10. Frontend menampilkan Facebook:
Connected / Ready

11. Pastikan connection tersimpan ke user yang sedang login.

SECURITY:

- Jangan print META_APP_SECRET.
- Jangan print access token.
- Jangan commit .env.
- Jangan membuat fake connection.
- Jangan membuat fake success.
- Jangan bypass OAuth.
- Jangan membuat database connection palsu.
- Jangan mengubah authentication/session yang sudah berhasil.

SETELAH SELESAI:

Jalankan:
- API typecheck
- Web typecheck
- Web production build

Kemudian laporkan singkat:

1. Root cause
2. Apakah kode perlu diubah
3. Konfigurasi Meta yang diperlukan
4. Redirect URI yang digunakan
5. Hasil API verification
6. Hasil OAuth test
7. Files changed
8. Build status

Jika masalah masih terjadi, JANGAN menebak.

Tampilkan authorization URL TANPA credential/token sensitif dan periksa:
- app ID
- redirect_uri
- domain
- callback path

STOP setelah menemukan dan memperbaiki root cause.
````
# Prompt: Fix Facebook Connection Flow
```
# Prompt — Fix Facebook Connection Flow

Kita lanjutkan project Content Pilot.

JANGAN mengulang atau mengubah sistem login utama karena login web sudah berhasil.

## STATUS SAAT INI

Hasil audit terakhir:

- Web Content Pilot sudah bisa dibuka.
- Login/register/session sudah berhasil.
- `/api/auth/login` sudah bekerja.
- `/api/auth/me` dengan session cookie sudah bekerja.
- `oauthStatus` Facebook di `/api/platforms` sudah `ready`.
- Facebook provider sudah terdaftar.
- `publishingAvailable: true`.
- Frontend sudah menampilkan Facebook = Ready.
- Masalah sekarang hanya pada tombol:

`Connect Facebook`

Saat tombol ditekan, frontend menampilkan:

`Unable to start the connection flow.`

Facebook login di website Facebook asli bisa dilakukan dengan normal.

## MASALAH YANG HARUS DISELESAIKAN

Cari penyebab sebenarnya kenapa:

Frontend
→ Connect Facebook
→ POST `/api/connections/facebook/connect`
→ connection flow

tidak berhasil dimulai.

Jangan berasumsi penyebabnya.

Audit kode yang benar-benar ada di repository.

---

# ATURAN PENTING

1. Jangan mengubah sistem `/api/auth/login`.
2. Jangan mengubah `/api/auth/me` kecuali benar-benar diperlukan dan terbukti menjadi penyebab.
3. Jangan menghapus authentication/session system.
4. Jangan membuat fake Facebook connection.
5. Jangan membuat fake `ready` status.
6. Jangan menyimpan access token Facebook secara plaintext.
7. Jangan menggunakan Facebook username/password automation.
8. Gunakan OAuth resmi Meta/Facebook.
9. Jangan membuat endpoint dummy hanya supaya tombol terlihat berhasil.
10. Jangan mengubah architecture provider yang sudah ada tanpa alasan.
11. Jangan mengubah fitur publishing.
12. Fokus hanya pada connection flow Facebook.
13. Jangan menganggap GET dan POST endpoint sama.
14. Pastikan method HTTP frontend dan backend benar-benar cocok.
15. Jangan menganggap callback berhasil hanya karena redirect URL terbuka.

---

# 1. AUDIT FRONTEND

Cari komponen/page yang menangani:

`Connect Facebook`

Periksa:

- URL endpoint yang dipanggil
- HTTP method
- request body
- headers
- credentials mode
- `credentials: "include"`
- response handling
- error handling
- redirect handling
- popup/new window jika ada
- authorization URL handling

Pastikan frontend memanggil endpoint yang benar.

Target konsep:

```text
POST /api/connections/facebook/connect

````
# Prompt: Fix Web Login
```
Fix only the Content Pilot web login.

Current issue:
https://contentpilot.biz.id/accounts shows "Invalid email or password" even though the account credentials should be valid.

Audit the existing authentication flow:
- /api/auth/login
- user lookup/database
- password hashing/verification
- session cookie
- /api/auth/me
- frontend login request

Find the actual cause from the existing code/database. Do NOT change Facebook OAuth or reverse proxy.

Fix the login with the smallest necessary change.

Then run:
- API typecheck
- Web typecheck
- build

Finally verify login -> session cookie -> /api/auth/me.

Do not create fake users or bypass password verification.

````
# Prompt — Fix Web Login & Session
```
Audit dan perbaiki masalah login web Content Pilot.

Kondisi:
- Facebook OAuth sudah READY.
- META_APP_ID dan META_APP_SECRET sudah terbaca service.
- /api/platforms = oauthStatus ready.
- Facebook native login berhasil.
- https://contentpilot.biz.id berjalan di Next.js port 3001.
- API berjalan di 4000.
- Saat membuka https://contentpilot.biz.id/accounts muncul Route not found /accounts.

Tugas:
1. Audit route login dan accounts di apps/web.
2. Pastikan frontend menggunakan API https://api.contentpilot.biz.id dengan benar.
3. Periksa session cookie, credentials: include, CORS, redirect OAuth, dan callback.
4. Pastikan login web benar-benar membuat session sebelum /accounts diakses.
5. Periksa apakah route /accounts memang ada. Jika route frontend berbeda, perbaiki redirect ke route yang benar.
6. Jangan ubah Facebook OAuth provider yang sudah READY.
7. Jangan ubah project toko-online port 3000.
8. Jangan membuat fake login atau fake success.
9. Perbaiki hanya bagian yang diperlukan.
10. Setelah selesai jalankan build/typecheck yang relevan dan laporkan hasilnya.

Fokus: login web → session → redirect → accounts.

````

# Prompt — Fix Frontend & Reverse Proxy
```
Lanjutkan dari audit terakhir.

Fokus hanya memperbaiki akses frontend Content Pilot.

1. Pastikan frontend Next.js di /root/content-pilot/apps/web berjalan di port 3000.
2. Jangan ubah API Fastify port 4000.
3. Pastikan contentpilot.biz.id diarahkan Nginx ke 127.0.0.1:3000.
4. Pastikan api.contentpilot.biz.id tetap diarahkan ke 127.0.0.1:4000.
5. Jangan mengubah kode Facebook/OAuth.
6. Restart service yang diperlukan.
7. Verifikasi:
   - curl -I http://127.0.0.1:3000
   - curl -I https://contentpilot.biz.id
   - curl http://127.0.0.1:4000/api/platforms
8. Jika ada error, perbaiki hanya bagian yang diperlukan.

Jangan refactor besar. Jangan membuat fitur baru.
Setelah selesai tampilkan hasil ketiga verifikasi tersebut.


```

# 
```

Audit deployment/domain Content Pilot.

Masalah:
https://contentpilot.biz.id/accounts
masuk ke API dan menghasilkan:
Route not found: /accounts

API seharusnya tetap:
https://api.contentpilot.biz.id

Cari di repository dan konfigurasi deployment:
1. Di mana frontend Next.js/web dijalankan.
2. Port frontend.
3. Domain/host yang seharusnya digunakan frontend.
4. Kenapa contentpilot.biz.id saat ini diarahkan ke API.
5. Konfigurasi nginx/Cloudflare/reverse proxy yang menyebabkan ini.

Jangan ubah kode.
Jangan membuat konfigurasi baru.
Cari dan laporkan penyebab serta URL frontend yang benar.

STOP setelah ditemukan.

```

# 
```

Lanjut verifikasi Facebook Connect.

Endpoint yang benar:
POST /api/connections/facebook/connect

Audit apps/web dan apps/api untuk memastikan frontend memanggil endpoint ini dengan:
- POST
- authenticated session/cookie
- provider facebook

Jangan ubah kode dulu.
Cari flow Connect Facebook yang sudah ada dan tentukan cara test yang benar dari browser/frontend.

STOP setelah ditemukan.

```

# Prompt: Audit Route Facebook Connect
```

Audit sekarang kenapa endpoint:

GET /api/connections/facebook/connect

menghasilkan 404 Route not found.

Cari route Facebook connection yang BENAR di seluruh repository, jangan berasumsi berdasarkan nama test.

Periksa:
- route registration
- controller/handler
- auth router
- provider-facebook
- apps/api
- worker jika relevan

Cari endpoint yang sebenarnya untuk memulai OAuth Facebook dan jelaskan:
1. route yang benar
2. method HTTP yang benar
3. file yang mendaftarkan route
4. kenapa /api/connections/facebook/connect tidak ditemukan

Jangan mengubah kode dulu.
Jangan membuat route baru sebelum audit selesai.
Jalankan grep/search seluruh repository.

STOP setelah menemukan penyebab dan route yang benar.

```

# Prompt — Audit Meta Environment Configuration
```
Audit konfigurasi Meta/Facebook OAuth pada project /root/content-pilot.

JANGAN mengubah kode atau menghapus file terlebih dahulu.

Masalah saat ini:
- GET /api/platforms berhasil HTTP 200
- Facebook providerRegistered=true
- oauthProviderRegistered=true
- oauthStatus="needs_configuration"
- META_APP_ID dan META_APP_SECRET tidak ditemukan oleh grep di /root/content-pilot/.env
- Service berjalan sebagai systemd service: content-pilot-api

Cari penyebab sebenarnya secara menyeluruh.

Periksa:
1. /root/content-pilot/.env
2. .env.example
3. seluruh source code untuk META_APP_ID dan META_APP_SECRET
4. konfigurasi dotenv/env loader
5. systemd unit content-pilot-api
6. EnvironmentFile pada systemd jika ada
7. WorkingDirectory service
8. environment yang benar-benar diterima process Node.js
9. apakah service menggunakan file .env yang berbeda
10. apakah nama variable yang digunakan source code berbeda
11. apakah ada prefix/scope/config object yang menyebabkan variable tidak terbaca
12. apakah service perlu restart setelah environment berubah

Gunakan perintah audit yang aman dan JANGAN pernah menampilkan nilai META_APP_SECRET secara plaintext.

Tampilkan:
- lokasi konfigurasi yang sebenarnya digunakan
- nama variable yang sebenarnya dibaca aplikasi
- apakah META_APP_ID terdeteksi
- apakah META_APP_SECRET terdeteksi
- dari mana systemd/service mendapatkan environment
- penyebab oauthStatus masih needs_configuration
- langkah perbaikan paling tepat

PENTING:
- Jangan meminta saya mengirim App Secret ke chat.
- Jangan commit secret.
- Jangan mengubah source code kecuali setelah akar masalah konfigurasi ditemukan.
- Jangan mengarang hasil.
- Setelah menemukan penyebab, berhenti dan laporkan perbaikannya terlebih dahulu.


```

# 
```


Prompt: Finalize Facebook OAuth Environment Configuration

Lanjutkan dari audit sebelumnya.

JANGAN mengubah source code OAuth.
JANGAN refactor.
JANGAN mengubah architecture.
JANGAN mengubah nginx atau Cloudflare.

Kondisi yang sudah terverifikasi:

API:
https://api.contentpilot.biz.id

Facebook OAuth callback:
https://api.contentpilot.biz.id/api/connections/facebook/callback

Callback HTTPS sudah reachable dan route mengembalikan HTTP 302.

Masalah saat ini hanya konfigurasi:
META_APP_ID dan META_APP_SECRET masih missing.

Sekarang lakukan:

1. Buka /root/contentpilot/.env.
2. Jangan tampilkan META_APP_SECRET ke output.
3. Jangan tampilkan credential sensitif.
4. Verifikasi apakah variable berikut tersedia:

META_APP_ID
META_APP_SECRET
META_REDIRECT_URI
WEB_BASE_URL

5. META_REDIRECT_URI harus:

https://api.contentpilot.biz.id/api/connections/facebook/callback

6. Cari di repository konfigurasi frontend Next.js yang sebenarnya.
   Tentukan apakah frontend berjalan pada:
   - https://contentpilot.biz.id
   - localhost:3000
   - domain lain

JANGAN menebak.

7. Periksa package.json, apps/web, konfigurasi Next.js, deployment config, dan environment references untuk menentukan WEB_BASE_URL yang benar.

8. Jika frontend memang menggunakan:
https://contentpilot.biz.id

maka set:

WEB_BASE_URL=https://contentpilot.biz.id

Jika bukan, gunakan URL frontend yang benar berdasarkan hasil audit.

9. Untuk META_APP_ID dan META_APP_SECRET:
   - jika sudah ada, jangan ubah
   - jika kosong/missing, jangan mengarang nilainya
   - cukup laporkan bahwa saya harus memasukkannya secara manual

10. Setelah konfigurasi non-secret selesai, restart service:

systemctl restart content-pilot-api

11. Verifikasi:

curl -s http://127.0.0.1:4000/api/platforms

12. Verifikasi juga:

curl -s https://api.contentpilot.biz.id/api/platforms

13. Pastikan Facebook tidak lagi dilaporkan sebagai configuration error jika META_APP_ID dan META_APP_SECRET sudah tersedia.

14. Jangan mencoba login Facebook melalui callback secara langsung.

15. Jangan melakukan perubahan lain.

OUTPUT:

=== FINAL OAUTH CONFIG ===

API:
...

FRONTEND:
...

META_REDIRECT_URI:
...

META_APP_ID:
configured / missing

META_APP_SECRET:
configured / missing

WEB_BASE_URL:
...

FACEBOOK PROVIDER:
configured / not configured

API STATUS:
...

EXACT NEXT ACTION:
...

STOP.
```

# 
```

Prompt: Audit Final OAuth Configuration

Lanjutkan audit konfigurasi OAuth Facebook saja.

JANGAN mengubah source code OAuth.
JANGAN melakukan refactor.
JANGAN mengubah nginx atau Cloudflare.

Kondisi yang sudah diketahui:

API:
https://api.contentpilot.biz.id

Callback:
https://api.contentpilot.biz.id/api/connections/facebook/callback

Callback HTTPS sudah berhasil dan mengembalikan HTTP 302.
Jadi infrastructure, DNS, Cloudflare, SSL, nginx, dan callback route sudah dapat diakses.

Sekarang cari dan verifikasi dari repository:

1. File .env yang benar-benar digunakan oleh service.
2. Nama variable yang dibutuhkan:
   META_APP_ID
   META_APP_SECRET
   META_REDIRECT_URI
   WEB_BASE_URL

3. Jangan tampilkan nilai META_APP_SECRET.
4. Jangan tampilkan access token atau credential sensitif.
5. Tampilkan hanya:
   configured / missing / placeholder.

6. Cari dari source code apakah WEB_BASE_URL digunakan untuk:
   - redirect setelah OAuth
   - frontend URL
   - /accounts
   - cookie
   - CORS
   - callback flow

7. Tentukan URL FRONTEND yang sebenarnya berdasarkan repository.
   Jangan menebak.

8. Pastikan:
   META_REDIRECT_URI =
   https://api.contentpilot.biz.id/api/connections/facebook/callback

9. Pastikan META_REDIRECT_URI tidak ditimpa oleh fallback/default lain.

10. Cari endpoint yang digunakan frontend untuk memulai Facebook OAuth.

11. Tampilkan URL entry point OAuth tersebut.

12. Periksa apakah konfigurasi saat ini menyebabkan:
   oauthStatus=needs_configuration
   atau
   connect=invalid

13. Jangan meminta saya memasukkan secret ke chat.
   Jika META_APP_ID atau META_APP_SECRET memang kosong, cukup laporkan bahwa variable tersebut missing.

14. Jangan melakukan perubahan file.

Output:

=== OAUTH CONFIG AUDIT ===

ENV FILE:
<path>

META_APP_ID:
configured / missing / placeholder

META_APP_SECRET:
configured / missing / placeholder

META_REDIRECT_URI:
<value jika aman>

WEB_BASE_URL:
<value>

FRONTEND URL:
<URL yang ditemukan dari repository>

OAUTH ENTRY POINT:
<endpoint>

CALLBACK:
<endpoint>

CONFIGURATION STATUS:
READY / NEEDS CONFIGURATION

EXACT ACTION REQUIRED:
<jelaskan hanya tindakan yang perlu dilakukan>

STOP setelah audit.

```

# 
```
Prompt: Audit Facebook OAuth Flow

Lakukan audit khusus terhadap Facebook OAuth flow di repository /root/content-pilot.

JANGAN langsung melakukan refactor besar dan JANGAN mengubah Cloudflare/nginx.

Kondisi yang sudah diverifikasi:

- Domain: https://api.contentpilot.biz.id
- HTTPS berhasil melalui Cloudflare
- /api/connections/facebook/callback dapat diakses
- Callback mengembalikan HTTP 302 ke:
  https://api.contentpilot.biz.id/accounts?connect=invalid
- Ini terjadi ketika callback dipanggil langsung tanpa parameter OAuth.

Sekarang cari dari source code:

1. Route yang memulai Facebook OAuth.
2. URL endpoint yang harus dibuka user untuk memulai OAuth.
3. Route callback Facebook.
4. Parameter query yang diharapkan callback:
   - code
   - state
   - error
   - error_reason
   - error_description
5. Bagaimana state dibuat dan divalidasi.
6. Bagaimana redirect_uri dibuat.
7. Pastikan redirect_uri yang digunakan authorization request SAMA PERSIS dengan:

https://api.contentpilot.biz.id/api/connections/facebook/callback

8. Periksa META_REDIRECT_URI dari .env dan seluruh fallback/default yang mungkin menimpa nilainya.
9. Periksa META_APP_ID dan META_APP_SECRET hanya untuk keberadaan/configuration; JANGAN tampilkan secret.
10. Periksa apakah frontend memanggil endpoint OAuth yang benar.
11. Cari kemungkinan route mismatch seperti:
    /api/connections/facebook/auth
    /api/auth/facebook
    /api/connections/facebook/connect
    atau route lain yang sebenarnya digunakan repository.
12. Periksa apakah authorization URL Facebook dibangun menggunakan graph version yang benar sesuai implementation saat ini.
13. Jangan mengarang endpoint atau permission.
14. Jika ada masalah, tunjukkan file dan line yang bermasalah.
15. Jalankan typecheck/test yang relevan setelah perubahan jika memang perlu.

PENTING:

Jangan menganggap callback URL rusak hanya karena membuka callback secara langsung menghasilkan connect=invalid.

Itu bisa merupakan behavior yang benar karena callback membutuhkan OAuth code/state.

Tujuan audit ini adalah menemukan ENTRY POINT OAuth yang benar dan memastikan seluruh flow:

START → Facebook → CALLBACK → TOKEN EXCHANGE → CONNECTION

berfungsi.

Jangan melakukan implementation besar.

Output:

OAUTH ENTRY POINT:
<endpoint sebenarnya>

CALLBACK:
<endpoint>

REDIRECT URI:
<nilai yang benar>

STATE:
<status>

TOKEN EXCHANGE:
<status>

FRONTEND FLOW:
<status>

META CONFIG:
<status tanpa membocorkan secret>

PROBLEMS FOUND:
<daftar>

FILES INVOLVED:
<daftar>

RECOMMENDED FIX:
<jelas>

Setelah audit selesai, STOP.


```

# Prompt — Audit & Perbaiki API + HTTPS Callback
```


Audit dan perbaiki masalah koneksi Content Pilot secara menyeluruh.

Kondisi saat ini:

Domain:
https://api.contentpilot.biz.id

DNS:
api.contentpilot.biz.id -> 104.207.89.204

Expected API:
127.0.0.1:4000

Expected Facebook OAuth callback:
https://api.contentpilot.biz.id/api/connections/facebook/callback

Hasil pengecekan:

curl http://127.0.0.1:4000/api/connections/facebook/callback
=> Failed to connect to 127.0.0.1 port 4000: Connection refused

curl https://api.contentpilot.biz.id/api/connections/facebook/callback
=> Failed to connect to api.contentpilot.biz.id port 443: Connection refused

JANGAN langsung menebak penyebab dan jangan hanya memberi instruksi manual.
LAKUKAN AUDIT LANGSUNG TERHADAP REPOSITORY DAN SERVER.

Periksa:

1. package.json dan scripts
2. struktur apps/api dan apps/web
3. entry point backend
4. port yang sebenarnya digunakan backend
5. environment variables
6. .env dan .env.example
7. apakah API memang seharusnya berjalan di port 4000
8. proses Node yang sedang berjalan
9. Docker/docker-compose jika digunakan
10. systemd/PM2 jika digunakan
11. firewall
12. apakah port 4000 sedang listen
13. reverse proxy yang tersedia (Nginx/Caddy/Traefik)
14. konfigurasi HTTPS
15. konfigurasi Cloudflare yang relevan
16. route /api/connections/facebook/callback
17. konfigurasi META_REDIRECT_URI
18. WEB_BASE_URL
19. NEXT_PUBLIC_API_BASE_URL
20. seluruh konfigurasi callback Facebook

Jalankan pemeriksaan yang diperlukan, misalnya:

ss -lntp
ps aux | grep -E 'node|npm|pnpm|next|tsx'
systemctl --type=service --state=running
docker ps
pm2 list
curl http://127.0.0.1:4000
curl http://127.0.0.1:4000/api/connections/facebook/callback
curl -I https://api.contentpilot.biz.id

Gunakan command yang memang sesuai dengan stack repository. Jangan mengubah sesuatu hanya untuk mencoba-coba.

TUJUAN AKHIR:

API harus berjalan pada port internal yang benar.

Domain:

https://api.contentpilot.biz.id

harus dapat diteruskan ke API melalui HTTPS.

Callback:

https://api.contentpilot.biz.id/api/connections/facebook/callback

harus dapat diakses dari internet.

Jika backend ternyata menggunakan port berbeda, jangan memaksakan port 4000. Tentukan port sebenarnya dari source code/configuration lalu sesuaikan reverse proxy dan environment secara konsisten.

Jika reverse proxy belum ada, buat konfigurasi yang paling sesuai dengan server yang sudah digunakan. Jangan memasang beberapa reverse proxy sekaligus.

Jika SSL belum tersedia, konfigurasi HTTPS dengan cara yang sesuai untuk domain Cloudflare dan server.

PERHATIAN:

- Jangan mengubah Facebook OAuth flow secara besar-besaran.
- Jangan membuat fake callback.
- Jangan membuat fake API response.
- Jangan menghapus source code existing.
- Jangan mengganti architecture project.
- Jangan melakukan refactor besar yang tidak diperlukan.
- Jangan commit secret.
- Jangan menampilkan nilai META_APP_SECRET atau credential.
- Jangan menganggap masalah selesai hanya karena konfigurasi file terlihat benar.

Setelah perbaikan:

1. pastikan backend benar-benar running
2. pastikan port backend listening
3. test endpoint lokal
4. test domain HTTPS
5. test callback endpoint
6. periksa response HTTP/status code
7. periksa log jika gagal
8. jalankan typecheck/lint/build yang relevan jika perubahan code dilakukan

Untuk callback endpoint, response 400/401/405 bisa tetap menunjukkan bahwa server dan route sudah reachable. Yang penting jangan mendapatkan connection refused/timeout.

Terakhir laporkan secara nyata:

SERVER API: RUNNING / NOT RUNNING
API PORT: <actual port>
LOCAL API: PASS / FAIL
HTTPS: PASS / FAIL
DOMAIN: PASS / FAIL
FACEBOOK CALLBACK: PASS / FAIL
REVERSE PROXY: <actual>
SSL: PASS / FAIL
ROOT CAUSE: <penyebab sebenarnya>
FILES CHANGED: <daftar>
TESTS: <hasil>

Jangan mengatakan PASS jika belum benar-benar dites.
```

# 
```

# Prompt — Audit & Find Facebook OAuth Callback URL

Jangan melakukan coding atau mengubah file apa pun.

Saya ingin kamu melakukan AUDIT repository `/root/content-pilot` untuk menemukan URL callback Facebook OAuth yang BENAR-BENAR digunakan oleh aplikasi ini.

Masalah:
Meta/Facebook meminta "Valid OAuth Redirect URI", tetapi kita belum tahu URL publik backend yang harus dimasukkan.

Dari source code yang sudah terlihat, terdapat route:

/api/connections/:platform/callback

dan untuk Facebook kemungkinan:

/api/connections/facebook/callback

Namun JANGAN berasumsi. Cari dan buktikan dari repository dan konfigurasi deployment.

## TUGAS

Audit repository secara menyeluruh untuk menentukan:

1. Backend berjalan di port berapa.
2. Frontend berjalan di port berapa.
3. Base URL aplikasi.
4. Public URL aplikasi.
5. API base URL.
6. Environment variable yang digunakan untuk callback.
7. Apakah ada META_REDIRECT_URI.
8. Apakah ada WEB_BASE_URL / API_BASE_URL / NEXT_PUBLIC_API_BASE_URL / APP_URL / PUBLIC_URL atau variable sejenis.
9. Apakah Docker Compose melakukan port mapping.
10. Apakah Nginx/Apache/Caddy/Traefik digunakan sebagai reverse proxy.
11. Domain/subdomain apa yang diarahkan ke backend.
12. Route callback Facebook yang sebenarnya.
13. Apakah callback menggunakan port 3000, 4000, atau port lain.
14. Apakah callback URL harus melalui frontend proxy atau langsung ke backend.
15. Apakah aplikasi sedang dijalankan melalui Docker, PM2, systemd, atau proses lain.

## PENTING

JANGAN melakukan grep besar terhadap:

- node_modules
- .next
- dist
- build
- coverage
- cache

Karena hasilnya akan dipenuhi source hasil compile/bundle.

Prioritaskan:

- .env
- .env.local
- .env.example
- docker-compose.yml
- docker-compose.yaml
- nginx configuration
- Caddy configuration
- package.json
- README.md
- apps/
- packages/
- source code
- API routes
- auth routes
- deployment configuration

Gunakan `git grep` atau pencarian yang mengecualikan generated files jika memungkinkan.

Cari secara khusus:

META_REDIRECT_URI
META_APP_ID
META_APP_SECRET
WEB_BASE_URL
API_BASE_URL
NEXT_PUBLIC_API_BASE_URL
APP_URL
PUBLIC_URL
BASE_URL
REDIRECT_URI
facebook
callback
connections/:platform/callback
connections/facebook/callback
proxy_pass
server_name
ports:
4000
3000
80
443

## JANGAN BERHENTI DI SOURCE CODE

Setelah menemukan route callback, telusuri bagaimana request dari internet sampai ke route tersebut.

Contoh:

Internet
→ Domain
→ Nginx / reverse proxy
→ Frontend/API
→ /api/connections/facebook/callback

Tentukan URL publik akhirnya.

## PERIKSA KONFIGURASI RUNTIME

Periksa juga:

- environment variable yang sedang digunakan
- Docker environment
- process manager
- listening ports
- reverse proxy
- domain configuration yang tersedia di server

Gunakan command yang aman/read-only seperti:

ss -lntp
docker ps
docker compose config
systemctl status nginx
nginx -T
pm2 list

Jika command tertentu tidak tersedia, lanjutkan dengan metode lain.

Jangan mengubah konfigurasi.

## VALIDASI

Jika memungkinkan, validasi route secara lokal menggunakan curl.

Contoh:

curl -I http://127.0.0.1:PORT/api/connections/facebook/callback

Jangan menganggap response 404 sebagai route tidak ada sebelum memeriksa method/route implementation.

Jika ada domain publik yang ditemukan, validasi juga URL publik tersebut secara aman.

## HASIL YANG WAJIB DIBERIKAN

Berikan laporan singkat dan jelas:

### 1. CALLBACK ROUTE

Contoh:

Route:
`/api/connections/facebook/callback`

### 2. BACKEND

Port:
`XXXX`

### 3. FRONTEND

Port:
`XXXX`

### 4. PUBLIC DOMAIN

Domain:
`https://example.com`

### 5. FINAL FACEBOOK CALLBACK URL

Tampilkan satu URL final yang harus dimasukkan ke Meta:

`https://example.com/api/connections/facebook/callback`

Jika belum dapat dipastikan, JANGAN mengarang.

Tulis:

`NOT DETERMINED`

lalu jelaskan informasi apa yang masih kurang.

### 6. META CONFIGURATION

Tentukan secara jelas:

Valid OAuth Redirect URIs:
`<URL FINAL>`

Jika ada lebih dari satu URL yang memang valid, jelaskan mana yang utama dan mana yang hanya untuk development.

### 7. EVIDENCE

Tampilkan file dan bagian source/configuration yang membuktikan URL tersebut.

Contoh:

`apps/api/src/routes/connections.ts`
→ callback route

`.env`
→ WEB_BASE_URL

`docker-compose.yml`
→ port mapping

`/etc/nginx/sites-enabled/...`
→ domain dan proxy_pass

### 8. CURRENT PROBLEM

Jelaskan kenapa sebelumnya kita tidak menemukan URL tersebut.

### 9. RECOMMENDATION

Berikan langkah berikutnya saja.

JANGAN mengubah file.
JANGAN commit.
JANGAN push Git.
JANGAN melakukan implementation.

STOP setelah audit selesai.

Tujuan akhir:

Saya ingin mendapatkan SATU URL callback Facebook yang benar dan bisa langsung saya masukkan ke Meta Developer Console → Facebook Login for Business → Settings → Valid OAuth Redirect URIs.

```


# Phase 4: Real Facebook Integration Test
```

Prompt 04 — Real Facebook Integration Test & Reels End-to-End

Lanjutkan Content Pilot dari kondisi repository saat ini.

Phase 0:
COMPLETE

Phase 1:
COMPLETE

Phase 1.5:
COMPLETE

Phase 2:
COMPLETE

Phase 3:
IMPLEMENTATION COMPLETE

Sekarang lakukan Phase 4 — REAL FACEBOOK INTEGRATION TEST.

TUJUAN UTAMA

Kita sekarang tidak ingin membuat architecture baru.

Kita ingin membuktikan bahwa implementation Facebook Provider yang sudah dibuat benar-benar dapat melakukan real publishing menggunakan Meta/Facebook API resmi.

Target utama:

1 video Reels
→ Content Pilot
→ Media
→ Storage
→ Post
→ Facebook Destination
→ PublishingJob
→ Queue
→ Worker
→ Facebook Provider
→ Meta Graph API
→ Facebook Page Reels

Hanya lakukan test terhadap Page Facebook yang memang dimiliki/dikelola dan sudah diotorisasi oleh credential yang digunakan.

Jangan melakukan spam.
Jangan membuat banyak test post.
Gunakan SATU video test.

==================================================
ATURAN PALING PENTING
==================================================

Sebelum melakukan apa pun:

1. Audit implementasi Phase 3.
2. Baca docs/research/facebook-api.md.
3. Baca docs/facebook-publishing.md jika tersedia.
4. Periksa FacebookProvider.
5. Periksa FacebookApiClient.
6. Periksa Reels module.
7. Periksa PlatformConnection.
8. Periksa Destination.
9. Periksa Storage.
10. Periksa PublishingJob.
11. Periksa PublishingAttempt.
12. Periksa Queue.
13. Periksa Worker.
14. Periksa Scheduler.
15. Jangan membuat architecture baru jika implementation existing sudah benar.
16. Jangan menghapus implementation yang sudah ada hanya untuk mengganti pendekatan.
17. Jangan membuat fake success.
18. Jangan menganggap published hanya karena API request berhasil dikirim.
19. Jangan menganggap real integration PASS jika credential tidak tersedia.
20. Jangan commit credential.

==================================================
1. META API VERIFICATION
==================================================

Sebelum real test, verifikasi kembali dokumentasi Meta yang relevan.

Gunakan sumber resmi Meta sebagai sumber utama.

Gunakan juga official Meta Postman collection jika membantu memverifikasi request flow.

Verifikasi aktual:

- current Graph API version
- Facebook Page publishing
- Page access token
- Page discovery
- Reels publishing
- upload initialization
- local video upload
- hosted video upload jika digunakan
- upload status
- publish/finalize
- caption/description
- title jika tersedia
- video_state
- required permissions
- token requirements
- Page requirements
- media requirements
- App Review requirements
- Business Verification requirements jika berlaku
- development mode limitations
- production limitations

Jangan memakai API version lama hanya karena contoh lama di internet.

Jika repository menggunakan API version tertentu:

bandingkan dengan version yang saat ini diverifikasi.

Jika perlu update version:

lakukan secara terkontrol.

Jangan mengubah API version tanpa alasan.

==================================================
2. REELS API FLOW
==================================================

Pastikan implementasi mengikuti flow resmi Meta yang telah diverifikasi.

Secara konsep:

STEP 1

Initialize Reel upload session.

Mendapatkan:

video_id

dan:

upload_url

atau informasi upload sesuai API version yang diverifikasi.

STEP 2

Upload video.

Jika source berupa local file:

gunakan upload flow resmi.

Jika source berupa hosted URL:

gunakan hosted upload flow resmi jika sesuai.

STEP 3

Jika API menyediakan upload/status endpoint:

cek status upload/processing.

STEP 4

Finalize/publish Reel.

Gunakan:

caption/description dari Post.

Jangan mengambil caption langsung dari source URL.

==================================================
3. CAPTION / DESCRIPTION
==================================================

Ini penting.

Pastikan:

Media.originalCaption

berbeda dari:

Post.caption

Contoh:

Original source caption:

Video bagus hari ini #travel #indonesia

User dapat mengubah menjadi:

Post.caption:

Liburan hari ini 🔥
#travel #indonesia

Facebook harus menerima:

Post.caption

bukan:

Media.originalCaption

Jika Meta endpoint menggunakan parameter bernama description:

map:

Post.caption

→ description

Jangan mengirim originalCaption jika user sudah mengubah caption.

==================================================
4. TITLE
==================================================

Jika Facebook Reels API yang diverifikasi mendukung title:

gunakan Post.title jika tersedia.

Jika title tidak diperlukan/tidak didukung:

jangan membuat fake parameter.

Dokumentasikan mapping yang digunakan.

==================================================
5. MEDIA VALIDATION
==================================================

Sebelum membuat real publishing job:

validasi video.

Gunakan requirement Meta yang benar-benar telah diverifikasi.

Periksa:

- MIME
- extension
- file size
- duration
- width
- height
- aspect ratio
- frame rate jika diwajibkan
- codec jika diwajibkan

Jangan menggunakan angka lama dari dokumentasi yang sudah deprecated.

Jika requirement tidak dapat diverifikasi:

NEEDS VERIFICATION

dan jangan memblokir/menyatakan valid berdasarkan asumsi.

==================================================
6. TEST VIDEO
==================================================

Gunakan satu video test yang memenuhi requirement Meta.

Jangan membuat banyak postingan.

Jika tidak ada video test yang sesuai:

jangan memalsukan hasil.

Laporkan:

TEST MEDIA NOT AVAILABLE

==================================================
7. STORAGE TEST
==================================================

Pastikan flow:

Media
→ Storage

berhasil.

Kemudian Facebook Provider dapat mengambil media dari Storage abstraction.

Storage tidak boleh hardcoded ke:

MinIO saja.

Pastikan architecture tetap kompatibel dengan:

- MinIO
- S3-compatible
- future Google Drive

==================================================
8. FACEBOOK CONNECTION
==================================================

Pastikan Phase 2 connection digunakan.

Jangan membuat OAuth system baru.

Periksa:

PlatformConnection

status:

connected

Destination:

Facebook Page

Pastikan Page benar-benar berasal dari connection user yang sedang login.

Jangan menerima Page ID arbitrary dari frontend.

==================================================
9. TOKEN SECURITY
==================================================

Pastikan Page Access Token:

- tidak dikirim ke frontend
- tidak disimpan di localStorage
- tidak masuk queue payload
- tidak masuk Redis payload
- tidak masuk log
- tidak masuk error message
- tidak masuk git
- tidak masuk screenshot/report

Provider mengambil credential secara aman dari backend.

==================================================
10. ENVIRONMENT
==================================================

Periksa:

.env

.env.example

META_APP_ID

META_APP_SECRET

META_REDIRECT_URI

META_GRAPH_API_VERSION

dan variable lain yang memang digunakan oleh implementation existing.

Jangan meminta user menaruh credential di source code.

Jika credential belum tersedia:

STOP real test.

Jangan fake.

Tampilkan:

REAL META INTEGRATION:
BLOCKED — CREDENTIALS NOT CONFIGURED

==================================================
11. META APP CONFIGURATION
==================================================

Jika credential tersedia, pastikan Meta App configuration sesuai kebutuhan.

Periksa:

- App ID
- App Secret
- OAuth redirect URI
- enabled products/login configuration
- permissions
- Page access
- development/production mode
- app review status jika diperlukan

Jangan mengubah Meta App configuration secara destructive.

Jika ada requirement yang tidak dapat dipenuhi:

dokumentasikan.

==================================================
12. CONNECTION TEST
==================================================

Sebelum publish:

test connection.

Pastikan Content Pilot dapat mengetahui:

- connected account
- Page ID
- Page name
- Page access status

Jika connection expired:

jangan lanjut publishing.

Tampilkan:

CONNECTION EXPIRED

Reconnect terlebih dahulu.

==================================================
13. DESTINATION TEST
==================================================

Pastikan destination:

- platform = facebook
- type = page
- externalId valid
- connection valid
- owned by current user

Jangan menggunakan destination yang tidak berasal dari connected account.

==================================================
14. PUBLISH NOW TEST
==================================================

Lakukan satu test:

Publish Now

Input:

Platform:
Facebook

Destination:
satu Page yang diotorisasi

Content:
Reels

Media:
satu test video

Caption:
gunakan caption test yang aman

Contoh:

Content Pilot integration test — please ignore.

Jangan menggunakan konten spam.

==================================================
15. END-TO-END FLOW
==================================================

Pastikan flow benar-benar:

User
→ Composer
→ Post
→ PublishingJob
→ Queue
→ Worker
→ FacebookProvider
→ Facebook API
→ upload
→ process
→ publish
→ external ID
→ database status

Jangan bypass Queue/Worker hanya untuk membuat test lebih mudah.

Jika architecture existing memang memiliki Publish Now shortcut:

pastikan tetap menggunakan PublishingJob dan provider pipeline.

==================================================
16. JOB STATUS
==================================================

Catat transition.

Contoh:

queued

→ processing

→ uploading

→ publishing

→ published

atau:

queued

→ processing

→ failed

Jika status provider berbeda:

map secara benar ke state machine existing.

==================================================
17. REAL SUCCESS CRITERIA
==================================================

REAL FACEBOOK TEST hanya dianggap PASS jika:

1. API credential valid.
2. Connection valid.
3. Destination valid.
4. Media valid.
5. Upload berhasil.
6. Meta menerima/finalize publishing.
7. Facebook memberikan external identifier atau response success yang dapat diverifikasi.
8. Database PublishingJob berubah menjadi published.
9. PublishingAttempt tersimpan.
10. User dapat melihat status published di Content Pilot.
11. Reel benar-benar dapat ditemukan pada Facebook Page yang ditargetkan, jika API/status flow memungkinkan verifikasi tersebut.

Jangan menyebut PASS hanya karena:

HTTP 200

atau:

success=true

jika proses sebenarnya belum selesai.

==================================================
18. PUBLISHING STATUS VERIFICATION
==================================================

Jika Meta menyediakan status endpoint:

gunakan untuk memverifikasi.

Contoh:

uploading
processing
published
error

Sesuaikan dengan API version yang diverifikasi.

Jika status asynchronous:

worker harus dapat melakukan polling/reconciliation sesuai architecture.

Jangan menganggap request finalize langsung berarti video sudah visible jika API menyatakan masih processing.

==================================================
19. IDEMPOTENCY TEST
==================================================

Setelah satu test berhasil:

pastikan retry/restart tidak membuat Reel kedua secara tidak sengaja.

Test secara aman.

Jangan sengaja membuat duplicate public Reel.

Gunakan unit/integration simulation untuk duplicate execution.

Jika perlu:

gunakan existing PublishingJob idempotency key.

==================================================
20. ERROR TEST
==================================================

Jangan sengaja membuat banyak failed public posts.

Gunakan mock/provider boundary untuk menguji:

- expired token
- permission denied
- timeout
- rate limit
- invalid media
- invalid destination

Pastikan mapping error benar.

==================================================
21. REAL TEST LIMIT
==================================================

Hanya:

1 REAL REEL

untuk real Meta integration.

Jangan membuat:

10 posts
100 posts
bulk posts

pada real integration test.

Bulk publishing akan diuji setelah single publishing terbukti stabil.

==================================================
22. QUEUE TEST
==================================================

Setelah satu real Publish Now berhasil:

uji architecture queue menggunakan test/mock bila diperlukan.

Pastikan queue dapat membuat:

PublishingJob

dan worker dapat memanggil:

FacebookProvider

Jangan membuat banyak real Facebook posts hanya untuk testing queue.

==================================================
23. SCHEDULER TEST
==================================================

Jangan membuat scheduled public test jika tidak diperlukan.

Gunakan test/mock untuk memastikan:

QueueItem
→ scheduledAt
→ PublishingJob
→ worker

berfungsi.

Real Facebook test cukup satu.

==================================================
24. UI VERIFICATION
==================================================

Periksa UI:

Accounts

Platforms

Media Library

Content Composer

Queue

History

Pastikan setelah real publishing:

History menunjukkan:

Platform:
Facebook

Destination:
Page

Content:
Reels

Status:
Published

External ID:
tersedia jika aman ditampilkan

Published At:
tersedia

Jangan menampilkan access token.

==================================================
25. ERROR UI
==================================================

Jika real test gagal:

UI harus memberikan error yang aman.

Contoh:

Facebook connection expired.

Permission required.

Facebook rejected the media.

Temporary Facebook API error.

Reels upload failed.

Jangan menampilkan:

raw access token

raw OAuth code

Meta App Secret

full internal stack trace

==================================================
26. LOGGING
==================================================

Log:

- publishing job ID
- provider
- destination ID
- external video ID jika aman
- status
- attempt
- duration
- sanitized error code

Jangan log:

- access token
- refresh token
- App Secret
- authorization code

==================================================
27. DOCUMENTATION UPDATE
==================================================

Update:

docs/research/facebook-api.md

docs/facebook-publishing.md

README.md

docs/ROADMAP.md

Dokumentasikan hasil REAL TEST.

Contoh:

REAL FACEBOOK REELS TEST

Date:
<actual date>

Result:
PASS / FAIL / BLOCKED

Provider:
Facebook

Destination:
Page test

Media:
Reels test video

API version:
<verified version>

Publishing:
PASS / FAIL

Status verification:
PASS / FAIL

Notes:
<actual result>

Jangan menulis PASS jika test sebenarnya skipped.

==================================================
28. SECURITY CHECK
==================================================

Sebelum commit:

git diff

Periksa:

.env

.env.example

logs

database dumps

screenshots

test fixtures

queue payload

Redis payload

Pastikan tidak ada:

META_APP_SECRET

Page Access Token

OAuth code

API key

password

credential

==================================================
29. TEST SUITE
==================================================

Jalankan:

pnpm lint

pnpm typecheck

pnpm test

pnpm build

Gunakan command repository jika berbeda.

Semua harus PASS kecuali real integration yang memang:

SKIPPED/BLOCKED

karena credential belum tersedia.

Jangan menyebut test suite PASS jika build/test gagal.

==================================================
30. REAL META RESULT
==================================================

Jika credential tersedia:

lakukan SATU real Reel test.

Jika credential tidak tersedia:

JANGAN berhenti setelah mengatakan "tidak bisa".

Lakukan semua local verification yang mungkin:

- provider unit tests
- API client tests
- media validation
- queue tests
- worker tests
- mocked publishing flow
- security checks
- build
- lint
- typecheck

Kemudian laporkan:

REAL META INTEGRATION:
BLOCKED — credentials not configured

==================================================
31. GIT REVIEW
==================================================

Setelah selesai:

git status

git diff --stat

git diff

Pastikan perubahan hanya:

- integration verification
- bug fixes
- documentation
- tests
- configuration example

Jangan commit credentials.

==================================================
32. COMMIT
==================================================

Jika ada perubahan:

git add .

git commit -m "test: verify facebook reels integration"

Jika hasil sebenarnya berupa bug fix yang lebih dominan, gunakan commit message yang jujur.

Jangan membuat commit kosong.

==================================================
33. PUSH LANGSUNG
==================================================

Setelah commit:

git push origin main

Jangan force push.

Jika tidak ada perubahan:

jangan membuat empty commit.

Jika push gagal:

jangan mengklaim sukses.

==================================================
34. REMOTE VERIFICATION
==================================================

Setelah push:

git status

git branch --show-current

git log -1 --oneline

git rev-parse HEAD

git ls-remote origin HEAD

Pastikan:

LOCAL HEAD == REMOTE HEAD

==================================================
35. FINAL REPORT
==================================================

Tampilkan secara jelas:

PHASE 4 STATUS:
COMPLETE / INCOMPLETE / BLOCKED

META API VERIFICATION:
PASS / FAIL / NEEDS VERIFICATION

META CREDENTIAL:
CONFIGURED / NOT CONFIGURED

FACEBOOK CONNECTION:
PASS / FAIL / BLOCKED

PAGE DESTINATION:
PASS / FAIL / BLOCKED

MEDIA VALIDATION:
PASS / FAIL

STORAGE:
PASS / FAIL

PUBLISHING JOB:
PASS / FAIL

QUEUE:
PASS / FAIL

WORKER:
PASS / FAIL

FACEBOOK PROVIDER:
PASS / FAIL

REELS UPLOAD:
PASS / FAIL / BLOCKED

REELS PUBLISH:
PASS / FAIL / BLOCKED

STATUS VERIFICATION:
PASS / FAIL / BLOCKED

DATABASE STATUS:
PASS / FAIL

UI STATUS:
PASS / FAIL

SECURITY:
PASS / FAIL

TEST:
PASS / FAIL

LINT:
PASS / FAIL

TYPECHECK:
PASS / FAIL

BUILD:
PASS / FAIL

REAL META INTEGRATION:
PASS / SKIPPED / BLOCKED / FAIL

REAL FACEBOOK REEL CREATED:
YES / NO

EXTERNAL REEL ID:
<id if safe>

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash or NONE>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED / NOT NEEDED

REMOTE VERIFIED:
YES / NO / NOT NEEDED

==================================================
FINAL STOP CONDITION
==================================================

Setelah Phase 4 selesai:

STOP.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Jangan membuat downloader.

Jangan membuat bulk Facebook publishing.

Jangan membuat recurring automation baru.

Jangan mulai Phase 5.

Tunggu instruksi berikutnya.

PRIORITAS UTAMA:

Kita ingin membuktikan SATU video Reels benar-benar dapat berjalan dari Content Pilot sampai Facebook Page secara nyata.

Tidak boleh ada fake success.
````



# Prompt 3 — Facebook Provider & Publishing Capability
```
Prompt 03 — Facebook Provider & Publishing Capability

Lanjutkan project Content Pilot dari repository dan kondisi terakhir yang sudah ada.

Phase 0:
COMPLETE

Phase 1:
COMPLETE

Phase 1.5:
COMPLETE

Phase 2:
COMPLETE

Phase 3:
SEKARANG DIKERJAKAN

Tujuan Phase 3 adalah mengimplementasikan Facebook sebagai provider publishing nyata menggunakan API resmi Meta/Facebook.

==================================================
ATURAN UTAMA
==================================================

Sebelum coding:

1. Audit repository saat ini.
2. Baca dokumentasi architecture existing.
3. Baca docs/research/facebook-api.md.
4. Periksa hasil implementasi Phase 2.
5. Periksa PlatformConnection.
6. Periksa Destination.
7. Periksa ProviderRegistry.
8. Periksa PublishingJob.
9. Periksa PublishingAttempt.
10. Periksa Queue.
11. Periksa Scheduler.
12. Periksa Media Library.
13. Periksa Storage Registry.
14. Periksa UI Accounts/Platforms.
15. Jangan membuat ulang fitur yang sudah ada.
16. Jangan merusak Phase 1, Phase 1.5, atau Phase 2.

Facebook harus tetap menjadi provider/module.

Core system TIDAK BOLEH menjadi Facebook-specific.

==================================================
TUJUAN PHASE 3
==================================================

Implementasikan kemampuan Facebook Page publishing yang nyata.

Prioritas:

1. Facebook Page text post
2. Facebook Page photo post
3. Facebook Page video
4. Facebook Page Reels
5. Publishing status
6. Error handling
7. Retry
8. Queue integration
9. Scheduler integration
10. Publishing history

Jangan langsung membuat semua fitur tambahan jika API atau permission belum terverifikasi.

Prioritaskan Reels karena itu merupakan salah satu tujuan utama Content Pilot.

==================================================
WAJIB RESEARCH META TERLEBIH DAHULU
==================================================

Sebelum menulis production code, lakukan research terhadap dokumentasi resmi Meta terbaru.

Gunakan sumber resmi Meta sebagai sumber utama.

Verifikasi secara aktual:

- current Graph API version
- Facebook Login / OAuth flow
- Page access token
- Page access token generation
- Page discovery
- Page permissions
- Page tasks/roles yang diperlukan
- Page publishing permissions
- text post endpoint
- photo publishing endpoint
- video publishing endpoint
- Reels publishing endpoint
- resumable upload
- upload host
- video requirements
- Reels requirements
- caption/description fields
- scheduled publishing
- publish status
- upload status
- error codes
- rate limits
- App Review
- Business Verification
- development mode restrictions
- production restrictions
- token expiration/reconnect

Jangan mengandalkan blog pihak ketiga sebagai sumber final.

Jika dokumentasi resmi Meta tidak dapat diakses:

JANGAN MENGARANG.

Tandai:

NEEDS VERIFICATION

dan dokumentasikan bagian tersebut.

==================================================
FACEBOOK PROVIDER ARCHITECTURE
==================================================

Gunakan ProviderRegistry existing.

Target:

Core
→ ProviderRegistry
→ FacebookProvider

FacebookProvider dapat memiliki module:

facebook/
├── auth/
├── pages/
├── posts/
├── photos/
├── videos/
├── reels/
├── api/
└── facebook.provider

Tetapi ikuti struktur repository existing jika struktur modular yang berbeda sudah digunakan.

Jangan membuat satu file raksasa.

Pisahkan:

API client

authentication

destination

media validation

upload

publishing

status

error mapping

==================================================
FACEBOOK API CLIENT
==================================================

Buat Facebook API client abstraction.

Contoh konsep:

FacebookApiClient

Kemampuan:

- request
- get
- post
- upload
- handle response
- normalize errors

Jangan membuat setiap service langsung melakukan fetch ke Graph API secara acak.

Semua komunikasi Facebook harus melewati provider/API client layer.

==================================================
TOKEN HANDLING
==================================================

Publishing menggunakan credential yang tersimpan pada PlatformConnection.

Jangan:

- mengirim token ke frontend
- menyimpan token di PublishingJob payload
- memasukkan token ke Redis payload
- memasukkan token ke log
- memasukkan token ke error message
- commit token

Provider harus mengambil credential secara aman dari backend.

Jika credential expired:

return connection_expired

bukan:

failed permanen tanpa informasi.

User harus diarahkan untuk reconnect.

==================================================
DESTINATION
==================================================

Facebook publishing hanya boleh dilakukan terhadap Destination yang valid dan terhubung.

Destination:

Facebook Page

Harus memiliki:

- platform
- externalId/pageId
- connection
- status
- metadata

Jangan menerima arbitrary Page ID dari frontend tanpa validasi ownership.

PublishingJob harus memastikan Destination memang milik authenticated user.

==================================================
CAPABILITY SYSTEM
==================================================

Facebook provider harus mendeklarasikan capability.

Contoh:

Facebook:

text_post
photo
video
reels

Jika suatu capability belum tersedia atau belum terverifikasi:

disabled

atau:

not_configured

Jangan menampilkan fitur sebagai aktif jika belum benar-benar diimplementasikan.

==================================================
POST MODEL
==================================================

Gunakan Post existing.

Pastikan Post dapat menyimpan:

- caption
- title jika diperlukan
- description jika diperlukan
- media
- destination
- publishing metadata

Original source caption tetap berbeda dari Post.caption.

Contoh:

Media.originalCaption:

Video asli dari sumber

Post.caption:

Caption final Facebook

User dapat mengubah caption sebelum publish.

==================================================
CAPTION
==================================================

Facebook provider harus menerima caption final dari Post.

Jangan mengambil caption langsung dari source URL saat publishing.

Flow:

Original source
→ originalCaption

User
→ edit caption

Post.caption
→ Facebook Provider

Facebook Provider
→ publish

==================================================
TEXT POST
==================================================

Implementasikan Facebook Page text publishing jika endpoint dan permission resmi sudah diverifikasi.

Flow:

Post
→ PublishingJob
→ FacebookProvider
→ Facebook Page
→ publish

Simpan external post ID.

Status:

queued
processing
publishing
published

Jika gagal:

failed

==================================================
PHOTO POST
==================================================

Implementasikan Facebook Page photo publishing jika API resmi sudah diverifikasi.

Media berasal dari Media/Storage layer.

Jangan membuat storage Facebook-specific.

Provider harus menerima media reference dan mendapatkan media dari Storage abstraction.

Jika API memerlukan public URL:

gunakan secure/presigned URL sesuai architecture.

Jangan membuat URL permanen yang membocorkan private media.

==================================================
VIDEO POST
==================================================

Implementasikan Facebook Page video publishing jika API resmi sudah diverifikasi.

Pastikan provider mendukung:

- media validation
- upload
- upload progress jika architecture mendukung
- publish
- status
- error

Video besar harus menggunakan flow resmi yang sesuai.

Jangan mengirim video besar melalui request API biasa jika Meta mensyaratkan resumable upload.

==================================================
FACEBOOK REELS
==================================================

Ini adalah fitur prioritas Phase 3.

Implementasikan Facebook Page Reels publishing menggunakan API resmi Meta yang telah diverifikasi.

Jangan menggunakan browser automation.

Jangan menggunakan Facebook web scraping.

Jangan menggunakan username/password.

Jangan menggunakan endpoint unofficial.

==================================================
REELS FLOW
==================================================

Setelah dokumentasi resmi diverifikasi, implementasikan flow sesuai API saat ini.

Architecture harus mendukung konsep:

1. initialize upload
2. obtain upload information
3. upload media
4. finalize/publish
5. monitor status jika diperlukan

Jika API resmi saat ini memiliki flow yang berbeda:

ikuti flow resmi tersebut.

Jangan mengikuti prompt lama jika dokumentasi terbaru Meta berbeda.

==================================================
REELS MEDIA VALIDATION
==================================================

Validasi media sebelum membuat publishing job berjalan.

Minimal architecture harus dapat memeriksa:

- MIME type
- file size
- duration
- width
- height
- aspect ratio

Jangan hardcode requirement yang belum diverifikasi.

Gunakan requirement resmi Meta.

Jika Meta memiliki requirement berbeda antara upload dan publishing:

ikuti requirement aktual.

Error harus jelas:

unsupported_media

invalid_duration

invalid_aspect_ratio

invalid_format

file_too_large

atau error code yang sesuai.

==================================================
UPLOAD STORAGE
==================================================

Media source:

Media Library
→ Storage Provider
→ Facebook upload

Storage provider dapat:

- MinIO
- S3-compatible
- Google Drive architecture
- Local

Jangan membuat Facebook provider bergantung langsung pada MinIO.

Provider hanya menggunakan Storage abstraction.

==================================================
PUBLIC MEDIA URL
==================================================

Jika Facebook API membutuhkan public URL:

buat mechanism yang aman.

Pertimbangkan:

presigned URL

temporary URL

upload endpoint

atau mekanisme resmi Meta yang sesuai.

Jangan membuat seluruh Media Library public.

Jangan expose private files secara permanen.

==================================================
PUBLISHING JOB
==================================================

Gunakan PublishingJob existing.

Jangan membuat Facebook-specific publishing job table jika tidak diperlukan.

Contoh:

PublishingJob:

provider:
facebook

destination:
page A

post:
post A

contentType:
reels

==================================================
JOB STATE MACHINE
==================================================

Gunakan state existing.

Minimal:

queued
processing
uploading
publishing
published
failed
retrying
cancelled

Gunakan status yang sudah ada jika repository memiliki enum/state machine.

Jangan membuat dua state machine yang berbeda.

==================================================
PUBLISHING ATTEMPT
==================================================

Setiap attempt harus dicatat.

Simpan:

- attempt number
- startedAt
- completedAt
- status
- provider
- externalId jika tersedia
- errorCode
- sanitized errorMessage

Jangan menyimpan token.

Jangan menyimpan secret.

==================================================
IDEMPOTENCY
==================================================

Publishing tidak boleh duplicate ketika:

- worker restart
- scheduler restart
- Redis restart
- API retry
- network timeout
- request timeout

Gunakan idempotency mechanism existing.

Jika Facebook API memberikan external upload/video ID:

simpan ID tersebut sehingga process dapat dilanjutkan/reconciled.

Jangan membuat duplicate Reel hanya karena worker tidak menerima response akibat timeout.

==================================================
RETRY
==================================================

Bedakan:

Temporary:

- timeout
- network failure
- transient API error
- rate limit
- temporary server error

→ retry

Permanent:

- invalid token
- permission denied
- invalid Page
- unsupported media
- invalid parameters
- policy rejection

→ failed

Jangan retry permanent error tanpa perubahan.

Gunakan exponential backoff jika worker architecture sudah mendukung.

==================================================
RATE LIMIT
==================================================

Jangan membuat angka rate limit berdasarkan asumsi.

Research Meta documentation.

Jika rate limit belum dapat diverifikasi:

NEEDS VERIFICATION

Namun architecture harus mendukung:

- provider rate limiter
- retry-after
- backoff
- concurrency limit

Facebook provider tidak boleh membanjiri API.

==================================================
QUEUE INTEGRATION
==================================================

Pastikan Queue Manager existing dapat menjalankan Facebook publishing.

Flow:

Queue
→ QueueItem
→ Schedule
→ PublishingJob
→ Worker
→ FacebookProvider
→ Facebook API

Jangan membuat scheduler khusus Facebook.

==================================================
SCHEDULER INTEGRATION
==================================================

Contoh:

Queue:

Video 001
Video 002
Video 003

Start:

01:00

Interval:

1 hour

Scheduler:

01:00 → Facebook Page A → Reel 001
02:00 → Facebook Page A → Reel 002
03:00 → Facebook Page A → Reel 003

Scheduler hanya menentukan waktu.

Facebook provider melakukan publishing.

==================================================
MULTI PAGE
==================================================

Satu Post dapat ditargetkan ke beberapa Page.

Contoh:

Video A

→ Page A
→ Page B
→ Page C

Buat publishing job terpisah.

Jika:

Page A = published

Page B = failed

Page C = published

History harus tetap menunjukkan status masing-masing.

==================================================
CROSSPOSTING
==================================================

Pastikan media tidak di-upload ulang ke storage hanya karena memiliki beberapa destination.

Media hanya satu.

PublishingJob berbeda.

Contoh:

Media 001

→ Job Facebook Page A
→ Job Facebook Page B
→ Job Facebook Page C

Provider dapat melakukan upload sesuai requirement Facebook.

Jangan menduplikasi Media record.

==================================================
PUBLISH NOW
==================================================

UI harus mendukung:

Publish Now

Flow:

User pilih:

Media
Caption
Facebook Page
Content Type

Klik:

Publish

→ create PublishingJob
→ queue
→ worker
→ Facebook

Jangan melakukan synchronous long-running upload dari frontend request.

==================================================
SCHEDULE
==================================================

UI harus mendukung:

Schedule

Contoh:

Tanggal:
22 August 2026

Waktu:
21:00

Timezone:
Asia/Jakarta

Post masuk scheduler.

Jangan membuat frontend timer.

Backend scheduler adalah source of truth.

==================================================
QUEUE MANAGER
==================================================

Pastikan user dapat melihat:

Video
Caption
Destination
Content Type
Scheduled Time
Status

Contoh:

Video 001
Facebook Page A
Reel
21:00
Scheduled

Video 002
Facebook Page A
Reel
22:00
Published

==================================================
CONTENT TYPE
==================================================

Gunakan generic content type.

Contoh:

text
photo
video
reels

Jangan:

facebook_reel

sebagai core content model.

Facebook provider dapat memetakan:

reels

→ Facebook Reels API

==================================================
UI CONTENT COMPOSER
==================================================

Update composer existing agar Facebook dapat dipilih.

Contoh:

Platform:

Facebook

Destination:

Page A

Content type:

Reels

Media:

Video.mp4

Caption:

[....................]

Schedule:

Publish Now

atau:

Schedule

==================================================
REELS VALIDATION UI
==================================================

Sebelum submit:

tampilkan validation.

Contoh:

✓ Video format supported
✓ Duration supported
✓ Aspect ratio supported
✓ File size supported

Jika gagal:

✗ Video duration tidak sesuai

Jangan menampilkan PASS jika backend belum memvalidasi.

==================================================
UPLOAD PROGRESS
==================================================

Jika provider/API mendukung progress:

tampilkan:

Preparing
Uploading
Publishing
Published

Jika progress percentage tidak tersedia:

jangan mengarang angka.

Gunakan status:

Uploading

bukan:

Uploading 73%

==================================================
PUBLISHING HISTORY
==================================================

History harus menampilkan:

- content
- platform
- destination
- content type
- scheduled time
- published time
- status
- error
- external ID jika aman

Contoh:

Video 001
Facebook
Page A
Reels
Published
22 Aug 2026 21:03

==================================================
ERROR UI
==================================================

Jika error:

Jangan menampilkan raw Graph API response yang dapat mengandung token atau informasi sensitif.

Tampilkan error yang aman.

Contoh:

Facebook connection expired.
Reconnect Facebook.

Permission required.
Reconnect or update Meta App permissions.

Unsupported video format.

Temporary Facebook API error.
Retrying...

==================================================
FACEBOOK CONNECTION
==================================================

Gunakan PlatformConnection dari Phase 2.

Jangan membuat OAuth system baru.

Jika token expired:

connection status:

expired

User:

Reconnect

Setelah reconnect:

refresh destination.

==================================================
DESTINATION REFRESH
==================================================

User dapat:

Refresh Pages

Provider mengambil Pages terbaru.

Jika Page sudah tidak tersedia:

mark inactive.

Jangan langsung menghapus historical data.

==================================================
APP CONFIGURATION
==================================================

Update:

.env.example

Jika diperlukan:

META_APP_ID
META_APP_SECRET
META_REDIRECT_URI
META_GRAPH_API_VERSION

Gunakan naming convention existing.

Jangan commit secret.

Jangan hardcode version jika architecture sudah memiliki centralized API version configuration.

Jika version harus ditentukan berdasarkan official Meta docs:

gunakan version yang telah diverifikasi.

==================================================
DOCUMENTATION
==================================================

Update:

README.md

docs/ARCHITECTURE.md

docs/PLATFORM_MODULES.md

docs/DATABASE.md

docs/ROADMAP.md

docs/research/facebook-api.md

Jika diperlukan:

docs/facebook-publishing.md

Dokumentasikan:

- Facebook provider
- Page publishing
- photo
- video
- Reels
- authentication
- Page token
- upload flow
- media requirements
- permissions
- status
- retry
- rate limit
- known limitations
- App Review
- development mode
- production requirements

==================================================
CAPABILITY MATRIX
==================================================

Update capability matrix.

Facebook:

Text Post
Photo
Video
Reels

Untuk masing-masing:

Implemented
Verified
Permission
Endpoint
Media Requirements
Scheduling
Status Tracking
Known Limitations

Jangan menandai Implemented jika code belum selesai.

==================================================
TESTING
==================================================

Buat unit/integration test untuk:

FacebookProvider

FacebookApiClient

Destination mapping

Page validation

Caption mapping

Media validation

Reels validation

PublishingJob creation

PublishingAttempt

Error mapping

Retry classification

Idempotency

Queue integration

Scheduler integration

Multi-page publishing

Connection expired

Permission denied

Unsupported media

Rate limit

Timeout

==================================================
MOCK BOUNDARY
==================================================

Untuk test:

Mock Facebook API pada boundary.

Jangan mock FacebookProvider business logic.

Test business logic sebenarnya.

Production code harus menggunakan API resmi.

==================================================
NO FAKE SUCCESS
==================================================

Jika META credentials belum tersedia:

Jangan membuat fake successful publishing.

Jika Meta App belum dikonfigurasi:

status:

NOT CONFIGURED

Jika permission belum tersedia:

status:

PERMISSION REQUIRED

Jika API behavior belum dapat diverifikasi:

status:

NEEDS VERIFICATION

Jangan mengubah menjadi published hanya agar test terlihat bagus.

==================================================
REAL INTEGRATION TEST
==================================================

Jika environment memiliki Meta credentials dan Page yang memang terhubung:

boleh lakukan real API verification terhadap Page yang memang dimiliki/diotorisasi.

Namun:

- jangan publish ke Page orang lain
- jangan spam
- jangan melakukan bulk test
- jangan membuat banyak postingan percobaan
- gunakan satu test content yang aman
- jangan commit credentials

Jika credentials tidak tersedia:

skip real integration test dengan alasan yang jelas.

Jangan menyebut integration test PASS jika sebenarnya skipped.

==================================================
SECURITY AUDIT
==================================================

Sebelum commit:

Periksa:

.env
.env.local
tokens
API keys
Meta App Secret
Page Access Token
OAuth credentials
logs
Redis payload
queue payload
database dumps

Pastikan:

- tidak ada secret committed
- token tidak masuk frontend
- token tidak masuk queue payload
- token tidak masuk logs
- token tidak masuk error response
- Page ID ownership tervalidasi
- user isolation tetap aktif

==================================================
BUILD & TEST
==================================================

Jalankan command existing.

Minimal:

pnpm lint

pnpm typecheck

pnpm test

pnpm build

Jika project memiliki command tambahan:

jalankan juga.

Jika ada error:

perbaiki.

Jangan menghapus test hanya agar PASS.

==================================================
UI VERIFICATION
==================================================

Periksa UI secara nyata.

Pastikan:

- Accounts tetap bekerja
- Platforms tetap bekerja
- Media Library tetap bekerja
- Queue tetap bekerja
- Scheduler tetap bekerja
- Content Composer dapat memilih Facebook
- Destination dapat dipilih
- Content type dapat dipilih
- Reels validation tersedia
- status publishing terlihat
- error state terlihat
- mobile responsive

Jangan membuat UI mock.

==================================================
DATABASE MIGRATION
==================================================

Jika schema perlu diubah:

buat migration.

Jangan menghapus data existing.

Pastikan:

Prisma schema valid.

Migration berhasil.

Application dapat start.

Worker dapat start.

==================================================
GIT REVIEW
==================================================

Sebelum commit:

git status

git diff --stat

git diff

Review semua perubahan.

Pastikan tidak ada:

.env

credentials

tokens

API keys

logs

temporary files

build artifacts yang tidak diperlukan

==================================================
COMMIT
==================================================

Jika seluruh Phase 3 selesai:

git add .

git commit -m "feat: add facebook publishing provider"

Jika perubahan sebenarnya lebih spesifik, gunakan commit message yang jujur.

Jangan membuat commit kosong.

==================================================
PUSH LANGSUNG
==================================================

Setelah commit:

git push origin main

Jangan force push.

Jika push gagal:

- jangan mengklaim sukses
- jangan menghapus commit
- jangan reset perubahan secara sembarangan
- tampilkan error sebenarnya

==================================================
REMOTE VERIFICATION
==================================================

Setelah push:

git status

git branch --show-current

git log -1 --oneline

git rev-parse HEAD

git ls-remote origin HEAD

Pastikan:

LOCAL HEAD == REMOTE HEAD

==================================================
FINAL REPORT
==================================================

Tampilkan:

PHASE 3 STATUS:
COMPLETE / INCOMPLETE

META API RESEARCH:
COMPLETE / NEEDS VERIFICATION

FACEBOOK PROVIDER:
PASS / FAIL

FACEBOOK CONNECTION:
PASS / FAIL

PAGE DESTINATION:
PASS / FAIL

TEXT POST:
PASS / FAIL / NOT IMPLEMENTED

PHOTO:
PASS / FAIL / NOT IMPLEMENTED

VIDEO:
PASS / FAIL / NOT IMPLEMENTED

REELS:
PASS / FAIL / NOT IMPLEMENTED

MEDIA VALIDATION:
PASS / FAIL

CAPTION:
PASS / FAIL

QUEUE:
PASS / FAIL

SCHEDULER:
PASS / FAIL

RETRY:
PASS / FAIL

IDEMPOTENCY:
PASS / FAIL

MULTI PAGE:
PASS / FAIL

PUBLISHING HISTORY:
PASS / FAIL

UI:
PASS / FAIL

SECURITY:
PASS / FAIL

TEST:
PASS / FAIL

LINT:
PASS / FAIL

TYPECHECK:
PASS / FAIL

BUILD:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

REAL META INTEGRATION:
PASS / SKIPPED / FAIL

Jika REAL META INTEGRATION = SKIPPED:
jelaskan alasannya.

==================================================
FINAL STOP CONDITION
==================================================

Setelah Phase 3 selesai dan push berhasil:

STOP.

Jangan mulai Phase 4.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Jangan implement downloader.

Jangan implement cross-platform downloader.

Jangan memperluas scope tanpa instruksi.

Tunggu instruksi berikutnya.

````



# 
```
Prompt 02 — Authentication & Platform Connection

Lanjutkan project Content Pilot dari kondisi repository saat ini.

Phase 0, Phase 1 Core Foundation, dan Phase 1.5 Automation Foundation sudah selesai dan sudah di-push ke repository.

Jangan mengulang pekerjaan yang sudah ada dan jangan merusak Queue, Scheduler, Media Library, Storage Registry, Provider Registry, PublishingJob, atau architecture yang sudah dibuat.

Sekarang kerjakan Phase 2 — Authentication & Platform Connection.

==================================================
TUJUAN PHASE 2
==================================================

Tujuan Phase 2 adalah membuat fondasi agar user dapat:

- register
- login
- logout
- menggunakan protected session
- menghubungkan akun platform
- melihat connection status
- mengambil destination/account yang tersedia
- reconnect
- disconnect
- mengelola beberapa platform connection
- mengelola beberapa destination

Arsitektur HARUS tetap platform-agnostic.

Facebook adalah provider pertama, tetapi core system tidak boleh menjadi Facebook-specific.

Target architecture:

User
→ PlatformConnection
→ Destination
→ PublishingJob

Contoh:

User A
→ Facebook Connection
→ Page A
→ Page B
→ Page C

User A
→ YouTube Connection
→ Channel A

==================================================
ATURAN PALING PENTING
==================================================

Sebelum coding:

1. Audit repository yang sekarang.
2. Baca README.md.
3. Baca docs/ARCHITECTURE.md.
4. Baca docs/DATABASE.md.
5. Baca docs/PLATFORM_MODULES.md.
6. Baca docs/ROADMAP.md.
7. Baca docs/QUEUE_SCHEDULER.md jika tersedia.
8. Baca docs/MEDIA_IMPORT.md jika tersedia.
9. Baca docs/STORAGE.md jika tersedia.
10. Periksa source code existing.
11. Gunakan abstraction yang sudah ada.
12. Jangan membuat duplicate architecture.
13. Jangan merusak Phase 1.
14. Jangan merusak Phase 1.5.

JANGAN melakukan:

- Facebook publishing
- Facebook Reels uploader
- YouTube publishing
- Instagram publishing
- TikTok publishing
- downloader nyata
- fake API integration
- fake OAuth success
- fake connected account
- browser automation menggunakan username/password
- penyimpanan token plaintext
- commit secret

Gunakan API/OAuth resmi platform.

==================================================
1. APPLICATION AUTHENTICATION
==================================================

Implementasikan authentication untuk aplikasi Content Pilot.

Minimal:

- register
- login
- logout
- session management
- protected API
- protected pages
- user ownership
- user isolation

Password:

- tidak boleh plaintext
- harus di-hash menggunakan metode aman
- jangan pernah dikembalikan melalui API

Session/cookie harus aman.

Gunakan architecture authentication yang sesuai dengan stack existing.

Jangan mengganti framework authentication tanpa alasan.

==================================================
2. USER ISOLATION
==================================================

Setiap data harus memiliki ownership yang jelas.

User A tidak boleh dapat:

- melihat media User B
- melihat post User B
- melihat queue User B
- melihat schedule User B
- melihat platform connection User B
- melihat destination User B
- mengubah publishing job User B
- menghapus data User B

Semua API harus melakukan authorization berdasarkan authenticated user.

Jangan hanya mengandalkan ID dari request.

==================================================
3. PLATFORM CONNECTION
==================================================

Buat atau sempurnakan generic PlatformConnection.

Konsep:

PlatformConnection

Minimal secara konsep:

- id
- userId
- platform
- status
- externalAccountId
- externalAccountName
- credential reference / encrypted credential
- expiresAt jika diperlukan
- metadata
- createdAt
- updatedAt

Sesuaikan dengan schema existing.

Jangan membuat model yang hanya cocok untuk Facebook.

==================================================
4. CONNECTION STATUS
==================================================

Minimal status:

connected
disconnected
expired
error
pending

Jika provider membutuhkan status tambahan, boleh ditambahkan.

Status harus mencerminkan kondisi nyata.

Jangan menampilkan connected jika credential belum benar-benar tersimpan/tervalidasi.

==================================================
5. DESTINATION
==================================================

Destination harus tetap generic.

Contoh:

Facebook Page
YouTube Channel
Instagram Account
TikTok Account

Semua direpresentasikan sebagai:

Destination

Jangan membuat core hanya menggunakan FacebookPage.

Destination minimal memiliki konsep:

- id
- platformConnectionId
- externalId
- name
- type
- status
- metadata
- createdAt
- updatedAt

Sesuaikan dengan database architecture existing.

==================================================
6. MULTI ACCOUNT
==================================================

Pastikan satu user dapat memiliki banyak platform connection.

Contoh:

User
→ Facebook Connection 1
→ Facebook Connection 2
→ YouTube Connection 1
→ Instagram Connection 1

Jangan membatasi satu connection per platform kecuali architecture memang memiliki alasan yang jelas.

Jangan membuat hardcoded single-account architecture.

==================================================
7. MULTI DESTINATION
==================================================

Satu platform connection dapat memiliki banyak destination jika provider mendukung.

Contoh:

Facebook Connection
→ Page A
→ Page B
→ Page C

YouTube Connection
→ Channel A
→ Channel B

Jangan membuat satu connection hanya untuk satu destination.

==================================================
8. PROVIDER AUTHENTICATION CONTRACT
==================================================

Authentication platform harus berada di provider layer.

Core tidak boleh mengetahui detail OAuth Facebook.

Buat abstraction yang dapat mendukung:

- authorization URL
- callback
- exchange authorization code
- validate connection
- refresh/reconnect jika tersedia
- disconnect
- retrieve destinations

Nama method boleh disesuaikan dengan architecture existing.

Target:

Core
→ Provider Registry
→ Facebook Provider
→ Facebook Auth

Kemudian nantinya:

Core
→ YouTube Provider
→ YouTube Auth

Core
→ Instagram Provider
→ Instagram Auth

Core
→ TikTok Provider
→ TikTok Auth

==================================================
9. FACEBOOK PROVIDER
==================================================

Facebook adalah provider pertama.

Pada Phase 2 implementasikan CONNECTION FOUNDATION saja.

Target flow:

User
→ Platforms
→ Connect Facebook
→ OAuth resmi Meta/Facebook
→ callback
→ validate state
→ exchange authorization code
→ validate access
→ retrieve available Pages/destinations
→ save connection
→ save destinations
→ show connected state

Jangan implement publishing.

==================================================
10. FACEBOOK API RESEARCH
==================================================

Sebelum implementation Facebook OAuth, lakukan research terhadap dokumentasi resmi Meta terbaru.

Verifikasi:

- OAuth flow
- authorization URL
- callback
- state parameter
- required permissions
- Page access/token model
- Page discovery
- token expiration
- token refresh/reconnect
- current Graph API version
- app configuration
- redirect URI requirements
- rate limits jika relevan
- App Review requirements
- permission requirements

Gunakan dokumentasi resmi Meta sebagai sumber utama.

Jangan mengarang permission.

Jangan mengarang endpoint.

Jangan menganggap token flow lama masih berlaku tanpa verifikasi.

Jika sesuatu belum dapat diverifikasi:

MARK AS NEEDS VERIFICATION

Jangan membuat fake implementation.

==================================================
11. FACEBOOK PAGE DISCOVERY
==================================================

Setelah OAuth connection berhasil:

Architecture harus siap mengambil Pages yang dapat diakses connection tersebut.

Contoh:

Facebook Connection

→ Page A
→ Page B
→ Page C

Simpan sebagai Destination.

Jangan hardcode Page ID.

Jangan meminta user memasukkan Page ID secara manual jika API resmi dapat menyediakan Page discovery.

Jika API/permission tidak memungkinkan:

dokumentasikan keterbatasannya.

==================================================
12. FACEBOOK CONNECTION MANAGEMENT
==================================================

User harus dapat:

- connect
- view connection
- refresh
- reconnect
- disconnect

Saat disconnect:

- jangan menghapus historical PublishingJob
- jangan menghapus historical records
- jangan menghapus media
- jangan menghapus post

Gunakan disconnected/deactivated state jika diperlukan.

==================================================
13. TOKEN SECURITY
==================================================

Access token dan refresh token jika ada harus diperlakukan sebagai secret.

Jangan:

- log token
- return token melalui API
- expose token ke frontend
- commit token
- menyimpan token plaintext jika secure encryption tersedia

Gunakan secure credential storage.

Application secret tetap menggunakan environment variables.

Jika encryption key dibutuhkan:

gunakan environment secret.

Jangan hardcode encryption key.

==================================================
14. ENVIRONMENT VARIABLES
==================================================

Tambahkan hanya environment variables yang memang diperlukan.

Contoh konsep:

META_APP_ID
META_APP_SECRET
META_REDIRECT_URI

Gunakan naming convention existing jika sudah tersedia.

Update:

.env.example

Jangan update .env dengan credential nyata.

Pastikan:

.env

.env.local

credentials

secrets

tidak masuk Git.

==================================================
15. OAUTH SECURITY
==================================================

Implementasikan:

- state validation
- CSRF protection
- redirect URI validation
- authorization code validation
- secure callback
- secure cookies
- session protection
- user ownership

Jangan menerima callback tanpa state validation.

Jangan menyimpan authorization code setelah tidak diperlukan.

==================================================
16. API
==================================================

Sesuaikan dengan API convention existing.

Minimal architecture harus menyediakan endpoint untuk:

GET /api/platforms

GET /api/connections

GET /api/connections/:id

POST /api/connections/:platform/connect

GET /api/connections/:platform/callback

POST /api/connections/:id/refresh

POST /api/connections/:id/disconnect

GET /api/destinations

Jika architecture existing menggunakan route berbeda:

ikuti convention existing.

Semua endpoint harus protected jika membutuhkan user authentication.

==================================================
17. API ERROR HANDLING
==================================================

Gunakan error response yang konsisten.

Contoh:

unauthorized
forbidden
not_found
invalid_request
provider_not_configured
oauth_failed
connection_expired
provider_error

Jangan mengembalikan raw secret atau raw provider credential.

Jangan membocorkan internal error kepada user.

Log detail internal secara aman.

==================================================
18. PROVIDER REGISTRY
==================================================

Gunakan Provider Registry existing.

Pastikan Facebook dapat didaftarkan sebagai provider tanpa membuat core Facebook-specific.

Provider dapat memberikan capability seperti:

- authentication
- destinations
- media
- publishing

Untuk Phase 2:

authentication = implemented

destinations = implemented jika API memungkinkan

publishing = NOT IMPLEMENTED

media importer = NOT IMPLEMENTED

Jangan menampilkan capability sebagai aktif jika belum diimplementasikan.

==================================================
19. UI — PLATFORMS / ACCOUNTS
==================================================

Buat atau update halaman:

Platforms / Accounts

Jangan membuat duplicate page jika sudah ada.

UI harus menampilkan:

Facebook

Status:

Not Connected

atau:

Connected

Jika connected:

- account name
- connection status
- number of destinations
- reconnect
- refresh
- disconnect

Jika provider belum dikonfigurasi:

Not configured

Jangan menampilkan Connected.

==================================================
20. FACEBOOK UI
==================================================

Contoh:

Facebook

Connect Facebook

Setelah connected:

Facebook
Connected

Account:
<account name>

Pages:
3 destinations

Actions:

Refresh
Reconnect
Disconnect

UI harus menggunakan data nyata dari API.

Jangan membuat fake connected state.

==================================================
21. DESTINATION UI
==================================================

Buat UI untuk melihat destination.

Contoh:

Facebook Pages

☑ Page A
☑ Page B
☑ Page C

Tampilkan:

- name
- status
- platform
- external ID jika memang diperlukan untuk admin/debug
- connection source

Jangan expose access token.

==================================================
22. RESPONSIVE UI
==================================================

UI harus:

- mobile friendly
- desktop friendly
- responsive
- clean
- konsisten dengan UI existing
- tidak terlalu banyak whitespace
- action utama mudah ditemukan

Ikuti docs/UI_DESIGN.md.

Jangan membuat design system baru jika repository sudah memiliki design system.

==================================================
23. DATABASE
==================================================

Update Prisma schema hanya jika diperlukan.

Pastikan schema mendukung:

User
→ PlatformConnection
→ Destination

dan tetap kompatibel dengan:

Media
Post
Queue
QueueItem
Schedule
PublishingJob
PublishingAttempt
Storage

Jangan menghapus data existing.

Gunakan migration yang aman.

==================================================
24. HISTORICAL DATA
==================================================

Disconnecting a platform tidak boleh merusak history.

Contoh:

Facebook connection disconnected.

Historical:

PublishingJob
PublishingAttempt
Post
Media

tetap ada.

Destination lama dapat menjadi:

inactive

atau:

disconnected

sesuai architecture.

==================================================
25. USER OWNERSHIP DATABASE
==================================================

Pastikan relation dan query service tidak memungkinkan cross-user access.

Contoh:

getConnection(userId, connectionId)

harus memastikan:

connection.userId === userId

Begitu juga:

getDestination(userId, destinationId)

getQueue(userId, queueId)

getPost(userId, postId)

getMedia(userId, mediaId)

Gunakan service/repository pattern yang konsisten.

==================================================
26. TESTING — AUTH
==================================================

Tambahkan test:

- register
- duplicate email
- login success
- login failure
- logout
- protected route
- unauthenticated access
- password hashing
- user isolation

==================================================
27. TESTING — CONNECTION
==================================================

Tambahkan test:

- create connection
- retrieve connection
- connection ownership
- destination ownership
- disconnect
- refresh state
- expired state
- invalid provider
- provider not configured

==================================================
28. TESTING — OAUTH
==================================================

Test:

- state generation
- state validation
- invalid state
- missing callback code
- provider error callback
- invalid callback
- authorization failure

Jika external Meta API tidak dapat dipanggil dalam unit test:

gunakan mocked provider boundary.

Jangan mock seluruh business logic.

==================================================
29. TESTING — FACEBOOK
==================================================

Test provider contract:

- authorization URL generation
- callback parsing
- token exchange boundary
- destination mapping
- connection state mapping

Jangan membuat fake API response yang membuat production integration terlihat sudah selesai.

Test mock hanya untuk unit/integration testing.

==================================================
30. WORKER COMPATIBILITY
==================================================

Pastikan perubahan authentication/platform connection tidak merusak worker.

Worker tetap dapat:

- membaca PublishingJob
- membaca Destination
- mengetahui provider
- memanggil provider layer

Namun publishing Facebook belum diimplementasikan.

Jika PublishingJob diarahkan ke provider yang belum memiliki publishing capability:

status harus:

not_configured

atau:

unsupported

bukan published.

==================================================
31. QUEUE COMPATIBILITY
==================================================

Queue dan scheduler dari Phase 1.5 harus tetap bekerja.

Jangan mengubah behavior existing tanpa alasan.

Pastikan QueueItem tetap dapat mengacu pada Post/Destination.

Scheduler tetap menggunakan database sebagai source of truth.

==================================================
32. STORAGE COMPATIBILITY
==================================================

Jangan mencampurkan:

Platform credential storage

dengan:

Media storage.

Media tetap menggunakan Storage Registry:

- S3-compatible
- MinIO
- Google Drive architecture
- Local jika tersedia

Platform token/credential memiliki secure credential handling sendiri.

==================================================
33. MEDIA IMPORT COMPATIBILITY
==================================================

Jangan membuat downloader nyata pada Phase 2.

Media Import abstraction dari Phase 1.5 harus tetap kompatibel.

Nantinya:

Source URL
→ Importer
→ Media
→ original metadata
→ Post
→ Queue
→ Scheduler
→ PublishingJob
→ Destination

Phase 2 hanya connection/authentication.

==================================================
34. SECURITY AUDIT
==================================================

Sebelum commit:

Periksa:

.env
.env.local
.env.example
credentials
tokens
API keys
passwords
private keys
OAuth secrets

Pastikan:

- tidak ada secret committed
- token tidak masuk logs
- token tidak masuk queue payload
- token tidak masuk frontend
- OAuth state aman
- protected API benar
- user isolation benar

Jika menemukan security issue:

perbaiki sebelum commit.

==================================================
35. DOCUMENTATION
==================================================

Update:

README.md

docs/ARCHITECTURE.md

docs/DATABASE.md

docs/PLATFORM_MODULES.md

docs/ROADMAP.md

Tambahkan jika benar-benar diperlukan:

docs/AUTHENTICATION.md

Jangan membuat duplicate documentation.

Dokumentasikan:

- application authentication
- session model
- user isolation
- PlatformConnection
- Destination
- provider authentication contract
- Facebook OAuth architecture
- Facebook Page discovery
- token security
- reconnect/disconnect
- current limitations
- required environment variables

==================================================
36. FACEBOOK RESEARCH DOCUMENT
==================================================

Jika belum ada:

docs/research/facebook-api.md

Buat/update dokumen ini.

Catat:

- API version yang diverifikasi
- OAuth flow
- permissions
- Page access model
- Page discovery
- token handling
- redirect URI
- App Review
- limitations
- verification status

Setiap item harus diberi status:

VERIFIED

atau:

NEEDS VERIFICATION

Jangan mengklaim sesuatu VERIFIED tanpa sumber resmi.

==================================================
37. ROADMAP UPDATE
==================================================

Update roadmap.

Status:

Phase 0:
COMPLETE

Phase 1:
COMPLETE

Phase 1.5:
COMPLETE

Phase 2:
Authentication & Platform Connection
CURRENT

Phase berikutnya:

Phase 3:
Facebook Provider / Facebook Publishing Capability

Tetapi jangan mulai Phase 3.

==================================================
38. BUILD & TEST
==================================================

Setelah implementation:

Jalankan:

pnpm lint

pnpm typecheck

pnpm test

pnpm build

Jika project menggunakan command berbeda:

gunakan command existing yang benar.

Jika ada error:

perbaiki.

Jangan menghapus test hanya agar PASS.

Jangan menutupi error.

==================================================
39. DATABASE MIGRATION CHECK
==================================================

Pastikan:

- migration berhasil
- schema valid
- existing data tidak hilang
- Prisma generate berhasil
- application dapat start
- worker dapat start

Jika database production belum tersedia:

gunakan local/test database untuk verification.

==================================================
40. API VERIFICATION
==================================================

Test:

- register
- login
- protected API
- connections list
- destinations list
- provider configuration state

Jika Meta credentials belum tersedia:

Jangan membuat fake connected account.

Tampilkan:

Facebook OAuth:
NEEDS CONFIGURATION

atau:

Facebook OAuth:
READY

berdasarkan kondisi environment sebenarnya.

==================================================
41. GIT REVIEW
==================================================

Setelah semua PASS:

git status

git diff --stat

git diff

Periksa seluruh perubahan.

Pastikan hanya perubahan yang berkaitan dengan Phase 2.

Jangan commit:

- .env
- access token
- refresh token
- OAuth secret
- API key
- credentials
- logs
- temporary files

==================================================
42. COMMIT
==================================================

Jika semua PASS:

git add .

git commit -m "feat: add authentication and platform connections"

Jika commit message perlu disesuaikan karena perubahan sebenarnya berbeda, gunakan message yang tetap jujur dan jelas.

Jangan membuat commit kosong.

==================================================
43. PUSH LANGSUNG
==================================================

Setelah commit:

git push origin main

Jangan force push.

Jika push gagal:

- jangan mengklaim berhasil
- jangan menghapus perubahan
- jangan reset commit secara sembarangan
- tampilkan error sebenarnya

==================================================
44. REMOTE VERIFICATION
==================================================

Setelah push berhasil:

git status

git branch --show-current

git log -1 --oneline

git rev-parse HEAD

git ls-remote origin HEAD

Pastikan:

local HEAD == remote HEAD

==================================================
45. FINAL REPORT
==================================================

Tampilkan:

PHASE 2 STATUS:
COMPLETE / INCOMPLETE

APPLICATION AUTH:
PASS / FAIL

USER ISOLATION:
PASS / FAIL

PLATFORM CONNECTION:
PASS / FAIL

FACEBOOK OAUTH:
COMPLETE / NEEDS CONFIGURATION / NEEDS VERIFICATION

FACEBOOK DESTINATION:
COMPLETE / NEEDS VERIFICATION

TOKEN SECURITY:
PASS / FAIL

DATABASE:
PASS / FAIL

API:
PASS / FAIL

WEB:
PASS / FAIL

WORKER:
PASS / FAIL

QUEUE COMPATIBILITY:
PASS / FAIL

STORAGE COMPATIBILITY:
PASS / FAIL

TEST:
PASS / FAIL

LINT:
PASS / FAIL

TYPECHECK:
PASS / FAIL

BUILD:
PASS / FAIL

SECURITY:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

NEXT RECOMMENDED STEP:
Phase 3 — Facebook Provider / Publishing Capability

==================================================
FINAL STOP CONDITION
==================================================

Setelah Phase 2 selesai dan push berhasil:

STOP.

Jangan mulai Phase 3.

Jangan implement Facebook Reels publishing.

Jangan implement Facebook video publishing.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Jangan implement downloader.

Tunggu instruksi berikutnya.

````


# 
```

Prompt 02 — Automation Foundation, Queue Manager & Storage

Kita lanjut dari Phase 1 yang sudah selesai dan sudah di-push ke repository.

Repository:
zenolambee/content-pilot

Branch:
main

Phase 1 sebelumnya sudah berhasil:

- TypeScript full-stack
- monorepo
- Next.js
- Fastify
- PostgreSQL
- Prisma
- Redis
- BullMQ
- MinIO
- Core foundation
- Provider abstraction
- Storage abstraction
- PublishingJob
- PublishingAttempt
- Scheduler foundation
- Worker foundation
- API foundation
- Web foundation
- tests
- lint
- typecheck
- build
- security check

Commit Phase 1:
d694dcf

Sekarang implementasikan PHASE 1.5 — AUTOMATION FOUNDATION.

TUJUAN PHASE 1.5

Siapkan fondasi Content Pilot agar dapat mengelola banyak video secara otomatis dan berurutan.

Target workflow:

Video / URL sumber
→ Media Import
→ Storage
→ Media Library
→ Post
→ Content Queue
→ Automatic Scheduler
→ Publishing Jobs
→ Worker
→ Platform Provider

Facebook publishing BELUM diimplementasikan pada phase ini.

Downloader platform-specific juga BELUM harus diimplementasikan secara penuh.

Yang dibuat sekarang adalah foundation agar downloader dan provider dapat ditambahkan tanpa membongkar core.

ATURAN UTAMA

Sebelum coding:

1. Baca README.md.
2. Baca docs/AUDIT.md jika tersedia.
3. Baca docs/ARCHITECTURE.md.
4. Baca docs/DATABASE.md.
5. Baca docs/PLATFORM_MODULES.md.
6. Baca docs/UI_DESIGN.md.
7. Baca docs/ROADMAP.md.
8. Audit hasil Phase 1 yang sekarang ada di repository.
9. Jangan merusak fitur Phase 1.
10. Jangan mengubah core architecture secara sembarangan.
11. Jangan implement Facebook OAuth.
12. Jangan implement Facebook publishing.
13. Jangan implement YouTube.
14. Jangan implement Instagram.
15. Jangan implement TikTok.
16. Jangan membuat fake downloader.
17. Jangan membuat fake publishing success.
18. Jangan menggunakan username/password automation untuk platform sosial.
19. Semua fitur baru harus modular.
20. Jangan membuat giant file.
21. Jangan menyimpan access token atau secret di queue payload.
22. Jangan commit secret.

KONSEP UTAMA CONTENT PILOT

Content Pilot bukan hanya uploader.

Content Pilot adalah:

CONTENT IMPORT
+
MEDIA LIBRARY
+
CONTENT QUEUE
+
AUTOMATIC SCHEDULER
+
PUBLISHING ENGINE

Contoh:

100 video dimasukkan ke queue.

Start:
01:00

Interval:
1 jam

Sistem otomatis membuat:

Video 001 → 01:00
Video 002 → 02:00
Video 003 → 03:00
Video 004 → 04:00
...
Video 100 → jadwal berikutnya

User tidak perlu menentukan waktu satu per satu.

1. CONTENT QUEUE

Buat konsep Content Queue.

Queue harus dapat berisi banyak Post.

Minimal:

Queue
QueueItem
Post
Media

QueueItem minimal:

- id
- queueId
- postId
- position
- status
- scheduledAt
- createdAt
- updatedAt

Status minimal:

pending
scheduled
processing
published
failed
cancelled
paused

Position harus memungkinkan reorder.

Contoh:

Queue:

1. Video A
2. Video B
3. Video C

User dapat mengubah:

1. Video C
2. Video A
3. Video B

Scheduler harus mengikuti urutan terbaru.

2. QUEUE MANAGER

Buat service:

QueueManager

Minimal kemampuan:

- createQueue
- addItem
- removeItem
- reorderItems
- pauseQueue
- resumeQueue
- cancelItem
- clearQueue
- getQueue
- getQueueStatus

Jangan membuat QueueManager Facebook-specific.

3. BULK IMPORT

Content Pilot harus siap menerima banyak media sekaligus.

Contoh:

10 video
20 video
100 video

Media dapat berasal dari:

- upload lokal
- URL
- downloader/importer
- storage lain

Phase ini cukup menyediakan generic import pipeline.

Jangan implement downloader Facebook/YouTube/TikTok yang sebenarnya.

4. MEDIA IMPORT

Buat abstraction:

MediaImporter

Konsep:

import(source)

→ MediaImportResult

MediaImportResult dapat berisi:

- media
- sourceUrl
- sourcePlatform
- originalTitle
- originalCaption
- hashtags
- thumbnail
- metadata

Semua field metadata harus optional karena setiap sumber menyediakan informasi berbeda.

5. SOURCE METADATA

Media harus dapat menyimpan metadata sumber.

Tambahkan jika belum ada:

- sourceUrl
- sourcePlatform
- originalTitle
- originalCaption
- originalDescription
- originalAuthor
- originalThumbnail
- originalPublishedAt
- sourceMetadata

Jangan menganggap semua platform menyediakan semua field.

Gunakan nullable/optional.

6. ORIGINAL CAPTION VS POST CAPTION

Ini sangat penting.

Jangan menyimpan caption sumber langsung sebagai caption final.

Gunakan:

originalCaption

dan:

post.caption

Contoh:

Downloader mendapatkan:

originalCaption:
Video bagus hari ini #travel #indonesia

Post dibuat:

caption:
Video bagus hari ini #travel #indonesia

Tetapi user tetap dapat mengubah post.caption.

Dengan demikian:

originalCaption = data sumber

post.caption = caption yang akan dipublish

Jangan kehilangan caption asli.

7. HASHTAGS

Simpan hashtag sumber jika tersedia.

Tetapi jangan menganggap hashtag selalu sama untuk semua platform.

Nantinya provider dapat melakukan transformasi.

Contoh:

Original:
#travel #indonesia #viral

Facebook:
#travel #indonesia

YouTube:
travel, indonesia

Phase 1.5 hanya menyiapkan data model/abstraction.

Jangan membuat platform-specific transformation sekarang.

8. STORAGE PROVIDER

Storage harus tetap abstraction.

Target:

StorageManager
→ S3-compatible
→ Google Drive
→ MinIO
→ Local

Core tidak boleh bergantung langsung pada Google Drive atau MinIO.

Buat interface generik.

Minimal:

- upload
- createUploadUrl
- createDownloadUrl
- getMetadata
- delete
- exists

Nama method boleh disesuaikan dengan architecture existing.

9. GOOGLE DRIVE

Google Drive harus didukung sebagai storage provider yang dapat ditambahkan.

Namun pada Phase 1.5:

JANGAN implement OAuth Google Drive production jika belum diperlukan.

Yang harus dibuat:

- provider contract
- configuration model
- storage provider registration architecture
- documentation

Jika implementasi Google Drive connector dilakukan sekarang, harus dibuat modular dan tidak mengikat core.

Jangan membuat credential Google Drive palsu.

10. S3 COMPATIBLE

Storage abstraction harus kompatibel dengan:

- AWS S3
- Cloudflare R2
- Backblaze B2
- Wasabi
- MinIO
- provider S3-compatible lainnya

Jangan membuat code khusus AWS saja.

11. MINIO

Tetap gunakan MinIO untuk local development.

Pastikan:

- upload
- object existence
- metadata
- download URL/presigned URL
- delete

dapat digunakan oleh storage abstraction.

12. STORAGE SELECTION

Desain agar user nantinya dapat memilih storage.

Contoh:

Settings
→ Storage

Storage provider:

S3
Google Drive
MinIO
Local

Provider yang belum dikonfigurasi harus:

Not configured

Jangan menampilkan seolah-olah connected.

13. AUTOMATIC SCHEDULER

Scheduler harus mendukung:

1. Manual schedule
2. Interval schedule
3. Queue-based automatic schedule

14. MANUAL SCHEDULE

User dapat menentukan:

Video 1 → 2026-08-22 01:00
Video 2 → 2026-08-22 03:00
Video 3 → 2026-08-22 06:00

Setiap QueueItem memiliki scheduledAt.

15. INTERVAL SCHEDULE

User dapat menentukan:

Start:
01:00

Interval:
1 hour

Queue:

Video 1 → 01:00
Video 2 → 02:00
Video 3 → 03:00
Video 4 → 04:00

Interval harus configurable.

Contoh:

15 minutes
30 minutes
1 hour
2 hours
6 hours
1 day

Jangan hardcode hanya 1 jam.

16. CUSTOM INTERVAL

Arsitektur harus mendukung interval custom dalam menit.

Contoh:

Interval:
90 minutes

Maka:

01:00
02:30
04:00
05:30

17. TIMEZONE

Scheduler harus timezone-aware.

Jangan menyimpan waktu schedule secara ambigu.

Gunakan UTC di backend/database jika architecture memilih demikian.

Timezone user disimpan secara eksplisit.

Contoh:

Asia/Jakarta

UI dapat menampilkan:

01:00 WIB

Backend tetap memiliki representasi waktu yang konsisten.

18. AUTO GENERATE SCHEDULE

Buat service:

ScheduleGenerator

Input:

- queue
- startAt
- interval
- timezone
- scheduling mode

Output:

scheduledAt untuk setiap QueueItem.

Contoh:

Queue memiliki 5 video.

Start:
01:00

Interval:
1 hour

Output:

01:00
02:00
03:00
04:00
05:00

Jangan membuat job publishing langsung ketika generate schedule.

Scheduler hanya menentukan jadwal.

19. RESCHEDULING

Jika queue berubah:

Video baru ditambahkan.
Video dihapus.
Video di-reorder.

Sistem harus dapat melakukan reschedule item yang masih pending.

Jangan mengubah job yang sudah published.

Jangan mengubah job yang sedang processing kecuali memang diperlukan.

20. PAUSE / RESUME

Queue harus dapat:

Pause

dan:

Resume.

Jika queue di-pause, item yang masih scheduled/pending tidak boleh diproses sampai queue di-resume.

21. CANCEL

Queue item dapat dibatalkan.

Status:

cancelled

Cancelled item tidak boleh dipublish.

Jika publishing job sudah running, cancellation harus mengikuti state machine yang aman.

22. QUEUE STATUS

Queue harus memiliki ringkasan:

Total
Pending
Scheduled
Processing
Published
Failed
Cancelled

Contoh:

Total: 100
Published: 20
Scheduled: 75
Failed: 3
Cancelled: 2

Jangan membuat status global yang menghilangkan status setiap item.

23. PUBLISHING JOB INTEGRATION

QueueItem ketika waktunya tiba akan menghasilkan/menjalankan PublishingJob sesuai architecture existing.

Flow:

QueueItem
→ scheduled
→ due
→ PublishingJob
→ queued
→ worker
→ provider

Provider nyata belum dibuat.

Phase ini hanya memastikan integration contract siap.

24. IDEMPOTENCY

Scheduler tidak boleh membuat duplicate publishing job jika scheduler dijalankan dua kali.

Gunakan idempotency key atau unique constraint.

Contoh konsep:

queueItemId + destinationId

atau identifier yang sesuai dengan database architecture.

Pastikan satu QueueItem tidak menghasilkan duplicate publish job karena worker/scheduler restart.

25. RETRY

Gunakan retry system dari Phase 1.

Temporary error:

retry

Permanent error:

failed

Retry harus tercatat sebagai PublishingAttempt.

26. MULTI DESTINATION

Queue architecture harus mendukung:

1 video
→ Facebook Page A
→ Facebook Page B
→ YouTube Channel A

Setiap destination menghasilkan publishing job terpisah.

Jangan membuat queue hanya untuk satu platform.

27. MULTI DESTINATION SCHEDULING

Desain agar nantinya user dapat memilih:

Schedule global

atau:

Schedule per destination.

Contoh:

Facebook Page A:
01:00

Facebook Page B:
01:30

YouTube:
02:00

Phase ini cukup menyediakan architecture/data model.

Jangan implement provider-specific publishing.

28. MEDIA LIBRARY

Buat foundation Media Library.

Minimal kemampuan:

- list media
- search
- filter
- metadata
- source
- status
- storage
- delete
- create post

Jangan membuat UI kompleks.

Buat API/service foundation terlebih dahulu.

29. CONTENT COMPOSER

Buat foundation agar Media dapat menjadi Post.

Flow:

Media
→ Create Post
→ Post

Post dapat memiliki:

- media
- caption
- title
- description
- hashtags
- metadata

Original metadata tetap disimpan terpisah.

30. CAPTION WORKFLOW

Content Composer harus dapat mendukung:

Use original caption

atau:

Custom caption

Contoh:

Original caption:
Video keren hari ini #travel

User memilih:

Use original caption

Maka:

Post.caption =
originalCaption

Jika user mengedit:

Post.caption =
custom text

Original caption tetap tidak berubah.

31. IMPORT URL

Buat API foundation untuk:

POST /api/media/import

Input:

sourceUrl

Optional:

sourcePlatform

Phase ini TIDAK boleh berpura-pura download jika provider belum ada.

Jika provider belum tersedia:

return status:

unsupported

atau:

provider_not_configured

Jangan mengembalikan fake media.

32. IMPORT PROVIDER REGISTRY

Buat:

MediaImporterRegistry

Konsep:

MediaImporterRegistry
→ FacebookImporter
→ YouTubeImporter
→ InstagramImporter
→ TikTokImporter

Namun Phase 1.5:

Registry boleh kosong.

Jangan membuat fake importer.

Core hanya mengetahui interface.

33. DOWNLOADER ARCHITECTURE

Downloader bukan bagian dari Facebook Publisher.

Pisahkan:

Media Importer

dari:

Platform Publisher.

Contoh:

Facebook Importer
→ mengambil media dari source

Facebook Publisher
→ mempublish media ke Facebook

Keduanya berbeda tanggung jawab.

34. SOURCE METADATA PIPELINE

Pipeline:

Source URL
→ Importer
→ Media
→ Original Metadata
→ Post Composer
→ Post
→ Queue

Jangan langsung:

Source URL
→ Facebook Publisher

35. BULK URL IMPORT

Architecture harus siap menerima:

1 URL
10 URL
100 URL

Contoh:

POST /api/media/import/bulk

Input:

sourceUrls[]

Tetapi jangan membuat downloader nyata.

Buat validation dan job model yang siap digunakan.

36. IMPORT JOB

Jika diperlukan, gunakan ImportJob.

Status:

pending
processing
completed
failed
cancelled

Setiap URL memiliki status sendiri.

Jangan membuat satu URL gagal menyebabkan semua import gagal.

37. IMPORT RETRY

Temporary import failure:

retry

Permanent:

failed

Simpan:

- attempt
- error
- next retry

Jangan retry URL invalid tanpa batas.

38. WEB UI

Buat UI foundation untuk:

Dashboard
Media Library
Queue
Scheduler

Prioritaskan Queue Manager.

39. QUEUE UI

Buat halaman:

Queue Manager

Tampilkan:

- video thumbnail
- filename/title
- caption preview
- destination
- scheduled time
- status
- position

Action:

- reorder
- pause
- resume
- cancel
- schedule

40. BULK SCHEDULING UI

UI harus memiliki:

Schedule Mode:

Manual

atau:

Interval

Jika Interval:

Start time
Interval

Contoh:

Start:
01:00

Every:
1 hour

Kemudian preview:

Video 1 → 01:00
Video 2 → 02:00
Video 3 → 03:00
Video 4 → 04:00

User dapat melihat hasil sebelum menyimpan.

41. STORAGE UI

Buat foundation settings:

Storage Provider

S3
Google Drive
MinIO
Local

Provider yang belum dikonfigurasi harus:

Not configured

42. DASHBOARD

Dashboard foundation dapat menampilkan:

Total Media
Queue
Scheduled
Published
Failed

Gunakan data nyata dari database.

Jangan membuat angka palsu.

43. RESPONSIVE UI

UI harus:

- mobile friendly
- desktop friendly
- responsive
- tidak terlalu banyak whitespace
- queue mudah digunakan dari mobile
- action utama mudah ditemukan

Ikuti docs/UI_DESIGN.md.

44. DATABASE

Update Prisma schema sesuai kebutuhan.

Entity yang mungkin diperlukan:

Queue
QueueItem
ImportJob
Media
Post
Schedule

Pertahankan entity Phase 1.

Pastikan migration aman.

Jangan menghapus data existing.

45. DATABASE CONSTRAINTS

Tambahkan constraint yang diperlukan untuk:

- unique idempotency
- queue position jika sesuai
- publishing job uniqueness
- platform connection relation
- destination relation

Hindari duplicate records akibat worker restart.

46. API

Tambahkan API foundation:

GET /api/media
POST /api/media/import
POST /api/media/import/bulk

GET /api/queues
POST /api/queues
GET /api/queues/:id
POST /api/queues/:id/items
POST /api/queues/:id/reorder
POST /api/queues/:id/pause
POST /api/queues/:id/resume
POST /api/queues/:id/schedule

Sesuaikan route convention yang sudah ada.

Jangan membuat endpoint publishing Facebook.

47. WORKER

Tambahkan worker jobs untuk:

- media import foundation
- schedule processing
- queue processing

Provider importer belum nyata.

Jika provider belum tersedia:

status harus jelas:

unsupported

atau:

not_configured

Jangan fake success.

48. SCHEDULER RECOVERY

Scheduler harus aman terhadap restart.

Pastikan:

- scheduled items tetap tersimpan di database
- Redis restart tidak menghilangkan source of truth
- scheduler dapat membaca kembali pending/scheduled items

Database adalah source of truth untuk schedule.

49. OBSERVABILITY

Log:

- queue created
- item added
- item reordered
- schedule generated
- schedule changed
- import requested
- import failed
- job created

Jangan log secret.

50. TESTING

Minimal test:

QueueManager:

- add
- reorder
- remove
- pause
- resume
- cancel

ScheduleGenerator:

- hourly
- custom interval
- timezone
- multiple items
- rescheduling

Idempotency:

- scheduler tidak duplicate job

Media:

- original metadata
- original caption
- custom caption

Storage:

- abstraction
- MinIO provider

Import:

- validation
- unsupported provider
- bulk validation

API:

- queue endpoints
- scheduling endpoint
- media import endpoint

51. ACCEPTANCE CRITERIA

Phase 1.5 COMPLETE jika:

[ ] Content Queue tersedia
[ ] Queue reorder tersedia
[ ] Queue pause/resume tersedia
[ ] Queue cancel tersedia
[ ] Bulk media foundation tersedia
[ ] Media Import abstraction tersedia
[ ] Original caption tersedia
[ ] Original metadata tersedia
[ ] Post caption terpisah dari original caption
[ ] Media Library foundation tersedia
[ ] Automatic interval scheduling tersedia
[ ] Manual scheduling tersedia
[ ] Custom interval tersedia
[ ] Timezone-aware scheduling tersedia
[ ] Schedule preview tersedia
[ ] Rescheduling tersedia
[ ] Idempotency tersedia
[ ] Storage abstraction tetap platform-independent
[ ] MinIO provider berjalan
[ ] S3-compatible architecture tersedia
[ ] Google Drive provider architecture tersedia
[ ] Tidak ada fake downloader
[ ] Tidak ada fake publisher
[ ] Worker berjalan
[ ] Scheduler recovery tersedia
[ ] API berjalan
[ ] Web berjalan
[ ] Tests PASS
[ ] Lint PASS
[ ] Typecheck PASS
[ ] Build PASS
[ ] No secrets committed
[ ] Documentation updated

52. DOCUMENTATION

Update:

README.md
docs/ARCHITECTURE.md
docs/DATABASE.md
docs/UI_DESIGN.md
docs/PLATFORM_MODULES.md
docs/ROADMAP.md

Tambahkan jika memang diperlukan:

docs/MEDIA_IMPORT.md
docs/QUEUE_SCHEDULER.md
docs/STORAGE.md

Jangan membuat duplicate documentation.

Dokumentasikan:

- Queue Manager
- Automatic Scheduling
- Media Import
- Original Caption
- Storage Provider
- Google Drive architecture
- S3-compatible architecture
- Import Provider
- Scheduler recovery
- Idempotency

53. ROADMAP UPDATE

Phase 1.5:

Automation Foundation

Setelah Phase 1.5:

Phase berikutnya:

Authentication & Platform Connection

Kemudian:

Facebook Provider

Kemudian:

Facebook Reels Publishing

Jangan menganggap downloader Facebook sudah tersedia.

54. SECURITY AUDIT

Sebelum commit periksa:

.env
.env.local
credentials
API keys
tokens
passwords
private keys

Pastikan tidak ada secret.

Queue payload tidak boleh berisi token.

Import URL harus divalidasi.

Jika URL fetching akan digunakan nantinya, dokumentasikan SSRF protection.

55. BUILD & TEST

Jalankan:

pnpm lint
pnpm typecheck
pnpm test
pnpm build

Jika ada error, perbaiki.

Jangan menutupi error.

Jangan menghapus test hanya supaya PASS.

56. GIT REVIEW

Setelah semuanya PASS:

git status
git diff --stat
git diff

Pastikan perubahan hanya untuk Phase 1.5.

Jangan commit:

- .env
- credentials
- API keys
- tokens
- logs
- temporary files
- build artifacts yang tidak diperlukan

57. COMMIT

Jika semua PASS:

git add .

git commit -m "feat: add automation queue and scheduling foundation"

Gunakan commit message tersebut atau message yang setara dan jujur terhadap perubahan sebenarnya.

58. PUSH LANGSUNG

Setelah commit:

git push origin main

Jangan force push.

Jika push gagal:

- jangan mengklaim berhasil
- jangan reset commit
- jangan menghapus perubahan
- tampilkan error sebenarnya

59. REMOTE VERIFICATION

Setelah push berhasil:

git status
git branch --show-current
git log -1 --oneline
git rev-parse HEAD
git ls-remote origin HEAD

Pastikan:

local HEAD == remote HEAD

60. FINAL REPORT

Tampilkan:

PHASE 1.5 STATUS:
COMPLETE / INCOMPLETE

QUEUE:
PASS / FAIL

SCHEDULER:
PASS / FAIL

MEDIA IMPORT:
PASS / FAIL

MEDIA LIBRARY:
PASS / FAIL

STORAGE:
PASS / FAIL

MINIO:
PASS / FAIL

GOOGLE DRIVE ARCHITECTURE:
PASS / FAIL

API:
PASS / FAIL

WEB:
PASS / FAIL

WORKER:
PASS / FAIL

TEST:
PASS / FAIL

LINT:
PASS / FAIL

TYPECHECK:
PASS / FAIL

BUILD:
PASS / FAIL

SECURITY:
PASS / FAIL

GIT STATUS:
CLEAN / NOT CLEAN

COMMIT:
<hash>

BRANCH:
<branch>

PUSH STATUS:
SUCCESS / FAILED

REMOTE VERIFIED:
YES / NO

NEXT RECOMMENDED STEP:
Phase 2 — Authentication & Platform Connection

FINAL STOP CONDITION

Setelah Phase 1.5 selesai dan push berhasil:

STOP.

Jangan mulai Phase 2.

Jangan implement Facebook OAuth.

Jangan implement Facebook publishing.

Jangan implement downloader Facebook.

Jangan implement YouTube.

Jangan implement Instagram.

Jangan implement TikTok.

Tunggu instruksi berikutnya.
````

# Prompt 02 — Phase 1 Core Foundation + Build + Push
```

# PROMPT 02 — PHASE 1 CORE FOUNDATION

Kita lanjut dari hasil Phase 0 yang SUDAH selesai dan SUDAH di-push.

Repository:
zenolambee/content-pilot

Branch utama:
main

Phase 0 sudah selesai:
- audit repository
- architecture
- database design
- provider architecture
- UI design
- Facebook API research
- roadmap

Sekarang MULAI IMPLEMENTATION PHASE 1.

==================================================
ATURAN PALING PENTING
==================================================

1. Baca terlebih dahulu:
   - README.md
   - docs/AUDIT.md
   - docs/ARCHITECTURE.md
   - docs/DATABASE.md
   - docs/PLATFORM_MODULES.md
   - docs/UI_DESIGN.md
   - docs/ROADMAP.md

2. Jangan mengulang Phase 0.

3. Jangan implement:
   - Facebook OAuth
   - Facebook publishing
   - YouTube
   - Instagram
   - TikTok
   - production publishing
   - fake provider
   - fake success state

4. Phase 1 hanya membangun CORE FOUNDATION.

5. Jangan membuat architecture baru yang bertentangan dengan
   docs/ARCHITECTURE.md.

6. Jika menemukan konflik antara dokumentasi, periksa semuanya,
   pilih desain yang paling konsisten, lalu update dokumentasi yang
   memang perlu. Jangan diam-diam mengubah architecture.

7. Jangan membuat giant file.

8. Gunakan modular architecture.

9. Core TIDAK BOLEH import provider Facebook atau provider platform lain.

10. Provider-specific implementation belum dibuat pada Phase 1.

11. Jangan memasukkan secret/API key/token ke repository.

12. Jangan membuat fake API integration.

13. Jangan membuat endpoint yang berpura-pura sudah melakukan publishing.

==================================================
TARGET STACK PHASE 1
==================================================

Gunakan stack yang sudah diputuskan di Phase 0:

- TypeScript strict
- pnpm
- Turborepo
- Next.js App Router
- Fastify
- PostgreSQL
- Prisma
- Redis
- BullMQ
- S3-compatible storage
- MinIO untuk development
- Zod
- Pino
- ESLint
- Prettier

Jika dependency belum ada, setup dengan versi stable yang kompatibel.

Jangan mengganti Fastify dengan NestJS.

==================================================
PHASE 1 GOAL
==================================================

Bangun fondasi teknis platform-agnostic:

1. Monorepo
2. Shared configuration
3. Database package
4. Core domain
5. Provider contract
6. Provider registry
7. Storage abstraction
8. Media management foundation
9. API skeleton
10. Web skeleton
11. Worker skeleton
12. Queue foundation
13. Scheduler foundation
14. Logging
15. Error handling
16. Health endpoints
17. Basic tests
18. Lint
19. Typecheck
20. Build
21. Documentation
22. Git commit
23. Git push
24. Remote verification

==================================================
1. MONOREPO
==================================================

Buat struktur:

content-pilot/

├── apps/
│   ├── web/
│   ├── api/
│   └── worker/
│
├── packages/
│   ├── core/
│   ├── db/
│   └── shared/
│
├── docs/
├── docker-compose.yml
├── package.json
├── pnpm-workspace.yaml
├── turbo.json
├── tsconfig.json
├── eslint.config.*
├── prettier.config.*
└── .gitignore

Sesuaikan nama file konfigurasi dengan tooling yang digunakan.

Jangan membuat struktur provider Facebook dulu jika belum dibutuhkan.

==================================================
2. TYPESCRIPT
==================================================

Gunakan TypeScript strict.

Pastikan:

- noImplicitAny
- strictNullChecks
- noImplicitThis
- strict
- typed boundaries

Hindari any kecuali benar-benar diperlukan dan diberi alasan.

Gunakan shared types secara benar.

==================================================
3. SHARED PACKAGE
==================================================

Buat:

packages/shared/

Minimal:

src/
├── config/
├── types/
├── enums/
├── schemas/
├── errors/
└── index.ts

Config loader menggunakan Zod.

Validasi environment variables.

Jangan membaca process.env secara acak di seluruh project.

Gunakan centralized configuration.

Minimal konfigurasi:

DATABASE_URL
REDIS_URL

S3_ENDPOINT
S3_BUCKET
S3_ACCESS_KEY
S3_SECRET_KEY

APP_SESSION_SECRET
TOKEN_ENCRYPTION_KEY

NODE_ENV

Jangan membutuhkan FACEBOOK_APP_ID/SECRET untuk Phase 1 karena
Facebook belum diimplementasikan.

Jika configuration architecture membutuhkan optional provider
variables, jangan membuat startup Phase 1 gagal hanya karena
provider belum aktif.

==================================================
4. DATABASE PACKAGE
==================================================

Buat:

packages/db/

Gunakan Prisma.

Database model harus mengikuti docs/DATABASE.md.

Minimal entity:

User
Platform
PlatformConnection
Destination
Media
Post
PostMedia jika diperlukan
PublishingJob
PublishingAttempt
Schedule
AuditLog
Notification

Jangan membuat model FacebookVideo,
YouTubeVideo,
InstagramVideo.

Gunakan model generik.

==================================================
5. USER
==================================================

User minimal harus memiliki:

- id
- email atau identifier yang sesuai architecture
- createdAt
- updatedAt

Jangan implement authentication penuh pada Phase 1.

Tetapi schema harus siap digunakan Phase 2.

==================================================
6. PLATFORM
==================================================

Platform adalah katalog platform.

Contoh seed:

facebook

Tetapi:

Jangan implement Facebook API.

Platform hanya menjadi database metadata/provider identifier.

Design agar nanti dapat ditambahkan:

youtube
instagram
tiktok

tanpa mengubah core schema.

==================================================
7. PLATFORM CONNECTION
==================================================

PlatformConnection harus mendukung:

User
→ multiple platform connections

Minimal konsep:

- id
- userId
- platformId
- external account identifier
- display name jika diperlukan
- encrypted credential/token fields
- status
- createdAt
- updatedAt

Token HARUS dianggap secret.

Phase 1 belum perlu OAuth.

Boleh menggunakan placeholder/null untuk token fields jika
schema membutuhkan.

Jangan membuat token palsu.

==================================================
8. DESTINATION
==================================================

Destination generik.

Contoh:

Facebook Page
YouTube Channel
Instagram Account

semuanya direpresentasikan sebagai Destination.

Minimal:

- id
- platformConnectionId
- externalId
- name
- type
- metadata jika diperlukan
- createdAt
- updatedAt

Jangan hardcode Facebook Page sebagai model khusus.

==================================================
9. MEDIA
==================================================

Media platform-independent.

Minimal metadata:

- id
- original filename
- mime type
- size bytes
- storage key
- duration
- width
- height
- thumbnail key jika diperlukan
- status
- createdAt
- updatedAt

Storage key harus aman.

Jangan menggunakan filename user sebagai path langsung.

Gunakan UUID/internal ID.

==================================================
10. POST
==================================================

Post merepresentasikan content yang akan dipublish.

Minimal:

- id
- owner/user
- caption/title/description jika architecture membutuhkannya
- status
- createdAt
- updatedAt

Post dapat menggunakan Media melalui relation.

==================================================
11. PUBLISHING JOB
==================================================

Ini sangat penting.

Satu Post dapat memiliki banyak PublishingJob.

Contoh:

Post 001

→ Facebook Page A = Job A
→ Facebook Page B = Job B
→ YouTube Channel A = Job C

PublishingJob minimal:

- id
- postId
- destinationId
- capability
- status
- idempotencyKey
- scheduledAt/runAt jika diperlukan
- createdAt
- updatedAt

Status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jangan membuat satu global publishing status sebagai pengganti
status per destination.

==================================================
12. PUBLISHING ATTEMPT
==================================================

Simpan histori attempt.

Minimal:

- id
- publishingJobId
- attemptNumber
- status
- errorClass
- errorCode
- errorMessage
- startedAt
- finishedAt
- nextRetryAt
- sanitized metadata

Jangan menyimpan:

Authorization header
access token
refresh token
API secret

==================================================
13. SCHEDULE
==================================================

Buat foundation untuk scheduling.

Phase 1 belum harus memiliki recurring scheduler lengkap.

Tetapi model/service harus siap untuk:

- immediate
- scheduled
- future recurring extension

Jangan implement platform-specific scheduler.

==================================================
14. AUDIT LOG
==================================================

Buat AuditLog append-only.

Minimal:

- actor/user
- action
- resource type
- resource id
- metadata
- createdAt

Metadata tidak boleh mengandung secret.

==================================================
15. NOTIFICATION
==================================================

Buat foundation Notification.

Contoh status:

- published
- failed
- retrying

Phase 1 belum membutuhkan push notification production.

==================================================
16. CORE PACKAGE
==================================================

Buat:

packages/core/

src/

├── domain/
├── provider/
├── services/
├── queue/
├── scheduler/
├── storage/
├── errors/
└── index.ts

Core harus PLATFORM-AGNOSTIC.

==================================================
17. PROVIDER CONTRACT
==================================================

Implementasikan kontrak provider berdasarkan
docs/ARCHITECTURE.md dan docs/PLATFORM_MODULES.md.

Jangan membuat contract yang terlalu Facebook-specific.

Minimal konsep:

PlatformProvider

- platform
- declaredCapabilities
- effectiveCapabilities()
- supports()
- validateContent()
- publish()
- checkProcessingStatus()

Untuk authentication, sediakan contract generic jika architecture
membutuhkannya:

- buildAuthorizationUrl()
- exchangeCodeForTokens()
- refreshTokens()
- listDestinations()

Tetapi jangan implement OAuth provider nyata.

Types harus generic.

==================================================
18. CAPABILITY
==================================================

Gunakan type-safe capability.

Contoh:

video
short_video
reels
photo
text_post
link_post
scheduling
analytics

Jangan menganggap semua provider memiliki semua capability.

ProviderRegistry dan UI nantinya harus dapat menggunakan capability.

==================================================
19. PROVIDER REGISTRY
==================================================

Implement:

ProviderRegistry

Minimal:

register(provider)
get(platform)
has(platform)
list()

Registry tidak boleh meng-import Facebook.

Provider didaftarkan dari bootstrap/application composition layer.

Pastikan dependency:

providers → core

bukan:

core → providers

Phase 1 boleh memiliki registry kosong.

Jangan membuat fake Facebook provider hanya agar registry terlihat
berisi.

==================================================
20. STORAGE ABSTRACTION
==================================================

Buat storage interface generik.

Contoh konsep:

StorageProvider

- createUploadUrl()
- getDownloadUrl()
- delete()
- head()

Implementasi development:

S3-compatible / MinIO.

Jangan mengikat core ke MinIO.

Core hanya mengetahui abstraction.

==================================================
21. MEDIA UPLOAD FOUNDATION
==================================================

Buat API foundation untuk upload media.

Alur:

Frontend
→ API create upload
→ storage presigned URL
→ browser upload langsung ke storage
→ API finalize
→ metadata/probe
→ Media record

Jangan upload file besar melalui API jika architecture memilih
direct-to-storage.

Validasi:

- MIME allowlist
- file size limit
- safe storage key

Jika metadata probing membutuhkan library tambahan, gunakan library
yang stabil dan modular.

Jangan implement platform-specific validation.

==================================================
22. API
==================================================

apps/api:

Fastify.

Minimal endpoint:

GET /health
GET /ready

Boleh menambahkan:

GET /api/health

jika architecture membutuhkan versioning.

Health harus membedakan:

process alive
dependency ready

Jangan membuat publishing endpoint Phase 1.

API harus memiliki:

- centralized error handler
- structured logging
- request correlation jika sesuai
- Zod validation
- graceful shutdown

==================================================
23. WEB
==================================================

apps/web:

Next.js App Router.

Buat skeleton dashboard sederhana.

Jangan membuat seluruh dashboard production.

Minimal:

- root layout
- basic navigation/shell
- health/status page atau dashboard placeholder
- reusable layout structure

Jangan membuat fake publishing UI.

Jangan menampilkan "Published successfully" jika belum ada backend
publishing.

UI harus menunjukkan bahwa publishing features belum tersedia.

==================================================
24. WORKER
==================================================

apps/worker:

BullMQ worker skeleton.

Buat queue foundation untuk:

publishing

scheduler

Tetapi:

Jangan memanggil Facebook.

Jangan memanggil YouTube.

Jangan publish apa pun.

Worker hanya harus memiliki struktur yang siap digunakan.

==================================================
25. QUEUE ARCHITECTURE
==================================================

Queue menerima identifier job, bukan seluruh object besar jika tidak
diperlukan.

Contoh:

{
  publishingJobId
}

Worker kemudian mengambil data dari database.

Jangan memasukkan token ke queue payload.

==================================================
26. SCHEDULER
==================================================

Buat scheduler foundation.

Harus siap menangani:

scheduled PublishingJob
runAt <= now

Tetapi Phase 1 belum harus memiliki production-grade scheduler.

Jika menggunakan delayed BullMQ, tetap desain agar recovery dari Redis
restart dapat dilakukan pada phase berikutnya.

Jangan membuat scheduler Facebook-specific.

==================================================
27. ERROR SYSTEM
==================================================

Buat error taxonomy generik.

Minimal:

ValidationError
NotFoundError
UnauthorizedError
ForbiddenError
ConflictError
TemporaryError
PermanentError

Provider-specific error mapping belum dibuat.

==================================================
28. LOGGING
==================================================

Gunakan Pino.

Structured logs.

Minimal context:

- requestId
- jobId jika ada
- component
- event

JANGAN log:

- access token
- refresh token
- API key
- Authorization header
- secret

==================================================
29. DOCKER COMPOSE
==================================================

Buat development infrastructure:

PostgreSQL
Redis
MinIO

Gunakan volume agar data development tidak hilang setiap restart.

Jangan memasukkan production secret.

Gunakan development credentials yang jelas sebagai LOCAL DEVELOPMENT
ONLY jika diperlukan.

Dokumentasikan cara menjalankan.

==================================================
30. DATABASE MIGRATION
==================================================

Buat initial Prisma migration.

Run:

pnpm prisma generate
pnpm prisma migrate dev

atau command yang sesuai dengan architecture.

Seed platform:

facebook

Jangan seed fake account,
fake token,
fake Page,
fake publishing job.

==================================================
31. TESTING
==================================================

Minimal test:

Core:
- ProviderRegistry
- capability handling
- error classification

DB:
- schema/migration validation

API:
- /health
- /ready

Storage:
- abstraction/unit tests jika memungkinkan

Jangan membuat fake publishing test yang menyatakan Facebook sukses.

==================================================
32. LINT / TYPECHECK / BUILD
==================================================

Sediakan root scripts:

pnpm lint
pnpm typecheck
pnpm build
pnpm test

Pastikan semuanya bekerja.

Jika menggunakan Turbo:

turbo run lint
turbo run typecheck
turbo run build
turbo run test

Sesuaikan scripts dengan package yang dibuat.

==================================================
33. IMPORT BOUNDARIES
==================================================

Wajib enforce:

packages/core TIDAK BOLEH import:
packages/providers/*

Karena provider belum dibuat pada Phase 1, tetap siapkan rule agar
architecture ini tidak rusak nanti.

Core boleh digunakan oleh provider.

==================================================
34. SECURITY CHECK
==================================================

Sebelum commit:

Cari:

- API keys
- tokens
- passwords
- private keys
- credentials
- .env files

Pastikan:

.env
.env.local
.env.*.local

tidak masuk Git.

Sediakan:

.env.example

tanpa secret nyata.

==================================================
35. DOCUMENTATION UPDATE
==================================================

Update documentation agar mencerminkan implementation sebenarnya.

README.md:
- cara install
- pnpm
- Docker
- database
- development
- commands
- architecture
- current phase
- limitations

ARCHITECTURE.md:
- implementation status
- monorepo structure
- core/provider boundary
- API
- worker
- storage

DATABASE.md:
- actual Prisma model
- relation
- migration status

ROADMAP.md:
- Phase 1 progress
- acceptance criteria

Jangan mengklaim fitur yang belum dibuat sebagai selesai.

==================================================
36. ACCEPTANCE CRITERIA PHASE 1
==================================================

Phase 1 hanya dianggap COMPLETE jika:

[ ] pnpm install berhasil
[ ] monorepo berhasil
[ ] TypeScript strict
[ ] shared package berhasil
[ ] Prisma schema berhasil
[ ] migration berhasil
[ ] database connection berhasil
[ ] platform seed berhasil
[ ] core domain berhasil
[ ] ProviderRegistry berhasil
[ ] provider boundary enforced
[ ] storage abstraction berhasil
[ ] MinIO development setup berhasil
[ ] API Fastify berjalan
[ ] /health berjalan
[ ] /ready berjalan
[ ] web Next.js berjalan
[ ] worker berjalan
[ ] BullMQ foundation berjalan
[ ] scheduler foundation tersedia
[ ] logging tersedia
[ ] error handling tersedia
[ ] tests tersedia
[ ] lint PASS
[ ] typecheck PASS
[ ] build PASS
[ ] no secrets committed
[ ] documentation updated

==================================================
37. JANGAN LANJUT PHASE 2
==================================================

Setelah acceptance criteria Phase 1 selesai:

STOP.

Jangan membuat:

- Facebook OAuth
- Facebook Page connection
- Facebook publishing
- YouTube OAuth
- Instagram provider
- TikTok provider
- production scheduler
- advanced analytics

Itu phase berikutnya.

==================================================
38. FINAL AUDIT SEBELUM COMMIT
==================================================

Sebelum commit lakukan:

git status

git diff --stat

git diff

Periksa file baru.

Pastikan tidak ada:

- secret
- credential
- API key
- token
- password
- .env production
- temporary files
- build artifacts yang tidak perlu

Pastikan hanya perubahan Phase 1 yang masuk.

==================================================
39. GIT COMMIT
==================================================

Jika semua acceptance criteria PASS:

git add .

Commit dengan:

feat: implement phase 1 core foundation

Jangan menggunakan commit message palsu.

==================================================
40. PUSH LANGSUNG
==================================================

Setelah commit:

git push origin main

Jangan force push.

Jika branch berbeda dari main, gunakan branch aktif yang memang digunakan
repository dan laporkan branch tersebut.

Jika push gagal:

JANGAN mengklaim berhasil.

Tampilkan error sebenarnya.

Jangan menghapus commit.

Jangan reset perubahan hanya untuk memaksa push.

==================================================
41. VERIFIKASI REMOTE
==================================================

Setelah push berhasil:

git status

git branch --show-current

git log -1 --oneline

git rev-parse HEAD

git ls-remote origin HEAD

Pastikan remote HEAD sesuai dengan commit lokal.

==================================================
42. FINAL REPORT
==================================================

Tampilkan ringkasan:

PHASE 1 STATUS: COMPLETE / INCOMPLETE

IMPLEMENTED:
- ...
- ...
- ...

TEST:
- lint: PASS/FAIL
- typecheck: PASS/FAIL
- build: PASS/FAIL
- test: PASS/FAIL

DATABASE:
- migration: PASS/FAIL
- seed: PASS/FAIL

SERVICES:
- API: PASS/FAIL
- Web: PASS/FAIL
- Worker: PASS/FAIL
- Redis: PASS/FAIL
- PostgreSQL: PASS/FAIL
- MinIO: PASS/FAIL

SECURITY:
- secrets checked
- .env protected

GIT STATUS: CLEAN / NOT CLEAN
COMMIT: <hash>
BRANCH: <branch>
PUSH STATUS: SUCCESS / FAILED
REMOTE VERIFIED: YES / NO

NEXT RECOMMENDED STEP:
Phase 2 — Authentication & Platform Connection

==================================================
FINAL RULE
==================================================

JANGAN lanjut Phase 2.

JANGAN implement Facebook.

JANGAN membuat fake success.

Kerjakan Phase 1 sampai benar-benar build/test dan push berhasil,
kemudian STOP.
````

# 
```
# Prompt 01 — Continue & Correct Repository Audit

Kita lanjutkan Prompt 01.

Saya sudah meninjau hasil sebelumnya dan ada masalah penting:

Repository saat ini masih berisi project lama berbasis Python/NiceGUI dan platform sosial yang berbeda. Project tersebut BUKAN arsitektur final untuk project baru Content Pilot yang sedang kita bangun.

Karena itu, jangan menganggap struktur lama sebagai arsitektur final.

Tujuan kita sekarang adalah menyelesaikan Phase 0 dengan benar sebelum coding fitur apa pun.

## PROJECT BARU

Nama project:

Content Pilot

Tujuan:

Membangun web platform untuk mengelola dan melakukan automatic content publishing ke berbagai platform sosial.

Platform pertama yang akan diimplementasikan adalah Facebook.

Namun arsitektur HARUS siap untuk:

* Facebook
* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang nantinya memiliki API publishing resmi yang sesuai

Facebook adalah provider pertama, bukan core system.

## ATURAN UTAMA

Jangan mulai implementation fitur publishing.

Jangan membuat Facebook uploader.

Jangan membuat OAuth Facebook terlebih dahulu.

Jangan membuat queue production terlebih dahulu.

Jangan membuat dashboard production terlebih dahulu.

Selesaikan discovery, architecture, documentation, dan roadmap terlebih dahulu.

## REPOSITORY AUDIT

Audit repository yang benar-benar sedang digunakan.

Periksa:

* seluruh root directory
* seluruh source code
* package/dependency
* konfigurasi
* database
* frontend
* backend
* test
* Docker
* deployment
* existing UI
* existing documentation

Pisahkan hasil menjadi:

1. Existing project lama
2. Existing code yang dapat dipertahankan
3. Existing code yang tidak relevan
4. Existing documentation yang perlu dipertahankan
5. Documentation yang perlu diperbarui
6. Komponen yang harus dibuat untuk Content Pilot
7. Risiko migrasi/refactor

Jangan mengklaim architecture baru sudah ada jika file tersebut belum benar-benar dibuat di repository.

## JANGAN MENGHAPUS PROJECT LAMA SECARA SEMBARANGAN

Sebelum menghapus atau mengganti source code lama:

* identifikasi terlebih dahulu
* jelaskan apa yang tidak relevan
* tentukan apakah project baru memang akan menggantikan project lama
* dokumentasikan keputusan

Jangan melakukan destructive migration pada Phase 0.

## TARGET TECH STACK

Gunakan TypeScript full-stack sebagai kandidat utama.

Kandidat architecture:

Frontend:
Next.js

Backend/API:
Fastify atau NestJS

Worker:
BullMQ

Queue:
Redis

Database:
PostgreSQL

Object storage:
S3-compatible storage

Namun ini masih architecture proposal.

Jangan langsung install atau implementasikan semuanya sebelum architecture final disetujui.

Bandingkan Fastify vs NestJS berdasarkan kebutuhan project ini dan pilih yang paling tepat.

Pertimbangkan:

* maintainability
* modular provider architecture
* queue/worker
* OAuth
* API integration
* validation
* testing
* scalability
* developer experience

## CORE ARCHITECTURE

Core tidak boleh bergantung pada Facebook.

Core harus menangani konsep generik:

* User
* Platform
* PlatformConnection
* Destination
* Media
* Post
* PublishingJob
* PublishingAttempt
* Schedule
* Queue
* Scheduler
* History
* AuditLog
* Notification
* Storage

Platform-specific implementation harus berada di provider/module masing-masing.

Target konsep:

Core
→ Provider Registry
→ Platform Provider
→ Platform-specific implementation

Contoh:

Core
→ Facebook Provider
→ YouTube Provider
→ Instagram Provider
→ TikTok Provider

## PROVIDER SYSTEM

Desain provider abstraction yang benar-benar extensible.

Jangan memaksakan semua provider memiliki fitur identik.

Gunakan capability-based architecture.

Contoh capability:

* video
* reels
* photo
* text_post
* link_post
* short_video
* scheduling
* analytics

Provider harus dapat melaporkan capability yang memang didukung.

Jangan membuat capability berdasarkan asumsi.

Capability harus dapat berasal dari:

* kemampuan API
* implementation provider
* permission
* destination type

## FACEBOOK

Facebook adalah provider pertama.

Tetapi sebelum implementation, lakukan research resmi.

Research:

* authentication
* OAuth
* Page connection
* Page discovery
* destination model
* video publishing
* Reels publishing
* photo publishing
* post publishing
* scheduling
* status checking
* error handling
* rate limits
* permissions
* app review requirements
* token expiration
* token refresh/reconnect

Jika fitur belum dapat diverifikasi:

MARK AS UNKNOWN / NEEDS VERIFICATION

Jangan mengarang endpoint atau permission.

## API RESEARCH

Gunakan dokumentasi resmi sebagai sumber utama.

Prioritas:

1. Meta/Facebook official documentation
2. YouTube official documentation
3. Instagram official documentation
4. TikTok official documentation

Untuk platform lain, research dilakukan setelah provider utama stabil.

Buat capability matrix.

Contoh kolom:

Platform
Authentication
Destination
Video
Reels
Photo
Text Post
Scheduling
Analytics
Required Permissions
Upload Flow
Known Limitations
Verification Status

Jangan menulis fitur sebagai AVAILABLE jika belum diverifikasi.

## MULTI ACCOUNT

Dari awal sistem harus mendukung:

User
→ multiple PlatformConnection
→ multiple Destination

Contoh:

User
→ Facebook Account
→ Page A
→ Page B
→ Page C

Dan nanti:

User
→ YouTube Account
→ Channel A
→ Channel B

Jangan membuat database yang hanya mendukung satu account atau satu Page.

## PUBLISHING JOB

Gunakan satu job per destination.

Contoh:

Video A

→ Facebook Page A = Job 001
→ Facebook Page B = Job 002
→ YouTube Channel A = Job 003

Setiap job memiliki status sendiri.

Contoh status:

draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying

Jika Facebook berhasil dan YouTube gagal:

Facebook = published
YouTube = failed

Bukan satu global job yang kehilangan detail platform.

## MEDIA ARCHITECTURE

Media harus platform-independent.

Video hanya disimpan sekali di media/storage layer.

Kemudian dapat digunakan oleh beberapa publishing job.

Jangan membuat:

FacebookVideo
YouTubeVideo
InstagramVideo

sebagai storage model utama.

Gunakan media generik lalu provider melakukan transformasi/validation sesuai capability platform.

## QUEUE

Queue harus platform-independent.

Core queue menerima PublishingJob.

Worker mengambil job.

Worker memanggil provider yang sesuai.

Contoh:

PublishingJob
→ provider = facebook
→ destination = Page A
→ publish()

Kemudian:

PublishingJob
→ provider = youtube
→ destination = Channel A
→ publish()

## RETRY

Bedakan temporary error dan permanent error.

Temporary:

* timeout
* network failure
* temporary API failure
* rate limit

Permanent:

* invalid token
* permission denied
* unsupported media
* invalid destination

Simpan:

* attempt count
* error code
* error message
* timestamp
* next retry
* provider response metadata jika aman

## SECURITY

Architecture harus memperhatikan:

* OAuth
* access token
* refresh token
* encryption
* secret management
* environment variables
* authorization
* user isolation
* file upload validation
* MIME validation
* file size limit
* path traversal
* SSRF
* rate limiting
* audit logs

Jangan commit secrets.

## UI DESIGN

Audit apakah repository saat ini sudah memiliki UI yang relevan untuk Content Pilot.

Jika UI lama tidak sesuai, jangan langsung menganggapnya sebagai UI final.

Dokumentasikan:

Current UI
→ reusable
→ needs redesign
→ obsolete

Untuk Content Pilot, target UI harus clean, modern, responsive, dan nyaman digunakan melalui desktop maupun mobile.

Konsep utama:

Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings

Tetapi jangan implementasikan semua halaman sekarang.

## UI DOCUMENTATION

Buat UI specification agar AI coding nantinya memiliki referensi yang konsisten.

Minimal dokumentasikan:

* layout
* navigation
* responsive behavior
* typography
* spacing
* buttons
* forms
* cards
* tables
* upload interface
* video preview
* publishing status
* queue
* scheduled posts
* account connection
* error state
* loading state
* empty state

Jangan membuat UI specification yang bertentangan dengan UI yang benar-benar dipilih untuk project.

## DOCUMENTATION

Buat documentation untuk project baru.

Gunakan struktur yang sederhana.

Minimal:

README.md

docs/ARCHITECTURE.md

docs/UI_DESIGN.md

docs/PLATFORM_MODULES.md

docs/DATABASE.md

docs/ROADMAP.md

docs/research/facebook-api.md

Jika dokumentasi dengan tujuan yang sama sudah ada, update file tersebut.

Jangan membuat duplicate documentation.

## DATABASE DESIGN

Buat ERD/logical model terlebih dahulu.

Minimal entity:

User
Platform
PlatformConnection
Destination
Media
Post
PublishingJob
PublishingAttempt
Schedule
AuditLog

Pastikan model mendukung:

1 user
→ many platform connections
→ many destinations
→ many media
→ many posts
→ many publishing jobs

Destination harus generik.

Facebook Page dan YouTube Channel harus dapat direpresentasikan sebagai destination tanpa mengubah core model.

## ROADMAP

Buat roadmap berdasarkan hasil audit aktual.

Phase 0:
Discovery, Audit, Research, Architecture, Documentation

Phase 1:
Core Foundation

Phase 2:
Authentication & Platform Connection

Phase 3:
Facebook Provider

Phase 4:
Facebook Publishing Capabilities

Phase 5:
Queue & Scheduler hardening

Phase 6:
YouTube Provider

Phase 7:
Instagram Provider

Phase 8:
TikTok Provider

Phase 9:
Advanced Automation

Jangan menganggap urutan ini final jika hasil audit menunjukkan urutan yang lebih baik.

Jelaskan alasan setiap phase.

## IMPORTANT

Pada tahap ini:

DO NOT implement publishing.

DO NOT implement Facebook OAuth.

DO NOT implement YouTube.

DO NOT implement TikTok.

DO NOT create fake API integrations.

DO NOT create fake success states.

DO NOT perform a massive refactor without reporting it.

DO NOT delete existing project files simply to make the repository look clean.

Fokus pada Phase 0.

## OUTPUT

Setelah selesai, berikan laporan:

Repository Status

Existing Stack

Existing Architecture

Existing UI

Existing Database

Existing Code

Reusable Components

Obsolete Components

Target Architecture

Provider Architecture

Database Model

UI Architecture

Facebook API Research

Platform Capability Matrix

Security Considerations

Migration Strategy

Roadmap

Recommended Phase 1

Risks

Open Questions

## REQUIRED FINAL STATUS

Tampilkan:

AUDIT STATUS: COMPLETE

ARCHITECTURE STATUS: READY / NEEDS REVISION

API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION

DOCUMENTATION STATUS: COMPLETE / INCOMPLETE

ROADMAP STATUS: READY

IMPLEMENTATION STATUS: NOT STARTED

NEXT RECOMMENDED STEP: ...

Jika architecture masih memiliki masalah, jangan menyatakan READY.

Tunjukkan masalahnya dan perbaiki dokumentasi terlebih dahulu.

STOP setelah Phase 0 selesai.

Jangan lanjut coding Phase 1 tanpa instruksi berikutnya.


````

# Prompt 01 — Initial Audit, Architecture & Roadmap
```

# Prompt 01 — Initial Audit, Architecture & Roadmap

## Tujuan

Kita akan membangun sebuah web platform untuk **automatic content publishing**, dengan **Facebook sebagai platform pertama**.

Namun, arsitektur project sejak awal HARUS dirancang agar nantinya dapat menambahkan platform lain seperti:

* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang memiliki API publishing yang sesuai

**Jangan membuat project menjadi Facebook-only.**

Facebook adalah provider/platform pertama, bukan core system.

---

# ATURAN PALING PENTING

Sebelum melakukan coding atau mengubah file apa pun:

1. Audit seluruh repository.
2. Baca README.md jika tersedia.
3. Baca seluruh dokumentasi yang sudah tersedia.
4. Periksa struktur folder.
5. Identifikasi frontend, backend, database, API, authentication, storage, queue, scheduler, dan konfigurasi.
6. Periksa package/dependency yang sudah digunakan.
7. Jalankan pemeriksaan/build/test yang aman jika memungkinkan.
8. Jangan menghapus atau mengganti arsitektur yang sudah ada hanya karena menurutmu ada pendekatan yang lebih bagus.
9. Jangan melakukan refactor besar pada tahap audit.
10. Jangan langsung membuat fitur publishing.
11. Jangan membuat dummy implementation yang terlihat seperti API sudah bekerja.
12. Jangan menggunakan Facebook username/password automation.
13. Gunakan API resmi platform apabila tersedia.
14. Jika kemampuan API atau permission belum pasti, lakukan research terlebih dahulu dan dokumentasikan hasilnya.
15. Jangan mengarang endpoint, permission, atau kemampuan API.

---

# TUJUAN PRODUK

Web ini nantinya menjadi centralized content publishing platform.

Konsep sederhananya:

Upload video
→ pilih platform
→ pilih account/Page/channel
→ isi caption/metadata
→ publish sekarang atau jadwalkan
→ masuk queue
→ worker melakukan publishing
→ status tersimpan
→ history tersedia di dashboard.

Contoh:

Video A

☑ Facebook Page A
☑ Facebook Page B
☑ YouTube Channel A

Schedule:
21 August 2026 20:00

Sistem membuat publishing jobs terpisah untuk setiap destination.

---

# PRINSIP ARSITEKTUR

Gunakan prinsip:

## Core ≠ Platform

Core system tidak boleh mengetahui detail API Facebook.

Core hanya menangani konsep umum seperti:

* media
* upload
* accounts
* destinations
* publishing jobs
* queue
* scheduler
* retry
* status
* history
* logs
* notifications
* database
* storage

Sedangkan implementasi platform berada di module/provider masing-masing.

Contoh konsep:

```text
Core
  |
  +-- Platform Provider Interface
          |
          +-- Facebook Provider
          +-- YouTube Provider
          +-- Instagram Provider
          +-- TikTok Provider
```

---

# PLATFORM PROVIDER ARCHITECTURE

Desain interface/provider abstraction yang memungkinkan platform baru ditambahkan tanpa mengubah core.

Contoh konsep:

```text
PublisherProvider

- authenticate()
- getAccounts()
- getDestinations()
- validateMedia()
- publish()
- getStatus()
- delete()
```

Tetapi jangan langsung menganggap method di atas final.

Audit requirement dan kemampuan masing-masing platform terlebih dahulu.

Provider harus dapat memiliki capability yang berbeda.

Contoh:

```text
Facebook
- Reels
- Video
- Photo
- Post
- Scheduled publishing jika didukung

YouTube
- Video
- Shorts jika endpoint/metadata yang digunakan mendukung

Instagram
- Reels
- Photo
- Post
```

Jangan memaksa semua platform memiliki fitur yang sama.

Gunakan konsep capability/feature detection.

Contoh:

```text
Platform
 ├── capabilities
 │   ├── video
 │   ├── reels
 │   ├── photo
 │   ├── text_post
 │   └── scheduling
```

---

# FACEBOOK SEBAGAI PROVIDER PERTAMA

Facebook harus dibuat modular.

Jangan membuat semua logic Facebook di satu file.

Pisahkan sesuai fungsi jika memang diperlukan, misalnya:

```text
platforms/
└── facebook/
    ├── auth/
    ├── reels/
    ├── videos/
    ├── photos/
    ├── posts/
    ├── api/
    └── facebook.provider.*
```

Struktur final harus disesuaikan dengan stack project setelah audit.

Jangan memaksakan struktur contoh di atas jika tidak cocok dengan repository.

---

# MULTI ACCOUNT / MULTI DESTINATION

Arsitektur harus mendukung banyak account sejak awal.

Contoh:

```text
User
 ├── Facebook Account
 │    ├── Page A
 │    ├── Page B
 │    └── Page C
 │
 └── YouTube Account
      ├── Channel A
      └── Channel B
```

Jangan membuat sistem hanya untuk satu Facebook Page.

Authentication harus dapat menyimpan connection/account secara aman.

Credential/token:

* jangan disimpan plaintext jika tidak diperlukan
* gunakan encryption/secure storage sesuai stack
* jangan commit secret ke Git
* gunakan environment variables untuk application secrets
* gunakan OAuth/API mechanism resmi

---

# MEDIA SYSTEM

Core media system harus bersifat platform-independent.

Minimal konsep:

```text
Media
- id
- filename
- mimeType
- size
- duration
- width
- height
- storage location
- thumbnail
- metadata
```

Jangan membuat media system khusus Facebook.

Video yang sama nantinya dapat digunakan untuk:

```text
Facebook
YouTube
Instagram
TikTok
```

---

# PUBLISHING JOB

Gunakan konsep job terpisah.

Contoh:

```text
Video 001
    |
    +-- Facebook Page A → Job 001
    +-- Facebook Page B → Job 002
    +-- YouTube Channel A → Job 003
```

Setiap job memiliki status sendiri.

Contoh status:

```text
draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying
```

Jangan menganggap satu publishing sebagai satu global status.

Jika Facebook berhasil tetapi YouTube gagal:

```text
Facebook = published
YouTube = failed
```

bukan:

```text
Global = failed
```

Global status dapat dihitung dari child jobs.

---

# QUEUE & SCHEDULER

Arsitektur harus siap untuk:

* publish now
* scheduled publishing
* queue
* retry
* failed jobs
* concurrency control
* rate limiting
* platform-specific limits

Jangan membuat scheduler yang hanya bekerja untuk Facebook.

Core scheduler harus membuat job dan provider yang menjalankan publishing.

---

# RETRY

Retry harus dirancang sejak awal.

Bedakan:

### Temporary error

Contoh:

* timeout
* temporary API error
* network error
* rate limit

→ dapat retry.

### Permanent error

Contoh:

* invalid token
* permission denied
* unsupported media
* destination tidak tersedia

→ jangan retry tanpa perubahan/reauthentication.

Simpan:

```text
attempt count
last error
error code
error message
next retry time
```

---

# UI / UX

Sebelum coding UI besar, audit UI yang sudah ada.

Jika belum ada UI, buat desain berdasarkan prinsip:

* clean
* modern
* responsive
* mobile-friendly
* desktop-friendly
* tidak terlalu banyak whitespace
* navigasi jelas
* komponen reusable
* consistent design system

Dashboard utama nantinya dapat memiliki:

```text
Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings
```

Tetapi jangan implementasikan semuanya pada tahap audit.

---

# UPLOAD UI

Konsep UI:

```text
Upload Content

[ Select / Drop Video ]

Video Preview

Caption
[........................]

Platforms

☑ Facebook
☐ YouTube
☐ Instagram
☐ TikTok

Destinations

☑ Facebook Page A
☐ Facebook Page B

Schedule

[ Publish Now ]
[ Schedule ]

[ Publish ]
```

Platform yang belum tersedia jangan dibuat seolah-olah sudah aktif.

Contoh:

```text
YouTube
Coming Soon
```

atau platform capability hanya muncul setelah provider tersedia.

---

# DOCUMENTATION

Pada tahap awal, buat atau update dokumentasi yang diperlukan.

Gunakan satu sumber dokumentasi utama dan jangan membuat banyak README yang tidak diperlukan.

Minimal dokumentasi:

```text
README.md
docs/
├── ARCHITECTURE.md
├── UI_DESIGN.md
├── PLATFORM_MODULES.md
├── DATABASE.md
└── ROADMAP.md
```

Jika repository sudah memiliki dokumentasi dengan nama/struktur berbeda, jangan membuat duplikasi tanpa alasan.

Gabungkan atau gunakan dokumentasi existing.

---

# README.md

README harus menjelaskan:

1. Nama project
2. Tujuan project
3. Teknologi
4. Cara menjalankan project
5. Struktur project
6. Architecture overview
7. Environment variables
8. Development workflow
9. Platform provider concept
10. Current implementation status
11. Roadmap
12. Security notes

---

# ARCHITECTURE.md

Dokumentasikan:

* system architecture
* frontend
* backend
* database
* media storage
* queue
* scheduler
* authentication
* provider abstraction
* publishing job
* retry
* logging
* error handling

Gunakan diagram ASCII jika membantu.

Contoh:

```text
Frontend
   |
   v
API
   |
   v
Core Publishing Service
   |
   +---- Queue
   |
   +---- Scheduler
   |
   +---- Provider Registry
             |
             +---- Facebook
             +---- YouTube
             +---- Instagram
             +---- TikTok
```

---

# PLATFORM_MODULES.md

Dokumentasikan aturan provider.

Jelaskan:

* bagaimana provider didaftarkan
* bagaimana authentication bekerja
* bagaimana account connection disimpan
* bagaimana destination ditemukan
* bagaimana capability didefinisikan
* bagaimana media divalidasi
* bagaimana publish job dibuat
* bagaimana error diterjemahkan
* bagaimana retry ditentukan

Tujuannya:

Menambahkan YouTube nantinya tidak boleh memerlukan perubahan besar pada core.

---

# UI_DESIGN.md

Dokumentasikan:

* design principles
* colors
* typography
* spacing
* buttons
* cards
* forms
* tables
* navigation
* responsive behavior
* mobile UI
* upload UI
* publishing status UI
* empty states
* loading states
* error states

Jika UI sudah tersedia di repository, dokumentasikan UI yang sebenarnya, jangan membuat spesifikasi yang bertentangan dengan implementasi.

---

# DATABASE.md

Desain database secara platform-independent.

Konsep entity minimal:

```text
User
Platform
PlatformConnection
Destination
Media
PublishingJob
PublishingAttempt
Schedule
Post
AuditLog
```

Jangan langsung membuat schema final sebelum audit stack/database existing.

Pastikan relasi mendukung:

```text
1 user
→ multiple platform connections
→ multiple destinations
→ multiple media
→ multiple publishing jobs
```

---

# SECURITY

Audit dan dokumentasikan:

* OAuth tokens
* refresh tokens
* API keys
* encryption
* secrets
* environment variables
* authorization
* user isolation
* webhook security jika diperlukan
* file upload security
* MIME validation
* file size limits
* path traversal protection
* SSRF prevention jika URL media digunakan
* rate limiting

Jangan commit credential atau token ke repository.

---

# API RESEARCH

Karena project menggunakan platform eksternal, sebelum implementation lakukan research resmi terhadap API.

Prioritaskan dokumentasi resmi:

1. Meta/Facebook Graph API
2. YouTube Data API
3. Instagram Graph API
4. TikTok Content Posting API
5. API platform lain jika diperlukan

Untuk setiap platform, catat:

```text
Platform
Authentication
Supported content
Supported destinations
Required permissions
Upload flow
Scheduling support
Media requirements
Rate limits
Known limitations
App review requirements
```

Jangan menggunakan blog random sebagai sumber utama jika dokumentasi resmi tersedia.

Jika sebuah fitur belum dapat dipastikan, tandai:

```text
UNKNOWN / NEEDS VERIFICATION
```

Jangan menganggap fitur tersebut tersedia.

---

# ROADMAP

Buat roadmap bertahap.

## Phase 0 — Discovery & Audit

* audit repository
* audit stack
* audit existing UI
* audit database
* audit API
* identify technical debt
* identify missing requirements

Output:

* architecture proposal
* UI specification
* platform capability matrix
* roadmap

---

## Phase 1 — Core Foundation

Bangun fondasi:

* project architecture
* authentication
* users
* media management
* storage abstraction
* platform registry
* provider interface
* destination abstraction
* publishing job model
* queue foundation
* scheduler foundation
* logging
* error handling

Belum perlu semua platform.

---

## Phase 2 — Facebook Connection

Implement:

* Facebook OAuth/official authentication
* connection management
* token management
* retrieve available Pages/destinations
* connection status
* reconnect
* disconnect
* secure credential handling

---

## Phase 3 — Facebook Reels

Implement:

* video upload
* video validation
* caption
* destination selection
* publishing job
* queue
* publish
* status tracking
* retry
* history
* error handling

---

## Phase 4 — Facebook Other Publishing

Setelah Reels stabil, tambahkan jenis content Facebook yang memang tersedia dan relevan melalui API resmi.

Contoh kandidat:

* Page video
* photo
* text post
* link post
* scheduling jika didukung

Setiap fitur harus dibuat sebagai capability/module, bukan hardcoded ke core.

---

## Phase 5 — Scheduler & Automation

Implement:

* schedule post
* recurring/advanced scheduling jika memang diperlukan
* queue management
* retry
* rate limiting
* concurrency
* failed jobs
* cancellation
* publishing history

---

## Phase 6 — YouTube Provider

Tambahkan YouTube tanpa mengubah core architecture.

Implement:

* YouTube OAuth
* channel connection
* channel selection
* video upload
* metadata
* thumbnail jika didukung
* Shorts handling jika sesuai API
* publishing status
* error handling

Target:

```text
Same video
→ Facebook
→ YouTube
```

dari dashboard yang sama.

---

## Phase 7 — Instagram Provider

Implement berdasarkan API resmi yang tersedia:

* authentication
* account/destination
* supported media
* publishing
* status
* errors

---

## Phase 8 — TikTok Provider

Implement berdasarkan Content Posting API dan permission yang tersedia.

Jangan mengandalkan browser automation jika official API dapat digunakan.

---

## Phase 9 — Advanced Automation

Setelah provider stabil:

* bulk upload
* bulk scheduling
* content queue
* templates
* caption templates
* hashtag templates
* platform-specific caption
* media presets
* automatic retry
* notifications
* analytics
* publishing calendar

---

# IMPORTANT DEVELOPMENT RULE

Jangan langsung mengimplementasikan seluruh roadmap.

Kerjakan **satu phase pada satu waktu**.

Setelah setiap phase:

1. run typecheck
2. run lint
3. run tests
4. run build
5. inspect UI
6. inspect database migration
7. inspect API integration
8. review security
9. update documentation
10. report what changed

Jangan lanjut ke phase berikutnya jika phase sebelumnya rusak.

---

# UI DEVELOPMENT RULE

AI wajib mengecek UI existing sebelum mengubah UI.

Jangan:

* membuat dashboard baru jika dashboard sudah ada
* mengganti design system tanpa alasan
* membuat duplicate component
* membuat duplicate page
* menghapus UI existing tanpa instruksi
* membuat mock UI yang tidak terhubung ke backend lalu menganggap fitur selesai

Jika fitur backend belum tersedia:

```text
UI = clearly marked as unavailable / coming soon
```

bukan fake success.

---

# CODE QUALITY

Gunakan:

* modular architecture
* single responsibility
* reusable components
* typed interfaces
* clear error handling
* dependency injection jika sesuai stack
* provider abstraction
* testable services

Hindari:

* giant files
* giant components
* Facebook logic di core
* hardcoded credentials
* hardcoded Page IDs
* duplicated upload logic
* duplicated scheduler logic
* duplicated queue logic

---

# OUTPUT YANG SAYA MINTA SEKARANG

Pada tahap ini **JANGAN melakukan implementation besar**.

Lakukan hanya:

### 1. Repository Audit

Berikan:

```text
Current Stack
Current Architecture
Current UI
Current Database
Current API
Current Problems
Current Risks
```

### 2. Architecture Proposal

Jelaskan arsitektur yang paling cocok berdasarkan repository sebenarnya.

### 3. Platform Architecture

Jelaskan bagaimana Facebook menjadi provider pertama dan bagaimana YouTube/Instagram/TikTok dapat ditambahkan nanti.

### 4. API Capability Research

Research dokumentasi resmi dan buat capability matrix.

### 5. Documentation

Buat/update dokumentasi yang diperlukan.

### 6. Roadmap

Buat roadmap berdasarkan hasil audit, bukan asumsi.

### 7. Implementation Plan

Tentukan **Phase 1 yang paling tepat untuk mulai coding**.

---

# STOP CONDITION

Setelah audit, dokumentasi, architecture proposal, API research, dan roadmap selesai:

**STOP.**

Jangan mulai membuat Facebook uploader atau mengubah banyak file.

Tunggu instruksi berikutnya sebelum implementation besar.

Di akhir laporan, tampilkan:

```text
AUDIT STATUS: COMPLETE
ARCHITECTURE STATUS: READY
API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION
ROADMAP STATUS: READY
IMPLEMENTATION STATUS: NOT STARTED
NEXT RECOMMENDED STEP: ...
```

Tujuan utama tahap ini adalah memastikan kita **tidak salah desain sejak awal** dan project dapat berkembang dari Facebook → YouTube → Instagram → TikTok tanpa harus membongkar core system.

````
# Prompt 01 — Initial Audit, Architecture & Roadmap
```

# Prompt 01 — Initial Audit, Architecture & Roadmap

## Tujuan

Kita akan membangun sebuah web platform untuk **automatic content publishing**, dengan **Facebook sebagai platform pertama**.

Namun, arsitektur project sejak awal HARUS dirancang agar nantinya dapat menambahkan platform lain seperti:

* YouTube
* Instagram
* TikTok
* X
* Pinterest
* LinkedIn
* platform lain yang memiliki API publishing yang sesuai

**Jangan membuat project menjadi Facebook-only.**

Facebook adalah provider/platform pertama, bukan core system.

---

# ATURAN PALING PENTING

Sebelum melakukan coding atau mengubah file apa pun:

1. Audit seluruh repository.
2. Baca `README.md` jika tersedia.
3. Baca seluruh dokumentasi yang sudah tersedia.
4. Periksa struktur folder.
5. Identifikasi frontend, backend, database, API, authentication, storage, queue, scheduler, dan konfigurasi.
6. Periksa package/dependency yang sudah digunakan.
7. Jalankan pemeriksaan/build/test yang aman jika memungkinkan.
8. Jangan menghapus atau mengganti arsitektur yang sudah ada hanya karena menurutmu ada pendekatan yang lebih bagus.
9. Jangan melakukan refactor besar pada tahap audit.
10. Jangan langsung membuat fitur publishing.
11. Jangan membuat dummy implementation yang terlihat seperti API sudah bekerja.
12. Jangan menggunakan Facebook username/password automation.
13. Gunakan API resmi platform apabila tersedia.
14. Jika kemampuan API atau permission belum pasti, lakukan research terlebih dahulu dan dokumentasikan hasilnya.
15. Jangan mengarang endpoint, permission, atau kemampuan API.

---

# TUJUAN PRODUK

Web ini nantinya menjadi centralized content publishing platform.

Konsep sederhananya:

Upload video
→ pilih platform
→ pilih account/Page/channel
→ isi caption/metadata
→ publish sekarang atau jadwalkan
→ masuk queue
→ worker melakukan publishing
→ status tersimpan
→ history tersedia di dashboard.

Contoh:

Video A

☑ Facebook Page A
☑ Facebook Page B
☑ YouTube Channel A

Schedule:
21 August 2026 20:00

Sistem membuat publishing jobs terpisah untuk setiap destination.

---

# PRINSIP ARSITEKTUR

Gunakan prinsip:

## Core ≠ Platform

Core system tidak boleh mengetahui detail API Facebook.

Core hanya menangani konsep umum seperti:

* media
* upload
* accounts
* destinations
* publishing jobs
* queue
* scheduler
* retry
* status
* history
* logs
* notifications
* database
* storage

Sedangkan implementasi platform berada di module/provider masing-masing.

Contoh konsep:

```text
Core
  |
  +-- Platform Provider Interface
          |
          +-- Facebook Provider
          +-- YouTube Provider
          +-- Instagram Provider
          +-- TikTok Provider
```

---

# PLATFORM PROVIDER ARCHITECTURE

Desain interface/provider abstraction yang memungkinkan platform baru ditambahkan tanpa mengubah core.

Contoh konsep:

```text
PublisherProvider

- authenticate()
- getAccounts()
- getDestinations()
- validateMedia()
- publish()
- getStatus()
- delete()
```

Tetapi jangan langsung menganggap method di atas final.

Audit requirement dan kemampuan masing-masing platform terlebih dahulu.

Provider harus dapat memiliki capability yang berbeda.

Contoh:

```text
Facebook
- Reels
- Video
- Photo
- Post
- Scheduled publishing jika didukung

YouTube
- Video
- Shorts jika endpoint/metadata yang digunakan mendukung

Instagram
- Reels
- Photo
- Post
```

Jangan memaksa semua platform memiliki fitur yang sama.

Gunakan konsep capability/feature detection.

Contoh:

```text
Platform
 ├── capabilities
 │   ├── video
 │   ├── reels
 │   ├── photo
 │   ├── text_post
 │   └── scheduling
```

---

# FACEBOOK SEBAGAI PROVIDER PERTAMA

Facebook harus dibuat modular.

Jangan membuat semua logic Facebook di satu file.

Pisahkan sesuai fungsi jika memang diperlukan, misalnya:

```text
platforms/
└── facebook/
    ├── auth/
    ├── reels/
    ├── videos/
    ├── photos/
    ├── posts/
    ├── api/
    └── facebook.provider.*
```

Struktur final harus disesuaikan dengan stack project setelah audit.

Jangan memaksakan struktur contoh di atas jika tidak cocok dengan repository.

---

# MULTI ACCOUNT / MULTI DESTINATION

Arsitektur harus mendukung banyak account sejak awal.

Contoh:

```text
User
 ├── Facebook Account
 │    ├── Page A
 │    ├── Page B
 │    └── Page C
 │
 └── YouTube Account
      ├── Channel A
      └── Channel B
```

Jangan membuat sistem hanya untuk satu Facebook Page.

Authentication harus dapat menyimpan connection/account secara aman.

Credential/token:

* jangan disimpan plaintext jika tidak diperlukan
* gunakan encryption/secure storage sesuai stack
* jangan commit secret ke Git
* gunakan environment variables untuk application secrets
* gunakan OAuth/API mechanism resmi

---

# MEDIA SYSTEM

Core media system harus bersifat platform-independent.

Minimal konsep:

```text
Media
- id
- filename
- mimeType
- size
- duration
- width
- height
- storage location
- thumbnail
- metadata
```

Jangan membuat media system khusus Facebook.

Video yang sama nantinya dapat digunakan untuk:

```text
Facebook
YouTube
Instagram
TikTok
```

---

# PUBLISHING JOB

Gunakan konsep job terpisah.

Contoh:

```text
Video 001
    |
    +-- Facebook Page A → Job 001
    +-- Facebook Page B → Job 002
    +-- YouTube Channel A → Job 003
```

Setiap job memiliki status sendiri.

Contoh status:

```text
draft
queued
scheduled
processing
uploading
publishing
published
failed
cancelled
retrying
```

Jangan menganggap satu publishing sebagai satu global status.

Jika Facebook berhasil tetapi YouTube gagal:

```text
Facebook = published
YouTube = failed
```

bukan:

```text
Global = failed
```

Global status dapat dihitung dari child jobs.

---

# QUEUE & SCHEDULER

Arsitektur harus siap untuk:

* publish now
* scheduled publishing
* queue
* retry
* failed jobs
* concurrency control
* rate limiting
* platform-specific limits

Jangan membuat scheduler yang hanya bekerja untuk Facebook.

Core scheduler harus membuat job dan provider yang menjalankan publishing.

---

# RETRY

Retry harus dirancang sejak awal.

Bedakan:

### Temporary error

Contoh:

* timeout
* temporary API error
* network error
* rate limit

→ dapat retry.

### Permanent error

Contoh:

* invalid token
* permission denied
* unsupported media
* destination tidak tersedia

→ jangan retry tanpa perubahan/reauthentication.

Simpan:

```text
attempt count
last error
error code
error message
next retry time
```

---

# UI / UX

Sebelum coding UI besar, audit UI yang sudah ada.

Jika belum ada UI, buat desain berdasarkan prinsip:

* clean
* modern
* responsive
* mobile-friendly
* desktop-friendly
* tidak terlalu banyak whitespace
* navigasi jelas
* komponen reusable
* consistent design system

Dashboard utama nantinya dapat memiliki:

```text
Dashboard
Upload
Queue
Scheduled
Accounts
Platforms
History
Analytics
Settings
```

Tetapi jangan implementasikan semuanya pada tahap audit.

---

# UPLOAD UI

Konsep UI:

```text
Upload Content

[ Select / Drop Video ]

Video Preview

Caption
[........................]

Platforms

☑ Facebook
☐ YouTube
☐ Instagram
☐ TikTok

Destinations

☑ Facebook Page A
☐ Facebook Page B

Schedule

[ Publish Now ]
[ Schedule ]

[ Publish ]
```

Platform yang belum tersedia jangan dibuat seolah-olah sudah aktif.

Contoh:

```text
YouTube
Coming Soon
```

atau platform capability hanya muncul setelah provider tersedia.

---

# DOCUMENTATION

Pada tahap awal, buat atau update dokumentasi yang diperlukan.

Gunakan satu sumber dokumentasi utama dan jangan membuat banyak README yang tidak diperlukan.

Minimal dokumentasi:

```text
README.md
docs/
├── ARCHITECTURE.md
├── UI_DESIGN.md
├── PLATFORM_MODULES.md
├── DATABASE.md
└── ROADMAP.md
```

Jika repository sudah memiliki dokumentasi dengan nama/struktur berbeda, jangan membuat duplikasi tanpa alasan.

Gabungkan atau gunakan dokumentasi existing.

---

# README.md

README harus menjelaskan:

1. Nama project
2. Tujuan project
3. Teknologi
4. Cara menjalankan project
5. Struktur project
6. Architecture overview
7. Environment variables
8. Development workflow
9. Platform provider concept
10. Current implementation status
11. Roadmap
12. Security notes

---

# ARCHITECTURE.md

Dokumentasikan:

* system architecture
* frontend
* backend
* database
* media storage
* queue
* scheduler
* authentication
* provider abstraction
* publishing job
* retry
* logging
* error handling

Gunakan diagram ASCII jika membantu.

Contoh:

```text
Frontend
   |
   v
API
   |
   v
Core Publishing Service
   |
   +---- Queue
   |
   +---- Scheduler
   |
   +---- Provider Registry
             |
             +---- Facebook
             +---- YouTube
             +---- Instagram
             +---- TikTok
```

---

# PLATFORM_MODULES.md

Dokumentasikan aturan provider.

Jelaskan:

* bagaimana provider didaftarkan
* bagaimana authentication bekerja
* bagaimana account connection disimpan
* bagaimana destination ditemukan
* bagaimana capability didefinisikan
* bagaimana media divalidasi
* bagaimana publish job dibuat
* bagaimana error diterjemahkan
* bagaimana retry ditentukan

Tujuannya:

Menambahkan YouTube nantinya tidak boleh memerlukan perubahan besar pada core.

---

# UI_DESIGN.md

Dokumentasikan:

* design principles
* colors
* typography
* spacing
* buttons
* cards
* forms
* tables
* navigation
* responsive behavior
* mobile UI
* upload UI
* publishing status UI
* empty states
* loading states
* error states

Jika UI sudah tersedia di repository, dokumentasikan UI yang sebenarnya, jangan membuat spesifikasi yang bertentangan dengan implementasi.

---

# DATABASE.md

Desain database secara platform-independent.

Konsep entity minimal:

```text
User
Platform
PlatformConnection
Destination
Media
PublishingJob
PublishingAttempt
Schedule
Post
AuditLog
```

Jangan langsung membuat schema final sebelum audit stack/database existing.

Pastikan relasi mendukung:

```text
1 user
→ multiple platform connections
→ multiple destinations
→ multiple media
→ multiple publishing jobs
```

---

# SECURITY

Audit dan dokumentasikan:

* OAuth tokens
* refresh tokens
* API keys
* encryption
* secrets
* environment variables
* authorization
* user isolation
* webhook security jika diperlukan
* file upload security
* MIME validation
* file size limits
* path traversal protection
* SSRF prevention jika URL media digunakan
* rate limiting

Jangan commit credential atau token ke repository.

---

# API RESEARCH

Karena project menggunakan platform eksternal, sebelum implementation lakukan research resmi terhadap API.

Prioritaskan dokumentasi resmi:

1. Meta/Facebook Graph API
2. YouTube Data API
3. Instagram Graph API
4. TikTok Content Posting API
5. API platform lain jika diperlukan

Untuk setiap platform, catat:

```text
Platform
Authentication
Supported content
Supported destinations
Required permissions
Upload flow
Scheduling support
Media requirements
Rate limits
Known limitations
App review requirements
```

Jangan menggunakan blog random sebagai sumber utama jika dokumentasi resmi tersedia.

Jika sebuah fitur belum dapat dipastikan, tandai:

```text
UNKNOWN / NEEDS VERIFICATION
```

Jangan menganggap fitur tersebut tersedia.

---

# ROADMAP

Buat roadmap bertahap.

## Phase 0 — Discovery & Audit

* audit repository
* audit stack
* audit existing UI
* audit database
* audit API
* identify technical debt
* identify missing requirements

Output:

* architecture proposal
* UI specification
* platform capability matrix
* roadmap

---

## Phase 1 — Core Foundation

Bangun fondasi:

* project architecture
* authentication
* users
* media management
* storage abstraction
* platform registry
* provider interface
* destination abstraction
* publishing job model
* queue foundation
* scheduler foundation
* logging
* error handling

Belum perlu semua platform.

---

## Phase 2 — Facebook Connection

Implement:

* Facebook OAuth/official authentication
* connection management
* token management
* retrieve available Pages/destinations
* connection status
* reconnect
* disconnect
* secure credential handling

---

## Phase 3 — Facebook Reels

Implement:

* video upload
* video validation
* caption
* destination selection
* publishing job
* queue
* publish
* status tracking
* retry
* history
* error handling

---

## Phase 4 — Facebook Other Publishing

Setelah Reels stabil, tambahkan jenis content Facebook yang memang tersedia dan relevan melalui API resmi.

Contoh kandidat:

* Page video
* photo
* text post
* link post
* scheduling jika didukung

Setiap fitur harus dibuat sebagai capability/module, bukan hardcoded ke core.

---

## Phase 5 — Scheduler & Automation

Implement:

* schedule post
* recurring/advanced scheduling jika memang diperlukan
* queue management
* retry
* rate limiting
* concurrency
* failed jobs
* cancellation
* publishing history

---

## Phase 6 — YouTube Provider

Tambahkan YouTube tanpa mengubah core architecture.

Implement:

* YouTube OAuth
* channel connection
* channel selection
* video upload
* metadata
* thumbnail jika didukung
* Shorts handling jika sesuai API
* publishing status
* error handling

Target:

```text
Same video
→ Facebook
→ YouTube
```

dari dashboard yang sama.

---

## Phase 7 — Instagram Provider

Implement berdasarkan API resmi yang tersedia:

* authentication
* account/destination
* supported media
* publishing
* status
* errors

---

## Phase 8 — TikTok Provider

Implement berdasarkan Content Posting API dan permission yang tersedia.

Jangan mengandalkan browser automation jika official API dapat digunakan.

---

## Phase 9 — Advanced Automation

Setelah provider stabil:

* bulk upload
* bulk scheduling
* content queue
* templates
* caption templates
* hashtag templates
* platform-specific caption
* media presets
* automatic retry
* notifications
* analytics
* publishing calendar

---

# IMPORTANT DEVELOPMENT RULE

Jangan langsung mengimplementasikan seluruh roadmap.

Kerjakan **satu phase pada satu waktu**.

Setelah setiap phase:

1. run typecheck
2. run lint
3. run tests
4. run build
5. inspect UI
6. inspect database migration
7. inspect API integration
8. review security
9. update documentation
10. report what changed

Jangan lanjut ke phase berikutnya jika phase sebelumnya rusak.

---

# UI DEVELOPMENT RULE

AI wajib mengecek UI existing sebelum mengubah UI.

Jangan:

* membuat dashboard baru jika dashboard sudah ada
* mengganti design system tanpa alasan
* membuat duplicate component
* membuat duplicate page
* menghapus UI existing tanpa instruksi
* membuat mock UI yang tidak terhubung ke backend lalu menganggap fitur selesai

Jika fitur backend belum tersedia:

```text
UI = clearly marked as unavailable / coming soon
```

bukan fake success.

---

# CODE QUALITY

Gunakan:

* modular architecture
* single responsibility
* reusable components
* typed interfaces
* clear error handling
* dependency injection jika sesuai stack
* provider abstraction
* testable services

Hindari:

* giant files
* giant components
* Facebook logic di core
* hardcoded credentials
* hardcoded Page IDs
* duplicated upload logic
* duplicated scheduler logic
* duplicated queue logic

---

# OUTPUT YANG SAYA MINTA SEKARANG

Pada tahap ini **JANGAN melakukan implementation besar**.

Lakukan hanya:

### 1. Repository Audit

Berikan:

```text
Current Stack
Current Architecture
Current UI
Current Database
Current API
Current Problems
Current Risks
```

### 2. Architecture Proposal

Jelaskan arsitektur yang paling cocok berdasarkan repository sebenarnya.

### 3. Platform Architecture

Jelaskan bagaimana Facebook menjadi provider pertama dan bagaimana YouTube/Instagram/TikTok dapat ditambahkan nanti.

### 4. API Capability Research

Research dokumentasi resmi dan buat capability matrix.

### 5. Documentation

Buat/update dokumentasi yang diperlukan.

### 6. Roadmap

Buat roadmap berdasarkan hasil audit, bukan asumsi.

### 7. Implementation Plan

Tentukan **Phase 1 yang paling tepat untuk mulai coding**.

---

# STOP CONDITION

Setelah audit, dokumentasi, architecture proposal, API research, dan roadmap selesai:

**STOP.**

Jangan mulai membuat Facebook uploader atau mengubah banyak file.

Tunggu instruksi berikutnya sebelum implementation besar.

Di akhir laporan, tampilkan:

```text
AUDIT STATUS: COMPLETE
ARCHITECTURE STATUS: READY
API RESEARCH STATUS: COMPLETE / NEEDS VERIFICATION
ROADMAP STATUS: READY
IMPLEMENTATION STATUS: NOT STARTED
NEXT RECOMMENDED STEP: ...
```

Tujuan utama tahap ini adalah memastikan kita **tidak salah desain sejak awal** dan project dapat berkembang dari Facebook → YouTube → Instagram → TikTok tanpa harus membongkar core system.

````
