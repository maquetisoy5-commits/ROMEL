<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Romel B. Maque | Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <style>
        /* RESET & BASE */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            scroll-behavior: smooth;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: #020617;
            color: white;
            line-height: 1.6;
            overflow-x: hidden;
            transition: background 0.4s, color 0.4s;
        }

        /* LOADER SYSTEM */
        #loader {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #020617;
            z-index: 999999;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            transition: opacity 0.8s ease, visibility 0.8s;
        }

        #loader.hide {
            opacity: 0;
            visibility: hidden;
            pointer-events: none;
        }

        .loader-bg {
            position: absolute;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, #0f172a, #020617);
            animation: pulsebg 4s infinite alternate;
        }

        @keyframes pulsebg {
            0% { transform: scale(1); }
            100% { transform: scale(1.1); }
        }

        .loader-box {
            position: relative;
            text-align: center;
            color: white;
            z-index: 2;
            width: 90%;
            max-width: 420px;
        }

        .loader-img {
            width: 120px;
            height: 120px;
            border-radius: 25px;
            object-fit: cover;
            border: 4px solid #38bdf8;
            box-shadow: 0 0 20px #38bdf8, 0 0 50px rgba(56,189,248,.6);
            animation: float 3s ease-in-out infinite;
            margin-bottom: 25px;
        }

        #loader-text {
            font-size: 32px;
            color: #38bdf8;
            margin-bottom: 10px;
            text-shadow: 0 0 15px rgba(56,189,248,.7);
            min-height: 40px;
        }

        .progress-bar {
            width: 100%;
            height: 12px;
            background: rgba(255, 255, 255, .08);
            border-radius: 30px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            width: 0%;
            background: linear-gradient(90deg, #38bdf8, #06b6d4);
            animation: loadbar 4s linear forwards;
            box-shadow: 0 0 15px #38bdf8;
        }

        @keyframes loadbar { 100% { width: 100%; } }

        /* MAIN CONTENT STYLES */
        .container { max-width: 1200px; margin: auto; padding: 0 20px; position: relative; z-index: 10; }
        
        header {
            position: sticky;
            top: 0;
            z-index: 999;
            background: rgba(2, 6, 23, .7);
            backdrop-filter: blur(10px);
            border-bottom: 1px solid rgba(255, 255, 255, .05);
        }

        .navbar { display: flex; justify-content: space-between; align-items: center; padding: 18px 0; }
        .logo { color: #38bdf8; font-size: 22px; font-weight: 700; }
        nav { display: flex; gap: 20px; flex-wrap: wrap; }
        nav a { color: white; text-decoration: none; transition: .3s; font-size: 15px; }
        nav a:hover { color: #38bdf8; }

        #theme-toggle {
            padding: 10px 14px;
            border: none;
            border-radius: 50%;
            cursor: pointer;
            font-size: 18px;
            background: #38bdf8;
            color: #000;
        }

        /* HERO */
        section { padding: 80px 0; }
        .hero { display: grid; grid-template-columns: 1fr 1fr; align-items: center; gap: 40px; }
        .hero h2 { font-size: 52px; margin-bottom: 10px; text-shadow: 0 0 12px rgba(56, 189, 248, .6); }
        .hero h2 span { color: #38bdf8; }
        #typing-text::after { content: "|"; animation: blink .7s infinite; }
        @keyframes blink { 50% { opacity: 0; } }

        .hero img {
            width: 280px; height: 280px; object-fit: cover; border-radius: 25px;
            border: 4px solid #38bdf8; box-shadow: 0 0 20px #38bdf8;
            animation: float 4s ease-in-out infinite; transition: .4s;
        }
        .hero img:hover { transform: scale(1.05) rotate(2deg); }

        @keyframes float { 0%, 100% { transform: translateY(0); } 50% { transform: translateY(-15px); } }

        .btn {
            display: inline-block; padding: 14px 28px; background: #38bdf8; color: #000;
            text-decoration: none; border-radius: 30px; font-weight: 600;
            box-shadow: 0 0 15px rgba(56, 189, 248, .5); transition: .4s;
        }
        .btn:hover { transform: translateY(-5px); box-shadow: 0 0 25px rgba(56, 189, 248, .9); }

        /* CARDS */
        .title { font-size: 32px; margin-bottom: 20px; color: #38bdf8; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 20px; }
        .card {
            background: rgba(255, 255, 255, .05); backdrop-filter: blur(10px);
            padding: 20px; border-radius: 16px; transition: .4s;
            border: 1px solid rgba(255, 255, 255, .08);
        }
        .card:hover { transform: translateY(-10px); box-shadow: 0 0 20px rgba(56, 189, 248, .4); }
        .card img, .card iframe { width: 100%; border-radius: 12px; margin-bottom: 15px; border:none; }

        /* SKILLS */
        .skills { display: flex; flex-wrap: wrap; gap: 12px; margin-top: 20px; }
        .skill { background: #1e293b; padding: 10px 16px; border-radius: 30px; font-size: 14px; }

        /* PARTICLES */
        #particles-js { position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: 1; }

        /* THEME MODES */
        body.light { background: #f8fafc; color: #111827; }
        body.light .card { background: white; color: #111827; box-shadow: 0 8px 20px rgba(0,0,0,.08); }
        body.light header { background: rgba(255, 255, 255, .8); }
        body.light nav a { color: #1e293b; }

        /* FOOTER */
        footer { text-align: center; padding: 30px 0; background: #020617; color: #94a3b8; position: relative; z-index: 10; }

        /* CHATBOT STYLES (Simplified for clarity) */
        #chat-widget { position: fixed; bottom: 20px; right: 20px; width: 300px; z-index: 9999; }
        #chat-header { background: #38bdf8; color: black; padding: 12px; border-radius: 14px 14px 0 0; cursor: pointer; text-align: center; font-weight: 700; }
        #chat-body { display: none; flex-direction: column; background: #1e293b; padding: 10px; border-radius: 0 0 14px 14px; }
        #chat-box { height: 220px; overflow-y: auto; background: #0f172a; padding: 10px; border-radius: 10px; margin-bottom: 10px; font-size: 14px; color: white; }
        #user-input { padding: 10px; border: none; border-radius: 8px; margin-bottom: 8px; width: 100%; }
        .chat-input-area button { width: 100%; padding: 8px; border: none; background: #38bdf8; border-radius: 8px; cursor: pointer; font-weight: bold; }
        .msg { margin-bottom: 10px; padding: 8px; border-radius: 8px; }
        .user { background: #38bdf8; color: black; align-self: flex-end; }
        .bot { background: #334155; color: white; align-self: flex-start; }

        @media(max-width: 768px) {
            .hero { grid-template-columns: 1fr; text-align: center; }
            .hero h2 { font-size: 36px; }
            nav { justify-content: center; }
        }
    </style>
</head>
<body>

<div id="loader">
    <div class="loader-bg"></div>
    <div class="loader-box">
        <img src="https://maquetisoy5-gnvsr.wordpress.com/wp-content/uploads/2025/10/file_0000000067846208ac514dd0883461997751722131553565781.png?w=200" class="loader-img">
        <h1 id="loader-text"></h1>
        <p>Initializing Portfolio System...</p>
        <div class="progress-bar"><div class="progress-fill"></div></div>
    </div>
</div>

<div id="particles-js"></div>

<header>
    <div class="container navbar">
        <div class="logo">ROMEL B. MAQUE</div>
        <nav>
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#skills">Skills</a>
            <a href="#projects">Certificates</a>
            <a href="#tutorials">Tutorials</a>
            <a href="#contact">Contact</a>
        </nav>
        <button id="theme-toggle">🌙</button>
    </div>
</header>

<section id="home">
    <div class="container hero">
        <div>
            <h2>Hello, I'm <span id="typing-text"></span></h2>
            <p>Aspiring Developer | Designer | Student</p>
            <a href="#" class="btn">Download Resume</a>
        </div>
        <div>
            <img src="https://maquetisoy5-gnvsr.wordpress.com/wp-content/uploads/2025/10/file_0000000067846208ac514dd0883461997751722131553565781.png?w=200">
        </div>
    </div>
</section>

<section id="about">
    <div class="container">
        <h2 class="title">About Me</h2>
        <p>I am passionate about web development, UI design, and creating responsive websites. I enjoy coding using HTML, CSS, JavaScript, Java, C++, and PHP. My goal is to become a professional software developer.</p>
    </div>
</section>

<section id="skills">
    <div class="container">
        <h2 class="title">My Skills</h2>
        <div class="skills">
            <div class="skill">HTML</div><div class="skill">CSS</div><div class="skill">JavaScript</div>
            <div class="skill">Java</div><div class="skill">PHP</div><div class="skill">C++</div>
            <div class="skill">UI/UX Design</div><div class="skill">GitHub</div>
        </div>
    </div>
</section>

<section id="projects">
    <div class="container">
        <h2 class="title">Certificates</h2>
        <div class="grid">
            <div class="card">
                <img src="https://maquetisoy5-gnvsr.wordpress.com/wp-content/uploads/2026/04/received_12669272453217607221729466555740244.jpeg?w=1024">
                <h3>CISCO Certificate</h3>
                <p>Networking and IT fundamentals certification.</p>
            </div>
            <div class="card">
                <img src="https://maquetisoy5-gnvsr.wordpress.com/wp-content/uploads/2026/04/img_20260305_160737_9978056948280424168292.jpg?w=1024">
                <h3>Seminar Certificate</h3>
                <p>Technology seminar participation.</p>
            </div>
        </div>
    </div>
</section>

<section id="contact">
    <div class="container">
        <h2 class="title">Contact Me</h2>
        <p>Email: <a href="mailto:maquetisoy5@gmail.com" style="color:#38bdf8">maquetisoy5@gmail.com</a></p>
    </div>
</section>

<footer>© 2026 ROMEL B. MAQUE | Portfolio</footer>

<div id="chat-widget">
    <div id="chat-header" onclick="toggleChat()">Chat with Romel</div>
    <div id="chat-body">
        <div id="chat-box"></div>
        <div class="chat-input-area">
            <input type="text" id="user-input" placeholder="Type a message..." />
            <button onclick="sendMessage()">➤ Send</button>
        </div>
    </div>
</div>

<script src="https://cdn.jsdelivr.net/particles.js/2.0.0/particles.min.js"></script>
<script>
    /* 1. LOADER LOGIC */
    const loadText = "ROMEL PORTFOLIO";
    let loaderIndex = 0;
    function typeLoader() {
        if (loaderIndex < loadText.length) {
            document.getElementById("loader-text").innerHTML += loadText.charAt(loaderIndex);
            loaderIndex++;
            setTimeout(typeLoader, 100);
        }
    }
    typeLoader();

    function hideLoader() {
        const loader = document.getElementById("loader");
        loader.classList.add("hide");
        document.body.style.overflow = "auto";
    }
    window.addEventListener("load", () => { setTimeout(hideLoader, 4200); });
    setTimeout(hideLoader, 7000); // Fail-safe

    /* 2. HERO TYPEWRITER */
    const heroText = "ROMEL B. MAQUE";
    let heroIndex = 0;
    function typeHero() {
        if (heroIndex < heroText.length) {
            document.getElementById("typing-text").innerHTML += heroText.charAt(heroIndex);
            heroIndex++;
            setTimeout(typeHero, 120);
        }
    }
    setTimeout(typeHero, 4500); // Start after loader

    /* 3. THEME & PARTICLES */
    const themeBtn = document.getElementById("theme-toggle");
    function loadParts(theme) {
        particlesJS("particles-js", {
            particles: {
                number: { value: 80 },
                color: { value: theme === "dark" ? "#38bdf8" : "#f59e0b" },
                shape: { type: "circle" },
                opacity: { value: 0.5 },
                size: { value: 3 },
                line_linked: { enable: true, distance: 150, color: theme === "dark" ? "#38bdf8" : "#f59e0b", opacity: 0.4 },
                move: { enable: true, speed: 2 }
            }
        });
    }

    themeBtn.onclick = () => {
        const isDark = document.body.classList.toggle("light");
        const newTheme = isDark ? "light" : "dark";
        themeBtn.innerHTML = isDark ? "☀️" : "🌙";
        localStorage.setItem("theme", newTheme);
        loadParts(newTheme);
    };

    const savedTheme = localStorage.getItem("theme") || "dark";
    if(savedTheme === "light") {
        document.body.classList.add("light");
        themeBtn.innerHTML = "☀️";
    }
    loadParts(savedTheme);

    /* 4. CHATBOT */
    function toggleChat() {
        const chatBody = document.getElementById("chat-body");
        chatBody.style.display = chatBody.style.display === "flex" ? "none" : "flex";
    }

    function sendMessage() {
        const input = document.getElementById("user-input");
        const box = document.getElementById("chat-box");
        if(!input.value.trim()) return;

        box.innerHTML += `<div class="msg user">${input.value}</div>`;
        const val = input.value.toLowerCase();
        input.value = "";
        
        setTimeout(() => {
            let reply = "Feel free to look around!";
            if(val.includes("skills")) reply = "I know HTML, CSS, JS, Java, and PHP!";
            if(val.includes("hello")) reply = "Hi there! How can I help you today?";
            box.innerHTML += `<div class="msg bot">${reply}</div>`;
            box.scrollTop = box.scrollHeight;
        }, 1000);
    }
</script>

</body>
</html>
