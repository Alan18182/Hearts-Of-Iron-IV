<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hearts Of Iron IV - Cuartel de Mando</title>
    <style>
        /* --- ESTÉTICA VISUAL (BLOQUEADA) --- */
        * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }

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
            pointer-events: none;
        }

        @keyframes humo-mov {
            from { transform: translate(0,0); }
            to { transform: translate(-100px,-100px); }
        }

        .wrapper {
            position: relative;
            z-index: 10;
            text-align: center;
            width: 95%;
            max-width: 900px;
        }

        h1 {
            font-size: clamp(30px, 8vw, 60px);
            text-shadow: 0 0 25px #00aaff;
            margin-bottom: 20px;
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
            z-index: 30;
        }

        .btn-entrar:hover { transform: scale(1.05); box-shadow: 0 0 40px #00aaff; }

        /* --- NAVEGACIÓN --- */
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
            font-weight: bold;
        }

        #detalle {
            margin-top: 25px;
            padding: 30px;
            background: rgba(0, 0, 0, 0.95);
            border: 1px solid #00aaff;
            display: none;
            text-align: left;
            line-height: 1.7;
            max-height: 550px;
            overflow-y: auto;
        }

        #detalle h3 { color: #00aaff; margin-bottom: 15px; border-bottom: 1px solid #333; padding-bottom: 5px; }
        #detalle strong { color: #00ccff; }
        #detalle ul { margin: 15px 0 15px 25px; }
        #detalle li { margin-bottom: 8px; }

        .btn-volver {
            background: none;
            border: 1px solid white;
            color: white;
            padding: 10px 20px;
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
            <p style="margin-bottom: 40px; opacity: 0.8;">MANUAL ESTRATÉGICO DE OPERACIONES</p>
            <button class="btn-entrar" onclick="accesoSeguro()">ENTRAR</button>
        </div>

        <div id="contenido">
            <button class="btn-volver" onclick="regresar()">⬅ VOLVER</button>
            <div class="grid-menu">
                <div class="tarjeta" onclick="cargarSeccion('marina')">⚓ MARINA</div>
                <div class="tarjeta" onclick="cargarSeccion('tierra')">🪖 TERRESTRE</div>
                <div class="tarjeta" onclick="cargarSeccion('aire')">✈️ AÉREO</div>
                <div class="tarjeta" onclick="cargarSeccion('logistica')">📦 LOGÍSTICA</div>
            </div>
            <div id="detalle"></div>
        </div>
    </div>

    <script>
        function accesoSeguro() {
            document.getElementById("inicio").style.display = "none";
            document.getElementById("contenido").style.display = "flex";
            document.body.style.overflow = "auto";
        }

        function regresar() {
            document.getElementById("inicio").style.display = "block";
            document.getElementById("contenido").style.display = "none";
            document.getElementById("detalle").style.display = "none";
            document.body.style.overflow = "hidden";
        }

        function cargarSeccion(s) {
            const d = document.getElementById("detalle");
            d.style.display = "block";
            
            const info = {
                marina: `<h3>⚓ ESTRATEGIA NAVAL</h3><p>Ratio 4:1 de pantallas. Patrulla con cruceros ligeros y usa la fuerza de choque para el combate decisivo.</p>`,
                tierra: `
                    <h3>🪖 EJÉRCITO Y COMBATE TERRESTRE</h3>
                    <p><strong>Mecánicas de Batalla:</strong> Las divisiones luchan según su Ataque Ligero, Pesado y Defensa. Se pierde cuando la Organización (barra verde) o Fuerza (barra naranja) llega a cero.</p>
                    <ul>
                        <li><strong>Ancho de Combate:</strong> Determinado por el terreno. Atacar desde múltiples direcciones suma +35 de ancho por cada lado adicional, permitiendo usar más reservas.</li>
                        <li><strong>Terrenos:</strong> Selva y Pantano son los peores; Llanura es el mejor para avanzar. Ciudades y Colinas ofrecen bonos defensivos.</li>
                        <li><strong>Generales:</strong> Nunca dejes ejércitos sin general. Ganan rasgos por experiencia (líder de infantería, montañero) y suben niveles de ataque, defensa, planificación y logística.</li>
                        <li><strong>Doctrinas Terrestres:</strong> 
                            <ul>
                                <li><em>Guerra Móvil:</em> Rapidez y blindados, decae en late game.</li>
                                <li><em>Fuego Superior:</em> Máximo ataque ligero, ideal contra la IA.</li>
                                <li><em>Gran Plan:</em> Bonos de planificación y defensa.</li>
                                <li><em>Asalto en Masa:</em> Reduce el ancho de la infantería, ideal para "avalanchas humanas".</li>
                            </ul>
                        </li>
                    </ul>`,
                aire: `<h3>✈️ SUPERIORIDAD AÉREA</h3><p>Los cazas son obligatorios para evitar penalizadores de movimiento y permitir el bombardeo táctico.</p>`,
                logistica: `
                    <h3>📦 LOGÍSTICA Y SUMINISTROS</h3>
                    <p><strong>Sistema de Red:</strong> El suministro fluye desde la Capital hacia los Hubs (centros de suministros) por vías férreas o hacia puertos por convoys.</p>
                    <ul>
                        <li><strong>Motorización de Hubs:</strong> Puedes configurar cada centro para usar caballos, camiones o motorización total. Esto extiende el "alcance" del suministro hacia las provincias cercanas.</li>
                        <li><strong>Ferrocarriles:</strong> Si hay cuellos de botella, mejora el nivel de las vías. El nivel de suministro que llega depende del nivel más bajo de vía en la ruta hacia la capital.</li>
                        <li><strong>Trenes:</strong> Produce Trenes Civiles (estándar), de Austeridad (baratos) o Blindados (resistentes a ataques aéreos).</li>
                        <li><strong>Puentes Aéreos:</strong> Aviones de transporte pueden suministrar tropas aisladas o cercadas si tienes superioridad aérea.</li>
                        <li><strong>Compañía de Logística:</strong> Indispensable en frentes grandes (Rusia/África) para reducir el consumo de suministros y combustible de la división.</li>
                    </ul>
                    <p><strong>Dato Crítico:</strong> El desempeño logístico debe estar siempre arriba del 70%. Los cuadros de cajas amarillas/rojas en el mapa indican dónde el suministro es insuficiente para atacar.</p>`
            };

            d.innerHTML = info[s];
            d.scrollIntoView({ behavior: 'smooth' });
        }
    </script>
</body>
</html>
