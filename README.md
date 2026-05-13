<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>El Pretérito — Study Guide</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,700;1,400&family=IBM+Plex+Mono:wght@400;600&family=IBM+Plex+Sans:wght@300;400;600&display=swap');

  :root {
    --bg: #0e0e0e;
    --surface: #161616;
    --card: #1c1c1c;
    --border: #2a2a2a;
    --yellow: #f5e642;
    --green: #4ade80;
    --blue: #60a5fa;
    --orange: #fb923c;
    --pink: #f472b6;
    --text: #e8e8e8;
    --muted: #888;
    --mono: 'IBM Plex Mono', monospace;
    --sans: 'IBM Plex Sans', sans-serif;
    --serif: 'Playfair Display', serif;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: var(--sans);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* TABS */
  .tab-bar {
    position: sticky;
    top: 0;
    z-index: 100;
    background: var(--bg);
    border-bottom: 1px solid var(--border);
    display: flex;
    gap: 0;
    overflow-x: auto;
    scrollbar-width: none;
  }
  .tab-bar::-webkit-scrollbar { display: none; }
  .tab {
    padding: 14px 22px;
    font-family: var(--mono);
    font-size: 12px;
    font-weight: 600;
    letter-spacing: .08em;
    text-transform: uppercase;
    cursor: pointer;
    border: none;
    background: transparent;
    color: var(--muted);
    border-bottom: 2px solid transparent;
    white-space: nowrap;
    transition: all .2s;
  }
  .tab:hover { color: var(--text); }
  .tab.active { color: var(--yellow); border-bottom-color: var(--yellow); }

  .panel { display: none; padding: 32px 20px 60px; max-width: 960px; margin: 0 auto; }
  .panel.active { display: block; }

  /* HERO */
  .hero {
    text-align: center;
    padding: 48px 20px 32px;
  }
  .hero h1 {
    font-family: var(--serif);
    font-size: clamp(2.4rem, 7vw, 4.5rem);
    color: var(--yellow);
    line-height: 1.1;
    letter-spacing: -.02em;
  }
  .hero .sub {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--muted);
    letter-spacing: .12em;
    margin-top: 10px;
    text-transform: uppercase;
  }

  /* SECTION HEADERS */
  h2 {
    font-family: var(--serif);
    font-size: 1.5rem;
    color: var(--yellow);
    margin: 36px 0 16px;
    padding-bottom: 6px;
    border-bottom: 1px solid var(--border);
  }
  h3 {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .12em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 10px;
  }

  /* RULE CARDS */
  .rule-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 20px 22px;
    margin-bottom: 14px;
  }
  .rule-card .label {
    font-family: var(--mono);
    font-size: 11px;
    letter-spacing: .1em;
    text-transform: uppercase;
    margin-bottom: 8px;
  }
  .rule-card p {
    font-size: 14px;
    line-height: 1.7;
    color: #ccc;
  }
  .rule-card .examples {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-top: 12px;
  }
  .pill {
    font-family: var(--mono);
    font-size: 12px;
    padding: 4px 12px;
    border-radius: 20px;
    background: #252525;
    border: 1px solid var(--border);
  }
  .pill.yellow { color: var(--yellow); border-color: #4a430a; background: #1e1a05; }
  .pill.green  { color: var(--green);  border-color: #14532d; background: #052010; }
  .pill.blue   { color: var(--blue);   border-color: #1e3a5f; background: #040f1f; }
  .pill.orange { color: var(--orange); border-color: #7c2d12; background: #1f0a03; }
  .pill.pink   { color: var(--pink);   border-color: #831843; background: #1f0412; }

  /* CONJUGATION TABLES */
  .conj-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap: 16px;
    margin-bottom: 16px;
  }
  .conj-table {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
  }
  .conj-table .verb-head {
    background: #222;
    padding: 10px 14px;
    font-family: var(--serif);
    font-size: 1rem;
    font-weight: 700;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .conj-table .verb-head .eng {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    font-style: italic;
  }
  .conj-table table {
    width: 100%;
    border-collapse: collapse;
    font-family: var(--mono);
    font-size: 12.5px;
  }
  .conj-table td {
    padding: 7px 14px;
    border-top: 1px solid var(--border);
    color: #ccc;
  }
  .conj-table td:first-child { color: var(--muted); font-size: 11px; }
  .conj-table tr:hover td { background: #222; }

  /* FLASHCARD MODE */
  #flashcard-panel {
    display: none;
    flex-direction: column;
    align-items: center;
    padding: 40px 20px 80px;
  }
  #flashcard-panel.active { display: flex; }

  .fc-controls {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    justify-content: center;
    margin-bottom: 32px;
  }
  .fc-controls select, .fc-controls button {
    font-family: var(--mono);
    font-size: 12px;
    padding: 9px 16px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--text);
    cursor: pointer;
    letter-spacing: .05em;
  }
  .fc-controls button { transition: all .2s; }
  .fc-controls button:hover { background: #282828; }
  .fc-controls .btn-primary { background: var(--yellow); color: #0e0e0e; border-color: var(--yellow); font-weight: 600; }
  .fc-controls .btn-primary:hover { opacity: .9; }

  .flashcard {
    width: 100%;
    max-width: 480px;
    aspect-ratio: 3/2;
    perspective: 1000px;
    cursor: pointer;
    user-select: none;
  }
  .flashcard-inner {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform .55s cubic-bezier(.4,0,.2,1);
  }
  .flashcard.flipped .flashcard-inner { transform: rotateY(180deg); }
  .flashcard-front, .flashcard-back {
    position: absolute;
    inset: 0;
    border-radius: 14px;
    backface-visibility: hidden;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 28px;
  }
  .flashcard-front {
    background: var(--card);
    border: 1px solid var(--border);
  }
  .flashcard-back {
    background: #171a10;
    border: 1px solid #3a4a1a;
    transform: rotateY(180deg);
  }
  .flashcard-front .prompt {
    font-family: var(--mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: .12em;
    text-transform: uppercase;
    margin-bottom: 14px;
  }
  .flashcard-front .word {
    font-family: var(--serif);
    font-size: clamp(1.6rem, 5vw, 2.4rem);
    color: var(--yellow);
    text-align: center;
  }
  .flashcard-back .answer-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4px 20px;
    font-family: var(--mono);
    font-size: 13px;
  }
  .flashcard-back .answer-grid span { color: var(--green); }
  .flashcard-back .hint {
    font-family: var(--mono);
    font-size: 10px;
    color: var(--muted);
    position: absolute;
    bottom: 16px;
    letter-spacing: .08em;
  }
  .fc-status {
    font-family: var(--mono);
    font-size: 12px;
    color: var(--muted);
    margin-top: 20px;
    letter-spacing: .06em;
  }
  .fc-nav {
    display: flex;
    gap: 16px;
    margin-top: 20px;
  }
  .fc-nav button {
    font-family: var(--mono);
    font-size: 13px;
    padding: 10px 28px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--text);
    cursor: pointer;
    transition: all .2s;
    letter-spacing: .04em;
  }
  .fc-nav button:hover { background: #282828; border-color: #444; }

  /* ORTHO section */
  .ortho-row {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
    gap: 12px;
    margin-bottom: 12px;
  }
  .ortho-box {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 16px;
    text-align: center;
  }
  .ortho-box .trigger {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--orange);
    margin-bottom: 6px;
  }
  .arrow {
    font-size: 18px;
    color: var(--muted);
    margin: 4px 0;
  }
  .ortho-box .result {
    font-family: var(--mono);
    font-size: 13px;
    color: var(--green);
  }
  .ortho-box .note {
    font-size: 11px;
    color: var(--muted);
    margin-top: 6px;
    line-height: 1.5;
  }

  /* QUIZ */
  .quiz-wrap { max-width: 600px; margin: 0 auto; }
  .quiz-q {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 24px;
    margin-bottom: 16px;
  }
  .quiz-q .q-prompt {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 10px;
    font-family: var(--mono);
    font-size: 12px;
    letter-spacing: .06em;
  }
  .quiz-q .q-sentence {
    font-family: var(--serif);
    font-size: 1.25rem;
    color: var(--text);
    line-height: 1.5;
    margin-bottom: 14px;
  }
  .quiz-q input {
    font-family: var(--mono);
    font-size: 14px;
    padding: 10px 14px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: #111;
    color: var(--text);
    width: 180px;
    outline: none;
    transition: border .2s;
  }
  .quiz-q input:focus { border-color: var(--yellow); }
  .quiz-q input.correct { border-color: var(--green); background: #05200f; color: var(--green); }
  .quiz-q input.wrong   { border-color: #ef4444;      background: #200505; color: #fca5a5; }
  .quiz-q .feedback {
    font-family: var(--mono);
    font-size: 12px;
    margin-top: 8px;
    min-height: 18px;
  }
  .quiz-q .feedback.correct { color: var(--green); }
  .quiz-q .feedback.wrong   { color: #fca5a5; }
  .quiz-btns {
    display: flex;
    gap: 12px;
    margin-bottom: 28px;
  }
  .quiz-btns button {
    font-family: var(--mono);
    font-size: 12px;
    padding: 10px 20px;
    border-radius: 6px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--text);
    cursor: pointer;
    letter-spacing: .05em;
    transition: all .2s;
  }
  .quiz-btns .btn-primary { background: var(--yellow); color: #0e0e0e; border-color: var(--yellow); font-weight: 600; }
  .quiz-score {
    font-family: var(--serif);
    font-size: 1.4rem;
    color: var(--yellow);
    text-align: center;
    padding: 16px;
    display: none;
  }

  /* REGULAR ENDINGS */
  .endings-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
    margin-bottom: 20px;
  }
  .endings-table {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 8px;
    overflow: hidden;
  }
  .endings-table .head {
    background: #1e1e1e;
    padding: 10px 14px;
    font-family: var(--serif);
    font-size: 1.1rem;
    color: var(--yellow);
  }
  .endings-table table {
    width: 100%;
    border-collapse: collapse;
    font-family: var(--mono);
    font-size: 12.5px;
  }
  .endings-table td {
    padding: 7px 14px;
    border-top: 1px solid var(--border);
  }
  .endings-table td:first-child { color: var(--muted); }
  .endings-table td:last-child  { color: var(--green); }

  .tip-box {
    background: #111a05;
    border: 1px solid #2a3a0a;
    border-radius: 8px;
    padding: 16px 20px;
    margin: 16px 0;
    font-size: 13.5px;
    line-height: 1.7;
    color: #bcd090;
  }
  .tip-box strong { color: var(--yellow); font-family: var(--mono); font-size: 12px; letter-spacing: .08em; text-transform: uppercase; }

  /* SCROLL FADE */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  .panel.active > * {
    animation: fadeUp .35s ease both;
  }
</style>
</head>
<body>

<div class="hero">
  <h1>El Pretérito</h1>
  <p class="sub">Interactive Study Guide &nbsp;·&nbsp; Preterite Tense</p>
</div>

<div class="tab-bar">
  <button class="tab active" onclick="show('rules')">Rules</button>
  <button class="tab" onclick="show('regulares')">Regular Verbs</button>
  <button class="tab" onclick="show('irregulares')">Irregular Verbs</button>
  <button class="tab" onclick="show('ortho')">Spelling Changes</button>
  <button class="tab" onclick="show('flashcards')">Flashcards</button>
  <button class="tab" onclick="show('quiz')">Quiz</button>
</div>

<!-- ===== RULES ===== -->
<div id="rules" class="panel active">
  <h2>Key Rules</h2>

  <div class="rule-card">
    <div class="label" style="color:var(--yellow)">When to use El Pretérito</div>
    <p>Use the preterite for actions that <strong>occurred in the past</strong> and are completed. It describes single events, sequences of events, or actions done a specific number of times.</p>
  </div>

  <div class="rule-card">
    <div class="label" style="color:var(--green)">Accents on Regular Verbs</div>
    <p>Regular -AR, -ER, -IR verbs have accents on the <strong>yo</strong> and <strong>él/ella</strong> forms (1st & 3rd person singular).</p>
    <div class="examples">
      <span class="pill yellow">hablé</span>
      <span class="pill yellow">habló</span>
      <span class="pill blue">comí</span>
      <span class="pill blue">comió</span>
      <span class="pill green">viví</span>
      <span class="pill green">vivió</span>
    </div>
  </div>

  <div class="rule-card">
    <div class="label" style="color:var(--orange)">Irregular Verbs — NO Accents</div>
    <p>All irregular preterite verbs have <strong>NO accent marks</strong>. This is a key way to distinguish them from regular forms.</p>
    <div class="examples">
      <span class="pill orange">tuve</span>
      <span class="pill orange">hice</span>
      <span class="pill orange">fui</span>
      <span class="pill orange">puse</span>
      <span class="pill orange">dije</span>
    </div>
  </div>

  <div class="rule-card">
    <div class="label" style="color:var(--pink)">Stem-Changing Verbs (o→u, e→i)</div>
    <p>Stem changes in the preterite occur <strong>only in 3rd person</strong> (él/ella and ellos/ellas). The stem change does NOT affect yo, tú, nosotros, or vosotros.</p>
    <div class="examples">
      <span class="pill pink">morir → murió / murieron</span>
      <span class="pill pink">dormir → durmió / durmieron</span>
      <span class="pill pink">preferir → prefirió / prefirieron</span>
      <span class="pill pink">mentir → mintió / mintieron</span>
    </div>
  </div>

  <div class="rule-card">
    <div class="label" style="color:var(--blue)">Hay</div>
    <p><strong>Hay</strong> (there is/there are) in the preterite becomes <strong>hubo</strong>. It has no accent.</p>
  </div>
</div>

<!-- ===== REGULAR VERBS ===== -->
<div id="regulares" class="panel">
  <h2>Regular Verb Endings</h2>

  <div class="tip-box">
    <strong>DNA Pasos de conjugación:</strong> Drop the infinitive ending (-ar/-er/-ir), then add the preterite ending.
  </div>

  <div class="endings-grid">
    <div class="endings-table">
      <div class="head">-AR verbs &nbsp;<span style="font-size:.75rem;color:var(--muted);font-family:var(--mono)">e.g. hablar</span></div>
      <table>
        <tr><td>yo</td><td>-é</td></tr>
        <tr><td>tú</td><td>-aste</td></tr>
        <tr><td>él/ella/Ud.</td><td>-ó</td></tr>
        <tr><td>nosotros,-as</td><td>-amos</td></tr>
        <tr><td>vosotros,-as</td><td>-asteis</td></tr>
        <tr><td>ellos/ellas/Uds.</td><td>-aron</td></tr>
      </table>
    </div>
    <div class="endings-table">
      <div class="head">-ER verbs &nbsp;<span style="font-size:.75rem;color:var(--muted);font-family:var(--mono)">e.g. comer</span></div>
      <table>
        <tr><td>yo</td><td>-í</td></tr>
        <tr><td>tú</td><td>-iste</td></tr>
        <tr><td>él/ella/Ud.</td><td>-ió</td></tr>
        <tr><td>nosotros,-as</td><td>-imos</td></tr>
        <tr><td>vosotros,-as</td><td>-isteis</td></tr>
        <tr><td>ellos/ellas/Uds.</td><td>-ieron</td></tr>
      </table>
    </div>
    <div class="endings-table">
      <div class="head">-IR verbs &nbsp;<span style="font-size:.75rem;color:var(--muted);font-family:var(--mono)">e.g. vivir</span></div>
      <table>
        <tr><td>yo</td><td>-í</td></tr>
        <tr><td>tú</td><td>-iste</td></tr>
        <tr><td>él/ella/Ud.</td><td>-ió</td></tr>
        <tr><td>nosotros,-as</td><td>-imos</td></tr>
        <tr><td>vosotros,-as</td><td>-isteis</td></tr>
        <tr><td>ellos/ellas/Uds.</td><td>-ieron</td></tr>
      </table>
    </div>
  </div>

  <div class="tip-box">
    <strong>Note:</strong> -ER and -IR verbs share the same preterite endings! The only difference between all three is the <em>yo</em> (-é vs -í) and <em>él</em> (-ó vs -ió) forms.
  </div>
</div>

<!-- ===== IRREGULAR VERBS ===== -->
<div id="irregulares" class="panel">
  <h2>Irregular Verbs</h2>
  <p style="color:var(--muted);font-size:13px;margin-bottom:24px;font-family:var(--mono)">Remember: NO accent marks on any of these.</p>

  <div class="conj-grid" id="conj-grid"></div>
</div>

<!-- ===== SPELLING CHANGES ===== -->
<div id="ortho" class="panel">
  <h2>Cambios Ortográficos (Spelling Changes)</h2>
  <p style="color:var(--muted);font-size:13px;margin-bottom:20px;">These changes happen to preserve the pronunciation of the original verb stem. They only affect the <strong style="color:var(--yellow)">yo</strong> form.</p>

  <h3>-car, -gar, -zar verbs (yo form only)</h3>
  <div class="ortho-row">
    <div class="ortho-box">
      <div class="trigger">-car</div>
      <div class="arrow">↓</div>
      <div class="result">-qué</div>
      <div class="note">buscar → <strong>busqué</strong></div>
    </div>
    <div class="ortho-box">
      <div class="trigger">-gar</div>
      <div class="arrow">↓</div>
      <div class="result">-gué</div>
      <div class="note">llegar → <strong>llegué</strong></div>
    </div>
    <div class="ortho-box">
      <div class="trigger">-zar</div>
      <div class="arrow">↓</div>
      <div class="result">-cé</div>
      <div class="note">empezar → <strong>empecé</strong></div>
    </div>
  </div>

  <h3 style="margin-top:28px;">-uir verbs (i → y in 3rd person)</h3>
  <div class="rule-card">
    <p>The <strong>i</strong> becomes <strong>y</strong> in 3rd person singular and plural. The <strong>i is accented</strong> in all other forms EXCEPT 1st person plural (nosotros).</p>
    <div class="conj-grid" style="margin-top:16px;">
      <div class="conj-table">
        <div class="verb-head">destruir <span class="eng">to destroy</span></div>
        <table>
          <tr><td>yo</td><td>destruí</td></tr>
          <tr><td>tú</td><td>destruiste</td></tr>
          <tr><td>él/ella</td><td>destru<strong style="color:var(--yellow)">y</strong>ó</td></tr>
          <tr><td>nosotros</td><td>destruimos</td></tr>
          <tr><td>vosotros</td><td>destruisteis</td></tr>
          <tr><td>ellos</td><td>destru<strong style="color:var(--yellow)">y</strong>eron</td></tr>
        </table>
      </div>
    </div>
  </div>

  <h3 style="margin-top:28px;">-aer, -eer, -oír, -oer verbs (i → y in 3rd person)</h3>
  <div class="rule-card">
    <p>Same rule as -uir: <strong>i → y</strong> in 3rd person. But here the <strong>i is accented in ALL forms except 3rd person</strong>.</p>
    <div class="conj-grid" style="margin-top:16px;">
      <div class="conj-table">
        <div class="verb-head">leer <span class="eng">to read</span></div>
        <table>
          <tr><td>yo</td><td>le<strong style="color:var(--blue)">í</strong></td></tr>
          <tr><td>tú</td><td>le<strong style="color:var(--blue)">í</strong>ste</td></tr>
          <tr><td>él/ella</td><td>le<strong style="color:var(--yellow)">y</strong>ó</td></tr>
          <tr><td>nosotros</td><td>le<strong style="color:var(--blue)">í</strong>mos</td></tr>
          <tr><td>vosotros</td><td>le<strong style="color:var(--blue)">í</strong>steis</td></tr>
          <tr><td>ellos</td><td>le<strong style="color:var(--yellow)">y</strong>eron</td></tr>
        </table>
      </div>
      <div class="conj-table">
        <div class="verb-head">creer <span class="eng">to believe</span></div>
        <table>
          <tr><td>yo</td><td>cre<strong style="color:var(--blue)">í</strong></td></tr>
          <tr><td>tú</td><td>cre<strong style="color:var(--blue)">í</strong>ste</td></tr>
          <tr><td>él/ella</td><td>cre<strong style="color:var(--yellow)">y</strong>ó</td></tr>
          <tr><td>nosotros</td><td>cre<strong style="color:var(--blue)">í</strong>mos</td></tr>
          <tr><td>vosotros</td><td>cre<strong style="color:var(--blue)">í</strong>steis</td></tr>
          <tr><td>ellos</td><td>cre<strong style="color:var(--yellow)">y</strong>eron</td></tr>
        </table>
      </div>
    </div>
  </div>

  <h3 style="margin-top:28px;">-cir verbs (stem becomes j; -ieron → -eron)</h3>
  <div class="rule-card">
    <p>Verbs ending in <strong>-cir</strong> (conducir, traducir, decir) drop the <strong>i</strong> in the ellos form: → <strong>-jeron</strong> not -jieron.</p>
    <div class="conj-grid" style="margin-top:16px;">
      <div class="conj-table">
        <div class="verb-head">conducir <span class="eng">to drive</span></div>
        <table>
          <tr><td>yo</td><td>conduje</td></tr>
          <tr><td>tú</td><td>condujiste</td></tr>
          <tr><td>él/ella</td><td>condujo</td></tr>
          <tr><td>nosotros</td><td>condujimos</td></tr>
          <tr><td>vosotros</td><td>condujisteis</td></tr>
          <tr><td>ellos</td><td>conduj<strong style="color:var(--yellow)">eron</strong></td></tr>
        </table>
      </div>
    </div>
  </div>
</div>

<!-- ===== FLASHCARDS ===== -->
<div id="flashcards" class="panel" style="padding:0;">
  <div id="flashcard-panel" class="active" style="padding:32px 20px 80px;">
    <div class="fc-controls">
      <select id="fc-category">
        <option value="all">All Irregular Verbs</option>
        <option value="irregular">Irregular Only</option>
        <option value="stem">Stem-Changing</option>
      </select>
      <button class="btn-primary" onclick="startFlashcards()">Shuffle & Start</button>
    </div>
    <div class="flashcard" id="flashcard" onclick="flipCard()">
      <div class="flashcard-inner">
        <div class="flashcard-front">
          <div class="prompt">Conjugate in Preterite</div>
          <div class="word" id="fc-front">Click Start</div>
        </div>
        <div class="flashcard-back">
          <div class="answer-grid" id="fc-back"></div>
          <div class="hint">tap to flip back</div>
        </div>
      </div>
    </div>
    <div class="fc-status" id="fc-status">Select a category and press Shuffle & Start</div>
    <div class="fc-nav">
      <button onclick="prevCard()">← Prev</button>
      <button onclick="nextCard()">Next →</button>
    </div>
  </div>
</div>

<!-- ===== QUIZ ===== -->
<div id="quiz" class="panel">
  <h2>Conjugation Quiz</h2>
  <div class="quiz-btns">
    <button class="btn-primary" onclick="generateQuiz()">Generate New Quiz</button>
    <button onclick="checkQuiz()">Check Answers</button>
  </div>
  <div class="quiz-wrap" id="quiz-wrap"></div>
  <div class="quiz-score" id="quiz-score"></div>
</div>

<script>
// ===== DATA =====
const irregulars = [
  { verb:'ir', eng:'to go', forms:['fui','fuiste','fue','fuimos','fuisteis','fueron'] },
  { verb:'ser', eng:'to be', forms:['fui','fuiste','fue','fuimos','fuisteis','fueron'] },
  { verb:'dar', eng:'to give', forms:['di','diste','dio','dimos','disteis','dieron'] },
  { verb:'ver', eng:'to see', forms:['vi','viste','vio','vimos','visteis','vieron'] },
  { verb:'venir', eng:'to come', forms:['vine','viniste','vino','vinimos','vinisteis','vinieron'] },
  { verb:'tener', eng:'to have', forms:['tuve','tuviste','tuvo','tuvimos','tuvisteis','tuvieron'] },
  { verb:'hacer', eng:'to do/make', forms:['hice','hiciste','hizo','hicimos','hicisteis','hicieron'] },
  { verb:'poner', eng:'to put/place', forms:['puse','pusiste','puso','pusimos','pusisteis','pusieron'] },
  { verb:'estar', eng:'to be', forms:['estuve','estuviste','estuvo','estuvimos','estuvisteis','estuvieron'] },
  { verb:'querer', eng:'to want', forms:['quise','quisiste','quiso','quisimos','quisisteis','quisieron'] },
  { verb:'poder', eng:'to be able to', forms:['pude','pudiste','pudo','pudimos','pudisteis','pudieron'] },
  { verb:'saber', eng:'to know', forms:['supe','supiste','supo','supimos','supisteis','supieron'] },
  { verb:'decir', eng:'to say/tell', forms:['dije','dijiste','dijo','dijimos','dijisteis','dijeron'] },
  { verb:'traer', eng:'to bring', forms:['traje','trajiste','trajo','trajimos','trajisteis','trajeron'] },
  { verb:'andar', eng:'to walk/roam', forms:['anduve','anduviste','anduvo','anduvimos','anduvisteis','anduvieron'] },
];

const stemChanging = [
  { verb:'morir (o→u)', eng:'to die', forms:['morí','moriste','murió','morimos','moristeis','murieron'] },
  { verb:'dormir (o→u)', eng:'to sleep', forms:['dormí','dormiste','durmió','dormimos','dormisteis','durmieron'] },
  { verb:'preferir (e→i)', eng:'to prefer', forms:['preferí','preferiste','prefirió','preferimos','preferisteis','prefirieron'] },
  { verb:'mentir (e→i)', eng:'to lie', forms:['mentí','mentiste','mintió','mentimos','mentisteis','mintieron'] },
];

const pronouns = ['yo','tú','él/ella','nosotros','vosotros','ellos/ellas'];

// Build conjugation tables
function buildConjTables() {
  const grid = document.getElementById('conj-grid');
  const all = [...irregulars, ...stemChanging];
  grid.innerHTML = all.map(v => `
    <div class="conj-table">
      <div class="verb-head">${v.verb} <span class="eng">${v.eng}</span></div>
      <table>
        ${pronouns.map((p,i) => `<tr><td>${p}</td><td>${v.forms[i]}</td></tr>`).join('')}
      </table>
    </div>
  `).join('');
}
buildConjTables();

// ===== FLASHCARDS =====
let deck = [], fcIndex = 0, fcFlipped = false;

function startFlashcards() {
  const cat = document.getElementById('fc-category').value;
  let source = cat === 'stem' ? stemChanging : cat === 'irregular' ? irregulars : [...irregulars, ...stemChanging];
  deck = shuffle([...source]);
  fcIndex = 0;
  document.getElementById('flashcard').classList.remove('flipped');
  fcFlipped = false;
  showCard();
}

function showCard() {
  if (!deck.length) return;
  const v = deck[fcIndex];
  document.getElementById('fc-front').textContent = v.verb;
  document.getElementById('fc-back').innerHTML = pronouns.map((p,i) =>
    `<span style="color:var(--muted)">${p}</span><span>${v.forms[i]}</span>`
  ).join('');
  document.getElementById('fc-status').textContent = `Card ${fcIndex+1} of ${deck.length}`;
  if (fcFlipped) {
    document.getElementById('flashcard').classList.remove('flipped');
    fcFlipped = false;
  }
}

function flipCard() {
  const el = document.getElementById('flashcard');
  el.classList.toggle('flipped');
  fcFlipped = !fcFlipped;
}

function nextCard() {
  if (!deck.length) return;
  fcIndex = (fcIndex + 1) % deck.length;
  showCard();
}
function prevCard() {
  if (!deck.length) return;
  fcIndex = (fcIndex - 1 + deck.length) % deck.length;
  showCard();
}

function shuffle(a) {
  for (let i = a.length-1; i > 0; i--) {
    const j = Math.floor(Math.random()*(i+1));
    [a[i],a[j]] = [a[j],a[i]];
  }
  return a;
}

// ===== QUIZ =====
const quizBank = [
  { sentence:'Yo ___ (hablar) con mi amiga ayer.', answer:'hablé', hint:'Regular -AR, yo' },
  { sentence:'Ella ___ (comer) una pizza anoche.', answer:'comió', hint:'Regular -ER, ella' },
  { sentence:'Nosotros ___ (vivir) en Madrid por dos años.', answer:'vivimos', hint:'Regular -IR, nosotros' },
  { sentence:'Tú ___ (ir) al mercado el sábado.', answer:'fuiste', hint:'Irregular: ir' },
  { sentence:'Ellos ___ (ser) buenos amigos.', answer:'fueron', hint:'Irregular: ser' },
  { sentence:'Yo ___ (tener) mucho trabajo la semana pasada.', answer:'tuve', hint:'Irregular: tener, NO accent' },
  { sentence:'Ella ___ (hacer) la tarea rápidamente.', answer:'hizo', hint:'Irregular: hacer, c→z in él form' },
  { sentence:'Nosotros ___ (estar) en el parque ayer.', answer:'estuvimos', hint:'Irregular: estar' },
  { sentence:'Yo ___ (buscar) mis llaves por una hora.', answer:'busqué', hint:'-car verb: c→qu in yo' },
  { sentence:'El estudiante ___ (leer) el libro entero.', answer:'leyó', hint:'-eer verb: i→y in él' },
  { sentence:'Ellas ___ (dormir) ocho horas.', answer:'durmieron', hint:'Stem-change o→u in 3rd person' },
  { sentence:'Él ___ (preferir) el café al té.', answer:'prefirió', hint:'Stem-change e→i in 3rd person' },
  { sentence:'Tú ___ (decir) la verdad siempre.', answer:'dijiste', hint:'Irregular: decir' },
  { sentence:'Yo ___ (llegar) tarde a la clase.', answer:'llegué', hint:'-gar verb: g→gu in yo' },
  { sentence:'Ella ___ (destruir) el castillo de arena.', answer:'destruyó', hint:'-uir verb: i→y in ella' },
  { sentence:'Ellos ___ (traer) comida a la fiesta.', answer:'trajeron', hint:'Irregular -cir/-jer: no i in ellos' },
  { sentence:'Yo ___ (poder) terminar el proyecto.', answer:'pude', hint:'Irregular: poder' },
  { sentence:'Nosotros ___ (dar) un regalo a la maestra.', answer:'dimos', hint:'Irregular: dar' },
];

let activeQuiz = [];

function generateQuiz() {
  activeQuiz = shuffle([...quizBank]).slice(0, 8);
  const wrap = document.getElementById('quiz-wrap');
  document.getElementById('quiz-score').style.display = 'none';
  wrap.innerHTML = activeQuiz.map((q,i) => `
    <div class="quiz-q" id="qq-${i}">
      <div class="q-prompt">Fill in the blank with the correct preterite form</div>
      <div class="q-sentence">${q.sentence}</div>
      <input type="text" id="qa-${i}" placeholder="escribe aquí..." autocomplete="off" autocorrect="off" spellcheck="false"
        onkeydown="if(event.key==='Enter')checkOne(${i})">
      <div class="feedback" id="qf-${i}"></div>
    </div>
  `).join('');
}

function checkOne(i) {
  const q = activeQuiz[i];
  const input = document.getElementById(`qa-${i}`);
  const fb = document.getElementById(`qf-${i}`);
  const val = input.value.trim().toLowerCase();
  const correct = q.answer.toLowerCase();
  if (val === correct) {
    input.className = 'correct';
    fb.className = 'feedback correct';
    fb.textContent = '✓ Correct!';
  } else if (val) {
    input.className = 'wrong';
    fb.className = 'feedback wrong';
    fb.textContent = `✗ Answer: ${q.answer}  (${q.hint})`;
  }
}

function checkQuiz() {
  let score = 0;
  activeQuiz.forEach((_,i) => {
    checkOne(i);
    const input = document.getElementById(`qa-${i}`);
    if (input.classList.contains('correct')) score++;
  });
  const s = document.getElementById('quiz-score');
  s.style.display = 'block';
  const pct = Math.round(score/activeQuiz.length*100);
  s.textContent = `Score: ${score} / ${activeQuiz.length}  (${pct}%) ${pct===100?'🎉 Perfect!':pct>=75?'👍 Great job!':'Keep studying!'}`;
}

generateQuiz();

// ===== TABS =====
function show(id) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  event.target.classList.add('active');
}
</script>
</body>
</html>
