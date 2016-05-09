1. iframe

  data.json
  ```json
  {
    "success": true,
    "data": "operation succeeded!"
  }
  ```
  get
  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script>
          function load() {
              var iframe = document.getElementById('iframe'),
                      content = document.getElementById('content');
              content.innerHTML = 'Loading...';
              iframe.src = 'data.json';
              iframe.onload = function() {
                  var data = iframe.contentDocument.body.innerText,
                          json = JSON.parse(data);
                  if (json.success) {
                      content.innerHTML = json.data;
                  }
              };
          }
      </script>
  </head>
  <body>
  <button onclick="load()">Load</button>
  <div id="content"></div>
  <iframe id="iframe" style="display:none"></iframe>
  </body>
  </html>
  ```
  post
  ```javascript
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script>
          function save() {
              var content = document.getElementById('content');
              content.innerHTML = 'Loading...';
              document.getElementById('form').submit();
          }
          window.onload = function() {
              var iframe = document.getElementById('iframe');
              iframe.onload = function() {
                  var data = iframe.contentDocument.body.innerText,
                          json = JSON.parse(data);
                  if (json.success) {
                      content.innerHTML = json.data;
                  }
              };
          };
      </script>
  </head>
  <body>
  <div id="content"></div>
  <form id="form" target="iframe" action="data.json" method="post">
      name:<input type="text">
      <button onclick="save();return false;">Submit</button>
  </form>
  <iframe id="iframe" name="iframe" style="display:none"></iframe>
  </body>
  </html>
  ```

2. script tag

  cb.js
  ```javascript
  callback('{"success": true, "data": "operation succeeded!"}');
  ```
  
  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script>
          function load() {
              var content = document.getElementById('content');
              content.innerHTML = 'Loading...';
  
              var script = document.createElement('script');
              script.src = 'cb.js';
              document.body.appendChild(script);
          }
  
          function callback(response) {
              response = JSON.parse(response);
              if (response.success) {
                  document.getElementById('content').innerHTML = response.data;
              }
          }
  
      </script>
  </head>
  <body>
  <div id="content"></div>
  <button onclick="load();">Submit</button>
  </body>
  </html>
  ```

3. image, style sheet

4. XMLHttpRequest
  ```html
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>Title</title>
      <script>
          function load() {
              var xhr = new XMLHttpRequest();
              xhr.onreadystatechange = function() {
                  if (xhr.readyState == 4 && xhr.status == 200) {
                      var response = JSON.parse(xhr.responseText);
                      if (response.success) {
                          document.getElementById("content").innerHTML = response.data;
                      }
                  }
              };
              xhr.open("GET", "data.json", true);
              xhr.send();
          }
      </script>
  </head>
  <body>
  <div id="content"></div>
  <button onclick="load();">Submit</button>
  </body>
  </html>
  ```

5. AngularJS
  ```html
  <!DOCTYPE html>
  <html>
  <head>
      <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.4.0/angular.min.js"></script>
      <meta charset="utf-8">
      <meta name="viewport" content="width=device-width">
      <title>Angular JS</title>
  </head>
  <script>
      angular.module('null', []).run(function($http) {
          $http({
              method: 'GET',
              url: 'http://www.google.ca/someUrl'
          }).then(function(response) {
              alert('successful')
          }, function(response) {
              alert('failed')
          });
      });
  
      angular.element(document).ready(function() {
          angular.bootstrap(document.body, ['null']);
      });
  </script>
  <body>
  </body>
  </html>
  ```

6. CORS
  1. CORS Request requires server support
    
    ```
    Access-Control-Allow-Origin: http://api.bob.com
    Access-Control-Allow-Credentials: true
    Access-Control-Expose-Headers: FooBar
    ```
  2. embedded iframe
  3. alternative jsonp
  4. XDomainRequest

7. GET vs POST
