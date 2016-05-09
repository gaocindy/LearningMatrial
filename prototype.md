1. prototype
    1. prerequisite  
        pointer, reference
    1. prototype vs \__proto__

        ```javascript
        function Person(name, age) {
            this.name = name;
            this.age = age;
        }
        Person.prototype.getName = function() {
            return this.name;
        };
        Person.prototype.getAge = function() {
            return this.age;
        };
        var person = new Person('Tom', 18);
        var person = {};
        Person.call(person, 'Tom', 18);
        person.__proto__ = Person.prototype;
        var p2 = new Person('Jerry', 20);
        ```
        
        ```javascript
        function Person(name, age) {
            this.name = name;
            this.age = age;
            
            this.getName = function() {
                return this.name;
            };
            
            this.getAge = function() {
                return this.age;
            };
        }
        var p = new Person('Tom', 20);
        ```
        
        ```javascript
        console.log(person.getName());

        function Cat(type) {
            this.type = type;
            this.name = 'cat:' + type;
        }
        
        var cat = new Cat('ttt');
        cat.getName = person.getName;
        console.log(cat.getName());
        
        Person.prototype.getName.call(cat);
        ```
        
    1. inheritance

        ```javascript
        var __extends = function (child, parent) {
            function __() { this.constructor = child; }
            __.prototype = parent.prototype;
            child.prototype = new __();
            //child.prototype = Object.create(parent.prototype);
            //child.prototype.constructor = child;
        };

        function Student(name, age, id) {
            Person.call(this, name, age);
            this.id = id;
        }

        __extends(Student, Person);

        Student.prototype.getId = function() {
            return this.id;
        };
        ```
    
    1. prototype chain (\_\_proto\_\_ chain)

        ```javascript
        var p = new Person('Tom', 15);
        p.getName = function() {/*...*/};
        p.getName();
        ```

    1. instanceof  
        Object.getPrototypeOf(obj) -> obj.\_\_proto\_\_  
        obj instanceof Clazz -> obj.\_\_proto\_\_ === Clazz.prototype || obj.\_\_proto\_\_.\_\_proto\_\_ === Clazz.prototype

        ```javascript
        var o = {};
        console.log(o instanceof Person);
        console.log(o instanceof Student);
        o.__proto__ = Student.prototype;
        ```

    1. Resources  
        1. [http://www.w3schools.com/js/js_object_prototypes.asp](http://www.w3schools.com/js/js_object_prototypes.asp)
        1. [http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/](http://javascriptissexy.com/javascript-prototype-in-plain-detailed-language/)
        1. [http://www.crockford.com/javascript/inheritance.html](http://www.crockford.com/javascript/inheritance.html)
        1. [http://javascript.crockford.com/prototypal.html](http://javascript.crockford.com/prototypal.html)
        1. [http://openwares.net/js/javascript_prototype_chain.html](http://openwares.net/js/javascript_prototype_chain.html)
        1. [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/prototype)
        1. [http://ms.csdn.net/share/2F555591FBA7ACD734AA8882189441D6_1_IPHONE_APP](http://ms.csdn.net/share/2F555591FBA7ACD734AA8882189441D6_1_IPHONE_APP)
        1. [Object.create](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/create)
