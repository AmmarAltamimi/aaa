**1)array**
```javascript
let a = 1;
let b = 2;
let c = 3;
let d = 4;

let myFriends = ["Ahmed", "Sayed", "Ali", "Maysa"];

[a = "A", b, c, d, e = "Osama"] = myFriends;

let [, y, , z] = myFriends;

console.log(a);
console.log(b);
console.log(c);
console.log(d);
console.log(e);

console.log(y);
console.log(z);
```

**2)array nested array**
```javascript
let myFriends = ["Ahmed", "Sayed", "Ali", ["Shady", "Amr", ["Mohamed", "Gamal"]]];

let [a, , , [b, , [, c]]] = myFriends;
//note > العناصر التي عبرت عليها لانها الاب مصفوفة فانه عمل فراغ
console.log(a); // Ahmed
console.log(b); // Shady
console.log(c); // Gamal
```

**3)array nested object**
```javascript
let myFriends = [
  { title: "Osama", age: 39, available: true, skills: ["HTML", "CSS"] },
  { title: "Ahmed", age: 25, available: false, skills: ["Python", "Django"] },
  { title: "Sayed", age: 33, available: true, skills: ["PHP", "Laravel"] },
];


let [ , ,{title:a,skills:[,b]}] =myFriends;
//note=> الاوبجكت الاول والثاني لانها داخل مصفوفة ولانريدهم جعلنا لهم فراغ
//note=> العمر وحالة منوفرة لانهم داخل الاوبجكت لم نجل لهم فراغ
//note=> لغة بي اتش بي لانها داخل مصفوفة ولانريدهم جعلنا لهم فراغ
console.log(a) ; // Sayed
console.log(b); // Laravel
```

**4)object**
```javascript

const user = {
  theName: "Osama",
  theAge: 39,
  theTitle: "Developer",
  theCountry: "Egypt",
};
// ({ theName, theAge, theTitle, theCountry } = user);
const { theName, theAge, theCountry } = user;

console.log(theName);
console.log(theAge);
console.log(theCountry);
```
**6)object nested object**

```javascript

const user = {
  theName: "Osama",
  theAge: 39,
  theTitle: "Developer",
  theCountry: "Egypt",
  theColor: "Black",
  skills: {
    html: 70,
    css: 80,
  },
};

const { theName: n, theAge: a, theCountry, theColor: co = "Red",skills: { html: h }} = user;

console.log(n);
console.log(a);
console.log(theCountry);
console.log(co);
console.log(`My HTML Skill Progress Is ${h}`);

```

**7)object nested array**


```javascript

const user = {
  theName: "Osama",
  theAge: 39,
  skills: ["HTML", "CSS", "JavaScript"],
  addresses: {
    egypt: "Cairo",
    ksa: "Riyadh",
  },
};

const { theName: n,theAge: a, skills: [, , three], addresses: { egypt: e }} = user;

console.log(`Your Name Is: ${n}`);
console.log(`Your Age Is: ${a}`);
console.log(`Your Last Skill Is: ${three}`);
console.log(`Your Live In: ${e}`);

```


**8)يمكن اختيار جزء فقط كالاتي**



```javascript


let myFriends = ["Ahmed", "Sayed", "Ali", ["Shady", "Amr", ["Mohamed", "Gamal"]]];

let [a,,[,b]] = myFriends[3];
console.log(a);
console.log(b);
```



```javascript

let myFriends = [
    { title: "Osama", age: 39, available: true, skills: ["HTML", "CSS"] },
    { title: "Ahmed", age: 25, available: false, skills: ["Python", "Django"] },
    { title: "Sayed", age: 33, available: true, skills: ["PHP", "Laravel"] },
  ];

  let{title:a,skills:[,b]} =myFriends[2];
  
  console.log(a);
  console.log(b);

```



```javascript
const user = {
    theName: "Osama",
    theAge: 39,
    skills: ["HTML", "CSS", "JavaScript"],
    addresses: {
      egypt: "Cairo",
      ksa: "Riyadh",
    },
  };

  let [a,,b] = user.skills;
  console.log(a);
  console.log(b);
  let {ksa} = user.addresses;
console.log(ksa);

```


**9)swap**
```javascript
let book = "Video";
let video = "Book";

[book, video] = [video, book];

```


**10)with function**
```javascript

const user = {
  theName: "Osama",
  theAge: 39,
  skills: {
    html: 70,
    css: 80,
  },
};

showDetails(user);

function showDetails({ theName: n, theAge: a, skills: { css: c } } = user) {
  console.log(`Your Name Is ${n}`);
  console.log(`Your Age Is ${a}`);
  console.log(`Your CSS Skill Progress Is ${c}`);
}

```


