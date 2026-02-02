---
layout: default
title: ❤️ A Message for Linh
permalink: /valentine/
---

<style>
  @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Great+Vibes&family=Quicksand:wght@500&display=swap');

  :root {
    --soft-white: #fff0f3;
    --body-color: #f08080;   
    --flap-color: #cd5c5c;   
    --flap-edge: #b34a4a;
  }

  .site-header, .site-footer { display: none !important; }

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, #ffafcc 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Quicksand', sans-serif;
    overflow: hidden;
    perspective: 2500px;
  }

  .envelope-wrapper {
    position: relative;
    width: 484px;
    height: 315px;
    z-index: 1;
    background: var(--body-color);
    box-shadow: 0 40px 80px rgba(0,0,0,0.25);
  }

  .envelope-back {
    position: absolute;
    width: 100%;
    height: 100%;
    background: linear-gradient(145deg, var(--body-color), #e07676);
    z-index: 1;
  }

  /* Improved Flap: Reduced vertical sides for a sharper triangular look */
  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--flap-color);
    /* 5% vertical side creates the sharp triangle transition */
    clip-path: polygon(0 0, 100% 0, 100% 5%, 50% 55%, 0 5%);
    transform-origin: top;
    transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1), z-index 0.1s 0.8s;
    z-index: 5;
    /* Chiseled shading on the flap edge */
    filter: drop-shadow(0 4px 2px rgba(0,0,0,0.2));
    border-bottom: 2px solid var(--flap-edge);
  }

  #open-button {
    position: absolute;
    top: 130px;
    left: 207px;
    width: 70px;
    height: 70px;
    background: radial-gradient(circle at 30% 30%, var(--flap-color), #b24d4d);
    color: white;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    cursor: pointer;
    z-index: 6;
    border: 3px solid #fff;
    font-size: 0.8rem;
    box-shadow: 0 4px 15px rgba(0,0,0,0.3);
    transition: 0.3s;
  }
  #open-button:hover { transform: scale(1.1); background: #d90429; }

  .envelope-label {
    position: absolute;
    bottom: 40px;
    left: 50px;
    font-family: 'Great Vibes', cursive;
    font-size: 3.5rem;
    color: rgba(255, 255, 255, 0.9);
    z-index: 4;
    pointer-events: none;
    transform: rotate(-5deg);
  }

  /* Card Logic */
  #valentine-container {
    position: absolute;
    top: 40px; 
    left: 42px; 
    background: #fff;
    background-image: linear-gradient(rgba(240,240,240,0.5) 1px, transparent 1px);
    background-size: 100% 25px;
    padding: 2rem;
    width: 400px;
    height: 250px;
    text-align: center;
    z-index: 2;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    opacity: 0;
    visibility: hidden;
    /* Transition to handle centering */
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.3s, top 1.2s, left 1.2s;
  }

  .photo-frame {
    width: 120px;
    height: 100px;
    border: 6px solid #fff;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  }

  h1.question-text { 
    font-family: 'Dancing Script', cursive; 
    color: var(--flap-color); 
    font-size: 1.8rem; 
  }

  .options-container { display: flex; gap: 40px; position: relative; width: 100%; justify-content: center; }
  .check-option { display: flex; align-items: center; gap: 10px; cursor: pointer; font-weight: bold; color: #444; }
  .box { width: 26px; height: 26px; border: 2px solid #555; background: white; }
  #no-wrapper { position: absolute; left: 60%; transition: 0.1s ease; }

  /* Animation Stages */
  .open-flap .flap { transform: rotateX(180deg); z-index: 0; }
  .open-flap #valentine-container { opacity: 1; visibility: visible; }
  .open-flap #open-button { display: none; }
  .open-flap .envelope-label { opacity: 0; transition: 0.4s; }

  /* Step 1: Slide Out */
  .pull-out #valentine-container { transform: translateY(-280px); }

  /* Step 2: Exact Screen Centering */
  .centered #valentine-container {
    z-index: 100;
    position: fixed; /* Switch to fixed to ignore envelope container */
    top: 50%;
    left: 50%;
    /* Standard trick for perfect centering: Translate -50% of itself */
    transform: translate(-50%, -50%) scale(1.8);
    box-shadow: 0 60px 140px rgba(0,0,0,0.4);
  }

  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to top, var(--body-color) 60%, #f49797 95%, #ffbaba 100%);
    /* Pocket matches the 5% shoulder height of the flap */
    clip-path: polygon(0 5%, 50% 55%, 100% 5%, 100% 100%, 0 100%);
    z-index: 3;
  }

  #success-section { display: none; }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: -1; }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }
</style>

<div class="envelope-wrapper" id="envelope">
  <div class="envelope-back"></div>
  <div class="flap"></div>
  <div class="envelope-label">To Linh</div>
  <div id="open-button" onclick="startSequence()">Open</div>
  
  <div id="valentine-container">
    <div id="question-section" style="width:100%; height:100%; display:flex; flex-direction:column; justify-content:space-between; align-items:center;">
      <div class="photo-frame">
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" alt="Linh" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <h1 class="question-text">Will you be my Valentine?</h1>
      <div class="options-container">
        <div class="check-option" onclick="celebrate()">
          <div class="box" id="yesBox"></div>
          <span>Yes</span>
        </div>
        <div id="no-wrapper">
          <div class="check-option" onmouseover="moveNo()">
            <div class="box"></div>
            <span>No</span>
          </div>
        </div>
      </div>
    </div>

    <div id="success-section">
        <h1 style="font-family: 'Dancing Script', cursive; color: var(--flap-color); font-size: 2.2rem; margin:0;">YAY! 🥰</h1>
        <p style="font-weight: bold; color: #555; margin: 10px 0;">See you soon, Linh!</p>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="120">
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

  function moveNo() {
    const btn = document.getElementById('no-wrapper');
    const x = Math.random() * 200 - 100;
    const y = Math.random() * 100 - 50;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    const box = document.getElementById('yesBox');
    box.style.background = '#4caf50';
    box.style.borderColor = '#4caf50';
    box.innerHTML = '<span style="color:white; position:absolute; top:-3px; left:4px; font-size:1.2rem;">✓</span>';
    setTimeout(() => {
        document.getElementById('question-section').style.display = 'none';
        document.getElementById('success-section').style.display = 'block';
        for(let i=0; i<60; i++) setTimeout(createHeart, i * 40);
    }, 500);
  }

  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = (Math.random() * 2 + 3) + 's';
    heart.style.fontSize = (Math.random() * 20 + 15) + 'px';
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 5000);
  }
</script>