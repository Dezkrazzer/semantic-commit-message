# Semantic Commit Message

Panduan lengkap tentang **Semantic Commit Message** - standar untuk menulis pesan commit yang konsisten, terstruktur, dan mudah dipahami.

## 📋 Daftar Isi

- [Pengenalan](#pengenalan)
- [Format Commit](#format-commit)
- [Jenis-jenis Commit](#jenis-jenis-commit)
- [Contoh Penggunaan](#contoh-penggunaan)
- [Best Practices](#best-practices)
- [Tools & Integrasi](#tools--integrasi)
- [Keuntungan](#keuntungan)

## Pengenalan

Semantic Commit Message adalah konvensi penulisan pesan commit yang mengikuti standar tertentu. Standar ini membantu:

- **Membaca history** commit dengan lebih mudah
- **Mengotomatisasi** versioning dan changelog
- **Kolaborasi tim** menjadi lebih baik
- **Tracking changes** menjadi lebih terstruktur

## Format Commit

Format standar Semantic Commit Message adalah:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Penjelasan:

| Bagian | Deskripsi |
|--------|-----------|
| **type** | Jenis commit (feat, fix, docs, dll) |
| **scope** | Bagian/modul yang diubah (opsional) |
| **subject** | Deskripsi singkat perubahan (imperatif, lowercase) |
| **body** | Penjelasan detail tentang perubahan (opsional) |
| **footer** | Informasi tambahan seperti issue number (opsional) |

### Contoh Format:

```
feat(authentication): tambahkan fitur login dengan OAuth

Menambahkan integrasi OAuth 2.0 untuk meningkatkan keamanan.
Pengguna dapat login menggunakan akun Google atau GitHub.

Closes #123
```

## Jenis-jenis Commit

| Tipe | Nama | Deskripsi | Contoh |
|------|------|-----------|---------|
| **feat** | Feature | Menambahkan fitur baru | `feat: tambahkan fitur login` |
| **fix** | Bug Fix | Memperbaiki bug atau error | `fix: perbaiki crash saat upload gambar besar` |
| **docs** | Documentation | Mengubah dokumentasi (README, Wiki) | `docs: update panduan instalasi di README` |
| **style** | Style | Perubahan format code (spasi, titik koma) tanpa mengubah logika | `style: hapus spasi berlebih di header` |
| **refactor** | Refactor | Mengubah struktur code tanpa menambah fitur atau perbaikan bug | `refactor: sederhanakan logika fungsi hitung gaji` |
| **perf** | Performance | Peningkatan code untuk meningkatkan performa | `perf: optimasi query database untuk user list` |
| **test** | Test | Menambahkan atau memperbaiki testing | `test: tambahkan unit test untuk module pembayaran` |
| **chore** | Chore | Tugas-tugas kecil, update dependency, atau build script | `chore: update versi discord.js ke v14` |
| **build** | Build | Perubahan sistem build (npm, gradle, gulp) | `build: tambahkan script minify css` |
| **ci** | CI | Perubahan pada file konfigurasi CI (GitHub Actions, Jenkins) | `ci: perbaiki script deploy ke vercel` |
| **revert** | Revert | Membatalkan commit sebelumnya | `revert: batalkan commit a2b3c4` |

## Contoh Penggunaan

### 1. Feature Baru

```
feat(user-profile): tambahkan halaman profil pengguna

- Menambahkan halaman profil yang menampilkan informasi pengguna
- Pengguna dapat mengedit foto profil
- Menambahkan fitur follow/unfollow user

Closes #45
```

### 2. Perbaikan Bug

```
fix(checkout): perbaiki error pada form pembayaran

Mengatasi issue dimana form pembayaran tidak mengirim data
ketika user menggunakan browser Safari.

Bug terjadi karena validasi email yang tidak kompatibel dengan Safari.

Closes #89
```

### 3. Update Dokumentasi

```
docs(README): update instruksi setup project

- Tambahkan requirement system yang jelas
- Perbaiki step-step instalasi yang membingungkan
- Tambahkan troubleshooting section
```

### 4. Refactoring Code

```
refactor(auth): pisahkan logika authentikasi dari controller

Memindahkan logika authentikasi dari UserController ke 
AuthService untuk meningkatkan reusability dan testability.
```

### 5. Performance Improvement

```
perf(database): gunakan connection pooling untuk DB queries

Mengurangi waktu response dari 200ms menjadi 50ms dengan
mengimplementasikan connection pooling di database layer.
```

### 6. Testing

```
test(payment): tambahkan test cases untuk payment gateway

- Test successful payment
- Test failed payment
- Test timeout handling
- Test refund process
```

### 7. Perubahan Dependencies

```
chore(dependencies): upgrade React dari v17 ke v18

- Update semua React dependencies
- Fix breaking changes di components
- Update testing library versions
```

### 8. CI/CD Configuration

```
ci(github-actions): tambahkan workflow untuk automated testing

Menambahkan GitHub Actions workflow yang:
- Menjalankan linter pada setiap pull request
- Menjalankan unit tests secara otomatis
- Generate coverage report
```

## Best Practices

### ✅ Lakukan

- **Gunakan imperative mood**: "tambahkan" bukan "ditambahkan" atau "menambahkan"
- **Jangan capitalize** huruf pertama subject: `feat: tambahkan...` bukan `feat: Tambahkan...`
- **Jangan gunakan period** di akhir subject: `feat: tambahkan fitur` bukan `feat: tambahkan fitur.`
- **Pisahkan subject dari body** dengan baris kosong
- **Wrap body** pada 72 karakter
- **Jelaskan what dan why**, bukan how
- **Reference issues** pada footer: `Closes #123`, `Fixes #456`
- **Commit yang atomic**: satu commit untuk satu perubahan logis

### ❌ Jangan Lakukan

```
# ❌ Buruk - tidak deskriptif
git commit -m "update code"

# ❌ Buruk - tanpa type
git commit -m "tambahkan halaman login"

# ❌ Buruk - type tidak valid
git commit -m "add(feature): login page"

# ❌ Buruk - terlalu banyak perubahan dalam satu commit
git commit -m "feat: tambahkan login, dashboard, dan payment"
```

### ✅ Bagus

```
git commit -m "feat(auth): tambahkan halaman login dengan OAuth"
git commit -m "fix(checkout): perbaiki validasi email di form pembayaran"
git commit -m "docs: update README dengan instruksi setup"
```

## Tools & Integrasi

### Commitizen

Tool untuk memudahkan pembuatan semantic commit message:

```bash
npm install -g commitizen
npm install --save-dev cz-conventional-changelog

# Gunakan dengan
git cz
```

### Husky + Commitlint

Otomatisasi validasi commit message:

```bash
npm install husky commitlint --save-dev

npx husky install
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"'
```

**File: `commitlint.config.js`**
```javascript
module.exports = {
  extends: ['@commitlint/config-conventional'],
};
```

### Pre-commit Hook

Validasi sebelum commit dilakukan:

```bash
npm install --save-dev @commitlint/cli
```

### Git Aliases

Buat alias untuk mempermudah:

```bash
git config --global alias.com 'commit -m'
git config --global alias.f 'fetch'
git config --global alias.p 'push'
```

## Keuntungan

### 📊 Automated Changelog

Dengan semantic commit message, changelog dapat di-generate otomatis:

```markdown
## [1.2.0] - 2024-01-15

### Added
- feat: tambahkan fitur login dengan OAuth
- feat(dashboard): tambahkan widget analytics

### Fixed
- fix: perbaiki crash saat upload gambar besar
- fix(checkout): validasi email form pembayaran

### Changed
- refactor: sederhanakan logika fungsi hitung gaji
```

### 🔄 Automated Versioning

Menggunakan Semantic Versioning (MAJOR.MINOR.PATCH):

- **MAJOR**: ketika ada breaking changes
- **MINOR**: ketika ada fitur baru yang backward compatible
- **PATCH**: ketika ada bug fix

### 🔍 Better Code Review

Reviewer dapat lebih mudah memahami intent dari perubahan melalui pesan commit yang jelas.

### 📝 Cleaner History

History commit menjadi lebih rapi dan mudah di-trace:

```bash
git log --oneline
```

Output yang terstruktur dan mudah dibaca.

### 🔄 Easier Bisecting

Mencari commit yang menyebabkan bug lebih mudah dengan konvensi yang konsisten.

## Referensi

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Commitizen](http://commitizen.github.io/cz-cli/)
- [Commitlint](https://commitlint.js.org/)

---

**Dibuat untuk membantu tim memahami dan mengimplementasikan Semantic Commit Message dengan baik.** ✨
