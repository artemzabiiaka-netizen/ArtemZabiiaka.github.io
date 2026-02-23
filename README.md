<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Резюме | Артем Забіяка</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;600;800&display=swap');
        
        body {
            font-family: 'Manrope', sans-serif;
            background-color: #f5f5f4; /* stone-100 */
        }

        /* Плавная анимация появления контента */
        .fade-in {
            animation: fadeIn 0.8s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Чтобы графики не ломали верстку на мобилках */
        .chart-wrapper {
            position: relative;
            margin: auto;
            height: 300px;
            width: 100%;
        }

        /* Стилизация скроллбара */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #444; border-radius: 10px; }
    </style>
</head>
<body class="p-4 md:p-10">

    <div class="max-w-6xl mx-auto fade-in">
        <div class="bg-white shadow-2xl rounded-[2rem] overflow-hidden border border-stone-200">
            
            <header class="bg-stone-900 text-white p-8 md:p-16 relative overflow-hidden">
                <div class="absolute top-0 right-0 w-64 h-64 bg-stone-800 rounded-full -mr-32 -mt-32 opacity-50"></div>
                
                <div class="relative z-10 flex flex-col md:flex-row items-center gap-8 md:gap-12">
                    <div class="group relative">
                        <div class="w-48 h-48 md:w-56 md:h-56 bg-stone-800 rounded-2xl border-4 border-stone-700 overflow-hidden shadow-2xl transform transition-transform group-hover:scale-105 duration-300">
                            <img src="https://i.ibb.co/W4b3CzKy/6b508ae3-5502-4a03-890c-4ef3734063c9.png" 
                                 alt="Артем" class="w-full h-full object-cover">
                        </div>
                    </div>

                    <div class="text-center md:text-left">
                        <h1 class="text-4xl md:text-7xl font-black tracking-tighter mb-4">АРТЕМ ЗАБІЯКА</h1>
                        <p class="text-stone-400 text-xl md:text-2xl font-light mb-8 italic">Junior Fullstack Developer</p>
                        
                        <div class="flex flex-wrap justify-center md:justify-start gap-4">
                            <a href="mailto:artem@example.com" class="bg-stone-800 hover:bg-stone-700 px-5 py-2 rounded-full text-sm border border-stone-700 transition-all flex items-center">
                                <i class="fas fa-envelope mr-2 text-stone-500"></i> Пошта
                            </a>
                            <a href="https://t.me/artem_zabiiaka" target="_blank" class="bg-stone-800 hover:bg-stone-700 px-5 py-2 rounded-full text-sm border border-stone-700 transition-all flex items-center">
                                <i class="fab fa-telegram mr-2 text-stone-500"></i> Telegram
                            </a>
                        </div>
                    </div>
                </div>
            </header>

            <div class="grid grid-cols-1 lg:grid-cols-12">
                
                <aside class="lg:col-span-4 bg-stone-50 p-8 md:p-12 border-r border-stone-200">
                    <section class="mb-12">
                        <h3 class="text-xs font-black text-stone-400 uppercase tracking-[0.2em] mb-6">Про мене</h3>
                        <p class="text-stone-600 leading-relaxed">
                            Захоплююсь створенням чистих, сучасних та функціональних веб-інтерфейсів. Постійно вивчаю нові технології та вдосконалюю навички у Fullstack розробці.
                        </p>
                    </section>

                    <section class="mb-12">
                        <h3 class="text-xs font-black text-stone-400 uppercase tracking-[0.2em] mb-6">Мови</h3>
                        <div class="space-y-4">
                            <div>
                                <div class="flex justify-between text-sm font-bold mb-1">
                                    <span>Українська</span>
                                    <span>Рідна</span>
                                </div>
                                <div class="h-1 bg-stone-200 rounded-full"><div class="h-1 bg-stone-800 w-full rounded-full"></div></div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm font-bold mb-1">
                                    <span>Англійська</span>
                                    <span>B2</span>
                                </div>
                                <div class="h-1 bg-stone-200 rounded-full"><div class="h-1 bg-stone-800 w-3/4 rounded-full"></div></div>
                            </div>
                        </div>
                    </section>
                </aside>

                <main class="lg:col-span-8 p-8 md:p-12 bg-white">
                    <section class="mb-16">
                        <h2 class="text-3xl font-black mb-10 tracking-tighter uppercase border-b-4 border-stone-900 inline-block">Технологічний радар</h2>
                        <div class="chart-wrapper">
                            <canvas id="skillsChart"></canvas>
                        </div>
                    </section>

                    <section>
                        <h2 class="text-3xl font-black mb-10 tracking-tighter uppercase border-b-4 border-stone-900 inline-block">Навички</h2>
                        <div class="grid grid-cols-2 sm:grid-cols-3 gap-4">
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">FRONTEND</span>
                                <span class="font-bold">HTML5 / CSS3</span>
                            </div>
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">SCRIPTING</span>
                                <span class="font-bold">JavaScript ES6</span>
                            </div>
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">STYLING</span>
                                <span class="font-bold">Tailwind CSS</span>
                            </div>
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">LIBRARY</span>
                                <span class="font-bold">React.js</span>
                            </div>
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">TOOLS</span>
                                <span class="font-bold">Git / GitHub</span>
                            </div>
                            <div class="p-4 rounded-2xl bg-stone-50 border border-stone-200 hover:border-stone-800 transition-all group">
                                <span class="block text-xs font-black text-stone-400 mb-1 group-hover:text-stone-800">DESIGN</span>
                                <span class="font-bold">Figma UI</span>
                            </div>
                        </div>
                    </section>
                </main>
            </div>
        </div>
    </div>

    <script>
        const ctx = document.getElementById('skillsChart').getContext('2d');
        
        // Настройка шрифтов для Chart.js
        Chart.defaults.font.family = "'Manrope', sans-serif";
        Chart.defaults.color = '#78716c';

        new Chart(ctx, {
            type: 'radar',
            data: {
                labels: ['Frontend', 'Backend', 'UI Design', 'Logic', 'Version Control', 'Soft Skills'],
                datasets: [{
                    label: 'Рівень',
                    data: [95, 65, 85, 80, 90, 95],
                    backgroundColor: 'rgba(28, 25, 23, 0.1)',
                    borderColor: '#1c1917',
                    borderWidth: 3,
                    pointBackgroundColor: '#1c1917',
                    pointBorderColor: '#fff',
                    pointHoverRadius: 5
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                scales: {
                    r: {
                        grid: { color: '#e7e5e4' },
                        angleLines: { color: '#e7e5e4' },
                        suggestedMin: 0,
                        suggestedMax: 100,
                        ticks: { display: false }
                    }
                },
                plugins: {
                    legend: { display: false }
                }
            }
        });

        // Реактивность для GitHub Pages
        window.addEventListener('resize', () => {
            Chart.instances[0].resize();
        });
    </script>
</body>
</html>
