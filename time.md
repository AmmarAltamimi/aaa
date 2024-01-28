# time and data
**1) عمل عداد تناقص يعني countdown**

```html
	<section class="one"></section>
	<section class="two"></section>
	<section class="three">
		<div> days
		<span class="days"></span>
			</div>
			<div> hours
				<span class="hours"></span>
			</div>
			<div> mins
		<span class="minutes"></span>
			</div>

			<div>sec
		<span class="seconds"></span>
		</div>
```


```javascript
setInterval(()=>{
	let spans = document.querySelectorAll("span");
let dateNow = new Date()
let waitingDate = new Date("2024,2,15 6:45:34");

let diff=waitingDate-dateNow;
let days = Math.floor(diff / (1000 * 60 * 60 *24));
let hours = Math.floor(diff % (1000 * 60 *60 *24) / (1000 * 60 *60));
let mins = Math.floor(diff % (1000 * 60 *60) / (1000 * 60));
let sec = Math.floor(diff % (1000 * 60 ) / (1000));

let array = [days, hours,mins,sec];

spans.forEach((el,i)=>{
	el.innerHTML = array[i] >=10 ? array[i]:`0${ array[i]}` ;
})

},1000)


```
   
