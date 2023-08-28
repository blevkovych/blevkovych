<!DOCTYPE html>
<html>

<head>
  <title>DVD Logo Bounce</title>
  <script type="text/javascript">
    let x = 0, y = 0;
    let dx = 4, dy = 4;
    const logoWidth = 80, logoHeight = 40;
    const svgWidth = 500, svgHeight = 500;
    const colors = ["red", "blue", "green", "yellow", "purple", "pink", "orange"];
    let colorIndex = 0;

    function changeColor(logo) {
      colorIndex = (colorIndex + 1) % colors.length;
      logo.style.fill = colors[colorIndex];
    }

    function moveLogo() {
      const logo = document.getElementById('logo');

      x += dx;
      y += dy;

      // Check for corners
      if ((x === 0 || x === svgWidth - logoWidth) && (y === 0 || y === svgHeight - logoHeight)) {
        changeColor(logo);
      }

      // Check for boundaries
      if (x <= 0 || x >= svgWidth - logoWidth) {
        dx = -dx;
      }

      if (y <= 0 || y >= svgHeight - logoHeight) {
        dy = -dy;
      }

      logo.setAttribute('x', x);
      logo.setAttribute('y', y);
    }

    function gameLoop() {
      moveLogo();
      requestAnimationFrame(gameLoop);
    }

    window.addEventListener('load', function () {
      gameLoop();
    });
  </script>
</head>

<body>

  <svg width="500" height="500" style="border: 1px solid;">
    <text id="logo" x="0" y="0" font-family="Verdana" font-size="24" style="fill:blue;">DVD</text>
  </svg>

</body>

</html>
