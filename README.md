<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Sweet 17 Party</title>
<link href="https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap" rel="stylesheet">
<style>
body {
  margin: 0;
  font-family: 'Press Start 2P', cursive;
  color: #3e3e3e;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  overflow: hidden;
}
.page {
  display: none;
  text-align: center;
  padding: 20px;
  background: rgba(255,255,255,0.6);
  border-radius: 10px;
}
.active { display: block; }
button {
  padding: 10px 20px;
  margin: 10px;
  font-family: inherit;
  font-size: 12px;
  border: none;
  background-color: #c49a6c;
  color: #fff;
  border-radius: 5px;
  cursor: pointer;
}
.cards-container, .game2-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 15px;
  margin-top: 20px;
}
.card {
  width: 80px;
  height: 80px;
  background: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  font-size: 30px;
  border: 2px solid #3e3e3e;
}
.hidden-card { background-color: #a58a5c; }
input {
  padding: 8px;
  font-size: 12px;
  margin: 10px 0;
  width: 200px;
}
.confetti {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  position: absolute;
  cursor: pointer;
  animation: fall linear forwards;
}
@keyframes fall {
  0% { transform: translateY(-30px) rotate(0deg); opacity: 1; }
  100% { transform: translateY(100vh) rotate(360deg); opacity: 0; }
}
.leaf {
  position: absolute;
  top: 0;
  width: 40px;
  height: 40px;
  background-image: url('https://i.ibb.co/K6mGfJd/pixel-leaf.png');
  background-size: cover;
  animation: float 15s linear infinite;
}
@keyframes float {
  0% { transform: translateX(100vw) translateY(0) rotate(0deg); }
  100% { transform: translateX(-50px) translateY(200px) rotate(360deg); }
}
.page-bg {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.8s ease-in-out;
}
.page-bg.active-bg { opacity: 1; }
</style>
</head>
<body>
  <!-- Background audio -->
<audio id="bg-audio" loop>
  <source src="https://deliberate-maroon-veh39jf1ah.edgeone.app/StockTune-Pixel%20Dreams%20At%20Midnight_1760877344.mp3" type="audio/mpeg">
  Your browser does not support the audio element.
</audio>
  <!-- Play/Pause Button -->
  <button id="audioBtn">🔊 Play Music</button>
<!-- Backgrounds -->
<div id="bg1" class="page-bg active-bg" style="background-image:url('https://i.postimg.cc/bNgTz2H0/huya.png');"></div>
<div id="bg2" class="page-bg" style="background-image:url('https://i.postimg.cc/rF7P648P/yessir.png');"></div>
<div id="bg3" class="page-bg" style="background-image:url('https://i.postimg.cc/PJvrxD0Y/cake.png');"></div>
<div id="bg4" class="page-bg" style="background-image:url('https://i.postimg.cc/X7ym2LwB/game.png');"></div>
<div id="bg5" class="page-bg" style="background-image:url('https://i.postimg.cc/L6Ffgk3B/wel.png');"></div>
<div id="bg6" class="page-bg" style="background-image:url('https://i.postimg.cc/0jyN7Qrz/party-yeah.png');"></div>
<div id="bg7" class="page-bg" style="background-image:url('https://i.postimg.cc/YSgcywTj/sad-huhu.png');"></div>
<div id="bg8" class="page-bg" style="background-image:url('https://i.postimg.cc/QMR8HmZ5/bye-bye.png');"></div>
<div id="bg9" class="page-bg" style="background-image:url('https://i.postimg.cc/Qd9vH3N3/sad.png');"></div>

<!-- Pages -->
<div id="page1" class="page active" style="background:none; display:flex; flex-direction:column; justify-content:flex-end; height:100vh;">
  <button style="margin-bottom:40px;" onclick="nextPage(2)">Start</button>
</div>

<div id="page2" class="page">
  <h1>Game 1</h1>
  <h3 id="game1-text">Pick a card</h3>
  <div class="cards-container">
    <div class="card" onclick="checkCard('wrong')">🎲</div>
    <div class="card" onclick="checkCard('right')">🍰</div>
    <div class="card" onclick="checkCard('wrong')">❤️</div>
  </div>
  <div id="game1-buttons"></div>
</div>

<div id="page3" class="page">
  <h1>Game 2</h1>
  <h3 id="game2-text">Match the card</h3>
  <div class="game2-grid">
    <div class="card hidden-card" data-pair="1" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="2" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="3" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="4" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="1" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="6" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="5" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="2" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="3" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="5" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="4" onclick="flipCard(this)">?</div>
    <div class="card hidden-card" data-pair="6" onclick="flipCard(this)">?</div>
  </div>
  <div id="game2-buttons"></div>
</div>

<div id="page4" class="page" style="position: relative; overflow: hidden; height: 80vh;">
  <h1>Game 3</h1>
  <h3 id="game3-text">Tap the confetti</h3>
  <div id="game3-buttons"></div>
</div>

<div id="page5" class="page">
  <p>Location: Jl. Ngagel Jaya Utara No.41, Surabaya</p>
  <p>Date: Saturday 15 November 2025</p>
  <p>Time: 15.00 - Tired</p>
  <p>Dresscode: Pajama (or anything comfy)</p>
  <h2>Would you join me??</h2>
  <button onclick="nextPage(6)">Yes</button>
  <button onclick="nextPage(7)">No</button>
</div>

<div id="page6" class="page">
  <h2>Fill your name</h2>
  <form id="rsvpFormName">
    <input type="text" name="name" placeholder="Your full name">
    <button type="submit">Next</button>
  </form>
</div>

<div id="page7" class="page">
  <h2>OH NO WHYYY</h2>
  <form id="rsvpFormReason">
    <input type="text" name="reason" placeholder="Reason (if not coming)">
    <button type="submit">Next</button>
  </form>
</div>

<div id="page8" class="page">
  <h1>THAT'S THE END</h1>
  <h2>WELCOME TO AILEEN'S SWEET 17TH PARTY</h2>
</div>

<div id="page9" class="page">
  <h1>THAT'S OKAY</h1>
  <h2>HAVE A NICE DAY ❤️</h2>
</div>

<script>
function nextPage(pageNum){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.getElementById('page'+pageNum).classList.add('active');

  document.querySelectorAll('.page-bg').forEach(bg=>bg.classList.remove('active-bg'));
  const bg=document.getElementById('bg'+pageNum);
  if(bg) bg.classList.add('active-bg');

  if(pageNum===4){ spawnConfetti(); }
}

function checkCard(result){
  const text=document.getElementById('game1-text');
  const buttonsDiv=document.getElementById('game1-buttons');
  buttonsDiv.innerHTML='';
  if(result==='right'){
    text.innerText='Yayy congratulations';
    buttonsDiv.innerHTML='<button onclick="nextPage(3)">Next</button>';
  } else {
    buttonsDiv.innerHTML='<button onclick="tryAgainGame1()">Try Again</button>';
  }
}
function tryAgainGame1(){
  document.getElementById('game1-text').innerText='Pick a card';
  document.getElementById('game1-buttons').innerHTML='';
}

let firstCard=null, lock=false, matched=0;
const pairsContent={1:'🐧',2:'⭐️',3:'🎁',4:'🎀',5:'🎲',6:'❤️'};
function flipCard(card){
  if(lock||card.classList.contains('flipped')) return;
  card.classList.add('flipped');
  card.innerText=pairsContent[card.dataset.pair];
  if(!firstCard){ firstCard=card; }
  else {
    lock=true;
    setTimeout(()=>{
      if(firstCard.dataset.pair===card.dataset.pair){
        matched+=2; firstCard=null; lock=false;
        if(matched===12){
          document.getElementById('game2-text').innerText='You Did It!';
          document.getElementById('game2-buttons').innerHTML='<button onclick="nextPage(4)">Next</button>';
        }
      } else {
        firstCard.innerText='?'; card.innerText='?';
        firstCard.classList.remove('flipped'); card.classList.remove('flipped');
        firstCard=null; lock=false;
      }
    },800);
  }
}

let score=0, confettiInterval;
function spawnConfetti(){
  clearInterval(confettiInterval);
  createConfettiBatch();
  confettiInterval=setInterval(()=>{ if(score>=10){ clearInterval(confettiInterval); return; } createConfettiBatch(); },1000);
}
function createConfettiBatch(){
  for(let i=0;i<10;i++){
    const c=document.createElement('div');
    c.classList.add('confetti');
    c.style.backgroundColor=`hsl(${Math.random()*360},70%,60%)`;
    c.style.left=Math.random()*90+'%';
    c.style.animationDuration=3+Math.random()*2+'s';
    c.onclick=()=>{ c.remove(); score++; if(score>=10){ document.getElementById('game3-text').innerText='Yayy! You got 10!'; document.getElementById('game3-buttons').innerHTML='<button onclick="nextPage(5)">Next</button>'; clearInterval(confettiInterval); } };
    document.getElementById('page4').appendChild(c);
  }
}

function toggleAudio(){
  const audio=document.getElementById('bg-audio');
  if(audio.paused) audio.play();
  else audio.pause();
}
const audio = document.getElementById('bg-audio');
const btn = document.getElementById('audioBtn');

btn.addEventListener('click', () => {
  if(audio.paused){
    audio.play();
    btn.innerText = "🔇 Pause Music";
  } else {
    audio.pause();
    btn.innerText = "🔊 Play Music";
  }
});
</script>
</body>
</html>
