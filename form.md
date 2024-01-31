# form 

**1)حساب عدد الحروف المتبقية لك في الحقل + عمل شريط يمثل نسبة الحروف المكتوب**
```html
	<form action="">
		<div>
		  <input type="text" placeholder="Your Username" maxlength="20" />
		  <span class="progress"></span>
		  <span class="count">30</span>
		</div>
	  </form>		
```


```css
* {
    box-sizing: border-box;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
  }
  div {
    width: 300px;
    margin: 20px auto;
  }
  input {
    padding: 15px;
    width: 100%;
    border: none;
    border-bottom: 2px solid #d7d7d7;
    background-color: #fbfbfb;
  }
  input:focus {
    outline: none;
  }
  .progress {
    background-color: #2196f3;
    height: 2px;
    width: 0;
    display: block;
    position: relative;
    top: -2px;
    transition: 0.5s;
  }
  .count {
    display: block;
    text-align: right;
    font-size: 12px;
    padding: 5px;
  }
  .zero {
    font-weight: bold;
    color: red;
  }
```


```javascript
let input = document.querySelector("input");
let progress = document.querySelector(".progress");
let count = document.querySelector(".count");
console.log(progress)
// when insert in input
input.addEventListener("input",()=>{
countRemainingLetter(input.value);
progress.style.width = `${((input.value.length) / input.maxLength) * 100}%`;

})


function countRemainingLetter(inputValue){
//get maxLength
let maxLengthValue = input.maxLength;
//get inputValueLength
let inputValueLength = inputValue.length;
//put the diff in count to see how much remaining
count.innerHTML = maxLengthValue - inputValueLength;
//change color when count 0
if(maxLengthValue - inputValueLength === 0){
count.classList.add("zero");
}
else{
	count.classList.remove("zero");
}
}

```
