
<!DOCTYPE html>
<html lang="it">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Cronologia — Irma Brandeis & Eugenio Montale</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,500;1,300;1,400&family=DM+Mono:wght@300;400&display=swap" rel="stylesheet">
<style>
:root {
  --cream: #f7f3ec;
  --ink: #1c1a16;
  --ink-soft: #4a4640;
  --ink-muted: #9a9590;
  --gold: #b89a5a;
  --gold-light: #e8d9b5;
  --blue: #185FA5;
  --purple: #534AB7;
  --coral: #993C1D;
  --green: #3B6D11;
  --gray: #5F5E5A;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background: var(--cream);
  color: var(--ink);
  font-family: 'Cormorant Garamond', Georgia, serif;
  min-height: 100vh;
}

.page-header {
  border-bottom: 1px solid var(--gold-light);
  padding: 3rem 3rem 2rem;
  position: relative;
  overflow: hidden;
}

.page-header::before {
  content: '';
  position: absolute;
  top: -40px;
  right: -40px;
  width: 200px;
  height: 200px;
  border: 1px solid var(--gold-light);
  border-radius: 50%;
  opacity: 0.5;
}

.page-header::after {
  content: '';
  position: absolute;
  bottom: -60px;
  right: 60px;
  width: 120px;
  height: 120px;
  border: 1px solid var(--gold-light);
  border-radius: 50%;
  opacity: 0.3;
}

.eyebrow {
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 1rem;
}

h1 {
  font-size: clamp(28px, 5vw, 48px);
  font-weight: 300;
  line-height: 1.15;
  margin-bottom: 0.5rem;
}

h1 em {
  font-style: italic;
  color: var(--ink-soft);
}

.subtitle {
  font-size: 15px;
  color: var(--ink-muted);
  font-style: italic;
  margin-top: 0.75rem;
}

.tei-ref {
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  color: var(--ink-muted);
  margin-top: 1.5rem;
  padding: 8px 12px;
  border-left: 2px solid var(--gold-light);
  display: inline-block;
}

.main {
  display: grid;
  grid-template-columns: 220px 1fr;
}

.sidebar {
  border-right: 1px solid var(--gold-light);
  padding: 2rem 1.5rem;
  position: sticky;
  top: 0;
  height: fit-content;
}

.sidebar-label {
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: var(--gold);
  margin-bottom: 1.25rem;
}

.legend-item {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 0.75rem;
  cursor: pointer;
  padding: 4px 0;
}

.legend-item.inactive {
  opacity: 0.3;
}

.leg-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 1.5px solid;
}

.legend-item span {
  font-size: 13px;
  color: var(--ink-soft);
}

.filter-all {
  font-family: 'DM Mono', monospace;
  font-size: 10px;
  color: var(--gold);
  cursor: pointer;
  margin-top: 1rem;
  text-decoration: underline;
}

.content {
  padding: 2rem 3rem;
}

.timeline {
  position: relative;
  padding-left: 2rem;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 0;
  top: 8px;
  bottom: 8px;
  width: 1px;
  background: linear-gradient(to bottom, transparent, var(--gold-light) 5%, var(--gold-light) 95%, transparent);
}

.tl-event {
  position: relative;
}

.tl-event.hidden {
  display: none;
}

.tl-dot-wrap {
  position: absolute;
  left: -2rem;
  top: 18px;
  width: 14px;
  height: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tl-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 1.5px solid;
  background: var(--cream);
  transition: transform 0.2s, box-shadow 0.2s;
}

.tl-event:hover .tl-dot,
.tl-event.active .tl-dot {
  transform: scale(1.4);
}

.type-biografico .tl-dot { border-color: var(--blue); }
.type-lettera .tl-dot { border-color: var(--purple); }
.type-poetico .tl-dot { border-color: var(--green); }
.type-storico .tl-dot { border-color: var(--coral); }
.type-accademico .tl-dot { border-color: #9C7A1C; }
.type-incontro .tl-dot { border-color: #0E7490; }
.type-morte .tl-dot { border-color: var(--gray); }
.type-critico .tl-dot { border-color: #7C3AED; }

.tl-inner {
  padding: 1.25rem 0 1.25rem 0.5rem;
  border-bottom: 1px solid transparent;
  cursor: pointer;
}

.tl-event:hover .tl-inner,
.tl-event.active .tl-inner {
  border-color: var(--gold-light);
}

.tl-date {
  font-family: 'DM Mono', monospace;
  font-size: 11px;
  color: var(--gold);
  margin-bottom: 4px;
}

.tl-label {
  font-size: 20px;
  line-height: 1.3;
}

.tl-tag {
  display: inline-block;
  font-family: 'DM Mono', monospace;
  font-size: 9px;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  padding: 2px 8px;
  border-radius: 2px;
  margin-top: 6px;
}

.tag-biografico { background:#E6F1FB; color:#185FA5; }
.tag-lettera { background:#EEEDFE; color:#3C3489; }
.tag-poetico { background:#EAF3DE; color:#27500A; }
.tag-storico { background:#FAECE7; color:#712B13; }
.tag-accademico { background:#F7F0D8; color:#7A5A00; }
.tag-incontro { background:#DFF6F8; color:#155E75; }
.tag-morte { background:#F1EFE8; color:#444441; }
.tag-critico { background:#EFE7FF; color:#5B21B6; }

.tl-desc {
  font-size: 15px;
  color: var(--ink-soft);
  line-height: 1.7;
  margin-top: 0.75rem;
  max-height: 0;
  overflow: hidden;
  opacity: 0;
  transition: max-height 0.4s ease, opacity 0.3s;
}

.tl-event.active .tl-desc {
  max-height: 400px;
  opacity: 1;
}

@media (max-width: 700px) {
  .main {
    grid-template-columns: 1fr;
  }

  .sidebar {
    position: static;
    border-right: none;
    border-bottom: 1px solid var(--gold-light);
  }

  .content {
    padding: 1.5rem;
  }
}
</style>
</head>
<body>

<header class="page-header">
  <p class="eyebrow">Edizione digitale — Timeline generata da XML TEI</p>
  <h1>Irma Brandeis<br><em>& Eugenio Montale</em></h1>
  <p class="subtitle">Cronologia biografica, poetica ed epistolare</p>
  <div class="tei-ref">fonte TEI: &lt;listEvent&gt;</div>
</header>

<div class="main">
  <aside class="sidebar">
    <p class="sidebar-label">Legenda</p>

    <div class="legend-item" data-type="biografico" onclick="filterType('biografico', this)">
      <div class="leg-dot" style="border-color:#185FA5"></div>
      <span>Biografico</span>
    </div>

    <div class="legend-item" data-type="lettera" onclick="filterType('lettera', this)">
      <div class="leg-dot" style="border-color:#534AB7"></div>
      <span>Lettere</span>
    </div>

    <div class="legend-item" data-type="poetico" onclick="filterType('poetico', this)">
      <div class="leg-dot" style="border-color:#3B6D11"></div>
      <span>Poetico</span>
    </div>

    <div class="legend-item" data-type="storico" onclick="filterType('storico', this)">
      <div class="leg-dot" style="border-color:#993C1D"></div>
      <span>Storico</span>
    </div>

    <div class="legend-item" data-type="accademico" onclick="filterType('accademico', this)">
      <div class="leg-dot" style="border-color:#9C7A1C"></div>
      <span>Accademico</span>
    </div>

    <div class="legend-item" data-type="incontro" onclick="filterType('incontro', this)">
      <div class="leg-dot" style="border-color:#0E7490"></div>
      <span>Incontri</span>
    </div>

    <div class="legend-item" data-type="critico" onclick="filterType('critico', this)">
      <div class="leg-dot" style="border-color:#7C3AED"></div>
      <span>Critico</span>
    </div>

    <div class="legend-item" data-type="morte" onclick="filterType('morte', this)">
      <div class="leg-dot" style="border-color:#5F5E5A"></div>
      <span>Morte</span>
    </div>

    <p class="filter-all" onclick="showAll()">mostra tutti</p>
  </aside>

  <main class="content">
    <div class="timeline">

      <!-- EVENTI GENERATI DAL TUO XML -->

      <div class="tl-event type-biografico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">12 ottobre 1896</div>
          <div class="tl-label">Nascita di Eugenio Montale</div>
          <span class="tl-tag tag-biografico">biografico</span>
          <div class="tl-desc">Eugenio Montale nasce a Genova il 12 ottobre 1896.</div>
        </div>
      </div>

      <div class="tl-event type-biografico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1905</div>
          <div class="tl-label">Nascita di Irma Brandeis</div>
          <span class="tl-tag tag-biografico">biografico</span>
          <div class="tl-desc">Irma Brandeis nasce a New York da una famiglia ebraica di origine austro-boema.</div>
        </div>
      </div>

      <div class="tl-event type-poetico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">15 giugno 1925</div>
          <div class="tl-label">Pubblicazione degli Ossi di seppia</div>
          <span class="tl-tag tag-poetico">poetico</span>
          <div class="tl-desc">Prima raccolta poetica di Montale, pubblicata da Gobetti. È il libro che Irma Brandeis cita come ragione del suo avvicinamento al poeta.</div>
        </div>
      </div>

      <div class="tl-event type-accademico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1929</div>
          <div class="tl-label">Montale direttore del Vieusseux</div>
          <span class="tl-tag tag-accademico">accademico</span>
          <div class="tl-desc">Montale viene nominato direttore del Gabinetto Scientifico Letterario G.P. Vieusseux di Firenze.</div>
        </div>
      </div>

      <div class="tl-event type-biografico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1931</div>
          <div class="tl-label">Primo soggiorno fiorentino di Irma Brandeis</div>
          <span class="tl-tag tag-biografico">biografico</span>
          <div class="tl-desc">Irma arriva a Firenze con l'intenzione di scrivere un libro sui suoi studi danteschi.</div>
        </div>
      </div>

      <div class="tl-event type-incontro" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1933</div>
          <div class="tl-label">Primo incontro al Vieusseux</div>
          <span class="tl-tag tag-incontro">incontro</span>
          <div class="tl-desc">Inizia la frequentazione quotidiana tra Irma e Montale: incontri al Doney, passeggiate e conversazioni su Pound, Eliot e l'America.</div>
        </div>
      </div>

      <div class="tl-event type-lettera" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">20 luglio 1933</div>
          <div class="tl-label">Lettera a Gino Bigongiari</div>
          <span class="tl-tag tag-lettera">lettera</span>
          <div class="tl-desc">«Sono ridicolmente felice.» Irma descrive il suo incontro con Montale e la vita fiorentina.</div>
        </div>
      </div>

      <div class="tl-event type-biografico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">agosto 1933</div>
          <div class="tl-label">Montale parte per Londra con Drusilla Tanzi</div>
          <span class="tl-tag tag-biografico">biografico</span>
          <div class="tl-desc">Montale soggiorna a Londra con Drusilla Tanzi, mentre Irma ancora ignora la loro relazione.</div>
        </div>
      </div>

      <div class="tl-event type-poetico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1939</div>
          <div class="tl-label">Pubblicazione de Le Occasioni</div>
          <span class="tl-tag tag-poetico">poetico</span>
          <div class="tl-desc">Montale pubblica Le Occasioni, dedicata a Irma Brandeis trasfigurata nella figura poetica di Clizia.</div>
        </div>
      </div>

      <div class="tl-event type-storico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1938</div>
          <div class="tl-label">Irma lascia l'Italia per le leggi razziali</div>
          <span class="tl-tag tag-storico">storico</span>
          <div class="tl-desc">Le leggi razziali fasciste rendono impossibile la permanenza di Irma in Italia.</div>
        </div>
      </div>

      <div class="tl-event type-accademico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1960</div>
          <div class="tl-label">Irma pubblica The Ladder of Vision</div>
          <span class="tl-tag tag-accademico">accademico</span>
          <div class="tl-desc">Volume fondamentale degli studi danteschi di Irma Brandeis.</div>
        </div>
      </div>

      <div class="tl-event type-morte" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1963</div>
          <div class="tl-label">Morte di Drusilla Tanzi</div>
          <span class="tl-tag tag-morte">morte</span>
          <div class="tl-desc">Muore Drusilla Tanzi, compagna e poi moglie di Montale.</div>
        </div>
      </div>

      <div class="tl-event type-critico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1965</div>
          <div class="tl-label">Montale cita The Ladder of Vision</div>
          <span class="tl-tag tag-critico">critico</span>
          <div class="tl-desc">Montale definisce il libro di Irma «quanto di più suggestivo» avesse letto sull'argomento.</div>
        </div>
      </div>

      <div class="tl-event type-poetico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1971</div>
          <div class="tl-label">Montale pubblica Satura</div>
          <span class="tl-tag tag-poetico">poetico</span>
          <div class="tl-desc">La raccolta poetica dedicata a Drusilla Tanzi trasfigurata in Xenia.</div>
        </div>
      </div>

      <div class="tl-event type-storico" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1975</div>
          <div class="tl-label">Montale riceve il Premio Nobel</div>
          <span class="tl-tag tag-storico">storico</span>
          <div class="tl-desc">Eugenio Montale riceve il Premio Nobel per la Letteratura.</div>
        </div>
      </div>

      <div class="tl-event type-lettera" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1980</div>
          <div class="tl-label">Annotazioni sul nome Clizia</div>
          <span class="tl-tag tag-lettera">lettera</span>
          <div class="tl-desc">Irma rifiuta l'identificazione assoluta con la figura poetica di Clizia.</div>
        </div>
      </div>

      <div class="tl-event type-lettera" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1981</div>
          <div class="tl-label">Ultimo biglietto di Montale</div>
          <span class="tl-tag tag-lettera">lettera</span>
          <div class="tl-desc">«Irma, sei ancora la mia dea, la mia divinità.»</div>
        </div>
      </div>

      <div class="tl-event type-morte" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">12 settembre 1981</div>
          <div class="tl-label">Morte di Eugenio Montale</div>
          <span class="tl-tag tag-morte">morte</span>
          <div class="tl-desc">Montale muore nel settembre del 1981.</div>
        </div>
      </div>

      <div class="tl-event type-morte" onclick="toggle(this)">
        <div class="tl-dot-wrap"><div class="tl-dot"></div></div>
        <div class="tl-inner">
          <div class="tl-date">1990</div>
          <div class="tl-label">Morte di Irma Brandeis</div>
          <span class="tl-tag tag-morte">morte</span>
          <div class="tl-desc">Irma Brandeis muore ad Annandale-on-Hudson nel 1990.</div>
        </div>
      </div>

    </div>
  </main>
</div>

<script>
function toggle(el) {
  const wasActive = el.classList.contains('active');
  document.querySelectorAll('.tl-event').forEach(e => e.classList.remove('active'));
  if (!wasActive) el.classList.add('active');
}

let activeFilter = null;

function filterType(type, item) {
  if (activeFilter === type) {
    showAll();
    return;
  }

  activeFilter = type;

  document.querySelectorAll('.legend-item').forEach(l => l.classList.add('inactive'));
  item.classList.remove('inactive');

  document.querySelectorAll('.tl-event').forEach(ev => {
    if (ev.classList.contains('type-' + type)) {
      ev.classList.remove('hidden');
    } else {
      ev.classList.add('hidden');
      ev.classList.remove('active');
    }
  });
}

function showAll() {
  activeFilter = null;

  document.querySelectorAll('.legend-item').forEach(l =>
    l.classList.remove('inactive')
  );

  document.querySelectorAll('.tl-event').forEach(ev =>
    ev.classList.remove('hidden')
  );
}
</script>

</body>
</html>
```

