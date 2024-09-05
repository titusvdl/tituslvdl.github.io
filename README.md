<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Welcome</title>
</head>
<body>
    <h1 id="welcome-message"></h1>

    <script>
        document.getElementById('welcome-message').textContent = 'Welcome!';
    </script>
</body>
</html>

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Catch the Falling Objects Game</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: #f0f0f0;
    }
    canvas {
      display: block;
      background: #d3e0ea;
    }
  </style>
</head>
<body>
  <canvas id="gameCanvas"></canvas>
  <script src="game.js"></script>
</body>
</html>
