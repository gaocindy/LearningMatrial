1.
```javascript
(function(x){
  delete x;
  return x;
})(1);
```

2.
```javascript
var foo = {
  bar: function() { return this.baz; },
  baz: 1
};
(function() {
  return typeof arguments[0]();
})(foo.bar);
```

3.
```javascript
var foo = {
  bar: function() { return this.baz; },
  baz: 1
};
typeof (f = foo.bar)();
```

4.
```javascript
(function(foo) {
  return typeof foo.bar;
})({ foo: { bar: 1 } });
```

5.
```javascript
  var f = (function f(){ return "1"; }, function g(){ return 2; })();
  typeof f;
```

6.
```javascript
(function f() {
  function f() { return 1; }
  return f();
  function f() { return 2; }
})();
```

7.
```javascript
function f() { return f; }
new f() instanceof f;
```

8.
```javascript
var count = 0; 
 
var timer = setInterval(function() {
  if (count < 5) { 
    console.log('Timer call: ', count); 
    count++; 
  } else { 
    clearInterval(timer); 
  } 
}, 100);
```

9.
```javascript
function X() {
  this.f = function() {
    return true; 
  }; 
} 
 
// Should return false, but will be overridden 
X.prototype.f = function() {
  return false; 
}; 
 
var x = new X(); 
x.f();
```

10.
```javascript
function X() { }
 
var x1 = new X();
X.prototype.f = function(){ 
  return false; 
}; 

var x2 = new X();
x1.f();
x2.f();
```

11.
```javascript
function foo() {
  this.isLive = true; 
} 
foo(); 
alert(isLive); 
```

12.
```javascript
var obj = { 
  foo: function() {
    this.isLive = true;
  } 
}; 
obj.foo(); 
alert(isLive);
```

13.
```javascript
var obj = {}; 
function foo() { 
  return this; 
} 
alert(foo() == this); 
alert(foo.call(obj) == obj);
```

14.
```javascript
function highest(){ 
  return arguments.sort(function(a, b) {
    return b - a; 
  }); 
}
```

15
```javascript
Object.prototype.keys = function() {
  var keys = []; 
  for (var i in this) { 
    keys.push(i);
  }
  return keys; 
};

var obj = { a: 1, b: 2, c: 3 };
alert(obj.keys());
```

16.
```javascript
isC2LSupported: function() {
  if(window.PsNavigate ||
    (window.interOp && window.interOp.postMessage) ||
    (window.webkit && window.webkit.messageHandlers && window.webkit.messageHandlers.interOp && window.webkit.messageHandlers.interOp.postMessage)) {
      return true;
  }
  return false;
}
```

17.
```javascript
function finder(records, cb) {
    console.log("1-finder....begin  ");
    setTimeout(function () {
        console.log("2-inside finder settimeout before push " + records);
        records.push(3, 4);
        console.log("3-inside finder settimeout after push " + records);
        cb(records);
        console.log("6-inside finder settimeout after callback " + records);
    }, 50);
    console.log("1-finder....end  ");
}

function processor(records, cb) {
    console.log("5- processor ....begin" );
    setTimeout(function () {
        console.log("7-inside processor settimeout before push " + records);
        records.push(5, 6);
        console.log("8-inside processor settimeout after push " + records);
        cb(records);
        console.log("10-inside processor settimeout after callback " + records);
    }, 500);
    console.log("5- processor ....end" );
}

// using the callbacks
finder([1, 2], function (records) {
    console.log("4-finder -cb...begin");
    processor(records, function(records) {
        console.log("9-Processor -step into cb ");
        console.log("result: "+records);
        console.log("9-Processor -step into cb ");
    });
    console.log("4-finder -cb...end");
});
```

18.
```javascript
var eventable = {
    on: function(event, cb) {
        console.log("0.1 on function......begin");
        $(this).on(event, cb);
        console.log("0.2 on function......end");
    },
    trigger: function (event, args) {
        console.log(this+"(3.1)(7.1)trigger function....begin");
        $(this).trigger(event, args);
        console.log("(3.3)(7.3)trigger function....end");
    }
};

var finder = {
    run: function (records) {
        console.log("1.1-enter finder run...begin");
        var self = this;
        console.log(self+ "1.2-enter finder run...begin");
        setTimeout(function () {
            console.log("2.1-enter finder settime begin ...");
            records.push(3, 4);
            console.log("2.2-enter finder after push ...");
            self.trigger('done', [records]);
            console.log("2.4-enter finder trigger done ...end");
        }, 500);
        console.log("1.3-enter finder run...end");
    }
};
var processor = {
    run: function (records) {
        console.log("5.1-enter process run function  ...begin ");
        var self = this;
        console.log("5.2-enter process run function ... ");
        setTimeout(function () {
            console.log("6.1-enter process settime begin ...");
            records.push(5, 6);
            console.log("6.2-enter process after push ...");
            self.trigger('done', [records]);
            console.log("6.4-enter process after trigger ...");
        }, 500);
        console.log("5.3-enter process run function...  end");
    }
};
$.extend(finder, eventable);
$.extend(processor, eventable);

finder.on('done', function (event, records) {
    console.log("4.1-enter finder on event ... begin");
    processor.run(records);
    console.log("4.3- enter finder on event ... end");
});
processor.on('done', function (event, records) {
    console.log("8.1-enter processor on event ...begin");
    console.log(" 8.2-processor on "+records);
    console.log("8.3-enter processor on event ...end");
});
finder.run([1,2]);
```

19.
```javascript
function async(your_function, callback) {
    setTimeout(function() {
        your_function();
        if (callback) {callback();}
    }, 0);
}

// 1
console.log(1);
async(function() {console.log('x')}, null);
console.log(2);
console.log(3);

// 2
async(function() {console.log('x');}, function() {console.log(1);});
```
