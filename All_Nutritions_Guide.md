```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Complete Human Nutrition Atlas</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Mono:ital,wght@0,300;0,400;0,500;1,300&family=Playfair+Display:ital,wght@0,700;0,900;1,700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
:root {
  --bg:         #0a0a0f;
  --bg2:        #0f0f1a;
  --bg3:        #141425;
  --card:       #111120;
  --border:     #1e1e3a;
  --accent1:    #00d4aa;
  --accent2:    #ff6b6b;
  --accent3:    #ffd166;
  --accent4:    #a78bfa;
  --accent5:    #38bdf8;
  --accent6:    #fb923c;
  --text:       #e8e8f0;
  --text2:      #9898b8;
  --text3:      #5a5a80;
  --mono:       'DM Mono', monospace;
  --display:    'Playfair Display', serif;
  --sans:       'Syne', sans-serif;
}

* { margin:0; padding:0; box-sizing:border-box; }

html { scroll-behavior: smooth; }

body {
  background: var(--bg);
  color: var(--text);
  font-family: var(--mono);
  font-size: 13px;
  line-height: 1.7;
  overflow-x: hidden;
}

/* ─── NOISE OVERLAY ─── */
body::before {
  content:'';
  position:fixed; inset:0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
  pointer-events:none; z-index:0; opacity:.4;
}

/* ─── HERO ─── */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex; flex-direction: column;
  justify-content: center; align-items: center;
  text-align: center;
  padding: 4rem 2rem;
  overflow: hidden;
}

.hero-glow {
  position: absolute;
  border-radius: 50%;
  filter: blur(120px);
  pointer-events: none;
  animation: pulse 8s ease-in-out infinite alternate;
}
.glow-a { width:600px; height:600px; background: rgba(0,212,170,0.08); top:-200px; left:-200px; }
.glow-b { width:500px; height:500px; background: rgba(167,139,250,0.07); bottom:-150px; right:-150px; animation-delay:3s; }
.glow-c { width:300px; height:300px; background: rgba(255,107,107,0.05); top:50%; left:50%; transform:translate(-50%,-50%); animation-delay:6s; }

@keyframes pulse { from{opacity:.5;transform:scale(1)} to{opacity:1;transform:scale(1.1)} }

.hero-label {
  font-family: var(--mono);
  font-size: 11px; letter-spacing:.25em; text-transform:uppercase;
  color: var(--accent1); margin-bottom:1.5rem;
  border: 1px solid rgba(0,212,170,.25);
  padding: .3rem 1rem; border-radius: 2rem;
  display: inline-block;
}

.hero h1 {
  font-family: var(--display);
  font-size: clamp(2.8rem, 8vw, 6rem);
  font-weight: 900;
  line-height: 1.05;
  color: #fff;
  margin-bottom: .5rem;
}
.hero h1 em { font-style: italic; color: var(--accent1); }

.hero-sub {
  font-family: var(--mono); font-size: 12px; letter-spacing: .15em;
  color: var(--text2); margin-bottom: 3rem; text-transform: uppercase;
}

/* ─── TOC GRID ─── */
.toc-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
  gap: .75rem; max-width: 900px; width: 100%;
}

.toc-pill {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: .5rem;
  padding: .6rem .8rem;
  text-decoration: none;
  color: var(--text2);
  font-size: 11px;
  letter-spacing:.05em;
  transition: all .2s;
  display: flex; align-items: center; gap:.5rem;
}
.toc-pill:hover { color: var(--text); border-color: var(--accent1); background: rgba(0,212,170,.06); }
.toc-pill span { font-size:16px; }

/* ─── SECTIONS ─── */
.section {
  max-width: 1400px; margin: 0 auto;
  padding: 5rem 2rem;
  position: relative; z-index: 1;
}

.section-header {
  display: flex; align-items: baseline; gap: 1rem;
  margin-bottom: 3rem;
  border-bottom: 1px solid var(--border);
  padding-bottom: 1.5rem;
}

.section-number {
  font-family: var(--mono); font-size: 11px;
  color: var(--text3); letter-spacing: .2em;
}

.section-title {
  font-family: var(--display);
  font-size: clamp(1.8rem, 4vw, 3rem);
  font-weight: 700; color: #fff;
}

.section-accent { color: var(--accent1); }

/* ─── NUTRITION CARDS ─── */
.cards-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(360px, 1fr));
  gap: 1.5rem;
}

.nutr-card {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: .75rem;
  overflow: hidden;
  transition: transform .2s, border-color .2s;
  animation: fadeUp .5s ease both;
}
.nutr-card:hover { transform: translateY(-3px); }

@keyframes fadeUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }

.card-header {
  padding: 1.2rem 1.4rem;
  display: flex; align-items: center; gap: 1rem;
  border-bottom: 1px solid var(--border);
}

.card-icon {
  width: 44px; height: 44px;
  border-radius: .5rem;
  display: flex; align-items: center; justify-content: center;
  font-size: 22px; flex-shrink: 0;
}

.card-meta { flex: 1; }

.card-name {
  font-family: var(--sans);
  font-size: 15px; font-weight: 700; color: #fff;
}

.card-also {
  font-family: var(--mono); font-size: 10px;
  color: var(--text3); letter-spacing: .05em;
}

.card-type-badge {
  font-size: 9px; letter-spacing: .15em;
  text-transform: uppercase;
  padding: .2rem .6rem;
  border-radius: 2rem;
  font-family: var(--mono);
}

.card-body { padding: 1.2rem 1.4rem; }

.info-row {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: .75rem;
  margin-bottom: .75rem;
}

.info-box {
  background: rgba(255,255,255,.025);
  border-radius: .4rem; padding: .7rem;
  border: 1px solid rgba(255,255,255,.04);
}

.info-box-label {
  font-size: 9px; letter-spacing: .18em;
  text-transform: uppercase; color: var(--text3);
  margin-bottom: .3rem; font-family: var(--mono);
}

.info-box-val {
  font-size: 12px; color: var(--text);
  line-height: 1.5;
}

.info-full {
  background: rgba(255,255,255,.025);
  border-radius: .4rem; padding: .7rem;
  border: 1px solid rgba(255,255,255,.04);
  margin-bottom: .75rem;
}

.pill-list {
  display: flex; flex-wrap: wrap; gap: .35rem;
  margin-top: .4rem;
}

.pill {
  font-size: 10px; padding: .15rem .5rem;
  border-radius: 2rem; font-family: var(--mono);
  letter-spacing: .03em;
}
.pill-green  { background: rgba(0,212,170,.12); color: var(--accent1); border: 1px solid rgba(0,212,170,.2); }
.pill-red    { background: rgba(255,107,107,.12); color: var(--accent2); border: 1px solid rgba(255,107,107,.2); }
.pill-yellow { background: rgba(255,209,102,.12); color: var(--accent3); border: 1px solid rgba(255,209,102,.2); }
.pill-purple { background: rgba(167,139,250,.12); color: var(--accent4); border: 1px solid rgba(167,139,250,.2); }
.pill-blue   { background: rgba(56,189,248,.12);  color: var(--accent5); border: 1px solid rgba(56,189,248,.2); }
.pill-orange { background: rgba(251,146,60,.12);  color: var(--accent6); border: 1px solid rgba(251,146,60,.2); }

/* body map bar */
.body-bar {
  margin-top: .5rem;
  display: flex; flex-wrap: wrap; gap: .3rem;
}
.body-tag {
  font-size: 9px; padding: .1rem .4rem;
  border-radius: .25rem;
  background: rgba(255,255,255,.04);
  color: var(--text2); border: 1px solid rgba(255,255,255,.06);
  font-family: var(--mono); letter-spacing: .03em;
}

/* pros / cons */
.pro-con {
  display: grid; grid-template-columns: 1fr 1fr;
  gap: .5rem; margin-top: .5rem;
}
.pro-con-box { border-radius:.4rem; padding:.6rem; border:1px solid transparent; }
.pros { background: rgba(0,212,170,.06); border-color: rgba(0,212,170,.15); }
.cons { background: rgba(255,107,107,.06); border-color: rgba(255,107,107,.15); }
.pro-con-title { font-size:9px; letter-spacing:.15em; text-transform:uppercase; font-family:var(--mono); margin-bottom:.3rem; }
.pros .pro-con-title { color: var(--accent1); }
.cons .pro-con-title { color: var(--accent2); }
.pro-con-box ul { list-style:none; }
.pro-con-box ul li { font-size:10px; color:var(--text2); padding:.1rem 0; }
.pro-con-box ul li::before { content:'› '; color:var(--text3); }

/* ─── HUMAN BODY SVG ─── */
.body-section {
  background: var(--card);
  border: 1px solid var(--border);
  border-radius: .75rem;
  padding: 2rem;
  margin-bottom: 3rem;
}

/* ─── MACROS TABLE ─── */
.macro-table-wrap { overflow-x:auto; }
.macro-table {
  width:100%; border-collapse:collapse;
  font-family:var(--mono); font-size:12px;
}
.macro-table th {
  background: rgba(255,255,255,.04);
  color: var(--text2);
  font-size: 9px; letter-spacing:.15em; text-transform:uppercase;
  padding: .6rem 1rem; text-align:left;
  border-bottom: 1px solid var(--border);
}
.macro-table td {
  padding: .75rem 1rem;
  border-bottom: 1px solid rgba(255,255,255,.04);
  color: var(--text);
  vertical-align: top;
}
.macro-table tr:hover td { background: rgba(255,255,255,.02); }

/* ─── DEFICIENCY WARN ─── */
.warn-grid {
  display:grid;
  grid-template-columns: repeat(auto-fill, minmax(280px,1fr));
  gap:1rem;
}
.warn-card {
  border-radius:.5rem; padding:1rem 1.2rem;
  background: rgba(255,107,107,.05);
  border: 1px solid rgba(255,107,107,.15);
}
.warn-card-title {
  font-family:var(--sans); font-size:13px; font-weight:700;
  color: var(--accent2); margin-bottom:.4rem;
}
.warn-card-body { font-size:11px; color:var(--text2); line-height:1.6; }

/* ─── INTERACTION BOX ─── */
.interact-grid {
  display:grid;
  grid-template-columns: repeat(auto-fill, minmax(300px,1fr));
  gap:1rem;
}
.interact-card {
  border-radius:.5rem; padding:1rem 1.2rem;
  background: rgba(167,139,250,.05);
  border: 1px solid rgba(167,139,250,.15);
}
.interact-card-title { font-family:var(--sans); font-size:13px; font-weight:700; color:var(--accent4); margin-bottom:.4rem; }
.interact-card-body { font-size:11px; color:var(--text2); line-height:1.6; }

/* ─── FOOD SOURCE VISUAL ─── */
.food-grid {
  display:grid;
  grid-template-columns: repeat(auto-fill, minmax(200px,1fr));
  gap:1rem;
}
.food-card {
  border-radius:.5rem; padding:1rem;
  background: var(--card); border:1px solid var(--border);
  text-align:center;
}
.food-emoji { font-size: 2.5rem; margin-bottom:.4rem; }
.food-name { font-family:var(--sans); font-size:13px; font-weight:700; color:#fff; margin-bottom:.3rem; }
.food-contains { font-size:10px; color:var(--text2); line-height:1.5; }

/* ─── DIVIDER ─── */
.divider {
  border:none; height:1px;
  background: linear-gradient(90deg, transparent, var(--border), transparent);
  margin: 0 2rem;
}

/* ─── FOOTER ─── */
footer {
  text-align:center; padding:3rem 2rem;
  font-size:11px; color:var(--text3);
  border-top:1px solid var(--border);
}
footer strong { color:var(--accent1); }

/* ─── SCROLLBAR ─── */
::-webkit-scrollbar { width:6px; height:6px; }
::-webkit-scrollbar-track { background:var(--bg); }
::-webkit-scrollbar-thumb { background:var(--border); border-radius:3px; }

/* color themes per card */
.c-a1 { --cc: var(--accent1); }
.c-a2 { --cc: var(--accent2); }
.c-a3 { --cc: var(--accent3); }
.c-a4 { --cc: var(--accent4); }
.c-a5 { --cc: var(--accent5); }
.c-a6 { --cc: var(--accent6); }

.nutr-card:hover { border-color: var(--cc, var(--border)); }
.card-header { border-bottom-color: var(--border); }
.card-icon { background: color-mix(in srgb, var(--cc,var(--accent1)) 15%, transparent); }
.card-type-badge.c-a1 { background:rgba(0,212,170,.15); color:var(--accent1); border:1px solid rgba(0,212,170,.25); }
.card-type-badge.c-a2 { background:rgba(255,107,107,.15); color:var(--accent2); border:1px solid rgba(255,107,107,.25); }
.card-type-badge.c-a3 { background:rgba(255,209,102,.15); color:var(--accent3); border:1px solid rgba(255,209,102,.25); }
.card-type-badge.c-a4 { background:rgba(167,139,250,.15); color:var(--accent4); border:1px solid rgba(167,139,250,.25); }
.card-type-badge.c-a5 { background:rgba(56,189,248,.15);  color:var(--accent5); border:1px solid rgba(56,189,248,.25); }
.card-type-badge.c-a6 { background:rgba(251,146,60,.15);  color:var(--accent6); border:1px solid rgba(251,146,60,.25); }
</style>
</head>
<body>

<!-- HERO -->
<section class="hero">
  <div class="hero-glow glow-a"></div>
  <div class="hero-glow glow-b"></div>
  <div class="hero-glow glow-c"></div>
  <p class="hero-label">Complete Reference Atlas · 2026 Edition</p>
  <h1>Human <em>Nutrition</em></h1>
  <p class="hero-sub">Vitamins · Minerals · Macronutrients · Phytonutrients · Water</p>
  <nav class="toc-grid">
    <a class="toc-pill" href="#fat-soluble"><span>🔆</span> Fat-Sol. Vitamins</a>
    <a class="toc-pill" href="#water-soluble"><span>💧</span> Water-Sol. Vitamins</a>
    <a class="toc-pill" href="#macrominerals"><span>🪨</span> Macrominerals</a>
    <a class="toc-pill" href="#traceminerals"><span>⚗️</span> Trace Minerals</a>
    <a class="toc-pill" href="#macronutrients"><span>⚡</span> Macronutrients</a>
    <a class="toc-pill" href="#phyto"><span>🌿</span> Phytonutrients</a>
    <a class="toc-pill" href="#water"><span>🌊</span> Water & Electrolytes</a>
    <a class="toc-pill" href="#body-map"><span>🧬</span> Body Impact Map</a>
    <a class="toc-pill" href="#deficiency"><span>⚠️</span> Deficiencies</a>
    <a class="toc-pill" href="#food-sources"><span>🥗</span> Food Sources</a>
    <a class="toc-pill" href="#interactions"><span>🔗</span> Interactions</a>
  </nav>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ FAT-SOLUBLE VITAMINS ═══════════════════════════════ -->
<section class="section" id="fat-soluble">
  <div class="section-header">
    <span class="section-number">01</span>
    <h2 class="section-title">Fat-Soluble <span class="section-accent">Vitamins</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Stored in fatty tissues and liver. Excess can accumulate and become toxic. Require dietary fat for absorption.</p>

  <div class="cards-grid">

    <!-- VITAMIN A -->
    <div class="nutr-card c-a6" style="animation-delay:.05s">
      <div class="card-header">
        <div class="card-icon">🟠</div>
        <div class="card-meta">
          <div class="card-name">Vitamin A</div>
          <div class="card-also">Retinol · β-Carotene · Retinal</div>
        </div>
        <span class="card-type-badge c-a6">Fat-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">700–900 µg RAE/day</div></div>
          <div class="info-box"><div class="info-box-label">UL (Upper Limit)</div><div class="info-box-val">3,000 µg/day (preformed)</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Vision (rhodopsin synthesis), immune cell differentiation, epithelial integrity, embryonic development, gene expression regulation.</div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Body Targets</div>
          <div class="body-bar">
            <span class="body-tag">Eyes</span><span class="body-tag">Skin</span><span class="body-tag">Lungs</span><span class="body-tag">Immune System</span><span class="body-tag">Liver</span><span class="body-tag">Reproductive Organs</span>
          </div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Natural Sources</div>
          <div class="pill-list">
            <span class="pill pill-orange">Beef liver</span><span class="pill pill-orange">Egg yolk</span><span class="pill pill-green">Carrots</span><span class="pill pill-green">Sweet potato</span><span class="pill pill-green">Spinach</span><span class="pill pill-green">Mango</span>
          </div>
        </div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Night vision</li><li>Skin barrier repair</li><li>Infection resistance</li><li>Bone remodelling</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Excess / Deficiency</div><ul><li>Toxicity → liver damage</li><li>Teratogenic in pregnancy</li><li>Deficiency → night blindness</li><li>Dry skin, infections</li></ul></div>
        </div>
      </div>
    </div>

    <!-- VITAMIN D -->
    <div class="nutr-card c-a3" style="animation-delay:.1s">
      <div class="card-header">
        <div class="card-icon">☀️</div>
        <div class="card-meta">
          <div class="card-name">Vitamin D</div>
          <div class="card-also">Cholecalciferol (D3) · Ergocalciferol (D2)</div>
        </div>
        <span class="card-type-badge c-a3">Fat-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">600–800 IU (15–20 µg)</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">4,000 IU/day</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Calcium & phosphorus absorption, bone mineralisation, immune modulation, muscle function, cell growth regulation, mood regulation via serotonin pathways.</div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Body Targets</div>
          <div class="body-bar">
            <span class="body-tag">Bones</span><span class="body-tag">Kidneys</span><span class="body-tag">Gut</span><span class="body-tag">Immune</span><span class="body-tag">Brain</span><span class="body-tag">Muscles</span><span class="body-tag">Heart</span>
          </div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Natural Sources</div>
          <div class="pill-list">
            <span class="pill pill-yellow">Sunlight (UVB)</span><span class="pill pill-blue">Salmon</span><span class="pill pill-blue">Mackerel</span><span class="pill pill-yellow">Egg yolk</span><span class="pill pill-blue">Cod liver oil</span><span class="pill pill-green">Mushrooms (UV)</span>
          </div>
        </div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Prevents rickets/osteoporosis</li><li>Mood & depression support</li><li>Immune defence</li><li>Reduces cancer risk</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Hypercalcaemia (excess)</li><li>Kidney stones (excess)</li><li>Deficiency: 1 billion+ globally</li><li>Indoor lifestyle risk</li></ul></div>
        </div>
      </div>
    </div>

    <!-- VITAMIN E -->
    <div class="nutr-card c-a1" style="animation-delay:.15s">
      <div class="card-header">
        <div class="card-icon">🟢</div>
        <div class="card-meta">
          <div class="card-name">Vitamin E</div>
          <div class="card-also">α-Tocopherol (most active) · 8 forms total</div>
        </div>
        <span class="card-type-badge c-a1">Fat-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">15 mg α-TE/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">1,000 mg/day</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Potent antioxidant — protects cell membranes from lipid peroxidation. Immune enhancement, vasodilation (via prostaglandins), anti-platelet aggregation, gene expression.</div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Body Targets</div>
          <div class="body-bar">
            <span class="body-tag">Cell Membranes</span><span class="body-tag">Blood Vessels</span><span class="body-tag">Nerves</span><span class="body-tag">Skin</span><span class="body-tag">Lungs</span><span class="body-tag">Immune</span>
          </div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Natural Sources</div>
          <div class="pill-list">
            <span class="pill pill-green">Almonds</span><span class="pill pill-green">Sunflower seeds</span><span class="pill pill-orange">Wheat germ oil</span><span class="pill pill-green">Avocado</span><span class="pill pill-green">Spinach</span><span class="pill pill-green">Hazelnuts</span>
          </div>
        </div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Slows oxidative aging</li><li>Cardiovascular protection</li><li>Skin health & wound healing</li><li>Eye health (cataracts)</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Blood thinning (high dose)</li><li>Interferes with Vit K clotting</li><li>Isolated deficiency rare</li></ul></div>
        </div>
      </div>
    </div>

    <!-- VITAMIN K -->
    <div class="nutr-card c-a4" style="animation-delay:.2s">
      <div class="card-header">
        <div class="card-icon">🟣</div>
        <div class="card-meta">
          <div class="card-name">Vitamin K</div>
          <div class="card-also">K1 (Phylloquinone) · K2 (Menaquinone)</div>
        </div>
        <span class="card-type-badge c-a4">Fat-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">90–120 µg/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">No established UL</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">K1: Blood coagulation (activates clotting factors II, VII, IX, X). K2: Calcium routing — activates osteocalcin (bone) and matrix Gla protein (arteries). Critical distinction: K2 (MK-7) stays in blood longest.</div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Body Targets</div>
          <div class="body-bar">
            <span class="body-tag">Liver</span><span class="body-tag">Blood (clotting)</span><span class="body-tag">Bones</span><span class="body-tag">Arteries</span><span class="body-tag">Heart</span><span class="body-tag">Kidneys</span>
          </div>
        </div>
        <div class="info-full">
          <div class="info-box-label">Natural Sources</div>
          <div class="pill-list">
            <span class="pill pill-green">Natto (K2 MK-7)</span><span class="pill pill-green">Kale</span><span class="pill pill-green">Spinach</span><span class="pill pill-green">Broccoli</span><span class="pill pill-yellow">Cheese (K2)</span><span class="pill pill-yellow">Egg yolk</span>
          </div>
        </div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Prevents haemorrhage</li><li>Stronger bones (K2)</li><li>Prevents arterial calcification</li><li>Synergistic with Vit D</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Antagonises Warfarin</li><li>Deficiency: newborns at risk</li><li>K1 vs K2 often confused</li></ul></div>
        </div>
      </div>
    </div>

  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ WATER-SOLUBLE VITAMINS ═══════════════════════════════ -->
<section class="section" id="water-soluble">
  <div class="section-header">
    <span class="section-number">02</span>
    <h2 class="section-title">Water-Soluble <span class="section-accent">Vitamins</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Not stored long-term. Excess mostly excreted in urine. Must be replenished regularly. Includes all B vitamins + Vitamin C.</p>

  <div class="cards-grid">

    <!-- B1 -->
    <div class="nutr-card c-a5" style="animation-delay:.05s">
      <div class="card-header">
        <div class="card-icon">💧</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B1 — Thiamine</div>
          <div class="card-also">Thiamin pyrophosphate (TPP) — active form</div>
        </div>
        <span class="card-type-badge c-a5">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1.1–1.2 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Whole grains, pork, legumes, nuts</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Carbohydrate metabolism — co-factor in pyruvate dehydrogenase & α-ketoglutarate dehydrogenase. Critical for ATP production, nerve conduction, acetylcholine synthesis.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Brain</span><span class="body-tag">Nerves</span><span class="body-tag">Heart</span><span class="body-tag">Muscles</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Energy metabolism</li><li>Nerve function</li><li>Cognitive health</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Deficiency</div><ul><li>Beriberi (dry/wet)</li><li>Wernicke-Korsakoff (alcohol)</li><li>Heart failure risk</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B2 -->
    <div class="nutr-card c-a3" style="animation-delay:.08s">
      <div class="card-header">
        <div class="card-icon">🟡</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B2 — Riboflavin</div>
          <div class="card-also">FMN · FAD (flavin coenzymes)</div>
        </div>
        <span class="card-type-badge c-a3">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1.1–1.3 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Dairy, eggs, lean meats, almonds</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Electron carrier in oxidative phosphorylation. Activates B6 and folate. Antioxidant via glutathione reductase. Mitochondrial energy production. Urine turns bright yellow when excess.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Mitochondria</span><span class="body-tag">Skin</span><span class="body-tag">Eyes</span><span class="body-tag">Mucous Membranes</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>ATP synthesis</li><li>Skin & eye health</li><li>Migraine prevention</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Deficiency</div><ul><li>Ariboflavinosis</li><li>Cracked lips (cheilosis)</li><li>Sore throat, anaemia</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B3 -->
    <div class="nutr-card c-a6" style="animation-delay:.11s">
      <div class="card-header">
        <div class="card-icon">🔥</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B3 — Niacin</div>
          <div class="card-also">NAD⁺ · NADP⁺ (critical coenzymes)</div>
        </div>
        <span class="card-type-badge c-a6">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">14–16 mg NE/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">35 mg/day (from supps)</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">NAD⁺/NADH: central to 400+ enzyme reactions. Glycolysis, TCA cycle, fatty acid synthesis, DNA repair (PARP), gene expression, cellular signalling. Pharmacological doses lower LDL cholesterol.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Every Cell</span><span class="body-tag">Liver</span><span class="body-tag">Brain</span><span class="body-tag">Skin</span><span class="body-tag">Blood Vessels</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Cellular energy core</li><li>DNA repair</li><li>Lowers LDL/triglycerides</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Pellagra (deficiency: 4 Ds)</li><li>Flushing (high dose supps)</li><li>Liver damage (excess)</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B5 -->
    <div class="nutr-card c-a1" style="animation-delay:.14s">
      <div class="card-header">
        <div class="card-icon">🌿</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B5 — Pantothenic Acid</div>
          <div class="card-also">Coenzyme A (CoA) precursor</div>
        </div>
        <span class="card-type-badge c-a1">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">5 mg/day (AI)</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Widespread — beef, potatoes, whole grains, avocado</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Forms Coenzyme A — essential for fatty acid synthesis & oxidation, steroid hormones, haem synthesis, acetylcholine, citric acid cycle. Wound healing, stress hormone production.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Adrenal Glands</span><span class="body-tag">Skin</span><span class="body-tag">Liver</span><span class="body-tag">Gut</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Stress response</li><li>Wound healing (skin)</li><li>Energy from all macros</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Deficiency very rare</li><li>High doses: GI upset</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B6 -->
    <div class="nutr-card c-a4" style="animation-delay:.17s">
      <div class="card-header">
        <div class="card-icon">🔵</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B6 — Pyridoxine</div>
          <div class="card-also">PLP (Pyridoxal 5'-phosphate) — active form</div>
        </div>
        <span class="card-type-badge c-a4">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1.3–1.7 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">100 mg/day</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Co-factor in 100+ enzyme reactions. Amino acid metabolism (transamination), neurotransmitter synthesis (dopamine, serotonin, GABA, norepinephrine), heme production, immune function, homocysteine metabolism.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Brain</span><span class="body-tag">Nerve</span><span class="body-tag">Blood (Heme)</span><span class="body-tag">Immune</span><span class="body-tag">Liver</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Mood & brain chemistry</li><li>PMS symptom relief</li><li>Cardiovascular protection</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Peripheral neuropathy (>500mg)</li><li>Deficiency: depression, anaemia</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B7 -->
    <div class="nutr-card c-a2" style="animation-delay:.2s">
      <div class="card-header">
        <div class="card-icon">💎</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B7 — Biotin</div>
          <div class="card-also">Vitamin H · Coenzyme R</div>
        </div>
        <span class="card-type-badge c-a2">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">30 µg/day (AI)</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Egg yolk, liver, nuts, sweet potato</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Carboxylase co-factor: fatty acid synthesis (ACC), gluconeogenesis (PC), amino acid catabolism, TCA cycle. Gene regulation via histone biotinylation. Hair, nail, skin keratin production.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Hair</span><span class="body-tag">Nails</span><span class="body-tag">Skin</span><span class="body-tag">Liver</span><span class="body-tag">Metabolism</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Hair & nail strengthening</li><li>Glucose metabolism</li><li>Fetal development</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Raw egg whites block absorption</li><li>Deficiency: hair loss, rashes</li><li>Skews lab test results</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B9 -->
    <div class="nutr-card c-a1" style="animation-delay:.23s">
      <div class="card-header">
        <div class="card-icon">🌱</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B9 — Folate</div>
          <div class="card-also">Folic acid (synthetic) · 5-MTHF (active)</div>
        </div>
        <span class="card-type-badge c-a1">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">400–600 µg DFE/day</div></div>
          <div class="info-box"><div class="info-box-label">Pregnancy</div><div class="info-box-val">600 µg (600–1000 µg)</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">DNA synthesis & repair (thymidine), cell division, methylation cycle (with B12), amino acid metabolism. Critical in first trimester for neural tube closure. Reduces homocysteine.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">DNA (all cells)</span><span class="body-tag">Neural Tube</span><span class="body-tag">Bone Marrow</span><span class="body-tag">Gut</span><span class="body-tag">Cardiovascular</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Prevents spina bifida</li><li>Cancer protection</li><li>Heart disease risk ↓</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Can mask B12 deficiency</li><li>Folic acid ≠ folate (MTHFR)</li><li>Deficiency: megaloblastic anaemia</li></ul></div>
        </div>
      </div>
    </div>

    <!-- B12 -->
    <div class="nutr-card c-a5" style="animation-delay:.26s">
      <div class="card-header">
        <div class="card-icon">🔴</div>
        <div class="card-meta">
          <div class="card-name">Vitamin B12 — Cobalamin</div>
          <div class="card-also">Methylcobalamin · Adenosylcobalamin · Cyanocobalamin</div>
        </div>
        <span class="card-type-badge c-a5">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">2.4 µg/day</div></div>
          <div class="info-box"><div class="info-box-label">Stored</div><div class="info-box-val">Liver — years supply</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Myelin sheath synthesis (nerve insulation), methionine synthesis (methylation), RBC maturation with folate, DNA synthesis, mitochondrial fatty acid metabolism. Only from animal/microbial sources.</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Nerves (Myelin)</span><span class="body-tag">Brain</span><span class="body-tag">Spinal Cord</span><span class="body-tag">Bone Marrow</span><span class="body-tag">DNA</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Nerve protection</li><li>Energy & memory</li><li>Mood regulation</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Vegans at HIGH risk</li><li>Pernicious anaemia</li><li>Irreversible nerve damage</li><li>Requires intrinsic factor</li></ul></div>
        </div>
      </div>
    </div>

    <!-- VITAMIN C -->
    <div class="nutr-card c-a6" style="animation-delay:.29s">
      <div class="card-header">
        <div class="card-icon">🍊</div>
        <div class="card-meta">
          <div class="card-name">Vitamin C — Ascorbic Acid</div>
          <div class="card-also">L-Ascorbate · Dehydroascorbate (oxidised)</div>
        </div>
        <span class="card-type-badge c-a6">Water-Soluble</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">75–90 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">2,000 mg/day</div></div>
        </div>
        <div class="info-full">
          <div class="info-box-label">What It Does</div>
          <div class="info-box-val">Collagen hydroxylation (essential for structure), potent antioxidant, iron absorption enhancer, immune stimulant (NK cells, neutrophils), carnitine synthesis, neurotransmitter synthesis (norepinephrine).</div>
        </div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Skin (Collagen)</span><span class="body-tag">Blood Vessels</span><span class="body-tag">Immune</span><span class="body-tag">Joints</span><span class="body-tag">Gums</span><span class="body-tag">Brain</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Immune system boost</li><li>Wound healing</li><li>Collagen synthesis</li><li>Anti-oxidant protection</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Scurvy (classic deficiency)</li><li>Kidney stones (mega-dose)</li><li>GI distress (>1g/day)</li></ul></div>
        </div>
      </div>
    </div>

  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ MACROMINERALS ═══════════════════════════════ -->
<section class="section" id="macrominerals">
  <div class="section-header">
    <span class="section-number">03</span>
    <h2 class="section-title">Macro<span class="section-accent">minerals</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Required in amounts >100 mg/day. Structural and electrolyte roles. Essential for every organ system.</p>

  <div class="cards-grid">

    <!-- CALCIUM -->
    <div class="nutr-card c-a3" style="animation-delay:.05s">
      <div class="card-header">
        <div class="card-icon">🦴</div>
        <div class="card-meta">
          <div class="card-name">Calcium (Ca)</div>
          <div class="card-also">Most abundant mineral in body — 99% in bones/teeth</div>
        </div>
        <span class="card-type-badge c-a3">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1,000–1,200 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">2,000–2,500 mg/day</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Bone & tooth mineralisation, muscle contraction (troponin), nerve signal transmission, blood clotting cascade, enzyme activation, cell signalling (second messenger). Regulated by PTH & Vit D.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Bones (99%)</span><span class="body-tag">Muscles</span><span class="body-tag">Heart</span><span class="body-tag">Nerves</span><span class="body-tag">Blood</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-yellow">Dairy (milk, cheese)</span><span class="pill pill-green">Kale</span><span class="pill pill-green">Bok choy</span><span class="pill pill-blue">Sardines (bones)</span><span class="pill pill-green">Tofu</span><span class="pill pill-green">Almonds</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Prevents osteoporosis</li><li>Muscle & heart function</li><li>Blood pressure regulation</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Excess → hypercalcaemia</li><li>Competes with Mg, Zn, Fe</li><li>Deficiency: osteopenia</li></ul></div>
        </div>
      </div>
    </div>

    <!-- MAGNESIUM -->
    <div class="nutr-card c-a1" style="animation-delay:.1s">
      <div class="card-header">
        <div class="card-icon">⚡</div>
        <div class="card-meta">
          <div class="card-name">Magnesium (Mg)</div>
          <div class="card-also">Co-factor in 300+ enzymatic reactions</div>
        </div>
        <span class="card-type-badge c-a1">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">310–420 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">UL (supps)</div><div class="info-box-val">350 mg/day</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">ATP synthesis (Mg-ATP complex), DNA/RNA synthesis, protein synthesis, nerve impulse, muscle relaxation (Ca antagonist), blood glucose & pressure control, bone structure, sleep (GABA activation).</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Mitochondria</span><span class="body-tag">Muscles</span><span class="body-tag">Brain</span><span class="body-tag">Heart</span><span class="body-tag">Bones</span><span class="body-tag">Kidneys</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-green">Pumpkin seeds</span><span class="pill pill-green">Dark chocolate</span><span class="pill pill-green">Spinach</span><span class="pill pill-yellow">Almonds</span><span class="pill pill-green">Black beans</span><span class="pill pill-yellow">Avocado</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Sleep quality</li><li>Anxiety & stress ↓</li><li>Migraine prevention</li><li>Athletic recovery</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>56% adults deficient</li><li>Diarrhoea (excess supps)</li><li>Depleted by alcohol/stress</li></ul></div>
        </div>
      </div>
    </div>

    <!-- PHOSPHORUS -->
    <div class="nutr-card c-a5" style="animation-delay:.15s">
      <div class="card-header">
        <div class="card-icon">🔬</div>
        <div class="card-meta">
          <div class="card-name">Phosphorus (P)</div>
          <div class="card-also">2nd most abundant mineral — phosphate (PO₄³⁻)</div>
        </div>
        <span class="card-type-badge c-a5">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">700 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Meat, dairy, fish, nuts, legumes</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Backbone of DNA/RNA (phosphodiester bonds), ATP energy currency, bone hydroxyapatite (85%), phospholipid membranes, acid-base buffer, cell signalling (phosphorylation cascades).</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Bones/Teeth (85%)</span><span class="body-tag">DNA</span><span class="body-tag">Cell Membranes</span><span class="body-tag">Kidneys</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Energy (ATP)</li><li>Bone strength</li><li>Cell membrane integrity</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Deficiency rare (excess common)</li><li>High P blocks Ca absorption</li><li>Kidney disease risk</li></ul></div>
        </div>
      </div>
    </div>

    <!-- POTASSIUM -->
    <div class="nutr-card c-a4" style="animation-delay:.2s">
      <div class="card-header">
        <div class="card-icon">💜</div>
        <div class="card-meta">
          <div class="card-name">Potassium (K)</div>
          <div class="card-also">Principal intracellular cation (K⁺)</div>
        </div>
        <span class="card-type-badge c-a4">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">2,600–3,400 mg/day</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Banana, potato, leafy greens</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Na/K-ATPase pump (maintains cell voltage), nerve action potentials, muscle contraction (including heart), blood pressure regulation (Na antagonist), acid-base balance, kidney function.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Heart (critical)</span><span class="body-tag">Kidneys</span><span class="body-tag">Muscles</span><span class="body-tag">Nerves</span><span class="body-tag">Blood Pressure</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Blood pressure control</li><li>Stroke risk ↓</li><li>Muscle cramp prevention</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Hypokalaemia → arrhythmia</li><li>Hyperkalaemia (kidney disease)</li><li>Diuretics deplete K</li></ul></div>
        </div>
      </div>
    </div>

    <!-- SODIUM -->
    <div class="nutr-card c-a2" style="animation-delay:.25s">
      <div class="card-header">
        <div class="card-icon">🧂</div>
        <div class="card-meta">
          <div class="card-name">Sodium (Na)</div>
          <div class="card-also">Principal extracellular cation (Na⁺)</div>
        </div>
        <span class="card-type-badge c-a2">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1,500 mg/day (AI)</div></div>
          <div class="info-box"><div class="info-box-label">UL (chronic)</div><div class="info-box-val">&lt;2,300 mg/day</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Fluid balance & osmotic pressure, nerve action potentials, nutrient absorption (Na-glucose co-transport), blood volume regulation, maintains ECF volume.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Blood Vessels</span><span class="body-tag">Kidneys</span><span class="body-tag">Nerves</span><span class="body-tag">All Cells (ECF)</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Hydration balance</li><li>Nerve transmission</li><li>Nutrient absorption</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Hypertension (excess)</li><li>Kidney & heart disease</li><li>Western diet: 3,400 mg avg</li></ul></div>
        </div>
      </div>
    </div>

    <!-- SULFUR -->
    <div class="nutr-card c-a3" style="animation-delay:.3s">
      <div class="card-header">
        <div class="card-icon">🟡</div>
        <div class="card-meta">
          <div class="card-name">Sulfur (S)</div>
          <div class="card-also">Cysteine · Methionine · Glutathione</div>
        </div>
        <span class="card-type-badge c-a3">Macromineral</span>
      </div>
      <div class="card-body">
        <div class="info-row">
          <div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">No RDA (via protein)</div></div>
          <div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Meat, eggs, garlic, cruciferous veg</div></div>
        </div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Disulfide bonds in protein structure (keratin, insulin), glutathione antioxidant system, liver detoxification (Phase II), collagen & cartilage (chondroitin sulfate), taurine synthesis.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Skin/Hair/Nails</span><span class="body-tag">Liver</span><span class="body-tag">Joints</span><span class="body-tag">All Proteins</span></div></div>
        <div class="pro-con">
          <div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Master antioxidant (GSH)</li><li>Detoxification support</li><li>Joint health</li></ul></div>
          <div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Rarely deficient</li><li>High-sulfur foods: gas/bloating</li></ul></div>
        </div>
      </div>
    </div>

  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ TRACE MINERALS ═══════════════════════════════ -->
<section class="section" id="traceminerals">
  <div class="section-header">
    <span class="section-number">04</span>
    <h2 class="section-title">Trace <span class="section-accent">Minerals</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Required in microgram to low-milligram quantities. Enzymatic catalysts, hormonal regulators, and structural cofactors with outsized physiological impact.</p>

  <div class="cards-grid">

    <!-- IRON -->
    <div class="nutr-card c-a2" style="animation-delay:.05s">
      <div class="card-header"><div class="card-icon">🔴</div><div class="card-meta"><div class="card-name">Iron (Fe)</div><div class="card-also">Heme-Fe (animal) · Non-heme Fe (plant) — very different absorption</div></div><span class="card-type-badge c-a2">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">8–18 mg/day (women higher)</div></div><div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">45 mg/day</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Haemoglobin oxygen transport, myoglobin in muscle, cytochrome enzymes (mitochondrial ETC), DNA synthesis, immune cell proliferation, neurotransmitter synthesis (dopamine, serotonin). Absorption enhanced by Vit C.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Blood (Hb)</span><span class="body-tag">Muscles</span><span class="body-tag">Mitochondria</span><span class="body-tag">Brain</span><span class="body-tag">Immune</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-red">Red meat (heme)</span><span class="pill pill-red">Liver</span><span class="pill pill-green">Lentils</span><span class="pill pill-green">Spinach</span><span class="pill pill-green">Tofu</span><span class="pill pill-yellow">Pumpkin seeds</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Oxygen delivery</li><li>Energy & cognition</li><li>Immune response</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Iron overload (hereditary)</li><li>Most common deficiency globally</li><li>Iron-deficiency anaemia</li></ul></div></div>
      </div>
    </div>

    <!-- ZINC -->
    <div class="nutr-card c-a5" style="animation-delay:.1s">
      <div class="card-header"><div class="card-icon">🔵</div><div class="card-meta"><div class="card-name">Zinc (Zn)</div><div class="card-also">Co-factor in 300+ enzymes · structural Zn-finger proteins</div></div><span class="card-type-badge c-a5">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">8–11 mg/day</div></div><div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">40 mg/day</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Immune cell development & function (T-cells, NK cells), wound healing, DNA binding (zinc fingers), testosterone synthesis, taste & smell, protein digestion (carboxypeptidase), SOD antioxidant enzyme.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Immune</span><span class="body-tag">Skin</span><span class="body-tag">Testes</span><span class="body-tag">Brain</span><span class="body-tag">Eyes</span><span class="body-tag">Gut</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-blue">Oysters (highest)</span><span class="pill pill-red">Beef</span><span class="pill pill-yellow">Pumpkin seeds</span><span class="pill pill-yellow">Hemp seeds</span><span class="pill pill-green">Lentils</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Cold duration ↓</li><li>Skin healing</li><li>Male fertility</li><li>Anti-inflammatory</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Excess blocks copper</li><li>Phytates in plants block absorption</li><li>Deficiency: growth stunting</li></ul></div></div>
      </div>
    </div>

    <!-- IODINE -->
    <div class="nutr-card c-a4" style="animation-delay:.15s">
      <div class="card-header"><div class="card-icon">🦋</div><div class="card-meta"><div class="card-name">Iodine (I)</div><div class="card-also">Thyroid hormones T3 & T4 — must have iodine</div></div><span class="card-type-badge c-a4">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">150 µg/day (220 pregnant)</div></div><div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">1,100 µg/day</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Thyroid hormone synthesis (T3/T4) — regulates basal metabolic rate, thermoregulation, protein synthesis, brain development in fetus & infant. Thyroid peroxidase requires iodine for oxidative coupling.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Thyroid</span><span class="body-tag">Brain</span><span class="body-tag">Metabolism (all cells)</span><span class="body-tag">Fetal Development</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-blue">Seaweed (nori, kelp)</span><span class="pill pill-blue">Fish/shrimp</span><span class="pill pill-yellow">Dairy</span><span class="pill pill-yellow">Iodised salt</span><span class="pill pill-yellow">Eggs</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Thyroid/metabolic health</li><li>Brain IQ (fetal)</li><li>Energy regulation</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Goitre (deficiency)</li><li>Cretinism (fetal)</li><li>Both deficiency & excess → dysfunction</li></ul></div></div>
      </div>
    </div>

    <!-- SELENIUM -->
    <div class="nutr-card c-a1" style="animation-delay:.2s">
      <div class="card-header"><div class="card-icon">🌟</div><div class="card-meta"><div class="card-name">Selenium (Se)</div><div class="card-also">Selenoproteins (25 known) · Glutathione peroxidase</div></div><span class="card-type-badge c-a1">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">55 µg/day</div></div><div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">400 µg/day</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Antioxidant enzyme (GPx), thyroid hormone conversion (T4→T3), DNA damage repair, immune function, male fertility (sperm motility). Brazil nuts: 1 nut = 70–90 µg selenium.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Thyroid</span><span class="body-tag">Testes</span><span class="body-tag">Immune</span><span class="body-tag">Liver</span><span class="body-tag">DNA</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-yellow">Brazil nuts (1–2/day)</span><span class="pill pill-blue">Tuna</span><span class="pill pill-blue">Sardines</span><span class="pill pill-red">Beef</span><span class="pill pill-yellow">Eggs</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Cancer risk ↓</li><li>Thyroid support</li><li>Male fertility</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Selenosis (toxicity): hair loss</li><li>Narrow therapeutic window</li><li>Keshan disease (deficiency)</li></ul></div></div>
      </div>
    </div>

    <!-- COPPER -->
    <div class="nutr-card c-a6" style="animation-delay:.25s">
      <div class="card-header"><div class="card-icon">🟤</div><div class="card-meta"><div class="card-name">Copper (Cu)</div><div class="card-also">Ceruloplasmin · SOD enzyme · Ferroxidase</div></div><span class="card-type-badge c-a6">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">900 µg/day</div></div><div class="info-box"><div class="info-box-label">UL</div><div class="info-box-val">10,000 µg/day</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Iron metabolism (ceruloplasmin oxidises Fe²⁺ → Fe³⁺), connective tissue (lysyl oxidase cross-links collagen/elastin), myelin synthesis, melanin production, neurotransmitter synthesis, superoxide dismutase.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Blood Vessels</span><span class="body-tag">Brain</span><span class="body-tag">Skin</span><span class="body-tag">Connective Tissue</span><span class="body-tag">Liver</span></div></div>
        <div class="info-full"><div class="info-box-label">Natural Sources</div><div class="pill-list"><span class="pill pill-red">Beef liver</span><span class="pill pill-blue">Oysters</span><span class="pill pill-green">Dark chocolate</span><span class="pill pill-yellow">Cashews</span><span class="pill pill-green">Shiitake mushrooms</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Cardiovascular health</li><li>Brain function</li><li>Collagen & skin</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Wilson's disease (genetic Cu accumulation)</li><li>Excess Zn depletes Cu</li><li>Deficiency: anaemia, nerve damage</li></ul></div></div>
      </div>
    </div>

    <!-- MANGANESE -->
    <div class="nutr-card c-a3" style="animation-delay:.3s">
      <div class="card-header"><div class="card-icon">🌾</div><div class="card-meta"><div class="card-name">Manganese (Mn)</div><div class="card-also">MnSOD · Arginase · Pyruvate carboxylase</div></div><span class="card-type-badge c-a3">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">1.8–2.3 mg/day</div></div><div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Whole grains, legumes, nuts, tea</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Mitochondrial antioxidant (MnSOD), bone formation (glycosaminoglycan synthesis), carbohydrate & amino acid metabolism, wound healing, nerve function, blood clotting.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Mitochondria</span><span class="body-tag">Bones</span><span class="body-tag">Brain</span><span class="body-tag">Liver</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Bone density</li><li>Blood sugar control</li><li>Antioxidant defence</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Excess: neurotoxic (Manganism)</li><li>Looks like Parkinson's</li></ul></div></div>
      </div>
    </div>

    <!-- CHROMIUM -->
    <div class="nutr-card c-a4" style="animation-delay:.35s">
      <div class="card-header"><div class="card-icon">💡</div><div class="card-meta"><div class="card-name">Chromium (Cr)</div><div class="card-also">Chromodulin · Insulin potentiator</div></div><span class="card-type-badge c-a4">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">25–35 µg/day (AI)</div></div><div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Broccoli, grape juice, whole grains</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Enhances insulin receptor signalling (via chromodulin), improves glucose uptake, lipid metabolism. Limited evidence, but clinically used in Type 2 diabetes support. Debated mechanism.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Pancreas</span><span class="body-tag">Muscle (glucose)</span><span class="body-tag">Liver</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Blood sugar regulation</li><li>Insulin sensitivity</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Evidence still debated</li><li>Deficiency signs subtle</li></ul></div></div>
      </div>
    </div>

    <!-- FLUORIDE -->
    <div class="nutr-card c-a5" style="animation-delay:.4s">
      <div class="card-header"><div class="card-icon">🦷</div><div class="card-meta"><div class="card-name">Fluoride (F)</div><div class="card-also">Fluorapatite in enamel</div></div><span class="card-type-badge c-a5">Trace Mineral</span></div>
      <div class="card-body">
        <div class="info-row"><div class="info-box"><div class="info-box-label">Daily Need</div><div class="info-box-val">3–4 mg/day (AI)</div></div><div class="info-box"><div class="info-box-label">Found In</div><div class="info-box-val">Fluoridated water, tea, toothpaste</div></div></div>
        <div class="info-full"><div class="info-box-label">What It Does</div><div class="info-box-val">Incorporates into enamel as fluorapatite — more acid-resistant than hydroxyapatite. Inhibits dental caries bacteria (blocks enolase). Bone mineralisation support.</div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Teeth</span><span class="body-tag">Bones</span></div></div>
        <div class="pro-con"><div class="pro-con-box pros"><div class="pro-con-title">Benefits</div><ul><li>Cavity prevention</li><li>Enamel strength</li></ul></div><div class="pro-con-box cons"><div class="pro-con-title">Issues</div><ul><li>Fluorosis (mottled enamel)</li><li>Skeletal fluorosis (excess)</li></ul></div></div>
      </div>
    </div>

  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ MACRONUTRIENTS ═══════════════════════════════ -->
<section class="section" id="macronutrients">
  <div class="section-header">
    <span class="section-number">05</span>
    <h2 class="section-title">Macro<span class="section-accent">nutrients</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Energy-providing nutrients. Required in large amounts (grams). Foundation of every diet and metabolic process.</p>

  <div class="macro-table-wrap">
    <table class="macro-table">
      <thead>
        <tr>
          <th>Macronutrient</th>
          <th>Cal/g</th>
          <th>RDA / Recommendation</th>
          <th>Key Functions</th>
          <th>Best Sources</th>
          <th>Excess Effect</th>
          <th>Deficiency Effect</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td style="color:#fff;font-weight:700;">Carbohydrates<br><span style="font-size:10px;color:var(--accent3);">Simple | Complex | Fibre</span></td>
          <td><span style="color:var(--accent3);font-weight:700;">4</span></td>
          <td>45–65% of calories<br>~130g/day (brain minimum)<br>Fibre: 25–38g/day</td>
          <td>Primary energy source (glucose → ATP via glycolysis/TCA), brain fuel (sole fuel for RBCs), glycogen stores (muscle/liver), protein sparing, gut microbiome (fibre)</td>
          <td>Whole grains, legumes, fruits, vegetables, oats, brown rice, sweet potato</td>
          <td>Weight gain, insulin resistance, metabolic syndrome, T2DM, dental caries</td>
          <td>Ketosis, muscle catabolism (gluconeogenesis from protein), fatigue, brain fog</td>
        </tr>
        <tr>
          <td style="color:#fff;font-weight:700;">Proteins<br><span style="font-size:10px;color:var(--accent2);">Complete | Incomplete | BCAA</span></td>
          <td><span style="color:var(--accent2);font-weight:700;">4</span></td>
          <td>0.8 g/kg/day (sedentary)<br>1.6–2.2 g/kg/day (athletes)<br>10–35% of calories</td>
          <td>Tissue synthesis & repair (muscle, organs), enzymes, hormones (insulin, GH), antibodies, transport (Hb, albumin), acid-base buffer, energy (last resort)</td>
          <td>Eggs, meat, fish, dairy, legumes, tofu, tempeh, quinoa, Greek yoghurt</td>
          <td>Kidney strain (pre-existing disease), high saturated fat intake (if from red meat), nitrogen load</td>
          <td>Muscle wasting (sarcopenia), immune suppression, oedema, growth failure, poor wound healing</td>
        </tr>
        <tr>
          <td style="color:#fff;font-weight:700;">Fats<br><span style="font-size:10px;color:var(--accent4);">Saturated | MUFA | PUFA | Trans</span></td>
          <td><span style="color:var(--accent4);font-weight:700;">9</span></td>
          <td>20–35% of calories<br>Saturated &lt;10%<br>Omega-3: 1.1–1.6g/day ALA</td>
          <td>Cell membrane structure (phospholipids), fat-soluble vitamin absorption (A/D/E/K), hormone synthesis (steroid hormones), myelin sheath, brain (60% fat), thermal insulation, energy reserve</td>
          <td>Avocado, olive oil, nuts, fatty fish (salmon), eggs, coconut oil, flaxseed, walnuts</td>
          <td>Obesity, cardiovascular disease (saturated/trans fats), inflammation (omega-6 excess)</td>
          <td>Deficiency of fat-soluble vitamins, hormonal dysfunction, brain impairment, dry skin</td>
        </tr>
        <tr>
          <td style="color:#fff;font-weight:700;">Omega-3 FA<br><span style="font-size:10px;color:var(--accent5);">ALA · EPA · DHA</span></td>
          <td><span style="color:var(--accent5);font-weight:700;">9</span></td>
          <td>EPA+DHA: 250–500 mg/day<br>ALA: 1.1–1.6g/day</td>
          <td>Anti-inflammatory (resolvins, protectins), brain DHA structure, retina, heart rhythm, blood pressure ↓, triglycerides ↓, fetal brain development</td>
          <td>Salmon, mackerel, herring, sardines, flaxseed, chia seeds, walnuts, algae oil</td>
          <td>Blood thinning (very high dose), GI issues</td>
          <td>Inflammation, cardiovascular risk, depression, poor brain development</td>
        </tr>
        <tr>
          <td style="color:#fff;font-weight:700;">Dietary Fibre<br><span style="font-size:10px;color:var(--accent1);">Soluble | Insoluble | Prebiotic</span></td>
          <td><span style="color:var(--accent1);font-weight:700;">~2</span></td>
          <td>25g/day (women)<br>38g/day (men)</td>
          <td>Soluble: lowers LDL (bile acid binding), glucose buffering, feeds microbiome. Insoluble: bowel regularity, colon cancer prevention. Prebiotic: produces SCFAs (butyrate = colon health)</td>
          <td>Oats, beans, lentils, flaxseed, apples, whole wheat, broccoli, berries, psyllium</td>
          <td>Bloating, gas, reduced mineral absorption (very high intake)</td>
          <td>Constipation, dysbiosis, colon cancer risk, blood sugar spikes</td>
        </tr>
      </tbody>
    </table>
  </div>

  <!-- Essential Amino Acids -->
  <div style="margin-top:3rem;">
    <h3 style="font-family:var(--sans);font-size:1.2rem;color:#fff;margin-bottom:1rem;">Essential Amino Acids <span style="font-size:12px;color:var(--text3);font-family:var(--mono);">(must obtain from diet)</span></h3>
    <div style="display:flex;flex-wrap:wrap;gap:.5rem;">
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Histidine</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Isoleucine (BCAA)</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Leucine (BCAA)</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Valine (BCAA)</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Lysine</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Methionine</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Phenylalanine</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Threonine</span>
      <span class="pill pill-purple" style="font-size:11px;padding:.3rem .8rem;">Tryptophan</span>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ PHYTONUTRIENTS ═══════════════════════════════ -->
<section class="section" id="phyto">
  <div class="section-header">
    <span class="section-number">06</span>
    <h2 class="section-title">Phyto<span class="section-accent">nutrients</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Plant-derived bioactive compounds. Not "essential" (no deficiency disease), but profoundly protective. 25,000+ identified. Eat the rainbow.</p>

  <div class="cards-grid">
    <div class="nutr-card c-a4" style="animation-delay:.05s">
      <div class="card-header"><div class="card-icon">🫐</div><div class="card-meta"><div class="card-name">Flavonoids</div><div class="card-also">Anthocyanins · Quercetin · Catechins · Resveratrol</div></div><span class="card-type-badge c-a4">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Potent antioxidant, anti-inflammatory, estrogenic activity modulation, cardiovascular protection, neuroprotection, anti-cancer (apoptosis induction), gut microbiome support. Quercetin is a natural antihistamine.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-purple">Blueberries</span><span class="pill pill-purple">Red wine</span><span class="pill pill-green">Green tea (EGCG)</span><span class="pill pill-purple">Dark chocolate</span><span class="pill pill-green">Apples</span><span class="pill pill-red">Onions</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Heart</span><span class="body-tag">Brain</span><span class="body-tag">DNA</span><span class="body-tag">Immune</span><span class="body-tag">Gut</span></div></div>
      </div>
    </div>

    <div class="nutr-card c-a6" style="animation-delay:.1s">
      <div class="card-header"><div class="card-icon">🍅</div><div class="card-meta"><div class="card-name">Carotenoids</div><div class="card-also">Lycopene · Lutein · Zeaxanthin · β-Carotene</div></div><span class="card-type-badge c-a6">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Lycopene: prostate & skin cancer protection. Lutein + Zeaxanthin: macula pigment density — prevents macular degeneration & cataracts. β-Carotene: Vit A precursor. All are powerful antioxidants in lipid environments.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-red">Tomatoes (lycopene)</span><span class="pill pill-orange">Carrots</span><span class="pill pill-green">Kale</span><span class="pill pill-orange">Pumpkin</span><span class="pill pill-green">Spinach</span><span class="pill pill-yellow">Corn</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Eyes (Macula)</span><span class="body-tag">Prostate</span><span class="body-tag">Skin</span><span class="body-tag">Lungs</span></div></div>
      </div>
    </div>

    <div class="nutr-card c-a1" style="animation-delay:.15s">
      <div class="card-header"><div class="card-icon">🥦</div><div class="card-meta"><div class="card-name">Glucosinolates</div><div class="card-also">Sulforaphane · Indole-3-carbinol</div></div><span class="card-type-badge c-a1">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Sulforaphane: activates Nrf2 pathway → upregulates 200+ antioxidant & detox genes. Induces Phase II liver enzymes. Anti-cancer (breast, prostate, colon). Indole-3-carbinol: estrogen metabolism. H. pylori inhibition.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-green">Broccoli sprouts (highest)</span><span class="pill pill-green">Kale</span><span class="pill pill-green">Cabbage</span><span class="pill pill-green">Brussels sprouts</span><span class="pill pill-green">Cauliflower</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Liver</span><span class="body-tag">DNA</span><span class="body-tag">Gut</span><span class="body-tag">Brain</span></div></div>
      </div>
    </div>

    <div class="nutr-card c-a3" style="animation-delay:.2s">
      <div class="card-header"><div class="card-icon">🧄</div><div class="card-meta"><div class="card-name">Organosulfurs</div><div class="card-also">Allicin · Diallyl disulfide · S-allylcysteine</div></div><span class="card-type-badge c-a3">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Allicin (from crushed garlic): antimicrobial, anti-platelet, cardiovascular. Lowers LDL & blood pressure. Anti-cancer properties. Immune stimulant. Hepatoprotective. Synergy with quercetin.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-yellow">Garlic</span><span class="pill pill-yellow">Onions</span><span class="pill pill-green">Leeks</span><span class="pill pill-green">Chives</span><span class="pill pill-green">Shallots</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Heart</span><span class="body-tag">Blood Vessels</span><span class="body-tag">Immune</span><span class="body-tag">Liver</span></div></div>
      </div>
    </div>

    <div class="nutr-card c-a5" style="animation-delay:.25s">
      <div class="card-header"><div class="card-icon">🫚</div><div class="card-meta"><div class="card-name">Polyphenols</div><div class="card-also">Curcumin · Resveratrol · Ellagic acid · Lignans</div></div><span class="card-type-badge c-a5">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Curcumin: inhibits NF-κB (master inflammation switch), activates AMPK, crosses blood-brain barrier. Resveratrol: SIRT1 activator (longevity pathway), cardiovascular. Ellagic acid: anti-carcinogenic, gut health.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-yellow">Turmeric (curcumin)</span><span class="pill pill-purple">Red grapes</span><span class="pill pill-red">Pomegranate</span><span class="pill pill-orange">Flaxseed</span><span class="pill pill-green">Olive oil (EVOO)</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Brain</span><span class="body-tag">Joints</span><span class="body-tag">Gut</span><span class="body-tag">Heart</span><span class="body-tag">DNA</span></div></div>
      </div>
    </div>

    <div class="nutr-card c-a2" style="animation-delay:.3s">
      <div class="card-header"><div class="card-icon">🌾</div><div class="card-meta"><div class="card-name">Phytosterols</div><div class="card-also">β-Sitosterol · Campesterol · Stigmasterol</div></div><span class="card-type-badge c-a2">Phytonutrient</span></div>
      <div class="card-body">
        <div class="info-full"><div class="info-box-label">What They Do</div><div class="info-box-val">Structurally similar to cholesterol — compete for absorption in gut. Reduce LDL cholesterol by 10–15%. Prostate health (BPH: β-sitosterol). Immune modulation. Added to fortified margarine/OJ for cardiovascular benefit.</div></div>
        <div class="info-full"><div class="info-box-label">Sources</div><div class="pill-list"><span class="pill pill-yellow">Nuts & seeds</span><span class="pill pill-orange">Wheat germ</span><span class="pill pill-green">Avocado</span><span class="pill pill-green">Broccoli</span><span class="pill pill-yellow">Fortified foods</span></div></div>
        <div class="info-full"><div class="info-box-label">Body Targets</div><div class="body-bar"><span class="body-tag">Gut (cholesterol)</span><span class="body-tag">Liver</span><span class="body-tag">Heart</span><span class="body-tag">Prostate</span></div></div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ WATER & ELECTROLYTES ═══════════════════════════════ -->
<section class="section" id="water">
  <div class="section-header">
    <span class="section-number">07</span>
    <h2 class="section-title">Water & <span class="section-accent">Electrolytes</span></h2>
  </div>

  <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:1.5rem;margin-bottom:2rem;">
    <div class="body-section" style="margin-bottom:0;">
      <h3 style="font-family:var(--sans);font-size:1.1rem;color:var(--accent5);margin-bottom:1rem;">💧 Water — The Universal Solvent</h3>
      <ul style="list-style:none;color:var(--text2);font-size:12px;line-height:2;">
        <li><span style="color:var(--accent1);">›</span> Body composition: 60% of body weight (brain: 75%, blood: 90%)</li>
        <li><span style="color:var(--accent1);">›</span> Solvent for biochemical reactions</li>
        <li><span style="color:var(--accent1);">›</span> Thermoregulation (sweat, vasodilation)</li>
        <li><span style="color:var(--accent1);">›</span> Nutrient transport & waste removal</li>
        <li><span style="color:var(--accent1);">›</span> Joint lubrication (synovial fluid)</li>
        <li><span style="color:var(--accent1);">›</span> Blood volume & blood pressure</li>
        <li><span style="color:var(--accent1);">›</span> Need: ~2–3.7 L/day (varies by activity, climate)</li>
        <li><span style="color:var(--accent2);">›</span> 1–2% dehydration → 10–20% performance drop</li>
        <li><span style="color:var(--accent2);">›</span> Hyponatraemia (overhydration) is also dangerous</li>
      </ul>
    </div>
    <div class="body-section" style="margin-bottom:0;">
      <h3 style="font-family:var(--sans);font-size:1.1rem;color:var(--accent3);margin-bottom:1rem;">⚡ Electrolytes — The Charge Carriers</h3>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:.5rem;">
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--accent3);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Sodium (Na⁺)</div>
          <div style="font-size:11px;color:var(--text2);">ECF volume, nerve impulse initiation, water balance</div>
        </div>
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--accent4);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Potassium (K⁺)</div>
          <div style="font-size:11px;color:var(--text2);">ICF balance, heart rhythm, muscle contraction</div>
        </div>
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--accent5);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Chloride (Cl⁻)</div>
          <div style="font-size:11px;color:var(--text2);">Follows Na⁺, stomach acid (HCl), acid-base buffer</div>
        </div>
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--accent1);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Magnesium (Mg²⁺)</div>
          <div style="font-size:11px;color:var(--text2);">Muscle relaxation, 300+ enzymes, ATP stability</div>
        </div>
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--accent6);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Calcium (Ca²⁺)</div>
          <div style="font-size:11px;color:var(--text2);">Muscle contraction, nerve signal, blood clotting</div>
        </div>
        <div style="background:rgba(255,255,255,.03);border-radius:.4rem;padding:.6rem;border:1px solid rgba(255,255,255,.06);">
          <div style="font-size:10px;color:var(--text2);letter-spacing:.1em;text-transform:uppercase;margin-bottom:.3rem;">Bicarbonate (HCO₃⁻)</div>
          <div style="font-size:11px;color:var(--text2);">Primary blood pH buffer, CO₂ transport</div>
        </div>
      </div>
    </div>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ BODY MAP ═══════════════════════════════ -->
<section class="section" id="body-map">
  <div class="section-header">
    <span class="section-number">08</span>
    <h2 class="section-title">Body <span class="section-accent">Impact Map</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Where each organ system relies on specific nutrients most critically.</p>

  <div class="body-section">
    <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:1rem;">
      <div style="background:rgba(255,107,107,.05);border:1px solid rgba(255,107,107,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🧠</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent2);margin-bottom:.5rem;">Brain & Nervous System</div>
        <div class="pill-list"><span class="pill pill-blue">B1 (Thiamine)</span><span class="pill pill-blue">B6</span><span class="pill pill-blue">B12 (Myelin)</span><span class="pill pill-blue">Folate</span><span class="pill pill-purple">Omega-3 DHA</span><span class="pill pill-yellow">Iodine</span><span class="pill pill-orange">Zinc</span><span class="pill pill-green">Vit D</span><span class="pill pill-orange">Iron</span><span class="pill pill-green">Magnesium</span></div>
      </div>
      <div style="background:rgba(255,209,102,.05);border:1px solid rgba(255,209,102,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">❤️</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent3);margin-bottom:.5rem;">Heart & Cardiovascular</div>
        <div class="pill-list"><span class="pill pill-purple">Potassium</span><span class="pill pill-green">Magnesium</span><span class="pill pill-yellow">Vit D</span><span class="pill pill-purple">Vit K2</span><span class="pill pill-blue">Omega-3 EPA</span><span class="pill pill-green">CoQ10*</span><span class="pill pill-orange">Niacin (B3)</span><span class="pill pill-green">Vit C</span><span class="pill pill-red">Iron</span></div>
      </div>
      <div style="background:rgba(0,212,170,.05);border:1px solid rgba(0,212,170,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🦴</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent1);margin-bottom:.5rem;">Bone & Skeletal</div>
        <div class="pill-list"><span class="pill pill-yellow">Calcium</span><span class="pill pill-yellow">Vit D</span><span class="pill pill-purple">Vit K2</span><span class="pill pill-green">Magnesium</span><span class="pill pill-blue">Phosphorus</span><span class="pill pill-orange">Manganese</span><span class="pill pill-orange">Copper</span><span class="pill pill-blue">Protein</span><span class="pill pill-green">Fluoride</span></div>
      </div>
      <div style="background:rgba(56,189,248,.05);border:1px solid rgba(56,189,248,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🛡️</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent5);margin-bottom:.5rem;">Immune System</div>
        <div class="pill-list"><span class="pill pill-orange">Vit C</span><span class="pill pill-yellow">Vit D</span><span class="pill pill-orange">Zinc</span><span class="pill pill-orange">Vit A</span><span class="pill pill-green">Selenium</span><span class="pill pill-red">Iron</span><span class="pill pill-blue">Folate</span><span class="pill pill-blue">B6</span><span class="pill pill-green">Omega-3</span></div>
      </div>
      <div style="background:rgba(167,139,250,.05);border:1px solid rgba(167,139,250,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">💪</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent4);margin-bottom:.5rem;">Muscles</div>
        <div class="pill-list"><span class="pill pill-yellow">Calcium</span><span class="pill pill-green">Magnesium</span><span class="pill pill-purple">Potassium</span><span class="pill pill-blue">Protein (AA)</span><span class="pill pill-yellow">Vit D</span><span class="pill pill-blue">B1, B2, B3</span><span class="pill pill-orange">Iron (myoglobin)</span><span class="pill pill-green">Creatine*</span></div>
      </div>
      <div style="background:rgba(251,146,60,.05);border:1px solid rgba(251,146,60,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🫀</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent6);margin-bottom:.5rem;">Liver & Detoxification</div>
        <div class="pill-list"><span class="pill pill-green">Vit C</span><span class="pill pill-orange">B vitamins</span><span class="pill pill-green">Selenium</span><span class="pill pill-green">Sulfur (GSH)</span><span class="pill pill-yellow">Zinc</span><span class="pill pill-orange">Copper</span><span class="pill pill-green">Choline*</span><span class="pill pill-purple">Sulforaphane</span></div>
      </div>
      <div style="background:rgba(0,212,170,.05);border:1px solid rgba(0,212,170,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">👁️</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent1);margin-bottom:.5rem;">Eyes</div>
        <div class="pill-list"><span class="pill pill-orange">Vit A (rhodopsin)</span><span class="pill pill-orange">Lutein</span><span class="pill pill-orange">Zeaxanthin</span><span class="pill pill-orange">Vit C</span><span class="pill pill-green">Vit E</span><span class="pill pill-orange">Zinc</span><span class="pill pill-purple">Omega-3 DHA</span></div>
      </div>
      <div style="background:rgba(255,209,102,.05);border:1px solid rgba(255,209,102,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🦠</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent3);margin-bottom:.5rem;">Gut & Microbiome</div>
        <div class="pill-list"><span class="pill pill-green">Dietary Fibre</span><span class="pill pill-green">Zinc</span><span class="pill pill-green">Vit A</span><span class="pill pill-orange">Vit D</span><span class="pill pill-green">Glutamine*</span><span class="pill pill-green">Omega-3</span><span class="pill pill-yellow">Probiotics*</span></div>
      </div>
      <div style="background:rgba(255,107,107,.05);border:1px solid rgba(255,107,107,.15);border-radius:.5rem;padding:1rem;">
        <div style="font-size:1.3rem;margin-bottom:.4rem;">🧬</div>
        <div style="font-family:var(--sans);font-size:13px;font-weight:700;color:var(--accent2);margin-bottom:.5rem;">DNA Synthesis & Repair</div>
        <div class="pill-list"><span class="pill pill-green">Folate (B9)</span><span class="pill pill-blue">B12</span><span class="pill pill-green">Vit C</span><span class="pill pill-yellow">Zinc</span><span class="pill pill-green">Selenium</span><span class="pill pill-orange">Niacin (NAD⁺)</span><span class="pill pill-green">Iron</span></div>
      </div>
    </div>
    <p style="font-size:10px;color:var(--text3);margin-top:1rem;font-family:var(--mono);">* Conditionally essential or non-vitamin/mineral nutrient with strong evidence</p>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ DEFICIENCY ═══════════════════════════════ -->
<section class="section" id="deficiency">
  <div class="section-header">
    <span class="section-number">09</span>
    <h2 class="section-title">Deficiency <span class="section-accent">Diseases</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Classic clinical consequences of prolonged nutritional deficiency. Most are preventable with diet.</p>

  <div class="warn-grid">
    <div class="warn-card"><div class="warn-card-title">Scurvy → Vit C</div><div class="warn-card-body">Defective collagen → bleeding gums, perifollicular haemorrhage, poor wound healing, corkscrew hairs, joint pain. Fatal if untreated. Historical: sailors on long voyages.</div></div>
    <div class="warn-card"><div class="warn-card-title">Rickets / Osteomalacia → Vit D</div><div class="warn-card-body">Soft bones in children (bowed legs, delayed fontanelle closure). Osteomalacia in adults (bone pain, muscle weakness, stress fractures). Pandemic scale globally.</div></div>
    <div class="warn-card"><div class="warn-card-title">Pellagra → Niacin (B3)</div><div class="warn-card-body">4 Ds: Dermatitis (sun-exposed skin), Diarrhoea, Dementia, Death. Occurs in maize-dominant diets (niacin bound as niacytin). Historic in American South & Africa.</div></div>
    <div class="warn-card"><div class="warn-card-title">Beriberi → Thiamine (B1)</div><div class="warn-card-body">Dry: peripheral neuropathy, muscle weakness. Wet: cardiac failure, oedema. Wernicke-Korsakoff in alcoholics: ataxia, ophthalmoplegia, confabulation. White-rice diets.</div></div>
    <div class="warn-card"><div class="warn-card-title">Night Blindness → Vit A</div><div class="warn-card-body">Rhodopsin cannot regenerate → inability to see in low light. Full deficiency → xerophthalmia → corneal ulceration → blindness. #1 cause of preventable blindness in children.</div></div>
    <div class="warn-card"><div class="warn-card-title">Iron-Deficiency Anaemia → Iron</div><div class="warn-card-body">Microcytic anaemia: fatigue, pallor, cold intolerance, pica, impaired cognition. Most common nutritional deficiency worldwide. Women of childbearing age at highest risk.</div></div>
    <div class="warn-card"><div class="warn-card-title">Goitre / Cretinism → Iodine</div><div class="warn-card-body">Goitre: thyroid enlargement. Cretinism (severe deficiency in pregnancy): intellectual disability, deafness, short stature. Still affects 800M+ globally (inland areas).</div></div>
    <div class="warn-card"><div class="warn-card-title">Megaloblastic Anaemia → B12/Folate</div><div class="warn-card-body">Large, immature RBCs (macro-ovalocytes). B12 also causes subacute combined degeneration of spinal cord — irreversible if untreated. Vegans: supplement B12.</div></div>
    <div class="warn-card"><div class="warn-card-title">Osteoporosis → Ca/Vit D/K2</div><div class="warn-card-body">Low bone mineral density → fracture risk. Common in post-menopausal women. Multifactorial (Ca + Vit D + K2 + Mg + protein + exercise). Silent until fracture.</div></div>
    <div class="warn-card"><div class="warn-card-title">Kwashiorkor → Protein</div><div class="warn-card-body">Severe protein malnutrition: oedema (hypoalbuminaemia), skin lesions, "moon face", liver enlargement, growth failure. Marasmus = caloric + protein (emaciation).</div></div>
    <div class="warn-card"><div class="warn-card-title">Hypomagnesaemia → Magnesium</div><div class="warn-card-body">Muscle cramps, tremors, arrhythmias, anxiety, insomnia, hypertension. Depleted by alcohol, stress, PPIs, diuretics. Subclinical deficiency extremely common.</div></div>
    <div class="warn-card"><div class="warn-card-title">Neural Tube Defects → Folate</div><div class="warn-card-body">Spina bifida, anencephaly — failure of neural tube closure at 21–28 days gestation (before many women know they're pregnant). Mandatory folic acid fortification in flour (many countries).</div></div>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ FOOD SOURCES ═══════════════════════════════ -->
<section class="section" id="food-sources">
  <div class="section-header">
    <span class="section-number">10</span>
    <h2 class="section-title">Food <span class="section-accent">Sources</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Nutritional powerhouses — foods with exceptional density across multiple nutrients.</p>

  <div class="food-grid">
    <div class="food-card"><div class="food-emoji">🥚</div><div class="food-name">Eggs</div><div class="food-contains">B12, B2, D, A, K2, Choline, Zinc, Selenium, Biotin, Quality protein (all EAA)</div></div>
    <div class="food-card"><div class="food-emoji">🐟</div><div class="food-name">Salmon</div><div class="food-contains">Omega-3 (EPA/DHA), Vit D, B12, B3, Selenium, Potassium, Protein, Astaxanthin</div></div>
    <div class="food-card"><div class="food-emoji">🥩</div><div class="food-name">Beef Liver</div><div class="food-contains">A, B12, Folate, B2, B6, Iron (heme), Copper, Zinc, CoQ10 — "nature's multivitamin"</div></div>
    <div class="food-card"><div class="food-emoji">🥦</div><div class="food-name">Broccoli</div><div class="food-contains">Vit C, K1, Folate, B6, Fibre, Sulforaphane (Nrf2), Calcium, Iron, Chromium</div></div>
    <div class="food-card"><div class="food-emoji">🫐</div><div class="food-name">Blueberries</div><div class="food-contains">Anthocyanins, Vit C, K1, Mn, Fibre, anti-oxidants — highest ORAC score of fruits</div></div>
    <div class="food-card"><div class="food-emoji">🥑</div><div class="food-name">Avocado</div><div class="food-contains">MUFA (oleic acid), Potassium (>banana), Folate, B5, B6, K1, Vit E, Fibre, Magnesium</div></div>
    <div class="food-card"><div class="food-emoji">🌿</div><div class="food-name">Spinach</div><div class="food-contains">Vit K1, A, C, Folate, Iron (non-heme), Magnesium, Manganese, B2, Lutein, Zeaxanthin</div></div>
    <div class="food-card"><div class="food-emoji">🫘</div><div class="food-name">Lentils</div><div class="food-contains">Folate, Iron, Fibre, Protein, Manganese, B1, B6, Potassium, Copper, Zinc, Phosphorus</div></div>
    <div class="food-card"><div class="food-emoji">🥜</div><div class="food-name">Almonds</div><div class="food-contains">Vit E (highest), Magnesium, Calcium, Phosphorus, MUFA, Fibre, Riboflavin, Manganese</div></div>
    <div class="food-card"><div class="food-emoji">🌊</div><div class="food-name">Seaweed / Nori</div><div class="food-contains">Iodine, B12 (some), Fucoidan, Omega-3, Vit K, Iron, Magnesium, Tyrosine — extremely mineral-dense</div></div>
    <div class="food-card"><div class="food-emoji">🫚</div><div class="food-name">Olive Oil (EVOO)</div><div class="food-contains">Oleic acid (MUFA), Vit E, Vit K, Polyphenols (oleocanthal = ibuprofen-like), Squalene</div></div>
    <div class="food-card"><div class="food-emoji">🌰</div><div class="food-name">Brazil Nuts</div><div class="food-contains">Selenium (1-2 nuts = daily RDA), Magnesium, Copper, Zinc, Vit E, Thiamine, Phosphorus</div></div>
    <div class="food-card"><div class="food-emoji">🧄</div><div class="food-name">Garlic</div><div class="food-contains">Allicin, Organosulfurs, B6, C, Mn, Selenium, Calcium, antimicrobial, cardiovascular support</div></div>
    <div class="food-card"><div class="food-emoji">🟡</div><div class="food-name">Turmeric</div><div class="food-contains">Curcumin (NF-κB inhibitor), Mn, Iron, B6, Vit C, Fibre — bioavailability ↑ with piperine (black pepper)</div></div>
    <div class="food-card"><div class="food-emoji">🍄</div><div class="food-name">Shiitake Mushrooms</div><div class="food-contains">B vitamins, D (UV), Copper, Zinc, Selenium, Lentinan (immune β-glucan), Pantothenic acid</div></div>
    <div class="food-card"><div class="food-emoji">🎋</div><div class="food-name">Natto</div><div class="food-contains">Vit K2 (MK-7) — highest known food source, Protein, Iron, Copper, Mn, B vitamins, nattokinase enzyme</div></div>
  </div>
</section>

<hr class="divider">

<!-- ═══════════════════════════════ INTERACTIONS ═══════════════════════════════ -->
<section class="section" id="interactions">
  <div class="section-header">
    <span class="section-number">11</span>
    <h2 class="section-title">Critical <span class="section-accent">Interactions</span></h2>
  </div>
  <p style="color:var(--text2);margin-bottom:2rem;font-size:12px;">Nutrients don't work in isolation. These synergies and antagonisms are often overlooked in single-nutrient thinking.</p>

  <div class="interact-grid">
    <div class="interact-card"><div class="interact-card-title">✅ Vit D + Vit K2 + Calcium + Magnesium</div><div class="interact-card-body">The "bone quartet": D increases Ca absorption, K2 routes Ca to bones (not arteries) via osteocalcin, Mg is required to activate D. Take all together. Missing K2 when supplementing D+Ca → arterial calcification risk.</div></div>
    <div class="interact-card"><div class="interact-card-title">✅ Vit C + Iron (non-heme)</div><div class="interact-card-body">Ascorbic acid reduces Fe³⁺ → Fe²⁺, increasing non-heme iron absorption 2–3x. Take lemon/orange juice with plant-based iron meals. Counteracts phytate inhibition in legumes.</div></div>
    <div class="interact-card"><div class="interact-card-title">✅ Folate + B12 + B6</div><div class="interact-card-body">Methylation trio: converts homocysteine → methionine (B12 + folate) and cystathionine (B6). Deficiency in any → hyperhomocysteinaemia → cardiovascular & neurological damage.</div></div>
    <div class="interact-card"><div class="interact-card-title">✅ Curcumin + Piperine</div><div class="interact-card-body">Black pepper's piperine inhibits CYP3A4 & glucuronidation → increases curcumin bioavailability by 2,000%. Always pair turmeric with black pepper. Fat-soluble → take with food.</div></div>
    <div class="interact-card"><div class="interact-card-title">✅ Omega-3 + Vit E</div><div class="interact-card-body">Omega-3 PUFAs are highly susceptible to oxidation. Vit E (α-tocopherol) protects them in vivo. High omega-3 intake slightly increases Vit E requirements. Both anti-inflammatory and synergistic.</div></div>
    <div class="interact-card"><div class="interact-card-title">✅ Selenium + Iodine</div><div class="interact-card-body">Selenium (via selenoproteins GPx + deiodinase) is required for T4 → T3 conversion AND protects thyroid from H₂O₂ oxidative stress during hormone synthesis. Without Se, iodine loading can damage thyroid.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Calcium vs Iron / Zinc</div><div class="interact-card-body">High Ca intake (>300mg) at same meal inhibits non-heme iron and zinc absorption competitively. Separate dairy from iron-rich meals. Particularly important for women with iron-deficiency anaemia.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Zinc vs Copper</div><div class="interact-card-body">High-dose zinc supplementation (>50 mg/day) induces metallothionein in gut — sequesters copper and blocks its absorption. Chronic zinc → copper deficiency → anaemia, nerve damage. Ratio matters: Zn:Cu ~8–15:1.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Folate masks B12 deficiency</div><div class="interact-card-body">High folate corrects the haematological signs of B12 deficiency (megaloblastic anaemia) while allowing the neurological damage (subacute combined degeneration) to progress silently. Always check B12 with high folate.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Vit E vs Vit K2</div><div class="interact-card-body">Very high Vit E (>400 IU/day) antagonises vitamin K's clotting factor activation — increases bleeding risk. Problematic on anticoagulants (Warfarin). Critical pre-surgery consideration.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Phytates block mineral absorption</div><div class="interact-card-body">Phytic acid in grains/legumes/nuts chelates Zn, Fe, Ca, Mn, Cu. Reduce by soaking (8h+), sprouting, fermenting, or cooking. Vegans especially affected. Vit C partially counteracts.</div></div>
    <div class="interact-card"><div class="interact-card-title">⚠️ Coffee / Tea vs Iron</div><div class="interact-card-body">Tannins & polyphenols in tea/coffee bind iron strongly, reducing absorption 50–90%. Wait 1h after iron-rich meals before coffee/tea. Green tea (EGCG) is particularly potent iron chelator.</div></div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p style="margin-bottom:.5rem;font-size:16px;">🧬</p>
  <p>Complete Human Nutrition Atlas · Compiled 2026</p>
  <p style="margin-top:.5rem;">All nutrient values based on <strong>DRI/RDA (NIH)</strong> and peer-reviewed evidence. For medical advice, consult a qualified dietitian or physician.</p>
  <p style="margin-top:.5rem;color:var(--text3);">Fat-Soluble Vitamins · Water-Soluble Vitamins · Macrominerals · Trace Minerals · Macronutrients · Phytonutrients · Electrolytes</p>
</footer>

</body>
</html>

```
