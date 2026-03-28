# Under-the-Sea---Game
<!DOCTYPE html>
<html>
<head>
  <title>Simple Side Scroller</title>
</head>
<body>
<canvas id="gameCanvas" width="600" height="400"></canvas>

<script>
const canvas = document.getElementById("gameCanvas");
const ctx = canvas.getContext("2d");

// Player
let player = {
  x: 50,
  y: 200,
  width: 30,
  height: 30,
  speedY: 0
};

// Controls
let keys = {};

document.addEventListener("keydown", (e) => {
  keys[e.key] = true;
});

document.addEventListener("keyup", (e) => {
  keys[e.key] = false;
});

// Game loop
function update() {
  // Move right automatically
  player.x += 2;

  // Up / Down movement
  if (keys["ArrowUp"]) {
    player.y -= 3;
  }
  if (keys["ArrowDown"]) {
    player.y += 3;
  }

  // Keep player in bounds
  if (player.y < 0) player.y = 0;
  if (player.y > canvas.height - player.height) {
    player.y = canvas.height - player.height;
  }
}

// Draw player
function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);

  ctx.fillStyle = "blue";
  ctx.fillRect(player.x, player.y, player.width, player.height);
}

// Main loop
function gameLoop() {
  update();
  draw();
  requestAnimationFrame(gameLoop);
}

gameLoop();
</script>
</body>
</html>
# hi
