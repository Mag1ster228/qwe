#qwe
<!DOCTYPE html>
<html lang="pl">
<head>
  <meta charset="UTF-8" />
  <title>Śledzenie kursora</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      background: #f0f0f0;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .eye {
      width: 100px;
      height: 100px;
      background: #fff;
      border: 4px solid #000;
      border-radius: 50%;
      position: relative;
    }

    .pupil {
      width: 30px;
      height: 30px;
      background: #000;
      border-radius: 50%;
      position: absolute;
      top: 35px;
      left: 35px;
      transition: top 0.05s, left 0.05s;
    }
  </style>
</head>
<body>
  <div class="eye">
    <div class="pupil" id="pupil"></div>
  </div>

  <script>
    const eye = document.querySelector('.eye');
    const pupil = document.getElementById('pupil');

    document.addEventListener('mousemove', (e) => {
      const rect = eye.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;

      const angle = Math.atan2(e.clientY - centerY, e.clientX - centerX);
      const radius = 20; // jak bardzo źrenica może się przesunąć

      const pupilX = Math.cos(angle) * radius;
      const pupilY = Math.sin(angle) * radius;

      pupil.style.left = 35 + pupilX + 'px';
      pupil.style.top = 35 + pupilY + 'px';
    });
  </script>
</body>
</html>
