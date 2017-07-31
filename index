<!DOCTYPE html>
<html>
  <b>**</b>
  <i>the paddles of avelor</i>
  <B>**</B>
  
<canvas id="gameCanvas" width="600" height="400"></canvas>
<script>
  var canvas;
  var Canvascontext;
  var ballx = 50;
  var bally = 50;
  var ballspeedx = 5;
  var ballspeedy = 5;
  var paddle1Y = 100;
  var paddle2y = 100;
  const paddleheight = 100;
  const paddlewidth = 10;
  var player1score = 0;
  var player2score = 0;
  const winningscore = 1;
  var showingwinningscreen = false;
  function handlemouseclick(evt){
    if (showingwinningscreen){
      player1score=0;
      player2score=0;
      showingwinningscreen = false;
      
    }
  }
  
  function calculateMousePos(evt){
    var rect = canvas.getBoundingClientRect();
    var root = document.documentElement;
    var mouseX = evt.clientX - rect.left - root.scrollLeft;
    var mouseY = evt.clientY - rect.top - root.scrollTop;
    return {
      x:mouseX,
      y:mouseY
    };
  }
  window.onload = function() {
    console.log("In a world where swords reigned");
    canvas = document.getElementById('gameCanvas');
    Canvascontext = canvas.getContext('2d');
    var framesPerSecond = 30;
    setInterval(function(){
      moveEverything();
      drawEverything();
    },1000/framesPerSecond);
    canvas.addEventListener('mousedown', handlemouseclick);
  canvas.addEventListener('mousemove',
  function(evt){
    var MousePos = calculateMousePos(evt)
    paddle1Y = MousePos.y - (paddleheight/2);
  });
   
   } 
   function ballreset(){
     if (player2score >= winningscore||player1score>=winningscore) {
       showingwinningscreen=true;
       
      
       
     }
     ballspeedx = -ballspeedx
     ballx = canvas.width/2;
     bally = canvas.height/2;
  }
  
  function computermovement() {
       var paddle2ycenter = paddle2y + (paddleheight/2);
       if (paddle2ycenter < bally - 35) {
         paddle2y += 6;
       } else if  (paddle2ycenter > bally + 35) {
         paddle2y -= 6;
       }
       
     }
     
  function moveEverything() {
  if (showingwinningscreen) {
    return;
  }
  computermovement();
  
  ballx = ballx + ballspeedx;
  bally = bally + ballspeedy;
  
  if (ballx <0) {
    if (bally > paddle1Y && 
    bally < paddle1Y+paddleheight){
      ballspeedx=-ballspeedx
      var deltay = bally 
      - (paddle1Y+paddleheight/2)
      ballspeedy = deltay*0.35;
    } else {
      player2score += 1;
      ballreset();
    }
  }
          
  if (ballx > canvas.width) {
    if (bally > paddle2y && 
    bally < paddle2y+paddleheight){
      ballspeedx=-ballspeedx
      var deltay = bally 
      - (paddle2y+paddleheight/2)
      ballspeedy = deltay*0.35;
    } else {
      player1score += 1;
      ballreset();
      
    }
  }
  if (bally <0) {
    ballspeedy= -ballspeedy
  }
  if (bally > canvas.height) {
    ballspeedy = -ballspeedy
  }
  
  }
    function drawnet() {
      for(var i=0;i<canvas.height; i+=40) {
        colorRect(canvas.width/2-1,i,2,20,'white');
      }
  
  }
  
  function drawEverything() {
    colorRect(0,0,canvas.width,canvas.height,'black');
    if (showingwinningscreen) {
    Canvascontext.fillStyle = 'pink';
    Canvascontext.fillText ("click to continue",150,150);
    if(player2score>=winningscore) {
    
    Canvascontext.fillText("player 2 wins",300,300);
    return;
    } else if (player1score>=winningscore) {
    
    Canvascontext.fillText("player 1 wins",300,300);
    return;
    }
    
    }
    drawnet();
    colorRect(0,paddle1Y,paddlewidth,paddleheight, 'blue');
    colorRect(canvas.width-10,paddle2y,paddlewidth,paddleheight,'orange');    
    colorCircle(ballx,bally,10,'red');
    Canvascontext.fillText(player1score,100,100);
    Canvascontext.fillText(player2score,canvas.width-100,canvas.height-100);
  }
  
  
  function colorCircle(centerX,centerY,radius,drawColor) {
    Canvascontext.fillStyle = drawColor;
    Canvascontext.beginPath();
    Canvascontext.arc(centerX,centerY,radius,0,Math.PI*2,true);
    Canvascontext.fill();
  }
 
  function colorRect(leftX,topY,width,height,drawColor) {
    Canvascontext.fillStyle = drawColor;
    Canvascontext.fillRect(leftX,topY,width,height);
  }
</script>
</html>
