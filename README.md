
<html lang="en" class="scroll-smooth">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Techbuilder | Learn Computers</title>
<meta name="description" content="Learn computer basics, hardware, software, PC building and troubleshooting with Techbuilder">
<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js"></script>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;background:#fff;color:#17243a;line-height:1.6}
header{height:78px;border-top:4px solid #1769e0;border-bottom:1px solid #e7ebf0;display:flex;align-items:center;justify-content:space-between;padding:0 8%;position:sticky;top:0;background:rgba(255,255,255,.96);backdrop-filter:blur(8px);z-index:20}
.logo{display:inline-flex;align-items:center;gap:10px;font-size:24px;font-weight:800;color:#17243a;text-decoration:none;letter-spacing:-0.4px}
.logo-mark{display:inline-flex;align-items:center;justify-content:center;width:36px;height:36px;border-radius:10px;background:linear-gradient(135deg,#1769e0 0%,#0ea5e9 100%);box-shadow:0 6px 14px rgba(23,105,224,.28)}
.logo-text span{color:#1769e0}
nav a{color:#344054;text-decoration:none;margin-left:23px;font-size:14px;font-weight:600}
nav a:hover,nav a.active-nav{color:#1769e0}
nav a.active-nav{border-bottom:2px solid #1769e0;padding-bottom:4px}
.page-section{display:none}
.page-section.active-section{display:block}
.hero{padding:75px 8%;background:#f7faff;text-align:center}
.hero h1{font-size:clamp(32px,5vw,54px);line-height:1.15;max-width:750px;margin:auto}
.hero p{color:#667085;max-width:620px;margin:18px auto}
.search{max-width:550px;margin:28px auto;display:flex;background:white;border:1px solid #dce3ed;border-radius:10px;overflow:hidden}
.search input{flex:1;min-width:0;padding:15px;border:0;outline:0;font-size:15px}
.search button,.btn{background:#1769e0;color:white;border:0;padding:14px 22px;cursor:pointer;text-decoration:none;border-radius:8px;font-weight:600;font-size:14px;display:inline-block}
.btn-outline{background:#fff;color:#1769e0;border:1px solid #1769e0;padding:11px 18px;border-radius:8px;cursor:pointer;font-weight:600;font-size:13px}
.btn-outline:hover{background:#f0f6ff}
.container{max-width:1150px;margin:auto;padding:65px 22px}
.heading{text-align:center;margin-bottom:35px}
.heading h2{font-size:30px}
.heading p{color:#667085;margin-top:8px}
.grid{display:grid;grid-template-columns:repeat(3,1fr);gap:20px}
.card{border:1px solid #e7ebf0;border-radius:12px;padding:25px;transition:.2s;background:#fff}
.card:hover{transform:translateY(-4px);box-shadow:0 8px 25px #17243a10}
.card .icon{font-size:32px;margin-bottom:12px}
.card h3{font-size:19px;margin-bottom:8px}
.card p{font-size:14px;color:#667085;margin-bottom:16px}
.card a{color:#1769e0;text-decoration:none;font-weight:bold;font-size:14px;cursor:pointer}
.feature{background:#f7faff;border-radius:16px;padding:35px;display:flex;align-items:center;justify-content:space-between;gap:20px}
.feature p{color:#667085;margin:10px 0 20px}
footer{background:#101d32;color:white;padding:35px 8%;text-align:center}
footer p{color:#bdc8d8;font-size:13px;margin-top:8px}
#noResults{text-align:center;color:#667085;padding:25px;display:none}

/* Interactive 3D Lab & Weekly Guide Panels */
.lab-wrap{display:grid;grid-template-columns:1.15fr 1fr;gap:24px;align-items:stretch}
.canvas-box{position:relative;background:radial-gradient(circle at 55% 40%,#eef5ff,#dce8fb 80%);border:1px solid #dce3ed;border-radius:16px;min-height:380px;overflow:hidden}
.canvas-box canvas{display:block;width:100%;height:100%;cursor:grab;touch-action:none}
.canvas-box canvas:active{cursor:grabbing}
.hud-top{position:absolute;top:14px;left:14px;background:rgba(255,255,255,.92);border:1px solid #dce3ed;padding:6px 12px;border-radius:999px;font-size:12px;font-weight:700;color:#17243a;pointer-events:none}
.hud-bottom{position:absolute;bottom:14px;left:14px;right:14px;display:flex;flex-wrap:wrap;gap:8px;justify-content:space-between}
.hud-btn{background:rgba(255,255,255,.94);border:1px solid #cfd9e8;color:#17243a;padding:7px 13px;border-radius:999px;font-size:12px;font-weight:600;cursor:pointer}
.hud-btn.active{background:#1769e0;color:#fff;border-color:#1769e0}
.info-panel{border:1px solid #e7ebf0;border-radius:16px;padding:24px;background:#fff;display:flex;flex-direction:column;justify-content:space-between;gap:16px}
.part-tabs{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:20px;justify-content:center}
.part-tab{border:1px solid #dce3ed;background:#fff;color:#344054;padding:8px 14px;border-radius:999px;font-size:13px;font-weight:600;cursor:pointer}
.part-tab.active{background:#1769e0;color:#fff;border-color:#1769e0}
.pill-list{display:flex;flex-wrap:wrap;gap:6px;margin-top:8px}
.pill{background:#f0f6ff;border:1px solid #d4e4fc;color:#1769e0;padding:4px 10px;border-radius:999px;font-size:12px;font-weight:600}
.guide-card{border:1px solid #e7ebf0;border-radius:16px;padding:30px;background:#fff}
.guide-meta{font-size:12px;color:#667085;background:#f7faff;border:1px solid #e7ebf0;padding:10px 14px;border-radius:8px;margin-bottom:18px}
.guide-section{margin-top:20px}
.guide-section h4{font-size:17px;color:#17243a;margin-bottom:8px}
.guide-section ul,.guide-section ol{padding-left:20px;color:#344054;font-size:14px}
.guide-section li{margin-bottom:6px}
.quiz-box{margin-top:22px;background:#f7faff;border:1px solid #dce3ed;border-radius:12px;padding:20px}
.quiz-opt{display:block;width:100%;text-align:left;margin-top:8px;padding:10px 14px;border-radius:8px;border:1px solid #dce3ed;background:#fff;cursor:pointer;font-size:14px;color:#17243a}
.quiz-opt:hover{border-color:#1769e0}
.quiz-opt.correct{background:#ecfdf3;border-color:#12b76a;color:#027a48;font-weight:600}
.quiz-opt.wrong{background:#fef3f2;border-color:#f04438;color:#b42318}
.book-reader{background:#f7faff;border:1px solid #dce3ed;border-radius:14px;padding:22px;margin-top:16px;font-size:14.5px;line-height:1.7;color:#1e293b}
.book-grid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:16px;margin-top:14px}
.book-rect{background:#fff;border:1px solid #dce3ed;border-radius:12px;padding:18px;box-shadow:0 2px 10px rgba(15,23,42,.03)}
.book-wide{grid-column:1 / -1}
@media(max-width:780px){.book-grid{grid-template-columns:1fr}}
.book-reader h3{font-size:24px;color:#1769e0;border-bottom:2px solid #eef5ff;padding-bottom:10px;margin-bottom:16px}
.book-reader h4{font-size:19px;color:#17243a;margin:24px 0 10px}
.book-reader h5{font-size:16px;color:#1769e0;margin:18px 0 8px}
.book-reader p{margin-bottom:14px}
.book-fig{background:#f7faff;border:1px dashed #93c5fd;border-radius:10px;padding:12px 16px;margin:14px 0;font-size:13.5px;color:#1e40af}
.book-cmd{background:#0f172a;color:#e2e8f0;font-family:monospace;font-size:13px;line-height:1.6;padding:14px 16px;border-radius:10px;margin:12px 0;overflow-x:auto;white-space:pre}
@media(max-width:600px){.book-reader{padding:18px;font-size:14.5px}}
.course-badge{display:inline-block;background:#eef5ff;color:#1769e0;font-size:11px;font-weight:700;padding:3px 9px;border-radius:999px;margin-bottom:10px}
.playground{display:grid;grid-template-columns:1fr 1fr;gap:16px;margin-top:16px}
.code-editor{width:100%;min-height:170px;font-family:monospace;font-size:13px;padding:12px;border:1px solid #dce3ed;border-radius:10px;background:#0f172a;color:#e2e8f0;resize:vertical}
.code-preview{border:1px solid #dce3ed;border-radius:10px;padding:14px;background:#fff;min-height:170px}
@media(max-width:750px){.playground{grid-template-columns:1fr}}

@media(max-width:850px){.lab-wrap{grid-template-columns:1fr}}
@media(max-width:750px){
header{padding:0 5%;height:auto;min-height:70px;flex-wrap:wrap}
nav{width:100%;padding:10px 0 15px;display:flex;gap:17px;overflow-x:auto}
nav a{margin:0;white-space:nowrap}
.grid{grid-template-columns:repeat(2,1fr)}
.feature{display:block}
}
@media(max-width:480px){.grid{grid-template-columns:1fr}.hero{padding:55px 5%}}
</style>
</head>
<body>

<header>
  <a href="#sec-home" class="logo section-jump" data-target="sec-home">
    <span class="logo-mark" aria-hidden="true">
      <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="#ffffff" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
        <path d="M12 2L2 7l10 5 10-5-10-5z"/>
        <path d="M2 17l10 5 10-5"/>
        <path d="M2 12l10 5 10-5"/>
      </svg>
    </span>
    <span class="logo-text">Tech<span>builder</span></span>
  </a>
  <nav id="mainNav">
    <a href="#sec-home" class="nav-tab active-nav" data-target="sec-home">Home</a>
    <a href="#sec-topics" class="nav-tab" data-target="sec-topics">Topics</a>
    <a href="#sec-hardware" class="nav-tab" data-target="sec-hardware">3D Hardware</a>
    <a href="#sec-courses" class="nav-tab" data-target="sec-courses">Courses</a>
    <a href="#sec-builder" class="nav-tab" data-target="sec-builder">Builder</a>
    <a href="#sec-basics" class="nav-tab" data-target="sec-basics">Guides</a>
    <a href="#sec-about" class="nav-tab" data-target="sec-about">About</a>
  </nav>
</header>

<section class="hero page-section active-section" id="sec-home">
  <div style="display:inline-block;background:linear-gradient(135deg,#e0f2fe 0%,#dbeafe 100%);border:1px solid #7dd3fc;color:#0369a1;font-size:13.5px;font-weight:700;padding:9px 20px;border-radius:999px;margin-bottom:20px;box-shadow:0 6px 18px rgba(14,165,233,0.18)">
    Thanks for visiting Techbuilder! Your curiosity for learning computers &amp; coding makes you unstoppable.
  </div>
  <h1>Understand Computers.<br>Build Your Knowledge.</h1>
  <p>Your beginner-friendly destination to learn computer hardware in 3D, software, PC building, and troubleshooting.</p>
  <div class="search" style="margin-bottom:10px">
    <input id="searchInput" type="search" placeholder="Live search anything: CPU, RTX 4060, SEBA, PAN/LAN, HTML, Python...">
    <button type="button" id="searchBtn">Search</button>
  </div>
  <div id="liveSearchResults" style="display:none;max-width:550px;margin:0 auto 22px;background:#fff;border:1px solid #dce3ed;border-radius:12px;text-align:left;box-shadow:0 12px 30px rgba(15,23,42,.1);max-height:290px;overflow-y:auto"></div>
  <a href="#sec-hardware" class="btn section-jump" data-target="sec-hardware">Explore 3D PC →</a>
</section>

<section class="container page-section" id="sec-topics" style="padding-top:35px">
  <div class="heading">
    <h2>Explore Computer Topics</h2>
    <p>Everything you need to know about computers in one place.</p>
  </div>

  <div class="grid" id="topicGrid">
    <article class="card" data-search="computer basics beginner introduction ipos input output">
      <div class="icon">💻</div>
      <h3>Computer Basics</h3>
      <p>Understand computers, their functions, types and how data flows from click to screen.</p>
      <a href="#sec-basics" class="section-jump" data-target="sec-basics" data-guide="basics">Learn More →</a>
    </article>

    <article class="card" data-search="hardware cpu ram gpu motherboard ssd psu ryzen rtx 4060 samsung 990 pro">
      <div class="icon">⚙️</div>
      <h3>Computer Hardware</h3>
      <p>Discover CPU, RAM, GPU, motherboard, storage and real product names in 3D.</p>
      <a href="#sec-hardware" class="section-jump" data-target="sec-hardware">Explore 3D →</a>
    </article>

    <article class="card" data-search="software windows linux macos applications os">
      <div class="icon">🖥️</div>
      <h3>Software &amp; OS</h3>
      <p>Learn about operating systems, applications and how software talks to hardware.</p>
      <a href="#sec-basics" data-topic="software" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>

    <article class="card" data-search="pc build gaming computer budget components">
      <div class="icon">🔧</div>
      <h3>PC Building</h3>
      <p>Understand compatible computer components and beginner-to-pro PC configurations.</p>
      <a href="#sec-hardware" class="section-jump" data-target="sec-hardware">Inspect Parts →</a>
    </article>

    <article class="card" data-search="troubleshooting repair problems overheating slow">
      <div class="icon">🛠️</div>
      <h3>Troubleshooting</h3>
      <p>Understand common computer issues, thermal throttling, and quick fixes.</p>
      <a href="#sec-basics" data-topic="troubleshooting" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>

    <article class="card" data-search="technology internet networking wifi router">
      <div class="icon">🌐</div>
      <h3>Technology</h3>
      <p>Explore the internet, networking, Wi-Fi, and modern computing.</p>
      <a href="#sec-basics" data-topic="technology" data-target="sec-basics" class="topic-jump section-jump">Learn More →</a>
    </article>
  </div>
  <p id="noResults">No matching topics found. Try another search.</p>
</section>

<!-- INTERACTIVE 3D HARDWARE SECTION -->
<section class="container page-section" id="sec-hardware" style="padding-top:35px">
  <div class="heading">
    <h2>Interactive 3D Computer Hardware</h2>
    <p>Rotate the 3D PC, explode the case, or click any component to see what it does and real product names.</p>
  </div>

  <div class="part-tabs" id="partTabs"></div>

  <div class="lab-wrap">
    <div class="canvas-box" id="pcCanvasWrap">
      <div class="hud-top" id="hudLabel">Full Desktop PC — Drag to Rotate</div>
      <div class="hud-bottom">
        <div style="display:flex;gap:8px;flex-wrap:wrap">
          <button type="button" class="hud-btn active" id="viewModeBtn">Mode: Mini-Parts 3D</button>
          <button type="button" class="hud-btn" id="explodeBtn">Explode Mini-Parts</button>
          <button type="button" class="hud-btn active" id="spinBtn">Auto-Spin: ON</button>
        </div>
        <button type="button" class="hud-btn" id="resetCamBtn">Reset Angle</button>
      </div>
    </div>

    <div class="info-panel">
      <div>
        <span style="font-size:12px;font-weight:700;color:#1769e0;text-transform:uppercase" id="partCat">Core Processing</span>
        <h3 style="font-size:24px;margin-top:4px" id="partTitle">CPU (Processor)</h3>
        <p style="font-size:14px;font-weight:600;color:#344054;margin-top:4px" id="partAnalogy"></p>
        <p style="font-size:14px;color:#667085;margin-top:12px" id="partDesc"></p>

        <div style="margin-top:16px">
          <strong style="font-size:12px;color:#344054;text-transform:uppercase">Popular Real-World Product Names</strong>
          <div class="pill-list" id="partProducts"></div>
        </div>
      </div>

      <div style="margin-top:4px">
        <strong style="font-size:12px;color:#344054;text-transform:uppercase">Small Mini-Parts Inside (Click any in 3D or below)</strong>
        <div class="pill-list" id="miniPartsList"></div>
        <div id="miniPartDetail" style="margin-top:10px;background:#eef5ff;border:1px solid #cfe0fc;border-radius:10px;padding:12px;font-size:13px;color:#17243a"></div>
      </div>

      <div style="background:#f7faff;border:1px solid #e7ebf0;border-radius:10px;padding:14px">
        <strong style="font-size:12px;color:#17243a">Where It Connects:</strong>
        <p style="font-size:13px;color:#667085;margin-top:4px" id="partConnect"></p>
      </div>
    </div>
  </div>
</section>

<!-- CODING & TECH COURSES SECTION -->
<section class="container page-section" id="sec-courses" style="padding-top:35px">
  <div class="heading">
    <h2>Beginner Coding &amp; Tech Courses</h2>
    <p>Learn HTML, CSS, JavaScript, Python, Git &amp; GitHub, and SQL—step by step with live practice.</p>
  </div>

  <div class="grid" id="courseGrid">
    <article class="card" style="border:2px solid #1769e0;background:#f7faff" data-search="how to make a website full expert course build deploy seo html css js">
      <div class="course-badge" style="background:#1769e0;color:#fff">Full Expert Course • 7 Modules</div>
      <div class="icon">🚀</div>
      <h3>How to Make a Website</h3>
      <p>Complete step-by-step expert masterclass: Planning, Semantic HTML5, CSS Grid/Flexbox, JS, SEO, Speed, &amp; Going Live.</p>
      <a href="#coursePlayer" class="course-open" data-course="webdev">Open Expert Course →</a>
    </article>

    <article class="card" style="border:2px solid #059669;background:#f0fdf4" data-search="class 10 computer science seba board assam hslc c programming mysql networks oop">
      <div class="course-badge" style="background:#059669;color:#fff">SEBA Board • Class 10</div>
      <div class="icon">📘</div>
      <h3>Class 10 Computer Science (SEBA)</h3>
      <p>Complete Assam SEBA Class X syllabus: Networks, HTML/CSS3, MySQL, C Loops/Arrays/Functions, OOP &amp; Practicals.</p>
      <a href="#coursePlayer" class="course-open" data-course="seba10">Open SEBA Class 10 →</a>
    </article>

    <article class="card" data-search="html web structure tags elements headings links">
      <div class="course-badge">Web Foundation</div>
      <div class="icon">🧱</div>
      <h3>HTML5 Basics</h3>
      <p>Build the structure of any webpage using headings, paragraphs, links, images, and forms.</p>
      <a href="#coursePlayer" class="course-open" data-course="html">Start HTML Course →</a>
    </article>

    <article class="card" data-search="css styling colors flexbox grid responsive design">
      <div class="course-badge">Web Design</div>
      <div class="icon">🎨</div>
      <h3>CSS3 Styling</h3>
      <p>Style websites with colors, fonts, spacing, Flexbox, Grid, and mobile-friendly layouts.</p>
      <a href="#coursePlayer" class="course-open" data-course="css">Start CSS Course →</a>
    </article>

    <article class="card" data-search="javascript js programming interactivity dom events">
      <div class="course-badge">Interactivity</div>
      <div class="icon">⚡</div>
      <h3>JavaScript Essentials</h3>
      <p>Make pages interactive with variables, functions, button clicks, and live DOM updates.</p>
      <a href="#coursePlayer" class="course-open" data-course="js">Start JS Course →</a>
    </article>

    <article class="card" data-search="java oop android programming classes objects beginner">
      <div class="course-badge">OOP &amp; Apps</div>
      <div class="icon">☕</div>
      <h3>Java Programming</h3>
      <p>Learn object-oriented programming, classes, loops, and how Java powers Android apps &amp; enterprise software.</p>
      <a href="#coursePlayer" class="course-open" data-course="java">Start Java Course →</a>
    </article>

    <article class="card" data-search="python coding beginner logic loops functions">
      <div class="course-badge">Programming</div>
      <div class="icon">🐍</div>
      <h3>Python for Beginners</h3>
      <p>Learn clean, readable programming from variables and loops to simple automation scripts.</p>
      <a href="#coursePlayer" class="course-open" data-course="python">Start Python Course →</a>
    </article>

    <article class="card" data-search="git github version control commits repositories">
      <div class="course-badge">Workflow</div>
      <div class="icon">🌿</div>
      <h3>Git &amp; GitHub</h3>
      <p>Save code versions, collaborate with classmates, and publish your projects online.</p>
      <a href="#coursePlayer" class="course-open" data-course="git">Start Git Course →</a>
    </article>

    <article class="card" data-search="sql database tables queries data storage">
      <div class="course-badge">Data</div>
      <div class="icon">🗄️</div>
      <h3>Databases &amp; SQL</h3>
      <p>Organize information in tables and fetch exact records using simple SQL queries.</p>
      <a href="#coursePlayer" class="course-open" data-course="sql">Start SQL Course →</a>
    </article>
  </div>

  <!-- Interactive Course Lesson & Live Playground -->
  <div class="guide-card" id="coursePlayer" style="margin-top:24px">
    <div style="display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:10px">
      <div>
        <span class="course-badge" id="courseBadge">Web Foundation</span>
        <h3 id="courseTitle" style="font-size:22px;color:#17243a">HTML5 Basics — Lesson 1: Your First Webpage</h3>
      </div>
      <button type="button" class="btn-outline" id="runCodeBtn">Run Live Preview</button>
    </div>
    <p id="courseDesc" style="font-size:14px;color:#667085;margin-top:8px"></p>

    <div id="courseDetailGrid" class="book-grid" style="display:none;margin-top:16px"></div>

    <div id="expertModulesWrap" style="display:none;margin-top:16px">
      <div class="part-tabs" id="expertModuleTabs" style="justify-content:flex-start;margin-bottom:12px"></div>
      <div id="expertModuleBody" style="background:#f7faff;border:1px solid #dce3ed;border-radius:12px;padding:18px;font-size:14px;color:#17243a"></div>
    </div>

    <div class="playground">
      <div>
        <label for="courseCode" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:6px">Editable Code / Example</label>
        <textarea id="courseCode" class="code-editor" spellcheck="false"></textarea>
      </div>
      <div>
        <span style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:6px">Live Output / Result</span>
        <div id="courseOutput" class="code-preview"></div>
      </div>
    </div>
  </div>
</section>

<!-- INTERACTIVE WEBSITE BUILDER & RUNNER -->
<section class="container page-section" id="sec-builder" style="padding-top:35px">
  <div class="heading">
    <h2>Live Website Builder &amp; Runner</h2>
    <p>Choose a website type, type what you want, and run your own working website right here.</p>
  </div>

  <div class="guide-card" style="margin-bottom:22px">
    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(190px,1fr));gap:14px">
      <div>
        <label for="wbType" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Website Type</label>
        <select id="wbType" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px;background:#fff">
          <option value="portfolio">Personal Portfolio</option>
          <option value="store">Online Store / Shop</option>
          <option value="blog">Tech &amp; Study Blog</option>
          <option value="landing">Product / App Landing Page</option>
        </select>
      </div>
      <div>
        <label for="wbName" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Website Name</label>
        <input id="wbName" type="text" value="MyAwesomeSite" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px">
      </div>
      <div>
        <label for="wbColor" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Accent Color</label>
        <select id="wbColor" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px;background:#fff">
          <option value="#1769e0">Royal Blue (#1769e0)</option>
          <option value="#8E44EC">Electric Purple (#8E44EC)</option>
          <option value="#059669">Emerald Green (#059669)</option>
          <option value="#e11d48">Vibrant Rose (#e11d48)</option>
        </select>
      </div>
      <div>
        <label for="wbTheme" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Theme Style</label>
        <select id="wbTheme" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px;background:#fff">
          <option value="light">Clean Light Mode</option>
          <option value="dark">Modern Dark Mode</option>
        </select>
      </div>
    </div>

    <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:14px;margin-top:14px">
      <div>
        <label for="wbHeadline" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Main Hero Headline</label>
        <input id="wbHeadline" type="text" value="Build Something Amazing Today" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px">
      </div>
      <div>
        <label for="wbCtaText" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">Button Text</label>
        <input id="wbCtaText" type="text" value="Get Started" style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px">
      </div>
    </div>

    <div style="margin-top:14px">
      <label for="wbGoal" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:5px">What do you want your website to say or offer?</label>
      <input id="wbGoal" type="text" value="A fast, modern website built for students and creators." style="width:100%;padding:10px;border:1px solid #dce3ed;border-radius:8px;font-size:14px">
    </div>

    <div style="margin-top:14px;display:flex;flex-wrap:wrap;gap:18px;font-size:13px;color:#344054">
      <label style="display:flex;align-items:center;gap:6px;cursor:pointer">
        <input type="checkbox" id="wbIncludeCards" checked> Include 3-Card Feature Section
      </label>
      <label style="display:flex;align-items:center;gap:6px;cursor:pointer">
        <input type="checkbox" id="wbIncludeContact" checked> Include Contact Form
      </label>
    </div>

    <div style="margin-top:16px;display:flex;flex-wrap:wrap;gap:10px">
      <button type="button" class="btn" id="wbGenerateBtn">Generate &amp; Run Website</button>
      <button type="button" class="btn-outline" id="wbRunCodeBtn">Run Code</button>
      <button type="button" class="btn-outline" id="wbDownloadBtn">Download index.html</button>
    </div>
  </div>

  <div class="playground">
    <div>
      <label for="wbCode" style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:6px">Generated Website Code (HTML + CSS + JS)</label>
      <textarea id="wbCode" class="code-editor" style="min-height:360px" spellcheck="false"></textarea>
    </div>
    <div>
      <span style="display:block;font-size:12px;font-weight:700;color:#344054;margin-bottom:6px">Live Running Website</span>
      <iframe id="wbPreview" title="Live Website Preview" style="width:100%;min-height:360px;border:1px solid #dce3ed;border-radius:10px;background:#fff"></iframe>
    </div>
  </div>
</section>

<!-- FEATURE BANNER -->
<section class="container page-section" id="sec-guides-banner" style="padding-top:35px">
  <div class="feature">
    <div>
      <h2>Start Your Computer Learning Journey</h2>
      <p>Read this week's step-by-step beginner guide and test yourself with the interactive quiz below.</p>
      <a class="btn" href="#basics">Read This Week's Guide</a>
    </div>
    <div style="font-size:75px">🚀</div>
  </div>
</section>

<!-- WEEKLY LEARNING GUIDE SECTION -->
<section class="container page-section" id="sec-basics" style="padding-top:35px">
  <div class="heading">
    <h2>Weekly Beginner Guide</h2>
    <p>Clear, student-friendly lessons that build your computer knowledge step by step.</p>
  </div>

  <div class="part-tabs" id="guideTabs">
    <button type="button" class="part-tab active" data-guide="basics">1. Computer Basics (This Week)</button>
    <button type="button" class="part-tab" data-guide="software">2. Software &amp; OS</button>
    <button type="button" class="part-tab" data-guide="troubleshooting">3. Troubleshooting</button>
    <button type="button" class="part-tab" data-guide="technology">4. Internet &amp; Wi-Fi</button>
  </div>

  <article class="guide-card" id="guideContent"></article>
</section>

<section class="container page-section" id="sec-about" style="padding-top:35px">
  <div class="heading">
    <h2>About Techbuilder</h2>
    <p>Our goal is to make computer education easy and accessible for everyone, especially beginners and students.</p>
  </div>
  <div class="guide-card" style="max-width:640px;margin:0 auto;text-align:center">
    <span class="course-badge">Creator</span>
    <h3 style="font-size:24px;color:#17243a;margin-top:4px">Mehetab Hussain</h3>
    <p style="font-size:14px;color:#667085;margin-top:10px">
      Created by <strong>Mehetab Hussain</strong> to help beginners and students learn computer hardware in interactive 3D, real-world PC parts, coding courses, and step-by-step guides.
    </p>
  </div>
</section>

<footer>
  <h2>Techbuilder</h2>
  <p>Learn computers. Understand technology. Build your knowledge.</p>
  <p>© 2026 Techbuilder — Created by Mehetab Hussain. All rights reserved.</p>
</footer>

<script>
const PARTS = [
  {
    id: 'cpu', name: 'CPU (Processor)',
    miniParts: [
      { id: 'ihs', name: 'Heat Spreader Lid (IHS)', desc: 'Metal lid on top that spreads heat evenly into the cooler.' },
      { id: 'die', name: 'Silicon Die & Cores', desc: 'Microscopic silicon chip containing CPU cores and ultra-fast L3 cache.' },
      { id: 'substrate', name: 'Substrate PCB', desc: 'Multi-layer green/blue board that routes signals from the tiny die to the pins.' },
      { id: 'pins', name: 'Gold Contact Pads/Pins', desc: 'Hundreds of gold contacts underneath that carry power and data to the motherboard.' },
      { id: 'smd', name: 'Micro Capacitors (SMDs)', desc: 'Tiny surface-mount capacitors that keep voltage steady for each core.' }
    ], cat: 'Core Processing',
    analogy: 'Analogy: The Brain of the Computer',
    desc: 'Executes instructions from your apps, games, and operating system billions of times per second.',
    products: ['AMD Ryzen 5 7600', 'Intel Core i5-14400F', 'AMD Ryzen 7 7800X3D', 'AMD Ryzen 9 7950X'],
    connect: 'Drops into the CPU socket on the center-top of the Motherboard under the cooler.'
  },
  {
    id: 'gpu', name: 'GPU (Graphics Card)',
    miniParts: [
      { id: 'fans', name: 'Dual Axial Fans', desc: 'Curved fan blades that push cool air down through the heatsink.' },
      { id: 'heatsink', name: 'Heatsink Fins & Heatpipes', desc: 'Stacked aluminum fins and copper pipes that pull heat away from the chip.' },
      { id: 'gpudie', name: 'GPU Die & 8x VRAM Chips', desc: 'Central graphics chip surrounded by fast GDDR6 video memory chips.' },
      { id: 'pcie', name: 'PCIe x16 Gold Connector', desc: 'Bottom gold edge connector that plugs into the motherboard.' },
      { id: 'io', name: 'HDMI & DisplayPort Bracket', desc: 'Metal rear bracket with ports that plug into your monitor.' }
    ], cat: 'Graphics & 3D',
    analogy: 'Analogy: A Team of Visual Artists',
    desc: 'Uses thousands of parallel cores to draw 3D shapes, lighting, shadows, and pixels onto your monitor.',
    products: ['NVIDIA GeForce RTX 4060 8GB', 'Sapphire Radeon RX 7700 XT', 'NVIDIA GeForce RTX 5070 12GB', 'NVIDIA GeForce RTX 5070 Ti'],
    connect: 'Plugs into the long PCIe x16 slot on the Motherboard and connects to your monitor.'
  },
  {
    id: 'motherboard', name: 'Motherboard',
    miniParts: [
      { id: 'socket', name: 'CPU Socket & Retention Frame', desc: 'Precision slot in the center-top that holds the CPU securely.' },
      { id: 'vrm', name: 'VRM Heatsinks & Chokes', desc: 'Power delivery blocks that step down voltage cleanly for the CPU.' },
      { id: 'dimm', name: '4x DIMM RAM Slots', desc: 'Long vertical slots with locking latches for memory sticks.' },
      { id: 'pcieslot', name: 'Reinforced PCIe x16 Slot', desc: 'Metal-armored horizontal slot where the heavy GPU plugs in.' },
      { id: 'cmos', name: 'CMOS Coin Battery (CR2032)', desc: 'Round silver battery that keeps your BIOS settings and clock saved.' }
    ], cat: 'System Hub',
    analogy: 'Analogy: The City Road Network',
    desc: 'The main circuit board that links the CPU, RAM, GPU, SSD, and USB ports so they can share power and data.',
    products: ['ASUS TUF Gaming B650M-PLUS WiFi', 'ASUS ROG Strix B650E-F', 'Gigabyte B760 Gaming X AX', 'ASUS ProArt X670E-Creator'],
    connect: 'Mounts directly to the PC case; almost every internal component plugs into it.'
  },
  {
    id: 'ram', name: 'RAM (Memory)',
    miniParts: [
      { id: 'spreader', name: 'Aluminum Heatspreader', desc: 'Sleek metal shell that keeps memory chips cool under load.' },
      { id: 'rgb', name: 'RGB Light Diffuser Bar', desc: 'Top light bar for customizable system lighting.' },
      { id: 'dram', name: '8x DRAM Memory Chips', desc: 'Black silicon memory chips soldered onto the stick that hold active data.' },
      { id: 'gold', name: '288-Pin Gold Edge + Notch', desc: 'Gold contacts with an off-center notch so you can only insert it the right way.' }
    ], cat: 'Fast Workspace',
    analogy: 'Analogy: Your Study Desk',
    desc: 'Holds the apps and files you are actively using right now for instant access, then clears when powered off.',
    products: ['Corsair Vengeance RGB 32GB DDR5', 'G.Skill Trident Z5 DDR5-6400', 'Corsair Vengeance LPX 16GB', 'G.Skill Flare X5 32GB'],
    connect: 'Snaps vertically into the DIMM slots right next to the CPU.'
  },
  {
    id: 'ssd', name: 'SSD (Storage)',
    miniParts: [
      { id: 'ctrl', name: 'NVMe Controller Chip', desc: 'Tiny built-in processor that decides where to read and write your files.' },
      { id: 'nand', name: '3D NAND Flash Chips', desc: 'Memory chips that store your apps and photos permanently without power.' },
      { id: 'cache', name: 'DRAM Cache Chip', desc: 'Small fast buffer chip that speeds up file lookups.' },
      { id: 'mkey', name: 'M-Key Gold Connector', desc: 'Edge connector that slides into the motherboard M.2 slot.' }
    ], cat: 'Permanent Vault',
    analogy: 'Analogy: Your Filing Cabinet',
    desc: 'Stores your operating system, apps, and school files permanently—even when the computer is unplugged.',
    products: ['Samsung 990 PRO 1TB NVMe', 'WD Black SN850X 2TB NVMe', 'Crucial T500 1TB Gen4', 'Lexar NM790 1TB NVMe'],
    connect: 'M.2 NVMe SSDs screw flat onto the Motherboard; SATA SSDs use a data cable.'
  },
  {
    id: 'psu', name: 'Power Supply (PSU)',
    miniParts: [
      { id: 'psufan', name: '120mm Intake Fan', desc: 'Pulls cool air over internal transformers and heatsinks.' },
      { id: 'trans', name: 'Main Transformer & Coils', desc: 'Steps high-voltage wall AC down to safe 12V, 5V, and 3.3V.' },
      { id: 'caps', name: 'Bulk Capacitors', desc: 'Large cylindrical capacitors that smooth out power ripples.' },
      { id: 'modular', name: 'Modular Cable Ports', desc: 'Sockets on the back for 24-pin motherboard and 8-pin GPU power cables.' }
    ], cat: 'Power Delivery',
    analogy: 'Analogy: The Power Converter',
    desc: 'Safely converts high-voltage wall AC power into steady low-voltage DC power for delicate chips.',
    products: ['Corsair CX450 450W', 'Corsair RM750x 750W Gold', 'Seasonic Focus GX-1000 Gold', 'EVGA SuperNOVA 1000 G6'],
    connect: 'Mounts at the bottom of the PC case with cables running to the Motherboard and GPU.'
  },
  {
    id: 'cooling', name: 'Cooling & Fans',
    miniParts: [
      { id: 'blades', name: '7-Blade PWM Impeller', desc: 'Angled blades spun by a brushless motor to move air quietly.' },
      { id: 'pipes', name: 'Copper Heatpipes', desc: 'Sealed copper tubes that carry heat from the CPU up into the fins.' },
      { id: 'fins', name: 'Aluminum Fin Stack', desc: 'Dozens of thin metal plates that release heat into the airflow.' },
      { id: 'coldplate', name: 'Copper Cold Plate', desc: 'Flat mirror-smooth base that sits directly on the CPU lid.' }
    ], cat: 'Airflow & Heat',
    analogy: 'Analogy: A/C for Electronics',
    desc: 'Pulls cool air in and pushes hot air out so your CPU and GPU never slow down from overheating.',
    products: ['Thermalright Peerless Assassin 120 SE', 'Noctua NH-U12A', 'DeepCool AK620', 'Arctic Liquid Freezer II 280mm'],
    connect: 'Screws onto the PC case and CPU socket, powered by 4-pin fan headers.'
  },
  {
    id: 'monitor', name: 'Monitor (Display)', cat: 'Output Device',
    analogy: 'Analogy: The Digital Canvas',
    desc: 'Turns signals from your GPU into millions of sharp, fast-refreshing pixels on your desk.',
    miniParts: [
      { id: 'panel', name: 'IPS / OLED Display Panel', desc: 'Front liquid-crystal or OLED layer that creates colors and images.' },
      { id: 'backlight', name: 'LED Backlight & Diffuser', desc: 'Evenly lights up the screen from behind so colors stay bright.' },
      { id: 'tcon', name: 'Timing Controller (T-Con) Board', desc: 'Translates HDMI/DisplayPort signals into row-by-row pixel commands.' },
      { id: 'stand', name: 'Ergonomic Stand & Base', desc: 'Holds the display steady and lets you adjust height and tilt.' },
      { id: 'mports', name: 'HDMI & DisplayPort Inputs', desc: 'Rear ports that receive video cables from your GPU.' }
    ],
    products: ['ASUS ProArt 27" QHD Display', 'Dell S2417DG 24" 165Hz', 'LG UltraGear 27GL850', 'BenQ SW272U 4K'],
    connect: 'Plugs into your GPU via HDMI or DisplayPort cable and into a wall power outlet.'
  },
  {
    id: 'peripherals', name: 'Keyboard & Mouse', cat: 'Input Devices',
    analogy: 'Analogy: Your Hands & Controls',
    desc: 'Captures every keystroke and hand movement and sends instant USB or wireless signals to the CPU.',
    miniParts: [
      { id: 'keycaps', name: 'PBT / ABS Keycaps', desc: 'Removable lettered caps you press with your fingers.' },
      { id: 'switches', name: 'Mechanical Key Switches', desc: 'Spring-loaded switches under each keycap that register clicks.' },
      { id: 'kpcb', name: 'Keyboard PCB & USB-C Port', desc: 'Circuit board that scans key presses and sends them over USB.' },
      { id: 'sensor', name: 'Optical Mouse Sensor', desc: 'Tiny high-speed camera underneath the mouse that tracks surface movement.' },
      { id: 'scroll', name: 'Scroll Wheel & Micro-Switches', desc: 'Encoder wheel and left/right click switches inside the mouse.' }
    ],
    products: ['Corsair Strafe RGB', 'Logitech K120 Keyboard', 'Keychron K2 Pro', 'Logitech G Pro X Superlight'],
    connect: 'Connects to USB-A / USB-C ports on your Motherboard or via a 2.4GHz wireless dongle.'
  },
  {
    id: 'router', name: 'Wi-Fi Router', cat: 'Networking Device',
    analogy: 'Analogy: The Internet Traffic Controller',
    desc: 'Connects your home/school LAN to your ISP and routes data packets wirelessly (Wi-Fi) and over Ethernet.',
    miniParts: [
      { id: 'antennas', name: 'High-Gain Wi-Fi Antennas', desc: 'Broadcast and receive 2.4GHz / 5GHz / 6GHz radio waves.' },
      { id: 'rcpu', name: 'Router SoC & Memory Board', desc: 'Mini computer inside that runs DHCP, firewall, and packet routing.' },
      { id: 'lanports', name: '4x Gigabit LAN Ports', desc: 'Yellow/blue RJ45 ports for wired PCs and switches.' },
      { id: 'wanport', name: 'WAN Internet Port', desc: 'Connects directly to your ISP modem or fiber ONT.' },
      { id: 'rleds', name: 'Status LED Indicator Bar', desc: 'Shows power, internet, and Wi-Fi activity at a glance.' }
    ],
    products: ['TP-Link Archer AX55', 'ASUS RT-AX86U Pro', 'Netgear Nighthawk RAX50', 'Linksys Hydra Pro 6'],
    connect: 'Plugs into your ISP fiber/modem via the WAN port and connects PCs via Wi-Fi or RJ45.'
  },
  {
    id: 'pccase', name: 'PC Case (Chassis)', cat: 'Enclosure & Airflow',
    analogy: 'Analogy: The Protective Armor',
    desc: 'Holds and protects every internal component, channels cool airflow, and provides front power and USB buttons.',
    miniParts: [
      { id: 'glass', name: 'Tempered Glass Side Panel', desc: 'Clear shatter-resistant window showing your internal components.' },
      { id: 'mesh', name: 'Front Mesh Airflow Panel', desc: 'Perforated front grille that lets intake fans pull cool air inside.' },
      { id: 'standoffs', name: 'Motherboard Standoffs', desc: 'Brass spacers that keep the motherboard from touching metal.' },
      { id: 'shroud', name: 'PSU Shroud Chamber', desc: 'Bottom cover that hides power cables and keeps airflow clean.' },
      { id: 'frontio', name: 'Front I/O (Power & USB)', desc: 'Top/front panel with the Power button, USB ports, and audio jack.' }
    ],
    products: ['NZXT H5 Flow RGB', 'Lian Li O11D EVO', 'Corsair 7000D Airflow', 'Fractal Design Pop Air'],
    connect: 'Houses the Motherboard, PSU, GPU, Drives, and Fans; Front I/O cables plug into the Motherboard.'
  }
];

const GUIDES = {
  basics: {
    title: 'How a Computer Actually Works: From Click to Screen',
    slug: '/guides/how-computers-process-information',
    meta: 'Learn how a computer turns a mouse click into action on your screen using the Input-Process-Memory-Output cycle.',
    objectives: [
      'Explain the 4-step Information Processing Cycle (Input → Memory/Storage → Processing → Output).',
      'Describe how the CPU, RAM, SSD, and GPU work together as a team.',
      'Trace what happens inside your PC in the split second after you click an app.'
    ],
    steps: [
      '<strong>Step 1 — Input:</strong> You click a mouse or press a key. That action becomes binary signals (1s and 0s) sent to the motherboard.',
      '<strong>Step 2 — Storage &amp; Memory:</strong> Your SSD (filing cabinet) copies the needed app files into RAM (your fast study desk).',
      '<strong>Step 3 — Processing:</strong> The CPU reads those instructions from RAM and performs billions of calculations per second.',
      '<strong>Step 4 — Output:</strong> The GPU turns visual results into pixels and sends them to your monitor.'
    ],
    terms: [
      '<strong>Binary:</strong> Computer language made of 0s (off) and 1s (on).',
      '<strong>RAM:</strong> Fast, temporary workspace that clears when power turns off.',
      '<strong>SSD:</strong> Permanent flash storage that keeps files safe without power.'
    ],
    example: '<strong>Everyday Example:</strong> Double-clicking <em>Science_Notes.docx</em> sends an input signal → loads the file from SSD into RAM → CPU opens the editor → GPU draws the page on your screen.',
    quiz: [
      { q: 'Which part acts like your fast, temporary study desk?', opts: ['SSD', 'RAM', 'PSU', 'Monitor'], ans: 1, exp: 'RAM holds active apps for instant access and clears when turned off.' },
      { q: 'Which component turns 3D data into pixels for your monitor?', opts: ['GPU', 'SSD', 'Keyboard', 'Cooling Fan'], ans: 0, exp: 'The GPU specializes in rendering images, video, and 3D graphics.' }
    ]
  },
  software: {
    title: 'Software & Operating Systems Explained for Beginners',
    slug: '/guides/software-and-operating-systems',
    meta: 'Understand the difference between an Operating System (Windows, macOS, Linux) and everyday applications.',
    objectives: ['Tell the difference between system software and application software.', 'Understand what an Operating System (OS) manages behind the scenes.'],
    steps: [
      '<strong>Operating System (OS):</strong> Software like Windows 11, macOS, or Linux that manages your CPU, RAM, and files.',
      '<strong>Applications (Apps):</strong> Tools you use directly—like web browsers, code editors, and games—that ask the OS for hardware access.'
    ],
    terms: ['<strong>OS:</strong> The manager between you and the hardware.', '<strong>Driver:</strong> Small helper software that lets the OS talk to a GPU or printer.'],
    example: '<strong>Everyday Example:</strong> When you print homework, your browser asks Windows/macOS, which uses a printer driver to send pages to the printer.',
    quiz: [
      { q: 'Which of these is an Operating System?', opts: ['Google Chrome', 'Linux', 'Corsair RAM', 'HDMI'], ans: 1, exp: 'Linux (alongside Windows and macOS) is an Operating System.' }
    ]
  },
  troubleshooting: {
    title: 'Beginner Troubleshooting: Why PCs Slow Down & How to Fix It',
    slug: '/guides/beginner-pc-troubleshooting',
    meta: 'Learn simple steps to diagnose a slow or overheating computer safely.',
    objectives: ['Spot signs of full RAM, full storage, or overheating.', 'Use safe first-step checks before panicking.'],
    steps: [
      '<strong>Check Open Apps (RAM):</strong> Too many browser tabs fill up RAM. Close unused tabs or restart.',
      '<strong>Check Airflow (Heat):</strong> Dust-clogged fans cause thermal throttling—keep vents clear.',
      '<strong>Restart First:</strong> A reboot clears stuck temporary processes in RAM.'
    ],
    terms: ['<strong>Thermal Throttling:</strong> When a hot CPU/GPU slows down to protect itself from heat damage.'],
    example: '<strong>Everyday Example:</strong> If a laptop fan sounds like a jet engine on a bed, moving it to a hard desk restores airflow and stops lag.',
    quiz: [
      { q: 'Why does a computer slow down when it gets too hot?', opts: ['Thermal throttling protects the chip', 'The SSD deletes files', 'RAM doubles in size', 'Wi-Fi turns off'], ans: 0, exp: 'CPUs and GPUs automatically reduce speed to lower temperatures safely.' }
    ]
  },
  technology: {
    title: 'How the Internet & Wi-Fi Reach Your Computer',
    slug: '/guides/how-internet-and-wifi-work',
    meta: 'A simple beginner guide to routers, Wi-Fi signals, IP addresses, and loading a website.',
    objectives: ['Understand what a router and IP address do.', 'Trace how a webpage travels from a server to your screen.'],
    steps: [
      '<strong>Your Request:</strong> Typing a web address sends a request over Wi-Fi to your home router.',
      '<strong>DNS Lookup:</strong> DNS translates a human name (like Techbuilder) into a numeric IP address.',
      '<strong>Data Packets:</strong> The website arrives in small packets and reassembles in your browser.'
    ],
    terms: ['<strong>Router:</strong> Directs internet traffic between your devices and your internet provider.', '<strong>DNS:</strong> The internet phonebook that turns names into IP addresses.'],
    example: '<strong>Everyday Example:</strong> Opening a video streams thousands of tiny data packets over Wi-Fi into your RAM in real time.',
    quiz: [
      { q: 'What acts like the internet’s phonebook, turning website names into IP addresses?', opts: ['PSU', 'DNS', 'BIOS', 'SSD'], ans: 1, exp: 'DNS (Domain Name System) translates domain names into IP addresses.' }
    ]
  }
};

let activePartId = 'cpu';
let viewMode = 'mini'; // 'mini' or 'full'
let exploded = false;
let autoSpin = true;
let heroParts = {};
let miniGroups = []; // { id, name, desc, group, home, exp }
let heroFans = [];
let heroOrbit = null;
let sceneRef = null, fullGroupRef = null, miniGroupRef = null, resizeHero3D = null;

function selectMiniPart(miniId) {
  const part = PARTS.find(p => p.id === activePartId);
  if (!part || !part.miniParts) return;
  const mp = part.miniParts.find(m => m.id === miniId) || part.miniParts[0];
  document.getElementById('miniPartDetail').innerHTML = `<strong>${mp.name}:</strong> ${mp.desc}`;
  document.getElementById('hudLabel').textContent = `${part.name} → ${mp.name}`;
  document.querySelectorAll('#miniPartsList .pill').forEach(el => {
    el.style.background = el.dataset.mid === mp.id ? '#1769e0' : '#f0f6ff';
    el.style.color = el.dataset.mid === mp.id ? '#fff' : '#1769e0';
  });
}

function selectPart(id) {
  const part = PARTS.find(p => p.id === id);
  if (!part) return;
  activePartId = id;
  document.getElementById('partCat').textContent = part.cat;
  document.getElementById('partTitle').textContent = part.name;
  document.getElementById('partAnalogy').textContent = part.analogy;
  document.getElementById('partDesc').textContent = part.desc;
  document.getElementById('partConnect').textContent = part.connect;
  document.getElementById('hudLabel').textContent = `Inspecting: ${part.name}`;
  document.getElementById('partProducts').innerHTML = part.products
    .map(p => `<span class="pill">${p}</span>`).join('');

  const mList = document.getElementById('miniPartsList');
  mList.innerHTML = (part.miniParts || []).map(m =>
    `<button type="button" class="pill" data-mid="${m.id}" style="cursor:pointer">${m.name}</button>`
  ).join('');
  mList.querySelectorAll('.pill').forEach(btn => {
    btn.addEventListener('click', () => selectMiniPart(btn.dataset.mid));
  });
  if (part.miniParts && part.miniParts.length) selectMiniPart(part.miniParts[0].id);

  document.querySelectorAll('#partTabs .part-tab').forEach(btn => {
    btn.classList.toggle('active', btn.dataset.id === id);
  });
  if (miniGroupRef) buildMiniPart3D(id);
}

function buildMiniPart3D(partId) {
  while (miniGroupRef.children.length) miniGroupRef.remove(miniGroupRef.children[0]);
  miniGroups = [];
  const matDark = new THREE.MeshStandardMaterial({ color: 0x111827, roughness: 0.42, metalness: 0.35 });
  const matPCBBlack = new THREE.MeshStandardMaterial({ color: 0x0b0f17, roughness: 0.55, metalness: 0.2 });
  const matCase = new THREE.MeshStandardMaterial({ color: 0x273244, metalness: 0.65, roughness: 0.32 });
  const matBlue = new THREE.MeshStandardMaterial({ color: 0x1769e0, emissive: 0x1769e0, emissiveIntensity: 0.25, roughness: 0.3 });
  const matCyan = new THREE.MeshStandardMaterial({ color: 0x38bdf8, emissive: 0x0284c7, emissiveIntensity: 0.2, roughness: 0.3 });
  const matSilver = new THREE.MeshStandardMaterial({ color: 0xd1d5db, metalness: 0.9, roughness: 0.18 });
  const matNickel = new THREE.MeshStandardMaterial({ color: 0xe2e8f0, metalness: 0.92, roughness: 0.15 });
  const matGold = new THREE.MeshStandardMaterial({ color: 0xf59e0b, metalness: 0.95, roughness: 0.18 });
  const matCopper = new THREE.MeshStandardMaterial({ color: 0xd97706, metalness: 0.9, roughness: 0.22 });
  const matPCB = new THREE.MeshStandardMaterial({ color: 0x047857, roughness: 0.52, metalness: 0.15 });

  function reg(id, grp, home, exp) {
    grp.position.set(...home);
    grp.traverse(c => { if (c.isMesh) { c.userData.miniId = id; } });
    miniGroupRef.add(grp);
    miniGroups.push({ id, group: grp, home: new THREE.Vector3(...home), exp: new THREE.Vector3(...exp) });
  }

  if (partId === 'cpu') {
    // Stepped nickel-plated IHS (like real LGA1700/AM5)
    const ihs = new THREE.Group();
    const ihsBase = new THREE.Mesh(new THREE.BoxGeometry(1.52, 0.06, 1.62), matNickel);
    const ihsTop = new THREE.Mesh(new THREE.BoxGeometry(1.24, 0.1, 1.32), matNickel);
    ihsTop.position.y = 0.07;
    ihs.add(ihsBase, ihsTop);
    reg('ihs', ihs, [0, 0.22, 0], [0, 1.0, 0]);

    // Silicon Die + Multi-Core Chiplets
    const die = new THREE.Group();
    const dieSub = new THREE.Mesh(new THREE.BoxGeometry(0.85, 0.04, 0.95), matDark);
    die.add(dieSub);
    const ioDie = new THREE.Mesh(new THREE.BoxGeometry(0.45, 0.06, 0.26), matSilver);
    ioDie.position.set(0, 0.03, -0.25);
    die.add(ioDie);
    for (let x = -0.24; x <= 0.24; x += 0.16) {
      for (let z = 0.05; z <= 0.32; z += 0.13) {
        const core = new THREE.Mesh(new THREE.BoxGeometry(0.13, 0.06, 0.1), matBlue);
        core.position.set(x, 0.03, z);
        die.add(core);
      }
    }
    reg('die', die, [0, 0.11, 0], [0, 0.48, 0]);

    // Multi-layer Substrate PCB with gold alignment triangle
    const sub = new THREE.Group();
    sub.add(new THREE.Mesh(new THREE.BoxGeometry(1.75, 0.08, 1.85), matPCB));
    const tri = new THREE.Mesh(new THREE.CylinderGeometry(0.06, 0.06, 0.09, 3), matGold);
    tri.position.set(-0.74, 0.01, 0.78);
    sub.add(tri);
    reg('substrate', sub, [0, 0, 0], [0, -0.05, 0]);

    // Dense Gold Contact Pads
    const pins = new THREE.Group();
    for (let x = -0.72; x <= 0.72; x += 0.12) {
      for (let z = -0.78; z <= 0.78; z += 0.12) {
        if (Math.abs(x) < 0.2 && Math.abs(z) < 0.2) continue;
        const p = new THREE.Mesh(new THREE.BoxGeometry(0.07, 0.03, 0.07), matGold);
        p.position.set(x, 0, z);
        pins.add(p);
      }
    }
    reg('pins', pins, [0, -0.06, 0], [0, -0.68, 0]);

    // Center SMD Capacitors
    const smd = new THREE.Group();
    for (let x = -0.15; x <= 0.15; x += 0.08) {
      for (let z = -0.15; z <= 0.15; z += 0.08) {
        const cap = new THREE.Mesh(new THREE.BoxGeometry(0.04, 0.05, 0.03), matCopper);
        cap.position.set(x, 0, z);
        smd.add(cap);
      }
    }
    reg('smd', smd, [0, -0.07, 0], [0, -1.05, 0]);
  } else if (partId === 'gpu') {
    // Realistic Dual-Fan Shroud with Spinning 7-Blade Fans
    const fans = new THREE.Group();
    const shroud = new THREE.Mesh(new THREE.BoxGeometry(2.55, 0.12, 1.1), matDark);
    fans.add(shroud);
    for (const fx of [-0.65, 0.65]) {
      const ring = new THREE.Mesh(new THREE.TorusGeometry(0.42, 0.035, 10, 32), matSilver);
      ring.rotation.x = Math.PI / 2; ring.position.set(fx, -0.06, 0);
      const hub = new THREE.Group();
      hub.position.set(fx, -0.06, 0);
      hub.add(new THREE.Mesh(new THREE.CylinderGeometry(0.12, 0.12, 0.06, 16), matCase));
      for (let b = 0; b < 7; b++) {
        const ang = (b * Math.PI * 2) / 7;
        const blade = new THREE.Mesh(new THREE.BoxGeometry(0.32, 0.02, 0.09), matSilver);
        blade.rotation.y = ang;
        blade.position.set(Math.cos(ang) * 0.22, 0, Math.sin(ang) * 0.22);
        hub.add(blade);
      }
      fans.add(ring, hub);
    }
    reg('fans', fans, [0, -0.22, 0], [0, -0.95, 0]);

    // Stacked Aluminum Heatsink Fins + 4 Copper Heatpipes
    const hs = new THREE.Group();
    for (let i = -1.1; i <= 1.1; i += 0.08) {
      const fin = new THREE.Mesh(new THREE.BoxGeometry(0.02, 0.22, 0.96), matSilver);
      fin.position.x = i; hs.add(fin);
    }
    for (const hz of [-0.28, -0.1, 0.1, 0.28]) {
      const pipe = new THREE.Mesh(new THREE.CylinderGeometry(0.03, 0.03, 2.35, 10), matCopper);
      pipe.rotation.z = Math.PI / 2; pipe.position.z = hz; hs.add(pipe);
    }
    reg('heatsink', hs, [0, -0.01, 0], [0, -0.35, 0]);

    // GPU PCB + Die + 8 GDDR6 VRAM Chips + VRM Inductors
    const gd = new THREE.Group();
    gd.add(new THREE.Mesh(new THREE.BoxGeometry(2.35, 0.05, 1.0), matPCBBlack));
    const die = new THREE.Mesh(new THREE.BoxGeometry(0.46, 0.06, 0.46), matSilver);
    die.position.set(-0.2, 0.04, 0); gd.add(die);
    const vramOffsets = [[-0.55,-0.2],[-0.55,0.2],[0.15,-0.2],[0.15,0.2],[-0.35,-0.38],[-0.05,-0.38],[-0.35,0.38],[-0.05,0.38]];
    vramOffsets.forEach(([vx, vz]) => {
      const vram = new THREE.Mesh(new THREE.BoxGeometry(0.14, 0.05, 0.12), matDark);
      vram.position.set(vx, 0.04, vz); gd.add(vram);
    });
    for (let vz = -0.35; vz <= 0.35; vz += 0.14) {
      const choke = new THREE.Mesh(new THREE.BoxGeometry(0.12, 0.07, 0.1), matCase);
      choke.position.set(0.55, 0.05, vz); gd.add(choke);
    }
    reg('gpudie', gd, [0, 0.16, 0], [0, 0.35, 0]);

    // PCIe x16 Gold Connector with notch
    const pcie = new THREE.Group();
    const p1 = new THREE.Mesh(new THREE.BoxGeometry(0.22, 0.11, 0.04), matGold); p1.position.x = -0.55;
    const p2 = new THREE.Mesh(new THREE.BoxGeometry(0.95, 0.11, 0.04), matGold); p2.position.x = 0.12;
    pcie.add(p1, p2);
    reg('pcie', pcie, [-0.3, 0.18, -0.53], [-0.3, 0.25, -1.0]);

    // Rear Slotted I/O Bracket with HDMI/DP Ports
    const io = new THREE.Group();
    io.add(new THREE.Mesh(new THREE.BoxGeometry(0.06, 0.44, 1.06), matSilver));
    for (let pz = -0.32; pz <= 0.32; pz += 0.21) {
      const port = new THREE.Mesh(new THREE.BoxGeometry(0.08, 0.07, 0.13), matDark);
      port.position.set(-0.02, 0.05, pz); io.add(port);
    }
    reg('io', io, [-1.22, 0.04, 0], [-1.7, 0.04, 0]);
  } else if (partId === 'motherboard') {
    const base = new THREE.Mesh(new THREE.BoxGeometry(2.05, 2.4, 0.06), matPCBBlack);
    miniGroupRef.add(base);

    // LGA Socket + Retention Frame
    const sock = new THREE.Group();
    sock.add(new THREE.Mesh(new THREE.BoxGeometry(0.58, 0.62, 0.08), matSilver));
    const inner = new THREE.Mesh(new THREE.BoxGeometry(0.42, 0.46, 0.09), matDark);
    sock.add(inner);
    reg('socket', sock, [-0.15, 0.42, 0.05], [-0.15, 0.42, 0.65]);

    // Fin-cut VRM Heatsinks (Top + Left)
    const vrm = new THREE.Group();
    const vTop = new THREE.Mesh(new THREE.BoxGeometry(0.75, 0.22, 0.22), matCase); vTop.position.set(0, 0.45, 0);
    const vLeft = new THREE.Mesh(new THREE.BoxGeometry(0.24, 0.72, 0.24), matCase); vLeft.position.set(-0.48, 0, 0);
    vrm.add(vTop, vLeft);
    reg('vrm', vrm, [-0.15, 0.45, 0.11], [-0.15, 0.65, 0.65]);

    // 4 Color-Coded DIMM Slots with Latches
    const dimm = new THREE.Group();
    for (let i = 0; i < 4; i++) {
      const sl = new THREE.Mesh(new THREE.BoxGeometry(0.05, 0.88, 0.1), i % 2 === 0 ? matDark : matCase);
      sl.position.x = i * 0.11; dimm.add(sl);
    }
    reg('dimm', dimm, [0.42, 0.42, 0.06], [0.85, 0.42, 0.55]);

    // Reinforced Steel PCIe x16 Slot
    const ps = new THREE.Group();
    ps.add(new THREE.Mesh(new THREE.BoxGeometry(1.22, 0.09, 0.11), matSilver));
    reg('pcieslot', ps, [-0.12, -0.32, 0.06], [-0.12, -0.32, 0.65]);

    // CR2032 CMOS Battery
    const cmos = new THREE.Group();
    const bat = new THREE.Mesh(new THREE.CylinderGeometry(0.16, 0.16, 0.05, 24), matNickel);
    bat.rotation.x = Math.PI / 2; cmos.add(bat);
    reg('cmos', cmos, [0.48, -0.68, 0.05], [0.75, -0.85, 0.65]);
  } else if (partId === 'ram') {
    const sp = new THREE.Group();
    const s1 = new THREE.Mesh(new THREE.BoxGeometry(2.35, 0.58, 0.07), matCase); s1.position.z = 0.09;
    const s2 = new THREE.Mesh(new THREE.BoxGeometry(2.35, 0.58, 0.07), matCase); s2.position.z = -0.09;
    sp.add(s1, s2);
    reg('spreader', sp, [0, 0.02, 0], [0, 0.02, 0.55]);

    const rgb = new THREE.Group();
    rgb.add(new THREE.Mesh(new THREE.BoxGeometry(2.3, 0.12, 0.14), matBlue));
    reg('rgb', rgb, [0, 0.36, 0], [0, 0.85, 0]);

    const dram = new THREE.Group();
    dram.add(new THREE.Mesh(new THREE.BoxGeometry(2.28, 0.5, 0.04), matPCBBlack));
    for (let i = -0.9; i <= 0.9; i += 0.25) {
      const chip = new THREE.Mesh(new THREE.BoxGeometry(0.16, 0.24, 0.06), matDark);
      chip.position.set(i, 0, 0); dram.add(chip);
    }
    reg('dram', dram, [0, 0, 0], [0, 0, -0.35]);

    // 288-Pin Gold Edge with Off-Center Notch
    const gold = new THREE.Group();
    const gL = new THREE.Mesh(new THREE.BoxGeometry(1.18, 0.1, 0.04), matGold); gL.position.x = -0.52;
    const gR = new THREE.Mesh(new THREE.BoxGeometry(0.92, 0.1, 0.04), matGold); gR.position.x = 0.62;
    gold.add(gL, gR);
    reg('gold', gold, [0, -0.3, 0], [0, -0.78, 0]);
  } else if (partId === 'ssd') {
    // True 2280 M.2 NVMe proportions (22mm x 80mm)
    const pcb = new THREE.Mesh(new THREE.BoxGeometry(2.4, 0.05, 0.68), matPCBBlack);
    miniGroupRef.add(pcb);

    const ctrl = new THREE.Group();
    ctrl.add(new THREE.Mesh(new THREE.BoxGeometry(0.36, 0.06, 0.36), matNickel));
    reg('ctrl', ctrl, [-0.62, 0.05, 0], [-0.62, 0.55, 0]);

    const nand = new THREE.Group();
    for (const nx of [0.12, 0.72]) {
      const c = new THREE.Mesh(new THREE.BoxGeometry(0.46, 0.06, 0.48), matDark);
      c.position.x = nx; nand.add(c);
    }
    reg('nand', nand, [0, 0.05, 0], [0.2, 0.65, 0]);

    const cache = new THREE.Group();
    cache.add(new THREE.Mesh(new THREE.BoxGeometry(0.24, 0.05, 0.24), matCase));
    reg('cache', cache, [-0.25, 0.05, 0.14], [-0.25, 0.45, 0.5]);

    const mkey = new THREE.Group();
    const mk1 = new THREE.Mesh(new THREE.BoxGeometry(0.16, 0.05, 0.42), matGold); mk1.position.z = -0.08;
    const mk2 = new THREE.Mesh(new THREE.BoxGeometry(0.16, 0.05, 0.12), matGold); mk2.position.z = 0.24;
    mkey.add(mk1, mk2);
    reg('mkey', mkey, [-1.22, 0, 0], [-1.62, 0, 0]);
  } else if (partId === 'psu') {
    const body = new THREE.Mesh(new THREE.BoxGeometry(1.75, 0.95, 1.55), matDark);
    miniGroupRef.add(body);

    const pf = new THREE.Group();
    pf.add(new THREE.Mesh(new THREE.TorusGeometry(0.5, 0.035, 10, 32), matSilver));
    pf.rotation.x = Math.PI / 2;
    for (let b = 0; b < 7; b++) {
      const ang = (b * Math.PI * 2) / 7;
      const bl = new THREE.Mesh(new THREE.BoxGeometry(0.4, 0.1, 0.02), matCase);
      bl.rotation.z = ang; bl.position.set(Math.cos(ang)*0.22, Math.sin(ang)*0.22, 0);
      pf.add(bl);
    }
    reg('psufan', pf, [0, 0.5, 0], [0, 1.1, 0]);

    const tr = new THREE.Group();
    tr.add(new THREE.Mesh(new THREE.BoxGeometry(0.5, 0.46, 0.5), matCopper));
    reg('trans', tr, [0.28, 0.05, 0], [0.65, 0.35, 0]);

    const caps = new THREE.Group();
    for (const cx of [-0.45, -0.2]) {
      const cap = new THREE.Mesh(new THREE.CylinderGeometry(0.11, 0.11, 0.52, 16), matCase);
      cap.position.x = cx; caps.add(cap);
    }
    reg('caps', caps, [-0.2, 0.05, 0.22], [-0.65, 0.35, 0.5]);

    const mod = new THREE.Group();
    for (let mx = -0.5; mx <= 0.5; mx += 0.25) {
      const sock = new THREE.Mesh(new THREE.BoxGeometry(0.18, 0.16, 0.08), matBlue);
      sock.position.x = mx; mod.add(sock);
    }
    reg('modular', mod, [0, -0.18, 0.78], [0, -0.18, 1.3]);
  } else if (partId === 'cooling') {
    const bl = new THREE.Group();
    bl.add(new THREE.Mesh(new THREE.BoxGeometry(1.4, 1.4, 0.26), matDark));
    const ring = new THREE.Mesh(new THREE.TorusGeometry(0.58, 0.04, 10, 32), matBlue);
    ring.position.z = 0.14; bl.add(ring);
    for (let b = 0; b < 7; b++) {
      const ang = (b * Math.PI * 2) / 7;
      const blade = new THREE.Mesh(new THREE.BoxGeometry(0.46, 0.12, 0.03), matSilver);
      blade.rotation.z = ang; blade.position.set(Math.cos(ang)*0.28, Math.sin(ang)*0.28, 0.04);
      bl.add(blade);
    }
    reg('blades', bl, [0, 0.25, 0.52], [0, 0.25, 1.25]);

    const fins = new THREE.Group();
    for (let y = -0.5; y <= 0.5; y += 0.07) {
      const fin = new THREE.Mesh(new THREE.BoxGeometry(1.32, 0.02, 0.78), matSilver);
      fin.position.y = y; fins.add(fin);
    }
    reg('fins', fins, [0, 0.25, -0.1], [0, 0.4, -0.55]);

    const pipes = new THREE.Group();
    for (const px of [-0.42, -0.14, 0.14, 0.42]) {
      const p = new THREE.Mesh(new THREE.CylinderGeometry(0.04, 0.04, 1.45, 12), matCopper);
      p.position.x = px; pipes.add(p);
    }
    reg('pipes', pipes, [0, 0.1, -0.1], [0, -0.05, -0.9]);

    const cp = new THREE.Group();
    cp.add(new THREE.Mesh(new THREE.BoxGeometry(0.92, 0.1, 0.92), matCopper));
    reg('coldplate', cp, [0, -0.62, -0.1], [0, -1.08, -0.1]);
  } else if (partId === 'monitor') {
    const panel = new THREE.Group();
    panel.add(new THREE.Mesh(new THREE.BoxGeometry(2.35, 1.38, 0.04), matDark));
    const screen = new THREE.Mesh(new THREE.BoxGeometry(2.24, 1.26, 0.02), matBlue);
    screen.position.z = 0.025; panel.add(screen);
    reg('panel', panel, [0, 0.35, 0.12], [0, 0.35, 0.85]);

    const bl = new THREE.Group();
    bl.add(new THREE.Mesh(new THREE.BoxGeometry(2.2, 1.22, 0.03), matCyan));
    reg('backlight', bl, [0, 0.35, 0.04], [0, 0.35, 0.3]);

    const tcon = new THREE.Group();
    tcon.add(new THREE.Mesh(new THREE.BoxGeometry(0.95, 0.46, 0.05), matPCB));
    reg('tcon', tcon, [0, 0.35, -0.04], [0, 0.35, -0.45]);

    const stand = new THREE.Group();
    const neck = new THREE.Mesh(new THREE.BoxGeometry(0.16, 0.88, 0.12), matSilver);
    neck.position.y = -0.36;
    const base = new THREE.Mesh(new THREE.BoxGeometry(1.05, 0.05, 0.56), matCase);
    base.position.set(0, -0.8, 0.12);
    stand.add(neck, base);
    reg('stand', stand, [0, -0.05, -0.12], [0, -0.5, -0.45]);

    const mp = new THREE.Group();
    mp.add(new THREE.Mesh(new THREE.BoxGeometry(0.68, 0.12, 0.08), matGold));
    reg('mports', mp, [0.3, -0.1, -0.12], [0.5, -0.1, -0.75]);
  } else if (partId === 'peripherals') {
    const keycaps = new THREE.Group();
    for (let r = -0.24; r <= 0.24; r += 0.16) {
      for (let c = -0.78; c <= 0.34; c += 0.16) {
        const k = new THREE.Mesh(new THREE.BoxGeometry(0.12, 0.07, 0.12), matNickel);
        k.position.set(c, 0, r); keycaps.add(k);
      }
    }
    const space = new THREE.Mesh(new THREE.BoxGeometry(0.65, 0.07, 0.12), matBlue);
    space.position.set(-0.22, 0, 0.38); keycaps.add(space);
    reg('keycaps', keycaps, [-0.2, 0.15, 0], [-0.2, 0.85, 0]);

    const switches = new THREE.Group();
    for (let r = -0.24; r <= 0.24; r += 0.16) {
      for (let c = -0.78; c <= 0.34; c += 0.16) {
        const sw = new THREE.Mesh(new THREE.BoxGeometry(0.08, 0.06, 0.08), matBlue);
        sw.position.set(c, 0, r); switches.add(sw);
      }
    }
    reg('switches', switches, [-0.2, 0.07, 0], [-0.2, 0.4, 0]);

    const kpcb = new THREE.Group();
    kpcb.add(new THREE.Mesh(new THREE.BoxGeometry(1.5, 0.07, 0.86), matDark));
    reg('kpcb', kpcb, [-0.2, -0.02, 0.05], [-0.2, -0.15, 0.05]);

    // Sculpted Ergonomic Mouse Body + Sensor
    const sensor = new THREE.Group();
    const mBase = new THREE.Mesh(new THREE.BoxGeometry(0.38, 0.12, 0.62), matCase);
    const mDome = new THREE.Mesh(new THREE.SphereGeometry(0.2, 16, 12), matDark);
    mDome.scale.set(0.95, 0.45, 1.5); mDome.position.y = 0.06;
    const lens = new THREE.Mesh(new THREE.CylinderGeometry(0.05, 0.05, 0.03, 16), matCyan);
    lens.position.y = -0.07;
    sensor.add(mBase, mDome, lens);
    reg('sensor', sensor, [0.95, 0.02, 0], [1.25, -0.25, 0]);

    const scroll = new THREE.Group();
    const wh = new THREE.Mesh(new THREE.CylinderGeometry(0.06, 0.06, 0.05, 16), matBlue);
    wh.rotation.z = Math.PI / 2;
    scroll.add(wh);
    reg('scroll', scroll, [0.95, 0.14, -0.14], [1.25, 0.55, -0.14]);
  } else if (partId === 'router') {
    const ants = new THREE.Group();
    for (const ax of [-0.75, -0.25, 0.25, 0.75]) {
      const a = new THREE.Mesh(new THREE.CylinderGeometry(0.03, 0.048, 1.05, 12), matDark);
      a.position.set(ax, 0.56, -0.36); ants.add(a);
    }
    reg('antennas', ants, [0, 0, 0], [0, 0.55, -0.45]);

    const rcpu = new THREE.Group();
    rcpu.add(new THREE.Mesh(new THREE.BoxGeometry(1.55, 0.06, 0.78), matPCB));
    const chip = new THREE.Mesh(new THREE.BoxGeometry(0.36, 0.06, 0.36), matSilver);
    chip.position.y = 0.05; rcpu.add(chip);
    reg('rcpu', rcpu, [0, 0.04, 0], [0, 0.45, 0]);

    const body = new THREE.Mesh(new THREE.BoxGeometry(1.8, 0.22, 0.92), matCase);
    miniGroupRef.add(body);

    const lan = new THREE.Group();
    for (let i = 0; i < 4; i++) {
      const p = new THREE.Mesh(new THREE.BoxGeometry(0.14, 0.12, 0.08), matGold);
      p.position.x = -0.35 + i * 0.22; lan.add(p);
    }
    reg('lanports', lan, [-0.1, 0, -0.47], [-0.1, 0, -0.95]);

    const wan = new THREE.Group();
    wan.add(new THREE.Mesh(new THREE.BoxGeometry(0.18, 0.13, 0.08), matBlue));
    reg('wanport', wan, [0.6, 0, -0.47], [0.85, 0, -0.95]);

    const leds = new THREE.Group();
    leds.add(new THREE.Mesh(new THREE.BoxGeometry(1.35, 0.035, 0.035), matCyan));
    reg('rleds', leds, [0, 0.12, 0.4], [0, 0.35, 0.75]);
  } else if (partId === 'pccase') {
    const glass = new THREE.Group();
    glass.add(new THREE.Mesh(new THREE.BoxGeometry(1.82, 2.2, 0.04), new THREE.MeshPhysicalMaterial({ color: 0x38bdf8, transparent: true, opacity: 0.32, roughness: 0.1 })));
    reg('glass', glass, [0, 0, 0.65], [0, 0, 1.35]);

    const mesh = new THREE.Group();
    mesh.add(new THREE.Mesh(new THREE.BoxGeometry(0.08, 2.2, 1.25), matDark));
    reg('mesh', mesh, [0.95, 0, 0], [1.55, 0, 0]);

    const standoffs = new THREE.Group();
    for (const sx of [-0.5, 0.4]) {
      for (const sy of [-0.4, 0.6]) {
        const st = new THREE.Mesh(new THREE.CylinderGeometry(0.04, 0.04, 0.12, 8), matGold);
        st.rotation.x = Math.PI / 2; st.position.set(sx, sy, 0); standoffs.add(st);
      }
    }
    reg('standoffs', standoffs, [-0.1, 0.1, -0.5], [-0.1, 0.1, -0.1]);

    const shroud = new THREE.Group();
    shroud.add(new THREE.Mesh(new THREE.BoxGeometry(1.8, 0.48, 1.2), matCase));
    reg('shroud', shroud, [0, -0.86, 0], [0, -1.25, 0.35]);

    const fio = new THREE.Group();
    fio.add(new THREE.Mesh(new THREE.BoxGeometry(0.62, 0.07, 0.24), matBlue));
    reg('frontio', fio, [0.55, 1.14, 0.35], [0.55, 1.55, 0.55]);

    const frame = new THREE.Mesh(new THREE.BoxGeometry(1.86, 2.26, 0.08), matCase);
    frame.position.z = -0.6;
    miniGroupRef.add(frame);
  }
}

function renderGuide(key) {
  const g = GUIDES[key] || GUIDES.basics;
  document.querySelectorAll('#guideTabs .part-tab').forEach(b => {
    b.classList.toggle('active', b.dataset.guide === key);
  });
  const el = document.getElementById('guideContent');
  el.innerHTML = `
    <div class="guide-meta">
      <strong>Suggested URL Slug:</strong> <code>${g.slug}</code> &nbsp;|&nbsp;
      <strong>Meta Description:</strong> ${g.meta}
    </div>
    <h3 style="font-size:24px;color:#17243a">${g.title}</h3>
    <div class="guide-section">
      <h4>Learning Objectives</h4>
      <ul>${g.objectives.map(o => `<li>${o}</li>`).join('')}</ul>
    </div>
    <div class="guide-section">
      <h4>Step-by-Step Explanation</h4>
      <ol>${g.steps.map(s => `<li>${s}</li>`).join('')}</ol>
    </div>
    <div class="guide-section">
      <h4>Important Terms</h4>
      <ul>${g.terms.map(t => `<li>${t}</li>`).join('')}</ul>
    </div>
    <div class="guide-section">
      <p style="font-size:14px;color:#344054">${g.example}</p>
    </div>
    <div class="quiz-box">
      <h4 style="font-size:16px;margin-bottom:10px">Quick Check Quiz</h4>
      ${g.quiz.map((q, qi) => `
        <div style="margin-bottom:14px">
          <p style="font-size:14px;font-weight:600">${qi + 1}. ${q.q}</p>
          ${q.opts.map((opt, oi) => `<button type="button" class="quiz-opt" data-qi="${qi}" data-oi="${oi}">${opt}</button>`).join('')}
          <p class="quiz-fb" id="qfb-${qi}" style="display:none;font-size:13px;margin-top:6px;color:#17243a"></p>
        </div>
      `).join('')}
    </div>
  `;

  el.querySelectorAll('.quiz-opt').forEach(btn => {
    btn.addEventListener('click', () => {
      const qi = Number(btn.dataset.qi);
      const oi = Number(btn.dataset.oi);
      const q = g.quiz[qi];
      const siblings = el.querySelectorAll(`.quiz-opt[data-qi="${qi}"]`);
      siblings.forEach((b, idx) => {
        b.disabled = true;
        if (idx === q.ans) b.classList.add('correct');
        else if (idx === oi) b.classList.add('wrong');
      });
      const fb = document.getElementById(`qfb-${qi}`);
      fb.style.display = 'block';
      fb.textContent = (oi === q.ans ? 'Correct! ' : 'Not quite. ') + q.exp;
    });
  });
}

function init3D() {
  const wrap = document.getElementById('pcCanvasWrap');
  const scene = new THREE.Scene();
  const camera = new THREE.PerspectiveCamera(42, wrap.clientWidth / wrap.clientHeight, 0.1, 100);
  const renderer = new THREE.WebGLRenderer({ antialias: true, alpha: true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
  renderer.setSize(wrap.clientWidth, wrap.clientHeight);
  renderer.toneMapping = THREE.ACESFilmicToneMapping;
  renderer.toneMappingExposure = 1.15;
  wrap.appendChild(renderer.domElement);

  scene.add(new THREE.HemisphereLight(0xf8fafc, 0x334155, 0.85));
  const keyLight = new THREE.DirectionalLight(0xffffff, 1.25);
  keyLight.position.set(5, 8, 6);
  scene.add(keyLight);
  const rimLight = new THREE.DirectionalLight(0x93c5fd, 0.75);
  rimLight.position.set(-6, 3, -5);
  scene.add(rimLight);
  const fillLight = new THREE.DirectionalLight(0xfef3c7, 0.45);
  fillLight.position.set(3, -5, 4);
  scene.add(fillLight);

  sceneRef = scene;
  const root = new THREE.Group();
  fullGroupRef = root;
  fullGroupRef.visible = (viewMode === 'full');
  scene.add(root);

  miniGroupRef = new THREE.Group();
  miniGroupRef.visible = (viewMode === 'mini');
  scene.add(miniGroupRef);

  const matCase = new THREE.MeshStandardMaterial({ color: 0x1e293b, metalness: 0.5, roughness: 0.4 });
  const matBlue = new THREE.MeshStandardMaterial({ color: 0x1769e0, emissive: 0x1769e0, emissiveIntensity: 0.35 });
  const matDark = new THREE.MeshStandardMaterial({ color: 0x0f172a, roughness: 0.5 });
  const matSilver = new THREE.MeshStandardMaterial({ color: 0xcbd5e1, metalness: 0.8, roughness: 0.25 });

  // Frame
  const back = new THREE.Mesh(new THREE.BoxGeometry(2.0, 2.7, 0.08), matCase); back.position.set(0, 0, -0.7);
  const topP = new THREE.Mesh(new THREE.BoxGeometry(2.0, 0.08, 1.4), matCase); topP.position.set(0, 1.31, 0);
  const botP = new THREE.Mesh(new THREE.BoxGeometry(2.0, 0.1, 1.4), matCase); botP.position.set(0, -1.31, 0);
  const sideL = new THREE.Mesh(new THREE.BoxGeometry(0.08, 2.7, 1.4), matCase); sideL.position.set(-0.96, 0, 0);
  root.add(back, topP, botP, sideL);

  function addPart(id, group, home, exp) {
    group.position.set(...home);
    group.traverse(c => { if (c.isMesh) c.userData.partId = id; });
    root.add(group);
    heroParts[id] = { group, home: new THREE.Vector3(...home), exp: new THREE.Vector3(...exp) };
  }

  const mobo = new THREE.Group();
  mobo.add(new THREE.Mesh(new THREE.BoxGeometry(1.45, 1.95, 0.06), matDark));
  addPart('motherboard', mobo, [0, 0.15, -0.56], [0, 0.15, -1.15]);

  const cpu = new THREE.Group();
  cpu.add(new THREE.Mesh(new THREE.BoxGeometry(0.36, 0.36, 0.06), matSilver));
  addPart('cpu', cpu, [-0.1, 0.52, -0.44], [-0.1, 0.65, 0.55]);

  const ram = new THREE.Group();
  for (let i = 0; i < 2; i++) {
    const s = new THREE.Mesh(new THREE.BoxGeometry(0.06, 0.62, 0.16), matBlue);
    s.position.x = i * 0.12;
    ram.add(s);
  }
  addPart('ram', ram, [0.32, 0.52, -0.4], [0.85, 0.65, 0.45]);

  const gpu = new THREE.Group();
  const gb = new THREE.Mesh(new THREE.BoxGeometry(1.2, 0.18, 0.48), matDark);
  const gs = new THREE.Mesh(new THREE.BoxGeometry(1.1, 0.04, 0.04), matBlue); gs.position.set(0, 0.06, 0.25);
  gpu.add(gb, gs);
  addPart('gpu', gpu, [-0.05, -0.15, -0.22], [-0.15, -0.15, 0.95]);

  const ssd = new THREE.Group();
  ssd.add(new THREE.Mesh(new THREE.BoxGeometry(0.4, 0.12, 0.04), matBlue));
  addPart('ssd', ssd, [0.05, -0.46, -0.46], [0.65, -0.5, 0.45]);

  const psu = new THREE.Group();
  psu.add(new THREE.Mesh(new THREE.BoxGeometry(0.9, 0.45, 0.75), matCase));
  addPart('psu', psu, [-0.42, -1.0, -0.1], [-1.25, -1.05, 0.2]);

  const cooling = new THREE.Group();
  for (let i = 0; i < 3; i++) {
    const f = new THREE.Group();
    f.position.y = 0.65 - i * 0.62;
    const ring = new THREE.Mesh(new THREE.TorusGeometry(0.21, 0.025, 8, 24), matBlue);
    ring.rotation.y = Math.PI / 2;
    const blades = new THREE.Mesh(new THREE.BoxGeometry(0.02, 0.34, 0.07), matSilver);
    heroFans.push(blades);
    f.add(ring, blades);
    cooling.add(f);
  }
  addPart('cooling', cooling, [0.85, 0.15, 0.1], [1.6, 0.15, 0.35]);

  let sph = { r: 5.0, theta: 0.5, phi: 1.3 };
  let dragging = false, px = 0, py = 0, down = { x: 0, y: 0 };
  function updateCam() {
    sph.phi = Math.max(0.25, Math.min(Math.PI - 0.25, sph.phi));
    sph.r = Math.max(2.6, Math.min(9, sph.r));
    camera.position.set(
      sph.r * Math.sin(sph.phi) * Math.sin(sph.theta),
      sph.r * Math.cos(sph.phi),
      sph.r * Math.sin(sph.phi) * Math.cos(sph.theta)
    );
    camera.lookAt(0, 0, 0);
  }
  updateCam();
  heroOrbit = { reset: () => { sph = { r: 5.0, theta: 0.5, phi: 1.3 }; updateCam(); } };

  const raycaster = new THREE.Raycaster();
  const pointer = new THREE.Vector2();
  renderer.domElement.addEventListener('pointerdown', e => {
    dragging = true; px = e.clientX; py = e.clientY; down = { x: px, y: py };
  });
  renderer.domElement.addEventListener('pointermove', e => {
    if (!dragging) return;
    sph.theta -= (e.clientX - px) * 0.008;
    sph.phi -= (e.clientY - py) * 0.008;
    px = e.clientX; py = e.clientY;
    updateCam();
  });
  renderer.domElement.addEventListener('pointerup', e => {
    dragging = false;
    if (Math.hypot(e.clientX - down.x, e.clientY - down.y) < 6) {
      const rect = renderer.domElement.getBoundingClientRect();
      pointer.x = ((e.clientX - rect.left) / rect.width) * 2 - 1;
      pointer.y = -((e.clientY - rect.top) / rect.height) * 2 + 1;
      raycaster.setFromCamera(pointer, camera);
      const targetGroup = viewMode === 'mini' ? miniGroupRef : root;
      const hits = raycaster.intersectObjects(targetGroup.children, true);
      for (const h of hits) {
        if (h.object.userData.miniId) { selectMiniPart(h.object.userData.miniId); break; }
        if (h.object.userData.partId) { selectPart(h.object.userData.partId); break; }
      }
    }
  });
  renderer.domElement.addEventListener('wheel', e => {
    e.preventDefault(); sph.r += e.deltaY * 0.004; updateCam();
  }, { passive: false });

  resizeHero3D = () => {
    const w = wrap.clientWidth || 500;
    const h = wrap.clientHeight || 380;
    camera.aspect = w / h;
    camera.updateProjectionMatrix();
    renderer.setSize(w, h);
  };
  window.addEventListener('resize', resizeHero3D);

  (function anim() {
    requestAnimationFrame(anim);
    heroFans.forEach(b => { b.rotation.x += 0.08; });
    Object.values(heroParts).forEach(p => p.group.position.lerp(exploded ? p.exp : p.home, 0.09));
    miniGroups.forEach(m => m.group.position.lerp(exploded ? m.exp : m.home, 0.09));
    if (autoSpin && !dragging) { sph.theta += 0.0035; updateCam(); }
    renderer.render(scene, camera);
  })();
}

function showSection(secId) {
  document.querySelectorAll('.page-section').forEach(sec => {
    sec.classList.toggle('active-section', sec.id === secId);
  });
  document.querySelectorAll('#mainNav .nav-tab').forEach(a => {
    a.classList.toggle('active-nav', a.dataset.target === secId);
  });
  window.scrollTo({ top: 0, behavior: 'smooth' });
  if (secId === 'sec-hardware' && resizeHero3D) {
    setTimeout(resizeHero3D, 30);
  }
}

function getSearchIndex() {
  const items = [];
  PARTS.forEach(p => {
    items.push({
      type: '3D Hardware',
      title: p.name,
      sub: p.products.slice(0, 2).join(', '),
      keywords: (p.name + ' ' + p.cat + ' ' + p.desc + ' ' + p.products.join(' ')).toLowerCase(),
      action: () => { showSection('sec-hardware'); selectPart(p.id); }
    });
  });
  Object.entries(COURSES).forEach(([k, c]) => {
    items.push({
      type: 'Course',
      title: c.title,
      sub: c.badge,
      keywords: (c.title + ' ' + c.desc + ' ' + c.badge).toLowerCase(),
      action: () => { showSection('sec-courses'); loadCourse(k); }
    });
  });
  SEBA10_MODULES.forEach((m, idx) => {
    items.push({
      type: 'SEBA Class 10',
      title: m.title,
      sub: m.summary.slice(0, 75) + '...',
      keywords: (m.title + ' ' + m.summary + ' pan lan man wan ip ipv4 ipv6 mac dhcp router hub switch ping ipconfig arp').toLowerCase(),
      action: () => { showSection('sec-courses'); loadCourse('seba10'); loadExpertModule(idx); }
    });
  });
  Object.entries(GUIDES).forEach(([k, g]) => {
    items.push({
      type: 'Guide',
      title: g.title,
      sub: g.meta.slice(0, 75) + '...',
      keywords: (g.title + ' ' + g.meta).toLowerCase(),
      action: () => { showSection('sec-basics'); renderGuide(k); }
    });
  });
  items.push({
    type: 'Builder',
    title: 'Live Website Builder & Runner',
    sub: 'Create, edit, and run your own custom website',
    keywords: 'website builder make site create portfolio store blog landing',
    action: () => showSection('sec-builder')
  });
  return items;
}

function searchTopics() {
  const query = document.getElementById('searchInput').value.toLowerCase().trim();
  const box = document.getElementById('liveSearchResults');
  if (!query) {
    box.style.display = 'none';
    box.innerHTML = '';
    return;
  }
  const matches = getSearchIndex().filter(it => it.keywords.includes(query)).slice(0, 8);
  box.style.display = 'block';
  if (!matches.length) {
    box.innerHTML = '<div style="padding:14px;font-size:13px;color:#667085;text-align:center">No results found. Try "CPU", "RTX 4060", "SEBA", "PAN", "HTML", or "Builder".</div>';
    return;
  }
  box.innerHTML = '';
  matches.forEach(m => {
    const row = document.createElement('button');
    row.type = 'button';
    row.style.cssText = 'display:flex;justify-content:space-between;align-items:center;width:100%;padding:11px 14px;border:0;border-bottom:1px solid #eef2f7;background:#fff;text-align:left;cursor:pointer';
    row.innerHTML = `
      <div>
        <div style="font-size:14px;font-weight:700;color:#17243a">${m.title}</div>
        <div style="font-size:12px;color:#667085">${m.sub}</div>
      </div>
      <span style="background:#eef5ff;color:#1769e0;font-size:11px;font-weight:700;padding:3px 9px;border-radius:999px;white-space:nowrap;margin-left:10px">${m.type} →</span>
    `;
    row.addEventListener('click', () => {
      box.style.display = 'none';
      m.action();
    });
    box.appendChild(row);
  });
}

window.addEventListener('load', () => {
  const tabsWrap = document.getElementById('partTabs');
  PARTS.forEach(p => {
    const b = document.createElement('button');
    b.type = 'button';
    b.className = 'part-tab';
    b.dataset.id = p.id;
    b.textContent = p.name.split(' ')[0];
    b.addEventListener('click', () => selectPart(p.id));
    tabsWrap.appendChild(b);
  });

  document.querySelectorAll('#guideTabs .part-tab').forEach(b => {
    b.addEventListener('click', () => renderGuide(b.dataset.guide));
  });
  document.querySelectorAll('.topic-jump').forEach(a => {
    a.addEventListener('click', () => renderGuide(a.dataset.topic));
  });

  document.getElementById('viewModeBtn').addEventListener('click', (e) => {
    viewMode = viewMode === 'mini' ? 'full' : 'mini';
    fullGroupRef.visible = (viewMode === 'full');
    miniGroupRef.visible = (viewMode === 'mini');
    e.target.textContent = viewMode === 'mini' ? 'Mode: Mini-Parts 3D' : 'Mode: Full 3D PC';
    document.getElementById('explodeBtn').textContent = exploded
      ? (viewMode === 'mini' ? 'Assemble Mini-Parts' : 'Assemble 3D PC')
      : (viewMode === 'mini' ? 'Explode Mini-Parts' : 'Explode 3D PC');
  });

  document.getElementById('explodeBtn').addEventListener('click', (e) => {
    exploded = !exploded;
    e.target.classList.toggle('active', exploded);
    e.target.textContent = exploded
      ? (viewMode === 'mini' ? 'Assemble Mini-Parts' : 'Assemble 3D PC')
      : (viewMode === 'mini' ? 'Explode Mini-Parts' : 'Explode 3D PC');
  });
  document.getElementById('spinBtn').addEventListener('click', (e) => {
    autoSpin = !autoSpin;
    e.target.classList.toggle('active', autoSpin);
    e.target.textContent = `Auto-Spin: ${autoSpin ? 'ON' : 'OFF'}`;
  });
  document.getElementById('resetCamBtn').addEventListener('click', () => heroOrbit && heroOrbit.reset());

  document.getElementById('searchInput').addEventListener('input', searchTopics);
  document.getElementById('searchBtn').addEventListener('click', searchTopics);

  init3D();
  selectPart('cpu');
  renderGuide('basics');
  loadCourse('webdev');
});

const EXPERT_WEB_MODULES = [
  {
    title: '1. Planning & Setup',
    summary: 'Every professional website starts with a clean folder structure, wireframe, and modern editor (like VS Code).',
    steps: [
      '<strong>Create a Clean Folder:</strong> Organize files into <code>index.html</code> (entry page), <code>css/style.css</code>, <code>js/app.js</code>, and <code>assets/images/</code>.',
      '<strong>Mobile-First Wireframing:</strong> Sketch the header, hero, content grid, and footer for a 375px phone screen first, then expand for tablets (768px) and desktops (1200px+).',
      '<strong>Use Live Server:</strong> Preview changes instantly in your browser while editing.'
    ],
    proTip: 'Never use spaces or uppercase letters in file names (use <code>about-us.html</code>, not <code>About Us.html</code>) so URLs never break on Linux web servers.',
    mode: 'text',
    code: 'my-website/\n├── index.html\n├── css/\n│   └── style.css\n├── js/\n│   └── app.js\n└── assets/\n    └── logo.webp',
    output: 'Project structure ready! index.html is always the default homepage file a web server looks for.'
  },
  {
    title: '2. Semantic HTML5 & SEO',
    summary: 'Semantic tags tell both screen readers and Google search bots what each part of your page means.',
    steps: [
      '<strong>Use Landmarks:</strong> Wrap navigation in <code>&lt;nav&gt;</code>, primary content in <code>&lt;main&gt;</code>, self-contained cards in <code>&lt;article&gt;</code>, and bottom info in <code>&lt;footer&gt;</code>.',
      '<strong>One &lt;h1&gt; Per Page:</strong> Use a single <code>&lt;h1&gt;</code> for the main title, then <code>&lt;h2&gt;</code> and <code>&lt;h3&gt;</code> in order without skipping levels.',
      '<strong>Meta &amp; Accessibility:</strong> Always include <code>&lt;meta name="viewport"&gt;</code>, a 150-char <code>&lt;meta name="description"&gt;</code>, and descriptive <code>alt=""</code> text on every image.'
    ],
    proTip: 'Use <code>&lt;button type="button"&gt;</code> for actions and <code>&lt;a href="..."&gt;</code> for navigation—never use clickable <code>&lt;div&gt;</code> elements.',
    mode: 'html',
    code: '<header>\n  <nav aria-label="Main">\n    <strong style="color:#1769e0">ProSite</strong>\n  </nav>\n</header>\n<main>\n  <article>\n    <h1 style="font-size:20px;color:#17243a">Semantic HTML5</h1>\n    <p>Clean structure boosts SEO &amp; accessibility.</p>\n  </article>\n</main>'
  },
  {
    title: '3. Pro CSS3 & Responsive Layout',
    summary: 'Experts use CSS variables, Flexbox for 1D rows, CSS Grid for 2D layouts, and fluid typography.',
    steps: [
      '<strong>Design Tokens (:root):</strong> Store brand colors and spacing in <code>--primary: #1769e0;</code> so you can update the entire site theme in one line.',
      '<strong>Auto-Fit CSS Grid:</strong> Use <code>grid-template-columns: repeat(auto-fit, minmax(220px, 1fr))</code> to build responsive card grids without dozens of media queries.',
      '<strong>Fluid Typography:</strong> Use <code>font-size: clamp(1.8rem, 4vw, 3.2rem);</code> so headings scale smoothly from phone to desktop.'
    ],
    proTip: 'Always start your CSS with <code>*, *::before, *::after { box-sizing: border-box; }</code> so padding never unexpectedly widens your boxes.',
    mode: 'html',
    code: '<style>\n  :root { --brand: #1769e0; --bg: #f7faff; }\n  .pro-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(130px,1fr)); gap:10px; }\n  .pro-box { background:var(--bg); border:1px solid #cfe0fc; border-radius:10px; padding:12px; font-weight:bold; color:var(--brand); }\n</style>\n<div class="pro-grid">\n  <div class="pro-box">CSS Grid</div>\n  <div class="pro-box">Variables</div>\n  <div class="pro-box">Fluid UI</div>\n</div>'
  },
  {
    title: '4. JavaScript & DOM State',
    summary: 'JavaScript turns static pages into interactive web apps using event delegation, state updates, and APIs.',
    steps: [
      '<strong>Event Listeners:</strong> Use <code>element.addEventListener("click", ...)</code> instead of inline HTML <code>onclick</code> attributes.',
      '<strong>State-Driven UI:</strong> Keep your data in a clean JS object/array, update the state on user action, then re-render the UI from that state.',
      '<strong>Error Handling:</strong> Wrap <code>fetch()</code> network calls and <code>localStorage</code> in <code>try { ... } catch (err) { ... }</code> so your app never crashes silently.'
    ],
    proTip: 'For search inputs, debounce or filter in-memory arrays cleanly and always escape/sanitize user text with <code>textContent</code> to prevent XSS attacks.',
    mode: 'text',
    code: 'const state = { clicks: 0 };\nfunction handleAction() {\n  state.clicks += 1;\n  return `Button clicked ${state.clicks} time(s)`;\n}\nconsole.log(handleAction());',
    output: 'Button clicked 1 time(s)\n[State updated cleanly -> UI re-renders from state]'
  },
  {
    title: '5. Speed, Security & Web Vitals',
    summary: 'Fast, secure websites rank higher on Google and keep visitors engaged.',
    steps: [
      '<strong>Optimize Media:</strong> Convert heavy PNG/JPG photos to <strong>WebP</strong> or <strong>AVIF</strong> and add <code>loading="lazy"</code> on below-the-fold images.',
      '<strong>Core Web Vitals:</strong> Aim for Largest Contentful Paint (LCP) under 2.5s and zero layout shift (always set width/height on images).',
      '<strong>HTTPS &amp; Security:</strong> Always serve over HTTPS, use <code>rel="noopener noreferrer"</code> on external <code>target="_blank"</code> links, and never put API keys in frontend JS.'
    ],
    proTip: 'Run Google Lighthouse (in Chrome DevTools → Lighthouse tab) to audit Performance, Accessibility, Best Practices, and SEO out of 100.',
    mode: 'text',
    code: '<img src="hero.webp" alt="PC Build" width="800" height="450" loading="lazy">\n<a href="https://example.com" target="_blank" rel="noopener noreferrer">External Link</a>',
    output: 'Lighthouse Audit Target:\n• Performance: 95+\n• Accessibility: 100\n• Best Practices: 100\n• SEO: 100'
  },
  {
    title: '6. Git & Hosting (Going Live)',
    summary: 'Publish your website to the real internet for free using Git, GitHub, and modern edge hosting.',
    steps: [
      '<strong>Track Code with Git:</strong> Commit working milestones with clear messages like <code>git commit -m "Add responsive navbar"</code>.',
      '<strong>Deploy Free Static Hosting:</strong> Push your repo to <strong>GitHub</strong> and connect it to <strong>GitHub Pages</strong>, <strong>Cloudflare Pages</strong>, or <strong>Vercel</strong> for instant global HTTPS.',
      '<strong>Connect a Custom Domain:</strong> Point your domain’s DNS (<code>A</code> or <code>CNAME</code> record) to your host—SSL/HTTPS activates automatically.'
    ],
    proTip: 'Every time you run <code>git push</code> to your main branch, platforms like Vercel and Cloudflare Pages automatically rebuild and update your live website in seconds.',
    mode: 'text',
    code: 'git init\ngit add .\ngit commit -m "Launch Techbuilder v1"\ngit branch -M main\ngit remote add origin https://github.com/user/Techbuildergit\ngit push -u origin main',
    output: '✓ Pushed to GitHub main branch\n✓ Auto-deployed with free HTTPS SSL\n✓ Live at https://Techbuilderpages.dev'
  },
  {
    title: '7. Full Live Website Sandbox',
    summary: 'Put all 6 modules together! Edit this complete mini-website (HTML + CSS) and click "Run Live Preview".',
    steps: [
      '<strong>Header + Hero + Card Grid:</strong> Notice semantic tags, CSS variables, Flexbox/Grid, and clean contrast all working together.',
      '<strong>Challenge Yourself:</strong> Try changing the accent color, adding a second card, or editing the button text!'
    ],
    proTip: 'Once you master static HTML/CSS/JS websites, your next step is learning React or Next.js for large multi-page web applications.',
    mode: 'html',
    code: '<style>\n  .mini-site { font-family:Arial; border:1px solid #dce3ed; border-radius:10px; overflow:hidden; }\n  .mini-nav { background:#1769e0; color:#fff; padding:10px 14px; display:flex; justify-content:space-between; font-weight:bold; }\n  .mini-hero { padding:18px; background:#f7faff; text-align:center; }\n  .mini-cta { background:#1769e0; color:#fff; border:0; padding:8px 16px; border-radius:6px; margin-top:8px; cursor:pointer; }\n</style>\n<div class="mini-site">\n  <div class="mini-nav"><span>Techbuilder</span><span>Pro Demo</span></div>\n  <div class="mini-hero">\n    <h3 style="margin:0;color:#17243a">Built by Mehetab Hussain</h3>\n    <p style="font-size:13px;color:#667085;margin:6px 0">Fast, semantic, and responsive.</p>\n    <button class="mini-cta">Explore Site</button>\n  </div>\n</div>'
  }
];

const SEBA10_MODULES = [
  {
    title: 'Ch 1: Computer Networks',
    summary: 'Full Textbook Edition — Chapter 1: Introduction to Computer Networks (SEBA Class 10 Computer Science).',
    steps: [],
    proTip: 'Read through each section like a textbook—all figures, Table 1.1, terminal outputs, keywords, and exercises are included below.',
    extraHtml: `
      <div class="book-reader">
        <h3>Chapter 1: Introduction to Computer Networks</h3>
        <p>Types of computer networks and their limitations, Computer Addresses, network connecting devices, communication protocols, and basic networking commands.</p>

        <div class="book-grid">
          <div class="book-rect">
            <h4 style="margin-top:0">1.1 Computer Network</h4>
            <p>A computer network is a set of computers and units connected to share data and resources (such as a network printer) using <strong>wired</strong> (Coaxial, Twisted Pair, Optical Fiber Cable) or <strong>wireless</strong> (Bluetooth, Wi-Fi, WiMAX) technologies.</p>
            <h5>1.1.1 Types of Computer Network</h5>
            <p><strong>PAN (~10m):</strong> Simplest individual network (laptop, phone, tablet, printer).<br>
            <strong>LAN (Building):</strong> Connects devices in an office, bank, or school lab via a switch.<br>
            <strong>MAN (City):</strong> Interconnects multiple LANs via an ISP using Optical Fiber Cable.<br>
            <strong>WAN (Global):</strong> Connects locations worldwide using Leased Circuits (e.g., Internet).</p>
          </div>

          <div class="book-rect">
            <h4 style="margin-top:0">1.2 Address in Computer Networks</h4>
            <p><strong>Hostname:</strong> Editable computer name shown via <code>hostname</code> (stored in <code>/etc/hostname</code> on Linux or "Rename PC" on Windows 10).</p>
            <p><strong>IP Address:</strong> Unique numerical label. <strong>IPv4</strong> = 32-bit dot-decimal (<code>172.16.254.2</code>). <strong>IPv6</strong> = 128-bit hex with colons. <strong>DHCP</strong> assigns IPs automatically to prevent "IP conflict".</p>
            <p><strong>MAC Address:</strong> Permanent 48-bit (12-hex-digit) NIC hardware address (e.g., <code>2C-EA-7F-FF-5A-22</code>). First 24 bits (3 bytes) = <strong>OUI</strong> from IEEE.</p>
          </div>

          <div class="book-rect">
            <h4 style="margin-top:0">1.3 Network Devices</h4>
            <p><strong>NIC:</strong> Wired or wireless (antenna) hardware adapter inside motherboard or via USB.</p>
            <p><strong>Hub vs Switch:</strong> Hub repeats &amp; broadcasts data to all ports; Switch reads destination addresses and forwards only to the target port using <strong>RJ45</strong> cables.</p>
            <p><strong>Router:</strong> Connects heterogeneous networks and divides subnetworks.</p>
            <p><strong>Access Point:</strong> Creates Wi-Fi and broadcasts an <strong>SSID</strong> (open, password-protected, or hidden).</p>
          </div>

          <div class="book-rect">
            <h4 style="margin-top:0">1.4 Protocols &amp; 1.5 Commands</h4>
            <p><strong>TCP/IP:</strong> TCP splits/reassembles packets; IP addresses &amp; delivers them.<br>
            <strong>POP &amp; SMTP:</strong> POP receives email; SMTP sends email.<br>
            <strong>HTTP / HTTPS:</strong> Web pages (HTTPS encrypts data).<br>
            <strong>FTP / SFTP / FTPS:</strong> File transfer (SFTP/FTPS add encryption).</p>
            <div class="book-cmd" style="margin-bottom:0">hostname      # Computer name
ping 172.16.0.1  # Test connectivity
ipconfig      # IPv4, Subnet, Gateway
arp -a        # IP to MAC mapping</div>
          </div>

          <div class="book-rect book-wide" style="overflow-x:auto">
            <h4 style="margin-top:0">Table 1.1: PAN vs LAN vs MAN vs WAN</h4>
            <table style="width:100%;border-collapse:collapse;font-size:13px">
              <tr style="background:#1769e0;color:#fff"><th style="padding:7px;border:1px solid #dce3ed">Feature</th><th style="padding:7px;border:1px solid #dce3ed">PAN</th><th style="padding:7px;border:1px solid #dce3ed">LAN</th><th style="padding:7px;border:1px solid #dce3ed">MAN</th><th style="padding:7px;border:1px solid #dce3ed">WAN</th></tr>
              <tr><td style="padding:7px;border:1px solid #dce3ed"><strong>Ownership</strong></td><td style="padding:7px;border:1px solid #dce3ed">Private (1 person)</td><td style="padding:7px;border:1px solid #dce3ed">Private</td><td style="padding:7px;border:1px solid #dce3ed">Private or shared</td><td style="padding:7px;border:1px solid #dce3ed">Not private (multi-org)</td></tr>
              <tr><td style="padding:7px;border:1px solid #dce3ed"><strong>Speed</strong></td><td style="padding:7px;border:1px solid #dce3ed">Very High</td><td style="padding:7px;border:1px solid #dce3ed">Slower than PAN</td><td style="padding:7px;border:1px solid #dce3ed">Slower than LAN</td><td style="padding:7px;border:1px solid #dce3ed">Slower than MAN</td></tr>
              <tr><td style="padding:7px;border:1px solid #dce3ed"><strong>Congestion</strong></td><td style="padding:7px;border:1px solid #dce3ed">None</td><td style="padding:7px;border:1px solid #dce3ed">Little</td><td style="padding:7px;border:1px solid #dce3ed">More than LAN</td><td style="padding:7px;border:1px solid #dce3ed">Highest</td></tr>
              <tr><td style="padding:7px;border:1px solid #dce3ed"><strong>Maintenance</strong></td><td style="padding:7px;border:1px solid #dce3ed">Easy</td><td style="padding:7px;border:1px solid #dce3ed">Easy</td><td style="padding:7px;border:1px solid #dce3ed">More difficult</td><td style="padding:7px;border:1px solid #dce3ed">Most difficult</td></tr>
            </table>
          </div>

          <div class="book-rect">
            <h4 style="margin-top:0">Long Answer Questions (1–3)</h4>
            <p><strong>1. Network Types &amp; Comparison:</strong> PAN (~10m, private, fastest, no congestion), LAN (building/switch, private, easy), MAN (city/ISP/OFC, medium), WAN (global/Internet, multi-org, highest congestion).</p>
            <p><strong>2. IP, IPv4 vs IPv6 &amp; DHCP:</strong> IPv4 is 32-bit dot-decimal; IPv6 is 128-bit hex. DHCP assigns IPs automatically from a pool to prevent IP conflicts.</p>
            <p><strong>3. Network Devices:</strong> NIC connects PC; Hub broadcasts to all; Switch forwards to destination; Router links heterogeneous networks; Access Point broadcasts Wi-Fi SSID.</p>
          </div>

          <div class="book-rect">
            <h4 style="margin-top:0">Long Answers (4–5) &amp; Fill in Blanks</h4>
            <p><strong>4. Protocols:</strong> Rules for communication—TCP (packets), IP (addressing), POP (receive mail), SMTP (send mail), HTTP/HTTPS (web/encrypted), FTP/SFTP (files/encrypted).</p>
            <p><strong>5. Commands:</strong> <code>ping</code> (reachability), <code>ipconfig</code> (IP/mask/gateway), <code>hostname</code> (PC name), <code>arp -a</code> (IP-to-MAC table).</p>
            <p><strong>Fill in the Blanks:</strong> (1) hostname, (2) 4 &amp; 16 bytes, (3) wireless devices, (4) verify connectivity, (5) encrypted.</p>
          </div>

          <div class="book-rect book-wide">
            <h4 style="margin-top:0">Short Answer Questions (1–8)</h4>
            <div class="book-grid" style="margin-top:8px">
              <div><strong>1. MAN Components:</strong> Multiple LANs, ISP, Optical Fiber Cable (OFC).</div>
              <div><strong>2. Hostname not unique:</strong> Users can rename PCs independently.</div>
              <div><strong>3. HTTP vs FTP:</strong> HTTP fetches web pages (HTTPS = secure); FTP transfers files (SFTP/FTPS = secure).</div>
              <div><strong>4. Switches for 31 PCs:</strong> <strong>3</strong> 16-port switches (48 ports minus 4 uplink ports = 44 usable).</div>
              <div><strong>5. MAC &amp; OUI:</strong> 12-hex permanent NIC ID; first 6 hex digits (24 bits) = IEEE OUI.</div>
              <div><strong>6. Hub vs Switch:</strong> Hub broadcasts to all; Switch sends only to target address.</div>
              <div><strong>7. SSID Config:</strong> Wi-Fi name; can be password-protected, open, or invisible.</div>
              <div><strong>8. Wired vs Wireless:</strong> Wired (Coaxial, Twisted Pair, OFC); Wireless (Bluetooth, Wi-Fi, WiMAX).</div>
            </div>
          </div>

          <div class="book-rect book-wide">
            <div style="display:flex;flex-wrap:wrap;justify-content:space-between;align-items:center;gap:10px">
              <h4 style="margin:0">Multiple Choice Questions (15 Int
