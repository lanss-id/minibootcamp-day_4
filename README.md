# 🤖 Mini Bootcamp — Experimenting with Google Generative AI
### Day 4 | Hands-On & Teaching Materials

Repo ini berisi semua materi yang dibutuhkan untuk menjalankan sesi **Mini Bootcamp Google GenAI** — mulai dari script pengajar sampai kode hands-on yang siap digunakan peserta.

---

## 📁 Isi Repo

| File | Untuk Siapa | Deskripsi |
|------|-------------|-----------|
| [`script_pengajar_bootcamp_genai.md`](./script_pengajar_bootcamp_genai.md) | 👨‍🏫 Pengajar | Narasi per slide lengkap dengan estimasi waktu, analogi, dan instruksi kapan pause/tanya audience |
| [`handson_labs_bootcamp_genai.md`](./handson_labs_bootcamp_genai.md) | 👨‍💻 Peserta & Pengajar | 6 lab hands-on dengan kode Python siap jalan + tantangan bonus |

---

## 🗺️ Struktur Bootcamp

```
Teori (~64 menit)          Hands-On (~90 menit)
─────────────────          ────────────────────
Slide 1–2: Intro      →    
Slide 3: Gemini 3     →    Lab 1: Gemini Chatbot
Slide 4: Vision/OCR   →    Lab 2: Vision & OCR
Slide 5: RAG          →    Lab 3: RAG Sederhana
Slide 6: Speech       →    Lab 4: STT & TTS
Slide 7: On-Premise   →    Lab 5: Gemma via Ollama
Slide 8: RecSys       →    Lab 6: Movie Recommender
```

---

## 🧪 Lab Overview

| Lab | Topik | Tools |
|-----|-------|-------|
| **Lab 1** | Gemini Chatbot multi-turn | `google-generativeai` |
| **Lab 2** | Analisis gambar & OCR | `Pillow`, `requests` |
| **Lab 3** | RAG — tanya dokumen sendiri | `numpy`, `text-embedding-004` |
| **Lab 4** | Voice Assistant (STT + TTS) | `gTTS`, `SpeechRecognition` |
| **Lab 5** | On-premise Gemma vs Gemini | `Ollama`, `requests` |
| **Lab 6** | Movie Recommender semantik | `numpy`, `text-embedding-004` |

---

## ⚙️ Setup Sebelum Bootcamp

### 1. Install dependencies
```bash
pip install google-generativeai pillow SpeechRecognition gTTS requests scikit-learn numpy openai
```

### 2. Dapatkan API Key
Buka → [https://aistudio.google.com/apikey](https://aistudio.google.com/apikey)  
Copy API key dan paste ke setiap file lab.

### 3. Install Ollama (khusus Lab 5)
```bash
# Linux / Mac
curl -fsSL https://ollama.ai/install.sh | sh
ollama pull gemma3:2b   # ~1.6GB — cukup RAM 8GB
```
Windows: download installer di [https://ollama.ai/download](https://ollama.ai/download)

---

## 👨‍🏫 Panduan untuk Pengajar

1. Buka `script_pengajar_bootcamp_genai.md` — setiap slide sudah ada narasi siap ucap
2. Teks dalam `[kurung kotak]` adalah instruksi internal — **tidak perlu diucapkan**
3. Estimasi total teori: **~64 menit**, hands-on: **~90 menit**
4. Ada **Appendix FAQ** di akhir script untuk antisipasi pertanyaan umum peserta

---

## 👨‍💻 Panduan untuk Peserta

1. Kerjakan lab **secara berurutan** — Lab 1 adalah fondasi
2. Isi `GOOGLE_API_KEY` di setiap lab sebelum dijalankan
3. Kalau selesai lebih cepat → kerjakan **Tantangan Bonus** di tiap lab
4. Error itu wajar — kalau stuck >10 menit, tanya pengajar

---

## 🔗 Resource Tambahan

- 📘 [Gemini API Docs](https://ai.google.dev/docs)
- 🧪 [Google AI Studio](https://aistudio.google.com)
- 🖥️ [Ollama](https://ollama.ai)
- 📦 [Gemma Models](https://ai.google.dev/gemma)

---

*Dibuat untuk Mini Bootcamp internal — Day 4: Google Generative AI*
