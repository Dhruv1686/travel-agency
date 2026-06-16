<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TOPS Technologies — IT Training & Placement</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Space+Grotesk:wght@400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
:root{
  --navy:#07091A;--navy2:#0C1026;
  --blue:#2563EB;--cyan:#06B6D4;--cyan2:#0EA5E9;
  --white:#F0F4FF;--grey:#8892A4;--grey2:#3A4460;
  --card-bg:rgba(255,255,255,0.035);
  --card-border:rgba(255,255,255,0.07);
}
html{scroll-behavior:smooth}
body{font-family:'Inter',sans-serif;background:var(--navy);color:var(--white);overflow-x:hidden;-webkit-font-smoothing:antialiased}

/* ─ NAV ─ */
nav{
  position:fixed;top:0;left:0;right:0;z-index:500;
  display:flex;align-items:center;justify-content:space-between;
  padding:0 4rem;height:68px;
  background:rgba(7,9,26,0.75);backdrop-filter:blur(20px);
  border-bottom:1px solid var(--card-border);
}
.nav-logo{font-family:'Space Grotesk',sans-serif;font-size:1.25rem;font-weight:700;color:var(--white);letter-spacing:-.02em}
.nav-logo span{color:var(--cyan)}
.nav-links{display:flex;gap:2rem;list-style:none}
.nav-links a{font-size:.85rem;font-weight:500;color:var(--grey);text-decoration:none;transition:color .2s}
.nav-links a:hover{color:var(--white)}
.nav-cta{background:var(--blue);color:#fff;border:none;border-radius:8px;padding:.5rem 1.25rem;font-size:.85rem;font-weight:600;cursor:pointer;transition:all .2s;text-decoration:none}
.nav-cta:hover{background:#1d4ed8;transform:translateY(-1px);box-shadow:0 6px 20px rgba(37,99,235,.4)}

/* ─ HERO ─ */
#hero{position:relative;min-height:100vh;display:flex;align-items:center;padding:0 4rem;overflow:hidden}
#hero-canvas{position:absolute;inset:0;width:100%;height:100%;z-index:0}
.hero-content{position:relative;z-index:2;max-width:700px}
.hero-eyebrow{
  display:inline-flex;align-items:center;gap:.5rem;
  background:rgba(6,182,212,.08);border:1px solid rgba(6,182,212,.22);
  border-radius:100px;padding:.32rem 1rem;
  font-size:.72rem;font-weight:700;color:var(--cyan);letter-spacing:.08em;text-transform:uppercase;margin-bottom:1.8rem
}
.hero-eyebrow::before{content:'';width:5px;height:5px;border-radius:50%;background:var(--cyan);animation:pdot 2s ease-in-out infinite}
@keyframes pdot{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.3;transform:scale(.6)}}
.hero h1{
  font-family:'Space Grotesk',sans-serif;
  font-size:clamp(2.8rem,5.5vw,4.8rem);font-weight:700;
  line-height:1.04;letter-spacing:-.03em;margin-bottom:1.4rem
}
.hero h1 em{
  font-style:normal;
  background:linear-gradient(130deg,var(--cyan) 0%,var(--cyan2) 40%,var(--blue) 100%);
  -webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text
}
.hero-sub{font-size:1.05rem;line-height:1.8;color:var(--grey);max-width:480px;margin-bottom:2.4rem}
.hero-actions{display:flex;gap:1rem;flex-wrap:wrap}
.btn-primary{
  background:var(--blue);color:#fff;border:none;border-radius:10px;
  padding:.82rem 2rem;font-size:.95rem;font-weight:600;cursor:pointer;
  transition:all .25s;text-decoration:none;display:inline-block;letter-spacing:.01em
}
.btn-primary:hover{background:#1d4ed8;transform:translateY(-2px);box-shadow:0 10px 35px rgba(37,99,235,.5)}
.btn-secondary{
  background:transparent;color:var(--white);border:1px solid var(--card-border);
  border-radius:10px;padding:.82rem 2rem;font-size:.95rem;font-weight:500;
  cursor:pointer;transition:all .25s;text-decoration:none;display:inline-block
}
.btn-secondary:hover{border-color:rgba(255,255,255,.18);background:rgba(255,255,255,.04)}

/* stats strip */
.stats-strip{
  display:grid;grid-template-columns:repeat(4,1fr);gap:1px;margin-top:4.5rem;
  background:var(--card-border);border:1px solid var(--card-border);border-radius:16px;overflow:hidden;
  position:relative;z-index:2
}
.stat-item{background:rgba(7,9,26,.55);backdrop-filter:blur(16px);padding:1.5rem 1.7rem;transition:background .25s}
.stat-item:hover{background:rgba(37,99,235,.1)}
.stat-num{font-family:'Space Grotesk',sans-serif;font-size:2rem;font-weight:700;color:var(--white);letter-spacing:-.03em;line-height:1}
.stat-num span{color:var(--cyan)}
.stat-label{font-size:.75rem;color:var(--grey);margin-top:.4rem;font-weight:500}

/* ─ TICKER ─ */
.ticker-wrap{overflow:hidden;padding:1.4rem 0;background:var(--navy);border-top:1px solid var(--card-border);border-bottom:1px solid var(--card-border)}
.ticker-inner{display:flex;gap:2rem;width:max-content;animation:tick 50s linear infinite}
.ticker-inner:hover{animation-play-state:paused}
@keyframes tick{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}
.chip{display:flex;align-items:center;gap:.55rem;background:var(--card-bg);border:1px solid var(--card-border);border-radius:100px;padding:.32rem .85rem;white-space:nowrap}
.chip .av{width:22px;height:22px;border-radius:50%;flex-shrink:0;background:linear-gradient(135deg,var(--blue),var(--cyan));display:flex;align-items:center;justify-content:center;font-size:.55rem;font-weight:700;color:#fff}
.chip .nm{font-size:.74rem;font-weight:500;color:var(--white)}
.chip .rl{font-size:.68rem;color:var(--cyan)}

/* ─ SHARED SECTION ─ */
.section{padding:7rem 4rem;position:relative;overflow:hidden}
.section-alt{background:var(--navy2)}
.section-tag{font-size:.7rem;font-weight:700;letter-spacing:.1em;text-transform:uppercase;color:var(--cyan);margin-bottom:.7rem}
.section-title{font-family:'Space Grotesk',sans-serif;font-size:clamp(1.85rem,3.8vw,2.9rem);font-weight:700;letter-spacing:-.025em;color:var(--white);line-height:1.1;margin-bottom:.9rem}
.section-sub{font-size:.97rem;color:var(--grey);line-height:1.72;max-width:500px}
.section-header{margin-bottom:3.5rem;position:relative;z-index:2}

/* ─ COURSES ─ */
.courses-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(255px,1fr));gap:1.4rem;position:relative;z-index:2}
.course-card{
  background:var(--card-bg);border:1px solid var(--card-border);border-radius:14px;padding:1.75rem;
  cursor:pointer;transform-style:preserve-3d;will-change:transform;
  transition:border-color .3s,box-shadow .3s
}
.course-card:hover{border-color:rgba(37,99,235,.4);box-shadow:0 24px 60px rgba(0,0,0,.5),0 0 0 1px rgba(37,99,235,.12),inset 0 1px 0 rgba(255,255,255,.05)}
.course-icon{width:44px;height:44px;border-radius:10px;background:rgba(37,99,235,.14);display:flex;align-items:center;justify-content:center;margin-bottom:1rem;font-size:1.3rem}
.course-name{font-family:'Space Grotesk',sans-serif;font-size:.97rem;font-weight:600;color:var(--white);margin-bottom:.4rem}
.course-desc{font-size:.78rem;color:var(--grey);line-height:1.55}
.course-tag{display:inline-block;margin-top:.85rem;font-size:.66rem;font-weight:700;letter-spacing:.05em;text-transform:uppercase;color:var(--cyan);background:rgba(6,182,212,.1);border-radius:4px;padding:.18rem .48rem}

/* ─ WHY ─ */
.why-grid{display:grid;grid-template-columns:1fr 1fr;gap:3rem;align-items:center;position:relative;z-index:2}
.why-features{display:flex;flex-direction:column;gap:1.1rem}
.feature-item{display:flex;gap:1rem;align-items:flex-start;padding:1.25rem 1.5rem;background:var(--card-bg);border:1px solid var(--card-border);border-radius:12px;transition:border-color .2s,transform .25s;cursor:default}
.feature-item:hover{border-color:rgba(37,99,235,.3);transform:translateX(5px)}
.feature-icon{width:40px;height:40px;border-radius:8px;flex-shrink:0;background:rgba(37,99,235,.14);display:flex;align-items:center;justify-content:center;font-size:1.1rem}
.feature-text h4{font-family:'Space Grotesk',sans-serif;font-size:.9rem;font-weight:600;color:var(--white);margin-bottom:.22rem}
.feature-text p{font-size:.78rem;color:var(--grey);line-height:1.52}

/* why-3d panel */
.why-3d-panel{position:relative;border-radius:20px;overflow:hidden;background:var(--card-bg);border:1px solid var(--card-border)}
#why-canvas{width:100%;display:block;aspect-ratio:1/1}
.why-overlay{
  position:absolute;bottom:0;left:0;right:0;
  padding:1.8rem;
  background:linear-gradient(to top,rgba(7,9,26,.95) 0%,rgba(7,9,26,.5) 60%,transparent 100%)
}
.bar-row{margin-bottom:.9rem}
.bar-row:last-child{margin-bottom:0}
.placement-bar-label{display:flex;justify-content:space-between;margin-bottom:.38rem}
.placement-bar-label span:first-child{font-size:.78rem;font-weight:500;color:var(--white)}
.placement-bar-label span:last-child{font-size:.78rem;font-weight:700;color:var(--cyan)}
.bar-track{background:rgba(255,255,255,.07);border-radius:100px;height:4px;overflow:hidden}
.bar-fill{height:100%;border-radius:100px;background:linear-gradient(90deg,var(--blue),var(--cyan));transform:scaleX(0);transform-origin:left;transition:transform 1.4s cubic-bezier(.4,0,.2,1)}
.bar-fill.go{transform:scaleX(1)}

/* ─ GLOBE SECTION ─ */
.globe-section{position:relative;min-height:560px;display:flex;align-items:center}
#globe-canvas{position:absolute;right:0;top:0;bottom:0;width:55%;pointer-events:none}
.globe-content{position:relative;z-index:2;max-width:480px}
.globe-stats{display:flex;gap:1.5rem;margin-top:2.5rem;flex-wrap:wrap}
.gstat{background:var(--card-bg);border:1px solid var(--card-border);border-radius:12px;padding:1.1rem 1.5rem}
.gstat-num{font-family:'Space Grotesk',sans-serif;font-size:1.6rem;font-weight:700;color:var(--white);letter-spacing:-.02em}
.gstat-num span{color:var(--cyan)}
.gstat-label{font-size:.72rem;color:var(--grey);margin-top:.2rem}

/* ─ JOBFEST ─ */
.jf-wrapper{
  background:linear-gradient(130deg,rgba(37,99,235,.12),rgba(6,182,212,.07));
  border:1px solid rgba(37,99,235,.18);border-radius:20px;
  padding:4rem;display:flex;gap:4rem;align-items:center;
  position:relative;overflow:hidden;z-index:2
}
.jf-text{flex:1}
.jf-num{font-family:'Space Grotesk',sans-serif;font-size:5rem;font-weight:700;letter-spacing:-.04em;line-height:1;background:linear-gradient(135deg,var(--cyan),var(--blue));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.jf-label{font-size:.82rem;color:var(--grey);margin-top:.5rem}
#jf-canvas{position:absolute;inset:0;width:100%;height:100%;pointer-events:none;opacity:.5}

/* ─ TESTIMONIALS ─ */
.t-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:1.4rem;position:relative;z-index:2}
.t-card{background:var(--card-bg);border:1px solid var(--card-border);border-radius:14px;padding:1.75rem;transform-style:preserve-3d;will-change:transform;transition:border-color .25s}
.t-card:hover{border-color:rgba(6,182,212,.25)}
.t-stars{color:#F59E0B;font-size:.82rem;margin-bottom:.75rem}
.t-text{font-size:.85rem;color:var(--grey);line-height:1.68;margin-bottom:1.1rem}
.t-author{display:flex;align-items:center;gap:.7rem}
.t-avatar{width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,var(--blue),var(--cyan));display:flex;align-items:center;justify-content:center;font-size:.7rem;font-weight:700;color:#fff;flex-shrink:0}
.t-name{font-size:.85rem;font-weight:600;color:var(--white)}
.t-role{font-size:.72rem;color:var(--grey)}

/* ratings */
.ratings-row{display:flex;gap:1.2rem;flex-wrap:wrap;margin-bottom:3rem}
.r-badge{display:flex;align-items:center;gap:.7rem;background:var(--card-bg);border:1px solid var(--card-border);border-radius:10px;padding:.75rem 1.1rem}
.r-platform{font-size:.7rem;font-weight:700;letter-spacing:.06em;text-transform:uppercase;color:var(--grey)}
.r-score{font-family:'Space Grotesk',sans-serif;font-size:1.05rem;font-weight:700;color:var(--white)}
.r-stars{color:#F59E0B;font-size:.75rem}
.r-count{font-size:.7rem;color:var(--grey)}

/* ─ LOCATIONS ─ */
.loc-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(210px,1fr));gap:1rem;position:relative;z-index:2}
.loc-card{background:var(--card-bg);border:1px solid var(--card-border);border-radius:12px;padding:1.3rem 1.5rem;transition:all .25s;cursor:pointer;transform-style:preserve-3d;will-change:transform}
.loc-card:hover{border-color:rgba(37,99,235,.35);background:rgba(37,99,235,.06)}
.loc-pin{font-size:1.1rem;margin-bottom:.5rem}
.loc-city{font-family:'Space Grotesk',sans-serif;font-size:.95rem;font-weight:600;color:var(--white)}
.loc-area{font-size:.7rem;color:var(--grey2);margin-top:.12rem}
.loc-phone{font-size:.75rem;color:var(--grey);margin-top:.3rem}

/* ─ CTA ─ */
.cta-section{position:relative;padding:8rem 4rem;text-align:center;overflow:hidden}
#cta-canvas{position:absolute;inset:0;width:100%;height:100%;pointer-events:none}
.cta-inner{position:relative;z-index:2;max-width:560px;margin:0 auto}
.cta-form{display:flex;flex-direction:column;gap:.9rem;max-width:380px;margin:0 auto}
.cta-form input{background:rgba(255,255,255,.05);border:1px solid var(--card-border);border-radius:10px;padding:.85rem 1.1rem;font-size:.88rem;color:var(--white);font-family:'Inter',sans-serif;outline:none;transition:border-color .2s}
.cta-form input::placeholder{color:var(--grey2)}
.cta-form input:focus{border-color:rgba(37,99,235,.5)}
.addr-row{display:flex;justify-content:center;gap:3rem;flex-wrap:wrap;margin-top:3rem}
.addr-item{text-align:center}
.addr-label{font-size:.7rem;letter-spacing:.07em;text-transform:uppercase;color:var(--grey);margin-bottom:.35rem;font-weight:600}
.addr-val{font-size:.88rem;color:var(--white);line-height:1.55}

/* ─ FOOTER ─ */
footer{background:var(--navy2);border-top:1px solid var(--card-border);padding:2.5rem 4rem;display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:1rem}
.f-logo{font-family:'Space Grotesk',sans-serif;font-size:1.05rem;font-weight:700;color:var(--white)}
.f-logo span{color:var(--cyan)}
.f-links{display:flex;gap:1.5rem;flex-wrap:wrap}
.f-links a{font-size:.78rem;color:var(--grey);text-decoration:none;transition:color .2s}
.f-links a:hover{color:var(--white)}
.f-copy{font-size:.75rem;color:var(--grey2)}

/* ─ REVEAL ─ */
.reveal{opacity:0;transform:translateY(28px);transition:opacity .65s ease,transform .65s ease}
.reveal.visible{opacity:1;transform:translateY(0)}
.rd1{transition-delay:.1s}.rd2{transition-delay:.2s}.rd3{transition-delay:.3s}

/* ─ MOBILE ─ */
@media(max-width:900px){
  nav{padding:0 1.4rem} .nav-links{display:none}
  #hero{padding:100px 1.5rem 4rem}
  .stats-strip{grid-template-columns:repeat(2,1fr)}
  .section{padding:5rem 1.5rem}
  .why-grid,.t-grid{grid-template-columns:1fr}
  #globe-canvas{display:none}
  .jf-wrapper{flex-direction:column;padding:2.5rem;gap:2rem}
  footer{flex-direction:column;padding:2rem 1.5rem;text-align:center}
  .cta-section{padding:5rem 1.5rem}
  .addr-row{gap:1.5rem}
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">TOPS<span>+</span></div>
  <ul class="nav-links">
    <li><a href="#courses">Courses</a></li>
    <li><a href="#why">Why TOPS</a></li>
    <li><a href="#placement">Placement</a></li>
    <li><a href="#locations">Locations</a></li>
  </ul>
  <a href="#contact" class="nav-cta">Get Started</a>
</nav>

<!-- HERO -->
<section id="hero">
  <canvas id="hero-canvas"></canvas>
  <div class="hero-content">
    <div class="hero-eyebrow">15 Years of IT Training Excellence</div>
    <h1>Build your career<br>in <em>technology</em><br>— for real.</h1>
    <p class="hero-sub">Practical, job-ready IT training with live projects, expert faculty, and direct connections to 3000+ hiring companies across India.</p>
    <div class="hero-actions">
      <a href="#courses" class="btn-primary">Explore Courses →</a>
      <a href="#contact" class="btn-secondary">Talk to us</a>
    </div>
    <div class="stats-strip reveal">
      <div class="stat-item"><div class="stat-num" data-target="100000">0<span>+</span></div><div class="stat-label">Students Placed</div></div>
      <div class="stat-item"><div class="stat-num" data-target="3000">0<span>+</span></div><div class="stat-label">Company Tie-Ups</div></div>
      <div class="stat-item"><div class="stat-num" data-target="50">0<span>+</span></div><div class="stat-label">Industry Courses</div></div>
      <div class="stat-item"><div class="stat-num" data-target="19">0<span>+</span></div><div class="stat-label">Offices in India</div></div>
    </div>
  </div>
</section>

<!-- TICKER -->
<div class="ticker-wrap"><div class="ticker-inner" id="ticker"></div></div>

<!-- COURSES -->
<section class="section" id="courses">
  <div class="section-header reveal">
    <div class="section-tag">What we teach</div>
    <h2 class="section-title">50+ career-ready courses</h2>
    <p class="section-sub">From foundations to advanced specializations — every course is designed around what companies actually hire for.</p>
  </div>
  <div class="courses-grid reveal">
    <div class="course-card"><div class="course-icon">🐍</div><div class="course-name">Python Development</div><div class="course-desc">Django, FastAPI, scripting, and automation pipelines.</div><span class="course-tag">Software Dev</span></div>
    <div class="course-card"><div class="course-icon">⚡</div><div class="course-name">Full Stack Development</div><div class="course-desc">React + Node.js + databases — end-to-end web engineering.</div><span class="course-tag">Full Stack</span></div>
    <div class="course-card"><div class="course-icon">🎨</div><div class="course-name">UI/UX Design</div><div class="course-desc">Figma, design systems, user research, and prototyping.</div><span class="course-tag">Design</span></div>
    <div class="course-card"><div class="course-icon">📊</div><div class="course-name">Data Science & AI/ML</div><div class="course-desc">Machine learning, neural networks, and real-world datasets.</div><span class="course-tag">AI & Data</span></div>
    <div class="course-card"><div class="course-icon">📱</div><div class="course-name">Flutter & Mobile Dev</div><div class="course-desc">Cross-platform app development for iOS and Android.</div><span class="course-tag">Mobile</span></div>
    <div class="course-card"><div class="course-icon">🔒</div><div class="course-name">Cyber Security</div><div class="course-desc">Ethical hacking, network defense, and penetration testing.</div><span class="course-tag">Security</span></div>
    <div class="course-card"><div class="course-icon">📈</div><div class="course-name">Digital Marketing</div><div class="course-desc">SEO, paid ads, analytics, and growth strategy.</div><span class="course-tag">Marketing</span></div>
    <div class="course-card"><div class="course-icon">🧪</div><div class="course-name">Software Testing</div><div class="course-desc">Manual & automation testing with Selenium and TestNG.</div><span class="course-tag">QA</span></div>
    <div class="course-card"><div class="course-icon">⚛️</div><div class="course-name">React / Angular</div><div class="course-desc">Modern frontend frameworks and state management.</div><span class="course-tag">Frontend</span></div>
    <div class="course-card"><div class="course-icon">🖼️</div><div class="course-name">Graphic Design</div><div class="course-desc">Adobe Suite, branding, and print & digital media.</div><span class="course-tag">Design</span></div>
    <div class="course-card"><div class="course-icon">🌐</div><div class="course-name">Web Designing</div><div class="course-desc">HTML, CSS, responsive layouts, and visual storytelling.</div><span class="course-tag">Design</span></div>
    <div class="course-card"><div class="course-icon">🏗️</div><div class="course-name">Java & ASP.NET</div><div class="course-desc">Enterprise-grade backend development and architecture.</div><span class="course-tag">Backend</span></div>
  </div>
</section>

<!-- WHY TOPS -->
<section class="section section-alt" id="why">
  <div class="why-grid">
    <div>
      <div class="section-header reveal">
        <div class="section-tag">Why students choose us</div>
        <h2 class="section-title">Training that actually gets you hired</h2>
        <p class="section-sub">Small batches, experienced mentors, live projects, and placement support from day one.</p>
      </div>
      <div class="why-features">
        <div class="feature-item reveal rd1"><div class="feature-icon">🎯</div><div class="feature-text"><h4>Job-Oriented Curriculum</h4><p>Syllabus built with hiring partners to match current requirements.</p></div></div>
        <div class="feature-item reveal rd2"><div class="feature-icon">🧑‍💻</div><div class="feature-text"><h4>Live Project Training</h4><p>Real-world projects from day one — build a portfolio, not just notes.</p></div></div>
        <div class="feature-item reveal rd3"><div class="feature-icon">🏅</div><div class="feature-text"><h4>NSDC / Skill India Certified</h4><p>Government-recognized certificates with international validity.</p></div></div>
        <div class="feature-item reveal"><div class="feature-icon">⏰</div><div class="feature-text"><h4>Flexible Batch Timings</h4><p>Morning, evening, and weekend batches for students and professionals.</p></div></div>
      </div>
    </div>
    <div class="why-3d-panel reveal">
      <canvas id="why-canvas"></canvas>
      <div class="why-overlay">
        <div class="bar-row"><div class="placement-bar-label"><span>Software Development</span><span>94%</span></div><div class="bar-track"><div class="bar-fill" data-w="0.94"></div></div></div>
        <div class="bar-row"><div class="placement-bar-label"><span>Data Science & AI</span><span>91%</span></div><div class="bar-track"><div class="bar-fill" data-w="0.91"></div></div></div>
        <div class="bar-row"><div class="placement-bar-label"><span>Design (UI/UX/Graphic)</span><span>88%</span></div><div class="bar-track"><div class="bar-fill" data-w="0.88"></div></div></div>
        <div class="bar-row"><div class="placement-bar-label"><span>Mobile Development</span><span>90%</span></div><div class="bar-track"><div class="bar-fill" data-w="0.90"></div></div></div>
        <div class="bar-row"><div class="placement-bar-label"><span>Digital Marketing</span><span>86%</span></div><div class="bar-track"><div class="bar-fill" data-w="0.86"></div></div></div>
      </div>
    </div>
  </div>
</section>

<!-- GLOBE / PLACEMENT -->
<section class="section globe-section" id="placement">
  <canvas id="globe-canvas"></canvas>
  <div class="globe-content">
    <div class="section-tag">Placement Network</div>
    <h2 class="section-title">3000+ companies.<br>Across India.</h2>
    <p class="section-sub">From Surat startups to Bangalore product companies — our placement network spans every major IT hub in the country.</p>
    <div class="globe-stats">
      <div class="gstat"><div class="gstat-num">1<span>L+</span></div><div class="gstat-label">Students Placed</div></div>
      <div class="gstat"><div class="gstat-num">7.2<span>L</span></div><div class="gstat-label">Max Fresher CTC</div></div>
      <div class="gstat"><div class="gstat-num">19<span>+</span></div><div class="gstat-label">Centers Pan-India</div></div>
    </div>
    <a href="#contact" class="btn-primary" style="margin-top:2rem;display:inline-block">Register for JobFest →</a>
  </div>
</section>

<!-- JOBFEST -->
<section class="section section-alt">
  <div class="jf-wrapper">
    <canvas id="jf-canvas"></canvas>
    <div class="jf-text reveal">
      <div class="section-tag">JobFest</div>
      <h2 class="section-title" style="max-width:380px">Meet your employer in one day</h2>
      <p style="font-size:.97rem;line-height:1.8;color:var(--grey);max-width:460px;margin-top:.5rem">TOPS organizes exclusive <strong style="color:var(--white)">JobFest</strong> events at convention centers — bringing 50+ companies together to interview hundreds of candidates simultaneously. One event. Maximum offers.</p>
      <div style="display:flex;gap:2rem;margin-top:2rem;flex-wrap:wrap">
        <div><div style="font-family:'Space Grotesk',sans-serif;font-size:1.6rem;font-weight:700;color:var(--white);letter-spacing:-.02em">50<span style="color:var(--cyan)">+</span></div><div style="font-size:.72rem;color:var(--grey);margin-top:.2rem">Companies per event</div></div>
        <div><div style="font-family:'Space Grotesk',sans-serif;font-size:1.6rem;font-weight:700;color:var(--white);letter-spacing:-.02em">3000<span style="color:var(--cyan)">+</span></div><div style="font-size:.72rem;color:var(--grey);margin-top:.2rem">Company tie-ups nationwide</div></div>
      </div>
    </div>
    <div class="reveal" style="text-align:center;flex-shrink:0">
      <div class="jf-num">₹7.2L</div>
      <div class="jf-label">Max CTC for a fresher<br>at TOPS JobFest</div>
    </div>
  </div>
</section>

<!-- TESTIMONIALS -->
<section class="section">
  <div class="section-header reveal">
    <div class="section-tag">Reviews</div>
    <h2 class="section-title">What our students say</h2>
    <div class="ratings-row">
      <div class="r-badge"><div><div class="r-platform">Google</div><div style="display:flex;align-items:center;gap:.35rem;margin-top:.12rem"><div class="r-score">4.5</div><div class="r-stars">★★★★½</div></div><div class="r-count">1,038 reviews</div></div></div>
      <div class="r-badge"><div><div class="r-platform">Facebook</div><div style="display:flex;align-items:center;gap:.35rem;margin-top:.12rem"><div class="r-score">4.7</div><div class="r-stars">★★★★★</div></div><div class="r-count">312 reviews</div></div></div>
      <div class="r-badge"><div><div class="r-platform">JustDial</div><div style="display:flex;align-items:center;gap:.35rem;margin-top:.12rem"><div class="r-score">4.3</div><div class="r-stars">★★★★</div></div><div class="r-count">984 reviews</div></div></div>
    </div>
  </div>
  <div class="t-grid">
    <div class="t-card reveal rd1"><div class="t-stars">★★★★★</div><p class="t-text">"The live project training gave me a portfolio before I even finished the course. I got placed at a product company with a package I wasn't expecting as a fresher."</p><div class="t-author"><div class="t-avatar">YS</div><div><div class="t-name">Yash Saradva</div><div class="t-role">React Developer</div></div></div></div>
    <div class="t-card reveal rd2"><div class="t-stars">★★★★★</div><p class="t-text">"TOPS isn't just a coaching class — the faculty genuinely mentors you. I switched careers from non-IT to data analytics in 6 months with their full support."</p><div class="t-author"><div class="t-avatar">NA</div><div><div class="t-name">Nishi Amin</div><div class="t-role">Data Analytics</div></div></div></div>
    <div class="t-card reveal rd3"><div class="t-stars">★★★★★</div><p class="t-text">"The JobFest was a game-changer. I had four interviews in a single day and walked out with two offers. That kind of access doesn't happen anywhere else."</p><div class="t-author"><div class="t-avatar">DB</div><div><div class="t-name">Dipam Bhatt</div><div class="t-role">Automation Tester</div></div></div></div>
  </div>
</section>

<!-- LOCATIONS -->
<section class="section section-alt" id="locations">
  <div class="section-header reveal">
    <div class="section-tag">Our Centers</div>
    <h2 class="section-title">19+ offices across India</h2>
    <p class="section-sub">The same quality training, faculty, and placement support at every location.</p>
  </div>
  <div class="loc-grid reveal">
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Surat — Ring Road</div><div class="loc-area">Jeevandeep Complex, Sagrampura</div><div class="loc-phone">+91 70695 98828</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Ahmedabad — C.G. Road</div><div class="loc-area">Central location</div><div class="loc-phone">+91 99747 55006</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Ahmedabad — Maninagar</div><div class="loc-area">South Ahmedabad</div><div class="loc-phone">+91 99748 63333</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Ahmedabad — SG Road</div><div class="loc-area">West Ahmedabad</div><div class="loc-phone">+91 99044 22211</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Ahmedabad — Nikol</div><div class="loc-area">East Ahmedabad</div><div class="loc-phone">+91 76240 07666</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Vadodara</div><div class="loc-area">Baroda center</div><div class="loc-phone">+91 97253 55009</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Rajkot</div><div class="loc-area">Rajkot center</div><div class="loc-phone">+91 97240 04242</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Gandhinagar</div><div class="loc-area">Capital city center</div><div class="loc-phone">+91 76240 06888</div></div>
    <div class="loc-card"><div class="loc-pin">📍</div><div class="loc-city">Nagpur</div><div class="loc-area">Maharashtra center</div><div class="loc-phone">+91 92252 32123</div></div>
  </div>
</section>

<!-- CONTACT CTA -->
<section class="cta-section" id="contact">
  <canvas id="cta-canvas"></canvas>
  <div class="cta-inner">
    <div class="section-tag">Start today</div>
    <h2 class="section-title">Ready to launch your IT career?</h2>
    <p class="section-sub" style="margin:0 auto 2.2rem;max-width:400px">Talk to an advisor or drop your details and we'll reach out within 24 hours.</p>
    <div class="cta-form">
      <input type="text" placeholder="Your full name">
      <input type="email" placeholder="Email address">
      <input type="tel" placeholder="+91 phone number">
      <a href="#" class="btn-primary" style="text-align:center">Request a Callback</a>
    </div>
    <div class="addr-row">
      <div class="addr-item"><div class="addr-label">Address</div><div class="addr-val">301, Jeevandeep Complex<br>Ring Road, Surat 395002</div></div>
      <div class="addr-item"><div class="addr-label">Phone</div><div class="addr-val">+91 70695 98828</div></div>
      <div class="addr-item"><div class="addr-label">Hours</div><div class="addr-val">Mon – Sat<br>9:00 AM – 8:00 PM</div></div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="f-logo">TOPS<span>+</span> Technologies</div>
  <div class="f-links">
    <a href="#courses">Courses</a><a href="#placement">Placement</a>
    <a href="#locations">Locations</a><a href="#contact">Contact</a>
    <a href="#">Privacy Policy</a><a href="#">Sitemap</a>
  </div>
  <div class="f-copy">© 2026 TOPS Technologies Pvt. Ltd. All rights reserved.</div>
</footer>

<script>
/* ═══════════════════════════════════════════════════════
   UTILITY
═══════════════════════════════════════════════════════ */
function makeRenderer(canvas, alpha=true) {
  const r = new THREE.WebGLRenderer({ canvas, antialias: true, alpha });
  r.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  return r;
}
function resizeRenderer(renderer, camera, el) {
  const w = el.clientWidth, h = el.clientHeight;
  renderer.setSize(w, h, false);
  camera.aspect = w / h;
  camera.updateProjectionMatrix();
}

/* ═══════════════════════════════════════════════════════
   1. HERO — DNA DOUBLE HELIX + PARTICLE NEBULA
═══════════════════════════════════════════════════════ */
(function heroScene() {
  const canvas = document.getElementById('hero-canvas');
  const renderer = makeRenderer(canvas);
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(60, 1, 0.1, 200);
  camera.position.set(0, 0, 22);

  // ---- Starfield ----
  const starGeo = new THREE.BufferGeometry();
  const starCount = 800;
  const starPos = new Float32Array(starCount * 3);
  for (let i = 0; i < starCount * 3; i++) starPos[i] = (Math.random() - 0.5) * 120;
  starGeo.setAttribute('position', new THREE.BufferAttribute(starPos, 3));
  scene.add(new THREE.Points(starGeo, new THREE.PointsMaterial({ color: 0xffffff, size: 0.08, transparent: true, opacity: 0.35 })));

  // ---- DNA Double Helix ----
  const helixGroup = new THREE.Group();
  scene.add(helixGroup);
  helixGroup.position.set(6, 0, 0);

  const strandMat1 = new THREE.MeshBasicMaterial({ color: 0x06B6D4, transparent: true, opacity: 0.9 });
  const strandMat2 = new THREE.MeshBasicMaterial({ color: 0x2563EB, transparent: true, opacity: 0.9 });
  const rungMat   = new THREE.MeshBasicMaterial({ color: 0x0EA5E9, transparent: true, opacity: 0.35 });
  const nodeMat1  = new THREE.MeshBasicMaterial({ color: 0x06B6D4 });
  const nodeMat2  = new THREE.MeshBasicMaterial({ color: 0x2563EB });

  const nodeGeo = new THREE.SphereGeometry(0.12, 8, 8);
  const runGeo  = new THREE.CylinderGeometry(0.03, 0.03, 1, 6);

  const helixPoints1 = [], helixPoints2 = [];
  const TURNS = 5, PTS = 120;
  for (let i = 0; i <= PTS; i++) {
    const t = (i / PTS) * TURNS * Math.PI * 2;
    const y = (i / PTS) * 18 - 9;
    const r = 2.2;
    helixPoints1.push(new THREE.Vector3(Math.cos(t) * r, y, Math.sin(t) * r));
    helixPoints2.push(new THREE.Vector3(Math.cos(t + Math.PI) * r, y, Math.sin(t + Math.PI) * r));
  }

  // Strand tubes
  const curve1 = new THREE.CatmullRomCurve3(helixPoints1);
  const curve2 = new THREE.CatmullRomCurve3(helixPoints2);
  const tubeGeo1 = new THREE.TubeGeometry(curve1, 200, 0.05, 6, false);
  const tubeGeo2 = new THREE.TubeGeometry(curve2, 200, 0.05, 6, false);
  helixGroup.add(new THREE.Mesh(tubeGeo1, strandMat1));
  helixGroup.add(new THREE.Mesh(tubeGeo2, strandMat2));

  // Nodes + rungs every N steps
  const RUNG_STEP = 8;
  for (let i = 0; i <= PTS; i += RUNG_STEP) {
    const p1 = helixPoints1[i], p2 = helixPoints2[i];
    // nodes
    const n1 = new THREE.Mesh(nodeGeo, nodeMat1); n1.position.copy(p1); helixGroup.add(n1);
    const n2 = new THREE.Mesh(nodeGeo, nodeMat2); n2.position.copy(p2); helixGroup.add(n2);
    // rung
    const mid = new THREE.Vector3().addVectors(p1, p2).multiplyScalar(0.5);
    const dist = p1.distanceTo(p2);
    const rung = new THREE.Mesh(
      new THREE.CylinderGeometry(0.03, 0.03, dist, 6),
      rungMat
    );
    rung.position.copy(mid);
    rung.lookAt(p1);
    rung.rotateX(Math.PI / 2);
    helixGroup.add(rung);
  }

  // ---- Floating tetrahedra ----
  const tetras = [];
  for (let i = 0; i < 8; i++) {
    const m = new THREE.Mesh(
      new THREE.TetrahedronGeometry(0.3 + Math.random() * 0.35),
      new THREE.MeshBasicMaterial({ color: i % 2 === 0 ? 0x06B6D4 : 0x2563EB, wireframe: true, transparent: true, opacity: 0.55 })
    );
    m.position.set((Math.random() - 0.5) * 24, (Math.random() - 0.5) * 14, (Math.random() - 0.5) * 10 - 4);
    m.userData = { vx: (Math.random() - 0.5) * 0.006, vy: (Math.random() - 0.5) * 0.005, rx: Math.random() * 0.01, ry: Math.random() * 0.008 };
    scene.add(m); tetras.push(m);
  }

  // ---- Icosahedron glow core ----
  const icosa = new THREE.Mesh(
    new THREE.IcosahedronGeometry(1.6, 1),
    new THREE.MeshBasicMaterial({ color: 0x2563EB, wireframe: true, transparent: true, opacity: 0.12 })
  );
  icosa.position.set(-8, 0, -4);
  scene.add(icosa);

  // Mouse parallax
  let mx = 0, my = 0;
  document.addEventListener('mousemove', e => {
    mx = (e.clientX / window.innerWidth - 0.5) * 2;
    my = (e.clientY / window.innerHeight - 0.5) * 2;
  });

  function resize() { resizeRenderer(renderer, camera, canvas.parentElement); }
  resize(); window.addEventListener('resize', resize);

  const clock = new THREE.Clock();
  (function animate() {
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();
    helixGroup.rotation.y = t * 0.22;
    helixGroup.position.x = 6 + Math.sin(t * 0.4) * 0.3;

    icosa.rotation.x = t * 0.15; icosa.rotation.y = t * 0.1;

    tetras.forEach(m => {
      m.rotation.x += m.userData.rx; m.rotation.y += m.userData.ry;
      m.position.x += m.userData.vx; m.position.y += m.userData.vy;
      if (Math.abs(m.position.x) > 13) m.userData.vx *= -1;
      if (Math.abs(m.position.y) > 8)  m.userData.vy *= -1;
    });

    // Soft parallax
    camera.position.x += (mx * 1.5 - camera.position.x) * 0.04;
    camera.position.y += (-my * 1.0 - camera.position.y) * 0.04;
    camera.lookAt(0, 0, 0);

    renderer.render(scene, camera);
  })();
})();

/* ═══════════════════════════════════════════════════════
   2. WHY — ROTATING SPHERE NETWORK
═══════════════════════════════════════════════════════ */
(function whyScene() {
  const canvas = document.getElementById('why-canvas');
  const renderer = makeRenderer(canvas);
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(50, 1, 0.1, 100);
  camera.position.set(0, 0, 9);

  // Node sphere network
  const group = new THREE.Group(); scene.add(group);
  const NODE_COUNT = 60;
  const nodes = [];
  const nodeGeo = new THREE.SphereGeometry(0.07, 6, 6);

  for (let i = 0; i < NODE_COUNT; i++) {
    const phi   = Math.acos(2 * Math.random() - 1);
    const theta = Math.random() * Math.PI * 2;
    const r     = 2.8 + Math.random() * 0.8;
    const pos   = new THREE.Vector3(
      r * Math.sin(phi) * Math.cos(theta),
      r * Math.sin(phi) * Math.sin(theta),
      r * Math.cos(phi)
    );
    const mat = new THREE.MeshBasicMaterial({ color: Math.random() > 0.5 ? 0x06B6D4 : 0x2563EB, transparent: true, opacity: 0.85 });
    const mesh = new THREE.Mesh(nodeGeo, mat);
    mesh.position.copy(pos);
    group.add(mesh); nodes.push(pos);
  }

  // Edges between close nodes
  const lineMat = new THREE.LineBasicMaterial({ color: 0x2563EB, transparent: true, opacity: 0.2 });
  for (let i = 0; i < nodes.length; i++) {
    for (let j = i + 1; j < nodes.length; j++) {
      if (nodes[i].distanceTo(nodes[j]) < 2.2) {
        const geo = new THREE.BufferGeometry().setFromPoints([nodes[i], nodes[j]]);
        group.add(new THREE.Line(geo, lineMat));
      }
    }
  }

  // Core icosahedron
  group.add(new THREE.Mesh(
    new THREE.IcosahedronGeometry(1.2, 1),
    new THREE.MeshBasicMaterial({ color: 0x0EA5E9, wireframe: true, transparent: true, opacity: 0.18 })
  ));

  function resize() {
    const w = canvas.parentElement.clientWidth;
    renderer.setSize(w, w, false);
    camera.aspect = 1;
    camera.updateProjectionMatrix();
  }
  resize(); window.addEventListener('resize', resize);

  const clock = new THREE.Clock();
  (function animate() {
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();
    group.rotation.y = t * 0.18;
    group.rotation.x = Math.sin(t * 0.12) * 0.25;
    renderer.render(scene, camera);
  })();
})();

/* ═══════════════════════════════════════════════════════
   3. GLOBE — INDIA MAP NODE NETWORK
═══════════════════════════════════════════════════════ */
(function globeScene() {
  const canvas = document.getElementById('globe-canvas');
  if (!canvas) return;
  const renderer = makeRenderer(canvas);
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(45, 1, 0.1, 200);
  camera.position.set(0, 0, 12);

  // Sphere wireframe globe
  const globeGroup = new THREE.Group(); scene.add(globeGroup);

  const globe = new THREE.Mesh(
    new THREE.SphereGeometry(4, 32, 32),
    new THREE.MeshBasicMaterial({ color: 0x0D1226, transparent: true, opacity: 0.6 })
  );
  globeGroup.add(globe);

  // Grid lines
  for (let lat = -80; lat <= 80; lat += 20) {
    const r = 4 * Math.cos(lat * Math.PI / 180);
    const y = 4 * Math.sin(lat * Math.PI / 180);
    const pts = [];
    for (let lng = 0; lng <= 360; lng += 3) {
      pts.push(new THREE.Vector3(r * Math.cos(lng * Math.PI / 180), y, r * Math.sin(lng * Math.PI / 180)));
    }
    globeGroup.add(new THREE.Line(
      new THREE.BufferGeometry().setFromPoints(pts),
      new THREE.LineBasicMaterial({ color: 0x06B6D4, transparent: true, opacity: 0.08 })
    ));
  }
  for (let lng = 0; lng < 360; lng += 20) {
    const pts = [];
    for (let lat = -90; lat <= 90; lat += 3) {
      const r = 4 * Math.cos(lat * Math.PI / 180);
      const y = 4 * Math.sin(lat * Math.PI / 180);
      pts.push(new THREE.Vector3(r * Math.cos(lng * Math.PI / 180), y, r * Math.sin(lng * Math.PI / 180)));
    }
    globeGroup.add(new THREE.Line(
      new THREE.BufferGeometry().setFromPoints(pts),
      new THREE.LineBasicMaterial({ color: 0x06B6D4, transparent: true, opacity: 0.08 })
    ));
  }

  // City pins (Indian IT hubs approx lat/lng → 3D)
  function latLngTo3D(lat, lng, r) {
    const phi   = (90 - lat) * Math.PI / 180;
    const theta = (lng + 180) * Math.PI / 180;
    return new THREE.Vector3(
      -r * Math.sin(phi) * Math.cos(theta),
       r * Math.cos(phi),
       r * Math.sin(phi) * Math.sin(theta)
    );
  }

  const cities = [
    [21.17, 72.83], // Surat
    [23.02, 72.57], // Ahmedabad
    [22.31, 73.18], // Vadodara
    [22.30, 70.80], // Rajkot
    [23.22, 72.65], // Gandhinagar
    [21.15, 79.08], // Nagpur
    [12.97, 77.59], // Bangalore
    [19.08, 72.88], // Mumbai
    [28.61, 77.20], // Delhi
    [17.38, 78.49], // Hyderabad
    [13.08, 80.27], // Chennai
    [22.57, 88.36], // Kolkata
    [18.52, 73.86], // Pune
  ];

  const pinGeo = new THREE.SphereGeometry(0.12, 8, 8);
  const pinMat = new THREE.MeshBasicMaterial({ color: 0x06B6D4 });
  const glowMat = new THREE.MeshBasicMaterial({ color: 0x06B6D4, transparent: true, opacity: 0.18 });
  const glowGeo = new THREE.SphereGeometry(0.28, 8, 8);
  const cityPositions = [];

  cities.forEach(([lat, lng]) => {
    const pos = latLngTo3D(lat, lng, 4.05);
    cityPositions.push(pos);
    const pin = new THREE.Mesh(pinGeo, pinMat); pin.position.copy(pos); globeGroup.add(pin);
    const glow = new THREE.Mesh(glowGeo, glowMat); glow.position.copy(pos); globeGroup.add(glow);
  });

  // Arc connections
  function arcBetween(a, b, height=1.2) {
    const mid = new THREE.Vector3().addVectors(a, b).multiplyScalar(0.5);
    mid.normalize().multiplyScalar(a.length() + height);
    const pts = [];
    for (let t = 0; t <= 1; t += 0.04) {
      const p = new THREE.Vector3()
        .addVectors(
          new THREE.Vector3().addVectors(a.clone().multiplyScalar((1-t)*(1-t)), mid.clone().multiplyScalar(2*t*(1-t))),
          b.clone().multiplyScalar(t*t)
        );
      pts.push(p);
    }
    return pts;
  }

  const arcMat = new THREE.LineBasicMaterial({ color: 0x2563EB, transparent: true, opacity: 0.4 });
  // Connect Surat (index 0) to a few key cities
  [1,2,6,7,8].forEach(j => {
    const pts = arcBetween(cityPositions[0], cityPositions[j]);
    globeGroup.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints(pts), arcMat));
  });
  // A few more arcs
  [[1,6],[6,8],[7,9],[4,8]].forEach(([i,j]) => {
    const pts = arcBetween(cityPositions[i], cityPositions[j]);
    globeGroup.add(new THREE.Line(new THREE.BufferGeometry().setFromPoints(pts), arcMat));
  });

  // Ambient particles
  const pGeo = new THREE.BufferGeometry();
  const pPos = new Float32Array(300 * 3);
  for (let i = 0; i < 300; i++) {
    pPos[i*3]   = (Math.random()-0.5)*20;
    pPos[i*3+1] = (Math.random()-0.5)*20;
    pPos[i*3+2] = (Math.random()-0.5)*20;
  }
  pGeo.setAttribute('position', new THREE.BufferAttribute(pPos, 3));
  scene.add(new THREE.Points(pGeo, new THREE.PointsMaterial({ color: 0x06B6D4, size: 0.06, transparent: true, opacity: 0.3 })));

  function resize() { resizeRenderer(renderer, camera, canvas.parentElement); }
  resize(); window.addEventListener('resize', resize);

  let autoRot = true;
  canvas.parentElement.addEventListener('mouseenter', () => autoRot = false);
  canvas.parentElement.addEventListener('mouseleave', () => autoRot = true);

  const clock = new THREE.Clock();
  (function animate() {
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();
    if (autoRot) {
      globeGroup.rotation.y = t * 0.14;
      globeGroup.rotation.x = Math.sin(t * 0.08) * 0.1;
    }
    renderer.render(scene, camera);
  })();
})();

/* ═══════════════════════════════════════════════════════
   4. JOBFEST — BURST RING PARTICLES
═══════════════════════════════════════════════════════ */
(function jfScene() {
  const canvas = document.getElementById('jf-canvas');
  if (!canvas) return;
  const renderer = makeRenderer(canvas);
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(60, 1, 0.1, 100);
  camera.position.set(0, 0, 18);

  function resize() { resizeRenderer(renderer, camera, canvas.parentElement); }
  resize(); window.addEventListener('resize', resize);

  // Concentric glowing rings
  for (let i = 0; i < 5; i++) {
    const tGeo = new THREE.TorusGeometry(3 + i * 1.2, 0.025, 8, 80);
    const tMat = new THREE.MeshBasicMaterial({ color: 0x2563EB, transparent: true, opacity: 0.12 - i*0.015 });
    const t = new THREE.Mesh(tGeo, tMat);
    t.rotation.x = Math.PI/2 + i * 0.18;
    t.userData = { speed: 0.008 - i*0.001 };
    scene.add(t);
  }

  // Orbiting cubes
  const cubes = [];
  for (let i = 0; i < 10; i++) {
    const size = 0.15 + Math.random() * 0.3;
    const c = new THREE.Mesh(
      new THREE.BoxGeometry(size, size, size),
      new THREE.MeshBasicMaterial({ color: i%3===0?0x06B6D4:0x2563EB, wireframe:true, transparent:true, opacity:.6 })
    );
    const angle = (i/10)*Math.PI*2;
    const radius = 4 + Math.random() * 3;
    c.userData = { angle, radius, speed: 0.008 + Math.random()*0.006, yi: Math.random()*Math.PI*2 };
    scene.add(c); cubes.push(c);
  }

  // Central dodecahedron
  const dodeca = new THREE.Mesh(
    new THREE.DodecahedronGeometry(1.8, 0),
    new THREE.MeshBasicMaterial({ color: 0x2563EB, wireframe: true, transparent: true, opacity: 0.2 })
  );
  scene.add(dodeca);

  const clock = new THREE.Clock();
  (function animate() {
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();
    dodeca.rotation.y = t * 0.3; dodeca.rotation.x = t * 0.15;

    scene.children.forEach(obj => {
      if (obj.isMesh && obj.geometry.type === 'TorusGeometry') {
        obj.rotation.z += obj.userData.speed || 0;
      }
    });

    cubes.forEach(c => {
      c.userData.angle += c.userData.speed;
      c.position.x = Math.cos(c.userData.angle) * c.userData.radius;
      c.position.z = Math.sin(c.userData.angle) * c.userData.radius;
      c.position.y = Math.sin(t * 0.5 + c.userData.yi) * 1.5;
      c.rotation.x += 0.02; c.rotation.y += 0.015;
    });

    renderer.render(scene, camera);
  })();
})();

/* ═══════════════════════════════════════════════════════
   5. CTA — WAVE PARTICLE FIELD
═══════════════════════════════════════════════════════ */
(function ctaScene() {
  const canvas = document.getElementById('cta-canvas');
  if (!canvas) return;
  const renderer = makeRenderer(canvas);
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(55, 1, 0.1, 100);
  camera.position.set(0, 4, 20);
  camera.lookAt(0, -2, 0);

  function resize() { resizeRenderer(renderer, camera, canvas.parentElement); }
  resize(); window.addEventListener('resize', resize);

  const COLS = 38, ROWS = 24;
  const positions = new Float32Array(COLS * ROWS * 3);
  const colors    = new Float32Array(COLS * ROWS * 3);
  const geo = new THREE.BufferGeometry();

  for (let i = 0; i < COLS; i++) {
    for (let j = 0; j < ROWS; j++) {
      const idx = (i * ROWS + j) * 3;
      positions[idx]   = (i/(COLS-1) - 0.5) * 34;
      positions[idx+1] = (j/(ROWS-1) - 0.5) * 22;
      positions[idx+2] = 0;
      // gradient color: blue -> cyan
      const mix = j / ROWS;
      colors[idx]   = 0.15 + mix * 0.08;
      colors[idx+1] = 0.45 + mix * 0.28;
      colors[idx+2] = 0.85 + mix * 0.15;
    }
  }
  geo.setAttribute('position', new THREE.BufferAttribute(positions, 3));
  geo.setAttribute('color', new THREE.BufferAttribute(colors, 3));
  const mat = new THREE.PointsMaterial({ size: 0.16, transparent: true, opacity: 0.45, vertexColors: true });
  const wave = new THREE.Points(geo, mat);
  scene.add(wave);

  const clock = new THREE.Clock();
  (function animate() {
    requestAnimationFrame(animate);
    const t = clock.getElapsedTime();
    const pos = wave.geometry.attributes.position;
    for (let i = 0; i < COLS; i++) {
      for (let j = 0; j < ROWS; j++) {
        const idx = i * ROWS + j;
        pos.setZ(idx, Math.sin(i * 0.45 + t * 0.9) * Math.cos(j * 0.38 + t * 0.65) * 1.8);
      }
    }
    pos.needsUpdate = true;
    wave.rotation.x = -0.25;
    renderer.render(scene, camera);
  })();
})();

/* ═══════════════════════════════════════════════════════
   6. 3D CARD TILT
═══════════════════════════════════════════════════════ */
document.querySelectorAll('.course-card, .t-card, .loc-card').forEach(card => {
  card.addEventListener('mousemove', e => {
    const r = card.getBoundingClientRect();
    const x = (e.clientX - r.left) / r.width  - 0.5;
    const y = (e.clientY - r.top)  / r.height - 0.5;
    card.style.transform = `perspective(700px) rotateY(${x*14}deg) rotateX(${-y*12}deg) translateZ(8px)`;
    card.style.transition = 'transform .05s ease';
  });
  card.addEventListener('mouseleave', () => {
    card.style.transform = 'perspective(700px) rotateY(0deg) rotateX(0deg) translateZ(0)';
    card.style.transition = 'transform .5s ease';
  });
});

/* ═══════════════════════════════════════════════════════
   7. SCROLL REVEAL
═══════════════════════════════════════════════════════ */
const revObs = new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); revObs.unobserve(e.target); } });
}, { threshold: 0.1 });
document.querySelectorAll('.reveal').forEach(el => revObs.observe(el));

/* ═══════════════════════════════════════════════════════
   8. COUNTER
═══════════════════════════════════════════════════════ */
function counter(el, target) {
  let v = 0; const step = target / 90;
  const iv = setInterval(() => {
    v = Math.min(v + step, target);
    el.childNodes[0].textContent = target >= 1000 ? Math.round(v).toLocaleString('en-IN') : Math.round(v);
    if (v >= target) clearInterval(iv);
  }, 16);
}
new IntersectionObserver(entries => {
  entries.forEach(e => { if (e.isIntersecting) { counter(e.target, +e.target.dataset.target); } });
}, { threshold: 0.5 }).observe !== undefined &&
document.querySelectorAll('.stat-num[data-target]').forEach(el => {
  new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { counter(e.target, +e.target.dataset.target); } });
  }, { threshold: 0.5 }).observe(el);
});

/* ═══════════════════════════════════════════════════════
   9. BAR CHART
═══════════════════════════════════════════════════════ */
new IntersectionObserver(entries => {
  entries.forEach(e => {
    if (e.isIntersecting) {
      e.target.querySelectorAll('.bar-fill').forEach(b => {
        b.style.transitionDelay = Math.random() * 0.3 + 's';
        b.style.transform = `scaleX(${b.dataset.w})`;
      });
    }
  });
}, { threshold: 0.4 }).observe(document.querySelector('.why-3d-panel'));

/* ═══════════════════════════════════════════════════════
   10. TICKER
═══════════════════════════════════════════════════════ */
const placed = [
  ["Yash Saradva","React Developer"],["Dipam Bhatt","Test Engineer"],
  ["Nishi Amin","Data Analyst"],["Nirmal Ghediya","Mobile Dev"],
  ["Urvi Parmar","Frontend Dev"],["Shivam Pandey","Flutter Dev"],
  ["Anubhab Nayek","PHP Dev"],["Mannat Kareliya","Data Analytics"],
  ["Vikram Makwana","Python Dev"],["Nayan Rajpura","UI/UX Designer"],
  ["Srushti Anand","Flutter Dev"],["Hritika Mistry","Data Analytics"],
  ["Mohit Kumar","Full Stack Dev"],["Aman Malhotra","Graphic Designer"],
  ["Jay Shukla","Software Tester"],["Prashant Tejura","Network Eng."],
  ["Harsh Dholakiya","Python Dev"],["Arnold Bakul","Digital Marketer"],
  ["Sagar Sonara","Python Dev"],["Piyush Panchal","Software Dev"],
  ["Arjun Chavda","Python Dev"],["Madhav Dhruve","PHP Dev"],
  ["Srushti Anand","Flutter Dev"],["Jaydeep Mishra","Full Stack Dev"],
  ["Meet Italiya","fronted dev"],["Madhav Mishra","Data Analyst"]
];
const tk = document.getElementById('ticker');
const mkChip = ([n,r]) => {
  const i = n.split(' ').map(w=>w[0]).join('').slice(0,2);
  return `<div class="chip"><div class="av">${i}</div><span class="nm">${n}</span><span class="rl">${r}</span></div>`;
};
tk.innerHTML = placed.map(mkChip).join('') + placed.map(mkChip).join('');
</script>
</body>
</html>
