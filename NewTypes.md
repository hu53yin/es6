> 1. Symbols

```javascript
let eventSymbol = Symbol('resize event');
console.log(eventSymbol.toString());

let s = Symbol.for('event');
let description = Symbol.keyFor(s);
console.log(s.toString());
console.log(description);
```
```javascript
let article = {
  title: 'Whiteface Mountain',
  [Symbol.for('article')]: 'My Article'
};

let value = article[Symbol.for('article')];
console.log(value);
console.log(Object.getOwnPropertySymbols(article));

Console output: My article
[Symbol(article)]
```

> 2. Well-known Symbols

```javascript
let Blog = function () {
};
Blog.prototype[Symbol.toStringTag] = 'Blog Class';

let blog = new Blog();

console.log(blog.toString());

Console output: [object Blog Class]
```

> 3. Object Extensions
```javascript
Object.setPrototypeOf
Object.assign
Object.is
```

> 4. String Extensions
```javascript
startsWith
endsWith
includes
"\u{1f3c4}"
```

```javascript
var title = "\u0301n";
console.log(title + ' ' + title.normalize().length);
console.log(title + ' ' + title.normalize().codePointAt(1).toString(16));
console.log(String.fromCodePoint(0x1f3c4));
```

```javascript
let title = 'Surfer';
let output = String.raw`${title} \u{1f3c4}\n`;
console.log(output);
```

```javascript
let wave = '\u{1f30a}';
console.log(wave.repeat(10));
```

> 5. Number Extensions
```javascript
Number.parseInt
Number.parseFloat
Number.isNaN
Number.isFinite
Number.isInteger
Number.isSafeInteger
Number.EPSILON
Number.MAX_SAFE_INTEGER
Number.MIN_SAFE_INTEGER
```

> 6. Math Extensions
```javascript
Math.sign
Math.cbrt(27); -> 3
Math.trunc
```

> 7. RegExp Extensions
```javascript
let pattern = '/\u{1f3c4}/';
console.log(pattern.test(''));

console.log(pattern.lastIndex);
console.log(pattern.flags);
```

> 8. Function Extensions
```javascript
let fn = function calc() {
  return 0;
};
console.log(fn.name);

Object.defineProperty();
```
