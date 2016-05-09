1. delete it
2. display: none
3. visibility: hidden
4. width/height: 0
5. offset 
6. opacity: 0

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
  <style>
    div {
      border: 1px black solid;
    }
  </style>
  <script>
    function hideB_1() {
      var b = document.getElementById('b');
      b.parentNode.removeChild(element);
    }
    function hideB_2() {
      var b = document.getElementById('b');
      b.style.display = 'none';
    }
    function hideB_3() {
      var b = document.getElementById('b');
      b.style.visibility = 'hidden';
    }
    function hideB_4() {
      var b = document.getElementById('b');
      b.style.height = '0';
      b.style.overflow = 'hidden';
    }
    function hideB_5() {
      var b = document.getElementById('b');
      b.style.position = 'fixed';  // try relative
      b.style.left = '-10000px';
    }
    function hideB_6() {
      var b = document.getElementById('b');
      b.style.opacity = '0';
    }
  </script>
</head>
<body>
<div>
  a
</div>
<div id="b">
  <button onclick="alert('b')">b</button>
</div>
<div>
  c
</div>
  <button onclick="hideB_5()">hide b</button>
</body>
</html>
```
