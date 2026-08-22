# prompt-Facebook-otomatic-

# 
```


````



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
