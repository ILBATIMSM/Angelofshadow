# Angelsofshadow
Сайт клана!
<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Angels of Shadow</title>
  <!-- Google Fonts & Font Awesome -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@400;700;900&display=swap" rel="stylesheet" />
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css" />
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: #0a0a0f;
      color: #d9d2e0;
      font-family: 'Cinzel', serif;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      overflow-x: hidden;
      position: relative;
    }

    /* Canvas для частиц */
    #particles-canvas {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      z-index: 0;
      pointer-events: none;
    }

    /* Основной контент */
    .content {
      position: relative;
      z-index: 1;
      max-width: 1200px;
      width: 90%;
      padding: 2rem 0;
      text-align: center;
      animation: fadeIn 2s ease-out;
    }

    @keyframes fadeIn {
      0% { opacity: 0; transform: translateY(30px); }
      100% { opacity: 1; transform: translateY(0); }
    }

    /* Заголовок */
    .main-title {
      font-size: clamp(3.5rem, 15vw, 7rem);
      font-weight: 900;
      letter-spacing: 0.15em;
      text-transform: uppercase;
      color: #f0eaff;
      text-shadow: 
        0 0 15px rgba(180, 150, 255, 0.7),
        0 0 40px rgba(120, 80, 200, 0.5),
        0 0 80px rgba(80, 40, 160, 0.3);
      transition: text-shadow 0.3s ease;
      margin-bottom: 0.5rem;
      line-height: 1.1;
    }

    .main-title:hover {
      text-shadow: 
        0 0 25px #b8a0ff,
        0 0 60px #7a4dff,
        0 0 120px #4a1a9e;
    }

    .sub-title {
      font-size: clamp(1rem, 3vw, 1.6rem);
      letter-spacing: 0.4em;
      color: #a89bb5;
      text-transform: uppercase;
      margin-bottom: 3rem;
      border-bottom: 1px solid rgba(180, 150, 255, 0.2);
      display: inline-block;
      padding-bottom: 0.75rem;
      backdrop-filter: blur(2px);
    }

    /* Сетка карточек */
    .cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
      gap: 2rem;
      margin: 3rem 0 4rem;
    }

    .card {
      background: rgba(20, 18, 30, 0.7);
      backdrop-filter: blur(6px);
      border: 1px solid rgba(180, 150, 255, 0.15);
      border-radius: 20px;
      padding: 2rem 1.5rem;
      transition: all 0.3s ease;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.6);
      cursor: default;
    }

    .card:hover {
      transform: translateY(-10px) scale(1.02);
      border-color: #b294ff;
      box-shadow: 0 20px 50px rgba(100, 70, 200, 0.4);
      background: rgba(30, 24, 50, 0.8);
    }

    .card i {
      font-size: 3.5rem;
      color: #b8a0ff;
      text-shadow: 0 0 20px rgba(150, 120, 255, 0.5);
      margin-bottom: 1.2rem;
      display: block;
      transition: transform 0.3s;
    }

    .card:hover i {
      transform: scale(1.1) rotate(4deg);
    }

    .card h3 {
      font-size: 1.4rem;
      font-weight: 700;
      letter-spacing: 0.1em;
      margin-bottom: 0.75rem;
      color: #e6ddf5;
    }

    .card p {
      font-family: 'Segoe UI', Roboto, sans-serif;
      font-size: 0.95rem;
      line-height: 1.6;
      color: #b8aec9;
      letter-spacing: 0.02em;
    }

    /* Секция с цитатой */
    .quote {
      font-size: clamp(1rem, 2.5vw, 1.5rem);
      font-style: italic;
      border-left: 3px solid #7a4dff;
      padding: 1.5rem 2rem;
      background: rgba(10, 8, 20, 0.6);
      border-radius: 40px 10px 40px 10px;
      backdrop-filter: blur(4px);
      max-width: 700px;
      margin: 0 auto 3rem;
      color: #cfc4e0;
      box-shadow: 0 0 40px rgba(70, 40, 140, 0.2);
      transition: all 0.3s;
    }

    .quote:hover {
      border-left-color: #b294ff;
      box-shadow: 0 0 60px rgba(120, 80, 200, 0.3);
    }

    .quote i {
      color: #b294ff;
      margin: 0 0.4rem;
    }

    /* Кнопка */
    .btn {
      display: inline-block;
      background: transparent;
      border: 2px solid #b294ff;
      color: #f0eaff;
      padding: 1rem 3rem;
      font-family: 'Cinzel', serif;
      font-weight: 700;
      font-size: 1.1rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      border-radius: 50px;
      transition: all 0.4s ease;
      cursor: pointer;
      backdrop-filter: blur(4px);
      background: rgba(20, 18, 30, 0.4);
      text-decoration: none;
      margin: 1rem 0 2rem;
    }

    .btn:hover {
      background: #b294ff;
      color: #0a0a0f;
      box-shadow: 0 0 50px rgba(150, 120, 255, 0.6);
      transform: scale(1.05);
      border-color: #b294ff;
    }

    /* Футер */
    .footer {
      margin-top: 3rem;
      font-size: 0.8rem;
      color: #6a5f7a;
      letter-spacing: 0.2em;
      border-top: 1px solid rgba(180, 150, 255, 0.1);
      padding-top: 2rem;
      width: 100%;
      display: flex;
      justify-content: center;
      gap: 2.5rem;
      flex-wrap: wrap;
    }

    .footer a {
      color: #8a7d9e;
      transition: color 0.3s;
      text-decoration: none;
    }

    .footer a:hover {
      color: #b8a0ff;
    }

    .footer i {
      margin-right: 0.5rem;
    }

    /* Адаптив */
    @media (max-width: 600px) {
      .main-title {
        letter-spacing: 0.08em;
      }
      .card {
        padding: 1.5rem 1rem;
      }
      .quote {
        padding: 1rem 1.2rem;
      }
    }
  </style>
</head>
<body>

  <!-- Холст для частиц -->
  <canvas id="particles-canvas"></canvas>

  <!-- Основной блок -->
  <div class="content">

    <h1 class="main-title">Angels of Shadow</h1>
    <div class="sub-title"><i class="fas fa-feather-alt" style="margin-right: 12px;"></i>Guardians of the Veil<i class="fas fa-feather-alt" style="margin-left: 12px;"></i></div>

    <!-- Карточки -->
    <div class="cards">
      <div class="card">
        <i class="fas fa-wings"></i>
        <h3>Wings of Night</h3>
        <p>Мы несём тень, чтобы защитить свет. Наши крылья — это барьер между мирами.</p>
      </div>
      <div class="card">
        <i class="fas fa-skull"></i>
        <h3>Shadow Sigil</h3>
        <p>Древние печати, вырезанные в самой тьме. Каждая — ключ к забвению.</p>
      </div>
      <div class="card">
        <i class="fas fa-moon"></i>
        <h3>Eclipse Pact</h3>
        <p>Мы заключили союз с луной и тенью. Наша сила — в тишине полуночи.</p>
      </div>
    </div>

    <!-- Цитата -->
    <div class="quote">
      <i class="fas fa-quote-left"></i> 
      In darkness we rise, in silence we strike. 
      <i class="fas fa-quote-right"></i>
    </div>

    <!-- Кнопка -->
    <a href="#" class="btn"><i class="fas fa-ghost" style="margin-right: 12px;"></i>Enter the Void</a>

    <!-- Футер -->
    <div class="footer">
      <span><i class="fas fa-crown"></i> Order of the Eclipse</span>
      <a href="#"><i class="fab fa-twitter"></i> Twitter</a>
      <a href="#"><i class="fab fa-discord"></i> Discord</a>
      <a href="#"><i class="fas fa-envelope"></i> Contact</a>
      <span>© 2026 · Angels of Shadow</span>
    </div>

  </div>

  <!-- JavaScript для частиц -->
  <script>
    (function() {
      const canvas = document.getElementById('particles-canvas');
      const ctx = canvas.getContext('2d');
      let width, height;
      let particles = [];
      const COUNT = 70;

      function resize() {
        width = canvas.width = window.innerWidth;
        height = canvas.height = window.innerHeight;
      }
      window.addEventListener('resize', resize);
      resize();

      class Particle {
        constructor() {
          this.reset();
        }

        reset() {
          this.x = Math.random() * width;
          this.y = Math.random() * height;
          this.size = Math.random() * 3 + 1.2;
          this.speedX = (Math.random() - 0.5) * 0.5;
          this.speedY = (Math.random() - 0.5) * 0.5;
          this.opacity = Math.random() * 0.6 + 0.2;
          this.color = `rgba(180, 150, 255, ${this.opacity})`;
        }

        update() {
          this.x += this.speedX;
          this.y += this.speedY;

          // отражение от краёв
          if (this.x < 0 || this.x > width) this.speedX *= -1;
          if (this.y < 0 || this.y > height) this.speedY *= -1;

          // мягкое притяжение к центру (эффект "туманности")
          const cx = width / 2;
          const cy = height / 2;
          const dx = this.x - cx;
          const dy = this.y - cy;
          const dist = Math.sqrt(dx*dx + dy*dy);
          if (dist > 300) {
            const force = 0.001;
            this.speedX -= dx * force;
            this.speedY -= dy * force;
          }
          // ограничение скорости
          const maxSpeed = 0.7;
          const sp = Math.sqrt(this.speedX*this.speedX + this.speedY*this.speedY);
          if (sp > maxSpeed) {
            this.speedX = (this.speedX / sp) * maxSpeed;
            this.speedY = (this.speedY / sp) * maxSpeed;
          }
        }

        draw() {
          ctx.beginPath();
          ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
          ctx.fillStyle = this.color;
          ctx.shadowColor = '#b294ff';
          ctx.shadowBlur = 15;
          ctx.fill();
          ctx.shadowBlur = 0; // сброс для других
        }
      }

      // инициализация
      for (let i = 0; i < COUNT; i++) {
        particles.push(new Particle());
      }

      // линии между близкими частицами
      function drawLines() {
        for (let i = 0; i < particles.length; i++) {
          for (let j = i + 1; j < particles.length; j++) {
            const dx = particles[i].x - particles[j].x;
            const dy = particles[i].y - particles[j].y;
            const dist = Math.sqrt(dx*dx + dy*dy);
            if (dist < 130) {
              const opacity = (1 - dist / 130) * 0.25;
              ctx.beginPath();
              ctx.moveTo(particles[i].x, particles[i].y);
              ctx.lineTo(particles[j].x, particles[j].y);
              ctx.strokeStyle = `rgba(150, 120, 220, ${opacity})`;
              ctx.lineWidth = 1.2;
              ctx.shadowBlur = 8;
              ctx.shadowColor = '#6a4a9e';
              ctx.stroke();
              ctx.shadowBlur = 0;
            }
          }
        }
      }

      function animate() {
        ctx.clearRect(0, 0, width, height);

        for (const p of particles) {
          p.update();
          p.draw();
        }
        drawLines();

        requestAnimationFrame(animate);
      }

      animate();

      // пересоздаём частицы при ресайзе (чтобы не разбегались)
      window.addEventListener('resize', () => {
        resize();
        // переместим существующие частицы в новые границы
        for (const p of particles) {
          p.x = Math.min(p.x, width);
          p.y = Math.min(p.y, height);
        }
      });

    })();
  </script>

</body>
</html>
