   ```
   # API QRIS Dinamis

   API untuk menghasilkan QRIS Dinamis berdasarkan jumlah nominal, biaya tambahan, dan kode QRIS statis.
   API ini memungkinkan pengguna untuk menghasilkan QRIS dengan data transaksi yang sudah ditentukan.
   ```

### 2. **Base URL**
   ```
   Base URL: https://api-qris-static-to-dynamic.vercel.app/api
   ```

### 3. **Endpoint dan Deskripsi**
   ```
   ## Endpoint: /orderkuota/cqris

   **Method:** GET

   **Deskripsi:**
   Menghasilkan QRIS Dinamis berdasarkan parameter yang diberikan seperti jumlah nominal, biaya tambahan, dan kode QRIS statis.

   **URL:**
   `https://api-qris-static-to-dynamic.vercel.app/api/orderkuota/cqris?amount=50000&fee=1000&codeqr=QRIS_CODE`

   ## Parameter:
   - `amount` (required): Jumlah nominal untuk transaksi. (contoh: 50000)
   - `fee` (required): Biaya tambahan yang dikenakan. (contoh: 1000)
   - `codeqr` (required): Kode QRIS statis yang telah ada. (contoh: "QRIS_CODE")

   **Contoh Permintaan (Request):**
   ```
   GET /api/orderkuota/cqris?amount=50000&fee=1000&codeqr=00020101021126670016COM.NOBUBANK.WWW01189360050300000879140214107456374359710303UMI51440014ID.CO.QRIS.WWW0215ID20232494105490303UMI5204511153033605802ID5912YANAMIKUBOTZ6005TEGAL61055211162070703A016304F0A6
   ```

   ### Response:
   - **status**: Status permintaan, jika berhasil akan bernilai `true`.
   - **creator**: Nama pembuat API.
   - **result**: Objek yang berisi hasil pembuatan QRIS Dinamis.
     - `amount`: Jumlah nominal yang diminta.
     - `fee`: Biaya tambahan yang dikenakan.
     - `created_at`: Tanggal dan waktu pembuatan QRIS.
     - `totalAmount`: Jumlah total setelah penambahan biaya.
     - `qrString`: String QRIS dinamis yang dihasilkan.
     - `status`: Status pembayaran (contoh: "pending").

   **Contoh Respons (Response):**
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

### 4. **Contoh Penggunaan (Usage Example)**
   **Contoh:**
   ```
   ## Contoh Penggunaan

   Untuk membuat QRIS Dinamis, Anda hanya perlu mengirim permintaan GET ke endpoint `/orderkuota/cqris` dengan parameter yang sesuai.

   **Permintaan:**
   ```bash
   GET https://api-qris-static-to-dynamic.vercel.app/api/orderkuota/cqris?amount=50000&fee=1000&codeqr=00020101021126670016COM.NOBUBANK.WWW01189360050300000879140214107456374359710303UMI51440014ID.CO.QRIS.WWW0215ID20232494105490303UMI5204511153033605802ID5912YANAMIKUBOTZ6005TEGAL61055211162070703A016304F0A6
   ```

   **Respons:**
   ```json
   {
     "status": true,
     "creator": "YanaMiku",
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

### 5. **Error Handling**
   **Contoh:**
   ```
   ## Error Handling

   ### 400 Bad Request
   Jika parameter yang diperlukan tidak lengkap atau salah, API akan mengembalikan status 400.
   
   **Pesan:**
   ```json
   {
     "status": false,
     "message": "Missing required parameters."
   }
   ```

   ### 405 Method Not Allowed
   Jika metode yang digunakan tidak diperbolehkan, API akan mengembalikan status 405.
   
   **Pesan:**
   ```json
   {
     "status": false,
     "message": "Method not allowed"
   }
   ```

   ### 500 Internal Server Error
   Jika terjadi kesalahan server, API akan mengembalikan status 500.

   **Pesan:**
   ```json
   {
     "status": false,
     "message": "Internal server error"
   }
   ```
   ```

### 6. **Kontak dan Dukungan**
   Sertakan informasi kontak jika pengguna membutuhkan bantuan lebih lanjut atau memiliki pertanyaan.

   **Contoh:**
   ```
   ## Kontak
   Untuk dukungan lebih lanjut, Anda dapat menghubungi kami di :
   - Email: support@yanamiku.xyz
   - WhatsApp: [Chat with us](https://wa.me/6285793589243)
   ```
