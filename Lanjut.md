


# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```

```
# 
```
CONTENTPILOT — IMPLEMENT P1-1 CONTENT LIBRARY & POST LIFECYCLE

Implementasikan fitur P1-1 berdasarkan hasil audit sebelumnya.

TUJUAN:
ContentPilot harus memiliki Content Library yang benar-benar usable untuk mengelola post yang sudah dibuat, bukan hanya membuat post lalu selesai.

==================================================
ATURAN WAJIB
==================================================

1. Kerjakan langsung, jangan bertanya balik kecuali benar-benar mustahil.
2. Jangan membuat fitur mock/fake.
3. Jangan mengubah database schema/migration kecuali audit implementasi benar-benar membuktikan mutlak diperlukan. Audit sebelumnya menyatakan tidak perlu migration.
4. Jangan mengubah publish pipeline yang sudah berjalan.
5. Jangan mengubah queue/scheduler/worker.
6. Jangan mengubah Facebook OAuth/provider.
7. Jangan mengubah Google Drive/OAuth.
8. Jangan menyentuh /downloader.
9. Jangan mengubah Caddy/DNS/TLS.
10. Jangan mengubah service Genspark/OpenClaw.
11. Pertahankan seluruh authorization dan ownership isolation.
12. Jangan membuat user bisa mengakses post milik user/destination lain.
13. Jangan menghapus fitur existing.
14. Jangan commit/push sebelum seluruh verification selesai.
15. Jangan restart service kecuali memang diperlukan untuk verification deployment.
16. Gunakan pola/error taxonomy/security helper yang sudah ada di repository.
17. Pertahankan arsitektur modular.
18. Tidak boleh ada fake success atau status palsu.

==================================================
1. BACKEND — POSTS API
==================================================

Implementasikan/sempurnakan:

GET /api/posts

Fungsi:
- list post milik authenticated user
- ownership isolation
- destination access validation
- pagination jika pola API saat ini sudah mendukung
- sorting terbaru
- filter status
- search jika model/data memungkinkan
- jangan mengembalikan data user lain

Query parameter yang boleh digunakan:

status
search
page
limit

Jangan memaksakan pagination baru jika repository sudah mempunyai pola pagination yang berbeda. Ikuti convention existing.

Response harus konsisten dengan API existing.

--------------------------------------------------

PATCH /api/posts/:id

Fungsi:
- edit post milik user
- authorization wajib
- validasi input
- update hanya field yang memang editable
- jangan izinkan user mengubah ownership
- jangan izinkan user memanipulasi destination yang bukan miliknya
- jangan izinkan perubahan yang merusak job publish aktif

Field editable sesuaikan dengan model yang benar-benar ada, misalnya:
- caption/text
- media metadata bila memang didukung
- scheduledAt bila memang aman

Jangan menambahkan field database baru hanya untuk fitur ini.

Jika post sudah published:
- jangan izinkan perubahan yang secara semantik mengubah published record menjadi draft secara sembarangan
- ikuti lifecycle yang aman berdasarkan model existing.

Jika post mempunyai active scheduled/publish job:
- jangan mengubah field yang dapat membuat queue/job menjadi inconsistent.

--------------------------------------------------

POST /api/posts/:id/duplicate

Fungsi:
- duplicate post milik user
- hasil duplicate menjadi DRAFT
- jangan ikut menjalankan publish
- jangan ikut membuat job queue/scheduler baru
- jangan menyalin status published/scheduled sebagai status aktif
- jangan menyalin ownership ke user lain
- media reference hanya boleh disalin jika memang aman dan sudah dimiliki user/destination yang sama
- jangan membuat duplicate job

Return post baru yang benar-benar tersimpan.

--------------------------------------------------

DELETE /api/posts/:id

Fungsi:
- hanya owner yang boleh menghapus
- destination isolation tetap berlaku
- jangan menghapus post user lain
- jika ada active scheduled/publish job, jangan menyebabkan orphan job atau accidental publish

Jika post memiliki job aktif:
gunakan behaviour/error convention yang sudah ada untuk mencegah data inconsistency.

Jangan melakukan cascade delete berbahaya di luar behaviour existing.

==================================================
2. POST LIFECYCLE
==================================================

Pastikan status lifecycle yang didukung model existing konsisten.

Target konsep:

DRAFT
  ↓
SCHEDULED
  ↓
PUBLISHED

Dan jika publish gagal, gunakan status/error state yang memang sudah tersedia di repository.

Jangan menambahkan status database baru tanpa alasan kuat.

Pastikan:
- duplicate → DRAFT
- edit draft → tetap DRAFT
- scheduled post tetap aman untuk scheduler
- published post tidak bisa dimanipulasi secara sembarangan
- failed state tetap dapat ditampilkan
- existing queue idempotency tetap utuh

Jangan merusak scheduler/worker.

==================================================
3. SECURITY
==================================================

Gunakan helper existing seperti:

requireUser
assertDestinationAccess
ownership/session guards
error taxonomy

Jangan membuat authorization logic baru yang menduplikasi atau melemahkan helper existing.

Test minimal:
- authenticated user dapat melihat post miliknya
- user tidak dapat melihat post user lain
- user tidak dapat edit post user lain
- user tidak dapat duplicate post user lain
- user tidak dapat delete post user lain
- user tidak dapat menggunakan destination milik user lain
- unauthenticated request ditolak

Pastikan tidak ada IDOR.

==================================================
4. FRONTEND — /library
==================================================

Buat halaman:

/library

Gunakan design system/component pattern yang sudah ada.

Jangan membuat UI yang terlihat seperti template AI generik.

UI harus clean, professional, SaaS-like, responsive, mobile-first.

Navigasi utama harus memiliki:

Library

Pastikan tidak merusak navigation existing.

==================================================
5. LIBRARY UI
==================================================

Tampilkan post dalam bentuk list/table/card sesuai pola UI existing.

Setiap item minimal menampilkan:

- preview media jika tersedia
- caption/title/text ringkas
- status
- destination/Page
- scheduled date/time jika ada
- created date
- updated date
- action menu

Action:

- Edit
- Duplicate
- Delete

Untuk post sesuai status, tampilkan action yang relevan.

Contoh:
DRAFT:
Edit / Duplicate / Delete

SCHEDULED:
Edit / Duplicate / Delete
(tetap hormati restriction terhadap job aktif)

PUBLISHED:
View/Edit sesuai kemampuan model / Duplicate
Delete hanya jika memang aman dan didukung behaviour backend

FAILED:
Edit / Duplicate / Delete
dan tampilkan error bila tersedia tanpa membocorkan secret.

==================================================
6. SEARCH & FILTER
==================================================

Implementasikan:

Search
- caption/text

Filter:
- All
- Draft
- Scheduled
- Published
- Failed jika status tersebut memang ada

Jangan membuat filter untuk status yang tidak ada di model.

Filter harus benar-benar mempengaruhi data.

Jangan membuat frontend filtering palsu jika dataset API besar; gunakan API query bila architecture existing mendukung.

==================================================
7. EDIT UI
==================================================

Buat editor yang menggunakan field existing.

Minimal:
- text/caption
- media preview bila tersedia
- destination bila memang editable dengan aman
- schedule bila memang editable dengan aman

Jangan izinkan perubahan yang backend tidak izinkan.

Validation frontend hanya UX tambahan.
Backend tetap menjadi source of truth.

Setelah save:
- tampilkan success hanya jika API benar-benar sukses
- refresh data
- tampilkan error yang jelas jika gagal

==================================================
8. DUPLICATE UI
==================================================

Saat user memilih Duplicate:

- panggil POST /api/posts/:id/duplicate
- jangan sekadar clone object di frontend
- setelah backend sukses, tampilkan hasil duplicate
- status harus DRAFT
- jangan ada publish action otomatis
- user dapat membuka/edit hasil duplicate

==================================================
9. DELETE UI
==================================================

Gunakan confirmation dialog.

Pesan harus jelas bahwa post akan dihapus.

Setelah DELETE sukses:
- remove/update item dari UI
- refresh list bila diperlukan

Jika backend menolak karena active job:
- tampilkan error yang jelas
- jangan mengatakan berhasil.

==================================================
10. EMPTY / LOADING / ERROR STATES
==================================================

Buat state yang benar:

Loading:
- skeleton/spinner sesuai design system existing

Empty:
"Belum ada konten"

Berikan CTA yang relevan seperti:
"Create Post"

Error:
pesan yang jelas dan tidak menampilkan stack trace/secret.

==================================================
11. RESPONSIVE
==================================================

Desktop:
- library nyaman untuk banyak post

Mobile:
- jangan membuat tabel melebar keluar layar
- gunakan card/list atau responsive layout
- action tetap mudah diakses

Pastikan:
- navigation existing tetap usable
- edit form usable di mobile
- dialog tidak overflow viewport

==================================================
12. API CLIENT
==================================================

Gunakan helper API client existing di:

apps/web/src/lib/api.ts

atau pattern yang memang digunakan repository.

Jangan membuat fetch abstraction kedua tanpa alasan.

==================================================
13. TEST BACKEND
==================================================

Tambahkan/ubah test yang diperlukan.

Minimal test:

GET:
- list own posts
- isolation
- filtering

PATCH:
- edit own post
- reject other user's post
- validation
- active job protection

DUPLICATE:
- duplicate own post
- result is DRAFT
- no queue job
- isolation

DELETE:
- delete own post
- reject other user's post
- active job protection

Lifecycle:
- valid status transition
- invalid transition rejected

==================================================
14. TEST FRONTEND
==================================================

Jika repository sudah memiliki frontend test setup, tambahkan test untuk:

- library renders
- loading state
- empty state
- search/filter
- edit
- duplicate
- delete confirmation
- API error state

Ikuti testing convention existing.

==================================================
15. REGRESSION
==================================================

Setelah implementasi:

pnpm typecheck
pnpm lint
pnpm test
pnpm build

Semua harus PASS.

Jika test gagal:
- perbaiki root cause
- jalankan ulang test

Jangan menonaktifkan test hanya agar PASS.

==================================================
16. GIT / DIFF REVIEW
==================================================

Sebelum selesai:

git status
git diff --stat
git diff

Pastikan perubahan hanya berkaitan dengan P1-1.

Tidak boleh ada:
- perubahan secret
- perubahan .env
- perubahan Caddy
- perubahan unrelated service
- perubahan OAuth
- perubahan queue/scheduler
- perubahan provider

==================================================
17. DEPLOYMENT
==================================================

Setelah verification PASS:

Jika deployment production membutuhkan restart agar artifact baru aktif, restart HANYA:

content-pilot-api.service
content-pilot-worker.service
content-pilot-web.service

Jangan restart:
- caddy
- Genspark
- OpenClaw
- service lain

Kemudian lakukan health check.

Jika deployment tidak diperlukan pada tahap ini, jangan restart apa pun.

==================================================
18. LIVE VERIFICATION
==================================================

Verifikasi minimal:

https://contentpilot.biz.id/
https://contentpilot.biz.id/accounts

dan route:

/library

Pastikan:
- halaman dapat dibuka
- auth bekerja
- API bekerja
- user dapat melihat library
- existing dashboard tidak rusak

Jangan bypass Google Safe Browsing.

==================================================
19. COMMIT
==================================================

JANGAN commit/push dulu.

Saya akan review hasil implementasi dan test terlebih dahulu.

==================================================
FINAL REPORT
==================================================

Laporkan:

1. Fitur yang diimplementasikan
2. Backend routes
3. Frontend /library
4. Lifecycle behaviour
5. Security/ownership protection
6. Files changed
7. Tests added/changed
8. pnpm typecheck
9. pnpm lint
10. pnpm test
11. pnpm build
12. Live verification
13. Services restarted (jika ada)
14. git diff --stat
15. Apakah ada issue tersisa

STOP setelah laporan.
```
# 
```
CONTENTPILOT — URGENT SECURITY / DANGEROUS SITE DIAGNOSIS AND FIX

Chrome menampilkan halaman merah:
"Dangerous site"

Terjadi ketika membuka ContentPilot pada:
domain production: contentpilot.biz.id
path: /settings/storage?connect=success

JANGAN meminta saya bypass warning Chrome.
JANGAN menyuruh saya mematikan Safe Browsing.
JANGAN menyuruh saya menekan "Proceed".
Kita harus mencari dan memperbaiki penyebab sebenarnya.

LAKUKAN LANGSUNG:

1. AUDIT DOMAIN PRODUCTION
Periksa:
- DNS contentpilot.biz.id
- DNS api.contentpilot.biz.id
- TLS certificate dan hostname/SNI
- certificate chain
- HTTP → HTTPS redirect
- HTTPS response
- status code
- response headers
- Content-Security-Policy jika ada
- HSTS jika ada
- X-Content-Type-Options
- Referrer-Policy
- X-Frame-Options / frame-ancestors
- CORS
- apakah ada redirect ke domain/IP asing
- apakah ada iframe/script/resource dari domain mencurigakan

2. AUDIT CADDY
Periksa konfigurasi Caddy yang melayani:
- contentpilot.biz.id
- api.contentpilot.biz.id

Pastikan:
- tidak ada konfigurasi asing
- tidak ada reverse proxy ke host yang tidak dikenal
- tidak ada redirect mencurigakan
- certificate sesuai domain
- konfigurasi ContentPilot tidak merusak service lain seperti Genspark/OpenClaw

JANGAN mengubah Caddy dulu sampai penyebab ditemukan.

3. AUDIT WEBSITE / BUILD
Periksa source dan build ContentPilot untuk kemungkinan:
- injected JavaScript
- iframe mencurigakan
- external script mencurigakan
- redirect JavaScript
- phishing-like page
- malware
- obfuscated script yang tidak dikenal
- asset dari domain asing
- perubahan file yang tidak berasal dari project

Bandingkan working tree dengan git HEAD/origin.
Jangan commit/push.

4. AUDIT OAUTH CALLBACK
Periksa flow:
Google OAuth
→ api.contentpilot.biz.id
→ /api/storage/google_drive/callback
→ contentpilot.biz.id/settings/storage?connect=success

Pastikan callback hanya redirect ke domain ContentPilot yang benar.
Tidak boleh ada open redirect atau user-controlled redirect URL.

5. PERIKSA LOG
Periksa Caddy/API/Web logs untuk request saat OAuth callback.
Cari:
- redirect abnormal
- 3xx ke domain asing
- 4xx/5xx
- suspicious user-agent/request
- injected content
- unexpected host

Jangan tampilkan OAuth code, token, cookie, secret, atau credential.

6. CEK STATUS SAFE BROWSING / REPUTATION
Jika VPS punya cara aman untuk memeriksa status Google Safe Browsing/Google Transparency Report terhadap domain production, lakukan pemeriksaan.
Jangan bypass warning.

7. JIKA DITEMUKAN MASALAH NYATA:
Perbaiki langsung hanya jika perubahan jelas, aman, dan terbatas pada ContentPilot.
Contoh:
- redirect salah
- header security salah
- injected resource
- konfigurasi Caddy salah
- callback redirect salah
- asset mencurigakan yang memang berasal dari deployment

Jangan mengubah database.

8. SETELAH PERBAIKAN:
- validasi Caddy config
- cek HTTPS
- cek contentpilot.biz.id
- cek api.contentpilot.biz.id
- cek OAuth callback
- cek API health
- cek Web health
- jalankan:
  pnpm typecheck
  pnpm lint
  pnpm test
  pnpm build

9. JANGAN restart service kecuali memang diperlukan untuk menerapkan perbaikan.
Jika perlu restart, restart hanya service ContentPilot yang terkait.
Jangan restart Caddy kecuali perubahan Caddy memang diperlukan.

10. JANGAN COMMIT/PUSH.

HASIL AKHIR WAJIB:

SECURITY STATUS
- Dangerous-site root cause: ...
- Domain/TLS: PASS/FAIL
- Redirect audit: PASS/FAIL
- Caddy audit: PASS/FAIL
- Website/build integrity: PASS/FAIL
- OAuth callback: PASS/FAIL
- Suspicious resource/injection: FOUND/NOT FOUND
- Safe Browsing status: ...
- Fix applied: YES/NO

REGRESSION
- typecheck: PASS/FAIL
- lint: PASS/FAIL
- test: PASS/FAIL
- build: PASS/FAIL

Jika tidak ditemukan penyebab yang dapat diperbaiki dari VPS, STOP dan jelaskan secara spesifik apa yang menyebabkan warning kemungkinan berasal dari reputation/Safe Browsing sehingga langkah berikutnya dapat dilakukan secara aman.

JANGAN meminta saya bypass Chrome.
```
# 
```
CONTENTPILOT — FIND EXISTING USER ACCOUNT

Saya lupa email akun ContentPilot yang sudah pernah dibuat.

Cari akun user yang sudah terdaftar di database production ContentPilot.

ATURAN:
- READ-ONLY.
- Jangan mengubah database.
- Jangan membuat user baru.
- Jangan reset password.
- Jangan mengubah credential.
- Jangan commit/push.
- Jangan restart service.
- Jangan tampilkan password, password hash, token, session, OAuth credential, atau secret apa pun.

Tampilkan hanya informasi yang aman:
- jumlah user yang terdaftar
- email user yang terdaftar (email boleh ditampilkan karena saya perlu mengenali akun saya)
- user ID jika aman diperlukan
- created_at jika tersedia

Jika hanya ada satu akun, tandai sebagai kandidat akun saya.
Jika ada beberapa akun, tampilkan daftar email agar saya bisa mengenali yang benar.

STOP setelah hasil ditemukan.
```

# 
```
CONTENTPILOT — REAL GOOGLE DRIVE OAUTH VERIFICATION

Google Cloud OAuth Client sudah dikonfigurasi dengan production redirect URI:

https://api.contentpilot.biz.id/api/storage/google_drive/callback

Sekarang lakukan pengujian end-to-end Google Drive OAuth ContentPilot.

ATURAN:
- Jangan coding kecuali ditemukan bug nyata; jika bug ditemukan STOP dan laporkan dulu.
- Jangan commit.
- Jangan push.
- Jangan mengubah database/schema.
- Jangan mengubah Caddy.
- Jangan mengubah credential/secret.
- Jangan menampilkan client secret atau token.
- Jangan melakukan tindakan Google Drive yang destruktif.
- Jangan menghapus file/folder Google Drive.
- Jangan membuat perubahan pada akun Google saya tanpa autentikasi/interaksi saya sendiri.

LANGKAH:

1. Verifikasi environment production:
   - Google Client ID = SET
   - Google Client Secret = SET
   - GOOGLE_DRIVE_REDIRECT_URI = production
   - provider = configured

2. Verifikasi endpoint:
   - Google OAuth connect endpoint
   - Google OAuth callback endpoint
   - API health/readiness

3. Buat/periksa authorization URL Google OAuth yang digunakan ContentPilot.
   Pastikan redirect_uri yang dikirim adalah tepat:
   https://api.contentpilot.biz.id/api/storage/google_drive/callback

   JANGAN tampilkan client secret atau authorization code.

4. Saya akan melakukan login/consent Google secara manual jika browser membuka halaman Google.

5. Jika OAuth berhasil kembali ke ContentPilot:
   - verifikasi callback berhasil
   - verifikasi state valid
   - verifikasi token exchange berhasil
   - verifikasi koneksi Google Drive tersimpan dengan benar
   - verifikasi token/credential tidak muncul di log

6. Jika aplikasi menyediakan endpoint/status untuk Google Drive connection, cek statusnya.

7. Jalankan regression setelah test:
   pnpm typecheck
   pnpm lint
   pnpm test
   pnpm build

LAPORAN:
- Google provider: PASS/FAIL
- Redirect URI: PASS/FAIL
- Connect endpoint: PASS/FAIL
- OAuth authorization: PASS/FAIL
- Callback: PASS/FAIL
- Token exchange: PASS/FAIL
- Google Drive connection: PASS/FAIL
- Secret exposure: PASS/FAIL
- typecheck: PASS/FAIL
- lint: PASS/FAIL
- test: PASS/FAIL
- build: PASS/FAIL

Jika test berhenti karena membutuhkan interaksi login Google saya, tampilkan URL/next step yang aman untuk saya buka, tanpa menampilkan secret.

STOP setelah hasil test.
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
