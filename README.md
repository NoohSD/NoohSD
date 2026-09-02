<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Nooh Suliman — Odoo Techno-Functional Consultant</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  :root{
    --bg-0:#150F1E;
    --bg-1:#20162E;
    --bg-2:#291D3B;
    --line:rgba(233,228,238,0.10);
    --ink:#E9E4EE;
    --ink-soft:#A79BB8;
    --gold:#CBA135;
    --teal:#2E9E8B;
    --r-sm:6px;
    --r-md:10px;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  @media (prefers-reduced-motion: reduce){
    html{scroll-behavior:auto;}
    *{animation-duration:0.001ms !important; transition-duration:0.001ms !important;}
  }
  body{
    margin:0;
    background:var(--bg-0);
    color:var(--ink);
    font-family:'IBM Plex Sans', sans-serif;
    line-height:1.55;
    -webkit-font-smoothing:antialiased;
  }
  h1,h2,h3,.display{font-family:'Space Grotesk', sans-serif; font-weight:600; margin:0;}
  a{color:inherit;}
  .mono{font-family:'IBM Plex Mono', monospace;}
  .wrap{max-width:1120px; margin:0 auto; padding:0 32px;}
  @media(max-width:640px){.wrap{padding:0 20px;}}

  /* ---------- layout shell: side rail + content ---------- */
  .shell{display:grid; grid-template-columns:64px 1fr; }
  @media(max-width:900px){.shell{grid-template-columns:1fr;}}

  .rail{
    position:sticky; top:0; height:100vh; display:flex; flex-direction:column;
    align-items:center; justify-content:center; gap:22px; border-right:1px solid var(--line);
  }
  @media(max-width:900px){.rail{display:none;}}
  .rail button{
    width:9px; height:9px; border-radius:50%; border:1px solid var(--ink-soft);
    background:transparent; cursor:pointer; padding:0; transition:background .2s, transform .2s;
  }
  .rail button.active{background:var(--gold); border-color:var(--gold); transform:scale(1.3);}

  section{padding:96px 0; border-bottom:1px solid var(--line);}
  section:last-of-type{border-bottom:none;}

  /* ---------- hero ---------- */
  .hero{position:relative; padding-top:88px; overflow:hidden;}
  .hero-pattern{position:absolute; inset:0; opacity:.35; pointer-events:none;}
  .kicker{color:var(--gold); font-family:'IBM Plex Mono', monospace; font-size:13px; letter-spacing:.02em;}
  .hero h1{font-size:clamp(38px,6vw,68px); line-height:1.04; margin-top:14px; max-width:14ch;}
  .hero .role{font-size:clamp(17px,2.2vw,22px); color:var(--ink-soft); margin-top:16px; max-width:46ch;}
  .chips{display:flex; flex-wrap:wrap; gap:10px; margin-top:32px;}
  .chip{border:1px solid var(--line); border-radius:999px; padding:7px 14px; font-size:13px; color:var(--ink-soft); font-family:'IBM Plex Mono',monospace;}
  .chip a{text-decoration:none;}
  .chip:hover{border-color:var(--gold); color:var(--ink);}

  .stat-row{display:grid; grid-template-columns:repeat(4,1fr); gap:24px; margin-top:64px;}
  @media(max-width:700px){.stat-row{grid-template-columns:repeat(2,1fr);}}
  .stat{border-left:2px solid var(--teal); padding-left:14px;}
  .stat .num{font-family:'Space Grotesk',sans-serif; font-size:34px; font-weight:600; color:var(--ink);}
  .stat .label{color:var(--ink-soft); font-size:13px; margin-top:2px;}

  /* ---------- headings ---------- */
  .eyebrow{color:var(--teal); font-family:'IBM Plex Mono',monospace; font-size:13px; margin-bottom:10px;}
  .sec-head{font-size:clamp(26px,3.4vw,36px); max-width:20ch;}
  .sec-sub{color:var(--ink-soft); max-width:60ch; margin-top:14px; font-size:16px;}

  /* ---------- about ---------- */
  .about-grid{display:grid; grid-template-columns:1.1fr 0.9fr; gap:56px; margin-top:48px;}
  @media(max-width:800px){.about-grid{grid-template-columns:1fr;}}
  .about-grid p{color:var(--ink-soft); font-size:16px; max-width:56ch;}
  .about-grid p + p{margin-top:16px;}
  .focus-list{list-style:none; margin:0; padding:0; display:flex; flex-direction:column; gap:0;}
  .focus-list li{border-top:1px solid var(--line); padding:14px 0; font-size:15px; display:flex; justify-content:space-between; color:var(--ink);}
  .focus-list li:last-child{border-bottom:1px solid var(--line);}
  .focus-list span.n{color:var(--ink-soft); font-family:'IBM Plex Mono',monospace; font-size:13px;}

  /* ---------- lifecycle stepper ---------- */
  .stepper{margin-top:52px; display:flex; flex-direction:column; border-top:1px solid var(--line);}
  .step{border-bottom:1px solid var(--line); cursor:pointer;}
  .step-head{display:flex; align-items:center; gap:20px; padding:20px 4px; justify-content:space-between;}
  .step-head-left{display:flex; align-items:center; gap:20px;}
  .step-idx{font-family:'IBM Plex Mono',monospace; color:var(--ink-soft); font-size:13px; width:26px;}
  .step-title{font-family:'Space Grotesk',sans-serif; font-size:18px; font-weight:600;}
  .step-plus{color:var(--gold); font-size:20px; font-family:'IBM Plex Mono',monospace; transition:transform .25s;}
  .step.open .step-plus{transform:rotate(45deg);}
  .step-body{max-height:0; overflow:hidden; transition:max-height .3s ease;}
  .step-body p{color:var(--ink-soft); padding:0 46px 22px 46px; margin:0; max-width:60ch; font-size:15px;}
  .step.open .step-body{max-height:160px;}

  /* ---------- expertise tabs ---------- */
  .tabs{display:flex; gap:8px; margin-top:44px; flex-wrap:wrap;}
  .tab-btn{background:transparent; border:1px solid var(--line); color:var(--ink-soft); padding:9px 18px; border-radius:999px; font-family:'IBM Plex Mono',monospace; font-size:13px; cursor:pointer; transition:.2s;}
  .tab-btn.active{background:var(--teal); border-color:var(--teal); color:#0E1613;}
  .tab-panel{display:none; margin-top:32px;}
  .tab-panel.active{display:grid; grid-template-columns:repeat(3,1fr); gap:14px;}
  @media(max-width:700px){.tab-panel.active{grid-template-columns:repeat(2,1fr);}}
  .pill{border:1px solid var(--line); border-radius:var(--r-sm); padding:14px 16px; font-size:14px; color:var(--ink);}

  /* ---------- projects ---------- */
  .proj-shell{display:grid; grid-template-columns:280px 1fr; gap:40px; margin-top:48px;}
  @media(max-width:800px){.proj-shell{grid-template-columns:1fr;}}
  .proj-list{display:flex; flex-direction:column; border-top:1px solid var(--line);}
  .proj-item{border-bottom:1px solid var(--line); padding:16px 6px; cursor:pointer; display:flex; justify-content:space-between; color:var(--ink-soft); font-family:'Space Grotesk',sans-serif; font-size:16px;}
  .proj-item.active{color:var(--gold);}
  .proj-item span{font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--ink-soft);}
  .proj-detail{border:1px solid var(--line); border-radius:var(--r-md); padding:32px; background:var(--bg-1);}
  .proj-detail h3{font-size:22px;}
  .proj-detail .meta{color:var(--gold); font-family:'IBM Plex Mono',monospace; font-size:13px; margin-top:8px;}
  .proj-detail ul{margin:20px 0 0 0; padding-left:18px; color:var(--ink-soft);}
  .proj-detail li{margin-bottom:6px; font-size:15px;}

  /* ---------- branch stats ---------- */
  .branch{margin-top:48px; border:1px solid var(--line); border-radius:var(--r-md); padding:40px; background:linear-gradient(135deg, var(--bg-1), var(--bg-2));}
  .branch-grid{display:grid; grid-template-columns:repeat(4,1fr); gap:20px; margin-top:28px;}
  @media(max-width:700px){.branch-grid{grid-template-columns:repeat(2,1fr);}}
  .branch-item{font-size:14px; color:var(--ink-soft); border-top:1px solid var(--line); padding-top:10px;}

  /* ---------- version slider ---------- */
  .versions{margin-top:52px;}
  .v-track{position:relative; display:flex; justify-content:space-between; padding:0 4px;}
  .v-line{position:absolute; top:9px; left:4px; right:4px; height:2px; background:var(--line);}
  .v-dot{position:relative; z-index:1; display:flex; flex-direction:column; align-items:center; gap:10px; cursor:pointer; background:var(--bg-0); }
  .v-dot .circle{width:20px; height:20px; border-radius:50%; border:2px solid var(--ink-soft); background:var(--bg-0); transition:.2s;}
  .v-dot.active .circle{border-color:var(--gold); background:var(--gold);}
  .v-dot .lab{font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--ink-soft);}
  .v-dot.active .lab{color:var(--ink);}
  .v-detail{margin-top:36px; border:1px solid var(--line); border-radius:var(--r-md); padding:26px 30px; min-height:64px; color:var(--ink-soft); font-size:15px;}
  .v-detail strong{color:var(--ink); font-family:'Space Grotesk',sans-serif;}

  /* ---------- certifications ---------- */
  .cert-grid{display:grid; grid-template-columns:repeat(2,1fr); gap:16px; margin-top:44px;}
  @media(max-width:700px){.cert-grid{grid-template-columns:1fr;}}
  .cert{border:1px solid var(--line); border-radius:var(--r-md); padding:22px; }
  .cert .yr{color:var(--gold); font-family:'IBM Plex Mono',monospace; font-size:13px;}
  .cert h3{font-size:17px; margin-top:6px;}
  .cert .org{color:var(--ink-soft); font-size:14px; margin-top:4px;}

  /* ---------- contact ---------- */
  .contact-grid{display:grid; grid-template-columns:1fr 1fr; gap:20px; margin-top:44px;}
  @media(max-width:700px){.contact-grid{grid-template-columns:1fr;}}
  .contact-card{border:1px solid var(--line); border-radius:var(--r-md); padding:26px; text-decoration:none; display:block; transition:.2s;}
  .contact-card:hover{border-color:var(--gold); background:var(--bg-1);}
  .contact-card .k{font-family:'IBM Plex Mono',monospace; font-size:12px; color:var(--ink-soft);}
  .contact-card .v{font-family:'Space Grotesk',sans-serif; font-size:18px; margin-top:8px;}
  footer{padding:40px 0; text-align:center; color:var(--ink-soft); font-size:13px;}

  ::selection{background:var(--gold); color:#0E1613;}
</style>
</head>
<body>

<div class="shell">
  <nav class="rail" id="rail">
    <button data-target="hero" class="active" aria-label="Hero"></button>
    <button data-target="about" aria-label="About"></button>
    <button data-target="lifecycle" aria-label="Lifecycle"></button>
    <button data-target="expertise" aria-label="Expertise"></button>
    <button data-target="projects" aria-label="Projects"></button>
    <button data-target="branch" aria-label="Multi-branch"></button>
    <button data-target="versions" aria-label="Versions"></button>
    <button data-target="certs" aria-label="Certifications"></button>
    <button data-target="contact" aria-label="Contact"></button>
  </nav>

  <main>
    <!-- HERO -->
    <section class="hero" id="hero">
      <svg class="hero-pattern" viewBox="0 0 1120 260" preserveAspectRatio="none">
        <defs>
          <pattern id="geo" width="60" height="60" patternUnits="userSpaceOnUse">
            <path d="M30 0 L60 30 L30 60 L0 30 Z" fill="none" stroke="#CBA135" stroke-width="0.6"/>
          </pattern>
        </defs>
        <rect width="1120" height="260" fill="url(#geo)"/>
      </svg>
      <div class="wrap">
        <div class="kicker">ODOO 19 CERTIFIED · SAUDI ARABIA</div>
        <h1>Nooh Suliman</h1>
        <div class="role">Senior Odoo Techno-Functional Consultant — I turn business requirements into ERP systems people can actually run a company on.</div>
        <div class="chips">
          <div class="chip"><a href="mailto:nooh8586@gmail.com">nooh8586@gmail.com</a></div>
          <div class="chip">+966 54 369 5851</div>
          <div class="chip"><a href="https://linkedin.com/in/nooh-suliman-081a3021/" target="_blank" rel="noopener">LinkedIn</a></div>
          <div class="chip"><a href="https://github.com/nooh8586" target="_blank" rel="noopener">GitHub</a></div>
        </div>
        <div class="stat-row">
          <div class="stat"><div class="num">5+</div><div class="label">Years in Odoo</div></div>
          <div class="stat"><div class="num">7+</div><div class="label">ERP implementations</div></div>
          <div class="stat"><div class="num">40+</div><div class="label">Branches supported</div></div>
          <div class="stat"><div class="num">100+</div><div class="label">Training sessions run</div></div>
        </div>
      </div>
    </section>

    <!-- ABOUT -->
    <section id="about">
      <div class="wrap">
        <div class="eyebrow">About</div>
        <h2 class="sec-head">Business first, Odoo second.</h2>
        <div class="about-grid">
          <div>
            <p>I specialize in ERP implementation, business analysis, process optimization, and digital transformation. Across the full implementation lifecycle — requirements, functional design, configuration, testing, training, and post-go-live support — my job is to close the gap between what a business actually needs and what the system is configured to do.</p>
            <p>I don't treat Odoo as software to install. I treat it as the operating platform a business runs on, which means the goal is never "go live" — it's an environment people trust and can scale with.</p>
          </div>
          <ul class="focus-list">
            <li>Fit-Gap Analysis & Process Mapping <span class="n">01</span></li>
            <li>Functional Solution Design <span class="n">02</span></li>
            <li>UAT & Go-Live Support <span class="n">03</span></li>
            <li>Client Training & Knowledge Transfer <span class="n">04</span></li>
            <li>Saudi ZATCA / Fatoora Compliance <span class="n">05</span></li>
          </ul>
        </div>
      </div>
    </section>

    <!-- LIFECYCLE -->
    <section id="lifecycle">
      <div class="wrap">
        <div class="eyebrow">How I work</div>
        <h2 class="sec-head">The implementation lifecycle</h2>
        <p class="sec-sub">Every project moves through the same spine — click a stage to see what it involves.</p>
        <div class="stepper" id="stepper"></div>
      </div>
    </section>

    <!-- EXPERTISE -->
    <section id="expertise">
      <div class="wrap">
        <div class="eyebrow">Expertise</div>
        <h2 class="sec-head">Functional depth, technical fluency</h2>
        <div class="tabs" id="tabs">
          <button class="tab-btn active" data-tab="functional">Functional</button>
          <button class="tab-btn" data-tab="apps">Odoo Apps</button>
          <button class="tab-btn" data-tab="technical">Technical</button>
        </div>
        <div class="tab-panel active" data-panel="functional">
          <div class="pill">Requirements Gathering</div><div class="pill">Business Analysis</div><div class="pill">Fit-Gap Analysis</div>
          <div class="pill">Process Mapping</div><div class="pill">SRS Documentation</div><div class="pill">UAT</div>
          <div class="pill">Go-Live Support</div><div class="pill">Client Training</div><div class="pill">Change Management</div>
        </div>
        <div class="tab-panel" data-panel="apps">
          <div class="pill">Sales & CRM</div><div class="pill">Purchase</div><div class="pill">Inventory</div>
          <div class="pill">Accounting</div><div class="pill">Point of Sale</div><div class="pill">Manufacturing</div>
          <div class="pill">Projects & Timesheets</div><div class="pill">HR & Attendance</div><div class="pill">Website / Studio</div>
        </div>
        <div class="tab-panel" data-panel="technical">
          <div class="pill">Python / XML</div><div class="pill">PostgreSQL / SQL</div><div class="pill">REST API / XML-RPC</div>
          <div class="pill">Custom Modules & Views</div><div class="pill">Security & Access Rights</div><div class="pill">QWeb Reports</div>
          <div class="pill">Docker / Odoo.sh</div><div class="pill">Linux / Git</div><div class="pill">Biometric Integration</div>
        </div>
      </div>
    </section>

    <!-- PROJECTS -->
    <section id="projects">
      <div class="wrap">
        <div class="eyebrow">Selected work</div>
        <h2 class="sec-head">ERP implementations</h2>
        <div class="proj-shell">
          <div class="proj-list" id="projList"></div>
          <div class="proj-detail" id="projDetail"></div>
        </div>
      </div>
    </section>

    <!-- MULTI-BRANCH -->
    <section id="branch">
      <div class="wrap">
        <div class="eyebrow">At scale</div>
        <h2 class="sec-head">Rolling out ERP across 40+ branches</h2>
        <div class="branch">
          <p style="color:var(--ink-soft); max-width:60ch; margin:0;">One of my strongest implementation experiences: a single organization running Point of Sale, Inventory, Accounting, Sales, Purchasing, Manufacturing and CRM consistently across more than forty branches — with centralized reporting and ZATCA compliance holding it together.</p>
          <div class="branch-grid">
            <div class="branch-item">Point of Sale</div>
            <div class="branch-item">Centralized Reporting</div>
            <div class="branch-item">ZATCA Compliance</div>
            <div class="branch-item">Data Consistency</div>
          </div>
        </div>
      </div>
    </section>

    <!-- VERSIONS -->
    <section id="versions">
      <div class="wrap">
        <div class="eyebrow">Platform depth</div>
        <h2 class="sec-head">Odoo 10 through 19</h2>
        <p class="sec-sub">Community and Enterprise. Click a version for where I've used it.</p>
        <div class="versions">
          <div class="v-track" id="vTrack"><div class="v-line"></div></div>
          <div class="v-detail" id="vDetail"></div>
        </div>
      </div>
    </section>

    <!-- CERTS -->
    <section id="certs">
      <div class="wrap">
        <div class="eyebrow">Certifications & education</div>
        <h2 class="sec-head">Credentials</h2>
        <div class="cert-grid">
          <div class="cert"><div class="yr">2026</div><h3>Odoo 19 Functional Certification</h3><div class="org">Odoo</div></div>
          <div class="cert"><div class="yr">2014–2020</div><h3>B.Sc. Computer Science & Information Systems</h3><div class="org">Omdurman Islamic University</div></div>
          <div class="cert"><div class="yr">2024</div><h3>Google IT Support Professional Certificate</h3><div class="org">Coursera</div></div>
          <div class="cert"><div class="yr">2024</div><h3>Odoo Technical Program</h3><div class="org">Odoo</div></div>
        </div>
      </div>
    </section>

    <!-- CONTACT -->
    <section id="contact">
      <div class="wrap">
        <div class="eyebrow">Get in touch</div>
        <h2 class="sec-head">Open to ERP implementation & consulting work</h2>
        <div class="contact-grid">
          <a class="contact-card" href="mailto:nooh8586@gmail.com">
            <div class="k">EMAIL</div><div class="v">nooh8586@gmail.com</div>
          </a>
          <a class="contact-card" href="tel:+966543695851">
            <div class="k">PHONE</div><div class="v">+966 54 369 5851</div>
          </a>
          <a class="contact-card" href="https://linkedin.com/in/nooh-suliman-081a3021/" target="_blank" rel="noopener">
            <div class="k">LINKEDIN</div><div class="v">nooh-suliman</div>
          </a>
          <a class="contact-card" href="https://github.com/nooh8586" target="_blank" rel="noopener">
            <div class="k">GITHUB</div><div class="v">nooh8586</div>
          </a>
        </div>
      </div>
    </section>

    <footer>Odoo Techno-Functional Consultant · Saudi Arabia</footer>
  </main>
</div>

<script>
// ---- data ----
const stages = [
  ["Requirements Analysis","Understanding the business as it actually operates today, before proposing anything about the system."],
  ["Process Mapping","Documenting current workflows so gaps against standard Odoo are visible to both sides."],
  ["Fit-Gap Analysis","Deciding what Odoo covers out of the box and what needs configuration or custom development."],
  ["Functional Solution Design","Translating the agreed process into a concrete configuration and customization plan."],
  ["Configuration & Customization","Building the system and coordinating development work against the design."],
  ["Testing / UAT","Validating the build against real business scenarios with the people who'll use it daily."],
  ["Training & Go-Live","Getting users confident on day one, then supporting the system as it settles in."],
];

const stepperEl = document.getElementById('stepper');
stages.forEach((s,i)=>{
  const div = document.createElement('div');
  div.className = 'step';
  div.innerHTML = `<div class="step-head">
      <div class="step-head-left"><span class="step-idx">0${i+1}</span><span class="step-title">${s[0]}</span></div>
      <span class="step-plus">+</span>
    </div>
    <div class="step-body"><p>${s[1]}</p></div>`;
  div.addEventListener('click', ()=>{
    const wasOpen = div.classList.contains('open');
    document.querySelectorAll('.step').forEach(el=>el.classList.remove('open'));
    if(!wasOpen) div.classList.add('open');
  });
  stepperEl.appendChild(div);
});
stepperEl.firstChild.classList.add('open');

// ---- tabs ----
document.querySelectorAll('.tab-btn').forEach(btn=>{
  btn.addEventListener('click', ()=>{
    document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
    document.querySelectorAll('.tab-panel').forEach(p=>p.classList.remove('active'));
    btn.classList.add('active');
    document.querySelector(`.tab-panel[data-panel="${btn.dataset.tab}"]`).classList.add('active');
  });
});

// ---- projects ----
const projects = [
  ["Nesco Company","Odoo 18 · 30+ Users",["Accounting, Sales, Purchase, Inventory, HR","ZATCA integration","Biometric attendance integration","Business workflow automation"]],
  ["Al-Hadithi Medical","Odoo 19 · 50+ Users",["Inventory management","Sales & Accounting","Purchasing workflows","User training, UAT & go-live support"]],
  ["Abhaj Contracting","Odoo 19 · 30+ Users",["Project management","Procurement","Financial management","Reporting & process optimization"]],
  ["NPS Manufacturing","Odoo 18 · 15+ Users",["Manufacturing & Inventory","Product & BOM configuration","Sales integration","Production process workflows"]],
  ["Unitedest Pest Control","Odoo 17 · 20+ Users",["CRM & Sales","Accounting","Customer workflows","Service operations"]],
  ["IDNS — Odoo.sh Upgrade","Odoo 17 → 19",["Odoo.sh version upgrade","Custom module compatibility","ZATCA & reporting","Post-upgrade training & support"]],
];
const listEl = document.getElementById('projList');
const detailEl = document.getElementById('projDetail');
function renderProject(i){
  document.querySelectorAll('.proj-item').forEach((el,idx)=>el.classList.toggle('active', idx===i));
  const p = projects[i];
  detailEl.innerHTML = `<h3>${p[0]}</h3><div class="meta">${p[1]}</div><ul>${p[2].map(x=>`<li>${x}</li>`).join('')}</ul>`;
}
projects.forEach((p,i)=>{
  const item = document.createElement('div');
  item.className = 'proj-item';
  item.innerHTML = `<span>${p[0]}</span><span>${p[1].split('·')[0].trim()}</span>`;
  item.addEventListener('click', ()=>renderProject(i));
  listEl.appendChild(item);
});
renderProject(0);

// ---- versions ----
const versions = [
  ["v10","Earliest environments I supported."],
  ["v11","Community deployments, early customization work."],
  ["v12","Continued module development & support."],
  ["v13","Functional configuration across multiple clients."],
  ["v14","Mixed Community/Enterprise environments."],
  ["v15","Expanded ERP implementation projects."],
  ["v16","Full-cycle implementations, Enterprise features."],
  ["v17","Unitedest Pest Control build; source version for the IDNS Odoo.sh upgrade."],
  ["v18","Nesco Company and NPS Manufacturing implementations."],
  ["v19","Al-Hadithi Medical and Abhaj Contracting; current certified version."],
];
const vTrack = document.getElementById('vTrack');
const vDetail = document.getElementById('vDetail');
function renderVersion(i){
  document.querySelectorAll('.v-dot').forEach((el,idx)=>el.classList.toggle('active', idx===i));
  vDetail.innerHTML = `<strong>Odoo ${versions[i][0]}</strong> — ${versions[i][1]}`;
}
versions.forEach((v,i)=>{
  const dot = document.createElement('div');
  dot.className = 'v-dot';
  dot.innerHTML = `<div class="circle"></div><div class="lab">${v[0]}</div>`;
  dot.addEventListener('click', ()=>renderVersion(i));
  vTrack.appendChild(dot);
});
renderVersion(9);

// ---- side rail active state on scroll ----
const railBtns = document.querySelectorAll('#rail button');
const sections = [...railBtns].map(b=>document.getElementById(b.dataset.target));
railBtns.forEach(b=>b.addEventListener('click', ()=>document.getElementById(b.dataset.target).scrollIntoView({behavior:'smooth'})));
const obs = new IntersectionObserver((entries)=>{
  entries.forEach(entry=>{
    if(entry.isIntersecting){
      const idx = sections.indexOf(entry.target);
      railBtns.forEach(b=>b.classList.remove('active'));
      railBtns[idx].classList.add('active');
    }
  });
}, {rootMargin:"-45% 0px -45% 0px"});
sections.forEach(s=>obs.observe(s));

// ---- stat count-up on first view ----
const statNums = document.querySelectorAll('.stat .num');
let counted = false;
const heroObs = new IntersectionObserver((entries)=>{
  if(entries[0].isIntersecting && !counted){
    counted = true;
    statNums.forEach(el=>{
      const target = parseInt(el.textContent);
      let cur = 0;
      const step = Math.max(1, Math.round(target/30));
      const suffix = el.textContent.replace(/[0-9]/g,'');
      const timer = setInterval(()=>{
        cur += step;
        if(cur >= target){ cur = target; clearInterval(timer); }
        el.textContent = cur + suffix;
      }, 25);
    });
  }
}, {threshold:0.4});
heroObs.observe(document.querySelector('.stat-row'));
</script>
</body>
</html>
