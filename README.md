<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rishi | Cyber-Romance Lab</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Fira+Code:wght@300;500&family=Orbitron:wght@400;700&family=Sacramento&display=swap');

        :root {
            --neon-pink: #ff2d75;
            --neon-green: #0f0;
            --dark-bg: #050505;
        }

        body {
            background-color: var(--dark-bg);
            color: #fff;
            font-family: 'Fira Code', monospace;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        h1, h2 {
            font-family: 'Orbitron', sans-serif;
        }

        /* Canvas Background */
        #matrix-canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
            opacity: 0.3;
        }

        /* Glassmorphism Navbar */
        nav {
            background: rgba(5, 5, 5, 0.8);
            backdrop-filter: blur(12px);
            border-bottom: 1px solid rgba(255, 45, 117, 0.2);
            position: fixed;
            width: 100%;
            z-index: 100;
        }

        /* Neon Glowing Text */
        .neon-text-pink {
            text-shadow: 0 0 10px var(--neon-pink), 0 0 20px var(--neon-pink);
        }

        .neon-text-green {
            text-shadow: 0 0 10px var(--neon-green), 0 0 20px var(--neon-green);
            color: var(--neon-green);
        }

        /* Heart Animation */
        .heart-beat {
            animation: heartbeat 1.5s infinite;
            filter: drop-shadow(0 0 15px var(--neon-pink));
        }

        @keyframes heartbeat {
            0% { transform: scale(1); }
            15% { transform: scale(1.3); }
            30% { transform: scale(1); }
            45% { transform: scale(1.15); }
            60% { transform: scale(1); }
        }

        /* Science Experiment Bubbles */
        .bubble {
            position: absolute;
            background: rgba(255, 45, 117, 0.3);
            border-radius: 50%;
            pointer-events: none;
            animation: float 4s infinite ease-in;
        }

        @keyframes float {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            50% { opacity: 0.8; }
            100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }

        /* Terminal Style Section */
        .terminal-box {
            background: rgba(0, 0, 0, 0.9);
            border: 1px solid var(--neon-green);
            box-shadow: 0 0 20px rgba(0, 255, 0, 0.1);
            padding: 20px;
            border-radius: 8px;
            word-wrap: break-word;
        }

        /* Glitch Effect */
        .glitch {
            position: relative;
        }
        .glitch::before {
            content: attr(data-text);
            position: absolute;
            left: -2px;
            text-shadow: 2px 0 blue;
            clip: rect(44px, 450px, 56px, 0);
            animation: glitch-anim 5s infinite linear alternate-reverse;
        }

        @keyframes glitch-anim {
            0% { clip: rect(31px, 9999px, 94px, 0); }
            20% { clip: rect(62px, 9999px, 42px, 0); }
            100% { clip: rect(89px, 9999px, 98px, 0); }
        }

        .insta-btn {
            background: linear-gradient(45deg, #f09433 0%,#e6683c 25%,#dc2743 50%,#cc2366 75%,#bc1888 100%); 
            transition: 0.3s;
            touch-action: manipulation;
        }
        .insta-btn:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 0 25px var(--neon-pink);
        }

        /* Mobile Menu */
        #mobile-menu {
            transition: transform 0.3s ease-in-out;
            transform: translateY(-100%);
        }
        #mobile-menu.active {
            transform: translateY(0);
        }

    </style>
</head>
<body>

    <!-- Matrix Canvas -->
    <canvas id="matrix-canvas"></canvas>

    <!-- Navigation -->
    <nav class="py-4 px-6 md:px-8 flex justify-between items-center">
        <div class="text-xl md:text-2xl font-bold neon-text-pink tracking-widest">RISHI</div>
        
        <!-- Desktop Menu -->
        <div class="hidden md:flex space-x-8 text-sm uppercase tracking-wider">
            <a href="#home" class="hover:text-[#ff2d75] transition">Home</a>
            <a href="#lab" class="hover:text-[#ff2d75] transition">The Lab</a>
            <a href="#hacking" class="hover:text-[#ff2d75] transition">Terminal</a>
            <a href="#contact" class="hover:text-[#ff2d75] transition">Connect</a>
        </div>

        <!-- Mobile Menu Toggle -->
        <div class="md:hidden cursor-pointer text-2xl" id="menu-toggle">
             <i class="fas fa-bars" id="menu-icon"></i>
        </div>
    </nav>

    <!-- Mobile Menu Overlay -->
    <div id="mobile-menu" class="fixed top-0 left-0 w-full h-auto bg-black/95 z-[90] flex flex-col items-center py-20 space-y-6 md:hidden border-b border-pink-500">
        <a href="#home" class="text-xl hover:text-pink-500 nav-link">Home</a>
        <a href="#lab" class="text-xl hover:text-pink-500 nav-link">The Lab</a>
        <a href="#hacking" class="text-xl hover:text-pink-500 nav-link">Terminal</a>
        <a href="#contact" class="text-xl hover:text-pink-500 nav-link">Connect</a>
    </div>

    <!-- Hero Section -->
    <section id="home" class="min-h-screen flex flex-col justify-center items-center text-center px-6 relative overflow-hidden">
        <div class="science-vial mb-6">
             <i class="fas fa-flask-vial text-5xl md:text-6xl neon-text-green animate-pulse"></i>
        </div>
        <h1 class="text-4xl sm:text-5xl md:text-7xl font-bold mb-4 glitch" data-text="RISHI'S WORLD">RISHI'S WORLD</h1>
        <p class="text-lg md:text-2xl text-pink-200 mb-8 max-w-2xl font-light italic" style="font-family: 'Sacramento', cursive;">
            "Hacking your heart with the chemistry of love and code."
        </p>
        <a href="#contact" class="heart-beat">
            <i class="fas fa-heart text-5xl md:text-6xl text-red-500"></i>
        </a>
        <p class="mt-6 text-[10px] md:text-xs tracking-widest uppercase opacity-50">Click to Initialize Connection</p>
    </section>

    <!-- Science Section -->
    <section id="lab" class="py-20 px-6 md:px-8 max-w-6xl mx-auto">
        <h2 class="text-2xl md:text-3xl font-bold mb-12 text-center neon-text-green uppercase tracking-widest">Experimental Data</h2>
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 md:gap-8">
            <div class="terminal-box border-pink-500">
                <i class="fas fa-dna text-2xl md:text-3xl mb-4 text-pink-500"></i>
                <h3 class="font-bold mb-2">Genetic Sync</h3>
                <p class="text-xs md:text-sm opacity-80">Calculating the molecular compatibility between your soul and Rishi's digital abyss.</p>
            </div>
            <div class="terminal-box">
                <i class="fas fa-microscope text-2xl md:text-3xl mb-4 neon-text-green"></i>
                <h3 class="font-bold mb-2">Subatomic Love</h3>
                <p class="text-xs md:text-sm opacity-80">Observed particles behaving in entanglement. Love is the only constant variable.</p>
            </div>
            <div class="terminal-box border-blue-500 sm:col-span-2 md:col-span-1">
                <i class="fas fa-atom text-2xl md:text-3xl mb-4 text-blue-500"></i>
                <h3 class="font-bold mb-2">Neural Breach</h3>
                <p class="text-xs md:text-sm opacity-80">Overriding system safeguards to inject affection. Protocol: RISHI_HEART_V2.exe</p>
            </div>
        </div>
    </section>

    <!-- Hacking Terminal Section -->
    <section id="hacking" class="py-16 bg-black/50">
        <div class="max-w-4xl mx-auto px-6">
            <div class="terminal-box font-mono text-xs sm:text-sm md:text-base min-h-[250px] overflow-hidden">
                <div class="flex items-center space-x-2 mb-4 border-b border-green-900 pb-2">
                    <div class="w-2 h-2 md:w-3 md:h-3 rounded-full bg-red-500"></div>
                    <div class="w-2 h-2 md:w-3 md:h-3 rounded-full bg-yellow-500"></div>
                    <div class="w-2 h-2 md:w-3 md:h-3 rounded-full bg-green-500"></div>
                    <span class="ml-2 md:ml-4 opacity-50 text-[10px] md:text-xs">rishi_override.sh — 80×24</span>
                </div>
                <div id="terminal-content" class="space-y-1">
                    <p class="text-green-500">> Initializing heart_hack_protocol...</p>
                    <p class="text-green-500">> Scanning for Rishi (@abyss.creep) presence...</p>
                    <p class="text-blue-400">> Found target in the emotional database.</p>
                    <p class="text-pink-500">> Warning: Critical Romantic Radiation.</p>
                    <p class="text-green-500">> Bypass successful. Firewall disabled.</p>
                    <p class="text-white animate-pulse">_</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Instagram & Contact -->
    <section id="contact" class="py-24 flex flex-col items-center justify-center relative overflow-hidden px-6">
        <div class="absolute inset-0 flex justify-center items-center opacity-10 pointer-events-none">
            <i class="fas fa-heart text-[15rem] md:text-[25rem] text-pink-500 blur-2xl"></i>
        </div>
        
        <h2 class="text-3xl md:text-4xl font-bold mb-12 z-10 text-center uppercase tracking-widest">Follow Rishi</h2>
        
        <div class="z-10 text-center w-full">
            <div class="relative inline-block group">
                <!-- Large Heart Animation -->
                <div class="heart-beat cursor-pointer mb-10">
                    <a href="https://instagram.com/abyss.creep" target="_blank" class="block">
                        <div class="w-32 h-32 md:w-48 md:h-48 rounded-full flex items-center justify-center bg-black border-4 border-pink-500 shadow-[0_0_40px_rgba(255,45,117,0.4)] overflow-hidden">
                            <i class="fab fa-instagram text-6xl md:text-8xl text-white"></i>
                        </div>
                    </a>
                </div>
                
                <div class="mt-4">
                    <a href="https://instagram.com/abyss.creep" target="_blank" 
                       class="insta-btn px-6 py-3 md:px-8 md:py-4 rounded-full font-bold text-lg md:text-xl inline-flex items-center space-x-3">
                        <span>@abyss.creep</span>
                        <i class="fas fa-external-link-alt text-xs"></i>
                    </a>
                </div>
            </div>
        </div>
        
        <div class="mt-24 text-gray-500 text-[10px] md:text-xs tracking-widest uppercase text-center">
            Made with <i class="fas fa-heart text-red-600"></i> and <i class="fas fa-code text-green-500"></i> by Rishi
        </div>
    </section>

    <script>
        // Matrix Rain Implementation
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        resizeCanvas();

        const chars = "01❤⚛☣☠♥";
        const fontSize = 16;
        let columns = canvas.width / fontSize;
        let drops = [];

        function initDrops() {
            columns = canvas.width / fontSize;
            drops = [];
            for (let x = 0; x < columns; x++) {
                drops[x] = 1;
            }
        }
        initDrops();

        function drawMatrix() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
            ctx.fillRect(0, 0, canvas.width, canvas.height);

            ctx.font = fontSize + "px monospace";

            for (let i = 0; i < drops.length; i++) {
                const text = chars.charAt(Math.floor(Math.random() * chars.length));
                if(Math.random() > 0.95) ctx.fillStyle = "#0f0";
                else ctx.fillStyle = "#ff2d75";

                ctx.fillText(text, i * fontSize, drops[i] * fontSize);

                if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                drops[i]++;
            }
        }

        setInterval(drawMatrix, 35);

        // Science Bubbles Generator
        function createBubble() {
            const section = document.getElementById('home');
            const bubble = document.createElement('div');
            bubble.classList.add('bubble');
            
            const sizeValue = Math.random() * 15 + 8;
            bubble.style.width = sizeValue + 'px';
            bubble.style.height = sizeValue + 'px';
            
            bubble.style.left = Math.random() * 100 + 'vw';
            bubble.style.animationDuration = Math.random() * 3 + 2 + 's';
            
            section.appendChild(bubble);
            
            setTimeout(() => {
                bubble.remove();
            }, 5000);
        }

        setInterval(createBubble, 400);

        // Mobile Menu Toggle Logic
        const menuToggle = document.getElementById('menu-toggle');
        const mobileMenu = document.getElementById('mobile-menu');
        const menuIcon = document.getElementById('menu-icon');
        const navLinks = document.querySelectorAll('.nav-link');

        function toggleMenu() {
            mobileMenu.classList.toggle('active');
            menuIcon.classList.toggle('fa-bars');
            menuIcon.classList.toggle('fa-times');
        }

        menuToggle.addEventListener('click', toggleMenu);
        
        navLinks.forEach(link => {
            link.addEventListener('click', () => {
                if(mobileMenu.classList.contains('active')) toggleMenu();
            });
        });

        window.addEventListener('resize', () => {
            resizeCanvas();
            initDrops();
        });

        // Typewriter effect for terminal simulation
        const terminalText = [
            "> Accessing rishi_romance_v2.dll...",
            "> Patching heart_bypass.v3",
            "> System Status: Rishi Mode Activated.",
            "> Connecting to @abyss.creep server...",
            "> CONNECTION SECURE. LOVE INJECTED."
        ];
        
        let lineIndex = 0;
        const terminalContainer = document.getElementById('terminal-content');

        function addTerminalLine() {
            if(lineIndex < terminalText.length) {
                const p = document.createElement('p');
                p.className = lineIndex % 2 === 0 ? "text-green-500" : "text-pink-400";
                p.innerHTML = terminalText[lineIndex];
                terminalContainer.insertBefore(p, terminalContainer.lastElementChild);
                lineIndex++;
                setTimeout(addTerminalLine, 2200);
            }
        }
        
        setTimeout(addTerminalLine, 2500);
    </script>
</body>
</html>
