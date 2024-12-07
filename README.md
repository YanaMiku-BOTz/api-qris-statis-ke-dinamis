# Dokumentasi API QRIS Dinamis

API ini memungkinkan Anda untuk mengonversi kode QRIS statis menjadi kode QRIS dinamis, yang dapat digunakan untuk transaksi pembayaran dengan menambahkan jumlah dan biaya layanan. API ini akan menerima parameter tertentu dan menghasilkan QRIS dinamis yang siap digunakan.

## Base URL

`https://api-qris-static-to-dynamic.vercel.app`

## Endpoint

### 1. `GET /api/orderkuota/cqris`

Endpoint ini digunakan untuk menghasilkan QRIS dinamis berdasarkan jumlah yang ditentukan, biaya tambahan (jika ada), dan kode QRIS statis.

#### URL Request

```
GET https://api-qris-static-to-dynamic.vercel.app/api/orderkuota/cqris?amount=50000&fee=1000&codeqr=QRIS_CODE
```

#### Parameter

- **amount** (required): Jumlah yang akan dibayar. Harus dalam format angka (misalnya, 50000).
- **fee** (required): Biaya tambahan yang akan dikenakan pada pembayaran. Harus dalam format angka (misalnya, 1000).
- **codeqr** (required): Kode QRIS statis yang ingin digunakan sebagai dasar untuk menghasilkan QRIS dinamis. Kode ini harus dalam format QRIS yang valid.

#### Contoh Request

```
GET https://api-qris-static-to-dynamic.vercel.app/api/orderkuota/cqris?amount=50000&fee=1000&codeqr=00020101021126670016COM.NOBUBANK.WWW01189360050300000879140214107456374359710303UMI51440014ID.CO.QRIS.WWW0215ID20232494105490303UMI5204511153033605802ID5912YANAMIKUBOTZ6005TEGAL61055211162070703A016304F0A6
```

#### Contoh Response

Jika permintaan berhasil, Anda akan menerima respons JSON yang berisi informasi tentang transaksi dan QRIS dinamis yang dihasilkan.

```json
{
  "status": true,
  "creator": "YanaMiku",
  "mess": "Berhasil Membuat QRIS",
  "result": {
    "amount": 50000,
    "fee": 1000,
    "created_at": "2024-12-07T12:34:56.789Z",
    "totalAmount": 51000,
    "qrString": "00020101021226670016COM.NOBUBANK.WWW01189360050300000879140214107456374359710303UMI51440014ID.CO.QRIS.WWW0215ID20232494105490303UMI520451115303360540411155802ID5912YANAMIKUBOTZ6005TEGAL61055211162070703A01630443FF",
    "status": "pending"
  }
}
```

#### Penjelasan Response

- **status**: Status dari permintaan. `true` berarti permintaan berhasil, `false` berarti ada kesalahan.
- **creator**: Nama pembuat API.
- **result**:
  - **amount**: Jumlah yang diminta untuk pembayaran.
  - **fee**: Biaya tambahan yang ditambahkan ke jumlah pembayaran.
  - **created_at**: Waktu ketika QRIS dinamis dibuat (Asia/Jakarta).
  - **totalAmount**: Total jumlah pembayaran yang termasuk biaya tambahan.
  - **qrString**: QRIS dinamis yang dihasilkan dalam format string.
  - **status**: Status transaksi, misalnya `pending` jika status pembayaran belum selesai.

#### Status Error

Jika ada kesalahan dalam permintaan, API akan mengembalikan respons dengan status `false` dan pesan error yang relevan.

Contoh respons kesalahan:

```json
{
  "status": false,
  "message": "Parameter yang diperlukan tidak lengkap."
}
```

### 2. Metode HTTP yang Didukung

- **GET**: Digunakan untuk mengambil data QRIS dinamis berdasarkan parameter yang diberikan.

### 3. Error Handling

Jika API menerima permintaan yang tidak lengkap atau parameter yang salah, API akan mengembalikan pesan kesalahan dengan status `false` dan penjelasan tentang kesalahan tersebut. Berikut adalah beberapa contoh kesalahan yang mungkin terjadi:

- **400 Bad Request**: Parameter yang diperlukan tidak lengkap atau salah format.
- **405 Method Not Allowed**: Metode HTTP yang digunakan tidak didukung (misalnya, menggunakan `POST` bukannya `GET`).

## Contoh Penggunaan API

Untuk menggunakan API ini, Anda dapat mengirimkan permintaan HTTP `GET` ke endpoint berikut dengan menyertakan parameter yang diperlukan:

```
GET https://api-qris-static-to-dynamic.vercel.app/api/orderkuota/cqris?amount=50000&fee=1000&codeqr=QRIS_CODE
```

API akan mengembalikan QRIS dinamis yang dapat dipindai untuk melakukan pembayaran dengan jumlah yang telah ditentukan.

---

Jika ada pertanyaan lebih lanjut atau jika Anda mengalami kesulitan, silakan hubungi kami di [ WhatsApp ](https://wa.me/6285793589243).

Jangan Lupa Klik Star🌟 & Follow yaaa!

---

### Penjelasan tambahan:
1. **Akses API**: API ini dapat diakses publik, namun Anda bisa menambahkan autentikasi jika diperlukan untuk akses yang lebih aman.
2. **Penggunaan dalam Aplikasi**: Anda bisa menggunakan API ini dalam aplikasi atau platform pembayaran yang membutuhkan QRIS dinamis untuk transaksi.
