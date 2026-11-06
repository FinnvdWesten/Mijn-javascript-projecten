# Mijn-portfolio
https://41475.hosts1.ma-cloud.nl/FS%20Portfolio/

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

