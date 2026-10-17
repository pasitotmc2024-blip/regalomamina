# regalomamina
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Feliz Día, Mamina! 💗</title>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:ital,wght@0,600;0,700;1,400&family=Sacramento&display=swap" rel="stylesheet">
    <style>
        :root {
            --bg-color: #fce4ec;
            --card-bg: #ffffff;
            --primary: #d81b60;
            --primary-light: #f8bbd0;
            --primary-dark: #ad1457;
            --text-main: #4a4a4a;
            --text-light: #7a7a7a;
            --accent: #ff80ab;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background-color: var(--bg-color);
            font-family: 'Montserrat', sans-serif;
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
            position: relative;
        }

        /* Pétalos flotantes de fondo */
        .petals-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 1;
        }

        .petal {
            position: absolute;
            background: var(--accent);
            border-radius: 150% 0 150% 0;
            animation: fall linear infinite;
            opacity: 0.6;
        }

        @keyframes fall {
            0% {
                transform: translateY(-10vh) rotate(0deg);
                opacity: 0.8;
            }
            100% {
                transform: translateY(110vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Pantalla de Bienvenida (Overlay Inicial) */
        #welcome-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(252, 228, 236, 0.95);
            backdrop-filter: blur(8px);
            z-index: 1000;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            transition: opacity 0.8s ease, visibility 0.8s ease;
        }

        .welcome-card {
            background: var(--card-bg);
            padding: 35px 30px;
            border-radius: 24px;
            text-align: center;
            max-width: 400px;
            width: 100%;
            box-shadow: 0 15px 35px rgba(216, 27, 96, 0.15);
            border: 1px solid rgba(248, 187, 208, 0.5);
            position: relative;
            animation: popUp 0.6s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        @keyframes popUp {
            0% { transform: scale(0.8); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .welcome-icon-wrapper {
            width: 70px;
            height: 70px;
            background: linear-gradient(135deg, #ff80ab, #d81b60);
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 0 auto 20px auto;
            box-shadow: 0 8px 20px rgba(216, 27, 96, 0.3);
        }

        .welcome-icon-wrapper svg {
            width: 32px;
            height: 32px;
            fill: white;
        }

        .welcome-subtitle {
            font-size: 0.85rem;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: var(--primary);
            font-weight: 600;
            margin-bottom: 8px;
        }

        .welcome-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.8rem;
            color: #2c2c2c;
            margin-bottom: 15px;
        }

        .welcome-text {
            font-size: 0.95rem;
            color: var(--text-light);
            line-height: 1.5;
            margin-bottom: 25px;
        }

        .btn-open {
            background: linear-gradient(135deg, #ff4081, #d81b60);
            color: white;
            border: none;
            padding: 14px 28px;
            font-size: 1rem;
            font-weight: 600;
            border-radius: 50px;
            cursor: pointer;
            width: 100%;
            box-shadow: 0 6px 20px rgba(216, 27, 96, 0.4);
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }

        .btn-open:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(216, 27, 96, 0.5);
        }

        /* Contenido Principal (Oculto hasta abrir) */
        #main-content {
            opacity: 0;
            visibility: hidden;
            transition: opacity 1s ease;
            width: 100%;
            max-width: 500px;
            padding: 20px;
            z-index: 10;
            display: flex;
            flex-direction: column;
            gap: 25px;
            margin: auto;
        }

        .visible {
            opacity: 1 !important;
            visibility: visible !important;
        }

        /* Tarjeta Contenedora Principal */
        .card {
            background: var(--card-bg);
            border-radius: 24px;
            padding: 30px 25px;
            box-shadow: 0 10px 30px rgba(0,0,0,0.05);
            border: 1px solid rgba(255, 182, 193, 0.3);
            text-align: center;
        }

        /* Barra de música */
        .music-bar {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            background: rgba(248, 187, 208, 0.3);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.85rem;
            color: var(--primary-dark);
            margin-bottom: 15px;
            font-weight: 500;
        }

        /* Título principal */
        .main-title {
            font-family: 'Sacramento', cursive;
            font-size: 3.5rem;
            color: var(--primary);
            margin-bottom: 15px;
            line-height: 1;
        }

        .main-message {
            font-size: 1.05rem;
            line-height: 1.6;
            color: var(--text-main);
        }

        /* Sección Sobres Sorpresa */
        .section-title {
            font-family: 'Playfair Display', serif;
            font-size: 1.3rem;
            color: var(--primary-dark);
            margin-bottom: 18px;
            font-weight: 600;
        }

        .envelope-btn {
            background: #fff;
            border: 1.5px solid var(--primary-light);
            padding: 14px 20px;
            border-radius: 14px;
            width: 100%;
            text-align: left;
            font-family: 'Montserrat', sans-serif;
            font-size: 0.95rem;
            font-weight: 500;
            color: var(--text-main);
            cursor: pointer;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
            transition: all 0.3s ease;
            box-shadow: 0 4px 10px rgba(0,0,0,0.02);
        }

        .envelope-btn:hover {
            background: #fff0f3;
            border-color: var(--accent);
            transform: translateY(-1px);
        }

        .envelope-content {
            max-height: 0;
            overflow: hidden;
            transition: max-height 0.4s ease, padding 0.4s ease;
            background: #fff9fa;
            border-radius: 0 0 14px 14px;
            margin-top: -10px;
            margin-bottom: 12px;
            text-align: left;
            padding: 0 20px;
            font-size: 0.92rem;
            line-height: 1.6;
            color: var(--text-main);
            border-left: 3px solid var(--primary);
        }

        .envelope-content.show {
            max-height: 350px;
            padding: 15px 20px;
        }

        /* Cupones Especiales */
        .coupons-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
        }

        .coupon {
            background: linear-gradient(135deg, #fff0f3, #ffe4e9);
            border: 2px dashed var(--primary-light);
            padding: 15px;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .coupon:hover {
            transform: scale(1.01);
        }

        .coupon-info h4 {
            font-size: 0.95rem;
            color: var(--primary-dark);
            margin-bottom: 3px;
        }

        .coupon-info p {
            font-size: 0.8rem;
            color: var(--text-light);
        }

        .coupon-btn {
            background: var(--primary);
            color: white;
            border: none;
            padding: 6px 14px;
            font-size: 0.8rem;
            border-radius: 20px;
            font-weight: 600;
            cursor: pointer;
            transition: background 0.2s;
        }

        .coupon.redeemed {
            background: #f0f0f0;
            border-color: #ddd;
            opacity: 0.7;
        }

        .coupon.redeemed .coupon-btn {
            background: #9e9e9e;
        }

        /* Botón final de celebración */
        .footer-action {
            text-align: center;
            padding-bottom: 20px;
        }

        .btn-celebrate {
            background: white;
            color: var(--primary);
            border: 2px solid var(--primary);
            padding: 12px 25px;
            border-radius: 30px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
            box-shadow: 0 4px 15px rgba(216, 27, 96, 0.1);
        }

        .btn-celebrate:hover {
            background: var(--primary);
            color: white;
        }
    </style>
</head>
<body>

    <!-- Pétalos cayendo -->
    <div class="petals-container" id="petals"></div>

    <!-- Pantalla de Bienvenida -->
    <div id="welcome-overlay">
        <div class="welcome-card">
            <div class="welcome-icon-wrapper">
                <svg viewBox="0 0 24 24">
                    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/>
                </svg>
            </div>
            <p class="welcome-subtitle">Un regalo con todo mi amor</p>
            <h1 class="welcome-title">Para la Mamina 💗</h1>
            <p class="welcome-text">Preparé esto para recordarte cuánto te quiero y agradecerte por todo.</p>
            <button class="btn-open" onclick="openCard()">Abrir mensaje especial ❤️</button>
        </div>
    </div>

    <!-- Contenido Principal -->
    <div id="main-content">
        
        <!-- Tarjeta Carta -->
        <div class="card">
            <div class="music-bar">
                <span>🎵 El Plan de la Mariposa - El túnel de la vida</span>
            </div>
            <h1 class="main-title">¡Feliz Día, Mamina!</h1>
            <p class="main-message">
                Gracias por tus abrazos que curan todo, por tu paciencia en mis días malos y por ser la razón de mi existir.
            </p>
        </div>

        <!-- Pequeños sobres sorpresa -->
        <div class="card">
            <h3 class="section-title">Pequeños sobres sorpresa 💌</h3>

            <!-- Sobre 1 -->
            <button class="envelope-btn" onclick="toggleEnvelope('env1')">
                <span>✨ Una razón para amarte</span>
                <span>▼</span>
            </button>
            <div id="env1" class="envelope-content">
                Porque haces todo lo posible para verme bien.<br><br>
                Porque siempre creíste en mí y me criaste fuerte e independiente.<br><br>
                Porque cuando la cena no alcanzaba para las dos, vos me dabas tu plato, y eso dice tanto de vos mamá.<br><br>
                Porque me permitis estar aquí, cumpliendo una de mis metas mas grandes, incluso aunque todo esto signifique un esfuerzo constante de ambas.
            </div>

            <!-- Sobre 2 -->
            <button class="envelope-btn" onclick="toggleEnvelope('env2')">
                <span>✨ Mis recuerdos favoritos</span>
                <span>▼</span>
            </button>
            <div id="env2" class="envelope-content">
                Cuando dormiamos en camas separadas y me dabas la manito para que pueda dormir.<br><br>
                Cuando me dejabas tocar tu chichito en todos lados jiji.<br><br>
                Cuando me abrazaste y me dijiste que nos ibamos de viaje a brasil.<br><br>
                Y así muchos más... solo espero que tengamos toda esta vida para crear nuevos e increíbles recuerdos juntas.
            </div>

            <!-- Sobre 3 -->
            <button class="envelope-btn" onclick="toggleEnvelope('env3')">
                <span>❤️ Un deseo para vos</span>
                <span>▼</span>
            </button>
            <div id="env3" class="envelope-content">
                Sé que este día de la madre es uno muy triste y con recuerdos que son como gotas de limón en una herida muy notoria. Pero realmente espero que algún día te sientas mejor y dejes de tener tantas culpas, porque sino la vida se te va a ir en toda esa tristeza; y yo te necesito fuerte y luchadora como todos estos años. Espero que este pequeño detalle te haga sentirte un poquitito mejor.
            </div>
        </div>

        <!-- Vales especiales -->
        <div class="card">
            <h3 class="section-title">Vales especiales para Mamá</h3>
            <div class="coupons-grid">
                <div class="coupon" onclick="redeemCoupon(this)">
                    <div class="coupon-info">
                        <h4>☕ Desayuno a la cama</h4>
                        <p>Preparado con mucho amor</p>
                    </div>
                    <button class="coupon-btn">Canjear</button>
                </div>
                <div class="coupon" onclick="redeemCoupon(this)">
                    <div class="coupon-info">
                        <h4>🫂 Abrazo de oso ilimitado</h4>
                        <p>Válido para cualquier momento</p>
                    </div>
                    <button class="coupon-btn">Canjear</button>
                </div>
                <div class="coupon" onclick="redeemCoupon(this)">
                    <div class="coupon-info">
                        <h4>🎬 Tarde de pelis juntas</h4>
                        <p>A elección de la reina</p>
                    </div>
                    <button class="coupon-btn">Canjear</button>
                </div>
            </div>
        </div>

        <!-- Botón Final -->
        <div class="footer-action">
            <button class="btn-celebrate" onclick="triggerCelebration()">🎉 ¡Te amo muchísimo, Mamina!</button>
        </div>

    </div>

    <!-- Script de interactividad -->
    <script>
        // Generar pétalos flotantes en el fondo
        function createPetals() {
            const container = document.getElementById('petals');
            const petalCount = 18;
            for (let i = 0; i < petalCount; i++) {
                const petal = document.createElement('div');
                petal.classList.add('petal');
                petal.style.left = Math.random() * 100 + 'vw';
                petal.style.top = -20 + 'px';
                const size = Math.random() * 10 + 10;
                petal.style.width = size + 'px';
                petal.style.height = size * 1.4 + 'px';
                petal.style.animationDuration = (Math.random() * 6 + 5) + 's';
                petal.style.animationDelay = (Math.random() * 5) + 's';
                container.appendChild(petal);
            }
        }
        createPetals();

        // Abrir tarjeta principal
        function openCard() {
            const overlay = document.getElementById('welcome-overlay');
            const mainContent = document.getElementById('main-content');
            
            overlay.style.opacity = '0';
            setTimeout(() => {
                overlay.style.display = 'none';
                mainContent.classList.add('visible');
            }, 600);
        }

        // Control de sobres desplegables
        function toggleEnvelope(id) {
            const content = document.getElementById(id);
            const isOpen = content.classList.contains('show');
            
            // Cerrar todos primero opcionalmente, o dejar abiertos. Aquí abrimos/cerramos de forma independiente:
            content.classList.toggle('show');
        }

        // Canjear cupones
        function redeemCoupon(element) {
            if (!element.classList.contains('redeemed')) {
                element.classList.add('redeemed');
                const btn = element.querySelector('.coupon-btn');
                btn.textContent = '¡Canjeado! ❤️';
            }
        }

        // Celebración final
        function triggerCelebration() {
            alert('¡Te amamos infinitamente, Mamina! Que tengas un hermoso día. 💖✨');
        }
    </script>
</body>
</html>
