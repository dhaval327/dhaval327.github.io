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

  .site-header, .site-footer { display: none !important; }

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, var(--primary-pink) 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Segoe UI', sans-serif;
    overflow: hidden;
    perspective: 2000px;
  }

  /* Envelope Assembly */
  .envelope-wrapper {
    position: relative;
    width: 300px;
    height: 200px;
    background-color: var(--envelope-color);
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    z-index: 1;
  }

  /* Layer 4: The Flap */
  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 150px solid transparent;
    border-right: 150px solid transparent;
    border-top: 110px solid var(--envelope-flap);
    transform-origin: top;
    transition: transform 0.8s ease-in-out, z-index 0.1s 0.8s;
    z-index: 5; /* Starts on top */
  }

  /* The Seal */
  #open-button {
    position: absolute;
    top: 75px;
    left: 120px;
    width: 60px;
    height: 60px;
    background: #ff4d6d;
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    cursor: pointer;
    z-index: 6;
    border: 3px solid white;
    box-shadow: 0 4px 10px rgba(0,0,0,0.2);
  }

  /* Layer 2: The Card */
  /* Width reduced to 250px so the 300px flap covers the "corners" completely */
  #valentine-container {
    position: absolute;
    top: 30px; 
    left: 25px; 
    background: white;
    padding: 1.5rem;
    border-radius: 8px;
    width: 250px;
    height: 160px;
    text-align: center;
    z-index: 2; /* Behind pocket (3) and flap (5) */
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    box-shadow: 0 4px 15px rgba(0,0,0,0.1);
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1);
  }

  /* Layer 3: Front Pocket */
  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 300px;
    height: 200px;
    background-color: var(--pocket-color);
    /* Lowered V to hide card perfectly */
    clip-path: polygon(0 40%, 100% 40%, 100% 100%, 0 100%, 0 40%, 50% 85%, 0 40%);
    z-index: 3;
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
  }

  /* ANIMATION PHASES */

  /* 1. Flap rotates and drops its z-index behind the card */
  .open-flap .flap {
    transform: rotateX(180deg);
    z-index: 0; 
  }
  .open-flap #open-button { display: none; }

  /* 2. Pull straight up */
  .pull-out #valentine-container {
    transform: translateY(-150px);
  }

  /* 3. Drop down and center */
  .centered #valentine-container {
    z-index: 10;
    /* TranslateX(0) ensures horizontal center relative to parent */
    transform: translateY(20px) scale(2.2); 
  }

  h1 { color: var(--dark-pink); font-size: 1rem; margin-bottom: 10px; }
  .buttons { position: relative; height: 40px; margin-top: 10px; width: 100%; }
  #yesButton { background: #4caf50; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer; }
  #noButton { 
    background: #f44336; color: white; border: none; padding: 8px 15px; border-radius: 5px; 
    position: absolute; left: 55%; transition: 0.1s;
  }

  #success-section { display: none; }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }
</style>

<div class="envelope-wrapper" id="envelope">
  <div class="flap"></div>
  <div id="open-button" onclick="startSequence()">Open</div>
  
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="80">
      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section">
      <h1>YAY! 🥰</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="100">
    </div>
  </div>

  <div class="envelope-front"></div>
</div>

<script>
  function startSequence() {
    const env = document.getElementById('envelope');
    
    // Phase 1: Flip flap
    env.classList.add('open-flap');
    
    // Phase 2: Pull out (upward)
    setTimeout(() => {
      env.classList.add('pull-out');
      
      // Phase 3: Center (down and forward)
      setTimeout(() => {
        env.classList.remove('pull-out');
        env.classList.add('centered');
      }, 1100);
    }, 800);
  }

  function moveButton() {
    const btn = document.getElementById('noButton');
    const x = Math.random() * 80 - 40;
    const y = Math.random() * 60 - 30;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    for(let i=0; i<30; i++) setTimeout(createHeart, i * 50);
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
    heart.style.fontSize = (Math.random() * 15 + 10) + 'px';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }

  setInterval(createHeart, 1000);
</script>