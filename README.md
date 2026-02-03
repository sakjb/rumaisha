<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Will You Be My Valentine?</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@500;700&family=Poppins:wght@300;400;500&display=swap" rel="stylesheet">

  <style>
    :root{
      --pink:#f6b7c1;
      --offwhite:#fff7f9;
      --deep:#d96c7b;
    }

    *{box-sizing:border-box}

    body{
      margin:0;
      min-height:100vh;
      font-family:'Poppins',sans-serif;
      /* Emoji love + rose background */
      background-color: var(--offwhite);
      background-image:
        url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='160' height='160'><text x='0' y='40' font-size='36'>🌹</text><text x='80' y='120' font-size='34'>💖</text><text x='20' y='120' font-size='30'>💕</text></svg>");
      background-size:160px 160px;
      display:flex;
      align-items:center;
      justify-content:center;
      overflow:hidden;
    }

    /* floating hearts animation */
    .heart{position:absolute;width:16px;height:16px;background:var(--pink);transform:rotate(45deg);opacity:.7;animation:float 6s linear infinite}
    .heart:before,.heart:after{content:"";position:absolute;width:16px;height:16px;background:var(--pink);border-radius:50%}
    .heart:before{left:-8px}
    .heart:after{top:-8px}
    @keyframes float{from{transform:translateY(100vh) rotate(45deg)}to{transform:translateY(-10vh) rotate(45deg)}}

    .card{
      width:92vw;
      max-width:420px;
      background:rgba(255,255,255,.94);
      border-radius:26px;
      padding:32px 22px 38px;
      text-align:center;
      box-shadow:0 20px 45px rgba(217,108,123,.35);
      animation:fadeUp 1.1s ease;
    }

    @keyframes fadeUp{
      from{opacity:0;transform:translateY(30px)}
      to{opacity:1;transform:translateY(0)}
    }

    h1{
      font-family:'Playfair Display',serif;
      font-size:32px;
      color:#7a3f49;
      margin-bottom:8px;
    }

    .name{
      font-family:'Playfair Display',serif;
      font-size:24px;
      color:var(--deep);
      margin-bottom:14px;
    }

    p{
      font-size:15px;
      line-height:1.7;
      margin-bottom:24px;
      color:#5b3a40;
    }

    .buttons{
      position:relative;
      height:70px;
      margin-top:10px;
    }

    button{
      position:absolute;
      border:none;
      border-radius:999px;
      padding:14px 26px;
      font-size:16px;
      cursor:pointer;
      transition:.12s linear;
      box-shadow:0 8px 18px rgba(217,108,123,.25);
    }

    .yes{
      left:50%;
      transform:translateX(-50%);
      background:linear-gradient(135deg, var(--pink), #ffdbe2);
      color:#7a3f49;
      font-weight:500;
      z-index:2;
    }

    .no{
      right:0;
      background:#fff;
      color:#7a3f49;
      border:2px solid rgba(217,108,123,.4);
      z-index:1;
    }

    .response{
      margin-top:22px;
      font-family:'Playfair Display',serif;
      font-size:18px;
      color:var(--deep);
      min-height:28px;
      white-space:pre-line;
    }

    .footer{
      margin-top:24px;
      font-size:12px;
      opacity:.7;
    }
  </style>
</head>
<body>

  <!-- floating hearts -->
  <div class="heart" style="left:10%"></div>
  <div class="heart" style="left:30%"></div>
  <div class="heart" style="left:50%"></div>
  <div class="heart" style="left:70%"></div>
  <div class="heart" style="left:90%"></div>

  <div class="card">
    <h1>Will You Be My Valentine?</h1>
    <div class="name">Rumaisha Jahan</div>

    <p>
      I made this little world just for you 🌹<br>
      Roses, love emojis, and all my heart.
    </p>

    <div class="buttons">
      <button class="yes" onclick="sayYes()">Yes 💖</button>
      <button class="no" id="noBtn">No 🙈</button>
    </div>

    <div class="response" id="response"></div>

    <div class="footer">— forever yours, Mahi</div>
  </div>

  <audio id="loveSong" src="https://cdn.pixabay.com/audio/2022/02/23/audio_48b9a1a02c.mp3"></audio>

  <script>
    const noBtn = document.getElementById('noBtn');
    const response = document.getElementById('response');
    const song = document.getElementById('loveSong');

    // Faster runaway behavior
    ['mouseover','touchstart','mousemove'].forEach(evt => {
      noBtn.addEventListener(evt, moveFast);
    });

    function moveFast(){
      const maxX = 80; // percent
      const maxY = 40; // px
      const x = Math.random() * maxX;
      const y = Math.random() * maxY;
      noBtn.style.left = x + '%';
      noBtn.style.top = y + 'px';
    }

    function sayYes(){
      response.innerText = `আমার সাথে ভালবাসা দিবসে ঘুরতে যাবে?
১৩ তারিখে আমার জন্মদিন থাকায় ১৪ তারিখ ঘুরতে না গেলেও হবে কারন আম্মু তো যেতে দিবেনা তোমাকে 😞
তোমাকে আমি অনেক ভালোবাসি এবং সারাজীবন এভাবেই তোমাকে ভালবাসবো আর খুশি রাখবো।
এভাবে জীবনের বাকি সব ফেব্রুয়ারি মাসে একসাথে দুইজনের জন্মদিন আর এই ভালোবাসা দিবস উদযাপন করতে চাই।
আজকের জন্য অনেক বাংলা হয়ে গেলো, বিদায় বাবু <3`;
      song.currentTime = 0;
      song.play();
    }
  </script>

</body>
</html>
