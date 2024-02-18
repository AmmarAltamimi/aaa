# accordion 
**1) two idea in js**

# Accordion

**1)الفكرة الاولى**
```html
<!DOCTYPE html>
<!-- Coding By CodingNepal - codingnepalweb.com -->
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <!----======== CSS ======== -->
    <link rel="stylesheet" href="main.css">

    <!-- =====Fontawesome CDN Link===== -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css">

   <title>Accordion in HTML CSS & JavaScript</title>
</head>
<body>
    <div class="accordion">
        <div class="accordion-content">
            <header>
                <span class="title">What do you mean by Accordion?</span>
                <i class="fa-solid fa-plus"></i>
            </header>

            <p class="description">
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus nobis ut perspiciatis minima quidem nisi, obcaecati, delectus consequatur fuga nostrum iusto ipsam ducimus quibusdam possimus. Maiores non enim numquam voluptatem?
            </p>
        </div>

        <div class="accordion-content">
            <header>
                <span class="title">What do you mean by Accordion?</span>
                <i class="fa-solid fa-plus"></i>
            </header>

            <p class="description">
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus nobis ut perspiciatis minima quidem nisi, obcaecati, delectus consequatur fuga nostrum iusto ipsam ducimus quibusdam possimus. Maiores non enim numquam voluptatem?
            </p>
        </div>
        <div class="accordion-content">
            <header>
                <span class="title">What do you mean by Accordion?</span>
                <i class="fa-solid fa-plus"></i>
            </header>

            <p class="description">
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus nobis ut perspiciatis minima quidem nisi, obcaecati, delectus consequatur fuga nostrum iusto ipsam ducimus quibusdam possimus. Maiores non enim numquam voluptatem?
                Lorem ipsum dolor sit amet, consectetur adipisicing elit. Iusto neque, sed inventore illum ut quis ducimus deleniti temporibus maiores? At nisi sed pariatur cupiditate quidem quod adipisci aut, eos quis minima voluptates non veniam ipsam quasi architecto ducimus error eum id ab, suscipit doloribus, ut accusantium consequuntur voluptate! Unde, hic sed rerum officia totam id libero officiis nihil rem sequi porro labore praesentium repudiandae a blanditiis molestias nisi beatae natus! Ea, ut voluptates, natus harum nesciunt odio hic eveniet reprehenderit veritatis, possimus tempora magni soluta eaque quidem neque maxime nostrum sapiente commodi? Earum ex cumque cupiditate dicta, tempora temporibus quaerat.
            </p>
        </div>
        <div class="accordion-content">
            <header>
                <span class="title">What do you mean by Accordion?</span>
                <i class="fa-solid fa-plus"></i>
            </header>

            <p class="description">
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Natus nobis ut perspiciatis minima quidem nisi, obcaecati, delectus consequatur fuga nostrum iusto ipsam ducimus quibusdam possimus. Maiores non enim numquam voluptatem?
            </p>
        </div>
    </div>
    
    <script src="main.js"></script>
</body>
</html>


```


```css
/* ===== Google Font Import - Poppins ===== */
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap');

*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}
body{
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #E3F2FD;
}
.accordion{
    max-width: 530px;
    width: 100%;
    background: #FFF;
    margin: 0 15px;
    padding: 15px;
    border-radius: 8px;
    box-shadow:  0 0 4px rgba(0,0,0,0.2);
}
.accordion .accordion-content{
    margin: 10px 0;
    border-radius: 4px;
    background: #FFF7F0;
    border: 1px solid #FFD6B3;
    overflow: hidden;
}
.accordion-content:nth-child(2){
    background-color: #F0FAFF;
    border-color: #CCEEFF;
}
.accordion-content:nth-child(3){
    background-color: #FFF0F3;
    border-color: #FFCCD6;
}
.accordion-content:nth-child(4){
    background-color: #F0F0FF;
    border-color: #CCCCFF;
}
.accordion-content.open{
    padding-bottom: 10px;
}
.accordion-content header{
    display: flex;
    min-height: 50px;
    padding: 0 15px;
    cursor: pointer;
    align-items: center;
    justify-content: space-between;
    transition: all 0.2s linear;
}
.accordion-content.open header{
    min-height: 35px;
}
.accordion-content header .title{
    font-size: 14px;
    font-weight: 500;
    color: #333;
}
.accordion-content header i{
    font-size: 15px;
    color: #333;
}
.accordion-content .description{
    height: 0;
    opacity: 0;
    font-size: 12px;
    color: #333;
    font-weight: 400;
    padding: 0 15px;
    transition: all 0.2s linear;
}
```




```javascript
let container = document.querySelectorAll(".accordion-content");
let description = document.querySelectorAll("p");
let icon = document.querySelectorAll("i")


container.forEach((con)=>{
    con.addEventListener("click",()=>{

        let currentDescription = con.lastElementChild;
        let currentIcon = con.firstElementChild.lastElementChild; // to change icon from + to -     



             //remove class active from all  expect currentDescription
             let rest = [...description].filter((ele)=>{
                return ele !=currentDescription;
            })
                    rest.forEach((re)=>{
                re.classList.remove("active")
            })

// or
 //  //remove class active from all  expect currentDescription
            //  description.forEach((item) => {
            //     if(item !=currentDescription ){
            //         item.classList.remove("active");
            //     }
            // });


            
             // show and hide description
            currentDescription.classList.toggle("active");

   

   

        description.forEach((des)=>{

            if(des.classList.contains("active")){
                des.style.height = `${currentDescription.scrollHeight}px`;
                des.style.opacity = "1";
    
            }else{
                des.style.height = `0px`;
                des.style.opacity = "0";
    
            }
        })


        icon.forEach((ic)=>{
            if(ic.parentElement.nextElementSibling.classList.contains("active")){
                ic.classList.replace("fa-plus", "fa-minus")


            }else{

              ic.classList.replace("fa-minus", "fa-plus")


            }
        })
 


    })
})

```


```javascript
let container = document.querySelectorAll(".accordion-content");
let description = document.querySelectorAll("p");
let icon = document.querySelectorAll("i")


container.forEach((con)=>{
    con.addEventListener("click",()=>{
        let currentDescription = con.lastElementChild;
        let currentIcon = con.firstElementChild.lastElementChild; // to change icon from + to -     

        if(currentDescription.classList.contains("active")){
            currentDescription.classList.remove("active");

        }else{
            description.forEach((des)=>{
                des.classList.remove("active");
            })
            currentDescription.classList.add("active")
        }




        description.forEach((des)=>{

            if(des.classList.contains("active")){
                des.style.height = `${currentDescription.scrollHeight}px`;
                des.style.opacity = "1";
    
            }else{
                des.style.height = `0px`;
                des.style.opacity = "0";
    
            }
        })


        icon.forEach((ic)=>{
            if(ic.parentElement.nextElementSibling.classList.contains("active")){
                ic.classList.replace("fa-plus", "fa-minus")


            }else{

              ic.classList.replace("fa-minus", "fa-plus")


            }
        })
 


    })
})
```

