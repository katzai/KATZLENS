<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>KatzLens — README</title>
<style>
@import url('https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=JetBrains+Mono:wght@300;400;500;600&family=DM+Sans:ital,wght@0,300;0,400;0,500;0,600;1,400&display=swap');

:root {
  --bg:       #05070f;
  --bg2:      #080b1c;
  --surface:  rgba(12,10,30,0.85);
  --border:   rgba(120,80,255,0.18);
  --accent:   #7850ff;
  --pink:     #ff3dac;
  --teal:     #00e5b0;
  --warn:     #ffb800;
  --text:     #e8e0ff;
  --dim:      #4a4270;
  --glow:     0 0 40px rgba(120,80,255,0.25);
  --glow-p:   0 0 40px rgba(255,61,172,0.2);
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: 'DM Sans', sans-serif;
  font-size: 16px;
  line-height: 1.7;
  overflow-x: hidden;
}

/* ── ANIMATED BG ── */
body::before {
  content: '';
  position: fixed; inset: 0; z-index: 0;
  background:
    radial-gradient(ellipse 80% 50% at 10% 20%, rgba(120,80,255,0.07) 0%, transparent 60%),
    radial-gradient(ellipse 60% 40% at 90% 80%, rgba(255,61,172,0.06) 0%, transparent 60%),
    radial-gradient(ellipse 50% 60% at 50% 50%, rgba(0,229,176,0.03) 0%, transparent 70%);
  pointer-events: none;
}

/* Animated grid overlay */
body::after {
  content: '';
  position: fixed; inset: 0; z-index: 0;
  background-image:
    linear-gradient(rgba(120,80,255,0.025) 1px, transparent 1px),
    linear-gradient(90deg, rgba(120,80,255,0.025) 1px, transparent 1px);
  background-size: 64px 64px;
  pointer-events: none;
  animation: gridDrift 20s linear infinite;
}
@keyframes gridDrift {
  0%   { transform: translate(0,0); }
  100% { transform: translate(64px, 64px); }
}

/* ── CANVAS PARTICLES ── */
#particles {
  position: fixed; inset: 0; z-index: 0;
  pointer-events: none;
}

/* ── WRAPPER ── */
.wrap {
  position: relative; z-index: 1;
  max-width: 900px;
  margin: 0 auto;
  padding: 0 28px 120px;
}

/* ── HERO HEADER ── */
.hero {
  padding: 90px 0 60px;
  text-align: center;
}

.logo-anim {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 90px; height: 90px;
  margin: 0 auto 28px;
}
.logo-ring {
  position: absolute; inset: 0;
  border-radius: 50%;
  border: 1.5px solid transparent;
}
.logo-ring-1 {
  background: linear-gradient(var(--bg), var(--bg)) padding-box,
    linear-gradient(135deg, var(--accent), var(--pink)) border-box;
  animation: spin 4s linear infinite;
}
.logo-ring-2 {
  inset: 10px;
  background: linear-gradient(var(--bg), var(--bg)) padding-box,
    linear-gradient(135deg, var(--pink), var(--teal)) border-box;
  animation: spin 2.5s linear infinite reverse;
}
@keyframes spin { to { transform: rotate(360deg); } }

.logo-eye {
  position: relative; z-index: 2;
  width: 44px; height: 44px;
}
.logo-eye svg { width: 100%; height: 100%; }

.hero-title {
  font-family: 'Syne', sans-serif;
  font-size: clamp(3rem, 8vw, 5.5rem);
  font-weight: 800;
  background: linear-gradient(135deg, #c0a8ff 0%, var(--accent) 40%, var(--pink) 80%);
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -2px;
  line-height: 1;
  margin-bottom: 16px;
  opacity: 0;
  animation: fadeSlideUp 0.8s 0.2s cubic-bezier(0.4,0,0.2,1) forwards;
}
.hero-sub {
  font-family: 'JetBrains Mono', monospace;
  font-size: clamp(0.7rem, 2vw, 0.85rem);
  color: var(--dim);
  letter-spacing: 5px;
  text-transform: uppercase;
  margin-bottom: 32px;
  opacity: 0;
  animation: fadeSlideUp 0.7s 0.4s cubic-bezier(0.4,0,0.2,1) forwards;
}

.badges {
  display: flex; flex-wrap: wrap; gap: 8px;
  justify-content: center;
  margin-bottom: 40px;
  opacity: 0;
  animation: fadeSlideUp 0.7s 0.6s cubic-bezier(0.4,0,0.2,1) forwards;
}
.badge {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 5px 14px;
  border-radius: 50px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.7rem;
  letter-spacing: 1px;
  border: 1px solid;
  transition: all 0.25s;
}
.badge:hover { transform: translateY(-2px); }
.badge-purple { border-color: rgba(120,80,255,0.4); color: #a080ff; background: rgba(120,80,255,0.08); }
.badge-pink   { border-color: rgba(255,61,172,0.4); color: var(--pink); background: rgba(255,61,172,0.07); }
.badge-teal   { border-color: rgba(0,229,176,0.35); color: var(--teal); background: rgba(0,229,176,0.07); }
.badge-warn   { border-color: rgba(255,184,0,0.35);  color: var(--warn); background: rgba(255,184,0,0.07); }

.scan-line-hero {
  width: 100%; height: 1px;
  background: linear-gradient(90deg, transparent, var(--accent), var(--pink), transparent);
  margin: 0 auto;
  opacity: 0;
  animation: fadeSlideUp 0.6s 0.8s ease forwards;
  box-shadow: 0 0 12px var(--accent), 0 0 30px rgba(120,80,255,0.2);
}

/* ── SECTIONS ── */
.section {
  margin: 60px 0;
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.section.visible {
  opacity: 1;
  transform: translateY(0);
}

.section-label {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  color: var(--accent);
  letter-spacing: 5px;
  text-transform: uppercase;
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  gap: 10px;
}
.section-label::before {
  content: '';
  display: block;
  width: 24px; height: 1px;
  background: var(--accent);
  box-shadow: 0 0 8px var(--accent);
}

.section-title {
  font-family: 'Syne', sans-serif;
  font-size: clamp(1.4rem, 4vw, 2rem);
  font-weight: 800;
  color: var(--text);
  letter-spacing: -0.5px;
  margin-bottom: 20px;
  line-height: 1.2;
}
.section-title span {
  background: linear-gradient(135deg, var(--accent), var(--pink));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
}

/* ── CARD ── */
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 18px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  padding: 28px 30px;
  transition: border-color 0.3s, box-shadow 0.3s;
  position: relative;
  overflow: hidden;
}
.card::before {
  content: '';
  position: absolute; top: 0; left: 0; right: 0; height: 1px;
  background: linear-gradient(90deg, transparent, rgba(120,80,255,0.4), transparent);
  opacity: 0;
  transition: opacity 0.3s;
}
.card:hover { border-color: rgba(120,80,255,0.35); box-shadow: var(--glow); }
.card:hover::before { opacity: 1; }

/* ── FEATURE GRID ── */
.feature-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
  gap: 16px;
}
.feature-card {
  background: rgba(10,8,28,0.7);
  border: 1px solid rgba(120,80,255,0.12);
  border-radius: 14px;
  padding: 22px;
  transition: all 0.3s;
  cursor: default;
}
.feature-card:hover {
  border-color: rgba(120,80,255,0.35);
  background: rgba(20,12,50,0.8);
  transform: translateY(-3px);
  box-shadow: var(--glow);
}
.feature-icon {
  font-size: 1.8rem;
  margin-bottom: 12px;
  display: block;
  filter: drop-shadow(0 0 8px rgba(120,80,255,0.5));
}
.feature-name {
  font-family: 'Syne', sans-serif;
  font-size: 1rem; font-weight: 700;
  color: var(--text);
  margin-bottom: 6px;
}
.feature-desc {
  font-size: 0.88rem;
  color: rgba(232,224,255,0.5);
  line-height: 1.6;
}

/* ── CODE BLOCK ── */
.code-block {
  background: rgba(0,0,0,0.6);
  border: 1px solid rgba(120,80,255,0.15);
  border-radius: 12px;
  overflow: hidden;
}
.code-header {
  display: flex; align-items: center; justify-content: space-between;
  padding: 10px 16px;
  background: rgba(120,80,255,0.07);
  border-bottom: 1px solid rgba(120,80,255,0.1);
}
.code-dots { display: flex; gap: 6px; }
.code-dots span {
  width: 10px; height: 10px; border-radius: 50%;
}
.d1 { background: #ff5f57; }
.d2 { background: #ffbc2e; }
.d3 { background: #28c840; }
.code-lang {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  color: var(--dim);
  letter-spacing: 2px;
  text-transform: uppercase;
}
.code-body {
  padding: 20px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.82rem;
  line-height: 1.9;
  color: rgba(232,224,255,0.75);
  overflow-x: auto;
}
.code-body .kw  { color: var(--pink); }
.code-body .str { color: var(--teal); }
.code-body .cm  { color: var(--dim); }
.code-body .fn  { color: #a080ff; }
.code-body .num { color: var(--warn); }

/* ── TIMELINE ── */
.timeline { position: relative; padding-left: 28px; }
.timeline::before {
  content: '';
  position: absolute; left: 8px; top: 8px; bottom: 8px; width: 1px;
  background: linear-gradient(to bottom, var(--accent), var(--pink), transparent);
}
.timeline-item {
  position: relative;
  margin-bottom: 28px;
}
.timeline-item::before {
  content: '';
  position: absolute; left: -24px; top: 6px;
  width: 9px; height: 9px;
  border-radius: 50%;
  background: var(--accent);
  box-shadow: 0 0 10px var(--accent);
}
.timeline-title {
  font-family: 'Syne', sans-serif;
  font-size: 1rem; font-weight: 700;
  color: var(--text);
  margin-bottom: 5px;
}
.timeline-desc {
  font-size: 0.9rem;
  color: rgba(232,224,255,0.5);
  line-height: 1.65;
}

/* ── KW TABLE ── */
.kw-table {
  width: 100%; border-collapse: collapse;
}
.kw-table th {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 3px;
  text-transform: uppercase;
  color: var(--dim);
  padding: 10px 14px;
  text-align: left;
  border-bottom: 1px solid rgba(120,80,255,0.1);
}
.kw-table td {
  padding: 10px 14px;
  font-size: 0.88rem;
  border-bottom: 1px solid rgba(120,80,255,0.05);
  vertical-align: middle;
}
.kw-table tr:last-child td { border: none; }
.kw-table tr:hover td { background: rgba(120,80,255,0.04); }

.tier-chip {
  display: inline-block;
  padding: 2px 10px;
  border-radius: 50px;
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  letter-spacing: 1px;
}
.tier-h { background: rgba(255,61,94,0.15);  border: 1px solid rgba(255,61,94,0.3);  color: #ff3d5e; }
.tier-m { background: rgba(255,184,0,0.12);  border: 1px solid rgba(255,184,0,0.3);  color: var(--warn); }
.tier-l { background: rgba(120,80,255,0.12); border: 1px solid rgba(120,80,255,0.3); color: #a080ff; }
.tier-t { background: rgba(0,229,176,0.1);   border: 1px solid rgba(0,229,176,0.25); color: var(--teal); }

/* ── STAT ROW ── */
.stat-row {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
  gap: 14px;
  margin-top: 0;
}
.stat-item {
  background: rgba(0,0,0,0.4);
  border: 1px solid rgba(120,80,255,0.12);
  border-radius: 12px;
  padding: 18px 16px;
  text-align: center;
  transition: all 0.3s;
}
.stat-item:hover {
  border-color: rgba(120,80,255,0.3);
  transform: translateY(-2px);
}
.stat-num {
  font-family: 'Syne', sans-serif;
  font-size: 2rem; font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--pink));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  line-height: 1;
  margin-bottom: 6px;
}
.stat-lbl {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.62rem;
  color: var(--dim);
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* ── DISCLAIMER BOX ── */
.disclaimer-box {
  border-left: 3px solid var(--pink);
  background: rgba(255,61,172,0.05);
  border-radius: 0 12px 12px 0;
  padding: 18px 22px;
}
.disclaimer-box p {
  font-size: 0.9rem;
  color: rgba(232,224,255,0.6);
  line-height: 1.7;
}
.disclaimer-box p + p { margin-top: 10px; }
.disclaimer-box strong { color: var(--text); }
.disclaimer-box a {
  color: var(--pink);
  text-decoration: none;
  font-weight: 600;
  padding: 1px 7px;
  background: rgba(255,61,172,0.1);
  border-radius: 4px;
  border: 1px solid rgba(255,61,172,0.25);
  transition: all 0.2s;
}
.disclaimer-box a:hover { background: rgba(255,61,172,0.2); }

/* ── CREDITS ── */
.credits-card {
  position: relative;
  overflow: hidden;
}
.credits-card::after {
  content: '';
  position: absolute; inset: 0;
  background:
    radial-gradient(ellipse 60% 60% at 100% 100%, rgba(255,61,172,0.08) 0%, transparent 70%),
    radial-gradient(ellipse 50% 50% at 0% 0%, rgba(120,80,255,0.08) 0%, transparent 70%);
  pointer-events: none;
}
.credits-inner { position: relative; z-index: 1; }
.credits-name {
  font-family: 'Syne', sans-serif;
  font-size: 1.8rem; font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--pink));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 4px;
}
.credits-handle {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.8rem;
  color: var(--dim);
  letter-spacing: 2px;
  margin-bottom: 16px;
}
.credits-desc {
  font-size: 0.92rem;
  color: rgba(232,224,255,0.55);
  line-height: 1.7;
  max-width: 480px;
  margin-bottom: 20px;
}
.insta-btn {
  display: inline-flex; align-items: center; gap: 10px;
  padding: 12px 24px;
  background: linear-gradient(135deg, rgba(120,80,255,0.2), rgba(255,61,172,0.2));
  border: 1px solid rgba(255,61,172,0.4);
  border-radius: 50px;
  color: var(--pink);
  font-family: 'Syne', sans-serif;
  font-size: 0.9rem; font-weight: 700;
  text-decoration: none;
  letter-spacing: 0.5px;
  transition: all 0.3s;
  position: relative;
  overflow: hidden;
}
.insta-btn::before {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(135deg, rgba(255,61,172,0.25), rgba(120,80,255,0.15));
  opacity: 0; transition: opacity 0.3s;
}
.insta-btn:hover { box-shadow: var(--glow-p); transform: translateY(-2px); }
.insta-btn:hover::before { opacity: 1; }
.insta-icon {
  font-size: 1.1rem;
  filter: drop-shadow(0 0 6px rgba(255,61,172,0.6));
}

/* ── FOOTER ── */
.footer {
  text-align: center;
  padding: 40px 0 20px;
  border-top: 1px solid rgba(120,80,255,0.08);
  margin-top: 60px;
}
.footer-logo {
  font-family: 'Syne', sans-serif;
  font-size: 1.4rem; font-weight: 800;
  background: linear-gradient(135deg, var(--accent), var(--pink));
  -webkit-background-clip: text; -webkit-text-fill-color: transparent;
  background-clip: text;
  margin-bottom: 8px;
}
.footer-note {
  font-family: 'JetBrains Mono', monospace;
  font-size: 0.65rem;
  color: var(--dim);
  letter-spacing: 2px;
  text-transform: uppercase;
}

/* ── ANIMATED SCAN LINE (page) ── */
.page-scan {
  position: fixed; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(120,80,255,0.4), rgba(255,61,172,0.4), transparent);
  pointer-events: none;
  z-index: 9999;
  animation: pageScan 6s linear infinite;
  opacity: 0.6;
}
@keyframes pageScan {
  0%   { top: -2px; }
  100% { top: 100vh; }
}

/* ── TYPING ANIMATION ── */
.typing {
  display: inline-block;
  overflow: hidden;
  white-space: nowrap;
  border-right: 2px solid var(--accent);
  animation: typing 2.5s steps(30) 1s both, blink 0.7s step-end 3.5s infinite;
}
@keyframes typing { from { width: 0; } to { width: 100%; } }
@keyframes blink { 50% { border-color: transparent; } }

/* ── FADE ANIMATIONS ── */
@keyframes fadeSlideUp {
  from { opacity: 0; transform: translateY(20px); }
  to   { opacity: 1; transform: translateY(0); }
}
@keyframes pulseDot {
  0%, 100% { box-shadow: 0 0 6px var(--teal); }
  50%       { box-shadow: 0 0 14px var(--teal), 0 0 28px rgba(0,229,176,0.3); }
}

/* ── SCROLLBAR ── */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: rgba(120,80,255,0.3); border-radius: 2px; }

/* ── RESPONSIVE ── */
@media(max-width: 600px) {
  .wrap { padding: 0 16px 80px; }
  .hero { padding: 60px 0 40px; }
  .card { padding: 20px; }
  .feature-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<div class="page-scan"></div>
<canvas id="particles"></canvas>

<div class="wrap">

  <!-- ══ HERO ══ -->
  <header class="hero">
    <div class="logo-anim">
      <div class="logo-ring logo-ring-1"></div>
      <div class="logo-ring logo-ring-2"></div>
      <div class="logo-eye">
        <svg viewBox="0 0 44 44" fill="none">
          <ellipse cx="22" cy="22" rx="18" ry="9" stroke="url(#eg1)" stroke-width="1.5"/>
          <circle cx="22" cy="22" r="6.5" fill="url(#eg2)"/>
          <circle cx="25" cy="19" r="2.5" fill="white" opacity="0.55"/>
          <circle cx="22" cy="22" r="11" fill="none" stroke="url(#eg1)" stroke-width="0.7" stroke-dasharray="3 5"/>
          <defs>
            <linearGradient id="eg1" x1="0" y1="0" x2="44" y2="44"><stop stop-color="#7850ff"/><stop offset="1" stop-color="#ff3dac"/></linearGradient>
            <linearGradient id="eg2" x1="0" y1="0" x2="44" y2="44"><stop stop-color="#ff3dac"/><stop offset="1" stop-color="#00e5b0"/></linearGradient>
          </defs>
        </svg>
      </div>
    </div>

    <h1 class="hero-title">KatzLens</h1>
    <p class="hero-sub">AI Content Detection · Prototype</p>

    <div class="badges">
      <span class="badge badge-purple">🔍 AI Detection</span>
      <span class="badge badge-pink">🧠 Keyword Engine</span>
      <span class="badge badge-teal">🎬 Video Analysis</span>
      <span class="badge badge-warn">⚠ Prototype</span>
      <span class="badge badge-purple">🖥 Client-Side</span>
      <span class="badge badge-pink">📄 PDF Export</span>
    </div>

    <div class="scan-line-hero"></div>
  </header>

  <!-- ══ WHAT IS IT ══ -->
  <section class="section">
    <div class="section-label">Overview</div>
    <h2 class="section-title">What is <span>KatzLens</span>?</h2>
    <div class="card">
      <p style="font-size:1rem;color:rgba(232,224,255,0.7);line-height:1.8;margin-bottom:16px">
        <strong style="color:var(--text)">KatzLens</strong> is a browser-based AI content detection prototype that analyzes videos and URLs for signals of artificial intelligence generation, deepfakes, or synthetic manipulation — entirely on the client side, with zero server dependency.
      </p>
      <p style="font-size:0.92rem;color:rgba(232,224,255,0.5);line-height:1.75">
        Built as a passion project by <strong style="color:var(--text)">@kas1ee</strong>, KatzLens combines heuristic frame analysis, voice spectral heuristics, metadata inspection, and a comprehensive AI keyword detection engine to produce a probabilistic AI score. Results are visual, detailed, and exportable as PDF.
      </p>
      <div class="stat-row" style="margin-top:24px">
        <div class="stat-item"><div class="stat-num">100<span style="font-size:1rem">+</span></div><div class="stat-lbl">AI Keywords</div></div>
        <div class="stat-item"><div class="stat-num">4</div><div class="stat-lbl">Detection Tiers</div></div>
        <div class="stat-item"><div class="stat-num">8</div><div class="stat-lbl">Heuristics</div></div>
        <div class="stat-item"><div class="stat-num">5</div><div class="stat-lbl">Platforms</div></div>
        <div class="stat-item"><div class="stat-num">0</div><div class="stat-lbl">Server Calls</div></div>
      </div>
    </div>
  </section>

  <!-- ══ FEATURES ══ -->
  <section class="section">
    <div class="section-label">Features</div>
    <h2 class="section-title">What it <span>Does</span></h2>
    <div class="feature-grid">
      <div class="feature-card">
        <span class="feature-icon">👁</span>
        <div class="feature-name">Intro Splash Animation</div>
        <div class="feature-desc">Spinning dual-ring logo with fade-in brand name and animated loading bar on every launch.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">🔑</span>
        <div class="feature-name">AI Keyword Engine</div>
        <div class="feature-desc">100+ backend keywords across 4 tiers — auto-scans descriptions, titles, captions, and hashtags without any user input.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">🎬</span>
        <div class="feature-name">Video Frame Analysis</div>
        <div class="feature-desc">Extracts up to 16 frames from uploaded videos using Canvas API. Runs smoothness, noise, edge, and diff heuristics per frame.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">📺</span>
        <div class="feature-name">Live Scan Preview</div>
        <div class="feature-desc">Video plays inside the scanner with an animated scan-line overlay, corner brackets, and real-time frame thumbnail grid.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">📊</span>
        <div class="feature-name">Detailed Forensic Report</div>
        <div class="feature-desc">Circular AI score meter, confidence value, 4 analysis tabs (Face, Voice, Frames, Metadata), expandable tech report.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">📄</span>
        <div class="feature-name">PDF Export</div>
        <div class="feature-desc">Export a full forensic report to PDF including all metrics, keyword hits, session ID, and analysis summary.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">🔗</span>
        <div class="feature-name">Share Report</div>
        <div class="feature-desc">Share analysis results via native share sheet or copy to clipboard with one tap.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">🌐</span>
        <div class="feature-name">Multi-Platform URL Support</div>
        <div class="feature-desc">Detects and handles YouTube, TikTok, Instagram, X/Twitter, and Facebook URLs automatically.</div>
      </div>
      <div class="feature-card">
        <span class="feature-icon">🎨</span>
        <div class="feature-name">KatzLens Design System</div>
        <div class="feature-desc">Custom dark UI with Syne + JetBrains Mono typography, animated particle background, glassmorphism cards.</div>
      </div>
    </div>
  </section>

  <!-- ══ HOW IT WORKS ══ -->
  <section class="section">
    <div class="section-label">Architecture</div>
    <h2 class="section-title">How It <span>Works</span></h2>
    <div class="card">
      <div class="timeline">
        <div class="timeline-item">
          <div class="timeline-title">① Splash & Disclaimer</div>
          <div class="timeline-desc">On load, the animated KatzLens logo plays for ~3 seconds. Then a disclaimer modal appears with full attribution to @kas1ee and a clear prototype warning.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">② Input — URL or File</div>
          <div class="timeline-desc">User pastes a social media URL or uploads a video file (MP4, MOV, AVI, WEBM). Uploaded files show a live video preview immediately.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">③ Keyword Phase</div>
          <div class="timeline-desc">The backend keyword database (100+ terms) scans the input text for AI signals across 4 tiers: High Risk, Medium, Low, and Hashtags. Hits animate in live during scanning.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">④ Deep Analysis</div>
          <div class="timeline-desc">For files: Canvas API extracts frames, running 5 heuristics per frame (smoothness variance, noise pattern, Sobel edge detection, frame-diff, histogram analysis). For URLs: simulated platform-specific scoring weighted by keyword hits.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">⑤ Score Aggregation</div>
          <div class="timeline-desc">Frame scores average into a final AI probability %. Keyword signals add weighted bonus. Gaussian noise provides realistic variance. Confidence index calculated from signal strength.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">⑥ Results & Export</div>
          <div class="timeline-desc">Full report renders: circular meter, risk badge, keyword breakdown, frame strip, 4 analysis tabs, expandable tech table. Export to PDF or share instantly.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ KEYWORD ENGINE ══ -->
  <section class="section">
    <div class="section-label">Detection Engine</div>
    <h2 class="section-title">Keyword <span>Tiers</span></h2>
    <div class="card">
      <p style="font-size:0.9rem;color:rgba(232,224,255,0.5);margin-bottom:20px;line-height:1.7">
        All keyword detection runs in the browser — no API calls, no servers. The engine checks descriptions, titles, captions, and hashtags automatically.
      </p>
      <table class="kw-table">
        <thead>
          <tr>
            <th>Tier</th>
            <th>Weight</th>
            <th>Example Keywords</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="tier-chip tier-h">High Risk</span></td>
            <td style="font-family:'JetBrains Mono',monospace;color:#ff3d5e;font-size:0.82rem">+22 pts / hit</td>
            <td style="font-size:0.85rem;color:rgba(232,224,255,0.55)">deepfake, ai generated, stable diffusion, sora, face swap, voice cloning, synthetic media…</td>
          </tr>
          <tr>
            <td><span class="tier-chip tier-m">Medium</span></td>
            <td style="font-family:'JetBrains Mono',monospace;color:var(--warn);font-size:0.82rem">+10 pts / hit</td>
            <td style="font-size:0.85rem;color:rgba(232,224,255,0.55)">avatar, cgi, neural network, gpt, ai tools, controlnet, gan, lora trained, img2img…</td>
          </tr>
          <tr>
            <td><span class="tier-chip tier-t">Hashtag</span></td>
            <td style="font-family:'JetBrains Mono',monospace;color:var(--teal);font-size:0.82rem">+8 pts / hit</td>
            <td style="font-size:0.85rem;color:rgba(232,224,255,0.55)">#aiart, #deepfake, #midjourney, #stablediffusion, #texttovideo, #virtualinfluencer…</td>
          </tr>
          <tr>
            <td><span class="tier-chip tier-l">Low Risk</span></td>
            <td style="font-family:'JetBrains Mono',monospace;color:#a080ff;font-size:0.82rem">+4 pts / hit</td>
            <td style="font-size:0.85rem;color:rgba(232,224,255,0.55)">ai, digital art, algorithm, robot, synthetic, computer generated, automated…</td>
          </tr>
        </tbody>
      </table>
      <p style="margin-top:14px;font-family:'JetBrains Mono',monospace;font-size:0.72rem;color:var(--dim)">
        Max keyword contribution capped at 60 pts to prevent over-scoring on keyword-heavy content.
      </p>
    </div>
  </section>

  <!-- ══ FILE STRUCTURE ══ -->
  <section class="section">
    <div class="section-label">File Structure</div>
    <h2 class="section-title">Project <span>Structure</span></h2>
    <div class="code-block">
      <div class="code-header">
        <div class="code-dots"><span class="d1"></span><span class="d2"></span><span class="d3"></span></div>
        <div class="code-lang">Directory</div>
      </div>
      <div class="code-body"><pre>
<span class="cm">📁 katzlens/</span>
├── <span class="str">katzlens.html</span>          <span class="cm">← Main app (single file, self-contained)</span>
├── <span class="str">README.html</span>            <span class="cm">← This animated documentation</span>
│
<span class="cm">━━ Inside katzlens.html ━━━━━━━━━━━━━━━━━━━</span>
│
├── <span class="kw">&lt;style&gt;</span>                <span class="cm">← All CSS (no external CSS files)</span>
│   ├── Splash screen styles
│   ├── Disclaimer modal
│   ├── Input card &amp; video preview
│   ├── Loading section &amp; scanner
│   ├── Results, tabs, frame strip
│   └── Animations &amp; responsive
│
├── <span class="kw">&lt;body&gt;</span>                 <span class="cm">← HTML structure</span>
│   ├── #splash          <span class="cm">← Intro animation</span>
│   ├── #disclaimer-modal
│   ├── #bg-canvas       <span class="cm">← Animated particle bg</span>
│   ├── .wrapper
│   │   ├── .hero        <span class="cm">← Logo &amp; title</span>
│   │   ├── .input-card  <span class="cm">← URL / File tabs</span>
│   │   ├── #loading-section
│   │   └── #results-section
│   └── #hidden-video    <span class="cm">← Off-screen video for frame extraction</span>
│
└── <span class="kw">&lt;script&gt;</span>              <span class="cm">← All JS</span>
    ├── <span class="fn">AI_KEYWORDS</span>      <span class="cm">← Backend keyword database</span>
    ├── <span class="fn">detectKeywords()</span> <span class="cm">← Text scanner</span>
    ├── <span class="fn">startScan()</span>      <span class="cm">← Main entry point</span>
    ├── <span class="fn">runKeywordPhase()</span>
    ├── <span class="fn">runURLAnalysis()</span>
    ├── <span class="fn">runFileAnalysis()</span>
    ├── <span class="fn">analyzeFrame()</span>   <span class="cm">← Canvas heuristics</span>
    ├── <span class="fn">renderResults()</span>
    ├── <span class="fn">downloadPDF()</span>
    └── <span class="fn">initBackground()</span>  <span class="cm">← Particle animation</span></pre>
      </div>
    </div>
  </section>

  <!-- ══ USAGE ══ -->
  <section class="section">
    <div class="section-label">Usage</div>
    <h2 class="section-title">How to <span>Use</span></h2>
    <div class="card" style="margin-bottom:16px">
      <div class="code-block" style="border:none;border-radius:8px;background:rgba(0,0,0,0.5)">
        <div class="code-header" style="background:rgba(0,0,0,0.3)">
          <div class="code-dots"><span class="d1"></span><span class="d2"></span><span class="d3"></span></div>
          <div class="code-lang">Method 1 — Direct Open</div>
        </div>
        <div class="code-body">
<span class="cm"># No installation required. Just open in browser.</span>
<span class="kw">open</span> <span class="str">katzlens.html</span>          <span class="cm"># macOS</span>
<span class="kw">start</span> <span class="str">katzlens.html</span>        <span class="cm"># Windows</span>
<span class="kw">xdg-open</span> <span class="str">katzlens.html</span>     <span class="cm"># Linux</span>
        </div>
      </div>
    </div>
    <div class="card">
      <div class="code-block" style="border:none;border-radius:8px;background:rgba(0,0,0,0.5)">
        <div class="code-header" style="background:rgba(0,0,0,0.3)">
          <div class="code-dots"><span class="d1"></span><span class="d2"></span><span class="d3"></span></div>
          <div class="code-lang">Method 2 — Local Server (recommended)</div>
        </div>
        <div class="code-body">
<span class="cm"># Python (built-in)</span>
<span class="fn">python3</span> <span class="kw">-m</span> http.server <span class="num">8080</span>

<span class="cm"># Node.js</span>
<span class="fn">npx</span> serve .

<span class="cm"># Then open → http://localhost:8080/katzlens.html</span>
        </div>
      </div>
    </div>
    <div style="margin-top:20px">
      <div class="timeline">
        <div class="timeline-item">
          <div class="timeline-title">Scan a URL</div>
          <div class="timeline-desc">Paste any YouTube, TikTok, Instagram, X, or Facebook video URL. Click ⚡ Scan. KatzLens will auto-detect keywords and run platform-weighted AI scoring.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">Upload a Video File</div>
          <div class="timeline-desc">Switch to the File tab. Drag and drop or click to upload MP4/MOV/AVI/WEBM. A video preview appears instantly. Click Analyze File to run full frame-level analysis.</div>
        </div>
        <div class="timeline-item">
          <div class="timeline-title">Read the Report</div>
          <div class="timeline-desc">View your AI probability score, risk level badge, keyword detections, frame anomaly strip, and 4 analysis tabs. Export to PDF or share the summary.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ TECH STACK ══ -->
  <section class="section">
    <div class="section-label">Tech Stack</div>
    <h2 class="section-title">Built <span>With</span></h2>
    <div class="card">
      <div class="feature-grid" style="gap:12px">
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">🌐</span>
          <div class="feature-name" style="font-size:0.92rem">Vanilla HTML/CSS/JS</div>
          <div class="feature-desc" style="font-size:0.82rem">Zero frameworks. No React, no Vue, no bundler. Pure browser APIs.</div>
        </div>
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">🎨</span>
          <div class="feature-name" style="font-size:0.92rem">Canvas API</div>
          <div class="feature-desc" style="font-size:0.82rem">Frame extraction, pixel-level heuristic analysis, synthetic frame rendering, particle background.</div>
        </div>
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">📄</span>
          <div class="feature-name" style="font-size:0.92rem">jsPDF 2.5</div>
          <div class="feature-desc" style="font-size:0.82rem">Client-side PDF generation for forensic report export.</div>
        </div>
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">🔤</span>
          <div class="feature-name" style="font-size:0.92rem">Google Fonts</div>
          <div class="feature-desc" style="font-size:0.82rem">Syne (display), JetBrains Mono (mono), DM Sans (body).</div>
        </div>
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">🎞</span>
          <div class="feature-name" style="font-size:0.92rem">HTML Video API</div>
          <div class="feature-desc" style="font-size:0.82rem">Seekable video element for frame-accurate timestamp extraction.</div>
        </div>
        <div class="feature-card" style="padding:16px 18px">
          <span class="feature-icon" style="font-size:1.4rem">📋</span>
          <div class="feature-name" style="font-size:0.92rem">Web Share API</div>
          <div class="feature-desc" style="font-size:0.82rem">Native share sheet on mobile, clipboard fallback on desktop.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ DISCLAIMER ══ -->
  <section class="section">
    <div class="section-label">Disclaimer</div>
    <h2 class="section-title">Important <span>Notice</span></h2>
    <div class="card">
      <div class="disclaimer-box">
        <p>
          <strong>KatzLens is a prototype.</strong> It is not a real AI detector. All analysis is performed using client-side heuristics and probabilistic scoring — not machine learning models, not neural networks, not real forensic AI.
        </p>
        <p>
          Results <strong>should not</strong> be used as evidence in any legal, journalistic, or investigative context. False positives and false negatives occur. Treat all output as educational and experimental only.
        </p>
        <p>
          This project was created for learning and creative exploration by <a href="https://www.instagram.com/kas1ee" target="_blank">@kas1ee</a>. No warranties, express or implied.
        </p>
      </div>
    </div>
  </section>

  <!-- ══ CREDITS ══ -->
  <section class="section">
    <div class="section-label">Credits</div>
    <h2 class="section-title">Made <span>By</span></h2>
    <div class="card credits-card">
      <div class="credits-inner">
        <div class="credits-name">@kas1ee</div>
        <div class="credits-handle">CREATOR · DESIGNER · DEVELOPER</div>
        <p class="credits-desc">
          KatzLens is a solo prototype project built from scratch. The design, detection logic, keyword database, animations, and UI system were all crafted as a personal exploration of AI content detection concepts.
        </p>
        <a href="https://www.instagram.com/kas1ee" target="_blank" rel="noopener" class="insta-btn">
          <span class="insta-icon">📸</span>
          Follow @kas1ee on Instagram
        </a>
      </div>
    </div>
  </section>

  <!-- ══ FOOTER ══ -->
  <footer class="footer section">
    <div class="footer-logo">KatzLens</div>
    <div class="footer-note" style="margin-bottom:8px">AI Content Detection Prototype · Made by @kas1ee</div>
    <div class="footer-note">Not for forensic use · Educational purposes only</div>
  </footer>

</div><!-- /wrap -->

<script>
/* ── SCROLL REVEAL ── */
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
      observer.unobserve(e.target);
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

document.querySelectorAll('.section').forEach((s, i) => {
  s.style.transitionDelay = '0ms';
  observer.observe(s);
});

/* Stagger children in feature grid on reveal */
const gridObs = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const cards = e.target.querySelectorAll('.feature-card, .stat-item');
      cards.forEach((c, i) => {
        c.style.opacity = '0';
        c.style.transform = 'translateY(16px)';
        c.style.transition = `opacity 0.5s ${i*0.07}s ease, transform 0.5s ${i*0.07}s ease`;
        setTimeout(() => { c.style.opacity = '1'; c.style.transform = 'translateY(0)'; }, 80);
      });
      gridObs.unobserve(e.target);
    }
  });
}, { threshold: 0.1 });

document.querySelectorAll('.feature-grid, .stat-row').forEach(g => gridObs.observe(g));

/* ── PARTICLE CANVAS ── */
(function initParticles() {
  const canvas = document.getElementById('particles');
  const ctx = canvas.getContext('2d');
  let W, H;

  function resize() {
    W = canvas.width  = window.innerWidth;
    H = canvas.height = window.innerHeight;
  }
  resize();
  window.addEventListener('resize', resize);

  const pts = Array.from({ length: 60 }, () => ({
    x: Math.random() * 1,
    y: Math.random() * 1,
    vx: (Math.random() - 0.5) * 0.00018,
    vy: (Math.random() - 0.5) * 0.00018,
    r: Math.random() * 1.3 + 0.3,
    a: Math.random() * 0.3 + 0.05,
    hue: 240 + Math.random() * 80,
  }));

  function frame(ts) {
    ctx.clearRect(0, 0, W, H);
    pts.forEach(p => {
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0) p.x = 1; if (p.x > 1) p.x = 0;
      if (p.y < 0) p.y = 1; if (p.y > 1) p.y = 0;
      ctx.beginPath();
      ctx.arc(p.x * W, p.y * H, p.r, 0, Math.PI * 2);
      ctx.fillStyle = `hsla(${p.hue},70%,65%,${p.a})`;
      ctx.fill();
    });

    // Connect nearby particles
    for (let i = 0; i < pts.length; i++) {
      for (let j = i + 1; j < pts.length; j++) {
        const dx = (pts[i].x - pts[j].x) * W;
        const dy = (pts[i].y - pts[j].y) * H;
        const dist = Math.sqrt(dx * dx + dy * dy);
        if (dist < 120) {
          ctx.beginPath();
          ctx.moveTo(pts[i].x * W, pts[i].y * H);
          ctx.lineTo(pts[j].x * W, pts[j].y * H);
          ctx.strokeStyle = `rgba(120,80,255,${(1 - dist / 120) * 0.08})`;
          ctx.lineWidth = 0.5;
          ctx.stroke();
        }
      }
    }
    requestAnimationFrame(frame);
  }
  requestAnimationFrame(frame);
})();

/* ── ANIMATE STAT NUMBERS ── */
function animateNum(el, to, dur) {
  const start = performance.now();
  const from = 0;
  function step(ts) {
    const p = Math.min((ts - start) / dur, 1);
    const ease = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.round(from + (to - from) * ease) + (el.dataset.suffix || '');
    if (p < 1) requestAnimationFrame(step);
  }
  requestAnimationFrame(step);
}

const statObs = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      const nums = e.target.querySelectorAll('.stat-num');
      nums.forEach(n => {
        const raw = n.textContent;
        const val = parseInt(raw);
        const suffix = raw.replace(/[0-9]/g, '');
        n.dataset.suffix = suffix;
        animateNum(n, val, 1400);
      });
      statObs.unobserve(e.target);
    }
  });
}, { threshold: 0.3 });
document.querySelectorAll('.stat-row').forEach(r => statObs.observe(r));
</script>
</body>
</html>
