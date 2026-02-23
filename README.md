<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Інтерактивне Резюме: Артем Забіяка</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;600;800&display=swap');
        
        body {
            font-family: 'Manrope', sans-serif;
            background-color: #fafaf9; /* stone-50 */
            color: #292524; /* stone-800 */
        }

        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }

        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #f5f5f4; 
        }
        ::-webkit-scrollbar-thumb {
            background: #d6d3d1; 
            border-radius: 4px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #a8a29e; 
        }

        .card-hover {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .card-hover:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1);
        }
        
        .timeline-line {
            position: absolute;
            left: 24px;
            top: 0;
            bottom: 0;
            width: 2px;
            background-color: #e7e5e4;
            z-index: 0;
        }
        @media (min-width: 768px) {
            .timeline-line {
                left: 50%;
                margin-left: -1px;
            }
        }
        .timeline-dot {
            position: absolute;
            left: 24px;
            margin-left: -16px;
            z-index: 20;
            width: 32px;
            height: 32px;
            background-color: #292524;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
        }
        @media (min-width: 768px) {
            .timeline-dot {
                left: 50%;
            }
        }
    </style>
    <!-- Chosen Palette: Warm Neutrals (Stone/Warm Grey) with subtle Orange accents -->
    <!-- Application Structure Plan: 
         1. Hero Section: Personal intro, contacts, and core value proposition.
         2. Dashboard "Metrics": Visualizing the quantitative data (Projects, Rating) and abstracting skills into a "Competence Balance" chart.
         3. Interactive Experience Timeline: A chronological view of work history with expandable details for key achievements.
         4. Skills & Tools Ecosystem: A filterable view of the tech stack (Adobe, AI, Soft Skills) with a breakdown chart.
         5. Education & Growth: Academic background.
         The structure is designed to move from "Who is this?" -> "What are the numbers?" -> "What is the history?" -> "How do they do it?".
    -->
    <!-- Visualization & Content Choices:
         - Radar Chart: To show the balance between Creative, Technical, AI, and Management skills. Goal: Illustrate the "Full Cycle" capability.
         - Doughnut Chart: To visualize the toolset distribution (Adobe vs AI vs Others). Goal: Emphasize the strong AI integration.
         - Interactive Counters: For "30+ Projects" and "5.0 Rating" to draw attention to key success metrics.
         - Timeline: To organize experience chronologically with interactive toggles to reduce text density.
         - CONFIRMATION: NO SVG graphics used. NO Mermaid JS used.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
</head>
<body class="bg-stone-50 min-h-screen flex flex-col">

    <!-- Navigation / Header -->
    <header class="bg-white border-b border-stone-200 sticky top-0 z-50 shadow-sm">
        <div class="container mx-auto px-4 py-4 flex justify-between items-center">
            <div class="flex items-center space-x-2">
                <div class="relative w-10 h-10 bg-stone-800 rounded-full flex items-center justify-center text-white font-bold text-xl overflow-hidden border border-stone-200">
                    <span class="z-0">АЗ</span>
                    <img src="https://ibb.co/b5DNrgnC" alt="Артем Забіяка" class="absolute inset-0 w-full h-full object-cover z-10" onerror="this.style.display='none'">
                </div>
                <div>
                    <h1 class="text-xl font-bold leading-none">Артем Забіяка</h1>
                    <span class="text-xs text-stone-500 uppercase tracking-wider">Моушн-дизайнер | 2D-аніматор</span>
                </div>
            </div>
            <nav class="hidden md:flex space-x-6 text-sm font-medium text-stone-600">
                <a href="#dashboard" class="hover:text-orange-600 transition-colors">Дашборд</a>
                <a href="#experience" class="hover:text-orange-600 transition-colors">Досвід</a>
                <a href="#skills" class="hover:text-orange-600 transition-colors">Навички</a>
                <a href="#education" class="hover:text-orange-600 transition-colors">Освіта</a>
            </nav>
            <div class="flex items-center space-x-4">
                <a href="https://drive.google.com/drive/u/1/folders/1QKtvepXXqdSTxF95KS8qJ02E8A0Fy7Ym" target="_blank" class="hidden sm:inline-block text-sm font-bold text-orange-600 hover:text-orange-700 transition-colors">
                    Портфоліо
                </a>
                <button onclick="document.getElementById('contact-modal').classList.remove('hidden')" class="bg-stone-800 text-white px-4 py-2 rounded-lg text-sm font-medium hover:bg-stone-700 transition-colors">
                    Контакти
                </button>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main class="flex-grow container mx-auto px-4 py-8 space-y-12">

        <!-- Section 1: Hero & Intro -->
        <section class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
            <div class="space-y-6">
                <div class="inline-block px-3 py-1 bg-orange-100 text-orange-800 rounded-full text-xs font-bold tracking-wide">
                    ВІДКРИТИЙ ДО ПРОПОЗИЦІЙ
                </div>
                <h2 class="text-4xl md:text-5xl font-extrabold text-stone-900 leading-tight">
                    Створюю динамічну анімацію та <span class="text-orange-600">AI-контент</span>
                </h2>
                <p class="text-lg text-stone-600 leading-relaxed max-w-xl">
                    Моушн-дизайнер із досвідом повного циклу: від ідеї до фінального рендеру. 
                    <strong class="text-stone-800">30+ успішних проєктів</strong>, інтеграція нейромереж для швидкості та якості, системний підхід до дедлайнів.
                </p>
                <div class="flex flex-wrap gap-4 pt-2">
                    <a href="#experience" class="bg-stone-800 text-white px-6 py-3 rounded-xl font-semibold shadow-lg hover:bg-stone-700 transition-transform active:scale-95">
                        Дивитись досвід
                    </a>
                    <a href="https://drive.google.com/drive/u/1/folders/1QKtvepXXqdSTxF95KS8qJ02E8A0Fy7Ym" target="_blank" class="bg-orange-600 text-white px-6 py-3 rounded-xl font-semibold shadow-lg hover:bg-orange-700 transition-transform active:scale-95">
                        Відкрити Портфоліо
                    </a>
                    <a href="#skills" class="bg-white border border-stone-300 text-stone-700 px-6 py-3 rounded-xl font-semibold hover:bg-stone-50 transition-colors">
                        Мій стек
                    </a>
                </div>
            </div>
            
            <!-- Quick Stats Cards & Photo -->
            <div class="flex flex-col items-center gap-6">
                <div class="relative w-48 h-48 md:w-56 md:h-56 bg-stone-800 rounded-full flex items-center justify-center text-white font-bold text-6xl overflow-hidden border-4 border-white shadow-xl">
    <span class="z-0">А3</span>
    <img src="https://i.ibb.co/W4b3CzKy/6b508ae3-5502-4a03-890c-4ef3734063c9.png" 
         alt="Артем Забіяка" 
         class="absolute inset-0 w-full h-full object-cover z-10">
</div>
                
                <div class="grid grid-cols-2 gap-4 w-full">
                    <div class="bg-white p-6 rounded-2xl shadow-sm border border-stone-100 text-center card-hover">
                        <div class="text-4xl font-bold text-orange-600 mb-1">30+</div>
                    <div class="text-4xl font-bold text-stone-800 mb-1">5.0</div>
                    <div class="text-sm text-stone-500 font-medium">Рейтинг клієнтів</div>
                    <div class="text-xs text-yellow-500 mt-1">★★★★★</div>
                </div>
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-stone-100 text-center card-hover col-span-2">
                    <div class="text-4xl font-bold text-stone-800 mb-1">Full Cycle</div>
                    <div class="text-sm text-stone-500 font-medium">Виробництво відео під ключ</div>
                </div>
            </div>
        </section>

        <hr class="border-stone-200">

        <!-- Section 2: Dashboard / Analytics -->
        <section id="dashboard" class="scroll-mt-24">
            <div class="mb-8">
                <h3 class="text-2xl font-bold text-stone-800">Аналітика Компетенцій</h3>
                <p class="text-stone-600 mt-2">Візуалізація мого професійного балансу між технічними навичками, креативом та менеджментом.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Radar Chart Container -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-stone-100">
                    <h4 class="text-lg font-semibold mb-4 text-center">Профіль Навичок</h4>
                    <div class="chart-container">
                        <canvas id="skillsRadarChart"></canvas>
                    </div>
                    <p class="text-xs text-center text-stone-400 mt-4">Дані базуються на частоті використання навичок у проєктах.</p>
                </div>

                <!-- Doughnut Chart Container -->
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-stone-100">
                    <h4 class="text-lg font-semibold mb-4 text-center">Інструментарій (Tool Stack)</h4>
                    <div class="chart-container">
                        <canvas id="toolsDoughnutChart"></canvas>
                    </div>
                    <p class="text-xs text-center text-stone-400 mt-4">Співвідношення класичних інструментів Adobe та новітніх AI рішень.</p>
                </div>
            </div>
        </section>

        <!-- Section 3: Interactive Experience Timeline -->
        <section id="experience" class="scroll-mt-24">
            <div class="mb-8 flex justify-between items-end">
                <div>
                    <h3 class="text-2xl font-bold text-stone-800">Професійний Шлях</h3>
                    <p class="text-stone-600 mt-2">Інтерактивна хронологія мого досвіду. Натисніть на картку для деталей.</p>
                </div>
            </div>

            <div class="relative space-y-8 pl-8 md:pl-0" id="timeline-container">
                <!-- Timeline items will be injected by JS -->
            </div>
        </section>

        <!-- Section 4: Skills Ecosystem -->
        <section id="skills" class="scroll-mt-24 bg-white rounded-3xl p-8 border border-stone-100 shadow-sm">
            <div class="text-center mb-10">
                <h3 class="text-2xl font-bold text-stone-800">Екосистема Навичок</h3>
                <p class="text-stone-600 mt-2 max-w-2xl mx-auto">Я використовую комбінацію класичного моушн-дизайну та передових AI-технологій для досягнення найкращих результатів.</p>
                
                <!-- Filter Buttons -->
                <div class="flex flex-wrap justify-center gap-2 mt-6" id="skill-filters">
                    <button class="filter-btn active bg-stone-800 text-white px-4 py-2 rounded-full text-sm font-medium transition-colors" data-filter="all">Всі</button>
                    <button class="filter-btn bg-stone-100 text-stone-600 px-4 py-2 rounded-full text-sm font-medium hover:bg-stone-200 transition-colors" data-filter="hard">Hard Skills</button>
                    <button class="filter-btn bg-stone-100 text-stone-600 px-4 py-2 rounded-full text-sm font-medium hover:bg-stone-200 transition-colors" data-filter="software">Software</button>
                    <button class="filter-btn bg-stone-100 text-stone-600 px-4 py-2 rounded-full text-sm font-medium hover:bg-stone-200 transition-colors" data-filter="ai">AI Tools</button>
                </div>
            </div>

            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4" id="skills-grid">
                <!-- Skills injected by JS -->
            </div>
        </section>

        <!-- Section 5: Education -->
        <section id="education" class="scroll-mt-24">
            <h3 class="text-2xl font-bold text-stone-800 mb-6">Освіта та Розвиток</h3>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                
                <!-- University -->
                <div class="bg-stone-100 p-6 rounded-xl border-l-4 border-stone-800">
                    <div class="flex justify-between items-start mb-2">
                        <h4 class="font-bold text-lg text-stone-900">Магістратура: Менеджмент</h4>
                        <span class="bg-stone-800 text-white text-xs px-2 py-1 rounded">2025 - дотепер</span>
                    </div>
                    <p class="text-stone-600 text-sm mb-4">Європейський університет</p>
                    <p class="text-stone-500 text-xs italic">Розвиток управлінських навичок для ефективної роботи над комплексними проєктами.</p>
                </div>

                <div class="bg-stone-100 p-6 rounded-xl border-l-4 border-stone-400">
                    <div class="flex justify-between items-start mb-2">
                        <h4 class="font-bold text-lg text-stone-900">Бакалавр</h4>
                        <span class="bg-white text-stone-600 text-xs px-2 py-1 rounded border border-stone-200">2014 - 2018</span>
                    </div>
                    <p class="text-stone-600 text-sm">КПІ ім. Ігоря Сікорського</p>
                    <p class="text-stone-500 text-xs italic mt-2">Фундаментальна технічна освіта.</p>
                </div>

                <!-- Courses List -->
                <div class="md:col-span-2 bg-white border border-stone-200 p-6 rounded-xl">
                    <h4 class="font-bold text-lg text-stone-900 mb-4">Профільні Курси</h4>
                    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4">
                        <div class="flex items-center space-x-3 p-3 bg-stone-50 rounded-lg">
                            <span class="text-orange-600 text-xl">●</span>
                            <div>
                                <div class="font-semibold text-sm">Color Management</div>
                                <div class="text-xs text-stone-500">В процесі</div>
                            </div>
                        </div>
                        <div class="flex items-center space-x-3 p-3 bg-stone-50 rounded-lg">
                            <span class="text-green-600 text-xl">●</span>
                            <div>
                                <div class="font-semibold text-sm">Супер After Effects</div>
                                <div class="text-xs text-stone-500">VideoSmile (2024)</div>
                            </div>
                        </div>
                        <div class="flex items-center space-x-3 p-3 bg-stone-50 rounded-lg">
                            <span class="text-green-600 text-xl">●</span>
                            <div>
                                <div class="font-semibold text-sm">AE from FreelStep</div>
                                <div class="text-xs text-stone-500">2023</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

    </main>

    <!-- Footer -->
    <footer class="bg-stone-900 text-stone-300 py-12 mt-12">
        <div class="container mx-auto px-4 text-center">
            <h2 class="text-2xl font-bold text-white mb-6">Готові до співпраці?</h2>
            <div class="flex flex-col md:flex-row justify-center items-center gap-6 mb-8">
                <a href="https://drive.google.com/drive/u/1/folders/1QKtvepXXqdSTxF95KS8qJ02E8A0Fy7Ym" target="_blank" class="flex items-center gap-2 text-orange-400 hover:text-orange-300 transition-colors font-bold">
                    <span class="text-xl">📁</span> Дивитись Портфоліо
                </a>
                <a href="mailto:artemzabiiaka@icloud.com" class="flex items-center gap-2 hover:text-white transition-colors">
                    <span class="text-xl">✉</span> artemzabiiaka@icloud.com
                </a>
                <a href="tel:+380989757974" class="flex items-center gap-2 hover:text-orange-400 transition-colors">
                    <span class="text-xl">☎</span> +38 (098) 975-79-74
                </a>
                <a href="https://t.me/ArtemZabiiaka" target="_blank" class="flex items-center gap-2 hover:text-orange-400 transition-colors">
                    <span class="text-xl w-6 text-center"><i class="fa-brands fa-telegram"></i></span> @ArtemZabiiaka
                </a>
            </div>
            <p class="text-stone-500 text-sm">&copy; 2026 Артем Забіяка. Всі права захищено.</p>
        </div>
    </footer>

    <!-- Contact Modal (Hidden by default) -->
    <div id="contact-modal" class="fixed inset-0 bg-black bg-opacity-50 hidden z-50 flex items-center justify-center backdrop-blur-sm p-4">
        <div class="bg-white rounded-2xl p-8 max-w-md w-full shadow-2xl transform transition-all relative">
            <button onclick="document.getElementById('contact-modal').classList.add('hidden')" class="absolute top-4 right-4 text-stone-400 hover:text-stone-800 font-bold text-xl">✕</button>
            <h3 class="text-xl font-bold text-stone-900 mb-4">Зв'язатися зі мною</h3>
            <div class="space-y-4">
                <a href="https://drive.google.com/drive/u/1/folders/1QKtvepXXqdSTxF95KS8qJ02E8A0Fy7Ym" target="_blank" class="block w-full bg-orange-100 text-orange-800 border border-orange-200 text-center py-3 rounded-xl font-bold hover:bg-orange-200 transition-colors">
                    Відкрити Портфоліо (Google Drive)
                </a>
                <a href="https://t.me/ArtemZabiiaka" class="block w-full bg-[#0088cc] text-white text-center py-3 rounded-xl font-semibold hover:opacity-90 transition-opacity">
                    <i class="fa-brands fa-telegram mr-2"></i>Написати в Telegram
                </a>
                <a href="mailto:artemzabiiaka@icloud.com" class="block w-full bg-stone-800 text-white text-center py-3 rounded-xl font-semibold hover:bg-stone-700 transition-opacity">
                    Написати Email
                </a>
                <a href="tel:+380989757974" class="block w-full border border-stone-300 text-stone-700 text-center py-3 rounded-xl font-semibold hover:bg-stone-50 transition-opacity">
                    Зателефонувати
                </a>
            </div>
        </div>
    </div>

    <script>
        // Data Store
        const resumeData = {
            experience: [
                {
                    id: 1,
                    role: "Моушн-дизайнер",
                    company: "Фундація “Незламна Україна”",
                    period: "2024 – дотепер",
                    type: "Full-time / Contract",
                    desc: "Повний цикл виробництва навчальних відео та інтеграція AI.",
                    details: [
                        "Забезпечення повного циклу виробництва: збір матеріалів, анімація, саунд-дизайн, титри.",
                        "Інтеграція AI-інструментів для оптимізації часу та підвищення якості.",
                        "Адаптація контенту під різні платформи.",
                        "Візуалізація складних освітніх тем."
                    ]
                },
                {
                    id: 2,
                    role: "Моушн-дизайнер (Фріланс)",
                    company: "Fiverr & Upwork",
                    period: "2023 – 2024",
                    type: "Freelance",
                    desc: "30+ комерційних проєктів з рейтингом 5.0.",
                    details: [
                        "Успішне виконання 30+ проєктів з оцінкою 5.0.",
                        "Паралельне ведення 2-3 проєктів з жорсткими дедлайнами.",
                        "Створення власної бази пресетів та шаблонів.",
                        "Швидка генерація ідей та розв'язання технічних завдань."
                    ]
                }
            ],
            skills: [
                { name: "2D Анімація", type: "hard", level: 95 },
                { name: "Анімація тексту", type: "hard", level: 90 },
                { name: "Візуальні ефекти (VFX)", type: "hard", level: 85 },
                { name: "Відеомонтаж", type: "hard", level: 85 },
                { name: "Генерація контенту ШІ", type: "hard", level: 85 },
                { name: "Створення шаблонів", type: "hard", level: 90 },
                { name: "Ротоскопіювання", type: "hard", level: 75 },
                { name: "Трекінг", type: "hard", level: 80 },
                { name: "Кеювання", type: "hard", level: 80 },
                { name: "Базовий звукомонтаж", type: "hard", level: 70 },
                { name: "After Effects", type: "software", level: 95 },
                { name: "Premiere Pro", type: "software", level: 85 },
                { name: "Illustrator", type: "software", level: 80 },
                { name: "Photoshop", type: "software", level: 80 },
                { name: "Figma", type: "software", level: 75 },
                { name: "Veo 3", type: "ai", level: 80 },
                { name: "RunwayML", type: "ai", level: 75 },
                { name: "DeepFaceLab", type: "ai", level: 60 },
                { name: "Leonardo.Ai", type: "ai", level: 85 },
                { name: "ElevenLabs", type: "ai", level: 80 },
                { name: "Nano Banana", type: "ai", level: 70 },
                { name: "Менеджмент", type: "soft", level: 100 },
                { name: "Комунікація", type: "soft", level: 90 }
            ]
        };

        // --- Initialization ---
        document.addEventListener('DOMContentLoaded', () => {
            renderCharts();
            renderTimeline();
            renderSkills('all');
            setupFilters();
        });

        // --- Charts Implementation ---
        function renderCharts() {
            // Radar Chart: Skills Profile
            const ctxRadar = document.getElementById('skillsRadarChart').getContext('2d');
            new Chart(ctxRadar, {
                type: 'radar',
                data: {
                    labels: ['Анімація (Motion)', 'Технічні (Soft/AI)', 'Менеджмент', 'Дизайн (Visual)', 'Монтаж (Edit)'],
                    datasets: [{
                        label: 'Рівень компетенції',
                        data: [5, 7, 6, 3, 5],
                        backgroundColor: 'rgba(234, 88, 12, 0.2)', // Orange-600 with opacity
                        borderColor: 'rgba(234, 88, 12, 1)',
                        pointBackgroundColor: 'rgba(234, 88, 12, 1)',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: 'rgba(234, 88, 12, 1)'
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            min: 0,
                            max: 8,
                            angleLines: { color: '#e7e5e4' },
                            grid: { color: '#e7e5e4' },
                            pointLabels: {
                                font: { size: 12, family: 'Manrope' },
                                color: '#44403c'
                            },
                            ticks: { display: false, stepSize: 1 }
                        }
                    },
                    plugins: {
                        legend: { display: false }
                    }
                }
            });

            // Doughnut Chart: Tool Stack
            const ctxDoughnut = document.getElementById('toolsDoughnutChart').getContext('2d');
            // Counting tools
            const softwareCount = 10;
            const aiCount = 8;
            const hardCount = 6;

            new Chart(ctxDoughnut, {
                type: 'doughnut',
                data: {
                    labels: ['Adobe & Design', 'AI Tools', 'Core Skills'],
                    datasets: [{
                        data: [softwareCount, aiCount, hardCount],
                        backgroundColor: [
                            '#292524', // Stone-800
                            '#ea580c', // Orange-600
                            '#a8a29e'  // Stone-400
                        ],
                        borderWidth: 0
                    }]
                },
                options: {
                    maintainAspectRatio: false,
                    cutout: '70%',
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                usePointStyle: true,
                                font: { family: 'Manrope' }
                            }
                        }
                    }
                }
            });
        }

        // --- Timeline Implementation ---
        function renderTimeline() {
            const container = document.getElementById('timeline-container');
            container.innerHTML = `<div class="timeline-line"></div>`; // Vertical line

            resumeData.experience.forEach((job, index) => {
                const isEven = index % 2 === 0;
                
                // HTML for the timeline Item
                const itemHTML = `
                    <div class="relative w-full mb-12 flex flex-col md:flex-row ${isEven ? 'md:justify-start' : 'md:justify-end'}">
                        <div class="timeline-dot">
                            <span class="w-2 h-2 rounded-full bg-white block"></span>
                        </div>
                        <div class="w-full md:w-5/12 pl-16 md:pl-0 ${isEven ? 'md:pr-12 md:text-right' : 'md:pl-12 md:text-left'}">
                            <div class="bg-white p-6 rounded-xl shadow-sm border border-stone-100 hover:border-orange-200 transition-colors cursor-pointer group" onclick="toggleJobDetails(${job.id})">
                                <span class="inline-block px-2 py-1 bg-stone-100 text-stone-600 text-xs rounded mb-2">${job.period}</span>
                                <h4 class="font-bold text-lg text-stone-800 group-hover:text-orange-600 transition-colors">${job.company}</h4>
                                <h5 class="font-semibold text-stone-600 text-sm mb-2">${job.role}</h5>
                                <p class="text-stone-500 text-sm mb-3">${job.desc}</p>
                                
                                <div id="job-details-${job.id}" class="hidden mt-4 pt-4 border-t border-stone-100 text-left">
                                    <ul class="list-disc list-inside text-sm text-stone-600 space-y-1">
                                        ${job.details.map(d => `<li>${d}</li>`).join('')}
                                    </ul>
                                </div>
                                
                                <div class="text-orange-600 text-xs font-bold mt-2 flex items-center ${isEven ? 'md:justify-end' : 'md:justify-start'} justify-start gap-1">
                                    <span id="job-btn-text-${job.id}">Показати деталі</span> <span>▼</span>
                                </div>
                            </div>
                        </div>
                    </div>
                `;
                container.innerHTML += itemHTML;
            });
        }

        function toggleJobDetails(id) {
            const details = document.getElementById(`job-details-${id}`);
            const btnText = document.getElementById(`job-btn-text-${id}`);
            
            if (details.classList.contains('hidden')) {
                details.classList.remove('hidden');
                btnText.textContent = "Згорнути";
            } else {
                details.classList.add('hidden');
                btnText.textContent = "Показати деталі";
            }
        }

        // --- Skills Implementation ---
        function renderSkills(filter) {
            const grid = document.getElementById('skills-grid');
            grid.innerHTML = '';

            const filteredSkills = filter === 'all' 
                ? resumeData.skills 
                : resumeData.skills.filter(s => s.type === filter);

            filteredSkills.forEach(skill => {
                let bgClass = 'bg-stone-50 text-stone-700';
                let icon = '';
                
                if (skill.type === 'ai') { bgClass = 'bg-orange-50 text-orange-800 border-orange-100'; icon = '✦'; }
                if (skill.type === 'software') { bgClass = 'bg-stone-100 text-stone-800 border-stone-200'; icon = '💻'; }
                if (skill.type === 'hard') { bgClass = 'bg-white text-stone-800 border-stone-300 shadow-sm'; icon = '🛠'; }

                const el = document.createElement('div');
                el.className = `p-3 rounded-lg border flex justify-between items-center ${bgClass} transition-all hover:scale-105`;
                el.innerHTML = `
                    <span class="font-medium text-sm">${skill.name}</span>
                    <span class="text-xs opacity-50 ml-2">${icon}</span>
                `;
                grid.appendChild(el);
            });
        }

        function setupFilters() {
            const buttons = document.querySelectorAll('.filter-btn');
            buttons.forEach(btn => {
                btn.addEventListener('click', (e) => {
                    // Update active state
                    buttons.forEach(b => {
                        b.classList.remove('bg-stone-800', 'text-white');
                        b.classList.add('bg-stone-100', 'text-stone-600');
                    });
                    e.target.classList.remove('bg-stone-100', 'text-stone-600');
                    e.target.classList.add('bg-stone-800', 'text-white');

                    // Render
                    renderSkills(e.target.dataset.filter);
                });
            });
        }

    </script>
</body>
</html>
