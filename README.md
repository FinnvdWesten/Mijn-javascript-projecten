# Mijn-portfolio
https://41475.hosts1.ma-cloud.nl/FS%20Portfolio/

## Getting started

function setup() {
    createCanvas(700, 600);
}

function draw() {
    background(0, 160, 190);
  fill("Yellow")
  stroke("Orange")
  strokeWeight(3)
    circle(620, 80, 130);
  fill("Green")
  strokeWeight(0.4)
  stroke("Black")
  text("🌲", 200, 340)
  textSize(120)
  text("🌲", 70, 340)
  text("🌲", 300, 340)
  textSize(80)
  text("🌲", 500, 340)
  rect(0, 350, 700, 370)
  strokeWeight(0)
  fill("white")
  ellipse(200, 150, 170, 70)
  ellipse(350, 110, 110, 40)
  textSize(100)
  text("🏕️", 400, 460)
  textSize(50)
  text("🔥", 310, 470)
  textSize(100)
  text("🏕️", 150, 420)
}


## Variables and change

let cloudOneX = 100;
let cloudTwoX = 160;

function setup() {
    createCanvas(700, 600);
}

function draw() {
    background(60, 110, 220);

    strokeWeight(0);
    fill("green");
    rect(0, 400, 800, 300);

    fill("yellow");
    stroke("orange");
    strokeWeight(2);
    circle(680, 30, 130)

    fill("white");
    strokeWeight(1);
    stroke("black");
    ellipse(cloudTwoX, 220, 120, 50);

    fill("white");
    strokeWeight(1);
    stroke("black");
    ellipse(cloudOneX, 200, 150, 70);

    cloudOneX = framecount % width
    cloudTwoX = framecount % width
}

## Conditionals and interactivity:

function setup() {
    createCanvas(800, 600);

    
}
let blueVal = 255;
let sunHeight;
let horizon = 440;
let backgroundColor;

function draw() {
    background(0, 0, blueVal);

    if(sunHeight < 590){
        blueVal -= 0.5;
    }
    else if(sunHeight > 590){
        blueVal = 255;
    }

    //Draws the sun
    fill("yellow");
    circle(400, sunHeight, 180);

    //Draws the floor
    fill("green");
    rect(0, 350, 800, 250);

    textSize(100);
    text("🏠", 200, 400);
    text("🏠", 290, 520);
    text("🏠", 80, 430);
    text("🌳", 450, 430);
    text("🌳", 550, 470);

    sunHeight = frameCount % height;

    if(sunHeight > 600)
    {
        sunHeight = 0;
    }
}


## Organizing code with functions:

function setup() {
    createCanvas(800, 600);
}

function draw() {
    background(133, 40, 40);
    drawPyramid();
    drawSun();
    drawSand();

}

function drawSun() {
    strokeWeight(1);
    stroke("orange");
    fill("yellow");
    circle(730 , 80, 120);
}

function drawSand(){
    strokeWeight(1);
    stroke(200, 178, 128);
    fill(194, 178, 128);
    rect(0, 400, 800, 600);
}

function drawPyramid(){
    fill(204, 119, 34);
    stroke(0);
    strokeWeight(1);
    triangle(100, 400, 450, 400, 250, 200);
}

# Repeating with loops

let startLine = 30;
let finishLine = 400;

let spacing = 20;
let segmentSize = 30;
let eyeSize = 15;

let numCaterpillars = 3;
let caterpillarEnds = [];

let isRacing = false;

function setup() {
  createCanvas(500, 500);
 
  frameRate(3);

  for (let i=0;i<numCaterpillars;i++) {
    caterpillarEnds.push(startLine)
  }
}

function draw() {
  background(121, 96, 76);
  noStroke();
  fill(0);
  rect(startLine, 0, 5, height);
  fill(0, 255, 0);
  rect(finishLine, 0, 20, height);

  if (isRacing === true) {
    moveCaterpillars();
  } else { 
    writeStart();
  }
  drawCaterpillars();

  checkWinner();
}

function writeStart() {

  textSize(24);
  textAlign(CENTER);
  fill(255);
  noStroke();

  text("🏁 Click to start!", width / 2, height / 2);
}

function drawCaterpillar(x, y, segments) {

  for (let i = 0; i < segments; i += 1) {
    fill(255, 0, 200);
    stroke(0);
    strokeWeight(1);
    circle(x, y, 50);
    x += spacing;
  }

  fill(0);
  stroke(255);
  strokeWeight(3);
  circle(x, y - eyeSize, eyeSize);
  circle(x - eyeSize, y - eyeSize, eyeSize);
}

function drawCaterpillars() {
  let padding = height / numCaterpillars;
  for (let i = 0; i < numCaterpillars; i += 1) {

    let y = (i + 0.5) * padding;

 
    crawl = random(3, 6);


    drawCaterpillar(caterpillarEnds[i], y, crawl);
  }
}

function mousePressed() {
  isRacing = true;
}


function moveCaterpillars() {
  for (let i = 0; i < numCaterpillars; i += 1) {

    let move = round(random(5, 30));

    caterpillarEnds[i] += move;
  }
}

function checkWinner() {
  for (let i = 0; i < caterpillarEnds.length; i += 1) {
    if (caterpillarEnds[i] >= finishLine) {

      textSize(24);
      textAlign(CENTER);
      fill(255);
      noStroke();

      text(`Caterpillar ${i + 1} wins!`,width/2,height/2);

      noLoop();
    }
  }
}

# Data structure garden


let flowers = []; 

function setup() {
createCanvas(400, 400);

flowerPower(); 
}

function draw() {
background('darkblue');

updateAndDrawFlowers();
}

function mousePressed() {
let flower = createFlower();

flower.x = mouseX; 

flower.y = mouseY;

flowers.push(flower);
}

function updateAndDrawFlowers() {
for (let flower of flowers) {

  drawFlower(flower);

  flower.size *= 0.89;

  flower.lifespan -= 2;
  
  if (flower.lifespan <= 0) {
    let i = flowers.indexOf(flower);
    
    flowers.splice(i, 1);
  }
}
}

function flowerPower(){
for(let i = 0; i < 20; i+=1){

  let flower1 = createFlower();
  
  flowers.push(flower1);
}
}

function createFlower() {
let flower = {
  x: random(20,380),
  y: random(20,380),
  size: random(20, 75),
  lifespan: random(365,500),
  color: color(random(255), random(255), random(255))
};

return flower;
}

function drawFlower(flower) {
noStroke();
fill(flower.color);

ellipse(flower.x, flower.y, flower.size / 2, flower.size);
ellipse(flower.x, flower.y, flower.size, flower.size / 2);

fill(255, 204, 0);
circle(flower.x, flower.y, flower.size / 2);

}
