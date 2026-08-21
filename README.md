<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zain -- Full-Stack Developer</title>
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html, body, #root, .app-wrap {
        background: #0C0C0C;
    }
    body {
        font-family: 'Kanit', sans-serif;
        overflow-x: clip;
    }

    .hero-heading {
        background: linear-gradient(180deg, #646973 0%, #BBCCD7 100%);
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        color: transparent;
    }

    /* ---------- fade-in-on-scroll (Framer Motion FadeIn equivalent) ---------- */
    .fade-in {
        opacity: 0;
        transform: translate(var(--fx, 0), var(--fy, 30px));
        transition: opacity .7s cubic-bezier(.25,.1,.25,1), transform .7s cubic-bezier(.25,.1,.25,1);
        transition-delay: var(--fd, 0s);
    }
    .fade-in.in-view { opacity: 1; transform: translate(0,0); }

    /* ---------- contact button ---------- */
    .btn-contact {
        display: inline-flex;
        align-items: center;
        border-radius: 9999px;
        background: linear-gradient(123deg, #18011F 7%, #B600A8 37%, #7621B0 72%, #BE4C00 100%);
        box-shadow: 0px 4px 4px rgba(181,1,167,0.25), 4px 4px 12px #7721B1 inset;
        outline: 2px solid white;
        outline-offset: -3px;
        color: #fff;
        font-weight: 500;
        text-transform: uppercase;
        letter-spacing: .12em;
        padding: .8rem 2.2rem;
        font-size: .85rem;
        text-decoration: none;
        transition: transform .25s ease;
    }
    .btn-contact:hover { transform: translateY(-2px); }

    .btn-ghost {
        display: inline-flex;
        align-items: center;
        border-radius: 9999px;
        border: 2px solid #D7E2EA;
        color: #D7E2EA;
        font-weight: 500;
        text-transform: uppercase;
        letter-spacing: .12em;
        padding: .75rem 2rem;
        font-size: .85rem;
        text-decoration: none;
        transition: background .25s ease;
        white-space: nowrap;
    }
    .btn-ghost:hover { background: rgba(215,226,234,.1); }

    /* ---------- magnet hero portrait ---------- */
    .magnet {
        display: inline-block;
        will-change: transform;
        transition: transform .6s cubic-bezier(.16,1,.3,1);
    }
    .magnet.active { transition: transform .3s ease-out; }

    .portrait-frame {
        border-radius: 32px;
        overflow: hidden;
        box-shadow: 0 40px 80px -20px rgba(0,0,0,.7);
        position: relative;
    }
    .portrait-frame::after {
        content: "";
        position: absolute; inset: 0;
        background: linear-gradient(180deg, transparent 55%, rgba(12,12,12,.65) 100%);
        pointer-events: none;
    }

    /* ---------- marquee ---------- */
    .marquee-row { display: flex; gap: .75rem; will-change: transform; }
    .marquee-tile {
        flex-shrink: 0;
        width: 300px; height: 190px;
        border-radius: 1rem;
        display: flex; flex-direction: column; align-items: center; justify-content: center;
        gap: .5rem;
        color: #D7E2EA;
        font-weight: 500;
        letter-spacing: .05em;
        text-transform: uppercase;
        font-size: .8rem;
        position: relative;
        overflow: hidden;
        border: 1px solid rgba(215,226,234,.12);
    }
    .marquee-tile span.tag {
        position: absolute; top: 12px; left: 14px;
        font-size: .65rem; opacity: .55; letter-spacing: .1em;
    }

    /* ---------- about corner decorations ---------- */
    .corner-blob {
        position: absolute;
        border-radius: 50%;
        filter: blur(2px);
        opacity: .9;
    }

    /* ---------- char reveal ---------- */
    .char { opacity: .2; transition: opacity .05s linear; }

    /* ---------- services rows ---------- */
    .service-row { border-top: 1px solid rgba(12,12,12,.15); }
    .service-row:last-child { border-bottom: 1px solid rgba(12,12,12,.15); }

    /* ---------- sticky project cards ---------- */
    .project-card {
        position: sticky;
        border-radius: 48px;
        border: 2px solid #D7E2EA;
        background: #0C0C0C;
        will-change: transform;
        transform-origin: top center;
    }

    .mockup-window {
        border-radius: 32px;
        overflow: hidden;
        position: relative;
        display: flex; align-items: center; justify-content: center;
    }
    .mockup-window .dots { position: absolute; top: 12px; left: 14px; display: flex; gap: 6px; }
    .mockup-window .dots span { width: 8px; height: 8px; border-radius: 50%; background: rgba(255,255,255,.3); }

    @media (prefers-reduced-motion: reduce) {
        .fade-in { transition-duration: .01ms !important; opacity: 1; transform: none; }
        .char { transition: none; }
    }
</style>
</head>
<body class="app-wrap">

<!-- ============================================================
     1. HERO SECTION
     ============================================================ -->
<section id="hero" class="h-screen flex flex-col overflow-x-clip relative">

    <nav class="fade-in flex justify-between px-6 md:px-10 pt-6 md:pt-8" style="--fy:-20px;">
        <a href="#about" class="text-[#D7E2EA] font-medium uppercase tracking-wider text-sm md:text-lg lg:text-[1.4rem] hover:opacity-70 transition-opacity duration-200">About</a>
        <a href="#services" class="text-[#D7E2EA] font-medium uppercase tracking-wider text-sm md:text-lg lg:text-[1.4rem] hover:opacity-70 transition-opacity duration-200">Skills</a>
        <a href="#projects" class="text-[#D7E2EA] font-medium uppercase tracking-wider text-sm md:text-lg lg:text-[1.4rem] hover:opacity-70 transition-opacity duration-200">Projects</a>
        <a href="#contact" class="text-[#D7E2EA] font-medium uppercase tracking-wider text-sm md:text-lg lg:text-[1.4rem] hover:opacity-70 transition-opacity duration-200">Contact</a>
    </nav>

    <div class="overflow-hidden w-full">
        <h1 class="fade-in hero-heading font-black uppercase tracking-tight leading-none whitespace-nowrap w-full mt-6 sm:mt-4 md:-mt-5 text-center"
            style="--fd:.15s; --fy:40px; font-size:14vw;" id="hero-h1">
            Hi, i&apos;m zain
        </h1>
    </div>

    <div class="flex-1 relative">
        <div class="magnet absolute left-1/2 -translate-x-1/2 top-1/2 -translate-y-1/2 sm:top-auto sm:translate-y-0 sm:bottom-0 z-10 w-[240px] sm:w-[300px] md:w-[360px] lg:w-[420px]" id="magnetPortrait">
            <div class="portrait-frame">
                <img src="data:image/jpeg;base64,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" class="w-full h-full object-cover" alt="Zain ul Abdeen" />
            </div>
        </div>
    </div>

    <div class="fade-in flex justify-between items-end pb-7 sm:pb-8 md:pb-10 px-6 md:px-10 relative z-20" style="--fd:.35s;">
        <p class="text-[#D7E2EA] font-light uppercase tracking-wide leading-snug max-w-[160px] sm:max-w-[220px] md:max-w-[260px]" style="font-size:clamp(0.75rem,1.4vw,1.5rem);">
            a full-stack developer driven by engineering the decisions behind great products
        </p>
        <a href="#contact" class="btn-contact fade-in" style="--fd:.5s; --fy:20px;">Contact Me</a>
    </div>

</section>

<!-- ============================================================
     2. MARQUEE SECTION
     ============================================================ -->
<section class="pt-24 sm:pt-32 md:pt-40 pb-10 overflow-hidden" id="marquee">
    <div class="flex flex-col gap-3">
        <div class="marquee-row" id="row1"></div>
        <div class="marquee-row" id="row2"></div>
    </div>
</section>

<!-- ============================================================
     3. ABOUT SECTION
     ============================================================ -->
<section id="about" class="min-h-screen flex flex-col items-center justify-center px-5 sm:px-8 md:px-10 py-20 relative">

    <div class="corner-blob fade-in" style="--fd:.1s; --fx:-80px; top:4%; left:2%; width:120px; height:120px; background:radial-gradient(circle at 35% 30%, #3A3457, #18152B); box-shadow:0 0 60px rgba(110,231,183,.15);"></div>
    <div class="corner-blob fade-in" style="--fd:.25s; --fx:-80px; bottom:8%; left:6%; width:90px; height:90px; background:radial-gradient(circle at 35% 30%, #2F9E6E, #18152B); box-shadow:0 0 50px rgba(47,158,110,.25);"></div>
    <div class="corner-blob fade-in" style="--fd:.15s; --fx:80px; top:4%; right:2%; width:130px; height:130px; background:radial-gradient(circle at 65% 30%, #6EE7B7, #18152B); box-shadow:0 0 60px rgba(110,231,183,.2);"></div>
    <div class="corner-blob fade-in" style="--fd:.3s; --fx:80px; bottom:8%; right:6%; width:100px; height:100px; background:radial-gradient(circle at 65% 30%, #3A3457, #18152B); box-shadow:0 0 50px rgba(58,52,87,.3);"></div>

    <h2 class="fade-in hero-heading font-black uppercase leading-none tracking-tight text-center" style="font-size:clamp(3rem,12vw,160px);">About me</h2>

    <div class="mt-10 sm:mt-14 md:mt-16 max-w-[560px] text-center">
        <p id="about-text" class="text-[#D7E2EA] font-medium leading-relaxed" style="font-size:clamp(1rem,2vw,1.35rem);"></p>
    </div>

    <a href="#contact" class="btn-contact mt-16 sm:mt-20 md:mt-24">Contact Me</a>
</section>

<!-- ============================================================
     4. SERVICES / SKILLS SECTION
     ============================================================ -->
<section id="services" class="bg-white rounded-t-[40px] sm:rounded-t-[50px] md:rounded-t-[60px] px-5 sm:px-8 md:px-10 py-20 sm:py-24 md:py-32">

    <h2 class="fade-in font-black uppercase text-center mb-16 sm:mb-20 md:mb-28" style="color:#0C0C0C; font-size:clamp(3rem,12vw,160px);">Skills</h2>

    <div class="max-w-5xl mx-auto">
        <div class="service-row fade-in flex items-start gap-6 py-8 sm:py-10 md:py-12">
            <span class="font-black shrink-0" style="color:#0C0C0C; font-size:clamp(3rem,10vw,140px);">01</span>
            <div>
                <h3 class="font-medium uppercase" style="color:#0C0C0C; font-size:clamp(1rem,2.2vw,2.1rem);">Full-Stack Development</h3>
                <p class="font-light leading-relaxed max-w-2xl mt-2" style="color:#0C0C0C; opacity:.6; font-size:clamp(0.85rem,1.6vw,1.25rem);">Architecting and shipping complete web applications with Laravel, PHP, Node and modern JS -- from database design to deployment.</p>
            </div>
        </div>
        <div class="service-row fade-in flex items-start gap-6 py-8 sm:py-10 md:py-12" style="--fd:.1s;">
            <span class="font-black shrink-0" style="color:#0C0C0C; font-size:clamp(3rem,10vw,140px);">02</span>
            <div>
                <h3 class="font-medium uppercase" style="color:#0C0C0C; font-size:clamp(1rem,2.2vw,2.1rem);">Front-End Engineering</h3>
                <p class="font-light leading-relaxed max-w-2xl mt-2" style="color:#0C0C0C; opacity:.6; font-size:clamp(0.85rem,1.6vw,1.25rem);">Vue.js, jQuery and Bootstrap interfaces built for speed and clarity, with pixel-level attention to detail.</p>
            </div>
        </div>
        <div class="service-row fade-in flex items-start gap-6 py-8 sm:py-10 md:py-12" style="--fd:.2s;">
            <span class="font-black shrink-0" style="color:#0C0C0C; font-size:clamp(3rem,10vw,140px);">03</span>
            <div>
                <h3 class="font-medium uppercase" style="color:#0C0C0C; font-size:clamp(1rem,2.2vw,2.1rem);">WordPress Engineering</h3>
                <p class="font-light leading-relaxed max-w-2xl mt-2" style="color:#0C0C0C; opacity:.6; font-size:clamp(0.85rem,1.6vw,1.25rem);">Custom themes, plugins and performance tuning -- a full year building production WordPress at InfoTechExpertX.</p>
            </div>
        </div>
        <div class="service-row fade-in flex items-start gap-6 py-8 sm:py-10 md:py-12" style="--fd:.3s;">
            <span class="font-black shrink-0" style="color:#0C0C0C; font-size:clamp(3rem,10vw,140px);">04</span>
            <div>
                <h3 class="font-medium uppercase" style="color:#0C0C0C; font-size:clamp(1rem,2.2vw,2.1rem);">Team Leadership</h3>
                <p class="font-light leading-relaxed max-w-2xl mt-2" style="color:#0C0C0C; opacity:.6; font-size:clamp(0.85rem,1.6vw,1.25rem);">Leading the development team at Nested Digital -- planning sprints, reviewing code, and keeping delivery on track.</p>
            </div>
        </div>
        <div class="service-row fade-in flex items-start gap-6 py-8 sm:py-10 md:py-12" style="--fd:.4s;">
            <span class="font-black shrink-0" style="color:#0C0C0C; font-size:clamp(3rem,10vw,140px);">05</span>
            <div>
                <h3 class="font-medium uppercase" style="color:#0C0C0C; font-size:clamp(1rem,2.2vw,2.1rem);">Systems & Databases</h3>
                <p class="font-light leading-relaxed max-w-2xl mt-2" style="color:#0C0C0C; opacity:.6; font-size:clamp(0.85rem,1.6vw,1.25rem);">MySQL, Firebase and Apache-backed systems designed to stay fast and reliable under real traffic.</p>
            </div>
        </div>
    </div>
</section>

<!-- ============================================================
     5. PROJECTS SECTION
     ============================================================ -->
<section id="projects" class="bg-[#0C0C0C] rounded-t-[40px] sm:rounded-t-[50px] md:rounded-t-[60px] -mt-10 sm:-mt-12 md:-mt-14 relative z-10 px-5 sm:px-8 md:px-10 pt-20 sm:pt-24 md:pt-32 pb-20">

    <h2 class="fade-in hero-heading font-black uppercase leading-none tracking-tight text-center mb-16 sm:mb-20 md:mb-28" style="font-size:clamp(3rem,12vw,160px);">Project</h2>

    <div id="projectsStack" class="max-w-5xl mx-auto relative">

        <div class="project-card p-4 sm:p-6 md:p-8" style="top:96px;" data-index="0">
            <div class="flex flex-wrap items-center justify-between gap-4 mb-6">
                <div class="flex items-center gap-4">
                    <span class="hero-heading font-black" style="font-size:clamp(3rem,10vw,140px);">01</span>
                    <div>
                        <p class="text-[#D7E2EA] opacity-60 uppercase tracking-widest text-xs">Client</p>
                        <p class="text-[#D7E2EA] font-medium uppercase" style="font-size:clamp(1.1rem,3vw,1.8rem);">Nested Digital Platform</p>
                    </div>
                </div>
                <span class="btn-ghost">Live Project</span>
            </div>
            <div class="flex gap-3">
                <div class="flex flex-col gap-3" style="width:40%;">
                    <div class="mockup-window" style="height:clamp(130px,16vw,230px); background:linear-gradient(135deg,#18152B,#201C38);">
                        <div class="dots"><span></span><span></span><span></span></div>
                        <svg width="46" height="46" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><rect x="3" y="4" width="18" height="14" rx="2"/><path d="M3 9h18"/></svg>
                    </div>
                    <div class="mockup-window" style="height:clamp(160px,22vw,340px); background:linear-gradient(160deg,#201C38,#0C0C0C);">
                        <svg width="52" height="52" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><path d="M4 17V7a2 2 0 0 1 2-2h9l5 5v7a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2Z"/><path d="M9 8h4"/><path d="M9 12h6"/></svg>
                    </div>
                </div>
                <div class="mockup-window" style="width:60%; background:linear-gradient(150deg,#0F2A20,#18152B);">
                    <svg width="70" height="70" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.3"><rect x="2" y="3" width="20" height="14" rx="2"/><path d="M8 21h8"/><path d="M12 17v4"/></svg>
                </div>
            </div>
        </div>

        <div class="project-card p-4 sm:p-6 md:p-8" style="top:124px;" data-index="1">
            <div class="flex flex-wrap items-center justify-between gap-4 mb-6">
                <div class="flex items-center gap-4">
                    <span class="hero-heading font-black" style="font-size:clamp(3rem,10vw,140px);">02</span>
                    <div>
                        <p class="text-[#D7E2EA] opacity-60 uppercase tracking-widest text-xs">Personal</p>
                        <p class="text-[#D7E2EA] font-medium uppercase" style="font-size:clamp(1.1rem,3vw,1.8rem);">Developer Portfolio</p>
                    </div>
                </div>
                <span class="btn-ghost">Live Project</span>
            </div>
            <div class="flex gap-3">
                <div class="flex flex-col gap-3" style="width:40%;">
                    <div class="mockup-window" style="height:clamp(130px,16vw,230px); background:linear-gradient(135deg,#2C2748,#18152B);">
                        <svg width="46" height="46" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><circle cx="12" cy="12" r="9"/><path d="M9 12l2 2 4-4"/></svg>
                    </div>
                    <div class="mockup-window" style="height:clamp(160px,22vw,340px); background:linear-gradient(160deg,#18152B,#0C0C0C);">
                        <svg width="52" height="52" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><path d="M4 4h16v16H4z"/><path d="M4 9h16"/><path d="M9 9v11"/></svg>
                    </div>
                </div>
                <div class="mockup-window" style="width:60%; background:linear-gradient(150deg,#201C38,#0F2A20);">
                    <svg width="70" height="70" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.3"><path d="M12 2v6"/><path d="M12 22v-6"/><circle cx="12" cy="12" r="4"/></svg>
                </div>
            </div>
        </div>

        <div class="project-card p-4 sm:p-6 md:p-8" style="top:152px;" data-index="2">
            <div class="flex flex-wrap items-center justify-between gap-4 mb-6">
                <div class="flex items-center gap-4">
                    <span class="hero-heading font-black" style="font-size:clamp(3rem,10vw,140px);">03</span>
                    <div>
                        <p class="text-[#D7E2EA] opacity-60 uppercase tracking-widest text-xs">Client</p>
                        <p class="text-[#D7E2EA] font-medium uppercase" style="font-size:clamp(1.1rem,3vw,1.8rem);">InfoTechExpertX WordPress</p>
                    </div>
                </div>
                <a href="https://infotechexpertx.us/" target="_blank" class="btn-ghost">Live Project</a>
            </div>
            <div class="flex gap-3">
                <div class="flex flex-col gap-3" style="width:40%;">
                    <div class="mockup-window" style="height:clamp(130px,16vw,230px); background:linear-gradient(135deg,#3A3457,#18152B);">
                        <svg width="46" height="46" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><path d="M3 6h18"/><path d="M3 12h18"/><path d="M3 18h18"/></svg>
                    </div>
                    <div class="mockup-window" style="height:clamp(160px,22vw,340px); background:linear-gradient(160deg,#0F2A20,#18152B);">
                        <svg width="52" height="52" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.5"><rect x="3" y="3" width="7" height="7"/><rect x="14" y="3" width="7" height="7"/><rect x="3" y="14" width="7" height="7"/><rect x="14" y="14" width="7" height="7"/></svg>
                    </div>
                </div>
                <div class="mockup-window" style="width:60%; background:linear-gradient(150deg,#18152B,#2C2748);">
                    <svg width="70" height="70" viewBox="0 0 24 24" fill="none" stroke="#6EE7B7" stroke-width="1.3"><path d="M12 20V10"/><path d="M18 20V4"/><path d="M6 20v-4"/></svg>
                </div>
            </div>
        </div>

    </div>
</section>

<!-- ============================================================
     6. CONTACT / FOOTER
     ============================================================ -->
<footer id="contact" class="bg-[#0C0C0C] text-center py-24 px-6">
    <h2 class="fade-in hero-heading font-black uppercase leading-none tracking-tight" style="font-size:clamp(2.4rem,9vw,110px);">Let's talk</h2>
    <p class="text-[#D7E2EA] opacity-70 mt-4 mb-10 max-w-md mx-auto">zjanjua6335@gmail.com &nbsp;•&nbsp; Faisalabad, Pakistan</p>
    <a href="mailto:zjanjua6335@gmail.com" class="btn-contact">Contact Me</a>
</footer>

<script>
/* ==========================================================
   FADE-IN ON SCROLL (mimics Framer Motion whileInView)
   ========================================================== */
const fadeEls = document.querySelectorAll('.fade-in');
const io = new IntersectionObserver((entries) => {
    entries.forEach(e => {
        if (e.isIntersecting) {
            e.target.classList.add('in-view');
            io.unobserve(e.target);
        }
    });
}, { threshold: 0.05, rootMargin: '0px 0px -50px 0px' });
fadeEls.forEach(el => io.observe(el));

/* ==========================================================
   MAGNET EFFECT ON HERO PORTRAIT
   ========================================================== */
const magnet = document.getElementById('magnetPortrait');
const STRENGTH = 4;
const PADDING = 120;
let magActive = false;
window.addEventListener('mousemove', (e) => {
    const r = magnet.getBoundingClientRect();
    const cx = r.left + r.width / 2;
    const cy = r.top + r.height / 2;
    const dx = e.clientX - cx;
    const dy = e.clientY - cy;
    const dist = Math.hypot(dx, dy);
    const within = dist < Math.max(r.width, r.height) / 2 + PADDING;

    if (within) {
        if (!magActive) { magnet.classList.add('active'); magActive = true; }
        magnet.style.transform = `translate3d(${dx / STRENGTH}px, ${dy / STRENGTH}px, 0)`;
    } else if (magActive) {
        magnet.classList.remove('active');
        magnet.style.transform = 'translate3d(0,0,0)';
        magActive = false;
    }
});

/* ==========================================================
   MARQUEE — scroll-linked horizontal drift
   ========================================================== */
const marqueeItems = [
    ['Laravel','Backend'], ['Vue.js','Frontend'], ['MySQL','Database'],
    ['WordPress','CMS'], ['Firebase','Cloud'], ['Bootstrap','UI'],
    ['PHP','Backend'], ['JavaScript','Core'], ['Figma','Design'],
    ['Git','Workflow'], ['Postman','API'],
];
const colors = ['#18152B','#201C38','#0F2A20','#2C2748','#18152B','#201C38'];

function buildRow(el, items, times = 3) {
    let html = '';
    for (let t = 0; t < times; t++) {
        items.forEach(([name, tag], i) => {
            const bg = colors[i % colors.length];
            html += `<div class="marquee-tile" style="background:${bg};">
                <span class="tag">${tag}</span>
                <span style="font-size:1.4rem; font-weight:700; color:#F3EFE6; text-transform:none; letter-spacing:0;">${name}</span>
            </div>`;
        });
    }
    el.innerHTML = html;
}
const row1El = document.getElementById('row1');
const row2El = document.getElementById('row2');
buildRow(row1El, marqueeItems.slice(0, 6));
buildRow(row2El, marqueeItems.slice(5));

const marqueeSection = document.getElementById('marquee');
function updateMarquee() {
    const rect = marqueeSection.getBoundingClientRect();
    const sectionTop = rect.top + window.scrollY;
    const offset = (window.scrollY - sectionTop + window.innerHeight) * 0.3;
    row1El.style.transform = `translateX(${offset - 400}px)`;
    row2El.style.transform = `translateX(${-(offset - 400)}px)`;
}
window.addEventListener('scroll', updateMarquee, { passive: true });
updateMarquee();

/* ==========================================================
   ABOUT — character-by-character scroll reveal
   ========================================================== */
const ABOUT_TEXT = "With over three years of hands-on experience across full-stack and WordPress development, I focus on building fast, reliable products, i truly enjoy working with teams that want to ship something they're proud of. Let's build something incredible together!";
const aboutP = document.getElementById('about-text');
aboutP.innerHTML = ABOUT_TEXT.split('').map(c => `<span class="char">${c === ' ' ? '&nbsp;' : c}</span>`).join('');
const chars = aboutP.querySelectorAll('.char');

function updateAboutReveal() {
    const rect = aboutP.getBoundingClientRect();
    const start = window.innerHeight * 0.8;
    const end = window.innerHeight * 0.2;
    const progress = Math.min(1, Math.max(0, (start - rect.top) / (start - end)));
    const revealCount = Math.floor(progress * chars.length);
    chars.forEach((c, i) => { c.style.opacity = i < revealCount ? 1 : 0.2; });
}
window.addEventListener('scroll', updateAboutReveal, { passive: true });
updateAboutReveal();

/* ==========================================================
   PROJECTS — sticky stack scale-down effect
   ========================================================== */
const cards = document.querySelectorAll('.project-card');
function updateStack() {
    const total = cards.length;
    cards.forEach((card, i) => {
        const rect = card.getBoundingClientRect();
        const start = window.innerHeight * 0.9;
        const raw = 1 - Math.min(1, Math.max(0, (start - rect.top) / (start + rect.height)));
        const targetScale = 1 - (total - 1 - i) * 0.03;
        const scale = 1 - (1 - targetScale) * raw;
        card.style.transform = `scale(${scale})`;
    });
}
window.addEventListener('scroll', updateStack, { passive: true });
updateStack();

/* responsive hero font (approximates 14vw / 17.5vw across breakpoints) */
function sizeHero() {
    const w = window.innerWidth;
    const h1 = document.getElementById('hero-h1');
    let vw = 14;
    if (w >= 1024) vw = 17.5;
    else if (w >= 768) vw = 16;
    else if (w >= 640) vw = 15;
    h1.style.fontSize = vw + 'vw';
}
window.addEventListener('resize', sizeHero);
sizeHero();
</script>
</body>
</html>
