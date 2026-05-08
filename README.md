<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hearts Of Iron IV - Guía para Principiantes</title>

<style>
/* ----------------------------------------------------
   RESÉTS BÁSICOS PARA QUE NADA SE ESTIRE SOLITO
  ---------------------------------------------------- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

/* ----------------------------------------------------
   CONFIGURACIÓN DEL CUERPO (BODY) Y FONDO
  ---------------------------------------------------- */
body {
  /* 1. Cargamos tu fondo.png */
  background: url('fondo.png') no-repeat center center fixed;
  
  /* 2. Esto es clave: hacemos que el fondo cubra todo sin estirar la imagen */
  background-size: cover;
  
  color: white;
  
  /* 3. Hacemos que la página mida al menos el alto de la pantalla */
  min-height: 100vh;
  
  /* 4. Centramos todo verticalmente (Flexbox) */
  display: flex;
  justify-content: center;
  align-items: center;
  
  /* 5. Capa oscura general para mejorar legibilidad */
  background-color: rgba(0, 0, 0, 0.7); 
  background-blend-mode: darken; /* Mezcla el color negro con la imagen */
}

/* ----------------------------------------------------
   CONTENEDOR PRINCIPAL (EL ENVOLTORIO)
  ---------------------------------------------------- */
.main-wrapper {
  width: 90%;
  max-width: 800px; /* Evita que en pantallas grandes todo sea gigante */
  text-align: center;
  padding: 40px 20px;
  position: relative;
  z-index: 10;
}

/* ----------------------------------------------------
   DISEÑO DE LAS PANTALLAS (INICIO Y CONTENIDO)
  ---------------------------------------------------- */
#inicio, #contenido {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  animation: aparecer 0.6s ease-out;
}

/* ----------------------------------------------------
   TÍTULO PRINCIPAL (EL DE TU CAPTURA)
  ---------------------------------------------------- */
.game-title {
  font-size: clamp(30px, 6vw, 60px); /* Tamaño fluido: min, preferido, max */
  font-weight: 800;
  color: white;
  text-shadow: 0 0 15px rgba(255,255,255,0.5);
  margin-bottom: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 15px;
}

/* Los íconos de las espadas */
.game-title .icon {
  font-size: 0.8em;
  opacity: 0.7;
}

/* SUBTÍTULO */
.subtitle {
  font-size: 1.1rem;
  color: #ccc;
  margin-bottom: 40px;
  font-weight: 400;
}

/* ----------------------------------------------------
   DISEÑO DEL BOTÓN "ENTRAR" (COMO TU CAPTURA)
  ---------------------------------------------------- */
.btn-entrar {
  padding: 15px 50px;
  border: none;
  border-radius: 8px; /* Bordes suaves */
  background-color: #00aaff; /* Azul brillante */
  color: white;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 170, 255, 0.4);
}

.btn-entrar:hover {
  background-color: #0088cc; /* Azul un poco más oscuro */
  transform: translateY(-3px); /* Pequeño salto al pasar el mouse */
  box-shadow: 0 6px 20px rgba(0, 170, 255, 0.6);
}

/* ----------------------------------------------------
   DISEÑO DE LA GRILLA DE SECCIONES
  ---------------------------------------------------- */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); /* Grilla auto-ajustable */
  gap: 15px;
  width: 100%;
  margin-top: 30px;
}

.seccion {
  padding: 20px;
  background: rgba(20, 20, 20, 0.9); /* Fondo negro muy oscuro */
  border-left: 5px solid #00aaff; /* Borde azul a la izquierda */
  border-radius: 4px;
  text-align: left;
  cursor: pointer;
  transition: 0.3s ease;
}

.seccion:hover {
  transform: translateX(8px); /* Se mueve a la derecha */
  background: rgba(30, 30, 30, 0.95);
  box-shadow: 0 0 15px rgba(0, 170, 255, 0.3);
}

/* BOTÓN VOLVER */
.btn-volver {
  padding: 8px 15px;
  border: 1px solid #777;
  background: transparent;
  color: #ccc;
  border-radius: 4px;
  cursor: pointer;
  align-self: flex-start; /* Se alinea a la izquierda */
  margin-bottom: 20px;
  transition: 0.2s;
}

.btn-volver:hover {
  border-color: white;
  color: white;
  background: rgba(255,255,255,0.1);
}

/* ----------------------------------------------------
   DETALLE DE LA SECCIÓN (EL PANEL)
  ---------------------------------------------------- */
#detalle {
  margin-top: 30px;
  width: 100%;
  padding: 25px;
  background: rgba(0, 0, 0, 0.85); /* Fondo muy oscuro para el texto */
  border: 1px dashed #00aaff; /* Borde azul punteado */
  border-radius: 8px;
  text-align: left;
  line-height: 1.7; /* Mejor separación de líneas para leer */
  display: none; /* Se oculta por defecto, se activa con JS */
}

/* Estilos para el texto dentro del detalle */
#detalle h3 { color: #00aaff; margin-bottom: 10px; font-size: 1.5rem; }
#detalle p { color: #ddd; font-size: 1rem; }

/* ----------------------------------------------------
   ANIMACIÓN DE APARICIÓN
  ---------------------------------------------------- */
@keyframes aparecer {
  from { opacity: 0; transform: translateY(15px); }
  to { opacity: 1; transform: translateY(0); }
}

</style>
</head>

<body>

    <div class="main-wrapper">

        <div id="inicio">
            <h1 class="game-title">
        <span class="icon">⚔️</span> 
        HEARTS OF IRON IV
        <span class="icon">⚔️</span>
      </h1>
            <p class="subtitle">Dominá la guerra, controlá el mundo.</p>
            <button class="btn-entrar" onclick="entrar()">Entrar</button>
    </div>

        <div id="contenido" style="display:none;">
            <button class="btn-volver" onclick="volver()">⬅ Volver</button>
      
            <h2 style="margin-bottom:20px; font-weight: 500;">Secciones de Mando</h2>

            <div class="menu-grid">
        <div class="seccion" onclick="abrir('marina')">⚓ Marina</div>
        <div class="seccion" onclick="abrir('tierra')">🪖 Terrestre</div>
        <div class="seccion" onclick="abrir('aire')">✈ Aéreo</div>
        <div class="seccion" onclick="abrir('investigaciones')">🔬 Investigaciones</div>
        <div class="seccion" onclick="abrir('focos')">📜 Focos Nacionales</div>
        <div class="seccion" onclick="abrir('logistica')">📦 Guía Logística</div>
      </div>

            <div id="detalle"></div>
    </div>

  </div>     <script>
    // Función para cambiar de la pantalla de inicio a la de contenido
    function entrar() {
      document.getElementById("inicio").style.display = "none";
      document.getElementById("contenido").style.display = "flex";
    }

    // Función para volver a la pantalla de inicio
    function volver() {
      document.getElementById("contenido").style.display = "none";
      document.getElementById("inicio").style.display = "flex";
      // Ocultamos el panel de detalle por si estaba abierto
      document.getElementById("detalle").style.display = "none";
    }

    // Función para abrir una sección y mostrar su contenido en el panel
    function abrir(tipo) {
      const detallePanel = document.getElementById("detalle");
      // Mostramos el panel
      detallePanel.style.display = "block";

      // Objeto con la información de cada sección
      const info = {
        marina: "<h3>⚓ Marina</h3><p>La clave para principiantes son los submarinos. Úsalos para hundir los convoyes enemigos y estrangular su economía.</p>",
        tierra: "<h3>🪖 Terrestre</h3><p>Mantén tus divisiones con un 'Combat Width' (Ancho de combate) de 20 o 40. No olvides la artillería de apoyo.</p>",
        aire: "<h3>✈ Aéreo</h3><p>La superioridad aérea es vital. Sin ella, tus tanques avanzarán más lento y tus fábricas serán bombardeadas.</p>",
        investigaciones: "<h3>🔬 Investigaciones</h3><p>Prioriza la industria y la computación. Más fábricas y más velocidad de investigación te darán la victoria.</p>",
        focos: "<h3>📜 Focos Nacionales</h3><p>Son tu árbol de decisiones políticas y económicas. Elige con cuidado qué camino tomará tu nación.</p>",
        logistica: "<h3>📦 Guía Logística</h3><p>Si la caja de suministros está en rojo, tus tropas no tienen armas. Construye trenes y centros de suministros.</p>"
      };

      // Insertamos el contenido correspondiente
      detallePanel.innerHTML = info[tipo];
    }
  </script>

</body>
</html>
