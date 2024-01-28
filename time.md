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
-------------------------------------------------------------------------------------

**2) عمل الوقت والتاريخ** : توجد طريقتين لعمل الوقت والتاريخ :

*أ) عن طريق دوال جاهزة : في هذه الطريقة لايمكن التعديل على الشكل الذي يظهر فيه التاريخ والوقت كالتالي :*

```html
	<section class="one"></section>
	<section class="two"></section>
```


```javascript
setInterval(()=>{
	let section1 = document.querySelector(".one");
	let section2 = document.querySelector(".two");
	let d = new Date();
	section1.innerHTML=d.toLocaleTimeString();
	section2.innerHTML=d.toLocaleDateString();
},1000)

```

*ب) عن طريق اكواد  : في هذه الطريقة تضيف الوقت والتاريخ بالاكواد الخاصة فيه كالتالي :*



```html
	<section class="data">
		<span class="dayWeek"></span>,
		<span class="month"></span>
		<span class="day"></span>,
		<span class="year"></span>
	</section>
	<section class="time">
		<span class="hours"></span>:
		<span class="mins"></span>:
		<span class="sec"></span>
		<span class="AMPM"></span>
	</section>
```


```javascript

	let spans = document.querySelectorAll("span")

	let dateTime = new Date();
	// get daysWeek
		let dayWeekIndex = dateTime.getDay();
		let dayWeek =['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday'];

	// get day
	let day = dateTime.getDate();

	// get months
	let MonthIndex = dateTime.getMonth();
	let months =  ["January","February","March","April","May","June","July",
	"August","September","October","November","December"];

	// get year
	let year = dateTime.getFullYear();

	//get hour
	let hour = dateTime.getHours();

	//get min
	let min = dateTime.getMinutes();

	//get sec
	let sec = dateTime.getSeconds();

	//get AM & PM
	let AmPm = hour >= 12 ? "PM":"AM";

	
	//change format if you want
	if( hour > 12 || hour === 0){
		hour = Math.abs(hour - 12); // Math => 0 - 12 = -12 
	}
	//---------------


//change 1 ,2 3,... to 01,02,03
function changeNum(num){
	 return num = num >= 10 ? num : `0${num}`;
}
day =  changeNum(day)
hour =  changeNum(hour)
min =  changeNum(min)
sec =  changeNum(sec)
//-----------------


	//add to page
	let collection = [dayWeek[dayWeekIndex],months[MonthIndex],day,year,hour,min,sec,AmPm];
	spans.forEach((el,i)=>{
	el.innerHTML=collection[i]
	
	})
	//-------------
	
},1000)


```

