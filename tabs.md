# tabs

**1)التطبيق الاول**

```html

	  <!-- => note : فكرة لما يكون اتربيوت هو نفسه لما نستعي عنصر الاول عن طريق العنصر الثاني -->

	  <!-- <ul class="tabs">
		<li class="active" data-cont="one">Tab 1</li>
		<li data-cont="two">Tab 2</li>
		<li data-cont="three">Tab 3</li>
	  </ul>
	  <div class="content">
		<div class="one">Content 1</div>
		<div class="two">Content 2</div>
		<div class="three">Content 3</div>
	  </div>
 -->



	  <!-- => note : فكرة لما يكون اتربيوت هو قيمة استدعاء العنصر الثاني -->

<ul class="tabs">
	<li class="active" data-cont=".one">Tab 1</li>
	<li data-cont=".two">Tab 2</li>
	<li data-cont=".three">Tab 3</li>
  </ul>
  <div class="content">
	<div class="one">Content 1</div>
	<div class="two">Content 2</div>
	<div class="three">Content 3</div>
  </div> 

```


```css
body {
    font-family: Arial, Helvetica, sans-serif;
  }
  .tabs {
    display: flex;
    list-style: none;
    padding: 0;
    margin: 0;
  }
  .tabs li {
    padding: 10px;
    background-color: #f6f4f4;
    border-right: 1px solid white;
    cursor: pointer;
    transition: 0.2s;
  }
  .tabs li.active,
  .tabs li:hover {
    background-color: #ddd;
  }
  .content {
    background-color: #ddd;
  }
  .content > div {
    padding: 20px;
  }
  .content > div:not(:first-child) {
    display: none;
  }
```




```jacascript
//  => note : فكرة لما يكون اتربيوت هو نفسه لما نستعي عنصر الاول عن طريق العنصر الثاني

let tabs = document.querySelectorAll(".tabs li");
let content = document.querySelectorAll(".content div");



tabs.forEach(element => {
	element.addEventListener("click",()=>{

		// remove class active from all and add it to action element
		removeActive(element);


       //display none all element them give the block to what you click 
	   removeElement(element);



		
	});
	
	})


//-----------------------------------------------------
	function removeActive(element){
		tabs.forEach((ele)=>{
			ele.classList.remove("active");
		})
		element.classList.add("active");
	}



//----------------------------------------------------
	function removeElement(element){
		content.forEach((el)=>{
			el.style.display = "none"
		})

		content.forEach((ele)=>{
			if(ele.classList.contains(element.dataset.cont)){
				ele.style.display ="block";
			}
		})

	}








//  => note :  فكرة لما يكون اتربيوت هو قيمة استدعاء العنصر الثاني 


let tabs = document.querySelectorAll(".tabs li");
let content = document.querySelectorAll(".content div");



tabs.forEach(element => {
	element.addEventListener("click",()=>{

		// remove class active from all and add it to action element
		removeActive(element);


       //display none all element them give the block to what you click 
	   removeElement(element);



		
	});
	
	})


//-----------------------------------------------------
	function removeActive(element){
		tabs.forEach((ele)=>{
			ele.classList.remove("active");
		})
		element.classList.add("active");
	}



//----------------------------------------------------
	function removeElement(element){
		content.forEach((el)=>{
			el.style.display = "none"
		})

	document.querySelector(element.dataset.cont).style.display="block";

	}







//  => note :  فكرة لما يكون العنصر الاول والثاني لهم نفس ترتيب في الاب حق كل واحد منهم

let tabs = document.querySelectorAll(".tabs li");
let content = document.querySelectorAll(".content div");



tabs.forEach((element,i) => {
	element.addEventListener("click",()=>{

		// remove class active from all and add it to action element
		removeActive(element);


       //display none all element them give the block to what you click 
	   removeElement(element,i);



		
	});
	
	})


//-----------------------------------------------------
	function removeActive(element){
		tabs.forEach((ele)=>{
			ele.classList.remove("active");
		})
		element.classList.add("active");
	}



//----------------------------------------------------
	function removeElement(element,i){
		content.forEach((el)=>{
			el.style.display = "none"
		})
console.log(element)
		content[i].style.display="block";
	}



```




-------------------------------------------------------------------------------

**1)التطبيق الثاني**

```html

	  <!-- => note : فكرة لما يكون اتربيوت هو نفسه لما نستعي عنصر الاول عن طريق العنصر الثاني -->

	  <ul class="switcher">
		<li class="active" data-cat="all">All Work</li>
		<li data-cat="web">Web</li>
		<li data-cat="gfx">Graphic</li>
		<li data-cat="marketing">Marketing</li>
	  </ul>
	  <div class="gallery">
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
	  </div>




	  <!-- => note : فكرة لما يكون اتربيوت هو قيمة استدعاء العنصر الثاني -->

	   <ul class="switcher">
		<li class="active" data-cat=".all">All Work</li>
		<li data-cat=".web">Web</li>
		<li data-cat=".gfx">Graphic</li>
		<li data-cat=".marketing">Marketing</li>
	  </ul>
	  <div class="gallery">
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all web" src="https://via.placeholder.com/150/F00/FFF?text=Web" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all marketing" src="https://via.placeholder.com/150/000/FFF?text=Marketing" alt="" />
		<img decoding="async" class="all gfx" src="https://via.placeholder.com/150/00F/FFF?text=Graphic" alt="" />
	  </div>

```


```css
body {
    font-family: Arial, Helvetica, sans-serif;
  }
  .switcher {
    display: flex;
    justify-content: center;
    list-style: none;
    padding: 0;
  }
  .switcher li {
    padding: 10px 15px;
    font-weight: bold;
    cursor: pointer;
    background-color: #eee;
    min-width: 105px;
    text-align: center;
    transition: 0.2s;
  }
  .switcher li.active,
  .switcher li:hover {
    background-color: red;
    color: white;
  }
  .gallery {
    display: flex;
    flex-wrap: wrap;
    width: 800px;
    margin: auto;
  }
  .gallery img {
    margin-bottom: 10px;
    transition: 0.3s;
    margin-left: 5px;
    margin-right: 5px;
  }
```




```jacascript
//  => note : فكرة لما يكون اتربيوت هو نفسه لما نستعي عنصر الاول عن طريق العنصر الثاني

let switcher = document.querySelectorAll(".switcher li");
let content = document.querySelectorAll(".gallery img");


switcher.forEach(element => {
	element.addEventListener("click",()=>{

		// remove class active from all and add it to action element
		removeActive(element);


       //display none all element them give the block to what you click 
	   removeElement(element);



		
	});
	
	})


//-----------------------------------------------------
	function removeActive(element){
		switcher.forEach((ele)=>{
			ele.classList.remove("active");
		})
		element.classList.add("active");
	}



//----------------------------------------------------
	function removeElement(element){
		content.forEach((el)=>{
			el.style.display = "none"
		})

		content.forEach((ele)=>{
			if(ele.classList.contains(element.dataset.cat)){
				ele.style.display ="block";
			}
		})

	}










//  => note :  فكرة لما يكون اتربيوت هو قيمة استدعاء العنصر الثاني 




let switcher = document.querySelectorAll(".switcher li");
let content = document.querySelectorAll(".gallery img");


switcher.forEach(element => {
	element.addEventListener("click",()=>{

		// remove class active from all and add it to click element
		removeActive(element);

       //display none all element them give the block to what you click 
	   removeElement(element);	
	});
	
	})



	
	//-----------------------------------------

	function removeActive(element){
		switcher.forEach((ele)=>{
			ele.classList.remove("active");
		})
		element.classList.add("active");
	};


	//-----------------------------------------


	function removeElement(element){

		content.forEach((el)=>{
			el.style.display = "none"
		})
		document.querySelectorAll(element.dataset.cat).forEach((e)=>{
			e.style.display = "block";
		})

	}







```

