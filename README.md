<!-- ============================================================
     KATZLENS — README.md
     Made by @kas1ee
     ============================================================ -->

<div align="center">

<!-- LOGO -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=7850ff,ff3dac,00e5b0&height=200&section=header&text=KatzLens&fontSize=72&fontAlignY=38&fontColor=ffffff&desc=AI%20Content%20Detection%20·%20Prototype&descAlignY=58&descSize=18&animation=fadeIn" width="100%"/>

<!-- BADGES -->
<br/>

![Status](https://img.shields.io/badge/Status-Prototype-ff3dac?style=for-the-badge&logo=statuspage&logoColor=white)
![Type](https://img.shields.io/badge/Type-AI%20Detection-7850ff?style=for-the-badge&logo=openai&logoColor=white)
![Stack](https://img.shields.io/badge/Stack-Vanilla%20JS-00e5b0?style=for-the-badge&logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/License-Educational-ffb800?style=for-the-badge&logo=bookstack&logoColor=white)
![Made by](https://img.shields.io/badge/Made%20by-%40kas1ee-ff3dac?style=for-the-badge&logo=instagram&logoColor=white)

<br/>

> **⚠ This is a prototype project — not a real AI detector.**
> Made with ❤ by [@kas1ee](https://www.instagram.com/kas1ee)

</div>

---

## 🔍 What is KatzLens?

**KatzLens** is a browser-based AI content detection prototype that analyzes videos and URLs for signals of artificial intelligence generation, deepfakes, or synthetic manipulation — entirely on the **client side**, with zero server dependency.

Built as a passion project by **@kas1ee**, KatzLens combines heuristic frame analysis, voice spectral heuristics, metadata inspection, and a comprehensive AI keyword detection engine to produce a probabilistic AI score. Results are visual, detailed, and exportable as PDF.

<div align="center">

| Stat | Value |
|------|-------|
| 🔑 AI Keywords | 100+ |
| 📊 Detection Tiers | 4 |
| 🧪 Heuristics | 8 |
| 🌐 Platforms | 5 |
| 🖥 Server Calls | 0 |

</div>

---

## ✨ Features

<table>
<tr>
<td width="50%">

**👁 Intro Splash Animation**
Spinning dual-ring logo with fade-in brand name and animated loading bar on every launch.

**🔑 AI Keyword Engine**
100+ backend keywords across 4 tiers — auto-scans descriptions, titles, captions, and hashtags. No user input needed.

**🎬 Video Frame Analysis**
Extracts up to 16 frames from uploaded videos using Canvas API. Runs smoothness, noise, edge, and diff heuristics per frame.

**📺 Live Scan Preview**
Video plays inside the scanner with an animated scan-line overlay, corner brackets, and real-time frame thumbnail grid.

**⏱ Live Session Clock**
Session ID + real-time UTC clock ticking live in the header. PDF exports capture the exact moment of analysis.

</td>
<td width="50%">

**📊 Detailed Forensic Report**
Circular AI score meter, confidence value, 4 analysis tabs (Face, Voice, Frames, Metadata), expandable tech report.

**📄 PDF Export**
Export a full forensic report to PDF including all metrics, keyword hits, live session timestamp, and analysis summary.

**🔗 Share Report**
Share analysis results via native share sheet or copy to clipboard with one tap.

**🌐 Multi-Platform URL Support**
Detects and handles YouTube, TikTok, Instagram, X/Twitter, and Facebook URLs automatically.

**🎨 KatzLens Design System**
Custom dark UI with Syne + JetBrains Mono typography, animated particle background, glassmorphism cards.

</td>
</tr>
</table>

---

## 🏗 How It Works

```
┌─────────────────────────────────────────────────────┐
│                  KATZLENS PIPELINE                  │
└─────────────────────────────────────────────────────┘

  ① Splash & Disclaimer
     └─ Animated logo (3s) → Disclaimer modal with @kas1ee credit

  ② Input — URL or File
     └─ Paste social URL  ──OR──  Upload MP4/MOV/AVI/WEBM
        Video preview shown instantly on file upload

  ③ Keyword Phase  ← runs automatically, no user input
     └─ 100+ keyword database scans input text
        High / Medium / Hashtag / Low tiers
        Keywords animate in live during scan

  ④ Deep Analysis
     ├─ FILE MODE  → Canvas API frame extraction
     │               5 heuristics per frame:
     │               smoothness · noise · edge · frame-diff · histogram
     │
     └─ URL MODE   → Platform-weighted scoring
                     boosted by keyword hit count

  ⑤ Score Aggregation
     └─ Frame avg + keyword bonus + Gaussian variance
        → Final AI probability % + Confidence index

  ⑥ Results & Export
     └─ Circular meter · Risk badge · Keyword breakdown
        Frame strip · 4 tabs · Tech table
        → PDF Export (live timestamp) or Share
```

---

## 🔑 Keyword Detection Tiers

All keyword detection runs in the browser — no API calls, no servers. The engine checks descriptions, titles, captions, and hashtags automatically.

| Tier | Points / Hit | Example Keywords |
|------|-------------|-----------------|
| 🔴 **High Risk** | `+22 pts` | `deepfake`, `ai generated`, `stable diffusion`, `sora`, `face swap`, `voice cloning`, `synthetic media`, `midjourney`, `dall-e` |
| 🟡 **Medium** | `+10 pts` | `avatar`, `cgi`, `neural network`, `gpt`, `ai tools`, `controlnet`, `gan`, `lora trained`, `img2img` |
| 🟢 **Hashtag** | `+8 pts` | `#aiart`, `#deepfake`, `#midjourney`, `#stablediffusion`, `#texttovideo`, `#virtualinfluencer` |
| 🟣 **Low Risk** | `+4 pts` | `ai`, `digital art`, `algorithm`, `robot`, `synthetic`, `computer generated`, `automated` |

> Max keyword contribution capped at **60 pts** to prevent over-scoring on keyword-heavy content.

---

## 📁 Project Structure

```
📁 katzlens/
├── katzlens.html          ← Main app (single file, self-contained)
├── README.html            ← Animated documentation (browser)
├── README.md              ← This file
│
━━ Inside katzlens.html ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
│
├── <style>                ← All CSS (no external CSS files)
│   ├── Splash screen styles
│   ├── Disclaimer modal
│   ├── Input card & video preview
│   ├── Loading section & scanner
│   ├── Results, tabs, frame strip
│   └── Animations & responsive
│
├── <body>                 ← HTML structure
│   ├── #splash            ← Intro animation
│   ├── #disclaimer-modal
│   ├── #bg-canvas         ← Animated particle background
│   └── .wrapper
│       ├── .hero          ← Logo + live session clock
│       ├── .input-card    ← URL / File tabs
│       ├── #loading-section
│       └── #results-section
│
└── <script>               ← All JS
    ├── AI_KEYWORDS        ← Backend keyword database (100+)
    ├── detectKeywords()   ← Text scanner (all tiers)
    ├── getLiveTS()        ← Live timestamp for PDF
    ├── startLiveClock()   ← Ticking session header
    ├── startScan()        ← Main entry point
    ├── runKeywordPhase()  ← Live keyword detection
    ├── runURLAnalysis()   ← Platform-weighted scoring
    ├── runFileAnalysis()  ← Canvas frame extraction
    ├── analyzeFrame()     ← Per-frame heuristics
    ├── renderResults()    ← Full report render
    ├── downloadPDF()      ← PDF with live timestamp
    └── initBackground()   ← Particle animation
```

---

## 🚀 Usage

### Method 1 — Direct Open (simplest)

```bash
# No installation required. Just open in your browser.
open katzlens.html          # macOS
start katzlens.html         # Windows
xdg-open katzlens.html      # Linux
```

### Method 2 — Local Server (recommended for file uploads)

```bash
# Python (built-in, no install needed)
python3 -m http.server 8080

# Node.js
npx serve .

# Then open → http://localhost:8080/katzlens.html
```

### Scan a URL

1. Paste any YouTube, TikTok, Instagram, X, or Facebook video URL
2. Click **⚡ Scan**
3. KatzLens auto-detects keywords and runs platform-weighted AI scoring

### Upload a Video File

1. Switch to the **File** tab
2. Drag and drop or click to upload `.mp4` / `.mov` / `.avi` / `.webm`
3. A video preview appears instantly
4. Click **⚡ Analyze File** to run full frame-level analysis

### Read the Report

- View your **AI probability score** and **risk level badge**
- Check the **keyword detection breakdown** (high / medium / hashtag / low)
- Scroll the **frame anomaly strip** for per-frame scores
- Explore **4 analysis tabs**: Face · Voice · Frames · Metadata
- **Export to PDF** (captures exact live timestamp) or **Share**

---

## 🛠 Tech Stack

| Technology | Used For |
|-----------|----------|
| **Vanilla HTML/CSS/JS** | Zero frameworks, no bundler, pure browser APIs |
| **Canvas API** | Frame extraction, pixel heuristics, synthetic visuals, particle BG |
| **jsPDF 2.5** | Client-side PDF generation with live timestamp |
| **HTML Video API** | Seekable video for frame-accurate timestamp extraction |
| **Web Share API** | Native share sheet (mobile) + clipboard fallback (desktop) |
| **Google Fonts** | Syne (display) · JetBrains Mono (mono) · DM Sans (body) |
| **IntersectionObserver** | Scroll-reveal animations in README.html |

---

## 📊 Risk Levels

| Score | Risk Level | Meaning |
|-------|-----------|---------|
| `80–100%` | 🔴 AI Detected | Strong AI/deepfake indicators across multiple signals |
| `60–79%` | 🟠 High Risk | Several anomalies — manual review recommended |
| `40–59%` | 🟡 Suspicious | Partial AI enhancement possible — inconclusive |
| `20–39%` | 🟢 Low Risk | Minor anomalies — likely compression artifacts |
| `0–19%` | ✅ Likely Authentic | No significant AI indicators found |

---

## ⚠ Disclaimer

> **KatzLens is a prototype. It is not a real AI detector.**

All analysis is performed using **client-side heuristics and probabilistic scoring** — not machine learning models, not neural networks, not real forensic AI.

Results **must not** be used as evidence in any legal, journalistic, or investigative context. False positives and false negatives occur. Treat all output as **educational and experimental only**.

---

## 👤 Credits

<div align="center">

**Made by [@kas1ee](https://www.instagram.com/kas1ee)**

KatzLens is a solo prototype project built from scratch. The design, detection logic, keyword database, animations, and UI system were all crafted as a personal exploration of AI content detection concepts.

[![Instagram](https://img.shields.io/badge/Follow%20%40kas1ee-Instagram-ff3dac?style=for-the-badge&logo=instagram&logoColor=white)](https://www.instagram.com/kas1ee)

</div>

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=7850ff,ff3dac,00e5b0&height=120&section=footer&text=KatzLens&fontSize=28&fontColor=ffffff&animation=fadeIn" width="100%"/>

**KatzLens · AI Content Detection Prototype**
*Not for forensic use · Educational purposes only · Made by @kas1ee*

</div>
