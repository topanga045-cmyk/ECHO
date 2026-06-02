i**ndex.html**  
  
<!DOCTYPE html>  
  
<html class="dark" lang="en"><head>  
<meta charset="utf-8"/>  
<meta content="width=device-width, initial-scale=1.0" name="viewport"/>  
<title>PROJECT ECHO | SECURE_TERMINAL</title>  
<script src="https://cdn.tailwindcss.com?plugins=forms,container-queries"></script>  
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;700&amp;family=Space+Mono:wght@400;700&amp;display=swap" rel="stylesheet"/>  
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet"/>  
<link href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:wght,FILL@100..700,0..1&amp;display=swap" rel="stylesheet"/>  
<script id="tailwind-config">  
        tailwind.config = {  
          darkMode: "class",  
          theme: {  
            extend: {  
              "colors": {  
                "on-secondary-fixed": "#002200",  
                "on-primary": "#013a00",  
                "on-background": "#e2e2e2",  
                "on-tertiary-fixed": "#0a2007",  
                "error-container": "#93000a",  
                "on-secondary-fixed-variant": "#13520d",  
                "error": "#ffb4ab",  
                "secondary": "#94d782",  
                "on-surface-variant": "#b9ccaf",  
                "surface-container-lowest": "#0e0e0e",  
                "surface-container": "#1f1f1f",  
                "tertiary-fixed": "#ceebc1",  
                "on-error": "#690005",  
                "surface-tint": "#02e600",  
                "on-tertiary-container": "#4e6746",  
                "inverse-on-surface": "#303030",  
                "tertiary-fixed-dim": "#b2cfa6",  
                "surface-container-low": "#1b1b1b",  
                "on-primary-container": "#027100",  
                "on-error-container": "#ffdad6",  
                "background": "#000000",  
                "primary": "#eaffde",  
                "on-primary-fixed": "#002200",  
                "outline": "#84967c",  
                "inverse-surface": "#e2e2e2",  
                "inverse-primary": "#026e00",  
                "primary-fixed-dim": "#02e600",  
                "on-surface": "#e2e2e2",  
                "primary-fixed": "#77ff61",  
                "on-tertiary-fixed-variant": "#354d2e",  
                "secondary-fixed-dim": "#94d782",  
                "surface": "#001100",  
                "tertiary-container": "#c7e4bb",  
                "primary-container": "#00ff00",  
                "tertiary": "#e9ffdd",  
                "on-tertiary": "#1f361a",  
                "surface-bright": "#393939",  
                "surface-dim": "#131313",  
                "surface-container-high": "#2a2a2a",  
                "on-primary-fixed-variant": "#015300",  
                "secondary-fixed": "#aff49c",  
                "surface-variant": "#353535",  
                "outline-variant": "#3b4b35",  
                "surface-container-highest": "#353535",  
                "secondary-container": "#16550f",  
                "on-secondary-container": "#87c976",  
                "on-secondary": "#003a00"  
              },  
              "spacing": {  
                "md": "16px", "xl": "48px", "sm": "8px", "gutter": "16px", "unit": "4px", "lg": "24px", "xs": "4px", "container-max": "1200px"  
              },  
              "fontFamily": {  
                "body-md": ["JetBrains Mono"], "label-sm": ["JetBrains Mono"], "display": ["Space Mono"], "headline-md": ["Space Mono"], "headline-lg": ["Space Mono"], "body-lg": ["JetBrains Mono"], "headline-lg-mobile": ["Space Mono"]  
              }  
            }  
          }  
        }  
    </script>  
<style>  
        body { background-color: #000000; overflow-x: hidden; }  
        .matrix-canvas { position: fixed; top: 0; left: 0; z-index: -1; opacity: 0.2; }  
        .scanlines {  
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;  
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));  
            background-size: 100% 2px, 3px 100%; pointer-events: none; z-index: 100;  
        }  
        .neon-glow { box-shadow: 0 0 15px rgba(2, 230, 0, 0.3); }  
        .neon-text { text-shadow: 0 0 8px rgba(2, 230, 0, 0.8); }  
        .terminal-cursor::after { content: "_"; animation: blink 1s infinite; }  
        @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0; } }  
        .glitch-hover:hover { animation: glitch 0.3s cubic-bezier(.25,.46,.45,.94) both infinite; }  
        @keyframes glitch { 0% { transform: translate(0); } 20% { transform: translate(-2px, 2px); } 40% { transform: translate(-2px, -2px); } 60% { transform: translate(2px, 2px); } 80% { transform: translate(2px, -2px); } 100% { transform: translate(0); } }  
    </style>  
</head>  
<body class="font-body-md text-on-surface selection:bg-primary-container selection:text-on-primary-container">  
<canvas class="matrix-canvas" id="matrix"></canvas>  
<div class="scanlines"></div>  
<!-- Top Navigation Shell -->  
<header class="fixed top-0 left-0 w-full z-50 flex justify-between items-center px-gutter py-sm bg-background border-b border-outline-variant shadow-[0_0_15px_rgba(2,230,0,0.3)]">  
<div class="font-display text-headline-md text-primary tracking-tighter neon-text">  
            SECURE_TERMINAL_V.8.2  
        </div>  
<div class="flex gap-md">  
<span class="material-symbols-outlined text-primary" data-icon="terminal">terminal</span>  
<span class="material-symbols-outlined text-primary" data-icon="security" style="font-variation-settings: 'FILL' 1;">security</span>  
<span class="material-symbols-outlined text-primary" data-icon="settings">settings</span>  
</div>  
</header>  
<!-- Sidebar Shell -->  
<aside class="fixed left-0 top-0 h-full z-40 flex flex-col pt-20 bg-surface border-r border-outline-variant shadow-[5px_0_15px_rgba(0,255,0,0.1)] w-64 hidden md:flex">  
<div class="px-md py-lg border-b border-outline-variant mb-md">  
<div class="font-display text-headline-md text-primary mb-xs">OPERATOR_01</div>  
<div class="text-label-sm text-outline uppercase tracking-widest">STATUS: INFILTRATING</div>  
</div>  
<nav class="flex-grow">  
<div class="text-on-primary-container bg-primary-container border-l-4 border-primary px-4 py-2 flex items-center gap-sm mb-unit cursor-default">  
<span class="material-symbols-outlined" data-icon="assignment">assignment</span>  
<span>MISSION_LOGS</span>  
</div>  
<div class="text-outline hover:text-primary-fixed-dim px-4 py-2 flex items-center gap-sm transition-all hover:bg-surface-variant cursor-pointer">  
<span class="material-symbols-outlined" data-icon="lock_open">lock_open</span>  
<span>DECRYPTOR</span>  
</div>  
<div class="text-outline hover:text-primary-fixed-dim px-4 py-2 flex items-center gap-sm transition-all hover:bg-surface-variant cursor-pointer">  
<span class="material-symbols-outlined" data-icon="leak_add">leak_add</span>  
<span>COMM_LINK</span>  
</div>  
<div class="text-outline hover:text-primary-fixed-dim px-4 py-2 flex items-center gap-sm transition-all hover:bg-surface-variant cursor-pointer">  
<span class="material-symbols-outlined" data-icon="hub">hub</span>  
<span>NETWORK_MAP</span>  
</div>  
</nav>  
<div class="p-md">  
<button class="w-full border border-primary py-sm text-primary-fixed-dim hover:bg-primary-container hover:text-on-primary-container transition-all uppercase font-bold text-label-sm">  
                &gt; ACCESS_CORE  
            </button>  
</div>  
</aside>  
<!-- Main Content Canvas -->  
<main class="pt-24 pb-20 px-4 md:pl-72 md:pr-8 min-h-screen flex flex-col items-center justify-center relative">  
<!-- Progress Bar Container -->  
<div class="w-full max-w-2xl mb-xl hidden" id="progress-container">  
<div class="flex justify-between text-label-sm text-primary mb-xs font-bold neon-text">  
<span>DECRYPTION_PROGRESS</span>  
<span id="progress-text">1/5</span>  
</div>  
<div class="w-full h-2 bg-surface border border-outline-variant overflow-hidden">  
<div class="h-full bg-primary-container transition-all duration-500 shadow-[0_0_10px_#00ff00]" id="progress-bar" style="width: 20%;"></div>  
</div>  
</div>  
<div class="w-full max-w-2xl" id="game-canvas">  
<!-- Screen 1: Intro -->  
<section class="text-center space-y-lg animate-pulse" id="screen-intro">  
<h1 class="font-display text-display md:text-[64px] text-primary-fixed-dim neon-text uppercase tracking-widest leading-none">PROJECT ECHO</h1>  
<p class="font-body-lg text-primary text-headline-md terminal-cursor">"คุณถูกเลือกให้เข้าร่วมการทดสอบ"</p>  
<div class="pt-xl">  
<button class="group relative px-xl py-md border-2 border-primary-fixed-dim text-primary bg-transparent hover:bg-primary-container hover:text-on-primary-container transition-all duration-300 neon-glow glitch-hover uppercase font-bold tracking-[0.2em] text-headline-md" onclick="gameState.startMission()">  
                        START MISSION  
                        <span class="absolute -top-2 -left-2 w-4 h-4 border-t-2 border-l-2 border-primary"></span>  
<span class="absolute -bottom-2 -right-2 w-4 h-4 border-b-2 border-r-2 border-primary"></span>  
</button>  
</div>  
</section>  
<!-- Screen 2: Puzzle -->  
<section class="hidden space-y-lg" id="screen-puzzle">  
<div class="bg-surface border border-primary-fixed-dim p-lg relative overflow-hidden">  
<div class="absolute top-0 right-0 p-xs text-[10px] text-outline opacity-50 uppercase">ID: 0x9331-ECHO</div>  
<div class="mb-lg border-b border-outline-variant pb-md" id="puzzle-header">  
<h2 class="text-label-sm text-outline mb-xs uppercase tracking-widest" id="puzzle-hint">HINT: INITIALIZING...</h2>  
<div class="text-headline-lg text-primary-fixed-dim font-display neon-text" id="puzzle-question">...</div>  
</div>  
<div class="space-y-md">  
<div class="relative">  
<input autocomplete="off" class="w-full bg-black border border-outline text-primary-fixed-dim p-md focus:ring-0 focus:border-primary-fixed-dim outline-none transition-all uppercase placeholder:opacity-30" id="puzzle-input" placeholder="INPUT_COMMAND" type="text"/>  
<div class="absolute right-4   
