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
            margin: 0;
            padding: 0;
        }

        /* Стабилизация для GitHub Pages */
        .resume-wrapper {
            opacity: 0;
            transition: opacity 0.5s ease-in;
        }
        .resume-wrapper.loaded {
            opacity: 1;
        }

        /* Фикс для графиков: предотвращает прыжки верстки */
        .chart-container {
            position: relative;
            width: 100%;
            height: 350px !important;
            margin-bottom: 2rem;
        }

        @media (min-width: 1024px) {
            .main-grid {
                display: grid !important;
                grid-template-columns: repeat(12, 1fr) !important;
            }
        }

        /* Убираем мерцание Tailwind */
        [v-cloak] { display: none; }
    </style>
</head>
<body class="p-4 md:p-8 flex justify-center">

    <div id="app" class="resume-wrapper container max-w-6xl mx-auto bg-white shadow-2xl rounded-3xl overflow-hidden border border-stone-200">
        <header class="relative bg-stone-900 text-white p-8 md:p-12 overflow-hidden">
            <div class="relative z-10 flex flex-col md:flex-row items-center gap-8">
                <div class="relative w-48 h-48 md:w-56 md:h-56 bg-stone-800 rounded-full flex items-center justify-center text-white font-bold text-6xl overflow-hidden border-4 border-white shadow-xl">
                    <span>АЗ</span>
                    <img src="https://i.ibb.co/W4b3CzKy/6b508ae3-5502-4a03-890c-4ef3734063c9.png" alt="Артем Забіяка" class="absolute inset-0 w-full h-full object-cover z-10" onerror="this.style.display='none'">
                </div>
                
                <div class="text-center md:text-left">
                    <h1 class="text-4xl md:text-6xl font-extrabold tracking-tight mb-2">Артем Забіяка</h1>
                    <p class="text-stone-400 text-xl md:text-2xl font-light mb-6 uppercase tracking-widest">Junior Fullstack Developer</p>
                    <div class="flex flex-wrap justify-center md:justify-start gap-4">
                        <span class="bg-stone-800 px-4 py-2 rounded-full border border-stone-700 text-sm"><i class="fas fa-map-marker-alt mr-2 text-stone-500"></i>Київ, Україна</span>
                        <span class="bg-stone-800 px-4 py-2 rounded-full border border-stone-700 text-sm"><i class="fas fa-envelope mr-2 text-stone-500"></i>artem.zabiiaka@gmail.com</span>
                    </div>
                </div>
            </div>
        </header>

        <div class="main-grid flex flex-col lg:flex-row">
            <aside class="lg:w-1/3 bg-stone-50 p-8 border-r border-stone-200">
                <section class="mb-10">
                    <h2 class="text-2xl font-bold mb-6 flex items-center tracking-tighter uppercase">Контакты</h2>
                    <div class="space-y-4">
                        <a href="https://t.me/artem_zabiiaka" target="_blank" class="flex items-center p-3 bg-white rounded-xl border border-stone-200 hover:border-stone-800 transition-all shadow-sm group">
                            <i class="fab fa-telegram text-2xl mr-4 text-stone-600 group-hover:text-sky-500"></i>
                            <div>
                                <p class="text-xs text-stone-400 uppercase font-bold">Telegram</p>
                                <p class="font-semibold text-sm">@artem_zabiiaka</p>
                            </div>
                        </a>
                        <a href="https://github.com/ArtemZabiiaka" target="_blank" class="flex items-center p-3 bg-white rounded-xl border border-stone-200 hover:border-stone-800 transition-all shadow-sm group">
                            <i class="fab fa-github text-2xl mr-4 text-stone-600 group-hover:text-black"></i>
                            <div>
                                <p class="text-xs text-stone-400 uppercase font-bold">GitHub</p>
                                <p class="font-semibold text-sm">ArtemZabiiaka</p>
                            </div>
                        </a>
                    </div>
                </section>

                <section>
                    <h2 class="text-2xl font-bold mb-6 flex items-center tracking-tighter uppercase">Мови</h2>
                    <div class="space-y-4">
                        <div>
                            <div class="flex justify-between mb-1 italic text-sm">
                                <span>Українська</span>
                                <span class="text-stone-400">Рідна</span>
                            </div>
                            <div class="h-1.5 w-full bg-stone-200 rounded-full overflow-hidden">
                                <div class="h-full bg-stone-800 w-full"></div>
                            </div>
                        </div>
                        <div>
                            <div class="flex justify-between mb-1 italic text-sm">
                                <span>Англійська</span>
                                <span class="text-stone-400">B2 (Upper-Intermediate)</span>
                            </div>
                            <div class="h-1.5 w-full bg-stone-200 rounded-full overflow-hidden">
                                <div class="h-full bg-stone-800 w-[75%]"></div>
                            </div>
                        </div>
                    </div>
                </section>
            </aside>

            <main class="lg:w-2/3 p-8 md:p-12">
                <section class="mb-12">
                    <h2 class="text-3xl font-black mb-8 tracking-tighter border-b-4 border-stone-900 inline-block uppercase">Технологічний стек</h2>
                    <div class="chart-container">
                        <canvas id="skillsChart"></canvas>
                    </div>
                </section>

                <section>
                    <div class="flex flex-col md:flex-row md:items-center justify-between mb-8 gap-4">
                        <h2 class="text-3xl font-black tracking-tighter uppercase">Навички</h2>
                        <div class="flex gap-2 filter-buttons">
                            <button class="filter-btn active bg-stone-800 text-white px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all" data-type="all">Всі</button>
                            <button class="filter-btn bg-stone-100 text-stone-600 px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all hover:bg-stone-200" data-type="software">Soft</button>
                            <button class="filter-btn bg-stone-100 text-stone-600 px-4 py-1.5 rounded-full text-xs font-bold uppercase tracking-wider transition-all hover:bg-stone-200" data-type="hard">Hard</button>
                        </div>
                    </div>
                    
                    <div id="skillsGrid" class="grid grid-cols-2 md:grid-cols-3 gap-3">
                        </div>
                </section>
            </main>
        </div>
    </div>

    <script>
        const skills = [
            { name: 'HTML5 / CSS3', type: 'hard' },
            { name: 'JavaScript ES6+', type: 'hard' },
            { name: 'React.js', type: 'hard' },
            { name: 'Tailwind CSS', type: 'hard' },
            { name: 'Python / Flask', type: 'hard' },
            { name: 'SQL / NoSQL', type: 'hard' },
            { name: 'Git / GitHub', type: 'hard' },
            { name: 'UI/UX Design', type: 'hard' },
            { name: 'Docker', type: 'hard' },
            { name: 'Командна робота', type: 'software' },
            { name: 'Критичне мислення', type: 'software' },
            { name: 'Тайм-менеджмент', type: 'software' },
            { name: 'Agile / Scrum', type: 'software' },
            { name: 'English B2', type: 'software' },
            { name: 'Problem Solving', type: 'software' }
        ];

        function initChart() {
            const ctx = document.getElementById('skillsChart').getContext('2d');
            new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['Frontend', 'Backend', 'UI/UX Design', 'Database', 'DevOps', 'Soft Skills'],
                    datasets: [{
                        label: 'Рівень компетенцій',
                        data: [95, 75, 85, 70, 60, 90],
                        backgroundColor: 'rgba(41, 37, 36, 0.1)',
                        borderColor: '#292524',
                        borderWidth: 3,
                        pointBackgroundColor: '#292524',
                        pointBorderColor: '#fff',
                        pointHoverBackgroundColor: '#fff',
                        pointHoverBorderColor: '#292524'
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        r: {
                            angleLines: { color: '#e7e5e4' },
                            grid: { color: '#e7e5e4' },
                            suggestedMin: 0,
                            suggestedMax: 100,
                            ticks: { display: false }
                        }
                    },
                    plugins: { legend: { display: false } }
                }
            });
        }

        function renderSkills(filterType = 'all') {
            const grid = document.getElementById('skillsGrid');
            grid.innerHTML = '';

            const filteredSkills = filterType === 'all' ? skills : skills.filter(s => s.type === filterType);

            filteredSkills.forEach(skill => {
                let bgClass = '';
                let icon = '';
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
                    buttons.forEach(b => {
                        b.classList.remove('bg-stone-800', 'text-white');
                        b.classList.add('bg-stone-100', 'text-stone-600');
                    });
                    e.target.classList.remove('bg-stone-100', 'text-stone-600');
                    e.target.classList.add('bg-stone-800', 'text-white');
                    renderSkills(e.target.dataset.type);
                });
            });
        }

        window.addEventListener('load', () => {
            document.getElementById('app').classList.add('loaded');
            initChart();
            renderSkills();
            setupFilters();
            // Финальный пересчет размеров для корректности сетки
            setTimeout(() => { window.dispatchEvent(new Event('resize')); }, 200);
        });
    </script>
</body>
</html>
