<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Test Bazar — অনলাইন পরীক্ষার প্রস্তুতি</title>
<link href="https://fonts.googleapis.com/css2?family=Tiro+Bangla:ital@0;1&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet">
<style>
:root {
  --green: #1a7a4a;
  --green-light: #2aad68;
  --green-pale: #e8f7ef;
  --saffron: #e8730a;
  --dark: #0f1a14;
  --text: #1c2e24;
  --muted: #5a7a66;
  --border: #c5dccb;
  --white: #f8fdf9;
}
* { margin: 0; padding: 0; box-sizing: border-box; }
html { scroll-behavior: smooth; }
body { font-family: 'Syne', sans-serif; background: var(--white); color: var(--text); overflow-x: hidden; }

/* NAV */
nav {
  position: fixed; top: 0; left: 0; right: 0; z-index: 100;
  display: flex; align-items: center; justify-content: space-between;
  padding: 1rem 2rem;
  background: rgba(248,253,249,0.95);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border);
}
.logo { font-size: 1.4rem; font-weight: 800; color: var(--green); }
.logo span { color: var(--saffron); }
.nav-links a { text-decoration: none; color: var(--text); font-size: 0.85rem; font-weight: 600; margin-left: 1.5rem; transition: color 0.2s; }
.nav-links a:hover { color: var(--green); }
.nav-cta { background: var(--green) !important; color: white !important; padding: 0.45rem 1.1rem; border-radius: 6px; }

/* HERO */
.hero {
  min-height: 100vh;
  display: flex; align-items: center;
  padding: 7rem 2rem 4rem;
  background: linear-gradient(160deg, #f0faf4 0%, #fdf6ee 100%);
}
.hero-inner { max-width: 1100px; margin: 0 auto; width: 100%; display: grid; grid-template-columns: 1fr 1fr; gap: 4rem; align-items: center; }
.hero-tag { display: inline-block; background: var(--green-pale); color: var(--green); font-size: 0.75rem; font-weight: 700; padding: 0.3rem 0.9rem; border-radius: 20px; border: 1px solid rgba(26,122,74,0.2); margin-bottom: 1.2rem; text-transform: uppercase; letter-spacing: 1px; }
h1 { font-family: 'Tiro Bangla', serif; font-size: clamp(2rem, 4vw, 3rem); line-height: 1.3; color: var(--dark); margin-bottom: 1rem; }
h1 em { font-style: normal; color: var(--green); }
.hero-sub { font-family: 'Tiro Bangla', serif; font-size: 1rem; color: var(--muted); line-height: 1.8; margin-bottom: 2rem; }
.hero-btns { display: flex; gap: 1rem; flex-wrap: wrap; }
.btn-primary { background: var(--green); color: white; padding: 0.8rem 1.8rem; border-radius: 8px; font-size: 0.95rem; font-weight: 700; cursor: pointer; border: none; text-decoration: none; display: inline-block; transition: all 0.2s; box-shadow: 0 4px 15px rgba(26,122,74,0.3); font-family: 'Tiro Bangla', serif; }
.btn-primary:hover { background: var(--green-light); transform: translateY(-2px); }
.btn-secondary { background: white; color: var(--green); padding: 0.8rem 1.8rem; border-radius: 8px; font-size: 0.95rem; font-weight: 700; cursor: pointer; border: 2px solid var(--green); text-decoration: none; display: inline-block; transition: all 0.2s; font-family: 'Tiro Bangla', serif; }
.btn-secondary:hover { background: var(--green-pale); }

/* HERO CARD */
.hero-card { background: white; border-radius: 16px; padding: 1.8rem; box-shadow: 0 20px 60px rgba(15,26,20,0.12); border: 1px solid var(--border); }
.card-tag { background: var(--green-pale); color: var(--green); font-size: 0.75rem; font-weight: 700; padding: 0.25rem 0.7rem; border-radius: 10px; display: inline-block; margin-bottom: 1rem; }
.class-grid { display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 0.6rem; }
.class-card { border: 1.5px solid var(--border); border-radius: 10px; padding: 0.8rem 0.6rem; text-align: center; cursor: pointer; transition: all 0.2s; }
.class-card:hover, .class-card.active { border-color: var(--green); background: var(--green-pale); }
.class-num { font-size: 1.2rem; font-weight: 800; color: var(--green); }
.class-label { font-family: 'Tiro Bangla', serif; font-size: 0.75rem; color: var(--muted); margin-top: 0.2rem; }
.subjects-show { margin-top: 1rem; background: var(--green-pale); border-radius: 8px; padding: 0.8rem; display: none; }
.subjects-show.active { display: block; }
.subj-item { font-family: 'Tiro Bangla', serif; font-size: 0.85rem; color: var(--text); padding: 0.25rem 0; }
.subj-item::before { content: "✓ "; color: var(--green); font-weight: 700; }

/* STATS */
.stats { background: var(--dark); padding: 3rem 2rem; }
.stats-inner { max-width: 1100px; margin: 0 auto; display: grid; grid-template-columns: repeat(4, 1fr); gap: 2rem; text-align: center; }
.stat-num { font-size: 2.2rem; font-weight: 800; color: var(--green-light); }
.stat-label { font-family: 'Tiro Bangla', serif; font-size: 0.9rem; color: rgba(255,255,255,0.6); margin-top: 0.3rem; }

/* CLASSES */
.classes { padding: 5rem 2rem; background: white; }
.section-inner { max-width: 1100px; margin: 0 auto; }
.section-label { font-size: 0.75rem; font-weight: 700; letter-spacing: 2px; text-transform: uppercase; color: var(--saffron); margin-bottom: 0.5rem; }
h2 { font-family: 'Tiro Bangla', serif; font-size: clamp(1.6rem, 3vw, 2.2rem); color: var(--dark); margin-bottom: 0.5rem; }
.section-sub { font-family: 'Tiro Bangla', serif; color: var(--muted); font-size: 1rem; margin-bottom: 2.5rem; }

.class-tabs { display: flex; gap: 0.5rem; margin-bottom: 2rem; flex-wrap: wrap; }
.tab { padding: 0.5rem 1.2rem; border-radius: 20px; border: 1.5px solid var(--border); font-family: 'Tiro Bangla', serif; font-size: 0.9rem; cursor: pointer; transition: all 0.2s; background: white; color: var(--text); }
.tab.active { background: var(--green); color: white; border-color: var(--green); }

.subject-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(200px, 1fr)); gap: 1rem; }
.subject-card { border: 1.5px solid var(--border); border-radius: 12px; padding: 1.2rem; transition: all 0.2s; }
.subject-card:hover { border-color: var(--green); box-shadow: 0 8px 25px rgba(26,122,74,0.1); transform: translateY(-2px); }
.subject-icon { font-size: 1.8rem; margin-bottom: 0.5rem; }
.subject-name { font-family: 'Tiro Bangla', serif; font-size: 0.95rem; font-weight: 600; color: var(--dark); }
.subject-chapters { font-size: 0.75rem; color: var(--muted); margin-top: 0.3rem; }
.subject-badge { display: inline-block; font-size: 0.7rem; background: var(--green-pale); color: var(--green); padding: 0.15rem 0.5rem; border-radius: 8px; margin-top: 0.4rem; }

/* PRICING */
.pricing { padding: 5rem 2rem; background: linear-gradient(180deg, #f0faf4 0%, white 100%); }
.pricing-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.5rem; max-width: 900px; margin: 0 auto; }
.price-card { background: white; border: 1.5px solid var(--border); border-radius: 16px; padding: 2rem 1.5rem; position: relative; transition: all 0.2s; }
.price-card:hover { box-shadow: 0 12px 40px rgba(15,26,20,0.1); transform: translateY(-4px); }
.price-card.popular { border-color: var(--green); box-shadow: 0 8px 30px rgba(26,122,74,0.15); }
.popular-badge { position: absolute; top: -12px; left: 50%; transform: translateX(-50%); background: var(--green); color: white; font-size: 0.7rem; font-weight: 700; padding: 0.25rem 0.9rem; border-radius: 20px; white-space: nowrap; }
.price-plan { font-family: 'Tiro Bangla', serif; font-size: 1rem; color: var(--muted); margin-bottom: 0.5rem; }
.price-amount { font-size: 2.5rem; font-weight: 800; color: var(--dark); line-height: 1; }
.price-amount span { font-size: 1rem; font-weight: 400; color: var(--muted); }
.price-divider { border: none; border-top: 1px solid var(--border); margin: 1.2rem 0; }
.price-feat { font-family: 'Tiro Bangla', serif; font-size: 0.88rem; color: var(--text); padding: 0.35rem 0; }
.price-feat::before { content: "✓ "; color: var(--green); font-weight: 700; }
.price-feat.no::before { content: "✗ "; color: #ccc; }
.price-feat.no { color: var(--muted); }
.price-btn { width: 100%; margin-top: 1.5rem; padding: 0.75rem; border-radius: 8px; font-family: 'Tiro Bangla', serif; font-size: 0.95rem; font-weight: 600; cursor: pointer; border: 2px solid var(--green); transition: all 0.2s; }
.price-btn.filled { background: var(--green); color: white; }
.price-btn.filled:hover { background: var(--green-light); }
.price-btn.outline { background: white; color: var(--green); }
.price-btn.outline:hover { background: var(--green-pale); }

/* HOW IT WORKS */
.howitworks { padding: 5rem 2rem; background: white; }
.steps { display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.5rem; margin-top: 2.5rem; }
.step { text-align: center; padding: 1.5rem 1rem; }
.step-num { width: 48px; height: 48px; border-radius: 50%; background: var(--green-pale); color: var(--green); font-size: 1.2rem; font-weight: 800; display: flex; align-items: center; justify-content: center; margin: 0 auto 1rem; }
.step-title { font-family: 'Tiro Bangla', serif; font-size: 1rem; font-weight: 600; color: var(--dark); margin-bottom: 0.4rem; }
.step-desc { font-family: 'Tiro Bangla', serif; font-size: 0.85rem; color: var(--muted); line-height: 1.6; }

/* FOOTER */
footer { background: var(--dark); padding: 2.5rem 2rem; text-align: center; }
footer p { font-family: 'Tiro Bangla', serif; font-size: 0.85rem; color: rgba(255,255,255,0.4); margin: 0.3rem 0; }

/* RESPONSIVE */
@media (max-width: 768px) {
  .hero-inner { grid-template-columns: 1fr; gap: 2rem; }
  .stats-inner { grid-template-columns: repeat(2, 1fr); }
  .pricing-grid { grid-template-columns: 1fr; max-width: 360px; margin: 0 auto; }
  .steps { grid-template-columns: repeat(2, 1fr); }
  .nav-links { display: none; }
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Test <span>Bazar</span></div>
  <div class="nav-links">
    <a href="#classes">বিষয়সমূহ</a>
    <a href="#pricing">মূল্য</a>
    <a href="#howitworks">কীভাবে কাজ করে</a>
    <a href="register.html" class="nav-cta">Registration করুন</a>
  </div>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-inner">
    <div>
      <div class="hero-tag">Class 10 · HS Sem 1 · HS Sem 3</div>
      <h1>পরীক্ষার প্রস্তুতি নাও <em>সঠিকভাবে</em></h1>
      <p class="hero-sub">Test Bazar এ Chapter-wise MCQ Test, Mock Test — সব বাংলায়। Class 10, একাদশ ও দ্বাদশ শ্রেণির জন্য।</p>
      <div class="hero-btns">
        <a href="register.html" class="btn-primary">এখনই শুরু করো →</a>
        <a href="#classes" class="btn-secondary">বিষয় দেখো</a>
      </div>
    </div>
    <div class="hero-card">
      <div class="card-tag">কোন Class এর জন্য?</div>
      <div class="class-grid">
        <div class="class-card active" onclick="showClass(this,'10')">
          <div class="class-num">10</div>
          <div class="class-label">মাধ্যমিক</div>
        </div>
        <div class="class-card" onclick="showClass(this,'11')">
          <div class="class-num">11</div>
          <div class="class-label">Sem 1</div>
        </div>
        <div class="class-card" onclick="showClass(this,'12')">
          <div class="class-num">12</div>
          <div class="class-label">Sem 3</div>
        </div>
      </div>
      <div class="subjects-show active" id="subjects-10">
        <div class="subj-item">বাংলা</div>
        <div class="subj-item">ইংরেজি</div>
        <div class="subj-item">গণিত</div>
        <div class="subj-item">ইতিহাস · ভূগোল</div>
        <div class="subj-item">জীবন বিজ্ঞান · ভৌত বিজ্ঞান</div>
      </div>
      <div class="subjects-show" id="subjects-11">
        <div class="subj-item">বাংলা (Sem 1)</div>
        <div class="subj-item">ইতিহাস (Sem 1)</div>
        <div class="subj-item">রাষ্ট্রবিজ্ঞান (Sem 1)</div>
        <div class="subj-item">ভূগোল (Sem 1)</div>
        <div class="subj-item">দর্শন (Sem 1)</div>
      </div>
      <div class="subjects-show" id="subjects-12">
        <div class="subj-item">বাংলা (Sem 3)</div>
        <div class="subj-item">ইতিহাস (Sem 3)</div>
        <div class="subj-item">রাষ্ট্রবিজ্ঞান (Sem 3)</div>
        <div class="subj-item">ভূগোল (Sem 3)</div>
        <div class="subj-item">দর্শন (Sem 3)</div>
      </div>
    </div>
  </div>
</section>

<!-- STATS -->
<div class="stats">
  <div class="stats-inner">
    <div><div class="stat-num">৩টি</div><div class="stat-label">Class উপলব্ধ</div></div>
    <div><div class="stat-num">১০+</div><div class="stat-label">বিষয়</div></div>
    <div><div class="stat-num">Chapter-wise</div><div class="stat-label">MCQ Test</div></div>
    <div><div class="stat-num">Mock Test</div><div class="stat-label">প্রতি বিষয়ে</div></div>
  </div>
</div>

<!-- CLASSES -->
<section class="classes" id="classes">
  <div class="section-inner">
    <div class="section-label">বিষয়সমূহ</div>
    <h2>Chapter-wise Test যা পাবে</h2>
    <p class="section-sub">প্রতিটি chapter আলাদা test · শেষে Mock Test</p>

    <div class="class-tabs">
      <button class="tab active" onclick="switchTab(this,'tab-10')">Class 10</button>
      <button class="tab" onclick="switchTab(this,'tab-11')">Class 11 (Sem 1 · Arts)</button>
      <button class="tab" onclick="switchTab(this,'tab-12')">Class 12 (Sem 3 · Arts)</button>
    </div>

    <!-- CLASS 10 -->
    <div id="tab-10" class="subject-grid">
      <div class="subject-card"><div class="subject-icon">📖</div><div class="subject-name">বাংলা</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">🔤</div><div class="subject-name">ইংরেজি</div><div class="subject-chapters">Grammar + Literature</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">📐</div><div class="subject-name">গণিত</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">🌿</div><div class="subject-name">জীবন বিজ্ঞান</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">⚡</div><div class="subject-name">ভৌত বিজ্ঞান</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">🌍</div><div class="subject-name">ভূগোল</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
      <div class="subject-card"><div class="subject-icon">📜</div><div class="subject-name">ইতিহাস</div><div class="subject-chapters">Chapter-wise + Mock</div><div class="subject-badge">সব chapter</div></div>
    </div>

    <!-- CLASS 11 -->
    <div id="tab-11" class="subject-grid" style="display:none">
      <div class="subject-card"><div class="subject-icon">📖</div><div class="subject-name">বাংলা</div><div class="subject-chapters">Sem 1 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">📜</div><div class="subject-name">ইতিহাস</div><div class="subject-chapters">Sem 1 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🏛️</div><div class="subject-name">রাষ্ট্রবিজ্ঞান</div><div class="subject-chapters">Sem 1 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🌍</div><div class="subject-name">ভূগোল</div><div class="subject-chapters">Sem 1 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🧠</div><div class="subject-name">দর্শন</div><div class="subject-chapters">Sem 1 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card" style="border-style:dashed;opacity:0.6"><div class="subject-icon">🔬</div><div class="subject-name">Science</div><div class="subject-chapters">শীঘ্রই আসছে</div><div class="subject-badge" style="background:#faeeda;color:#633806">Coming Soon</div></div>
    </div>

    <!-- CLASS 12 -->
    <div id="tab-12" class="subject-grid" style="display:none">
      <div class="subject-card"><div class="subject-icon">📖</div><div class="subject-name">বাংলা</div><div class="subject-chapters">Sem 3 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">📜</div><div class="subject-name">ইতিহাস</div><div class="subject-chapters">Sem 3 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🏛️</div><div class="subject-name">রাষ্ট্রবিজ্ঞান</div><div class="subject-chapters">Sem 3 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🌍</div><div class="subject-name">ভূগোল</div><div class="subject-chapters">Sem 3 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card"><div class="subject-icon">🧠</div><div class="subject-name">দর্শন</div><div class="subject-chapters">Sem 3 · Chapter-wise</div><div class="subject-badge">Arts</div></div>
      <div class="subject-card" style="border-style:dashed;opacity:0.6"><div class="subject-icon">🔬</div><div class="subject-name">Science</div><div class="subject-chapters">শীঘ্রই আসছে</div><div class="subject-badge" style="background:#faeeda;color:#633806">Coming Soon</div></div>
    </div>
  </div>
</section>

<!-- PRICING -->
<section class="pricing" id="pricing">
  <div class="section-inner">
    <div style="text-align:center;margin-bottom:2.5rem">
      <div class="section-label">মূল্য পরিকল্পনা</div>
      <h2>তোমার বাজেট অনুযায়ী বেছে নাও</h2>
      <p class="section-sub">UPI / GPay / PhonePe / Paytm এ payment করা যাবে</p>
    </div>
    <div class="pricing-grid">
      <div class="price-card">
        <div class="price-plan">ফ্রি</div>
        <div class="price-amount">₹০</div>
        <hr class="price-divider">
        <div class="price-feat">Demo test দেখা</div>
        <div class="price-feat">Result দেখা</div>
        <div class="price-feat no">Chapter-wise test</div>
        <div class="price-feat no">Mock test</div>
        <button class="price-btn outline" onclick="window.location.href='register.html'">শুরু করো</button>
      </div>
      <div class="price-card popular">
        <div class="popular-badge">সবচেয়ে জনপ্রিয়</div>
        <div class="price-plan">মাসিক</div>
        <div class="price-amount">₹৯৯ <span>/ মাস</span></div>
        <hr class="price-divider">
        <div class="price-feat">সব class এর test</div>
        <div class="price-feat">Chapter-wise MCQ</div>
        <div class="price-feat">Mock test</div>
        <div class="price-feat">Result analysis</div>
        <button class="price-btn filled" onclick="window.location.href='register.html'">এখনই নাও</button>
      </div>
      <div class="price-card">
        <div class="price-plan">বার্ষিক</div>
        <div class="price-amount">₹৮৯৯ <span>/ বছর</span></div>
        <hr class="price-divider">
        <div class="price-feat">সব মাসিক সুবিধা</div>
        <div class="price-feat">২ মাস ফ্রি</div>
        <div class="price-feat">Priority support</div>
        <div class="price-feat">New content আগে পাবে</div>
        <button class="price-btn outline" onclick="window.location.href='register.html'">বার্ষিক নাও</button>
      </div>
    </div>
    <p style="text-align:center;font-family:'Tiro Bangla',serif;font-size:0.85rem;color:var(--muted);margin-top:1.5rem">
      💳 UPI ID: <strong style="color:var(--green)">ajsuajsu71@oksbi</strong> · WhatsApp: <strong style="color:var(--green)">+91 8710032880</strong>
    </p>
  </div>
</section>

<!-- HOW IT WORKS -->
<section class="howitworks" id="howitworks">
  <div class="section-inner">
    <div style="text-align:center">
      <div class="section-label">কীভাবে কাজ করে</div>
      <h2>মাত্র ৪টা ধাপ</h2>
      <p class="section-sub">Registration থেকে Test — সব সহজ</p>
    </div>
    <div class="steps">
      <div class="step">
        <div class="step-num">১</div>
        <div class="step-title">Registration করো</div>
        <div class="step-desc">নাম, email, mobile নম্বর দিয়ে register করো</div>
      </div>
      <div class="step">
        <div class="step-num">২</div>
        <div class="step-title">Payment করো</div>
        <div class="step-desc">UPI তে payment করো, screenshot পাঠাও WhatsApp এ</div>
      </div>
      <div class="step">
        <div class="step-num">৩</div>
        <div class="step-title">ID পাও</div>
        <div class="step-desc">WhatsApp এ User ID ও Password পাবে</div>
      </div>
      <div class="step">
        <div class="step-num">৪</div>
        <div class="step-title">Test দাও</div>
        <div class="step-desc">Login করে chapter-wise ও mock test দাও</div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <p><strong style="color:#2aad68">Test Bazar</strong> — Class 10 · HS Sem 1 · HS Sem 3</p>
  <p>UPI: yourname@gpay · WhatsApp: +91 XXXXXXXXXX</p>
</footer>

<script>
function showClass(el, cls) {
  document.querySelectorAll('.class-card').forEach(c => c.classList.remove('active'));
  document.querySelectorAll('.subjects-show').forEach(s => s.classList.remove('active'));
  el.classList.add('active');
  document.getElementById('subjects-' + cls).classList.add('active');
}

function switchTab(el, tabId) {
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.querySelectorAll('.subject-grid').forEach(g => g.style.display = 'none');
  el.classList.add('active');
  document.getElementById(tabId).style.display = 'grid';
}
</script>
</body>
</html>
