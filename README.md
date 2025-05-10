# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Edutech

## Business Understanding
Jaya Jaya Institut merupakan institusi pendidikan tinggi yang telah berdiri sejak tahun 2000 dan memiliki reputasi baik dalam mencetak lulusan. Namun, mereka menghadapi masalah serius berupa tingginya angka mahasiswa yang dropout (tidak menyelesaikan studi). Hal ini berpotensi menurunkan citra dan akreditasi institusi. Oleh karena itu, institusi ingin mendeteksi lebih awal mahasiswa yang berpotensi dropout agar bisa diberikan intervensi atau bimbingan khusus.

### Permasalahan Bisnis
1. Tingginya jumlah mahasiswa yang tidak menyelesaikan pendidikan (dropout).
2. Belum adanya sistem yang dapat memprediksi kemungkinan seorang mahasiswa akan dropout berdasarkan data historis mereka.
3. Kebutuhan akan dashboard yang informatif untuk memantau performa dan status mahasiswa.

### Cakupan Proyek
1. Melakukan eksplorasi dan analisis terhadap data mahasiswa.
2. Membangun sistem machine learning untuk memprediksi status mahasiswa (aktif, lulus, atau dropout).
3. Membuat dashboard visualisasi yang menampilkan statistik penting dari data mahasiswa.

### Persiapan

Sumber data: (https://github.com/Ezraliano/submission_akhir_data_science_final1/blob/main/data.csv)

## Set Up Metabase:
1. Jalankan perintah berikut pada Terminal/Command Prompt/PowerShell guna memanggil (pull) Docker image untuk menjalankan Metabase.
docker pull metabase/metabase:v0.54.3.
2. docker run -p 3000:3000 --name jaya-jaya_institute metabase/metabase
3. http://localhost:3000/setup
4. Metabase akun : root@gmail.com
    password : root123
5. Pada Halaman Home Metabase, pilih jaya-jaya dashboard untuk mengakses dashboard yang telah dibuat.

## Set Up Environment
1. pip install pandas sqlalchemy

## Set Up Database di Supabase
1. Create New Project
2. Mengirim Dataset ke supabase 
from sqlalchemy import create_engine
 
URL = "postgresql://postgres:[YOUR-PASSWORD]@db.hhjaouxzsxzsvvkauicu.supabase.co:5432/postgres"
 
engine = create_engine(URL)
df.to_sql('orders', engine)

3. Kemudian gunakan transaction pooler untuk menghubungkan supabase dengan metabase

postgresql://postgres.hhjaouxzsxzsvvkauicu:[YOUR-PASSWORD]@aws-0-ap-southeast-1.pooler.supabase.com:6543/postgres

## Business Dashboard
Berikut Link untuk mengakses dashboard "http://localhost:3000/dashboard/2-jaya-jaya-institute-dashboard"
Dataset ini memiliki .. kolom, berikut penjelasannya :
1. Marital status : Status perkawinan mahasiswa
2. Application mode : Metode aplikasi yang digunakan oleh siswa.
3. Application order : Urutan pendaftaran siswa
4. Course : Kursus yang diambil oleh siswa.
5. Daytime/evening attendance : Apakah siswa menghadiri kelas pada siang hari atau malam hari.
6. Previous qualification : Kualifikasi yang diperoleh siswa sebelum mendaftar di pendidikan tinggi.
7. Previous qualification (grade) : Nilai kualifikasi sebelumnya (antara 0 dan 200)
8. Nacionality : Kebangsaan siswa.
9. Mother's qualification : Kualifikasi ibu siswa.
10. Father's qualification : Kualifikasi ayah siswa.
11. Admission grade : Nilai penerimaan (antara 0 dan 200)
12. Displaced : Apakah siswa tersebut merupakan orang terlantar.
13. Educational special needs : Apakah siswa tersebut memiliki kebutuhan pendidikan khusus.
14. Debtor : Apakah mahasiswa tersebut seorang debitur.
15. Tuition fees up to date : Apakah biaya kuliah siswa sudah sesuai dengan ketentuan yang berlaku.
16. Gender : Jenis kelamin siswa.
17. Scholarship holder : Apakah siswa tersebut merupakan pemegang beasiswa.
18. Age at enrollment : Usia siswa pada saat mendaftar.
19. International : Apakah siswa tersebut merupakan siswa internasional.
20. Curricular units 1st sem (credited) : Jumlah satuan mata kuliah yang dikreditkan oleh mahasiswa pada semester pertama
21. Curricular units 1st sem (enrolled) : Jumlah satuan kurikulum yang diambil oleh mahasiswa pada semester pertama.
22. Curricular units 1st sem (evaluations) : Jumlah satuan kurikulum yang dievaluasi oleh mahasiswa pada semester pertama.
23. Curricular units 1st sem (approved) : Jumlah satuan kurikulum yang disetujui oleh mahasiswa pada semester pertama.

Penjelasan Model Dashboard 
Deskripsi :
Dashboard yang telah dibuat memvisualisasikan:
1. Proporsi mahasiswa berdasarkan status (aktif, dropout, lulus)
2. Jumlah pemegang beasiswa berdasarkan status.
3. Perbandingan nilai akademik dan nilai admission berdasarkan status mahasiswa



## Menjalankan Sistem Machine Learning
Sistem ini dibangun menggunakan model Random Forest yang dikombinasikan dengan teknik preprocessing dan oversampling menggunakan SMOTE. Aplikasi prototipe dapat dijalankan secara lokal maupun online dengan Streamlit.
Untuk menjalankan aplikasi dapat menggunakan perintah berikut :
streamlit run app.py


## Conclusion
Model machine learning yang dibangun mampu memprediksi status mahasiswa berdasarkan atribut historis mereka seperti nilai akademik, admission grade, dan jumlah SKS. Dashboard yang dibuat memberikan insight visual yang membantu pihak manajemen dalam memantau performa mahasiswa dan mengambil keputusan strategis.

### Rekomendasi Action Items
Berikut merupakan beberapa rekomendasi action Items :
1. Bangun Program Intervensi Dini
- memberikan mentoring, konseling, atau pelatihan tambahan kepada mahasiswa dengan nilai akademik rendah atau tidak memiliki beasiswa.
2. Perbaiki Dukungan Akademik bagi Mahasiswa dengan Nilai Akademik Rendah
- Sediakan program remedial, tutoring, atau akademik coaching bagi mahasiswa dengan nilai akademik semester awal.
- Berikan pelatihan belajar efektif atau manajemen waktu pada awal tahun akademik.
3. Monitoring Ketat Terhadap Mahasiswa Aktif yang Berisiko
- Melakukan implementasi pendekatan advising berbasis data, di mana dosen wali dapat melihat histori risiko mahasiswa per semester.
- Melakukan follow-up rutin dengan mahasiswa aktif yang menunjukkan penurunan performa.
