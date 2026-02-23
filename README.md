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
            background-color: #fafaf9;
            color: #292524;
            -webkit-print-color-adjust: exact !important;
            print-color-adjust: exact !important;
        }

        /* Стабилизация для GitHub: предотвращаем прыжки контента */
        .container {
            width: 100% !important;
            max-width: 1000px !important;
            margin: 0 auto;
        }

        .chart-container {
            position: relative;
            width: 100%;
            height: 300px !important; /* Фиксируем высоту для стабильности */
            margin: 0 auto;
        }

        /* Настройки для идеального PDF */
        @media print {
            body { background-color: white !important; }
            .no-print, .filter-btn, .filter-buttons { display: none !important; }
            
            .grid { 
                display: grid !important; 
                grid-template-columns: repeat(2, 1fr) !important; 
            }
            
            section { 
                page-break-inside: avoid; 
                margin-bottom: 1rem !important;
            }
            
            .shadow-xl, .shadow-2xl { shadow: none !important; border: 1px solid #e5e7eb; }
            
            canvas { 
                max-width: 100% !important; 
                height: auto !important; 
            }
        }

        /* Плавное появление (фикс мерцания Tailwind) */
        [v-cloak] { display: none; }
    </style>
</head>
<body class="p-4 md:p-8">

    <div class="container mx-auto bg-white shadow-2xl rounded-3xl overflow-hidden border border-stone-200">
        <header class="relative bg-stone-900 text-white p-8 md:p-12 overflow-hidden">
            <div class="relative z-10 flex flex-col md:flex-row items-center gap-8">
                <div class="relative w-48 h-48 md:w-56 md:h-56 bg-stone-800 rounded-full flex items-center justify-center text-white font-bold text-6xl overflow-hidden border-4 border-white shadow-xl">
                    <span class="z-0">АЗ</span>
                    <img src="https://i.ibb.co/W4b3CzKy/6b508ae3-5502-4a03-890c-4ef3734063c9.png" 
                         alt="Артем Забіяка" 
                         class="absolute inset-0 w-full h-full object-cover z-10">
                </div>
                
                <div class="text-center md:text-left">
                    <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight mb-2">Артем Забіяка</h1>
                    <p class="text-stone-400 text-xl md:text-2xl font-light mb-6">Junior Fullstack Developer / UI Designer</p>
                    <div class="flex flex-wrap justify-center md:justify-start gap-4 text-sm">
                        <span class="bg-stone-800 px-4 py-2 rounded-full border border-stone-700"><i class="fas fa-map-marker-alt mr-2 text-stone-500"></i>Київ, Україна</span>
                        <span class="bg-stone-800 px-4 py-2 rounded-full border border-stone-700"><i class="fas fa-envelope mr-2 text-stone-500"></i>artem@example.com</span>
                    </div>
                </div>
            </div>
        </header>

        <div class="grid grid-cols-1 lg:grid-cols-3">
            <aside class="lg:col-span-1 bg-stone-50 p-8 border-r border-stone-200">
                <section class="mb-10">
                    <h2 class="text-2xl font-bold mb-6 flex items-center tracking-tighter">
                        <span class="w-8 h-8 bg-stone-800 text-white rounded-lg flex items-center justify-center mr-3 text-sm">01</span>
                        КОНТАКТИ
                    </h2>
                    <div class="space-y-4">
                        <a href="#" class="flex items-center p-3 bg-white rounded-xl border border-stone-200 hover:border-stone-800 transition-colors shadow-sm">
                            <i class="fab fa-telegram text-2xl mr-4 text-stone-600"></i>
                            <div>
                                <p class="text-xs text-stone-400 uppercase font-bold">Telegram</p>
                                <p class="font-semibold">@artem_zabiiaka</p>
                            </div>
                        </a>
                        <a href="#" class="flex items-center p-3 bg-white rounded-xl border border-stone-200 hover:border-stone-800 transition-colors shadow-sm">
                            <i class="fab fa-github text-2xl mr-4 text-stone-600"></i>
                            <div>
                                <p class="text-xs text-stone-400 uppercase font-bold">GitHub</p>
                                <p class="font-semibold">github.com/artem</p>
                            </div>
                        </a>
                    </div>
                </section>

                <section>
                    <h2 class="text-2xl font-bold mb-6 flex items-center tracking-tighter">
                        <span class="w-8 h-8 bg-stone-800 text-white rounded-lg flex items-center justify-center mr-3 text-sm">02</span>
                        МОВИ
                    </h2>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-1 italic">
                                <span>Українська</span>
                                <span class="text-stone-400">Рідна</span>
                            </div>
                            <div class="h-1.5 w-full bg-stone-200 rounded-full overflow-hidden">
                                <div class="h-full bg-stone-800 w-[100%]"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1 italic">
                                <span>Англійська</span>
                                <span class="text-stone-400">B2 (Intermediate)</span>
                            </div>
                            <div class="h-1.5 w-full bg-stone-200 rounded-full overflow-hidden">
                                <div class="h-full bg-stone-800 w-[75%]"></div>
                            </div>
                        </div>
                    </div>
                </section>
            </aside>

            <main class="lg:col-span-2 p-8 md:p-12">
                <section class="mb-12">
                    <h2 class="text-3xl font-black mb-8 tracking-tighter uppercase">Технологічний стек</h2>
                    <div class="chart-container">
                        <canvas id="skillsChart"></canvas>
                    </div>
                </section>

                <section class="mb-12">
                    <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-4">
                        <h2 class="text-3xl font-black tracking-tighter uppercase">Професійні навички</h2>
                        <div class="flex gap-2 filter-buttons no-print">
                            <button onclick="filterSkills('all')" class="filter-btn px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all bg-stone-800 text-white">Всі</button>
                            <button onclick="filterSkills('soft')" class="filter-btn px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all bg-stone-100 text-stone-600 hover:bg-stone-200">Soft</button>
                            <button onclick="filterSkills('hard')" class="filter-btn px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all bg-stone-100 text-stone-600 hover:bg-stone-200">Hard</button>
                        </div>
                    </div>
                    
                    <div id="skillsGrid" class="grid grid-cols-2 md:grid-cols-3 gap-3">
                        </div>
                </section>
            </main>
        </div>
    </div>

    <script>
        // Инициализация графиков
        const ctx = document.getElementById('skillsChart').getContext('2d');
        new Chart(ctx, {
            type: 'radar',
            data: {
                labels: ['HTML/CSS', 'JavaScript', 'React', 'Python', 'UI Design', 'SQL'],
                datasets: [{
                    label: 'Рівень володіння',
                    data: [95, 85, 75, 70, 90, 65],
                    fill: true,
                    backgroundColor: 'rgba(41, 37, 36, 0.1)',
                    borderColor: 'rgb(41, 37, 36)',
                    pointBackgroundColor: 'rgb(41, 37, 36)',
                    pointBorderColor: '#fff',
                    pointHoverBackgroundColor: '#fff',
                    pointHoverBorderColor: 'rgb(41, 37, 36)'
                }]
            },
            options: {
                responsive: true,
                maintainAspectRatio: false,
                elements: { line: { borderWidth: 3 } },
                scales: {
                    r: {
                        angleLines: { display: true },
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

        const skills = [
            { name: 'Командна робота', type: 'soft' },
            { name: 'Критичне мислення', type: 'soft' },
            { name: 'Тайм-менеджмент', type: 'soft' },
            { name: 'Tailwind CSS', type: 'hard' },
            { name: 'Git / GitHub', type: 'hard' },
            { name: 'Figma', type: 'hard' },
            { name: 'React.js', type: 'hard' },
            { name: 'Node.js', type: 'hard' },
            { name: 'Agile/Scrum', type: 'soft' }
        ];

        function renderSkills(filter = 'all') {
            const grid = document.getElementById('skillsGrid');
            grid.innerHTML = '';
            
            const filtered = filter === 'all' ? skills : skills.filter(s => s.type === filter);
            
            filtered.forEach(skill => {
                const bgClass = skill.type === 'soft' ? 'bg-stone-100 text-stone-800' : 'bg-white border-stone-300';
                const el = document.createElement('div');
                el.className = `p-3 rounded-lg border flex justify-between items-center ${bgClass} shadow-sm`;
                el.innerHTML = `<span class="font-bold text-xs uppercase tracking-tight">${skill.name}</span>`;
                grid.appendChild(el);
            });
        }

        function filterSkills(type) {
            renderSkills(type);
            // Визуальное обновление кнопок (для браузера)
            if (window.event) {
                const buttons = document.querySelectorAll('.filter-btn');
                buttons.forEach(b => b.classList.replace('bg-stone-800', 'bg-stone-100'));
                buttons.forEach(b => b.classList.replace('text-white', 'text-stone-600'));
                event.target.classList.add('bg-stone-800', 'text-white');
            }
        }

        // Запуск при загрузке
        window.onload = () => {
            renderSkills();
            // Фикс для корректного размера графиков
            setTimeout(() => { window.dispatchEvent(new Event('resize')); }, 500);
        };
    </script>
</body>
</html>
