# slider img

**1)التطبيق الاول**

```html
	<div class="slider-container">
		<div id="slide-number" class="slide-number"></div>
		<img decoding="async"  src="01.jpg" alt="" />
		<img decoding="async" src="02.jpg" alt="" />
		<img decoding="async" src="03.jpg"" alt="" />
		<img decoding="async" src="04.jpg"" alt="" />
		<img decoding="async" src="05.jpg"" alt="" />
	  </div>
	  <div class="slider-controls">
		<span id="prev" class="prev">Previous</span>
		<span id="indicators" class="indicators"></span>
		<span id="next" class="next">Next</span>
	  </div>
```





```css
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Tahoma, Arial;
  }
  .slider-container {
    margin: 10px auto;
    width: 800px;
    height: 250px;
    position: relative;
  }
  .slider-container img {
    position: absolute;
    opacity: 0;
    transition: opacity 1s;
    z-index: 1;
    max-width: 150px;
  }
  .slider-container img.active {
    opacity: 1;
  }
  .slider-container .slide-number {
    position: absolute;
    left: 10px;
    top: 10px;
    background-color: rgba(0, 0, 0, .6);
    color: #FFF;
    padding: 5px 10px;
    font-size: 20px;
    z-index: 2;
    border-radius: 6px;
  }
  .slider-controls {
    width: 800px;
    margin: auto;
    overflow: hidden;
  }
  .slider-controls .prev,
  .slider-controls .next {
    background-color: #009688;
    color: #FFF;
    font-size: 16px;
    text-align: center;
    cursor: pointer;
    border-radius: 4px;
    padding: 5px;
    user-select: none;
    width: 20%;
  }
  .slider-controls .prev {
    float: left;
  }
  .slider-controls .next {
    float: right;
  }
  .slider-controls .prev.disabled,
  .slider-controls .next.disabled {
    background-color: rgba(0, 150, 136, 0.5);
    cursor: no-drop;
  }
  .slider-controls .indicators {
    width: 60%;
    float: left;
  }
  .slider-controls .indicators ul {
    list-style: none;
    margin: 0;
    text-align: center;
  }
  .slider-controls .indicators ul li {
    display: inline-block;
    background-color: #F6F6F6;
    color: #333;
    font-weight: bold;
    height: 28px;
    width: 28px;
    border-radius: 4px;
    margin: 0 2px;
    line-height: 28px;
    cursor: pointer;
  }
  .slider-controls .indicators ul li.active {
    background-color: #009688;
    color: #FFF;
  }
```






```javascript
let sliderImg = document.querySelectorAll(".slider-container img");
let sliderNo = document.querySelector(".slider-container .slide-number");
let sliderPrev = document.querySelector(".slider-controls .prev");
let sliderNext = document.querySelector(".slider-controls .next");
let sliderIndicators = document.querySelector(".slider-controls .indicators");


//add ul amd li to page
let sliderUl = document.createElement("ul");
sliderUl.setAttribute('id', 'pagination-ul');
for(let i = 1 ; i<=sliderImg.length ;  i++ ){

  let slideCreate= document.createElement("li");
  slideCreate.setAttribute("data-value",i)
  slideCreate.appendChild(document.createTextNode(i));
  sliderUl.appendChild(slideCreate);
}
sliderIndicators.append(sliderUl);

//call li and action click
let sliderLi = document.querySelectorAll("#pagination-ul li");


//get index from storage
window.addEventListener("load",()=>{
  if(window.localStorage.getItem("ele")){
    let da = JSON.parse(window.localStorage.getItem("ele"))
    sliderLi[da].click()
  }
  
  else{
//function at beginning
    defaultFunction();
  }  
})

//click on li 
sliderLi.forEach((li,index) => {
  li.addEventListener("click",()=>{

 //remove active class from all li and add it to select li 
 removeAddActiveList(li);

 //remove active class from all img and add it to select img 
 removeAddActiveImg(index);

//prev button 
prevButton(index);

//next button 
nextButton(index);

// no of img we are 
sliderNumber(index);

//save index from storage
window.localStorage.setItem("ele",JSON.stringify(index));

  })
});

//function when ypu click on sliderPrev
sliderPrev.addEventListener("click",sliderPrevFunction)

//function when ypu click on sliderNext
sliderNext.addEventListener("click",sliderNextFunction)


//----------------all function bellow ---------------|

//function at beginning
function defaultFunction(){
  sliderImg[0].className = "active";
  sliderLi[0].className = "active";
  sliderNo.innerHTML =`#slider 1 / ${sliderImg.length} `;
  sliderPrev.classList.add("disabled");
}




 //remove active class from all li and add it to select li 
function removeAddActiveList(li){
sliderLi.forEach((list)=>{
 list.classList.remove("active")
})
li.classList.add("active")

}



 //remove active class from all img and add it to select img 
function removeAddActiveImg(index){
sliderImg.forEach((img)=>{
  img.classList.remove("active")
})
sliderImg[index].classList.add("active")

}




//prev button 
function prevButton(index){
if(index === 0){
  sliderPrev.classList.add("disabled");
}else{
  sliderPrev.classList.remove("disabled");
}
}



//next button 
function nextButton(index){
if(index === sliderImg.length-1){
  sliderNext.classList.add("disabled");
}else{
  sliderNext.classList.remove("disabled");
}
}




// no of img we are 
function sliderNumber(index){
sliderNo.innerHTML=`#slider ${index + 1} / ${sliderImg.length}`
}


//function when ypu click on sliderPrev
function sliderPrevFunction(){
    let liActive = document.querySelector("li.active");
    if( +liActive.getAttribute("data-value") === 1){
      return;
    }else
    {
      liActive.previousElementSibling.click()
    }
  }


  //function when ypu click on sliderNext
  function sliderNextFunction(){
 
    let liActive = document.querySelector("li.active");
    if( +liActive.getAttribute("data-value") === sliderImg.length){
      return;
    }
    else{
      liActive.nextElementSibling.click()
    }
  }














// const members = [
// 	{ id: 1, name: 'John' },
// 	{ id: 2, name: 'Jane' },
// 	{ id: 1, name: 'Johnny' },
// 	{ id: 4, name: 'Alice' },
//   ];

//   let ammar = members.map((m) => [m.id, m]);
//   console.log(ammar);

//   const unique = [...new Map(ammar).values()];
// console.log(unique)



// const ammar = [];
// const newone =[];

// for(let i = 0 ;  i < members.length;i++){

// 	if(!ammar.includes(members[i].id)){
// 		ammar.push(members[i].id)
// 		newone.push(members[i]);

// 	}
// }
	
// console.log(newone)





// const members = [1,2,3,1,2];
// const ammar = [];


// for(let i = 0 ;  i < members.length;i++){

// 	if(i ===members.findIndex(e=>(members[i]===e))){
// 		ammar.push(members[i]);

// 	}
// }
	
// console.log(ammar)

```
