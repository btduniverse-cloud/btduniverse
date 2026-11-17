<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BTD UNIVERSE — Hub Operacional Transmídia</title>
    <style>
        :root {
            --bg: #030306;
            --ink: #f5f5f7;
            --cyan: #00f0ff;
            --purple: #7000ff;
            --pink: #ff007f;
            --gold: #ffd166;
            --sans: 'Rajdhani', sans-serif;
            --mono: 'Space Mono', monospace;
        }
        body {
            background: var(--bg);
            color: var(--ink);
            font-family: var(--sans);
            font-size: 16px;
            line-height: 1.7;
            overflow-x: hidden;
            margin: 0;
            padding: 0;
        }
        body::before {
            content: "";
            position: fixed;
            inset: 0;
            background: repeating-linear-gradient(0deg, transparent, transparent 3px, rgba(0,212,255,0.01) 3px, rgba(0,212,255,0.01) 4px);
            pointer-events: none;
            z-index: 999;
        }
        nav {
            position: fixed;
            top: 0; left: 0; right: 0;
            z-index: 200;
            padding: 1.2rem 4rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: rgba(3,3,6,0.9);
            backdrop-filter: blur(20px);
            border-bottom: 1px solid rgba(0,240,255,0.1);
        }
        .nav-logo {
            font-family: var(--mono);
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            color: var(--cyan);
            text-decoration: none;
        }
        .banner-hero {
            position: relative;
            min-height: 50vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 10rem 2rem 4rem;
            background: linear-gradient(180deg, rgba(3,3,6,0.5) 0%, rgba(3,3,6,1) 100%), url('btdbanner.png') center/cover no-repeat;
            border-bottom: 1px solid rgba(255, 0, 127, 0.2);
        }
        .logo-container img {
            max-width: 240px;
            height: auto;
            filter: drop-shadow(0 0 25px rgba(0,240,255,0.4));
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }
        .main-headline {
            font-family: var(--mono);
            font-size: 14px;
            letter-spacing: 0.3em;
            text-transform: uppercase;
            color: var(--pink);
            margin-bottom: 3rem;
            border-left: 3px solid var(--pink);
            padding-left: 1rem;
        }
        .section-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2.5rem;
            margin-bottom: 4rem;
        }
        @media (max-width: 768px) { .section-grid { grid-template-columns: 1fr; } }
        .card {
            background: rgba(3,3,6,0.6);
            border: 1px solid rgba(0,240,255,0.1);
            padding: 2.5rem;
            border-radius: 4px;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        .card:hover { 
            border-color: var(--cyan);
            box-shadow: 0 0 30px rgba(0,240,255,0.05);
        }
        .card h3 {
            font-family: var(--mono);
            font-size: 1.1rem;
            letter-spacing: 0.15em;
            text-transform: uppercase;
            margin-top: 0;
            color: var(--cyan);
            border-bottom: 1px solid rgba(0,240,255,0.2);
            padding-bottom: 0.5rem;
        }
        .status-badge {
            display: inline-block;
            font-family: var(--mono);
            font-size: 10px;
            padding: 0.2rem 0.6rem;
            border-radius: 2px;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            margin-bottom: 1rem;
        }
        .status-badge.active { background: rgba(0,240,255,0.1); color: var(--cyan); border: 1px solid var(--cyan); }
        .status-badge.progress { background: rgba(255,0,127,0.1); color: var(--pink); border: 1px solid var(--pink); }
        .status-badge.pitch { background: rgba(255,209,102,0.1); color: var(--gold); border: 1px solid var(--gold); }
        
        .audio-pipeline {
            background: rgba(255,0,127,0.03);
            border: 1px solid rgba(255,0,127,0.2);
            padding: 1.5rem;
            border-radius: 4px;
            margin-top: 1.5rem;
        }
        .streaming-links {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 1rem;
            margin-top: 1.5rem;
        }
        @media (max-width: 480px) { .streaming-links { grid-template-columns: 1fr 1fr; } }
        .stream-btn {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0.8rem;
            font-family: var(--mono);
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 0.1em;
            text-decoration: none;
            border-radius: 2px;
            background: rgba(255,255,255,0.03);
            color: var(--ink);
            border: 1px solid rgba(255,255,255,0.05);
            transition: all 0.2s;
        }
        .stream-btn.spotify:hover { background: #1DB954; color: #000; }
        .stream-btn.apple:hover { background: #FC3C44; color: #fff; }
        .stream-btn.amazon:hover { background: #00A8E1; color: #fff; }
        .stream-btn.youtube:hover { background: #FF0000; color: #fff; }

        .ln-link {
            color: var(--gold);
            text-decoration: none;
            font-family: var(--mono);
            font-size: 12px;
            letter-spacing: 0.1em;
            font-weight: bold;
            display: inline-block;
            margin-top: 1rem;
        }
        .ln-link:hover { text-decoration: underline; color: var(--cyan); }

        .drive-section {
            text-align: center;
            background: linear-gradient(135deg, rgba(255,0,127,0.03) 0%, rgba(112,0,255,0.03) 100%);
            border: 1px solid rgba(255,0,127,0.2);
            padding: 4rem 2rem;
            border-radius: 4px;
            box-shadow: inset 0 0 20px rgba(0,0,0,0.5);
            margin-top: 2rem;
        }
        .drive-btn {
            display: inline-block;
            padding: 1.2rem 3rem;
            font-family: var(--mono);
            font-size: 12px;
            font-weight: bold;
            text-transform: uppercase;
            letter-spacing: 0.25em;
            text-decoration: none;
            background: rgba(0,240,255,0.08);
            color: var(--ink);
            border: 1px solid var(--cyan);
            border-radius: 2px;
            transition: all 0.3s ease;
            margin-top: 2rem;
            box-shadow: 0 0 15px rgba(0,240,255,0.1);
        }
        .drive-btn:hover { background: var(--cyan); color: #030306; box-shadow: 0 0 25px var(--cyan); }
    </style>
</head>
<body>

    <nav>
        <a href="#" class="nav-logo">BTD UNIVERSE</a>
    </nav>

    <header class="banner-hero">
        <div class="logo-container">
            <img src="btdlogo.png" alt="BTD Logo">
        </div>
    </header>

    <main class="container">
        
        <div class="main-headline">// HUB OPERACIONAL — CONCEITO E ECOSSISTEMA TRANSMÍDIA SOBERANO</div>

        <div class="section-grid">
            
            <!-- CORE TRILOGY 01: BORN TO DIE -->
            <div class="card">
                <span class="status-badge active">Publicado / Codex Mestre</span>
                <h3>Born to Die — O Fio Tênue</h3>
                <p>Há um fio que não se vê, mas se sente, entre o que somos e o que fingimos ser, e ainda o que poderíamos ser. Entre o que lembramos e o que inventamos ou simulamos ter vivido. Uma linha instável entre a vigília e o sono, entre a lucidez e a loucura, entre estar vivo e apenas continuar.</p>
                <a href="https://caravanagrupoeditorial.com" target="_blank" class="ln-link">→ ACESSAR O LIVRO NA CARAVANA</a>
            </div>

            <!-- CORE TRILOGY 02: GROUND ZERO / TECIDO VISÍVEL DO NADA -->
            <div class="card">
                <span class="status-badge pitch">Rodadas de Negócio / Pitching</span>
                <h3>Ground Zero — Tecido Visível do Nada</h3>
                <p>Thriller psicológico transmídia de ficção e suspense focado em fricção algorítmica, tecnologia e ciência aplicada. Estrutura de longa duração desenvolvida de forma ontológica, em circulação ativa em rodadas de negócios de audiovisual e eventos de mercado internacionais.</p>
            </div>

            <!-- CORE TRILOGY 03: COLD BOT THEATER -->
            <div class="card">
                <span class="status-badge progress">Bíblia de Pitch & Desenvolvimento</span>
                <h3>Cold Bot Theater</h3>
                <p>Análise e narrativa cênica focada nas complexidades humanas viscerais, neurodiversidade, isolamento sistêmico e no resgate arqueológico de memórias immemoriais sob a fricção algorítmica de cenários extremos.</p>
            </div>

            <!-- PIPELINE FONOGRÁFICO: SADSTINK -->
            <div class="card">
                <span class="status-badge active">Phonographic Rights</span>
                <h3>SadStink — Core Audio & Clipes</h3>
                <p>Conceito musical híbrido fundindo pós-grunge, ópera gótica melódica e distorções mecânicas industriais. Direitos autorais e linhas fonográficas protegidos via Avctoris IP Blockchain.</p>
                
                <div class="audio-pipeline">
