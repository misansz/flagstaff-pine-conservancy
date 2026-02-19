<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flagstaff Pine Conservancy</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=Crimson+Pro:ital,wght@0,300;0,400;0,500;1,300&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --pine: #1a2e1a;
    --bark: #3d2b1f;
    --sage: #6b7c5a;
    --ash: #c4bfb3;
    --ember: #c45c2a;
    --sky: #a8bfc4;
    --cream: #f2ede4;
    --char: #0d0d0b;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--cream);
    color: var(--pine);
    font-family: 'Crimson Pro', Georgia, serif;
    font-size: 18px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* GRAIN OVERLAY */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none;
    z-index: 1000;
    opacity: 0.4;
  }

  /* NAV */
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 100;
    padding: 1.2rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(242, 237, 228, 0.92);
    backdrop-filter: blur(8px);
    border-bottom: 1px solid rgba(26, 46, 26, 0.1);
  }

  .nav-logo {
    font-family: 'Space Mono', monospace;
    font-size: 0.75rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--pine);
    text-decoration: none;
  }

  .nav-links {
    display: flex;
    gap: 2.5rem;
    list-style: none;
  }

  .nav-links a {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--pine);
    text-decoration: none;
    opacity: 0.7;
    transition: opacity 0.2s;
  }

  .nav-links a:hover { opacity: 1; }

  /* HERO */
  .hero {
    min-height: 100vh;
    display: grid;
    grid-template-columns: 1fr 1fr;
    padding-top: 80px;
    position: relative;
    overflow: hidden;
  }

  .hero-left {
    padding: 8rem 4rem 6rem 5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    position: relative;
    z-index: 2;
  }

  .hero-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ember);
    margin-bottom: 1.5rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.2s forwards;
  }

  .hero-title {
    font-family: 'Playfair Display', Georgia, serif;
    font-size: clamp(3.5rem, 6vw, 6rem);
    font-weight: 900;
    line-height: 1.0;
    color: var(--pine);
    margin-bottom: 2rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.4s forwards;
  }

  .hero-title em {
    font-style: italic;
    color: var(--sage);
  }

  .hero-subtitle {
    font-size: 1.15rem;
    font-weight: 300;
    color: var(--bark);
    max-width: 420px;
    margin-bottom: 3rem;
    opacity: 0;
    animation: fadeUp 0.8s 0.6s forwards;
  }

  .hero-cta {
    display: flex;
    gap: 1rem;
    flex-wrap: wrap;
    opacity: 0;
    animation: fadeUp 0.8s 0.8s forwards;
  }

  .btn-primary {
    background: var(--pine);
    color: var(--cream);
    padding: 0.9rem 2rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-decoration: none;
    border: none;
    cursor: pointer;
    transition: background 0.2s, transform 0.2s;
    display: inline-block;
  }

  .btn-primary:hover {
    background: var(--ember);
    transform: translateY(-2px);
  }

  .btn-outline {
    background: transparent;
    color: var(--pine);
    padding: 0.9rem 2rem;
    font-family: 'Space Mono', monospace;
    font-size: 0.7rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    text-decoration: none;
    border: 1.5px solid var(--pine);
    cursor: pointer;
    transition: all 0.2s;
    display: inline-block;
  }

  .btn-outline:hover {
    background: var(--pine);
    color: var(--cream);
    transform: translateY(-2px);
  }

  .hero-right {
    position: relative;
    overflow: hidden;
  }

  .hero-forest {
    width: 100%;
    height: 100%;
    background: var(--pine);
    position: relative;
    display: flex;
    align-items: flex-end;
    justify-content: center;
    overflow: hidden;
  }

  /* SVG Forest Scene */
  .forest-svg {
    width: 100%;
    height: 100%;
    position: absolute;
    bottom: 0;
  }

  .hero-stat-overlay {
    position: absolute;
    bottom: 3rem;
    left: 2rem;
    right: 2rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1px;
    background: rgba(196, 191, 179, 0.2);
    z-index: 10;
    opacity: 0;
    animation: fadeUp 0.8s 1s forwards;
  }

  .hero-stat {
    background: rgba(13, 13, 11, 0.7);
    backdrop-filter: blur(4px);
    padding: 1.2rem 1.5rem;
    border: 1px solid rgba(196, 191, 179, 0.15);
  }

  .hero-stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 2rem;
    font-weight: 700;
    color: var(--ash);
    display: block;
    line-height: 1;
  }

  .hero-stat-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.55rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.6);
    margin-top: 0.3rem;
    display: block;
  }

  /* TICKER */
  .ticker {
    background: var(--pine);
    color: var(--ash);
    padding: 0.7rem 0;
    overflow: hidden;
    white-space: nowrap;
  }

  .ticker-inner {
    display: inline-block;
    animation: ticker 30s linear infinite;
  }

  .ticker-item {
    display: inline-block;
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    margin: 0 3rem;
    opacity: 0.7;
  }

  .ticker-dot {
    color: var(--ember);
    margin-right: 3rem;
  }

  /* SECTION BASE */
  section {
    padding: 7rem 5rem;
  }

  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.65rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--ember);
    margin-bottom: 1.2rem;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2rem, 4vw, 3.2rem);
    font-weight: 700;
    line-height: 1.1;
    color: var(--pine);
    margin-bottom: 1.5rem;
  }

  /* CRISIS SECTION */
  .crisis {
    background: var(--char);
    color: var(--ash);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }

  .crisis .section-title {
    color: var(--cream);
  }

  .crisis-body {
    font-size: 1.1rem;
    font-weight: 300;
    color: rgba(196, 191, 179, 0.8);
    line-height: 1.8;
  }

  .crisis-stats {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: rgba(196, 191, 179, 0.1);
  }

  .crisis-stat-box {
    background: var(--char);
    padding: 2.5rem 2rem;
    border: 1px solid rgba(196, 191, 179, 0.08);
    position: relative;
    overflow: hidden;
    transition: border-color 0.3s;
  }

  .crisis-stat-box:hover {
    border-color: rgba(196, 92, 42, 0.4);
  }

  .crisis-stat-box::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 2px;
    background: var(--ember);
    transform: scaleX(0);
    transition: transform 0.3s;
  }

  .crisis-stat-box:hover::before {
    transform: scaleX(1);
  }

  .crisis-num {
    font-family: 'Playfair Display', serif;
    font-size: 2.8rem;
    font-weight: 900;
    color: var(--ember);
    display: block;
    line-height: 1;
    margin-bottom: 0.5rem;
  }

  .crisis-desc {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.5);
    line-height: 1.5;
  }

  /* APPROACH */
  .approach {
    background: var(--cream);
  }

  .approach-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 3rem;
    margin-top: 4rem;
  }

  .approach-card {
    position: relative;
    padding: 2.5rem;
    border: 1px solid rgba(26, 46, 26, 0.12);
    transition: border-color 0.3s, transform 0.3s;
    background: white;
  }

  .approach-card:hover {
    border-color: var(--sage);
    transform: translateY(-4px);
  }

  .approach-number {
    font-family: 'Playfair Display', serif;
    font-size: 4rem;
    font-weight: 900;
    color: rgba(26, 46, 26, 0.06);
    position: absolute;
    top: 1rem;
    right: 1.5rem;
    line-height: 1;
  }

  .approach-icon {
    font-size: 1.8rem;
    margin-bottom: 1.2rem;
    display: block;
  }

  .approach-card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.4rem;
    font-weight: 700;
    color: var(--pine);
    margin-bottom: 0.8rem;
  }

  .approach-card-body {
    font-size: 1rem;
    color: var(--bark);
    font-weight: 300;
    line-height: 1.7;
  }

  /* RESEARCH SECTION */
  .research {
    background: var(--pine);
    color: var(--cream);
    position: relative;
    overflow: hidden;
  }

  .research::before {
    content: 'RESEARCH';
    position: absolute;
    font-family: 'Playfair Display', serif;
    font-size: 18vw;
    font-weight: 900;
    color: rgba(255,255,255,0.02);
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    white-space: nowrap;
    pointer-events: none;
  }

  .research .section-title {
    color: var(--cream);
  }

  .research-layout {
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: 6rem;
    align-items: start;
    margin-top: 3rem;
    position: relative;
    z-index: 2;
  }

  .research-body {
    font-size: 1.1rem;
    font-weight: 300;
    color: rgba(242, 237, 228, 0.75);
    line-height: 1.8;
    margin-bottom: 2rem;
  }

  .research-card {
    background: rgba(242, 237, 228, 0.04);
    border: 1px solid rgba(242, 237, 228, 0.1);
    padding: 2rem 2.5rem;
    margin-bottom: 1.5rem;
    transition: background 0.3s, border-color 0.3s;
  }

  .research-card:hover {
    background: rgba(242, 237, 228, 0.07);
    border-color: rgba(196, 92, 42, 0.4);
  }

  .research-card-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--ember);
    margin-bottom: 0.5rem;
  }

  .research-card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 700;
    color: var(--cream);
    margin-bottom: 0.5rem;
  }

  .research-card-body {
    font-size: 0.95rem;
    color: rgba(242, 237, 228, 0.6);
    font-weight: 300;
  }

  /* GET INVOLVED */
  .involved {
    background: var(--cream);
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 6rem;
    align-items: center;
  }

  .involved-form {
    background: white;
    padding: 3rem;
    border: 1px solid rgba(26, 46, 26, 0.1);
  }

  .form-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 700;
    color: var(--pine);
    margin-bottom: 0.5rem;
  }

  .form-subtitle {
    font-size: 0.95rem;
    color: var(--bark);
    font-weight: 300;
    margin-bottom: 2rem;
  }

  .form-group {
    margin-bottom: 1.2rem;
  }

  .form-group label {
    display: block;
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: var(--pine);
    margin-bottom: 0.4rem;
    opacity: 0.7;
  }

  .form-group input,
  .form-group textarea,
  .form-group select {
    width: 100%;
    padding: 0.8rem 1rem;
    font-family: 'Crimson Pro', serif;
    font-size: 1rem;
    color: var(--pine);
    background: var(--cream);
    border: 1px solid rgba(26, 46, 26, 0.15);
    outline: none;
    transition: border-color 0.2s;
    appearance: none;
  }

  .form-group input:focus,
  .form-group textarea:focus,
  .form-group select:focus {
    border-color: var(--sage);
  }

  .form-group textarea {
    resize: vertical;
    min-height: 100px;
  }

  /* FOOTER */
  footer {
    background: var(--char);
    color: var(--ash);
    padding: 4rem 5rem;
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    gap: 4rem;
  }

  .footer-brand {
    font-family: 'Playfair Display', serif;
    font-size: 1.8rem;
    font-weight: 900;
    color: var(--cream);
    margin-bottom: 1rem;
  }

  .footer-tagline {
    font-size: 0.95rem;
    font-weight: 300;
    color: rgba(196, 191, 179, 0.6);
    max-width: 300px;
    line-height: 1.7;
  }

  .footer-heading {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--ember);
    margin-bottom: 1.2rem;
  }

  .footer-links {
    list-style: none;
  }

  .footer-links li {
    margin-bottom: 0.7rem;
  }

  .footer-links a {
    color: rgba(196, 191, 179, 0.6);
    text-decoration: none;
    font-size: 0.95rem;
    font-weight: 300;
    transition: color 0.2s;
  }

  .footer-links a:hover {
    color: var(--cream);
  }

  .footer-bottom {
    background: var(--char);
    border-top: 1px solid rgba(196, 191, 179, 0.08);
    padding: 1.5rem 5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .footer-bottom-text {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.08em;
    color: rgba(196, 191, 179, 0.3);
    text-transform: uppercase;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes ticker {
    from { transform: translateX(0); }
    to { transform: translateX(-50%); }
  }

  /* SCROLL REVEAL */
  .reveal {
    opacity: 0;
    transform: translateY(30px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .reveal.visible {
    opacity: 1;
    transform: translateY(0);
  }

  /* Stagger children */
  .reveal-stagger > * {
    opacity: 0;
    transform: translateY(25px);
    transition: opacity 0.6s ease, transform 0.6s ease;
  }

  .reveal-stagger.visible > *:nth-child(1) { opacity: 1; transform: none; transition-delay: 0s; }
  .reveal-stagger.visible > *:nth-child(2) { opacity: 1; transform: none; transition-delay: 0.15s; }
  .reveal-stagger.visible > *:nth-child(3) { opacity: 1; transform: none; transition-delay: 0.3s; }

  /* STICKY SCROLL WRAPPER — forest density + fire combined */
  .density-sticky-wrapper {
    height: 600vh;
    position: relative;
  }

  .density-sticky {
    position: sticky;
    top: 0;
    height: 100vh;
    overflow: hidden;
    background: #0a0d0a;
  }

  #density-canvas {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
  }

  /* HUD — fixed at top of sticky container */
  .density-hud {
    position: absolute;
    top: 2.5rem;
    left: 0;
    right: 0;
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
    text-align: center;
    pointer-events: none;
    padding: 0 2rem;
  }

  .density-year {
    font-family: 'Playfair Display', serif;
    font-size: clamp(4rem, 10vw, 8rem);
    font-weight: 900;
    color: rgba(242, 237, 228, 0.12);
    line-height: 1;
    display: block;
    letter-spacing: -0.02em;
  }

  .density-info-row {
    display: flex;
    justify-content: center;
    align-items: baseline;
    gap: 0.5rem;
    margin-top: 0.3rem;
  }

  .density-trees-count {
    font-family: 'Playfair Display', serif;
    font-size: clamp(1.8rem, 3.5vw, 2.8rem);
    font-weight: 900;
    color: #6b7c5a;
    line-height: 1;
    transition: color 0.4s;
  }

  .density-trees-unit {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.4);
  }

  .density-status {
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.35);
    display: block;
    margin-top: 0.5rem;
    transition: color 0.4s;
  }

  /* FIRE RISK GAUGE — right side, simple red fill */
  .fire-risk-meter {
    position: absolute;
    right: 2.5rem;
    top: 50%;
    transform: translateY(-50%);
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.6rem;
    pointer-events: none;
  }

  .fire-risk-label-top {
    font-family: 'Space Mono', monospace;
    font-size: 0.5rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(196, 92, 42, 0.6);
    writing-mode: vertical-rl;
    transform: rotate(180deg);
  }

  .fire-risk-track {
    width: 8px;
    height: 200px;
    background: rgba(255,255,255,0.05);
    border-radius: 4px;
    border: 1px solid rgba(255,255,255,0.08);
    position: relative;
    overflow: hidden;
  }

  .fire-risk-fill {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 0%;
    background: linear-gradient(to top, #8B0000, #c45c2a, #ff4400);
    border-radius: 4px;
    transition: height 0.05s linear;
  }

  .fire-risk-label-bottom {
    font-family: 'Space Mono', monospace;
    font-size: 0.5rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(107, 124, 90, 0.5);
    writing-mode: vertical-rl;
    transform: rotate(180deg);
  }

  .fire-risk-icon {
    font-size: 1rem;
    opacity: 0;
    transition: opacity 0.4s;
  }

  /* LEFT — time progress bar */
  .density-progress-bar {
    position: absolute;
    left: 2.5rem;
    top: 50%;
    transform: translateY(-50%);
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.7rem;
    pointer-events: none;
  }

  .progress-label-top {
    font-family: 'Space Mono', monospace;
    font-size: 0.5rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.3);
    writing-mode: vertical-rl;
    transform: rotate(180deg);
  }

  .progress-track {
    width: 2px;
    height: 200px;
    background: rgba(196, 191, 179, 0.08);
    border-radius: 2px;
    position: relative;
    overflow: hidden;
  }

  .progress-fill {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    background: rgba(196, 191, 179, 0.3);
    border-radius: 2px;
    transition: height 0.05s linear;
  }

  .progress-label-bottom {
    font-family: 'Space Mono', monospace;
    font-size: 0.5rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.3);
    writing-mode: vertical-rl;
    transform: rotate(180deg);
  }

  /* SCROLL ARROW */
  .scroll-arrow {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    z-index: 20;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.4rem;
    pointer-events: none;
    transition: opacity 0.5s;
  }

  .scroll-arrow-label {
    font-family: 'Space Mono', monospace;
    font-size: 0.55rem;
    letter-spacing: 0.18em;
    text-transform: uppercase;
    color: rgba(196, 191, 179, 0.35);
  }

  .scroll-arrow-icon {
    width: 24px;
    height: 24px;
    animation: arrowBounce 1.5s ease-in-out infinite;
  }

  @keyframes arrowBounce {
    0%, 100% { transform: translateY(0); opacity: 0.4; }
    50% { transform: translateY(6px); opacity: 0.9; }
  }

  /* WARNING FLASH */
  .density-warning {
    position: absolute;
    top: 2rem;
    left: 50%;
    transform: translateX(-50%);
    z-index: 20;
    font-family: 'Space Mono', monospace;
    font-size: 0.6rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: #c45c2a;
    opacity: 0;
    transition: opacity 0.5s;
    white-space: nowrap;
    border: 1px solid rgba(196, 92, 42, 0.3);
    padding: 0.5rem 1.2rem;
    background: rgba(13, 13, 11, 0.6);
  }

  /* FIRE OVERLAY — renders over density canvas at high progress */
  #fire-canvas {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    opacity: 0;
    transition: opacity 0.3s;
    z-index: 15;
  }

  .fire-text-overlay {
    position: absolute;
    bottom: 12%;
    left: 50%;
    transform: translateX(-50%);
    z-index: 25;
    text-align: center;
    max-width: 560px;
    padding: 2rem 2.5rem;
    background: rgba(10, 8, 5, 0.75);
    backdrop-filter: blur(6px);
    border: 1px solid rgba(196, 92, 42, 0.25);
    opacity: 0;
    transition: opacity 0.6s;
    pointer-events: none;
    width: 90%;
  }

  .fire-text-overlay .section-label { color: #ff8c42; }
  .fire-text-overlay .section-title {
    color: var(--cream);
    font-size: clamp(1.5rem, 3vw, 2.4rem);
    margin-bottom: 0.8rem;
  }
  .fire-text-overlay p {
    color: rgba(242, 237, 228, 0.65);
    font-weight: 300;
    font-size: 1rem;
    line-height: 1.75;
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#" class="nav-logo">Flagstaff Pine Conservancy</a>
  <ul class="nav-links">
    <li><a href="#crisis">The Crisis</a></li>
    <li><a href="#approach">Our Approach</a></li>
    <li><a href="#research">Research</a></li>
    <li><a href="#involved">Get Involved</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-left">
    <p class="hero-eyebrow">Flagstaff, Arizona — Est. 2026</p>
    <h1 class="hero-title">
      Protecting<br><em>Ponderosa</em><br>Country
    </h1>
    <p class="hero-subtitle">
      The forests surrounding Flagstaff face an existential threat. We are working to change that — through research, policy advocacy, and community action.
    </p>
    <div class="hero-cta">
      <a href="#involved" class="btn-primary">Get Involved</a>
      <a href="#crisis" class="btn-outline">Learn More</a>
    </div>
  </div>

  <div class="hero-right">
    <div class="hero-forest">
      <!-- SVG Forest Scene -->
      <svg class="forest-svg" viewBox="0 0 600 700" xmlns="http://www.w3.org/2000/svg" preserveAspectRatio="xMidYMax meet">
        <!-- Sky gradient -->
        <defs>
          <linearGradient id="skyGrad" x1="0" y1="0" x2="0" y2="1">
            <stop offset="0%" stop-color="#0d1a0d"/>
            <stop offset="60%" stop-color="#1a2e1a"/>
            <stop offset="100%" stop-color="#2a3d1a"/>
          </linearGradient>
          <linearGradient id="moonGlow" cx="50%" cy="50%" r="50%" fx="50%" fy="50%" id="moonGlow" gradientUnits="objectBoundingBox">
            <stop offset="0%" stop-color="#f2ede4" stop-opacity="0.15"/>
            <stop offset="100%" stop-color="#f2ede4" stop-opacity="0"/>
          </linearGradient>
        </defs>
        <rect width="600" height="700" fill="url(#skyGrad)"/>

        <!-- Stars -->
        <circle cx="80" cy="60" r="1" fill="#f2ede4" opacity="0.6"/>
        <circle cx="150" cy="40" r="1.5" fill="#f2ede4" opacity="0.5"/>
        <circle cx="230" cy="80" r="1" fill="#f2ede4" opacity="0.7"/>
        <circle cx="320" cy="30" r="1" fill="#f2ede4" opacity="0.4"/>
        <circle cx="400" cy="55" r="1.5" fill="#f2ede4" opacity="0.6"/>
        <circle cx="480" cy="35" r="1" fill="#f2ede4" opacity="0.5"/>
        <circle cx="550" cy="70" r="1" fill="#f2ede4" opacity="0.7"/>
        <circle cx="50" cy="120" r="1" fill="#f2ede4" opacity="0.3"/>
        <circle cx="170" cy="100" r="1" fill="#f2ede4" opacity="0.5"/>
        <circle cx="430" cy="90" r="1.5" fill="#f2ede4" opacity="0.4"/>
        <circle cx="510" cy="110" r="1" fill="#f2ede4" opacity="0.6"/>

        <!-- Moon -->
        <circle cx="480" cy="80" r="28" fill="#c4bfb3" opacity="0.15"/>
        <circle cx="480" cy="80" r="20" fill="#f2ede4" opacity="0.12"/>

        <!-- Distant tree line (dark) -->
        <g opacity="0.4">
          <polygon points="30,420 55,340 80,420" fill="#0d1a0d"/>
          <polygon points="60,420 90,330 120,420" fill="#0d1a0d"/>
          <polygon points="100,420 125,350 150,420" fill="#0d1a0d"/>
          <polygon points="480,420 510,320 540,420" fill="#0d1a0d"/>
          <polygon points="520,420 550,340 580,420" fill="#0d1a0d"/>
        </g>

        <!-- Mid trees -->
        <g opacity="0.65">
          <!-- Tree 1 -->
          <rect x="88" y="390" width="8" height="80" fill="#3d2b1f"/>
          <polygon points="92,230 65,390 119,390" fill="#1a3a1a"/>
          <polygon points="92,270 68,390 116,390" fill="#1f4020"/>
          <polygon points="92,310 72,390 112,390" fill="#1a3a1a"/>

          <!-- Tree 2 -->
          <rect x="178" y="400" width="7" height="70" fill="#3d2b1f"/>
          <polygon points="181,250 158,400 204,400" fill="#162e16"/>
          <polygon points="181,290 160,400 202,400" fill="#1a3510"/>
          <polygon points="181,330 163,400 199,400" fill="#162e16"/>

          <!-- Tree 3 -->
          <rect x="308" y="385" width="9" height="85" fill="#3d2b1f"/>
          <polygon points="312,210 282,385 342,385" fill="#1a3a1a"/>
          <polygon points="312,255 285,385 339,385" fill="#1f4020"/>
          <polygon points="312,300 288,385 336,385" fill="#1a3a1a"/>
          <polygon points="312,340 292,385 332,385" fill="#1f4020"/>

          <!-- Tree 4 -->
          <rect x="428" y="395" width="8" height="75" fill="#3d2b1f"/>
          <polygon points="432,240 405,395 459,395" fill="#162e16"/>
          <polygon points="432,280 408,395 456,395" fill="#1a3510"/>
          <polygon points="432,320 411,395 453,395" fill="#162e16"/>

          <!-- Tree 5 -->
          <rect x="538" y="400" width="7" height="70" fill="#3d2b1f"/>
          <polygon points="541,255 518,400 564,400" fill="#1a3a1a"/>
          <polygon points="541,295 521,400 561,400" fill="#1f4020"/>
          <polygon points="541,335 524,400 558,400" fill="#1a3a1a"/>
        </g>

        <!-- Foreground trees (darkest) -->
        <g opacity="0.9">
          <!-- Left foreground -->
          <rect x="18" y="430" width="12" height="270" fill="#2a1f15"/>
          <polygon points="24,200 -15,430 63,430" fill="#0d1a0d"/>
          <polygon points="24,255 -10,430 58,430" fill="#112211"/>
          <polygon points="24,310 -5,430 53,430" fill="#0d1a0d"/>
          <polygon points="24,360 0,430 48,430" fill="#112211"/>

          <!-- Right foreground -->
          <rect x="568" y="440" width="12" height="260" fill="#2a1f15"/>
          <polygon points="574,210 535,440 613,440" fill="#0d1a0d"/>
          <polygon points="574,265 538,440 610,440" fill="#112211"/>
          <polygon points="574,320 542,440 606,440" fill="#0d1a0d"/>
          <polygon points="574,370 546,440 602,440" fill="#112211"/>
        </g>

        <!-- Ground -->
        <rect x="0" y="460" width="600" height="240" fill="#0d1a0d"/>
        <rect x="0" y="460" width="600" height="30" fill="#112211" opacity="0.8"/>

        <!-- Ember glow at base (fire/char effect) -->
        <ellipse cx="300" cy="470" rx="200" ry="15" fill="#c45c2a" opacity="0.06"/>

        <!-- Ground texture lines -->
        <line x1="0" y1="480" x2="600" y2="480" stroke="#1a2e1a" stroke-width="1" opacity="0.3"/>
        <line x1="0" y1="500" x2="600" y2="500" stroke="#1a2e1a" stroke-width="1" opacity="0.2"/>
      </svg>

      <div class="hero-stat-overlay">
        <div class="hero-stat">
          <span class="hero-stat-num">2.4M</span>
          <span class="hero-stat-label">Acres of Ponderosa Pine at risk</span>
        </div>
        <div class="hero-stat">
          <span class="hero-stat-num">150%</span>
          <span class="hero-stat-label">Increase in wildfire intensity since 1980</span>
        </div>
        <div class="hero-stat">
          <span class="hero-stat-num">85%</span>
          <span class="hero-stat-label">Of forests overstocked beyond historic density</span>
        </div>
        <div class="hero-stat">
          <span class="hero-stat-num">$100</span>
          <span class="hero-stat-label">Cost of modular biochar unit we're developing</span>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker">
  <div class="ticker-inner">
    <span class="ticker-item">Forest Restoration</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Biochar Research</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Wildfire Prevention</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Carbon Sequestration</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Community Action</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Policy Advocacy</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Flagstaff, Arizona</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Forest Restoration</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Biochar Research</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Wildfire Prevention</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Carbon Sequestration</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Community Action</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Policy Advocacy</span>
    <span class="ticker-dot">✦</span>
    <span class="ticker-item">Flagstaff, Arizona</span>
    <span class="ticker-dot">✦</span>
  </div>
</div>

<!-- FOREST DENSITY + FIRE SCROLL (unified sticky) -->
<div class="density-sticky-wrapper">
  <div class="density-sticky">
    <!-- Forest canvas (background) -->
    <canvas id="density-canvas"></canvas>
    <!-- Fire canvas (overlaid at high progress) -->
    <canvas id="fire-canvas"></canvas>

    <!-- Fire risk gauge — right side -->
    <div class="fire-risk-meter">
      <span class="fire-risk-icon" id="fire-risk-icon">🔥</span>
      <span class="fire-risk-label-top">High Risk</span>
      <div class="fire-risk-track">
        <div class="fire-risk-fill" id="fire-risk-fill"></div>
      </div>
      <span class="fire-risk-label-bottom">Low Risk</span>
    </div>

    <!-- Time progress — left side -->
    <div class="density-progress-bar">
      <span class="progress-label-top">Today</span>
      <div class="progress-track">
        <div class="progress-fill" id="progress-fill" style="height:0%"></div>
      </div>
      <span class="progress-label-bottom">1900</span>
    </div>

    <!-- Warning badge top -->
    <div class="density-warning" id="density-warning">⚠ Critical fire risk — overstocked forest</div>

    <!-- Central HUD -->
    <div class="density-hud">
      <span class="density-year" id="density-year">1900</span>
      <div class="density-info-row">
        <span class="density-trees-count" id="density-count">50</span>
        <span class="density-trees-unit">trees / acre</span>
      </div>
      <span class="density-status" id="density-status">Healthy historical forest</span>
    </div>

    <!-- Scroll arrow -->
    <div class="scroll-arrow" id="scroll-arrow">
      <span class="scroll-arrow-label">Scroll through time</span>
      <svg class="scroll-arrow-icon" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M12 5v14M5 12l7 7 7-7" stroke="rgba(196,191,179,0.5)" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <!-- Fire text overlay (appears at end) -->
    <div class="fire-text-overlay" id="fire-text-overlay">
      <p class="section-label">The Consequence</p>
      <h2 class="section-title">Overstocked Forests Become Infernos</h2>
      <p>When trees compete for water and light at 10× historical density, the entire forest becomes catastrophic fuel. One spark reshapes the landscape for generations.</p>
    </div>
  </div>
</div>

<!-- CRISIS -->
<section class="crisis reveal" id="crisis">
  <div>
    <p class="section-label">The Problem</p>
    <h2 class="section-title">Northern Arizona's Forests Are in Crisis</h2>
    <p class="crisis-body">
      A century of fire suppression has left Flagstaff's ponderosa pine forests dangerously overstocked. Where historical forests had 50–100 trees per acre, today's forests often exceed 1,000. The result is catastrophic wildfire risk, accelerating beetle infestations, and a carbon cycle spinning out of balance.
    </p>
    <p class="crisis-body" style="margin-top:1rem;">
      The slash piles left behind from necessary thinning operations represent both a problem and an opportunity. The Flagstaff Pine Conservancy is developing low-cost, modular solutions to turn forest waste into biochar — sequestering carbon while reducing fuel loads.
    </p>
  </div>
  <div class="crisis-stats reveal-stagger">
    <div class="crisis-stat-box">
      <span class="crisis-num">10×</span>
      <span class="crisis-desc">Current tree density vs.<br>historical baseline</span>
    </div>
    <div class="crisis-stat-box">
      <span class="crisis-num">400K</span>
      <span class="crisis-desc">Acres treated through<br>Four Forest Restoration Initiative</span>
    </div>
    <div class="crisis-stat-box">
      <span class="crisis-num">$1B+</span>
      <span class="crisis-desc">Annual wildfire suppression<br>costs in Arizona</span>
    </div>
    <div class="crisis-stat-box">
      <span class="crisis-num">50yr</span>
      <span class="crisis-desc">Timeline for full forest<br>restoration at current pace</span>
    </div>
  </div>
</section>

<!-- APPROACH -->
<section class="approach" id="approach">
  <div class="reveal">
    <p class="section-label">What We Do</p>
    <h2 class="section-title">A Three-Part Approach to Forest Resilience</h2>
  </div>
  <div class="approach-grid reveal-stagger">
    <div class="approach-card">
      <span class="approach-number">01</span>
      <span class="approach-icon">🔬</span>
      <h3 class="approach-card-title">Applied Research</h3>
      <p class="approach-card-body">Developing a $100 modular TLUD biochar reactor optimized for ponderosa pine slash — in collaboration with NAU's Ecological Restoration Institute. Making forest restoration technology accessible to private landowners.</p>
    </div>
    <div class="approach-card">
      <span class="approach-number">02</span>
      <span class="approach-icon">📋</span>
      <h3 class="approach-card-title">Policy Advocacy</h3>
      <p class="approach-card-body">Engaging with the Greater Flagstaff Forests Partnership, Coconino County flood control, and city sustainability programs to translate research into actionable forest management policy.</p>
    </div>
    <div class="approach-card">
      <span class="approach-number">03</span>
      <span class="approach-icon">🌲</span>
      <h3 class="approach-card-title">Community Education</h3>
      <p class="approach-card-body">Building public understanding of the forest crisis through workshops, stakeholder engagement, and accessible resources that empower Flagstaff residents to take action on their own land.</p>
    </div>
  </div>
</section>

<!-- RESEARCH -->
<section class="research reveal" id="research">
  <div>
    <p class="section-label">Current Work</p>
    <h2 class="section-title">Research in Progress</h2>
  </div>
  <div class="research-layout">
    <div>
      <p class="research-body">
        Our flagship project is the design and testing of a low-cost, modular biochar reactor suited to Flagstaff's distributed slash pile problem. Working with Dr. Han-Sup Han and Dr. Dipita Ghosh at NAU's Ecological Restoration Institute, we are optimizing secondary air control and residence time parameters to produce consistent, high-quality biochar from ponderosa pine feedstock.
      </p>
      <p class="research-body">
        The goal is a system that costs under $100 to build, can be deployed by private landowners without specialized training, and produces biochar suitable for soil amendment and carbon sequestration verification.
      </p>
      <a href="#involved" class="btn-outline" style="color: var(--cream); border-color: rgba(242,237,228,0.3); margin-top:1rem;">Follow Our Research</a>
    </div>
    <div>
      <div class="research-card">
        <p class="research-card-label">Phase 1 — Complete</p>
        <h4 class="research-card-title">Literature Review & Design</h4>
        <p class="research-card-body">Reviewed peer-reviewed pyrolysis literature. Analyzed TLUD vs. fixed-bed systems for Flagstaff context. Completed 3D SketchUp prototype design with NAU faculty feedback.</p>
      </div>
      <div class="research-card">
        <p class="research-card-label">Phase 2 — In Progress</p>
        <h4 class="research-card-title">Baseline Testing</h4>
        <p class="research-card-body">Collected ponderosa pine biochar samples from NAU lab for control comparisons. Beginning experimental testing of secondary air control configurations and quench protocols.</p>
      </div>
      <div class="research-card">
        <p class="research-card-label">Phase 3 — Upcoming</p>
        <h4 class="research-card-title">Field Deployment & Analysis</h4>
        <p class="research-card-body">Full prototype build and testing. Biochar property analysis including surface area, ash content, and carbon stability. Presenting findings to GFFP stakeholders and county leadership.</p>
      </div>
    </div>
  </div>
</section>

<!-- GET INVOLVED -->
<section class="involved" id="involved">
  <div class="reveal">
    <p class="section-label">Take Action</p>
    <h2 class="section-title">Join the effort to protect Flagstaff's forests</h2>
    <p style="font-size:1.1rem; font-weight:300; color:var(--bark); line-height:1.8; margin-bottom:2rem;">
      Whether you're a landowner with slash piles, a researcher, a policy advocate, or simply someone who loves these forests — there's a place for you here.
    </p>
    <p style="font-size:1.1rem; font-weight:300; color:var(--bark); line-height:1.8;">
      We are actively seeking connections with forest management professionals, academic collaborators, and community members who want to contribute to a more resilient landscape around Flagstaff.
    </p>
  </div>
  <div class="involved-form reveal">
    <h3 class="form-title">Get in Touch</h3>
    <p class="form-subtitle">We'll respond within 48 hours.</p>
    <div class="form-group">
      <label>Your Name</label>
      <input type="text" placeholder="Full name">
    </div>
    <div class="form-group">
      <label>Email Address</label>
      <input type="email" placeholder="your@email.com">
    </div>
    <div class="form-group">
      <label>How can you help?</label>
      <select>
        <option value="">Select an option</option>
        <option>I'm a landowner with slash piles</option>
        <option>I'm a researcher or academic</option>
        <option>I work in forest policy</option>
        <option>I want to volunteer</option>
        <option>I'm a student interested in the project</option>
        <option>Other</option>
      </select>
    </div>
    <div class="form-group">
      <label>Message</label>
      <textarea placeholder="Tell us about your interest or how you'd like to get involved..."></textarea>
    </div>
    <button class="btn-primary" style="width:100%; padding:1rem; font-size:0.75rem;">Send Message</button>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div>
    <div class="footer-brand">Flagstaff Pine Conservancy</div>
    <p class="footer-tagline">Working to protect and restore the ponderosa pine forests of Northern Arizona through research, advocacy, and community action.</p>
  </div>
  <div>
    <p class="footer-heading">Navigate</p>
    <ul class="footer-links">
      <li><a href="#crisis">The Crisis</a></li>
      <li><a href="#approach">Our Approach</a></li>
      <li><a href="#research">Research</a></li>
      <li><a href="#involved">Get Involved</a></li>
    </ul>
  </div>
  <div>
    <p class="footer-heading">Connect</p>
    <ul class="footer-links">
      <li><a href="#">Greater Flagstaff Forests Partnership</a></li>
      <li><a href="#">NAU Ecological Restoration Institute</a></li>
      <li><a href="#">Coconino County Flood Control</a></li>
      <li><a href="#">City of Flagstaff Sustainability</a></li>
    </ul>
  </div>
</footer>
<div class="footer-bottom">
  <span class="footer-bottom-text">© 2026 Flagstaff Pine Conservancy — Flagstaff, Arizona</span>
  <span class="footer-bottom-text">Protecting Ponderosa Country</span>
</div>

<script>
  // ============================================================
  // SCROLL REVEAL
  // ============================================================
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => { if (entry.isIntersecting) entry.target.classList.add('visible'); });
  }, { threshold: 0.1, rootMargin: '0px 0px -50px 0px' });
  document.querySelectorAll('.reveal, .reveal-stagger').forEach(el => observer.observe(el));

  // ============================================================
  // FOREST DENSITY SCROLL
  // ============================================================
  const densityCanvas = document.getElementById('density-canvas');
  const dctx = densityCanvas.getContext('2d');

  function resizeDensityCanvas() {
    densityCanvas.width = densityCanvas.offsetWidth;
    densityCanvas.height = densityCanvas.offsetHeight;
  }
  resizeDensityCanvas();
  window.addEventListener('resize', resizeDensityCanvas);

  // Stable seeded random so tree positions don't jump
  function mulberry32(seed) {
    return function() {
      seed |= 0; seed = seed + 0x6D2B79F5 | 0;
      let t = Math.imul(seed ^ seed >>> 15, 1 | seed);
      t = t + Math.imul(t ^ t >>> 7, 61 | t) ^ t;
      return ((t ^ t >>> 14) >>> 0) / 4294967296;
    };
  }

  // Pre-generate fixed tree positions once
  const MAX_TREES = 800;
  const treeData = [];
  const rng = mulberry32(42);
  for (let i = 0; i < MAX_TREES; i++) {
    treeData.push({
      x: rng(),       // 0-1 normalized x
      row: rng(),     // 0-1 normalized depth (0=far, 1=close)
      h: 0.5 + rng() * 0.5,  // relative height multiplier
      jitter: (rng() - 0.5) * 0.04
    });
  }

  function drawPineTree(ctx, x, y, height, alpha) {
    const trunkH = height * 0.28;
    const trunkW = Math.max(2, height * 0.06);

    ctx.save();
    ctx.globalAlpha = alpha;

    // Trunk — brown
    ctx.fillStyle = '#5c3d1e';
    ctx.fillRect(x - trunkW / 2, y - trunkH, trunkW, trunkH);

    // Pine layers — visible green
    const layers = 4;
    const colors = ['#2d5a1b', '#366e20', '#3d7a25', '#4a8c2e'];
    for (let i = 0; i < layers; i++) {
      const ly    = y - trunkH - i * height * 0.16;
      const lw    = height * 0.55 * (1 - i * 0.18);
      const lh    = height * 0.22;
      ctx.fillStyle = colors[Math.min(i, colors.length - 1)];
      ctx.beginPath();
      ctx.moveTo(x, ly - lh);
      ctx.lineTo(x - lw / 2, ly);
      ctx.lineTo(x + lw / 2, ly);
      ctx.closePath();
      ctx.fill();
    }

    ctx.restore();
  }

  function renderForest(progress) {
    const w = densityCanvas.width;
    const h = densityCanvas.height;
    dctx.clearRect(0, 0, w, h);

    // Night sky gradient
    const sky = dctx.createLinearGradient(0, 0, 0, h * 0.7);
    sky.addColorStop(0, '#0a0f0a');
    sky.addColorStop(1, '#162316');
    dctx.fillStyle = sky;
    dctx.fillRect(0, 0, w, h);

    // Stars fade as trees fill in
    const starOp = Math.max(0, 0.7 - progress * 0.9);
    if (starOp > 0.02) {
      const sr = mulberry32(99);
      for (let i = 0; i < 60; i++) {
        dctx.beginPath();
        dctx.arc(sr() * w, sr() * h * 0.5, sr() + 0.3, 0, Math.PI * 2);
        dctx.fillStyle = `rgba(242,237,228,${starOp * (0.3 + sr() * 0.7)})`;
        dctx.fill();
      }
    }

    const groundY = h * 0.78;

    // How many trees to show: 8 → MAX_TREES
    const treeCount = Math.floor(8 + progress * (MAX_TREES - 8));

    // Sort the slice by row (far to near = painters algorithm)
    const slice = treeData.slice(0, treeCount).sort((a, b) => a.row - b.row);

    slice.forEach(t => {
      const depth = t.row; // 0=far, 1=near
      const screenX = (t.x + t.jitter * (1 - depth)) * w;
      // Far trees appear higher up, near trees near groundY
      const screenY = groundY - depth * h * 0.35 + (1 - depth) * h * 0.05;
      const treeH   = (30 + depth * 100) * t.h;
      // Near trees are fully opaque, far trees slightly faded
      const alpha   = 0.4 + depth * 0.6;

      drawPineTree(dctx, screenX, screenY, treeH, alpha);
    });

    // Ground strip
    const gr = dctx.createLinearGradient(0, groundY, 0, h);
    gr.addColorStop(0, '#1a2e10');
    gr.addColorStop(1, '#0d1a08');
    dctx.fillStyle = gr;
    dctx.fillRect(0, groundY, w, h - groundY);

    // Density haze at high progress
    if (progress > 0.4) {
      dctx.fillStyle = `rgba(5,10,5,${(progress - 0.4) * 0.45})`;
      dctx.fillRect(0, 0, w, h);
    }

    // --- UI updates ---
    const year = Math.floor(1900 + progress * 125);
    document.getElementById('density-year').textContent = year;
    document.getElementById('density-count').textContent = treeCount.toLocaleString();

    const ce = document.getElementById('density-count');
    ce.style.color = progress > 0.65 ? '#c45c2a' : progress > 0.35 ? '#c49a2a' : '#6b7c5a';

    const se = document.getElementById('density-status');
    if (progress > 0.8)       { se.textContent = '⚠ Critical — catastrophic fire risk'; se.style.color = 'rgba(196,92,42,0.8)'; }
    else if (progress > 0.55) { se.textContent = 'Severely overstocked'; se.style.color = 'rgba(196,154,42,0.7)'; }
    else if (progress > 0.28) { se.textContent = 'Overcrowding accelerating'; se.style.color = 'rgba(196,191,179,0.45)'; }
    else                      { se.textContent = 'Healthy historical forest'; se.style.color = 'rgba(107,124,90,0.7)'; }

    // Year ghost color intensifies
    const ye = document.getElementById('density-year');
    ye.style.color = progress > 0.7
      ? `rgba(${Math.floor(180 + progress * 60)},${Math.floor(40 - progress * 30)},5,${0.1 + progress * 0.15})`
      : `rgba(242,237,228,${0.07 + progress * 0.05})`;

    // Left time bar
    document.getElementById('progress-fill').style.height = (progress * 100) + '%';

    // RIGHT fire gauge — direct red fill
    const gauge = document.getElementById('fire-risk-fill');
    gauge.style.height = (progress * 100) + '%';

    // Fire icon
    const icon = document.getElementById('fire-risk-icon');
    icon.style.opacity = progress > 0.4 ? Math.min(1, (progress - 0.4) / 0.2) : 0;

    // Warning
    const we = document.getElementById('density-warning');
    if (we) we.style.opacity = progress > 0.7 ? Math.min(1, (progress - 0.7) / 0.1) : 0;

    // Scroll arrow fades out
    const ae = document.getElementById('scroll-arrow');
    if (ae) ae.style.opacity = progress < 0.05 ? 1 : Math.max(0, 1 - (progress - 0.05) / 0.08);
  }

  // ============================================================
  // FIRE SIMULATION (overlaid at end of scroll)
  // ============================================================
  const fireCanvas = document.getElementById('fire-canvas');
  const fctx = fireCanvas.getContext('2d');

  function resizeFireCanvas() {
    fireCanvas.width  = fireCanvas.offsetWidth;
    fireCanvas.height = fireCanvas.offsetHeight;
    initFire();
  }

  const FIRE_SCALE = 3;
  let fireW, fireH, firePixels, firePalette;

  function buildFirePalette() {
    firePalette = [];
    for (let i = 0; i < 256; i++) {
      let r, g, b;
      if      (i < 50)  { r = Math.floor(i * 2.5); g = 0; b = 0; }
      else if (i < 110) { r = Math.min(255, 125 + (i-50)*2.1); g = Math.floor((i-50)*1.5); b = 0; }
      else if (i < 185) { r = 255; g = Math.floor((i-110)*3.4); b = 0; }
      else              { r = 255; g = 255; b = Math.floor((i-185)*3.6); }
      firePalette.push([r, g, b]);
    }
  }

  function initFire() {
    fireW = Math.ceil(fireCanvas.width  / FIRE_SCALE);
    fireH = Math.ceil(fireCanvas.height / FIRE_SCALE);
    firePixels = new Uint8Array(fireW * fireH).fill(0);
    buildFirePalette();
    for (let x = 0; x < fireW; x++) {
      firePixels[(fireH-1)*fireW+x] = 255;
      firePixels[(fireH-2)*fireW+x] = 200 + Math.floor(Math.random()*55);
    }
  }

  function spreadFire() {
    for (let y = 0; y < fireH-1; y++) {
      for (let x = 0; x < fireW; x++) {
        const src = firePixels[(y+1)*fireW+x];
        const decay  = Math.floor(Math.random()*3);
        const spread = Math.floor(Math.random()*3)-1;
        const nx = Math.max(0, Math.min(fireW-1, x+spread));
        firePixels[y*fireW+nx] = Math.max(0, src-decay);
      }
    }
    for (let x = 0; x < fireW; x++) {
      if (Math.random() > 0.05)
        firePixels[(fireH-1)*fireW+x] = 210 + Math.floor(Math.random()*45);
    }
  }

  function renderFireCanvas() {
    spreadFire();
    const w = fireCanvas.width, h = fireCanvas.height;
    const id = fctx.createImageData(w, h);
    const data = id.data;
    for (let y = 0; y < fireH; y++) {
      for (let x = 0; x < fireW; x++) {
        const val = firePixels[y*fireW+x];
        const [r,g,b] = firePalette[val];
        for (let sy = 0; sy < FIRE_SCALE; sy++) {
          for (let sx = 0; sx < FIRE_SCALE; sx++) {
            const px = ((y*FIRE_SCALE+sy)*w+(x*FIRE_SCALE+sx))*4;
            data[px]=r; data[px+1]=g; data[px+2]=b; data[px+3]=val>4?255:0;
          }
        }
      }
    }
    fctx.putImageData(id, 0, 0);
    fctx.globalCompositeOperation='destination-over';
    fctx.fillStyle='rgba(0,0,0,0)';
    fctx.fillRect(0,0,w,h);
    fctx.globalCompositeOperation='source-over';

    // Tree silhouettes on top of fire
    const tr = mulberry32(555);
    for (let i = 0; i < 18; i++) {
      const tx=(i/18)*w+tr()*(w/18), th=70+tr()*130, gy=h*0.75;
      fctx.globalAlpha=0.9; fctx.fillStyle='#060604';
      fctx.fillRect(tx-th*0.03, gy-th*0.28, th*0.06, th*0.28);
      for (let l=0;l<4;l++){
        const ly=gy-th*0.22-l*th*0.2, lw=th*0.48*(1-l*0.19);
        fctx.beginPath(); fctx.moveTo(tx,ly-th*0.23);
        fctx.lineTo(tx-lw/2,ly); fctx.lineTo(tx+lw/2,ly);
        fctx.closePath(); fctx.fill();
      }
    }
    fctx.globalAlpha=1;
    fctx.fillStyle='#060400'; fctx.fillRect(0,h*0.75,w,h*0.25);

    // Embers
    embers.forEach((e,i) => {
      e.y-=e.vy; e.x+=e.vx+(Math.random()-0.5)*0.5; e.life-=0.007+Math.random()*0.006;
      if(e.life<=0||e.y<0){ embers[i]=mkEmber(w,h); return; }
      fctx.save(); fctx.globalAlpha=Math.min(1,e.life*1.3);
      fctx.fillStyle=`rgb(255,${Math.floor(60+e.life*190)},0)`;
      fctx.beginPath(); fctx.arc(e.x,e.y,e.size,0,Math.PI*2); fctx.fill();
      fctx.restore();
    });
  }

  function mkEmber(w,h) {
    return {
      x: Math.random()*w, y: h*0.65+Math.random()*h*0.1,
      vx:(Math.random()-0.5)*2, vy:1+Math.random()*3,
      size:0.5+Math.random()*2, life:0.5+Math.random()*0.5
    };
  }

  let embers=[], fireRunning=false, currentFireIntensity=0;
  function fireLoop(){
    if(!fireRunning) return;
    renderFireCanvas();
    requestAnimationFrame(fireLoop);
  }

  // ============================================================
  // SCROLL HANDLER
  // ============================================================
  const stickyWrapper = document.querySelector('.density-sticky-wrapper');

  function onScroll() {
    const rect    = stickyWrapper.getBoundingClientRect();
    const total   = stickyWrapper.offsetHeight - window.innerHeight;
    const scrolled= -rect.top;
    const progress= Math.max(0, Math.min(1, scrolled / total));

    renderForest(progress);

    // Fire fades in at 75% progress
    const firePhase = Math.max(0, (progress - 0.75) / 0.25);
    fireCanvas.style.opacity = Math.min(1, firePhase * 3);
    currentFireIntensity = firePhase;

    const ftOverlay = document.getElementById('fire-text-overlay');
    if (ftOverlay) ftOverlay.style.opacity = firePhase > 0.4 ? Math.min(1,(firePhase-0.4)/0.3) : 0;

    if (firePhase > 0.05 && !fireRunning) {
      fireRunning = true;
      resizeFireCanvas();
      embers = Array.from({length:120}, ()=>mkEmber(fireCanvas.width, fireCanvas.height));
      fireLoop();
    } else if (firePhase <= 0 && fireRunning) {
      fireRunning = false;
    }
  }

  window.addEventListener('scroll', onScroll, {passive:true});
  renderForest(0);
</script>
</body>
</html>
