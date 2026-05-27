```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Computer Science Roadmap — From Bits to Beyond</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:ital,wght@0,400;0,700;1,400&family=Syne:wght@400;600;700;800&family=DM+Mono:wght@300;400;500&display=swap');

  :root {
    --bg: #050810;
    --bg2: #080d1a;
    --bg3: #0d1526;
    --line: rgba(255,255,255,0.06);
    --accent1: #00e5ff;
    --accent2: #7b61ff;
    --accent3: #ff6b6b;
    --accent4: #39ff14;
    --accent5: #ffaa00;
    --accent6: #ff4de4;
    --text: #e8eaf2;
    --muted: #6b7a99;
    --glow1: rgba(0,229,255,0.15);
    --glow2: rgba(123,97,255,0.15);

    /* Level colors */
    --c0: #39ff14;   /* Foundations */
    --c1: #00e5ff;   /* Systems */
    --c2: #7b61ff;   /* Theory */
    --c3: #ffaa00;   /* Software Eng */
    --c4: #ff6b6b;   /* Specializations */
    --c5: #ff4de4;   /* Frontier */
    --c6: #ffffff;   /* Future */
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Mono', monospace;
    overflow-x: hidden;
    cursor: crosshair;
  }

  /* Noise overlay */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 9999; opacity: 0.35;
  }

  /* Grid lines background */
  .grid-bg {
    position: fixed; inset: 0; pointer-events: none; z-index: 0;
    background-image:
      linear-gradient(var(--line) 1px, transparent 1px),
      linear-gradient(90deg, var(--line) 1px, transparent 1px);
    background-size: 60px 60px;
    mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 20%, transparent 100%);
  }

  /* HEADER */
  header {
    position: relative; z-index: 10;
    padding: 80px 40px 60px;
    text-align: center;
    border-bottom: 1px solid var(--line);
    overflow: hidden;
  }

  header::after {
    content: '';
    position: absolute; bottom: -1px; left: 50%; transform: translateX(-50%);
    width: 300px; height: 1px;
    background: linear-gradient(90deg, transparent, var(--accent1), transparent);
    box-shadow: 0 0 20px var(--accent1);
  }

  .header-eyebrow {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.3em;
    color: var(--accent1);
    text-transform: uppercase;
    margin-bottom: 20px;
    opacity: 0;
    animation: fadeUp 0.6s ease forwards 0.2s;
  }

  h1 {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: clamp(2.4rem, 6vw, 5rem);
    line-height: 1.05;
    letter-spacing: -0.02em;
    background: linear-gradient(135deg, #fff 0%, var(--accent1) 40%, var(--accent2) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.4s;
  }

  .header-sub {
    margin-top: 16px;
    font-size: 13px;
    color: var(--muted);
    letter-spacing: 0.05em;
    opacity: 0;
    animation: fadeUp 0.7s ease forwards 0.6s;
  }

  /* LEGEND */
  .legend {
    display: flex; flex-wrap: wrap; gap: 10px;
    justify-content: center;
    padding: 30px 40px;
    border-bottom: 1px solid var(--line);
    position: relative; z-index: 10;
  }

  .legend-item {
    display: flex; align-items: center; gap: 8px;
    font-size: 11px;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--muted);
    padding: 6px 14px;
    border: 1px solid var(--line);
    border-radius: 2px;
    transition: all 0.2s;
    cursor: pointer;
  }

  .legend-item:hover { color: var(--text); border-color: rgba(255,255,255,0.2); }

  .legend-dot {
    width: 8px; height: 8px; border-radius: 50%;
    box-shadow: 0 0 6px currentColor;
  }

  /* MAIN LAYOUT */
  main {
    position: relative; z-index: 5;
    max-width: 1400px;
    margin: 0 auto;
    padding: 60px 30px 100px;
  }

  /* PHASE SECTION */
  .phase {
    margin-bottom: 80px;
    opacity: 0;
    transform: translateY(40px);
    transition: opacity 0.7s ease, transform 0.7s ease;
  }

  .phase.visible {
    opacity: 1;
    transform: translateY(0);
  }

  .phase-header {
    display: flex; align-items: baseline; gap: 20px;
    margin-bottom: 30px;
    padding-bottom: 16px;
    border-bottom: 1px solid var(--line);
    position: relative;
  }

  .phase-header::after {
    content: '';
    position: absolute; bottom: -1px; left: 0;
    width: 120px; height: 1px;
    background: var(--phase-color);
    box-shadow: 0 0 10px var(--phase-color);
    transition: width 0.8s ease;
  }

  .phase.visible .phase-header::after { width: 240px; }

  .phase-num {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 0.2em;
    color: var(--phase-color);
    text-transform: uppercase;
  }

  .phase-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(1.2rem, 3vw, 1.8rem);
    font-weight: 700;
    color: var(--text);
  }

  .phase-badge {
    margin-left: auto;
    font-size: 10px;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--phase-color);
    border: 1px solid var(--phase-color);
    padding: 4px 10px;
    border-radius: 2px;
    opacity: 0.7;
    white-space: nowrap;
  }

  /* TOPIC GRID */
  .topic-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 14px;
  }

  /* TOPIC CARD */
  .card {
    background: var(--bg2);
    border: 1px solid var(--line);
    border-radius: 4px;
    padding: 20px;
    position: relative;
    overflow: hidden;
    cursor: default;
    transition: border-color 0.25s, transform 0.25s, background 0.25s;
  }

  .card::before {
    content: '';
    position: absolute; top: 0; left: 0; right: 0;
    height: 2px;
    background: var(--phase-color);
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.35s ease;
  }

  .card:hover {
    border-color: rgba(255,255,255,0.12);
    background: var(--bg3);
    transform: translateY(-3px);
  }

  .card:hover::before { transform: scaleX(1); }

  .card-icon {
    font-size: 20px;
    margin-bottom: 10px;
    display: block;
  }

  .card-title {
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    font-weight: 700;
    color: var(--text);
    margin-bottom: 8px;
    letter-spacing: 0.02em;
  }

  .card-topics {
    list-style: none;
    display: flex; flex-wrap: wrap; gap: 5px;
    margin-top: 10px;
  }

  .card-topics li {
    font-size: 10px;
    letter-spacing: 0.05em;
    color: var(--muted);
    background: rgba(255,255,255,0.04);
    border: 1px solid var(--line);
    padding: 3px 8px;
    border-radius: 2px;
    transition: color 0.2s, border-color 0.2s;
  }

  .card:hover .card-topics li {
    color: rgba(255,255,255,0.6);
    border-color: rgba(255,255,255,0.1);
  }

  .card-desc {
    font-size: 11px;
    color: var(--muted);
    line-height: 1.7;
    margin-top: 6px;
  }

  /* Corner accent */
  .card::after {
    content: '';
    position: absolute;
    bottom: 10px; right: 10px;
    width: 20px; height: 20px;
    border-right: 1px solid var(--phase-color);
    border-bottom: 1px solid var(--phase-color);
    opacity: 0;
    transition: opacity 0.3s;
  }

  .card:hover::after { opacity: 0.4; }

  /* CONNECTOR LINE between phases */
  .connector {
    display: flex; flex-direction: column; align-items: center;
    margin: 0 auto 40px;
    gap: 4px;
    height: 60px;
  }

  .connector-dot {
    width: 6px; height: 6px; border-radius: 50%;
    background: var(--muted);
    animation: pulse 2s ease-in-out infinite;
  }

  .connector-dot:nth-child(2) { animation-delay: 0.3s; }
  .connector-dot:nth-child(3) { animation-delay: 0.6s; }
  .connector-line {
    flex: 1; width: 1px;
    background: linear-gradient(to bottom, var(--from-color), var(--to-color));
    box-shadow: 0 0 8px var(--to-color);
  }

  /* FOOTER */
  footer {
    text-align: center;
    padding: 40px;
    border-top: 1px solid var(--line);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 0.1em;
    position: relative; z-index: 10;
  }

  /* FLOATING PARTICLES */
  .particles {
    position: fixed; inset: 0; pointer-events: none; z-index: 1;
    overflow: hidden;
  }

  .particle {
    position: absolute;
    width: 2px; height: 2px;
    border-radius: 50%;
    background: var(--accent1);
    opacity: 0;
    animation: float linear infinite;
  }

  /* ANIMATIONS */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes pulse {
    0%, 100% { opacity: 0.3; transform: scale(1); }
    50%       { opacity: 1;   transform: scale(1.4); }
  }

  @keyframes float {
    0%   { opacity: 0; transform: translateY(100vh) translateX(0); }
    10%  { opacity: 0.6; }
    90%  { opacity: 0.6; }
    100% { opacity: 0; transform: translateY(-10vh) translateX(30px); }
  }

  /* SCAN LINE */
  @keyframes scan {
    0%   { top: -2px; }
    100% { top: 100%; }
  }

  .scan-line {
    position: fixed; left: 0; right: 0;
    height: 2px;
    background: linear-gradient(90deg, transparent, rgba(0,229,255,0.08), transparent);
    pointer-events: none; z-index: 9998;
    animation: scan 8s linear infinite;
  }

  /* PROGRESS BAR */
  .progress-bar {
    position: fixed; top: 0; left: 0; z-index: 10000;
    height: 2px;
    background: linear-gradient(90deg, var(--accent4), var(--accent1), var(--accent2), var(--accent6));
    box-shadow: 0 0 10px var(--accent1);
    width: 0%;
    transition: width 0.1s linear;
  }

  /* HOVER GLOW on phase titles */
  .phase-title span {
    display: inline-block;
    transition: color 0.3s;
  }

  /* TOOLTIP */
  [data-tip] { position: relative; }
  [data-tip]:hover::before {
    content: attr(data-tip);
    position: absolute;
    bottom: 110%; left: 50%; transform: translateX(-50%);
    background: var(--bg3);
    border: 1px solid var(--line);
    padding: 6px 12px;
    font-size: 10px;
    white-space: nowrap;
    color: var(--text);
    letter-spacing: 0.05em;
    pointer-events: none;
    z-index: 100;
  }

  /* Responsiveness */
  @media (max-width: 600px) {
    header { padding: 50px 20px 40px; }
    main { padding: 40px 16px 60px; }
    .legend { padding: 20px 16px; }
    .topic-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<div class="progress-bar" id="progress"></div>
<div class="scan-line"></div>
<div class="grid-bg"></div>
<div class="particles" id="particles"></div>

<!-- HEADER -->
<header>
  <div class="header-eyebrow">// complete knowledge map · version 2026</div>
  <h1>Computer Science<br>Roadmap</h1>
  <div class="header-sub">From Bits &amp; Logic → Revolutionary Frontier Technologies</div>
</header>

<!-- LEGEND -->
<div class="legend">
  <div class="legend-item"><span class="legend-dot" style="color:var(--c0);background:var(--c0)"></span>Foundations</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c1);background:var(--c1)"></span>Systems</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c2);background:var(--c2)"></span>Theory</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c3);background:var(--c3)"></span>Software Engineering</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c4);background:var(--c4)"></span>Specializations</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c5);background:var(--c5)"></span>Frontier AI / Research</div>
  <div class="legend-item"><span class="legend-dot" style="color:var(--c6);background:var(--c6)"></span>Future Computing</div>
</div>

<main>

<!-- ═══════════════════════════════════ PHASE 0 ═══════════ -->
<section class="phase" style="--phase-color: var(--c0)">
  <div class="phase-header">
    <span class="phase-num">Phase 00</span>
    <h2 class="phase-title">Foundations &amp; Digital Basics</h2>
    <span class="phase-badge">Start Here</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">⚡</span>
      <div class="card-title">What is a Computer?</div>
      <div class="card-desc">Hardware components, electricity as information, how transistors work.</div>
      <ul class="card-topics">
        <li>CPU</li><li>RAM</li><li>Storage</li><li>I/O</li><li>Motherboard</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">🔢</span>
      <div class="card-title">Number Systems</div>
      <div class="card-desc">Binary, octal, hexadecimal. How machines count and represent everything.</div>
      <ul class="card-topics">
        <li>Binary</li><li>Hex</li><li>Octal</li><li>Base Conversion</li><li>2's Complement</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">🔲</span>
      <div class="card-title">Boolean Logic &amp; Gates</div>
      <div class="card-desc">AND, OR, NOT, XOR. Building computation from switches.</div>
      <ul class="card-topics">
        <li>Truth Tables</li><li>Logic Gates</li><li>Combinational</li><li>Karnaugh Maps</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">💾</span>
      <div class="card-title">Data Representation</div>
      <div class="card-desc">How integers, floats, text, images, and sound are encoded in bits.</div>
      <ul class="card-topics">
        <li>ASCII / Unicode</li><li>IEEE 754</li><li>Pixels</li><li>Encoding</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">🖥️</span>
      <div class="card-title">Operating Systems Basics</div>
      <div class="card-desc">What an OS does, files, processes, terminal commands.</div>
      <ul class="card-topics">
        <li>Linux CLI</li><li>File System</li><li>Processes</li><li>Permissions</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c0)">
      <span class="card-icon">📐</span>
      <div class="card-title">Discrete Mathematics</div>
      <div class="card-desc">Sets, logic, relations, functions — the language of CS proofs.</div>
      <ul class="card-topics">
        <li>Set Theory</li><li>Proofs</li><li>Functions</li><li>Relations</li><li>Induction</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c0);--to-color:var(--c1)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 1 ═══════════ -->
<section class="phase" style="--phase-color: var(--c1)">
  <div class="phase-header">
    <span class="phase-num">Phase 01</span>
    <h2 class="phase-title">Programming Fundamentals</h2>
    <span class="phase-badge">Core Skill</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">📝</span>
      <div class="card-title">First Language (C / Python)</div>
      <div class="card-desc">Variables, control flow, functions. The syntax of thought.</div>
      <ul class="card-topics">
        <li>Variables</li><li>Loops</li><li>Functions</li><li>Recursion</li><li>I/O</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">🧱</span>
      <div class="card-title">Data Structures</div>
      <div class="card-desc">Arrays, linked lists, stacks, queues, trees, graphs, hash tables.</div>
      <ul class="card-topics">
        <li>Array</li><li>Linked List</li><li>Stack/Queue</li><li>Trees</li><li>Graphs</li><li>Hash Map</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">⚙️</span>
      <div class="card-title">Algorithms</div>
      <div class="card-desc">Sorting, searching, graph traversal, divide and conquer, greedy, DP.</div>
      <ul class="card-topics">
        <li>Sorting</li><li>BFS/DFS</li><li>Greedy</li><li>Divide &amp; Conquer</li><li>DP</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">📊</span>
      <div class="card-title">Algorithm Analysis</div>
      <div class="card-desc">Big-O, Θ, Ω. Measuring time and space complexity rigorously.</div>
      <ul class="card-topics">
        <li>Big-O</li><li>Recurrences</li><li>Master Theorem</li><li>Amortized</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">🏗️</span>
      <div class="card-title">Object-Oriented Programming</div>
      <div class="card-desc">Classes, encapsulation, polymorphism, inheritance, design patterns.</div>
      <ul class="card-topics">
        <li>Classes</li><li>Inheritance</li><li>Polymorphism</li><li>SOLID</li><li>Patterns</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c1)">
      <span class="card-icon">🔧</span>
      <div class="card-title">Tools of the Trade</div>
      <div class="card-desc">Git, debugging, editors, build systems — professional workflow.</div>
      <ul class="card-topics">
        <li>Git</li><li>GDB/LLDB</li><li>Make</li><li>Valgrind</li><li>VS Code</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c1);--to-color:var(--c2)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 2 ═══════════ -->
<section class="phase" style="--phase-color: var(--c2)">
  <div class="phase-header">
    <span class="phase-num">Phase 02</span>
    <h2 class="phase-title">Computer Systems &amp; Architecture</h2>
    <span class="phase-badge">Deep Layer</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🔩</span>
      <div class="card-title">Computer Architecture</div>
      <div class="card-desc">Von Neumann model, ISA, pipelining, cache, branch prediction.</div>
      <ul class="card-topics">
        <li>ISA</li><li>Pipeline</li><li>Cache</li><li>x86/ARM</li><li>RISC-V</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🔡</span>
      <div class="card-title">Assembly Language</div>
      <div class="card-desc">Talking directly to the CPU. Registers, instructions, stack frames.</div>
      <ul class="card-topics">
        <li>x86 ASM</li><li>Registers</li><li>Stack</li><li>Calling Conv.</li><li>SIMD</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🌀</span>
      <div class="card-title">Operating Systems</div>
      <div class="card-desc">Process scheduling, virtual memory, file systems, concurrency.</div>
      <ul class="card-topics">
        <li>Scheduling</li><li>Virtual Memory</li><li>Semaphores</li><li>FS</li><li>Syscalls</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🔗</span>
      <div class="card-title">Computer Networks</div>
      <div class="card-desc">OSI model, TCP/IP, DNS, HTTP, sockets — how data travels.</div>
      <ul class="card-topics">
        <li>TCP/IP</li><li>DNS</li><li>HTTP/S</li><li>Sockets</li><li>BGP</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🗄️</span>
      <div class="card-title">Database Systems</div>
      <div class="card-desc">Relational algebra, SQL, indexing, transactions, ACID, query planning.</div>
      <ul class="card-topics">
        <li>SQL</li><li>Indexing</li><li>Transactions</li><li>ACID</li><li>B-Trees</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c2)">
      <span class="card-icon">🔐</span>
      <div class="card-title">Systems Security</div>
      <div class="card-desc">Buffer overflows, memory safety, exploits, defenses at system level.</div>
      <ul class="card-topics">
        <li>Buffer Overflow</li><li>ASLR</li><li>Canaries</li><li>ROP</li><li>Sandboxing</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c2);--to-color:var(--c3)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 3 ═══════════ -->
<section class="phase" style="--phase-color: var(--c3)">
  <div class="phase-header">
    <span class="phase-num">Phase 03</span>
    <h2 class="phase-title">Theory of Computation &amp; Mathematics</h2>
    <span class="phase-badge">Rigor Level</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">🤖</span>
      <div class="card-title">Automata Theory</div>
      <div class="card-desc">DFA, NFA, regular languages, pumping lemma. What computers can't do.</div>
      <ul class="card-topics">
        <li>DFA/NFA</li><li>Regex</li><li>CFG</li><li>PDA</li><li>Turing Machine</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">∞</span>
      <div class="card-title">Computability Theory</div>
      <div class="card-desc">Halting problem, reductions, undecidability — limits of algorithms.</div>
      <ul class="card-topics">
        <li>Halting Problem</li><li>Rice's Theorem</li><li>Reductions</li><li>Recursion Th.</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">🏔️</span>
      <div class="card-title">Computational Complexity</div>
      <div class="card-desc">P, NP, NP-Complete, NP-Hard. The deepest open problem in CS.</div>
      <ul class="card-topics">
        <li>P vs NP</li><li>NP-Complete</li><li>Reductions</li><li>PSPACE</li><li>Approximation</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">🎲</span>
      <div class="card-title">Probability &amp; Statistics</div>
      <div class="card-desc">Distributions, Bayes' theorem, expectation, concentration bounds.</div>
      <ul class="card-topics">
        <li>Bayes</li><li>Distributions</li><li>MLE</li><li>Markov Chains</li><li>CLT</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">📐</span>
      <div class="card-title">Linear Algebra</div>
      <div class="card-desc">Vectors, matrices, eigenvalues, SVD — the backbone of modern ML.</div>
      <ul class="card-topics">
        <li>Eigenvalues</li><li>SVD</li><li>PCA</li><li>Matrix Factorization</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c3)">
      <span class="card-icon">📈</span>
      <div class="card-title">Calculus &amp; Optimization</div>
      <div class="card-desc">Derivatives, gradients, convexity, Lagrange multipliers, gradient descent.</div>
      <ul class="card-topics">
        <li>Gradients</li><li>Convexity</li><li>Lagrange</li><li>SGD</li><li>Adam</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c3);--to-color:var(--c4)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 4 ═══════════ -->
<section class="phase" style="--phase-color: var(--c4)">
  <div class="phase-header">
    <span class="phase-num">Phase 04</span>
    <h2 class="phase-title">Software Engineering &amp; Systems Design</h2>
    <span class="phase-badge">Industry Ready</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">🧩</span>
      <div class="card-title">Software Architecture</div>
      <div class="card-desc">Monolith, microservices, event-driven, hexagonal — structuring large systems.</div>
      <ul class="card-topics">
        <li>Microservices</li><li>Event-Driven</li><li>Layered</li><li>CQRS</li><li>DDD</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">🏛️</span>
      <div class="card-title">System Design</div>
      <div class="card-desc">Load balancers, CDNs, caches, queues, sharding — large scale distributed systems.</div>
      <ul class="card-topics">
        <li>CAP Theorem</li><li>Sharding</li><li>CDN</li><li>Rate Limiting</li><li>Kafka</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">☁️</span>
      <div class="card-title">Cloud &amp; DevOps</div>
      <div class="card-desc">AWS/GCP/Azure, containers, Kubernetes, CI/CD, infrastructure as code.</div>
      <ul class="card-topics">
        <li>Docker</li><li>Kubernetes</li><li>Terraform</li><li>CI/CD</li><li>Serverless</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">🔑</span>
      <div class="card-title">Cybersecurity</div>
      <div class="card-desc">Cryptography, PKI, zero-trust, threat modeling, secure coding.</div>
      <ul class="card-topics">
        <li>TLS</li><li>AES/RSA</li><li>OAuth2</li><li>OWASP</li><li>Pentesting</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">🌐</span>
      <div class="card-title">Distributed Systems</div>
      <div class="card-desc">Consensus (Raft/Paxos), consistency models, fault tolerance, distributed transactions.</div>
      <ul class="card-topics">
        <li>Raft</li><li>Paxos</li><li>Eventual Consistency</li><li>2PC</li><li>Gossip</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c4)">
      <span class="card-icon">🧪</span>
      <div class="card-title">Compilers &amp; Languages</div>
      <div class="card-desc">Lexing, parsing, IR, optimization passes, code generation.</div>
      <ul class="card-topics">
        <li>Lexer</li><li>Parser</li><li>AST</li><li>SSA</li><li>LLVM</li><li>JIT</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c4);--to-color:var(--c5)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 5 ═══════════ -->
<section class="phase" style="--phase-color: var(--c5)">
  <div class="phase-header">
    <span class="phase-num">Phase 05</span>
    <h2 class="phase-title">Specializations &amp; Applied Domains</h2>
    <span class="phase-badge">Branch Out</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">🤖</span>
      <div class="card-title">Machine Learning</div>
      <div class="card-desc">Supervised, unsupervised, reinforcement learning. Training, inference, evaluation.</div>
      <ul class="card-topics">
        <li>Regression</li><li>SVM</li><li>Ensemble</li><li>RL</li><li>Feature Eng.</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">🧠</span>
      <div class="card-title">Deep Learning</div>
      <div class="card-desc">CNNs, RNNs, Transformers, backprop, batch norm, modern training techniques.</div>
      <ul class="card-topics">
        <li>CNNs</li><li>Transformers</li><li>Backprop</li><li>Attention</li><li>BatchNorm</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">👁️</span>
      <div class="card-title">Computer Vision</div>
      <div class="card-desc">Image classification, object detection, segmentation, generative models.</div>
      <ul class="card-topics">
        <li>ResNet</li><li>YOLO</li><li>Segmentation</li><li>NeRF</li><li>Diffusion</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">💬</span>
      <div class="card-title">Natural Language Processing</div>
      <div class="card-desc">Tokenization, embeddings, language models, RLHF, RAG pipelines.</div>
      <ul class="card-topics">
        <li>Word2Vec</li><li>BERT</li><li>GPT</li><li>RAG</li><li>RLHF</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">🎮</span>
      <div class="card-title">Computer Graphics &amp; Simulation</div>
      <div class="card-desc">Rendering, shaders, ray tracing, physics engines, VR/AR.</div>
      <ul class="card-topics">
        <li>OpenGL/Vulkan</li><li>Ray Tracing</li><li>GLSL</li><li>Physics Sim</li><li>XR</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">📡</span>
      <div class="card-title">Embedded &amp; IoT</div>
      <div class="card-desc">Microcontrollers, RTOS, bare-metal, sensors, edge computing.</div>
      <ul class="card-topics">
        <li>Arduino/RPi</li><li>RTOS</li><li>Bare Metal C</li><li>MQTT</li><li>Edge ML</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">🔒</span>
      <div class="card-title">Formal Verification</div>
      <div class="card-desc">Model checking, Coq, Lean, type theory — proving programs correct.</div>
      <ul class="card-topics">
        <li>Model Checking</li><li>Coq</li><li>Lean4</li><li>Dependent Types</li><li>SAT/SMT</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">📦</span>
      <div class="card-title">Data Engineering</div>
      <div class="card-desc">Data lakes, pipelines, streaming, warehouses, ETL, Spark, Flink.</div>
      <ul class="card-topics">
        <li>Spark</li><li>Flink</li><li>dbt</li><li>Kafka</li><li>Lakehouse</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c5)">
      <span class="card-icon">🔗</span>
      <div class="card-title">Blockchain &amp; Cryptography</div>
      <div class="card-desc">Distributed consensus, zero-knowledge proofs, smart contracts, post-quantum crypto.</div>
      <ul class="card-topics">
        <li>ZKP</li><li>Ethereum/EVM</li><li>Consensus</li><li>Post-Quantum</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--c5);--to-color:var(--accent6)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 6 ═══════════ -->
<section class="phase" style="--phase-color: var(--accent6)">
  <div class="phase-header">
    <span class="phase-num">Phase 06</span>
    <h2 class="phase-title">Frontier AI &amp; Research Frontiers</h2>
    <span class="phase-badge">Cutting Edge</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">🌟</span>
      <div class="card-title">Large Language Models</div>
      <div class="card-desc">Scaling laws, pretraining, RLHF, Constitutional AI, alignment research.</div>
      <ul class="card-topics">
        <li>Scaling Laws</li><li>Pretraining</li><li>Alignment</li><li>Constitutional AI</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">🎨</span>
      <div class="card-title">Generative AI</div>
      <div class="card-desc">Diffusion models, GANs, VAEs, flow matching, score-based generation.</div>
      <ul class="card-topics">
        <li>Diffusion</li><li>Flow Matching</li><li>GAN</li><li>VAE</li><li>ControlNet</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">🦾</span>
      <div class="card-title">AI Agents &amp; Reasoning</div>
      <div class="card-desc">Tool-use, chain-of-thought, multi-agent systems, embodied AI.</div>
      <ul class="card-topics">
        <li>ReAct</li><li>Tool Use</li><li>Multi-Agent</li><li>CoT</li><li>Embodied</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">🔬</span>
      <div class="card-title">AI for Science</div>
      <div class="card-desc">AlphaFold, protein design, drug discovery, climate modeling, materials AI.</div>
      <ul class="card-topics">
        <li>AlphaFold</li><li>GNNs</li><li>Drug Discovery</li><li>Physics ML</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">⚖️</span>
      <div class="card-title">AI Safety &amp; Ethics</div>
      <div class="card-desc">Alignment, interpretability, robustness, fairness, governance.</div>
      <ul class="card-topics">
        <li>Interpretability</li><li>Robustness</li><li>Fairness</li><li>Governance</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--accent6)">
      <span class="card-icon">🔮</span>
      <div class="card-title">Neuromorphic Computing</div>
      <div class="card-desc">Spiking neural networks, brain-inspired hardware, event-driven processing.</div>
      <ul class="card-topics">
        <li>SNN</li><li>Intel Loihi</li><li>Event Cameras</li><li>Plasticity</li>
      </ul>
    </div>

  </div>
</section>

<div class="connector"><div class="connector-line" style="--from-color:var(--accent6);--to-color:var(--c6)"></div><div class="connector-dot"></div><div class="connector-dot"></div><div class="connector-dot"></div></div>

<!-- ═══════════════════════════════════ PHASE 7 ═══════════ -->
<section class="phase" style="--phase-color: var(--c6)">
  <div class="phase-header">
    <span class="phase-num">Phase 07</span>
    <h2 class="phase-title">Future &amp; Revolutionary Technologies</h2>
    <span class="phase-badge">Beyond Horizon</span>
  </div>
  <div class="topic-grid">

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">⚛️</span>
      <div class="card-title">Quantum Computing</div>
      <div class="card-desc">Qubits, superposition, entanglement, Shor's/Grover's algorithm, quantum ML.</div>
      <ul class="card-topics">
        <li>Qubits</li><li>Shor's Algo</li><li>Grover</li><li>Qiskit</li><li>Error Correction</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">🧬</span>
      <div class="card-title">DNA &amp; Biological Computing</div>
      <div class="card-desc">DNA storage (1 exabyte/gram), molecular computation, synthetic biology.</div>
      <ul class="card-topics">
        <li>DNA Storage</li><li>Molecular Logic</li><li>CRISPR Compute</li><li>BioCircuits</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">💡</span>
      <div class="card-title">Photonic Computing</div>
      <div class="card-desc">Light-based processors, silicon photonics, optical neural networks.</div>
      <ul class="card-topics">
        <li>Silicon Photonics</li><li>Optical NN</li><li>LiDAR</li><li>Integrated Optics</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">🌐</span>
      <div class="card-title">Brain-Computer Interfaces</div>
      <div class="card-desc">Neural decoding, direct cortical interfaces, prosthetics, memory augmentation.</div>
      <ul class="card-topics">
        <li>EEG/ECoG</li><li>Neural Decode</li><li>Neuralink</li><li>Thought2Text</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">🤯</span>
      <div class="card-title">Artificial General Intelligence</div>
      <div class="card-desc">World models, cognitive architectures, causal reasoning, general problem-solving.</div>
      <ul class="card-topics">
        <li>World Models</li><li>Causal AI</li><li>Cognitive Arch.</li><li>Self-Improvement</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">🔷</span>
      <div class="card-title">Topological &amp; Analog Computing</div>
      <div class="card-desc">Non-von Neumann paradigms, memristors, in-memory compute, reservoir computing.</div>
      <ul class="card-topics">
        <li>Memristors</li><li>CIM</li><li>Reservoir</li><li>Analog ML</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">🌌</span>
      <div class="card-title">Post-Silicon Computing</div>
      <div class="card-desc">Carbon nanotubes, 2D materials (graphene), spintronics, 3D ICs.</div>
      <ul class="card-topics">
        <li>CNFET</li><li>Graphene</li><li>Spintronics</li><li>3D ICs</li><li>GaN/SiC</li>
      </ul>
    </div>

    <div class="card" style="--phase-color: var(--c6)">
      <span class="card-icon">♾️</span>
      <div class="card-title">Superintelligence &amp; Alignment</div>
      <div class="card-desc">MIRI-style safety research, decision theory, value alignment, corrigibility.</div>
      <ul class="card-topics">
        <li>Decision Theory</li><li>Corrigibility</li><li>Value Learning</li><li>IRL</li>
      </ul>
    </div>

  </div>
</section>

</main>

<!-- FOOTER -->
<footer>
  <div>COMPUTER SCIENCE ROADMAP &nbsp;·&nbsp; BITS TO BEYOND &nbsp;·&nbsp; 2026</div>
  <div style="margin-top:8px; font-size:10px; letter-spacing:0.2em; opacity:0.4">
    PHASE 00 → PHASE 07 &nbsp;·&nbsp; ~12–15 YEARS OF MASTERY
  </div>
</footer>

<script>
  // Progress bar
  const progress = document.getElementById('progress');
  window.addEventListener('scroll', () => {
    const pct = window.scrollY / (document.body.scrollHeight - window.innerHeight) * 100;
    progress.style.width = pct + '%';
  });

  // Intersection observer for phase animations
  const phases = document.querySelectorAll('.phase');
  const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('visible'); }
    });
  }, { threshold: 0.07 });
  phases.forEach(p => io.observe(p));

  // Particles
  const container = document.getElementById('particles');
  const colors = ['#00e5ff','#7b61ff','#39ff14','#ffaa00','#ff4de4'];

  for (let i = 0; i < 35; i++) {
    const p = document.createElement('div');
    p.className = 'particle';
    const color = colors[Math.floor(Math.random() * colors.length)];
    const left = Math.random() * 100;
    const duration = 15 + Math.random() * 25;
    const delay = Math.random() * 20;
    p.style.cssText = `
      left:${left}%;
      background:${color};
      box-shadow: 0 0 4px ${color};
      animation-duration:${duration}s;
      animation-delay:-${delay}s;
    `;
    container.appendChild(p);
  }

  // Card stagger on hover in grid
  document.querySelectorAll('.topic-grid').forEach(grid => {
    grid.addEventListener('mouseenter', () => {
      const cards = grid.querySelectorAll('.card');
      cards.forEach((c, i) => {
        c.style.transitionDelay = (i * 0.02) + 's';
      });
    });
    grid.addEventListener('mouseleave', () => {
      grid.querySelectorAll('.card').forEach(c => {
        c.style.transitionDelay = '0s';
      });
    });
  });
</script>
</body>
</html>
```
# LINK - [HTML](file:///C:/Users/ayush/Downloads/cs_roadmap.html)
