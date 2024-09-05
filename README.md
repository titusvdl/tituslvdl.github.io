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

const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let player = {
  x: canvas.width / 2 - 50,
  y: canvas.height - 100,
  width: 100,
  height: 20,
  dx: 0,
  speed: 7
};

let objects = [];
let score = 0;

function createObject() {
  let object = {
    x: Math.random() * (canvas.width - 20),
    y: 0,
    width: 20,
    height: 20,
    dy: 2 + Math.random() * 3
  };
  objects.push(object);
}

function drawPlayer() {
  ctx.fillStyle = '#ff6347';
  ctx.fillRect(player.x, player.y, player.width, player.height);
}

function drawObject(object) {
  ctx.fillStyle = '#008080';
  ctx.fillRect(object.x, object.y, object.width, object.height);
}

function movePlayer() {
  player.x += player.dx;
  if (player.x < 0) player.x = 0;
  if (player.x + player.width > canvas.width) player.x = canvas.width - player.width;
}

function moveObjects() {
  objects.forEach((object, index) => {
    object.y += object.dy;
    
    // Remove object if it falls out of the screen
    if (object.y > canvas.height) {
      objects.splice(index, 1);
    }
    
    // Check collision with player
    if (
      object.x < player.x + player.width &&
      object.x + object.width > player.x &&
      object.y < player.y + player.height &&
      object.y + object.height > player.y
    ) {
      objects.splice(index, 1);
      score += 1;
    }
  });
}

function update() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  drawPlayer();
  objects.forEach(drawObject);
  
  movePlayer();
  moveObjects();
  
  // Spawn new object
  if (Math.random() < 0.02) {
    createObject();
  }
  
  // Display score
  ctx.font = '20px Arial';
  ctx.fillStyle = '#333';
  ctx.fillText(`Score: ${score}`, 20, 30);
  
  requestAnimationFrame(update);
}

document.addEventListener('keydown', (e) => {
  if (e.key === 'ArrowRight') {
    player.dx = player.speed;
  } else if (e.key === 'ArrowLeft') {
    player.dx = -player.speed;
  }
});

document.addEventListener('keyup', () => {
  player.dx = 0;
});

// Start the game
update();
