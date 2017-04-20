> 1. Get by Proxy

```javascript
function Employee() {
  this.name = 'Milton Waddams';
  this.salary = 0;
}

var e = new Employee();

var p = new Proxy(e, { 
  get: function (target, prop, receiver) {
    return "Attempted access: " + prop;
  }
});

console.log(p.salary); -> Attempted access: salary

var p = new Proxy(e, { 
  get: function (target, prop, receiver) {
    return Reflect.get(target, prop, receiver);
  }
});

console.log(p.salary); -> 0

var p = new Proxy(e, { 
  get: function (target, prop, receiver) {
    if(prop === 'salary')
      return 'Denied';
    return Reflect.get(target, prop, receiver);
  }
});

console.log(p.salary); -> Denied
console.log(p.name); -> Milton Waddams
```

```javascript
function getId() { 
  return 55;
}

var p = new Proxy(getId, { 
  apply: function(target, thisArg, argumentsList) {
    return Reflect.apply(target, thisArg, argumentsList);
  }
});

console.log(p()); -> 55
```

```javascript
var t = {
  tableId: 99
}

var p = new Proxy({}, { 
  apply: function(target, prop, receiver) {
    return 'Property ' + prop + ' doesn\'t exist...';
  }
});

Object.setPrototypeOf(t, p);
```

```javascript
var t = { 
  tableId: 99
}

let { proxy, revoke } = Proxy.revocable(t, {
  get: function(target, prop, receiver) { 
    return Reflect.get(target, prop, receiver) + 100;
  }
});

console.log(proxy.tableId); -> 199
revoke();
console.log(proxy.tableId); -> Property size doesn''t exist
```
