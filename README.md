<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Bartek Staniszewski</title>
  <link rel="shortcut icon" type="image/x-icon" href="favicon.ico">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/lipis/flag-icons@7.3.2/css/flag-icons.min.css" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Karla:wght@300;400;500&display=swap" rel="stylesheet">

  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --ink:    #1a1612;
      --paper:  #f5f0e8;
      --cream:  #ede7d9;
      --green:  #152913;
      --gold:   #b5802a;      --muted:  #7a7060;
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

    /* Hide custom cursor on touch devices */
    @media (hover: none) {
      body { cursor: auto; }
      .cursor { display: none; }
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
    .nav-links { display: flex; gap: 2.4rem; list-style: none; align-items: center; }
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

    /* ── Hamburger toggle ── */
    .nav-toggle {
      display: none;
      flex-direction: column;
      justify-content: center;
      gap: 5px;
      background: none;
      border: none;
      cursor: pointer;
      padding: 4px;
      z-index: 110;
    }
    .nav-toggle span {
      display: block;
      width: 22px;
      height: 2px;
      background: var(--ink);
      transition: transform .3s ease, opacity .3s ease;
    }
    .nav-toggle.open span:nth-child(1) { transform: translateY(7px) rotate(45deg); }
    .nav-toggle.open span:nth-child(2) { opacity: 0; }
    .nav-toggle.open span:nth-child(3) { transform: translateY(-7px) rotate(-45deg); }
    
    /* ── Hero ── */
    #hero {
min-height: auto; 
  display: grid;
  grid-template-columns: 1fr 1fr;
  padding-top: 80px;
  overflow: hidden;
  align-items: start; 
}
.hero-left {
  display: flex;
  flex-direction: column;
  justify-content: flex-start; 
  padding: 3rem 4rem 6rem 3rem; 
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
  display: flex;
  gap: 1rem;
  padding: 1.5rem;      /* space around the buttons */
  opacity: 0;
  animation: fadeUp .7s .55s forwards;
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
  background: var(--paper);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: flex-start;
  padding: 0; /* remove padding so image goes edge-to-edge */
}

.hero-right img {
  width: 100%;
  height: 550px;        /* or whatever height you want */
  object-fit: cover;
  object-position: center top;
  display: block;
  outline: 5px solid var(--green); /* Your golden border */
  outline-offset: -5px;           /* Pulls the border inside the image */
}
     .hero-name {
      position: absolute;
      bottom: 2rem;
      left: 2rem;
      z-index: 1;
      font-family: var(--serif);
      font-size: clamp(1.8rem, 2.5vw, 2.6rem);
      font-weight: 300;
      color: #fff;
      text-shadow: 0 2px 16px rgba(0,0,0,.55);
      opacity: 0;
      animation: fadeUp .7s .4s forwards;
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
    .hero-image-wrap {
  position: relative;
  width: 100%;
}

.hero-image-wrap img {
  width: 100%;
  height: 500px;
  object-fit: cover;
  object-position: center top;
  display: block;
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
      background: var(--green);
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
     /* Hamburger: show toggle, collapse links into dropdown */
      .nav-toggle { display: flex; }
      .nav-links {
        display: none;
        position: absolute;
        top: 100%; left: 0; right: 0;
        flex-direction: column;
        gap: 0;
        background: var(--paper);
        border-bottom: 1px solid var(--rule);
        box-shadow: 0 4px 20px rgba(0,0,0,.07);
        padding: .5rem 1.5rem 1.5rem;
      }
      .nav-links.open { display: flex; }
      .nav-links li { border-bottom: 1px solid var(--rule); }
      .nav-links li:last-child { border-bottom: none; }
      .nav-links a {
        display: block;
        padding: .75rem 0;
        font-size: .85rem;
      }


      
      #hero { grid-template-columns: 1fr; min-height: auto; }
      .hero-left { padding: 5rem 1.5rem 3rem; border-right: none; border-bottom: 1px solid var(--rule); }     /* Fix hero image: give the wrapper an explicit height so the absolutely-positioned img has something to fill */
      .hero-right {
        position: relative;
        overflow: hidden;
        min-height: unset;
      }
      .hero-image-wrap {
        height: 420px;
      }
      .hero-right img {
        position: absolute;
        inset: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        object-position: center top;
        display: block;
      }

      section { padding: 5rem 1.5rem; }
      .cv-cols { grid-template-columns: 1fr; gap: 3rem; }
      footer { grid-template-columns: 1fr; padding: 3rem 1.5rem 2rem; }
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
  <a href="polish.html" class="nav-logo"> Zmień język na polski <span class="fi fi-pl"></span></a>
  <ul class="nav-links" id="nav-links">
    <li><a href="#"> </a></li>
    <li><a href="https://www.staniszewski.biz/">About</a></li>
    <li><a href="writing.html">Writing</a></li>
    <li><a href="media.html">Media</a></li>
    <li><a href="cv.html">CV</a></li>
    <li><a href="contact.html">Contact</a></li>
  </ul>
  <button class="nav-toggle" id="nav-toggle" aria-label="Toggle menu">
    <span></span><span></span><span></span>
  </button>
</nav>

<!-- Hero -->
<section id="hero">
  <div class="hero-left">
    <p class="hero-eyebrow"><a href="https://www.linkedin.com/in/bastaniszewski/"><i class="fa-brands fa-linkedin"></i> LinkedIn</a> · <a href="https://x.com/BGStaniszewski"><i class="fa-brands fa-square-twitter"></i> Twitter</a> · <a href="mailto:bastaniszewski@gmail.com"><i class="fa-solid fa-square-envelope"></i> Email</a></p>
   
    <p>I am a political analyst and strategist with four years of experience working in the heart of Westminster. Currently based between Warsaw and London, I am the co-Founder of Bright Blue Europe and former Head of Research at Bright Blue in the UK.<br><br>
    
    In my time advising politicians and public affairs, I authored nine research reports, published over fifty articles in twelve different publications, including <i>the Spectator</i> and <i>the Critic</i>, and hired seven full-time employees. Under my leadership, the research team at Bright Blue  published sixteen analyses and had around thirty of its policy recommendations adopted by either the UK Government or major UK political parties. Our work has been featured, among others, on the BBC, GB News, LBC, and Vatican News. <br> <br>I am also the Editor-in-Chief of Centre Write and a political adviser to several political campaigns.<br><br>I am primarily interested in social policy, political philosophy, and political strategy. Before working in politics, I read for a Master's in Philosophical Theology at the University of Oxford. You can find my work on those topics on this website.</p>

  </div>
 <div class="hero-right">
  <div class="hero-image-wrap">
    <img src="https://i.imgur.com/VsjPWfd.png"/>
    <h1 class="hero-name">Bartek Staniszewski</h1>
  </div>
  <div class="hero-actions">
    <a href="https://www.staniszewski.biz/writing.html" class="btn btn-gold">Read my work</a>
    <a href="https://www.staniszewski.biz/cv.html" class="btn">View my CV</a>
  </div>
</div>
</section>

<!-- Publications -->
<section id="publications">
  <div class="section-header reveal">
    <div class="section-number">Select recent work</div>
    <div class="section-title-block">
      <h2></h2>
      <p>Reports, articles and talks</p>
    </div>
  </div>

  <div class="publications-grid">
    <a href="https://www.brightblue.org.uk/wp-content/uploads/2025/10/BB-Essay-Collection-August-2025_PRF04.pdf" class="pub-card reveal">
      <div class="pub-year">2025</div>
      <div class="pub-title">Mending the net? A new centre-right approach to social security</div>
      <div class="pub-venue">Bright Blue</div>
      <div class="pub-desc">I edited and wrote the introduction to this collection of essays on reforming social security in the UK. Featuring also contributions from Danny Kruger, Henry Hill, David Goodhart, John Glen, and others.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="https://centrewrite.brightblue.org.uk/interview-with-mel-stride/" class="pub-card reveal">
      <div class="pub-year">2025</div>
      <div class="pub-title">Interview with Mel Stride</div>
      <div class="pub-venue">Centre Write</div>
      <div class="pub-desc">I interviewed the Rt Hon Mel Stride MP, the Shadow Chancellor of the Exchquer, for the launch of the Centre Write magazine.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="https://www.brightblue.org.uk/portfolio/right-road/" class="pub-card reveal">
      <div class="pub-year">2025</div>
      <div class="pub-title">The right road: The future of the European centre-right</div>
      <div class="pub-venue">Bright Blue</div>
      <div class="pub-desc">I wrote most of the chapters in this book about the past and future of the European centre-right.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="https://spectator.com/article/its-time-to-tackle-britains-health-and-safety-obsession/" class="pub-card reveal">
      <div class="pub-year">2025</div>
      <div class="pub-title">Red tape has broken Britain</div>
      <div class="pub-venue">The Spectator</div>
      <div class="pub-desc">An article on a true cause behind the collapse of the social contract in the UK.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="https://spectator.com/article/autists-are-the-answer-to-britains-worklessness-crisis/" class="pub-card reveal">
      <div class="pub-year">2025</div>
      <div class="pub-title">Autists are the answer to Britain’s worklessness crisis</div>
      <div class="pub-venue">The Spectator</div>
      <div class="pub-desc">An article on the interaction between the UK's autistic population and the benefit claimant system.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

    <a href="https://thecritic.co.uk/not-everyone-should-be-in-therapy/" class="pub-card reveal">
      <div class="pub-year">2024</div>
      <div class="pub-title">Not everyone should be in therapy</div>
      <div class="pub-venue">The Critic</div>
      <div class="pub-desc">An article on the prevalence of and problems with therapy culture.</div>
      <span class="pub-arrow">Read more →</span>
    </a>

  </div>
</section>

<!-- Footer / Contact -->
<footer id="contact">
  <div>
    <div class="footer-brand">Bartek Staniszewski</div>
    <div class="footer-tagline">Political advisory, analysis & strategy</div>
  </div>
  <div>
    <div class="footer-heading">Navigate</div>
    <ul class="footer-links">
      <li><a href="writing.html">Publications</a></li>
      <li><a href="media.html">Media</a></li>
      <li><a href="cv.html">CV</a></li>
      <li><a href="contact.html">Contact</a></li>
    </ul>
  </div>
  <div>
    <div class="footer-heading">Other links</div>
    <ul class="footer-links">
      <li><a href="https://www.eubrightblue.org/">Bright Blue Europe</a></li>
      <li><a href="https://www.brightblue.org.uk/portfolio/bartek-staniszewski/">Bright Blue UK</a></li>
      <li><a href="https://www.linkedin.com/in/bastaniszewski/">LinkedIn</a></li>
      <li><a href="https://x.com/BGStaniszewski">Twitter / X</a></li>
    </ul>
  </div>
  <div class="footer-copy">
    <span>Created and  designed in 2026 by Bartlomiej Staniszewski.</span>
  </div>
</footer>

<script>
    // Hamburger menu toggle
  const navToggle = document.getElementById('nav-toggle');
  const navLinks  = document.getElementById('nav-links');
  navToggle.addEventListener('click', () => {
    navToggle.classList.toggle('open');
    navLinks.classList.toggle('open');
  });
  // Close menu when a link is tapped
  navLinks.querySelectorAll('a').forEach(a => {
    a.addEventListener('click', () => {
      navToggle.classList.remove('open');
      navLinks.classList.remove('open');
    });
  });


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
