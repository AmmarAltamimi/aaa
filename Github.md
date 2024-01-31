# Github 

**1)جلب ال Repositories من موقع Github**
```html
    <div class="repos-container">
      <div class="get-repos">
        <input type="text" placeholder="Github Username">
        <span class="get-button">Get Repos</span>
      </div>
      <div class="show-data">
        <span>No Data To Show</span>
      </div>
    </div>

```

```css
* {
    box-sizing: border-box;
  }
  body {
    font-family: Tahoma, Arial;
  }
  .repos-container {
    width: 800px;
    background-color: #F6F6F6;
    margin: auto;
  }
  .repos-container .get-repos {
    padding: 20px;
    display: flex;
    background-color: #EEE;
  }
  .repos-container .get-repos input {
    width: 100%;
    padding: 15px 20px;
    border: none;
    font-size: 20px;
    height: 54px;
  }
  .repos-container .get-repos input:focus {
    outline: 2px solid #F44336;
  }
  .repos-container .get-repos .get-button {
    width: 140px;
    margin-left: 10px;
    height: 54px;
    background-color: #F44336;
    color: #FFF;
    line-height: 54px;
    text-align: center;
    font-weight: bold;
    cursor: pointer;
  }
  .repos-container .show-data {
    padding: 20px;
    background-color: #E0E0E0;
  }
  .repos-container .show-data .repo-box {
    background-color: #FFF;
    padding: 15px;
  }
  .repos-container .show-data .repo-box:not(:last-child) {
    margin-bottom: 5px;
  }
  .repos-container .show-data .repo-box a,
  .repos-container .show-data .repo-box span {
    float: right;
    margin-left: 4px;
    border-radius: 4px;
    color: #FFF;
    font-size: 12px;
    width: 90px;
    text-align: center;
    padding: 4px;
  }
  .repos-container .show-data .repo-box a {
    text-decoration: none;
    background-color: #E91E63;
  }
  .repos-container .show-data .repo-box span {
    background-color: #009688;
  }
```

```javascript

let input = document.querySelector(".get-repos input");
let submitButton = document.querySelector(".get-button");
let container = document.querySelector(".show-data");
let inputValue;

if(getFromStorage("data")){
	addToPage(getFromStorage("data"));
}

submitButton.addEventListener("click",()=>{
	if(input.value ==""){
		container.innerHTML = `<span>pls Enter the user</span>`
	}else{
		inputValue=input.value.trim();
		fetchUser(inputValue);
	}
	input.value=""
})


//fetch api and add element to page
function fetchUser(inputValue){
	fetch(`https://api.github.com/users/${inputValue}/repos`).then((response)=>{
		let data = response.json();
		return data;
	}).then((repositories)=>{
		addToPage(repositories);
		addToStorage("data",repositories);
	})
};


// add element to page
function addToPage(array){
	container.innerHTML = "";
	array.forEach(element => {
		let div = document.createElement("div");
		div.className = "repo-box"
		div.appendChild(document.createTextNode(element.name));

		let visitLink = document.createElement("a");
		visitLink.href = `https://github.com/${inputValue}/${element.name}`
		visitLink.setAttribute("target","_blank");
		visitLink.appendChild(document.createTextNode("visit"));
		div.appendChild(visitLink);


		let star = document.createElement("span");
		star.appendChild(document.createTextNode(`star : ${element.stargazers_count}`));
		div.appendChild(star);

		container.appendChild(div);

	});
}


//add to storage
function addToStorage(name,array){
	window.localStorage.setItem(name,JSON.stringify(array));
}

//get from storage
function getFromStorage(name){
	let data = JSON.parse(window.localStorage.getItem(name));
	return data;
}

```
