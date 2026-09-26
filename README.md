<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>web anak tolol</title>
  <style>
    body {
      background-color: #1e1e1e;
      color: #00ff66;
      font-family: 'Courier New', Courier, monospace;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      min-height: 100vh;
      margin: 0;
      overflow: hidden;
      transition: transform 0.1s ease;
    }

    .editor {
      background: #252526;
      border: 2px solid #333;
      border-radius: 8px;
      padding: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.5);
      width: 80%;
      max-width: 600px;
      position: relative;
    }

    button {
      background-color: #ff0055;
      color: white;
      border: none;
      padding: 12px 24px;
      font-size: 18px;
      font-weight: bold;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 15px;
      box-shadow: 0 4px #990033;
    }

     
    .bug, .flying-text {
      position: absolute;
      font-size: 25px;
      user-select: none;
      pointer-events: none;
      z-index: 999;
    }

    .shake {
      animation: shake 0.1s infinite;
    }

    @keyframes shake {
      0% { transform: translate(3px, 3px) rotate(0deg); }
      50% { transform: translate(-3px, -2px) rotate(2deg); }
      100% { transform: translate(1px, -3px) rotate(-1deg); }
    }
  </style>
</head>
<body>

  <div class="editor" id="code-box">
    <h2>apacoba</h2>
    <p>// tekan tombol di bawah coba...</p>
    <pre><code>function rakitKodingan() {
  let pizza = Infinity;
  let bug = "Uncaught TypeError";
  return pizza + bug;
}</code></pre>
  </div>

  <button id="run-btn">▶ RUN CODE (jangan diklik kayaknuya)</button>

  <script>
    const runBtn = document.getElementById("run-btn");
    const codeBox = document.getElementById("code-box");
    const body = document.body;

    const pesanKocak = [
      "ERROR 404: Otak Not Found!",
      "Uncaught TypeError: error njir",
      "SyntaxError: nyoli terus sih",
      "WARNING: device kamu jebol",
      "😱",
      "npm install kehidupan...",
      "Undefined is not a function bro!",
      "git push --force (Bismillah)"
    ];

    runBtn.addEventListener("click", () => {
      // 1. Efek Layar Bergetar
      body.classList.add("shake");
      setTimeout(() => body.classList.remove("shake"), 3000);

      // 2. Munculin Bug (🪲) Acak di Layar
      for (let i = 0; i < 15; i++) {
        createBug();
      }

      // 3. Munculin Teks Error Kocak Terbang
      for (let i = 0; i < 5; i++) {
        createFlyingText();
      }

      // 4. Muter-muter Box Kode
      const randomDeg = Math.floor(Math.random() * 360);
      codeBox.style.transform = `rotate(${randomDeg}deg)`;
      codeBox.style.transition = "transform 0.5s ease";

      // 5. Ubah Warna Background Secara Acak
      const randomColor = `#${Math.floor(Math.random()*16777215).toString(16)}`;
      body.style.backgroundColor = randomColor;
    });

    function createBug() {
      const bug = document.createElement("div");
      bug.classList.add("bug");
      bug.innerText = "🪲";
      bug.style.left = Math.random() * window.innerWidth + "px";
      bug.style.top = Math.random() * window.innerHeight + "px";
      document.body.appendChild(bug);

      // Gerakin bug-nya muter/jalan acak
      let angle = 0;
      setInterval(() => {
        angle += 0.1;
        bug.style.transform = `translate(${Math.cos(angle) * 20}px, ${Math.sin(angle) * 20}px) rotate(${angle * 50}deg)`;
      }, 50);
    }

    function createFlyingText() {
      const text = document.createElement("div");
      text.classList.add("flying-text");
      text.innerText = pesanKocak[Math.floor(Math.random() * pesanKocak.length)];
      text.style.color = "#ff0000";
      text.style.fontWeight = "bold";
      text.style.left = Math.random() * (window.innerWidth - 200) + "px";
      text.style.top = Math.random() * (window.innerHeight - 50) + "px";
      document.body.appendChild(text);

      setTimeout(() => {
        text.remove();
      }, 2500);
    }
  </script>
</body>
</html>
