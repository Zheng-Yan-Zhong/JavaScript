# JavaScript & Algorithm

## Table of Contents
* [**Grammar**](#Grammar)
    * [Variable](#Variable)
    * [Data Type](#Data-Type)
    * [Operator](#Operator)
    * [Scope](#Scope)
    * [Hoisting](#Hoisting)
    * [Closure](#Closure)
    * [Callback](#Callback)
    * [Promise](#Promise)
      * [Promise.all](#Promise.all)
      * [Promise.race](#Promise.race)
    * [Async await](#Async-await)
    * [Function case](#Function-case)
    * [Proxy](#Proxy)
    * [Module](#Module)
      * [MJS](#MJS)
      * [CJS](#CJS)
    * [try...catch](#Try…Catch)
    * [Class](#Class)
      * [static](#static)
      * [extends](#extends)
      * [override property](#override-property)
      * [override method](#override-method)
* [**Algorithm**](#Algorithm)
    * [Big O](#Big-O)
    * [*Search*](#Search)
        * [Linear Search](#Linear-Search)
        * [Binary Search](#Binary-Search)
    * *Sort*
        * [Bubble Sort]()
        * [Insertion Sort]()
        * [Selection Sort]()
        * [Merge Sort]()
        * [Quick Sort]()

* [**Data Structure**](Data-Structure)
    * [Stack](#Stack)
    * [Queue](#Queue)
    * [Linked List](#Linked-List)
    * Hash
    * Tree

---

# Grammar

## Variable

- **var**
  - `可被重複宣告`
  - `可宣告不賦值`
  - `可被重新賦值`

```javascript
// [v]
var user;
const user = {
  
}
// [v]
var user = "Dennis";
var user = "Admin";
```

- **let**
  - `塊級作用域`
  - `不可被重複宣告`
  - `可宣告不賦值`
  - `可被重新賦值`

```javascript
// [v]
let user;
// [X]
let user = "Dennis";
let user = "Jack";
```

- **const**
  - `不可重複宣告`
  - `不可宣告未賦值`
  - `不可重新賦值`

```javascript
// [v]
const user = "Dennis";
// [x]
const user;
// [x]
const user = "Dennis";
const user = "Jack"
```


---

## Data Type

- **Primitive**
  - `String`
  - `Number`
  - `Undefined`
  - `Null`
  - `NaN`
  - `Boolean`
- **Reference**
  - `Object`
  - `Array(Object)`
  - `Function(Object)`

### Primitive type

原始數據(primitive)是所謂的 deep copy(深複製)，也就是説當今天引用了另一個變數，由於深度複製，可以避免引用到記憶體位址，進而造成改 B 也改到 A 的問題。

```javascript
let a = 12;
let b = a;
b = 13;
// a: 12, b: 13
```

### Reference

參考數據(Reference)是 shallow copy(淺複製)，由於淺複製是引用記憶體位置，所以改動 B 則 A 也會更動。

```javascript
let user = {
  name: "Dennis",
};
let copyUser = user;
copyUser.name = "Jack";
//user["name"]: Jack, copyUser["name"]: Jack;
```

- **`String`**

```JavaScript
// [v]
let str = new String('Hello World')
// [v]
let str = 'Hello World';
// [v]
let str = "Hello World";
// [v]
let str = `Hello World`
```

- **`Number`**

```javascript
// [v]
let num = new Number(100);
// [v]
let num = 100;
```

- **`Undefined`**

```javascript
let str;
console.log(str); //Undefined
```

- **`Null`**

```javascript
let str = null;
```

- **`NaN`**

```javascript
let number = 12;
let mod = "error";
console.log(number / mod); //NaN
```

- **`Boolean`**

```javascript
let bool = true;
let bool = false;
```

- **`Object`**

```javascript
// [v]
let user = new Object({ name: "Dennis", age: 22 });
// [v]
let user = {
  name: "Dennis",
  age: 22,
};
```

**Object Dot notation**
```javascript
let user = {
  name: "Dennis",
  age: 22,
};
console.log(user.name); //"Dennis"
```

**Object Bracket notation**

```javascript
let user = {
  name: "Dennis",
  age: 22,
};
console.log(user["name"]); //"Dennis"
```

- **`Array`**

```javascript
// [v]
let list = new Array("A", "B", "C"); // ["A", "B", "C"]
// [v]
let list = ["A", "B", "C"]; // ["A", "B", "C"]
```

**Index**

```javascript
let list = ["A", "B", "C"];
// list[0] //'A'
// list[2] //'C'
```

- **`Function`**

```javascript
//declaration Function
function sum(a, b) {
  return a + b;
}
//Anonymous Function
function (a,b) {
  return a + b
}
//Anonymous Expression Function
const sum = function(a,b) {
  return a + b
}
//Arrow Function
const sum = (a,b) => {
  return a + b
}
```

### Immediately Function

```javascript
function sayHi() {
  console.log("Hello World!");
}
sayHi(); //Hello World
```

```javascript
// Immediately Function
(function sayHi() {
  console.log("Hello World!");
})(); //Hello World
```

---

## Operator

- **`Arithmetic`**

```javascript
// +
let result = 3 + 3; //6
// -
let result = 3 - 3; //0
// *
let result = 3 * 3; // 9
// **
let result = 3 ** 3; //27
// /
let result = 3 / 3; //1
// %
let result = 3 / 3; //0
// ++
let num = 3;
let result = ++num; // result = 4;
let result = num++; // result = 3;
// --
let num = 3;
let result = --num; // result = 2;
let result = num--; // result = 3;
```

- **`Comparison`**

```javascript
let str = "3";
let num = 3;
// ==
console.log(str == num); //true
// ===
console.log(str === num); //false
// !=
console.log(str != num); //false
// !==
console.log(str !== num); // true
// >
console.log(3 > 3); //false
// >=
console.log(3 >= 3); //true
// <
console.log(3 < 3); //false
// <=
console.log(3 <= 3); //true
```

- **`Logic`**

```javascript
let bool = true;
// && (block1 == true, execute block2)
console.log(bool && 1); //1
console.log(bool && 1 && 3); //3
// || (block1 == true, execute block1, block1 == false, execute block2)
console.log(bool || 1); // true
console.log(false || bool); //true
// !true //false
console.log(!true); //false
```

## Scope

```javascript
let name = "Ivy";
function outter() {
  let name = "Dennis";
  console.log(name);
}
outter(); //Dennis
```

```javascript
let name = "Ivy";
function outter() {
  console.log(name);
}
outter(); //Ivy
```

**advanced**
由於 function 是看所在的區塊，所以無論是在 function 中，一樣會先呼叫本身所在區塊的變數。

```javascript
let name = "Ivy";
function sayHi() {
  console.log(name);
}
function user() {
  let name = "Dennis";
  sayHi();
}
user(); //Ivy
```

---

## Hoisting

**`var`**

```javascript
console.log(name); //ReferenceError
```

```javascript
var name;
console.log(name); //undefined
```

**`let`**

```javascript
console.log(name); //ReferenceError
```

```javascript
let name;
console.log(name); //undefined
```

**`const`**

```javascript
const name;
console.log(name) //Reference error must initialize Variable
```

```javascript
const name = null;
console.log(name); //null
```

## Closure

**private**

```javascript
function count(value) {
  let base = 2;
  return base * value;
}
console.log(count(3)); //6
```

**closure**

```javascript
function count(power = 0) {
  return function (value) {
    return power * value;
  };
}
const counter = count();
console.log(counter(3)); //0

const counter = count(3);
console.log(counter(3)); //9
```

`advanced`

```javascript
function count() {
  function increase(value) {
    return value + 1;
  }
  function decrease(value) {
    return value - 1;
  }
  return {
    increase,
    decrease,
  };
}
const counter = count();
console.log(counter.increase(7)); //8

//---------- ES6 destructuring
const { increase, decrease } = count();
console.log(decrease(7)); // 6
```

## Callback

```javascript
function callback(value, call) {
  call(value * value);
}
// 最後利用一個函式帶入參數，並取出結果
callback(3, (result) => {
  console.log(result);
});
```

## Promise
### syntax
```javascript
new Promise((resolve, reject)=> {
  //conditional
})
```

* ES6(ECMA 2015)
* 解決閉包難以閱讀的語法
* 更好的非同步方法
* `then`接受resolve
* `catch`接受reject
* `finally`必定回傳

```javascript
const promise = () =>
  new Promise((resolve, reject) => {
    let count = 10;
    // setTimeout會進入event queue模擬非同步
    setTimeout(() => {
      count = 0;

      if (count === 0) {
        resolve("success");
      } else {
        reject("sorry is crash");
      }
    }, 2000);
  });
console.log(promise()); //Promise { <pending> }
```

接著我們需要使用`.then`接收回傳的資料
```javascript
promise()
  //滿足了 resolve函式所以會在
  .then((res) => console.log(res)) //success
```

若是符合reject則使用`.catch`捕捉錯誤
```javascript
promise()
  .then((res) => console.log(res)) 
  .catch((err) => console.log(err)); //sorry is crash
```

最後使用`.finally`來做處理完畢的提醒
```javascript
promise()
  .then((res) => console.log(res)) 
  .catch((err) => console.log(err)); //sorry is crash
  .finally(() => console.log('finished'))
```

### Promise.all
* 執行陣列中所有的Promise，且都必須符合才會回傳所有Promise

```javascript
const promise1 = () =>
  new Promise((resolve, reject) => {
    let count = 10;
    // setTimeout會進入event queue模擬非同步
    setTimeout(() => {
      count = 0;
      if (count === 0) {
        resolve("success1");
      } else {
        reject("sorry is crash1");
      }
    }, 1000);
  });

const promise2 = () =>
  new Promise((resolve, reject) => {
    let count = 10;
    // setTimeout會進入event queue模擬非同步
    setTimeout(() => {
      count = 0;

      if (count === 0) {
        resolve("success2");
      } else {
        reject("sorry is crash2");
      }
    }, 2000);
  });

Promise.all([promise1(), promise2()])
  .then((res) => console.log(res)) //[ 'success1', 'success2' ]
  .catch((err) => console.log(err));

```

### Promise.race
* 比較Promise中最快的，並且回傳該Promise

```javascript
const promise1 = () =>
  new Promise((resolve, reject) => {
    let count = 10;
    // setTimeout會進入event queue模擬非同步
    setTimeout(() => {
      count = 0;

      if (count === 0) {
        resolve("success1");
      } else {
        reject("sorry is crash");
      }
    }, 4000);
  });

const promise2 = () =>
  new Promise((resolve, reject) => {
    let count = 10;
    // setTimeout會進入event queue模擬非同步
    setTimeout(() => {
      count = 0;

      if (count === 0) {
        resolve("success2");
      } else {
        reject("sorry is crash");
      }
    }, 2000);
  });

Promise.race([promise1(), promise2()])
  .then((res) => console.log(res)) //兩個Promise都滿足，但是Promise2比較快，所以回傳Promise2
  .catch((err) => console.log(err));

```

---

## Function case
下面的狀況是需要一個蘿蔔一個坑，參數順序完全不能錯誤
```javascript
let users = []
function addUser(name, age, email) {
	users.push({
	name: name,
	age: age,
	email: email
	})	
}

addUser("Dennis",23, "test@gmail.com")

console.log(users)
/* 
[{
  age: 23,
  email: "test@gmail.com",
  name: "Dennis"
}]
*/
```

而我們如果使用物件傳遞參數可以避免未來參數增加造成順序傳遞的問題

```javascript
let users = []
const obj = {
	name: "Dennis",
	age: 23,
	email: "test@gmail.com"
}
function addUser({name, age, email}) {
	users.push({
	name: name,
	age: age,
	email: email
	})	
}

addUser(obj)

console.log(users)
/* 
[{
  age: 23,
  email: "test@gmail.com",
  name: "Dennis"
}]
*/

```

## Proxy
### syntax
```javascript
  new Proxy(target, handler)
```

* 代理變數並且做任何的操作
* [Proxy MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/Proxy/get)
* Vue3使用Proxy進行包裹

--- 

```javascript
const spec = {};
const specProxy = new Proxy(spec, {});
specProxy.ram = "4G";
console.log(spec); //{ ram: '4G' }
```

下面使用Proxy提供的方法進行操作
* get
* set

```javascript
const spec = {weight: "200g", ram: "3G"};
const specProxy = new Proxy(spec, {
  get: (target, property) => {
    return property in target ? target[property] : null;
  },
  set: (target, property, value) => {
    //只提供修改weight
    if (property === "weight") {
      target[property] = value;
    } 
  },
});
specProxy.ram = "4G";
console.log("spec", specProxy); //{weight: "200g", ram: "3G"}
```

## Async await
* Async 宣告函式為非同步
* await 等待並且完成才繼續執行

以下是一般使用Promise的寫法，並且使用.then取得Promise資料
```javascript
function getUsers() {
  let data = [];
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      data.push("Dennis");
      data.push("Anne");

      if (data.length > 0) {
        resolve(data);
      } else {
        reject("no data");
      }
    }, 1000);
  });
}
getUsers().then((data) => console.log(data)); //[ 'Dennis', 'Anne' ]
```

但是如果每寫一個Promise都需要使用.then可能不是很美觀，在ES7新增了Async的語法糖，本質上輔助Promise，因為沒有Promise就不需要Async語法糖

這邊有兩個Promise函式，分別是getUsers、getUsers2
```javascript
function getUsers() {
  let data = [];
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      data.push("Dennis");
      data.push("Anne");

      if (data.length > 0) {
        resolve(data);
      } else {
        reject("no data");
      }
    }, 1000);
  });
}

function getUsers2() {
  let data = [];
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      data.push("Jason");
      data.push("May");

      if (data.length > 0) {
        resolve(data);
      } else {
        reject("no data");
      }
    }, 1000);
  });
}
```

使用async宣告函式， await依序等待

```javascript
async function initApplication() {
  const data = await getUsers();
  const data2 = await getUsers2();
  console.log(data, data2); //[ 'Dennis', 'Anne' ] [ 'Jason', 'May' ]
}

initApplication();
```

當然我們可以使用Promise.all美化程式碼，由於使用Promise.all所以若是有任一 reject，則會回報錯誤，若成功回傳陣列
```javascript
async function initApplication() {
  const data = await Promise.all([getUsers(), getUsers2()]);
  console.log(data); //[[ 'Dennis', 'Anne' ] [ 'Jason', 'May' ]]
}

initApplication();
```
搭配Try...catch確保程式可以完整執行
```javascript
async function initApplication() {
  try {
    const data = await Promise.all([getUsers(), getUsers2()]);
    console.log(data); //[[ 'Dennis', 'Anne' ] [ 'Jason', 'May' ]]
  } catch (err) {
    console.log("err", err);
  }
}
initApplication();
```

---

## Module
### MJS
* `import`、`export`
* 檔案若不使用.mjs -> .js，則package.json中必須設定`type: module`
```javascript
//sayHi.mjs
function sayHi() {
  console.log("hello");
}

const initData = {
  date: "2023-01-01",
};
export default sayHi;
export { initData };
```
```javascript
import sayHiFunction from "./sayHi.mjs";
import { initData } from "./sayHi.mjs";
sayHiFunction();
console.log(initData);
```

![](https://i.imgur.com/bOf1UDT.png)

### CJS
* NodeJS常用
```javascript
//sayHi.cjs
function sayHi() {
  console.log("hello");
}

const initData = {
  date: "2023-01-01",
};
module.exports = sayHi;
module.exports = {
  sayHi,
  initData,
};
```

```javascript
//main.cjs
const sayHiAction = require("./sayHi.cjs");
sayHiAction.sayHi();

console.log(sayHiAction.initData);
```
![](https://i.imgur.com/krEbC4k.png)

---

## Try...Catch
* **try** 
* **catch** 可帶入參數
* **finally** 
```javascript
function getData() {
  return new Promise((resolve, reject) => {
    let data;
    //模擬非同步
    setTimeout(() => {
      data = 1;
      if (data) {
        if (data > 2) {
          return resolve(data);
        } else {
          return reject("data less than 2");
        }
      } else {
        return reject("empty data");
      }
    }, 2000);
  });
}

async function initApplication() {
  try {
    await getData();
    //error 斷掉並且不會執行以下函式
    console.log("initApplication");
  } catch (err) {
    console.log("error", err);
  } finally {
    console.log("end");
  }
}

initApplication();
```
![](https://i.imgur.com/V2dVd3u.png)

---



## Class
* contructor
* super
* extends
* static


在Class中定義屬性，必須使用`constructor`定義參數，並且最後使用`new`建立**實體(instance)**
```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}
const std1 = new Student("Dennis", 23); //建立實體

console.log(std1.sayHi()); //Hello I'm Dennis
```

### static
在類別中定義該函式為static，則建立實體後無法使用

```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  static printParameter() {
    console.log("name and age");
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}
const std1 = new Student("Dennis", 23);

console.log(std1.sayHi()); //Hello I'm Dennis
Student.printParameter(); // name and age
```

### extends
```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  static printParameter() {
    console.log("name and age");
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}

class ClassLeader extends Student {}

const classALeader = new ClassLeader("Jason", 18);

console.log(classALeader.sayHi());
```

### override property 

假設今天我在班長的類別想要增加`sex`的屬性：

```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  static printParameter() {
    console.log("name and age");
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}

class ClassLeader extends Student {
  constructor(sex) {
    this.sex = sex;
  }
}
const classALeader = new ClassLeader("Jason", 18, "male");

console.log(classALeader.sayHi()); 

//ReferenceError: Must call super constructor in derived class before accessing 'this' or returning from derived constructor
```

必須在`ClassLeader`中使用建構子，並且使用`super`繼承該屬性


>這邊要注意`super`一定要在繼承類別中定義屬性的第一行

```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  static printParameter() {
    console.log("name and age");
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}

class ClassLeader extends Student {
  constructor(name, age, sex) {
    super(name, age); //一定要在第一行
    this.sex = sex;
  }
}
const classALeader = new ClassLeader("Jason", 18, "male");

console.log(classALeader.sayHi()); //Hello I'm Jason
```

如果怕繼承寫錯繼承屬性我們可以使用參數的方式
```javascript
class ClassLeader extends Student {
  constructor(argus, sex) {
    super(argus); //帶入參數
    this.sex = sex;
  }
}
```

### override method
直接在繼承類別中定義相同命名的函式即可
```javascript
class Student {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  static printParameter() {
    console.log("name and age");
  }

  sayHi() {
    return `Hello I'm ${this.name}`;
  }
}

class ClassLeader extends Student {
  constructor(argus, sex) {
    super(argus);
    this.sex = sex;
  }
  sayHi() {
    return "ClassLeader";
  }
}
const classALeader = new ClassLeader("Jason", 18, "male");

console.log(classALeader.sayHi()); //ClassLeader
```

---

# Algorithm

* [Big O](#Big-O)
* [Search](#Search)
    * Linear Search
    * Binary Search
* [Recursion](#Recursion)
* [Sort](#Sort)
    * Bubble Sort
    * Insertion Sort
    * Selection Sort
    * Merge Sort
    * Quick Sort

---

## Big O
* `O(1)`
* `O(logn)`
* `O(n)`
* `O(nlogn)`
* `O(n^2)`

![](https://i.imgur.com/eCzuZ3Z.jpg)
> sour`https://cdn-media-1.freecodecamp.org/images/1*KfZYFUT2OKfjekJlCeYvuQ.jpeg`

Big O是演算法中用來計算時間複雜度(time complexity)及空間複雜度(space complexity)的一種量化規則。

使用不嚴謹(unnecessary)及模糊(freezy)的方式通常以最大程度影響複雜度的為主，其餘則忽略不計。

舉個例子:
```javascript
function timeComplexity(n) {
    for(let i = 0; i < n; i++) {
        console.log('running')
        for(let j = 0; j < n; j++) {
            console.log(`i*j = ${i*j}`)
        }
    }
}
```

當上面有兩層迴圈時時間複雜度為`O(n^2)`，我們可以看到這時候第三行的`console.log('running')`為`O(n)`，所以目前的時間複雜度為`O(n^2) + O(n)`。

由於Big O為模糊的計算方式，所以只取影響大的數值，也就是上面的時間複雜度正確來說為`O(n^2)`。

我們再舉個例子：
```javascript
function timeComplexity() {
    console.log('1')
    console.log('2')
}
```
上面會執行兩次console.log，而我們可以表示為`O(1)`即可。



### Object
* 搜尋  **O(n)**
* 插入  **O(1)**
* 移除  **O(1)**
* 取得  **O(1)**

```javascrip
const user = {
    firstname: "Dennis",
    lastname: "Zheng"
}
```

### Array
* 搜尋 **O(n)**
* 插入 **O(n)**
* 移除 **O(n)**
* 取得 **O(1)**
```javascript
const arr = [1,2,3,4]
```
---
## Search
搜尋演算法是一項非常重要的概念，所有的一切皆為資料。既然都是資料，不只是要正確的找到，且也要快速的找到。這時候就有賴於我們的搜尋演算法針對各個不同的場景使用不同的手段了。

## Linear Search
* 時間複雜度 `O(n)`
```javascript
const arr = [1,3,5,7,10]

function LinearSearch(arr, target) {
  for(let i = 0; i < arr.length -1; i++) {
    if(arr[i] == target){
      return i 
    }
  }
}

const index = LinearSearch(arr,5)
console.log(index) //2
```
## Binary Search
* 時間複雜度 `O(nlogn)`

```javascript
const arr = [3, 6, 8, 12, 20, 21];

function binarySearch(arr, target) {
  let left = 0;
  let right = arr.length - 1;
  let middle;
  while (left <= right) {
    middle = Math.floor(left + right / 2);
    if (arr[middle] > target) {
      right = middle;
    } else if (arr[middle] < target) {
      left = middle;
    } else {
      return middle;
    }
  }
}

const index = binarySearch(arr, 20);
console.log(index); // 4
```
## Recursion
* Recursion的核心觀念為透過呼叫自身函數

```javascript
function recursion(num) {
  if (num > 0) {
    console.log(num);
  } else {
    console.log("end");
    return;
  }
  //每次傳入 num -1 
  return recursion(num - 1);
}

recursion(5);
/*
  5 -> 4 -> 3 -> 2 -> 1 -> end
*/
```

由於遞迴的資料結構為堆疊(Stack)所以會是先進後出(FILO)
```javascript
 recursion(5) 
    recursion(4) 
      recursion(3)
        recursion(2)
          recursion(1)
```
## Sort

### Bubble Sort
* O(n^2)

![](https://i.imgur.com/QHW98e0.gif)


```javascript
const arr = [3, 10, 1, 0];

function bubbleSort(arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    for (let j = 0; j < arr.length - 1; j++) {
      swap(arr, j, j + 1);
    }
  }
  function swap(array, prev, current) {
    if (array[current] < array[prev]) {
      let temp = array[prev];
      array[prev] = array[current];
      array[current] = temp;
    }
  }
  return arr;
}

const result = bubbleSort(arr);
console.log(result); //[ 0, 1, 3, 10 ]
```

---

### Selection Sort
* O(n^2)


```javascript
const arr = [1, 3, 0, 10, 2];

function selectionSort(arr) {
  let store = [];
  for (let i = 0; i < arr.length; i++) {
    let minIndex = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[minIndex]) {
        minIndex = j;
      }
    }
    //swap
    console.log(store);
    /*
      [ 0 ]
      [ 0, 1 ]
      [ 0, 1, 2 ]
      [ 0, 1, 2, 3 ]
      [ 0, 1, 2, 3, 10 ]
    */
    store.push(arr[minIndex]);
    let temp = arr[minIndex];
    arr[minIndex] = arr[i];
    arr[i] = temp;
  }
  return store;
}

const result = selectionSort(arr);
console.log(result);


```

### Insertion Sort

```javascript


```

### Merge Sort
* **分而治之，大問題切分各個小問題**
* **O(nlogn)**

![](https://i.imgur.com/Mc8DK1I.gif)
> https://ithelp.ithome.com.tw/articles/10241640

看到上面的GIF可以發現，利用遞迴的方式切割成每個單一數值，最後再進行合併。


我們先從合併開始寫起，這邊要注意左和右都必須是已排序過的陣列
```javascript
function merge(left, right) {
  let i = 0; 
  let j = 0;
  let temp = [];
  while (i < left.length && j < right.length) {
    console.log("temp");
    console.log(temp);
    if (left[i] < right[j]) {
      temp.push(left[i]);
      i++;
    }
    if (right[j] < left[i]) {
      temp.push(right[j]);
      j++;
    }
  }
// 避免左或右還有未排序的數值
  while (i < left.length) {
    temp.push(left[i]);
    i++;
  }

  while (j < right.length) {
    temp.push(right[j]);
    j++;
  }
  return temp;
}
```
接著是遞迴切割
```javascript
function mergeSort(arr) {
  if (arr.length == 1) {
    return arr;
  }
  let left = arr.slice(0, Math.floor(arr.length / 2));
  let right = arr.slice(Math.floor(arr.length / 2, 0));
  return merge(mergeSort(left), mergeSort(right));
}
```

```javascript
arr [ 3, 5, 10, 2, 0 ]
arr [ 3, 5 ]
arr [ 3 ]
arr [ 5 ]
left [ 3 ]
right [ 5 ]
arr [ 10, 2, 0 ]
arr [ 10 ]
arr [ 2, 0 ]
arr [ 2 ]
arr [ 0 ]
left [ 2 ]
right [ 0 ]
left [ 10 ]
right [ 0, 2 ]
left [ 3, 5 ]
right [ 0, 2, 10 ]

result [ 0, 2, 3, 5, 10 ]
```

---

# Data Structure

## Stack

```javascript
function Queue(arr) {
  this.arr = arr;
  this.push = function (value) {
    this.arr[this.arr.length] = value;
    return this.arr;
  };
  this.shift = function () {
    for (let i = 0; i < this.arr.length - 1; i++) {
      this.arr[i] = this.arr[i + 1];
      console.log(this.arr);
    }
    this.arr.length = this.arr.length - 1;
    return this.arr;
  };
}
let arr = [1, 2, 3];
var queue = new Queue(arr);
console.log(queue.shift());
```


## Queue

```javascript
function Queue(arr) {
  this.arr = arr;
  this.push = function (value) {
    this.arr[this.arr.length] = value;
    return this.arr;
  };
}
let arr = [1, 2, 3];
var queue = new Queue(arr);
console.log(queue.push(5)); //[ 1, 2, 3, 5 ]
```


## Linked List

```javascript
class Node {
  constructor(item) {
    this.item = item;
    this.next = null;
  }
}
class LinkedList {
  constructor() {
    this.length = 0;
    this.head = null;
  }
}
const linkedList = new LinkedList();
```

**append**

```javascript
class Node {
  constructor(item) {
    this.item = item;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.length = 0;
    this.head = null;
  }
  getLength() {
    console.log(this.length);
    return this.length;
  }

  append(value) {
    if (this.length == 0 && this.head == null) {
      this.length = this.length + 1;
      this.head = new Node(value);
      return;
    }
    if (this.length == 1) {
      this.length = this.length + 1;
      this.head.next = new Node(value);
      return;
    }
    if (this.length >= 2) {
      let head = this.head;
      let nextNode = head.next;
      while (nextNode.next !== null) {
        nextNode = nextNode.next;
      }
      nextNode.next = new Node(value);
      this.length = this.length + 1;
    }
  }
}
const linkedList = new LinkedList();
linkedList.append(13);
linkedList.append(14);

console.log(linkedList);
/*
LinkedList {
  length: 2,
  head: Node { item: 13, next: Node { item: 14, next: null } }
}
*/
```

**delete**

```javascript

```
