<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Flashcard — Prazos de Uso da Palavra no Plenário</title>
<link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700;800&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  *{margin:0;padding:0;box-sizing:border-box;}

  body {
    background: #1a1a28;
    font-family: 'DM Sans', system-ui, sans-serif;
    min-height: 100vh;
    display: flex;
    align-items: flex-start;
    justify-content: center;
    padding: 2rem 1rem;
  }

  .card {
    width: 100%;
    max-width: 700px;
    border-radius: 18px;
    overflow: hidden;
    box-shadow: 0 8px 48px rgba(0,0,0,0.6);
    background: #fafaf8;
  }

  /* ── BANNER ── */
  .banner {
    background: #111120;
    padding: 11px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 6px;
  }
  .banner-subject {
    font-size: 0.58rem;
    font-weight: 700;
    letter-spacing: 0.14em;
    text-transform: uppercase;
    color: #5555aa;
  }
  .badge-row { display:flex; gap:6px; flex-wrap:wrap; }
  .badge {
    font-size: 0.6rem;
    font-weight: 800;
    padding: 3px 10px;
    border-radius: 20px;
    letter-spacing: 0.04em;
  }
  .badge-arts { background: #2a2a4a; color: #9999dd; }
  .badge-hot  { background: #ff4466; color: #fff; }

  /* ── QUESTION ── */
  .question {
    padding: 22px 24px 18px;
    border-bottom: 2px solid #eeeef4;
    background: #fff;
  }
  .question p {
    font-size: 1.08rem;
    font-weight: 700;
    color: #111128;
    line-height: 1.4;
  }

  /* ── SECTION LABEL ── */
  .sec-label {
    font-size: 0.6rem;
    font-weight: 800;
    letter-spacing: 0.13em;
    text-transform: uppercase;
    color: #8888aa;
    padding: 14px 24px 6px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .sec-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: #e8e8f2;
  }

  /* ── GRID OF CARDS ── */
  .cards-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    padding: 0 20px 4px;
  }
  @media(max-width:500px){ .cards-grid{ grid-template-columns: 1fr; } }

  .pcard {
    border-radius: 12px;
    padding: 12px 14px;
    display: flex;
    align-items: flex-start;
    gap: 12px;
    border: 1.5px solid transparent;
  }

  /* phase colors */
  .pc-exp   { background:#eeeeff; border-color:#ccccff; }
  .pc-com   { background:#fff5e0; border-color:#ffe0a0; }
  .pc-dis   { background:#e8fff0; border-color:#a0ecc0; }
  .pc-vot   { background:#fff0f0; border-color:#ffcccc; }
  .pc-ord   { background:#f0f8ff; border-color:#b8d8f8; }
  .pc-misc  { background:#f5f0ff; border-color:#d4b8ff; }

  .pcard-icon {
    font-size: 1.4rem;
    flex-shrink: 0;
    line-height: 1;
    margin-top: 2px;
  }

  .pcard-body { flex: 1; }

  .pcard-name {
    font-size: 0.8rem;
    font-weight: 700;
    color: #222240;
    line-height: 1.25;
    margin-bottom: 4px;
  }
  .pcard-art {
    font-size: 0.62rem;
    font-family: 'DM Mono', monospace;
    font-weight: 500;
    color: #9999bb;
    margin-bottom: 5px;
  }

  .time-row {
    display: flex;
    align-items: baseline;
    gap: 4px;
    flex-wrap: wrap;
    margin-bottom: 3px;
  }
  .time-num {
    font-size: 1.6rem;
    font-weight: 800;
    line-height: 1;
    font-family: 'DM Mono', monospace;
  }
  .time-unit {
    font-size: 0.72rem;
    font-weight: 600;
    color: #666;
    margin-left: 1px;
  }
  .time-qual {
    font-size: 0.67rem;
    color: #888;
    font-weight: 500;
  }

  /* color per phase */
  .pc-exp  .time-num  { color: #4444cc; }
  .pc-com  .time-num  { color: #cc7700; }
  .pc-dis  .time-num  { color: #1a8040; }
  .pc-vot  .time-num  { color: #cc2244; }
  .pc-ord  .time-num  { color: #1166cc; }
  .pc-misc .time-num  { color: #7733cc; }

  .sub-rows { margin-top:4px; }
  .sub-row {
    font-size: 0.72rem;
    color: #444;
    padding: 2px 0;
    display: flex;
    align-items: center;
    gap: 6px;
    line-height: 1.3;
  }
  .sub-row::before {
    content:'▸';
    font-size: 0.6rem;
    flex-shrink:0;
    opacity:.5;
  }

  .tag {
    display:inline-block;
    padding:1px 7px;
    border-radius:20px;
    font-size:0.62rem;
    font-weight:700;
    white-space:nowrap;
  }
  .tag-urg  { background:#ffd0d8; color:#aa1030; }
  .tag-lid  { background:#d8d8ff; color:#3030aa; }
  .tag-any  { background:#e8f8e8; color:#1a6030; }

  /* ── URGÊNCIA NOTE ── */
  .urg-banner {
    margin: 4px 20px 12px;
    background: linear-gradient(90deg, #fff0f3, #fff8f0);
    border: 1.5px solid #ffb8c8;
    border-radius: 10px;
    padding: 10px 14px;
    display: flex;
    align-items: center;
    gap: 10px;
    font-size: 0.78rem;
    color: #6a1030;
    line-height: 1.5;
  }
  .urg-banner .urg-icon { font-size: 1.1rem; flex-shrink:0; }
  .urg-banner strong { color: #aa1030; }

  /* ── CEBRASPE ── */
  .cebraspe {
    background: #fffcec;
    border-top: 2px solid #ffe58a;
    padding: 14px 20px 16px;
  }
  .ceb-label {
    font-size: 0.6rem;
    font-weight: 800;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    color: #c87800;
    margin-bottom: 10px;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .trap-grid {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    gap: 7px;
  }
  @media(max-width:520px){ .trap-grid{ grid-template-columns: 1fr 1fr; } }
  .trap {
    background: #fff;
    border: 1.5px solid #ffe090;
    border-radius: 9px;
    padding: 9px 10px;
    font-size: 0.73rem;
    color: #4a3600;
    line-height: 1.45;
  }
  .trap strong { color: #1a1a00; font-weight: 700; }
  .trap .wrong { color: #cc2200; text-decoration: line-through; font-size: 0.68rem; }
  .trap .right { color: #1a6a20; font-weight: 700; }

  /* ── FOOTER ── */
  .lei-seca {
    background: #f5f5ea;
    border-top: 1.5px solid #e0e0c0;
    padding: 10px 20px;
    font-size: 0.71rem;
    color: #5a5a30;
    line-height: 1.5;
  }
  .lei-seca strong { color: #3a3a10; }
</style>
</head>
<body>
<div class="card">

  <!-- BANNER -->
  <div class="banner">
    <span class="banner-subject">RICD &nbsp;·&nbsp; Sessão Plenária &nbsp;·&nbsp; Uso da Palavra</span>
    <div class="badge-row">
      <span class="badge badge-arts">Arts. 81, 87, 89, 90, 95, 96, 157, 174, 192</span>
      <span class="badge badge-hot">⚡ Todos os prazos atualizados</span>
    </div>
  </div>

  <!-- QUESTION -->
  <div class="question">
    <p>Quais são <em>todos</em> os prazos de uso da palavra para um Deputado no Plenário da Câmara?</p>
  </div>

  <!-- EXPEDIENTE -->
  <div class="sec-label">📋 Fase do Expediente</div>
  <div class="cards-grid">

    <div class="pcard pc-exp">
      <div class="pcard-icon">🗂</div>
      <div class="pcard-body">
        <div class="pcard-name">Pequeno Expediente</div>
        <div class="pcard-art">Art. 81, caput</div>
        <div class="time-row">
          <span class="time-num">5</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row"><span class="tag tag-any">Qualquer Dep.</span> inscrito</div>
          <div class="sub-row">Vedados os apartes</div>
        </div>
      </div>
    </div>

    <div class="pcard pc-exp">
      <div class="pcard-icon">🎙</div>
      <div class="pcard-body">
        <div class="pcard-name">Grande Expediente</div>
        <div class="pcard-art">Art. 87, caput</div>
        <div class="time-row">
          <span class="time-num">25</span><span class="time-unit">min</span>
          <span class="time-qual">por orador</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Bloco de 50 min dividido entre <strong>2 oradores</strong> inscritos</div>
          <div class="sub-row">Cada um fala até 25 min (apartes inclusos)</div>
        </div>
      </div>
    </div>

  </div>

  <!-- COMUNICAÇÕES -->
  <div class="sec-label">📢 Comunicações</div>
  <div class="cards-grid">

    <div class="pcard pc-com">
      <div class="pcard-icon">👔</div>
      <div class="pcard-body">
        <div class="pcard-name">Comunicações de Lideranças</div>
        <div class="pcard-art">Art. 89</div>
        <div class="time-row">
          <span class="time-num" style="font-size:1.3rem;">3 a 10</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Proporcional; Gov/Minoria/Maioria/Oposição: 8 min</div>
          <div class="sub-row">Sem Liderança: 5 min/semana</div>
          <div class="sub-row">Banc. Negra/Mulher/Infância: 5 min/semana</div>
        </div>
      </div>
    </div>

    <div class="pcard pc-com">
      <div class="pcard-icon">💬</div>
      <div class="pcard-body">
        <div class="pcard-name">Comunicações Parlamentares</div>
        <div class="pcard-art">Art. 90, Parágrafo único</div>
        <div class="time-row">
          <span class="time-num">10</span><span class="time-unit">min</span>
          <span class="time-qual">máximo</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Oradores indicados pelos Líderes</div>
          <div class="sub-row">Após a Ordem do Dia, se houver tempo</div>
        </div>
      </div>
    </div>

  </div>

  <!-- DISCUSSÃO -->
  <div class="sec-label">📖 Fase de Discussão (Ordem do Dia)</div>
  <div class="cards-grid">

    <div class="pcard pc-dis">
      <div class="pcard-icon">⚖️</div>
      <div class="pcard-body">
        <div class="pcard-name">Discussão de proposição</div>
        <div class="pcard-art">Art. 174, caput e §4º</div>
        <div class="time-row">
          <span class="time-num">5</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Prorrogável no máximo pela metade (+2,5 min)</div>
          <div class="sub-row"><span class="tag tag-urg">Urgência</span> 3 min (Art. 157, §3º)</div>
        </div>
      </div>
    </div>

    <div class="pcard pc-dis">
      <div class="pcard-icon">💭</div>
      <div class="pcard-body">
        <div class="pcard-name">Aparte</div>
        <div class="pcard-art">Art. 176, caput e §3º</div>
        <div class="time-row">
          <span class="time-num" style="font-size:1.3rem;">Breve</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Não há limite fixo de "1 min" no RICD</div>
          <div class="sub-row">Descontado do tempo do orador</div>
        </div>
      </div>
    </div>

  </div>

  <!-- VOTAÇÃO -->
  <div class="sec-label">🗳 Fase de Votação</div>
  <div class="cards-grid">

    <div class="pcard pc-vot">
      <div class="pcard-icon">🏛</div>
      <div class="pcard-body">
        <div class="pcard-name">Encaminhamento de votação</div>
        <div class="pcard-art">Art. 192, caput e §1º</div>
        <div class="time-row">
          <span class="time-num">3</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Até 4 oradores (2 a favor, 2 contra)</div>
          <div class="sub-row"><span class="tag tag-urg">Urgência</span> 3 min (Art. 157, §3º)</div>
        </div>
      </div>
    </div>

    <div class="pcard pc-vot">
      <div class="pcard-icon">📌</div>
      <div class="pcard-body">
        <div class="pcard-name">Orientação de bancada</div>
        <div class="pcard-art">Arts. 10, IV e 192, §2º</div>
        <div class="time-row">
          <span class="time-num">1</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Exclusividade do <span class="tag tag-lid">Líder</span> (ou delegado)</div>
          <div class="sub-row">Feita durante qualquer votação</div>
        </div>
      </div>
    </div>

  </div>

  <!-- ORDEM E RECLAMAÇÃO -->
  <div class="sec-label">⚙️ Questões Processuais</div>
  <div class="cards-grid">

    <div class="pcard pc-ord">
      <div class="pcard-icon">❓</div>
      <div class="pcard-body">
        <div class="pcard-name">Questão de Ordem</div>
        <div class="pcard-art">Art. 95, §2º</div>
        <div class="time-row">
          <span class="time-num">3</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Dúvida sobre interpretação do RICD/CF</div>
          <div class="sub-row">Decisão pelo Presidente da sessão</div>
        </div>
      </div>
    </div>

    <div class="pcard pc-ord">
      <div class="pcard-icon">📣</div>
      <div class="pcard-body">
        <div class="pcard-name">Reclamação</div>
        <div class="pcard-art">Art. 96, §3º</div>
        <div class="time-row">
          <span class="time-num">3</span><span class="time-unit">min</span>
        </div>
        <div class="sub-rows">
          <div class="sub-row">Aplica-se a mesma norma da Q.O.</div>
          <div class="sub-row">Para reclamar de inobservância regimental</div>
        </div>
      </div>
    </div>

  </div>

  <!-- URGÊNCIA RULE -->
  <div class="urg-banner">
    <span class="urg-icon">⚡</span>
    <span><strong>Regra da Urgência:</strong> Na discussão e no encaminhamento de votação de proposição em regime de urgência, o tempo é fixado em <strong>3 minutos</strong> por orador (Art. 157, §3º), sendo <strong>vedada</strong> a prorrogação do prazo na discussão (Art. 174, §4º).</span>
  </div>

  <!-- CEBRASPE -->
  <div class="cebraspe">
    <div class="ceb-label">⚠ Armadilhas CEBRASPE</div>
    <div class="trap-grid">
      <div class="trap">
        <strong>Pequeno Expediente = 3 min?</strong><br>
        <span class="wrong">Errado</span>.<br>
        RICD fixa em <span class="right">5 minutos</span> (Art. 81).
      </div>
      <div class="trap">
        <strong>Discussão em Urgência:</strong><br>
        Cai pela metade (2,5 min)? <span class="wrong">Errado</span>. O tempo é expressamente fixado em <span class="right">3 minutos</span> (Art. 157).
      </div>
      <div class="trap">
        <strong>Reclamação = 1 minuto?</strong><br>
        <span class="wrong">Errado</span>. Aplicam-se as regras da Questão de Ordem, logo o prazo é de <span class="right">3 minutos</span>.
      </div>
      <div class="trap">
        <strong>Líder no encam. de votação:</strong><br>
        Tem 10 min? <span class="wrong">Errado</span>. Para <i>orientar a bancada</i> o tempo não pode exceder a <span class="right">1 minuto</span>.
      </div>
      <div class="trap">
        <strong>Aparte tem 1 minuto?</strong><br>
        <span class="wrong">Errado</span>. O RICD exige apenas que seja "breve e oportuno", sendo descontado do tempo do orador.
      </div>
      <div class="trap">
        <strong>Comunicações Parlamentares:</strong><br>
        É de 5 min? <span class="wrong">Errado</span>. É de período não excedente a <span class="right">10 minutos</span> para cada Deputado.
      </div>
    </div>
  </div>

  <!-- LEI SECA -->
  <div class="lei-seca">
    <strong>Lei Seca:</strong> Art. 81 (Peq. Exp. – 5 min) · Art. 87 (Gr. Exp. – 25 min) · Art. 89 (Com. Lideranças – 3 a 10 min proporcional) · Art. 90 (Com. Parlamentares – 10 min) · Art. 95 (Questão de Ordem – 3 min) · Art. 96 (Reclamação – 3 min) · Art. 174 (Discussão – 5 min, prorroga ½) · Art. 157 (Urgência discussão/encaminhamento – 3 min) · Art. 176 (Aparte – breve) · Art. 192 (Encaminhamento votação – 3 min) · Art. 10 (Orientação de bancada – 1 min).
  </div>

</div>
</body>
</html>