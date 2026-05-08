<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Centro de Mando</title>
    <style>
        /* --- ESTÉTICA VISUAL (SIN TOCAR) --- */
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
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }

        .capa-oscura {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1;
        }

        .humo {
            position: fixed;
            width: 200%; height: 200%;
            background: radial-gradient(circle, rgba(255,255,255,0.03) 10%, transparent 60%);
            animation: humo-mov 25s linear infinite;
            z-index: 2;
            pointer-events: none; /* CRÍTICO: Esto permite hacer clic a través del humo */
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-100px,-100px); }
        }

        .wrapper {
            position: relative;
            z-index: 10; /* Por encima de la capa oscura y el humo */
            text-align: center;
            width: 90%;
            max-width: 850px;
        }

        h1 {
            font-size: clamp(30px, 8vw, 60px);
            text-shadow: 0 0 25px #00aaff;
            margin-bottom: 20px;
            letter-spacing: 2px;
        }

        .btn-entrar {
            padding: 20px 60px;
            background: #00aaff;
            border: none;
            color: white;
            font-size: 22px;
            font-weight: bold;
            cursor: pointer;
            border-radius: 5px;
            box-shadow: 0 0 20px rgba(0, 170, 255, 0.6);
            transition: 0.3s;
            position: relative;
            z-index: 20; /* Asegura prioridad de clic */
        }

        .btn-entrar:hover {
            transform: scale(1.05);
            box-shadow: 0 0 40px #00aaff;
        }

        /* --- PANELES DE NAVEGACIÓN --- */
        #inicio { display: block; }
        #contenido { display: none; flex-direction: column; align-items: center; }

        .grid-menu {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
            gap: 15px;
            width: 100%;
            margin-top: 30px;
        }

        .tarjeta {
            padding: 20px;
            background: rgba(15, 15, 15, 0.9);
            border-left: 5px solid #00aaff;
            cursor: pointer;
            transition: 0.3s;
            text-align: left;
        }

        .tarjeta:hover {
            background: rgba(0, 170, 255, 0.2);
            transform: translateX(10px);
        }

        #detalle {
            margin-top: 25px;
            padding: 25px;
            background: rgba(0, 0, 0, 0.95);
            border: 1px solid #00aaff;
            display: none;
            text-align: left;
            line-height: 1.7;
            max-height: 450px;
            overflow-y: auto;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 10px; }
        #detalle ul { margin-left: 20px; }

        .btn-volver {
            background: none;
            border: 1px solid white;
            color: white;
            padding: 8px 18px;
            cursor: pointer;
            margin-bottom: 20px;
            align-self: flex-start;
        }
    </style>
</head>
<body>

    <div class="capa-oscura"></div>
    <div class="humo"></div>

    <div class="wrapper">
        <div id="inicio">
            <h1>⚔️ HEARTS OF IRON IV ⚔️</h1>
            <p style="margin-bottom: 40px; opacity: 0.8;">GUÍA TÁCTICA Y LOGÍSTICA</p>
            <button class="btn-entrar" onclick="ejecutarEntrada()">ENTRAR</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="volverInicio()">⬅ VOLVER</button>
            <div class="grid-menu">
                <div class="tarjeta" onclick="mostrarInfo('marina')">⚓ MARINA</div>
                <div class="tarjeta" onclick="mostrarInfo('tierra')">🪖 TERRESTRE</div>
                <div class="tarjeta" onclick="mostrarInfo('aire')">✈️ AÉREO</div>
                <div class="tarjeta" onclick="mostrarInfo('logistica')">📦 LOGÍSTICA</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        // Función entrar corregida
        function ejecutarEntrada() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
            document.body.style.overflow = "auto";
        }

        // Función volver corregida
        function volverInicio() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
            document.body.style.overflow = "hidden";
        }

        // Función de información actualizada con Logística Completa
        function mostrarInfo(seccion) {
            const panel = document.getElementById("detalle");
            panel.style.display = "block";
            
            const datos = {
                marina: `<h3>⚓ ESTRATEGIA NAVAL</h3><p>Usa pantallas en ratio 4:1. Fuerza de choque en puerto y submarinos en océanos profundos.</p>`,
                tierra: `<h3>🪖 EJÉRCITO TERRESTRE</h3><p>El combate depende de la Organización y el Ancho de Combate. Ataca desde varios flancos para maximizar el daño.</p>`,
                aire: `<h3>✈️ SUPERIORIDAD AÉREA</h3><p>Vital para proteger tus suministros y permitir que tus tanques avancen sin penalizaciones.</p>`,
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Cadena de Suministro:</strong> Los recursos viajan desde la capital hasta los Centros de Suministro y Bases Navales mediante trenes y convoys.</p>
                    
                    <ul>
                        <li><strong>Motorización:</strong> Cambia de caballos a camiones (Nivel 1 o 2) en los hubs para expandir el rango de entrega de suministros.</li>
                        <li><strong>Trenes:</strong> El tren civil es el básico, pero el tren blindado es vital para resistir bombardeos logísticos enemigos.</li>
                        <li><strong>Vías Férreas:</strong> Sube el nivel de los ferrocarriles para eliminar "cuellos de botella" en zonas de alto consumo.</li>
                        <li><strong>Suministro Aéreo:</strong> Usa aviones de transporte para crear puentes aéreos hacia tropas cercadas.</li>
                    </ul>
                    <p><em>Consejo:</em> Mantén el desempeño logístico por encima del 70% para evitar el colapso de tus divisiones.</p>
                `
            };

            panel.innerHTML = datos[seccion];
            panel.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
