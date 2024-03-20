# math randow application 
**1) random number**
```javascript
function rang(min,max){
	return (Math.floor(Math.random() * (max-min+1)) + min);
 }
```

------------------------------------------------------------------------------------------------
**2) random color with out array**
```html
<div></div>
<p></p>
```

```css
body{
  display: flex;
  justify-content: center;
  align-items: center;

}


div,p{
  width: 400px;
  height: 400px;
background-color: red;
margin-right: 20px;
}
```

```javascript
let first = Math.round(Math.random() *360);
let second = Math.round(Math.random() *100);
let third = Math.round(Math.random() *100);

document.body.style.backgroundColor=`hsl(${first},${second}%,${third}%)`

document.querySelector("div").style.backgroundColor=`rgb(${third},${second},${first})`


let hex = Math.random().toString(16);
let color = hex.slice(2,8);

document.querySelector("p").style.backgroundColor=`#${color}`

```

-------------------------------------------------------------------------------------------------
**3) random color with array or string**
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
------------------------------------------------------------------------------------------------
**4) random element fron serial with array**
```javascript

let arr = ["Ahmed", "Sayed", "Ali"];

console.log(arr[Math.trunc(Math.random() * arr.length)]);
```
------------------------------------------------------------------------------------------------
**5) random password with array or string**
```javascript
//note => تدخل طول كلمة السر + والاجابة بنعم او لا هل الحالة التي تريد ان تشملها كلمة السر مثال هل تريد فيها حروف كبيرة لانه بنعمل شرط فيما بعد انه اذا كانت الاجابة لا مابضيفه في المصفوفة او النص الذي اريد ان انشي به كلمة السر
function generatePassword(length, includeLowercase, includeUppercase, includeNumbers, includeSymbols){ 

	// note => تم التفصيل هنا حتى نختار ايش الذي تريده في كلمة السر مثلا هل حروف كبيرة تشملها كلمة السر او لا .. في بعض الحالات الاخرى قد نفصل حتى مثلا نختار عشوائي حرف من كل كلمة سر حتى تشمل كلمة السر كل الحالات (لايوجد مثال هنا) 
    const lowercaseChars = "abcdefghijklmnopqrstuvwxyz";
    const uppercaseChars = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const numberChars = "0123456789";
    const symbolChars = "!@#$%^&*()_+-=";

    let allowedChars = "";
    let password = "";

//note => اضافة الحالات التي تريدها في كلمة السر الى المتغير الذي يشمل كل الحالات

    allowedChars += includeLowercase ? lowercaseChars : "";
    allowedChars += includeUppercase ? uppercaseChars : "";
    allowedChars += includeNumbers ? numberChars : "";
    allowedChars += includeSymbols ? symbolChars : "";

//note => اذا الطول الذي دخله اقل من صفر

    if(length <= 0){
        return `(password length must be at least 1)`;
    }

//note => اذا كل الاجبات كانت لا بالتالي كيف بانشا كلمة السر

    if(allowedChars.length === 0){
        return `(At least 1 set of character needs to be selected)`;
    }

//note =>  عمل كلمة السر حسب الطول الذي عملته

    for(let i = 0; i < length; i++){
        const randomIndex = Math.floor(Math.random() * allowedChars.length);
        password += allowedChars[randomIndex];
    }

    return password;
}


//note => مثال على كلمة السر حبيث يعطي مدخلات من عنده للفانكشن

const passwordLength = 10;
const includeLowercase = true;
const includeUppercase = true;
const includeNumbers = true;
const includeSymbols = true;

const password = generatePassword(passwordLength, 
                                 includeLowercase, 
                                 includeUppercase, 
                                 includeNumbers, 
                                 includeSymbols);

console.log(`Generated password: ${password}`);

```
------------------------------------------------------------------------------------------------
**6)عرض جميع عناصر array بطريقة عشوائي وبدون تكرار اي عنصر**



```javascript
let randomIndexArray = [];
    while(array.length > randomIndexArray.length) {
        let randomIndex = Math.round(Math.random() * array.length);
        if(!randomIndexArray.includes(randomIndex)){
            randomIndexArray.push(randomIndex);
        }
    }

```

```javascript
let randomIndexArray = [];
    while(answers.length > 0){
        let random = Math.floor(Math.random() * answers.length);
        randomIndexArray.push(random);
        answers.splice(random,1);
   
```

