```        
Closures are functions that refer to independent (free) variables.
```

1. Resources 
    1. [http://www.w3schools.com/js/js_function_closures.asp](http://www.w3schools.com/js/js_function_closures.asp)
    1. [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures)
    1. [http://javascriptissexy.com/understand-javascript-closures-with-ease/](http://javascriptissexy.com/understand-javascript-closures-with-ease/)
1. Conclusion
    1. function returns a function
    1. the function uses a local variable between the two functions
    
    ```javascript
    function makeAdder(x) {
        return function(y) {
            return x + y;
        };
    }

    var add5 = makeAdder(5);
    add5(3);
    add5(6);
    
    var add10 = makeAdder(10);
    add10(7);

    function foo(bar) {
        // ...
    }
    function foo() {
        var bar = arguments[0];
        // ...
    }
    ```

1. this, self, me, ths

    ```javascript
    var myObject = {
        foo: "bar",
        func: function() {
            var self = this;
            console.log("outer func:  this.foo = " + this.foo);
            console.log("outer func:  self.foo = " + self.foo);
            (function() {
                console.log("inner func:  this.foo = " + this.foo);
                console.log("inner func:  self.foo = " + self.foo);
            }());
        }
    };
    myObject.func();
    ```
1. closure in a loop

    ```javascript
    function showHelp(help) {
        document.getElementById('help').innerHTML = help;
    }

    function setupHelp() {
        var helpText = [
            {'id': 'email', 'help': 'Your e-mail address'},
            {'id': 'name', 'help': 'Your full name'},
            {'id': 'age', 'help': 'Your age (you must be over 16)'}
        ];

        for (var i = 0; i < helpText.length; i++) {
            var item = helpText[i];
            document.getElementById(item.id).onfocus = function() {
                showHelp(item.help);
            }
        }
    }

    setupHelp();
    ```

    fix
    
    ```javascript
    for (var i = 0; i < helpText.length; i++) {
        var item = helpText[i];
        document.getElementById(item.id).onfocus = (function() {
            var help = item.help;
            return function() {
                showHelp(help);
            };
        }());
    }
    ```

1. private members
  ```javascript
  function X() {
    function a() {
      alert('a');
    }
    
    this.b = a;
  }
  
  X.prototype.f = function() {
    alert(this.b());
  };
  
  new X().f();
  ```
  
  ```javascript
  function Counter() {
    var count = 0;
    this.get = function() {
      return count;
    };
    this.add = function() {
      count++;
      return this;
    };
  }
  
  var c1 = new Counter();
  c1.add().add();
  c1.get();  // returns 2
  
  var c2 = new Counter();
  c2.add();  // returns 1
  ```
  
  ```javascript
  var c1 = {
      count: 0;
      add: function() {
          this.count++;
          return this;
      },
      get: function() {
          return this.count;
      }
  };
  ```
  
  ```javascript
  var c1 = (function(){
      var count = 0;
      return {
          add: function(contact) {
              count++;
              return this;
          },
          get: function(idx) {
              return count;
          }
      };
  }());
  ```
