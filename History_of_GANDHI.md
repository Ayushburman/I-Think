```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mohandas Karamchand Gandhi — The Complete Chronicle</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400;1,700&family=IBM+Plex+Mono:wght@400;500&family=Source+Serif+4:ital,opsz,wght@0,8..60,300;0,8..60,400;1,8..60,300&display=swap" rel="stylesheet"/>
<style>
:root {
  --bg: #0d0c08;
  --bg2: #131208;
  --bg3: #1a1810;
  --surface: #1e1c13;
  --surface2: #252318;
  --gold: #c9922a;
  --gold-dim: #8a6218;
  --gold-bright: #e8b44a;
  --cream: #e8e0cc;
  --cream-dim: #a89c82;
  --cream-muted: #6e6352;
  --red: #c23a2b;
  --red-dim: #7a2419;
  --blue: #3a7ab5;
  --blue-dim: #24517a;
  --green: #4a8c5c;
  --green-dim: #2e5c3a;
  --orange: #c4632a;
  --purple: #7a4b9c;
  --mono: 'IBM Plex Mono', monospace;
  --serif: 'Playfair Display', Georgia, serif;
  --body: 'Source Serif 4', Georgia, serif;
  --timeline-w: 3px;
}

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--cream);
  font-family: var(--body);
  font-size: 15px;
  line-height: 1.7;
  min-height: 100vh;
}

/* ─── NOISE TEXTURE overlay ─── */
body::before {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events: none;
  z-index: 0;
  opacity: 0.6;
}

/* ─── HEADER ─── */
header {
  position: relative;
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: center;
  padding: 6rem 2rem 4rem;
  overflow: hidden;
}

header::before {
  content: '';
  position: absolute;
  inset: 0;
  background: radial-gradient(ellipse 70% 60% at 50% 40%, #2a1e0a 0%, transparent 70%),
              radial-gradient(ellipse 40% 30% at 50% 60%, #1a100400 0%, transparent 60%);
  z-index: 0;
}

.header-ornament {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 6px;
  color: var(--gold-dim);
  text-transform: uppercase;
  margin-bottom: 2rem;
  position: relative;
  z-index: 1;
}

.header-ornament::before,
.header-ornament::after {
  content: '——';
  margin: 0 1rem;
  opacity: 0.5;
}

header h1 {
  font-family: var(--serif);
  font-size: clamp(2.8rem, 7vw, 5.5rem);
  font-weight: 900;
  color: var(--cream);
  line-height: 1.1;
  position: relative;
  z-index: 1;
  letter-spacing: -0.02em;
}

header h1 em {
  font-style: italic;
  color: var(--gold);
}

.header-dates {
  font-family: var(--mono);
  font-size: 13px;
  color: var(--gold-dim);
  letter-spacing: 4px;
  margin: 1.5rem 0;
  position: relative;
  z-index: 1;
}

.header-sub {
  font-family: var(--body);
  font-style: italic;
  font-size: 1.15rem;
  color: var(--cream-dim);
  max-width: 560px;
  line-height: 1.6;
  position: relative;
  z-index: 1;
}

.spinning-wheel {
  position: relative;
  z-index: 1;
  margin: 3rem auto 0;
  width: 80px;
  height: 80px;
  opacity: 0.5;
}

.spinning-wheel svg {
  animation: spin 20s linear infinite;
  width: 100%;
  height: 100%;
}

@keyframes spin { to { transform: rotate(360deg); } }

/* ─── LEGEND / FILTER ─── */
.legend-section {
  position: sticky;
  top: 0;
  z-index: 100;
  background: rgba(13, 12, 8, 0.92);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(201, 146, 42, 0.15);
  padding: 1rem 2rem;
}

.legend-inner {
  max-width: 900px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem 1rem;
}

.legend-label {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 3px;
  color: var(--cream-muted);
  text-transform: uppercase;
  margin-right: 0.5rem;
}

.filter-btn {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 1.5px;
  text-transform: uppercase;
  border: 1px solid;
  border-radius: 2px;
  padding: 4px 12px;
  background: transparent;
  cursor: pointer;
  transition: all 0.2s;
}

.filter-btn:hover, .filter-btn.active {
  color: var(--bg);
}

.filter-btn[data-type="all"]    { color: var(--cream); border-color: var(--cream-muted); }
.filter-btn[data-type="all"].active, .filter-btn[data-type="all"]:hover { background: var(--cream); }

.filter-btn[data-type="action"]  { color: var(--green); border-color: var(--green-dim); }
.filter-btn[data-type="action"].active, .filter-btn[data-type="action"]:hover { background: var(--green); }

.filter-btn[data-type="personal"] { color: var(--blue); border-color: var(--blue-dim); }
.filter-btn[data-type="personal"].active, .filter-btn[data-type="personal"]:hover { background: var(--blue); }

.filter-btn[data-type="controversy"] { color: var(--red); border-color: var(--red-dim); }
.filter-btn[data-type="controversy"].active, .filter-btn[data-type="controversy"]:hover { background: var(--red); }

.filter-btn[data-type="achievement"] { color: var(--gold); border-color: var(--gold-dim); }
.filter-btn[data-type="achievement"].active, .filter-btn[data-type="achievement"]:hover { background: var(--gold); }

/* ─── TIMELINE LAYOUT ─── */
.timeline-container {
  max-width: 900px;
  margin: 0 auto;
  padding: 4rem 2rem 8rem;
  position: relative;
}

.timeline-spine {
  position: absolute;
  left: 50%;
  top: 0;
  bottom: 0;
  width: var(--timeline-w);
  background: linear-gradient(to bottom,
    transparent 0%,
    var(--gold-dim) 5%,
    var(--gold-dim) 95%,
    transparent 100%);
  transform: translateX(-50%);
}

/* ─── ERA DIVIDERS ─── */
.era {
  position: relative;
  text-align: center;
  margin: 3rem 0 2rem;
  z-index: 5;
}

.era-label {
  display: inline-block;
  background: var(--bg);
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 4px;
  color: var(--gold);
  text-transform: uppercase;
  padding: 6px 20px;
  border: 1px solid var(--gold-dim);
  position: relative;
}

.era-label::before,
.era-label::after {
  content: '';
  position: absolute;
  top: 50%;
  width: 100px;
  height: 1px;
  background: var(--gold-dim);
  opacity: 0.4;
}
.era-label::before { right: 100%; }
.era-label::after  { left: 100%; }

/* ─── TIMELINE ENTRIES ─── */
.entry {
  display: flex;
  align-items: flex-start;
  margin-bottom: 2.5rem;
  position: relative;
  transition: opacity 0.3s;
}

.entry.hidden { opacity: 0.08; pointer-events: none; }

.entry.left  { flex-direction: row-reverse; }
.entry.right { flex-direction: row; }

/* Year pillar */
.year-pillar {
  flex: 0 0 calc(50% - 28px);
  text-align: right;
  padding-right: 2rem;
  padding-top: 1.2rem;
}

.entry.right .year-pillar {
  text-align: left;
  padding-right: 0;
  padding-left: 2rem;
  order: 2;
}

.year-num {
  font-family: var(--serif);
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--gold);
  line-height: 1;
  opacity: 0.3;
}

.year-loc {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 2px;
  color: var(--cream-muted);
  text-transform: uppercase;
  margin-top: 4px;
}

/* Node dot */
.node-dot {
  flex: 0 0 56px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding-top: 1.2rem;
  position: relative;
  z-index: 2;
}

.dot-ring {
  width: 14px;
  height: 14px;
  border-radius: 50%;
  border: 2px solid;
  background: var(--bg);
  position: relative;
  transition: transform 0.2s;
}

.entry:hover .dot-ring { transform: scale(1.4); }

.entry[data-type="action"]       .dot-ring { border-color: var(--green);   }
.entry[data-type="personal"]     .dot-ring { border-color: var(--blue);    }
.entry[data-type="controversy"]  .dot-ring { border-color: var(--red);     }
.entry[data-type="achievement"]  .dot-ring { border-color: var(--gold);    background: var(--gold-dim); }

/* Card */
.card-area {
  flex: 0 0 calc(50% - 28px);
  padding-bottom: 0.5rem;
}

.entry.right .card-area { order: 3; }

.card {
  background: var(--surface);
  border: 1px solid rgba(201, 146, 42, 0.1);
  border-radius: 3px;
  padding: 1.1rem 1.3rem;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  transition: border-color 0.2s, background 0.2s;
}

.card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 3px;
  height: 100%;
}

.entry[data-type="action"]       .card::before { background: var(--green);   }
.entry[data-type="personal"]     .card::before { background: var(--blue);    }
.entry[data-type="controversy"]  .card::before { background: var(--red);     }
.entry[data-type="achievement"]  .card::before { background: var(--gold);    }

.card:hover {
  background: var(--surface2);
  border-color: rgba(201, 146, 42, 0.25);
}

.card-tag {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
  display: inline-block;
}

.entry[data-type="action"]       .card-tag { color: var(--green); }
.entry[data-type="personal"]     .card-tag { color: var(--blue); }
.entry[data-type="controversy"]  .card-tag { color: var(--red); }
.entry[data-type="achievement"]  .card-tag { color: var(--gold); }

.card h3 {
  font-family: var(--serif);
  font-size: 1.05rem;
  font-weight: 700;
  color: var(--cream);
  margin-bottom: 0.4rem;
  line-height: 1.3;
}

.card p {
  font-size: 13.5px;
  color: var(--cream-dim);
  line-height: 1.65;
}

.card-expand {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.4s ease, margin-top 0.3s;
}

.card.open .card-expand { max-height: 400px; margin-top: 0.7rem; }

.card-expand p {
  font-size: 13px;
  color: var(--cream-muted);
  border-top: 1px solid rgba(201, 146, 42, 0.08);
  padding-top: 0.7rem;
  font-style: italic;
}

.card-more {
  font-family: var(--mono);
  font-size: 10px;
  color: var(--cream-muted);
  margin-top: 0.6rem;
  letter-spacing: 1px;
  display: flex;
  align-items: center;
  gap: 4px;
  transition: color 0.2s;
}
.card:hover .card-more { color: var(--gold-dim); }
.card-more::after { content: '+'; }
.card.open .card-more::after { content: '−'; }

/* ─── QUOTE PULLOUTS ─── */
.quote-block {
  text-align: center;
  padding: 3rem 2rem;
  margin: 2rem 0;
  position: relative;
}

.quote-block blockquote {
  font-family: var(--serif);
  font-size: 1.4rem;
  font-style: italic;
  color: var(--gold);
  max-width: 600px;
  margin: 0 auto;
  line-height: 1.6;
  position: relative;
}

.quote-block blockquote::before {
  content: '\201C';
  font-size: 5rem;
  line-height: 0;
  position: absolute;
  top: 1rem;
  left: -2rem;
  color: var(--gold-dim);
  opacity: 0.4;
}

.quote-source {
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 3px;
  color: var(--cream-muted);
  text-transform: uppercase;
  margin-top: 1.2rem;
}

/* ─── SECTION STAT CARDS ─── */
.stat-row {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
  gap: 1px;
  background: rgba(201, 146, 42, 0.08);
  border: 1px solid rgba(201, 146, 42, 0.08);
  border-radius: 3px;
  margin: 3rem 0;
  overflow: hidden;
}

.stat-cell {
  background: var(--surface);
  padding: 1.2rem 1.4rem;
  text-align: center;
}

.stat-n {
  font-family: var(--serif);
  font-size: 2.2rem;
  font-weight: 700;
  color: var(--gold);
  line-height: 1;
}

.stat-label {
  font-family: var(--mono);
  font-size: 9px;
  letter-spacing: 2px;
  color: var(--cream-muted);
  text-transform: uppercase;
  margin-top: 0.4rem;
}

/* ─── SECTION HEADINGS ─── */
.section-heading {
  text-align: center;
  margin: 5rem 0 0;
  position: relative;
  z-index: 5;
}

.section-heading h2 {
  font-family: var(--serif);
  font-size: 1.8rem;
  font-weight: 700;
  color: var(--cream);
  display: inline-block;
  background: var(--bg);
  padding: 0 1.5rem;
}

/* ─── CONTROVERSY BOX ─── */
.controversy-explainer {
  background: rgba(194, 58, 43, 0.05);
  border: 1px solid rgba(194, 58, 43, 0.2);
  border-left: 3px solid var(--red);
  border-radius: 2px;
  padding: 1.2rem 1.5rem;
  margin: 2rem 0;
  font-size: 13.5px;
  color: var(--cream-dim);
  line-height: 1.7;
}

.controversy-explainer strong {
  color: var(--red);
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 2px;
  text-transform: uppercase;
  display: block;
  margin-bottom: 0.5rem;
}

/* ─── FINAL EVENT MARKER ─── */
.final-marker {
  text-align: center;
  padding: 3rem 2rem;
  position: relative;
  z-index: 5;
}

.final-marker .cross {
  font-size: 2rem;
  color: var(--red-dim);
  margin-bottom: 1rem;
}

.final-marker h2 {
  font-family: var(--serif);
  font-size: 2rem;
  font-weight: 900;
  font-style: italic;
  color: var(--cream);
}

.final-marker p {
  font-family: var(--mono);
  font-size: 11px;
  letter-spacing: 3px;
  color: var(--cream-muted);
  text-transform: uppercase;
  margin-top: 0.8rem;
}

/* ─── FOOTER ─── */
footer {
  background: var(--bg2);
  border-top: 1px solid rgba(201, 146, 42, 0.1);
  text-align: center;
  padding: 3rem 2rem;
  font-family: var(--mono);
  font-size: 10px;
  letter-spacing: 2px;
  color: var(--cream-muted);
  text-transform: uppercase;
}

/* ─── SCROLL ANIMATION ─── */
.entry { opacity: 0; transform: translateY(20px); transition: opacity 0.5s, transform 0.5s; }
.entry.visible { opacity: 1; transform: translateY(0); }
.entry.hidden { opacity: 0.08 !important; transform: none; }

/* ─── RESPONSIVE ─── */
@media (max-width: 680px) {
  .timeline-spine { left: 28px; }
  .entry, .entry.left { flex-direction: row; }
  .year-pillar, .entry.right .year-pillar { display: none; }
  .node-dot { flex: 0 0 56px; }
  .card-area, .entry.right .card-area { flex: 1; order: 3; padding-left: 0; }
  .era-label::before, .era-label::after { width: 30px; }
  .year-num { font-size: 1.6rem; }
}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-ornament">The Complete Chronicle</div>
  <h1>Mohandas<br/><em>Karamchand Gandhi</em></h1>
  <div class="header-dates">2 October 1869 — 30 January 1948</div>
  <p class="header-sub">Lawyer. Activist. Philosopher. Father of a Nation. A life that transformed the world's understanding of nonviolent resistance.</p>
  <div class="spinning-wheel" title="Charkha — the spinning wheel, symbol of self-reliance">
    <svg viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="50" cy="50" r="44" stroke="#c9922a" stroke-width="1.5" stroke-dasharray="4 3" opacity="0.6"/>
      <circle cx="50" cy="50" r="32" stroke="#c9922a" stroke-width="1" opacity="0.3"/>
      <circle cx="50" cy="50" r="4" fill="#c9922a" opacity="0.8"/>
      <!-- Spokes -->
      <line x1="50" y1="6" x2="50" y2="18" stroke="#c9922a" stroke-width="1.5" opacity="0.7"/>
      <line x1="50" y1="82" x2="50" y2="94" stroke="#c9922a" stroke-width="1.5" opacity="0.7"/>
      <line x1="6" y1="50" x2="18" y2="50" stroke="#c9922a" stroke-width="1.5" opacity="0.7"/>
      <line x1="82" y1="50" x2="94" y2="50" stroke="#c9922a" stroke-width="1.5" opacity="0.7"/>
      <line x1="19" y1="19" x2="27" y2="27" stroke="#c9922a" stroke-width="1.5" opacity="0.5"/>
      <line x1="73" y1="73" x2="81" y2="81" stroke="#c9922a" stroke-width="1.5" opacity="0.5"/>
      <line x1="81" y1="19" x2="73" y2="27" stroke="#c9922a" stroke-width="1.5" opacity="0.5"/>
      <line x1="19" y1="81" x2="27" y2="73" stroke="#c9922a" stroke-width="1.5" opacity="0.5"/>
      <line x1="32" y1="11" x2="36" y2="22" stroke="#c9922a" stroke-width="1" opacity="0.4"/>
      <line x1="68" y1="78" x2="64" y2="89" stroke="#c9922a" stroke-width="1" opacity="0.4"/>
      <line x1="89" y1="32" x2="78" y2="36" stroke="#c9922a" stroke-width="1" opacity="0.4"/>
      <line x1="11" y1="68" x2="22" y2="64" stroke="#c9922a" stroke-width="1" opacity="0.4"/>
    </svg>
  </div>
</header>

<!-- STICKY LEGEND / FILTER -->
<div class="legend-section">
  <div class="legend-inner">
    <span class="legend-label">Filter</span>
    <button class="filter-btn active" data-type="all">All Events</button>
    <button class="filter-btn" data-type="personal">Personal</button>
    <button class="filter-btn" data-type="action">Political Action</button>
    <button class="filter-btn" data-type="achievement">Achievement</button>
    <button class="filter-btn" data-type="controversy">Controversy</button>
  </div>
</div>

<!-- STAT ROW -->
<div style="max-width:900px;margin:3rem auto 0;padding:0 2rem">
  <div class="stat-row">
    <div class="stat-cell"><div class="stat-n">78</div><div class="stat-label">Years lived</div></div>
    <div class="stat-cell"><div class="stat-n">241</div><div class="stat-label">Days fasting (total)</div></div>
    <div class="stat-cell"><div class="stat-n">21</div><div class="stat-label">Years in South Africa</div></div>
    <div class="stat-cell"><div class="stat-n">6</div><div class="stat-label">Times imprisoned</div></div>
    <div class="stat-cell"><div class="stat-n">386</div><div class="stat-label">km Dandi March</div></div>
    <div class="stat-cell"><div class="stat-n">1947</div><div class="stat-label">Year of Independence</div></div>
  </div>
</div>

<!-- TIMELINE -->
<div class="timeline-container">
  <div class="timeline-spine"></div>

  <!-- ═══ ERA 1: BIRTH & YOUTH ═══ -->
  <div class="era"><div class="era-label">Birth &amp; Formative Years</div></div>

  <div class="entry left" data-type="personal">
    <div class="year-pillar"><div class="year-num">1869</div><div class="year-loc">Porbandar, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Birth of Mohandas Karamchand Gandhi</h3>
        <p>Born on 2 October 1869 in Porbandar, a coastal town in present-day Gujarat, into a Bania (merchant caste) Hindu family. His father, Karamchand Gandhi, was the diwan (chief minister) of the Porbandar state.</p>
        <div class="card-expand"><p>His mother, Putlibai, was deeply religious and her vows of fasting and prayer left a lasting impression on young Mohandas. The household practiced Vaishnavism mixed with Jain influences — a worldview emphasising non-violence and compassion that would define Gandhi's life philosophy.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="personal">
    <div class="year-pillar"><div class="year-num">1876</div><div class="year-loc">Rajkot, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Family relocates to Rajkot</h3>
        <p>The Gandhi family moves to Rajkot where his father takes up a new posting. Gandhi attends local schools; described as an unremarkable student — shy, introverted, afraid of ghosts and the dark.</p>
        <div class="card-expand"><p>He later recounted how he was terrified of the dark and would sleep with a lamp lit. His earliest moral crisis came when he stole a piece of gold from his brother's armlet to pay a debt, and then confessed to his father in writing — his father's silence and tears, rather than punishment, was Gandhi's first lesson in the power of truth.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="personal">
    <div class="year-pillar"><div class="year-num">1882</div><div class="year-loc">Porbandar, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Married at 13 to Kasturbai Makanji</h3>
        <p>In an arranged child marriage deeply embedded in local custom, Gandhi married Kasturbai Makanji (later known as Kasturba). Both were 13 years old. Gandhi later wrote of his adolescent jealousy and possessiveness with deep regret.</p>
        <div class="card-expand"><p>He would later acknowledge the cruelty of child marriage and advocate strongly against it. Yet Kasturba would become his steadfast partner, participating in his activism and enduring prison alongside him. She preceded him in death in 1944, after 62 years of marriage.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="personal">
    <div class="year-pillar"><div class="year-num">1885</div><div class="year-loc">Rajkot, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Death of his father; first child lost</h3>
        <p>His father Karamchand dies. Gandhi was attending to Kasturba on their wedding night when his father passed — a moment of guilt he carried his whole life. Their first child, born the same year, died shortly after birth.</p>
        <div class="card-expand"><p>This convergence of events — his father's death while he was away pursuing marital intimacy, and the immediate death of their infant — instilled in Gandhi a profound sense of shame about sexuality. It contributed to his later philosophy of brahmacharya (celibacy), which he formally adopted in 1906.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- ═══ ERA 2: ENGLAND ═══ -->
  <div class="era"><div class="era-label">Studies in England</div></div>

  <div class="entry left" data-type="personal">
    <div class="year-pillar"><div class="year-num">1888</div><div class="year-loc">London, England</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Sails to England to study law</h3>
        <p>Against family objections and the ruling of his caste (which declared overseas travel taboo), Gandhi travels to London to study law at the Inner Temple. He promises his mother to abstain from meat, alcohol and women.</p>
        <div class="card-expand"><p>In London he experimented with "playing the English gentleman" — buying a top hat, taking violin lessons, dancing classes, and elocution lessons — before abandoning the effort. He joined the London Vegetarian Society, becoming a member of its executive committee, and encountered the writings of Henry David Thoreau and the Sermon on the Mount, both of which shaped his ethics profoundly.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1891</div><div class="year-loc">London / Bombay</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Called to the Bar; returns to India</h3>
        <p>Gandhi is called to the Bar and admitted as a barrister of the Inner Temple. He returns to India to learn of his mother's death (kept secret to avoid distracting him). His early law practice in Bombay and Rajkot fails — he is too shy to speak in court.</p>
        <div class="card-expand"><p>His first case in Bombay saw him tongue-tied and unable to cross-examine a single witness. He fled the courtroom in embarrassment. The early failure in Indian legal practice drove him to accept a one-year contract in South Africa — a decision that transformed the course of history.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- ═══ ERA 3: SOUTH AFRICA ═══ -->
  <div class="era"><div class="era-label">South Africa — Awakening (1893–1914)</div></div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1893</div><div class="year-loc">South Africa</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>The Pietermaritzburg train incident</h3>
        <p>Travelling first class with a valid ticket, Gandhi is forcibly thrown off the train at Pietermaritzburg station for refusing to move to a third-class compartment reserved for "coloured" passengers. He spends the night shivering in the cold waiting room.</p>
        <div class="card-expand"><p>This single incident is widely regarded as the turning point in Gandhi's life. In the cold waiting room that night he deliberated — should he return to India, or stay and fight? He resolved to stay and confront racial prejudice. Later he called it the most formative experience of his life and the seed of his public activism.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="action">
    <div class="year-pillar"><div class="year-num">1894</div><div class="year-loc">Natal, South Africa</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Founds Natal Indian Congress</h3>
        <p>Gandhi founds the Natal Indian Congress (NIC) to fight discriminatory legislation targeting Indian settlers in Natal. He organises petitions, writes to newspapers, and lobbies the Colonial Secretary in London, making the plight of South African Indians an international issue for the first time.</p>
        <div class="card-expand"><p>The NIC became the first organisation Gandhi led. He used it to develop tactics he would later refine in India: mass petitioning, forming coalitions, using the press strategically, and training ordinary people to articulate their rights in legal language. He stayed two decades instead of one year.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1899</div><div class="year-loc">South Africa</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Organises Indian Ambulance Corps — Boer War</h3>
        <p>During the Anglo-Boer War, Gandhi organises an Indian Ambulance Corps of 1,100 volunteers to serve the British forces, believing loyalty would secure political rights for Indians. The corps serves at the Battle of Spion Kop.</p>
        <div class="card-expand"><p>Gandhi's support for the British Empire during the Boer War (and later World War I) remains one of his most contested decisions. Critics argue he colluded with colonial power; Gandhi maintained he was duty-bound as a British subject and hoped earned loyalty would produce rights. It did not, and later in life he acknowledged his strategic misjudgement.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1904</div><div class="year-loc">Phoenix, Natal</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Founds Phoenix Settlement &amp; Indian Opinion</h3>
        <p>Inspired by Ruskin's <em>Unto This Last</em>, Gandhi establishes the Phoenix Settlement — a communal farm near Durban where residents live simply and work collectively. He also founds the newspaper <em>Indian Opinion</em> to articulate Indian grievances.</p>
        <div class="card-expand"><p>Phoenix Settlement was Gandhi's first experiment in communal living — a precursor to his later ashrams in India. He read Ruskin's book on a train journey and was so moved he got off and began implementing its ideas immediately. The settlement blended craft, labour, simplicity and journalism, prefiguring the ashram model he would perfect in India.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1906</div><div class="year-loc">Johannesburg</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Birth of Satyagraha — First Campaign</h3>
        <p>The Transvaal government passes the Black Act requiring all Indians to carry registration passes. At a mass meeting in Johannesburg, Gandhi proposes a new form of resistance — <em>Satyagraha</em> (truth-force or soul-force). Thousands pledge to resist the law peacefully even at the cost of imprisonment.</p>
        <div class="card-expand"><p>Satyagraha was Gandhi's greatest conceptual contribution to political thought. It combined civil disobedience, self-suffering, and a refusal to hate the opponent. Gandhi distinguished it sharply from passive resistance (which he saw as a weapon of the weak) — Satyagraha was active, courageous, and based on truth. The 1906 campaign launched seven years of struggle in South Africa and prefigured every major Indian independence campaign.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="controversy">
    <div class="year-pillar"><div class="year-num">1906</div><div class="year-loc">Natal, South Africa</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Controversy</div>
        <h3>Serves British forces in Zulu Rebellion</h3>
        <p>Gandhi again organises an Indian Stretcher-Bearer Corps to support British suppression of the Zulu Bambatha Rebellion in Natal. The British response to the rebellion was brutal; Gandhi tended wounded Zulu soldiers but did not oppose the campaign.</p>
        <div class="card-expand"><p>This episode has drawn sharp criticism. African scholars and activists point out that Gandhi at this stage showed little concern for Black South Africans' rights, focusing exclusively on Indian rights. Some of his early writings used language disparaging of Black Africans that would later be strongly condemned. Gandhi's advocates note he evolved significantly on race; his critics note the evolution was incomplete and slow.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1910</div><div class="year-loc">Johannesburg</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Founds Tolstoy Farm</h3>
        <p>Inspired by Leo Tolstoy, with whom Gandhi corresponded, he establishes Tolstoy Farm near Johannesburg — a 1,100-acre communal settlement where Satyagrahi families (of resisters) live together in voluntary simplicity during the struggle.</p>
        <div class="card-expand"><p>Tolstoy Farm became the model for Gandhi's later Sabarmati and Sevagram Ashrams in India. It was intentionally multi-religious and multi-ethnic. Gandhi himself taught the children, baked bread, and did carpentry. The farm gave the movement's families a home while the breadwinners were in jail.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1913</div><div class="year-loc">South Africa</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Great March — Women enter the struggle</h3>
        <p>Gandhi leads a historic march of over 2,000 Indian coal miners across the Natal border in protest of discriminatory laws, including a £3 head tax. Indian women, led by Kasturba, march from Phoenix into Natal to invite arrest. Strikers are shot at; many are arrested. International outrage forces the South African government to negotiate.</p>
        <div class="card-expand"><p>The 1913 Great March was the climax of the South African Satyagraha. General Smuts later acknowledged Gandhi's moral authority. The Indian Relief Act of 1914 abolished the £3 tax, recognised Indian marriages, and addressed some grievances — a partial but significant victory. It proved mass civil disobedience could extract concessions from the state.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="personal">
    <div class="year-pillar"><div class="year-num">1914</div><div class="year-loc">London / India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Returns to India after 21 years</h3>
        <p>Gandhi leaves South Africa permanently, stops in London (where he organises an Indian Ambulance Corps at the outbreak of WWI), and returns to India in January 1915 at age 45. Gopal Krishna Gokhale, his political mentor, advises him to travel India for one year before entering politics.</p>
        <div class="card-expand"><p>Rabindranath Tagore, who had already won the Nobel Prize, reportedly gave Gandhi the title "Mahatma" — Great Soul — around this time. Gandhi disliked the honorific his whole life, saying it was unearned. He arrived in India a decorated but distant figure; his one year of travel transformed him into someone who intimately understood the conditions of Indian peasants.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    <blockquote>Be the change that you wish to see in the world.</blockquote>
    <div class="quote-source">— Attributed to Gandhi</div>
  </div>

  <!-- ═══ ERA 4: INDIA ═══ -->
  <div class="era"><div class="era-label">India — Rise to Leadership (1915–1930)</div></div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1916</div><div class="year-loc">Lucknow, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Sabarmati Ashram founded; Lucknow Pact</h3>
        <p>Gandhi establishes the Sabarmati Ashram near Ahmedabad — a community devoted to truth, non-violence, and village industries. At the Indian National Congress session in Lucknow he meets a young Muhammad Ali Jinnah and helps broker the Lucknow Pact between the Congress and the Muslim League.</p>
        <div class="card-expand"><p>The Sabarmati Ashram became the headquarters of Gandhi's Indian political work and the launching pad of the 1930 Salt March. Notably Gandhi admitted an "untouchable" family into the ashram — a decision that cost him many high-caste donors and nearly closed the ashram financially. He held firm. The ashram embodied his vision of social equality lived, not just proclaimed.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1917</div><div class="year-loc">Champaran, Bihar</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Champaran Satyagraha — First in India</h3>
        <p>Gandhi's first major civil disobedience in India. British planters in Champaran force peasants to grow indigo on 15% of their land at fixed prices. Gandhi arrives, investigates, organises, and is ordered to leave — he refuses. The government backs down; a commission investigates and delivers partial relief.</p>
        <div class="card-expand"><p>Champaran introduced Gandhi's working method in India: arrive, listen, document, organise locally, confront authority with truth. It also introduced him to large-scale peasant mobilisation. The government's eventual capitulation proved the method worked. Rajendra Prasad, who assisted Gandhi there, would later become India's first President. Champaran gave Gandhi national credibility beyond city-educated elites.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="action">
    <div class="year-pillar"><div class="year-num">1918</div><div class="year-loc">Ahmedabad / Kheda</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Ahmedabad Mill Strike &amp; Kheda Satyagraha</h3>
        <p>Gandhi mediates a labour dispute between Ahmedabad textile workers and mill-owners. He undertakes his first fast as a political instrument to maintain the workers' resolve. In Kheda district he supports famine-hit peasants refusing to pay land revenue — the government eventually suspends collection.</p>
        <div class="card-expand"><p>The Ahmedabad mill strike is notable because Gandhi was close friends with the mill-owner Ambalal Sarabhai, whose sister Anasuya was a strike leader. Gandhi fasted to shame both sides into agreement. Critics noted a conflict of interest; supporters saw it as Gandhi using personal sacrifice rather than power. The Kheda agitation extended Satyagraha to agrarian tax resistance.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1919</div><div class="year-loc">All India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Rowlatt Satyagraha &amp; Amritsar Massacre</h3>
        <p>Gandhi launches a nationwide hartal (strike) against the Rowlatt Act, which allowed detention without trial. The campaign spirals into violence in some areas. On 13 April 1919, British General Dyer orders troops to fire on a peaceful crowd at Jallianwala Bagh, Amritsar — killing 379 to 1,000+ people. Gandhi is shaken to the core.</p>
        <div class="card-expand"><p>The Amritsar Massacre became the turning point in Indian opinion of British rule. Gandhi initially suspended the Satyagraha when it turned violent (he called it a "Himalayan miscalculation" that he had misjudged people's readiness). But after Amritsar, his cooperation with the British Empire effectively ended. He returned his medals from the South African campaigns. He later said he could no longer in conscience participate in the British imperial project.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="action">
    <div class="year-pillar"><div class="year-num">1920</div><div class="year-loc">All India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Non-Cooperation Movement launched</h3>
        <p>Gandhi launches the Non-Cooperation Movement — his first mass national campaign. Indians are called to boycott British goods, schools, courts, and elections; return British honours; and promote khadi (hand-spun cloth) and village self-sufficiency. Millions participate. Gandhi becomes president of the Indian National Congress.</p>
        <div class="card-expand"><p>The Non-Cooperation Movement transformed the Congress from an elite debating society into a mass political party. Millions of ordinary Indians — peasants, workers, women — entered politics for the first time. The spinning wheel became a political symbol of self-reliance. The movement was suspended in 1922 after violence at Chauri Chaura (where protesters killed 22 policemen), a decision that bitterly divided the independence movement.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1922</div><div class="year-loc">Ahmedabad</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>The Great Trial — "I plead guilty"</h3>
        <p>Charged with sedition, Gandhi delivers one of history's most remarkable courtroom statements, pleading guilty and inviting the maximum punishment. He tells the judge he regards it as an honour to receive the heaviest penalty. He is sentenced to 6 years, serving 2 before release for medical treatment.</p>
        <div class="card-expand"><p>Gandhi's trial speech was a masterclass in moral authority. He acknowledged inspiring disaffection against the government, then methodically explained why the government had earned disaffection — citing Champaran, Kheda, Amritsar. He turned the dock into a lectern. Judge Broomfield sentenced him while acknowledging it was impossible not to respect him. The speech was reprinted worldwide.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="controversy">
    <div class="year-pillar"><div class="year-num">1924</div><div class="year-loc">India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Controversy</div>
        <h3>21-day fast on Hindu-Muslim unity</h3>
        <p>After his release from prison Gandhi fasts for 21 days to promote Hindu-Muslim unity amid bloody communal riots. The fast attracts enormous attention but also criticism — Ambedkar and others argue a fast is religious coercion disguised as politics.</p>
        <div class="card-expand"><p>Gandhi's use of fasting as political leverage was widely criticised by B.R. Ambedkar, who called it "a form of coercion" that backed opponents into a corner through emotional pressure rather than rational argument. Gandhi maintained it was the only weapon available to the powerless — a form of self-suffering, not aggression. The debate over whether fasting constitutes moral blackmail versus spiritual discipline remains unresolved among scholars.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- QUOTE -->
  <div class="quote-block">
    <blockquote>First they ignore you, then they laugh at you, then they fight you, then you win.</blockquote>
    <div class="quote-source">— Gandhi</div>
  </div>

  <!-- ═══ ERA 5: PEAK CAMPAIGNS ═══ -->
  <div class="era"><div class="era-label">The Great Campaigns (1930–1942)</div></div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1930</div><div class="year-loc">Dandi, Gujarat</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>The Salt March — Dandi (Defying Empire)</h3>
        <p>Gandhi leads a 386-km march from Sabarmati Ashram to the coastal village of Dandi, picking up salt from the sea to defy the British salt tax. He sets out on 12 March with 78 followers; by the time he reaches the sea on 5 April, the march has become a national movement. 60,000 people are imprisoned.</p>
        <div class="card-expand"><p>The Salt March was a masterpiece of political theatre. Gandhi wrote to the Viceroy in advance warning him exactly what he intended to do. Each step of the march was reported by international press; photographs of Gandhi stooping to pick up salt circled the globe. The spectacle of a 61-year-old man defying an empire with a handful of salt crystallised the injustice of colonial rule for a worldwide audience. Time magazine named him Man of the Year 1930.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1931</div><div class="year-loc">London, England</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Gandhi-Irwin Pact &amp; Round Table Conference</h3>
        <p>Gandhi negotiates the Gandhi-Irwin Pact, suspending civil disobedience in exchange for the release of political prisoners and right to make salt on the coast. He attends the Second Round Table Conference in London as the sole representative of the Congress. He meets Charlie Chaplin and the King.</p>
        <div class="card-expand"><p>Gandhi's appearance in London — dhoti, walking stick, shawl — was itself a statement. When asked if he thought his dress was appropriate to meet the King, he said "the King was wearing enough for both of us." The Round Table Conference failed to produce a constitutional agreement, but Gandhi's London visit transformed him into a global icon. The Lancashire mill workers, whose livelihoods he threatened by boycotting British cloth, famously cheered him.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="controversy">
    <div class="year-pillar"><div class="year-num">1932</div><div class="year-loc">Poona, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Controversy</div>
        <h3>Poona Pact — Gandhi vs. Ambedkar</h3>
        <p>The British award Dalits (untouchables) separate electorates. Gandhi fasts unto death to oppose this, calling separate representation a barrier to Hindu unity. Ambedkar, the Dalit leader, is forced to negotiate the Poona Pact under duress — exchanging separate electorates for reserved seats in general Hindu constituencies.</p>
        <div class="card-expand"><p>This remains Gandhi's most contested act. Ambedkar believed separate electorates were the only mechanism to guarantee Dalit political power independent of upper-caste votes. He argued — compellingly — that Gandhi's fast amounted to using his life as a veto over Dalit political rights. Gandhi had spoken warmly of "Harijans" (his term for Dalits, rejected by Ambedkar as patronising) but his opposition to separate electorates denied Dalits independent political agency. Many Dalit scholars consider this Gandhi's greatest failure.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1934</div><div class="year-loc">India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Village Industry movement; Harijan campaigns</h3>
        <p>Gandhi establishes the All India Village Industries Association and embarks on tours fighting untouchability. He walks through villages opening temples to Dalits, campaigns for their right to use public wells, and writes extensively in his newspaper <em>Harijan</em> on caste reform.</p>
        <div class="card-expand"><p>Gandhi's anti-untouchability campaigns were genuinely radical within Hinduism — he insisted that untouchability was a "poison that has entered the body of Hinduism" and that no one who practised it could call themselves Hindu. He was attacked and nearly killed by a Hindu zealot in 1934 for this stance. Yet Ambedkar maintained Gandhi's approach was reformist rather than abolitionist — patching the caste system rather than dismantling it.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="controversy">
    <div class="year-pillar"><div class="year-num">1939</div><div class="year-loc">India / Europe</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Controversy</div>
        <h3>Gandhi's letters to Hitler; non-resistance to fascism</h3>
        <p>Gandhi writes two personal letters to Adolf Hitler (1939 and 1940) addressed "Dear Friend," appealing to him to avoid war and asking him to apply nonviolence. The letters drew sharp criticism — viewed as naive, morally tone-deaf, or worse.</p>
        <div class="card-expand"><p>Gandhi also advised European Jews to "offer themselves to the butcher's knife" through nonviolent resistance to the Nazis. In 1946 he told Louis Fischer that the Holocaust was a successful example of Jewish sacrifice. These statements remain deeply shocking and were vigorously condemned by Jewish leaders, including Einstein. Gandhi's defenders argue his philosophy of nonviolence was universally applied; his critics argue he catastrophically misread totalitarian violence. George Orwell called Gandhi's politics workable only against opponents "who have a spark of decency."</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="action">
    <div class="year-pillar"><div class="year-num">1942</div><div class="year-loc">Bombay, India</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Quit India Movement — "Do or Die"</h3>
        <p>On 8 August 1942 Gandhi delivers his most electrifying speech at Gowalia Tank Maidan, Bombay, launching the Quit India Movement: "Do or Die — we shall either free India or die in the attempt." The next morning the entire Congress leadership is arrested. Mass rebellion erupts across India.</p>
        <div class="card-expand"><p>The Quit India Movement was Gandhi's most radical campaign — a call for immediate, unconditional British withdrawal during a world war. The British response was ferocious: 100,000 arrests, 1,000 deaths, and two years of suppression. Gandhi was imprisoned at the Aga Khan Palace. The movement failed militarily but deepened the conviction that India's independence was inevitable. Gandhi himself spent most of 1942–44 imprisoned, where Kasturba died in his arms in February 1944.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- ═══ ERA 6: FINAL YEARS ═══ -->
  <div class="era"><div class="era-label">Independence &amp; Partition (1944–1948)</div></div>

  <div class="entry left" data-type="personal">
    <div class="year-pillar"><div class="year-num">1944</div><div class="year-loc">Aga Khan Palace, Pune</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Personal</div>
        <h3>Kasturba dies in imprisonment; Gandhi's health breaks</h3>
        <p>Kasturba Gandhi dies in Gandhi's arms on 22 February 1944, after being imprisoned alongside him for 18 months. Gandhi is devastated. He says: "I cannot imagine life without Ba." He himself nearly dies of malaria shortly after, and is released in May 1944.</p>
        <div class="card-expand"><p>Kasturba's death while imprisoned provoked outrage across India and internationally. She had been arrested at age 74 and was ill throughout her imprisonment; the British denied her penicillin treatment. Their marriage had been unequal by their own early admission — Gandhi was domineering in youth — but evolved into a profound partnership. Gandhi wrote that she was braver than him in facing imprisonment without complaint.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="controversy">
    <div class="year-pillar"><div class="year-num">1946</div><div class="year-loc">Noakhali, Bengal</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Controversy</div>
        <h3>Brahmacharya experiments — "sleeping naked with women"</h3>
        <p>In his ashram and during his Noakhali peace walks, Gandhi conducted controversial experiments in celibacy — sleeping next to young women (including his grandniece Manu Gandhi) to "test" his brahmacharya vows. These were widely condemned by colleagues including Nehru and Patel.</p>
        <div class="card-expand"><p>Gandhi called these experiments essential to building his spiritual strength. Many close associates — including Nirmal Kumar Bose (his secretary) and Pyarelal Nayar — expressed deep unease. Contemporary critics describe the experiments as involving inherent power imbalances and psychological harm to the young women, regardless of intent. This remains one of the most contested and troubling aspects of Gandhi's personal conduct. Several of Gandhi's grandnieces spoke about it in later decades with evident discomfort.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1946</div><div class="year-loc">Noakhali, Bengal</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Noakhali peace walks amid communal violence</h3>
        <p>Amid catastrophic Hindu-Muslim violence in Noakhali (Bengal) following the Cabinet Mission's failure, Gandhi walks barefoot through 47 riot-affected villages over four months, often alone, personally appealing for peace. He is 77, barefoot, walking on shards and thorns.</p>
        <div class="card-expand"><p>The Noakhali peace mission was Gandhi at his most elemental — stripped of institutional politics, walking alone into violence. He took a vow not to leave Bengal until peace was restored. The walks had a measurable effect in the districts he visited. Years later, Mountbatten said Gandhi alone had done more for communal peace in Noakhali than an entire army division could do in the Punjab.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry right" data-type="achievement">
    <div class="year-pillar"><div class="year-num">1947</div><div class="year-loc">Calcutta / New Delhi</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Achievement</div>
        <h3>Independence — but also Partition</h3>
        <p>India gains independence at midnight on 14/15 August 1947. Gandhi is not in Delhi; he is in Calcutta fasting to stop communal killings. He refuses to attend independence celebrations, calling it a day of mourning for the partition he had opposed. He is later called "a one-man boundary force."</p>
        <div class="card-expand"><p>Gandhi wept at Partition. He had consistently opposed dividing India along religious lines, arguing that Hindus and Muslims were one people. He felt personally responsible — had he done more, could it have been avoided? His fast in Calcutta on 15 August 1947 stopped violence in the city almost overnight, leading Mountbatten to write that Gandhi had achieved what 50,000 soldiers could not. He accepted independence as incomplete, insisting the real test was whether free India would serve its poorest citizens.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <div class="entry left" data-type="action">
    <div class="year-pillar"><div class="year-num">1948</div><div class="year-loc">New Delhi</div></div>
    <div class="node-dot"><div class="dot-ring"></div></div>
    <div class="card-area">
      <div class="card" onclick="this.classList.toggle('open')">
        <div class="card-tag">Political Action</div>
        <h3>Final fast — for peace in Delhi</h3>
        <p>On 13 January 1948 Gandhi begins his last fast — demanding that India release Rs 55 crore owed to Pakistan under partition terms, and that Delhi's Muslims be guaranteed safety. The government complies. He breaks the fast on 18 January 1948. It is his final act.</p>
        <div class="card-expand"><p>The last fast drew fury from Hindu nationalist groups who saw Gandhi as protecting Pakistan. Nathuram Godse and his co-conspirators had already made one failed assassination attempt on 20 January. Gandhi dismissed warnings of danger. On 29 January he said to his grandniece Manu: "If someone were to fire a bullet at me and I took the blow with a smile on my face, praying for my assassin — only then should you say I was a true man." The next evening, he walked to evening prayer.</p></div>
        <div class="card-more">More detail</div>
      </div>
    </div>
  </div>

  <!-- FINAL EVENT -->
  <div class="final-marker">
    <div class="cross">✦</div>
    <h2>30 January 1948</h2>
    <p>Birla House, New Delhi — 5:17 pm</p>
  </div>

</div>

<!-- ASSASSINATION SECTION -->
<div style="max-width:900px;margin:0 auto;padding:0 2rem 6rem">

  <div class="controversy-explainer">
    <strong>Assassination — 30 January 1948</strong>
    At 5:17 pm, Gandhi was walking to his evening prayer meeting at Birla House, supported by his grandnieces. Nathuram Godse, a Hindu nationalist who blamed Gandhi for appeasing Muslims and for Partition, stepped forward from the crowd, bowed to Gandhi, then fired three shots at point-blank range. Gandhi said "Hey Ram" (O God) and collapsed. He died minutes later. He was 78 years old.<br/><br/>
    Godse and conspirator Narayan Apte were executed in November 1949. Godse argued in court — in a speech the Indian government tried to suppress — that Gandhi's policy of non-violence had led to the slaughter of Hindus during Partition and his appeasement of Pakistan had weakened India. The speech was banned in India for decades. Gandhi's assassination shocked the world. Prime Minister Nehru broadcast to the nation: "The light has gone out of our lives and there is darkness everywhere."
  </div>

  <div class="stat-row">
    <div class="stat-cell"><div class="stat-n">78</div><div class="stat-label">Age at death</div></div>
    <div class="stat-cell"><div class="stat-n">3</div><div class="stat-label">Bullets fired</div></div>
    <div class="stat-cell"><div class="stat-n">5:17</div><div class="stat-label">Time of death</div></div>
    <div class="stat-cell"><div class="stat-n">1948</div><div class="stat-label">Year of assassination</div></div>
  </div>

  <!-- LEGACY -->
  <div style="margin-top:4rem">
    <div class="era"><div class="era-label">Legacy &amp; Global Impact</div></div>

    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:1px;background:rgba(201,146,42,0.08);border:1px solid rgba(201,146,42,0.08);border-radius:3px;overflow:hidden;margin-top:2rem">
      <div style="background:var(--surface);padding:1.4rem 1.5rem">
        <div style="font-family:var(--mono);font-size:9px;letter-spacing:2px;color:var(--gold);text-transform:uppercase;margin-bottom:0.6rem">Philosophy</div>
        <p style="font-size:13.5px;color:var(--cream-dim);line-height:1.65">Satyagraha became the foundational theory of nonviolent civil disobedience adopted worldwide — by the US civil rights movement, Nelson Mandela, Aung San Suu Kyi, anti-apartheid activists, and the Solidarity movement in Poland.</p>
      </div>
      <div style="background:var(--surface);padding:1.4rem 1.5rem">
        <div style="font-family:var(--mono);font-size:9px;letter-spacing:2px;color:var(--blue);text-transform:uppercase;margin-bottom:0.6rem">Influence</div>
        <p style="font-size:13.5px;color:var(--cream-dim);line-height:1.65">Martin Luther King Jr. studied Gandhi extensively and modelled the Montgomery Bus Boycott on Satyagraha. He visited India in 1959 and called Gandhi "the guiding light of our technique of nonviolent social change."</p>
      </div>
      <div style="background:var(--surface);padding:1.4rem 1.5rem">
        <div style="font-family:var(--mono);font-size:9px;letter-spacing:2px;color:var(--red);text-transform:uppercase;margin-bottom:0.6rem">Criticism</div>
        <p style="font-size:13.5px;color:var(--cream-dim);line-height:1.65">B.R. Ambedkar, Subhas Chandra Bose, and later African scholars challenged Gandhi's record on caste, race, and political strategy. His legacy remains deeply contested — a saint to some, a political conservative to others.</p>
      </div>
      <div style="background:var(--surface);padding:1.4rem 1.5rem">
        <div style="font-family:var(--mono);font-size:9px;letter-spacing:2px;color:var(--green);text-transform:uppercase;margin-bottom:0.6rem">Commemoration</div>
        <p style="font-size:13.5px;color:var(--cream-dim);line-height:1.65">2 October is celebrated as Gandhi Jayanti (national holiday in India) and International Day of Non-Violence by the United Nations. He appears on every Indian rupee note and is officially titled "Father of the Nation."</p>
      </div>
    </div>
  </div>

  <!-- Final quote -->
  <div class="quote-block" style="margin-top:4rem">
    <blockquote>My life is my message.</blockquote>
    <div class="quote-source">— Mohandas Karamchand Gandhi</div>
  </div>

</div>

<footer>
  <div>Mohandas Karamchand Gandhi · 1869–1948 · A complete chronicle of actions, achievements &amp; controversies</div>
  <div style="margin-top:0.5rem;opacity:0.5">Sources: Gandhi's Autobiography (The Story of My Experiments with Truth) · Ramachandra Guha's Gandhi Before India &amp; Gandhi: The Years That Changed the World · Ambedkar's What Congress and Gandhi Have Done to the Untouchables</div>
</footer>

<script>
// ─── SCROLL REVEAL ───
const entries = document.querySelectorAll('.entry');
const observer = new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.classList.add('visible');
    }
  });
}, { threshold: 0.1, rootMargin: '0px 0px -40px 0px' });
entries.forEach(e => observer.observe(e));

// ─── FILTER ───
const btns = document.querySelectorAll('.filter-btn');
btns.forEach(btn => {
  btn.addEventListener('click', () => {
    btns.forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    const type = btn.dataset.type;
    entries.forEach(entry => {
      if (type === 'all' || entry.dataset.type === type) {
        entry.classList.remove('hidden');
      } else {
        entry.classList.add('hidden');
      }
    });
  });
});
</script>
</body>
</html>

```


------------------------------------------------------------------

