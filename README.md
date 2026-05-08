<Con el fin de conocimientos del juego.>
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

    .container {
      text-align: center;
      backdrop-filter: blur(10px);
      background: rgba(0,0,0,0.5);
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 0 40px rgba(56,189,248,0.3);
    }

    h1 {
      font-size: 3em;
      color: #38bdf8;
      text-shadow: 0 0 20px #38bdf8;
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
      background: #38bdf8;
      color: black;
      cursor: pointer;
      transition: 0.3s;
      box-shadow: 0 0 15px #38bdf8;
    }

    button:hover {
      transform: scale(1.1);
      background: #0ea5e9;
      box-shadow: 0 0 25px #38bdf8;
    }

    footer {
      margin-top: 20px;
      font-size: 0.8em;
      color: #94a3b8;
    }

    /* PANEL OCULTO */
    #menu {
      display: none;
      position: absolute;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.9);
      top: 0;
      left: 0;
      padding-top: 80px;
      text-align: center;
    }

    .seccion {
      margin: 15px;
      padding: 15px;
      background: rgba(56,189,248,0.1);
      border: 1px solid #38bdf8;
      border-radius: 10px;
      display: inline-block;
      width: 200px;
      transition: 0.3s;
    }

    .seccion:hover {
      transform: scale(1.1);
      background: rgba(56,189,248,0.3);
    }
  </style>
</head>

<body>

  <!-- PANTALLA PRINCIPAL -->
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

  <!-- MENU OCULTO -->
  <div id="menu">

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
  </script>

</body>
</html>
