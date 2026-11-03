<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Mizan – Government AI model selection</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Schibsted+Grotesk:wght@400;500;700;800&display=swap">
<style>
:root{--bg:#f3f5f4;--surface:#fff;--ink:#12201f;--muted:#5b6b69;--line:#d5dddb;--brand:#0f4c4a;--brand-ink:#fff;--gold:#b8860b;--ok:#17724a;--okbg:#e3f3ea;--bad:#a63a2b;--badbg:#f8e6e2;
box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0d1514;--surface:#15201f;--ink:#e6efed;--muted:#97aaa7;--line:#2a3a38;--brand:#5fc2b8;--brand-ink:#08201e;--gold:#e0b64a;--ok:#6fd4a0;--okbg:#14352a;--bad:#f09a8c;--badbg:#3a1d19}}
:root[data-theme="dark"]{--bg:#0d1514;--surface:#15201f;--ink:#e6efed;--muted:#97aaa7;--line:#2a3a38;--brand:#5fc2b8;--brand-ink:#08201e;--gold:#e0b64a;--ok:#6fd4a0;--okbg:#14352a;--bad:#f09a8c;--badbg:#3a1d19}
*{box-sizing:border-box}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
body{margin:0;background:var(--bg);color:var(--ink);font:400 16px/1.5 "Schibsted Grotesk",system-ui,-apple-system,"Segoe UI",sans-serif}
.wrap{max-width:1120px;margin:0 auto;padding:16px 16px 56px}
h1{font-size:clamp(28px,5vw,44px);line-height:1.08;margin:0 0 10px;font-weight:800;letter-spacing:-.02em;max-width:18ch}
h2{font-size:20px;margin:0 0 12px;font-weight:700}
h3{margin:0 0 6px;font-size:16px}
p{margin:0}
.top{display:flex;justify-content:space-between;align-items:center;gap:12px;flex-wrap:wrap;margin-bottom:12px}
.brand{font-weight:800;font-size:18px;display:flex;align-items:center;gap:10px}
.brand i{width:26px;height:26px;border:2px solid var(--brand);border-radius:50%;position:relative;display:inline-block}
.brand i:after{content:"";position:absolute;left:50%;top:3px;bottom:3px;width:2px;background:var(--gold);transform:translateX(-50%)}
.who{display:flex;align-items:center;gap:8px;font-size:14px;color:var(--muted);flex-wrap:wrap}
.nav{display:flex;gap:4px;border-bottom:1px solid var(--line);margin-bottom:20px;overflow-x:auto}
.nav button{background:none;border:0;border-bottom:3px solid transparent;padding:10px 14px;font-weight:700;color:var(--muted);cursor:pointer;white-space:nowrap}
.nav button.on{color:var(--brand);border-color:var(--gold)}
.hero{position:relative;border-radius:12px;overflow:hidden;min-height:260px;margin-bottom:16px;background:#0f4c4a}
.hero svg,.hero img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.hero .txt{position:relative;padding:32px 24px;color:#fff;background:linear-gradient(90deg,rgba(8,32,30,.88),rgba(8,32,30,.2))}
.hero h1{color:#fff}.hero p{max-width:52ch;font-size:17px;opacity:.92}
.card{background:var(--surface);border:1px solid var(--line);border-radius:10px;padding:16px}
.lead{color:var(--muted);max-width:60ch;font-size:17px}
.scen{display:flex;flex-wrap:wrap;gap:8px;margin:12px 0 20px;align-items:center}
.scen span{font-weight:700;font-size:14px}
.pill{border:1px solid var(--brand);background:transparent;color:var(--brand);padding:7px 12px;border-radius:999px;font-weight:700;cursor:pointer;font-size:14px}
.pill:hover{background:var(--brand);color:var(--brand-ink)}
.roles{display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:12px;margin:4px 0}
.rc{background:var(--surface);border:1px solid var(--line);border-radius:12px;padding:10px;text-align:left;cursor:pointer;color:var(--ink);transition:transform .15s,border-color .15s}
.rc:hover{transform:translateY(-3px);border-color:var(--brand)}
.rc b{display:block;font-size:17px;margin-top:10px}
.rc span{font-size:13px;color:var(--muted)}
.ph{position:relative;height:110px;border-radius:8px;overflow:hidden}
.ph svg,.ph img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.hero{min-height:320px;box-shadow:0 14px 40px rgba(8,32,30,.28)}
.hero .txt{display:flex;flex-direction:column;justify-content:center;min-height:320px;padding:36px 28px;background:linear-gradient(90deg,rgba(6,26,25,.92) 0%,rgba(6,26,25,.55) 60%,rgba(6,26,25,.15) 100%)}
.kick{display:inline-block;align-self:flex-start;background:rgba(224,182,74,.18);border:1px solid #e0b64a;color:#f5e3a8;font-size:12px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;border-radius:999px;padding:4px 12px;margin-bottom:14px}
.hero h1{font-size:clamp(30px,6vw,52px);max-width:16ch}
.hero .go{align-self:flex-start;margin-top:18px;background:#e0b64a;color:#12201f;border:0;border-radius:999px;padding:12px 24px;font-weight:800;cursor:pointer;box-shadow:0 6px 18px rgba(0,0,0,.3);transition:transform .15s}
.hero .go:hover{transform:translateY(-2px)}
.badges{display:flex;flex-wrap:wrap;gap:8px;margin-top:18px}
.badges span{background:rgba(255,255,255,.12);border:1px solid rgba(255,255,255,.25);color:#fff;border-radius:8px;padding:6px 10px;font-size:13px;font-weight:700;backdrop-filter:blur(4px)}
.ph{height:140px}
.ph:after{content:"";position:absolute;inset:0;background:linear-gradient(180deg,transparent 55%,rgba(8,32,30,.45));pointer-events:none}
.rc{box-shadow:0 2px 10px rgba(8,32,30,.08)}
.rc:hover{box-shadow:0 12px 28px rgba(8,32,30,.2)}
.rc b:after{content:" →";color:var(--gold)}
.sech{display:flex;align-items:center;gap:10px;margin:22px 0 10px}
.sech h2{margin:0}.sech:after{content:"";flex:1;height:1px;background:var(--line)}
.card .big{color:var(--brand)}
.metrics{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px;margin:0 0 20px}
.time .row{display:flex;align-items:center;gap:10px;font-size:14px;margin-top:8px}
.time .lbl{width:84px;color:var(--muted);flex:none}
.bar{height:14px;border-radius:3px;background:var(--line);flex:1;overflow:hidden}
.bar b{display:block;height:100%;background:var(--muted);transition:width .4s}
.bar b.new{background:var(--brand)}
.big{font-size:34px;font-weight:800;line-height:1}
.small{font-size:13px;color:var(--muted)}
.main{display:grid;grid-template-columns:320px 1fr;gap:20px;align-items:start}
@media(max-width:860px){.main{grid-template-columns:1fr}}
.side{position:sticky;top:12px}
@media(max-width:860px){.side{position:static}}
label{display:block;font-weight:700;font-size:14px;margin:14px 0 6px}
.first{margin-top:0}
select,input[type=text],input[type=email],textarea,button{font:inherit}
select,input[type=text],input[type=email],textarea{width:100%;padding:10px;border:1px solid var(--line);border-radius:8px;background:var(--bg);color:var(--ink)}
input[type=range]{width:100%;accent-color:var(--brand)}
.sl{margin-top:10px;font-size:14px}
:focus-visible{outline:3px solid var(--gold);outline-offset:2px}
.chk{display:flex;gap:8px;align-items:center;font-weight:500;margin:10px 0 0}
.chk input{accent-color:var(--brand)}
.m{border:1px solid var(--line);border-radius:10px;background:var(--surface);padding:16px;margin-bottom:12px;display:grid;grid-template-columns:1fr auto;gap:8px 16px}
.m.blocked{background:transparent;border-style:dashed}
.m h3{font-size:18px;margin:0}
.vendor{color:var(--muted);font-size:14px}
.score{text-align:right}.score .big{font-size:30px}
.chips{display:flex;flex-wrap:wrap;gap:6px;grid-column:1/-1}
.chip{font-size:12.5px;padding:2px 8px;border-radius:4px;font-weight:500}
.chip.y{background:var(--okbg);color:var(--ok)}.chip.n{background:var(--badbg);color:var(--bad)}
.why{grid-column:1/-1;color:var(--bad);font-size:14px;font-weight:500}
.perf{grid-column:1/-1;display:grid;grid-template-columns:repeat(3,1fr);gap:10px;font-size:13px;color:var(--muted)}
.perf .bar{height:6px;margin-top:4px}
.det{grid-column:1/-1;font-size:14px;color:var(--muted);border-top:1px solid var(--line);padding-top:8px}
.acts{display:flex;gap:8px;flex-wrap:wrap}
.btn{background:var(--brand);color:var(--brand-ink);border:0;padding:9px 16px;border-radius:8px;font-weight:700;cursor:pointer}
.btn[disabled]{opacity:.4;cursor:not-allowed}
.btn.ghost{background:transparent;color:var(--brand);border:1px solid var(--brand)}
.gate{margin-top:28px}
.gate ul{padding:0;margin:12px 0}
.gate li{list-style:none;padding:10px 0;border-top:1px solid var(--line)}
.gate li label{display:flex;gap:10px;margin:0;font-weight:500;align-items:flex-start}
.gate li input{margin-top:5px;accent-color:var(--brand)}
.prog{display:flex;align-items:center;gap:12px}.status{font-weight:700}
.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:12px}
.step{font-size:30px;font-weight:800;color:var(--gold)}
.tbl{overflow-x:auto}
table{border-collapse:collapse;width:100%;font-size:14px;min-width:640px}
th,td{text-align:left;padding:10px;border-bottom:1px solid var(--line)}
.ok{color:var(--ok);font-weight:700}.no{color:var(--bad);font-weight:700}
.note{margin-top:24px;font-size:13px;color:var(--muted)}
.hide{display:none!important}
.login{position:fixed;inset:0;background:var(--bg);z-index:20;overflow:auto;display:flex;align-items:center;justify-content:center;padding:16px}
.login .card{width:100%;max-width:440px;padding:24px}
.err{color:var(--bad);font-size:14px;margin-top:10px;min-height:20px}
.demo{background:var(--badbg);border:1px solid var(--gold);border-radius:8px;padding:10px 12px;font-size:13px;line-height:1.4;margin:12px 0 4px}
.fe{color:var(--bad);font-size:13px;margin-top:4px;display:none}
.login input.bad{border-color:var(--bad)}
.opt{font-weight:400;color:var(--muted)}
.welc{text-align:center;padding:20px 0}
.welc .tick{width:60px;height:60px;border-radius:50%;background:var(--brand);color:var(--brand-ink);display:grid;place-items:center;font-size:30px;margin:0 auto 14px}
</style>
</head>
<body>

<div class="login" id="login">
  <div class="card">
    <div id="lform">
      <div class="brand" style="margin-bottom:12px"><i></i>Mizan</div>
      <h2>Sign in to AI Trust Passport</h2>
      <p class="small">Sign in to pick and test AI models.</p>
      <div class="demo"><b>Demo access only.</b> This prototype is not connected to UAE PASS or any government system. Type fictional test details only.</div>
      <label for="lname">Full Name</label><input type="text" id="lname" autocomplete="off" placeholder="e.g. Test User">
      <div class="fe" id="e-lname">Please type something here.</div>
      <label for="lpass">UAE PASS <span class="opt">(demo)</span></label><input type="text" id="lpass" autocomplete="off" placeholder="Type anything">
      <div class="fe" id="e-lpass">Please type something here.</div>
      <label for="leid">Emirates ID <span class="opt">(demo)</span></label><input type="text" id="leid" autocomplete="off" placeholder="Type anything">
      <div class="fe" id="e-leid">Please type something here.</div>
      <label for="lemp">Employee ID <span class="opt">(demo)</span></label><input type="text" id="lemp" autocomplete="off" placeholder="Type anything">
      <div class="fe" id="e-lemp">Please type something here.</div>
      <div class="acts" style="margin-top:20px"><button class="btn" id="lgo" type="button">Sign in</button><button class="btn ghost" id="ldemo" type="button">Use demo account</button></div>
      <p class="note">Simulated access, not real identity verification. Nothing you type is checked or sent anywhere. Only your name is kept, on this device, for this session.</p>
    </div>
    <div class="welc hide" id="lwelcome" role="status" aria-live="polite">
      <div class="tick">✓</div>
      <h2>Welcome to AI Trust Passport!</h2>
      <p class="small" id="lwho"></p>
    </div>
  </div>
</div>

<div class="wrap" id="app">
  <div class="top">
    <div class="brand"><i></i>Mizan</div>
    <div class="who"><span id="who"></span><button class="btn ghost" id="theme" type="button">Theme</button><button class="btn ghost" id="out" type="button">Sign out</button></div>
  </div>
  <nav class="nav" aria-label="Pages">
    <button class="on" data-tab="select">Select a model</button>
    <button data-tab="bench">Benchmarks</button>
    <button data-tab="comp">Compliance</button>
    <button data-tab="uses">Use cases</button>
    <button data-tab="registry">Model registry</button>
    <button data-tab="how">How it works</button>
    <button data-tab="feedback">Feedback</button>
  </nav>

  <!-- TAB 1 -->
  <div id="t-select">
    <div class="hero">
      <svg viewBox="0 0 800 260" preserveAspectRatio="xMidYMax slice" aria-hidden="true">
        <defs><linearGradient id="sky" x1="0" y1="0" x2="0" y2="1"><stop offset="0" stop-color="#0b3a3a"/><stop offset="1" stop-color="#c7a24a"/></linearGradient></defs>
        <rect width="800" height="260" fill="url(#sky)"/><circle cx="640" cy="90" r="34" fill="#f5e3a8" opacity=".85"/>
        <g fill="#082322"><rect x="40" y="170" width="40" height="90"/><rect x="90" y="140" width="34" height="120"/><rect x="135" y="185" width="50" height="75"/><rect x="200" y="120" width="30" height="140"/><rect x="240" y="165" width="46" height="95"/><path d="M330 260V150l10-30 6-60 5 60 10 30v110z"/><rect x="380" y="150" width="40" height="110"/><rect x="430" y="110" width="36" height="150"/><rect x="478" y="175" width="52" height="85"/><rect x="545" y="135" width="38" height="125"/><rect x="595" y="180" width="44" height="80"/><rect x="650" y="150" width="34" height="110"/><rect x="695" y="190" width="60" height="70"/></g>
      </svg>
      <img src="images/hero.jpg" alt="" onerror="this.remove()">
      <div class="txt"><span class="kick">UAE Government AI</span><h1>Months of AI vetting. Done in minutes.</h1><p>Choose your role. Mizan checks every AI model against government standards, ranks the ones that pass, and blocks the rest, with the reason.</p><div class="badges"><span>80% faster evaluation</span><span>100% compliance gate</span><span>UAE AI Strategy 2031</span></div><button class="go" id="heroGo" type="button">Start now →</button></div>
    </div>

    <div class="sech" id="roleHead"><h2>Who are you?</h2></div>
<div class="roles">
<button class="rc" data-sc="0" type="button"><div class="ph"><svg viewBox="0 0 160 90" preserveAspectRatio="xMidYMid slice" aria-hidden="true"><rect width="160" height="90" fill="#0f4c4a"/><circle cx="80" cy="32" r="13" fill="#f1c27d"/><rect x="58" y="48" width="44" height="36" rx="10" fill="#e0b64a"/><path d="M80 52v14M74 58h12" stroke="#0f4c4a" stroke-width="3" stroke-linecap="round"/></svg><img src="images/director.jpg" alt="" onerror="this.remove()"></div><b>Project Director</b><span>Leads the project and team.</span></button>
<button class="rc" data-sc="1" type="button"><div class="ph"><svg viewBox="0 0 160 90" preserveAspectRatio="xMidYMid slice" aria-hidden="true"><rect width="160" height="90" fill="#b8860b"/><rect x="52" y="22" width="56" height="46" rx="6" fill="#12302f"/><rect x="66" y="35" width="28" height="20" rx="3" fill="#5fc2b8"/><path d="M60 14v8M72 14v8M88 14v8M100 14v8M60 68v8M72 68v8M88 68v8M100 68v8" stroke="#e6efed" stroke-width="3" stroke-linecap="round"/></svg><img src="images/cto.jpg" alt="" onerror="this.remove()"></div><b>CTO</b><span>Oversees technology.</span></button>
<button class="rc" data-sc="2" type="button"><div class="ph"><svg viewBox="0 0 160 90" preserveAspectRatio="xMidYMid slice" aria-hidden="true"><rect width="160" height="90" fill="#2d6a5f"/><path d="M80 12l32 12v22c0 18-14 30-32 36-18-6-32-18-32-36V24z" fill="#12302f"/><path d="M66 46l10 10 20-22" stroke="#e0b64a" stroke-width="6" fill="none" stroke-linecap="round" stroke-linejoin="round"/></svg><img src="images/governance.jpg" alt="" onerror="this.remove()"></div><b>AI Governance Officer</b><span>Ensures standards are met.</span></button>
</div>
<div class="scen"><span>Or try:</span>
      
      
      
      <button class="pill" data-sc="3">Highly sensitive citizen data</button>
    </div>

    <div class="metrics">
      <div class="card time"><div class="small">Evaluation time for your shortlist</div>
        <div class="row"><span class="lbl">Manual</span><div class="bar"><b id="bManual" style="width:100%"></b></div><span id="tManual">–</span></div>
        <div class="row"><span class="lbl">With Mizan</span><div class="bar"><b class="new" id="bNew" style="width:20%"></b></div><span id="tNew">–</span></div></div>
      <div class="card"><div class="big">80%</div><div class="small">less evaluation time, because benchmarks and compliance checks are already on file for every registry model.</div></div>
      <div class="card"><div class="big" id="pass">–</div><div class="small">of registry models pass every mandatory control for your inputs. Only those can be deployed.</div></div>
    </div>

    <div class="main">
      <aside class="card side" aria-label="Your requirements">
        <h2>Your requirements</h2>
        <label class="first" for="uc">Use case</label>
        <select id="uc"><option value="chat">Citizen services chatbot</option><option value="summarize">Summarising government documents</option><option value="legal">Policy and regulation review</option><option value="translate">Arabic–English translation</option></select>
        <label for="cls">Data classification</label>
        <select id="cls"><option value="0">Public info</option><option value="1" selected>Internal government info</option><option value="2">Confidential records</option><option value="3">Highly sensitive</option></select>
        <label for="dep">Where it will run</label>
        <select id="dep"><option value="onprem">On-premises</option><option value="uaecloud" selected>UAE sovereign cloud</option><option value="public">Public cloud</option></select>
        <label>What matters most</label>
        <div class="sl">Answer quality</div><input type="range" id="wP" min="0" max="10" value="8" aria-label="Answer quality weight">
        <div class="sl">Speed</div><input type="range" id="wS" min="0" max="10" value="4" aria-label="Speed weight">
        <div class="sl">Low cost</div><input type="range" id="wC" min="0" max="10" value="3" aria-label="Cost weight">
        <p style="margin-top:14px"><button class="pill" id="more" type="button">Show more options</button></p>
        <div id="extra" class="hide">
          <label class="chk"><input type="checkbox" id="fUae"> UAE-built models only</label>
          <label class="chk"><input type="checkbox" id="fCert"> Security-certified only</label>
        </div>
      </aside>
      <section aria-live="polite"><h2>Ranked models</h2><div id="list"></div></section>
    </div>

    <section class="card gate hide" id="gate">
      <h2 id="gateTitle">Deployment gate</h2>
      <p class="small">Every item is mandatory. Deployment stays locked until all are confirmed.</p>
      <ul id="checks"></ul>
      <div class="prog"><span class="status" id="gstat"></span><button class="btn" id="deploy" type="button" disabled>Approve for deployment</button></div>
    </section>
  </div>

  <!-- NEW TABS -->
  <div id="t-bench" class="hide">
    <h2>Performance benchmarks</h2>
    <p class="lead" style="margin-bottom:16px">Answer quality for each government use case, plus speed and cost efficiency. Scores are out of 100.</p>
    <div class="card tbl"><table id="benchT"></table></div>
  </div>
  <div id="t-comp" class="hide">
    <h2>Compliance frameworks</h2>
    <p class="lead" style="margin-bottom:16px">The controls every model is checked against, and how many registry models currently meet each one.</p>
    <div class="grid" id="compG"></div>
    <p class="small" style="margin-top:14px">Mandatory for deployment: data residency, audit logging and bias testing. The other controls raise or lower a model’s standing.</p>
  </div>
  <div id="t-uses" class="hide">
    <h2>Government use case repository</h2>
    <p class="lead" style="margin-bottom:16px">Verified starting points from other entities. Tap one to load it into the model selector.</p>
    <div class="grid" id="useG"></div>
  </div>

  <!-- TAB 2 -->
  <div id="t-registry" class="hide">
    <h2>Approved model registry</h2>
    <p class="lead" style="margin-bottom:16px">Every model with its approved data level, hosting options and compliance controls.</p>
    <div class="card tbl"><table id="reg"></table></div>
  </div>

  <!-- TAB 3 -->
  <div id="t-how" class="hide">
    <h2>How it works</h2>
    <div class="grid" style="margin-bottom:24px">
      <div class="card"><div class="step">1</div><h3>Describe your need</h3><p class="small">Use case, data sensitivity, where it runs, and what matters most.</p></div>
      <div class="card"><div class="step">2</div><h3>Mizan filters</h3><p class="small">Models that break a mandatory rule are blocked, with the reason.</p></div>
      <div class="card"><div class="step">3</div><h3>Mizan ranks</h3><p class="small">Passing models get a fit score. UAE-built models get a small boost.</p></div>
      <div class="card"><div class="step">4</div><h3>Pass the gate</h3><p class="small">Deployment unlocks only when every checklist item is confirmed.</p></div>
    </div>
    <h2>Policy alignment</h2>
    <div class="grid">
      <div class="card"><h3>UAE National Strategy for AI 2031</h3><p class="small">Supports faster government adoption of AI and favours UAE-built models, which strengthens the national AI ecosystem.</p></div>
      <div class="card"><h3>UAE AI Governance Framework</h3><p class="small">Controls map to privacy, security, transparency and fairness: data residency, audit logging, bias testing and security certification.</p></div>
      <div class="card"><h3>Use case repository</h3><p class="small">Each entity’s chosen use case and result is saved, so the next entity with the same need starts from a verified shortlist.</p></div>
    </div>
  </div>

  <!-- TAB 4 -->
  <div id="t-feedback" class="hide">
    <h2>Test it and tell us</h2>
    <p class="lead" style="margin-bottom:16px">Tried Mizan? Rate it and tell us what was confusing or missing.</p>
    <div class="card" style="max-width:520px" id="fbox">
      <label class="first" for="rate">How easy was it?</label>
      <select id="rate"><option value="5">5 – Very easy</option><option value="4">4 – Easy</option><option value="3">3 – OK</option><option value="2">2 – Hard</option><option value="1">1 – Very hard</option></select>
      <label for="cmt">Comment</label><textarea id="cmt" rows="4"></textarea>
      <p style="margin-top:14px"><button class="btn" id="send" type="button">Send feedback</button></p>
    </div>
    <p class="small" id="fcount" style="margin-top:10px"></p>
  </div>

  <p class="note">All models, scores and compliance results on this page are sample data for demonstration. In production they come from the approved model registry, benchmark service and compliance framework APIs.</p>
</div>

<script>
var CLS=["Public","Internal","Confidential","Highly sensitive"];
var DEP={onprem:"On-premises",uaecloud:"UAE sovereign cloud",public:"Public cloud"};
var MODELS=[
 {n:"Falcon-H1 34B",v:"TII, UAE",uae:1,d:"Mid-size open model built in the UAE. Balanced quality and speed.",dep:["onprem","uaecloud","public"],max:3,c:{res:1,aud:1,pdpl:1,bias:1,cert:1},s:{chat:82,summarize:84,legal:76,translate:80},sp:80,co:4},
 {n:"Jais 70B",v:"Inception and MBZUAI, UAE",uae:1,d:"Large Arabic-focused model. Strongest on Arabic, slower to run.",dep:["onprem","uaecloud"],max:3,c:{res:1,aud:1,pdpl:1,bias:1,cert:1},s:{chat:88,summarize:82,legal:80,translate:90},sp:62,co:3},
 {n:"Llama 3.3 70B",v:"Meta, open weights",d:"Strong general model. Lacks a security certification on file.",dep:["onprem","uaecloud","public"],max:2,c:{res:1,aud:1,pdpl:1,bias:1,cert:0},s:{chat:85,summarize:86,legal:79,translate:78},sp:66,co:3},
 {n:"Falcon 3 7B",v:"TII, UAE",uae:1,d:"Small and very fast. Good for simple tasks at low cost.",dep:["onprem","uaecloud","public"],max:3,c:{res:1,aud:1,pdpl:1,bias:1,cert:1},s:{chat:66,summarize:68,legal:58,translate:64},sp:95,co:5},
 {n:"Mistral Large",v:"Mistral AI",d:"High quality, but no bias evaluation on file yet.",dep:["uaecloud","public"],max:1,c:{res:1,aud:1,pdpl:1,bias:0,cert:0},s:{chat:86,summarize:85,legal:82,translate:80},sp:70,co:2},
 {n:"Offshore frontier API",v:"Hosted outside the UAE",d:"Top scores, but data leaves the UAE, so it fails residency.",dep:["public"],max:0,c:{res:0,aud:1,pdpl:0,bias:1,cert:1},s:{chat:92,summarize:91,legal:88,translate:89},sp:85,co:2}
];
var CN={res:"Data stays in UAE",aud:"Audit logging",pdpl:"Data protection aligned",bias:"Bias tested",cert:"Security certified"};
var MAND=["res","aud","bias"];
var SC=[{uc:"chat",cls:1,dep:"uaecloud"},{uc:"summarize",cls:2,dep:"onprem"},{uc:"legal",cls:2,dep:"uaecloud"},{uc:"summarize",cls:3,dep:"onprem"}];
var $=function(i){return document.getElementById(i)};
var picked=null,fb=0;

/* ---------- demo sign in (fictional access only: no checks, no verification) ---------- */
var LF=["lname","lpass","leid","lemp"];
function enterSite(name){
 $("who").textContent=name;
 $("login").classList.add("hide");
}
function signIn(name){
 // Only the display name is kept (this session, this device). IDs are never stored or sent.
 try{sessionStorage.setItem("mizanUser",JSON.stringify([name]))}catch(e){}
 $("lform").classList.add("hide");
 $("lwelcome").classList.remove("hide");
 $("lwho").textContent=name;
 setTimeout(function(){enterSite(name)},1500);
}
$("lgo").addEventListener("click",function(){
 var ok=true;
 LF.forEach(function(i){
  var empty=!$(i).value.trim(); // only checks "not empty", never the format
  $(i).classList.toggle("bad",empty);
  $("e-"+i).style.display=empty?"block":"none";
  if(empty)ok=false;
 });
 if(ok)signIn($("lname").value.trim());
});
LF.forEach(function(i){$(i).addEventListener("input",function(){$(i).classList.remove("bad");$("e-"+i).style.display="none"})});
$("ldemo").addEventListener("click",function(){
 $("lname").value="Demo User";$("lpass").value="DEMO-UAEPASS";$("leid").value="000-0000-0000000-0";$("lemp").value="EMP-0000";
 signIn("Demo User");
});
$("out").addEventListener("click",function(){
 try{sessionStorage.removeItem("mizanUser")}catch(e){}
 LF.forEach(function(i){$(i).value="";$(i).classList.remove("bad");$("e-"+i).style.display="none"});
 $("lwelcome").classList.add("hide");$("lform").classList.remove("hide");
 $("login").classList.remove("hide");
});
try{var u=JSON.parse(sessionStorage.getItem("mizanUser")||"null");if(u&&u[0])enterSite(u[0])}catch(e){}

/* ---------- tabs ---------- */
document.querySelectorAll(".nav button").forEach(function(b){
 b.addEventListener("click",function(){
  document.querySelectorAll(".nav button").forEach(function(x){x.classList.toggle("on",x===b)});
  document.querySelectorAll('[id^="t-"]').forEach(function(p){p.classList.toggle("hide",p.id!=="t-"+b.getAttribute("data-tab"))});
 });
});

/* ---------- evaluate and render ---------- */
function evaluate(){
 var uc=$("uc").value,cls=+$("cls").value,dep=$("dep").value;
 var wP=+$("wP").value,wS=+$("wS").value,wC=+$("wC").value,tot=(wP+wS+wC)||1;
 return MODELS.map(function(m,i){
  var why=[];
  if(m.dep.indexOf(dep)<0)why.push("Not available on "+DEP[dep].toLowerCase()+".");
  if(cls>m.max)why.push("Not approved for "+CLS[cls].toLowerCase()+" data (limit: "+CLS[m.max].toLowerCase()+").");
  MAND.forEach(function(k){if(!m.c[k]&&(k!=="res"||cls>0))why.push("Missing control: "+CN[k].toLowerCase()+".")});
  if($("fUae").checked&&!m.uae)why.push("Not UAE-built.");
  if($("fCert").checked&&!m.c.cert)why.push("No security certification.");
  var fit=Math.round((m.s[uc]*wP+m.sp*wS+m.co*20*wC)/tot+(m.uae?2:0));
  return {i:i,m:m,why:why,fit:Math.min(fit,99),uc:m.s[uc]};
 }).sort(function(a,b){return (a.why.length>0)-(b.why.length>0)||b.fit-a.fit});
}
function render(){
 var r=evaluate(),ok=r.filter(function(x){return !x.why.length}),h="";
 r.forEach(function(x){
  var m=x.m,bl=x.why.length>0;
  h+='<article class="m'+(bl?' blocked':'')+'"><div><h3>'+m.n+'</h3><div class="vendor">'+m.v+'</div></div>';
  h+=bl?'<div class="score small">Blocked</div>':'<div class="score"><div class="big">'+x.fit+'</div><div class="small">fit score</div></div>';
  h+='<div class="chips">'+Object.keys(CN).map(function(k){return '<span class="chip '+(m.c[k]?'y':'n')+'">'+(m.c[k]?'Pass: ':'Fail: ')+CN[k]+'</span>'}).join("")+'</div>';
  if(bl)h+='<div class="why">'+x.why.join(" ")+'</div>';
  else h+='<div class="perf"><div>Use-case accuracy '+x.uc+'<div class="bar"><b class="new" style="width:'+x.uc+'%"></b></div></div><div>Speed '+m.sp+'<div class="bar"><b class="new" style="width:'+m.sp+'%"></b></div></div><div>Cost efficiency '+m.co*20+'<div class="bar"><b class="new" style="width:'+m.co*20+'%"></b></div></div></div>';
  h+='<div class="det hide" id="det'+x.i+'">'+m.d+' Approved up to '+CLS[m.max].toLowerCase()+' data. Hosting: '+m.dep.map(function(d){return DEP[d]}).join(", ")+'.</div>';
  h+='<div class="acts">'+(bl?'':'<button class="btn" type="button" data-pick="'+m.n+'">'+(picked===m.n?'Selected':'Select for deployment')+'</button>')+'<button class="btn ghost" type="button" data-det="'+x.i+'">Details</button></div>';
  h+='</article>';
 });
 $("list").innerHTML=h;
 var n=Math.min(ok.length,3),man=n*10,neu=n*2;
 $("tManual").textContent=man+" days";$("tNew").textContent=neu+" days";
 $("bNew").style.width=man?"20%":"0";$("bManual").style.width=man?"100%":"0";
 $("pass").textContent=ok.length+" of "+MODELS.length;
 if(picked&&!ok.some(function(x){return x.m.n===picked})){picked=null;$("gate").classList.add("hide")}
}

/* ---------- registry table ---------- */
(function(){
 var h="<tr><th>Model</th><th>Maker</th><th>Max data level</th><th>Hosting</th>"+Object.keys(CN).map(function(k){return"<th>"+CN[k]+"</th>"}).join("")+"</tr>";
 MODELS.forEach(function(m){
  h+="<tr><td><b>"+m.n+"</b></td><td>"+m.v+"</td><td>"+CLS[m.max]+"</td><td>"+m.dep.map(function(d){return DEP[d]}).join(", ")+"</td>"+Object.keys(CN).map(function(k){return m.c[k]?'<td class="ok">Pass</td>':'<td class="no">Fail</td>'}).join("")+"</tr>";
 });
 $("reg").innerHTML=h;
})();

/* ---------- benchmarks, compliance, use cases ---------- */
function bb(v){return '<div class="bar" style="height:6px;margin-top:3px"><b class="new" style="width:'+v+'%"></b></div>'}
(function(){
 var h="<tr><th>Model</th><th>Citizen chatbot</th><th>Summarising</th><th>Policy review</th><th>Translation</th><th>Speed</th><th>Cost efficiency</th></tr>";
 MODELS.forEach(function(m){
  var v=[m.s.chat,m.s.summarize,m.s.legal,m.s.translate,m.sp,m.co*20];
  h+="<tr><td><b>"+m.n+"</b><div class='small'>"+m.v+"</div></td>"+v.map(function(x){return "<td>"+x+bb(x)+"</td>"}).join("")+"</tr>";
 });
 $("benchT").innerHTML=h;
 var CD={res:["Privacy","Government data never leaves the UAE."],aud:["Security","Every request is logged for review."],pdpl:["Privacy","Aligned with UAE data protection law."],bias:["Fairness","Tested for unfair outcomes on sample data."],cert:["Security","Independent security certification on file."]};
 $("compG").innerHTML=Object.keys(CN).map(function(k){
  var n=MODELS.filter(function(m){return m.c[k]}).length,man=MAND.indexOf(k)>-1;
  return '<div class="card"><div class="small">'+CD[k][0]+(man?' · Mandatory':'')+'</div><h3>'+CN[k]+'</h3><p class="small">'+CD[k][1]+'</p><div class="big" style="margin-top:10px">'+n+' of '+MODELS.length+'</div><div class="small">models pass</div></div>';
 }).join("");
})();
var USES=[
 {t:"Citizen services chatbot",d:"Answers public questions about services, in Arabic and English.",uc:"chat",cls:1,dep:"uaecloud",m:"Falcon-H1 34B"},
 {t:"Document summarisation",d:"Summarises long internal reports and briefings.",uc:"summarize",cls:2,dep:"onprem",m:"Jais 70B"},
 {t:"Policy and regulation review",d:"Compares draft policies against existing regulations.",uc:"legal",cls:2,dep:"uaecloud",m:"Falcon-H1 34B"},
 {t:"Arabic–English translation",d:"Translates public notices and press material.",uc:"translate",cls:0,dep:"public",m:"Falcon-H1 34B"},
 {t:"Contract analysis",d:"Flags risks and missing clauses in procurement contracts.",uc:"legal",cls:3,dep:"onprem",m:"Jais 70B"},
 {t:"Internal knowledge assistant",d:"Helps staff find answers in internal guidance.",uc:"chat",cls:1,dep:"onprem",m:"Falcon 3 7B"}
];
$("useG").innerHTML=USES.map(function(u,i){
 return '<div class="card"><h3>'+u.t+'</h3><p class="small">'+u.d+'</p><p class="small" style="margin-top:8px"><b>'+CLS[u.cls]+'</b> data · '+DEP[u.dep]+'</p><p class="small">Verified pick: <b>'+u.m+'</b></p><p style="margin-top:12px"><button class="btn" type="button" data-use="'+i+'">Use this</button></p></div>';
}).join("");
document.addEventListener("click",function(e){
 var b=e.target.closest("[data-use]");if(!b)return;
 var u=USES[+b.getAttribute("data-use")];
 $("uc").value=u.uc;$("cls").value=u.cls;$("dep").value=u.dep;render();
 document.querySelector('.nav button[data-tab="select"]').click();
 $("list").scrollIntoView({behavior:"smooth",block:"start"});
});

/* ---------- deployment gate ---------- */
function buildGate(name){
 picked=name;
 var items=["Use case and data classification recorded in the government use case repository","Model version matches the approved registry entry","Hosting location confirmed: "+DEP[$("dep").value].toLowerCase(),"Audit logging switched on and sent to the entity’s security team","Bias and accuracy test passed on a sample of the entity’s own data","Human review step defined for decisions that affect people","Named owner assigned for incident response"];
 $("gateTitle").textContent="Deployment gate: "+name;
 $("checks").innerHTML=items.map(function(t){return '<li><label><input type="checkbox">'+t+'</label></li>'}).join("");
 $("gate").classList.remove("hide");
 updGate();render();
 $("gate").scrollIntoView({behavior:"smooth",block:"nearest"});
}
function updGate(){
 var b=document.querySelectorAll("#checks input"),d=0;
 b.forEach(function(x){if(x.checked)d++});
 $("gstat").textContent=d+" of "+b.length+" confirmed";
 $("deploy").disabled=d<b.length;
 $("deploy").textContent="Approve for deployment";
}

/* ---------- events ---------- */
document.addEventListener("input",function(e){if(e.target.matches("#t-select select,#t-select input[type=range],#fUae,#fCert"))render()});
document.addEventListener("change",function(e){
 if(e.target.matches("#t-select select,#fUae,#fCert"))render();
 if(e.target.matches("#checks input"))updGate();
});
document.addEventListener("click",function(e){
 var t=e.target,p=t.closest("[data-pick]"),d=t.closest("[data-det]"),s=t.closest("[data-sc]");
 if(p)buildGate(p.getAttribute("data-pick"));
 if(d)$("det"+d.getAttribute("data-det")).classList.toggle("hide");
 if(s){var c=SC[+s.getAttribute("data-sc")];$("uc").value=c.uc;$("cls").value=c.cls;$("dep").value=c.dep;render();$("list").scrollIntoView({behavior:"smooth",block:"start"})}
 if(t===$("deploy"))$("deploy").textContent="Approved. Added to the registry log.";
 if(t===$("more")){var x=$("extra");x.classList.toggle("hide");t.textContent=x.classList.contains("hide")?"Show more options":"Hide extra options"}
 if(t===$("send")){fb++;$("fbox").innerHTML='<h3>Thank you!</h3><p class="small">Your feedback was recorded for this session.</p>';$("fcount").textContent="Feedback sent this session: "+fb}
});
$("theme").addEventListener("click",function(){
 var r=document.documentElement,dark=r.getAttribute("data-theme")==="dark"||(!r.getAttribute("data-theme")&&matchMedia("(prefers-color-scheme:dark)").matches);
 r.setAttribute("data-theme",dark?"light":"dark");
});
$("heroGo").addEventListener("click",function(){$("roleHead").scrollIntoView({behavior:"smooth",block:"start"})});
(function(){var el=document.querySelector(".metrics .card:nth-child(2) .big");if(!el||matchMedia("(prefers-reduced-motion:reduce)").matches)return;var n=0,t=setInterval(function(){n+=4;if(n>=80){n=80;clearInterval(t)}el.textContent=n+"%"},30)})();
render();
</script>
</body>
</html