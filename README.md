<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bisleri — README</title>
<link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@700;900&family=Rajdhani:wght@400;500;600;700&family=Russo+One&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { margin: 0; padding: 0; box-sizing: border-box; }

  :root {
    --orange: #9C6ADE;
    --orange-light: #C4A1F0;
    --red: #7B2FBE;
    --red-dark: #5A1D8E;
    --dark: #08070C;
    --dark-card: #0E0D14;
    --dark-surface: #14121C;
    --dark-border: #1F1D2A;
    --white: #E4E0ED;
    --white-dim: #8882A0;
    --blue: #6FC3F7;
    --purple: #B07AFF;
    --green: #66BB6A;
    --yellow: #FFD54F;
  }

  body {
    background: var(--dark);
    color: var(--white);
    font-family: 'Rajdhani', sans-serif;
    overflow-x: hidden;
    min-height: 100vh;
  }

  .bg-layer {
    position: fixed; inset: 0; z-index: 0; pointer-events: none; overflow: hidden;
  }
  .bg-layer::before {
    content: '';
    position: absolute; top: -50%; left: -50%; width: 200%; height: 200%;
    background:
      radial-gradient(ellipse at 25% 15%, rgba(156,106,222,0.06) 0%, transparent 50%),
      radial-gradient(ellipse at 75% 85%, rgba(123,47,190,0.04) 0%, transparent 50%);
    animation: drift 15s ease-in-out infinite alternate;
  }
  @keyframes drift { to { transform: scale(1.08) rotate(2deg); } }

  .pixel-bg {
    position: fixed; font-size: 11px; opacity: 0.04;
    font-family: 'Courier New', monospace; color: var(--orange);
    pointer-events: none; z-index: 0; letter-spacing: 2px;
    animation: float 18s ease-in-out infinite;
    white-space: pre; line-height: 1.2;
  }
  .pixel-bg:nth-child(1) { top: 8%; left: 4%; }
  .pixel-bg:nth-child(2) { top: 45%; right: 6%; animation-delay: -6s; font-size: 9px; }
  .pixel-bg:nth-child(3) { bottom: 15%; left: 18%; animation-delay: -12s; font-size: 13px; color: var(--red); }
  @keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-20px); } }

  .container {
    position: relative; z-index: 1;
    max-width: 860px; margin: 0 auto; padding: 40px 20px 80px;
  }

  /* HERO */
  .hero {
    text-align: center; padding: 56px 28px 48px;
    border: 1px solid var(--dark-border); border-radius: 3px;
    background: var(--dark-card); position: relative;
    overflow: hidden; margin-bottom: 28px;
  }
  .hero::before {
    content: ''; position: absolute; top: 0; left: 0; right: 0; height: 3px;
    background: linear-gradient(90deg, var(--red-dark), var(--red), var(--orange-light), var(--red), var(--red-dark));
    background-size: 200% 100%; animation: fireline 3s linear infinite;
  }
  @keyframes fireline { to { background-position: 200% 50%; } }
  .hero::after {
    content: ''; position: absolute; inset: 0;
    background:
      repeating-linear-gradient(0deg, transparent, transparent 48px, rgba(156,106,222,0.015) 48px, rgba(156,106,222,0.015) 49px),
      repeating-linear-gradient(90deg, transparent, transparent 48px, rgba(156,106,222,0.015) 48px, rgba(156,106,222,0.015) 49px);
    pointer-events: none;
  }

  .leaf-mark {
    width: 64px; height: 64px; margin: 0 auto 20px; opacity: 0.35;
    animation: slowspin 40s linear infinite;
  }
  @keyframes slowspin { to { transform: rotate(360deg); } }

  .hero-name {
    font-family: 'Cinzel', serif;
    font-size: clamp(32px, 6vw, 56px); font-weight: 900;
    letter-spacing: 3px; text-transform: uppercase;
    background: linear-gradient(135deg, var(--orange-light), var(--orange), var(--red));
    -webkit-background-clip: text; -webkit-text-fill-color: transparent; background-clip: text;
    filter: drop-shadow(0 0 25px rgba(156,106,222,0.3)); line-height: 1.15;
  }
  .hero-aka {
    font-family: 'Russo One', sans-serif; font-size: 13px;
    letter-spacing: 6px; text-transform: uppercase;
    color: var(--white-dim); margin: 6px 0 24px;
  }
  .hero-sub { font-size: 15px; color: var(--white-dim); letter-spacing: 1px; }

  /* BADGES */
  .badges { display: flex; flex-wrap: wrap; gap: 8px; justify-content: center; margin-bottom: 28px; }
  .badge {
    padding: 5px 14px; border-radius: 2px; font-size: 11px; font-weight: 700;
    letter-spacing: 1.5px; text-transform: uppercase;
    border: 1px solid; transition: transform 0.2s;
  }
  .badge:hover { transform: translateY(-2px); }
  .badge.o { background: rgba(156,106,222,0.08); border-color: rgba(156,106,222,0.25); color: var(--orange-light); }
  .badge.b { background: rgba(79,195,247,0.08); border-color: rgba(79,195,247,0.25); color: var(--blue); }
  .badge.p { background: rgba(156,106,222,0.08); border-color: rgba(156,106,222,0.25); color: var(--purple); }
  .badge.g { background: rgba(102,187,106,0.08); border-color: rgba(102,187,106,0.25); color: var(--green); }

  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--dark-border), rgba(156,106,222,0.2), var(--dark-border), transparent);
    margin: 4px 0;
  }

  /* CARDS */
  .card {
    background: var(--dark-card); border: 1px solid var(--dark-border);
    border-radius: 3px; padding: 28px; margin-bottom: 20px;
    position: relative; overflow: hidden; transition: border-color 0.3s;
  }
  .card:hover { border-color: rgba(156,106,222,0.2); }
  .card::before {
    content: ''; position: absolute; top: 0; left: 0;
    width: 3px; height: 100%;
    background: linear-gradient(180deg, var(--orange), transparent);
  }
  .card-head { display: flex; align-items: center; gap: 12px; margin-bottom: 16px; }
  .card-icon {
    width: 34px; height: 34px; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px; flex-shrink: 0;
  }
  .card-icon.o { background: rgba(156,106,222,0.12); }
  .card-icon.b { background: rgba(79,195,247,0.12); }
  .card-icon.g { background: rgba(102,187,106,0.12); }
  .card-icon.r { background: rgba(196,30,58,0.12); }
  .card-icon.y { background: rgba(255,213,79,0.12); }
  .card-title {
    font-family: 'Russo One', sans-serif; font-size: 18px;
    letter-spacing: 2px; text-transform: uppercase; color: var(--white);
  }
  .card-title .jp {
    display: block; font-size: 11px; color: var(--white-dim);
    letter-spacing: 3px; font-family: 'Rajdhani', sans-serif;
    font-weight: 400; margin-top: 1px;
  }
  .card-body { font-size: 15px; line-height: 1.8; color: var(--white-dim); }
  .card-body p { margin-bottom: 10px; }
  .hl { color: var(--orange-light); font-weight: 600; }
  .hl-b { color: var(--blue); font-weight: 600; }

  /* TECH GRID */
  .tech-grid {
    display: grid; grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
    gap: 10px; margin-top: 14px;
  }
  .tech-item {
    background: var(--dark-surface); border: 1px solid var(--dark-border);
    border-radius: 3px; padding: 16px 12px; text-align: center;
    transition: all 0.25s; position: relative; overflow: hidden;
  }
  .tech-item:hover {
    border-color: var(--orange); transform: translateY(-3px);
    box-shadow: 0 6px 20px rgba(156,106,222,0.1);
  }
  .tech-item::after {
    content: ''; position: absolute; bottom: 0; left: 0; right: 0;
    height: 2px; background: var(--orange);
    transform: scaleX(0); transition: transform 0.25s;
  }
  .tech-item:hover::after { transform: scaleX(1); }
  .tech-emoji { font-size: 26px; display: block; margin-bottom: 6px; }
  .tech-name { font-weight: 700; font-size: 13px; letter-spacing: 1px; text-transform: uppercase; color: var(--white); }
  .tech-note { font-size: 10px; color: var(--white-dim); margin-top: 3px; }

  /* STAT BARS */
  .stats { margin-top: 12px; }
  .stat-row {
    display: flex; align-items: center; gap: 14px;
    padding: 10px 0; border-bottom: 1px solid rgba(255,255,255,0.03);
  }
  .stat-row:last-child { border-bottom: none; }
  .stat-label { font-size: 13px; font-weight: 600; color: var(--white); min-width: 130px; flex-shrink: 0; }
  .stat-track { flex: 1; height: 7px; background: var(--dark-surface); border-radius: 4px; overflow: hidden; }
  .stat-fill { height: 100%; border-radius: 4px; animation: grow 1.2s ease-out forwards; transform-origin: left; }
  @keyframes grow { from { transform: scaleX(0); } }
  .stat-fill.o { background: linear-gradient(90deg, var(--orange), var(--orange-light)); }
  .stat-fill.b { background: linear-gradient(90deg, #1565C0, var(--blue)); }
  .stat-fill.p { background: linear-gradient(90deg, #6A1B9A, var(--purple)); }
  .stat-fill.g { background: linear-gradient(90deg, #2E7D32, var(--green)); }
  .stat-fill.y { background: linear-gradient(90deg, #E65100, var(--yellow)); }
  .stat-fill.r { background: linear-gradient(90deg, var(--red-dark), var(--red)); }
  .stat-pct { font-size: 12px; color: var(--white-dim); min-width: 32px; text-align: right; }

  /* TIMELINE */
  .timeline { margin-top: 14px; padding-left: 24px; position: relative; }
  .timeline::before {
    content: ''; position: absolute; left: 6px; top: 0; bottom: 0;
    width: 2px; background: linear-gradient(180deg, var(--orange), var(--red), transparent);
  }
  .tl-item { position: relative; margin-bottom: 18px; }
  .tl-item::before {
    content: ''; position: absolute; left: -22px; top: 5px;
    width: 10px; height: 10px; border-radius: 50%;
    background: var(--orange); border: 2px solid var(--dark-card);
    box-shadow: 0 0 8px rgba(156,106,222,0.4);
  }
  .tl-item:last-child::before { background: var(--blue); box-shadow: 0 0 8px rgba(79,195,247,0.3); }
  .tl-label { font-size: 11px; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--orange); margin-bottom: 2px; }
  .tl-text { font-size: 14px; color: var(--white-dim); line-height: 1.6; }

  /* CODE */
  .codeblock {
    background: var(--dark-surface); border: 1px solid var(--dark-border);
    border-radius: 3px; padding: 18px; margin-top: 14px;
    font-family: 'Courier New', monospace; font-size: 13px;
    line-height: 1.8; color: var(--white-dim); overflow-x: auto;
  }
  .codeblock .c { color: #444; }
  .codeblock .k { color: var(--orange-light); }
  .codeblock .s { color: var(--green); }

  /* CTA */
  .cta {
    text-align: center; padding: 44px 24px;
    background: var(--dark-card); border: 1px solid var(--dark-border);
    border-radius: 3px; margin-top: 4px; position: relative; overflow: hidden;
  }
  .cta::before {
    content: ''; position: absolute; inset: 0;
    background: radial-gradient(circle at center, rgba(156,106,222,0.05) 0%, transparent 65%);
  }
  .cta-title {
    font-family: 'Cinzel', serif; font-size: clamp(18px, 3vw, 26px);
    font-weight: 700; color: var(--orange-light); margin-bottom: 10px;
  }
  .cta-text { font-size: 14px; color: var(--white-dim); max-width: 440px; margin: 0 auto 24px; line-height: 1.7; }
  .cta-btns { display: flex; gap: 14px; justify-content: center; flex-wrap: wrap; }
  .btn {
    display: inline-flex; align-items: center; gap: 8px;
    padding: 11px 24px; border-radius: 2px;
    font-family: 'Russo One', sans-serif; font-size: 12px;
    letter-spacing: 2px; text-transform: uppercase;
    text-decoration: none; transition: all 0.25s; cursor: pointer; border: none;
  }
  .btn.pri {
    background: linear-gradient(135deg, var(--orange), var(--red)); color: #fff;
    box-shadow: 0 4px 16px rgba(156,106,222,0.3);
  }
  .btn.pri:hover { transform: translateY(-2px); box-shadow: 0 6px 24px rgba(156,106,222,0.45); }
  .btn.sec { background: transparent; color: var(--white); border: 1px solid var(--dark-border); }
  .btn.sec:hover { border-color: var(--orange); color: var(--orange-light); transform: translateY(-2px); }

  /* FOOTER */
  .footer { text-align: center; padding: 36px 20px; font-size: 12px; color: var(--white-dim); letter-spacing: 2px; }
  .footer .mark { font-size: 28px; opacity: 0.2; margin-bottom: 10px; }
  .footer .line { margin-bottom: 4px; }
  .footer .sig { color: var(--orange); font-family: 'Russo One', sans-serif; font-size: 11px; letter-spacing: 4px; }

  .fi { opacity: 0; transform: translateY(16px); animation: fadeUp 0.7s ease forwards; }
  @keyframes fadeUp { to { opacity: 1; transform: translateY(0); } }
  .fi:nth-child(2) { animation-delay: 0.08s; }
  .fi:nth-child(3) { animation-delay: 0.16s; }
  .fi:nth-child(4) { animation-delay: 0.24s; }
  .fi:nth-child(5) { animation-delay: 0.32s; }
  .fi:nth-child(6) { animation-delay: 0.40s; }
  .fi:nth-child(7) { animation-delay: 0.48s; }
  .fi:nth-child(8) { animation-delay: 0.56s; }
  .fi:nth-child(9) { animation-delay: 0.64s; }
  .fi:nth-child(10) { animation-delay: 0.72s; }

  @media (max-width: 600px) {
    .container { padding: 16px 10px 60px; }
    .hero { padding: 36px 16px 32px; }
    .card { padding: 20px 16px; }
    .tech-grid { grid-template-columns: repeat(2, 1fr); }
    .stat-label { min-width: 100px; font-size: 12px; }
  }
</style>
</head>
<body>

<div class="bg-layer"></div>
<div class="pixel-bg">█▀▀ ▄▀▄ █▀▄ █▀▀
█   █ █ █ █ █▀▀
▀▀▀ ▀▀▀ ▀▀  ▀▀▀</div>
<div class="pixel-bg">░▒▓█ ▄▀▄ █▀▄ ░▒▓█
░▒▓█ █▀█ █▀▄ ░▒▓█</div>
<div class="pixel-bg">▓▓▓▓▓▓▓▓
▓░░▓▓░░▓
▓▓▓▓▓▓▓▓
░▓▓▓▓▓▓░
░░▓▓▓▓░░</div>

<div class="container">

  <!-- HERO -->
  <div class="hero fi">
    <svg class="leaf-mark" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
      <circle cx="50" cy="50" r="44" stroke="#9C6ADE" stroke-width="1.2" opacity="0.4"/>
      <path d="M50 10C55 30,70 40,90 50C70 55,60 70,50 90C45 70,30 60,10 50C30 45,40 30,50 10Z" stroke="#9C6ADE" stroke-width="1" fill="none" opacity="0.5"/>
      <circle cx="50" cy="50" r="7" stroke="#9C6ADE" stroke-width="1.2" opacity="0.4"/>
    </svg>
    <div class="hero-name">Bisleri</div>
    <div class="hero-aka">Dave — XR Developer</div>
    <div class="hero-sub">Building worlds you can walk into.</div>
  </div>

  <!-- BADGES -->
  <div class="badges fi">
    <span class="badge o">XR / VR / AR</span>
    <span class="badge b">Unity 3D</span>
    <span class="badge p">Blender</span>
    <span class="badge g">Frontend</span>
    <span class="badge o">Creative Dev</span>
  </div>

  <div class="divider"></div>

  <!-- ABOUT -->
  <div class="card fi">
    <div class="card-head">
      <div class="card-icon o">▸</div>
      <div class="card-title">About</div>
    </div>
    <div class="card-body">
      <p>I'm Dave — most people know me as <span class="hl">Bisleri</span>. I build immersive experiences. XR is my main thing — I spend most of my time inside <span class="hl-b">Unity</span> and <span class="hl">Blender</span>, making things that blur the line between screen and space.</p>
      <p>I also do frontend work and some backend when the project needs it. I like shipping things that feel good to use.</p>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="card fi">
    <div class="card-head">
      <div class="card-icon b">⚡</div>
      <div class="card-title">Stack</div>
    </div>
    <div class="tech-grid">
      <div class="tech-item">
        <span class="tech-emoji">🎮</span>
        <div class="tech-name">Unity 3D</div>
        <div class="tech-note">Primary engine</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🧊</span>
        <div class="tech-name">Blender</div>
        <div class="tech-note">3D modeling</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🥽</span>
        <div class="tech-name">XR / VR / AR</div>
        <div class="tech-note">Immersive dev</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">⚛️</span>
        <div class="tech-name">React</div>
        <div class="tech-note">Frontend</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🟨</span>
        <div class="tech-name">JavaScript</div>
        <div class="tech-note">Web</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🔷</span>
        <div class="tech-name">C#</div>
        <div class="tech-note">Unity scripting</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🗄️</span>
        <div class="tech-name">Backend</div>
        <div class="tech-note">When needed</div>
      </div>
      <div class="tech-item">
        <span class="tech-emoji">🐙</span>
        <div class="tech-name">Git</div>
        <div class="tech-note">Version control</div>
      </div>
    </div>
  </div>

  <!-- SKILLS -->
  <div class="card fi">
    <div class="card-head">
      <div class="card-icon r">📊</div>
      <div class="card-title">Skills</div>
    </div>
    <div class="stats">
      <div class="stat-row">
        <div class="stat-label">Unity 3D</div>
        <div class="stat-track"><div class="stat-fill o" style="width:92%"></div></div>
        <div class="stat-pct">92</div>
      </div>
      <div class="stat-row">
        <div class="stat-label">Blender</div>
        <div class="stat-track"><div class="stat-fill p" style="width:85%"></div></div>
        <div class="stat-pct">85</div>
      </div>
      <div class="stat-row">
        <div class="stat-label">XR Development</div>
        <div class="stat-track"><div class="stat-fill r" style="width:90%"></div></div>
        <div class="stat-pct">90</div>
      </div>
      <div class="stat-row">
        <div class="stat-label">Frontend</div>
        <div class="stat-track"><div class="stat-fill b" style="width:75%"></div></div>
        <div class="stat-pct">75</div>
      </div>
      <div class="stat-row">
        <div class="stat-label">Backend</div>
        <div class="stat-track"><div class="stat-fill g" style="width:50%"></div></div>
        <div class="stat-pct">50</div>
      </div>
      <div class="stat-row">
        <div class="stat-label">3D Art / Design</div>
        <div class="stat-track"><div class="stat-fill y" style="width:80%"></div></div>
        <div class="stat-pct">80</div>
      </div>
    </div>
  </div>

  <div class="divider"></div>

  <!-- CTA -->
  <div class="cta fi">
    <div class="cta-title">Let's Build Something</div>
    <div class="cta-text">If you're into XR, 3D, or just making cool things — hit me up.</div>
    <div class="cta-btns">
      <a class="btn pri" href="#">Follow</a>
      <a class="btn sec" href="#">Projects</a>
      <a class="btn sec" href="#">Contact</a>
    </div>
  </div>

  <!-- FOOTER -->
  <div class="footer fi">
    <div class="mark" style="font-family: 'Courier New', monospace; font-size: 14px; letter-spacing: 2px;">▓█▓█▓</div>
    <div class="sig">BUILT DIFFERENT</div>
    <div class="line" style="margin-top: 10px;">Made by <span style="color: var(--orange-light);">Bisleri</span></div>
    <div class="line" style="opacity: 0.3; font-family: 'Courier New', monospace; font-size: 10px;">░▒▓ XR DEV ▓▒░</div>
  </div>

</div>
</body>
</html>
