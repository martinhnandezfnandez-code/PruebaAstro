---
setup: |
  import Layout from '../../layouts/BlogPost.astro'
title: Manuel Barrera
publishDate: 27 May 2022
value: 128
cover: https://assets.warhammer-community.com/40k_knightsindex-jun18-image1_wide-3z9qlgmgvg.jpg
description: Imperial Knights

---

---
// Imperium_Adeptus_Titanicus_List.astro
// Componente Astro que renderiza la lista de ejército proporcionada.
const list = {
  faction: 'Imperium — Adeptus Titanicus',
  points: 3330,
  allied: 'Unaligned Forces & Imperial Knights',
  units: [
    { name: 'Plasma Obliterator', tag: '[Legends]', pts: 225, equip: ['1× Plasma obliterator'] },
    { name: 'Primaris Redoubt', tag: '[Legends]', pts: 220, equip: ['1× Primaris Redoubt turbo-laser destructor'] },
    { name: 'Ambull', tag: '[Legends]', pts: 85, equip: ['1× Enormous claws'] },
    // cuatro Acastus Knight Porphyrion idénticos
    ...Array.from({ length: 4 }).map(() => ({
      name: 'Acastus Knight Porphyrion',
      pts: 700,
      equip: [
        '1× Titanic feet',
        '2× Twin magna lascannon',
        '2× Acastus autocannon',
        '1× Acastus ironstorm missile pod'
      ]
    }))
  ],
  secondaries: [
    'Bring It Down: (1x2) + (2x4) + (4x6)',
    'Assassination: 1 Characters'
  ]
};
---

<html lang="es">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>{list.faction} — Lista {list.points}pts</title>
    <style>
      :root{--bg:#0f1724;--card:#0b1220;--muted:#9aa4b2;--accent:#d1af37;--glass:rgba(255,255,255,0.03)}
      *{box-sizing:border-box}
      body{margin:0;font-family:Inter,system-ui,Segoe UI,Roboto,Arial;background:linear-gradient(180deg,#071025 0%, #081426 100%);color:#e6eef6;line-height:1.45;padding:28px}
      .container{max-width:980px;margin:0 auto}
      header{display:flex;gap:18px;align-items:center;margin-bottom:20px}
      .badge{background:var(--glass);padding:10px 14px;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}
      h1{margin:0;font-size:20px}
      .meta{margin-left:auto;text-align:right;color:var(--muted);font-size:13px}
      .grid{display:grid;grid-template-columns:1fr 320px;gap:18px}
      .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));padding:16px;border-radius:12px;border:1px solid rgba(255,255,255,0.03)}
      .section-title{font-size:14px;color:var(--accent);margin-bottom:8px}
      dl{display:grid;grid-template-columns:130px 1fr;gap:6px 12px}
      dt{color:var(--muted);font-size:13px}
      dd{margin:0;font-weight:600}
      .unit-list{display:flex;flex-direction:column;gap:10px}
      .unit{padding:12px;border-radius:10px;background:rgba(255,255,255,0.01);border:1px solid rgba(255,255,255,0.02)}
      .unit h3{margin:0;font-size:15px}
      .unit .pts{color:var(--muted);font-size:13px}
      ul.equip{margin:8px 0 0 18px;color:var(--muted)}
      footer{margin-top:18px;color:var(--muted);font-size:13px}
      @media (max-width:880px){.grid{grid-template-columns:1fr}}
    </style>
  </head>
  <body>
    <div class="container">
      <header>
        <div class="badge">
          <h1>{list.faction}</h1>
          <div style="color:var(--muted);font-size:13px">Lista de ejército</div>
        </div>
        <div class="meta">
          <div><strong>PTS</strong> {list.points}pts</div>
          <div><strong>Allied</strong> {list.allied}</div>
          <div style="margin-top:6px;color:var(--muted);font-size:12px">UNITS: {list.units.length} • Enhancement: —</div>
        </div>
      </header>

      <div class="grid">
        <main>
          <section class="card">
            <div class="section-title">Resumen de misiones secundarias</div>
            <pre style="white-space:pre-wrap;color:var(--muted);margin:0;font-size:13px">{list.secondaries.join('
')}</pre>
          </section>

          <section class="card" style="margin-top:12px">
            <div class="section-title">Datasheets / Unidades</div>
            <div class="unit-list" style="margin-top:8px">
              {list.units.map((u, i) => (
                <article class="unit" key={i}>
                  <h3>{u.name} {u.tag ? <span class="pts">{u.tag} — {u.pts} pts</span> : <span class="pts">— {u.pts} pts</span>}</h3>
                  <ul class="equip">
                    {u.equip.map((e, j) => <li key={j}>{e}</li>)}
                  </ul>
                </article>
              ))}
            </div>
          </section>

        </main>

        <aside>
          <div class="card">
            <div class="section-title">Datos rápidos</div>
            <dl>
              <dt>Faction</dt><dd>{list.faction}</dd>
              <dt>Total points</dt><dd>{list.points}pts</dd>
              <dt>Allied units</dt><dd>{list.allied}</dd>
              <dt>Number of units</dt><dd>{list.units.length}</dd>
              <dt>Enhancement</dt><dd>—</dd>
            </dl>
            <hr style="margin:12px 0;border:none;border-top:1px solid rgba(255,255,255,0.03)">
            <div class="section-title">Resumen puntos por unidad</div>
            <ul style="margin:8px 0 0 18px;color:var(--muted);font-size:14px">
              {list.units.map((u, idx) => <li key={idx}>{u.name} — {u.pts} pts</li>)}
            </ul>
          </div>

          <div class="card" style="margin-top:12px">
            <div class="section-title">Notas</div>
            <p style="color:var(--muted);font-size:13px;margin:0">Este archivo es un componente .astro listo para usar en un proyecto Astro. Opciones que puedo aplicar:</p>
            <ul style="color:var(--muted);margin-top:8px">
              <li>Separar las 4 Acastus Knight en entradas individuales (actualmente están listadas como 4 elementos iguales).</li>
              <li>Añadir campos para reglas o perfiles si me das esos datos.</li>
              <li>Exportar a HTML estático o generar una versión imprimible.</li>
            </ul>
          </div>
        </aside>
      </div>

      <footer>
        Exportado automáticamente — lista base proporcionada por el usuario.
      </footer>
    </div>
  </body>
</html>

