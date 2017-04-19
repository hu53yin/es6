> 1. Array Extensions
```javascript
Array(90000);
Array.of(90000);
Array.from(amounts, v => v + 100);

let salaries = [600, 700, 800];
salaries.fill(900);
console.log(salaries); -> [900, 900, 900]

let salaries = [600, 700, 800];
salaries.fill(900, 1);
console.log(salaries); -> [600, 900, 900]

let salaries = [600, 700, 800];
salaries.fill(900, 1, 2);
console.log(salaries); -> [600, 900, 800]

let salaries = [600, 700, 800];
salaries.fill(900, -1);
console.log(salaries); -> [600, 700, 900]
```

```javascript
let salaries = [600, 700, 800];
let result = salaries.find(value => value >= 650);
console.log(result); -> 700

let result = salaries.findIndex(function (value, index, array)
{
  return value == this;
}, 700);

console.log(result); -> 1

salaries.copyWithin(2, 0);
console.log(salaries); -> [600, 700, 600]

let ids = [1, 2, 3, 4, 5];
ids.copyWithin(0, 1);
console.log(ids); -> [2, 3, 4, 5, 5]

let ids = ['A','B','C'];
console.log(...ids.entries()); -> [0, "A"], [1, "B"], [2, "C"]
console.log(...ids.keys()); -> 0 1 2
console.log(...ids.values()); -> A B C
```

> 2. Array Buffers and Typed Arrays
```javascript
let buffer = new ArrayBuffer(1024);
console.log(buffer.byteLength); -> 1024

let a = new Int8Array(buffer);
a[0] = 0xff;
console.log(a[0]); -> -1
```

> 3. DataView and Endiannes
```javascript
let buffer = new ArrayBuffer(1024);
let dv = new DataView(buffer);
console.log(dv.byteLength); -> 1024

let dv = new DataView(buffer, 0, 32);
console.log(dv.byteLength); -> 32

let dv = new DataView(buffer);
dv.setUint8(0, 1);
console.log(dv.getUint16(0)); -> 256

dv.setUint8(0, 1);
console.log(dv.getUint16(0, true)); -> 1
```

> 4. Map and WeakMap
```javascript
let employee1 = {name: 'Jake'};
let employee2 = {name: 'Janet'};

let employees = new Map();
employees.set(employee1, 'ABC');
employees.set(employee2, '123');

console.log(employees.get(employee1));
console.log(employees.size);

console.log(employees.delete(employee2));
console.log(employees.size);

employees.clear();
console.log(employees.size);

let employees = new WeakMap([
  [employees1, 'ABC'],
  [employees2, '123']
]);

employee1 = null;
//wait for GC cycle

console.log(employees.size); -> undefined
```

> 4. Set and WeakSet
```javascript
let perks = new Set();

perks.add('Car');
perks.add('Super Long Vacation');

console.log(perks.size); -> 2
```
