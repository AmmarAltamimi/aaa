# validation form 

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="main.css">
  <style>
  </style>
  <title>Login</title>
</head>
<body>
  <div class="container">
    <div class="header">
      <h2>Create Account</h2>
    </div>
    <form id="form" class="form">
      <div class="form-control">
        <label for="username">Username</label>
        <input type="text" placeholder="ammar506" id="username" />
        <i class="fas fa-check-circle"></i>
        <i class="fas fa-exclamation-circle"></i>
        <small>Error message</small>
      </div>
      <div class="form-control">
        <label for="username">Email</label>
        <input type="email" placeholder="a@gmail.com" id="email" />
        <i class="fas fa-check-circle"></i>
        <i class="fas fa-exclamation-circle"></i>
        <small>Error message</small>
      </div>
      <div class="form-control">
        <label for="username">Password</label>
        <input type="password" placeholder="Password" id="password"/>
        <i class="fas fa-check-circle"></i>
        <i class="fas fa-exclamation-circle"></i>
        <small>Error message</small>
      </div>
      <div class="form-control">
        <label for="username">Password check</label>
        <input type="password" placeholder="confirm password" id="password2"/>
        <i class="fas fa-check-circle"></i>
        <i class="fas fa-exclamation-circle"></i>
        <small>Error message</small>
      </div>
      <input type="submit" value="Sign up">
    </form>
  </div>
  
  <script src="main.js"></script>
</body>
</html>

```


```css
@import url('https://fonts.googleapis.com/css?family=Muli&display=swap');
@import url('https://fonts.googleapis.com/css?family=Open+Sans:400,500&display=swap');

* {
	box-sizing: border-box;
}

body {
	background-color: #a699ac;
	font-family: 'Open Sans', sans-serif;
	display: flex;
	align-items: center;
	justify-content: center;
	min-height: 100vh;
	margin: 0;
}

.container {
	background-color: #fff;
	border-radius: 5px;
	box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
	overflow: hidden;
	width: 400px;
	max-width: 100%;
}

.header {
	border-bottom: 1px solid #f0f0f0;
	background-color: #f7f7f7;
	padding: 20px 40px;
}

.header h2 {
	margin: 0;
}

.form {
	padding: 30px 40px;	
}

.form-control {
	margin-bottom: 10px;
	padding-bottom: 20px;
	position: relative;
}

.form-control label {
	display: inline-block;
	margin-bottom: 5px;
}

.form-control input {
	border: 2px solid #f0f0f0;
	border-radius: 4px;
	display: block;
	font-family: inherit;
	font-size: 14px;
	padding: 10px;
	width: 100%;
}

.form-control input:focus {
	outline: 0;
	border-color: #777;
}

.form-control input.success {
	border-color: #2ecc71;
}

.form-control input.error {
	border-color: #e74c3c;
}

.form-control i {
	/* visibility: hidden;
	position: absolute;
	top: 40px;
	right: 10px; */
  color: red;
  width: 20px;
  height: 20px;

}

.form-control i.fa-check-circle.success {
	/* color: #2ecc71;
	visibility: visible; */
}

.form-control i.fa-exclamation-circle.error  {
	/* color: #e74c3c;
	visibility: visible; */
}

.form-control small {
	color: #e74c3c;
	position: absolute;
	bottom: 0;
	left: 0;
	visibility: hidden;
}

.form-control small.active{
	visibility: visible;
}

.form input[type="submit"] {
	background-color: #8e44ad;
	border: 2px solid #8e44ad;
	border-radius: 4px;
	color: #fff;
	display: block;
	font-family: inherit;
	font-size: 16px;
	padding: 10px;
	margin-top: 20px;
	width: 100%;
  cursor: pointer;
}

```

```javascript
let userInput = document.querySelector("#username");
let emailInput = document.querySelector("#email");
let passwordInput = document.querySelector("#password");
let password2Input = document.querySelector("#password2");
let small = document.querySelectorAll("small");

let form = document.querySelector("#form");


form.addEventListener("submit",(e)=>{
    e.preventDefault();


                
    // user name
    if( userInput.value == ""){
        error(userInput,"the username is blank");
    }
    else {
        success(userInput);
    }

    //email 
    if( emailInput.value == ""){
        error(emailInput,"the email is blank");

    }
    else if(!isEmail(emailInput.value)){
        error(emailInput,"the email is not valid");
    }
    else {
        success(emailInput);
    }

     //password
     if( passwordInput.value == ""){
        error(passwordInput,"the password is blank");
    }
    else if(!ispassword(passwordInput.value) ){
        error(passwordInput,"the password is not valid");
    }
    else {
        success(passwordInput);
    }

    //password check
    if( password2Input.value == ""){
        error(password2Input,"the confirm password  is blank");
    
    }
    else if( passwordInput.value !=  password2Input.value ){
        error(password2Input,"the password dont match");
    }
    else {
        success(password2Input);
    }


})


// --------------------FUNCTION ---------------------//

function isEmail(value){
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
    return emailRegex.test(value);

}


function ispassword(value){
    const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[@.#$!%*?&^])[A-Za-z\d@.#$!%*?&]{8,15}$/;;
    return passwordRegex.test(value);

}


function error(element,text){
    element.nextElementSibling.nextElementSibling.nextElementSibling.classList.add("active")
    element.nextElementSibling.nextElementSibling.nextElementSibling.innerHTML = text;

    element.classList.add("error")
}



function success(element){
    element.classList.add("success")
    element.nextElementSibling.classList.add("success")

}
```
