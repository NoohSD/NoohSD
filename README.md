<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nooh Suliman — Odoo Techno-Functional Consultant</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,500;9..144,600&family=Space+Grotesk:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg:#1C1420;
    --bg-raised:#241A29;
    --ink:#F3ECE4;
    --ink-dim:#B9AEB8;
    --coral:#FF6B4A;
    --coral-dim:#7A3626;
    --gold:#E8B94F;
    --line:rgba(243,236,228,0.12);
    --max:1080px;
  }
  *{box-sizing:border-box; margin:0; padding:0;}
  html{scroll-behavior:smooth;}
  body{
    background:var(--bg);
    color:var(--ink);
    font-family:'Space Grotesk', sans-serif;
    overflow-x:hidden;
    cursor:none;
  }
  ::selection{background:var(--coral); color:#1C1420;}
  h1,h2,h3{font-family:'Fraunces', serif; font-weight:600; line-height:1.1;}
  .mono{font-family:'JetBrains Mono', monospace;}
  a{color:inherit; text-decoration:none;}
  section{max-width:var(--max); margin:0 auto; padding:140px 32px;}

  /* ---------- custom cursor ---------- */
  #cursor{
    position:fixed; width:22px; height:22px; border-radius:50%;
    border:1.5px solid var(--coral); pointer-events:none; z-index:9999;
    transform:translate(-50%,-50%); transition:width .18s, height .18s, background .18s, border-color .18s;
    mix-blend-mode:difference;
  }
  #cursor.hover{width:52px; height:52px; background:var(--coral); border-color:transparent;}
  #glow{
    position:fixed; width:520px; height:520px; border-radius:50%;
    pointer-events:none; z-index:0; transform:translate(-50%,-50%);
    background:radial-gradient(circle, rgba(255,107,74,0.10) 0%, rgba(255,107,74,0) 70%);
  }
  @media (hover:none){ #cursor,#glow{display:none;} body{cursor:auto;} }

  /* ---------- nav ---------- */
  nav{
    position:fixed; top:0; left:0; right:0; z-index:100;
    display:flex; justify-content:space-between; align-items:center;
    padding:22px 40px; backdrop-filter:blur(10px);
    background:rgba(28,20,32,0.55); border-bottom:1px solid var(--line);
  }
  .logo{font-family:'Fraunces', serif; font-weight:600; font-size:1.15rem;}
  .logo span{color:var(--coral);}
  .navlinks{display:flex; gap:34px; font-size:0.86rem;}
  .navlinks a{color:var(--ink-dim); position:relative; padding-bottom:4px;}
  .navlinks a::after{
    content:''; position:absolute; left:0; bottom:0; width:0; height:1px;
    background:var(--coral); transition:width .25s ease;
  }
  .navlinks a.active, .navlinks a:hover{color:var(--ink);}
  .navlinks a.active::after, .navlinks a:hover::after{width:100%;}
  #navToggle{display:none;}

  /* ---------- hero ---------- */
  #hero{
    min-height:100vh; display:flex; flex-direction:column; justify-content:center;
    position:relative; padding-top:140px;
  }
  .eyebrow{
    font-family:'JetBrains Mono', monospace; font-size:0.8rem; color:var(--gold);
    letter-spacing:.06em; display:flex; align-items:center; gap:10px; margin-bottom:22px;
  }
  .eyebrow .dot{width:7px; height:7px; border-radius:50%; background:var(--gold); animation:pulse 1.8s infinite;}
  @keyframes pulse{0%,100%{opacity:1;} 50%{opacity:.25;}}

  .hero-title{font-size:clamp(2.6rem, 6vw, 4.6rem); max-width:16ch;}
  .hero-title .accent{color:var(--coral); font-style:italic;}
  .hero-sub{margin-top:26px; max-width:56ch; color:var(--ink-dim); font-size:1.1rem;}

  .hero-cta{margin-top:44px; display:flex; gap:18px; flex-wrap:wrap;}
  .btn{
    font-family:'Space Grotesk', sans-serif; font-weight:600; font-size:0.92rem;
    padding:15px 30px; border-radius:100px; border:1px solid var(--line);
    display:inline-flex; align-items:center; gap:10px; transition:all .25s ease;
  }
  .btn-solid{background:var(--coral); color:#1C1420; border-color:var(--coral);}
  .btn-solid:hover{background:var(--gold); border-color:var(--gold); transform:translateY(-2px);}
  .btn-ghost:hover{border-color:var(--ink); transform:translateY(-2px);}

  .scroll-cue{
    position:absolute; bottom:40px; left:32px; font-family:'JetBrains Mono', monospace;
    font-size:0.72rem; color:var(--ink-dim); display:flex; align-items:center; gap:10px;
  }
  .scroll-cue .line{width:34px; height:1px; background:var(--ink-dim); animation:scrollline 1.6s infinite;}
  @keyframes scrollline{0%{transform:scaleX(0); transform-origin:left;} 50%{transform:scaleX(1); transform-origin:left;} 51%{transform-origin:right;} 100%{transform:scaleX(0); transform-origin:right;}}

  /* ---------- reveal ---------- */
  .reveal{opacity:0; transform:translateY(28px); transition:opacity .7s ease, transform .7s ease;}
  .reveal.in{opacity:1; transform:none;}

  /* ---------- section label ---------- */
  .label{
    font-family:'JetBrains Mono', monospace; font-size:0.78rem; color:var(--coral);
    margin-bottom:16px; display:flex; align-items:center; gap:12px;
  }
  .label::before{content:''; width:24px; height:1px; background:var(--coral);}
  .sec-title{font-size:clamp(1.8rem,3vw,2.6rem); margin-bottom:44px;}

  /* ---------- stats ---------- */
  .stats{
    display:grid; grid-template-columns:repeat(4,1fr); gap:1px;
    background:var(--line); border:1px solid var(--line); margin-top:64px;
  }
  .stat{background:var(--bg-raised); padding:32px 24px;}
  .stat .num{font-family:'Fraunces', serif; font-size:2.1rem; color:var(--coral);}
  .stat .lbl{margin-top:8px; font-size:0.82rem; color:var(--ink-dim);}

  /* ---------- about ---------- */
  .about-grid{display:grid; grid-template-columns:1.3fr 1fr; gap:64px; align-items:start;}
  .about-grid p{color:var(--ink-dim); margin-bottom:18px; font-size:1.02rem; line-height:1.75;}
  .timeline{border-left:1px solid var(--line); padding-left:24px; display:flex; flex-direction:column; gap:22px;}
  .tl-item{position:relative;}
  .tl-item::before{
    content:''; position:absolute; left:-29px; top:5px; width:9px; height:9px;
    border-radius:50%; background:var(--gold);
  }
  .tl-item .yr{font-family:'JetBrains Mono', monospace; font-size:0.76rem; color:var(--gold);}
  .tl-item .txt{font-size:0.92rem; color:var(--ink-dim); margin-top:4px;}

  /* ---------- skills ---------- */
  .skill-grid{display:grid; grid-template-columns:repeat(2, 1fr); gap:40px 60px;}
  .skill-row{margin-bottom:18px;}
  .skill-row:last-child{margin-bottom:0;}
  .skill-top{display:flex; justify-content:space-between; font-size:0.9rem; margin-bottom:8px;}
  .skill-top .pct{font-family:'JetBrains Mono', monospace; color:var(--coral);}
  .bar-track{height:6px; background:var(--line); border-radius:4px; overflow:hidden;}
  .bar-fill{height:100%; width:0%; background:linear-gradient(90deg,var(--coral),var(--gold)); border-radius:4px; transition:width 1.4s cubic-bezier(.2,.8,.2,1);}

  /* ---------- services ---------- */
  .service-grid{display:grid; grid-template-columns:repeat(3,1fr); gap:1px; background:var(--line); border:1px solid var(--line);}
  .service-card{
    background:var(--bg-raised); padding:34px 28px; transition:background .3s ease, transform .3s ease;
    position:relative; overflow:hidden;
  }
  .service-card::before{
    content:''; position:absolute; inset:0; background:radial-gradient(circle at var(--mx,50%) var(--my,50%), rgba(255,107,74,0.14), transparent 60%);
    opacity:0; transition:opacity .3s ease;
  }
  .service-card:hover::before{opacity:1;}
  .service-card .n{font-family:'JetBrains Mono', monospace; color:var(--gold); font-size:0.8rem;}
  .service-card h3{font-size:1.1rem; margin-top:14px; margin-bottom:12px;}
  .service-card p{font-size:0.88rem; color:var(--ink-dim); position:relative; z-index:1;}

  /* ---------- projects ---------- */
  .project-list{display:flex; flex-direction:column;}
  .project{
    display:grid; grid-template-columns:120px 1fr auto; gap:24px; align-items:center;
    padding:28px 4px; border-top:1px solid var(--line); cursor:pointer; transition:padding-left .3s ease;
  }
  .project:last-child{border-bottom:1px solid var(--line);}
  .project:hover{padding-left:16px;}
  .project .idx{font-family:'JetBrains Mono', monospace; color:var(--ink-dim); font-size:0.85rem;}
  .project h4{font-size:1.3rem; transition:color .3s ease;}
  .project:hover h4{color:var(--coral);}
  .project .tags{margin-top:6px; display:flex; gap:8px; flex-wrap:wrap;}
  .tag{font-family:'JetBrains Mono', monospace; font-size:0.68rem; padding:3px 9px; border:1px solid var(--line); border-radius:100px; color:var(--ink-dim);}
  .project .arrow{font-size:1.4rem; color:var(--ink-dim); transition:transform .3s ease, color .3s ease;}
  .project:hover .arrow{transform:translateX(6px); color:var(--coral);}
  .project-detail{
    max-height:0; overflow:hidden; transition:max-height .4s ease;
    grid-column:1/-1; font-size:0.9rem; color:var(--ink-dim); padding-left:144px;
  }
  .project.open .project-detail{max-height:120px; padding-top:10px;}

  /* ---------- education ---------- */
  .edu-grid{display:grid; grid-template-columns:repeat(2,1fr); gap:1px; background:var(--line); border:1px solid var(--line);}
  .edu-card{background:var(--bg-raised); padding:28px;}
  .edu-card .yr{font-family:'JetBrains Mono', monospace; font-size:0.76rem; color:var(--gold);}
  .edu-card h4{margin-top:10px; font-size:1rem; font-family:'Space Grotesk'; font-weight:600;}
  .edu-card p{margin-top:6px; font-size:0.85rem; color:var(--ink-dim);}

  /* ---------- contact ---------- */
  #contact{text-align:center;}
  #contact h2{font-size:clamp(2rem,5vw,3.4rem); max-width:16ch; margin:0 auto 24px;}
  #contact p{color:var(--ink-dim); max-width:50ch; margin:0 auto;}
  .big-link{
    display:inline-block; margin-top:44px; font-family:'Fraunces', serif; font-size:clamp(1.6rem,4vw,2.4rem);
    border-bottom:2px solid var(--coral); padding-bottom:6px; transition:color .3s ease;
  }
  .big-link:hover{color:var(--coral);}
  .contact-meta{margin-top:44px; display:flex; justify-content:center; gap:40px; flex-wrap:wrap; font-family:'JetBrains Mono', monospace; font-size:0.82rem; color:var(--ink-dim);}

  footer{
    border-top:1px solid var(--line); padding:32px; display:flex; justify-content:space-between;
    max-width:var(--max); margin:0 auto; font-size:0.78rem; color:var(--ink-dim); flex-wrap:wrap; gap:10px;
  }

  @media (max-width:860px){
    .navlinks{display:none;}
    .stats{grid-template-columns:repeat(2,1fr);}
    .about-grid{grid-template-columns:1fr;}
    .skill-grid{grid-template-columns:1fr;}
    .service-grid{grid-template-columns:1fr;}
    .edu-grid{grid-template-columns:1fr;}
    .project{grid-template-columns:50px 1fr auto;}
    .project-detail{padding-left:0;}
    section{padding:96px 20px;}
  }
</style>
</head>
<body>

<div id="cursor"></div>
<div id="glow"></div>

<nav>
  <div class="logo">Nooh<span>.</span></div>
  <div class="navlinks">
    <a href="#hero" data-nav>Home</a>
    <a href="#about" data-nav>About</a>
    <a href="#skills" data-nav>Skills</a>
    <a href="#services" data-nav>Services</a>
    <a href="#projects" data-nav>Work</a>
    <a href="#contact" data-nav>Contact</a>
  </div>
</nav>

<section id="hero">
  <div class="eyebrow"><span class="dot"></span>AVAILABLE FOR NEW ODOO PROJECTS</div>
  <h1 class="hero-title">Odoo systems, built to<br><span class="accent">actually</span> run the business.</h1>
  <p class="hero-sub">I'm Nooh Suliman — a Techno-Functional Consultant based in Al Khobar, Saudi Arabia. I lead ERP implementations end to end: requirements, configuration, ZATCA compliance, training, and the stuff that happens after Go-Live.</p>
  <div class="hero-cta">
    <a href="#projects" class="btn btn-solid" data-hover>See the work →</a>
    <a href="#contact" class="btn btn-ghost" data-hover>Get in touch</a>
  </div>
  <div class="scroll-cue"><div class="line"></div>SCROLL</div>
</section>

<section id="about">
  <div class="label">01 / OVERVIEW</div>
  <h2 class="sec-title reveal">Bridging business needs and technical systems</h2>
  <div class="about-grid">
    <div class="reveal">
      <p>With hands-on experience across manufacturing, medical, contracting, and service industries, I help businesses turn operational requirements into scalable Odoo solutions — spanning requirements gathering, gap analysis, configuration, integrations, training, and post-Go-Live support.</p>
      <p>My work has included full migrations across major versions, ZATCA compliance rollouts, and supporting organizations running 40+ branches on a single system.</p>
    </div>
    <div class="timeline reveal">
      <div class="tl-item"><div class="yr">2020</div><div class="txt">Technical Support — building a foundation in systems and troubleshooting.</div></div>
      <div class="tl-item"><div class="yr">2021 – 2023</div><div class="txt">Odoo Functional Consultant — requirements, gap analysis, delivery.</div></div>
      <div class="tl-item"><div class="yr">2024 – 2025</div><div class="txt">Led a full Odoo v10 → v17 migration and two-phase ZATCA integration.</div></div>
      <div class="tl-item"><div class="yr">2025 — Present</div><div class="txt">Odoo Techno-Functional Consultant at EPA, Al Khobar.</div></div>
    </div>
  </div>

  <div class="stats reveal">
    <div class="stat"><div class="num">7+</div><div class="lbl">ERP implementations</div></div>
    <div class="stat"><div class="num">v10→v19</div><div class="lbl">Odoo version range</div></div>
    <div class="stat"><div class="num">I & II</div><div class="lbl">ZATCA phases delivered</div></div>
    <div class="stat"><div class="num">40+</div><div class="lbl">Branches supported</div></div>
  </div>
</section>

<section id="skills">
  <div class="label">02 / TOOLKIT</div>
  <h2 class="sec-title reveal">Where I add the most value</h2>
  <div class="skill-grid reveal">
    <div>
      <div class="skill-row" data-pct="95"><div class="skill-top"><span>ERP Implementation & Configuration</span><span class="pct">95%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
      <div class="skill-row" data-pct="90"><div class="skill-top"><span>Business & Gap Analysis</span><span class="pct">90%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
      <div class="skill-row" data-pct="88"><div class="skill-top"><span>ZATCA & Regulatory Compliance</span><span class="pct">88%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
    </div>
    <div>
      <div class="skill-row" data-pct="92"><div class="skill-top"><span>System Migration & Upgrades</span><span class="pct">92%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
      <div class="skill-row" data-pct="85"><div class="skill-top"><span>User Training & Documentation</span><span class="pct">85%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
      <div class="skill-row" data-pct="87"><div class="skill-top"><span>Post-Go-Live Support</span><span class="pct">87%</span></div><div class="bar-track"><div class="bar-fill"></div></div></div>
    </div>
  </div>
</section>

<section id="services">
  <div class="label">03 / SERVICES</div>
  <h2 class="sec-title reveal">Consulting & delivery</h2>
  <div class="service-grid reveal">
    <div class="service-card" data-tilt><div class="n">01</div><h3>Requirements & Gap Analysis</h3><p>Mapping current processes and defining a scope that fits operational reality.</p></div>
    <div class="service-card" data-tilt><div class="n">02</div><h3>Odoo Implementation</h3><p>Sales, CRM, Inventory, Accounting, POS, and Manufacturing — configured around how the business works.</p></div>
    <div class="service-card" data-tilt><div class="n">03</div><h3>Migration & Upgrades</h3><p>Moving businesses forward across Odoo versions without losing data integrity.</p></div>
    <div class="service-card" data-tilt><div class="n">04</div><h3>ZATCA Compliance</h3><p>Phase I & II e-invoicing integration built into ERP workflows.</p></div>
    <div class="service-card" data-tilt><div class="n">05</div><h3>Training & Documentation</h3><p>Making sure teams actually adopt the system, not just switch it on.</p></div>
    <div class="service-card" data-tilt><div class="n">06</div><h3>Post-Go-Live Support</h3><p>Stabilizing operations after launch with ongoing functional support.</p></div>
  </div>
</section>

<section id="projects">
  <div class="label">04 / SELECTED WORK</div>
  <h2 class="sec-title reveal">Flagship rollouts</h2>
  <div class="project-list reveal">
    <div class="project" data-toggle>
      <span class="idx">01</span>
      <div><h4>Nesco Company</h4><div class="tags"><span class="tag">Odoo v18</span><span class="tag">50+ users</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">Full ERP rollout across all core modules, integrated with ZATCA and biometric systems.</div>
    </div>
    <div class="project" data-toggle>
      <span class="idx">02</span>
      <div><h4>Al-Hadithi Medical Co.</h4><div class="tags"><span class="tag">Odoo v19</span><span class="tag">80+ users</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">Full ERP for medical operations — Inventory, Sales, Accounting, Purchasing.</div>
    </div>
    <div class="project" data-toggle>
      <span class="idx">03</span>
      <div><h4>Khafif Food Company</h4><div class="tags"><span class="tag">v10 → v17</span><span class="tag">ZATCA I & II</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">Full version migration plus two-phase ZATCA compliance integration.</div>
    </div>
    <div class="project" data-toggle>
      <span class="idx">04</span>
      <div><h4>Unitedest</h4><div class="tags"><span class="tag">Odoo v17</span><span class="tag">20 users</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">Sales, CRM, and Accounting rollout for a pest-control service business.</div>
    </div>
    <div class="project" data-toggle>
      <span class="idx">05</span>
      <div><h4>NPS Company</h4><div class="tags"><span class="tag">Manufacturing</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">Production, inventory, and sales configuration for manufacturing operations.</div>
    </div>
    <div class="project" data-toggle>
      <span class="idx">06</span>
      <div><h4>Abhaj Contracting</h4><div class="tags"><span class="tag">Project & Procurement</span></div></div>
      <span class="arrow">↗</span>
      <div class="project-detail">ERP configuration for project tracking, procurement, and finance.</div>
    </div>
  </div>
</section>

<section id="education">
  <div class="label">05 / EDUCATION</div>
  <h2 class="sec-title reveal">Qualifications</h2>
  <div class="edu-grid reveal">
    <div class="edu-card"><div class="yr">2026</div><h4>Odoo 19 Functional Certification</h4><p>Coursera</p></div>
    <div class="edu-card"><div class="yr">2014–2020</div><h4>B.Sc. Computer Science & Information Systems</h4><p>Omdurman Islamic University, Sudan</p></div>
    <div class="edu-card"><div class="yr">2024</div><h4>Google IT Support Professional Certificate</h4><p>Coursera / Google</p></div>
    <div class="edu-card"><div class="yr">2024</div><h4>Odoo Technical – Experience Accelerate Program</h4><p>Technical delivery track</p></div>
  </div>
</section>

<section id="contact">
  <div class="label" style="justify-content:center;">06 / CONTACT</div>
  <h2 class="reveal">Planning an Odoo implementation or upgrade?</h2>
  <p class="reveal">Let's talk about your requirements and how Odoo can be configured to fit your operations.</p>
  <a href="mailto:nooh8586@gmail.com" class="big-link reveal" data-hover>nooh8586@gmail.com</a>
  <div class="contact-meta reveal">
    <span>+966 543 695 851</span>
    <span>Al Khobar, Saudi Arabia</span>
    <a href="https://linkedin.com/in/nooh-suliman-081a302a1/" target="_blank" data-hover>LinkedIn</a>
  </div>
</section>

<footer>
  <span>© 2026 Nooh Suliman</span>
  <span>Odoo Techno-Functional Consultant</span>
</footer>

<script>
  // custom cursor
  const cursor = document.getElementById('cursor');
  const glow = document.getElementById('glow');
  window.addEventListener('mousemove', e=>{
    cursor.style.left = e.clientX+'px'; cursor.style.top = e.clientY+'px';
    glow.style.left = e.clientX+'px'; glow.style.top = e.clientY+'px';
  });
  document.querySelectorAll('[data-hover], a, .service-card, .project').forEach(el=>{
    el.addEventListener('mouseenter', ()=>cursor.classList.add('hover'));
    el.addEventListener('mouseleave', ()=>cursor.classList.remove('hover'));
  });

  // scroll reveal
  const io = new IntersectionObserver(entries=>{
    entries.forEach(en=>{ if(en.isIntersecting){ en.target.classList.add('in'); } });
  }, {threshold:0.15});
  document.querySelectorAll('.reveal').forEach(el=>io.observe(el));

  // skill bars animate on view
  const skillIo = new IntersectionObserver(entries=>{
    entries.forEach(en=>{
      if(en.isIntersecting){
        const fill = en.target.querySelector('.bar-fill');
        fill.style.width = en.target.dataset.pct + '%';
        skillIo.unobserve(en.target);
      }
    });
  }, {threshold:0.4});
  document.querySelectorAll('.skill-row').forEach(el=>skillIo.observe(el));

  // active nav highlight
  const navLinks = document.querySelectorAll('[data-nav]');
  const sections = Array.from(navLinks).map(l=>document.querySelector(l.getAttribute('href')));
  function setActive(){
    let current = sections[0];
    const y = window.scrollY + 160;
    sections.forEach(s=>{ if(s.offsetTop <= y) current = s; });
    navLinks.forEach(l=> l.classList.toggle('active', l.getAttribute('href') === '#'+current.id));
  }
  document.addEventListener('scroll', setActive, {passive:true});
  setActive();

  // service card cursor-follow glow
  document.querySelectorAll('.service-card').forEach(card=>{
    card.addEventListener('mousemove', e=>{
      const r = card.getBoundingClientRect();
      card.style.setProperty('--mx', (e.clientX-r.left)+'px');
      card.style.setProperty('--my', (e.clientY-r.top)+'px');
    });
  });

  // project expand on click
  document.querySelectorAll('[data-toggle]').forEach(p=>{
    p.addEventListener('click', ()=> p.classList.toggle('open'));
  });
</script>

</body>
</html>
