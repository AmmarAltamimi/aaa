```html
<!DOCTYPE html>
<!-- Coding By CodingNepal - codingnepalweb.com -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!----======== CSS ======== -->
    <link rel="stylesheet" href="main.css">

   <title>Accordion in HTML CSS & JavaScript</title>
</head>
<body>

<textarea name="" id="" ></textarea>    
    <script src="main.js"></script>
</body>
</html>
```


```css
textarea{
  resize: none;
}

textarea::-webkit-scrollbar{
  width: 0;
}

```

```javascript
let text = document.querySelector("textarea");

text.addEventListener("keyup",()=>{
text.style.height = "auto";
    text.style.height=`${text.scrollHeight}px`
    
})

```
