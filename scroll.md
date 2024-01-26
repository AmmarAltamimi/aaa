# scroll

1) **عمل شريط في الاعلى وهذا الشريطة كلما نزلت للاسقل يزداد عرضه وعندما تصل الى النهاية يكون اكتمل الشريط على عرض الصفحة**


```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta http-equiv="X-UA-Compatible" content="IE=edge">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Task List 2021</title>

	<link rel="stylesheet" href="main.css" />
</head>
<body>
	<div class="scroller"></div>
	<script src="main.js"></script>
</body>
</html>
```

``css
.scroller{
    background-color: blueviolet;
    position: fixed;
    top: 0;
    left: 0;
    height: 4px;
    /* عرض الشريط والذي ناتي به بالنسبة */
    width: 0px ; 
    z-index: 99999;

}

body{
    /* نفرض ارتفاع لانه لايوجد تصميم  */
    height: 9000px; 
}

```

```javascript
 let scroll = document.querySelector(".scroller");
let scrollHeight = document.documentElement.scrollHeight;
let clientHeight = document.documentElement.clientHeight;
let hideHide = scrollHeight - clientHeight;

window.addEventListener("scroll",()=>{
let scrollTop = document.documentElement.scrollTop;
scroll.style.width = `${(scrollTop / hideHide) * 100}%` ;


})
```

