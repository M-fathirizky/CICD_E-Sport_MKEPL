# E-Sports Arena - Tournament Hub System

## 1. Deskripsi Singkat Proyek
E-Sports Arena adalah sistem pendaftaran dan manajemen turnamen esports kampus berbasis Java CLI yang dibangun menggunakan Apache Maven. Aplikasi ini mendukung dua peran pengguna:

- **Admin:** Mengelola turnamen, melihat daftar peserta, dan memvalidasi pendaftaran.
- **Pemain:** Mendaftar turnamen, melihat informasi turnamen, dan mengelola data registrasi.

## 2. Arsitektur Pipeline CI/CD
Proyek ini direncanakan untuk menggunakan **GitHub Actions** sebagai pipeline CI/CD. File konfigurasi pipeline akan berada di `.github/workflows/maven.yml`.

Strategi branching yang disarankan:
- `feature/**` untuk pengembangan fitur baru
- `develop` untuk integrasi dan testing keseluruhan
- `main` sebagai branch release/production

Arsitektur pipeline mencakup komponen berikut:

- **Continuous Integration (CI):** Setiap push atau pull request ke `main`, `develop`, atau `feature/**` akan memicu GitHub Actions. Pipeline menyiapkan environment JDK 21 dan menjalankan build Maven dengan `mvn -B clean package`.
- **Continuous Testing (CT):** Setelah build berhasil, pipeline menjalankan unit test menggunakan JUnit melalui `mvn test`. Jika ada tes gagal, pipeline berhenti dan merge tidak disarankan.
- **Continuous Inspection:** Setelah build dan unit test, kode akan dianalisis secara statis untuk menjaga kualitas. Tool yang disarankan misalnya SpotBugs atau Checkstyle.
- **Continuous Delivery (CD):** Deployment dapat dipicu saat merge ke `main` setelah semua tahap berhasil. Deploy masih membutuhkan review manual sebelum rilis ke lingkungan production.

## 3. Pembagian Tugas Anggota Kelompok
| Nama | NIM | Tanggung Jawab (Fitur & Pipeline) |
|------|------|------------------------------------|
| Muhammad Fathir Rizky Salam | 103022300009 | Continuous Integration: GitHub Actions workflow, build Maven, konfigurasi project |
| Haidar Zahran Haryono | 103022330140 | Continue Testing: unit tests, `mvn test`, validasi fitur aplikasi |
| Hafizryandin Haykal Matondang | 103022300158 | Continue Inspection: static code analysis, quality gate, code review support |
| Hafizh Naufal Pradana | 103022300163 | Continuous Deployment: deployment pipeline, release artifact, GitHub Actions deploy |

## 4. Tools dan Teknologi yang Digunakan
Berikut adalah daftar teknologi yang digunakan di setiap tahapan pipeline:

- **Bahasa Pemrograman:** Java (JDK 21)
- **Package Manager & Build Tool:** Apache Maven
- **Continuous Integration & Testing:** GitHub Actions & JUnit Jupiter
- **Continuous Inspection:** SpotBugs / Checkstyle (atau tools serupa)
- **Continuous Delivery / Deployment:** GitHub Actions & GitHub Releases (jika diperlukan)

## 5. Panduan Menjalankan Proyek Secara Lokal
Untuk menjalankan proyek ini secara lokal, pastikan **Java JDK 21** dan **Maven** sudah terpasang.

1. Buka terminal di folder project.
2. Build project dan unduh dependency:
   ```powershell
   mvn clean package
   ```
3. Jalankan aplikasi:
   ```powershell
   java -jar target\esports-arena.jar
   ```
4. Jalankan unit test secara terpisah jika diperlukan:
   ```powershell
   mvn test
   ```

## Account Login
| Username | Password | Role |
|----------|----------|------|
| admin | admin123 | Admin |
| Player01 | pass01 | Pemain |
| Player02 | pass02 | Pemain |
| Player03 | pass03 | Pemain |

## Catatan
- Pastikan `pom.xml` disinkronkan di VS Code setelah melakukan perubahan.
- Gunakan `Java: Update Project Configuration` atau reload Maven project di VS Code untuk memperbarui classpath.
