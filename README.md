<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Planner — Condomínio Rua Uchôa</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d0f14;
    --surface: #151820;
    --surface2: #1c2030;
    --border: #252a3a;
    --gold: #c9a84c;
    --gold-light: #e8c96a;
    --gold-dim: #8a6e2e;
    --green: #3ddc84;
    --green-dim: #1e6640;
    --orange: #ff8c42;
    --orange-dim: #7a3e18;
    --blue: #4a9eff;
    --blue-dim: #1a3d6e;
    --red: #ff5252;
    --text: #e8ecf4;
    --text-dim: #8892a4;
    --text-muted: #4a5268;
    --radius: 10px;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'Space Mono', monospace;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* HEADER */
  header {
    background: linear-gradient(135deg, #0d0f14 0%, #151820 50%, #1a1f2e 100%);
    border-bottom: 1px solid var(--border);
    padding: 28px 24px 20px;
    position: relative;
    overflow: hidden;
  }
  header::before {
    content: '';
    position: absolute;
    top: -40px; right: -40px;
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(201,168,76,0.12) 0%, transparent 70%);
    pointer-events: none;
  }
  .header-tag {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 3px;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  header h1 {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 800;
    color: var(--text);
    line-height: 1.2;
  }
  header h1 span { color: var(--gold); }
  .header-sub {
    font-size: 11px;
    color: var(--text-dim);
    margin-top: 4px;
  }

  /* TABS */
  .tabs {
    display: flex;
    background: var(--surface);
    border-bottom: 1px solid var(--border);
    overflow-x: auto;
    scrollbar-width: none;
  }
  .tabs::-webkit-scrollbar { display: none; }
  .tab {
    padding: 12px 16px;
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 1px;
    text-transform: uppercase;
    color: var(--text-muted);
    cursor: pointer;
    border-bottom: 2px solid transparent;
    white-space: nowrap;
    transition: all 0.2s;
    flex-shrink: 0;
  }
  .tab.active {
    color: var(--gold);
    border-bottom-color: var(--gold);
  }
  .tab:hover:not(.active) { color: var(--text-dim); }

  /* MAIN */
  main { padding: 20px 16px; max-width: 800px; margin: 0 auto; }

  /* SECTION */
  .section { display: none; }
  .section.active { display: block; }

  /* CARDS */
  .card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 12px;
  }
  .card-title {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    color: var(--gold);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 12px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .card-title .icon { font-size: 16px; }

  /* METRICS GRID */
  .metrics {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 10px;
    margin-bottom: 12px;
  }
  .metric {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 8px;
    padding: 12px;
  }
  .metric-label {
    font-size: 9px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 4px;
  }
  .metric-value {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 800;
    color: var(--text);
    line-height: 1;
  }
  .metric-value.gold { color: var(--gold); }
  .metric-value.green { color: var(--green); }
  .metric-value.orange { color: var(--orange); }
  .metric-sub {
    font-size: 10px;
    color: var(--text-muted);
    margin-top: 2px;
  }

  /* PERMUTA TABLE */
  .permuta-row {
    display: grid;
    grid-template-columns: 1fr auto auto;
    gap: 8px;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 11px;
  }
  .permuta-row:last-child { border-bottom: none; }
  .permuta-name { color: var(--text); font-weight: 700; }
  .permuta-name small { display: block; color: var(--text-muted); font-size: 10px; font-weight: 400; }
  .lotes-badge {
    background: var(--surface2);
    border: 1px solid var(--border);
    border-radius: 6px;
    padding: 4px 8px;
    font-size: 12px;
    font-weight: 700;
    color: var(--gold);
    text-align: center;
    white-space: nowrap;
  }
  .valor-badge {
    font-size: 11px;
    color: var(--green);
    font-weight: 700;
    text-align: right;
    white-space: nowrap;
  }

  /* FASES */
  .fase-card {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    margin-bottom: 10px;
    overflow: hidden;
  }
  .fase-header {
    padding: 14px 16px;
    cursor: pointer;
    display: flex;
    align-items: center;
    gap: 12px;
    user-select: none;
  }
  .fase-num {
    width: 28px; height: 28px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 12px;
    font-weight: 800;
    flex-shrink: 0;
  }
  .fase-info { flex: 1; }
  .fase-title {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
  }
  .fase-meta {
    font-size: 10px;
    color: var(--text-muted);
    margin-top: 2px;
    display: flex;
    gap: 12px;
  }
  .fase-arrow {
    color: var(--text-muted);
    font-size: 14px;
    transition: transform 0.2s;
  }
  .fase-card.open .fase-arrow { transform: rotate(180deg); }
  .fase-body {
    display: none;
    padding: 0 16px 14px;
  }
  .fase-card.open .fase-body { display: block; }

  /* PROGRESS BAR */
  .progress-wrap {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-bottom: 12px;
  }
  .progress-bar-bg {
    flex: 1;
    height: 4px;
    background: var(--border);
    border-radius: 2px;
    overflow: hidden;
  }
  .progress-bar-fill {
    height: 100%;
    border-radius: 2px;
    transition: width 0.4s ease;
  }
  .progress-pct {
    font-size: 10px;
    font-weight: 700;
    min-width: 30px;
    text-align: right;
  }

  /* CHECKLIST */
  .checklist { list-style: none; }
  .check-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 8px 0;
    border-bottom: 1px solid var(--border);
    cursor: pointer;
  }
  .check-item:last-child { border-bottom: none; }
  .check-box {
    width: 18px; height: 18px;
    border: 2px solid var(--border);
    border-radius: 4px;
    flex-shrink: 0;
    margin-top: 1px;
    display: flex; align-items: center; justify-content: center;
    font-size: 11px;
    transition: all 0.15s;
  }
  .check-item.done .check-box {
    background: var(--green-dim);
    border-color: var(--green);
    color: var(--green);
  }
  .check-text {
    font-size: 11px;
    color: var(--text-dim);
    line-height: 1.4;
    flex: 1;
  }
  .check-item.done .check-text {
    color: var(--text-muted);
    text-decoration: line-through;
  }
  .check-cost {
    font-size: 10px;
    color: var(--orange);
    white-space: nowrap;
    margin-top: 1px;
  }

  /* BUDGET TRACKER */
  .budget-total {
    background: linear-gradient(135deg, var(--surface2) 0%, #1a1f2e 100%);
    border: 1px solid var(--gold-dim);
    border-radius: var(--radius);
    padding: 16px;
    margin-bottom: 12px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .budget-label {
    font-size: 10px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--text-muted);
  }
  .budget-amount {
    font-family: 'Syne', sans-serif;
    font-size: 24px;
    font-weight: 800;
    color: var(--gold);
  }
  .budget-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px 0;
    border-bottom: 1px solid var(--border);
    font-size: 11px;
  }
  .budget-item:last-child { border-bottom: none; }
  .budget-item-name { color: var(--text-dim); }
  .budget-item-val { color: var(--text); font-weight: 700; }
  .budget-bar-row {
    margin-top: 4px;
    height: 3px;
    background: var(--border);
    border-radius: 2px;
    overflow: hidden;
  }
  .budget-bar-fill { height: 100%; background: var(--gold); border-radius: 2px; }

  /* STATUS BADGE */
  .badge {
    display: inline-block;
    padding: 2px 8px;
    border-radius: 4px;
    font-size: 9px;
    letter-spacing: 1px;
    text-transform: uppercase;
    font-weight: 700;
  }
  .badge-pending { background: var(--orange-dim); color: var(--orange); }
  .badge-active { background: var(--blue-dim); color: var(--blue); }
  .badge-done { background: var(--green-dim); color: var(--green); }
  .badge-wait { background: var(--border); color: var(--text-muted); }

  /* CRONOGRAMA */
  .timeline-row {
    display: flex;
    gap: 0;
    margin-bottom: 8px;
    align-items: center;
  }
  .tl-label {
    width: 90px;
    font-size: 9px;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    flex-shrink: 0;
    padding-right: 8px;
  }
  .tl-months {
    flex: 1;
    display: flex;
    gap: 2px;
  }
  .tl-month {
    flex: 1;
    height: 20px;
    border-radius: 3px;
    background: var(--border);
  }
  .tl-month.f0 { background: #8a6e2e; }
  .tl-month.f1 { background: #4a9eff55; border: 1px solid #4a9eff44; }
  .tl-month.f2 { background: #c9a84c66; border: 1px solid #c9a84c44; }
  .tl-month.f3 { background: #3ddc8455; border: 1px solid #3ddc8444; }
  .tl-month.f4 { background: #ff8c4255; border: 1px solid #ff8c4244; }
  .tl-month.f5 { background: #ff525255; border: 1px solid #ff525244; }
  .tl-header { display: flex; gap: 2px; margin-bottom: 4px; padding-left: 90px; }
  .tl-hm { flex: 1; font-size: 8px; color: var(--text-muted); text-align: center; }

  /* LEGENDA */
  .legend { display: flex; flex-wrap: wrap; gap: 8px; margin-top: 12px; }
  .legend-item { display: flex; align-items: center; gap: 5px; font-size: 10px; color: var(--text-dim); }
  .legend-dot { width: 10px; height: 10px; border-radius: 2px; flex-shrink: 0; }

  /* NOTES */
  .note-box {
    background: var(--surface2);
    border-left: 3px solid var(--gold);
    border-radius: 0 6px 6px 0;
    padding: 10px 12px;
    font-size: 11px;
    color: var(--text-dim);
    line-height: 1.6;
    margin: 10px 0;
  }
  .note-box.green { border-left-color: var(--green); }
  .note-box.orange { border-left-color: var(--orange); }
  .note-box.red { border-left-color: var(--red); }

  /* SECTION DIVIDER */
  .sdiv {
    font-size: 9px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin: 16px 0 8px;
    padding-bottom: 6px;
    border-bottom: 1px solid var(--border);
  }

  /* RESPONSIVE */
  @media (max-width: 400px) {
    .metrics { grid-template-columns: 1fr 1fr; }
    .metric-value { font-size: 15px; }
  }

  /* ANIMATE IN */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }
  .section.active > * { animation: fadeUp 0.3s ease forwards; }

  /* SAVE INDICATOR */
  .save-indicator {
    position: fixed;
    bottom: 16px; right: 16px;
    background: var(--green-dim);
    border: 1px solid var(--green);
    color: var(--green);
    font-size: 10px;
    padding: 6px 12px;
    border-radius: 6px;
    opacity: 0;
    transition: opacity 0.3s;
    pointer-events: none;
    font-family: 'Space Mono', monospace;
  }
  .save-indicator.show { opacity: 1; }
</style>
</head>
<body>

<header>
  <div class="header-tag">Projeto Imobiliário · Piracicaba SP</div>
  <h1>Condomínio <span>Rua Uchôa</span></h1>
  <div class="header-sub">17.000 m² · ~65 lotes · Modelo permuta · R$100k capital</div>
</header>

<div class="tabs">
  <div class="tab active" onclick="showTab('visao')">Visão Geral</div>
  <div class="tab" onclick="showTab('permuta')">Permuta</div>
  <div class="tab" onclick="showTab('planner')">Planner</div>
  <div class="tab" onclick="showTab('budget')">Budget</div>
  <div class="tab" onclick="showTab('cronograma')">Cronograma</div>
</div>

<main>

  <!-- ===== VISÃO GERAL ===== -->
  <div class="section active" id="visao">

    <div class="sdiv">📍 Dados do Projeto</div>
    <div class="metrics">
      <div class="metric">
        <div class="metric-label">Terreno</div>
        <div class="metric-value gold">17.000</div>
        <div class="metric-sub">m² total</div>
      </div>
      <div class="metric">
        <div class="metric-label">Lotes Estimados</div>
        <div class="metric-value gold">~65</div>
        <div class="metric-sub">de 140 m² cada</div>
      </div>
      <div class="metric">
        <div class="metric-label">Ticket Mín. (140m²)</div>
        <div class="metric-value">R$140k</div>
        <div class="metric-sub">R$1.000/m²</div>
      </div>
      <div class="metric">
        <div class="metric-label">Ticket Duplo (280m²)</div>
        <div class="metric-value">R$280k</div>
        <div class="metric-sub">2 lotes unidos</div>
      </div>
    </div>

    <div class="sdiv">💰 Potencial Financeiro</div>
    <div class="metrics">
      <div class="metric">
        <div class="metric-label">VGV Bruto</div>
        <div class="metric-value green">R$9,1M</div>
        <div class="metric-sub">65 × 140 × R$1.000</div>
      </div>
      <div class="metric">
        <div class="metric-label">Capital Próprio</div>
        <div class="metric-value orange">R$100k</div>
        <div class="metric-sub">só papelada/projetos</div>
      </div>
      <div class="metric">
        <div class="metric-label">Terreno Atual</div>
        <div class="metric-value">R$450</div>
        <div class="metric-sub">por m² (bruto)</div>
      </div>
      <div class="metric">
        <div class="metric-label">Alvo</div>
        <div class="metric-value gold">R$1.000</div>
        <div class="metric-sub">por m² (lote pronto)</div>
      </div>
    </div>

    <div class="sdiv">🏘️ Benchmarks da Rua</div>
    <div class="card">
      <div class="card-title"><span class="icon">📊</span>Condomínios Vizinhos</div>
      <div class="permuta-row">
        <div class="permuta-name">
          Vizinho A
          <small>Padrão mais baixo</small>
        </div>
        <span class="badge badge-done">Vendido</span>
        <div class="valor-badge">R$238k</div>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">
          Vizinho B
          <small>Padrão intermediário</small>
        </div>
        <span class="badge badge-done">Vendido</span>
        <div class="valor-badge">~R$350k</div>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">
          Vizinho C
          <small>Melhor avaliado</small>
        </div>
        <span class="badge badge-done">Vendido</span>
        <div class="valor-badge">R$500–600k</div>
      </div>
      <div class="note-box green" style="margin-top:10px">
        ✅ Mercado comprovado e absorvido. Demanda validada. Seu lote de 140m² + casa de 100m² estaria alinhado com o ticket do Vizinho A, com potencial de valorização conforme acabamento.
      </div>
    </div>

    <div class="note-box orange">
      ⚠️ <strong>Atenção:</strong> 80 lotes de 140m² = 11.200m² de área vendável. Com 35–40% obrigatório para vias/verde, você precisaria de ~18.500m². Com 17.000m², o número mais realista é <strong>60–65 lotes</strong>. Confirmar com arquiteto/urbanista na Fase 0.
    </div>
  </div>

  <!-- ===== PERMUTA ===== -->
  <div class="section" id="permuta">

    <div class="note-box" style="margin-bottom:14px">
      O modelo de permuta elimina a necessidade de comprar o terreno (~R$7,6M) e pagar a obra (~R$2M). Você entra como <strong>incorporador gestor</strong> e captura valor pela gestão do negócio.
    </div>

    <div class="sdiv">🤝 Estrutura da Divisão</div>
    <div class="card">
      <div class="card-title"><span class="icon">🏗️</span>Divisão dos Lotes</div>
      <div class="permuta-row">
        <div class="permuta-name">
          Dono do Terreno
          <small>Permuta pelo terreno de 17.000m²</small>
        </div>
        <div class="lotes-badge">~28 lotes</div>
        <div class="valor-badge">~R$3,9M</div>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">
          Construtora
          <small>Permuta pela infraestrutura (~R$2M)</small>
        </div>
        <div class="lotes-badge">~18 lotes</div>
        <div class="valor-badge">~R$2,5M</div>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">
          Você (Incorporador)
          <small>Gestão + capital de giro + risco</small>
        </div>
        <div class="lotes-badge">~19 lotes</div>
        <div class="valor-badge">~R$2,7M</div>
      </div>
      <div class="permuta-row" style="padding-top:12px;border-top:1px solid var(--gold-dim)">
        <div class="permuta-name" style="color:var(--gold);font-family:'Syne',sans-serif">
          Total
        </div>
        <div class="lotes-badge" style="border-color:var(--gold);color:var(--gold-light)">65 lotes</div>
        <div class="valor-badge">R$9,1M</div>
      </div>
    </div>

    <div class="sdiv">📋 Como Abordar o Dono do Terreno</div>
    <div class="card">
      <div class="card-title"><span class="icon">🗣️</span>Argumento de Valor</div>
      <div style="font-size:11px;color:var(--text-dim);line-height:1.7">
        <p style="margin-bottom:8px">• Hoje o terreno vale <strong style="color:var(--text)">R$7,65M</strong> como área bruta</p>
        <p style="margin-bottom:8px">• Na permuta, os 28 lotes dele valerão <strong style="color:var(--green)">R$3,9M</strong> — mas são lotes prontos, registrados, com infraestrutura</p>
        <p style="margin-bottom:8px">• Ele pode vender os 28 lotes progressivamente, <strong style="color:var(--text)">sem pagar nada</strong>, só esperando a aprovação</p>
        <p style="margin-bottom:8px">• Os três condomínios da mesma rua são prova social de demanda</p>
        <p>• <strong style="color:var(--gold)">Alternativa para o dono:</strong> Receber menos lotes (ex: 20) + entrada de R$30–50k em dinheiro para dar liquidez imediata</p>
      </div>
    </div>

    <div class="sdiv">🏢 Como Abordar a Construtora</div>
    <div class="card">
      <div class="card-title"><span class="icon">⚙️</span>O que oferecer</div>
      <div style="font-size:11px;color:var(--text-dim);line-height:1.7">
        <p style="margin-bottom:8px">• Obra estimada de <strong style="color:var(--text)">R$1,6–2,5M</strong> em infraestrutura (terraplanagem, vias, elétrica, água, muro)</p>
        <p style="margin-bottom:8px">• Em troca: <strong style="color:var(--green)">~18 lotes de 140m²</strong> (R$2,5M) — margem atrativa para elas</p>
        <p style="margin-bottom:8px">• Procurar construtoras <strong style="color:var(--text)">locais de Piracicaba</strong> que já fizeram loteamentos similares na região</p>
        <p>• Elas assumem o risco da obra; você assume o risco regulatório e comercial</p>
      </div>
    </div>

    <div class="note-box red">
      🔴 <strong>Crítico:</strong> Nunca feche permuta sem SPE registrada e contratos assinados com advogado. A divisão de lotes precisa estar definida ANTES de qualquer obra ou gasto relevante.
    </div>
  </div>

  <!-- ===== PLANNER ===== -->
  <div class="section" id="planner">

    <div style="font-size:11px;color:var(--text-dim);margin-bottom:14px">
      Clique nas fases para expandir. Marque as tarefas conforme avança. Progresso salvo automaticamente.
    </div>

    <!-- FASE 0 -->
    <div class="fase-card" id="fase0">
      <div class="fase-header" onclick="toggleFase('fase0')">
        <div class="fase-num" style="background:#8a6e2e;color:#e8c96a">0</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--gold)">Validação Prévia</div>
          <div class="fase-meta">
            <span>Mês 1–2</span>
            <span>~R$3.000</span>
            <span id="prog0-txt">0 de 5</span>
          </div>
        </div>
        <span class="badge badge-pending">Início</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog0" style="width:0%;background:var(--gold)"></div></div>
          <div class="progress-pct" id="prog0-pct" style="color:var(--gold)">0%</div>
        </div>
        <div class="note-box" style="margin-bottom:10px">
          <strong>Objetivo:</strong> Confirmar que o projeto é viável ANTES de gastar qualquer valor relevante.
        </div>
        <ul class="checklist" id="cl0">
          <li class="check-item" onclick="toggle(this,'cl0')">
            <div class="check-box"></div>
            <div class="check-text">Consulta prévia na Prefeitura de Piracicaba (SEPLAN) — verificar zoneamento e parâmetros da Rua Uchôa</div>
            <div class="check-cost">Grátis</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl0')">
            <div class="check-box"></div>
            <div class="check-text">Pesquisar matrícula e escritura do terreno no Cartório de Imóveis — confirmar que está limpo</div>
            <div class="check-cost">~R$200</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl0')">
            <div class="check-box"></div>
            <div class="check-text">Conversa informal com o dono do terreno — testar receptividade para permuta</div>
            <div class="check-cost">Grátis</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl0')">
            <div class="check-box"></div>
            <div class="check-text">Visitar os 3 condomínios vizinhos — pesquisar preço real de venda e absorção do mercado</div>
            <div class="check-cost">Grátis</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl0')">
            <div class="check-box"></div>
            <div class="check-text">Contato inicial com 2–3 construtoras locais de Piracicaba — testar interesse em permuta de obra</div>
            <div class="check-cost">Grátis</div>
          </li>
        </ul>
      </div>
    </div>

    <!-- FASE 1 -->
    <div class="fase-card" id="fase1">
      <div class="fase-header" onclick="toggleFase('fase1')">
        <div class="fase-num" style="background:var(--blue-dim);color:var(--blue)">1</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--blue)">Estruturação Jurídica</div>
          <div class="fase-meta">
            <span>Mês 2–4</span>
            <span>~R$25.000</span>
            <span id="prog1-txt">0 de 6</span>
          </div>
        </div>
        <span class="badge badge-wait">Aguarda F0</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog1" style="width:0%;background:var(--blue)"></div></div>
          <div class="progress-pct" id="prog1-pct" style="color:var(--blue)">0%</div>
        </div>
        <div class="note-box" style="margin-bottom:10px">
          <strong>Objetivo:</strong> Blindar o negócio juridicamente antes de qualquer obra.
        </div>
        <ul class="checklist" id="cl1">
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Contratar advogado imobiliário especializado em incorporações / loteamentos</div>
            <div class="check-cost">~R$5.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Abrir SPE — Sociedade de Propósito Específico (CNPJ exclusivo do projeto)</div>
            <div class="check-cost">~R$1.500</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Redigir e assinar contrato de permuta com dono do terreno (definir lotes + cronograma)</div>
            <div class="check-cost">~R$5.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Redigir e assinar contrato de parceria com construtora (escopo de obra + lotes de pagamento)</div>
            <div class="check-cost">~R$5.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Definir tabela de lotes: quais são do dono, construtora e você — documentar no contrato da SPE</div>
            <div class="check-cost">Incluído</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl1')">
            <div class="check-box"></div>
            <div class="check-text">Registro da incorporação no Cartório de Imóveis de Piracicaba</div>
            <div class="check-cost">~R$8.000</div>
          </li>
        </ul>
      </div>
    </div>

    <!-- FASE 2 -->
    <div class="fase-card" id="fase2">
      <div class="fase-header" onclick="toggleFase('fase2')">
        <div class="fase-num" style="background:var(--gold-dim);color:var(--gold-light)">2</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--gold-light)">Projetos e Aprovações</div>
          <div class="fase-meta">
            <span>Mês 3–10</span>
            <span>~R$55.000</span>
            <span id="prog2-txt">0 de 8</span>
          </div>
        </div>
        <span class="badge badge-wait">Aguarda F1</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog2" style="width:0%;background:var(--gold)"></div></div>
          <div class="progress-pct" id="prog2-pct" style="color:var(--gold)">0%</div>
        </div>
        <div class="note-box" style="margin-bottom:10px">
          <strong>Objetivo:</strong> Obter o alvará de loteamento — a licença para vender e construir.
        </div>
        <ul class="checklist" id="cl2">
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Levantamento topográfico completo do terreno</div>
            <div class="check-cost">~R$6.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Contratar arquiteto/urbanista para projeto de loteamento (implantação dos lotes, vias, áreas verdes)</div>
            <div class="check-cost">~R$18.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Projeto de terraplanagem e drenagem pluvial (engenheiro civil)</div>
            <div class="check-cost">~R$6.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Projeto elétrico e iluminação interna (aprovação CPFL Piracicaba)</div>
            <div class="check-cost">~R$4.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Projeto hidrossanitário — rede de água e esgoto (aprovação SAAE Piracicaba)</div>
            <div class="check-cost">~R$5.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">EIV — Estudo de Impacto de Vizinhança (verificar se a Prefeitura exige)</div>
            <div class="check-cost">~R$4.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Protocolo e acompanhamento na Prefeitura (SEPLAN) — processo de aprovação do loteamento</div>
            <div class="check-cost">~R$8.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl2')">
            <div class="check-box"></div>
            <div class="check-text">Registro do loteamento aprovado no Cartório de Imóveis — abertura das matrículas individuais</div>
            <div class="check-cost">~R$5.000</div>
          </li>
        </ul>
      </div>
    </div>

    <!-- FASE 3 -->
    <div class="fase-card" id="fase3">
      <div class="fase-header" onclick="toggleFase('fase3')">
        <div class="fase-num" style="background:var(--green-dim);color:var(--green)">3</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--green)">Obra de Infraestrutura</div>
          <div class="fase-meta">
            <span>Mês 10–18</span>
            <span>Permuta construtora</span>
            <span id="prog3-txt">0 de 7</span>
          </div>
        </div>
        <span class="badge badge-wait">Permuta</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog3" style="width:0%;background:var(--green)"></div></div>
          <div class="progress-pct" id="prog3-pct" style="color:var(--green)">0%</div>
        </div>
        <div class="note-box green" style="margin-bottom:10px">
          <strong>Custo seu: R$0.</strong> A construtora executa tudo em troca dos lotes acordados na Fase 1.
        </div>
        <ul class="checklist" id="cl3">
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Terraplanagem e movimentação de terra</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Abertura e pavimentação das ruas internas</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Instalação da rede elétrica e iluminação interna</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Rede de água e esgoto conforme projeto aprovado</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Muro perimetral e guarita de acesso</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Área verde/lazer obrigatória (Lei 6.766/79)</div>
            <div class="check-cost">Permuta</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl3')">
            <div class="check-box"></div>
            <div class="check-text">Habite-se do loteamento — laudo de conclusão e vistoria final</div>
            <div class="check-cost">~R$2.000</div>
          </li>
        </ul>
      </div>
    </div>

    <!-- FASE 4 -->
    <div class="fase-card" id="fase4">
      <div class="fase-header" onclick="toggleFase('fase4')">
        <div class="fase-num" style="background:var(--orange-dim);color:var(--orange)">4</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--orange)">Vendas</div>
          <div class="fase-meta">
            <span>Mês 8–20</span>
            <span>Inicia antes da obra</span>
            <span id="prog4-txt">0 de 6</span>
          </div>
        </div>
        <span class="badge badge-wait">Paralelo F2</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog4" style="width:0%;background:var(--orange)"></div></div>
          <div class="progress-pct" id="prog4-pct" style="color:var(--orange)">0%</div>
        </div>
        <div class="note-box orange" style="margin-bottom:10px">
          <strong>Dica:</strong> Você pode vender "na planta" após aprovação do projeto, antes de terminar a obra. Isso gera caixa antecipado.
        </div>
        <ul class="checklist" id="cl4">
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Definir tabela de preços (variação por posição: esquina, fundos, frente)</div>
            <div class="check-cost">—</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Criar material de vendas: planta do condomínio, fotos do entorno, comparativo com vizinhos</div>
            <div class="check-cost">~R$3.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Firmar parceria com 1–2 imobiliárias locais de Piracicaba (comissão ~6% do valor)</div>
            <div class="check-cost">6% VGV</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Lançamento comercial — evento no local ou campanha digital local</div>
            <div class="check-cost">~R$5.000</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Estruturar opções de pagamento: à vista, parcelado pela SPE ou financiamento bancário</div>
            <div class="check-cost">—</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl4')">
            <div class="check-box"></div>
            <div class="check-text">Escrituração e transferência das matrículas dos lotes vendidos</div>
            <div class="check-cost">~R$800/lote</div>
          </li>
        </ul>
      </div>
    </div>

    <!-- FASE 5 -->
    <div class="fase-card" id="fase5">
      <div class="fase-header" onclick="toggleFase('fase5')">
        <div class="fase-num" style="background:#3d1f1f;color:var(--red)">5</div>
        <div class="fase-info">
          <div class="fase-title" style="color:var(--red)">Encerramento</div>
          <div class="fase-meta">
            <span>Mês 20–26</span>
            <span>Distribuição do resultado</span>
            <span id="prog5-txt">0 de 4</span>
          </div>
        </div>
        <span class="badge badge-wait">Final</span>
        <div class="fase-arrow">▼</div>
      </div>
      <div class="fase-body">
        <div class="progress-wrap">
          <div class="progress-bar-bg"><div class="progress-bar-fill" id="prog5" style="width:0%;background:var(--red)"></div></div>
          <div class="progress-pct" id="prog5-pct" style="color:var(--red)">0%</div>
        </div>
        <ul class="checklist" id="cl5">
          <li class="check-item" onclick="toggle(this,'cl5')">
            <div class="check-box"></div>
            <div class="check-text">Quitação dos lotes do dono do terreno conforme contrato de permuta</div>
            <div class="check-cost">—</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl5')">
            <div class="check-box"></div>
            <div class="check-text">Quitação dos lotes da construtora conforme contrato de obra</div>
            <div class="check-cost">—</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl5')">
            <div class="check-box"></div>
            <div class="check-text">Distribuição do resultado líquido para você — apuração final da SPE</div>
            <div class="check-cost">—</div>
          </li>
          <li class="check-item" onclick="toggle(this,'cl5')">
            <div class="check-box"></div>
            <div class="check-text">Encerramento formal da SPE no cartório e receita federal</div>
            <div class="check-cost">~R$2.000</div>
          </li>
        </ul>
      </div>
    </div>

  </div>

  <!-- ===== BUDGET ===== -->
  <div class="section" id="budget">

    <div class="budget-total">
      <div>
        <div class="budget-label">Orçamento Total</div>
        <div class="budget-amount">R$ 100.000</div>
      </div>
      <div style="text-align:right">
        <div class="budget-label">Capital Próprio</div>
        <div style="font-size:12px;color:var(--text-dim);margin-top:2px">Fase 0 + 1 + 2</div>
      </div>
    </div>

    <div class="sdiv">📋 Breakdown do Investimento</div>
    <div class="card">
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Advogado (estruturação + contratos)</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:20%"></div></div>
        </div>
        <div class="budget-item-val">R$15–20k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Arquiteto/urbanista (projeto loteamento)</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:18%"></div></div>
        </div>
        <div class="budget-item-val">R$15–18k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Topografia</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:6%"></div></div>
        </div>
        <div class="budget-item-val">R$5–6k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Projetos complementares (elétrico, hidro)</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:9%"></div></div>
        </div>
        <div class="budget-item-val">R$8–10k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Taxas prefeitura + SAAE + CPFL</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:15%"></div></div>
        </div>
        <div class="budget-item-val">R$8–15k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Registro cartório (incorporação + loteamento)</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:13%"></div></div>
        </div>
        <div class="budget-item-val">R$10–13k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">SPE + abertura empresa</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:2%"></div></div>
        </div>
        <div class="budget-item-val">R$1,5k</div>
      </div>
      <div class="budget-item">
        <div>
          <div class="budget-item-name">Material de vendas + lançamento</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:8%"></div></div>
        </div>
        <div class="budget-item-val">R$5–8k</div>
      </div>
      <div class="budget-item" style="border-top:1px solid var(--gold-dim);padding-top:12px;margin-top:4px">
        <div>
          <div class="budget-item-name" style="color:var(--gold);font-weight:700">Reserva de contingência</div>
          <div class="budget-bar-row"><div class="budget-bar-fill" style="width:15%;background:var(--orange)"></div></div>
        </div>
        <div class="budget-item-val" style="color:var(--orange)">R$13–15k</div>
      </div>
    </div>

    <div class="note-box green">
      ✅ <strong>O que NÃO sai do seu bolso:</strong> Compra do terreno (~R$7,6M) e a obra de infraestrutura (~R$1,6–2,5M) — ambos cobertos pelas permutas com o dono e a construtora.
    </div>

    <div class="sdiv">🎯 Retorno Estimado Você</div>
    <div class="metrics">
      <div class="metric">
        <div class="metric-label">Lotes seus</div>
        <div class="metric-value gold">~19</div>
        <div class="metric-sub">lotes de 140 m²</div>
      </div>
      <div class="metric">
        <div class="metric-label">Resultado Bruto</div>
        <div class="metric-value green">R$2,7M</div>
        <div class="metric-sub">19 × R$140k</div>
      </div>
      <div class="metric">
        <div class="metric-label">Capital Investido</div>
        <div class="metric-value orange">R$100k</div>
        <div class="metric-sub">total gasto</div>
      </div>
      <div class="metric">
        <div class="metric-label">ROI</div>
        <div class="metric-value green">~27x</div>
        <div class="metric-sub">retorno sobre o caixa</div>
      </div>
    </div>
  </div>

  <!-- ===== CRONOGRAMA ===== -->
  <div class="section" id="cronograma">

    <div class="note-box" style="margin-bottom:14px">
      Prazo total estimado: <strong>22–26 meses</strong>. O maior tempo é regulatório (Fase 2), não de obra.
    </div>

    <div class="sdiv">📅 Visão por Mês</div>
    <div class="card" style="overflow-x:auto">
      <div style="min-width:340px">
        <div class="tl-header">
          <div class="tl-hm">M1</div><div class="tl-hm">M2</div><div class="tl-hm">M3</div>
          <div class="tl-hm">M4</div><div class="tl-hm">M5</div><div class="tl-hm">M6</div>
          <div class="tl-hm">M8</div><div class="tl-hm">M10</div><div class="tl-hm">M12</div>
          <div class="tl-hm">M14</div><div class="tl-hm">M16</div><div class="tl-hm">M18</div>
          <div class="tl-hm">M20</div><div class="tl-hm">M22</div><div class="tl-hm">M24</div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F0 Validação</div>
          <div class="tl-months">
            <div class="tl-month f0"></div><div class="tl-month f0"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div>
          </div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F1 Jurídico</div>
          <div class="tl-months">
            <div class="tl-month"></div><div class="tl-month f1"></div>
            <div class="tl-month f1"></div><div class="tl-month f1"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div>
          </div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F2 Projetos</div>
          <div class="tl-months">
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month f2"></div><div class="tl-month f2"></div>
            <div class="tl-month f2"></div><div class="tl-month f2"></div>
            <div class="tl-month f2"></div><div class="tl-month f2"></div>
            <div class="tl-month f2"></div><div class="tl-month f2"></div>
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
          </div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F3 Obra</div>
          <div class="tl-months">
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month f3"></div>
            <div class="tl-month f3"></div><div class="tl-month f3"></div>
            <div class="tl-month f3"></div><div class="tl-month f3"></div>
            <div class="tl-month f3"></div><div class="tl-month f3"></div>
            <div class="tl-month"></div>
          </div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F4 Vendas</div>
          <div class="tl-months">
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month f4"></div>
            <div class="tl-month f4"></div><div class="tl-month f4"></div>
            <div class="tl-month f4"></div><div class="tl-month f4"></div>
            <div class="tl-month f4"></div><div class="tl-month f4"></div>
            <div class="tl-month f4"></div>
          </div>
        </div>
        <div class="timeline-row">
          <div class="tl-label">F5 Encerr.</div>
          <div class="tl-months">
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month"></div>
            <div class="tl-month"></div><div class="tl-month f5"></div>
            <div class="tl-month f5"></div>
          </div>
        </div>
      </div>
    </div>

    <div class="legend">
      <div class="legend-item"><div class="legend-dot" style="background:#8a6e2e"></div>F0 Validação</div>
      <div class="legend-item"><div class="legend-dot" style="background:#4a9eff55;border:1px solid #4a9eff44"></div>F1 Jurídico</div>
      <div class="legend-item"><div class="legend-dot" style="background:#c9a84c66;border:1px solid #c9a84c44"></div>F2 Projetos</div>
      <div class="legend-item"><div class="legend-dot" style="background:#3ddc8455;border:1px solid #3ddc8444"></div>F3 Obra</div>
      <div class="legend-item"><div class="legend-dot" style="background:#ff8c4255;border:1px solid #ff8c4244"></div>F4 Vendas</div>
      <div class="legend-item"><div class="legend-dot" style="background:#ff525255;border:1px solid #ff525244"></div>F5 Encerr.</div>
    </div>

    <div class="sdiv">⚡ Marcos Críticos</div>
    <div class="card">
      <div class="permuta-row">
        <div class="permuta-name">Dono aceita permuta <small>Pré-requisito de tudo</small></div>
        <span class="badge badge-pending">Mês 1–2</span>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">SPE aberta + contratos assinados <small>Estrutura jurídica pronta</small></div>
        <span class="badge badge-wait">Mês 3–4</span>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">Alvará da Prefeitura <small>Pode vender na planta</small></div>
        <span class="badge badge-wait">Mês 8–10</span>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">Início das vendas <small>Gera caixa antes da obra terminar</small></div>
        <span class="badge badge-wait">Mês 8–10</span>
      </div>
      <div class="permuta-row">
        <div class="permuta-name">Obra concluída + Habite-se <small>Entrega dos lotes</small></div>
        <span class="badge badge-wait">Mês 18</span>
      </div>
      <div class="permuta-row" style="border-bottom:none">
        <div class="permuta-name">Resultado distribuído <small>Fim da SPE</small></div>
        <span class="badge badge-wait">Mês 22–24</span>
      </div>
    </div>

  </div>

</main>

<div class="save-indicator" id="saveInd">✓ Salvo</div>

<script>
  // TABS
  function showTab(id) {
    document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
    document.querySelectorAll('.section').forEach(s => s.classList.remove('active'));
    document.getElementById(id).classList.add('active');
    event.target.classList.add('active');
  }

  // FASE TOGGLE
  function toggleFase(id) {
    document.getElementById(id).classList.toggle('open');
  }

  // LOAD STATE
  function loadState() {
    try {
      const saved = localStorage.getItem('loteamento_checks');
      if (!saved) return;
      const state = JSON.parse(saved);
      for (const [clId, indices] of Object.entries(state)) {
        const ul = document.getElementById(clId);
        if (!ul) continue;
        const items = ul.querySelectorAll('.check-item');
        indices.forEach(i => {
          if (items[i]) {
            items[i].classList.add('done');
            items[i].querySelector('.check-box').textContent = '✓';
          }
        });
      }
      // update all progress bars
      ['cl0','cl1','cl2','cl3','cl4','cl5'].forEach((id, i) => updateProgress(id, i));
    } catch(e) {}
  }

  // SAVE STATE
  function saveState() {
    try {
      const state = {};
      ['cl0','cl1','cl2','cl3','cl4','cl5'].forEach(id => {
        const ul = document.getElementById(id);
        if (!ul) return;
        const items = ul.querySelectorAll('.check-item');
        const checked = [];
        items.forEach((item, i) => { if (item.classList.contains('done')) checked.push(i); });
        state[id] = checked;
      });
      localStorage.setItem('loteamento_checks', JSON.stringify(state));
      const ind = document.getElementById('saveInd');
      ind.classList.add('show');
      setTimeout(() => ind.classList.remove('show'), 1500);
    } catch(e) {}
  }

  // TOGGLE ITEM
  function toggle(el, clId) {
    const phaseIndex = parseInt(clId.replace('cl',''));
    el.classList.toggle('done');
    const box = el.querySelector('.check-box');
    box.textContent = el.classList.contains('done') ? '✓' : '';
    updateProgress(clId, phaseIndex);
    saveState();
  }

  function updateProgress(clId, phaseIndex) {
    const ul = document.getElementById(clId);
    if (!ul) return;
    const items = ul.querySelectorAll('.check-item');
    const done = ul.querySelectorAll('.check-item.done').length;
    const total = items.length;
    const pct = Math.round((done / total) * 100);
    const bar = document.getElementById('prog' + phaseIndex);
    const pctEl = document.getElementById('prog' + phaseIndex + '-pct');
    const txtEl = document.getElementById('prog' + phaseIndex + '-txt');
    if (bar) bar.style.width = pct + '%';
    if (pctEl) pctEl.textContent = pct + '%';
    if (txtEl) txtEl.textContent = done + ' de ' + total;
  }

  // INIT
  loadState();
  // open fase 0 by default
  document.getElementById('fase0').classList.add('open');
</script>

</body>
</html>
