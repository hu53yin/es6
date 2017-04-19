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
