# XI-8 Classroom

Website kelas responsif untuk 36 siswa dan 1 guru, dengan tema biru-putih dan dark/futuristik.

## Isi
- Dashboard, data siswa (36 data contoh), absensi, jadwal, pengumuman, tugas, galeri, struktur kelas, kas, aspirasi.
- Tema dapat diganti melalui ikon setengah lingkaran.
- Halaman publik dapat dilihat semua orang; pengelolaan data memerlukan login admin guru.
- Mode demo tanpa Supabase menyimpan data sementara di browser (localStorage). Untuk akses multi-perangkat dan login sungguhan, wajib hubungkan Supabase.

## A. Hubungkan database dan login guru
1. Buat project di https://supabase.com/
2. Buka Authentication > Users, buat akun email dan password guru.
3. Buka SQL Editor, jalankan seluruh isi `supabase-setup.sql`.
4. Buka Authentication > Users, salin UUID akun guru.
5. Di SQL Editor jalankan: `insert into public.admins(user_id) values ('UUID-GURU');` (ganti dengan UUID asli).
6. Buka Project Settings > API. Salin Project URL dan anon/public key.
7. Isi nilai `SUPABASE_URL` dan `SUPABASE_ANON_KEY` di `config.js`.
8. Ganti nama contoh Siswa 01–36 di tabel `students` melalui Table Editor.

Jangan pernah menaruh `service_role` key di `config.js` atau di browser. Gunakan hanya anon/public key dengan RLS aktif.

## B. Publikasikan dengan GitHub + Netlify
1. Buat repository baru di https://github.com/new (misalnya `xi8-classroom`).
2. Upload semua file dalam folder ini ke root repository: `index.html`, `style.css`, `app.js`, `config.js`, `supabase-setup.sql`, `README.md`.
3. Buka https://app.netlify.com/ dan login.
4. Pilih **Add new site > Import an existing project**, hubungkan GitHub, lalu pilih repository `xi8-classroom`.
5. Build command kosong, Publish directory isi `.` (titik), lalu Deploy.
6. Setelah selesai, Netlify memberi alamat website. Ubah nama domain melalui **Site configuration > Change site name** jika tersedia.

## Catatan
- Website ini belum diunggah ke akun GitHub/Netlify Anda karena memerlukan akses dan persetujuan login akun Anda. Paket ini sudah disiapkan agar bisa diunggah.
- Data siswa saat ini placeholder, bukan nama siswa sebenarnya.
- Foto galeri menggunakan tautan gambar yang ditambahkan guru.
