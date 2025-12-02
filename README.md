🚍 Transjakarta Weekend Ridership Analysis — Capstone Project Modul 2

oleh Muhammad Farhan Adriansyah

Proyek ini bertujuan untuk menganalisis pola perjalanan penumpang Transjakarta pada hari weekend, mengidentifikasi area yang kurang optimal, dan menyusun rekomendasi operasional untuk meningkatkan efektivitas layanan pada hari libur.

Analisis dilakukan melalui Python (VS Code) untuk pembersihan & eksplorasi data, serta Tableau untuk pembuatan visualisasi skenario dan dashboard.

📦 1. Dataset

Dataset berisi data perjalanan harian penumpang Transjakarta berupa informasi:

Customer Identifier

Card ID → kode kartu penumpang

Pay Card Name → jenis metode pembayaran (e-money, JakCard, dll.)

Trip Identifier

Corridor ID → koridor yang digunakan

Direction → arah perjalanan (1 = pergi, 2 = pulang)

Hour → hasil ekstraksi jam dari waktu tap-in

Day Type → Weekend / Weekday

Tap In Identifier

Tap In Stops Name

Tap In Stops Lat/Lon

Tap In Time

Tap Out Identifier

Tap Out Stops Name

Tap Out Stops Lat/Lon

Tap Out Time

Calculated Fields (Feature Engineering)

Trip Duration (menit)

Hour (0–23)

Day Type (Weekend/Weekday)

🔧 2. Data Cleaning (Python)

Proses pembersihan data meliputi:

1. Missing Values

Koordinat halte kosong → drop row

Tap out time kosong → drop row

Pay Amount kosong → dianggap missing

2. Perbaikan Tipe Data

Kolom datetime → diubah menjadi datetime object

Kolom koordinat → float

Pay Amount → int

3. Feature Engineering

Ekstraksi Hour dari Tap In Time

Menghitung Trip Duration = (tapout_time - tapin_time)

Penandaan Day Type

Penandaan Corridor Category dan grouping lain

4. Filtering Data Noise

Durasi < 1 menit → drop

Durasi > 3 jam → outlier → drop

Koordinat bernilai 0 → invalid → drop

5. Validasi Identitas

Corridor ID tidak boleh kosong

Tap In/Out Stops Name harus terisi

📊 3. Exploratory Data Analysis (EDA)

EDA fokus pada:

Perbandingan volume weekday vs weekend

Pola jam sibuk weekend

Koridor dengan volume weekend terendah

Halte dengan tap-in paling sedikit

Durasi perjalanan weekend vs weekday

Hasil EDA digunakan untuk mendefinisikan 5 Research Questions (RQ).

❓ 4. Research Questions (RQ)

RQ1: Apakah jumlah perjalanan weekend lebih rendah dibanding weekday?

RQ2: Pada jam berapa weekend paling sepi?

RQ3: Koridor mana yang paling sedikit penumpangnya saat weekend?

RQ4: Halte mana yang paling rendah tap-in-nya saat weekend?

RQ5: Apakah durasi perjalanan weekend lebih lama dibanding weekday?

📈 5. Hasil Analisis & Insight
RQ1 – Weekday vs Weekend

Weekend jauh lebih rendah dibanding weekday

Weekday punya 2 jam sibuk (07:00 & 17:00)

Weekend stabil tanpa lonjakan

RQ2 – Weekend Hourly Pattern

Volume stabil pada 150–240 perjalanan/jam

Jam sepi 14.00–15.00

Puncak 08.00 & 17.00

RQ3 – Weekend by Corridor

Banyak koridor memiliki perjalanan <30/hari

Beberapa koridor masih tinggi seperti JAK 1M, D11

Koridor low-volume cocok untuk pengurangan frekuensi

RQ4 – Weekend by Stops

Karena dataset bukan nama halte asli Transjakarta, insight disesuaikan:

✔ Insight:
“Halte dengan volume weekend terendah didominasi oleh halte pinggir rute & halte feeder yang memiliki aktivitas lokal rendah.”

✔ Interpretasi:

Bisa dipertimbangkan pengurangan headway

Bisa diaktifkan melalui kerjasama event / integrasi transportasi mikro

RQ5 – Duration Weekend

Durasi weekend sedikit lebih lama dari weekday

Rata-rata 65–75 menit

Koridor dengan durasi terlama: JAK 64 & JAK 66

Jam paling lama: 08.00 dan 17.00

🚀 6. Rekomendasi Operasional

Tambah armada di jam sibuk weekend (08.00 dan 17.00)

Kurangi armada pada koridor low-volume

Lakukan aktivasi halte sepi melalui event atau promosi area

Evaluasi headway pada koridor berdurasi panjang

Memaksimalkan efisiensi operasional untuk menekan biaya

🧩 7. Teknologi yang Digunakan

Python (VS Code)

Pandas

NumPy

Matplotlib

Datetime processing

Tableau (visualisasi RQ 1–5)

GitHub (repository dokumentasi)
