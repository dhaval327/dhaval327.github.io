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
  }

  /* This targets the default Jekyll header/nav area */
.site-header {
  background-color: #fff0f3 !important;
  border-top: 5px solid #ffafcc !important;
  border-bottom: none !important;
}

.site-title, .site-title:visited {
  color: #ff5c8a !important; /* Soft pink title */
  font-weight: bold;
}

/* This hides the default footer if you want a cleaner look */
.site-footer {
  display: none;
}

/* If you are still using Cayman, this forcefully overrides the green hero section */
.page-header {
  background-color: #ffafcc !important;
  background-image: linear-gradient(120deg, #ffafcc, #ffc8dd) !important;
  color: white !important;
}

  body {
    background: linear-gradient(135deg, var(--soft-white) 0%, var(--primary-pink) 100%);
    margin: 0;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  }

  #valentine-container {
    background: rgba(255, 255, 255, 0.8);
    backdrop-filter: blur(10px);
    padding: 3rem;
    border-radius: 20px;
    box-shadow: 0 10px 30px rgba(255, 92, 138, 0.2);
    border: 2px solid white;
    max-width: 500px;
    width: 90%;
  }

  h1 {
    color: var(--dark-pink);
    font-size: 2.5rem;
    text-shadow: 1px 1px 2px rgba(0,0,0,0.05);
  }

  .buttons button {
    transition: transform 0.2s, box-shadow 0.2s;
  }

  .buttons button:hover {
    transform: scale(1.05);
    box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  }
</style>

<div id="valentine-container" style="text-align: center; margin-top: 50px; font-family: 'Arial', sans-serif;">
  <div id="question-section">
    <h1 style="color: #e91e63;">Will you be my Valentine? ❤️</h1>
    <div id="gif-container" style="margin: 20px;">
      <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/l41JWZ59PzT2/giphy.gif" width="250" alt="Cute gif">
    </div>

    <div class="buttons">
      <button id="yesButton" onclick="celebrate()" style="background-color: #4caf50; color: white; padding: 15px 32px; font-size: 16px; border: none; border-radius: 8px; cursor: pointer;">Yes!</button>

      <button id="noButton" onmouseover="moveButton()" style="background-color: #f44336; color: white; padding: 15px 32px; font-size: 16px; border: none; border-radius: 8px; position: absolute; margin-left: 10px;">No</button>
    </div>
  </div>

  <div id="success-section" style="display: none;">
    <h1 style="color: #e91e63;">YAY! See you on the 14th! 🥰</h1>
    <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExOHp1ZzR2cnR5ZzR2cnR5ZzR2cnR5/26FLdmIp6wJr91JAI/giphy.gif" width="300">
  </div>
</div>

<script>
  function moveButton() {
    const btn = document.getElementById('noButton');
    // Get random coordinates within the viewport
    const x = Math.random() * (window.innerWidth - btn.offsetWidth);
    const y = Math.random() * (window.innerHeight - btn.offsetHeight);

    btn.style.left = x + 'px';
    btn.style.top = y + 'px';
  }

  function celebrate() {
    document.getElementById('question-section').style.display = 'none';
    document.getElementById('success-section').style.display = 'block';
  }
</script>

<script>
  function createHeart() {
    const heart = document.createElement('div');
    heart.classList.add('heart-effect');
    heart.innerHTML = '❤️';
    heart.style.left = Math.random() * 100 + 'vw';
    heart.style.animationDuration = Math.random() * 2 + 3 + 's';
    heart.style.position = 'fixed';
    heart.style.bottom = '-20px';
    heart.style.fontSize = Math.random() * 10 + 20 + 'px';
    heart.style.opacity = Math.random();
    heart.style.zIndex = '-1';

    document.body.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 5000);
  }

  // Create a heart every 300ms
  setInterval(createHeart, 300);
</script>

<style>
  @keyframes floatUp {
    0% { transform: translateY(0) rotate(0deg); }
    100% { transform: translateY(-110vh) rotate(360deg); }
  }
  .heart-effect {
    animation: floatUp linear forwards;
  }
</style>