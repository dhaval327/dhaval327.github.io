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

  /* The Container for the whole interaction */
  .valentine-stage {
    position: relative;
    width: 350px;
    height: 250px;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  /* The Envelope Body */
  .envelope {
    position: relative;
    width: 300px;
    height: 200px;
    background: var(--envelope-color);
    border-bottom-left-radius: 10px;
    border-bottom-right-radius: 10px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.15);
    z-index: 2;
  }

  /* The Flap: A triangle made with borders */
  .flap {
    position: absolute;
    top: 0;
    width: 0;
    height: 0;
    border-left: 150px solid transparent;
    border-right: 150px solid transparent;
    border-top: 100px solid var(--envelope-flap);
    transform-origin: top;
    transition: transform 0.6s ease-in-out;
    z-index: 4; /* Sits above everything initially */
  }

  /* The Front: This hides the card while it's "inside" */
  .envelope-front {
    position: absolute;
    bottom: 0;
    width: 0;
    height: 0;
    border-left: 150px solid transparent;
    border-right: 150px solid transparent;
    border-bottom: 100px solid #f29090; /* Slightly lighter shade for depth */
    z-index: 3;
  }

  /* The Card */
  #valentine-container {
    position: absolute;
    bottom: 10px;
    background: white;
    padding: 1.5rem;
    border-radius: 10px;
    width: 270px;
    height: 180px;
    text-align: center;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    z-index: 1; /* Behind the front pocket and flap */
    transition: all 1s cubic-bezier(0.68, -0.55, 0.27, 1.55);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    overflow: hidden;
  }

  /* Animation States */
  .open .flap {
    transform: rotateX(180deg);
    z-index: 0; /* Move behind card after opening */
  }

  .extracted #valentine-container {
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) scale(1.8);
    width: 400px;
    height: auto;
    z-index: 10;
    box-shadow: 0 20px 50px rgba(0,0,0,0.2);
  }

  h1 { color: var(--dark-pink); font-size: 1.2rem; margin: 10px 0; line-height: 1.2; }
  
  /* Buttons Styling */
  .buttons { margin-top: 15px; position: relative; width: 100%; height: 50px; }
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

<div class="valentine-stage" id="stage">
  <div class="flap"></div>
  <div class="envelope"></div>
  <div class="envelope-front"></div>
  
  <div id="valentine-container">
    <div id="question-section">
      <h1>Will you be my Valentine? ❤️</h1>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="120" alt="Cute gif">
      <div class="buttons">
        <button id="yesButton" onclick="celebrate()">Yes!</button>
        <button id="noButton" onmouseover="moveButton()">No</button>
      </div>
    </div>

    <div id="success-section" style="display: none;">
      <h1>YAY! 🥰</h1>
      <p style="color: var(--dark-pink); margin: 5px 0;">See you on the 14th!</p>
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="120">
    </div>
  </div>
</div>

<script>
  window.onload = () => {
    const stage = document.getElementById('stage');
    
    // Step 1: Open Flap
    setTimeout(() => {
      stage.classList.add('open');
      
      // Step 2: Extract and Center Card
      setTimeout(() => {
        stage.classList.add('extracted');
      }, 1000);
    }, 1000);
  };

  function moveButton() {
    const btn = document.getElementById('noButton');
    const x = Math.random() * 120 - 60;
    const y = Math.random() * 80 - 40;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
    for(let i=0; i<20; i++) {
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
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }

  setInterval(createHeart, 500);
</script>