# scroll

1) **عمل شريط في الاعلى وهذا الشريطة كلما نزلت للاسقل يزداد عرضه وعندما تصل الى النهاية يكون اكتمل الشريط على عرض الصفحة**
   ```javascript
   
 let scroll = document.querySelector(".scroller");
let scrollHeight = document.documentElement.scrollHeight;
let clientHeight = document.documentElement.clientHeight;
let hideHide = scrollHeight - clientHeight;



window.addEventListener("scroll",()=>{
let scrollTop = document.documentElement.scrollTop;
scroll.style.width = `${(scrollTop / hideHide) * 100}%` ;


})
   ```
