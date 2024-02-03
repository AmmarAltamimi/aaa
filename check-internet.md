# chech the internet if online or offline

```html
	<p>ammar</p>
```

```javacsrtipt

let p = document.querySelector("p");

window.addEventListener("load",()=>{
    if(window.navigator.onLine){
        p.innerHTML="online"

    }else{
        p.innerHTML="offline"

    }
})
window.addEventListener("online",()=>{
    p.innerHTML="online"
})

window.addEventListener("offline",()=>{
    p.innerHTML="offline"
})
```
