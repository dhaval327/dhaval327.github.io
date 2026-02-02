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

  /* Envelope container: appropriately sized like a real envelope */
  .envelope-wrapper {
    position: relative;
    width: 35vw; /* envelope width */
    height: 22vh; /* envelope height */
    max-width: 500px;
    max-height: 350px;
    background: var(--envelope-color);
    border-bottom-left-radius: 8px;
    border-bottom-right-radius: 8px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
    cursor: pointer;
    overflow: hidden;
  }

  /* Triangular flap that covers the envelope opening */
  .envelope-wrapper::before {
    content: "";
    position: absolute;
    top: 0;
    left: 50%;
    width: 0;
    height: 0;
    border-left: 50% solid transparent;
    border-right: 50% solid transparent;
    border-top: 11vh solid var(--envelope-flap);
    z-index: 3;
    transform-origin: top center;
    transition: transform 0.6s 0.4s;
  }

  /* Opening State: triangular flap rotates upward to reveal card */
  .envelope-wrapper.open::before {
    transform: translateX(-50%) rotateX(-180deg);
    z-index: 0;
  }

  /* The Valentine Card: starts inside the envelope, then extracts and enlarges */
  #valentine-container {
    position: absolute;
    bottom: 8%;
    left: 10%;
    background: rgba(255, 255, 255, 0.95);
    backdrop-filter: blur(5px);
    padding: 1.2rem;
    border-radius: 10px;
    box-shadow: 0 8px 20px rgba(255, 92, 138, 0.2);
    border: 2px solid white;
    width: 80%;
    z-index: 1;
    transition: all 1.2s 0.8s cubic-bezier(0.4, 0.0, 0.2, 1);
    text-align: center;
    box-sizing: border-box;
  }

  /* When the card is extracted and enlarged to center screen */
  #valentine-container.center {
    position: fixed;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%) scale(2.2);
    width: min(55vw, 650px);
    z-index: 6;
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