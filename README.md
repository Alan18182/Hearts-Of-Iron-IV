<A fines de entretenimiento y conocimiento.>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Cuartel de Mando</title>
    <style>
        /* --- ESTILOS VISUALES TOTALMENTE MANTENIDOS --- */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            /* Mantenemos tu fondo.png */
            background: url('fondo.png') no-repeat center center fixed;
            background-size: cover;
            color: white;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
        }

        /* Capa oscura para legibilidad */
        .capa-oscura {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.78);
            z-index: 1;
        }

        /* Efecto de humo animado visual */
        .humo {
            position: fixed;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.03) 10%, transparent 60%);
            animation: humo-mov 25s linear infinite;
            z-index: 2;
            pointer-events: none;
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-150px,-150px); }
        }

        /* Contenedor de la interfaz */
        .wrapper {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 90%;
            max-width: 850px;
            padding: 20px;
        }

        /* Título con el brillo azul neón visual */
        h1 {
            font-size: clamp(35px, 8vw, 60px);
            text-shadow: 0 0 25px #00aaff;
            letter-spacing: 2px;
            margin-bottom: 10px;
        }

        .slogan {
            font-size: 1.2rem;
            margin-bottom: 40px;
            opacity: 0.8;
            color: #ddd;
        }

        /* Botón de entrada azul visual */
        .btn-entrar {
            padding: 18px 55px;
            background: #00aaff;
            border: none;
            color: white;
            font-size: 20px;
            font-weight: bold;
            text-transform: uppercase;
            cursor: pointer;
            border-radius: 8px;
            transition: 0.3s;
            box-shadow: 0 0 20px rgba(0, 170, 255, 0.5);
        }

        .btn-entrar:hover {
            transform: scale(1.05);
            background: #0088cc;
            box-shadow: 0 0 35px #00aaff;
        }

        /* Pantallas de Navegación */
        #inicio { display: block; }
        #contenido { display: none; flex-direction: column; align-items: center; animation: fadeIn 0.6s ease; }

        /* Estilo de las tarjetas de menú visual */
        .grid-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 20px;
        }

        .tarjeta {
            padding: 20px;
            background: rgba(15, 15, 15, 0.9);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            transition: 0.3s;
            text-align: left;
            font-weight: bold;
        }

        .tarjeta:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
        }

        /* Panel de Detalle visual con la info */
        #detalle {
            margin-top: 25px;
            padding: 25px;
            background: rgba(0, 0, 0, 0.95);
            border: 1px solid #00aaff;
            border-radius: 5px;
            text-align: left;
            display: none;
            line-height: 1.7;
            animation: fadeIn 0.4s ease;
            max-height: 500px;
            overflow-y: auto;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 15px; font-size: 1.6rem; }
        #detalle ul { margin-left: 20px; margin-top: 10px; }
        #detalle li { margin-bottom: 10px; color: #eee; }

        /* Botón volver visual */
        .btn-volver {
            background: transparent;
            border: 1px solid #ffffff;
            color: white;
            padding: 8px 18px;
            cursor: pointer;
            margin-bottom: 25px;
            align-self: flex-start;
            transition: 0.3s;
        }

        .btn-volver:hover { background: white; color: black; }

        /* Animaciones */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
    </style>
</head>
<body>

    <div class="capa-oscura"></div>
    <div class="humo"></div>

    <div class="wrapper">
        <div id="inicio">
            <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
            <p class="slogan">Guía de Mando y Estrategia Naval y Terrestre</p>
            <button class="btn-entrar" onclick="entrar()">ENTRAR</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="volver()">⬅ VOLVER</button>
            <div class="grid-menu">
                <div class="tarjeta" onclick="abrir('marina')">⚓ Marina</div>
                <div class="tarjeta" onclick="abrir('tierra')">🪖 Terrestre</div>
                <div class="tarjeta" onclick="abrir('aire')">✈️ Aéreo</div>
                <div class="tarjeta" onclick="abrir('logistica')">📦 Logística</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        // Función para entrar
        function entrar() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
        }

        // Función para volver al inicio
        function volver() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
        }

        // Función para abrir secciones e insertar la info de los videos
        function abrir(seccion) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const info = {
                marina: `
                    <h3>⚓ ESTRATEGIA NAVAL DEFINITIVA</h3>
                    <p><strong>Estructura:</strong> Ratio 4:1 de pantallas por buque pesado. Usa cruceros ligeros rápidos para patrulla y mantén la fuerza de choque en puerto.</p>
                `,
                tierra: `
                    <h3>🪖 MANUAL DEL EJÉRCITO</h3>
                    <p><strong>Estadísticas:</strong> Se decide por Organización y Ataque Ligero/Pesado. El clima (frío y barro) es tu peor enemigo.</p>
                `,
                aire: `<h3>✈️ SUPERIORIDAD AÉREA</h3><p>La superioridad aérea protege a tus tropas y permite el CAS, vital para ganar batallas.</p>`,
                logistica: `
                    <h3>📦 LOGÍSTICA</h3>
                    <p><strong>Suministro:</strong> Conecta todo a la capital por tren. Cambia caballos por camiones para mayor alcance en el frente.</p>
                `
            };

            d.innerHTML = info[seccion];
            
            // Auto-scroll suave para ver la info
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
