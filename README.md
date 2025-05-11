<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Happy Mother's Day</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background: #fff0f5;
      overflow: hidden;
      text-align: center;
    }

    .center {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }

    #gift {
      width: 150px;
      cursor: pointer;
      transition: transform 0.3s;
    }

    #gift:hover {
      transform: scale(1.1);
    }

    #mother-img {
      position: absolute;
      top: -500px;
      left: 50%;
      transform: translateX(-50%);
      width: 300px;
      opacity: 0;
      transition: top 1s ease-in-out, opacity 1s;
    }

    h1 {
      font-size: 3em;
      color: #d6336c;
      margin-top: 20px;
      opacity: 0;
      transform: translateY(-100px);
      transition: all 1s ease-in-out;
    }

    #roses {
      width: 200px;
      margin-top: 20px;
      opacity: 0;
      transition: opacity 2s ease-in;
    }

    .heart {
      width: 20px;
      height: 20px;
      background-color: red;
      position: absolute;
      transform: rotate(45deg);
      animation: floatUp 5s infinite;
      opacity: 0.7;
    }

    .heart::before,
    .heart::after {
      content: "";
      width: 20px;
      height: 20px;
      background-color: red;
      border-radius: 50%;
      position: absolute;
    }

    .heart::before {
      top: -10px;
      left: 0;
    }

    .heart::after {
      left: -10px;
      top: 0;
    }

    @keyframes floatUp {
      0% {
        transform: translateY(0) rotate(45deg);
        opacity: 1;
      }
      100% {
        transform: translateY(-800px) rotate(45deg);
        opacity: 0;
      }
    }
  </style>
</head>
<body>

  <div class="center" id="box-container">
    <img id="gift" src="gift.png" alt="Gift Box" />
  </div>

  <img id="mother-img" src="mother.jpg" alt="Mother" />
  <h1 id="title">Happy Mother's Day!</h1>
  <img id="roses" src="roses.png" alt="Roses" />

  <script>
    function createHeart() {
      const heart = document.createElement("div");
      heart.classList.add("heart");
      heart.style.left = Math.random() * 100 + "vw";
      heart.style.animationDuration = (Math.random() * 2 + 3) + "s";
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 5000);
    }

    // Only create hearts after gift click
    function startHearts() {
      setInterval(createHeart, 300);
    }

    document.getElementById("gift").addEventListener("click", function() {
      document.getElementById("gift").style.display = "none";
      const img = document.getElementById("mother-img");
      const title = document.getElementById("title");
      const roses = document.getElementById("roses");

      img.style.top = "100px";
      img.style.opacity = "1";

      setTimeout(() => {
        title.style.opacity = "1";
        title.style.transform = "translateY(0)";
      }, 1000);

      setTimeout(() => {
        roses.style.opacity = "1";
        startHearts();
      }, 2000);
    });
  </script>

</body>
</html>
