# 🎬 Brand Ad Video Analyzer

> **PineOS** — Analyze any brand's advertisement video for tone, messaging, and brand consistency using AI Vision.

**Built by:** Aniket Humbe  
**Stack:** Python · OpenCV · Gemini 2.0 Flash Lite Vision · Google Colab

---

## 📌 What It Does

The **Brand Ad Video Analyzer** is an end-to-end pipeline that takes any brand advertisement video (MP4), breaks it into visual frames, and uses Google Gemini's Vision model to extract deep brand intelligence — tone, messaging, product visibility, and on-brand consistency scoring.

It outputs a structured JSON report that can power downstream brand analytics, competitive intelligence, or creative review workflows.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 🖼️ Frame Extraction | Extracts frames every N seconds using OpenCV |
| 🤖 AI Frame Analysis | Gemini Vision analyzes each frame individually |
| 🎨 Brand Intelligence | Detects tone, dominant colors, products, on-screen text |
| 📊 Consistency Scoring | Scores each frame 1–10 for brand consistency |
| 🔀 Merged Summary Report | Synthesizes all frames into a final brand intelligence report |
| 💾 JSON Export | Downloads full report as structured JSON |

---

## 🧠 How It Works

```
MP4 Video
    ↓
OpenCV Frame Extraction (every N seconds)
    ↓
Gemini 2.0 Flash Lite Vision (per-frame analysis)
    ↓  ↓  ↓  ↓  ↓
Frame Results (tone, products, text, score, colors)
    ↓
Gemini Synthesis (summary prompt)
    ↓
Final Brand Intelligence Report (JSON)
```

---

## 📦 Tech Stack

- **Python 3.10+**
- **OpenCV** (`opencv-python-headless`) — frame extraction
- **Google GenAI SDK** (`google-genai`) — Gemini 2.0 Flash Lite Vision API
- **Matplotlib** — frame grid visualization
- **Google Colab** — upload/download helpers

---

## 🔧 Setup & Usage

### 1. Open in Google Colab
Open the notebook directly: **[Brand Ad Video Analyzer on Colab](https://colab.research.google.com/drive/1p_T9xLQDeDOVLejwOxTuCwt2fsjF2_mz)**

### 2. Set your Gemini API Key
Add your API key to Colab Secrets under the name `GEMINI_API_KEY`, or paste it when prompted.

> Get a free API key at [aistudio.google.com](https://aistudio.google.com/app/apikey)

### 3. Run the Cells in Order

| Cell | Purpose |
|---|---|
| Cell 1 | Install dependencies (`opencv-python-headless`, `google-genai`) |
| Cell 2 | Load Gemini API key from Colab Secrets |
| Cell 3 | Load all functions (frame extractor, analyzer, display helpers) |
| Cell 4 | Upload your MP4 video & run full analysis |
| Cell 5 | View full JSON report |
| Cell 6 | View per-frame analysis with frame previews |
| Cell 7 | Download JSON report to your machine |

### 4. Configure Settings (Cell 4)

```python
BRAND_NAME       = "Mamaearth"   # Brand name for AI context
FRAME_INTERVAL_S = 2              # Extract 1 frame every 2 seconds
MAX_FRAMES       = 8              # Max frames to analyze (keep ≤10 for free tier)
SHOW_FRAMES_GRID = True           # Show visual frame preview grid
```

---

## 📄 Output Format

### Per-Frame Analysis
```json
{
  "timestamp_s": 4.0,
  "products_visible": ["moisturizer", "face serum"],
  "text_on_screen": "Naturally Yours",
  "dominant_colors": ["green", "white", "gold"],
  "tone": "premium",
  "scene_description": "A woman applies a product in a bright, natural setting.",
  "on_brand_score": 9,
  "notes": "Strong visual branding with nature-forward aesthetic."
}
```

### Final Summary Report
```json
{
  "brand": "Mamaearth",
  "video_duration_analyzed": "14.0s",
  "frames_analyzed": 8,
  "overall_tone": ["premium", "natural", "emotional"],
  "products_featured": ["moisturizer", "face serum", "hair oil"],
  "key_messages": ["Naturally Yours", "Goodness Inside"],
  "dominant_colors": ["green", "white", "golden"],
  "avg_on_brand_score": 8.4,
  "consistency_score": 9,
  "brand_persona_summary": "Mamaearth presents itself as a natural, toxin-free brand rooted in trust and purity...",
  "recommendations": ["Add competitive benchmarking layer", "Track tone shifts across campaign phases"],
  "frame_analysis": [...],
  "model_used": "gemini-2.0-flash-lite"
}
```

---

## ⚙️ Rate Limit Handling

The pipeline includes built-in rate limit protection for Gemini's free tier:
- **4.5-second delay** between API calls
- **Exponential backoff** with up to 4 retries (10s → 20s → 40s → 80s)
- **Frame cap** (default: 10) to stay within free quota

---

## 🛡️ Limitations

- Free Gemini tier: ~15 RPM. Keep `MAX_FRAMES ≤ 10` to avoid quota errors.
- Only MP4 format tested. Other formats may work with OpenCV but are not guaranteed.
- JSON parsing failures on individual frames are gracefully skipped.
- Large videos (>100MB) may be slow to upload in Colab.

---

## 🗺️ Roadmap Ideas

- [ ] Multi-video batch analysis for competitive benchmarking
- [ ] Auto-detect brand from video (no manual name input)
- [ ] Streamlit / web UI wrapper
- [ ] Integration with Google Sheets for campaign tracking
- [ ] Support for YouTube URL input (via yt-dlp)

---

## 👤 Author

**Aniket Humbe**  
BSc Data Science, IIT Madras · AI Trainer, Scaler AI Labs  
GitHub: [github.com/humbeaniket2006-max/Brand_Ad_Video_Analyzer](https://github.com/humbeaniket2006-max/Brand_Ad_Video_Analyzer)

---

## 📜 License

MIT License — free to use, modify, and distribute with attribution.
