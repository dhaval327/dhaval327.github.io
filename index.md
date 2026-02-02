---
layout: default
title: ❤️ A Message for Linh
permalink: /valentine/
---

<style>
  @import url('https://fonts.googleapis.com/css2?family=Dancing+Script:wght@700&family=Great+Vibes&family=Quicksand:wght@500&display=swap');

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
    font-family: 'Quicksand', sans-serif;
    overflow: hidden;
    perspective: 2000px;
  }

  /* Envelope Assembly - Scaled up an additional 10% (~440px) */
  .envelope-wrapper {
    position: relative;
    width: 440px;
    height: 286px;
    background-color: var(--envelope-color);
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
    z-index: 1;
    box-shadow: 0 25px 50px rgba(0,0,0,0.25);
  }

  .flap {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 0;
    border-left: 220px solid transparent;
    border-right: 220px solid transparent;
    border-top: 155px solid var(--envelope-flap);
    transform-origin: top;
    transition: transform 0.8s ease-in-out, z-index 0.1s 0.8s;
    z-index: 5;
    filter: drop-shadow(0 5px 5px rgba(0,0,0,0.15));
  }

  #open-button {
    position: absolute;
    top: 110px;
    left: 185px;
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
    font-size: 0.8rem;
  }

  .envelope-label {
    position: absolute;
    bottom: 35px;
    left: 45px;
    font-family: 'Great Vibes', cursive;
    font-size: 2.8rem;
    color: rgba(255, 255, 255, 0.95);
    z-index: 4;
    pointer-events: none;
    transform: rotate(-5deg);
  }

  /* Realistic Card with Stationery Texture */
  #valentine-container {
    position: absolute;
    top: 40px; 
    left: 40px; 
    background: #fff;
    background-image: radial-gradient(#f0f0f0 1px, transparent 0);
    background-size: 20px 20px;
    padding: 1.5rem;
    border-radius: 5px;
    width: 360px;
    height: 230px;
    text-align: center;
    z-index: 2;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    border: 1px solid #ddd;
    box-shadow: 0 10px 20px rgba(0,0,0,0.1);
    opacity: 0;
    visibility: hidden;
    transition: transform 1.2s cubic-bezier(0.4, 0, 0.2, 1), opacity 0.3s;
  }

  /* Photo Space */
  .photo-frame {
    width: 100px;
    height: 80px;
    border: 3px solid #fff;
    outline: 1px solid #eee;
    background: #fafafa;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    margin-bottom: 5px;
  }
  .photo-frame img { width: 100%; height: 100%; object-fit: cover; }

  /* Elegant Font for Question */
  h1.question-text { 
    font-family: 'Dancing Script', cursive; 
    color: var(--dark-pink); 
    font-size: 1.6rem; 
    margin: 0;
  }

  /* Cartoon Style Checkbox Buttons */
  .options-container {
    display: flex;
    gap: 30px;
    margin-bottom: 10px;
    position: relative;
    width: 100%;
    justify-content: center;
  }

  .check-option {
    display: flex;
    align-items: center;
    gap: 8px;
    cursor: pointer;
    font-weight: bold;
    color: #444;
  }

  .box {
    width: 22px;
    height: 22px;
    border: 2px solid #555;
    background: white;
    position: relative;
    display: inline-block;
  }

  #no-wrapper { position: absolute; left: 60%; transition: 0.1s ease; }

  /* Sequence Actions */
  .open-flap .flap { transform: rotateX(180deg); z-index: 0; }
  .open-flap #valentine-container { opacity: 1; visibility: visible; }
  .open-flap #open-button { opacity: 0; pointer-events: none; }
  .open-flap .envelope-label { opacity: 0; transition: opacity 0.5s; }

  .pull-out #valentine-container { transform: translateY(-220px); }

  .centered #valentine-container {
    z-index: 10;
    transform: translateY(40px) scale(1.9);
    box-shadow: 0 40px 100px rgba(0,0,0,0.3);
  }

  /* Front Pocket */
  .envelope-front {
    position: absolute;
    bottom: 0;
    left: 0;
    width: 440px;
    height: 286px;
    background: linear-gradient(to top, var(--pocket-color) 60%, #f7a3a3 100%);
    clip-path: polygon(0 40%, 100% 40%, 100% 100%, 0 100%, 0 40%, 50% 85%, 0 40%);
    z-index: 3;
    border-bottom-left-radius: 12px;
    border-bottom-right-radius: 12px;
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
    <div id="question-section" style="width:100%; height:100%; display:flex; flex-direction:column; justify-content:space-between; align-items:center;">
      <div class="photo-frame">
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" alt="Our Photo">
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
        <h1 style="font-family: 'Dancing Script', cursive; color: var(--dark-pink); font-size: 2rem;">YAY! 🥰</h1>
        <p style="font-weight: bold; color: #555;">Check yes! See you soon, Linh!</p>
        <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="100">
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
    const x = Math.random() * 160 - 80;
    const y = Math.random() * 80 - 40;
    btn.style.transform = `translate(${x}px, ${y}px)`;
  }

  function celebrate() {
    // Fill the Yes box
    document.getElementById('yesBox').style.background = '#4caf50';
    document.getElementById('yesBox').innerHTML = '<span style="color:white; position:absolute; top:-2px; left:3px;">✓</span>';
    
    setTimeout(() => {
        document.getElementById('question-section').style.display = 'none';
        document.getElementById('success-section').style.display = 'block';
        for(let i=0; i<50; i++) setTimeout(createHeart, i * 50);
    }, 400);
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
  setInterval(createHeart, 1500);
</script>