```html
<!DOCTYPE html>
<!-- Coding By CodingNepal - codingnepalweb.com -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <!-- ====== Fontawesome CDN Link ====== -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"/>

    <!-- ====== CSS ====== -->
    <link rel="stylesheet" href="main.css">

    <title>Toast Notification with Progress Bar </title> 
</head>

<body>

    <div class="toast">
        <div class="toast-content">
            <i class="fas fa-solid fa-check check"></i>

            <div class="message">
                <span class="text text-1">Success</span>
                <span class="text text-2">Your changes has been saved</span>
            </div>
        </div>
        <i class="fa-solid fa-xmark close"></i>

        <div class="progress"></div>
    </div>

    <button>Show Toast</button>

     <script src="main.js"></script>
</body>
</html>
```


```css
/* Google Font Import - Poppins */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body{
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: #f2f2f2;
    overflow: hidden;
}

.toast{
    position: absolute;
    top: 25px;
    right: 30px;
    border-radius: 12px;
    background: #fff;
    padding: 20px 35px 20px 25px;
    box-shadow: 0 5px 10px rgba(0,0,0,0.1);
    border-left: 6px solid #4070f4;
    overflow: hidden;
    transform: translateX(calc(100% + 30px));
    transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.35);
}

.toast.active{
    transform: translateX(0%);
 
}

.toast .toast-content{
    display: flex;
    align-items: center;
}

.toast-content .check{
    display: flex;
    align-items: center;
    justify-content: center;
    height: 35px;
    width: 35px;
    background-color: #4070f4;
    color: #fff;
    font-size: 20px;
    border-radius: 50%;
}

.toast-content .message{
    display: flex;
    flex-direction: column;
    margin: 0 20px;
}

.message .text{
    font-size: 20px;
    font-weight: 400;;
    color: #666666;
}

.message .text.text-1{
    font-weight: 600;
    color: #333;
}

.toast .close{
    position: absolute;
    top: 10px;
    right: 15px;
    padding: 5px;
    cursor: pointer;
    opacity: 0.7;
}

.toast .close:hover{
    opacity: 1;
}

.toast .progress{
    position: absolute;
    bottom: 0;
    left: 0;
    height: 3px;
    width: 100%;
    background: #694ab1;
}


button{
    padding: 12px 20px;
    font-size: 20px;
    outline: none;
    border: none;
    background-color: #4070f4;
    color: #fff;
    border-radius: 6px;
    cursor: pointer;
    transition: 0.3s;
}

button:hover{
    background-color: #0e4bf1;
}

.toast.active ~ button{
    pointer-events: none;
}
```

```javascript
const button = document.querySelector("button"),
      toast = document.querySelector(".toast")
      closeIcon = document.querySelector(".close"),
      progress = document.querySelector(".progress");
      let width;
    let a
      button.addEventListener("click",()=>{

        toast.classList.add("active");
        progress.style.width=`100%`;

        // تنتظر لما ياتي الشريط للشاشة  ثم تنقص العرض اذا ماسويتها  بينزل العرض وهو بالطريق يعني تنتظر لين يجي للصفحة ثم تبدا تنقص
        setTimeout(()=>{



            let width = 100;
            let a =  setInterval(()=>{
               progress.style.width=`${width}%`;
               width = width -1;
               if(width ===0){
                  width=100;
                  toast.classList.remove("active");
                   clearInterval(a);
               }
             },20)






        },400)

      })




      closeIcon.addEventListener(("click"),()=>{
        toast.classList.remove("active");
        progress.style.width=`0%`;
        clearInterval(a);
      })



 
 
```