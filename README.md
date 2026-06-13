<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Draw a Planet</title>

<style>
body {
  margin: 0;
  background: radial-gradient(circle at center, #0b0b1a, black);
  color: white;
  text-align: center;
  font-family: Arial;
}

h1 {
  margin-top: 15px;
  color: #7fd1ff;
  text-shadow: 0 0 10px #7fd1ff;
}

canvas {
  background: rgba(255,255,255,0.05);
  border: 2px solid #7fd1ff;
  border-radius: 10px;
  margin-top: 15px;
}

button {
  margin: 10px;
  padding: 10px 15px;
  border: none;
  border-radius: 8px;
  background: #7fd1ff;
  font-weight: bold;
  cursor: pointer;
}

button:hover {
  transform: scale(1.05);
}

p {
  opacity: 0.8;
}
</style>
</head>

<body>

<h1>🪐 Draw Your Planet</h1>
<p>Click and drag to draw your planet shape</p>

<button onclick="clearCanvas()">Clear</button>
<button onclick="toggleGlow()">Glow ✨</button>

<canvas id="c" width="500" height="500"></canvas>

<script>
const canvas = document.getElementById("c");
const ctx = canvas.getContext("2d");

let drawing = false;
let glow = false;

// mouse controls
canvas.addEventListener("mousedown", () => drawing = true);
canvas.addEventListener("mouseup", () => {
  drawing = false;
  ctx.beginPath();
});
canvas.addEventListener("mousemove", draw);

function draw(e) {
  if (!drawing) return;

  ctx.lineWidth = 4;
  ctx.lineCap = "round";
  ctx.strokeStyle = glow ? "#ffcc66" : "#7fd1ff";

  ctx.lineTo(e.offsetX, e.offsetY);
  ctx.stroke();
  ctx.beginPath();
  ctx.moveTo(e.offsetX, e.offsetY);
}

function clearCanvas() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
}

function toggleGlow() {
  glow = !glow;
}
</script>

</body>
</html>
