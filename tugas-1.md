
# Tugas 1

## Server-Side Rendering (SSR)
Server-Side Rendering (SSR) adalah teknik rendering di mana konten halaman web dihasilkan di server saat ada permintaan dari pengguna. Server akan mengirimkan halaman HTML lengkap kepada klien. SSR memungkinkan pengguna mendapatkan konten yang siap tampil di browser tanpa menunggu JavaScript memuat terlebih dahulu. 

### Kelebihan:
- SEO lebih baik karena konten sudah tersedia saat halaman dimuat.
- Waktu muat awal (initial load) cepat pada koneksi yang baik.
- Cocok untuk aplikasi dengan konten dinamis yang berubah-ubah.

### Kekurangan:
- Beban pada server meningkat karena setiap permintaan menghasilkan proses rendering baru.
- Latensi dapat meningkat pada server dengan trafik tinggi.

---

## Static Site Generation (SSG)
Static Site Generation (SSG) adalah metode di mana konten halaman web dihasilkan selama waktu build dan disimpan dalam bentuk file statis. File ini kemudian dilayani langsung oleh server atau CDN (Content Delivery Network).

### Kelebihan:
- Sangat cepat karena file statis sudah tersedia.
- Beban server rendah karena konten tidak perlu dihasilkan secara dinamis.
- Lebih aman karena tidak ada backend aktif yang terlibat.

### Kekurangan:
- Tidak ideal untuk konten yang sering berubah karena perlu membangun ulang situs untuk setiap pembaruan.
- Konten dinamis membutuhkan solusi tambahan, seperti API.

---

## API Routes
API Routes adalah fitur yang memungkinkan pembuatan endpoint API langsung dalam aplikasi menggunakan framework seperti Next.js. File dalam direktori `pages/api` secara otomatis diperlakukan sebagai endpoint API.

### Contoh:
```javascript
// pages/api/hello.js
export default function handler(req, res) {
  res.status(200).json({ message: 'Hello, World!' });
}
```

### Kegunaan:
- Mengimplementasikan logika backend sederhana.
- Menghubungkan aplikasi dengan database atau layanan pihak ketiga.
- Menyediakan endpoint untuk aplikasi frontend.

---

## File-based Routing
File-based Routing adalah sistem routing di mana struktur file dalam direktori menentukan rute aplikasi. Framework seperti Next.js menggunakan pendekatan ini, di mana file yang ada dalam direktori `pages` secara otomatis menjadi rute.

### Contoh:
- `pages/index.js` => `/`
- `pages/about.js` => `/about`

### Kelebihan:
- Mudah dipahami karena rute sesuai dengan struktur file.
- Tidak memerlukan konfigurasi routing tambahan.

---

## Dynamic Routes
Dynamic Routes adalah fitur dalam file-based routing yang memungkinkan pembuatan rute dinamis menggunakan parameter URL. File yang menggunakan kurung siku `[]` dianggap sebagai rute dinamis.

### Contoh:
- `pages/post/[id].js` akan menangani rute seperti `/post/1` atau `/post/abc`.

### Kegunaan:
- Mengelola konten yang bergantung pada parameter, seperti halaman detail produk atau artikel.

---

## Middleware
Middleware adalah fungsi yang dijalankan di antara proses permintaan dan respons. Dalam framework seperti Next.js, middleware memungkinkan untuk menangani logika seperti autentikasi, logging, atau pengalihan sebelum permintaan mencapai endpoint atau halaman.

### Contoh:
```javascript
export function middleware(req) {
  const url = req.nextUrl.clone();
  if (!req.cookies.token) {
    url.pathname = '/login';
    return NextResponse.redirect(url);
  }
}
```

### Kegunaan:
- Autentikasi pengguna.
- Modifikasi permintaan/respons.
- Logging aktivitas pengguna.

---
