<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Carta de San Valentín</title>
  <script src="https://cdn.jsdelivr.net/npm/fireworks-js@2.x/dist/index.umd.js"></script>
  <script src="https://unpkg.com/fireworks-js@2.x/dist/index.umd.js"></script>
  <style>
    /* Estilos existentes */
    #envelope {
      margin: 150px;
      position: relative;
      width: 280px;
      height: 180px;
      border-bottom-left-radius: 6px;
      border-bottom-right-radius: 6px;
      margin-left: auto;
      margin-right: auto;
      top: 150px;
      background-color: #f9c5c8;
      box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2);
      transition: transform 1s ease, opacity 1s ease;
      z-index: 2;
    }

    .front {
      position: absolute;
      width: 0;
      height: 0;
      z-index: 3;
    }

    .flap {
      border-left: 140px solid transparent;
      border-right: 140px solid transparent;
      border-bottom: 82px solid transparent;
      border-top: 98px solid #ff3333;
      transform-origin: top;
      pointer-events: none;
    }

    .pocket {
      border-left: 140px solid #ff9999;
      border-right: 140px solid #ff9999;
      border-bottom: 90px solid #fd8787;
      border-top: 90px solid transparent;
      border-bottom-left-radius: 6px;
      border-bottom-right-radius: 6px;
    }

    .letter {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%) scale(0.8);
      background-color: #f9c5c8;
      width: 90%;
      max-width: 400px;
      height: auto;
      border-radius: 6px;
      box-shadow: 0 2px 26px rgba(0, 0, 0, 0.12);
      opacity: 0;
      z-index: 3;
      transition: opacity 1s ease, transform 1s ease;
      padding: 20px;
    }

    .letter:after {
      content: "";
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      background-image: none;
    }

    .open .letter {
      opacity: 1;
      transform: translate(-50%, -50%) scale(1);
    }

    .open #envelope {
      transform: translateY(-1000px) rotate(30deg);
      opacity: 0;
    }

    .flower {
      display: block;
      margin: 10px auto;
      width: 150px;
      height: auto;
    }

    .hearts {
      position: absolute;
      top: 90px;
      left: 0;
      right: 0;
      z-index: 2;
    }

    .heart {
      position: absolute;
      bottom: 0;
      right: 10%;
      pointer-events: none;
    }

    .heart:before,
    .heart:after {
      position: absolute;
      content: "";
      left: 50px;
      top: 0;
      width: 50px;
      height: 80px;
      background: #D00000;
      border-radius: 50px 50px 0 0;
      transform: rotate(-45deg);
      transform-origin: 0 100%;
      pointer-events: none;
    }

    .heart:after {
      left: 0;
      transform: rotate(45deg);
      transform-origin: 100% 100%;
    }

    .close .heart {
      opacity: 0;
      -webkit-animation: none;
              animation: none;
    }

    .a1 {
      left: 20%;
      transform: scale(0.6);
      opacity: 1;
      -webkit-animation: slideUp 4s linear 1, sideSway 2s ease-in-out 4 alternate;
      -moz-animation: slideUp 4s linear 1, sideSway 2s ease-in-out 4 alternate;
      -webkit-animation-fill-mode: forwards;
              animation-fill-mode: forwards;
      -webkit-animation-delay: 0.7s;
              animation-delay: 0.7s;
    }

    .a2 {
      left: 55%;
      transform: scale(1);
      opacity: 1;
      -webkit-animation: slideUp 5s linear 1, sideSway 4s ease-in-out 2 alternate;
      -moz-animation: slideUp 5s linear 1, sideSway 4s ease-in-out 2 alternate;
      -webkit-animation-fill-mode: forwards;
              animation-fill-mode: forwards;
      -webkit-animation-delay: 0.7s;
              animation-delay: 0.7s;
    }

    .a3 {
      left: 10%;
      transform: scale(0.8);
      opacity: 1;
      -webkit-animation: slideUp 7s linear 1, sideSway 2s ease-in-out 6 alternate;
      -moz-animation: slideUp 7s linear 1, sideSway 2s ease-in-out 6 alternate;
      -webkit-animation-fill-mode: forwards;
              animation-fill-mode: forwards;
      -webkit-animation-delay: 0.7s;
              animation-delay: 0.7s;
    }

    @-webkit-keyframes slideUp {
      0% {
        top: 0;
      }
      100% {
        top: -600px;
      }
    }
    @keyframes slideUp {
      0% {
        top: 0;
      }
      100% {
        top: -600px;
      }
    }
    @-webkit-keyframes sideSway {
      0% {
        margin-left: 0px;
      }
      100% {
        margin-left: 50px;
      }
    }
    @keyframes sideSway {
      0% {
        margin-left: 0px;
      }
      100% {
        margin-left: 50px;
      }
    }
    body {
      background-color: #f7d9da;
    }

    .envlope-wrapper {
      height: 380px;
    }

    .reset {
      text-align: center;
      margin-top: 40px;
    }

    .reset button {
      font-weight: 800;
      font-style: normal;
      transition: all 0.1s linear;
      -webkit-appearance: none;
      background-color: transparent;
      border: solid 2px #ff5757;
      border-radius: 4px;
      color: #ff5757;
      display: inline-block;
      font-size: 16px;
      text-transform: uppercase;
      margin: 10px;
      padding: 15px 30px;
      line-height: 1em;
      text-decoration: none;
      min-width: 150px;
      cursor: pointer;
      position: relative;
      z-index: 1000;
    }

    .reset button:hover {
      background-color: #fc9d9d;
      color: #a10000;
    }

    .fireworks {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      pointer-events: none;
      z-index: 999;
    }

    .letter-content {
      font-size: 18px;
      font-weight: 600;
      line-height: 1.6;
      color: #333;
    }

    .poem {
      font-style: italic;
      text-align: center;
      margin: 20px 0;
    }

    @media (max-width: 768px) {
      #envelope {
        margin: 50px auto;
        top: 100px;
      }

      .letter {
        width: 80%;
        max-width: 300px;
      }

      .flower {
        width: 100px;
      }

      .reset {
        margin-top: 300px;
      }
    }

    @media (max-width: 480px) {
      #envelope {
        margin: 30px auto;
        top: 80px;
      }

      .letter {
        width: 90%;
        max-width: 250px;
      }

      .flower {
        width: 80px;
      }

      .reset {
        margin-top: 250px;
      }
    }
  </style>
</head>
<body>
<div class="fireworks"></div>
<div class="envelope-wrapper">
    <div id="envelope" class="close">
        <div class="front flap"></div>
        <div class="front pocket"></div>
        <div class="letter">
            <div class="paper">
                <h2 class="letter-title"><b><i>Para Azalia Ceballos</i></b></h2>
                <p class="letter-content">Querida Azalia,</p>
                <p class="letter-content">Espero que este pequeño detalle ilumine tu día.</p>
                <p class="letter-content">En este día tan especial, quiero regalarte un poema:</p>
                <p class="letter-content poem">
                    "Tu belleza es como el sol al amanecer,<br>
                    iluminas mi mundo con tu ser.<br>
                    Cada mirada tuya es un regalo,<br>
                    y en tu sonrisa encuentro mi mayor halago.<br>
                    Eres la estrella que guía mi camino,<br>
                    y en tu presencia, todo es divino."
                </p>
                <p class="letter-content">Te veo poco, pero te pienso mas de lo que quiero. 😉</p>
                <p class="letter-content">Con todo mi cariño,</p>
                <p class="letter-content">Eric RV</p>
                <img class="flower" src="https://raw.githubusercontent.com/EricRV33/Imagenes/f46e30ae51825a64637c6fb78a751dc0309aa7a8/R.jpg" alt="Flores">
            </div>
        </div>
        <div class="hearts">
            <div class="heart a1"></div>
            <div class="heart a2"></div>
            <div class="heart a3"></div>
        </div>
    </div>
</div>
<div class="reset">
    <button id="open">Abrir</button>
    <button id="reset">Reiniciar</button>
</div>
<script>
// Función para abrir la carta
document.getElementById("open").addEventListener("click", function() {
    const envelope = document.getElementById("envelope");
    envelope.classList.add("open");
    envelope.classList.remove("close");
    document.getElementById("open").style.display = "none";

    // Mover el botón de reiniciar
    const resetButton = document.getElementById("reset");
    resetButton.style.marginTop = "20px";

    setTimeout(function() {
        // Iniciar fuegos artificiales
        const container = document.querySelector('.fireworks');
        const fireworks = new Fireworks.default(container);
        fireworks.start();

        // Mostrar la hoja de la carta con animación
        const letter = document.querySelector('.letter');
        letter.style.opacity = "1";
        letter.style.transform = "translate(-50%, -50%) scale(1)";
        letter.style.transition = "transform 1s ease, opacity 1s ease";
    }, 1000);
});

// Función para reiniciar la página
document.getElementById("reset").addEventListener("click", function() {
    location.reload();
});
</script>
</body>
</html>
