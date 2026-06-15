<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Piyush Kumar Hota</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">

    <style>
        /* ==========================================================================
           1. DESIGN TOKENS & SYSTEM THEMES
           ========================================================================== */
        :root[data-theme="dark"] {
            --bg-main: #0a0f1d;
            --text-main: #f3f4f6;
            --text-muted: #9ca3af;
            --accent: #3b82f6;
            --accent-rgb: 59, 130, 246;
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.08);
            --glass-shadow: rgba(0, 0, 0, 0.3);
            --orb-1: #1e3a8a;
            --orb-2: #581c87;
            --orb-3: #0369a1;
        }

        :root[data-theme="light"] {
            --bg-main: #f8fafc;
            --text-main: #0f172a;
            --text-muted: #475569;
            --accent: #6366f1;
            --accent-rgb: 99, 102, 241;
            --glass-bg: rgba(255, 255, 255, 0.4);
            --glass-border: rgba(255, 255, 255, 0.6);
            --glass-shadow: rgba(15, 23, 42, 0.05);
            --orb-1: #e0e7ff;
            --orb-2: #fae8ff;
            --orb-3: #e0f2fe;
        }

        :root[data-theme="cyber"] {
            --bg-main: #050508;
            --text-main: #00ffcc;
            --text-muted: #8899a6;
            --accent: #ff007f;
            --accent-rgb: 255, 0, 127;
            --glass-bg: rgba(5, 5, 8, 0.6);
            --glass-border: rgba(0, 255, 204, 0.2);
            --glass-shadow: rgba(255, 0, 127, 0.15);
            --orb-1: #110022;
            --orb-2: #001122;
            --orb-3: #1a001a;
        }

        /* ==========================================================================
           2. BASE SETUP & RESET
           ========================================================================== */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Inter', sans-serif;
            background-color: var(--bg-main);
            color: var(--text-main);
            overflow-x: hidden;
            transition: background-color 0.5s ease, color 0.3s ease;
            line-height: 1.6;
        }

        /* ==========================================================================
           3. ANIMATED & PARALLAX BACKGROUND
           ========================================================================== */
        .bg-wrapper {
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            z-index: -1;
            overflow: hidden;
        }

        .bg-gradient {
            position: absolute;
            width: 100%;
            height: 100%;
            opacity: 0.4;
            background: radial-gradient(circle at 50% 50%, rgba(var(--accent-rgb), 0.1), transparent 70%);
        }

        .parallax-orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px);
            opacity: 0.6;
            transition: transform 0.2s cubic-bezier(0.1, 0.8, 0.2, 1);
            will-change: transform;
        }

        .orb-1 { width: 400px; height: 400px; background: var(--orb-1); top: -10%; left: -10%; }
        .orb-2 { width: 500px; height: 500px; background: var(--orb-2); bottom: -10%; right: -10%; }
        .orb-3 { width: 350px; height: 350px; background: var(--orb-3); top: 40%; left: 60%; }

        /* ==========================================================================
           4. GLASSMORPHISM UTILITY & HEADER
           ========================================================================== */
        .glass {
            background: var(--glass-bg);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid var(--glass-border);
            box-shadow: 0 8px 32px 0 var(--glass-shadow);
        }

        .header-glass {
            position: fixed;
            top: 0;
            width: 100%;
            z-index: 1000;
            background: rgba(var(--bg-main), 0.2);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border-bottom: 1px solid var(--glass-border);
            transition: background 0.4s ease, border-color 0.4s ease;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1.2rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-weight: 800;
            font-size: 1.5rem;
            text-decoration: none;
            color: var(--text-main);
            letter-spacing: -1px;
        }

        .logo span { color: var(--accent); }

        .nav-links a {
            color: var(--text-main);
            text-decoration: none;
            margin-left: 2rem;
            font-size: 0.95rem;
            font-weight: 600;
            opacity: 0.8;
            transition: opacity 0.3s, color 0.3s;
        }

        .nav-links a:hover {
            opacity: 1;
            color: var(--accent);
        }

        #theme-toggle {
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            padding: 0.5rem;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.1rem;
            transition: transform 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        #theme-toggle:hover {
            transform: scale(1.1) rotate(15deg);
        }

        /* ==========================================================================
           5. SECTIONS & LAYOUTS
           ========================================================================== */
        section {
            max-width: 1200px;
            margin: 0 auto;
            padding: 8rem 2rem 4rem 2rem;
            min-height: 80vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        /* Hero Section */
        .hero-section { min-height: 100vh; }
        .hero-title {
            font-size: 4.5rem;
            font-weight: 800;
            line-height: 1.1;
            letter-spacing: -2px;
            margin-bottom: 1.5rem;
        }

        .text-gradient {
            background: linear-gradient(45deg, var(--accent), #ec4899);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }

        .hero-subtitle {
            font-size: 1.25rem;
            color: var(--text-muted);
            max-width: 600px;
            margin-bottom: 2.5rem;
        }

        /* Buttons */
        .cta-group { display: flex; gap: 1rem; }
        .btn {
            padding: 0.8rem 2rem;
            border-radius: 8px;
            font-weight: 600;
            text-decoration: none;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }

        .btn-primary {
            background: var(--accent);
            color: #ffffff;
            box-shadow: 0 4px 15px rgba(var(--accent-rgb), 0.4);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(var(--accent-rgb), 0.5);
        }

        .btn-secondary {
            background: var(--glass-bg);
            color: var(--text-main);
            border: 1px solid var(--glass-border);
        }

        .btn-secondary:hover {
            background: var(--glass-border);
            transform: translateY(-3px);
        }

        /* Projects Layout */
        .section-header { margin-bottom: 4rem; }
        .section-header h2 { font-size: 2.5rem; font-weight: 800; margin-bottom: 0.5rem;}
        .section-header p { color: var(--text-muted); }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 2.5rem;
        }

        .project-card {
            border-radius: 16px;
            overflow: hidden;
            transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.4s ease;
        }

        .project-card:hover {
            transform: translateY(-10px) scale(1.01);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        .project-image-wrapper {
            width: 100%;
            height: 220px;
            overflow: hidden;
            position: relative;
        }

        .project-image-placeholder {
            width: 100%;
            height: 100%;
            transition: transform 0.5s ease;
        }

        .project-card:hover .project-image-placeholder {
            transform: scale(1.08);
        }

        .project-info { padding: 2rem; }
        .project-tag {
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: var(--accent);
            font-weight: 800;
        }

        .project-info h3 { margin: 0.5rem 0 1rem 0; font-size: 1.5rem; font-weight: 600; }
        .project-info p { color: var(--text-muted); margin-bottom: 1.5rem; font-size: 0.95rem;}

        .project-links { display: flex; gap: 1.5rem; }
        .project-link {
            color: var(--text-main);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 600;
        }

        .project-link.source { color: var(--text-muted); }
        .project-link:hover { color: var(--accent); }

        /* About Section */
        .about-container { padding: 3rem; border-radius: 24px; }
        .about-text h2 { font-size: 2.5rem; margin-bottom: 1.5rem; }
        .about-text p { margin-bottom: 1.5rem; color: var(--text-muted); max-width: 800px;}

        .skills-tags { display: flex; flex-wrap: wrap; gap: 0.8rem; margin-top: 2rem;}
        .skill-tag {
            background: var(--glass-bg);
            border: 1px solid var(--glass-border);
            padding: 0.5rem 1.2rem;
            border-radius: 50px;
            font-size: 0.85rem;
            font-weight: 600;
        }

        /* Contact Section */
        .contact-section { align-items: center; text-align: center; min-height: 60vh; }
        .contact-card {
            padding: 4rem 2rem;
            border-radius: 24px;
            max-width: 700px;
            width: 100%;
        }
        .contact-card h2 { font-size: 2.5rem; margin-bottom: 1rem; }
        .contact-card p { color: var(--text-muted); margin-bottom: 2rem; }

        /* Footer */
        footer {
            text-align: center;
            padding: 3rem 2rem;
            border-top: 1px solid var(--glass-border);
            color: var(--text-muted);
            font-size: 0.9rem;
        }

        /* ==========================================================================
           6. PREMIUM MOTION & REVEAL STRUCTURING
           ========================================================================== */
        .reveal {
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s cubic-bezier(0.16, 1, 0.3, 1), transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
            will-change: transform, opacity;
        }

        .reveal.active {
            opacity: 1;
            transform: translateY(0);
        }

        @media (max-width: 768px) {
            .hero-title { font-size: 3rem; }
            .nav-links { display: none; }
            section { padding: 6rem 1.5rem 2rem 1.5rem; }
        }
    </style>
</head>
<body>

    <div class="bg-wrapper">
        <div class="bg-gradient"></div>
        <div class="parallax-orb orb-1"></div>
        <div class="parallax-orb orb-2"></div>
        <div class="parallax-orb orb-3"></div>
    </div>

    <header class="navbar header-glass">
        <div class="nav-container">
            <a href="#" class="logo">ARUL<span>.</span></a>
            <nav class="nav-links">
                <a href="#hero">Home</a>
                <a href="#projects">Works</a>
                <a href="#about">About</a>
                <a href="#contact">Contact</a>
            </nav>
            <div class="theme-switch-wrapper">
                <button id="theme-toggle" aria-label="Toggle Theme">
                    <span class="theme-icon">🌙</span>
                </button>
            </div>
        </div>
    </header>

    <main>
        <section id="hero" class="hero-section">
            <div class="hero-content reveal">
                <h1 class="hero-title">HELLO THERE!<br><span class="text-gradient">This is Arul,</span></h1>
                <p class="hero-subtitle">A fellow specializing in nothing...🫡</p>
                <div class="cta-group">
                    <a href="#projects" class="btn btn-primary">View My Projects</a>
                    <a href="#contact" class="btn btn-secondary">Get In Touch</a>
                </div>
            </div>
        </section>

        <section id="projects" class="projects-section">
            <div class="section-header reveal">
                <h2>Selected Works</h2>
                <p>A curated selection of projects.</p>
            </div>

            <div class="projects-grid">
                
                <div class="project-card glass reveal">
                    <div class="project-image-wrapper">
                        <div class="project-image-placeholder" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"></div>
                    </div>
                    <div class="project-info">
                        <span class="project-tag">jetaeronautics</span>
                        <h3>Systems in modern fighter aviation</h3>
                        <p>Advanced Aeronautics: Aerodynamics,Propulsion, and Integrated Systems inmModern Fighter Aviation</p>
                        <div class="project-links">
                            <a href="https://github.com/ARUL-space/jetaeronautics/blob/main/Systems%20in%20Modern%20Fighter%20Aviation.pdf" class="project-link">Pdf ↗</a>
                            <a href="https://github.com/ARUL-space/jetaeronautics/raw/refs/heads/main/Advanced%20Aeronautical%20Engineering.docx" class="project-link source">Word file ↗</a>
                        </div>
                    </div>
                </div>
                
               <div class="project-card glass reveal">
                    <div class="project-image-wrapper">
                        <div class="project-image-placeholder" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"></div>
                    </div>
                    <div class="project-info">
                        <span class="project-tag">jetaeronautics</span>
                        <h3>THE Evolution and Engineering of Aerospace Propulsion.</h3>
                        <p>"It felt as if angels were pushing-Adolf Galland on early jet fight."</p>
                        <div class="project-links">
                            <a href="https://github.com/ARUL-space/jetaeronautics/blob/main/The%20Evolution%20and%20Engineering%20of%20Aerospace%20Propulsion.pdf" class="project-link">Pdf ↗</a>
                            <a href="https://github.com/ARUL-space/jetaeronautics/raw/refs/heads/main/The%20Evolution%20and%20Engineering%20of%20Aerospace%20Propulsion.docx" class="project-link source">Word file ↗</a>
                        </div>
                    </div>
                </div>
                <div class="project-card glass reveal">
                    <div class="project-image-wrapper">
                        <div class="project-image-placeholder" style="background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);"></div>
                    </div>
                    <div class="project-info">
                        <span class="project-tag">jetaeronautics</span>
                        <h3>SF_25 SINGULARITY</h3>
                        <p>Design and Integration of the SF-25 Hypersonic TBCC Engine with Retractable UHTCMC Turbine Isolation and Multiphase Thermal Protection.</p>
                        <div class="project-links">
                            <a href="https://github.com/ARUL-space/jetaeronautics/blob/main/Design%20and%20Integration%20of%20the%20SF.pdf" class="project-link">Pdf ↗</a>
                            <a href="https://github.com/ARUL-space/jetaeronautics/raw/refs/heads/main/Design%20and%20Integration%20of%20the%20SF.docx" class="project-link source">Word file ↗</a>
                        </div>
                    </div>
                </div>
        </section>

        <section id="about" class="about-section">
            <div class="about-container glass reveal">
                <div class="about-text">
                    <h2>About Me</h2>
                    <p>"Sometimes, an overwhelming restlessness settles in, and my eccentric passions gently pull me back into those bittersweet, beautiful depths. In that space, the rigid world of studies and schedules fades entirely. It is a captivating escape—simultaneously a blissful sanctuary and a guilty distraction. Yet, I find myself powerless against the pull; after all, our days are fleeting, and life is far too short to ignore the things that truly make us feel alive."</p>
                   SKILL tags...
                    <div class="skills-tags">
                        <span class="skill-tag">i don't really know</span>
                        <span class="skill-tag">wasting time in some shitty things</span>
                        <span class="skill-tag">forever a delusionist</span>
                        <span class="skill-tag">Not so intresting</span>
                        <span class="skill-tag">Multiple intrests</span>
                      <span class="skill-tag">NONCHALANT</span>
                    <span class="skill-tag">getting everything wrong in my life all by myself and all due to my faults..</span>
                      <span class="skill-tag">keep going even if everything goes wrong</span>
                    
                </div>
                </div>
            </div>
        </section>

        <section id="contact" class="contact-section">
            <div class="contact-card glass reveal">
                <h2>Let's Create Something Remarkable</h2>
                <p>Whether you have an exciting project in mind or just want to chat, my inbox is open.</p>
                <a href="https://www.instagram.com/zero_hertz_?igsh=NXJiYTVrYXI4enQx" class="btn btn-primary email-btn">Say Hello</a>
            </div>
        </section>
    </main>

    <footer>
        <p>&copy; 2026 Developer Portfolio. Built with precision and fluid motion.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            
            // --- Theme Switch Switcher Controls ---
            const themeToggle = document.getElementById('theme-toggle');
            const themes = ['dark', 'light', 'cyber'];
            let currentThemeIndex = 0;

            themeToggle.addEventListener('click', () => {
                currentThemeIndex = (currentThemeIndex + 1) % themes.length;
                const nextTheme = themes[currentThemeIndex];
                
                document.documentElement.setAttribute('data-theme', nextTheme);
                
                const icons = { dark: '🌙', light: '☀️', cyber: '🔮' };
                themeToggle.querySelector('.theme-icon').textContent = icons[nextTheme];
            });

            // --- Scroll Intersection Monitoring Engine ---
            const revealElements = document.querySelectorAll('.reveal');
            const revealOptions = {
                threshold: 0.1,
                rootMargin: "0px 0px -50px 0px"
            };

            const revealObserver = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('active');
                        observer.unobserve(entry.target); 
                    }
                });
            }, revealOptions);

            revealElements.forEach(element => {
                revealObserver.observe(element);
            });

            // --- Accelerated Parallax Node Tracking ---
            const orbs = document.querySelectorAll('.parallax-orb');
            let lastScrollY = window.scrollY;
            let ticked = false;

            function updateOrbs() {
                const speedMultiplier = [0.15, -0.1, 0.05]; 
                
                orbs.forEach((orb, index) => {
                    const speed = speedMultiplier[index] || 0.1;
                    const yOffset = lastScrollY * speed;
                    orb.style.transform = `translate3d(0, ${yOffset}px, 0)`;
                });

                ticked = false;
            }

            window.addEventListener('scroll', () => {
                lastScrollY = window.scrollY;

                if (!ticked) {
                    window.requestAnimationFrame(() => {
                        updateOrbs();
                    });
                    ticked = true;
                }
            });
        });
    </script>
</body>
</html>
