## inheritance

**A Functions's Prototype**

A function's prototype is the object `instance` that will become the prototype for all objects created using this function as a constructor.

**An Objects's Prototype**

An object's prototype is the object `instance` from which the object is inherited.

Prototype is in action 
```javascript
function Person(name){
    this.name = name;
}

Person.prototype.age = 18;

let alice = new Person("Alice");
let bob = new Person("Bob")

Person.prototype === alice.__proto__;// true

alice.hasOwnProperty("age"); // false
bob.hasOwnProperty("age");   // false

alice.age;           // 18
alice.__proto__.age; // 18
bob.age;             // 18

alice.age = 25;

alice.age;           // 25
alice.__proto__.age; // 18
bob.age;             // 18

alice.hasOwnProperty("age"); // true
bob.hasOwnProperty("age");   // false
```

Prototypal inheritance chain
```javascript
function Person(first, last, age){
    this.first = first;
    this.last = last;
    this.age = age;
    Object.defineProperty(this, "full", {
        get: function() {
            return this.first + " " + this.last;
        },
        enumerable: true
    });
}

function Student(first, last, age){
    Person.call(this, first, last, age);
    this._courses = [];

    this.addCourse = function(courseId) {
        this._courses.push(courseId);
    }

    this.getCourses = function() {
        return this.full + ":" + this._courses.join(", ");
    }
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;
```