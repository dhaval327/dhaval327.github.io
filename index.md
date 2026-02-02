---
layout: default
title: A Special Question
permalink: /valentine/
---

<style>
  :root {
    --primary-pink: #ffafcc;
    --dark-pink: #ff5c8a;
    --soft-white: #fff0f3;
    --envelope-color: #f08080;
    --envelope-flap: #cd5c5c;
  }

  /* Theme Overrides */
  .site-header { background-color: var(--soft-white) !important; border-top: 5px solid var(--primary-pink) !important; border-bottom: none !important; }
  .site-title, .site-title:visited { color: var(--dark-pink) !important; font-weight: bold; }
  .site-footer { display: none; }
  .page-header { background-color: var(--primary-pink) !important; background-image: linear-gradient(120deg, #ffafcc, #ffc8dd) !important; color: white !important; }

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, var(--primary-pink) 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    overflow: hidden;
  }

  /* Envelope container: centered and responsive */
  .envelope-wrapper {
    position: relative;
    width: 50vw; /* half of viewport width */
    height: 30vh; /* 30% of viewport height */
    max-width: 900px;
    max-height: 600px;
    background: var(--envelope-color);
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    cursor: pointer;
  }

  /* Flap that fully covers the envelope area when closed */
  .envelope-wrapper::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--envelope-flap);
    z-index: 3;
    transform-origin: top center;
    transition: transform 0.5s 0.3s;
    backface-visibility: hidden;
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
  }

  /* Opening State */
  .envelope-wrapper.open::before {
    transform: rotateX(-180deg);
    z-index: 0;
  }

  /* The Valentine Card inside the envelope; sized with percentages so it scales */
  #valentine-container {
    position: absolute;
    bottom: 5%;
    left: 10%;
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(5px);
    padding: 1.5rem;
    border-radius: 12px;
    box-shadow: 0 10px 30px rgba(255, 92, 138, 0.2);
    border: 2px solid white;
    width: 80%;
    z-index: 1;
    transition: transform 0.8s 0.8s, z-index 0s 1s, width 0.5s 0.8s, left 0s 0s, top 0s 0s;
    text-align: center;
    box-sizing: border-box;
  }

  /* When the envelope is opened we center the card in the viewport via JS */
  #valentine-container.center {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    width: min(60vw, 700px);
    z-index: 6;
  }

  .envelope-wrapper.open #valentine-container {
    /* small lift while flap animation runs; final centering is handled by the .center class */
    transform: translateY(-10%);
    z-index: 5;
  }

  h1 { color: var(--dark-pink); font-size: 1.5rem; margin-bottom: 15px; }

  .buttons { position: relative; height: 60px; margin-top: 20px; }
  
  #yesButton { background-color: #4caf50; color: white; padding: 10px 20px; border: none; border-radius: 8px; cursor: pointer; }
  
  #noButton { 
    background-color: #f44336; color: white; padding: 10px 20px; border: none; border-radius: 8px; 
    position: absolute; left: 55%; transition: 0.2s ease;
  }

  /* Heart Animation */
  @keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg); opacity: 1; }
    100% { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
  }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
</style>

<div class="envelope-wrapper" id="envelope">
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="150" alt="Cute gif">

      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section" style="display: none;">
      <h1>YAY! 🥰</h1>
      <p style="color: var(--dark-pink);">See you on the 14th!</p>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="150">
    </div>
  </div>
</div>

<script>
  // Automatically open envelope after 1 second
  // Automatically open envelope after 1 second, then center the card after flap opens
  window.onload = () => {
    setTimeout(() => {
      const envelope = document.getElementById('envelope');
      const card = document.getElementById('valentine-container');
      envelope.classList.add('open');
      // After flap's transition (delay 0.3s + duration 0.5s = 0.8s) start centering animation
      setTimeout(() => {
        card.classList.add('center');
      }, 800);
    }, 1000);
  };

  function moveButton() {
    const btn = document.getElementById('noButton');
    // Random move within the card boundaries
    const x = Math.random() * 150 - 75;
    const y = Math.random() * 150 - 75;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    // Burst of hearts
    for(let i=0; i<15; i++) {
        setTimeout(createHeart, i * 100);
    }
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = Math.random() * 2 + 3 + 's';
    heart.style.fontSize = Math.random() * 10 + 20 + 'px';
    heart.style.opacity = Math.random();
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }

  setInterval(createHeart, 400);
</script>