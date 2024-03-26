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


