# Konfigurasi Koneksi Navbar

Dokumen ini menjelaskan cara menghubungkan navbar antara proyek `anargya-task` dan `rsvp`.

## Cara Kerja

1. **Navbar di anargya-task**: Tombol "Mark 1.5" akan redirect ke halaman RSVP
2. **Navbar di rsvp**: Tombol "Home" akan redirect kembali ke halaman utama anargya-task

## Konfigurasi URL

### Development (Local)

Secara default, kedua proyek menggunakan:
- **anargya-task**: `http://localhost:5173`
- **rsvp**: `http://localhost:5174`

### Mengubah Port (jika diperlukan)

#### Untuk proyek rsvp:
Edit `vite.config.js`:
```js
export default defineConfig({
  plugins: [vue()],
  server: {
    port: 5174  // atau port lain yang diinginkan
  }
})
```

#### Untuk proyek anargya-task:
Edit `vite.config.js`:
```js
export default defineConfig({
  plugins: [vue()],
  server: {
    port: 5173  // atau port lain yang diinginkan
  }
})
```

### Menggunakan Environment Variable

#### Di proyek rsvp:
Buat file `.env` di root folder `rsvp`:
```
VITE_MAIN_URL=http://localhost:5173
```

#### Di proyek anargya-task:
Buat file `.env` di root folder `anargya-task`:
```
VITE_RSVP_URL=http://localhost:5174
```

### Production

Untuk production, ganti URL dengan domain yang sebenarnya:

**rsvp/.env:**
```
VITE_MAIN_URL=https://your-main-domain.com
```

**anargya-task/.env:**
```
VITE_RSVP_URL=https://your-rsvp-domain.com
```

## Cara Menjalankan

1. **Jalankan anargya-task** (terminal 1):
```bash
cd anargya-task
npm run dev
# Akan berjalan di http://localhost:5173
```

2. **Jalankan rsvp** (terminal 2):
```bash
cd rsvp
npm run dev
# Akan berjalan di http://localhost:5174
```

3. **Test koneksi**:
   - Buka `http://localhost:5173`
   - Klik tombol "Mark 1.5" di navbar → akan redirect ke `http://localhost:5174`
   - Di halaman rsvp, klik tombol "Home" → akan kembali ke `http://localhost:5173`

## Troubleshooting

### Navbar tidak redirect
- Pastikan kedua server berjalan
- Cek URL di environment variable sesuai dengan port yang digunakan
- Cek console browser untuk error

### Port sudah digunakan
- Ubah port di `vite.config.js` atau
- Tutup aplikasi lain yang menggunakan port tersebut

