# math randow application 
**2) random number **
```javascript
function rang(min,max){
	return (Math.floor(Math.random() * (max-min+1)) + min);
 }
```

------------------------------------------------------------------------------------------------
**2) random color**
```javascript

//------------------------------------------using array-----------------------------------------------//

function changeColor(){
	let array = [0,1,2,3,4,5,6,7,8,9,"A","B","C","D","E","F"];
	let newArray = [];

	let i = 0 ;
	while(i < 6){

		newArray.push(array[Math.floor(Math.random() * array.length )]);
		i++;
	}

	let color = `#${newArray.join("")}`

		document.body.style.backgroundColor = color;

}


//------------------------------------------using string-----------------------------------------------//

function changeColor(){
	let str ="0123456789ABCDEF"
	let newstr="";

	let i = 0 ;
	while(i < 6){

		newstr +=str[Math.floor(Math.random() * str.length)] 
		i++;
	}

	let color = `#${newstr}`

		document.body.style.backgroundColor = color;

}


```
