<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>For Tessi ❤️</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to top right, #ffe6f0, #f3e5f5);
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      overflow: hidden;
      position: relative;
    }

    .container {
      background: white;
      padding: 35px 30px;
      border-radius: 25px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
      width: 90%;
      max-width: 500px;
      text-align: center;
      animation: fadeIn 1s ease-in-out;
      position: relative;
      z-index: 2;
    }

    @keyframes fadeIn {
      0% { opacity: 0; transform: scale(0.95); }
      100% { opacity: 1; transform: scale(1); }
    }

    .page {
      display: none;
    }

    .active {
      display: block;
    }

    input {
      padding: 12px;
      width: 90%;
      margin-top: 15px;
      border-radius: 10px;
      border: 1px solid #ccc;
      font-size: 16px;
    }

    button {
      margin-top: 25px;
      padding: 12px 30px;
      font-size: 16px;
      border: none;
      border-radius: 25px;
      background-color: #ff69b4;
      color: white;
      cursor: pointer;
      box-shadow: 0 4px 15px rgba(255, 105, 180, 0.5);
      transition: all 0.3s ease;
    }

    button:hover {
      background-color: #ff1493;
      transform: scale(1.05);
    }

    #heart {
      font-size: 80px;
      color: red;
      animation: pulse 1s infinite;
      margin: 20px 0;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.2); }
      100% { transform: scale(1); }
    }

    /* Floating hearts */
    .floating-heart {
      position: absolute;
      font-size: 20px;
      animation: float 6s infinite ease-in-out;
      color: #ff4d6d;
      opacity: 0.6;
    }

    @keyframes float {
      0% {
        transform: translateY(100vh) scale(1);
        opacity: 0;
      }
      50% {
        opacity: 0.8;
      }
      100% {
        transform: translateY(-10vh) scale(1.5);
        opacity: 0;
      }
    }

    /* Popup message */
    .popup {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: #fff0f5;
      border: 1px solid #ff69b4;
      color: #c2185b;
      padding: 12px 20px;
      border-radius: 10px;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
      z-index: 100;
      animation: slideDown 0.5s ease;
    }

    @keyframes slideDown {
      from { opacity: 0; transform: translateY(-30px) translateX(-50%); }
      to { opacity: 1; transform: translateY(0) translateX(-50%); }
    }

  </style>
</head>
<body>

<!-- Background Music -->
<audio autoplay loop>
  <source src="https://dl.sndup.net/64nf/Drunk%20Text.mp3" type="audio/mpeg" />
  Your browser does not support the audio element.
</audio>

<!-- Floating Hearts -->
<script>
  for (let i = 0; i < 40; i++) {
    let heart = document.createElement("div");
    heart.classList.add("floating-heart");
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.animationDuration = (4 + Math.random() * 4) + "s";
    heart.style.fontSize = (16 + Math.random() * 20) + "px";
    heart.innerHTML = "❤️";
    document.body.appendChild(heart);
  }
</script>

<div class="container">
  <div class="page active" id="page1">
    <h2>Hi Tessi ❤️</h2>
    <p>What's my favorite color?</p>
    <input type="text" id="q1" />
    <button onclick="validateAnswer(1)">Next</button>
  </div>

  <div class="page" id="page2">
    <p>How many stars would you give our love?</p>
    <input type="number" id="q2" min="1" max="10" />
    <button onclick="validateAnswer(2)">Next</button>
  </div>

  <div class="page" id="page3">
    <p>What do I call you the most?</p>
    <input type="text" id="q3" />
    <button onclick="validateAnswer(3)">Next</button>
  </div>

  <div class="page" id="page4">
    <p>When’s our shared special day?</p>
    <input type="text" id="q4" />
    <button onclick="validateAnswer(4)">Next</button>
  </div>

  <div class="page" id="page5">
    <p>How much do I love you?</p>
    <input type="text" id="q5" />
    <button onclick="checkFinalAnswer()">Finish</button>
  </div>
</div>

<script>
  function showPopup(message, duration = 3000) {
    const popup = document.createElement("div");
    popup.className = "popup";
    popup.textContent = message;
    document.body.appendChild(popup);
    setTimeout(() => {
      popup.remove();
    }, duration);
  }

  const correctAnswers = {
    1: ["red", "your eyes color", "you"],
    2: [10],
    3: ["tessi", "babe", "baby"],
    4: ["11", "the 11th"],
    5: ["a lot", "so much", "infinite", "to the moon", "endlessly"]
  };

  const hints = {
    1: "Think about what i adore most about you.or the fire between us 🌤️",
    2: "Be honest... is it less than perfect? 🌟",
    3: "It’s short, sweet, and starts with a 'T' 😉",
    4: "It’s the month we both blow candles 🎂",
    5: "Endless... like the stars ✨"
  };

  function validateAnswer(num) {
    const input = document.getElementById("q" + num).value.trim().toLowerCase();
    if (!input) {
      showPopup("Please fill in the answer 📝");
      return;
    }

    let isCorrect;
    if (num === 2) {
      isCorrect = correctAnswers[num].includes(Number(input));
    } else {
      isCorrect = correctAnswers[num].some(answer => input.includes(answer));
    }

    if (isCorrect) {
      showPopup("✅ That’s right!", 1500);
      setTimeout(() => {
        document.getElementById("page" + num).classList.remove("active");
        document.getElementById("page" + (num + 1)).classList.add("active");
      }, 1200);
    } else {
      showPopup("❌ Not quite. Hint: " + hints[num]);
    }
  }

  function checkFinalAnswer() {
    const input = document.getElementById("q5").value.trim().toLowerCase();
    const valid = correctAnswers[5].some(answer => input.includes(answer));

    if (valid) {
      document.body.innerHTML = `
        <div class="container">
          <div id="heart">❤️</div>
          <h2>I love you, Tessi</h2>
          <p>Now press play and let the music speak 🎶</p>
          <p>Redirecting in 5 seconds...</p>
        </div>
      `;
      setTimeout(() => {
        window.location.href = "https://open.spotify.com/playlist/7waJW6EkQMOISLNn3dc89j";
      }, 5000);
    } else {
      showPopup("❌ Almost! Hint: " + hints[5]);
    }
  }
</script>

</body>
</html>
