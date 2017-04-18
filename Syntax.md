# es6
notes and exercises

> 1. Rest and Spread parameters

```javascript

'use strict'
var showCategories = function(productId, ...categories) {
  console.log(categories);
};

showCategories(123, 'search', 'advertising');
```

> 2. Object Literal Extensions

```javascript
'use strict'

var price = 5.99, quantity = 10;
var productView = {
  price,
  quantity,
  "calculate value"() {
    return this.price * this.quantity
  }
};

console.log(productView["calculate value"]());

'use strict'
var field = "dynamicField";
var price = 5.99;
var productView = {
  [field]: price
};

console.log(productView);

'use strict'
var ident = 'productId';
var productView = {
  get [ident] () { return true; }
  set [ident] (value) { }
};

console.log(productView.productId);

```

> 3. Template Literals

```javascript
'use strict'
let invoiceNum = '1350';
console.log(`Invoice Number: ${"INV-" + invoiceNum}`);

'use strict'
function processInvoice(segments, ...values) {
  console.log(segments);
  console.log(values);
}

let invoiceNum = '1350';
let amount = '2000';

processInvoice `Invoice: ${invoiceNum} for ${amount}`;

Console output: ["Invoice: ", " for ", ""]
[1350, 2000]
```

> 4. Destructuring

```javascript
'use strict'

let salary = ['32000', '50000', '75000'];
let [low, average, high] = salary;
console.log(avarage);

Console output: 50000

'use strict';

let salary = {
  low: '32000',
  average: '50000',
  high: '75000'
};
let { low, average, high } = salary;
console.log(high);

'use strict';

let salary = {
  low: '32000',
  average: '50000',
  high: '75000'
};
let { low: newLow, average: newAverage, high: newHigh } = salary;
console.log(newHigh);
```
