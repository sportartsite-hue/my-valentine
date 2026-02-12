<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>💕 Veux-tu être ma Valentine ? 💕</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Georgia', serif;
            overflow: hidden;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 50%, #ff9a9e 100%);
            position: relative;
        }

        /* Animation de fond avec des coeurs flottants */
        .heart-bg {
            position: absolute;
            width: 100%;
            height: 100%;
            overflow: hidden;
            pointer-events: none;
            z-index: 0;
        }

        .floating-heart {
            position: absolute;
            font-size: 20px;
            opacity: 0.4;
            animation: float 8s infinite ease-in-out;
        }

        @keyframes float {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.4;
            }
            90% {
                opacity: 0.4;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Étoiles scintillantes */
        .sparkle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: white;
            border-radius: 50%;
            animation: sparkle 2s infinite ease-in-out;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.8);
        }

        @keyframes sparkle {
            0%, 100% {
                opacity: 0;
                transform: scale(0);
            }
            50% {
                opacity: 1;
                transform: scale(1);
            }
        }

        /* Container principal */
        .container {
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 245, 250, 0.95) 100%);
            padding: 60px 50px;
            border-radius: 30px;
            box-shadow: 0 30px 80px rgba(255, 105, 135, 0.3);
            text-align: center;
            max-width: 600px;
            width: 90%;
            position: relative;
            z-index: 1;
            backdrop-filter: blur(10px);
            border: 3px solid rgba(255, 182, 193, 0.6);
        }

        @media (max-width: 600px) {
            .container {
                padding: 40px 30px;
                width: 85%;
            }
        }

        /* Décoration de roses dans les coins */
        .rose-decoration {
            position: absolute;
            font-size: 50px;
            opacity: 0.8;
        }

        .rose-top-left {
            top: -20px;
            left: -20px;
            transform: rotate(-25deg);
        }

        .rose-top-right {
            top: -20px;
            right: -20px;
            transform: rotate(25deg);
        }

        .rose-bottom-left {
            bottom: -20px;
            left: -20px;
            transform: rotate(-45deg);
        }

        .rose-bottom-right {
            bottom: -20px;
            right: -20px;
            transform: rotate(45deg);
        }

        /* Coeur principal animé */
        .main-heart {
            font-size: 80px;
            animation: heartbeat 1.5s infinite;
            margin-bottom: 20px;
            display: inline-block;
        }

        @keyframes heartbeat {
            0%, 100% {
                transform: scale(1);
            }
            10%, 30% {
                transform: scale(1.1);
            }
            20%, 40% {
                transform: scale(1.05);
            }
        }

        h1 {
            color: #ff6b9d;
            font-size: 42px;
            margin-bottom: 30px;
            text-shadow: 2px 2px 8px rgba(255, 182, 193, 0.4);
            font-weight: bold;
            letter-spacing: 1px;
        }

        .question {
            font-size: 28px;
            color: #5a5a5a;
            margin-bottom: 50px;
            font-style: italic;
            line-height: 1.5;
        }

        @media (max-width: 600px) {
            h1 {
                font-size: 32px;
                margin-bottom: 20px;
            }

            .question {
                font-size: 22px;
                margin-bottom: 40px;
            }

            .main-heart {
                font-size: 60px;
                margin-bottom: 15px;
            }

            .rose-decoration {
                font-size: 35px;
            }
        }

        /* Conteneur des boutons */
        .buttons-container {
            display: flex;
            gap: 15px;
            justify-content: center;
            align-items: center;
            margin-top: 40px;
            position: relative;
            height: 80px;
            width: 100%;
            max-width: 550px;
            margin-left: auto;
            margin-right: auto;
            padding: 0 20px;
        }

        button {
            padding: 18px 20px;
            font-size: 20px;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
            box-shadow: 0 8px 20px rgba(255, 182, 193, 0.3);
            font-family: 'Georgia', serif;
            text-transform: uppercase;
            letter-spacing: 1.5px;
            position: relative;
            white-space: nowrap;
            min-width: 0;
        }

        #btnOui {
            background: linear-gradient(135deg, #ffafbd 0%, #ffc3a0 100%);
            color: white;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.2);
            flex: 1;
            max-width: 250px;
        }

        #btnOui:hover {
            transform: translateY(-2px);
            box-shadow: 0 12px 30px rgba(255, 175, 189, 0.5);
        }

        #btnOui:active {
            transform: translateY(0);
        }

        #btnNon {
            background: linear-gradient(135deg, #ffeaa7 0%, #fdcb6e 100%);
            color: #8b7355;
            text-shadow: 1px 1px 2px rgba(255, 255, 255, 0.5);
            flex: 1;
            max-width: 250px;
            overflow: hidden;
        }

        #btnNon:hover {
            background: linear-gradient(135deg, #fdcb6e 0%, #ffeaa7 100%);
            transform: translateY(-2px);
        }
        
        #btnNon.hidden {
            flex: 0;
            max-width: 0;
            padding: 0;
            margin: 0;
            opacity: 0;
            pointer-events: none;
            border: none;
        }

        @media (max-width: 600px) {
            .buttons-container {
                max-width: 90%;
            }
            
            button {
                font-size: 18px;
                padding: 15px 15px;
                letter-spacing: 1px;
            }
        }

        /* Page de succès */
        .success-page {
            display: none;
            text-align: center;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, #ffd1dc 0%, #ffb6c1 25%, #ffa6b8 50%, #ff96ad 75%, #ff86a2 100%);
            z-index: 1000;
            justify-content: center;
            align-items: center;
            animation: fadeIn 1s ease;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
            }
            to {
                opacity: 1;
            }
        }

        .success-content {
            background: linear-gradient(135deg, rgba(255, 255, 255, 0.98) 0%, rgba(255, 250, 252, 0.96) 100%);
            padding: 50px 40px 45px;
            border-radius: 50px;
            box-shadow: 
                0 50px 120px rgba(255, 105, 135, 0.4),
                0 0 0 1px rgba(255, 255, 255, 0.8) inset;
            max-width: 650px;
            width: 90%;
            max-height: 90vh;
            overflow-y: auto;
            animation: popIn 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55);
            border: 5px solid rgba(255, 182, 193, 0.7);
            position: relative;
        }

        .success-content::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(255, 182, 193, 0.15) 0%, transparent 70%);
            animation: pulse 3s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% {
                transform: scale(1);
                opacity: 0.5;
            }
            50% {
                transform: scale(1.1);
                opacity: 0.8;
            }
        }

        @media (max-width: 600px) {
            .success-content {
                padding: 35px 25px 30px;
                width: 85%;
                border-radius: 35px;
                max-height: 85vh;
            }

            .success-page h2 {
                font-size: 26px;
                margin-bottom: 18px;
            }

            .success-page p {
                font-size: 18px;
                margin-bottom: 15px;
            }

            .success-page .subtitle {
                font-size: 15px;
            }

            .big-heart {
                font-size: 60px;
                margin-bottom: 15px;
            }

            .flower-divider {
                font-size: 28px;
                margin: 15px 0;
            }

            .love-quote {
                font-size: 14px;
                padding: 12px 15px;
                margin-top: 20px;
            }
        }

        @keyframes popIn {
            0% {
                transform: scale(0.3) rotate(-5deg);
                opacity: 0;
            }
            60% {
                transform: scale(1.05) rotate(2deg);
            }
            100% {
                transform: scale(1) rotate(0deg);
                opacity: 1;
            }
        }

        .success-page h2 {
            font-size: 36px;
            background: linear-gradient(135deg, #ff6b9d 0%, #ff8fab 50%, #ffb3c1 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 25px;
            text-shadow: none;
            font-weight: bold;
            line-height: 1.2;
            position: relative;
            z-index: 1;
        }

        .success-page p {
            font-size: 24px;
            color: #6a4c4c;
            line-height: 1.5;
            font-style: italic;
            margin-bottom: 20px;
            position: relative;
            z-index: 1;
        }

        .success-page .subtitle {
            font-size: 18px;
            color: #8b6b6b;
            margin-top: 15px;
            font-style: normal;
            font-weight: 500;
            opacity: 0.9;
            position: relative;
            z-index: 1;
        }

        .big-heart {
            font-size: 80px;
            margin-bottom: 20px;
            display: inline-block;
            animation: heartbeatSuccess 1.5s infinite;
            filter: drop-shadow(0 5px 15px rgba(255, 105, 135, 0.4));
            position: relative;
            z-index: 1;
        }

        @keyframes heartbeatSuccess {
            0%, 100% {
                transform: scale(1);
            }
            10%, 30% {
                transform: scale(1.15);
            }
            20%, 40% {
                transform: scale(1.05);
            }
        }

        .flower-divider {
            font-size: 35px;
            margin: 20px 0;
            position: relative;
            z-index: 1;
            opacity: 0.9;
        }

        .love-quote {
            font-size: 16px;
            color: #997676;
            font-style: italic;
            margin-top: 25px;
            padding: 15px 20px;
            border-left: 4px solid #ffb3c1;
            border-right: 4px solid #ffb3c1;
            background: rgba(255, 182, 193, 0.08);
            border-radius: 15px;
            position: relative;
            z-index: 1;
            line-height: 1.6;
        }
            display: inline-block;
            animation: heartbeat 1s infinite;
        }

        /* Confettis et décorations de la page de succès */
        .confetti {
            position: absolute;
            width: 15px;
            height: 15px;
            background: #f50057;
            animation: confettiFall 3s linear infinite;
        }

        @keyframes confettiFall {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .flower {
            position: absolute;
            font-size: 40px;
            animation: floatFlower 4s ease-in-out infinite;
        }

        @keyframes floatFlower {
            0%, 100% {
                transform: translateY(0) rotate(0deg);
            }
            50% {
                transform: translateY(-30px) rotate(180deg);
            }
        }

        /* Particules de coeurs qui tombent */
        .heart-particle {
            position: absolute;
            font-size: 30px;
            animation: fallDown 4s linear infinite;
            opacity: 0.8;
        }

        @keyframes fallDown {
            to {
                transform: translateY(100vh) rotate(360deg);
                opacity: 0;
            }
        }

        /* Effet POOFFF */
        .poof {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 120px;
            font-weight: bold;
            color: #fff;
            text-shadow: 0 0 20px rgba(255, 255, 255, 0.8);
            z-index: 2000;
            animation: poofEffect 1s ease-out forwards;
            display: none;
        }

        @keyframes poofEffect {
            0% {
                transform: translate(-50%, -50%) scale(0);
                opacity: 0;
            }
            50% {
                transform: translate(-50%, -50%) scale(1.5);
                opacity: 1;
            }
            100% {
                transform: translate(-50%, -50%) scale(2);
                opacity: 0;
            }
        }
    </style>
</head>
<body>
    <!-- Coeurs flottants en arrière-plan -->
    <div class="heart-bg" id="heartBg"></div>

    <!-- Page principale -->
    <div class="container" id="mainPage">
        <div class="rose-decoration rose-top-left">🌹</div>
        <div class="rose-decoration rose-top-right">🌹</div>
        <div class="rose-decoration rose-bottom-left">🌹</div>
        <div class="rose-decoration rose-bottom-right">🌹</div>
        
        <div class="main-heart">💖</div>
        <h1>Saint-Valentin 2026</h1>
        <p class="question">Veux-tu être ma Valentine ?</p>
        
        <div class="buttons-container">
            <button id="btnOui">Oui ❤️</button>
            <button id="btnNon">Non</button>
        </div>
    </div>

    <!-- Effet POOFFF -->
    <div class="poof" id="poof">💥 POOFFF! 💥</div>

    <!-- Page de succès -->
    <div class="success-page" id="successPage">
        <div class="success-content">
            <div class="big-heart">💕</div>
            <h2>Tu as illuminé mon cœur</h2>
            <div class="flower-divider">✨ 🌹 ✨</div>
            <p>Merci d'avoir dit oui</p>
            <p class="subtitle">Tu es mon plus beau rêve devenu réalité</p>
            <div class="love-quote">
                "Avec toi, chaque moment devient magique"
            </div>
            <div style="margin-top: 30px; font-size: 45px; opacity: 0.8;">
                🌹 💐 🌸 💝
            </div>
        </div>
    </div>

    <script>
        // Créer des coeurs flottants en arrière-plan
        const heartBg = document.getElementById('heartBg');
        const hearts = ['❤️', '💕', '💖', '💗', '💓', '💝'];
        
        function createFloatingHeart() {
            const heart = document.createElement('div');
            heart.className = 'floating-heart';
            heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
            heart.style.left = Math.random() * 100 + '%';
            heart.style.animationDelay = Math.random() * 5 + 's';
            heart.style.animationDuration = (Math.random() * 5 + 5) + 's';
            heartBg.appendChild(heart);
            
            setTimeout(() => heart.remove(), 8000);
        }

        setInterval(createFloatingHeart, 500);

        // Créer des étoiles scintillantes
        function createSparkle() {
            const sparkle = document.createElement('div');
            sparkle.className = 'sparkle';
            sparkle.style.left = Math.random() * 100 + '%';
            sparkle.style.top = Math.random() * 100 + '%';
            sparkle.style.animationDelay = Math.random() * 2 + 's';
            heartBg.appendChild(sparkle);
            
            setTimeout(() => sparkle.remove(), 2000);
        }

        setInterval(createSparkle, 300);

        // Bouton NON - réduction progressive avec flex
        const btnNon = document.getElementById('btnNon');
        const btnOui = document.getElementById('btnOui');
        const container = document.querySelector('.buttons-container');

        let clickCount = 0;
        const maxClicks = 6; // Nombre de clics pour faire disparaître complètement le bouton Non

        btnNon.addEventListener('click', (e) => {
            e.preventDefault();
            clickCount++;
            
            // Calculer les nouvelles valeurs flex
            const flexNon = Math.max(0, 1 - (clickCount * 0.2)); // Réduit le flex
            const flexOui = 1 + (clickCount * 0.4); // Augmente le flex
            
            if (clickCount >= maxClicks) {
                // Faire disparaître complètement le bouton Non
                btnNon.classList.add('hidden');
                btnOui.style.flex = '1';
                btnOui.style.maxWidth = '100%';
            } else {
                // Appliquer les nouvelles valeurs flex
                btnNon.style.flex = flexNon;
                btnOui.style.flex = flexOui;
                
                // Ajuster le padding du bouton Non progressivement
                const paddingValue = Math.max(5, 20 - (clickCount * 3));
                btnNon.style.paddingLeft = paddingValue + 'px';
                btnNon.style.paddingRight = paddingValue + 'px';
                
                // Réduire la taille de la police du bouton Non
                const fontSize = Math.max(12, 20 - (clickCount * 1.5));
                btnNon.style.fontSize = fontSize + 'px';
                
                // Changer le texte si le bouton devient trop petit
                if (clickCount >= 4) {
                    btnNon.textContent = '...';
                } else if (clickCount >= 3) {
                    btnNon.textContent = 'Non';
                }
            }
        });

        // Bouton OUI - afficher la page de succès
        btnOui.addEventListener('click', () => {
            // Afficher l'effet POOFFF
            const poof = document.getElementById('poof');
            poof.style.display = 'block';
            
            setTimeout(() => {
                // Cacher la page principale
                document.getElementById('mainPage').style.display = 'none';
                
                // Afficher la page de succès
                const successPage = document.getElementById('successPage');
                successPage.style.display = 'flex';
                
                // Créer des confettis
                createConfetti();
                
                // Créer des fleurs
                createFlowers();
                
                // Créer des coeurs qui tombent
                createFallingHearts();
            }, 1000);
        });

        // Créer des confettis
        function createConfetti() {
            const colors = ['#ff0066', '#ff69b4', '#ff1493', '#c71585', '#db7093', '#ffc0cb'];
            
            for (let i = 0; i < 100; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    confetti.style.left = Math.random() * 100 + '%';
                    confetti.style.top = -20 + 'px';
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.animationDelay = Math.random() * 2 + 's';
                    confetti.style.animationDuration = (Math.random() * 2 + 2) + 's';
                    document.getElementById('successPage').appendChild(confetti);
                    
                    setTimeout(() => confetti.remove(), 5000);
                }, i * 30);
            }
        }

        // Créer des fleurs flottantes
        function createFlowers() {
            const flowers = ['🌹', '🌺', '🌸', '🌷', '💐', '🌻', '🏵️'];
            
            for (let i = 0; i < 20; i++) {
                setTimeout(() => {
                    const flower = document.createElement('div');
                    flower.className = 'flower';
                    flower.textContent = flowers[Math.floor(Math.random() * flowers.length)];
                    flower.style.left = Math.random() * 100 + '%';
                    flower.style.top = Math.random() * 100 + '%';
                    flower.style.animationDelay = Math.random() * 2 + 's';
                    document.getElementById('successPage').appendChild(flower);
                }, i * 100);
            }
        }

        // Créer des coeurs qui tombent
        function createFallingHearts() {
            const hearts = ['❤️', '💕', '💖', '💗', '💓', '💝', '💞'];
            
            setInterval(() => {
                const heart = document.createElement('div');
                heart.className = 'heart-particle';
                heart.textContent = hearts[Math.floor(Math.random() * hearts.length)];
                heart.style.left = Math.random() * 100 + '%';
                heart.style.top = -50 + 'px';
                heart.style.animationDelay = Math.random() * 1 + 's';
                heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
                document.getElementById('successPage').appendChild(heart);
                
                setTimeout(() => heart.remove(), 6000);
            }, 300);
        }
    </script>
</body>
</html>
