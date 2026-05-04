# 📋 Script Pengajar — Mini Bootcamp Google Generative AI

> **Panduan penggunaan script ini:**
> - Teks dalam `[kurung kotak]` = instruksi untuk pengajar, tidak perlu diucapkan
> - Teks dalam **bold** = poin yang perlu ditekankan saat bicara
> - Estimasi waktu per slide sudah tertera
> - Bagian demo akan dihandle saat sesi hands-on, tidak perlu dijelaskan detail di sini

---

## 🎬 SLIDE 1 — Cover
### *"Experimenting with Google GenAI"*
**⏱ Estimasi: 2–3 menit**

---

Selamat datang semua di mini bootcamp hari ini!

Jadi hari ini kita bakal ngobrol, belajar, dan yang paling penting — **langsung coding** bareng-bareng soal Google Generative AI.

Kalau kalian pernah denger nama-nama kayak **ChatGPT, Gemini, atau Claude** — itu semua adalah contoh dari apa yang kita sebut *Generative AI*, atau disingkat **GenAI**. Tapi hari ini kita spesifik fokus ke **ekosistem Google** — karena Google punya tooling yang sangat lengkap dan banyak dipakai di industri.

Kita bakal cover **6 topik besar** yang kalian bisa lihat di bagian bawah slide ini:

- **Gemini 3** — model AI terbaru dari Google
- **Vision / OCR** — bikin AI bisa "melihat" dan baca gambar
- **RAG** — cara ngasih AI akses ke data kita sendiri
- **Speech** — suara jadi teks, teks jadi suara
- **On-Premise** — jalanin AI di laptop sendiri, tanpa internet
- **RecSys** — bikin sistem rekomendasi kayak Netflix atau Shopee

Nah, yang paling seru — semua topik ini ada **demo langsung** pas sesi hands-on. Jadi untuk yang masih belum familiar, jangan khawatir. Kita bakal lihat langsung kodenya berjalan.

Siap? Kita mulai!

---

## 🎬 SLIDE 2 — Agenda
### *"What We'll Cover Today"*
**⏱ Estimasi: 2 menit**

---

Ini adalah roadmap kita hari ini. Ada **6 modul** yang bakal kita bahas secara berurutan.

Setiap modul kita bakal jelasin dulu konsepnya — sekitar **5 sampai 10 menit** — terus nanti di akhir ada **sesi hands-on** di mana kalian bakal coding sendiri.

Yang perlu dicatat: kita **sengaja tidak bahas terlalu dalam** di bagian teori. Karena pengalaman gue, yang paling nempel itu justru waktu kalian udah pegang keyboard dan jalanin kodenya sendiri.

Jadi kalau ada yang bingung di bagian penjelasan, itu **wajar** — nanti akan lebih jelas begitu kita masuk demo.

Oke, langsung masuk modul pertama!

---

## 🎬 SLIDE 3 — Gemini 3 Models
### *"Gemini 3 Model Family"*
**⏱ Estimasi: 7–10 menit**

---

Modul pertama: **Gemini 3**.

Gemini adalah model AI buatan Google. Versi 3 ini adalah yang terbaru dan paling canggih yang bisa kita akses sekarang via API.

Kalian mungkin familiar dengan ChatGPT dari OpenAI — nah, **Gemini itu equivalen-nya dari Google**. Tapi ada beberapa hal yang bikin Gemini menarik, dan kita bakal bahas itu sekarang.

---

### Tiga Varian Model

Google ngerilis Gemini dalam **tiga ukuran**, dan ini penting dipahami karena kalian bakal sering dihadapkan pilihan ini ketika bikin aplikasi:

**Gemini Flash — yang paling cepat**

> *"Flash itu kayak motor bebek. Irit, gesit, dan cukup untuk sebagian besar kebutuhan sehari-hari."*

Flash itu punya **latency rendah** — artinya responnya cepat banget. Ini cocok untuk chatbot, aplikasi real-time, atau use case di mana user nggak mau nunggu lama. Harganya juga paling murah dari ketiganya.

**Gemini Pro — yang paling balanced**

> *"Pro itu kayak mobil sedan. Bisa buat harian, bisa buat jarak jauh, harga masuk akal."*

Ini adalah **pilihan default** untuk kebanyakan production use case. Kemampuannya bagus, harganya reasonable, dan cocok untuk task yang butuh reasoning lebih dalam dari Flash tapi nggak butuh kapabilitas maksimum.

**Gemini Ultra — yang paling powerful**

> *"Ultra itu kayak truk trailer. Kapasitas besar, tapi sesuaikan kebutuhan dulu."*

Ultra adalah model terkuat. Ini yang dipakai untuk task yang **benar-benar kompleks** — analisis dokumen panjang, reasoning multi-step, atau research-heavy applications.

---

### Key Capabilities di Bawah

Di bagian bawah slide, kalian lihat 5 kemampuan utama Gemini:

**Text & Chat** — ini yang paling basic. Kalian bisa kirim pertanyaan, Gemini jawab. Tapi jauh lebih dari sekadar itu.

**Multimodal** — ini yang bikin Gemini spesial. Kalian bisa kirim **gambar, video, bahkan audio** bareng teksnya. Misalnya: foto struk belanja, terus tanya "Totalnya berapa?" — Gemini bisa jawab.

**Function Calling** — ini fitur powerful yang sering dipakai di production. Gemini bisa **memanggil fungsi atau API** yang kalian definisikan sendiri. Contoh: kalian kasih tool `get_weather(city)`, nanti kalau user nanya "Cuaca Jakarta gimana?", Gemini otomatis tahu harus panggil fungsi itu.

**Long Context — 1 juta token** — ini luar biasa. Untuk konteks, 1 juta token itu setara dengan **sekitar 750 ribu kata**, atau kira-kira 10 novel tebal. Kalian bisa masukin dokumen panjang, codebase besar, atau histori percakapan yang sangat panjang.

**Code Generation** — Gemini terlatih dengan data kode dalam jumlah besar. Dia bisa generate kode, explain kode, dan debug kode dengan sangat baik.

---

`[Pause sebentar, tanya ke audience]`

> Ada yang udah pernah pakai Gemini sebelumnya, entah via Google AI Studio atau API-nya langsung?

`[Tunggu respon, lanjutkan]`

Oke, nanti di hands-on Lab 1, kalian bakal langsung bikin chatbot sederhana pakai Gemini API. Kita lanjut ke modul berikutnya.

---

## 🎬 SLIDE 4 — Google Cloud Vision API
### *"Vision & OCR"*
**⏱ Estimasi: 7–8 menit**

---

Modul kedua: **Vision dan OCR**.

Jadi pertanyaan dasarnya: **gimana cara AI "melihat"?**

Manusia kalau dikasih foto struk belanja, bisa langsung baca angkanya. Nah, komputer butuh proses khusus untuk itu — dan itulah yang kita bahas di modul ini.

Google punya dua cara utama untuk handle ini:

---

### Sisi Kiri — Google Cloud Vision API (Specialized)

**Vision API** itu adalah layanan yang **spesialis** untuk analisis gambar. Dia udah di-train khusus untuk task-task visual tertentu:

**OCR / Text Detection** — ini yang paling sering dipakai. Kalian upload gambar — bisa foto struk, scan dokumen, atau foto papan nama — dan Vision API bisa **ekstrak teks yang ada di gambar itu**. Bahkan tulisan tangan sekalipun bisa dibaca dengan akurasi tinggi.

**Object & Label Detection** — upload foto taman, Vision API bisa bilang: "Ada pohon, ada kursi, ada orang, ada anjing." Ini berguna banget untuk aplikasi seperti moderasi konten atau tagging otomatis.

**Face Detection** — bisa detect wajah, dan bahkan bisa nebak emosi — senang, sedih, kaget. Penting: ini bukan facial recognition ya, ini hanya deteksi wajah dan ekspresinya.

**Safe Search** — berguna untuk platform UGC seperti media sosial atau marketplace. Bisa detect apakah sebuah gambar mengandung konten dewasa atau kekerasan, lalu di-flag otomatis.

**Document AI** — ini level lebih advanced. Bisa parsing form, ekstrak field dari invoice, atau memahami layout dokumen yang kompleks. Ini yang biasa dipakai di perusahaan untuk automasi dokumen.

---

### Sisi Kanan — Gemini Vision (General Purpose)

Sekarang ada alternatif yang lebih modern: **Gemini Vision**.

Bedanya apa dengan Vision API?

> *"Vision API itu kayak pisau spesialis — tajam untuk tugas tertentu. Gemini Vision itu kayak chef knife serbaguna — bisa hampir segalanya."*

Dengan Gemini Vision, kalian **nggak perlu API terpisah**. Cukup kirim gambar beserta instruksi teks ke Gemini, dan dia akan prosesnya.

Contoh:
- Foto menu restoran → tanya "Rekomendasiin makanan yang enak buat vegetarian" → Gemini bisa jawab
- Foto kode di whiteboard → tanya "Translate ke Python" → Gemini bisa lakuin itu
- Foto grafik/chart → tanya "Analisis tren datanya" → Gemini bisa interpret visualnya

**Demo yang akan kita lakuin di Lab 2:** Receipt OCR → Structured JSON. Kalian foto struk belanja, dan sistem akan otomatis ekstrak semua item beserta harganya dalam format JSON yang rapi. Ini adalah use case nyata yang banyak dipakai di aplikasi keuangan.

---

## 🎬 SLIDE 5 — RAG & Embeddings
### *"RAG & Embedding Models"*
**⏱ Estimasi: 10–12 menit**

---

Modul ketiga ini adalah **salah satu yang paling penting** dan paling banyak dipakai di dunia nyata: **RAG**.

RAG itu singkatan dari **Retrieval-Augmented Generation**.

Terdengar complicated, tapi konsepnya sederhana. Gue kasih analogi dulu:

> *"Bayangin kalian lagi ujian open book. Kalian nggak harus hafal semua materi — kalian cukup tahu di buku halaman berapa jawaban itu ada, terus buka, baca, jawab. Nah, RAG itu persis kayak gitu, tapi untuk AI."*

Masalah utama LLM seperti Gemini adalah: **dia punya knowledge cutoff**. Gemini nggak tahu tentang event yang terjadi setelah tanggal training-nya. Dan yang lebih penting — **dia nggak tahu tentang data internal perusahaan kalian**.

RAG adalah solusinya.

---

### Pipeline Flow (Diagram di Atas)

Mari kita trace pipeline-nya dari kiri ke kanan:

**1. Documents** — ini adalah sumber data kalian. Bisa PDF laporan keuangan, artikel berita, dokumentasi internal, email — format apa aja.

**2. Chunk** — dokumen dipotong-potong jadi bagian kecil. Kenapa? Karena kita nggak bisa masukin seluruh dokumen sekaligus ke dalam query. Kita potong per paragraf, atau per sekian karakter.

**3. Embed** — setiap chunk diubah jadi **vector** — sekumpulan angka yang merepresentasikan *makna* dari teks itu. Di sinilah `text-embedding-004` dari Google bekerja. Satu kalimat bisa direpresentasikan sebagai 768 angka.

> *"Bayangkan setiap kalimat itu punya koordinat di ruang 768 dimensi. Kalimat yang mirip maknanya akan punya koordinat yang berdekatan."*

**4. Vector DB** — semua vector itu disimpan di database khusus yang bisa mencari berdasarkan kemiripan. Kita pakai `pgvector` di PostgreSQL, atau Pinecone, atau Supabase Vector Store.

**5. Query & Generate** — ini bagian terakhir. Ketika user nanya sesuatu, pertanyaannya juga di-embed, lalu sistem cari chunk yang paling mirip di Vector DB, ambil chunk-chunk itu, dan kasih ke Gemini sebagai konteks. Gemini lalu jawab **berdasarkan konteks yang kita kasih**, bukan hanya dari training data-nya.

---

### Kenapa Ini Penting?

Ada tiga alasan utama:

**Knowledge cutoff teratasi** — kalian bisa inject berita hari ini, dokumen terbaru, apapun — dan AI bisa jawab berdasarkan itu.

**Data privat tetap aman** — data tidak dikirim ke mana-mana selain VectorDB yang kalian kontrol sendiri. Cocok untuk dokumen internal perusahaan.

**Halusinasi berkurang drastis** — AI cenderung "mengarang" kalau nggak punya informasi yang cukup. Dengan RAG, kita kasih dia konteks yang konkret, sehingga jawaban jauh lebih akurat dan bisa di-trace ke sumbernya.

---

### Stack yang Kita Pakai

Di kanan slide kalian lihat stack-nya:
- **Gemini API** untuk embedding-nya
- **pgvector** kalau pakai PostgreSQL (atau Supabase yang built-in pgvector)
- **LangChain** atau **LlamaIndex** sebagai framework orchestration-nya

Di Lab 3 nanti, kalian bakal bikin mini RAG app — upload dokumen, sistem embed otomatis, terus kalian bisa tanya-jawab soal isi dokumen itu.

---

## 🎬 SLIDE 6 — Speech to Text & TTS
### *"Speech to Text & TTS"*
**⏱ Estimasi: 7–8 menit**

---

Modul keempat: **Speech** — dua arahnya, dari suara ke teks, dan dari teks ke suara.

Ini adalah building block penting kalau kalian mau bikin **voice assistant**, **call center AI**, atau aplikasi yang **aksesibel** untuk pengguna yang tidak bisa mengetik.

---

### Sisi Kiri — Speech-to-Text (STT)

Google Cloud Speech-to-Text v2 adalah layanan transcription mereka yang production-grade.

**125+ bahasa** — termasuk **Bahasa Indonesia**. Jadi kalian bisa langsung pakai untuk aplikasi lokal.

**Real-time streaming** — ini yang menarik. Kalian nggak harus tunggu user selesai ngomong dulu baru diproses. Sistemnya bisa transcribe sambil user masih ngomong — persis kayak live caption di YouTube atau Google Meet.

**Speaker diarization** — ini fitur yang sering dipakai di call center. Sistem bisa bedain "ini yang ngomong adalah Speaker A, ini Speaker B." Jadi kalau ada rekaman meeting dengan 5 orang, hasilnya bisa rapi: "Pak Budi: ..., Bu Sari: ..."

**Auto punctuation & word timestamps** — kalian dapat hasil yang udah ada tanda bacanya otomatis, dan setiap kata punya timestamp kapan diucapkannya. Ini berguna banget untuk fitur navigasi di video atau podcast.

**Yang menarik** — sekarang, Gemini sendiri bisa langsung terima audio sebagai input. Jadi kalian bisa kirim file audio ke Gemini dan minta dia transcribe atau langsung analisis isinya — tanpa perlu Speech-to-Text API terpisah.

---

### Sisi Kanan — Text-to-Speech (TTS)

Kebalikannya — dari teks ke suara.

Google Cloud TTS punya teknologi **WaveNet** dan **Neural2** — ini adalah suara yang dihasilkan oleh neural network, bukan pre-recorded. Hasilnya jauh lebih natural dibanding TTS generasi lama yang kedengaran robotic.

**SSML** — Speech Synthesis Markup Language. Ini adalah cara kalian *mengontrol* cara AI ngomong. Kalian bisa atur:
- Tempo bicara — lebih cepat atau lebih lambat
- Penekanan pada kata tertentu
- Jeda di tempat yang tepat
- Intonasi naik-turun

Contoh SSML: `<break time="500ms"/>` untuk jeda setengah detik, atau `<emphasis level="strong">` untuk penekanan.

**Custom Voice** — fitur paling advanced. Kalian bisa **train TTS dengan suara kalian sendiri**. Setelah training, sistem bisa generate speech yang kedengarannya seperti suara kalian. Ini dipakai brand untuk voice consistency, atau influencer yang mau scale konten.

**Gemini 2.5 Flash TTS** — perkembangan terbaru. Gemini sekarang punya TTS native — jadi satu API untuk generate teks sekaligus audionya.

Di Lab 4, kalian bakal bikin full pipeline: ngomong ke mic → transkripsi → kirim ke Gemini → jawaban Gemini dibaca balik ke kalian. Kayak voice assistant sederhana buatan sendiri.

---

## 🎬 SLIDE 7 — On-Premise Models (Gemma 4)
### *"Gemma 4 & Local LLMs"*
**⏱ Estimasi: 7–8 menit**

---

Modul kelima: **on-premise models** — atau lebih gampangnya, **AI yang jalan di laptop sendiri**.

Pertanyaan pertama yang biasanya muncul: "Ngapain repot-repot jalanin lokal kalau udah ada Gemini API yang tinggal pakai?"

Jawaban yang ada di slide ini cukup jelas:

---

### Kenapa Harus On-Premise?

**Data privacy** — ini alasan nomor satu untuk enterprise. Kalau kalian kerja di sektor perbankan, kesehatan, atau pemerintahan — ada regulasi ketat soal data tidak boleh keluar dari infrastruktur internal. Dengan local model, **tidak ada satu byte pun data yang meninggalkan server kalian**.

**Zero cost** — nggak ada API cost, nggak ada rate limit, nggak ada kuota. Sekali setup, kalian bisa query model itu **jutaan kali** tanpa bayar sepeser pun. Ini sangat menarik untuk use case dengan volume tinggi.

**Offline & air-gapped** — ada environment kerja yang memang tidak terkoneksi internet. Pabrik, fasilitas militer, kapal — semuanya butuh AI tapi tidak ada koneksi ke cloud. Local model adalah satu-satunya solusi.

**Full control** — kalian bisa fine-tune model-nya, modifikasi behavior-nya, atau customize sesuai domain kalian. Ini tidak bisa kalian lakukan dengan API dari vendor.

---

### Stack yang Dipakai

**Gemma 4** — ini adalah model open-source dari Google, available dalam tiga ukuran:
- **2B parameter** — sangat ringan, bisa jalan di laptop biasa dengan RAM 8GB
- **9B parameter** — balance antara kapabilitas dan resource
- **27B parameter** — powerful, butuh GPU atau RAM lebih besar

> *"Parameter itu kasarnya bisa dianggap sebagai 'ukuran otak' model. Lebih besar = lebih pintar, tapi lebih berat."*

**Ollama** — ini adalah tool yang bikin semua ini jadi gampang banget. Dengan satu command `ollama pull gemma4`, model udah terdownload dan siap jalan. Ollama otomatis handle format GGUF, quantization, dan expose OpenAI-compatible API.

**LM Studio** — kalau kalian prefer GUI daripada terminal, LM Studio adalah pilihan yang bagus. Bisa download, manage, dan chat dengan model lokal semua lewat interface grafis.

**OpenAI-compatible API** — ini yang bikin menarik. Ollama expose REST API yang **format-nya sama persis dengan OpenAI**. Artinya, aplikasi yang kalian bikin dengan Gemini API bisa di-switch ke local model hanya dengan ganti base URL. Zero perubahan kode.

Di Lab 5, kalian bakal pull Gemma 4 via Ollama, lalu bandingkan hasilnya dengan Gemini API untuk pertanyaan yang sama. Kalian sendiri yang bakal rasain perbedaannya.

---

## 🎬 SLIDE 8 — Recommendation System
### *"AI-Powered Recommendations"*
**⏱ Estimasi: 8–10 menit**

---

Modul terakhir — dan ini salah satu yang paling berdampak di kehidupan sehari-hari: **Recommendation System**.

Setiap hari kalian berinteraksi dengan recommendation system:
- Shopee yang tau kalian mau beli apa padahal kalian belum search
- Spotify yang rekomendasiin lagu yang cocok mood kalian
- Netflix yang tau kalian bakal nonton series apa setelah selesai satu episode

**Bagaimana sistem itu bekerja?** Ada tiga pendekatan utama.

---

### Pendekatan 1 — Collaborative Filtering (User-Based)

> *"Cari orang yang mirip dengan kamu, terus rekomendasiin apa yang mereka suka."*

Ini pendekatan klasik yang jadi fondasi recommendation system modern. Logikanya: kalau Andi dan Budi punya selera film yang sangat mirip — keduanya suka film action sci-fi dan comedy — maka kalau Budi nonton film X dan sangat suka, ada kemungkinan besar Andi juga bakal suka film X itu meskipun belum pernah nonton.

Secara teknis, ini menggunakan teknik **Matrix Factorization** seperti **SVD (Singular Value Decomposition)** — yang intinya adalah menemukan "hidden patterns" dari data rating yang sangat sparse.

Kelemahannya: butuh data historis yang cukup banyak. Kalau user baru masuk, sistem nggak tau dia mirip siapa — ini yang disebut **cold start problem**.

---

### Pendekatan 2 — Content-Based Filtering (Item-Based)

> *"Rekomendasiin item yang fitur-fiturnya mirip dengan item yang sudah kamu suka."*

Pendekatan ini nggak bergantung pada data user lain — dia fokus ke **karakteristik item itu sendiri**.

Contoh: kalian suka lagu "Coldplay - The Scientist" yang genre-nya alternative rock, tempo lambat, vokal male. Sistem akan rekomendasiin lagu lain yang punya karakteristik serupa — mungkin Radiohead, Snow Patrol, atau Keane.

Secara teknis, item bisa direpresentasikan pakai **TF-IDF** (untuk text/tag) atau lebih modern pakai **embedding**.

Keunggulannya: bisa langsung kerja bahkan untuk user baru, asalkan kita tahu preferensi awalnya.

---

### Pendekatan 3 — Semantic / LLM (AI-Native)

> *"Ini yang paling modern dan yang paling relevan untuk kita hari ini."*

Dengan LLM seperti Gemini, kita bisa representasikan item bukan hanya sebagai angka atau tag — tapi sebagai **embedding semantik** yang merepresentasikan makna yang lebih dalam.

Contoh: kalian suka produk "sepatu lari Nike Air Max untuk outdoor trail." Dengan embedding, sistem bisa menemukan produk lain yang secara makna mirip — bahkan kalau nama produknya sama sekali berbeda — karena embedding-nya akan berdekatan di vector space.

Yang lebih powerful lagi: kalian bisa **tanya Gemini langsung** — "Berikan rekomendasi produk untuk user yang suka aktivitas outdoor, budget menengah, dan preferensi brand lokal" — dan Gemini bisa berikan penjelasan yang masuk akal untuk tiap rekomendasinya.

---

### Library & Tools

Di bagian bawah ada beberapa tools:
- **Surprise** — library Python yang bagus untuk collaborative filtering (SVD, KNN)
- **Scikit-learn** — untuk content-based dan preprocessing
- **LangChain + Embeddings** — untuk semantic recommendation
- **Vertex AI Matching Engine** — kalau butuh scale ke jutaan item
- **pgvector cosine similarity** — untuk semantic search di PostgreSQL

Di Lab 6, kalian akan build movie recommender sederhana yang pakai embedding similarity. Kalian akan lihat betapa powerful-nya pendekatan semantik dibanding cara konvensional.

---

## 🎬 SLIDE 9 — Hands-On Session
### *"Time to Code!"*
**⏱ Estimasi: 2–3 menit (intro) + sesi hands-on*

---

Oke, ini dia bagian yang paling ditunggu-tunggu!

Kita punya **6 lab** yang masing-masing correspond ke modul yang baru kita bahas.

Sebelum kita mulai, beberapa hal yang perlu diperhatikan:

**Satu — Setup environment dulu.** Pastikan kalian sudah install Python, sudah punya Google AI Studio API key, dan sudah clone repo yang gue share di chat. Kalau ada yang belum, setup dulu sekarang, gue kasih waktu 5 menit.

**Dua — Kerjakan berurutan.** Lab 1 adalah fondasi. Banyak konsep di Lab 2, 3, dan seterusnya yang nge-build di atas Lab 1.

**Tiga — Jangan takut error.** Error itu bagian dari proses. Kalau stuck lebih dari 10 menit, langsung tanya. Bukan tanda bodoh — justru itu tandanya kalian udah mau coba.

**Empat — Eksplorasi itu dianjurkan.** Kalau kalian selesai satu lab lebih cepat, modifikasi kodenya. Ganti prompt-nya, tambah fitur, atau coba model yang berbeda. Itu yang bikin belajar lebih nempel.

---

`[Pause, lihat audience]`

Ada pertanyaan sebelum kita mulai sesi hands-on?

`[Jawab pertanyaan yang ada, lalu lanjutkan ke sesi lab]`

Oke — buka laptop, buka VS Code, dan let's build!

---

## 📎 Appendix: Pertanyaan yang Sering Muncul

Berikut adalah pertanyaan umum yang mungkin muncul dari peserta, beserta jawabannya:

---

**Q: Apa bedanya Gemini dengan ChatGPT?**

> Keduanya adalah Large Language Models yang powerful. Perbedaan utamanya: ChatGPT dibuat oleh OpenAI, Gemini oleh Google. Dari sisi teknis, Gemini punya context window yang lebih besar (1 juta token vs 128K token di GPT-4), dan Gemini lebih terintegrasi dengan ekosistem Google (Google Search, Google Workspace, dll). Untuk developer, pilihan sering kali bergantung pada ekosistem yang sudah dipakai tim.

---

**Q: Seberapa mahal API-nya?**

> Gemini Flash sangat murah — sekitar $0.075 per 1 juta input token. Untuk scale kecil-menengah, biayanya sangat terjangkau. Google AI Studio juga punya free tier yang cukup generous untuk development dan eksperimen. Untuk production scale besar, perlu hitung-hitung sesuai volume.

---

**Q: Apakah RAG bisa dipakai dengan model lokal (Gemma)?**

> Bisa! Pipeline RAG sebenarnya model-agnostic. Kalian bisa pakai Ollama untuk generate jawaban, dan pakai embedding model terpisah (bisa Gemini embedding, atau model embedding lokal seperti `nomic-embed-text`) untuk proses vectorization-nya. Ini adalah setup yang sangat umum di deployment enterprise yang butuh privasi data.

---

**Q: Berapa lama untuk bisa productive dengan tools ini?**

> Untuk use case dasar (chatbot, OCR, simple RAG), seseorang dengan background Python dasar bisa productive dalam **1-2 minggu** belajar serius. Yang makan waktu bukan syntax API-nya — itu cepat dipelajari — tapi memahami *bagaimana merancang sistem yang tepat* untuk problem yang dihadapi. Itulah kenapa bootcamp ini fokus ke konsep dan hands-on, bukan cuma syntax.

---

**Q: Apakah data yang kita kirim ke Gemini API aman?**

> Google punya kebijakan bahwa data yang dikirim via API tidak digunakan untuk melatih model mereka (dengan konfigurasi default). Namun untuk data yang benar-benar sensitif — rekam medis, data keuangan rahasia — rekomendasi terbaik adalah menggunakan on-premise model seperti yang kita bahas di modul Gemma 4.

---

*— End of Presenter Script —*
