<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Debarjun Maharaj — Full-Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet">
<style>
:root {
  --void: #04060e;
  --deep: #080c1a;
  --surface: #0d1226;
  --glass: rgba(255,255,255,0.04);
  --glass-border: rgba(255,255,255,0.08);
  --neon-cyan: #00f5ff;
  --neon-blue: #4169ff;
  --neon-violet: #8b5cf6;
  --neon-pink: #f472b6;
  --neon-green: #00ff9d;
  --text-primary: #f0f4ff;
  --text-secondary: #8892a4;
  --text-muted: #4a5568;
}

*, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--void);
  color: var(--text-primary);
  font-family: 'Outfit', sans-serif;
  overflow-x: hidden;
  min-height: 100vh;
}

/* === ANIMATED BACKGROUND === */
.bg-canvas {
  position: fixed;
  inset: 0;
  z-index: 0;
  overflow: hidden;
}

.bg-canvas::before {
  content: '';
  position: absolute;
  inset: 0;
  background: 
    radial-gradient(ellipse 80% 60% at 20% 10%, rgba(65,105,255,0.12) 0%, transparent 60%),
    radial-gradient(ellipse 60% 80% at 80% 90%, rgba(139,92,246,0.10) 0%, transparent 60%),
    radial-gradient(ellipse 40% 40% at 50% 50%, rgba(0,245,255,0.04) 0%, transparent 70%);
  animation: bgShift 12s ease-in-out infinite alternate;
}

@keyframes bgShift {
  0% { opacity: 0.7; transform: scale(1); }
  100% { opacity: 1; transform: scale(1.05); }
}

.grid-overlay {
  position: fixed;
  inset: 0;
  z-index: 0;
  background-image: 
    linear-gradient(rgba(65,105,255,0.04) 1px, transparent 1px),
    linear-gradient(90deg, rgba(65,105,255,0.04) 1px, transparent 1px);
  background-size: 60px 60px;
  mask-image: radial-gradient(ellipse at center, black 30%, transparent 80%);
}

/* Floating particles */
.particles {
  position: fixed;
  inset: 0;
  z-index: 0;
  pointer-events: none;
}
.particle {
  position: absolute;
  border-radius: 50%;
  animation: floatUp linear infinite;
  opacity: 0;
}
@keyframes floatUp {
  0% { transform: translateY(100vh) scale(0); opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 0.5; }
  100% { transform: translateY(-20px) scale(1); opacity: 0; }
}

/* === MAIN WRAPPER === */
.wrapper {
  position: relative;
  z-index: 1;
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 24px 80px;
}

/* === HERO SECTION === */
.hero {
  padding: 80px 0 60px;
  text-align: center;
  position: relative;
}

.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 100px;
  padding: 6px 18px;
  font-family: 'Space Mono', monospace;
  font-size: 11px;
  color: var(--neon-cyan);
  letter-spacing: 0.15em;
  text-transform: uppercase;
  margin-bottom: 28px;
  animation: fadeSlideDown 0.8s ease both;
}

.hero-badge .dot {
  width: 6px; height: 6px;
  background: var(--neon-green);
  border-radius: 50%;
  animation: pulse 2s ease infinite;
}

@keyframes pulse {
  0%, 100% { box-shadow: 0 0 0 0 rgba(0,255,157,0.6); }
  50% { box-shadow: 0 0 0 6px rgba(0,255,157,0); }
}

.hero-name {
  font-family: 'Syne', sans-serif;
  font-weight: 800;
  font-size: clamp(48px, 8vw, 88px);
  line-height: 1;
  letter-spacing: -0.03em;
  margin-bottom: 16px;
  animation: fadeSlideDown 0.8s 0.1s ease both;
}

.hero-name .line1 { display: block; color: var(--text-primary); }
.hero-name .line2 {
  display: block;
  background: linear-gradient(135deg, var(--neon-cyan), var(--neon-blue), var(--neon-violet));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradientShift 4s ease infinite alternate;
}
@keyframes gradientShift {
  0% { filter: hue-rotate(0deg); }
  100% { filter: hue-rotate(30deg); }
}

.hero-title {
  font-family: 'Space Mono', monospace;
  font-size: 13px;
  color: var(--text-secondary);
  letter-spacing: 0.2em;
  text-transform: uppercase;
  margin-bottom: 32px;
  animation: fadeSlideDown 0.8s 0.2s ease both;
}

/* Typing animation */
.typewriter {
  font-family: 'Space Mono', monospace;
  font-size: 16px;
  color: var(--neon-cyan);
  height: 24px;
  display: inline-block;
  animation: fadeSlideDown 0.8s 0.3s ease both;
}
.typewriter::after {
  content: '|';
  animation: blink 0.8s infinite;
}
@keyframes blink { 0%,100% { opacity: 1; } 50% { opacity: 0; } }

.hero-social {
  display: flex;
  justify-content: center;
  gap: 12px;
  margin-top: 32px;
  flex-wrap: wrap;
  animation: fadeSlideDown 0.8s 0.4s ease both;
}

.social-pill {
  display: inline-flex;
  align-items: center;
  gap: 7px;
  padding: 8px 16px;
  border-radius: 100px;
  font-size: 12px;
  font-weight: 500;
  text-decoration: none;
  color: var(--text-secondary);
  background: var(--glass);
  border: 1px solid var(--glass-border);
  transition: all 0.3s ease;
  letter-spacing: 0.04em;
}
.social-pill:hover {
  color: var(--text-primary);
  border-color: var(--neon-cyan);
  box-shadow: 0 0 20px rgba(0,245,255,0.15);
  transform: translateY(-2px);
}
.social-pill svg { width: 14px; height: 14px; }

/* === SECTION COMMON === */
section {
  margin-bottom: 64px;
  animation: fadeSlideUp 0.6s ease both;
}

.section-label {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 28px;
}
.section-label .line {
  flex: 1;
  height: 1px;
  background: linear-gradient(90deg, var(--glass-border), transparent);
}
.section-label h2 {
  font-family: 'Syne', sans-serif;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--neon-cyan);
  white-space: nowrap;
}

/* === ABOUT GRID === */
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media(max-width: 600px) { .about-grid { grid-template-columns: 1fr; } }

.about-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 20px;
  display: flex;
  align-items: flex-start;
  gap: 14px;
  transition: all 0.3s ease;
  cursor: default;
}
.about-card:hover {
  border-color: rgba(0,245,255,0.3);
  background: rgba(0,245,255,0.03);
  transform: translateY(-2px);
  box-shadow: 0 8px 32px rgba(0,245,255,0.06);
}
.about-card .icon {
  font-size: 22px;
  flex-shrink: 0;
  margin-top: 2px;
}
.about-card strong {
  display: block;
  font-size: 13px;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 4px;
  font-family: 'Syne', sans-serif;
}
.about-card span {
  font-size: 12px;
  color: var(--text-secondary);
  line-height: 1.5;
}

/* === APP SHOWCASE === */
.app-showcase {
  background: linear-gradient(135deg, rgba(65,105,255,0.08), rgba(139,92,246,0.06));
  border: 1px solid rgba(65,105,255,0.2);
  border-radius: 24px;
  padding: 32px;
  display: flex;
  align-items: center;
  gap: 28px;
  position: relative;
  overflow: hidden;
  transition: all 0.3s ease;
  text-decoration: none;
}
.app-showcase::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(65,105,255,0.12) 0%, transparent 70%);
  animation: slowRotate 8s linear infinite;
}
@keyframes slowRotate { to { transform: rotate(360deg); } }
.app-showcase:hover {
  border-color: rgba(0,245,255,0.4);
  transform: translateY(-3px);
  box-shadow: 0 16px 48px rgba(65,105,255,0.15);
}

.app-logo-wrap {
  position: relative;
  flex-shrink: 0;
}
.app-logo {
  width: 80px;
  height: 80px;
  border-radius: 20px;
  object-fit: cover;
  border: 2px solid rgba(0,245,255,0.3);
  box-shadow: 0 0 30px rgba(0,245,255,0.2);
  position: relative;
  z-index: 1;
  transition: all 0.3s ease;
}
.app-showcase:hover .app-logo {
  box-shadow: 0 0 50px rgba(0,245,255,0.4);
  border-color: var(--neon-cyan);
}
.app-logo-glow {
  position: absolute;
  inset: -4px;
  border-radius: 24px;
  background: linear-gradient(135deg, var(--neon-cyan), var(--neon-blue));
  opacity: 0.3;
  filter: blur(8px);
  animation: glowPulse 2s ease-in-out infinite alternate;
}
@keyframes glowPulse { from { opacity: 0.2; } to { opacity: 0.5; } }

.app-info { flex: 1; position: relative; z-index: 1; }
.app-store-badge {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  background: rgba(0,245,255,0.1);
  border: 1px solid rgba(0,245,255,0.2);
  border-radius: 100px;
  padding: 3px 10px;
  font-size: 10px;
  font-family: 'Space Mono', monospace;
  color: var(--neon-cyan);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-bottom: 10px;
}
.app-name {
  font-family: 'Syne', sans-serif;
  font-weight: 700;
  font-size: 22px;
  color: var(--text-primary);
  margin-bottom: 6px;
}
.app-desc {
  font-size: 13px;
  color: var(--text-secondary);
  line-height: 1.6;
  margin-bottom: 16px;
}
.app-cta {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  background: linear-gradient(135deg, var(--neon-blue), var(--neon-violet));
  color: white;
  text-decoration: none;
  padding: 10px 20px;
  border-radius: 100px;
  font-size: 13px;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 16px rgba(65,105,255,0.3);
}
.app-cta:hover { 
  transform: translateY(-1px);
  box-shadow: 0 8px 24px rgba(65,105,255,0.5); 
}

/* === TECH GRID === */
.tech-categories {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
@media(max-width: 640px) { .tech-categories { grid-template-columns: 1fr; } }

.tech-cat {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 20px;
  transition: all 0.3s ease;
}
.tech-cat:hover {
  border-color: rgba(0,245,255,0.2);
  transform: translateY(-3px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.3);
}
.tech-cat-title {
  font-family: 'Syne', sans-serif;
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  margin-bottom: 14px;
}
.tech-cat.frontend .tech-cat-title { color: var(--neon-cyan); }
.tech-cat.backend .tech-cat-title { color: var(--neon-violet); }
.tech-cat.design .tech-cat-title { color: var(--neon-pink); }

.tech-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 6px;
}
.tech-tag {
  font-family: 'Space Mono', monospace;
  font-size: 10px;
  padding: 4px 10px;
  border-radius: 6px;
  letter-spacing: 0.05em;
}
.frontend .tech-tag {
  background: rgba(0,245,255,0.08);
  color: rgba(0,245,255,0.8);
  border: 1px solid rgba(0,245,255,0.15);
}
.backend .tech-tag {
  background: rgba(139,92,246,0.08);
  color: rgba(139,92,246,0.8);
  border: 1px solid rgba(139,92,246,0.15);
}
.design .tech-tag {
  background: rgba(244,114,182,0.08);
  color: rgba(244,114,182,0.8);
  border: 1px solid rgba(244,114,182,0.15);
}

/* === STATS === */
.stats-row {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
  margin-bottom: 16px;
}
@media(max-width: 500px) { .stats-row { grid-template-columns: 1fr 1fr; } }

.stat-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 16px;
  padding: 20px;
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}
.stat-card::before {
  content: '';
  position: absolute;
  top: 0; left: 0; right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--neon-cyan), var(--neon-blue));
  opacity: 0;
  transition: opacity 0.3s ease;
}
.stat-card:hover::before { opacity: 1; }
.stat-card:hover {
  transform: translateY(-3px);
  border-color: rgba(0,245,255,0.2);
}
.stat-value {
  font-family: 'Syne', sans-serif;
  font-size: 32px;
  font-weight: 800;
  background: linear-gradient(135deg, var(--neon-cyan), var(--neon-blue));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  display: block;
}
.stat-label {
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 0.1em;
  text-transform: uppercase;
  margin-top: 4px;
}

/* === PROJECTS === */
.projects-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}
@media(max-width: 600px) { .projects-grid { grid-template-columns: 1fr; } }

.project-card {
  background: var(--glass);
  border: 1px solid var(--glass-border);
  border-radius: 20px;
  overflow: hidden;
  transition: all 0.4s ease;
  text-decoration: none;
  color: inherit;
  display: block;
}
.project-card:hover {
  transform: translateY(-6px);
  border-color: rgba(0,245,255,0.25);
  box-shadow: 0 20px 60px rgba(0,0,0,0.4), 0 0 40px rgba(0,245,255,0.05);
}
.project-img {
  width: 100%;
  height: 160px;
  object-fit: cover;
  display: block;
}
.project-img-placeholder {
  width: 100%;
  height: 160px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 40px;
}
.project-card:nth-child(1) .project-img-placeholder {
  background: linear-gradient(135deg, rgba(0,245,255,0.1), rgba(65,105,255,0.15));
}
.project-card:nth-child(2) .project-img-placeholder {
  background: linear-gradient(135deg, rgba(139,92,246,0.1), rgba(244,114,182,0.15));
}
.project-body { padding: 20px; }
.project-name {
  font-family: 'Syne', sans-serif;
  font-size: 15px;
  font-weight: 700;
  color: var(--text-primary);
  margin-bottom: 6px;
}
.project-desc {
  font-size: 12px;
  color: var(--text-secondary);
  line-height: 1.5;
  margin-bottom: 14px;
}
.project-tags { display: flex; gap: 6px; flex-wrap: wrap; }
.project-tag {
  font-size: 10px;
  font-family: 'Space Mono', monospace;
  padding: 3px 8px;
  border-radius: 4px;
  background: rgba(255,255,255,0.05);
  color: var(--text-secondary);
  border: 1px solid var(--glass-border);
}

/* === GITHUB STATS === */
.github-stats {
  display: grid;
  grid-template-columns: 1fr;
  gap: 12px;
}
.github-img {
  width: 100%;
  border-radius: 16px;
  border: 1px solid var(--glass-border);
  display: block;
  transition: all 0.3s ease;
}
.github-img:hover {
  border-color: rgba(0,245,255,0.25);
  box-shadow: 0 8px 32px rgba(0,245,255,0.08);
}
.github-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}

/* === FOOTER === */
.footer {
  text-align: center;
  padding: 40px 0 20px;
  border-top: 1px solid var(--glass-border);
}
.footer-text {
  font-family: 'Space Mono', monospace;
  font-size: 11px;
  color: var(--text-muted);
  letter-spacing: 0.1em;
}
.footer-text span {
  color: var(--neon-cyan);
}

/* === ANIMATIONS === */
@keyframes fadeSlideDown {
  from { opacity: 0; transform: translateY(-20px); }
  to { opacity: 1; transform: translateY(0); }
}
@keyframes fadeSlideUp {
  from { opacity: 0; transform: translateY(30px); }
  to { opacity: 1; transform: translateY(0); }
}

/* Staggered section reveals */
section:nth-child(1) { animation-delay: 0.1s; }
section:nth-child(2) { animation-delay: 0.2s; }
section:nth-child(3) { animation-delay: 0.3s; }
section:nth-child(4) { animation-delay: 0.4s; }
section:nth-child(5) { animation-delay: 0.5s; }
section:nth-child(6) { animation-delay: 0.6s; }

/* Scrollbar */
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: var(--void); }
::-webkit-scrollbar-thumb { background: rgba(0,245,255,0.2); border-radius: 2px; }
</style>
</head>
<body>

<!-- Background -->
<div class="bg-canvas"></div>
<div class="grid-overlay"></div>
<div class="particles" id="particles"></div>

<div class="wrapper">

  <!-- HERO -->
  <div class="hero">
    <div class="hero-badge">
      <span class="dot"></span>
      Available for work &amp; collaborations
    </div>

    <h1 class="hero-name">
      <span class="line1">Debarjun</span>
      <span class="line2">Maharaj</span>
    </h1>

    <p class="hero-title">Full-Stack Developer &nbsp;·&nbsp; Designer &nbsp;·&nbsp; Creator</p>

    <div class="typewriter" id="typewriter"></div>

    <div class="hero-social">
      <a href="https://linkedin.com/in/netfie" class="social-pill" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 01-2.063-2.065 2.064 2.064 0 112.063 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a href="https://x.com/debarjunmaharaj" class="social-pill" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.244 2.25h3.308l-7.227 8.26 8.502 11.24H16.17l-4.714-6.231-5.401 6.231H2.744l7.73-8.835L1.254 2.25H8.08l4.713 6.231zm-1.161 17.52h1.833L7.084 4.126H5.117z"/></svg>
        X / Twitter
      </a>
      <a href="https://instagram.com/debarjunmaharaj" class="social-pill" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838a6.162 6.162 0 100 12.324 6.162 6.162 0 000-12.324zM12 16a4 4 0 110-8 4 4 0 010 8zm6.406-11.845a1.44 1.44 0 100 2.881 1.44 1.44 0 000-2.881z"/></svg>
        Instagram
      </a>
      <a href="https://youtube.com/@Netfie" class="social-pill" target="_blank">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M23.498 6.186a3.016 3.016 0 00-2.122-2.136C19.505 3.545 12 3.545 12 3.545s-7.505 0-9.377.505A3.017 3.017 0 00.502 6.186C0 8.07 0 12 0 12s0 3.93.502 5.814a3.016 3.016 0 002.122 2.136c1.871.505 9.376.505 9.376.505s7.505 0 9.377-.505a3.015 3.015 0 002.122-2.136C24 15.93 24 12 24 12s0-3.93-.502-5.814zM9.545 15.568V8.432L15.818 12l-6.273 3.568z"/></svg>
        YouTube
      </a>
      <a href="mailto:debarjunofficial@gmail.com" class="social-pill">
        <svg viewBox="0 0 24 24" fill="currentColor"><path d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 010 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"/></svg>
        Email
      </a>
    </div>
  </div>

  <!-- ABOUT -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>⚡ About Me</h2>
      <div class="line"></div>
    </div>
    <div class="about-grid">
      <div class="about-card">
        <div class="icon">🔭</div>
        <div>
          <strong>Currently Building</strong>
          <span>AI-powered web applications that push the boundaries of what's possible on the web</span>
        </div>
      </div>
      <div class="about-card">
        <div class="icon">🌱</div>
        <div>
          <strong>Learning</strong>
          <span>Cloud Architecture &amp; React — always leveling up my skill set</span>
        </div>
      </div>
      <div class="about-card">
        <div class="icon">💼</div>
        <div>
          <strong>Experience</strong>
          <span>5+ years as a Full-Stack Developer combining technology with creative design</span>
        </div>
      </div>
      <div class="about-card">
        <div class="icon">🎯</div>
        <div>
          <strong>2025 Goal</strong>
          <span>Contribute meaningfully to Open Source — code that lives beyond me</span>
        </div>
      </div>
      <div class="about-card">
        <div class="icon">📱</div>
        <div>
          <strong>Mobile Development</strong>
          <span>Published apps on Google Play Store — bringing ideas to Android users</span>
        </div>
      </div>
      <div class="about-card">
        <div class="icon">⚡</div>
        <div>
          <strong>Fun Fact</strong>
          <span>Code by day, game by night — balance is everything</span>
        </div>
      </div>
    </div>
  </section>

  <!-- LATEST APP -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>📱 Latest App</h2>
      <div class="line"></div>
    </div>
    <a href="https://play.google.com/store/apps/details?id=com.netfie.dainikinfobangla" target="_blank" class="app-showcase">
      <div class="app-logo-wrap">
        <div class="app-logo-glow"></div>
        <img 
          src="https://play-lh.googleusercontent.com/B2t8MsPmzSEWL3g8f2p5epLKDribpALiBD27QWXThQxZ7nKr95o7pwEgqxVasfDiHiHFQG01F7DwVpahWXYmyA=w240-h480-rw" 
          alt="Dainik Info Bangla App" 
          class="app-logo"
        />
      </div>
      <div class="app-info">
        <span class="app-store-badge">
          <svg width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><path d="M3 20.5v-17c0-.83 1.01-1.31 1.63-.8l15 8.5c.55.31.55 1.09 0 1.4l-15 8.5c-.62.5-1.63.03-1.63-.6z"/></svg>
          Google Play
        </span>
        <div class="app-name">Dainik Info Bangla</div>
        <div class="app-desc">A Bengali news app delivering the latest news, updates and information to users in their native language — built with love for the Bengali-speaking community.</div>
        <span class="app-cta">
          <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          View on Play Store
        </span>
      </div>
    </a>
  </section>

  <!-- TECH STACK -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>💻 Tech Arsenal</h2>
      <div class="line"></div>
    </div>
    <div class="tech-categories">
      <div class="tech-cat frontend">
        <div class="tech-cat-title">Frontend</div>
        <div class="tech-tags">
          <span class="tech-tag">HTML5</span>
          <span class="tech-tag">CSS3</span>
          <span class="tech-tag">JavaScript</span>
          <span class="tech-tag">Bootstrap</span>
          <span class="tech-tag">jQuery</span>
          <span class="tech-tag">React</span>
        </div>
      </div>
      <div class="tech-cat backend">
        <div class="tech-cat-title">Backend</div>
        <div class="tech-tags">
          <span class="tech-tag">PHP</span>
          <span class="tech-tag">Laravel</span>
          <span class="tech-tag">Python</span>
          <span class="tech-tag">MySQL</span>
          <span class="tech-tag">SQLite</span>
          <span class="tech-tag">WordPress</span>
        </div>
      </div>
      <div class="tech-cat design">
        <div class="tech-cat-title">Design</div>
        <div class="tech-tags">
          <span class="tech-tag">Photoshop</span>
          <span class="tech-tag">Illustrator</span>
          <span class="tech-tag">Figma</span>
          <span class="tech-tag">Adobe XD</span>
        </div>
      </div>
    </div>
  </section>

  <!-- STATS -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>📊 Metrics</h2>
      <div class="line"></div>
    </div>
    <div class="stats-row">
      <div class="stat-card">
        <span class="stat-value">5+</span>
        <span class="stat-label">Years Experience</span>
      </div>
      <div class="stat-card">
        <span class="stat-value">50+</span>
        <span class="stat-label">Projects Built</span>
      </div>
      <div class="stat-card">
        <span class="stat-value">10+</span>
        <span class="stat-label">Tech Stack</span>
      </div>
    </div>

    <div class="github-stats">
      <div class="github-row">
        <img class="github-img" src="https://github-readme-stats.vercel.app/api?username=debarjunmaharaj&show_icons=true&count_private=true&hide_border=true&title_color=00f5ff&icon_color=4169ff&text_color=c9d1d9&bg_color=04060e" alt="GitHub Stats" />
        <img class="github-img" src="https://github-readme-stats.vercel.app/api/top-langs/?username=debarjunmaharaj&layout=compact&hide_border=true&title_color=00f5ff&text_color=4169ff&bg_color=04060e" alt="Top Languages" />
      </div>
      <img class="github-img" src="https://nirzak-streak-stats.vercel.app/?user=debarjunmaharaj&theme=dark&hide_border=true&stroke=00f5ff&fire=4169ff&currStreakNum=00f5ff&ring=4169ff&currStreakLabel=4169ff&sideNums=00f5ff&sideLabels=8892a4&dates=ffffff&background=04060e" alt="GitHub Streak" />
      <img class="github-img" src="https://github-readme-activity-graph.vercel.app/graph?username=debarjunmaharaj&bg_color=04060e&color=00f5ff&line=4169ff&point=00f5ff&area=true&hide_border=true" alt="Activity Graph" />
    </div>
  </section>

  <!-- PROJECTS -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>🚀 Projects</h2>
      <div class="line"></div>
    </div>
    <div class="projects-grid">
      <a href="https://github.com/debarjunmaharaj/ShopWave" class="project-card" target="_blank">
        <div class="project-img-placeholder">🛒</div>
        <div class="project-body">
          <div class="project-name">E-Commerce Platform</div>
          <div class="project-desc">WordPress e-commerce platform with custom theme and plugins for seamless shopping experiences</div>
          <div class="project-tags">
            <span class="project-tag">WordPress</span>
            <span class="project-tag">PHP</span>
            <span class="project-tag">WooCommerce</span>
          </div>
        </div>
      </a>
      <a href="https://github.com/debarjunmaharaj/PHP-Portfolio-CMS" class="project-card" target="_blank">
        <div class="project-img-placeholder">📊</div>
        <div class="project-body">
          <div class="project-name">CRM Dashboard</div>
          <div class="project-desc">Laravel-based CRM system with advanced reporting features and intuitive data visualization</div>
          <div class="project-tags">
            <span class="project-tag">Laravel</span>
            <span class="project-tag">MySQL</span>
            <span class="project-tag">JavaScript</span>
          </div>
        </div>
      </a>
    </div>
  </section>

  <!-- FOOTER -->
  <div class="footer">
    <p class="footer-text">
      Built with <span>♥</span> by Debarjun Maharaj &nbsp;·&nbsp; <span>debarjunofficial@gmail.com</span>
    </p>
    <br>
    <img src="https://profile-counter.glitch.me/debarjunmaharaj/count.svg" alt="Visitor Count" style="margin-top: 8px; opacity: 0.5; filter: hue-rotate(180deg);" />
  </div>

</div>

<script>
// === PARTICLES ===
const container = document.getElementById('particles');
const colors = ['#00f5ff', '#4169ff', '#8b5cf6', '#f472b6', '#00ff9d'];
for (let i = 0; i < 30; i++) {
  const p = document.createElement('div');
  p.className = 'particle';
  const size = Math.random() * 3 + 1;
  p.style.cssText = `
    width: ${size}px; height: ${size}px;
    left: ${Math.random() * 100}%;
    background: ${colors[Math.floor(Math.random() * colors.length)]};
    animation-duration: ${Math.random() * 15 + 10}s;
    animation-delay: ${Math.random() * 10}s;
    box-shadow: 0 0 ${size * 4}px currentColor;
    filter: blur(${Math.random() > 0.5 ? 0.5 : 0}px);
  `;
  container.appendChild(p);
}

// === TYPEWRITER ===
const phrases = [
  'Building Digital Experiences',
  'WordPress Expert',
  'Laravel Architect',
  'Creative Technologist',
  'Open Source Enthusiast',
];
let pi = 0, ci = 0, deleting = false;
const el = document.getElementById('typewriter');
function type() {
  const phrase = phrases[pi];
  if (!deleting) {
    el.textContent = phrase.slice(0, ci + 1);
    ci++;
    if (ci === phrase.length) { deleting = true; setTimeout(type, 1800); return; }
  } else {
    el.textContent = phrase.slice(0, ci - 1);
    ci--;
    if (ci === 0) { deleting = false; pi = (pi + 1) % phrases.length; }
  }
  setTimeout(type, deleting ? 50 : 80);
}
type();

// === INTERSECTION OBSERVER for section animations ===
const observer = new IntersectionObserver((entries) => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.style.animationPlayState = 'running';
    }
  });
}, { threshold: 0.1 });
document.querySelectorAll('section').forEach(s => {
  s.style.animationPlayState = 'paused';
  observer.observe(s);
});
</script>

</body>
</html>
