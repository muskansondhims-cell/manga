<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Harman 💕</title>

<style>
  body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(135deg, #fde2e4, #fadadd);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: "Poppins", sans-serif;
    overflow: hidden;
  }

  .card {
    background: #fff;
    padding: 45px;
    border-radius: 30px;
    text-align: center;
    box-shadow: 0 25px 50px rgba(0,0,0,0.15);
    width: 330px;
    position: relative;
    z-index: 2;
  }

  h1 {
    color: #ff5d8f;
    margin-bottom: 25px;
    font-size: 24px;
  }

  button {
    padding: 12px 26px;
    border: none;
    border-radius: 30px;
    font-size: 16px;
    cursor: pointer;
    margin: 10px;
    transition: 0.2s;
  }

  #yes {
    background: #ff5d8f;
    color: white;
  }

  #no {
    background: #ffd6e0;
    color: #ff5d8f;
    position: absolute;
  }

  .heart, .balloon {
    position: absolute;
    animation: float 6s linear infinite;
    opacity: 0.8;
  }

  .heart {
    color: #ff5d8f;
    font-size: 20px;
  }

  .balloon {
    width: 18px;
    height: 25px;
    background: #ffc8dd;
    border-radius: 50%;
  }

  @keyframes float {
    0% { transform: translateY(100vh); }
    100% { transform: translateY(-120vh); }
  }

  canvas {
    position: fixed;
    top: 0;
    left: 0;
    pointer-events: none;
    z-index: 1;
  }
</style>
</head>

<body>

<canvas id="confetti"></canvas>

<div class="card" id="card">
  <h1>Will you be my Valentine, Harman? 💘</h1>
  <button id="yes">Yes 💖</button>
  <button id="no">No 🙈</button>
</div>

<script>
  const noBtn = document.getElementById("no");
  const yesBtn = document.getElementById("yes");
  const card = document.getElementById("card");

  // NO button runs away
  noBtn.addEventListener("mouseover", () => {
    const x = Math.random() * (window.innerWidth - 100);
    const y = Math.random() * (window.innerHeight - 100);
    noBtn.style.left = x + "px";
    noBtn.style.top = y + "px";
  });

  // Hearts & balloons
  function createFloat(type) {
    const el = document.createElement("div");
    el.className = type;
    el.style.left = Math.random() * 100 + "vw";
    el.style.animationDuration = (Math.random() * 3 + 4) + "s";
    el.innerHTML = type === "heart" ? "💗" : "";
    document.body.appendChild(el);
    setTimeout(() => el.remove(), 7000);
  }

  setInterval(() => createFloat("heart"), 400);
  setInterval(() => createFloat("balloon"), 900);

  // Confetti
  const canvas = document.getElementById("confetti");
  const ctx = canvas.getContext("2d");
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;
  let confetti = [];

  function startConfetti() {
    for (let i = 0; i < 200; i++) {
      confetti.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 6 + 3,
        d: Math.random() * 5 + 2,
        color: `hsl(${Math.random()*360},100%,75%)`
      });
    }
    setInterval(drawConfetti, 20);
  }

  function drawConfetti() {
    ctx.clearRect(0,0,canvas.width,canvas.height);
    confetti.forEach(c => {
      ctx.beginPath();
      ctx.arc(c.x, c.y, c.r, 0, Math.PI*2);
      ctx.fillStyle = c.color;
      ctx.fill();
      c.y += c.d;
      if (c.y > canvas.height) c.y = -10;
    });
  }

  // YES click
  yesBtn.addEventListener("click", () => {
    card.innerHTML = `
      <h1>Yayyy 💕<br>I love you, Harman 💖</h1>
      <p>Lover is playing 🎶</p>
    `;
    startConfetti();
    window.open("https://www.youtube.com/watch?v=-BjZmE2gtdo", "_blank");
  });
</script>

</body>
</html># manga
