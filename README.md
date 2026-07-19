<!DOCTYPE html>
<html lang="bn">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>System Design & Backend Engineering - সম্পূর্ণ গাইড বাংলায়</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', 'SolaimanLipi', 'Kalpurush', Arial, sans-serif;
            background: #0a0a0a;
            color: #e0e0e0;
            line-height: 1.8;
        }

        /* ══════════════════════════════════════
           COVER PAGE
        ══════════════════════════════════════ */
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
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, rgba(0, 212, 255, 0.05) 0%, transparent 70%);
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        .cover-badge {
            background: linear-gradient(135deg, #00d4ff, #0080ff);
            color: white;
            padding: 8px 24px;
            border-radius: 50px;
            font-size: 14px;
            font-weight: 700;
            letter-spacing: 3px;
            text-transform: uppercase;
            margin-bottom: 30px;
        }

        .cover-title {
            font-size: 52px;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #ffffff, #00d4ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            line-height: 1.2;
            margin-bottom: 20px;
        }

        .cover-subtitle {
            font-size: 22px;
            color: #888;
            margin-bottom: 40px;
        }

        .cover-modules {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 15px;
            max-width: 900px;
            margin: 40px auto;
        }

        .cover-module-card {
            background: rgba(255,255,255,0.05);
            border: 1px solid rgba(0, 212, 255, 0.2);
            border-radius: 12px;
            padding: 15px;
            text-align: center;
        }

        .cover-module-card .module-icon {
            font-size: 28px;
            margin-bottom: 8px;
        }

        .cover-module-card .module-name {
            font-size: 12px;
            color: #00d4ff;
            font-weight: 600;
        }

        .cover-stats {
            display: flex;
            gap: 40px;
            margin-top: 40px;
        }

        .stat {
            text-align: center;
        }

        .stat-number {
            font-size: 36px;
            font-weight: 900;
            color: #00d4ff;
        }

        .stat-label {
            font-size: 13px;
            color: #666;
        }

        /* ══════════════════════════════════════
           NAVIGATION / TOC
        ══════════════════════════════════════ */
        .toc {
            background: #111;
            padding: 60px 40px;
            border-bottom: 1px solid #222;
        }

        .toc-title {
            font-size: 32px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 40px;
            text-align: center;
        }

        .toc-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .toc-item {
            background: #1a1a1a;
            border: 1px solid #2a2a2a;
            border-left: 4px solid #00d4ff;
            border-radius: 10px;
            padding: 20px;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            color: inherit;
            display: block;
        }

        .toc-item:hover {
            border-left-color: #00ff88;
            transform: translateX(5px);
            background: #1e1e1e;
        }

        .toc-item-header {
            display: flex;
            align-items: center;
            gap: 12px;
            margin-bottom: 8px;
        }

        .toc-module-num {
            background: linear-gradient(135deg, #00d4ff, #0080ff);
            color: white;
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 800;
            font-size: 14px;
            flex-shrink: 0;
        }

        .toc-module-title {
            font-size: 15px;
            font-weight: 700;
            color: #fff;
        }

        .toc-topics {
            font-size: 12px;
            color: #666;
            padding-left: 48px;
        }

        /* ══════════════════════════════════════
           MODULE SECTIONS
        ══════════════════════════════════════ */
        .module-section {
            padding: 80px 40px;
            border-bottom: 2px solid #1a1a1a;
        }

        .module-section:nth-child(even) {
            background: #0d0d0d;
        }

        .module-header {
            text-align: center;
            margin-bottom: 60px;
        }

        .module-number-badge {
            display: inline-block;
            background: linear-gradient(135deg, #00d4ff, #0080ff);
            color: white;
            padding: 6px 20px;
            border-radius: 50px;
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 2px;
            margin-bottom: 15px;
        }

        .module-title {
            font-size: 38px;
            font-weight: 900;
            color: #fff;
            margin-bottom: 12px;
        }

        .module-subtitle {
            font-size: 16px;
            color: #666;
        }

        /* ══════════════════════════════════════
           CONCEPT CARDS
        ══════════════════════════════════════ */
        .concept-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 24px;
            margin: 40px 0;
            max-width: 1200px;
            margin-left: auto;
            margin-right: auto;
        }

        .concept-card {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 16px;
            padding: 28px;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .concept-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 3px;
            background: linear-gradient(90deg, #00d4ff, #0080ff);
        }

        .concept-card:hover {
            border-color: #00d4ff33;
            transform: translateY(-4px);
            box-shadow: 0 20px 40px rgba(0, 212, 255, 0.1);
        }

        .concept-card.green::before { background: linear-gradient(90deg, #00ff88, #00cc66); }
        .concept-card.purple::before { background: linear-gradient(90deg, #b44fff, #7c3aed); }
        .concept-card.orange::before { background: linear-gradient(90deg, #ff8c00, #ff4500); }
        .concept-card.pink::before { background: linear-gradient(90deg, #ff6b9d, #c44569); }
        .concept-card.yellow::before { background: linear-gradient(90deg, #ffd700, #ffa500); }

        .card-icon {
            font-size: 36px;
            margin-bottom: 16px;
        }

        .card-title {
            font-size: 18px;
            font-weight: 800;
            color: #fff;
            margin-bottom: 12px;
        }

        .card-desc {
            font-size: 14px;
            color: #aaa;
            line-height: 1.7;
        }

        /* ══════════════════════════════════════
           FLOW DIAGRAMS
        ══════════════════════════════════════ */
        .flow-container {
            background: #0f0f0f;
            border: 1px solid #2a2a2a;
            border-radius: 20px;
            padding: 40px;
            margin: 40px auto;
            max-width: 1000px;
        }

        .flow-title {
            font-size: 20px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 30px;
            text-align: center;
        }

        .flow-row {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-wrap: wrap;
            gap: 10px;
            margin: 20px 0;
        }

        .flow-box {
            background: linear-gradient(135deg, #1a2a3a, #1a1a2e);
            border: 1px solid #00d4ff33;
            border-radius: 12px;
            padding: 16px 24px;
            text-align: center;
            min-width: 120px;
        }

        .flow-box .fb-icon { font-size: 24px; margin-bottom: 6px; }
        .flow-box .fb-label { font-size: 13px; font-weight: 700; color: #00d4ff; }
        .flow-box .fb-sub { font-size: 11px; color: #666; margin-top: 4px; }

        .flow-arrow {
            font-size: 24px;
            color: #00d4ff;
            font-weight: 900;
        }

        /* ══════════════════════════════════════
           COMPARISON TABLE
        ══════════════════════════════════════ */
        .comparison-table {
            width: 100%;
            max-width: 1000px;
            margin: 40px auto;
            border-collapse: collapse;
            border-radius: 16px;
            overflow: hidden;
        }

        .comparison-table th {
            background: linear-gradient(135deg, #00d4ff22, #0080ff22);
            color: #00d4ff;
            padding: 16px 20px;
            text-align: left;
            font-size: 14px;
            font-weight: 700;
            border-bottom: 2px solid #00d4ff44;
        }

        .comparison-table td {
            padding: 14px 20px;
            border-bottom: 1px solid #1e1e1e;
            font-size: 13px;
            color: #ccc;
            background: #111;
        }

        .comparison-table tr:hover td {
            background: #151515;
        }

        .badge {
            display: inline-block;
            padding: 3px 10px;
            border-radius: 20px;
            font-size: 11px;
            font-weight: 700;
        }

        .badge-green { background: #00ff8822; color: #00ff88; border: 1px solid #00ff8844; }
        .badge-red { background: #ff444422; color: #ff6666; border: 1px solid #ff444444; }
        .badge-blue { background: #00d4ff22; color: #00d4ff; border: 1px solid #00d4ff44; }
        .badge-yellow { background: #ffd70022; color: #ffd700; border: 1px solid #ffd70044; }

        /* ══════════════════════════════════════
           CODE BLOCKS
        ══════════════════════════════════════ */
        .code-block {
            background: #0d1117;
            border: 1px solid #2a2a2a;
            border-radius: 12px;
            padding: 28px;
            margin: 24px auto;
            max-width: 1000px;
            overflow-x: auto;
            position: relative;
        }

        .code-block-header {
            display: flex;
            align-items: center;
            gap: 10px;
            margin-bottom: 20px;
            padding-bottom: 16px;
            border-bottom: 1px solid #2a2a2a;
        }

        .code-dots {
            display: flex;
            gap: 6px;
        }

        .code-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }

        .dot-red { background: #ff5f57; }
        .dot-yellow { background: #febc2e; }
        .dot-green { background: #28c840; }

        .code-filename {
            font-size: 13px;
            color: #666;
            margin-left: 10px;
        }

        .code-block pre {
            font-family: 'Courier New', 'Consolas', monospace;
            font-size: 13px;
            line-height: 1.8;
            color: #e6edf3;
            white-space: pre-wrap;
            word-wrap: break-word;
        }

        .code-block .comment { color: #6a9955; }
        .code-block .keyword { color: #569cd6; }
        .code-block .string { color: #ce9178; }
        .code-block .number { color: #b5cea8; }

        /* ══════════════════════════════════════
           INFO BOXES
        ══════════════════════════════════════ */
        .info-box {
            border-radius: 12px;
            padding: 24px 28px;
            margin: 24px auto;
            max-width: 1000px;
            display: flex;
            gap: 16px;
            align-items: flex-start;
        }

        .info-box.tip {
            background: rgba(0, 255, 136, 0.05);
            border: 1px solid rgba(0, 255, 136, 0.2);
        }

        .info-box.warning {
            background: rgba(255, 200, 0, 0.05);
            border: 1px solid rgba(255, 200, 0, 0.2);
        }

        .info-box.danger {
            background: rgba(255, 68, 68, 0.05);
            border: 1px solid rgba(255, 68, 68, 0.2);
        }

        .info-box.info {
            background: rgba(0, 212, 255, 0.05);
            border: 1px solid rgba(0, 212, 255, 0.2);
        }

        .info-icon {
            font-size: 24px;
            flex-shrink: 0;
        }

        .info-content .info-title {
            font-size: 15px;
            font-weight: 800;
            margin-bottom: 8px;
        }

        .info-box.tip .info-title { color: #00ff88; }
        .info-box.warning .info-title { color: #ffc800; }
        .info-box.danger .info-title { color: #ff4444; }
        .info-box.info .info-title { color: #00d4ff; }

        .info-content p {
            font-size: 14px;
            color: #aaa;
            line-height: 1.7;
        }

        /* ══════════════════════════════════════
           ARCHITECTURE DIAGRAMS
        ══════════════════════════════════════ */
        .arch-diagram {
            background: #0f0f0f;
            border: 1px solid #2a2a2a;
            border-radius: 20px;
            padding: 40px;
            margin: 40px auto;
            max-width: 1000px;
            text-align: center;
        }

        .arch-title {
            font-size: 20px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 40px;
        }

        .arch-layer {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 12px;
            padding: 20px;
            margin: 10px 0;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .arch-layer.highlight {
            border-color: #00d4ff44;
            background: #00d4ff08;
        }

        .arch-node {
            background: #1a2a3a;
            border: 1px solid #00d4ff44;
            border-radius: 10px;
            padding: 12px 20px;
            text-align: center;
        }

        .arch-node .node-icon { font-size: 20px; }
        .arch-node .node-label {
            font-size: 12px;
            font-weight: 700;
            color: #00d4ff;
            margin-top: 4px;
        }
        .arch-node .node-sub {
            font-size: 10px;
            color: #555;
        }

        .arch-arrow-down {
            text-align: center;
            font-size: 20px;
            color: #00d4ff;
            margin: 5px 0;
        }

        /* ══════════════════════════════════════
           METRICS / STATS CARDS
        ══════════════════════════════════════ */
        .metrics-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin: 40px auto;
            max-width: 1000px;
        }

        .metric-card {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 16px;
            padding: 24px;
            text-align: center;
        }

        .metric-value {
            font-size: 32px;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #00ff88);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .metric-label {
            font-size: 13px;
            color: #666;
            margin-top: 6px;
        }

        .metric-desc {
            font-size: 12px;
            color: #444;
            margin-top: 4px;
        }

        /* ══════════════════════════════════════
           ALGORITHM VISUALIZATION
        ══════════════════════════════════════ */
        .algo-container {
            background: #0f0f0f;
            border: 1px solid #2a2a2a;
            border-radius: 20px;
            padding: 40px;
            margin: 40px auto;
            max-width: 1000px;
        }

        .algo-title {
            font-size: 18px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 24px;
        }

        .token-bucket {
            display: flex;
            align-items: center;
            gap: 30px;
            flex-wrap: wrap;
        }

        .bucket-visual {
            background: #1a1a1a;
            border: 2px solid #00d4ff;
            border-radius: 0 0 16px 16px;
            border-top: none;
            width: 120px;
            height: 150px;
            position: relative;
            overflow: hidden;
        }

        .bucket-fill {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(180deg, #00d4ff66, #00d4ff);
            transition: height 0.5s;
        }

        .bucket-tokens {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 24px;
            font-weight: 900;
            color: white;
            z-index: 1;
        }

        .nines-table {
            width: 100%;
            max-width: 800px;
            margin: 0 auto;
        }

        .nines-row {
            display: flex;
            align-items: center;
            gap: 16px;
            padding: 12px 0;
            border-bottom: 1px solid #1a1a1a;
        }

        .nines-percent {
            font-size: 16px;
            font-weight: 800;
            color: #00d4ff;
            width: 100px;
        }

        .nines-bar-bg {
            flex: 1;
            height: 8px;
            background: #1a1a1a;
            border-radius: 4px;
            overflow: hidden;
        }

        .nines-bar-fill {
            height: 100%;
            border-radius: 4px;
            background: linear-gradient(90deg, #00d4ff, #00ff88);
        }

        .nines-downtime {
            font-size: 13px;
            color: #888;
            width: 150px;
            text-align: right;
        }

        /* ══════════════════════════════════════
           NETWORK DIAGRAMS
        ══════════════════════════════════════ */
        .network-diagram {
            background: #0f0f0f;
            border: 1px solid #2a2a2a;
            border-radius: 20px;
            padding: 40px;
            margin: 40px auto;
            max-width: 1000px;
        }

        .namespace-box {
            background: #1a1a1a;
            border: 2px dashed #00d4ff44;
            border-radius: 12px;
            padding: 20px;
            margin: 10px;
            display: inline-block;
            text-align: center;
            min-width: 150px;
        }

        .namespace-title {
            font-size: 13px;
            font-weight: 700;
            color: #00d4ff;
            margin-bottom: 10px;
        }

        .namespace-ip {
            font-size: 12px;
            color: #888;
            font-family: monospace;
        }

        .bridge-box {
            background: linear-gradient(135deg, #1a2a1a, #1a3a1a);
            border: 2px solid #00ff8844;
            border-radius: 12px;
            padding: 16px 30px;
            text-align: center;
            display: inline-block;
        }

        .bridge-label {
            font-size: 14px;
            font-weight: 800;
            color: #00ff88;
        }

        .bridge-ip {
            font-size: 12px;
            color: #666;
            font-family: monospace;
        }

        .veth-line {
            display: flex;
            align-items: center;
            justify-content: center;
            color: #00d4ff;
            font-size: 20px;
            margin: 5px 0;
        }

        /* ══════════════════════════════════════
           SECTION DIVIDERS
        ══════════════════════════════════════ */
        .section-divider {
            height: 2px;
            background: linear-gradient(90deg, transparent, #00d4ff44, transparent);
            margin: 60px auto;
            max-width: 600px;
        }

        .subsection-title {
            font-size: 24px;
            font-weight: 800;
            color: #fff;
            margin: 40px auto 24px;
            max-width: 1000px;
            padding-left: 16px;
            border-left: 4px solid #00d4ff;
        }

        .subsection-desc {
            font-size: 15px;
            color: #777;
            max-width: 1000px;
            margin: 0 auto 30px;
        }

        /* ══════════════════════════════════════
           TIMELINE
        ══════════════════════════════════════ */
        .timeline {
            max-width: 800px;
            margin: 40px auto;
            position: relative;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 30px;
            top: 0;
            bottom: 0;
            width: 2px;
            background: linear-gradient(180deg, #00d4ff, #0080ff);
        }

        .timeline-item {
            display: flex;
            gap: 24px;
            margin-bottom: 30px;
            padding-left: 10px;
        }

        .timeline-dot {
            width: 42px;
            height: 42px;
            background: linear-gradient(135deg, #00d4ff, #0080ff);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
            flex-shrink: 0;
            z-index: 1;
        }

        .timeline-content {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 12px;
            padding: 20px;
            flex: 1;
        }

        .timeline-content h4 {
            font-size: 16px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 8px;
        }

        .timeline-content p {
            font-size: 14px;
            color: #aaa;
            line-height: 1.6;
        }

        /* ══════════════════════════════════════
           FOOTER
        ══════════════════════════════════════ */
        .footer {
            background: #050505;
            padding: 60px 40px;
            text-align: center;
            border-top: 1px solid #1a1a1a;
        }

        .footer-logo {
            font-size: 28px;
            font-weight: 900;
            background: linear-gradient(135deg, #00d4ff, #ffffff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 16px;
        }

        .footer-text {
            font-size: 14px;
            color: #444;
            margin-bottom: 8px;
        }

        /* ══════════════════════════════════════
           PRINT STYLES
        ══════════════════════════════════════ */
        @media print {
            body { background: white; color: black; }
            .cover { background: #f0f8ff; min-height: auto; padding: 40px; }
            .module-section { padding: 40px 20px; }
            .concept-card { border: 1px solid #ddd; background: #f9f9f9; }
            .code-block { background: #f5f5f5; color: black; border: 1px solid #ddd; }
        }

        /* ══════════════════════════════════════
           SCROLL ANIMATIONS
        ══════════════════════════════════════ */
        @keyframes fadeInUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .animate-in {
            animation: fadeInUp 0.6s ease forwards;
        }

        /* ══════════════════════════════════════
           RESPONSIVE
        ══════════════════════════════════════ */
        @media (max-width: 768px) {
            .cover-title { font-size: 32px; }
            .cover-modules { grid-template-columns: repeat(2, 1fr); }
            .toc-grid { grid-template-columns: 1fr; }
            .concept-grid { grid-template-columns: 1fr; }
            .metrics-grid { grid-template-columns: repeat(2, 1fr); }
            .cover-stats { gap: 20px; }
            .module-title { font-size: 28px; }
        }

        /* Highlight classes */
        .highlight-blue { color: #00d4ff; font-weight: 700; }
        .highlight-green { color: #00ff88; font-weight: 700; }
        .highlight-orange { color: #ff8c00; font-weight: 700; }
        .highlight-red { color: #ff4444; font-weight: 700; }
        .highlight-yellow { color: #ffd700; font-weight: 700; }

        /* List styles */
        .custom-list {
            list-style: none;
            max-width: 1000px;
            margin: 20px auto;
        }

        .custom-list li {
            padding: 10px 0;
            border-bottom: 1px solid #1a1a1a;
            font-size: 14px;
            color: #ccc;
            display: flex;
            align-items: flex-start;
            gap: 12px;
        }

        .custom-list li::before {
            content: '▸';
            color: #00d4ff;
            font-size: 16px;
            flex-shrink: 0;
            margin-top: 2px;
        }

        /* Step boxes */
        .steps-container {
            max-width: 1000px;
            margin: 40px auto;
        }

        .step-item {
            display: flex;
            gap: 20px;
            margin-bottom: 20px;
            align-items: flex-start;
        }

        .step-number {
            background: linear-gradient(135deg, #00d4ff, #0080ff);
            color: white;
            width: 44px;
            height: 44px;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 900;
            font-size: 18px;
            flex-shrink: 0;
        }

        .step-content {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 12px;
            padding: 20px;
            flex: 1;
        }

        .step-content h4 {
            font-size: 16px;
            font-weight: 800;
            color: #fff;
            margin-bottom: 8px;
        }

        .step-content p {
            font-size: 14px;
            color: #aaa;
            line-height: 1.6;
        }

        /* Two column layout */
        .two-col {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 24px;
            max-width: 1000px;
            margin: 40px auto;
        }

        @media (max-width: 768px) {
            .two-col { grid-template-columns: 1fr; }
        }

        .col-box {
            background: #141414;
            border: 1px solid #2a2a2a;
            border-radius: 16px;
            padding: 24px;
        }

        .col-box h4 {
            font-size: 16px;
            font-weight: 800;
            color: #00d4ff;
            margin-bottom: 16px;
            padding-bottom: 12px;
            border-bottom: 1px solid #2a2a2a;
        }

        .col-box ul {
            list-style: none;
        }

        .col-box ul li {
            padding: 8px 0;
            font-size: 14px;
            color: #aaa;
            border-bottom: 1px solid #1a1a1a;
            display: flex;
            gap: 8px;
        }

        .col-box ul li:last-child { border: none; }
    </style>
</head>
<body>

<!-- ══════════════════════════════════════════════════
     COVER PAGE
══════════════════════════════════════════════════ -->
<div class="cover">
    <div class="cover-badge">📚 সম্পূর্ণ গাইড ২০২৪</div>
    <h1 class="cover-title">System Design &<br>Backend Engineering</h1>
    <p class="cover-subtitle">সহজ বাংলায় — ভিজুয়াল ও প্র্যাকটিক্যাল পদ্ধতিতে</p>

    <div class="cover-modules">
        <div class="cover-module-card">
            <div class="module-icon">🏗️</div>
            <div class="module-name">Module 1<br>System Design Basics</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🧮</div>
            <div class="module-name">Module 2<br>Mathematics</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🟢</div>
            <div class="module-name">Module 3<br>Node.js API</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🚦</div>
            <div class="module-name">Module 4<br>Rate Limiting</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">☁️</div>
            <div class="module-name">Module 6<br>AWS Scaling</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🐳</div>
            <div class="module-name">Module 7<br>Docker</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🌐</div>
            <div class="module-name">Module 8<br>Microservice Net</div>
        </div>
        <div class="cover-module-card">
            <div class="module-icon">🎯</div>
            <div class="module-name">সব একসাথে<br>বাংলায়</div>
        </div>
    </div>

    <div class="cover-stats">
        <div class="stat">
            <div class="stat-number">7+</div>
            <div class="stat-label">মডিউল</div>
        </div>
        <div class="stat">
            <div class="stat-number">50+</div>
            <div class="stat-label">ভিজুয়াল ডায়াগ্রাম</div>
        </div>
        <div class="stat">
            <div class="stat-number">100+</div>
            <div class="stat-label">বাংলা উদাহরণ</div>
        </div>
        <div class="stat">
            <div class="stat-number">∞</div>
            <div class="stat-label">জ্ঞান</div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     TABLE OF CONTENTS
══════════════════════════════════════════════════ -->
<div class="toc" id="toc">
    <h2 class="toc-title">📋 বিষয়সূচি</h2>
    <div class="toc-grid">
        <a href="#module1" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">1</div>
                <div class="toc-module-title">🏗️ System Design Basics</div>
            </div>
            <div class="toc-topics">নেটওয়ার্কিং • Consistency Models • Failure Models • CAP Theorem • System Architecture</div>
        </a>
        <a href="#module2" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">2</div>
                <div class="toc-module-title">🧮 Mathematics for System Design</div>
            </div>
            <div class="toc-topics">Latency • Server Types • RPS Estimation • Storage • Bandwidth • Availability • Scalability</div>
        </a>
        <a href="#module3" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">3</div>
                <div class="toc-module-title">🟢 Node.js API Development</div>
            </div>
            <div class="toc-topics">Node.js Basics • ES6 • Async Programming • Express.js • PostgreSQL • Microservices</div>
        </a>
        <a href="#module4" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">4</div>
                <div class="toc-module-title">🚦 Rate Limit Module</div>
            </div>
            <div class="toc-topics">Token Bucket • Fixed Window • Sliding Window • Nginx • Microservice Rate Limit</div>
        </a>
        <a href="#module6" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">6</div>
                <div class="toc-module-title">☁️ AWS For Scaling</div>
            </div>
            <div class="toc-topics">VPC • Networking • Microservices • Storage • Database • Auto Scaling • Load Balancer</div>
        </a>
        <a href="#module7" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">7</div>
                <div class="toc-module-title">🐳 Docker For Backend</div>
            </div>
            <div class="toc-topics">Dockerfile • MySQL Replication • Redis • Kafka • Elasticsearch • Nginx LB • Docker Compose</div>
        </a>
        <a href="#module8" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">8</div>
                <div class="toc-module-title">🌐 Microservice Networking</div>
            </div>
            <div class="toc-topics">Linux Networking • Network Namespace • veth Pair • Bridge • Host Connection</div>
        </a>
        <a href="#summary" class="toc-item">
            <div class="toc-item-header">
                <div class="toc-module-num">✓</div>
                <div class="toc-module-title">🎯 সম্পূর্ণ সারসংক্ষেপ</div>
            </div>
            <div class="toc-topics">সব Module একসাথে • Quick Reference • Interview Tips • রোডম্যাপ</div>
        </a>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 1: SYSTEM DESIGN BASICS
══════════════════════════════════════════════════ -->
<div class="module-section" id="module1">
    <div class="module-header">
        <div class="module-number-badge">MODULE 01</div>
        <h2 class="module-title">🏗️ System Design Basics</h2>
        <p class="module-subtitle">নেটওয়ার্কিং থেকে CAP Theorem — সব বাংলায়</p>
    </div>

    <!-- Networking Basics -->
    <h3 class="subsection-title">📡 Networking Basics</h3>
    <p class="subsection-desc">নেটওয়ার্কিং হলো এক জায়গা থেকে আরেক জায়গায় ডাটা পাঠানোর প্রক্রিয়া।</p>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">📮</div>
            <div class="card-title">IP Address</div>
            <div class="card-desc">প্রতিটা ডিভাইসের ইউনিক ঠিকানা। যেমন বাড়ির ডাক ঠিকানা। উদাহরণ: 192.168.1.1 হলো তোমার Router এর ঠিকানা।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🚪</div>
            <div class="card-title">Port</div>
            <div class="card-desc">একটা সার্ভারের বিভিন্ন দরজা। Port 80 = HTTP, Port 443 = HTTPS, Port 3306 = MySQL। এক ঠিকানায় অনেক সেবা চলতে পারে।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📖</div>
            <div class="card-title">DNS</div>
            <div class="card-desc">ফোনবুকের মতো। google.com লিখলে DNS বলে "এর IP হলো 142.250.190.14"। তুমি নাম মনে রাখো, DNS IP মনে রাখে।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🤝</div>
            <div class="card-title">Protocol</div>
            <div class="card-desc">কথা বলার নিয়ম। HTTP = ওয়েব ব্রাউজিং, TCP = নির্ভরযোগ্য ডাটা, UDP = দ্রুত কিন্তু অনিশ্চিত ডাটা।</div>
        </div>
    </div>

    <!-- Request-Response Flow -->
    <div class="flow-container">
        <div class="flow-title">📊 Request-Response Flow</div>
        <div class="flow-row">
            <div class="flow-box">
                <div class="fb-icon">👤</div>
                <div class="fb-label">User</div>
                <div class="fb-sub">Browser/App</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">📡</div>
                <div class="fb-label">DNS</div>
                <div class="fb-sub">নাম → IP</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">⚖️</div>
                <div class="fb-label">Load Balancer</div>
                <div class="fb-sub">ট্রাফিক ভাগ</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">🖥️</div>
                <div class="fb-label">Server</div>
                <div class="fb-sub">Request প্রসেস</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">💾</div>
                <div class="fb-label">Database</div>
                <div class="fb-sub">ডাটা আনা/রাখা</div>
            </div>
        </div>
    </div>

    <!-- Consistency Models -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔄 Consistency Models</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">⚡</div>
            <div class="card-title">Strict Consistency</div>
            <div class="card-desc"><strong style="color:#00d4ff">সবচেয়ে কঠোর।</strong> একজন লিখলে সবাই সাথে সাথে দেখে। ব্যাংকের মতো — টাকা কাটলে সব জায়গায় তাৎক্ষণিক আপডেট। বাস্তবে প্রায় অসম্ভব।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">📋</div>
            <div class="card-title">Sequential Consistency</div>
            <div class="card-desc"><strong style="color:#00ff88">ক্রম মানে।</strong> সবাই একই ক্রমে দেখে, কিন্তু একটু দেরি হতে পারে। পোস্ট ১→২→৩ — সবাই এই ক্রমেই দেখবে।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🔗</div>
            <div class="card-title">Causal Consistency</div>
            <div class="card-desc"><strong style="color:#b44fff">সম্পর্কিত ক্রম।</strong> প্রশ্ন আগে, উত্তর পরে — এই ক্রম রক্ষা হয়। সম্পর্কহীন জিনিস যেকোনো ক্রমে হতে পারে।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🌐</div>
            <div class="card-title">Eventual Consistency</div>
            <div class="card-desc"><strong style="color:#ff8c00">শেষ পর্যন্ত একই।</strong> এখনই না, কিন্তু কিছুক্ষণ পরে সবাই একই দেখবে। Instagram Like count এভাবে কাজ করে।</div>
        </div>
    </div>

    <!-- CAP Theorem -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">⚖️ CAP Theorem</h3>

    <div class="arch-diagram">
        <div class="arch-title">⚖️ CAP Theorem — ৩টার মধ্যে ২টাই পাবে!</div>
        <div style="display:flex; justify-content:center; gap:40px; flex-wrap:wrap; margin:30px 0;">
            <div style="text-align:center;">
                <div style="font-size:48px;">🎯</div>
                <div style="font-size:20px; font-weight:900; color:#00d4ff; margin:10px 0;">C</div>
                <div style="font-size:15px; font-weight:700; color:#fff;">Consistency</div>
                <div style="font-size:13px; color:#666; max-width:150px;">সব সার্ভার একই ডাটা দেখায়</div>
            </div>
            <div style="text-align:center;">
                <div style="font-size:48px;">✅</div>
                <div style="font-size:20px; font-weight:900; color:#00ff88; margin:10px 0;">A</div>
                <div style="font-size:15px; font-weight:700; color:#fff;">Availability</div>
                <div style="font-size:13px; color:#666; max-width:150px;">সবসময় কাজ করে, "না" বলে না</div>
            </div>
            <div style="text-align:center;">
                <div style="font-size:48px;">🛡️</div>
                <div style="font-size:20px; font-weight:900; color:#b44fff; margin:10px 0;">P</div>
                <div style="font-size:15px; font-weight:700; color:#fff;">Partition Tolerance</div>
                <div style="font-size:13px; color:#666; max-width:150px;">নেটওয়ার্ক কাটলেও চলে</div>
            </div>
        </div>
        <table class="comparison-table" style="margin-top:20px;">
            <tr>
                <th>Combination</th>
                <th>কী পাবে</th>
                <th>কী হারাবে</th>
                <th>উদাহরণ</th>
            </tr>
            <tr>
                <td><span class="badge badge-blue">CP</span></td>
                <td>সঠিক ডাটা + নেটওয়ার্ক সমস্যায় চলে</td>
                <td>কখনো unavailable হয়</td>
                <td>🏦 ব্যাংক, MongoDB</td>
            </tr>
            <tr>
                <td><span class="badge badge-green">AP</span></td>
                <td>সবসময় চলে + নেটওয়ার্ক সমস্যায় চলে</td>
                <td>পুরানো ডাটা দেখাতে পারে</td>
                <td>📱 Facebook, Cassandra</td>
            </tr>
            <tr>
                <td><span class="badge badge-yellow">CA</span></td>
                <td>সঠিক ডাটা + সবসময় চলে</td>
                <td>নেটওয়ার্ক বিচ্ছিন্নতায় ব্যর্থ</td>
                <td>🖥️ Single Server</td>
            </tr>
        </table>
    </div>

    <!-- Failure Models -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">💥 Failure Models</h3>

    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-dot">🛑</div>
            <div class="timeline-content">
                <h4>Fail-Stop — সহজ ব্যর্থতা</h4>
                <p>সার্ভার বন্ধ হয়ে সবাইকে জানায় "আমি বন্ধ!" ফ্যানের সুইচ অফের মতো — সবাই দেখতে পায়। সবচেয়ে সহজ ব্যর্থতা।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">💀</div>
            <div class="timeline-content">
                <h4>Crash Failure — নীরব ব্যর্থতা</h4>
                <p>সার্ভার চুপচাপ বন্ধ হয়, কাউকে জানায় না। ফোন হঠাৎ বন্ধ হওয়ার মতো — কারণ কেউ জানে না।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">📭</div>
            <div class="timeline-content">
                <h4>Omission Failure — বাদ পড়া</h4>
                <p>সার্ভার চলছে কিন্তু কিছু message পাঠায় না বা পায় না। ৫টা SMS পাঠালে ৩টা পেল — ২টা মাঝে হারিয়ে গেল।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">⏰</div>
            <div class="timeline-content">
                <h4>Temporal Failure — দেরি করা</h4>
                <p>সার্ভার কাজ করে কিন্তু অনেক দেরিতে। Uber driver ১ ঘণ্টা পরে এলো — কাজ হয়েছে, কিন্তু সময়মতো হয়নি।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">😈</div>
            <div class="timeline-content">
                <h4>Byzantine Failure — প্রতারণা</h4>
                <p>সার্ভার ইচ্ছাকৃতভাবে ভুল তথ্য দেয়। হ্যাক হওয়া সার্ভার মিথ্যা ব্যালেন্স দেখায়। সবচেয়ে বিপজ্জনক!</p>
            </div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 2: MATHEMATICS
══════════════════════════════════════════════════ -->
<div class="module-section" id="module2">
    <div class="module-header">
        <div class="module-number-badge">MODULE 02</div>
        <h2 class="module-title">🧮 Mathematics for System Design</h2>
        <p class="module-subtitle">Estimation, Latency, Scalability — সব হিসাব বাংলায়</p>
    </div>

    <!-- Key Numbers -->
    <h3 class="subsection-title">📏 গুরুত্বপূর্ণ সংখ্যা মনে রাখো</h3>
    <div class="metrics-grid">
        <div class="metric-card">
            <div class="metric-value">1 KB</div>
            <div class="metric-label">= ১,০২৪ bytes</div>
            <div class="metric-desc">একটা ছোট টেক্সট ফাইল</div>
        </div>
        <div class="metric-card">
            <div class="metric-value">1 MB</div>
            <div class="metric-label">= ১,০২৪ KB</div>
            <div class="metric-desc">একটা ছবি / গান</div>
        </div>
        <div class="metric-card">
            <div class="metric-value">1 GB</div>
            <div class="metric-label">= ১,০২৪ MB</div>
            <div class="metric-desc">একটা মুভি</div>
        </div>
        <div class="metric-card">
            <div class="metric-value">86,400</div>
            <div class="metric-label">= ১ দিনের সেকেন্ড</div>
            <div class="metric-desc">RPS হিসাবের ভাজক</div>
        </div>
        <div class="metric-card">
            <div class="metric-value">~100K</div>
            <div class="metric-label">মোটামুটি ১ দিন</div>
            <div class="metric-desc">সহজ হিসাবের জন্য</div>
        </div>
        <div class="metric-card">
            <div class="metric-value">×3</div>
            <div class="metric-label">Peak Multiplier</div>
            <div class="metric-desc">Average থেকে Peak</div>
        </div>
    </div>

    <!-- Latency Table -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">⏱️ Latency Numbers</h3>

    <table class="comparison-table">
        <tr>
            <th>অপারেশন</th>
            <th>সময়</th>
            <th>তুলনা</th>
            <th>বাস্তব উদাহরণ</th>
        </tr>
        <tr>
            <td>⚡ L1 Cache</td>
            <td><span class="badge badge-green">1 ns</span></td>
            <td>চোখের পলক</td>
            <td>CPU এর সবচেয়ে কাছের মেমরি</td>
        </tr>
        <tr>
            <td>⚡ RAM Read</td>
            <td><span class="badge badge-green">100 ns</span></td>
            <td>চা বানানো (1.5 min)</td>
            <td>তোমার কম্পিউটারের RAM</td>
        </tr>
        <tr>
            <td>💾 SSD Read</td>
            <td><span class="badge badge-blue">100 μs</span></td>
            <td>১ দিন ৩ ঘণ্টা</td>
            <td>SSD হার্ড ড্রাইভ</td>
        </tr>
        <tr>
            <td>💿 HDD Read</td>
            <td><span class="badge badge-yellow">10 ms</span></td>
            <td>প্রায় ২ সপ্তাহ</td>
            <td>পুরানো হার্ড ড্রাইভ</td>
        </tr>
        <tr>
            <td>🌐 Same City</td>
            <td><span class="badge badge-yellow">1 ms</span></td>
            <td>শহরের মধ্যে</td>
            <td>ঢাকা → ঢাকা</td>
        </tr>
        <tr>
            <td>🌍 Cross Country</td>
            <td><span class="badge badge-red">150 ms</span></td>
            <td>৯.৫ বছর!</td>
            <td>ঢাকা → আমেরিকা</td>
        </tr>
    </table>

    <div class="info-box tip">
        <div class="info-icon">💡</div>
        <div class="info-content">
            <div class="info-title">মনে রাখার টিপস</div>
            <p>Cache ব্যবহার করো → ১০০ গুণ দ্রুত! Database এর পরিবর্তে Cache থেকে ডাটা দিলে Response Time নাটকীয়ভাবে কমে। <strong>L1 Cache > RAM > SSD > HDD > Network</strong> — এই ক্রমে গতি কমে।</p>
        </div>
    </div>

    <!-- RPS Estimation -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📊 RPS Estimation (Twitter উদাহরণ)</h3>

    <div class="flow-container">
        <div class="flow-title">Twitter এর হিসাব — ৩০ কোটি DAU</div>
        <div class="flow-row">
            <div class="flow-box">
                <div class="fb-icon">👥</div>
                <div class="fb-label">DAU</div>
                <div class="fb-sub">300 Million</div>
            </div>
            <div class="flow-arrow">×</div>
            <div class="flow-box">
                <div class="fb-icon">📱</div>
                <div class="fb-label">দৈনিক Read</div>
                <div class="fb-sub">20 tweets</div>
            </div>
            <div class="flow-arrow">÷</div>
            <div class="flow-box">
                <div class="fb-icon">⏰</div>
                <div class="fb-label">দিনের সেকেন্ড</div>
                <div class="fb-sub">86,400</div>
            </div>
            <div class="flow-arrow">=</div>
            <div class="flow-box">
                <div class="fb-icon">⚡</div>
                <div class="fb-label">Read RPS</div>
                <div class="fb-sub">~70,000/sec</div>
            </div>
        </div>
    </div>

    <!-- Availability Nines -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Availability — "Nines" বোঝো</h3>

    <div class="algo-container">
        <div class="algo-title">বছরে কতক্ষণ বন্ধ থাকবে?</div>
        <div class="nines-table">
            <div class="nines-row">
                <div class="nines-percent">90%</div>
                <div class="nines-bar-bg"><div class="nines-bar-fill" style="width:10%; background: #ff4444;"></div></div>
                <div class="nines-downtime">😰 36.5 দিন বন্ধ</div>
            </div>
            <div class="nines-row">
                <div class="nines-percent">99%</div>
                <div class="nines-bar-bg"><div class="nines-bar-fill" style="width:40%; background: #ff8c00;"></div></div>
                <div class="nines-downtime">😟 3.65 দিন বন্ধ</div>
            </div>
            <div class="nines-row">
                <div class="nines-percent">99.9%</div>
                <div class="nines-bar-bg"><div class="nines-bar-fill" style="width:65%; background: #ffd700;"></div></div>
                <div class="nines-downtime">😐 8.76 ঘণ্টা বন্ধ</div>
            </div>
            <div class="nines-row">
                <div class="nines-percent">99.99%</div>
                <div class="nines-bar-bg"><div class="nines-bar-fill" style="width:85%;"></div></div>
                <div class="nines-downtime">😊 52.6 মিনিট বন্ধ</div>
            </div>
            <div class="nines-row">
                <div class="nines-percent">99.999%</div>
                <div class="nines-bar-bg"><div class="nines-bar-fill" style="width:98%;"></div></div>
                <div class="nines-downtime">🌟 5.26 মিনিট বন্ধ</div>
            </div>
        </div>
    </div>

    <!-- Scaling -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Scalability — দুই ধরনের Scaling</h3>
    <div class="two-col">
        <div class="col-box">
            <h4>⬆️ Vertical Scaling (বড় করো)</h4>
            <ul>
                <li>✅ একটা সার্ভারকেই শক্তিশালী করো</li>
                <li>✅ সহজ, কোড বদলাতে হয় না</li>
                <li>✅ ছোট প্রজেক্টের জন্য ভালো</li>
                <li>❌ সীমা আছে (সবচেয়ে বড় সার্ভারেও)</li>
                <li>❌ একটা fail = সব বন্ধ</li>
                <li>💰 ব্যয়বহুল</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>➡️ Horizontal Scaling (বাড়াও)</h4>
            <ul>
                <li>✅ একই রকম সার্ভার যোগ করো</li>
                <li>✅ সীমাহীন বাড়ানো যায়</li>
                <li>✅ একটা fail হলেও বাকিরা চলে</li>
                <li>❌ জটিল সেটআপ</li>
                <li>❌ Load Balancer লাগে</li>
                <li>✅ সাশ্রয়ী (ছোট ছোট সার্ভার)</li>
            </ul>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 3: NODE.JS
══════════════════════════════════════════════════ -->
<div class="module-section" id="module3">
    <div class="module-header">
        <div class="module-number-badge">MODULE 03</div>
        <h2 class="module-title">🟢 Node.js API Development</h2>
        <p class="module-subtitle">Backend Development — Express থেকে Microservices পর্যন্ত</p>
    </div>

    <!-- Node.js Basics -->
    <h3 class="subsection-title">🟢 Node.js কী?</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🌐</div>
            <div class="card-title">Browser JS vs Node.js</div>
            <div class="card-desc">Browser JS = শুধু ওয়েবপেজে চলে। Node.js = Server এ চলে। File পড়তে পারে, Database কানেক্ট করতে পারে, API বানাতে পারে!</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🔄</div>
            <div class="card-title">Event Loop</div>
            <div class="card-desc">Node.js এর হৃদয়। একসাথে অনেক কাজ সামলায়। Non-blocking = একটা কাজ শেষ না হলেও অন্য কাজ শুরু করে!</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📦</div>
            <div class="card-title">NPM</div>
            <div class="card-desc">Node Package Manager। হাজারো ready-made package পাওয়া যায়। express, axios, mongoose — সব NPM দিয়ে install করো।</div>
        </div>
    </div>

    <!-- Async Programming -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔄 Async Programming — ৩টা পদ্ধতি</h3>

    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-dot">1️⃣</div>
            <div class="timeline-content">
                <h4>😵 Callback — পুরানো পদ্ধতি</h4>
                <p>কাজ শেষ হলে function call করো। সমস্যা: Callback Hell — একের ভেতরে আরেক, ভেতরে আরেক। "Christmas Tree Pattern" বা "Pyramid of Doom" নামে পরিচিত।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">2️⃣</div>
            <div class="timeline-content">
                <h4>😐 Promise — মাঝারি পদ্ধতি</h4>
                <p>তিনটা অবস্থা: Pending (অপেক্ষা), Resolved (সফল), Rejected (ব্যর্থ)। .then() .catch() দিয়ে chain করা যায়। Callback Hell থেকে মুক্তি!</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">3️⃣</div>
            <div class="timeline-content">
                <h4>😊 Async/Await — সেরা পদ্ধতি</h4>
                <p>সবচেয়ে সহজ ও পরিষ্কার। Async function এর ভেতরে await দিয়ে অপেক্ষা করো। Synchronous কোডের মতো দেখায় কিন্তু Async ভাবে কাজ করে!</p>
            </div>
        </div>
    </div>

    <!-- Express API -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🚀 Express.js — HTTP Methods</h3>

    <table class="comparison-table">
        <tr>
            <th>Method</th>
            <th>কাজ</th>
            <th>উদাহরণ URL</th>
            <th>HTTP Code</th>
            <th>বাস্তব উদাহরণ</th>
        </tr>
        <tr>
            <td><span class="badge badge-green">GET</span></td>
            <td>পড়া (Read)</td>
            <td>/api/users</td>
            <td>200 OK</td>
            <td>ব্যবহারকারীর তালিকা দেখা</td>
        </tr>
        <tr>
            <td><span class="badge badge-blue">POST</span></td>
            <td>তৈরি (Create)</td>
            <td>/api/users</td>
            <td>201 Created</td>
            <td>নতুন অ্যাকাউন্ট তৈরি</td>
        </tr>
        <tr>
            <td><span class="badge badge-yellow">PUT</span></td>
            <td>পুরো আপডেট</td>
            <td>/api/users/1</td>
            <td>200 OK</td>
            <td>সম্পূর্ণ প্রোফাইল আপডেট</td>
        </tr>
        <tr>
            <td><span class="badge badge-yellow">PATCH</span></td>
            <td>আংশিক আপডেট</td>
            <td>/api/users/1</td>
            <td>200 OK</td>
            <td>শুধু নাম পরিবর্তন</td>
        </tr>
        <tr>
            <td><span class="badge badge-red">DELETE</span></td>
            <td>মুছা (Delete)</td>
            <td>/api/users/1</td>
            <td>200 OK</td>
            <td>অ্যাকাউন্ট মুছে ফেলা</td>
        </tr>
    </table>

    <!-- Enterprise Architecture -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ Enterprise Node.js Architecture</h3>

    <div class="arch-diagram">
        <div class="arch-title">Layer Architecture — ধাপে ধাপে</div>
        <div class="arch-layer highlight">
            <div class="arch-node">
                <div class="node-icon">👤</div>
                <div class="node-label">Client Request</div>
                <div class="node-sub">HTTP/HTTPS</div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node">
                <div class="node-icon">🛣️</div>
                <div class="node-label">Routes Layer</div>
                <div class="node-sub">URL → Controller</div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node">
                <div class="node-icon">🎮</div>
                <div class="node-label">Controller Layer</div>
                <div class="node-sub">Request/Response</div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node">
                <div class="node-icon">⚙️</div>
                <div class="node-label">Service Layer</div>
                <div class="node-sub">Business Logic</div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node">
                <div class="node-icon">🗄️</div>
                <div class="node-label">Repository Layer</div>
                <div class="node-sub">Database Query</div>
            </div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer highlight">
            <div class="arch-node">
                <div class="node-icon">💾</div>
                <div class="node-label">Database</div>
                <div class="node-sub">PostgreSQL/MongoDB</div>
            </div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 4: RATE LIMITING
══════════════════════════════════════════════════ -->
<div class="module-section" id="module4">
    <div class="module-header">
        <div class="module-number-badge">MODULE 04</div>
        <h2 class="module-title">🚦 Rate Limit Module</h2>
        <p class="module-subtitle">সিস্টেম সুরক্ষা — DDoS থেকে Business Model পর্যন্ত</p>
    </div>

    <!-- Why Rate Limit -->
    <h3 class="subsection-title">🤔 কেন Rate Limit দরকার?</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🛡️</div>
            <div class="card-title">DDoS Attack রোধ</div>
            <div class="card-desc">হাজারো ভুয়া request পাঠিয়ে সার্ভার বন্ধ করার চেষ্টা। Rate Limit → সর্বোচ্চ ১০০! → সার্ভার নিরাপদ।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">💰</div>
            <div class="card-title">Resource সাশ্রয়</div>
            <div class="card-desc">প্রতিটা request মানে CPU + RAM + DB খরচ। অতিরিক্ত request মানে অতিরিক্ত বিল। Rate Limit = খরচ নিয়ন্ত্রণ।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">⚖️</div>
            <div class="card-title">সমান সুযোগ</div>
            <div class="card-desc">১ জন সব resource নিয়ে নিলে বাকিরা ব্যবহার করতে পারবে না। Rate Limit নিশ্চিত করে সবাই সমান সুযোগ পায়।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">🔐</div>
            <div class="card-title">Brute Force রোধ</div>
            <div class="card-desc">হাজারবার পাসওয়ার্ড চেষ্টা করা থেকে রক্ষা। ৫ বার ভুল = ১ ঘণ্টা block!</div>
        </div>
        <div class="concept-card pink">
            <div class="card-icon">📊</div>
            <div class="card-title">Business Model</div>
            <div class="card-desc">Free: ১০০/দিন, Basic: ১,০০০/দিন, Premium: ১০,০০০/দিন। Rate Limit = আয়ের হাতিয়ার!</div>
        </div>
        <div class="concept-card yellow">
            <div class="card-icon">🌐</div>
            <div class="card-title">বাস্তব উদাহরণ</div>
            <div class="card-desc">Twitter: ১৫ মিনিটে ১৫০ request। GitHub: ১ ঘণ্টায় ৫,০০০। OpenAI: ১ মিনিটে ৬০। Google Maps: দিনে ২৫,০০০।</div>
        </div>
    </div>

    <!-- Algorithms -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔢 Rate Limiting Algorithms</h3>

    <div class="algo-container">
        <div class="algo-title">🪣 Token Bucket Algorithm</div>
        <div style="display:flex; gap:30px; align-items:center; flex-wrap:wrap;">
            <div style="text-align:center;">
                <div style="background:#1a1a1a; border:2px solid #00d4ff; border-radius:0 0 16px 16px; border-top:none; width:100px; height:120px; position:relative; margin:0 auto;">
                    <div style="position:absolute; bottom:0; left:0; right:0; background:linear-gradient(180deg,#00d4ff66,#00d4ff); height:70%; border-radius:0 0 14px 14px;"></div>
                    <div style="position:absolute; top:50%; left:50%; transform:translate(-50%,-50%); font-size:28px; font-weight:900; color:white; z-index:1;">7</div>
                </div>
                <div style="margin-top:10px; font-size:13px; color:#666;">বালতিতে ৭টা টোকেন</div>
            </div>
            <div style="flex:1; min-width:200px;">
                <div style="margin-bottom:16px; padding:12px; background:#141414; border-radius:8px;">
                    <div style="font-size:13px; color:#00d4ff; font-weight:700; margin-bottom:6px;">নিয়ম:</div>
                    <div style="font-size:13px; color:#aaa;">• সর্বোচ্চ ১০টা টোকেন ধরে</div>
                    <div style="font-size:13px; color:#aaa;">• প্রতি সেকেন্ডে ২টা যোগ হয়</div>
                    <div style="font-size:13px; color:#aaa;">• প্রতি request এ ১টা খরচ হয়</div>
                    <div style="font-size:13px; color:#aaa;">• খালি হলে request BLOCK 🛑</div>
                </div>
                <div style="padding:12px; background:#141414; border-radius:8px;">
                    <div style="font-size:13px; color:#00ff88; font-weight:700; margin-bottom:6px;">সুবিধা:</div>
                    <div style="font-size:13px; color:#aaa;">✅ Burst allow করে, ✅ সহজ implement</div>
                    <div style="font-size:13px; color:#ff8888; font-weight:700; margin-top:8px; margin-bottom:6px;">অসুবিধা:</div>
                    <div style="font-size:13px; color:#aaa;">❌ Memory বেশি লাগে (প্রতি user এর জন্য)</div>
                </div>
            </div>
        </div>
    </div>

    <table class="comparison-table" style="margin-top:30px;">
        <tr>
            <th>Algorithm</th>
            <th>কীভাবে কাজ করে</th>
            <th>Burst?</th>
            <th>Memory</th>
            <th>সেরা ব্যবহার</th>
        </tr>
        <tr>
            <td>🪣 Token Bucket</td>
            <td>বালতিতে টোকেন, খালি হলে block</td>
            <td><span class="badge badge-green">✅ হ্যাঁ</span></td>
            <td>কম</td>
            <td>API Throttling</td>
        </tr>
        <tr>
            <td>🚰 Leaky Bucket</td>
            <td>ধীরে ধীরে চুইয়ে পড়ে</td>
            <td><span class="badge badge-red">❌ না</span></td>
            <td>কম</td>
            <td>Traffic Shaping</td>
        </tr>
        <tr>
            <td>📅 Fixed Window</td>
            <td>নির্দিষ্ট সময়ে count রিসেট</td>
            <td><span class="badge badge-yellow">⚠️ Window শেষে</span></td>
            <td>সবচেয়ে কম</td>
            <td>Simple Rate Limit</td>
        </tr>
        <tr>
            <td>🔄 Sliding Window</td>
            <td>সবসময় "গত X সেকেন্ড" দেখে</td>
            <td><span class="badge badge-red">❌ না</span></td>
            <td>বেশি</td>
            <td>Production (সেরা!)</td>
        </tr>
    </table>

    <div class="info-box tip">
        <div class="info-icon">🏆</div>
        <div class="info-content">
            <div class="info-title">Production এ সেরা পছন্দ</div>
            <p><strong>Sliding Window Counter + Redis</strong> = সবচেয়ে ভালো। Redis এ সব সার্ভার share করে, Sliding Window সবচেয়ে নির্ভুল। Nginx দিয়ে প্রথম স্তরে সুরক্ষা দাও, তারপর Application Level এ। এই দুই স্তরের সুরক্ষা = Defense in Depth!</p>
        </div>
    </div>

    <!-- Microservice Rate Limit -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔀 Microservice Rate Limit Architecture</h3>

    <div class="arch-diagram">
        <div class="arch-title">স্তরে স্তরে Rate Limit সুরক্ষা</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">👤</div><div class="node-label">User Request</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">🌐</div><div class="node-label">Nginx</div><div class="node-sub">Layer 1: IP-based Limit</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer highlight">
            <div class="arch-node"><div class="node-icon">🚪</div><div class="node-label">API Gateway</div><div class="node-sub">Layer 2: Global Limit</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">⚙️</div><div class="node-label">Service A</div><div class="node-sub">Layer 3: Service Limit</div></div>
            <div class="arch-node"><div class="node-icon">⚙️</div><div class="node-label">Service B</div><div class="node-sub">Layer 3: Service Limit</div></div>
        </div>
        <div class="arch-arrow-down">↓</div>
        <div class="arch-layer">
            <div class="arch-node"><div class="node-icon">📊</div><div class="node-label">Redis</div><div class="node-sub">Shared Counter Store</div></div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 6: AWS
══════════════════════════════════════════════════ -->
<div class="module-section" id="module6">
    <div class="module-header">
        <div class="module-number-badge">MODULE 06</div>
        <h2 class="module-title">☁️ AWS For Scaling</h2>
        <p class="module-subtitle">Cloud Infrastructure — VPC থেকে Auto Scaling পর্যন্ত</p>
    </div>

    <!-- AWS Intro -->
    <h3 class="subsection-title">☁️ AWS কী?</h3>

    <div class="info-box info">
        <div class="info-icon">☁️</div>
        <div class="info-content">
            <div class="info-title">AWS = ইন্টারনেটে ভাড়া দেওয়া কম্পিউটার ও সেবা</div>
            <p>নিজের সার্ভার কেনা = বাড়ি বানানো (লক্ষ টাকা, সময় বেশি)। AWS ব্যবহার = বাড়ি ভাড়া নেওয়া (যতটুকু ব্যবহার ততটুকু বিল, যেকোনো সময় বড় করা যায়)। Pay-as-you-go মডেল।</p>
        </div>
    </div>

    <!-- AWS Services -->
    <table class="comparison-table">
        <tr>
            <th>AWS সেবা</th>
            <th>বাড়ির সাথে তুলনা</th>
            <th>কাজ</th>
            <th>উদাহরণ</th>
        </tr>
        <tr><td>🏗️ VPC</td><td>জমি/প্লট</td><td>নিজের নেটওয়ার্ক</td><td>প্রাইভেট নেটওয়ার্ক</td></tr>
        <tr><td>🖥️ EC2</td><td>ঘর</td><td>ভার্চুয়াল সার্ভার</td><td>Web/App Server</td></tr>
        <tr><td>🚪 Security Group</td><td>দরজা</td><td>Firewall</td><td>Port 80 allow করো</td></tr>
        <tr><td>📦 S3</td><td>গুদাম</td><td>ফাইল স্টোরেজ</td><td>ছবি, ভিডিও, Backup</td></tr>
        <tr><td>🗄️ RDS</td><td>আলমারি</td><td>ডাটাবেস</td><td>PostgreSQL, MySQL</td></tr>
        <tr><td>⚖️ ELB</td><td>টোকেন সিস্টেম</td><td>Load Balancer</td><td>Traffic ভাগ করা</td></tr>
        <tr><td>📈 Auto Scaling</td><td>বড় করা</td><td>স্বয়ংক্রিয় বৃদ্ধি</td><td>Traffic বাড়লে Server বাড়াও</td></tr>
        <tr><td>⚡ ElastiCache</td><td>টেবিলের উপর</td><td>Cache</td><td>Redis, Memcached</td></tr>
    </table>

    <!-- VPC Design -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🏗️ VPC Design</h3>

    <div class="arch-diagram">
        <div class="arch-title">🌐 সম্পূর্ণ VPC Architecture</div>
        <div style="font-size:13px; color:#666; margin-bottom:20px;">Internet → IGW → Public Subnet → Private Subnet → DB Subnet</div>

        <div style="border:2px dashed #00d4ff44; border-radius:16px; padding:20px; margin:10px 0;">
            <div style="font-size:12px; color:#00d4ff; font-weight:700; margin-bottom:15px;">🌐 PUBLIC SUBNET (বৈঠকখানা — অতিথি আসতে পারে)</div>
            <div style="display:flex; gap:15px; justify-content:center; flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">⚖️</div><div class="node-label">ALB</div><div class="node-sub">Load Balancer</div></div>
                <div class="arch-node"><div class="node-icon">🌐</div><div class="node-label">NAT Gateway</div><div class="node-sub">Internet Access</div></div>
                <div class="arch-node"><div class="node-icon">🔑</div><div class="node-label">Bastion Host</div><div class="node-sub">SSH Access</div></div>
            </div>
        </div>

        <div class="arch-arrow-down">↓</div>

        <div style="border:2px dashed #00ff8844; border-radius:16px; padding:20px; margin:10px 0;">
            <div style="font-size:12px; color:#00ff88; font-weight:700; margin-bottom:15px;">🔒 PRIVATE SUBNET (শোবার ঘর — শুধু বাড়ির লোক)</div>
            <div style="display:flex; gap:15px; justify-content:center; flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">🖥️</div><div class="node-label">EC2 Server</div><div class="node-sub">App Server 1</div></div>
                <div class="arch-node"><div class="node-icon">🖥️</div><div class="node-label">EC2 Server</div><div class="node-sub">App Server 2</div></div>
            </div>
        </div>

        <div class="arch-arrow-down">↓</div>

        <div style="border:2px dashed #ff8c0044; border-radius:16px; padding:20px; margin:10px 0;">
            <div style="font-size:12px; color:#ff8c00; font-weight:700; margin-bottom:15px;">🔒🔒 DB SUBNET (সিন্দুক — সবচেয়ে সুরক্ষিত)</div>
            <div style="display:flex; gap:15px; justify-content:center; flex-wrap:wrap;">
                <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">RDS Primary</div><div class="node-sub">AZ-a</div></div>
                <div class="arch-node"><div class="node-icon">💾</div><div class="node-label">RDS Standby</div><div class="node-sub">AZ-b (Auto Sync)</div></div>
            </div>
        </div>
    </div>

    <!-- Storage Comparison -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📦 AWS Storage তুলনা</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🪣</div>
            <div class="card-title">S3 — গুদামঘর</div>
            <div class="card-desc">Object Storage। ছবি, ভিডিও, Backup রাখো। অসীম জায়গা। ১১টা নয়ন Durability। সস্তা ($0.023/GB/মাস)। EC2 ছাড়াও কাজ করে।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">💿</div>
            <div class="card-title">EBS — হার্ডডিস্ক</div>
            <div class="card-desc">Block Storage। EC2 এর সাথে লাগানো ডিস্ক। দ্রুত। OS install করা যায়। Database এর জন্য ভালো। কিন্তু একটা EC2 এরই।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">📁</div>
            <div class="card-title">EFS — Shared Drive</div>
            <div class="card-desc">File Storage। অনেক EC2 একসাথে ব্যবহার করতে পারে। Auto scaling। অফিসের shared network drive এর মতো। একটু ধীর কিন্তু flexible।</div>
        </div>
    </div>

    <!-- Auto Scaling -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📈 Auto Scaling Group</h3>

    <div class="flow-container">
        <div class="flow-title">Auto Scaling কীভাবে কাজ করে</div>
        <div class="flow-row">
            <div class="flow-box">
                <div class="fb-icon">📊</div>
                <div class="fb-label">CloudWatch</div>
                <div class="fb-sub">CPU > 70% দেখে</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">🔔</div>
                <div class="fb-label">Alert!</div>
                <div class="fb-sub">Alarm trigger</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">📋</div>
                <div class="fb-label">ASG Policy</div>
                <div class="fb-sub">+2 instances</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">🖥️🖥️</div>
                <div class="fb-label">নতুন EC2</div>
                <div class="fb-sub">Launch!</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">⚖️</div>
                <div class="fb-label">Load Balancer</div>
                <div class="fb-sub">Register করো</div>
            </div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 7: DOCKER
══════════════════════════════════════════════════ -->
<div class="module-section" id="module7">
    <div class="module-header">
        <div class="module-number-badge">MODULE 07</div>
        <h2 class="module-title">🐳 Docker For Backend Engineers</h2>
        <p class="module-subtitle">Container থেকে Microservice Deployment</p>
    </div>

    <!-- Docker Basics -->
    <h3 class="subsection-title">🐳 Docker এর ৩টা মূল জিনিস</h3>

    <div class="steps-container">
        <div class="step-item">
            <div class="step-number">1</div>
            <div class="step-content">
                <h4>📝 Dockerfile — রেসিপি</h4>
                <p>Container বানানোর নির্দেশিকা। "কী কী লাগবে, কীভাবে বানাবে" — বিরিয়ানির রেসিপির মতো। FROM, RUN, COPY, CMD কমান্ড দিয়ে লেখা হয়।</p>
            </div>
        </div>
        <div class="step-item">
            <div class="step-number">2</div>
            <div class="step-content">
                <h4>📸 Image — ছাঁচ/টেমপ্লেট</h4>
                <p>Dockerfile থেকে তৈরি। Read-only। একটা Image থেকে অনেক Container বানানো যায়। Docker Hub এ হাজারো ready Image আছে।</p>
            </div>
        </div>
        <div class="step-item">
            <div class="step-number">3</div>
            <div class="step-content">
                <h4>📦 Container — চলমান অ্যাপ</h4>
                <p>Image থেকে তৈরি, চলতে থাকে। বিরিয়ানির ছাঁচ থেকে রান্না করা বিরিয়ানির মতো। প্রতিটা Container আলাদা, বিচ্ছিন্ন।</p>
            </div>
        </div>
    </div>

    <!-- VM vs Docker -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🆚 VM vs Docker</h3>

    <div class="two-col">
        <div class="col-box">
            <h4>🖥️ Virtual Machine</h4>
            <ul>
                <li>❌ প্রতিটায় আলাদা OS</li>
                <li>❌ ভারী (GB সাইজ)</li>
                <li>❌ ধীর (মিনিট লাগে শুরু হতে)</li>
                <li>✅ সম্পূর্ণ আলাদা পরিবেশ</li>
                <li>✅ বেশি নিরাপদ</li>
                <li>💰 বেশি Resource খরচ</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>🐳 Docker Container</h4>
            <ul>
                <li>✅ OS share করে</li>
                <li>✅ হালকা (MB সাইজ)</li>
                <li>✅ দ্রুত (সেকেন্ডে চালু)</li>
                <li>✅ Portable (সব জায়গায় একই)</li>
                <li>✅ Easy scaling</li>
                <li>💰 কম Resource খরচ</li>
            </ul>
        </div>
    </div>

    <!-- Dockerfile Best Practices -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">✅ Dockerfile Best Practices</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🪶</div>
            <div class="card-title">Alpine Image ব্যবহার করো</div>
            <div class="card-desc">node:18 = 900MB। node:18-alpine = 120MB। Alpine = ছোট Linux। Image ছোট হলে Deploy দ্রুত, খরচ কম।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">📦</div>
            <div class="card-title">Layer Cache</div>
            <div class="card-desc">কম বদলানো জিনিস আগে। package.json আগে COPY → npm install → তারপর src। Cache কাজ করলে Build দ্রুত।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🏗️</div>
            <div class="card-title">Multi-stage Build</div>
            <div class="card-desc">Build করো একটা stage এ, চালাও আরেকটায়। Build tools Image এ থাকে না। Production Image ছোট ও নিরাপদ।</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">👤</div>
            <div class="card-title">Non-root User</div>
            <div class="card-desc">Root user = হ্যাকারের স্বপ্ন! Non-root user তৈরি করো ও ব্যবহার করো। Security best practice।</div>
        </div>
    </div>

    <!-- MySQL Replication -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🐬 MySQL Replication Architecture</h3>

    <div class="arch-diagram">
        <div class="arch-title">Master-Slave Replication</div>
        <div style="display:flex; gap:30px; justify-content:center; align-items:flex-start; flex-wrap:wrap;">
            <div style="text-align:center;">
                <div style="font-size:36px;">✍️</div>
                <div style="font-size:12px; color:#aaa; margin-bottom:10px;">Write Only</div>
                <div style="background:#1a2a3a; border:2px solid #00d4ff; border-radius:12px; padding:20px;">
                    <div style="font-size:20px;">🐬</div>
                    <div style="font-size:14px; font-weight:700; color:#00d4ff;">MASTER</div>
                    <div style="font-size:12px; color:#666;">Port: 3306</div>
                    <div style="font-size:11px; color:#555; margin-top:6px;">Binary Log</div>
                </div>
            </div>
            <div style="display:flex; flex-direction:column; align-items:center; justify-content:center; gap:20px; padding-top:50px;">
                <div style="font-size:13px; color:#00d4ff;">────── Sync ──────></div>
                <div style="font-size:13px; color:#00d4ff;">────── Sync ──────></div>
            </div>
            <div style="display:flex; flex-direction:column; gap:15px;">
                <div style="text-align:center;">
                    <div style="font-size:12px; color:#aaa; margin-bottom:6px;">📖 Read Only</div>
                    <div style="background:#1a3a1a; border:2px solid #00ff88; border-radius:12px; padding:15px;">
                        <div style="font-size:16px;">🐬</div>
                        <div style="font-size:13px; font-weight:700; color:#00ff88;">REPLICA 1</div>
                        <div style="font-size:11px; color:#666;">Port: 3307</div>
                    </div>
                </div>
                <div style="text-align:center;">
                    <div style="background:#1a3a1a; border:2px solid #00ff88; border-radius:12px; padding:15px;">
                        <div style="font-size:16px;">🐬</div>
                        <div style="font-size:13px; font-weight:700; color:#00ff88;">REPLICA 2</div>
                        <div style="font-size:11px; color:#666;">Port: 3308</div>
                    </div>
                </div>
            </div>
        </div>
        <div style="margin-top:20px; padding:16px; background:#141414; border-radius:10px; font-size:13px; color:#aaa; text-align:left; max-width:500px; margin-left:auto; margin-right:auto;">
            <div style="color:#00d4ff; font-weight:700; margin-bottom:8px;">📊 Read/Write Split:</div>
            <div>✍️ INSERT/UPDATE/DELETE → Master (নিরাপদ লেখা)</div>
            <div>📖 SELECT → Replica 1/2 (load balance)</div>
            <div>⚡ পড়ার চাপ ভাগ হয় → আরো দ্রুত!</div>
        </div>
    </div>

    <!-- Kafka -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">📨 Kafka — Message Streaming</h3>

    <div class="flow-container">
        <div class="flow-title">📨 Kafka Message Flow</div>
        <div class="flow-row">
            <div class="flow-box">
                <div class="fb-icon">📝</div>
                <div class="fb-label">Producer</div>
                <div class="fb-sub">Order Service</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">📊</div>
                <div class="fb-label">Topic: orders</div>
                <div class="fb-sub">Partition 0,1,2</div>
            </div>
            <div class="flow-arrow">→</div>
            <div class="flow-box">
                <div class="fb-icon">📖</div>
                <div class="fb-label">Consumer Group</div>
                <div class="fb-sub">Email, SMS, Analytics</div>
            </div>
        </div>
        <div style="margin-top:20px; display:flex; gap:15px; justify-content:center; flex-wrap:wrap;">
            <div style="background:#141414; border:1px solid #2a2a2a; border-radius:8px; padding:12px 20px; text-align:center;">
                <div style="font-size:20px;">📧</div>
                <div style="font-size:12px; color:#00d4ff;">Email Service</div>
            </div>
            <div style="background:#141414; border:1px solid #2a2a2a; border-radius:8px; padding:12px 20px; text-align:center;">
                <div style="font-size:20px;">📱</div>
                <div style="font-size:12px; color:#00d4ff;">SMS Service</div>
            </div>
            <div style="background:#141414; border:1px solid #2a2a2a; border-radius:8px; padding:12px 20px; text-align:center;">
                <div style="font-size:20px;">📊</div>
                <div style="font-size:12px; color:#00d4ff;">Analytics</div>
            </div>
            <div style="background:#141414; border:1px solid #2a2a2a; border-radius:8px; padding:12px 20px; text-align:center;">
                <div style="font-size:20px;">📦</div>
                <div style="font-size:12px; color:#00d4ff;">Inventory</div>
            </div>
        </div>
        <div style="margin-top:16px; font-size:13px; color:#666; text-align:center;">একটা event → অনেক service একসাথে কাজ করে! Decoupled Architecture 🎉</div>
    </div>

    <!-- Layer 4 vs 7 -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">⚖️ Layer 4 vs Layer 7 Load Balancer</h3>

    <div class="two-col">
        <div class="col-box">
            <h4>📦 Layer 4 (TCP/UDP)</h4>
            <ul>
                <li>✅ শুধু IP + Port দেখে</li>
                <li>✅ অনেক দ্রুত</li>
                <li>✅ কম CPU ব্যবহার</li>
                <li>❌ URL দেখতে পারে না</li>
                <li>❌ Smart routing নেই</li>
                <li>🏠 ডাক বিভাগের সোর্টার</li>
            </ul>
        </div>
        <div class="col-box">
            <h4>🧠 Layer 7 (HTTP/HTTPS)</h4>
            <ul>
                <li>✅ URL, Header, Cookie দেখে</li>
                <li>✅ Smart routing করে</li>
                <li>✅ SSL termination</li>
                <li>✅ Caching করতে পারে</li>
                <li>❌ একটু ধীর</li>
                <li>🏠 রিসেপশনিস্ট (উদ্দেশ্য বোঝে)</li>
            </ul>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     MODULE 8: MICROSERVICE NETWORKING
══════════════════════════════════════════════════ -->
<div class="module-section" id="module8">
    <div class="module-header">
        <div class="module-number-badge">MODULE 08</div>
        <h2 class="module-title">🌐 Microservice Networking</h2>
        <p class="module-subtitle">Linux Networking — Namespace থেকে Bridge পর্যন্ত</p>
    </div>

    <!-- Linux Networking -->
    <h3 class="subsection-title">🐧 Linux Networking মূল ধারণা</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🔌</div>
            <div class="card-title">Network Interface</div>
            <div class="card-desc">eth0 = ইন্টারনেট কার্ড। lo = নিজের সাথে কথা বলা। wlan0 = WiFi। প্রতিটার আলাদা IP আছে।</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🗺️</div>
            <div class="card-title">Routing Table</div>
            <div class="card-desc">ট্রাফিক কোথায় যাবে তার মানচিত্র। Default Route = সব অজানা ট্রাফিক Gateway এ যাবে।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🛡️</div>
            <div class="card-title">iptables</div>
            <div class="card-desc">Linux Firewall। Port allow/block করো। NAT করো। Docker ও iptables ব্যবহার করে!</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">📡</div>
            <div class="card-title">মূল কমান্ড</div>
            <div class="card-desc">ip addr (interface দেখো), ip route (route দেখো), ss -tuln (connection দেখো), ping (connectivity test)।</div>
        </div>
    </div>

    <!-- Network Namespace -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔲 Network Namespace</h3>

    <div class="info-box info">
        <div class="info-icon">🏢</div>
        <div class="info-content">
            <div class="info-title">Namespace = অফিস বিল্ডিংয়ের আলাদা ফ্লোর</div>
            <p>প্রতিটা ফ্লোরের নিজস্ব ফোন নম্বর (IP), নেটওয়ার্ক, নিরাপত্তা। এক ফ্লোরের কর্মীরা অন্য ফ্লোরের নেটওয়ার্ক দেখতে পায় না। Docker Container = আলাদা Namespace!</p>
        </div>
    </div>

    <div class="network-diagram">
        <div style="text-align:center; font-size:18px; font-weight:800; color:#00d4ff; margin-bottom:30px;">Network Namespace Architecture</div>
        <div style="display:flex; gap:20px; justify-content:center; flex-wrap:wrap;">
            <div class="namespace-box">
                <div class="namespace-title">Host Namespace</div>
                <div style="font-size:20px; margin:10px 0;">🖥️</div>
                <div class="namespace-ip">eth0: 192.168.1.100</div>
                <div class="namespace-ip">lo: 127.0.0.1</div>
            </div>
            <div class="namespace-box">
                <div class="namespace-title">ns_red (Container A)</div>
                <div style="font-size:20px; margin:10px 0;">📦</div>
                <div class="namespace-ip">eth0: 10.0.0.1</div>
                <div class="namespace-ip">lo: 127.0.0.1</div>
                <div style="font-size:11px; color:#555; margin-top:6px;">আলাদা নেটওয়ার্ক!</div>
            </div>
            <div class="namespace-box">
                <div class="namespace-title">ns_blue (Container B)</div>
                <div style="font-size:20px; margin:10px 0;">📦</div>
                <div class="namespace-ip">eth0: 10.0.0.2</div>
                <div class="namespace-ip">lo: 127.0.0.1</div>
                <div style="font-size:11px; color:#555; margin-top:6px;">আলাদা নেটওয়ার্ক!</div>
            </div>
        </div>
    </div>

    <!-- Connection Methods -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🔌 Namespace সংযোগের পদ্ধতি</h3>

    <div class="steps-container">
        <div class="step-item">
            <div class="step-number">1</div>
            <div class="step-content">
                <h4>veth Pair — দুই মাথার তার</h4>
                <p>Virtual Ethernet Cable। এক মাথা Host এ, অন্য মাথা Namespace এ। দুটো টিনের কৌটা সুতো দিয়ে যুক্ত টেলিফোনের মতো! Host ↔ Namespace সরাসরি কথা বলতে পারে।</p>
            </div>
        </div>
        <div class="step-item">
            <div class="step-number">2</div>
            <div class="step-content">
                <h4>Bridge — Virtual Switch</h4>
                <p>অনেক Namespace কে একটা Bridge এ যুক্ত করো। Bridge = Virtual Switch। সব Namespace → Bridge → সবাই সবার সাথে কথা বলতে পারে! PABX Exchange এর মতো।</p>
            </div>
        </div>
        <div class="step-item">
            <div class="step-number">3</div>
            <div class="step-content">
                <h4>Bridge এ IP + iptables NAT</h4>
                <p>Bridge এ IP দাও → Host ও সব Namespace এ যেতে পারে। iptables NAT → Namespace → Internet যেতে পারে। এটাই Docker networking এর ভিত্তি!</p>
            </div>
        </div>
    </div>

    <!-- Full Architecture -->
    <div class="network-diagram">
        <div style="text-align:center; font-size:18px; font-weight:800; color:#00d4ff; margin-bottom:30px;">🌐 সম্পূর্ণ Bridge Architecture</div>
        <div style="text-align:center; margin-bottom:20px;">
            <div style="font-size:13px; color:#888;">🌍 Internet</div>
            <div class="veth-line">↕</div>
            <div style="font-size:13px; color:#888;">eth0: 192.168.1.100 (Host)</div>
        </div>
        <div class="veth-line">↕ iptables NAT</div>
        <div style="text-align:center; margin:15px 0;">
            <div class="bridge-box">
                <div class="bridge-label">🌉 Bridge: br0</div>
                <div class="bridge-ip">IP: 192.168.100.1/24</div>
                <div style="font-size:11px; color:#555; margin-top:4px;">Virtual Switch</div>
            </div>
        </div>
        <div class="veth-line">↕ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↕ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↕</div>
        <div style="display:flex; gap:15px; justify-content:center; flex-wrap:wrap; margin-top:10px;">
            <div class="namespace-box">
                <div class="namespace-title">ns_red</div>
                <div style="font-size:16px; margin:6px 0;">🟥</div>
                <div class="namespace-ip">192.168.100.10</div>
                <div class="namespace-ip" style="color:#555;">GW: 100.1</div>
            </div>
            <div class="namespace-box">
                <div class="namespace-title">ns_blue</div>
                <div style="font-size:16px; margin:6px 0;">🟦</div>
                <div class="namespace-ip">192.168.100.20</div>
                <div class="namespace-ip" style="color:#555;">GW: 100.1</div>
            </div>
            <div class="namespace-box">
                <div class="namespace-title">ns_green</div>
                <div style="font-size:16px; margin:6px 0;">🟩</div>
                <div class="namespace-ip">192.168.100.30</div>
                <div class="namespace-ip" style="color:#555;">GW: 100.1</div>
            </div>
        </div>
        <div style="margin-top:20px; padding:16px; background:#141414; border-radius:10px; font-size:13px; text-align:center;">
            <span style="color:#00ff88;">✅</span> Host ↔ সব NS &nbsp;&nbsp;
            <span style="color:#00ff88;">✅</span> NS ↔ NS &nbsp;&nbsp;
            <span style="color:#00ff88;">✅</span> NS → Internet
        </div>
    </div>

    <div class="info-box tip">
        <div class="info-icon">🐳</div>
        <div class="info-content">
            <div class="info-title">Docker এর রহস্য উন্মোচন!</div>
            <p>Docker Container = Linux Namespace + veth Pair + Bridge (docker0) + iptables NAT। docker run চালালে Docker এই সব কাজ স্বয়ংক্রিয়ভাবে করে! এখন তুমি Docker এর ভেতরে কী হয় জানো! 🎉</p>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     SUMMARY
══════════════════════════════════════════════════ -->
<div class="module-section" id="summary" style="background:#080808;">
    <div class="module-header">
        <div class="module-number-badge">সম্পূর্ণ সারসংক্ষেপ</div>
        <h2 class="module-title">🎯 Quick Reference Guide</h2>
        <p class="module-subtitle">সব Module এক জায়গায় — Interview এর জন্য প্রস্তুত হও!</p>
    </div>

    <!-- Master Table -->
    <h3 class="subsection-title">📋 সব Module এক নজরে</h3>

    <table class="comparison-table">
        <tr>
            <th>Module</th>
            <th>মূল বিষয়</th>
            <th>গুরুত্বপূর্ণ ধারণা</th>
            <th>মনে রাখার টিপস</th>
        </tr>
        <tr>
            <td>🏗️ Module 1</td>
            <td>System Design Basics</td>
            <td>CAP Theorem, Consistency, Failure Models</td>
            <td>CAP এ ৩টার মধ্যে ২টা — সবসময়!</td>
        </tr>
        <tr>
            <td>🧮 Module 2</td>
            <td>Mathematics</td>
            <td>RPS = DAU×requests÷86400, Nines</td>
            <td>Peak = Average × 3</td>
        </tr>
        <tr>
            <td>🟢 Module 3</td>
            <td>Node.js API</td>
            <td>Async/Await, Express, PostgreSQL</td>
            <td>Callback→Promise→Async/Await (সহজ থেকে সহজ)</td>
        </tr>
        <tr>
            <td>🚦 Module 4</td>
            <td>Rate Limiting</td>
            <td>Sliding Window + Redis = সেরা</td>
            <td>স্তরে স্তরে সুরক্ষা = Defense in Depth</td>
        </tr>
        <tr>
            <td>☁️ Module 6</td>
            <td>AWS Scaling</td>
            <td>VPC, EC2, RDS, Auto Scaling, ELB</td>
            <td>Public→Private→DB Subnet (নিরাপত্তার স্তর)</td>
        </tr>
        <tr>
            <td>🐳 Module 7</td>
            <td>Docker</td>
            <td>Dockerfile, Compose, MySQL Replication</td>
            <td>Dockerfile→Image→Container (রেসিপি→ছাঁচ→খাবার)</td>
        </tr>
        <tr>
            <td>🌐 Module 8</td>
            <td>Microservice Networking</td>
            <td>Namespace, veth, Bridge, NAT</td>
            <td>Docker = Namespace + veth + Bridge + iptables</td>
        </tr>
    </table>

    <!-- Interview Tips -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">💡 Interview Tips</h3>

    <div class="concept-grid">
        <div class="concept-card">
            <div class="card-icon">🎯</div>
            <div class="card-title">Estimation প্রশ্নে</div>
            <div class="card-desc">১. DAU জিজ্ঞেস করো। ২. দৈনিক action জিজ্ঞেস করো। ৩. RPS হিসাব করো। ৪. Peak ×3 করো। ৫. Server সংখ্যা বের করো। সবসময় ধাপে ধাপে!</div>
        </div>
        <div class="concept-card green">
            <div class="card-icon">🏗️</div>
            <div class="card-title">System Design এ</div>
            <div class="card-desc">১. Requirements বোঝো। ২. Scale অনুমান করো। ৩. API Design করো। ৪. Database বেছে নাও। ৫. Scaling Strategy বলো। ৬. Failure cases নিয়ে ভাবো।</div>
        </div>
        <div class="concept-card purple">
            <div class="card-icon">🔄</div>
            <div class="card-title">Trade-offs নিয়ে বলো</div>
            <div class="card-desc">CAP Theorem: C বা A বেছে নাও। SQL vs NoSQL। Cache vs DB। Sync vs Async। প্রতিটা পছন্দের কারণ বলো — এটাই Interview তে জেতার চাবিকাঠি!</div>
        </div>
        <div class="concept-card orange">
            <div class="card-icon">📊</div>
            <div class="card-title">সংখ্যা মনে রাখো</div>
            <div class="card-desc">1 day ≈ 86,400s। Peak = avg×3। 99.99% = 52min/year downtime। L1 Cache = 1ns। Network = 150ms। এই সংখ্যাগুলো Estimation এ কাজে লাগে।</div>
        </div>
    </div>

    <!-- Learning Roadmap -->
    <div class="section-divider"></div>
    <h3 class="subsection-title">🗺️ শেখার রোডম্যাপ</h3>

    <div class="timeline">
        <div class="timeline-item">
            <div class="timeline-dot">1️⃣</div>
            <div class="timeline-content">
                <h4>সপ্তাহ ১-২: Foundation</h4>
                <p>Module 1 ও 2 ভালো করে পড়ো। CAP Theorem, Consistency, Latency মুখস্থ করো। Back-of-envelope calculation practice করো।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">2️⃣</div>
            <div class="timeline-content">
                <h4>সপ্তাহ ৩-৪: Node.js API</h4>
                <p>Module 3 এর কোড নিজে লেখো। Express দিয়ে CRUD API বানাও। PostgreSQL সংযুক্ত করো। Async/Await ভালো করে বোঝো।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">3️⃣</div>
            <div class="timeline-content">
                <h4>সপ্তাহ ৫-৬: Rate Limit ও Docker</h4>
                <p>Module 4 ও 7। Rate limiting middleware লেখো। Docker দিয়ে app containerize করো। Docker Compose দিয়ে পুরো stack চালাও।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">4️⃣</div>
            <div class="timeline-content">
                <h4>সপ্তাহ ৭-৮: AWS ও Networking</h4>
                <p>Module 6 ও 8। AWS Free Tier দিয়ে VPC বানাও। Linux Namespace experiment করো। পুরো microservice architecture deploy করো।</p>
            </div>
        </div>
        <div class="timeline-item">
            <div class="timeline-dot">🎓</div>
            <div class="timeline-content">
                <h4>সপ্তাহ ৯+: Practice ও Projects</h4>
                <p>System Design interview questions practice করো। Twitter, YouTube, WhatsApp design করার চেষ্টা করো। Real project বানাও এবং deploy করো!</p>
            </div>
        </div>
    </div>

    <!-- Final Motivation -->
    <div style="max-width:800px; margin:60px auto; text-align:center; padding:40px; background:linear-gradient(135deg, #0a1628, #0d2040); border:1px solid #00d4ff22; border-radius:24px;">
        <div style="font-size:48px; margin-bottom:20px;">🚀</div>
        <h3 style="font-size:28px; font-weight:900; background:linear-gradient(135deg,#00d4ff,#00ff88); -webkit-background-clip:text; -webkit-text-fill-color:transparent; background-clip:text; margin-bottom:16px;">তুমি পারবে!</h3>
        <p style="font-size:16px; color:#aaa; line-height:1.8; margin-bottom:24px;">System Design শেখা একটা যাত্রা, গন্তব্য নয়। প্রতিদিন একটু একটু শেখো, কোড লেখো, experiment করো। ভুল হওয়াটা স্বাভাবিক — সেটাই শেখার পথ।</p>
        <div style="display:flex; gap:20px; justify-content:center; flex-wrap:wrap;">
            <div style="background:#00d4ff11; border:1px solid #00d4ff33; border-radius:12px; padding:16px 24px;">
                <div style="font-size:24px;">📚</div>
                <div style="font-size:13px; color:#00d4ff; font-weight:700; margin-top:6px;">পড়ো</div>
            </div>
            <div style="background:#00ff8811; border:1px solid #00ff8833; border-radius:12px; padding:16px 24px;">
                <div style="font-size:24px;">💻</div>
                <div style="font-size:13px; color:#00ff88; font-weight:700; margin-top:6px;">কোড লেখো</div>
            </div>
            <div style="background:#b44fff11; border:1px solid #b44fff33; border-radius:12px; padding:16px 24px;">
                <div style="font-size:24px;">🔧</div>
                <div style="font-size:13px; color:#b44fff; font-weight:700; margin-top:6px;">Build করো</div>
            </div>
            <div style="background:#ff8c0011; border:1px solid #ff8c0033; border-radius:12px; padding:16px 24px;">
                <div style="font-size:24px;">🎯</div>
                <div style="font-size:13px; color:#ff8c00; font-weight:700; margin-top:6px;">Deploy করো</div>
            </div>
        </div>
    </div>
</div>

<!-- ══════════════════════════════════════════════════
     FOOTER
══════════════════════════════════════════════════ -->
<div class="footer">
    <div class="footer-logo">System Design & Backend Engineering</div>
    <p class="footer-text">সম্পূর্ণ গাইড বাংলায় — সহজ ভাষায়, ভিজুয়াল পদ্ধতিতে</p>
    <p class="footer-text" style="margin-top:8px; color:#333;">Module 1 • Module 2 • Module 3 • Module 4 • Module 6 • Module 7 • Module 8</p>
    <div style="margin-top:30px; padding-top:30px; border-top:1px solid #1a1a1a;">
        <p style="font-size:13px; color:#333;">সহজ বাংলায় শেখো, দক্ষ Engineer হও 🚀</p>
    </div>
</div>

<script>
    // Smooth scroll for TOC links
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
        anchor.addEventListener('click', function(e) {
            e.preventDefault();
            const target = document.querySelector(this.getAttribute('href'));
            if (target) {
                target.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }
        });
    });

    // Intersection Observer for animations
    const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
            if (entry.isIntersecting) {
                entry.target.style.opacity = '1';
                entry.target.style.transform = 'translateY(0)';
            }
        });
    }, { threshold: 0.1 });

    document.querySelectorAll('.concept-card, .metric-card, .timeline-item, .step-item').forEach(el => {
        el.style.opacity = '0';
        el.style.transform = 'translateY(20px)';
        el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
        observer.observe(el);
    });

    // Print function
    function printDoc() {
        window.print();
    }

    console.log(`
    ╔═══════════════════════════════════════╗
    ║  System Design Guide - বাংলায়         ║
    ║  সম্পূর্ণ গাইড লোড হয়েছে! 🎉         ║
    ║                                       ║
    ║  Modules: 1, 2, 3, 4, 6, 7, 8        ║
    ║  ভাষা: বাংলা                           ║
    ║  পদ্ধতি: Visual + Practical            ║
    ╚═══════════════════════════════════════╝
    `);
</script>

</body>
</html>
