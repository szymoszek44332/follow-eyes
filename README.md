<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Follow Eyes</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      background: #f0f0f0;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: 'Segoe UI', sans-serif;
    }

    .head {
      width: 300px;
      height: 300px;
      background: #ffe0bd;
      border-radius: 50%;
      position: relative;
      box-shadow: 0 0 20px rgba(0,0,0,0.2);
    }

    .eye {
      width: 60px;
      height: 60px;
      background: white;
      border-radius: 50%;
      position: absolute;
      top: 80px;
    }

    .eye.left { left: 60px; }
    .eye.right { right: 60px; }

    .pupil {
      width: 20px;
      height: 20px;
      background: black;
      border-radius: 50%;
      position: absolute;
      top: 20px;
      left: 20px;
      transition: 0.05s;
    }

    h1 {
      position: absolute;
      top: 20px;
      width: 100%;
      text-align: center;
      font-size: 24px;
      color: #333;
    }
  </style>
</head>
<body>
  <div class="head">
    <h1>Follow Eyes 👀</h1>
    <div class="eye left"><div class="pupil"></div></div>
    <div class="eye right"><div class="pupil"></div></div>
  </div>

  <script>
    const pupils = document.querySelectorAll('.pupil');

    document.addEventListener('mousemove', (e) => {
      const eyes = document.querySelectorAll('.eye');
      eyes.forEach((eye, index) => {
        const rect = eye.getBoundingClientRect();
        const eyeX = rect.left + rect.width / 2;
        const eyeY = rect.top + rect.height / 2;
        const dx = e.clientX - eyeX;
        const dy = e.clientY - eyeY;
        const angle = Math.atan2(dy, dx);
        const radius = 15;
        const pupil = pupils[index];
        pupil.style.left = `${20 + radius * Math.cos(angle)}px`;
        pupil.style.top = `${20 + radius * Math.sin(angle)}px`;
      });
    });
  </script>
</body>
</html>

