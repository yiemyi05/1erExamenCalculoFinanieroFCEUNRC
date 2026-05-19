[index.html](https://github.com/user-attachments/files/28013441/index.html)
# 1erExamenCalculoFinanieroFCEUNRC<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Portal de Examen</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;900&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>

  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --navy: #0f1b2d;
      --deep: #162236;
      --card: #1a2a42;
      --accent1: #4f8ef7;
      --accent2: #00d4aa;
      --gold: #f5c842;
      --text: #e8edf5;
      --muted: #7a93b4;
    }

    body {
      font-family: 'DM Sans', sans-serif;
      background: var(--navy);
      color: var(--text);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      overflow: hidden;
      position: relative;
    }

    .bg-orb {
      position: fixed;
      border-radius: 50%;
      filter: blur(80px);
      opacity: 0.18;
      animation: float 10s ease-in-out infinite;
      pointer-events: none;
    }

    .bg-orb.o1 { width: 500px; height: 500px; background: #4f8ef7; top: -100px; left: -150px; animation-delay: 0s; }
    .bg-orb.o2 { width: 400px; height: 400px; background: #00d4aa; bottom: -100px; right: -100px; animation-delay: 3s; }
    .bg-orb.o3 { width: 300px; height: 300px; background: #f5c842; top: 40%; left: 55%; animation-delay: 6s; }

    @keyframes float {
      0%, 100% { transform: translateY(0) scale(1); }
      50% { transform: translateY(-30px) scale(1.05); }
    }

    .dots {
      position: fixed;
      inset: 0;
      background-image: radial-gradient(circle, rgba(255,255,255,0.06) 1px, transparent 1px);
      background-size: 32px 32px;
      pointer-events: none;
    }

    .container {
      position: relative;
      z-index: 10;
      text-align: center;
      padding: 2rem;
      max-width: 720px;
      width: 100%;
      animation: fadeUp 0.8s ease both;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(79,142,247,0.15);
      border: 1px solid rgba(79,142,247,0.35);
      border-radius: 999px;
      padding: 6px 18px;
      font-size: 0.8rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent1);
      margin-bottom: 1.5rem;
      animation: fadeUp 0.8s 0.1s ease both;
    }

    .badge-dot {
      width: 7px;
      height: 7px;
      background: var(--accent1);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0%, 100% { opacity: 1; transform: scale(1); }
      50% { opacity: 0.4; transform: scale(0.7); }
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.2rem, 5vw, 3.2rem);
      font-weight: 900;
      line-height: 1.15;
      margin-bottom: 0.6rem;
      animation: fadeUp 0.8s 0.2s ease both;
      background: linear-gradient(135deg, #e8edf5 30%, #4f8ef7 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
    }

    .subtitle {
      color: var(--muted);
      font-size: 1rem;
      font-weight: 300;
      margin-bottom: 3rem;
      animation: fadeUp 0.8s 0.3s ease both;
    }

    .divider {
      width: 60px;
      height: 3px;
      background: linear-gradient(90deg, var(--accent1), var(--accent2));
      border-radius: 2px;
      margin: 0 auto 2.8rem;
      animation: fadeUp 0.8s 0.35s ease both;
    }

    .cards {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 1.4rem;
      animation: fadeUp 0.8s 0.4s ease both;
    }

    .card {
      background: var(--card);
      border: 1px solid rgba(255,255,255,0.07);
      border-radius: 20px;
      padding: 2.2rem 1.8rem 2rem;
      color: var(--text);
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
      position: relative;
      overflow: hidden;
      transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
    }

    .card::before {
      content: '';
      position: absolute;
      inset: 0;
      opacity: 0;
      transition: opacity 0.3s ease;
      border-radius: 20px;
      pointer-events: none;
    }

    .card.forms::before { background: radial-gradient(circle at 50% 0%, rgba(79,142,247,0.18), transparent 70%); }
    .card.excel::before { background: radial-gradient(circle at 50% 0%, rgba(0,212,170,0.18), transparent 70%); }

    .card:hover {
      transform: translateY(-6px);
      box-shadow: 0 24px 48px rgba(0,0,0,0.4);
    }

    .card.forms:hover { border-color: rgba(79,142,247,0.5); box-shadow: 0 24px 48px rgba(79,142,247,0.15); }
    .card.excel:hover { border-color: rgba(0,212,170,0.5); box-shadow: 0 24px 48px rgba(0,212,170,0.15); }
    .card:hover::before { opacity: 1; }

    .icon-wrap {
      width: 76px;
      height: 76px;
      border-radius: 18px;
      display: flex;
      align-items: center;
      justify-content: center;
      position: relative;
      z-index: 1;
    }

    .card.forms .icon-wrap { background: linear-gradient(135deg, #1565c0, #4f8ef7); box-shadow: 0 8px 24px rgba(79,142,247,0.35); }
    .card.excel .icon-wrap { background: linear-gradient(135deg, #0a5c41, #00d4aa); box-shadow: 0 8px 24px rgba(0,212,170,0.35); }

    .icon-wrap svg { width: 38px; height: 38px; }

    .card-label {
      font-size: 0.72rem;
      font-weight: 500;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      opacity: 0.5;
      position: relative;
      z-index: 1;
    }

    .card-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.25rem;
      font-weight: 700;
      line-height: 1.2;
      position: relative;
      z-index: 1;
    }

    .card-desc {
      font-size: 0.82rem;
      color: var(--muted);
      line-height: 1.5;
      position: relative;
      z-index: 1;
    }

    .card-btn {
      margin-top: 0.5rem;
      padding: 9px 22px;
      border-radius: 999px;
      font-size: 0.82rem;
      font-weight: 500;
      border: none;
      cursor: pointer;
      transition: opacity 0.2s, transform 0.2s;
      text-decoration: none;
      display: inline-block;
      position: relative;
      z-index: 2;
    }

    .card.forms .card-btn { background: var(--accent1); color: #fff; }
    .card.excel .card-btn { background: var(--accent2); color: #0a2a1f; }
    .card-btn:hover { opacity: 0.88; transform: scale(1.04); }

    .arrow {
      position: absolute;
      bottom: 16px;
      right: 18px;
      opacity: 0;
      transform: translateX(-6px);
      transition: opacity 0.3s, transform 0.3s;
      font-size: 1.1rem;
    }

    .card.forms .arrow { color: var(--accent1); }
    .card.excel .arrow { color: var(--accent2); }
    .card:hover .arrow { opacity: 1; transform: translateX(0); }

    .footer {
      margin-top: 2.8rem;
      font-size: 0.75rem;
      color: var(--muted);
      opacity: 0.6;
      animation: fadeUp 0.8s 0.55s ease both;
    }

    @media (max-width: 520px) {
      body { overflow: auto; }
      .cards { grid-template-columns: 1fr; }
      .container { padding: 1.4rem; }
    }
  </style>
</head>

<body>

  <div class="bg-orb o1"></div>
  <div class="bg-orb o2"></div>
  <div class="bg-orb o3"></div>
  <div class="dots"></div>

  <div class="container">

    <div class="badge">
      <span class="badge-dot"></span>
      Examen en curso
    </div>

    <h1>Portal de Evaluación</h1>
    <p class="subtitle">Seleccioná la herramienta que necesitás para completar tu examen</p>
    <div class="divider"></div>

    <div class="cards">

      <article class="card forms">
        <div class="icon-wrap">
          <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="6" y="4" width="28" height="40" rx="3" fill="white" fill-opacity="0.15"/>
            <rect x="6" y="4" width="28" height="40" rx="3" stroke="white" stroke-opacity="0.4" stroke-width="1.5"/>
            <rect x="12" y="13" width="16" height="2.5" rx="1.25" fill="white" fill-opacity="0.9"/>
            <rect x="12" y="20" width="16" height="2.5" rx="1.25" fill="white" fill-opacity="0.7"/>
            <rect x="12" y="27" width="10" height="2.5" rx="1.25" fill="white" fill-opacity="0.5"/>
            <circle cx="38" cy="38" r="8" fill="#4f8ef7"/>
            <path d="M34.5 38l2.5 2.5 4.5-4.5" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
        </div>

        <span class="card-label">Paso 1</span>
        <span class="card-title">Formulario del Examen</span>
        <p class="card-desc">Completá las preguntas del cuestionario en Microsoft Forms.</p>

        <a class="card-btn" href="https://forms.office.com/pages/responsepage.aspx?id=mUZ9H9fM1kW8eLi5ULyu3IKMINbC58NOrHOCtZI_DVBUODI2SzRGTENJR0NMUjhSRkI0OE4zQUIyMC4u&route=shorturl" target="_blank" rel="noopener">
          Abrir Formulario
        </a>

        <span class="arrow">→</span>
      </article>

      <article class="card excel">
        <div class="icon-wrap">
          <svg viewBox="0 0 48 48" fill="none" xmlns="http://www.w3.org/2000/svg">
            <rect x="6" y="4" width="28" height="40" rx="3" fill="white" fill-opacity="0.12"/>
            <rect x="6" y="4" width="28" height="40" rx="3" stroke="white" stroke-opacity="0.35" stroke-width="1.5"/>
            <line x1="6" y1="16" x2="34" y2="16" stroke="white" stroke-opacity="0.2" stroke-width="1.2"/>
            <line x1="6" y1="24" x2="34" y2="24" stroke="white" stroke-opacity="0.2" stroke-width="1.2"/>
            <line x1="6" y1="32" x2="34" y2="32" stroke="white" stroke-opacity="0.2" stroke-width="1.2"/>
            <line x1="20" y1="4" x2="20" y2="44" stroke="white" stroke-opacity="0.2" stroke-width="1.2"/>
            <path d="M11 20l4.5 7L11 34" stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
            <path d="M17 20l4.5 7L17 34" stroke="white" stroke-opacity="0.6" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" fill="none"/>
            <circle cx="38" cy="38" r="8" fill="#00d4aa"/>
            <rect x="34.5" y="36" width="7" height="1.8" rx="0.9" fill="white"/>
            <rect x="34.5" y="39.2" width="7" height="1.8" rx="0.9" fill="white"/>
          </svg>
        </div>

        <span class="card-label">Paso 2</span>
        <span class="card-title">Excel en la Nube</span>
        <p class="card-desc">Creá tu propio archivo Excel online para resolver el examen.</p>

        <a class="card-btn" href="https://excel.new/" target="_blank" rel="noopener">
          Crear mi Excel
        </a>

        <span class="arrow">→</span>
      </article>

    </div>

    <p class="footer">🔒 Entorno seguro · Universidad Nacional de Río Cuarto - Facultad de Ciencias Económicas · Evaluación supervisada</p>

  </div>

</body>
</html>
