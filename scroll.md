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



```css
.scroller{
    background-color: blueviolet;
    position: fixed;
    top: 0;
    left: 0;
    height: 4px;

    /* note=> عرض الشريط والذي ناتي به بالنسبة */
    width: 0px ; 
    z-index: 99999;

}

body{
    /* note=>نفرض ارتفاع لانه لايوجد تصميم  */
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


------------------------------------------------------------------------------------------------------------------
2) **عمل زر بالاسفل عندما اعمل scroll للصفحة عند مسافة معينة يظهر عنصر وعندما اعمل اكشن عليه ينقلنا لموقع معين**

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
	<div class="scroller">up</div>
	<script src="main.js"></script>
</body>
</html>
```



```css
.scroller{
    background-color: blueviolet;
    position: fixed;
    bottom: 30PX;
    right: -50px;
    height: 40px;
    width: 40px ; 
    z-index: 99999;
    border-radius: 5px;
    font-size: 25px;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    transition: 0.5s;
    z-index: 999999;
}

.scroller.show{
    right: 20px;
}



body{
    height: 9000px; 
}

```



```javascript
let scroller = document.querySelector(".scroller");

window.addEventListener("scroll",()=>{
	if(window.scrollY >= 900){
		scroller.classList.add("show");
	}else{
		scroller.classList.remove("show")
	}
})

scroller.addEventListener("click",()=>{
	window.scrollTo({
		top : 0,
		behavior : "smooth",
	})
})


```


