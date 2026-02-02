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
    --wax-seal: #9e1b32;
    --tape-color: rgba(255, 175, 204, 0.6);
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

  /* Envelope & Flap logic kept sharp */
  .envelope-wrapper {
    position: relative;
    width: 484px;
    height: 315px;
    z-index: 1;
    background: var(--body-color);
    box-shadow: 0 40px 80px rgba(0,0,0,0.25);
  }

  .envelope-back {
    position: absolute; width: 100%; height: 100%;
    background: linear-gradient(145deg, var(--body-color), #e07676);
    z-index: 1;
  }

  .flap {
    position: absolute; top: 0; left: 0; width: 100%; height: 100%;
    background: var(--flap-color);
    clip-path: polygon(0 0, 100% 0, 100% 5%, 50% 55%, 0 5%);
    transform-origin: top;
    transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1), z-index 0.1s 0.8s;
    z-index: 5;
    filter: drop-shadow(0 4px 2px rgba(0,0,0,0.2));
  }

  /* Occasional Wiggle Animation */
  @keyframes periodicWiggle {
    0%, 90% { transform: rotate(0deg); }
    92% { transform: rotate(5deg); }
    94% { transform: rotate(-5deg); }
    96% { transform: rotate(5deg); }
    98% { transform: rotate(-5deg); }
    100% { transform: rotate(0deg); }
  }

  #open-button {
    position: absolute; top: 130px; left: 207px;
    width: 70px; height: 70px;
    background: radial-gradient(circle at 30% 30%, var(--wax-seal), #7a1224);
    color: #ffd700; border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    font-weight: bold; cursor: pointer; z-index: 6;
    border: 2px solid #8a1428;
    box-shadow: 0 4px 10px rgba(0,0,0,0.4);
    font-size: 0.75rem; text-transform: uppercase;
    animation: periodicWiggle 4s infinite ease-in-out;
    transition: opacity 0.3s;
  }

  /* Card & Washi Tape */
  #valentine-container {
    position: absolute; top: 40px; left: 42px; 
    background: #fffcf5;
    background-image: url("https://www.transparenttextures.com/patterns/felt.png");
    padding: 2rem; width: 400px; height: 250px;
    text-align: center; z-index: 2; display: flex;
    flex-direction: column; justify-content: space-between; align-items: center;
    opacity: 0; visibility: hidden;
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.5s;
  }

  .photo-frame {
    position: relative; width: 110px; height: 90px;
    background: white; padding: 5px; box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    transform: rotate(-2deg);
  }

  /* Washi Tape Corners */
  .tape {
    position: absolute; width: 40px; height: 15px;
    background: var(--tape-color);
    box-shadow: 1px 1px 2px rgba(0,0,0,0.05);
    z-index: 10;
  }
  .tape-tl { top: -8px; left: -15px; transform: rotate(-35deg); }
  .tape-tr { top: -8px; right: -15px; transform: rotate(35deg); }

  h1.question-text { font-family: 'Dancing Script', cursive; color: var(--wax-seal); font-size: 1.8rem; }

  .options-container { display: flex; gap: 60px; justify-content: center; width: 100%; margin-bottom: 10px; }
  .check-option { display: flex; align-items: center; gap: 10px; cursor: pointer; font-weight: bold; }
  .box { width: 26px; height: 26px; border: 2.5px solid #555; background: white; position: relative; }

  #no-wrapper { transition: 0.1s ease; }

  /* Confetti Styles */
  .confetti {
    position: fixed; width: 8px; height: 8px; z-index: 200;
    animation: confettiFall 3s ease-out forwards;
  }
  @keyframes confettiFall {
    0% { transform: translateY(0) rotate(0deg); opacity: 1; }
    100% { transform: translateY(100vh) rotate(720deg); opacity: 0; }
  }

  /* Background Hearts */
  .heart-bg {
    position: fixed; bottom: -20px; color: rgba(255, 175, 204, 0.4);
    animation: floatUp linear forwards; z-index: -1;
  }
  @keyframes floatUp { to { transform: translateY(-110vh) rotate(360deg); opacity: 0; } }

  /* Logic triggers */
  .open-flap .flap { transform: rotateX(180deg); z-index: 0; }
  .open-flap #valentine-container { opacity: 1; visibility: visible; }
  .open-flap #open-button { opacity: 0; pointer-events: none; }
  .centered #valentine-container { transform: translateY(-80px) scale(1.9); z-index: 100; box-shadow: 0 60px 140px rgba(0,0,0,0.5); }
</style>

<div id="overlay"></div>

<div class="envelope-wrapper" id="envelope">
  <div class="envelope-back"></div>
  <div class="flap"></div>
  <div id="open-button" onclick="startSequence()">Open</div>
  
  <div id="valentine-container">
    <div id="question-section" style="width:100%; height:100%; display:flex; flex-direction:column; justify-content:space-between; align-items:center;">
      <div class="photo-frame">
        <div class="tape tape-tl"></div>
        <div class="tape tape-tr"></div>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" style="width:100%; height:100%; object-fit:cover;">
      </div>
      <h1 class="question-text">Will you be my Valentine?</h1>
      <div class="options-container">
        <div class="check-option" onclick="celebrate()">
          <div class="box" id="yesBox"></div><span>Yes</span>
        </div>
        <div id="no-wrapper">
          <div class="check-option" onmouseover="moveNo()">
            <div class="box"></div><span>No</span>
          </div>
        </div>
      </div>
    </div>
    <div id="success-section" style="display:none;">
        <h1 style="font-family: 'Dancing Script', cursive; color: var(--wax-seal); font-size: 2.2rem;">YAY! 🥰</h1>
        <p style="font-weight: bold; color: #555;">See you soon, Linh!</p>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="100">
    </div>
  </div>
  <div class="envelope-front" style="clip-path: polygon(0 5%, 50% 55%, 100% 5%, 100% 100%, 0 100%);"></div>
</div>

<script>
  // Background Hearts
  function spawnHeart() {
    const h = document.createElement('div');
    h.className = 'heart-bg';
    h.innerHTML = '❤️';
    h.style.left = Math.random() * 100 + 'vw';
    h.style.fontSize = (Math.random() * 20 + 10) + 'px';
    h.style.animationDuration = (Math.random() * 3 + 4) + 's';
    document.body.appendChild(h);
    setTimeout(() => h.remove(), 7000);
  }
  setInterval(spawnHeart, 1000);

  function startSequence() {
    const env = document.getElementById('envelope');
    env.classList.add('open-flap');
    setTimeout(() => {
      env.classList.add('centered');
      document.body.classList.add('centered-view');
    }, 800);
  }

  function moveNo() {
    const n = document.getElementById('no-wrapper');
    n.style.transform = `translate(${Math.random()*160-80}px, ${Math.random()*80-40}px)`;
  }

  function celebrate() {
    document.getElementById('yesBox').style.background = '#4caf50';
    document.getElementById('yesBox').innerHTML = '<span style="color:white; position:absolute; top:-3px; left:4px;">✓</span>';
    
    // Confetti burst
    for(let i=0; i<100; i++) {
      const c = document.createElement('div');
      c.className = 'confetti';
      c.style.left = '50%'; c.style.top = '50%';
      c.style.backgroundColor = ['#ffafcc', '#ff5c8a', '#ffd700', '#ffffff'][Math.floor(Math.random()*4)];
      c.style.setProperty('--x', (Math.random()-0.5)*1000 + 'px');
      c.style.transform = `translate(${(Math.random()-0.5)*400}px, ${(Math.random()-0.5)*400}px)`;
      document.body.appendChild(c);
      setTimeout(() => c.remove(), 3000);
    }

    setTimeout(() => {
      document.getElementById('question-section').style.display = 'none';
      document.getElementById('success-section').style.display = 'block';
    }, 400);
  }
</script>