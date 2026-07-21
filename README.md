# Success-Story
Success Story
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>How I Built a Corporate AI Agent with Zero Code — Using Claude Cowork</title>
  <style>
    :root {
      --gold: #C9A84C;
      --gold-light: #E8C97A;
      --gold-dim: rgba(201,168,76,0.12);
      --dark:  #0A0E14;
      --dark2: #111620;
      --dark3: #181E2A;
      --border: #252D3D;
      --text:  #E4ECF7;
      --muted: #7A8899;
      --green: #3FB950;
      --blue:  #58A6FF;
      --red:   #F85149;
    }
    *, *::before, *::after { margin:0; padding:0; box-sizing:border-box; }
    html { scroll-behavior: smooth; }
    body {
      background: var(--dark);
      color: var(--text);
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
      line-height: 1.75;
      overflow-x: hidden;
    }

    /* ── CONFIDENTIALITY BANNER ── */
    .conf-banner {
      background: rgba(201,168,76,0.08);
      border-bottom: 1px solid rgba(201,168,76,0.2);
      text-align: center;
      padding: 10px 24px;
      font-size: 11px;
      font-weight: 700;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--gold);
    }

    /* ── HERO ── */
    .hero {
      position: relative;
      background: linear-gradient(160deg, #0A0E14 0%, #111A28 55%, #0A1520 100%);
      border-bottom: 1px solid var(--border);
      padding: 90px 40px 70px;
      text-align: center;
      overflow: hidden;
    }
    .hero::before {
      content:'';
      position:absolute; top:-180px; left:50%; transform:translateX(-50%);
      width:800px; height:800px;
      background: radial-gradient(circle, rgba(201,168,76,0.09) 0%, transparent 65%);
      pointer-events:none;
    }
    .hero::after {
      content:'';
      position:absolute; bottom:-1px; left:0; right:0; height:1px;
      background: linear-gradient(90deg, transparent, var(--gold), transparent);
    }

    .platform-tag {
      display:inline-flex; align-items:center; gap:8px;
      background: rgba(201,168,76,0.1);
      border: 1px solid rgba(201,168,76,0.3);
      border-radius: 30px;
      padding: 7px 18px;
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 1.5px;
      text-transform: uppercase;
      color: var(--gold-light);
      margin-bottom: 28px;
    }
    .platform-tag .cowork-dot {
      width:8px; height:8px; border-radius:50%;
      background: var(--gold);
      animation: breathe 2.5s ease-in-out infinite;
    }
    @keyframes breathe { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:.5;transform:scale(0.7)} }

    .hero h1 {
      font-size: clamp(26px, 4.5vw, 56px);
      font-weight: 900;
      line-height: 1.12;
      max-width: 900px;
      margin: 0 auto 22px;
      background: linear-gradient(145deg, #E4ECF7 0%, var(--gold-light) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }
    .hero-sub {
      font-size: 18px;
      color: var(--muted);
      max-width: 640px;
      margin: 0 auto 44px;
    }
    .hero-chips {
      display:flex; justify-content:center; flex-wrap:wrap; gap:14px;
    }
    .chip {
      background: var(--dark3);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 8px 16px;
      font-size: 13px;
      color: var(--muted);
      display:flex; align-items:center; gap:6px;
    }
    .chip strong { color: var(--text); }

    /* ── LAYOUT ── */
    .wrap { max-width:1020px; margin:0 auto; padding:0 32px; }

    /* ── SECTION ── */
    .section { padding: 76px 0; border-bottom: 1px solid var(--border); }
    .eyebrow {
      font-size: 10px; font-weight:800; letter-spacing:3px;
      text-transform:uppercase; color:var(--gold);
      margin-bottom:10px;
    }
    .section-title {
      font-size: clamp(22px, 3vw, 32px);
      font-weight:800; margin-bottom: 36px;
      line-height:1.25;
    }

    /* ── PROBLEM / SOLUTION ── */
    .ps-grid {
      display:grid; grid-template-columns:1fr 1fr; gap:24px;
    }
    .ps-card {
      background: var(--dark2);
      border: 1px solid var(--border);
      border-radius:14px;
      padding:28px;
    }
    .ps-card.problem { border-top: 3px solid var(--red); }
    .ps-card.solution { border-top: 3px solid var(--green); }
    .ps-card h3 {
      font-size:15px; font-weight:700; margin-bottom:14px;
      display:flex; align-items:center; gap:8px;
    }
    .ps-card ul { list-style:none; }
    .ps-card ul li {
      font-size:14px; color:var(--muted);
      padding: 9px 0;
      border-bottom: 1px solid var(--border);
      display:flex; gap:10px; align-items:flex-start;
    }
    .ps-card ul li:last-child { border-bottom:none; }
    .ps-card ul li .ico { flex-shrink:0; margin-top:2px; }

    /* ── HOW COWORK MADE IT POSSIBLE ── */
    .cowork-steps {
      display:grid; grid-template-columns: repeat(3, 1fr); gap:20px;
      margin-top:36px;
    }
    .step-card {
      background:var(--dark2);
      border:1px solid var(--border);
      border-radius:12px;
      padding:24px;
      position:relative;
    }
    .step-num {
      position:absolute; top:18px; right:18px;
      font-size:36px; font-weight:900;
      color: rgba(201,168,76,0.1);
      line-height:1;
    }
    .step-card h4 { font-size:15px; font-weight:700; margin-bottom:8px; }
    .step-card p  { font-size:14px; color:var(--muted); line-height:1.6; }
    .step-icon { font-size:26px; margin-bottom:14px; }

    /* ── SKILLS ARCHITECTURE ── */
    .skills-arch {
      background: var(--dark2);
      border:1px solid var(--border);
      border-radius:16px;
      padding:36px;
      margin-top:36px;
    }
    .arch-title {
      font-size:14px; font-weight:700;
      color:var(--muted); text-transform:uppercase;
      letter-spacing:2px; margin-bottom:28px;
      text-align:center;
    }

    /* Pyramid */
    .pyramid { display:flex; flex-direction:column; gap:10px; align-items:center; }
    .pyr-row {
      display:flex; gap:10px; justify-content:center; flex-wrap:wrap;
    }
    .pyr-box {
      background:var(--dark3);
      border:1px solid var(--border);
      border-radius:9px;
      padding:13px 20px;
      font-size:13px; font-weight:700;
      text-align:center;
      min-width:160px;
      transition:border-color .2s, background .2s;
    }
    .pyr-box:hover {
      border-color:rgba(201,168,76,.4);
      background:rgba(201,168,76,.06);
    }
    .pyr-box .skill-role {
      font-size:10px; font-weight:600; color:var(--muted);
      text-transform:uppercase; letter-spacing:1px;
      margin-top:3px;
    }
    .pyr-box.top    { border-color:rgba(201,168,76,.5); background:rgba(201,168,76,.08); }
    .pyr-box.gov    { border-color:rgba(248,81,73,.35);  background:rgba(248,81,73,.05); }
    .pyr-box.worker { }
    .pyr-arrow { color:var(--muted); font-size:20px; text-align:center; }

    /* ── AGENT FLEET ── */
    .fleet-grid {
      display:grid; grid-template-columns:repeat(auto-fit, minmax(290px,1fr));
      gap:18px; margin-top:36px;
    }
    .agent {
      background:var(--dark2); border:1px solid var(--border);
      border-radius:12px; padding:24px;
      position:relative; overflow:hidden;
      transition:transform .2s, border-color .2s;
    }
    .agent:hover { transform:translateY(-3px); border-color:rgba(201,168,76,.35); }
    .agent::before {
      content:''; position:absolute; top:0; left:0; right:0; height:3px;
      background:linear-gradient(90deg, var(--gold), transparent);
      opacity:0; transition:opacity .2s;
    }
    .agent:hover::before { opacity:1; }
    .agent-emoji { font-size:28px; margin-bottom:12px; }
    .agent-name  { font-size:15px; font-weight:700; margin-bottom:2px; }
    .agent-role  { font-size:11px; color:var(--gold); font-weight:700;
                   text-transform:uppercase; letter-spacing:1px; margin-bottom:12px; }
    .agent-desc  { font-size:14px; color:var(--muted); line-height:1.6; }
    .agent-badge {
      display:inline-block; margin-top:12px;
      font-size:10px; font-weight:700; letter-spacing:1px;
      text-transform:uppercase; padding:3px 9px; border-radius:5px;
    }
    .badge-green { background:rgba(63,185,80,.1); border:1px solid rgba(63,185,80,.25); color:var(--green); }
    .badge-gold  { background:rgba(201,168,76,.1); border:1px solid rgba(201,168,76,.25); color:var(--gold); }
    .badge-blue  { background:rgba(88,166,255,.1); border:1px solid rgba(88,166,255,.25); color:var(--blue); }

    /* ── RESULTS ── */
    .results-section { padding:76px 0; border-bottom:1px solid var(--border); }
    .results-grid {
      display:grid; grid-template-columns:repeat(auto-fit, minmax(200px,1fr));
      gap:18px; margin-top:36px;
    }
    .result-card {
      background:var(--dark2); border:1px solid var(--border);
      border-radius:12px; padding:26px 20px;
      text-align:center; position:relative; overflow:hidden;
    }
    .result-card::after {
      content:''; position:absolute; bottom:0; left:0; right:0; height:2px;
      background:linear-gradient(90deg, transparent, var(--gold), transparent);
    }
    .result-num {
      font-size:42px; font-weight:900; display:block; margin-bottom:6px;
      background:linear-gradient(135deg, var(--gold), var(--gold-light));
      -webkit-background-clip:text; -webkit-text-fill-color:transparent;
      background-clip:text;
    }
    .result-label { font-size:13px; color:var(--muted); line-height:1.5; }

    /* ── COMMAND PROTOCOL ── */
    .protocol-section { padding:76px 0; border-bottom:1px solid var(--border); }
    .cmd-grid { display:grid; grid-template-columns:1fr 1fr; gap:16px; margin-top:36px; }
    .cmd-card {
      background:var(--dark2); border:1px solid var(--border);
      border-radius:10px; padding:20px 22px;
      display:flex; gap:16px; align-items:flex-start;
    }
    .cmd-label {
      font-family:monospace; font-size:13px; font-weight:700;
      color:var(--gold); background:rgba(201,168,76,.1);
      border:1px solid rgba(201,168,76,.25); border-radius:6px;
      padding:5px 12px; white-space:nowrap; flex-shrink:0; margin-top:2px;
    }
    .cmd-card h4 { font-size:14px; font-weight:700; margin-bottom:4px; }
    .cmd-card p  { font-size:13px; color:var(--muted); line-height:1.5; }

    /* ── QUOTE ── */
    .quote-block {
      background:linear-gradient(135deg, rgba(201,168,76,.07), rgba(201,168,76,.02));
      border:1px solid rgba(201,168,76,.2); border-radius:16px;
      padding:44px 40px; margin:60px 0; text-align:center;
    }
    .quote-mark { font-size:64px; color:var(--gold); opacity:.25; line-height:1; }
    blockquote {
      font-size:clamp(17px,2.5vw,23px); font-weight:600; font-style:italic;
      color:var(--text); max-width:700px; margin:0 auto 14px; line-height:1.5;
    }
    cite { font-size:13px; color:var(--muted); font-style:normal; }

    /* ── BEFORE/AFTER ── */
    .before-after { display:grid; grid-template-columns:1fr 1fr; gap:20px; margin-top:36px; }
    .ba-card { background:var(--dark2); border:1px solid var(--border); border-radius:12px; padding:26px; }
    .ba-card.before { border-top:3px solid var(--red); }
    .ba-card.after  { border-top:3px solid var(--green); }
    .ba-label { font-size:11px; font-weight:800; letter-spacing:2px; text-transform:uppercase; margin-bottom:16px; }
    .ba-card.before .ba-label { color:var(--red); }
    .ba-card.after  .ba-label { color:var(--green); }
    .ba-card p { font-size:14px; color:var(--muted); margin-bottom:10px; display:flex; gap:10px; }
    .ba-card p:last-child { margin-bottom:0; }

    /* ── WHAT COWORK ENABLES ── */
    .enable-list { list-style:none; margin-top:28px; }
    .enable-list li {
      padding:20px 0; border-bottom:1px solid var(--border);
      display:flex; gap:18px; align-items:flex-start;
    }
    .enable-list li:last-child { border-bottom:none; }
    .enable-icon {
      width:40px; height:40px; border-radius:10px;
      background:rgba(201,168,76,.1); border:1px solid rgba(201,168,76,.2);
      display:flex; align-items:center; justify-content:center;
      font-size:18px; flex-shrink:0;
    }
    .enable-list h4 { font-size:16px; font-weight:700; margin-bottom:4px; }
    .enable-list p  { font-size:14px; color:var(--muted); }

    /* ── CLOSING ── */
    .closing { padding:90px 0; text-align:center; }
    .closing h2 {
      font-size:clamp(24px, 4vw, 42px); font-weight:900; margin-bottom:16px;
      background:linear-gradient(135deg, var(--text) 0%, var(--gold-light) 100%);
      -webkit-background-clip:text; -webkit-text-fill-color:transparent;
      background-clip:text; line-height:1.2;
    }
    .closing p { font-size:17px; color:var(--muted); max-width:560px; margin:0 auto 36px; }
    .cta-row { display:flex; justify-content:center; gap:14px; flex-wrap:wrap; }
    .btn { display:inline-block; padding:13px 26px; border-radius:9px; font-size:14px; font-weight:700; text-decoration:none; transition:all .2s; cursor:pointer; }
    .btn-gold { background:linear-gradient(135deg, var(--gold), var(--gold-light)); color:#0A0E14; }
    .btn-ghost { background:transparent; border:1px solid var(--border); color:var(--text); }
    .btn:hover { transform:translateY(-2px); box-shadow:0 10px 28px rgba(201,168,76,.18); }

    /* ── FOOTER ── */
    footer {
      border-top:1px solid var(--border);
      padding:22px 32px;
      display:flex; justify-content:space-between; align-items:center;
      flex-wrap:wrap; gap:10px;
      font-size:12px; color:var(--muted);
    }
    footer strong { color:var(--gold); }
    .watermark { font-size:11px; letter-spacing:1px; text-transform:uppercase; }

    /* ── RESPONSIVE ── */
    @media (max-width:740px) {
      .ps-grid, .cowork-steps, .cmd-grid, .before-after, .cowork-steps { grid-template-columns:1fr; }
      .hero { padding:60px 22px 50px; }
      .wrap { padding:0 18px; }
      .skills-arch { padding:22px; }
      footer { flex-direction:column; text-align:center; }
    }
  </style>
</head>
<body>

<!-- ── BANNER ── -->
<div class="conf-banner">
  ✦ Outbound / Shared · Tier A · All commercial & client data redacted per AES Confidentiality Protocol v1.0 ✦
</div>

<!-- ══════════════════════ HERO ══════════════════════ -->
<header class="hero">
  <div class="platform-tag"><span class="cowork-dot"></span> Built on Claude Cowork · Anthropic</div>
  <h1>How a Construction Engineer Built a Production-Grade Corporate AI Agent — With Zero Code</h1>
  <p class="hero-sub">A real-world story of using Claude Cowork's skill-based architecture to automate one of the most complex workflows in enterprise construction tendering</p>
  <div class="hero-chips">
    <div class="chip">🏗 <strong>Top-Tier MENA Contractor</strong> · Enterprise Scale</div>
    <div class="chip">🌊 <strong>Major Infrastructure</strong> · Live Tender</div>
    <div class="chip">⚙ <strong>6 Agents Deployed</strong> · Live Tender Cycle</div>
    <div class="chip">💻 <strong>0 Lines of Code</strong> Written by the Architect</div>
  </div>
</header>

<!-- ══════════════════════ CONTEXT ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">The Scale · The Company · The Problem</div>
    <h2 class="section-title">Enterprise Construction at Scale — And Its Hardest Problem</h2>

    <p style="color:var(--muted); font-size:16px; max-width:800px; margin-bottom:36px;">
      The organisation is one of the largest engineering and construction companies in the Middle East and North Africa. It bids on some of the region's most complex infrastructure projects — marine terminals, highways, industrial facilities, power plants — often running multiple large tenders simultaneously. Winning or losing a bid can represent hundreds of millions of dollars. The estimation department is where those bids are made or broken.
    </p>

    <div class="ps-grid">
      <div class="ps-card problem">
        <h3><span>🔴</span> The Problem: Manual Estimation at Enterprise Scale</h3>
        <ul>
          <li><span class="ico">📦</span> Tender packages arrive as thousands of pages split across ZIP archives of JPEG scans — not searchable, not extractable, not machine-readable</li>
          <li><span class="ico">🏢</span> Eight technical departments must coordinate simultaneously on a single tender — civil, marine, MEP, structural, finishing, utilities, procurement, and preliminaries</li>
          <li><span class="ico">💰</span> Rates are looked up manually from historical files with no traceability — no record of which file, which row, which supplier quote was used</li>
          <li><span class="ico">📋</span> Addenda (revised tender documents) force a full re-review of work — no way to isolate only what changed</li>
          <li><span class="ico">⏱</span> Submission deadlines are fixed — if the team falls behind on extraction and analysis, quality is sacrificed</li>
          <li><span class="ico">🔒</span> Subcontractor pricing must remain strictly siloed — one supplier's rates can never leak to another during the bid</li>
        </ul>
      </div>
      <div class="ps-card solution">
        <h3><span>🟢</span> The Solution: AES Agent-1 — Prompt-Engineered on Cowork</h3>
        <ul>
          <li><span class="ico">🤖</span> A family of six specialized AI agents, each with a defined role, governed by a versioned rule-set — built entirely through Claude Cowork skills</li>
          <li><span class="ico">🔁</span> A sprint loop from document intake to Version 0 deliverable set — automated orchestration, human decision points only</li>
          <li><span class="ico">📍</span> Cell-level rate provenance — every rate lookup shows the exact source file, sheet, and row. Rates are never adopted by the agent — only by the engineer</li>
          <li><span class="ico">⚡</span> Addendum delta engine — computes only what changed, patches only the affected line items. Zero baseline restarts</li>
          <li><span class="ico">🛡</span> A governing confidentiality protocol that acts as the output gate for every deliverable — Tier A / B / C classification with automatic redaction before any external issue</li>
          <li><span class="ico">💡</span> Five command interface: RUN · AUDIT · STATUS · PROMOTE · ADDENDUM. One command in = one complete sprint out</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ HOW COWORK MADE IT POSSIBLE ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">The Platform · Claude Cowork</div>
    <h2 class="section-title">Why Cowork — Not Code — Was the Right Tool</h2>
    <p style="color:var(--muted); font-size:16px; max-width:800px; margin-bottom:0;">
      Most AI automation in construction requires developers, APIs, and months of custom engineering. Claude Cowork changed the equation. The AES agent wasn't built by a software team — it was built by an estimation engineer who understood the domain deeply enough to write precise rules.
    </p>

    <div class="cowork-steps">
      <div class="step-card">
        <div class="step-num">01</div>
        <div class="step-icon">📝</div>
        <h4>Skills Replace Code</h4>
        <p>Instead of writing Python scripts, each agent capability is a Skill — a structured set of rules, behaviours, and constraints written in plain language. Precise enough to be enforced. Human-readable enough to be audited. No compiler required.</p>
      </div>
      <div class="step-card">
        <div class="step-num">02</div>
        <div class="step-icon">🔗</div>
        <h4>Connectors Replace Integrations</h4>
        <p>Google Drive, Gmail, Google Calendar — connected in seconds through Cowork's connector panel. The agent can read tender files from Drive, send status updates, and track deadlines without a single API call written by the engineer.</p>
      </div>
      <div class="step-card">
        <div class="step-num">03</div>
        <div class="step-icon">🧠</div>
        <h4>Projects Replace Memory</h4>
        <p>The Claude Project holds the entire system context across sessions — the Blueprint, the Sprint State, the agent skills, the decision log. Every new session recovers state automatically. No database, no session management code needed.</p>
      </div>
      <div class="step-card">
        <div class="step-num">04</div>
        <div class="step-icon">📋</div>
        <h4>Tasks Replace Project Management</h4>
        <p>Sprint progress is tracked through Cowork's built-in task system — visible in real-time as agents work through extraction, rate lookup, cost build-up, and gate checks. The engineer sees exactly where the sprint is without opening a project management tool.</p>
      </div>
      <div class="step-card">
        <div class="step-num">05</div>
        <div class="step-icon">🏛</div>
        <h4>The Project IS the Governance Layer</h4>
        <p>Version control, rule amendments, state blocks, confidentiality gates — everything lives in the Project. The system governs itself through its own documentation. When a rule changes, the Project is updated and the change takes effect immediately for every agent in the family.</p>
      </div>
      <div class="step-card">
        <div class="step-num">06</div>
        <div class="step-icon">🚀</div>
        <h4>Domain Expertise IS the Architecture</h4>
        <p>The AES system's competitive advantage isn't its technology stack — it's the depth of tendering knowledge encoded into it. Cowork didn't replace that expertise. It gave it a runtime. Anyone in construction with deep domain knowledge can build this.</p>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ SKILLS ARCHITECTURE ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">Technical Architecture · Skills Stack</div>
    <h2 class="section-title">The Skills That Power the Agent — No Code, All Rules</h2>
    <p style="color:var(--muted); font-size:16px; max-width:800px; margin-bottom:0;">
      Each skill is a self-contained governance document — defining what the agent does, what it must never do, what stays blank until the human decides, and when it fires. The stack is layered: a governing protocol above everything, an orchestrator in the middle, workers below.
    </p>

    <div class="skills-arch">
      <div class="arch-title">AES Agent-1 · Skills Architecture</div>
      <div class="pyramid">

        <div class="pyr-row">
          <div class="pyr-box gov">
            🛡 Confidentiality Protocol v1.0
            <div class="skill-role">Governing Layer · All Outputs Pass Through Here</div>
          </div>
        </div>

        <div class="pyr-arrow">↑ gates every output ↑</div>

        <div class="pyr-row">
          <div class="pyr-box top">
            🧠 Agent Alpha v4.0
            <div class="skill-role">Orchestrator · Sprint Loop · Gate Checks</div>
          </div>
        </div>

        <div class="pyr-arrow">↑ calls workers ↑</div>

        <div class="pyr-row">
          <div class="pyr-box worker">💰 Alpha-2 v1.2<div class="skill-role">Rate Lookup</div></div>
          <div class="pyr-box worker">🔢 Alpha-3<div class="skill-role">Cost Engine</div></div>
          <div class="pyr-box worker">⚡ ADD 1.0<div class="skill-role">Addendum Delta</div></div>
        </div>

        <div class="pyr-row">
          <div class="pyr-box worker">📦 BOQ Digitalisation<div class="skill-role">Document → Excel</div></div>
          <div class="pyr-box worker">📐 Takeoff Engine<div class="skill-role">Quantity Extraction</div></div>
          <div class="pyr-box worker">📋 RFQ Procurement<div class="skill-role">Supplier Packages</div></div>
        </div>

        <div class="pyr-arrow">↑ all rooted in ↑</div>

        <div class="pyr-row">
          <div class="pyr-box" style="border-color:rgba(88,166,255,.35); background:rgba(88,166,255,.05); min-width:300px;">
            📄 AES Blueprint v1.3 · Versioned Governance Document
            <div class="skill-role">Source of Truth · Rules · Enforcement Classes · Sprint Protocol</div>
          </div>
        </div>

      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ AGENT FLEET ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">The Fleet · Six Specialized Agents</div>
    <h2 class="section-title">Each Agent Has One Job — And Is Not Allowed to Do Anyone Else's</h2>

    <div class="fleet-grid">
      <div class="agent">
        <div class="agent-emoji">🧠</div>
        <div class="agent-name">Agent Alpha v4.0</div>
        <div class="agent-role">Core Orchestrator</div>
        <div class="agent-desc">The sprint loop. Recovers state automatically, sequences all workers, runs Proof-of-Read handshakes on source documents, manages six gate checks (G-01 → G-06), and delivers the full Version 0 deliverable set. Self-orchestrates everything from a single RUN command.</div>
        <span class="agent-badge badge-gold">Primary Agent</span>
      </div>

      <div class="agent">
        <div class="agent-emoji">💰</div>
        <div class="agent-name">Agent Alpha-2 v1.2</div>
        <div class="agent-role">Rate Lookup · Cell-Level Provenance</div>
        <div class="agent-desc">Searches the engineer's historical rate library and returns the exact source row, file name, sheet, and price spread — never a single number without its origin. Runs supplier comparisons side-by-side. Rate adoption is always the engineer's decision, never the agent's.</div>
        <span class="agent-badge badge-blue">Data Agent</span>
      </div>

      <div class="agent">
        <div class="agent-emoji">🔢</div>
        <div class="agent-name">Agent Alpha-3</div>
        <div class="agent-role">Cost Engine · First Principles Build-Up</div>
        <div class="agent-desc">Constructs unit rates from components: material + waste factor + labour × productivity norm + plant + subcontract. Calculates escalation from published construction indices. Every input is either confirmed from a cited source or left blank pending engineer adoption. No guessed numbers, ever.</div>
        <span class="agent-badge badge-blue">Compute Agent</span>
      </div>

      <div class="agent">
        <div class="agent-emoji">⚡</div>
        <div class="agent-name">ADD 1.0 v1.1</div>
        <div class="agent-role">Addendum Delta Engine</div>
        <div class="agent-desc">When a revised tender package arrives, ADD 1.0 compares it to the baseline, isolates exactly what changed, and produces a surgical patch list. Only the affected deliverables and line items re-open. The rest of the sprint stays frozen. Zero baseline restarts.</div>
        <span class="agent-badge badge-green">Delta Agent</span>
      </div>

      <div class="agent">
        <div class="agent-emoji">📦</div>
        <div class="agent-name">BOQ Digitalisation Skill</div>
        <div class="agent-role">Document Converter</div>
        <div class="agent-desc">Transforms scanned, non-searchable BOQ documents — including ZIP archives of JPEG images — into formula-live Excel workbooks with discipline-named sheets, yellow rate-input cells, and auto-calculating amount columns. Handles Arabic content. One command, a structured workbook.</div>
        <span class="agent-badge badge-blue">Conversion Agent</span>
      </div>

      <div class="agent">
        <div class="agent-emoji">📐</div>
        <div class="agent-name">Quantity Takeoff Engine</div>
        <div class="agent-role">Measurement Extraction</div>
        <div class="agent-desc">Extracts quantities from drawings and specifications with full source traceability per item. BOQ sovereignty is absolute — takeoff quantities never override the tender's own BOQ without an explicit engineer instruction. Outputs per-discipline with named source references.</div>
        <span class="agent-badge badge-blue">Measurement Agent</span>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ COMMAND PROTOCOL ══════════════════════ -->
<section class="protocol-section">
  <div class="wrap">
    <div class="eyebrow">The Interface · Command Protocol v1.0</div>
    <h2 class="section-title">Five Commands. One Engineer. One Complete Sprint.</h2>
    <p style="color:var(--muted); font-size:16px; max-width:800px; margin-bottom:0;">
      The final design insight: the engineer's vocabulary is <em>decisions</em>, not instructions. The agent self-orchestrates everything — state recovery, skill selection, extraction, generation, gate checks — inside a single turn. The engineer only speaks at decision points.
    </p>
    <div class="cmd-grid">
      <div class="cmd-card">
        <div class="cmd-label">RUN</div>
        <div>
          <h4>Full Sprint Execution</h4>
          <p>One command triggers the entire pipeline: state recovery → source re-read → extraction → rate lookup → deliverable generation → gate checks → checkpoint. No orchestration questions, ever.</p>
        </div>
      </div>
      <div class="cmd-card">
        <div class="cmd-label">AUDIT</div>
        <div>
          <h4>Decision Input</h4>
          <p>The engineer's corrections, adopted rates, RFI answers, rejections — in any format. The agent parses them into structured audit points, confirms the parse, applies on the next RUN. The engineer never reformats their own notes.</p>
        </div>
      </div>
      <div class="cmd-card">
        <div class="cmd-label">STATUS</div>
        <div>
          <h4>10-Line Situational Report</h4>
          <p>Current state, what's blocking convergence, what decision is awaited — in ten lines maximum. No essays. No re-narration of the method. Pure situational awareness.</p>
        </div>
      </div>
      <div class="cmd-card">
        <div class="cmd-label">PROMOTE</div>
        <div>
          <h4>Version 0 Issue Gate</h4>
          <p>Only valid when the agent has declared convergence. Runs the full split gate — machine checks (pass/fail itemized) + judgment score. Only if green does Version 0 issue. The engineer never promotes without the gate passing.</p>
        </div>
      </div>
      <div class="cmd-card" style="grid-column: 1 / -1;">
        <div class="cmd-label">ADDENDUM</div>
        <div>
          <h4>Revised Package Processing</h4>
          <p>Hands the revised document set to ADD 1.0. Computes the delta against the active baseline. Produces a surgical patch list. The next RUN consumes the patches automatically — only the affected line items re-open, everything else stays frozen. No manual re-review of unchanged scope.</p>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ BEFORE / AFTER ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">The Transformation</div>
    <h2 class="section-title">Before AES Agent-1 vs. After</h2>
    <div class="before-after">
      <div class="ba-card before">
        <div class="ba-label">❌ Before · Manual Process</div>
        <p><span>📄</span> BOQ documents printed or opened as scans — manually tabulated into Excel cell by cell</p>
        <p><span>🔍</span> Rates looked up from memory or by searching through multiple historical Excel files with no standardised structure</p>
        <p><span>🔄</span> Addendum arrives → full re-review of all affected items → risk of missing something in the delta</p>
        <p><span>💬</span> Eight departments coordinated via email chains and shared folder versions with no clear state tracking</p>
        <p><span>🔒</span> Confidentiality managed by convention — no systematic check before any outbound document is issued</p>
        <p><span>⏳</span> Sprint from intake to Version 0 takes days of manual effort; deadline pressure compresses QA</p>
      </div>
      <div class="ba-card after">
        <div class="ba-label">✅ After · AES Agent-1 on Cowork</div>
        <p><span>📦</span> ZIP-of-JPEG archives extracted and structured into formula-live Excel workbooks automatically — one command</p>
        <p><span>📍</span> Every rate returned with its exact source row, file, sheet, and price range — cell-level provenance, not memory</p>
        <p><span>⚡</span> Addendum arrives → ADD 1.0 computes delta → only changed items re-open → sprint continues from the checkpoint</p>
        <p><span>📋</span> Sprint state tracked in the Project — any session, any device, agent recovers exactly where the last session ended</p>
        <p><span>🛡</span> Every output passes the confidentiality gate before delivery — Tier A redaction automatic, never skippable</p>
        <p><span>🚀</span> Version 0 deliverable set — Clarification Request, Technical Index, Project Summary, Kick-Off Deck, Base QS — produced in a single sprint cycle</p>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ RESULTS ══════════════════════ -->
<section class="results-section">
  <div class="wrap">
    <div class="eyebrow">Measured Results · Live Production</div>
    <h2 class="section-title" style="margin-bottom:0;">What the System Has Delivered on a Live Marine Infrastructure Tender</h2>
    <p style="color:var(--muted); font-size:15px; margin-top:12px; margin-bottom:0; max-width:800px;">
      A large-scale infrastructure tender was the first live production run of AES Agent-1. Numbers below reflect the first active tender cycle.
    </p>
    <div class="results-grid">
      <div class="result-card">
        <span class="result-num">6</span>
        <div class="result-label">Specialized agents deployed across a single tender cycle — each with a distinct, non-overlapping role</div>
      </div>
      <div class="result-card">
        <span class="result-num">5</span>
        <div class="result-label">Version 0 deliverables produced per sprint cycle from intake to signed-off output</div>
      </div>
      <div class="result-card">
        <span class="result-num">8</span>
        <div class="result-label">Technical departments coordinated through a single structured state block — no email coordination needed</div>
      </div>
      <div class="result-card">
        <span class="result-num">3</span>
        <div class="result-label">Suppliers compared in a single normalized workbook — with spec-conformance analysis against project drawings</div>
      </div>
      <div class="result-card">
        <span class="result-num">4</span>
        <div class="result-label">Addendum documents processed through delta-only impact pass — zero full baseline restarts required</div>
      </div>
      <div class="result-card">
        <span class="result-num">0</span>
        <div class="result-label">Outbound documents issued without passing the confidentiality gate — 100% systematic coverage</div>
      </div>
      <div class="result-card">
        <span class="result-num">v4.0</span>
        <div class="result-label">Blueprint iterations — each version fixing a real production failure, not a hypothetical edge case</div>
      </div>
      <div class="result-card">
        <span class="result-num">0</span>
        <div class="result-label">Lines of code written by the system's architect. Built entirely through skill design and rule engineering on Cowork</div>
      </div>
    </div>
  </div>
</section>

<!-- ══════════════════════ QUOTE ══════════════════════ -->
<div class="wrap">
  <div class="quote-block">
    <div class="quote-mark">"</div>
    <blockquote>
      Cowork didn't replace my estimation expertise — it gave it a runtime. The intelligence in the system isn't in the platform. It's in the rules I was precise enough to write. That's what any senior construction professional can do, if they think in systems instead of syntax.
    </blockquote>
    <cite>— Alaa El-Sebaie · Estimation Engineer · AES Agent-1 Architect</cite>
  </div>
</div>

<!-- ══════════════════════ WHAT COWORK ENABLES ══════════════════════ -->
<section class="section">
  <div class="wrap">
    <div class="eyebrow">The Broader Point · Corporate AI</div>
    <h2 class="section-title">What This Proves for Every Large Enterprise Using Claude Cowork</h2>
    <ul class="enable-list">
      <li>
        <div class="enable-icon">🏛</div>
        <div>
          <h4>Domain Experts Can Build Production AI — Without an Engineering Team</h4>
          <p>The AES agent handles the full complexity of a multi-department marine infrastructure tender. It was built by one estimation engineer. No software team. No months of development. Cowork's skill architecture puts that capability in the hands of the person who actually understands the domain.</p>
        </div>
      </li>
      <li>
        <div class="enable-icon">🔒</div>
        <div>
          <h4>Enterprise-Grade Governance Is a Skill, Not a Product Feature</h4>
          <p>The AES system's confidentiality protocol, rate sovereignty rules, and human-decision gates aren't built into the platform — they're encoded into the skills. That means they're version-controlled, auditable, and transferable to any tender the same team runs. Governance scales with the skill stack, not the software budget.</p>
        </div>
      </li>
      <li>
        <div class="enable-icon">⚡</div>
        <div>
          <h4>Speed Compounds When State Is Automatic</h4>
          <p>The biggest time saving in the AES system isn't the BOQ digitalisation or the rate lookups — it's the fact that state is never lost. Every session begins exactly where the last ended. In a construction tender environment where a team member might pick up another's work mid-sprint, that continuity is transformational.</p>
        </div>
      </li>
      <li>
        <div class="enable-icon">📈</div>
        <div>
          <h4>The System Gets Smarter With Every Tender</h4>
          <p>Each tender cycle adds new rate data to the lookup library, new rule amendments to the Blueprint, and new supplier comparisons to the workbook archive. The agent reads from that expanding knowledge base on every sprint. The more tenders it runs, the more precise its lookups and the richer its comparisons become.</p>
        </div>
      </li>
    </ul>
  </div>
</section>

<!-- ══════════════════════ CLOSING ══════════════════════ -->
<section class="closing">
  <div class="wrap">
    <h2>This Is Agent-1.<br>The Pipeline Scales to Every Tender.</h2>
    <p>The AES system is designed from the ground up to be replicable — new tender, same skills, same sprint loop, same governance. The estimation department now has a reusable AI infrastructure that grows with every bid it processes.</p>
    <div class="cta-row">
      <a href="https://github.com/alaaelsebaie" class="btn btn-gold" target="_blank">View on GitHub →</a>
      <a href="#" class="btn btn-ghost">AES Build Blueprint v1.1</a>
    </div>
  </div>
</section>

<!-- ══════════════════════ FOOTER ══════════════════════ -->
<footer>
  <div>
    <strong>AES Estimation System · Agent-1</strong> · Built by <strong>Alaa El-Sebaie</strong><br>
    Powered by <strong>Claude Cowork · Anthropic</strong> · Zero code written by hand
  </div>
  <div class="watermark">PUBLIC PORTFOLIO VERSION · Employer and project identifiers redacted</div>
</footer>

</body>
</html>
