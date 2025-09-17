# Portfolio_Lavanya
Portfolio Website
This repository contains the source code for my personal interactive portfolio. It is built using HTML, CSS, and JavaScript and showcases my skills, projects, and certifications in an organized and visually engaging manner.

Key Features
Responsive design optimized for desktop and mobile devices

Sections highlighting About, Skills, Projects, Certifications, and Contact information

Smooth animations and interactive elements for an enhanced user experience

Contact form with basic validation

Clean and modern UI inspired by GitHub’s dark theme

Purpose
The portfolio serves as a professional platform to demonstrate my technical expertise in web development and AI/ML, as well as to provide easy access to my projects and certifications.
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Ratakonda Lavanya | Portfolio</title>
  <meta name="description" content="Ratakonda Lavanya - Interactive Digital Portfolio showcasing skills, projects, and contact information." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#0d1117;
      --panel:#161b22;
      --muted:#8b949e;
      --text:#f0f6fc;
      --acc:#58a6ff;
      --acc-2:#f78166;
      --ok:#3fb950;
      --danger:#f85149;
      --ring: 0 0 0 3px color-mix(in oklab, var(--acc) 30%, transparent);
      --radius: 18px;
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --maxw: 1100px;
    }
    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, Arial, sans-serif;
      color:var(--text);
      background:var(--bg);
      line-height:1.6;
    }
    header{position:sticky; top:0; z-index:50; backdrop-filter:blur(8px); background:rgba(13,17,23,.8); border-bottom:1px solid rgba(255,255,255,.06);}
    .nav{max-width:var(--maxw); margin:auto; display:flex; align-items:center; gap:16px; padding:12px 20px}
    .brand{font-weight:800; letter-spacing:.4px}
    .brand span{color:var(--acc)}
    .nav a{color:var(--muted); text-decoration:none; font-weight:600; padding:10px 12px; border-radius:12px}
    .nav a.active, .nav a:hover{color:var(--text); background:rgba(255,255,255,.06)}
    .spacer{flex:1}
    .cta{background:linear-gradient(90deg, var(--acc), var(--acc-2)); color:#0d1117!important; padding:10px 16px; border-radius:14px; box-shadow:var(--shadow);}
    .hero{max-width:var(--maxw); margin:40px auto; padding:24px 20px 0; display:grid; grid-template-columns:1.2fr .8fr; gap:28px; align-items:center}
    .hero h1{font-size:clamp(32px, 4.6vw, 56px); line-height:1.1; margin:0 0 14px}
    .hero p{color:var(--muted); font-size:1.05rem}
    .hero .tag{display:inline-block; padding:8px 12px; border-radius:999px; background:rgba(255,255,255,.06); color:var(--acc); font-weight:700; letter-spacing:.06em; margin-bottom:12px}
    .chip-row{display:flex; flex-wrap:wrap; gap:10px; margin-top:14px}
    .chip{padding:8px 12px; background:#0f1520; border:1px solid rgba(255,255,255,.08); border-radius:999px; font-size:.9rem}
    section{max-width:var(--maxw); margin:70px auto; padding:0 20px}
    section h2{font-size:clamp(24px,3.2vw,36px); margin:0 0 14px}
    .sub{color:var(--muted); margin-top:-6px}
    .about{display:grid; grid-template-columns: 1.1fr .9fr; gap:24px}
    .about .panel{background:var(--panel); border:1px solid rgba(255,255,255,.06); border-radius:var(--radius); padding:22px; box-shadow:var(--shadow)}
    .skills-grid{display:grid; grid-template-columns: repeat(auto-fit,minmax(240px,1fr)); gap:16px}
    .skill{background:var(--panel); border:1px solid rgba(255,255,255,.06); border-radius:var(--radius); padding:18px}
    .bar{height:10px; background:#0f1520; border:1px solid rgba(255,255,255,.06); border-radius:999px; overflow:hidden}
    .bar > span{display:block; height:100%; width:0%; background:linear-gradient(90deg, var(--acc), var(--acc-2)); border-radius:999px}
    .grid{display:grid; grid-template-columns: repeat(auto-fit,minmax(260px,1fr)); gap:20px}
    .card{background:var(--panel); border:1px solid rgba(255,255,255,.06); border-radius:var(--radius); padding:18px; position:relative; overflow:hidden; transition:transform .25s ease, box-shadow .25s ease}
    .card:hover{transform:translateY(-4px); box-shadow:0 16px 32px rgba(0,0,0,.45)}
    .card .badge{position:absolute; top:14px; right:14px; font-size:.8rem; color:#0d1117; background:linear-gradient(90deg, var(--acc), var(--acc-2)); padding:6px 10px; border-radius:999px; font-weight:800}
    form{display:grid; gap:12px; max-width:680px}
    input, textarea{width:100%; padding:14px 16px; border-radius:14px; border:1px solid rgba(255,255,255,.08); background:#0f1520; color:var(--text); outline:none; transition:border .2s, box-shadow .2s;}
    input:focus, textarea:focus{border-color:var(--acc); box-shadow: var(--ring)}
    button{padding:12px 16px; border-radius:14px; border:none; font-weight:800; cursor:pointer; background:linear-gradient(90deg, var(--acc), var(--acc-2)); color:#0d1117; box-shadow:var(--shadow);}
    footer{max-width:var(--maxw); margin:60px auto 30px; padding:0 20px; color:var(--muted); display:flex; justify-content:space-between; align-items:center}
    .top{position:fixed; right:20px; bottom:20px; border-radius:999px; padding:12px 14px; border:1px solid rgba(255,255,255,.15); background:#0f1520; display:none}
    .reveal{opacity:0; transform:translateY(14px); transition:opacity .6s ease, transform .6s ease}
    .reveal.show{opacity:1; transform:none}
    @media (max-width: 900px){.hero{grid-template-columns:1fr;} .about{grid-template-columns:1fr}}
  </style>
</head>
<body>
  <header id="top">
    <nav class="nav">
      <div class="brand">Lavanya<span>R</span></div>
      <a href="#about" class="nav-link">About</a>
      <a href="#skills" class="nav-link">Skills</a>
      <a href="#projects" class="nav-link">Projects</a>
      <a href="#contact" class="nav-link">Contact</a>
      <div class="spacer"></div>
      <a href="#contact" class="cta">Hire Me</a>
    </nav>
  </header>

  <section class="hero">
    <div>
      <div class="tag">Interactive Digital Portfolio</div>
      <h1>Hi, I'm <span style="color:var(--acc)">Ratakonda Lavanya</span>, a passionate <span style="color:var(--acc-2)">CSE(AIML)</span> student.</h1>
      <p>I love building user‑friendly web apps and applying AI/ML to real problems. This portfolio highlights my journey, skills, and projects.</p>
      <div class="chip-row reveal">
        <div class="chip">HTML</div>
        <div class="chip">CSS</div>
        <div class="chip">JavaScript</div>
        <div class="chip">Python</div>
        <div class="chip">Machine Learning</div>
      </div>
    </div>
  </section>

  <section id="about" class="about">
    <div class="panel reveal">
      <h2>About Me</h2>
      <p class="sub">Quick introduction</p>
      <p>I am currently pursuing B.Tech in CSE (AIML) at Mohan Babu University. My interests lie in AI/ML, Web Development, and building impactful tech solutions. I enjoy solving problems and collaborating on projects that make a difference.</p>
    </div>
    <div class="panel reveal">
      <h2>At a glance</h2>
      <ul>
        <li>Location: Tirupati, India</li>
        <li>Education: B.Tech CSE (AIML), Mohan Babu University</li>
        <li>Interests: AI, Web Development,Python</li>
        <li>Currently learning: Python ,Machine Learning, Deep Learning</li>
      </ul>
    </div>
  </section>

  <section id="skills">
    <h2>Skills</h2>
    <div class="skills-grid">
      <div class="skill reveal"><h4>HTML5</h4><div class="bar" data-level="95"><span></span></div></div>
      <div class="skill reveal"><h4>CSS3</h4><div class="bar" data-level="70"><span></span></div></div>
      <div class="skill reveal"><h4>Python</h4><div class="bar" data-level="80"><span></span></div></div>
      <div class="skill reveal"><h4>Machine Learning</h4><div class="bar" data-level="55"><span></span></div></div>
      <div class="skill reveal"><h4>Git</h4><div class="bar" data-level="55"><span></span></div></div>
    </div>
  </section>

  <section id="projects">
    <h2>Projects</h2>
    <div class="grid">
        <article class="card reveal">
  <span class="badge">Certification</span>
  <h3>Wipro TalentNext Certification</h3>
  <p>Repository containing programs and solutions completed as part of the Wipro TalentNext certification.</p>
  <a href="https://github.com/lavanyaratakonda/wipro_talentnext" target="_blank">View Project →</a>
</article>
      <article class="card reveal"><span class="badge">AI</span><h3>Early Anxiety Detection</h3><p>currently working on Deep learning project for detecting early signs of student anxiety and  stress.</p><a href=" " target="_blank">View Project →</a></article>
      <article class="card reveal"><span class="badge">Web</span><h3>Interactive Portfolio</h3><p>This portfolio website built with HTML, CSS, and JS.</p><a href="https://github.com/your-repo/portfolio" target="_blank">View Project →</a></article>
    </div>
  </section>
  <section id="certifications">
  <h2>Certifications</h2>
  <div class="grid">
    <article class="card reveal">
      <span class="badge">Microsoft & LinkedIn</span>
      <h3>Career Essentials Certificate</h3>
      <p>Completed Career Essentials program, strengthening professional and technical skills.</p>
      <a href="https://www.linkedin.com/learning/certificates/e9fc3523d29724742466536bbf77df33ec38b1a04f581b1e6957dea196e69691?trk=share_certificate" target="_blank">View Certificate →</a>
    </article>

    <article class="card reveal">
      <span class="badge">Udemy</span>
      <h3>Python for Data Science & ML Bootcamp</h3>
      <p>Comprehensive course covering Python, data science, and machine learning concepts.</p>
      <a href="https://www.udemy.com/certificate/UC-a5ba38af-2b41-46e8-9641-06ba22190601/" target="_blank">View Certificate →</a>
    </article>

    <article class="card reveal">
      <span class="badge">Accenture</span>
      <h3>Software Engineering Virtual Experience</h3>
      <p>Virtual internship by Accenture Nordics covering software engineering practices.</p>
      <a href="https://forage-uploads-prod.s3.amazonaws.com/completion-certificates/xhih9yFWsf6AYfngd/HNpZwZcuYwona2d8Y_xhih9yFWsf6AYfngd_85QCo4FRmqkKgp6Au_1751949998851_completion_certificate.pdf" target="_blank">View Certificate →</a>
    </article>

    <article class="card reveal">
      <span class="badge">Deloitte</span>
      <h3>Technology Virtual Experience</h3>
      <p>Virtual internship with Deloitte Australia focusing on technology solutions.</p>
      <a href="https://forage-uploads-prod.s3.amazonaws.com/completion-certificates/9PBTqmSxAf6zZTseP/udmxiyHeqYQLkTPvf_9PBTqmSxAf6zZTseP_85QCo4FRmqkKgp6Au_1751885337196_completion_certificate.pdf" target="_blank">View Certificate →</a>
    </article>
  </div>
</section>


  <section id="contact">
    <h2>Contact</h2>
    <div class="panel reveal" style="margin-top:20px; padding:16px; background:var(--panel); border-radius:var(--radius); border:1px solid rgba(255,255,255,.06);">
  <h3>My Contact Information</h3>
  <p><strong>Name:</strong> Ratakonda Lavanya</p>
  <p><strong>Mobile:</strong> 9346680668</p>
  <p><strong>Email:</strong> <a href="mailto:lavanyaratakonda24@gmail.com" style="color:var(--acc)">lavanyaratakonda24@gmail.com</a></p>
</div>
    <form class="reveal" id="contactForm" novalidate>
      <input id="name" name="name" placeholder="Your name" required />
      <input id="email" name="email" type="email" placeholder="you@example.com" required />
      <textarea id="message" name="message" rows="6" placeholder="Your message..." required></textarea>
      <button type="submit">Send Message</button>
      <p class="note" id="formNote"></p>
    </form>
  </section>

  <footer>
    <span>© <span id="year"></span> Lavanya Ratakonda</span>
    <a class="top" id="toTop" href="#top">↑</a>
  </footer>

  <script>
    const sections=document.querySelectorAll('section[id]');const navLinks=document.querySelectorAll('.nav-link');const spy=new IntersectionObserver((entries)=>{entries.forEach(entry=>{const id=entry.target.getAttribute('id');const link=document.querySelector(`.nav a[href="#${id}"]`);if(entry.isIntersecting){navLinks.forEach(a=>a.classList.remove('active'));link?.classList.add('active');}});},{ rootMargin:"-40% 0px -55% 0px", threshold:[0,.2,.6] });sections.forEach(s=>spy.observe(s));
    const reveals=document.querySelectorAll('.reveal');const revealIO=new IntersectionObserver((entries)=>{entries.forEach(e=>{if(e.isIntersecting){e.target.classList.add('show');revealIO.unobserve(e.target);}})},{threshold:.15});reveals.forEach(el=>revealIO.observe(el));
    const bars=document.querySelectorAll('.bar');const barIO=new IntersectionObserver((entries)=>{entries.forEach(e=>{if(e.isIntersecting){const target=e.target.querySelector('span');const lvl=e.target.dataset.level||70;requestAnimationFrame(()=>{target.style.width=lvl+'%'});barIO.unobserve(e.target);}})},{threshold:.6});bars.forEach(b=>barIO.observe(b));
    const form=document.getElementById('contactForm');const note=document.getElementById('formNote');form.addEventListener('submit',(ev)=>{ev.preventDefault();if(!form.checkValidity()){note.textContent='Please fill all fields correctly.';note.style.color='var(--danger)';return;}note.textContent='Thanks! Your message has been queued.';note.style.color='var(--ok)';form.reset();});
    const toTop=document.getElementById('toTop');const showTop=new IntersectionObserver(([e])=>{toTop.style.display=e.isIntersecting?'none':'inline-block';});showTop.observe(document.querySelector('header'));
    document.getElementById('year').textContent=new Date().getFullYear();
  </script>
</body>
</html>
