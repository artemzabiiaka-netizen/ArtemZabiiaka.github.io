<!DOCTYPE html>
<html lang="uk">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Резюме: Артем Забіяка</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;600;800&display=swap');
        
        body {
            font-family: 'Manrope', sans-serif;
            background-color: #fafaf9;
            margin: 0; padding: 20px;
            display: flex; justify-content: center;
        }

        /* ЖЕСТКАЯ СТРУКТУРА (не дает блокам разъезжаться) */
        .main-container {
            width: 100%;
            max-width: 1100px;
            background: white;
            border-radius: 24px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            display: flex;
            flex-direction: column;
        }

        header {
            background: #1c1917;
            color: white;
            padding: 40px;
            display: flex;
            align-items: center;
            gap: 30px;
        }

        .content-layout {
            display: flex;
            flex-wrap: wrap; /* Для мобильных устройств */
        }

        aside {
            width: 300px; /* Фиксированная ширина сайдбара */
            background: #fbfbfb;
            padding: 40px;
            border-right: 1px solid #e7e5e4;
        }

        main {
            flex: 1; /* Занимает всё оставшееся место */
            padding: 40px;
            min-width: 320px;
        }

        .chart-container {
            position: relative;
            height: 350px;
            width: 100%;
            margin-bottom: 30px;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(150px, 1fr));
            gap: 12px;
        }

        @media (max-width: 768px) {
            header { flex-direction: column; text-align: center; }
            aside { width: 100%; border-right: none; border-bottom: 1px solid #e7e5e4; }
            .content-layout { flex-direction: column; }
        }

        /* Фикс для аватара */
        .avatar-box {
            width: 180px; height: 180px;
            border-radius: 50%;
            border: 4px solid white;
            overflow: hidden;
            flex-shrink: 0;
            background: #292524;
            position: relative;
        }
    </style>
</head>
<body>

    <div class="main-container">
        <header>
            <div class="avatar-box">
                <img src="https://i.ibb.co/W4b3CzKy/6b508ae3-5502-4a03-890c-4ef3734063c9.png" 
                     alt="Артем" style="width:100%; height:100%; object-fit:cover;">
            </div>
            <div>
                <h1 style="font-size: 3rem; margin: 0; font-weight: 800; letter-spacing: -2px;">АРТЕМ ЗАБІЯКА</h1>
                <p style="color: #a8a29e; font-size: 1.25rem; margin-top: 5px;">Junior Fullstack Developer</p>
            </div>
        </header>

        <div class="content-layout">
            <aside>
                <h3 style="text-transform: uppercase; font-size: 0.75rem; letter-spacing: 2px; color: #78716c;">Контакти</h3>
                <p style="font-weight: 600; margin-bottom: 5px;">📍 Київ, Україна</p>
                <p style="font-weight: 600; margin-bottom: 5px;">✉️ artem.zab@gmail.com</p>
                <p style="font-weight: 600;">📱 @artem_zabiiaka</p>
                
                <hr style="margin: 30px 0; border: 0; border-top: 1px solid #e7e5e4;">
                
                <h3 style="text-transform: uppercase; font-size: 0.75rem; letter-spacing: 2px; color: #78716c;">Мови</h3>
                <p><b>Українська</b> — Рідна</p>
                <p><b>Англійська</b> — B2</p>
            </aside>

            <main>
                <h2 style="font-size: 1.8rem; font-weight: 800; margin-bottom: 25px; border-bottom: 4px solid #1c1917; display: inline-block;">СТЕК ТЕХНОЛОГІЙ</h2>
                
                <div class="chart-container">
                    <canvas id="skillsChart"></canvas>
                </div>

                <h2 style="font-size: 1.8rem; font-weight: 800; margin-top: 40px; margin-bottom: 25px; border-bottom: 4px solid #1c1917; display: inline-block;">НАВИЧКИ</h2>
                
                <div class="skills-grid" id="skillsGrid">
                    </div>
            </main>
        </div>
    </div>

    <script>
        const skills = [
            { name: 'HTML5/CSS3', type: 'hard' },
            { name: 'JavaScript ES6', type: 'hard' },
            { name: 'React.js', type: 'hard' },
            { name: 'Tailwind CSS', type: 'hard' },
            { name: 'Python', type: 'hard' },
            { name: 'Git / GitHub', type: 'hard' },
            { name: 'Teamwork', type: 'soft' },
            { name: 'Time Management', type: 'soft' },
            { name: 'Problem Solving', type: 'soft' }
        ];

        function renderSkills() {
            const grid = document.getElementById('skillsGrid');
            skills.forEach(skill => {
                const div = document.createElement('div');
                div.style.padding = '12px';
                div.style.background = 'white';
                div.style.border = '1px solid #e7e5e4';
                div.style.borderRadius = '8px';
                div.style.fontSize = '0.8rem';
                div.style.fontWeight = '700';
                div.style.textAlign = 'center';
                div.innerText = skill.name;
                grid.appendChild(div);
            });
        }

        function initChart() {
            const ctx = document.getElementById('skillsChart').getContext('2d');
            new Chart(ctx, {
                type: 'radar',
                data: {
                    labels: ['Frontend', 'Backend', 'Design', 'Git', 'Soft Skills', 'Logic'],
                    datasets: [{
                        data: [95, 70, 85, 90, 95, 80],
                        backgroundColor: 'rgba(28, 25, 23, 0.1)',
                        borderColor: '#1c1917',
                        borderWidth: 2
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: { legend: { display: false } }
                }
            });
        }

        window.onload = () => {
            renderSkills();
            initChart();
            // Принудительный ресайз для GitHub
            setTimeout(() => { window.dispatchEvent(new Event('resize')); }, 300);
        };
    </script>
</body>
</html>
