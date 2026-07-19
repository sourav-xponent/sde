```html
<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>System Design & Backend Engineering - সম্পূর্ণ গাইড বাংলায়</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: #0a0a0a;
            color: #e0e0e0;
            line-height: 1.8;
        }

        /* ── COVER ── */
        .cover {
            min-height: 100vh;
            background: linear-gradient(135deg, #0a0a0a 0%, #1a1a2e 50%, #16213e 100%);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            padding: 40px;
            position: relative;
            overflow: hidden;
        }
        .cover::before {
            content: '';
            position: absolute;
            width: 700px; height: 700px;
            background: radial-gradient(circle, rgba(0,212,255,0.04) 0%, transparent 70%);
            top: 50%; left: 50%;
            transform: translate(-50%,-50%);
        }
        .cover-badge {
            background: linear-gradient(135deg,#00d4ff,#0080ff);
            color: white;
            padding: 8px 28px;
            border-radius: 50px;
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 28px;
        }
        .cover-title {
            font-size: 54px;
            font-weight: 900;
            background: linear-gradient(135deg,#00d4ff,#ffffff,#00d4ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
            margin-bottom: 18px;
        }
        .cover-subtitle {
            font-size: 20px;
            color: #777;
            margin-bottom: 50px;
        }
        .cover-modules {
            display: grid;
            grid-template-columns: repeat(4,1fr);
            gap: 14px;
            max-width: 960px;
            margin: 0 auto 50px;
        }
        .cover-module-card {
            background: rgba(255,255,255,0.04);
            border: 1px solid rgba(0,212,255,0.15);
            border-radius: 12px;
            padding: 16px 12px;
            text-align: center;
        }
        .cover-module-card .mc-icon { font-size: 26px; margin-bottom: 8px; }
        .cover-module-card .mc-name { font-size: 11px; color: #00d4ff; font-weight: 700; }
        .cover-stats {
            display: flex;
            gap: 50px;
        }
        .stat { text-align: center; }
        .stat-number { font-size: 38px; font-weight: 900; color: #00d4ff; }
        .stat-label { font-size: 12px; color: #555; margin-top: 4px; }

        /* ── TOC ── */
        .toc {
            background: #0d0d0d;
            padding: 70px 40px;
            border-bottom: 1px solid #1a1a1a;
        }
        .toc-title {
            font-size: 34px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 40px;
            text-align: center;
        }
        .toc-grid {
            display: grid;
            grid-template-columns: repeat(3,1fr);
            gap: 16px;
            max-width: 1100px;
            margin: 0 auto;
        }
        .toc-item {
            background: #141414;
            border: 1px solid #222;
            border-left: 4px solid #00d4ff;
            border-radius: 10px;
            padding: 18px;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            color: inherit;
            display: block;
        }
        .toc-item:hover { border-left-color: #00ff88; transform: translateX(4px); }
        .toc-item-header { display: flex; align-items: center; gap: 10px; margin-bottom: 6px; }
        .toc-num {
            background: linear-gradient(135deg,#00d4ff,#0080ff);
            color: white;
            width: 32px; height: 32px;
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            font-weight: 800; font-size: 13px;
            flex-shrink: 0;
        }
        .toc-module-title { font-size: 14px; font-weight: 700; color: #fff; }
        .toc-topics { font-size: 11px; color: #555; padding-left: 42px; }

        /* ── MODULE SECTION ── */
        .module-section {
            padding: 80px 40px;
            border-bottom: 2px solid #111;
            max-width: 1200px;
            margin: 0 auto;
        }
        .module-header { text-align: center; margin-bottom: 60px; }
        .module-number-badge {
            display: inline-block;
            background: linear-gradient(135deg,#00d4ff,#0080ff);
            color: white;
            padding: 6px 22px;
            border-radius: 50px;
            font-size: 12px;
            font-weight: 700;
            letter-spacing: 2px;
            margin-bottom: 14px;
        }
        .module-title { font-size: 40px; font-weight: 900; color: #fff; margin-bottom: 10px; }
        .module-subtitle { font-size: 15px; color: #666; }

        /* ── SUBSECTION ── */
        .subsection-title {
            font-size: 22px;
            font-weight: 800;
            color: #fff;
            margin: 50px auto 20px;
            max-width: 1100px;
            padding-left: 16px;
            border-left: 4px solid #00d4ff;
        }
        .subsection-desc {
            font-size: 14px;
            color: #666;
            max-width: 1100px;
            margin: 0 auto 28px;
        }
        .section-divider {
            height: 1px;
            background: linear-gradient(90deg,transparent,#00d4ff33,transparent);
            margin: 50px auto;
            max-width: 700px;
        }

        /* ── CONCEPT CARDS ── */
        .concept-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit,minmax(280px,1fr));
            gap: 22px;
            margin: 30px auto;
            max-width: 1100px;
        }
        .concept-card {
            background: #141414;
            border: 1px solid #222;
            border-radius: 16px;
            padding: 26px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }
        .concept-card::before {
            content: '';
            position: absolute;
            top: 0; left: 0; right: 0;
            height: 3px;
            background: linear-gradient(90deg,#00d4ff,#0080ff);
        }
        .concept-card.green::before { background: linear-gradient(90deg,#00ff88,#00cc66); }
        .concept-card.purple::before { background: linear-gradient(90deg,#b44fff,#7c3aed); }
        .concept-card.orange::before { background: linear-gradient(90deg,#ff8c00,#ff4500); }
        .concept-card.pink::before { background: linear-gradient(90deg,#ff6b9d,#c44569); }
        .concept-card.yellow::before { background: linear-gradient(90deg,#ffd700,#ffa500); }
        .concept-card.red::before { background: linear-gradient(90deg,#ff4444,#cc0000); }
        .concept-card:hover { border-color: #00d4ff33; transform: translateY(-4px); box-shadow: 0 16px 40px rgba(0,212,255,0.08); }
        .card-icon { font-size: 34px; margin-bottom: 14px; }
        .card-title { font-size: 17px; font-weight: 800; color: #fff; margin-bottom: 10px; }
        .card-desc { font-size: 13px; color: #999; line-height: 1.7; }

        /* ── FLOW ── */
        .flow-container {
            background: #0f0f0f;
            border: 1px solid #222;
            border-radius: 20px;
            padding: 36px;
            margin: 30px auto;
            max-width: 1100px;
        }
        .flow-title { font-size: 18px; font-weight: 800; color: #00d4ff; margin-bottom: 28px; text-align: center; }
        .flow-row { display: flex; align-items: center; justify-content: center; flex-wrap: wrap; gap: 10px; margin: 16px 0; }
        .flow-box {
            background: linear-gradient(135deg,#1a2a3a,#1a1a2e);
            border: 1px solid #00d4ff33;
            border-radius: 12px;
            padding: 14px 20px;
            text-align: center;
            min-width: 110px;
        }
        .flow-box .fb-icon { font-size: 22px; margin-bottom: 4px; }
        .flow-box .fb-label { font-size: 12px; font-weight: 700; color: #00d4ff; }
        .flow-box .fb-sub { font-size: 10px; color: #555; margin-top: 3px; }
        .flow-arrow { font-size: 20px; color: #00d4ff; font-weight: 900; }

        /* ── TABLE ── */
        .comparison-table {
            width: 100%;
            max-width: 1100px;
            margin: 30px auto;
            border-collapse: collapse;
            border-radius: 14px;
            overflow: hidden;
        }
        .comparison-table th {
            background: linear-gradient(135deg,#00d4ff18,#0080ff18);
            color: #00d4ff;
            padding: 14px 18px;
            text-align: left;
            font-size: 13px;
            font-weight: 700;
            border-bottom: 2px solid #00d4ff33;
        }
        .comparison-table td {
            padding: 12px 18px;
            border-bottom: 1px solid #1a1a1a;
            font-size: 13px;
            color: #bbb;
            background: #111;
        }
        .comparison-table tr:hover td { background: #141414; }

        /* ── BADGES ── */
        .badge {
            display: inline-block;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 700;
        }
        .badge-green { background:#00ff8818; color:#00ff88; border:1px solid #00ff8844; }
        .badge-red { background:#ff444418; color:#ff6666; border:1px solid #ff444444; }
        .badge-blue { background:#00d4ff18; color:#00d4ff; border:1px solid #00d4ff44; }
        .badge-yellow { background:#ffd70018; color:#ffd700; border:1px solid #ffd70044; }
        .badge-purple { background:#b44fff18; color:#b44fff; border:1px solid #b44fff44; }

        /* ── INFO BOXES ── */
        .info-box {
            border-radius: 12px;
            padding: 22px 26px;
            margin: 22px auto;
            max-width: 1100px;
            display: flex;
            gap: 14px;
            align-items: flex-start;
        }
        .info-box.tip { background:rgba(0,255,136,0.04); border:1px solid rgba(0,255,136,0.2); }
        .info-box.warning { background:rgba(255,200,0,0.04); border:1px solid rgba(255,200,0,0.2); }
        .info-box.danger { background:rgba(255,68,68,0.04); border:1px solid rgba(255,68,68,0.2); }
        .info-box.info { background:rgba(0,212,255,0.04); border:1px solid rgba(0,212,255,0.2); }
        .info-icon { font-size: 22px; flex-shrink: 0; }
        .info-content .info-title { font-size: 14px; font-weight: 800; margin-bottom: 7px; }
        .info-box.tip .info-title { color:#00ff88; }
        .info-box.warning .info-title { color:#ffc800; }
        .info-box.danger .info-title { color:#ff4444; }
        .info-box.info .info-title { color:#00d4ff; }
        .info-content p { font-size: 13px; color:#999; line-height:1.7; }

        /* ── CODE BLOCK ── */
        .code-block {
            background: #0d1117;
            border: 1px solid #222;
            border-radius: 12px;
            padding: 26px;
            margin: 22px auto;
            max-width: 1100px;
            overflow-x: auto;
        }
        .code-block-header {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 18px;
            padding-bottom: 14px;
            border-bottom: 1px solid #1e1e1e;
        }
        .code-dots { display:flex; gap:6px; }
        .code-dot { width:11px; height:11px; border-radius:50%; }
        .dot-red { background:#ff5f57; }
        .dot-yellow { background:#febc2e; }
        .dot-green { background:#28c840; }
        .code-filename { font-size:12px; color:#555; margin-left:8px; }
        .code-block pre {
            font-family:'Courier New','Consolas',monospace;
            font-size:12.5px;
            line-height:1.9;
            color:#e6edf3;
            white-space:pre-wrap;
            word-wrap:break-word;
        }

        /* ── ARCH DIAGRAM ── */
        .arch-diagram {
            background: #0f0f0f;
            border: 1px solid #222;
            border-radius: 20px;
            padding: 36px;
            margin: 30px auto;
            max-width: 1100px;
            text-align: center;
        }
        .arch-title { font-size: 18px; font-weight: 800; color: #00d4ff; margin-bottom: 36px; }
        .arch-layer {
            background: #141414;
            border: 1px solid #222;
            border-radius: 12px;
            padding: 18px;
            margin: 8px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 16px;
            flex-wrap: wrap;
        }
        .arch-layer.highlight { border-color:#00d4ff33; background:#00d4ff06; }
        .arch-layer.green { border-color:#00ff8833; background:#00ff8806; }
        .arch-layer.orange { border-color:#ff8c0033; background:#ff8c0006; }
        .arch-node {
            background: #1a2a3a;
            border: 1px solid #00d4ff33;
            border-radius: 10px;
            padding: 10px 18px;
            text-align: center;
        }
        .arch-node .node-icon { font-size: 18px; }
        .arch-node .node-label { font-size: 11px; font-weight: 700; color: #00d4ff; margin-top: 3px; }
        .arch-node .node-sub { font-size: 10px; color: #444; }
        .arch-arrow-down { text-align:center; font-size:18px; color:#00d4ff; margin:4px 0; }

        /* ── METRICS ── */
        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit,minmax(180px,1fr));
            gap: 18px;
            margin: 30px auto;
            max-width: 1100px;
        }
        .metric-card {
            background: #141414;
            border: 1px solid #222;
            border-radius: 14px;
            padding: 22px;
            text-align: center;
        }
        .metric-value {
            font-size: 28px;
            font-weight: 900;
            background: linear-gradient(135deg,#00d4ff,#00ff88);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .metric-label { font-size: 12px; color:#666; margin-top:5px; }
        .metric-desc { font-size:11px; color:#444; margin-top:3px; }

        /* ── TIMELINE ── */
        .timeline { max-width:900px; margin:36px auto; position:relative; }
        .timeline::before {
            content:'';
            position:absolute;
            left:28px; top:0; bottom:0;
            width:2px;
            background:linear-gradient(180deg,#00d4ff,#0080ff);
        }
        .timeline-item { display:flex; gap:22px; margin-bottom:26px; padding-left:8px; }
        .timeline-dot {
            width:40px; height:40px;
            background:linear-gradient(135deg,#00d4ff,#0080ff);
            border-radius:50%;
            display:flex; align-items:center; justify-content:center;
            font-size:16px;
            flex-shrink:0; z-index:1;
        }
        .timeline-content {
            background:#141414;
            border:1px solid #222;
            border-radius:12px;
            padding:18px;
            flex:1;
        }
        .timeline-content h4 { font-size:15px; font-weight:800; color:#00d4ff; margin-bottom:7px; }
        .timeline-content p { font-size:13px; color:#999; line-height:1.6; }

        /* ── STEPS ── */
        .steps-container { max-width:1100px; margin:30px auto; }
        .step-item { display:flex; gap:18px; margin-bottom:18px; align-items:flex-start; }
        .step-number {
            background:linear-gradient(135deg,#00d4ff,#0080ff);
            color:white;
            width:42px; height:42px;
            border-radius:12px;
            display:flex; align-items:center; justify-content:center;
            font-weight:900; font-size:17px;
            flex-shrink:0;
        }
        .step-content {
            background:#141414;
            border:1px solid #222;
            border-radius:12px;
            padding:18px;
            flex:1;
        }
        .step-content h4 { font-size:15px; font-weight:800; color:#fff; margin-bottom:7px; }
        .step-content p { font-size:13px; color:#999; line-height:1.6; }

        /* ── TWO COL ── */
        .two-col { display:grid; grid-template-columns:1fr 1fr; gap:22px; max-width:1100px; margin:30px auto; }
        .col-box { background:#141414; border:1px solid #222; border-radius:16px; padding:22px; }
        .col-box h4 { font-size:15px; font-weight:800; color:#00d4ff; margin-bottom:14px; padding-bottom:10px; border-bottom:1px solid #222; }
        .col-box ul { list-style:none; }
        .col-box ul li { padding:7px 0; font-size:13px; color:#999; border-bottom:1px solid #1a1a1a; display:flex; gap:8px; }
        .col-box ul li:last-child { border:none; }

        /* ── REDIS DATATYPE VISUAL ── */
        .datatype-grid { display:grid; grid-template-columns:repeat(auto-fit,minmax(250px,1fr)); gap:20px; max-width:1100px; margin:30px auto; }
        .datatype-card { background:#141414; border:1px solid #222; border-radius:16px; padding:24px; }
        .datatype-header { display:flex; align-items:center; gap:12px; margin-bottom:16px; }
        .datatype-icon { font-size:28px; }
        .datatype-name { font-size:16px; font-weight:800; color:#00d4ff; }
        .datatype-visual { background:#0f0f0f; border:1px solid #1a1a1a; border-radius:10px; padding:14px; margin:12px 0; font-family:monospace; font-size:12px; color:#aaa; }
        .datatype-use { font-size:12px; color:#666; }
        .datatype-example { font-size:11px; color:#555; margin-top:8px; font-style:italic; }

        /* ── NINES TABLE ── */
        .nines-table { width:100%; max-width:800px; margin:0 auto; }
        .nines-row { display:flex; align-items:center; gap:14px; padding:10px 0; border-bottom:1px solid #1a1a1a; }
        .nines-percent { font-size:15px; font-weight:800; color:#00d4ff; width:90px; }
        .nines-bar-bg { flex:1; height:7px; background:#1a1a1a; border-radius:4px; overflow:hidden; }
        .nines-bar-fill { height:100%; border-radius:4px; background:linear-gradient(90deg,#00d4ff,#00ff88); }
        .nines-downtime { font-size:12px; color:#777; width:140px; text-align:right; }

        /* ── RABBITMQ EXCHANGE ── */
        .exchange-diagram { background:#0f0f0f; border:1px solid #222; border-radius:20px; padding:36px; margin:30px auto; max-width:1100px; }
        .exchange-title { font-size:18px; font-weight:800; color:#00d4ff; margin-bottom:30px; text-align:center; }
        .exchange-visual { display:flex; align-items:center; justify-content:center; gap:20px; flex-wrap:wrap; }
        .exchange-box {
            background:linear-gradient(135deg,#1a2a1a,#1a3a2a);
            border:2px solid #00ff8844;
            border-radius:14px;
            padding:16px 24px;
            text-align:center;
            min-width:120px;
        }
        .exchange-box .ex-icon { font-size:28px; margin-bottom:6px; }
        .exchange-box .ex-name { font-size:13px; font-weight:800; color:#00ff88; }
        .exchange-box .ex-rule { font-size:11px; color:#555; margin-top:4px; }
        .producer-box {
            background:linear-gradient(135deg,#1a1a2e,#1a2a3e);
            border:2px solid #00d4ff44;
            border-radius:12px;
            padding:14px 20px;
            text-align:center;
        }
        .queue-box {
            background:linear-gradient(135deg,#2a1a1a,#3a1a1a);
            border:2px solid #ff8c0044;
            border-radius:10px;
            padding:10px 16px;
            text-align:center;
            font-size:12px;
            color:#ff8c00;
            font-weight:700;
        }

        /* ── SOCKET ── */
        .socket-visual { background:#0f0f0f; border:1px solid #222; border-radius:20px; padding:36px; margin:30px auto; max-width:1100px; }

        /* ── URL SHORTENER ── */
        .url-flow { background:#0f0f0f; border:1px solid #222; border-radius:20px; padding:36px; margin:30px auto; max-width:1100px; }

        /* ── FOOTER ── */
        .footer { background:#050505; padding:60px 40px; text-align:center; border-top:1px solid #111; }
        .footer-logo { font-size:26px; font-weight:900; background:linear-gradient(135deg,#00d4ff,#fff); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; margin-bottom:14px; }
        .footer-text { font-size:13px; color:#333; margin-bottom:6px; }

        /* ── RESPONSIVE ── */
        @media(max-width:768px) {
            .cover-title { font-size:32px; }
            .cover-modules { grid-template-columns:repeat(2,1fr); }
            .toc-grid { grid-template-columns:1fr; }
            .concept-grid { grid-template-columns:1fr; }
            .two-col { grid-template-columns:1fr; }
            .module-title { font-size:28px; }
            .cover-stats { gap:20px; }
        }

        @media print {
            body { background:white; color:black; }
            .cover { background:#f0f8ff; min-height:auto; }
            .module-section { padding:30px 20px; }
        }

        /* animations */
        @keyframes fadeUp { from{opacity:0;transform:translateY(20px)} to{opacity:1;transform:translateY(0)} }
        .animate-in { animation:fadeUp 0.5s ease forwards; }

        .highlight-blue { color:#00d4ff; font-weight:700; }
        .highlight-green { color:#00ff88; font-weight:700; }
        .highlight-orange { color:#ff8c00; font-weight:700; }
        .highlight-red { color:#ff4444; font-weight:700; }
        .highlight-yellow { color:#ffd700; font-weight:700; }

        /* Full-width wrapper for sections */
        .full-section {
            background: inherit;
            padding: 80px 0;
            border-bottom: 2px solid #111;
        }
        .full-section:nth-child(even) { background: #0d0d0d; }
        .full-section > .module-section { border-bottom: none; padding: 0 40px; }
    </style>
</head>
<body>

<!-- ══════════════════════════════════════
     COVER
══════════════════════════════════════ -->
<div class="cover">
    <div class="cover-badge">📚 সম্পূর্ণ গাইড ২০২৪ — বাংলায়</div>
    <h1 class="cover-title">System Design &<br>Backend Engineering</h1>
    <p class="cover-subtitle">Module 1 → Module 12 | সহজ বাংলায় | ভিজুয়াল পদ্ধতিতে</p>

    <div class="cover-modules">
        <div class="cover-module-card"><div class="mc-icon">🏗️</div><div class="mc-name">M1: System Design Basics</div></div>
        <div class="cover-module-card"><div class="mc-icon">🧮</div><div class="mc-name">M2: Mathematics</div></div>
        <div class="cover-module-card"><div class="mc-icon">🟢</div><div class="mc-name">M3: Node.js API</div></div>
        <div class="cover-module-card"><div class="mc-icon">🚦</div><div class="mc-name">M4: Rate Limiting</div></div>
        <div class="cover-module-card"><div class="mc-icon">☁️</div><div class="mc-name">M6: AWS Scaling</div></div>
        <div class="cover-module-card"><div class="mc-icon">🐳</div><div class="mc-name">M7: Docker</div></div>
        <div class="cover-module-card"><div class="mc-icon">🌐</div><div class="mc-name">M8: Microservice Net</div></div>
        <div class="cover-module-card"><div class="mc-icon">⚡</div><div class="mc-name">M9: Redis</div></div>
        <div class="cover-module-card"><div class="mc-icon">🐰</div><div class="mc-name">M10: RabbitMQ</div></div>
        <div class="cover-module-card"><div class="mc-icon">🔌</div><div class="mc-name">M11: Socket</div></div>
        <div class="cover-module-card"><div class="mc-icon">🔗</div><div class="mc-name">M12: URL Shortener</div></div>
        <div class="cover-module-card"><div class="mc-icon">🎯</div><div class="mc-name">সব বাংলায়</div></div>
    </div>

    <div class="cover-stats">
        <div class="stat"><div class="stat-number">12</div><div class="stat-label">মডিউল</div></div>
        <div class="stat"><div class="stat-number">80+</div><div class="stat-label">ভিজুয়াল ডায়াগ্রাম</div></div>
        <div class="stat"><div class="stat-number">150+</div><div class="stat-label">বাংলা উদাহরণ</div></div>
        <div class="stat"><div class="stat-number">∞</div><div class="stat-label">জ্ঞান</div></div>
    </div>
</div>

<!-- ══════════════════════════════════════
     TOC
══════════════════════════════════════ -->
<div class="toc" id="toc">
    <h2 class="toc-title">📋 বিষয়সূচি</h2>
    <div class="toc-grid">
        <a href="#module1" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">1</div><div class="toc-module-title">🏗️ System Design Basics</div></div>
            <div class="toc-topics">Networking • Consistency • Failure Models • CAP Theorem</div>
        </a>
        <a href="#module2" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">2</div><div class="toc-module-title">🧮 Mathematics</div></div>
            <div class="toc-topics">Latency • RPS • Storage • Bandwidth • Availability • Scalability</div>
        </a>
        <a href="#module3" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">3</div><div class="toc-module-title">🟢 Node.js API</div></div>
            <div class="toc-topics">ES6 • Async • Express • PostgreSQL • Microservices</div>
        </a>
        <a href="#module4" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">4</div><div class="toc-module-title">🚦 Rate Limiting</div></div>
            <div class="toc-topics">Token Bucket • Sliding Window • Nginx • Microservice</div>
        </a>
        <a href="#module6" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">6</div><div class="toc-module-title">☁️ AWS Scaling</div></div>
            <div class="toc-topics">VPC • EC2 • RDS • Auto Scaling • Load Balancer</div>
        </a>
        <a href="#module7" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">7</div><div class="toc-module-title">🐳 Docker</div></div>
            <div class="toc-topics">Dockerfile • MySQL Replication • Redis • Kafka • Nginx LB</div>
        </a>
        <a href="#module8" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">8</div><div class="toc-module-title">🌐 Microservice Networking</div></div>
            <div class="toc-topics">Namespace • veth • Bridge • iptables NAT</div>
        </a>
        <a href="#module9" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">9</div><div class="toc-module-title">⚡ Redis</div></div>
            <div class="toc-topics">Data Types • TTL • Transactions • Streams • Geo • Sharding</div>
        </a>
        <a href="#module10" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">10</div><div class="toc-module-title">🐰 RabbitMQ</div></div>
            <div class="toc-topics">Exchange Types • Routing • Fanout • Topic • Header</div>
        </a>
        <a href="#module11" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">11</div><div class="toc-module-title">🔌 Socket</div></div>
            <div class="toc-topics">Socket.io • Rooms • Broadcasting • Chat App Design</div>
        </a>
        <a href="#module12" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">12</div><div class="toc-module-title">🔗 URL Shortener</div></div>
            <div class="toc-topics">System Design • Architecture • Nginx L7 LB</div>
        </a>
        <a href="#summary" class="toc-item">
            <div class="toc-item-header"><div class="toc-num">✓</div><div class="toc-module-title">🎯 সম্পূর্ণ সারসংক্ষেপ</div></div>
            <div class="toc-topics">Quick Reference • Interview Tips • রোডম্যাপ</div>
        </a>
    </div>
</div>

<!-- ══════════════════════════════════════
     MODULE 1
══════════════════════════════════════ -->
<div class="full-section" id="module1">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 01</div>
        <h2 class="module-title">🏗️ System Design Basics</h2>
        <p class="module-subtitle">নেটওয়ার্কিং থেকে CAP Theorem — সব বাংলায়</p>
    </div>

    <h3 class="subsection-title">📡 Networking Basics</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">📮</div>
            <div class="card-title">IP Address</div>
            <div class="card-desc">প্রতিটা ডিভাইসের ইউনিক ঠিকানা। বাড়ির ডাক ঠিকানার মতো। Public IP = বাইরের ঠিকানা। Private IP = ভেতরের রুম নম্বর।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🚪</div>
            <div class="card-title">Port</div>
            <div class="card-desc">সার্ভারের বিভিন্ন দরজা। 80=HTTP, 443=HTTPS, 3306=MySQL, 5432=PostgreSQL, 6379=Redis। একটা IP তে অনেক সেবা।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📖</div>
            <div class="card-title">DNS</div>
            <div class="card-desc">ফোনবুক। google.com → 142.250.190.14। নাম লিখলে DNS IP খুঁজে দেয়। Recursive ও Authoritative DNS আছে।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🤝</div>
            <div class="card-title">Protocol</div>
            <div class="card-desc">HTTP = ওয়েব। HTTPS = সুরক্ষিত ওয়েব। TCP = নির্ভরযোগ্য (ব্যাংক)। UDP = দ্রুত (গেম, ভিডিও)।</div>
        </div>
        <div class="concept-card pink">
            <div class="card-icon">🔄</div>
            <div class="card-title">Abstraction</div>
            <div class="card-desc">গাড়ি চালাতে ইঞ্জিন জানা লাগে না। API call করলে নেটওয়ার্কের ভেতরে কী হয় জানা দরকার নেই। সহজ interface দিয়ে জটিল কাজ।</div>
        </div>
        <div class="concept-card yellow">
            <div class="card-icon">🌐</div>
            <div class="card-title">Load Balancer</div>
            <div class="card-desc">ব্যাংকের টোকেন মেশিন। ১০০ জন কাস্টমার → ৫টা কাউন্টারে ভাগ। Traffic ভাগ করে সার্ভারে চাপ কমায়।</div>
        </div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🔄 Consistency Models</h3>
    <table class="comparison-table">
        <tr><th>Model</th><th>কীভাবে কাজ করে</th><th>গতি</th><th>উদাহরণ</th></tr>
        <tr><td><span class="badge badge-red">Strict</span></td><td>লিখলে সবাই সাথে সাথে দেখে</td><td>🐢 সবচেয়ে ধীর</td><td>ব্যাংকিং সিস্টেম</td></tr>
        <tr><td><span class="badge badge-yellow">Sequential</span></td><td>সবাই একই ক্রমে দেখে</td><td>🚶 ধীর</td><td>Distributed Log</td></tr>
        <tr><td><span class="badge badge-blue">Causal</span></td><td>সম্পর্কিত ঘটনা সঠিক ক্রমে</td><td>🚴 মাঝারি</td><td>Facebook Comments</td></tr>
        <tr><td><span class="badge badge-green">Eventual</span></td><td>শেষ পর্যন্ত একই হবে</td><td>🚀 দ্রুত</td><td>Instagram Likes</td></tr>
    </table>

    <div class="section-divider"></div>
    <h3 class="subsection-title">💥 Failure Models (সহজ → কঠিন)</h3>
    <div class="flow-container">
        <div class="flow-title">ব্যর্থতার ধরন</div>
        <div class="flow-row">
            <div class="flow-box"><div class="fb-icon">🛑</div><div class="fb-label">Fail-Stop</div><div class="fb-sub">জানিয়ে বন্ধ</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">💀</div><div class="fb-label">Crash</div><div class="fb-sub">নীরবে বন্ধ</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">📭</div><div class="fb-label">Omission</div><div class="fb-sub">বার্তা হারায়</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">⏰</div><div class="fb-label">Temporal</div><div class="fb-sub">দেরি করে</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">😈</div><div class="fb-label">Byzantine</div><div class="fb-sub">মিথ্যা বলে</div></div>
        </div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">⚖️ CAP Theorem</h3>
    <div class="arch-diagram">
        <div class="arch-title">৩টার মধ্যে সর্বোচ্চ ২টা পাবে!</div>
        <div style="display:flex;justify-content:center;gap:40px;flex-wrap:wrap;margin:30px 0;">
            <div style="text-align:center;"><div style="font-size:44px;">🎯</div><div style="font-size:18px;font-weight:900;color:#00d4ff;margin:8px 0;">C — Consistency</div><div style="font-size:12px;color:#555;">সব সার্ভার একই ডাটা দেখায়</div></div>
            <div style="text-align:center;"><div style="font-size:44px;">✅</div><div style="font-size:18px;font-weight:900;color:#00ff88;margin:8px 0;">A — Availability</div><div style="font-size:12px;color:#555;">সবসময় কাজ করে</div></div>
            <div style="text-align:center;"><div style="font-size:44px;">🛡️</div><div style="font-size:18px;font-weight:900;color:#b44fff;margin:8px 0;">P — Partition Tolerance</div><div style="font-size:12px;color:#555;">নেটওয়ার্ক কাটলেও চলে</div></div>
        </div>
        <table class="comparison-table" style="margin-top:10px;">
            <tr><th>Choice</th><th>পায়</th><th>হারায়</th><th>উদাহরণ</th></tr>
            <tr><td><span class="badge badge-blue">CP</span></td><td>সঠিক ডাটা + Network resilience</td><td>কখনো unavailable</td><td>🏦 ব্যাংক, MongoDB</td></tr>
            <tr><td><span class="badge badge-green">AP</span></td><td>সবসময় চলে + Network resilience</td><td>পুরানো ডাটা দেখায়</td><td>📱 Facebook, Cassandra</td></tr>
            <tr><td><span class="badge badge-yellow">CA</span></td><td>সঠিক ডাটা + সবসময় চলে</td><td>Network partition এ ব্যর্থ</td><td>🖥️ Single Server DB</td></tr>
        </table>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 2
══════════════════════════════════════ -->
<div class="full-section" id="module2">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 02</div>
        <h2 class="module-title">🧮 Mathematics for System Design</h2>
        <p class="module-subtitle">Estimation, Latency, Scalability — সব হিসাব বাংলায়</p>
    </div>

    <h3 class="subsection-title">📏 Key Numbers</h3>
    <div class="metrics-grid">
        <div class="metric-card"><div class="metric-value">1 KB</div><div class="metric-label">= ১,০২৪ bytes</div><div class="metric-desc">ছোট টেক্সট ফাইল</div></div>
        <div class="metric-card"><div class="metric-value">1 MB</div><div class="metric-label">= ১,০২৪ KB</div><div class="metric-desc">একটা ছবি/গান</div></div>
        <div class="metric-card"><div class="metric-value">1 GB</div><div class="metric-label">= ১,০২৪ MB</div><div class="metric-desc">একটা মুভি</div></div>
        <div class="metric-card"><div class="metric-value">1 TB</div><div class="metric-label">= ১,০২৪ GB</div><div class="metric-desc">বড় Database</div></div>
        <div class="metric-card"><div class="metric-value">86,400</div><div class="metric-label">= ১ দিনের সেকেন্ড</div><div class="metric-desc">RPS হিসাবের ভাজক</div></div>
        <div class="metric-card"><div class="metric-value">×3</div><div class="metric-label">Peak Multiplier</div><div class="metric-desc">Average → Peak</div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">⏱️ Latency Numbers — মনে রাখো!</h3>
    <table class="comparison-table">
        <tr><th>অপারেশন</th><th>সময়</th><th>বাস্তব তুলনা</th><th>মনে রাখার উপায়</th></tr>
        <tr><td>⚡ L1 Cache</td><td><span class="badge badge-green">1 ns</span></td><td>চোখের পলক</td><td>সবচেয়ে দ্রুত!</td></tr>
        <tr><td>⚡ L2 Cache</td><td><span class="badge badge-green">4 ns</span></td><td>L1 × 4</td><td>এখনো দ্রুত</td></tr>
        <tr><td>💻 RAM</td><td><span class="badge badge-blue">100 ns</span></td><td>চা বানানো (~1.5 min)</td><td>L1 × 100</td></tr>
        <tr><td>💾 SSD</td><td><span class="badge badge-yellow">100 μs</span></td><td>১ দিন ৩ ঘণ্টা</td><td>RAM × 1000</td></tr>
        <tr><td>💿 HDD</td><td><span class="badge badge-red">10 ms</span></td><td>প্রায় ২ সপ্তাহ</td><td>SSD × 100</td></tr>
        <tr><td>🌐 Network (Same city)</td><td><span class="badge badge-yellow">1 ms</span></td><td>শহরের মধ্যে</td><td>ঢাকা → ঢাকা</td></tr>
        <tr><td>🌍 Network (Global)</td><td><span class="badge badge-red">150 ms</span></td><td>৯.৫ বছর!</td><td>ঢাকা → আমেরিকা</td></tr>
    </table>

    <div class="section-divider"></div>
    <h3 class="subsection-title">📊 RPS Estimation Formula</h3>
    <div class="flow-container">
        <div class="flow-title">হিসাবের সূত্র</div>
        <div class="flow-row">
            <div class="flow-box"><div class="fb-icon">👥</div><div class="fb-label">DAU</div><div class="fb-sub">দৈনিক User</div></div>
            <div class="flow-arrow">×</div>
            <div class="flow-box"><div class="fb-icon">📱</div><div class="fb-label">Requests/User</div><div class="fb-sub">দৈনিক Actions</div></div>
            <div class="flow-arrow">÷</div>
            <div class="flow-box"><div class="fb-icon">⏰</div><div class="fb-label">86,400</div><div class="fb-sub">দিনের সেকেন্ড</div></div>
            <div class="flow-arrow">=</div>
            <div class="flow-box"><div class="fb-icon">⚡</div><div class="fb-label">Average RPS</div><div class="fb-sub">×3 = Peak</div></div>
        </div>
        <div style="margin-top:20px;padding:16px;background:#141414;border-radius:10px;font-size:13px;color:#aaa;text-align:center;">
            <strong style="color:#00d4ff;">Twitter উদাহরণ:</strong> 300M DAU × 20 reads ÷ 86,400 = <strong style="color:#00ff88;">~70,000 RPS</strong> | Peak = 70,000 × 3 = <strong style="color:#ff8c00;">210,000 RPS!</strong>
        </div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Availability Nines</h3>
    <div class="flow-container">
        <div class="flow-title">বছরে কতক্ষণ বন্ধ থাকে?</div>
        <div class="nines-table">
            <div class="nines-row"><div class="nines-percent">90%</div><div class="nines-bar-bg"><div class="nines-bar-fill" style="width:10%;background:#ff4444;"></div></div><div class="nines-downtime">😰 36.5 দিন বন্ধ</div></div>
            <div class="nines-row"><div class="nines-percent">99%</div><div class="nines-bar-bg"><div class="nines-bar-fill" style="width:35%;background:#ff8c00;"></div></div><div class="nines-downtime">😟 3.65 দিন বন্ধ</div></div>
            <div class="nines-row"><div class="nines-percent">99.9%</div><div class="nines-bar-bg"><div class="nines-bar-fill" style="width:60%;background:#ffd700;"></div></div><div class="nines-downtime">😐 8.76 ঘণ্টা বন্ধ</div></div>
            <div class="nines-row"><div class="nines-percent">99.99%</div><div class="nines-bar-bg"><div class="nines-bar-fill" style="width:83%;"></div></div><div class="nines-downtime">😊 52.6 মিনিট বন্ধ</div></div>
            <div class="nines-row"><div class="nines-percent">99.999%</div><div class="nines-bar-bg"><div class="nines-bar-fill" style="width:97%;"></div></div><div class="nines-downtime">🌟 5.26 মিনিট বন্ধ</div></div>
        </div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Scalability</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>⬆️ Vertical Scaling</h4>
            <ul>
                <li>✅ সহজ, কোড বদলায় না</li>
                <li>✅ ছোট প্রজেক্টে ভালো</li>
                <li>❌ সীমা আছে</li>
                <li>❌ Single point of failure</li>
                <li>💰 ব্যয়বহুল</li>
                <li>🏠 ছোট দোকান → বড় দোকান</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>➡️ Horizontal Scaling</h4>
            <ul>
                <li>✅ সীমাহীন বৃদ্ধি</li>
                <li>✅ একটা নষ্ট হলেও চলে</li>
                <li>❌ জটিল, LB লাগে</li>
                <li>❌ Distributed system challenge</li>
                <li>✅ সাশ্রয়ী</li>
                <li>🏠 ১টা দোকান → চেইন শপ</li>
            </ul>
        </div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 3
══════════════════════════════════════ -->
<div class="full-section" id="module3">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 03</div>
        <h2 class="module-title">🟢 Node.js API Development</h2>
        <p class="module-subtitle">Backend Development — Express থেকে Microservices পর্যন্ত</p>
    </div>

    <h3 class="subsection-title">🟢 Node.js মূল ধারণা</h3>
    <div class="concept-grid">
        <div class="concept-card"><div class="card-icon">🌐</div><div class="card-title">Browser JS vs Node.js</div><div class="card-desc">Browser JS = শুধু ওয়েবপেজে। Node.js = Server এ চলে। File পড়তে পারে, Database connect করে, API বানায়।</div></div>
        <div class="concept-card green"><div class="card-icon">🔄</div><div class="card-title">Event Loop</div><div class="card-desc">Non-blocking। একটা কাজ শেষ না হলেও অন্য কাজ শুরু করে। রেস্টুরেন্টের ওয়েটারের মতো — একসাথে অনেক টেবিল সামলায়।</div></div>
        <div class="concept-card purple"><div class="card-icon">📦</div><div class="card-title">NPM Packages</div><div class="card-desc">হাজারো ready-made package। express, axios, pg, ioredis, kafkajs — সব npm install করে ব্যবহার করো।</div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🔄 Async Programming</h3>
    <div class="timeline">
        <div class="timeline-item"><div class="timeline-dot">1️⃣</div><div class="timeline-content"><h4>😵 Callback</h4><p>পুরানো পদ্ধতি। সমস্যা: Callback Hell। একের ভেতরে আরেক function। "Pyramid of Doom" নামে পরিচিত।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">2️⃣</div><div class="timeline-content"><h4>😐 Promise</h4><p>উন্নত পদ্ধতি। তিনটা অবস্থা: Pending, Resolved, Rejected। .then().catch() দিয়ে chain করো।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">3️⃣</div><div class="timeline-content"><h4>😊 Async/Await</h4><p>সেরা পদ্ধতি। সহজ, পরিষ্কার। try/catch দিয়ে error handle। আজকাল সবাই এটাই ব্যবহার করে।</p></div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🚀 Express API — HTTP Methods</h3>
    <table class="comparison-table">
        <tr><th>Method</th><th>কাজ</th><th>URL</th><th>Status</th></tr>
        <tr><td><span class="badge badge-green">GET</span></td><td>পড়া</td><td>/api/users</td><td>200 OK</td></tr>
        <tr><td><span class="badge badge-blue">POST</span></td><td>তৈরি</td><td>/api/users</td><td>201 Created</td></tr>
        <tr><td><span class="badge badge-yellow">PUT</span></td><td>পুরো Update</td><td>/api/users/:id</td><td>200 OK</td></tr>
        <tr><td><span class="badge badge-yellow">PATCH</span></td><td>আংশিক Update</td><td>/api/users/:id</td><td>200 OK</td></tr>
        <tr><td><span class="badge badge-red">DELETE</span></td><td>মুছা</td><td>/api/users/:id</td><td>200 OK</td></tr>
    </table>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ Enterprise Architecture</h3>
    <div class="arch-diagram">
        <div class="arch-title">Layer Architecture</div>
        <div class="arch-layer highlight"><div class="arch-node"><div class="node-icon">👤</div><div class="node-label">Client</div><div class="node-sub">HTTP Request</div></div></div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer"><div class="arch-node"><div class="node-icon">🛣️</div><div class="node-label">Routes</div><div class="node-sub">URL → Controller</div></div></div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer"><div class="arch-node"><div class="node-icon">🎮</div><div class="node-label">Controller</div><div class="node-sub">Request/Response</div></div></div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer"><div class="arch-node"><div class="node-icon">⚙️</div><div class="node-label">Service</div><div class="node-sub">Business Logic</div></div></div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer"><div class="arch-node"><div class="node-icon">🗄️</div><div class="node-label">Repository</div><div class="node-sub">DB Query</div></div></div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer highlight"><div class="arch-node"><div class="node-icon">💾</div><div class="node-label">Database</div><div class="node-sub">PostgreSQL</div></div></div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 4
══════════════════════════════════════ -->
<div class="full-section" id="module4">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 04</div>
        <h2 class="module-title">🚦 Rate Limit Module</h2>
        <p class="module-subtitle">সিস্টেম সুরক্ষা — DDoS থেকে Business Model</p>
    </div>

    <h3 class="subsection-title">🤔 কেন দরকার?</h3>
    <div class="concept-grid">
        <div class="concept-card"><div class="card-icon">🛡️</div><div class="card-title">DDoS রোধ</div><div class="card-desc">হাজারো ভুয়া request → সার্ভার crash। Rate Limit → সর্বোচ্চ ১০০ → সার্ভার নিরাপদ।</div></div>
        <div class="concept-card green"><div class="card-icon">💰</div><div class="card-title">Resource সাশ্রয়</div><div class="card-desc">প্রতিটা request = CPU + RAM + DB খরচ। Rate Limit = বিল কমাও।</div></div>
        <div class="concept-card purple"><div class="card-icon">⚖️</div><div class="card-title">সমান সুযোগ</div><div class="card-desc">১ জন সব নিলে বাকিরা পাবে না। Rate Limit = Fair use।</div></div>
        <div class="concept-card orange"><div class="card-icon">🔐</div><div class="card-title">Brute Force রোধ</div><div class="card-desc">৫ বার ভুল password → ১ ঘণ্টা block!

</div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🔢 Algorithms তুলনা</h3>
    <table class="comparison-table">
        <tr><th>Algorithm</th><th>কীভাবে</th><th>Burst</th><th>Memory</th><th>সেরা জন্য</th></tr>
        <tr><td>🪣 Token Bucket</td><td>বালতিতে টোকেন</td><td><span class="badge badge-green">✅</span></td><td>কম</td><td>API Throttling</td></tr>
        <tr><td>🚰 Leaky Bucket</td><td>ধীরে চুইয়ে পড়ে</td><td><span class="badge badge-red">❌</span></td><td>কম</td><td>Traffic Shaping</td></tr>
        <tr><td>📅 Fixed Window</td><td>নির্দিষ্ট সময়ে রিসেট</td><td><span class="badge badge-yellow">⚠️ Window শেষে</span></td><td>সবচেয়ে কম</td><td>Simple cases</td></tr>
        <tr><td>🔄 Sliding Window</td><td>সবসময় "গত X সেকেন্ড"</td><td><span class="badge badge-red">❌</span></td><td>বেশি</td><td>Production ✅</td></tr>
    </table>

    <div class="info-box tip">
        <div class="info-icon">🏆</div>
        <div class="info-content"><div class="info-title">Production সেরা পছন্দ</div><p><strong>Sliding Window Counter + Redis</strong> = সবচেয়ে ভালো। Nginx দিয়ে প্রথম স্তর + Application level = Defense in Depth!</p></div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 6
══════════════════════════════════════ -->
<div class="full-section" id="module6">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 06</div>
        <h2 class="module-title">☁️ AWS For Scaling</h2>
        <p class="module-subtitle">Cloud Infrastructure — VPC থেকে Auto Scaling</p>
    </div>

    <h3 class="subsection-title">☁️ AWS সেবাগুলো</h3>
    <table class="comparison-table">
        <tr><th>সেবা</th><th>তুলনা</th><th>কাজ</th></tr>
        <tr><td>🏗️ VPC</td><td>জমি/প্লট</td><td>নিজের নেটওয়ার্ক</td></tr>
        <tr><td>🖥️ EC2</td><td>ঘর</td><td>ভার্চুয়াল সার্ভার</td></tr>
        <tr><td>📦 S3</td><td>গুদাম</td><td>File Storage (অসীম)</td></tr>
        <tr><td>🗄️ RDS</td><td>আলমারি</td><td>Managed Database</td></tr>
        <tr><td>⚖️ ELB</td><td>টোকেন মেশিন</td><td>Load Balancer</td></tr>
        <tr><td>📈 Auto Scaling</td><td>চাহিদামতো বড়-ছোট</td><td>স্বয়ংক্রিয় Scaling</td></tr>
        <tr><td>⚡ ElastiCache</td><td>টেবিলের উপর</td><td>Redis/Memcached Cache</td></tr>
        <tr><td>🔐 IAM</td><td>চাবি/পাস</td><td>Access Control</td></tr>
    </table>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ VPC Design</h3>
    <div class="arch-diagram">
        <div class="arch-title">সম্পূর্ণ VPC Architecture</div>
        <div style="font-size:12px;color:#555;margin-bottom:20px;">Internet → IGW → Public → Private → DB (নিরাপত্তার স্তর বাড়ে)</div>
        <div style="border:2px dashed #00d4ff33;border-radius:14px;padding:16px;margin:8px 0;">
            <div style="font-size:11px;color:#00d4ff;font-weight:700;margin-bottom:12px;">🌐 PUBLIC SUBNET — বৈঠকখানা</div>
            <div style="display:flex;gap:12px;justify-content:center;flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">⚖️</div><div class="node-label">ALB</div></div>
                <div class="arch-node"><div class="node-icon">🌐</div><div class="node-label">NAT Gateway</div></div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div style="border:2px dashed #00ff8833;border-radius:14px;padding:16px;margin:8px 0;">
            <div style="font-size:11px;color:#00ff88;font-weight:700;margin-bottom:12px;">🔒 PRIVATE SUBNET — শোবার ঘর</div>
            <div style="display:flex;gap:12px;justify-content:center;flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">🖥️</div><div class="node-label">EC2 App 1</div></div>
                <div class="arch-node"><div class="node-icon">🖥️</div><div class="node-label">EC2 App 2</div></div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div style="border:2px dashed #ff8c0033;border-radius:14px;padding:16px;margin:8px 0;">
            <div style="font-size:11px;color:#ff8c00;font-weight:700;margin-bottom:12px;">🔒🔒 DB SUBNET — সিন্দুক</div>
            <div style="display:flex;gap:12px;justify-content:center;flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">RDS Primary (AZ-a)</div></div>
                <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">RDS Standby (AZ-b)</div></div>
            </div>
        </div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 7
══════════════════════════════════════ -->
<div class="full-section" id="module7">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 07</div>
        <h2 class="module-title">🐳 Docker For Backend Engineers</h2>
        <p class="module-subtitle">Container থেকে Microservice Deployment</p>
    </div>

    <h3 class="subsection-title">🐳 Docker মূল ধারণা</h3>
    <div class="flow-container">
        <div class="flow-title">Dockerfile → Image → Container</div>
        <div class="flow-row">
            <div class="flow-box"><div class="fb-icon">📝</div><div class="fb-label">Dockerfile</div><div class="fb-sub">রেসিপি</div></div>
            <div class="flow-arrow">→ build →</div>
            <div class="flow-box"><div class="fb-icon">📸</div><div class="fb-label">Image</div><div class="fb-sub">ছাঁচ (Read-only)</div></div>
            <div class="flow-arrow">→ run →</div>
            <div class="flow-box"><div class="fb-icon">📦</div><div class="fb-label">Container</div><div class="fb-sub">চলমান অ্যাপ</div></div>
        </div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">✅ Dockerfile Best Practices</h3>
    <div class="concept-grid">
        <div class="concept-card"><div class="card-icon">🪶</div><div class="card-title">Alpine Image</div><div class="card-desc">node:18 = 900MB। node:18-alpine = 120MB। সবসময় Alpine ব্যবহার করো।</div></div>
        <div class="concept-card green"><div class="card-icon">🏗️</div><div class="card-title">Multi-stage Build</div><div class="card-desc">Build stage আলাদা, production আলাদা। Dev tools Production Image এ থাকে না।</div></div>
        <div class="concept-card purple"><div class="card-icon">👤</div><div class="card-title">Non-root User</div><div class="card-desc">Root user = হ্যাকারের স্বপ্ন! Non-root user create করে run করো।</div></div>
        <div class="concept-card orange"><div class="card-icon">📦</div><div class="card-title">Layer Cache</div><div class="card-desc">package.json আগে COPY → কম বদলানো জিনিস উপরে রাখো।</div></div>
        <div class="concept-card pink"><div class="card-icon">🏥</div><div class="card-title">Health Check</div><div class="card-desc">HEALTHCHECK দিয়ে Docker জানে Container সুস্থ আছে কিনা।</div></div>
        <div class="concept-card yellow"><div class="card-icon">🏷️</div><div class="card-title">Specific Version</div><div class="card-desc">node:latest ❌। node:18.17.0-alpine ✅। নির্দিষ্ট version ব্যবহার করো।</div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">⚖️ Layer 4 vs Layer 7 Load Balancer</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>📦 Layer 4 — TCP/UDP</h4>
            <ul>
                <li>✅ IP + Port দেখে শুধু</li>
                <li>✅ অনেক দ্রুত</li>
                <li>❌ URL/Header দেখে না</li>
                <li>🏠 ডাক সোর্টার — ঠিকানা দেখে</li>
                <li>📌 Database LB এর জন্য</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>🧠 Layer 7 — HTTP</h4>
            <ul>
                <li>✅ URL, Header, Cookie দেখে</li>
                <li>✅ Smart routing</li>
                <li>✅ SSL termination</li>
                <li>🏠 রিসেপশনিস্ট — উদ্দেশ্য বোঝে</li>
                <li>📌 Web App LB এর জন্য</li>
            </ul>
        </div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 8
══════════════════════════════════════ -->
<div class="full-section" id="module8">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 08</div>
        <h2 class="module-title">🌐 Microservice Networking</h2>
        <p class="module-subtitle">Linux Namespace থেকে Bridge — Docker এর রহস্য</p>
    </div>

    <h3 class="subsection-title">🐧 Linux Networking মূল কমান্ড</h3>
    <div class="concept-grid">
        <div class="concept-card"><div class="card-icon">🔌</div><div class="card-title">ip addr show</div><div class="card-desc">সব Network Interface দেখো। IP Address, MAC Address। পুরানো: ifconfig।</div></div>
        <div class="concept-card green"><div class="card-icon">🗺️</div><div class="card-title">ip route show</div><div class="card-desc">Routing Table দেখো। কোন নেটওয়ার্কে কোন পথে যাবে। Default Gateway দেখো।</div></div>
        <div class="concept-card purple"><div class="card-icon">🔗</div><div class="card-title">ss -tuln</div><div class="card-desc">Active Connections দেখো। কোন Port Listening। পুরানো: netstat -tuln।</div></div>
        <div class="concept-card orange"><div class="card-icon">🛡️</div><div class="card-title">iptables</div><div class="card-desc">Linux Firewall। Port allow/block। NAT করো। Docker এটাই ব্যবহার করে!</div></div>
    </div>

    <div class="section-divider"></div>
    <h3 class="subsection-title">🔲 Network Namespace সংযোগ</h3>
    <div class="steps-container">
        <div class="step-item"><div class="step-number">1</div><div class="step-content"><h4>Namespace তৈরি</h4><p>ip netns add ns_red — আলাদা নেটওয়ার্ক পরিবেশ। বিল্ডিংয়ের আলাদা ফ্লোর। নিজস্ব IP, Route, Interface।</p></div></div>
        <div class="step-item"><div class="step-number">2</div><div class="step-content"><h4>veth Pair তৈরি</h4><p>দুই মাথার Virtual Cable। এক মাথা Host এ, অন্য মাথা Namespace এ। টিনের কৌটা টেলিফোনের মতো।</p></div></div>
        <div class="step-item"><div class="step-number">3</div><div class="step-content"><h4>Bridge তৈরি</h4><p>Virtual Switch। অনেক Namespace Bridge এ যুক্ত। সবাই সবার সাথে কথা বলতে পারে।</p></div></div>
        <div class="step-item"><div class="step-number">4</div><div class="step-content"><h4>Bridge এ IP + NAT</h4><p>Bridge এ IP দাও → Host যুক্ত হয়। iptables NAT → Namespace → Internet। এটাই Docker!</p></div></div>
    </div>

    <div class="info-box tip">
        <div class="info-icon">🐳</div>
        <div class="info-content"><div class="info-title">Docker = Linux Magic</div><p>Docker Container = Namespace + veth + Bridge (docker0) + iptables NAT। docker run = এই সব স্বয়ংক্রিয়ভাবে হয়!</p></div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 9: REDIS
══════════════════════════════════════ -->
<div class="full-section" id="module9">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 09</div>
        <h2 class="module-title">⚡ Redis</h2>
        <p class="module-subtitle">In-Memory Data Store — ডাটা টাইপ থেকে Sharding পর্যন্ত</p>
    </div>

    <!-- What is Redis -->
    <h3 class="subsection-title">⚡ Redis কী এবং কেন দরকার?</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🧠</div>
            <div class="card-title">Redis কী?</div>
            <div class="card-desc"><strong class="highlight-blue">RE</strong>mote <strong class="highlight-blue">DI</strong>ctionary <strong class="highlight-blue">S</strong>erver। RAM এ ডাটা রাখে → অত্যন্ত দ্রুত! Database = আলমারি (50ms), Redis = টেবিলের উপর (1ms)।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">⚡</div>
            <div class="card-title">কত দ্রুত?</div>
            <div class="card-desc">১ মিলিসেকেন্ড = ১,০০০,০০০ operations/second! PostgreSQL = ~5,000 QPS। Redis = ~100,000 QPS। ২০ গুণ দ্রুত!</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🎯</div>
            <div class="card-title">কেন দরকার?</div>
            <div class="card-desc">Cache (DB চাপ কমাও), Session Store (Login), Rate Limiting, Pub/Sub (Notification), Queue (Background Job), Leaderboard (Sorted Set)।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">📈</div>
            <div class="card-title">Redis Evolution</div>
            <div class="card-desc">2009: Salvatore Sanfilippo তৈরি করেন। Simple Key-Value → Rich Data Structures → Cluster → Streams → Modules। এখন Redis Stack!</div>
        </div>
    </div>

    <!-- Redis Data Types -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📊 Redis Data Types — সব ধরনের ডাটা</h3>

    <div class="datatype-grid">
        <!-- String -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🔤</div>
                <div class="datatype-name">String</div>
            </div>
            <div class="datatype-visual">
SET user:name "রহিম"
GET user:name → "রহিম"
INCR counter → 1, 2, 3...
APPEND key " উদ্দিন"
STRLEN key → 4
            </div>
            <div class="datatype-use">✅ Cache, Counter, Session Token, JSON Store</div>
            <div class="datatype-example">🏠 উদাহরণ: একটা বাক্সে একটাই জিনিস। সংখ্যা, টেক্সট, JSON — সব String।</div>
        </div>

        <!-- Lists -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">📋</div>
                <div class="datatype-name">Lists</div>
            </div>
            <div class="datatype-visual">
LPUSH queue "task1"  ← বাম থেকে
RPUSH queue "task2"  ← ডান থেকে
LPOP queue → "task1"
LRANGE queue 0 -1
LLEN queue → count
            </div>
            <div class="datatype-use">✅ Queue (FIFO), Stack (LIFO), Activity Feed, Recent Items</div>
            <div class="datatype-example">🏠 উদাহরণ: সুপারশপে কাস্টমারের লাইন — যে আগে ঢোকে আগে বের হয়।</div>
        </div>

        <!-- Sets -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🔵</div>
                <div class="datatype-name">Sets</div>
            </div>
            <div class="datatype-visual">
SADD tags "python" "js"
SMEMBERS tags → all
SISMEMBER tags "js" → 1
SUNION set1 set2
SINTER set1 set2
SDIFF set1 set2
            </div>
            <div class="datatype-use">✅ Unique Items, Tags, Followers, Blocking List</div>
            <div class="datatype-example">🏠 উদাহরণ: ব্যাগে জিনিস রাখো — একই জিনিস দুইবার রাখা যাবে না!</div>
        </div>

        <!-- Hashes -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🗂️</div>
                <div class="datatype-name">Hashes</div>
            </div>
            <div class="datatype-visual">
HSET user:1 name "রহিম"
HSET user:1 age 25
HGET user:1 name → "রহিম"
HGETALL user:1 → সব field
HINCRBY user:1 age 1
            </div>
            <div class="datatype-use">✅ Object Store, User Profile, Product Data</div>
            <div class="datatype-example">🏠 উদাহরণ: Excel এর একটা Row — Field:Value জোড়া। Object এর মতো।</div>
        </div>

        <!-- Sorted Sets -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🏆</div>
                <div class="datatype-name">Sorted Sets (ZSet)</div>
            </div>
            <div class="datatype-visual">
ZADD leaderboard 100 "রহিম"
ZADD leaderboard 200 "করিম"
ZRANK leaderboard "রহিম" → 0
ZRANGE lb 0 -1 WITHSCORES
ZREVRANGE lb 0 9 → Top 10
            </div>
            <div class="datatype-use">✅ Leaderboard, Ranking, Priority Queue, Rate Limiting</div>
            <div class="datatype-example">🏠 উদাহরণ: পরীক্ষার মেধাতালিকা — score অনুযায়ী সাজানো।</div>
        </div>

        <!-- Bitmaps -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🔢</div>
                <div class="datatype-name">Bitmaps</div>
            </div>
            <div class="datatype-visual">
SETBIT login:2024 userId 1
GETBIT login:2024 userId
BITCOUNT login:2024
BITOP AND result bm1 bm2
BITPOS key 1 → first bit
            </div>
            <div class="datatype-use">✅ User Activity Tracking, Feature Flags, Daily Login</div>
            <div class="datatype-example">🏠 উদাহরণ: হাজির/অনুপস্থিত রেজিস্টার। প্রতিটা bit = একজন ব্যবহারকারী। ১০ কোটি user = মাত্র ১২ MB!</div>
        </div>

        <!-- HyperLogLog -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🔬</div>
                <div class="datatype-name">HyperLogLog</div>
            </div>
            <div class="datatype-visual">
PFADD visitors "user1" "user2"
PFADD visitors "user1"  ← duplicate!
PFCOUNT visitors → ~2 (unique)
PFMERGE total hll1 hll2
            </div>
            <div class="datatype-use">✅ Unique Visitor Count, Distinct Value Count</div>
            <div class="datatype-example">🏠 উদাহরণ: ওয়েবসাইটে আজ কতজন unique visitor — exact না, কিন্তু ~99% accurate। মাত্র 12KB!</div>
        </div>

        <!-- Streams -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🌊</div>
                <div class="datatype-name">Streams</div>
            </div>
            <div class="datatype-visual">
XADD orders * product "phone"
XREAD COUNT 10 STREAMS orders 0
XGROUP CREATE orders grp $
XREADGROUP GROUP grp c1 > COUNT 10
XACK orders grp id
            </div>
            <div class="datatype-use">✅ Event Sourcing, Message Queue, Real-time Analytics, IoT</div>
            <div class="datatype-example">🏠 উদাহরণ: নদীর স্রোত — ডাটা একমুখী বয়ে যায়। Kafka এর মতো কিন্তু Redis এ।</div>
        </div>

        <!-- Geo -->
        <div class="datatype-card">
            <div class="datatype-header">
                <div class="datatype-icon">🗺️</div>
                <div class="datatype-name">Geo</div>
            </div>
            <div class="datatype-visual">
GEOADD locations 90.4 23.8 "ঢাকা"
GEOADD locations 91.8 22.3 "চট্টগ্রাম"
GEODIST locations ঢাকা চট্টগ্রাম km
GEORADIUS locations 90 23 100 km
GEOPOS locations "ঢাকা"
            </div>
            <div class="datatype-use">✅ Nearby Stores, Ride Sharing, Delivery Tracking</div>
            <div class="datatype-example">🏠 উদাহরণ: Uber — কাছের ড্রাইভার খোঁজো। Sorted Set এর উপরে built।</div>
        </div>
    </div>

    <!-- TTL & Expiration -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">⏰ Expiration & TTL</h3>
    <div class="flow-container">
        <div class="flow-title">TTL — Time To Live (কতক্ষণ থাকবে?)</div>
        <div class="concept-grid" style="margin-top:0;">
            <div class="concept-card">
                <div class="card-icon">⏱️</div>
                <div class="card-title">TTL সেট করো</div>
                <div class="card-desc">
                    <strong>EXPIRE key 3600</strong> → ১ ঘণ্টা পরে মুছে যাবে<br>
                    <strong>SETEX key 60 value</strong> → Set + Expire একসাথে<br>
                    <strong>TTL key</strong> → কত সেকেন্ড বাকি দেখো<br>
                    <strong>PERSIST key</strong> → TTL বাতিল করো (চিরকাল রাখো)<br>
                    TTL -1 = চিরকাল, TTL -2 = নেই (মুছে গেছে)
                </div>
            </div>
            <div class="concept-card green">
                <div class="card-icon">🏠</div>
                <div class="card-title">বাস্তব ব্যবহার</div>
                <div class="card-desc">
                    Session Token → 30 মিনিট TTL<br>
                    OTP Code → 5 মিনিট TTL<br>
                    Rate Limit Counter → 1 মিনিট TTL<br>
                    Cache Data → 1 ঘণ্টা TTL<br>
                    🏠 উদাহরণ: দুধ — তারিখ আছে, পরে নষ্ট হয়!
                </div>
            </div>
            <div class="concept-card purple">
                <div class="card-icon">🔄</div>
                <div class="card-title">Eviction Policy</div>
                <div class="card-desc">
                    <strong>allkeys-lru</strong> → পুরানো ডাটা মুছো ✅<br>
                    <strong>volatile-lru</strong> → TTL যুক্ত পুরানো মুছো<br>
                    <strong>allkeys-lfu</strong> → কম ব্যবহৃত মুছো<br>
                    <strong>noeviction</strong> → Error দেয়<br>
                    🏠 টেবিলে জায়গা নেই → পুরানো জিনিস সরাও
                </div>
            </div>
        </div>
    </div>

    <!-- Atomic Operations -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔒 Atomic Operations & Transactions</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>🔒 Atomic Commands</h4>
            <ul>
                <li>INCR/DECR → 1 করে বাড়ায়/কমায় (thread-safe!)</li>
                <li>GETSET → পড়ো এবং নতুন রাখো একসাথে</li>
                <li>SETNX → শুধু নতুন হলে set করো</li>
                <li>HSETNX → Hash field শুধু নতুন হলে</li>
                <li>🏠 উদাহরণ: ATM → ব্যালেন্স চেক + কাটা = একসাথে</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>📋 MULTI/EXEC (Transaction)</h4>
            <ul>
                <li>MULTI → Transaction শুরু</li>
                <li>...commands queue হয়...</li>
                <li>EXEC → সব একসাথে execute</li>
                <li>DISCARD → বাতিল করো</li>
                <li>WATCH key → Optimistic Lock</li>
                <li>🏠 উদাহরণ: ব্যাংক transfer — ২টা account একসাথে</li>
            </ul>
        </div>
    </div>

    <div class="code-block">
        <div class="code-block-header">
            <div class="code-dots"><div class="code-dot dot-red"></div><div class="code-dot dot-yellow"></div><div class="code-dot dot-green"></div></div>
            <div class="code-filename">📁 redis/transaction.js</div>
        </div>
        <pre>
// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
// Redis Transaction — MULTI/EXEC
// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

const redis = require('ioredis');
const client = new redis();

// ✅ Atomic Transfer: A → B তে ৫০০ টাকা
async function transfer(fromUser, toUser, amount) {
    
    // WATCH — কেউ বদলালে transaction fail হবে
    await client.watch(`balance:${fromUser}`);
    
    const balance = await client.get(`balance:${fromUser}`);
    
    if (parseInt(balance) < amount) {
        await client.unwatch();
        throw new Error('ব্যালেন্স কম!');
    }
    
    // MULTI → Transaction শুরু
    const pipeline = client.multi();
    
    pipeline.decrby(`balance:${fromUser}`, amount);  // A থেকে কমাও
    pipeline.incrby(`balance:${toUser}`, amount);    // B তে বাড়াও
    pipeline.lpush('transfer:log', 
        JSON.stringify({ from: fromUser, to: toUser, amount, time: Date.now() })
    );
    
    // EXEC → সব একসাথে execute
    const results = await pipeline.exec();
    
    if (!results) {
        throw new Error('Transaction ব্যর্থ — আবার চেষ্টা করো');
    }
    
    return { success: true, results };
}

// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
// Cache-Aside Pattern
// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

async function getUserWithCache(userId) {
    const cacheKey = `user:${userId}`;
    
    // ১. Cache চেক
    const cached = await client.get(cacheKey);
    if (cached) {
        console.log('⚡ Cache HIT!');
        return JSON.parse(cached);
    }
    
    // ২. DB থেকে আনো
    console.log('🐌 Cache MISS → DB');
    const user = await db.query('SELECT * FROM users WHERE id = $1', [userId]);
    
    // ৩. Cache এ রাখো (১ ঘণ্টা)
    await client.setex(cacheKey, 3600, JSON.stringify(user));
    
    return user;
}
        </pre>
    </div>

    <!-- Streams Hands On -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🌊 Streams Hands On</h3>
    <div class="flow-container">
        <div class="flow-title">Redis Streams — Event Sourcing</div>
        <div class="flow-row">
            <div class="flow-box"><div class="fb-icon">📝</div><div class="fb-label">Producer</div><div class="fb-sub">XADD orders</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">🌊</div><div class="fb-label">Stream</div><div class="fb-sub">orders (log)</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">👥</div><div class="fb-label">Consumer Group</div><div class="fb-sub">XREADGROUP</div></div>
            <div class="flow-arrow">→</div>
            <div class="flow-box"><div class="fb-icon">✅</div><div class="fb-label">Acknowledge</div><div class="fb-sub">XACK</div></div>
        </div>
        <div style="margin-top:16px;font-size:13px;color:#666;text-align:center;">Kafka এর মতো কিন্তু Redis এ! At-least-once delivery। Consumer Group = parallel processing।</div>
    </div>

    <!-- Persistence -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">💾 Persistence — ডাটা টিকিয়ে রাখা</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>📸 RDB (Snapshot)</h4>
            <ul>
                <li>নির্দিষ্ট সময়ে পুরো ডাটার ছবি তোলে</li>
                <li>সংক্ষিপ্ত ফাইল, দ্রুত restart</li>
                <li>কিছু ডাটা হারাতে পারে (শেষ snapshot পরে)</li>
                <li>SAVE / BGSAVE কমান্ড</li>
                <li>🏠 ফটো তোলার মতো — মুহূর্তের স্মৃতি</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>📝 AOF (Append Only File)</h4>
            <ul>
                <li>প্রতিটা write command log করে</li>
                <li>বেশি নিরাপদ, ডাটা হারায় না</li>
                <li>ফাইল বড় হয়, ধীরে restart</li>
                <li>appendfsync: always/everysec/no</li>
                <li>🏠 ডায়েরি লেখা — প্রতিটা ঘটনা লিখে রাখো</li>
            </ul>
        </div>
    </div>
    <div class="info-box tip">
        <div class="info-icon">💡</div>
        <div class="info-content"><div class="info-title">Production এ সেরা: RDB + AOF দুটোই ব্যবহার করো!</div><p>RDB = দ্রুত backup ও restore। AOF = কোনো ডাটা হারাবে না। দুটো একসাথে = সর্বোচ্চ নিরাপত্তা।</p></div>
    </div>

    <!-- Replication -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔄 Master-Slave Replication & Failover</h3>
    <div class="arch-diagram">
        <div class="arch-title">Redis Replication + Sentinel (Failover)</div>
        <div style="display:flex;gap:20px;justify-content:center;align-items:flex-start;flex-wrap:wrap;">
            <div style="text-align:center;">
                <div style="background:#1a2a3a;border:2px solid #00d4ff;border-radius:12px;padding:20px;">
                    <div style="font-size:24px;">⚡</div>
                    <div style="font-size:14px;font-weight:700;color:#00d4ff;">MASTER</div>
                    <div style="font-size:11px;color:#555;">Read + Write</div>
                    <div style="font-size:11px;color:#555;">Port: 6379</div>
                </div>
            </div>
            <div style="display:flex;flex-direction:column;align-items:center;justify-content:center;gap:15px;padding-top:40px;">
                <div style="font-size:12px;color:#00d4ff;">── Async Replication ──></div>
                <div style="font-size:12px;color:#00d4ff;">── Async Replication ──></div>
            </div>
            <div style="display:flex;flex-direction:column;gap:12px;">
                <div style="background:#1a3a1a;border:2px solid #00ff88;border-radius:10px;padding:14px;text-align:center;">
                    <div style="font-size:16px;">⚡</div>
                    <div style="font-size:12px;font-weight:700;color:#00ff88;">REPLICA 1</div>
                    <div style="font-size:10px;color:#555;">Read Only | Port: 6380</div>
                </div>
                <div style="background:#1a3a1a;border:2px solid #00ff88;border-radius:10px;padding:14px;text-align:center;">
                    <div style="font-size:16px;">⚡</div>
                    <div style="font-size:12px;font-weight:700;color:#00ff88;">REPLICA 2</div>
                    <div style="font-size:10px;color:#555;">Read Only | Port: 6381</div>
                </div>
            </div>
        </div>
        <div style="margin-top:24px;padding:16px;background:#141414;border-radius:10px;font-size:13px;color:#aaa;text-align:left;max-width:600px;margin-left:auto;margin-right:auto;">
            <div style="color:#ffd700;font-weight:700;margin-bottom:8px;">🛡️ Redis Sentinel (Failover):</div>
            <div>• Master down → Sentinel detect করে (~30s)</div>
            <div>• Sentinel vote করে নতুন Master নির্বাচন করে</div>
            <div>• Replica → Master promote হয়</div>
            <div>• App কে নতুন Master এর address জানায়</div>
            <div style="margin-top:8px;">• Min 3 Sentinel = Quorum (বেশিরভাগ মত)</div>
        </div>
    </div>

    <!-- Sharding -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔀 Partitioning & Sharding</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">✂️</div>
            <div class="card-title">Sharding কী?</div>
            <div class="card-desc">ডাটা ভাগ করে অনেক Node এ রাখা। ১টা Node = 32GB RAM সীমা। ৮টা Node = ২৫৬GB! Horizontal Scaling।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🔑</div>
            <div class="card-title">Key-based Sharding</div>
            <div class="card-desc">key এর hash → কোন node? CRC16(key) % 16384 = slot। Redis Cluster = 16384 slots। প্রতিটা Node কিছু slot নেয়।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">⭕</div>
            <div class="card-title">Consistent Hashing</div>
            <div class="card-desc">Node যোগ/বাদ দিলে কম ডাটা move হয়। Hash Ring এ সবাই। নতুন Node আসলে শুধু পাশের Node এর কিছু ডাটা নেয়।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🌐</div>
            <div class="card-title">Redis Cluster</div>
            <div class="card-desc">Auto Sharding + Replication। কমপক্ষে ৩টা Master। প্রতিটা Master এর Replica। Cluster gossip protocol।</div>
        </div>
    </div>

    <!-- Consistent Hashing Visual -->
    <div class="flow-container">
        <div class="flow-title">⭕ Consistent Hashing Ring</div>
        <div style="text-align:center;margin:20px 0;">
            <div style="position:relative;width:240px;height:240px;margin:0 auto;">
                <svg viewBox="0 0 240 240" style="width:240px;height:240px;">
                    <circle cx="120" cy="120" r="100" fill="none" stroke="#00d4ff33" stroke-width="2"/>
                    <!-- Nodes -->
                    <circle cx="220" cy="120" r="16" fill="#1a2a3a" stroke="#00d4ff" stroke-width="2"/>
                    <text x="220" y="125" fill="#00d4ff" font-size="10" text-anchor="middle">N1</text>
                    <circle cx="45" cy="45" r="16" fill="#1a3a1a" stroke="#00ff88" stroke-width="2"/>
                    <text x="45" y="50" fill="#00ff88" font-size="10" text-anchor="middle">N2</text>
                    <circle cx="45" cy="195" r="16" fill="#3a1a1a" stroke="#ff8c00" stroke-width="2"/>
                    <text x="45" y="200" fill="#ff8c00" font-size="10" text-anchor="middle">N3</text>
                    <circle cx="195" cy="45" r="14" fill="#2a1a2a" stroke="#b44fff" stroke-width="2"/>
                    <text x="195" y="50" fill="#b44fff" font-size="10" text-anchor="middle">N4</text>
                    <!-- Keys -->
                    <circle cx="160" cy="30" r="6" fill="#ffd700"/>
                    <text x="172" y="34" fill="#ffd700" font-size="9">K1</text>
                    <circle cx="30" cy="110" r="6" fill="#ffd700"/>
                    <text x="10" y="114" fill="#ffd700" font-size="9">K2</text>
                    <circle cx="120" cy="218" r="6" fill="#ffd700"/>
                    <text x="130" y="222" fill="#ffd700" font-size="9">K3</text>
                </svg>
            </div>
            <div style="font-size:12px;color:#666;margin-top:10px;">Key → Hash → Ring এ position → Clockwise পরের Node</div>
        </div>
        <div style="display:flex;gap:20px;justify-content:center;flex-wrap:wrap;margin-top:10px;">
            <div style="background:#141414;border-radius:8px;padding:10px 16px;font-size:12px;color:#aaa;">
                <span style="color:#00d4ff;">✅ Node যোগ করলে:</span> শুধু পাশের Node এর কিছু Key move হয়
            </div>
            <div style="background:#141414;border-radius:8px;padding:10px 16px;font-size:12px;color:#aaa;">
                <span style="color:#ff8c00;">⚠️ Node বাদ দিলে:</span> সেই Node এর Key পরের Node নেয়
            </div>
        </div>
    </div>

    <!-- GUI Tools -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🖥️ Redis GUI Tools</h3>
    <table class="comparison-table">
        <tr><th>Tool</th><th>ধরন</th><th>বৈশিষ্ট্য</th><th>সেরা জন্য</th></tr>
        <tr><td>🖥️ RedisInsight</td><td>Desktop App (Official)</td><td>Data browser, Profiler, Slow log, Streams viewer</td><td>সব কাজের জন্য ✅</td></tr>
        <tr><td>🌐 Redis Commander</td><td>Web UI</td><td>Docker এ সহজ, CRUD operations</td><td>Development</td></tr>
        <tr><td>📱 Another Redis Desktop</td><td>Desktop App</td><td>Multiple connections, Cluster support</td><td>Production management</td></tr>
        <tr><td>🔧 redis-cli</td><td>Terminal</td><td>সব কমান্ড, scripting</td><td>Advanced users</td></tr>
    </table>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 10: RabbitMQ
══════════════════════════════════════ -->
<div class="full-section" id="module10">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 10</div>
        <h2 class="module-title">🐰 RabbitMQ As Service Bus</h2>
        <p class="module-subtitle">Message Broker — Publisher থেকে Consumer পর্যন্ত</p>
    </div>

    <!-- What is RabbitMQ -->
    <h3 class="subsection-title">🐰 RabbitMQ কী এবং কেন দরকার?</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">📬</div>
            <div class="card-title">RabbitMQ কী?</div>
            <div class="card-desc">Message Broker। Service এর মধ্যে Message পাঠায়। AMQP Protocol ব্যবহার করে। ডাকঘরের মতো — চিঠি নেয়, সঠিক জায়গায় পাঠায়।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🔌</div>
            <div class="card-title">কেন দরকার?</div>
            <div class="card-desc">Decoupling: Service আলাদা। Async: Response এর জন্য অপেক্ষা নেই। Load Leveling: Queue এ জমা রাখো। Retry: ব্যর্থ হলে আবার চেষ্টা।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🆚</div>
            <div class="card-title">RabbitMQ vs Kafka</div>
            <div class="card-desc">RabbitMQ = Smart Broker (routing logic এ)। Kafka = Smart Consumer (partition এ)। RabbitMQ = Task Queue। Kafka = Event Streaming।</div>
        </div>
    </div>

    <!-- Components -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔧 RabbitMQ Components</h3>
    <div class="arch-diagram">
        <div class="arch-title">RabbitMQ Architecture</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">📝</div><div class="node-label">Publisher</div><div class="node-sub">Message পাঠায়</div></div>
        </div>
        <div class="arch-arrow-down">↓ Message + Routing Key</div>
        <div class="arch-layer green">
            <div class="arch-node"><div class="node-icon">🔀</div><div class="node-label">Exchange</div><div class="node-sub">Routing Logic</div></div>
        </div>
        <div class="arch-arrow-down">↓ Binding Rules অনুযায়ী</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">📦</div><div class="node-label">Queue 1</div><div class="node-sub">Message Store</div></div>
            <div class="arch-node"><div class="node-icon">📦</div><div class="node-label">Queue 2</div><div class="node-sub">Message Store</div></div>
            <div class="arch-node"><div class="node-icon">📦</div><div class="node-label">Queue 3</div><div class="node-sub">Message Store</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">📖</div><div class="node-label">Consumer 1</div><div class="node-sub">Message নেয়</div></div>
            <div class="arch-node"><div class="node-icon">📖</div><div class="node-label">Consumer 2</div><div class="node-sub">Message নেয়</div></div>
        </div>
    </div>

    <!-- Exchange Types -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔀 Exchange Types — ৫ ধরনের Routing</h3>

    <div class="exchange-diagram">
        <div class="exchange-title">Exchange Types তুলনা</div>

        <!-- Direct Exchange -->
        <div style="background:#141414;border:1px solid #222;border-radius:14px;padding:20px;margin-bottom:16px;">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
                <div style="font-size:24px;">🎯</div>
                <div>
                    <div style="font-size:15px;font-weight:800;color:#00d4ff;">Direct Exchange</div>
                    <div style="font-size:12px;color:#555;">Exact Routing Key match</div>
                </div>
            </div>
            <div class="exchange-visual">
                <div class="producer-box"><div style="font-size:13px;font-weight:700;color:#00d4ff;">Publisher</div><div style="font-size:11px;color:#555;">key: "order"</div></div>
                <div style="font-size:20px;color:#00d4ff;">→</div>
                <div class="exchange-box"><div class="ex-icon">🎯</div><div class="ex-name">Direct</div><div class="ex-rule">key === binding</div></div>
                <div style="font-size:20px;color:#00d4ff;">→</div>
                <div class="queue-box">Queue: orders ✅</div>
                <div style="font-size:20px;color:#555;">✗</div>
                <div class="queue-box" style="border-color:#55555544;color:#555;">Queue: logs ❌</div>
            </div>
            <div style="font-size:12px;color:#666;margin-top:10px;">🏠 উদাহরণ: নামের সাথে হুবহু মিললে পাঠাও। Order Service → orders queue সরাসরি।</div>
        </div>

        <!-- Default Exchange -->
        <div style="background:#141414;border:1px solid #222;border-radius:14px;padding:20px;margin-bottom:16px;">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
                <div style="font-size:24px;">📭</div>
                <div>
                    <div style="font-size:15px;font-weight:800;color:#00ff88;">Default Exchange</div>
                    <div style="font-size:12px;color:#555;">Queue নামেই পাঠাও (সরাসরি)</div>
                </div>
            </div>
            <div style="font-size:12px;color:#888;padding:10px;background:#0f0f0f;border-radius:8px;">Routing Key = Queue এর নাম। কোনো Exchange declare করতে হয় না। সহজ use case এর জন্য।</div>
        </div>

        <!-- Fanout Exchange -->
        <div style="background:#141414;border:1px solid #222;border-radius:14px;padding:20px;margin-bottom:16px;">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
                <div style="font-size:24px;">📢</div>
                <div>
                    <div style="font-size:15px;font-weight:800;color:#b44fff;">Fanout Exchange</div>
                    <div style="font-size:12px;color:#555;">সব Queue তে ছড়িয়ে দাও</div>
                </div>
            </div>
            <div class="exchange-visual">
                <div class="producer-box"><div style="font-size:13px;font-weight:700;color:#00d4ff;">Publisher</div><div style="font-size:11px;color:#555;">Any message</div></div>
                <div style="font-size:20px;color:#00d4ff;">→</div>
                <div class="exchange-box" style="background:linear-gradient(135deg,#2a1a2a,#3a1a3a);border-color:#b44fff44;"><div class="ex-icon">📢</div><div class="ex-name" style="color:#b44fff;">Fanout</div><div class="ex-rule">সবাইকে!</div></div>
                <div style="font-size:14px;color:#b44fff;">→ সব Queue →</div>
                <div style="display:flex;flex-direction:column;gap:6px;">
                    <div class="queue-box" style="border-color:#b44fff44;color:#b44fff;">Email ✅</div>
                    <div class="queue-box" style="border-color:#b44fff44;color:#b44fff;">SMS ✅</div>
                    <div class="queue-box" style="border-color:#b44fff44;color:#b44fff;">Push ✅</div>
                </div>
            </div>
            <div style="font-size:12px;color:#666;margin-top:10px;">🏠 উদাহরণ: রেডিও ব্রডকাস্ট। একটা পাঠাও → সবাই পায়। নতুন অর্ডার → Email + SMS + Push notification।</div>
        </div>

        <!-- Topic Exchange -->
        <div style="background:#141414;border:1px solid #222;border-radius:14px;padding:20px;margin-bottom:16px;">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
                <div style="font-size:24px;">🏷️</div>
                <div>
                    <div style="font-size:15px;font-weight:800;color:#ff8c00;">Topic Exchange</div>
                    <div style="font-size:12px;color:#555;">Pattern matching দিয়ে Route</div>
                </div>
            </div>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:16px;">
                <div style="background:#0f0f0f;border-radius:8px;padding:12px;font-size:12px;font-family:monospace;color:#aaa;">
                    <div style="color:#ff8c00;margin-bottom:8px;">Routing Keys:</div>
                    order.created → Email Queue ✅<br>
                    order.shipped → SMS Queue ✅<br>
                    order.#       → All Order Q ✅<br>
                    *.created     → All Created Q ✅
                </div>
                <div style="background:#0f0f0f;border-radius:8px;padding:12px;font-size:12px;color:#aaa;">
                    <div style="color:#ff8c00;margin-bottom:8px;">Wildcards:</div>
                    * = ঠিক একটা শব্দ<br>
                    # = শূন্য বা আরো শব্দ<br><br>
                    🏠 উদাহরণ: news.sports.cricket<br>
                    news.# → সব news পাবে
                </div>
            </div>
        </div>

        <!-- Header Exchange -->
        <div style="background:#141414;border:1px solid #222;border-radius:14px;padding:20px;">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px;">
                <div style="font-size:24px;">📋</div>
                <div>
                    <div style="font-size:15px;font-weight:800;color:#ffd700;">Header Exchange</div>
                    <div style="font-size:12px;color:#555;">Message Header দিয়ে Route</div>
                </div>
            </div>
            <div style="background:#0f0f0f;border-radius:8px;padding:12px;font-size:12px;color:#aaa;">
                Routing Key এর পরিবর্তে Message Header ব্যবহার করে। <br>
                x-match: all → সব header মিলতে হবে। x-match: any → যেকোনো একটা মিললেই হবে।<br>
                🏠 উদাহরণ: { type: "order", priority: "high" } → Priority Queue তে যাবে।
            </div>
        </div>
    </div>

    <!-- Payload -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📦 RabbitMQ Payload</h3>
    <div class="code-block">
        <div class="code-block-header">
            <div class="code-dots"><div class="code-dot dot-red"></div><div class="code-dot dot-yellow"></div><div class="code-dot dot-green"></div></div>
            <div class="code-filename">📁 rabbitmq/publisher.js</div>
        </div>
        <pre>
const amqp = require('amqplib');

async function publishOrder(orderData) {
    const conn = await amqp.connect('amqp://localhost');
    const channel = await conn.createChannel();
    
    // Exchange declare করো
    await channel.assertExchange('orders', 'topic', { durable: true });
    
    // Message Payload
    const payload = {
        orderId: orderData.id,
        userId: orderData.userId,
        amount: orderData.amount,
        items: orderData.items,
        timestamp: new Date().toISOString()
    };
    
    // Routing Key: order.created
    channel.publish(
        'orders',                    // Exchange
        'order.created',             // Routing Key
        Buffer.from(JSON.stringify(payload)),
        {
            persistent: true,        // Disk এ রাখো (Crash safe)
            contentType: 'application/json',
            headers: {
                'priority': 'high',
                'source': 'order-service'
            }
        }
    );
    
    console.log('✅ Order published:', orderData.id);
    await conn.close();
}

// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
// Consumer
async function consumeOrders() {
    const conn = await amqp.connect('amqp://localhost');
    const channel = await conn.createChannel();
    
    await channel.assertQueue('email-notifications', { durable: true });
    await channel.bindQueue('email-notifications', 'orders', 'order.*');
    
    // একবারে ১টা (Fair dispatch)
    channel.prefetch(1);
    
    channel.consume('email-notifications', async (msg) => {
        const order = JSON.parse(msg.content.toString());
        
        try {
            await sendEmail(order.userId, order.orderId);
            channel.ack(msg);  // ✅ সফল
        } catch (error) {
            channel.nack(msg, false, true);  // ❌ আবার queue তে
        }
    });
}
        </pre>
    </div>

    <!-- Multi Cluster & Management -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🌐 Multi-cluster & Kubernetes</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🌐</div>
            <div class="card-title">Multi-cluster RabbitMQ</div>
            <div class="card-desc">Federation Plugin: আলাদা Cluster এ Message forward করো। Shovel Plugin: Queue থেকে Queue তে move করো। Geographic distribution।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">📊</div>
            <div class="card-title">Management UI</div>
            <div class="card-desc">http://localhost:15672। Queue monitor করো। Exchange দেখো। Message rate, connection count। Dead Letter Queue পরীক্ষা করো।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">☸️</div>
            <div class="card-title">Kubernetes Deploy</div>
            <div class="card-desc">RabbitMQ Cluster Operator। StatefulSet দিয়ে Deploy। Persistent Volume। Auto-healing। Production-ready।</div>
        </div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 11: SOCKET
══════════════════════════════════════ -->
<div class="full-section" id="module11">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 11</div>
        <h2 class="module-title">🔌 Socket</h2>
        <p class="module-subtitle">Real-time Communication — Chat App থেকে Scaling</p>
    </div>

    <!-- What is Socket -->
    <h3 class="subsection-title">🔌 Socket কী এবং কেন দরকার?</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>❌ HTTP (পুরানো পদ্ধতি)</h4>
            <ul>
                <li>Client সবসময় request করে</li>
                <li>Server শুধু response দেয়</li>
                <li>প্রতিটা request নতুন connection</li>
                <li>Real-time এ Polling লাগে (ব্যয়বহুল)</li>
                <li>🏠 চিঠি পাঠানো — একমুখী</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>✅ WebSocket (আধুনিক)</h4>
            <ul>
                <li>একটা Connection, দুইমুখী</li>
                <li>Server যেকোনো সময় push করে</li>
                <li>কম overhead</li>
                <li>Real-time: Chat, Game, Stock</li>
                <li>🏠 ফোন কল — দুইমুখী, সবসময় খোলা</li>
            </ul>
        </div>
    </div>

    <!-- Socket Architecture -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ Socket.io Architecture</h3>
    <div class="arch-diagram">
        <div class="arch-title">Socket.io Components</div>
        <div style="display:flex;gap:30px;justify-content:center;align-items:center;flex-wrap:wrap;">
            <div style="text-align:center;">
                <div style="background:#1a1a2e;border:2px solid #00d4ff;border-radius:14px;padding:20px;min-width:150px;">
                    <div style="font-size:28px;">🖥️</div>
                    <div style="font-size:14px;font-weight:700;color:#00d4ff;margin:8px 0;">Client</div>
                    <div style="font-size:11px;color:#555;">socket.emit('msg', data)</div>
                    <div style="font-size:11px;color:#555;">socket.on('reply', fn)</div>
                </div>
            </div>
            <div style="text-align:center;">
                <div style="font-size:12px;color:#00d4ff;">WebSocket Connection</div>
                <div style="font-size:24px;color:#00d4ff;">⇄</div>
                <div style="font-size:11px;color:#555;">ws://server:3000</div>
            </div>
            <div style="text-align:center;">
                <div style="background:#1a2e1a;border:2px solid #00ff88;border-radius:14px;padding:20px;min-width:150px;">
                    <div style="font-size:28px;">🖥️</div>
                    <div style="font-size:14px;font-weight:700;color:#00ff88;margin:8px 0;">Server</div>
                    <div style="font-size:11px;color:#555;">io.emit('msg', data)</div>
                    <div style="font-size:11px;color:#555;">socket.on('msg', fn)</div>
                </div>
            </div>
        </div>
        <div style="margin-top:24px;display:flex;gap:16px;justify-content:center;flex-wrap:wrap;">
            <div style="background:#141414;border:1px solid #222;border-radius:10px;padding:12px 20px;text-align:center;">
                <div style="font-size:16px;">🏠</div>
                <div style="font-size:12px;font-weight:700;color:#00d4ff;margin-top:4px;">Namespace</div>
                <div style="font-size:11px;color:#555;">/chat, /game</div>
            </div>
            <div style="background:#141414;border:1px solid #222;border-radius:10px;padding:12px 20px;text-align:center;">
                <div style="font-size:16px;">🚪</div>
                <div style="font-size:12px;font-weight:700;color:#00ff88;margin-top:4px;">Room</div>
                <div style="font-size:11px;color:#555;">room-123</div>
            </div>
            <div style="background:#141414;border:1px solid #222;border-radius:10px;padding:12px 20px;text-align:center;">
                <div style="font-size:16px;">📢</div>
                <div style="font-size:12px;font-weight:700;color:#b44fff;margin-top:4px;">Broadcast</div>
                <div style="font-size:11px;color:#555;">সবাইকে পাঠাও</div>
            </div>
            <div style="background:#141414;border:1px solid #222;border-radius:10px;padding:12px 20px;text-align:center;">
                <div style="font-size:16px;">✅</div>
                <div style="font-size:12px;font-weight:700;color:#ff8c00;margin-top:4px;">ACK</div>
                <div style="font-size:11px;color:#555;">পেয়েছি নিশ্চিত</div>
            </div>
        </div>
    </div>

    <!-- Rooms & Namespaces -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏠 Rooms & Namespaces</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🏢</div>
            <div class="card-title">Namespace</div>
            <div class="card-desc">একটা Server এ একাধিক App এর মতো। /chat, /game, /notification। আলাদা event space। io.of('/chat') দিয়ে তৈরি।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🚪</div>
            <div class="card-title">Room</div>
            <div class="card-desc">Namespace এর ভেতরে Group। socket.join('room-123')। শুধু সেই Room এ পাঠাও। Chat group, Game lobby।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📢</div>
            <div class="card-title">Broadcasting</div>
            <div class="card-desc">io.emit = সবাইকে। socket.broadcast.emit = নিজে ছাড়া সবাই। io.to('room').emit = শুধু সেই Room এ।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">✅</div>
            <div class="card-title">Acknowledgement</div>
            <div class="card-desc">Message পেয়েছে কিনা confirm। socket.emit('msg', data, callback)। Callback দিয়ে confirm নাও।</div>
        </div>
    </div>

    <!-- Chat App Code -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">💬 Chat App — Basic Implementation</h3>
    <div class="code-block">
        <div class="code-block-header">
            <div class="code-dots"><div class="code-dot dot-red"></div><div class="code-dot dot-yellow"></div><div class="code-dot dot-green"></div></div>
            <div class="code-filename">📁 socket/chatServer.js</div>
        </div>
        <pre>
const express = require('express');
const { createServer } = require('http');
const { Server } = require('socket.io');
const redis = require('ioredis');

const app = express();
const httpServer = createServer(app);
const io = new Server(httpServer, {
    cors: { origin: "*" }
});

// Redis Adapter (Multiple Server Scaling এর জন্য!)
const { createAdapter } = require('@socket.io/redis-adapter');
const pubClient = new redis({ host: 'localhost', port: 6379 });
const subClient = pubClient.duplicate();
io.adapter(createAdapter(pubClient, subClient));

// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
// Chat Namespace
// ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
const chatNS = io.of('/chat');

chatNS.on('connection', (socket) => {
    console.log(`✅ User connected: ${socket.id}`);
    
    // Room এ যোগ দাও
    socket.on('join-room', ({ roomId, username }) => {
        socket.join(roomId);
        socket.data.username = username;
        socket.data.room = roomId;
        
        // Room এর সবাইকে জানাও
        socket.to(roomId).emit('user-joined', {
            username,
            message: `${username} Chat এ যোগ দিয়েছে!`,
            timestamp: new Date()
        });
        
        console.log(`${username} joined room: ${roomId}`);
    });
    
    // Message পাঠাও
    socket.on('send-message', ({ roomId, message }, callback) => {
        const msgData = {
            id: Date.now(),
            sender: socket.data.username,
            message,
            timestamp: new Date()
        };
        
        // Room এর সবাইকে পাঠাও (নিজেও পাবে)
        chatNS.to(roomId).emit('receive-message', msgData);
        
        // Redis এ সেভ করো (History)
        pubClient.lpush(
            `chat:${roomId}:history`,
            JSON.stringify(msgData)
        );
        pubClient.ltrim(`chat:${roomId}:history`, 0, 99); // শেষ ১০০টা
        
        // Acknowledgement পাঠাও
        callback({ status: 'delivered', id: msgData.id });
    });
    
    // Typing indicator
    socket.on('typing', ({ roomId, isTyping }) => {
        socket.to(roomId).emit('user-typing', {
            username: socket.data.username,
            isTyping
        });
    });
    
    // Disconnect
    socket.on('disconnect', () => {
        const { username, room } = socket.data;
        if (username && room) {
            socket.to(room).emit('user-left', {
                username,
                message: `${username} চলে গেছে`
            });
        }
        console.log(`❌ User disconnected: ${socket.id}`);
    });
});

httpServer.listen(3000, () => console.log('🔌 Socket Server: http://localhost:3000'));
        </pre>
    </div>

    <!-- Chat System Design -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ Chat Application System Design</h3>
    <div class="arch-diagram">
        <div class="arch-title">💬 Scalable Chat System Design</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">📱</div><div class="node-label">Client Apps</div><div class="node-sub">iOS, Android, Web</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">⚖️</div><div class="node-label">Load Balancer</div><div class="node-sub">Sticky Session (ip_hash)</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer green">
            <div class="arch-node"><div class="node-icon">🔌</div><div class="node-label">Socket Server 1</div><div class="node-sub">Node.js + Socket.io</div></div>
            <div class="arch-node"><div class="node-icon">🔌</div><div class="node-label">Socket Server 2</div><div class="node-sub">Node.js + Socket.io</div></div>
            <div class="arch-node"><div class="node-icon">🔌</div><div class="node-label">Socket Server 3</div><div class="node-sub">Node.js + Socket.io</div></div>
        </div>
        <div class="arch-arrow-down">↓ Redis Pub/Sub (Server sync)</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">⚡</div><div class="node-label">Redis</div><div class="node-sub">Pub/Sub + Session + Cache</div></div>
            <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">PostgreSQL</div><div class="node-sub">Messages + Users</div></div>
            <div class="arch-node"><div class="node-icon">📦</div><div class="node-label">S3</div><div class="node-sub">Files, Images</div></div>
        </div>
    </div>

    <!-- Scaling -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Socket Application Scaling</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">⚡</div>
            <div class="card-title">Redis Adapter</div>
            <div class="card-desc">Multiple Server sync। Server 1 এ event → Redis Pub → Server 2 Sub → সেই Server এর Client পায়! @socket.io/redis-adapter।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🔒</div>
            <div class="card-title">Sticky Session</div>
            <div class="card-desc">একই Client সবসময় একই Server এ। Nginx ip_hash। WebSocket connection maintain থাকে। Long polling fallback।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📊</div>
            <div class="card-title">Horizontal Scaling</div>
            <div class="card-desc">আরো Server যোগ করো। Redis Adapter সব sync রাখে। Load Balancer traffic ভাগ করে। কোটি connection সামলানো সম্ভব!</div>
        </div>
    </div>

    <div class="info-box tip">
        <div class="info-icon">💡</div>
        <div class="info-content"><div class="info-title">Socket Scaling Secret</div><p>একটা Node.js Server = ~65,000 WebSocket connections। ১০ টা Server + Redis Adapter = ৬,৫০,০০০ connections! Redis Pub/Sub সব server sync রাখে।</p></div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     MODULE 12: URL SHORTENER
══════════════════════════════════════ -->
<div class="full-section" id="module12">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">MODULE 12</div>
        <h2 class="module-title">🔗 URL Shortener Service</h2>
        <p class="module-subtitle">System Design থেকে Production Deploy পর্যন্ত</p>
    </div>

    <!-- Theory -->
    <h3 class="subsection-title">📐 Theory: URL Shortener Design</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🔗</div>
            <div class="card-title">URL Shortener কী?</div>
            <div class="card-desc">দীর্ঘ URL → ছোট URL। bit.ly, tinyurl.com এর মতো। https://example.com/very-long-path → https://sht.ly/abc123।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">📊</div>
            <div class="card-title">Scale Estimation</div>
            <div class="card-desc">১০০M URLs/দিন। Read:Write = ১০:১। ১০ বছর স্টোরেজ = 365B URLs। প্রতি URL ~500bytes → ~180TB Storage!</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🔑</div>
            <div class="card-title">Short Key কীভাবে?</div>
            <div class="card-desc">Base62 encoding: a-z, A-Z, 0-9 = 62 chars। ৬ chars = 62^6 = ৫৬ বিলিয়ন unique URLs! MD5/SHA256 hash → প্রথম ৬ chars।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">⚡</div>
            <div class="card-title">Cache Strategy</div>
            <div class="card-desc">80% request = 20% URL (Pareto Principle)। Top URLs Redis এ Cache। Hit Rate > 80%। DB চাপ কমে নাটকীয়ভাবে।</div>
        </div>
    </div>

    <!-- System Design -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ সম্পূর্ণ System Design</h3>
    <div class="url-flow">
        <div style="text-align:center;font-size:18px;font-weight:800;color:#00d4ff;margin-bottom:30px;">URL Shortener Architecture</div>

        <div style="display:flex;gap:30px;justify-content:space-around;flex-wrap:wrap;">
            <!-- Create Flow -->
            <div style="flex:1;min-width:280px;">
                <div style="font-size:14px;font-weight:700;color:#00ff88;margin-bottom:16px;text-align:center;">✍️ URL তৈরির Flow</div>
                <div class="steps-container">
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">1</div>
                        <div class="step-content"><h4>POST /api/shorten</h4><p>Long URL পাঠাও body তে</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">2</div>
                        <div class="step-content"><h4>MD5 Hash</h4><p>Long URL → hash → প্রথম ৬ char = short key</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">3</div>
                        <div class="step-content"><h4>Collision চেক</h4><p>DB তে আছে কিনা। থাকলে counter যোগ করো।</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">4</div>
                        <div class="step-content"><h4>Save করো</h4><p>PostgreSQL: short_key, long_url, created_at, clicks</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">5</div>
                        <div class="step-content"><h4>Return</h4><p>{ shortUrl: "https://sht.ly/abc123" }</p></div>
                    </div>
                </div>
            </div>

            <!-- Redirect Flow -->
            <div style="flex:1;min-width:280px;">
                <div style="font-size:14px;font-weight:700;color:#00d4ff;margin-bottom:16px;text-align:center;">🔀 Redirect Flow</div>
                <div class="steps-container">
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">1</div>
                        <div class="step-content"><h4>GET /:shortKey</h4><p>User short URL ক্লিক করে</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">2</div>
                        <div class="step-content"><h4>Redis Cache চেক</h4><p>Cache HIT → সাথে সাথে redirect (1ms)</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">3</div>
                        <div class="step-content"><h4>Cache MISS → DB</h4><p>PostgreSQL থেকে long_url পাও</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">4</div>
                        <div class="step-content"><h4>Cache Update</h4><p>Redis এ রাখো (TTL: 1 ঘণ্টা)</p></div>
                    </div>
                    <div class="step-item">
                        <div class="step-number" style="font-size:13px;">5</div>
                        <div class="step-content"><h4>301/302 Redirect</h4><p>Long URL এ redirect করো। Analytics count বাড়াও।</p></div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Full Architecture -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🌐 Production Architecture</h3>
    <div class="arch-diagram">
        <div class="arch-title">URL Shortener — Production Architecture</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">👤</div><div class="node-label">Users</div><div class="node-sub">Browser / App</div></div>
        </div>
        <div class="arch-arrow-down">↓ DNS → sht.ly</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">🌐</div><div class="node-label">CloudFront CDN</div><div class="node-sub">Static Files Cache</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer green">
            <div class="arch-node"><div class="node-icon">⚖️</div><div class="node-label">Nginx L7 LB</div><div class="node-sub">API + Redirect Routing</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">🟢</div><div class="node-label">URL Service 1</div><div class="node-sub">Node.js :3001</div></div>
            <div class="arch-node"><div class="node-icon">🟢</div><div class="node-label">URL Service 2</div><div class="node-sub">Node.js :3002</div></div>
            <div class="arch-node"><div class="node-icon">🟢</div><div class="node-label">URL Service 3</div><div class="node-sub">Node.js :3003</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer orange">
            <div class="arch-node"><div class="node-icon">⚡</div><div class="node-label">Redis Cache</div><div class="node-sub">Hot URLs (80% Hit Rate)</div></div>
            <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">PostgreSQL</div><div class="node-sub">All URLs + Analytics</div></div>
            <div class="arch-node"><div class="node-icon">📨</div><div class="node-label">Kafka</div><div class="node-sub">Click Analytics Stream</div></div>
        </div>
    </div>

    <!-- Nginx L7 Config -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🌐 Nginx Layer 7 Load Balancer Config</h3>
    <div class="code-block">
        <div class="code-block-header">
            <div class="code-dots"><div class="code-dot dot-red"></div><div class="code-dot dot-yellow"></div><div class="code-dot dot-green"></div></div>
            <div class="code-filename">📁 nginx/url-shortener.conf</div>
        </div>
        <pre>
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
# URL Shortener — Nginx Layer 7 Load Balancer
# ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

http {

    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    # Upstream Server Groups
    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    upstream url_services {
        least_conn;  # সবচেয়ে কম connection এ পাঠাও
        
        server url-service-1:3001 weight=3;
        server url-service-2:3002 weight=3;
        server url-service-3:3003 weight=3;
        
        keepalive 32;  # Connection reuse
    }

    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    # Rate Limiting
    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    limit_req_zone $binary_remote_addr 
                   zone=api_limit:10m 
                   rate=30r/m;  # ১ মিনিটে ৩০টা
    
    limit_req_zone $binary_remote_addr 
                   zone=redirect_limit:10m 
                   rate=100r/s;  # Redirect: প্রতি সেকেন্ডে ১০০

    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    # Main Server
    # ━━━━━━━━━━━━━━━━━━━━━━━━━━
    server {
        listen 80;
        server_name sht.ly;
        
        # ── Redirect HTTP → HTTPS
        return 301 https://$host$request_uri;
    }

    server {
        listen 443 ssl http2;
        server_name sht.ly;
        
        # SSL Certificates
        ssl_certificate     /etc/ssl/sht.ly.crt;
        ssl_certificate_key /etc/ssl/sht.ly.key;
        
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        # API Routes (URL তৈরি)
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        location /api/ {
            limit_req zone=api_limit burst=5 nodelay;
            limit_req_status 429;
            
            proxy_pass http://url_services;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
            
            proxy_connect_timeout 5s;
            proxy_read_timeout 10s;
        }
        
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        # Redirect Routes (short URL → long URL)
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        location ~* ^/([a-zA-Z0-9]{6,10})$ {
            limit_req zone=redirect_limit burst=20 nodelay;
            
            proxy_pass http://url_services;
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            
            # Cache redirect responses
            proxy_cache_valid 301 1h;
            proxy_cache_valid 404 1m;
        }
        
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        # Health Check
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        location /health {
            access_log off;
            return 200 '{"status":"ok"}';
            add_header Content-Type application/json;
        }
        
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        # Custom Error Pages
        # ━━━━━━━━━━━━━━━━━━━━━━━━━━
        error_page 429 @too_many;
        location @too_many {
            return 429 '{"error":"অনেক বেশি request! একটু পরে চেষ্টা করুন"}';
        }
        
        error_page 404 @not_found;
        location @not_found {
            return 404 '{"error":"URL পাওয়া যায়নি!"}';
        }
    }
}
        </pre>
    </div>

    <!-- URL Design Decisions -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🤔 Design Decisions</h3>
    <table class="comparison-table">
        <tr><th>সিদ্ধান্ত</th><th>Option A</th><th>Option B</th><th>আমরা বেছেছি</th></tr>
        <tr><td>Short Key Generation</td><td>Hash (MD5)</td><td>Auto-increment + Base62</td><td><span class="badge badge-green">Hash ✅</span> — Distributed safe</td></tr>
        <tr><td>Redirect Type</td><td>301 (Permanent)</td><td>302 (Temporary)</td><td><span class="badge badge-yellow">302</span> — Analytics সম্ভব</td></tr>
        <tr><td>Database</td><td>NoSQL (DynamoDB)</td><td>SQL (PostgreSQL)</td><td><span class="badge badge-green">SQL ✅</span> — Complex query</td></tr>
        <tr><td>Cache</td><td>In-memory</td><td>Redis</td><td><span class="badge badge-green">Redis ✅</span> — Distributed</td></tr>
        <tr><td>Key Length</td><td>5 chars</td><td>7 chars</td><td><span class="badge badge-blue">6 chars</span> — Balance</td></tr>
    </table>

    <div class="info-box tip">
        <div class="info-icon">🎓</div>
        <div class="info-content"><div class="info-title">Interview এ URL Shortener</div><p>এটা সবচেয়ে জনপ্রিয় System Design interview question! মনে রাখো: <strong>Estimation → API Design → DB Schema → Cache → Scaling → Edge Cases</strong> — এই ক্রমে উত্তর দাও।</p></div>
    </div>
</div>
</div>

<!-- ══════════════════════════════════════
     SUMMARY
══════════════════════════════════════ -->
<div class="full-section" id="summary" style="background:#080808;">
<div class="module-section">
    <div class="module-header">
        <div class="module-number-badge">সম্পূর্ণ সারসংক্ষেপ</div>
        <h2 class="module-title">🎯 Quick Reference Guide</h2>
        <p class="module-subtitle">সব ১২টা Module এক নজরে</p>
    </div>

    <h3 class="subsection-title">📋 সব Module এক টেবিলে</h3>
    <table class="comparison-table">
        <tr><th>Module</th><th>বিষয়</th><th>মূল ধারণা</th><th>মনে রাখার টিপস</th></tr>
        <tr><td>🏗️ M1</td><td>System Design</td><td>CAP, Consistency, Failure</td><td>CAP = ২টাই পাবে, ৩টা না</td></tr>
        <tr><td>🧮 M2</td><td>Mathematics</td><td>RPS, Latency, Nines</td><td>Peak = Average × 3</td></tr>
        <tr><td>🟢 M3</td><td>Node.js</td><td>Async, Express, PostgreSQL</td><td>Callback→Promise→Async/Await</td></tr>
        <tr><td>🚦 M4</td><td>Rate Limit</td><td>Sliding Window + Redis</td><td>Defense in Depth (স্তরে স্তরে)</td></tr>
        <tr><td>☁️ M6</td><td>AWS</td><td>VPC, EC2, RDS, Auto Scale</td><td>Public→Private→DB (নিরাপত্তার স্তর)</td></tr>
        <tr><td>🐳 M7</td><td>Docker</td><td>Dockerfile, Compose, MySQL Rep</td><td>Dockerfile→Image→Container</td></tr>
        <tr><td>🌐 M8</td><td>Networking</td><td>Namespace, veth, Bridge</td><td>Docker = NS + veth + Bridge + NAT</td></tr>
        <tr><td>⚡ M9</td><td>Redis</td><td>Datatypes, TTL, Cluster</td><td>String→List→Set→Hash→ZSet→Stream</td></tr>
        <tr><td>🐰 M10</td><td>RabbitMQ</td><td>Exchange Types, Routing</td><td>Direct→Fanout→Topic→Header</td></tr>
        <tr><td>🔌 M11</td><td>Socket</td><td>WebSocket, Rooms, Scale</td><td>Redis Adapter = Multiple Server Sync</td></tr>
        <tr><td>🔗 M12</td><td>URL Shortener</td><td>Hash, Cache, Nginx</td><td>Hash → Redis → PostgreSQL → Nginx</td></tr>
    </table>

    <!-- Technology Stack -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🛠️ Complete Technology Stack</h3>
    <div class="concept-grid">
        <div class="concept-card"><div class="card-icon">🟢</div><div class="card-title">Backend</div><div class="card-desc">Node.js + Express.js + TypeScript। REST API + WebSocket। JWT Auth। Input Validation।</div></div>
        <div class="concept-card green"><div class="card-icon">💾</div><div class="card-title">Database</div><div class="card-desc">PostgreSQL (Primary)। Redis (Cache + Session + Queue)। S3 (File Storage)। Elasticsearch (Search)।</div></div>
        <div class="concept-card purple"><div class="card-icon">📨</div><div class="card-title">Messaging</div><div class="card-desc">RabbitMQ (Task Queue)। Kafka (Event Streaming)। Redis Pub/Sub (Real-time)। Socket.io (WebSocket)।</div></div>
        <div class="concept-card orange"><div class="card-icon">🐳</div><div class="card-title">DevOps</div><div class="card-desc">Docker + Docker Compose। Kubernetes। Nginx (LB + Reverse Proxy)। AWS (EC2, RDS, S3, ELB)।</div></div>
        <div class="concept-card pink"><div class="card-icon">📊</div><div class="card-title">Monitoring</div><div class="card-desc">Prometheus + Grafana। CloudWatch। ELK Stack। Jaeger (Tracing)। Alerting।</div></div>
        <div class="concept-card yellow"><div class="card-icon">🔐</div><div class="card-title">Security</div><div class="card-desc">JWT + Refresh Token। Rate Limiting। HTTPS/SSL। CORS। Input Sanitization। Helmet.js।</div></div>
    </div>

    <!-- Interview Tips -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">💡 Interview Tips</h3>
    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🎯</div>
            <div class="card-title">Estimation প্রশ্নে</div>
            <div class="card-desc">১. DAU জিজ্ঞেস করো। ২. Read:Write ratio। ৩. RPS হিসাব। ৪. Peak ×3। ৫. Storage (৫ বছর)। ৬. Bandwidth। সবসময় ধাপে ধাপে!</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🏗️</div>
            <div class="card-title">System Design এ</div>
            <div class="card-desc">Requirements → Scale → API → DB → Cache → Scaling → Failure → Monitoring। প্রতিটা পদক্ষেপে কারণ বলো।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🔄</div>
            <div class="card-title">Trade-offs বলো</div>
            <div class="card-desc">SQL vs NoSQL। Cache vs DB। Sync vs Async। RabbitMQ vs Kafka। প্রতিটা পছন্দের WHY বলো — এটাই সেরা উত্তর!</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🔢</div>
            <div class="card-title">Key Numbers</div>
            <div class="card-desc">1 day = 86,400s। Peak = avg×3। 99.99% = 52min/year। Redis = 1ms। DB = 10-50ms। L1 Cache = 1ns।</div>
        </div>
    </div>

    <!-- Roadmap -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🗺️ শেখার রোডম্যাপ</h3>
    <div class="timeline">
        <div class="timeline-item"><div class="timeline-dot">1️⃣</div><div class="timeline-content"><h4>সপ্তাহ ১-২: Foundation</h4><p>Module 1 ও 2। CAP Theorem, Consistency Models, Latency মুখস্থ। Back-of-envelope calculation practice।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">2️⃣</div><div class="timeline-content"><h4>সপ্তাহ ৩-৪: Node.js ও API</h4><p>Module 3 ও 4। Express CRUD API বানাও। PostgreSQL সংযুক্ত করো। Rate Limiting implement করো।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">3️⃣</div><div class="timeline-content"><h4>সপ্তাহ ৫-৬: Docker ও Infrastructure</h4><p>Module 7 ও 8। App containerize করো। MySQL Replication সেটআপ করো। Network Namespace experiment করো।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">4️⃣</div><div class="timeline-content"><h4>সপ্তাহ ৭-৮: Redis ও Messaging</h4><p>Module 9 ও 10। সব Redis Data Type ব্যবহার করো। RabbitMQ দিয়ে async task বানাও। Kafka streaming experiment।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">5️⃣</div><div class="timeline-content"><h4>সপ্তাহ ৯-১০: Real-time ও AWS</h4><p>Module 6 ও 11। Socket.io দিয়ে chat app বানাও। AWS তে VPC, EC2, RDS deploy করো। Auto Scaling test করো।</p></div></div>
        <div class="timeline-item"><div class="timeline-dot">🎓</div><div class="timeline-content"><h4>সপ্তাহ ১১-১২: Full Project</h4><p>Module 12 + সব। URL Shortener বানাও সব component দিয়ে। System Design interview practice। Deploy করো!</p></div></div>
    </div>

    <!-- Final Motivation -->
    <div style="max-width:850px;margin:60px auto;text-align:center;padding:50px;background:linear-gradient(135deg,#0a1628,#0d2040);border:1px solid #00d4ff22;border-radius:24px;">
        <div style="font-size:52px;margin-bottom:20px;">🚀</div>
        <h3 style="font-size:30px;font-weight:900;background:linear-gradient(135deg,#00d4ff,#00ff88);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;margin-bottom:16px;">তুমি পারবে!</h3>
        <p style="font-size:16px;color:#aaa;line-height:1.8;margin-bottom:28px;">১২টা Module শেষ করেছো — এটাই সবচেয়ে বড় achievement! System Design শেখা একটা যাত্রা। প্রতিদিন কোড লেখো, experiment করো, build করো।</p>
        <div style="display:flex;gap:16px;justify-content:center;flex-wrap:wrap;">
            <div style="background:#00d4ff11;border:1px solid #00d4ff33;border-radius:12px;padding:16px 22px;text-align:center;"><div style="font-size:22px;">📚</div><div style="font-size:12px;color:#00d4ff;font-weight:700;margin-top:6px;">পড়ো</div></div>
            <div style="background:#00ff8811;border:1px solid #00ff8833;border-radius:12px;padding:16px 22px;text-align:center;"><div style="font-size:22px;">💻</div><div style="font-size:12px;color:#00ff88;font-weight:700;margin-top:6px;">কোড লেখো</div></div>
            <div style="background:#b44fff11;border:1px solid #b44fff33;border-radius:12px;padding:16px 22px;text-align:center;"><div style="font-size:22px;">🔧</div><div style="font-size:12px;color:#b44fff;font-weight:700;margin-top:6px;">Build করো</div></div>
            <div style="background:#ff8c0011;border:1px solid #ff8c0033;border-radius:12px;padding:16px 22px;text-align:center;"><div style="font-size:22px;">🌐</div><div style="font-size:12px;color:#ff8c00;font-weight:700;margin-top:6px;">Deploy করো</div></div>
            <div style="background:#ffd70011;border:1px solid #ffd70033;border-radius:12px;padding:16px 22px;text-align:center;"><div style="font-size:22px;">🎯</div><div style="font-size:12px;color:#ffd700;font-weight:700;margin-top:6px;">Interview Crack!</div></div>
        </div>
    </div>
</div>
</div>

<!-- FOOTER -->
<div class="footer">
    <div class="footer-logo">System Design & Backend Engineering — বাংলায়</div>
    <p class="footer-text">Module 1 • 2 • 3 • 4 • 6 • 7 • 8 • 9 • 10 • 11 • 12</p>
    <p class="footer-text">Redis • RabbitMQ • Socket • URL Shortener • AWS • Docker • Nginx</p>
    <div style="margin-top:24px;padding-top:24px;border-top:1px solid #111;">
        <p style="font-size:12px;color:#222;">সহজ বাংলায় শেখো • দক্ষ Engineer হও • 🚀</p>
    </div>
</div>

<script>
    // Smooth scroll
    document.querySelectorAll('a[href^="#"]').forEach(a => {
        a.addEventListener('click', function(e) {
            e.preventDefault();
            const t = document.querySelector(this.getAttribute('href'));
            if(t) t.scrollIntoView({ behavior:'smooth', block:'start' });
        });
    });

    // Scroll animations
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(e => {
            if(e.isIntersecting) {
                e.target.style.opacity = '1';
                e.target.style.transform = 'translateY(0)';
            }
        });
    }, { threshold: 0.08 });

    document.querySelectorAll('.concept-card,.metric-card,.timeline-item,.step-item,.datatype-card,.col-box').forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(18px)';
        el.style.transition = 'opacity 0.45s ease, transform 0.45s ease';
        observer.observe(el);
    });

    console.log(`
╔══════════════════════════════════════════════╗
║   System Design Guide — সম্পূর্ণ বাংলায়  ║
║   ✅ সব ১২টা Module লোড হয়েছে!           ║
║   Module 9:  Redis                          ║
║   Module 10: RabbitMQ                       ║
║   Module 11: Socket                         ║
║   Module 12: URL Shortener                  ║
╚══════════════════════════════════════════════╝
    `);
</script>
</body>
</html>
```

## ফাইলটি সেভ করার নির্দেশনা:

**`system-design-complete-bangla.html`** নামে সেভ করো।

### নতুন যা যোগ হয়েছে:

| Module | বিষয় | হাইলাইট |
|--------|-------|----------|
| **⚡ M9: Redis** | সব ৮টা Data Type | String, List, Set, Hash, ZSet, Bitmap, HyperLogLog, Stream, Geo |
| **🐰 M10: RabbitMQ** | ৫টা Exchange Type | Direct, Default, Fanout, Topic, Header — Visual Diagram |
| **🔌 M11: Socket** | Real-time Chat | Socket.io Code, Scaling with Redis Adapter |
| **🔗 M12: URL Shortener** | Full System Design | Nginx Config, Architecture, Design Decisions |
