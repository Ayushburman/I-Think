```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Steve Jobs — The Journey</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=DM+Mono:wght@300;400;500&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --black: #0a0a0a;
    --white: #f5f0e8;
    --cream: #ede7d9;
    --gold: #c9952a;
    --gold-light: #e8b84b;
    --amber: #d4701c;
    --rust: #8b3a1a;
    --sage: #4a6741;
    --sage-light: #6a8f61;
    --blue-deep: #1a2f4a;
    --blue-mid: #2d5a8e;
    --sand: #c4a882;
    --silver: #a0a0a0;
    --charcoal: #1e1e1e;
    --timeline-col: #c9952a;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--black);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    line-height: 1.6;
    overflow-x: hidden;
  }

  /* ── HERO ── */
  .hero {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    position: relative;
    text-align: center;
    padding: 60px 24px;
    background: radial-gradient(ellipse 80% 60% at 50% 40%, #1a120a 0%, #0a0a0a 100%);
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      repeating-linear-gradient(0deg, transparent, transparent 59px, rgba(201,149,42,0.04) 60px),
      repeating-linear-gradient(90deg, transparent, transparent 59px, rgba(201,149,42,0.04) 60px);
  }

  .apple-glyph {
    width: 80px;
    height: 80px;
    margin-bottom: 32px;
    opacity: 0.9;
    animation: floatY 4s ease-in-out infinite;
  }

  @keyframes floatY {
    0%,100% { transform: translateY(0); }
    50% { transform: translateY(-10px); }
  }

  .hero-eyebrow {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 20px;
  }

  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(52px, 9vw, 110px);
    font-weight: 700;
    line-height: 0.95;
    letter-spacing: -0.02em;
    color: var(--white);
    margin-bottom: 8px;
  }

  .hero-title em {
    font-style: italic;
    color: var(--gold-light);
  }

  .hero-sub {
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    font-weight: 300;
    color: var(--silver);
    letter-spacing: 0.12em;
    margin-top: 20px;
    text-transform: uppercase;
  }

  .hero-dates {
    font-family: 'DM Mono', monospace;
    font-size: 13px;
    color: var(--gold);
    margin-top: 12px;
    opacity: 0.7;
  }

  .scroll-hint {
    position: absolute;
    bottom: 32px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    opacity: 0.5;
    animation: pulse 2s ease-in-out infinite;
  }

  @keyframes pulse { 0%,100%{opacity:.5} 50%{opacity:.9} }

  .scroll-hint span {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--gold);
  }

  .scroll-arrow {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--gold), transparent);
  }

  /* ── SECTION WRAPPERS ── */
  section {
    max-width: 960px;
    margin: 0 auto;
    padding: 80px 32px;
  }

  .section-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.35em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(to right, var(--gold), transparent);
    opacity: 0.4;
  }

  .section-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(28px, 5vw, 48px);
    font-weight: 700;
    line-height: 1.1;
    margin-bottom: 32px;
    color: var(--white);
  }

  .section-title em { font-style: italic; color: var(--gold-light); }

  /* ── ROADMAP TIMELINE ── */
  .timeline-wrap {
    background: #0f0f0f;
    border-top: 1px solid rgba(201,149,42,0.15);
    border-bottom: 1px solid rgba(201,149,42,0.15);
    padding: 0;
  }

  .timeline {
    position: relative;
    max-width: 960px;
    margin: 0 auto;
    padding: 60px 32px;
  }

  .timeline::before {
    content: '';
    position: absolute;
    left: 50%;
    top: 0;
    bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--gold) 10%, var(--gold) 90%, transparent);
    opacity: 0.3;
    transform: translateX(-50%);
  }

  .era-header {
    text-align: center;
    margin: 60px 0 40px;
    position: relative;
    z-index: 2;
  }

  .era-badge {
    display: inline-block;
    background: var(--gold);
    color: var(--black);
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    font-weight: 500;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    padding: 6px 16px;
    border-radius: 2px;
  }

  .era-title {
    font-family: 'Playfair Display', serif;
    font-size: 22px;
    color: var(--white);
    margin-top: 12px;
    opacity: 0.9;
  }

  .t-node {
    display: flex;
    align-items: flex-start;
    margin-bottom: 48px;
    position: relative;
  }

  .t-node.left { flex-direction: row; }
  .t-node.right { flex-direction: row-reverse; }

  .t-content {
    width: calc(50% - 48px);
    flex-shrink: 0;
  }

  .t-node.left .t-content { text-align: right; padding-right: 32px; }
  .t-node.right .t-content { text-align: left; padding-left: 32px; }

  .t-year {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--gold);
    letter-spacing: 0.15em;
    margin-bottom: 6px;
  }

  .t-event-title {
    font-family: 'Playfair Display', serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--white);
    line-height: 1.2;
    margin-bottom: 8px;
  }

  .t-event-desc {
    font-size: 13px;
    color: rgba(245,240,232,0.6);
    line-height: 1.7;
  }

  .t-dot {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    width: 14px;
    height: 14px;
    border-radius: 50%;
    background: var(--black);
    border: 2px solid var(--gold);
    z-index: 3;
    flex-shrink: 0;
    top: 4px;
    transition: all 0.3s;
  }

  .t-dot.big {
    width: 20px;
    height: 20px;
    background: var(--gold);
    box-shadow: 0 0 20px rgba(201,149,42,0.4);
  }

  .t-spacer { width: calc(50% - 48px); flex-shrink: 0; }

  /* ── INDIA / SPIRITUALITY ── */
  .india-wrap {
    background: linear-gradient(135deg, #0a0f0a 0%, #0d1a0d 50%, #0a0a0a 100%);
    border-top: 1px solid rgba(74,103,65,0.3);
    border-bottom: 1px solid rgba(74,103,65,0.3);
  }

  .india-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 32px;
    margin-top: 40px;
  }

  .india-card {
    background: rgba(74,103,65,0.08);
    border: 1px solid rgba(74,103,65,0.25);
    border-radius: 4px;
    padding: 28px;
    position: relative;
    overflow: hidden;
  }

  .india-card::before {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px;
    height: 100%;
    background: var(--sage-light);
    opacity: 0.6;
  }

  .india-card-icon {
    font-size: 28px;
    margin-bottom: 16px;
    display: block;
  }

  .india-card-title {
    font-family: 'Playfair Display', serif;
    font-size: 16px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 10px;
  }

  .india-card-text {
    font-size: 13px;
    color: rgba(245,240,232,0.6);
    line-height: 1.75;
  }

  .india-quote {
    margin-top: 40px;
    border-left: 3px solid var(--sage-light);
    padding: 20px 28px;
    background: rgba(74,103,65,0.06);
    border-radius: 0 4px 4px 0;
  }

  .india-quote p {
    font-family: 'Playfair Display', serif;
    font-size: 17px;
    font-style: italic;
    color: rgba(245,240,232,0.85);
    line-height: 1.75;
    margin-bottom: 10px;
  }

  .india-quote cite {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.15em;
    color: var(--sage-light);
  }

  /* ── BOOK SECTION ── */
  .book-wrap {
    background: #0a0a10;
    border-top: 1px solid rgba(45,90,142,0.2);
    border-bottom: 1px solid rgba(45,90,142,0.2);
  }

  .book-layout {
    display: grid;
    grid-template-columns: 200px 1fr;
    gap: 48px;
    align-items: start;
    margin-top: 40px;
  }

  .book-cover {
    background: linear-gradient(135deg, #1a2f4a, #0d1f35);
    border: 1px solid rgba(45,90,142,0.4);
    border-radius: 3px;
    aspect-ratio: 2/3;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 24px;
    text-align: center;
    position: relative;
    box-shadow: 6px 6px 0 rgba(0,0,0,0.5);
  }

  .book-cover::after {
    content: '';
    position: absolute;
    left: 0; top: 0; bottom: 0;
    width: 12px;
    background: linear-gradient(to right, rgba(45,90,142,0.5), transparent);
  }

  .book-cover-title {
    font-family: 'Playfair Display', serif;
    font-size: 14px;
    font-weight: 700;
    color: var(--white);
    line-height: 1.3;
    margin-bottom: 16px;
  }

  .book-cover-author {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: rgba(255,255,255,0.5);
    letter-spacing: 0.1em;
  }

  .book-cover-om {
    font-size: 40px;
    margin-bottom: 16px;
    opacity: 0.6;
  }

  .book-info-title {
    font-family: 'Playfair Display', serif;
    font-size: 24px;
    color: var(--white);
    margin-bottom: 4px;
  }

  .book-info-author {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: var(--blue-mid);
    letter-spacing: 0.15em;
    margin-bottom: 20px;
  }

  .book-info-text {
    font-size: 14px;
    color: rgba(245,240,232,0.65);
    line-height: 1.8;
    margin-bottom: 16px;
  }

  .book-themes {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 20px;
  }

  .book-tag {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.1em;
    color: var(--blue-mid);
    border: 1px solid rgba(45,90,142,0.4);
    padding: 4px 10px;
    border-radius: 2px;
  }

  /* ── IDEOLOGY SECTION ── */
  .ideology-wrap {
    background: #0a0a0a;
  }

  .ideology-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    margin-top: 40px;
  }

  .ideology-cell {
    background: #111;
    padding: 32px 24px;
    position: relative;
    overflow: hidden;
    transition: background 0.3s;
  }

  .ideology-cell:hover { background: #161616; }

  .ideology-cell::before {
    content: attr(data-num);
    position: absolute;
    top: 16px;
    right: 20px;
    font-family: 'DM Mono', monospace;
    font-size: 48px;
    font-weight: 500;
    color: rgba(201,149,42,0.06);
    line-height: 1;
  }

  .ideology-cell-icon {
    margin-bottom: 16px;
  }

  .ideology-cell-title {
    font-family: 'Playfair Display', serif;
    font-size: 16px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 10px;
    line-height: 1.3;
  }

  .ideology-cell-text {
    font-size: 13px;
    color: rgba(245,240,232,0.55);
    line-height: 1.75;
  }

  .ideology-quote-row {
    background: var(--gold);
    color: var(--black);
    margin-top: 2px;
  }

  .ideology-quote-row p {
    font-family: 'Playfair Display', serif;
    font-size: clamp(15px, 2.5vw, 22px);
    font-style: italic;
    line-height: 1.5;
    font-weight: 700;
  }

  .ideology-quote-row cite {
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    opacity: 0.7;
    display: block;
    margin-top: 12px;
    font-style: normal;
  }

  /* ── APPLE TRANSFORMATION SVG ── */
  .transform-wrap {
    background: #080808;
    border-top: 1px solid rgba(255,255,255,0.05);
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }

  .product-timeline {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 16px;
    margin-top: 40px;
  }

  .product-card {
    background: #111;
    border: 1px solid rgba(255,255,255,0.07);
    border-radius: 3px;
    padding: 20px 16px;
    text-align: center;
    position: relative;
    transition: border-color 0.3s;
  }

  .product-card:hover { border-color: rgba(201,149,42,0.4); }

  .product-year {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    color: var(--gold);
    letter-spacing: 0.15em;
    margin-bottom: 12px;
  }

  .product-icon {
    font-size: 32px;
    margin-bottom: 12px;
    display: block;
  }

  .product-name {
    font-family: 'Playfair Display', serif;
    font-size: 14px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 8px;
    line-height: 1.2;
  }

  .product-impact {
    font-size: 11px;
    color: rgba(245,240,232,0.5);
    line-height: 1.6;
  }

  .product-arrow {
    display: flex;
    align-items: center;
    justify-content: center;
    color: rgba(201,149,42,0.3);
    font-size: 18px;
    padding-top: 60px;
  }

  /* ── LEGACY ── */
  .legacy-wrap {
    background: linear-gradient(to bottom, #0a0a0a, #0d0a06);
  }

  .legacy-stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    margin: 40px 0;
  }

  .stat-cell {
    background: #111;
    padding: 28px 20px;
    text-align: center;
  }

  .stat-num {
    font-family: 'Playfair Display', serif;
    font-size: 36px;
    font-weight: 700;
    color: var(--gold-light);
    line-height: 1;
    margin-bottom: 8px;
  }

  .stat-label {
    font-family: 'DM Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.15em;
    color: var(--silver);
    text-transform: uppercase;
  }

  .legacy-closing {
    text-align: center;
    padding: 60px 32px;
    border-top: 1px solid rgba(201,149,42,0.1);
  }

  .legacy-closing blockquote {
    font-family: 'Playfair Display', serif;
    font-size: clamp(18px, 3vw, 28px);
    font-style: italic;
    color: rgba(245,240,232,0.9);
    line-height: 1.6;
    max-width: 700px;
    margin: 0 auto 20px;
  }

  .legacy-closing cite {
    font-family: 'DM Mono', monospace;
    font-size: 12px;
    letter-spacing: 0.15em;
    color: var(--gold);
  }

  /* ── DIVIDER ── */
  .divider {
    width: 60px;
    height: 1px;
    background: var(--gold);
    margin: 0 auto;
    opacity: 0.4;
  }

  /* ── FOOTER ── */
  footer {
    text-align: center;
    padding: 40px 24px;
    border-top: 1px solid rgba(255,255,255,0.05);
    font-family: 'DM Mono', monospace;
    font-size: 11px;
    color: rgba(255,255,255,0.2);
    letter-spacing: 0.1em;
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 680px) {
    .india-grid { grid-template-columns: 1fr; }
    .ideology-grid { grid-template-columns: 1fr; }
    .product-timeline { grid-template-columns: repeat(2, 1fr); }
    .legacy-stats { grid-template-columns: repeat(2, 1fr); }
    .book-layout { grid-template-columns: 1fr; }
    .timeline::before { left: 20px; }
    .t-node { flex-direction: column; }
    .t-node.right { flex-direction: column; }
    .t-content { width: 100%; text-align: left !important; padding-left: 44px !important; padding-right: 0 !important; }
    .t-dot { left: 20px; }
    .t-spacer { display: none; }
  }

  /* ── ENTRANCE ANIMATIONS ── */
  .fade-in {
    opacity: 0;
    transform: translateY(24px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }
  .fade-in.visible { opacity: 1; transform: translateY(0); }
</style>
</head>
<body>

<!-- ════════════════ HERO ════════════════ -->
<div class="hero">
  <svg class="apple-glyph" viewBox="0 0 80 80" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path d="M52 14c1.5-3.8 1.2-9.5-2.5-12C46 5.2 40.5 8.5 38 12c-2.3 3.2-2.2 8.2.5 10.8 2.8-0.2 8.8-3.6 13.5-8.8z" fill="#c9952a" opacity="0.9"/>
    <path d="M14 34c-8 9.5-8 26 2 36 4 4.5 8 7 12 7 4.5 0 6.5-2.5 12-2.5s7.5 2.5 12 2.5c4 0 8-2.5 12-7 3-4 5-8.5 6-13.5-4.5-2-8-7-8-12.5 0-5 2.8-9.5 7-12-3-4-8-7-14-7-5 0-9 2.5-12 2.5-3 0-7-2.5-11-2.5-3 0-12 2.5-18 9z" fill="#c9952a" opacity="0.85"/>
  </svg>
  <div class="hero-eyebrow">The Full Story</div>
  <h1 class="hero-title">Steve<br><em>Jobs</em></h1>
  <div class="hero-sub">Vision · India · Zen · Apple · Legacy</div>
  <div class="hero-dates">February 24, 1955 — October 5, 2011</div>
  <div class="scroll-hint">
    <span>Scroll</span>
    <div class="scroll-arrow"></div>
  </div>
</div>

<!-- ════════════════ ROADMAP TIMELINE ════════════════ -->
<div class="timeline-wrap">
  <div class="timeline">
    <div class="era-header fade-in">
      <div class="era-badge">Chapter 1</div>
      <div class="era-title">The Origins</div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1955</div>
        <div class="t-event-title">Born in San Francisco</div>
        <div class="t-event-desc">Given up for adoption at birth, raised by Paul and Clara Jobs in Mountain View, California — the future epicentre of Silicon Valley.</div>
      </div>
      <div class="t-dot big"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot"></div>
      <div class="t-content">
        <div class="t-year">1969</div>
        <div class="t-event-title">Meets Steve Wozniak</div>
        <div class="t-event-desc">A neighbour introduces 14-year-old Jobs to 19-year-old Wozniak. A friendship and creative partnership that changes history begins in a garage.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1972</div>
        <div class="t-event-title">Reed College — Drops Out</div>
        <div class="t-event-desc">Enrolls at Reed College in Portland, then drops out after 6 months — but stays 18 months, sleeping on dorm floors and auditing a calligraphy class that later shaped Mac typography.</div>
      </div>
      <div class="t-dot"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot"></div>
      <div class="t-content">
        <div class="t-year">1974</div>
        <div class="t-event-title">Atari — First Tech Job</div>
        <div class="t-event-desc">Gets hired as a technician at Atari. Works nights to avoid bothering colleagues. Saves money for his pivotal journey to India.</div>
      </div>
    </div>

    <!-- ── ERA 2 ── -->
    <div class="era-header fade-in" style="margin-top:80px">
      <div class="era-badge">Chapter 2</div>
      <div class="era-title">The India Awakening — 1974</div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1974 — Spring</div>
        <div class="t-event-title">Journeys to India</div>
        <div class="t-event-desc">Travels to India with his Reed friend Daniel Kottke seeking spiritual enlightenment under Neem Karoli Baba (Maharaj-ji), the guru also revered by Ram Dass.</div>
      </div>
      <div class="t-dot big" style="background: #4a6741; border-color: #6a8f61;"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot" style="border-color: #6a8f61;"></div>
      <div class="t-content">
        <div class="t-year">1974 — Summer</div>
        <div class="t-event-title">7 Months of Wandering</div>
        <div class="t-event-desc">Treks through rural Himachal Pradesh, Uttarakhand, and the Kumbh Mela. Shaves his head. Lives in ashrams. Reads Paramahansa Yogananda's autobiography obsessively.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1974 — Autumn</div>
        <div class="t-event-title">Zen Buddhism Takes Root</div>
        <div class="t-event-desc">Returns from India profoundly changed. Later studies Zen with Shunryu Suzuki's disciple Kobun Chino Otogawa — Zen principles of simplicity, intuition, and the "beginner's mind" become his design philosophy.</div>
      </div>
      <div class="t-dot" style="border-color: #6a8f61;"></div>
      <div class="t-spacer"></div>
    </div>

    <!-- ── ERA 3 ── -->
    <div class="era-header fade-in" style="margin-top:80px">
      <div class="era-badge">Chapter 3</div>
      <div class="era-title">Building Apple</div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot big"></div>
      <div class="t-content">
        <div class="t-year">1976</div>
        <div class="t-event-title">Apple Computer Founded</div>
        <div class="t-event-desc">Jobs, Wozniak, and Ronald Wayne found Apple Computer on April 1. The Apple I sells for $666.66. Jobs insists it be sold as a finished computer, not a kit.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1977</div>
        <div class="t-event-title">Apple II — Mass Market</div>
        <div class="t-event-desc">The Apple II launches with color graphics and an open architecture. It sells millions and generates $139 million in revenue by 1980, making Apple the fastest-growing company in US history.</div>
      </div>
      <div class="t-dot"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot big"></div>
      <div class="t-content">
        <div class="t-year">1984</div>
        <div class="t-event-title">Macintosh — "1984" Ad</div>
        <div class="t-event-desc">The Mac introduces the GUI mouse-driven computer to the world. The iconic Ridley Scott Super Bowl ad runs once and becomes the most celebrated ad of the century.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1985</div>
        <div class="t-event-title">Ousted from Apple</div>
        <div class="t-event-desc">A boardroom coup led by CEO John Sculley (whom Jobs himself recruited) forces him out. A dark period — but Jobs calls it "the best thing that ever happened to me."</div>
      </div>
      <div class="t-dot" style="border-color: #8b3a1a;"></div>
      <div class="t-spacer"></div>
    </div>

    <!-- ── ERA 4 ── -->
    <div class="era-header fade-in" style="margin-top:80px">
      <div class="era-badge">Chapter 4</div>
      <div class="era-title">The Wilderness Years</div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot"></div>
      <div class="t-content">
        <div class="t-year">1985</div>
        <div class="t-event-title">NeXT Computer Founded</div>
        <div class="t-event-desc">Founds NeXT with $7 million of his own money to build workstations for higher education. The hardware fails commercially but the NeXTSTEP OS becomes transformative.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1986</div>
        <div class="t-event-title">Buys Pixar — $5 Million</div>
        <div class="t-event-desc">Acquires Lucasfilm's computer graphics division for $5 million. Loses $50 million over a decade before Toy Story (1995) changes everything, making Pixar the most successful animation studio in history.</div>
      </div>
      <div class="t-dot"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot big"></div>
      <div class="t-content">
        <div class="t-year">1995</div>
        <div class="t-event-title">Toy Story — Pixar IPO</div>
        <div class="t-event-desc">Toy Story grosses $373 million worldwide. Pixar's IPO makes Jobs a billionaire and the world's most valuable media company founder — two years before his Apple return.</div>
      </div>
    </div>

    <!-- ── ERA 5 ── -->
    <div class="era-header fade-in" style="margin-top:80px">
      <div class="era-badge">Chapter 5</div>
      <div class="era-title">The Second Coming</div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">1997</div>
        <div class="t-event-title">Apple Acquires NeXT</div>
        <div class="t-event-desc">Apple buys NeXT for $429 million, bringing Jobs back as an advisor. Within weeks he's interim CEO, inheriting a company 90 days from bankruptcy with a $1 billion annual loss.</div>
      </div>
      <div class="t-dot big"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot"></div>
      <div class="t-content">
        <div class="t-year">1998</div>
        <div class="t-event-title">iMac — "Think Different"</div>
        <div class="t-event-desc">The colorful, Jony Ive-designed iMac saves Apple. The "Think Different" campaign — celebrating Einstein, Gandhi, Picasso — repositions Apple as a cultural icon, not a computer company.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">2001</div>
        <div class="t-event-title">iPod + iTunes</div>
        <div class="t-event-desc">"1,000 songs in your pocket." Transforms the music industry. The iTunes Store sells 70 million songs in its first year, displacing Napster and the CD era simultaneously.</div>
      </div>
      <div class="t-dot big"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot big"></div>
      <div class="t-content">
        <div class="t-year">2007</div>
        <div class="t-event-title">iPhone — Reinvents the Phone</div>
        <div class="t-event-desc">"An iPod, a phone, and an internet communicator… are you getting it?" The world's most successful consumer product ever. 2.3 billion units sold across all models by 2023.</div>
      </div>
    </div>

    <div class="t-node left fade-in">
      <div class="t-content">
        <div class="t-year">2010</div>
        <div class="t-event-title">iPad — Invents a Category</div>
        <div class="t-event-desc">Creates the modern tablet market, selling 3 million units in 80 days. Later, becomes the primary computing device for 500 million people worldwide.</div>
      </div>
      <div class="t-dot"></div>
      <div class="t-spacer"></div>
    </div>

    <div class="t-node right fade-in">
      <div class="t-spacer"></div>
      <div class="t-dot big" style="background: #4a6741;"></div>
      <div class="t-content">
        <div class="t-year">October 5, 2011</div>
        <div class="t-event-title">"Oh wow. Oh wow. Oh wow."</div>
        <div class="t-event-desc">Steve Jobs dies at age 56 from pancreatic neuroendocrine tumor, surrounded by family. His reported last words. Apple's stock halts. World leaders mourn. A generation weeps for a man they never met.</div>
      </div>
    </div>

  </div>
</div>

<!-- ════════════════ PRODUCT TRANSFORMATIONS ════════════════ -->
<div class="transform-wrap">
  <section>
    <div class="section-label fade-in">Apple's Transformation of Technology</div>
    <h2 class="section-title fade-in">He didn't just make <em>products.</em><br>He made new worlds.</h2>
    <div class="product-timeline">
      <div class="product-card fade-in">
        <div class="product-year">1977</div>
        <span class="product-icon">🖥</span>
        <div class="product-name">Apple II</div>
        <div class="product-impact">First mass-market personal computer. Put computing in homes, not just labs.</div>
      </div>
      <div class="product-card fade-in">
        <div class="product-year">1984</div>
        <span class="product-icon">🖱</span>
        <div class="product-name">Macintosh</div>
        <div class="product-impact">GUI, mouse, and desktop metaphor for everyone — not just engineers.</div>
      </div>
      <div class="product-card fade-in">
        <div class="product-year">2001</div>
        <span class="product-icon">🎵</span>
        <div class="product-name">iPod + iTunes</div>
        <div class="product-impact">Killed the music album. Invented the digital media economy.</div>
      </div>
      <div class="product-card fade-in">
        <div class="product-year">2007</div>
        <span class="product-icon">📱</span>
        <div class="product-name">iPhone</div>
        <div class="product-impact">Collapsed camera, map, music player, internet into one glass slab.</div>
      </div>
      <div class="product-card fade-in">
        <div class="product-year">2010</div>
        <span class="product-icon">📲</span>
        <div class="product-name">iPad</div>
        <div class="product-impact">Created the tablet market. Changed how children, doctors, pilots, artists work.</div>
      </div>
    </div>
  </section>
</div>

<!-- ════════════════ INDIA & SPIRITUALITY ════════════════ -->
<div class="india-wrap">
  <section>
    <div class="section-label fade-in">India — Spirituality — Zen</div>
    <h2 class="section-title fade-in">The journey that <em>rewired</em><br>everything he made.</h2>

    <div class="india-grid">
      <div class="india-card fade-in">
        <span class="india-card-icon">🇮🇳</span>
        <div class="india-card-title">7 Months in India (1974)</div>
        <div class="india-card-text">At 19, Jobs spent 7 months in India searching for Neem Karoli Baba. The guru had died by the time he arrived. Instead he wandered ashrams in Rishikesh, Haridwar, and the Kumbh Mela — observing, meditating, fasting. He contracted severe dysentery but was transformed. He returned with a shaved head and a new way of seeing.</div>
      </div>
      <div class="india-card fade-in">
        <span class="india-card-icon">☸️</span>
        <div class="india-card-title">Zen Buddhism</div>
        <div class="india-card-text">After India, Jobs became a serious Zen practitioner under Kobun Chino Otogawa at the Haiku Zendo. Zen gave him: the principle of emptiness as elegance, the discipline of removing everything unnecessary, the idea that the journey and product are one. He nearly became a monk — Kobun encouraged him to build Apple instead.</div>
      </div>
      <div class="india-card fade-in">
        <span class="india-card-icon">🧘</span>
        <div class="india-card-title">Intuition Over Data</div>
        <div class="india-card-text">India taught Jobs to trust intuition above rational analysis. "The people in the Indian countryside don't use their intellect like we do," he said. "They use their intuition instead, and their intuition is far more developed." This became Apple's design philosophy — feel before function, beauty before spec sheets.</div>
      </div>
      <div class="india-card fade-in">
        <span class="india-card-icon">⬜</span>
        <div class="india-card-title">Zen Aesthetics in Design</div>
        <div class="india-card-text">Zen's ma (negative space), wabi-sabi (beauty in imperfection), and shoshin (beginner's mind) directly shaped Apple's design language. White space wasn't waste — it was message. The first iPhone had no physical keyboard: a Zen-like act of subtraction. "Deciding what not to build is as important as deciding what to build."</div>
      </div>
    </div>

    <div class="india-quote fade-in">
      <p>"If you just sit and observe, you will see how restless your mind is. If you try to calm it, it only makes it worse, but over time it does calm, and when it does, there's room to hear more subtle things — that's when your intuition starts to blossom."</p>
      <cite>— Steve Jobs, as told to Walter Isaacson</cite>
    </div>
  </section>
</div>

<!-- ════════════════ FAVOURITE BOOK ════════════════ -->
<div class="book-wrap">
  <section>
    <div class="section-label fade-in">The Book He Carried for Life</div>
    <h2 class="section-title fade-in">His most beloved <em>text.</em></h2>

    <div class="book-layout fade-in">
      <div class="book-cover">
        <div class="book-cover-om">☸</div>
        <div class="book-cover-title">Autobiography of a Yogi</div>
        <div style="height: 1px; background: rgba(45,90,142,0.4); width: 60%; margin: 12px auto;"></div>
        <div class="book-cover-author">Paramahansa Yogananda</div>
        <div style="margin-top: 16px; font-family: 'DM Mono', monospace; font-size: 9px; color: rgba(255,255,255,0.3); letter-spacing: 0.1em;">1946</div>
      </div>
      <div>
        <div class="book-info-title">Autobiography of a Yogi</div>
        <div class="book-info-author">By Paramahansa Yogananda · 1946</div>
        <div class="book-info-text">Jobs first read this book as a teenager. He re-read it every year of his adult life. When he died in 2011, it was the only book on his iPad — downloaded to be given to all 500 guests at his memorial service at Stanford Memorial Church.</div>
        <div class="book-info-text">The book describes a path of spiritual self-mastery, the science of Kriya Yoga, and the idea that consciousness itself is the fundamental substance of the universe — not matter. For Jobs, this resonated with his belief that technology was a tool for expanding human consciousness.</div>
        <div class="book-info-text">Yogananda's central argument — that the rational and spiritual are not opposites but complementary — became Jobs's personal creed. It's why he called Apple products "tools for the mind."</div>
        <div class="book-themes">
          <span class="book-tag">Consciousness</span>
          <span class="book-tag">Intuition</span>
          <span class="book-tag">Self-mastery</span>
          <span class="book-tag">East + West</span>
          <span class="book-tag">Reality as illusion</span>
          <span class="book-tag">Kriya Yoga</span>
        </div>
      </div>
    </div>

    <div style="margin-top: 40px; background: rgba(45,90,142,0.08); border: 1px solid rgba(45,90,142,0.2); border-radius: 3px; padding: 28px; border-left: 3px solid #2d5a8e;" class="fade-in">
      <div style="font-family: 'Playfair Display', serif; font-size: 17px; font-style: italic; color: rgba(245,240,232,0.85); line-height: 1.75; margin-bottom: 10px;">"The juice goes out of Christianity when it becomes too based on faith rather than on living the example or finding the essence of the things Jesus, Buddha, and Yogananda all taught."</div>
      <div style="font-family: 'DM Mono', monospace; font-size: 11px; letter-spacing: 0.15em; color: #2d5a8e;">— Steve Jobs, Walter Isaacson biography</div>
    </div>
  </section>
</div>

<!-- ════════════════ IDEOLOGY ════════════════ -->
<div class="ideology-wrap">
  <section>
    <div class="section-label fade-in">The Jobs Doctrine</div>
    <h2 class="section-title fade-in">A philosophy built at the<br><em>intersection of art and technology.</em></h2>
  </section>

  <div class="ideology-grid">
    <div class="ideology-cell fade-in" data-num="01">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <circle cx="12" cy="12" r="10"/><path d="M12 8v4l3 3"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Simplicity is the Ultimate Sophistication</div>
      <div class="ideology-cell-text">Jobs inherited this from Leonardo da Vinci. Products should be so simple a child can use them. Every unnecessary element is a failure. The first Mac manual famously started with the words "Do not be afraid."</div>
    </div>
    <div class="ideology-cell fade-in" data-num="02">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <path d="M12 2L2 7l10 5 10-5-10-5M2 17l10 5 10-5M2 12l10 5 10-5"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Craft the Back of the Fence</div>
      <div class="ideology-cell-text">His father Paul Jobs taught him to finish the back of a cabinet even if no one sees it. Every circuit board inside a Mac had to be beautiful. "For you to sleep well at night, the aesthetic, the quality, has to be carried all the way through."</div>
    </div>
    <div class="ideology-cell fade-in" data-num="03">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <path d="M21 16V8a2 2 0 00-1-1.73l-7-4a2 2 0 00-2 0l-7 4A2 2 0 003 8v8a2 2 0 001 1.73l7 4a2 2 0 002 0l7-4A2 2 0 0021 16z"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Integrate Hardware, Software, and Content</div>
      <div class="ideology-cell-text">Jobs saw that the real magic happened at the intersection. Apple controlled chips, OS, apps, and stores — a vertical stack no competitor could replicate. This was heresy in the open-architecture era, and it won.</div>
    </div>
    <div class="ideology-cell fade-in" data-num="04">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <path d="M1 12s4-8 11-8 11 8 11 8-4 8-11 8-11-8-11-8z"/><circle cx="12" cy="12" r="3"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Focus on the User, Not the Customer</div>
      <div class="ideology-cell-text">Jobs famously said customers don't know what they want until you show them. He ignored focus groups. He shipped what he believed would change lives, then watched the world catch up. "It's really hard to design products by focus groups."</div>
    </div>
    <div class="ideology-cell fade-in" data-num="05">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <circle cx="12" cy="12" r="3"/><path d="M12 1v4M12 19v4M4.22 4.22l2.83 2.83M16.95 16.95l2.83 2.83M1 12h4M19 12h4M4.22 19.78l2.83-2.83M16.95 7.05l2.83-2.83"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Stay at the Intersection of Art and Science</div>
      <div class="ideology-cell-text">The liberal arts, humanities, and the sciences were never opposites to Jobs. Great products, like great art, require technical mastery and emotional depth simultaneously. Apple's DNA carries both.</div>
    </div>
    <div class="ideology-cell fade-in" data-num="06">
      <div class="ideology-cell-icon">
        <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="#c9952a" stroke-width="1.5" stroke-linecap="round">
          <path d="M22 11.08V12a10 10 0 11-5.93-9.14"/><polyline points="22 4 12 14.01 9 11.01"/>
        </svg>
      </div>
      <div class="ideology-cell-title">Reality Distortion Field</div>
      <div class="ideology-cell-text">Jobs's engineers coined this phrase for his ability to convince himself and others that the impossible was achievable. It was partly inspiration, partly manipulation — and it repeatedly broke through what experts said couldn't be done.</div>
    </div>
  </div>

  <div class="ideology-quote-row ideology-cell fade-in" style="padding: 40px 48px;">
    <p>"Your time is limited, so don't waste it living someone else's life. Don't be trapped by dogma — which is living with the results of other people's thinking. Have the courage to follow your heart and intuition."</p>
    <cite>— Stanford Commencement Address, June 12, 2005</cite>
  </div>
</div>

<!-- ════════════════ LEGACY ════════════════ -->
<div class="legacy-wrap">
  <section>
    <div class="section-label fade-in">The Numbers Behind the Legacy</div>
    <div class="legacy-stats">
      <div class="stat-cell fade-in">
        <div class="stat-num">$3.5T</div>
        <div class="stat-label">Apple market cap peak</div>
      </div>
      <div class="stat-cell fade-in">
        <div class="stat-num">2.3B</div>
        <div class="stat-label">iPhones sold (all models)</div>
      </div>
      <div class="stat-cell fade-in">
        <div class="stat-num">27</div>
        <div class="stat-label">Granted patents per week (avg)</div>
      </div>
      <div class="stat-cell fade-in">
        <div class="stat-num">$5M</div>
        <div class="stat-label">Pixar → $7.4B at Disney sale</div>
      </div>
    </div>

    <div class="divider"></div>
  </section>

  <div class="legacy-closing fade-in">
    <blockquote>"Here's to the crazy ones. The misfits. The rebels. The troublemakers. The round pegs in the square holes. The ones who see things differently…"</blockquote>
    <cite>— Think Different, Apple, 1997</cite>
  </div>
</div>

<footer>
  Steve Jobs Visual Journey · 1955–2011 · Created as a visual graphic reference
</footer>

<script>
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        obs.unobserve(e.target);
      }
    });
  }, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });

  document.querySelectorAll('.fade-in').forEach((el, i) => {
    el.style.transitionDelay = (i % 4) * 80 + 'ms';
    obs.observe(el);
  });
</script>
</body>
</html>

```
<img width="1355" height="617" alt="image" src="https://github.com/user-attachments/assets/57c0c4ec-70cc-4be2-b879-0679f5577e97" />
<img width="1353" height="617" alt="image" src="https://github.com/user-attachments/assets/128c0524-b771-4d15-9871-fdfd166a28c6" />
<img width="1352" height="614" alt="image" src="https://github.com/user-attachments/assets/a7402d16-efee-4493-8f43-ea9f46c9a849" />
<img width="1349" height="614" alt="image" src="https://github.com/user-attachments/assets/469dfac8-447c-4d5f-90d0-08b59f12c385" />
<img width="1355" height="616" alt="image" src="https://github.com/user-attachments/assets/b79a271d-5501-42c8-865c-a23042405399" />
<img width="1350" height="619" alt="image" src="https://github.com/user-attachments/assets/af63485b-4acc-4ed4-b37c-421695916708" />
<img width="1349" height="617" alt="image" src="https://github.com/user-attachments/assets/fc083834-9efc-4577-b711-0e1552daa657" />
<img width="1352" height="619" alt="image" src="https://github.com/user-attachments/assets/9efb10d5-c57a-41fd-812f-a1df70fb05a9" />
<img width="1348" height="617" alt="image" src="https://github.com/user-attachments/assets/aaa0e76e-560d-4bf4-91c6-26fd20c3e846" />
<img width="1354" height="614" alt="image" src="https://github.com/user-attachments/assets/2aaac962-ea53-43b6-9dde-57bdc6776837" />
<img width="1353" height="615" alt="image" src="https://github.com/user-attachments/assets/f021db4e-f9d6-4da7-bc7a-d6bd2a70ebdb" />
<img width="1353" height="612" alt="image" src="https://github.com/user-attachments/assets/ac913555-a291-48a6-9569-544c9dbc81cd" />
<img width="1350" height="615" alt="image" src="https://github.com/user-attachments/assets/2b13d035-5564-4198-92fa-af939d5e72ee" />
<img width="1349" height="615" alt="image" src="https://github.com/user-attachments/assets/9bc79d24-6abb-40f9-8747-8f476dae4e8c" />
<img width="1353" height="616" alt="image" src="https://github.com/user-attachments/assets/3f374efe-dc07-4f58-8047-6d25e9fda156" />







