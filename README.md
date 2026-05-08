<A fines de entretenimiento y conocimiento.>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Guía</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', sans-serif;
        }

        body {
            background: url('fondo.png') no-repeat center center fixed;
            background-size: cover;
            color: white;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        /* CAPA OSCURA DE FONDO */
        .overlay {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.75);
            z-index: 1;
        }

        /* EFECTO DE HUMO ANIMADO */
        .humo {
            position: fixed;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.05) 10%, transparent 60%);
            animation: humo-mov 20s linear infinite;
            z-index: 2;
            pointer-events: none;
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-100px,-100px); }
        }

        .container {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 90%;
            max-width: 800px;
        }

        /* TÍTULO CON BRILLO AZUL */
        h1 {
            font-size: clamp(35px, 8vw, 60px);
            text-shadow: 0 0 20px #00aaff;
            margin-bottom: 10px;
            color: white;
        }

        .slogan {
            font-size: 1.2rem;
            margin-bottom: 40px;
            opacity: 0.8;
        }

        /* BOTÓN ENTRAR ESTILIZADO */
        .btn-entrar {
            padding: 15px 50px;
            background: #00aaff;
            border: none;
            color: white;
            font-size: 20px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.3s;
            box-shadow: 0 0 15px rgba(0, 170, 255, 0.5);
        }

        .btn-entrar:hover {
            transform: scale(1.05);
            box-shadow: 0 0 30px #00aaff;
        }

        /* PANTALLA DE CONTENIDO */
        #contenido {
            display: none;
            flex-direction: column;
            align-items: center;
        }

        .menu-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 20px;
        }

        .tarjeta {
            padding: 20px;
            background: rgba(0, 0, 0, 0.8);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            text-align: left;
            transition: 0.3s;
        }

        .tarjeta:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
        }

        /* PANEL DE DETALLE (EL DEL VIDEO) */
        #detalle {
            margin-top: 20px;
            padding: 25px;
            background: rgba(0, 0, 0, 0.9);
            border: 1px solid #00aaff;
            text-align: left;
            display: none;
            line-height: 1.6;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 10px; }
        #detalle ul { margin-left: 20px; }

        .btn-volver {
            background: none;
            border: 1px solid white;
            color: white;
            padding: 5px 15px;
            cursor: pointer;
            margin-bottom: 20px;
            align-self: flex-start;
        }
    </style>
</head>
<body>

    <div class="overlay"></div>
    <div class="humo"></div>

    <div class="container">
        <div id="inicio">
            <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
            <p class="slogan">Guía Táctica de Combate</p>
            <button class="btn-entrar" onclick="entrar()">Entrar</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="volver()">⬅ Volver</button>
            <div class="menu-grid">
                <div class="tarjeta" onclick="abrir('marina')">⚓ Marina</div>
                <div class="tarjeta" onclick="abrir('tierra')">🪖 Terrestre</div>
                <div class="tarjeta" onclick="abrir('aire')">✈️ Aéreo</div>
                <div class="tarjeta" onclick="abrir('logistica')">📦 Logística</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        function entrar() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
        }

        function volver() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
        }

        function abrir(seccion) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const info = {
                marina: `
                    <h3>⚓ ESTRATEGIA NAVAL DEFINITIVA</h3>
                    <p><strong>Estructura de Combate:</strong> Divide tu flota en 4 zonas. Las pantallas (Destructores/Cruceros Ligeros) deben proteger a tus Buques Capitales en un ratio de 4:1 para interceptar torpedos.</p>
                    <ul>
                        <li><strong>Fuerza de Choque:</strong> Tu fuerza principal. Déjala en puerto para ahorrar fuel; saldrá al detectar enemigos.</li>
                        <li><strong>Patrulla:</strong> Barcos rápidos para localizar la flota enemiga. Orden: "Nunca atacar".</li>
                        <li><strong>Submarinos:</strong> Ataque de convoyes en océanos profundos para asfixiar al enemigo.</li>
                    </ul>
                    <br>
                    <p><strong>Meta 1940:</strong> Usa motores nivel 3 y cascos de 1940. La velocidad esquiva disparos. Investiga "Control de Daños" obligatoriamente.</p>
                `,
                tierra: "<h3>🪖 Terrestre</h3><p>Usa anchos de combate de 20 o 40. La artillería es fundamental para romper líneas enemigas.</p>",
                aire: "<h3>✈️ Aéreo</h3><p>La superioridad aérea es vital. Sin ella, tus tanques avanzarán mucho más lento.</p>",
                logistica: "<h3>📦 Logística</h3><p>Construye trenes y camiones. Sin suministros, tus divisiones no podrán pelear.</p>"
            };

            d.innerHTML = info[seccion];
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
