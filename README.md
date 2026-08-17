# Panel Langganan BurgerBox

Panel Super Admin untuk modul langganan BurgerBox POS: memeriksa bukti transfer yang masuk,
menyetujui atau menolaknya, dan membatalkan keputusan.

## Kenapa repo ini terpisah dan publik

Terpisah dari sumber POS supaya yang tayang di GitHub Pages hanya satu berkas tampilan — bukan
seluruh kode aplikasi kasir.

Publik karena GitHub Pages gratis menuntutnya, dan itu aman: `index.html` hanya memuat kode
tampilan dan **anon key** Supabase — kunci yang memang dirancang publik dan tidak dapat membaca
apa pun, sebab RLS menyala tanpa policy di seluruh tabel.

**Yang tidak pernah ada di sini:** `service_role key`, sandi database, `CRON_SECRET`, dan kunci
privat penanda tangan lisensi.

## Kenapa URL publik ini tidak berbahaya

Yang melindungi bukan kerahasiaan alamatnya. Seluruh data datang dari Edge Function yang menuntut
JWT Supabase Auth **dan** keanggotaan tabel `admins`. Orang asing yang membuka halaman ini hanya
melihat kotak email; akun sah yang bukan admin tetap ditolak 401.

## Cara memperbarui

Jangan sunting `index.html` di sini — ia berkas turunan. Sunting templatenya di repo POS
(`billing/panel/index.template.html`), lalu jalankan `npm run panel` dari `billing/`.
