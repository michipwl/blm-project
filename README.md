<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Black Lives Matter — Before & After Timeline</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=Inter:wght@400;500;600&family=Mono:wght@400&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --bg: #080810;
    --surface: #0f0f1a;
    --border: #1e1e30;
    --text: #e8e8f0;
    --muted: #5a5a7a;
    --before: #7c3aed;
    --before-dim: #1a0d35;
    --turning: #d97706;
    --turning-dim: #1f1200;
    --after: #059669;
    --after-dim: #021a10;
    --impact: #10b981;
    --line: #1e1e30;
  }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Inter', system-ui, sans-serif;
    font-size: 15px;
    line-height: 1.6;
    min-height: 100vh;
    padding: 0 0 80px;
  }

  /* ── HERO ── */
  .hero {
    text-align: center;
    padding: 72px 24px 56px;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background: radial-gradient(ellipse 80% 60% at 50% 0%, rgba(124,58,237,.18) 0%, transparent 70%);
    pointer-events: none;
  }
  .hero-eyebrow {
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 20px;
  }
  .hero-title {
    font-family: 'Playfair Display', Georgia, serif;
    font-size: clamp(36px, 8vw, 72px);
    font-weight: 900;
    line-height: 1.05;
    color: #fff;
    margin-bottom: 10px;
  }
  .hero-title span {
    color: var(--before);
  }
  .hero-sub {
    font-size: 16px;
    color: var(--muted);
    max-width: 480px;
    margin: 0 auto 36px;
  }

  /* Legend */
  .legend {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
  }
  .legend-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 12px;
    color: #9898b8;
  }
  .legend-dot {
    width: 10px; height: 10px;
    border-radius: 50%;
    flex-shrink: 0;
  }

  /* ── TIMELINE WRAPPER ── */
  .timeline {
    max-width: 700px;
    margin: 0 auto;
    padding: 0 20px;
    position: relative;
  }
  .timeline::before {
    content: '';
    position: absolute;
    left: 39px;
    top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--line) 10%, var(--line) 90%, transparent);
  }

  /* ── ITEM ── */
  .item {
    display: flex;
    gap: 20px;
    margin-bottom: 20px;
    position: relative;
  }

  /* Icon bubble */
  .icon-wrap {
    flex-shrink: 0;
    width: 58px; height: 58px;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
    position: relative;
    z-index: 1;
    transition: transform .2s;
    cursor: pointer;
    border: 1.5px solid transparent;
  }
  .item[data-type="before"] .icon-wrap  { background: var(--before-dim);  border-color: var(--before);  }
  .item[data-type="turning"] .icon-wrap { background: var(--turning-dim); border-color: var(--turning); }
  .item[data-type="after"] .icon-wrap   { background: var(--after-dim);   border-color: var(--after);   }

  .item.open .icon-wrap { transform: scale(1.1); }

  /* Card */
  .card {
    flex: 1;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: var(--surface);
    overflow: hidden;
    transition: border-color .2s, background .2s;
    cursor: pointer;
  }
  .item.open .card { background: var(--surface); }
  .item[data-type="before"].open .card  { border-color: var(--before);  background: var(--before-dim); }
  .item[data-type="turning"].open .card { border-color: var(--turning); background: var(--turning-dim); }
  .item[data-type="after"].open .card   { border-color: var(--after);   background: var(--after-dim);  }

  .card-head {
    padding: 14px 18px 12px;
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    gap: 12px;
  }
  .badge {
    display: inline-block;
    font-size: 10px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1.5px;
    padding: 3px 9px;
    border-radius: 99px;
    color: #fff;
    flex-shrink: 0;
  }
  .item[data-type="before"]  .badge { background: var(--before); }
  .item[data-type="turning"] .badge { background: var(--turning); }
  .item[data-type="after"]   .badge { background: var(--after); }

  .date {
    font-size: 11px;
    color: var(--muted);
    margin-top: 5px;
  }
  .chevron {
    font-size: 11px;
    color: var(--muted);
    margin-top: 4px;
    flex-shrink: 0;
    transition: transform .2s;
  }
  .item.open .chevron { transform: rotate(180deg); }

  .card-title {
    font-family: 'Playfair Display', Georgia, serif;
    font-size: 15px;
    font-weight: 700;
    color: #f0f0ff;
    padding: 0 18px 12px;
  }

  /* Body */
  .card-body {
    display: none;
    padding: 0 18px 16px;
  }
  .item.open .card-body { display: block; }

  .card-desc {
    font-size: 14px;
    color: #b8b8d8;
    line-height: 1.65;
    margin-bottom: 12px;
  }

  .impact-box {
    background: rgba(16,185,129,.08);
    border: 1px solid rgba(16,185,129,.25);
    border-radius: 8px;
    padding: 12px 14px;
  }
  .impact-label {
    font-size: 10px;
    font-weight: 700;
    color: var(--impact);
    text-transform: uppercase;
    letter-spacing: 1.5px;
    margin-bottom: 6px;
  }
  .impact-text {
    font-size: 13px;
    color: #6ee7b7;
    line-height: 1.6;
  }

  /* ── SECTION DIVIDER ── */
  .divider {
    text-align: center;
    margin: 32px 0 24px;
    position: relative;
  }
  .divider::before {
    content: '';
    position: absolute;
    top: 50%; left: 0; right: 0;
    height: 1px;
    background: var(--border);
  }
  .divider span {
    position: relative;
    background: var(--bg);
    padding: 0 16px;
    font-size: 11px;
    font-weight: 700;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* ── FOOTER NOTE ── */
  .footer {
    text-align: center;
    margin-top: 48px;
    font-size: 11px;
    color: var(--muted);
    line-height: 1.8;
  }

  /* ── HOVER ── */
  .card:hover { border-color: #30305a; }
  .item[data-type="before"].open .card:hover  { border-color: var(--before); }
  .item[data-type="turning"].open .card:hover { border-color: var(--turning); }
  .item[data-type="after"].open .card:hover   { border-color: var(--after); }

  @media (max-width: 520px) {
    .hero { padding: 48px 16px 40px; }
    .timeline::before { left: 30px; }
    .icon-wrap { width: 46px; height: 46px; font-size: 20px; }
    .timeline { padding: 0 12px; }
  }
</style>
</head>
<body>

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow">Group 4 · Protests &amp; Impact</div>
  <h1 class="hero-title">Black Lives<br><span>Matter</span></h1>
  <p class="hero-sub">A "Before and After" timeline — from the first hashtag to real policy change.</p>
  <div class="legend">
    <div class="legend-item"><div class="legend-dot" style="background:#7c3aed"></div> Before BLM</div>
    <div class="legend-item"><div class="legend-dot" style="background:#d97706"></div> Turning Point</div>
    <div class="legend-item"><div class="legend-dot" style="background:#059669"></div> After / Impact</div>
  </div>
</div>

<!-- TIMELINE -->
<div class="timeline">

  <div class="divider"><span>Origins</span></div>

  <!-- 1 -->
  <div class="item" data-type="before" onclick="toggle(this)">
    <div class="icon-wrap">✊</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">Before BLM</span><div class="date">July 13, 2013</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">The Hashtag That Started a Movement</div>
      <div class="card-body">
        <p class="card-desc">After George Zimmerman was acquitted for the killing of unarmed teenager Trayvon Martin, Alicia Garza, Patrisse Cullors, and Opal Tometi founded Black Lives Matter — initially as the hashtag #BlackLivesMatter on social media. It grew rapidly into a decentralized movement against systemic racism and police brutality.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Why it mattered</div>
          <p class="impact-text">Social media turned a local outrage into a national conversation about race and justice for the first time at this scale.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 2 -->
  <div class="item" data-type="before" onclick="toggle(this)">
    <div class="icon-wrap">🎥</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">Before BLM</span><div class="date">July 17, 2014</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Eric Garner — "I Can't Breathe"</div>
      <div class="card-body">
        <p class="card-desc">NYPD officer Daniel Pantaleo put 43-year-old Eric Garner in a chokehold, killing him. Footage captured Garner saying "I can't breathe" eleven times. Pantaleo was never charged, triggering protests in New York. The phrase has since been echoed by countless activists — including at the George Floyd protests six years later.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">New York passed the Eric Garner Anti-Chokehold Act in June 2020, making police use of chokeholds a criminal offense.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 3 -->
  <div class="item" data-type="before" onclick="toggle(this)">
    <div class="icon-wrap">📢</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">Before BLM</span><div class="date">August 9, 2014</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Michael Brown Shot in Ferguson</div>
      <div class="card-body">
        <p class="card-desc">Police officer Darren Wilson shot and killed 18-year-old Michael Brown in Ferguson, Missouri. Mass protests erupted in the city for weeks. This became a defining turning point in BLM's transformation from an online hashtag into an organised street movement.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">A Department of Justice investigation was launched into the Ferguson police department. Ferguson protests catapulted BLM into national and international headlines.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 4 -->
  <div class="item" data-type="before" onclick="toggle(this)">
    <div class="icon-wrap">⚖️</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">Before BLM</span><div class="date">March 13, 2020</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Breonna Taylor Killed in No-Knock Raid</div>
      <div class="card-body">
        <p class="card-desc">Louisville police executed a no-knock warrant and fatally shot 26-year-old EMT Breonna Taylor while she slept in her home. No officers were charged with her killing, igniting widespread anger across the country.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">Louisville unanimously passed "Breonna's Law" banning no-knock warrants. Her case became a global symbol of police impunity.</p>
        </div>
      </div>
    </div>
  </div>

  <div class="divider"><span>The Turning Point</span></div>

  <!-- 5 — TURNING -->
  <div class="item" data-type="turning" onclick="toggle(this)">
    <div class="icon-wrap">🌍</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">Turning Point</span><div class="date">May 25, 2020</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">George Floyd Murdered in Minneapolis</div>
      <div class="card-body">
        <p class="card-desc">Officer Derek Chauvin knelt on George Floyd's neck for over 9 minutes during an arrest, killing him. A bystander's video spread globally within hours, triggering the largest wave of protests in American history. Floyd's daughter later said: "Daddy changed the world."</p>
        <div class="impact-box">
          <div class="impact-label">📌 Scale</div>
          <p class="impact-text">An estimated 15–26 million people participated in U.S. protests — making it the largest protest movement in American history. Over 1.2 million #BlackLivesMatter tweets were posted on a single day in June 2020.</p>
        </div>
      </div>
    </div>
  </div>

  <div class="divider"><span>After — Policy &amp; Change</span></div>

  <!-- 6 -->
  <div class="item" data-type="after" onclick="toggle(this)">
    <div class="icon-wrap">🗺️</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">After / Impact</span><div class="date">June 2020</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Global Protests Across All 7 Continents</div>
      <div class="card-body">
        <p class="card-desc">Within two weeks of George Floyd's death, protests had spread worldwide — including the largest BLM demonstrations ever recorded in the UK, Germany, Australia, Brazil, and Japan. The movement became truly global, with each country connecting it to their own histories of racial injustice.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">67% of U.S. adults expressed support for BLM — its all-time high. The UK government commissioned a national report on institutional racism in response.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 7 -->
  <div class="item" data-type="after" onclick="toggle(this)">
    <div class="icon-wrap">📜</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">After / Impact</span><div class="date">June 2020</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Justice in Policing Act Introduced</div>
      <div class="card-body">
        <p class="card-desc">Democrats introduced a sweeping federal bill to ban chokeholds and no-knock warrants, create a national police misconduct registry, mandate body cameras, and reform qualified immunity — the legal shield protecting officers from civil lawsuits.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">Though the federal bill stalled, it set the template for dozens of state and local reform packages passed across the country in the following months.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 8 -->
  <div class="item" data-type="after" onclick="toggle(this)">
    <div class="icon-wrap">📷</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">After / Impact</span><div class="date">2020 – 2021</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Sweeping Police Policy Changes</div>
      <div class="card-body">
        <p class="card-desc">Across the U.S., police departments adopted mandatory body cameras, implicit bias training, and duty-to-intervene laws — requiring officers to stop colleagues from using excessive force. Virginia banned chokeholds and no-knock warrants. California made police disciplinary records public for the first time in decades.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">Mandatory body-worn cameras became standard budget items for departments nationwide. Over 40 states introduced police reform legislation in the year after Floyd's murder.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 9 -->
  <div class="item" data-type="after" onclick="toggle(this)">
    <div class="icon-wrap">🏛️</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">After / Impact</span><div class="date">May 2022</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">Biden Signs Federal Executive Order on Policing</div>
      <div class="card-body">
        <p class="card-desc">President Biden signed an executive order limiting no-knock entries by federal officers and requiring public reports detailing all instances of police use of force or firearms — the first federal-level executive action directly targeting these practices.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">The EO was the most significant federal response to BLM's demands. It was later rescinded by the Trump administration in 2025, showing how policy gains remain contested.</p>
        </div>
      </div>
    </div>
  </div>

  <!-- 10 -->
  <div class="item" data-type="after" onclick="toggle(this)">
    <div class="icon-wrap">💬</div>
    <div class="card">
      <div class="card-head">
        <div><span class="badge">After / Impact</span><div class="date">2020 – Present</div></div>
        <div class="chevron">▼</div>
      </div>
      <div class="card-title">A Permanent Shift in Public Discourse</div>
      <div class="card-body">
        <p class="card-desc">BLM moved terms like "systemic racism," "white privilege," and "intersectionality" from academic papers into everyday conversation. In 2020, 77% of Americans believed the focus on racial inequality marked a fundamental shift in how most people think. Confederate statues were removed across the South. "Black Lives Matter" was painted on the street in front of the White House.</p>
        <div class="impact-box">
          <div class="impact-label">📌 Impact</div>
          <p class="impact-text">Major corporations overhauled diversity and inclusion policies. Mainstream media permanently changed how it covers race and policing. BLM is now recognised as the largest civil rights movement of the 21st century.</p>
        </div>
      </div>
    </div>
  </div>

</div>

<!-- FOOTER -->
<div class="footer">
  Group 4 · What has BLM changed? — Protests &amp; Impact<br>
  Sources: Brookings Institution · Britannica · Pew Research Center · PBS NewsHour · The Mayfield Crier<br><br>
  Click any card to expand details.
</div>

<script>
  function toggle(el) {
    el.classList.toggle('open');
  }
</script>

</body>
</html>
