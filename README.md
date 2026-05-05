<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Aakash | Kanak Technology</title>
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;700;800&family=Space+Mono:wght@400;700&family=Outfit:wght@300;400;500;600&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --bg: #020d18;
      --surface: #071828;
      --card: #0a1f30;
      --accent: #00e5ff;
      --accent2: #7b2fff;
      --accent3: #ff2f7b;
      --gold: #ffd166;
      --text: #e8f4fd;
      --muted: #7a9bb5;
      --border: rgba(0,229,255,0.15);
      --glow: 0 0 40px rgba(0,229,255,0.18);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--bg);
      color: var(--text);
      font-family: 'Outfit', sans-serif;
      overflow-x: hidden;
      cursor: none;
    }

    /* Custom Cursor */
    .cursor {
      width: 12px; height: 12px;
      background: var(--accent);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9999;
      transition: transform 0.1s;
      mix-blend-mode: screen;
    }
    .cursor-ring {
      width: 36px; height: 36px;
      border: 1.5px solid var(--accent);
      border-radius: 50%;
      position: fixed;
      pointer-events: none;
      z-index: 9998;
      transition: all 0.18s ease;
      mix-blend-mode: screen;
    }

    /* GRID LINES BG */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image:
        linear-gradient(rgba(0,229,255,0.025) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0,229,255,0.025) 1px, transparent 1px);
      background-size: 50px 50px;
      z-index: 0;
      pointer-events: none;
    }

    /* NAV */
    nav {
      position: fixed; top: 0; left: 0; right: 0; z-index: 100;
      display: flex; align-items: center; justify-content: space-between;
      padding: 18px 60px;
      background: rgba(2,13,24,0.8);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
    }
    .logo {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1.4rem;
      color: var(--accent);
      letter-spacing: 2px;
      text-decoration: none;
    }
    .logo span { color: var(--text); }
    .nav-links { display: flex; gap: 40px; list-style: none; }
    .nav-links a {
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      color: var(--muted);
      text-decoration: none;
      letter-spacing: 2px;
      text-transform: uppercase;
      transition: color 0.3s;
      position: relative;
    }
    .nav-links a::after {
      content: '';
      position: absolute; bottom: -4px; left: 0;
      width: 0; height: 1px;
      background: var(--accent);
      transition: width 0.3s;
    }
    .nav-links a:hover { color: var(--accent); }
    .nav-links a:hover::after { width: 100%; }
    .nav-cta {
      font-family: 'Space Mono', monospace;
      font-size: 0.75rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      padding: 10px 24px;
      border: 1px solid var(--accent);
      color: var(--accent);
      background: transparent;
      cursor: none;
      transition: all 0.3s;
    }
    .nav-cta:hover { background: var(--accent); color: var(--bg); }

    /* HERO */
    .hero {
      min-height: 100vh;
      display: flex; align-items: center;
      padding: 120px 60px 60px;
      position: relative;
      overflow: hidden;
    }
    .hero-orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(80px);
      pointer-events: none;
    }
    .orb1 { width: 500px; height: 500px; background: rgba(0,229,255,0.08); top: -100px; right: -100px; }
    .orb2 { width: 400px; height: 400px; background: rgba(123,47,255,0.08); bottom: -100px; left: 100px; }
    .orb3 { width: 300px; height: 300px; background: rgba(255,47,123,0.06); top: 40%; right: 20%; }

    .hero-content { position: relative; z-index: 2; max-width: 700px; }
    .hero-badge {
      display: inline-flex; align-items: center; gap: 10px;
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 3px;
      text-transform: uppercase;
      color: var(--accent);
      border: 1px solid var(--border);
      padding: 8px 20px;
      margin-bottom: 32px;
      animation: fadeInDown 0.8s ease both;
    }
    .badge-dot { width: 6px; height: 6px; background: var(--accent); border-radius: 50%; animation: pulse 2s infinite; }
    @keyframes pulse { 0%,100%{opacity:1; transform:scale(1)} 50%{opacity:0.4; transform:scale(1.4)} }

    .hero-title {
      font-family: 'Syne', sans-serif;
      font-size: clamp(3.5rem, 8vw, 7rem);
      font-weight: 800;
      line-height: 0.95;
      letter-spacing: -2px;
      margin-bottom: 12px;
      animation: fadeInUp 0.9s 0.1s ease both;
    }
    .hero-title .name { color: var(--accent); display: block; }
    .hero-title .role { color: var(--text); display: block; }

    .hero-sub {
      font-family: 'Space Mono', monospace;
      font-size: 0.85rem;
      color: var(--accent2);
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 28px;
      animation: fadeInUp 0.9s 0.2s ease both;
    }
    .hero-desc {
      font-size: 1.05rem;
      color: var(--muted);
      line-height: 1.8;
      max-width: 560px;
      margin-bottom: 48px;
      animation: fadeInUp 0.9s 0.3s ease both;
    }
    .hero-btns { display: flex; gap: 20px; flex-wrap: wrap; animation: fadeInUp 0.9s 0.4s ease both; }
    .btn-primary {
      padding: 16px 40px;
      background: var(--accent);
      color: var(--bg);
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      border: none; cursor: none;
      font-weight: 700;
      transition: all 0.3s;
      position: relative; overflow: hidden;
    }
    .btn-primary::before {
      content: '';
      position: absolute; inset: 0;
      background: var(--accent2);
      transform: translateX(-100%);
      transition: transform 0.4s;
    }
    .btn-primary:hover::before { transform: translateX(0); }
    .btn-primary span { position: relative; z-index: 1; }
    .btn-outline {
      padding: 16px 40px;
      border: 1px solid var(--muted);
      color: var(--text);
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      background: transparent; cursor: none;
      transition: all 0.3s;
    }
    .btn-outline:hover { border-color: var(--accent); color: var(--accent); }

    /* HERO IMAGE */
    .hero-visual {
      position: absolute; right: 60px; top: 50%; transform: translateY(-50%);
      z-index: 1; animation: fadeInRight 1s 0.3s ease both;
    }
    .hero-img-frame {
      width: 380px; height: 480px;
      position: relative;
    }
    .hero-img-frame::before {
      content: '';
      position: absolute;
      inset: -2px;
      background: linear-gradient(135deg, var(--accent), var(--accent2), var(--accent3));
      z-index: -1;
      border-radius: 2px;
      animation: rotateBorder 4s linear infinite;
    }
    @keyframes rotateBorder {
      0% { opacity: 1; }
      50% { opacity: 0.5; }
      100% { opacity: 1; }
    }
    .hero-img-frame img {
      width: 100%; height: 100%;
      object-fit: cover;
      display: block;
      filter: grayscale(20%) contrast(1.1);
    }
    .hero-img-frame .scan-line {
      position: absolute; left: 0; right: 0;
      height: 2px;
      background: linear-gradient(90deg, transparent, var(--accent), transparent);
      animation: scan 3s linear infinite;
      z-index: 2;
    }
    @keyframes scan { 0%{top:0} 100%{top:100%} }

    .hero-stats {
      position: absolute; bottom: -20px; left: -20px;
      background: var(--card);
      border: 1px solid var(--border);
      padding: 20px 28px;
      display: grid; grid-template-columns: repeat(3,1fr);
      gap: 20px;
      z-index: 3;
    }
    .stat { text-align: center; }
    .stat-num {
      font-family: 'Syne', sans-serif;
      font-size: 1.8rem; font-weight: 800;
      color: var(--accent);
    }
    .stat-label {
      font-family: 'Space Mono', monospace;
      font-size: 0.6rem;
      color: var(--muted);
      letter-spacing: 1px;
      text-transform: uppercase;
    }

    /* SCROLLING TICKER */
    .ticker {
      background: var(--accent);
      padding: 14px 0;
      overflow: hidden;
      position: relative;
      z-index: 5;
    }
    .ticker-track {
      display: flex; gap: 60px;
      animation: ticker 20s linear infinite;
      white-space: nowrap;
    }
    .ticker-item {
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      font-weight: 700;
      color: var(--bg);
      letter-spacing: 3px;
      text-transform: uppercase;
      flex-shrink: 0;
    }
    .ticker-sep { color: rgba(0,0,0,0.4); }
    @keyframes ticker { 0%{transform:translateX(0)} 100%{transform:translateX(-50%)} }

    /* SECTIONS */
    section { padding: 120px 60px; position: relative; }

    .section-tag {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 4px;
      text-transform: uppercase;
      color: var(--accent);
      margin-bottom: 12px;
    }
    .section-title {
      font-family: 'Syne', sans-serif;
      font-size: clamp(2rem, 4vw, 3.5rem);
      font-weight: 800;
      line-height: 1.1;
      margin-bottom: 16px;
    }
    .section-desc {
      color: var(--muted);
      font-size: 1rem;
      max-width: 560px;
      line-height: 1.8;
    }

    /* ABOUT */
    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      margin-top: 64px;
      align-items: center;
    }
    .about-img-wrap {
      position: relative;
    }
    .about-img-wrap img {
      width: 100%;
      height: 500px;
      object-fit: cover;
      display: block;
      filter: grayscale(15%);
    }
    .about-img-wrap::after {
      content: '';
      position: absolute;
      bottom: -16px; right: -16px;
      width: 200px; height: 200px;
      background: linear-gradient(135deg, var(--accent2), var(--accent));
      z-index: -1;
      opacity: 0.5;
    }
    .about-img-wrap .corner-tag {
      position: absolute; top: 20px; right: 20px;
      background: var(--accent);
      color: var(--bg);
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 2px;
      padding: 8px 16px;
      font-weight: 700;
    }
    .about-content { }
    .about-highlight {
      font-size: 1.15rem;
      line-height: 1.9;
      color: var(--text);
      margin-bottom: 32px;
    }
    .about-highlight strong { color: var(--accent); font-weight: 600; }
    .skills-grid {
      display: grid; grid-template-columns: repeat(2, 1fr);
      gap: 12px; margin-top: 32px;
    }
    .skill-chip {
      display: flex; align-items: center; gap: 10px;
      background: var(--card);
      border: 1px solid var(--border);
      padding: 12px 16px;
      font-family: 'Space Mono', monospace;
      font-size: 0.72rem;
      color: var(--text);
      letter-spacing: 1px;
      transition: all 0.3s;
    }
    .skill-chip:hover { border-color: var(--accent); color: var(--accent); transform: translateX(4px); }
    .skill-chip::before { content: '▸'; color: var(--accent); }

    /* SERVICES */
    .services { background: var(--surface); }
    .services-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 2px;
      margin-top: 64px;
    }
    .service-card {
      background: var(--card);
      padding: 48px 36px;
      position: relative;
      overflow: hidden;
      transition: all 0.4s;
      cursor: none;
    }
    .service-card::before {
      content: '';
      position: absolute; top: 0; left: 0;
      width: 100%; height: 3px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      transform: scaleX(0);
      transition: transform 0.4s;
    }
    .service-card:hover::before { transform: scaleX(1); }
    .service-card:hover { background: #0d2640; transform: translateY(-4px); }
    .service-icon {
      width: 64px; height: 64px;
      display: flex; align-items: center; justify-content: center;
      font-size: 2rem;
      margin-bottom: 28px;
      position: relative;
    }
    .service-icon::before {
      content: '';
      position: absolute; inset: 0;
      background: rgba(0,229,255,0.08);
      border-radius: 50%;
    }
    .service-num {
      position: absolute; top: 24px; right: 24px;
      font-family: 'Syne', sans-serif;
      font-size: 4rem; font-weight: 800;
      color: rgba(0,229,255,0.04);
      line-height: 1;
    }
    .service-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.35rem;
      font-weight: 700;
      margin-bottom: 16px;
      color: var(--text);
    }
    .service-desc { color: var(--muted); font-size: 0.92rem; line-height: 1.7; }
    .service-tags { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 24px; }
    .stag {
      font-family: 'Space Mono', monospace;
      font-size: 0.62rem;
      letter-spacing: 1.5px;
      color: var(--accent);
      border: 1px solid var(--border);
      padding: 4px 12px;
    }

    /* FEATURED PROJECT */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 24px;
      margin-top: 64px;
    }
    .project-card {
      background: var(--card);
      border: 1px solid var(--border);
      overflow: hidden;
      position: relative;
      transition: all 0.4s;
      cursor: none;
    }
    .project-card:hover { border-color: var(--accent); transform: translateY(-6px); box-shadow: var(--glow); }
    .project-card.featured { grid-column: span 2; }
    .project-img {
      width: 100%; height: 220px;
      object-fit: cover;
      display: block;
      transition: transform 0.5s;
      filter: grayscale(20%);
    }
    .project-card.featured .project-img { height: 340px; }
    .project-card:hover .project-img { transform: scale(1.04); }
    .project-overlay {
      position: absolute; inset: 0;
      background: linear-gradient(180deg, transparent 40%, rgba(2,13,24,0.95) 100%);
      opacity: 0;
      transition: opacity 0.4s;
      display: flex; align-items: flex-end;
      padding: 32px;
    }
    .project-card:hover .project-overlay { opacity: 1; }
    .overlay-link {
      font-family: 'Space Mono', monospace;
      font-size: 0.7rem;
      letter-spacing: 2px;
      color: var(--accent);
      border-bottom: 1px solid var(--accent);
      padding-bottom: 4px;
    }
    .project-info { padding: 28px; }
    .project-category {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 3px;
      color: var(--accent2);
      text-transform: uppercase;
      margin-bottom: 8px;
    }
    .project-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.2rem;
      font-weight: 700;
      margin-bottom: 12px;
    }
    .project-desc { color: var(--muted); font-size: 0.88rem; line-height: 1.6; }

    /* COMPANY */
    .company { background: var(--surface); }
    .company-inner {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 80px; align-items: center;
      margin-top: 64px;
    }
    .company-logo-block {
      display: flex; flex-direction: column;
      align-items: center; justify-content: center;
      background: var(--card);
      border: 1px solid var(--border);
      padding: 60px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .company-logo-block::before {
      content: '';
      position: absolute; inset: 0;
      background: radial-gradient(ellipse at center, rgba(0,229,255,0.06) 0%, transparent 70%);
    }
    .company-logo-icon {
      font-size: 5rem; margin-bottom: 20px;
      filter: drop-shadow(0 0 20px rgba(0,229,255,0.4));
    }
    .company-name-big {
      font-family: 'Syne', sans-serif;
      font-size: 2rem; font-weight: 800;
      color: var(--accent);
      letter-spacing: 1px;
      margin-bottom: 8px;
    }
    .company-tagline {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 3px;
      color: var(--muted);
      text-transform: uppercase;
    }
    .company-features { display: flex; flex-direction: column; gap: 20px; }
    .feat-item {
      display: flex; gap: 20px;
      background: var(--card);
      border: 1px solid var(--border);
      padding: 24px;
      transition: all 0.3s;
    }
    .feat-item:hover { border-color: var(--accent); }
    .feat-icon { font-size: 1.8rem; flex-shrink: 0; }
    .feat-title { font-family: 'Syne', sans-serif; font-size: 1rem; font-weight: 700; margin-bottom: 6px; }
    .feat-desc { color: var(--muted); font-size: 0.88rem; line-height: 1.6; }

    /* TESTIMONIALS / CERTIFICATIONS */
    .certs-grid {
      display: grid; grid-template-columns: repeat(4, 1fr);
      gap: 16px; margin-top: 64px;
    }
    .cert-card {
      background: var(--card);
      border: 1px solid var(--border);
      padding: 32px 24px;
      text-align: center;
      transition: all 0.3s;
    }
    .cert-card:hover { border-color: var(--accent); transform: translateY(-4px); }
    .cert-icon { font-size: 2.5rem; margin-bottom: 16px; }
    .cert-name { font-family: 'Syne', sans-serif; font-size: 0.95rem; font-weight: 700; margin-bottom: 8px; }
    .cert-org { font-family: 'Space Mono', monospace; font-size: 0.65rem; color: var(--accent); letter-spacing: 1px; }

    /* CONTACT */
    .contact-inner {
      display: grid; grid-template-columns: 1fr 1fr;
      gap: 80px; margin-top: 64px;
    }
    .contact-info { }
    .contact-item {
      display: flex; align-items: flex-start; gap: 20px;
      margin-bottom: 32px;
      padding-bottom: 32px;
      border-bottom: 1px solid var(--border);
    }
    .contact-item:last-child { border-bottom: none; }
    .contact-icon {
      width: 48px; height: 48px;
      display: flex; align-items: center; justify-content: center;
      border: 1px solid var(--border);
      font-size: 1.2rem;
      flex-shrink: 0;
      color: var(--accent);
    }
    .contact-label {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 2px;
      color: var(--muted);
      text-transform: uppercase;
      margin-bottom: 6px;
    }
    .contact-value { color: var(--text); font-size: 1rem; }

    .contact-form { display: flex; flex-direction: column; gap: 16px; }
    .form-group { display: flex; flex-direction: column; gap: 8px; }
    .form-label {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      letter-spacing: 2px;
      color: var(--muted);
      text-transform: uppercase;
    }
    .form-input, .form-textarea {
      background: var(--card);
      border: 1px solid var(--border);
      color: var(--text);
      padding: 14px 18px;
      font-family: 'Outfit', sans-serif;
      font-size: 0.95rem;
      transition: border-color 0.3s;
      outline: none;
      resize: none;
    }
    .form-input:focus, .form-textarea:focus { border-color: var(--accent); }
    .form-textarea { height: 140px; }
    .form-submit {
      padding: 16px 40px;
      background: linear-gradient(90deg, var(--accent), var(--accent2));
      color: var(--bg);
      font-family: 'Space Mono', monospace;
      font-size: 0.78rem;
      letter-spacing: 2px;
      text-transform: uppercase;
      border: none; cursor: none;
      font-weight: 700;
      transition: all 0.3s;
      align-self: flex-start;
    }
    .form-submit:hover { opacity: 0.85; transform: translateY(-2px); }

    /* FOOTER */
    footer {
      background: #010a12;
      border-top: 1px solid var(--border);
      padding: 60px;
      display: flex; align-items: center; justify-content: space-between;
    }
    .footer-logo {
      font-family: 'Syne', sans-serif;
      font-size: 1.4rem; font-weight: 800;
      color: var(--accent);
    }
    .footer-logo span { color: var(--text); }
    .footer-copy {
      font-family: 'Space Mono', monospace;
      font-size: 0.65rem;
      color: var(--muted);
      letter-spacing: 1px;
    }
    .social-links { display: flex; gap: 12px; }
    .social-btn {
      width: 40px; height: 40px;
      border: 1px solid var(--border);
      display: flex; align-items: center; justify-content: center;
      color: var(--muted);
      font-size: 1rem;
      transition: all 0.3s;
      cursor: none;
    }
    .social-btn:hover { border-color: var(--accent); color: var(--accent); }

    /* ANIMATIONS */
    @keyframes fadeInDown { from{opacity:0;transform:translateY(-20px)} to{opacity:1;transform:translateY(0)} }
    @keyframes fadeInUp { from{opacity:0;transform:translateY(30px)} to{opacity:1;transform:translateY(0)} }
    @keyframes fadeInRight { from{opacity:0;transform:translate(40px,-50%)} to{opacity:1;transform:translate(0,-50%)} }

    .reveal {
      opacity: 0;
      transform: translateY(30px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible { opacity: 1; transform: translateY(0); }

    /* Responsive */
    @media (max-width: 1100px) {
      .hero-visual { display: none; }
      .about-grid, .company-inner, .contact-inner { grid-template-columns: 1fr; gap: 40px; }
      .services-grid { grid-template-columns: 1fr 1fr; }
      .certs-grid { grid-template-columns: repeat(2, 1fr); }
      .projects-grid { grid-template-columns: 1fr; }
      .project-card.featured { grid-column: span 1; }
      nav { padding: 16px 24px; }
      section { padding: 80px 24px; }
      .hero { padding: 120px 24px 60px; }
      footer { padding: 40px 24px; flex-direction: column; gap: 20px; text-align: center; }
    }
    @media (max-width: 640px) {
      .nav-links { display: none; }
      .services-grid { grid-template-columns: 1fr; }
      .certs-grid { grid-template-columns: 1fr 1fr; }
    }
  </style>
</head>
<body>

  <!-- Custom Cursor -->
  <div class="cursor" id="cursor"></div>
  <div class="cursor-ring" id="cursorRing"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="logo">KT<span>.</span></a>
    <ul class="nav-links">
      <li><a href="#about">About</a></li>
      <li><a href="#services">Services</a></li>
      <li><a href="#projects">Projects</a></li>
      <li><a href="#company">Company</a></li>
      <li><a href="#contact">Contact</a></li>
    </ul>
    <button class="nav-cta" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">Hire Me</button>
  </nav>

  <!-- HERO -->
  <section class="hero" id="home">
    <div class="hero-orb orb1"></div>
    <div class="hero-orb orb2"></div>
    <div class="hero-orb orb3"></div>

    <div class="hero-content">
      <div class="hero-badge">
        <span class="badge-dot"></span>
        Available for Projects
      </div>
      <h1 class="hero-title">
        <span class="name">Aakash</span>
        <span class="role">Cyber<br>Security</span>
      </h1>
      <div class="hero-sub">Expert &amp; Founder · Kanak Technology</div>
      <p class="hero-desc">
        Building the digital fortress of tomorrow. I specialize in cybersecurity, software development, and web technologies — protecting and empowering businesses through cutting-edge solutions.
      </p>
      <div class="hero-btns">
        <button class="btn-primary" onclick="document.getElementById('services').scrollIntoView({behavior:'smooth'})">
          <span>Explore Services</span>
        </button>
        <button class="btn-outline" onclick="document.getElementById('contact').scrollIntoView({behavior:'smooth'})">
          Get In Touch
        </button>
      </div>
    </div>

    <div class="hero-visual">
      <div class="hero-img-frame">
        <img src="https://images.unsplash.com/photo-1614741118887-7a4ee193a5fa?w=600&q=80" alt="Aakash - Cybersecurity Expert"/>
        <div class="scan-line"></div>
        <div class="hero-stats">
          <div class="stat">
            <div class="stat-num">5+</div>
            <div class="stat-label">Years Exp</div>
          </div>
          <div class="stat">
            <div class="stat-num">120+</div>
            <div class="stat-label">Projects</div>
          </div>
          <div class="stat">
            <div class="stat-num">98%</div>
            <div class="stat-label">Success</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- TICKER -->
  <div class="ticker">
    <div class="ticker-track" id="tickerTrack">
      <span class="ticker-item">Cybersecurity <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Penetration Testing <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Web Development <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Software Engineering <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Network Security <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Cloud Solutions <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Kanak Technology <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Cybersecurity <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Penetration Testing <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Web Development <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Software Engineering <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Network Security <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Cloud Solutions <span class="ticker-sep">✦</span></span>
      <span class="ticker-item">Kanak Technology <span class="ticker-sep">✦</span></span>
    </div>
  </div>

  <!-- ABOUT -->
  <section id="about">
    <div class="section-tag">// About Me</div>
    <h2 class="section-title">The Mind Behind<br>the Security</h2>
    <p class="section-desc">Securing digital ecosystems with precision, innovation, and expertise.</p>

    <div class="about-grid reveal">
      <div class="about-img-wrap">
        <img src="https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?w=600&q=80" alt="Aakash - Cybersecurity Professional"/>
        <div class="corner-tag">FOUNDER · CEO</div>
      </div>
      <div class="about-content">
        <p class="about-highlight">
          I'm <strong>Aakash</strong>, a cybersecurity expert and the <strong>Founder of Kanak Technology</strong>. With years of hands-on experience in ethical hacking, network defense, and full-stack development, I've built a company that stands at the intersection of <strong>security and innovation</strong>.
        </p>
        <p class="about-highlight" style="font-size:0.95rem; color: var(--muted);">
          At Kanak Technology, we don't just build software — we build it <strong>secure from the ground up</strong>. Our team delivers enterprise-grade cybersecurity, modern web solutions, and robust software that businesses trust.
        </p>
        <div class="skills-grid">
          <div class="skill-chip">Ethical Hacking</div>
          <div class="skill-chip">Penetration Testing</div>
          <div class="skill-chip">VAPT</div>
          <div class="skill-chip">Network Security</div>
          <div class="skill-chip">Full-Stack Dev</div>
          <div class="skill-chip">Cloud Security</div>
          <div class="skill-chip">Malware Analysis</div>
          <div class="skill-chip">OSINT</div>
        </div>
      </div>
    </div>
  </section>

  <!-- SERVICES -->
  <section id="services" class="services">
    <div class="section-tag">// What I Do</div>
    <h2 class="section-title">Services &amp;<br>Expertise</h2>
    <p class="section-desc">Comprehensive digital solutions — from securing your infrastructure to building your next product.</p>

    <div class="services-grid reveal">
      <div class="service-card">
        <div class="service-num">01</div>
        <div class="service-icon">🛡️</div>
        <div class="service-title">Cybersecurity</div>
        <div class="service-desc">End-to-end security audits, vulnerability assessment, and penetration testing to protect your digital assets from evolving threats.</div>
        <div class="service-tags">
          <span class="stag">VAPT</span>
          <span class="stag">Pen Testing</span>
          <span class="stag">Threat Intel</span>
          <span class="stag">SOC</span>
        </div>
      </div>
      <div class="service-card">
        <div class="service-num">02</div>
        <div class="service-icon">💻</div>
        <div class="service-title">Software Development</div>
        <div class="service-desc">Custom software solutions built with performance, scalability, and security at the core. From architecture to deployment.</div>
        <div class="service-tags">
          <span class="stag">Python</span>
          <span class="stag">Node.js</span>
          <span class="stag">APIs</span>
          <span class="stag">SaaS</span>
        </div>
      </div>
      <div class="service-card">
        <div class="service-num">03</div>
        <div class="service-icon">🌐</div>
        <div class="service-title">Web Development</div>
        <div class="service-desc">Premium, high-performance websites and web apps. Modern design, blazing speed, and built with best-in-class security practices.</div>
        <div class="service-tags">
          <span class="stag">React</span>
          <span class="stag">Next.js</span>
          <span class="stag">UI/UX</span>
          <span class="stag">PWA</span>
        </div>
      </div>
    </div>
  </section>

  <!-- PROJECTS -->
  <section id="projects">
    <div class="section-tag">// Portfolio</div>
    <h2 class="section-title">Selected<br>Projects</h2>
    <p class="section-desc">Real-world solutions delivered with precision and technical excellence.</p>

    <div class="projects-grid reveal">
      <div class="project-card featured">
        <img class="project-img" src="https://images.unsplash.com/photo-1550751827-4bd374c3f58b?w=1200&q=80" alt="Security Operations Platform"/>
        <div class="project-overlay">
          <span class="overlay-link">VIEW PROJECT →</span>
        </div>
        <div class="project-info">
          <div class="project-category">Cybersecurity · Enterprise</div>
          <div class="project-title">Security Operations Center Dashboard</div>
          <div class="project-desc">A real-time SOC platform for monitoring threats, incidents, and network activity across enterprise infrastructure. Built with advanced analytics and AI-powered threat detection.</div>
        </div>
      </div>
      <div class="project-card">
        <img class="project-img" src="https://images.unsplash.com/photo-1461749280684-dccba630e2f6?w=800&q=80" alt="Web App Development"/>
        <div class="project-overlay">
          <span class="overlay-link">VIEW PROJECT →</span>
        </div>
        <div class="project-info">
          <div class="project-category">Web Development</div>
          <div class="project-title">FinTech Web Platform</div>
          <div class="project-desc">Secure, high-performance financial web application with end-to-end encryption and compliance-ready architecture.</div>
        </div>
      </div>
      <div class="project-card">
        <img class="project-img" src="https://images.unsplash.com/photo-1544197150-b99a580bb7a8?w=800&q=80" alt="Network Security"/>
        <div class="project-overlay">
          <span class="overlay-link">VIEW PROJECT →</span>
        </div>
        <div class="project-info">
          <div class="project-category">Network Security</div>
          <div class="project-title">Zero-Trust Network Architecture</div>
          <div class="project-desc">Designed and deployed a zero-trust security model for a 500+ employee organization, eliminating internal trust boundaries.</div>
        </div>
      </div>
    </div>
  </section>

  <!-- COMPANY -->
  <section id="company" class="company">
    <div class="section-tag">// The Company</div>
    <h2 class="section-title">Kanak<br>Technology</h2>
    <p class="section-desc">A next-generation tech company built on security-first principles and innovation.</p>

    <div class="company-inner reveal">
      <div class="company-logo-block">
        <div class="company-logo-icon">⚡</div>
        <div class="company-name-big">KANAK TECHNOLOGY</div>
        <div class="company-tagline">Secure · Innovate · Elevate</div>
      </div>
      <div class="company-features">
        <div class="feat-item">
          <div class="feat-icon">🔐</div>
          <div>
            <div class="feat-title">Security-First Culture</div>
            <div class="feat-desc">Every product we build starts with a security review. Our team treats every line of code as a potential attack surface.</div>
          </div>
        </div>
        <div class="feat-item">
          <div class="feat-icon">🚀</div>
          <div>
            <div class="feat-title">Innovation Lab</div>
            <div class="feat-desc">Constantly researching emerging threats and technologies to keep our clients ahead of the curve.</div>
          </div>
        </div>
        <div class="feat-item">
          <div class="feat-icon">🤝</div>
          <div>
            <div class="feat-title">End-to-End Partnership</div>
            <div class="feat-desc">From concept to deployment and ongoing support — we're your long-term technology partner, not just a vendor.</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- CERTIFICATIONS -->
  <section>
    <div class="section-tag">// Credentials</div>
    <h2 class="section-title">Certifications &amp;<br>Recognition</h2>
    <div class="certs-grid reveal">
      <div class="cert-card">
        <div class="cert-icon">🏆</div>
        <div class="cert-name">CEH</div>
        <div class="cert-org">Certified Ethical Hacker</div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🔒</div>
        <div class="cert-name">CISSP</div>
        <div class="cert-org">Information System Security</div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">⚙️</div>
        <div class="cert-name">CompTIA Security+</div>
        <div class="cert-org">CompTIA Certified</div>
      </div>
      <div class="cert-card">
        <div class="cert-icon">🌐</div>
        <div class="cert-name">OSCP</div>
        <div class="cert-org">Offensive Security</div>
      </div>
    </div>
  </section>

  <!-- CONTACT -->
  <section id="contact" style="background: var(--surface);">
    <div class="section-tag">// Contact</div>
    <h2 class="section-title">Let's Build<br>Something Secure</h2>
    <p class="section-desc">Ready to protect your business or build your next digital product? Let's talk.</p>

    <div class="contact-inner reveal">
      <div class="contact-info">
        <div class="contact-item">
          <div class="contact-icon">📧</div>
          <div>
            <div class="contact-label">Email</div>
            <div class="contact-value">aakash@kanaktechnology.com</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📞</div>
          <div>
            <div class="contact-label">Phone</div>
            <div class="contact-value">+91 98XXX XXXXX</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">🏢</div>
          <div>
            <div class="contact-label">Company</div>
            <div class="contact-value">Kanak Technology</div>
          </div>
        </div>
        <div class="contact-item">
          <div class="contact-icon">📍</div>
          <div>
            <div class="contact-label">Location</div>
            <div class="contact-value">India</div>
          </div>
        </div>
      </div>
      <form class="contact-form" onsubmit="handleSubmit(event)">
        <div class="form-group">
          <label class="form-label">Your Name</label>
          <input class="form-input" type="text" placeholder="John Doe" required/>
        </div>
        <div class="form-group">
          <label class="form-label">Email Address</label>
          <input class="form-input" type="email" placeholder="john@company.com" required/>
        </div>
        <div class="form-group">
          <label class="form-label">Subject</label>
          <input class="form-input" type="text" placeholder="Security Audit / Project Inquiry"/>
        </div>
        <div class="form-group">
          <label class="form-label">Message</label>
          <textarea class="form-textarea" placeholder="Tell me about your project or security needs..."></textarea>
        </div>
        <button type="submit" class="form-submit">Send Message →</button>
        <div id="form-msg" style="font-family:'Space Mono',monospace;font-size:0.75rem;color:var(--accent);display:none;margin-top:8px;">
          ✓ Message sent! I'll get back to you soon.
        </div>
      </form>
    </div>
  </section>

  <!-- FOOTER -->
  <footer>
    <div class="footer-logo">KANAK<span>TECHNOLOGY</span></div>
    <div class="footer-copy">© 2025 Aakash · Kanak Technology · All Rights Reserved</div>
    <div class="social-links">
      <a class="social-btn" href="#" title="LinkedIn">in</a>
      <a class="social-btn" href="#" title="GitHub">gh</a>
      <a class="social-btn" href="#" title="Twitter">tw</a>
    </div>
  </footer>

  <script>
    // Custom Cursor
    const cursor = document.getElementById('cursor');
    const ring = document.getElementById('cursorRing');
    let mx = 0, my = 0, rx = 0, ry = 0;

    document.addEventListener('mousemove', e => {
      mx = e.clientX; my = e.clientY;
      cursor.style.left = mx - 6 + 'px';
      cursor.style.top = my - 6 + 'px';
    });

    function animateRing() {
      rx += (mx - rx) * 0.12;
      ry += (my - ry) * 0.12;
      ring.style.left = rx - 18 + 'px';
      ring.style.top = ry - 18 + 'px';
      requestAnimationFrame(animateRing);
    }
    animateRing();

    document.querySelectorAll('button, a, .service-card, .project-card, .cert-card').forEach(el => {
      el.addEventListener('mouseenter', () => {
        cursor.style.transform = 'scale(2)';
        ring.style.transform = 'scale(1.4)';
        ring.style.borderColor = 'var(--accent2)';
      });
      el.addEventListener('mouseleave', () => {
        cursor.style.transform = 'scale(1)';
        ring.style.transform = 'scale(1)';
        ring.style.borderColor = 'var(--accent)';
      });
    });

    // Scroll Reveal
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver(entries => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          setTimeout(() => entry.target.classList.add('visible'), i * 80);
        }
      });
    }, { threshold: 0.1 });
    reveals.forEach(r => observer.observe(r));

    // Navbar active
    const sections = document.querySelectorAll('section[id]');
    const navLinks = document.querySelectorAll('.nav-links a');
    window.addEventListener('scroll', () => {
      const scrollY = window.scrollY;
      sections.forEach(section => {
        const top = section.offsetTop - 100;
        const h = section.offsetHeight;
        const id = section.getAttribute('id');
        if (scrollY >= top && scrollY < top + h) {
          navLinks.forEach(a => {
            a.style.color = '';
            if (a.getAttribute('href') === '#' + id) a.style.color = 'var(--accent)';
          });
        }
      });
    });

    // Form submit
    function handleSubmit(e) {
      e.preventDefault();
      const msg = document.getElementById('form-msg');
      msg.style.display = 'block';
      e.target.reset();
      setTimeout(() => msg.style.display = 'none', 5000);
    }

    // Glitch title effect
    const title = document.querySelector('.hero-title .name');
    const chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!@#$%';
    let orig = title.textContent;
    let glitching = false;
    title.addEventListener('mouseenter', () => {
      if (glitching) return;
      glitching = true;
      let iter = 0;
      const interval = setInterval(() => {
        title.textContent = orig.split('').map((c, i) => {
          if (i < iter) return orig[i];
          return c === ' ' ? ' ' : chars[Math.floor(Math.random() * chars.length)];
        }).join('');
        if (iter >= orig.length) { clearInterval(interval); title.textContent = orig; glitching = false; }
        iter += 0.5;
      }, 40);
    });
  </script>
</body>
</html>
