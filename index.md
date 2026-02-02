---
layout: default
title: ❤️ A Message for Linh
permalink: /valentine/
---

<style>
  :root {
    --primary-pink: #ffafcc;
    --dark-pink: #ff5c8a;
    --soft-white: #fff0f3;
    --envelope-color: #f08080;
    --envelope-flap: #cd5c5c;
    --pocket-color: #f29090;
    --shadow-color: rgba(0, 0, 0, 0.2);
  }

  .site-header, .site-footer { display: none !important; }

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, var(--primary-pink) 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Segoe UI', Tahoma, sans-serif;
    overflow: hidden;
    perspective: 2000px;
  }

  /* Envelope Assembly - Scaled up to 400px width */
  .envelope-wrapper {
    position: relative;
    width: 400px;
    height: 260px;
    background-color: var(--envelope-color);
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
    z-index: 1;
    border: 1px solid rgba(0,0,0,0.1);
    box-shadow: 0 20px 45px var(--shadow-color);
  }

  /* Scaled Flap */
  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 200px solid transparent;
    border-right: 200px solid transparent;
    border-top: 140px solid var(--envelope-flap);
    transform-origin: top;
    transition: transform 0.8s ease-in-out, z-index 0.1s 0.8s;
    z-index: 5;
    filter: drop-shadow(0 5px 5px rgba(0,0,0,0.1));
  }

  /* The Seal */
  #open-button {
    position: absolute;
    top: 100px;
    left: 165px;
    width: 70px;
    height: 70px;
    background: radial-gradient(circle, #ff4d6d 0%, #d90429 100%);
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    cursor: pointer;
    z-index: 6;
    border: 3px solid #fff;
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    transition: 0.3s;
    text-transform: uppercase;
    font-size: 0.8rem;
  }
  #open-button:hover { transform: scale(1.1); }

  /* "To Linh" Text */
  .envelope-label {
    position: absolute;
    bottom: 30px;
    left: 40px;
    font-family: 'Brush Script MT', cursive, sans-serif;
    font-size: 2rem;
    color: rgba(255, 255, 255, 0.9);
    text-shadow: 1px 1px 2px rgba(0,0,0,0.1);
    z-index: 4; /* On top of the front pocket */
    pointer-events: none;
    transform: rotate(-5deg);
  }

  /* The Card */
  #valentine-container {
    position: absolute;
    top: 40px; 
    left: 35px; 
    background: white;
    padding: 2rem;
    border-radius: 10px;
    width: 330px;
    height: 200px;
    text-align: center;
    z-index: 2;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: inset 0 0 15px rgba(0,0,0,0.05), 0 5px 15px rgba(0,0,0,0.1);
    opacity: 0;
    visibility: hidden;
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.3s;
  }

  /* Front Pocket */
  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 400px;
    height: 260px;
    background: linear-gradient(to top, var(--pocket-color) 60%, #f7a3a3 100%);
    clip-path: polygon(0 40%, 100% 40%, 100% 100%, 0 100%, 0 40%, 50% 85%, 0 40%);
    z-index: 3;
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
  }

  /* Sequence Actions */
  .open-flap .flap { transform: rotateX(180deg); z-index: 0; }
  .open-flap #valentine-container { opacity: 1; visibility: visible; }
  .open-flap #open-button { opacity: 0; pointer-events: none; }
  .open-flap .envelope-label { opacity: 0; transition: opacity 0.5s; }

  .pull-out #valentine-container { transform: translateY(-200px); }

  .centered #valentine-container {
    z-index: 10;
    transform: translateY(30px) scale(1.8); /* Adjusted scale for larger card */
    box-shadow: 0 40px 80px rgba(0,0,0,0.3);
  }

  h1 { color: var(--dark-pink); font-size: 1.4rem; margin-bottom: 10px; font-weight: 800; }
  .buttons { position: relative; height: 50px; margin-top: 15px; width: 100%; }
  #yesButton { background: #4caf50; color: white; border: none; padding: 10px 25px; border-radius: 25px; cursor: pointer; font-weight: bold; font-size: 1rem; }
  #noButton { 
    background: #f44336; color: white; border: none; padding: 10px 25px; border-radius: 25px; 
    position: absolute; left: 55%; transition: 0.1s; font-weight: bold; font-size: 1rem;
  }

  #success-section { display: none; }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }
</style>

<div class="envelope-wrapper" id="envelope">
  <div class="flap"></div>
  <div class="envelope-label">To Linh</div>
  <div id="open-button" onclick="startSequence()">Open</div>
  
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="110">
      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section">
      <h1>YAY! 🥰</h1>
      <p style="color:var(--dark-pink); font-size:1rem; font-weight: bold;">See you soon, Linh!</p>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="130">
    </div>
  </div>

  <div class="envelope-front"></div>
</div>

<script>
  function startSequence() {
    const env = document.getElementById('envelope');
    env.classList.add('open-flap');
    setTimeout(() => {
      env.classList.add('pull-out');
      setTimeout(() => {
        env.classList.remove('pull-out');
        env.classList.add('centered');
      }, 1100);
    }, 800);
  }

  function moveButton() {
    const btn = document.getElementById('noButton');
    const x = Math.random() * 140 - 70;
    const y = Math.random() * 80 - 40;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    for(let i=0; i<50; i++) setTimeout(createHeart, i * 50);
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
    heart.style.fontSize = (Math.random() * 20 + 10) + 'px';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }
  setInterval(createHeart, 1200);
</script>