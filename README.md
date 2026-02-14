<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="style.css" />
    <title>Valentine Letter</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />

    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Aldrich&family=Pixelify+Sans:wght@400..700&display=swap"
      rel="stylesheet"
    />
    <title>Document</title>
  </head>
  <body>
    
    <div id="envelope-container">
      <img src="envelope.png" alt="Envelope" id="envelope" />
      <p>♡ Letter for You ♡</p>
    </div>

   
    <div id="letter-container">
      <div class="letter-window">
        <h1 id="letter-title">Will you be my Valentine?</h1>

        <img src="cat_heart.gif" class="cat" id="letter-cat" />

        <div class="buttons" id="letter-buttons">
          <img src="yes.png" class="btn yes-btn" alt="Yes" />

          <div class="no-wrapper">
            <img src="no.png" class="btn no-btn" alt="No" />
          </div>
        </div>

        <p id="final-text" class="final-text" style="display: none">
          <strong>Valentine Date:</strong>  Now you’re stuck with me this Valentine’s Baccha x3
        </p>
      </div>
    </div>
    <script src="script.js"></script>
  </body>
</html>
body {
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-image: url("heart-bg.jpg");
    font-family: "Pixelify Sans", sans-serif;
}


#envelope-container {
    text-align: center;
    cursor:pointer;
}

@keyframes pulse {
    0% {
        transform:scale(1);
    }
    50% {
        transform: scale(1.1);
    }
    100% {
        transform: scale(1);
    }
}

#envelope{
    width: 200px;
    animation: pulse 1.5s infinite;
    cursor: pointer;
}

#letter-container{
    display: none;
    position:fixed;
    inset: 0;
    justify-content: center;
    align-items: center;
}

.letter-window{
    width: 90vw;
    max-width: 800px;
    aspect-ratio: 3/2;
    padding: 20px 20px 0 20px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    background-image: url("window.png");
    background-size: contain;
    background-repeat: no-repeat;
    background-position: center;
    border-radius: 12px;
    gap: 1px;
    padding-top: 180px;

    transform: scale(1.2);
    opacity: 0;
    transition: transform 0.6s ease, opacity 0.6s ease;
}

.letter-window.open {
    transform: scale(1);
    opacity: 1;
}

h1 {
    font-size: 30px;
    margin:0;
}

p {
    font-size: 40px;
}

/* Cat */

.cat {
    width: 250px;
    margin: 10px 0;
    transition: width 0.4s ease;
}

.letter-window.final .cat {
    width: 180px;
}

/* buttons */
.buttons {
    display: flex;
    justify-content: center;
    gap: 30px;
    position: relative;
}

.no-wrapper{
    position:relative;
}

.btn {
    width: 120px;
    cursor: pointer;
    user-select: none;
}

.yes-btn,
.no-btn {
width: 120px;
height: auto;
display: inline-block;
}

.yes-btn {
    position: relative;
    z-index: 2;
    transform-origin: center center;
    transition: transform 0.3s ease;
}

.no-btn {
    z-index: 1;
    position: relative;
    transition: transform 0.15s ease;
    cursor: default;
}

.final-text{
    font-size: 22px;
    line-height: 1.4;
    text-align: center;
    display: inline-block;
    padding: 10px 20px;
    background-color: rgba(255,240,240,0.5);
    border-radius: 12px;
}

const envelope = document.getElementById("envelope-container");
const letter = document.getElementById("letter-container");
const noBtn = document.querySelector(".no-btn");
const yesBtn = document.querySelector(".btn[alt='Yes']");

const title = document.getElementById("letter-title");
const catImg = document.getElementById("letter-cat");
const buttons = document.getElementById("letter-buttons");
const finalText = document.getElementById("final-text");



envelope.addEventListener("click", () => {
    envelope.style.display = "none";
    letter.style.display = "flex";

    setTimeout( () => {
        document.querySelector(".letter-window").classList.add("open");
    },50);
});



noBtn.addEventListener("mouseover", () => {
    const min = 200;
    const max = 200;

    const distance = Math.random() * (max - min) + min;
    const angle = Math.random() * Math.PI * 2;

    const moveX = Math.cos(angle) * distance;
    const moveY = Math.sin(angle) * distance;

    noBtn.style.transition = "transform 0.3s ease";
    noBtn.style.transform = translate(${moveX}px, ${moveY}px);
});

// Logic to make YES btn to grow

// let yesScale = 1;

// yesBtn.style.position = "relative"
// yesBtn.style.transformOrigin = "center center";
// yesBtn.style.transition = "transform 0.3s ease";

// noBtn.addEventListener("click", () => {
//     yesScale += 2;

//     if (yesBtn.style.position !== "fixed") {
//         yesBtn.style.position = "fixed";
//         yesBtn.style.top = "50%";
//         yesBtn.style.left = "50%";
//         yesBtn.style.transform = translate(-50%, -50%) scale(${yesScale});
//     }else{
//         yesBtn.style.transform = translate(-50%, -50%) scale(${yesScale});
//     }
// });

// YES is clicked

yesBtn.addEventListener("click", () => {
    title.textContent = "Yippeeee!";

    catImg.src = "cat_dance.gif";

    document.querySelector(".letter-window").classList.add("final");

    buttons.style.display = "none";

    finalText.style.display = "block";
});
