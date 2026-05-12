
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>ULTIMATE FUTURE BIKE HUD</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial;
}

html,body{
width:100%;
height:100%;
overflow:hidden;
background:#000;
color:#00ffff;
}

/* CYBERPUNK BACKGROUND */

body{
background:
radial-gradient(circle at center,#001122,#000),
linear-gradient(135deg,#000,#001122,#120024);
}

/* AMOLED MODE */

.amoled{
background:#000 !important;
}

/* GRID */

.grid{
position:absolute;
width:100%;
height:100%;
background:
linear-gradient(rgba(0,255,255,.05) 1px,transparent 1px),
linear-gradient(90deg,rgba(0,255,255,.05) 1px,transparent 1px);
background-size:35px 35px;
animation:gridMove 5s linear infinite;
}

@keyframes gridMove{
0%{transform:translateY(0);}
100%{transform:translateY(35px);}
}

/* STARTUP */

.startup{
position:absolute;
width:100%;
height:100%;
background:black;
display:flex;
justify-content:center;
align-items:center;
font-size:clamp(30px,7vw,60px);
font-weight:bold;
color:#00ffff;
z-index:9999;
animation:start 3s forwards;
text-shadow:0 0 20px #00ffff;
}

@keyframes start{
0%{opacity:1;}
80%{opacity:1;}
100%{
opacity:0;
visibility:hidden;
}
}

/* CLOCK */

.clock{
position:absolute;
top:10px;
left:50%;
transform:translateX(-50%);
font-size:clamp(14px,2vw,24px);
z-index:10;
}

/* WARNING */

.warn{
position:absolute;
top:40px;
left:50%;
transform:translateX(-50%);
font-size:clamp(12px,2vw,22px);
color:red;
font-weight:bold;
text-shadow:0 0 15px red;
z-index:10;
}

/* NAVIGATION */

.navArrow{
position:absolute;
top:80px;
left:50%;
transform:translateX(-50%);
font-size:55px;
text-shadow:0 0 25px #00ffff;
animation:blink 1s infinite;
z-index:10;
}

@keyframes blink{
50%{opacity:.4;}
}

/* CENTER HUD */

.centerHUD{
position:absolute;
top:55%;
left:50%;
transform:translate(-50%,-50%);
width:min(72vw,72vh);
height:min(72vw,72vh);
display:flex;
justify-content:center;
align-items:center;
}

/* OUTER */

.outerRing{
width:100%;
height:100%;
border-radius:50%;
border:4px solid rgba(0,255,255,.4);
display:flex;
justify-content:center;
align-items:center;
position:relative;
box-shadow:
0 0 25px #00ffff,
0 0 90px #00ffff inset;
animation:pulse 2s infinite alternate;
}

@keyframes pulse{

from{
box-shadow:
0 0 20px #00ffff,
0 0 60px #00ffff inset;
}

to{
box-shadow:
0 0 50px #00ffff,
0 0 120px #00ffff inset;
}

}

/* SPEED NUMBERS */

.speedNumbers{
position:absolute;
width:100%;
height:100%;
border-radius:50%;
display:flex;
justify-content:center;
align-items:center;
}

.speedNumbers span{

position:absolute;

font-size:clamp(10px,2vw,18px);

font-weight:bold;

text-shadow:0 0 12px #00ffff;

transform:
rotate(calc(var(--i) * 30deg))
translateY(calc(-1 * min(33vw,33vh)))
rotate(calc(var(--i) * -30deg));

}

/* NEEDLE */

.needle{

position:absolute;

width:4px;

height:38%;

background:#ff0033;

bottom:50%;

left:50%;

transform-origin:bottom center;

transform:translateX(-50%) rotate(-120deg);

border-radius:10px;

box-shadow:0 0 20px red;

transition:.15s linear;

z-index:5;

}

.needle::after{

content:"";

position:absolute;

bottom:-10px;

left:50%;

transform:translateX(-50%);

width:18px;

height:18px;

border-radius:50%;

background:white;

box-shadow:0 0 15px #00ffff;

}

/* INNER */

.innerRing{
width:75%;
height:75%;
border-radius:50%;
border:2px solid #00ffff;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
backdrop-filter:blur(10px);
background:rgba(0,0,0,.2);
}

/* SPEED */

.speed{
font-size:clamp(50px,12vw,120px);
font-weight:bold;
color:white;
text-shadow:0 0 35px #00ffff;
}

.kmh{
font-size:clamp(12px,2vw,22px);
letter-spacing:5px;
}

.gear{
margin-top:10px;
font-size:clamp(20px,5vw,42px);
font-weight:bold;
}

/* PANELS */

.panel{
position:absolute;
width:min(42vw,240px);
padding:12px;
background:rgba(0,0,0,.35);
border:1px solid rgba(0,255,255,.3);
border-radius:18px;
box-shadow:0 0 20px rgba(0,255,255,.3);
backdrop-filter:blur(10px);
}

/* LEFT */

.left{
left:10px;
top:18%;
}

/* RIGHT */

.right{
right:10px;
top:18%;
}

/* CARDS */

.card{
margin-bottom:15px;
}

/* BAR */

.bar{
margin-top:8px;
height:10px;
background:#111;
border-radius:20px;
overflow:hidden;
}

.fill{
height:100%;
width:0%;
background:#00ffff;
box-shadow:0 0 20px #00ffff;
transition:.2s;
}

/* MAP */

.map{
width:100%;
height:140px;
border:none;
border-radius:15px;
margin-top:10px;
}

/* COMPASS */

.compass{
width:80px;
height:80px;
margin:auto;
border-radius:50%;
border:2px solid #00ffff;
display:flex;
justify-content:center;
align-items:center;
font-size:32px;
animation:spin 6s linear infinite;
}

@keyframes spin{
from{transform:rotate(0deg);}
to{transform:rotate(360deg);}
}

/* LEAN */

.lean{
position:absolute;
bottom:90px;
right:20px;
font-size:18px;
text-shadow:0 0 10px #00ffff;
}

/* CAMERA */

#cam{
position:absolute;
bottom:10px;
right:10px;
width:120px;
height:80px;
border:2px solid #00ffff;
border-radius:10px;
object-fit:cover;
}

/* RAIN */

#rain{
position:absolute;
top:0;
left:0;
width:100%;
height:100%;
pointer-events:none;
}

/* BUTTONS */

.controls{
position:absolute;
bottom:10px;
left:50%;
transform:translateX(-50%);
display:flex;
gap:10px;
flex-wrap:wrap;
justify-content:center;
width:100%;
padding:10px;
}

button{
padding:10px 14px;
background:black;
border:1px solid #00ffff;
color:#00ffff;
border-radius:12px;
font-weight:bold;
cursor:pointer;
transition:.3s;
font-size:clamp(11px,2vw,15px);
}

button:hover{
background:#00ffff;
color:black;
box-shadow:0 0 20px #00ffff;
}

/* MOBILE */

@media(max-width:768px){

.left{
width:43vw;
top:12px;
left:5px;
font-size:12px;
}

.right{
width:43vw;
top:12px;
right:5px;
font-size:12px;
}

.centerHUD{
top:60%;
width:68vw;
height:68vw;
}

.map{
height:80px;
}

.speedNumbers span{
font-size:10px;
}

#cam{
width:90px;
height:60px;
}

}

</style>
</head>

<body>

<div class="startup">
BIKE HUD SYSTEM
</div>

<div class="grid"></div>

<canvas id="rain"></canvas>

<!-- CLOCK -->

<div class="clock" id="clock"></div>

<!-- WARNING -->

<div class="warn" id="warn"></div>

<!-- NAVIGATION -->

<div class="navArrow" id="navArrow">⬆</div>

<!-- LEAN -->

<div class="lean" id="lean">
LEAN 0°
</div>

<!-- CENTER -->

<div class="centerHUD">

<div class="outerRing">

<!-- SPEED NUMBERS -->

<div class="speedNumbers">

<span style="--i:0">0</span>
<span style="--i:1">20</span>
<span style="--i:2">40</span>
<span style="--i:3">60</span>
<span style="--i:4">80</span>
<span style="--i:5">100</span>
<span style="--i:6">120</span>
<span style="--i:7">140</span>
<span style="--i:8">160</span>
<span style="--i:9">180</span>
<span style="--i:10">200</span>
<span style="--i:11">220</span>

</div>

<!-- NEEDLE -->

<div id="needle" class="needle"></div>

<!-- INNER -->

<div class="innerRing">

<div class="speed" id="speed">0</div>

<div class="kmh">KM/H</div>

<div class="gear" id="gear">N</div>

</div>

</div>

</div>

<!-- LEFT PANEL -->

<div class="panel left">

<div class="card">
<h3>RPM</h3>
<div id="rpmText">0 RPM</div>

<div class="bar">
<div class="fill" id="rpmFill"></div>
</div>
</div>

<div class="card">
<h3>FUEL</h3>
<div id="fuelText">100%</div>

<div class="bar">
<div class="fill" id="fuelFill"></div>
</div>
</div>

<div class="card">
<h3>TEMP</h3>
<div id="temp">70°C</div>
</div>

<div class="card">
<h3>BATTERY</h3>
<div id="battery">12.8V</div>
</div>

</div>

<!-- RIGHT PANEL -->

<div class="panel right">

<h3>LIVE GPS</h3>

<iframe
class="map"
id="map"
src="https://maps.google.com/maps?q=bhopal&output=embed">
</iframe>

<div class="card">

<h3 style="text-align:center;margin-top:10px;">
COMPASS
</h3>

<div class="compass">🧭</div>

<div
id="dir"
style="text-align:center;margin-top:10px;">
DIR : N
</div>

</div>

</div>

<!-- CAMERA -->

<video
id="cam"
autoplay
playsinline
muted>
</video>

<!-- MUSIC -->

<audio id="music"></audio>

<!-- BUTTONS -->

<div class="controls">

<button onclick="startBike()">🏍 START</button>

<button onclick="voiceAI()">🎤 AI</button>

<button onclick="toggleNight()">🌙 NIGHT</button>

<button onclick="toggleAMOLED()">⚫ AMOLED</button>

<button onclick="connectHelmet()">🎧 HELMET</button>

<button onclick="fullScreen()">⛶ FULL</button>

</div>

<script>

/* CLOCK */

setInterval(()=>{

clock.innerText=
new Date().toLocaleTimeString();

},1000);

/* VARIABLES */

let started=false;
let fuel=100;

/* START */

function startBike(){

started=true;

speak("Bike system activated");

}

/* SPEAK */

function speak(text){

speechSynthesis.speak(
new SpeechSynthesisUtterance(text)
);

}

/* NIGHT MODE */

function toggleNight(){

document.body.style.filter=
"brightness(.8) contrast(1.2)";

}

/* AMOLED */

function toggleAMOLED(){

document.body.classList.toggle("amoled");

}

/* HELMET */

function connectHelmet(){

if(navigator.bluetooth){

navigator.bluetooth.requestDevice({
acceptAllDevices:true
})
.then(device=>{

alert("Helmet Connected: "+device.name);

});

}

}

/* FULLSCREEN */

function fullScreen(){

document.documentElement.requestFullscreen();

}

/* AI */

function voiceAI(){

let rec=
new(window.SpeechRecognition||
window.webkitSpeechRecognition)();

rec.lang="en-US";

rec.onresult=(e)=>{

let cmd=
e.results[0][0].transcript.toLowerCase();

if(cmd.includes("speed")){

speak(
"Current speed is "+
speed.innerText+
" kilometer per hour"
);

}

if(cmd.includes("fuel")){

speak(
"Fuel level is "+
fuelText.innerText
);

}

};

rec.start();

}

/* GPS */

if(navigator.geolocation){

navigator.geolocation.watchPosition(

(pos)=>{

if(!started) return;

let lat=pos.coords.latitude;
let lon=pos.coords.longitude;

/* MAP */

map.src=
`https://maps.google.com/maps?q=${lat},${lon}&output=embed`;

/* SPEED */

let s=pos.coords.speed;

if(s==null) s=0;

let kmh=Math.round(s*3.6);

speed.innerText=kmh;

/* NEEDLE */

let angle=
-120+(kmh/220)*240;

needle.style.transform=
`translateX(-50%) rotate(${angle}deg)`;

/* GEAR */

let g="N";

if(kmh>0) g="1";
if(kmh>20) g="2";
if(kmh>40) g="3";
if(kmh>60) g="4";
if(kmh>90) g="5";
if(kmh>120) g="6";

gear.innerText=g;

/* RPM */

let rpm=kmh*100;

rpmText.innerText=
rpm+" RPM";

rpmFill.style.width=
Math.min(rpm/12000*100,100)+"%";

/* TEMP */

let temp=70+kmh/5;

document.getElementById("temp").innerText=
temp.toFixed(0)+"°C";

/* FUEL */

fuel-=kmh*0.0005;

if(fuel<0) fuel=0;

fuelText.innerText=
fuel.toFixed(0)+"%";

fuelFill.style.width=
fuel+"%";

/* BATTERY */

battery.innerText=
(12.8-(kmh*0.002)).toFixed(1)+"V";

/* DIRECTION */

let dirs=["⬆","⬅","➡"];

navArrow.innerText=
dirs[Math.floor(Math.random()*3)];

/* WARN */

let w="";

if(kmh>140){
w="⚠ OVER SPEED";
}
else if(temp>100){
w="⚠ ENGINE HOT";
}
else if(fuel<10){
w="⚠ LOW FUEL";
}

warn.innerText=w;

},

()=>{

warn.innerText=
"GPS BLOCKED";

}

);

}

/* LEAN SENSOR */

window.addEventListener(
"deviceorientation",

(e)=>{

let lean=
Math.round(e.gamma);

document.getElementById("lean").innerText=
"LEAN "+lean+"°";

}

);

/* CAMERA */

navigator.mediaDevices
.getUserMedia({video:true})

.then(stream=>{

cam.srcObject=stream;

});

/* RAIN EFFECT */

const rain =
document.getElementById("rain");

const ctx =
rain.getContext("2d");

rain.width=window.innerWidth;
rain.height=window.innerHeight;

let drops=[];

for(let i=0;i<200;i++){

drops.push({
x:Math.random()*rain.width,
y:Math.random()*rain.height,
l:Math.random()*20
});

}

function drawRain(){

ctx.clearRect(
0,0,
rain.width,
rain.height
);

ctx.strokeStyle=
"rgba(0,255,255,.4)";

ctx.lineWidth=1;

for(let d of drops){

ctx.beginPath();

ctx.moveTo(d.x,d.y);

ctx.lineTo(d.x,d.y+d.l);

ctx.stroke();

d.y+=8;

if(d.y>rain.height){

d.y=-20;

}

}

requestAnimationFrame(drawRain);

}

drawRain();

</script>

</body>
</html>
