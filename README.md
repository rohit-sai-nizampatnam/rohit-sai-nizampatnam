<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rohith Sai · 3D Premium Profile</title>
  <!-- Google Fonts & Font Awesome -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:opsz,wght@14..32,300;14..32,400;14..32,500;14..32,600;14..32,700;14..32,800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    /* ---------- RESET & GLOBAL ---------- */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: radial-gradient(circle at 10% 20%, #0a0f1e, #03050b);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 2rem 1.5rem;
      font-family: 'Inter', sans-serif;
      color: #eef2ff;
      perspective: 1200px;
      overflow-x: hidden;
    }

    /* main 3D card container */
    .card-3d {
      max-width: 1280px;
      width: 100%;
      transform-style: preserve-3d;
      transition: transform 0.1s ease-out;
      will-change: transform;
      border-radius: 3rem;
      box-shadow: 0 40px 80px -20px rgba(0, 0, 0, 0.9), 0 0 0 1px rgba(139, 92, 246, 0.2) inset, 0 0 40px rgba(94, 23, 235, 0.3);
      background: linear-gradient(145deg, #0b1020, #0a0e1a);
      padding: 2rem 2.5rem;
      backdrop-filter: blur(2px);
    }

    /* interior elements get 3D lift */
    .lift-3d {
      transform: translateZ(30px);
      transition: transform 0.2s ease;
    }

    .lift-3d-sm {
      transform: translateZ(15px);
    }

    /* ---------- TYPOGRAPHY & UTILS ---------- */
    h1, h2, h3, h4 {
      font-weight: 600;
      letter-spacing: -0.02em;
    }

    .gradient-text {
      background: linear-gradient(135deg, #c4b5fd, #a78bfa, #8b5cf6, #6d28d9);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .badge-glass {
      background: rgba(139, 92, 246, 0.12);
      backdrop-filter: blur(12px);
      border: 1px solid rgba(139, 92, 246, 0.3);
      border-radius: 100px;
      padding: 0.5rem 1.2rem;
      font-size: 0.8rem;
      font-weight: 500;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      transition: all 0.25s;
      color: #d9d2ff;
    }

    .badge-glass:hover {
      background: rgba(139, 92, 246, 0.25);
      border-color: #8b5cf6;
      box-shadow: 0 0 18px rgba(139, 92, 246, 0.6);
      color: white;
    }

    /* pill nav */
    .pill-nav {
      display: flex;
      flex-wrap: wrap;
      gap: 0.75rem;
      justify-content: center;
      margin: 1.5rem 0 2rem;
    }

    .pill-nav a {
      display: inline-flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(20, 25, 45, 0.8);
      border: 1px solid rgba(139, 92, 246, 0.25);
      border-radius: 100px;
      padding: 0.55rem 1.4rem;
      font-size: 0.85rem;
      font-weight: 500;
      color: #b9b1e6;
      text-decoration: none;
      transition: 0.2s;
      backdrop-filter: blur(8px);
    }

    .pill-nav a i {
      color: #a78bfa;
      font-size: 1rem;
    }

    .pill-nav a:hover {
      background: #1a1f35;
      border-color: #8b5cf6;
      color: white;
      box-shadow: 0 0 15px rgba(139, 92, 246, 0.5);
      transform: translateY(-2px);
    }

    /* sections */
    section {
      margin: 3.5rem 0;
    }

    .section-title {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 1.8rem;
    }

    .section-title h2 {
      font-size: 1.8rem;
      font-weight: 700;
      background: linear-gradient(135deg, #e0d7ff, #b49af0);
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .section-title .line {
      flex: 1;
      height: 2px;
      background: linear-gradient(90deg, #5e17eb, transparent);
      border-radius: 2px;
    }

    /* code block */
    .code-block {
      background: #0b0f18;
      border: 1px solid #2a1f4a;
      border-radius: 1.5rem;
      padding: 1.5rem 1.8rem;
      font-family: 'Fira Code', 'Inter', monospace;
      font-size: 0.9rem;
      line-height: 1.7;
      color: #d1d5ff;
      box-shadow: 0 15px 30px -15px #000000, inset 0 1px 0 rgba(139, 92, 246, 0.2);
      backdrop-filter: blur(4px);
      white-space: pre-wrap;
      word-break: break-word;
    }

    .code-block .key {
      color: #c084fc;
    }

    .code-block .value {
      color: #a5f3fc;
    }

    /* skill icons */
    .skills-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 1rem 1.8rem;
      align-items: center;
    }

    .skills-grid img {
      height: 40px;
      filter: drop-shadow(0 6px 10px rgba(0, 0, 0, 0.6));
      transition: transform 0.2s, filter 0.2s;
    }

    .skills-grid img:hover {
      transform: scale(1.08) translateY(-4px);
      filter: drop-shadow(0 12px 18px #5e17ebaa);
    }

    /* project cards */
    .project-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 1.8rem;
    }

    @media (max-width: 800px) {
      .project-grid {
        grid-template-columns: 1fr;
      }
    }

    .project-card {
      background: rgba(15, 20, 35, 0.8);
      border: 1px solid rgba(139, 92, 246, 0.3);
      border-radius: 1.8rem;
      padding: 1.2rem 1.2rem 1.5rem;
      transition: all 0.3s cubic-bezier(0.2, 0.9, 0.3, 1);
      backdrop-filter: blur(8px);
      box-shadow: 0 25px 35px -15px #000000;
      transform-style: preserve-3d;
    }

    .project-card:hover {
      border-color: #a78bfa;
      box-shadow: 0 30px 40px -12px #2e1065, 0 0 30px #5e17eb66;
      transform: translateZ(16px) scale(1.01);
    }

    .project-card img {
      width: 100%;
      border-radius: 1.2rem;
      border: 1px solid #3b2b6e;
      aspect-ratio: 16/9;
      object-fit: cover;
      transition: all 0.3s;
      box-shadow: 0 10px 20px -5px black;
    }

    .project-card:hover img {
      border-color: #b69cff;
    }

    .project-card h3 {
      font-size: 1.3rem;
      margin: 1rem 0 0.4rem;
      font-weight: 600;
      color: #e4d9ff;
    }

    .project-card p {
      font-size: 0.9rem;
      color: #a7a0c9;
      margin-bottom: 0.8rem;
    }

    .project-link {
      display: inline-flex;
      align-items: center;
      gap: 0.4rem;
      color: #b49af0;
      text-decoration: none;
      font-weight: 500;
      font-size: 0.9rem;
      border-bottom: 1px dotted #8b5cf6;
    }

    .project-link:hover {
      color: #d7c6ff;
      gap: 0.7rem;
    }

    /* experience table style */
    .exp-item {
      display: grid;
      grid-template-columns: 180px 1fr;
      gap: 1.5rem;
      padding: 1.2rem 0;
      border-bottom: 1px solid rgba(139, 92, 246, 0.2);
      align-items: start;
    }

    @media (max-width: 600px) {
      .exp-item {
        grid-template-columns: 1fr;
        gap: 0.5rem;
      }
    }

    .exp-date {
      color: #a78bfa;
      font-weight: 600;
      font-size: 0.9rem;
      letter-spacing: 0.02em;
      text-transform: uppercase;
    }

    .exp-role {
      font-weight: 700;
      font-size: 1.1rem;
      color: #e6deff;
    }

    .exp-company {
      color: #9f8dd0;
      font-weight: 500;
      font-size: 0.95rem;
      margin: 0.2rem 0 0.4rem;
    }

    .exp-desc {
      color: #aaa3cc;
      font-size: 0.9rem;
      line-height: 1.5;
    }

    /* stats & analytics placeholders */
    .analytics-row {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.5rem;
      margin-top: 1.5rem;
    }

    .analytics-row img {
      border-radius: 1.2rem;
      border: 1px solid #2f2355;
      background: #0b0f18;
      padding: 0.6rem;
      box-shadow: 0 15px 25px -12px black;
      max-width: 100%;
    }

    /* small badges */
    .badge-group {
      display: flex;
      flex-wrap: wrap;
      gap: 0.7rem;
      margin-top: 1.2rem;
    }

    .badge-group span {
      background: #151c2e;
      border: 1px solid #3b2e6b;
      border-radius: 100px;
      padding: 0.4rem 1.2rem;
      font-size: 0.8rem;
      font-weight: 500;
      color: #c4b5fd;
      transition: 0.15s;
    }

    .badge-group span:hover {
      background: #1e1a3a;
      border-color: #8b5cf6;
      box-shadow: 0 0 12px #5e17eb88;
    }

    /* footer */
    .footer-note {
      text-align: center;
      margin-top: 3rem;
      font-size: 0.9rem;
      color: #716a9e;
      border-top: 1px solid #1f1a3a;
      padding-top: 2rem;
    }

    .footer-note strong {
      color: #cbbef5;
      font-weight: 600;
    }

    .footer-wave {
      margin-top: 2rem;
      border-radius: 2rem;
      opacity: 0.7;
    }

    /* floating animation for 3d tilt effect */
    .tilt-shine {
      position: relative;
      overflow: hidden;
    }
  </style>
</head>
<body>
  <!-- 3D tilt container – will be enhanced with JS -->
  <div class="card-3d" id="tiltCard">
    <!-- BANNER (3D lifted) -->
    <div style="display: flex; justify-content: center; margin-bottom: 1rem;" class="lift-3d">
      <img src="https://capsule-render.vercel.app/api?type=venom&height=240&text=ROHITH%20SAI&fontSize=68&fontColor=ffffff&color=0:0b1e3d,50:5e17eb,100:0b1e3d&stroke=8b5cf6&strokeWidth=1&animation=fadeIn&fontAlignY=45&desc=WEB%20DEVELOPER%20%7C%20TECH%20STRATEGIST%20%7C%20BUILDER&descSize=15&descAlignY=65" width="100%" alt="Rohith Sai banner" style="border-radius: 2rem; box-shadow: 0 25px 35px -10px #1e0b4b, 0 0 0 1px #4c1d95 inset;" />
    </div>

    <!-- SOCIAL PILLS -->
    <div class="pill-nav lift-3d-sm">
      <a href="https://stagzon.com/rohit-sai/"><i class="fas fa-globe"></i> PORTFOLIO</a>
      <a href="https://www.linkedin.com/in/rohit-sai-nizampatnam-65a1402b9/"><i class="fab fa-linkedin-in"></i> LINKEDIN</a>
      <a href="mailto:rohithsainizampatnam@gmail.com"><i class="fas fa-envelope"></i> EMAIL</a>
      <a href="https://stagzon.com/"><i class="fas fa-cube"></i> STAGZON</a>
    </div>

    <!-- tagline with 3D -->
    <div style="text-align: center; margin: 1rem 0 0.5rem;" class="lift-3d-sm">
      <p style="font-size: 1.5rem; font-weight: 500; color: #d9d0ff; text-shadow: 0 5px 15px #3b1d8b;">I turn ideas into digital experiences.</p>
      <p style="font-size: 1rem; color: #9f97c7; margin-top: 0.3rem;">Building scalable websites, powerful web applications and thoughtful digital products.</p>
    </div>

    <!-- PROFILE VIEWS (3D badge) -->
    <div style="display: flex; justify-content: center; margin: 1.5rem 0 0.5rem;" class="lift-3d-sm">
      <img src="https://komarev.com/ghpvc/?username=YOUR_GITHUB_USERNAME&style=flat-square&color=5e17eb&label=PROFILE+VIEWS" alt="Profile views" style="border-radius: 30px; box-shadow: 0 8px 20px #0d0621;" />
    </div>

    <!-- ABOUT ME (yaml block) -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ ABOUT ME</h2>
        <div class="line"></div>
      </div>
      <div class="code-block">
<span class="key">name:</span> <span class="value">Rohith Sai Nizampatnam</span>
<span class="key">location:</span> <span class="value">Hyderabad, India</span>
<span class="key">role:</span> <span class="value">Web Developer & Tech Strategist</span>
<span class="key">experience:</span> <span class="value">5+ Years</span>
<span class="key">company:</span> <span class="value">Stagzon Creative Solutions</span>
<span class="key">focus:</span>
  - WordPress & Full Stack Web Development
  - Web Applications & E-commerce
  - Website Infrastructure & Optimisation
  - AI-Powered Solutions & Automation
<span class="key">currently_exploring:</span>
  - React.js
  - TypeScript
  - Agentic AI
  - Modern Web Architectures
      </div>
      <div style="margin-top: 1.5rem; color: #b9b0e0; line-height: 1.7;">
        I'm a web developer focused on creating reliable, scalable and visually engaging digital experiences. My work combines development, infrastructure, design and business thinking.
        <div class="badge-group" style="margin-top: 1.2rem;">
          <span>30+ production websites</span>
          <span>Custom WordPress</span>
          <span>eCommerce</span>
          <span>DNS / Cloudflare</span>
          <span>AI workflows</span>
        </div>
      </div>
    </section>

    <!-- WHAT I BUILD (2x2 grid) -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ WHAT I BUILD</h2>
        <div class="line"></div>
      </div>
      <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 1.5rem;">
        <div style="background: #0f1525; border-radius: 1.5rem; padding: 1.5rem; border: 1px solid #2f2355;">
          <h3 style="color: #c8b6ff; font-size: 1.3rem;">◈ Web Development</h3>
          <p style="color: #a59fc9; font-size: 0.9rem; margin-top: 0.5rem;">Custom WordPress solutions, dynamic websites, responsive interfaces and API-driven applications.</p>
        </div>
        <div style="background: #0f1525; border-radius: 1.5rem; padding: 1.5rem; border: 1px solid #2f2355;">
          <h3 style="color: #c8b6ff; font-size: 1.3rem;">◈ E-commerce Engineering</h3>
          <p style="color: #a59fc9; font-size: 0.9rem; margin-top: 0.5rem;">WooCommerce, multi-vendor platforms, product systems and business-focused integrations.</p>
        </div>
        <div style="background: #0f1525; border-radius: 1.5rem; padding: 1.5rem; border: 1px solid #2f2355;">
          <h3 style="color: #c8b6ff; font-size: 1.3rem;">◈ Web Operations</h3>
          <p style="color: #a59fc9; font-size: 0.9rem; margin-top: 0.5rem;">DNS, Cloudflare, SSL, hosting, deployment, migrations, performance and technical SEO.</p>
        </div>
        <div style="background: #0f1525; border-radius: 1.5rem; padding: 1.5rem; border: 1px solid #2f2355;">
          <h3 style="color: #c8b6ff; font-size: 1.3rem;">◈ AI & Automation</h3>
          <p style="color: #a59fc9; font-size: 0.9rem; margin-top: 0.5rem;">AI-assisted development, intelligent workflows, automation pipelines and emerging AI applications.</p>
        </div>
      </div>
    </section>

    <!-- TECH STACK -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ TECHNOLOGY STACK</h2>
        <div class="line"></div>
      </div>
      <div style="margin-bottom: 1.2rem;">
        <p style="font-weight: 600; color: #b7a6ff; margin-bottom: 0.6rem;">Frontend</p>
        <div class="skills-grid">
          <img src="https://skillicons.dev/icons?i=html,css,js,ts,react&theme=dark" alt="Frontend" />
        </div>
      </div>
      <div style="margin-bottom: 1.2rem;">
        <p style="font-weight: 600; color: #b7a6ff; margin-bottom: 0.6rem;">Backend & CMS</p>
        <div class="skills-grid">
          <img src="https://skillicons.dev/icons?i=php,mysql,wordpress&theme=dark" alt="Backend" />
        </div>
      </div>
      <div style="margin-bottom: 1.2rem;">
        <p style="font-weight: 600; color: #b7a6ff; margin-bottom: 0.6rem;">Tools & Infrastructure</p>
        <div class="skills-grid">
          <img src="https://skillicons.dev/icons?i=git,github,cloudflare,figma,linux,vscode&theme=dark" alt="Tools" />
        </div>
      </div>
      <div class="badge-group" style="margin-top: 1rem;">
        <span>Elementor</span><span>WooCommerce</span><span>Divi</span><span>ACF</span><span>REST APIs</span><span>Cloudflare</span><span>GA4</span>
      </div>
    </section>

    <!-- EXPERIENCE -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ EXPERIENCE</h2>
        <div class="line"></div>
      </div>
      <div class="exp-item">
        <div class="exp-date">2019 — Present</div>
        <div>
          <div class="exp-role">Founder & Tech Strategist</div>
          <div class="exp-company">Stagzon Creative Solutions</div>
          <div class="exp-desc">Building digital solutions across web development, branding, UI/UX and AI-enabled services.</div>
        </div>
      </div>
      <div class="exp-item">
        <div class="exp-date">Dec 2024 — Present</div>
        <div>
          <div class="exp-role">Web Development & Digital Experience</div>
          <div class="exp-company">Malla Reddy Institutions</div>
          <div class="exp-desc">Website development, institutional web applications, technical SEO and website operations.</div>
        </div>
      </div>
      <div class="exp-item">
        <div class="exp-date">Jan 2021 — Nov 2024</div>
        <div>
          <div class="exp-role">WordPress & Frontend Developer</div>
          <div class="exp-company">Bhavya Web Technologies Pvt. Ltd.</div>
          <div class="exp-desc">WordPress development, frontend implementation and production website delivery.</div>
        </div>
      </div>
    </section>

    <!-- SELECTED PROJECTS -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ SELECTED PROJECTS</h2>
        <div class="line"></div>
      </div>
      <div class="project-grid">
        <div class="project-card">
          <a href="https://mrvv.edu.in/" target="_blank"><img src="https://image.thum.io/get/width/800/crop/500/https://mrvv.edu.in/" alt="MRVV website preview" /></a>
          <h3>01 / MRVV</h3>
          <p>Institutional website and digital experience.</p>
          <a href="https://mrvv.edu.in/" class="project-link" target="_blank">Visit Website <i class="fas fa-arrow-up-right-from-square"></i></a>
        </div>
        <div class="project-card">
          <a href="https://mrdu.edu.in/" target="_blank"><img src="https://image.thum.io/get/width/800/crop/500/https://mrdu.edu.in/" alt="MRDU website preview" /></a>
          <h3>02 / MRDU</h3>
          <p>University web presence and digital platform.</p>
          <a href="https://mrdu.edu.in/" class="project-link" target="_blank">Visit Website <i class="fas fa-arrow-up-right-from-square"></i></a>
        </div>
        <div class="project-card">
          <a href="https://accman.in/" target="_blank"><img src="https://image.thum.io/get/width/800/crop/500/https://accman.in/" alt="ACCMAN website preview" /></a>
          <h3>03 / ACCMAN</h3>
          <p>Education website and programme-focused digital experience.</p>
          <a href="https://accman.in/" class="project-link" target="_blank">Visit Website <i class="fas fa-arrow-up-right-from-square"></i></a>
        </div>
        <div class="project-card">
          <a href="https://stagzon.com/" target="_blank"><img src="https://image.thum.io/get/width/800/crop/500/https://stagzon.com/" alt="Stagzon website preview" /></a>
          <h3>04 / STAGZON</h3>
          <p>Creative technology and digital solutions.</p>
          <a href="https://stagzon.com/" class="project-link" target="_blank">Visit Website <i class="fas fa-arrow-up-right-from-square"></i></a>
        </div>
      </div>
    </section>

    <!-- GITHUB ANALYTICS (with placeholders and 3D) -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ GITHUB ANALYTICS</h2>
        <div class="line"></div>
      </div>
      <div class="analytics-row">
        <img width="100%" src="https://github-readme-activity-graph.vercel.app/graph?username=YOUR_GITHUB_USERNAME&bg_color=0b1020&color=a78bfa&line=8b5cf6&point=ffffff&area=true&hide_border=true" alt="Contribution activity graph" style="max-width: 100%; border-radius: 1.5rem;" />
      </div>
      <div class="analytics-row">
        <img height="170" src="https://github-readme-stats.vercel.app/api?username=YOUR_GITHUB_USERNAME&show_icons=true&hide_border=true&bg_color=0b1020&title_color=a78bfa&text_color=cbd5e1&icon_color=8b5cf6&rank_icon=github" alt="GitHub stats" />
        <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_GITHUB_USERNAME&layout=compact&hide_border=true&bg_color=0b1020&title_color=a78bfa&text_color=cbd5e1" alt="Top languages" />
        <img width="70%" src="https://streak-stats.demolab.com?user=YOUR_GITHUB_USERNAME&theme=transparent&hide_border=true&ring=8b5cf6&fire=a78bfa&currStreakLabel=a78bfa" alt="GitHub streak" />
      </div>
    </section>

    <!-- BEYOND THE CODE -->
    <section class="lift-3d-sm">
      <div class="section-title">
        <h2>✦ BEYOND THE CODE</h2>
        <div class="line"></div>
      </div>
      <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 1rem; color: #b9b0e0;">
        <div style="background: #0f1525; border-radius: 1.2rem; padding: 1rem 1.2rem; border-left: 3px solid #8b5cf6;">Product thinking: Turning business requirements into practical digital products.</div>
        <div style="background: #0f1525; border-radius: 1.2rem; padding: 1rem 1.2rem; border-left: 3px solid #8b5cf6;">Design mindset: Creating clean, intuitive and purposeful interfaces.</div>
        <div style="background: #0f1525; border-radius: 1.2rem; padding: 1rem 1.2rem; border-left: 3px solid #8b5cf6;">Problem solving: Diagnosing complex website, performance and infrastructure issues.</div>
        <div style="background: #0f1525; border-radius: 1.2rem; padding: 1rem 1.2rem; border-left: 3px solid #8b5cf6;">Continuous learning: Exploring modern development tools and AI technologies.</div>
      </div>
    </section>

    <!-- LET'S BUILD SOMETHING -->
    <section style="text-align: center; margin-top: 3rem;" class="lift-3d-sm">
      <h2 style="font-size: 2.2rem; font-weight: 700; background: linear-gradient(135deg, #ddd3ff, #b79eff); -webkit-background-clip: text; background-clip: text; color: transparent;">Have an idea? Let's make it real.</h2>
      <p style="color: #a197d1; margin: 0.8rem 0 1.5rem; font-size: 1.1rem;">I'm open to interesting collaborations, development opportunities and conversations around technology.</p>
      <div style="display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap;">
        <a href="https://stagzon.com/rohit-sai/" style="display: inline-flex; align-items: center; gap: 0.5rem; background: #5e17eb; border: none; border-radius: 100px; padding: 0.8rem 2rem; font-weight: 600; color: white; text-decoration: none; box-shadow: 0 15px 20px -10px #5e17eb; transition: 0.2s; transform: translateZ(10px);"><i class="fas fa-globe"></i> EXPLORE MY WORK</a>
        <a href="mailto:rohithsainizampatnam@gmail.com" style="display: inline-flex; align-items: center; gap: 0.5rem; background: #1e1a3a; border: 1px solid #8b5cf6; border-radius: 100px; padding: 0.8rem 2rem; font-weight: 600; color: #d9d0ff; text-decoration: none; transition: 0.2s; transform: translateZ(10px);"><i class="fas fa-envelope"></i> LET'S TALK</a>
      </div>
    </section>

    <!-- FOOTER -->
    <div class="footer-note lift-3d-sm">
      <p><strong>Rohith Sai Nizampatnam</strong></p>
      <p style="font-style: italic; margin-top: 0.3rem;">Build with purpose. Create with curiosity. Keep evolving.</p>
      <img src="https://capsule-render.vercel.app/api?type=waving&color=0:0b1e3d,50:5e17eb,100:0b1e3d&height=120&section=footer" width="100%" class="footer-wave" alt="Footer banner" style="margin-top: 1.5rem;" />
    </div>
  </div>

  <!-- 3D TILT SCRIPT -->
  <script>
    (function() {
      const card = document.getElementById('tiltCard');
      if (!card) return;

      function handleMove(e) {
        const rect = card.getBoundingClientRect();
        let x, y;

        // touch or mouse
        if (e.touches) {
          x = e.touches[0].clientX - rect.left;
          y = e.touches[0].clientY - rect.top;
        } else {
          x = e.clientX - rect.left;
          y = e.clientY - rect.top;
        }

        const centerX = rect.width / 2;
        const centerY = rect.height / 2;
        const deltaX = (x - centerX) / centerX;
        const deltaY = (y - centerY) / centerY;

        // limit rotation for subtle premium feel
        const rotateY = Math.max(-6, Math.min(6, deltaX * 8));
        const rotateX = Math.max(-6, Math.min(6, -deltaY * 8));

        card.style.transform = `rotateX(${rotateX}deg) rotateY(${rotateY}deg) scale3d(1.01, 1.01, 1.01)`;
        card.style.transition = 'transform 0.08s ease-out';
      }

      function resetTilt() {
        card.style.transform = 'rotateX(0deg) rotateY(0deg) scale3d(1, 1, 1)';
        card.style.transition = 'transform 0.6s cubic-bezier(0.23, 1, 0.32, 1)';
      }

      // use pointer for better feel
      card.addEventListener('mousemove', handleMove);
      card.addEventListener('mouseleave', resetTilt);
      // Touch support
      card.addEventListener('touchmove', (e) => {
        e.preventDefault(); // prevent scroll while tilting
        handleMove(e);
      }, { passive: false });
      card.addEventListener('touchend', resetTilt);
      card.addEventListener('touchcancel', resetTilt);

      // reset transform on window resize (just in case)
      window.addEventListener('resize', resetTilt);
    })();
  </script>

  <!-- small note: replace YOUR_GITHUB_USERNAME with actual username for stats -->
  <div style="display: none;">placeholders for github analytics - update YOUR_GITHUB_USERNAME</div>
</body>
</html>
