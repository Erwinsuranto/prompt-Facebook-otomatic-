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


````
# 
```


````
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
