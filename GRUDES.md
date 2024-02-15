# نظام ال gruds

```html

<html>
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <!-- bootstrap link  -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous"/>
    <!-- bootstrap link end  -->
    <link rel="stylesheet" href="main.css" />
    <title>CRUDS</title>
  </head>
  <body>

    <!-- all content  -->

          <div class="cruds">
			
            <!-- header  -->
              <div class="head">
                <h1>cruds</h1>
                <p>product management system</p>
              </div>
            <!-- header end -->
      
            <!-- all form inputs -->
              <div class="operations">
                <div class="input">
                  <input id="title" placeholder="title" type="text" />
      
                  <div class="price">
                    <input  type="number" id="price" placeholder="price" />
                    <input  type="number" id="taxes" placeholder="taxes" readonly="readonly"/>          
                  </div>
      
                  <div class="price">
                    <input  type="number" id="ads" placeholder="ads" />
                    <input  type="number" id="discount" placeholder="discount%"/>
                  </div>
      
                  <div class="price">
                    <small id="total"></small>
                  </div>
      
                  <input id="count" placeholder="count" type="number" />
                  <input id="category" placeholder="category" type="text" />
                  <div class="submitBtn"><button id="submit">Create</button></div>
                  
                </div>
      
                <div class="output">
                  <input id="search" placeholder="search" type="text" />
                  <div class="btnsearch">
                    <button id="searchTitle">Title Search</button>
                    <button id="searchCategory">Category Search</button>
                  </div>
      
                  <button id="deleteAll">2222</button>
                </div>
              </div>
            <!-- all form inputs end  -->
      
            <!-- table desplay data  -->
              <table class="style-table">
                <thead>
                  <tr>
                    <th>index</th>
                    <th>title</th>
                    <th>price</th>
                    <th>taxes</th>
                    <th>ads</th>
                    <th>discout</th>
                    <th>total</th>
                    <th>category</th>
                    <th>update</th>
                    <th>delete</th>      
                  </tr>
                </thead>
              
                <tbody id="demo">
        
                </tbody>
                
              </table>
            <!-- table desplay data end -->
      
          </div>

    <!-- all content end -->

    <script src="main.js"></script>
  </body>
</html>
```

```css
/* google fonts links  */
@import url('https://fonts.googleapis.com/css2?family=Lora:ital,wght@1,600&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Uchen&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Alkatra:wght@500&family=Lora:ital,wght@1,600&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Uchen&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Alkatra:wght@500&family=Lora:ital,wght@1,600&family=Pacifico&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Uchen&display=swap');
/* google fonts links end */


*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    background-color: #141e14;
    color: #fff;
    font-family: 'Poppins', sans-serif;    
}

/* all content  */
.cruds {
    width: 80%;
    margin: auto;
}
/* all content end */


/* header  */
.head {
    text-transform: uppercase;
    text-align: center;
    margin: 20px 0px;
    font-family: 'Alkatra', cursive;
    letter-spacing: 3px;
}
.head h1{
    font-family: 'Pacifico', cursive;
    letter-spacing: 10px;
}
/* header end  */



/* all form inputs  */
.operations{
    width: 70%;
    margin: 10px  auto;
    background-color: #5a715a;
    padding: 30px 40px 20px 40px;
    border-radius: 50px;
    transition: 0.3s ease;
    box-shadow: 0 0 10px #657f65 ,
                0 0 10px #657f65 ,
                0 0 10px #657f65 ,
                0 0 10px #657f65 ;
}

.operations:hover{
    transform: translateY(-10px);
}

input {
    background-color: #0b0e0b;
    color: #fff;
    width: 100%;
    height: 30px;
    border: none;
    outline: none;
    padding: 20px;
    border-radius: 10px;
    margin: 4px 0;
}

input::placeholder{
    color: #657f65;
    font-family: 'Alkatra', cursive;
    letter-spacing: 3px;
    text-transform: uppercase;
}

input:focus{
    background-color: #000;
    transform: scale(1.1);
}

.price {
    display: flex;  
    align-items: start;
    justify-content: center
}
.price input{
    width: 50%;
    margin: 4px;
}

#total{
    background-color: #0b0e0b;
    padding: 5px 2px ;
    border-radius: 4px;
    margin-left: 20px;
    width: 20%;
}

#total::before{
    content: 'Final Price : ';    
}

button{
    width: 100%;
    height: 30px;
    color: #fff;
    background-color:#0b0e0b ;
    border-radius: 20px;
    border: none;
    transition: 0.3s ease;
    font-weight: bolder;
    text-transform: capitalize;
}
.operations button:hover,#deleteAll:hover{
    background-color: #718e71;
    border: solid 1px black;
    letter-spacing: 1px;
    color: black;
    font-weight: bolder;
}

.submitBtn{
    width: 50%;
    margin: auto;
    padding: 10px 0;
}
#submit{
    height: 35px;
}

.btnsearch{
    display: flex;
    justify-content: space-evenly;
}

.btnsearch button{
    width: 35%;
}
#deleteAll{
    display: none;
    margin: 30px auto;
    width: 50%;
    background-color: black;
    padding: 5px;
    text-align: center;
    border-radius: 20px;
}
/* all form inputs end */


/* table desplay data  */
table {
    text-align: center;
    width: 100%;
    margin: 30px 0 10px 0;
}

th{
    font-weight: bold ;
    text-transform: uppercase;
    padding:15px;
    border-bottom: solid 1px #718e71;
    margin-bottom: 30px;
}

td{
    padding: 10px;
    font-weight: 500;
    text-transform: uppercase;
    border-bottom: solid 1px #718e71;
}

#demo button:hover{
    background-color: #718e71;
    color: black;
    font-weight: bolder;
}
/* table desplay data end */
```


```javascript

let titleInput = document.querySelector("#title");
let priceInput = document.querySelector("#price");
let taxesInput = document.querySelector("#taxes");
let adsInput = document.querySelector("#ads");
let discountInput = document.querySelector("#discount");
let totalPrice = document.querySelector("#total");
let countInput = document.querySelector("#count");
let categoryInput = document.querySelector("#category");
let submitInput = document.querySelector("#submit");
let searchInput = document.querySelector("#search");
let searchButton = document.querySelectorAll(".btnsearch button");
let searchTitle = document.querySelector("#searchTitle");
let searchCategory = document.querySelector("#searchCategory");
let deleteAll = document.querySelector("#deleteAll");
let bodyTable = document.querySelector("#demo");



let mood = "create"
let searchType = "searchTitle"
// window.localStorage.clear();

// array empty or from add data to array from local storage 
let dataArray = [];
if(window.localStorage.getItem("data")){
     dataArray = JSON.parse(window.localStorage.getItem("data"));
}else{
    dataArray = [];
}


//----------------------------------------------

// get data from local storage and display it in page
if(window.localStorage.getItem("data")){
    let data = JSON.parse(window.localStorage.getItem("data"));
    addToPage(data);
}


//----------------------------------------------


//get the value of fullprice or total price to save in newProduct object bellow
priceInput.addEventListener("input",calculate);
taxesInput.addEventListener("input",calculate);
adsInput.addEventListener("input",calculate);
discountInput.addEventListener("input",calculate);


//----------------------------------------------



// action click in submit 
submitInput.addEventListener("click",()=>{

    
    //step one create array and push to array 
    let newProduct ={
        title : titleInput.value.trim(),
        price : priceInput.value.trim(),
        taxes : taxesInput.value.trim(),
        ads    :  adsInput.value.trim(),
        discount : discountInput.value.trim() ===""? 0:discountInput.value.trim() ,
        fullPrice : totalPrice.innerHTML, 
        category : categoryInput.value.trim()
    }

    //    make condition 
    if(titleInput.value !=""
     &&priceInput.value
     && taxesInput.value !="" 
     && adsInput.value !=""
     && categoryInput.value !=""
     && countInput.value.length <= 100){

        if(mood ==="create"){
        for(let i= 1 ; i<= +countInput.value ; i++){
        dataArray.push(newProduct);
        }
    }else {
        dataArray[+submitInput.getAttribute("data-set")]=newProduct;
        submitInput.innerHTML="Create";
        countInput.style.display="block";
        mood= "create"
    }
       //clear inputs
        clearData();

    }

        //function add delete all element
        addDeleteAll();

        //add to page
       addToPage(dataArray);


     //step five add array to local storage
     window.localStorage.setItem("data", JSON.stringify(dataArray));

})

// to delete all element
deleteAll.addEventListener("click",deleteFunction);

//to choose type of search
searchButton.forEach((button,i)=>{
    button.addEventListener("click",()=>{
        searchType=button.getAttribute("id");
        searchInput.value="";
        searchInput.focus()
        addToPage(dataArray);
    });
})

// enter your search 
searchInput.addEventListener("input",()=>{
    let newArray = [];
    let value = searchInput.value.trim();
    let tr = document.querySelectorAll("#demo tr");
    if(value ==""){

   addToPage(dataArray);
    }
        else{
    if(searchType === searchTitle.getAttribute("id")){

        dataArray.forEach((ele,index)=>{
            if(ele.title.includes(value)){
                newArray.push(ele);
            }
                
            
        })
        addToPage(newArray)

    }

    else if(searchType === searchCategory.getAttribute("id")){

        dataArray.forEach((ele,index)=>{
            if(ele.category.includes(value)){

                newArray.push(ele);

                addToPage(newArray);

            }
                
            
        })
        addToPage(newArray)


    }

}

});



//---------------------------------function ------------------------------//


// calculate all elemet to delete
function calculate(){

    if(priceInput.value !=""){
        taxesInput.value = Math.floor((+priceInput.value * (15/100)));
        if(adsInput.value !="" && taxesInput.value !="" ){
              let price = +priceInput.value + +taxesInput.value + +adsInput.value ;
                totalPrice.innerHTML= Math.floor(price - ((+discount.value / 100) * price));
          } else{
                    // في حالة كانت وحدة منهم فاضية بيمسح يعني مثلا عبيت وحدة بعدين مسحتها يجب ان ينمسح السعر
                 totalPrice.innerHTML = "";
            }
    }
        else{
            taxesInput.value="";
            totalPrice.innerHTML = "";

        }

    }




//clear data function from input
function clearData(){
 titleInput.value ="";
    priceInput.value ="";
   taxesInput.value ="";
    adsInput.value ="";
    discountInput.value ="";
    totalPrice.innerHTML="";
    countInput.value ="";
    categoryInput.value  ="";
    searchInput.value="";

}


//add data to page function 
function addToPage (dataArray){

    // empty innerHTML
    bodyTable.innerHTML="";



    //add data to page
    dataArray.forEach((element,i) => {
        //create tr
        let tr = document.createElement("tr");
            tr.className="tr";

        //create th index
        let thIndex = document.createElement("th");
        thIndex.appendChild(document.createTextNode((i+1)));
        tr.appendChild(thIndex);

     //create th object inside tr
        for(let i in element){
        let th =document.createElement("th");
        th.appendChild(document.createTextNode(element[i]));
        tr.appendChild(th);
        }



       //create update button inside tr
       let rowUpdate =document.createElement("th");
        let updateButton = document.createElement("button");
        updateButton.className="update";
        updateButton.appendChild(document.createTextNode("update"));
        rowUpdate.appendChild(updateButton);
         tr.appendChild(rowUpdate);



         //create delete button inside tr
         let rowDelete = document.createElement("th");
          let deleteButton = document.createElement("button");
          deleteButton.className="delete";
          deleteButton.appendChild(document.createTextNode("delete"));
          rowDelete.appendChild(deleteButton);
          tr.appendChild(rowDelete);



        //add tr to body 
         bodyTable.appendChild(tr);
         

 //----------------action update & delete---------//


        // update click action
                // update click action
                updateButton.addEventListener("click",()=>{
                
                    titleInput.value =dataArray[i].title;
                    priceInput.value =dataArray[i].price;
                   taxesInput.value =dataArray[i].taxes;
                    adsInput.value =dataArray[i].ads;
                    discountInput.value =dataArray[i].discount;
                    totalPrice.innerHTML=dataArray[i].fullPrice;
                    categoryInput.value  =dataArray[i].category;
    
                    submitInput.innerHTML="Update";
                    countInput.style.display="none";
                    submitInput.setAttribute("data-set",i)
                    mood ="update"
                    scrollTo({
                        top:0,
                        behavior:"smooth"
                    })
                    
                
                });
    


        // delete click action 
        deleteButton.addEventListener("click",()=>{
                
            dataArray = dataArray.filter((ele,index)=>{

                return i != index;
            })
            deleteAll.innerHTML=`delete all (${dataArray.length})`;
            addToPage(dataArray);
            window.localStorage.setItem("data", JSON.stringify(dataArray));

        })


});


}


//delete all function
function deleteFunction(){
bodyTable.innerHTML="";
deleteAll.style.display="none";
}



//function add delete all element
function addDeleteAll(){
if(dataArray.length > 0){

    deleteAll.style.display = "block";
    deleteAll.innerHTML=`delete all (${dataArray.length})`;
}else{

    deleteAll.style.display = "none";

}
}






```
