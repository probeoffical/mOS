# mOS <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>mOS // Micro Operating System</title>
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: rgba(255, 255, 255, 0.03);
            --card-border: rgba(255, 255, 255, 0.08);
            --text-main: #f3f4f6;
            --text-muted: #9ca3af;
            --accent: #38bdf8;
            --accent-glow: rgba(56, 189, 248, 0.2);
            --badge-bg: rgba(56, 189, 248, 0.1);
            --badge-border: rgba(56, 189, 248, 0.3);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Roboto, Helvetica, Arial, sans-serif;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
            position: relative;
        }

        body::before {
            content: '';
            position: absolute;
            top: -20%;
            left: 50%;
            transform: translateX(-50%);
            width: 600px;
            height: 600px;
            background: radial-gradient(circle, var(--accent-glow) 0%, rgba(0,0,0,0) 70%);
            z-index: -1;
            filter: blur(60px);
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 24px 40px;
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
        }

        .brand {
            font-weight: 700;
            font-size: 1.1rem;
            letter-spacing: 1px;
            color: var(--text-main);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .brand span {
            color: var(--accent);
        }

        .lang-switch {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            color: var(--text-main);
            padding: 6px 14px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 0.85rem;
            font-weight: 600;
            transition: all 0.2s ease;
            backdrop-filter: blur(10px);
        }

        .lang-switch:hover {
            border-color: var(--accent);
            background: rgba(56, 189, 248, 0.05);
        }

        main {
            flex: 1;
            width: 100%;
            max-width: 1000px;
            margin: 0 auto;
            padding: 0 24px 60px 24px;
            display: flex;
            flex-direction: column;
            gap: 24px;
            animation: fadeIn 0.6s ease-out;
        }

        .card {
            background: var(--card-bg);
            border: 1px solid var(--card-border);
            border-radius: 16px;
            padding: 32px;
            backdrop-filter: blur(16px);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.3);
            transition: border-color 0.2s ease;
        }

        .card:hover {
            border-color: rgba(255, 255, 255, 0.15);
        }

        h1 {
            font-size: 2.2rem;
            font-weight: 800;
            margin-bottom: 12px;
            background: linear-gradient(135deg, #ffffff 0%, #94a3b8 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .subtitle {
            color: var(--text-muted);
            font-size: 1.05rem;
            line-height: 1.6;
            margin-bottom: 24px;
        }

        h2 {
            font-size: 1.3rem;
            font-weight: 700;
            margin-bottom: 14px;
            color: var(--accent);
            display: flex;
            align-items: center;
            gap: 8px;
        }

        p, li {
            color: var(--text-muted);
            font-size: 0.95rem;
            line-height: 1.7;
        }

        ul {
            list-style: none;
            display: flex;
            flex-direction: column;
            gap: 10px;
            margin-top: 10px;
        }

        .features-list li {
            position: relative;
            padding-left: 20px;
        }

        .features-list li::before {
            content: '▪';
            position: absolute;
            left: 0;
            color: var(--accent);
        }

        /* GitHub Release Box Styling */
        .release-box {
            border-left: 4px solid var(--accent);
            background: rgba(56, 189, 248, 0.02);
        }

        .release-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 16px;
            flex-wrap: wrap;
            gap: 10px;
        }

        .tag-badge {
            background: var(--badge-bg);
            border: 1px solid var(--badge-border);
            color: var(--accent);
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 700;
            letter-spacing: 0.5px;
        }

        .compatibility-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 16px;
            margin-top: 20px;
            margin-bottom: 24px;
        }

        .compat-card {
            background: rgba(0, 0, 0, 0.2);
            border: 1px solid var(--card-border);
            border-radius: 12px;
            padding: 20px;
        }

        .compat-card h3 {
            font-size: 1rem;
            color: var(--text-main);
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
        }

        .compat-card h3 span {
            font-size: 0.75rem;
            padding: 2px 6px;
            border-radius: 4px;
            background: rgba(255, 255, 255, 0.1);
            color: var(--text-muted);
        }

        .download-btn {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 8px;
            width: 100%;
            background: var(--accent);
            color: #0b0f19;
            padding: 10px 16px;
            border-radius: 8px;
            font-weight: 700;
            text-decoration: none;
            margin-top: 14px;
            transition: opacity 0.2s ease, transform 0.2s ease;
        }

        .download-btn:hover {
            opacity: 0.9;
            transform: translateY(-1px);
        }

        footer {
            text-align: center;
            padding: 24px;
            color: var(--text-muted);
            font-size: 0.8rem;
            border-top: 1px solid var(--card-border);
            max-width: 1000px;
            width: 100%;
            margin: 0 auto;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .lang-content {
            display: none;
        }

        .lang-content.active {
            display: flex;
            flex-direction: column;
            gap: 24px;
        }
    </style>
</head>
<body>

    <header>
        <div class="brand">mOS <span>// PROBE</span></div>
        <button class="lang-switch" onclick="toggleLanguage()" id="langBtn">TR / EN</button>
    </header>

    <main>
        <!-- ENGLISH CONTENT -->
        <div id="content-en" class="lang-content active">
            <div class="card">
                <h1>🚀 mOS (Micro Operating System)</h1>
                <p class="subtitle">A minimalist, dual-architecture custom firmware and micro-UI for BBC micro:bit v1/v1.5 and v2.<br><strong>Developed by PROBE</strong></p>
            </div>

            <div class="card">
                <h2>📌 What is mOS?</h2>
                <p>mOS is a custom-built, lightweight operating system/firmware designed from scratch for BBC micro:bit microcontrollers. Built to bypass the limitations of stock environments, mOS brings a clean, PCB-inspired minimalist interface, custom boot sequences, system utilities, and retro arcade gaming directly to your 5x5 LED matrix.</p>
            </div>

            <div class="card">
                <h2>⚡ Architectural Editions</h2>
                <ul class="features-list">
                    <li><strong>mOS Pixel Alpha (v1 / v1.5):</strong> Engineered for the 16KB RAM limit. Ultra-lightweight, zero bloatware, focusing on core system monitoring and smooth retro gameplay.</li>
                    <li><strong>mOS Pixel Pro (v2):</strong> Harnessing the full power of the nRF52833 chip. Features onboard audio/speaker support, touch-logo shortcuts, and advanced real-time sensor integration.</li>
                </ul>
            </div>

            <!-- GITHUB RELEASE / DOWNLOAD HUB -->
            <div class="card release-box">
                <div class="release-header">
                    <h2>📦 Latest Release: Pixel Alpha (v1.0)</h2>
                    <span class="tag-badge">Stable Build</span>
                </div>
                <p>Select your hardware version below to download the compiled firmware package (.hex). Drag and drop the file directly onto your connected micro:bit drive.</p>
                
                <div class="compatibility-grid">
                    <div class="compat-card">
                        <h3>mOS Pixel Alpha <span>v1 / v1.5</span></h3>
                        <p>Optimized for 16KB RAM chips. Includes System Monitor & Retro Pong.</p>
                        <a href="https://github.com/probeoffical/mOS/releases/latest" target="_blank" class="download-btn">Download v1 .HEX ⬇</a>
                    </div>
                    <div class="compat-card">
                        <h3>mOS Pixel Pro <span>v2</span></h3>
                        <p>Powered by nRF52833. Includes onboard speaker audio & touch logo.</p>
                        <a href="https://github.com/probeoffical/mOS/releases/latest" target="_blank" class="download-btn">Download v2 .HEX ⬇</a>
                    </div>
                </div>

                <p style="font-size: 0.85rem; color: var(--text-muted);">💡 <strong>Installation Guide:</strong> Connect your micro:bit via USB, put it into mass storage mode, and copy the downloaded `.hex` file straight into the MICROBIT drive.</p>
            </div>

            <div class="card">
                <h2>🎮 Core Features (Pixel Alpha Edition)</h2>
                <ul class="features-list">
                    <li><strong>Custom Boot Sequence:</strong> Minimalist expanding-pixel animation leading straight into the mOS startup screen.</li>
                    <li><strong>System Monitor:</strong> Real-time light level and environmental status checking.</li>
                    <li><strong>Retro Pong:</strong> A classic physics-based arcade minigame optimized for the LED grid.</li>
                    <li><strong>Quick Info Shortcut:</strong> Pressing A + B anywhere in the menu instantly displays your exact build info (mOS v1.5-v1 pixel alpha).</li>
                </ul>
            </div>
        </div>

        <!-- TURKISH CONTENT -->
        <div id="content-tr" class="lang-content">
            <div class="card">
                <h1>🚀 mOS (Micro Operating System)</h1>
                <p class="subtitle">BBC micro:bit v1/v1.5 ve v2 için minimalist, çift mimarili özel yazılım ve mikro arayüz.<br><strong>Geliştiren: PROBE</strong></p>
            </div>

            <div class="card">
                <h2>📌 mOS Nedir?</h2>
                <p>mOS, BBC micro:bit mikrodenetleyicileri için sıfırdan tasarlanmış özel bir hafif işletim sistemi/yazılımdır. Stok ortamların kısıtlamalarını aşmak için inşa edilen mOS; temiz, PCB esintili minimalist bir arayüz, özel açılış sekansları, sistem araçları ve retro arcade oyunlarını doğrudan 5x5 LED matrisinize getirir.</p>
            </div>

            <div class="card">
                <h2>⚡ Mimari Sürümler</h2>
                <ul class="features-list">
                    <li><strong>mOS Pixel Alpha (v1 / v1.5):</strong> 16KB RAM sınırı için tasarlandı. Aşırı hafif, gereksiz şişkinlik yok, temel sistem izleme ve pürüzsüz retro oynanışa odaklanır.</li>
                    <li><strong>mOS Pixel Pro (v2):</strong> nRF52833 çipinin tüm gücünü arkasına alır. Dahili ses/hoparlör desteği, dokunmatik logo kısayolları ve gelişmiş gerçek zamanlı sensör entegrasyonu sunar.</li>
                </ul>
            </div>

            <!-- GITHUB RELEASE / DOWNLOAD HUB (TURKISH) -->
            <div class="card release-box">
                <div class="release-header">
                    <h2>📦 En Son Sürüm: Pixel Alpha (v1.0)</h2>
                    <span class="tag-badge">Kararlı Sürüm</span>
                </div>
                <p>Derlenmiş yazılım paketini (.hex) indirmek için aşağıdan donanım sürümünüzü seçin. Dosyayı doğrudan bağlı olan micro:bit sürücünüze sürükleyip bırakın.</p>
                
                <div class="compatibility-grid">
                    <div class="compat-card">
                        <h3>mOS Pixel Alpha <span>v1 / v1.5</span></h3>
                        <p>16KB RAM çipler için optimize edilmiştir. Sistem Monitörü ve Retro Pong içerir.</p>
                        <a href="https://github.com/probeoffical/mOS/releases/latest" target="_blank" class="download-btn">v1 .HEX İndir ⬇</a>
                    </div>
                    <div class="compat-card">
                        <h3>mOS Pixel Pro <span>v2</span></h3>
                        <p>nRF52833 gücüyle çalışır. Dahili hoparlör sesi ve dokunmatik logo barındırır.</p>
                        <a href="https://github.com/probeoffical/mOS/releases/latest" target="_blank" class="download-btn">v2 .HEX İndir ⬇</a>
                    </div>
                </div>

                <p style="font-size: 0.85rem; color: var(--text-muted);">💡 <strong>Kurulum Rehberi:</strong> micro:bit'inizi USB ile bağlayın ve indirdiğiniz `.hex` dosyasını doğrudan MICROBIT sürücüsünün içine kopyalayın.</p>
            </div>

            <div class="card">
                <h2>🎮 Temel Özellikler (Pixel Alpha Sürümü)</h2>
                <ul class="features-list">
                    <li><strong>Özel Açılış Sekansı:</strong> mOS başlangıç ekranına doğrudan bağlanan minimalist genişleyen piksel animasyonu.</li>
                    <li><strong>Sistem Monitörü:</strong> Gerçek zamanlı ışık seviyesi ve çevresel durum kontrolü.</li>
                    <li><strong>Retro Pong:</strong> LED ızgarası için optimize edilmiş klasik fizik tabanlı arcade mini oyunu.</li>
                    <li><strong>Hızlı Bilgi Kısayolu:</strong> Menünün herhangi bir yerinde A + B tuşlarına basarak tam sürüm bilginizi (mOS v1.5-v1 pixel alpha) anında görüntüleyin.</li>
                </ul>
            </div>
        </div>
    </main>

    <footer>
        <p>"mOS is an independent project by PROBE. Not affiliated with any other operating systems."</p>
    </footer>

    <script>
        let currentLang = 'en';

        function toggleLanguage() {
            const enContent = document.getElementById('content-en');
            const trContent = document.getElementById('content-tr');
            const langBtn = document.getElementById('langBtn');

            if (currentLang === 'en') {
                enContent.classList.remove('active');
                trContent.classList.add('active');
                langBtn.innerText = 'EN / TR';
                currentLang = 'tr';
            } else {
                trContent.classList.remove('active');
                enContent.classList.add('active');
                langBtn.innerText = 'TR / EN';
                currentLang = 'en';
            }
        }
    </script>
</body>
</html>
