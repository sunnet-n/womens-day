```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Women's Day Nadia</title>

<style>

body{
margin:0;
overflow:hidden;
background:#0f0f1a;
font-family:Arial, sans-serif;
color:white;
text-align:center;
}

canvas{
position:absolute;
top:0;
left:0;
}

/* center message */

.container{
position:absolute;
top:40%;
left:50%;
transform:translate(-50%,-50%);
z-index:10;
}

#name{
font-size:80px;
letter-spacing:12px;
color:#ff66b2;
text-shadow:0 0 25px #ff66b2,0 0 50px #ff66b2;
animation:pulse 2s infinite alternate;
}

@keyframes pulse{
from{transform:scale(1);}
to{transform:scale(1.1);}
}

#message{
font-size:26px;
margin-top:20px;
min-height:40px;
}

/* scattered photos */

.photo{
position:absolute;
border-radius:20px;
border:6px solid white;
box-shadow:0 0 20px rgba(255,255,255,0.7);
object-fit:cover;
transition:transform 0.4s;
}

.photo:hover{
transform:scale(1.15);
z-index:20;
}

/* hearts and roses */

.heart,.rose{
position:absolute;
font-size:24px;
animation:float 7s linear infinite;
}

@keyframes float{
from{
transform:translateY(100vh);
opacity:1;
}
to{
transform:translateY(-10vh);
opacity:0;
}
}

</style>
</head>

<body>

<canvas id="sky"></canvas>

<div class="container">
<div id="name">NADIA</div>
<div id="message"></div>
</div>

<!-- photos -->

<img src="photo1.jpg" class="photo">
<img src="photo2.jpg" class="photo">
<img src="photo3.jpg" class="photo">
<img src="photo4.jpg" class="photo">
<img src="photo5.jpg" class="photo">

<script>

/* star background */

const canvas=document.getElementById("sky");
const ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let stars=[];

for(let i=0;i<250;i++){
stars.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
r:Math.random()*2
});
}

function drawStars(){

ctx.clearRect(0,0,canvas.width,canvas.height);

ctx.fillStyle="white";

stars.forEach(s=>{
ctx.beginPath();
ctx.arc(s.x,s.y,s.r,0,Math.PI*2);
ctx.fill();
});

requestAnimationFrame(drawStars);

}

drawStars();

/* typing message */

const text="Happy International Women's Day Nadia! You are inspiring, brilliant and wonderful ✨";
let i=0;

function typing(){

if(i<text.length){
document.getElementById("message").innerHTML+=text.charAt(i);
i++;
setTimeout(typing,50);
}

}

typing();

/* floating hearts */

function heart(){

let h=document.createElement("div");
h.className="heart";
h.innerHTML="💖";
h.style.left=Math.random()*100+"vw";

document.body.appendChild(h);

setTimeout(()=>h.remove(),7000);

}

setInterval(heart,400);

/* roses */

function rose(){

let r=document.createElement("div");
r.className="rose";
r.innerHTML="🌹";
r.style.left=Math.random()*100+"vw";

document.body.appendChild(r);

setTimeout(()=>r.remove(),7000);

}

setInterval(rose,1500);

/* fireworks */

let particles=[];

function firework(){

let x=Math.random()*canvas.width;
let y=Math.random()*canvas.height/2;

for(let i=0;i<40;i++){

let angle=Math.random()*Math.PI*2;
let speed=Math.random()*5;

particles.push({
x:x,
y:y,
vx:Math.cos(angle)*speed,
vy:Math.sin(angle)*speed,
life:80
});

}

}

function animateFireworks(){

particles.forEach((p,index)=>{

p.x+=p.vx;
p.y+=p.vy;
p.life--;

ctx.fillStyle="pink";
ctx.fillRect(p.x,p.y,3,3);

if(p.life<=0) particles.splice(index,1);

});

requestAnimationFrame(animateFireworks);

}

setInterval(firework,2000);

animateFireworks();

/* randomize photo position and size */

const photos=document.querySelectorAll(".photo");

photos.forEach(photo=>{

let size=120+Math.random()*140;

photo.style.width=size+"px";
photo.style.height=size+"px";

photo.style.left=Math.random()*90+"vw";
photo.style.top=Math.random()*80+"vh";

});

</script>

</body>
</html>
```
