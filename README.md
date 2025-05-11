# Carta-Para-Mama
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta para Mamá</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;700&family=Satisfy&family=Montserrat:wght@300;400;500&family=Petit+Formal+Script&family=Tangerine:wght@400;700&display=swap');
        
        body {
            font-family: 'Petit Formal Script', cursive;
            background: linear-gradient(135deg, #f5e9d9, #efe5d5, #e9e0cc, #f0ebe2);
            height: 100vh;
            margin: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
        }
        
        .container {
            position: relative;
            width: 450px;
            height: 350px;
            perspective: 1500px;
            margin: 20px auto;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }
        
        .envelope {
            position: relative;
            width: 100%;
            height: 100%;
            background-color: #e8dcbf;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
            transition: transform 0.8s ease;
            transform-style: preserve-3d;
            border-radius: 5px;
            overflow: hidden;
        }
        
        .envelope-front {
            position: absolute;
            width: 100%;
            height: 45%;
            background: linear-gradient(145deg, #e8dcbf, #d9ceaf);
            z-index: 10;
            transform-origin: top;
            transition: transform 1s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            backface-visibility: hidden;
            clip-path: polygon(0 0, 50% 50%, 100% 0, 100% 100%, 0 100%);
            bottom: 55%;
        }
        
        .heart-seal {
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: #e22424;
            transform: rotate(45deg);
            top: 40%;
            left: 50%;
            margin-top: -25px;
            margin-left: -25px;
            cursor: pointer;
            z-index: 15;
            transition: all 0.8s ease;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.2);
        }
        
        .heart-seal:before,
        .heart-seal:after {
            content: "";
            position: absolute;
            width: 50px;
            height: 50px;
            background-color: #e22424;
            border-radius: 50%;
        }
        
        .heart-seal:before {
            top: 0;
            left: -25px;
        }
        
        .heart-seal:after {
            top: -25px;
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
            height: 90%;
            background: linear-gradient(135deg, #fff9f0, #ffffff);
            padding: 20px;
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
        }
        
        .letter p {
            color: #5d4037;
            line-height: 1.7;
            margin-bottom: 15px;
            text-align: justify;
            font-size: 1.05em;
            font-family: 'Petit Formal Script', cursive;
        }
        
        .letter h1 {
            color: #8d6e63;
            margin-bottom: 25px;
            font-size: 2.2em;
            text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.1);
            font-family: 'Tangerine', cursive;
            font-weight: 700;
        }
        
        .letter .signature {
            color: #8d6e63;
            font-family: 'Tangerine', cursive;
            margin-top: 30px;
            font-size: 1.8em;
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
            z-index: 2; /* Asegúrate de que esté detrás de la carta */
        }
        
        .heart {
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: rgba(255, 82, 82, 0.6);
            transform: rotate(45deg);
            opacity: 0;
            animation: float 4s ease-in-out infinite;
        }
        
        .heart:before,
        .heart:after {
            content: "";
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: rgba(255, 82, 82, 0.6);
            border-radius: 50%;
        }
        
        .heart:before {
            top: 0;
            left: -7.5px;
        }
        
        .heart:after {
            top: -7.5px;
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
            width: 15px;
            height: 15px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
        }
        
        .flower:before {
            content: "";
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
            top: 0;
            left: -5px;
        }
        
        .flower:after {
            content: "";
            position: absolute;
            width: 15px;
            height: 15px;
            background-color: rgba(233, 30, 99, 0.5);
            border-radius: 50%;
            top: -5px;
            left: 0;
        }
        
        .heart, .flower {
            width: 10px;
            height: 10px;
        }

        .heart:before, .heart:after,
        .flower:before, .flower:after {
            width: 10px;
            height: 10px;
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
                transform: rotate(45deg) translateY(-20px);
                opacity: 1;
            }
            100% {
                transform: rotate(45deg) translateY(-50px);
                opacity: 0;
            }
        }
        
        @media (max-width: 500px) {
            body {
                height: auto;
                overflow-y: auto;
            }

            .container {
                width: 90vw;
                height: auto;
                margin: 10px auto;
            }

            .envelope {
                width: 100%;
                height: auto;
            }

            .letter {
                width: 100%;
                height: auto;
                padding: 10px;
                font-size: 0.9em;
            }

            .letter h1 {
                font-size: 1.5em;
            }

            .letter p {
                font-size: 0.85em;
            }

            .image-gallery img {
                width: 80px;
                height: 80px;
            }

            .heart-seal {
                width: 40px;
                height: 40px;
            }

            .heart-seal:before,
            .heart-seal:after {
                width: 40px;
                height: 40px;
            }
        }

        /* Estilos para las imágenes dentro de la carta */
        .image-gallery {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin: 20px 0;
        }

        .image-gallery img {
            width: 100px;
            height: 100px;
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
            width: 80px;
            height: 80px;
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
                <p>En este día tan especial, quiero decirte que eres el regalo más grande que la vida me ha dado. Tu presencia ilumina cada uno de mis días, y tu amor incondicional me ha sostenido en cada paso de mi camino.</p>
                <p>Desde mis primeros latidos en tu vientre hasta hoy, has sido la fuerza invisible que me impulsa y el refugio al que siempre puedo volver. Gracias por ser mi guía, mi confidente, mi apoyo inquebrantable y mi ejemplo a seguir.</p>
                <p>Cada sacrificio, cada noche sin dormir, cada palabra de aliento, cada abrazo sanador... todo ha formado la persona que soy hoy. Me has enseñado a ser fuerte frente a las adversidades, a perseverar cuando todo parece imposible, y sobre todo, a amar sin límites ni condiciones.</p>
                <p>Admiro tu fortaleza, tu paciencia infinita y esa capacidad única que tienes para ver lo mejor en cada persona, incluso cuando ni nosotros mismos podemos verlo. Tu sabiduría ha sido mi brújula, y tu ternura, el bálsamo para mis heridas.</p>
                <p>Quiero pedirte disculpas desde lo más profundo de mi corazón por aquellas veces en las que no he sido o hecho lo que esperabas de mí. Por esos momentos en que mi terquedad no me permitió ver la sabiduría en tus consejos, o cuando mi inmadurez me llevó a tomar decisiones que te preocuparon y te quitaron el sueño.</p>
                <p>Perdóname por las lágrimas que he causado en tus ojos, por las canas que aparecieron prematuramente por mis rebeldías, y por las veces que no valoré tus sacrificios como debía. A veces olvidamos que antes de ser madres, eres una mujer con sueños, miedos y anhelos propios.</p>
                <p>Te pido perdón por aquellos momentos en que te hice sentir que no te escuchaba, cuando en realidad, tus palabras estaban grabándose en mi alma. Lamento las veces en que elegí el camino difícil a pesar de tus advertencias, obligándote a recoger mis pedazos con amor infinito.</p>
                <p>Prometo esforzarme cada día para ser ese hijo/a que mereces, para hacerte sentir orgullosa y para devolverte aunque sea una fracción de todo el amor que me has dado. Prometo valorar más tus consejos, estar más presente en tu vida y demostrarte que todas tus enseñanzas han dado fruto.</p>
                <p>Tu corazón es mi primer hogar, y tu amor es mi mayor fortaleza. Cuando pienso en la palabra "amor", veo tu rostro; cuando busco seguridad, recuerdo tus abrazos; cuando necesito valor, evoco tus palabras de aliento.</p>
                <p>No hay palabras suficientes en ningún idioma para expresar cuánto te amo, te respeto y te admiro. Eres mi heroína sin capa, mi ángel en la tierra, el reflejo más puro del amor divino.</p>
                <p>¡Feliz Día de las Madres, mamá querida! Hoy y siempre, celebro el milagro de tenerte en mi vida y el privilegio de llamarte "madre". Te amo infinitamente, más allá de lo que las palabras puedan expresar.</p>
                    <!-- Contenedor de imágenes dentro de la carta -->
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
            
            // Crear corazones decorativos
            for (let i = 0; i < 10; i++) {
                createHeart();
            }
            
            // Crear flores decorativas
            for (let i = 0; i < 8; i++) {
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
                heart.style.left = Math.random() * 80 + 10 + '%'; // Posición horizontal alrededor de la carta
                heart.style.top = Math.random() * 80 + 10 + '%'; // Posición vertical alrededor de la carta
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
