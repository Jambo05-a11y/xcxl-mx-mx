<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>АСЯ, Я ТЕБЯ ЛЮБЛЮ</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            position: relative;
        }

        .love-container {
            text-align: center;
            position: relative;
            z-index: 20;
        }

        .love-text {
            font-size: 3rem;
            color: #e74c3c;
            text-shadow: 0 0 10px rgba(231, 76, 60, 0.5);
            margin-bottom: 2rem;
            opacity: 0;
            transform: translateY(50px);
            animation: fadeInUp 1.5s ease forwards 0.5s;
            position: relative;
            z-index: 30;
        }

        .heart-container {
            position: relative;
            width: 150px;
            height: 150px;
            margin: 0 auto;
            z-index: 30;
        }

        .heart {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(45deg) scale(0);
            width: 80px;
            height: 80px;
            background-color: #e74c3c;
            transform-origin: center;
            animation: heartbeat 2s infinite ease-in-out 1s;
        }

        .heart::before,
        .heart::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 80px;
            background-color: #e74c3c;
            border-radius: 50%;
        }

        .heart::before {
            top: -40px;
            left: 0;
        }

        .heart::after {
            top: 0;
            left: 40px;
        }

        /* Идеальное большое сердце на заднем плане */
        .background-heart {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(45deg) scale(0);
            width: 600px;
            height: 600px;
            z-index: 5;
            animation: growHeart 4s ease-out forwards;
            background-color: rgba(231, 76, 60, 0.25);
            filter: blur(8px);
        }

        .background-heart::before,
        .background-heart::after {
            content: '';
            position: absolute;
            width: 300px;
            height: 300px;
            background-color: rgba(231, 76, 60, 0.25);
            border-radius: 50%;
        }

        .background-heart::before {
            top: -150px;
            left: 0;
        }

        .background-heart::after {
            top: 0;
            left: 150px;
        }

        /* Анимации */
        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes heartbeat {
            0% {
                transform: translate(-50%, -50%) rotate(45deg) scale(1);
            }
            50% {
                transform: translate(-50%, -50%) rotate(45deg) scale(1.2);
            }
            100% {
                transform: translate(-50%, -50%) rotate(45deg) scale(1);
            }
        }

        @keyframes growHeart {
            0% {
                transform: translate(-50%, -50%) rotate(45deg) scale(0);
                opacity: 0;
            }
            70% {
                opacity: 0.3;
            }
            100% {
                transform: translate(-50%, -50%) rotate(45deg) scale(1);
                opacity: 0.25;
            }
        }

        /* Плавающие сердечки */
        .floating-heart {
            position: absolute;
            background-color: rgba(231, 76, 60, 0.7);
            border-radius: 50%;
            pointer-events: none;
            opacity: 0;
            animation: floatUp 4s ease-out forwards;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(1) rotate(0deg);
                opacity: 0.7;
            }
            100% {
                transform: translateY(-200px) scale(0.5) rotate(360deg);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Большое идеальное сердце на заднем плане -->
    <div class="background-heart"></div>

    <div class="love-container">
        <div class="love-text">АСЯ, Я ТЕБЯ ЛЮБЛЮ</div>
        <div class="heart-container">
            <div class="heart"></div>
        </div>
    </div>

    <script>
        // Функция для создания плавающих сердечек
        function createFloatingHearts() {
            const body = document.body;
            const heartCount = 20;

            for (let i = 0; i < heartCount; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.classList.add('floating-heart');

                    // Случайный размер от 10 до 40px
                    const size = Math.random() * 30 + 10;
                    heart.style.width = size + 'px';
                    heart.style.height = size + 'px';

                    // Случайная позиция по горизонтали
                    const left = Math.random() * 100;
                    heart.style.left = left + '%';

                    // Случайная задержка анимации
                    const delay = Math.random() * 5;
                    heart.style.animationDelay = delay + 's';

                    // Случайная начальная позиция по вертикали (ниже экрана)
                    const startY = window.innerHeight + 50;
                    heart.style.bottom = -startY + 'px';

                    body.appendChild(heart);

                    // Удаляем сердечко после завершения анимации
                    setTimeout(() => {
                        heart.remove();
                    }, 4000 + delay * 1000);
                }, i * 300); // Создаем сердечки с интервалом
            }
        }

        // Запускаем создание сердечек каждые 3 секунды
        setInterval(createFloatingHearts, 3000);

        // Первый запуск через 1 секунду после загрузки
        setTimeout(createFloatingHearts, 1000);
    </script>
</body>
</html>
