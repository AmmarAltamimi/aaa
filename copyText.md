# copy 
**1)من input الطريقة الاولى والثانية بكود مختلف في جافا اسكربيت:**

```html
  <div class="copy-link">
    <input type="text" class="copy-link-input" value="https://www.youtube.com/" readonly>
    <button type="button" class="copy-link-button">
   copy </button>
  </div>

```

```css
.copy-link {
  --height: 36px;

  display: flex;
  max-width: 250px;
}

.copy-link-input {
  flex-grow: 1;
  padding: 0 8px;
  font-size: 14px;
  border: 1px solid #cccccc;
  border-right: none;
  outline: none;
}

.copy-link-input:hover {
  background: #eeeeee;
}

.copy-link-button {
  flex-shrink: 0;
  width: var(--height);
  height: var(--height);
  display: flex;
  align-items: center;
  justify-content: center;
  background: #dddddd;
  color: #333333;
  outline: none;
  border: 1px solid #cccccc;
  cursor: pointer;
}

.copy-link-button:hover {
  background: #cccccc;
}

```


```javascript
    const inputField = document.querySelector(".copy-link-input");
    const copyButton = document.querySelector(".copy-link-button");
    const text = inputField.value;


    copyButton.addEventListener("click", () => {
        //copy the string
      inputField.select();
      navigator.clipboard.writeText(text);
  
      
        // show it is copy
      inputField.value = "Copied!";
      setTimeout(() => (inputField.value = text), 2000);
    });

  
```


```javascript
    const inputField = document.querySelector(".copy-link-input");
    const copyButton = document.querySelector(".copy-link-button");
    const text = inputField.value;


    copyButton.addEventListener("click", () => {
        //copy the string
      inputField.select();
        document.execCommand("copy")

        // show it is copy
      inputField.value = "Copied!";
      setTimeout(() => (inputField.value = text), 2000);
    });

  
```


**1)من innerhtml:**


```html
<html>
<head>
  <!-- Meta tags -->
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- Typed.js CSS -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/typed.js/2.0.12/typed.min.css">

  <link rel="stylesheet" href="main.css">

  <title>CRUDS</title>
</head>
<body>

  <div class="copy-link">
    https://www.youtube.com/
  </div>

  <script src="main.js"></script>
</body>
</html>

```

```css
div{
  width: 200px;
  height: 50px;
  background-color: blueviolet;
}
```

```javascript
    const div = document.querySelector("div");


    div.addEventListener("click", () => {
        //copy the string
      navigator.clipboard.writeText(div.innerHTML);

    });

  
```








