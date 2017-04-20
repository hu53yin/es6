> 1. The Reflect API
```javascript
class Restaurant {
  constructor(name, city) {
    console.log(`${name} in ${city}`);
  }
}

let r = Reflect.construct(Restaurant, ["Zoey's", "Goleta"]);

class Restaurant {
  constructor() {
    this.id = 33;
  }
  show(prefix) {
    console.log(prefix);
  }
}

Reflect.apply(Restaurant.prototype.show, {id: 22}, ['REST:']);

class Restaurant {
}
let setup = {
  getId() { return 88; }
}
let r = new Restaurant();
Reflect.setPrototypeOf(r, setup);
console.log(r.getId()); -> 88 
```

```javascript
class Restaurant {
  constructor() {
    this.id = 8000;
  }
}

let r = new Restaurant();
console.log(Reflect.get(r, 'id')); -> 8000
```

```javascript
class Restaurant {
  constructor() {
    this._id = 9000;
  }
  get id() {
    return this._id;
  }
}

let r = new Restaurant();
console.log(Reflect.get(r, 'id'), { _id: 88 }); -> 88

Reflect.set(r, 'id', 88);
console.log(r.id); -> 88
```

```javascript
class Location {
  constructor() {
    this.city = 'Goleta';
  }
}

class Restaurant extends Location {
  constructor() {
    super();
    this.id=9000;
  }
}

let r = new Restaurant();
console.log(Reflect.has(r, 'id')); -> true
console.log(Reflect.has(r, 'city')); -> true
console.log(Reflect.ownKeys(r)); -> ["city", "id"]
```

```javascript
class Restaurant {
}

let r = new Restaurant();
Reflect.defineProperty(r, 'id', { 
  value:2000, 
  configurable:true,
  enumerable:true
});

console.log(r['id']); -> 2000

Reflect.deleteProperty(r, 'id');

let d = Reflect.getOwnPropertyDescriptor(r, 'id');
console.log(d);
```

```javascript
let rest = {
  id:2000
};

Reflect.preventExtensions(rest);
rest.location = 'Goleta';

console.log(rest.location); -> undefined
```
