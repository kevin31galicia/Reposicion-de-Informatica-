# Reposicion-de-Informatica-
en este trabajo adjunto o que es: el codigo html, css y js de lo que es mi pagina web acerca del futbol 
CODIGO HTML
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Perfil de Leyenda del Fútbol</title>
    <!-- Vinculación de la hoja de estilos externa -->
    <link rel="stylesheet" href="style.css">
</head>
<body>

    <div class="player-card">
        <!-- Título de la página -->
        <h1>Ficha Técnica ⚽</h1>

        <!-- Mensaje inicial -->
        <div class="status-box">
            <p id="mensaje-inicial">Estado: En la banca</p>
            <p id="subtitulo" class="subtext">Presiona para hacer ingresar al delantero</p>
        </div>

        <!-- Estadísticas del jugador -->
        <div class="stat-grid">
            <div class="stat-item">
                <div id="statGoles" class="stat-val">0</div>
                <div class="stat-lbl">Goles Totales</div>
            </div>
            <div class="stat-item">
                <div id="statNivel" class="stat-val">Inicial</div>
                <div class="stat-lbl">Rendimiento</div>
            </div>
        </div>

        <!-- Botones de acción -->
        <div class="controls">
            <button id="btnEntrenar" class="btn-action">⚡ Registrar Acción de Juego</button>
            <button id="btnReiniciar" class="btn-reset">🔄 Reiniciar Temporada</button>
        </div>
    </div>

    <!-- Vinculación del archivo JavaScript externo (al final del body) -->
    <script src="script.js"></script>
</body>
</html>

CODIGO CSS
/* Estilos en paleta oscura estilo Champions League */
body {
    font-family: 'Trebuchet MS', 'Lucida Sans Unicode', Arial, sans-serif;
    background: linear-gradient(135deg, #0b132b, #1c2541);
    color: #ffffff;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    margin: 0;
}

/* Tarjeta con estética de cromo / ficha de jugador */
.player-card {
    background-color: #1c2541;
    border: 2px solid #6fffe9;
    border-radius: 16px;
    padding: 30px;
    width: 380px;
    box-shadow: 0 10px 25px rgba(111, 255, 233, 0.2);
    text-align: center;
}

h1 {
    color: #6fffe9;
    font-size: 1.6rem;
    margin-top: 0;
    text-transform: uppercase;
    letter-spacing: 1px;
}

/* Mensaje del estado del jugador */
.status-box {
    background-color: #0b132b;
    padding: 15px;
    border-radius: 8px;
    border-left: 4px solid #6fffe9;
    margin: 20px 0;
}

#mensaje-inicial {
    font-size: 1.2rem;
    font-weight: bold;
    color: #ffffff;
    margin: 0 0 5px 0;
}

.subtext {
    color: #5bc0be;
    font-size: 0.85rem;
    margin: 0;
}

/* Panel de estadísticas */
.stat-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
    margin-bottom: 25px;
}

.stat-item {
    background-color: #0b132b;
    padding: 12px;
    border-radius: 8px;
}

.stat-val {
    font-size: 1.8rem;
    font-weight: bold;
    color: #6fffe9;
}

.stat-lbl {
    font-size: 0.75rem;
    color: #a5a5a5;
    text-transform: uppercase;
}

/* Botones personalizados */
.controls {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

button {
    padding: 12px;
    font-size: 0.95rem;
    font-weight: bold;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s, background-color 0.2s;
}

.btn-action {
    background-color: #6fffe9;
    color: #0b132b;
}

.btn-action:hover {
    background-color: #5bc0be;
    transform: scale(1.02);
}

.btn-reset {
    background-color: transparent;
    color: #a5a5a5;
    border: 1px solid #3a506b;
}

.btn-reset:hover {
    color: #ffffff;
    border-color: #6fffe9;
}

CODIGO JS 
// Variable para almacenar el contador de goles (almacena un dato)
let totalGoles = 0;

// Selección de elementos del DOM
const mensajeElem = document.getElementById('mensaje-inicial');
const subtituloElem = document.getElementById('subtitulo');
const golesElem = document.getElementById('statGoles');
const nivelElem = document.getElementById('statNivel');
const btnEntrenar = document.getElementById('btnEntrenar');
const btnReiniciar = document.getElementById('btnReiniciar');

// Función para ejecutar la acción de progreso en el partido
function simularJugada() {
    totalGoles++; // Modificar la variable
    
    // Actualizar número de goles en pantalla
    golesElem.textContent = totalGoles;

    // Modificar textos dinámicamente según la cantidad de goles
    if (totalGoles === 1) {
        mensajeElem.textContent = "Estado: ¡Primer gol en el debut!";
        subtituloElem.textContent = "El delantero empieza a mostrar su calidad.";
        nivelElem.textContent = "Promesa";
    } else if (totalGoles === 2) {
        mensajeElem.textContent = "Estado: ¡Doblete estelar!";
        subtituloElem.textContent = "Dominando el ataque de su equipo.";
        nivelElem.textContent = "Figura";
    } else if (totalGoles >= 3) {
        mensajeElem.textContent = "Estado: ¡Hat-Trick histórico!";
        subtituloElem.textContent = "¡Se lleva el balón a casa!";
        nivelElem.textContent = "Leyenda";
    }
}

// Función para reiniciar los valores
function reiniciarPerfil() {
    totalGoles = 0;
    golesElem.textContent = "0";
    nivelElem.textContent = "Inicial";
    mensajeElem.textContent = "Estado: En la banca";
    subtituloElem.textContent = "Presiona para hacer ingresar al delantero";
}

// Eventos click para detectar la acción del usuario
btnEntrenar.addEventListener('click', simularJugada);
btnReiniciar.addEventListener('click', reiniciarPerfil);
