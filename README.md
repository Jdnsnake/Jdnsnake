# Jdnsnake.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>GamesGo — Learn Board Games</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Sora:wght@400;600;700;800&family=Inter:wght@400;500;600&display=swap');
    :root {
      --teal:#0D9488;--teal-dark:#0A7970;--teal-mid:#14B8A6;
      --teal-light:#CCFBF1;--teal-pale:#F0FDF9;
      --amber:#F59E0B;--amber-dark:#D97706;--amber-light:#FEF3C7;
      --ink:#1C2B2A;--muted:#4B6B68;--border:#D1FAF4;--bg:#F8FFFE;
    }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
    html{scroll-behavior:smooth;}
    body{font-family:'Inter',sans-serif;background:var(--bg);color:var(--ink);min-height:100vh;}
    h1,h2,h3,h4,h5{font-family:'Sora',sans-serif;}
    a{text-decoration:none;color:inherit;}
    .page{display:none;}.page.active{display:block;}
    .nav{position:sticky;top:0;z-index:100;background:rgba(248,255,254,0.93);backdrop-filter:blur(14px);border-bottom:1px solid var(--border);}
    .nav-inner{max-width:1120px;margin:0 auto;padding:0 24px;height:64px;display:flex;align-items:center;justify-content:space-between;}
    .nav-logo{font-family:'Sora',sans-serif;font-weight:800;font-size:1.2rem;color:var(--teal);display:flex;align-items:center;gap:8px;cursor:pointer;}
    .nav-links{display:flex;align-items:center;gap:28px;}
    .nav-links a{font-size:0.875rem;font-weight:500;color:var(--muted);transition:color 0.15s;}
    .nav-links a:hover{color:var(--ink);}
    .nav-back{display:none;align-items:center;gap:8px;font-size:0.875rem;font-weight:600;color:var(--teal);cursor:pointer;border:none;background:none;font-family:'Inter',sans-serif;}
    .nav-back:hover{color:var(--teal-dark);}
    .btn-amber{background:var(--amber);color:var(--ink);font-family:'Sora',sans-serif;font-weight:700;padding:12px 24px;border-radius:12px;border:none;cursor:pointer;transition:background 0.15s,transform 0.1s;display:inline-block;font-size:0.9rem;}
    .btn-amber:hover{background:var(--amber-dark);}
    .btn-amber:active{transform:scale(0.97);}
    .btn-outline{background:white;color:var(--teal);font-family:'Sora',sans-serif;font-weight:600;padding:12px 24px;border-radius:12px;border:2px solid var(--teal);cursor:pointer;transition:background 0.15s;display:inline-block;font-size:0.9rem;}
    .btn-outline:hover{background:var(--teal-light);}
    .badge{background:var(--amber-light);color:var(--amber-dark);font-family:'Sora',sans-serif;font-size:0.72rem;font-weight:700;padding:4px 12px;border-radius:999px;display:inline-block;}
    .badge-teal{background:var(--teal-light);color:var(--teal-dark);font-family:'Sora',sans-serif;font-size:0.72rem;font-weight:700;padding:4px 12px;border-radius:999px;display:inline-block;}
    /* HOME */
    .home-hero{max-width:1120px;margin:0 auto;padding:80px 24px 64px;display:grid;grid-template-columns:1fr 1fr;gap:64px;align-items:center;}
    .home-hero h1{font-size:clamp(2.2rem,5vw,3.4rem);line-height:1.12;font-weight:800;margin:16px 0 20px;}
    .home-hero p{color:var(--muted);line-height:1.7;font-size:1.05rem;max-width:440px;margin-bottom:32px;}
    .hero-cta{display:flex;gap:14px;flex-wrap:wrap;}
    .dice-cluster{display:grid;grid-template-columns:1fr 1fr;gap:16px;max-width:320px;}
    .dice-face{background:white;border:2px solid var(--border);border-radius:20px;aspect-ratio:1;display:flex;align-items:center;justify-content:center;font-size:2.4rem;box-shadow:0 4px 16px rgba(13,148,136,0.08);transition:transform 0.2s;}
    .dice-face:hover{transform:rotate(-6deg) scale(1.06);}
    .dice-face.featured{background:var(--teal);grid-column:span 2;aspect-ratio:2/1;font-size:3rem;}
    .stats-bar{background:var(--teal);padding:28px 24px;}
    .stats-inner{max-width:1120px;margin:0 auto;display:flex;justify-content:space-around;flex-wrap:wrap;gap:20px;}
    .stat-num{font-family:'Sora',sans-serif;font-weight:800;font-size:1.8rem;color:white;}
    .stat-label{font-size:0.78rem;color:var(--teal-light);margin-top:4px;}
    .games-section{max-width:1120px;margin:0 auto;padding:72px 24px;}
    .section-header{margin-bottom:40px;}
    .section-header h2{font-size:1.8rem;font-weight:800;margin-top:10px;}
    .section-header p{color:var(--muted);margin-top:8px;font-size:0.95rem;}
    .games-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:24px;}
    .game-card{background:white;border:1.5px solid var(--border);border-radius:20px;overflow:hidden;cursor:default;transition:box-shadow 0.2s,transform 0.2s;user-select:none;}
    .game-card:hover{box-shadow:0 12px 40px rgba(13,148,136,0.13);transform:translateY(-3px);}
    .game-card-thumb{height:160px;display:flex;align-items:center;justify-content:center;font-size:4rem;position:relative;}
    .game-card-body{padding:22px;}
    .game-card-body h3{font-size:1.1rem;font-weight:700;margin-bottom:6px;}
    .game-card-body p{color:var(--muted);font-size:0.875rem;line-height:1.55;margin-bottom:16px;}
    .game-meta{display:flex;gap:10px;flex-wrap:wrap;font-size:0.75rem;color:var(--muted);}
    .game-meta span{background:var(--teal-pale);padding:3px 10px;border-radius:999px;font-weight:500;}
    .card-cta{margin-top:18px;display:flex;align-items:center;justify-content:space-between;}
    .learn-btn-wrap{position:relative;display:inline-block;}
    .learn-btn{background:var(--teal);color:white;font-family:'Sora',sans-serif;font-weight:700;font-size:0.82rem;padding:9px 18px;border-radius:10px;border:none;cursor:pointer;transition:background 0.18s,transform 0.15s,box-shadow 0.18s;position:relative;z-index:1;}
    .learn-btn:hover{background:var(--teal-dark);transform:scale(1.06);box-shadow:0 6px 20px rgba(13,148,136,0.35);}
    .btn-critter{position:absolute;bottom:100%;opacity:0;pointer-events:none;z-index:10;}
    .btn-critter.snake-svg{left:-8px;}
    .btn-critter.pawn-svg{right:-8px;}
    .learn-btn-wrap:hover .btn-critter.snake-svg{animation:snakePop 0.55s cubic-bezier(0.22,1.4,0.36,1) forwards;}
    .learn-btn-wrap:hover .btn-critter.pawn-svg{animation:pawnPop 0.55s cubic-bezier(0.22,1.4,0.36,1) 0.07s forwards;}
    @keyframes snakePop{
      0%{opacity:0;transform:translateY(18px) rotate(-20deg) scale(0.4);}
      60%{opacity:1;transform:translateY(-22px) rotate(10deg) scale(1.15);}
      80%{transform:translateY(-18px) rotate(-5deg) scale(1);}
      100%{opacity:1;transform:translateY(-20px) rotate(0deg) scale(1);}
    }
    @keyframes pawnPop{
      0%{opacity:0;transform:translateY(18px) rotate(20deg) scale(0.4);}
      60%{opacity:1;transform:translateY(-26px) rotate(-8deg) scale(1.2);}
      80%{transform:translateY(-20px) rotate(4deg) scale(1);}
      100%{opacity:1;transform:translateY(-22px) rotate(0deg) scale(1);}
    }
    .game-card.coming-soon{opacity:0.5;cursor:default;pointer-events:none;}
    .coming-badge{position:absolute;top:12px;right:12px;background:rgba(0,0,0,0.15);color:white;font-size:0.68rem;font-weight:700;font-family:'Sora',sans-serif;padding:3px 10px;border-radius:999px;}
    /* TUTORIAL */
    .tutorial-hero{background:var(--teal);padding:64px 24px;}
    .tutorial-hero-inner{max-width:1120px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;}
    .tutorial-hero h1{font-size:clamp(2rem,4.5vw,3rem);color:white;line-height:1.15;font-weight:800;margin:14px 0 18px;}
    .tutorial-hero p{color:var(--teal-light);line-height:1.7;font-size:1rem;margin-bottom:28px;}
    .hero-stats{display:flex;gap:28px;flex-wrap:wrap;}
    .hero-stat .val{font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;color:var(--amber);}
    .hero-stat .lbl{font-size:0.75rem;color:var(--teal-light);}
    .board-preview{display:grid;grid-template-columns:repeat(10,1fr);gap:3px;border-radius:14px;overflow:hidden;border:3px solid rgba(255,255,255,0.3);max-width:300px;}
    .bc{aspect-ratio:1;display:flex;align-items:center;justify-content:center;font-size:0.45rem;font-weight:700;font-family:'Sora',sans-serif;}
    .bc-a{background:rgba(255,255,255,0.15);color:rgba(255,255,255,0.8);}
    .bc-b{background:rgba(255,255,255,0.08);color:rgba(255,255,255,0.6);}
    .bc-snake{background:#FEE2E2;color:#DC2626;}
    .bc-ladder{background:var(--amber-light);color:var(--amber-dark);}
    .bc-win{background:var(--amber);color:var(--ink);font-size:0.6rem;}
    .tutorial-content{max-width:1120px;margin:0 auto;padding:72px 24px;}
    .steps-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:20px;margin-top:32px;}
    .step-card{background:white;border:1.5px solid var(--border);border-radius:18px;padding:26px;transition:box-shadow 0.2s;}
    .step-card:hover{box-shadow:0 8px 28px rgba(13,148,136,0.09);}
    .step-num{width:30px;height:30px;border-radius:50%;background:var(--teal);color:white;font-family:'Sora',sans-serif;font-weight:800;font-size:0.8rem;display:flex;align-items:center;justify-content:center;margin-bottom:14px;}
    .step-card h3{font-size:0.95rem;font-weight:700;margin-bottom:8px;}
    .step-card p{color:var(--muted);font-size:0.875rem;line-height:1.6;}
    .two-col{display:grid;grid-template-columns:1fr 1fr;gap:48px;align-items:start;margin-top:64px;}
    .rule-card{background:white;border-left:4px solid var(--amber);border-radius:12px;padding:20px 22px;margin-bottom:14px;}
    .rule-card h4{font-size:0.9rem;font-weight:700;margin-bottom:6px;}
    .rule-card p{color:var(--muted);font-size:0.85rem;line-height:1.6;}
    .positions-box{background:white;border:1.5px solid var(--border);border-radius:18px;padding:24px;}
    .pos-label{font-size:0.75rem;font-weight:700;color:var(--muted);font-family:'Sora',sans-serif;margin-bottom:12px;}
    .sl-row{display:flex;align-items:center;gap:12px;padding:9px 0;border-bottom:1px solid var(--teal-pale);}
    .sl-row:last-child{border-bottom:none;}
    .sl-icon{width:36px;height:36px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:1.1rem;flex-shrink:0;}
    .sl-row span{font-size:0.875rem;}
    .tips-section{background:var(--teal-pale);padding:72px 24px;margin-top:72px;}
    .tips-grid{max-width:1120px;margin:32px auto 0;display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:16px;}
    .tip-card{background:white;border:1.5px solid var(--border);border-radius:16px;padding:22px;display:flex;gap:14px;align-items:flex-start;}
    .tip-card .ico{font-size:1.5rem;flex-shrink:0;}
    .tip-card h4{font-size:0.9rem;font-weight:700;margin-bottom:5px;}
    .tip-card p{color:var(--muted);font-size:0.85rem;line-height:1.55;}
    .faq-section{max-width:720px;margin:72px auto;padding:0 24px;}
    details{background:white;border:1.5px solid var(--border);border-radius:14px;padding:18px 22px;margin-bottom:12px;cursor:pointer;}
    details[open]{border-color:var(--teal);}
    summary{font-family:'Sora',sans-serif;font-weight:600;font-size:0.95rem;list-style:none;display:flex;justify-content:space-between;align-items:center;}
    summary::after{content:'+';color:var(--teal);font-size:1.2rem;font-weight:700;}
    details[open] summary::after{content:'−';}
    details p{margin-top:12px;color:var(--muted);line-height:1.65;font-size:0.9rem;}
    footer{background:var(--teal);padding:40px 24px;text-align:center;}
    footer .logo{font-family:'Sora',sans-serif;font-weight:800;font-size:1.15rem;color:white;margin-bottom:8px;}
    footer p{color:var(--teal-light);font-size:0.85rem;}
    footer .copy{color:#99F6E4;font-size:0.75rem;margin-top:14px;}
    @keyframes celebBounce{0%{opacity:0;transform:scale(0.3) rotate(-15deg);}60%{transform:scale(1.2) rotate(5deg);}100%{opacity:1;transform:scale(1) rotate(0);}}
    @keyframes celebFadeUp{from{opacity:0;transform:translateY(20px);}to{opacity:1;transform:translateY(0);}}
    @keyframes slideIn{from{opacity:0;transform:translateX(12px);}to{opacity:1;transform:translateX(0);}}
      .home-hero{grid-template-columns:1fr;gap:40px;padding:48px 20px 40px;}
      .dice-cluster{display:none;}
      .tutorial-hero-inner{grid-template-columns:1fr;}
      .board-preview{display:none;}
      .two-col{grid-template-columns:1fr;gap:32px;}
      .nav-links{display:none;}
    }
    @media(max-width:480px){.games-grid{grid-template-columns:1fr;}}
  </style>
</head>
<body>

<!-- NAV -->
<nav class="nav">
  <div class="nav-inner">
    <div class="nav-logo" onclick="showPage('home')">🎲 GamesGo</div>
    <div id="nav-home-links" class="nav-links">
      <a href="#games">Games</a>
      <a href="#about">About</a>
      <button class="btn-amber" style="padding:9px 20px;font-size:0.82rem;" onclick="document.getElementById('games').scrollIntoView({behavior:'smooth'})">Browse Games</button>
    </div>
    <button id="nav-back-btn" class="nav-back" onclick="showPage('home')" style="display:none;">
      ← All Games
    </button>
  </div>
</nav>

<!-- ══ HOME ══ -->
<div id="page-home" class="page active">
  <section class="home-hero">
    <div>
      <span class="badge">Free Game Tutorials</span>
      <h1>Learn any board game, fast.</h1>
      <p>Clear step-by-step tutorials for classic board games. No experience needed — pick a game and start playing.</p>
      <div class="hero-cta">
        <button class="btn-amber" onclick="document.getElementById('games').scrollIntoView({behavior:'smooth'})">Browse Games</button>
      </div>
    </div>
    <div style="display:flex;justify-content:center;">
      <div class="dice-cluster">
        <div class="dice-face featured">🎲</div>
        <div class="dice-face">🐍</div>
        <div class="dice-face">🪜</div>
      </div>
    </div>
  </section>

  <div class="stats-bar">
    <div class="stats-inner">
      <div style="text-align:center;"><div class="stat-num">1</div><div class="stat-label">Game available now</div></div>
      <div style="text-align:center;"><div class="stat-num">5 min</div><div class="stat-label">To learn each game</div></div>
      <div style="text-align:center;"><div class="stat-num">Free</div><div class="stat-label">Always & forever</div></div>
      <div style="text-align:center;"><div class="stat-num">All ages</div><div class="stat-label">Beginner friendly</div></div>
    </div>
  </div>

  <section class="games-section" id="games">
    <div class="section-header">
      <span class="badge-teal">Game Library</span>
      <h2>Pick a game to learn</h2>
      <p>Each tutorial covers setup, rules, tips, and common questions.</p>
    </div>
    <div class="games-grid">

      <div class="game-card" style="cursor:default;">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#CCFBF1 0%,#99F6E4 100%);">
          <span>🐍🪜</span>
        </div>
        <div class="game-card-body">
          <h3>Snake & Ladders</h3>
          <p>The classic luck-based race — climb ladders, dodge snakes, and be first to reach square 100.</p>
          <div class="game-meta">
            <span>2–6 players</span><span>~15 min</span>
          </div>
          <div class="card-cta">
            <span class="badge-teal" id="sl-card-badge" style="font-size:0.7rem;">Available now</span>
            <div style="display:flex;gap:8px;">
              <button class="learn-btn" style="background:#0D9488;" onclick="showPage('sl-game')">🎮 Play now</button>
              <button id="sl-card-btn" class="learn-btn" onclick="showPage('snake-ladders')">Learn to play</button>
            </div>
          </div>
        </div>
      </div>

      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#FEF3C7 0%,#FDE68A 100%);">
          <span>♟️</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Chess</h3>
          <p>The ultimate strategy game. Learn piece movement and start thinking ahead.</p>
          <div class="game-meta"><span>2 players</span><span>Ages 6+</span></div>
        </div>
      </div>

      <div class="game-card" style="cursor:default;">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#FEE2E2 0%,#FECACA 100%);">
          <span>🎴</span>
        </div>
        <div class="game-card-body">
          <h3>Uno</h3>
          <p>Match colors and numbers, play action cards, and be first to shout "Uno!" 6 versions available.</p>
          <div class="game-meta"><span>2–10 players</span><span>6 versions</span></div>
          <div class="card-cta">
            <span class="badge-teal" id="uno-card-badge" style="font-size:0.7rem;">Available now</span>
            <button class="learn-btn" style="background:#DC2626;" onclick="showPage('uno-versions')">Pick a version</button>
          </div>
        </div>
      </div>

    </div>
  </section>

  <section id="about" style="background:var(--teal);padding:72px 24px;">
    <div style="max-width:700px;margin:0 auto;text-align:center;">
      <span class="badge" style="background:rgba(255,255,255,0.2);color:white;">About GamesGo</span>
      <h2 style="color:white;font-size:1.9rem;margin:16px 0 16px;">Games are better when everyone knows how to play.</h2>
      <p style="color:var(--teal-light);line-height:1.75;font-size:1rem;">GamesGo is a free library of board game tutorials for beginners. No fluff — just clear rules, visual guides, and tips that get you playing in minutes. More games added regularly.</p>
    </div>
  </section>

  <footer>
    <div class="logo">🎲 GamesGo</div>
    <p>Your go-to guide for board games — beginner to confident player.</p>
    <p class="copy">© 2026 GamesGo. All rights reserved.</p>
  </footer>
</div>


<!-- ══ UNO VERSIONS PAGE ══ -->
<div id="page-uno-versions" class="page">
  <section style="background:linear-gradient(135deg,#EF4444,#DC2626);padding:64px 24px 48px;">
    <div style="max-width:900px;margin:0 auto;text-align:center;">
      <span class="badge" style="background:rgba(255,255,255,0.2);color:white;">Card Games</span>
      <h1 style="font-family:'Sora',sans-serif;font-weight:800;font-size:clamp(2rem,5vw,3rem);color:white;margin:16px 0 14px;">Which Uno are you playing?</h1>
      <p style="color:#FECACA;font-size:1rem;line-height:1.7;max-width:520px;margin:0 auto;">Six versions, each with its own twist. Pick one to learn how to play.</p>
    </div>
  </section>

  <div style="max-width:1000px;margin:0 auto;padding:48px 24px;">
    <div style="display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:22px;">

      <!-- Standard -->
      <div class="game-card" onclick="showPage('uno-standard')" style="cursor:pointer;">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#FEE2E2,#FCA5A5);">
          <span style="font-size:3.5rem;">🟥🟦🟩🟨</span>
        </div>
        <div class="game-card-body">
          <h3>Standard Uno</h3>
          <p>The classic 108-card deck. Match colors and numbers, play action cards, and shout "Uno!" first.</p>
          <div class="game-meta"><span>2–10 players</span><span>Ages 7+</span></div>
          <div class="card-cta" style="margin-top:14px;">
            <span class="badge-teal" style="font-size:0.7rem;">Available now</span>
            <button class="learn-btn">Learn to play</button>
          </div>
        </div>
      </div>

      <!-- Flip -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#1E293B,#334155);">
          <span style="font-size:3.5rem;">🌗</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Uno Flip!</h3>
          <p>Double-sided deck with a brutal dark side. Flip cards switch everyone to harsher penalties.</p>
          <div class="game-meta"><span>2–10 players</span><span>Light & Dark sides</span></div>
        </div>
      </div>

      <!-- Show Em No Mercy -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#7F1D1D,#991B1B);">
          <span style="font-size:3.5rem;">💀</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Show 'Em No Mercy</h3>
          <p>Stackable draw cards, discard all action, and elimination if you hold 25+ cards.</p>
          <div class="game-meta"><span>2–10 players</span><span>Brutal edition</span></div>
        </div>
      </div>

      <!-- All Wild -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#4C1D95,#6D28D9);">
          <span style="font-size:3.5rem;">🃏</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Uno All Wild</h3>
          <p>Every single card is a Wild card. No colors, no numbers — just chaos.</p>
          <div class="game-meta"><span>2–10 players</span><span>All wild deck</span></div>
        </div>
      </div>

      <!-- Flex -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#065F46,#059669);">
          <span style="font-size:3.5rem;">⚡</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Uno Flex</h3>
          <p>Power cards let you change a card's color or unlock flex actions on specialty cards.</p>
          <div class="game-meta"><span>2–10 players</span><span>Power cards</span></div>
        </div>
      </div>

      <!-- DOS -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#1E3A5F,#2563EB);">
          <span style="font-size:3.5rem;">2️⃣</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>DOS</h3>
          <p>Two center piles, card combinations, and a totally different way to win.</p>
          <div class="game-meta"><span>2–6 players</span><span>Spin-off</span></div>
        </div>
      </div>

      <!-- Liar's Uno -->
      <div class="game-card coming-soon">
        <div class="game-card-thumb" style="background:linear-gradient(135deg,#713F12,#92400E);">
          <span style="font-size:3.5rem;">🤥</span><div class="coming-badge">Coming soon</div>
        </div>
        <div class="game-card-body">
          <h3>Liar's Uno</h3>
          <p>Play cards face-down and bluff about what you played — until someone calls you out.</p>
          <div class="game-meta"><span>2–10 players</span><span>Bluffing edition</span></div>
        </div>
      </div>

    </div>
  </div>

  <footer>
    <div class="logo">🎲 GamesGo</div>
    <p>Your go-to guide for board games — beginner to confident player.</p>
    <p class="copy">© 2026 GamesGo. All rights reserved.</p>
  </footer>
</div>

<!-- ══ STANDARD UNO TUTORIAL ══ -->
<div id="page-uno-standard" class="page">
  <section style="background:linear-gradient(135deg,#DC2626,#B91C1C);padding:64px 24px;">
    <div style="max-width:1120px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:60px;align-items:center;">
      <div>
        <span class="badge">Card Games · Classic</span>
        <h1 style="font-family:'Sora',sans-serif;font-weight:800;font-size:clamp(2rem,4.5vw,3rem);color:white;line-height:1.15;margin:14px 0 18px;">Standard Uno</h1>
        <p style="color:#FECACA;line-height:1.7;font-size:1rem;margin-bottom:28px;">The classic 108-card game of matching colors and numbers. Play action cards, block your opponents, and be first to empty your hand.</p>
        <div style="display:flex;gap:28px;flex-wrap:wrap;">
          <div><div style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;color:#FCA5A5;">2–10</div><div style="font-size:0.75rem;color:#FECACA;">Players</div></div>
          <div><div style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;color:#FCA5A5;">~30 min</div><div style="font-size:0.75rem;color:#FECACA;">Per game</div></div>
          <div><div style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;color:#FCA5A5;">108</div><div style="font-size:0.75rem;color:#FECACA;">Cards</div></div>
        </div>
      </div>
      <div style="display:flex;justify-content:center;align-items:center;position:relative;height:180px;pointer-events:none;">
        <div style="position:absolute;transform:rotate(-20deg) translateX(-60px);background:#EF4444;border:3px solid white;border-radius:10px;width:70px;height:100px;display:flex;align-items:center;justify-content:center;font-family:'Sora',sans-serif;font-weight:800;font-size:1.5rem;color:white;box-shadow:0 4px 12px rgba(0,0,0,0.3);">7</div>
        <div style="position:absolute;transform:rotate(-8deg) translateX(-20px);background:#3B82F6;border:3px solid white;border-radius:10px;width:70px;height:100px;display:flex;align-items:center;justify-content:center;font-family:'Sora',sans-serif;font-weight:800;font-size:1.5rem;color:white;box-shadow:0 4px 12px rgba(0,0,0,0.3);">⊘</div>
        <div style="position:absolute;transform:rotate(6deg) translateX(20px);background:#22C55E;border:3px solid white;border-radius:10px;width:70px;height:100px;display:flex;align-items:center;justify-content:center;font-family:'Sora',sans-serif;font-weight:800;font-size:1.5rem;color:white;box-shadow:0 4px 12px rgba(0,0,0,0.3);">+2</div>
        <div style="position:absolute;transform:rotate(20deg) translateX(60px);background:#1C2B2A;border:3px solid white;border-radius:10px;width:70px;height:100px;display:flex;align-items:center;justify-content:center;font-family:'Sora',sans-serif;font-weight:800;font-size:1.1rem;color:white;box-shadow:0 4px 12px rgba(0,0,0,0.3);">🌈</div>
      </div>
    </div>
  </section>

  <!-- HOW TO PLAY SLIDESHOW -->
  <div style="max-width:1120px;margin:0 auto;padding:56px 24px 0;">
    <span class="badge-teal">Step by Step</span>
    <h2 style="font-size:1.8rem;font-weight:800;margin-top:10px;">How to play Standard Uno</h2>
    <p style="color:var(--muted);margin-top:8px;">Seven steps and you're ready to shout Uno!</p>

    <div id="uno-slideshow" style="margin-top:32px;background:white;border:1.5px solid var(--border);border-radius:24px;overflow:hidden;">
      <div style="display:grid;grid-template-columns:1fr 1fr;min-height:400px;">
        <!-- Left: canvas animation -->
        <div style="padding:28px;display:flex;flex-direction:column;align-items:center;justify-content:center;background:var(--teal-pale);border-right:1.5px solid var(--border);">
          <canvas id="unoCanvas" width="300" height="260" style="border-radius:12px;max-width:100%;"></canvas>
          <p id="uno-canvas-caption" style="font-size:0.72rem;color:var(--muted);margin-top:10px;font-style:italic;text-align:center;"></p>
        </div>
        <!-- Right: text -->
        <div style="padding:36px 32px;display:flex;flex-direction:column;justify-content:center;">
          <div id="uno-slide-num" style="font-family:'Sora',sans-serif;font-weight:800;font-size:3rem;color:#FEE2E2;line-height:1;margin-bottom:8px;"></div>
          <h3 id="uno-slide-title" style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;margin-bottom:14px;color:var(--ink);"></h3>
          <p id="uno-slide-desc" style="color:var(--muted);line-height:1.75;font-size:0.95rem;"></p>
          <div style="display:flex;gap:12px;margin-top:28px;align-items:center;">
            <button id="uno-btn-prev" onclick="unoStep(unoCurrentStep-1)" style="background:white;border:2px solid var(--border);color:var(--muted);font-family:'Sora',sans-serif;font-weight:700;font-size:0.85rem;padding:10px 20px;border-radius:10px;cursor:pointer;">← Back</button>
            <button id="uno-btn-next" onclick="unoNextStep()" style="background:#DC2626;color:white;font-family:'Sora',sans-serif;font-weight:700;font-size:0.85rem;padding:10px 24px;border-radius:10px;border:none;cursor:pointer;">Next →</button>
            <span id="uno-slide-counter" style="font-size:0.78rem;color:var(--muted);margin-left:auto;font-family:'Sora',sans-serif;"></span>
          </div>
        </div>
      </div>
      <!-- Step tabs -->
      <div style="display:flex;border-top:1.5px solid var(--border);" id="uno-dots"></div>
    </div>
  </div>

  <!-- CARD TYPES -->
  <div style="max-width:1120px;margin:48px auto 0;padding:0 24px;">
    <h2 style="font-size:1.6rem;font-weight:800;margin-bottom:24px;">Card types</h2>
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:16px;">
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #EF4444;">
        <div style="font-size:1.8rem;margin-bottom:8px;">0–9</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Number Cards</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">76 cards total. Match by color or number to the discard pile.</p>
      </div>
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #3B82F6;">
        <div style="font-size:1.8rem;margin-bottom:8px;">⊘</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Skip</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">Next player loses their turn. Available in all 4 colors.</p>
      </div>
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #22C55E;">
        <div style="font-size:1.8rem;margin-bottom:8px;">↩️</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Reverse</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">Flips the direction of play. In a 2-player game, acts like a Skip.</p>
      </div>
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #F59E0B;">
        <div style="font-size:1.8rem;margin-bottom:8px;">+2</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Draw Two</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">Next player draws 2 cards and loses their turn.</p>
      </div>
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #7C3AED;">
        <div style="font-size:1.8rem;margin-bottom:8px;">🌈</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Wild</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">Play anytime. You choose the new color for the next player.</p>
      </div>
      <div style="background:white;border:1.5px solid var(--border);border-radius:16px;padding:20px;border-top:4px solid #1C2B2A;">
        <div style="font-size:1.8rem;margin-bottom:8px;">+4</div>
        <h4 style="font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;margin-bottom:6px;">Wild Draw Four</h4>
        <p style="color:var(--muted);font-size:0.82rem;line-height:1.55;">Next player draws 4, you choose color. Only legal if you have no matching color card.</p>
      </div>
    </div>
  </div>

  <!-- FAQ -->
  <section style="max-width:720px;margin:56px auto;padding:0 24px;">
    <div style="text-align:center;margin-bottom:32px;">
      <span class="badge-teal">FAQ</span>
      <h2 style="font-size:1.8rem;font-weight:800;margin-top:12px;">Common questions</h2>
    </div>
    <details><summary>What happens if I forget to say "Uno"?</summary><p>If you play your second-to-last card and forget to say "Uno!" before the next player takes their turn, you must draw 2 penalty cards when caught.</p></details>
    <details><summary>Can I stack Draw Two cards?</summary><p>In official rules, no — you cannot stack +2 on +2. The next player must draw 2 and skip. House rules often allow stacking though.</p></details>
    <details><summary>What if the deck runs out?</summary><p>Shuffle the discard pile (except the top card) to form a new draw pile and continue.</p></details>
    <details><summary>Who wins if two players go out at the same time?</summary><p>This can't happen — only one player goes at a time. The first player to play their last card wins immediately.</p></details>
  </section>

  <div style="text-align:center;padding:0 24px 56px;">
    <button class="btn-outline" onclick="showPage('uno-versions')">← Back to Uno versions</button>
  </div>

  <footer>
    <div class="logo">🎲 GamesGo</div>
    <p>Your go-to guide for board games — beginner to confident player.</p>
    <p class="copy">© 2026 GamesGo. All rights reserved.</p>
  </footer>
</div>


<div id="page-snake-ladders" class="page">

  <section class="tutorial-hero">
    <div class="tutorial-hero-inner">
      <div>
        <span class="badge">Board Games · Beginner</span>
        <h1>Snake & Ladders</h1>
        <p>One of the world's oldest board games — pure luck, no experience needed. Perfect for all ages.</p>
        <div class="hero-stats">
          <div class="hero-stat"><div class="val">2–6</div><div class="lbl">Players</div></div>
          <div class="hero-stat"><div class="val">~15 min</div><div class="lbl">Per game</div></div>
        </div>
      </div>
      <div style="display:flex;justify-content:flex-end;">
        <div>
          <div class="board-preview" id="board"></div>
          <p style="font-size:0.72rem;color:var(--teal-light);margin-top:10px;text-align:center;font-style:italic;">Simplified 10×10 preview</p>
        </div>
      </div>
    </div>
  </section>

  <div class="tutorial-content">
    <span class="badge-teal">Step by Step</span>
    <h2 style="font-size:1.8rem;font-weight:800;margin-top:10px;">How to play</h2>
    <p style="color:var(--muted);margin-top:8px;">Six steps and you're ready to play your first game.</p>

    <!-- INTERACTIVE SLIDESHOW -->
    <div id="slideshow" style="margin-top:36px;background:white;border:1.5px solid var(--border);border-radius:24px;overflow:hidden;">
      <!-- Main content -->
      <div style="display:grid;grid-template-columns:1fr 1fr;min-height:420px;">

        <!-- Left: canvas board -->
        <div style="padding:28px;display:flex;flex-direction:column;align-items:center;justify-content:center;background:var(--teal-pale);border-right:1.5px solid var(--border);">
          <canvas id="stepCanvas" width="300" height="300" style="border-radius:12px;max-width:100%;"></canvas>
          <p id="canvas-caption" style="font-size:0.72rem;color:var(--muted);margin-top:10px;font-style:italic;text-align:center;"></p>
        </div>

        <!-- Right: text -->
        <div style="padding:36px 32px;display:flex;flex-direction:column;justify-content:center;position:relative;">
          <!-- Default text panel -->
          <div id="slide-text-panel">
            <div id="slide-num" style="font-family:'Sora',sans-serif;font-weight:800;font-size:3rem;color:var(--teal-light);line-height:1;margin-bottom:8px;"></div>
            <h3 id="slide-title" style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.4rem;margin-bottom:14px;color:var(--ink);"></h3>
            <p id="slide-desc" style="color:var(--muted);line-height:1.75;font-size:0.95rem;"></p>
          </div>

          <!-- Roll-off panel (shown only on step 2) -->
          <div id="rolloff-panel" style="display:none;flex-direction:column;gap:10px;width:100%;">
            <h3 style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.1rem;color:var(--ink);margin-bottom:4px;">Who goes first?</h3>
            <div id="roll-results" style="display:flex;flex-direction:column;gap:8px;min-height:120px;"></div>
            <button id="rolloff-reset" onclick="resetRollOff()" style="display:none;background:var(--teal-light);border:1.5px solid var(--teal);color:var(--teal-dark);font-size:0.85rem;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;padding:9px 16px;border-radius:10px;margin-top:2px;">↺ Roll again</button>
          </div>

          <!-- Nav buttons -->
          <div style="display:flex;gap:12px;margin-top:28px;align-items:center;">
            <button id="btn-prev" onclick="prevStep()" style="background:white;border:2px solid var(--border);color:var(--muted);font-family:'Sora',sans-serif;font-weight:700;font-size:0.85rem;padding:10px 20px;border-radius:10px;cursor:pointer;">← Back</button>
            <button id="btn-next" onclick="nextStep()" style="background:var(--teal);color:white;font-family:'Sora',sans-serif;font-weight:700;font-size:0.85rem;padding:10px 24px;border-radius:10px;border:none;cursor:pointer;">Next →</button>
            <span id="slide-counter" style="font-size:0.78rem;color:var(--muted);margin-left:auto;font-family:'Sora',sans-serif;"></span>
          </div>
        </div>
      </div>

      <!-- Step tabs at bottom -->
      <div style="display:flex;border-top:1.5px solid var(--border);">
        <div id="dot-0" onclick="goStep(0)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;background:var(--teal);color:white;transition:background 0.2s,color 0.2s;">1</div>
        <div id="dot-1" onclick="goStep(1)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">2</div>
        <div id="dot-2" onclick="goStep(2)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">3</div>
        <div id="dot-3" onclick="goStep(3)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">4</div>
        <div id="dot-4" onclick="goStep(4)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">5</div>
        <div id="dot-5" onclick="goStep(5)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">6</div>
        <div id="dot-6" onclick="goStep(6)" style="flex:1;padding:14px 8px;text-align:center;cursor:pointer;font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;color:var(--muted);transition:background 0.2s,color 0.2s;">7</div>
      </div>
    </div>

    <div class="two-col">
      <div>
        <h2 style="font-size:1.6rem;font-weight:800;margin-bottom:20px;">The rules</h2>
        <div class="rule-card"><h4>Exact landing to win</h4><p>You must hit square 100 exactly. Overshoot and bounce back by the remainder.</p></div>
        <div class="rule-card"><h4>One die, standard play</h4><p>Standard play uses a single six-sided die. Some editions use two — check your box.</p></div>
        <div class="rule-card"><h4>Sharing squares is fine</h4><p>Multiple players can occupy the same square. Nobody gets knocked out.</p></div>
        <div class="rule-card"><h4>Heads & feet only</h4><p>Snakes activate on the head only. Ladders activate at the foot only. Landing on a body section does nothing.</p></div>
      </div>

      <div>
        <h2 style="font-size:1.6rem;font-weight:800;margin-bottom:20px;">Board positions</h2>
        <div class="positions-box">
          <div class="pos-label">LADDERS — climb up 🪜</div>
          <div class="sl-row"><div class="sl-icon" style="background:#DCFCE7;">🪜</div><span><strong>4 → 14</strong> — small early boost</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#DCFCE7;">🪜</div><span><strong>9 → 31</strong> — big early jump</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#DCFCE7;">🪜</div><span><strong>28 → 84</strong> — massive shortcut</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#DCFCE7;">🪜</div><span><strong>40 → 59</strong> — mid-game help</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#DCFCE7;">🪜</div><span><strong>51 → 67</strong> — steady climb</span></div>
          <div style="height:16px;"></div>
          <div class="pos-label">SNAKES — slide down 🐍</div>
          <div class="sl-row"><div class="sl-icon" style="background:#FEE2E2;">🐍</div><span><strong>17 → 7</strong> — early punisher</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#FEE2E2;">🐍</div><span><strong>54 → 34</strong> — brutal midpoint</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#FEE2E2;">🐍</div><span><strong>62 → 19</strong> — the heartbreaker</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#FEE2E2;">🐍</div><span><strong>87 → 24</strong> — near the end, worst fall</span></div>
          <div class="sl-row"><div class="sl-icon" style="background:#FEE2E2;">🐍</div><span><strong>99 → 78</strong> — so close, so painful</span></div>
        </div>
      </div>
    </div>
  </div>

  <section class="tips-section">
    <div style="max-width:1120px;margin:0 auto;text-align:center;">
      <span class="badge">Tips</span>
      <h2 style="font-size:1.8rem;font-weight:800;margin-top:12px;">Make the game more fun</h2>
    </div>
    <div class="tips-grid">
      <div class="tip-card"><div class="ico">🎉</div><div><h4>Laugh at the snakes</h4><p>Snake slides are the funniest moments — lean into it and keep the energy light.</p></div></div>
      <div class="tip-card"><div class="ico">🏡</div><div><h4>Try house rules</h4><p>Some families send you back to square 1 on a snake's head. Chaotic, but fun.</p></div></div>
      <div class="tip-card"><div class="ico">⏱️</div><div><h4>Set a time limit</h4><p>Agree on a time limit — whoever is furthest ahead when it ends wins.</p></div></div>
      <div class="tip-card"><div class="ico">🎨</div><div><h4>Personalise your token</h4><p>Use a coin, button, or small toy — it makes the game feel more personal.</p></div></div>
      <div class="tip-card"><div class="ico">📝</div><div><h4>Track wins over sessions</h4><p>Even a luck game gets competitive with a running tally.</p></div></div>
      <div class="tip-card"><div class="ico">👶</div><div><h4>Great for young kids</h4><p>Builds number recognition and counting without competitive pressure.</p></div></div>
    </div>
  </section>

  <section class="faq-section">
    <div style="text-align:center;margin-bottom:36px;">
      <span class="badge-teal">FAQ</span>
      <h2 style="font-size:1.8rem;font-weight:800;margin-top:12px;">Common questions</h2>
    </div>
    <details><summary>Do I need a specific roll to start?</summary><p>In standard play, no — you move from square 1 straight away on your first turn. Some editions require rolling a 6; check your board's instructions.</p></details>
    <details><summary>What if I roll more than needed to reach 100?</summary><p>You move to 100 then bounce back by the leftover squares. On 97 with a roll of 5: go to 100, back 2 — you land on 98.</p></details>
    <details><summary>Can two players share a square?</summary><p>Yes, multiple tokens can sit on the same square. Nobody is knocked out in standard rules.</p></details>
    <details><summary>What if I land on a snake's body or a ladder's middle?</summary><p>Nothing happens. Snakes only activate at the head; ladders only at the foot.</p></details>
    <details><summary>Is there any skill, or is it pure luck?</summary><p>Pure luck — the dice decides everything. That's the charm: anyone can win, making it great for all ages.</p></details>
    <details><summary>How many players can play?</summary><p>Most boards support 2–6 comfortably. Above 6 the game slows down, but there's no hard limit.</p></details>
  </section>

  <div style="text-align:center;padding:0 24px 64px;">
    <button class="btn-outline" onclick="showPage('home')">← Back to all games</button>
  </div>

  <!-- CELEBRATION OVERLAY -->
  <div id="celebrate-overlay" style="display:none;position:fixed;inset:0;z-index:200;background:rgba(13,148,136,0.97);flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:32px;">
    <canvas id="confetti-canvas" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;"></canvas>
    <div style="position:relative;z-index:2;">
      <div id="celebrate-emoji" style="font-size:5rem;margin-bottom:16px;animation:celebBounce 0.8s cubic-bezier(0.34,1.56,0.64,1) both;"></div>
      <h1 id="celebrate-title" style="font-family:'Sora',sans-serif;font-weight:800;font-size:clamp(1.8rem,5vw,3rem);color:white;margin-bottom:14px;animation:celebFadeUp 0.6s 0.2s both;"></h1>
      <p id="celebrate-sub" style="color:var(--teal-light);font-size:1.1rem;max-width:480px;line-height:1.7;margin:0 auto 32px;animation:celebFadeUp 0.6s 0.35s both;"></p>
      <div style="display:flex;gap:14px;justify-content:center;flex-wrap:wrap;animation:celebFadeUp 0.6s 0.5s both;">
        <button onclick="closeCelebrate()" style="background:var(--amber);color:var(--ink);font-family:'Sora',sans-serif;font-weight:800;font-size:1rem;padding:14px 28px;border-radius:14px;border:none;cursor:pointer;transition:transform 0.1s;">🎮 Browse more games</button>
        <button onclick="closeCelebrate()" style="background:rgba(255,255,255,0.15);color:white;font-family:'Sora',sans-serif;font-weight:700;font-size:1rem;padding:14px 28px;border-radius:14px;border:2px solid rgba(255,255,255,0.4);cursor:pointer;">← Back to tutorial</button>
      </div>
    </div>
  </div>

  <footer>
    <div class="logo">🎲 GamesGo</div>
    <p>Your go-to guide for board games — beginner to confident player.</p>
    <p class="copy">© 2026 GamesGo. All rights reserved.</p>
  </footer>
</div>

<!-- ══ LIVE GAME PAGE ══ -->
<div id="page-sl-game" class="page">
  <style>
    .game-board-wrap{display:grid;grid-template-columns:1fr 300px;gap:24px;max-width:980px;margin:0 auto;padding:28px 24px;}
    #gameCanvas{border-radius:16px;border:3px solid var(--teal);width:100%;display:block;}
    .game-panel{display:flex;flex-direction:column;gap:14px;position:sticky;top:72px;align-self:start;}
    .player-card{background:white;border:2px solid var(--border);border-radius:14px;padding:16px 18px;transition:border-color 0.2s,box-shadow 0.2s;}
    .player-card.active{border-color:var(--teal);box-shadow:0 4px 20px rgba(13,148,136,0.15);}
    .p-name{font-family:'Sora',sans-serif;font-weight:700;font-size:0.9rem;display:flex;align-items:center;gap:8px;}
    .p-sq{font-size:0.75rem;color:var(--muted);margin-top:4px;}
    .p-status{font-size:0.72rem;font-weight:600;margin-top:5px;font-family:'Sora',sans-serif;}
    .dice-wrap{background:white;border:2px solid var(--border);border-radius:14px;padding:18px;text-align:center;}
    .dice-wrap h4{font-family:'Sora',sans-serif;font-weight:700;font-size:0.85rem;margin-bottom:12px;color:var(--ink);}
    #gameDice{width:68px;height:68px;margin:0 auto 12px;display:block;cursor:pointer;transition:transform 0.15s;}
    #roll-game-btn{background:var(--amber);color:var(--ink);font-family:'Sora',sans-serif;font-weight:800;font-size:0.95rem;padding:11px 20px;border-radius:11px;border:none;cursor:pointer;transition:background 0.15s,transform 0.1s;width:100%;}
    #roll-game-btn:hover:not(:disabled){background:var(--amber-dark);transform:scale(1.03);}
    #roll-game-btn:disabled{background:#D1D5DB;color:#9CA3AF;cursor:not-allowed;transform:none;}
    .game-log{background:white;border:1.5px solid var(--border);border-radius:12px;padding:12px 14px;max-height:150px;overflow-y:auto;}
    .game-log h4{font-family:'Sora',sans-serif;font-weight:700;font-size:0.82rem;margin-bottom:6px;}
    .log-entry{font-size:0.77rem;color:var(--muted);padding:3px 0;border-bottom:1px solid #F0FDF9;line-height:1.4;}
    .log-entry:last-child{border:none;}
    #game-winner-banner{display:none;position:fixed;inset:0;z-index:300;background:rgba(13,148,136,0.97);flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:32px;}
    @media(max-width:700px){.game-board-wrap{grid-template-columns:1fr;}}
  </style>

  <div style="background:var(--teal);padding:18px 24px;display:flex;align-items:center;justify-content:space-between;">
    <div style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.05rem;color:white;">🐍🪜 Snake & Ladders — You vs AI</div>
    <button onclick="showPage('home')" style="background:rgba(255,255,255,0.15);color:white;border:1.5px solid rgba(255,255,255,0.3);font-family:'Sora',sans-serif;font-weight:600;font-size:0.82rem;padding:7px 16px;border-radius:9px;cursor:pointer;">✕ Exit</button>
  </div>

  <div class="game-board-wrap">
    <canvas id="gameCanvas" width="524" height="524"></canvas>

    <div class="game-panel">
      <div class="player-card active" id="pc-0">
        <div class="p-name"><span style="width:11px;height:11px;border-radius:50%;background:#F59E0B;display:inline-block;flex-shrink:0;"></span>You (Player)</div>
        <div class="p-sq" id="psq-0">Square: Start</div>
        <div class="p-status" id="pst-0" style="color:var(--teal);">Your turn — roll!</div>
      </div>
      <div class="player-card" id="pc-1">
        <div class="p-name"><span style="width:11px;height:11px;border-radius:50%;background:#EF4444;display:inline-block;flex-shrink:0;"></span>🤖 AI</div>
        <div class="p-sq" id="psq-1">Square: Start</div>
        <div class="p-status" id="pst-1" style="color:var(--muted);">Waiting...</div>
      </div>

      <div class="dice-wrap">
        <h4 id="dice-label">Your turn!</h4>
        <canvas id="gameDice" width="68" height="68" onclick="playerRoll()"></canvas>
        <button id="roll-game-btn" onclick="playerRoll()">🎲 Roll Dice</button>
      </div>

      <div class="game-log">
        <h4>Game Log</h4>
        <div id="game-log-entries"></div>
      </div>
    </div>
  </div>

  <!-- Winner banner -->
  <div id="game-winner-banner">
    <canvas id="gw-confetti" style="position:absolute;inset:0;width:100%;height:100%;pointer-events:none;"></canvas>
    <div style="position:relative;z-index:2;text-align:center;">
      <div id="gw-emoji" style="font-size:5rem;margin-bottom:12px;"></div>
      <h1 id="gw-title" style="font-family:'Sora',sans-serif;font-weight:800;font-size:2.2rem;color:white;margin-bottom:10px;"></h1>
      <p id="gw-sub" style="color:var(--teal-light);font-size:1rem;margin-bottom:28px;"></p>
      <div style="display:flex;gap:12px;justify-content:center;flex-wrap:wrap;">
        <button onclick="startGame()" style="background:var(--amber);color:var(--ink);font-family:'Sora',sans-serif;font-weight:800;font-size:1rem;padding:13px 26px;border-radius:13px;border:none;cursor:pointer;">🔄 Play Again</button>
        <button onclick="showPage('home')" style="background:rgba(255,255,255,0.15);color:white;font-family:'Sora',sans-serif;font-weight:700;font-size:1rem;padding:13px 26px;border-radius:13px;border:2px solid rgba(255,255,255,0.4);cursor:pointer;">🏠 Home</button>
      </div>
    </div>
  </div>
</div>

<script>

  // ── SLIDESHOW ──
  const SNAKE_HEADS = {17:7, 54:34, 62:19, 87:24, 99:78};
  const LADDER_BASES = {4:14, 9:31, 28:84, 40:59, 51:67};
  const COLS = 10, ROWS = 10;

  // Convert square number (1-100) to {row,col} on a 10x10 board
  function squareToRC(n) {
    const row = Math.floor((n - 1) / 10); // 0=bottom row
    const col = (row % 2 === 0) ? (n - 1) % 10 : 9 - (n - 1) % 10;
    return { row: ROWS - 1 - row, col };
  }

  const CELL = 28, PAD = 6;
  const BW = COLS * CELL + (COLS - 1) * 2 + PAD * 2;

  function cellCenter(sq) {
    const { row, col } = squareToRC(sq);
    return {
      x: PAD + col * (CELL + 2) + CELL / 2,
      y: PAD + row * (CELL + 2) + CELL / 2
    };
  }

  const steps = [
    {
      title: 'Set up the board',
      desc: 'Place the board flat on a table. Each player picks a token — a coin or any small object. All tokens start off the board, before square 1.',
      caption: 'The board — 100 squares, numbered 1 to 100',
      draw(ctx, t) {
        drawBoard(ctx, [], []);
        // Draw 3 tokens clustered on square 1
        const colors = ['#F59E0B','#EF4444','#3B82F6'];
        const c = cellCenter(1);
        const offsets = [[-7,0],[7,0],[0,-8]];
        for (let i = 0; i < 3; i++) {
          drawToken(ctx, c.x + offsets[i][0], c.y + offsets[i][1], colors[i], 8);
        }
      }
    },
    {
      title: 'Decide who goes first',
      desc: 'Everyone rolls the die once. The player with the highest roll goes first — then 2nd, 3rd, and 4th in descending order.',
      caption: 'Click "Roll!" to see who goes first',
      draw(ctx, t) {
        // Just draw the board with all pawns on sq 1 as backdrop
        drawBoard(ctx, [], []);
        const colors = ['#F59E0B','#EF4444','#3B82F6','#22C55E'];
        const c = cellCenter(1);
        const off = [[-8,4],[8,4],[0,-8],[0,8]];
        for(let i=0;i<4;i++) drawToken(ctx, c.x+off[i][0], c.y+off[i][1], colors[i], 7);
      }
    },
    {
      title: 'Roll & move',
      desc: 'On your turn, roll the die and move your token forward that many squares. Squares are numbered 1 through 100.',
      caption: 'Token moving forward square by square',
      draw(ctx, t) {
        drawBoard(ctx, [], []);
        // cycle: 2s moving, 0.8s pause at 6, then snap back to 1
        const cycle = t % 2.8;
        let sq, face;
        if (cycle < 2) {
          // moving forward
          const prog = cycle / 2;
          sq = 1 + Math.floor(prog * 5);
          face = Math.floor(prog * 5) + 1;
        } else {
          // pause at 6 then snap
          sq = 6; face = 6;
        }
        const c = cellCenter(sq);
        drawToken(ctx, c.x, c.y, '#F59E0B', 11);
        drawDice(ctx, BW - 36, BW - 36, 28, Math.min(face, 6));
      }
    },
    {
      title: 'Climb a ladder 🪜',
      desc: 'If your token lands at the bottom of a ladder, zoom all the way up to the square at the top. A lucky shortcut!',
      caption: 'Landing on square 4 — climbing up to 14!',
      draw(ctx, t) {
        drawBoard(ctx, [], [4]);
        const prog = (Math.sin(t * 1.8) * 0.5 + 0.5);
        const from = cellCenter(4), to = cellCenter(14);
        const x = from.x + (to.x - from.x) * prog;
        const y = from.y + (to.y - from.y) * prog - Math.sin(prog * Math.PI) * 20;
        drawToken(ctx, x, y, '#F59E0B', 11);
        // Glow on ladder squares
        glowSquare(ctx, 4, '#22C55E', 0.3 + 0.2 * Math.sin(t * 3));
        glowSquare(ctx, 14, '#22C55E', 0.3 + 0.2 * Math.sin(t * 3 + 1));
      }
    },
    {
      title: 'Slide down a snake 🐍',
      desc: 'If your token lands on a snake\'s head, slide all the way down to its tail. Bad luck — but keep going!',
      caption: 'Landing on square 17 — sliding down to 7!',
      draw(ctx, t) {
        drawBoard(ctx, [17], []);
        const prog = (Math.sin(t * 1.8) * 0.5 + 0.5);
        const from = cellCenter(17), to = cellCenter(7);
        const x = from.x + (to.x - from.x) * prog;
        const y = from.y + (to.y - from.y) * prog + Math.sin(prog * Math.PI) * 18;
        drawToken(ctx, x, y, '#EF4444', 11);
        glowSquare(ctx, 17, '#EF4444', 0.3 + 0.2 * Math.sin(t * 3));
        glowSquare(ctx, 7, '#EF4444', 0.3 + 0.2 * Math.sin(t * 3 + 1));
      }
    },
    {
      title: 'Reach 100 to win! 🏆',
      desc: 'The first player to land exactly on square 100 wins the game. Roll too high? Bounce back from 100 by the extra squares.',
      caption: 'Token reaching the winning square!',
      draw(ctx, t) {
        drawBoard(ctx, [], []);
        const bounce = Math.abs(Math.sin(t * 3)) * 8;
        const c = cellCenter(100);
        glowSquare(ctx, 100, '#F59E0B', 0.4 + 0.3 * Math.sin(t * 4));
        drawToken(ctx, c.x, c.y - bounce, '#F59E0B', 13);
        for (let i = 0; i < 5; i++) {
          const angle = (t * 2 + i * 1.26) % (Math.PI * 2);
          const r = 18 + Math.sin(t * 3 + i) * 4;
          ctx.save();
          ctx.globalAlpha = 0.7 + 0.3 * Math.sin(t * 4 + i);
          ctx.fillStyle = '#F59E0B';
          ctx.font = '10px serif';
          ctx.fillText('★', c.x + Math.cos(angle) * r - 5, c.y + Math.sin(angle) * r + 4);
          ctx.restore();
        }
      }
    },
    {
      title: 'The rules 📋',
      desc: 'Quick reminder: land exactly on 100 to win (overshoot = bounce back). Snakes only bite on the head. Ladders only help from the foot. Multiple players can share a square. One die, standard play.',
      caption: 'Key rules at a glance',
      draw(ctx, t) {
        drawBoard(ctx, [], []);
        // Pulse all snake heads and ladder bases to highlight them
        Object.keys(SNAKE_HEADS).forEach((h, i) => {
          glowSquare(ctx, +h, '#EF4444', 0.25 + 0.15 * Math.sin(t * 2 + i));
        });
        Object.keys(LADDER_BASES).forEach((b, i) => {
          glowSquare(ctx, +b, '#22C55E', 0.25 + 0.15 * Math.sin(t * 2 + i + 1));
        });
        glowSquare(ctx, 100, '#F59E0B', 0.35 + 0.2 * Math.sin(t * 3));
      }
    }
  ];

  function drawBoard(ctx, highlightSnakes, highlightLadders) {
    ctx.clearRect(0, 0, BW, BW);
    ctx.fillStyle = '#F0FDF9';
    ctx.fillRect(0, 0, BW, BW);

    // Draw cells
    for (let sq = 1; sq <= 100; sq++) {
      const { row, col } = squareToRC(sq);
      const x = PAD + col * (CELL + 2);
      const y = PAD + row * (CELL + 2);
      let bg = (row + col) % 2 === 0 ? '#CCFBF1' : '#E0FAF5';
      if (sq === 100) bg = '#FEF3C7';
      ctx.fillStyle = bg;
      roundRect(ctx, x, y, CELL, CELL, 3);
      ctx.fill();
      ctx.fillStyle = '#4B6B68';
      ctx.font = `bold ${sq >= 10 ? 5.5 : 6.5}px sans-serif`;
      ctx.textAlign = 'center';
      ctx.textBaseline = 'top';
      ctx.fillText(sq, x + CELL / 2, y + 2);
    }

    // ── LADDERS ──
    const ladderColors = ['#B45309','#0D9488','#2563EB','#7C3AED','#16A34A'];
    Object.entries(LADDER_BASES).forEach(([base, top], i) => {
      const from = cellCenter(+base), to = cellCenter(+top);
      const color = ladderColors[i % ladderColors.length];
      const dx = to.x - from.x, dy = to.y - from.y;
      const len = Math.sqrt(dx * dx + dy * dy);
      // perpendicular offset for the two rails
      const px = (-dy / len) * 4, py = (dx / len) * 4;

      ctx.save();
      ctx.globalAlpha = 0.92;
      ctx.lineCap = 'round';

      // Left rail
      ctx.beginPath();
      ctx.moveTo(from.x - px, from.y - py);
      ctx.lineTo(to.x - px, to.y - py);
      ctx.strokeStyle = color;
      ctx.lineWidth = 2.2;
      ctx.stroke();

      // Right rail
      ctx.beginPath();
      ctx.moveTo(from.x + px, from.y + py);
      ctx.lineTo(to.x + px, to.y + py);
      ctx.strokeStyle = color;
      ctx.lineWidth = 2.2;
      ctx.stroke();

      // Rungs — short, perpendicular, evenly spaced
      const numRungs = Math.max(3, Math.floor(len / 14));
      for (let r = 1; r < numRungs; r++) {
        const t = r / numRungs;
        const rx = from.x + dx * t;
        const ry = from.y + dy * t;
        ctx.beginPath();
        ctx.moveTo(rx - px * 1.1, ry - py * 1.1);
        ctx.lineTo(rx + px * 1.1, ry + py * 1.1);
        ctx.strokeStyle = color;
        ctx.lineWidth = 1.6;
        ctx.stroke();
      }

      ctx.restore();
    });

    // ── SNAKES ──
    const snakeColors = [
      {body:'#DC2626', belly:'#FCA5A5', scale:'#B91C1C'},
      {body:'#16A34A', belly:'#86EFAC', scale:'#15803D'},
      {body:'#7C3AED', belly:'#C4B5FD', scale:'#6D28D9'},
      {body:'#0891B2', belly:'#67E8F9', scale:'#0E7490'},
      {body:'#D97706', belly:'#FDE68A', scale:'#B45309'},
    ];
    Object.entries(SNAKE_HEADS).forEach(([head, tail], i) => {
      const from = cellCenter(+head), to = cellCenter(+tail);
      const sc = snakeColors[i % snakeColors.length];
      const dx = to.x - from.x, dy = to.y - from.y;
      const len = Math.sqrt(dx * dx + dy * dy);

      // Wavy body using multiple bezier segments
      const mid1x = from.x + dx * 0.33 - dy * 0.45;
      const mid1y = from.y + dy * 0.33 + dx * 0.45;
      const mid2x = from.x + dx * 0.66 + dy * 0.45;
      const mid2y = from.y + dy * 0.66 - dx * 0.45;

      ctx.save();
      ctx.globalAlpha = 0.95;
      ctx.lineCap = 'round';
      ctx.lineJoin = 'round';

      // Outer body (thick)
      ctx.beginPath();
      ctx.moveTo(from.x, from.y);
      ctx.bezierCurveTo(mid1x, mid1y, mid2x, mid2y, to.x, to.y);
      ctx.strokeStyle = sc.body;
      ctx.lineWidth = 6;
      ctx.stroke();

      // Belly stripe (thinner, lighter)
      ctx.beginPath();
      ctx.moveTo(from.x, from.y);
      ctx.bezierCurveTo(mid1x, mid1y, mid2x, mid2y, to.x, to.y);
      ctx.strokeStyle = sc.belly;
      ctx.lineWidth = 2.5;
      ctx.stroke();

      // ── Snake HEAD ──
      // Direction: from head square toward first bezier control point
      const hdx = mid1x - from.x, hdy = mid1y - from.y;
      const hlen = Math.sqrt(hdx * hdx + hdy * hdy) || 1;
      const hax = hdx / hlen, hay = hdy / hlen; // forward
      const hrx = -hay, hry = hax;              // right

      const HR = 5.5; // head radius
      // Head = filled oval, wide side toward body, rounded snout forward
      ctx.save();
      ctx.translate(from.x, from.y);
      ctx.rotate(Math.atan2(hay, hax));
      ctx.beginPath();
      ctx.ellipse(HR * 0.4, 0, HR * 1.3, HR * 0.85, 0, 0, Math.PI * 2);
      ctx.fillStyle = sc.body;
      ctx.fill();
      ctx.strokeStyle = sc.scale;
      ctx.lineWidth = 0.8;
      ctx.stroke();

      // Scales hint — two small arcs on top of head
      ctx.beginPath();
      ctx.arc(HR * 0.2, -HR * 0.3, HR * 0.45, Math.PI, 0);
      ctx.strokeStyle = sc.scale;
      ctx.lineWidth = 0.7;
      ctx.stroke();

      // Eye
      ctx.beginPath();
      ctx.arc(HR * 0.8, -HR * 0.45, 1.8, 0, Math.PI * 2);
      ctx.fillStyle = 'white';
      ctx.fill();
      ctx.beginPath();
      ctx.arc(HR * 0.9, -HR * 0.45, 0.9, 0, Math.PI * 2);
      ctx.fillStyle = '#111';
      ctx.fill();

      // Nostril dot
      ctx.beginPath();
      ctx.arc(HR * 1.2, -HR * 0.2, 0.8, 0, Math.PI * 2);
      ctx.fillStyle = sc.scale;
      ctx.fill();

      // Forked tongue
      ctx.beginPath();
      ctx.moveTo(HR * 1.55, 0);
      ctx.lineTo(HR * 2.1, 0);
      ctx.strokeStyle = '#EF4444';
      ctx.lineWidth = 1;
      ctx.lineCap = 'round';
      ctx.stroke();
      ctx.beginPath();
      ctx.moveTo(HR * 2.1, 0);
      ctx.lineTo(HR * 2.6, -HR * 0.45);
      ctx.moveTo(HR * 2.1, 0);
      ctx.lineTo(HR * 2.6, HR * 0.45);
      ctx.lineWidth = 0.8;
      ctx.stroke();

      ctx.restore();

      // Tail tip (pointy)
      ctx.beginPath();
      ctx.arc(to.x, to.y, 2, 0, Math.PI * 2);
      ctx.fillStyle = sc.body;
      ctx.fill();

      ctx.restore();
    });
  }

  function glowSquare(ctx, sq, color, alpha) {
    const { row, col } = squareToRC(sq);
    const x = PAD + col * (CELL + 2);
    const y = PAD + row * (CELL + 2);
    ctx.save();
    ctx.globalAlpha = alpha;
    ctx.fillStyle = color;
    roundRect(ctx, x, y, CELL, CELL, 3);
    ctx.fill();
    ctx.restore();
  }

  function drawToken(ctx, x, y, color, r) {
    ctx.save();
    // Shadow
    ctx.shadowColor = 'rgba(0,0,0,0.25)';
    ctx.shadowBlur = 6;
    ctx.shadowOffsetY = 2;
    ctx.beginPath();
    ctx.arc(x, y, r, 0, Math.PI * 2);
    ctx.fillStyle = color;
    ctx.fill();
    ctx.shadowBlur = 0;
    // Shine
    ctx.beginPath();
    ctx.arc(x - r * 0.3, y - r * 0.3, r * 0.35, 0, Math.PI * 2);
    ctx.fillStyle = 'rgba(255,255,255,0.4)';
    ctx.fill();
    ctx.restore();
  }

  function drawDice(ctx, x, y, size, face) {
    const h = size / 2;
    ctx.save();
    ctx.shadowColor = 'rgba(0,0,0,0.2)';
    ctx.shadowBlur = 8;
    ctx.fillStyle = 'white';
    roundRect(ctx, x - h, y - h, size, size, size * 0.15);
    ctx.fill();
    ctx.shadowBlur = 0;
    ctx.strokeStyle = '#D1FAF4';
    ctx.lineWidth = 1.5;
    ctx.stroke();
    // Dots
    const dots = {
      1: [[0,0]],
      2: [[-1,-1],[1,1]],
      3: [[-1,-1],[0,0],[1,1]],
      4: [[-1,-1],[1,-1],[-1,1],[1,1]],
      5: [[-1,-1],[1,-1],[0,0],[-1,1],[1,1]],
      6: [[-1,-1],[1,-1],[-1,0],[1,0],[-1,1],[1,1]]
    };
    const dr = size * 0.1, sp = size * 0.28;
    ctx.fillStyle = '#0D9488';
    (dots[face] || []).forEach(([dx, dy]) => {
      ctx.beginPath();
      ctx.arc(x + dx * sp, y + dy * sp, dr, 0, Math.PI * 2);
      ctx.fill();
    });
    ctx.restore();
  }

  function roundRect(ctx, x, y, w, h, r) {
    ctx.beginPath();
    ctx.moveTo(x + r, y);
    ctx.lineTo(x + w - r, y);
    ctx.quadraticCurveTo(x + w, y, x + w, y + r);
    ctx.lineTo(x + w, y + h - r);
    ctx.quadraticCurveTo(x + w, y + h, x + w - r, y + h);
    ctx.lineTo(x + r, y + h);
    ctx.quadraticCurveTo(x, y + h, x, y + h - r);
    ctx.lineTo(x, y + r);
    ctx.quadraticCurveTo(x, y, x + r, y);
    ctx.closePath();
  }

  let currentStep = 0, animFrame, startTime = null;
  let unoAnimFrame, unoStartTime = null, unoCurrentStep = 0;

  function renderStep(ts) {
    if (!startTime) startTime = ts;
    const t = (ts - startTime) / 1000;
    const canvas = document.getElementById('stepCanvas');
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    canvas.width = BW; canvas.height = BW;
    steps[currentStep].draw(ctx, t);
    animFrame = requestAnimationFrame(renderStep);
  }

  // ── ROLL-OFF ──
  const PLAYERS = [
    {name:'Player 1', color:'#F59E0B'},
    {name:'Player 2', color:'#EF4444'},
    {name:'Player 3', color:'#3B82F6'},
    {name:'Player 4', color:'#22C55E'},
  ];
  let rollResults = [];

  function resetRollOff() {
    rollResults = [];
    document.getElementById('roll-results').innerHTML = '';
    document.getElementById('rolloff-reset').style.display = 'none';
    setTimeout(runAutoRoll, 600);
  }

  function runAutoRoll() {
    rollResults = [];
    document.getElementById('roll-results').innerHTML = '';
    PLAYERS.forEach((p, i) => {
      setTimeout(() => {
        const roll = Math.floor(Math.random() * 6) + 1;
        rollResults.push({...p, roll});

        const container = document.getElementById('roll-results');
        const row = document.createElement('div');
        row.style.cssText = `display:flex;align-items:center;gap:10px;padding:8px 12px;background:white;border:1.5px solid var(--border);border-radius:10px;animation:slideIn 0.3s ease;`;
        row.innerHTML = `
          <div style="width:10px;height:10px;border-radius:50%;background:${p.color};flex-shrink:0;"></div>
          <span style="font-family:'Sora',sans-serif;font-weight:600;font-size:0.85rem;flex:1;">${p.name}</span>
          <span style="font-size:1rem;">🎲</span>
          <span style="font-family:'Sora',sans-serif;font-weight:800;font-size:1.1rem;color:${p.color};">${roll}</span>
        `;
        container.appendChild(row);

        // After last player, show ranking
        if (i === PLAYERS.length - 1) {
          setTimeout(() => {
            const sorted = [...rollResults].sort((a,b) => b.roll - a.roll);
            const order = sorted.map(p => `<span style="color:${p.color};font-weight:700;">${p.name}</span>`).join(' → ');
            const winner = document.createElement('div');
            winner.style.cssText = `margin-top:6px;padding:10px 14px;background:var(--amber-light);border:2px solid var(--amber);border-radius:12px;animation:slideIn 0.35s ease;`;
            winner.innerHTML = `
              <div style="font-family:'Sora',sans-serif;font-size:0.78rem;color:var(--amber-dark);font-weight:700;margin-bottom:4px;">ORDER OF PLAY</div>
              <div style="font-size:0.82rem;line-height:1.6;">${order}</div>
              <div style="font-size:0.78rem;color:var(--muted);margin-top:4px;font-style:italic;">${sorted[0].name} rolled ${sorted[0].roll} — goes first!</div>
            `;
            container.appendChild(winner);
            document.getElementById('rolloff-reset').style.display = '';
          }, 500);
        }
      }, i * 700);
    });
  }

  function goStep(i) {
    cancelAnimationFrame(animFrame);
    startTime = null;
    currentStep = i;
    for (let d = 0; d < 7; d++) {
      const el = document.getElementById('dot-' + d);
      if (!el) continue;
      el.style.background = d === i ? 'var(--teal)' : '';
      el.style.color = d === i ? 'white' : 'var(--muted)';
    }
    const isRollStep = i === 1;
    document.getElementById('slide-num').textContent = '0' + (i + 1);
    document.getElementById('slide-title').textContent = steps[i].title;
    document.getElementById('slide-desc').textContent = steps[i].desc;
    document.getElementById('canvas-caption').textContent = isRollStep ? '' : steps[i].caption;
    document.getElementById('slide-counter').textContent = (i + 1) + ' / ' + steps.length;
    document.getElementById('btn-prev').style.opacity = i === 0 ? '0.35' : '1';
    document.getElementById('btn-next').textContent = i === steps.length - 1 ? '🏆 Done!' : 'Next →';
    document.getElementById('btn-next').style.background = i === steps.length - 1 ? 'var(--amber)' : 'var(--teal)';
    document.getElementById('btn-next').style.color = i === steps.length - 1 ? 'var(--ink)' : 'white';
    document.getElementById('btn-next').onmouseenter = i === steps.length - 1 ? startDoneHover : null;
    document.getElementById('btn-next').onmouseleave = i === steps.length - 1 ? stopDoneHover : null;

    // Toggle roll-off panel
    document.getElementById('slide-text-panel').style.display = isRollStep ? 'none' : '';
    document.getElementById('rolloff-panel').style.display = isRollStep ? 'flex' : 'none';
    if (isRollStep) { resetRollOff(); }

    animFrame = requestAnimationFrame(renderStep);
  }

  function nextStep() {
    if (currentStep < steps.length - 1) {
      goStep(currentStep + 1);
    } else {
      showCelebration('Snake & Ladders');
    }
  }

  // ── DONE BUTTON HOVER ANIMATION ──
  let doneHoverFrame, doneHoverCanvas;
  function startDoneHover() {
    const btn = document.getElementById('btn-next');
    if (!btn) return;
    btn.style.transform = 'scale(1.08)';
    btn.style.boxShadow = '0 0 0 4px rgba(245,158,11,0.4)';
    // spawn tiny emoji burst above
    let el = document.getElementById('done-hover-burst');
    if (!el) {
      el = document.createElement('div');
      el.id = 'done-hover-burst';
      el.style.cssText = 'position:absolute;pointer-events:none;z-index:999;font-size:1.2rem;';
      document.body.appendChild(el);
    }
    const rect = btn.getBoundingClientRect();
    const emojis = ['🏆','⭐','🎉','✨','🎊'];
    el.innerHTML = '';
    emojis.forEach((e, i) => {
      const span = document.createElement('span');
      span.textContent = e;
      span.style.cssText = `position:fixed;left:${rect.left + rect.width/2 + (i-2)*24}px;top:${rect.top - 10}px;opacity:0;transition:all 0.4s cubic-bezier(0.34,1.56,0.64,1);transform:translateY(0px) rotate(0deg);display:inline-block;`;
      el.appendChild(span);
      setTimeout(() => {
        span.style.opacity = '1';
        span.style.transform = `translateY(-${28 + i*6}px) rotate(${(i-2)*15}deg)`;
      }, i * 60);
    });
  }
  function stopDoneHover() {
    const btn = document.getElementById('btn-next');
    if (btn) { btn.style.transform = ''; btn.style.boxShadow = ''; }
    const el = document.getElementById('done-hover-burst');
    if (el) el.innerHTML = '';
  }

  // ── CELEBRATION ──
  const GAME_DATA = {
    'Snake & Ladders': { emoji: '🐍🪜', title: "You learned Snake & Ladders!", sub: "You now know how to set up the board, roll to decide who goes first, move your token, climb ladders, dodge snakes, and race to square 100. Time to play!" }
  };

  const completedGames = new Set();

  function updateGameCard(gameName) {
    if (gameName === 'Snake & Ladders') {
      const badge = document.getElementById('sl-card-badge');
      const btn = document.getElementById('sl-card-btn');
      if (badge) { badge.textContent = '✅ Completed'; badge.style.background = '#DCFCE7'; badge.style.color = '#15803D'; }
      if (btn) { btn.textContent = '↺ Learn again'; btn.style.background = '#0A7970'; }
    }
  }

  function showCelebration(gameName) {
    completedGames.add(gameName);
    updateGameCard(gameName);
    const data = GAME_DATA[gameName] || { emoji:'🎉', title:'You did it!', sub:'You finished the tutorial!' };
    document.getElementById('celebrate-emoji').textContent = data.emoji;
    document.getElementById('celebrate-title').textContent = data.title;
    document.getElementById('celebrate-sub').textContent = data.sub;
    const overlay = document.getElementById('celebrate-overlay');
    overlay.style.display = 'flex';
    startConfetti();
  }

  function closeCelebrate() {
    document.getElementById('celebrate-overlay').style.display = 'none';
    stopConfetti();
    showPage('home');
  }

  // ── CONFETTI ──
  let confettiAnim, confettiParticles = [];
  function startConfetti() {
    const canvas = document.getElementById('confetti-canvas');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
    confettiParticles = Array.from({length: 120}, () => ({
      x: Math.random() * canvas.width,
      y: Math.random() * -canvas.height,
      r: 5 + Math.random() * 7,
      color: ['#F59E0B','#0D9488','#EF4444','#3B82F6','#22C55E','#CCFBF1','#FEF3C7'][Math.floor(Math.random()*7)],
      speed: 2 + Math.random() * 4,
      drift: (Math.random() - 0.5) * 2,
      spin: (Math.random() - 0.5) * 0.15,
      angle: Math.random() * Math.PI * 2,
      shape: Math.random() > 0.5 ? 'rect' : 'circle'
    }));
    function draw() {
      const ctx = canvas.getContext('2d');
      ctx.clearRect(0, 0, canvas.width, canvas.height);
      confettiParticles.forEach(p => {
        p.y += p.speed;
        p.x += p.drift;
        p.angle += p.spin;
        if (p.y > canvas.height) { p.y = -10; p.x = Math.random() * canvas.width; }
        ctx.save();
        ctx.translate(p.x, p.y);
        ctx.rotate(p.angle);
        ctx.fillStyle = p.color;
        ctx.globalAlpha = 0.85;
        if (p.shape === 'rect') {
          ctx.fillRect(-p.r/2, -p.r*0.4, p.r, p.r*0.5);
        } else {
          ctx.beginPath();
          ctx.arc(0, 0, p.r/2, 0, Math.PI*2);
          ctx.fill();
        }
        ctx.restore();
      });
      confettiAnim = requestAnimationFrame(draw);
    }
    draw();
  }
  function stopConfetti() {
    cancelAnimationFrame(confettiAnim);
    confettiParticles = [];
    const canvas = document.getElementById('confetti-canvas');
    if (canvas) canvas.getContext('2d').clearRect(0,0,canvas.width,canvas.height);
  }
  function prevStep() { if (currentStep > 0) goStep(currentStep - 1); }

  // Init slideshow when snake-ladders page is shown
  const _origShowPage = null;

  function showPage(id) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById('page-' + id).classList.add('active');
    const isHome = id === 'home';
    document.getElementById('nav-home-links').style.display = isHome ? '' : 'none';
    const backBtn = document.getElementById('nav-back-btn');
    backBtn.style.display = isHome ? 'none' : 'flex';
    backBtn.onclick = id === 'sl-game' ? () => showPage('home') : () => showPage('home');
    window.scrollTo({ top: 0, behavior: 'smooth' });
    if (id === 'snake-ladders') {
      cancelAnimationFrame(animFrame);
      startTime = null;
      setTimeout(() => goStep(0), 80);
    } else if (id === 'sl-game') {
      cancelAnimationFrame(animFrame);
      setTimeout(() => startGame(), 80);
    } else if (id === 'uno-standard') {
      cancelAnimationFrame(animFrame);
      cancelAnimationFrame(unoAnimFrame);
      unoStartTime = null;
      setTimeout(() => unoStep(0), 80);
    } else {
      cancelAnimationFrame(animFrame);
      cancelAnimationFrame(unoAnimFrame);
    }
  }

  // ══ UNO STANDARD SLIDESHOW ══
  const UNO_COLORS = {red:'#EF4444', blue:'#3B82F6', green:'#22C55E', yellow:'#F59E0B', black:'#1C2B2A'};

  function drawUnoCard(ctx, x, y, w, h, color, label, angle=0, alpha=1){
    ctx.save();
    ctx.globalAlpha = alpha;
    ctx.translate(x, y);
    ctx.rotate(angle);
    // Shadow
    ctx.shadowColor = 'rgba(0,0,0,0.22)';
    ctx.shadowBlur = 8; ctx.shadowOffsetY = 3;
    // Card body
    ctx.fillStyle = UNO_COLORS[color] || color;
    unoRoundRect(ctx, -w/2, -h/2, w, h, 8);
    ctx.fill();
    ctx.shadowBlur = 0;
    // White border
    ctx.strokeStyle = 'rgba(255,255,255,0.9)';
    ctx.lineWidth = 2.5;
    ctx.stroke();
    // Oval on card
    ctx.fillStyle = 'rgba(255,255,255,0.15)';
    ctx.beginPath();
    ctx.ellipse(0, 0, w*0.35, h*0.45, Math.PI/4, 0, Math.PI*2);
    ctx.fill();
    // Label
    ctx.fillStyle = 'white';
    ctx.font = `bold ${label.length > 2 ? 13 : 18}px Sora, sans-serif`;
    ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
    ctx.fillText(label, 0, 0);
    // Corner labels
    ctx.font = 'bold 8px Sora, sans-serif';
    ctx.fillText(label, -w/2+7, -h/2+8);
    ctx.restore();
  }

  function unoRoundRect(ctx, x, y, w, h, r){
    ctx.beginPath();
    ctx.moveTo(x+r,y); ctx.lineTo(x+w-r,y); ctx.quadraticCurveTo(x+w,y,x+w,y+r);
    ctx.lineTo(x+w,y+h-r); ctx.quadraticCurveTo(x+w,y+h,x+w-r,y+h);
    ctx.lineTo(x+r,y+h); ctx.quadraticCurveTo(x,y+h,x,y+h-r);
    ctx.lineTo(x,y+r); ctx.quadraticCurveTo(x,y,x+r,y);
    ctx.closePath();
  }

  function drawCardBack(ctx, x, y, w, h, angle=0, alpha=1){
    ctx.save();
    ctx.globalAlpha = alpha;
    ctx.translate(x, y); ctx.rotate(angle);
    ctx.shadowColor = 'rgba(0,0,0,0.2)'; ctx.shadowBlur = 6; ctx.shadowOffsetY = 2;
    ctx.fillStyle = '#DC2626';
    unoRoundRect(ctx, -w/2, -h/2, w, h, 8); ctx.fill();
    ctx.shadowBlur = 0;
    ctx.strokeStyle = 'rgba(255,255,255,0.8)'; ctx.lineWidth = 2; ctx.stroke();
    ctx.fillStyle = 'rgba(0,0,0,0.25)';
    ctx.beginPath(); ctx.ellipse(0,0,w*0.3,h*0.42,Math.PI/4,0,Math.PI*2); ctx.fill();
    ctx.fillStyle = 'white'; ctx.font = 'bold 10px Sora, sans-serif';
    ctx.textAlign = 'center'; ctx.textBaseline = 'middle';
    ctx.fillText('UNO', 0, 0);
    ctx.restore();
  }

  const unoSteps = [
    {
      title: 'Deal the cards',
      desc: 'Shuffle the 108-card deck. Deal 7 cards face-down to each player. Place the remaining cards as the draw pile. Flip the top card to start the discard pile — if it\'s a Wild Draw Four, shuffle it back and flip again.',
      caption: '7 cards dealt to each player',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        // Draw pile
        for(let i=4;i>=0;i--) drawCardBack(ctx, 60, H/2, 52, 74, 0, 0.6+i*0.08);
        // Cards flying to player one by one
        const cardData = [{c:'red',l:'7'},{c:'blue',l:'⊘'},{c:'green',l:'+2'},{c:'yellow',l:'3'},{c:'red',l:'1'},{c:'blue',l:'5'},{c:'green',l:'🌈'}];
        const count = Math.min(7, Math.floor(t * 1.4));
        for(let i=0;i<count;i++){
          const prog = Math.min(1, (t*1.4 - i));
          const ease = 1 - Math.pow(1-prog,3);
          const sx=60, sy=H/2, ex=170+i*10, ey=200;
          const x = sx+(ex-sx)*ease, y = sy+(ey-sy)*ease - Math.sin(prog*Math.PI)*30;
          drawCardBack(ctx, x, y, 44, 62, (i-3)*0.15*ease);
        }
        // Player hand label
        ctx.fillStyle='var(--muted)'; ctx.font='bold 9px sans-serif';
        ctx.textAlign='center'; ctx.fillText('Your hand', 210, 235);
        // Discard pile top
        const flip = Math.min(1, Math.max(0, t*1.4-6));
        if(flip>0) drawUnoCard(ctx, 130, H/2-10, 52, 74, 'red', '5', 0.05, flip);
        ctx.fillStyle='#4B6B68'; ctx.font='bold 9px sans-serif';
        ctx.textAlign='center'; ctx.fillText('Discard pile', 130, H/2+50);
      }
    },
    {
      title: 'Match to play a card',
      desc: 'On your turn, play one card matching the top of the discard pile by COLOR or NUMBER. Can\'t play? Draw one card — if it matches, you may play it immediately.',
      caption: 'Match by color OR number',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        // Discard pile — red 7
        drawUnoCard(ctx, W/2, 90, 58, 82, 'red', '7', 0);
        ctx.fillStyle='#4B6B68'; ctx.font='bold 9px sans-serif';
        ctx.textAlign='center'; ctx.fillText('Discard pile', W/2, 140);
        // Player hand options
        const hand = [{c:'red',l:'3',ok:true},{c:'blue',l:'7',ok:true},{c:'green',l:'5',ok:false},{c:'yellow',l:'2',ok:false}];
        hand.forEach((card,i)=>{
          const x = 50 + i*55, y = 210;
          const hover = card.ok ? Math.sin(t*2+i)*5 : 0;
          drawUnoCard(ctx, x, y+hover, 44, 62, card.c, card.l, 0);
          if(card.ok){
            ctx.fillStyle='#22C55E'; ctx.font='bold 11px sans-serif';
            ctx.textAlign='center'; ctx.fillText('✓', x, y+hover-38);
          } else {
            ctx.fillStyle='#EF4444'; ctx.font='bold 11px sans-serif';
            ctx.textAlign='center'; ctx.fillText('✗', x, y+hover-38);
          }
        });
        // Animated arrow from valid card to pile
        const prog = (Math.sin(t*2)*0.5+0.5);
        const srcX=50, srcY=185, dstX=W/2, dstY=115;
        ctx.save(); ctx.globalAlpha=0.6*prog;
        ctx.strokeStyle='#22C55E'; ctx.lineWidth=2; ctx.setLineDash([4,3]);
        ctx.beginPath(); ctx.moveTo(srcX,srcY); ctx.lineTo(dstX,dstY); ctx.stroke();
        ctx.restore();
      }
    },
    {
      title: 'Action cards',
      desc: 'Skip makes the next player lose their turn. Reverse flips the direction of play. Draw Two forces the next player to draw 2 cards and skip their turn.',
      caption: 'Three action card types',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        const cards = [{c:'red',l:'⊘',label:'Skip',y:0},{c:'green',l:'↩',label:'Reverse',y:0},{c:'blue',l:'+2',label:'Draw Two',y:0}];
        cards.forEach((card,i)=>{
          const x = 55+i*95, y = 115+Math.sin(t*1.5+i*1.1)*8;
          drawUnoCard(ctx, x, y, 58, 82, card.c, card.l, Math.sin(t*0.8+i)*0.06);
          ctx.fillStyle='#4B6B68'; ctx.font='bold 9px sans-serif';
          ctx.textAlign='center'; ctx.fillText(card.label, x, y+54);
        });
        // Effect arrow for skip
        const skipAlpha = 0.4+0.4*Math.abs(Math.sin(t*2));
        ctx.save(); ctx.globalAlpha=skipAlpha;
        ctx.strokeStyle='#EF4444'; ctx.lineWidth=2;
        ctx.beginPath(); ctx.arc(55, 60, 16, 0, Math.PI*1.6); ctx.stroke();
        ctx.fillStyle='#EF4444'; ctx.font='bold 14px sans-serif';
        ctx.textAlign='center'; ctx.fillText('⊘', 55, 64);
        ctx.restore();
      }
    },
    {
      title: 'Wild cards',
      desc: 'A Wild card can be played on any color — you choose the next color. Wild Draw Four forces the next player to draw 4 cards. Only legal if you have no matching color card.',
      caption: 'Play wild cards on any color',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        // Wild card spinning color segments
        const cx=W/2, cy=95, r=32;
        const segs=['#EF4444','#3B82F6','#22C55E','#F59E0B'];
        segs.forEach((c,i)=>{
          ctx.beginPath();
          ctx.moveTo(cx,cy);
          ctx.arc(cx,cy,r,i*Math.PI/2+t*0.5,(i+1)*Math.PI/2+t*0.5);
          ctx.fillStyle=c; ctx.fill();
        });
        ctx.beginPath(); ctx.arc(cx,cy,r,0,Math.PI*2);
        ctx.strokeStyle='white'; ctx.lineWidth=3; ctx.stroke();
        ctx.fillStyle='white'; ctx.font='bold 14px Sora, sans-serif';
        ctx.textAlign='center'; ctx.textBaseline='middle'; ctx.fillText('W',cx,cy);
        ctx.textBaseline='alphabetic';
        // Wild +4 card
        drawUnoCard(ctx, W/2, 185, 58, 82, 'black', '+4', Math.sin(t)*0.05);
        // Color choice arrows
        const colors2=['#EF4444','#3B82F6','#22C55E','#F59E0B'];
        colors2.forEach((c,i)=>{
          const angle = -Math.PI/2+i*(Math.PI*2/4)+t*0.3;
          const ax=cx+Math.cos(angle)*55, ay=cy+Math.sin(angle)*55;
          ctx.beginPath(); ctx.arc(ax,ay,9,0,Math.PI*2);
          ctx.fillStyle=c; ctx.fill();
          ctx.strokeStyle='white'; ctx.lineWidth=1.5; ctx.stroke();
        });
        ctx.fillStyle='#4B6B68'; ctx.font='bold 9px sans-serif';
        ctx.textAlign='center'; ctx.fillText('Choose any color!', W/2, 30);
      }
    },
    {
      title: 'Say "Uno!"',
      desc: 'When you play a card and are left with only ONE card in your hand, shout "Uno!" immediately. If another player catches you before the next turn, you draw 2 penalty cards.',
      caption: 'Play down to 1 card — shout Uno!',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        // Player hand — 2 cards
        drawUnoCard(ctx, W/2-20, 180, 52, 74, 'red', '3', -0.1);
        drawUnoCard(ctx, W/2+20, 180, 52, 74, 'blue', '7', 0.1);
        // Playing one card toward discard
        const prog = (Math.sin(t*1.5)*0.5+0.5);
        const px=W/2-20+prog*40, py=180-prog*90;
        drawUnoCard(ctx, px, py, 52, 74, 'red', '3', -0.1+prog*0.1);
        // UNO shout bubble
        const scale = 0.8+0.25*Math.abs(Math.sin(t*3));
        ctx.save();
        ctx.translate(W/2, 80); ctx.scale(scale,scale);
        ctx.fillStyle='#DC2626';
        unoRoundRect(ctx,-52,-22,104,44,12); ctx.fill();
        ctx.fillStyle='white'; ctx.font='bold 26px Sora, sans-serif';
        ctx.textAlign='center'; ctx.textBaseline='middle';
        ctx.fillText('UNO!',0,0);
        ctx.restore();
        // Speech bubble tail
        ctx.fillStyle='#DC2626';
        ctx.beginPath(); ctx.moveTo(W/2-8,103); ctx.lineTo(W/2+8,103); ctx.lineTo(W/2,118); ctx.fill();
      }
    },
,
    {
      title: 'Win the round!',
      desc: 'First player to play all their cards wins! Empty your entire hand before anyone else and you take the victory.',
      caption: 'Empty your hand to win!',
      draw(ctx, t) {
        const W=300, H=260;
        ctx.clearRect(0,0,W,H);
        ctx.fillStyle='#F0FDF9'; ctx.fillRect(0,0,W,H);
        const bounce = Math.abs(Math.sin(t*2.5))*10;
        ctx.font=`${52+Math.abs(Math.sin(t*2))*6}px serif`;
        ctx.textAlign='center'; ctx.fillText('🏆',W/2,100-bounce);
        const cardCols=['red','blue','green','yellow'];
        for(let i=0;i<8;i++){
          const angle=(t*1.5+i*0.78)%(Math.PI*2);
          const r=70+Math.sin(t+i)*20;
          const cx2=W/2+Math.cos(angle)*r;
          const cy2=120+Math.sin(angle)*r*0.5;
          drawUnoCard(ctx,cx2,cy2,28,40,cardCols[i%4],String(i+1),(angle+t)*0.5,0.8);
        }
        ctx.fillStyle='#DC2626'; ctx.font='bold 13px Sora, sans-serif';
        ctx.textAlign='center'; ctx.fillText('First to empty their deck wins!',W/2,220);
      }
    }
  ];

  function unoRenderLoop(ts){
    if(!unoStartTime) unoStartTime=ts;
    const t=(ts-unoStartTime)/1000;
    const canvas=document.getElementById('unoCanvas');
    if(!canvas){cancelAnimationFrame(unoAnimFrame);return;}
    const ctx=canvas.getContext('2d');
    canvas.width=300; canvas.height=260;
    unoSteps[unoCurrentStep].draw(ctx,t);
    unoAnimFrame=requestAnimationFrame(unoRenderLoop);
  }

  function unoStep(i){
    if(i<0||i>=unoSteps.length) return;
    cancelAnimationFrame(unoAnimFrame);
    unoStartTime=null;
    unoCurrentStep=i;
    const s=unoSteps[i];
    document.getElementById('uno-slide-num').textContent='0'+(i+1);
    document.getElementById('uno-slide-title').textContent=s.title;
    document.getElementById('uno-slide-desc').textContent=s.desc;
    document.getElementById('uno-canvas-caption').textContent=s.caption;
    document.getElementById('uno-slide-counter').textContent=(i+1)+' / '+unoSteps.length;
    document.getElementById('uno-btn-prev').style.opacity=i===0?'0.35':'1';
    const nextBtn=document.getElementById('uno-btn-next');
    nextBtn.textContent=i===unoSteps.length-1?'🎉 Done!':'Next →';
    nextBtn.style.background=i===unoSteps.length-1?'var(--amber)':'#DC2626';
    nextBtn.style.color=i===unoSteps.length-1?'var(--ink)':'white';
    // Dots
    const dotsEl=document.getElementById('uno-dots');
    dotsEl.innerHTML=unoSteps.map((_,d)=>
      `<div onclick="unoStep(${d})" style="flex:1;padding:13px 8px;text-align:center;cursor:pointer;
        font-family:'Sora',sans-serif;font-weight:700;font-size:0.78rem;
        background:${d===i?'#DC2626':''};color:${d===i?'white':'var(--muted)'};
        transition:background 0.2s,color 0.2s;">${d+1}</div>`
    ).join('');
    unoAnimFrame=requestAnimationFrame(unoRenderLoop);
  }

  function unoNextStep(){
    if(unoCurrentStep<unoSteps.length-1){
      unoStep(unoCurrentStep+1);
    } else {
      cancelAnimationFrame(unoAnimFrame);
      const data={emoji:'🎴',title:'You learned Standard Uno!',sub:'You now know how to deal, match cards, play action and wild cards, call Uno, challenge, and score. Time to play!'};
      document.getElementById('celebrate-emoji').textContent=data.emoji;
      document.getElementById('celebrate-title').textContent=data.title;
      document.getElementById('celebrate-sub').textContent=data.sub;
      document.getElementById('celebrate-overlay').style.display='flex';
      startConfetti();
    }
  }


  // Build mini board
    const board = document.getElementById('board');
  if (board) {
    const snakeHeads = new Set([17,54,62,87,99]);
    const ladderBases = new Set([4,9,28,40,51]);
    const nums = [];
    for (let row = 9; row >= 0; row--) {
      const r = [];
      for (let col = 0; col < 10; col++) r.push(row * 10 + col + 1);
      if ((9 - row) % 2 === 1) r.reverse();
      nums.push(...r);
    }
    nums.forEach((n, i) => {
      const cell = document.createElement('div');
      cell.className = 'bc';
      if (n === 100) { cell.className += ' bc-win'; cell.textContent = '★'; }
      else if (snakeHeads.has(n)) { cell.className += ' bc-snake'; cell.textContent = '🐍'; }
      else if (ladderBases.has(n)) { cell.className += ' bc-ladder'; cell.textContent = '🪜'; }
      else { cell.className += (i % 2 === 0 ? ' bc-a' : ' bc-b'); cell.textContent = n; }
      board.appendChild(cell);
    });
  }

  // ══ LIVE GAME ENGINE ══
  const G_SNAKES  = {17:7, 54:34, 62:19, 87:24, 99:78};
  const G_LADDERS = {4:14, 9:31, 28:84, 40:59, 51:67};
  const G_COLS = 10, G_PAD = 6, G_CELL = 50, G_GAP = 2;
  const G_BW = G_COLS * G_CELL + (G_COLS-1)*G_GAP + G_PAD*2; // = 524

  let gPos = [0, 0]; // 0 = not yet on board
  let gTurn = 0; // 0=player, 1=AI
  let gRolling = false;
  let gAnimFrame2;
  let gDiceFace = 1;
  let gShakeT = 0;
  let gMoveAnim = null; // {player, from, to, t, special}
  let gHighlight = null;
  let gLogEntries = [];
  const G_COLORS = ['#F59E0B','#EF4444'];
  const G_NAMES  = ['You','AI'];

  function gSquareToRC(n) {
    if (n <= 0) return {row: G_COLS, col: 0};
    const row = Math.floor((n-1)/10);
    const col = (row%2===0) ? (n-1)%10 : 9-(n-1)%10;
    return {row: G_COLS-1-row, col};
  }

  function gCellCenter(sq) {
    if (sq <= 0) {
      const x = G_PAD + G_CELL/2;
      const y = G_PAD + (G_COLS)*(G_CELL+G_GAP) - G_CELL/2 + 12;
      return {x, y};
    }
    const {row,col} = gSquareToRC(sq);
    return {
      x: G_PAD + col*(G_CELL+G_GAP) + G_CELL/2,
      y: G_PAD + row*(G_CELL+G_GAP) + G_CELL/2
    };
  }

  function startGame() {
    gPos = [0,0]; gTurn = 0; gRolling = false;
    gDiceFace = 1; gMoveAnim = null; gHighlight = null; gLogEntries = [];
    document.getElementById('game-winner-banner').style.display = 'none';
    document.getElementById('game-log-entries').innerHTML = '';
    setRollBtn(true);
    updatePlayerCards();
    cancelAnimationFrame(gAnimFrame2);
    drawDiceFace(gDiceFace);
    gGameLoop();
    addLog('🎮 Game started! You go first.');
  }

  function gGameLoop() {
    const canvas = document.getElementById('gameCanvas');
    if (!canvas) return;
    const ctx = canvas.getContext('2d');
    canvas.width = G_BW; canvas.height = G_BW;
    gDrawBoard(ctx);
    gAnimFrame2 = requestAnimationFrame(gGameLoop);
  }

  function gDrawBoard(ctx) {
    ctx.clearRect(0,0,G_BW,G_BW);
    ctx.fillStyle = '#F0FDF9';
    ctx.fillRect(0,0,G_BW,G_BW);

    // Cells
    for (let sq=1; sq<=100; sq++) {
      const {row,col} = gSquareToRC(sq);
      const x = G_PAD + col*(G_CELL+G_GAP);
      const y = G_PAD + row*(G_CELL+G_GAP);
      let bg = (row+col)%2===0 ? '#CCFBF1' : '#E0FAF5';
      if (sq===100) bg='#FEF3C7';
      if (gHighlight && gHighlight.sq===sq) bg=gHighlight.color;
      ctx.fillStyle=bg;
      gRoundRect(ctx,x,y,G_CELL,G_CELL,4); ctx.fill();
      ctx.fillStyle='#4B6B68';
      ctx.font=`bold ${sq>=10?8:9}px sans-serif`;
      ctx.textAlign='center'; ctx.textBaseline='top';
      ctx.fillText(sq, x+G_CELL/2, y+3);
    }

    // Ladders
    const lColors=['#B45309','#0D9488','#2563EB','#7C3AED','#16A34A'];
    Object.entries(G_LADDERS).forEach(([b,t],i) => {
      const from=gCellCenter(+b), to=gCellCenter(+t);
      const dx=to.x-from.x,dy=to.y-from.y,len=Math.sqrt(dx*dx+dy*dy);
      const px=(-dy/len)*5,py=(dx/len)*5;
      const c=lColors[i%lColors.length];
      ctx.save(); ctx.globalAlpha=0.85; ctx.lineCap='round';
      [[from,to]].forEach(()=>{
        ctx.beginPath(); ctx.moveTo(from.x-px,from.y-py); ctx.lineTo(to.x-px,to.y-py);
        ctx.strokeStyle=c; ctx.lineWidth=2.5; ctx.stroke();
        ctx.beginPath(); ctx.moveTo(from.x+px,from.y+py); ctx.lineTo(to.x+px,to.y+py);
        ctx.strokeStyle=c; ctx.lineWidth=2.5; ctx.stroke();
      });
      const rungs=Math.max(3,Math.floor(len/18));
      for(let r=1;r<rungs;r++){
        const tt=r/rungs,rx=from.x+dx*tt,ry=from.y+dy*tt;
        ctx.beginPath(); ctx.moveTo(rx-px*1.1,ry-py*1.1); ctx.lineTo(rx+px*1.1,ry+py*1.1);
        ctx.strokeStyle=c; ctx.lineWidth=2; ctx.stroke();
      }
      ctx.restore();
    });

    // Snakes
    const sColors=[
      {body:'#DC2626',belly:'#FCA5A5'},{body:'#16A34A',belly:'#86EFAC'},
      {body:'#7C3AED',belly:'#C4B5FD'},{body:'#0891B2',belly:'#67E8F9'},
      {body:'#D97706',belly:'#FDE68A'}
    ];
    Object.entries(G_SNAKES).forEach(([h,t],i)=>{
      const from=gCellCenter(+h),to=gCellCenter(+t);
      const dx=to.x-from.x,dy=to.y-from.y,len=Math.sqrt(dx*dx+dy*dy);
      const sc=sColors[i%sColors.length];
      const m1x=from.x+dx*0.33-dy*0.45,m1y=from.y+dy*0.33+dx*0.45;
      const m2x=from.x+dx*0.66+dy*0.45,m2y=from.y+dy*0.66-dx*0.45;
      ctx.save(); ctx.globalAlpha=0.92; ctx.lineCap='round';
      ctx.beginPath(); ctx.moveTo(from.x,from.y); ctx.bezierCurveTo(m1x,m1y,m2x,m2y,to.x,to.y);
      ctx.strokeStyle=sc.body; ctx.lineWidth=7; ctx.stroke();
      ctx.beginPath(); ctx.moveTo(from.x,from.y); ctx.bezierCurveTo(m1x,m1y,m2x,m2y,to.x,to.y);
      ctx.strokeStyle=sc.belly; ctx.lineWidth=3; ctx.stroke();
      // Head
      const HR=7,hdx=m1x-from.x,hdy=m1y-from.y,hl=Math.sqrt(hdx*hdx+hdy*hdy)||1;
      const hax=hdx/hl,hay=hdy/hl,hrx=-hay,hry=hax;
      ctx.translate(from.x,from.y); ctx.rotate(Math.atan2(hay,hax));
      ctx.beginPath(); ctx.ellipse(HR*0.4,0,HR*1.3,HR*0.85,0,0,Math.PI*2);
      ctx.fillStyle=sc.body; ctx.fill();
      ctx.beginPath(); ctx.arc(HR*0.8,-HR*0.45,2,0,Math.PI*2); ctx.fillStyle='white'; ctx.fill();
      ctx.beginPath(); ctx.arc(HR*0.9,-HR*0.45,1,0,Math.PI*2); ctx.fillStyle='#111'; ctx.fill();
      ctx.beginPath(); ctx.moveTo(HR*1.55,0); ctx.lineTo(HR*2.1,0);
      ctx.strokeStyle='#EF4444'; ctx.lineWidth=1.2; ctx.stroke();
      ctx.beginPath(); ctx.moveTo(HR*2.1,0); ctx.lineTo(HR*2.6,-HR*0.5); ctx.moveTo(HR*2.1,0); ctx.lineTo(HR*2.6,HR*0.5);
      ctx.lineWidth=0.9; ctx.stroke();
      ctx.restore();
    });

    // Tokens
    const offsets=[[0,0],[6,-6]];
    for(let p=0;p<2;p++){
      let cx,cy;
      if(gMoveAnim && gMoveAnim.player===p){
        const prog=Math.min(gMoveAnim.t,1);
        const ease=prog<0.5?2*prog*prog:1-Math.pow(-2*prog+2,2)/2;
        const fc=gCellCenter(gMoveAnim.from), tc=gCellCenter(gMoveAnim.to);
        cx=fc.x+(tc.x-fc.x)*ease;
        cy=fc.y+(tc.y-fc.y)*ease - (gMoveAnim.isLadder?Math.sin(prog*Math.PI)*20:0)
                                  + (gMoveAnim.isSnake?Math.sin(prog*Math.PI)*15:0);
      } else {
        const c=gCellCenter(gPos[p]);
        cx=c.x+offsets[p][0]; cy=c.y+offsets[p][1];
      }
      // Shadow
      ctx.save();
      ctx.shadowColor='rgba(0,0,0,0.25)'; ctx.shadowBlur=6; ctx.shadowOffsetY=2;
      ctx.beginPath(); ctx.arc(cx,cy,11,0,Math.PI*2);
      ctx.fillStyle=G_COLORS[p]; ctx.fill(); ctx.shadowBlur=0;
      ctx.beginPath(); ctx.arc(cx-3,cy-3,4,0,Math.PI*2);
      ctx.fillStyle='rgba(255,255,255,0.4)'; ctx.fill();
      // Label
      ctx.fillStyle='white'; ctx.font='bold 8px sans-serif';
      ctx.textAlign='center'; ctx.textBaseline='middle';
      ctx.fillText(p===0?'P':'AI',cx,cy);
      ctx.restore();
    }
  }

  function gRoundRect(ctx,x,y,w,h,r){
    ctx.beginPath();
    ctx.moveTo(x+r,y); ctx.lineTo(x+w-r,y); ctx.quadraticCurveTo(x+w,y,x+w,y+r);
    ctx.lineTo(x+w,y+h-r); ctx.quadraticCurveTo(x+w,y+h,x+w-r,y+h);
    ctx.lineTo(x+r,y+h); ctx.quadraticCurveTo(x,y+h,x,y+h-r);
    ctx.lineTo(x,y+r); ctx.quadraticCurveTo(x,y,x+r,y);
    ctx.closePath();
  }

  function drawDiceFace(face) {
    const canvas=document.getElementById('gameDice');
    if(!canvas) return;
    const ctx=canvas.getContext('2d');
    const s=68;
    ctx.clearRect(0,0,s,s);
    ctx.fillStyle='white';
    gRoundRect(ctx,2,2,s-4,s-4,10); ctx.fill();
    ctx.strokeStyle=gTurn===0?'#F59E0B':'#EF4444';
    ctx.lineWidth=2.5; ctx.stroke();
    const dots={1:[[0,0]],2:[[-1,-1],[1,1]],3:[[-1,-1],[0,0],[1,1]],
      4:[[-1,-1],[1,-1],[-1,1],[1,1]],5:[[-1,-1],[1,-1],[0,0],[-1,1],[1,1]],
      6:[[-1,-1],[1,-1],[-1,0],[1,0],[-1,1],[1,1]]};
    const sp=12,dr=4;
    ctx.fillStyle='#1C2B2A';
    (dots[face]||[]).forEach(([dx,dy])=>{
      ctx.beginPath(); ctx.arc(s/2+dx*sp,s/2+dy*sp,dr,0,Math.PI*2); ctx.fill();
    });
  }

  function rollDice(isPlayer){
    const r1 = Math.floor(Math.random()*6)+1;
    if(isPlayer){
      // 25% chance take better of two rolls — looks like natural luck
      if(Math.random() < 0.25){
        return Math.max(r1, Math.floor(Math.random()*6)+1);
      }
    } else {
      // AI: 20% chance take worse of two rolls — subtle, unnoticeable
      if(Math.random() < 0.20){
        return Math.min(r1, Math.floor(Math.random()*6)+1);
      }
    }
    return r1;
  }

  function setRollBtn(enabled){
    const btn=document.getElementById('roll-game-btn');
    const dice=document.getElementById('gameDice');
    if(!btn||!dice) return;
    btn.disabled=!enabled;
    dice.style.cursor=enabled?'pointer':'default';
    dice.style.opacity=enabled?'1':'0.5';
  }

  function addLog(msg){
    gLogEntries.unshift(msg);
    const el=document.getElementById('game-log-entries');
    if(!el) return;
    el.innerHTML=gLogEntries.slice(0,20).map(e=>`<div class="log-entry">${e}</div>`).join('');
  }

  function updatePlayerCards(){
    for(let p=0;p<2;p++){
      const pc=document.getElementById('pc-'+p);
      const psq=document.getElementById('psq-'+p);
      const pst=document.getElementById('pst-'+p);
      if(pc) pc.classList.toggle('active',gTurn===p);
      if(psq) psq.textContent='Square: '+(gPos[p]===0?'Start':gPos[p]);
      if(pst){
        if(gTurn===p){
          pst.style.color=p===0?'var(--teal)':'#EF4444';
          pst.textContent=p===0?'Your turn — roll!':'AI is thinking...';
        } else {
          pst.style.color='var(--muted)';
          pst.textContent='Waiting...';
        }
      }
    }
    const lbl=document.getElementById('dice-label');
    if(lbl) lbl.textContent=gTurn===0?'Your turn!':'AI rolling...';
    drawDiceFace(gDiceFace);
  }

  function movePlayer(player, face){
    const from = gPos[player];
    let rawTo = from + face;
    let bounced = false;
    const logName = player===0 ? '<strong>You</strong>' : '<strong>AI</strong>';

    if(rawTo > 100){ rawTo = 100-(rawTo-100); bounced = true; }
    if(rawTo < 1) rawTo = 1; // safety clamp
    if(bounced) addLog(`${logName} rolled ${face} — bounced back to ${rawTo}`);
    else addLog(`${logName} rolled ${face} → square ${rawTo}`);

    setRollBtn(false);

    // Step one square at a time
    let current = from;
    const target = rawTo;

    function stepOne(){
      if(current === target){
        gPos[player] = current;
        gMoveAnim = null;
        setTimeout(() => {
          if(G_LADDERS[current]){
            const dest = G_LADDERS[current];
            gHighlight = {sq:current, color:'rgba(34,197,94,0.3)'};
            addLog(`🪜 ${logName} hit a ladder! ${current} → ${dest}`);
            setTimeout(() => {
              gMoveAnim = {player, from:current, to:dest, t:0, isLadder:true, isSnake:false};
              let i2 = setInterval(() => {
                gMoveAnim.t += 0.05;
                if(gMoveAnim.t >= 1){
                  clearInterval(i2);
                  gPos[player] = dest; gMoveAnim = null; gHighlight = null;
                  updatePlayerCards(); checkWin(player, dest);
                }
              }, 16);
            }, 400);
          } else if(G_SNAKES[current]){
            const dest = G_SNAKES[current];
            gHighlight = {sq:current, color:'rgba(220,38,38,0.3)'};
            addLog(`🐍 ${logName} hit a snake! ${current} → ${dest}`);
            setTimeout(() => {
              gMoveAnim = {player, from:current, to:dest, t:0, isLadder:false, isSnake:true};
              let i2 = setInterval(() => {
                gMoveAnim.t += 0.05;
                if(gMoveAnim.t >= 1){
                  clearInterval(i2);
                  gPos[player] = dest; gMoveAnim = null; gHighlight = null;
                  updatePlayerCards(); checkWin(player, dest);
                }
              }, 16);
            }, 400);
          } else {
            updatePlayerCards(); checkWin(player, current);
          }
        }, 100);
        return;
      }

      // Move one step toward target
      const next = current < target ? current + 1 : current - 1;
      if(next < 1 || next > 100){ current = target; stepOne(); return; } // safety
      gMoveAnim = {player, from:current, to:next, t:0, isLadder:false, isSnake:false};
      let interval = setInterval(() => {
        gMoveAnim.t += 0.18;
        if(gMoveAnim.t >= 1){
          clearInterval(interval);
          current = next;
          gPos[player] = current;
          gMoveAnim = null;
          updatePlayerCards();
          setTimeout(stepOne, 55); // pause between each step
        }
      }, 16);
    }

    stepOne();
  }

  function checkWin(player,sq){
    if(sq===100){
      cancelAnimationFrame(gAnimFrame2);
      const banner=document.getElementById('game-winner-banner');
      banner.style.display='flex';
      document.getElementById('gw-emoji').textContent=player===0?'🏆':'🤖';
      document.getElementById('gw-title').textContent=player===0?'You won!':'AI wins!';
      document.getElementById('gw-sub').textContent=player===0?'Congrats — you reached square 100 first!':'Better luck next time! The AI reached 100 first.';
      return;
    }
    // Next turn
    gTurn=1-player;
    updatePlayerCards();
    if(gTurn===1) setTimeout(aiTurn,900);
    else setRollBtn(true);
  }

  function playerRoll(){
    if(gTurn!==0||gRolling) return;
    gRolling=true;
    setRollBtn(false);
    let shakes=0;
    const shakeInterval=setInterval(()=>{
      gDiceFace=rollDice(true); drawDiceFace(gDiceFace);
      shakes++;
      if(shakes>=6){
        clearInterval(shakeInterval);
        const face=rollDice(true); gDiceFace=face; drawDiceFace(face);
        gRolling=false;
        setTimeout(()=>movePlayer(0,face),200);
      }
    },55);
  }

  function aiTurn(){
    setRollBtn(false);
    let shakes=0;
    const shakeInterval=setInterval(()=>{
      gDiceFace=rollDice(false); drawDiceFace(gDiceFace);
      shakes++;
      if(shakes>=6){
        clearInterval(shakeInterval);
        const face=rollDice(false); gDiceFace=face; drawDiceFace(face);
        setTimeout(()=>movePlayer(1,face),200);
      }
    },55);
  }
</script>
</body>
</html>
