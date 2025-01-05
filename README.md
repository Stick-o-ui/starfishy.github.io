# starfishy.github.io
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Matrix Rain Intro</title>
  <style>
    /* Fullscreen setup */
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      overflow: hidden;
    }

    canvas {
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      z-index: -1;
    }

    /* Introductory Text Styling */
    .intro {
      position: relative;
      color: #0f0;
      font-family: monospace;
      text-align: center;
      z-index: 1;
      top: 20px;
    }

    h1 {
      font-size: 3rem;
      margin: 0;
      animation: fadeIn 3s ease-in-out;
    }

    p {
      font-size: 1.5rem;
      margin-top: 20px;
      animation: fadeIn 5s ease-in-out;
    }

    /* Animation for text fade-in */
    @keyframes fadeIn {
      0% { opacity: 0; }
      100% { opacity: 1; }
    }
  </style>
</head>
<body>
  <!-- Matrix Rain Background -->
  <canvas id="matrix"></canvas>

  <!-- Intro Text -->
  <div class="intro">
    <h1>Welcome to My World</h1>
    <p>hope you enjoy roblox script </p>
  </div>

  <script>
    const canvas = document.getElementById('matrix');
    const ctx = canvas.getContext('2d');

    // Set canvas dimensions to fit the screen
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const fontSize = 16;
    const columns = Math.floor(canvas.width / fontSize);
    const drops = Array(columns).fill(1);

    function draw() {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.fillStyle = '#0f0';
      ctx.font = `${fontSize}px monospace`;

      for (let i = 0; i < drops.length; i++) {
        const text = String.fromCharCode(Math.random() * 128);
        ctx.fillText(text, i * fontSize, drops[i] * fontSize);

        if (drops[i] * fontSize > canvas.height || Math.random() > 0.975) {
          drops[i] = 0;
        }
        drops[i]++;
      }
    }

    setInterval(draw, 50);

    // Adjust canvas size dynamically on resize
    window.addEventListener('resize', () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
      drops.length = Math.floor(canvas.width / fontSize);
      drops.fill(1);
    });
  </script>
</body>
</html>
