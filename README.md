# prompt-Facebook-otomatic-







# 
```


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
