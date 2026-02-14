# sumit-portfolio
Professional Portfolio Website - B.Tech CSE AIML Student at Suresh Gyan Vihar University
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sumit - Modern Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            overflow-x: hidden;
        }

        /* Navigation */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 1rem 0;
            z-index: 1000;
            transition: all 0.3s ease;
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.8rem;
            font-weight: bold;
            color: #333;
            text-decoration: none;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: #333;
            font-weight: 500;
            transition: color 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: #667eea;
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -5px;
            left: 0;
            background: linear-gradient(45deg, #667eea, #764ba2);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        /* Hero Section */
        .hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            text-align: center;
            color: white;
            position: relative;
        }

        .hero-content {
            max-width: 800px;
            padding: 2rem;
            animation: fadeInUp 1s ease-out;
        }

        .hero h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
            opacity: 0;
            animation: fadeInUp 1s ease-out 0.5s forwards;
        }

        .hero p {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0;
            animation: fadeInUp 1s ease-out 1s forwards;
        }

        .cta-button {
            display: inline-block;
            padding: 1rem 2rem;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            text-decoration: none;
            border-radius: 50px;
            font-weight: bold;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            opacity: 0;
            animation: fadeInUp 1s ease-out 1.5s forwards;
        }

        .cta-button:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 107, 107, 0.4);
        }

        /* Floating Particles */
        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            overflow: hidden;
            z-index: -1;
        }

        .particle {
            position: absolute;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        .particle:nth-child(1) {
            width: 20px;
            height: 20px;
            top: 20%;
            left: 10%;
            animation-delay: 0s;
        }

        .particle:nth-child(2) {
            width: 30px;
            height: 30px;
            top: 60%;
            left: 80%;
            animation-delay: 2s;
        }

        .particle:nth-child(3) {
            width: 15px;
            height: 15px;
            top: 40%;
            left: 60%;
            animation-delay: 4s;
        }

        .particle:nth-child(4) {
            width: 25px;
            height: 25px;
            top: 80%;
            left: 20%;
            animation-delay: 1s;
        }

        .particle:nth-child(5) {
            width: 18px;
            height: 18px;
            top: 30%;
            left: 90%;
            animation-delay: 3s;
        }

        /* About Section */
        .about {
            padding: 5rem 0;
            background: white;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
        }

        .section-title {
            text-align: center;
            font-size: 3rem;
            margin-bottom: 3rem;
            color: #333;
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            width: 100px;
            height: 4px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 4rem;
            align-items: center;
        }

        .about-image {
            text-align: center;
        }

        .profile-img {
            width: 300px;
            height: 300px;
            border-radius: 50%;
            object-fit: cover;
            border: 5px solid #667eea;
            box-shadow: 0 20px 40px rgba(102, 126, 234, 0.3);
            transition: transform 0.3s ease;
        }

        .profile-img-container:hover .profile-img,
        .profile-img-container:hover .profile-img-fallback {
            transform: scale(1.05);
        }

        .about-text {
            font-size: 1.2rem;
            color: #666;
            line-height: 1.8;
        }

        /* Skills Section */
        .skills {
            padding: 5rem 0;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .skill-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            padding: 2rem;
            border-radius: 15px;
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .skill-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            display: block;
        }

        .skill-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
        }

        /* Projects Section */
        .projects {
            padding: 5rem 0;
            background: white;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .project-link {
            text-decoration: none;
            color: inherit;
            display: block;
        }

        .project-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            cursor: pointer;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 2rem;
        }

        .project-content {
            padding: 2rem;
            position: relative;
        }

        .project-card h3 {
            font-size: 1.5rem;
            margin-bottom: 1rem;
            color: #333;
        }

        .project-card p {
            color: #666;
            line-height: 1.6;
            margin-bottom: 1rem;
        }

        .view-project {
            display: inline-block;
            color: #667eea;
            font-weight: bold;
            font-size: 0.9rem;
            opacity: 0;
            transform: translateY(10px);
            transition: all 0.3s ease;
        }

        .project-card:hover .view-project {
            opacity: 1;
            transform: translateY(0);
        }

        /* Contact Section */
        .contact {
            padding: 5rem 0;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .contact-form {
            max-width: 600px;
            margin: 3rem auto 0;
        }

        .form-group {
            margin-bottom: 2rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            border: none;
            border-radius: 10px;
            background: rgba(255, 255, 255, 0.1);
            color: white;
            font-size: 1rem;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .submit-btn {
            width: 100%;
            padding: 1rem;
            background: linear-gradient(45deg, #ff6b6b, #ee5a24);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }

        .submit-btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(255, 107, 107, 0.4);
        }

        /* Footer */
        footer {
            background: #333;
            color: white;
            text-align: center;
            padding: 2rem 0;
        }

        .social-links {
            margin-top: 1rem;
        }

        .social-links a {
            color: white;
            font-size: 1.5rem;
            margin: 0 1rem;
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .social-links a:hover {
            color: #667eea;
        }

        /* Animations */
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

        @keyframes float {
            0%, 100% {
                transform: translateY(0px);
            }
            50% {
                transform: translateY(-20px);
            }
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .hero h1 {
                font-size: 2.5rem;
            }

            .hero p {
                font-size: 1.2rem;
            }

            .nav-links {
                display: none;
            }

            .about-content {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .profile-img {
                width: 250px;
                height: 250px;
            }

            .section-title {
                font-size: 2.5rem;
            }
        }

        /* Smooth scroll behavior */
        html {
            scroll-behavior: smooth;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 10px;
        }

        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }

        ::-webkit-scrollbar-thumb {
            background: linear-gradient(45deg, #667eea, #764ba2);
            border-radius: 10px;
        }

        ::-webkit-scrollbar-thumb:hover {
            background: linear-gradient(45deg, #764ba2, #667eea);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <a href="#" class="logo">Sumit</a>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="particles">
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
            <div class="particle"></div>
        </div>
        <div class="hero-content">
            <h1>Hi, I'm Sumit</h1>
            <p>B.Tech CSE AIML Student at Suresh Gyan Vihar University | Passionate Developer creating AI-powered digital experiences</p>
            <a href="#about" class="cta-button">Discover My Work</a>
        </div>
    </section>

    <!-- About Section -->
    <section id="about" class="about">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="about-image">
                    <div class="profile-img-container">
                        <img src="sumit-photo.jpg" alt="Sumit's Profile Photo" class="profile-img" onError="this.style.display='none'; this.nextElementSibling.style.display='flex';">
                        <div class="profile-img-fallback" style="display: none; width: 300px; height: 300px; border-radius: 50%; background: linear-gradient(45deg, #667eea, #764ba2); color: white; font-size: 4rem; font-weight: bold; border: 5px solid #667eea; box-shadow: 0 20px 40px rgba(102, 126, 234, 0.3); transition: transform 0.3s ease; align-items: center; justify-content: center;">S</div>
                    </div>
                </div>
                <div class="about-text">
                    <p>Welcome to my digital world! I'm Sumit, currently pursuing B.Tech in Computer Science Engineering with specialization in Artificial Intelligence and Machine Learning at Suresh Gyan Vihar University, Jaipur. I'm a dedicated developer with a passion for creating innovative AI-powered solutions and user-friendly applications.</p>
                    <p>As a CSE AIML student at SGVU, I combine traditional software development skills with cutting-edge AI/ML technologies. My academic journey at this prestigious institution has equipped me with strong fundamentals in computer science while specializing in artificial intelligence and machine learning applications.</p>
                    <p>At Suresh Gyan Vihar University, I've gained hands-on experience with various programming languages, AI frameworks, and software development methodologies. When I'm not attending lectures or working on assignments, you can find me exploring new AI frameworks, working on innovative projects, and contributing to the tech community.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="skills">
        <div class="container">
            <h2 class="section-title">My Skills</h2>
            <div class="skills-grid">
                <div class="skill-card">
                    <span class="skill-icon">🤖</span>
                    <h3>AI & Machine Learning</h3>
                    <p>Developing intelligent systems using Python, TensorFlow, PyTorch, scikit-learn, and implementing ML algorithms for real-world problems.</p>
                </div>
                <div class="skill-card">
                    <span class="skill-icon">🎨</span>
                    <h3>Frontend Development</h3>
                    <p>Creating responsive and interactive user interfaces using HTML5, CSS3, JavaScript, and modern frameworks like React and Vue.js.</p>
                </div>
                <div class="skill-card">
                    <span class="skill-icon">⚙️</span>
                    <h3>Backend Development</h3>
                    <p>Building robust server-side applications with Node.js, Python, Django, Flask and databases like MongoDB and PostgreSQL.</p>
                </div>
                <div class="skill-card">
                    <span class="skill-icon">📊</span>
                    <h3>Data Science & Analytics</h3>
                    <p>Analyzing complex datasets using pandas, NumPy, matplotlib, and creating data-driven insights for business decisions.</p>
                </div>
                <div class="skill-card">
                    <span class="skill-icon">🧠</span>
                    <h3>Deep Learning</h3>
                    <p>Implementing neural networks, computer vision, NLP models, and working with frameworks like Keras and PyTorch.</p>
                </div>
                <div class="skill-card">
                    <span class="skill-icon">☁️</span>
                    <h3>Cloud & DevOps</h3>
                    <p>Deploying AI models on AWS, Azure, Google Cloud, and managing ML pipelines with Docker and Kubernetes.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">🤖</div>
                        <div class="project-content">
                            <h3>AI Chatbot System</h3>
                            <p>An intelligent conversational AI built with NLP techniques, featuring sentiment analysis, intent recognition, and context awareness. Implemented using Python and TensorFlow.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">🔍</div>
                        <div class="project-content">
                            <h3>Image Recognition App</h3>
                            <p>A computer vision application using CNN models for object detection and classification. Built with PyTorch and OpenCV for real-time image processing.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">📈</div>
                        <div class="project-content">
                            <h3>Predictive Analytics Platform</h3>
                            <p>A machine learning platform for business forecasting using regression models, time series analysis, and data visualization with Python and scikit-learn.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">🌟</div>
                        <div class="project-content">
                            <h3>Smart Recommendation Engine</h3>
                            <p>An AI-powered recommendation system using collaborative filtering and content-based algorithms. Features real-time recommendations with Flask API.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">🌐</div>
                        <div class="project-content">
                            <h3>Full-Stack AI Web App</h3>
                            <p>A comprehensive web application integrating AI models with modern frontend, featuring React, Node.js, and deployed ML models for intelligent user interactions.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
                <a href="#" class="project-link">
                    <div class="project-card">
                        <div class="project-image">📊</div>
                        <div class="project-content">
                            <h3>Data Science Dashboard</h3>
                            <p>An interactive analytics dashboard with real-time data processing, ML model monitoring, and advanced visualizations using D3.js and Python backend.</p>
                            <span class="view-project">View Project →</span>
                        </div>
                    </div>
                </a>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact">
        <div class="container">
            <h2 class="section-title">Get In Touch</h2>
            <form class="contact-form" action="https://formsubmit.co/sumitstudent2026@gmail.com" method="POST">
                <input type="hidden" name="_captcha" value="false">
                <input type="hidden" name="_subject" value="New Contact from Portfolio Website!">
                <div class="form-group">
                    <label for="name">Your Name</label>
                    <input type="text" id="name" name="name" placeholder="Enter your name" required>
                </div>
                <div class="form-group">
                    <label for="email">Your Email</label>
                    <input type="email" id="email" name="email" placeholder="Enter your email" required>
                </div>
                <div class="form-group">
                    <label for="subject">Subject</label>
                    <input type="text" id="subject" name="subject" placeholder="What's this about?" required>
                </div>
                <div class="form-group">
                    <label for="message">Message</label>
                    <textarea id="message" name="message" rows="5" placeholder="Your message here..." required></textarea>
                </div>
                <button type="submit" class="submit-btn">Send Message</button>
                <div style="text-align: center; margin-top: 1rem;">
                    <p style="color: rgba(255,255,255,0.8);">Or reach me directly:</p>
                    <a href="https://wa.me/918298756451?text=Hi%20Sumit,%20I%20saw%20your%20portfolio!" target="_blank" style="color: #25D366; text-decoration: none; font-weight: bold;">📱 WhatsApp Me</a>
                </div>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <div class="container">
            <p>&copy; 2026 Sumit. All rights reserved.</p>
            <div class="social-links">
                <a href="#" title="GitHub">🔗</a>
                <a href="#" title="LinkedIn">💼</a>
                <a href="#" title="Twitter">🐦</a>
                <a href="#" title="Email">📧</a>
            </div>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
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

        // Navigation background change on scroll
        window.addEventListener('scroll', function() {
            const nav = document.querySelector('nav');
            if (window.scrollY > 100) {
                nav.style.background = 'rgba(255, 255, 255, 0.98)';
                nav.style.boxShadow = '0 2px 20px rgba(0, 0, 0, 0.1)';
            } else {
                nav.style.background = 'rgba(255, 255, 255, 0.95)';
                nav.style.boxShadow = 'none';
            }
        });

        // Form submission handler
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            
            // Show success message
            const btn = document.querySelector('.submit-btn');
            const originalText = btn.textContent;
            btn.textContent = 'Message Sent! ✅';
            btn.style.background = 'linear-gradient(45deg, #00b894, #00a085)';
            
            // Reset after 3 seconds
            setTimeout(() => {
                btn.textContent = originalText;
                btn.style.background = 'linear-gradient(45deg, #ff6b6b, #ee5a24)';
                this.reset();
            }, 3000);
        });

        // Add scroll animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe all sections
        document.querySelectorAll('section').forEach(section => {
            section.style.opacity = '0';
            section.style.transform = 'translateY(50px)';
            section.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
            observer.observe(section);
        });

        // Add typing effect to hero text
        const heroTitle = document.querySelector('.hero h1');
        const text = heroTitle.textContent;
        heroTitle.textContent = '';
        
        let i = 0;
        const typeWriter = () => {
            if (i < text.length) {
                heroTitle.textContent += text.charAt(i);
                i++;
                setTimeout(typeWriter, 100);
            }
        };
        
        setTimeout(typeWriter, 1000);

        // Add parallax effect to particles
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const particles = document.querySelectorAll('.particle');
            
            particles.forEach((particle, index) => {
                const speed = (index + 1) * 0.1;
                particle.style.transform = `translateY(${scrolled * speed}px)`;
            });
        });

        // Add hover effects to skill cards
        document.querySelectorAll('.skill-card').forEach(card => {
            card.addEventListener('mouseenter', function() {
                this.style.transform = 'translateY(-15px) rotateX(10deg)';
                this.style.boxShadow = '0 25px 50px rgba(0, 0, 0, 0.3)';
            });
            
            card.addEventListener('mouseleave', function() {
                this.style.transform = 'translateY(0) rotateX(0deg)';
                this.style.boxShadow = '0 10px 30px rgba(0, 0, 0, 0.2)';
            });
        });

        // Add loading animation
        window.addEventListener('load', () => {
            document.body.style.opacity = '1';
            document.body.style.transform = 'translateY(0)';
        });

        // Initialize page
        document.body.style.opacity = '0';
        document.body.style.transform = 'translateY(20px)';
        document.body.style.transition = 'opacity 0.8s ease, transform 0.8s ease';
    </script>
</body>
</html>
