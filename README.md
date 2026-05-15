<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>WaiFox - Android Media Downloader</title>
    <style>
        :root {
            --bg-primary: #0f0f0f;
            --bg-secondary: #181818;
            --bg-tertiary: #202020;
            --text-primary: #ffffff;
            --text-secondary: #bdbdbd;
            --border-color: #303030;
            --accent-color: #FF0000;
            --accent-blue: #3EA6FF;
            --patreon-color: #FF424D;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(180deg, #0f0f0f 0%, #171717 100%);
            color: var(--text-primary);
            line-height: 1.6;
            min-height: 100vh;
            padding: 40px 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: var(--bg-primary);
            border-radius: 15px;
            box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
            border: 1px solid var(--border-color);
            overflow: hidden;
        }

        header {
            padding: 50px 40px;
            text-align: center;
            border-bottom: 1px solid var(--border-color);
            background: var(--bg-secondary);
        }

        .app-icon {
            width: 120px;
            height: 120px;
            border-radius: 24px;
            margin-bottom: 25px;
            box-shadow: 0 10px 30px rgba(255, 0, 0, 0.3);
            background: #202020;
            display: inline-block;
            object-fit: contain;
        }

        h1 {
            font-size: 3rem;
            margin-bottom: 10px;
            font-weight: 800;
            letter-spacing: -1px;
        }

        .badges {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-bottom: 25px;
            flex-wrap: wrap;
        }

        .badges img {
            height: 28px;
        }

        .tagline {
            color: var(--text-secondary);
            font-size: 1.2rem;
            max-width: 700px;
            margin: 0 auto 30px;
        }

        .btn-container {
            display: flex;
            justify-content: center;
            gap: 15px;
            flex-wrap: wrap;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 10px;
            padding: 12px 24px;
            border-radius: 8px;
            text-decoration: none;
            font-weight: 700;
            font-size: 0.9rem;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            border: 1px solid transparent;
        }

        .btn-release { background: var(--accent-color); color: white; }
        .btn-release:hover { background: #cc0000; transform: translateY(-2px); }

        .btn-windows { background: var(--bg-tertiary); color: var(--accent-blue); border-color: var(--border-color); }
        .btn-windows:hover { border-color: var(--accent-blue); transform: translateY(-2px); }

        .btn-patreon { background: var(--patreon-color); color: white; }
        .btn-patreon:hover { opacity: 0.9; transform: translateY(-2px); }

        .content {
            padding: 50px 40px;
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 35px;
            padding-left: 15px;
            border-left: 4px solid var(--accent-color);
        }

        .feature-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
            margin-bottom: 50px;
        }

        .feature-item {
            background: var(--bg-secondary);
            border: 1px solid var(--border-color);
            padding: 25px;
            border-radius: 12px;
            transition: transform 0.3s, border-color 0.3s;
        }

        .feature-item:hover {
            transform: translateY(-5px);
            border-color: var(--accent-blue);
        }

        .feature-icon {
            font-size: 1.8rem;
            margin-bottom: 15px;
            display: block;
        }

        .feature-item h3 {
            margin-bottom: 10px;
            color: var(--text-primary);
        }

        .feature-item p {
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        .app-preview {
            background: var(--bg-tertiary);
            border-radius: 12px;
            padding: 30px;
            border: 1px solid var(--border-color);
            margin-bottom: 50px;
        }

        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 25px;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 10px;
            overflow-x: auto;
        }

        .tab-btn {
            background: none;
            border: none;
            color: var(--text-secondary);
            padding: 10px 20px;
            cursor: pointer;
            font-weight: 600;
            border-radius: 8px;
            transition: all 0.2s;
            white-space: nowrap;
        }

        .tab-btn.active {
            background: var(--bg-secondary);
            color: var(--accent-blue);
        }

        .tab-content {
            display: none;
            animation: fadeIn 0.4s ease;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .info-card {
            background: var(--bg-secondary);
            padding: 20px;
            border-radius: 8px;
            border-left: 4px solid var(--accent-color);
            margin-bottom: 15px;
        }

        footer {
            text-align: center;
            padding: 40px;
            background: var(--bg-secondary);
            border-top: 1px solid var(--border-color);
            color: var(--text-secondary);
            font-size: 0.9rem;
        }

        @media (max-width: 600px) {
            .content { padding: 20px; }
            h1 { font-size: 2rem; }
        }
    </style>
</head>
<body>

    <div class="container">
        <header>
            <img src="C:\Users\gonza\Desktop\Yt-Downloader - apk\Icono.ico" alt="WaiFox Icon" class="app-icon" onerror="this.src='https://raw.githubusercontent.com/OneMoreKyra/WaiFox_Android/main/Icono.ico';">
            <h1>WaiFox</h1>
            
            <div class="badges">
                <img src="https://img.shields.io/github/v/release/OneMoreKyra/WaiFox_Android?style=for-the-badge&color=FF0000&label=VERSIÓN" alt="Versión">
                <img src="https://img.shields.io/github/downloads/OneMoreKyra/WaiFox_Android/total?style=for-the-badge&color=3EA6FF&label=DESCARGAS" alt="Descargas">
                <img src="https://img.shields.io/github/stars/OneMoreKyra/WaiFox_Android?style=for-the-badge&color=yellow&label=ESTRELLAS" alt="Estrellas">
            </div>

            <p class="tagline">Tu contenido favorito de cualquier red social, siempre contigo, sin anuncios y totalmente gratis.</p>

            <div class="btn-container">
                <a href="https://github.com/OneMoreKyra/WaiFox_Android/releases/latest" class="btn btn-release">Descargar APK</a>
                <a href="https://github.com/OneMoreKyra/YtDownloader" class="btn btn-windows">Versión para PC</a>
                <a href="https://www.patreon.com/OneMoreKyra" class="btn btn-patreon">Apoyame en Patreon</a>
            </div>
        </header>

        <div class="content">
            <h2 class="section-title">Funciones Principales</h2>
            <div class="feature-grid">
                <div class="feature-item">
                    <span class="feature-icon">🎬</span>
                    <h3>Videos de Alta Calidad</h3>
                    <p>Descarga desde YouTube, Facebook, Twitter (X), Instagram y TikTok (¡Sin marcas de agua!). Elige siempre la mejor resolución.</p>
                </div>
                <div class="feature-item">
                    <span class="feature-icon">✨</span>
                    <h3>Gran Personalización</h3>
                    <p>Haz la app a tu medida. Elige entre temas claro u oscuro, personaliza tus carpetas de descarga fácilmente y mucho mas.</p>
                </div>
                <div class="feature-item">
                    <span class="feature-icon">💎</span>
                    <h3>Sin Pagos Ocultos</h3>
                    <p>Disfruta de la experiencia completa sin suscripciones, muros de pago ni límites de descarga engañosos.</p>
                </div>
                <div class="feature-item">
                    <span class="feature-icon">🚫</span>
                    <h3>Sin Rellenos</h3>
                    <p>Utiliza el poder de <a href="https://github.com/ajayyy/SponsorBlock" target="_blank" style="color: var(--accent-blue); text-decoration: none; font-weight: bold;">SponsorBlock</a> para saltar automáticamente las introducciones y anuncios de patrocinadores en los videos para ir directo al contenido.</p>
                </div>

                <div class="feature-item">
                    <span class="feature-icon">📋</span>
                    <h3>Copiado Inteligente</h3>
                    <p>Solo copia un enlace y abre la app; WaiFox lo detectará al instante para empezar la descarga.</p>
                </div>
                <div class="feature-item">
                    <span class="feature-icon">⚡</span>
                    <h3>Segundo Plano</h3>
                    <p>Sigue usando tu móvil mientras WaiFox descarga tus archivos, con notificaciones de progreso reales.</p>
                </div>
            </div>

            <h2 class="section-title">¿Cómo funciona?</h2>
            <div class="app-preview">
                <div class="tabs">
                    <button class="tab-btn active" onclick="showTab('redes')">Redes Sociales</button>
                    <button class="tab-btn" onclick="showTab('musica')">Música</button>
                    <button class="tab-btn" onclick="showTab('ajustes')">Ajustes</button>
                </div>

                <div id="redes" class="tab-content active">
                    <div class="info-card">
                        <strong>Compatibilidad Total:</strong> Baja videos de casi cualquier lugar. TikTok, Instagram, Twitter y más, conservando la mayor calidad posible y sin marcas de agua molestas.
                    </div>
                </div>

                <div id="musica" class="tab-content">
                    <div class="info-card" style="border-left-color: var(--accent-blue);">
                        <strong>Música Perfecta:</strong> Tus canciones se descargan en MP3 con su carátula original, nombre del artista y título correcto automáticamente.
                    </div>
                </div>

                <div id="ajustes" class="tab-content">
                    <div class="info-card" style="border-left-color: #99ff99;">
                        <strong>A tu Estilo:</strong> Cambia el tema de la app, elige dónde guardar tus archivos y personaliza tu experiencia en un solo lugar.
                    </div>
                </div>
            </div>
        </div>

        <footer>
            <p>Creado con ❤️ por <strong>OneMoreKyra</strong></p>
            <p style="margin-top: 10px; opacity: 0.6;">Disfruta de tu contenido favorito sin límites, sin marcas y con estilo.</p>
        </footer>
    </div>

    <script>
        function showTab(id) {
            document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(b => b.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            event.target.classList.add('active');
        }
    </script>
</body>
</html>
