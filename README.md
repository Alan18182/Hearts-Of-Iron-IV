<!-- Todo hecho a base para conocimientos sobre el juego. -->
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Hearts Of Iron IV</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">

<style>
body {
  margin: 0;
  font-family: 'Orbitron', sans-serif;
  background: radial-gradient(circle, #0a0a0a, #000000);
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  overflow: hidden;
}

/* EFECTO HUMO SIMPLE (sin imagen externa) */
body::after {
  content: "";
  position: absolute;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255,255,255,0.05) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: humo 20s linear infinite;
}

@keyframes humo {
  from { transform: translate(0,0); }
  to { transform: translate(-200px,-200px); }
}

/* INICIO */
#inicio {
  text-align: center;
  background: rgba(0,0,0,0.6);
  padding: 40px;
  border-radius: 20px;
  box-shadow: 0 0 30px black;
  z-index: 2;
}

h1 {
  font-size: 3em;
  margin-bottom: 20px;
}

p {
  margin-bottom: 20px;
  color: #aaa;
}

button {
  padding: 10px 20px;
  background: #222;
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  transform: scale(1.1);
  background: #444;
}

/* MENU */
#menu {
  display: none;
  position: absolute;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, #020617, #000);
  text-align: center;
  padding-top: 80px;
}

/* BOTON VOLVER */
.volver-btn {
  position: absolute;
  top: 20px;
  left: 20px;
}

/* SECCIONES */
.seccion {
  margin: 15px;
  padding: 15px;
  border: 1px solid #555;
  display: inline-block;
  width: 200px;
  background: rgba(30,30,30,0.7);
  transition: 0.3s;
  cursor: pointer;
  opacity: 0;
  animation: aparecer 1s forwards;
}

.seccion:nth-child(3){animation-delay:0.2s;}
.seccion:nth-child(4){animation-delay:0.4s;}
.seccion:nth-child(5){animation-delay:0.6s;}
.seccion:nth-child(6){animation-delay:0.8s;}
.seccion:nth-child(7){animation-delay:1s;}
.seccion:nth-child(8){animation-delay:1.2s;}

@keyframes aparecer {
  from {opacity:0; transform: translateY(30px);}
  to {opacity:1; transform: translateY(0);}
}

.seccion:hover {
  transform: scale(1.1);
  background: #333;
}
</style>
</head>

<body>

<div id="inicio">
  <h1>⚔️ Hearts Of Iron IV ⚔️</h1>
  <p>Todo lo relacionado con el juego Hearts Of Iron IV de Paradox</p>
  <button onclick="entrar()">Entrar</button>
</div>

<div id="menu">
  <button onclick="volver()" class="volver-btn">⬅️ Volver atrás</button>

  <h2>Secciones</h2>

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
