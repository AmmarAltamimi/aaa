# image Editor

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Image Editor</title>

    <link rel="stylesheet" href="main.css" />
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.2/css/all.min.css"
      integrity="sha512-z3gLpd7yknf1YoNbCzqRKc4qyor8gaKU1qmn+CShxbuBusANI9QpRohGBreCFkKxLhei6S9CQXFEbbKuqLg0DA=="
      crossorigin="anonymous"
      referrerpolicy="no-referrer"
    />

    <script src="main.js" defer></script>
  </head>
  <body>
    <div class="container">
      <h1>image editor</h1>
      <!-- start filter options & view -->
      <div class="options-and-view">
        <!-- start options -->
        <div class="options">
          <div class="filter-options">
            <h2>filters</h2>
            <button class="active" data-filter="brightness">brightness</button>
            <button data-filter="saturate">saturation</button>
            <button data-filter="invert">inversion</button>
            <button data-filter="grayscale">grayscale</button>
          </div>

          <div class="current-filter">
            <div class="box active" data-filter="brightness">
              <p class="name">brightness</p>
              <p class="precent">100%</p>
              <input
                type="range"
                id="current-filter-range"
                min="0"
                max="100"
                value="100"
              />
            </div>
            <div class="box" data-filter="saturate">
              <p class="name">saturation</p>
              <p class="precent">100%</p>
              <input
                type="range"
                id="current-filter-range"
                min="0"
                max="100"
                value="100"
              />
            </div>
            <div class="box" data-filter="invert">
              <p class="name">inversion</p>
              <p class="precent">0%</p>
              <input
                type="range"
                id="current-filter-range"
                min="0"
                max="100"
                value="0"
              />
            </div>
            <div class="box" data-filter="grayscale">
              <p class="name">grayscale</p>
              <p class="precent">0%</p>
              <input
                type="range"
                id="current-filter-range"
                min="0"
                max="100"
                value="0"
              />
            </div>
          </div>
        </div>
        <!-- end options -->

        <!-- start view -->
        <img src="" alt="">
        <canvas class="view"> </canvas>
        <!-- end view -->
      </div>
      <!-- end filter options & view -->

      <!-- start file options options -->
      <div class="reset-and-file">
        <button class="reset">reset filters</button>
        <div class="file-options">
          <label for="img-input">select image</label>
          <input
            type="file"
            id="img-input"
            accept="image/jpg, image/png, image/jpeg"
          />
          <button class="remove-img">remove</button>
          <a class="save" download="editedImg" href="">save image</a>
        </div>
      </div>
      <!-- end file options options -->
    </div>
  </body>
</html>

```


```css
@import url("https://fonts.googleapis.com/css2?family=Lato:wght@300;400;700&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}

:root {
  --bg-clr: #e3f2fd;
  --blue: #5272e3;
  --gray: #6a757c;
}

a {
  text-decoration: none;
}

body {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: var(--bg-clr);
  font-family: "Lato", sans-serif;
  /* overflow: hidden; */
}

.container {
  width: clamp(60%, 700px, 100%);
  display: flex;
  flex-direction: column;
  gap: 1rem;
  background-color: white;
  padding: 1.5rem 2rem;
  margin: 1rem 0;
  border-radius: 4px;
  text-transform: capitalize;
}

.options-and-view {
  display: flex;
  gap: 1rem;
}

@media (max-width: 1112px) {
  .options-and-view {
    flex-direction: column;
  }
}

.options-and-view > * {
  border-radius: 4px;
}

.options-and-view .options {
  padding: 1.5rem 1rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  border: 1px solid var(--gray);
}

.options-and-view .options h2 {
  margin-bottom: 1rem;
}

.options-and-view .options .filter-options {
  display: grid;
  gap: 0.5rem;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 1fr 1fr 1fr;
}

.options-and-view .options .filter-options h2 {
  grid-column: 1/3;
}

.options-and-view .options .filter-options button {
  padding: 0.5rem 1rem;
  text-transform: capitalize;
  background-color: white;
  border: 1px solid var(--gray);
  color: var(--gray);
  font-size: 1rem;
  border-radius: 3px;
  cursor: pointer;
  transition: 0.3s;
}

.options-and-view .options .filter-options button:hover {
  background-color: var(--bg-clr);
}

.options-and-view .options .filter-options button.active {
  background-color: var(--blue);
  color: white;
  border-color: var(--blue);
}

.options-and-view .options .current-filter .box {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.5rem;
  display: none;
}

.options-and-view .options .current-filter .box.active {
  display: grid;
}

.options-and-view .options .current-filter .precent {
  text-align: end;
}

.options-and-view .options .current-filter input[type="range"] {
  grid-column: 1/3;
  background-color: var(--blue);
  cursor: grab;
}


  .options-and-view .view{
  border: 1px solid var(--gray);
  flex: 1 1;
  width: 600px;
  height: 300px;
  margin: auto;
}

.reset-and-file {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 1rem;
}

.reset-and-file :is(button, label, a) {
  padding: 0.5rem 1rem;
  text-transform: capitalize;
  background-color: white;
  border: 1px solid var(--gray);
  color: var(--gray);
  font-size: 1rem;
  border-radius: 3px;
  cursor: pointer;
  transition: 0.3s;
}

.reset-and-file :is(button, label, a):hover {
  background-color: var(--bg-clr);
}

.reset-and-file .file-options {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.reset-and-file .file-options input[type="file"] {
  display: none;
}

.reset-and-file .file-options .save {
  color: white;
  background-color: var(--blue);
}

.file-options .remove-img {
  background-color: red;
  color: white;
  border-color: transparent;
}

.file-options .remove-img:hover {
  color: var(--gray);
  border-color: var(--gray);
}

#accepted-img {
  position: absolute;
  z-index: -10;
  opacity: 0;
  transform: scale(0.1, 0.1);
}

```


```javascript
let allButton = document.querySelectorAll(".filter-options button");
// let brightnessButton = document.querySelector("[data-filter='brightness']");
// let saturateButton = document.querySelector("[data-filter='saturate']");
// let invertButton = document.querySelector("[data-filter='invert']");
// let grayscaleButton = document.querySelector("[data-filter='grayscale']");

let filterRangDiv = document.querySelectorAll(".current-filter div");
let filterRang = document.querySelectorAll(".current-filter input");
let filterBrightness = document.querySelector("[data-filter='brightness'] input");
let filterSaturate = document.querySelector("[data-filter='saturate'] input");
let filterInvert = document.querySelector("[data-filter='invert'] input");
let filterGrayscale = document.querySelector("[data-filter='grayscale'] input");

let inputPrecent = document.querySelectorAll(".precent");

let reset = document.querySelector(".reset");
let select = document.querySelector("#img-input");
let remove = document.querySelector(".remove-img")
let save = document.querySelector(".save");


let img = document.querySelector("img");
let canvas = document.querySelector("canvas");
let ctx = canvas.getContext("2d");


// console.log(select);

allButton.forEach((btn,i)=>{
    btn.addEventListener("click",()=>{

        
        allButton.forEach((button)=>{
            button.classList.remove("active")
        })
        allButton[i].classList.add("active")



        filterRangDiv.forEach((rang)=>{
            rang.classList.remove("active")
        })
        filterRangDiv[i].classList.add("active")



    })
})



reset.addEventListener("click",()=>{
    restFilter();
})


select.addEventListener("change",()=>{
    let file = new FileReader();
    file.readAsDataURL(select.files[0]);
    file.addEventListener("load",()=>{
        img.src=file.result;

    })

})

img.addEventListener("load",()=>{
    canvas.width = img.width;
    canvas.height=img.height;
    ctx.drawImage(img,0,0,canvas.width,canvas.height);
    img.style.display="none";

})

filterRang.forEach((rang)=>{
    rang.addEventListener("input",()=>{

    calucaltePrecent(rang);

    ctx.filter=`
        saturate(${filterSaturate.value}%)
        brightness(${filterBrightness.value}%)
        grayscale(${filterGrayscale.value}%)
        invert(${filterInvert.value}%)
    
    `
    ctx.drawImage(img,0,0,canvas.width,canvas.height);

    })
})

remove.addEventListener("click",()=>{
    img.removeAttribute("src")
})


save.addEventListener("click",()=>{
    save.href = canvas.toDataURL("")
})






// -------------functions-------------//


function restFilter (){
    filterRang[0].value = 100;
    filterRang[1].value = 100;
    filterRang[2].value = 0;
    filterRang[3].value = 0;

    img.style.filter=`
    saturate(${filterSaturate.value}%)
    brightness(${filterBrightness.value}%)
    grayscale(${filterGrayscale.value}%)
    invert(${filterInvert.value})

`

    inputPrecent[0].innerHTML="100%";
    inputPrecent[1].innerHTML="100%";
    inputPrecent[2].innerHTML="0%";
    inputPrecent[3].innerHTML="0%";
}


function calucaltePrecent(rang){
rang.previousElementSibling.innerHTML=`${Math.floor(((rang.value)/rang.getAttribute("max")) * 100)}%`
}



```







