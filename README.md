<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0"> <!-- Añadido para responsive design -->
  <title>Carta de San Valentín</title>
  <link rel="stylesheet" href="style.css"> 
  <script src="https://cdn.jsdelivr.net/npm/fireworks-js@2.x/dist/index.umd.js"></script>
  <script src="https://unpkg.com/fireworks-js@2.x/dist/index.umd.js"></script>
</head>
<body>
<div class="fireworks"></div> <!-- Contenedor para los fuegos artificiales -->
<div class="envelope-wrapper">
    <div id="envelope" class="close">
        <div class="front flap"></div>
        <div class="front pocket"></div>
        <div class="letter">
            <div class="paper">
                <h2 class="letter-title"><b><i>Para Azalia Ceballos</i></b></h2>
                <p class="letter-content">Querida Azalia,</p>
                <p class="letter-content">Espero que este pequeño detalle ilumine tu día. Siempre serás especial para mí.</p>
                <p class="letter-content">En este día tan especial, quiero regalarte un poema:</p>
                <p class="letter-content poem">
                    "Tu belleza es como el sol al amanecer,<br>
                    iluminas mi mundo con tu ser.<br>
                    Cada mirada tuya es un regalo,<br>
                    y en tu sonrisa encuentro mi mayor halago.<br>
                    Eres la estrella que guía mi camino,<br>
                    y en tu presencia, todo es divino."
                </p>
                <p class="letter-content">Aunque te encuentres lejos, te pienso mas de lo que quiero. 😉</p>
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
    resetButton.style.marginTop = "500px"; // Mover el botón más abajo

    setTimeout(function() {
        // Iniciar fuegos artificiales
        const container = document.querySelector('.fireworks');
        const fireworks = new Fireworks.default(container);
        fireworks.start();

        // Mostrar la hoja de la carta con animación
        const letter = document.querySelector('.letter');
        letter.style.opacity = "1";
        letter.style.transform = "translate(-50%, -50%) scale(1)"; /* Centrar y tamaño adecuado */
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
