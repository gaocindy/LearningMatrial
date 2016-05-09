1. Basic Syntax
  1. var x = 1;
  1. data types : String, Number, Boolean, Array, Object
  1. value comparison, **== vs ===**, != vs !==
  
      [Equality_comparisons_and_sameness](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness)
      1. always use === and !==
      1. must use === or !== to compare null, undefine, '' etc.
  
  1. operator +, -, *, /, %, ++, --, |, &
  1. function
    ```javascript
    function sum(a, b) {
      return a + b;
    }
    ```

  1. conditional statements: if, switch
    ```javascript
    var foo;
    if (foo) {
        // ...
    }
    ```

  1. regex
  1. object
    ```javascript
      var person = {};
      person.name = 'Tom';
      person.age = 10;
      person['date-of-birth'] = new Date();
    ```

  1. array
    ```javascript
      var arr = [1, 2, 3];
      arr.push(9);
    ```

  1. loop: for, while
  1. error handling
    ```javascript
      try {
        // ...
      } catch (e) {
        // ...
      }
    ```
  
  1. [strict mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)
    ```javascript
      "use strict"
    ```

1. Object: dynamic, HashMap
  1. built-in objects. JSON, Math, Date, RegExp, Object, String, Number, Array, Function etc.
    1. **[API](http://docs.sencha.com/extjs/4.2.2/#!/api)**
    1. [API@Mozilla](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects)
  1. create object
    1. {}
    1. new Object();
    1. Object.create();
      ```javascript          
      function object(o) {
          function F() {}
          F.prototype = o;
          return new F();
      }
      
      var __extends = this.__extends || function (d, b) {
          for (var p in b) if (b.hasOwnProperty(p)) d[p] = b[p];
          function __() { this.constructor = d; }
          __.prototype = b.prototype;
          d.prototype = new __();
      };
      ```

  1. JSON: serialization
    ```javascript
      JSON.stringify();
      JSON.parse();
    ```

  1. retrieval & set
    1. **property name: $, _, a-z, A-Z, 0-9**
    1. **person.name, person[‘name’]**
  1. window, global
  1. delete
    1. delete property vs set undefined
      ```javascript
        var obj = {
            foo: 'a',
            bar: 'b'
        };
        obj.foo = undefined;
        console.log(obj.foo);
        
        delete obj.bar;
        console.log(obj.bar);
      ```

    1. configurable property
      ```javascript
        var foo = 'test';
        delete window.foo;
        window.bar = 'test';
        delete window.bar;
      ```

  1. enumeration
    1. in
    1. for in
      ```javascript  
      for (var key in object) {
          console.log(key, object[key]);
      }
      ```

      1. Object.keys

1. Array
  1. special object, automatically maintain length property
  1. iteration
    1. for (var i=0; i<length; i++) { }
    1. while(length--) { }
    1. for (i in array) { }
    1. **forEach**
      
      ```javascript
        var arr = [1, 2, 3];
        arr.forEach(function(num, i, a) {
          console.log(num);
        });
      ```

  1. methods
    1. isArray: static
    1. push
    1. concat
    1. sort: unstable
    1. indexOf/lastIndexOf
    1. **slice**: clone
    1. splice
      1. insert & delete
      1. difference from delete
    1. join/reverse/pop/reduce
  1. **Array-Like Objects**
    1. dom methods, function arguments
    1. convert to real array
    ```javascript
      Array.prototype.slice.apply(arguments);
    ```

1. String
  1. readonly array-like objects
  1. array methods on string
    ```javascript
      Array.prototype.method.apply(string);
    ```
  
  1. new String() vs ""
  1. methods
1. Function
  1. constructor class
  1. **define functions**
    ```javascript
    function foo() {
        // ...
    }
    var foo = function() {
        // ...
    };
    (function() {
        // ...
    })();
    ```

  1. arguments
    ```javascript
      function foo(p1, p2, p3) {
        var p1 = arguments[0],
          p2 = arguments[1],
          p3 = arguments[2];
          
          // ...
      }
    ```

  1. **hoisting**
  1. **scope**
    1. what’s this?
    1. change scope
      1. function.call/apply(obj, arg)
      1. obj.foo = func;

1. variable scope [This is not an answer](http://stackoverflow.com/questions/500431/what-is-the-scope-of-variables-in-javascript)
  1. global
    ```javascript
    var myglobal = 432;
    console.log(window.myglobal);
    for (var key in window) {
        console.log(key);
    }
    console.log(key);
    ```

  1. function/local
    ```javascript
    function foo() {
        var local1 = 'local1',
            local2 = 'local2';
        function bar() {
            var local1 = 'another local';
            console.log(local1);
            console.log(local2);
        }
        console.log(local1);
        bar();
        console.log(local2);
    }
    ```

  1. let
    ```javascript
    /*jshint esnext: true*/
    function letTest() {
        'use strict';
        let x = 31;
        if (true) {
          let x = 71;  // different variable
          console.log(x);  // 71
        }
        console.log(x);  // 31
    }

    letTest();
    ```
      
    test:
    
    ```javascript
    var x = 5;

    function foo() {
        console.log(x);
        var x = 10;
        console.log(x); 
    }
    
    foo();
    ```

1. [hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var)
  1. only declaration, not assignment
  1. function
1. [IIFE - immediately-invoked function expression](http://benalman.com/news/2010/11/immediately-invoked-function-expression/#iife)
    
    ```html
    <html>
      <head>
        <scipt>
          function winloaded() {
            alert('loaded');
          }
          window.onload = winloaded;
        </script>
      </head>
      <body>
      </body>
    </html>
    ```
    
    ```javascript
    (function() {
        // ...
    })();
    ```

1. [modular pattern](http://www.adequatelygood.com/JavaScript-Module-Pattern-In-Depth.html)
    
    ```typescript
    module victoria {
        export function myFunc() {
            console.log('victoria.myFunc');
        }
    }
    ```
    
    ```javascript
    var victoria;
    (function (victoria) {
        function myFunc() {
            console.log('victoria.myFunc');
        }
        victoria.myFunc = myFunc;
    })(victoria || (victoria = {}));
    ```
