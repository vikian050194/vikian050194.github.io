## Equality

### All ways to check equality

Operator `==` is NOT type-safe. Should be avoided. Useful only in rare cases.

```javascript
"42" == 42
0 == false
null == undefined
"" == 0
[1,2] == "1,2"
```

Operator `===` is type-safe. Most common. Should be used in almost all cases. Convenient and concise.

```javascript
NaN !== NaN
+0 === -0
```

`Object.is()` function is type-safe as well. Less common. Like `===` except for a few mathematical differences. Verbose.

```javascript
Object.is(NaN, NaN)
!Object.is(+0, -0)
```

### Objects equality

```javascript
let person1 = {
    name: "Kirill",
    age: 27
};

let person2 = {
    name: "Ivan",
    age: 31
};

let doubleEqual = person1 == person2;      // false
let tripleEqual = person1 === person2;     // false
let isEqual = Object.is(person1, person2); // false

person2 = person1;

doubleEqual = person1 == person2;      // true
tripleEqual = person1 === person2;     // true
isEqual = Object.is(person1, person2); // true
```

### Primitive types equality

```javascript
let name1 = "Kirill";
let name2 = "Kirill";

doubleEqual = name1 == name2;      // true
tripleEqual = name1 === name2;     // true
isEqual = Object.is(name1, name2); // true
```