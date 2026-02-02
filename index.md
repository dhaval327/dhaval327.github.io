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
    --wax-seal: #9e1b32; 
    --tape-color: rgba(255, 175, 204, 0.5); /* Washi tape color */
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

  #overlay {
    position: fixed;
    top: 0; left: 0; width: 100%; height: 100%;
    background: rgba(0,0,0,0);
    transition: background 1s ease;
    z-index: 0;
    pointer-events: none;
  }
  .centered-view #overlay { background: rgba(0,0,0,0.4); }

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

  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: var(--flap-color);
    clip-path: polygon(0 0, 100% 0, 100% 5%, 50% 55%, 0 5%);
    transform-origin: top;
    transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1), z-index 0.1s 0.8s;
    z-index: 5;
    filter: drop-shadow(0 4px 2px rgba(0,0,0,0.2));
    border-bottom: 2px solid var(--flap-edge);
  }

  /* Periodic Wiggle Animation */
  @keyframes periodicWiggle {
    0%, 85% { transform: scale(1) rotate(0deg); }
    87% { transform: scale(1.05) rotate(3deg); }
    89% { transform: scale(1.05) rotate(-3deg); }
    91% { transform: scale(1.05) rotate(3deg); }
    93% { transform: scale(1.05) rotate(-3deg); }
    95% { transform: scale(1) rotate(0deg); }
  }

  #open-button {
    position: absolute;
    top: 130px;
    left: 207px;
    width: 70px;
    height: 70px;
    background: radial-gradient(circle at 30% 30%, var(--wax-seal), #7a1224);
    color: #ffd700;
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: bold;
    cursor: pointer;
    z-index: 6;
    border: 2px solid #8a1428;
    box-shadow: 0 4px 10px rgba(0,0,0,0.4), inset 0 0 10px rgba(0,0,0,0.2);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    animation: periodicWiggle 4s infinite ease-in-out;
    transition: all 0.3s ease;
  }

  #open-button:hover {
    animation: wiggle 0.3s infinite; /* Keeps your original hover wiggle */
    box-shadow: 0 8px 20px rgba(0,0,0,0.5);
  }

  @keyframes wiggle {
    0% { transform: scale(1.1) rotate(0deg); }
    25% { transform: scale(1.1) rotate(3deg); }
    75% { transform: scale(1.1) rotate(-3deg); }
    100% { transform: scale(1.1) rotate(0deg); }
  }

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

  #valentine-container {
    position: absolute;
    top: 40px; 
    left: 42px; 
    background: #fffcf5; 
    background-image: url("https://www.transparenttextures.com/patterns/felt.png"),
                      linear-gradient(rgba(240,240,240,0.3) 1px, transparent 1px);
    background-size: auto, 100% 25px;
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
    border-radius: 2px;
    border: 1px solid #e0ddd5;
    opacity: 0;
    visibility: hidden;
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.5s;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  }

  /* Washi Tape Logic */
  .photo-frame {
    position: relative;
    width: 120px;
    height: 100px;
    border: 6px solid #fff;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    background: white;
  }

  .photo-frame::before, .photo-frame::after {
    content: '';
    position: absolute;
    width: 40px;
    height: 15px;
    background: var(--tape-color);
    z-index: 10;
  }
  .photo-frame::before { top: -8px; left: -15px; transform: rotate(-35deg); }
  .photo-frame::after { top: -8px; right: -15px; transform: rotate(35deg); }

  h1.question-text { 
    font-family: 'Dancing Script', cursive; 
    color: var(--wax-seal); 
    font-size: 1.8rem;
    margin: 5px 0;
  }

  .options-container { 
    display: flex; 
    gap: 60px; 
    position: relative; 
    width: 100%; 
    justify-content: center; 
    align-items: center;
    margin-bottom: 10px;
  }

  .check-option { 
    display: flex; 
    align-items: center; 
    gap: 12px; 
    cursor: pointer; 
    font-weight: bold; 
    color: #444;
    font-size: 1.1rem;
  }

  .box { 
    width: 28px; 
    height: 28px; 
    border: 2.5px solid #555; 
    background: white; 
    position: relative;
    box-shadow: inset 0 2px 4px rgba(0,0,0,0.1);
  }

  #no-wrapper { 
    display: inline-block;
    transition: 0.1s ease; 
  }

  .open-flap .flap { transform: rotateX(180deg); z-index: 0; }
  .open-flap #valentine-container { opacity: 1; visibility: visible; }
  .open-flap #open-button { opacity: 0; pointer-events: none; }
  .open-flap .envelope-label { opacity: 0; transition: 0.4s; }

  .pull-out #valentine-container { transform: translateY(-280px); }

  .centered #valentine-container {
    z-index: 100;
    transform: translateY(-80px) scale(1.9);
    box-shadow: 5px 30px 100px rgba(0,0,0,0.3), inset 0 0 100px rgba(255,255,255,0.2);
  }

  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(to top, var(--body-color) 60%, #f49797 95%, #ffbaba 100%);
    clip-path: polygon(0 5%, 50% 55%, 100% 5%, 100% 100%, 0 100%);
    z-index: 3;
  }

  #success-section { display: none; }
  .heart-effect { position: fixed; bottom: -20px; animation: floatUp linear forwards; z-index: 101; }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }
</style>

<div id="overlay"></div>

<div class="envelope-wrapper" id="envelope">
  <div class="envelope-back"></div>
  <div class="flap"></div>
  <div class="envelope-label">To Linh</div>
  <div id="open-button" onclick="startSequence()">Open</div>
  
  <div id="valentine-container">
    <div id="question-section" style="width:100%; height:100%; display:flex; flex-direction:column; justify-content:space-between; align-items:center;">
      <div class="photo-frame">
        <img src="image.png" alt="Linh" style="width:100%; height:100%; object-fit:cover;">
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
        <h1 style="font-family: 'Dancing Script', cursive; color: var(--wax-seal); font-size: 2.2rem; margin:0;">YAY! 🥰</h1>
        <p style="font-weight: bold; color: #555; margin: 10px 0;">I love you my pookie bear soulmate!! Always and forever!</p>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="120">
    </div>
  </div>

  <div class="envelope-front"></div>
</div>

<script>
  // Restore ambient background hearts
  setInterval(createHeart, 800);

  function startSequence() {
    const env = document.getElementById('envelope');
    const body = document.body;
    env.classList.add('open-flap');
    setTimeout(() => {
      env.classList.add('pull-out');
      setTimeout(() => {
        env.classList.remove('pull-out');
        env.classList.add('centered');
        body.classList.add('centered-view');
      }, 1000);
    }, 800);
  }

  function moveNo() {
    const btn = document.getElementById('no-wrapper');
    const x = Math.random() * 160 - 80;
    const y = Math.random() * 80 - 40;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    const box = document.getElementById('yesBox');
    box.style.background = '#4caf50';
    box.style.borderColor = '#4caf50';
    box.innerHTML = '<span style="color:white; position:absolute; top:-3px; left:4px; font-size:1.2rem;">✓</span>';
    
    // Confetti burst for the Yes button
    for(let i=0; i<50; i++) {
        setTimeout(() => {
            const h = document.createElement('div');
            h.classList.add('heart-effect');
            h.innerHTML = ['❤️', '✨', '💖', '🌸'][Math.floor(Math.random() * 4)];
            h.style.left = (40 + Math.random() * 20) + 'vw';
            h.style.bottom = '50vh';
            h.style.fontSize = (Math.random() * 15 + 10) + 'px';
            h.style.animationDuration = (Math.random() * 1 + 1) + 's';
            document.body.appendChild(h);
            setTimeout(() => h.remove(), 1500);
        }, i * 20);
    }

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