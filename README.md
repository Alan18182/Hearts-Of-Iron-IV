<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Hearts Of Iron IV</title>

<style>

/* RESET */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', sans-serif;
}

/* FONDO */
body {
  background: url('TU_IMAGEN_AQUI.jpg') no-repeat center center/cover;
  color: white;
  overflow: hidden;
}

/* CAPA OSCURA */
body::before {
  content: "";
  position: fixed;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.75);
  z-index: -1;
}

/* HUMO */
body::after {
  content: "";
  position: fixed;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255,255,255,0.05) 10%, transparent 60%);
  animation: humo 20s linear infinite;
  z-index: -1;
}

@keyframes humo {
  from { transform: translate(0,0); }
  to { transform: translate(-200px,-200px); }
}

/* PANTALLAS */
#inicio, #contenido {
  position: absolute;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* TITULO */
h1 {
  font-size: 50px;
  margin-bottom: 20px;
  text-shadow: 0 0 20px rgba(0,150,255,0.8);
}

/* BOTON */
button {
  padding: 15px 40px;
  border: none;
  border-radius: 10px;
  background: #00aaff;
  color: white;
  font-size: 18px;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  background: #0077aa;
  transform: scale(1.1);
  box-shadow: 0 0 20px #00aaff;
}

/* SECCIONES */
.seccion {
  width: 250px;
  margin: 10px;
  padding: 15px;
  background: rgba(0,0,0,0.7);
  border-left: 5px solid #00aaff;
  cursor: pointer;
  transition: 0.3s;
}

.seccion:hover {
  transform: translateX(10px);
  background: rgba(0,0,0,0.9);
  box-shadow: 0 0 15px #00aaff;
}

/* DETALLE */
#detalle {
  margin-top: 20px;
  padding: 20px;
  background: rgba(0,0,0,0.8);
  border-radius: 10px;
  animation: aparecer 0.5s ease;
}

@keyframes aparecer {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}

</style>
</head>

<body>

<!-- INICIO -->
<div id="inicio">
  <h1>⚔️ Hearts Of Iron IV ⚔️</h1>
  <p>Dominá la guerra, controlá el mundo.</p>
  <button onclick="entrar()">Entrar</button>
</div>

<!-- CONTENIDO -->
<div id="contenido" style="display:none;">

  <button onclick="volver()">⬅ Volver</button>

  <h2 style="margin:20px;">Secciones</h2>

  <div class="seccion" onclick="abrirSeccion('marina')">⚓ Marina</div>
  <div class="seccion" onclick="abrirSeccion('tierra')">🪖 Terrestre</div>
  <div class="seccion" onclick="abrirSeccion('aire')">✈ Aéreo</div>
  <div class="seccion" onclick="abrirSeccion('investigaciones')">🔬 Investigaciones</div>
  <div class="seccion" onclick="abrirSeccion('focos')">📜 Focos Nacionales</div>
  <div class="seccion" onclick="abrirSeccion('logistica')">📦 Guía Logística</div>

  <div id="detalle"></div>

</div>

<script>

function entrar() {
  document.getElementById("inicio").style.display = "none";
  document.getElementById("contenido").style.display = "flex";
}

function volver() {
  document.getElementById("contenido").style.display = "none";
  document.getElementById("inicio").style.display = "flex";
  document.getElementById("detalle").innerHTML = "";
}

function abrirSeccion(seccion) {
  let contenido = "";

  if (seccion === "marina") {
    contenido = "<h3>⚓ Marina</h3><p>Dominá los mares con flotas, portaaviones y submarinos.</p>";
  }

  if (seccion === "tierra") {
    contenido = "<h3>🪖 Terrestre</h3><p>Estrategias de infantería, tanques y líneas de frente.</p>";
  }

  if (seccion === "aire") {
    contenido = "<h3>✈ Aéreo</h3><p>Control total del cielo con cazas y bombarderos.</p>";
  }

  if (seccion === "investigaciones") {
    contenido = "<h3>🔬 Investigaciones</h3><p>Desbloqueá tecnología para dominar la guerra.</p>";
  }

  if (seccion === "focos") {
    contenido = "<h3>📜 Focos Nacionales</h3><p>Expandí tu nación con decisiones estratégicas.</p>";
  }

  if (seccion === "logistica") {
    contenido = "<h3>📦 Logística</h3><p>Gestioná suministros, trenes y producción.</p>";
  }

  document.getElementById("detalle").innerHTML = contenido;
}

</script>

</body>
</html>
