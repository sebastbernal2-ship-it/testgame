import streamlit as st

st.markdown("""
<canvas id="game" width="800" height="600" style="border:1px solid #000; image-rendering:pixelated;"></canvas>
<script>
// Simple 2D Minecraft-style: grid of blocks, click to place/break hearts
const canvas = document.getElementById('game');
const ctx = canvas.getContext('2d');
const TILE = 32;
const WIDTH = canvas.width / TILE; // 25 tiles
const HEIGHT = canvas.height / TILE; // ~18
let grid = Array(HEIGHT).fill().map(() => Array(WIDTH).fill(0)); // 0=air, 1=grass, 2=heart
let selected = 2; // Start with heart block

// Draw grid
function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  for (let y = 0; y < HEIGHT; y++) {
    for (let x = 0; x < WIDTH; x++) {
      if (grid[y][x] === 1) ctx.fillStyle = '#0f0'; // Grass
      else if (grid[y][x] === 2) ctx.fillStyle = '#f0f'; // Heart (pink)
      else continue;
      ctx.fillRect(x * TILE, y * TILE, TILE, TILE);
    }
  }
}

// Click to place/break
canvas.addEventListener('click', (e) => {
  const rect = canvas.getBoundingClientRect();
  const x = Math.floor((e.clientX - rect.left) / TILE);
  const y = Math.floor((e.clientY - rect.top) / TILE);
  grid[y][x] = grid[y][x] ? 0 : selected;
  draw();
});

// Fill bottom with grass initially
for (let x = 0; x < WIDTH; x++) grid[HEIGHT-3][x] = 1;
draw();
</script>
""", unsafe_allow_html=True)
