<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>volvemos</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <style>
    /* ===== Reset y tipografía ===== */
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap');
    html, body { margin: 0; padding: 0; height: 100%; overflow: hidden; }
    body {
      font-family: 'Orbitron', sans-serif;
      background: url('https://images.unsplash.com/photo-1446824505046-e43605ffb17f') 
        no-repeat center center fixed;
      background-size: cover;
      position: relative;
      color: #0e0303;
      text-align: center;
    }

    /* ===== Pájaros volando ===== */
    .bird-container {
      position: absolute;
      left: -10vw;
      transform: scale(0.4);
      animation: fly 20s linear infinite;
      pointer-events: none;
      z-index: 0;
    }
    .bird { 
      width: 88px; height: 125px;
      background: url('https://s3-us-west-2.amazonaws.com/s.cdpn.io/174479/bird-cells-new.svg') 
        no-repeat 0 0; background-size: auto 100%;
      animation: fly-cycle 1s steps(10) infinite;
    }
    @keyframes fly { 0% { left: -10vw } 100% { left: 110vw } }
    @keyframes fly-cycle { 100% { background-position: -900px 0 } }

    /* ===== Contenedor de contenido ===== */
    .main-content {
      position: relative;
      z-index: 1;
      padding: 80px 20px;
    }

    .brand {
      font-size: 2.5rem;
      color: #010c0c;
      text-shadow: 0 0 10px #f1f3f3, 0 0 20px #f6f8f8;
      margin-bottom: 20px;
    }

    /* ===== Máquina de escribir ===== */
    .typewriter {
      display: inline-block;
      overflow: hidden;
      border-right: 2px solid rgb(8, 0, 0);
      white-space: nowrap;
      width: 0; /* inicia en 0 */
      animation: typing 2s steps(8) forwards, blink-caret .75s step-end infinite;
      font-size: 2.5rem;
      color: #0c0404;
      margin: 0 auto 20px;
    }
    @keyframes typing {
      from { width: 0 }
      to   { width: 8ch } /* "Volvemos" tiene 8 caracteres */
    }
    @keyframes blink-caret {
      50% { border-color: transparent }
    }

    /* ===== Cuenta regresiva y lista ===== */
    #countdown {
      font-size: 2rem;
      color: red;
      margin-bottom: 30px;
    }
    h2 {
      font-size: 1.5rem;
      text-shadow: 0 0 5px rgb(243, 242, 242);
      margin-bottom: 10px;
    }
    ul {
      list-style: none;
      padding: 0;
      margin: 0 auto;
      max-width: 300px;
      font-size: 1.1rem;
      color: rgb(14, 1, 1);
    }
    ul li {
      margin: 5px 0;
      transition: color .3s;
    }
    ul li:hover {
      color: #0c0101;
    }
  </style>
</head>
<body>
  <!-- 3 pájaros con delays distintos -->
  <div class="bird-container" style="top:20%; animation-delay: 0s;">
    <div class="bird"></div>
  </div>
  <div class="bird-container" style="top:35%; animation-delay: 6s;">
    <div class="bird"></div>
  </div>
  <div class="bird-container" style="top:50%; animation-delay: 12s;">
    <div class="bird"></div>
  </div>

  <!-- Contenido principal -->
  <div class="main-content">
    <div class="brand">vapeando sv</div>
    <div class="typewriter">Volvemos</div>
    <div id="countdown">Cargando...</div>
    <h2>Productos a ingresar en el restock:</h2>
    <ul>
      <li>Ignite</li>
      <li>Geek Bar</li>
      <li>Elf Bar</li>
      <li>Nik Bar</li>
      <li>Nexa</li>
    </ul>
  </div>

  <!-- Script de cuenta regresiva -->
  <script>
    const target = new Date("June 1, 2025 00:00:00").getTime();
    const el = document.getElementById("countdown");
    setInterval(() => {
      const d = new Date().getTime(), diff = target - d;
      if (diff < 0) { el.innerText = "¡Ya volvimos!"; return; }
      const days = Math.floor(diff / 86400000),
            hrs  = Math.floor((diff % 86400000) / 3600000),
            mins = Math.floor((diff % 3600000) / 60000),
            secs = Math.floor((diff % 60000) / 1000);
      el.innerText = `${days}d ${hrs}h ${mins}m ${secs}s`;
    }, 1000);
  </script>
</body>
</html>
