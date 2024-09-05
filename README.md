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
  <title>Click the Circle Game</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      font-family: Arial, sans-serif;
    }
    .game-area {
      position: relative;
      width: 100vw;
      height: 100vh;
      background-color: #f0f0f0;
      overflow: hidden;
    }
    .circle {
      position: absolute;
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background-color: #ff6347;
    }
    .score-board {
      position: absolute;
      top: 20px;
      left: 20px;
      font-size: 24px;
    }
  </style>
</head>
<body>
  <div class="game-area">
    <div class="score-board">Score: 0</div>
    <div class="circle"></div>
  </div>

  <script>
    const gameArea = document.querySelector('.game-area');
    const circle = document.querySelector('.circle');
    const scoreBoard = document.querySelector('.score-board');
    let score = 0;

    function getRandomPosition() {
      const x = Math.random() * (gameArea.clientWidth - 50);
      const y = Math.random() * (gameArea.clientHeight - 50);
      return { x, y };
    }

    function moveCircle() {
      const { x, y } = getRandomPosition();
      circle.style.left = `${x}px`;
      circle.style.top = `${y}px`;
    }

    circle.addEventListener('click', () => {
      score += 1;
      scoreBoard.textContent = `Score: ${score}`;
      moveCircle();
    });

    // Initial position
    moveCircle();
  </script>
</body>
</html>
