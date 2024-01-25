# to do list js
```javascript
form = document.querySelector("#new-task-form");
input = document.querySelector("#new-task-input");
tasks = document.querySelector("#tasks");
h2 = document.querySelector("h2");
let plannedArray = [];
 plannedArray = getFromLocalStorageJson("plans");

 if(getFromLocalStorageJson("plans")){
	addToPage(getFromLocalStorageJson("plans"))
 }

 
 if(getFromLocalStorage("counter")){
	h2.innerHTML = getFromLocalStorage("counter");
}




// --------------------------------------------------------------


form.addEventListener("submit" , (e)=>{
	e.preventDefault();
	if(!input.value){
		alert("pls enter what do you have planned");
	}
	else{
		let inputValue = (input.value).trim();
		clickFun(inputValue);
	}

input.value="";
})



tasks.addEventListener("click",(e)=>{
if(e.target.className=="delete"){
let del = e.target;
deleteTask(del);
}
else if(e.target.className=="edit"){
		let edit = e.target;
		editTask(edit);
		}

else if(e.target.className=="submit"){
		let submit = e.target;
		submitTask(submit);
}

})



// --------------------------------------------------------------
// 1-click fun 
function clickFun(value){

	const plans = {
		id : Date.now(),
		plan :value,
		completed :false,
	}


	if(plannedArray.findIndex((ele)=>ele.plan==value)!=-1){
		alert("this task has already added");
	}else{

		plannedArray.push(plans);
	}




h2.innerHTML = `we have ${counter()} task(s) to be completed`;
console.log(h2.innerHTML);

addToPage(plannedArray);

addToLocalStorageJson("plans",plannedArray);
addToLocalStorage("counter",h2.innerHTML);

}





// --------------------------------------------------------------
// 2-add to page

function addToPage(array){

	tasks.innerHTML = "";
array.forEach(ele => {
	let h2 = document.createElement("h2");
	h2.appendChild(document.createTextNode(`we have ${counter()}s to be completed`));
	task=document.createElement("div");
	task.className = "task";
	task.setAttribute("id-data",ele.id)
	content = document.createElement("div");
	content.className="content";
	inputTask = document.createElement("input")
	inputTask.type = "text";
	inputTask.className = "text";
	inputTask.value = ele.plan;
	if(ele.completed ==true){
		inputTask.classList.add("done")
	}
	inputTask.setAttribute("readonly","readonly")
	actions = document.createElement("div");
	actions.className="actions";

	button1 = document.createElement("button");
	button1.className = "submit";
	button1.innerHTML = "waiting";
	if(ele.completed ==true){
		button1.innerHTML = "submitted";
	}
	button1.setAttribute("id-data",ele.id)
	button2 = document.createElement("button");
	button2.className = "edit";
	button2.innerHTML = "edit";
	// button1.appendChild(document.createTextNode("edit"));
	button3 = document.createElement("button");
	button3.className = "delete";
	button3.innerHTML = "delete";
	
	// button2.appendChild(document.createTextNode("delete"));

	tasks.appendChild(task);
	task.appendChild(content);
	content.appendChild(inputTask);
	task.appendChild(actions);
	actions.appendChild(button1);
	actions.appendChild(button2);
	actions.appendChild(button3);

});

}


// --------------------------------------------------------------
// 3-delete

function deleteTask(del){
del.parentElement.parentElement.remove();
 plannedArray = plannedArray.filter((ele)=>{
	return ele.id != del.parentElement.parentElement.getAttribute("id-data");
});
h2.innerHTML = `we have ${counter()} task(s) to be completed`;
addToLocalStorageJson("plans",plannedArray);
addToLocalStorage("counter",h2.innerHTML);


}


// --------------------------------------------------------------
// 4-edit

let oldValue ;

function editTask(edit){
if(edit.innerHTML =="edit"){

	if(edit.previousElementSibling.innerHTML == "submitted"){
		alert("this task has already submitted");
	}else{

	 oldValue = edit.parentElement.previousElementSibling.firstElementChild.value;
	console.log(oldValue);

	edit.innerHTML="save";
	edit.parentElement.previousElementSibling.firstElementChild.removeAttribute("readonly");
	edit.parentElement.previousElementSibling.firstElementChild.focus();
}

}
	else{

	let newValue= edit.parentElement.previousElementSibling.firstElementChild.value;
console.log(newValue);

	edit.innerHTML="edit";
	edit.parentElement.previousElementSibling.firstElementChild.setAttribute("readonly","readonly");

	 plannedArray = plannedArray.map((e)=>{
		if(e.plan === oldValue)
			return {...e,plan:newValue};
		else
			return e;

	})

	}

	addToLocalStorageJson("plans",plannedArray);

}


// --------------------------------------------------------------
// 5-submit


function submitTask(submit){
if(submit.innerHTML =="waiting"){

	submit.innerHTML="submitted";
	submit.parentElement.previousElementSibling.firstElementChild.classList.add("done");

	plannedArray = plannedArray.map((e)=>{

		if(e.id == submit.getAttribute("id-data")){
		return {...e,completed : true};
		}

		else
		return e;
	})

	h2.innerHTML = `we have ${counter()} task(s) to be completed`;

}
	else{

	submit.innerHTML="waiting";
	submit.parentElement.previousElementSibling.firstElementChild.classList.remove("done");


	plannedArray = plannedArray.map((e)=>{

		if(e.id == submit.getAttribute("id-data")){
		return {...e,completed : false};
		}

		else
		return e;
	})

	h2.innerHTML = `we have ${counter()} task(s) to be completed`;


	}
	addToLocalStorageJson("plans",plannedArray);
	addToLocalStorage("counter",h2.innerHTML);


}


// --------------------------------------------------------------
// 6-add storage 
function addToLocalStorageJson(name,value){
window.localStorage.setItem(name,JSON.stringify(value))

}
// --------------------------------------------------------------
// 7-get json storage 
function getFromLocalStorageJson(name){
	let data = JSON.parse(window.localStorage.getItem(name));
	return data;

		}
	


// --------------------------------------------------------------
// 8-add storage 
function addToLocalStorage(name,value){
	window.localStorage.setItem(name,value)
	
	}
	





	// --------------------------------------------------------------
// 9-get storage 
function getFromLocalStorage(name){
	let data =window.localStorage.getItem(name);
		return data;
		
		}



// --------------------------------------------------------------
// 10-counter 

function counter(){
	let count = 0;
	for(let i = 0 ; i<plannedArray.length ; i++){
		if(plannedArray[i].completed ==false){
			count +=1;
		}

	}

	return count;
}

```
----------------------------------------------------------------------------------------------
# to do list html

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
	
	<header>
		<h1>Task List 2023</h1>
		<form id="new-task-form">
			<input 
				type="text" 
				name="new-task-input" 
				id="new-task-input" 
				placeholder="What do you have planned?" />
			<input 
				type="submit"
				id="new-task-submit" 
				value="Add task" />
		</form>
	</header>
	<main>
		<section class="task-list">
			<h2>we have 0 task(s) to be completed</h2>
			<div id="tasks">
			
				<!-- <div class="task">
					<div class="content">
						<input 
							type="text" 
							class="text" 
							value="A new task"
							readonly>
					</div>
					<div class="actions">
						<button class="edit">Edit</button>
						<button class="delete">Delete</button>
					</div>
				</div> -->


			</div>
		</section>
	</main>

	<script src="main.js"></script>
</body>
</html>

```
------------------------------------------------------------------------------
# to do list css

```css
:root {
	--dark: #374151;
	--darker: #1F2937;
	--darkest: #111827;
	--grey: #6B7280;
	--pink: #EC4899;
	--purple: #8B5CF6;
	--light: #EEE;
}

* {
	margin: 0;
	box-sizing: border-box;
	font-family: "Fira sans", sans-serif;
}

body {
	display: flex;
	flex-direction: column;
	min-height: 100vh;
	color: #FFF;
	background-color: var(--dark);
}

header {
	padding: 2rem 1rem;
	max-width: 800px;
	width: 100%;
	margin: 0 auto;
}

header h1{ 
	font-size: 2.5rem;
	font-weight: 300;
	color: var(--grey);
	margin-bottom: 1rem;
}

#new-task-form {
	display: flex;;
}

input, button {
	appearance: none;
	border: none;
	outline: none;
	background: none;
}

#new-task-input {
	flex: 1 1 0%;
	background-color: var(--darker);
	padding: 1rem;
	border-radius: 1rem;
	margin-right: 1rem;
	color: var(--light);
	font-size: 1.25rem;
}

#new-task-input::placeholder {
	color: var(--grey);
}

#new-task-submit {
	color: var(--pink);
	font-size: 1.25rem;
	font-weight: 700;
	background-image: linear-gradient(to right, var(--pink), var(--purple));
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
	cursor: pointer;
	transition: 0.4s;
}

#new-task-submit:hover {
	opacity: 0.8;
}

#new-task-submit:active {
	opacity: 0.6;
}

main {
	flex: 1 1 0%;
	max-width: 800px;
	width: 100%;
	margin: 0 auto;
}

.task-list {
	padding: 1rem;
}

.task-list h2 {
	font-size: 1.5rem;
	font-weight: 300;
	color: var(--grey);
	margin-bottom: 1rem;
}

#tasks .task {
	display: flex;
	justify-content: space-between;
	background-color: var(--darkest);
	padding: 1rem;
	border-radius: 1rem;
	margin-bottom: 1rem;
	cursor: pointer;
	
}

.task .content {
	flex: 1 1 0%;
}

.task .content .text {
	color: var(--light);
	font-size: 1.125rem;
	width: 100%;
	display: block;
	transition: 0.4s;
}



.task .content .text:not(:read-only) {
	color: var(--pink);
}



.task .content .text.done {
    text-decoration: line-through;
    color: #edd2ac47;
}

.task .actions {
	display: flex;
	margin: 0 -0.5rem;
}

.task .actions button {
	cursor: pointer;
	margin: 0 0.5rem;
	font-size: 1.125rem;
	font-weight: 700;
	text-transform: uppercase;
	transition: 0.4s;
}

.task .actions button:hover {
	opacity: 0.8;
}

.task .actions button:active {
	opacity: 0.6;
}

.task .actions .edit {
	background-image: linear-gradient(to right, var(--pink), var(--purple));
	-webkit-background-clip: text;
	-webkit-text-fill-color: transparent;
}

.task .actions .delete {
	color: crimson;
}


.task .actions .submit {
	color: rgb(48, 143, 111);
}
```
-------------------------------------------------------------------------------
