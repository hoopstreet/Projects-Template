<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MAID Protocol — TikTok-Prompt-Generator</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Sora:wght@300;400;600;700;800&display=swap');

  :root {
    --bg: #080c14;
    --surface: #0d1520;
    --surface2: #111d2e;
    --border: #1a2d45;
    --accent: #00d4ff;
    --accent2: #7b2fff;
    --green: #00ff88;
    --yellow: #ffd700;
    --red: #ff4466;
    --orange: #ff8c42;
    --text: #c8dff0;
    --muted: #5a7a99;
    --mono: 'Space Mono', monospace;
    --sans: 'Sora', sans-serif;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    font-size: 14px;
    line-height: 1.7;
    overflow-x: hidden;
  }

  /* GRID BG */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,212,255,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,212,255,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrap { position: relative; z-index: 1; max-width: 1100px; margin: 0 auto; padding: 40px 20px 80px; }

  /* HEADER */
  .hero {
    border: 1px solid var(--border);
    background: linear-gradient(135deg, #0d1520 0%, #0a1628 60%, #0d1035 100%);
    border-radius: 12px;
    padding: 48px 40px;
    margin-bottom: 40px;
    position: relative;
    overflow: hidden;
  }
  .hero::after {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(0,212,255,0.08) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-tag {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    letter-spacing: 3px;
    text-transform: uppercase;
    margin-bottom: 12px;
    display: block;
  }
  .hero h1 {
    font-size: 2.4rem;
    font-weight: 800;
    color: #fff;
    line-height: 1.2;
    margin-bottom: 10px;
  }
  .hero h1 span { color: var(--accent); }
  .hero-sub {
    color: var(--muted);
    font-size: 13px;
    font-family: var(--mono);
  }
  .hero-meta {
    display: flex;
    gap: 24px;
    margin-top: 24px;
    flex-wrap: wrap;
  }
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    color: var(--accent);
    font-family: var(--mono);
    font-size: 11px;
    padding: 4px 12px;
    border-radius: 4px;
    letter-spacing: 1px;
  }
  .badge.green { background: rgba(0,255,136,0.08); border-color: rgba(0,255,136,0.2); color: var(--green); }
  .badge.purple { background: rgba(123,47,255,0.1); border-color: rgba(123,47,255,0.3); color: #b88fff; }

  /* SECTION */
  .section { margin-bottom: 40px; }
  .section-header {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
    padding-bottom: 12px;
    border-bottom: 1px solid var(--border);
  }
  .section-num {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--accent);
    background: rgba(0,212,255,0.08);
    border: 1px solid rgba(0,212,255,0.2);
    padding: 2px 8px;
    border-radius: 4px;
  }
  .section-title {
    font-size: 1.1rem;
    font-weight: 700;
    color: #fff;
  }
  .section-title span { color: var(--accent); }

  /* CARDS */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    margin-bottom: 16px;
  }
  .card h3 {
    font-size: 13px;
    font-weight: 700;
    color: #fff;
    margin-bottom: 10px;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .card p { color: var(--text); font-size: 13px; }

  .grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
  .grid-3 { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 16px; }

  @media(max-width: 700px) {
    .grid-2, .grid-3 { grid-template-columns: 1fr; }
    .hero { padding: 28px 20px; }
    .hero h1 { font-size: 1.6rem; }
  }

  /* ROLE CARDS */
  .role-card {
    border-radius: 10px;
    padding: 24px;
    border: 1px solid;
  }
  .role-card.human {
    background: linear-gradient(135deg, rgba(0,212,255,0.05), rgba(0,212,255,0.02));
    border-color: rgba(0,212,255,0.25);
  }
  .role-card.ai {
    background: linear-gradient(135deg, rgba(123,47,255,0.07), rgba(123,47,255,0.02));
    border-color: rgba(123,47,255,0.3);
  }
  .role-icon {
    font-size: 28px;
    margin-bottom: 12px;
    display: block;
  }
  .role-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .role-card.human .role-label { color: var(--accent); }
  .role-card.ai .role-label { color: #b88fff; }
  .role-card h3 { font-size: 1rem; font-weight: 700; color: #fff; margin-bottom: 12px; }
  .role-card ul { list-style: none; }
  .role-card ul li {
    font-size: 12px;
    color: var(--text);
    padding: 5px 0;
    border-bottom: 1px solid rgba(255,255,255,0.04);
    display: flex;
    align-items: flex-start;
    gap: 8px;
  }
  .role-card ul li::before { content: '→'; color: var(--accent); flex-shrink: 0; }
  .role-card.ai ul li::before { color: #b88fff; }

  /* TABLES */
  .tbl-wrap { overflow-x: auto; border-radius: 10px; border: 1px solid var(--border); margin-bottom: 16px; }
  table { width: 100%; border-collapse: collapse; font-size: 12px; }
  thead tr { background: rgba(0,212,255,0.06); }
  thead th {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--accent);
    padding: 12px 16px;
    text-align: left;
    white-space: nowrap;
    border-bottom: 1px solid var(--border);
  }
  tbody tr { border-bottom: 1px solid rgba(255,255,255,0.04); }
  tbody tr:last-child { border-bottom: none; }
  tbody tr:hover { background: rgba(255,255,255,0.02); }
  tbody td { padding: 11px 16px; color: var(--text); vertical-align: top; }
  .mono { font-family: var(--mono); }
  .status-ok { color: var(--green); }
  .status-pend { color: var(--yellow); }
  .status-err { color: var(--red); }
  .status-new { color: var(--accent); font-family: var(--mono); font-size: 11px; }
  .tag {
    display: inline-block;
    font-family: var(--mono);
    font-size: 10px;
    padding: 2px 8px;
    border-radius: 3px;
    margin: 1px;
  }
  .tag-v { background: rgba(0,255,136,0.1); color: var(--green); border: 1px solid rgba(0,255,136,0.2); }
  .tag-s { background: rgba(0,212,255,0.1); color: var(--accent); border: 1px solid rgba(0,212,255,0.2); }
  .tag-e { background: rgba(255,68,102,0.1); color: var(--red); border: 1px solid rgba(255,68,102,0.2); }
  .tag-u { background: rgba(255,140,66,0.1); color: var(--orange); border: 1px solid rgba(255,140,66,0.2); }

  /* CODE BLOCKS */
  .code-phase { margin-bottom: 20px; }
  .phase-label {
    font-family: var(--mono);
    font-size: 10px;
    letter-spacing: 2px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .phase-label::after { content: ''; flex: 1; height: 1px; background: rgba(0,212,255,0.15); }
  pre {
    background: #060b12;
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent);
    border-radius: 8px;
    padding: 18px 20px;
    overflow-x: auto;
    font-family: var(--mono);
    font-size: 12px;
    line-height: 1.8;
    color: #a8c8e8;
    white-space: pre;
  }
  pre .cmt { color: var(--muted); }
  pre .kw { color: var(--accent); }
  pre .str { color: var(--green); }
  pre .cmd { color: #ffd700; }

  /* FLOW DIAGRAM */
  .flow {
    display: flex;
    align-items: center;
    gap: 0;
    flex-wrap: wrap;
    margin: 20px 0;
  }
  .flow-step {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 18px;
    min-width: 140px;
    text-align: center;
    flex-shrink: 0;
  }
  .flow-step .step-icon { font-size: 20px; margin-bottom: 4px; }
  .flow-step .step-label { font-family: var(--mono); font-size: 10px; color: var(--accent); letter-spacing: 1px; }
  .flow-step .step-desc { font-size: 11px; color: var(--muted); margin-top: 3px; }
  .flow-arrow {
    color: var(--accent);
    font-size: 18px;
    padding: 0 8px;
    opacity: 0.5;
  }

  /* RULES */
  .rule {
    background: var(--surface);
    border: 1px solid var(--border);
    border-left: 3px solid var(--accent2);
    border-radius: 8px;
    padding: 16px 20px;
    margin-bottom: 10px;
  }
  .rule-head {
    font-family: var(--mono);
    font-size: 11px;
    color: #b88fff;
    font-weight: 700;
    margin-bottom: 6px;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .rule p { font-size: 12px; color: var(--text); }
  .rule code {
    font-family: var(--mono);
    font-size: 11px;
    background: rgba(0,0,0,0.3);
    padding: 2px 6px;
    border-radius: 3px;
    color: var(--green);
  }

  /* SUGGESTIONS */
  .suggest-list { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  @media(max-width:600px) { .suggest-list { grid-template-columns: 1fr; } }
  .suggest-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 14px 16px;
    display: flex;
    gap: 12px;
    align-items: flex-start;
  }
  .suggest-num {
    font-family: var(--mono);
    font-size: 20px;
    font-weight: 700;
    color: rgba(0,212,255,0.2);
    line-height: 1;
    flex-shrink: 0;
  }
  .suggest-item h4 { font-size: 12px; font-weight: 700; color: #fff; margin-bottom: 3px; }
  .suggest-item p { font-size: 11px; color: var(--muted); }

  /* TRAINING BLOCK */
  .training-box {
    background: linear-gradient(135deg, rgba(123,47,255,0.08), rgba(0,212,255,0.04));
    border: 1px solid rgba(123,47,255,0.3);
    border-radius: 10px;
    padding: 24px;
    margin-bottom: 16px;
  }
  .training-box h3 {
    font-family: var(--mono);
    font-size: 11px;
    color: #b88fff;
    letter-spacing: 2px;
    text-transform: uppercase;
    margin-bottom: 14px;
  }
  .ai-label {
    display: inline-block;
    font-family: var(--mono);
    font-size: 10px;
    padding: 2px 8px;
    border-radius: 3px;
    margin: 2px;
    border: 1px solid;
  }
  .ai-chatgpt { color: #10a37f; border-color: rgba(16,163,127,0.4); background: rgba(16,163,127,0.08); }
  .ai-gemini  { color: #4285f4; border-color: rgba(66,133,244,0.4); background: rgba(66,133,244,0.08); }
  .ai-deepseek{ color: #ff6b6b; border-color: rgba(255,107,107,0.4); background: rgba(255,107,107,0.08); }

  .divider {
    border: none;
    border-top: 1px solid var(--border);
    margin: 40px 0;
  }

  .info-box {
    background: rgba(255,215,0,0.05);
    border: 1px solid rgba(255,215,0,0.2);
    border-radius: 8px;
    padding: 14px 18px;
    font-size: 12px;
    color: #ffd700;
    margin-bottom: 16px;
  }
  .info-box strong { color: #ffe566; }

  .warn-box {
    background: rgba(255,68,102,0.05);
    border: 1px solid rgba(255,68,102,0.2);
    border-radius: 8px;
    padding: 14px 18px;
    font-size: 12px;
    color: #ff8888;
    margin-bottom: 16px;
  }
</style>
</head>
<body>
<div class="wrap">

  <!-- HERO -->
  <div class="hero">
    <span class="hero-tag">⚡ MAID Protocol · v0.1.0-stable</span>
    <h1>TikTok-Prompt-<span>Generator</span> 🧬</h1>
    <p style="color:var(--muted);font-size:13px;margin-top:8px;">Mobile-AI Integrated Development · Zero-Local-Load Architecture</p>
    <div class="hero-meta">
      <span class="badge">👤 hoopstreet</span>
      <span class="badge">📱 iSH · Alpine Linux</span>
      <span class="badge green">✅ GitHub Actions CI/CD</span>
      <span class="badge purple">🤖 AI Self-Coder</span>
    </div>
  </div>

  <!-- SECTION 1: ARCHITECTURE -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">01</span>
      <span class="section-title">Architecture — <span>Zero-Local-Load</span></span>
    </div>
    <p style="color:var(--muted);font-size:12px;margin-bottom:16px;">The iPhone is a Signal Transmitter only. All heavy computation runs on GitHub Actions.</p>
    <div class="grid-2">
      <div class="card">
        <h3>🏗 System Components</h3>
        <div class="tbl-wrap" style="border:none;border-radius:0;">
          <table>
            <thead><tr><th>Component</th><th>Role</th><th>Tech</th></tr></thead>
            <tbody>
              <tr><td class="mono">iSH iPhone</td><td>Commander / Signal Sender</td><td>Alpine Linux</td></tr>
              <tr><td class="mono">GitHub</td><td>Version Control + Truth Source</td><td>Git</td></tr>
              <tr><td class="mono">GitHub Actions</td><td>AI Self-Coder Executor</td><td>YAML Workflows</td></tr>
              <tr><td class="mono">Task.md</td><td>Human Input Buffer / Trigger</td><td>Markdown</td></tr>
              <tr><td class="mono">Roadmap.md</td><td>AI Output Reality / Project State</td><td>Markdown</td></tr>
            </tbody>
          </table>
        </div>
      </div>
      <div class="card">
        <h3>📂 Two-File System</h3>
        <div class="tbl-wrap" style="border:none;border-radius:0;">
          <table>
            <thead><tr><th>File</th><th>Owner</th><th>Purpose</th><th>Trigger</th></tr></thead>
            <tbody>
              <tr><td class="mono" style="color:var(--accent)">Task.md</td><td>Human Coder</td><td>Input Buffer — The "What"</td><td>New row <code style="color:var(--green)">new</code></td></tr>
              <tr><td class="mono" style="color:#b88fff">Roadmap.md</td><td>AI Self-Coder</td><td>Output Reality — The "How"</td><td>Detects <code style="color:var(--green)">new</code></td></tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- FLOW DIAGRAM -->
    <div style="margin-top:8px;">
      <div class="phase-label">Continuous 1→2 Execution Flow</div>
      <div class="flow">
        <div class="flow-step">
          <div class="step-icon">📱</div>
          <div class="step-label">Human (iSH)</div>
          <div class="step-desc">Appends task to Task.md + Roadmap.md</div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-step">
          <div class="step-icon">☁️</div>
          <div class="step-label">git push</div>
          <div class="step-desc">Status: <span style="color:var(--accent)">new</span></div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-step">
          <div class="step-icon">⚙️</div>
          <div class="step-label">Actions Trigger</div>
          <div class="step-desc">Detects <span style="color:var(--accent)">new</span> in files</div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-step">
          <div class="step-icon">🤖</div>
          <div class="step-label">AI Self-Coder</div>
          <div class="step-desc">Executes + Updates status</div>
        </div>
        <div class="flow-arrow">→</div>
        <div class="flow-step">
          <div class="step-icon">📊</div>
          <div class="step-label">Result</div>
          <div class="step-desc">✅ or ❌ written back</div>
        </div>
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 2: ROLES -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">02</span>
      <span class="section-title">Developer <span>Roles</span> — Separation of Concerns</span>
    </div>
    <div class="grid-2">
      <div class="role-card human">
        <span class="role-icon">👤</span>
        <div class="role-label">Role 1 · Commander</div>
        <h3>Human Coder</h3>
        <ul>
          <li>Device: iPhone running iSH (Alpine Linux)</li>
          <li>Goal: Define the <strong>"What"</strong> — strategic intent only</li>
          <li>Appends new rows to <code style="color:var(--green)">Task.md</code> and <code style="color:var(--green)">Roadmap.md</code></li>
          <li>Every commit push always has status <code style="color:var(--accent)">new</code></li>
          <li>Never edits <code>Roadmap.md</code> columns manually — only appends</li>
          <li>Uses AI providers (ChatGPT, Gemini, Deepseek) to generate iSH scripts</li>
          <li>Runs only <code>cat EOF</code> fragmented scripts — no nano/vi</li>
          <li>Human increments <strong>Minor</strong> version: <code>v1.<u>1</u>.0</code></li>
          <li>When only adding to Task.md → commit tag: <code>new</code> only</li>
          <li>When executing both files → commit includes status + notes + tags</li>
        </ul>
      </div>
      <div class="role-card ai">
        <span class="role-icon">🤖</span>
        <div class="role-label">Role 2 · Executor</div>
        <h3>AI Self-Coder</h3>
        <ul>
          <li>Environment: GitHub Actions Runner (cloud)</li>
          <li>Goal: Define the <strong>"How"</strong> and execute it</li>
          <li>Scans <code style="color:#b88fff">Task.md</code> and <code style="color:#b88fff">Roadmap.md</code> for <code>new</code> status</li>
          <li>If <code>new</code> → execute; if done → do nothing</li>
          <li>Builds full project logic from <code>Roadmap.md</code> goals</li>
          <li>Updates <strong>Status, Tags, Notes</strong> after execution</li>
          <li>Writes <code>✅</code>, <code>❌</code>, or <code>ERROR</code> + short note</li>
          <li>Generates automatic <code>CHANGELOG.md</code> entries</li>
          <li>Dependency check: blocks Task B if Task A ≠ <code>✅</code></li>
          <li>AI increments <strong>Patch</strong> version: <code>v1.1.<u>1</u></code></li>
        </ul>
      </div>
    </div>
    <div class="info-box" style="margin-top:16px;">
      <strong>⚡ Versioning Agreement:</strong> Human Coder bumps Minor version (<code>v1.<b>2</b>.0</code>) · AI Self-Coder bumps Patch version (<code>v1.2.<b>3</b></code>) — no conflicts ever.
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 3: TABLE STRUCTURE -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">03</span>
      <span class="section-title">Table Structures — <span>Task.md &amp; Roadmap.md</span></span>
    </div>

    <!-- TASK.MD -->
    <div class="phase-label">task.md — Human Input Buffer (Tactical Layer)</div>
    <div class="tbl-wrap">
      <table>
        <thead>
          <tr>
            <th>Task</th>
            <th>Description</th>
            <th>Notes</th>
            <th>Tags</th>
            <th>Dev</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td class="mono" style="color:var(--accent)">T-001</td>
            <td>iSH Environment Setup — Initial workspace &amp; Alpine config</td>
            <td>mkdir ~/TikTok-Prompt-Generator, git init</td>
            <td><span class="tag tag-v">v0.1.0</span> <span class="tag tag-s">stable</span></td>
            <td class="status-ok">✅ Human Coder</td>
          </tr>
          <tr>
            <td class="mono" style="color:var(--accent)">T-002</td>
            <td>GitHub Auth — credential.helper store setup</td>
            <td>PAT token required for iSH push</td>
            <td><span class="tag tag-v">v0.1.0</span> <span class="tag tag-u">setup</span></td>
            <td class="status-ok">✅ Human Coder</td>
          </tr>
          <tr>
            <td class="mono" style="color:var(--accent)">T-003</td>
            <td>GitHub Actions Workflow — Create dev.yml trigger</td>
            <td>Depends on T-002; scans for <code style="color:var(--accent)">new</code> tag</td>
            <td><span class="tag tag-v">v0.2.0</span> <span class="tag tag-u">automation</span></td>
            <td class="status-pend">⌛ AI Self-Coder</td>
          </tr>
          <tr>
            <td class="mono" style="color:var(--accent)">T-004</td>
            <td>TikTok Shop API Auth — Connect affiliate keys</td>
            <td style="color:var(--red)">⚠️ Needs TikTok API KEY</td>
            <td><span class="tag tag-v">v0.3.0</span> <span class="tag tag-s">new</span></td>
            <td class="status-new">new · Human Coder</td>
          </tr>
          <tr>
            <td class="mono" style="color:var(--accent)">T-005</td>
            <td>Prompt Generator Engine — AI script generation from product data</td>
            <td>Depends on T-003, T-004</td>
            <td><span class="tag tag-v">v1.0.0</span> <span class="tag tag-u">feature</span></td>
            <td class="status-err">❌ Error — see notes</td>
          </tr>
        </tbody>
      </table>
    </div>

    <!-- Column Definitions for Task.md -->
    <div class="card">
      <h3>📋 Task.md Column Definitions</h3>
      <div class="tbl-wrap" style="border:none;border-radius:0;">
        <table>
          <thead><tr><th>#</th><th>Column</th><th>Format</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td class="mono">1</td><td><strong>Task</strong></td><td>T-001, T-002…</td><td>Unique atomic ID. One task = one specific functionality. Used for dependency mapping and branch naming.</td></tr>
            <tr><td class="mono">2</td><td><strong>Description</strong></td><td>Plain English</td><td>Clear objective of what is being built or changed. Must be specific enough for AI to act on.</td></tr>
            <tr><td class="mono">3</td><td><strong>Notes</strong></td><td>Technical detail</td><td>File paths, API requirements, errors, blockers. AI writes execution logs here after running.</td></tr>
            <tr><td class="mono">4</td><td><strong>Tags</strong></td><td>vX.X.X · keyword</td><td>Version tag + type: <code>stable</code>, <code>upgrade</code>, <code>fix</code>, <code>fallback</code>, <code>new</code>, <code>feature</code>, <code>automation</code></td></tr>
            <tr><td class="mono">5</td><td><strong>Dev</strong></td><td>Name + Status</td><td><code>Human Coder</code> or <code>AI Self-Coder</code>. Combined with emoji status: ✅ ⌛ ❌ ⚠️ + <code>new</code></td></tr>
          </tbody>
        </table>
      </div>
    </div>

    <!-- ROADMAP.MD -->
    <div class="phase-label" style="margin-top:24px;">roadmap.md — AI Output Reality (Strategic Layer)</div>
    <div class="tbl-wrap">
      <table>
        <thead>
          <tr>
            <th>Task</th>
            <th>Description</th>
            <th>Notes</th>
            <th>Tags</th>
            <th>Dev</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><strong>Foundation</strong></td>
            <td>iSH-to-GitHub handshake. Zero-Local-Load base environment configured.</td>
            <td>Alpine Linux · credential.helper store active</td>
            <td><span class="tag tag-v">v0.1.0-stable</span></td>
            <td class="status-ok">✅ Human Coder</td>
          </tr>
          <tr>
            <td><strong>CI/CD Automation</strong></td>
            <td>GitHub Actions dev.yml workflow. Detects <code>new</code> in Task.md and triggers AI Self-Coder.</td>
            <td>Workflow file: .github/workflows/dev.yml</td>
            <td><span class="tag tag-v">v0.2.0-automation</span></td>
            <td class="status-pend">⌛ AI Self-Coder</td>
          </tr>
          <tr>
            <td><strong>API Integration</strong></td>
            <td>TikTok Shop Affiliate API connection. Product keyword scraping enabled.</td>
            <td style="color:var(--red)">⚠️ API KEY Required — TikTok Partner Center</td>
            <td><span class="tag tag-v">v0.3.0-feature</span></td>
            <td class="status-new">new · Human Coder</td>
          </tr>
          <tr>
            <td><strong>Prompt Engine v1</strong></td>
            <td>AI-powered script generator. Takes product data → outputs Taglish TikTok video script.</td>
            <td>Blocked by T-004 (API KEY missing)</td>
            <td><span class="tag tag-v">v1.0.0-stable</span></td>
            <td class="status-err">❌ AI Self-Coder</td>
          </tr>
          <tr>
            <td><strong>Video Generator</strong></td>
            <td>ElevenLabs voiceover + Creatomate video output. Full pipeline to posting.</td>
            <td>Depends on Prompt Engine v1</td>
            <td><span class="tag tag-v">v1.1.0-upgrade</span></td>
            <td style="color:var(--muted)">📅 Scheduled</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="card">
      <h3>📋 Roadmap.md Column Definitions</h3>
      <div class="tbl-wrap" style="border:none;border-radius:0;">
        <table>
          <thead><tr><th>#</th><th>Column</th><th>Format</th><th>Description</th></tr></thead>
          <tbody>
            <tr><td class="mono">1</td><td><strong>Task</strong></td><td>Milestone Name</td><td>High-level feature name. Strategic grouping of multiple tasks. Readable by non-developers.</td></tr>
            <tr><td class="mono">2</td><td><strong>Description</strong></td><td>Full sentence</td><td>Business value and technical summary. Written by AI Self-Coder after execution. Updated automatically.</td></tr>
            <tr><td class="mono">3</td><td><strong>Notes</strong></td><td>Technical detail</td><td>Blockers, API requirements, errors. AI writes: <code>Needs API KEY</code>, <code>Blocked by T-00X</code>, etc.</td></tr>
            <tr><td class="mono">4</td><td><strong>Tags</strong></td><td>vX.X.X-keyword</td><td>Full semver tag: <code>v1.0.0-stable</code>, <code>v1.1.0-upgrade</code>, <code>v1.1.1-fix</code>, <code>v1.0.0-fallback</code></td></tr>
            <tr><td class="mono">5</td><td><strong>Dev</strong></td><td>Name + Status</td><td>Who last updated: <code>Human Coder</code> or <code>AI Self-Coder</code>. Always includes emoji status.</td></tr>
          </tbody>
        </table>
      </div>
    </div>

    <!-- STATUS LEGEND -->
    <div class="card" style="margin-top:8px;">
      <h3>🔵 Status &amp; Tag Legend</h3>
      <div class="tbl-wrap" style="border:none;border-radius:0;">
        <table>
          <thead><tr><th>Symbol</th><th>Meaning</th><th>Who Sets It</th><th>Trigger</th></tr></thead>
          <tbody>
            <tr><td><span style="color:var(--accent);font-family:var(--mono)">new</span></td><td>Newly added — ready to trigger AI</td><td>Human Coder</td><td>AI detects and executes</td></tr>
            <tr><td><span class="status-pend">⌛</span></td><td>In progress — AI is executing</td><td>AI Self-Coder</td><td>Set during execution</td></tr>
            <tr><td><span class="status-ok">✅</span></td><td>Complete — merged to main, verified</td><td>AI Self-Coder</td><td>Unblocks next dependent task</td></tr>
            <tr><td><span class="status-err">❌</span></td><td>Error — execution failed</td><td>AI Self-Coder</td><td>Blocks all dependent tasks</td></tr>
            <tr><td><span style="color:var(--orange)">⚠️</span></td><td>Warning — missing key/config</td><td>AI Self-Coder</td><td>Human must resolve manually</td></tr>
            <tr><td><span style="color:var(--muted)">📅</span></td><td>Scheduled — not yet started</td><td>Human Coder</td><td>Waiting for previous milestone</td></tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 4: RULES -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">04</span>
      <span class="section-title">AI Developer Protocol — <span>Strict Rules</span></span>
    </div>

    <div class="rule"><div class="rule-head">Rule 1 · No Manual Edits</div><p>Never use <code>nano</code>, <code>vi</code>, or any text editor. All file updates via <code>cat &lt;&lt; 'EOF'</code> scripts only. Fully automated script-based delivery.</p></div>
    <div class="rule"><div class="rule-head">Rule 2 · 150-Character Hard Limit</div><p>Any code block line exceeding 150 characters is <strong>INVALID</strong>. Must be split into multiple <code>cat EOF</code> parts. No exceptions.</p></div>
    <div class="rule"><div class="rule-head">Rule 3 · EOF Safety</div><p>Never nest <code>cat</code> inside <code>cat</code>. Each file creation is an isolated phase. Always: <code>cat &lt;&lt; 'EOF' &gt; file</code> … <code>EOF</code> — clean, single-purpose blocks.</p></div>
    <div class="rule"><div class="rule-head">Rule 4 · Blank Space Buffer</div><p>Every code block ends with a trailing blank line after <code>EOF</code>. This prevents iSH cursor from "sticking" to the last character and ensures clean Enter press.</p></div>
    <div class="rule"><div class="rule-head">Rule 5 · Mobile-First Always</div><p>Every code block starts with: <code>cd ~/[PROJECT-NAME] || mkdir -p ~/[PROJECT-NAME] &amp;&amp; cd ~/[PROJECT-NAME]</code> — guarantees correct directory before any operation.</p></div>
    <div class="rule"><div class="rule-head">Rule 6 · Safe-Pull Protocol</div><p>Always pull before push: <code>git pull origin main --rebase</code> then <code>git push origin main</code>. This preserves remote history and prevents data loss.</p></div>
    <div class="rule"><div class="rule-head">Rule 7 · Dependency Mapping</div><p>AI Self-Coder checks: if Task A is not <code>✅</code>, Task B is blocked. AI writes <code>Blocked by T-00X</code> in Notes column automatically.</p></div>
    <div class="rule"><div class="rule-head">Rule 8 · Commit Status Signals</div><p>Human push with Task.md only → commit message: <code>"status: new"</code>. Human push with both files → commit: <code>"execute: roadmap vX.X.X"</code>. AI updates → <code>"ai: updated T-00X ✅"</code></p></div>
  </div>

  <hr class="divider">

  <!-- SECTION 5: iSH CODE -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">05</span>
      <span class="section-title">iSH Implementation Scripts — <span>Copy-Paste Ready</span></span>
    </div>

    <div class="info-box">
      <strong>⚡ Instructions:</strong> Copy each phase block separately into iSH. Wait for the prompt to return before pasting the next phase. Each block is under 150 chars per line.
    </div>

    <!-- INIT -->
    <div class="code-phase">
      <div class="phase-label">Phase 1 · Environment Init &amp; Identity</div>
<pre><span class="cmt"># PHASE 1: Directory + Identity Setup</span>
<span class="cmd">mkdir</span> -p ~/TikTok-Prompt-Generator
<span class="cmd">cd</span> ~/TikTok-Prompt-Generator

<span class="cmd">git</span> config --global user.name <span class="str">"hoopstreet"</span>
<span class="cmd">git</span> config --global user.email <span class="str">"hoopstreet143@gmail.com"</span>
<span class="cmd">git</span> config --global credential.helper store
 </pre>
    </div>

    <div class="code-phase">
      <div class="phase-label">Phase 2 · Create Task.md</div>
<pre><span class="cmt"># PHASE 2A: Task.md Header</span>
<span class="cmd">cd</span> ~/TikTok-Prompt-Generator || <span class="cmd">mkdir</span> -p ~/TikTok-Prompt-Generator && <span class="cmd">cd</span> ~/TikTok-Prompt-Generator

<span class="cmd">cat</span> << <span class="str">'EOF'</span> > Task.md
# 🛠 Task Ledger: TikTok-Prompt-Generator
| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---:|
EOF
 </pre>
<pre><span class="cmt"># PHASE 2B: Task.md First Row</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Task.md
| T-001 | iSH Workspace Setup | Alpine Linux · git init | v0.1.0 stable | ✅ Human Coder |
EOF
 </pre>
<pre><span class="cmt"># PHASE 2C: Task.md Row 2</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Task.md
| T-002 | GitHub Auth Setup | credential.helper store | v0.1.0 setup | new Human Coder |
EOF
 </pre>
    </div>

    <div class="code-phase">
      <div class="phase-label">Phase 3 · Create Roadmap.md</div>
<pre><span class="cmt"># PHASE 3A: Roadmap.md Header</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> > Roadmap.md
# 🗺 Project Roadmap: TikTok-Prompt-Generator
| Task | Description | Notes | Tags | Dev |
|:---|:---|:---|:---|:---:|
EOF
 </pre>
<pre><span class="cmt"># PHASE 3B: Roadmap.md First Milestone</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Roadmap.md
| Foundation | iSH-to-GitHub base setup | Alpine Linux configured | v0.1.0-stable | ✅ Human Coder |
EOF
 </pre>
<pre><span class="cmt"># PHASE 3C: Roadmap.md Second Milestone</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Roadmap.md
| CI/CD Automation | GitHub Actions dev.yml | Detects new tag | v0.2.0-automation | new Human Coder |
EOF
 </pre>
    </div>

    <div class="code-phase">
      <div class="phase-label">Phase 4 · Git Init &amp; First Push</div>
<pre><span class="cmt"># PHASE 4A: Initialize Git</span>
<span class="cmd">cd</span> ~/TikTok-Prompt-Generator
<span class="cmd">git</span> init
<span class="cmd">git</span> branch -M main
 </pre>
<pre><span class="cmt"># PHASE 4B: Add Remote (replace YOUR-TOKEN and USERNAME)</span>
<span class="cmd">git</span> remote add origin https://YOUR-TOKEN@github.com/USERNAME/TikTok-Prompt-Generator.git
 </pre>
<pre><span class="cmt"># PHASE 4C: First Commit and Push</span>
<span class="cmd">git</span> add .
<span class="cmd">git</span> commit -m <span class="str">"feat: initial roadmap and task structure v0.1.0"</span>
<span class="cmd">git</span> pull origin main --rebase
<span class="cmd">git</span> push origin main
 </pre>
    </div>

    <!-- ADD NEW TASK ONLY -->
    <div class="code-phase">
      <div class="phase-label">Scenario A · Add New Task (Task.md Only — Status: new)</div>
<pre><span class="cmt"># SCENARIO A: Add task only → commit "status: new"</span>
<span class="cmd">cd</span> ~/TikTok-Prompt-Generator || <span class="cmd">exit</span>

<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Task.md
| T-003 | GitHub Actions Workflow | Create .github/workflows/dev.yml | v0.2.0 automation | new Human Coder |
EOF

<span class="cmd">git</span> add Task.md
<span class="cmd">git</span> commit -m <span class="str">"status: new"</span>
<span class="cmd">git</span> pull origin main --rebase
<span class="cmd">git</span> push origin main
 </pre>
    </div>

    <!-- EXECUTE BOTH -->
    <div class="code-phase">
      <div class="phase-label">Scenario B · Execute Both Files (Full Trigger — with Tags + Status)</div>
<pre><span class="cmt"># SCENARIO B PART 1: Append to Task.md</span>
<span class="cmd">cd</span> ~/TikTok-Prompt-Generator || <span class="cmd">exit</span>

<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Task.md
| T-004 | TikTok API Auth | Needs TikTok API KEY from Partner Center | v0.3.0 feature | new Human Coder |
EOF
 </pre>
<pre><span class="cmt"># SCENARIO B PART 2: Append to Roadmap.md</span>
<span class="cmd">cat</span> << <span class="str">'EOF'</span> >> Roadmap.md
| API Integration | Connect TikTok Affiliate API | Needs API KEY - TikTok Partner Center | v0.3.0-feature | new Human Coder |
EOF
 </pre>
<pre><span class="cmt"># SCENARIO B PART 3: Push to trigger AI Self-Coder</span>
<span class="cmd">git</span> add .
<span class="cmd">git</span> commit -m <span class="str">"execute: roadmap v0.3.0 T-004 new"</span>
<span class="cmd">git</span> pull origin main --rebase
<span class="cmd">git</span> push origin main
 </pre>
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 6: AI TRAINING -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">06</span>
      <span class="section-title">AI Provider Training Guide — <span>ChatGPT · Gemini · Deepseek</span></span>
    </div>
    <p style="color:var(--muted);font-size:12px;margin-bottom:16px;">Copy and paste this training prompt when starting a new chat with any AI provider. This trains them on your exact system.</p>

    <div class="training-box">
      <h3>🤖 Universal AI Training Prompt — Copy This</h3>
      <div style="display:flex;gap:8px;margin-bottom:14px;flex-wrap:wrap;">
        <span class="ai-label ai-chatgpt">ChatGPT</span>
        <span class="ai-label ai-gemini">Gemini</span>
        <span class="ai-label ai-deepseek">Deepseek</span>
      </div>
<pre style="border-left-color:var(--accent2);font-size:11px;line-height:1.9;">I am a Human Coder using iSH (Alpine Linux) on iPhone.
Follow the MAID Protocol strictly.

SYSTEM:
- Two files only: Task.md (input) and Roadmap.md (output)
- I am Human Coder. GitHub Actions is AI Self-Coder.
- Project: [INSERT PROJECT NAME e.g. TikTok-Prompt-Generator]

CODE RULES (STRICT):
1. ALL code in fragmented cat << 'EOF' blocks
2. MAX 150 characters per line — split if longer
3. NEVER use nano/vi — cat EOF scripts only
4. Every block starts: cd ~/[PROJECT] || exit
5. EOF always followed by blank line
6. Never nest cat inside cat
7. Always end with: git pull origin main --rebase && git push

COMMIT RULES:
- Task.md only append → commit: "status: new"
- Both files appended → commit: "execute: roadmap vX.X.X"

TABLE COLUMNS (both files):
Task | Description | Notes | Tags | Dev

STATUS VALUES:
new = Human just added (triggers AI)
⌛  = AI executing
✅  = Complete
❌  = Error
⚠️  = Missing key/config

DEV VALUES:
- "new Human Coder" = just added by me
- "✅ Human Coder" = I verified complete
- "✅ AI Self-Coder" = Actions completed it
- "❌ AI Self-Coder" = Actions failed

VERSIONING:
Human bumps Minor: v1.2.0 → v1.3.0
AI bumps Patch:    v1.3.0 → v1.3.1

After providing code → wait for my response.
Provide fix code only for the broken part.
Always provide error/fix tables and 10 next suggestions.
 </pre>
    </div>

    <div class="grid-3" style="margin-top:16px;">
      <div class="card">
        <h3>🟢 ChatGPT Tips</h3>
        <p style="font-size:11px;color:var(--muted);">Use GPT-4o. Paste the training prompt as the first message. For long scripts, ask it to "split into phases under 150 chars."</p>
      </div>
      <div class="card">
        <h3>🔵 Gemini Tips</h3>
        <p style="font-size:11px;color:var(--muted);">Use Gemini 1.5 Pro. It may over-explain — add "respond with code only, no prose" to the training prompt.</p>
      </div>
      <div class="card">
        <h3>🔴 Deepseek Tips</h3>
        <p style="font-size:11px;color:var(--muted);">Excellent for bash scripts. Add "strict bash only" to training. Best for long multi-phase automation scripts.</p>
      </div>
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 7: STATUS TABLES -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">07</span>
      <span class="section-title">Current Status — <span>Problems &amp; Fixes</span></span>
    </div>

    <div class="phase-label">Problems / Errors Needing Fix</div>
    <div class="tbl-wrap">
      <table>
        <thead><tr><th>Problem / Error</th><th>Fix Status</th><th>Missing / Notes</th></tr></thead>
        <tbody>
          <tr><td>Git Remote URL not set</td><td class="status-err">❌</td><td>Run: git remote add origin https://TOKEN@github.com/USER/REPO.git</td></tr>
          <tr><td>GitHub Personal Access Token</td><td class="status-err">❌</td><td>Generate PAT from GitHub Settings → Developer → Tokens (Classic)</td></tr>
          <tr><td>iSH Buffer Crashes on long paste</td><td class="status-ok">✅</td><td>Solved by 150-char fragmentation rule</td></tr>
          <tr><td>Credential persistence after reboot</td><td class="status-err">❌</td><td>Run credential.helper store before first push</td></tr>
          <tr><td>GitHub Actions .yml missing</td><td class="status-pend">⌛</td><td>T-003 pending — dev.yml not yet created</td></tr>
          <tr><td>TikTok API KEY not configured</td><td class="status-err">❌</td><td>Required for T-004 — get from TikTok Partner Center</td></tr>
        </tbody>
      </table>
    </div>

    <div class="phase-label" style="margin-top:20px;">Updates / Upgrades / Completed</div>
    <div class="tbl-wrap">
      <table>
        <thead><tr><th>Update / Upgrade</th><th>Status</th><th>Notes</th></tr></thead>
        <tbody>
          <tr><td>Git Identity Config</td><td class="status-ok">✅</td><td>hoopstreet / hoopstreet143@gmail.com</td></tr>
          <tr><td>150-char fragmentation rule</td><td class="status-ok">✅</td><td>Applied to all code blocks</td></tr>
          <tr><td>Task.md Table Structure</td><td class="status-ok">✅</td><td>5 columns: Task, Description, Notes, Tags, Dev</td></tr>
          <tr><td>Roadmap.md Table Structure</td><td class="status-ok">✅</td><td>Same 5 columns — milestone-based</td></tr>
          <tr><td>Role Separation (Human / AI)</td><td class="status-ok">✅</td><td>Defined with versioning agreement</td></tr>
          <tr><td>Dependency Mapping Logic</td><td class="status-ok">✅</td><td>Blocks Task B if Task A ≠ ✅</td></tr>
          <tr><td>Commit Signal Protocol</td><td class="status-ok">✅</td><td>new only vs execute: roadmap vX.X.X</td></tr>
          <tr><td>AI Provider Training Prompt</td><td class="status-ok">✅</td><td>Universal prompt for ChatGPT/Gemini/Deepseek</td></tr>
        </tbody>
      </table>
    </div>
  </div>

  <hr class="divider">

  <!-- SECTION 8: SUGGESTIONS -->
  <div class="section">
    <div class="section-header">
      <span class="section-num">08</span>
      <span class="section-title">Next 10 Development <span>Upgrade Suggestions</span></span>
    </div>
    <div class="suggest-list">
      <div class="suggest-item">
        <div class="suggest-num">01</div>
        <div><h4>Auto-Status Updater Workflow</h4><p>GitHub Action that changes Task.md status from ⌛ to ✅ automatically after a build passes. Zero Human input needed.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">02</div>
        <div><h4>AI-Generated Task Append Script</h4><p>One-line idea → full Markdown table row. AI expands "Add TikTok auth" into a complete T-00X row with proper tags.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">03</div>
        <div><h4>Mobile Webhook Notifications</h4><p>Receive a push notification to iPhone when any GitHub Action completes — success or failure.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">04</div>
        <div><h4>Automatic CHANGELOG.md Generator</h4><p>AI Self-Coder builds a running CHANGELOG.md from every ✅ milestone in Roadmap.md. Auto-versioned.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">05</div>
        <div><h4>iSH Aliases Setup</h4><p>Add <code>gpl</code> = git pull --rebase, <code>gps</code> = git push, <code>gst</code> = git status to .profile for faster mobile typing.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">06</div>
        <div><h4>TikTok API Secret Manager</h4><p>GitHub Secrets store for TikTok API keys. AI Self-Coder injects secrets into runner environment automatically.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">07</div>
        <div><h4>Multi-Project Dashboard</h4><p>Single README that aggregates Roadmap.md status from all Hoopstreet repos: TikTok-Prompt-Generator, TikTok-Video-Generator, etc.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">08</div>
        <div><h4>Error-to-GitHub-Issue Pipeline</h4><p>If AI Self-Coder hits a ❌, it auto-creates a GitHub Issue with the full error log attached. Human gets notified.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">09</div>
        <div><h4>Fallback Branch Protocol</h4><p>Before any major Roadmap execution, AI creates a <code>fallback/vX.X.X</code> branch automatically. One command to revert.</p></div>
      </div>
      <div class="suggest-item">
        <div class="suggest-num">10</div>
        <div><h4>Workflow Multiplexer</h4><p>Separate .yml files: <code>fix.yml</code>, <code>upgrade.yml</code>, <code>append.yml</code>. Each triggered by its tag type in the commit message.</p></div>
      </div>
    </div>
  </div>

  <!-- FOOTER -->
  <div style="margin-top:48px;padding-top:24px;border-top:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px;">
    <div>
      <div style="font-family:var(--mono);font-size:11px;color:var(--muted);">MAID Protocol · TikTok-Prompt-Generator</div>
      <div style="font-family:var(--mono);font-size:10px;color:rgba(90,122,153,0.5);margin-top:2px;">hoopstreet · hoopstreet143@gmail.com</div>
    </div>
    <div style="display:flex;gap:8px;flex-wrap:wrap;">
      <span class="badge">v0.1.0-stable</span>
      <span class="badge green">Task.md ✅</span>
      <span class="badge green">Roadmap.md ✅</span>
    </div>
  </div>

</div>
</body>
</html>
