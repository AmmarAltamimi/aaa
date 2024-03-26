Sure, here are examples for each built-in constructor in JavaScript:

1. **String:**
   ```javascript
   // Example 1
   let str1 = "Hello";
   
   // Example 2
   let str2 = new String("World");
   ```

2. **Number:**
   ```javascript
   // Example 1
   let num1 = 42;
   
   // Example 2
   let num2 = new Number(3.14);
   ```

3. **Boolean:**
   ```javascript
   // Example 1
   let bool1 = true;
   
   // Example 2
   let bool2 = new Boolean(false);
   ```

4. **Array:**
   ```javascript
   // Example 1
   let arr1 = [1, 2, 3];
   
   // Example 2
   let arr2 = new Array('apple', 'banana', 'orange');
   ```

5. **Object:**
   ```javascript
   // Example 1
   let obj1 = { name: 'John', age: 30 };
   
   // Example 2
   let obj2 = new Object();
   obj2.property = 'value';
   ```
   **يمكن ايضا انشاء object عن طريق عمل constructor  بيدك اي لما نعمل object من class**

6. **Function:**
   ```javascript
   // Example 1
   function greet(name) {
       console.log("Hello, " + name + "!");
   }
   
   // Example 2
   let func2 = new Function('console.log("This is a function");');
   ```

7. **RegExp:**
   ```javascript
   // Example 1
   let regex1 = /\d+/;
   
   // Example 2
   let regex2 = new RegExp('\\w+');
   ```

These examples illustrate the use of both literal notation and constructor invocation for each data type.
