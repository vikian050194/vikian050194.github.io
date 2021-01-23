## Object property descriptor

```javascript
let person = {
    name: "Kirill"
};

let nameDescriptor = Object.getOwnPropertyDescriptor(person, "name");
// {
//     value: "Kirill",
//     writable: true,
//     enumerable: true,
//     configurable: true
// }

Object.defineProperty(person, "age", { writable: false });

person.age = 27; // age is undefined

Object.defineProperty(person, "age", { writable: true });
person.age = 27;

let names = [];
for(let properyName in person){
    names.push(propertyName);
}
// names is ["name", "age"]

names = [];
Object.defineProperty(person, "age", { enumerable: false });
for(let properyName in person){
    names.push(propertyName);
}
// names is ["name"]

Object.defineProperty(person, "age", { configurable: false });
Object.defineProperty(person, "age", { configurable: true });// TypeError: Cannot redefine property: age
Object.defineProperty(person, "age", { enumerable: true });// TypeError: Cannot redefine property: age
Object.defineProperty(person, "age", { writable: false });// It's possible to change "writable"!
delete person.age;// false

person = {
    name: {
        first: "Kirill",
        last: "Vinogradov"
    },
    age: 27
};

Object.defineProperty(person, "full", { 
    get: function() {
        return this.name.first + ' ' + this.name.last;
    },
    set: function(value){
        const [first, last] = value.split(" ");
        this.name.first = first;
        this.name.last = last;
    }
});

const currentFullName = person.full;// "Kirill Vinogradov"
person.full = "Foo Bar";
const first = person.name.first;// "Foo"
const last = person.name.last;// "Bar"
```