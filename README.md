[settling_tank_design.html](https://github.com/user-attachments/files/29290139/settling_tank_design.html)
# Settling-Tank-Design<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ถังตกตะกอน — คู่มือการออกแบบ</title>
<style>
:root {
  --bg: #f7f5f0;
  --bg2: #ffffff;
  --text: #1a1917;
  --text2: #5a5854;
  --text3: #9a9690;
  --accent: #1D9E75;
  --accent2: #0F6E56;
  --accent3: #E1F5EE;
  --amber: #BA7517;
  --amber-bg: #FAEEDA;
  --blue: #185FA5;
  --blue-bg: #E6F1FB;
  --coral: #993C1D;
  --coral-bg: #FAECE7;
  --border: rgba(0,0,0,0.10);
  --shadow: 0 1px 3px rgba(0,0,0,0.06);
  --radius: 10px;
  --radius-lg: 16px;
}
@media (prefers-color-scheme: dark) {
  :root {
    --bg: #1c1b19;
    --bg2: #252421;
    --text: #e8e6e0;
    --text2: #a8a49e;
    --text3: #6a6660;
    --accent: #1D9E75;
    --accent2: #5DCAA5;
    --accent3: #04342C;
    --amber: #EF9F27;
    --amber-bg: #412402;
    --blue: #85B7EB;
    --blue-bg: #042C53;
    --coral: #F0997B;
    --coral-bg: #4A1B0C;
    --border: rgba(255,255,255,0.10);
    --shadow: 0 1px 3px rgba(0,0,0,0.3);
  }
}
* { box-sizing: border-box; margin: 0; padding: 0; }
body {
  font-family: 'Segoe UI', -apple-system, sans-serif;
  background: var(--bg);
  color: var(--text);
  font-size: 15px;
  line-height: 1.7;
}
.page { max-width: 960px; margin: 0 auto; padding: 0 20px 80px; }

/* HERO */
.hero {
  background: linear-gradient(135deg, #085041 0%, #0F6E56 40%, #1D9E75 100%);
  color: white;
  padding: 56px 40px 48px;
  border-radius: 0 0 var(--radius-lg) var(--radius-lg);
  margin-bottom: 40px;
  position: relative;
  overflow: hidden;
}
.hero::before {
  content: '';
  position: absolute;
  right: -40px; top: -40px;
  width: 260px; height: 260px;
  border-radius: 50%;
  background: rgba(255,255,255,0.05);
}
.hero-eyebrow {
  font-size: 11px;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.65);
  margin-bottom: 12px;
}
.hero h1 {
  font-size: 32px;
  font-weight: 700;
  line-height: 1.25;
  margin-bottom: 12px;
}
.hero-sub {
  font-size: 15px;
  color: rgba(255,255,255,0.75);
  max-width: 560px;
  margin-bottom: 28px;
}
.hero-sources {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
}
.hero-src {
  background: rgba(255,255,255,0.15);
  border: 1px solid rgba(255,255,255,0.25);
  border-radius: 20px;
  padding: 4px 14px;
  font-size: 12px;
  color: rgba(255,255,255,0.9);
}

/* NAV TABS */
.nav-tabs {
  display: flex;
  gap: 4px;
  margin-bottom: 28px;
  background: var(--bg2);
  border: 0.5px solid var(--border);
  border-radius: var(--radius);
  padding: 4px;
}
.nav-tab {
  flex: 1;
  padding: 9px 12px;
  border-radius: 8px;
  border: none;
  background: transparent;
  color: var(--text2);
  font-size: 13px;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
  text-align: center;
}
.nav-tab.active {
  background: var(--accent);
  color: white;
}
.nav-tab:hover:not(.active) {
  background: var(--bg);
}

/* SECTIONS */
.section { display: none; }
.section.active { display: block; }

/* CARDS */
.card {
  background: var(--bg2);
  border: 0.5px solid var(--border);
  border-radius: var(--radius-lg);
  padding: 24px 28px;
  margin-bottom: 20px;
  box-shadow: var(--shadow);
}
.card-header {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
}
.card-icon {
  width: 36px; height: 36px;
  border-radius: 8px;
  display: flex; align-items: center; justify-content: center;
  font-size: 18px;
  flex-shrink: 0;
}
.ci-green { background: var(--accent3); }
.ci-amber { background: var(--amber-bg); }
.ci-blue  { background: var(--blue-bg); }
.ci-coral { background: var(--coral-bg); }
.card-title { font-size: 16px; font-weight: 600; color: var(--text); }
.card-source { font-size: 11px; color: var(--text3); margin-top: 2px; }

/* PRINCIPLES GRID */
.principle-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px,1fr)); gap: 16px; margin-bottom: 20px; }
.principle-item {
  background: var(--bg);
  border: 0.5px solid var(--border);
  border-radius: var(--radius);
  padding: 16px 18px;
}
.principle-label { font-size: 11px; font-weight: 700; letter-spacing: 0.08em; text-transform: uppercase; color: var(--text3); margin-bottom: 6px; }
.principle-value { font-size: 15px; font-weight: 600; color: var(--text); }
.principle-desc { font-size: 13px; color: var(--text2); margin-top: 4px; }

/* FORMULA BOX */
.formula-box {
  background: var(--blue-bg);
  border: 0.5px solid var(--blue);
  border-radius: var(--radius);
  padding: 16px 20px;
  margin: 14px 0;
  font-family: 'Courier New', monospace;
  font-size: 15px;
  color: var(--blue);
  font-weight: 600;
}
.formula-vars { margin-top: 10px; }
.fvar { font-size: 13px; color: var(--text2); font-family: inherit; }
.fvar strong { color: var(--blue); }

/* STEP LIST */
.steps { counter-reset: step; }
.step-item {
  display: flex;
  gap: 16px;
  margin-bottom: 20px;
  padding-bottom: 20px;
  border-bottom: 0.5px solid var(--border);
}
.step-item:last-child { border-bottom: none; margin-bottom: 0; padding-bottom: 0; }
.step-num {
  width: 28px; height: 28px;
  border-radius: 50%;
  background: var(--accent);
  color: white;
  font-size: 12px;
  font-weight: 700;
  display: flex; align-items: center; justify-content: center;
  flex-shrink: 0;
  margin-top: 2px;
}
.step-body { flex: 1; }
.step-title { font-weight: 600; font-size: 14px; margin-bottom: 6px; }
.step-desc { font-size: 13px; color: var(--text2); line-height: 1.6; }

/* CONSTRAINT TABLE */
.table-wrap { overflow-x: auto; margin: 14px 0; }
table { width: 100%; border-collapse: collapse; font-size: 13px; }
th { background: var(--bg); color: var(--text2); font-weight: 600; font-size: 11px; text-transform: uppercase; letter-spacing: 0.06em; padding: 9px 14px; text-align: left; border-bottom: 0.5px solid var(--border); }
td { padding: 10px 14px; border-bottom: 0.5px solid var(--border); color: var(--text); vertical-align: top; }
tr:last-child td { border-bottom: none; }
td.highlight { font-weight: 600; color: var(--accent2); }

/* WARNING / INFO BOXES */
.note-box {
  border-radius: var(--radius);
  padding: 14px 18px;
  font-size: 13px;
  line-height: 1.6;
  margin: 14px 0;
  border-left: 3px solid;
}
.note-warn { background: var(--amber-bg); border-color: var(--amber); color: var(--text); }
.note-info { background: var(--blue-bg); border-color: var(--blue); color: var(--text); }
.note-green { background: var(--accent3); border-color: var(--accent); color: var(--text); }
.note-coral { background: var(--coral-bg); border-color: var(--coral); color: var(--text); }
.note-title { font-weight: 700; margin-bottom: 4px; }

/* VESSEL SVG */
.vessel-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; margin: 16px 0; }
.vessel-card {
  background: var(--bg);
  border: 0.5px solid var(--border);
  border-radius: var(--radius);
  padding: 20px;
  text-align: center;
}
.vessel-card h4 { font-size: 14px; font-weight: 600; margin-bottom: 12px; color: var(--text); }
svg.vessel { width: 100%; max-width: 200px; height: auto; display: block; margin: 0 auto; }

/* CALCULATOR */
.calc-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
.calc-group { display: flex; flex-direction: column; gap: 6px; }
.calc-label { font-size: 12px; font-weight: 600; color: var(--text2); }
.calc-input {
  padding: 8px 12px;
  border: 0.5px solid var(--border);
  border-radius: 8px;
  background: var(--bg);
  color: var(--text);
  font-size: 14px;
  outline: none;
  transition: border-color 0.2s;
}
.calc-input:focus { border-color: var(--accent); }
.calc-unit { font-size: 11px; color: var(--text3); }
.calc-btn {
  margin-top: 20px;
  padding: 11px 24px;
  background: var(--accent);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
  width: 100%;
}
.calc-btn:hover { background: var(--accent2); }
.result-panel {
  margin-top: 20px;
  background: var(--accent3);
  border: 0.5px solid var(--accent);
  border-radius: var(--radius);
  padding: 18px 20px;
  display: none;
}
.result-panel.show { display: block; }
.result-grid { display: grid; grid-template-columns: repeat(3,1fr); gap: 12px; margin-top: 10px; }
.result-item { text-align: center; }
.result-val { font-size: 22px; font-weight: 700; color: var(--accent2); }
.result-lbl { font-size: 11px; color: var(--text2); }

/* PHASE INVERSION BOX */
.pi-wrap {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
  margin: 14px 0;
}
.pi-card {
  border-radius: var(--radius);
  padding: 16px;
  font-size: 13px;
}
.pi-std { background: var(--blue-bg); border: 0.5px solid var(--blue); }
.pi-cpo { background: var(--coral-bg); border: 0.5px solid var(--coral); }
.pi-head { font-weight: 700; font-size: 13px; margin-bottom: 8px; }
.pi-std .pi-head { color: var(--blue); }
.pi-cpo .pi-head { color: var(--coral); }

/* CHART PLACEHOLDER */
.chart-container {
  position: relative;
  width: 100%;
  padding-bottom: 280px;
  overflow: hidden;
}
.chart-container svg { position: absolute; top: 0; left: 0; width: 100%; height: 100%; }

/* RESPONSIVE */
@media (max-width: 600px) {
  .hero { padding: 36px 20px 32px; }
  .hero h1 { font-size: 24px; }
  .nav-tab { font-size: 11px; padding: 8px 6px; }
  .calc-grid { grid-template-columns: 1fr; }
  .vessel-wrap { grid-template-columns: 1fr; }
  .pi-wrap { grid-template-columns: 1fr; }
  .result-grid { grid-template-columns: 1fr 1fr; }
}

/* BADGE */
.badge {
  display: inline-block;
  padding: 2px 10px;
  border-radius: 12px;
  font-size: 11px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.06em;
}
.badge-green { background: var(--accent3); color: var(--accent2); }
.badge-amber { background: var(--amber-bg); color: var(--amber); }
.badge-blue  { background: var(--blue-bg);  color: var(--blue); }
.badge-coral { background: var(--coral-bg); color: var(--coral); }

hr.divider { border: none; border-top: 0.5px solid var(--border); margin: 20px 0; }

p { margin-bottom: 10px; color: var(--text2); font-size: 14px; }
p:last-child { margin-bottom: 0; }
</style>
</head>
<body>
<div class="page">

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow">CPO Degumming Process · Water-in-Oil System</div>
  <h1>คู่มือออกแบบถังตกตะกอน<br>Settling Tank Design Guide</h1>
  <p class="hero-sub">สรุปหลักการ สูตรคำนวณ และข้อแตกต่างสำหรับระบบ Water Degumming ของ CPO จากหนังสืออ้างอิง 3 เล่ม</p>
  <div class="hero-sources">
    <span class="hero-src">📘 API Publication 421</span>
    <span class="hero-src">📗 Edible Oil Processing</span>
    <span class="hero-src">📙 Equipment Design Handbook Ch.5</span>
  </div>
</div>

<!-- NAV TABS -->
<div class="nav-tabs">
  <button class="nav-tab active" onclick="showSection('principles')">หลักการ</button>
  <button class="nav-tab" onclick="showSection('api421')">API 421</button>
  <button class="nav-tab" onclick="showSection('edibleoil')">Edible Oil</button>
  <button class="nav-tab" onclick="showSection('calc')">คำนวณ</button>
  <button class="nav-tab" onclick="showSection('adapt')">CPO Adapt</button>
</div>

<!-- ================== TAB 1: PRINCIPLES ================== -->
<div id="principles" class="section active">

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-green">🔬</div>
      <div>
        <div class="card-title">หลักการตกตะกอนด้วยแรงโน้มถ่วง</div>
        <div class="card-source">ที่มา: API 421 §1.3, Appendix A · Equipment Design Handbook §5</div>
      </div>
    </div>
    <p>การแยกสองเฟสของเหลวด้วยแรงโน้มถ่วงเกิดจากความแตกต่างของความหนาแน่น (Δρ) หยดเล็กๆ จะลอยขึ้นหรือจมลงตามกฎของ Stokes เมื่อ Reynolds number ของอนุภาค ≤ 0.5</p>
    <div class="formula-box">
      V<sub>t</sub> = g · D<sub>p</sub>² · (ρ<sub>L</sub> − ρ<sub>d</sub>) / (18μ)
      <div class="formula-vars">
        <div class="fvar"><strong>V<sub>t</sub></strong> = ความเร็วตกตะกอน (m/s หรือ ft/s)</div>
        <div class="fvar"><strong>g</strong> = ความเร่งโน้มถ่วง (9.81 m/s²)</div>
        <div class="fvar"><strong>D<sub>p</sub></strong> = เส้นผ่านศูนย์กลางหยด (m)</div>
        <div class="fvar"><strong>ρ<sub>L</sub></strong> = ความหนาแน่นเฟสต่อเนื่อง (continuous phase)</div>
        <div class="fvar"><strong>ρ<sub>d</sub></strong> = ความหนาแน่นเฟสกระจาย (dispersed phase)</div>
        <div class="fvar"><strong>μ</strong> = ความหนืดของเฟสต่อเนื่อง (Pa·s)</div>
      </div>
    </div>
    <div class="note-box note-info">
      <div class="note-title">💡 สองปัจจัยสำคัญจาก API 421</div>
      ① ยิ่ง Δρ มาก → หยดแยกได้เร็ว · ② ยิ่งอุณหภูมิสูง → μ ต่ำ → แยกได้เร็ว ทั้งสองปัจจัยนี้ส่งผลต่อ sizing โดยตรง
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-amber">⚖️</div>
      <div>
        <div class="card-title">Surface Overflow Rate — หัวใจของ Sizing</div>
        <div class="card-source">ที่มา: API 421 §2.1.4.6</div>
      </div>
    </div>
    <p>ขนาดพื้นที่ผิวของถัง (Horizontal Area) ถูกกำหนดจาก Surface Loading Rate ไม่ใช่จากความลึก ซึ่งต่างจาก vapor-liquid separator ที่ใช้ velocity approach</p>
    <div class="formula-box">
      A<sub>H</sub> = F · (Q<sub>m</sub> / V<sub>t</sub>)
      <div class="formula-vars">
        <div class="fvar"><strong>A<sub>H</sub></strong> = พื้นที่ผิวแนวนอนขั้นต่ำ (ft²)</div>
        <div class="fvar"><strong>F</strong> = ค่าปรับ Turbulence & Short-Circuiting (1.28–1.74 ขึ้นกับ v<sub>H</sub>/V<sub>t</sub>)</div>
        <div class="fvar"><strong>Q<sub>m</sub></strong> = อัตราการไหล (ft³/min)</div>
        <div class="fvar"><strong>V<sub>t</sub></strong> = ความเร็วตกตะกอน (ft/min)</div>
      </div>
    </div>
    <div class="note-box note-warn">
      <div class="note-title">⚠️ ข้อแตกต่างสำคัญ</div>
      ในถัง Ideal ขนาด A<sub>H</sub> = Q/V<sub>t</sub> ไม่ขึ้นกับความลึก แต่ในความเป็นจริงต้องคูณ F เพื่อชดเชย turbulence และ short-circuiting ซึ่งค่า F อ่านจาก Chart (Figure 4 ใน API 421)
    </div>

    <!-- F Factor Chart (simplified visual) -->
    <div style="margin: 16px 0;">
      <div class="table-wrap">
        <table>
          <thead><tr><th>v<sub>H</sub>/V<sub>t</sub></th><th>Turbulence Factor (F<sub>t</sub>)</th><th>F = 1.2 × F<sub>t</sub></th></tr></thead>
          <tbody>
            <tr><td>20</td><td>1.45</td><td class="highlight">1.74</td></tr>
            <tr><td>15</td><td>1.37</td><td class="highlight">1.64</td></tr>
            <tr><td>10</td><td>1.27</td><td class="highlight">1.52</td></tr>
            <tr><td>6</td><td>1.14</td><td class="highlight">1.37</td></tr>
            <tr><td>3</td><td>1.07</td><td class="highlight">1.28</td></tr>
          </tbody>
        </table>
      </div>
      <p style="font-size:12px; margin-top:6px;">* ค่า F มาจาก Short-Circuiting Factor 1.21 × Turbulence Factor — ที่มา: API 421 Figure 4</p>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-blue">📐</div>
      <div>
        <div class="card-title">ประเภทถังและการเปรียบเทียบ</div>
        <div class="card-source">ที่มา: Edible Oil Processing §3.10.5 · API 421 §2.2</div>
      </div>
    </div>
    <div class="vessel-wrap">
      <!-- Horizontal tank SVG -->
      <div class="vessel-card">
        <h4>🔁 Horizontal Tank (แนวนอน)</h4>
        <svg class="vessel" viewBox="0 0 200 130" xmlns="http://www.w3.org/2000/svg">
          <!-- tank body -->
          <rect x="15" y="35" width="170" height="60" rx="10" fill="#E1F5EE" stroke="#1D9E75" stroke-width="1.5"/>
          <!-- oil zone (top) -->
          <rect x="15" y="35" width="170" height="28" rx="10" fill="#9FE1CB" opacity="0.5"/>
          <text x="100" y="54" text-anchor="middle" font-size="9" fill="#085041" font-weight="600">CPO (เบา)</text>
          <!-- sludge zone (bottom) -->
          <rect x="15" y="79" width="170" height="16" rx="0" fill="#BA7517" opacity="0.3"/>
          <text x="100" y="90" text-anchor="middle" font-size="9" fill="#412402" font-weight="600">Sludge Water (หนัก)</text>
          <!-- interface line -->
          <line x1="15" y1="79" x2="185" y2="79" stroke="#1D9E75" stroke-width="0.8" stroke-dasharray="3,2"/>
          <!-- inlet arrow -->
          <line x1="15" y1="65" x2="0" y2="65" stroke="#185FA5" stroke-width="1.5" marker-end="url(#arrowB)"/>
          <text x="0" y="61" font-size="8" fill="#185FA5">In</text>
          <!-- outlet arrows -->
          <line x1="185" y1="50" x2="200" y2="50" stroke="#0F6E56" stroke-width="1.5" marker-end="url(#arrowG)"/>
          <text x="188" y="46" font-size="8" fill="#0F6E56">CPO</text>
          <line x1="185" y1="92" x2="200" y2="92" stroke="#854F0B" stroke-width="1.5" marker-end="url(#arrowA)"/>
          <text x="185" y="108" font-size="8" fill="#854F0B">SLW</text>
          <!-- dimensions -->
          <line x1="15" y1="115" x2="185" y2="115" stroke="#9a9690" stroke-width="0.8"/>
          <text x="100" y="125" text-anchor="middle" font-size="8" fill="#9a9690">L (ความยาว)</text>
          <line x1="195" y1="35" x2="195" y2="95" stroke="#9a9690" stroke-width="0.8"/>
          <text x="185" y="68" font-size="8" fill="#9a9690" transform="rotate(-90, 197, 65)">d</text>
          <defs>
            <marker id="arrowB" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5" markerHeight="5" orient="auto"><path d="M1 1L6 4L1 7" fill="none" stroke="#185FA5" stroke-width="1.5"/></marker>
            <marker id="arrowG" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5" markerHeight="5" orient="auto"><path d="M1 1L6 4L1 7" fill="none" stroke="#0F6E56" stroke-width="1.5"/></marker>
            <marker id="arrowA" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5" markerHeight="5" orient="auto"><path d="M1 1L6 4L1 7" fill="none" stroke="#854F0B" stroke-width="1.5"/></marker>
          </defs>
        </svg>
        <div style="font-size:12px; color:var(--text2); margin-top:10px; text-align:left;">
          <b>✅ เหมาะสำหรับ CPO Degumming</b><br>
          พื้นที่ผิว A<sub>H</sub> มาก · ควบคุม Residence Time ได้ดี · รองรับของเหลว load สูง
        </div>
      </div>
      <!-- Vertical tank SVG -->
      <div class="vessel-card">
        <h4>⬆️ Vertical Tank (แนวตั้ง)</h4>
        <svg class="vessel" viewBox="0 0 200 130" xmlns="http://www.w3.org/2000/svg">
          <!-- tank body -->
          <rect x="55" y="10" width="90" height="110" rx="10" fill="#E6F1FB" stroke="#185FA5" stroke-width="1.5"/>
          <!-- oil zone (top) -->
          <rect x="55" y="10" width="90" height="45" rx="10" fill="#B5D4F4" opacity="0.5"/>
          <text x="100" y="37" text-anchor="middle" font-size="9" fill="#042C53" font-weight="600">CPO</text>
          <!-- sludge zone (bottom) -->
          <rect x="55" y="98" width="90" height="22" rx="0" fill="#BA7517" opacity="0.3"/>
          <text x="100" y="112" text-anchor="middle" font-size="9" fill="#412402">Sludge</text>
          <!-- interface -->
          <line x1="55" y1="80" x2="145" y2="80" stroke="#185FA5" stroke-width="0.8" stroke-dasharray="3,2"/>
          <!-- feed (side) -->
          <line x1="40" y1="65" x2="55" y2="65" stroke="#185FA5" stroke-width="1.5" marker-end="url(#arrowBv)"/>
          <text x="10" y="63" font-size="8" fill="#185FA5">Feed</text>
          <!-- top outlet -->
          <line x1="100" y1="10" x2="100" y2="0" stroke="#0F6E56" stroke-width="1.5" marker-end="url(#arrowGv)"/>
          <text x="105" y="8" font-size="8" fill="#0F6E56">CPO</text>
          <!-- bottom drain -->
          <line x1="100" y1="120" x2="100" y2="130" stroke="#854F0B" stroke-width="1.5" marker-end="url(#arrowAv)"/>
          <text x="105" y="128" font-size="8" fill="#854F0B">SLW</text>
          <defs>
            <marker id="arrowBv" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5" markerHeight="5" orient="auto"><path d="M1 1L6 4L1 7" fill="none" stroke="#185FA5" stroke-width="1.5"/></marker>
            <marker id="arrowGv" viewBox="0 0 8 8" refX="1" refY="4" markerWidth="5" markerHeight="5" orient="auto-start-reverse"><path d="M7 1L2 4L7 7" fill="none" stroke="#0F6E56" stroke-width="1.5"/></marker>
            <marker id="arrowAv" viewBox="0 0 8 8" refX="6" refY="4" markerWidth="5" markerHeight="5" orient="auto"><path d="M1 1L6 4L1 7" fill="none" stroke="#854F0B" stroke-width="1.5"/></marker>
          </defs>
        </svg>
        <div style="font-size:12px; color:var(--text2); margin-top:10px; text-align:left;">
          <b>⚠️ ใช้ได้แต่ต้องระวัง</b><br>
          Footprint เล็ก · แต่ A<sub>H</sub> จำกัด · Surge Volume น้อย · ทำความสะอาดยาก
        </div>
      </div>
    </div>
  </div>

</div><!-- end #principles -->

<!-- ================== TAB 2: API 421 ================== -->
<div id="api421" class="section">

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-blue">📘</div>
      <div>
        <div class="card-title">API Publication 421 — ขั้นตอนการออกแบบ 7 ขั้น</div>
        <div class="card-source">API 421 §2.1.4 Step-by-Step Design Calculations (ออกแบบสำหรับ oil-in-water)</div>
      </div>
    </div>
    <div class="note-box note-coral">
      <div class="note-title">⚠️ ข้อสังเกตสำคัญสำหรับ CPO Degumming</div>
      API 421 ออกแบบมาสำหรับ <b>Oil-in-Water</b> (น้ำเป็น Continuous Phase) แต่ระบบ degumming CPO เป็น <b>Water-in-Oil</b> (น้ำมันเป็น Continuous Phase หยดน้ำจม) — ต้องปรับทิศทาง (Sludge ตกลงไม่ใช่ลอยขึ้น) และต้องปรับค่า Density อ้างอิง
    </div>

    <div class="steps">
      <div class="step-item">
        <div class="step-num">1</div>
        <div class="step-body">
          <div class="step-title">คำนวณ Rise Rate (V<sub>t</sub>) ของหยด</div>
          <div class="step-desc">ใช้สมการ Stokes' Law (สำหรับ D = 0.015 cm = 150 micron ซึ่ง API กำหนดเป็นค่า design standard):</div>
          <div class="formula-box" style="font-size:13px; margin:8px 0;">
            V<sub>t</sub> = 0.0241 · (S<sub>w</sub> − S<sub>o</sub>) / μ &nbsp;&nbsp;[ft/min]
            <div class="formula-vars">
              <div class="fvar"><strong>S<sub>w</sub></strong> = SG ของ continuous phase · <strong>S<sub>o</sub></strong> = SG ของ dispersed phase · <strong>μ</strong> = viscosity (poise)</div>
            </div>
          </div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">2</div>
        <div class="step-body">
          <div class="step-title">กำหนด Horizontal Velocity (v<sub>H</sub>)</div>
          <div class="step-desc">เลือกค่าที่น้อยกว่าระหว่าง: <b>15 × V<sub>t</sub></b> หรือ <b>3 ft/min</b> เพื่อป้องกัน turbulence รบกวนการแยก</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">3</div>
        <div class="step-body">
          <div class="step-title">คำนวณ Cross-sectional Area (A<sub>c</sub>)</div>
          <div class="step-desc">A<sub>c</sub> = Q<sub>m</sub> / v<sub>H</sub> &nbsp;[ft²] — พื้นที่หน้าตัดขั้นต่ำตลอดความยาวถัง</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">4</div>
        <div class="step-body">
          <div class="step-title">กำหนดจำนวน Channel (n) และ Width (B)</div>
          <div class="step-desc">n = A<sub>c</sub> / 160 (ปัดขึ้นเป็นเลขจำนวนเต็ม, ขั้นต่ำ 2 channel) · กว้าง B = 6–20 ft per channel</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">5</div>
        <div class="step-body">
          <div class="step-title">คำนวณ Depth (d)</div>
          <div class="step-desc">d = A<sub>c</sub> / (B × n) — ต้องอยู่ในช่วง <b>3–8 ft</b> และ d/B = <b>0.3–0.5</b></div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">6</div>
        <div class="step-body">
          <div class="step-title">คำนวณ Length (L)</div>
          <div class="step-desc">L = F · (v<sub>H</sub> / V<sub>t</sub>) · d &nbsp; — ตรวจสอบ L/B ≥ 5</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">7</div>
        <div class="step-body">
          <div class="step-title">ตรวจสอบ Horizontal Area (A<sub>H</sub>)</div>
          <div class="step-desc">A<sub>H</sub> = F · (Q<sub>m</sub> / V<sub>t</sub>) — เพื่อยืนยันว่า sizing สอดคล้องกัน และเป็น check สุดท้าย</div>
        </div>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-amber">📏</div>
      <div>
        <div class="card-title">Design Constraints จาก API 421</div>
        <div class="card-source">API 421 §2.1.4.1 General + §2.1.4.4</div>
      </div>
    </div>
    <div class="table-wrap">
      <table>
        <thead><tr><th>พารามิเตอร์</th><th>ขีดจำกัด (API 421)</th><th>เหตุผล</th></tr></thead>
        <tbody>
          <tr><td>Horizontal velocity v<sub>H</sub></td><td class="highlight">≤ 3 ft/min และ ≤ 15V<sub>t</sub></td><td>ป้องกัน turbulence</td></tr>
          <tr><td>ความลึก d</td><td class="highlight">3–8 ft (0.9–2.4 m)</td><td>ป้องกัน turbulence จาก scraper</td></tr>
          <tr><td>อัตราส่วน d/B</td><td class="highlight">0.3–0.5</td><td>Flow distribution สม่ำเสมอ</td></tr>
          <tr><td>ความกว้าง B</td><td class="highlight">6–20 ft</td><td>รองรับ scraper มาตรฐาน</td></tr>
          <tr><td>L/B ratio</td><td class="highlight">≥ 5</td><td>ลด inlet/outlet turbulence effect</td></tr>
          <tr><td>จำนวน channel</td><td class="highlight">≥ 2</td><td>ให้บำรุงรักษาได้โดยไม่หยุด</td></tr>
          <tr><td>Droplet size design</td><td class="highlight">150 micron (0.015 cm)</td><td>ค่า conservative จากการทดสอบ API</td></tr>
        </tbody>
      </table>
    </div>
    <div class="note-box note-info" style="margin-top:14px;">
      <div class="note-title">📊 ตัวอย่าง API 421 Design Example (§2.1.5)</div>
      Q = 4,490 gpm · T = 105°F · S<sub>w</sub> = 0.992 · μ = 0.0065 poise · S<sub>o</sub> = 0.92<br>
      → V<sub>t</sub> = 0.0241 × (0.992−0.92)/0.0065 = <b>0.267 ft/min</b><br>
      → v<sub>H</sub> = min(15×0.267, 3) = min(4.0, 3) = <b>3 ft/min</b><br>
      → A<sub>c</sub> = 600/3 = <b>200 ft²</b> · n = 200/160 → <b>2 channels</b><br>
      → B=18 ft, d=6 ft (d/B=0.33 ✓) → F=1.55 → <b>L = 105 ft</b>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-green">🔧</div>
      <div>
        <div class="card-title">Construction Details ที่สำคัญ (API 421 §2.2)</div>
      </div>
    </div>
    <div class="table-wrap">
      <table>
        <thead><tr><th>ส่วนประกอบ</th><th>หน้าที่</th><th>ข้อสังเกต</th></tr></thead>
        <tbody>
          <tr><td>Preseparator Flume</td><td>ลดความเร็ว + แยก oil เบื้องต้น</td><td>ลด turbulence ก่อนเข้า channel</td></tr>
          <tr><td>Forebay + Baffle</td><td>กระจายน้ำให้สม่ำเสมอ</td><td>Reaction-Jet Inlet ช่วยได้</td></tr>
          <tr><td>Oil Skimmer</td><td>รวบรวม oil layer ด้านบน</td><td>หลายแบบ: Traveling Bridge, Rotary Drum, Floating</td></tr>
          <tr><td>Sludge/Flight Scraper</td><td>ขูดตะกอนที่ก้น</td><td>เป็นเหตุให้ต้องมี d ≥ 3 ft</td></tr>
          <tr><td>Cover</td><td>กัน VOC / rain</td><td>ต้องระวัง pontoon submergence</td></tr>
        </tbody>
      </table>
    </div>
  </div>

</div><!-- end #api421 -->

<!-- ================== TAB 3: EDIBLE OIL ================== -->
<div id="edibleoil" class="section">

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-green">📗</div>
      <div>
        <div class="card-title">Edible Oil Processing — CPO Clarification</div>
        <div class="card-source">Edible Oil Processing §3.10.5 Crude Oil Clarification</div>
      </div>
    </div>
    <p>กระบวนการ Clarification ใน Palm Oil Mill แยกน้ำมัน น้ำ และสิ่งเจือปนออกจากกัน โดยอาศัยความแตกต่างของ Specific Gravity ในถังตกตะกอนแบบต่อเนื่อง (Continuous Decantation Tank)</p>

    <div class="principle-grid">
      <div class="principle-item">
        <div class="principle-label">รูปแบบถัง</div>
        <div class="principle-value">Rectangular Horizontal</div>
        <div class="principle-desc">หรือ Cylindrical Vertical — แต่ horizontal นิยมกว่า</div>
      </div>
      <div class="principle-item">
        <div class="principle-label">อุณหภูมิ Process</div>
        <div class="principle-value">90°C</div>
        <div class="principle-desc">ลด viscosity ของน้ำมัน → แยกได้เร็วขึ้น</div>
      </div>
      <div class="principle-item">
        <div class="principle-label">ทางเลือกเพิ่มเติม</div>
        <div class="principle-value">3-Phase Decanter</div>
        <div class="principle-desc">ลด effluent + maintenance cost</div>
      </div>
      <div class="principle-item">
        <div class="principle-label">Sludge Treatment</div>
        <div class="principle-value">Centrifuge</div>
        <div class="principle-desc">บาง mill ใช้ centrifuge แทน settling</div>
      </div>
    </div>

    <div class="note-box note-green">
      <div class="note-title">🌴 บริบทของ CPO Degumming (Water Degumming)</div>
      Water Degumming เพิ่มน้ำ (DI water ~1–3% by weight) ลงใน CPO แล้ว hydrate phosphatides → ทำให้ Gums (sludge water) แยกเฟสออกมาและตกตะกอน ต่างจากการ Clarify หลัง press ตรงที่ load ของ dispersed phase (SLW) น้อยกว่า และ droplet size อาจเล็กกว่า → ต้องใช้ Lab settling test กำหนด residence time ก่อน sizing
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-amber">🏭</div>
      <div>
        <div class="card-title">Storage Tank Design Rules จาก Edible Oil Processing</div>
        <div class="card-source">Edible Oil Processing §10.5 Tank Park Design Rules</div>
      </div>
    </div>
    <div class="steps">
      <div class="step-item">
        <div class="step-num" style="background:var(--amber);">●</div>
        <div class="step-body">
          <div class="step-title">วัสดุท่อและถัง</div>
          <div class="step-desc">Mild steel ยอมรับได้สำหรับ crude oil · แต่ <b>Stainless Steel แนะนำ</b> (SS 316/316L สำหรับ food-grade) — สอดคล้องกับ decision ของโปรเจกต์แล้ว</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num" style="background:var(--amber);">●</div>
        <div class="step-body">
          <div class="step-title">การ Insulation และ Heating</div>
          <div class="step-desc">ท่อที่จะแข็งตัวที่อุณหภูมิห้อง <b>ต้อง insulate และ heat trace</b> · อุณหภูมิท่อ ≤ 110°C เพื่อไม่ให้น้ำมันเสื่อมคุณภาพ — เช่นเดียวกับ decision ปัจจุบัน</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num" style="background:var(--amber);">●</div>
        <div class="step-body">
          <div class="step-title">การกวน (Agitation) ใน Storage</div>
          <div class="step-desc">ถังเก็บ crude oil ควรมี Side-Entry Stirrer เพื่อป้องกัน impurities ตกตะกอน — แต่ <b>ไม่ใช้ใน settling tank</b> ที่ต้องการให้ตกตะกอน</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num" style="background:var(--amber);">●</div>
        <div class="step-body">
          <div class="step-title">การ Fill จากด้านล่าง</div>
          <div class="step-desc">เติม CPO จาก bottom หรือ dip pipe เพื่อหลีกเลี่ยง aeration และการฟอง → สำคัญมากสำหรับ settling tank เพื่อไม่ให้เกิด turbulence</div>
        </div>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-coral">🧪</div>
      <div>
        <div class="card-title">Lab Test ที่จำเป็นก่อน Sizing</div>
        <div class="card-source">ตามหลักการของ Edible Oil Processing + API 421</div>
      </div>
    </div>
    <div class="table-wrap">
      <table>
        <thead><tr><th>ข้อมูลที่ต้องการ</th><th>วิธีการ</th><th>นำไปใช้ใน</th></tr></thead>
        <tbody>
          <tr><td>Settling time ที่ 90°C</td><td>Batch settling test ในห้อง Lab</td><td>Residence Time → Volume ถัง</td></tr>
          <tr><td>ความหนาแน่น Sludge Water (ρ<sub>SLW</sub>)</td><td>Pycnometer ที่ 90°C</td><td>Δρ → V<sub>t</sub> ตาม Stokes</td></tr>
          <tr><td>% DI Water ที่เหมาะสม</td><td>Lab optimization (titration)</td><td>Flow rate of SLW</td></tr>
          <tr><td>Droplet size distribution</td><td>Microscopy / Particle sizer</td><td>V<sub>t</sub> → A<sub>H</sub></td></tr>
          <tr><td>Viscosity CPO ที่ 90°C</td><td>Viscometer</td><td>μ ใน Stokes equation</td></tr>
        </tbody>
      </table>
    </div>
    <div class="note-box note-warn" style="margin-top:14px;">
      <div class="note-title">🔬 HOLD — รอผล Lab</div>
      การ size ถังตกตะกอนยังอยู่ใน HOLD จนกว่าจะได้ผล Lab settling test, % DI water ที่เหมาะสม, และ density ของ Sludge Water ที่ 90°C
    </div>
  </div>

</div><!-- end #edibleoil -->

<!-- ================== TAB 4: CALCULATOR ================== -->
<div id="calc" class="section">

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-green">🧮</div>
      <div>
        <div class="card-title">Settling Velocity Calculator (Stokes' Law)</div>
        <div class="card-source">ตาม API 421 Eq. 1 + Equipment Design Handbook Eq. 5-5</div>
      </div>
    </div>
    <p>ป้อนคุณสมบัติของระบบเพื่อคำนวณ Terminal Settling Velocity ของหยดน้ำ (dispersed phase) ใน CPO (continuous phase)</p>

    <div class="calc-grid">
      <div class="calc-group">
        <label class="calc-label">ความหนาแน่น CPO (ρ<sub>CPO</sub>)</label>
        <input type="number" class="calc-input" id="rho_cpo" value="889" step="0.1">
        <span class="calc-unit">kg/m³ ที่ 90°C (ประมาณ)</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">ความหนาแน่น Sludge Water (ρ<sub>SLW</sub>)</label>
        <input type="number" class="calc-input" id="rho_slw" value="1050" step="0.1">
        <span class="calc-unit">kg/m³ (รอผล Lab — ใส่ค่าประมาณก่อน)</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">Viscosity CPO (μ) ที่ 90°C</label>
        <input type="number" class="calc-input" id="mu_cpo" value="0.018" step="0.001">
        <span class="calc-unit">Pa·s (mPa·s ÷ 1000)</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">Droplet Diameter (D<sub>p</sub>)</label>
        <input type="number" class="calc-input" id="dp" value="150" step="10">
        <span class="calc-unit">micron (μm) — API 421 ใช้ 150 μm เป็น design basis</span>
      </div>
    </div>
    <button class="calc-btn" onclick="calcStokes()">⚙️ คำนวณ Settling Velocity</button>

    <div class="result-panel" id="result-stokes">
      <div style="font-size:13px; font-weight:700; color:var(--accent2); margin-bottom:10px;">ผลการคำนวณ</div>
      <div class="result-grid">
        <div class="result-item">
          <div class="result-val" id="res-vt-mms">—</div>
          <div class="result-lbl">V<sub>t</sub> (mm/s)</div>
        </div>
        <div class="result-item">
          <div class="result-val" id="res-vt-mmin">—</div>
          <div class="result-lbl">V<sub>t</sub> (m/min)</div>
        </div>
        <div class="result-item">
          <div class="result-val" id="res-re">—</div>
          <div class="result-lbl">Re<sub>p</sub></div>
        </div>
      </div>
      <div class="note-box note-green" style="margin-top:14px;" id="res-check"></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-blue">📐</div>
      <div>
        <div class="card-title">Settling Tank Sizing (Horizontal Tank)</div>
        <div class="card-source">ดัดแปลงจาก API 421 §2.1.4 สำหรับ Liquid-Liquid System</div>
      </div>
    </div>
    <p>คำนวณขนาดถังเบื้องต้น โดยใช้ค่า V<sub>t</sub> จากด้านบน</p>
    <div class="calc-grid">
      <div class="calc-group">
        <label class="calc-label">Flow Rate CPO (Q)</label>
        <input type="number" class="calc-input" id="q_cpo" value="10" step="0.5">
        <span class="calc-unit">m³/hr</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">Residence Time (t<sub>r</sub>) — จาก Lab Test</label>
        <input type="number" class="calc-input" id="t_res" value="30" step="5">
        <span class="calc-unit">นาที (ป้อนค่าจาก Lab settling test)</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">Safety Factor</label>
        <input type="number" class="calc-input" id="sf" value="1.5" step="0.1">
        <span class="calc-unit">— (ทั่วไป 1.3–2.0)</span>
      </div>
      <div class="calc-group">
        <label class="calc-label">ความสูงของเหลว (d)</label>
        <input type="number" class="calc-input" id="depth" value="1.5" step="0.1">
        <span class="calc-unit">m (API 421: 0.9–2.4 m)</span>
      </div>
    </div>
    <button class="calc-btn" onclick="calcTank()">📏 คำนวณขนาดถัง</button>

    <div class="result-panel" id="result-tank">
      <div style="font-size:13px; font-weight:700; color:var(--accent2); margin-bottom:10px;">ขนาดถังเบื้องต้น</div>
      <div class="result-grid" style="grid-template-columns: repeat(4,1fr);">
        <div class="result-item">
          <div class="result-val" id="res-vol">—</div>
          <div class="result-lbl">Volume (m³)</div>
        </div>
        <div class="result-item">
          <div class="result-val" id="res-ah">—</div>
          <div class="result-lbl">A<sub>H</sub> min (m²)</div>
        </div>
        <div class="result-item">
          <div class="result-val" id="res-l">—</div>
          <div class="result-lbl">L est. (m)</div>
        </div>
        <div class="result-item">
          <div class="result-val" id="res-w">—</div>
          <div class="result-lbl">W est. (m)</div>
        </div>
      </div>
      <div class="note-box note-warn" style="margin-top:14px;" id="res-tank-note"></div>
    </div>
  </div>

</div><!-- end #calc -->

<!-- ================== TAB 5: CPO ADAPTATION ================== -->
<div id="adapt" class="section">

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-coral">🔄</div>
      <div>
        <div class="card-title">Phase Inversion — Oil-in-Water vs Water-in-Oil</div>
        <div class="card-source">ข้อสรุปจากการวิเคราะห์ API 421 สำหรับ CPO Degumming</div>
      </div>
    </div>
    <p>ระบบ CPO Degumming มีทิศทางตรงข้ามกับ API 421 ซึ่งสำคัญมากสำหรับการออกแบบ:</p>
    <div class="pi-wrap">
      <div class="pi-card pi-std">
        <div class="pi-head">📘 API 421 — Oil-in-Water</div>
        <b>Continuous Phase:</b> Water (น้ำ)<br>
        <b>Dispersed Phase:</b> Oil droplets (ลอยขึ้น ⬆️)<br>
        <b>Skimmer:</b> เก็บ oil ที่ผิวบน<br>
        <b>Drain:</b> Water ออกด้านล่าง<br>
        <b>Density reference (μ):</b> Viscosity ของน้ำ
      </div>
      <div class="pi-card pi-cpo">
        <div class="pi-head">🌴 CPO Degumming — Water-in-Oil</div>
        <b>Continuous Phase:</b> CPO (น้ำมัน)<br>
        <b>Dispersed Phase:</b> Sludge Water (จม ⬇️)<br>
        <b>Overflow:</b> CPO สะอาดออกด้านบน<br>
        <b>Drain:</b> SLW (Sludge Water) ออกด้านล่าง<br>
        <b>Density reference (μ):</b> Viscosity ของ CPO ที่ 90°C
      </div>
    </div>
    <div class="note-box note-warn">
      <div class="note-title">⚠️ ผลกระทบต่อ Stokes' Law</div>
      ใน CPO system: (ρ<sub>SLW</sub> − ρ<sub>CPO</sub>) เป็นบวก (SLW หนักกว่า) → หยดน้ำจมลง (Settling Velocity เป็นบวก แต่ทิศทางลง) ใช้ |Δρ| ในสมการเช่นเดิม แต่ต้องปรับ outlet design ให้สอดคล้อง
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-green">✅</div>
      <div>
        <div class="card-title">สรุป: อะไรนำมาใช้ได้ — อะไรปรับก่อน</div>
      </div>
    </div>
    <div class="table-wrap">
      <table>
        <thead><tr><th>หัวข้อ</th><th>API 421</th><th>Edible Oil Proc.</th><th>Equipment Design HB</th><th>ใช้ได้กับ CPO?</th></tr></thead>
        <tbody>
          <tr>
            <td>Stokes' Law สำหรับ V<sub>t</sub></td>
            <td>✅ ให้สมการครบ</td>
            <td>—</td>
            <td>✅ ยืนยัน (Eq. 5-5)</td>
            <td><span class="badge badge-green">ใช้ได้ ปรับ Δρ + μ</span></td>
          </tr>
          <tr>
            <td>Surface Loading Rate Concept</td>
            <td>✅ A<sub>H</sub> = F·Q/V<sub>t</sub></td>
            <td>—</td>
            <td>—</td>
            <td><span class="badge badge-green">ใช้หลักการได้</span></td>
          </tr>
          <tr>
            <td>Turbulence Factor F</td>
            <td>✅ Chart Figure 4</td>
            <td>—</td>
            <td>—</td>
            <td><span class="badge badge-amber">ปรับใช้ (L/L ≠ G/L)</span></td>
          </tr>
          <tr>
            <td>Horizontal vessel preference</td>
            <td>✅ แนะนำ</td>
            <td>✅ สนับสนุน</td>
            <td>✅ Large liquid load</td>
            <td><span class="badge badge-green">ใช้ได้</span></td>
          </tr>
          <tr>
            <td>Nomograph สำหรับ sizing</td>
            <td>—</td>
            <td>—</td>
            <td>✅ มี (สำหรับ V/L drum)</td>
            <td><span class="badge badge-coral">ใช้ไม่ได้ (V/L เท่านั้น)</span></td>
          </tr>
          <tr>
            <td>Temperature effect (μ)</td>
            <td>✅ Figure 2 (น้ำ)</td>
            <td>ยืนยัน 90°C เหมาะ</td>
            <td>—</td>
            <td><span class="badge badge-amber">ปรับ: ใช้ μ<sub>CPO</sub> ที่ 90°C</span></td>
          </tr>
          <tr>
            <td>Droplet size D<sub>p</sub></td>
            <td>150 μm (standard)</td>
            <td>—</td>
            <td>3–100 μm (liquid)</td>
            <td><span class="badge badge-amber">ต้องวัดจาก Lab</span></td>
          </tr>
          <tr>
            <td>Residence Time approach</td>
            <td>—</td>
            <td>✅ สนับสนุน</td>
            <td>Holding time concept</td>
            <td><span class="badge badge-green">แนะนำ (เป็น primary)</span></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>

  <div class="card">
    <div class="card-header">
      <div class="card-icon ci-blue">📋</div>
      <div>
        <div class="card-title">Design Checklist สำหรับ CPO Settling Tank</div>
      </div>
    </div>
    <div class="steps">
      <div class="step-item">
        <div class="step-num">A</div>
        <div class="step-body">
          <div class="step-title">รับข้อมูลจาก Lab (HOLD)</div>
          <div class="step-desc">✦ % DI water ที่เหมาะสม → SLW flow rate · ✦ Batch settling time ที่ 90°C → Residence time · ✦ SLW density ที่ 90°C → Δρ</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">B</div>
        <div class="step-body">
          <div class="step-title">คำนวณ V<sub>t</sub> ด้วย Stokes' Law</div>
          <div class="step-desc">ใช้ μ ของ CPO ที่ 90°C ≈ 0.018 Pa·s · Δρ = ρ<sub>SLW</sub> − ρ<sub>CPO</sub> · D<sub>p</sub> จาก Lab หรือใช้ conservative value</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">C</div>
        <div class="step-body">
          <div class="step-title">Size จาก Residence Time ก่อน (Primary)</div>
          <div class="step-desc">V<sub>tank</sub> = Q<sub>total</sub> × t<sub>r</sub> × SF · ตรวจสอบว่า A<sub>H</sub> ≥ F·Q/V<sub>t</sub> ด้วย</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">D</div>
        <div class="step-body">
          <div class="step-title">กำหนด Geometry</div>
          <div class="step-desc">L/B ≥ 3 (อย่างน้อย) · d/B ≈ 0.3–0.5 · วัสดุ SS316L · Material class 150# · Design temp 115°C</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">E</div>
        <div class="step-body">
          <div class="step-title">Internals และ Nozzles</div>
          <div class="step-desc">Feed Inlet: ต่ำ (ใต้ interface) พร้อม distributor · CPO Outlet: overflow weir ด้านบน · SLW Drain: ก้นถัง · Level instruments: LI/LA · Temperature: TI</div>
        </div>
      </div>
      <div class="step-item">
        <div class="step-num">F</div>
        <div class="step-body">
          <div class="step-title">Piping และ Utilities</div>
          <div class="step-desc">CPO lines: Heat Tracing (solidification risk) · SLW lines: Insulation only · ถังอาจต้องการ Steam Jacket หรือ Hot Water Coil เพื่อรักษา 90°C</div>
        </div>
      </div>
    </div>
  </div>

</div><!-- end #adapt -->

</div><!-- end .page -->

<script>
function showSection(id) {
  document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
  document.querySelectorAll('.nav-tab').forEach(t => t.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  event.currentTarget.classList.add('active');
}

function calcStokes() {
  const rho_c = parseFloat(document.getElementById('rho_cpo').value);
  const rho_d = parseFloat(document.getElementById('rho_slw').value);
  const mu = parseFloat(document.getElementById('mu_cpo').value);
  const dp_um = parseFloat(document.getElementById('dp').value);
  const dp = dp_um * 1e-6;
  const g = 9.81;
  const dRho = Math.abs(rho_d - rho_c);
  const Vt = (g * dp * dp * dRho) / (18 * mu);
  const Vt_mms = Vt * 1000;
  const Vt_mmin = Vt * 60;
  const Re = rho_c * Vt * dp / mu;
  document.getElementById('res-vt-mms').textContent = Vt_mms.toFixed(3);
  document.getElementById('res-vt-mmin').textContent = (Vt_mmin * 1000).toFixed(2) + ' mm/min';
  document.getElementById('res-re').textContent = Re.toFixed(4);
  let checkMsg = '';
  if (Re < 0.5) {
    checkMsg = '<div class="note-title">✅ Stokes\' Law ใช้ได้ (Re < 0.5)</div>การคำนวณนี้ถูกต้อง อยู่ใน Stokes\' regime';
  } else if (Re < 1.0) {
    checkMsg = '<div class="note-title">⚠️ Re อยู่ในช่วงกลาง (0.5–1.0)</div>Stokes\' Law ยังได้ผลใกล้เคียง แต่ควรใช้ drag correlation ที่แม่นกว่า';
  } else {
    checkMsg = '<div class="note-title">❌ Re > 1.0 — Stokes\' Law ไม่เหมาะ</div>ต้องใช้สมการ drag ทั่วไป (Intermediate Law) — ลด D<sub>p</sub> หรือตรวจสอบข้อมูล';
  }
  document.getElementById('res-check').innerHTML = checkMsg;
  document.getElementById('result-stokes').classList.add('show');
}

function calcTank() {
  const Q_m3hr = parseFloat(document.getElementById('q_cpo').value);
  const t_min = parseFloat(document.getElementById('t_res').value);
  const sf = parseFloat(document.getElementById('sf').value);
  const depth = parseFloat(document.getElementById('depth').value);
  const rho_c = parseFloat(document.getElementById('rho_cpo').value);
  const rho_d = parseFloat(document.getElementById('rho_slw').value);
  const mu = parseFloat(document.getElementById('mu_cpo').value);
  const dp = parseFloat(document.getElementById('dp').value) * 1e-6;
  const g = 9.81;
  const dRho = Math.abs(rho_d - rho_c);
  const Vt = (g * dp * dp * dRho) / (18 * mu);
  const Q_m3min = Q_m3hr / 60;
  const Q_m3s = Q_m3hr / 3600;
  const Vol = Q_m3min * t_min * sf;
  const AH_stokes = 1.5 * Q_m3s / Vt;
  const AH_res = Vol / depth;
  const AH = Math.max(AH_stokes, AH_res);
  const L_est = Math.sqrt(AH * 3);
  const W_est = L_est / 3;
  document.getElementById('res-vol').textContent = Vol.toFixed(1);
  document.getElementById('res-ah').textContent = AH.toFixed(1);
  document.getElementById('res-l').textContent = L_est.toFixed(1);
  document.getElementById('res-w').textContent = W_est.toFixed(1);
  let note = '<div class="note-title">📌 หมายเหตุ</div>';
  note += 'A<sub>H</sub> จาก Residence Time: ' + AH_res.toFixed(1) + ' m² · ';
  note += 'A<sub>H</sub> จาก Stokes (F=1.5): ' + AH_stokes.toFixed(1) + ' m²<br>';
  note += 'ใช้ค่าที่มากกว่า = <b>' + AH.toFixed(1) + ' m²</b> · L/B assumed = 3:1<br>';
  note += '⚠️ นี่เป็นการประมาณเบื้องต้นเท่านั้น ต้องรอผล Lab ยืนยัน';
  document.getElementById('res-tank-note').innerHTML = note;
  document.getElementById('result-tank').classList.add('show');
}
</script>
</body>
</html>
