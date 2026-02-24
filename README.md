# Sembar Adventure – Rafting & Camping Landing Page

Landing page Next.js 15 untuk promosi paket rafting, camping, outbound, dan cafe Sembar Adventure di Sungai Cisadane, Bogor. Seluruh aset gambar disajikan lokal (`/public/assets/images`) untuk memastikan loading cepat tanpa bergantung CDN.

## Fitur
- Hero, paket harga, layanan, galeri, testimoni, dan form booking WhatsApp.
- Floating CTA WhatsApp yang langsung membuka chat dengan nomor bisnis.
- Keamanan header via `middleware.ts` (CSP, HSTS, X-Frame-Options, Permissions-Policy, dsb).
- Typography memakai font sistem (tidak perlu fetch Google Fonts).

## Prasyarat
- Node.js 18+ (disarankan 20+)
- npm

## Menjalankan di lokal
1. Instal dependensi  
   ```bash
   npm install
   ```
2. Siapkan environment file `.env.local` (salin dari `.env.example`) dan isi:
   - `NEXT_PUBLIC_WHATSAPP_NUMBER` — nomor bisnis diawali kode negara, hanya digit (contoh: 62812xxxxxxx).
   - `NEXT_PUBLIC_CONTACT_EMAIL` — email publik untuk footer.
   - `GEMINI_API_KEY` — hanya diperlukan jika Anda memakai integrasi Gemini di masa depan (aman dibiarkan kosong untuk landing page ini).
3. Jalankan dev server  
   ```bash
   npm run dev
   ```
   Akses di http://localhost:3000

## Build & start produksi
```bash
npm run build
npm start         # atau: node .next/standalone/server.js jika output standalone dipertahankan
```

## Catatan keamanan & privasi
- Tidak ada nomor/email hardcode di kode; semua via env vars di atas.
- CSP membatasi sumber ke `self`, data:, dan blob: untuk gambar; jika menambah domain pihak ketiga (misal CDN atau analytics), perlu ditambahkan ke header di `middleware.ts`.
- Embed peta menggunakan iframe Google Maps; tidak menyertakan kunci API.

## Struktur penting
- `app/page.tsx`      – halaman utama.
- `components/*`      – komponen UI (Hero, Packages, Services, Gallery, BookingForm, Footer, Navbar).
- `public/assets/images` – gambar lokal (.webp).
- `middleware.ts`     – header keamanan.
- `next.config.ts`    – konfigurasi Next (standalone output, remotePatterns untuk image placeholders).

## Lisensi
Gunakan sesuai kebutuhan proyek; pastikan mematuhi lisensi gambar dan font yang Anda tambahkan sendiri.
