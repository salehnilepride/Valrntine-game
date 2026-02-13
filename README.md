<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will You Be My Valentine? (Impossible Edition)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&family=Bangers&family=Comic+Neue:wght@700&display=swap" rel="stylesheet">
    <style>
        * {
            cursor: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24"><path fill="%23ff006e" stroke="%23fff" stroke-width="1" d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41.81 4.5 2.09C13.09 3.81 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z"/></svg>') 16 16, auto !important;
        }

        body {
            font-family: 'Comic Neue', cursive;
            background: linear-gradient(45deg, #ff006e, #8338ec, #3a86ff, #06ffa5, #ffbe0b);
            background-size: 400% 400%;
            animation: gradientShift 8s ease infinite;
            overflow: hidden;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .pixel-font { font-family: 'Press Start 2P', cursive; }
        .comic-font { font-family: 'Bangers', cursive; letter-spacing: 2px; }

        .floating-emoji {
            position: absolute;
            font-size: 3rem;
            animation: floatEmoji 4s ease-in-out infinite;
            pointer-events: none;
        }

        @keyframes floatEmoji {
            0%, 100% { transform: translateY(0) rotate(0deg); }
            50% { transform: translateY(-30px) rotate(10deg); }
        }

        .shake-crazy {
            animation: shakeCrazy 0.3s cubic-bezier(.36,.07,.19,.97) both infinite;
        }

        @keyframes shakeCrazy {
            0% { transform: translate(2px, 2px) rotate(0deg); }
            10% { transform: translate(-2px, -4px) rotate(-2deg); }
            20% { transform: translate(-6px, 0px) rotate(2deg); }
            30% { transform: translate(6px, 4px) rotate(0deg); }
            40% { transform: translate(2px, -2px) rotate(2deg); }
            50% { transform: translate(-2px, 4px) rotate(-2deg); }
            60% { transform: translate(-6px, 2px) rotate(0deg); }
            70% { transform: translate(6px, 2px) rotate(-2deg); }
            80% { transform: translate(-2px, -2px) rotate(2deg); }
            90% { transform: translate(2px, 4px) rotate(0deg); }
            100% { transform: translate(2px, -4px) rotate(-2deg); }
        }

        .spin-super {
            animation: spinSuper 1s linear infinite;
        }

        @keyframes spinSuper {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        .pulse-glow {
            animation: pulseGlow 1.5s ease-in-out infinite;
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 20px #ff006e, 0 0 40px #ff006e; transform: scale(1); }
            50% { box-shadow: 0 0 40px #ffbe0b, 0 0 80px #ffbe0b; transform: scale(1.05); }
        }

        .escape-btn {
            position: absolute;
            transition: all 0.15s cubic-bezier(0.68, -0.55, 0.265, 1.55);
        }

        .rage-text {
            position: fixed;
            font-family: 'Bangers', cursive;
            font-size: 4rem;
            color: #ff0000;
            text-transform: uppercase;
            pointer-events: none;
            opacity: 0;
            transform: scale(0) rotate(-10deg);
            transition: all 0.2s ease;
            text-shadow: 4px 4px 0 #000, -2px -2px 0 #fff;
            z-index: 1000;
            -webkit-text-stroke: 3px black;
        }

        .rage-text.show {
            opacity: 1;
            transform: scale(1.2) rotate(-5deg);
        }

        .meme-card {
            background: linear-gradient(135deg, #fff 0%, #ffe4ec 100%);
            border: 6px solid #000;
            box-shadow: 12px 12px 0 #000;
            transform: rotate(-2deg);
            transition: transform 0.3s;
        }

        .meme-card:hover {
            transform: rotate(0deg) scale(1.02);
        }

        .btn-yes {
            background: #00ff00;
            border: 4px solid #000;
            box-shadow: 6px 6px 0 #000;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.8rem;
            transition: all 0.1s;
        }

        .btn-yes:hover {
            transform: translate(-2px, -2px);
            box-shadow: 8px 8px 0 #000;
            background: #00ff88;
        }

        .btn-yes:active {
            transform: translate(4px, 4px);
            box-shadow: 2px 2px 0 #000;
        }

        .btn-no {
            background: #ff0000;
            border: 4px solid #000;
            box-shadow: 6px 6px 0 #000;
            font-family: 'Press Start 2P', cursive;
            font-size: 0.7rem;
            color: #fff;
        }

        .mini-game {
            position: fixed;
            background: #000;
            border: 4px solid #fff;
            padding: 20px;
            z-index: 500;
            display: none;
        }

        .typing-text::after {
            content: '|';
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        .confetti-particle {
            position: fixed;
            width: 15px;
            height: 15px;
            pointer-events: none;
            z-index: 9999;
        }

        .sweat-drop {
            position: absolute;
            font-size: 2rem;
            animation: sweatDrop 1s ease-out forwards;
            pointer-events: none;
        }

        @keyframes sweatDrop {
            0% { transform: translateY(0) scale(1); opacity: 1; }
            100% { transform: translateY(40px) scale(0.5); opacity: 0; }
        }

        .glitch-effect {
            animation: glitch 0.3s infinite;
        }

        @keyframes glitch {
            0% { transform: translate(0); filter: hue-rotate(0deg); }
            20% { transform: translate(-5px, 5px); filter: hue-rotate(90deg); }
            40% { transform: translate(5px, -5px); filter: hue-rotate(180deg); }
            60% { transform: translate(-5px, -5px); filter: hue-rotate(270deg); }
            80% { transform: translate(5px, 5px); filter: hue-rotate(360deg); }
            100% { transform: translate(0); filter: hue-rotate(0deg); }
        }

        .troll-face {
            position: absolute;
            font-size: 5rem;
            opacity: 0.05;
            pointer-events: none;
            filter: grayscale(100%) contrast(200%);
        }

        .health-bar {
            width: 200px;
            height: 30px;
            background: #333;
            border: 3px solid #000;
            position: relative;
            overflow: hidden;
        }

        .health-fill {
            height: 100%;
            background: linear-gradient(90deg, #ff0000, #ff6600, #ffff00, #00ff00);
            transition: width 0.3s;
            width: 100%;
        }

        .boss-mode {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.9);
            display: none;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            z-index: 2000;
        }

        .typing-game {
            font-family: 'Press Start 2P', cursive;
            color: #00ff00;
            font-size: 1.5rem;
            text-align: center;
        }

        .target-word {
            display: inline-block;
            padding: 10px;
            margin: 5px;
            background: #003300;
            border: 2px solid #00ff00;
        }

        .target-word.correct {
            background: #00ff00;
            color: #000;
        }

        .dodge-game {
            width: 400px;
            height: 300px;
            background: #222;
            position: relative;
            overflow: hidden;
            border: 4px solid #fff;
        }

        .player {
            width: 30px;
            height: 30px;
            background: #00ff00;
            position: absolute;
            bottom: 10px;
            left: 185px;
            transition: left 0.1s;
        }

        .obstacle {
            width: 30px;
            height: 30px;
            background: #ff0000;
            position: absolute;
            top: -30px;
        }

        .math-problem {
            font-size: 3rem;
            color: #fff;
            text-align: center;
            margin: 20px;
        }

        .math-input {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.5rem;
            padding: 10px;
            text-align: center;
            width: 200px;
        }
    </style>
</head>
<body class="min-h-screen flex items-center justify-center relative">

    <!-- Floating Background Emojis -->
    <div id="bg-emojis" class="fixed inset-0 pointer-events-none overflow-hidden">
        <div class="floating-emoji" style="top: 10%; left: 10%; animation-delay: 0s;">💘</div>
        <div class="floating-emoji" style="top: 20%; right: 15%; animation-delay: 0.5s;">💖</div>
        <div class="floating-emoji" style="bottom: 20%; left: 20%; animation-delay: 1s;">💝</div>
        <div class="floating-emoji" style="bottom: 10%; right: 10%; animation-delay: 1.5s;">💕</div>
        <div class="floating-emoji" style="top: 50%; left: 5%; animation-delay: 2s;">🌹</div>
        <div class="floating-emoji" style="top: 60%; right: 5%; animation-delay: 2.5s;">🍫</div>
    </div>

    <!-- Main Game Card -->
    <div id="main-card" class="meme-card relative p-8 rounded-2xl max-w-2xl w-full mx-4 z-10">
        <div class="troll-face top-2 right-2">😈</div>
        
        <!-- Header -->
        <div class="text-center mb-6">
            <div class="text-6xl mb-4 animate-bounce">🎯</div>
            <h1 class="comic-font text-5xl text-pink-600 mb-2" style="text-shadow: 3px 3px 0 #000;">VALENTINE BOSS BATTLE</h1>
            <p class="pixel-font text-xs text-gray-600 mt-4">INSERT COIN TO CONTINUE... OR JUST SAY YES 💕</p>
        </div>

        <!-- Health Bar -->
        <div class="flex justify-center mb-6">
            <div class="text-center">
                <p class="pixel-font text-xs mb-2">NO BUTTON'S RESISTANCE</p>
                <div class="health-bar">
                    <div id="health-fill" class="health-fill"></div>
                </div>
            </div>
        </div>

        <!-- Main Character Display -->
        <div class="bg-pink-100 border-4 border-black rounded-xl p-6 mb-6 text-center relative overflow-hidden">
            <div id="character-display" class="text-8xl mb-4 transition-all duration-300">👉👈🥺</div>
            <p id="dialogue-text" class="comic-font text-2xl text-pink-700 typing-text">Will you be my Valentine?</p>
            
            <!-- Sweat drops container -->
            <div id="sweat-container" class="absolute top-0 right-0 w-full h-full pointer-events-none"></div>
        </div>

        <!-- Stats -->
        <div class="flex justify-between mb-4 pixel-font text-xs">
            <span class="text-green-600">YES POWER: <span id="yes-power">100%</span></span>
            <span class="text-red-600">REJECTION CHANCE: <span id="rejection-chance">0.01%</span></span>
        </div>

        <!-- Button Battle Arena -->
        <div id="button-arena" class="relative h-40 flex items-center justify-center">
            <button id="yes-btn" class="btn-yes px-8 py-4 rounded text-black font-bold z-20">
                YES!!! ❤️
            </button>
            
            <button id="no-btn" class="btn-no escape-btn px-6 py-3 rounded absolute z-30">
                NO 💔
            </button>
        </div>

        <!-- Message Area -->
        <div id="message-area" class="mt-4 h-16 flex items-center justify-center">
            <p id="funny-text" class="comic-font text-xl text-purple-600 opacity-0 transition-opacity"></p>
        </div>

        <!-- Attempt Counter -->
        <div class="text-center mt-2 pixel-font text-xs text-gray-500">
            ATTEMPTS TO CLICK NO: <span id="attempt-count" class="text-red-600 font-bold">0</span>
        </div>
    </div>

    <!-- Rage Text Overlay -->
    <div id="rage-text" class="rage-text">NICE TRY!</div>

    <!-- Boss Mode: Typing Game -->
    <div id="typing-boss" class="boss-mode">
        <h2 class="comic-font text-4xl text-yellow-400 mb-4">PHASE 1: TYPING TEST</h2>
        <p class="text-white mb-4 pixel-font text-xs">TYPE THE WORDS TO WEAKEN THE NO BUTTON!</p>
        <div id="typing-words" class="typing-game mb-6"></div>
        <input type="text" id="typing-input" class="math-input" placeholder="TYPE HERE" autocomplete="off">
        <p id="typing-timer" class="text-red-500 pixel-font mt-4">TIME: 10</p>
    </div>

    <!-- Boss Mode: Dodge Game -->
    <div id="dodge-boss" class="boss-mode">
        <h2 class="comic-font text-4xl text-cyan-400 mb-4">PHASE 2: DODGE THE NO</h2>
        <p class="text-white mb-4 pixel-font text-xs">USE ARROW KEYS TO DODGE!</p>
        <div class="dodge-game" id="dodge-container">
            <div class="player" id="dodge-player"></div>
        </div>
        <p id="dodge-score" class="text-green-400 pixel-font mt-4">SCORE: 0</p>
    </div>

    <!-- Boss Mode: Math Problem -->
    <div id="math-boss" class="boss-mode">
        <h2 class="comic-font text-4xl text-pink-400 mb-4">FINAL PHASE: MATH</h2>
        <p class="text-white mb-4 pixel-font text-xs">SOLVE TO PROVE YOUR LOVE!</p>
        <div id="math-problem" class="math-problem"></div>
        <input type="number" id="math-input" class="math-input" placeholder="ANSWER">
        <p id="math-timer" class="text-red-500 pixel-font mt-4">TIME: 5</p>
    </div>

    <!-- Victory Screen -->
    <div id="victory-screen" class="fixed inset-0 bg-gradient-to-br from-pink-400 via-purple-400 to-indigo-400 hidden items-center justify-center flex-col z-[3000]">
        <div class="text-9xl mb-4 animate-pulse">💕🎉💕</div>
        <h1 class="comic-font text-6xl text-white mb-4" style="text-shadow: 4px 4px 0 #000;">VICTORY!</h1>
        <p class="pixel-font text-white text-lg mb-8 text-center max-w-md">
            YOU'VE DEFEATED THE NO BUTTON!<br>
            VALENTINE STATUS: <span class="text-yellow-300">ACCEPTED</span>
        </p>
        <div class="bg-white rounded-xl p-6 border-4 border-black shadow-[8px_8px_0_#000] max-w-sm mx-4">
            <p class="comic-font text-2xl text-pink-600 text-center mb-2">💌 Love Confirmed! 💌</p>
            <p class="text-gray-600 text-center text-sm">You may now collect your reward: infinite hugs 🫂</p>
        </div>
        <button onclick="location.reload()" class="mt-8 bg-yellow-400 border-4 border-black px-8 py-4 rounded comic-font text-xl shadow-[6px_6px_0_#000] hover:translate-y-1 hover:shadow-[4px_4px_0_#000] transition-all">
            PLAY AGAIN 🎮
        </button>
    </div>

    <!-- Audio Context Warning -->
    <div id="start-overlay" class="fixed inset-0 bg-black/80 flex items-center justify-center z-[4000]">
        <div class="bg-white border-4 border-pink-500 p-8 rounded-2xl text-center max-w-md mx-4">
            <div class="text-6xl mb-4">🎮</div>
            <h2 class="comic-font text-3xl text-pink-600 mb-4">READY TO PLAY?</h2>
            <p class="mb-6 text-gray-600">Warning: This game contains intense meme action and an impossible "No" button.</p>
            <button id="start-game-btn" class="bg-pink-500 text-white px-8 py-4 rounded-full comic-font text-xl hover:bg-pink-600 transition">
                START GAME ❤️
            </button>
        </div>
    </div>

    <script>
        // Game State
        const state = {
            attempts: 0,
            health: 100,
            phase: 1,
            isMoving: false,
            gameStarted: false,
            yesPower: 100
        };

        // Elements
        const noBtn = document.getElementById('no-btn');
        const yesBtn = document.getElementById('yes-btn');
        const mainCard = document.getElementById('main-card');
        const funnyText = document.getElementById('funny-text');
        const rageText = document.getElementById('rage-text');
        const attemptCount = document.getElementById('attempt-count');
        const healthFill = document.getElementById('health-fill');
        const characterDisplay = document.getElementById('character-display');
        const dialogueText = document.getElementById('dialogue-text');
        const yesPower = document.getElementById('yes-power');
        const rejectionChance = document.getElementById('rejection-chance');

        // Message Arrays
        const phase1Messages = [
            "Nice try! 😏",
            "Too slow! 🐌",
            "Skill issue! 🎮",
            "Button says no to 'No'! 🚫",
            "Error 404: Rejection not found 😎",
            "You can't escape destiny! 💫",
            "Gravity shifted... towards YES! 🌍",
            "Are you sure? Look at that face! 🥺",
            "The universe says try again! ✨",
            "That's not the right answer! 📚"
        ];

        const phase2Messages = [
            "THE BUTTON IS ANGRY! 😡",
            "IT'S EVOLVING! 🧬",
            "CRITICAL HIT... ON YOUR FEELINGS! 💥",
            "NO BUTTON USED: CONFUSION! 🤯",
            "IT'S SUPER EFFECTIVE! ⚡",
            "YOU'RE MAKING IT STRONGER! 💪",
            "STOP FEEDING THE TROLL! 🧌",
            "THIS ISN'T EVEN MY FINAL FORM! 👹"
        ];

        const phase3Messages = [
            "REALITY IS BREAKING! 🌌",
            "THE NO BUTTON TRANSCENDS MORTALITY! ☠️",
            "YOU'VE AWOKEN THE ANCIENT ONE! 🐉",
            "CHAOS REIGNS! 🔥",
            "GIVE UP AND CLICK YES! 🙏",
            "YOUR PERSISTENCE IS... ADMIRABLE? 🤔"
        ];

        const rageMessages = [
            "TRY AGAIN!", "CLICK YES!", "WRONG BUTTON!", 
            "NICE TRY!", "TOO SLOW!", "NOT TODAY!",
            "KEEP DREAMING!", "YES IS THE WAY!"
        ];

        const emojis = ["👉👈🥺", "🥹", "🫣", "🤗", "😤", "😈", "🤡", "💀", "👻", "🤖"];

        // Initialize
        document.getElementById('start-game-btn').addEventListener('click', () => {
            document.getElementById('start-overlay').style.display = 'none';
            state.gameStarted = true;
            initAudio();
        });

        // Audio (simulated with visual feedback)
        function initAudio() {
            // Audio would go here - using visual feedback instead
            document.body.classList.add('pulse-glow');
            setTimeout(() => document.body.classList.remove('pulse-glow'), 1000);
        }

        // No Button Logic
        noBtn.addEventListener('mouseenter', handleNoHover);
        noBtn.addEventListener('touchstart', handleNoHover);
        noBtn.addEventListener('click', (e) => {
            e.preventDefault();
            handleNoClick();
        });

        function handleNoHover(e) {
            if (!state.gameStarted || state.isMoving) return;
            
            state.attempts++;
            attemptCount.textContent = state.attempts;
            
            // Phase progression
            if (state.attempts === 5) enterPhase2();
            if (state.attempts === 15) enterPhase3();
            if (state.attempts === 25) startBossMode();

            moveButton();
            updateHealth();
            showMessage();
            evolveCharacter();
            powerUpYes();
        }

        function handleNoClick() {
            showRageText();
            createSweatDrop();
            
            // Glitch effect
            mainCard.classList.add('glitch-effect');
            setTimeout(() => mainCard.classList.remove('glitch-effect'), 300);
        }

        function moveButton() {
            state.isMoving = true;
            
            const arena = document.getElementById('button-arena');
            const arenaRect = arena.getBoundingClientRect();
            
            let newX, newY;
            
            if (state.phase === 1) {
                // Phase 1: Random within arena
                const maxX = arenaRect.width - 100;
                const maxY = arenaRect.height - 50;
                newX = Math.random() * maxX - (maxX / 2);
                newY = Math.random() * maxY - (maxY / 2);
            } else if (state.phase === 2) {
                // Phase 2: Move further, faster
                const angle = Math.random() * Math.PI * 2;
                const distance = 100 + Math.random() * 100;
                newX = Math.cos(angle) * distance;
                newY = Math.sin(angle) * distance;
            } else {
                // Phase 3: Teleport anywhere on screen
                const screenX = Math.random() * (window.innerWidth - 100);
                const screenY = Math.random() * (window.innerHeight - 50);
                noBtn.style.position = 'fixed';
                noBtn.style.left = screenX + 'px';
                noBtn.style.top = screenY + 'px';
                noBtn.style.transform = 'none';
                
                // Random rotation and scale
                const rot = Math.random() * 360;
                const scale = 0.5 + Math.random();
                noBtn.style.transform = `rotate(${rot}deg) scale(${scale})`;
                
                state.isMoving = false;
                return;
            }
            
            const rotation = Math.random() * 30 - 15;
            const scale = 1 - (state.attempts * 0.02); // Gets smaller
            
            noBtn.style.transform = `translate(${newX}px, ${newY}px) rotate(${rotation}deg) scale(${Math.max(0.5, scale)})`;
            
            // Add shake to card
            mainCard.classList.add('shake-crazy');
            setTimeout(() => mainCard.classList.remove('shake-crazy'), 300);
            
            setTimeout(() => { state.isMoving = false; }, 150);
        }

        function updateHealth() {
            state.health = Math.max(0, 100 - (state.attempts * 3));
            healthFill.style.width = state.health + '%';
            
            // Change color based on health
            if (state.health < 30) {
                healthFill.style.background = 'linear-gradient(90deg, #ff0000, #660000)';
            }
        }

        function showMessage() {
            let messages = phase1Messages;
            if (state.phase === 2) messages = phase2Messages;
            if (state.phase === 3) messages = phase3Messages;
            
            const msg = messages[Math.floor(Math.random() * messages.length)];
            funnyText.textContent = msg;
            funnyText.style.opacity = 1;
            
            setTimeout(() => funnyText.style.opacity = 0, 2000);
        }

        function evolveCharacter() {
            const emojiIndex = Math.min(Math.floor(state.attempts / 3), emojis.length - 1);
            characterDisplay.textContent = emojis[emojiIndex];
            
            // Update dialogue
            const dialogues = [
                "Will you be my Valentine?",
                "P-please? 🥺",
                "I'm waiting... ⏰",
                "You're making me sad 😢",
                "STOP CLICKING NO! 😤",
                "I'M BECOMING UNSTOPPABLE! 😈",
                "REALITY IS MINE TO COMMAND! 👹",
                "ACCEPT YOUR FATE! 💀",
                "YES IS THE ONLY OPTION! 🤖",
                "RESISTANCE IS FUTILE! 🌀"
            ];
            
            const dialogueIndex = Math.min(Math.floor(state.attempts / 3), dialogues.length - 1);
            dialogueText.textContent = dialogues[dialogueIndex];
        }

        function powerUpYes() {
            state.yesPower += 10;
            yesPower.textContent = state.yesPower + '%';
            
            const rejection = Math.max(0.01, 100 - state.yesPower).toFixed(2);
            rejectionChance.textContent = rejection + '%';
            
            // Grow yes button
            const scale = 1 + (state.attempts * 0.08);
            yesBtn.style.transform = `scale(${scale})`;
        }

        function showRageText() {
            const msg = rageMessages[Math.floor(Math.random() * rageMessages.length)];
            rageText.textContent = msg;
            rageText.style.left = (Math.random() * 60 + 20) + '%';
            rageText.style.top = (Math.random() * 60 + 20) + '%';
            rageText.classList.add('show');
            
            setTimeout(() => rageText.classList.remove('show'), 600);
        }

        function createSweatDrop() {
            const sweat = document.createElement('div');
            sweat.className = 'sweat-drop';
            sweat.textContent = '💧';
            sweat.style.left = Math.random() * 80 + 10 + '%';
            sweat.style.top = '20%';
            document.getElementById('sweat-container').appendChild(sweat);
            setTimeout(() => sweat.remove(), 1000);
        }

        function enterPhase2() {
            state.phase = 2;
            document.body.style.animation = 'gradientShift 2s ease infinite';
            noBtn.classList.add('pulse-glow');
            showRageText();
        }

        function enterPhase3() {
            state.phase = 3;
            mainCard.style.animation = 'shakeCrazy 2s infinite';
            document.getElementById('bg-emojis').classList.add('spin-super');
        }

        // Boss Mode System
        function startBossMode() {
            document.getElementById('typing-boss').style.display = 'flex';
            startTypingGame();
        }

        // Typing Game
        function startTypingGame() {
            const words = ['LOVE', 'HEART', 'CUPID', 'ROSE', 'HUG', 'KISS', 'FOREVER'];
            const container = document.getElementById('typing-words');
            const input = document.getElementById('typing-input');
            
            container.innerHTML = words.map(w => `<span class="target-word">${w}</span>`).join('');
            
            let timeLeft = 10;
            const timer = setInterval(() => {
                timeLeft--;
                document.getElementById('typing-timer').textContent = `TIME: ${timeLeft}`;
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    document.getElementById('typing-boss').style.display = 'none';
                    document.getElementById('dodge-boss').style.display = 'flex';
                    startDodgeGame();
                }
            }, 1000);
            
            input.focus();
            input.addEventListener('input', () => {
                const val = input.value.toUpperCase();
                const wordElements = container.querySelectorAll('.target-word');
                wordElements.forEach(el => {
                    if (el.textContent === val) {
                        el.classList.add('correct');
                        input.value = '';
                        state.health -= 10;
                        updateHealth();
                    }
                });
            });
        }

        // Dodge Game
        function startDodgeGame() {
            const container = document.getElementById('dodge-container');
            const player = document.getElementById('dodge-player');
            let playerX = 185;
            let score = 0;
            
            document.addEventListener('keydown', (e) => {
                if (e.key === 'ArrowLeft' && playerX > 0) playerX -= 30;
                if (e.key === 'ArrowRight' && playerX < 370) playerX += 30;
                player.style.left = playerX + 'px';
            });
            
            const gameInterval = setInterval(() => {
                const obstacle = document.createElement('div');
                obstacle.className = 'obstacle';
                obstacle.style.left = Math.random() * 370 + 'px';
                container.appendChild(obstacle);
                
                let obstacleY = -30;
                const fallInterval = setInterval(() => {
                    obstacleY += 5;
                    obstacle.style.top = obstacleY + 'px';
                    
                    // Collision detection
                    const obstacleRect = obstacle.getBoundingClientRect();
                    const playerRect = player.getBoundingClientRect();
                    
                    if (obstacleRect.bottom > playerRect.top && 
                        obstacleRect.left < playerRect.right && 
                        obstacleRect.right > playerRect.left &&
                        obstacleRect.top < playerRect.bottom) {
                        // Hit!
                        obstacle.remove();
                        clearInterval(fallInterval);
                        score += 10;
                        document.getElementById('dodge-score').textContent = `SCORE: ${score}`;
                        
                        if (score >= 50) {
                            clearInterval(gameInterval);
                            document.getElementById('dodge-boss').style.display = 'none';
                            document.getElementById('math-boss').style.display = 'flex';
                            startMathGame();
                        }
                    }
                    
                    if (obstacleY > 300) {
                        obstacle.remove();
                        clearInterval(fallInterval);
                    }
                }, 20);
            }, 800);
        }

        // Math Game
        function startMathGame() {
            const num1 = Math.floor(Math.random() * 50) + 10;
            const num2 = Math.floor(Math.random() * 50) + 10;
            const answer = num1 + num2;
            
            document.getElementById('math-problem').textContent = `${num1} + ${num2} = ?`;
            
            const input = document.getElementById('math-input');
            input.value = '';
            input.focus();
            
            let timeLeft = 5;
            const timer = setInterval(() => {
                timeLeft--;
                document.getElementById('math-timer').textContent = `TIME: ${timeLeft}`;
                
                if (timeLeft <= 0) {
                    clearInterval(timer);
                    // Wrong answer - restart math
                    startMathGame();
                }
            }, 1000);
            
            input.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    if (parseInt(input.value) === answer) {
                        clearInterval(timer);
                        showVictory();
                    }
                }
            });
        }

        // Victory
        function showVictory() {
            document.getElementById('math-boss').style.display = 'none';
            document.getElementById('victory-screen').classList.remove('hidden');
            document.getElementById('victory-screen').classList.add('flex');
            
            // Massive confetti
            for (let i = 0; i < 200; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti-particle';
                    confetti.style.left = Math.random() * 100 + 'vw';
                    confetti.style.top = '-20px';
                    confetti.style.background = ['#ff006e', '#8338ec', '#3a86ff', '#06ffa5', '#ffbe0b'][Math.floor(Math.random() * 5)];
                    confetti.style.animation = `confetti-fall ${3 + Math.random() * 2}s linear forwards`;
                    document.body.appendChild(confetti);
                }, i * 20);
            }
        }

        // Yes Button - Instant Victory
        yesBtn.addEventListener('click', () => {
            // Create heart explosion
            for (let i = 0; i < 50; i++) {
                const heart = document.createElement('div');
                heart.textContent = '💖';
                heart.style.position = 'fixed';
                heart.style.left = '50%';
                heart.style.top = '50%';
                heart.style.fontSize = '2rem';
                heart.style.pointerEvents = 'none';
                heart.style.zIndex = '9999';
                
                const angle = (Math.PI * 2 * i) / 50;
                const velocity = 200 + Math.random() * 200;
                const tx = Math.cos(angle) * velocity;
                const ty = Math.sin(angle) * velocity;
                
                heart.style.transition = 'all 1s ease-out';
                document.body.appendChild(heart);
                
                setTimeout(() => {
                    heart.style.transform = `translate(${tx}px, ${ty}px) scale(0)`;
                    heart.style.opacity = '0';
                }, 10);
                
                setTimeout(() => heart.remove(), 1000);
            }
            
            setTimeout(() => {
                document.getElementById('main-card').style.display = 'none';
                showVictory();
            }, 500);
        });

        // Easter egg: Konami code
        let konami = [];
        document.addEventListener('keydown', (e) => {
            konami.push(e.key);
            if (konami.length > 10) konami.shift();
            if (konami.join('').includes('ArrowUpArrowUpArrowDownArrowDown')) {
                state.health = 0;
                updateHealth();
                document.body.style.filter = 'invert(1)';
                setTimeout(() => document.body.style.filter = '', 1000);
            }
        });
    </script>
</body>
</html>
