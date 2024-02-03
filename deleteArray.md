
**1)حذف العناصر المكرر في array**

*->في array العاية*

```javascript
let array = [1, 2, 2, 3, 4, 4, 5];
let uniqueArray = [...new Set(array)];
console.log(uniqueArray); // [1, 2, 3, 4, 5]
```

```javascript
const array = [1, 2, 3, 4, 1, 2, 3];
const uniqueArray = array.filter((value, index, self) => {
  return self.indexOf(value) === index;
});
console.log(uniqueArray); // [1, 2, 3, 4]
```


```javascript
const array = [1, 2, 3, 4, 1, 2, 3];
const uniqueArray = array.reduce((accumulator, currentValue) => {
  if (!accumulator.includes(currentValue)) {
    accumulator.push(currentValue);
  }
  return accumulator;
}, []);
console.log(uniqueArray); // [1, 2, 3, 4]
```


```javascript
let arr = ["apple", "mango",
          "apple", "orange", "mango", "mango"];
 
function removeDuplicates(arr) {
    let unique = arr.reduce(function (acc, curr) {
        if (!acc.includes(curr))
            acc.push(curr);
        return acc;
    }, []);
    return unique;
}
console.log(removeDuplicates(arr));
```



```javascript


let arr = ["apple", "mango",
          "apple", "orange", "mango", "mango"];
 
function removeDuplicates(arr) {
    let unique = [];
    for (i = 0; i < arr.length; i++) {
        if (unique.indexOf(arr[i]) === -1) {
            unique.push(arr[i]);
        }
    }
    return unique;
}
```
----------------------------------------
*->في array of object*
```javascript
const arr = [
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Alice'},
  {id: 2, name: 'Nick'},
  {id: 2, name: 'James'},
];


function removeDuplicateObjects(arr, property) {
  return [...new Map(arr.map(obj => [obj[property], obj])).values()];
}

// [ { id: 1, name: 'Alice' }, { id: 2, name: 'James' } ]
```

```javascript
let arrayOfObjects = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Jane' },
  { id: 1, name: 'John' }, // Duplicate
  { id: 3, name: 'Bob' },
  { id: 2, name: 'Jane' }  // Duplicate
];

let uniqueArray = [];
let seenIds = [];

for (let obj of arrayOfObjects) {
  if (!seenIds.includes(obj.id)) {
    seenIds.push(obj.id);
    uniqueArray.push(obj);
  }
}

console.log(uniqueArray);

```



```javascript
const arr = [
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Tom', age: 30},
  {id: 2, name: 'Nick'},
  {id: 2, name: 'Nick', age: 40},
];

const unique = arr.filter((obj, index) => {
  return index === arr.findLastIndex(o => obj.id === o.id);
});

// 👇️ [ { id: 1, name: 'Tom', age: 30 }, { id: 2, name: 'Nick', age: 40 } ]
console.log(unique);
```


```javascript
const arr = [
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Tom'},
  {id: 2, name: 'Nick'},
  {id: 2, name: 'Nick'},
];

const unique = arr.filter((obj, index) => {
  return index === arr.findIndex(o => obj.id === o.id);
});

// 👇️ [ { id: 1, name: 'Tom' }, { id: 2, name: 'Nick' } ]
```


```javascript
const arr2 = [
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Tom'},
  {id: 1, name: 'Alice'},
  {id: 2, name: 'Nick'},
  {id: 2, name: 'Nick'},
  {id: 2, name: 'Bob'},
];

const unique2 = arr2.filter((obj, index) => {
  return index === arr2.findIndex(o => obj.id === o.id && obj.name === o.name);
});

// [
//   { id: 1, name: 'Tom' },
//   { id: 1, name: 'Alice' },
//   { id: 2, name: 'Nick' },
//   { id: 2, name: 'Bob' }
// ]
```
-------------------------
*->في array of array نفس اعلاه*












