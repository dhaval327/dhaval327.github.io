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
    --pocket-color: #f29090;
  }

  /* Theme Overrides */
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
    perspective: 1200px;
  }

  /* Container for the whole envelope assembly */
  .envelope-container {
    position: relative;
    width: 300px;
    height: 200px;
    transform-style: preserve-3d;
  }

  /* The Flap */
  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 150px solid transparent;
    border-right: 150px solid transparent;
    border-top: 105px solid var(--envelope-flap); /* Slightly larger to cover edges */
    transform-origin: top;
    transition: transform 0.7s ease-in-out;
    z-index: 4; /* Stays on top until opened */
  }

  /* Front Layer (The Pocket) */
  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 300px;
    height: 200px;
    background-color: var(--pocket-color);
    clip-path: polygon(0 0, 100% 0, 100% 100%, 0 100%, 0 0, 50% 50%, 0 0);
    /* The clip-path creates a 'V' shape opening at the top */
    z-index: 3;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
  }

  /* Back Layer */
  .envelope-back {
    position: absolute;
    top: 0;
    left: 0;
    width: 300px;
    height: 200px;
    background: var(--envelope-color);
    border-radius: 10px;
    z-index: 1;
  }

  /* The Card */
  #valentine-container {
    position: absolute;
    top: 5px; /* Sits just inside the top edge */
    left: 15px;
    background: white;
    padding: 1.5rem;
    border-radius: 5px;
    width: 270px;
    height: 180px;
    text-align: center;
    z-index: 2; /* Sandwiched between back and front */
    transition: all 1.2s cubic-bezier(0.4, 0, 0.2, 1);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-sizing: border-box;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
  }

  /* ANIMATION STATES */
  
  /* 1. Flap opens */
  .open .flap {
    transform: rotateX(180deg);
    z-index: 0; /* Move behind everything once open */
  }

  /* 2. Card pulls out and centers */
  .extracted #valentine-container {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.8);
    width: 400px;
    height: auto;
    z-index: 10;
    box-shadow: 0 20px 50px rgba(0,0,0,0.3);
  }

  h1 { color: var(--dark-pink); font-size: 1.3rem; margin: 5px 0; }
  
  .buttons { margin-top: 15px; position: relative; width: 100%; height: 50px; }
  
  #yesButton { background-color: #4caf50; color: white; padding: 10px 20px; border: none; border-radius: 8px; cursor: pointer; }
  
  #noButton { 
    background-color: #f44336; color: white; padding: 10px 20px; border: none; border-radius: 8px; 
    position: absolute; left: 55%; transition: 0.1s ease;
  }

  /* Background Hearts */
  @keyframes floatUp {
    to { transform: translateY(-110vh) rotate(360deg); opacity: 0; }
  }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
</style>

<div class="envelope-container" id="envelope-wrapper">
  <div class="flap"></div>
  <div class="envelope-back"></div>
  
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="100" alt="Cute gif">
      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section" style="display: none;">
      <h1>YAY! 🥰</h1>
      <p style="color: var(--dark-pink);">Can't wait for Feb 14th!</p>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="120">
    </div>
  </div>

  <div class="envelope-front"></div>
</div>

<script>
  window.onload = () => {
    const envelope = document.getElementById('envelope-wrapper');
    
    // Start Sequence
    setTimeout(() => {
      // Step 1: Open the flap
      envelope.classList.add('open');
      
      // Step 2: Extract the card after flap is clear
      setTimeout(() => {
        envelope.classList.add('extracted');
      }, 1000);
    }, 1200);
  };

  function moveButton() {
    const btn = document.getElementById('noButton');
    const x = Math.random() * 200 - 100;
    const y = Math.random() * 100 - 50;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    // Success heart burst
    for(let i=0; i<30; i++) {
        setTimeout(createHeart, i * 60);
    }
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
    heart.style.fontSize = (Math.random() * 15 + 15) + 'px';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }

  setInterval(createHeart, 700);
</script>