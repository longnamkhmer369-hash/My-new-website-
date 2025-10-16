# My-new-website-
I'm very thankful 🙏😀
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Live Wallpaper Effect</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background: radial-gradient(circle, #00111a, #000);
    }
    canvas {
      display: block;
    }
  </style>
</head>
<body>
  <canvas id="wallpaper"></canvas>
  <script>
    const canvas = document.getElementById('wallpaper');
    const ctx = canvas.getContext('2d');
    let w, h;
    function resize() {
      w = canvas.width = window.innerWidth;
      h = canvas.height = window.innerHeight;
    }
    window.onresize = resize;
    resize();

    const stars = Array(100).fill().map(() => ({
      x: Math.random() * w,
      y: Math.random() * h,
      r: Math.random() * 2,
      dx: (Math.random() - 0.5) * 0.5,
      dy: (Math.random() - 0.5) * 0.5
    }));

    function draw() {
      ctx.fillStyle = "rgba(0, 0, 20, 0.3)";
      ctx.fillRect(0, 0, w, h);
      ctx.fillStyle = "white";
      stars.forEach(s => {
        ctx.beginPath();
        ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
        ctx.fill();
        s.x += s.dx;
        s.y += s.dy;
        if (s.x < 0 || s.x > w) s.dx *= -1;
        if (s.y < 0 || s.y > h) s.dy *= -1;
      });
      requestAnimationFrame(draw);
    }
    draw();
  </script>
</body>
</html>
