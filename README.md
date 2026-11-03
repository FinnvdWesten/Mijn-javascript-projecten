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
