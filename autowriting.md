# text effect

**1)عمل نص ويظهر جرف حرف كأنك تعمله بالكيبورد بطريقتين**
```html
<div class="one" data-con="I am Ammar Faroq Abdullah Altamimi From Yemen"></div>
```

```javascript
let div =document.querySelector(".one");
let paragraph = div.dataset.con;
let i=0;
let a = setInterval(()=>{

div.innerHTML +=paragraph[i];
i++;

if(i === paragraph.length ){
	clearInterval(a);
}
},100)

```


```javascript
let div =document.querySelector(".one");
let paragraph = div.dataset.con;
let i=1;
let a = setInterval(()=>{

div.innerHTML =paragraph.slice(0,i);
i++;

if(i === paragraph.length+1 ){

	clearInterval(a);
}

},100)
```

**2)عن طريق مكتبة تعملها في html ل type.js**

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
  <div>Im <span class="one"></span></div>

  <!-- Typed.js script -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/typed.js/2.0.12/typed.min.js"></script>

  <!-- Your custom JavaScript -->
  <script src="main.js"></script>
</body>
</html>

```

```javascript
let type = new Typed(".one", {
    strings: ["Ammar Altamimi", "From Yemen", "Web developer"],
    typeSpeed: 100,
    backSpeed: 100,
    loop: true
});

```

