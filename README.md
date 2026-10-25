<!DOCTYPE html>
<html lang="en" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Devadarshini S | Cyber Portfolio & README Generator</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;500;600;700&family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        pinkcyber: {
                            bg: '#0d0208',
                            card: '#16040f',
                            cardDark: '#0f020a',
                            border: '#ff1493',
                            pink: '#ff1493',
                            magenta: '#ff2a85',
                            bright: '#ff66cc',
                            soft: '#ffb3da',
                            glow: 'rgba(255, 20, 147, 0.35)',
                        }
                    },
                    fontFamily: {
                        mono: ['"Fira Code"', 'monospace'],
                        sans: ['Inter', 'sans-serif'],
                    }
                }
            }
        }
    </script>

    <style>
        /* Retro Pink Scanline & CRT Screen Effects */
        .crt-scanlines {
            background: linear-gradient(
                rgba(18, 0, 10, 0) 50%, 
                rgba(0, 0, 0, 0.35) 50%
            ), linear-gradient(
                90deg,
                rgba(255, 20, 147, 0.04),
                rgba(255, 102, 204, 0.02),
                rgba(255, 42, 133, 0.04)
            );
            background-size: 100% 4px, 6px 100%;
            pointer-events: none;
        }

        .crt-tv-screen {
            box-shadow: inset 0 0 35px rgba(255, 20, 147, 0.3), 0 0 20px rgba(255, 20, 147, 0.4);
            border-radius: 20px / 14px;
        }

        /* 3D Cyber Pink Buttons (rude-shrimp-21 Inspired) */
        .pink-3d-btn {
            background: linear-gradient(135deg, #180310 0%, #29061c 100%);
            border: 1px solid #ff1493;
            box-shadow: 0 5px 0 #b30059, 0 8px 15px rgba(255, 20, 147, 0.4);
            transition: all 0.15s ease-in-out;
            position: relative;
            top: 0;
        }

        .pink-3d-btn:hover {
            top: -2px;
            box-shadow: 0 7px 0 #b30059, 0 12px 20px rgba(255, 20, 147, 0.6);
            background: linear-gradient(135deg, #230418 0%, #3a0828 100%);
        }

        .pink-3d-btn:active {
            top: 4px;
            box-shadow: 0 1px 0 #b30059, 0 4px 8px rgba(255, 20, 147, 0.3);
        }

        /* Continuous Infinite Moving Marquee (swift-panda-38 Inspired) */
        @keyframes marqueeScroll {
            0% { transform: translateX(0%); }
            100% { transform: translateX(-50%); }
        }

        .animate-pink-marquee {
            display: flex;
            width: max-content;
            animation: marqueeScroll 26s linear infinite;
        }

        .animate-pink-marquee:hover {
            animation-play-state: paused;
        }

        /* Glassmorphic Pink Cards */
        .pink-glass-panel {
            background: rgba(22, 4, 15, 0.85);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 20, 147, 0.35);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.6), inset 0 0 15px rgba(255, 20, 147, 0.08);
        }

        .pink-glass-panel:hover {
            border-color: rgba(255, 102, 204, 0.7);
            box-shadow: 0 8px 32px 0 rgba(255, 20, 147, 0.3), inset 0 0 20px rgba(255, 20, 147, 0.15);
        }

        /* Custom Pink Scrollbar */
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #0d0208;
        }
        ::-webkit-scrollbar-thumb {
            background: #ff1493;
            border-radius: 3px;
        }
    </style>
</head>
<body class="bg-pinkcyber-bg text-pinkcyber-soft font-sans min-h-screen relative overflow-x-hidden selection:bg-pinkcyber-pink selection:text-black">

    <!-- Grid Background Pattern in Glowing Pink -->
    <div class="fixed inset-0 pointer-events-none opacity-25" 
         style="background-image: radial-gradient(#ff1493 1px, transparent 1px); background-size: 24px 24px;">
    </div>

    <!-- MAIN CONTAINER -->
    <div class="max-w-7xl mx-auto px-4 py-6 sm:px-6 lg:px-8 relative z-10 space-y-8">

        <!-- HEADER & TOOLBAR -->
        <header class="flex flex-col md:flex-row justify-between items-center gap-4 pb-4 border-b border-pinkcyber-pink/30">
            <div class="flex items-center gap-3">
                <div class="w-3 h-3 rounded-full bg-pinkcyber-bright animate-ping"></div>
                <h1 class="text-xl sm:text-2xl font-mono font-bold text-transparent bg-clip-text bg-gradient-to-r from-pinkcyber-bright via-pinkcyber-pink to-pinkcyber-magenta tracking-wider">
                    DEVADARSHINI S // CYBER_PORTFOLIO
                </h1>
            </div>
            
            <div class="flex flex-wrap items-center gap-3">
                <button id="toggleScanlinesBtn" onclick="toggleScanlines()" class="px-3 py-1.5 text-xs font-mono bg-pinkcyber-card border border-pinkcyber-pink/40 rounded-lg hover:border-pinkcyber-bright text-pinkcyber-bright transition-all flex items-center gap-2">
                    <i class="fa-solid fa-tv"></i> CRT Scanlines: <span id="scanlineStatus">ON</span>
                </button>
                <button onclick="openExportModal()" class="px-4 py-1.5 text-xs font-mono font-semibold bg-pinkcyber-pink text-black rounded-lg hover:bg-pinkcyber-bright transition-all shadow-[0_0_15px_rgba(255,20,147,0.5)] flex items-center gap-2">
                    <i class="fa-solid fa-code"></i> EXPORT README.MD
                </button>
            </div>
        </header>

        <!-- TOP SECTION: RETRO CRT TV MONITOR + TERMINAL HEADER -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-stretch">
            
            <!-- LEFT: RETRO CRT TV MONITOR WITH PHOTO 1 -->
            <div class="lg:col-span-5 pink-glass-panel rounded-2xl p-5 relative flex flex-col justify-between items-center border border-pinkcyber-pink/50">
                
                <!-- Retro Antenna -->
                <div class="relative w-full flex justify-center -mt-8 mb-2">
                    <div class="w-16 h-1 bg-pink-950 rounded-full border border-pinkcyber-pink/50"></div>
                    <!-- Antenna Rods -->
                    <div class="absolute -top-7 left-[38%] w-1 h-8 bg-gradient-to-t from-gray-700 to-pinkcyber-bright -rotate-12 rounded-full">
                        <div class="w-2.5 h-2.5 rounded-full bg-pinkcyber-bright -mt-1 -ml-0.5 animate-pulse shadow-[0_0_8px_#ff66cc]"></div>
                    </div>
                    <div class="absolute -top-7 right-[38%] w-1 h-8 bg-gradient-to-t from-gray-700 to-pinkcyber-bright rotate-12 rounded-full">
                        <div class="w-2.5 h-2.5 rounded-full bg-pinkcyber-bright -mt-1 -ml-0.5 animate-pulse shadow-[0_0_8px_#ff66cc]"></div>
                    </div>
                </div>

                <!-- TV Cabinet Frame Box -->
                <div class="w-full bg-[#17030e] border-4 border-[#330820] rounded-3xl p-4 shadow-2xl relative flex flex-col items-center">
                    
                    <!-- CRT Screen Container -->
                    <div id="crtScreenBox" class="crt-tv-screen relative w-full h-64 sm:h-72 bg-black overflow-hidden flex flex-col items-center justify-center border-2 border-pinkcyber-pink/50">
                        
                        <!-- Scanline Overlay Layer -->
                        <div id="scanlineLayer" class="crt-scanlines absolute inset-0 z-20"></div>

                        <!-- Display Photo 1 inside CRT Screen -->
                        <div class="relative z-10 w-full h-full flex items-center justify-center p-3">
                            
                            <!-- Cyber Pink Corner Brackets -->
                            <div class="absolute top-4 left-4 w-4 h-4 border-t-2 border-l-2 border-pinkcyber-bright z-30"></div>
                            <div class="absolute top-4 right-4 w-4 h-4 border-t-2 border-r-2 border-pinkcyber-bright z-30"></div>
                            <div class="absolute bottom-4 left-4 w-4 h-4 border-b-2 border-l-2 border-pinkcyber-bright z-30"></div>
                            <div class="absolute bottom-4 right-4 w-4 h-4 border-b-2 border-r-2 border-pinkcyber-bright z-30"></div>

                            <!-- Photo 1 Container -->
                            <div class="relative group w-44 h-56 rounded-xl overflow-hidden border-2 border-pinkcyber-pink shadow-[0_0_20px_rgba(255,20,147,0.4)]">
                                <img id="photo1Display" src="./photo1.jpg" onerror="this.onerror=null; this.src='https://images.unsplash.com/photo-1534528741775-53994a69daeb?auto=format&fit=crop&w=600&q=80';" 
                                     class="w-full h-full object-cover filter contrast-110 saturate-110 transition-transform duration-500 group-hover:scale-105" alt="Devadarshini S - photo1.jpg">
                                
                                <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-transparent to-transparent flex flex-col justify-end p-2 text-center">
                                    <span class="font-mono text-[11px] text-pinkcyber-bright tracking-widest font-bold">@just-deva</span>
                                    <span class="font-mono text-[9px] text-pinkcyber-soft/70">./photo1.jpg</span>
                                </div>
                            </div>
                        </div>

                        <!-- Scan Status Overlay Text -->
                        <div class="absolute bottom-2 left-3 z-30 font-mono text-[10px] text-pinkcyber-bright flex items-center gap-1.5">
                            <span class="w-1.5 h-1.5 rounded-full bg-pinkcyber-pink animate-ping"></span>
                            CRT-60Hz // TARGET_LOCKED
                        </div>
                    </div>

                    <!-- TV Controls Dashboard (Power LED & Dials) -->
                    <div class="w-full flex items-center justify-between mt-3 px-2 pt-2 border-t border-pink-950 font-mono text-xs text-pinkcyber-soft">
                        <div class="flex items-center gap-3">
                            <!-- Power LED -->
                            <div class="flex items-center gap-1.5">
                                <div class="w-2.5 h-2.5 rounded-full bg-pinkcyber-pink shadow-[0_0_8px_#ff1493] animate-pulse"></div>
                                <span class="text-[10px] text-pinkcyber-bright">PWR</span>
                            </div>
                            <!-- Speaker Grille -->
                            <div class="flex gap-1">
                                <div class="w-1 h-3 bg-pink-950 rounded-full"></div>
                                <div class="w-1 h-3 bg-pink-950 rounded-full"></div>
                                <div class="w-1 h-3 bg-pink-950 rounded-full"></div>
                            </div>
                        </div>

                        <!-- Dials -->
                        <div class="flex items-center gap-2">
                            <div class="w-5 h-5 rounded-full bg-pink-950 border border-pinkcyber-pink/40 flex items-center justify-center cursor-pointer hover:border-pinkcyber-bright">
                                <div class="w-0.5 h-2 bg-pinkcyber-bright rotate-45"></div>
                            </div>
                            <div class="w-5 h-5 rounded-full bg-pink-950 border border-pinkcyber-pink/40 flex items-center justify-center cursor-pointer hover:border-pinkcyber-bright">
                                <div class="w-0.5 h-2 bg-pinkcyber-bright -rotate-12"></div>
                            </div>
                            <span class="text-[10px] text-pinkcyber-bright">CH 04</span>
                        </div>
                    </div>
                </div>

                <!-- Custom Photo Uploader Helper -->
                <div class="mt-3 text-center w-full">
                    <label class="cursor-pointer text-[11px] font-mono text-pinkcyber-soft/70 hover:text-pinkcyber-bright transition-colors flex items-center justify-center gap-1">
                        <i class="fa-solid fa-camera"></i> Change Photo 1 (Local Preview)
                        <input type="file" accept="image/*" class="hidden" onchange="previewImage(event, 'photo1Display')">
                    </label>
                </div>
            </div>

            <!-- RIGHT: TERMINAL HEADER SCREEN -->
            <div class="lg:col-span-7 pink-glass-panel rounded-2xl p-6 flex flex-col justify-between border border-pinkcyber-pink/50 relative">
                
                <div>
                    <!-- Terminal Window Control Dots -->
                    <div class="flex items-center justify-between pb-3 mb-4 border-b border-pink-950">
                        <div class="flex items-center gap-2">
                            <span class="w-3 h-3 rounded-full bg-pink-600 inline-block"></span>
                            <span class="w-3 h-3 rounded-full bg-pink-500 inline-block"></span>
                            <span class="w-3 h-3 rounded-full bg-pink-400 inline-block"></span>
                            <span class="ml-2 font-mono text-xs text-pinkcyber-soft/80">devadarshini@cyber-terminal: ~</span>
                        </div>
                        <span class="font-mono text-[11px] text-pinkcyber-bright">bash v5.2</span>
                    </div>

                    <!-- Dynamic Typing Banner -->
                    <div class="bg-black/60 border border-pinkcyber-pink/30 rounded-xl p-4 font-mono mb-4">
                        <div class="text-pinkcyber-bright text-sm sm:text-base font-bold flex items-center gap-2 min-h-[32px]">
                            <span id="typingOutput"></span>
                            <span class="w-2 h-5 bg-pinkcyber-pink animate-pulse"></span>
                        </div>
                    </div>

                    <!-- Academic & System Details -->
                    <div class="font-mono text-xs sm:text-sm text-pinkcyber-soft space-y-2.5 leading-relaxed">
                        <div class="flex items-center gap-2">
                            <i class="fa-solid fa-location-dot text-pinkcyber-bright w-4"></i>
                            <span><b>Location:</b> Coimbatore, Tamil Nadu, India</span>
                        </div>
                        <div class="flex items-center gap-2">
                            <i class="fa-solid fa-graduation-cap text-pinkcyber-bright w-4"></i>
                            <span><b>Education:</b> B.Tech CS (Cybersecurity) @ Amrita Vishwa Vidyapeetham</span>
                        </div>
                        <div class="flex items-start gap-2">
                            <i class="fa-solid fa-shield-halved text-pinkcyber-bright w-4 mt-1"></i>
                            <span><b>Focus Areas:</b> Cryptography • AI Security • Digital Twins • Systems Engineering • Programming</span>
                        </div>
                    </div>
                </div>

                <!-- Terminal Quick Status Badges -->
                <div class="mt-6 pt-4 border-t border-pink-950 flex flex-wrap gap-2 font-mono text-xs">
                    <span class="px-2.5 py-1 bg-pinkcyber-pink/15 border border-pinkcyber-pink/50 text-pinkcyber-bright rounded-md">
                        <i class="fa-solid fa-terminal mr-1"></i> status: online
                    </span>
                    <span class="px-2.5 py-1 bg-pinkcyber-pink/15 border border-pinkcyber-pink/50 text-pinkcyber-bright rounded-md">
                        <i class="fa-solid fa-user-shield mr-1"></i> CybeReach Lead
                    </span>
                    <span class="px-2.5 py-1 bg-pinkcyber-pink/15 border border-pinkcyber-pink/50 text-pinkcyber-bright rounded-md">
                        <i class="fa-solid fa-brain mr-1"></i> AI Security & Crypto
                    </span>
                </div>
            </div>
        </div>

        <!-- SOCIAL MEDIA & ACCOUNTS BAR (3D Pink Buttons) -->
        <section class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/50">
            <h2 class="font-mono text-xs text-pinkcyber-bright uppercase tracking-widest mb-4 flex items-center gap-2">
                <i class="fa-solid fa-network-wired"></i> Connected Accounts & Networks
            </h2>
            
            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-4">
                <!-- LinkedIn -->
                <a href="https://linkedin.com/in/your-linkedin-profile" target="_blank" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-brands fa-linkedin text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">LinkedIn</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">@devadarshini</span>
                </a>

                <!-- LeetCode -->
                <a href="https://leetcode.com/your-leetcode-profile" target="_blank" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-solid fa-code text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">LeetCode</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">@just-deva</span>
                </a>

                <!-- HackerRank -->
                <a href="https://hackerrank.com/your-hackerrank-profile" target="_blank" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-brands fa-hackerrank text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">HackerRank</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">@just-deva</span>
                </a>

                <!-- TryHackMe -->
                <a href="https://tryhackme.com/p/your-tryhackme-profile" target="_blank" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-solid fa-user-secret text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">TryHackMe</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">@just-deva</span>
                </a>

                <!-- GitHub -->
                <a href="https://github.com/just-deva" target="_blank" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-brands fa-github text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">GitHub</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">@just-deva</span>
                </a>

                <!-- Email -->
                <a href="mailto:devadarshini@example.com" 
                   class="pink-3d-btn rounded-xl p-3 flex flex-col items-center justify-center text-center group">
                    <i class="fa-solid fa-envelope text-2xl text-pinkcyber-bright mb-1 group-hover:scale-110 transition-transform"></i>
                    <span class="font-mono text-xs font-semibold text-white">Email</span>
                    <span class="text-[10px] font-mono text-pinkcyber-soft/70">Direct Ping</span>
                </a>
            </div>
        </section>

        <!-- MAIN CONTENT GRID: TERMINAL PANELS -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">

            <!-- PANEL 1: cat about_me.md WITH PHOTO 2 ENCLOSED IN MINI TV FRAME -->
            <div class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/40 flex flex-col justify-between">
                <div>
                    <!-- Header -->
                    <div class="flex items-center justify-between pb-3 mb-3 border-b border-pink-950 font-mono text-xs">
                        <span class="text-pinkcyber-bright font-semibold"><i class="fa-solid fa-file-code mr-1"></i> $ cat about_me.md</span>
                        <span class="text-pinkcyber-soft/60">UTF-8</span>
                    </div>

                    <div class="flex flex-col sm:flex-row gap-4 items-start">
                        <!-- Bio Text -->
                        <div class="font-mono text-xs text-pinkcyber-soft leading-relaxed space-y-2 order-2 sm:order-1">
                            <p>
                                Cybersecurity undergraduate at <span class="text-pinkcyber-bright font-semibold">Amrita Vishwa Vidyapeetham</span> specializing in cryptography, AI security, programming, and secure software engineering.
                            </p>
                            <p>
                                Active <span class="text-pinkcyber-bright font-semibold">Student Lead at CybeReach Club</span> managing technical workshops and student attendance engines. Researching <span class="text-pinkcyber-bright">Digital Twin platforms</span> (AWS, Azure, ThingsBoard) and LLM toolchains with Ollama.
                            </p>
                        </div>

                        <!-- PHOTO 2 ENCLOSED INSIDE INTEGRATED MINI TV BOX -->
                        <div class="order-1 sm:order-2 shrink-0 self-center sm:self-start">
                            <div class="bg-[#15020c] border-2 border-pinkcyber-pink rounded-xl p-2 shadow-[0_0_15px_rgba(255,20,147,0.3)] relative text-center">
                                <!-- TV Antenna Visual -->
                                <div class="font-mono text-[9px] text-pinkcyber-bright mb-1 leading-none">\ /<br/>o</div>
                                
                                <!-- Photo Screen -->
                                <div class="w-28 h-36 rounded-lg overflow-hidden border border-pinkcyber-bright/60 relative group">
                                    <img id="photo2Display" src="./photo2.jpg" onerror="this.onerror=null; this.src='https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?auto=format&fit=crop&w=600&q=80';" 
                                         class="w-full h-full object-cover group-hover:scale-105 transition-transform" alt="Devadarshini S - photo2.jpg">
                                </div>

                                <!-- TV Bottom Controls -->
                                <div class="flex items-center justify-between mt-1.5 px-1 font-mono text-[8px] text-pinkcyber-bright">
                                    <span class="flex gap-1">
                                        <span class="w-1.5 h-1.5 rounded-full bg-pinkcyber-bright"></span>
                                        <span class="w-1.5 h-1.5 rounded-full bg-pinkcyber-pink"></span>
                                    </span>
                                    <span>[PWR]</span>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="mt-4 pt-2 text-right">
                    <label class="cursor-pointer text-[10px] font-mono text-pinkcyber-soft/60 hover:text-pinkcyber-bright">
                        <i class="fa-solid fa-upload"></i> Change Photo 2 (Local Preview)
                        <input type="file" accept="image/*" class="hidden" onchange="previewImage(event, 'photo2Display')">
                    </label>
                </div>
            </div>

            <!-- PANEL 2: ls skills/ -->
            <div class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/40 flex flex-col justify-between">
                <div>
                    <!-- Header -->
                    <div class="flex items-center justify-between pb-3 mb-3 border-b border-pink-950 font-mono text-xs">
                        <span class="text-pinkcyber-bright font-semibold"><i class="fa-solid fa-folder-open mr-1"></i> $ ls skills/</span>
                        <span class="text-pinkcyber-soft/60">Categorized</span>
                    </div>

                    <div class="space-y-3 font-mono text-xs">
                        <!-- Languages -->
                        <div>
                            <span class="text-pinkcyber-bright text-[11px] block mb-1.5 font-bold">LANGUAGES:</span>
                            <div class="flex flex-wrap gap-1.5">
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Python</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">C</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">C++</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Go</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Java</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">JavaScript</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">SQL</span>
                            </div>
                        </div>

                        <!-- Security & Crypto -->
                        <div>
                            <span class="text-pinkcyber-bright text-[11px] block mb-1.5 font-bold">SECURITY & CRYPTO:</span>
                            <div class="flex flex-wrap gap-1.5">
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Cryptography (RSA/ElGamal)</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">API Vuln Scanning</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Threat Modeling</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Blockchain Verification</span>
                            </div>
                        </div>

                        <!-- AI & Digital Twins -->
                        <div>
                            <span class="text-pinkcyber-bright text-[11px] block mb-1.5 font-bold">AI SECURITY & DIGITAL TWINS:</span>
                            <div class="flex flex-wrap gap-1.5">
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Ollama (Qwen2.5-Coder)</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">AI Security</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">ThingsBoard & Docker</span>
                                <span class="px-2 py-0.5 bg-pink-950/60 border border-pinkcyber-pink/50 text-pinkcyber-soft rounded">Linux</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- PANEL 3: ls -la leadership_and_roles/ -->
            <div class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/40">
                <div class="flex items-center justify-between pb-3 mb-3 border-b border-pink-950 font-mono text-xs">
                    <span class="text-pinkcyber-bright font-semibold"><i class="fa-solid fa-list-check mr-1"></i> $ ls -la leadership_and_roles/</span>
                    <span class="text-pinkcyber-soft/60">2 Directories</span>
                </div>

                <div class="font-mono text-xs space-y-3">
                    <div class="p-3 bg-black/50 border border-pink-950 rounded-lg hover:border-pinkcyber-pink/60 transition-colors">
                        <div class="flex justify-between items-center text-pinkcyber-bright mb-1">
                            <span class="font-bold">CybeReach Security Club — Student Lead</span>
                            <span class="text-[10px] px-1.5 py-0.5 bg-pinkcyber-pink/20 border border-pinkcyber-pink/40 rounded">Active</span>
                        </div>
                        <p class="text-pinkcyber-soft/80 text-[11px]">
                            Directing technical tracks, school cyber-awareness workshops, and student attendance web solutions.
                        </p>
                    </div>

                    <div class="p-3 bg-black/50 border border-pink-950 rounded-lg hover:border-pinkcyber-pink/60 transition-colors">
                        <div class="flex justify-between items-center text-pinkcyber-bright mb-1">
                            <span class="font-bold">Digital Twin & AI Security Research</span>
                            <span class="text-[10px] px-1.5 py-0.5 bg-pinkcyber-pink/20 border border-pinkcyber-pink/40 rounded">Projects</span>
                        </div>
                        <p class="text-pinkcyber-soft/80 text-[11px]">
                            Configured Docker container pipelines for IoT data (ThingsBoard) and evaluated LLM safety verification metrics.
                        </p>
                    </div>
                </div>
            </div>

            <!-- PANEL 4: ./github-analytics.sh -->
            <div class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/40">
                <div class="flex items-center justify-between pb-3 mb-3 border-b border-pink-950 font-mono text-xs">
                    <span class="text-pinkcyber-bright font-semibold"><i class="fa-solid fa-chart-line mr-1"></i> $ ./github-analytics.sh</span>
                    <span class="text-pinkcyber-soft/60">Live Metrics</span>
                </div>

                <div class="grid grid-cols-3 gap-3 mb-4 font-mono text-center">
                    <div class="bg-black/60 p-2.5 rounded-lg border border-pinkcyber-pink/30">
                        <span class="text-[10px] text-pinkcyber-soft/70 block">COMMITS</span>
                        <span class="text-lg font-bold text-pinkcyber-bright">549+</span>
                    </div>
                    <div class="bg-black/60 p-2.5 rounded-lg border border-pinkcyber-pink/30">
                        <span class="text-[10px] text-pinkcyber-soft/70 block">STREAK</span>
                        <span class="text-lg font-bold text-pinkcyber-bright">45 Days</span>
                    </div>
                    <div class="bg-black/60 p-2.5 rounded-lg border border-pinkcyber-pink/30">
                        <span class="text-[10px] text-pinkcyber-soft/70 block">GRADE</span>
                        <span class="text-lg font-bold text-pinkcyber-bright">A+</span>
                    </div>
                </div>

                <!-- Pink Language Breakdown Bar -->
                <div class="font-mono text-xs space-y-1.5">
                    <div class="flex justify-between text-[11px] text-pinkcyber-soft/80">
                        <span>Language Distribution</span>
                        <span>Python • C/C++ • Go • JS</span>
                    </div>
                    <div class="w-full h-2.5 bg-pink-950/80 rounded-full overflow-hidden flex">
                        <div class="h-full bg-pinkcyber-pink w-[40%]" title="Python 40%"></div>
                        <div class="h-full bg-pinkcyber-bright w-[30%]" title="C/C++ 30%"></div>
                        <div class="h-full bg-pinkcyber-magenta w-[20%]" title="Go 20%"></div>
                        <div class="h-full bg-pink-400 w-[10%]" title="JavaScript 10%"></div>
                    </div>
                </div>
            </div>

        </div>

        <!-- BOTTOM MOVING PROJECTS CAROUSEL (ALL PINK) -->
        <section class="pink-glass-panel rounded-2xl p-5 border border-pinkcyber-pink/50 overflow-hidden relative">
            <div class="flex items-center justify-between mb-4 font-mono text-xs border-b border-pink-950 pb-2">
                <span class="text-pinkcyber-bright font-semibold flex items-center gap-2">
                    <i class="fa-solid fa-spinner animate-spin text-pinkcyber-pink"></i> $ ./run-project-marquee.sh
                </span>
                <span class="text-pinkcyber-soft/70 text-[11px] hidden sm:inline">(Hover to pause marquee)</span>
            </div>

            <!-- Pink Marquee Carousel Container -->
            <div class="relative w-full overflow-hidden">
                <!-- Fade Gradients at Edges -->
                <div class="absolute left-0 top-0 bottom-0 w-12 bg-gradient-to-r from-pinkcyber-bg to-transparent z-10 pointer-events-none"></div>
                <div class="absolute right-0 top-0 bottom-0 w-12 bg-gradient-to-l from-pinkcyber-bg to-transparent z-10 pointer-events-none"></div>

                <div class="animate-pink-marquee flex gap-4">
                    
                    <!-- PROJECT CARD 1 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-brands fa-python text-lg"></i> The Python Toolkit
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Password generators, API vulnerability scanners, and cryptosystem solvers suite.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Python • Security</span>
                            <span class="text-pinkcyber-bright">v1.2</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 2 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-camera text-lg"></i> kannadiga.lens
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Computer vision & cultural text/image recognition analysis framework.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">OpenCV • Python</span>
                            <span class="text-pinkcyber-bright">v1.0</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 3 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-link text-lg"></i> MindForge
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Blockchain document verification with AI security guardrails and integrity hashes.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Blockchain • AI</span>
                            <span class="text-pinkcyber-bright">v2.0</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 4 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-globe text-lg"></i> My Portfolio
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Interactive dark neon pink cyber portfolio dashboard & GitHub showcase.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">HTML • Tailwind</span>
                            <span class="text-pinkcyber-bright">Live</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 5 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-bolt text-lg"></i> Bit-Torrent Client
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Custom peer-to-peer file transfer BitTorrent protocol implementation in Go.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Go • Networking</span>
                            <span class="text-pinkcyber-bright">v1.1</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 6 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-qrcode text-lg"></i> Attendance Tracker
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Dynamic QR code student attendance system engineered for CybeReach Club.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Web • QR Engine</span>
                            <span class="text-pinkcyber-bright">v1.5</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 7 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-building-columns text-lg"></i> Bank Management
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Secure transactional portal and encrypted banking database system.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">C++ • SQL</span>
                            <span class="text-pinkcyber-bright">v1.0</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 8 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-server text-lg"></i> Student Admin API
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                RESTful backend service for academic records, grades, and enrollment.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Node.js • API</span>
                            <span class="text-pinkcyber-bright">v2.1</span>
                        </div>
                    </div>

                    <!-- PROJECT CARD 9 -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-cart-shopping text-lg"></i> Smart Procurement
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Automated vendor tracking and procurement management ecosystem.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <a href="https://github.com/just-deva/Smart-Procurement-and-Vendor-Management-System" target="_blank" class="px-2 py-0.5 bg-pinkcyber-pink text-black font-bold rounded hover:bg-pinkcyber-bright">
                                GitHub Repo <i class="fa-solid fa-external-link ml-1"></i>
                            </a>
                            <span class="text-pinkcyber-bright">v1.0</span>
                        </div>
                    </div>

                    <!-- DUPLICATE MARQUEE ITEMS FOR SEAMLESS INFINITE LOOP -->
                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-brands fa-python text-lg"></i> The Python Toolkit
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Password generators, API vulnerability scanners, and cryptosystem solvers suite.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">Python • Security</span>
                            <span class="text-pinkcyber-bright">v1.2</span>
                        </div>
                    </div>

                    <div class="w-72 bg-black/70 border border-pinkcyber-pink/40 rounded-xl p-4 shrink-0 hover:border-pinkcyber-bright transition-all flex flex-col justify-between">
                        <div>
                            <div class="flex items-center gap-2 text-pinkcyber-bright font-mono text-sm font-bold mb-1">
                                <i class="fa-solid fa-camera text-lg"></i> kannadiga.lens
                            </div>
                            <p class="font-mono text-xs text-pinkcyber-soft mb-3 line-clamp-2">
                                Computer vision & cultural text/image recognition analysis framework.
                            </p>
                        </div>
                        <div class="flex items-center justify-between font-mono text-[10px]">
                            <span class="px-2 py-0.5 bg-pinkcyber-pink/20 text-pinkcyber-bright rounded">OpenCV • Python</span>
                            <span class="text-pinkcyber-bright">v1.0</span>
                        </div>
                    </div>

                </div>
            </div>
        </section>

        <!-- FOOTER -->
        <footer class="text-center font-mono text-xs text-pinkcyber-soft/60 py-4 border-t border-pink-950">
            Built for <a href="https://github.com/just-deva" target="_blank" class="text-pinkcyber-bright hover:underline">@just-deva</a>
        </footer>

    </div>

    <!-- EXPORT MARKDOWN MODAL -->
    <div id="exportModal" class="fixed inset-0 bg-black/85 backdrop-blur-md z-50 hidden flex items-center justify-center p-4">
        <div class="pink-glass-panel w-full max-w-3xl rounded-2xl p-6 border border-pinkcyber-pink max-h-[85vh] flex flex-col justify-between">
            <div>
                <div class="flex items-center justify-between pb-3 mb-4 border-b border-pink-950">
                    <h3 class="font-mono text-sm font-bold text-pinkcyber-bright flex items-center gap-2">
                        <i class="fa-solid fa-file-export"></i> Generated GitHub README.md Code (Pure Pink)
                    </h3>
                    <button onclick="closeExportModal()" class="text-pinkcyber-soft hover:text-white font-mono text-lg">&times;</button>
                </div>
                
                <p class="font-mono text-xs text-pinkcyber-soft mb-3">
                    Copy and paste this clean code directly into your GitHub repository (`just-deva/README.md`):
                </p>

                <textarea id="markdownCodeArea" readonly class="w-full h-80 bg-black/95 border border-pinkcyber-pink/40 rounded-xl p-3 font-mono text-xs text-pinkcyber-bright focus:outline-none resize-none"></textarea>
            </div>

            <div class="flex justify-end gap-3 mt-4 pt-3 border-t border-pink-950">
                <button onclick="closeExportModal()" class="px-4 py-2 text-xs font-mono bg-pink-950/60 text-pinkcyber-soft rounded-lg hover:bg-pink-900">Close</button>
                <button onclick="copyMarkdownCode()" class="px-5 py-2 text-xs font-mono font-bold bg-pinkcyber-pink text-black rounded-lg hover:bg-pinkcyber-bright flex items-center gap-2 shadow-[0_0_15px_rgba(255,20,147,0.5)]">
                    <i class="fa-solid fa-copy"></i> Copy Markdown Code
                </button>
            </div>
        </div>
    </div>

    <!-- TOAST NOTIFICATION -->
    <div id="toast" class="fixed bottom-6 right-6 z-50 bg-pinkcyber-pink text-black font-mono text-xs font-bold px-4 py-3 rounded-xl shadow-[0_0_20px_rgba(255,20,147,0.7)] transform translate-y-20 opacity-0 transition-all duration-300 flex items-center gap-2">
        <i class="fa-solid fa-circle-check text-sm"></i> <span id="toastMsg">Code copied to clipboard!</span>
    </div>

    <!-- JAVASCRIPT LOGIC -->
    <script>
        // Auto-Typewriter Logic for Header Banner
        const typingLines = [
            "Hi 👋 I'm Devadarshini S",
            "Cybersecurity @ Amrita",
            "AI Security & Crypto Researcher",
            "Lead @ CybeReach Club"
        ];
        
        let lineIdx = 0;
        let charIdx = 0;
        let isDeleting = false;
        const typingSpeed = 90;
        const deleteSpeed = 40;
        const pauseDelay = 1500;

        function typeLoop() {
            const currentLine = typingLines[lineIdx];
            const outputEl = document.getElementById('typingOutput');

            if (isDeleting) {
                outputEl.textContent = currentLine.substring(0, charIdx - 1);
                charIdx--;
            } else {
                outputEl.textContent = currentLine.substring(0, charIdx + 1);
                charIdx++;
            }

            if (!isDeleting && charIdx === currentLine.length) {
                isDeleting = true;
                setTimeout(typeLoop, pauseDelay);
            } else if (isDeleting && charIdx === 0) {
                isDeleting = false;
                lineIdx = (lineIdx + 1) % typingLines.length;
                setTimeout(typeLoop, 300);
            } else {
                setTimeout(typeLoop, isDeleting ? deleteSpeed : typingSpeed);
            }
        }

        document.addEventListener('DOMContentLoaded', () => {
            typeLoop();
            generateMarkdownTemplate();
        });

        // Scanline Layer Toggle
        function toggleScanlines() {
            const scanlineLayer = document.getElementById('scanlineLayer');
            const statusEl = document.getElementById('scanlineStatus');
            if (scanlineLayer.classList.contains('hidden')) {
                scanlineLayer.classList.remove('hidden');
                statusEl.textContent = 'ON';
            } else {
                scanlineLayer.classList.add('hidden');
                statusEl.textContent = 'OFF';
            }
        }

        // Local Image Preview Switcher
        function previewImage(event, targetId) {
            const reader = new FileReader();
            reader.onload = function() {
                const output = document.getElementById(targetId);
                output.src = reader.result;
                showToast('Image updated successfully!');
            };
            if(event.target.files[0]) {
                reader.readAsDataURL(event.target.files[0]);
            }
        }

        // Generate Pure Pink Clean Markdown for Export
        function generateMarkdownTemplate() {
            const mdCode = `<div align="center">

<!-- ========================================== -->
<!-- 1. RETRO PINK CRT TV & HEADER SECTION      -->
<!-- ========================================== -->
<table width="100%" style="background-color: #1a030d; border: 2px solid #ff1493; border-radius: 12px;">
  <tr>
    <td width="38%" align="center" style="vertical-align: middle; padding: 15px; border-right: 1px dashed #ff1493;">
      <img src="./photo1.jpg" width="140" style="border-radius: 10px; border: 3px solid #ff1493; box-shadow: 0 0 15px #ff1493;" alt="Devadarshini S - photo1.jpg" />
      <p style="color: #ff66cc; font-family: monospace; font-size: 13px; margin-top: 10px; margin-bottom: 0;"><b>@just-deva</b></p>
    </td>
    <td width="62%" style="padding: 20px; vertical-align: top;">
      <pre style="color: #ff1493; font-family: monospace; font-size: 12px; margin: 0;">🔴 🟡 🟢 devadarshini@cyber-terminal: ~</pre>
      <hr style="border: 0.5px solid #ff1493; margin: 10px 0;" />
      <a href="https://git.io/typing-svg">
        <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=20&pause=1000&color=FF1493&width=450&height=40&lines=Hi+%F0%9F%91%8B+I'm+Devadarshini+S;Cybersecurity+%40+Amrita;AI+Security+%26+Crypto+Researcher;Lead+%40+CybeReach+Club" alt="Typing Banner" />
      </a>
      <p style="color: #ffb3da; font-family: monospace; font-size: 13px; line-height: 1.6; margin-top: 10px;">
        📍 <b style="color: #ff66cc;">Location:</b> Coimbatore, Tamil Nadu, India<br/>
        🎓 <b style="color: #ff66cc;">Education:</b> B.Tech CS (Cybersecurity) @ Amrita Vishwa Vidyapeetham<br/>
        🛡️ <b style="color: #ff66cc;">Focus Areas:</b> Cryptography • AI Security • Digital Twins • Systems Engineering • Programming
      </p>
    </td>
  </tr>
</table>

<br/>

<!-- ========================================== -->
<!-- 2. PINK BADGES & PLATFORMS                 -->
<!-- ========================================== -->
<p align="center">
  <a href="https://linkedin.com/in/your-linkedin-profile" target="_blank"><img src="https://img.shields.io/badge/LinkedIn-FF1493?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" /></a>
  <a href="https://leetcode.com/your-leetcode-profile" target="_blank"><img src="https://img.shields.io/badge/LeetCode-FF1493?style=for-the-badge&logo=leetcode&logoColor=white" alt="LeetCode" /></a>
  <a href="https://hackerrank.com/your-hackerrank-profile" target="_blank"><img src="https://img.shields.io/badge/HackerRank-FF1493?style=for-the-badge&logo=hackerrank&logoColor=white" alt="HackerRank" /></a>
  <a href="https://tryhackme.com/p/your-tryhackme-profile" target="_blank"><img src="https://img.shields.io/badge/TryHackMe-FF1493?style=for-the-badge&logo=tryhackme&logoColor=white" alt="TryHackMe" /></a>
  <a href="mailto:devadarshini@example.com"><img src="https://img.shields.io/badge/Email-FF66CC?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" /></a>
</p>

</div>

<br/>

<!-- ========================================== -->
<!-- 3. ABOUT ME WITH PHOTO 2 ENCLOSED IN TV    -->
<!-- ========================================== -->
<table width="100%">
  <tr>
    <td bgcolor="#1a030d" style="border: 1px solid #ff1493; border-radius: 8px; padding: 15px;">
      <pre style="color: #ff1493; font-family: monospace; margin: 0;">🔴 🟡 🟢 $ cat about_me.md</pre>
      <hr style="border: 0.5px solid #ff1493; margin: 10px 0;" />
      <table width="100%">
        <tr>
          <td style="vertical-align: top; padding-right: 15px;">
            <p style="color: #ffb3da; font-family: monospace; line-height: 1.6; margin: 0;">
              Cybersecurity undergraduate passionate about building resilient systems, low-level tooling, cryptographic algorithms, AI security, and programming.<br/><br/>
              • <b style="color: #ff66cc;">Student Lead</b> at <i>CybeReach Club</i> leading technical workshops, security outreach, and internal application development.<br/>
              • <b style="color: #ff66cc;">Researcher</b> exploring <i>Digital Twin platforms</i> (AWS, Azure, ThingsBoard) and offline local LLM toolchains using Ollama.<br/>
              • <b style="color: #ff66cc;">Open Source Builder</b> developing cybersecurity utility toolkits, networking engines, and full-stack enterprise portals.
            </p>
          </td>
          <td width="150" align="center" style="vertical-align: top;">
            <table style="background-color: #0d0107; border: 2px solid #ff66cc; border-radius: 10px; padding: 6px;">
              <tr>
                <td align="center">
                  <img src="./photo2.jpg" width="120" style="border-radius: 6px; border: 2px solid #ff1493;" alt="Devadarshini S - photo2.jpg" />
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

<br/>

<!-- ========================================== -->
<!-- 4. MOVING PROJECT MARQUEE                  -->
<!-- ========================================== -->
<table width="100%">
  <tr>
    <td bgcolor="#1a030d" style="border: 1px solid #ff1493; border-radius: 8px; padding: 15px;">
      <pre style="color: #ff1493; font-family: monospace; margin: 0;">🔴 🟡 🟢 $ ./run-project-marquee.sh</pre>
      <hr style="border: 0.5px solid #ff1493; margin: 10px 0;" />
      <marquee behavior="scroll" direction="left" scrollamount="6" style="color: #ff66cc; font-family: monospace; font-size: 14px;">
        🐍 <b>The Python Toolkit</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🔍 <b>kannadiga.lens</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🔗 <b>MindForge Document Verification</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🌐 <b>My Portfolio</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        ⚡ <b>Bit-torrent Client</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🎯 <b>Attendance Tracker</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🏦 <b>Bank Management System</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        ⚙️ <b>Student Management API</b> &nbsp;&nbsp;•&nbsp;&nbsp; 
        🛒 <b>Smart Procurement and Vendor Management System</b>
      </marquee>
    </td>
  </tr>
</table>

<br/>

<!-- ========================================== -->
<!-- 5. ALL-PINK GITHUB ANALYTICS              -->
<!-- ========================================== -->
<div align="center">
  <img height="165" src="https://github-readme-stats.vercel.app/api?username=just-deva&show_icons=true&theme=dark&bg_color=1A030D&title_color=FF1493&icon_color=FF66CC&text_color=FFB3DA&border_color=FF1493&hide_border=false" />
  <img height="165" src="https://github-readme-streak-stats.herokuapp.com/?user=just-deva&theme=dark&background=1A030D&stroke=FF1493&alarm=FF1493&fire=FF1493&ring=FF1493&hard=FF1493&currStreakLabel=FF66CC&border=FF1493" />
</div>`;

            document.getElementById('markdownCodeArea').value = mdCode;
        }

        // Modal Controls
        function openExportModal() {
            document.getElementById('exportModal').classList.remove('hidden');
        }

        function closeExportModal() {
            document.getElementById('exportModal').classList.add('hidden');
        }

        // Toast Helper
        function showToast(msg) {
            const toast = document.getElementById('toast');
            document.getElementById('toastMsg').textContent = msg;
            toast.classList.remove('translate-y-20', 'opacity-0');
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 3000);
        }

        function copyMarkdownCode() {
            const codeArea = document.getElementById('markdownCodeArea');
            codeArea.select();
            document.execCommand('copy');
            showToast('README Markdown code copied to clipboard!');
        }
    </script>
</body>
</html>