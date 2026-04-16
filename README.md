<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Your Name - Portfolio Resume</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: #333;
            overflow-x: hidden;
        }

        .container {
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* Animated Background */
        .bg-animation {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            animation: gradientShift 15s ease infinite;
        }

        @keyframes gradientShift {
            0%, 100% { background: linear-gradient(135deg, #667eea 0%, #764ba2 100%); }
            33% { background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%); }
            66% { background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%); }
        }

        /* Floating Particles */
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
            background: rgba(255, 255, 255, 0.1);
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
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Navigation */
        .nav {
            position: fixed;
            top: 30px;
            right: 30px;
            z-index: 1000;
        }

        .nav-toggle {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            padding: 12px;
            border-radius: 50%;
            cursor: pointer;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }

        .nav-toggle:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }

        /* Main Content */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .hero-content h1 {
            font-size: clamp(3rem, 8vw, 6rem);
            font-weight: 700;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #fff, #f0f0f0);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            animation: textGlow 3s ease-in-out infinite alternate;
        }

        @keyframes textGlow {
            from { filter: drop-shadow(0 0 20px rgba(255,255,255,0.5)); }
            to { filter: drop-shadow(0 0 30px rgba(255,255,255,0.8)); }
        }

        .hero-content .subtitle {
            font-size: clamp(1.2rem, 3vw, 1.8rem);
            font-weight: 300;
            margin-bottom: 2rem;
            opacity: 0.9;
        }

        .scroll-indicator {
            position: absolute;
            bottom: 30px;
            left: 50%;
            transform: translateX(-50%);
            color: rgba(255,255,255,0.7);
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
            40% { transform: translateX(-50%) translateY(-10px); }
            60% { transform: translateX(-50%) translateY(-5px); }
        }

        /* Sections */
        .section {
            padding: 120px 5% 80px;
            max-width: 1200px;
            margin: 0 auto;
            position: relative;
        }

        .section-title {
            font-size: 3rem;
            font-weight: 700;
            margin-bottom: 3rem;
            text-align: center;
            background: linear-gradient(45deg, #333, #666);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 80px;
            height: 4px;
            background: linear-gradient(90deg, #667eea, #764ba2);
            border-radius: 2px;
        }

        /* Skills Grid */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.95);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.2);
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }

        .skill-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.4), transparent);
            transition: left 0.5s;
        }

        .skill-card:hover::before {
            left: 100%;
        }

        .skill-card:hover {
            transform: translateY(-15px) scale(1.02);
            box-shadow: 0 30px 60px rgba(0,0,0,0.2);
        }

        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        /* Experience Timeline */
        .timeline {
            position: relative;
            max-width: 800px;
            margin: 0 auto;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 4px;
            height: 100%;
            background: linear-gradient(to bottom, #667eea, #764ba2);
            border-radius: 2px;
        }

        .timeline-item {
            display: flex;
            margin-bottom: 4rem;
            position: relative;
        }

        .timeline-item:nth-child(odd) {
            justify-content: flex-end;
            padding-right: 0;
        }

        .timeline-item:nth-child(even) {
            justify-content: flex-start;
            padding-left: 0;
        }

        .timeline-content {
            width: 45%;
            background: rgba(255, 255, 255, 0.95);
            padding: 2rem;
            border-radius: 20px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
            position: relative;
            transition: all 0.3s ease;
        }

        .timeline-content:hover {
            transform: translateY(-5px);
        }

        .timeline-dot {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
            width: 20px;
            height: 20px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 50%;
            z-index: 2;
            box-shadow: 0 0 0 4px rgba(255,255,255,0.8);
        }

        /* Projects Grid */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            transition: all 0.4s ease;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 30px 60px rgba(0,0,0,0.2);
        }

        .project-image {
            height: 200px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 4rem;
            position: relative;
        }

        .project-content {
            padding: 2rem;
        }

        /* Contact */
        .contact {
            text-align: center;
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 4rem 2rem;
            max-width: 600px;
            margin: 0 auto;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        }

        .contact-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-top: 2rem;
            flex-wrap: wrap;
        }

        .contact-link {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: #333;
            text-decoration: none;
            padding: 1rem 2rem;
            border: 2px solid transparent;
            border-radius: 50px;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .contact-link:hover {
            border-color: #667eea;
            color: #667eea;
            transform: translateY(-3px);
        }

        /* Responsive */
        @media (max-width: 768px) {
            .timeline::before {
                left: 20px;
            }
            
            .timeline-item {
                flex-direction: column;
                align-items: flex-start;
                padding-left: 60px !important;
                padding-right: 0 !important;
            }
            
            .timeline-content {
                width: 100%;
                margin-left: 0;
            }
            
            .timeline-dot {
                left: 20px;
            }
        }

        /* Scroll animations */
        .fade-in {
            opacity: 0;
            transform: translateY(50px);
            transition: all 0.8s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <div class="bg-animation"></div>
    <div class="particles" id="particles"></div>
    
    <nav class="nav">
        <button class="nav-toggle" onclick="scrollToTop()">
            <i class="fas fa-arrow-up"></i>
        </button>
    </nav>

    <div class="container">
        <!-- Hero Section -->
        <section class="hero">
            <div class="hero-content fade-in">
                <h1>John Doe</h1>
                <p class="subtitle">Full Stack Developer & UI/UX Designer</p>
                <div class="scroll-indicator">
                    <i class="fas fa-chevron-down"></i>
                </div>
            </div>
        </section>

        <!-- Skills Section -->
        <section class="section" id="skills">
            <h2 class="section-title fade-in">Skills</h2>
            <div class="skills-grid">
                <div class="skill-card fade-in">
                    <div class="skill-icon">
                        <i class="fab fa-react"></i>
                    </div>
                    <h3>Frontend</h3>
                    <p>React, Vue.js, Next.js, Tailwind CSS, TypeScript</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">
                        <i class="fas fa-server"></i>
                    </div>
                    <h3>Backend</h3>
                    <p>Node.js, Python, Express, MongoDB, PostgreSQL</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <h3>Mobile</h3>
                    <p>React Native, Flutter, Swift, Kotlin</p>
                </div>
                <div class="skill-card fade-in">
                    <div class="skill-icon">
                        <i class="fas fa-cloud"></i>
                    </div>
                    <h3>DevOps</h3>
                    <p>Docker, AWS, CI/CD, Kubernetes, Git</p>
                </div>
            </div>
        </section>

        <!-- Experience Section -->
        <section class="section" id="experience">
            <h2 class="section-title fade-in">Experience</h2>
            <div class="timeline">
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content fade-in">
                        <h3>Senior Full Stack Developer</h3>
                        <span>TechCorp Inc. — 2022 - Present</span>
                        <p>Led development of scalable web applications serving 1M+ users. Implemented microservices architecture and optimized performance by 40%.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content fade-in">
                        <h3>Frontend Developer</h3>
                        <span>StartupXYZ — 2020 - 2022</span>
                        <p>Designed and developed responsive UIs using React and TypeScript. Collaborated with design team to create award-winning interfaces.</p>
                    </div>
                </div>
                <div class="timeline-item">
                    <div class="timeline-dot"></div>
                    <div class="timeline-content fade-in">
                        <h3>Junior Developer</h3>
                        <span>WebSolutions — 2019 - 2020</span>
                        <p>Built and maintained client websites using modern JavaScript frameworks and CMS platforms.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Projects Section -->
        <section class="section" id="projects">
            <h2 class="section-title fade-in">Projects</h2>
            <div class="projects-grid">
                <div class="project-card fade-in">
                    <div class="project-image">
                        <i class="fas fa-globe"></i>
                    </div>
                    <div class="project-content">
                        <h3>E-Commerce Platform</h3>
                        <p>Full-stack e-commerce solution with real-time inventory and payment integration.</p>
                        <div style="margin-top: 1rem;">
                            <span class="tech-tag">React</span>
                            <span class="tech-tag">Node.js</span>
                            <span class="tech-tag">Stripe</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">
                        <i class="fas fa-chart-line"></i>
                    </div>
                    <div class="project-content">
                        <h3>Analytics Dashboard</h3>
                        <p>Interactive data visualization dashboard with real-time updates and ML insights.</p>
                        <div style="margin-top: 1rem;">
                            <span class="tech-tag">Vue.js</span>
                            <span class="tech-tag">D3.js</span>
                            <span class="tech-tag">Python</span>
                        </div>
                    </div>
                </div>
                <div class="project-card fade-in">
                    <div class="project-image">
                        <i class="fas fa-mobile-alt"></i>
                    </div>
                    <div class="project-content">
                        <h3>Mobile Banking App</h3>
                        <p>Cross-platform banking app with biometric authentication and real-time transactions.</p>
                        <div style="margin-top: 1rem;">
                            <span class="tech-tag">React Native</span>
                            <span class="tech-tag">Firebase</span>
                            <span class="tech-tag">GraphQL</span>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section class="section" id="contact">
            <div class="contact fade-in">
                <h2 class="section-title">Let's Connect</h2>
                <p style="font-size: 1.2rem; margin-bottom: 2rem; opacity: 0.8;">
                    Ready to build something amazing together?
                </p>
                                <div class="contact-links">
                    <a href="mailto:john@example.com" class="contact-link">
                        <i class="fas fa-envelope"></i>
                        Email
                    </a>
                    <a href="https://linkedin.com/in/johndoe" class="contact-link" target="_blank">
                        <i class="fab fa-linkedin"></i>
                        LinkedIn
                    </a>
                    <a href="https://github.com/johndoe" class="contact-link" target="_blank">
                        <i class="fab fa-github"></i>
                        GitHub
                    </a>
                    <a href="https://twitter.com/johndoe" class="contact-link" target="_blank">
                        <i class="fab fa-twitter"></i>
                        Twitter
                    </a>
                </div>
            </div>
        </section>
    </div>

    <script>
        // Create floating particles
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            for (let i = 0; i < 50; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.width = particle.style.height = (Math.random() * 4 + 1) + 'px';
                particle.style.animationDelay = Math.random() * 20 + 's';
                particle.style.animationDuration = (Math.random() * 10 + 10) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Smooth scroll to top
        function scrollToTop() {
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        // Intersection Observer for fade-in animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observe all fade-in elements
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            
            document.querySelectorAll('.fade-in').forEach(el => {
                observer.observe(el);
            });

            // Smooth scrolling for anchor links
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    const target = document.querySelector(this.getAttribute('href'));
                    if (target) {
                        target.scrollIntoView({
                            behavior: 'smooth',
                            block: 'start'
                        });
                    }
                });
            });

            // Parallax effect for hero
            window.addEventListener('scroll', () => {
                const scrolled = window.pageYOffset;
                const hero = document.querySelector('.hero');
                const rate = scrolled * -0.5;
                hero.style.transform = `translateY(${rate}px)`;
            });
        });

        // Tech tags styling (add this CSS if you want styled tags)
        const style = document.createElement('style');
        style.textContent = `
            .tech-tag {
                display: inline-block;
                background: linear-gradient(45deg, #667eea, #764ba2);
                color: white;
                padding: 0.3rem 0.8rem;
                border-radius: 20px;
                font-size: 0.8rem;
                font-weight: 500;
                margin-right: 0.5rem;
                margin-bottom: 0.5rem;
                box-shadow: 0 4px 15px rgba(102, 126, 234, 0.4);
            }
        `;
        document.head.appendChild(style);

        // Typing effect for hero subtitle (optional enhancement)
        function typeWriter(element, text, speed = 100) {
            let i = 0;
            element.innerHTML = '';
            function type() {
                if (i < text.length) {
                    element.innerHTML += text.charAt(i);
                    i++;
                    setTimeout(type, speed);
                }
            }
            type();
        }

        // Uncomment below to enable typing effect
        /*
        window.addEventListener('load', () => {
            const subtitle = document.querySelector('.subtitle');
            const originalText = subtitle.textContent;
            subtitle.textContent = '';
            setTimeout(() => typeWriter(subtitle, originalText), 1000);
        });
        */
    </script>
</body>
</html>
