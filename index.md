---
layout: default
title: A Special Question
permalink: /valentine/
---

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