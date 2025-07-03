<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nayeem Mustakim - Developer Dashboard</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #0f0f23 0%, #1a1a2e 50%, #16213e 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(139, 69, 255, 0.8);
            border-radius: 50%;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 2;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            animation: fadeInDown 1s ease-out;
        }

        .profile-card {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 40px;
            margin-bottom: 30px;
            border: 1px solid rgba(139, 69, 255, 0.3);
            box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
            animation: slideInLeft 1s ease-out;
        }

        .profile-header {
            display: flex;
            align-items: center;
            margin-bottom: 30px;
        }

        .avatar {
            width: 120px;
            height: 120px;
            border-radius: 50%;
            background: linear-gradient(135deg, #8b45ff, #ff006e, #00d4ff);
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 3rem;
            margin-right: 40px;
            animation: profilePulse 3s infinite;
            border: 3px solid rgba(139, 69, 255, 0.6);
            box-shadow: 0 0 30px rgba(139, 69, 255, 0.4);
            position: relative;
            overflow: hidden;
        }

        .avatar::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255, 255, 255, 0.1), transparent);
            animation: shimmer 2s infinite;
        }

        .avatar-icon {
            z-index: 2;
            position: relative;
            filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.5));
        }

        .profile-info h1 {
            color: white;
            font-size: 3rem;
            margin-bottom: 15px;
            background: linear-gradient(45deg, #8b45ff, #ff006e, #00d4ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            font-weight: 700;
            letter-spacing: 2px;
            text-shadow: 0 0 20px rgba(139, 69, 255, 0.3);
            animation: textGlow 2s infinite alternate;
        }

        .profile-info p {
            color: rgba(255, 255, 255, 0.9);
            font-size: 1.3rem;
            font-weight: 300;
            letter-spacing: 1px;
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(15px);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            border: 1px solid rgba(139, 69, 255, 0.3);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            animation: fadeInUp 1s ease-out;
        }

        .stat-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(139, 69, 255, 0.3);
        }

        .stat-icon {
            font-size: 2.5rem;
            margin-bottom: 15px;
            display: block;
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: white;
            margin-bottom: 5px;
        }

        .stat-label {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.9rem;
        }

        .skills-section {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            margin-bottom: 30px;
            border: 1px solid rgba(139, 69, 255, 0.3);
            animation: slideInRight 1s ease-out;
        }

        .skills-title {
            color: white;
            font-size: 1.8rem;
            margin-bottom: 25px;
            text-align: center;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(120px, 1fr));
            gap: 20px;
        }

        .skill-item {
            background: rgba(0, 0, 0, 0.5);
            border-radius: 12px;
            padding: 20px;
            text-align: center;
            transition: transform 0.3s ease;
            animation: bounceIn 1s ease-out;
            border: 1px solid rgba(139, 69, 255, 0.2);
        }

        .skill-item:hover {
            transform: scale(1.05);
            border-color: rgba(139, 69, 255, 0.5);
            box-shadow: 0 8px 25px rgba(139, 69, 255, 0.3);
        }

        .skill-icon {
            font-size: 2.5rem;
            margin-bottom: 10px;
            display: block;
        }

        .skill-name {
            color: white;
            font-size: 0.9rem;
            font-weight: 500;
        }

        .activities-section {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(20px);
            border-radius: 20px;
            padding: 30px;
            border: 1px solid rgba(139, 69, 255, 0.3);
            animation: fadeInUp 1s ease-out;
        }

        .activities-title {
            color: white;
            font-size: 1.8rem;
            margin-bottom: 25px;
            text-align: center;
        }

        .activities-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
        }

        .activity-card {
            background: rgba(0, 0, 0, 0.5);
            border-radius: 15px;
            padding: 25px;
            text-align: center;
            transition: transform 0.3s ease;
            border: 1px solid rgba(139, 69, 255, 0.2);
        }

        .activity-card:hover {
            transform: translateY(-5px);
            border-color: rgba(139, 69, 255, 0.5);
            box-shadow: 0 10px 30px rgba(139, 69, 255, 0.3);
        }

        .activity-icon {
            font-size: 3rem;
            margin-bottom: 15px;
            display: block;
        }

        .activity-title {
            color: white;
            font-size: 1.2rem;
            margin-bottom: 10px;
        }

        .activity-desc {
            color: rgba(255, 255, 255, 0.9);
            font-size: 0.9rem;
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-50px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes slideInLeft {
            from {
                opacity: 0;
                transform: translateX(-50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes slideInRight {
            from {
                opacity: 0;
                transform: translateX(50px);
            }
            to {
                opacity: 1;
                transform: translateX(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes profilePulse {
            0%, 100% {
                transform: scale(1);
                box-shadow: 0 0 30px rgba(139, 69, 255, 0.4);
            }
            50% {
                transform: scale(1.02);
                box-shadow: 0 0 40px rgba(139, 69, 255, 0.6);
            }
        }

        @keyframes shimmer {
            0% {
                transform: translateX(-100%) translateY(-100%) rotate(45deg);
            }
            100% {
                transform: translateX(100%) translateY(100%) rotate(45deg);
            }
        }

        @keyframes textGlow {
            0% {
                filter: drop-shadow(0 0 10px rgba(139, 69, 255, 0.3));
            }
            100% {
                filter: drop-shadow(0 0 20px rgba(139, 69, 255, 0.6));
            }
        }

        @keyframes bounceIn {
            0% {
                opacity: 0;
                transform: scale(0.3);
            }
            50% {
                opacity: 1;
                transform: scale(1.05);
            }
            70% {
                transform: scale(0.9);
            }
            100% {
                opacity: 1;
                transform: scale(1);
            }
        }

        .wave {
            animation: none;
        }

        @media (max-width: 768px) {
            .profile-header {
                flex-direction: column;
                text-align: center;
            }
            
            .avatar {
                margin-right: 0;
                margin-bottom: 25px;
                width: 100px;
                height: 100px;
            }
            
            .profile-info h1 {
                font-size: 2.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="particles"></div>
    
    <div class="container">
        <div class="profile-card">
            <div class="profile-header">
                <div class="avatar">
                    <span class="avatar-icon">👨‍💻</span>
                </div>
                <div class="profile-info">
                    <h1>NAYEEM MUSTAKIM</h1>
                    <p>Full-Stack Flutter Developer</p>
                </div>
            </div>
            
            <div class="stats-grid">
                <div class="stat-card">
                    <span class="stat-icon">🔭</span>
                    <div class="stat-number">Active</div>
                    <div class="stat-label">Working on Projects</div>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">🌱</span>
                    <div class="stat-number">Flutter</div>
                    <div class="stat-label">Building Apps</div>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">🤝</span>
                    <div class="stat-number">Open</div>
                    <div class="stat-label">To Collaborate</div>
                </div>
                <div class="stat-card">
                    <span class="stat-icon">⚡</span>
                    <div class="stat-number">Fun</div>
                    <div class="stat-label">Sports Enthusiast</div>
                </div>
            </div>
        </div>

        <div class="skills-section">
            <h2 class="skills-title">🛠️ Languages & Tools</h2>
            <div class="skills-grid">
                <div class="skill-item">
                    <span class="skill-icon">📱</span>
                    <div class="skill-name">Flutter</div>
                </div>
                <div class="skill-item">
                    <span class="skill-icon">☕</span>
                    <div class="skill-name">Java</div>
                </div>
                <div class="skill-item">
                    <span class="skill-icon">🎨</span>
                    <div class="skill-name">Material UI</div>
                </div>
                <div class="skill-item">
                    <span class="skill-icon">🔥</span>
                    <div class="skill-name">Firebase</div>
                </div>
                <div class="skill-item">
                    <span class="skill-icon">🌿</span>
                    <div class="skill-name">Git</div>
                </div>
            </div>
        </div>

        <div class="activities-section">
            <h2 class="activities-title">🎯 Current Focus</h2>
            <div class="activities-grid">
                <div class="activity-card">
                    <span class="activity-icon">💼</span>
                    <h3 class="activity-title">Client Projects</h3>
                    <p class="activity-desc">Working on personal and client projects with cutting-edge technology</p>
                </div>
                <div class="activity-card">
                    <span class="activity-icon">🏸</span>
                    <h3 class="activity-title">Badminton</h3>
                    <p class="activity-desc">Passionate about playing badminton and staying active</p>
                </div>
                <div class="activity-card">
                    <span class="activity-icon">🚴</span>
                    <h3 class="activity-title">Cycling</h3>
                    <p class="activity-desc">Love exploring new places and staying fit through cycling</p>
                </div>
                <div class="activity-card">
                    <span class="activity-icon">🚀</span>
                    <h3 class="activity-title">Innovation</h3>
                    <p class="activity-desc">Always looking for innovative and impactful project collaborations</p>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Create floating particles
        function createParticles() {
            const particlesContainer = document.querySelector('.particles');
            
            for (let i = 0; i < 50; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 20 + 's';
                particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Animate skill items on scroll
        function animateOnScroll() {
            const skillItems = document.querySelectorAll('.skill-item');
            const statCards = document.querySelectorAll('.stat-card');
            const activityCards = document.querySelectorAll('.activity-card');
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.style.animationDelay = Math.random() * 0.5 + 's';
                        entry.target.style.animation = 'bounceIn 0.8s ease-out forwards';
                    }
                });
            });

            [...skillItems, ...statCards, ...activityCards].forEach(item => {
                observer.observe(item);
            });
        }

        // Add hover effects
        function addHoverEffects() {
            const cards = document.querySelectorAll('.stat-card, .skill-item, .activity-card');
            
            cards.forEach(card => {
                card.addEventListener('mouseenter', () => {
                    card.style.transform = 'translateY(-10px) scale(1.02)';
                    card.style.boxShadow = '0 20px 40px rgba(0, 0, 0, 0.3)';
                });
                
                card.addEventListener('mouseleave', () => {
                    card.style.transform = 'translateY(0) scale(1)';
                    card.style.boxShadow = '0 8px 32px rgba(0, 0, 0, 0.1)';
                });
            });
        }

        // Dynamic gradient animation
        function animateBackground() {
            const body = document.body;
            let hue = 240;
            
            setInterval(() => {
                hue = (hue + 0.3) % 360;
                body.style.background = `linear-gradient(135deg, 
                    hsl(${hue}, 80%, 8%) 0%, 
                    hsl(${(hue + 30) % 360}, 70%, 12%) 50%,
                    hsl(${(hue + 60) % 360}, 60%, 16%) 100%)`;
            }, 150);
        }

        // Initialize all animations
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            animateOnScroll();
            addHoverEffects();
            animateBackground();
        });
    </script>
</body>
</html>
