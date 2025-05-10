<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Happy Birthday, My Love!</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #ffe6f0;
      text-align: center;
      padding: 20px;
      overflow: hidden;
    }
    h1 {
      color: #ff4d6d;
      font-size: 2.5em;
    }
    .letter, .quiz, .prize {
      background: white;
      padding: 20px;
      margin: 20px auto;
      width: 90%;
      max-width: 500px;
      border-radius: 10px;
      box-shadow: 0 0 15px #ffb3c6;
    }
    button {
      background: #ff4d6d;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 5px;
      cursor: pointer;
      margin: 10px;
    }
    button:hover {
      background: #ff1f4c;
    }
    #countdown {
      font-size: 1.3em;
      margin-bottom: 10px;
      color: #ff4d6d;
    }
    .hidden {
      display: none;
    }
    .heart {
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      transform: rotate(45deg);
      animation: fall 5s linear infinite;
    }
    .heart::before,
    .heart::after {
      content: "";
      position: absolute;
      width: 20px;
      height: 20px;
      background: red;
      border-radius: 50%;
    }
    .heart::before {
      top: -10px;
      left: 0;
    }
    .heart::after {
      left: -10px;
      top: 0;
    }
    @keyframes fall {
      0% { top: -10%; left: calc(100% * var(--i)); opacity: 1; }
      100% { top: 110%; left: calc(100% * var(--i) + 50px); opacity: 0; }
    }
    .heart-beat {
      font-size: 2em;
      color: red;
      animation: beat 1s infinite;
    }
    @keyframes beat {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.3); }
    }
    .win-animation {
      font-size: 2em;
      color: #ff4d6d;
      animation: flash 1s infinite;
    }
    @keyframes flash {
      0%, 100% { opacity: 1; }
      50% { opacity: 0.3; }
    }
  </style>
</head>
<body>

  <h1>Happy Birthday, My Love!</h1>

  <!-- Falling hearts -->
  <div class="heart" style="--i:0.1"></div>
  <div class="heart" style="--i:0.3"></div>
  <div class="heart" style="--i:0.5"></div>
  <div class="heart" style="--i:0.7"></div>
  <div class="heart" style="--i:0.9"></div>

  <div class="letter">
    <div id="countdown">Countdown: 10 seconds</div>
    <p>Hi Baby,</p>
    <p>I know we’re far apart right now, but I wanted to give you this little virtual gift to remind you how much I love you.  
    Thank you for being the most amazing boyfriend — my game buddy, my best friend, my love, my forever.  
    Every moment with you, even online, makes my heart happy. I miss your voice, your hugs, and your laugh.  
    Please remember: no matter how far apart we are, you are always in my heart.  
    Let’s play a little quiz now — let’s see how well you remember our love story!</p>
  </div>

  <div class="quiz hidden">
    <p><strong>1. Where did we first meet?</strong></p>
    <button onclick="checkAnswer(1, 'a')">a) Online</button>
    <button onclick="checkAnswer(1, 'b')">b) School</button>
    <button onclick="checkAnswer(1, 'c')">c) Game lobby</button>
    <div id="q1"></div>

    <p><strong>2. What’s my favorite nickname for you?</strong></p>
    <button onclick="checkAnswer(2, 'a')">a) Baby</button>
    <button onclick="checkAnswer(2, 'b')">b) Daddy / Dada</button>
    <button onclick="checkAnswer(2, 'c')">c) Honhon</button>
    <div id="q2"></div>

    <p><strong>3. Which game do we love to play together?</strong></p>
    <button onclick="checkAnswer(3, 'a')">a) Mobile Legends</button>
    <button onclick="checkAnswer(3, 'b')">b) Minecraft</button>
    <button onclick="checkAnswer(3, 'c')">c) Roblox</button>
    <div id="q3"></div>

    <p><strong>4. What’s something I always say to you?</strong></p>
    <button onclick="checkAnswer(4, 'a')">a) “I’m mad at you!”</button>
    <button onclick="checkAnswer(4, 'b')">b) “I love you forever.”</button>
    <button onclick="checkAnswer(4, 'c')">c) “Go play games now.”</button>
    <div id="q4"></div>

    <p><strong>5. What’s my dream with you?</strong></p>
    <button onclick="checkAnswer(5, 'a')">a) Travel the world</button>
    <button onclick="checkAnswer(5, 'b')">b) Build a home together</button>
    <button onclick="checkAnswer(5, 'c')">c) Just stay LDR forever</button>
    <div id="q5"></div>

    <p><strong>6. When is our anniversary?</strong></p>
    <button onclick="checkAnswer(6, 'a')">a) November 3</button>
    <button onclick="checkAnswer(6, 'b')">b) December 3</button>
    <button onclick="checkAnswer(6, 'c')">c) October 3</button>
    <div id="q6"></div>

    <p><strong>7. Who fell first?</strong></p>
    <button onclick="checkAnswer(7, 'a')">a) Me</button>
    <button onclick="checkAnswer(7, 'b')">b) You</button>
    <button onclick="checkAnswer(7, 'c')">c) Same time</button>
    <div id="q7"></div>
  </div>

  <div id="prize" class="prize hidden">
    <h2 class="heart-beat">You Win My Heart!</h2>
    <p class="win-animation">Congratulations, baby! You answered all the questions and you win:</p>
    <ul style="list-style: none; padding: 0;">
      <li>♥ A virtual hug</li>
      <li>♥ A thousand kisses</li>
      <li>♥ My endless love</li>
    </ul>
    <p>I promise you, one day, we will look back at this and smile because we made it through everything.  
    Happy birthday, baby! I love you so much, always and forever.</p>
  </div>

  <script>
    let countdown = 10;
    const countdownElement = document.getElementById('countdown');
    const quizSection = document.querySelector('.quiz');
    const prizeSection = document.getElementById('prize');
    let score = 0;
    let answered = 0;

    const timer = setInterval(() => {
      countdown--;
      countdownElement.textContent = `Countdown: ${countdown} seconds`;
      if (countdown <= 0) {
        clearInterval(timer);
        countdownElement.style.display = 'none';
        quizSection.classList.remove('hidden');
      }
    }, 1000);

    function checkAnswer(question, answer) {
      const correctAnswers = {
        1: 'a',
        2: 'b',
        3: 'a',
        4: 'b',
        5: 'b',
        6: 'a',
        7: 'a'
      };
      const resultDiv = document.getElementById('q' + question);
      if (!resultDiv.textContent) {
        if (correctAnswers[question] === answer) {
          resultDiv.textContent = 'Correct!';
          score++;
        } else {
          resultDiv.textContent = 'Oops! Wrong answer.';
        }
        answered++;
      }

      if (answered === 7) {
        quizSection.classList.add('hidden');
        prizeSection.classList.remove('hidden');
      }
    }
  </script>

</body>
</html>
