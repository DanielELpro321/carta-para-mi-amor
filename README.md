<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carta para mi princesa</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(135deg, #ff9a9e, #fad0c4);
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            position: relative;
            animation: fadeIn 2s ease-in-out forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        .sobre {
            width: 300px;
            height: 200px;
            background: #f8d7da;
            position: relative;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            transition: transform 0.5s;
        }

        .sobre::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #e57373;
            clip-path: polygon(0 0, 100% 0, 50% 50%);
        }

        .hoja {
            width: 280px;
            height: 350px;
            background: white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) scale(0);
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
            text-align: center;
            transition: transform 0.5s ease-in-out;
        }

        .hoja h1 {
            color: #e63946;
            font-size: 22px;
            margin-bottom: 10px;
        }

        .hoja p {
            color: #333;
            font-size: 14px;
            line-height: 1.6;
        }

        .abierto .hoja {
            transform: translate(-50%, -50%) scale(1);
        }

        .abierto .sobre {
            transform: translateY(-50px) scale(0.9);
        }

        .corazon {
            position: absolute;
            color: red;
            font-size: 24px;
            opacity: 0.8;
            animation: flotar 4s linear infinite;
        }

        @keyframes flotar {
            0% {
                transform: translateY(0) translateX(0);
                opacity: 1;
            }
            100% {
                transform: translateY(-200px) translateX(calc(-50px + 100px * var(--random-x)));
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <div class="sobre" onclick="abrirCarta()">
        💌
    </div>
    <div class="hoja">
        <h1>Para mi amor ❤️</h1>
        <p>Querida Luna,</p>
        <p>En este día tan especial, quiero decirte lo mucho que significas para mí. Eres mi razón para sonreír cada día y mi inspiración para ser mejor.</p>
        <p>Gracias por estar a mi lado en los buenos y malos momentos. Te amo más de lo que las palabras pueden expresar.</p>
        <p>Con todo mi cariño,</p>
        <p>Tu hombre</p>
    </div>

    <script>
        function abrirCarta() {
            document.body.classList.toggle('abierto');
            if (document.body.classList.contains('abierto')) {
                generarCorazones();
            }
        }

        function generarCorazones() {
            for (let i = 0; i < 20; i++) {
                let corazon = document.createElement('div');
                corazon.innerHTML = '❤️';
                corazon.classList.add('corazon');
                document.body.appendChild(corazon);
                
                let xPos = Math.random() * window.innerWidth;
                let yPos = window.innerHeight;
                corazon.style.left = `${xPos}px`;
                corazon.style.top = `${yPos}px`;
                corazon.style.fontSize = `${Math.random() * 20 + 20}px`;
                corazon.style.setProperty('--random-x', Math.random());
                corazon.style.animationDuration = `${Math.random() * 2 + 2}s`;
                
                setTimeout(() => {
                    corazon.remove();
                }, 4000);
            }
        }
    </script>
</body>
</html>

