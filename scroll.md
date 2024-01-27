# scroll

1) **عمل شريط في الاعلى وهذا الشريطة كلما نزلت للاسقل يزداد عرضه وعندما تصل الى النهاية يكون اكتمل الشريط على عرض الصفحة**


```html
<body>
	<div class="scroller"></div>
	<script src="main.js"></script>
</body>
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

<body>
	<div class="scroller">up</div>
	<script src="main.js"></script>
</body>
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
--------------------------------------------------------------------------------------------------------------------

3) **عندما اعمل scroll للصفحة عند نصل الى قسم معين يبدا العداد**

```html
	<section class="one">Section One</section>
	<section class="two">Section Two</section>
	<section class="three">
	  <div class="nums">
		<div class="num" data-goal="100">0</div>
		<div class="num" data-goal="500">0</div>
		<div class="num" data-goal="300">0</div>
	  </div>
	</section>
	<section class="four">Section Four</section>
```



```css
* {
  box-sizing: border-box;
}
body {
  font-family: "Trebuchet MS", "Lucida Sans Unicode", sans-serif;
  margin: 0;
}
section {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
section:first-child {
  background-color: #aaa;
}
section:nth-child(2) {
  background-color: #bbb;
}
section:nth-child(3) {
  background-color: #ccc;
}
section:last-of-type {
  background-color: #eee;
}
.nums {
  width: 400px;
  display: flex;
}
.nums .num {
  flex: 1;
  text-align: center;
  font-size: 40px;
  padding: 20px;
}

```



```javascript
let counter = [...document.getElementsByClassName("num")];
let section = document.getElementsByClassName("three")[0];

window.addEventListener("scroll",()=>{

	if(window.scrollY >=section.offsetTop){

		counter.forEach(element => {
			let goal = element.getAttribute("data-goal");
			let increase = setInterval(()=>{
					if(element.textContent === goal){
						clearInterval(increase);
					}else{
						element.textContent++;
					}
			},2000/goal)
		});
	}
	
})



```




