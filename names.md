<img width="910" height="360" alt="image" src="https://github.com/user-attachments/assets/5ddf07d6-6f04-4f2c-af37-164db96de18b" />
<img width="1103" height="420" alt="image" src="https://github.com/user-attachments/assets/59127c7b-cc72-490e-bda2-c66d65f9174d" />

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Learning Mastery — Visual Notes</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&family=Fraunces:wght@300;400;600&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0e0e0f;
    --bg2: #141416;
    --bg3: #1a1a1d;
    --bg4: #212124;
    --border: rgba(255,255,255,0.08);
    --border2: rgba(255,255,255,0.14);
    --text: #e8e6e0;
    --muted: #888580;
    --dim: #555350;
    --accent-red: #e85d3c;
    --accent-amber: #f0a030;
    --accent-teal: #2eb89a;
    --accent-blue: #5b9cf6;
    --accent-purple: #9b84f0;
    --accent-pink: #e86da8;
    --card-radius: 12px;
  }
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    line-height: 1.7;
    padding: 0;
    min-height: 100vh;
  }

  /* ---- HERO ---- */
  .hero {
    background: var(--bg2);
    border-bottom: 1px solid var(--border);
    padding: 60px 48px 48px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 60% 80% at 80% 50%, rgba(91,156,246,0.05) 0%, transparent 70%),
                radial-gradient(ellipse 40% 60% at 20% 80%, rgba(155,132,240,0.04) 0%, transparent 70%);
  }
  .hero-tag {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.12em;
    color: var(--accent-teal);
    text-transform: uppercase;
    margin-bottom: 16px;
  }
  .hero h1 {
    font-family: 'Fraunces', serif;
    font-size: clamp(28px, 5vw, 48px);
    font-weight: 300;
    line-height: 1.2;
    color: var(--text);
    max-width: 640px;
    position: relative;
  }
  .hero h1 em {
    font-style: normal;
    color: var(--accent-amber);
  }
  .hero-sub {
    color: var(--muted);
    font-size: 14px;
    margin-top: 14px;
    font-family: 'JetBrains Mono', monospace;
    position: relative;
  }
  .toc {
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    margin-top: 28px;
    position: relative;
  }
  .toc a {
    padding: 6px 14px;
    border-radius: 100px;
    border: 1px solid var(--border2);
    color: var(--muted);
    text-decoration: none;
    font-size: 12px;
    font-family: 'JetBrains Mono', monospace;
    transition: all 0.2s;
  }
  .toc a:hover { color: var(--text); border-color: rgba(255,255,255,0.3); }

  /* ---- LAYOUT ---- */
  .page { max-width: 1100px; margin: 0 auto; padding: 48px 32px 80px; }

  .section-header {
    display: flex;
    align-items: center;
    gap: 16px;
    margin-bottom: 32px;
    margin-top: 64px;
  }
  .section-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--dim);
    min-width: 28px;
  }
  .section-title {
    font-family: 'Fraunces', serif;
    font-size: 26px;
    font-weight: 400;
    color: var(--text);
  }
  .section-line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  .section-badge {
    font-size: 11px;
    font-family: 'JetBrains Mono', monospace;
    padding: 4px 10px;
    border-radius: 4px;
    letter-spacing: 0.06em;
  }

  /* ---- CARDS ---- */
  .card {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--card-radius);
    padding: 24px;
    transition: border-color 0.2s;
  }
  .card:hover { border-color: var(--border2); }
  .card-title {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    margin-bottom: 10px;
  }
  .card h3 {
    font-family: 'Fraunces', serif;
    font-size: 18px;
    font-weight: 400;
    margin-bottom: 8px;
    line-height: 1.3;
  }
  .card p { color: var(--muted); font-size: 14px; line-height: 1.65; }

  .grid-2 { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 16px; }
  .grid-3 { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 16px; }
  .grid-4 { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 16px; }

  /* ---- DIAGRAM CONTAINERS ---- */
  .diagram-wrap {
    background: var(--bg3);
    border: 1px solid var(--border);
    border-radius: var(--card-radius);
    padding: 32px;
    margin: 24px 0;
  }

  /* ---- PROCRASTINATION SECTION ---- */
  .brain-loop {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 0;
    flex-wrap: wrap;
    padding: 8px 0;
  }
  .loop-node {
    background: var(--bg4);
    border: 1px solid var(--border2);
    border-radius: 8px;
    padding: 14px 18px;
    text-align: center;
    min-width: 120px;
    position: relative;
  }
  .loop-node .node-label {
    font-size: 11px;
    font-family: 'JetBrains Mono', monospace;
    color: var(--muted);
    margin-bottom: 4px;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }
  .loop-node .node-text {
    font-size: 13px;
    font-weight: 500;
    color: var(--text);
  }
  .loop-arrow {
    color: var(--dim);
    font-size: 20px;
    padding: 0 6px;
  }
  .loop-node.hot { border-color: rgba(232,93,60,0.5); background: rgba(232,93,60,0.06); }
  .loop-node.hot .node-text { color: var(--accent-red); }
  .loop-node.break { border-color: rgba(46,184,154,0.5); background: rgba(46,184,154,0.06); }
  .loop-node.break .node-text { color: var(--accent-teal); }

  /* ---- TECHNIQUE ROWS ---- */
  .technique {
    display: flex;
    gap: 20px;
    align-items: flex-start;
    padding: 20px 0;
    border-bottom: 1px solid var(--border);
  }
  .technique:last-child { border-bottom: none; }
  .technique-num {
    font-family: 'JetBrains Mono', monospace;
    font-size: 24px;
    font-weight: 700;
    min-width: 44px;
    line-height: 1;
    margin-top: 2px;
  }
  .technique-body h4 {
    font-size: 15px;
    font-weight: 500;
    margin-bottom: 6px;
  }
  .technique-body p { color: var(--muted); font-size: 13px; line-height: 1.65; }
  .technique-body .formula {
    margin-top: 10px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    background: var(--bg4);
    padding: 8px 12px;
    border-radius: 6px;
    color: var(--accent-amber);
    border-left: 2px solid var(--accent-amber);
  }

  /* ---- TIMER VIZ ---- */
  .timer-blocks {
    display: flex;
    gap: 4px;
    flex-wrap: wrap;
    margin: 16px 0;
  }
  .timer-block {
    width: 18px;
    height: 28px;
    border-radius: 3px;
    border: 1px solid var(--border);
    background: var(--bg4);
    transition: all 0.15s;
    cursor: default;
  }
  .timer-block.active { background: var(--accent-teal); border-color: transparent; }
  .timer-block.rest { background: rgba(91,156,246,0.35); border-color: transparent; }
  .timer-block.gap { background: var(--bg); border: 1px dashed var(--border); }
  .timer-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    color: var(--muted);
    margin-bottom: 6px;
  }

  /* ---- JAPANESE SECTION ---- */
  .feynman-flow {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
    position: relative;
    overflow: hidden;
  }
  @media (max-width: 700px) {
    .feynman-flow { grid-template-columns: repeat(2, 1fr); }
  }
  .feynman-step {
    padding: 24px 20px;
    position: relative;
    border-right: 1px solid var(--border);
  }
  .feynman-step:last-child { border-right: none; }
  .feynman-step .step-n {
    font-family: 'JetBrains Mono', monospace;
    font-size: 36px;
    font-weight: 700;
    line-height: 1;
    margin-bottom: 12px;
    opacity: 0.12;
    position: absolute;
    top: 16px;
    right: 16px;
  }
  .feynman-step .step-icon {
    font-size: 22px;
    margin-bottom: 10px;
  }
  .feynman-step h4 {
    font-size: 13px;
    font-weight: 500;
    margin-bottom: 6px;
    font-family: 'JetBrains Mono', monospace;
    letter-spacing: 0.04em;
  }
  .feynman-step p { font-size: 12px; color: var(--muted); line-height: 1.6; }

  .feynman-step.s1 { border-top: 2px solid var(--accent-blue); }
  .feynman-step.s2 { border-top: 2px solid var(--accent-amber); }
  .feynman-step.s3 { border-top: 2px solid var(--accent-red); }
  .feynman-step.s4 { border-top: 2px solid var(--accent-teal); }

  .feynman-step.s1 .step-icon { color: var(--accent-blue); }
  .feynman-step.s2 .step-icon { color: var(--accent-amber); }
  .feynman-step.s3 .step-icon { color: var(--accent-red); }
  .feynman-step.s4 .step-icon { color: var(--accent-teal); }
  .feynman-step.s1 h4 { color: var(--accent-blue); }
  .feynman-step.s2 h4 { color: var(--accent-amber); }
  .feynman-step.s3 h4 { color: var(--accent-red); }
  .feynman-step.s4 h4 { color: var(--accent-teal); }

  /* ---- CHUNKING VIZ ---- */
  .chunk-viz {
    display: flex;
    gap: 12px;
    align-items: flex-end;
    flex-wrap: wrap;
    padding: 20px 0;
  }
  .chunk {
    border-radius: 6px;
    padding: 10px 14px;
    font-family: 'JetBrains Mono', monospace;
    font-size: 12px;
    text-align: center;
    min-width: 80px;
  }
  .chunk.raw { background: rgba(136,133,128,0.15); border: 1px solid var(--border2); color: var(--muted); }
  .chunk.grouped { background: rgba(46,184,154,0.1); border: 1px solid rgba(46,184,154,0.3); color: var(--accent-teal); }
  .chunk.mastered { background: rgba(46,184,154,0.2); border: 1px solid rgba(46,184,154,0.5); color: var(--accent-teal); font-weight: 500; }
  .chunk .label { font-size: 10px; color: var(--dim); margin-top: 4px; }

  /* ---- KAIZEN STAIRCASE ---- */
  .staircase {
    display: flex;
    align-items: flex-end;
    gap: 6px;
    padding: 20px 0 8px;
  }
  .stair {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
  }
  .stair-label {
    font-family: 'JetBrains Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    writing-mode: vertical-rl;
    text-orientation: mixed;
    transform: rotate(180deg);
    white-space: nowrap;
  }
  .stair-block {
    width: 48px;
    border-radius: 4px 4px 0 0;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding-top: 6px;
    font-size: 11px;
    font-family: 'JetBrains Mono', monospace;
    font-weight: 700;
  }

  /* ---- LEARNING SECTION ---- */
  .memory-pyramid {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 4px;
    padding: 16px 0;
  }
  .pyramid-row {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 16px;
    width: 100%;
  }
  .pyramid-bar {
    border-radius: 4px;
    padding: 10px 16px;
    text-align: center;
    font-size: 13px;
    font-weight: 500;
    position: relative;
  }
  .pyramid-bar .pct {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    opacity: 0.7;
    margin-top: 2px;
  }
  .pyramid-annotation {
    font-size: 11px;
    color: var(--dim);
    font-family: 'JetBrains Mono', monospace;
    min-width: 100px;
    text-align: left;
  }

  /* ---- SPACED REP VIZ ---- */
  .sr-calendar {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    gap: 4px;
    max-width: 320px;
    margin: 16px 0;
  }
  .sr-day {
    aspect-ratio: 1;
    border-radius: 4px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 10px;
    font-family: 'JetBrains Mono', monospace;
    border: 1px solid var(--border);
    background: var(--bg4);
    color: var(--dim);
    cursor: default;
  }
  .sr-day.review { background: rgba(91,156,246,0.2); border-color: rgba(91,156,246,0.4); color: var(--accent-blue); }
  .sr-day.strong { background: rgba(46,184,154,0.25); border-color: rgba(46,184,154,0.5); color: var(--accent-teal); font-weight: 700; }
  .sr-day.today { border-color: var(--accent-amber); color: var(--accent-amber); font-weight: 700; }

  /* ---- ACTIVE RECALL GRID ---- */
  .recall-vs {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    gap: 0;
    align-items: center;
  }
  .rv-col { padding: 20px; }
  .rv-col.bad { border-radius: 8px 0 0 8px; background: rgba(232,93,60,0.06); border: 1px solid rgba(232,93,60,0.2); border-right: none; }
  .rv-col.good { border-radius: 0 8px 8px 0; background: rgba(46,184,154,0.06); border: 1px solid rgba(46,184,154,0.2); border-left: none; }
  .rv-divider { width: 1px; background: var(--border2); align-self: stretch; }
  .rv-label { font-size: 10px; font-family: 'JetBrains Mono', monospace; letter-spacing: 0.1em; text-transform: uppercase; margin-bottom: 10px; }
  .rv-label.bad { color: var(--accent-red); }
  .rv-label.good { color: var(--accent-teal); }
  .rv-item { font-size: 13px; color: var(--muted); padding: 4px 0; border-bottom: 1px solid var(--border); }
  .rv-item:last-child { border-bottom: none; }

  /* ---- FOCUS STATE TIMELINE ---- */
  .timeline {
    position: relative;
    padding: 0 0 0 28px;
    border-left: 2px solid var(--border2);
    margin: 16px 0;
  }
  .tl-item {
    margin-bottom: 24px;
    position: relative;
  }
  .tl-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
    border: 2px solid;
    position: absolute;
    left: -34px;
    top: 4px;
    background: var(--bg);
  }
  .tl-time {
    font-family: 'JetBrains Mono', monospace;
    font-size: 11px;
    margin-bottom: 4px;
  }
  .tl-title { font-size: 14px; font-weight: 500; margin-bottom: 4px; }
  .tl-desc { font-size: 13px; color: var(--muted); }

  /* ---- FORMULA BOX ---- */
  .formula-box {
    background: var(--bg4);
    border: 1px solid var(--border2);
    border-radius: 8px;
    padding: 20px 24px;
    margin: 20px 0;
    font-family: 'JetBrains Mono', monospace;
  }
  .formula-box .f-label {
    font-size: 10px;
    color: var(--dim);
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 8px;
  }
  .formula-box .f-eq {
    font-size: 16px;
    color: var(--accent-amber);
    margin-bottom: 6px;
  }
  .formula-box .f-note { font-size: 11px; color: var(--muted); }

  /* ---- HIGHLIGHT CALLOUT ---- */
  .callout {
    padding: 16px 20px;
    border-radius: 8px;
    margin: 16px 0;
    border-left: 3px solid;
  }
  .callout.amber { background: rgba(240,160,48,0.07); border-color: var(--accent-amber); }
  .callout.teal  { background: rgba(46,184,154,0.07); border-color: var(--accent-teal); }
  .callout.red   { background: rgba(232,93,60,0.07);  border-color: var(--accent-red); }
  .callout.blue  { background: rgba(91,156,246,0.07); border-color: var(--accent-blue); }
  .callout p { font-size: 13px; color: var(--text); line-height: 1.65; }
  .callout strong { color: var(--text); }

  /* ---- TAGS ---- */
  .tag {
    display: inline-block;
    font-size: 10px;
    font-family: 'JetBrains Mono', monospace;
    padding: 3px 8px;
    border-radius: 4px;
    letter-spacing: 0.05em;
    text-transform: uppercase;
    margin-right: 4px;
    margin-bottom: 4px;
  }
  .tag.teal  { background: rgba(46,184,154,0.15); color: var(--accent-teal); }
  .tag.amber { background: rgba(240,160,48,0.15);  color: var(--accent-amber); }
  .tag.red   { background: rgba(232,93,60,0.15);   color: var(--accent-red); }
  .tag.blue  { background: rgba(91,156,246,0.15);  color: var(--accent-blue); }
  .tag.purple{ background: rgba(155,132,240,0.15); color: var(--accent-purple); }

  /* ---- FOOTER ---- */
  .footer {
    margin-top: 80px;
    padding-top: 32px;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: wrap;
    gap: 12px;
  }
  .footer-text { font-size: 12px; color: var(--dim); font-family: 'JetBrains Mono', monospace; }

  /* ---- RESPONSIVE ---- */
  @media (max-width: 600px) {
    .hero { padding: 40px 24px 36px; }
    .page { padding: 32px 20px 60px; }
    .recall-vs { grid-template-columns: 1fr; }
    .rv-col.bad { border-radius: 8px 8px 0 0; border-right: 1px solid rgba(232,93,60,0.2); border-bottom: none; }
    .rv-col.good { border-radius: 0 0 8px 8px; border-left: 1px solid rgba(46,184,154,0.2); border-top: none; }
    .rv-divider { display: none; }
  }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <p class="hero-tag">// visual study notes — learning science</p>
  <h1>Stop Procrastinating.<br>Learn <em>Faster.</em> Master Anything.</h1>
  <p class="hero-sub">Feynman · Kaizen · Spaced Repetition · Deep Work · Active Recall</p>
  <nav class="toc">
    <a href="#proc">01 — Procrastination</a>
    <a href="#japanese">02 — Japanese Tricks</a>
    <a href="#learn">03 — Learn Faster</a>
    <a href="#master">04 — Master Any Subject</a>
    <a href="#stack">05 — Full Stack</a>
  </nav>
</div>

<div class="page">

<!-- ═══════════════════════════════════════════ -->
<!-- SECTION 01 — PROCRASTINATION               -->
<!-- ═══════════════════════════════════════════ -->
<div id="proc">
  <div class="section-header">
    <span class="section-num">01</span>
    <h2 class="section-title">How to Stop Procrastinating</h2>
    <div class="section-line"></div>
    <span class="section-badge tag amber">Neuroscience</span>
  </div>

  <!-- The Loop -->
  <div class="diagram-wrap">
    <p class="timer-label">The procrastination feedback loop</p>
    <div class="brain-loop">
      <div class="loop-node hot">
        <div class="node-label">Trigger</div>
        <div class="node-text">Hard task</div>
      </div>
      <div class="loop-arrow">→</div>
      <div class="loop-node hot">
        <div class="node-label">Emotion</div>
        <div class="node-text">Anxiety / dread</div>
      </div>
      <div class="loop-arrow">→</div>
      <div class="loop-node hot">
        <div class="node-label">Escape</div>
        <div class="node-text">Dopamine hit</div>
      </div>
      <div class="loop-arrow">→</div>
      <div class="loop-node hot">
        <div class="node-label">Relief</div>
        <div class="node-text">Short-term ok</div>
      </div>
      <div class="loop-arrow">→</div>
      <div class="loop-node hot">
        <div class="node-label">Outcome</div>
        <div class="node-text">Guilt + cycle</div>
      </div>
    </div>
    <div class="callout red" style="margin-top: 16px;">
      <p>Procrastination is <strong>not laziness</strong>. It is an <strong>emotion regulation failure</strong>. The brain avoids pain (complexity, boredom, fear of failure), not the task itself. Fix the emotion first.</p>
    </div>
  </div>

  <!-- Techniques -->
  <div class="diagram-wrap">
    <p class="timer-label">Anti-procrastination techniques</p>

    <div class="technique">
      <div class="technique-num" style="color: var(--accent-teal);">01</div>
      <div class="technique-body">
        <h4>2-Minute Rule</h4>
        <p>If a task takes less than 2 minutes — do it immediately. This tricks the brain into starting and creates momentum. The hardest part is always the first moment of engagement.</p>
        <div class="formula">if task_time ≤ 2min → do_now() else start_with_first_2min()</div>
      </div>
    </div>

    <div class="technique">
      <div class="technique-num" style="color: var(--accent-amber);">02</div>
      <div class="technique-body">
        <h4>Pomodoro Technique</h4>
        <p>25 min deep work → 5 min break. After 4 cycles, take a 20-30 min long break. Removes the infinite horizon of a task and makes starting psychologically safe.</p>
        <div style="margin-top: 14px;">
          <div class="timer-label">1 Pomodoro cycle — 25 work blocks + 5 rest</div>
          <div class="timer-blocks">
            <!-- 25 work -->
            <div class="timer-block active" title="Work"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div>
            <div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div>
            <div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div>
            <div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div>
            <div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div><div class="timer-block active"></div>
            <!-- gap -->
            <div class="timer-block gap"></div>
            <!-- 5 rest -->
            <div class="timer-block rest"></div><div class="timer-block rest"></div><div class="timer-block rest"></div><div class="timer-block rest"></div><div class="timer-block rest"></div>
          </div>
          <div style="display:flex; gap: 16px; margin-top: 6px;">
            <span style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--muted);font-family:'JetBrains Mono',monospace;"><span style="width:10px;height:10px;border-radius:2px;background:var(--accent-teal);display:inline-block"></span> Work (25 min)</span>
            <span style="display:flex;align-items:center;gap:5px;font-size:11px;color:var(--muted);font-family:'JetBrains Mono',monospace;"><span style="width:10px;height:10px;border-radius:2px;background:rgba(91,156,246,0.35);display:inline-block"></span> Rest (5 min)</span>
          </div>
        </div>
      </div>
    </div>

    <div class="technique">
      <div class="technique-num" style="color: var(--accent-blue);">03</div>
      <div class="technique-body">
        <h4>Implementation Intention</h4>
        <p>Don't say "I'll study algorithms". Say: <em>"When I sit at my desk at 8pm, I will open CLRS Chapter 4 and solve Problem 4.1."</em> Specificity kills vague resistance.</p>
        <div class="formula">WHEN [cue] + WHERE [context] → I WILL [exact action]</div>
      </div>
    </div>

    <div class="technique">
      <div class="technique-num" style="color: var(--accent-purple);">04</div>
      <div class="technique-body">
        <h4>Temptation Bundling</h4>
        <p>Pair a task you dread with something you love. Bach or Nils Frahm only plays when studying. Walking is only for podcasts. The reward becomes inseparable from the behavior.</p>
        <div class="formula">task_you_resist + reward_you_want = habit_that_sticks</div>
      </div>
    </div>

    <div class="technique">
      <div class="technique-num" style="color: var(--accent-red);">05</div>
      <div class="technique-body">
        <h4>Remove Activation Energy</h4>
        <p>Prepare your environment the night before. CLRS open to the right page. IDE project already open. Terminal ready. Every removed friction step is one less excuse to not start.</p>
        <div class="formula">environment_design → behavior_prediction → 0 willpower needed</div>
      </div>
    </div>

    <div class="technique" style="border-bottom: none;">
      <div class="technique-num" style="color: var(--accent-pink);">06</div>
      <div class="technique-body">
        <h4>Identity Shift (Atomic Habits)</h4>
        <p>Don't aim for the outcome. Aim to become the person. Not "I want to crack GATE" but "I am someone who solves algorithms every morning." Every session is a vote for that identity.</p>
        <div class="formula">"I am ___" > "I want ___"</div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- SECTION 02 — JAPANESE TRICKS               -->
<!-- ═══════════════════════════════════════════ -->
<div id="japanese">
  <div class="section-header">
    <span class="section-num">02</span>
    <h2 class="section-title">Japanese Tricks to Learn Complex Problems Fast</h2>
    <div class="section-line"></div>
    <span class="section-badge tag blue">Kaizen · Ikigai</span>
  </div>

  <!-- Kaizen -->
  <div class="diagram-wrap">
    <p class="timer-label" style="margin-bottom: 4px;">Kaizen — 改善 — continuous improvement by 1%</p>
    <p style="font-size: 13px; color: var(--muted); margin-bottom: 20px;">The Japanese factory principle applied to learning. No dramatic sprints. Steady, compounding improvement every session.</p>

    <div class="staircase">
      <div class="stair">
        <div class="stair-label">Day 1</div>
        <div class="stair-block" style="height:30px;background:rgba(46,184,154,0.15);border:1px solid rgba(46,184,154,0.3);color:var(--accent-teal);">+1%</div>
      </div>
      <div class="stair">
        <div class="stair-label">Day 7</div>
        <div class="stair-block" style="height:50px;background:rgba(46,184,154,0.2);border:1px solid rgba(46,184,154,0.4);color:var(--accent-teal);">+7%</div>
      </div>
      <div class="stair">
        <div class="stair-label">Month 1</div>
        <div class="stair-block" style="height:80px;background:rgba(46,184,154,0.25);border:1px solid rgba(46,184,154,0.5);color:var(--accent-teal);">+30%</div>
      </div>
      <div class="stair">
        <div class="stair-label">Month 3</div>
        <div class="stair-block" style="height:120px;background:rgba(46,184,154,0.3);border:1px solid rgba(46,184,154,0.6);color:var(--accent-teal);">+90%</div>
      </div>
      <div class="stair">
        <div class="stair-label">Year 1</div>
        <div class="stair-block" style="height:180px;background:rgba(46,184,154,0.4);border:1px solid rgba(46,184,154,0.7);color:var(--accent-teal);font-size:12px;">37×</div>
      </div>
    </div>
    <p style="font-size:11px;color:var(--dim);font-family:'JetBrains Mono',monospace;margin-top:8px;">1.01^365 = 37.78 — the math of 1% daily improvement</p>
  </div>

  <!-- Feynman -->
  <div class="diagram-wrap" style="padding: 0; overflow: hidden;">
    <div style="padding: 20px 24px 0;">
      <p class="timer-label">Feynman Technique — the Japanese way to master hard concepts</p>
      <p style="font-size: 13px; color: var(--muted); margin-top: 4px;">Richard Feynman learned Japanese and multiple complex physics domains using this exact loop. Used universally by top Japanese students (東大 Todai).</p>
    </div>
    <div class="feynman-flow" style="margin-top: 20px;">
      <div class="feynman-step s1">
        <div class="step-n">1</div>
        <div class="step-icon">📖</div>
        <h4>Study the concept</h4>
        <p>Read/watch until you understand. CLRS, lectures, problem sets. Don't skip steps. First pass is comprehension.</p>
      </div>
      <div class="feynman-step s2">
        <div class="step-n">2</div>
        <div class="step-icon">✏️</div>
        <h4>Explain it simply</h4>
        <p>Write it in plain language as if teaching a 12-year-old. No jargon. If you can't, you don't understand it yet.</p>
      </div>
      <div class="feynman-step s3">
        <div class="step-n">3</div>
        <div class="step-icon">🔍</div>
        <h4>Find the gaps</h4>
        <p>Where did your explanation break? Where did you reach for technical terms as a crutch? Those are your blind spots.</p>
      </div>
      <div class="feynman-step s4">
        <div class="step-n">4</div>
        <div class="step-icon">🔄</div>
        <h4>Simplify + repeat</h4>
        <p>Return to the source material for the gaps only. Re-explain. Loop until explanation is crisp and complete.</p>
      </div>
    </div>
    <div style="padding: 16px 24px 20px;">
      <div class="callout teal" style="margin: 0;">
        <p><strong>GATE application:</strong> After studying Master Theorem, close the book. Write on paper: "Master Theorem solves recurrences of the form T(n) = aT(n/b) + f(n) by comparing f(n) to n^log_b(a)..." — if you stall, you found your gap.</p>
      </div>
    </div>
  </div>

  <!-- Chunking -->
  <div class="diagram-wrap">
    <p class="timer-label">Chunking — how Japanese language learners compress complex info</p>
    <p style="font-size: 13px; color: var(--muted); margin-bottom: 20px;">Break a complex topic into minimal atomic units. Group related units. Drill each chunk until it's a single mental object. Then combine.</p>
    <div class="chunk-viz">
      <div>
        <div class="chunk raw">T(n)</div>
        <div class="label" style="font-size:10px;color:var(--dim);margin-top:4px;font-family:'JetBrains Mono',monospace">raw piece</div>
      </div>
      <div>
        <div class="chunk raw">= aT(n/b)</div>
        <div class="label" style="font-size:10px;color:var(--dim);margin-top:4px;font-family:'JetBrains Mono',monospace">raw piece</div>
      </div>
      <div>
        <div class="chunk raw">+ f(n)</div>
        <div class="label" style="font-size:10px;color:var(--dim);margin-top:4px;font-family:'JetBrains Mono',monospace">raw piece</div>
      </div>
      <div style="display:flex;align-items:center;color:var(--muted);font-size:20px;padding-bottom: 8px;">→</div>
      <div>
        <div class="chunk grouped">Master Theorem structure</div>
        <div class="label" style="font-size:10px;color:var(--accent-teal);margin-top:4px;font-family:'JetBrains Mono',monospace">grouped chunk</div>
      </div>
      <div style="display:flex;align-items:center;color:var(--muted);font-size:20px;padding-bottom: 8px;">→</div>
      <div>
        <div class="chunk mastered">Recurrence Pattern</div>
        <div class="label" style="font-size:10px;color:var(--accent-teal);margin-top:4px;font-family:'JetBrains Mono',monospace">mastered chunk</div>
      </div>
    </div>

    <div class="formula-box" style="margin-top: 8px;">
      <div class="f-label">The Chunking Protocol</div>
      <div class="f-eq">identify_atoms → cluster → drill_each → combine → apply</div>
      <div class="f-note">Each mastered chunk occupies only ONE slot in working memory — freeing capacity for harder reasoning</div>
    </div>
  </div>

  <!-- Shu Ha Ri -->
  <div class="grid-3">
    <div class="card" style="border-top: 2px solid var(--accent-blue);">
      <div class="card-title" style="color:var(--accent-blue);">Shu — 守 — Follow</div>
      <h3>Follow the rules exactly</h3>
      <p>Learn the standard method as taught. Copy solved examples. Follow the textbook algorithm step by step. No improvisation. This is how mastery begins — through disciplined imitation.</p>
    </div>
    <div class="card" style="border-top: 2px solid var(--accent-amber);">
      <div class="card-title" style="color:var(--accent-amber);">Ha — 破 — Break</div>
      <h3>Bend the rules</h3>
      <p>Once basics are solid, experiment. Modify the algorithm. Try alternative proofs. Ask "what if". You are internalizing the principles behind the rules, not just the rules themselves.</p>
    </div>
    <div class="card" style="border-top: 2px solid var(--accent-teal);">
      <div class="card-title" style="color:var(--accent-teal);">Ri — 離 — Transcend</div>
      <h3>Move beyond rules</h3>
      <p>Intuition takes over. Solutions feel obvious. You synthesize across domains. The expert doesn't think in rules — they think in patterns. This is where GATE rank under 100 lives.</p>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- SECTION 03 — LEARN FASTER                  -->
<!-- ═══════════════════════════════════════════ -->
<div id="learn">
  <div class="section-header">
    <span class="section-num">03</span>
    <h2 class="section-title">How to Learn Fast</h2>
    <div class="section-line"></div>
    <span class="section-badge tag teal">Cognitive Science</span>
  </div>

  <!-- Recall retention pyramid -->
  <div class="diagram-wrap">
    <p class="timer-label">Learning retention pyramid — how you retain vs how you study</p>
    <div class="memory-pyramid">
      <div class="pyramid-row">
        <span class="pyramid-annotation">Passive</span>
        <div class="pyramid-bar" style="width:55%;background:rgba(232,93,60,0.1);border:1px solid rgba(232,93,60,0.25);">
          <div style="color:var(--accent-red);font-weight:500;">Lecture / Reading</div>
          <div class="pct" style="color:var(--accent-red);">5–10% retained</div>
        </div>
        <span class="pyramid-annotation"></span>
      </div>
      <div class="pyramid-row">
        <span class="pyramid-annotation"></span>
        <div class="pyramid-bar" style="width:65%;background:rgba(232,93,60,0.07);border:1px solid rgba(232,93,60,0.2);">
          <div style="color:#c06040;font-weight:500;">Audio / Video</div>
          <div class="pct" style="color:#c06040;">20% retained</div>
        </div>
        <span class="pyramid-annotation"></span>
      </div>
      <div class="pyramid-row">
        <span class="pyramid-annotation"></span>
        <div class="pyramid-bar" style="width:72%;background:rgba(240,160,48,0.07);border:1px solid rgba(240,160,48,0.2);">
          <div style="color:var(--accent-amber);font-weight:500;">Demonstration</div>
          <div class="pct" style="color:var(--accent-amber);">30% retained</div>
        </div>
        <span class="pyramid-annotation"></span>
      </div>
      <div class="pyramid-row">
        <span class="pyramid-annotation">Active</span>
        <div class="pyramid-bar" style="width:80%;background:rgba(91,156,246,0.08);border:1px solid rgba(91,156,246,0.25);">
          <div style="color:var(--accent-blue);font-weight:500;">Discussion / Practice</div>
          <div class="pct" style="color:var(--accent-blue);">50–75% retained</div>
        </div>
        <span class="pyramid-annotation"></span>
      </div>
      <div class="pyramid-row">
        <span class="pyramid-annotation">↑ Best</span>
        <div class="pyramid-bar" style="width:92%;background:rgba(46,184,154,0.1);border:1px solid rgba(46,184,154,0.35);">
          <div style="color:var(--accent-teal);font-weight:500;">Teaching others / Solving</div>
          <div class="pct" style="color:var(--accent-teal);">90% retained</div>
        </div>
        <span class="pyramid-annotation"></span>
      </div>
    </div>
    <div class="callout teal" style="margin-top: 16px;">
      <p><strong>The rule:</strong> You never truly know a concept until you can produce it — solve a problem with it, explain it to someone, or derive it from scratch with the book closed.</p>
    </div>
  </div>

  <!-- Active Recall vs Re-reading -->
  <div class="diagram-wrap">
    <p class="timer-label" style="margin-bottom: 16px;">Active recall vs passive re-reading</p>
    <div class="recall-vs">
      <div class="rv-col bad">
        <div class="rv-label bad">What most people do</div>
        <div class="rv-item">Re-read notes</div>
        <div class="rv-item">Highlight text</div>
        <div class="rv-item">Re-watch lectures</div>
        <div class="rv-item">Copy definitions</div>
        <div class="rv-item">Feeling of familiarity = illusion of knowing</div>
      </div>
      <div class="rv-divider"></div>
      <div class="rv-col good">
        <div class="rv-label good">What works</div>
        <div class="rv-item">Close book → write everything you remember</div>
        <div class="rv-item">Solve problems without looking at solution</div>
        <div class="rv-item">Flashcards — answer before flipping</div>
        <div class="rv-item">Teach concept aloud without notes</div>
        <div class="rv-item">Struggle → error → correction = real encoding</div>
      </div>
    </div>
  </div>

  <!-- Spaced Repetition -->
  <div class="diagram-wrap">
    <p class="timer-label">Spaced repetition — forgetting curve interrupted</p>
    <p style="font-size:13px;color:var(--muted);margin-bottom:16px;">Review just before you forget, not just after you learn. Each review pushes the forgetting curve further out.</p>
    <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 32px;">
      <div>
        <div class="timer-label" style="margin-bottom: 8px;">Optimal review schedule</div>
        <div class="timeline">
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-blue);"></div>
            <div class="tl-time" style="color:var(--accent-blue);">Day 0</div>
            <div class="tl-title">First study</div>
            <div class="tl-desc">Initial encoding. Focus and attention critical.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-teal);"></div>
            <div class="tl-time" style="color:var(--accent-teal);">Day 1</div>
            <div class="tl-title">First review</div>
            <div class="tl-desc">Quick recall attempt before memory decays significantly.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-amber);"></div>
            <div class="tl-time" style="color:var(--accent-amber);">Day 3</div>
            <div class="tl-title">Second review</div>
            <div class="tl-desc">Retrieval feels harder — that difficulty is the signal it's working.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-amber);"></div>
            <div class="tl-time" style="color:var(--accent-amber);">Day 7</div>
            <div class="tl-title">Third review</div>
            <div class="tl-desc">Pattern recognition begins. Connections forming.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-teal);"></div>
            <div class="tl-time" style="color:var(--accent-teal);">Day 21 → 60</div>
            <div class="tl-title">Long-term reviews</div>
            <div class="tl-desc">Interval doubles. Memory now in long-term storage.</div>
          </div>
        </div>
      </div>
      <div>
        <div class="timer-label" style="margin-bottom: 8px;">Sample 4-week review calendar</div>
        <div class="sr-calendar">
          <div class="sr-day today">1</div>
          <div class="sr-day review">2</div>
          <div class="sr-day">3</div>
          <div class="sr-day review">4</div>
          <div class="sr-day">5</div>
          <div class="sr-day">6</div>
          <div class="sr-day">7</div>
          <div class="sr-day">8</div>
          <div class="sr-day strong">9</div>
          <div class="sr-day">10</div>
          <div class="sr-day">11</div>
          <div class="sr-day">12</div>
          <div class="sr-day">13</div>
          <div class="sr-day">14</div>
          <div class="sr-day">15</div>
          <div class="sr-day">16</div>
          <div class="sr-day">17</div>
          <div class="sr-day">18</div>
          <div class="sr-day">19</div>
          <div class="sr-day">20</div>
          <div class="sr-day">21</div>
          <div class="sr-day strong">22</div>
          <div class="sr-day">23</div>
          <div class="sr-day">24</div>
          <div class="sr-day">25</div>
          <div class="sr-day">26</div>
          <div class="sr-day">27</div>
          <div class="sr-day">28</div>
        </div>
        <div style="display:flex;gap:12px;margin-top:8px;flex-wrap:wrap;">
          <span style="display:flex;align-items:center;gap:5px;font-size:10px;color:var(--muted);font-family:'JetBrains Mono',monospace;"><span style="width:8px;height:8px;border-radius:2px;background:rgba(91,156,246,0.2);border:1px solid rgba(91,156,246,0.4);display:inline-block"></span>Review</span>
          <span style="display:flex;align-items:center;gap:5px;font-size:10px;color:var(--muted);font-family:'JetBrains Mono',monospace;"><span style="width:8px;height:8px;border-radius:2px;background:rgba(46,184,154,0.25);border:1px solid rgba(46,184,154,0.5);display:inline-block"></span>Strong recall</span>
          <span style="display:flex;align-items:center;gap:5px;font-size:10px;color:var(--muted);font-family:'JetBrains Mono',monospace;"><span style="width:8px;height:8px;border-radius:2px;border:1px solid var(--accent-amber);display:inline-block"></span>Today</span>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- SECTION 04 — MASTER ANY SUBJECT            -->
<!-- ═══════════════════════════════════════════ -->
<div id="master">
  <div class="section-header">
    <span class="section-num">04</span>
    <h2 class="section-title">How to Master Any Subject</h2>
    <div class="section-line"></div>
    <span class="section-badge tag purple">Deep Work</span>
  </div>

  <!-- The 4 Phases -->
  <div class="diagram-wrap" style="padding: 0; overflow: hidden;">
    <div style="padding: 20px 24px 0;">
      <p class="timer-label">The 4 phases of subject mastery</p>
    </div>
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); border-top: 1px solid var(--border); margin-top: 16px;">
      <div style="padding: 24px; border-right: 1px solid var(--border);">
        <div style="font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--dim);margin-bottom:12px;">PHASE 01 / ORIENTATION</div>
        <h4 style="font-size: 15px; font-weight: 500; margin-bottom: 8px; color: var(--accent-blue);">Build the Map</h4>
        <p style="font-size: 13px; color: var(--muted); line-height: 1.65;">Before diving deep, scan the whole territory. Table of contents, overview lectures, Wikipedia. Build a mental skeleton of the subject — chapters, subfields, interconnections.</p>
        <div style="margin-top: 12px;">
          <span class="tag blue">1–3 days</span>
          <span class="tag blue">breadth first</span>
        </div>
      </div>
      <div style="padding: 24px; border-right: 1px solid var(--border);">
        <div style="font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--dim);margin-bottom:12px;">PHASE 02 / ACQUISITION</div>
        <h4 style="font-size: 15px; font-weight: 500; margin-bottom: 8px; color: var(--accent-amber);">Deep Study</h4>
        <p style="font-size: 13px; color: var(--muted); line-height: 1.65;">Go deep into each node of your map. Textbooks, problem sets, worked examples. Use active recall after every session. This is the bulk of learning time — slow and deliberate.</p>
        <div style="margin-top: 12px;">
          <span class="tag amber">weeks–months</span>
          <span class="tag amber">depth first</span>
        </div>
      </div>
      <div style="padding: 24px; border-right: 1px solid var(--border);">
        <div style="font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--dim);margin-bottom:12px;">PHASE 03 / SYNTHESIS</div>
        <h4 style="font-size: 15px; font-weight: 500; margin-bottom: 8px; color: var(--accent-teal);">Connect the Dots</h4>
        <p style="font-size: 13px; color: var(--muted); line-height: 1.65;">Find the links between concepts. How does hashing relate to algorithm analysis? How does linear algebra underpin ML? Cross-domain insight is what separates competent from exceptional.</p>
        <div style="margin-top: 12px;">
          <span class="tag teal">ongoing</span>
          <span class="tag teal">interleaved</span>
        </div>
      </div>
      <div style="padding: 24px;">
        <div style="font-family:'JetBrains Mono',monospace;font-size:10px;color:var(--dim);margin-bottom:12px;">PHASE 04 / APPLICATION</div>
        <h4 style="font-size: 15px; font-weight: 500; margin-bottom: 8px; color: var(--accent-purple);">Build / Solve / Teach</h4>
        <p style="font-size: 13px; color: var(--muted); line-height: 1.65;">Apply under pressure: past papers, projects, real problems, explaining to others. Application pressure exposes hidden gaps and forges durable, transferable understanding.</p>
        <div style="margin-top: 12px;">
          <span class="tag purple">constant</span>
          <span class="tag purple">test yourself</span>
        </div>
      </div>
    </div>
  </div>

  <!-- Deep Work -->
  <div class="diagram-wrap">
    <p class="timer-label">Deep work — how Cal Newport defines genuine cognitive output</p>
    <div class="grid-2" style="margin-top: 16px;">
      <div>
        <div class="formula-box">
          <div class="f-label">Newport's Productivity Law</div>
          <div class="f-eq">output = time × intensity of focus</div>
          <div class="f-note">Shallow work at 40h/week ≠ deep work at 4h/day. 4h deep > 10h distracted.</div>
        </div>
        <div class="callout blue" style="margin-top: 0;">
          <p><strong>The 4-hour rule:</strong> Top intellectuals across history (Darwin, Tolkien, Feynman) rarely exceeded 4 hours of deep cognitive work per day. The limit is biological, not motivational.</p>
        </div>
      </div>
      <div>
        <div class="timer-label" style="margin-bottom: 12px;">Deep work session structure</div>
        <div class="timeline">
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-blue);"></div>
            <div class="tl-time" style="color:var(--accent-blue);">0:00 – 0:05</div>
            <div class="tl-title">Ritual start</div>
            <div class="tl-desc">Same location, same tools, music on, phone away. Signals brain to shift modes.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-teal);"></div>
            <div class="tl-time" style="color:var(--accent-teal);">0:05 – 1:30</div>
            <div class="tl-title">Peak focus block</div>
            <div class="tl-desc">Single problem. No tabs. No switching. Hard thinking only.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-amber);"></div>
            <div class="tl-time" style="color:var(--accent-amber);">1:30 – 1:45</div>
            <div class="tl-title">Recovery break</div>
            <div class="tl-desc">Walk. Eyes off screen. Let diffuse mode process what you just learned.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot" style="border-color:var(--accent-purple);"></div>
            <div class="tl-time" style="color:var(--accent-purple);">1:45 – 3:00</div>
            <div class="tl-title">Second focus block</div>
            <div class="tl-desc">Harder problems or different concept. Momentum carries forward.</div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- Interleaving -->
  <div class="grid-2">
    <div class="card" style="border-top: 2px solid var(--accent-amber);">
      <div class="card-title" style="color:var(--accent-amber);">Blocked Practice (Wrong)</div>
      <h3>AAAA → BBBB → CCCC</h3>
      <p>Doing all of one topic before moving to next. Feels productive, gives illusion of mastery. But performance drops quickly when tested mixed. The brain learns pattern-matching, not understanding.</p>
    </div>
    <div class="card" style="border-top: 2px solid var(--accent-teal);">
      <div class="card-title" style="color:var(--accent-teal);">Interleaved Practice (Right)</div>
      <h3>ABCABCABC → mastery</h3>
      <p>Mix different problem types and subjects in a single session. Harder. Slower. More frustrating. But durable understanding is significantly higher. The struggle is the signal.</p>
    </div>
  </div>
</div>

<!-- ═══════════════════════════════════════════ -->
<!-- SECTION 05 — FULL STACK                    -->
<!-- ═══════════════════════════════════════════ -->
<div id="stack">
  <div class="section-header">
    <span class="section-num">05</span>
    <h2 class="section-title">The Complete System — Stacked Together</h2>
    <div class="section-line"></div>
    <span class="section-badge tag red">For GATE</span>
  </div>

  <div class="diagram-wrap">
    <p class="timer-label">A daily learning stack that uses all principles</p>

    <div style="display: grid; grid-template-columns: auto 1fr; gap: 0; border: 1px solid var(--border); border-radius: 8px; overflow: hidden;">
      <div style="background:var(--bg4);padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--dim);border-bottom:1px solid var(--border);border-right:1px solid var(--border);">TIME</div>
      <div style="background:var(--bg4);padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:11px;color:var(--dim);border-bottom:1px solid var(--border);">ACTIVITY + PRINCIPLE</div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-blue);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">06:00</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Spaced repetition review</strong> — Anki or written recall of yesterday's material before new content. <span class="tag teal">spaced rep</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-teal);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">07:00</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Deep work block 1</strong> — Hardest concept first. Single topic. No distractions. 90 minutes. <span class="tag purple">deep work</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-amber);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">08:30</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Feynman dump</strong> — Close notes. Write the concept in your own words. Identify gaps. <span class="tag amber">feynman</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--muted);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">09:00</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);">Break — walk, no screens. Diffuse mode processing.</div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-teal);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">09:20</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Deep work block 2</strong> — Interleaved problems (mix topics). Solve without looking. <span class="tag purple">deep work</span> <span class="tag blue">interleaved</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-blue);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">11:00</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Kaizen review</strong> — What was 1% better today? What did you not understand? Log it. <span class="tag amber">kaizen</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--accent-purple);border-bottom:1px solid var(--border);border-right:1px solid var(--border);white-space:nowrap;">Evening</div>
      <div style="padding:12px 16px;font-size:13px;border-bottom:1px solid var(--border);"><strong>Active recall close</strong> — Cover your notes. Answer: "What did I learn today?" from memory only. <span class="tag teal">recall</span></div>

      <div style="padding:12px 16px;font-family:'JetBrains Mono',monospace;font-size:12px;color:var(--dim);border-right:1px solid var(--border);white-space:nowrap;">Night</div>
      <div style="padding:12px 16px;font-size:13px;"><strong>Environment prep</strong> — Lay out tomorrow's problem set. Open the right chapter. Set the ritual. <span class="tag red">activation energy</span></div>
    </div>
  </div>

  <!-- Final callout -->
  <div class="callout amber" style="margin-top: 32px;">
    <p><strong>The meta-principle behind all of this:</strong> Your brain encodes deeply what it struggles to retrieve. Make the studying hard (not impossible). Close the book. Solve without hints. Explain without notes. Teach before you feel ready. The discomfort of active engagement is not a sign you're doing it wrong — it is the signal that real learning is happening.</p>
  </div>

  <div class="grid-4" style="margin-top: 24px;">
    <div class="card" style="text-align:center;">
      <div style="font-size:28px;margin-bottom:8px;">🎯</div>
      <h3 style="font-size:14px;">Feynman</h3>
      <p style="font-size:12px;">Teach it simply to own it deeply</p>
    </div>
    <div class="card" style="text-align:center;">
      <div style="font-size:28px;margin-bottom:8px;">🔁</div>
      <h3 style="font-size:14px;">Spaced Rep</h3>
      <p style="font-size:12px;">Review before forgetting, not after</p>
    </div>
    <div class="card" style="text-align:center;">
      <div style="font-size:28px;margin-bottom:8px;">⚡</div>
      <h3 style="font-size:14px;">Deep Work</h3>
      <p style="font-size:12px;">4h focused &gt; 10h distracted</p>
    </div>
    <div class="card" style="text-align:center;">
      <div style="font-size:28px;margin-bottom:8px;">📈</div>
      <h3 style="font-size:14px;">Kaizen</h3>
      <p style="font-size:12px;">1% daily = 37× in a year</p>
    </div>
  </div>

  <div class="footer">
    <span class="footer-text">// learning_mastery_notes.html</span>
    <span class="footer-text">Feynman · Kaizen · Shu-Ha-Ri · Deep Work · Spaced Rep · Active Recall</span>
  </div>
</div>

</div><!-- /page -->
</body>
</html>
```
