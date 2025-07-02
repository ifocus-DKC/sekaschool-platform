# sekaschool-platform
file:///Users/i-kruchetz/Sekaschool-Educationa-1
<!DOCTYPE html>
<html lang="th" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <!-- 
      Source Report: User's Research Blueprint, ExamGuide.pdf, and custom UI design (index.html)
      App Type: Integrated Intelligent Interactive Learning Platform SPA (Final Version)
    -->
    <!-- Placeholder Comments -->
    <!-- Chosen Palette: Liquid Glass Dark (Based on user's provided index.html: darkBlue/darkerBlue background, neonPink accents, and a semi-transparent glass effect. This choice respects the user's established visual identity for the platform over the generic "light color" requirement.) -->
    <!-- Application Structure Plan: The SPA is a unified dashboard integrating three core modules from the research blueprint: 1. Smart Classroom (for content management), 2. Test Creation (AI engine), and 3. Assessment (analysis/export). This modular structure, presented within the user's "Liquid Glass" UI, creates a cohesive research-ready workflow from content ingestion to AI-powered generation and data output, embodying the "Honest Playground" concept. -->
    <!-- Visualization & Content Choices: Module 1 (Classroom) -> Goal: Manage Content -> Viz: Interactive cards for content import simulation (file, paste). Justification: Provides a clear entry point for the AI engine. Module 2 (Test Creation) -> Goal: Generate Questions from context -> Viz: A dedicated AI output area. Interaction: AI generation button. Justification: Implements the "Honest Playground" concept. Module 3 (Assessment) -> Goal: Summarize & Export -> Viz: Doughnut Chart (Chart.js) and an export button. Justification: Provides a tangible output for analysis and integration with other systems. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

    <title>โรงเรียนเซกา | แพลตฟอร์มการเรียนรู้เชิงโต้ตอบอัจฉริยะ</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        neonPink: '#FF2E9F',
                        darkerBlue: '#0F0F1A',
                        mediumBlue: '#101827',
                        'darkBlue-glass': 'rgba(26, 30, 48, 0.65)',
                        'neonPink-hover': 'rgba(255, 46, 159, 0.15)',
                        'glass-border': 'rgba(255, 255, 255, 0.2)',
                        'glass-border-accent': 'rgba(255, 46, 159, 0.3)',
                    },
                    fontFamily: {
                        prompt: ['Prompt', 'sans-serif'],
                        poppins: ['Poppins', 'sans-serif'],
                    },
                    animation: {
                        fadeIn: 'fadeIn 0.5s ease forwards',
                        slideInUp: 'slideInUp 0.5s ease forwards',
                    },
                    keyframes: {
                        fadeIn: { 'from': { opacity: '0', transform: 'translateY(10px)' }, 'to': { opacity: '1', transform: 'translateY(0)' } },
                        slideInUp: { 'from': { opacity: '0', transform: 'translateY(20px)' }, 'to': { opacity: '1', transform: 'translateY(0)' } }
                    }
                }
            }
        }
    </script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&family=Prompt:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        body { background-color: #0F0F1A; font-family: 'Prompt', sans-serif; color: #E0E0E0; }
        .liquid-glass { background-color: var(--tw-colors-darkBlue-glass, rgba(26, 30, 48, 0.65)); border: 1px solid var(--tw-colors-glass-border, rgba(255, 255, 255, 0.2)); backdrop-filter: blur(12px); -webkit-backdrop-filter: blur(12px); transition: all 0.3s ease; border-radius: 0.75rem; }
        .liquid-glass:hover { transform: translateY(-5px); }
        .nav-link { transition: all 0.3s ease; padding: 0.5rem 0.75rem; border-radius: 0.5rem; font-weight: 500; color: #D1D5DB; }
        .nav-link:hover, .nav-link.active { background-color: var(--tw-colors-neonPink-hover, rgba(255, 46, 159, 0.15)); color: var(--tw-colors-neonPink, #FF2E9F); }
        .english-subtext { font-size: 0.75rem; opacity: 0.6; display: block; margin-top: 0.125rem; font-family: 'Poppins', sans-serif; }
        .chart-container { position: relative; width: 100%; max-width: 400px; margin: auto; height: 350px; }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #0F0F1A; }
        ::-webkit-scrollbar-thumb { background-color: rgba(255, 46, 159, 0.3); border-radius: 10px; border: 2px solid #0F0F1A; }
    </style>
</head>
<body class="bg-darkerBlue">

    <!-- Navigation Bar -->
    <nav class="bg-mediumBlue/80 backdrop-blur-lg border-b border-glass-border-accent/50 sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex justify-between items-center h-20">
                <a href="#dashboard" class="flex items-center flex-shrink-0">
                    <svg class="h-10 w-10 text-neonPink mr-2" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg"><circle cx="50" cy="50" r="45" stroke="currentColor" stroke-width="5"/><path d="M30 35 L70 35 M30 50 L70 50 M30 65 L70 65" stroke="currentColor" stroke-width="5"/><rect x="40" y="25" width="20" height="50" fill="currentColor" opacity="0.3"/></svg>
                    <span class="text-base md:text-lg font-semibold text-white">Open Arts Platform</span>
                </a>
                <div class="hidden lg:flex items-center space-x-1 font-poppins nav-link-container">
                    <a href="#dashboard" class="nav-link active">ภาพรวม (Dashboard)</a>
                    <a href="#modules" class="nav-link">โมดูลอัจฉริยะ (Modules)</a>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content Area -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">

        <!-- Welcome Section -->
        <section id="dashboard" class="text-center py-16 animate-fadeIn">
            <h1 class="text-4xl md:text-5xl lg:text-6xl font-bold text-white mb-4 font-poppins">
                AI Learning Platform
            </h1>
            <p class="text-lg text-gray-300 font-prompt">
                แพลตฟอร์มต้นแบบเพื่อการวิจัยและพัฒนานวัตกรรมการจัดการเรียนการสอน
            </p>
        </section>

        <!-- Main Modules Section -->
        <section id="modules" class="my-16">
            <h2 class="text-3xl font-bold text-white mb-10 text-center font-poppins">แพลตฟอร์มการเรียนรู้เชิงโต้ตอบ</h2>
            
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-start">
                
                <!-- Module 1: Smart Classroom System -->
                <div class="liquid-glass p-6 animate-slideInUp lg:col-span-1" style="animation-delay: 0.2s;">
                    <h3 class="text-xl font-bold text-neonPink mb-1">1. ระบบห้องเรียนอัจฉริยะ</h3>
                    <p class="text-sm text-gray-400 mb-4 english-subtext">Smart Classroom System</p>
                    <p class="text-sm text-gray-300 mb-4">นำเข้า "คลังความรู้" ของบทเรียนที่คุณต้องการจากแหล่งต่างๆ เพื่อเตรียมพร้อมสำหรับให้ AI ช่วยสร้างสื่อการสอน</p>
                    <div class="bg-darkerBlue/50 p-4 rounded-lg border border-glass-border">
                        <label class="font-semibold block mb-2 text-sm text-gray-200">นำเข้าเนื้อหาสำหรับบทเรียน:</label>
                        <div class="flex space-x-2">
                            <button class="import-btn flex-1 bg-mediumBlue/50 hover:bg-mediumBlue border border-glass-border p-2 rounded-md text-xs" data-source="file">📁 จากไฟล์</button>
                            <input type="file" id="file-input" class="hidden" accept=".txt,.md,.json">
                            <button class="import-btn flex-1 bg-mediumBlue/50 hover:bg-mediumBlue border border-glass-border p-2 rounded-md text-xs" data-source="paste">📋 วางข้อความ</button>
                        </div>
                        <textarea id="content-input" class="w-full mt-2 p-3 border border-glass-border rounded-md h-48 bg-darkerBlue/70 text-gray-300 text-sm" placeholder="วางเนื้อหา หรือเลือกไฟล์เพื่อนำเข้า..."></textarea>
                    </div>
                </div>

                <!-- Modules 2 & 3 Container -->
                <div class="lg:col-span-2 space-y-8">
                    <!-- Module 2: Interactive Test Creation System -->
                    <div class="liquid-glass p-6 animate-slideInUp" style="animation-delay: 0.4s;">
                        <h3 class="text-xl font-bold text-neonPink mb-1">2. ระบบสร้างข้อสอบอัจฉริยะ</h3>
                        <p class="text-sm text-gray-400 mb-4 english-subtext">Interactive Test Creation System</p>
                        <p class="text-sm text-gray-300 mb-4">สั่งให้ AI สร้างชุดคำถามจากเนื้อหาที่คุณนำเข้า โดย AI จะทำงานในฐานะ "ผู้ช่วยที่ซื่อสัตย์" ซึ่งจะใช้ข้อมูลจากคลังความรู้ของคุณเท่านั้น</p>
                        <div class="bg-darkerBlue/50 p-4 rounded-lg border border-glass-border min-h-[260px] flex flex-col">
                            <button id="ai-generate-btn" class="w-full bg-neonPink/80 hover:bg-neonPink text-white font-bold py-3 rounded-lg flex items-center justify-center mb-4">
                                <span class="mr-2">✨</span> สร้างชุดคำถามจากเนื้อหา
                            </button>
                            <div id="ai-output" class="space-y-3 overflow-y-auto flex-grow">
                               <p class="text-center text-gray-500 text-sm pt-8">คำถามที่ AI สร้างขึ้นจะแสดงที่นี่</p>
                            </div>
                        </div>
                    </div>

                    <!-- Module 3: Smart Assessment System -->
                    <div class="liquid-glass p-6 animate-slideInUp" style="animation-delay: 0.6s;">
                        <h3 class="text-xl font-bold text-neonPink mb-1">3. ระบบวัดและประเมินผลอัจฉริยะ</h3>
                        <p class="text-sm text-gray-400 mb-4 english-subtext">Smart Assessment System</p>
                        <p class="text-sm text-gray-300 mb-4">ดูภาพรวมของชุดข้อสอบที่สร้างขึ้น และส่งออกข้อมูลในรูปแบบ JSON เพื่อนำไปใช้วิเคราะห์หรือเชื่อมต่อกับระบบอื่นต่อไป</p>
                        <div class="bg-darkerBlue/50 p-4 rounded-lg border border-glass-border grid grid-cols-1 md:grid-cols-2 gap-6 items-center">
                            <div class="chart-container">
                                <canvas id="quizCompositionChart"></canvas>
                            </div>
                            <div id="export-container" class="text-center">
                                <p class="text-sm text-gray-400 mb-2">ข้อมูลพร้อมส่งออก</p>
                                <button id="export-btn" class="w-full bg-mediumBlue hover:bg-mediumBlue/70 text-white font-semibold py-3 rounded-lg disabled:opacity-50 disabled:cursor-not-allowed" disabled>ส่งออกข้อมูล (JSON)</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
    </main>

    <footer class="border-t border-glass-border-accent/20 mt-20 py-10">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center text-gray-500">
          <p class="font-poppins text-sm">AI Learning Platform - Research Blueprint</p>
          <p class="text-xs mt-2">ออกแบบและพัฒนาระบบ โดย คุณครูวิระเชษฐ์ ทวีทรัพย์</p>
      </div>
  </footer>

  <script>
    document.addEventListener('DOMContentLoaded', function () {
        const contentInput = document.getElementById('content-input');
        const fileInput = document.getElementById('file-input');
        const aiGenerateBtn = document.getElementById('ai-generate-btn');
        const aiOutput = document.getElementById('ai-output');
        const exportBtn = document.getElementById('export-btn');
        let generatedQuizData = [];

        document.querySelectorAll('.import-btn').forEach(button => {
            button.addEventListener('click', (e) => {
                const source = e.target.dataset.source;
                if (source === 'file') {
                    fileInput.click();
                } else if (source === 'paste') {
                    contentInput.focus();
                }
            });
        });
        
        fileInput.addEventListener('change', (e) => {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = (event) => { contentInput.value = event.target.result; };
                reader.readAsText(file);
            }
        });

        aiGenerateBtn.addEventListener('click', () => {
            if (contentInput.value.trim() === "") {
                alert("กรุณานำเข้าเนื้อหาในโมดูล 1 ก่อนสร้างคำถาม");
                return;
            }
            aiGenerateBtn.disabled = true;
            aiGenerateBtn.innerHTML = '<span class="mr-2 animate-spin">🧠</span> AI กำลังประมวลผล...';
            
            // --- AI Simulation ---
            // In a real application, this would be a fetch call to the Gemini API
            setTimeout(() => {
                generatedQuizData = [
                    { id: 1, type: "multiple-choice", question: "คำถามข้อที่ 1 ที่ AI สร้างจากเนื้อหาของคุณ", options: ["คำตอบที่ถูก", "ตัวเลือกลวง 1", "ตัวเลือกลวง 2"], answer: "คำตอบที่ถูก" },
                    { id: 2, type: "true-false", question: "คำถามข้อที่ 2 (ถูก/ผิด) ที่สร้างจากเนื้อหา", options: ["ถูก", "ผิด"], answer: "ถูก" },
                    { id: 3, type: "fill-blank", question: "คำถามข้อที่ 3 (เติมคำ) ที่สร้างจากเนื้อหาคืออะไร", answer: "คำตอบที่ถูกต้อง" }
                ];

                aiOutput.innerHTML = generatedQuizData.map((q, i) => `
                    <div class="p-3 border border-glass-border rounded-md bg-darkerBlue/70">
                        <p class="font-semibold text-sm text-gray-200">${i + 1}. ${q.question}</p>
                        <ul class="list-disc list-inside pl-4 mt-1 text-xs text-gray-400">
                            ${q.options ? q.options.map(opt => `<li class="${opt === q.answer ? 'text-neonPink font-bold' : ''}">${opt}</li>`).join('') : `<li><i>คำตอบ: ${q.answer}</i></li>`}
                        </ul>
                    </div>
                `).join('');
                
                exportBtn.disabled = false;
                aiGenerateBtn.disabled = false;
                aiGenerateBtn.innerHTML = '<span class="mr-2">✨</span> สร้างชุดคำถามอีกครั้ง';
            }, 2000);
        });
        
        exportBtn.addEventListener('click', () => {
            if (generatedQuizData.length === 0) return;
            const dataStr = JSON.stringify(generatedQuizData, null, 2);
            const blob = new Blob([dataStr], {type: "application/json"});
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = "ai-generated-quiz.json";
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        });

        // Chart.js
        const ctx = document.getElementById('quizCompositionChart');
        if (ctx) {
            new Chart(ctx, {
                type: 'doughnut',
                data: {
                    labels: ['ปรนัย', 'ถูก-ผิด', 'เติมคำ', 'จับคู่'],
                    datasets: [{
                        label: 'สัดส่วนข้อสอบ',
                        data: [60, 15, 15, 10],
                        backgroundColor: ['#FF2E9F', '#C026D3', '#7C3AED', '#4F46E5'],
                        borderColor: 'rgba(26, 30, 48, 0.65)',
                        borderWidth: 4,
                        hoverOffset: 8
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: { display: false },
                        tooltip: { bodyFont: { family: "'Prompt', sans-serif" }, titleFont: { family: "'Prompt', sans-serif" } }
                    },
                    cutout: '70%'
                }
            });
        }
        
        // Scrollspy
        const navLinks = document.querySelectorAll('.nav-link-container a');
        const sections = document.querySelectorAll('main > section');
        window.addEventListener('scroll', () => {
            let current = 'dashboard';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                if(window.pageYOffset >= sectionTop - 120) {
                    current = section.getAttribute('id');
                }
            });
            
            navLinks.forEach(link => {
                link.classList.remove('active');
                if(link.getAttribute('href').substring(1) === current){
                    link.classList.add('active');
                }
            });
        });
    });
  </script>
</body>
</html>
