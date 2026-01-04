# Sorry-Mam..<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <title>Sorry 😅</title>
  <style>
    body {
      background: #fff0f0;
      font-family: "Poppins", Arial, sans-serif;
      margin: 0;
      padding: 20px;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    h1 {
      color: #d33;
      font-size: 2rem;
      margin-bottom: 20px;
      text-align: center;
    }

    #sorry-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 8px;
      margin-bottom: 40px;
    }

    .sorry {
      background: #ffe6e6;
      padding: 8px 16px;
      border-radius: 12px;
      color: #c00;
      font-weight: bold;
      animation: pop 0.5s ease forwards;
    }

    @keyframes pop {
      0% { transform: scale(0.5); opacity: 0; }
      60% { transform: scale(1.2); opacity: 1; }
      100% { transform: scale(1); }
    }

    .button-container {
      display: flex;
      align-items: center;
      gap: 12px;
      margin-bottom: 50px;
    }

    button {
      background-color: #ff6666;
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 25px;
      font-size: 18px;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background-color: #ff3333;
      transform: scale(1.05);
    }

    #tap-icon {
      font-size: 20px;
      color: #c00;
      animation: blink 1s infinite;
    }

    @keyframes blink {
      0%, 50%, 100% { opacity: 1; }
      25%, 75% { opacity: 0; }
    }

    #thankyou {
      display: none;
      text-align: center;
      font-size: 28px;
      color: #c00;
      font-weight: bold;
      margin-top: 20px;
    }

    .heart {
      display: inline-block;
      animation: heartbeat 1s infinite;
      transform-origin: center;
    }

    @keyframes heartbeat {
      0%, 100% { transform: scale(1); }
      25% { transform: scale(1.2); }
      50% { transform: scale(1); }
      75% { transform: scale(1.15); }
    }

    /* Confetti particles */
    .confetti {
      position: absolute;
      width: 8px;
      height: 8px;
      background-color: #ff3333;
      pointer-events: none;
      z-index: 9999;
      opacity: 0.8;
      border-radius: 50%;
      animation: confetti-fall 2s linear forwards;
    }

    @keyframes confetti-fall {
      0% { transform: translateY(0) rotate(0deg); opacity: 1; }
      100% { transform: translateY(400px) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>

  <h1>Oops! 😅</h1>

  <div id="sorry-container"></div>

  <div class="button-container">
    <button id="forgiveBtn">Forgive Me Mam ❤️</button>
    <span id="tap-icon">👆 Tap here</span>
  </div>

  <div id="thankyou"><span class="heart">Thank you so much Mam ❤️</span></div>

  <script>
    const container = document.getElementById("sorry-container");
    const messages = ["Sorry 😅", "Oops!", "My bad 😢", "Forgive me 🙏", "Really sorry!"];
    let i = 0;

    // Pop up messages gradually
    function addSorry() {
      if(i >= 20) return;
      const p = document.createElement("div");
      p.className = "sorry";
      p.textContent = messages[Math.floor(Math.random() * messages.length)];
      container.appendChild(p);
      i++;
      setTimeout(addSorry, 300);
    }
    addSorry();

    // Handle button click
    const btn = document.getElementById("forgiveBtn");
    const thanks = document.getElementById("thankyou");

    btn.addEventListener("click", () => {
      btn.style.display = "none";
      document.getElementById("tap-icon").style.display = "none";
      thanks.style.display = "block";
      thanks.scrollIntoView({behavior: "smooth"});
      createConfetti(50); // create 50 confetti particles
    });

    // Create confetti particles
    function createConfetti(count) {
      for(let i=0; i<count; i++){
        const conf = document.createElement("div");
        conf.className = "confetti";
        conf.style.left = Math.random() * window.innerWidth + "px";
        conf.style.backgroundColor = `hsl(${Math.random()*360}, 80%, 60%)`;
        conf.style.animationDuration = 1 + Math.random()*1.5 + "s";
        conf.style.width = conf.style.height = 5 + Math.random()*5 + "px";
        document.body.appendChild(conf);
        setTimeout(() => conf.remove(), 2000);
      }
    }
  </script>

</body>
</html>
