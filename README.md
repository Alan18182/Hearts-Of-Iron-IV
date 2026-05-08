<!-- Todo hecho a base para conocimientos sobre el juego. -->
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Hearts Of Iron IV</title>

  <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      height: 100vh;
      background: url('fondo.png') no-repeat center center/cover;
      font-family: 'Orbitron', sans-serif;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      overflow: hidden;
    }

    /* OSCURECER */
    body::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(0,0,0,0.8) 20%, rgba(0,0,0,0.95) 80%);
      z-index: 1;
    }

    /* HUMO */
    body::after {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background: url('https://i.imgur.com/8bKQX3K.png');
      opacity: 0.15;
      animation: humo 60s linear infinite;
      z-index: 1;
    }

    @keyframes humo {
      from { transform: translate(0,0); }
      to { transform: translate(-500px, -300px); }
    }

    .container {
      text-align: center;
      backdrop-filter: blur(8px);
      background: rgba(0,0,0,0.6);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 0 40px rgba(0,0,0,0.9);
      z-index: 2;
      animation: aparecer 1.5s ease;
    }

    @keyframes aparecer {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    h1 {
      font-size: 3em;
      color: #94a3b8;
      text-shadow: 0 0 15px black;
      margin-bottom: 20px;
    }

    p {
      font-size: 1.2em;
      color: #cbd5f5;
      margin-bottom: 30px;
    }

    button {
      padding: 12px 25px;
      font-size: 1em;
      border: none;
      border-radius: 10px;
      background: #1e293b;
      color: white;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      transform: scale(1.1);
      background: #334155;
    }

    footer {
      margin-top: 20px;
      font-size: 0.8em;
      color: #64748b;
    }

    /* MENU */
    #menu {
      display: none;
      position: absolute;
      width: 100%;
      height: 100%;
      background: radial-gradient(circle, #020617, #000000);
      top: 0;
      left: 0;
      padding-top: 80px;
      text-align: center;
      z-index: 2;
    }

    /* BANDERAS */
    #menu::before {
      content: "";
      position: absolute;
      width: 200%;
      height: 200%;
      background: linear-gradient(120deg, rgba(255,255,255,0.03), transparent);
      animation: bandera 10s infinite linear;
    }

    @keyframes bandera {
      0% { transform: translateX(0); }
      100% { transform: translateX(-300px); }
    }

    /* BOTON VOLVER */
    .volver-btn {
      position: absolute;
      top: 20px;
      left: 20px;
      padding: 10px 20px;
      background: #1e293b;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      transition: 0.3s;
      z-index: 3;
    }

    .volver-btn:hover {
      background: #334155;
      transform: scale(1.05);
    }

    .seccion {
      margin: 15px;
      padding: 15px;
      background: rgba(30,41,59,0.6);
      border: 1px solid #475569;
      border-radius: 10px;
      display: inline-block;
      width: 200px;
      transition: 0.3s;
      cursor: pointer;
      animation: entradaSeccion 1s ease forwards;
      opacity: 0;
    }

    .seccion:nth-child(3) { animation-delay: 0.2s; }
    .seccion:nth-child(4) { animation-delay: 0.4s; }
    .seccion:nth-child(5) { animation-delay: 0.6s; }
    .seccion:nth-child(6) { animation-delay: 0.8s; }
    .seccion:nth-child(7) { animation-delay: 1s; }
    .seccion:nth-child(8) { animation-delay: 1.2s; }

    @keyframes entradaSeccion {
      from { opacity: 0; transform: translateY(40px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .seccion:hover {
      transform: scale(1.1) rotate(-1deg);
      background: rgba(51,65,85,0.9);
      box-shadow: 0 0 15px black;
    }

  </style>
</head>

<body>

  <!-- INICIO -->
  <div class="container" id="inicio">
    <h1>⚔️ Hearts Of Iron IV ⚔️</h1>
    
    <p>
      Todo lo relacionado con el juego Hearts Of Iron IV de Paradox
    </p>

    <button onclick="entrar()">Entrar</button>

    <footer>
      Fan page no oficial
    </footer>
  </div>

  <!-- MENU -->
  <div id="menu">

    <button onclick="volver()" class="volver-btn">⬅️ Volver atrás</button>

    <h1>📚 Secciones</h1>

    <div class="seccion">⚓ Marina</div>
    <div class="seccion">🪖 Terrestre</div>
    <div class="seccion">✈️ Aéreo</div>
    <div class="seccion">🔬 Investigaciones</div>
    <div class="seccion">🏛️ Focos Nacionales</div>
    <div class="seccion">📦 Guía Logística</div>

  </div>

  <script>
    function entrar() {
      document.getElementById("inicio").style.display = "none";
      document.getElementById("menu").style.display = "block";
    }

    function volver() {
      document.getElementById("menu").style.display = "none";
      document.getElementById("inicio").style.display = "flex";
    }
  </script>

</body>
</html>
