<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Carta para Mamá</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Satisfy&family=Montserrat:wght@300;400;500&family=Petit+Formal+Script&family=Tangerine:wght@400;700&display=swap');
        
        body {
            font-family: 'Petit Formal Script', cursive;
            background: linear-gradient(135deg, #f5e9d9, #efe5d5, #e9e0cc, #f0ebe2);
            min-height: 100vh;
            margin: 0;
            padding: 20px 0;
            display: flex;
            justify-content: center;
            align-items: center;
            box-sizing: border-box;
        }
        
        .container {
            width: 90%;
            max-width: 500px; /* Limita el ancho máximo en pantallas grandes */
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            perspective: 1500px;
            margin: 0 auto;
        }
        
        .envelope,
        .envelope-front,
        .envelope-back {
            background-image: url('ruta-a-textura-papel.jpg'); /* Reemplaza con la ruta de tu textura */
            background-size: cover;
            background-blend-mode: multiply;
        }

        .envelope {
            position: relative;
            width: 100%;
            padding-bottom: 70%; /* Mantiene proporción del sobre */
            background: linear-gradient(145deg, #e8a94b, #deab52e6);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            transition: transform 0.8s ease;
            transform-style: preserve-3d;
            border-radius: 5px;
            overflow: hidden;
            border: 2px solid #b08968;
        }
        
        .envelope-front {
            position: absolute;
            width: 100%;
            height: 45%;
            background: linear-gradient(145deg, #d4b483, #c9a66b);
            z-index: 10;
            transform-origin: top;
            transition: transform 1s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            backface-visibility: hidden;
            clip-path: polygon(0 0, 50% 50%, 100% 0, 100% 100%, 0 100%);
            bottom: 55%;
            border-bottom: 2px solid #b08968;
        }
        
        .envelope-back {
            position: absolute;
            width: 100%;
            height: 100%;
            background: linear-gradient(145deg, #d4b483, #c9a66b);
            border-radius: 5px;
            box-shadow: inset 0 0 10px rgba(0, 0, 0, 0.2);
        }
        
        .envelope-border {
            position: absolute;
            width: 100%;
            height: 100%;
            border: 2px solid #b08968;
            border-radius: 5px;
            box-sizing: border-box;
            pointer-events: none;
        }
        
        .heart-seal {
            position: absolute;
            width: 40px;
            height: 40px;
            background-color: #c60505;
            transform: rotate(45deg);
            top: 40%;
            left: 50%;
            margin-top: -20px;
            margin-left: -20px;
            cursor: pointer;
            z-index: 15;
            transition: all 0.8s ease;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2), inset 0 0 5px rgba(0, 0, 0, 0.3);
            border: 2px solid #c60505;
        }
        
        .heart-seal:before,
        .heart-seal:after {
            content: "";
            position: absolute;
            width: 40px;
            height: 40px;
            background-color: #c60505;
            border-radius: 50%;
        }
        
        .heart-seal:before {
            top: 0;
            left: -20px;
        }
        
        .heart-seal:after {
            top: -20px;
            left: 0;
        }
        
        .heart-seal:hover {
            transform: rotate(45deg) scale(1.1);
        }
        
        .heart-fly-away {
            animation: fly-away 1.5s forwards;
        }
        
        @keyframes fly-away {
            0% {
                transform: rotate(45deg) scale(1);
                opacity: 1;
            }
            50% {
                transform: rotate(45deg) scale(1.2) translateY(-20px);
                opacity: 0.8;
            }
            100% {
                transform: rotate(45deg) scale(0.1) translateY(-200px);
                opacity: 0;
            }
        }
        
        .letter {
            position: absolute;
            width: 90%;
            height: 85%;
            background: linear-gradient(135deg, #fff9f0, #ffffff);
            padding: 15px;
            box-sizing: border-box;
            text-align: center;
            border-radius: 3px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            top: 5%;
            left: 5%;
            transform: translateZ(-2px) scale(0.5);
            opacity: 0;
            transition: all 1s ease;
            overflow-y: auto;
            border: 1px solid #d8c9a7;
            font-size: 1em;
        }
        
        .letter p {
            color: #5d4037;
            line-height: 1.5;
            margin-bottom: 12px;
            text-align: justify;
            font-size: 0.9em;
            font-family: 'Petit Formal Script', cursive;
        }
        
        .letter h1 {
            color: #8d6e63;
            margin-bottom: 15px;
            font-size: 1.8em;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
            font-family: 'Tangerine', cursive;
            font-weight: 700;
        }
        
        .letter .signature {
            color: #8d6e63;
            font-family: 'Tangerine', cursive;
            margin-top: 15px;
            font-size: 1.6em;
            font-weight: 700;
        }
        
        .hearts, .flowers {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
        }
        
        .hearts {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            overflow: hidden;
            z-index: 2;
        }
        
        .heart {
            position: absolute;
            width: 12px;
            height: 12px;
            background-color: rgba(255, 82, 82, 0.6);
            transform: rotate(45deg);
            opacity: 0;
            animation: float 4s ease-in-out infinite;
        }
        
        .heart:before,
        .heart:after {
            content: "";
            position: absolute;
            width: 12px;
            height: 12px;
            background-color: rgba(255, 82, 82, 0.6);
            border-radius: 50%;
        }
        
        .heart:before {
            top: 0;
            left: -6px;
        }
        
        .heart:after {
            top: -6px;
            left: 0;
        }
        
        .flowers {
            position: absolute;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }
        
        .flower {
            position: absolute;
            width: 12px;
            height: 12px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
        }
        
        .flower:before {
            content: "";
            position: absolute;
            width: 12px;
            height: 12px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
            top: 0;
            left: -4px;
        }
        
        .flower:after {
            content: "";
            position: absolute;
            width: 12px;
            height: 12px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
            top: -4px;
            left: 0;
        }
        
        .opened .envelope-front {
            transform: rotateX(-180deg);
        }
        
        .opened .letter {
            transform: translateZ(0) scale(1);
            opacity: 1;
            z-index: 5;
        }
        
        .heart-animation {
            animation: float 4s ease-in-out infinite;
        }
        
        @keyframes float {
            0% {
                transform: rotate(45deg) translateY(0);
                opacity: 0.8;
            }
            50% {
                transform: rotate(45deg) translateY(-10px);
                opacity: 1;
            }
            100% {
                transform: rotate(45deg) translateY(-20px);
                opacity: 0;
            }
        }
        
        /* Estilos para las imágenes dentro de la carta */
        .image-gallery {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 15px 0;
        }

        .image-gallery img {
            width: 80px;
            height: 80px;
            border-radius: 10px;
            box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
            object-fit: cover;
        }

        /* Estilos para imágenes decorativas alrededor */
        .decorative-images {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

        .decorative-images img {
            position: absolute;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            object-fit: cover;
            opacity: 0.8;
            animation: float 6s ease-in-out infinite;
        }

        .decorative-images img:nth-child(1) {
            top: 10%;
            left: 20%;
        }

        .decorative-images img:nth-child(2) {
            top: 70%;
            left: 80%;
        }
        
        /* Ajustes específicos para móviles pequeños */
        @media (max-width: 360px) {
            .letter p {
                font-size: 0.85em;
                line-height: 1.4;
                margin-bottom: 8px;
            }
            
            .letter h1 {
                font-size: 1.6em;
                margin-bottom: 10px;
            }
            
            .image-gallery img {
                width: 60px;
                height: 60px;
            }
            
            .heart-seal {
                width: 30px;
                height: 30px;
                margin-top: -15px;
                margin-left: -15px;
            }
            
            .heart-seal:before,
            .heart-seal:after {
                width: 30px;
                height: 30px;
            }
            
            .heart-seal:before {
                left: -15px;
            }
            
            .heart-seal:after {
                top: -15px;
            }
        }
        
        /* Ajustes para tamaños muy pequeños como iPhone SE */
        @media (max-height: 568px) {
            body {
                padding: 10px 0;
            }
            
            .container {
                width: 95%;
            }
            
            .envelope {
                padding-bottom: 75%;
            }
            
            .letter {
                height: 82%;
                padding: 10px;
            }
            
            .letter p {
                font-size: 0.8em;
                margin-bottom: 6px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="envelope">
            <div class="envelope-back"></div>
            <div class="envelope-border"></div>
            <div class="envelope-bottom"></div>
            <div class="letter">
                <h1>Para mi querida Mamá</h1>
                <p>Mamá, hoy en este día, quiero decirte que aunque la vida nos ha puesto pruebas y hemos tenido nuestros momentos, tú eres un regalo importante en mi vida. Tu presencia siempre ha marcado mis días, y sé que tu amor, a tu manera, me ha acompañado en cada paso.</p>
                <p>Desde que estaba en tu vientre hasta hoy, has sido una fuerza en mi vida y un lugar al que siempre puedo volver. Gracias por guiarme, por escucharme cuando lo haya hecho, por apoyarme a tu modo y por ser el ejemplo que has podido ser.</p>
                <p>Cada esfuerzo, cada noche que te preocupaste, cada palabra que me diste, cada abrazo... todo eso ha contribuido a la persona que soy. Me has enseñado a ser fuerte ante las dificultades, a seguir adelante cuando no es fácil, y también a querer, a mi manera.</p>
                <p>Admiro tu fortaleza, tu paciencia cuando la has tenido, y esa capacidad de ver algo bueno en las personas. Tu experiencia ha sido una guía, y tu cariño, cuando lo necesitado, ha sido un alivio.</p>
                <p>Quiero pedirte perdón desde lo más profundo por esas veces en las que no he sido o hecho lo que esperabas. Por esos momentos en que mi forma de ser no me permitió ver tu punto de vista, o cuando mis decisiones te preocuparon.</p>
                <p>Perdóname por las preocupaciones que te he dado, por las veces que quizás no valoré tus esfuerzos como debías. A veces olvidamos que antes de ser madres, son personas con sus propias vidas y sus propias luchas.</p>
                <p>Te pido perdón por aquellos momentos en que sentiste que no te escuchaba, aunque en el fondo, tus palabras siempre han tenido un peso. Lamento las veces en que elegí mi propio camino a pesar de tus consejos, y tú estuviste ahí para ayudarme a levantarme.</p>
                <p>Prometo intentar cada día ser ese hijo/a que te haga sentir orgullosa a mi manera, y tratar de valorar más tus consejos y estar presente en tu vida. Quiero que veas que tus enseñanzas han tenido un impacto en mí.</p>
                <p>Tu cariño es como un hogar para mí, un lugar de referencia, y sé que a tu manera siempre me has querido fuerte. Cuando pienso en ese afecto, pienso en ti; cuando necesito sentirme seguro, recuerda tus gestos; cuando busco fuerza, recuerda tus palabras.</p>
                <p>No hay palabras exactas para expresar todo lo que siento por ti, el respeto y el cariño que te tengo. Eres una persona importante en mi vida, alguien que siempre ha estado ahí a su manera.</p>
                <p>¡Feliz Día de las Madres, mamá! Hoy y siempre, celebro que estés en mi vida y que seas mi madre. Te quiero, a mi manera, más de lo que a veces puedo expresar.</p>
                <div class="image-gallery">
                    <img src="WhatsApp Image 2025-05-10 at 11.16.37 PM.jpeg" alt="Imagen 2">
                </div>
                <div class="signature">Con todo mi amor,<br>De Juancito</div>
            </div>
            <div class="envelope-front"></div>
            <div class="heart-seal" id="seal"></div>
        </div>
        <div class="hearts" id="hearts"></div>
        <div class="flowers" id="flowers"></div>
    </div>
    
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const seal = document.getElementById('seal');
            const envelope = document.querySelector('.envelope');
            const heartsContainer = document.getElementById('hearts');
            const flowersContainer = document.getElementById('flowers');
            
            // Crear menos corazones y flores para mejorar el rendimiento
            for (let i = 0; i < 5; i++) {
                createHeart();
            }

            for (let i = 0; i < 4; i++) {
                createFlower();
            }
            
            // Función para abrir el sobre
            seal.addEventListener('click', () => {
                // Hacer que el corazón desaparezca volando
                seal.classList.add('heart-fly-away');
                
                // Esperar un momento antes de abrir el sobre
                setTimeout(() => {
                    envelope.classList.add('opened');
                    
                    // Simular la carta saliendo del sobre con un retraso
                    setTimeout(() => {
                        // Animar corazones cuando se abre la carta
                        animateHearts();
                    }, 800);
                }, 500);
            });
            
            function createHeart() {
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.style.left = Math.random() * 80 + 10 + '%';
                heart.style.top = Math.random() * 80 + 10 + '%';
                heart.style.transform = 'rotate(45deg) scale(' + (Math.random() * 0.5 + 0.5) + ')';
                heartsContainer.appendChild(heart);
            }
            
            function createFlower() {
                const flower = document.createElement('div');
                flower.classList.add('flower');
                flower.style.left = Math.random() * 100 + '%';
                flower.style.top = Math.random() * 100 + '%';
                flower.style.transform = 'scale(' + (Math.random() * 0.5 + 0.5) + ')';
                flowersContainer.appendChild(flower);
            }
            
            function animateHearts() {
                const hearts = document.querySelectorAll('.heart');
                hearts.forEach((heart, index) => {
                    setTimeout(() => {
                        heart.style.opacity = '1';
                        heart.classList.add('heart-animation');
                        
                        // Eliminar la animación después de que termine
                        setTimeout(() => {
                            heart.classList.remove('heart-animation');
                            heart.style.opacity = '0';
                            
                            // Crear un nuevo corazón
                            setTimeout(() => {
                                heart.style.left = Math.random() * 100 + '%';
                                heart.style.top = Math.random() * 100 + '%';
                                heart.style.transform = 'rotate(45deg) scale(' + (Math.random() * 0.5 + 0.5) + ')';
                            }, 500);
                        }, 4000);
                    }, index * 400);
                });
                
                // Repetir la animación
                setTimeout(animateHearts, 5000); // Repite la animación cada 5 segundos
            }
        });
    </script>
</body>
</html>
