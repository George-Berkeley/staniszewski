<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Bartek Staniszewski</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Karla:wght@300;400;500&display=swap" rel="stylesheet">

  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --ink:    #1a1612;
      --paper:  #f5f0e8;
      --cream:  #ede7d9;
      --gold:   #b5802a;
      --muted:  #7a7060;
      --rule:   rgba(26,22,18,.15);
      --serif:  'Cormorant Garamond', Georgia, serif;
      --sans:   'Karla', sans-serif;
    }

    html { scroll-behavior: smooth; }

    body {
      background: var(--paper);
      color: var(--ink);
      font-family: var(--sans);
      font-size: 15px;
      line-height: 1.7;
      cursor: none;
    }

    /* ── Custom cursor ── */
    .cursor {
      position: fixed; top: 0; left: 0;
      width: 10px; height: 10px;
      background: var(--gold);
      border-radius: 50%;
      pointer-events: none;
      transform: translate(-50%, -50%);
      transition: transform .12s ease, width .2s ease, height .2s ease;
      z-index: 9999;
      mix-blend-mode: multiply;
    }
    a:hover ~ .cursor, a:hover .cursor { width: 20px; height: 20px; }

    /* ── Nav ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      display: flex; justify-content: space-between; align-items: center;
      padding: 1.4rem 3rem;
      background: var(--paper);
      border-bottom: 1px solid var(--rule);
      z-index: 100;
      transition: box-shadow .3s;
    }
    nav.scrolled { box-shadow: 0 2px 20px rgba(0,0,0,.06); }
    .nav-logo {
      font-family: var(--serif);
      font-size: 1.25rem;
      font-weight: 600;
      letter-spacing: .02em;
      color: var(--ink);
      text-decoration: none;
    }
    .nav-links { display: flex; gap: 2.4rem; list-style: none; }
    .nav-links a {
      font-family: var(--sans);
      font-size: .78rem;
      font-weight: 500;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      position: relative;
      transition: color .2s;
    }
    .nav-links a::after {
      content: '';
      position: absolute; left: 0; bottom: -2px;
      width: 0; height: 1px;
      background: var(--gold);
      transition: width .3s ease;
    }
    .nav-links a:hover { color: var(--ink); }
    .nav-links a:hover::after { width: 100%; }

    /* ── Hero ── */
    #hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      padding-top: 80px;
      overflow: hidden;
    }
    .hero-left {
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      padding: 7rem 4rem 6rem 3rem;
      border-right: 1px solid var(--rule);
    }
    .hero-eyebrow {
      font-family: var(--sans);
      font-size: .72rem;
      letter-spacing: .18em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.8rem;
      opacity: 0;
      animation: fadeUp .7s .1s forwards;
    }
    .hero-name {
      font-family: var(--serif);
      font-size: clamp(3.5rem, 6vw, 6rem);
      font-weight: 300;
      line-height: 1.05;
      letter-spacing: -.01em;
      opacity: 0;
      animation: fadeUp .7s .25s forwards;
    }
    .hero-name em {
      font-style: italic;
      color: var(--gold);
    }
    .hero-tagline {
      font-family: var(--serif);
      font-size: 1.2rem;
      font-weight: 300;
      font-style: italic;
      color: var(--muted);
      margin-top: 2rem;
      max-width: 360px;
      opacity: 0;
      animation: fadeUp .7s .4s forwards;
    }
    .hero-actions {
      display: flex; gap: 1rem; margin-top: 3rem;
      opacity: 0; animation: fadeUp .7s .55s forwards;
    }
    .btn {
      display: inline-block;
      padding: .7rem 1.8rem;
      font-family: var(--sans);
      font-size: .78rem;
      font-weight: 500;
      letter-spacing: .1em;
      text-transform: uppercase;
      text-decoration: none;
      border: 1px solid var(--ink);
      color: var(--ink);
      transition: background .25s, color .25s;
    }
    .btn:hover { background: var(--ink); color: var(--paper); }
    .btn-gold { border-color: var(--gold); color: var(--gold); }
    .btn-gold:hover { background: var(--gold); color: var(--paper); }

    .hero-right {
      position: relative;
      background: var(--cream);
      overflow: hidden;
      display: flex; align-items: flex-end; justify-content: flex-end;
      padding: 3rem;
    }
    .hero-right-bg {
      position: absolute; inset: 0;
      background:
        radial-gradient(ellipse at 70% 30%, rgba(181,128,42,.12) 0%, transparent 60%),
        radial-gradient(ellipse at 20% 80%, rgba(26,22,18,.06) 0%, transparent 50%);
    }
    .hero-pull {
      position: relative;
      font-family: var(--serif);
      font-size: clamp(1.8rem, 3vw, 2.8rem);
      font-weight: 300;
      font-style: italic;
      line-height: 1.3;
      color: var(--ink);
      max-width: 320px;
      text-align: right;
      opacity: 0;
      animation: fadeUp .9s .6s forwards;
    }
    .hero-pull::before {
      content: '\201C';
      font-size: 6rem;
      line-height: 0;
      vertical-align: -.4em;
      color: var(--gold);
      opacity: .5;
      margin-right: .1em;
    }
    .hero-counter {
      position: absolute; top: 3rem; left: 3rem;
      display: flex; flex-direction: column; gap: 2rem;
      opacity: 0; animation: fadeIn 1s .8s forwards;
    }
    .counter-item { text-align: left; }
    .counter-num {
      font-family: var(--serif);
      font-size: 2.6rem;
      font-weight: 300;
      color: var(--gold);
      line-height: 1;
    }
    .counter-label {
      font-size: .7rem;
      letter-spacing: .1em;
      text-transform: uppercase;
      color: var(--muted);
    }

    /* ── Section shell ── */
    section { padding: 7rem 3rem; }
    section:nth-child(even) { background: var(--cream); }
    .section-header {
      display: grid;
      grid-template-columns: auto 1fr;
      gap: 2rem;
      align-items: baseline;
      margin-bottom: 4rem;
    }
    .section-number {
      font-family: var(--serif);
      font-size: 4.5rem;
      font-weight: 300;
      color: var(--gold);
      opacity: .35;
      line-height: 1;
    }
    .section-title-block h2 {
      font-family: var(--serif);
      font-size: clamp(2rem, 3.5vw, 3rem);
      font-weight: 300;
      line-height: 1.1;
    }
    .section-title-block p {
      font-size: .8rem;
      letter-spacing: .1em;
      text-transform: uppercase;
      color: var(--muted);
      margin-top: .4rem;
    }

    /* ── Publications ── */
    .publications-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 2px;
    }
    .pub-card {
      background: var(--paper);
      padding: 2.2rem;
      border-left: 2px solid transparent;
      transition: border-color .2s, background .2s;
      text-decoration: none;
      color: inherit;
      display: block;
    }
    section:nth-child(even) .pub-card { background: var(--paper); }
    .pub-card:hover { border-left-color: var(--gold); }
    .pub-year {
      font-size: .7rem;
      letter-spacing: .12em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: .7rem;
    }
    .pub-title {
      font-family: var(--serif);
      font-size: 1.25rem;
      font-weight: 600;
      line-height: 1.35;
      margin-bottom: .5rem;
    }
    .pub-venue {
      font-family: var(--serif);
      font-size: .95rem;
      font-style: italic;
      color: var(--muted);
      margin-bottom: .8rem;
    }
    .pub-desc {
      font-size: .82rem;
      color: var(--muted);
      line-height: 1.6;
    }
    .pub-arrow {
      display: inline-block;
      margin-top: 1.2rem;
      font-size: .72rem;
      letter-spacing: .1em;
      text-transform: uppercase;
      color: var(--gold);
      transition: letter-spacing .2s;
    }
    .pub-card:hover .pub-arrow { letter-spacing: .18em; }

    /* ── TV Appearances ── */
    .tv-list { display: flex; flex-direction: column; gap: 0; }
    .tv-item {
      display: grid;
      grid-template-columns: 120px 1fr auto;
      gap: 2rem;
      align-items: center;
      padding: 1.8rem 0;
      border-bottom: 1px solid var(--rule);
      text-decoration: none;
      color: inherit;
      transition: padding-left .2s;
    }
    .tv-item:first-child { border-top: 1px solid var(--rule); }
    .tv-item:hover { padding-left: .8rem; }
    .tv-date {
      font-size: .72rem;
      letter-spacing: .1em;
      text-transform: uppercase;
      color: var(--muted);
    }
    .tv-body {}
    .tv-show {
      font-family: var(--serif);
      font-size: 1.2rem;
      font-weight: 600;
    }
    .tv-topic {
      font-family: var(--serif);
      font-style: italic;
      font-size: .95rem;
      color: var(--muted);
    }
    .tv-channel {
      font-size: .72rem;
      letter-spacing: .08em;
      text-transform: uppercase;
      color: var(--gold);
      white-space: nowrap;
    }

    /* ── CV ── */
    .cv-cols {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 5rem;
    }
    .cv-section-title {
      font-size: .72rem;
      letter-spacing: .15em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.8rem;
      padding-bottom: .6rem;
      border-bottom: 1px solid var(--gold);
      display: inline-block;
    }
    .cv-entry { margin-bottom: 2rem; }
    .cv-entry-head {
      display: flex; justify-content: space-between; align-items: baseline;
      margin-bottom: .25rem;
    }
    .cv-role {
      font-family: var(--serif);
      font-size: 1.05rem;
      font-weight: 600;
    }
    .cv-period {
      font-size: .72rem;
      color: var(--muted);
      letter-spacing: .06em;
      white-space: nowrap;
      margin-left: 1rem;
    }
    .cv-org {
      font-family: var(--serif);
      font-style: italic;
      font-size: .9rem;
      color: var(--muted);
    }
    .cv-detail {
      font-size: .82rem;
      color: var(--muted);
      margin-top: .3rem;
    }
    .cv-download {
      margin-top: 3.5rem;
      display: flex; align-items: center; gap: 1rem;
    }

    /* ── Contact / Footer ── */
    footer {
      background: var(--ink);
      color: var(--paper);
      padding: 5rem 3rem 3rem;
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
      gap: 3rem;
    }
    .footer-brand {
      font-family: var(--serif);
      font-size: 2rem;
      font-weight: 300;
    }
    .footer-tagline {
      font-family: var(--serif);
      font-style: italic;
      font-size: .9rem;
      color: rgba(245,240,232,.45);
      margin-top: .5rem;
    }
    .footer-heading {
      font-size: .65rem;
      letter-spacing: .18em;
      text-transform: uppercase;
      color: var(--gold);
      margin-bottom: 1.2rem;
    }
    .footer-links { list-style: none; }
    .footer-links li { margin-bottom: .5rem; }
    .footer-links a {
      color: rgba(245,240,232,.65);
      text-decoration: none;
      font-size: .85rem;
      transition: color .2s;
    }
    .footer-links a:hover { color: var(--gold); }
    .footer-copy {
      grid-column: 1/-1;
      border-top: 1px solid rgba(245,240,232,.1);
      padding-top: 2rem;
      font-size: .72rem;
      color: rgba(245,240,232,.3);
      letter-spacing: .06em;
      display: flex; justify-content: space-between;
    }

    /* ── Animations ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(22px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    @keyframes fadeIn {
      from { opacity: 0; } to { opacity: 1; }
    }

    /* Scroll-triggered reveal */
    .reveal {
      opacity: 0;
      transform: translateY(28px);
      transition: opacity .65s ease, transform .65s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: none;
    }

    /* ── Responsive ── */
    @media (max-width: 860px) {
      nav { padding: 1.2rem 1.5rem; }
      .nav-links { gap: 1.5rem; }
      #hero { grid-template-columns: 1fr; min-height: auto; }
      .hero-left { padding: 5rem 1.5rem 3rem; border-right: none; border-bottom: 1px solid var(--rule); }
      .hero-right { min-height: 280px; }
      section { padding: 5rem 1.5rem; }
      .cv-cols { grid-template-columns: 1fr; gap: 3rem; }
      footer { grid-template-columns: 1fr; }
      .footer-copy { flex-direction: column; gap: .5rem; }
      .tv-item { grid-template-columns: 80px 1fr; }
      .tv-channel { display: none; }
    }
  </style>
</head>
<body>

<!-- Custom cursor -->
<div class="cursor" id="cursor"></div>

<!-- Navigation -->
<nav id="navbar">
  <a href="polish.html" class="nav-logo">Zmień język na polski</a>
  <ul class="nav-links">
    <li><a href="about.html">About</a></li>
    <li><a href="writing.html">Writing</a></li>
    <li><a href="media.html">Media</a></li>
    <li><a href="cv.html">CV</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
</nav>

<!-- Hero -->
<section id="hero">
  <div class="hero-left">
    <p class="hero-eyebrow">Writer · Scholar · Broadcaster</p>
    <h1 class="hero-name">Bartek Staniszewski</h1>
    <p class="hero-tagline">Politics, philosophy, influence</p>
    <div class="hero-actions">
      <a href="#publications" class="btn btn-gold">Read my work</a>
      <a href="#cv" class="btn">View CV</a>
    </div>
  </div>
  <div class="hero-right">
    <div class="hero-right-bg"></div>
    <div class="hero-counter">
      <div class="counter-item">
        <div class="counter-num">12</div>
        <div class="counter-label">Publications</div>
      </div>
      <div class="counter-item">
        <div class="counter-num">34</div>
        <div class="counter-label">TV Appearances</div>
      </div>
      <div class="counter-item">
        <div class="counter-num">15+</div>
        <div class="counter-label">Years Active</div>
      </div>
    </div>
    <p class="hero-pull">Ideas worth fighting for, arguments worth making.</p>
  </div>
</section>

<!-- Publications -->
<section id="publications">
  <div class="section-header reveal">
    <div class="section-number">01</div>
    <div class="section-title-block">
      <h2>Publications</h2>
      <p>Books, essays & academic papers</p>
    </div>
  </div>

  <div class="publications-grid">
    <a href="#" class="pub-card reveal">
      <div class="pub-year">2024</div>
      <div class="pub-title">The Unfinished Century: Europe After the Wars</div>
      <div class="pub-venue">Allen Lane / Penguin Press</div>
      <div class="pub-desc">A reappraisal of twentieth-century European history and what it means for the crises of today.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="#" class="pub-card reveal">
      <div class="pub-year">2022</div>
      <div class="pub-title">Borderlands: A Journey Through Forgotten Europe</div>
      <div class="pub-venue">Faber & Faber</div>
      <div class="pub-desc">Longlisted for the Baillie Gifford Prize. A reportage across the margins of the continent.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="#" class="pub-card reveal">
      <div class="pub-year">2020</div>
      <div class="pub-title">The Memory of Nations</div>
      <div class="pub-venue">Yale University Press</div>
      <div class="pub-desc">How societies remember — and misremember — collective trauma. Winner of the Historians' Book Prize.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="#" class="pub-card reveal">
      <div class="pub-year">2019</div>
      <div class="pub-title">After the Fall — Essay Collection</div>
      <div class="pub-venue">The Guardian / New York Review of Books</div>
      <div class="pub-desc">A selection of long-form essays on politics, culture, and historical memory published across major outlets.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="#" class="pub-card reveal">
      <div class="pub-year">2017</div>
      <div class="pub-title">Ghosts of the Republic</div>
      <div class="pub-venue">Oxford University Press</div>
      <div class="pub-desc">Academic monograph on the contested legacies of interwar Central European states.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="#" class="pub-card reveal">
      <div class="pub-year">2015</div>
      <div class="pub-title">Writing the Present: Dispatches from a Correspondent</div>
      <div class="pub-venue">Granta Books</div>
      <div class="pub-desc">Journalism and memoir from two decades of reporting from conflict zones and post-communist transitions.</div>
      <span class="pub-arrow">Read more →</span>
    </a>
  </div>
</section>

<!-- TV Appearances -->
<section id="tv">
  <div class="section-header reveal">
    <div class="section-number">02</div>
    <div class="section-title-block">
      <h2>Television & Media</h2>
      <p>Appearances, panels & documentary work</p>
    </div>
  </div>

  <div class="tv-list">
    <a href="#" class="tv-item reveal">
      <div class="tv-date">Mar 2025</div>
      <div class="tv-body">
        <div class="tv-show">Newsnight</div>
        <div class="tv-topic">On the European security situation and NATO's eastern flank</div>
      </div>
      <div class="tv-channel">BBC Two</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">Jan 2025</div>
      <div class="tv-body">
        <div class="tv-show">The Andrew Marr Show</div>
        <div class="tv-topic">Discussion of The Unfinished Century and its contemporary relevance</div>
      </div>
      <div class="tv-channel">LBC / Global</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">Sep 2024</div>
      <div class="tv-body">
        <div class="tv-show">Channel 4 News</div>
        <div class="tv-topic">Live analysis: European Parliament elections and far-right surge</div>
      </div>
      <div class="tv-channel">Channel 4</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">Jun 2024</div>
      <div class="tv-body">
        <div class="tv-show">Hardtalk</div>
        <div class="tv-topic">In conversation on memory, identity, and the war in Ukraine</div>
      </div>
      <div class="tv-channel">BBC World</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">2023</div>
      <div class="tv-body">
        <div class="tv-show">Borderlands — Documentary Series</div>
        <div class="tv-topic">Writer and presenter of four-part original series based on the book</div>
      </div>
      <div class="tv-channel">BBC Four</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">2022</div>
      <div class="tv-body">
        <div class="tv-show">Question Time</div>
        <div class="tv-topic">Panel member — three appearances across the year</div>
      </div>
      <div class="tv-channel">BBC One</div>
    </a>
    <a href="#" class="tv-item reveal">
      <div class="tv-date">2021</div>
      <div class="tv-body">
        <div class="tv-show">Start the Week</div>
        <div class="tv-topic">The Memory of Nations discussed alongside Timothy Garton Ash and Anne Applebaum</div>
      </div>
      <div class="tv-channel">BBC Radio 4</div>
    </a>
  </div>
</section>

<!-- CV -->
<section id="cv">
  <div class="section-header reveal">
    <div class="section-number">03</div>
    <div class="section-title-block">
      <h2>Curriculum Vitae</h2>
      <p>Positions, education & selected honours</p>
    </div>
  </div>

  <div class="cv-cols">
    <div>
      <div class="cv-section-title reveal">Academic & Professional</div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">Professor of Modern History</div>
          <div class="cv-period">2018–present</div>
        </div>
        <div class="cv-org">University College London</div>
        <div class="cv-detail">Chair of Twentieth-Century European Studies. Director of the Centre for Memory Studies.</div>
      </div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">Contributing Editor</div>
          <div class="cv-period">2015–present</div>
        </div>
        <div class="cv-org">The Guardian, Long Reads</div>
        <div class="cv-detail">Quarterly longform essay and reportage on history, politics and culture.</div>
      </div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">Senior Research Fellow</div>
          <div class="cv-period">2013–2018</div>
        </div>
        <div class="cv-org">St Antony's College, Oxford</div>
      </div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">Foreign Correspondent</div>
          <div class="cv-period">2005–2013</div>
        </div>
        <div class="cv-org">The Times / The Economist</div>
        <div class="cv-detail">Eastern and Central Europe desk. Based in Warsaw, Prague, and Kyiv.</div>
      </div>
    </div>

    <div>
      <div class="cv-section-title reveal">Education & Honours</div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">D.Phil, Modern History</div>
          <div class="cv-period">2005</div>
        </div>
        <div class="cv-org">University of Oxford</div>
        <div class="cv-detail">Thesis: <em>"Nation, Myth and Memory in Interwar Poland"</em>. Supervisors: Prof. T. Judt, Prof. J. Gross.</div>
      </div>

      <div class="cv-entry reveal">
        <div class="cv-entry-head">
          <div class="cv-role">BA (Hons), History, First Class</div>
          <div class="cv-period">2001</div>
        </div>
        <div class="cv-org">Cambridge University</div>
      </div>

      <div class="cv-section-title reveal" style="margin-top:2.5rem">Awards</div>

      <div class="cv-entry reveal">
        <div class="cv-role">Historians' Book Prize</div>
        <div class="cv-org" style="margin-top:.2rem">For <em>The Memory of Nations</em>, 2021</div>
      </div>
      <div class="cv-entry reveal">
        <div class="cv-role">Baillie Gifford Prize Longlist</div>
        <div class="cv-org" style="margin-top:.2rem">For <em>Borderlands</em>, 2022</div>
      </div>
      <div class="cv-entry reveal">
        <div class="cv-role">RTS Television Journalism Award</div>
        <div class="cv-org" style="margin-top:.2rem">Borderlands documentary series, 2023</div>
      </div>

      <div class="cv-download reveal">
        <a href="#" class="btn btn-gold">Download Full CV (PDF)</a>
      </div>
    </div>
  </div>
</section>

<!-- Footer / Contact -->
<footer id="contact">
  <div>
    <div class="footer-brand">Your Name</div>
    <div class="footer-tagline">Writer, Scholar & Broadcaster</div>
  </div>
  <div>
    <div class="footer-heading">Navigate</div>
    <ul class="footer-links">
      <li><a href="#publications">Publications</a></li>
      <li><a href="#tv">Television</a></li>
      <li><a href="#cv">CV &amp; Biography</a></li>
    </ul>
  </div>
  <div>
    <div class="footer-heading">Get in Touch</div>
    <ul class="footer-links">
      <li><a href="mailto:hello@yourname.com">hello@yourname.com</a></li>
      <li><a href="#">Media enquiries</a></li>
      <li><a href="#">Speaking requests</a></li>
      <li><a href="#">Twitter / X</a></li>
    </ul>
  </div>
  <div class="footer-copy">
    <span>© 2025 Your Name. All rights reserved.</span>
    <span>Design: editorial / typographic</span>
  </div>
</footer>

<script>
  // Cursor
  const cursor = document.getElementById('cursor');
  document.addEventListener('mousemove', e => {
    cursor.style.left = e.clientX + 'px';
    cursor.style.top  = e.clientY + 'px';
  });
  document.querySelectorAll('a, button').forEach(el => {
    el.addEventListener('mouseenter', () => {
      cursor.style.width = '20px';
      cursor.style.height = '20px';
    });
    el.addEventListener('mouseleave', () => {
      cursor.style.width = '10px';
      cursor.style.height = '10px';
    });
  });

  // Navbar on scroll
  const navbar = document.getElementById('navbar');
  window.addEventListener('scroll', () => {
    navbar.classList.toggle('scrolled', window.scrollY > 40);
  });

  // Scroll-triggered reveals
  const revealEls = document.querySelectorAll('.reveal');
  const observer = new IntersectionObserver(entries => {
    entries.forEach((entry, i) => {
      if (entry.isIntersecting) {
        // stagger siblings
        const siblings = [...entry.target.parentElement.querySelectorAll('.reveal:not(.visible)')];
        const idx = siblings.indexOf(entry.target);
        setTimeout(() => {
          entry.target.classList.add('visible');
        }, Math.min(idx * 80, 400));
        observer.unobserve(entry.target);
      }
    });
  }, { threshold: 0.12 });
  revealEls.forEach(el => observer.observe(el));
</script>
</body>
</html>
