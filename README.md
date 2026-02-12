# Valentines
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>For Nya ❤️</title>

<style>
body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg,#ff758c,#ff7eb3,#ffd3e0);
  font-family: 'Segoe UI', sans-serif;
  color: white;
  text-align: center;
  overflow: hidden;
}

.container { margin-top: 10vh; }

h1 { font-size: 3em; }

#counter { font-size: 1.3em; margin-top: 10px; }

button {
  padding: 15px 28px;
  font-size: 20px;
  border: none;
  border-radius: 14px;
  cursor: pointer;
  margin: 20px;
  transition: 0.25s;
}

#yes { background:#ff4d6d; color:white; }
#yes:hover { transform:scale(1.1); }

#no { background:white; color:black; position:absolute; }

img {
  width:260px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,.25);
  margin-top:20px;
}

.letter {
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.6);
  display:none;
  align-items:center;
  justify-content:center;
}

.card {
  background:white;
  color:#333;
  padding:30px;
  border-radius:18px;
  max-width:420px;
  animation:fade .5s ease;
}

@keyframes fade { from{transform:scale(.8);opacity:0} to{transform:scale(1);opacity:1} }

.hearts span {
  position:absolute;
  font-size:24px;
  animation:float 6s linear infinite;
}

@keyframes float {
  0%{transform:translateY(100vh);opacity:1}
  100%{transform:translateY(-10vh);opacity:0}
}

.music { margin-top:15px; }
</style>
</head>

<body>

<div class="hearts" id="hearts"></div>

<div class="container">
  <h1>Nya, will you be my Valentine? ❤️</h1>
  <div id="counter"></div>
  <p>You make every day feel safe, warm, and worth it.</p>

  <div id="slideshow"><img id="slide" src="https://i.imgur.com/isiOb97.jpg" alt="us" /></div>
  <br/>

  <button id="yes" onclick="openLetter()">YES 💕</button>
  <button id="no" onmouseover="moveButton()">no 😢</button>

  <div class="music">
    <button onclick="playSong()">Play our song 🎶</button>
    <div id="player"></div>
  </div>
</div>

<div class="letter" id="letter">
  <div class="card">
    <h2>I love you</h2>
    <p>
      Since July 5th, 2024, you've been my peace, my happiness, and my favorite person.
      I don't just want today with you — I want every tomorrow too.
      Thank you for choosing me, for loving me, and for being you.
      Happy Valentine's Day ❤️
      <br/><br/>
      <strong>Our Date:</strong><br/>
      Feb 14, 2026<br/>
      Dinner at Giulio's Greek Italian at 6 🍝<br/>
      Ice cream after 🍨
    </p>
    <button onclick="closeLetter()">hug accepted 🥰</button>
  </div>
</div>

<script>
// relationship counter
const start = new Date('2024-07-05');
function updateCounter(){
  const now = new Date();
  const diff = now - start;
  const days = Math.floor(diff / (1000*60*60*24));
  document.getElementById('counter').innerText = `We've been together for ${days} days 💞`;
}
setInterval(updateCounter,1000);
updateCounter();

// running button
function moveButton(){
  const btn=document.getElementById('no');
  btn.style.top=Math.random()*window.innerHeight+'px';
  btn.style.left=Math.random()*window.innerWidth+'px';
}

// letter popup
function openLetter(){ document.getElementById('letter').style.display='flex'; }
function closeLetter(){ document.getElementById('letter').style.display='none'; }

// floating hearts
const hearts=document.getElementById('hearts');
setInterval(()=>{
  const heart=document.createElement('span');
  heart.innerText='❤️';
  heart.style.left=Math.random()*100+'vw';
  heart.style.animationDuration=4+Math.random()*3+'s';
  hearts.appendChild(heart);
  setTimeout(()=>heart.remove(),7000);
},400);

// slideshow images
const images=[
  "https://i.imgur.com/isiOb97.jpg",
  "https://i.imgur.com/SiyqO6m.jpg"
];
let i=0;
setInterval(()=>{
  i=(i+1)%images.length;
  document.getElementById('slide').src=images[i];
},2500);

// youtube song (replace VIDEO_ID if needed)
function playSong(){
  document.getElementById('player').innerHTML=
    '<iframe width="0" height="0" src="https://www.youtube.com/embed/VIDEO_ID?autoplay=1&loop=1&playlist=VIDEO_ID" frameborder="0" allow="autoplay"></iframe>';
}
</script>

</body>
</html>
