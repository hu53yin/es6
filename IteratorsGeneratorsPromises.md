> 1. Iterators
```javascript
let ids = [9000, 9001, 9002];
console.log(typeof ids[Symbol.iterator]); -> function

let it = ids[Symbol.iterator]();
console.log(it.next()); -> {done: false, value: 9000}
```

```javascript
let idMaker = {
  [Symbol.iterator]() {
    let nextId = 8000;
    return {
      next() {
        let value = nextId > 8002 ? undefined : nextId++;
        let done = !value;
        return { value, done };
      }
    };
  }
};

for (let v of idMaker)
  console.log(v);
```

> 2. Generators
```javascript
function *process() {
  yield 8000;
  yield 8001;
}

let it = process();
console.log(it.next()); -> {done: false, value: 8000}
```

> 3. Yielding in Generators
```javascript
function *process() {
  let newArray = [yield, yield, yield];
  console.log(newArray[2]);
}

let it = process();
it.next();
it.next(2);
it.next(4);
it.next(42); -> 42
```

```javascript
function *process() {
  yield 42;
  yield* [1,2,3];
}

let it = process();

console.log(it.next().value); -> 42
console.log(it.next().value); -> 1
console.log(it.next().value); -> 2
console.log(it.next().value); -> 3
console.log(it.next().value); -> undefined
```

> 4. throw and return
```javascript
function *process() {
  try {
    yield 9000;
    yield 9001;
    yield 9002;
  }
  catch(e) {
  
  }
}

let it = process();
console.log(it.next().value); -> 9000
console.log(it.throw('foo')); -> {done:true, value: undefined}
console.log(it.next()); -> {done:true, value: undefined}
```

```javascript
function *process() {
    yield 9000;
    yield 9001;
    yield 9002;
}

let it = process();
console.log(it.next().value); -> 9000
console.log(it.return('foo')); -> {value: "foo", done:true}
console.log(it.next()); -> {value: undefined, done:true}
```

> 5. Promises
```javascript
function doAsync() {
  let p = new Promise(function (resolve, reject) {
    console.log('in promise code');
    setTimeout(function () {
      console.log('rejecting...');
      reject();
    }, 2000);
  });
  return p;
}

doAsync().then(function () {
  console.log('Fulfilled!');
  },
  function () {
    console.log('Rejected!');
  });
  
doAsync().catch(function (reason) {
  console.log('Error: ' + reason);
});
```

```javascript
function doAsync() {
  return Promise.resolve('SomeString');
}

doAsync().then(
  function(value) { console.log('Ok:' + value) },
  function(reason) { console.log('Nope:' + reason) }
);
```

```javascript
Promise.all
Promise.race
```
