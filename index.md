---
layout: default
title: ❤️ A Special Message
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
  }

  /* Hide Jekyll standard UI */
  .site-header, .site-footer { display: none !important; }

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, var(--primary-pink) 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    overflow: hidden;
    perspective: 1500px;
  }

  /* The main assembly */
  .envelope-wrapper {
    position: relative;
    width: 300px;
    height: 200px;
    background-color: var(--envelope-color);
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    z-index: 1;
  }

  /* The Triangular Flap */
  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 150px solid transparent;
    border-right: 150px solid transparent;
    border-top: 105px solid var(--envelope-flap);
    transform-origin: top;
    transition: transform 0.8s ease-in-out;
    z-index: 4; /* Covers card initially */
  }

  /* The Card: Hidden inside */
  #valentine-container {
    position: absolute;
    top: 5px; 
    left: 15px;
    background: white;
    padding: 1.5rem;
    border-radius: 5px;
    width: 270px;
    height: 180px;
    text-align: center;
    z-index: 2; /* Between flap and back */
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    
    /* Smooth transition for the "Pull Out" */
    transition: transform 1.5s cubic-bezier(0.4, 0, 0.2, 1);
    transform: translateY(0) scale(1);
  }

  /* The Front Pocket (creates the V-shape) */
  .envelope-front {
    position: absolute;
    top: 0;
    left: 0;
    width: 300px;
    height: 200px;
    background-color: var(--pocket-color);
    clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%, 0 0, 50% 50%, 0 0);
    z-index: 3; /* Above the card */
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
  }

  /* ANIMATION CLASSES */

  /* Step 1: Flap flips up */
  .open-flap .flap {
    transform: rotateX(180deg);
    z-index: 0; 
  }

  /* Step 2: Card pulls straight up and stays centered */
  /* We use negative translateY to pull it out, then scale to make it "large" */
  .pull-out #valentine-container {
    transform: translateY(-250px) scale(1.8);
    z-index: 10;
  }

  h1 { color: var(--dark-pink); font-size: 1.2rem; margin: 10px 0; }
  .buttons { position: relative; margin-top: 15px; width: 100%; height: 50px; }
  #yesButton { background: #4caf50; color: white; border: none; padding: 10px 20px; border-radius: 8px; cursor: pointer; }
  #noButton { 
    background: #f44336; color: white; border: none; padding: 10px 20px; border-radius: 8px; 
    position: absolute; left: 55%; transition: 0.15s ease;
  }

  /* Success State */
  #success-section { display: none; }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }
</style>

<div class="envelope-wrapper" id="envelope">
  <div class="flap"></div>
  
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="100">
      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section">
      <h1>YAY! 🥰</h1>
      <p style="color: var(--dark-pink);">See you on the 14th!</p>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="120">
    </div>
  </div>

  <div class="envelope-front"></div>
</div>

<script>
  window.onload = () => {
    const env = document.getElementById('envelope');
    
    // Sequence:
    // 1. Open the flap
    setTimeout(() => {
      env.classList.add('open-flap');
      
      // 2. Pull the card out (1 second later)
      setTimeout(() => {
        env.classList.add('pull-out');
      }, 1000);
    }, 1000);
  };

  function moveButton() {
    const btn = document.getElementById('noButton');
    // Constrained random movement so it stays on the card
    const x = Math.random() * 140 - 70;
    const y = Math.random() * 80 - 40;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    // Success burst
    for(let i=0; i<40; i++) {
        setTimeout(createHeart, i * 50);
    }
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

  // Constant background hearts
  setInterval(createHeart, 800);
</script>