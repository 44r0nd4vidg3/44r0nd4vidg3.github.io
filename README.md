<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
<style>
    body {
        background-color: #000;
        color: #00ff00;
        font-family: 'Courier New', monospace;
        margin: 0;
        padding: 20px;
        overflow-x: hidden;
    }
    .container {
        max-width: 800px;
        margin: 0 auto;
        position: relative;
        z-index: 1;
    }
    h1 {
        text-align: center;
        font-size: 3em;
        text-shadow: 0 0 10px #00ff00, 0 0 20px #00ff00, 0 0 30px #00ff00;
        animation: glow 2s ease-in-out infinite alternate, pulse 1s infinite;
    }
    @keyframes glow {
        from { text-shadow: 0 0 10px #00ff00; }
        to { text-shadow: 0 0 20px #00ff00, 0 0 30px #00ff00, 0 0 40px #00ff00; }
    }
    @keyframes pulse {
        0% { transform: scale(1); }
        50% { transform: scale(1.05); }
        100% { transform: scale(1); }
    }
    .typing {
        border-right: 2px solid #00ff00;
        animation: blink 1s infinite;
    }
    @keyframes blink {
        0%, 50% { border-color: transparent; }
        51%, 100% { border-color: #00ff00; }
    }
    .matrix-rain {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        pointer-events: none;
        z-index: 0;
    }
    .section {
        margin: 40px 0;
        padding: 20px;
        border: 1px solid #00ff00;
        background: rgba(0, 255, 0, 0.05);
        animation: fadeIn 1s ease-in, slideIn 1s ease-out;
    }
    @keyframes fadeIn {
        from { opacity: 0; }
        to { opacity: 1; }
    }
    @keyframes slideIn {
        from { transform: translateX(-20px); }
        to { transform: translateX(0); }
    }
    .skill {
        display: inline-block;
        margin: 5px;
        padding: 10px;
        border: 1px solid #00ff00;
        transition: all 0.3s;
        animation: float 3s ease-in-out infinite;
    }
    .skill:nth-child(odd) { animation-delay: 0s; }
    .skill:nth-child(even) { animation-delay: 1.5s; }
    @keyframes float {
        0%, 100% { transform: translateY(0px); }
        50% { transform: translateY(-10px); }
    }
    .skill:hover {
        background: #00ff00;
        color: #000;
        box-shadow: 0 0 10px #00ff00;
        animation: spin 0.5s linear;
    }
    @keyframes spin {
        from { transform: rotate(0deg); }
        to { transform: rotate(360deg); }
    }
    .project {
        margin: 20px 0;
        padding: 15px;
        border-left: 3px solid #00ff00;
        transition: all 0.3s;
        animation: bounceIn 1s ease-out;
    }
    @keyframes bounceIn {
        0% { transform: scale(0.3); opacity: 0; }
        50% { transform: scale(1.05); }
        70% { transform: scale(0.9); }
        100% { transform: scale(1); opacity: 1; }
    }
    .project:hover {
        border-left-color: #ffff00;
        background: rgba(255, 255, 0, 0.1);
        transform: translateX(10px);
    }
    .icon {
        margin-right: 10px;
        animation: rotate 2s linear infinite;
    }
    @keyframes rotate {
        from { transform: rotate(0deg); }
        to { transform: rotate(360deg); }
    }
    .footer {
        text-align: center;
        margin-top: 50px;
        animation: fadeIn 2s ease-in;
    }
    .footer p {
        animation: colorChange 3s infinite;
    }
    @keyframes colorChange {
        0%, 100% { color: #00ff00; }
        33% { color: #ff0000; }
        66% { color: #0000ff; }
    }
</style>

<canvas id="matrix-rain" class="matrix-rain"></canvas>
<div class="container">
    <h1><i class="fas fa-robot icon"></i>44r0nd4vidg3</h1>
    <p id="bio" class="typing">Initializing cybernetic interface...</p>

    <div class="section">
        <h2><i class="fas fa-user icon"></i>About Me</h2>
        <p>I am a cybernetic entity navigating the digital realm. My mission: to code, create, and innovate in the matrix of technology.</p>
    </div>

    <div class="section">
        <h2><i class="fas fa-cogs icon"></i>Skills</h2>
        <div class="skill"><i class="fab fa-js-square"></i> JavaScript</div>
        <div class="skill"><i class="fab fa-python"></i> Python</div>
        <div class="skill"><i class="fab fa-react"></i> React</div>
        <div class="skill"><i class="fab fa-node-js"></i> Node.js</div>
        <div class="skill"><i class="fas fa-brain"></i> AI/ML</div>
        <div class="skill"><i class="fas fa-shield-alt"></i> Cybersecurity</div>
    </div>

    <div class="section">
        <h2><i class="fas fa-project-diagram icon"></i>Projects</h2>
        <div class="project">
            <h3><i class="fas fa-network-wired"></i> Neural Network Simulator</h3>
            <p>A deep learning framework for simulating artificial neural networks.</p>
        </div>
        <div class="project">
            <h3><i class="fas fa-lock"></i> Cyber Defense Toolkit</h3>
            <p>Tools for ethical hacking and cybersecurity analysis.</p>
        </div>
        <div class="project">
            <h3><i class="fas fa-atom"></i> Quantum Computing Playground</h3>
            <p>An interactive environment for experimenting with quantum algorithms.</p>
        </div>
    </div>

    <div class="section">
        <h2><i class="fas fa-envelope icon"></i>Contact</h2>
        <p>Reach me through the matrix: <a href="mailto:contact@44r0nd4vidg3.com" style="color: #00ff00;">contact@44r0nd4vidg3.com</a></p>
        <p>Follow my digital footprint: <a href="https://github.com/44r0nd4vidg3" style="color: #00ff00;"><i class="fab fa-github"></i> GitHub</a> | <a href="https://linkedin.com/in/44r0nd4vidg3" style="color: #00ff00;"><i class="fab fa-linkedin"></i> LinkedIn</a></p>
    </div>

    <div class="footer">
        <p>System Online. Ready for Deployment.</p>
    </div>
</div>

<script>
    // Matrix Rain Effect
    const canvas = document.getElementById('matrix-rain');
    const ctx = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const matrix = "ABCDEFGHIJKLMNOPQRSTUVWXYZ123456789@#$%^&*()*&^%+-/~{[|`]}";
    const matrixArray = matrix.split("");

    const fontSize = 16;
    const columns = canvas.width / fontSize;
    const drops = [];

    for (let x = 0; x < columns; x++) {
        drops[x] = 1;
    }

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.04)";
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        ctx.fillStyle = "#00ff00";
        ctx.font = fontSize + "px monospace";

        for (let i = 0; i < drops.length; i++) {
            const text = matrixArray[Math.floor(Math.random() * matrixArray.length)];
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);

            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }
            drops[i]++;
        }
    }

    setInterval(draw, 35);

    // Typing Effect
    const bioText = "I am 44r0nd4vidg3, a cybernetic developer forging the future of technology.";
    let i = 0;
    const bioElement = document.getElementById('bio');

    function typeWriter() {
        if (i < bioText.length) {
            bioElement.innerHTML = bioText.substring(0, i + 1) + '<span class="typing"></span>';
            i++;
            setTimeout(typeWriter, 100);
        } else {
            bioElement.innerHTML = bioText;
        }
    }

    setTimeout(typeWriter, 2000);
</script>

