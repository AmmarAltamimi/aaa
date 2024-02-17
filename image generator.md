```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="main.css">
  <style>
  </style>
  <title>OpenAI Image Generator</title>
</head>
<body>
  <header>
    <div class="navbar">
      <div class="logo">
        <h2>OpenAI Image Generator</h2>
      </div>
      <div class="nav-links">
        <ul>
          <li>
            <a href="https://beta.openai.com/docs" target="_blank">OpenAI API Docs</a>
          </li>
        </ul>
      </div>
    </div>
  </header>

  <main>
    <section class="showcase">
      <div id="image-form">
        <h1>Describe An Image</h1>
        <div class="form-control">
          <input type="text" id="prompt" placeholder="Enter Text">
        </div>
        <div class="form-control">
          <input type="number" id="number" placeholder="Enter Image Number">
        </div>
        <!-- size -->
        <div class="form-control">
          <select name="size" id="size">
            <option value="small">Small</option>
            <option value="medium" selected>Medium</option>
            <option value="large">Large</option>
          </select>
        </div>
        <button class="btn">Generate</button>
      </div>
    </section>

    <section class="image">
      <div class="image-container"></div>
      <div class="image-container"></div>
      <div class="image-container"></div>
    </section>
  </main>
  <script src="main.js"></script>
</body>
</html>

```




```css
body {
  margin: 0;
  padding: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f9f9f9;
  color: #333;
}

header {
  background-color: #2c3e50;
  color: #fff;
  padding: 10px 0;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.logo h2 {
  margin: 0;
  font-size: 24px;
}

.nav-links ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.nav-links ul li {
  display: inline-block;
  margin-left: 20px;
}

.nav-links ul li a {
  color: #fff;
  text-decoration: none;
  font-size: 16px;
  transition: color 0.3s ease;
}

.nav-links ul li a:hover {
  color: #ffd700;
}

.showcase {
  text-align: center;
  padding: 50px 20px;
}

.showcase h1 {
  margin-bottom: 20px;
  font-size: 32px;
  color: #333;
}

.form-control {
  margin-bottom: 20px;
}

.form-control input[type="text"],
.form-control input[type="number"],
.form-control select {
  width: 100%;
  padding: 12px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 5px;
  font-size: 16px;
  transition: border-color 0.3s ease;
}

.form-control input[type="text"]:focus,
.form-control input[type="number"]:focus,
.form-control select:focus {
  outline: none;
  border-color: #1a1a1a;
}

.btn {
  background-color: #2980b9;
  color: #fff;
  padding: 12px 20px;
  border: none;
  cursor: pointer;
  border-radius: 5px;
  font-size: 16px;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: #3498db;
}

.image {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}

.image-container {
  margin: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 10px;
  overflow: hidden;
  background-color: #fff;
  transition: box-shadow 0.3s ease;
}

.image-container:hover {
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
}

.image-container img {
  max-width: 100%;
  height: auto;
  display: block;
}

```

```javascript
let textInput = document.querySelector("[type='text']");
let numberInput = document.querySelector("[type='number']");
let sizeInput = document.querySelector("[name='size']");
let buttonInput = document.querySelector(".btn");
let img = document.querySelector(".image");
// console.log(textInput,numberInput,sizeInput,buttonInput,img)



buttonInput.addEventListener("click",()=>{
    let textValue = textInput.value;
    let numberValue = +numberInput.value;
    let sizeValue = sizeInput.value;
    let size;
    if(sizeValue === "small"){
         size = "512x512"

    }else if(sizeValue === "medium"){
         size = "512x512"

    }else{
        
         size = "512x512"
    }
    let api = "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";
    methods = {
        method : "POST",
        headers : {
            "Content-Type" :"application/json",
            "Authorization" : `Bearer ${api}`
        },
        body:JSON.stringify({
            "prompt" : textValue,
            "n" : numberValue,
            "size" : size


        })
    }

    fetch("https://api.openai.com/v1/images/generations ",methods).then((data)=>{
        let imgJ= data.json();
        return imgJ;
    }).then((result)=>{
        console.log(result)
    })

})
```
