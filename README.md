<!DOCTYPE html>
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

        h1, h2, h3 {
            font-family: 'Orbitron', sans-serif;
        }

        /* Hacking Gate-Keeper */
        #gate-keeper {
            position: fixed;
            inset: 0;
            background: #000;
            z-index: 2000;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            transition: transform 1s cubic-bezier(0.85, 0, 0.15, 1), opacity 1s;
        }

        .cat-btn {
            font-size: 6rem;
            cursor: pointer;
            color: var(--neon-green);
            filter: drop-shadow(0 0 15px var(--neon-green));
            animation: cat-glitch 2s infinite;
        }

        @keyframes cat-glitch {
            0% { transform: scale(1); opacity: 1; }
            5% { transform: translate(-5px, 2px); opacity: 0.8; color: var(--neon-pink); }
            10% { transform: translate(5px, -2px); opacity: 1; color: var(--neon-green); }
            15% { transform: translate(0); }
            100% { transform: translate(0); }
        }

        /* Matrix Background */
        #matrix-canvas {
            position: fixed;
            top: 0;
            left: 0;
            z-index: -1;
            opacity: 0.3;
        }

        /* Scroll Reveal Animation */
        .reveal {
            opacity: 0;
            transform: translateY(30px);
            transition: all 1s ease-out;
        }
        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        /* Neon & Heart Pulsing */
        .neon-text-pink { text-shadow: 0 0 10px var(--neon-pink), 0 0 20px var(--neon-pink); }
        .neon-text-green { text-shadow: 0 0 10px var(--neon-green), 0 0 20px var(--neon-green); color: var(--neon-green); }

        .heart-beat {
            animation: heartbeat 1.2s infinite cubic-bezier(0.215, 0.61, 0.355, 1);
            filter: drop-shadow(0 0 20px var(--neon-pink));
        }

        /* Terminal Box */
        .terminal-box {
            background: rgba(0, 0, 0, 0.85);
            border: 1px solid var(--neon-green);
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.1);
            padding: 25px;
            border-radius: 15px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            min-width: 280px;
        }

        /* Profile Glitch */
        .profile-card {
            background: linear-gradient(135deg, rgba(255,45,117,0.1) 0%, rgba(15,255,0,0.05) 100%);
            border: 1px solid rgba(255,255,255,0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
        }

        .glitch-text { position: relative; }
        .glitch-text::before {
            content: attr(data-text);
            position: absolute;
            top: 0; left: 0; width: 100%; height: 100%;
            color: #0ff; z-index: -1;
            animation: glitch-anim 2s infinite linear alternate-reverse;
        }

        @keyframes glitch-anim {
            0% { clip-path: inset(20% 0 30% 0); transform: translate(-2px, -2px); }
            100% { clip-path: inset(60% 0 10% 0); transform: translate(2px, 2px); }
        }

        .insta-btn {
            background: linear-gradient(45deg, #f09433 0%,#e6683c 25%,#dc2743 50%,#cc2366 75%,#bc1888 100%); 
            transition: 0.3s;
        }

        #music-toggle {
            position: fixed;
            bottom: 30px;
            right: 30px;
            z-index: 1000;
            background: rgba(0, 0, 0, 0.7);
            border: 2px solid var(--neon-pink);
            width: 60px; height: 60px;
            border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            cursor: pointer;
        }
        
        section { padding: 100px 20px; }
        .topics-row { display: flex; overflow-x: auto; gap: 25px; padding: 30px 10px; scrollbar-width: none; }
        .topics-row::-webkit-scrollbar { display: none; }
    </style>
</head>
<body>

    <!-- GATE KEEPER PAGE -->
    <div id="gate-keeper">
        <div id="gate-logs" class="absolute top-10 left-10 text-[10px] text-green-500 font-mono opacity-50 pointer-events-none"></div>
        <div class="cat-btn" id="cat-trigger">
            <i class="fas fa-cat"></i>
        </div>
        <div class="mt-12 text-center">
            <h2 class="neon-text-green font-bold tracking-[0.6em] text-lg">ACCESSING ABYSS</h2>
            <p class="text-[10px] opacity-40 mt-3 uppercase" id="gate-status">Click to override security protocols</p>
        </div>
    </div>

    <!-- AUDIO -->
    <audio id="bg-music" loop>
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <div id="music-toggle">
        <i class="fas fa-volume-mute text-pink-500 text-xl" id="music-icon"></i>
    </div>

    <canvas id="matrix-canvas"></canvas>

    <!-- [HOME] -->
    <section id="home" class="min-h-screen flex flex-col justify-center items-center text-center relative">
        <div class="mb-10">
            <i class="fas fa-vial text-7xl neon-text-green animate-pulse"></i>
        </div>
        <h1 class="text-7xl md:text-[10rem] font-bold mb-6 glitch-text" data-text="RISHI">RISHI</h1>
        <p class="text-2xl md:text-4xl text-pink-200 mb-12 italic" style="font-family: 'Sacramento', cursive;">
            "Engineering the perfect chemistry of love."
        </p>
        <div class="heart-beat cursor-pointer">
            <i class="fas fa-heart text-7xl text-red-500"></i>
        </div>
    </section>

    <!-- [ABOUT] -->
    <section id="about" class="reveal">
        <div class="profile-card p-10 flex flex-col md:flex-row items-center gap-12 max-w-5xl mx-auto">
            <div class="w-56 h-56 rounded-full border-4 border-pink-500 flex-shrink-0 flex items-center justify-center bg-black shadow-[0_0_40px_rgba(255,45,117,0.5)]">
                <i class="fas fa-user-ninja text-7xl text-pink-500 animate-pulse"></i>
            </div>
            <div>
                <h2 class="text-4xl font-bold mb-6 neon-text-pink uppercase tracking-tighter">Bio-Data: Rishi</h2>
                <p class="text-gray-300 text-xl italic leading-relaxed mb-8">
                    "Code ki gehraiyon mein chhupa ek aashiq... jo system ko nahi, dilon ko hack karna jaanta hai."
                </p>
            </div>
        </div>
    </section>

    <!-- [LAB TOPICS] -->
    <section id="lab" class="reveal">
        <h2 class="text-3xl font-bold mb-16 text-center neon-text-green uppercase tracking-[0.4em]">The Research Lab</h2>
        <div class="topics-row">
            <div class="terminal-box border-pink-500">
                <i class="fas fa-atom text-4xl mb-6 text-pink-500"></i>
                <h3 class="text-xl font-bold mb-3">Genetic Sync</h3>
                <p class="text-sm opacity-70">DNA mapping to find the frequency of true affection.</p>
            </div>
            <div class="terminal-box">
                <i class="fas fa-dna text-4xl mb-6 neon-text-green"></i>
                <h3 class="text-xl font-bold mb-3">Quantum Heart</h3>
                <p class="text-sm opacity-70">Where distance doesn't matter, feelings are entangled.</p>
            </div>
            <div class="terminal-box border-blue-500">
                <i class="fas fa-brain text-4xl mb-6 text-blue-500"></i>
                <h3 class="text-xl font-bold mb-3">Neural Link</h3>
                <p class="text-sm opacity-70">Direct mind-to-mind emotional data transfer protocol.</p>
            </div>
        </div>
    </section>

    <!-- [INSTAGRAM] -->
    <section id="contact" class="reveal flex flex-col items-center">
        <h2 class="text-5xl font-bold mb-16 neon-text-pink uppercase tracking-widest text-center">Breach My Reality</h2>
        <div class="heart-beat cursor-pointer mb-12">
            <a href="https://instagram.com/abyss.creep" target="_blank">
                <div class="w-52 h-52 rounded-full flex items-center justify-center bg-black border-4 border-pink-500 shadow-[0_0_60px_rgba(255,45,117,0.6)]">
                    <i class="fab fa-instagram text-8xl text-white"></i>
                </div>
            </a>
        </div>
        <a href="https://instagram.com/abyss.creep" target="_blank" class="bg-white text-black px-12 py-5 rounded-full font-black text-2xl uppercase tracking-[0.2em]">
            @abyss.creep
        </a>
    </section>

    <script>
        const apiKey = ""; // Runtime provides this

        // WAV Conversion Helper
        function pcmToWav(pcmData, sampleRate) {
            const buffer = new ArrayBuffer(44 + pcmData.length);
            const view = new DataView(buffer);
            const writeString = (offset, string) => {
                for (let i = 0; i < string.length; i++) {
                    view.setUint8(offset + i, string.charCodeAt(i));
                }
            };
            writeString(0, 'RIFF');
            view.setUint32(4, 36 + pcmData.length, true);
            writeString(8, 'WAVE');
            writeString(12, 'fmt ');
            view.setUint32(16, 16, true);
            view.setUint16(20, 1, true);
            view.setUint16(22, 1, true);
            view.setUint32(24, sampleRate, true);
            view.setUint32(28, sampleRate * 2, true);
            view.setUint16(32, 2, true);
            view.setUint16(34, 16, true);
            writeString(36, 'data');
            view.setUint32(40, pcmData.length, true);
            for (let i = 0; i < pcmData.length; i++) {
                view.setUint8(44 + i, pcmData[i]);
            }
            return new Blob([buffer], { type: 'audio/wav' });
        }

        async function playHackerWelcome() {
            const text = "Say in a deep, distorted, robotic hacker voice: Welcome to the abyss, Rishi. Heart-hack protocol initiated. Access granted.";
            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-tts:generateContent?key=${apiKey}`;
            const payload = {
                contents: [{ parts: [{ text }] }],
                generationConfig: {
                    responseModalities: ["AUDIO"],
                    speechConfig: { voiceConfig: { prebuiltVoiceConfig: { voiceName: "Iapetus" } } }
                }
            };

            let retries = 0;
            const delays = [1000, 2000, 4000, 8000, 16000];

            async function fetchVoice() {
                try {
                    const response = await fetch(url, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });
                    const result = await response.json();
                    const audioData = result.candidates[0].content.parts[0].inlineData;
                    const mimeType = audioData.mimeType;
                    const sampleRate = parseInt(mimeType.split('rate=')[1]) || 24000;
                    const binaryString = atob(audioData.data);
                    const pcmData = new Uint8Array(binaryString.length);
                    for (let i = 0; i < binaryString.length; i++) pcmData[i] = binaryString.charCodeAt(i);
                    
                    const wavBlob = pcmToWav(pcmData, sampleRate);
                    const audio = new Audio(URL.createObjectURL(wavBlob));
                    audio.play();
                } catch (error) {
                    if (retries < 5) {
                        setTimeout(() => { retries++; fetchVoice(); }, delays[retries]);
                    }
                }
            }
            fetchVoice();
        }

        // Matrix Background
        const canvas = document.getElementById('matrix-canvas');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        const chars = "01❤⚛♥☣";
        const fontSize = 16;
        let drops = Array(Math.floor(canvas.width / fontSize)).fill(1);

        function drawMatrix() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.05)";
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            ctx.font = fontSize + "px monospace";
            drops.forEach((y, i) => {
                const text = chars[Math.floor(Math.random() * chars.length)];
                ctx.fillStyle = Math.random() > 0.9 ? "#0f0" : "#ff2d75";
                ctx.fillText(text, i * fontSize, y * fontSize);
                if (y * fontSize > canvas.height && Math.random() > 0.975) drops[i] = 0;
                drops[i]++;
            });
        }
        setInterval(drawMatrix, 40);

        // Gate Logic
        const gate = document.getElementById('gate-keeper');
        const catTrigger = document.getElementById('cat-trigger');
        const music = document.getElementById('bg-music');
        const musicIcon = document.getElementById('music-icon');
        const statusText = document.getElementById('gate-status');
        let isPlaying = false;

        catTrigger.addEventListener('click', () => {
            statusText.textContent = "BREACHING... ACCESSING AI CORE...";
            playHackerWelcome();
            
            setTimeout(() => {
                gate.style.transform = "translateY(-100%)";
                gate.style.opacity = "0";
                music.play().catch(() => {});
                isPlaying = true;
                musicIcon.className = 'fas fa-volume-up text-pink-500';
            }, 1500);
        });

        document.getElementById('music-toggle').addEventListener('click', () => {
            if (isPlaying) { music.pause(); musicIcon.className = 'fas fa-volume-mute'; }
            else { music.play(); musicIcon.className = 'fas fa-volume-up'; }
            isPlaying = !isPlaying;
        });

        // Reveal Logic
        window.addEventListener('scroll', () => {
            document.querySelectorAll('.reveal').forEach(rev => {
                if (rev.getBoundingClientRect().top < window.innerHeight - 100) rev.classList.add('active');
            });
        });

        window.onresize = () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            drops = Array(Math.floor(canvas.width / fontSize)).fill(1);
        };
    </script>
</body>
</html>
