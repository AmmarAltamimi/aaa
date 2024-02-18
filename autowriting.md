# text effect

**1)عمل نص ويظهر جرف حرف كأنك تعمله بالكيبورد بطريقتين**
```html
<div class="one" data-con="I am Ammar Faroq Abdullah Altamimi From Yemen"></div>
```

```javascript
let div =document.querySelector(".one");
let paragraph = div.dataset.con;
let i=0;
let a = setInterval(()=>{

div.innerHTML +=paragraph[i];
i++;

if(i === paragraph.length ){
	clearInterval(a);
}
},100)

```


```javascript
let div =document.querySelector(".one");
let paragraph = div.dataset.con;
let i=1;
let a = setInterval(()=>{

div.innerHTML =paragraph.slice(0,i);
i++;

if(i === paragraph.length+1 ){

	clearInterval(a);
}

},100)
```
